---
title: "&quot;Could not change permissions for&quot; message in Dolphin"
date: 2009-05-23
forum: New to Ubuntu
---

### Post by RyanVanDiemen on 2009-05-23
Hi, I`m a long time gnome user, but recently I switched to KDE on my desktop. The problem I need help with is that everytime I copy/move a file/folder to ntfs drive (I have a 320 GB drive I use for files that I want to have accessible also for win) Dolphin show error: "Could not change permissions for nameofthefile). If I wait until the copy of the folder is complete and then click ok, nothing happens, if I click ok, then Dolphin shows the same message for another file that`s being copied. This is not the end of the world, but it really bugs me... Anyone can help how to turn this message off completely?

---

### Post by Didius Falco on 2009-05-23
Hi,

Make sure you are a member of the "fuse" group. Open a Terminal and type  ```
sudo adduser ryan fuse
``` log out and back in.

If that doesn't fix it, let's have a look at your /etc/fstab file.

Regards,

Didius

---

### Post by RyanVanDiemen on 2009-05-23
No that didn`t help.

Here`s the output from my fstab file:

```
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda3 during installation
UUID=cd366a05-bf46-4663-9fc8-7eec5d9a5b97 /               ext4    relatime,errors=remount-ro 0       1
# /mnt/toshiba was on /dev/sdb1 during installation
UUID=9EB0FB07B0FAE525 /mnt/toshiba    ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /mnt/windows was on /dev/sda1 during installation
UUID=AAF85208F851D365 /mnt/windows    ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# swap was on /dev/sda2 during installation
UUID=f3800e09-59fe-4b43-bfbb-670b2d6c3eca none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

```

the drive I`m talking about is /dev/sdb1 mounted at /mnt/toshiba, but it`s the same with windows partition /dev/sda1

---

### Post by Didius Falco on 2009-05-23
Open a Terminal and type ```
sudo apt-get install ntfs-3g
```. After it's installed (or told you that the latest version is already installed), change the fstab lines for those to partitions from "ntfs" to "ntfs-3g".

Here is a sample listing from my own fstab:

 ```
/dev/sda8                                  /media/FileStorage  ntfs-3g      defaults                    0  0  
```

With ntfs-3g, I don't need any permissions other than the "defaults" setting.

Regards,

Didius

---

### Post by RyanVanDiemen on 2009-05-23
I had the latest version installed but changing /etc/fstab didn`t help either (I restarted before trying to copy the file). 

Any other ideas?

---

### Post by RyanVanDiemen on 2009-05-25
I did search on web a lot but didnt find any solution. I cant believe Im the only one with this issue... Any idea?

---

### Post by [deXter] on 2010-01-03
Sorry for bumping an old thread, but has anyone come across a solution for this problem yet?

---

### Post by mankmonjre on 2010-01-15
I am facing the same problem on karmic. I am unable to find anything useful on the web related to this. Has anyone found a solution yet?

---

### Post by aniketvb on 2010-03-16
even I am having same problem. Please we need a solution fast

---

### Post by palanteer on 2010-10-01
I just add my group and user ids to /etc/fstab, and it's work!
Look:
```
/dev/sda3       /win            ntfs    utf8,umask=000,**uid=1000,gid=1000** 0       1
```Don't forget to:
```
sudo umount /win
sudo mount -a
```

---

### Post by minoo1 on 2010-11-28
> **palanteer said:**
> I just add my group and user ids to /etc/fstab, and it's work!
Look:
```
/dev/sda3       /win            ntfs    utf8,umask=000,**uid=1000,gid=1000** 0       1
```Don't forget to:
```
sudo umount /win
sudo mount -a
```

This really hellped ! thanX a lot

---

### Post by mo.mashi on 2011-01-12
> **palanteer said:**
> I just add my group and user ids to /etc/fstab, and it's work!
Look:
```
/dev/sda3       /win            ntfs    utf8,umask=000,**uid=1000,gid=1000** 0       1
```Don't forget to:
```
sudo umount /win
sudo mount -a
```


Dude you f-ing ROCK!!! It works!!! You don't know how much of a bane you have lifted from my existence!!

---

### Post by theToolman on 2011-06-30
Hey guys, just a slight refinement on your solution;


```
UUID=7A1F8A7658B88888 /media/twinTerror ntfs    defaults,umask=007,uid=1000,gid=46 0       0
```

Leave the gid @ 46, which is your plugdev group (check /etc/group if you like) and set the umask for user/group rwx as above.  

So in my case everything is mounted toolman:plugdev, and dolphin doesnt alert with a permission problem.  

It means that any other user in the plugdev group can use the drive, although they will still get the annoying warning..

---

