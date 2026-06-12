---
title: "if i format a partition , will ubunto boot"
date: 2009-09-06
forum: New to Ubuntu
---

### Post by sarois3 on 2009-09-06
I have a partition that i would like to format and put back to vista envirnment.
This partition was reserved by ubuntu as a swap space

if i format partition that partition, will ubunto boot

---

### Post by ibutho on 2009-09-06
Ubuntu will boot, but will complain that it cannot find the swap device. If you do not wish to use swap or want to use the partition for something else, edit /etc/fstab and comment out the line for swap e.g. change
```
# swap was on /dev/sda6 during installation
UUID=65f2cc5f-e23d-4d3c-b30e-9b8c338de942 none            swap    sw              0       0

```
to
```
# swap was on /dev/sda6 during installation
#UUID=65f2cc5f-e23d-4d3c-b30e-9b8c338de942 none            swap    sw              0       0

```

---

### Post by Bucky Ball on 2009-09-06
Not the greatest idea to run without a /swap.

ibutho's suggestion should work.

---

### Post by bumanie on 2009-09-06
I ran ubuntu without /swap for a period of time. If you only have  512mb of ram, I would keep the /swap space. How large is /swap? 1GB /swap is usually enough if you are running 1-2 GB of ram. If /swap is large, you could shrink it with gparted and then hand the rest back to vista. As long as you have plenty of ram and not doing lots of heavy stuff like converting video etc., things should work OK - your only 'issue' should be ubuntu complaining that there is no /swap, it should boot though. Of course, if you just shrink /swap, ubuntu won't complain at all.

---

### Post by sarois3 on 2009-09-06
> **ibutho said:**
> Ubuntu will boot, but will complain that it cannot find the swap device. If you do not wish to use swap or want to use the partition for something else, edit /etc/fstab and comment out the line for swap e.g. change
```
# swap was on /dev/sda6 during installation
UUID=65f2cc5f-e23d-4d3c-b30e-9b8c338de942 none            swap    sw              0       0

```
to
```
# swap was on /dev/sda6 during installation
#UUID=65f2cc5f-e23d-4d3c-b30e-9b8c338de942 none            swap    sw              0       0

```

where exactly do i put this code.
Sorry i am very new to linux.

---

### Post by Bucky Ball on 2009-09-06
Applications->Accessories->Terminal, then:
```

sudo nano /etc/fstab
``` Remember: your UUID number will be different to ibutho's. 

You will find it in that file. If you just want to look at it first without making any changes run the command above without the 'sudo' at the start.

```
nano /etc/fstab
```WARNING: don't change anything else in there! If you want to be really safe, back this file up first with:

```
sudo cp /etc/fstab /etc/fstab.backup
```Makes a copy of the file 'fstab' called 'fstab.backup' in the folder 'etc'. :)

---

### Post by mlentink on 2009-09-06
Why would you want to reclaim those few gigs? A swap partition can't be bigger than, say, 2GB (the rest would be a waste of space). I hear Vista is resource-hungry, but _*that*_ much?

---

