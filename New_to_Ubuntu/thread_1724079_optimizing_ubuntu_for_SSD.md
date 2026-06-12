---
title: "optimizing ubuntu for SSD"
date: 2011-04-07
forum: New to Ubuntu
---

### Post by fremantle on 2011-04-07
hy,
i got a new ssd netbook (mini 9) and installed natty beta 1 on it. i found some google results like [this]("http://itezer.com/blog/ubuntu-linux/125-Four_Tweaks_for_Using_Ubuntu_with_SSD.html") that suggest some tweaks to use ubuntu with SSD. my question is, do i really need to do these 'optimizations' to use ubuntu in my ssd netbook?

---

### Post by Locke_99GS on 2011-04-07
You don't *need* to do them, no. Many of them can help, though, with speed (on any system) and SSD longevity.

Note that the default IO scheduler, CFQ, has had some work over the past couple of years, and that an alternative IO scheduler called BFQ does away with stalling.

---

### Post by fremantle on 2011-04-07
which ones do you most recommend regarding performance and life of ssd?

---

### Post by Paqman on 2011-04-07
Mounting /tmp on a ramdisk will improve performance on any kind of disk, so you might as well go ahead and do that. Btw, the command that tutorial uses is wrong, to edit fstab using gedit you would use:
```
gksudo gedit /etc/fstab
```
The tutorial uses sudo, which is only for command line apps, not GUI ones like gedit.

If you're using Firefox and you've got /tmp in a ramdisk then putting Firefox's cache into /tmp will reduce disk writes, but it'll also mean your cache gets wiped out every boot, so it may increase your bandwidth use. That could be an issue if you're on a capped 3G connection.

Some people do change the scheduler for their SSDs, but i've never bothered personally. You might want to consider aligning the partitions on your disk though. You can do that in Gparted, just put 1MB either end of each partition and make sure the "align to cylinders" box is unchecked.

---

### Post by fremantle on 2011-04-07
cool. and what about enabling noatime?

---

### Post by wolfen69 on 2011-04-07
> **Paqman said:**
> You might want to consider aligning the partitions on your disk though. You can do that in Gparted, just put 1MB either end of each partition and make sure the "align to cylinders" box is unchecked.

Newer versions of ubuntu automatically do that now if you select "use whole disk" to install.

---

### Post by Paqman on 2011-04-07
> **fremantle said:**
> cool. and what about enabling noatime?

Ubuntu's default is now "relatime" which gives some of the same benefits. Some older apps don't play nicely with "noatime" but they're few and far between AFAIK. Enable it and if stuff starts acting weird you can always switch back.

---

### Post by 1clue on 2011-04-07
All four are really good ideas.

One huge error that is not mentioned by anyone else so far:  Any time you put a temp dir into /tmp, you should put it into a separate folder for your user.  So /tmp/1clue/firefox for firefox.  Do this for every user.

The consequence is that if you have two people running the same app (at the same time or not) writing any temp file with the same name, or creating a directory (like firefox does) with a specific name, then the second guy can't run the app because they don't have write permission to that directory.

One thing not recommended in there is that you get significantly more RAM than you actually need to run your system.  If you ever actually use swap, then you are paging RAM to the disk which not only trashes performance but starts "wearing a hole" in the disk.  The swap is a particular space on the drive, and it will be written over and over if you regularly hit swap.

Better yet, if you have a lot of RAM that is never used for "normal" things, Linux will use it as a disk cache which speeds you up even more.

---

### Post by Paqman on 2011-04-07
> **1clue said:**
> 
One thing not recommended in there is that you get significantly more RAM than you actually need to run your system.  If you ever actually use swap, then you are paging RAM to the disk which not only trashes performance but starts "wearing a hole" in the disk.  The swap is a particular space on the drive, and it will be written over and over if you regularly hit swap.


Yep, and if you have got plenty of RAM then you'll want to wind your swappiness right down to make sure you're never touching your swap.

[https://help.ubuntu.com/community/SwapFaq#What is swappiness and how do I change it?](https://help.ubuntu.com/community/SwapFaq#What is swappiness and how do I change it?)

---

### Post by 1clue on 2011-04-08
By the way, if you have a mechanical disk and do steps 1,2 and 3 from the HOWTO, plus have about 12G RAM, then you will have nearly all the benefits of an SSD for everyday use as long as you don't shut down constantly.  Your first-load time is going to be just like the normal disk, but subsequent reads will be cached in RAM and therefore have faster-than-ssd reads, same as if you do it with an SSD.

It's suprising how much writing your system doesn't do, and if you have enough RAM to cache all the disk accesses then the only delays from running something like OpenOffice the second time is the time it takes to initialize the app.

---

