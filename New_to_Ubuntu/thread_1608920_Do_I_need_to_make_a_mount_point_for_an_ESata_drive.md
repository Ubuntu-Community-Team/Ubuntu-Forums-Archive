---
title: "Do I need to make a mount point for an ESata drive"
date: 2010-10-29
forum: New to Ubuntu
---

### Post by grewolf on 2010-10-29
I am currently running ubuntu 10.10 (maverick) and I beleive I have a mounting issue but am not sure.  I have installed the vantec 6 port pci host card with raid.  I am not using the raid function.  Here is what I have for the code lspci

```
01:09.0 RAID bus controller: Silicon Image, Inc. SiI 3114 [SATALink/SATARaid] Serial ATA Controller (rev 02)
	Subsystem: Silicon Image, Inc. Device 7114
	Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 17
	I/O ports at cc00 [size=8]
	I/O ports at c800 [size=4]
	I/O ports at c400 [size=8]
	I/O ports at c000 [size=4]
	I/O ports at bc00 [size=16]
	Memory at fdeff000 (32-bit, non-prefetchable) [size=1K]
	Expansion ROM at fde00000 [disabled] [size=512K]
	Capabilities: [60] Power Management version 2
	Kernel driver in use: sata_sil
	Kernel modules: sata_sil

```

So it sees the card.  but when I do fdisk- l it doesn't see the drive

I have tried to follow this post

 [http://ubuntuforums.org/showthread.php?t=907124]("http://ubuntuforums.org/showthread.php?t=907124")

but have not had any luck viewing the drive.

The external drive is a Western digital 1tb drive mounted in a nexstar 3 enclosure and it has both a usb connection and a esata connection.  I have connected it through the usb with no problems it was picked up by maverick right away.  

I have read that usb and esata are viewed differently by maverick...  Now if I understand correctly I need a mount point when I have it connected via esata but don't when it is connected via usb

Thank you for your time

---

### Post by NT4usB on 2010-10-29
I'm using 10.04 and have a SATA card:
02:01.0 Mass storage controller: Silicon Image, Inc. SiI 3512 [SATALink/SATARaid] Serial ATA Controller (rev 01)

Before I upgraded to 10.04 I would have to run:```
sudo scsiadd -s 3
``` after plugging in a drive.

Since 10.04, they are automagically detected however, sometimes they don't mount.

fwiw, I don't hot swap the drives. I plug them in, then power up. Always umount and power down the drive before swapping drives.

From a fresh boot, I run ```
ls -alh /dev/sd*
```
to see all the drives...```
brw-rw---- 1 root disk 8,  0 2010-10-28 18:48 /dev/sda
brw-rw---- 1 root disk 8,  1 2010-10-28 18:48 /dev/sda1
brw-rw---- 1 root disk 8,  2 2010-10-28 18:48 /dev/sda2
brw-rw---- 1 root disk 8,  3 2010-10-28 18:48 /dev/sda3
brw-rw---- 1 root disk 8,  4 2010-10-28 18:48 /dev/sda4
brw-rw---- 1 root disk 8,  5 2010-10-28 18:48 /dev/sda5
brw-rw---- 1 root disk 8,  6 2010-10-28 18:48 /dev/sda6
brw-rw---- 1 root disk 8, 16 2010-10-28 18:48 /dev/sdb
brw-rw---- 1 root disk 8, 17 2010-10-28 18:48 /dev/sdb1
```
Then plug in and power up the eSATA drive. 
ls *bla* again and I see the new sd* device has been added.```
brw-rw---- 1 root disk 8,  0 2010-10-28 18:48 /dev/sda
brw-rw---- 1 root disk 8,  1 2010-10-28 18:48 /dev/sda1
brw-rw---- 1 root disk 8,  2 2010-10-28 18:48 /dev/sda2
brw-rw---- 1 root disk 8,  3 2010-10-28 18:48 /dev/sda3
brw-rw---- 1 root disk 8,  4 2010-10-28 18:48 /dev/sda4
brw-rw---- 1 root disk 8,  5 2010-10-28 18:48 /dev/sda5
brw-rw---- 1 root disk 8,  6 2010-10-28 18:48 /dev/sda6
brw-rw---- 1 root disk 8, 16 2010-10-28 18:48 /dev/sdb
brw-rw---- 1 root disk 8, 17 2010-10-28 18:48 /dev/sdb1
brw-rw---- 1 root disk 8, 32 2010-10-29 18:07 /dev/sdc
brw-rw---- 1 root disk 8, 33 2010-10-29 18:07 /dev/sdc1
```Then, if it didn't mount...```
 sudo mount /dev/sdc1 (*or whatever*) /mnt/
```

10.04 is pretty good about automounting but after a few dozen swaps it sometimes gives up. Then I have to go through the ```
 sudo mount *bla* sudo umount *bla* 
``` routine...

...Looks like it mounted automagically this time:```
ct@g41p2:/etc/default$ mount -l | grep sd
/dev/sda5 on / type ext3 (rw,errors=remount-ro) [root]
/dev/sda1 on /boot type ext3 (rw) [boot]
/dev/sdb1 on /raid type ext3 (rw)
/dev/sda6 on /home type ext3 (rw) [home]
/dev/sda4 on /vid type ext3 (rw) [vid]
ct@g41p2:/etc/default$ mount -l | grep sd
/dev/sda5 on / type ext3 (rw,errors=remount-ro) [root]
/dev/sda1 on /boot type ext3 (rw) [boot]
/dev/sdb1 on /raid type ext3 (rw)
/dev/sda6 on /home type ext3 (rw) [home]
/dev/sda4 on /vid type ext3 (rw) [vid]
/dev/sdc1 on /media/HIT_10_10 type ext3 (rw,nosuid,nodev,uhelper=udisks) [HIT_10_10]
```

ed: Although the eSATA drive shows up in Nautilus, have to click on it to get it to actually mount...

---

### Post by grewolf on 2010-10-30
```
ls -alh /dev/sd*
```


After I did this it showed the drive and I was able to access it.  Thank you.  :P

---

