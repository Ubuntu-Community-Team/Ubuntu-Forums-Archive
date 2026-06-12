---
title: "[SOLVED] How to list partitions and hardware?"
date: 2008-12-30
forum: New to Ubuntu
---

### Post by Aussieartist on 2008-12-30
Hi all, quick terminal question:

What's the command to show all of the drives and partitions?

And while we're at it, what's the command to show all of the specs and hardware on a laptop... One that I can copy and paste.

Thanks
Aussie
HP dv5t 1000
Ubuntu 8.10

---

### Post by Michael.Godawski on 2008-12-30
hi,

partitions:
```

sudo fdisk -l
```

hardware:
```
lspci
sudo lshw
```

---

### Post by 73ckn797 on 2008-12-30
> **Aussieartist said:**
> Hi all, quick terminal question:

What's the command to show all of the drives and partitions?

And while we're at it, what's the command to show all of the specs and hardware on a laptop... One that I can copy and paste.

Thanks
Aussie
HP dv5t 1000
Ubuntu 8.10

To view hardware:

```
sudo lshw
```

for partition info:

```
sudo fdisk -l
```

---

### Post by 73ckn797 on 2008-12-30
THERE! You get to do it twice = :lolflag:

---

### Post by Aussieartist on 2008-12-30
Thanks to you both...

Just quickly... does the sda2 below look suspicious? I'm thinking it's a remnant of the original evil Vi$ta...

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x34c662a0

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       37804   303660598+  83  Linux
/dev/sda2           37805       38913     8908042+   5  Extended
/dev/sda5           37805       38913     8908011   82  Linux swap / Solaris

Cheers :D
Aussie
HP dv5t 1000
Ubuntu 8.10

---

### Post by adult swim on 2008-12-30
sda2 is nothing to worry about.  essentially sda5, your swap partition, is nestled into sda2.  if you still feel uneasy about it do some reading on primary, extended, and logical partitions.

---

### Post by 73ckn797 on 2008-12-30
> **adult swim said:**
> sda2 is nothing to worry about.  essentially sda5, your swap partition, is nestled into sda2.  if you still feel uneasy about it do some reading on primary, extended, and logical partitions.

Adult Swimmers are the best to learn from.:D

---

### Post by Aussieartist on 2008-12-30
LOL, 
I love the Cable TV "Adult Swim"... But I only seem to find it in cheap hotels...

---

