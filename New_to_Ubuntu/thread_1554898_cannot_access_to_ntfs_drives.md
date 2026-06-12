---
title: "cannot access to ntfs drives"
date: 2010-08-17
forum: New to Ubuntu
---

### Post by langmarp on 2010-08-17
hi

i have reinstalled 10.04
I gave mount point for my ntfs partitions, but they do not appear in the system
I have tried ntfsprogs, gparted and ntfs config tool

what is the solution?

thanks!

---

### Post by Hospadar on 2010-08-17
Are you sure?
Can you post the output of the following commands (you can just copy-paste the whole block into the terminal and copy the result back here)
```

#show currently mounted disks, the -h option uses human-friendly numbers for disk size
df -h
#look at the folders where they are supposed to be mounted
ls /vb
ls /data
ls /
#

```When you browse to /vb or /data do you just see empty folders?

---

### Post by langmarp on 2010-08-17
```
petak@petak-laptop:~$ #show currently mounted disks, the -h option uses human-friendly numbers for disk size
petak@petak-laptop:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1              68G  4.3G   60G   7% /
none                  1.5G  328K  1.5G   1% /dev
none                  1.5G  3.4M  1.5G   1% /dev/shm
none                  1.5G   84K  1.5G   1% /var/run
none                  1.5G     0  1.5G   0% /var/lock
none                  1.5G     0  1.5G   0% /lib/init/rw
/dev/sda4             153G   65G   89G  43% /data
/dev/sda3              69G   30G   39G  44% /vb
petak@petak-laptop:~$ #look at the folders where they are supposed to be mountedpetak@petak-laptop:~$ ls /vb
win7 vb.vdi
petak@petak-laptop:~$ ls /data
actual     downloads      Kontra             Selection_003.png  win7 vb.vdi
Art        ebook calibre  research           Selection_004.png
aup        email          Selection_001.png  Selection_005.png
documents  emlek temp     Selection_002.png  Ugyek
petak@petak-laptop:~$ ls /
bin    data  home            lib         mnt   root     srv  usr  vmlinuz
boot   dev   initrd.img      lost+found  opt   sbin     sys  var  vmlinuz.old
cdrom  etc   initrd.img.old  media       proc  selinux  tmp  vb

```

fine, I see (in Nautilus) the drives in the file system as folders, but there are three negative changes since the reinstall:
partitions appear only as folders, but not as separate partitions
can not move file to the trash
can not create a shortcut to the folder


thank you!

---

