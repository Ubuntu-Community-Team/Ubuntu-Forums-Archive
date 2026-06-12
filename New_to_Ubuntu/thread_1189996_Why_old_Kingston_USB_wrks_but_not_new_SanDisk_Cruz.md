---
title: "Why old Kingston USB wrks but not new SanDisk Cruzer?"
date: 2009-06-17
forum: New to Ubuntu
---

### Post by Goover on 2009-06-17
Hi,

I have been installing Ubuntu Desktop for two days not, getting it all in place before I make an image... (So, it is quite in mint condition, only automated some updates).

However, I downloaded a lot of things, via another computer at a place with high speed Internet connection and put all that to 4GB SanDisk Cruzer U3.

I've been trying to find out what is going wrong, and googled a lot, but nothing useful...

Then I took an old Kingston 1GB USB, and in a second the content was displayed!

From what I can see the Kingston is FAT, but the SanDisk?

I did a: sudo fdisk -l, for the Kingston drive and the part for the Kingston drive looks like this:
 > Disk /dev/sdb: 999 MB, 999555072 bytes
31 heads, 62 sectors/track, 1015 cylinders
Units = cylinders of 1922 * 512 = 984064 bytes
Disk identifier: 0x6f20736b

This doesn't look like a partition table
Probably you selected the wrong device.

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   ?      404858      998775   570754815+  72  Unknown
Partition 1 has different physical/logical beginnings (non-Linux?):
     phys=(357, 116, 40) logical=(404857, 12, 11)
Partition 1 has different physical/logical endings:
     phys=(357, 32, 45) logical=(998774, 30, 51)
Partition 1 does not end on cylinder boundary.
/dev/sdb2   ?       87768     1095067   968014120   65  Novell Netware 386
Partition 2 has different physical/logical beginnings (non-Linux?):
     phys=(288, 115, 43) logical=(87767, 21, 47)
Partition 2 has different physical/logical endings:
     phys=(367, 114, 50) logical=(1095066, 14, 42)
Partition 2 does not end on cylinder boundary.
/dev/sdb3   ?      972884     1980182   968014096   79  Unknown
Partition 3 has different physical/logical beginnings (non-Linux?):
     phys=(366, 32, 33) logical=(972883, 5, 30)
Partition 3 has different physical/logical endings:
     phys=(357, 32, 43) logical=(1980181, 28, 39)
Partition 3 does not end on cylinder boundary.
/dev/sdb4   ?           1     1892418  1818613248    d  Unknown
Partition 4 has different physical/logical beginnings (non-Linux?):
     phys=(372, 97, 50) logical=(0, 0, 1)
Partition 4 has different physical/logical endings:
     phys=(0, 10, 0) logical=(1892417, 16, 30)
Partition 4 does not end on cylinder boundary.

Partition table entries are not in disk order
So, even that is not very encouraging in respect to how Ubuntu ought to handle USBs?

What to do with the SanDisk Cruzer?

Cheers,

Goover

---

### Post by halitech on 2009-06-17
sounds to me like the new drive has U3 enabled on it and thats what is causing the issues for you. There is an uninstaller here:

[http://www.pendrivelinux.com/u3-uninstaller-for-usb-flash-drive/](http://www.pendrivelinux.com/u3-uninstaller-for-usb-flash-drive/)

---

### Post by niteshifter on 2009-06-17
Hi,
The generic U3 removal tool won't work, you need the SanDisk one. Direct link is [here]("http://www.sandisk.com/Assets/u3/launchpadremoval.exe") (sandisk.com, Windows executable file).
Yep, gotta use windows for this, there is no Linux version.

---

### Post by Goover on 2009-06-18
Thanks, for confirming this U3 problem. Went to SanDisk and saw that they had a U3 reinstaller, so I went to a Windows computer:

1. backed up the SanDisk Cruzer
2. formated SanDisk Cruzer with FAT32 (twice to be certain)
3. moved the backuped files to the Cruzer
4. Moved to Ubuntu computer and the Cruzer was acknowledged.

So, I could install the apps I like...

Sadly, I think this is a flaw in Ubuntu - I mean: Even if it cannot recognize the U3 system, it ought to be able to see that there was something going on on the USB port - and then tell the user it didn't know what to do...

Cheers,

Goover

---

### Post by MrWES on 2009-06-18
> **Goover said:**
> Thanks, for confirming this U3 problem. Went to SanDisk and saw that they had a U3 reinstaller, so I went to a Windows computer:

1. backed up the SanDisk Cruzer
2. formated SanDisk Cruzer with FAT32 (twice to be certain)
3. moved the backuped files to the Cruzer
4. Moved to Ubuntu computer and the Cruzer was acknowledged.

So, I could install the apps I like...

Sadly, I think this is a flaw in Ubuntu - I mean: Even if it cannot recognize the U3 system, it ought to be able to see that there was something going on on the USB port - and then tell the user it didn't know what to do...

Cheers,

Goover

When you removed the drive from your Windows machine, did you just pull it out, or did you use the 'safely remove hardware' icon in the system tray? If not, try it and then try it again in Ubuntu.

Bill

Edit: Might be a bug: [https://bugs.launchpad.net/ubuntu/+source/util-linux/+bug/284171]("https://bugs.launchpad.net/ubuntu/+source/util-linux/+bug/284171")

---

### Post by Knacker_Ned on 2009-06-18
MrWES, correct me if I'm wrong, but I think Goover is saying that all is fine now with the SanDisk Cruzer. He's saying, however, that there's a flaw in Ubuntu which stops it from reporting the problem.

---

