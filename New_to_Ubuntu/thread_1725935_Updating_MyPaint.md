---
title: "Updating MyPaint"
date: 2011-04-10
forum: New to Ubuntu
---

### Post by tinyyuki on 2011-04-10
Okay, I'm not sure why this isn't working, but I'm trying to update my version of the art program MyPaint from version 0.8.2 to version 0.9.0. I have the tar.bz2 file on my desktop, and I already have it unpacked. I tried to follow the readme directions in the folder (scons && ./mypaint), and it tells me I don't have scons installed. When I try to install scons (sudo apt-get install scons), I get:


```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  ttf-mscorefonts-installer
The following NEW packages will be installed:
  scons
The following packages will be upgraded:
  ttf-mscorefonts-installer
1 upgraded, 1 newly installed, 0 to remove and 82 not upgraded.
1 not fully installed or removed.
E: Could not get lock /var/cache/apt/archives/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the download directory
```

I also noticed that I have 82 not upgraded things, so when I went to my update manager and tried to update everything, I got:

E: Could not get lock /var/cache/apt/archives/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the download directory

My computer has been acting really weird since my dad changed me from the administrator to a desktop user, and back to an administrator. It's kinda weird.

I have Ubuntu Studio.

Any help is much appreciated. Thanks so much in advance!

Tinyyuki

---

### Post by Locke_99GS on 2011-04-10
```

lsof | grep /var/cache/apt/archives/lock

```

Will let you know what process has that file. (the lock) Close it or kill it, then try again.

---

### Post by tinyyuki on 2011-04-10
I tried that code and I'm not getting anything back. It just pauses then gives another line to try another code. I'm not sure I described that right. >.<


```
mariann@ubuntu:~$ lsof | grep /var/cache/apt/archives/lock
mariann@ubuntu:~$ lsof | grep /var/cache/apt/archives/lock
mariann@ubuntu:~$
``` 

that's what happens.

---

### Post by jtarin on 2011-04-10
Try your installation command with the preface "sudo".

---

### Post by tinyyuki on 2011-04-10
The command wasn't found. Arghhh! Maybe my computer is just crap. >.< I really just wanted to add more brushes to the program, but I can't find the option to do that, so I think updating it might fix it. But now it won't update! >.<

---

