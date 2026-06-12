---
title: "help me set my Fat32 drives Writeable!"
date: 2009-08-10
forum: New to Ubuntu
---

### Post by jadhav92 on 2009-08-10
With the helps of people here i have succesfully mounted my Fat32 drives in Ubuntu, but they seem to be in read-only format.

Is there any way i can mount my fat32 drives permanently and they are writeable too???

help me with this,

Thanks,
Rajesh

---

### Post by jadhav92 on 2009-08-10
guyzz.....someone in need of help:(

---

### Post by oldfred on 2009-08-10
I did this so long ago I do not remember all the details:
This the entry in my fstab which was prior to uuid's and then hand edited  to use uuid's.  I first created "share".
# before uuid  /dev/sda4 /home/fred/share vfat user,auto,fmask=0111,dmask=0000 0 0
UUID=46CD-C9B2 /home/fred/share vfat user,auto,fmask=0111,dmask=0000 0 0

I created "share" as a mount under my home directory and under ls -l
is shows this.
drwxrwxrwx 15 root root    16384 1969-12-31 18:00 share

So I must have changed permissions. I thought I was under fred not root but it still works? I probably did something like this without the chown command that I probably should have run.
sudo chown -R fred:fred /home/fred/new_directory 
sudo chmod -R 755 /home/fred/new_directory

---

### Post by jadhav92 on 2009-08-10
does anyone else remember the whole procedure....a correct one???

---

### Post by oldfred on 2009-08-10
from the terminal list your UUID's
blkid 
remember uuid and enter my line in previous post with your UUID and mount point
UUID=[COLOR=DarkRed]46CD-C9B2[/COLOR] [COLOR=DarkRed]/home/fred/share[/COLOR] vfat user,auto,fmask=0111,dmask=0000 0 0

gksudo gedit /etc/fstab

Correction the fmask and dmask set permissions, if you want the same use umask. fmask is files, dmask is directories, umask is both.
umask=000 sets the permissions of files and folders to 777 or rwxrwxrwx.

Edit to add:
to read new fstab
in terminal
sudo mount -a

---

### Post by fragos on 2009-08-10
Just bout an SDHC 8GB card and have run into this read only issue. That card is FAT32. I don't have the same issue with SD cards which are FAT16. I can see using FSTAB for hard drives but my case is removable storage on SD cards.

---

### Post by juanoleso on 2009-08-10
[[COLOR="Blue"]_https://help.ubuntu.com/community/AutomaticallyMountPartitions_[/COLOR]]("https://help.ubuntu.com/community/AutomaticallyMountPartitions")

Here is the page I always look at.

Find your fat32 partition if you don't know it with

```

sudo fdisk -l

```

Edit your fstab file:

```
gksudo gedit /etc/fstab
```

add the line below replacing /dev/hda1 with your fat32 partition.

> fstab example

So, to grant all users access to '/dev/hda1', which will be located at '/media/windows', and is of type 'vfat', the line added would be.

/dev/hda1   /media/windows   vfat   user,fmask=0111,dmask=0000   0   0

Then

```
sudo mount -a
```

is like pretending that the computer is starting up, so it will mount all the partitions in fstab.

```
sudo mount -avvv
```

will show all the debug information if it doesn't work the first time.

Hope this helps

---

