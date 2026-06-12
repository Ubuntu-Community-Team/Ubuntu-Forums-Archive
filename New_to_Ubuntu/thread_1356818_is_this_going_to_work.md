---
title: "is this going to work?"
date: 2009-12-16
forum: New to Ubuntu
---

### Post by jfbooth on 2009-12-16
Been given an old Compaq desktop.  700MHZ Celeron, 512MB, USB 1.1, 1 HD with two partitions [c: 6.31G and d: 2.99G with a label of SYSTEM.SAV]  System has a factory installation of Windows ME on C: and some 'restore facility' on D:.  I also have the factory restore CD.

I also have a 160G SATA drive out of an old parted out HP notebook.  I have ordered a USB cable interface for it.  The spec on the interface says:

"Operating System Support: Desktop and Laptop computers with Windows 98SE/ME/2000/XP/2003 and MAC OS 9.2 above"

I think it needs a driver to work with ME.  I do not know if XUBUNTU will see it or not.

Questions:

I have 'messed' with partitions but it has been years .. back in the DOS days.  Decided on Xubuntu due to limited resources.  Figured I would return the space on D: to C: and have one drive, one partition to install Xubuntu on.  Would appreciate tips/comments on repartitioning this HD.

Assuming XUBUNTU will see the SATA, can I install XUBUNTU programs to it?  Initially install XUBUNTU to C: but as I install more programs from Package Manager, put 'em on the SATA, or should I just use the SATA for data (pictures, music, etc)?  Does PACKAGE MANAGER even give the option to install on 'device of choice"?

I'm a little worried having only a 10G HD for an OS and its programs.

If I can install programs to the SATA, should I get a USB 2.0 bus card?

Comments, criticisms, and advice are all welcome.  Thank you in advance.

---

### Post by Sef on 2009-12-16
> "Operating System Support: Desktop and Laptop computers with Windows 98SE/ME/2000/XP/2003 and MAC OS 9.2 above"

I think it needs a driver to work with ME. I do not know if XUBUNTU will see it or not.

Does the motherboard support SATA?

---

### Post by natravis on 2009-12-16
If the motherboard has on-board SATA ports, then what I would do is make one partition on your new drive for /home and leave everything else on old drive. 10GBs is actually a good amount of room and considering the specs of the computer I can't see you installing millions of programs without having tons of duplicate functions (i.e. multiple audio players, video players, etc). You may also put the swap space on the second drive. If you do not have SATA ports available, a USB 2.0 card would be far better than trying to run it via the 1.1 slots but will still not be very fast. Too bad SATA cards are expensive.

---

### Post by jfbooth on 2009-12-16
thank you both for the replies.  I doubt seriously the motherboard supports SATA .. it is an ME vintage machine.  Since I don't know how to tell for sure, I am assuming it does not.  

On that note, looks like I won't be using that SATA drive for anything but "DATA" if at all.

SOOOO, going to put Xubuntu on the 10G internal HD.  That brings me to partitioning it.  Just don't see any reason to keep that System.Sav partition.  How to partition this drive for 100% use for Xubuntu??  Does the iso CD for Xubuntu offer a utility?

Also, machine has an nVidia GEForce2 MX 100/200 video card.  There is a sticky note in the Installation & Upgrades forum saying that causes problems with UBUNTU installations .. but I plan to use Xubuntu.  Gonna be OK there? (same kernel, right?).

---

### Post by bwang on 2009-12-16
The installer in Ubuntu offers an option to use the entire drive.

---

### Post by 3rdalbum on 2009-12-16
USB storage devices use the standard USB Mass Storage driver. This driver is present on all USB-capable operating systems. Usually if you see Mac OS 9.2 or earlier as supported, it means that the device is plug 'n' play on any USB-capable operating system, because nobody writes drivers for OS 9.2 anymore.

---

### Post by jfbooth on 2009-12-17
3rdalbum ... thank you for the comment.  I interpret it as saying Xubuntu is likely TO see that USB interfaced SATA drive (?).  Waiting for a part, then will find out.  thanks for your comment.

---

### Post by natravis on 2009-12-17
> **jfbooth said:**
> 3rdalbum ... thank you for the comment.  I interpret it as saying Xubuntu is likely TO see that USB interfaced SATA drive (?).  Waiting for a part, then will find out.  thanks for your comment.

Yes Ubuntu is likely to see a USB interface for your SATA drive. Also, for your possible problem with NVidia, it is not a generalized "everyone" problem. For example, I had not one issue when I did my clean install and I was quite happy about that. Subsequent updates have not broken anything though I am aware a particularly annoying PulseAudio bug (unsure it has been resolved yet and too busy watching dexter to go searching).

---

### Post by jfbooth on 2009-12-17
thanks natravis.  that is encouraging that there may not be a problem w/ the video card.  I'm hoping it goes smooth.  Just waiting for more memory to arrive and will give it a go.

---

### Post by oldsoundguy on 2009-12-17
IF you are going to go to an external drive, you will need to get a PCI USB 2.0 internal card (eBay for 5 bucks) .. as external drives do NOT like USB 1.1 .. way too slow!

---

### Post by jfbooth on 2009-12-17
Thank you, Oldsoundguy .. yep, . ordered one today.  What I would really like to know is can I install Xubuntu on C: and install programs to USB 2.0 external drive?  Otherwise, only use for the external drive is storing pictures, music, etc.

---

