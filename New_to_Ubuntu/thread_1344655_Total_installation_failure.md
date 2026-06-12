---
title: "Total installation failure"
date: 2009-12-03
forum: New to Ubuntu
---

### Post by Tycoon timbo on 2009-12-03
This is the 6th attempt to install ubuntu.
Each attempt has arrived at the same result; GNU GRUB option screen with a choice of Ubuntu, Ubuntu recovery ot the memory test.  Selecting either of the Ubuntu options gets the error:  no such device: 62fcf4f7-2759-4084-b8d6-1c9186d0021d

I have 2 hard drives set up on cable select.  They are both present and correct in the bios.
I have removed the motherboard battery to blank the on board memory.
I have verified the Ubuntu cd prior to installation.
The same cd was used to install on my laptop, which is working fine.
Could the problem be overwriting Ububntu with Ubuntu?
Each installation tells me that Ubuntu is already installed on the hard drive.

If I wasn't already bald, I would be pulling my hair out.

Can you help?  ](*,)

---

### Post by ukripper on 2009-12-03
When you installed ubuntu did you completely wipe out partitions? boot into ubuntu live cd and post output of this:
```
sudo fdisk -l
```

```
sudo blkid
```

---

### Post by Tycoon timbo on 2009-12-03
Hi ukripper, the saga continues.

sudo fdisk  -1  

Disk /dev/sda: 80.1 GB, 80060424192 bytes
255 heads, 63 sectors/track, 9733 cylinders
Units = cylinders of 1065 * 512 = 8225260 bytes
Disk identifier: 0xa41e07cf

  Device Boot     Start     End     Blocks       Id   System
/dev/sda1  *            1   9331  74951226    83   Linux
/dev/sda2           9332  9733    3229065     5    Extended
/dev/sda5           9332  9733    3229033+  82   Linux swap / solaris

Disk /dev/sdb: 40.0 GB,  40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 1605 * 512 = 8225280 bytes
Disk identifier: 0x75b1b6ea

/dev/sdb1   *     1       4865    39078081    7      HPFS/NTFS



sudo blkid

/dev/loop0: TYPE="squashfs"
/dev/sda1: UUID="62fcf4f7-2759-4048-b8d6-1c9186d0021d" TYPE="ext4"
/dev/sda5: UUiD="da7b9339-alf3-4749-80b9-a3bb2e53c871" TYPE="swap"
/dev/sdb1: UUID"40B8D90DB8901F8" TYPE="ntfs"


looks good?

---

### Post by ed-koala on 2009-12-03
I think you have to change that UUID number to a /sda or something similar in GRUB, gonna research and get back to you (unless someone beats me to it).  I'm sure I remember reading about this exact issue here somewhere.

---

### Post by ukripper on 2009-12-03
> **Tycoon timbo said:**
> 

yeh looks good. Can you tell me what error you are getting on startup with error number? example Error 21:

While in ubuntu live cd, can you click on the ubuntu inatlled drive showing up in your "places" and make sure it gets mounted by double clicking and open up in a new window.

and then run this command:
```
df -h 
```

i want to make sure it gets mounted so we can further get details from fstab and grub

Are you using ubuntu 9.10 or 9.04?

---

### Post by cartisdm on 2009-12-03
Do you have a copy of GParted? If so, try loading that up and completely wiping both drives and delete all the partitions (GRUB, MBR, ext3, etc.).  Now, with the drives completely empty you should be able to install as usual.  Post back with results

---

### Post by ed-koala on 2009-12-03
Ok, a quick and easy check to see if Grub config is to blame. Hold down shift so you get the Grub menu upon boot.  There should be an option to edit boot parameters or commands, or something similar.

You'll want to change root=UUID=lalalalala to root=/dev/sda1

Hit b to boot and if you boot up, you know all you need to do is edit your grug config to change that uuid  to /dev/sda1.  Plenty of posts here on editing grub2.

---

### Post by Tycoon timbo on 2009-12-03
df -h

filesystem         size    used   avail   use%  mounted on
aufs                  754m   98m   657m   13        /
udev                 754m  416k   754m      1       /dev
/dev/sr0            690m  690m     0     100       /cdrom
/dev/loop0         668m  668m     0     100       /rofs
none                 754m  244k  754m      1       /dev/shm
tmpfs                754m    12k  754m      1       /tmp
none                 754m    88k  754m      1       /var/run
none                 754m      0    754m      0      /var/lock
none                 754m      0    754         0      /lib/init/rws
/dev/sda1           71g     2.2g   65g        4      /media/62fcf4f7-2759-4048-b8d6-1c198
6d0021d

I am using the latest version of Ububntu  9.10

---

### Post by ukripper on 2009-12-03
while in live cd, after mounting again (if not mounted already as explained earlier), in terminal type this :
```
gedit /media/62fcf4f7-2759-4048-b8d6-1c198
6d0021d/etc/fstab
```

and 

```
gedit /media/62fcf4f7-2759-4048-b8d6-1c198
6d0021d/etc/grub.d/40_custom
```

post output here.

---

### Post by Tycoon timbo on 2009-12-03
using gparted, I have wiped all partitions from both drives.  Am now re-installing Ubutntu 9.10.

---

### Post by ukripper on 2009-12-03
> **Tycoon timbo said:**
> using gparted, I have wiped all partitions from both drives.  Am now re-installing Ubutntu 9.10.

i guess that is another way to go about! Hope it works out ok this time.

---

### Post by Tycoon timbo on 2009-12-03
This time setup found no operating system on the drive.  Hopefully it will work this time.

---

### Post by Tycoon timbo on 2009-12-03
No joy there, back in exactly the same place as before.

Fail to understand why it works on the laptop and not on the pc.

Feeling I need to shoot the damn machine, leave all technology behind and become a monk.

---

### Post by ukripper on 2009-12-03
ok let's calm down and see where the problem is. 
Checklist:
[LIST=1]

[*]Check in BIOS master and slave are there?
[*]Post any error you are getting?
[*]Burn another cd and install it from there.
[*]Use smartctl to check for bad blocks as i explained yesterday in PMs?
[/LIST]

---

### Post by b0b138 on 2009-12-03
Try installing grub manually. Go here [https://wiki.ubuntu.com/Grub2](https://wiki.ubuntu.com/Grub2) and about 3/4 the way down is the section recover grub 2 via livecd

---

### Post by Tycoon timbo on 2009-12-03
Okay.  Both drives present and correct in BIOS.
I checked the cd for errors prior to installation, one of the options on the installation menu.

error: no such device: da8c6409-392e-4b5a-9983-774d9c3730aa

is the error code I get from the choosing ubuntu from the grub menu.

I will try downloading another cd tomorrow, I am going out tonight.

---

