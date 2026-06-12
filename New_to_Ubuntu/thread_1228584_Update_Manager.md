---
title: "Update Manager"
date: 2009-08-01
forum: New to Ubuntu
---

### Post by The Linux Nub on 2009-08-01
The upgrade needs a total of 389M free space on disk '/'. Please free at least an additional 360M of disk space on '/'. Empty your trash and remove temporary packages of former installations using 'sudo apt-get clean'.

Alright, so far this is my second post on Ubuntu forums, Thus meaning i am new.. How am i able to fix this problem please help yet once again


                                                                                                 -Regaurds
                                                                                                   The Linux Nub

---

### Post by Sef on 2009-08-01
Applications > Accessories > Terminal

Then copy and paste this command in the Terminal:

```
sudo fdisk -l
```

That will show us your hard drive partitions.   I would like to see how you partitioned it.

---

### Post by The Linux Nub on 2009-08-01
> **Sef said:**
> Applications > Accessories > Terminal

Then copy and paste this command in the Terminal:

```
sudo fdisk -l
```

That will show us your hard drive partitions.   I would like to see how you partitioned it.
Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x14cb14cb

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       14267   114599646    7  HPFS/NTFS
/dev/sda2           14268       14593     2618595    5  Extended
/dev/sda5           14268       14571     2441848+  83  Linux
/dev/sda6           14572       14593      176683+  82  Linux swap / Solaris

---

### Post by pastalavista on 2009-08-01
You need to do what it says... free up some space on the disk. Delete files you don't need or else resize the / partition. To resize, you'll need to boot from the live CD and use System > Administration > Partition Editor (gparted).

---

### Post by Sef on 2009-08-01
It looks like your ubuntu partition is too small.  How many gigabytes did you make for it?

---

### Post by The Linux Nub on 2009-08-01
> **Sef said:**
> It looks like your ubuntu partition is too small.  How many gigabytes did you make for it?
i think just minimal amount, not sure though how may i find how much it takes up (i installed inside windows so im dual booting)

---

### Post by The Linux Nub on 2009-08-01
anyone know what i could do? =/

---

### Post by pastalavista on 2009-08-01
> **The Linux Nub said:**
> anyone know what i could do? =/

First, boot in Windows and defrag it a couple of times and be sure you shut it down clean, that is, no hanging programs (like anti-virus for example) and make sure there's no pending updates. Since you are running a Wubi (inside Windows) install, you should have as much space for Ubuntu as you do for Windows. How full is your Windows drive?

---

### Post by The Linux Nub on 2009-08-01
My windows drive is not very full at all ( i had just done a restoration of windows xp using restore disk) so all i pretty much have is antivirus and drivers and such installed, thats it. anyways brb, ima try that suggestion if it doesnt work, ill let you know, if not, ill let you know anyways.

-Thanks
The Linux Nub.

---

### Post by The Linux Nub on 2009-08-01
Ok, im back i have done a disk defragmenatation, what now?

---

### Post by Sef on 2009-08-01
> Since you are running a Wubi (inside Windows) install, you should have as much space for Ubuntu as you do for Windows. How full is your Windows drive?

Ubuntu is installed, but there is not enough room on the partition. (See post #3.)  What will be needed to do is increase the Ubuntu partition, but I would have to check into how to do that.

---

### Post by The Linux Nub on 2009-08-01
Thank you.

---

### Post by The Linux Nub on 2009-08-01
=/ im still left clueless on how to resize partition via gparted but then again i cant find it on system settings, do i need to reboot PC with disk in and tell it to boot from it?

---

### Post by pastalavista on 2009-08-01
I don't know much about Wubi so I looked it up...
[https://wiki.ubuntu.com/WubiGuide#How%20do%20I%20resize%20the%20virtual%20disks?]("https://wiki.ubuntu.com/WubiGuide#How%20do%20I%20resize%20the%20virtual%20disks?")

---

### Post by The Linux Nub on 2009-08-01
> **pastalavista said:**
> I don't know much about Wubi so I looked it up...
[https://wiki.ubuntu.com/WubiGuide#How%20do%20I%20resize%20the%20virtual%20disks?]("https://wiki.ubuntu.com/WubiGuide#How%20do%20I%20resize%20the%20virtual%20disks?")
lol, it wont let me download, it wont let me go back and forth from page to page either using firefox. :(

---

### Post by The Linux Nub on 2009-08-01
> **The Linux Nub said:**
> lol, it wont let me download, it wont let me go back and forth from page to page either using firefox. :(
dpkg: failed to write status record about `xml-core' to `/var/lib/dpkg/status': No space left on device

.. what is this?.. and is it bad? :/

---

### Post by pastalavista on 2009-08-01
You'll need to get rid of something on the disk to make room for the download. Copy (move) some large files from your /home folder to CD or the Windows partition. 

Wubi came out after I'd already given up on Windows so I never tried it. There is also a way to transfer the Wubi install to it's own primary partition on the wiki Wubi guide page. That's what I'd do, I think.

---

### Post by Shig on 2009-08-01
Seeing as how you've plenty of space on your Windows partition, You can use  [LVPM]("http://lubi.sourceforge.net/lvpm.html") to increase the size of the virtual partition that Ubuntu is living in.

There are several scenarios in this [forum thread]("http://ubuntuforums.org/showthread.php?t=438591"), one of which tells you how to resize an existing virtual disk used by Wubi.

Hopefully using these steps you can simply increase the size of the virtual disk you have Ubuntu installed in and fix the errors you are seeing.

---

### Post by 3rdalbum on 2009-08-01
Can't you use Gparted to downsize the Windows partition, and upsize the Ubuntu one? You need to boot from the live CD to do this, of course.

*sigh* I hope the installer in Ubuntu 9.10 makes the resizing handle more visible, and brings up a warning message if you try to give it the minimum amount of space. You're certainly not the first person to have left the resizing at the default and then wondered why you get "no space left on device" messages when you try to update.

---

