---
title: "Partitioning questions"
date: 2010-01-08
forum: New to Ubuntu
---

### Post by chrisinspace on 2010-01-08
I've been using Linux for a few years now, but I've usually gone with the automatic partitioning options when I do a new install.  Recently, I've been experimenting with custom partitions, like a **/home** partition.  

In doing some reading, I've noticed a practice that I don't fully understand. What are the advantages of creating a separate **/boot** partition?

Another question is, if you are setting up a machine to dual-boot multiple Linux distros, can they share the same swap or do you need a swap for each of them?

Finally, does the order that you create your partitions make a difference?  I typically create my root (**/**) partition first, then my swap, then any additional partitions, all from the beginning of the space.

---

### Post by juancarlospaco on 2010-01-08
All Linux can share the same Swap, if no Swap Linux boots anyways, but performance slowdown.

Order doesnt matter, Linux uses UUID to identify the partitions by default.

/boot is used with custom partition scheme, I.E. /boot and SoftRAID, /boot and Encrypted LVM

:)

---

### Post by amauk on 2010-01-08
Some BIOS's on older motherboards can only "see" the first 1024 cylinders of a disk
if you have a large disk and an ancient motherboard, a separate /boot is required for the BIOS to see, and execute the kernel

Also, separate /boot can come in handy if you regularly share kernels across different installs

for normal usage though, separate /boot it's not necessary

Yes, swap partitions can be shared across different installs

Order of partitions is not really important
(except if you do have a separate /boot for an old motherboard, in which case it needs to be at the start of the disk - within first 1024 cylinders)

---

### Post by juancarlospaco on 2010-01-08
Another example: 
when EXT4 still under alpha development you need to do an EXT3 /boot and then / using EXT4
I ear that you can do the same with BTRFS right now but not tested myself...

---

### Post by chrisinspace on 2010-01-08
Makes sense.  Thanks for your responses.

---

### Post by oldfred on 2010-01-08
If you are going to do multiple installs it may be worthwhile to add a data partition. You can share all you data even when you cannot share /home.

GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)
[http://www.howtoplaza.com/how-to-install-ubuntu-904-on-a-manually-created-partition](http://www.howtoplaza.com/how-to-install-ubuntu-904-on-a-manually-created-partition)
With add'l info on manually partitioning
[http://guvnr.com/pc/ubuntu-partition-planning/](http://guvnr.com/pc/ubuntu-partition-planning/)
[http://guvnr.com/pc/karmic-install-tutorial/](http://guvnr.com/pc/karmic-install-tutorial/)

---

