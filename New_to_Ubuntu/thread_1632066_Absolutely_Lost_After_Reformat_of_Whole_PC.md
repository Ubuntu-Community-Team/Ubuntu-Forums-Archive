---
title: "Absolutely Lost After Reformat of Whole PC"
date: 2010-11-27
forum: New to Ubuntu
---

### Post by OGalekos on 2010-11-27
Hey guys, I'm very new here, so please bare with me.

How do I get back on the partition that I've made before the necessary complete wipe of my whole HD had to be made (Faulty and Buggy - So I had to wipe my HD with Windows 7 Boot Disk)...I need to install Ubuntu back on that partition again but don't know how?

I haven't tested anything yet at all on my own, just wanted to hear from you guys on what to follow up on...I hope you understood me, I'm quite not sure about this either myself.

---

### Post by muteXe on 2010-11-27
Not sure I understand.
What OS do you currently have on your machine?

---

### Post by OGalekos on 2010-11-27
> **muteXe said:**
> Not sure I understand.
What OS do you currently have on your machine?

I have Windows 7 right now working, but as I was trying to state here that I already have seemed to have dual boot in my PC, I have a custom PC built from newegg.com, nothing from Dell or Anything like that, but I wiped after doing that sucessfully after toying with Ubuntu 10.04 and I decided to wipe completely and seeing it still has my dual boot in effect but has no files on it, the partition is still there but empty.

---

### Post by muteXe on 2010-11-27
Nope, sorry, still not getting you. That was a very long sentence :)  Maybe i'm a bit simple today and someone else can understand.

If you have an ubuntu live CD, you could boot off this, then use 'gparted' to look at all of your partitions.  If you could do that and post a screen shot on here that would make things a bit clearer.

---

### Post by OGalekos on 2010-11-27
> **muteXe said:**
> Nope, sorry, still not getting you. That was a very long sentence :)  Maybe i'm a bit simple today and someone else can understand.

If you have an ubuntu live CD, you could boot off this, then use 'gparted' to look at all of your partitions.  If you could do that and post a screen shot on here that would make things a bit clearer.



I'm trying to explain that I already installed Ubuntu before, and I wiped after doing so and the partition is still there after the wipe, I was assuming if I ran this LiveCD to install, will it get on the exact same partition I made before wipe?

---

### Post by muteXe on 2010-11-27
Before you use the live CD to install use the live cd to run 'gparted' just to double-check the partition you want to install to is there. You can also then make a note of the name of that partition e.g sda1, sda2 etc.
You can use gparted, or do a:
```

sudo fdisk -l

```
from a terminal. This will give you the same information as gparted.

---

### Post by OGalekos on 2010-11-27
Thank you, that did the trick.

---

