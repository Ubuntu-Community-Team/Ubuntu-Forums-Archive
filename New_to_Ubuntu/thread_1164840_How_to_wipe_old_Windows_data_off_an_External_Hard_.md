---
title: "How to wipe old Windows data off an External Hard Drive with Ubuntu OS"
date: 2009-05-20
forum: New to Ubuntu
---

### Post by mikodo on 2009-05-20
Hello everyone,

I have an external Hard Drive that I used with Acronis (back up program for windows). It still remains connected to my computer and when I start it, it is read as   Location: /Media/Acronis B_U.  I no longer use any Windows OS's, and wonder if there is an easy way to accomplish wiping it clean with my running Ubuntu Hardy to render it useful for back-ups and storage in Hardy? 

Thank you,

mikodo

---

### Post by rybaxs on 2009-05-20
use GParted

---

### Post by superprash2003 on 2009-05-20
use a software called gparted

---

### Post by Game Over on 2009-05-20
sudo apt-get install gparted

then

gparted &

Just had to be part of the action... Heh heh.

---

### Post by mikodo on 2009-05-20
> **Game Over said:**
> sudo apt-get install gparted

then

gparted &

Just had to be part of the action... Heh heh.

I ran in terminal as above; then gparted /Media/Acronis B_U and received:

**************-desktop:~$ gparted /Media/Acronis B_U
[2]+  Done                    gparted
**************-desktop:~$ 

When I clicked on the icon for Acronis it indicates O items, Free Space 465.6 GB. I think that is what was available before all my Windows back-ups.

Is that all there is to it??

Thanks

Mikodo

---

### Post by Mark Phelps on 2009-05-20
Not to nitpick, but let's be sure we have our terms right ...

You asked about "wiping" the drive.  GParted repartitions the drive, which if you simply want to reuse it, is OK.  However, nearly all of the data is still present on the drive, just not easily accessible.  

If you really wanted to "wipe" the drive, meaning physically removing ALL the data from the drive, you need to check out dban.

---

### Post by mikodo on 2009-05-20
> **Mark Phelps said:**
> Not to nitpick, but let's be sure we have our terms right ...

You asked about "wiping" the drive.  GParted repartitions the drive, which if you simply want to reuse it, is OK.  However, nearly all of the data is still present on the drive, just not easily accessible.  

If you really wanted to "wipe" the drive, meaning physically removing ALL the data from the drive, you need to check out dban.

This is what I asked for. But it sounded a little scary when I read up on it. If the Gparted repartition of the external drive allows it to be reused, maybe I'll just use it for now. You stated the data is not easily accessible.

If in the future, with more confidence in using dban, maybe I will go that route, but for now, I don't want to make a mistake and wipe the wrong drive, when Gparted repartitioning is probably sufficient for my use.

Thanks so much,

mikodo

---

