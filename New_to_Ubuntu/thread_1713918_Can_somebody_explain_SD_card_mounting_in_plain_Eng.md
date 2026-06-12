---
title: "Can somebody explain SD card mounting in plain English, please?"
date: 2011-03-24
forum: New to Ubuntu
---

### Post by Shie6meepo on 2011-03-24
I've got an HP Mini, which I installed 10.10 Netbook on a few months ago, and have been trying to get my 4gb SD card to mount since I installed. I've gone to tons of threads and so on to find instructions I understand, but any that I did ended up not working. Can anyone explain how to get it to mount (not even automount, just mount, though it would be nice if I could get it to automount, too) either in plain terms or with screenshots if it's not able to be explained in plain terms?

Thank you so much if you can

---

### Post by Kirboosy on 2011-03-24
Sure I will take a stab at it. :)

First off you need to figure out what id your device has been assigned. To do this simply open a Terminal and type ```
sudo fdisk -l
```

There will be a list of drives that pop up. Figure out which one is your card (it will most likely be a FAT/FAT32 drive)


After that you need to choose where to mount the drive. (I mount mine normally under /media so thats where this example will be)

In the terminal type in ```
sudo mount /dev/(device id of your card) /media
```

You can change the "/media" location to anywhere you want. /home, /home/ssrock/Documents....etc

to unmount just type the command ```
umount /dev/(device id)
```


Hope that helps,
~Caboose

---

### Post by coffeecat on 2011-03-24
Are you using the internal SD card reader? It seems that it works for some people and not others. Probably a driver issue. This from a quick search of the forum:

[http://ubuntuforums.org/showthread.php?t=1635534](http://ubuntuforums.org/showthread.php?t=1635534)

If you are having trouble with the internal card reader, I have a simpler solution. Get yourself something like this:

[http://www.amazon.co.uk/Integral-USB-Single-Slot-Reader/dp/B000VY80AM/ref=sr_1_7?ie=UTF8&qid=1301005227&sr=8-7](http://www.amazon.co.uk/Integral-USB-Single-Slot-Reader/dp/B000VY80AM/ref=sr_1_7?ie=UTF8&qid=1301005227&sr=8-7)

I've got something similar, not the same. It works on every machine I've installed Ubuntu to. You simply put the card in the slot, plug the reader into a USB slot and the thing automounts.

**EDIT**: @ssrock64, there might just be another issue. The internal card readers on my desktop and laptop which detect and automount 2GB and smaller SD cards just fine, won't do so with an 8GB SD card. The kernel doesn't detect it either - nothing from fdisk. I don't have a 4GB card to test but this might be a limitation of the driver for an internal card reader. Clearly not a limitation for whichever driver that is used for the device I posted.

---

### Post by Shie6meepo on 2011-03-24
@coffeecat Yes, it is an internal drive, so the solution posted by the first user doesn't work for me (thanks anyways!). I don't quite understand the process described in the tutorial that you linked to (I am definitely not technology-oriented), so I'll try to find a simpler wording until I get lazy enough to ask some friends to explain.

---

### Post by JKyleOKC on 2011-03-24
Depending on the age of the HP Mini, the reader might not be able to deal with current SD card capacities. I have an HP notebook, DV8000, with built-in SD reader, and under Windows it can read a 1-GB card just fine but cannot read a 2-GB card. I've not tried reading a card with it using Xubuntu, because I have a USB reader that I use now for all my systems...

---

### Post by Chronon on 2011-03-24
Perhaps the drivers do not support SDHC.  Do normal SD cards work?  (SD is 2GB or less.  Some 2GB cards are SDHC, some are SD.)

I usually use "dmesg" to find out what device node the card is using.  See if it's being recognized.  If it is associated with a device node (like /dev/sdc) you can manually mount it using the command Cabooose885 posted.  (I usually create a directory inside of /media since on my system it usually already has subdirectories containing mounted partitions.)

---

### Post by Shie6meepo on 2011-03-24
Trust me, it's not a simple problem of it being over capacity. The card worked just fine on Windows. I just need to get it to auto-mount.

---

### Post by coffeecat on 2011-03-25
> **ssrock64 said:**
> Trust me, it's not a simple problem of it being over capacity. The card worked just fine on Windows. I just need to get it to auto-mount.

No - the situation is more complex. On my laptop, I can read low-capacity SD cards in the internal reader in Ubuntu. With my 8GB card Windows 7 can read it but Ubuntu does not even recognise it is there. The most likely explanation is a limitation in the Linux driver for the internal reader - at least on my machine. The same could be true of yours.

The pragmatic solution is to get yourself one of those cheap SD card readers that I linked to. I have two different ones and have not had a problem with them on several machines and with all SD cards I have used them with. Clearly, a different driver is used. You don't have to go to Amazon to get one. I've seen them on sale in other outlets and one of mine came "free" with an SD card.

**EDIT**: I think Chronon's comment is relevant:

> **Chronon said:**
> Perhaps the drivers do not support SDHC.

My 8GB card is an SDHC one. The lettering is so small I coudn't make it out before.

---

