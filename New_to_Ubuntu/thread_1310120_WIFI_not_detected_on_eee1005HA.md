---
title: "WIFI not detected on eee1005HA"
date: 2009-11-01
forum: New to Ubuntu
---

### Post by wscrivens on 2009-11-01
I've run Ubuntu in a VM and liked it, so when I got an Asus eee 1005HA with Windows, I decided to install Ubuntu on it.
I checked the hardware compatibility page and found that the remix 9.1 worked with no problems reported so i downloaded and installed.
 
After several hours of searechnig the forums and trying different things I cannot get WIFI to work at all.
 
From Windows I learned that the WIFI is an Atheros AR9285. All of the discussion on the forums seems to be for Atheros 5K; anyhow none of the cures seem to work. I haven't tride NDISwrapper since so many people are reporting problems with it.
 
I also tried a Live CD version of Ubuntu 9.1 and had the same problems.
 
I'm out of ideas, can anyone help me, please?
 
Walt

---

### Post by bkratz on 2009-11-01
> **wscrivens said:**
> I've run Ubuntu in a VM and liked it, so when I got an Asus eee 1005HA with Windows, I decided to install Ubuntu on it.
I checked the hardware compatibility page and found that the remix 9.1 worked with no problems reported so i downloaded and installed.
 
After several hours of searechnig the forums and trying different things I cannot get WIFI to work at all.
 
From Windows I learned that the WIFI is an Atheros AR9285. All of the discussion on the forums seems to be for Atheros 5K; anyhow none of the cures seem to work. I haven't tride NDISwrapper since so many people are reporting problems with it.
 
I also tried a Live CD version of Ubuntu 9.1 and had the same problems.
 
I'm out of ideas, can anyone help me, please?
 
Walt



check out post #2 in the following and good luck!

[http://ubuntuforums.org/showthread.php?t=1286503&highlight=AR9285](http://ubuntuforums.org/showthread.php?t=1286503&highlight=AR9285)

---

### Post by mahy on 2009-11-01
Well, you'd be surprised, but the insides of a laptop can differ even within one model! (A friend of mine has a Toshiba A300, just like I do, but he's got a different BIOS, motherboard chipset, graphics card, different wi-fi card etc etc.) That means you should verify the actual type of your card. I don't know how much you can do in a Linux system, but try opening a Terminal (you'll find it in a menu), and run the following command:

lspci

then post here the results. Good luck!

---

### Post by autocrosser on 2009-11-01
Also--the ath5k driver was blacklisted during Karmic-Development---look at /etc/modprobe.d & see if there is a blacklist-ath_pci.conf   If so do in a terminal ```
1. gksudo gedit /etc/modprobe.d/blacklist-ath_pci.conf
2. when the file opens, put a # in front of "blacklist ath_pci" and save the file
3. reboot & check your wireless
```

This "MAY" fix your problem if you need the ath5k driver.

---

### Post by wscrivens on 2009-11-02
Thanks, this worked, but I'm a bit uneasy as to what I've done.  It looks like I've "Regressed" my Ubuntu to a previous version.

After installing these drivers, WIFI worked.  Once connected tot he network, the first thing Ububtu did was give me a list of high priority updates to be installed; I told it to go ahead, and after that WIFI quit again, so I installed the drivers again, and that is the state my Eee is now in.  

How do I get this machine back onto the main track with regard to upgrades?  I like to keep all my machines current, especially for security patches.

Walt

> **bkratz said:**
> check out post #2 in the following and good luck!

[http://ubuntuforums.org/showthread.php?t=1286503&highlight=AR9285](http://ubuntuforums.org/showthread.php?t=1286503&highlight=AR9285)

---

### Post by bkratz on 2009-11-02
> **wscrivens said:**
> Thanks, this worked, but I'm a bit uneasy as to what I've done.  It looks like I've "Regressed" my Ubuntu to a previous version.

After installing these drivers, WIFI worked.  Once connected tot he network, the first thing Ububtu did was give me a list of high priority updates to be installed; I told it to go ahead, and after that WIFI quit again, so I installed the drivers again, and that is the state my Eee is now in.  

How do I get this machine back onto the main track with regard to upgrades?  I like to keep all my machines current, especially for security patches.

Walt


Please check your personal messages

---

