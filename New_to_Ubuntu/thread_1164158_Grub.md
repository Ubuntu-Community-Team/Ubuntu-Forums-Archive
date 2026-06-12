---
title: "Grub"
date: 2009-05-19
forum: New to Ubuntu
---

### Post by mistypotato on 2009-05-19
I have two 320 GB hard drives currently in my computer...
One is the current working Ubuntu install and the other is a hard drive from a previous Ubuntu that I stopped using 2 months ago.

The drive in question today is the SATA 320 GB drive that I removed about 2 months ago because I bought a new drive.  So, now I'm just using it for experimenting and learning Ubuntu.

Currently it's still installed and connected but won't boot. I want to see if I can get it to boot again.

I had actually deleted all the partitions and played around with gpart and amazingly it recovered all the partitions that had been deleted with a partition editor 2 months ago so that was fun.  So, now I can access the files on the Hard disk but cannot get it to boot.

when I run **fdisk -l**

    I get this........

Cannot open /dev/sda
Cannot open /dev/sdb
Cannot open /dev/sdc

I did boot from the distro CD and ran the Grub reinstall and it seemed to work as far as Grub loaded and then an error message (error: 15 file does not exist) came up and all halted.

When I look at the hard drive there are no mount points on any partitions and if I try to add them, the installer warns that all data will be lost but I didn't check the "format" option.

Can you suggest a step forward?

Thx ):P

---

### Post by bswilson on 2009-05-19
You forgot to use sudo.

```
sudo fdisk -l
```

---

### Post by mistypotato on 2009-05-19
rofl

---

