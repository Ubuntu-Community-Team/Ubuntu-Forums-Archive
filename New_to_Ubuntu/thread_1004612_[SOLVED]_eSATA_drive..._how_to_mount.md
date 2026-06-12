---
title: "[SOLVED] eSATA drive... how to mount?"
date: 2008-12-07
forum: New to Ubuntu
---

### Post by solex222 on 2008-12-07
totally stupid question but PLEASE help me out! I have external NTFS-formatted HDD linked via eSATA, ntfs-config is already installed and support for external drives is on.
system responds as below

solex@solex-desk:~$ sudo blkid
  /dev/sda1: UUID="E29C74B59C7485B7" TYPE="ntfs" 
  /dev/sdb1: UUID="200b40ff-ed7e-4a8a-b603-5f5436e2dd94" TYPE="ext3" 
  /dev/sdb5: TYPE="swap" UUID="2a67855f-93ea-45d5-a0ec-96786eb4855c" 
  /dev/sdc1: UUID="96C83342C8331FC3" LABEL="FreeAgent XTreme" TYPE="ntfs" 

solex@solex-desk:~$ cat /etc/fstab
  proc /proc proc defaults 0 0
  # Entry for /dev/sdb1 :
  UUID=200b40ff-ed7e-4a8a-b603-5f5436e2dd94 / ext3   
  relatime,errors=remount-ro 0 1
  # Entry for /dev/sdb5 :
  UUID=2a67855f-93ea-45d5-a0ec-96786eb4855c none swap sw 0 0
  /dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0
  /dev/sda1 /media/WinXP ntfs-3g defaults,locale=ru_RU.UTF-8 0 0

what i have to do next to be able to use drive labelled "FreeAgent XTreme" please? how to modify system to have it mounted automatically when system loads? may be couple of links to where i may get some structured information on this subject?

Thanks in advance!

---

### Post by cdtech on 2008-12-07
Create a directory:
```
sudo mkdir /media/FreeAgent
```
Then add this to your "fstab" file:
```
# Entry for /dev/sdc1 :
UUID=96C83342C8331FC3 /media/FreeAgent ntfs defaults,umask=002,gid=46 0 2
```
Then:
```
sudo mount -a
```

---

### Post by lovelyvik293 on 2008-12-07
You have three HDD's and the third one which you want to mount doesn't have the entry at the /etc/fstab
so you can mount it manualy by using command mount 

```

mount -t ntfs /mount point /dev/hdc1

```

---

