---
title: "[SOLVED] Sharing a partition between two directories"
date: 2008-12-11
forum: New to Ubuntu
---

### Post by ukulele_ninja on 2008-12-11
On my mythbuntu setup, The way my main drive is mounted it has all my system files installed on a small 12gig partition which has run out of space. Meanwhile, I have put all my media onto the free space mounted to /var/lib/mythtv 

What is the command to share that free space with my system files without damaging any of the files in either directory?

---

### Post by nhasian on 2008-12-11
no sure what your trying to achieve but I think you have two options.  you can mount the free space in a directory in your main filesystem, or you can use the ln (link) command to make a symbolic link to another folder.

---

### Post by ukulele_ninja on 2008-12-11
I just want to allocate some additional hard drive space to my system partition because while trying to install apps and such it says ive run out of room.

---

### Post by mikewhatever on 2008-12-11
Try these two for freeing space.
sudo apt-get clean
sudo apt-get autoremove

---

### Post by Duck2006 on 2008-12-11
You may have to resize your partitions to get the space you need.
ie decrease the partition that has the space to spare and then add it to the partition that needs it.

[http://wiki.partedmagic.com/index.php/Using_GParted](http://wiki.partedmagic.com/index.php/Using_GParted)

Use parted magic or gparted to do this with.

---

### Post by ukulele_ninja on 2008-12-11
> **Duck2006 said:**
> You may have to resize your partitions to get the space you need.
ie decrease the partition that has the space to spare and then add it to the partition that needs it.

[http://wiki.partedmagic.com/index.php/Using_GParted](http://wiki.partedmagic.com/index.php/Using_GParted)

Use parted magic or gparted to do this with.

I have gparted installed and am willing to do this, but if i reduce space on my main storage partition will it corrupt anything on that partition? I guess this is what i needed to ask to begin with.

---

### Post by Titan8990 on 2008-12-11
> I have gparted installed and am willing to do this, but if i reduce space on my main storage partition will it corrupt anything on that partition? I guess this is what i needed to ask to begin with.

This is possible anytime you are making changes to partitions. Always back up your data prior to making these types of changes.

---

### Post by Duck2006 on 2008-12-11
Use the live cd of gparted or parted magic to do this with. It should not corrup your files, Just make sure you have backed up your data.

---

### Post by Titan8990 on 2008-12-11
> **Duck2006 said:**
> Use the live cd of gparted or parted magic to do this with. It should not corrup your files, Just make sure you have backed up your data.

[http://en.wikipedia.org/wiki/Murphy%27s_law](http://en.wikipedia.org/wiki/Murphy%27s_law)

---

### Post by ukulele_ninja on 2008-12-11
Alright, thanks guys!

---

