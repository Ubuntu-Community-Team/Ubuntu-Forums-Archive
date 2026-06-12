---
title: "Can't connect to broadband internet with Ethernet modem"
date: 2008-04-15
forum: Networking &amp; Wireless
---

### Post by iandravid on 2008-04-15
Hi, I'm a relative Linux n00b. I was pretty happy to finally see Ubuntu load up [some trouble with Jmicron controller], but internet won't work. The same setup worked flawlessly on the Knoppix LiveCD [I didn't test it while installin Ubuntu...but I suspect it must have] but now that I'm doing a native boot, I can't seem to connect. OS recognises the modem in Hardware manager, and it says I'm connected to a wied connection soon after I log in, but there's no internet.

I was checking every related thread and tried the Firefox IPv6 cheat, no luck. There was some mention of r1000 drivers for linux for the Realtek family, I couldn't find the r1000, so I got the official latest pack for the 8169 family and followed the instructions as best as I could

and after the
# make install
# insmod yadayada

I did
# lsmod | grep r8169 [I dunno what this does]
and it returned
r8169     32392   0  [and I dunno what this means either]

In any case, can you guys give me suggestions for possible problems? Exams coming soon...really need the Internet badly. Thanks in advance.

---

### Post by iandravid on 2008-04-19
Oh thanks anyway but the problem is solved. I did a re-install with the alternate install CD and let the DHCP aut-confifuration mess around throughly until it got the settings fixed.

---

