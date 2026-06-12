---
title: "Qualcomm Atheros QCA6174 in Ubuntu 16.04 WLAN drops randomly"
date: 2017-01-08
forum: Networking &amp; Wireless
---

### Post by harlock593 on 2017-01-08
Hello, i have an issue while loading flash animations on firefox nightly. instead of getting the flash game or animation, i get a brown with yellow writings telling me failed to load libpepperflashpalyer.so

i don't know what i made wrong i maybe tried to enable pepper flash on chromium the wrong way but now i can't play any flash on firefox trunk (nightly)

my version of firefox is 53.0a1

Here is the pepper flash i installed and i'll show what flash is installed too

```
harlock59@Aspire-chbre:~$ aptitude search pepper
i   browser-plugin-freshplayer-pepperflash                                                  - PPAPI-host NPAPI-plugin adapter for pepperflash                                                   
p   browser-plugin-freshplayer-pepperflash:i386                                             - PPAPI-host NPAPI-plugin adapter for pepperflash                                                   
p   libjs-jquery-ui-theme-pepper-grinder                                                    - Thème Pepper Grinder pour jQuery UI                                                               
p   pepper                                                                                  - Outil de rapport et de statistiques de dépôt de code source                                       
p   pepper:i386                                                                             - Outil de rapport et de statistiques de dépôt de code source                                       
i   pepperflashplugin-nonfree                                                               - Pepper Flash Player - greffon de navigateur                                                       
harlock59@Aspire-chbre:~$ aptitude search pep
i   browser-plugin-freshplayer-pepperflash                                                  - PPAPI-host NPAPI-plugin adapter for pepperflash                                                   
p   browser-plugin-freshplayer-pepperflash:i386                                             - PPAPI-host NPAPI-plugin adapter for pepperflash                                                   
p   golang-github-rogpeppe-fastuuid-dev                                                     - fast generation of 192-bit UUIDs                                                                  
v   golang-github-rogpeppe-go-charset-dev                                                   -                                                                                                   
p   libfsharp-data-typeproviders4.4-cil                                                     - functional-first programming language - data integration library                                  
p   libjs-jquery-ui-theme-pepper-grinder                                                    - Thème Pepper Grinder pour jQuery UI                                                               
p   pep8                                                                                    - Python PEP 8 code style checker - transitional package                                            
p   pepper                                                                                  - Outil de rapport et de statistiques de dépôt de code source                                       
p   pepper:i386                                                                             - Outil de rapport et de statistiques de dépôt de code source                                       
i   pepperflashplugin-nonfree                                                               - Pepper Flash Player - greffon de navigateur                                                       
p   python-autopep8                                                                         - tool that automatically formats Python code to conform to PEP 8                                   
p   python-pep8                                                                             - Python PEP 8 code style checker - Python                                                          
p   python-pep8-naming                                                                      - check for PEP 8 naming conventions (flake8 plugin for Python2)                                    
p   python3-pep8                                                                            - Python PEP 8 code style checker - Python 3                                                        
p   python3-pep8-naming                                                                     - check for PEP 8 naming conventions (flake8 plugin for Python3)                                    
p   vim-autopep8                                                                            - vim plugin to apply autopep8                                                                      
harlock59@Aspire-chbre:~$
```
```

harlock59@Aspire-chbre:~$ aptitude search flash
v   adobe-flash-properties                                                                  -                                                                                                   
v   adobe-flash-properties:i386                                                             -                                                                                                   
p   adobe-flash-properties-gtk                                                              - GTK+ control panel for Adobe Flash Player plugin                                                  
p   adobe-flash-properties-gtk:i386                                                         - GTK+ control panel for Adobe Flash Player plugin                                                  
p   adobe-flash-properties-kde                                                              - KDE control panel Adobe Flash Player plugin                                                       
p   adobe-flash-properties-kde:i386                                                         - KDE control panel Adobe Flash Player plugin                                                       
p   adobe-flashplugin                                                                       - Adobe Flash Player plugin                                                                         
p   adobe-flashplugin:i386                                                                  - Adobe Flash Player plugin                                                                         
i   browser-plugin-freshplayer-pepperflash                                                  - PPAPI-host NPAPI-plugin adapter for pepperflash                                                   
p   browser-plugin-freshplayer-pepperflash:i386                                             - PPAPI-host NPAPI-plugin adapter for pepperflash                                                   
v   firefox-video-without-flash                                                             -                                                                                                   
p   flashbake                                                                               - automated snapshots with git                                                                      
p   flashbench                                                                              - identify flash storage properties                                                                 
p   flashbench:i386                                                                         - identify flash storage properties                                                                 
p   flashcache-dkms                                                                         - write-back block device cache for Linux (DKMS version)                                            
p   flashcache-utils                                                                        - write-back block device cache for Linux (user space utilities)                                    
p   flashcache-utils:i386                                                                   - write-back block device cache for Linux (user space utilities)                                    
v   flashplugin-downloader                                                                  -                                                                                                   
p   flashplugin-downloader:i386                                                             - Installation du plugin Adobe Flash Player (paquet de transition)                                  
i   flashplugin-installer                                                                   - Installeur du greffon Adobe « Flash Player »                                                      
p   flashplugin-installer:i386                                                              - Installeur du greffon Adobe « Flash Player »                                                      
v   flashplugin-nonfree                                                                     -                                                                                                   
v   flashplugin-nonfree:i386                                                                -                                                                                                   
p   flashplugin-nonfree-extrasound                                                          - Bibliothèque de prise en charge de la plateforme Adobe Flash Player pour Esound et OSS            
p   flashplugin-nonfree-extrasound:i386                                                     - Bibliothèque de prise en charge de la plateforme Adobe Flash Player pour Esound et OSS            
p   flashproxy-client                                                                       - Pluggable transport to circumvent IP address blocking - client transport plugin                   
p   flashproxy-common                                                                       - Pluggable transport to circumvent IP address blocking - common library                            
p   flashproxy-facilitator                                                                  - Pluggable transport to circumvent IP address blocking - facilitator                               
p   flashproxy-proxy                                                                        - Pluggable transport to circumvent IP address blocking - browser proxy                             
p   flashrom                                                                                - Identify, read, write, erase, and verify BIOS/ROM/flash chips                                     
p   flashrom:i386                                                                           - Identify, read, write, erase, and verify BIOS/ROM/flash chips                                     
p   flashybrid                                                                              - automatise l'utilisation d'un disque flash comme système de fichiers racine                       
p   get-flash-videos                                                                        - Téléchargeur de vidéos pour différents sites d'hébergement de vidéos en Flash                     
p   gnome-flashback                                                                         - GNOME Flashback application                                                                       
p   gnome-flashback:i386                                                                    - GNOME Flashback application                                                                       
p   gnome-flashback-common                                                                  - GNOME Flashback application - common data files                                                   
p   gnome-session-flashback                                                                 - Gestionnaire de session GNOME - Session GNOME Flashback                                           
p   heimdall-flash                                                                          - Outil de flashage du microprogramme sur les périphériques Samsung Galaxy S                        
p   heimdall-flash:i386                                                                     - Outil de flashage du microprogramme sur les périphériques Samsung Galaxy S                        
p   heimdall-flash-frontend                                                                 - Outil de flashage du microprogramme sur les périphériques Samsung Galaxy S - interface graphique Q
p   heimdall-flash-frontend:i386                                                            - Outil de flashage du microprogramme sur les périphériques Samsung Galaxy S - interface graphique Q
p   libdancer-plugin-flashmessage-perl                                                      - Dancer plugin to display temporary, so called "flash messages"                                    
p   libhal1-flash                                                                           - Compatibility library to allow playback of Flash DRM content                                      
p   libhal1-flash:i386                                                                      - Compatibility library to allow playback of Flash DRM content                                      
p   lm4flash                                                                                - Command-line firmware flashing tool to communicate with the Stellaris Launchpad                   
p   lm4flash:i386                                                                           - Command-line firmware flashing tool to communicate with the Stellaris Launchpad                   
p   m16c-flash                                                                              - programmeur flash pour microcontrôleurs Renesas M16C et R8C                                       
p   m16c-flash:i386                                                                         - programmeur flash pour microcontrôleurs Renesas M16C et R8C                                       
p   node-flashproxy                                                                         - Pluggable transport to circumvent IP address blocking - nodejs proxy                              
i   pepperflashplugin-nonfree                                                               - Pepper Flash Player - greffon de navigateur                                                       
p   python-webflash                                                                         - Portable flash messages for Python WSGI applications                                              
p   rkflashtool                                                                             - Tools for flashing Rockchip devices                                                               
p   rkflashtool:i386                                                                        - Tools for flashing Rockchip devices                                                               
p   ruby-rack-flash3                                                                        - Flash hash for Ruby Rack applications                                                             
p   stm32flash                                                                              - STM32 chip flashing utility using a serial bootloader                                             
p   stm32flash:i386                                                                         - STM32 chip flashing utility using a serial bootloader                                             
p   ubuntu-device-flash                                                                     - Flash supported devices with Ubuntu                                                               
p   ubuntu-device-flash:i386                                                                - Flash supported devices with Ubuntu                                                               
v   video-without-flash                                                                     -                                                                                                   
p   xul-ext-video-without-flash                                                             - extension to watch videos without the Flash plugin                                                
harlock59@Aspire-chbre:~$ 
```

