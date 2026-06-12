---
title: "partitioning"
date: 2009-01-31
forum: New to Ubuntu
---

### Post by theozzlives on 2009-01-31
k, here's the low down. I had Windows XP on sda1 when I installed 8.04. / is on sda3, and /home is on sda4. I want to move the free space down to sda4.

I tried gparted live and deleted Windows. Moved the free space past the extended, and past the swap. Gparted wont let me move it any farther, or resize sda3 or 4.

So I'm stuck, I don't wanna re-install. HELP!!

---

### Post by Jynxx on 2009-01-31
Quick question, were the partitions unmounted when you tried resizing them? They have to be unmounted to resize.

---

### Post by theozzlives on 2009-01-31
> **Jynxx said:**
> Quick question, were the partitions unmounted when you tried resizing them? They have to be unmounted to resize.

yes they were

---

### Post by taurus on 2009-01-31
Post the layout of your harddrive.

```
sudo fdisk -l
```

---

### Post by theozzlives on 2009-01-31
Disk /dev/sda: 20.0 GB, 20020396032 bytes
255 heads, 63 sectors/track, 2434 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x24f224f2

   Device Boot      Start         End      Blocks   Id  System
/dev/sda2               1        1311    10530576    5  Extended
/dev/sda3            1312        2069     6088635   83  Linux
/dev/sda4            2070        2434     2931862+  83  Linux
/dev/sda5               1          65      522049+  82  Linux swap / Solaris

It don't show the unallocated space but in gparted it's right under swap which is under extended.

---

### Post by taurus on 2009-01-31
Can you post the screenshot of gparted showing your harddrive, /dev/sda.

---

### Post by theozzlives on 2009-01-31
here ya go

---

### Post by jerome1232 on 2009-01-31
Maybe you can shrink the extended partition (/dev/sda2) down to the swap partition then move / and /home down behind the freespace, but you will still need to do it from a live cd since they need to be unmounted.

---

### Post by taurus on 2009-01-31
Are you running gparted from your harddrive, /dev/sda3?  You cannot unmount root filesystem while you are still using it.  Therefore, you have to use either gparted from the LiveCD or GParted LiveCD, [http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php).

---

### Post by theozzlives on 2009-01-31
They were unmounted, just not now. I didn't think of moving the extended, I can do that?

---

### Post by theozzlives on 2009-01-31
I did it, and didn't lose data:

---

