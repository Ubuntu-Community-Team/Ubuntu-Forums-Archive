---
title: "Easy Peasy hijacked my MBR!"
date: 2009-09-20
forum: New to Ubuntu
---

### Post by bledsoe on 2009-09-20
I was attempting to create a bootable jump drive with Easy Peasy for my wife's new netbook, and apparently I did something wrong since the bootable jump drive didn't work, but Easy Peasy was somehow installed onto the Ubuntu PC that I was using to create the bootable jump drive.  Now when I turn on my PC, instead of booting into my regular Ubuntu install, it boots into Easy Peasy.

Specifically, I get an initial screen that says:

```
UNetbootin

Default
Help
oem = OEM install (for manufacturers)

Will boot automatically in x seconds
```

The "Default" option goes to Easy Peasy, and the other two seem to go to some sort of command line, but there's no option that says, "I accidentally installed Easy Peasy on this PC, give me back my regular Ubuntu OS."

I know all my files and stuff are still there because on the Easy Peasy desktop there's a hard drive icon and when I open it up, I can see my file system and all my files.

How do I get rid of Easy Peasy and get back to my regular Ubuntu system? I'm guessing this involves the Master Boot Record somehow? 

Any suggestions appreciated,

---

### Post by The Cog on 2009-09-20
Try this:
Boot the live Ubuntu install CD and choose try without installing.
From a command prompt, become root with: **sudo -i**
Mount your normal Ubuntu root partition like this (assuming /dev/sda1): **mount /dev/sda1 /mnt**
Change to using that as your root: **chroot /mnt**
Reinstall grub: **grub-install /dev/sda**
reboot

---

### Post by bledsoe on 2009-09-20
Hi, and thanks for the help.

I tried what you suggested, but when I got to the step where I enter the "chroot /mnt" command, I get a message that says "cannot run command '/bin/bash': no such file or directory".

Also, the whole "/mnt" stuff is a little unclear to me; I'm not entirely sure what you meant when you said "assuming /dev/sda1".  Does this mean my regular Ubuntu installation might be mounted somewhere else?  How do I find out?

Thanks,

---

### Post by The Cog on 2009-09-20
That sounds like you mounted the wrong partition. You need to do somw digging to find the right partition. First, this command:
```
sudo fdisk -l
```
will show you which partitions exist. I guess you need to try each in turn until you find the Ubuntu one. Something like this:
```
sudo -i
mount /dev/sda1 /mnt
ls /mnt
unmount /mnt
mount /dev/sda2 /mnt
ls /mnt
unmount /mnt
mount /dev/sda3 /mnt
ls /mnt
unmount /mnt
```
Stop when one of the ls sommands shows the directories bin, boot, etc and others. This is the one you want. Don't unmount it, but then do
```
chroot /mnt
grub-install /dev/sda
```

---

### Post by bledsoe on 2009-09-20
When I run the "sudo fdisk -l" command, I get this:

```
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000b898e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       12158    97659103+   b  W95 FAT32
/dev/sda2           12159       60801   390724897+   5  Extended
/dev/sda5           12159       60059   384764751   83  Linux
/dev/sda6           60060       60801     5960083+  82  Linux swap / Solaris
ubuntu@ubuntu:~$ 
```

The mount/ls commands indicate that the one I want is /dev/sda5, as that has all my files, but when I mount it and run the chroot and grub-install commands, I get this:

```
root@ubuntu:~# chroot /mnt
root@ubuntu:/# grub-install /dev/sda
/dev/sda: Not found or not a block device.
root@ubuntu:/# grub-install /dev/sda5
/dev/sda5: Not found or not a block device.
root@ubuntu:/# 

```

(I tried the "grub-install /dev/sda5" command in case the other was a typo)

I seem to be closer than I was before, but still not there. Other suggestions?

---

### Post by bledsoe on 2009-09-21
I found a solution (woo-hoo!), though it involved a different procedure (described [here]("http://ubuntuforums.org/showthread.php?t=609548")) that installs GRUB to MBR.

Since the PC in question originally only had one OS installed on it (Ubuntu), I don't know if GRUB was originally installed at all; does Ubuntu install GRUB if Ubuntu is the only OS on the machine, or is it just for dual/multi-boot configurations?

At any rate, I booted using an Ubuntu LiveCD, went thru the steps described in the link above, which installed (re-installed?) GRUB to the MBR on my first (or, in my case, only) hard disk, and presto, I got my Ubuntu system back, good as new.

Thanks again for all the help,

---

