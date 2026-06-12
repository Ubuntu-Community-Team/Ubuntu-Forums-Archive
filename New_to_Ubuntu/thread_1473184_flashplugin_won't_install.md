---
title: "flashplugin won't install"
date: 2010-05-04
forum: New to Ubuntu
---

### Post by lyni on 2010-05-04
I have Ubuntu 8.04. I have tried a clean install to Ubuntu 10.04. I could not install the new system even though I downloaded it to several different CD's.
this morning I decided to upgrade instead.
now I have part of a system because there were errors throughout the upgrade process. one of the errors was that the flashplugin did not install.

I have been trying to install the flashplugin from synaptic but I get this error message: flashplugin-nonfree-package is in a very bad inconsistent state - you should reinstall it before attempting a removal.

so it does not allow me to install it. even if I go to a website which tells me I need extra plugins and I click the button there I get the same error message.

thanks.

---

### Post by GSF1200S on 2010-05-05
> **lyni said:**
> I have Ubuntu 8.04. I have tried a clean install to Ubuntu 10.04. I could not install the new system even though I downloaded it to several different CD's.
this morning I decided to upgrade instead.
now I have part of a system because there were errors throughout the upgrade process. one of the errors was that the flashplugin did not install.

I have been trying to install the flashplugin from synaptic but I get this error message: flashplugin-nonfree-package is in a very bad inconsistent state - you should reinstall it before attempting a removal.

so it does not allow me to install it. even if I go to a website which tells me I need extra plugins and I click the button there I get the same error message.

thanks.

Try this:
```
sudo dpkg --configure -a
sudo apt-get update
sudo apt-get purge flashplugin-nonfree flashplugin-installer
sudo apt-get install -f
sudo apt-get dist-upgrade
sudo apt-get install flashplugin-installer

```

---

### Post by lyni on 2010-05-05
this is what I got from the Terminal:

lyn@lyn-desktop:~$ sudo dpkg --configure -a
lyn@lyn-desktop:~$ apt-get update
E: Could not open lock file /var/lib/apt/lists/lock - open (13: Permission denied)
E: Unable to lock the list directory
lyn@lyn-desktop:~$ sudo apt-get purge flashplugin-nonfree flashplugin-installer
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package flashplugin-installer is not installed, so not removed
The following packages were automatically installed and are no longer required:
  libgladeui-1-9 libfreebob0 libarts1c2a libgtk2.0-0-dbg
  evolution-data-server-dbg libktnef1 libgsf-gnome-1-114 libartsc0 rpm2cpio
  librpmbuild0 rhythmbox-dbg gstreamer0.10-plugins-base-dbg lsb-languages
  libavutil1d libatk1.0-dbg exim4-config libdc1394-13 debhelper
  libgda-4.0-common libgsf-1-114-dbg libdevhelp-1-1 libgoffice-0.8-8-common
  intltool-debian libgda3-common evince-dbg mplayer-skins libkcal2b
  libpango1.0-0-dbg libwxgtk2.6-0 libbeecrypt6 libgfortran3 libgnomevfs2-0-dbg
  exim4-daemon-light libopts25 epiphany-browser-data lsb-graphics libtagc0
  libopts25-dev lsb-desktop evolution-dbg autogen m4 libwebkit-1.0-2-dbg
  eog-dbg libatspi-dbg librpmio0 libapr1 librpm0 rpm-common
  openoffice.org-hyphenation-en-us po-debconf ncurses-term autoconf python-dbg
  anjuta-common libpostproc1d libservlet2.4-java libgdl-1-dbg libnss3-dev
  libxft2-dbg libdvbpsi4 exuberant-ctags libavformat1d python-cairo-dbg
  libfontconfig1-dbg binutils-static libxosd2 libgoffice-0.8-8 libsvn1
  intltool ruby1.8 libkleopatra1 libtool libx264-57 libgoffice-dbg libvlc0
  anjuta libgsf-gnome-1-114-dbg gettext nvidia-kernel-common python-numpy ruby
  devhelp-common bsh anjuta-dbg cvs gstreamer0.10-plugins-ugly-dbg libggi2
  libgda-4.0-4 gstreamer0.10-plugins-good-dbg libgii1 libjaxp1.3-java
  libwxbase2.6-0 autotools-dev libkpimidentities1 libloudmouth1-0-dbg
  libkdepim1a libjline-java lsb libnspr4-dev libxerces2-java pax libxml2-dbg
  gnome-panel-dbg python2.6-dbg libtunepimp5 libboo2.0-cil libifp4
  libgnomecanvas2-dbg libgii1-target-x lsb-multimedia rpm libnss3-1d-dbg
  libkpimexchange1 libxalan2-java libiso9660-5 libdvdread3 libkarma0 libzip1
  libblas3gf nautilus-dbg python-numpy-dbg automake libgtkhtml3.14-dbg
  liblapack3gf libkmime2 libavahi1.0-cil lsb-printing gnome-applets-dbg
  liboobs-1-4-dbg libgda3-bin libavcodec1d libgda3-3 librsvg2-dbg
  libnspr4-0d-dbg libgda3-3-dbg libpq5 exim4 html2text libgnomeui-0-dbg
  exim4-base mailx odt2txt libglib2.0-0-dbg libgnome2-dbg libruby1.8 libvala0
  lsb-core totem-dbg alien libaudit0 libltdl-dev libaprutil1 libgail-gnome-dbg
  libnjb5 libgdl-1-3 gimp-dbg python-gobject-dbg libgstreamer0.10-0-dbg
  python-gtk2-dbg libgdl-1-common lsb-cxx
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  flashplugin-nonfree*
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 168kB disk space will be freed.
Do you want to continue [Y/n]?

