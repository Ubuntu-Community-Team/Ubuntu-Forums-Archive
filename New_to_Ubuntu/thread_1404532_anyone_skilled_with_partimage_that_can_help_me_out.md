---
title: "anyone skilled with partimage that can help me out?"
date: 2010-02-11
forum: New to Ubuntu
---

### Post by hortstu on 2010-02-11
So im thinking of installing partimage then making a boot drive out of a old hard drive that's in an external case.  I'm looking to get a linux system all setup on the external and use it for a backup or an alternative to a boot disk when I install ubuntu on to friends drives. 

Recently a friend handed me their drive and asked for linux since they're drive was overrun with viruses and inaccessible in windows.  They had no windows boot disk and didn't want to buy a new version.  They also feared they lost most of their pictures etc. I managed to save them.

Is partimage the right software for this?

---

### Post by Mark Phelps on 2010-02-11
> **hortstu said:**
> ... Is partimage the right software for this?

If by "this" you mean partitioning, and you want to do it for Ubuntu 9.10, the answer is no -- because Ubuntu 9.0 uses the Ext4 filesystem by default and partimage can't handle Ext4 filesystems.

Gparted, on the other hand, CAN handle Ext4.  You should download a LiveCD image of GParted, burn it to CD, boot from that, and use it to do your partitioning.

---

### Post by hortstu on 2010-02-11
Thanks Mark,

No, by "this" I meant making an image of an installation that I can duplicate easily so that I have an updated version of hardy ready to be written to a drive. I want to basically have a fine tuned live CD that I can install right to a blank disc.  I'm trying to figure out how to get to that point.

I got this from the part image website... 

[http://partimage.org/Main_Page](http://partimage.org/Main_Page)

"This utility can be used to install many identical computers. For example, if you buy 50 PCs, with the same hardware, and you want to install the same linux systems on all 50 PCs, you will save a lot of time. Indeed, you just have to install on the first PC and create an image from it. For the 49 others, you can use the image file and Partition Image's restore function."

Seems like what I want to do but I haven't found directions on how to do it.

Thanks.

---

### Post by Mustard on 2010-02-11
> [http://http://partimage.org/Main_Page]("This utility can be used to install many identical computers. For example, if you buy 50 PCs, with the same hardware, and you want to install the same linux systems on all 50 PCs, you will save a lot of time. Indeed, you just have to install on the first PC and create an image from it. For the 49 others, you can use the image file and Partition Image's restore function. ")



The link is broken..

Try this link [http://partimage.org/Main_Page]("http://partimage.org/Main_Page")

---

### Post by lkraemer on 2010-02-11
I question why you would bother......

For example you do as you suggest.....Then three months from now your
friend wants his system restored from your backup drive.  But, it is now
three months old, with no updates, and Version 10.04 has already been
released.  Wouldn't your friend want 10.04 LTS installed versus an old
version?

Just load the latest LiveCD Version, update, and go....

lk

---

### Post by hortstu on 2010-02-11
> **lkraemer said:**
> I question why you would bother......

For example you do as you suggest.....Then three months from now your
friend wants his system restored from your backup drive.  But, it is now
three months old, with no updates, and Version 10.04 has already been
released.  Wouldn't your friend want 10.04 LTS installed versus an old
version?

Just load the latest LiveCD Version, update, and go....

lk

Thanks for the help kramer... but I learn by doing and that's my ultimate goal here.  I can always wipe the drive and do the same thing when the next LTS version comes out.  I'm still using hardy.

---

