---
title: "HP MINI 311 --- How to create HD image"
date: 2009-10-17
forum: New to Ubuntu
---

### Post by kamaboko on 2009-10-17
Hello,

I just picked up a HP Mini 311 netbook.  I expected it to come with a restore CD..but..Noooooooooooooooooooo...HP wouldn't drop 25 cents on a CD.  So, how would you suggest I create an image of the drive before installing Ubuntu?  I do have an external DVD player for this netbook and a 4GB flash drive if that info helps.

Thanks,
K

---

### Post by swoody on 2009-10-20
Are you running XP or Vista on this computer?

---

### Post by LewRockwell on 2009-10-20
> **kamaboko said:**
> Hello,

I just picked up a HP Mini 311 netbook.  I expected it to come with a restore CD..but..Noooooooooooooooooooo...HP wouldn't drop 25 cents on a CD.  So, how would you suggest I create an image of the drive before installing Ubuntu?  I do have an external DVD player for this netbook and a 4GB flash drive if that info helps.

Thanks,
K

so how does HP expect you to re-install the operating system they sold you if you experience a hard drive failure and are required to replace it?

what did/does their documentation/manual/literature say about that?

.

---

### Post by lavinog on 2009-10-20
some hp's require that you burn your own installation disk.
If you your computer doesn't have a cd burnner, you will need an external drive to do this.
You could use an external hard drive and a live cd to make a copy of the reocovery partition, or maybe your whole drive.
gparted live, partimage, or clonezilla can do this.

---

### Post by Daveski on 2009-10-20
> **kamaboko said:**
>  So, how would you suggest I create an image of the drive before installing Ubuntu?  I do have an external DVD player for this netbook and a 4GB flash drive if that info helps.

Boot a LiveCD and use that environment to image the HDD to a USB drive. I would recommend CloneZilla if you are comfortable with text based menus, and have an understanding of how Linux assigns devices and partitions.

You can also dd the entire drive to an image file on another disk in the Ubunutu live environment.

I used CloneZilla to succesfully backup and restore my ASUS eeepc with a USB hard drive and a USB CDROM.

---

