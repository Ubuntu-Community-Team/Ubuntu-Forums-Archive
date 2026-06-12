---
title: "Server 11.04 additional HDD"
date: 2011-09-01
forum: New to Ubuntu
---

### Post by Tappers1979 on 2011-09-01
I have just installed Ubuntu Server 11.04 on a PATA hard drive and all went successful. It was on /dev/sda.

I then added a SATA drive and thought it would be /dev/sdb but it changed the PATA to sdb and the SATA to sda should I be worried?

I come from a Windows background where is C: changed to D: the system would be dead, hope this is not a silly question.

Many thanks

---

### Post by cariboo on 2011-09-01
Set your drive order in the bios first, then use UUID to mount the drives instead of the device name for example:

> # /dev/sdb1	/media/music	xfs	defaults	0	0
UUID=2b9e52c6-de78-4669-bb11-ec45dec29317	/media/music	xfs	defaults

in the above line from /etc/fstab, I created a comment showing the line needed using the device name to mount the drive, then the actual line used, using UUID. IF you don't know what the UUIDs are, use the following command:

```
sudo blkid
```

the result should be similar to this:

> cariboo@willy:~$ sudo blkid
[sudo] password for cariboo: 
/dev/sda1: UUID="6ee983d6-abaf-40b4-8327-e260f3067e15" TYPE="ext4" 
/dev/sda2: UUID="e61fc65b-8fa2-4e97-b56c-34e8dc44198b" TYPE="swap" 
/dev/sda3: UUID="5a1bbaae-0ea2-440c-bd7a-182af1b5c9ad" TYPE="ext4" 
/dev/sdb1: UUID="2b9e52c6-de78-4669-bb11-ec45dec29317" TYPE="xfs" 
/dev/sdc1: UUID="b1debca6-d141-4d4a-b687-d410a2670cf7" TYPE="xfs" 
/dev/sde1: UUID="6f1f0afb-8cfe-4d7b-9ba9-15d42c37c4ab" TYPE="xfs" 
/dev/sdd1: UUID="bc75bb38-6da9-4fb4-8061-1809479ce788" TYPE="xfs" 
/dev/sdf1: UUID="ff6faf9e-8cbd-46b6-8cc0-734add7e8a9d" TYPE="xfs" 
/dev/sdg1: UUID="fcb2b52c-d820-4b7f-98e9-e74f8ca9f89d" TYPE="xfs" 
/dev/sdh1: UUID="1fe87acc-57d8-4487-b919-ab39e2a673fd" TYPE="xfs"

The above is from my server that has 2 PATA drives and 6 SATA drives installed.

---

### Post by Tappers1979 on 2011-09-03
thanks for the reply Cariboo907.
 
The thing that I didn't understand was that the server still booted! Where can I find info on the /dev/sd? bit to understand more about it.:confused:
 
I checked the BIOS and boot order is IDE/PATA before SATA but the SATA still comes up as SDA1:confused:
 
do I just replace the /dev/sda1 with the uid as you have below?
 
I deleted the DEV/SDA1 partition from the SATA drive and now get some weird messages on bootup but eventurally it did boot to login so will try and copy down the messages and see if anyone can assist.
 
thanks again

---

