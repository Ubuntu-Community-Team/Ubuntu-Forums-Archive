---
title: "A possible frugal install - Like Puppy Linux?"
date: 2009-08-09
forum: New to Ubuntu
---

### Post by Dark Aspect on 2009-08-09
Hello Ubuntu users and Windows users alike,

I got my hands on a free 8GB Flash drive today and I was curious if there is a way to install Ubuntu on a non-linux filesystem like fat32 or NTFS. Much like Puppy Linux's frugal installation where data is kept from each session in a small ext2 file system. Basically, I am looking for a file structure much like:

```
Root
 |
 |-----boot
 |       |
 |      initrd.gz (Ubuntu system files)
 |       |
 |      vmlinuz (Kernel)
 |       |
 |      Other files (System related)
 |
 |
 |----Other files and folders
```

The reason I don't want ext3 is I am trying to create a bootable USB device but keep windows compatibility.

Thank you for reading and any suggestions.

---

### Post by cwsnyder on 2009-08-09
A WUBI installation is designed to work in a small NTFS system, but I don't know about installing on a flash drive.

---

### Post by Dark Aspect on 2009-08-09
> **cwsnyder said:**
> A WUBI installation is designed to work in a small NTFS system, but I don't know about installing on a flash drive.

I was under the influence that WUBI worked like a virtual machine, I'll check it out my self but I believe I am looking for something else.

Thanks anyway though

---

### Post by Ji Ruo on 2009-08-09
There is a package in synaptic called unetbootin (appears to be QT based) that has a GUI for creating a linux flash drive. Someone has posted a tutorial on YouTube using unetbootin, that uses fat32 - [http://www.youtube.com/watch?v=AIdQ_N8nwZw](http://www.youtube.com/watch?v=AIdQ_N8nwZw)

HTH

---

### Post by mrgreggie on 2009-08-09
I don't have a free drive handy to try it at the moment, but can't you partition a thumb drive like any other drive?  That way you could have a partition for Ubuntu and another one for storage.  With an 8GB drive it would actually be practical too.

---

### Post by tgalati4 on 2009-08-09
Damn Small Linux has a USB installer that puts DSL on a small, second ext2 partition.  The first partition is fat32 and that allows you to boot yet keep your /home files in a windows and linux readable partition.

So, yes you can do it, but realize that your flash drive life will shorten if you don't take precautions on how frequently the drive is written.  DSL runs primarily in RAM or reads from a small, compressed ISO image.

Ubuntu is much larger and requires a proper file system to operate.  Because of the hold-til-cache-is-full writing strategy to USB flash drives, performance may be problematic.

Let us know what works for you.

---

### Post by Dark Aspect on 2009-08-09
> **Ji Ruo said:**
> There is a package in synaptic called unetbootin (appears to be QT based) that has a GUI for creating a linux flash drive. Someone has posted a tutorial on YouTube using unetbootin, that uses fat32 - [http://www.youtube.com/watch?v=AIdQ_N8nwZw](http://www.youtube.com/watch?v=AIdQ_N8nwZw)

HTH

Thank you, that might be what I need.

> **mrgreggie said:**
> I don't have a free drive handy to try it at the moment, but can't you partition a thumb drive like any other drive?  That way you could have a partition for Ubuntu and another one for storage.  With an 8GB drive it would actually be practical too.

Thats a good point, can I format a drive where the home folder is the fat32/NTFS partition? If so where can I find a good howto for that very setup.

> **tgalati4 said:**
> 
So, yes you can do it, but realize that your flash drive life will shorten if you don't take precautions on how frequently the drive is written.  DSL runs primarily in RAM or reads from a small, compressed ISO image.


The only thing I need to take in account to reduce the chance of a shortened life is the swap file, no?

Thats how I have previously setup thumb drives and I have never had a problem.

---

### Post by mrgreggie on 2009-08-11
> **Dark Aspect said:**
> 
 Thats a good point, can I format a drive where the home folder is the fat32/NTFS partition? If so where can I find a good howto for that very setup.


I couldn't find anything thumb drive specific, but I imagine that gparted should be able to handle it without a problem.  Since the entire thing is formatted FAT/NTFS already, it should just be a matter of shrinking the FAT/NTFS partition and creating a new ext3 and swap partition with the newfound free space.  Unfortunately I don't have a thumb drive larger than 512MB, otherwise I'd gladly try it myself and write up a good howto.

---

### Post by PartsMan on 2009-08-11
You might check out this site.
[http://www.pendrivelinux.com/index.php?s=ubuntu](http://www.pendrivelinux.com/index.php?s=ubuntu)

---

