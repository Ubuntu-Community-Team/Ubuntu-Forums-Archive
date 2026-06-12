---
title: "Unable to mount /home or mount partition"
date: 2011-04-28
forum: New to Ubuntu
---

### Post by cesar0094 on 2011-04-28
Hi, I am having the following problem, I have 4 different partitions:

/ and /home filesystem   sda4
/home                    sda1
/ filesystem             sda2
swap                     sda3

They are in that order, the reason is I was working with sda1, sda2 and sda3 as normal, I had really weird problems, ubuntu will completely crash, (no way to reset the computer other than pushing the button) and I was getting frustrated, so my sda4 used to be a broken windows partition :) so I installed a brand new linux system on that partition so I could transfer all my information to it and delete sda1 and sda2. After installing the new ubuntu, i was not able to access any of my information from sda1, I tried mounting in, then booting directly to it, nothing is working. Here are the errors I get:

**Trying to access it in my working partition:**
Error mounting: mount: wrong fs type, bad option, bad superblock on /dev/sda1.

**Ran e2fsck /dev/sda1:**
e2fsck: Group descriptors look bad... trying backup blocks...
e2fsck: Bad magic number in super-block when using the backup blocks
e2fsck: going back to original superblock
e2fsck: Device or resource busy while trying to open /dev/sda1
Filesystem mounted or opened exclusively by another program?

**Ran e2fsck /dev/sda1 -b 32768:**
e2fsck: Bad magic number in super-block while trying to open /dev/sda1
The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>

**If I try to boot from my previous root (sda2):**
Serious problem were found in /home
And the same tests fail.

I have 10.10.
I don't know what to do, I've been looking around for two days and nothing. All my important information is in that partition. I even tried to access it through another Windows computer with an adapter I have which makes HDs portable and installed some programs that were supposed to access ext3 partitions and nothing worked. Sorry for the bunch of info, but I wanted to provide as many as I could and not having to be back and forth. Thank you very much for your help!

---

### Post by vivek.pandey on 2011-04-28
you can do 2 things 
1) boot from a live ubuntu cd and run fsck command from terminal for the partition which contains error
2) for some reasons sometimes booting from live ubuntu cd doesnt work... you can try slax or backtrack ... slax is a small linux distro hence can be downloaded easily from [www.slax.org](www.slax.org)
burn it and boot from it
then run fsck from the terminal
all the best

---

### Post by vivek.pandey on 2011-04-28
sorry for double post

---

### Post by grahammechanical on 2011-04-28
Have you tried using Disc Uility? There are options to mount a volume and to check and fix file systems. I find it strange that /home is sda1 and sda2 is file system. If home is one a separate partition then the OS usually goes on the first partition. This is the way it is on my system.

Regards.

---

### Post by cesar0094 on 2011-04-28
@vivek.pandey
I just tried, I got the same errors.

@grahammechanical
I just used Disc Utility. When mounting gives me the first error I wrote. When checking filesystem it tells me it is NOT clean. Ran the Self-Test, everything seems fine. I know the order is kind of weird, I was a noobie back then, and sda1 is ext2 and sda2 is ext3, I dont know what I was thinking of.

---

