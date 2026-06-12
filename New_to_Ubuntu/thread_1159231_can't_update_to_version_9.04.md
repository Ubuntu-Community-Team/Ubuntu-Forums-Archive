---
title: "can't update to version 9.04"
date: 2009-05-14
forum: New to Ubuntu
---

### Post by SKOREAPV83 on 2009-05-14
My friend has a laptop that had an older version (I forget which) of Ubuntu. It refuses to boot from the CD-ROM drive. I don't know how to make a boot disk to wipe the hard drive and make it boot from the CD-ROM drive. HELP!

---

### Post by whoop on 2009-05-14
To find out which version of ubuntu he is running ask him to type this in a terminal:
```

cat /etc/issue

```
The ubuntu ISO you can download from [http://www.ubuntu.com](http://www.ubuntu.com) will be bootable when you burn it to a cd.

---

### Post by kanikilu on 2009-05-14
Is the BIOS set to boot from CD first? Also, most computers have a key (usually ESC, F10, F12, or something like that) to choose a temporary boot device.

Will that computer boot from other CD's? If so, something may be wrong with that one, so just try downloading the ISO again and making a new 9.04 CD.

If other CD's don't boot either, then you may need to try an external USB CD drive (if available) or use something like Unetbootin to make a bootable flash drive from the ISO file.

---

### Post by SKOREAPV83 on 2009-05-14
Umm...the laptop won't boot at all unless I have the MS-DOS startup disk in the floppy drive. I just went to a Windows XP computer and used the "Create an MS-DOS startup disk" option under the floppy disk formatter. When I boot the laptop from that disk, it gives me an A:\ prompt. What do I type there to make it wipe the hard drive and boot from CD? It used to boot from CD and I don't know why it suddenly won't. I tried to load Ubuntu 9.04 on it 4 times and it kept telling me that selecting and installing hardware failed.

---

