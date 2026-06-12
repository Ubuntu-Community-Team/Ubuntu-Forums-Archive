---
title: "Help"
date: 2009-11-12
forum: New to Ubuntu
---

### Post by berdar on 2009-11-12
I'm brand new to Ubuntu and have enjoyed my week with it.  Last night I was playing with the Update Manager.  It tried to update Adobe Flash Plugin.  It stopped and gave me the error message below.   I've tried to remove the Plugin with both the Ubuntu Software Center and Synaptic Package Manager.   I keep getting the same error message. 

Anybody know what would help me get this repaired?




**Package operation failed**
The installation or removal of a software package failed.

E:I wasn't able to locate file for the adobe-flashplugin package. This might mean you need to manually fix this package.:

---

### Post by Shazaam on 2009-11-12
Enter this in terminal (Applications>Accessories>Terminal)...
```
sudo dpkg --configure -a
```
and then...
```
sudo apt-get install -f
```
Those should get you sorted out. When it asks you for a password, enter the one you use to login to Ubuntu. You won't see any output as you are typing it in but don't worry, it will be there. Hit enter after you type in your password.
When done try Synaptic again.

---

### Post by berdar on 2009-11-12
Didn't quite work.  I got something like this from the terminal


[quote=Shazaam;8301422]Enter this in terminal (Applications>Accessories>Terminal)...
```
sudo dpkg --configure -a
```dpkg: error processing adobe-flashplugin (--configure):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting configuration.
Errors were encountered while processing:
 adobe-flashplugin
..
```
sudo apt-get install -f
```then

bill@bill-laptop:~$ sudo apt-get install -f
[sudo] password for bill: 
Reading package lists... Done

The following packages were automatically installed and are no longer required:
  python-crypto empathy-doc kdebase-plasma python-desktopcouch-records
  libqimageblitz4 librpmbuild0 telepathy-salut libqt4-assistant
  ndiswrapper-common desktopcouch erlang-inets wine-gecko postfix
  erlang-syntax-tools sun-java6-plugin libgfortran3 python-pygame libqt4-test
  libwxgtk2.8-0 libpst4 lsb-graphics lsb-desktop libsctp1 erlang-mnesia
  libkdegames5 furiusisomount java-common librpmio0 librpm0
  libcouchdb-glib-1.0-1 ncurses-term libqt4-core kdebase-workspace-libs4+5
  libempathy-gtk28 python-telepathy libdvbpsi5 startupmanager binutils-static
  libsnack2-alsa amsn sun-java6-bin libloudmouth1-0 couchdb-bin unixodbc skype
  python-couchdb libvlc2 python-numpy python-avahi telepathy-haze libqt4-gui
  erlang-xmerl libkonq5 vlc-nox odbcinst1debian1 sun-java6-jre libmikmod2
  amsn-data trackballs-music libwxbase2.8-0 ubuntu-restricted-extras lsb pax
  libjson-glib-1.0-0 wine telepathy-gabble lksctp-tools rpm libiso9660-5
  libblas3gf fuseiso vlc tcl8.5 trackballs-data erlang-crypto libsdl-mixer1.2
  liblapack3gf dopewars-data tk8.5 liblua5.1-0 libkonq5-templates bsd-mailx
  vlc-plugin-pulse libempathy-gtk-common vlc-data erlang-ssl ndisgtk gufw
  plasma-widget-folderview telepathy-butterfly kdelibs libtar mailx winbind
  python-desktopcouch python-papyon erlang-runtime-tools lsb-core libvlccore2
  alien libvcdinfo0 libebml0 tcl-tls libmatroska0 modemmanager erlang-base
  libsdl-image1.2 erlang-public-key lsb-cxx ndiswrapper-utils-1.9 libsmpeg0
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  adobe-flashplugin
Suggested packages:
  konqueror-nsplugins ttf-xfree86-nonfree xfs
The following packages will be upgraded:
  adobe-flashplugin
1 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B/4,018kB of archives.
After this operation, 147kB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 161133 files and directories currently installed.)
Preparing to replace adobe-flashplugin 10.0.22.87-1 (using .../adobe-flashplugin_10.0.32.18-1jaunty1_i386.deb) ...
update-alternatives: error: no alternatives for iceape-flashplugin.
update-alternatives: error: no alternatives for iceape-flashplugin.
dpkg: warning: old pre-removal script returned error exit status 2
dpkg - trying script from the new package instead ...
update-alternatives: error: no alternatives for iceape-flashplugin.
update-alternatives: error: no alternatives for iceape-flashplugin.
dpkg: error processing /var/cache/apt/archives/adobe-flashplugin_10.0.32.18-1jaunty1_i386.deb (--unpack):
 subprocess new pre-removal script returned error exit status 2
postinst called with argument `abort-upgrade'
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 /var/cache/apt/archives/adobe-flashplugin_10.0.32.18-1jaunty1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)




I then went to Synapic to remove the software and got this error

E: adobe-flashplugin: Package is in a very bad inconsistent state - you should  reinstall it before attempting a removal.

Any Ideas?

---

### Post by ukripper on 2009-11-12
Remove adobe-flashplugin using following commands:
```
 sudo rm /var/lib/dpkg/info/adobe-flashplugin.prerm
```
 ```
sudo dpkg --remove --force-remove-reinstreq adobe-flashplugin
```

---

### Post by berdar on 2009-11-12
Perfect,



Thank you so very much.

---

### Post by zkriesse on 2009-11-12
Now..if you haven't installed it yet go to Adobe and download the .deb version for Ubuntu.

---

