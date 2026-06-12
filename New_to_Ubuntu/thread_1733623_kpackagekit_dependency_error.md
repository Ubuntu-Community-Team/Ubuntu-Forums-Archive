---
title: "kpackagekit dependency error"
date: 2011-04-19
forum: New to Ubuntu
---

### Post by flurry21 on 2011-04-19
any one can  help me  with this error 


```

maverick@maverick:~$ sudo apt-get install kpackagekit
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 kpackagekit : Depends:[COLOR=Lime] [/COLOR][COLOR=Lime]software-properties-kde [/COLOR]but it is not going to be installed
E: Broken packages


maverick@maverick:~$ sudo apt-get install software-properties-kde
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 software-properties-kde : Depends: [COLOR=Lime]qapt-batch[/COLOR] but it is not going to be installed
E: Broken packages


maverick@maverick:~$ sudo apt-get install qapt-batch
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 qapt-batch : Depends: libqapt-runtime but it is not going to be installed
E: Broken packages


maverick@maverick:~$ sudo apt-get install libqapt-runtime
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 libqapt-runtime : Depends: libpolkit-qt-1-0 but it is not going to be installed
E: Broken packages


maverick@maverick:~$ sudo apt-get install[COLOR=Lime] libpolkit-qt-1-0[/COLOR]
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  desktop-base konq-plugins-l10n libmarblewidget11 libkldap4 libktnef4 libkpimtextedit4
  libkcalutils4 libmicroblog4 libdesktop-agnostic0 libjpeg8 libkipi8 libdiscid0 libotr2
  fortunes-min libdesktop-agnostic-cfg-gconf libkleo4 plasma-desktopthemes-artwork
  libboost-program-options1.42.0 mysql-client-core-5.1 xscreensaver plasma-dataengines-addons
  amarok-common libmimelib4 libkexiv2-9 fortune-mod libkcddb4 cairo-dock-data libloudmouth1-0
  mysql-server-core-5.1 librecode0 libkcalcore4 libqtscript4-core libdesktop-agnostic-vfs-gio
  libkpgp4 libqgpgme1 libmailtransport4 libakonadi-kde4 libkabc4 aumix libkresources4
  cairo-dock-core libkpimutils4 libdesktop-agnostic-fdo-glib oss-compat kdewallpapers
  konqueror-plugin-searchbar libksieve4 kdegraphics-libs-data libkpimidentities4
  libqtscript4-gui libqtscript4-uitools libkcal4 aumix-common libtunepimp5
  plasma-widget-message-indicator libindicate-qt0 libkimap4 libpoppler-qt4-3 thunar-data
  libqtscript4-sql ksysguardd libkmime4 libqtscript4-xml libakonadi-contact4 libakonadi-kabc4
  akonadi-server libqca2-plugin-ossl plasma-widget-folderview libokularcore1 libtag-extras1
  liblastfm0 libmessagecore4 marble-data libjpeg-progs libakonadiprotocolinternals1
  kdebase-workspace-wallpapers libakonadi-kcal4 amarok-utils libsyndication4 libgtkglext1
  libexo-common libakonadi-kmime4 libqtscript4-network libetpan13 kdepimlibs-kio-plugins
  libmsn0.3 libgpgme++2 libdmtx0a libmusicbrainz3-6 libkontactinterface4
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  akregator amarok ark dolphin dragonplayer firefox-kde-support gwenview jockey-kde juk
  kaddressbook kate kcalc kde-plasma-desktop kde-standard kde-window-manager kdebase-apps
  kdebase-bin kdebase-runtime kdebase-workspace kdebase-workspace-bin kdelibs5-plugins
  kdemultimedia-kio-plugins kdepasswd kdepim-runtime kdeplasma-addons kdesudo kfind
  khelpcenter4 klipper kmail kmix knm-runtime knotes konq-plugins konqueror konsole kopete
  kopete-message-indicator korganizer kscreensaver kscreensaver-xsavers ksnapshot ksysguard
  kwalletmanager kwrite libkdepim4 libkopete4 libmessagelist4 libpolkit-qt-1-1
  libreoffice-kde okular plasma-dataengines-workspace plasma-desktop plasma-runners-addons
  plasma-wallpapers-addons plasma-widget-lancelot plasma-widget-networkmanagement
  plasma-widgets-addons plasma-widgets-workspace polkit-kde-1 sweeper systemsettings
  update-manager-kde
The following NEW packages will be installed:
  libpolkit-qt-1-0
0 upgraded, 1 newly installed, 63 to remove and 23 not upgraded.
Need to get 0B/70.8kB of archives.
After this operation, 163MB disk space will be freed.
Do you want to continue [Y/n]?
```


i use ubuntu maverick 10.10 with gnome and kde desktop, i was try to install kpackagekit for kde 

thanks

---

### Post by mynameisnotbob on 2011-04-19
so what is the problem?
To continue from that message, press y and then enter. Then you should be able to install the others. That, by the way, is quite a chain of dependencies. Kudos to you for discovering it.

