---
title: "[SOLVED] GNOME won't start on fresh Intrepid install"
date: 2008-12-20
forum: New to Ubuntu
---

### Post by aheckler on 2008-12-20
Hey all, I just installed Intrepid on my old desktop. It boots normally, I can enter my username and password just fine. But after logging me in, the computer just hangs there on the peach-colored background and mouse cursor, but nothing else. It's seems as if GNOME or X can't start for some reason, so I can't even get to a desktop.

Also, my network isn't functioning at the moment, but I do have a second connection, so I can download packages and move them over via USB if needed.

---

### Post by abn91c on 2008-12-20
that is probably due to compiz not supported by you video card, you may need to log in to recovery mode and disable desktop effects and maybe even remove compiz altogether

---

### Post by aheckler on 2008-12-20
I can get to the root shell via recovery mode, is it just a simple matter of:

```
sudo apt-get remove compiz
```

???

---

### Post by abn91c on 2008-12-20
also sudo apt-get remove compiz-core

---

### Post by aheckler on 2008-12-20
Woohoo! That did it, thanks abn91c! I didn't even think of the vid card as a possible cause...

:)

---

### Post by abn91c on 2008-12-20
> **aheckler said:**
> Woohoo! That did it, thanks abn91c! I didn't even think of the vid card as a possible cause...

:)
Welcome dude:), have fun with Ubuntu:)

---

### Post by Fixman on 2008-12-20
> **abn91c said:**
> Welcome dude:), have fun with Ubuntu:)

>  Join Date: Apr 2008 

mm...

---

### Post by aheckler on 2008-12-20
Yeah I've been using Ubuntu for a few years actually. This thread only concerns an installation on an older PC I did today.

I have, however, loved Ubuntu ever since I switched over :)

---

### Post by ugm6hr on 2008-12-20
> **aheckler said:**
> Yeah I've been using Ubuntu for a few years actually. This thread only concerns an installation on an older PC I did today.

Don't apologise.

I joined almost a year before I installed.  Never looked back - I think that's why.

---

