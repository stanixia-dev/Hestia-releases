# Hestia — releases

Binaires officiels de **Hestia**, client SSH personnel pour Linux et Android : clés, connexions et empreintes d'hôtes dans un coffre chiffré synchronisé entre appareils, terminaux en onglets et transferts SFTP.

Ce dépôt ne contient que les versions publiées et le manifeste de mise à jour automatique ; le code source est privé.

**[⬇ Télécharger la dernière version](https://github.com/stanixia-dev/Hestia-releases/releases/latest)**

## Fonctionnalités

- **Coffre chiffré** : clés SSH, connexions et `known_hosts` protégés par un mot de passe maître (Argon2id + XChaCha20-Poly1305). Verrouillage automatique après inactivité, à la mise en veille et au verrouillage de session.
- **Synchronisation** du coffre chiffré via un dossier partagé (Syncthing, Nextcloud…) ou un serveur SFTP, avec fusion des modifications faites sur plusieurs appareils.
- **Terminaux en onglets** : rebond (jump host), agent SSH et transfert d'agent, sessions tmux reprises automatiquement, copie distante (OSC 52).
- **Clés SSH** : génération Ed25519 et installation sur un hôte (équivalent de `ssh-copy-id`).
- **Fichiers** : navigateur SFTP, transferts avec reprise après coupure, édition d'un fichier distant dans l'application locale.
- **Redirection de ports locale** (`-L`) par hôte.
- **Mises à jour automatiques** signées, avec canal bêta optionnel.

## Installation

| Plateforme | Fichier | Remarques |
|---|---|---|
| Linux (x86_64) | `Hestia_<version>_amd64.AppImage` | Rendre exécutable (`chmod +x`) puis lancer. Mise à jour automatique intégrée. |
| Debian / Ubuntu | `Hestia_<version>_amd64.deb` | `sudo apt install ./Hestia_<version>_amd64.deb`. La mise à jour automatique demande le mot de passe administrateur. |
| Android 8+ (arm64) | `Hestia_<version>_arm64.apk` | Ouvrir l'APK sur le téléphone et autoriser l'installation depuis cette source. |

## Mises à jour

Hestia vérifie les nouvelles versions au lancement, puis régulièrement tant qu'elle reste ouverte. Ce réglage peut être désactivé dans **Réglages → Mises à jour**.

- **Stable** : la release marquée *Latest*.
- **Bêta** (option dans les réglages) : reçoit aussi les pré-releases, qui sont des builds de test non validés.

Les paquets desktop sont signés : Hestia vérifie la signature (`.sig`) avant d'installer. Sur Android, l'installeur système demande une confirmation à chaque mise à jour.

## Vérifier un téléchargement

Chaque AppImage et chaque `.deb` est accompagné d'un fichier `.sig` (signature minisign utilisée par la mise à jour automatique). `latest.json` décrit la dernière version pour l'outil de mise à jour.

L'APK est signé avec la clé de release d'Hestia :

```sh
apksigner verify --print-certs Hestia_<version>_arm64.apk
```

## Signaler un problème

Les retours se font directement auprès de l'auteur, car le dépôt de code n'est pas public.
