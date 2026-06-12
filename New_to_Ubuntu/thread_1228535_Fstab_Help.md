---
title: "Fstab Help"
date: 2009-08-01
forum: New to Ubuntu
---

### Post by Darksmac on 2009-08-01
hey guys if any one can give me any advice please help me out

setup:
i setup a dualboot system vista/xubuntu i have beeen trying to get the xubuntu os to recognize the ntfs partition as well as a fat32 swap partiton that i have set up

here is my list of partitons:
darksmac@Darksmac-laptop-xubuntu:~$ ls -l /dev/disk/by-uuid
total 0
lrwxrwxrwx 1 root root 10 2009-07-31 17:31 166d09ec-787a-4e74-8c3b-c9cf27e3a755 -> ../../sda3
lrwxrwxrwx 1 root root 10 2009-07-31 17:31 4a1210dc-5137-42b1-8dc8-8e08dff3811c -> ../../sda4
lrwxrwxrwx 1 root root 10 2009-07-31 17:31 B674BD4874BD0BDD -> ../../sda1
lrwxrwxrwx 1 root root 10 2009-07-31 17:31 E6C2-2D7F -> ../../sda2

So just so you know here is my fstab:

# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda4 during installation
UUID=4a1210dc-5137-42b1-8dc8-8e08dff3811c /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sda3 during installation
UUID=166d09ec-787a-4e74-8c3b-c9cf27e3a755 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
UUID=B674BD4874BD0BDD       /media/disk1 ntfs                    defaults 	  0	  0
UUID=E6C2-2D7F      /media/disk2     vfat                    defaults	  0 	  0


Thank you for any advice!

---

### Post by doas777 on 2009-08-01
I think the problem is your uuid for the ntfs disk. it's too short. I usually address ntfs by /dev/sdXY notation for exactly that reason.

good luck

---

### Post by sisco311 on 2009-08-01
And what's your question? The fstab entries are ok.

You have to create the mount points:
```
sudo mkdir /media/disk1
sudo mkdir /media/disk2
```

You may also want to set the owner and permissions:
```
UUID=B674BD4874BD0BDD /media/disk1 ntfs defaults,uid=**username**,dmask=0027,fmask=0137 0 0
UUID=E6C2-2D7F /media/disk2 vfat defaults,uid=**username**,dmask=0027,fmask=0137 0 0
```

You can also try PySDM:
[thread=872197]GUI Fstab Editing with PySDM[/thread]

---

### Post by dennisntstar on 2009-08-01
Try
/dev/sda1       /media/disk1    ntfs    defaults        0       0
The uuid also works for me.By the way does /media/disk1 exist?.You should create the /media/disk1 directory yourself.It is not created automatically.

---

### Post by Darksmac on 2009-08-01
Thank you all of you guys. this has solved my problem i just copied the 2 lines from sisco311 as well as created the directories and it worked both ways using the uuid as well as the /dev/sdXY method i haven't tried it with out permissions but it worked so i wont break it 

Thanks again guys for the quick response.

---

