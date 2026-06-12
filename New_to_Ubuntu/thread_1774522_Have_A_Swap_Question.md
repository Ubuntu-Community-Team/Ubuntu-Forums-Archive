---
title: "Have A Swap Question"
date: 2011-06-03
forum: New to Ubuntu
---

### Post by JohnBonne on 2011-06-03
After reading this thread I have a question that has always existed since installing my first linux system. (A month ago) Noticed from system monitor I never have any swap usage.Is there a problem in my configuration and is it important? I run Ubuntu on an External Drive.
[http://ubuntuforums.org/showthread.php?t=1773757](http://ubuntuforums.org/showthread.php?t=1773757)

I ran ```
$ sudo blkid
``` and got:

/dev/loop0: UUID="78629ec4-38a6-42a2-a178-eb42d848e65f" TYPE="ext4" 
/dev/sda1: UUID="BA80A07680A03B31" TYPE="ntfs" 
/dev/sda2: LABEL="HP_RECOVERY" UUID="5A18F4B818F4946B" TYPE="ntfs" 
/dev/sdb1: LABEL="Ubuntu" UUID="EA1A6F681A6F312D" TYPE="ntfs" 
/dev/sdb2: UUID="01CBD0945E4134E0" TYPE="ntfs" 

Then:
```
gksudo gedit /etc/fstab
```and got

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/host/ubuntu/disks/root.disk /               ext4    loop,errors=remount-ro 0       1
/host/ubuntu/disks/swap.disk none            swap    loop,sw         0       0

Then
```
 
gksudo gedit /etc/initramfs-tools/conf.d/resume
```And got a blank sheet.


If anyone could decipher this turkey gobble for me I would appreciate it.
Thanks,
John

---

### Post by JohnBonne on 2011-06-03
The line that bothers me is this one

```

sudo update-initramfs -u
```
Got:
Generating /boot/initrd.img-2.6.38-02063806-generic
Warning: No support for locale: en_US.utf8
administrator@ubuntu:~$

---

### Post by JohnBonne on 2011-06-03
bump

---

### Post by oldfred on 2011-06-03
You are running wubi not a full partitioned install.

How much memory do you have. If more than 2GB it probably is normal not to have used swap. Linux leaves things in memory on the chance you may reuse something. But it only ends up using swap if you load too much new stuff which is very many large applications or video editing.

[https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)

[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)
[https://help.ubuntu.com/community/Wubi](https://help.ubuntu.com/community/Wubi)

---

### Post by corncob on 2011-06-03
I've run Conky which monitors swap file usage and I've never seen any.  I have 3 gigs of RAM and an 8 gig swap file.  I think I had combined swap files from previous installations.  Anyhow, if an extra 6 gigs will ever make any difference in the Ubuntu partition I know where to get it.

---

### Post by JohnBonne on 2011-06-03
> **oldfred said:**
> You are running wubi not a full partitioned install.

How much memory do you have. If more than 2GB it probably is normal not to have used swap. Linux leaves things in memory on the chance you may reuse something. But it only ends up using swap if you load too much new stuff which is very many large applications or video editing.

[https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)

[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)
[https://help.ubuntu.com/community/Wubi](https://help.ubuntu.com/community/Wubi)

_You are running wubi not a full partitioned install._ What does that mean and how do I do a full partition install on an external drive?


I'll have a look at your links. I am going into a daze with this. I want to install Windows Vista / Ubuntu on a new hard drive. Mine has a few bad sectors on it. And I want to keep an Ubuntu on the external drive.

Thanks oldfred.

---

### Post by oldfred on 2011-06-03
The creator of wubi:
[http://howsoftwareisbuilt.com/2009/03/12/interview-with-agostino-russo-wubi-ubuntu/](http://howsoftwareisbuilt.com/2009/03/12/interview-with-agostino-russo-wubi-ubuntu/)
Agostino: Wubi actually wasn’t designed to do long-term installations. The main aim was really to let people try out Ubuntu with confidence. Normally, users that start with Wubi tend to upgrade to a full installation to a dedicated partition at the next release cycle.

HOWTO: migrate wubi install to partition - bcbc 
[http://ubuntuforums.org/showthread.php?t=1519354](http://ubuntuforums.org/showthread.php?t=1519354)

If doing a new install to a second drive, this is one of the few sets of instructions with screenshots. Based on Maverick but only minor screen changes with other versions.

Installing Ubuntu in Hard Disk Two (or more) internal or external Maverick screens shown
[http://members.iinet.net.au/~herman546/p24.html](http://members.iinet.net.au/~herman546/p24.html)

Install with separate /home from aysiu
[http://www.psychocats.net/ubuntu/installseparatehome](http://www.psychocats.net/ubuntu/installseparatehome)

---

