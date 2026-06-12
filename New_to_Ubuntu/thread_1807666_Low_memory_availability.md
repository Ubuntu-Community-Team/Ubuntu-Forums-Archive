---
title: "Low memory availability"
date: 2011-07-19
forum: New to Ubuntu
---

### Post by TACITVS on 2011-07-19
I was recently given an HP dv6000 and as I went to restore it to factory cfg, the sys restore failed (Vista); therefore dead laptop. The wonderful part about that is that it led me to the wonderful world of ubuntu. My only concern is that my du shows 82% of the HD (120gb total, 8341430b used) which leads me to believe that all of the accursed programs from Windows aren't deleted. The only thing that would run after the sys restore wouldn't work (I tried to change the boot log) was the BIOS. 

With all that said, how can I see if there's another partition being used and how do I delete it? I'm new but learning very quickly and all the commands I've used have shown me what ubuntu is on, but I'm not sure how to check elsewhere.

Thank you folks in advance.

---

### Post by skatinjj on 2011-07-19
You can go to the software center and download gparted.

This will display all the partitions on the system and what file system they are.

::EDIT::

It will also allow you to delete and resize partitions.

---

### Post by skatinjj on 2011-07-19
Also, you could do a complete install of Ubuntu and just tell it to use the whole hard drive for the install.

---

### Post by TACITVS on 2011-07-19
I think I did do a full install, that's what I remember from the ISO/USB...it shouldn't take 83gb for Ubuntu, should it?

---

### Post by androssofer on 2011-07-19
> **TACITVS said:**
> I think I did do a full install, that's what I remember from the ISO/USB...it shouldn't take 83gb for Ubuntu, should it?

def not, only a few gigs for a fresh install... i think the default option during install is to put the ubuntu partition along side windows...(**note** might be incorrect...) so maybe that happened?

download gparted as advised by skatinjj and u'll get a nice visual display of the partitions.

what did you use to get the info about it being 82% full?

---

### Post by skatinjj on 2011-07-19
The default option is to install along side of another operating system to help prevent wiping it out.  

You would have to manually select the second option to use the whole hard drive or go advanced and manually configure your partitions.

---

### Post by TACITVS on 2011-07-19
Thanks so much for the really fast help! 

Here's what gparted says...

[http://www.flickr.com/photos/65427059@N06/5955005840/in/photostream](http://www.flickr.com/photos/65427059@N06/5955005840/in/photostream)

Sorry for the link, it wouldn't upload correctly...

EDIT:

My mistake the link should be accessible now.

---

### Post by TACITVS on 2011-07-19
Failte Androssofer! :P

---

### Post by TACITVS on 2011-07-19
I failed to mention I'm using Deja Dup...if that changes anything.

And it did; I just trashed my backup and gained over half my HD space back...is there any way to get around that? Perhaps setup a partition that just has say kubuntu (I heard that it is very light) and some important folders? I'm really sorry for wasting your time earlier; I didn't even think about the backup files.

---

