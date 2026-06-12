---
title: "Disk Usage Analyzer...wrong?"
date: 2009-02-17
forum: New to Ubuntu
---

### Post by JustANewb on 2009-02-17
Weird situation...

I ran the disk usage analyzer because I thought that maybe the amount of free space that shows at the bottom of Nautilus was incorrect somehow but the number is correct.  Here's the problem though...

My amount of space used in / is only 30.x g while it shows that I have used 74.x g.  where is my 40g hidding?

I have attached a pic so you can see what I mean...


Edit:  Ubuntu is the only thing installed on this hard drive if that matters at all.  I have windows on it's own hard drive...

---

### Post by cariboo on 2009-02-17
The Disk Usage Analyzer also include the total of the gvfs too. the best way in my opionion to check disk usage it to open a terminal and type:

```
df -h
```

You should see an output that looks something like this:

```
 df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sdb2             5.8G  3.7G  1.9G  66% /
tmpfs                 994M     0  994M   0% /lib/init/rw
varrun                994M  112K  994M   1% /var/run
varlock               994M     0  994M   0% /var/lock
udev                  994M   68K  994M   1% /dev
tmpfs                 994M     0  994M   0% /dev/shm
lrm                   994M  2.4M  992M   1% /lib/modules/2.6.28-7-generic/volatile
/dev/sdb4             143G   44G   92G  33% /home
/dev/sda1             151G   88G   57G  61% /home/storage
```

Jim

---

### Post by Paqman on 2009-02-17
Try running the disk analyzer as root:
```

gksu baobab

```
There might be some root-owned files that aren't being counted.

---

### Post by JustANewb on 2009-02-17
Thanks for these pointers.  I'll check back later when I am able to test these ideas at home...

---

### Post by drs305 on 2009-02-17
You can turn off the gvfs information if it is displayed (seemingly doubling your disk space) via baobab/DUA's Edit, Preferences and unticking .gvfs

---

### Post by Coreigh on 2009-02-17
Mine does that too. Because I have network mounted drives and the total disk space used is more than the size of the partition my / filesystem.
Seems like a bug to me.

Baobab 2.20.0.1 on  Ubuntu 8.04.2, kernel 2.6.24-23-generic

---

### Post by JustANewb on 2009-02-17
Well.  Its still showing a really high usage.  I just deleted some videos (whole dvds) I had on my system and that's why its lower now...  But still, I don't think I have used 55g...

And...I figured out where it was.  It was tucked away in root's /.local/share/trash.  Is there any way to delete that without having to ```
sudo nautilus
```?

Thanks Paqman for pointing that out to me.

---

### Post by jerome1232 on 2009-02-17
Well that's where files get moved to when you delete things as the root user (using gksu nautilus).

If you are going to be deleting files in a root nautilus try holding shift when you press delete, this bypasses the trash.

---

### Post by JustANewb on 2009-02-17
I'll through around my thanks and solve this thread when the options come back...

---

### Post by JustANewb on 2009-02-17
> **jerome1232 said:**
> Well that's where files get moved to when you delete things as the root user (using gksu nautilus).

If you are going to be deleting files in a root nautilus try holding shift when you press delete, this bypasses the trash.

Thanks.  I couldn't figure out why, for the life of me, I would have ever deleted anything as root, but I remember what it was now.  I did a backup using Keep or something like that and I didn't have permissions on the folder it was stored in so I sudo nautilus'd into it...

---