---

### Post by GSF1200S on 2010-05-05
> **lyni said:**
> this is what I got from the Terminal:

lyn@lyn-desktop:~$ sudo dpkg --configure -a
lyn@lyn-desktop:~$ apt-get update
E: Could not open lock file /var/lib/apt/lists/lock - open (13: Permission denied)
E: Unable to lock the list directory
lyn@lyn-desktop:~$ sudo apt-get purge flashplugin-nonfree flashplugin-installer
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package flashplugin-installer is not installed, so not removed
The following packages were automatically installed and are no longer required:
  libgladeui-1-9 libfreebob0 libarts1c2a libgtk2.0-0-dbg
  evolution-data-server-dbg libktnef1 libgsf-gnome-1-114 libartsc0 rpm2cpio
  librpmbuild0 rhythmbox-dbg gstreamer0.10-plugins-base-dbg lsb-languages
  libavutil1d libatk1.0-dbg exim4-config libdc1394-13 debhelper
  libgda-4.0-common libgsf-1-114-dbg libdevhelp-1-1 libgoffice-0.8-8-common
  intltool-debian libgda3-common evince-dbg mplayer-skins libkcal2b
  libpango1.0-0-dbg libwxgtk2.6-0 libbeecrypt6 libgfortran3 libgnomevfs2-0-dbg
  exim4-daemon-light libopts25 epiphany-browser-data lsb-graphics libtagc0
  libopts25-dev lsb-desktop evolution-dbg autogen m4 libwebkit-1.0-2-dbg
  eog-dbg libatspi-dbg librpmio0 libapr1 librpm0 rpm-common
  openoffice.org-hyphenation-en-us po-debconf ncurses-term autoconf python-dbg
  anjuta-common libpostproc1d libservlet2.4-java libgdl-1-dbg libnss3-dev
  libxft2-dbg libdvbpsi4 exuberant-ctags libavformat1d python-cairo-dbg
  libfontconfig1-dbg binutils-static libxosd2 libgoffice-0.8-8 libsvn1
  intltool ruby1.8 libkleopatra1 libtool libx264-57 libgoffice-dbg libvlc0
  anjuta libgsf-gnome-1-114-dbg gettext nvidia-kernel-common python-numpy ruby
  devhelp-common bsh anjuta-dbg cvs gstreamer0.10-plugins-ugly-dbg libggi2
  libgda-4.0-4 gstreamer0.10-plugins-good-dbg libgii1 libjaxp1.3-java
  libwxbase2.6-0 autotools-dev libkpimidentities1 libloudmouth1-0-dbg
  libkdepim1a libjline-java lsb libnspr4-dev libxerces2-java pax libxml2-dbg
  gnome-panel-dbg python2.6-dbg libtunepimp5 libboo2.0-cil libifp4
  libgnomecanvas2-dbg libgii1-target-x lsb-multimedia rpm libnss3-1d-dbg
  libkpimexchange1 libxalan2-java libiso9660-5 libdvdread3 libkarma0 libzip1
  libblas3gf nautilus-dbg python-numpy-dbg automake libgtkhtml3.14-dbg
  liblapack3gf libkmime2 libavahi1.0-cil lsb-printing gnome-applets-dbg
  liboobs-1-4-dbg libgda3-bin libavcodec1d libgda3-3 librsvg2-dbg
  libnspr4-0d-dbg libgda3-3-dbg libpq5 exim4 html2text libgnomeui-0-dbg
  exim4-base mailx odt2txt libglib2.0-0-dbg libgnome2-dbg libruby1.8 libvala0
  lsb-core totem-dbg alien libaudit0 libltdl-dev libaprutil1 libgail-gnome-dbg
  libnjb5 libgdl-1-3 gimp-dbg python-gobject-dbg libgstreamer0.10-0-dbg
  python-gtk2-dbg libgdl-1-common lsb-cxx
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  flashplugin-nonfree*
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 168kB disk space will be freed.
Do you want to continue [Y/n]?

