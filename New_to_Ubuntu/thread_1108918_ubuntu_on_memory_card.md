---
title: "ubuntu on memory card"
date: 2009-03-28
forum: New to Ubuntu
---

### Post by Ginoxy on 2009-03-28
hello, 
can i install ubuntu on my asus notebook but in an SD memory card instead of the HD?

---

### Post by snowpine on 2009-03-28
Yes. Ubuntu doesn't really care what kind of drive it's on. :) Installing to an SD card is a great way to test out new distros, in my opinion. The only danger you want to watch out for is to make sure you install the Grub bootloader on your SD card instead of the internal SDD/hard drive. When you get to the last step of the installer, click Advanced Options, and verify that Grub will be installed to the correct device (/dev/sdb for example). Other than that, it's just like the normal install process.

---

### Post by Ginoxy on 2009-03-28
this is great !!! 
thanks a lot !

---

### Post by ugm6hr on 2009-03-28
If using an SD card, I would avoid creating a swap partition.

SD cards have a finite number of write cycles, so a swap partition will shorten the SD card lifespan.

Else, consider creating a swap partition on the internal HD.

---

### Post by Ginoxy on 2009-03-28
one more question please 
is it also possible to download wubi to it ??

---

### Post by Ginoxy on 2009-03-28
> **ugm6hr said:**
> If using an SD card, I would avoid creating a swap partition.

SD cards have a finite number of write cycles, so a swap partition will shorten the SD card lifespan.

Else, consider creating a swap partition on the internal HD.

what do you mean ?

---

### Post by Lisa Y on 2009-03-28
Hello there,

Of course you can install Ubuntu to your SD card.

First we will need to determine the device name of the partition. Unmount and remove the card. Open a terminal, type

```
sudo blkid
```

Now insert a card, wait until the icon appears on the desktop and again re-issue that same command 

Your SD card should look something like this /dev/sd##. For example /dev/sdc1. BUT ITS DEFFINTILY /dev/sda1 (lol)

To check the file system, you have to unmount it: you can not check a filesystem when it is in use. You can right-click the icon to unmount, or unmount directly from the terminal:

```
sudo umount /dev/sdc1
sudo fsck /dev/sdc1
```

the second command is used to check sdc1

---

### Post by Ginoxy on 2009-03-28
> **Lisa Y said:**
> Hello there,

Of course you can install Ubuntu to your SD card.

First we will need to determine the device name of the partition. Unmount and remove the card. Open a terminal, type

```
sudo blkid
```

Now insert a card, wait until the icon appears on the desktop and again re-issue that same command 

Your SD card should look something like this /dev/sd##. For example /dev/sdc1. BUT ITS DEFFINTILY /dev/sda1 (lol)

To check the file system, you have to unmount it: you can not check a filesystem when it is in use. You can right-click the icon to unmount, or unmount directly from the terminal:

```
sudo umount /dev/sdc1
sudo fsck /dev/sdc1
```

the second command is used to check sdc1

this should be from the live CD menue ? or from where ?

---

### Post by snowpine on 2009-03-28
> **Ginoxy said:**
> what do you mean ?

A default install of Ubuntu creates a "swap partition," which is kind of like virtual memory. If your ram fills up, the swap partition is like extra ram on the disk. 

If you don't want a swap partition, you will have to choose Manual Partition during the install process. Ubuntu will run just fine without a swap partition, as long as you have enough ram for your needs (I recommend 512mb minimum).

SD cards (and other flash media like USB thumb drives) theoretically have a maximum number of write cycles before they wear out. If you use a swap partition, your SD card will wear out quicker. You will have to decide whether you're willing to take that risk or not. Personally, I don't care whether my SD card wears out in, say, 5 years instead of 10, since I only paid $9. :)

---

### Post by Ginoxy on 2009-03-28
i just need to get it right before starting to fo anything. 

now i need to download ubunut (done) 
second, since i dont have cd rom coz its a notebook that does not has a cd rom , i need to copy the whole ubunut to my sd card right ?

---

### Post by ugm6hr on 2009-03-28
You need a PC (with CD drive) to create a LiveUSB (1GB+ USB stick) from the CD, which then needs to be used to install on to the SD card on the netbook.

You could use a LiveSD instead of a LiveUSB, provided you have 2 SD card slots on the netbook.

---

### Post by Ginoxy on 2009-03-29
how about this software 
[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

can i use for such thing ?

i think i can load ubuntu to a USB flash drive then boot from it and then install it to SD MC right ?

---

### Post by ugm6hr on 2009-03-29
> **Ginoxy said:**
> how about this software 
[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

can i use for such thing ?

i think i can load ubuntu to a USB flash drive then boot from it and then install it to SD MC right ?

Yes. Exactly right.  I have done this many times (although installing on to HD).

---

### Post by Ginoxy on 2009-03-29
Great ! 
what about the GRUB thing ? how can i install it on SD not to my HD ?

---

### Post by ugm6hr on 2009-03-29
> **Ginoxy said:**
> Great ! 
what about the GRUB thing ? how can i install it on SD not to my HD ?

From memory, the Ubuntu installer allows you to specify a GRUB location in the traditional Linux nomenclature.

Linux = sda, sdb etc (or hda, hdb)
Grub = hd0, hd1 etc

When booted from the LiveUSB, with HD, SD and USB all plugged in, go to the Terminal and enter:
```
fdisk -l
```

This will list all the connected "hard drives" i.e. SD, USB and HD.  Work out which is the SD, and remember its name (e.g. sdb).

When installing Ubuntu, just before the "Install" (at step 7), select the Advnaced button (see screenshot, courtesy [http://www.psychocats.net/ubuntu/dualboot](http://www.psychocats.net/ubuntu/dualboot) ).  This should give you options as to where to install Grub.  Pick the right one!!!!!

**I would recommend a backup before installing any new OS.**

---

### Post by Ginoxy on 2009-03-29
This is cool !! 
Thanks a lot :KS

---

### Post by Ginoxy on 2009-04-10
hi again 
is it as for the grub if i installed it into the SD memory card as well as the OS it self is it ok?

---

### Post by ugm6hr on 2009-04-10
> **Ginoxy said:**
> hi again 
is it as for the grub if i installed it into the SD memory card as well as the OS it self is it ok?

I think you are asking if Grub and Ubuntu can exist on the same SD card.

The answer is yes.

---

### Post by Ginoxy on 2009-04-10
great ! so if the SD is not attached to the notebook it will boot to windows normally ! wont affecting it ?

---

### Post by wubrgamer on 2009-04-10
> **Ginoxy said:**
> great ! so if the SD is not attached to the notebook it will boot to windows normally ! wont affecting it ?

Assuming that you have left the internal disk untouched and leave the BIOS to boot from the internal disk, then yes. It will boot from the original operating system. (Windows :icon_frown:)

---

### Post by Ginoxy on 2009-04-24
now im facing a problem 

when i reach step 3 and going to step 4 another small box appear asking me the following : 
unmount partitions that are in use? 

/dev/sdb, /dev/sdc 

when i click forward i got only /dev/sdb left to unmount (which is USB) that im currently use as liveUSB 

now when i click "go back" 

it goes to step 4 (prepare disk space) 

i have these options 

1- use entire disk
2- install them side by side choosing between them each startup
3-specify partitions manually (advanced) 

when i click on "3" it scanning disks

and then gives me /dev/sdc (memody card) 


now what to do ?

by the way the type of the memory card is fat32

---

### Post by Ginoxy on 2009-04-25
any idea guys ?

---

