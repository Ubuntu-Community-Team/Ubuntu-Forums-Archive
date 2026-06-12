---
title: "How do I identify my video card?"
date: 2009-07-13
forum: New to Ubuntu
---

### Post by l951b951 on 2009-07-13
I'm running Hardy Heron on a Compaq Evo N610C laptop.  My graphics work out of the box, but videos can lag it occasionally, so i'd like to figure a way to max out my performance if I can.  The sticker on the laptop says it has an ATI card in it.  I have installed the ATI Catalyst control center and it gives me an error, that either no driver is installed or it is incorrectly configured.  My problem is that I don't know what exact video card I have, so I can't search for solutions and howto's to troubleshoot it.  What is the first step in identifying my video card?

---

### Post by LewRockwell on 2009-07-13
```
sudo lshw -C video
```

---

### Post by l951b951 on 2009-07-13
> **LewRockwell said:**
> ```
sudo lshw -C video
```

Thank you.  Now I know i have a Radeon Mobility M7 LW [Radeon Mobility 7500].

Now for the fun part.  Lol.

---

### Post by n2stc on 2009-07-13
> **LewRockwell said:**
> ```
sudo lshw -C video
```

Thanks from me too!  Is there a search-able compendium of ALL these commands?  I tend to forget them quickly!  :)

---

### Post by LewRockwell on 2009-07-13
> **n2stc said:**
> Thanks from me too!  Is there a search-able compendium of ALL these commands?  I tend to forget them quickly!  :)

mostly I google stuff I don't already know

who refuses to use the largest dictionary/encyclopedia in the history of the world?

.

---

