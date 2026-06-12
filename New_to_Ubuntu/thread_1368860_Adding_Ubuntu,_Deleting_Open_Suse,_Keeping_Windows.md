---
title: "Adding Ubuntu, Deleting Open Suse, Keeping Windows"
date: 2009-12-31
forum: New to Ubuntu
---

### Post by jmat on 2009-12-31
Hi Folks,

I have a few interrelated questions, but first some preliminary thoughts...I've gotten fairly good over the last few years at installing various Linux distros: Open Suse, Redhat, Mandriva(Mandrake), and now Ubuntu.  I remember  the first time I installed Linux, an Open Suse distro (10.0). I was a nervous wreck going thru the installation, fearing the worst, but in the end it functioned properly and introduced me to a whole new and productive world of computing.

So here's my question: I know how to take a Window's OS or a blank hard drive and install Linux onto it, but what I need to learn is how to take a Linux-only system and ***add ***Windows XP to it?  Is there an easy method?

The second question is somewhat related to the first: How do I ***delete old versions*** of, let's say Open Suse Linux, and install Ubuntu on it.  Particularly, I have a desktop with Windows XP (which I want to keep) but several versions of Open Suse on it.  What is the best way to delete those versions?

I've never really utilized a partitioner manually, but have a hunch that I may need to in order to delete those versions of Open Suse.

Any help would be greatly appreciated!

Happy New Year's to all!!!

Joe

---

### Post by blazemore on 2009-12-31
It should be very easy.
If you fire up the Ubuntu installer, you should see, when it gets to the partitioning stage, which partitions contain which OS.
All you'd have to do is go to Manual Partitioning, and format the OpenSuse partition you want to get rid of with the following settings:
```

Filesystem: ext4
Mountpoint: /
```

Alternatively, you could remove OpenSuse from another OS using a tool like gparted.
The Ubuntu installer will then give you an option to install into the free space.
Use this if you are at all unsure.

---

### Post by audiomick on 2009-12-31
On the first question:
You need to shrink the Linux partiton (see next paragraph), then install windows, then re-install grub. Windows installs always overwrite the Master Boot Record, which kills grub.

On the second question:
Blazemores advice is good. I would tend to the option of doing the partitioning first, then the install, simply to have only one thing happening at a time. This is not neccessarily the most time effective way, but it works better for my brain...:)

You can do your partitioning from the Ubuntu live CD which has gparted installed. System> Administration> gparted

Or you can get a gparted live CD here
[http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)

If you are comfortable with installing and such, you shouldn't have any great dramas figuring out how to deal with gparted.

---

### Post by jmat on 2009-12-31
Blazemore and Audiomick,

I really appreciate this advice.  In a bit I will give it a go--wish me luck!  Also thanks for the heads-up on "gparted." It sounds like just what I need to familiarise me with the wonderful world of partitioning.  

Joe

---

