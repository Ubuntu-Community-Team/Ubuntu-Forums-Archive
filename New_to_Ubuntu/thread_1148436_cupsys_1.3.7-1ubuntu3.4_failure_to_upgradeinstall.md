---
title: "cupsys 1.3.7-1ubuntu3.4 failure to upgrade/install"
date: 2009-05-04
forum: New to Ubuntu
---

### Post by ericeclifford on 2009-05-04
Everytime I run apt-get upgrade on my live cd customization I get cupsysy failure to upgrade/install anyone know a fix? ive dont lots of research, but have not found a failure to this version that has a fix.

Was wondering is there a way I can just avoid upgrade it all together. like a apt-get upgrade that avoids upgrading cupsys particular.

---

### Post by ptn107 on 2009-05-04
cupsys is a transitional package for cups.  I don't think it needs to be installed.  The only cups packages installed by default [for 9.04] are: cups cups-bsd cups-client cups-common cupsddk cupsddk-drivers cups-driver-gutenprint.

---

### Post by ericeclifford on 2009-05-04
root@eric:/# apt-get remove cupsys
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: The package cupsys needs to be reinstalled, but I can't find an archive for it.

so how do I remove it?

---

### Post by ptn107 on 2009-05-04
Try installing the new packages first before removing the obsolete ones (may be easier to copy/paste):
```
sudo aptitude update && sudo aptitude -f install cups cups-bsd cups-client cups-common cupsddk cupsddk-drivers cups-driver-gutenprint -y && sudo aptitude -f remove cupsys cupsys-bsd cupsys-client cupsys-common cupsys-driver-gutenprint -y
```

---

### Post by ericeclifford on 2009-05-04
root@eric:/# aptitude update && aptitude -f install cups cups-bsd cups-client cups-common cupsddk cupsddk-drivers cups-driver-gutenprint -y && aptitude -f remove cupsys cupsys-bsd cupsys-client cupsys-common cupsys-driver-gutenprint -yErr [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy Release.gpg
  Could not resolve 'packages.medibuntu.org'
