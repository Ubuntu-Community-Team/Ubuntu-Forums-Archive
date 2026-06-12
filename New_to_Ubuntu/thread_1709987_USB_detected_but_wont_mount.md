---
title: "USB detected but wont mount"
date: 2011-03-19
forum: New to Ubuntu
---

### Post by daveboy23 on 2011-03-19
when i plug the USB HD it shows:

Unable to mount location
[B]Error mounting: mount exited with exit code 1: helper failed with:
mount: wrong fs type, bad option, bad superblock on /dev/sdb1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so[/B]


anyone can help? what going on?

---

### Post by mikewhatever on 2011-03-19
You might need to run a file system check. Do you know what file system there is?

---

### Post by NightwishFan on 2011-03-19
Check System -> Administration -> Disk Utility for information about the drive. It should show what the partitioning scheme is and info about the individual partitions.

---

### Post by vivek.pandey on 2011-03-19
sorry to post it here instead of starting new thread.... but i am also facing exactly the same problem with same error... should i take it as my usb device (flash drive) is corrupted?

---

### Post by r-senior on 2011-03-19
Could you (both) try the following (the order of all this is important) and post output from the commands:

Confirm your kernel version:

```

$ uname -r

```

With the drive unplugged:

```

$ sudo fdisk -l
$ lsusb
$ tail -f /var/log/syslog

```

Now plug in the device and record the messages in the syslog. Control-C to stop following the log file.

```

$ sudo fdisk -l
$ lsusb

```

If lsusb hangs say so, otherwise record the output. Unplug the device.

---

### Post by vivek.pandey on 2011-03-19
i get a strange output with this

```

vivek@NEO:~$ dmesg | tail
[15593.681852] sd 25:0:0:0: [sdd] Mode Sense: 0b 00 00 08
[15593.681875] sd 25:0:0:0: [sdd] Assuming drive cache: write through
[15593.722122] sd 25:0:0:0: [sdd] Assuming drive cache: write through
[15593.722134]  sdd: sdd1 sdd2
[15593.779677] sd 25:0:0:0: [sdd] Assuming drive cache: write through
[15593.779691] sd 25:0:0:0: [sdd] Attached SCSI removable disk
[15599.539089] type=1400 audit(1300535596.236:537): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/mysqld" pid=29329 comm="apparmor_parser"
[15629.799425] type=1400 audit(1300535626.508:538): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/mysqld" pid=29442 comm="apparmor_parser"
[15660.050581] type=1400 audit(1300535656.772:539): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/mysqld" pid=29550 comm="apparmor_parser"
[15690.297354] type=1400 audit(1300535687.032:540): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/mysqld" pid=29664 comm="apparmor_parser"
vivek@NEO:~$ 


```

now what this is all about..what are the last few lines doing there?

---

### Post by r-senior on 2011-03-19
It's something to do with MySQL database and [AppArmor](http://en.wikipedia.org/wiki/AppArmor). Not relevant to your USB drive.

---

### Post by vivek.pandey on 2011-03-19
> **r-senior said:**
> Could you (both) try the following (the order of all this is important) and post output from the commands:

Confirm your kernel version:

```

$ uname -r

```

With the drive unplugged:

```

$ sudo fdisk -l
$ lsusb
$ tail -f /var/log/syslog

```

Now plug in the device and record the messages in the syslog. Control-C to stop following the log file.

```

$ sudo fdisk -l
$ lsusb

```

If lsusb hangs say so, otherwise record the output. Unplug the device.

hey thanx for your reply
here is what you asked for