Ensure that Synaptic, Update Manager and Add/Remove Programs is CLOSED before you run the commands I listed- sorry I didnt clarify this. Whenever it says that APT is locked with:
> E: Could not open lock file /var/lib/apt/lists/lock - open (13: Permission denied)
E: Unable to lock the list directory
that usually means that something is using apt. **EDIT** In this case it means im an idiot who forgot to put sudo in front of the command 'apt-get install' (apt-get install needs to be run as root) ;)

After its all closed, run the following commands:
```
sudo dpkg --configure -a
sudo apt-get update
sudo apt-get install -f
sudo apt-get install ubuntu-desktop
sudo apt-get dist-upgrade
sudo apt-get purge flashplugin-nonfree flashplugin-installer
sudo apt-get install flashplugin-installer
```

I am trying to get APT back the way it should be so you dont have any issues. Let me know the output of those commands.

---

### Post by lyni on 2010-05-05
thanks GSF1200S.
I looked at the Known Bugs and they gave some directions there so I now have the Flashplugin.

but the Desktop is a tan colour rather than purple and a couple of the Icons on the top Panel are not quite right - ie where the Firefox Icon should be I have a Black Square.

is there something I can do about the Desktop and the Icons?

thanks again for taking the time to assist.

---

### Post by GSF1200S on 2010-05-05
> **lyni said:**
> thanks GSF1200S.
I looked at the Known Bugs and they gave some directions there so I now have the Flashplugin.

but the Desktop is a tan colour rather than purple and a couple of the Icons on the top Panel are not quite right - ie where the Firefox Icon should be I have a Black Square.

is there something I can do about the Desktop and the Icons?

thanks again for taking the time to assist.

There is a good chance that you dont have all the applications of Ubuntu because the update process failed. Please run all the above commands EXCEPT for the ones concerning the flashplugin-installer. When you showed me your apt printout, it suggested you remove a LOT of packages, and I dont want this to be an issue for you later. You should have all your icons back and apt should be good if you run at least these commands:
```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get install -f
sudo apt-get ubuntu-desktop
```
Let me know what the output of these commands is and where or not your icons come back. You might need to restart X in order for the icons to come back; save all open documents and then run:
```
sudo /etc/init.d/gdm restart
```
and hopefully everything should be good.

---

### Post by lyni on 2010-05-05
here is the read out for that list of commands:

