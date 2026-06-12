---
title: "Increasing the linux partition"
date: 2009-08-17
forum: New to Ubuntu
---

### Post by coldfusion1313 on 2009-08-17
Hi everyone, I just install Ubuntu on my HP Pavilion dv6000. The specs are 1.8GHz AMD Athlon 64, Nvidia GeForce 7150m, 2GB of RAM, and a 160 GB hard drive. I am loving every minute of Ubuntu. The reason I installed Ubuntu was that Windows Vista, which ran fine, was turned into a drone and my computer would randomly go to web pages. So I had the idea to backup all my stuff on my mom's computer then install Ubuntu and Vista again. But once I had installed Ubuntu and got all my drivers working I don't want to go back to Vista. I gave Ubuntu only 15gb of space but I want to give it a lot more, how do I do that.
Thanks, 
Mark

---

### Post by Schendje on 2009-08-17
I always use GParted (look for GNOME Partition Editor in Add/Remove). Works great for me. But if you want to enlarge the partition that's currently in use, I think you'll need to use the Ubuntu LiveCD (which already has GParted installed).

Simply boot up the LiveCD and navigate to System -> Administration -> GParted. Watch out with partitions though: do a full backup of your data first!

Welcome to Ubuntu by the way, good to hear you're liking it.:)

---

### Post by Finalfantasykid on 2009-08-17
This happened to me, as well as a lot of people(I Went from 16GB -> 32GB)

So, assuming you have an Ubuntu Live CD handy(It doesn't really matter which version), load it up, and once in the Live OS, then open GParted.

You probably remember this program when first installing Ubuntu, so it should be familiar.  But anyways, make sure that your swapdrive is 'unswapped' otherwise you probably won't be able to expand your partition(just right click the swap partition > unswap).  First resize your Windows Partition to whatever size you want(you might want to defrag your windows c drive a couple times first though to make everything go more smoothly).  Then you can expand your linux partition.

When I did this though, I ran into a small snag.  After expanding the Linux Partition, there was some error, I'm not sure why it showed up, but it resulted in Ubuntu not seeing the entire partition(I'm guessing it did not expand the filesystem to the rest of the partition).  I believe I fixed this by right clicking the linux partition and selection 'check'.

I hope I didn't miss anything :\

---

### Post by Schendje on 2009-08-17
All that sounds about right, but it's "swapoff" instead of "unswap" I believe. :)

---

### Post by Finalfantasykid on 2009-08-17
^Ah thanks for correcting me, that definitely sounds right.

---

### Post by coldfusion1313 on 2009-08-17
Thanks for all the help. I did not except this many replies in such a short time. :) 
> **Finalfantasykid said:**
> 
  But anyways, make sure that your swapdrive is 'unswapped' otherwise you probably won't be able to expand your partition(just right click the swap partition > unswap).  First resize your Windows Partition to whatever size you want.  Then you can expand your linux partition.



You lost me :confused:. What is the swapdrive?

---

### Post by Finalfantasykid on 2009-08-17
The swap drive/partition is where the OS starts writing to the harddrive when it starts to run out of ram.

It is possible that you do not have a swap drive, in which case you won't have to do anything with the swapoff stuff.

If you go to your gnome system monitor > Resources, you will see half way down your ram usage and swap usage.  If swap says '0 bytes (0.0%) of 0 bytes' or something like that, then you probably don't have a swap drive.

---

### Post by egalvan on 2009-08-17
> **Finalfantasykid said:**
> This happened to me, as well as a lot of people(I Went from 16GB -> 32GB)

Yessir, indeed. :)


> assuming you have an Ubuntu Live CD handy(**It doesn't really matter which version**), 
load it up, and once in the Live OS, then open GParted.


Actually, yes it does....
newer versions of gparted have more advanced features.
Some of these features are not back-wards compatible.

Examples....
support for newer file system types such as ext4, reiser4.
support for large inodes
non-destructive labeling of partitions


I always use the latest from gparted, or partedmagic LiveCD.

---

### Post by Schendje on 2009-08-17
[https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)

Basically, an extra (though small) partition Linux uses for stuff like hibernating.

It'll show up as a small pink/purple partition in GParted, next to your Ubuntu partition.

Thing is, when the LiveCD boots, it mounts the swap so it can use it (correct me if I'm wrong). When a partition is mounted, it can't be changed, so right-click on it and choose "swapoff" so it's not in use anymore. That way, you can change it all you like. :)

//Edit, or what FFK said. ;)

---

### Post by oldfred on 2009-08-17
There are some concerns that Vista is not happy with other partitioners. You should use the Vista partitioner to shrink the Vista partition. You should also defrag the Vista install a couple of times. If you never want to go back to Vista ignore this.

---

### Post by coldfusion1313 on 2009-08-17
I decides that I am not going to back to windows on this machine so I deleted my windows partition, not a problem because vista was not even activated. I now 133.97 GB of free space. How can I expand the Ubuntu partition.

---

### Post by Schendje on 2009-08-17
Right-click on it, then choose Resize/Move.

---

### Post by coldfusion1313 on 2009-08-17
What kind of file system should I make it?

---

### Post by Schendje on 2009-08-17
Isn't that already set? You only have to resize or move it, after all. What is it now?

//Edit: I meant right-clicking on the partition, not on the free space. You can either enlarge the partition Ubuntu is already installed on, or create a new partition in the free space.

---

### Post by Finalfantasykid on 2009-08-17
Just keep it the way it is, unless you are doing a complete reinstall, in which case you would probably want to use ext4.  If you change the filesystem, then you are probably ending up reformatting your partition(unless you really know what you are doing, in which case you can go from ext3 to ext4, and maybe some others).  But if you are simple resizing the partition, then you don't need to change what filesystem it is.

---

