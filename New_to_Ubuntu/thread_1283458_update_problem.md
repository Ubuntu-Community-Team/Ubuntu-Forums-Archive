---
title: "update problem"
date: 2009-10-05
forum: New to Ubuntu
---

### Post by inter-m on 2009-10-05
i just installed ubuntu 9.04 but now I'm trying to update but I'm prompted that there is not enough space... what could be causing the problem...

---

### Post by kanikilu on 2009-10-05
Can you post the results of the following commands from a terminal (Applications > Accessories > Terminal)?

```
df -h /
``` and ```
sudo fdisk -l
```

---

### Post by dwasifar on 2009-10-05
> **inter-m said:**
> i just installed ubuntu 9.04 but now I'm trying to update but I'm prompted that there is not enough space... what could be causing the problem...
Um... perhaps there is not enough space?  :)

Did you install dual boot with some other operating system, and allow the partitioner to clear space and put Ubuntu in the reclaimed area?  If so, it's likely the reclaimed area was just barely enough to do the install and has no room to download update packages.

How big is your drive, and how is it allocated?

---

### Post by QIII on 2009-10-05
And also ...

Did you install via Wubi?

---

### Post by inter-m on 2009-10-05
> **kanikilu said:**
> Can you post the results of the following commands from a terminal (Applications > Accessories > Terminal)?

```
df -h /
``` and ```
sudo fdisk -l
```
this is what i got

Filesystem            Size  Used Avail Use% Mounted on
/dev/sda5             2.3G  2.2G   43M  99% /

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xac7ee453

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       12327    99016596   12  Compaq diagnostics
/dev/sda2   *       12328       17427    40965750    7  HPFS/NTFS
/dev/sda3           17428       19131    13687380    7  HPFS/NTFS
/dev/sda4           19132       19457     2618595    5  Extended
/dev/sda5           19132       19435     2441848+  83  Linux
/dev/sda6           19436       19457      176683+  82  Linux swap / Solaris

---

### Post by inter-m on 2009-10-05
> **QIII said:**
> And also ...

Did you install via Wubi?
no i installed it using live cd

---

### Post by inter-m on 2009-10-05
> **dwasifar said:**
> Um... perhaps there is not enough space?  :)

Did you install dual boot with some other operating system, and allow the partitioner to clear space and put Ubuntu in the reclaimed area?  If so, it's likely the reclaimed area was just barely enough to do the install and has no room to download update packages.

How big is your drive, and how is it allocated?
i c what u mean and i think ur correct... but the strange thing is that i used gparted to allocate more space but i think i messed that up...

---

### Post by kanikilu on 2009-10-05
> **inter-m said:**
> Filesystem            Size  Used Avail Use% Mounted on
/dev/sda5             2.3G  2.2G   43M  99% / Yeah, you are out of space, you need to allocate more room for linux during the install. The installation guide recommends a minimum of 5GB for a full desktop install:

[https://help.ubuntu.com/9.04/installation-guide/i386/minimum-hardware-reqts.html](https://help.ubuntu.com/9.04/installation-guide/i386/minimum-hardware-reqts.html)

You might be able to fix this by booting up with the live CD and resize the partitions with gparted, or just reinstall and give the root partition more space next time.

---

### Post by inter-m on 2009-10-05
thank u all... my problem was that i increased the size of the wrong partition... thanx all...

---

