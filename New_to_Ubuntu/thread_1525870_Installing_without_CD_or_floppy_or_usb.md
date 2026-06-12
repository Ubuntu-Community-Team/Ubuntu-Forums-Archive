---
title: "Installing without CD or floppy or usb"
date: 2010-07-07
forum: New to Ubuntu
---

### Post by roeldebacker on 2010-07-07
hi,
 
I'm trying to reinstall Ubuntu on my portable.
 
situation as it is now:
1 partition (NTFS): windows FT wubi(ubuntu 10.04)
 
I have a second computer running ubuntu 10.04 which i can use for installing to the portable.
 
I would like to use the entire disk (if possible) or at least an easy way to install ubuntu and replace windows once and for all.
 
thanks

---

### Post by timbosity on 2010-07-07
The [wubi FAQ]("https://wiki.ubuntu.com/WubiGuide#How%20do%20I%20migrate%20to%20a%20real%20partition,%20and/or%20get%20rid%20of%20Windows%20entirely?") has a bit on installing ubuntu properly from wubi itself. Seems pretty straightforward as long you have internet connection.

---

### Post by timbosity on 2010-07-07
Assuming obviously that your windows and wubi set up is still working?

---

### Post by roeldebacker on 2010-07-07
you assume correct my good sir
 
I will try the solution given and report back if I have more news :)
 
For those who wonder what I am to try (or are like me and are sometimes a bit lazy :p) here's the option I'm about to give a shot.
**How do I migrate to a real partition, and/or get rid of Windows entirely?**


Existing Wubi/Lubi installations can be upgraded to an installation on a dedicated partition via LVPM. The main site for LVPM is at [http://lubi.sourceforge.net/lvpm.html](http://lubi.sourceforge.net/lvpm.html) and the guide and support forum is at [http://ubuntuforums.org/showthread.php?t=438591](http://ubuntuforums.org/showthread.php?t=438591). 
As an alternative, the following script can be used with Wubi 8.04. 
Download [wubi-move-to-partition]("https://wiki.ubuntu.com/WubiGuide?action=AttachFile&do=view&target=wubi-move-to-partition") 
Open a terminal and run: sudo sh wubi-move-to-partition /dev/sda9 /dev/sda10Replace /dev/sda9 with the partition where you would like to migrate the Wubi installation to, and /dev/sda10 with the appropriate swap partition (you can omit the second argument completely, in which case no swap will be setup). The two partitions must already exist and be empty (you can use any partitioning tool such as gparted to create them in advance). Note that the script will install grub as main bootloader replacing the existing bootloader, and it may not be easy to undo the changes (if things do not work as expected you will have to boot from a Live CD and replace/edit the bootloader manually). Also note that if you have multiple hard-disks, the disk order might have to be adjusted manually.

---

### Post by roeldebacker on 2010-07-08
I tried the solution given but failed :s 

I removed some partitions to create space for my new partition, in doing that i bricked my grub. I tried a usb cd-rom from the office and it magically worked. I'm starting to love ubuntu more and more.

many thanks to timbosity for the tips

---

### Post by timbosity on 2010-07-13
No worries.
Just wondering what might have caused the install from wubi to fail...I used that script without hassle to install on a friend's laptop recently... had to make sure the disks were labeled correctly (as in sd1a, sd2a etc...).
Did the script just not work? what were the issues?

Glad your enjoying the Ubuntu experience. You wont go back.

---

### Post by vagrale13 on 2010-07-13
I think you can do that with **UNetbootin** :-k
[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

---

### Post by roeldebacker on 2010-07-13
It was the laptop of a friend of mine and he did some tweaks to make the grub bootloader (hope this is correct) better. I did not know the changes but by throwing some partitions in the bin I probably erased some information vital for the grub to function. so booting was no longer an option. thankfully this problem is solved now.

---

### Post by kukker32 on 2010-07-13
try mounting it.. :P simple if you have the .ISO file

---

