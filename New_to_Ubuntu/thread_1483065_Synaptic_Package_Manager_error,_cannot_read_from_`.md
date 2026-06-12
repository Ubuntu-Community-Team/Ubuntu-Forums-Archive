---
title: "Synaptic Package Manager error, cannot read from `/dev/sdb'"
date: 2010-05-14
forum: New to Ubuntu
---

### Post by thewhiteraven on 2010-05-14
I have the same problem with Synaptic and Update manager. When I do dpkg --configure -a, this is what I get:

```
jan@jan-laptop:~$ sudo dpkg --configure -a
Setting up linux-image-2.6.31-21-generic (2.6.31-21.59) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.31-21-generic
Running postinst hook script /usr/sbin/update-grub.
error: cannot read from `/dev/sdb'

```

Please help!

---

### Post by philinux on 2010-05-14
Post moved to own thread.

---

### Post by drs305 on 2010-05-14
thewhiteraven,

Grub2 is having a problem updating. Does your install include OS's on different partitions or G2 and your OS on different partitions? If not, it could be as simple as looking at (and removing references to sdb) from /boot/grub/device.map.

You might also check the error messages by running update-grub by itself:
```
sudo update-grub
```

Otherwise it may be easiest to just take a look at your system by using meierfra's bootinfo script:
[http://bootinfoscript.sourceforge.net/]("http://bootinfoscript.sourceforge.net/")

---

### Post by fher98 on 2010-10-19
Same problem here when grub tries to update... In /boot/grub/device.map I only have

(hd0)   /dev/disk/by-id/ata-SAMSUNG_HD753LJ_S13UJ90S510383
(hd1)   /dev/disk/by-id/ata-SAMSUNG_HD753LJ_S13UJ90S510378

---

### Post by drs305 on 2010-10-19
> **fher98 said:**
> Same problem here when grub tries to update... In /boot/grub/device.map I only have

(hd0)   /dev/disk/by-id/ata-SAMSUNG_HD753LJ_S13UJ90S510383
(hd1)   /dev/disk/by-id/ata-SAMSUNG_HD753LJ_S13UJ90S510378

Try refreshing the device map with this command:
```
sudo grub-mkdevicemap
```

You normally don't even need a device.map file, which is stored in /boot/grub.

---

### Post by fher98 on 2010-10-21
Thanks for your reply, I executed grub-mkdevicemap, then

:~# update-grub
Generating grub.cfg ...
...
Found initrd image: /boot/initrd.img-2.6.26-2-amd64
  /dev/sdb: read failed after 0 of 4096 at 0: Input/output error
  /dev/sdb1: read failed after 0 of 2048 at 0: Input/output error
  /dev/sdb2: read failed after 0 of 2048 at 0: Input/output error
  /dev/sdb3: read failed after 0 of 4096 at 0: Input/output error
  No volume groups found

---

### Post by drs305 on 2010-10-21
> **fher98 said:**
> Thanks for your reply, I executed grub-mkdevicemap, then

:~# update-grub
Generating grub.cfg ...
...
Found initrd image: /boot/initrd.img-2.6.26-2-amd64
  /dev/sdb: read failed after 0 of 4096 at 0: Input/output error
  /dev/sdb1: read failed after 0 of 2048 at 0: Input/output error
  /dev/sdb2: read failed after 0 of 2048 at 0: Input/output error
  /dev/sdb3: read failed after 0 of 4096 at 0: Input/output error
  No volume groups found

fher98,

Have you recently moved drives around, added drives, etc? The only references to this type of issue I could readily find recommended refreshing the initrd image.

```
man mkinitramfs
```

---

