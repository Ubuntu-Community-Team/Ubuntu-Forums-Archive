---
title: "Boot Advice Needed"
date: 2009-11-18
forum: New to Ubuntu
---

### Post by nheather on 2009-11-18
Firstly let me say that my knowledge of Linux is pretty limited.

However, I have an installation of Ubuntu which I use now and then.  It is installed on it's own hard drive and it took me some time and effort to get right - I'm a beginner so it took a lot of Googling to install extra applications and configure them, most of which I completed without 100% understanding and I doubt I could replicate it easily.

I currently boot from GRUB installed on my main Windows XP hard disk.

I will soon be doing a hardware upgrade and moving to Windows 7.  This will mean reformatting my disk so I will lose GRUB.

I really want to keep my Ubuntu but with my limited knowledge I wont be able to boot it after the upgrade.

So is there a way of creating a Boot CD or USB Stick which will allow me to get into Ubuntu.

Someone suggested Super GRUB - I have installed it to a bootable CD but I must confess that having done so I haven't a clue what I need to do with it.

Is SuperGrub the answer - if so is there a beginner's guide you could recommend?

Or is there a better way?

Many thanks,

Nigel

---

### Post by bumanie on 2009-11-18
It would help to know which version of ubuntu you are using as the latest (karmic) has the grub2 bootloader, whereas previous versions had what is now called grub-legacy as the default bootloader - the installation procedure off a live cd differs between the two versions of grub.

---

### Post by ukripper on 2009-11-18
If you are installing Ubuntu 9.10 or later (comes with GRUB2)then you will need to follow the steps given in this guide - [https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD](https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD) ,  look for "**Reinstalling GRUB 2**" section

---

### Post by nheather on 2009-11-18
Not sure which version - will boot into Ubuntu and find out.

Back soon.

Cheers,

Nigel

---

### Post by nheather on 2009-11-18
The version is 8.10.

But it may be a moot point because the installation doesn't appear to be working any more.

When I slect Ubuntu 8.10 from Grub, the screen goes black and then displays

Boot from (hd1,0) ext3 {serial number}
Starting up...

and that's it.  No matter how long I leave it it just sticks there.


Only recent change is the graphics card - was an 8800GTS now an HD4890.

Cheers,

Nigel

---

### Post by ukripper on 2009-11-19
looking at (hd1,0) i assume you have got two HDDs and second one runs your ubuntu 8.10. Do you get any error at all? during grub like Error 15 or 17 or anyother?

---

### Post by nheather on 2009-11-19
Yes you are correct, Ubuntu is on it's own hard disk.

No error codes, was working fine before, now I just get stuck at

> Starting up...

My first thought was that I may have knocked the SATA cable when I installed the Graphics Card but have since dismissed this because

(a) When I look in Windows Device manager, both my hard disks are present

(b) I believe that GRUB configuration is stored on this disk

Cheers,

Nigel

---

### Post by ukripper on 2009-11-19
> **nheather said:**
> Yes you are correct, Ubuntu is on it's own hard disk.

No error codes, was working fine before, now I just get stuck at



My first thought was that I may have knocked the SATA cable when I installed the Graphics Card but have since dismissed this because

(a) When I look in Windows Device manager, both my hard disks are present

(b) I believe that GRUB configuration is stored on this disk

Cheers,

Nigel



[LIST=1]
[*]Can you see your Ubuntu HDD  in BIOS?
[*]If you can see your HDD in BIOS. Could you boot from your ubuntu 8.10 Live cd and post output of the following command:
```
sudo fdisk -l
```
[/LIST]

---