without pen drive inserted 
```


vivek@NEO:~$ uname -r
2.6.35-27-generic

vivek@NEO:~$ sudo fdisk -l
[sudo] password for vivek: 

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xf0000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1          49      393561   de  Dell Utility
/dev/sda2              50        1240     9565184    7  HPFS/NTFS
/dev/sda3   *        1241       23295   177150976    7  HPFS/NTFS
/dev/sda4           23295       38914   125458433    f  W95 Ext'd (LBA)
/dev/sda5           23295       28497    41783183    7  HPFS/NTFS
/dev/sda6           28497       33423    39569408   83  Linux
/dev/sda7           33423       33639     1738752   82  Linux swap / Solaris
/dev/sda8           33640       38692    40577024   83  Linux
/dev/sda9           38692       38914     1780736   82  Linux swap / Solaris

vivek@NEO:~$ lsusb
Bus 002 Device 061: ID 0458:003a KYE Systems Corp. (Mouse Systems) NetScroll+ Mini Traveler
Bus 002 Device 060: ID 05e3:0608 Genesys Logic, Inc. USB-2.0 4-Port HUB
Bus 002 Device 023: ID 230d:0001  
Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 008: ID 413c:8160 Dell Computer Corp. 
Bus 001 Device 007: ID 413c:8162 Dell Computer Corp. 
Bus 001 Device 006: ID 413c:8161 Dell Computer Corp. 
Bus 001 Device 005: ID 0bda:0158 Realtek Semiconductor Corp. USB 2.0 multicard reader
Bus 001 Device 004: ID 0c45:641d Microdia 
Bus 001 Device 003: ID 0a5c:4500 Broadcom Corp. BCM2046B1 USB 2.0 Hub (part of BCM2046 Bluetooth)
Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
vivek@NEO:~$ tail -f /var/log/syslog >log
Mar 19 17:51:46 NEO kernel: [17309.436337] sd 28:0:0:0: [sdd] Assuming drive cache: write through
Mar 19 17:51:46 NEO kernel: [17309.477764] sd 28:0:0:0: [sdd] Assuming drive cache: write through
Mar 19 17:51:46 NEO kernel: [17309.477780]  sdd: sdd1 sdd2
Mar 19 17:51:46 NEO kernel: [17309.536363] sd 28:0:0:0: [sdd] Assuming drive cache: write through
Mar 19 17:51:46 NEO kernel: [17309.536377] sd 28:0:0:0: [sdd] Attached SCSI removable disk
Mar 19 17:52:01 NEO init: mysql post-start process (3905) terminated with status 1
Mar 19 17:52:01 NEO kernel: [17323.664153] type=1400 audit(1300537321.048:594): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/mysqld" pid=4031 comm="apparmor_parser"
Mar 19 17:52:03 NEO kernel: [17326.002856] usb 2-1.2: USB disconnect, address 62
Mar 19 17:52:06 NEO init: mysql main process (4035) terminated with status 1
Mar 19 17:52:06 NEO init: mysql main process ended, respawning
Mar 19 17:52:31 NEO init: mysql post-start process (4036) terminated with status 1
Mar 19 17:52:31 NEO kernel: [17353.930055] type=1400 audit(1300537351.324:595): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/mysqld" pid=4147 comm="apparmor_parser"
Mar 19 17:52:36 NEO init: mysql main process (4151) terminated with status 1
Mar 19 17:52:36 NEO init: mysql main process ended, respawning
Mar 19 17:53:01 NEO init: mysql post-start process (4152) terminated with status 1
Mar 19 17:53:01 NEO kernel: [17384.182039] type=1400 audit(1300537381.592:596): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/mysqld" pid=4260 comm="apparmor_parser"
Mar 19 17:53:07 NEO init: mysql main process (4264) terminated with status 1
Mar 19 17:53:07 NEO init: mysql main process ended, respawning
Mar 19 17:53:31 NEO init: mysql post-start process (4265) terminated with status 1
Mar 19 17:53:31 NEO kernel: [17414.440098] type=1400 audit(1300537411.860:597): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/mysqld" pid=4373 comm="apparmor_parser"
Mar 19 17:53:37 NEO init: mysql main process (4377) terminated with status 1
Mar 19 17:53:37 NEO init: mysql main process ended, respawning
Mar 19 17:54:02 NEO init: mysql post-start process (4378) terminated with status 1
Mar 19 17:54:02 NEO kernel: [17444.673553] type=1400 audit(1300537442.108:598): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/mysqld" pid=4484 comm="apparmor_parser"
Mar 19 17:54:07 NEO init: mysql main process (4488) terminated with status 1
Mar 19 17:54:07 NEO init: mysql main process ended, respawning
Mar 19 17:54:32 NEO init: mysql post-start process (4489) terminated with status 1
Mar 19 17:54:32 NEO kernel: [17474.910559] type=1400 audit(1300537472.356:599): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/mysqld" pid=4595 comm="apparmor_parser"
Mar 19 17:54:38 NEO init: mysql main process (4599) terminated with status 1
Mar 19 17:54:38 NEO init: mysql main process ended, respawning


```

here is the output with pen drive inserted

```

vivek@NEO:~$ sudo fdisk -l
[sudo] password for vivek: 

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xf0000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1          49      393561   de  Dell Utility
/dev/sda2              50        1240     9565184    7  HPFS/NTFS
/dev/sda3   *        1241       23295   177150976    7  HPFS/NTFS
/dev/sda4           23295       38914   125458433    f  W95 Ext'd (LBA)
/dev/sda5           23295       28497    41783183    7  HPFS/NTFS
/dev/sda6           28497       33423    39569408   83  Linux
/dev/sda7           33423       33639     1738752   82  Linux swap / Solaris
/dev/sda8           33640       38692    40577024   83  Linux
/dev/sda9           38692       38914     1780736   82  Linux swap / Solaris

Disk /dev/sdd: 34.4 GB, 34359738368 bytes
64 heads, 32 sectors/track, 32768 cylinders
Units = cylinders of 2048 * 512 = 1048576 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000eec81

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1       32768    33554416   83  Linux
/dev/sdd2               1           1          15+   0  Empty
Partition 2 does not end on cylinder boundary.
vivek@NEO:~$ lsusb
Bus 002 Device 063: ID 6610:6610  
Bus 002 Device 061: ID 0458:003a KYE Systems Corp. (Mouse Systems) NetScroll+ Mini Traveler
Bus 002 Device 060: ID 05e3:0608 Genesys Logic, Inc. USB-2.0 4-Port HUB
Bus 002 Device 023: ID 230d:0001  
Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 008: ID 413c:8160 Dell Computer Corp. 
Bus 001 Device 007: ID 413c:8162 Dell Computer Corp. 
Bus 001 Device 006: ID 413c:8161 Dell Computer Corp. 
Bus 001 Device 005: ID 0bda:0158 Realtek Semiconductor Corp. USB 2.0 multicard reader
Bus 001 Device 004: ID 0c45:641d Microdia 
Bus 001 Device 003: ID 0a5c:4500 Broadcom Corp. BCM2046B1 USB 2.0 Hub (part of BCM2046 Bluetooth)
Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
vivek@NEO:~$ 

```

