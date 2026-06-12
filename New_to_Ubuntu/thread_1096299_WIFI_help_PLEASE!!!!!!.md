---
title: "WIFI help? PLEASE!!!!!??!"
date: 2009-03-14
forum: New to Ubuntu
---

### Post by mgrantcolburn on 2009-03-14
Hello all...

I just downloaded Ubuntu and am trying to get my wifi to work. I have looked all over this forum and the web trying to get a million different methods to work, but... I have failed at everything.

Here is my card: Atheros AR242x 802.11 abg

I'm running an Acer 5050 something or another. I could just be retarded, I'm not a computer person at ALL, but is there somebody willing to either give step by step (idiot proof, in the most base possible meaning) instructions or point me in the direction of a blog that has them? I'm losing my mind with frustration here. Thanks!

---

### Post by bubba_169 on 2009-03-14
Something you could try if you are on 8.10 ... in a terminal type:

```
sudo apt-get install linux-backports-modules-intrepid
```

When that has finished restart your computer and see if you have wifi.

---

### Post by lkraemer on 2009-03-14
Well, a quick SEARCH for AR242x & HOWTO: turns up this guide
which I just used and I know it works.  GOOGLE & SEARCH can be
your friend too!

[http://ubuntuforums.org/showthread.php?t=792158&highlight=AR5007EG](http://ubuntuforums.org/showthread.php?t=792158&highlight=AR5007EG)

The question is are you running 32 Bit or a 64 Bit install, and 8.04 LTS
or 8.10, or what version?  The howto needs to cover your version.

Let us know how it goes?

lkraemer

---

### Post by cptrohn on 2009-03-14
> **bubba_169 said:**
> Something you could try if you are on 8.10 ... in a terminal type:

```
sudo apt-get install linux-backports-modules-intrepid
```

When that has finished restart your computer and see if you have wifi.

I have the same card and this is the best solution (and easiest) that have found.

---

