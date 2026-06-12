---
title: "Apt unmet dependencies wants to uninstall all of my KDE programs"
date: 2009-01-29
forum: New to Ubuntu
---

### Post by Firestem4 on 2009-01-29
I recently upgraded to KDE4.2 and in the installation guide iw as told to uninstall koffice. I removed and now that I am trying to reinstall koffice, this is what i get.
```
icarus@icarus-linux:~$ sudo apt-get install koffice
[sudo] password for icarus:                        
Reading package lists... Done                      
Building dependency tree                           
Reading state information... Done                  
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.                                    

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against         
that package should be filed.                                          
The following information may help to resolve the situation:           

The following packages have unmet dependencies:
  koffice: Depends: kformula (>= 1:1.6.3-6ubuntu3) but it is not going to be installed                                                                              
E: Broken packages                                                                
icarus@icarus-linux:~$ sudo apt-get install kformula
Reading package lists... Done                       
Building dependency tree
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libsbigudrv0 kdeartwork-misc kdegames-card-data libcfitsio3 xscreensaver-gl
  xscreensaver libcln5 kdegames-mahjongg-data libqalculate4 kdeartwork-emoticons
  kdewallpapers kstars-data indi libjpeg-progs xscreensaver-data
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  koffice-data koffice-libs latex-xft-fonts
Suggested packages:
  wordnet tetex-extra
The following packages will be REMOVED:
  adept akonadi-kde akregator ark basket bomber bovo dolphin dragonplayer
  gdebi-kde guidance-power-manager gwenview install-package jockey-kde
  kaddressbook kamera kapman kate katomic kbattleship kblackbox kblocks kbounce
  kbreakout kde-core kde-printer-applet kde-window-manager kde-zeroconf
  kdeartwork kdeartwork-style kdebase-bin kdebase-data kdebase-plasma
  kdebase-runtime kdebase-runtime-bin-kde4 kdebase-workspace
  kdebase-workspace-bin kdebase-workspace-libs4+5 kdebluetooth kdegames
  kdegraphics-strigi-plugins kdelibs-bin kdelibs5 kdemultimedia-kio-plugins
  kdepasswd kdepim-kresources kdepim-strigi-plugins kdepim-wizards kdepimlibs5
  kdeplasma-addons kdesudo kdiamond kdm kfind kfourinline kgoldrunner
  kgrubeditor khelpcenter4 killbots kinfocenter kiriki kjumpingcube klines
  klipper kmag kmahjongg kmail kmines kmix kmousetool knetwalk knotes kolf
  kollision konqueror konqueror-nsplugins konqueror-plugin-searchbar konquest
  konsole kontact korganizer kpat krdc kreversi krfb ksame kscreensaver
  kscreensaver-xsavers kshisen ksirk ksnapshot kspaceduel ksquares kstars
  ksudoku ksysguard ksystemlog ktimetracker ktorrent ktuberling kubrick
  kubuntu-docs kubuntu-konqueror-shortcuts kuser kvkbd kwalletmanager kwin
  language-selector-qt libkcddb4 libkdecorations4 libkdeedu4 libkdegames5
  libkdepim4 libkexiv2-7 libkholidays4 libkipi5 libkleo4 libkonq5 libkpgp4
  libksieve4 libkwineffects1 libmaildir4 libmimelib4 libokularcore1 libplasma3
  lskat okular okular-extra-backends plasmoid-quickaccess python-kde4
  software-properties-kde step superkaramba sweeper system-config-printer-kde
  systemsettings update-manager-kde update-notifier-kde xorg
The following NEW packages will be installed:
  kformula koffice-data koffice-libs latex-xft-fonts
0 upgraded, 4 newly installed, 139 to remove and 0 not upgraded.
Need to get 4377kB of archives.
After this operation, 257MB disk space will be freed.
Do you want to continue [Y/n]? n
Abort.
icarus@icarus-linux:~$

```

Can anyone help me figure this problem out? 

Thanks in advance.

---

### Post by yeats on 2009-01-30
so how did you go about getting/installing KDE 4.2?  If from source, this would explain why the dependencies are unmet.  Or did you add a special repository?

---

### Post by Firestem4 on 2009-02-02
I removed koffice as a whole, even though the guide said i only need to remove 1 thing. However apt- didn't find that package installed. So i felt like playing it safe and removed KOffice before I installed KDE4.2.

I added the repository from Kubuntu to download the KDE4.2 desktop (there is  an installation guide on kubuntu.org)

---

