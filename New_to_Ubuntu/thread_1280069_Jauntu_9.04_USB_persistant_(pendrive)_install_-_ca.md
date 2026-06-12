---
title: "Jauntu 9.04 USB persistant (pendrive) install - can't add more SWAP"
date: 2009-10-01
forum: New to Ubuntu
---

### Post by &#1058;&#1086;&#1084;&#1080;&#1094;&#1072; on 2009-10-01
Hello everyone.

I'm new here and I'm very glad to be joining you. I'm a complete beginner on Linux, and I LOVE it!

Now, right from the start I have a problem which I tried to find a solution for on this forum, but failed. So, if there is a similar topic, please forgive me for re-posting, I did my best to search for a solution.

I recently installed Jaunty on my 8GB USB Flash memory stick using [this tutorial]("http://www.pendrivelinux.com/usb-ubuntu-904-persistent-install-windows/"). What I noticed afterwards is that:
[LIST=a]
[*]my SWAP file is much smaller than optimal, 120MB;
[*]it keeps filling up at a (by my opinion) much faster rate than it should, resulting in being filled within 15 minutes, after which I simply can't use my Ubuntu without restarting it;
[/LIST]
I found [this other tutorial]("https://help.ubuntu.com/community/SwapFaq") which helps add more SWAP. I did everything from the tutorial, except I made a 120MB file instead of 512MB but after the command:
```
sudo swapon /mnt/120Mb.swap
```
I get this error message:
```
swapon: /mnt/120Mb.swap: Input/output error
```
Can anyone help me please? Thanks in advance!

---

### Post by bbukh on 2009-10-06
I have exactly the same problem. USB pen drive install using PortableLinux, and want a bigger swap, but upon running swapon get the same message. The '-v' (verbose) option to swapon does not provide any additional information.

---

### Post by Crumbles on 2009-10-19
Just tried this today and got the exact same error... Go ubuntu!

```
ubuntu@ubuntu:~$ sudo su -
root@ubuntu:~# free
             total       used       free     shared    buffers     cached
Mem:       3566556    2651228     915328          0      26452     524488
-/+ buffers/cache:    2100288    1466268
Swap:            0          0          0
root@ubuntu:~# dd if=/dev/zero of=/mnt/1024Mb.swap bs=1M count=1024
1024+0 records in
1024+0 records out
1073741824 bytes (1.1 GB) copied, 38.491 s, 27.9 MB/s
root@ubuntu:~# mkswap /mnt/1024Mb.swap
Setting up swapspace version 1, size = 1048572 KiB
no label, UUID=fd17c734-5098-47f0-a166-05f40500e690
root@ubuntu:~# swapon /mnt/1024Mb.swap
swapon: /mnt/1024Mb.swap: Input/output error
```

---

### Post by Mighty_Joe on 2009-10-19
My wild-assed guess is that because the "live cd" style install doesn't have "real" disk space to work with (both the compressed "live" file system and the persistent casper-rw file have to be loaded into memory to be used), one cannot create a swap file inside the persistent partition and use it as swap space.
You could try creating a new partition on the USB drive using GParted and using that as swap space.
I'd caution against using swap on a flash drive if it is at all possible.  Flash drives can [wear out]("http://www.bress.net/blog/archives/114-How-Long-Does-a-Flash-Drive-Last.html"), though under ordinary use, they will last a very long time.  My laptop has 2Gb of RAM.  I don't use swap at all and haven't had any problems.

---

### Post by Crumbles on 2009-10-19
Mighty_Joe, thanks for your reply.  Here's why I was doing it...

I'm currently running a multipass setup off of a seagate portable hard drive.  (one of the really small ones.)  I carry it around with my in my laptop bag.  It's great because I can literally boot up my computer anywhere I go.

I have two virtual boxes (a Win7 and a WinXP) running in ubuntu.  I use the XP one at work, and the Win7 one is just to mess around with.  Well, today I loaded both of them at the same time.  I noticed that the local hard drive activity light on the laptop started going haywire and I could hear the laptop hard drive running!  NOTHING I'm doing should be touching the local hard drive on the laptop.

My only explanation as to what was going on, was I had possibly run out of RAM on the laptop (it has 3.5 GB), so Ubuntu just randomly decided to choose the local hard drive it saw mounted?  I have no other explanation as to WHAT or WHY it was writing to the local laptop hard drive for.

I shut down the system, and removed the laptop hard drive entirely from the laptop just to confirm that I was actually running everything off of the segate portable hard drive.  Everything still ran fine...

So, do you have any ideas as to what ubuntu was writing to the local hard drive?  My only guess was I was in need of more swap or something...

Is there a way I can tell ubuntu to NEVER use any other drive except my EXT3 partition I have set up? The fact that ubuntu just wrote a ton of data to the laptop hard drive totally defeats my purpose of what I'm doing.  I want to not leave any traces of anything behind on the PC I boot from.

Thanks in advance.

---

### Post by KhanTG on 2009-10-20
@ Crumbles...