### Post by Perfect Storm on 2011-04-10
It might be that you have Ubuntu Software Center/Synaptic Package Manager open while doing it. Close them.
Try again with:
```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by tinyyuki on 2011-04-10
The update command worked, but the upgrade command didn't, even after fixing "gt" to "get." >.< All I have open is the terminal and my browser.

---

### Post by Perfect Storm on 2011-04-10
Can you please post the full in/output of previous command.

Also try  rebooting. It can be that somewhere someplace it's locked in the system.

---

### Post by jtarin on 2011-04-11
Have you tried just adding brushes manually? I don't have MyPaint installed but I've done things like this in many applications (Gimp) when the import functions are not there or non-existent. With your version it indicates you can also make and save brushes. What version of Ubuntu are you running? In 10.04 the current version is 9.0.1 as you wanted (listed in Synaptic)

---

### Post by madjr on 2011-04-11
install mypaint from getdeb:

[http://www.getdeb.net/app/MyPaint](http://www.getdeb.net/app/MyPaint)

or
[http://www.multimediaboom.com/how-to-install-mypaint-0-9-x-using-ppa-in-ubuntu-9-10-10-04-9-04/](http://www.multimediaboom.com/how-to-install-mypaint-0-9-x-using-ppa-in-ubuntu-9-10-10-04-9-04/)

also you may want to try similar programs like **krita or gimp paint studio** edition

[http://www.webupd8.org/2011/02/gimp-painter-and-gimp-paint-studio.html](http://www.webupd8.org/2011/02/gimp-painter-and-gimp-paint-studio.html)


for you, i would not recommend installing from source, use a .deb or ppa instead if its not already in the software center.

---

### Post by tinyyuki on 2011-04-11
```
Hit http://security.ubuntu.com lucid-security Release.gpg
Ign http://security.ubuntu.com/ubuntu/ lucid-security/main Translation-en_US
Ign http://security.ubuntu.com/ubuntu/ lucid-security/restricted Translation-en_US
Hit http://us.archive.ubuntu.com lucid Release.gpg                   
Ign http://us.archive.ubuntu.com/ubuntu/ lucid/main Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ lucid/restricted Translation-en_US
Hit http://ppa.launchpad.net lucid Release.gpg                       
Ign http://ppa.launchpad.net/doctormo/wacom-plus/ubuntu/ lucid/main Translation-en_US
Hit http://ppa.launchpad.net lucid Release.gpg                       
Ign http://security.ubuntu.com/ubuntu/ lucid-security/universe Translation-en_US
Ign http://security.ubuntu.com/ubuntu/ lucid-security/multiverse Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ lucid/universe Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ lucid/multiverse Translation-en_US
Hit http://us.archive.ubuntu.com lucid-updates Release.gpg           
Ign http://us.archive.ubuntu.com/ubuntu/ lucid-updates/main Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ lucid-updates/restricted Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ lucid-updates/universe Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ lucid-updates/multiverse Translation-en_US
Ign http://ppa.launchpad.net/hughescih/ppa/ubuntu/ lucid/main Translation-en_US
Hit http://ppa.launchpad.net lucid Release.gpg                       
Ign http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/ lucid/main Translation-en_US
Hit http://ppa.launchpad.net lucid Release                           
Hit http://us.archive.ubuntu.com lucid Release                       
Hit http://security.ubuntu.com lucid-security Release
Hit http://us.archive.ubuntu.com lucid-updates Release               
Hit http://ppa.launchpad.net lucid Release                           
Hit http://ppa.launchpad.net lucid Release     
Hit http://ppa.launchpad.net lucid/main Packages                               
Hit http://us.archive.ubuntu.com lucid/main Packages                 
Hit http://security.ubuntu.com lucid-security/main Packages
Hit http://ppa.launchpad.net lucid/main Packages
Hit http://ppa.launchpad.net lucid/main Packages
Hit http://us.archive.ubuntu.com lucid/restricted Packages
Hit http://us.archive.ubuntu.com lucid/main Sources
Hit http://us.archive.ubuntu.com lucid/restricted Sources
Hit http://us.archive.ubuntu.com lucid/universe Packages
Hit http://us.archive.ubuntu.com lucid/universe Sources
Hit http://security.ubuntu.com lucid-security/restricted Packages
Hit http://security.ubuntu.com lucid-security/main Sources
Hit http://security.ubuntu.com lucid-security/restricted Sources
Hit http://security.ubuntu.com lucid-security/universe Packages
Hit http://us.archive.ubuntu.com lucid/multiverse Packages
Hit http://us.archive.ubuntu.com lucid/multiverse Sources
Hit http://us.archive.ubuntu.com lucid-updates/main Packages
Hit http://us.archive.ubuntu.com lucid-updates/restricted Packages
Hit http://us.archive.ubuntu.com lucid-updates/main Sources
Hit http://security.ubuntu.com lucid-security/universe Sources
Hit http://security.ubuntu.com lucid-security/multiverse Packages
Hit http://security.ubuntu.com lucid-security/multiverse Sources
Hit http://us.archive.ubuntu.com lucid-updates/restricted Sources
Hit http://us.archive.ubuntu.com lucid-updates/universe Packages
Hit http://us.archive.ubuntu.com lucid-updates/universe Sources
Hit http://us.archive.ubuntu.com lucid-updates/multiverse Packages
Hit http://us.archive.ubuntu.com lucid-updates/multiverse Sources
Reading package lists... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages have been kept back:
  linux-generic linux-headers-generic linux-image-generic
