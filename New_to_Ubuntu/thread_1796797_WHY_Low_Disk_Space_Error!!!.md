---
title: "WHY Low Disk Space Error!!?!?"
date: 2011-07-04
forum: New to Ubuntu
---

### Post by P-rench on 2011-07-04
I'm on the verge of madness right now trying to understand this. I* have searched all over the internet for why this annoying error keeps appearing. I have a wubi install on windows xp using 17gb. In the home folder I checked and had about 3 gigs left that I never use. Well at random ubuntu will just give me totally obscure low disk error messages telling me I have 800mb left or 21mb left then 300 mb and at the current moment I have 8mb left. Certainly can't make its mind up, thats for sure. This makes no sense to me as I have not added anything to the home folder or desktop or any of that. I dunno what the deal is but it's driving me up the wall and causing things not to work in ubuntu because apparently I'm all out of space. Does anyone have a solution for this?????

---

### Post by apollothethird on 2011-07-04
> **P-rench said:**
> I'm on the verge of madness right now trying to understand this. I* have searched all over the internet for why this annoying error keeps appearing. I have a wubi install on windows xp using 17gb. In the home folder I checked and had about 3 gigs left that I never use. Well at random ubuntu will just give me totally obscure low disk error messages telling me I have 800mb left or 21mb left then 300 mb and at the current moment I have 8mb left. Certainly can't make its mind up, thats for sure. This makes no sense to me as I have not added anything to the home folder or desktop or any of that. I dunno what the deal is but it's driving me up the wall and causing things not to work in ubuntu because apparently I'm all out of space. Does anyone have a solution for this?????

Depending on the size of your hard drive 3 gigs is a very small amount of work space for the OS.  I believe you should have about 10% of the drive capacity free for the OS to work properly.  wubi is probably responding to some of the problems you're having with your base OS.  3 gigs free might be a fair operating edge if your total drive capacity is 30 gigs, but if your drive capacity is 50 gigs 3 gigs free isn't sufficient for proper performance.

As far as wubi in general, it's okay to take a quick preview of Ubuntu.  But if you want Ubuntu in a reliable operating environment you should give it, it's own partition.  Otherwise, the annoyance you're describing here is just a sample of the type of annoyances you'll continue to face.

-- L. James

-- 
L. D. James
[EMAIL="ljames@apollo3.com"]ljames@apollo3.com[/EMAIL]
[www.apollo3.com/~ljames]("http://www.apollo3.com/%7Eljames")

---

### Post by drs305 on 2011-07-04
Do you have 3GB *left* or 3GB reserved for Wubi? 

Within a running Ubuntu, there are a few things that might be stealing your space: large log files in /var, undeleted Trash in your Trash bin *or root's* (it takes up space until you empty the bin, and root has it's own bin), and backups made to a folder in / rather than on a device *mounted* somewhere on /.

I wrote a guide on checking these issues and more. It was written for a normal installation, but can apply to Wubi installations as well. Keep in mind that if the space you reserved for Wubi is too small (e.g. you made it only 3GB), none of these will permanently solve the issue.
[http://ubuntuforums.org/showthread.php?t=1122670]("http://ubuntuforums.org/showthread.php?t=1122670")

---

### Post by P-rench on 2011-07-04
I have 17gb reserved for wubi and currently have 3gb free in the home folder.

---

### Post by aeiah on 2011-07-04
open a terminal and issue:
```

df -h

```
so we can have a clearer idea of your disk usage

---

### Post by P-rench on 2011-07-04
I did df -h and this is what I pulled up. 

Filesystem            Size  Used Avail Use% Mounted on
/dev/loop0             17G   15G  421M  98% /
none                 1005M  360K 1005M   1% /dev
none                 1005M   12M  994M   2% /dev/shm
none                 1005M  204K 1005M   1% /var/run
none                 1005M     0 1005M   0% /var/lock
none                 1005M     0 1005M   0% /lib/init/rw
/dev/sda1              98G   34G   65G  35% /host
/dev/sda2              56G   27G   29G  49% /media/Local Disc
/dev/sdb1             233G  227G  6.7G  98% /media/Local Disk

---

### Post by aeiah on 2011-07-04
code tags make it clearer ;)


```

Filesystem            Size  Used Avail Use% Mounted on
/dev/loop0             17G   15G  421M  98% /
none                 1005M  360K 1005M   1% /dev
none                 1005M   12M  994M   2% /dev/shm
none                 1005M  204K 1005M   1% /var/run
none                 1005M     0 1005M   0% /var/lock
none                 1005M     0 1005M   0% /lib/init/rw
/dev/sda1              98G   34G   65G  35% /host
/dev/sda2              56G   27G   29G  49% /media/Local Disc
/dev/sdb1             233G  227G  6.7G  98% /media/Local Disk

```

looks like your home folder hasnt got its own partition and uses root (/) - which has 421mb free.

any software you install will affect your disk space as well as any files you store in home. 

if you havent been installing a lot of software and havent copied lots of stuff to your home dir, it could be that your log files are filling up for some reason.

what does the output of this give you?
```

du -sh /var/log/

```

if this seems unusually large (say, over 1 gig), you could run it without the summarise flag to give you a breakdown:
```

du -h /var/log/

```

or list all files in your log:
```

ls -Rsh /var/log/

```

---

### Post by apollothethird on 2011-07-04
> **P-rench said:**
> I did df -h and this is what I pulled up. 

Filesystem            Size  Used Avail Use% Mounted on
/dev/loop0             17G   15G  421M  98% /
none                 1005M  360K 1005M   1% /dev
none                 1005M   12M  994M   2% /dev/shm
none                 1005M  204K 1005M   1% /var/run
none                 1005M     0 1005M   0% /var/lock
none                 1005M     0 1005M   0% /lib/init/rw
/dev/sda1              98G   34G   65G  35% /host
/dev/sda2              56G   27G   29G  49% /media/Local Disc
/dev/sdb1             233G  227G  6.7G  98% /media/Local Disk

It looks like you thought you had 3 gigs free on your Wubi, but in just the few minutes of the life of this thread the number appears to have chanced from 3 to 2 (looking at your /dev/loop0).  I would think that the OS is advising you that 98% of the capacity is time for a "Low Disk Space Error" flag, as per the namesake of this thread.

-- L. James

-- 
L. D. James
[EMAIL="ljames@apollo3.com"]ljames@apollo3.com[/EMAIL]
[www.apollo3.com/~ljames]("http://www.apollo3.com/%7Eljames")

---

### Post by Wim Sturkenboom on 2011-07-04
Look at that 'first' line; 98% used

Use **du** as shown below (the shown output gives you an example of what to expect) to find which directories take up a lot of space; eject any memory sticks and external HDs so you don't get confused.

```

root@webserver:~#  **du -h --max-depth=1 /**
3.3G    /usr
du: cannot access `/proc/3917/task/3917/fd/4': No such file or directory
du: cannot access `/proc/3917/fd/4': No such file or directory
0       /proc
12K     /tmp
11M     /etc
64K     /media
40K     /mnt
0       /sys
16K     /lost+found
140K    /root
4.0G    /home
4.0K    /srv
104M    /lib
13M     /sbin
36M     /var
2.5M    /dev
7.9M    /bin
4.0K    /opt
17M     /boot
7.5G    /
root@webserver:~#

```

PS use sudo; the example was taken from a system that has a normal root user

---

### Post by wildmanne39 on 2011-07-04
Hi, here is a guide for resizing wubi partitions.
[http://ubuntuforums.org/showthread.php?t=1625371](http://ubuntuforums.org/showthread.php?t=1625371)

---

