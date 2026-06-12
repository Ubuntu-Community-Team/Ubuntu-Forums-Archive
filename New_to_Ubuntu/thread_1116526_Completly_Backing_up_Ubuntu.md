---
title: "Completly Backing up Ubuntu"
date: 2009-04-05
forum: New to Ubuntu
---

### Post by Ayeco on 2009-04-05
I am planning of messing around with different OS 's and will most likely clean my hard drive.  I need a way to backup my current ubuntu configuration,  kernel(I'm running a modded kernel for the Eee PC), appearance, basically everything, but I don't need my documents.  Later I will be putting Ubuntu back on my computer and do not want to spend hours configuring it again.  I'm nearly certain that this question has already been asked, so if someone would be so kind as to guide me to that thread, I would greatly appreciate it.  --Ayeco

---

### Post by linuxuser21 on 2009-04-05
Try [Simple Linux Backup]("http://simplelinuxbkup.sourceforge.net/").  It will backup everything.

---

### Post by kansasnoob on 2009-04-05
I like aptoncd. That is Apt on CD!

You'd still have to reinstall from the live CD but then you can install all packages you'd installed previously!

That's the safest way if you've changed any hardware along the way.

---

### Post by RedSingularity on 2009-04-05
I personally love clonezilla.  Works great for me.

---

### Post by hyper_ch on 2009-04-05
best to make an image... can you boot a live cd from an external cd drive or usb stick there?

---

### Post by longtom on 2009-04-05
Just to chip in - don't want to hijack but...

How can I backup the whole system without having to download all the programs again?  Either on an external drive or a bunch of DVDs.

I am only talking about Ubuntu as is as well as all programs installed.  Data will be taken care off seperately.

---

### Post by Armor Nick on 2009-04-05
> **longtom said:**
> Just to chip in - don't want to hijack but...

How can I backup the whole system without having to download all the programs again?  Either on an external drive or a bunch of DVDs.

I am only talking about Ubuntu as is as well as all programs installed.  Data will be taken care off seperately.
As stated above, AptOnCD is perfect for this, as it gathers all the debs of your apps into a disc image, which you can use to install your apps without downloading them again.

---

### Post by longtom on 2009-04-05
> **Armor Nick said:**
> As stated above, AptOnCD is perfect for this, as it gathers all the debs of your apps into a disc image, which you can use to install your apps without downloading them again.

Thank you.

I had my struggles, tries and tribulations with AptOnCD....  I am no backing up my cache as is, which appears to be more reliable.

I was more thinking of:

Backing up my system and all programs/applications (Oo, Thunar. etc)

Once restored to a HD all runs exactly the way it was before backup, no configurations, no additional downloads, no missing dependencies.  Am I having my head in cloud 7 again?

---

### Post by hyper_ch on 2009-04-05
make a disk image... then the current state of your installation is saved... very simple.

---

### Post by longtom on 2009-04-05
> **hyper_ch said:**
> make a disk image... then the current state of your installation is saved... very simple.

Once again you are full of simple solutions.  Could you point me, as an uninitiated in that procedure, in a direction were I can learn how to do that?  And spliiting up everything it fits on DVDs?

I tried to get to grips with one of the <How to installclonezilla on Ubuntu> tuts - but my head is to square for that...

Thanks and

---

### Post by hyper_ch on 2009-04-05
well, I don't know what you have at your disposal but I would:

(1) start a live system
(2) attach an external drive
(3) dd my disk onto the external drive

But it all depends what you have to run on...

---

### Post by longtom on 2009-04-05
> **hyper_ch said:**
> well, I don't know what you have at your disposal but I would:

(1) start a live system
(2) attach an external drive
(3) dd my disk onto the external drive

But it all depends what you have to run on...

Sounds simple enough....but....(*blushing because caught ignorant...) what is <dd>?

---

### Post by hyper_ch on 2009-04-05
dd is a command... also humorously called "disk destroyer". Bascially it makes a bit by bit copy of a given devices... like a harddisk.

Problem is if you confuse if and of you just might overwrite your data instead of backing it up.

---

### Post by longtom on 2009-04-05
> **hyper_ch said:**
> dd is a command... also humorously called "disk destroyer". Bascially it makes a bit by bit copy of a given devices... like a harddisk.

Problem is if you confuse if and of you just might overwrite your data instead of backing it up.

This is awfully reassuring to a beginner like me....:p

What can it be confused with?  Any "idiots guide for <dd>" out there?  Nothing more userfriendly and less potentially hazardous?

<...overwrite your data...>  I'm still shivering...

---

### Post by hyper_ch on 2009-04-05
basically it goes:

```

sudo dd if=/dev/sdX of=/dev/sdY

```
or
```

sudo dd if=/dev/sdX of=/media/externalmountedrive/backup.iso

```

