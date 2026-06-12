---
title: "How to format portable Hard Disk"
date: 2009-05-21
forum: New to Ubuntu
---

### Post by mosaabJ on 2009-05-21
Hello, I just want to ask how to format a portable hard disk that contains Ubuntu 9.04 on it.

---

### Post by Cypher on 2009-05-21
Does it connect to your PC through a USB port? If so, plug it in, wait for a moment and it should be recognized, from the command line do
```

sudo fdisk -l

```
This will show you all the partitions, fine the one you are interesting in (by looking at the size) and once you have that you can do
```

mkfs.ext3 <partition name>

```
This will format (erase all data) from the partition and make it an EXT3 filesystem. You can set other optional stuff on the partition, do "man mkfs.ext3" to check those out..

NOTE: This assumes you don't care what's on the portable hard drive and WANT to erase everything on there indiscriminately.

---

### Post by mosaabJ on 2009-05-21
How do I know which one is the Hard Disk if both the internal and external hard disk have the same size

---

### Post by Cypher on 2009-05-21
There are multple ways, the internal hardware will have the earlier alphabet..so it will be sda (if you have multiple HDs, they will take sdb) and so on. The portable will take the later alphabet.

The other way is to unplug the portable drive, run "sudo fdisk -l" to see what's there, then plug the drive in and re-run the command notice the newly added device name.

---

### Post by mosaabJ on 2009-05-21
I am really sorry but really there are many info I didn't know which one is the partition name

---

### Post by Cypher on 2009-05-21
How about you show us the output and we'll tell you.

---

### Post by mosaabJ on 2009-05-21
```
Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x9e009e00

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *         681       38913   307106572+   7  HPFS/NTFS
/dev/sda2               1         680     5462068+  12  Compaq diagnostics

Partition table entries are not in disk order

Disk /dev/sdf: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe3414533

   Device Boot      Start         End      Blocks   Id  System
/dev/sdf1   *           1       37973   305018091   83  Linux
/dev/sdf2           37974       38913     7550550    5  Extended
/dev/sdf5           37974       38913     7550518+  82  Linux swap / Solaris
ubuntu@ubuntu:~$ 
```

---

### Post by Cypher on 2009-05-21
OK, so I'm going to guess that SDA is your internal HD and SDF is the external HD. Not sure what happened to B-E..

Let's confirm this by unplugged the portabl HD and run the command show the output..

---

### Post by mosaabJ on 2009-05-21
Yes I did confirm this

---

### Post by mosaabJ on 2009-05-21
I wrote this:
mkfs.ext3 /dev/sdf

 but it says: 
mkfs.ext3: Permission denied while trying to determine filesystem size

---

### Post by TpyKv on 2009-05-21
you will need to type 

sudo 

before the rest of the command....

---

### Post by mosaabJ on 2009-05-21
Now I get this message: 
/dev/sdf is apparently in use by the system; will not make a filesystem here!

---

### Post by KoolPenguin on 2009-05-21
> **mosaabJ said:**
> Now I get this message: 
/dev/sdf is apparently in use by the system; will not make a filesystem here!

I use GParted to partition and format my external drives.  Select the device, in your case /dev/sdf, unmount it from within GParted and select Format.  Both unmount and format options are under the Partition menu.

---

### Post by mosaabJ on 2009-05-21
Do I have to install Gparted

---

### Post by KoolPenguin on 2009-05-21
> **mosaabJ said:**
> Do I have to install Gparted

In Gnome, look under System -> Administration for Partition Editor. If not there then install gparted with Synaptic Package Manager.

---

### Post by mosaabJ on 2009-05-21
I,ve Formatted and it works now Thank you):P

---

### Post by KoolPenguin on 2009-05-24
> **mosaabJ said:**
> I,ve Formatted and it works now Thank you):P

Glad I could help.

---

### Post by ruchir77 on 2009-05-25
> **mosaabJ said:**
> Now I get this message: 
/dev/sdf is apparently in use by the system; will not make a filesystem here!

dude you must have the disk running in the file browser or some other  application(media player, notepad) that is why you got the error message 

close all that 

then unmount the drive

then give sudo mkfs.ext3 <name of partition>

i did it just now...worked fine :)

---

