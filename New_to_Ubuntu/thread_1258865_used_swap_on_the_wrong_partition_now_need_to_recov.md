---
title: "used swap on the wrong partition now need to recover it..HOW"
date: 2009-09-05
forum: New to Ubuntu
---

### Post by sarois3 on 2009-09-05
As a brank new user for ubunto 9.04 and linux in general, it seems i have made a silly mistake.
I have 1 hard disk with three partitions

Partition 1. for windows vista system
Partition 2. for my data created from vista
Partition 3. free

While installing the system i have slected partition 3 for the system and partition 2 for swap space.
After installation i went back to vista to find out that partition 2 is no longer visable in the window explorer, in vista nor in ubunto window explorer, which is a destaster.
Does this mean that the partition is gone

Is there anyway i can save partition 2. and get it back to vista?

please help.

---

### Post by Xenomorph05 on 2009-09-05
In Ubuntu install Gnome Partition Editor so you can see the partitions and modify them. It is very likely that if you used your partition 2 as swap then it would have formated it. swap spaces only needs to be 2-3 gb big so if your partition 2 is larger then that (which I think it would be) then you can reformat it to NTFS for your windows to us and cut a few gigs our for swap so you have 4 partitions.

---

### Post by LewRockwell on 2009-09-05
we just posted something on this earlier today...

be back in a minute...

[http://ubuntuforums.org/showthread.php?t=1258718](http://ubuntuforums.org/showthread.php?t=1258718)

there you go

.

---

### Post by Paqman on 2009-09-05
> **sarois3 said:**
> 
Does this mean that the partition is gone


Highly likely. Don't mount that partition, and especially don't do anything that will write to it (Ubuntu may well be writing to swap constantly)

Do you have your data backed up? If not, it *may* be possible to recover some data, but you will have lost some or all of it.

---

### Post by sarois3 on 2009-09-05
i am so basic with linux only few minutes of experience. and i am only exited to know, if this ultimately means that the data is totally lost. ie does using my 80 gb partition(2) as swap disk mean that it HAS been formatted.
is there any way to remove the swap off this partion thus retrieving the partition as it was?

---

### Post by Xenomorph05 on 2009-09-05
> **sarois3 said:**
>  ie does using my 80 gb partition(2) as swap disk mean that it HAS been formatted.
is there any way to remove the swap off this partion thus retrieving the partition as it was?

If you can use your windows still I suggest installing Recuva and let it check your partition 2 for files. It is very possible that because you changed the file system from NTFS to swap that the data is lost. I do not think that formating it back to NTFS and then scanning it with Recuva will make much difference but you can try it.

---

### Post by Paqman on 2009-09-05
> **Xenomorph05 said:**
> I do not think that formating it back to NTFS and then scanning it with Recuva will make much difference but you can try it.

Best thing to do, is *change nothing* on that partition. Every write you make on it could be writing over data you want to recover.

Now might be a good time to start thinking about starting a regular backup regime, or better yet redundant data storage.

---

### Post by Xenomorph05 on 2009-09-05
Does Ubuntu have software similar to Recuva? What would his best options be to try to salvage his data on that swap partition?

---

### Post by halitech on 2009-09-05
there is testdisk and photorec but I'm not sure if either works on a partition mounted as a swap partition. Worth a shot though

---

### Post by sarois3 on 2009-09-06
Thanks for the help.
Our IT team took it over and used a tool called R-Studio.
Miracoullesly we managed to recover the data from the disappeared partition and have saved it on an external hard disk .
My IT guy said it was pure luck that we got it back.

Now the question is: if i now format partition two, will ubunto boot?

---

### Post by Paqman on 2009-09-07
> **sarois3 said:**
> 
Now the question is: if i now format partition two, will ubunto boot?

How big is this partition? If it was being used to store data it's probably way too big for swap space. The swap partition only needs to be the same size as your RAM, tops. For most machines that's only going to be a couple of GB.

You can mess around creating a swap partiion, but it'd probably be quicker to just reinstall, and be a bit more cautious during the partitioning step this time.

Btw, have you got all the data you recovered backed up now?

---

