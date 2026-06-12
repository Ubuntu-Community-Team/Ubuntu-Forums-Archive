---
title: "mounting windows partition's folders"
date: 2011-08-21
forum: New to Ubuntu
---

### Post by emoguitarist06 on 2011-08-21
I already updated my fstab to auto mount my windows partition (sda3) to /media/windows but I want to mount my pictures and videos from that partition to take place of my ~/home/username/videos & pictures

---

### Post by lmarmisa on 2011-08-21
I recommend to use symbolic links. This is an example:

```

ln -s /media/windows/MyPictures ~/Pictures/MyPictures

```

---

### Post by apollothethird on 2011-08-21
> **emoguitarist06 said:**
> I already updated my fstab to auto mount my windows partition (sda3) to /media/windows but I want to mount my pictures and videos from that partition to take place of my ~/home/username/videos & pictures

Rename or remove your ~/home/username/videos and pictures folders then link the folders to that area from where you have them auto mounted.

-- L. James

-- 
L. D. James
[email]ljames@apollo3.com[/email]
[www.apollo3.com/~ljames](www.apollo3.com/~ljames)

---

### Post by sbraz on 2011-08-21
> **emoguitarist06 said:**
> I already updated my fstab to auto mount my windows partition (sda3) to **/media/**windows but I want to mount my pictures and videos from that partition to take place of my ~/home/username/videos & pictures
i've read somewhere that this is a system folder and we shouldn't use that location for anything but nautilus automatic mount feature. don't be surprised if something breaks because of this. :)

---

### Post by Megaptera on 2011-08-22
> **emoguitarist06 said:**
> I already updated my fstab to auto mount my windows partition (sda3) to /media/windows but I want to mount my pictures and videos from that partition to take place of my ~/home/username/videos & pictures

I found this guide useful (quote) "... most people are really just concerned about their documents, music, videos, and so forth.  This solves that issue by pointing both OSs to look in the same place for them."

Guide: [http://www.howtogeek.com/howto/35807/how-to-harmonize-your-dual-boot-setup-for-windows-and-ubuntu/](http://www.howtogeek.com/howto/35807/how-to-harmonize-your-dual-boot-setup-for-windows-and-ubuntu/)

Hope it's of interest?

---

