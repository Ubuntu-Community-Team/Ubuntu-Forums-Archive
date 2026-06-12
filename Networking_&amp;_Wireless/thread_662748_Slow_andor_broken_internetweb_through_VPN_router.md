---
title: "Slow and/or broken internet/web through VPN router"
date: 2008-01-09
forum: Networking &amp; Wireless
---

### Post by bignickel on 2008-01-09
I'm having a very strange problem with slow and/or broken internet access using Gutsy.  I've been using Ubuntu for a few months at work with no problems at all.  Then our "IT guy" installed a new VPN router, and now my internet access seems to be crippled.  Web sites will resolve quickly (so it's not a DNS problem), but then only part of the HTML will load and the status bar will stay at that position for quite a while.  And it doesn't matter which browser I use.

I can ssh into my machine at home, and it connects very fast, but hangs if I run a command that produces lots of output (like ls on a large directory) or try to to forward an X window.  So it can't be that it's limiting certain packets, because ssh is encrypted, right?

To top it all off, they just gave me a new computer, and it came with Windows on it.  It's internet access seems to be fine, but I set it up for dual boot and installed Gutsy, and still have the same problems in Linux.

I'm banging my head against my laptop in frustration with this.  I've used Ubuntu for so long but since this VPN router went in it's basically unusable.  I don't want to switch back to Windows!

---

### Post by ARhere on 2008-01-09
I am not what to say to help you with this.  It sounds like the problem is defiantly with the VPN holding your packets for what-ever-reason.

You said the problems go away when you use Windows?  What was the Windows browser?  If it was IE, then try Firefox on Windows and see what happens.  This will at least help in isolating the problem down to OS or browser.

EDIT:  Find out if the VPN is a D-Link.  If it is, your solution is a base ball bat!  Where to apply your solution is the next question.

-AR

---

### Post by merlinesq on 2008-01-09
It may be psychosomatic, but my web-browsing through firefox seems much slower since I upgraded to Gutsy.  It's an old slow PC, but I am sure it was quicker under Feisty.

Tried my work laptop through the same router (still using firefox, but running XP) and nice and quick.  OK so it's a quicker machine, so not a quantative test.

The question I suppose I am asking is, has anything about the way that packets are sent benn changed between Feisty and Gutsy that might require me to change settings in my router ?

---

### Post by bignickel on 2008-01-09
It's not Firefox in my case, Opera does the same thing, as does POP email, and ssh.  So there's something with the router (it's a Linksys RV042).  Everything (browsing in IE or firefox, ssh, POP) works in Windows.  I don't understand how the operating system could possibly affect which packets are getting though.

---

### Post by ARhere on 2008-01-09
Might be a stupid suggestion, but I noticed a firmware update for your model number.  You should ask your IT guy if he updated it before installing it on the network.

-AR

---

### Post by bignickel on 2008-01-11
So it turns out it was the firmware.  It's been upgraded and now everything works fine, which is great because this had the air of one of those problems that may never have a solution.  Thanks!

---

