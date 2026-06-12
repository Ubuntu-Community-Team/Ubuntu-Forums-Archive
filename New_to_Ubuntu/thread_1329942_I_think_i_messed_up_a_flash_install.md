---
title: "I think i messed up a flash install"
date: 2009-11-17
forum: New to Ubuntu
---

### Post by techforay on 2009-11-17
I have just installed ubuntu 9.10 on my daughters lap top.  She was trying to watch youtube video and were being told that flash needed to be downloaded.  I tried to download one of the options I was given and I think I messed something up.  I looked at another thread and it said to run the following code and you will see the error that I am getting.  Please help.  I am a absolute novice at linux

ashley@ashley-laptop:~$ sudo apt-get install flashplugin-nonfree
[sudo] password for ashley: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: The package adobe-flashplugin needs to be reinstalled, but I can't find an archive for it.

---

### Post by mikewhatever on 2009-11-17
Try the following:

```

sudo apt-get purge swfdec-gnome swfdec-mozilla gnash mozilla-plugin-gnash
sudo apt-get autoremove
sudo apt-get install flashplugin-installer

```

It should get rid of the other thing you tried installing and install Adobe flash plugin. Close your browser before running these and post the output if possible.

---

### Post by techforay on 2009-11-17
I know this is a basic question but do you run these codes all at once in the terminal window or indivualy.

---

### Post by gradinaruvasile on 2009-11-17
One at a time. Copy-paste one line at a time in the terminal then press enter.

---

### Post by techforay on 2009-11-17
I tried shuting down the browser before I ran these codes but when I did i lost what I copied.  Here are the results

ashley@ashley-laptop:~$ sudo apt-get purge swfdec-gnome swfdec-mozilla gnash mozilla-plugin-gnash
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: The package adobe-flashplugin needs to be reinstalled, but I can't find an archive for it.
ashley@ashley-laptop:~$ sudo apt-get autoremove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: The package adobe-flashplugin needs to be reinstalled, but I can't find an archive for it.
ashley@ashley-laptop:~$ sudo apt-get install flashplugin-installer
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: The package adobe-flashplugin needs to be reinstalled, but I can't find an archive for it.
ashley@ashley-laptop:~$

---

### Post by mikewhatever on 2009-11-18
Try updating the package list with
```
sudo apt-get update
```

and then reinstalling flash
```
sudo apt-get --reinstall install flashplugin-installer
```

---

### Post by techforay on 2009-11-18
The results

sudo apt-get update
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic Release.gpg                            
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/main Translation-en_US                 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security Release.gpg
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates Release.gpg
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/multiverse Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/restricted Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/universe Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/main Packages        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/multiverse Sources
Reading package lists... Done
ashley@ashley-laptop:~$ sudo apt-get --reinstall install flashplugin-installer
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: The package adobe-flashplugin needs to be reinstalled, but I can't find an archive for it.
ashley@ashley-laptop:~$

---

### Post by mikewhatever on 2009-11-18
A search shows it's not an infrequent problem with flash.

```
I was having this error and fixed it by doing:

sudo rm /var/lib/dpkg/info/adobe-flashplugin.prerm
sudo dpkg-reconfigure adobe-flashplugin --force
sudo dpkg --purge --force-all adobe-flashplugin
```

The stuff above has been reported to work.
Link for reference-> [http://ubuntuforums.org/archive/index.php/t-1141450.html](http://ubuntuforums.org/archive/index.php/t-1141450.html)

---

