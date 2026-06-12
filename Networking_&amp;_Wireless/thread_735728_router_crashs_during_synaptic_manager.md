---
title: "router crashs during synaptic manager?"
date: 2008-03-25
forum: Networking &amp; Wireless
---

### Post by kamasabi on 2008-03-25
Gents,

I have stumbled across a rather perplexing problem......as weird as it may sound, whenever I run the synapic package manager to download files, mostly larger ones, it actually causes my router to quite literally crash.  Currently using a netgear WGT624v3.    And it only happens with SPM, which is the weirdest thing.  I confirmed this by trying to log in to the router on another windows machine, and not only did it lose its connection to the intertrode, but it wasn't able to log in at all either to the router.  I usually crashes about 20 or 30 seconds after starting on a larger file, and then it just stop, and the network dies.  Has this happened to anyone else before?   I'm going to be looking for a new router pretty soon anyway (gigabit networking ftw :) ), but was just wondering if anyone else came across this problem...while not a severe issue, it is pretty annoying.  

Any info is appreciated!!!

Thanks,

Kama

---

### Post by jetsam on 2008-03-26
Post #7 in this thread: [http://ubuntuforums.org/showthread.php?t=197046&highlight=WGT624v3]("http://ubuntuforums.org/showthread.php?t=197046&highlight=WGT624v3") 
...mentions your router and problems with synaptic.  Turning keyword blocking off seemed to help in that case.  

If that doesn't work, try disabling everything you can under the "Content Filtering" menu.  Apt and Synaptic use http, and it seems plausible that they're giving your router's content filter an aneurysm.

---

### Post by kamasabi on 2008-03-29
tried doing this, and still didn't work....BUT NO WORRIES!!!  I just got a brand new Dlink DGL-4500, so its good :)

Thanks for help though

---

