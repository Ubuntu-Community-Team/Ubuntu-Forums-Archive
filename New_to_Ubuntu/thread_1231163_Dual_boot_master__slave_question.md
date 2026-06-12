---
title: "Dual boot master / slave question"
date: 2009-08-04
forum: New to Ubuntu
---

### Post by Danne_M on 2009-08-04
Hi everybody,
 
I am new to Linux and have not yet started my first installation. I will install UBUNTU 9.04 on a DELL Inspiron 8200 where I have already Win XP installed on a Western Digital IDE disk. I have bought a second WD IDE disk and my objective is to be able to choose XP or Linux at startup.
 
My question is now how the two disks should be strapped. I have understood that I should set up the BIOS to boot the Linux disk first since Linux (GRUB) will recognize that an XP disk is present as well, and offer the choice which system to boot, but how do I strap the two disks?
Linus master & xp slave?
Linux master & xp master?
 
And what about the third strap option on the WD disks, "master with slave"??
 
Please give me some advice how to do.
 
Best regards,
Dan (in Sweden)

---

### Post by wizard10000 on 2009-08-04
> **Danne_M said:**
> Hi everybody,
 
I am new to Linux and have not yet started my first installation. I will install UBUNTU 9.04 on a DELL Inspiron 8200 where I have already Win XP installed on a Western Digital IDE disk. I have bought a second WD IDE disk and my objective is to be able to choose XP or Linux at startup.
 
My question is now how the two disks should be strapped. I have understood that I should set up the BIOS to boot the Linux disk first since Linux (GRUB) will recognize that an XP disk is present as well, and offer the choice which system to boot, but how do I strap the two disks?
Linus master & xp slave?
Linux master & xp master?
 
And what about the third strap option on the WD disks, "master with slave"??
 
Please give me some advice how to do.
 
Best regards,
Dan (in Sweden)

Your drives should probably be jumpered as cable select on any machine built in the last several years.  That way the drive on the end of the cable is master and the one on the connector closest to the motherboard is slave.

Your IDE cable also needs to support cable select but that shouldn't be an issue with any machine built in the last five or six years.

But to answer your question you can't jumper two drives as master on the same channel - if you're building for performance you'd want the drives on separate channels as the slave drive uses the controller hardware of the master drive - that's why they call it a slave  ;)

Hope this helps -

---

### Post by egalvan on 2009-08-04
> **Danne_M said:**
> Hi everybody,
 
new to Linux... not yet started my first install... I will install UBUNTU 9.04
 I have Win XP installed on a WD IDE disk.
 I have a second WD IDE disk ...
objective is to choose XP or Linux at startup.


Bog-standard aim of a dual boot...
nothing to see here, move along.
 
> ...I should set up the BIOS to boot the Linux disk first since Linux (GRUB) will recognize that an XP disk is present as well,


OK, Linux, GRUB, XP...

three seperate items...b 

Grand Unified Bootloader is a set of software used to boot a computer,
either to GRUB itself, or (almost always) to another operating system, such as Linux or XP.


> 
how do I strap the two disks?
Linus master & xp slave?
Linux master & xp master?

And what about the third strap option on the WD disks, "master with slave"??
 
Please give me some advice how to do.
Dan (in Sweden)

OK, if both drives are on the same controller (the same cable),
then ...
XP drive should be set as Master
Linux drive should be set as Slave
OR
BOTH set to Cable Select.
With the XP drive connected to the end of the cable
and the Linux drive to the middle connector.
(as Wizard10000 stated)

XP REALLY REALLY likes to be the first drive, and gets very grumpy when it doesn't get it's way...
easiest just to give in and make it first.
 Yes, you can load XP to any drive or partition, but being first makes thing so much easier.

Test your setup once both drives are installed and connected,
BEFORE you install Linux, 
to make sure XP loads fine.

Then, boot with the Ubuntu LiveCD,
check with gparted to make sure the drives are as referenced below,
/sd[COLOR="Red"]a [/COLOR] is the [COLOR="Red"]first[/COLOR] drive, which should have XP
/sd[COLOR="DarkOrange"]b [/COLOR] is the [color=darkorange]second[/color] drive, which should be empty (soon to have Linux)

