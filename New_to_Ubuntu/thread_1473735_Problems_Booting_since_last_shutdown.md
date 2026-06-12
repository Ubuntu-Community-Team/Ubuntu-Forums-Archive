---
title: "Problems Booting since last shutdown"
date: 2010-05-05
forum: New to Ubuntu
---

### Post by amphibian on 2010-05-05
Running Karma, been using without problems. Shutdown systems last night by means of proper shutdown, came in this morning and see that it hangs with black screen, thought it had loaded and went to screen saver, pressed enter key and see the following message:


"Gave up waiting for root device" and then of course it list several reasn possible this is happening,

The " Alert! /dev/disk/by-uuid/b4563717-c069-4743-9da8-c59b81f8a469 does not exsist. Dropping to a shell!"

Then BusyBox comes up with " (initramfs) "

I am assuming it did not find the root file or fstab/mtab information for booting.

I have automatic updates selected, assuming that it did an update and something went wrong? Need to know how best to correct this.

I see a lot of post pertaining to BusyBox and initramffs for dual boot systems, mine is not the case. Running AMD64 machine with just Ubuntu loaded. I have tried to boot from cd then attempt to mount sda1, but it tells me that no such dev found in Fsatb/mtab, any suggestion would be very helpful.


Thanks
Amphibian

---

### Post by Troublegum on 2010-05-05
If I were you, I would try the following things:


[LIST]
[*]When Ubuntu drops to a root shell, type
```
blkid
```
This should give you a list of all detected hard drives with their labels and their UUID. On my PC, it looks like this:
```
nam@pc-andrenam:~$ sudo blkid
/dev/sdb1: LABEL="System-reserviert" UUID="3636217936213B6F" TYPE="ntfs" 
/dev/sdb2: LABEL="win7" UUID="AE1C253D1C2501C7" TYPE="ntfs" 
/dev/sdb3: UUID="c6ed5b34-be3f-4e77-baef-a897c1f9080d" TYPE="ext4" 
/dev/sdb5: LABEL="images" UUID="245C51FE494FB104" TYPE="ntfs" 
/dev/sdb6: UUID="04596dcb-e5f8-4674-9d7e-b296ff1a1f2d" TYPE="swap" 
/dev/sdb7: UUID="a198d737-1cab-4728-a344-a5db4b4c1b5c" TYPE="ext4" 
/dev/sda5: LABEL="data" UUID="BED0FBF5D0FBB22F" TYPE="ntfs" 
/dev/sda6: LABEL="dev" UUID="32D419CCD4199369" TYPE="ntfs" 

```
[*]This way, you can identify which partition is meant with UUID b4563717-c069-4743-9da8-c59b81f8a469 (the one that could not be mounted).
[*]If you find the partition, you could try to mount it manually with
```
mount -t type /dev/sdXY /mountpoint
```
[*]If that fails, try to mount your partitions using a Live CD. You dont have to use /etc/fstab (you cant use that any using the live cd), but by double-clicking on your drives in nautilus.
[*]If you can mount your Ubuntu partition, compare the UUID given by "sudo blkid" with the ones in your /etc/fstab file (the file on your ubuntu partition). The UUIDs should be the same. If they differ, you could replace the UUID in your /etc/fstab file with the correct one. Or you could replace the whole UUID=.... part in your /etc/fstab with the device path (/dev/sdXY).
[/LIST]

---

