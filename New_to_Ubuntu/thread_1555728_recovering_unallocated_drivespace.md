---
title: "recovering unallocated drivespace"
date: 2010-08-18
forum: New to Ubuntu
---

### Post by mhanes_1 on 2010-08-18
I just deleted my Windows partition (after not booting it for two years) and now G Parted reports that there is 12 GB unallocated space.

This might sound dumb, but how do I recover that space for my Ubuntu system to use?

---

### Post by xircon on 2010-08-18
Use Gparted, create a new partition, format to ext4 and set a mount point.

---

### Post by mhanes_1 on 2010-08-18
so will this set up the space to be used in conjunction with my ext3 partition?

I was thinking I would like to increase the size of my current ext3.

Is there a relatively safe way to do that?
:-k

---

### Post by xircon on 2010-08-18
Yes, you can do that, are the two partitions next to each other?

---

### Post by mhanes_1 on 2010-08-18
yes, but the windows partition was on the computer first, and the empty space is now at the beginning of the hdd.

the drive is a small 40 GB on my laptop. I left it (windows)  there since this was my first successful foray into Linux.

---

### Post by xircon on 2010-08-18
So......

|Windows|root|swap|home|

Is that the general idea?  The only thing you have to watch out is screwing Grub up.  I am new to Grub2, I am an ex-Mandriva user, couldn't get my wireless card to work, so have been distro hopping till I found one that worked.

There is another thread about this running today:

[http://ubuntuforums.org/showthread.php?t=1555510&page=1](http://ubuntuforums.org/showthread.php?t=1555510&page=1)

Can I chicken out? (due to my lack of knowldege of grub2)

---

