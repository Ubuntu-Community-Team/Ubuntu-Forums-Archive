---
title: "cant boot ubunru 8.10 after install"
date: 2008-12-31
forum: New to Ubuntu
---

### Post by wenn_die on 2008-12-31
I had some teething problems installing the ubuntu os, which is installed as a dual os with windows xp; with help these have been solved. Now I cant actually run ubuntu. I get the ubuntu circle, and the progress bar loads to about 98%, then the screen goes black and nothing. I am forced to reset my computer each time I try it. I was advised to boot without the flash screen but the text runs so fast cant read the last line.I'd be happy to relay any of the specs of my computer of that helps? 

I would really like to persevere and get linux working.:confused:

---

### Post by bumanie on 2008-12-31
Have you tried booting into recovery mode? Try that and post back whether it booted or not.

---

### Post by Michael.Godawski on 2008-12-31
hi,

if you are able to boot into the recovery mode, run the 
```
dmesg
```
to see for errors.

Might be an ati related graphic issue... what is your graphic card?

---

### Post by wenn_die on 2008-12-31
OK, about to try the recovery mode, (after I watch the 9pm fireworks).
I have an ATI Radeon HD 3880 graphics card,, I know its a bit of overkill, but it was on sale!

---

### Post by Michael.Godawski on 2008-12-31
Hm, perhaps when you have Internet you can download the Radeon HD drivers according [to this guide]("https://help.ubuntu.com/community/RadeonHD") in recovery mode?

---

### Post by wenn_die on 2008-12-31
When I run dmesg I it goes to:
17.387229] ip_tables: (C) 2000-2006 Netfilter Core Team

If I try dpkg it says:
could not resolve 'security.ubuntu.com' and could not resolve 'au.archive.ubuntu.com' amongst many other 'failed to fetch...'messages. I guess this means I dont have internet with ubuntu.

I tried to get the radeonhd driver, but if my assumption is correct (that I dont have internet) this would explain the 'failed to fetch...' and 'could not resolve...' messages there.

---

