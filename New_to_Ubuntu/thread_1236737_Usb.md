---
title: "Usb"
date: 2009-08-10
forum: New to Ubuntu
---

### Post by GodlySoup on 2009-08-10
How do I get anything I plug into my usb to work? I've heard of "mounting" things, but I don't know how to do that. I'm sorry for asking so many questions, but these forums are quite hard to search through. The top choices are always the "bump" thread or something else irrelevant.

---

### Post by MaindotC on 2009-08-10
I'm assuming you are talking about a USB storage device.  When you plug it in, wait a few seconds and then type:
```

sudo fdisk -l

```

Post the output here using code tags.

---

### Post by GodlySoup on 2009-08-10
```
dustin@Osiris:~$ sudo fdisk -l
[sudo] password for dustin: 

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000acc61

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       37460   300897418+  83  Linux
/dev/sda2           37461       38913    11671222+   5  Extended
/dev/sda5           37461       38913    11671191   82  Linux swap / Solaris

Disk /dev/sdb: 4016 MB, 4016045568 bytes
255 heads, 63 sectors/track, 488 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1         488     3919841    b  W95 FAT32
dustin@Osiris:~$ 






```

Well, not just storage devices. Like Mp3 players and my phone.

---

### Post by Schendje on 2009-08-10
Most of them should work automatically. I'd say try them and come back to us if it somehow goes wrong. :)

---

### Post by MaindotC on 2009-08-10
As you may be able to tell by the size of this disk, 320GB, this is your hard drive and it is called /dev/sda:
> **GodlySoup said:**
> ```

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000acc61

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       37460   300897418+  83  Linux
/dev/sda2           37461       38913    11671222+   5  Extended
/dev/sda5           37461       38913    11671191   82  Linux swap / Solaris

```
Within /dev/sda, there are partitions, 3 of them, and they are denoted as /dev/sda1, /dev/sda2, and /dev/sda5.  And here is the usb stick - looks like a 4GB:
```

Disk /dev/sdb: 4016 MB, 4016045568 bytes
255 heads, 63 sectors/track, 488 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1         488     3919841    b  W95 FAT32

```
The usb drive should appear in /media - usually it'll be /media/disk but look around in /media.  Typically when you insert the usb drive there is an icon that appears on your desktop that denotes its appearance.  You can also go go Places -> Computer and there should be an icon that says something like "4.00 GB drive".

As for your phone or mp3 player, it depends.  Is /dev/sdb a usb drive or is it your mp3 player?

---

### Post by kansasnoob on 2009-08-10
You don't mention what device you're trying to mount but I've found that adding 'pmount' from Synaptic makes all of my flash drives, external drives, and many other things mount automatically.

If an external (or flash) drive is formatted as NTFS I also like to add 'ntfsprogs".

Both available in Synaptic or can be installed from terminal:

```
sudo apt-get install pmount ntfsprogs
```

for both, or simply choose only pmount if that's what's needed.

**Warning: ntfsprogs is powerful which means you can mount and DESTROY anything in Windows using it if you're reckless!**

[http://www.linux-ntfs.org/doku.php](http://www.linux-ntfs.org/doku.php)

---

