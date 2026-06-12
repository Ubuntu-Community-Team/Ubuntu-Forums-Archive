---
title: "Is disk partitioning necessary?"
date: 2009-08-03
forum: New to Ubuntu
---

### Post by ovroniil on 2009-08-03
When I was using Windows I always partitioned my disk into at least two parts. In one parts the Windows was installed and the other part(s) contained my files, songs, videos, games etc. I did that because within a cycle of every six or seven months I had to re-install Windows (other wise the performance would become degraded). So that other parts of the hard disk did not face any problem of loosing any important data.

I am now using Ubuntu. Do I need to partition my harddisk for the same reason? Or is it really necessary to partition my hard drive? Is there any benefit of doing that?

---

### Post by 3rdalbum on 2009-08-03
> **ovroniil said:**
> When I was using Windows I always partitioned my disk into at least two parts. In one parts the Windows was installed and the other part(s) contained my files, songs, videos, games etc. I did that because within a cycle of every six or seven months I had to re-install Windows (other wise the performance would become degraded). So that other parts of the hard disk did not face any problem of loosing any important data.

I am now using Ubuntu. Do I need to partition my harddisk for the same reason? Or is it really necessary to partition my hard drive? Is there any benefit of doing that?

You can run Ubuntu on one single partition, but if you ever want to reinstall Ubuntu for any reason (or install a different distribution) you would lose the contents of your home directory.

Putting /home on a different partition does mean that the corruption of your / partition won't usually affect the contents of your home directory, but happily it's rare to have such corruption anyway.

---

### Post by Moop on 2009-08-03
You don't need to worry about Ubuntu degrading over time. However creating a separate partition for your /home directory will have the same effect as your 2nd partition in windows did. You would be able to reinstall and save your settings and data.

---

### Post by andrew.46 on 2009-08-03
Hi ovroniil,

> **ovroniil said:**
>  Or is it really necessary to partition my hard drive?

You will get so many different answers to this question :-). I will admit that I am so lazy that I only make 2 partitions, one for swap and one for everything else. I backup regularly and once a year or so wipe the lot and reinstall. But this is a very lazy way to do it...

Andrew

---

### Post by credobyte on 2009-08-03
Personally, I don't see a reason why I should split my drive into smaller partitions ( in case if I need to backup, I've another PC in a local network ).

---

### Post by wizard10000 on 2009-08-03
I think it's necessary but as andrew said you'll get a lot of different answers.

I always put /home on its own partition so that I can reload the OS (or add another Linux distribution to the same hard drive) without jumping through hoops to reload all my personal stuff.

If I'm building a server I normally put /var on its own partition to keep a runaway process from writing enough logfiles to bring the server down.  Some people put /opt or /tmp on a separate partition but I've never felt the need.

I used to use a separate /boot partition but recovery tools have gotten so good there's been no need for me to do this for several years.

---

### Post by jerome1232 on 2009-08-03
Personally I only use multiple partitions with LVM. That way I can start the partitions small and grow them on the fly as needed.

Personally the main advantage I see to using multiple partitions is to use different file systems/file system options that are optimized for the tasks to which the partition will be put to use for.

---

### Post by Psicolonia on 2009-08-03
even though there are many different answers, most people would agree that creating a swap partition is a good idea. If you want to separate your /home for updates of new distros, etc, that's just fine. Personally I use a third partition for /boot. Most people would say that's not necessary for you. I however use a disk encryption tool and I need my grub on an unencrypted partition (because I have another encrypted OS only).

so I would say:
/
/home
swap

since you may have 4 primary partitions you don't need top create extendend ones, so, no logic extended is needed.

---

### Post by ovroniil on 2009-08-04
Thanks everyone for taking part. I am gonna divide my hard disk as 

/
/swap
/home

---

