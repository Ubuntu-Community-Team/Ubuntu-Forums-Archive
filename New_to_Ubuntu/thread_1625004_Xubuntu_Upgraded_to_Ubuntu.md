---
title: "Xubuntu Upgraded to Ubuntu?"
date: 2010-11-18
forum: New to Ubuntu
---

### Post by EnigmaticCoder on 2010-11-18
I did a distribution upgrade on my parents Xubuntu computer, but it upgraded to Ubuntu. Their machine is really old and cannot handle Ubuntu. How do I convert back to Xubuntu?

---

### Post by Hippytaff on 2010-11-18
you can remove gnome and install Kde (or if thier system is that tender xfce)
anyway try this [http://www.psychocats.net/ubuntu/kde](http://www.psychocats.net/ubuntu/kde)

---

### Post by EnigmaticCoder on 2010-11-18
Well, I'd like to follow those instructions, but I'm not given a GUI log in screen. I'm given a terminal login prompt.

---

### Post by Hippytaff on 2010-11-18
sorry...what was I thinking :-s

ok...
```

sudo apt-get install kubuntu-desktop

```you might then (once you have a gui) want to get rid of the gnome (ubuntu-desktop) by using this
[http://www.psychocats.net/ubuntu/purekdedapper](http://www.psychocats.net/ubuntu/purekdedapper)

---

### Post by EnigmaticCoder on 2010-11-18
KDE Works fine, except that it forces me into low graphics mode at bootup. See this thread: [http://ubuntuforums.org/showthread.php?t=1625087](http://ubuntuforums.org/showthread.php?t=1625087)

---

### Post by theozzlives on 2010-11-18
do he following:
```
sudo apt-get install xubuntu-desktop
```

---

### Post by Hippytaff on 2010-11-18
out of interest, do you have an nvidia graphics card?

---

### Post by EnigmaticCoder on 2010-11-18
> **Hippytaff said:**
> out of interest, do you have an nvidia graphics card?

Yes.

(Note: I fixed the problem)

---

