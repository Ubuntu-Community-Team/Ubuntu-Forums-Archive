---
title: "Bluetooth down, no such device"
date: 2016-12-18
forum: Networking &amp; Wireless
---

### Post by minecraft-electricity on 2016-12-18
Hi,

I installed ubuntu 14.04, bluetooth worked, since time passed and I upgraded to 16.04, recently I tryed to use bluetooth but it did not worked, so here is all i've done:
```
 306  shuf -i 1-2 -n 1
  307  clear
  308  shuf -i 1-5 -n 1
  309  sudo apt-get remove --purge gnome-bluetooth 
  310  sudo apt-get install gnome-bluetooth 
  313  sudo apt-get update && sudo apt-get upgrade -y && sudo apt-get autoremove -y && sudo apt-get -y autoclean
  314  sudo apt-get install unity-control-center
  317  sudo nano /etc/rc.local
  318  sudo rfkill unblock bluetooth && rfkill list bluetooth
  319  sudo rfkill unblock all
  320  sudo hciconfig hci0 up
  321  sudo /etc/init.d/bluetooth restart
  322  sudo rfkill unblock all
  323  sudo hciconfig hci0 up
  324  hciconfig hci0 reset
  325  sudo hciconfig hci0 reset
  327  rfkill list
  328  sudo rfkill unblock bluetooth
  329  rfkill list
  330  lspci -knn | grep Net -A2
  331  sudo /etc/init.d/networking restart
  332  rfkill list
  333  sudo rfkill unblock all
  334  sudo hciconfig hci0 up
  335  sudo /etc/init.d/bluetooth restart
  362  rfkill list
  363  lspci -knn | grep Net -A2
  364  sudo apt-get remove gnome-bluetooth 
  365  sudo apt-get update && sudo apt-get upgrade && sudo apt-get autoremove && sudo apt-get autoclean
  407  sudo apt-get install bluedevil 
  408  bluedevil-wizard 
  409  hciconfig up 
  410  bluedevil-wizard 
  411  bluetooth-wizard 
  412  bluemoon 
  413  sudo /etc/init.d/bluetooth start
  414  sudo apt-get install blueman bluez-utils bluez bluetooth
  415  sudo apt-get install blueman bluez bluetooth
  416  sudo apt-get install blueman bluez:i386
  417  sudo apt-get install pulseaudio-module-bluetooth* ubuntu-desktop* unity-control-center*
  418  UP RUNNING PSCAN ISCAN
  419  hciconfig -a
  420  hciconfig hci0 up
  421  sudo hciconfig hci0 up
  422  rfkill list
  423  hcitool dev
  424  dmesg | grep -i bluetooth
  425  sudo hciconfig hci0 up
  426  watch -n 60 synclient TapButton3=3 TapButton2=2
  427  rfkill list
  428  dmesg | grep -i bluetooth
  429  sudo hciconfig hci0 up
  430  hciconfig -a
  431  bluetoothctl
  432  dmesg | grep -i bluetooth
  433  hciconfig -a
  434  man bluetoothctl 
  435  bluetoothctl -h
  436  sudo nautilus
  437  history

mineelectricity@mineelectricity:~$ sudo rfkill unblock bluetooth && rfkill list bluetooth
1: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
mineelectricity@mineelectricity:~$ hcitool dev
Devices:
mineelectricity@mineelectricity:~$ hciconfig
hci0:    Type: BR/EDR  Bus: USB
    BD Address: 54:27:1E:0C:53:63  ACL MTU: 820:8  SCO MTU: 255:16
    DOWN 
    RX bytes:1274 acl:0 sco:0 events:129 errors:0
    TX bytes:25311 acl:0 sco:0 commands:137 errors:0
mineelectricity@mineelectricity:~$ hcitool scan
Device is not available: No such device
mineelectricity@mineelectricity:~$ uname -a
Linux mineelectricity 4.4.0-53-generic #74-Ubuntu SMP Fri Dec 2 15:59:10 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux
```

I tested and my bluetooth work on W10, ubuntu 16.04 liveusb but not on ubuntu mate liveusb

