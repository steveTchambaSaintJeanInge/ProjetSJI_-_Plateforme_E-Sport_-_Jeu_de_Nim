# ProjetSJI_-_Plateforme_E-Sport_-_Jeu_de_Nim
L'objectif de ce projet est de concevoir et développer une application web de jeu en ligne décentralisée (P2P). L'application permet à deux joueurs de s'affronter au Jeu de Nim en temps réel directement depuis leur navigateur web, d'autoriser des spectateurs à observer la partie, d'organiser des tournois et de suivre leurs statistiques.
# Gestion des Salons & Connexion P2P
Génération d'Identifiant : À son arrivée, l'utilisateur reçoit automatiquement un Identifiant Réseau unique (son Peer ID).
Création de Salon (Mode Hôte) : Tout utilisateur peut devenir "Hôte" et créer un salon de jeu. L'application génère un Code de Salon à partager.
Rejoindre une partie (Mode Joueur / Spectateur) : si le salon compte 1 seul joueur, le premier entrant devient l'Adversaire. Si le salon compte déjà 2 joueurs, les entrants suivants basculent automatiquement en mode Spectateur.
# Résilience réseau : 
En cas de déconnexion d'un joueur, la partie est mise en pause pendant 15 secondes. Sans réapparition, l'autre joueur est déclaré vainqueur par forfait. NB : cette durée peut être configurable l’hôte.

# Règles de Jeu
- Chaque début de partie génère un plateau imprévisible composé de 3 à 5 lignes contenant chacune un nombre minimal et un nombre maximal bâtonnets. Le nombre minimum de bâtonnets minimum est strictement supérieur à 2 et le nombre maximum de bâtonnets est strictement supérieur à 7.
- Chaque joueur dispose de 15 secondes (par défaut) maximum pour valider son coup. Cette durée est configurable par l’hôte. Si le temps expire, le tour passe à l'adversaire et un bâtonnet est retiré automatiquement.
- La partie démarre aléatoirement en mode Mboutman (celui qui prend le dernier bâtonnet perd) ou Donman (celui qui prend le dernier bâtonnet gagne).
- Mode Arcade il permet à un joueur d affronter les joueurs ayant des points
supérieurs aux siens siens. Si le joueur a un score inférieur ou égal à 500 points, alors reste
en mode Mboutman (il n aura plus l option de changer de mode) mode). Lorsque le joueur
réalise une victoire, afficher une carte ( qui montre comment se dernier se
déplace vers le prochain adversaire
- Une fois par partie, un joueur peut cliquer sur "Utiliser Joker" pour inverser le mode de jeu actuel. L'adversaire est immédiatement notifié du changement.
- Si un joueur enchaîne plusieurs coups avec un temps de réponse trop parfait (ex: inférieur à 150 millisecondes), un message d'avertissement "Comportement suspect détecté" est émis et la partie peut être invalidée.
- À chaque coup joué, l'application génère une empreinte numérique de sécurité (alphanumérique). L'application de l'adversaire vérifie que l'empreinte correspond à la règle jouée pour s'assurer que personne n'a modifié le code JavaScript localement pour tricher.

# Maitre de Salon
L'utilisateur qui crée le tournoi définit le nombre de participants (4, 8 ou 16 joueurs). L'application génère automatiquement les affrontements (Quarts de finale, Demi-finales, Finale). Lorsqu'un match P2P se termine, le résultat est transmis au créateur du tournoi qui publie le résultat en temps réel pour tous les participants.
Statistiques, Replay & Personnalisation
Chaque joueur démarre avec un score de 1200 points. Les victoires font gagner des points et les défaites en font perdre. 5 points pour une victoire et -5 points pour une défaite.
L'utilisateur peut télécharger le fichier d'une partie terminée (format .json ou .csv).
L'application permet de charger ce fichier et de réviser la partie coup par coup (Boutons : Suivant, Précédent – sous forme de slides).
Un tableau de bord affiche le taux de victoire, la vitesse moyenne de décision et la courbe d'évolution du score d’un joueur.


# 3. Restdictions Stricte :
- Aucun framework JS (pas de React, Vue, Angular, Svelte, etc.).
- Aucun thème CSS (vous pouvez utiliser Bootstrap ou Tailwindcss sans utiliser les thèmes existants sur Internet).
- Aucun serveur Backend de base de données (pas de Node.js/Express avec DB, Firebase, Supabase, etc.).
- Tout le stockage et le calcul doivent résider dans les navigateurs interconnectés.