if=input file
of=output file

Just make sure you set the right devices accordingly.

---

### Post by longtom on 2009-04-05
Ok - I can do that.  Thank you.

And how do you get it back?  Just pop in the DVD and all runs by itself?  What happens to grub and any other OS installed?  There is always something....

---

### Post by hyper_ch on 2009-04-05
well, you can store it on a second disk in the computer or on an external disk or on a networked disk... that's why I said I don't know what you have at your disposal :)

as for putting it back again, you just rever the input and output

e.g.

for backup
```

sudo dd if=/dev/sda of=//server/backup.iso

```

for restore
```

sudo dd if=//server/backup.iso of=/dev/sda

```

that's just an example. Depending on how big those in that case /dev/sda is and how much data you have on there, you might wnat to use another tool than dd because dd will make a 1:1 copy that means the resulting backup.iso is as big as the disk /dev/sda.

---

### Post by Lunx on 2009-04-05
This thread has some very useful info 

[http://ubuntuforums.org/showthread.php?t=35087](http://ubuntuforums.org/showthread.php?t=35087)

---

### Post by Tews on 2009-04-05
Ive always found Quick Start the easiest way way to back-up ubuntu.  You can use it to back up your system using the .tar method or it can make an image ... works backing up your windows partition too!

Check it out at  [http://www.quickstart.freeforums.org/quickstart-download-pics-t2.html]("http://www.quickstart.freeforums.org/quickstart-download-pics-t2.html")

---

### Post by Ayeco on 2009-04-05
Thanks for the great tips, I'll try to image my drive with your great instructions.

---

### Post by hyper_ch on 2009-04-05
well, disk imaging will enable you to just put the system back into the stage it is now... file backups will save you data but you'll still need to setup again. good luck.

---

### Post by tea for one on 2009-04-05
You may want to have a look at Remastersys. This software allows you to make an image of your software only or an image of software and data.

This tutorial was useful for me:-

[http://www.dedoimedo.com/computers/remastersys.html](http://www.dedoimedo.com/computers/remastersys.html)

---

### Post by Lunx on 2009-04-06
> **tea for one said:**
> You may want to have a look at Remastersys. This software allows you to make an image of your software only or an image of software and data.

This tutorial was useful for me:-

[http://www.dedoimedo.com/computers/remastersys.html](http://www.dedoimedo.com/computers/remastersys.html)

That rocks, I set the repository, downloaded and had an ISO of my system in less than half an hour start to finish (including the repo change, update and application download). Unfortunately I now realise I don't have any DVD disks on hand, so haven't been able to create a disk yet. No experience with VM yet either, but I guess that's something I should begin to investigate now.

---

### Post by tea for one on 2009-04-06
One of the excellent features of Remastersys is that the remastered image created contains the Ubuntu install routine. (choose language, country, partitions etc) and will also perform as a "live" CD

My other advice would be to consider keeping data on a separate home partition so that, if you corrupt your system, you only have to reinstall the OS.

For backing up data, I have successfully used Grsync (install via Synaptic)

---

### Post by mamamia88 on 2009-04-06
so aptoncd lets you backup all installed apps for fresh install?  could be useful since i have a home partition and the only thing it doesn't backup is installed apps

---

### Post by longtom on 2009-04-07
> **tea for one said:**
> 
My other advice would be to consider keeping data on a separate home partition so that, if you corrupt your system, you only have to reinstall the OS.


This is excellent advice indeed, which I am following for quite some time.

However - I would also like to backup my system as is with all installed applications.  Bandwith is an issue in some countries.

Remastersys seems to be an application which might help with that.  I'll check it out!

---

### Post by tea for one on 2009-04-07
When you run Remastersys, it will create an iso which will include all your installed applications.

For example, if you have installed Mozilla Thunderbird, this application will be included in your "remastered" image.

Now, if you have added many additional applications, you may find that the image will be t0o large for a CD but it should fit OK on a DVD.

I, also, do not have unlimited bandwidth agreement with my ISP, and sometimes I am reluctant to download data unless there is no alternative.

---

### Post by expatCM on 2009-04-07
Is there a way of keeping the remastersys image up to date?   The way I understand this, if I add a couple of apps today I need to create a fresh remastersys iso in full in order to include them.  Is there a way to do a partial or incremental update?

---

### Post by tea for one on 2009-04-07
Good question "partial or incremental update"?

As far as I am aware, you can only perform a complete image with Remastersys i.e. there is no partial facility.

However, unless you are continually adding software packages, there may be no need to continually "remaster"

I use it approx once per month to keep an image of recently added packages and including security updates.

The "remaster" process takes about 1 hour including burning to a DVD and then testing the DVD as a "live" system.

---

