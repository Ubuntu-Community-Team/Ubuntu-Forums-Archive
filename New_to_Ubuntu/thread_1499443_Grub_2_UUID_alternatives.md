---
title: "Grub 2 UUID alternatives"
date: 2010-06-01
forum: New to Ubuntu
---

### Post by GMHilltop on 2010-06-01
I have installed a copy of Windows XP on one of my partitions and then imaged it, and reinstalled it onto another partition of the same hard drive (with a minor tweak to the boot.ini file of course).

Then I installed Ubuntu 10.04 LTS and had Grub 2 do the loading.

the problem that I am having is that when I set up the 40_custom file the 2 partitions that have the XP installations on them have the SAME UUID.  (see the code below).

Now it doesn't sound like there is a simple way to change an NTFS's UUID .... Anyone???

SO . . . is there another way I can help Grub 2 Identify the partitions without having to use or reference the UUID numbers?

Here is the code that I have in my 40_custom file:
[INDENT]#!/bin/sh
exec tail -n +3 $0
# This file provides an easy way to add custom menu entries.  Simply  type the
# menu entries you want to add after this comment.  Be careful not to  change
# the 'exec tail' line above.

menuentry "Paul's OS" {
    insmod ntfs
    parttool (hd0,1) hidden-
    parttool (hd0,5) hidden-
    parttool (hd0,7) hidden-
    parttool (hd0,2) hidden+
    parttool (hd0,3) hidden+
    parttool (hd0,6) hidden+
    parttool (hd0,8) hidden+
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set d091001490ffff2a
    drivemap -s (hd0) ${root}
    chainloader +1
}

menuentry "Anna's OS" {
    insmod ntfs
    parttool (hd0,2) hidden-
    parttool (hd0,6) hidden-
    parttool (hd0,7) hidden-
    parttool (hd0,1) hidden+
    parttool (hd0,3) hidden+
    parttool (hd0,5) hidden+
    parttool (hd0,8) hidden+
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set d091001490ffff2a
    drivemap -s (hd0) ${root}
    chainloader +1
}

menuentry 'Ubuntu, 10.04 LTS 32Bit' --class ubuntu --class gnu-linux  --class gnu --class os {
    recordfail
    insmod ext2
    parttool (hd0,1) hidden-
    parttool (hd0,2) hidden-
    parttool (hd0,3) hidden-
    parttool (hd0,5) hidden-
    parttool (hd0,6) hidden-
    parttool (hd0,7) hidden-
    parttool (hd0,8) hidden-
    set root='(hd0,3)'
    search --no-floppy --fs-uuid --set  709810c2-cc30-48ea-9b52-446207f52bfb
    linux    /boot/vmlinuz-2.6.32-21-generic  root=UUID=709810c2-cc30-48ea-9b52-446207f52bfb ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-21-generic
}

menuentry "" {
insmod ext2
}

menuentry "Reboot" {
reboot
}
menuentry "" {
set root=
}
menuentry "<====Entries Below Are For System Maintenance &  Testing=====>" {
set root=
}
menuentry "" {
set root=
}

menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,3)'
    search --no-floppy --fs-uuid --set  709810c2-cc30-48ea-9b52-446207f52bfb
    linux16    /boot/memtest86+.bin
}
menuentry "" {
set root=
}
menuentry 'Ubuntu, 10.04 LTS (recovery mode)' --class ubuntu --class  gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    parttool (hd0,1) hidden-
    parttool (hd0,2) hidden-
    parttool (hd0,3) hidden-
    parttool (hd0,5) hidden-
    parttool (hd0,6) hidden-
    parttool (hd0,7) hidden-
    parttool (hd0,8) hidden-
    set root='(hd0,3)'
    search --no-floppy --fs-uuid --set  709810c2-cc30-48ea-9b52-446207f52bfb
    echo    'Loading Linux 2.6.32-21-generic ...'
    linux    /boot/vmlinuz-2.6.32-21-generic  root=UUID=709810c2-cc30-48ea-9b52-446207f52bfb ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-21-generic
}[/INDENT]

---

### Post by BoneKracker on 2010-06-01
GRUB (and /etc/fstab for that matter) are not authoritative sources for the UUID of a device.  You find out what the UUID is, and then you enter it into your GRUB configuration and your fstab.

This will tell you the blkid of each partition, as well as the device name and any corresponding labels, in a nice tabular format:
```
blkid -o list
```

If you have two partitions with the same UUID, then you indeed have two copies of the same filesystem on both.  If you don't want these just delete it (or "reformat" it).  You could do that by firing up gparted, clicking on it, making sure it's unmounted, and deleting it (or put a new filesystem on it by using gparted to "format as" whatever).

