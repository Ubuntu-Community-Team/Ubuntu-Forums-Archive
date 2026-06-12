---
title: "How to identify HDs in software raid"
date: 2010-01-07
forum: New to Ubuntu
---

### Post by down_shift on 2010-01-07
This might come out as a complete noob question but..

I'm planning on setting up a 4x Hd raid5 array.
Now if one drive were to die, how would I know which drive to pull out and replace?

Should I be labeling the outside of each drive? And if so, how would I go by finding out which drive is which?


Thanks

---

### Post by firefly2442 on 2010-01-07
Not really a beginner question but... :)

If the drives are all different sizes then it should be pretty easy as when one fails you can just use the "fdisk -l" listing or another tool to see which one has failed and then remove it.

The mdadm tool will probably also come in handy.  Here's a couple links (Google will find more).

[http://www.review-ninja.com/2009/05/software-raid-raid-arrays-mdadm-on.html](http://www.review-ninja.com/2009/05/software-raid-raid-arrays-mdadm-on.html)

[http://docs.hp.com/en/5991-7402/ch21s04.html](http://docs.hp.com/en/5991-7402/ch21s04.html)

Also, when you do the setup, I don't believe you can put the /boot partition on the software RAID, this will have to be it's own separate small partition.  Everything else however can be on the RAID.  *Does Google search and comes back*  OK, I may be wrong about this.  It looks like it might be possible to have /boot partitions on multiple drives and then configure GRUB to set the order of drives to boot off.  Here's another excellent link:

[http://tldp.org/HOWTO/Software-RAID-HOWTO.html](http://tldp.org/HOWTO/Software-RAID-HOWTO.html)

Also, just so you know, you'll need to use the "alternate" CD for Ubuntu as this is the one that has the drivers and setup for software RAID (the regular "desktop" Ubuntu CD won't work).  I know it can do software RAID levels 0 or 1 as I've used this before but I'm not sure if it has the option for 5.  You may want to check on this.

Anyway, good luck, hope this gets you started at least. :)

---

### Post by Fcon_Vpro on 2010-01-10
There are a lot of different ways to do this and it will depend on your own setup, especially if your system has sata and IDE drives, etc. So im just going to do a quick run down to show you.

Im making these assumptions:
You are using equal sized SATA drives for your raid5
You are going to use MDADM to create the raid array

Solution: Check on your motherboard or your motherboard manual as it should list the order of your sata ports there. Ubuntu will place these drives in the same order ie. sata1 = /dev/sda; sata2 = /dev/sdb; etc
If you go into your motherboard bios, it will also list your drive order according to what is plugged into sata1, sata2, sata3, etc.

If you open up terminal (applications - accessories - terminal), type "sudo fdisk -l" (small/lowercase L), this will list all your drives and partitions.

So to be safe label your drives accordingly(or you will have to follow from the sata cable back to the drive) so that when you call up something like "mdadm --detail /dev/md0", it will tell you which drive is faulty and you will know exactly which drive to change.

Any questions?

This is a good guide for setting up your raid5: [http://bfish.xaedalus.net/2006/11/software-raid-5-in-ubuntu-with-mdadm/](http://bfish.xaedalus.net/2006/11/software-raid-5-in-ubuntu-with-mdadm/)

---

