---
title: "unable to mount 2nd Hard drive"
date: 2009-05-10
forum: New to Ubuntu
---

### Post by rhythmiccycle on 2009-05-10
when I try to open my second hard drive (that works in windows)
it says

"unable to mount device".

below are some detail about my situation:

I was having some problems with my computer. 
I removed all the partitions and installed windows.
I then installed ubuntu 9.04 from within windows.

when ubuntu is loading.
this shows up

Buffer I/O error of device sda1 Logical block (then some numbers)

and a bunch of other words too. they pass threw my screen, in cycles with the numbers changing, but the same I/O error message. it goes on for about 10 minutes, then ubuntu loads.

it seems to be working well, I'm using it now. 
but there is no sound(i checked to volume).
and  when I try to open my second hard drive (that works in windows)
it says

unable to mount device.

are all these problems related or are they 3 separate problems?
what should I do to get my sound and second hard drive to work?

---

### Post by belikralj on 2009-05-11
What else does it say besides "unable to mount device"? Are you mounting it with sudo or just normally and if it is without sudo do you have permissions to mount it? Also tell us a little more about the hard disk. When you connect it show us the result of the command > ls /dev/?d*

---

### Post by rhythmiccycle on 2009-05-11
when i type "ls /dev/?d* " is says:

```

/dev/cdrom  /dev/cdrw  /dev/sda  /dev/sdb  /dev/sdb1  /dev/sdc  /dev/sdd

/dev/fd:
0  1  2  3


```


> Are you mounting it with sudo or just normally and if it is without sudo do you have permissions to mount it?

i'm just opening the "computer" from the system menu, and I see the drive called "mass storage Drive" I double click on the icon, and it says 

Unable to mount location
Can't mount file


 > Also tell us a little more about the hard disk.

its a sata 250 gig. It seems to be working when i run windows.

also, here's a part of the error message when its loading:

> 
[  519.038185] sd 0:0:0:0: [sda] 488397168 512-byte hardware sectors: (250 GB/232 GiB)
[  519.038218] sd 0:0:0:0: [sda] Write Protect is off
[  519.038224] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[  519.038277] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[  522.218534] ata1.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
[  522.218540] ata1.00: irq_stat 0x40000008
[  522.218548] ata1.00: cmd 60/08:00:bf:00:00/00:00:00:00:00/40 tag 0 ncq 4096 in
[  522.218549]          res 51/40:08:bf:00:00/00:00:00:00:00/00 Emask 0x409 (media error) <F>
[  522.218553] ata1.00: status: { DRDY ERR }
[  522.218556] ata1.00: error: { UNC }
[  522.221015] ata1.00: configured for UDMA/133
[  522.221036] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[  522.221043] sd 0:0:0:0: [sda] Sense Key : Medium Error [current] [descriptor]
[  522.221052] Descriptor sense data with sense descriptors (in hex):
[  522.221056]         72 03 11 04 00 00 00 0c 00 0a 80 00 00 00 00 00 
[  522.221075]         00 00 00 bf 
[  522.221083] sd 0:0:0:0: [sda] Add. Sense: Unrecovered read error - auto reallocate failed
[  522.221093] end_request: I/O error, dev sda, sector 191
[  522.221100] Buffer I/O error on device sda1, logical block 128
[  522.221106] Buffer I/O error on device sda1, logical block 129
[  522.221109] Buffer I/O error on device sda1, logical block 130
[  522.221113] Buffer I/O error on device sda1, logical block 131
[  522.221116] Buffer I/O error on device sda1, logical block 132
[  522.221119] Buffer I/O error on device sda1, logical block 133
[  522.221123] Buffer I/O error on device sda1, logical block 134
[  522.221126] Buffer I/O error on device sda1, logical block 135
[  522.221144] ata1: EH complete


---

### Post by sahabcse on 2009-05-11
For mounting the NTFS and Fat32 partition pls follow below url

[http://sahabm.blogspot.com/2009/03/mount-ntfs-fat32-windows-drive-in.html](http://sahabm.blogspot.com/2009/03/mount-ntfs-fat32-windows-drive-in.html)

---

### Post by rhythmiccycle on 2009-05-11
when i type
```
mount -t ntfs-3g /dev/sda1 /media/windisk -o force
```

it says
```
Failed to access volume '/dev/sda1': No such file or directory
Please type '/sbin/mount.ntfs-3g --help' for more information.

```

---

