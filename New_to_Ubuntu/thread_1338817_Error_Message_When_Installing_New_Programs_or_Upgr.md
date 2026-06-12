---
title: "Error Message When Installing New Programs or Upgrading"
date: 2009-11-26
forum: New to Ubuntu
---

### Post by cfraicol on 2009-11-26
I recently installed Ubuntu Netbook Remix on my Aspire 1 netbook and love it.  I would love it more, though, if I could install new programs or update current ones.  Every time I try to install anything I get the following error message:



                                 Extracting templates from packages: 100%
 Selecting previously deselected package freepats.
 (Reading database … 25%dpkg: unrecoverable fatal error, aborting:
      failed in buffer_read(fd): files list for package 'xserver_xorg-video-savage':
 Input/output error
 E: Sub-process /usr/bin/dpkg returned an error code (2)
 A package failed to install.  Trying to recover:
 

I have searched everywhere for information on the package "xserver-xorg-video-savage" because, to me, that seems to be the problem.  I don't know very much though so I could be completely off.  If anyone could help me out it would be awesome.

Thanks so much in advance.

---

### Post by Buuntu on 2009-11-27
```
sudo apt-get -f install
```

---

### Post by cfraicol on 2009-11-27
Thank you for the suggestion.  I did "sudo apt-get -f install" and received a message saying that 

Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 132 not upgraded.


When I go to the software center and hit the install button on a packet nothing happens.  Like... the computer doesn't freeze.  There is just no kind of response at all.  And when I go to the update manager to update the system as a whole I get the same exact error message as was the original problem.  It seems like there is a problem with "dpkg;" whatever that is. 

Any ideas?

---

### Post by philinux on 2009-11-27
Post the output from this.

```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by cfraicol on 2009-11-28
Philinux I typed that in and this is what I got.  About halfway through it prompted me to say yes or no and I went with yes.  Then I got the final error message I always seem to get.

chase@CWF-Netbook:~$ sudo apt-get update && sudo apt-get upgrade
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security Release.gpg
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/main Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/restricted Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/universe Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/multiverse Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/main Packages  
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic Release.gpg            
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/multiverse Translation-en_US
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates Release.gpg [189B]
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic Release
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates Release [44.1kB]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/main Packages                          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/restricted Packages                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/main Sources                           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/restricted Sources                     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/universe Packages                      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/universe Sources                       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/multiverse Packages                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/multiverse Sources                     
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/main Packages [88.5kB]       
Get:4 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/restricted Packages [14B]    
Get:5 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/main Sources [28.5kB]        
Get:6 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/restricted Sources [14B]     
Get:7 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/universe Packages [54.1kB]   
Get:8 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/universe Sources [12.2kB]    
Get:9 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/multiverse Packages [1,616B] 
Get:10 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/multiverse Sources [1,223B] 
Fetched 230kB in 7s (29.3kB/s)                                                 
Reading package lists... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages have been kept back:
  linux-generic linux-headers-generic linux-image-generic
The following packages will be upgraded:
  adduser apparmor apparmor-utils apport apport-gtk avahi-autoipd avahi-daemon
  binutils brasero checkbox checkbox-gtk cups cups-bsd cups-client cups-common
  empathy empathy-doc evince evolution evolution-common
  evolution-documentation-en evolution-plugins f-spot firefox firefox-3.5
  firefox-3.5-branding firefox-3.5-gnome-support firefox-gnome-support
  gnome-about gnome-desktop-data gnome-settings-daemon grub-common grub-pc
  gstreamer0.10-alsa gstreamer0.10-plugins-base
  gstreamer0.10-plugins-base-apps gstreamer0.10-x gtk2-engines
  gtk2-engines-murrine gtk2-engines-pixbuf ibus ibus-gtk initscripts
  kerneloops-daemon libapparmor-perl libapparmor1 libavahi-client3
  libavahi-common-data libavahi-common3 libavahi-core6 libavahi-glib1
  libavahi-gobject0 libavahi-ui0 libbrasero-media0 libclutter-gtk-0.10-0
  libcups2 libcupscgi1 libcupsdriver1 libcupsimage2 libcupsmime1 libcupsppdc1
  libempathy-common libempathy-gtk-common libempathy-gtk28 libempathy30
  libenchant1c2a libevdocument1 libevview1 libgail-common libgail18 libgd2-xpm
  libgnome-desktop-2-11 libgstreamer-plugins-base0.10-0 libgtk2.0-0
  libgtk2.0-bin libgtk2.0-common libgudev-1.0-0 libhtml-parser-perl libibus1
  libindicate-gtk1 libindicate3 libnautilus-extension1 libpoppler-glib4
  libpoppler5 libpython2.6 libsmbclient libudev0 libvorbis0a libvorbisenc2
  libvorbisfile3 libwbclient0 linux-firmware linux-libc-dev nautilus
  nautilus-data nvidia-common poppler-utils python python-apport python-avahi
  python-ibus python-minimal python-problem-report python-ubuntuone-client
  python2.6 python2.6-minimal rhythmbox samba-common samba-common-bin
  smbclient system-tools-backends sysv-rc sysvinit-utils totem totem-common
  totem-mozilla totem-plugins tzdata ubuntu-xsplash-artwork ubuntuone-client
  ubuntuone-client-gnome udev update-manager update-manager-core xsane
  xsane-common xsplash xulrunner-1.9.1 xulrunner-1.9.1-gnome-support
129 upgraded, 0 newly installed, 0 to remove and 3 not upgraded.
Need to get 688kB/75.0MB of archives.
After this operation, 3,928kB disk space will be freed.
Do you want to continue [Y/n]? Y
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/main tzdata 2009s-0ubuntu0.9.10 [688kB]
Fetched 688kB in 6s (109kB/s)                                                  
Extracting templates from packages: 100%
Preconfiguring packages ...
(Reading database ... 25%dpkg: unrecoverable fatal error, aborting:
 failed in buffer_read(fd): files list for package `xserver-xorg-video-savage': Input/output error
E: Sub-process /usr/bin/dpkg returned an error code (2)



Thank you guys so much.

---

### Post by cfraicol on 2009-11-29
bump   Please help

---

### Post by skatinjj on 2009-11-29
```
sudo dpkg-reconfigure -a 
```

---

### Post by 3rdalbum on 2009-11-29
It sounds like your apt database has become corrupted. Try renaming /etc/var/cache/apt/pkgcache.bin so Apt won't find it, and will be forced to completely refresh package information from the server.

If you're unsure, you can rename it in the terminal like this:

```
sudo mv /var/cache/apt/pkgcache.bin /var/cache/apt/pkgcache-old.bin
```

Package list corruption is rare, it's possible that your hard disk or SSD is failing.

---

### Post by cfraicol on 2009-11-30
Would finding a new install file and reinstalling ubuntu be an option?  Or is the problem deeper than that?

---

### Post by mangaskahn on 2009-12-09
Hello, 

I am having the same problem as cfraicol and have not been able to find a solution. I have tried the suggestions above, but to no avail. 

Are there any other suggestions? Is it possible dpkg is corrupted and needs to be reinstalled?

---

### Post by mangaskahn on 2009-12-09
Found this thread while I was looking for a solution:

[http://art.ubuntuforums.org/showthread.php?t=1301928](http://art.ubuntuforums.org/showthread.php?t=1301928)

This got it working for me:

sudo rm /var/lib/dpkg/info/*
sudo dpkg --clear-avail && sudo apt-get update
sudo apt-get upgrade


Hope it helps.

---

