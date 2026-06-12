---
title: "Screwed up my MBR"
date: 2010-02-15
forum: New to Ubuntu
---

### Post by Redmage913 on 2010-02-15
Greetings,

This isn't a Ubuntu problem, but since I've had such great help here in the past, I thought I'd throw this one at you.

I have a Dell Mini 9 with Win7 Pro on the SSD and I tried installing Fedora 12 LXDE spin on a 8 GB SDHC card to see if I could dual-boot with it.  The install seemed to work fine, but when I restarted the computer, all I get is a blinking cursor after the dell startup screen.  I tried manually starting the computer from the hard drive and "removable devices", both of which lead me to the blinking cursor.

I'd like to install GRUB (or LILO or whatever'll work, I don't care) as the bootloader, to allow me to run Windows, and to allow me to have Linux distros on a SDHC card, updating grub as I change things.

Frankly, how do I do this?  Do I need any sort of rescue ISO to burn to my USB thumbdrive? (No optical drives on the netbook)

Thank you for all the help I've been given in the past, and I hope to be able to ask the forum many, many more questions as I find myself getting deeper than I expected into trouble.

--Red

---

### Post by bodhi.zazen on 2010-02-15
You should be able to install grub from almost any live CD, here is how to do with with Ubuntu 9.10 :

[https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD](https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD)

The only potential problem may be it seems grub has issues with separate /boot partitions, as is typically the case with a default F12 install (Fedora uses LVM), in which case you may need to manually add an entry for F12.

---

### Post by Redmage913 on 2010-02-15
Okay, I'll try that. I have to say, I don't know anything about manually adding a grub entry, but I'll read the page you sent me and see if it will help.  First, I have to download the Ubuntu iso.

Another post I was reading a few minutes ago was talking about supergrub - is that helpful to me in any way, or is the method you said probably the most efficient and effective?

--Red

---

### Post by Redmage913 on 2010-02-15
I changed my mind - this was going to be my chance at experimenting with Fedora XFCE spin, but I've decided to install Xubuntu 9.10 instead.  As far as I know, it uses ALSA instead of Pulse, so I'm more apt to like the sound I get out of the system (Pulse in Ubuntu 9.10 was a nightmare for my Mini).

Before I install that on the SDHC card, anything I should keep in mind? Will this conceivably fix my boot problem if I make sure that grub is installed to my main SSD hard drive?

--Red

---

### Post by bodhi.zazen on 2010-02-15
I believe Xubuntu 9.10 also uses Pulse Audio.

When you install, grub will be installed and you should be fine.

---

### Post by Redmage913 on 2010-02-15
I know I have a semi-double post about this, but what partition on /dev/sda should I put GRUB?  sda1 is windows 7's 100 MB system reserved partition, and sda2 is the so-called C drive.

---

### Post by bodhi.zazen on 2010-02-15
grub should be installed into the MBR, not into a partition.

Go with the defaults or specify /dev/sda

[http://en.wikipedia.org/wiki/Master_boot_record](http://en.wikipedia.org/wiki/Master_boot_record)

---

### Post by Redmage913 on 2010-02-15
Thank you. I didn't know where the MBR was precisely located.  Here goes...I'm formatting and installing Xubuntu 9.10 on the SD card, and grub will install on /dev/sda (not sda1 or sda2).

I'll let you know if something's broken when I'm done installing.

--Red

---

### Post by Redmage913 on 2010-02-15
<Deleted - Accidental Double-Post>

---

### Post by Redmage913 on 2010-02-15
New problem!

```
GRUB loading.
error: no such disk
grub rescue>
```

I'm guessing that this means that one of the drives isn't properly mounted? probably the SD card - I dunno if that card has to be mounted within an operating system to work.  Probably.

--Red

---

### Post by Redmage913 on 2010-02-15
Okay, at this point I don't care if I get Linux to work. I would like to have things so I can get Win7 back up and running for classes tomorrow. I can use the Xubuntu Live USB if necessary, but eventually I need to get Windows back up and running.

Any way to get grub to just boot windows and nothing else?  I'm guessing removing the SD card, booting into the Live USB, and updating grub from there.

Also, what's the commands to update grub from the live USB?

---

