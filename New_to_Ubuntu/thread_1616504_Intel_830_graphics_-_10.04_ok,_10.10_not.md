---
title: "Intel 830 graphics - 10.04 ok, 10.10 not"
date: 2010-11-08
forum: New to Ubuntu
---

### Post by anewguy on 2010-11-08
I guess I'll add one more to the "oops" column for 10.10.

I just aquired an older Gateway 200STM laptop from craigslist EXTREMELY cheap.  Loaded 10.04 to it - no problem with graphics.  I then did an install of 10.10 - get a black screen with no cursor and have to crtl-alt-F1 to get to a terminal window.  I know it runs old Intel graphics - if I remember correctly it's something like 8x830 (can't remember what the "x" is, don't have it powered up right now).

So, at least from an X standpoint, something changed from 10.04 to 10.10 to where the graphics are no longer supported out of the box, which means I'll be stuck at 10.04 for now as I really don't want to screw with it much.

I'm trying to get a cheap laptop running Ubuntu, with wine for a couple of must-have Windows apps (don't ask, been there, no easy way to migrate to Linux) and sending it to my parents.  They are elderly, and have always had problems getting viruses and trojans, no matter what I do.  I guess they just don't keep things up to date and don't scan.  It's always been a tough time walking them through getting things straighten out over the phone since they are 1200 miles from me.  Their latest was the last straw for my dad and he disconnected his internet.  I'm trying to get a cheap ubuntu setup to them to try for a while since Linux is relatively safe from most hacking efforts compared to Windows (won't debate "relatively" either - been there, done that) ;)

SO, does anyone know if they just dropped support for that graphics adapter, or will I need to eventually get online and do an update then check hardware drivers? (Nothing is the for now, but I also don't have any internet on that laptop yet - still working on that - have a different wi-fi adapter on the way that will support WPA2).

Thanks in advance!
Dave ;)

---

### Post by Rubi1200 on 2010-11-08
If you get to a terminal, please post the output of ```
lspci | grep VGA
```The problems with Intel graphics cards, outlined here ([https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes](https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes)), were supposed to have been, to a certain extent, resolved with 10.10.

However, after contacting Stefan Glasenhardt, who packaged the GTT Incoherency Patch for 855GM cards, it seems that there are still problems with these chipsets and 10.10: [https://wiki.ubuntu.com/X/Bugs/Mavericki8xxStatus](https://wiki.ubuntu.com/X/Bugs/Mavericki8xxStatus)

Stefan told me that he hopes all these problems will be finally resolved with 11.04.

I have been testing the workarounds on both 10.04 and 10.10 and I hope this information helps with your specific issue.

Off-topic: congratulations on reaching the 3,500 mark and being able to add a custom title :-)

---

### Post by mosaic2s on 2010-11-08
For parents or people who are not computer savvy, stick to 10.04 version. They are looking at getting the e-mailing or chat done. not spending time getting help or resolving issues. Which will crop up more frequently with newer version like 10.10 or 11.04.

I had used 8.04 earlier and shifted to 8.10 and 9.04 but then realised that printers and graphic card support was easier and comprehensive in 8.04.

Finally, got 10.04 - happy since then.

---

### Post by anewguy on 2010-11-08
> **Rubi1200 said:**
> If you get to a terminal, please post the output of ```
lspci | grep VGA
```The problems with Intel graphics cards, outlined here ([https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes](https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes)), were supposed to have been, to a certain extent, resolved with 10.10.

However, after contacting Stefan Glasenhardt, who packaged the GTT Incoherency Patch for 855GM cards, it seems that there are still problems with these chipsets and 10.10: [https://wiki.ubuntu.com/X/Bugs/Mavericki8xxStatus](https://wiki.ubuntu.com/X/Bugs/Mavericki8xxStatus)

Stefan told me that he hopes all these problems will be finally resolved with 11.04.

I have been testing the workarounds on both 10.04 and 10.10 and I hope this information helps with your specific issue.

Off-topic: congratulations on reaching the 3,500 mark and being able to add a custom title :-)

Thanks!  I already knew about the 855 problems, as outlined in your first link - it seems this has been an on-going problem for a few releases that I remember.

My graphics is the 830, so the first link doesn't apply.  However, the second link does as it mentions the 830.  I'll give that a try tonight at home and let you know how that goes.

Thanks again!
Dave ;)

---

