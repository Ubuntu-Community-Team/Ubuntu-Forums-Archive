---
title: "ATI prorietary drivers? - Back to Ubuntu but haven't used it since version 6"
date: 2009-11-13
forum: New to Ubuntu
---

### Post by ovimunt on 2009-11-13
Hello everyone,


After a long while I've decided to get Ubuntu again so I've just installed the 9.10 release. As I mentioned in the subject, I haven't used Ubuntu since version 6 (which means a very long time ago) and back then intalling ATI proprietary drivers used to be a bit tricky. For example I remeber that you had to uninstall the open source drivers first and then install the ATI drivers. 

Anyway, with the 9.10 release I have noticed that quite a few things are a lot easier to do and a lot more user firendly. So before I go on and mess something up in my fresh installation I though that maybe I should ask to see if there is now some automated way to intall the ATI proprietary drivers, out of the box, with no command line and etc. And if there is no such thing then maybe someone could point me to right thread?

Thanks a lot!

---

### Post by ukripper on 2009-11-13
Welcome back!

click on System-->Administration-->Hardware drivers. This will detect your graphics card automatically. if it doesnt post output of the following command:
```
lspci
```

---

### Post by ovimunt on 2009-11-13
Umm... is is really that simple? Will that install the **ATI Proprietary Drivers**? :???:

---

### Post by Nightstrike2009 on 2009-11-13
NON-INTERNET USERS: I use these debs from:[http://packages.ubuntu.com/]("http://packages.ubuntu.com/")

[COLOR="Green"]dkms_2.0.21.1-0ubuntu3_all.deb
patch_2.5.9-5_i386.deb
fakeroot_1.12.1ubuntu1_i386.deb
fglrx-amdcccle_8.600-0ubuntu2_i386.deb
fglrx-kernel-source_8.600-0ubuntu2_i386.deb
xorg-driver-fglrx_8.600-0ubuntu2_i386.deb[/COLOR]

Install dkms_2.0.21.1-0ubuntu3_all.deb first then re-boot Ubuntu once Installed.

After Ubuntu has rebooted, go to (Title Bar) System>Administration>Hardware Drivers your card should be detected in Hardware Drivers, if not don't continue with these instructions until it has (Or it will crash Ubuntu on boot-up). 

---------------------------------------------------------------------------------------------------

[COLOR="Green"]INTERNET USERS: If you are connected to internet you should connect then, click Enable in Hardware Drivers and Ubuntu should download dependencies & Install Automatically. After completing reboot Ubuntu as requested by Hardware Drivers.[/COLOR]

---

### Post by ukripper on 2009-11-13
> **ovimunt said:**
> Umm... is is really that simple? Will that install the **ATI Proprietary Drivers**? :???:

Depends on the ati card you using. New Nv/ATI cards are well supported with ubuntu 9.10 automatically download and install after the installation upon first login. For old cards you may be able to use Envyng tool. again depending on your card.

[http://ubuntuguide.net/install-nvidiaati-graphics-card-driver-in-ubuntu-910karmic](http://ubuntuguide.net/install-nvidiaati-graphics-card-driver-in-ubuntu-910karmic)

---

### Post by proxess on 2009-11-13
Install the proprietary drivers ONLY, and ONLY if you have a HD series card (HD2xxx or more). If you don't, be happy with the open-source drivers like the rest of us.

As for the open-source drivers, use either Radeon (or ATI, they're the same) or RadeonHD.

---

### Post by ovimunt on 2009-11-13
Right, I guess I should post my full system specs too:

2 x ATI Radeon HD 4850 (CrossFire)
Intel Core 2 Duo E8400
8GB RAM
1TB HDD
Gigabyte GA-X48-DQ6 Motherboard

Also, I'm not in front of my computer right now so I can't go and try the various options but will do as soon as I get home. And untill then I want to make sure I'm trying to right thing to start with.

Thanks again

---

### Post by ukripper on 2009-11-13
Catalyst 9.10 Linux - [http://blogs.amd.com/play/2009/10/22/ati-catalyst%E2%84%A2-9-10-driver-%E2%80%93-what%E2%80%99s-new/](http://blogs.amd.com/play/2009/10/22/ati-catalyst%E2%84%A2-9-10-driver-%E2%80%93-what%E2%80%99s-new/)

---

### Post by Dvdre on 2009-11-13
I'm going to guess you will run into problems installing that ATI Radeon driver. I have the ATI 4570 in a Sony laptop and had no luck at all getting a driver installed in 9.10

In 9.04 I used the EnvyNG program to install it and it worked first time.

In 9.10 EnvyNG did not properly install and I tried multiple other recommended solutions and none worked. 

This wasn't my only problem with 9.10 so I reinstalled 9.04, which is plenty nice.

---

### Post by ukripper on 2009-11-13
From my personal experience, if i have an ATI card i will stick to ubuntu 9.04 or may be 8.04 LTS(for old card support) till 10.04 comes out. I am using ubuntu 9.10 on testing machines with Nvidia cards and on my clients main machines with same nvidia cards.

---

### Post by QIII on 2009-11-13
On the other hand...

I have an ATI HD series, have installed the ATI 9.10 driver from the repos (ATI pushed it out specifically to get it in Karmic and only later made it available for public consumption) and I am very happy with the results.

---

