---
title: "changing permissions"
date: 2009-11-12
forum: New to Ubuntu
---

### Post by jhapk on 2009-11-12
Hi,

I am trying to change permissions on a mounted drive, and its not allowing me to do it.
Here's the output I am getting

```
jhapk@chhotu:/pitcairn$ ls -l favourites2.pdf 
-rwxrwxrwx 1 root root 368384 2006-03-22 18:41 favourites2.pdf
jhapk@chhotu:/pitcairn$ sudo chmod 755 favourites2.pdf 
jhapk@chhotu:/pitcairn$ ls -l favourites2.pdf 
-rwxrwxrwx 1 root root 368384 2006-03-22 18:41 favourites2.pdf
```

Any idea what can be going wrong?

The line in fstab mounting this drive is
[CODE]
/dev/sda7       /pitcairn auto    iocharset=utf8,umask=000        0       0
[\CODE]

THanks

---

### Post by phishie on 2009-11-12
My guess is that's a drive formatted with a format that does not support permissions like FAT32.

---

### Post by ukripper on 2009-11-12
What is the filesystem format of the drive? Fat32/NTFS won't support linux ACL

---

### Post by jhapk on 2009-11-12
Hi,

 the output for $df -T is
 ```

/dev/sda7     vfat    30701232  27146624   3554608  89% /pitcairn

```Don't know if that helps

---

### Post by phishie on 2009-11-12
> **jhapk said:**
> Hi,

 the output for $df -T is
 ```

/dev/sda7     vfat    30701232  27146624   3554608  89% /pitcairn

```Don't know if that helps

Yeap, vfat can't support ACL. That's the problem you are having there.

---

### Post by ukripper on 2009-11-12
> **jhapk said:**
> Hi,

 the output for $df -T is
 ```

/dev/sda7     vfat    30701232  27146624   3554608  89% /pitcairn

```Don't know if that helps

it is fat/fat32 partititioned drive. You need reformat the drive to ext3/ext4 to make use of file permissions on ubuntu system. Make sure to backup your data first if you are going to reformat  your above drive

---

### Post by jhapk on 2009-11-12
I changed it to ext4.
Works fine now. Thanks a lot.

---

### Post by Zoot7 on 2009-11-12
Just to add here's a great article on the intricacies of the Linux file permissions.
[http://www.linuxforums.org/articles/file-permissions_94.html](http://www.linuxforums.org/articles/file-permissions_94.html)

---

