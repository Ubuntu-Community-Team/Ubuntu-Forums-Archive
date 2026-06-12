---
title: "Installing on an external drive, will it wipe out the contents?"
date: 2009-04-24
forum: New to Ubuntu
---

### Post by medebe on 2009-04-24
I am an absolute noob/rookie at installing Ubuntu.  Win XP pro is my standard operating system on a Dell Dimension 4600.  I copied it to CD and, after it wouldn't boot off the CD drive, I opened it from the CD and installed a bootable piece of something or the other.  I decided to install it on an external hard drive where I store tons of other folders/pics, etc.  However, at stage 7 of 7, right before final install, it warned me that everything on the partition I created (didn't know I had) was about to be wiped out.  I can't afford to lose anything on the external hard drive, especially the pics, so I stopped the installation only to find it allowed me to open Ubuntu anyway, presumably from the CD.  Can I get some good guidance on whether installing it on the external hard drive will erase everything there?  Thanks in advance.
Andy P

---

### Post by zvacet on 2009-04-24
[Here]("https://help.ubuntu.com/community/BurningIsoHowto") is described standard process of downloading,checking and burning iso.If everything goes right then install it.During installation you should see your HDD-s and pick one you want to install Ubuntu on.You can read [this]("http://psychocats.s465.sureserver.com/ubuntu/installing") before installing and see more about partitioning.

---

### Post by durand on 2009-04-24
> **zvacet said:**
> [Here]("https://help.ubuntu.com/community/BurningIsoHowto") is described standard process of downloading,checking and burning iso.If everything goes right then install it.During installation you should see your HDD-s and pick one you want to install Ubuntu on.You can read [this]("http://psychocats.s465.sureserver.com/ubuntu/installing") before installing and see more about partitioning.

He's already worked that much out.

medebe, you need to use manual partitioning and resize your media partition and make 2 more partitions. One is for "swap", this is where ubuntu will write to if you need to hibernate or run out of memory. Create this with about twice the amount of RAM you have with partition type swap. You also need the main partition, "/". This is where ubuntu will be installed to. Partition this with type ext3 or ext4. I would recommend ext4 as it is much faster however it has only been released recently so it may not be completely bug free. You also need to set it's mount point to be "/". If you install it from there, it should work however I'm not completely sure how installing on an external hard drive works...so you might have to do something else as well.

Oh and you should backup your media if something goes wrong which is likely when partitioning.

---

