---
title: "Is ubuntu able to mount ntfs volumes from windows"
date: 2009-04-24
forum: New to Ubuntu
---

### Post by sn00pd0gg1 on 2009-04-24
I need help badly, I'm wondering if ubuntu could mount ntfs volumes of a windows pc dual booted with linux?

---

### Post by Peter09 on 2009-04-24
This useful?
[https://help.ubuntu.com/community/MountingWindowsPartitions/ThirdPartyNTFS3G](https://help.ubuntu.com/community/MountingWindowsPartitions/ThirdPartyNTFS3G)

---

### Post by blazemore on 2009-04-24
Yes, it can.

Click the Places menu, and see if your disk is listed there.

if it isn't you'll have to mount it yourself.

Create a directory called /windows (for example)
```
sudo mkdir /windows
```

Find the device name of the Windows disk:
```
sudo fdisk -l
```

You're looking for an ntfs disk. I'm going to assume it's /dev/sda1, but for you it may be different.

Mount this disk in the /windows folder:

```
sudo mount -t ntfs /dev/**sda1** /windows
```
Remember to change the device name to match your system.

---

### Post by mbzn on 2009-04-24
yes it can

goto Places>(volume name). the volume will be called something like '500GiB volume' or something like that.

Otherwise try google
[HTML]http://www.arsgeek.com/2006/09/25/ubuntu-tricks-how-to-mount-your-windows-partition-and-make-it-readwritable/[/HTML]

There are 1000's

---

### Post by Paddy Landau on 2009-04-24
Ubuntu should have automatically found your Windows partition, as the previous posters said. Linux handles NTFS well.

If you want to access your Linux partition from Windows, however, you need to download a (free) program for Windows. The best that I found was [IFS Driver]("http://www.fs-driver.org/"), which allows you to choose between read-only and read-write.

---

### Post by colau on 2009-06-27
> **sn00pd0gg1 said:**
> I need help badly, I'm wondering if ubuntu could mount ntfs volumes of a windows pc dual booted with linux?
Does [ntfs-3g]("http://ubuntuforums.org/showthread.php?t=1168719&highlight=mount+ntfs") help?

---

### Post by SunnyRabbiera on 2009-06-27
also ntfs config can help too.

---

### Post by ~sHyLoCk~ on 2009-06-27
install ntfs-3g and > sudo mkdir /windows
and then add > /dev/sda1 /windows ntfs-3g defaults,rw   0 0 to /etc/fstab

---

### Post by rockerphil on 2009-06-28
> **Paddy Landau said:**
> Ubuntu should have automatically found your Windows partition, as the previous posters said. Linux handles NTFS well.


not always true. i built a minimal Ubuntu system using this tuturial


[http://www.psychocats.net/ubuntu/minimal](http://www.psychocats.net/ubuntu/minimal)

and Ubuntu doesn't auto-mount my NTFS fily systems, i had to add it to my /etc/fstab file

it simply depends on the DE you use

Phil

---

### Post by binbash on 2009-06-28
> **rockerphil said:**
> not always true. i built a minimal Ubuntu system using this tuturial


[http://www.psychocats.net/ubuntu/minimal](http://www.psychocats.net/ubuntu/minimal)

and Ubuntu doesn't auto-mount my NTFS fily systems, i had to add it to my /etc/fstab file

it simply depends on the DE you use

Phil

Linux means linux kernel not OS

---

### Post by Mark Phelps on 2009-06-29
> **rockerphil said:**
> not always true.
READ what he said ... he said that Ubuntu "finds" the partitions automatically, not that it "mounts" them.

If you go into Places, you will see ALL the partitions on your PC. Simply clicking on the icon will mount the partition.  As you have already found, though, you have to add it to FSTAB to get it to be auto-mounted at startup.

---

