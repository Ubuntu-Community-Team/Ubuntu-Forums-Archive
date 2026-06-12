---
title: "ipw2200 ieee80211 not compiling modules error"
date: 2005-10-09
forum: Networking &amp; Wireless
---

### Post by asterix404 on 2005-10-09
I just tried to follow the howto for the ipw2200 and I got to the point of doing the ieee80211 make and I get the error that 

"no rule to make target 'modules'" stop

and I don't know what to do. Does anyone ave a fix for this? If I compiled the ieee stuff as modules inside of the ubuntu kernel would that work or not?

---

### Post by MrNamjama on 2005-10-09
I had a similar problem when I was installing one of those packages, too. Be sure that you do not have any spaces in the path leading to the folder where you run 'make'. I cannot verify it now since I don't have my computer handy, but either the ipw or the ieee package actually went ahead and created new folders for every space separated word in the folder name, then tried to 'make' inside them and failed because there was nothing in the directory...

I might have misinterpreted the reason for failure (I'm not too familiar with make rules and such) but the problem was definitely the spaces in folder names for me.

---

