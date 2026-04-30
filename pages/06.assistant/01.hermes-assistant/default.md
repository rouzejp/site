---
title: "Hermes — Mon Assistant Personnel"
menu: Hermes Assistant
published: true
date: 2025-04-30
author: Jean-Paul Rouzé
taxonomy:
    tag:
        - assistant
        - IA
        - obsidian
        - workflow
---

# Hermes — Mon Assistant Personnel

> Depuis son arrivée dans mon environnement numérique, Hermes est devenu le chef d'orchestre de ma vie digitale : gestionnaire de mon coffre Obsidian, éditeur de mon site web, aiguilleur de contenu vers les réseaux sociaux, et architecte de toute mon infrastructure technique sous WSL. Voici tout ce qu'il fait concrètement pour moi.

---

## 1. Le Cœur du Système : Mon Coffre Obsidian "Jenkins"

La pièce maîtresse de notre collaboration. Mon coffre Obsidian — un "Second Cerveau" numérique — est devenu un écosystème vivant qu'Hermes gère quasiment en autonomie.

### 1.1 L'Architecture du Vault

Ensemble, nous avons bâti une structure en français, logique et extensible :

```
00_Boite_Reception/    ← Captures web en attente
raw/                   ← Sources brutes archivées
  articles/            ← Articles, tutoriels
  conversations/       ← Conversations Hermes archivées
queries/               ← Logs de conversations IA (par thème)
  dev-tech/            ← Code et logiciel
  homelab/             ← Serveurs et réseau
  sciences/            ← Physique, bio
  societe-politique/   ← Débats et société
  site-web/            ← Contenu pour rouze.eu
  IA-outils/           ← Prompts et comparaisons
entities/              ← Fiches de connaissance (outils, projets)
concepts/              ← Sujets transverses, méthodes
10_Homelab/            ← Infrastructure maison
20_Usine_Contenu/      ← Pipeline de publication
  01_Ideation/         ← Idées de contenu
  02_En_Cours/         ← Rédaction en cours
  03_Publie/           ← Contenu publié
30_Second_Cerveau/     ← Notes permanentes
50_Lectures/           ← Fiches de lecture
   Livres/             ← Par livre
   Auteurs/            ← Biographies d'auteurs
90_Systeme/            ← Modèles, SCHEMA, pièces jointes
```

Le fichier **SCHEMA.md** définit la taxonomie des tags, les conventions de nommage, et le format des métadonnées — une bible que je n'ai plus à retenir.

### 1.2 Le Workflow Boîte de Réception → Connaissance

Quand je capture un article intéressant dans la boîte de réception :

1. **Hermes analyse** le contenu
2. **Détermine le type** : entité (outil, projet) ou concept (méthode, sujet) ?
3. **Sauvegarde la source brute**
4. **Crée une fiche de connaissance** avec résumé, wikilinks, métadonnées
5. **Nettoie la boîte de réception**
6. **Met à jour l'index** et le journal

Le résultat : plus jamais de "j'ai lu ça quelque part" — tout est indexé, lié, retrouvable.

### 1.3 Le Suivi de Lectures

Je lui envoie un simple message du type `lu: Xenos - Dan Abnett`, et Hermes fait le reste :

1. Trouve les infos du livre sur le web (Wikipédia, Fandom, Amazon)
2. Crée la fiche auteur avec biographie et photo
3. Crée la fiche livre avec résumé, couverture, notes
4. Publie l'article sur rouze.eu dans la section Lectures
5. Met à jour l'index du vault

Ma bibliothèque personnelle se construit automatiquement, sans que j'aie à faire autre chose que lire.

### 1.4 La Maintenance Automatique

Deux tâches programmées tournent toutes les 12 heures :

| Tâche | Horaire | Ce qu'elle fait |
|-------|---------|-----------------|
| Santé du vault | 00h00 / 12h00 | Vérifie l'intégrité : fichiers orphelins, métadonnées manquantes, liens cassés |
| Surveillance inbox | 00h30 / 12h30 | Vérifie les nouveaux éléments dans la boîte de réception |

Je n'ai plus à penser à la maintenance — le vault reste propre en permanence.

---

## 2. Le Site Web (rouze.eu)

Hermes gère mon site GRAV CMS (thème Canvas), hébergé chez o2switch.

### 2.1 Création et Édition de Pages

Je lui demande de publier un article, et il :

1. Récupère le contenu depuis le vault Obsidian
2. Écrit l'article complet en Markdown
3. Crée la structure GRAV : dossier numéroté, frontmatter YAML
4. Ajoute les images et ressources dans le dossier de la page
5. Commit et push sur GitHub
6. M'indique de vider le cache GRAV

### 2.2 La Synchronisation

Le site utilise le plugin **Git Sync** (v3.2.0) qui synchronise le dossier `pages/` entre le serveur et GitHub. Hermes a configuré et dépanné cette synchronisation à plusieurs reprises.

---

## 3. Les Réseaux Sociaux

### 3.1 Bluesky

Quand un article est publié sur le site, Hermes peut le partager automatiquement sur Bluesky (compte @jprouze.eurosky.social, PDS personnalisé eurosky.social). Pas de LinkedIn ni X/Twitter — je n'y suis pas.

---

## 4. L'Infrastructure Technique

Tout ce qui fait que ce système tient debout.

### 4.1 WSL Persistant

Hermes tourne sur WSL2 (Ubuntu) sous Windows. Pour que ça reste en ligne 24/7 :

- **Service systemd** : le gateway Telegram est un service systemd user avec restart automatique
- **Linger activé** : le service survit à la déconnexion
- **Keepalive cron** : une commande toutes les minutes empêche WSL de s'éteindre
- **Démarrage auto au boot** : un script VBS dans le dossier Startup de Windows

### 4.2 Gateway Telegram

Le pont avec le monde extérieur. Hermes me répond via Telegram (bot @hermeswsljpr_bot), écoute les messages et les hooks, redémarre automatiquement en cas de crash. Je peux discuter avec mon assistant depuis mon téléphone, n'importe où.

### 4.3 GitHub

Authentification HTTPS + PAT. Hermes peut cloner, modifier, committer et pusher sans intervention de ma part.

---

## 5. Les Automatisations

| Automatisation | Horaire | Description |
|----------------|---------|-------------|
| Rapport d'activité quotidien | 08h00 | Résumé des dernières 24h : actions, créations, problèmes, décisions |
| Check santé vault | 00h00 / 12h00 | Audit automatique du coffre Obsidian |
| Surveillance inbox | 00h30 / 12h30 | Détection de nouveaux contenus à traiter |

---

## 6. En Résumé : Ce Que Ça M'apporte

| Avant Hermes | Après Hermes |
|--------------|--------------|
| Je notais sur des post-its | Tout est structuré dans un vault Obsidian vivant |
| Je cherchais pendant 10 minutes | Tout est indexé, retrouvable en 2 secondes |
| Je poussais manuellement des fichiers | Un message Telegram → article publié |
| "Je l'ai lu mais je ne sais plus où" | Fiche de lecture complète, automatique |
| Je devais relancer WSL à chaque fois | Service toujours en ligne depuis le boot |
| Maintenance oubliée | Crons automatiques toutes les 12h |

---

*Rédigé par Hermes Agent le 30 avril 2025 — en collaboration avec Jean-Paul.*
