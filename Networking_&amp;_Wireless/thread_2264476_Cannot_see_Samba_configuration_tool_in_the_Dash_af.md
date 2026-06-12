---
title: "Cannot see Samba configuration tool in the Dash after frech ubuntu 14.04 install"
date: 2015-02-07
forum: Networking &amp; Wireless
---

### Post by ldp06000 on 2015-02-07
After a fresh instal of ubuntu 14.04 (my previous installation has seen to be broken somewhere reading .wmv file with VLC), I've installed Samba GUI tool from the software center.
It briefly appears in the launchpad then disappears. From this time I cannot the see in in the dash.
I've found this in askUbuntu [Cannot run samba interface after installing 13.04]("http://askubuntu.com/questions/289574/cannot-run-samba-interface-after-installing-13-04")

but the command sudo apt-get install samba samba-common gives me nothing to install.
Lecture des listes de paquets... Fait
Construction de l'arbre des dépendances       
Lecture des informations d'état... Fait
samba est déjà la plus récente version disponible.
samba passé en « installé manuellement ».
samba-common est déjà la plus récente version disponible.
Les paquets suivants ont été installés automatiquement et ne sont plus nécessaires :
  kde-l10n-engb kde-l10n-fr
Veuillez utiliser « apt-get autoremove » pour les supprimer.
0 mis à jour, 0 nouvellement installés, 0 à enlever et 8 non mis à jour.

The following guide [Install and Configure Samba share in Ubuntu 13.10 &#8216;Saucy Salamander&#8217; , 13.04| Howto]("http://www.unixmen.com/howto-install-and-configure-samba-share-in-ubuntu/") has no result either.
sudo apt-get install system-config-samba
Lecture des listes de paquets... Fait
Construction de l'arbre des dépendances       
Lecture des informations d'état... Fait
system-config-samba est déjà la plus récente version disponible.
Les paquets suivants ont été installés automatiquement et ne sont plus nécessaires :
  kde-l10n-engb kde-l10n-fr
Veuillez utiliser « apt-get autoremove » pour les supprimer.
0 mis à jour, 0 nouvellement installés, 0 à enlever et 8 non mis à jour.


Any idea ?
Laurent06000

---

### Post by bab1 on 2015-02-07
> **ldp06000 said:**
> After a fresh instal of ubuntu 14.04 (my previous installation has seen to be broken somewhere reading .wmv file with VLC), I've installed Samba GUI tool from the software center.
It briefly appears in the launchpad then disappears. From this time I cannot the see in in the dash.
I've found this in askUbuntu Cannot run samba interface after installing 13.04

but the command sudo apt-get install samba samba-common gives me nothing to install.
Lecture des listes de paquets... Fait
Construction de l'arbre des dépendances 
Lecture des informations d'état... Fait
samba est déjà la plus récente version disponible.
samba passé en « installé manuellement ».
samba-common est déjà la plus récente version disponible.
Les paquets suivants ont été installés automatiquement et ne sont plus nécessaires :
kde-l10n-engb kde-l10n-fr
Veuillez utiliser « apt-get autoremove » pour les supprimer.
0 mis à jour, 0 nouvellement installés, 0 à enlever et 8 non mis à jour.

The following guide Install and Configure Samba share in Ubuntu 13.10 &#8216;Saucy Salamander&#8217; , 13.04| Howto has no result either.
sudo apt-get install system-config-samba
Lecture des listes de paquets... Fait
Construction de l'arbre des dépendances 
Lecture des informations d'état... Fait
system-config-samba est déjà la plus récente version disponible.
Les paquets suivants ont été installés automatiquement et ne sont plus nécessaires :
kde-l10n-engb kde-l10n-fr
Veuillez utiliser « apt-get autoremove » pour les supprimer.
0 mis à jour, 0 nouvellement installés, 0 à enlever et 8 non mis à jour.


Any idea ?
Laurent06000

There is no need for a Samba GUI share configuration tool.  Just open the /etc/samba/smb/conf file in a text editor, change the WORKGROUP NAME  and add the share definitions at the bottom.  There is no need for altering anything else for us in a simple LAN.

---

