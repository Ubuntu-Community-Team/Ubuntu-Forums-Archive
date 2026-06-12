---
title: "kubuntu-desktop uninstalled but still shows 70 updates"
date: 2009-02-15
forum: New to Ubuntu
---

### Post by SentientFluid on 2009-02-15
I originally installed Ubuntu off CD and then installed kubuntu-desktop using ```
sudo aptitude install kubuntu-desktop
```I decided I wanted to stick with Gnome rather the KDE and logged into an Ubuntu session and ran ```
sudo aptitude remove kubuntu-desktop
```

Everything was fine until today when suddenly there are a bunch of new updates for Kubuntu as shown here:

```
geoff@Podfather:~$ sudo aptitude safe-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
The following packages will be upgraded:
  akregator ark dolphin dpkg dpkg-dev gvfs gvfs-backends gvfs-bin gvfs-fuse gwenview kate 
  kde-icons-oxygen kde-printer-applet kde-window-manager kde-zeroconf kdebase-plasma 
  kdebase-runtime kdebase-runtime-bin-kde4 kdebase-runtime-data kdebase-runtime-data-common 
  kdebase-workspace-data kdebase-workspace-libs4+5 kdegraphics-strigi-plugins kdelibs-bin 
  kdelibs5 kdelibs5-data kdepasswd kdepim-strigi-plugins kdepimlibs-data kdepimlibs5 
  kdeplasma-addons kdeplasma-addons-data kdeplasma-addons-libs4 kdm kfind khelpcenter4 
  klipper kmag kmail kmix kmousetool konsole krdc krfb ksnapshot ksysguard ksysguardd 
  ksystemlog ktimetracker kuser libgvfscommon0 libkdecorations4 libkdepim4 libkipi-common 
  libkipi5 libkleo4 libkonq5 libkonq5-templates libkpgp4 libksieve4 libkwineffects1 
  libmimelib4 libokularcore1 libplasma2 okular okular-extra-backends phonon-backend-xine 
  python-kde4 rhythmbox systemsettings 
70 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 74.6MB of archives. After unpacking 36.9kB will be used.
Do you want to continue? [Y/n/?] n
Abort.

```

Tried purging Kubuntu:
```
geoff@Podfather:~$ sudo aptitude purge kubuntu-desktop
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 70 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done

```

What do I need to do to stop Ubuntu from looking for those updates?

---

### Post by RomeReactor on 2009-02-15
Hi. Removing the kubuntu-desktop package with aptitude only gets rid of the metapackage, leaving the actual desktop installed. Follow the instructions [here]("http://www.psychocats.net/ubuntu/purekde").

---

### Post by SentientFluid on 2009-02-15
> **RomeReactor said:**
> Hi. Removing the kubuntu-desktop package with aptitude only gets rid of the metapackage, leaving the actual desktop installed. Follow the instructions [here]("http://www.psychocats.net/ubuntu/purekde").

EXACTLY what I was looking for (except [this link for Pure Gnome]("http://www.psychocats.net/ubuntu/puregnome"), thanks!!

---

### Post by SentientFluid on 2009-02-16
Followed Psychocats instructions for Pure Gnome and now I'm having Skydome issues that I posted [here]("http://ubuntuforums.org/showthread.php?p=6746548").  Any ideas would be appreciated. :)

---