I had a similar issue (I think).  My problem was running out of space for the casper-rw file.  I am running a persistent USB install (made with Ubuntu's USB Startup Disk Creator) on an iomega 250GB HDD (the small USB type).  I created a 40GB ext2 partition (using gparted) and labeled it "casper-rw"... then I deleted the casper-rw file that was on the USB installation.  no more problems .. the rest of the disk is formatted as fat32 (so it can be used as storage on any OS).  Of course I'm not runing vmware (yet), nor would I attempt to run two vboxes at the same time (it being a USB device and all).. but I'll give it a shot just to see if I can (and to see if I get the same issue)... regardless, my setup doesn't touch my systems native HDD....

Hope this was all relevant to your situation... 

Regards!

---

### Post by Crumbles on 2009-10-20
I'm not using a file either... The seagate drive is around 250 GB, and my EXT3 casper-rw partition is over 100 GB of that...

So, I'm still not sure why it was writing to the local hard drive... :(

---

### Post by Mighty_Joe on 2009-10-20
> **Crumbles said:**
> So, I'm still not sure why it was writing to the local hard drive... :(

Unless you configured Ubuntu to mount your laptop drive, it can not use it. Is it possible that your laptop's disk activity LED lights when writing to a USB drive?  I've never looked at mine while running Ubuntu on a flash drive to tell the truth.
Post the contents of your /etc/fstab file

---

### Post by Crumbles on 2009-10-20
> **Mighty_Joe said:**
> Unless you configured Ubuntu to mount your laptop drive, it can not use it. Is it possible that your laptop's disk activity LED lights when writing to a USB drive?  I've never looked at mine while running Ubuntu on a flash drive to tell the truth.
Post the contents of your /etc/fstab fileWell... technically it's a live install with persistance... as far as I know, ubuntu finds all drives and mounts them automatically on boot.  I'm not sure how to stop it from mounting the hard drive...  although, you make a good point, I can just right click the drive and choose unmount if I wanted....  here's the contents of what you requested:

```

ubuntu@ubuntu:~$ cat /etc/fstab
aufs / aufs rw 0 0
tmpfs /tmp tmpfs nosuid,nodev 0 0
/dev/sda6 swap swap defaults 0 0

```

---

### Post by Mighty_Joe on 2009-10-20
> **Crumbles said:**
> as far as I know, ubuntu finds all drives and mounts them automatically on boot.

The only Live CD type install I have handy is the 9.10 UNR Beta. It does not mount the internal hard drive on my laptop (just rebooted to check).  The purpose of the Live CD is to try out Ubuntu without making changes, so it makes sense not to mount anything unless explicitly told to.
Is /dev/sda6 your USB drive or your hard drive?  On my Live USB, /dev/sdb is the thumb drive.  It may be that you created your swap file on the internal hard drive.

---

### Post by Crumbles on 2009-10-20
> **Mighty_Joe said:**
> The only Live CD type install I have handy is the 9.10 UNR Beta. It does not mount the internal hard drive on my laptop (just rebooted to check).  The purpose of the Live CD is to try out Ubuntu without making changes, so it makes sense not to mount anything unless explicitly told to.Right, but I'm doing something pretty unique.  The reason for this setup is so that ubuntu is not installed and configured for a single PC.  I can literally plug this hard drive into any box, boot from it (thanks to the way the live CD acts) and have my ubuntu box, and windows boxes all one.

[quote=Mighty_Joe]Is /dev/sda6 your USB drive or your hard drive?  On my Live USB, /dev/sdb is the thumb drive.  It may be that you created your swap file on the internal hard drive.[/quote]I don't know a lot about linux yet, so, I may not give you information you're asking for... but, after doing the following command:

```

ubuntu@ubuntu:~$ fdisk -l
ubuntu@ubuntu:~$ sudo !!
sudo fdisk -l

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa42d04a3

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1          23      184716   de  Dell Utility
/dev/sda2   *          24       11767    94333680    7  HPFS/NTFS
/dev/sda3           11768       30401   149677605    5  Extended
/dev/sda5           11768       29639   143556808+  83  Linux
/dev/sda6           29640       30401     6120733+  82  Linux swap / Solaris

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000c9ba7

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       16043   128865366    7  HPFS/NTFS
/dev/sdb2           16044       30337   114816555   83  Linux
/dev/sdb3           30338       30401      514080    c  W95 FAT32 (LBA)

```

It would appear that SDA2 is my local laptop hard drive NTFS partition -- SDB1 is the NTFS partition on my portable segate drive, SDB2 is ubuntu's partition, and SDB3 is a FAT32 partition I had to setup to get a live Kaspersky CD to work right with the multipass...

I don't have any swap set up, that's where I was originally getting stuck :(

---

### Post by Mighty_Joe on 2009-10-20
> **Crumbles said:**
> I don't have any swap set up, that's where I was originally getting stuck :(

Your post [here]("http://ubuntuforums.org/showpost.php?p=8134644&postcount=9") shows your fstab is set up to mount /dev/sda6 as swap and that partition is on your local hard drive.  This explains the behavior you saw [here]("http://ubuntuforums.org/showpost.php?p=8132370&postcount=5").  When you started up your virtual boxes, the system started using the swap on the local hard drive, which made the hard disk LED go haywire. 
You may have validated my [post]("http://ubuntuforums.org/showpost.php?p=8128673&postcount=4") where I suggested using a separate partition for swap, as opposed to a swap file.

---

### Post by Crumbles on 2009-10-20
> **Mighty_Joe said:**
> Your post [here]("http://ubuntuforums.org/showpost.php?p=8134644&postcount=9") shows your fstab is set up to mount /dev/sda6 as swap and that partition is on your local hard drive.  This explains the behavior you saw [here]("http://ubuntuforums.org/showpost.php?p=8132370&postcount=5").  When you started up your virtual boxes, the system started using the swap on the local hard drive, which made the hard disk LED go haywire. 
You may have validated my [post]("http://ubuntuforums.org/showpost.php?p=8128673&postcount=4") where I suggested using a separate partition for swap, as opposed to a swap file.
OK, so you figured out what happened then.

My local laptop has a dual boot Windows/Ubuntu INSTALL on the laptop.  My external hard drive must have seen this swap file set up by the installed ubuntu and started using it...

---

