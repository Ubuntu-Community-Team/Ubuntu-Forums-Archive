---
title: "Mounting USB drive logical partition"
date: 2010-08-21
forum: New to Ubuntu
---

### Post by blackhill on 2010-08-21
I have attached a USB hard drive with three  primary partitions and a fourth extended partition to my Ubuntu 10.04 system

The three primary partitions are visible under "Places" in Ubuntu and can be read and written to.

The extended partition has one logical partition which is not accessible for writing
Unlike the primary partitions, it has two entries under "Places"
One simply names it (A_Ubuntu), the other entry is Mount A_Ubuntu

I presume that this partition requires mounting but I do not know how to do this
Please can someone point me in the right direction

---

### Post by Zimmer on 2010-08-21
One moment..
Quickest way to handle disk mounting is to right click on the Gnome panel and add the 'Disk Mounter ' App. this will put little icons of all partitions on the panel and you can click on them to get a mount/ unmount  facility.

---

### Post by Zimmer on 2010-08-21
and in answer to your next question.... how to access it read/write as your user..
Assuming it gets mounted at /media..

sudo chown <yourusername> /media/<yourpartitionname>

---

