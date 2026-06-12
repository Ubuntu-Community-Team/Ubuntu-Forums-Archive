---
title: "Uninstall Ubuntu 11.04 and Re-Install Windows XP"
date: 2011-08-16
forum: New to Ubuntu
---

### Post by mystictartlet2012 on 2011-08-16
Hey everyone:

I want to remove Ubuntu entirely off of my PC. When I tried to remove the Linux partitions, it showed that I had no Windows partitions although I made sure that I had some Windows partitions before installing Ubuntu.

I did my research on how to uninstall Ubuntu and to reinstall Win XP but most of them say that I have to have a Windows recovery CD, which I don't have. I don't mind buying a new one but I'm on a pretty tight budget right now.

I tried to install a few bootable CDs for Win XP as an alt option but they all seem to not work. A few will work and start up but when you get to a certain point of the installation or booting, it will stop working and say that there are errors. A few will even say that my PC has no NTFS or FAT files. With the others, the PC will just say that it is not a readable CD or that it is not a System Disc (or disk).

If anyone can help, thanks in advance! =D

---

### Post by Bucky Ball on 2011-08-16
Boot from the Ubuntu LiveCD, Try Ubuntu (like you did to install it), once at a desktop System>Administration>Gparted.

Make sure all partitions are unmounted by right clicking then delete them. Create NTFS partitions if you like but there should be no need, you can do this when installing Windows. Incidentally, you will see any NTFS partitions you already have in Gparted. 

As for Windows install issues you might like to try a Windows forum. It's probably because you have an EXT4 partition where your Windows is looking - first partition, first drive - and it don't like that. Doesn't know what an EXT* partition is. Deleting all EXT* partitions will fix that. ;)

---

### Post by mystictartlet2012 on 2011-08-17
Ah, okay. I got into the GParted but I am unsure what to delete/resize.
Here's how it looks like:

Partition        **File System**    _Size_

/dev/sda1     **ext4**                  _10.75_GiB
/dev/sda2     **extended        **_26.50_GiB
/dev/sda8     **ext4**                 _10.26_GiB
/dev/sda9     **unknown**        _498.00_MiB
unallocated **unallocated**    _4.00_MiB
/dev/sda6     **ext4**                 _14.76_GiB
/dev/sda7     **linux-swap**     _495.00_MiB
unallocated **unallocated**    _7.00_MiB
/dev/sda5     **linux-swap**     _502.00_MiB


Thank you, I'll look into that. (:

---

### Post by mikewhatever on 2011-08-17
Since you want to remove Ubuntu, delete all of the above partitions.
Dealing with Windows installation errors is very much beyond the scope of this forum's goal purpose and design. Try a Windows dedicated forum.

---

### Post by corncob on 2011-08-17
I wasn't quite clear on whether or not you have a bootable XP installation disk.  If so, go ahead and install it and it will wipe everything else out (whether you want it to or not).  I don't know what the books say but that's my experience.
I agree that you should be on a Windows forum for this.  I use the Q&A board at [http://www.smartcomputing.com](http://www.smartcomputing.com) .  You can browse the board but you have to be a subscriber to one of their magazines to ask questions.

---

### Post by mystictartlet2012 on 2011-08-17
> **mikewhatever said:**
> Since you want to remove Ubuntu, delete all of the above partitions.

Alright. 

> **corncob said:**
> I wasn't quite clear on whether or not you have a  bootable XP installation disk.  If so, go ahead and install it and it  will wipe everything else out (whether you want it to or not).  I don't  know what the books say but that's my experience.
I agree that you should be on a Windows forum for this.  I use the Q&A board at [http://www.smartcomputing.com]("http://www.smartcomputing.com/") .  You can browse the board but you have to be a subscriber to one of their magazines to ask questions.

No, I don't have a bootable XP installation disk.
I have already posted a thread on a Windows forum, no worries.

---

### Post by bluepicaso on 2012-01-07
> **Bucky Ball said:**
> Boot from the Ubuntu LiveCD, Try Ubuntu (like you did to install it), once at a desktop System>Administration>Gparted.

Make sure all partitions are unmounted by right clicking then delete them. Create NTFS partitions if you like but there should be no need, you can do this when installing Windows. Incidentally, you will see any NTFS partitions you already have in Gparted. 

As for Windows install issues you might like to try a Windows forum. It's probably because you have an EXT4 partition where your Windows is looking - first partition, first drive - and it don't like that. Doesn't know what an EXT* partition is. Deleting all EXT* partitions will fix that. ;)

Removing EXT helped me thank you so much mate

:P

---