thanx again

---

### Post by r-senior on 2011-03-19
It seems to recognise the USB device, although there's no information displayed for it:

```

$ lsusb
[COLOR="Red"]Bus 002 Device 063: ID 6610:6610 [/COLOR] 
Bus 002 Device 061: ID 0458:003a KYE Systems Corp. (Mouse Systems) NetScroll+ Mini Traveler
Bus 002 Device 060: ID 05e3:0608 Genesys Logic, Inc. USB-2.0 4-Port HUB
Bus 002 Device 023: ID 230d:0001  
Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 008: ID 413c:8160 Dell Computer Corp. 
Bus 001 Device 007: ID 413c:8162 Dell Computer Corp. 
Bus 001 Device 006: ID 413c:8161 Dell Computer Corp. 
Bus 001 Device 005: ID 0bda:0158 Realtek Semiconductor Corp. USB 2.0 multicard reader
Bus 001 Device 004: ID 0c45:641d Microdia 
Bus 001 Device 003: ID 0a5c:4500 Broadcom Corp. BCM2046B1 USB 2.0 Hub (part of BCM2046 Bluetooth)
Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

And it's showing up as a filesystem with fdisk (could you confirm that looks like what you are plugging in - a 35GB external hard drive?):

```

Disk /dev/sdd: 34.4 GB, 34359738368 bytes
64 heads, 32 sectors/track, 32768 cylinders
Units = cylinders of 2048 * 512 = 1048576 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000eec81

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1       32768    33554416   83  Linux
/dev/sdd2               1           1          15+   0  Empty
Partition 2 does not end on cylinder boundary.

```

Beyond that I don't know. I'm having a different USB problem and I thought (hoped) it might be related. Someone else might be able to help.

Have you tried following the instructions in here to mount it manually? **Make sure you also unmount it**.

[https://help.ubuntu.com/community/Mount/USB](https://help.ubuntu.com/community/Mount/USB)

---

### Post by vivek.pandey on 2011-03-19
> **r-senior said:**
> It seems to recognise the USB device, although there's no information displayed for it:

```

$ lsusb
[COLOR="Red"]Bus 002 Device 063: ID 6610:6610 [/COLOR] 
Bus 002 Device 061: ID 0458:003a KYE Systems Corp. (Mouse Systems) NetScroll+ Mini Traveler
Bus 002 Device 060: ID 05e3:0608 Genesys Logic, Inc. USB-2.0 4-Port HUB
Bus 002 Device 023: ID 230d:0001  
Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 008: ID 413c:8160 Dell Computer Corp. 
Bus 001 Device 007: ID 413c:8162 Dell Computer Corp. 
Bus 001 Device 006: ID 413c:8161 Dell Computer Corp. 
Bus 001 Device 005: ID 0bda:0158 Realtek Semiconductor Corp. USB 2.0 multicard reader
Bus 001 Device 004: ID 0c45:641d Microdia 
Bus 001 Device 003: ID 0a5c:4500 Broadcom Corp. BCM2046B1 USB 2.0 Hub (part of BCM2046 Bluetooth)
Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

And it's showing up as a filesystem with fdisk (could you confirm that looks like what you are plugging in - a 35GB external hard drive?):

```

Disk /dev/sdd: 34.4 GB, 34359738368 bytes
64 heads, 32 sectors/track, 32768 cylinders
Units = cylinders of 2048 * 512 = 1048576 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000eec81

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1       32768    33554416   83  Linux
/dev/sdd2               1           1          15+   0  Empty
Partition 2 does not end on cylinder boundary.

```

Beyond that I don't know. I'm having a different USB problem and I thought (hoped) it might be related. Someone else might be able to help.

Have you tried following the instructions in here to mount it manually? **Make sure you also unmount it**.

[https://help.ubuntu.com/community/Mount/USB](https://help.ubuntu.com/community/Mount/USB)

thanx for your reply

its a 32 gb pen drive... and yes i tried to mount it manually but didnt work.... is my pen drive corrupted or its fine ?

---

### Post by vivek.pandey on 2011-03-21
bump?

---

### Post by daveboy23 on 2011-03-22
well, after trying a lot of things, (the day of the "post") i've decided to just uninstall and reinstall the machine (seeing how it was a brand new-install anyway).  did it and now everything is ok

---

### Post by vivek.pandey on 2011-03-22
> **daveboy23 said:**
> well, after trying a lot of things, (the day of the "post") i've decided to just uninstall and reinstall the machine (seeing how it was a brand new-install anyway).  did it and now everything is ok

do you think this will be helpful in my case too?

---

