---
title: "Using GPARTED to change unallocated to my ubuntu drive"
date: 2011-08-19
forum: New to Ubuntu
---

### Post by JerkyMcgee on 2011-08-19
I am on a usb boot of ubuntu and took some of my main WINDOWS 7 drive and put it to unallocated, thinking that I could then put it to ubunto.
BUT
Apparently my drive with Ubuntu has a maximum capacity...
How do I increase this maximum to add the unallocated space to it?

---

### Post by Basher101 on 2011-08-19
From what i read, you want to add the unallocated space to your usb drive?

---

### Post by JerkyMcgee on 2011-08-19
> **Basher101 said:**
> From what i read, you want to add the unallocated space to your usb drive?
no, to the drive that I use UBUNTU with.
The only way to have access to my windows drive though was to boot off of a usb.

---

### Post by Basher101 on 2011-08-19
so you cant boot into windows right now? and you want to install ubuntu onto a seperate partition? That partition must be at least ~5 GB big, also you will need swap space (not necessary if you have enough RAM)

---

### Post by fdrake on 2011-08-19
> **JerkyMcgee said:**
> no, to the drive that I use UBUNTU with.
The only way to have access to my windows drive though was to boot off of a usb.




If you are using gparted from a usb-boot live desktop, unmount the ubuntu partition first and then use the borders (arrows) of the side of the partition to increase or lower the size of ubuntu. But remember first you need to "unmount" the partition first.

ps from what i understand u have both win 7 and ubuntu installed right?

---

### Post by JerkyMcgee on 2011-08-19
> **Basher101 said:**
> so you cant boot into windows right now? and you want to install ubuntu onto a seperate partition? That partition must be at least ~5 GB big, also you will need swap space (not necessary if you have enough RAM)
Ahh I'm sorry,
Ubuntu is already installed onto my computer, but only with 16gbs.
I am on a bootable, smaller version so that I can edit my drives easier!
Basically I want to increase the maximum size of ubunto so that I can move the unallocated space over to it.
Does this make sense?

---

### Post by Basher101 on 2011-08-19
Please attach a screenshot of GParted so we can see how your partitions are set up. If the unallocated space is in front of your ubuntu partition its hard to add it to the ubuntu partition

---

### Post by JerkyMcgee on 2011-08-19
> **Basher101 said:**
> Please attach a screenshot of GParted so we can see how your partitions are set up. If the unallocated space is in front of your ubuntu partition its hard to add it to the ubuntu partition

OKay, there should be an attatchement
THe top one is my ubuntu drive.

---

### Post by fdrake on 2011-08-19
you don't have an ubuntu partition . it looks like you have ubuntu installed in windows wit wubi.exe, right?

---

### Post by bodhi.zazen on 2011-08-19
IMO wubi is for trying Ubuntu, if you like what you see I suggest a standard installation.

You do NOT use gparted to manage wubi, you use gparted to manage your physical partitions on your disk.

To increase the size of your wubi disk see :

[http://ubuntuforums.org/showthread.php?t=1625371](http://ubuntuforums.org/showthread.php?t=1625371)

To migrate your wubi disk to a physical partition see:

[http://ubuntuforums.org/showthread.php?t=1519354](http://ubuntuforums.org/showthread.php?t=1519354)

If that seems too complicated, remove wubi and install ubuntu. You will loose all your data and customizations if you go this route.

[https://wiki.ubuntu.com/WubiGuide#Uninstallation](https://wiki.ubuntu.com/WubiGuide#Uninstallation)

[https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)

---

### Post by JerkyMcgee on 2011-08-19
> **bodhi.zazen said:**
> IMO wubi is for trying Ubuntu, if you like what you see I suggest a standard installation.

You do NOT use gparted to manage wubi, you use gparted to manage your physical partitions on your disk.

To increase the size of your wubi disk see :

[http://ubuntuforums.org/showthread.php?t=1625371](http://ubuntuforums.org/showthread.php?t=1625371)

To migrate your wubi disk to a physical partition see:

[http://ubuntuforums.org/showthread.php?t=1519354](http://ubuntuforums.org/showthread.php?t=1519354)

If that seems too complicated, remove wubi and install ubuntu. You will loose all your data and customizations if you go this route.

[https://wiki.ubuntu.com/WubiGuide#Uninstallation](https://wiki.ubuntu.com/WubiGuide#Uninstallation)

[https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)

Thanks!
GOt it working now...
Now to get FF7 working on wine....

---