some more things i've done:
```
mineelectricity@mineelectricity:~$ sudo rfkill unblock bluetooth && rfkill list bluetooth
1: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
mineelectricity@mineelectricity:~$ hcitool dev
Devices:
mineelectricity@mineelectricity:~$ hciconfig
hci0:    Type: BR/EDR  Bus: USB
    BD Address: 54:27:1E:0C:53:63  ACL MTU: 820:8  SCO MTU: 255:16
    DOWN 
    RX bytes:1274 acl:0 sco:0 events:129 errors:0
    TX bytes:25311 acl:0 sco:0 commands:137 errors:0
mineelectricity@mineelectricity:~$ hcitool scan
Device is not available: No such device
mineelectricity@mineelectricity:~$ uname -a
Linux mineelectricity 4.4.0-53-generic #74-Ubuntu SMP Fri Dec 2 15:59:10 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux

mineelectricity@mineelectricity:~$ sudo /etc/init.d/bluetooth restart
[sudo] Mot de passe de mineelectricity : 
[ ok ] Restarting bluetooth (via systemctl): bluetooth.service.
```

updates + reboot
```
mineelectricity@mineelectricity:~$ sudo apt update
[sudo] Mot de passe de mineelectricity : 
Atteint:1 http://archive.canonical.com/ubuntu xenial InRelease            
Réception de:2 http://security.ubuntu.com/ubuntu xenial-security InRelease [102 kB]
Réception de:3 http://security.ubuntu.com/ubuntu xenial-security/main amd64 DEP-11 Metadata [68,2 kB]
Réception de:4 http://security.ubuntu.com/ubuntu xenial-security/main DEP-11 64x64 Icons [48,0 kB]
Réception de:5 http://security.ubuntu.com/ubuntu xenial-security/universe amd64 DEP-11 Metadata [19,4 kB]
Réception de:6 http://security.ubuntu.com/ubuntu xenial-security/universe DEP-11 64x64 Icons [25,6 kB]
Réception de:7 http://security.ubuntu.com/ubuntu xenial-security/multiverse amd64 DEP-11 Metadata [212 B]
Atteint:8 http://fr.archive.ubuntu.com/ubuntu xenial InRelease                 
Atteint:9 http://ppa.launchpad.net/linrunner/tlp/ubuntu xenial InRelease       
Réception de:10 http://fr.archive.ubuntu.com/ubuntu xenial-updates InRelease [102 kB]
Atteint:11 http://ppa.launchpad.net/nerdherd/cloud/ubuntu xenial InRelease
Atteint:12 http://ppa.launchpad.net/peterlevi/ppa/ubuntu xenial InRelease      
Atteint:13 https://repo.skype.com/deb stable InRelease                         
Atteint:14 http://ppa.launchpad.net/webupd8team/java/ubuntu xenial InRelease   
Réception de:15 http://fr.archive.ubuntu.com/ubuntu xenial-backports InRelease [102 kB]
Réception de:16 http://fr.archive.ubuntu.com/ubuntu xenial-updates/main amd64 Packages [441 kB]
Réception de:17 http://fr.archive.ubuntu.com/ubuntu xenial-updates/main i386 Packages [433 kB]
Réception de:18 http://fr.archive.ubuntu.com/ubuntu xenial-updates/main amd64 DEP-11 Metadata [302 kB]
Réception de:19 http://fr.archive.ubuntu.com/ubuntu xenial-updates/main DEP-11 64x64 Icons [183 kB]
Réception de:20 http://fr.archive.ubuntu.com/ubuntu xenial-updates/universe amd64 Packages [370 kB]
Réception de:21 http://fr.archive.ubuntu.com/ubuntu xenial-updates/universe i386 Packages [366 kB]
Réception de:22 http://fr.archive.ubuntu.com/ubuntu xenial-updates/universe amd64 DEP-11 Metadata [121 kB]
Réception de:23 http://fr.archive.ubuntu.com/ubuntu xenial-updates/universe DEP-11 64x64 Icons [145 kB]
Réception de:24 http://fr.archive.ubuntu.com/ubuntu xenial-updates/multiverse amd64 DEP-11 Metadata [2 516 B]
Réception de:25 http://fr.archive.ubuntu.com/ubuntu xenial-backports/main amd64 DEP-11 Metadata [208 B]
Réception de:26 http://fr.archive.ubuntu.com/ubuntu xenial-backports/universe amd64 DEP-11 Metadata [212 B]
Réception de:27 http://fr.archive.ubuntu.com/ubuntu xenial-backports/multiverse amd64 DEP-11 Metadata [212 B]
2 832 ko réceptionnés en 23s (123 ko/s)                                        
AppStream cache update completed, but some metadata was ignored due to errors.
Lecture des listes de paquets... Fait
Construction de l'arbre des dépendances       
Lecture des informations d'état... Fait
19 packages can be upgraded. Run 'apt list --upgradable' to see them.
mineelectricity@mineelectricity:~$ apt list --upgradable
En train de lister... Fait
deja-dup/xenial-updates 34.2-0ubuntu1.1 amd64 [upgradable from: 34.2-0ubuntu1]
deja-dup-backend-gvfs/xenial-updates,xenial-updates 34.2-0ubuntu1.1 all [upgradable from: 34.2-0ubuntu1]
gnome-software/xenial-updates 3.20.1+git20161013.0.d77d6cf-0ubuntu2~xenial1 amd64 [upgradable from: 3.20.1+git20160923.2.7374bdc-0ubuntu1~xenial1]
gnome-software-common/xenial-updates,xenial-updates 3.20.1+git20161013.0.d77d6cf-0ubuntu2~xenial1 all [upgradable from: 3.20.1+git20160923.2.7374bdc-0ubuntu1~xenial1]
libpam-systemd/xenial-updates 229-4ubuntu13 amd64 [upgradable from: 229-4ubuntu12]
libsystemd-dev/xenial-updates 229-4ubuntu13 amd64 [upgradable from: 229-4ubuntu12]
libsystemd0/xenial-updates 229-4ubuntu13 amd64 [upgradable from: 229-4ubuntu12]
libudev-dev/xenial-updates 229-4ubuntu13 amd64 [upgradable from: 229-4ubuntu12]
libudev1/xenial-updates 229-4ubuntu13 amd64 [upgradable from: 229-4ubuntu12]
linux-firmware/xenial-updates,xenial-updates 1.157.6 all [upgradable from: 1.157.5]
python3-software-properties/xenial-updates,xenial-updates 0.96.20.5 all [upgradable from: 0.96.20.4]
software-properties-common/xenial-updates,xenial-updates 0.96.20.5 all [upgradable from: 0.96.20.4]
software-properties-gtk/xenial-updates,xenial-updates 0.96.20.5 all [upgradable from: 0.96.20.4]
systemd/xenial-updates 229-4ubuntu13 amd64 [upgradable from: 229-4ubuntu12]
systemd-sysv/xenial-updates 229-4ubuntu13 amd64 [upgradable from: 229-4ubuntu12]
ubuntu-software/xenial-updates 3.20.1+git20161013.0.d77d6cf-0ubuntu2~xenial1 amd64 [upgradable from: 3.20.1+git20160923.2.7374bdc-0ubuntu1~xenial1]
udev/xenial-updates 229-4ubuntu13 amd64 [upgradable from: 229-4ubuntu12]

mineelectricity@mineelectricity:~$ sudo apt full-upgrade
Lecture des listes de paquets... Fait
Construction de l'arbre des dépendances       
Lecture des informations d'état... Fait
Calcul de la mise à jour... Fait
Les NOUVEAUX paquets suivants seront installés :
  libsnapd-glib1 snapd-login-service
Les paquets suivants seront mis à jour :
  deja-dup deja-dup-backend-gvfs gnome-software gnome-software-common libpam-systemd libsystemd-dev libsystemd0 libsystemd0:i386 libudev-dev libudev1
  libudev1:i386 linux-firmware python3-software-properties software-properties-common software-properties-gtk systemd systemd-sysv ubuntu-software udev
19 mis à jour, 2 nouvellement installés, 0 à enlever et 0 non mis à jour.
Il est nécessaire de prendre 43,5 Mo/46,1 Mo dans les archives.
Après cette opération, 182 ko d'espace disque supplémentaires seront utilisés.
Souhaitez-vous continuer ? [O/n] 
Réception de:1 http://fr.archive.ubuntu.com/ubuntu xenial-updates/main amd64 libsystemd-dev amd64 229-4ubuntu13 [159 kB]
Réception de:2 http://fr.archive.ubuntu.com/ubuntu xenial-updates/main amd64 libpam-systemd amd64 229-4ubuntu13 [115 kB]
Réception de:3 http://fr.archive.ubuntu.com/ubuntu xenial-updates/main amd64 libudev1 amd64 229-4ubuntu13 [55,1 kB]
Réception de:4 http://fr.archive.ubuntu.com/ubuntu xenial-updates/main i386 libudev1 i386 229-4ubuntu13 [58,4 kB]
Réception de:5 http://fr.archive.ubuntu.com/ubuntu xenial-updates/main amd64 libudev-dev amd64 229-4ubuntu13 [150 kB]
Réception de:6 http://fr.archive.ubuntu.com/ubuntu xenial-updates/main amd64 udev amd64 229-4ubuntu13 [991 kB]
Réception de:7 http://fr.archive.ubuntu.com/ubuntu xenial-updates/main i386 libsystemd0 i386 229-4ubuntu13 [223 kB]
Réception de:8 http://fr.archive.ubuntu.com/ubuntu xenial-updates/main amd64 libsystemd0 amd64 229-4ubuntu13 [205 kB]
Réception de:9 http://fr.archive.ubuntu.com/ubuntu xenial-updates/main amd64 systemd amd64 229-4ubuntu13 [3 615 kB]
Réception de:10 http://fr.archive.ubuntu.com/ubuntu xenial-updates/main amd64 systemd-sysv amd64 229-4ubuntu13 [12,6 kB]                                          
Réception de:11 http://fr.archive.ubuntu.com/ubuntu xenial-updates/main amd64 deja-dup amd64 34.2-0ubuntu1.1 [297 kB]                                             
Réception de:12 http://fr.archive.ubuntu.com/ubuntu xenial-updates/universe amd64 deja-dup-backend-gvfs all 34.2-0ubuntu1.1 [3 436 B]                             
Réception de:13 http://fr.archive.ubuntu.com/ubuntu xenial-updates/main amd64 linux-firmware all 1.157.6 [37,6 MB]                                                
Réception de:14 http://fr.archive.ubuntu.com/ubuntu xenial-updates/main amd64 software-properties-common all 0.96.20.5 [9 432 B]                                  
Réception de:15 http://fr.archive.ubuntu.com/ubuntu xenial-updates/main amd64 software-properties-gtk all 0.96.20.5 [47,2 kB]                                     
Réception de:16 http://fr.archive.ubuntu.com/ubuntu xenial-updates/main amd64 python3-software-properties all 0.96.20.5 [19,9 kB]                                 
43,5 Mo réceptionnés en 48s (898 ko/s)                                                                                                                            
(Lecture de la base de données... 475748 fichiers et répertoires déjà installés.)
Préparation du dépaquetage de .../libsystemd-dev_229-4ubuntu13_amd64.deb ...
Dépaquetage de libsystemd-dev:amd64 (229-4ubuntu13) sur (229-4ubuntu12) ...
Préparation du dépaquetage de .../libpam-systemd_229-4ubuntu13_amd64.deb ...
Dépaquetage de libpam-systemd:amd64 (229-4ubuntu13) sur (229-4ubuntu12) ...
Préparation du dépaquetage de .../libudev1_229-4ubuntu13_i386.deb ...
Déconfiguration de libudev1:amd64 (229-4ubuntu12) ...
Dépaquetage de libudev1:i386 (229-4ubuntu13) sur (229-4ubuntu12) ...
Préparation du dépaquetage de .../libudev1_229-4ubuntu13_amd64.deb ...
Dépaquetage de libudev1:amd64 (229-4ubuntu13) sur (229-4ubuntu12) ...
Traitement des actions différées (« triggers ») pour man-db (2.7.5-1) ...
Traitement des actions différées (« triggers ») pour libc-bin (2.23-0ubuntu5) ...
Paramétrage de libudev1:amd64 (229-4ubuntu13) ...
Paramétrage de libudev1:i386 (229-4ubuntu13) ...
Traitement des actions différées (« triggers ») pour libc-bin (2.23-0ubuntu5) ...
(Lecture de la base de données... 475748 fichiers et répertoires déjà installés.)
Préparation du dépaquetage de .../libudev-dev_229-4ubuntu13_amd64.deb ...
Dépaquetage de libudev-dev:amd64 (229-4ubuntu13) sur (229-4ubuntu12) ...
Préparation du dépaquetage de .../udev_229-4ubuntu13_amd64.deb ...
Dépaquetage de udev (229-4ubuntu13) sur (229-4ubuntu12) ...
Préparation du dépaquetage de .../libsystemd0_229-4ubuntu13_amd64.deb ...
Déconfiguration de libsystemd0:i386 (229-4ubuntu12) ...........................................................................................................] 
Dépaquetage de libsystemd0:amd64 (229-4ubuntu13) sur (229-4ubuntu12) ..........................................................................................] 
Préparation du dépaquetage de .../libsystemd0_229-4ubuntu13_i386.deb ..........................................................................................] 
Dépaquetage de libsystemd0:i386 (229-4ubuntu13) sur (229-4ubuntu12) ...
Préparation du dépaquetage de .../systemd_229-4ubuntu13_amd64.deb ...
Dépaquetage de systemd (229-4ubuntu13) sur (229-4ubuntu12) ...
Traitement des actions différées (« triggers ») pour man-db (2.7.5-1) ...
Traitement des actions différées (« triggers ») pour ureadahead (0.100.0-19) ...
ureadahead will be reprofiled on next reboot
Traitement des actions différées (« triggers ») pour libc-bin (2.23-0ubuntu5) ...
Paramétrage de libsystemd0:amd64 (229-4ubuntu13) ...
Paramétrage de libsystemd0:i386 (229-4ubuntu13) ...
Paramétrage de systemd (229-4ubuntu13) ...
addgroup: Le groupe « systemd-journal » existe déjà en tant que groupe système. Fin de la procédure.
Traitement des actions différées (« triggers ») pour dbus (1.10.6-1ubuntu3.1) ...
Traitement des actions différées (« triggers ») pour libc-bin (2.23-0ubuntu5) ...
(Lecture de la base de données... 475736 fichiers et répertoires déjà installés.)
Préparation du dépaquetage de .../systemd-sysv_229-4ubuntu13_amd64.deb ...
Dépaquetage de systemd-sysv (229-4ubuntu13) sur (229-4ubuntu12) ...
Traitement des actions différées (« triggers ») pour man-db (2.7.5-1) ...
Paramétrage de systemd-sysv (229-4ubuntu13) ...
(Lecture de la base de données... 475736 fichiers et répertoires déjà installés.)
Préparation du dépaquetage de .../deja-dup_34.2-0ubuntu1.1_amd64.deb ...
Dépaquetage de deja-dup (34.2-0ubuntu1.1) sur (34.2-0ubuntu1) ...
Préparation du dépaquetage de .../deja-dup-backend-gvfs_34.2-0ubuntu1.1_all.deb ...
Dépaquetage de deja-dup-backend-gvfs (34.2-0ubuntu1.1) sur (34.2-0ubuntu1) ...
Préparation du dépaquetage de .../ubuntu-software_3.20.1+git20161013.0.d77d6cf-0ubuntu2~xenial1_amd64.deb ...
Dépaquetage de ubuntu-software (3.20.1+git20161013.0.d77d6cf-0ubuntu2~xenial1) sur (3.20.1+git20160923.2.7374bdc-0ubuntu1~xenial1) ...
Préparation du dépaquetage de .../gnome-software_3.20.1+git20161013.0.d77d6cf-0ubuntu2~xenial1_amd64.deb ...
Dépaquetage de gnome-software (3.20.1+git20161013.0.d77d6cf-0ubuntu2~xenial1) sur (3.20.1+git20160923.2.7374bdc-0ubuntu1~xenial1) ...
Préparation du dépaquetage de .../gnome-software-common_3.20.1+git20161013.0.d77d6cf-0ubuntu2~xenial1_all.deb ...
Dépaquetage de gnome-software-common (3.20.1+git20161013.0.d77d6cf-0ubuntu2~xenial1) sur (3.20.1+git20160923.2.7374bdc-0ubuntu1~xenial1) ...
Sélection du paquet libsnapd-glib1:amd64 précédemment désélectionné.
Préparation du dépaquetage de .../libsnapd-glib1_1.2-0ubuntu1.1~xenial_amd64.deb ...
Dépaquetage de libsnapd-glib1:amd64 (1.2-0ubuntu1.1~xenial) ...
Préparation du dépaquetage de .../linux-firmware_1.157.6_all.deb ...
Dépaquetage de linux-firmware (1.157.6) sur (1.157.5) ...
Préparation du dépaquetage de .../software-properties-common_0.96.20.5_all.deb ...
Dépaquetage de software-properties-common (0.96.20.5) sur (0.96.20.4) ...
Préparation du dépaquetage de .../software-properties-gtk_0.96.20.5_all.deb ...
Dépaquetage de software-properties-gtk (0.96.20.5) sur (0.96.20.4) ...
Préparation du dépaquetage de .../python3-software-properties_0.96.20.5_all.deb ...
Dépaquetage de python3-software-properties (0.96.20.5) sur (0.96.20.4) ...
Sélection du paquet snapd-login-service précédemment désélectionné.
Préparation du dépaquetage de .../snapd-login-service_1.2-0ubuntu1.1~xenial_amd64.deb ...
Dépaquetage de snapd-login-service (1.2-0ubuntu1.1~xenial) ...
Traitement des actions différées (« triggers ») pour hicolor-icon-theme (0.15-0ubuntu1) ...
Traitement des actions différées (« triggers ») pour gconf2 (3.2.6-3ubuntu6) ...
Traitement des actions différées (« triggers ») pour libglib2.0-0:i386 (2.48.1-1~ubuntu16.04.1) ...
Traitement des actions différées (« triggers ») pour libglib2.0-0:amd64 (2.48.1-1~ubuntu16.04.1) ...
Traitement des actions différées (« triggers ») pour bamfdaemon (0.5.3~bzr0+16.04.20160824-0ubuntu1) ...
Rebuilding /usr/share/applications/bamf-2.index...
Traitement des actions différées (« triggers ») pour gnome-menus (3.13.3-6ubuntu3.1) ...
Traitement des actions différées (« triggers ») pour desktop-file-utils (0.22-1ubuntu5) ...
Traitement des actions différées (« triggers ») pour mime-support (3.59ubuntu1) ...
Traitement des actions différées (« triggers ») pour man-db (2.7.5-1) ...
Traitement des actions différées (« triggers ») pour libc-bin (2.23-0ubuntu5) ...
Traitement des actions différées (« triggers ») pour dbus (1.10.6-1ubuntu3.1) ...
Traitement des actions différées (« triggers ») pour shared-mime-info (1.5-2ubuntu0.1) ...
Paramétrage de libsystemd-dev:amd64 (229-4ubuntu13) ...
Paramétrage de libpam-systemd:amd64 (229-4ubuntu13) ...
Paramétrage de libudev-dev:amd64 (229-4ubuntu13) ...
Paramétrage de udev (229-4ubuntu13) ...
addgroup: Le groupe « input » existe déjà en tant que groupe système. Fin de la procédure.
update-initramfs: deferring update (trigger activated)
Paramétrage de deja-dup (34.2-0ubuntu1.1) ...
Paramétrage de deja-dup-backend-gvfs (34.2-0ubuntu1.1) ...
Paramétrage de gnome-software-common (3.20.1+git20161013.0.d77d6cf-0ubuntu2~xenial1) ...
Paramétrage de libsnapd-glib1:amd64 (1.2-0ubuntu1.1~xenial) ...
Paramétrage de gnome-software (3.20.1+git20161013.0.d77d6cf-0ubuntu2~xenial1) ...
Paramétrage de ubuntu-software (3.20.1+git20161013.0.d77d6cf-0ubuntu2~xenial1) ...
Paramétrage de linux-firmware (1.157.6) ...
update-initramfs: Generating /boot/initrd.img-4.4.0-53-generic
update-initramfs: Generating /boot/initrd.img-4.4.0-51-generic
update-initramfs: Generating /boot/initrd.img-3.19.0-58-generic
Paramétrage de python3-software-properties (0.96.20.5) ...
Paramétrage de software-properties-common (0.96.20.5) ...
Paramétrage de software-properties-gtk (0.96.20.5) ...
Paramétrage de snapd-login-service (1.2-0ubuntu1.1~xenial) ...
Traitement des actions différées (« triggers ») pour initramfs-tools (0.122ubuntu8.5) ...
update-initramfs: Generating /boot/initrd.img-4.4.0-53-generic
Traitement des actions différées (« triggers ») pour libc-bin (2.23-0ubuntu5) ...
Traitement des actions différées (« triggers ») pour dbus (1.10.6-1ubuntu3.1) ...
```
and tryed more
```
mineelectricity@mineelectricity:~$ sudo rfkill unblock bluetooth && rfkill list bluetooth
1: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
mineelectricity@mineelectricity:~$ sudo rfkill unblock all
mineelectricity@mineelectricity:~$ sudo hciconfig hci0 up
Can't init device hci0: Connection timed out (110)
mineelectricity@mineelectricity:~$ sudo hciconfig hci0 reset
Can't init device hci0: Connection timed out (110)
```

