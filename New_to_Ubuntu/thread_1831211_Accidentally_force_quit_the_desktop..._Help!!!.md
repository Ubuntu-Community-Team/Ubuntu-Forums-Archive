---
title: "Accidentally force quit the desktop... Help!!!"
date: 2011-08-23
forum: New to Ubuntu
---

### Post by inlorfaze on 2011-08-23
I was trying to force quit chromium, but accidentally force quit the desktop!!! Every thing froze, so I had to shut it down. When I restarted it, the terminal came up with a bunch of stuff covering the screen. I don't know what to do. Help!!:(




P.S: I am running ubuntu 10.04 on an acer aspire 3690

---

### Post by androssofer on 2011-08-23
> **inlorfaze said:**
> I was trying to force quit chromium, but accidentally force quit the desktop!!! Every thing froze, so I had to shut it down. When I restarted it, the terminal cam with a bunch of random words. I don't know what to do. Help!!:(




P.S: I am running ubuntu 10.04 on an acer aspire 3690

so u boot up... then it loads up?

is it a black screen with some wrtting top left. and does it say (tty1) sumwer?

then ask for a login?

---

### Post by inlorfaze on 2011-08-23
Heres a picture: [http://ubuntuone.com/p/1CNR](http://ubuntuone.com/p/1CNR)

The acer boot screen shows up, then goes to a terminal and then I just dont know what to do.

---

### Post by inlorfaze on 2011-08-23
It doesn't ask for anything and the whole screen is filled.

---

### Post by bodhi.zazen on 2011-08-23
Boot a live CD and run fsck on your root partition.

---

### Post by inlorfaze on 2011-08-23
So... I put in a live cd. Do you want me to run the System Testing Application?

---

### Post by bodhi.zazen on 2011-08-23
> **inlorfaze said:**
> So... I put in a live cd. Do you want me to run the System Testing Application?

I do not know what you mean by "System Testing Application"

I suggest you boot an Ubuntu live (desktop) cd , open a terminal, and run fsck

```
fsck -y /dev/sdxy
```

where sdxy is your root partition , if you have a separate home run it on home as well.

---

### Post by Miljet on 2011-08-23
Hate to be the bearer of bad news, but I have had this exact problem twice in the last month and had to re-install both times. Here is a link to another poster with the same problem a couple of days ago. I believe in the end, he had to re-install also.
[http://ubuntuforums.org/showthread.php?t=1830465](http://ubuntuforums.org/showthread.php?t=1830465)

As best I could figure out, this has something to do with the partition becoming corrupted. Not the file system, but the partition itself.

---

### Post by bodhi.zazen on 2011-08-23
> **Miljet said:**
> Hate to be the bearer of bad news, but I have had this exact problem twice in the last month and had to re-install both times. Here is a link to another poster with the same problem a couple of days ago. I believe in the end, he had to re-install also.
[http://ubuntuforums.org/showthread.php?t=1830465](http://ubuntuforums.org/showthread.php?t=1830465)

As best I could figure out, this has something to do with the partition becoming corrupted. Not the file system, but the partition itself.

It may come to that, but ...

Start with fsck , then we would need to look at any error messages we are contending with.

Don't need to reinstall if we can fix it.

---

### Post by inlorfaze on 2011-08-24
hmm... I'm kinda new and I don't know what my root partition is named.):

---

### Post by bodhi.zazen on 2011-08-24
> **inlorfaze said:**
> hmm... I'm kinda new and I don't know what my root partition is named.):

You will have to mount them and look at them then.

```
sudo -i
mount /dev/sda1 /mnt
ls /mnt
umount /mnt

mount /dev/sda2
ls /mnt 
umount /mnt 

...
```

See also : [http://ubuntuforums.org/showthread.php?t=282018](http://ubuntuforums.org/showthread.php?t=282018)

---

### Post by Miljet on 2011-08-25
Looks like this thread died with no resolution.

---

### Post by pierreyy on 2011-08-25
hey... tell me more about ur system... is it a dual boot? wubi or normal? try to shutdown ur system properly

---

### Post by inlorfaze on 2011-08-30
normal

---

### Post by inlorfaze on 2011-09-01
ok, so I have 1 partition, just sda. When i tried to run a fsck its denied it and said```
Permission denied while trying to oped /dev/sda You must have r/w access to the filesystem or be root
```

I am unable to mount the Filesystem on the live cd, either.

---

### Post by bodhi.zazen on 2011-09-01
/dev/sda is not a partition, it is the entire hard drive.

/dev/sda1 would be a partition.

List your partitions with 

```
fdisk -l
```

If there are none, next step would then be to use testdisk to try to recover your partitions.

[http://ubuntuforums.org/showthread.php?t=282018](http://ubuntuforums.org/showthread.php?t=282018)

---

### Post by inlorfaze on 2011-09-09
ok it after putting in fdisk -l it says:

 DEVICE    boot         Start                End            Blocks   Id System
/dev/sda1   *                  1                6993        56165376  83 Linux
/dev/sda2                  6993              7296          2437121    5 Extended
/dev/sda5                  6993              7296          2437120   82 Linux swap / Solaris

---

### Post by bodhi.zazen on 2011-09-09
```
fsck -ay /dev/sda1
```

---

