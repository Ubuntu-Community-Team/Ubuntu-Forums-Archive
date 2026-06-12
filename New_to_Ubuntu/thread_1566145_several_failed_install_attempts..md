---
title: "several failed install attempts."
date: 2010-09-02
forum: New to Ubuntu
---

### Post by shawnic on 2010-09-02
I'm trying to install Ubuntu onto a harddrive my friend gave me.
I made a boot disk for 10.04 and it seems to be loading but then it just goes to a blackscreen with a bunch of words.
I tried the alternate installer and it was working until it tried to install the base system. It kept saying that the various components were missing.
now the harddrive is wiped.
I tried to boot from a usb memory stick but my computer won't boot from it, even though I set 'generic usb device' to top priority.
I really want to get Ubuntu but i dont know what to do.
please help.

---

### Post by Gone fishing on 2010-09-02
Try the CD again (cut another in case it has a problem) it is a live CD so will allow you to try Ubuntu without installing. If this works the install will work. If the live CD doesn't work properly post the worlds you see on the black screen.

---

### Post by Elfy on 2010-09-02
Have you checked that the discs are burnt correctly? [https://help.ubuntu.com/community/Installation/CDIntegrityCheck](https://help.ubuntu.com/community/Installation/CDIntegrityCheck) 

Possibly you will need to press any key to get the boot menu up.

HAve you checked the md5sum? [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

[https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes)

You might also find that you have a lot of partitions if you have been getting past the partition stage of the install. You can check from a terminal with 

```
sudo fdisk -l
```

---

### Post by shawnic on 2010-09-02
I'm all out of blank CD's. Would a DVD work?
When I burned them I used ISO recorder 3.1 at 8x speed(lowest it had), because for some reason ImgBurn wasn't working.

---

### Post by ibizatunes on 2010-09-02
Specs of your machine?
Does it have 512 of RAM min
and a 1Ghz processor?
Check the disc for errors, before trying to install
What is the model or your machine

---

### Post by coffeecat on 2010-09-02
Post details of your system specs, including and especially the graphics card. It could be that you have one of the graphics chipsets that prevent booting into the GUI desktop. Some of the ATI cards do this.

---

### Post by shawnic on 2010-09-02
Vista Home Premium  32-bit  v6.0.6001  Service Pack 1
intel Celeron 2.0GHz, 2 Cores, 2 Logical Processors
installed RAM- 2.00 GB
Total RAM- 1.75 GB
Available RAM- 969 MB
Total Virtual Memory- 3.74 GB
Available Virtual Memory- 2.67 GB
DirectX 10
The computer is an eMachines

---

### Post by coffeecat on 2010-09-02
> **coffeecat said:**
> Post details of your system specs, **including and especially the graphics card.**

> **shawnic said:**
> Vista Home Premium  32-bit  v6.0.6001  Service Pack 1
intel Celeron 2.0GHz, 2 Cores, 2 Logical Processors
installed RAM- 2.00 GB
Total RAM- 1.75 GB
Available RAM- 969 MB
Total Virtual Memory- 3.74 GB
Available Virtual Memory- 2.67 GB
DirectX 10
The computer is an eMachines

Nope. Can't see it. :confused:

:wink:

Somewhere in the Windows control panel (I can't remember where exactly) it should give you details of your graphics card if you don't know this.

---

