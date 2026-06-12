---
title: "Network scan problem"
date: 2022-06-07
forum: Networking &amp; Wireless
---

### Post by namichel on 2022-06-07
Hi all

I'm unable to scan with my HP Color LaserJet MFP M480 connected with an Ethernet cable to my network.
An other computer on the same network can scan with no problem.

Printing is OK

I found this info which could match 
[https://alioth-lists.debian.net/pipermail/sane-devel/2009-February/024117.html](https://alioth-lists.debian.net/pipermail/sane-devel/2009-February/024117.html)
But I do not understand which URI I have to use
In the example he give  "Device URI: hp:/net/Officejet_Pro_L7500?ip=192.168.2.9"
What is the name I have to fill ? where should I find it ?

I expect if I understand how to write the URI, I should specify it in the escl.conf file, but actually I'm unable to write it corectly :
$ grep -v "^#" /etc/sane.d/escl.conf 
device hpaio:/net/NPID5AA80?ip=192.168.1.36

Could you please explain to me how to write the corect URI ?

Thanks !


For more information ...

$ cat /etc/lsb-release 
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=21.10
DISTRIB_CODENAME=impish
DISTRIB_DESCRIPTION="Ubuntu 21.10"


$ sudo dpkg -l |grep sane
ii  libsane-common                             1.0.32-3ubuntu1                            all          API library for scanners -- documentation and support files
ii  libsane-dev:amd64                          1.0.32-3ubuntu1                            amd64        API development library for scanners [development files]
rc  libsane-hpaio:amd64                        3.21.6+dfsg0-0ubuntu1                      amd64        HP SANE backend for multi-function peripherals
ii  libsane1:amd64                             1.0.32-3ubuntu1                            amd64        API library for scanners
ii  sane                                       1.0.14-16                                  amd64        scanner graphical frontends
ii  sane-airscan                               0.99.26-2ubuntu1                           amd64        SANE backend for AirScan (eSCL) and WSD document scanner
ii  sane-utils                                 1.0.32-3ubuntu1                            amd64        API library for scanners -- utilities
ii  xsane                                      0.999-11ubuntu1                            amd64        featureful graphical frontend for SANE (Scanner Access Now Easy)
ii  xsane-common                               0.999-11ubuntu1                            all          xsane architecture independent files


$ lpstat -v
matériel pour HP_color : socket://192.168.1.36:9100

$ scanimage -L
No scanners were identified.

I tried to update HPLIP with the last version available on HP dev site

$ dpkg -l |grep hplip
rc  hplip                                      3.21.6+dfsg0-0ubuntu1                      amd64        HP Linux Printing and Imaging System (HPLIP)

Then hp-doctor say : 

---------------------------------
| INSTALLED CUPS PRINTER QUEUES |
---------------------------------
Type: Unknown
Device URI: socket://192.168.1.36:9100

hp-setup say :
HPLIP cannot detect printers in your network.

(even if I can print with no problem)

If I specify an IP, it say : error: No device selected/specified or that supports this functionality.

Here is my printer network config :



[FONT=Courier][SIZE=3]-------- Informations générales --------          ---------------- TCP/IP ----------------
État:                    Carte E/S prête          IPv4:                             Activé
                                                  IPv6:                             Activé
Numéro de modèle:                 J8032E          Nom d'hôte:                    NPID5AA80
Adresse matérielle:         C85ACFD5AA80          Nom de domaine IPv4:                home
Vers. micrologiciel:         JOL25020020          Nom de domaine IPv6:        Non spécifié
LAA:                        C85ACFD5AA80          Serveur DNS principal:       192.168.1.1
Configuration port:       1000T INTÉGRAL          Serveur DNS secondaire:     Non spécifié
Auto-négociation:                    Oui          DNS(IPv6):                              
ID du fabricant:                                  Non spécifié                            
Date de fabrication:             XX/XXXX                                                  
Enregistrement WS:            Enregistré          Serveur WINS:               Non spécifié
Etat WS:                        Connecté          Exp. du délai d'inactivité TCP:  270 sec
HP Connected:                   Autorisé                                                  
Courrier électronique:                            ----------------- IPv4 -----------------
[email]8682hw74kyy@hpeprint.com[/email]                          État:                               Prêt
                                                                                          
-------- Paramètres de sécurité --------                                                  
802.1X:                     Non spécifié          Adresse IP:                 192.168.1.36
IPsec:                         Désactivé          Masque de sous-réseau:     255.255.255.0
Web sécurisé:          HTTPS obligatoire          Passerelle par défaut:                  
Date expiration certif:2027-05-08 22:03           192.168.1.1                             
Versions de SNMP:              Désactivé          Configuration par:                  DHCP
Nom d'appartenance écriture SNMP:Non spé          Serveur DHCP:                192.168.1.1
Obtenir nom de communauté SNMP:Non spéci                                                  
                                                  Nom du service Bonjour:                 
Mot de passe Admin:         Non spécifié          HP Color LaserJet MFP M480 [D5AA80]     
Agent d'annonce:                   Echec                                                  
                                                  ----------------- IPv6 -----------------
Mode protégé DNS:                    Non          État:                               Prêt
Pare-feu:                      Désactivé                                                  
                                                                                          
--------- Statistiques réseau ----------          Lien local:                             
Total des paquets reçus:           55308          fe80::ca5a:cfff:fed5:aa80               
                                                  Sans état:                              
Mauvais paquets reçus:                 0          2a02:1210:7a33:6000:ca5a:cfff:fed5:aa80 
Total des paquets transmis:        53193                                                  
                                                                                          
Paquets intransmissibles:              0                                                  
                                                  DHCPv6:                                 
                                                  Non configuré                           
                                                  Manuel:                                 
                                                  Non configuré                           
                                                                                          
[/SIZE][/FONT]

---

