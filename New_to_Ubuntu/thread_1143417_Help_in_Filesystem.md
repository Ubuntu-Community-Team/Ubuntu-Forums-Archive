---
title: "Help in Filesystem"
date: 2009-04-29
forum: New to Ubuntu
---

### Post by llemm on 2009-04-29
Hi,

I Have been using Ubuntu for some time now I am using 8.10 since January. I just need some help in my /home Filesystem (/dev/sda7) it is getting full and I have a spare Filesystem (/dev/sda3). Im just wondering If I could somehow use that /dev/sda3 Filesystem free space to add it to /home. or can I mount two Partition for one /home? I have been downloading lately thats why my /home gets filled quickly. 

and here is my Filesystems Structure in case you will need it. 


rommell@rommell-desktop:~$ df -k
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda11             6728280   3105292   3281208  49% /
tmpfs                  1490532         0   1490532   0% /lib/init/rw
varrun                 1490532       104   1490428   1% /var/run
varlock                1490532         4   1490528   1% /var/lock
udev                   1490532      2844   1487688   1% /dev
tmpfs                  1490532        12   1490520   1% /dev/shm
lrm                    1490532      2004   1488528   1% /lib/modules/2.6.27-11-generic/volatile
/dev/sda7              9614116   6527024   2598720  72% /home
/dev/sda9              2885780     70016   2669176   3% /tmp
/dev/sda10             4806904    140992   4421728   4% /usr/local
/dev/sda8              4806904    663316   3899404  15% /var
/dev/sda5             81923432  67665204  14258228  83% /media/New Volume
/dev/sdb1             19944665  17446114   2498551  88% /media/disk
/dev/sda3             10555040    157388   9861484   2% /media/NewVol


I am Downloading JJ now and some movies through Torrents and I am hitting 160Kbps and I believe this will be filled very soon

^_^

---

### Post by fornix on 2009-04-29
You could mount your spare filesystem onto a folder inside your home filesystem. That way you would end up with more space

---

### Post by llamabr on 2009-04-29
This could be even more simply achieved with a symlink, and a folder in your home dir.

---

### Post by kk0sse54 on 2009-04-29
If you don't care about the data on your spare partition (or you could just back it up) you could delete /dev/sda3 using a liveCD such as Ubuntu and Gparted, and then expand your home partition so you have more space.

---

### Post by llamabr on 2009-04-29
Note, though, that even in the best of circumstances, resizing your home dir is likely to destroy all of your data.  make backups.

And, I'm not an expert here, but I would think you could do this without a livecd.

---

### Post by steve101101 on 2009-04-29
> **llamabr said:**
> Note, though, that even in the best of circumstances, resizing your home dir is likely to destroy all of your data.  make backups.

And, I'm not an expert here, but I would think you could do this without a livecd.

+1 backup before you change partitions or you will regret it when all your data gets corrupted.

---

### Post by mkoehler on 2009-04-29
You can't actually modify partions while they are mounted.  This is why you need to be running a live cd of ubuntu or the gparted live cd.

---

### Post by llemm on 2009-04-30
> **fornix said:**
> You could mount your spare filesystem onto a folder inside your home filesystem. That way you would end up with more space

Im Gonna Try this first

---

### Post by llemm on 2009-04-30
> **llamabr said:**
> Note, though, that even in the best of circumstances, resizing your home dir is likely to destroy all of your data.  make backups.

And, I'm not an expert here, but I would think you could do this without a livecd.

Im gonna try to use symlink first. Im afraid of resizing after reading this. Hehehehe.

---

### Post by llemm on 2009-04-30
Hi Fornix

