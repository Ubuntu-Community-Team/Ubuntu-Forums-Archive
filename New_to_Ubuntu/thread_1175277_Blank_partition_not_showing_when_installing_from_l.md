---
title: "Blank partition not showing when installing from live CD"
date: 2009-06-01
forum: New to Ubuntu
---

### Post by mb1 on 2009-06-01
Hi,
I am a noob and am helping out a friend by installing Ubuntu on his desktop. His HD was partitioned when he installed Windows XP. I am using the Ubuntu live CD now and I was able to mount his windows partition, but the other empty partition does not show up when trying to install Ubuntu. Here is part of the o/p from the lshw command:

        *-disk
             description: ATA Disk
             product: WDC WD6401AALS-0
             vendor: Western Digital
             physical id: 0.0.0
             bus info: scsi@6:0.0.0
             logical name: /dev/sda
             version: 01.0
             serial: WD-WCASY4667410
             size: **596GiB (640GB)**
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=5 signature=50c850c7
           *-volume
                description: Windows NTFS volume
                physical id: 1
                bus info: scsi@6:0.0.0,1
                logical name: /dev/sda1
                logical name: /media/disk
                version: 3.1
                serial: 7227b4f8-1b4b-424a-9e38-4727f1b63710
                size: **488GiB**
                capacity: 488GiB
                capabilities: primary bootable ntfs initialized
                configuration: clustersize=4096 created=2009-04-03 00:00:54 filesystem=ntfs mount.fstype=fuseblk mount.options=rw,nosuid,nodev,user_id=0,group_id=0,allow_other,blksize=4096 state=mounted

Please kindly advice.

---

### Post by Didius Falco on 2009-06-01
Please type ```
fdisk -l
``` in the Terminal and post the output here.

Regards,

Didius

---

### Post by mb1 on 2009-06-01
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x50c850c7

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       63741   511999551    7  HPFS/NTFS
ubuntu@ubuntu:~$

---

### Post by Didius Falco on 2009-06-01
According to the output of that command, you only have one partition on that hard drive, and that's the windows partition.

Go to S**ystem/Administration/Partition Editor** and open it up. If you can, post a screen shot of the Gparted (that is the name of the partitioner I just asked you to open) screen. Then we can see exactly what is going on.

Regards,

Didius

---

### Post by mb1 on 2009-06-01
Thanks Didius Falco.
I have also attached the screen shot when I am installing from the live CD.

---

### Post by Didius Falco on 2009-06-01
Thanks for posting that - it makes it a lot easier to see exactly what the situation is.

Let's "talk" about how your friend wants to set it up.

You want to use all the free space for Ubuntu?

Do you want a separate Home partition? (I recommend it)

Do you want a third partition just for your own Data, and do you want to share it with Windows?

How much RAM is in your PC?

Do you use Hibernation mode?

Answer these and I will help you set up the partitions you'll need and get you started on the install.

Regards,

Didius

---

### Post by mb1 on 2009-06-01
Please see below. Thanks.
> **Didius Falco said:**
> Thanks for posting that - it makes it a lot easier to see exactly what the situation is.

Let's "talk" about how your friend wants to set it up.

You want to use all the free space for Ubuntu?
Yes I would want to use all the free space(~100 gigs) for Ubuntu

Do you want a separate Home partition? (I recommend it)
Sure, if that is better

Do you want a third partition just for your own Data, and do you want to share it with Windows?
I can mount the windows partition and move files around if needed, right? I want to keep it simple for now.

How much RAM is in your PC?
1.5 gigs

Do you use Hibernation mode?
No

Answer these and I will help you set up the partitions you'll need and get you started on the install.

Regards,

Didius

---

### Post by Didius Falco on 2009-06-01
> **mb1 said:**
> Please see below. Thanks.

Use Gparted to do the following. If I tell you things you already know, please don't be offended. It's just easier to tell you everything you might need to know at once, so as to get you moving forward sooner:

1. Right-click on the Windows partition to highlight it and open a menu. Unmount the Windows partition.

2. Left click in the "unallocated" space. Go to the **Partition** menu and select new. Make an Extended partition and let it use all of the free space. Click  the **Apply **button to create the Extended partition.

3. Click inside the Extended partition and make 3 partitions:

A. First make a Linux Swap partition 1.5 Gigs in size. Format it in the Linux Swap file system.

B. The next two will be EXT3 partitions. Make the next one 15 Gigs, and format it to EXT3 file system. This will be your Ubuntu Root (/) partition

