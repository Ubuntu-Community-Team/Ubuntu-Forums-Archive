---
title: "Looking for downgrade help"
date: 2009-11-15
forum: New to Ubuntu
---

### Post by Aaris on 2009-11-15
I upgraded from Ubuntu 9.04 to 9.10 when the release became available. I am not happy with 9.10's performance on my laptop and would like to go back. Things to note:

- I am currently running 9.10 only. I do not dual boot with any other OS.
- I think I have made a live CD of 9.04, but no automatic installer runs when I open it.
- I cannot get it to boot from the CD.
- I'm not able to access the boot menu.

Ideally, I would greatly appreciate it if someone would help to walk me through this. I've been using Ubuntu generally for the last year, I enjoy it and I am familiar with most things, but this is the first time I've tried to "downgrade" and do a "clean install" so I'm really lost. I know this is kind of a large request, but I would really appreciate it.

---

### Post by Sef on 2009-11-15
First we need to know how your hard drive is partitioned.

Applications > Accessories > Terminal

then copy and paste this code

```
sudo fdisk -l
```

Copy and paste the results here.

---

### Post by werecatomega on 2009-11-15
you can't get to the boot menu? if you have all you personal info backup, i'd say reinstall, but you can't do that, tell me your computer stats

---

### Post by Aaris on 2009-11-15
> **Sef said:**
> First we need to know how your hard drive is partitioned.

Applications > Accessories > Terminal

then copy and paste this code

```
sudo fdisk -l
```

Copy and paste the results here.

Results:
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00077963

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1824    14648437+  83  Linux
/dev/sda2            1824        2304     3858398   83  Linux
/dev/sda3            2304       19458   137784068   83  Linux

---

