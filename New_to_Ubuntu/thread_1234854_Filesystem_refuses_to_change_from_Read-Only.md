---
title: "Filesystem refuses to change from Read-Only"
date: 2009-08-08
forum: New to Ubuntu
---

### Post by rednano12 on 2009-08-08
Hello all,

I have a MicroSD card and a USB adapter for said card. I have successfully gotten it to be recognized in Ubuntu, but recently, it suddenly refused to be written to because it was read-only. 

Result of fdisk -l

```
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xfac6fac6

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       54426   437176813+   7  HPFS/NTFS
/dev/sda2           54427       54550      996030   82  Linux swap / Solaris
/dev/sda3           54551       60801    50211157+  83  Linux

Disk /dev/sdb: 2002 MB, 2002780160 bytes
11 heads, 10 sectors/track, 35560 cylinders
Units = cylinders of 110 * 512 = 56320 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               2       35561     1955775+   b  W95 FAT32

```
I unmounted and remounted using these commands:

```

sudo umount /media/SD
sudo mount -t vfat /dev/sdb1 /media/SD
```

But nothing. I then tried changing the permissions with chmod:
```

sudo chmod 775 /dev/sdb1
```

But nothing changed. I then tried this command:

```
sudo chmod 775 /media/SD
```

And got the error chmod: changing permissions of `/media/SD': Read-only file system

Please help!

---

### Post by Liolikas on 2009-08-08
Force rw:
sudo mount -t vfat /dev/sdb1 /media/SD -o rw
Try to search for magic button on device.

---

### Post by rednano12 on 2009-08-08
Thank you for responding, but that command still did not allow me to copy my file over to the disk.

And what is the magic button?

---

### Post by Liolikas on 2009-08-08
Small and hidden.

---

### Post by mcduck on 2009-08-08
You can't use commands like chown or chmod with wndows file systems, they don't support Unix/Linux-style of file ownerships and permissions. Permissions for these filesystems are set at the time you mount the drive.

Does your card have lock switch? Make sure it's not locked.

---

### Post by rednano12 on 2009-08-08
Erm... I have a microSD card. There is no lock switch.

EDIT: Just tried unmounting the drive from the desktop and got this error:
Error org.freedesktop.DBus.Error.UnkownMethod.

If I hit the details button:
Method "Unmount" with signature "as" on interface "org.freedesktop.HAL.Device.Volume" does not exist.

---

### Post by Liolikas on 2009-08-08
Sounds like bug then. Report it.

---

### Post by rednano12 on 2009-08-08
I don't think that it's a bug as I was able to R/W/X from it before. The last time, to get it working, I had to reboot with it plugged in. I did that again, but still... AGH!

---

### Post by Zer0Nin3r on 2009-08-08
This happens to me every now and then when using my flash drive.  The only thing I was able to do was backup the drive & reformat then recopy everything back onto it.  Annoying.

Let me know if you find a solution.

---

