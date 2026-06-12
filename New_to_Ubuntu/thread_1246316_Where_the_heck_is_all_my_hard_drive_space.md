---
title: "Where the heck is all my hard drive space??"
date: 2009-08-21
forum: New to Ubuntu
---

### Post by wonderpigeon on 2009-08-21
Hey all,

I just installed Ubuntu as a second OS on a machine already running Vista.

I had set aside 30 gigs for Ubuntu. When I installed it I selected to have Ubuntu use the largest continuous space. This all appears to have gone just fine.

However, somehow I only have 373mb left of this original 30 gigs!!

df -h gives me this:

Filesystem            Size  Used Avail Use% Mounted on
/dev/sda6              29G   27G  373M  99% /
tmpfs                 1.8G     0  1.8G   0% /lib/init/rw
varrun                1.8G  104K  1.8G   1% /var/run
varlock               1.8G     0  1.8G   0% /var/lock
udev                  1.8G  184K  1.8G   1% /dev
tmpfs                 1.8G   96K  1.8G   1% /dev/shm
lrm                   1.8G  2.2M  1.8G   1% /lib/modules/2.6.28-15-generic/volatile
/dev/sda3             264G  140G  124G  54% /media/OS

All of the folders in my filesystem folder EXCEPT /media total 3.7 gigs. The /media folder is large because that's where I mounted the Windows partition where I keep all my personal documents, but my understanding is that those files are all on a separate partition (and they far exceed the 27 gigs that are supposed to be filled on this partition anyhow). What the heck is taking up 27 gigs in my Ubuntu partition???

Any insights would be greatly appreciated!

Thanks!

---

### Post by ptviperz on 2009-08-21
Try going to Applications->Accessories->Disk Usage Analyzer

Then run the analyzer on your home folder and you should be able to see where the disk space is going

---

### Post by Penguin Guy on 2009-08-21
Try running the program [COLOR="Green"]baobab[/COLOR], it gives you lots of info about how much, and where data is stored on your disks. It should be installed by default.

---

### Post by mapes12 on 2009-08-21
Just to help me out here please could you also post the output to ```
sudo fdisk -l
```and to make things easier on the eye a screen shot from Gparted would be good (Gparted is in Synaptic)

---

### Post by wonderpigeon on 2009-08-21
Okay, well now I'm feeling stupid. I ran the disk analyzer and found that most of the space was taken up by things... *drum roll* ... in the trash. Ah.

(I had imported files into F-spot, and it had copied them onto the local partition, and I had deleted them and they were all sitting in the trash, being huge and stuff.)

Thanks for the help!

---

### Post by Katalog on 2009-08-21
> **ptviperz said:**
> Try going to Applications->Accessories->**Disk Usage Analyzer**

Then run the analyzer on your home folder and you should be able to see where the disk space is going

> **Penguin Guy said:**
> Try running the program **baobab**, it gives you lots of info about how much, and where data is stored on your disks. It should be installed by default.

Um, aren't those the same app, but it's just listed as "Disk Usage Analyzer" in the Accessories menu?

---

### Post by mapes12 on 2009-08-21
> **wonderpigeon said:**
> Okay, well now I'm feeling stupid. I ran the disk analyzer and found that most of the space was taken up by things... *drum roll* ... in the trash. Ah.

(I had imported files into F-spot, and it had copied them onto the local partition, and I had deleted them and they were all sitting in the trash, being huge and stuff.)

Thanks for the help!Good to hear you got it sorted.

For the future BEWARE TRASH! Have a look here. I have it bookmarked:  [http://ubuntuforums.org/showthread.php?t=898573](http://ubuntuforums.org/showthread.php?t=898573)

---

### Post by ptviperz on 2009-08-21
> **Katalog said:**
> Um, aren't those the same app, but it's just listed as "Disk Usage Analyzer" in the Accessories menu?

Yep, but I think Disk Usage Analyzer may be a little easier to remember than baobab. And some don't like terminal.

---

### Post by kaptain0 on 2009-08-21
it kinda looks like it partitioned your drive into 10 partitions for everything, instead of all together.
 
i just do manual

---