Hold on...you use gnome and KDE? why?

---

### Post by Zorael on 2011-04-19
Use **aptitude** instead of apt-get (so '**sudo aptitude install kpackagekit**'). It's much better at resolving dependencies than apt-get is, and will offer you several solutions to pick between.

The way you're doing it seems to work too, though. :3

---

### Post by flurry21 on 2011-04-19
> **Zorael said:**
> Use **aptitude** instead of apt-get (so '**sudo aptitude install kpackagekit**'). It's much better at resolving dependencies than apt-get is, and will offer you several solutions to pick between.

The way you're doing it seems to work too, though. :3
  


and i've got this
```

maverick@maverick:~$ sudo aptitude install kpackagekit
The following NEW packages will be installed:
  kpackagekit libdebconf-kde0{a} libpackagekit-glib2-14{a} libpackagekit-qt-14{a} 
  libpolkit-qt-1-0{a} libqapt-runtime{a} libqapt1{a} packagekit{a} 
  packagekit-backend-aptcc{a} python-packagekit{a} qapt-batch{a} 
  software-properties-kde{a} 
0 packages upgraded, 12 newly installed, 0 to remove and 32 not upgraded.
Need to get 1,555kB/1,626kB of archives. After unpacking 5,485kB will be used.
The following packages have unmet dependencies:
  libpolkit-qt-1-1: Conflicts: libpolkit-qt-1-0 (<= 0.99.0-0ubuntu1) but 0.95.1-1ubuntu1 is to be installed.
                    Breaks: libpolkit-qt-1-0 (<= 0.99.0-0ubuntu1) but 0.95.1-1ubuntu1 is to be installed.
The following actions will resolve these dependencies:

     Keep the following packages at their current version:
1)     kpackagekit [Not Installed]                        
2)     libpolkit-qt-1-0 [Not Installed]                   
3)     libqapt-runtime [Not Installed]                    
4)     qapt-batch [Not Installed]                         
5)     software-properties-kde [Not Installed]            



Accept this solution? [Y/n/q/?] 

```

after typing yes well nothing happen!!??
i still cannot installing it!!

---

### Post by Dutch70 on 2011-04-19
Run the following command and then try it again.
```
sudo apt-get install -f
```

---

### Post by flurry21 on 2011-04-19
> **Dutch70 said:**
> Run the following command and then try it again.
```
sudo apt-get install -f
```

```

maverick@maverick:~$ sudo apt-get install -f
[sudo] password for maverick: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 32 not upgraded.
maverick@maverick:~$ 


```

still nothing  happen!!!???

---

### Post by Dutch70 on 2011-04-19
I don't see where you tried to install it again.

---

### Post by flurry21 on 2011-04-19
> **Dutch70 said:**
> I don't see where you tried to install it again.


you installing kpackagekit after 
```

maverick@maverick:~$ sudo aptitude install kpackagekit
[sudo] password for maverick: 
The following NEW packages will be installed:
  kpackagekit libdebconf-kde0{a} libpackagekit-glib2-14{a} libpackagekit-qt-14{a} libpolkit-qt-1-0{a} libqapt-runtime{a} libqapt1{a} 
  packagekit{a} packagekit-backend-aptcc{a} python-packagekit{a} qapt-batch{a} software-properties-kde{a} 
0 packages upgraded, 12 newly installed, 0 to remove and 32 not upgraded.
Need to get 1,555kB/1,626kB of archives. After unpacking 5,485kB will be used.
The following packages have unmet dependencies:
  libpolkit-qt-1-1: Conflicts: libpolkit-qt-1-0 (<= 0.99.0-0ubuntu1) but 0.95.1-1ubuntu1 is to be installed.
                    Breaks: libpolkit-qt-1-0 (<= 0.99.0-0ubuntu1) but 0.95.1-1ubuntu1 is to be installed.
The following actions will resolve these dependencies:

     Keep the following packages at their current version:
1)     kpackagekit [Not Installed]                        
2)     libpolkit-qt-1-0 [Not Installed]                   
3)     libqapt-runtime [Not Installed]                    
4)     qapt-batch [Not Installed]                         
5)     software-properties-kde [Not Installed]            



Accept this solution? [Y/n/q/?] 

```

---

### Post by Zorael on 2011-04-20
The first solution offered is often very pessimistic and will suggest that you don't install anything at all.

What's happening here is that **libpolkit-qt-1-[COLOR="Red"]0[/COLOR]** has been replaced by **libpolkit-qt-1-[COLOR="Green"]1[/COLOR]**, so you want to find a solution that removes **libpolkit-qt-1-[COLOR="Red"]0[/COLOR]** and installs the rest. Package managers always err on the side of safety when it comes to automatically *removing* packages.

---

### Post by mynameisnotbob on 2011-04-20
Maybe this is stating the obvious, but ```
sudo aptitude purge libpolkit-qt-1-0 && sudo aptitude install kpackagekit
``` should work. Do you need two sudos?

---

