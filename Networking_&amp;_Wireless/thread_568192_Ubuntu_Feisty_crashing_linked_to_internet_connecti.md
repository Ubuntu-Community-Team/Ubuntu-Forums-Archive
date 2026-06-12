---
title: "Ubuntu Feisty crashing linked to internet connection"
date: 2007-10-05
forum: Networking &amp; Wireless
---

### Post by glasafmt on 2007-10-05
Hello All

I am running Feisty Fawn ubuntu and had several months using it with no problems with the wireless networking.  I am using a Ralink RT61 wireless card.

Whenever another computer on the same network gets an IP address from my router my computer would crash.  I solved this problem by assigning a static IP address.  The computer now crashes if I turn it on when my wireless router is not switched on.  There is obviously some problem with the way the computer is getting a network connection, but this is outside of my experience to figure out why it is happening, and I don't seem to be able to find anything online.

Any help would be very gratefully received.

Thanks

Lee Russell

---

### Post by n00bWillingToLearn on 2007-10-05
Do you see any errors that seem possibly relevent if you run dmesg after a crash? Also, how badly does it crash? For instance can you still get to a console with ctrl+alt+F1 , or restart X with ctrl+alt+backspace , or alt+sysrq+k ?

---

### Post by glasafmt on 2007-10-06
>  Do you see any errors that seem possibly relevent if you run dmesg after a crash? Also, how badly does it crash? For instance can you still get to a console with ctrl+alt+F1 , or restart X with ctrl+alt+backspace , or alt+sysrq+k ?

I will check dmesg after the next crash.

In response to how badly it crashes, I can do nothing other than turn the computer off and on again, nothing else works.

Lee

---

### Post by glasafmt on 2007-10-07
> I will check dmesg after the next crash.

I can see nothiing obvious in dmesg.  If no-one has any more ideas, it is a problem I can easily live with.

Lee

---

