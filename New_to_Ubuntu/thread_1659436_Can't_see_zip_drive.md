---
title: "Can't see zip drive"
date: 2011-01-04
forum: New to Ubuntu
---

### Post by mlempenau on 2011-01-04
This is driving me silly!!  when I enter "sudo fdisk -l" in a terminal window I get my zip drive to show up.  But I can not see it in Nautilus.  I have used gparted to reformat it to fat32 and rename it.  It all shows up and changes but I can't see in Nautilus.  It also shows up the media folder.  What am I forgetting?  Thanks

---

### Post by gandaran on 2011-01-04
> **mlempenau said:**
> This is driving me silly!!  when I enter "sudo fdisk -l" in a terminal window I get my zip drive to show up.  But I can not see it in Nautilus.  I have used gparted to reformat it to fat32 and rename it.  It all shows up and changes but I can't see in Nautilus.  It also shows up the media folder.  What am I forgetting?  Thanks
can you open it from the media folder? if so then just bookmark it in nautilus, bookmarking should give you a menu option in nautilus and also from the panel places menu.

---

### Post by nomko on 2011-01-04
Not bookmark it, better to add the zip drive in **fstab**.
 
To the topic starter:
can you do this:
- open a terminal
- type in: **sudo blkid**
- put the output here.
- type in: **cat /etc/fstab**
- put the output here.

---

### Post by mlempenau on 2011-01-04
Well, after adding the new post I had another problem and many things to do and when I plugged it in this morning it just up and worked even before I had a chance to follow the instructions given!  I'm afraid I don't know what to make of it??  I did try to open it in media yesterday and it just locked the window.  Tried that several times and even after I formated and rename it the same thing happened.  

What is blkid?  Thanks everyone for help.  Mike

---

### Post by nomko on 2011-01-05
> **mlempenau said:**
> Well, after adding the new post I had another problem and many things to do and when I plugged it in this morning it just up and worked even before I had a chance to follow the instructions given! I'm afraid I don't know what to make of it?? I did try to open it in media yesterday and it just locked the window. Tried that several times and even after I formated and rename it the same thing happened. 
 
What is blkid? Thanks everyone for help. Mike
 
blkid is a command you have to enter in a terminal =>> [http://linux.die.net/man/8/blkid](http://linux.die.net/man/8/blkid)
 
Which version of Ubuntu are you using?

---

### Post by mlempenau on 2011-01-05
Well, now it's late in the day and I try to use the zip drive and it's not there????!!!!!

when I type sudo blkid
mikee@mike-desktop:~$ sudo blkid
[sudo] password for mikee: 
/dev/sdb1: LABEL="Ubuntu" UUID="6e333ed7-65ab-4852-a98e-35a599b600ac" TYPE="ext4" 
/dev/sdb3: LABEL="VIDEO" UUID="11AD-E3CE" TYPE="vfat" 
/dev/sdb4: LABEL="EXTENDED" UUID="1EA8-E211" TYPE="vfat" 
/dev/sdb5: UUID="4bce2fc3-1f06-4d24-ba7e-f788fbc62a1b" TYPE="swap" 
/dev/sdc1: LABEL="MIKESPRIMAR" UUID="AE7045AA70457A5F" TYPE="ntfs" 
/dev/sdc2: LABEL="Test" UUID="06EC2881EC286D5D" TYPE="ntfs" 
/dev/sdc4: LABEL="BACKUP" UUID="F6D80EECD80EAB47" TYPE="ntfs" 
/dev/sde1: SEC_TYPE="msdos" LABEL="USB1" TYPE="vfat" 
/dev/sda1: LABEL="MIKEZIPDRIV" UUID="79CE-B1DA" TYPE="vfat" 
mikee@mike-desktop:~$ 

when I type [B]cat /etc/fstab
mikee@mike-desktop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sda1       /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=4bce2fc3-1f06-4d24-ba7e-f788fbc62a1b none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
mikee@mike-desktop:~$ cat /etc/fstab

I have four ports in use at this time.  A HP printer, HP scanner and two USB zip drives one called USB1 and the other mikeszipdrive.

[/B]

---