Err [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/free Translation-en_US
  Could not resolve 'packages.medibuntu.org'
Err [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/non-free Translation-en_US
  Could not resolve 'packages.medibuntu.org'
Reading package lists... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
No candidate version found for cups
Couldn't find any package whose name or description matched "cups-bsd"
Couldn't find any package whose name or description matched "cups-client"
Couldn't find any package whose name or description matched "cups-common"
Couldn't find any package whose name or description matched "cups-driver-gutenprint"
No candidate version found for cups
Couldn't find any package whose name or description matched "cups-bsd"
Couldn't find any package whose name or description matched "cups-client"
Couldn't find any package whose name or description matched "cups-common"
Couldn't find any package whose name or description matched "cups-driver-gutenprint"
The following partially installed packages will be configured:
  cupsys msttcorefonts 
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Error!
E: I wasn't able to locate file for the cupsys package. This might mean you need to manually fix this package.
root@eric:/# 




This was the output for those commands while I was in the chroot edit(live cd customization).
BTW thanks a lot for trying.

---

### Post by ptn107 on 2009-05-04
From that output I can see that the only repository listed is [http://packages.medibuntu.org](http://packages.medibuntu.org).  You need to have the official Ubuntu repositories enabled before you can run the previous command.  (If your NOT running Ubuntu 9.04, stop me now!  These repos are for 9.04 only!) Press ALT+F2 and type:

**gksu gedit /etc/apt/sources.list**

Click run.  Now add the following lines to the file:

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty main restricted
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-updates main restricted
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-updates universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-updates multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-updates multiverse
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security multiverse

Save and close the file.

Now run:
```
sudo aptitude update && sudo aptitude -f install cups cups-bsd cups-client cups-common cupsddk cupsddk-drivers cups-driver-gutenprint -y && sudo aptitude -f remove cupsys cupsys-bsd cupsys-client cupsys-common cupsys-driver-gutenprint -y
```

Post your progress.  We will figure this out.

---

### Post by ericeclifford on 2009-05-04
Well 8.04.2 is my current version and is the iso image I am using to customize my live cd. here is the source list that is default with it.

#deb cdrom:[Ubuntu 8.04.2 _Hardy Heron_ - Release i386 (20090121)]/ hardy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security multiverse

This is before I install medibuntu, ill use that one command again during the script, but I still get a crash report saying that it failed the exact same when I boot up the live cd. But ill play around with it a bit and then post.

---

### Post by ericeclifford on 2009-05-04
Well I extract all of the contents to the edit folder and enter the chroot edit environment. and got this.

root@eric:~/live# chroot edit
root@eric:/# aptitude update && aptitude -f install cups cups-bsd cups-client cups-common cupsddk cupsddk-drivers cups-driver-gutenprint -y && aptitude -f remove cupsys cupsys-bsd cupsys-client cupsys-common cupsys-driver-gutenprint -yReading package lists... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Initializing package states... Done
Writing extended state information... Done
Building tag database... Done             
No candidate version found for cups
Couldn't find any package whose name or description matched "cups-bsd"
Couldn't find any package whose name or description matched "cups-client"
Couldn't find any package whose name or description matched "cups-common"
Couldn't find any package whose name or description matched "cups-driver-gutenprint"
No candidate version found for cups
Couldn't find any package whose name or description matched "cups-bsd"
Couldn't find any package whose name or description matched "cups-client"
Couldn't find any package whose name or description matched "cups-common"
Couldn't find any package whose name or description matched "cups-driver-gutenprint"
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
The following packages are BROKEN:
  bluez-cups cups-pdf hal-cups-utils hplip ubuntu-desktop 
The following packages will be REMOVED:
  cupsys cupsys-bsd cupsys-client cupsys-common cupsys-driver-gutenprint 
0 packages upgraded, 0 newly installed, 5 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 16.7MB will be freed.
The following packages have unmet dependencies:
  hal-cups-utils: Depends: cupsys but it is not installable
  bluez-cups: Depends: cupsys but it is not installable
  hplip: Depends: cupsys (>= 1.1.20) but it is not installable
  ubuntu-desktop: Depends: cupsys but it is not installable
                  Depends: cupsys-bsd but it is not installable
                  Depends: cupsys-client but it is not installable
                  Depends: cupsys-driver-gutenprint but it is not installable
  cups-pdf: Depends: cupsys-client but it is not installable
            PreDepends: cupsys (>= 1.1.15) but it is not installable
Resolving dependencies...
The following actions will resolve these dependencies:

Remove the following packages:
ubuntu-desktop

Keep the following packages at their current version:
cupsys [1.3.7-1ubuntu3.3 (now)]
cupsys-client [1.3.7-1ubuntu3.3 (now)]
cupsys-common [1.3.7-1ubuntu3.3 (now)]

Score is 152

The following packages will be automatically REMOVED:
  ubuntu-desktop 
The following packages will be REMOVED:
  cupsys-bsd cupsys-driver-gutenprint ubuntu-desktop 
0 packages upgraded, 0 newly installed, 3 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 971kB will be freed.
Writing extended state information... Done
Can not write log, openpty() failed (/dev/pts not mounted?)
(Reading database ... 98538 files and directories currently installed.)
Removing ubuntu-desktop ...
Removing cupsys-bsd ...
Removing cupsys-driver-gutenprint ...
invoke-rc.d: initscript cupsys, action "force-reload" failed.
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Writing extended state information... Done
Building tag database... Done             
root@eric:/# 


Now I might of messed something up, because my script might of went too far so I am going to reextract the iso contents to the edit folder and erase this one and see what happens ill keep you updated,  P.S. Thanks again.

---

### Post by ericeclifford on 2009-05-04
This is what I got when I entered the commands without touching anything of the 8.04.2 version.

root@eric:/# aptitude update && aptitude -f install cups cups-bsd cups-client cups-common cupsddk cupsddk-drivers cups-driver-gutenprint -y && aptitude -f remove cupsys cupsys-bsd cupsys-client cupsys-common cupsys-driver-gutenprint -yGet:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy Release.gpg [189B]                 
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/main Translation-en_US               
Get:2 [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release.gpg [189B]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/multiverse Translation-en_US
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates Release.gpg [189B]
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/multiverse Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Translation-en_US
Get:4 [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release [58.5kB]
Get:5 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy Release [65.9kB]
Get:6 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates Release [58.5kB]               
Get:7 [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Packages [161kB]           
Get:8 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/main Packages [1178kB]                 
Get:9 [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Packages [8008B]     
Get:10 [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Sources [26.9kB]          
Get:11 [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Sources [903B]      
Get:12 [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Packages [79.1kB]     
Get:13 [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Sources [11.7kB]      
Get:14 [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Packages [11.9kB]   
Get:15 [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Sources [1105B]     
Get:16 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/restricted Packages [6986B]           
Get:17 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/main Sources [338kB]                  
Get:18 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/restricted Sources [1488B]            
Get:19 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/universe Packages [4293kB]            
Get:20 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/universe Sources [1323kB]             
Get:21 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/multiverse Packages [179kB]           
Get:22 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/multiverse Sources [60.9kB]           
Get:23 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main Packages [434kB]         
Get:24 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/restricted Packages [8437B]   
Get:25 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main Sources [112kB]          
Get:26 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/restricted Sources [901B]     
Get:27 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/universe Packages [193kB]     
Get:28 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/universe Sources [41.4kB]     
Get:29 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/multiverse Packages [29.1kB]  
Get:30 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/multiverse Sources [5538B]    
Fetched 8689kB in 24s (348kB/s)                                                 
Reading package lists... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Initializing package states... Done
Writing extended state information... Done
Building tag database... Done             
No candidate version found for cups
Couldn't find any package whose name or description matched "cups-bsd"
Couldn't find any package whose name or description matched "cups-client"
Couldn't find any package whose name or description matched "cups-common"
Couldn't find any package whose name or description matched "cups-driver-gutenprint"
No candidate version found for cups
Couldn't find any package whose name or description matched "cups-bsd"
Couldn't find any package whose name or description matched "cups-client"
Couldn't find any package whose name or description matched "cups-common"
Couldn't find any package whose name or description matched "cups-driver-gutenprint"
The following packages have been automatically kept back:
  linux-headers-2.6.24-23 linux-headers-2.6.24-23-generic 
  linux-restricted-modules-common 
The following packages have been kept back:
  acpid apport apport-gtk apt apt-utils cupsys cupsys-bsd cupsys-client 
  cupsys-common dash doc-base evolution-data-server 
  evolution-data-server-common firefox firefox-3.0 
  firefox-3.0-gnome-support firefox-gnome-support gedit gedit-common 
  ghostscript ghostscript-x gnome-power-manager gnome-system-tools gparted 
  gstreamer0.10-plugins-good gvfs gvfs-backends gvfs-fuse hal-info 
  initscripts jockey-common jockey-gtk libcamel1.2-11 libcupsimage2 
  libcupsys2 libcurl3 libcurl3-gnutls libebook1.2-9 libecal1.2-7 
  libedata-book1.2-2 libedata-cal1.2-6 libedataserver1.2-9 
  libedataserverui1.2-8 libegroupwise1.2-13 libexchange-storage1.2-3 
  libfreetype6 libgdata-google1.2-1 libgdata1.2-1 libglib2.0-0 libgs8 
  libgvfscommon0 libicu38 libjasper1 libkrb53 liblcms1 libldap-2.4-2 
  libnss3-1d libpng12-0 libpoppler-glib2 libpoppler2 libpurple0 libsndfile1 
  libssl0.9.8 libvolume-id0 libwmf0.2-7 linux-generic linux-headers-generic 
  linux-image-2.6.24-23-generic linux-image-generic 
  linux-restricted-modules-generic linux-ubuntu-modules-2.6.24-23-generic 
  network-manager-gnome openssl pidgin pidgin-data poppler-utils 
  python-apport python-apt python-gobject python-problem-report ssl-cert 
  sudo sysv-rc sysvutils tasksel tasksel-data totem totem-common 
  totem-gstreamer totem-mozilla totem-plugins tzdata udev ufw 
  update-manager update-manager-core vim-common vim-tiny xfonts-scalable 
  xserver-xorg-video-ati xserver-xorg-video-intel xulrunner-1.9 
  xulrunner-1.9-gnome-support 
0 packages upgraded, 0 newly installed, 0 to remove and 106 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Building tag database... Done      
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Building tag database... Done      
The following packages are BROKEN:
  bluez-cups cups-pdf hal-cups-utils hplip ubuntu-desktop 
The following packages have been automatically kept back:
  linux-headers-2.6.24-23 linux-headers-2.6.24-23-generic 
  linux-restricted-modules-common 
The following packages have been kept back:
  acpid apport apport-gtk apt apt-utils dash doc-base evolution-data-server 
  evolution-data-server-common firefox firefox-3.0 
  firefox-3.0-gnome-support firefox-gnome-support gedit gedit-common 
  ghostscript ghostscript-x gnome-power-manager gnome-system-tools gparted 
  gstreamer0.10-plugins-good gvfs gvfs-backends gvfs-fuse hal-info 
  initscripts jockey-common jockey-gtk libcamel1.2-11 libcupsimage2 
  libcupsys2 libcurl3 libcurl3-gnutls libebook1.2-9 libecal1.2-7 
  libedata-book1.2-2 libedata-cal1.2-6 libedataserver1.2-9 
  libedataserverui1.2-8 libegroupwise1.2-13 libexchange-storage1.2-3 
  libfreetype6 libgdata-google1.2-1 libgdata1.2-1 libglib2.0-0 libgs8 
  libgvfscommon0 libicu38 libjasper1 libkrb53 liblcms1 libldap-2.4-2 
  libnss3-1d libpng12-0 libpoppler-glib2 libpoppler2 libpurple0 libsndfile1 
  libssl0.9.8 libvolume-id0 libwmf0.2-7 linux-generic linux-headers-generic 
  linux-image-2.6.24-23-generic linux-image-generic 
  linux-restricted-modules-generic linux-ubuntu-modules-2.6.24-23-generic 
  network-manager-gnome openssl pidgin pidgin-data poppler-utils 
  python-apport python-apt python-gobject python-problem-report ssl-cert 
  sudo sysv-rc sysvutils tasksel tasksel-data totem totem-common 
  totem-gstreamer totem-mozilla totem-plugins tzdata udev ufw 
  update-manager update-manager-core vim-common vim-tiny xfonts-scalable 
  xserver-xorg-video-ati xserver-xorg-video-intel xulrunner-1.9 
  xulrunner-1.9-gnome-support 
The following packages will be REMOVED:
  cupsys cupsys-bsd cupsys-client cupsys-common cupsys-driver-gutenprint 
0 packages upgraded, 0 newly installed, 5 to remove and 102 not upgraded.
Need to get 0B of archives. After unpacking 16.7MB will be freed.
The following packages have unmet dependencies:
  hal-cups-utils: Depends: cupsys but it is not installable
  bluez-cups: Depends: cupsys but it is not installable
  hplip: Depends: cupsys (>= 1.1.20) but it is not installable
  ubuntu-desktop: Depends: cupsys but it is not installable
                  Depends: cupsys-bsd but it is not installable
                  Depends: cupsys-client but it is not installable
                  Depends: cupsys-driver-gutenprint but it is not installable
  cups-pdf: Depends: cupsys-client but it is not installable
            PreDepends: cupsys (>= 1.1.15) but it is not installable
Resolving dependencies...
The following actions will resolve these dependencies:

Remove the following packages:
ubuntu-desktop

Upgrade the following packages:
cupsys [1.3.7-1ubuntu3.3 (now) -> 1.3.7-1ubuntu3.4 (hardy-updates,
hardy-security)]
cupsys-client [1.3.7-1ubuntu3.3 (now) -> 1.3.7-1ubuntu3.4 (hardy-updates,
hardy-security)]
cupsys-common [1.3.7-1ubuntu3.3 (now) -> 1.3.7-1ubuntu3.4 (hardy-updates,
hardy-security)]

Score is 152

The following packages have been automatically kept back:
  linux-headers-2.6.24-23 linux-headers-2.6.24-23-generic 
  linux-restricted-modules-common 
The following packages will be automatically REMOVED:
  ubuntu-desktop 
The following packages have been kept back:
  acpid apport apport-gtk apt apt-utils dash doc-base evolution-data-server 
  evolution-data-server-common firefox firefox-3.0 
  firefox-3.0-gnome-support firefox-gnome-support gedit gedit-common 
  ghostscript ghostscript-x gnome-power-manager gnome-system-tools gparted 
  gstreamer0.10-plugins-good gvfs gvfs-backends gvfs-fuse hal-info 
  initscripts jockey-common jockey-gtk libcamel1.2-11 libcupsimage2 
  libcupsys2 libcurl3 libcurl3-gnutls libebook1.2-9 libecal1.2-7 
  libedata-book1.2-2 libedata-cal1.2-6 libedataserver1.2-9 
  libedataserverui1.2-8 libegroupwise1.2-13 libexchange-storage1.2-3 
  libfreetype6 libgdata-google1.2-1 libgdata1.2-1 libglib2.0-0 libgs8 
  libgvfscommon0 libicu38 libjasper1 libkrb53 liblcms1 libldap-2.4-2 
  libnss3-1d libpng12-0 libpoppler-glib2 libpoppler2 libpurple0 libsndfile1 
  libssl0.9.8 libvolume-id0 libwmf0.2-7 linux-generic linux-headers-generic 
  linux-image-2.6.24-23-generic linux-image-generic 
  linux-restricted-modules-generic linux-ubuntu-modules-2.6.24-23-generic 
  network-manager-gnome openssl pidgin pidgin-data poppler-utils 
  python-apport python-apt python-gobject python-problem-report ssl-cert 
  sudo sysv-rc sysvutils tasksel tasksel-data totem totem-common 
  totem-gstreamer totem-mozilla totem-plugins tzdata udev ufw 
  update-manager update-manager-core vim-common vim-tiny xfonts-scalable 
  xserver-xorg-video-ati xserver-xorg-video-intel xulrunner-1.9 
  xulrunner-1.9-gnome-support 
The following packages will be REMOVED:
  cupsys-bsd cupsys-driver-gutenprint ubuntu-desktop 
The following packages will be upgraded:
  cupsys cupsys-client cupsys-common 
3 packages upgraded, 0 newly installed, 3 to remove and 102 not upgraded.
Need to get 3096kB of archives. After unpacking 971kB will be freed.
Writing extended state information... Done
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main cupsys-common 1.3.7-1ubuntu3.4 [1144kB]
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main cupsys 1.3.7-1ubuntu3.4 [1863kB]
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main cupsys-client 1.3.7-1ubuntu3.4 [88.4kB]
Fetched 3096kB in 5s (562kB/s)     
Preconfiguring packages ...
Can not write log, openpty() failed (/dev/pts not mounted?)
(Reading database ... 98538 files and directories currently installed.)
Removing ubuntu-desktop ...
Removing cupsys-bsd ...
Removing cupsys-driver-gutenprint ...
invoke-rc.d: initscript cupsys, action "force-reload" failed.
Can not write log, openpty() failed (/dev/pts not mounted?)
(Reading database ... 98502 files and directories currently installed.)
Preparing to replace cupsys-common 1.3.7-1ubuntu3.3 (using .../cupsys-common_1.3.7-1ubuntu3.4_all.deb) ...
Unpacking replacement cupsys-common ...
Preparing to replace cupsys 1.3.7-1ubuntu3.3 (using .../cupsys_1.3.7-1ubuntu3.4_i386.deb) ...
Ignoring nonregistered document `cupsys'
invoke-rc.d: initscript cupsys, action "stop" failed.
dpkg: warning - old pre-removal script returned error exit status 1
dpkg - trying script from the new package instead ...
invoke-rc.d: initscript cupsys, action "stop" failed.
dpkg: error processing /var/cache/apt/archives/cupsys_1.3.7-1ubuntu3.4_i386.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
invoke-rc.d: initscript cupsys, action "start" failed.
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 1
Preparing to replace cupsys-client 1.3.7-1ubuntu3.3 (using .../cupsys-client_1.3.7-1ubuntu3.4_i386.deb) ...
Unpacking replacement cupsys-client ...
Errors were encountered while processing:
 /var/cache/apt/archives/cupsys_1.3.7-1ubuntu3.4_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up cupsys-common (1.3.7-1ubuntu3.4) ...
Setting up cupsys-client (1.3.7-1ubuntu3.4) ...

dpkg: error processing cupsys (--configure):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting configuration.
Errors were encountered while processing:
 cupsys
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Writing extended state information... Done
Building tag database... Done

---

### Post by ptn107 on 2009-05-05
Since your running 8.04.2 and not 9.04 the command needs to be modified a little:

```
sudo aptitude update && sudo aptitude -f reinstall cupsys cupsys-bsd cupsys-client cupsys-common cupsys-driver-gutenprint -y
```

If that works you may want to fix the other things it says are broken:
```
sudo aptitude -f install ubuntu-desktop && sudo aptitude full-upgrade
```

---

### Post by ericeclifford on 2009-05-05
invoke-rc.d: initscript cupsys, action "start" failed.
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 1
Preparing to replace cupsys-bsd 1.3.7-1ubuntu3.3 (using .../cupsys-bsd_1.3.7-1ubuntu3.4_i386.deb) ...
Unpacking replacement cupsys-bsd ...
Preparing to replace cupsys-client 1.3.7-1ubuntu3.3 (using .../cupsys-client_1.3.7-1ubuntu3.4_i386.deb) ...
Unpacking replacement cupsys-client ...
Preparing to replace doc-base 0.8.7 (using .../doc-base_0.8.7ubuntu1_all.deb) ...
Unpacking replacement doc-base ...
Preparing to replace evolution-data-server 2.22.3-0ubuntu2 (using .../evolution-data-server_2.22.3-0ubuntu3_i386.deb) ...
Unpacking replacement evolution-data-server ...
Preparing to replace evolution-data-server-common 2.22.3-0ubuntu2 (using .../evolution-data-server-common_2.22.3-0ubuntu3_all.deb) ...
Unpacking replacement evolution-data-server-common ...
Preparing to replace libglib2.0-0 2.16.6-0ubuntu1 (using .../libglib2.0-0_2.16.6-0ubuntu1.1_i386.deb) ...
Unpacking replacement libglib2.0-0 ...
Preparing to replace libedataserver1.2-9 2.22.3-0ubuntu2 (using .../libedataserver1.2-9_2.22.3-0ubuntu3_i386.deb) ...
Unpacking replacement libedataserver1.2-9 ...
Preparing to replace libnss3-1d 3.12.0.3-0ubuntu0.8.04.4 (using .../libnss3-1d_3.12.0.3-0ubuntu0.8.04.5_i386.deb) ...
Unpacking replacement libnss3-1d ...
Preparing to replace libcamel1.2-11 2.22.3-0ubuntu2 (using .../libcamel1.2-11_2.22.3-0ubuntu3_i386.deb) ...
Unpacking replacement libcamel1.2-11 ...
Preparing to replace libebook1.2-9 2.22.3-0ubuntu2 (using .../libebook1.2-9_2.22.3-0ubuntu3_i386.deb) ...
Unpacking replacement libebook1.2-9 ...
Preparing to replace libecal1.2-7 2.22.3-0ubuntu2 (using .../libecal1.2-7_2.22.3-0ubuntu3_i386.deb) ...
Unpacking replacement libecal1.2-7 .

Getting same errors as before, Seems like this new upgrade screws up the whole live cd.

Dont really know what to do, but not upgrade at all, which gimps me a lot. And the possibility of medibuntu not installing correctly.

Also this.

dpkg: error processing cupsys (--configure):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting configuration.
Setting up gstreamer0.10-plugins-good (0.10.7-3ubuntu0.2) ...

Setting up firefox-3.0 (3.0.10+nobinonly-0ubuntu0.8.04.1) ...
Please restart all running instances of Firefox-3.0, or you will experience problems.
Cannot find /proc/version - is /proc mounted?
[: 26: 0: unexpected operator

Processing triggers for libc6 ...
ldconfig deferred processing now taking place
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.24-23-generic
Errors were encountered while processing:
 cupsys

---

### Post by ericeclifford on 2009-05-05
I think you nailed it with those last commands, It works perfectly. 

No error report in the live cd and all programs seem to work, but I still do get error reports and failures during the script but it all looks ok in the actual live cd. thanks alot.

---

### Post by ericeclifford on 2009-06-05
I am getting this crash report in the live cd I customize, and also it said errors while processing: cupsys still as well, I have those commands done as well, bump for a continued problem.

---

### Post by bcschmerker on 2009-11-30
I have a variation of this problem on my Everex refit with Gigabyte MA78GM-S2HP system board and Advance Micro Devices Athlon X2 5600+; in my case, Cupsys fails to set up from Synaptic, stalling the rest of the printer setup:
```
invoke-rc.d: initscript cupsys, action "start" failed.
dpkg: error processing cupsys (--configure):
 subprocess post-installation script returned error exit status 127
```The failure of CUPSd to initialize resulted in HPLIP and HPIJS, among other CUPS-related packages, remaining unconfigured.  (This did not affect LibCUPS packages, which I installed prior to the CUPSys packages.)

Update:  The Common UNIX Printing System daemon, /usr/sbin/cupsd (Package cupsys) *did* install from apt-get in single-user mode, indicating a possible conflict between APT and SELinUX concerning CUPS.

---

