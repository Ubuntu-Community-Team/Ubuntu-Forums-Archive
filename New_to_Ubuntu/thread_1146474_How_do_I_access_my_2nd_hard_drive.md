---
title: "How do I access my 2nd hard drive ?"
date: 2009-05-02
forum: New to Ubuntu
---

### Post by zulasmum on 2009-05-02
Hi
I have a PC running ubuntu server 8.04 which I access using putty and I have 2 identical 320 gb drives inside. Only 1 is being used for os and data. I would like to use the other as a back up but not sure how to go about it. At the moment the output of fdisk -l is:

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0007cb96

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       38160   306520168+  83  Linux
/dev/sda2           38161       38913     6048472+   5  Extended
/dev/sda5           38161       38913     6048441   82  Linux swap / Solaris

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

Disk /dev/sdb doesn't contain a valid partition table

So, if I wanted to use space on this disk (/dev/sdb)to back up data from my network what do I need to do?
Hope my question makes sense!

Zulasmum

---

### Post by taurus on 2009-05-02
You first need to create a partition on that new drive, /dev/sdb1, and format it before you can use it.  Then, you can add an entry in /etc/fstab to have it mount automatically each time you boot.

---

### Post by zulasmum on 2009-05-02
What is the best way to create a partition?

---

### Post by taurus on 2009-05-02
Since you are running a server, I assume everything is from a prompt.  You can create a partition with cfdisk.

```
sudo cfdisk /dev/sdb
```

---

### Post by zulasmum on 2009-05-02
Should I just make one partition and would it be sensible to make it bootable?

---

### Post by taurus on 2009-05-02
Pick the p for primary and you do not need to make it bootable.  Make sure you make it as a Linux partition, 83, though.

Once you write and quite, you then need to format it.  Assuming you are using ext3 filesystem, you would do something like

```
sudo mke2fs -j /dev/sdb1
```

---

### Post by zulasmum on 2009-05-02
Thanks Taurus - I have formatted it, I think. What next - you mentioned automatically mountuing it?

---