I tried to create a symbolink link in my /dev/sda3 using this instruction
[http://www.tech-recipes.com/rx/17/create_a_symbolic_link_in_unix_solaris_linux/](http://www.tech-recipes.com/rx/17/create_a_symbolic_link_in_unix_solaris_linux/)
but before that I formatted /dev/sda3 to fat32 because in ext3 I do not have a permission but I think its not important what type I use.

This is the Log of what I did


rommell@rommell-desktop:~$ df -k
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda11             6728280   3105292   3281208  49% /
tmpfs                  1490532         0   1490532   0% /lib/init/rw
varrun                 1490532       108   1490424   1% /var/run
varlock                1490532         4   1490528   1% /var/lock
udev                   1490532      2844   1487688   1% /dev
tmpfs                  1490532        12   1490520   1% /dev/shm
lrm                    1490532      2004   1488528   1% /lib/modules/2.6.27-11-generic/volatile
/dev/sda7              9614116   6722808   2402936  74% /home
/dev/sda9              2885780     70016   2669176   3% /tmp
/dev/sda10             4806904    140992   4421728   4% /usr/local
/dev/sda8              4806904    663332   3899388  15% /var
/dev/sda5             81923432  67665204  14258228  83% /media/New Volume
/dev/sdb1             19944665  17446114   2498551  88% /media/disk
/dev/sda3             10712904         8  10712896   1% /media/disk-1
rommell@rommell-desktop:~$ cd /media/disk-1
rommell@rommell-desktop:/media/disk-1$ ls
rommell@rommell-desktop:/media/disk-1$ ln -s /media/disk-1 /home
ln: creating symbolic link `/home/disk-1': Permission denied
rommell@rommell-desktop:/media/disk-1$ sudo  ln -s /media/disk-1 /home
rommell@rommell-desktop:/media/disk-1$ df -k
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda11             6728280   3105292   3281208  49% /
tmpfs                  1490532         0   1490532   0% /lib/init/rw
varrun                 1490532       108   1490424   1% /var/run
varlock                1490532         4   1490528   1% /var/lock
udev                   1490532      2844   1487688   1% /dev
tmpfs                  1490532        12   1490520   1% /dev/shm
lrm                    1490532      2004   1488528   1% /lib/modules/2.6.27-11-generic/volatile
/dev/sda7              9614116   6723424   2402320  74% /home
/dev/sda9              2885780     70016   2669176   3% /tmp
/dev/sda10             4806904    140992   4421728   4% /usr/local
/dev/sda8              4806904    663332   3899388  15% /var
/dev/sda5             81923432  67665204  14258228  83% /media/New Volume
/dev/sdb1             19944665  17446114   2498551  88% /media/disk
/dev/sda3             10712904         8  10712896   1% /media/disk-1

I dont see any improvement in my /home. but will it automatically saved to /dev/sda3 when I save something?

Thank you very much for the reply

---

### Post by CatKiller on 2009-04-30
This command is broken.

> **llemm said:**
> 
rommell@rommell-desktop:/media/disk-1$ sudo  ln -s /media/disk-1 /home


Especially because you've formatted that partition as FAT, which is insufficient for your purposes. You've replaced all your users' Home folders with whatever was on that partition, and FAT can't handle permissions. Or symlinks.

What you probably wanted to do was something like ```
ln -s /media/disk-1 /home/rommel/storage
```

I'm kind of surprised that anything is still working at all. You might still be able to remove your symlink and re-mount your /home partition though.

---

### Post by llemm on 2009-05-06
> **CatKiller said:**
> This command is broken.



Especially because you've formatted that partition as FAT, which is insufficient for your purposes. You've replaced all your users' Home folders with whatever was on that partition, and FAT can't handle permissions. Or symlinks.

What you probably wanted to do was something like ```
ln -s /media/disk-1 /home/rommel/storage
```

I'm kind of surprised that anything is still working at all. You might still be able to remove your symlink and re-mount your /home partition though.



Thanks CatKiller 

I am at work right now. But I will gonna do that later at home. As a workaround I moved some Files to a spare Filesystem that is not in used.

I will update this thread on whatever happens

Thanks

---

