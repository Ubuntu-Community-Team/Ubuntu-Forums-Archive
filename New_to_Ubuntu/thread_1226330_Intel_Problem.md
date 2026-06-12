---
title: "Intel Problem"
date: 2009-07-29
forum: New to Ubuntu
---

### Post by Whisper of Neko on 2009-07-29
I have used Ubuntu for over a year now, and loved it!!  Until my computer died and I bought a new laptop.... with intel graphics.

Is there anyway to FIX the problem?  I cannot live with all the trouble it causes.  Is there a different driver I can install to fix it?  Anything?  Please help!

---

### Post by ddrichardson on 2009-07-29
What *is* the problem?

---

### Post by nhasian on 2009-07-29
actually having an intel adaptor is a GOOD thing with Karmic as it supports [KMS]("https://wiki.ubuntu.com/X/KernelModeSetting").  they've made a lot of changes under the hood and it should run a lot smoother for you now.

---

### Post by Whisper of Neko on 2009-07-29
So, should I wait for Karmic?  I don't really want do download any alphas or betas.

---

### Post by nhasian on 2009-07-29
I've been using Karmic since Alpha2 and its been working great for me on my laptop.  Alpha3 is out now, and Alpha4 will be out in two weeks.  It comes out in October, but feel free to give alpha3 a whirl now.  you wont need to reinstall when it goes final, as long as you do all the updates, you will automatically be upgraded to the final product when its released.

---

### Post by Whisper of Neko on 2009-07-29
Is it possible to install it directly from Jaunty without burning a new C.D.?  I would love to try it out, but I ran out of C.D.'s last week and I don't want to burn a DVD of such a small file.  :/

---

### Post by gn2 on 2009-07-29
Use 8.04, it should be fine.

---

### Post by nhasian on 2009-07-29
To upgrade from Ubuntu 9.04 on a desktop system, press Alt+F2 and type in "update-manager -d" (without the quotes) into the command box. Update Manager should open up and tell you: New distribution release '9.10' is available. Click Upgrade and follow the on-screen instructions. 

> **Whisper of Neko said:**
> Is it possible to install it directly from Jaunty without burning a new C.D.?  I would love to try it out, but I ran out of C.D.'s last week and I don't want to burn a DVD of such a small file.  :/

---

### Post by Whisper of Neko on 2009-07-31
Thank you so much!  I love it.  It works great!

---

### Post by PreviousN on 2009-07-31
I would strongly warn anyone going with intel in the near future. Their gma500/poulsbo is a disaster, and includes two closed sourced binary blobs. Video hasn't worked right for many since **Hardy** with this chipset. Even then it was sketchy. Search the forums for *Dell Mini 12* or *Sony Viao P* or the *Kohjinsha SC3*, all of which have GMA500, and you'll find out what I mean. 

So, since this guy never did indicate exactly what his problem was, it could be a major one. Check out this 70+ post thread about the problem I am refurring to: [http://georgia.ubuntuforums.org/showthread.php?p=7711782](http://georgia.ubuntuforums.org/showthread.php?p=7711782)

Need even more proof? Check out this article that was posted on Slashdot: [http://slashdot.org/article.pl?sid=09/01/31/1859200](http://slashdot.org/article.pl?sid=09/01/31/1859200)

---

### Post by Liolikas on 2009-07-31
They tried to make better drivers and ended up with KMS/noKMS * EXA/UXA/XXA *DRI/DRI2*... options. As rule at least 1 of those combinations do not work.

---

### Post by Durden on 2009-07-31
> **nhasian said:**
> To upgrade from Ubuntu 9.04 on a desktop system, press Alt+F2 and type in "update-manager -d" (without the quotes) into the command box. Update Manager should open up and tell you: New distribution release '9.10' is available. Click Upgrade and follow the on-screen instructions.

Keep in mind this method will not give you the ext4 filesystem available in Karmic. You need to do a fresh install/format for that.

---

