---
title: "CPU Lockup after following guide"
date: 2008-10-14
forum: Networking &amp; Wireless
---

### Post by vyperstrike on 2008-10-14
I was having some issues with my wireless, so I did a quick search. Found this thread:
[http://tennessee.ubuntuforums.com/showthread.php?t=766560&highlight=cpu+lockup](http://tennessee.ubuntuforums.com/showthread.php?t=766560&highlight=cpu+lockup)
Followed the steps one by one, didn't think I had a problem, till I hit the end and tried to reboot. Now I get a soft lockup upon trying to boot.

Getting it to spit info at me when I boot, it gets to here:

* Starting Samba daemons               [ OK ]
[   65.351921] ndiswrapper (NdisWriteErrorLogEntry:191): log: C000138D, count: 1, return_address: f8c71d9d
[   65.351978] ndiswrapper (NdisWriteErrorLogEntry:194): code 0x10e
[   76.875377] BUG: soft lockup - CPU#0 stuck for 11s! [events/0:6]
[   88.666299] BUG: soft lockup - CPU#0 stuck for 11s! [events/0:6]

Continuously repeating the soft lockup message.

Any solution?

---

### Post by vyperstrike on 2008-10-14
Update:
I figured out how to boot into a root command prompt and removed the driver in ndiswrapper, and the compy now boots fine.

Dunno what caused it to go crazy.

---

