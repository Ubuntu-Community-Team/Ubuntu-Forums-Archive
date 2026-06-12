---
title: "How do I make more space on the / drive?"
date: 2009-01-01
forum: New to Ubuntu
---

### Post by ah pook on 2009-01-01
I'm running out of room on a 40 g drive i use for /. I've removed all my stuff from my /home directory, but still am sitting at 96% used. I've also  got
an 80 g, a 120 g, and a 160 g installed in the system; is there some way i can repartition one of the others and mount it to /?

any ideas would be most helpful...


Happy New Year...

---

### Post by ajcham on 2009-01-01
> **ah pook said:**
> I've removed all my stuff from my /home directory, but still am sitting at 96% used.


Have you emptied the trash?

---

### Post by drs305 on 2009-01-01
Check out this HOWTO:
[Disk Full? - Check Your Trash Bin(s)]("http://ubuntuforums.org/showthread.php?t=898573")

It started out to discuss hidden trash files but expanded to cover other places to look for space 'hogs': trash, apt packages, misplaced backup files, large log files, etc.

You can use gparted to resize partitions. If you run the following it can give us an idea of what kind of space you have:
```

df -Th

```

---

### Post by stderr on 2009-01-01
Well, you can mount one of them to a directory under /. For example:

```
sudo mount /dev/sdb1 /mntpt
```
```
sudo mount /dev/sdc2 /media/myDrive
```

Where /dev/xxxx is the partition you want to mount. The second directory (the one to mount to) must already exist.

I always find the disk usage analyser to be a very useful tool in discovering where my disk space has gone. Access it via Applications -> Accessories -> Disk Usage Analyser. Alternatively run it with Alt+F2, "baobab".

---

### Post by ah pook on 2009-01-01
That's just what I needed! Thanks!

---

### Post by nemilar on 2009-01-01
I agree with the previous posts; use the disk analyser and try to find out what's taking up all the space.  Optionally, if you prefer the commandline, you can use:


```
sudo du -hcs /*
```

Find which directory is the largest, enter that, and repeat.  If you find that /var looks suspiciously large, for example: 

```
sudo du -hcs /var/*
```

---

### Post by kristopher.ives on 2009-01-01
The Disk Usage Analyzer will tell you what parts of the drive are using the most disk space. If you're a developer I noticed that any Java docs take around 300Mb, so I was using a few gig for multiple Java VMs and tools.

Also most of the stuff in /usr/share/doc is very bloated and often worthless. It's hard to find and when you do find it usually is in a bad bloated format.

Cheers,
Kris

---

### Post by hyper_ch on 2009-01-02
you should also erase all the downloaded .debs during updates:

```

sudo apt-get clean

```

And as the poster above said to mount in /media/xxx

You could also mount it in some place else... e.g. if you have a lot of videos in your home folder or music, you could use that bigger partition to make a seperate /home folder or maybe just /home/USER/Music or whatever :)

---