C. Make the last one EXT3 as well, and use all the remaining space.

More in next message...

---

### Post by Didius Falco on 2009-06-01
After you have created all your partitions, quit out of Gparted and start the installer.

When it gets to the Partitioner, choose the **Manual (advanced)** option.

Select the swap partition and click the "Edit Partition" button at the bottom of the screen. Set it to "Use" and "Swap" type.

Next select the 15 Gig partition, and click the "Edit Partition" button. Set this one to "Use", "EXT3" and type "/". This marks it as your root partition.

Repeat the above on the last partition, except set the Type to "Home".

After you've done this continue on with the install.

After you are done and it boots into Ubuntu, it will automatically use the swap partition, and your Home partition will appear as though it is part of the Ubuntu partition, so you don't have to do anything special to use it.

Having a separate Home makes reinstall and upgrades easier, because all your data and your configuration files will be on that separate partition.

That way, if you ever decide to reinstall the same version or upgrade to a newer version, your data and configuration files will be separate and not overwritten.

That about covers it - other than to to remind you that, although 99 times out of a hundred, partitioning won't cause any problems, there is always a danger of losing your existing Data. Backups are always recommended.

I hope this helps, and if you have more questions, come on back and post 'em.

Regards,

Didius

---

### Post by mb1 on 2009-06-01
Thank you again.

---

### Post by Didius Falco on 2009-06-01
My pleasure!

You partition faster than I can type! ;)

Enjoy Ubuntu - I think you'll like it. This forum is a great place for information and help, so be sure and drop in.

Regards,

Didius

---

### Post by mb1 on 2009-06-01
Thank you very much Didius Falco. I will try it and let you know. Your help is appreciated very much. :)

---

### Post by mb1 on 2009-06-01
The partitioning worked Didius Falco. Thanks for all your help. Ubuntu does look very interesting :D
Be well..

---

### Post by Didius Falco on 2009-06-01
You are most welcome! Thanks for reporting back on your progress.

Regards,

Didius

---

### Post by mal1958 on 2009-06-02
I had a similar problem on another system that I was setting up for a neighbor and his son.  I followed your walk through Didius and they are up and running on Ubuntu now and happier then ever,  I would like to add my thanks for such a detailed walkthrough and the Thanks of Frank SR. and JR.   Now if I can just figure out a way to format and control this western digital usb external through Ubuntu I will be happy.

Mike

---

### Post by Didius Falco on 2009-06-02
Thanks for sharing that, Mike.

Helping others is, ultimately, a selfish act for me. It makes me feel good to know that I've helped someone. A two-fer is even better!

Post a new thread (if you haven't already) about your external drive and I'm sure someone will help you get it up and running.

It sounds, off the top of my head, like a permissions problem that should be fairly simple to fix.

Regards,

Didius

---

### Post by jkjuk on 2009-09-23
Thanks to advice by Didius Falco, I have managed to successfully install Ubuntu 9.04 on my Dell D620. Installs from Live CD from within Windows 7 had repeatedly failed with log showing Error 22. I deleted one of the spare NTFS partitions during Ubuntu install and created it as 3 partitions as recommended. Success and now I can use both Windows 7 RC and Ubuntu 9.04. I am new to Linux but initial impressions are good. Just for sheer speed of O/S load and web browsing I will stick with Ubuntu and may learn to use other applications  in time.

JKJ

---

### Post by elpasmo on 2009-11-01
Hi,  I'm trying to install ubuntu 9.10 karmic koala on a friend's computer and I have the same problem. When I arrive to the partition step all I get is an empty list.  I've tried to follow the Didius guide without success.  

This is the current situation: 

Disco /dev/sda: 200.0 GB, 200049647616 bytes
255 cabezas, 63 sectores/pista, 24321 cilindros
Unidades = cilindros de 16065 * 512 = 8225280 bytes
Identificador de disco: 0xd1b3d1b3

Disposit. Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/sda1   *           1       12748   102398278+   7  HPFS/NTFS
/dev/sda2           12749       24321    92960122+   5  Extendida
/dev/sda5           12749       12975     1823346   82  Linux swap / Solaris
/dev/sda6           12976       24321    91136713+  83  Linux

---

### Post by 1branchonthevine on 2009-12-11
Okay, then explain this...

I can't even get Karmic to even see my drive (sda) during install. But it is seen by fdisk -l  and gparted, and I can even mount it within the live cd! Running my head around this one!

---

