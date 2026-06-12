---
title: "How to remove some desktop icons"
date: 2009-02-25
forum: New to Ubuntu
---

### Post by Swenghk on 2009-02-25
I have a dual boot with Windows Vista and Ubuntu 8.04. On my desktop I have two icons that read "51.4 GB Media" and "21.4 GB Media"

How do I remove these from the Desktop?

---

### Post by Therion on 2009-02-25
Right-click and use "Unmount Volume".

---

### Post by dje on 2009-02-25
please post the output of:
```
cat /etc/fstab
```

dje

---

### Post by Swenghk on 2009-02-25
seth@SETH-LAPTOP:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda7
UUID=b5aa5f56-1e91-4c94-8e71-6135453b183f /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda8
UUID=be089fa5-d845-4a5e-939f-cf36338e9c88 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
seth@SETH-LAPTOP:~$

---

### Post by Swenghk on 2009-02-25
And I though Unmount Volume would screw up the partition?

---

### Post by Bölvaður on 2009-02-25
I am not sure why it is popping up on the desktop in the first place, could be release dependent. In my 8.10 I auto mount via fstab and have the fun mount points under Places &#8594; Removable Media (which will place an icon on the desktop when mounted)

If you dont want an icon on the desktop you have to mount the drive to a specific directory. If you mount it without picking any place then it will be placed on the desktop (I think).

From that you can see there are 2 options:

  1. setup your fstab (a text file) to auto mount your partitions to a good place (like /mnt/data)
  2. make an executable file that mounts your partitions (to something like /mnt/data)

Do you like one of those?
Or the third one... live with it.
I know that the desktop is supposed to be empty, but if the icons are only when you are using the partitions.. then I dont see too big problem with it.


*added*
according to your fstab then you do not have any other partitions (parts of your hard disk) mounted (connected) after bootup (when you turn on your computer into ubuntu)

(I saw some one that had problems with technical terms so Im adding these explanations.. sorry if it looks stupid)

---

### Post by Bölvaður on 2009-02-25
> **Swenghk said:**
> And I though Unmount Volume would screw up the partition?

It will not... it will just unmount it ^^ (disconnect it)

---

### Post by dje on 2009-02-25
strange fstab has no instructions to mount them. Are you mounting them manually or are they mounted when you log in. i would also recommend what Bölvaður suggests

dje

---

### Post by Swenghk on 2009-02-25
Alright, I did it. Thanks you guys!

---

### Post by Bölvaður on 2009-02-25
> **Swenghk said:**
> Alright, I did it. Thanks you guys!

Did what?
(others that are looking for similar problems may one day see this thread and hope to see the solution ;) )

---

