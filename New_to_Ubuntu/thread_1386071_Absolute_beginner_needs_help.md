---
title: "Absolute beginner needs help"
date: 2010-01-20
forum: New to Ubuntu
---

### Post by Ron Burgundy on 2010-01-20
Hi,

Im completely new to the world of Linux and programming. I am trying to get onto my other hard drive which did contain Windows until I got a virus on it and now it refuses to repair or allow me any access onto the drive. I installed Linux on a second drive and am trying to save anything I can from drive 1 (ex-windows).
I got as far as trying to mount the drive, when I get the following error:

"Error mounting: mount exited with exit code 18: Failed to open hiberfil.sys data attribute: No such file or directory
Failed to mount '/dev/sdb1': No such file or directory"

I have installed Linux headers and ntfs-3g and tried to open it using Wine. 
Any help would be appreciated

Thanks

---

### Post by wojox on 2010-01-20
Try

```
sudo ntfs-3g /dev/sdb1 /mnt/location -o remove_hiberfile
```

---

### Post by nothingspecial on 2010-01-20
What command are you using to mount the drive?

Post the output of ```
sudo fdisk -l
```

---

### Post by Ron Burgundy on 2010-01-20
@ wojox: that gives me

"The disk contains an unclean file system (0, 1).
The file system wasn't safely closed on Windows. Fixing.
Failed to open hiberfil.sys data attribute: No such file or directory"

---

### Post by Ron Burgundy on 2010-01-20
and @nothingspecial:
Disk /dev/sda: 82.0 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd71bd71b

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9553    76734441   83  Linux
/dev/sda2            9554        9964     3301357+   5  Extended
/dev/sda5            9554        9964     3301326   82  Linux swap / Solaris

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x973a973a

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        9728    78140128+   7  HPFS/NTFS
/dev/sdb2            9729       19457    78148192+   f  W95 Ext'd (LBA)
/dev/sdb5            9729       19457    78148161    7  HPFS/NTFS

---

### Post by nothingspecial on 2010-01-20
See what errors this gives

   ```
 ntfs-3g.probe --readwrite /dev/sdb1
```

---

### Post by synapsys on 2010-01-20
```
sudo mount -t ntfs-3g /dev/sdb1 /mnt/location -o force
```

---

### Post by Ron Burgundy on 2010-01-20
@ nothing special: 
I just get:
"Error opening '/dev/sdb1': Permission denied"

@ synapsis:

"Failed to open hiberfil.sys data attribute: No such file or directory
Failed to mount '/dev/sdb1': No such file or directory"

Thanks to you all for responding. I was lost as soon as it didn't mount when I clicked it on the GUI

---

### Post by nothingspecial on 2010-01-20
sorry I forgot the sudo

```
sudo  ntfs-3g.probe --readwrite /dev/sdb1
```

---

### Post by wojox on 2010-01-20
> **synapsys said:**
> ```
sudo mount -t ntfs-3g /dev/sdb1 /mnt/location -o force
```

That was going to be my next suggestion, when in doubt Force it out.

---

### Post by Ron Burgundy on 2010-01-20
@ nothing special:
It doesn't seem to help any with the sudo
"Failed to open hiberfil.sys data attribute: No such file or directory"

---

### Post by Ron Burgundy on 2010-01-20
I'm officially giving up on this and formatting the drive.
Thanks for the help though Programmy people!

---

