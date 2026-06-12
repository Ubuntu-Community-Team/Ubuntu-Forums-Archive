---
title: "Grub Error 17 and problem mounting the HDD in Knoppix"
date: 2009-04-26
forum: New to Ubuntu
---

### Post by Steveor on 2009-04-26
I was running Ubuntu 8.10 when I got a screen full of computer warnings during shut down that made no sense to me.  The next time I tried to startup I got Error 17 and was unable to boot up.  By the way I'm on a Dell Dimension 8400 with an 80GB HDD running Ubuntu and an 18GB HDD running Windows XP (I switch off the 18GB in the BIOS when I want to run Ubuntu). 

So I put in my Knoppix CD to find the problem with the HDD (sdb1).  The HDD was on the Knoppix desktop but I was unable to mount it ("Could not mount device. The reported error was:  mount: I could not determine the filesystem type, and none was specified").  So I think I have some sort of hardware issue.  The BIOS recognizes the hard drive and when I ran fdisk -l I get the following:

Disk /dev/sda: 16.9 GB, 16907304960 bytes
255 heads, 63 sectors/track, 2055 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2054    16498723+   7  HPFS/NTFS

Disk /dev/sdb: 80.0 GB, 80000000000 bytes
255 heads, 63 sectors/track, 9726 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        7902    63472783+  83  Linux
/dev/sdb2            7903        8145     1951897+   5  Extended
/dev/sdb5            7903        8145     1951866   82  Linux swap / Solaris

I've been reading scores of forums that provide programs or other means of recovering or diagnosing the problem with my HDD.  However, when I try the suggestions I inevitably encounter a road block in the terminal or some other problem.  If anyone can guide me in possibly repairing my HDD or at least recovering some photos (about a month's worth), I'd really appreciate it.

---

### Post by WSmart on 2009-04-27
What up.

Use a liveCD and copy out your data that way.(Opps, scrach that. EDIT)


I've been having a ton of error 17 trying to install 9.04 today.  I was partitioning an NTFS drive, resized it, and it wouldn't boot afterwards.  I just realized that I had flagged the Ubuntu partition bootable which it's the second partition on the drive...  I see that now as I let the installer do the partitioning,not assigning the bootable flag.  Error 17 means the GRUB is not finding what it needs where it's being directed, so I read. 

My first thought is that you changed something in the configuration, either hardware or in the BIOS, like moved the optical drive up or down in priority.  Don't rush into anything.  If you can get your data secured, and that really should not be an issue at all, then maybe if you give it some time you'll remember something that helps, something you changed, ext.    This would be a good time  to spend $60 bucks and get a nice 500GB drive and try a fresh 9.04 install, or two.  :)

So tired of losing my mouse today running these installs.  Cheap KVM's don't remember the mouse when you're working without an mouse on another machine.  I'm using the alternative CD. The mousekey program is not right.

Thanks!

---

### Post by Steveor on 2009-04-27
My main concern is that I can't even get anything to recognize the HDD.  Neither Knoppix nor Ubunutu can mount it so how do I get the data?

---

### Post by bumanie on 2009-04-27
According to [Herman's page]("http://users.bigpond.net.au/hermanzone/p15.htm#17"), on 8.10 (and 9.04) the best thing to try for grub error 17 is a filesystem check. Boot with a live ubuntu cd and try this code in terminal (assuming you are using ext3 filesystem) and after the check has finished, try booting your computer to see if it has helped.> sudo e2fsck -C0 -p -f -v /dev/sdb1  If that doesn't work, post back and someone will either suggest something else or help with retrieving the photo's you want.

---

### Post by Steveor on 2009-04-27
I booted with a live ubuntu cd and tried the following in my terminal and got this:

ubuntu@ubuntu:~$ sudo e2fsck -C0 -p -f -v /dev/sdb1
e2fsck: No such file or directory while trying to open /dev/sdb1
/dev/sdb1: 
The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>

ubuntu@ubuntu:~$  e2fsck -b 8193 /dev/sdb1
e2fsck 1.41.3 (12-Oct-2008)
e2fsck: No such file or directory while trying to open /dev/sdb1

The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>

---

