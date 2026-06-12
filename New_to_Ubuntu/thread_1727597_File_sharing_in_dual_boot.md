---
title: "File sharing in dual boot?"
date: 2011-04-12
forum: New to Ubuntu
---

### Post by mikro 402 on 2011-04-12
How can I access the Win 7 files from Ubuntu and vice versa. (I mean on the same machine.)
I have Wine installed and working but I need to access the files from the C: drive.

I had been reading about Samba but I'm not sure thats what I need.

Thank you,

Mikro

---

### Post by TeoBigusGeekus on 2011-04-12
Go to the Places menu, select your win drive and click it.
Windows cannot access linux filesystems - and a good thing too.

If you want to have a common data partition for both systems, you could create an extra ntfs partition which can be accessed by both linux and windows.

---

### Post by mikro 402 on 2011-04-12
> **TeoBigusGeekus said:**
> Go to the Places menu, select your win drive and click it.
Windows cannot access linux filesystems - and a good thing too.

If you want to have a common data partition for both systems, you could create an extra ntfs partition which can be accessed by both linux and windows.

It isn't in Places..Just HomeFolder,Documents,Desktop,Music,Pictures,Videos,Downloads,Computer,Factory Image,Network,Basement,Connect To Server,Search For Files, and Recent Documents.

---

### Post by jtarin on 2011-04-12
Can you post a copy of your /etc/fstab file?

---

### Post by mikro 402 on 2011-04-12
> **jtarin said:**
> Can you post a copy of your /etc/fstab file?


# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/host/ubuntu/disks/root.disk /               ext4    loop,errors=remount-ro 0       1
/host/ubuntu/disks/swap.disk none            swap    loop,sw         0       0

---

### Post by jtarin on 2011-04-12
> **mikro 402 said:**
> # /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/host/ubuntu/disks/root.disk /               ext4    loop,errors=remount-ro 0       1
/host/ubuntu/disks/swap.disk none            swap    loop,sw         0       0
You don't have a mount point for NTFS

---

### Post by akakingess on 2011-04-12
[TeoBigusGeekus]("http://ubuntuforums.org/member.php?u=504094") is 100% correct, that is the simplest way to share files, however, creating a partition formatted NTFS strictly for sharing/storage is the best way to go if you can.

---

### Post by rosencrantz on 2011-04-12
NTFS partitions should show up in Places no matter what the fstab says.
Your Places list looks a bit funny, though. Can you attach a screenshot?
For a permanent solution: +1 for the additional shared NTFS partition. That one should be added to fstab to have it permanently mounted.

---

### Post by jtarin on 2011-04-12
> **rosencrantz said:**
> NTFS partitions should show up in Places no matter what the fstab says.
Your Places list looks a bit funny, though. Can you attach a screenshot?
For a permanent solution: +1 for the additional shared NTFS partition. That one should be added to fstab to have it permanently mounted.My bad....I didn't catch the "from C: drive", but the best way by far is a shared partition. That was my thinking when I asked for the fstab.

---

### Post by mikro 402 on 2011-04-12
> **rosencrantz said:**
> NTFS partitions should show up in Places no matter what the fstab says.
Your Places list looks a bit funny, though. Can you attach a screenshot?
For a permanent solution: +1 for the additional shared NTFS partition. That one should be added to fstab to have it permanently mounted.

[IMG]http://i1194.photobucket.com/albums/aa364/Mikro402/Screenshot.png?t=1302659080[/IMG]

---

### Post by jtarin on 2011-04-12
What's that entry Factory_Image? Could be methinks.

---

### Post by mikro 402 on 2011-04-12
> **jtarin said:**
> What's that entry Factory_Image? Could be methinks.

I think it is the Windows Vista. I had upgraded to Win 7 before loading Ubuntu

---

### Post by jtarin on 2011-04-12
And when you click on it what does it mount?

---

### Post by mikro 402 on 2011-04-12
I tried this:

den@ubuntu:~$ sudo mount -t ntfs -o nls=utf8,umask=0222 /dev/sda1 /mnt/windrive/c
Mount is denied because the NTFS volume is already exclusively opened.
The volume may be already mounted, or another software may use it which
could be identified for example by the help of the 'fuser' command.


Where could it be if it's already mounted?

---

### Post by mikro 402 on 2011-04-12
I found the directory /host in Nautilus and that is where the Windows files are. I think its /dev/sda1

---

### Post by rosencrantz on 2011-04-12
OK, do you have more than one non-linux partition or any external disks/memory cards attached?
If not, I'd guess that FACTORY_IMAGE is your Windows partition and Factory_image is the partition label.
Try mounting it and see what's on it.
Be **very** careful about writing to it. Stick to 'My Documents'.

OK: This post was inexplicably late...

---

