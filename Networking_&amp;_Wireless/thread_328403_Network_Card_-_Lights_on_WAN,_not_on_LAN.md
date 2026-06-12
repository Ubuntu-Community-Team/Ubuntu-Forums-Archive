---
title: "Network Card - Lights on WAN, not on LAN?"
date: 2006-12-30
forum: Networking &amp; Wireless
---

### Post by adamonline on 2006-12-30
Hello, I'm not sure if this is an issue with my Ubuntu configs, a hardware issue, or just a non-issue.


PROBLEM:

I have an Intel PRO/1000 MT Desktop Adapter, with a patch cable going to a linksys 8-port gigabit switch.  The lights on the back of the network adaptor don't come on, and there's no light on the switch indicating connectivity.

I'm afraid I'm not sending any signal out.  I'm trying to use the Intel card (eth1) as the output to my LAN, using my Ubuntu machine as a DHCP server.  I haven't been able to get it to assign an IP to my windows machine, though, so I thought I'd find out if the card's even connecting to the switch.


TROUBLESHOOTING:

I have a Realtek NIC (eth0) that successfully connects to the internet, no problems there. I have a WinXP computer that *is* showing connectivity at the switch when plugged in; but that's irrelevant to my Intel NIC.  Also, if I take the output from my cable modem out of eth0 (the realtek card) and plug it into my Intel card (eth1), the lights on the back of the Intel card will come on, but when I plug my switch into the intel card, I get nothing.


QUESTION:

What the HECK is goin' on?  I can't really phrase a specific question; i just want to make sure my Intel NIC is actually connected to my network switch, because it doesn't seem like it's linking up.  How would I ping my windows machine if it doesn't have an IP assigned to it? Which line from my etc/network/interfaces would I use to ping my Ubuntu box from my Windows box?


I hope I worded that okay and it's not too difficult to follow!  I'd be willing to draw a diagram and cut and paste any files that are needed, if there are any that will help.  Thanks!

-ADAM

---

### Post by adamonline on 2006-12-31
Argh, once again I solved my own problem :)  As always, after pulling my hair out and posting for help :rolleyes:   It was just the cheap generic patch cables (I tried two).  They didn't fit right; the plastic cover over the clip held the cable just far enough out of the connector for it to not work.  I presume it was merely "clicking in" on the metal trim around my expansion slot.

---

