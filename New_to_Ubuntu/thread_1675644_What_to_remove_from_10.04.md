---
title: "What to remove from 10.04"
date: 2011-01-25
forum: New to Ubuntu
---

### Post by cjv8888 on 2011-01-25
I installed 10.04 onto my eeepc 901 with / in the 4G SSD and /home in the 16G SSD.  Now after some essentials such as languages and ubuntu-restricted-extras the 4G disk is left with less than 50MB.  I would appreciate suggestions on what to remove from / to create more room. Thanks in advance.

---

### Post by Megaptera on 2011-01-26
> **cjv8888 said:**
> I would appreciate suggestions on what to remove from / to create more room. Thanks in advance.

It's difficult to advise when we don't know what apps you use. For instance if you never use OpenOffice but just need a w/p from time to time you could remove OpenOffice and install AbiWord.

You could run some apps from a flash drive (USB stick) so you don't need them on the eeepc:
From link:"Just Download, Make Executable, and Run! These Apps have been tested on
Ubuntu 10.04 (Lucid Lynx) 32-bit, OpenSUSE 11.3 (GNOME) 32-bit , and Fedora 12 (GNOME) 32-bit." [http://portablelinuxapps.org/](http://portablelinuxapps.org/)

---

### Post by mikewhatever on 2011-01-26
You could remove quite a few things, depending on what you use what what not, but you'd probably get even better results by using the minimal iso and then installing only the programs you need.

---

### Post by Megaptera on 2011-01-26
Good guide to minimal install here [http://www.psychocats.net/ubuntu/minimal](http://www.psychocats.net/ubuntu/minimal)
Ubuntu version has changed, but method remains the same.

---

### Post by fabricator4 on 2011-01-26
> **cjv8888 said:**
> I installed 10.04 onto my eeepc 901 with / in the 4G SSD and /home in the 16G SSD.  Now after some essentials such as languages and ubuntu-restricted-extras the 4G disk is left with less than 50MB.  I would appreciate suggestions on what to remove from / to create more room. Thanks in advance.

Literally anything you don't use.  ;-)

Go ahead, get brutal.

On my 900SD I got rid of all the games (well, almost!), Ubuntu One, bluetooth stuff, and anything else I wouldn't miss.  I trolled through the installed programs and got rid of hundreds of megabytes. I know how much 100 MB is on an E-PC.

During the troll I also got rid of _all_ the old kernels and header files left by the automatic updates.  Doctrine says you should leave at least the previous known good one in case of trouble, but the current one is fine.  I'd be more worried if it wasn't the LTS release (good choice!)

You could try a lighter desktop system - I've tried it in the past and didn't particularly enjoy the loss of functionality but if your apps are command line you don't even need a desktop at all.

Getting rid of a lot of the apps didn't really save that much space, but getting rid of the extra kernals and header files saved hundreds of MB's (there was quite a few of them by that time).

Also, how much swap space did you make on the SSD?  Yes, it's "ideally" the same size as the RAM but an Eee-PC just doesn't have a lot to spare.  Mine is 384Mb and I've had no trouble going into (or out of) suspend mode, but I am a little bit careful about memory usage.  I have GKrellm running to monitor memory usage (also CPU, disk activity(sda,adb,adc) and network).  It only takes a few MB's and very little other resources.

I love my 900SD:KS

Chris

---

### Post by Rubi1200 on 2011-01-26
The one thing that has not been mentioned so far is the following:

whatever you decide to remove, make sure you look at what it takes with it otherwise you can find yourself with no system to boot into!

---

### Post by lavinog on 2011-01-26
install bleachbit, and purge language files that you do not need (need to do this as a superuser)

Also open synaptic and sort by installed size.
Remove large packages that you don't want one by one.  If you get a dependency message, you may want to skip that package.

Also look for foreign fonts that you don't need in synaptic.

---

### Post by Wobblybob on 2011-01-26
Have a look at /var/cache/apt/archives you will find all the packages that have been installed so far which are then saved on your system so that if in the future you need to reinstall then the system does not need to download them again. These take up quite a few MB so if you don't mind having to re download them if you ever need to reinstall them delete all the .debs.

Also install localepurge it removes and continues to remove all language files you don't use.

---

### Post by fabricator4 on 2011-01-26
> **Wobblybob said:**
> Have a look at /var/cache/apt/archives you will find all the packages that have been installed so far 

Nice one, I just got 227 MB back.  For some reason I ASSumed computer janitor would get rid of stuff like that.

Chris.

---

### Post by cjv8888 on 2011-01-28
Thanks for all the suggestions above.  
Now I have a problem.

I went into /var/cache/apt/archives using gksu nautilus and found about 500MB of .deb files there so I move them into Trash, but when I look at the Trash to delete them, the Trash is empty! And the 500 MB of space had not been recovered.  Where have those files gone?

---

### Post by NightwishFan on 2011-01-28
The root trash, probably a hidden file in your / directory called .trash_something.

---

### Post by cjv8888 on 2011-01-28
I found the files at /root/.local/share/Trash/files

How do I remove them?

---

### Post by cjv8888 on 2011-01-28
Done it.  Removed the files by doing a rm -rf
Thanks for all the suggestions.
Now I got back 800MB by removing the old kernels and the files in the archives.  I will mark this as solved.

---

