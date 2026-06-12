---
title: "mdadm /etc/mdadm.conf: Permission denied ..."
date: 2009-04-27
forum: New to Ubuntu
---

### Post by oehq on 2009-04-27
I am running ubuntu 9.04 Can someone please help me in mounting a software raid?

I am trying to mount a software raid that I created
the sudo fdisk -l
Displays the following
************************************************** *********
Disk /dev/sda: 80.0 GB, 80000000000 bytes
255 heads, 63 sectors/track, 9726 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x142f142e

Device Boot Start End Blocks Id System
/dev/sda1 * 1 9544 76662148+ 83 Linux
/dev/sda2 9545 9726 1461915 5 Extended
/dev/sda5 9545 9726 1461883+ 82 Linux swap / Solaris

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000787cb

Device Boot Start End Blocks Id System
/dev/sdb1 1 121601 976760001 fd Linux raid autodetect

Disk /dev/sdc: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0001770e

Device Boot Start End Blocks Id System
/dev/sdc1 1 121601 976760001 fd Linux raid autodetect

Disk /dev/md_d0: 1000.2 GB, 1000202174464 bytes
2 heads, 4 sectors/track, 244189984 cylinders
Units = cylinders of 8 * 512 = 4096 bytes
Disk identifier: 0x00000000

Disk /dev/md_d0 doesn't contain a valid partition table
heffsvr@heffsvr-us01:~$
************************************************** **********

Do I need to build a partition on this raid to get it to mount??
If so How do I do it?

What would the command be to mount the drive as /mnt/U_raid1

I was following the guide
[http://bfish.xaedalus.net/?p=188=3](http://bfish.xaedalus.net/?p=188=3)

but when I got to the step
sudo echo "DEVICE partitions" > /etc/mdadm/mdadm.conf
I received the following

*************************************************
sudo echo "DEVICE partitions" > /etc/mdadm/mdadm.conf
bash: /etc/mdadm.conf: Permission denied
***********************************************

I have since rebooted and now I cannot mount the raid
/dev/md_d0

sudo watch cat /proc/mdstat shows raid is syncing...
*******************************************
md_0 : active raid sdb1[0] sdc1[1]
*******************************************

so it looks like the raid exist
can you help me mount it?? it says it is says resync = 93%
How do I partition it ?
I want just want one large partition for the whole volume

also I need help with how to automate this mounting process on reboots?

Thanks so much for the Help

Jim

ps I can someone tell me how to make a shortcut to nautalis from the system menu it is a pain to go to the command window every time I want to use the file manager?

---