I defenetly think the problem is here (and i'm not alone [http://pastebin.com/1x3ChAhT](http://pastebin.com/1x3ChAhT) )
```
mineelectricity@mineelectricity:~$ hciconfig
hci0:    Type: BR/EDR  Bus: USB
    BD Address: 54:27:1E:0C:53:63  ACL MTU: 820:8  SCO MTU: 255:16
    DOWN 
    RX bytes:1274 acl:0 sco:0 events:129 errors:0
    TX bytes:25311 acl:0 sco:0 commands:136 errors:0
$ lsusb -v
[...]
Bus 003 Device 002: ID 13d3:3394 IMC Networks Bluetooth
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass          224 Wireless
  bDeviceSubClass         1 Radio Frequency
  bDeviceProtocol         1 Bluetooth
  bMaxPacketSize0        64
  idVendor           0x13d3 IMC Networks
  idProduct          0x3394 Bluetooth
  bcdDevice            2.00
  iManufacturer           1 Realtek
  iProduct                2 RT Bluetooth Radio
  iSerial                 3 00e04c000001
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength          177
    bNumInterfaces          2
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0xe0
      Self Powered
      Remote Wakeup
    MaxPower              500mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           3
      bInterfaceClass       224 Wireless
      bInterfaceSubClass      1 Radio Frequency
      bInterfaceProtocol      1 Bluetooth
      iInterface              4 Bluetooth Radio
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0010  1x 16 bytes
        bInterval               1
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x02  EP 2 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x82  EP 2 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               0
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        1
      bAlternateSetting       0
      bNumEndpoints           2
      bInterfaceClass       224 Wireless
      bInterfaceSubClass      1 Radio Frequency
      bInterfaceProtocol      1 Bluetooth
      iInterface              4 Bluetooth Radio
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x03  EP 3 OUT
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0000  1x 0 bytes
        bInterval               1
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x83  EP 3 IN
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0000  1x 0 bytes
        bInterval               1
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        1
      bAlternateSetting       1
      bNumEndpoints           2
      bInterfaceClass       224 Wireless
      bInterfaceSubClass      1 Radio Frequency
      bInterfaceProtocol      1 Bluetooth
      iInterface              4 Bluetooth Radio
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x03  EP 3 OUT
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0009  1x 9 bytes
        bInterval               1
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x83  EP 3 IN
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0009  1x 9 bytes
        bInterval               1
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        1
      bAlternateSetting       2
      bNumEndpoints           2
      bInterfaceClass       224 Wireless
      bInterfaceSubClass      1 Radio Frequency
      bInterfaceProtocol      1 Bluetooth
      iInterface              4 Bluetooth Radio
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x03  EP 3 OUT
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0011  1x 17 bytes
        bInterval               1
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x83  EP 3 IN
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0011  1x 17 bytes
        bInterval               1
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        1
      bAlternateSetting       3
      bNumEndpoints           2
      bInterfaceClass       224 Wireless
      bInterfaceSubClass      1 Radio Frequency
      bInterfaceProtocol      1 Bluetooth
      iInterface              4 Bluetooth Radio
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x03  EP 3 OUT
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0019  1x 25 bytes
        bInterval               1
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x83  EP 3 IN
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0019  1x 25 bytes
        bInterval               1
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        1
      bAlternateSetting       4
      bNumEndpoints           2
      bInterfaceClass       224 Wireless
      bInterfaceSubClass      1 Radio Frequency
      bInterfaceProtocol      1 Bluetooth
      iInterface              4 Bluetooth Radio
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x03  EP 3 OUT
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0021  1x 33 bytes
        bInterval               1
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x83  EP 3 IN
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0021  1x 33 bytes
        bInterval               1
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        1
      bAlternateSetting       5
      bNumEndpoints           2
      bInterfaceClass       224 Wireless
      bInterfaceSubClass      1 Radio Frequency
      bInterfaceProtocol      1 Bluetooth
      iInterface              4 Bluetooth Radio
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x03  EP 3 OUT
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0031  1x 49 bytes
        bInterval               1
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x83  EP 3 IN
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0031  1x 49 bytes
        bInterval               1
Device Status:     0x0001
  Self Powered
[...]
```

and I've tryed more things like 
```
mineelectricity@mineelectricity:~$ sudo bluetoothctl 
[sudo] Mot de passe de mineelectricity : 
[NEW] Controller 54:27:1E:0C:53:63 ubuntu-0 [default]
[bluetooth]# power on
Failed to set power on: org.bluez.Error.Failed

```

so my history is now 
```
  436  sudo nautilus
  437  sudo apt install bluetooth
  438  # /etc/init.d/bluetooth status
  439  /etc/init.d/bluetooth status
  440  /etc/init.d/bluetooth start
  441  /etc/init.d/bluetooth status
  442  systemctl status bluetooth
  443  sudo rfkill unblock bluetooth && rfkill list bluetooth
  444  hcitool dev
  445  hciconfig
  446  hcitool scan
  447  sudo hcitool info <AdresseMacPériphérique>
  448  sudo /etc/init.d/networking restart
  449  hcitool scan
  450  hciconfig
  451  hcitool dev
  452  sudo rfkill unblock bluetooth && rfkill list bluetooth
  453  sudo rfkill unblock all
  454  sudo hciconfig hci0 up
  455  sudo /etc/init.d/bluetooth restart
  456  sudo hciconfig hci0 up
  457  uname -a
  458  lspci  -k | grep -A3 Net
  459  sudo apt-get install pulseaudio-module-bluetooth
  460  sudo /etc/init.d/bluetooth restart
  461  history
  462  sudo rfkill unblock bluetooth && rfkill list bluetooth
  463  hcitool dev
  464  hciconfig
  465  hcitool scan
  466  uname -a
  467  uname -a; lspci -nnk | grep -iA2 net; lsusb; dmesg | grep -i bluetooth; dmesg | grep -i firmware; lsmod | grep bluetooth
  468  bluetooth-applet
  469  sudo apt install 
  470  sudo /etc/init.d/bluetooth restart
  471  watch -n 60 synclient TapButton3=3 TapButton2=2
  472  sudo apt update
  473  apt list --upgradable
  474  sudo apt update
  475  sudo apt full-upgrade
  476  sudo reboot
  477  sudo /etc/init.d/bluetooth restart
  478  bluetooth-applet
  479  sudo rfkill unblock bluetooth && rfkill list bluetooth
  480  sudo rfkill unblock all
  481  sudo hciconfig hci0 up
  482  sudo hciconfig hci0 reset
  483  hci0 up
  484  hciconfig 
  485  hciconfig up
  486  hciconfig
  487  sudo hciconfig hci0 up
  488  hciconfig hci0 piscan 
  489  sudo hciconfig hci0 piscan 
  490  sudo     hciconfig hci0 piscan
  491  sudo hciconfig device up
  492  lsusb -v
  493  sudo lsusb -v
  494  bluez
  495  sudo apt install bluez
  496  sudo apt install python-gobject python-dbus
  497  cd  /usr/share/doc/bluez/examples/
  498  hcitool dev
  499  cat /var/lib/NetworkManager/NetworkManager.state
  500  lsmod
  501  usb-devices
  502  hciconfig --all
  503  sudo hcitool scan
  504  sudo apt-get install bluetooth bluez bluez-tools rfkill rfcomm
  505  sudo apt-get install bluetooth bluez bluez-tools rfkill
  506  sudo apt-get install bluez-firmware firmware-realtek
  507  sudo service bluetooth start
  508  sudo rfkill unblock bluetooth
  509  sudo hciconfig hci0 up
  510  bluetoothctl 
  511  sudo bluetoothctl 
  512  sudo hcitool scan
  513  hciconfig --all
  514  history

```

So I know that there is a problem, and that there is no device when I do hcitool dev ... Help ? :eek: :-({|=

---

### Post by minecraft-electricity on 2016-12-19
apparently upgrades between ubuntu versions are bad.
case closed. :3

---

