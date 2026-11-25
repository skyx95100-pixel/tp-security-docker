# TP : Sécurisation d'un conteneur Docker

[TOC]

## Contexte

Nous avons créé un Dockerfile permettant de construire une image Docker et d'exécuter l'application Quiz Docker. L'application fonctionne, mais son fonctionnement ne garantit pas que son image et son conteneur respectent les bonnes pratiques de sécurité.
On interviens désormais en tant qu'ingénieur(e) DevOps au sein d'une entreprise qui souhaite déployer cette application
dans un environnement de production.

Avant d'autoriser ce déploiement, votre responsable technique vous demande de réaliser un audit de sécurité, d'identifier
les risques potentiels et de renforcer la configuration Docker. Vous devez appliquer les bonnes pratiques de sécurité, sans compromettre le fonctionnement de l'application.
Objectif

À l'issue du TP, on sera en mesure de :
- Identifier les risques de sécurité liés à une image et à un conteneur Docker.
- Appliquer les bonnes pratiques de création d'images Docker.
- Réduire la surface d'attaque d'une image.
- Contrôler les privilèges et les ressources d'un conteneur.
- Utiliser un outil d'analyse de vulnérabilités.
- Comparer et justifier les améliorations réalisées.

## Mission 1 : Audit de l'image Docker existante

Reprenez le Dockerfile que vous avez réalisé lors de l'exercice (dockerfile-exercice2). Avant toute modification, effectuez un
état des lieux de sa sécurité. Travail demandé :

- Construisez votre image initiale sous le nom quiz-docker:initial.
- Vérifiez que l'application fonctionne.
- Identifiez l'image de base utilisée.
- Vérifiez sous quel utilisateur s'exécute le processus applicatif.
- Relevez la taille de l'image.
- Analysez les différentes couches qui la composent.
- Réalisez une première analyse des vulnérabilités.
- Conservez les résultats de cette analyse.

Questions :
- L'image utilisée est-elle adaptée à une utilisation en production ?
    - Réponse :
- Quels composants sont réellement nécessaires pour exécuter l'application ?
    - Réponse :
- Quels risques de sécurité identifiez-vous ?
    - Réponse :
- Quelles améliorations recommanderiez-vous en priorité ?
    - Réponse :
- Faites un tableau présentant l'état initial de votre image Docker et les risques identifiés.
    - Réponse :

## Mission 2 : Sécuriser l'image et le conteneur Docker

Vous devez maintenant appliquer les recommandations de sécurité suivantes :

- Utiliser des images de base minimales
- Ne pas exécuter les conteneurs avec l'utilisateur root
- Utiliser .dockerignore
- Utiliser des tags d'images précis
- Privilégier l’instruction COPY plutôt que ADD
- Limiter les ressources et les privilèges des conteneurs
- Utiliser des builds multi-étapes
- Eviter d'exposer directement le socket Docker (/var/run/docker.sock) aux conteneurs
- Vérifier (régulièrement) la sécurité des images et des conteneurs

## Mission 3 : Comparer les résultats avant et après sécurisation

Après avoir appliqué les recommandations :

- Construisez une nouvelle image sous le nom de quiz-docker:secure
- Démarrez un conteneur à partir de cette image et vérifiez le bon fonctionnement de l'application.
- Publiez l’image dans votre registry dockerHub
- Complétez un tableau comparatif de l’image initial et sécurisé avec les critères comme présence d'outils de développement, utilisation de .- dockerignore, multi-stage build, limitation des ressources, restrictions des privilèges, accès au socket Docker, CVE critiques, CVE élevées, CVE moyennes, CVE faibles etc…

Questions d'analyse :

- Quelles modifications ont apporté les améliorations les plus significatives ?
    - Réponse :
- La taille de l'image a-t-elle diminué ? Pourquoi ?
    - Réponse :
- Quelles recommandations concernent le Dockerfile et lesquelles concernent l'exécution du conteneur ?
    - Réponse :
- Votre image est-elle désormais totalement sécurisée ? Justifiez votre réponse.
    - Réponse :
- Quelles mesures complémentaires proposeriez-vous pour un déploiement en production ?
    - Réponse :

## Mission 4 : Utiliser Docker Hardened Image

Réalisez l'atelier pratique : Migration d’une application Node vers des images Docker renforcées accessible sur
https://docs.docker.com/guides/lab-dhi-node/ 👁 afin d'etudier la possibilité d'utiliser une Docker Hardened Image pour
l'environnement de production. Comparez son contenu, ses propriétés de sécurité et ses vulnérabilités avec votre image
actuelle sécurisée.

## Livrables attendus

À la fin du TP, fournir :

- Le Dockerfile initial et le Dockerfile sécurisé.
- Le fichier .dockerignore.
- Les commandes utilisées pour construire et exécuter les images et les conteneurs.
- Les résultats des analyses de sécurité avant et après.
- Le tableau comparatif complété.
- Une courte synthèse expliquant les améliorations apportées et les risques résiduels.
- Le lien vers le dépôt Git contenant les modifications ainsi que les images publiées dans un registry publique.