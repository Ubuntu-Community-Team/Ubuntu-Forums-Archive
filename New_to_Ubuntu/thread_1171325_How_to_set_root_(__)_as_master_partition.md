---
title: "How to set root ( / ) as master partition?"
date: 2009-05-27
forum: New to Ubuntu
---

### Post by Melhisedek on 2009-05-27
Hello there folks,
been trying to install Ubuntu on my new rig for a while now. Tried going back in versions down to 8.04 but still I have the same error. Which is described here:

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/181812](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/181812)

Now the guy at the bottom wrote that I should set root as master partition... How do I do that?

I have 120 Gig free on my primary SATA disc and I tell Ubuntu to use largest continous free space, but I always end up with this damn error so GRUB can't install :( 

Any help would be greatly appreciated!
Thank you for your time!

---

### Post by Baelus on 2009-05-27
I'm not familiar with the term "master" partition.

My best guess is that it means install ubuntu on a primary partition
(not a logical drive sitting in an extended partition), and make it bootable.

That's all I can make of it.

---

### Post by philinux on 2009-05-27
> **Melhisedek said:**
> Hello there folks,
been trying to install Ubuntu on my new rig for a while now. Tried going back in versions down to 8.04 but still I have the same error. Which is described here:

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/181812](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/181812)

Now the guy at the bottom wrote that I should set root as master partition... How do I do that?

I have 120 Gig free on my primary SATA disc and I tell Ubuntu to use largest continous free space, but I always end up with this damn error so GRUB can't install :( 

Any help would be greatly appreciated!
Thank you for your time!

Is there just the one HD on your system?

---

### Post by Melhisedek on 2009-05-27
No I have two... One 1.5 TB and one 320GB.
Linux would be installed on 1.5TB one... I can try and install it on 320GB, or should I disconect 320 one and try again?

---

### Post by Melhisedek on 2009-05-28
bump

---

### Post by Yannick Le Saint kyncani on 2009-05-28
I have made another ubuntu installer (nrnux).

It is slow and you would have to use a temporary usb flash stick but it may or may not work for you.

Let me know if you want to try it out, or check my sig.

---

### Post by philinux on 2009-05-28
> **Melhisedek said:**
> No I have two... One 1.5 TB and one 320GB.
Linux would be installed on 1.5TB one... I can try and install it on 320GB, or should I disconect 320 one and try again?

Can you describe the partition already on these disks and the operating systems already installed?

---

### Post by Melhisedek on 2009-05-28
> **philinux said:**
> Can you describe the partition already on these disks and the operating systems already installed?

Hmmm I'm doing this from memory but it is something like:

First harddrive

100 GB C:
600 GB D:
700 GB E:

100 GB free space (It is here I try to install Ubuntu)



Than there is another disc 320 GB that is partitioned in two

I'll try yours installer mate and see how it goes

---

### Post by Melhisedek on 2009-07-01
Bump

---

### Post by Jakey_TheSnake on 2009-07-01
> **Melhisedek said:**
> Hmmm I'm doing this from memory but it is something like:

First harddrive

100 GB C:
600 GB D:
700 GB E:

100 GB free space (It is here I try to install Ubuntu)



Than there is another disc 320 GB that is partitioned in two

I'll try yours installer mate and see how it goes


What is on C, D, E? 

When booting from LiveCD/USB, go into System > Administration > Partition Editor and check the type of partition of each of them. I believe there is something about only being able to have 4 Primary partitions, maybe you already do unwittingly. 

Is the free 100GB formatted at all? If not, try formatting to ext3 as a primary partition first. Note that it will have to be unmounted for you to do anything to it.

---

### Post by Jakey_TheSnake on 2009-07-01
Waaaait a second, apart from the grub install, is the Ubuntu installation still fine? I.e. could we install grub manually now? 

1. Boot from LiveCD/USB.
2. Mount your 100GB Ubuntu partition. 
3. Open up a Terminal
4. Type "sudo grub"
5. Type "find /boot/grub/stage1" (use the output from this command in the next command)
6. Type "root (hd0,1)", replace 1 with whatever it was above. 
7. Type "setup (hd0)" (assuming that the 1.5TB HDD is your first - the number will be the same as the one before the comma you're using above...most likely 0 so no worries). 
8. Type "quit"
9. Open Partition Editor
10. Set the 100GB Ubuntu partition with the boot flag. Restart. If it works, post back and I'll make it so you can boot your Windows partition(s).

---

### Post by Melhisedek on 2009-07-01
Will do as soon as I get home later tonight :)

Thank you mate !!!

I thind C, D, and E are all primary partitions not really sure. Can I "unprimary" them somehow? :)

---

### Post by Melhisedek on 2009-07-01
Here is how my harddrives look like:

