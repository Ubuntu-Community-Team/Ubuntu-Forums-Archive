---
title: "Autorun difficulties"
date: 2011-01-15
forum: New to Ubuntu
---

### Post by MustaphaMond on 2011-01-15
I successfully installed a windows program using wine and when I run the program it asks me to load the disc. I only need to do this once to get the program up and running, but I have no disc, just the ISO. I've tried mounting it in several different ways, including the program Gmount-iso, but the program says I still haven't loaded the disc! I believe it has something to do with the autorun not working properly because I had trouble with that when I was installing the program, too. Please help!

---

### Post by I8NY on 2011-01-15
Well I have had success with acetonelISO for mounting iso files. (Note: you must unmount it in acetoneISO not nautilus)  I have never tried it for wine but it *should* work.  Wine may not be configured to see the mounted ISO or the program is looking at the wrong drive letter.  Another thing to do is u could burn the ISO to a CD/DVD and then u would have the real disc.

---

### Post by MustaphaMond on 2011-01-15
Unfortunately AcetoneISO won't work either... things are mounting just fine but the program still thinks the disc hasn't loaded. I might have to go out and buy DVDs and have a friend write it for me because my disc drive can't do that.

---

### Post by I8NY on 2011-01-15
One more thing to try before u burn that DVD.  Maker sure in wine it is configured to see the mounted ISO. (Application>wine>configure wine>drivers)

---

