---
title: "Kernal Panic"
date: 2009-11-12
forum: New to Ubuntu
---

### Post by iSteed on 2009-11-12
I'm not sure if this thread belongs in the Beginner section, but here it is anyway.

I have been using ubuntu as my linux distro of choice for quit some time as a hobbiest. i installed the ubuntu notebook remix to my dell inspiron 710m. everything was going well, but when the update manager opened i just hit the install button. i guess i should have read was i was really installing. because when i shut the computer down, it would no longer boot. i get the message 

kernel panic not syncing vfs unable to mount root fs on unknown-block 8 1

that or something very close to it. i did some googling and apparently it is a common problem but seems to happen on mostly installations. i however have some documents on the computer that i would like to recover. if i could go back to the way things were that would be great. but i also plan on reinstalling ubuntu anyway, not a big fan of notebook remix. I have tried some things i have read about on the subject, but i just feel lost and in over my head.

When i boot up from my live usb disk (as i am now) i can not see the original drive, or maybe i dont know where to look. at this point i just want my files, but any information on how to reverse this problem if it comes up again, would be much appreciated.

---

### Post by eagle416 on 2009-11-12
look around on nautilus for your hard disk listed as a drive. On a live disk your root will actually be on the cd, not the hard drive.

If you can't find your hard disk, manually mount it.

```
sudo fdisk -l
``` should give you a list of the filesystems to search through.

---

### Post by sandyd on 2009-11-12
> **iSteed said:**
> I'm not sure if this thread belongs in the Beginner section, but here it is anyway.

I have been using ubuntu as my linux distro of choice for quit some time as a hobbiest. i installed the ubuntu notebook remix to my dell inspiron 710m. everything was going well, but when the update manager opened i just hit the install button. i guess i should have read was i was really installing. because when i shut the computer down, it would no longer boot. i get the message 

kernel panic not syncing vfs unable to mount root fs on unknown-block 8 1

that or something very close to it. i did some googling and apparently it is a common problem but seems to happen on mostly installations. i however have some documents on the computer that i would like to recover. if i could go back to the way things were that would be great. but i also plan on reinstalling ubuntu anyway, not a big fan of notebook remix. I have tried some things i have read about on the subject, but i just feel lost and in over my head.

When i boot up from my live usb disk (as i am now) i can not see the original drive, or maybe i dont know where to look. at this point i just want my files, but any information on how to reverse this problem if it comes up again, would be much appreciated.
seems like initrid / your partition might be corrupt.

try running testdisk or some disk-checking utility (ill go with corruption cause of the mounting problem)

p.s if it IS initrid, running```
sudo update-initramfs
``` would be helpful

---

### Post by iSteed on 2009-11-12
i ran the fdisk -l returning:

ubuntu@ubuntu:/$ sudo fdisk -l

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd0f4738c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        7139    57343986    7  HPFS/NTFS
/dev/sda2            7140        9729    20804175    f  W95 Ext'd (LBA)
/dev/sda5            7140        9729    20804143+   7  HPFS/NTFS

Disk /dev/sdb: 2047 MB, 2047678976 bytes
63 heads, 62 sectors/track, 1023 cylinders
Units = cylinders of 3906 * 512 = 1999872 bytes
Disk identifier: 0x0004155f

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        1023     1997888    b  W95 FAT32
Partition 1 has different physical/logical endings:
     phys=(1023, 62, 62) logical=(1022, 62, 62)


i then mounted sda1 and sda5, and i believe since sda2 is an extension, and i cant mount it.

sda1 contained:

<all my windows junk>

sda5 contained:

AUTORUN.INF  RECYCLER  SMRTNTKY  System Volume Information  setupSNK.exe

which i think that is a partition with nothing on it too important from the previous owner of this computer.

where would my ubuntu installation be?

---

### Post by eagle416 on 2009-11-12
how big is your Ubuntu partition (assuming that's what you want to access)?

take note that in the data you posted you do have an /dev/sdb1 of a FAT32 nature. Is that a memory stick or is that the partition?

---

### Post by iSteed on 2009-11-12
i can not remember off the top of my head how large it is. i left the deafults while installing knowing it would partition it off from windows. and yes sdb1 is the memory stick i booted off of. i want to say though i left it at something like 16 gigabytes.

---

### Post by iSteed on 2009-11-12
just found something interesting:

while sifting through sda1, i have an ubuntu folder. inside there is -

ubuntu@ubuntu:~$ ls /mnt/sda1/ubuntu/disks/         
boot  root.disk  swap.disk


boot is a directory and the other two items are files. am i able to virtually mount these?

---

### Post by iSteed on 2009-11-12
ok, so i installed ubuntu using the webui under windows. and i found my 16 gig file named root.disk. now my new problem is how do i get my files out of there?

---

### Post by iSteed on 2009-11-12
Ok i have solved my problem. this is what i did:

ubuntu@ubuntu:~$ sudo mkdir /win
ubuntu@ubuntu:~$ sudo mount /dev/sda1 /win
ubuntu@ubuntu:~$ sudo mkdir /vdisk
ubuntu@ubuntu:~$ sudo mount -o loop /win/ubuntu/disks/root.disk /vdisk
ubuntu@ubuntu:~$ ls /vdisk
bin    dev   host        lost+found  opt   sbin     sys  var
boot   etc   initrd.img  media       proc  selinux  tmp  vmlinuz
cdrom  home  lib         mnt         root  srv      usr


and now i can copy over my files and reinstall and take the whole hard drive for my ubuntu.

---