Now, if you actually want to _keep_ both ntfs filesystems (as a backup or because you've put new data on one that you need to keep), but you want it to have a new UUID, that's a little hairier, but doable:
[http://www.linux.com/community/blogs/howto-modify-uuid-for-an-ntfs-partition.html](http://www.linux.com/community/blogs/howto-modify-uuid-for-an-ntfs-partition.html)
[http://ubuntuforums.org/showthread.php?t=1240146](http://ubuntuforums.org/showthread.php?t=1240146)

Once you're done changing stuff, reboot into linux, double-check blkid (per above), and then make sure you change any entries that need to be changed in your fstab or grub configuration.

---

### Post by GMHilltop on 2010-06-02
Thanks for the great links BoneKracker.

I DO want to keep the Operating systems exactly the same.  I can set it up ONCE with everything that these 2 people need, without having to LOAD it all twice.

The idea is to keep them completely independent of each other, and have it so that I can use the SINGLE image of the OS created to replace a potentially corrupted OS on either partition (with a simple boot.ini modification, of course)

Now, I think I understand what the "superblock" is that we are modifying, but to clarify, let me ask this question to see if the answer confirms my understanding . . . If I were to modify that superblocks UUID number, and then I were to reinstall Ubuntu and Grub 2, would Grub automatically identify that partitions new UUID?

Or,

If I were to then make an image of that partition with something like Acronis, and copied THAT image to yet a 3rd partition, if I were to run:   sudo blkid  would I see 2 partitions with the same "Modified" UUID?

Thanks again for the help.

---

### Post by BoneKracker on 2010-06-02
> **GMHilltop said:**
> Thanks for the great links BoneKracker.

I DO want to keep the Operating systems exactly the same.  I can set it up ONCE with everything that these 2 people need, without having to LOAD it all twice.

The idea is to keep them completely independent of each other, and have it so that I can use the SINGLE image of the OS created to replace a potentially corrupted OS on either partition (with a simple boot.ini modification, of course)
That's a bit extreme; linux **is** designed as a multi-user system.  Also, if you are going to go to such lengths, shouldn't you have them on separate physical disk drives?  Drive failure is a common cause of data loss or corruption.

> **GMHilltop said:**
> Now, I think I understand what the "superblock" is that we are modifying, but to clarify, let me ask this question to see if the answer confirms my understanding . . . If I were to modify that superblocks UUID number, and then I were to reinstall Ubuntu and Grub 2, would Grub automatically identify that partitions new UUID?

Or,

If I were to then make an image of that partition with something like Acronis, and copied THAT image to yet a 3rd partition, if I were to run:   sudo blkid  would I see 2 partitions with the same "Modified" UUID?

Thanks again for the help.

Yes, and Yes.

---

### Post by GMHilltop on 2010-06-03
I agree that they should be on separate hard drives, but it's a laptop with only 1 hard drive.  (I have them backing up important data to an external drive.)

By doing it this way one person can tinker as much with their OS as they want without affecting the others at all - which was the point of it all.

If changing the UUID is as simple as it appears to be (the links you've provided)  This will save a whole lot of work having to do a double install - AND I just learned another cool thing about partitions and how they work.

Now is the time for me to tinker with the UUID's because there is nothing to lose (data) because the os is imaged and can be put back in a couple of minutes, and every thing to gain (knowledge).

Thanks again BoneKracker - I'll let you know here how it turns out when I get a chance to try it.

---

### Post by GMHilltop on 2010-06-03
Does Ubuntu have a hex editor built in? (I am thinking - no)

If not, is there a way to download the program on one computer and then transfer it using a USB stick to the computer with Ubuntu that I am working on which doesn't have an internet connection?

Where would I get it from?

And how would I install it (commands to use etc)?

From what I can see,  it looks like a person should be able to download the "packages" instead of using 'apt-get' . . . is that right?

(maybe a new thread - but now that I have typed it - there it is)

My apologies - I am still very new to Ubuntu, but I am slowly getting there - and Thanks for the help.

---

### Post by BoneKracker on 2010-06-03
> **GMHilltop said:**
> Does Ubuntu have a hex editor built in? (I am thinking - no)

If not, is there a way to download the program on one computer and then transfer it using a USB stick to the computer with Ubuntu that I am working on which doesn't have an internet connection?

Where would I get it from?

And how would I install it (commands to use etc)?

From what I can see,  it looks like a person should be able to download the "packages" instead of using 'apt-get' . . . is that right?

(maybe a new thread - but now that I have typed it - there it is)

My apologies - I am still very new to Ubuntu, but I am slowly getting there - and Thanks for the help.
I don't know what Ubuntu's got on it because I don't use it.

There are many ways you could handle this.  What immediately comes to mind for me would be to do this using SystemRescueCD, which is the CD I always keep on hand if I have to boot from outside the system to perform repairs or surgery such as this.  They have a bootable CD version and a bootable USB version.  It has at least two hex editors on it (hexedit and hexcurse).  
[http://www.sysresccd.org/Main_Page](http://www.sysresccd.org/Main_Page)

Or you could search the Web for a list of linux hex editors, then see if any of them are on the Ubuntu CD you already have.

---

### Post by oldfred on 2010-06-03
If you look in synaptic under hex you get a bunch of hex editors. None seem to be installed automatically as I do not see any installed on my system.

---

### Post by BoneKracker on 2010-06-03
> **oldfred said:**
> If you look in synaptic under hex you get a bunch of hex editors. None seem to be installed automatically as I do not see any installed on my system.

True.  If you have any bootable systems on the disk, you could use a hex editor you install on one of them.  I was thinking there weren't any bootable systems on the disk.

---

### Post by GMHilltop on 2010-06-04
> **BoneKracker said:**
> ....  What immediately comes to mind for me would be to do this using SystemRescueCD, which is the CD I always keep on hand if I have to boot from outside the system to perform repairs or surgery such as this.  They have a bootable CD version and a bootable USB version.  It has at least two hex editors on it (hexedit and hexcurse).  
[http://www.sysresccd.org/Main_Page](http://www.sysresccd.org/Main_Page)



This could be a great Solution for me! Thanks for the heads up :)  I'll give it a try and see if I can get it to work.

I could install an editor on one of the os's (and would actually put it on the Ubuntu installation) but I can't get it online.  So unless there is a "package" that I can download and install, using a rescue disk like this should work just as well and would allow me to apply it where I need to.

I can't wait to try it.

I'll report back and let you know how I made out.

---

### Post by GMHilltop on 2010-10-28
Ok, THIS I got to work for me - Hopefully it helps others as well.

First credit where credit is due - I got the help I was looking for here:

[Changing / Modifying an NTFS partitions UUID using dd]("http://www.linux.com/community/blogs/howto-modify-uuid-for-an-ntfs-partition.html#comment-3322")

Thank You very much to Simon Williams for taking the time to respond  (See the comments to Adam's original post there).  I hope everyone here  finds this as useful.

Here is The Code used:

```
sudo dd if=/dev/urandom of=/dev/[ntfspartition] bs=8 count=1 seek=9
```

[COLOR=Red]**!!!!!!!!!!!!!!! WARNING WARNING WARNING !!!!!!!!!!!**[/COLOR]
For [ntfspartition] YOU MUST make sure you Identify the PROPER partition!!
ie:  sda1   or   sda2   or  sdb1  or  sdb2  or  sdc1  or sdc2   etc etc etc.
**DO NOT** put sda in there or you will SCREW your MBR !
Also you will want to run:  sudo blkid to make SURE you are modifying the proper partition.
DO NOT miss any part of the code above or you'll risk modifying more than just the UUID
**also posted at the above link with regard to the above code:**
Be warned that you can cause data loss ON ANY DISK CONNECTED TO YOUR  MACHINE if you specify the wrong disk or partition, or if the partition  you specify turns out to not be the one you were expecting. Disks of the  "new" form /dev/sda (rather than the old /dev/hda, etc) have  unpredictable ordering. Running this on a non-NTFS partition, or worse,  the entire disk (e.g. /dev/sda rather than /dev/sda1) will mess things  up very badly._** YOU HAVE BEEN WARNED. **_
[COLOR=Red]!!!!!!!!!!!!!!! END OF WARNING !!!!!!!!!!!!!!!![/COLOR]

as an example of the the code to be used --- if I wanted to modify the UUID of the 1st partition of the first hard drive _**IN MY SYSTEM**_ this is what I would type:

sudo dd if=/dev/urandom of=/dev/sda1 bs=8 count=1 seek=9

to do the 2nd partition of the first hard drive it would be:

sudo dd if=/dev/urandom of=/dev/sda2 bs=8 count=1 seek=9

**(Again - best verify what the system sees _IN YOUR SYSTEM_ by typing in Sudo blkid)**

Simon Williams gives a very nice breakdown as to what each piece of the  code does for those who are interested (Again - it is in the comments to  the original post there).
I think it is the 11th comment that starts off with "dd explained"
Comment 14 by Simon Williams that starts off with "written by Simon Williams, October 13, 2010
Yey, now that I can login again... :S "
gives even further detail to this part of the code:
/dev/urandom

Again Thanks again to Simon Williams for the assistance.  He was very professional and courteous!

---

