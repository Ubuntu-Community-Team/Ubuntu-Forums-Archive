---
title: "Deleted file still occupies space"
date: 2009-07-19
forum: New to Ubuntu
---

### Post by Jacko77 on 2009-07-19
G'day all,

The problem started when I was trying to extract (or convert?) a dmg image into a img file, using dmg2img. That was going all fine, until I ran out of disk space.

So, I had this 9Gb img file, which wasn't the complete dmg file, so I figured to delete it.
Hit the delete key, and it was gone I thought.

Except, it still occupies that 9-odd Gb on the filesystem.

Disk Usage Analyzer says the root is only using 2.1GB, but I'm still using 11.8GB.. So, I have no idea where the file is, or what's going on.

I've tried searching for all *img files, searching for all files over 1GB, but to no avail.

Also tried finding all Trash folders, and have removed both of them (One in root, and one under my username), but it still says the space is being used.

I'm not sure what else to do.

Any help would be appreciated.

Cheers.

---

### Post by Celauran on 2009-07-19
You can use du to find out where the usage is.

```
sudo du -sh /*
```

Then drill down from there.

---

### Post by The Tronyx on 2009-07-19
You can find files larger than the size you wish to search for by using the find command.

You might wish to use something like 
```

find / -size +10240000c -exec du -h {} \; 

```

Which will look for files over 10 MB or
```

find / -type f -size +1024k

```

---

### Post by Jacko77 on 2009-07-19
> **Celauran said:**
> You can use du to find out where the usage is.

```
sudo du -sh /*
```Then drill down from there.

I tried this, and root is only using 2.1GB, and /usr is using 1.7GB of that.
So unless I'm not using du right, where could 9GB be?

> **The Tronyx said:**
> You can find files larger than the size you wish to search for by using the find command.

You might wish to use something like 
```

find / -size +10240000c -exec du -h {} \; 

```Which will look for files over 10 MB or
```

find / -type f -size +1024k

```

I also tried this, but the largest file is no bigger than 40M.

Could du just have any error?

---

### Post by Celauran on 2009-07-19
All the tools you've used seem to show that file as gone. What's making you think different?

---

### Post by Jacko77 on 2009-07-19
> **Celauran said:**
> All the tools you've used seem to show that file as gone. What's making you think different?
Because after I first deleted it, and still after using the tools I used in my first post, I still got errors saying my disk was full. I wasn't able to save a text doc, or the chat logs in pidgin.

Also, because in the gui of disk usage,  it tells me "Total filesystem capacity: 22.9GB (Used: 11.8GB available: 11.1GB)

(I have free space now, because somehow I managed to delete the original .dmg file I was trying to extract.. This is why I'm so confused, because I was able to delete this file, but not the img file)

I want to believe it's gone, but it just doesn't seem it.

---

### Post by The Tronyx on 2009-07-19
What is the output of 'df -h'?

---

### Post by Jacko77 on 2009-07-19
> **The Tronyx said:**
> What is the output of 'df -h'?

```
Filesystem            Size Used Avail Use% Mounted on
/dev/sdb1              23G   12G   10G  55% /
tmpfs                 502M     0  502M   0% /lib/init/rw
varrun                502M  108K  502M   1% /var/run
varlock               502M     0  502M   0% /var/lock
udev                  502M  216K  502M   1% /dev
tmpfs                 502M  128K  502M   1% /dev/shm
lrm                   502M  2.4M  499M   1% /lib/modules/2.6.28-11-generic/volatile
overflow              1.0M   16K 1008K   2% /tmp
```

---

### Post by The Tronyx on 2009-07-19
Hi Jacko77.  And next, to what directory did you extract this image file?

---

### Post by halitech on 2009-07-19
whats the output of ```
df
```

according to this [color="red"]"Total filesystem capacity: 22.9GB (Used: 11.8GB available: 11.1GB)[/color] you have 11.1gig free, question is where is the free space

---

### Post by Jacko77 on 2009-07-19
I extracted the file in /.
(Which is root, if I've gathered that much so far)

---

### Post by halitech on 2009-07-19
but looking at your output, you don't have a seperate /home partition so it could be anywhere on the drive.

for example here is mine with a seperate /home partition
```
daryl@debian:~$ df
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda1             28834716   4046888  23323104  15% /
tmpfs                   901160         0    901160   0% /lib/init/rw
udev                     10240       100     10140   1% /dev
tmpfs                   901160         0    901160   0% /dev/shm
/dev/sda2            123039800  24368660  92421052  21% /home
/dev/sdc2            302382416 171244184 115778084  60% /home/daryl/storage
/dev/sdb1            115377640  59468244  50048484  55% /home/daryl/120gigdrive

```

---