lyn@lyn-desktop:~$ sudo apt-get update
[sudo] password for lyn: 
Ign cdrom://Ubuntu 10.04 LTS _Lucid Lynx_ - Release i386 (20100429)/ lucid/main Translation-en_AU
Ign cdrom://Ubuntu 10.04 LTS _Lucid Lynx_ - Release i386 (20100429)/ lucid/restricted Translation-en_AU
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) lucid Release.gpg                             
Hit [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) lucid/main Translation-en_AU          
Hit [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) lucid/restricted Translation-en_AU    
Ign [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) lucid/universe Translation-en_AU      
Hit [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) lucid/multiverse Translation-en_AU    
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) lucid-updates Release.gpg
Ign [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) lucid-updates/main Translation-en_AU
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid Release.gpg
Ign [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) lucid/partner Translation-en_AU       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security Release.gpg                      
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/main Translation-en_AU   
Ign [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) lucid-updates/restricted Translation-en_AU
Ign [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) lucid-updates/universe Translation-en_AU
Ign [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) lucid-updates/multiverse Translation-en_AU
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid Release 
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/restricted Translation-en_AU
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/universe Translation-en_AU
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/multiverse Translation-en_AU
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security Release                          
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) lucid Release                                 
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) lucid-updates Release                         
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) lucid/main Packages                 
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) lucid/restricted Packages           
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) lucid/main Sources
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) lucid/restricted Sources            
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) lucid/universe Packages             
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) lucid/universe Sources              
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) lucid/multiverse Packages           
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid/partner Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/main Packages
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) lucid/multiverse Sources
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) lucid-updates/main Packages         
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) lucid-updates/restricted Packages   
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) lucid-updates/main Sources
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) lucid-updates/restricted Sources
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) lucid-updates/universe Packages
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) lucid-updates/universe Sources
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) lucid-updates/multiverse Packages
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) lucid-updates/multiverse Sources
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid/partner Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/multiverse Sources
Reading package lists... Done
lyn@lyn-desktop:~$

---

### Post by GSF1200S on 2010-05-05
> **lyni said:**
> here is the read out for that list of commands:

lyn@lyn-desktop:~$ sudo apt-get update
[sudo] password for lyn: 
Ign cdrom://Ubuntu 10.04 LTS _Lucid Lynx_ - Release i386 (20100429)/ lucid/main Translation-en_AU
Ign cdrom://Ubuntu 10.04 LTS _Lucid Lynx_ - Release i386 (20100429)/ lucid/restricted Translation-en_AU
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) lucid Release.gpg                             
Hit [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) lucid/main Translation-en_AU          
Hit [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) lucid/restricted Translation-en_AU    
Ign [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) lucid/universe Translation-en_AU      
Hit [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) lucid/multiverse Translation-en_AU    
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) lucid-updates Release.gpg
Ign [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) lucid-updates/main Translation-en_AU
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid Release.gpg
Ign [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) lucid/partner Translation-en_AU       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security Release.gpg                      
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/main Translation-en_AU   
Ign [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) lucid-updates/restricted Translation-en_AU
Ign [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) lucid-updates/universe Translation-en_AU
Ign [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) lucid-updates/multiverse Translation-en_AU
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid Release 
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/restricted Translation-en_AU
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/universe Translation-en_AU
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/multiverse Translation-en_AU
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security Release                          
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) lucid Release                                 
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) lucid-updates Release                         
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) lucid/main Packages                 
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) lucid/restricted Packages           
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) lucid/main Sources
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) lucid/restricted Sources            
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) lucid/universe Packages             
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) lucid/universe Sources              
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) lucid/multiverse Packages           
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid/partner Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/main Packages
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) lucid/multiverse Sources
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) lucid-updates/main Packages         
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) lucid-updates/restricted Packages   
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) lucid-updates/main Sources
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) lucid-updates/restricted Sources
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) lucid-updates/universe Packages
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) lucid-updates/universe Sources
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) lucid-updates/multiverse Packages
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) lucid-updates/multiverse Sources
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid/partner Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/multiverse Sources
Reading package lists... Done
lyn@lyn-desktop:~$

I can see that this is your printout for:
```
sudo apt-get update
```
but wheres the printout for the other commands? Try the following command, but DO NOT hit 'y' if it asks you whether you want to remove packages- hit 'n' instead:
```
sudo apt-get autoremove
```
Paste the results here. When you attempted to delete flashplugin-installer before, it gave a HUGE list of packages that you "no longer" needed. Im just making sure you dont do apt-get autoremove at somepoint and remove half your desktop. You should be fine if you ran the commands in my earlier replies, but im just trying to make sure to help you ;)

---

### Post by lyni on 2010-05-05
thank you very much GSF1200S.
I turned off before I received your last reply. but on restarting the system seems to all be right. I got the purple Desktop and thing so far seem to be okay. I'll go through everything now and make sure that they all work.

thank you again for all your assistance.

---

### Post by GSF1200S on 2010-05-05
> **lyni said:**
> thank you very much GSF1200S.
I turned off before I received your last reply. but on restarting the system seems to all be right. I got the purple Desktop and thing so far seem to be okay. I'll go through everything now and make sure that they all work.

thank you again for all your assistance.

No problem :)

---