```
harlock59@Aspire-chbre:~$ aptitude search gnash
p   browser-plugin-gnash            - lecteur GNU Shockwave Flash (SWF) - greffo
p   browser-plugin-gnash:i386       - lecteur GNU Shockwave Flash (SWF) - greffo
i   gnash                           - Lecteur Shockwave Flash (SWF) GNU         
p   gnash:i386                      - Lecteur Shockwave Flash (SWF) GNU         
i   gnash-common                    - Lecteur Shockwave Flash (SWF) GNU - fichie
p   gnash-common:i386               - Lecteur Shockwave Flash (SWF) GNU - fichie
p   gnash-common-opengl             - Paquet factice pour le retrait de gnash-co
p   gnash-cygnal                    - Lecteur Shockwave Flash (SWF) GNU - serveu
p   gnash-cygnal:i386               - Lecteur Shockwave Flash (SWF) GNU - serveu
p   gnash-dbg                       - Lecteur Shockwave Flash (SWF) GNU - symbol
p   gnash-dbg:i386                  - Lecteur Shockwave Flash (SWF) GNU - symbol
p   gnash-dev                       - Lecteur Shockwave Flash (SWF) GNU - Fichie
p   gnash-dev:i386                  - Lecteur Shockwave Flash (SWF) GNU - Fichie
p   gnash-doc                       - Lecteur Shockwave Flash (SWF) GNU - docume
p   gnash-ext-fileio                - Lecteur Shockwave Flash (SWF) GNU - extens
p   gnash-ext-fileio:i386           - Lecteur Shockwave Flash (SWF) GNU - extens
p   gnash-ext-lirc                  - GNU Shockwave Flash (SWF) player - LIRC ex
p   gnash-ext-lirc:i386             - GNU Shockwave Flash (SWF) player - LIRC ex
p   gnash-ext-mysql                 - GNU Shockwave Flash (SWF) player - MySQL e
p   gnash-ext-mysql:i386            - GNU Shockwave Flash (SWF) player - MySQL e
p   gnash-opengl                    - Paquet factice pour le retrait de gnash-op
p   gnash-tools                     - Lecteur Shockwave Flash (SWF) GNU - outils
p   gnash-tools:i386                - Lecteur Shockwave Flash (SWF) GNU - outils
i   konqueror-plugin-gnash          - Lecteur Shockwave Flash (SWF) GNU - plugin
p   konqueror-plugin-gnash:i386     - Lecteur Shockwave Flash (SWF) GNU - plugin
v   libgnash0                       -                                           
v   libgnash0:i386                  -                                           
p   mozilla-plugin-gnash            - Paquet factice pour le changement de nom e
v   mozilla-plugin-gnash:i386       -                                           
p   python-gtk-gnash                - GNU Shockwave Flash (SWF) player - Python 
p   python-gtk-gnash:i386           - GNU Shockwave Flash (SWF) player - Python 
v   python2.7-gtk-gnash             -                                           
v   python2.7-gtk-gnash:i386        -                                           
harlock59@Aspire-chbre:~$ 


```

---

