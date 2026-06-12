---
title: "Device names in Linux"
date: 2011-07-26
forum: New to Ubuntu
---

### Post by gigenieks on 2011-07-26
Hi, guys! :rolleyes:

I'm trying to understand how Linux ( (K)Ubuntu ) is naming devices (hard disks etc).
So here goes basics...

Found this page --->
[Click - Device names in Linux]("https://help.ubuntu.com/8.04/installation-guide/i386/device-names.html")

[COLOR="DarkRed"]**Is information in link above correct? **[/COLOR]


And if it is, I have some questions:

> 
The first SCSI disk is named **/dev/sda.**

1. Does SATA = SCSI? (I have one SATA hard drive and it is named [b]sdc[/])


> 
[LIST]
[*]The master disk on IDE primary controller is named /dev/hda.
[*]The slave disk on IDE primary controller is named /dev/hdb.
[/LIST]


2. I don't see any hard drives / partions named **hd(x)**; instead everything is named sd(x).
And I have 2 IDE hard drives.

I get that info by:
```

sudo fdisk -l

```

[Click - Paste Ubuntu of my fdisk]("http://paste.ubuntu.com/652209/")


Also does someone have some good links about this kinda things? (easy to understand language; or if not "hard language" :biggrin:)

---

### Post by coffeecat on 2011-07-26
The link you found was for Ubuntu Hardy (8.04) which is now no longer supported in the desktop version (the server version is still supported). The important thing is that there has been a change in the hard drive controller kernel drivers since Hardy. It used to be that sdX referred specifically to a SCSI drive, but when flash drives and SATA drives appeared, the SCSI controller driver was developed to include them so that sdX could refer to SCSI, SATA and flash drives. IDE/PATA drives still had their own kernel driver and were referred to as hdX. But then all types of hard or flash drives were integrated into one kernel driver and since then hdX device names have disappeared and all hard drives and flash drives appear as sdX - unless you use an old version of the Linux kernel.

To be honest, I thought the change occurred before Hardy but, whatever, I do remember that with one version of the kernel during the changover, hdX/sdX designation varied according to the make of hardware controller. I had the disconcerting experience of seeing my IDE drives referred to as sdX in one machine and hdX on another - that's with the same release of Ubuntu.

It's simpler now. Device name hdX belongs in the past.

---

### Post by amjjawad on 2011-07-26
I always use GParted to give some Labels to my drives so that I can easily access them.

I think Coffeecat has explained everything already :)

---