[[IMG]http://img262.imageshack.us/img262/2596/52236314.th.png[/IMG]](http://img262.imageshack.us/i/52236314.png/)

I tried disconnecting 2nd harddrive (H, G, I) but got the same error :(

Both discs are SATA and my DVD-rom is IDE if that is to any help
I'm trying to install Ubuntu on to "Free Space"

---

### Post by Melhisedek on 2009-07-01
Darn, something is wrong...

I "installed" Ubuntu as far as it will go (94 percent) and after that it boots from Live CD as installer crashed. So I try to use your commands and here are the results:

> grub> find /boot/grub/stage1

Error 15: File not found

grub> sudo

Error 27: Unrecognized command

grub> find

Error 15: File not found

grub> find /
Error 12: Invalid device requested

grub> find /b
Error 12: Invalid device requested


As you can see I'm mounted on /target don't know what that is...

[[IMG]http://img27.imageshack.us/img27/8626/screenshotakp.th.png[/IMG]](http://img27.imageshack.us/i/screenshotakp.png/)

---

### Post by Melhisedek on 2009-07-01
bump

---

### Post by Melhisedek on 2009-07-02
Here is fdisk -l

```
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x01940193

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       12748   102398278+   7  HPFS/NTFS
/dev/sda2           12749      182401  1362737722+   f  W95 Ext'd (LBA)
/dev/sda5           12749       88911   611779266    7  HPFS/NTFS
/dev/sda6           89238      168377   635691764    7  HPFS/NTFS
/dev/sda7          168378      181826   108029061   83  Linux
/dev/sda8          181827      182401     4618656   82  Linux swap / Solaris

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xed42928a

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        6902    55440283+   5  Extended
/dev/sdb2   *        6903       13914    56323890    7  HPFS/NTFS
/dev/sdb3           13915       38913   200804467+   7  HPFS/NTFS
/dev/sdb5               1        6902    55440252    7  HPFS/NTFS


```

here is what var/log/messages says:

```
Jul  1 22:06:30 ubuntu grub-installer: info: Installing grub on '/dev/sda'
Jul  1 22:06:30 ubuntu grub-installer: info: grub-install supports --no-floppy
Jul  1 22:06:30 ubuntu grub-installer: info: Running chroot /target grub-install  --no-floppy  "/dev/sda"
Jul  1 22:06:30 ubuntu grub-installer: Probing devices to guess BIOS drives. This may take a long time.
Jul  1 22:06:30 ubuntu grub-installer: Searching for GRUB installation directory ... found: /boot/grub
Jul  1 22:06:36 ubuntu grub-installer: The file /boot/grub/stage1 not read correctly.
Jul  1 22:06:36 ubuntu grub-installer: error: Running 'grub-install  --no-floppy  "/dev/sda"' failed.
```

How come I have boot on both drives?

Also what is MBR on my drive? Is it /dev/sda?

---

### Post by austinpsycho on 2009-07-02
do you think he meant set the linux partition as the *active partition??

---

### Post by austinpsycho on 2009-07-02
[http://forums.opensuse.org/archives/sf-archives/archives-install-boot/347167-howto-change-set-active-partition.html](http://forums.opensuse.org/archives/sf-archives/archives-install-boot/347167-howto-change-set-active-partition.html) kind of a similar issue i think it may be of some help

---

### Post by caravel on 2009-07-02
You can remove the boot flag from the other partion(s) using gparted.  Also when installing you can set where you want to install grub so I'm not sure what the issue is?

---

### Post by austinpsycho on 2009-07-02
oh actually; you could use windows to set up the dual boot.  Just boot off your windows install cd, when its finally waiting for your response one of the options will be hit 'r' to get to recovery console.. then type in fixmbr and follow the instructions.  You can add other operating systems from there..

---

### Post by austinpsycho on 2009-07-02
also another option; im not sure if i understood this right, but are you using a live cd?  Cause in my experience live cd's suck.  I've never had good luck with them.  perhaps try redownloading

---

### Post by Melhisedek on 2009-07-02
> **caravel said:**
> You can remove the boot flag from the other partion(s) using gparted.  Also when installing you can set where you want to install grub so I'm not sure what the issue is?

Issue is that GRUB fails and won't install. I have tried pointing it to / , than creating a little partition /boot. All of them fail.

Now I don't know if I can try and install it on some windows partition like sda1

Also one other thing I don't understand is it looks like I have 4 windows partitions on my first HD
```

/dev/sda1   *           1       12748   102398278+   7  HPFS/NTFS
/dev/sda2           12749      182401  1362737722+   f  W95 Ext'd (LBA)
/dev/sda5           12749       88911   611779266    7  HPFS/NTFS
/dev/sda6           89238      168377   635691764    7  HPFS/NTFS
/dev/sda7          168378      181826   108029061   83  Linux
/dev/sda8          181827      182401     4618656   82  Linux swap / Solaris

```

While I only have 3 as you can see here:
[IMG]http://img262.imageshack.us/img262/2596/52236314.png[/IMG]
I will try clearing mbr like you Austin mentioned.

Yes I'm using LiveCD, tried using USB stick as well but still same thing. Is there another way of installing?

Everything installs just fine I believe, there are 3+ Gigs of data on disk so it is just GRUB failing that gets me :(

---

### Post by Melhisedek on 2009-07-02
I've been trying to fool around with Super Grub Disk but all I get is 

Error 15: File not found

no matter what I pick, at the end I tried all the options but got the exact same answer every time :(

---