The following packages will be upgraded:
  binutils chromium-browser chromium-browser-inspector chromium-browser-l10n
  chromium-codecs-ffmpeg-extra chromium-codecs-ffmpeg-extra-dbg
  chromium-codecs-ffmpeg-nonfree chromium-codecs-ffmpeg-nonfree-dbg dbus
  dbus-x11 firefox firefox-branding firefox-gnome-support
  flashplugin-installer flashplugin-nonfree gcj-4.4-base gcj-4.4-jre
  gcj-4.4-jre-headless gcj-4.4-jre-lib gdm gnome-screensaver krb5-multidev
  libavcodec52 libavdevice52 libavformat52 libavutil49 libdbus-1-3
  libdbus-1-dev libgcj10 libgcj10-awt libgssapi-krb5-2 libgssrpc4 libk5crypto3
  libkadm5clnt-mit7 libkadm5srv-mit7 libkdb5-4 libkrb5-3 libkrb5-dev
  libkrb5support0 libldap-2.4-2 libnss3-1d libphonon4 libpostproc51
  libqt4-assistant libqt4-dbus libqt4-designer libqt4-help libqt4-network
  libqt4-opengl libqt4-qt3support libqt4-script libqt4-scripttools libqt4-sql
  libqt4-sql-mysql libqt4-sql-sqlite libqt4-svg libqt4-test libqt4-webkit
  libqt4-xml libqt4-xmlpatterns libqtcore4 libqtgui4 libservlet2.5-java
  libsmbclient libswscale0 libtiff-tools libtiff4 linux-libc-dev
  openssh-client phonon python-gnomeapplet samba-common-bin ssh-askpass-gnome
  tex-common ttf-mscorefonts-installer tzdata tzdata-java w3m
  x11-xserver-utils xulrunner-1.9.2
80 upgraded, 0 newly installed, 0 to remove and 3 not upgraded.
1 not fully installed or removed.
E: Could not get lock /var/cache/apt/archives/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the download directory
```

> Have you tried just adding brushes manually? I don't have MyPaint installed but I've done things like this in many applications (Gimp) when the import functions are not there or non-existent. With your version it indicates you can also make and save brushes. What version of Ubuntu are you running? In 10.04 the current version is 9.0.1 as you wanted (listed in Synaptic)

I have tried adding them manually. I can't find the option to upload them. In the "brush" drop down menu on the canvas, I seem to be missing "Import Brush Package." I'm running Ubuntu Studio Lucid.


> install mypaint from getdeb:

[http://www.getdeb.net/app/MyPaint](http://www.getdeb.net/app/MyPaint)

or
[http://www.multimediaboom.com/how-to...10-10-04-9-04/](http://www.multimediaboom.com/how-to...10-10-04-9-04/)

also you may want to try similar programs like krita or gimp paint studio edition

[http://www.webupd8.org/2011/02/gimp-...nt-studio.html](http://www.webupd8.org/2011/02/gimp-...nt-studio.html)


for you, i would not recommend installing from source, use a .deb or ppa instead if its not already in the software center.

I tried installing from getdeb, and "mypaint is already installed." Yes, I know this. I'm not trying to install MyPaint. I'm trying to upgrade it from it's current version that I have installed, to a higher version. I can't figure out how to use Krita, and Gimp makes my computer lag so bad I hate using it. Thanks for trying though. :(

---

### Post by jtarin on 2011-04-11
Your not getting it through apt because your sources are being ignored. The MyPaint application is in /ubuntu/pool/universe/ for lucid. You need to add it to your sources. Just find a server that won't ignore your request.
Attached is a pic that shows where you can change servers. Choose from the dropdown and find the best...fastest.

---

### Post by madjr on 2011-04-11
> **tinyyuki said:**
> 


I tried installing from getdeb, and "mypaint is already installed." Yes, I know this. I'm not trying to install MyPaint. I'm trying to upgrade it from it's current version that I have installed, to a higher version. I can't figure out how to use Krita, and Gimp makes my computer lag so bad I hate using it. Thanks for trying though. :(

did you follow the getdeb instructions?

you need to add the getdeb ppa (repositories)

here are the instructions:
[http://www.getdeb.net/updates/Ubuntu/10.04/](http://www.getdeb.net/updates/Ubuntu/10.04/)

as for krita, am sure there are a good number of tutorials online.

---