Now install Linux to the [COLOR="DarkOrange"]second[/COLOR] drive,
which will be 
/sd[COLOR="darkorange"]b[/COLOR]
this one should be empty, 
if it isn't, then the drives were not picked correctly, 
or mis-jumpered.

Choose the "use entire drive for Linux" option.
(this will wipe the drive, so make sure it does not have any data you need...
it shouldn't, since you said you just purchased it.)

Let GRUB be installed to the MBR of the [color=red]FIRST[/color] drive,
which will be 
/sd[color=red]a[/color]

you should then have GRUB load up and allow you to choose Linux or XP.

> **wizard10000 said:**
> Your drives should probably be jumpered as cable select on any machine built in the last several years.
That way the drive on the end of the cable is master and the one on the connector closest to the motherboard is slave.

usually the best way to go.

> Your IDE cable also needs to support cable select but that shouldn't be an issue with any machine built in the last five or six years.

except when the manufactirer cuts a few sheckels from the price,
or is trying to get rid of excess old inventory,
and tosses a 40-wire cable in the mix.

> 
[B]the slave drive uses the controller hardware of the master drive
 - that's why they call it a slave[/B]  ;)


The "slave" no longer uses the controller of the "master".
It's been a  few years since this stopped.

---

### Post by Danne_M on 2009-08-14
Hi guys and thanks for your answers.
I have now managed to intall UBUNTU on my PC. Initially I tried with 9.04 but I could not even get it to boot so I continued with 8.04 and that worked better. I did get an error 21 when trying to boot the system aftetr the installation but it turned out to be  the BIOS that had the new disk where I installed UBUNTU, to OFF. After setting it to AUTO everything workd fine and I got the menu where I could choose XP or UBUNTU, just as I wanted.
 
Once running UBUNTU, I am a bit dissapointed that performance is not better. The PC is equipped with a Pentiom 4 1.8 GHz and 1 GB RAM, so I thought it would run better.
One suspiscion I have is that the graphics card I have slows it down. I have a MSI RX2600PRO PCI card with 512 MB graphics memory, but I think that UBUNTU is not properly supporting this card. I went in to the hardware driver config screen and changed it to run with a unofficial driver. It got downloaded and after the restart the machine ran like a dog. It was not possible to work with it at all, so I quickly changed back to runing with, what I guess is, a generic driver. Does anyone have any input here?
 
Regards,
Dan

---

### Post by Bartender on 2009-08-14
Yeah, replace that ATI card with an Nvidia card

---

### Post by eriktheblu on 2009-08-14
It's not so much that Ubuntu doesn't support your card, but that ATI doesn't have very good support for Linux. There is from what I've read some proprietary issue with one of their suppliers.

My old machine had a built in ATI card. After much hassle I managed to get World of Warcraft to produce somewhat recognizable shapes. I never could get it to perform as well as it did under XP.

Switching to Nvidia produced a immediate and dramatic difference. If you want to do 3D graphics under Linux, Nvidia seems to be the common wisdom.

If a new card is not an option, you can run it un-accelerated (generic drivers), or try different drivers.

---

### Post by Danne_M on 2009-08-18
Thanks again for your answers that confirm my thoughts about the graphics card I have. I have managed to find a second hand NVIDIA AGP card based on the 7600 GPU. Hopefully it will work better than what I have today.
 
When starting the LINUX system after having switched graphics cards, will the system have support for the card directly or will I have to do something? Like putting in the UBUNTU installation disk to get the driver, download a driver or something?
Will it have to rebuild the UBUNTU kernel?
 
I don't have the card yet but I guess that within a few days I'll have it and it would be good to know up front how to handle the switch.
 
Regards,
Dan

---

### Post by Bartender on 2009-08-18
You "should" get graphics with the Nvidia card and the drivers that Ubuntu includes in a standard install.

Let's hope that you do get a screen.  If you do, get on the internet, and go to System>Administration>Hardware Drivers.  Ask it to look for hardware drivers.  Ubuntu should report back that nvidia driver such and such is available.  Click on "Activate" and be patient.  It will take a few minutes.

The "Activate" button does nothing unless you're online.

---

