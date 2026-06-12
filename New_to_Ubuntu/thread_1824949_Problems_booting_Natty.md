---
title: "Problems booting Natty"
date: 2011-08-14
forum: New to Ubuntu
---

### Post by Johnnyreb65401 on 2011-08-14
I have a Toshiba Satellite C655D. It is set for dual boot. Windoze 7 on one side and Natty on the other. Unfortunately I can not boot directly in to Natty. I have to start windoze. Once in the log in screen I then have to restart. Then I can log in to Natty. If I try to go log in to Natty first it locks up.

Any suggestions?

---

### Post by elgordodude on 2011-08-14
Did you install natty with wubi or a live cd?

---

### Post by Johnnyreb65401 on 2011-08-14
D/L directly from ubuntu then made live thumbdrive to make install on computer.

---

### Post by elgordodude on 2011-08-14
> If I try to go log in to Natty first it locks up.

Hold on, I think I read this wrong, at first it looked like the computer, just booted into windows with a power on, but you could then hit restart and get to ubuntu. This line makes it look like ubuntu is indeed an option at power on, it just consistently fails.

Regardless we should probably start with the disk, what does

```
sudo fdisk -l
```

give you? And anything you note about the way it starts up.

---

### Post by Johnnyreb65401 on 2011-08-14
When I boot, I get the normal dual boot menu (Linux or windows). If I boot to linux without first going to the windows login screen then restart and go back to the dual boot menu it will freeze at the login screen for natty. I can see my user name but the mouse and key board is unresponsive. If by chance I get logged in, it will lock up before linux fully loads.

sudo fdisk -l gives me the following

> Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x1be57ecb

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         192     1536000   27  Unknown
Partition 1 does not end on cylinder boundary.
/dev/sda2             192       15484   122836965    7  HPFS/NTFS
/dev/sda3           29029       30402    11028480   17  Hidden HPFS/NTFS
/dev/sda4           15484       29029   108795905    5  Extended
/dev/sda5           15484       28689   106068992   83  Linux
/dev/sda6           28689       29029     2725888   82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdb: 32.0 GB, 32015679488 bytes
64 heads, 32 sectors/track, 30532 cylinders
Units = cylinders of 2048 * 512 = 1048576 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0009372a

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       30532    31264752    c  W95 FAT32 (LBA)


---

### Post by elgordodude on 2011-08-14
Good news is that it doesn't look like the drive, it seems most of the hang at boot errors are caused by video drivers. When you can get into natty have you tried installing the ATI drivers for your card?

Here's the wiki [https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

Secondly, you could try "classic" mode, that seems to help some people.

Finally, if it's still a fresh installation because of these lockups you can try a reinstall or install 10.04 or 10.10

---

