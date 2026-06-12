---
title: "How would i format my entire hard drive."
date: 2010-07-23
forum: New to Ubuntu
---

### Post by Rave Gloves on 2010-07-23
In an attempt to fix my hard drive problems im going to scrub my hard drive, i do not mean like a clean install, i want to totally format it. Cheers :)

---

### Post by wojox on 2010-07-23
Personally I like [DBAN]("http://www.dban.org/")

---

### Post by Serpher on 2010-07-23
In an Ubuntu live disc go into terminal and type the following commands:

```
sudo -i
fdisk /dev/sda
```

When in  fdisk, type 'd' then 1-4 until all your partitions are gone. This will also delete logical partitions as theyre all in an extended partition which is a primary partition. Then make a new partition using 'n' and make it your whole hardrive and a primary partition.

```
mkfs -t ext4 /dev/sda1
mount -t ext4 /dev/sda1 /mnt/
dd if=/dev/zero of=/mnt/a bs=1G count=10000
umount /mnt/
fdisk /dev/sda1
logout
```

Now delete your partition using the d command again in fdisk. Also the dd command should be run overnight. Takes a long long time to complete. Making a 250GB disk image using it takes close to 4 hours on my 2.4GHz pentium D. This way of formatting turns every single bit on your hardrive besides for a few left over by the ext4 filesystem and MBR into a 0.

---

### Post by gordie69 on 2010-07-23
when i format my drives i use my bootable 98 disk an go into fdisk an erase the partition an create a new one an then format your drive an there you go
try that
good formatting

---

### Post by jboywer on 2010-07-23
Thank you, i wanted to know how to do this.

---

### Post by -kg- on 2010-07-23
You could also read the information at the link in my signature block.  It's a good tutorial on hard drive partitioning operations.

---

