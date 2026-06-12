---
title: "Wireless not working"
date: 2007-10-30
forum: Networking &amp; Wireless
---

### Post by weaverworld on 2007-10-30
All

I have Ubuntu 7.10 sitting on a Thinkpad X60 with an internal Intel 3945 wireless card. I use Network Manager to connect to wireless networks but so far my success in actually being able to use this have been close to zero.

Network Manager finds the network and I can associate to them, at least that is what NM tells me, but I am unable to actually use the wireless network. I have Macintosh and Windows machines hooked up to the same networks and they all work like a charm but my Linux simply won't play.

I have setup different wireless routers (Airport, Linksys, D-link), using No encryption, WEP64, WEP128, WPA and WPA2 but none work. What usually happens is that NM-applet tries to associate, succeeds but then goes from 80% to 0% and keeps changing between these two values.
On the odd occasion I do manage to get an IP-address but that is really a crapshoot, when doing dhclient eth1 I rarely get a reply and when I do I can't ping the wireless router that delivers the DHCP instead I get "subnet cannot be reached" error from my wireless card.

Since I use my laptop in my work I can't afford not being able to use my wireless but before I go back to windows I want to see if anyone have seen anything like this before.

Setup is:
Lenovo X60
Ubuntu 7.10
Intel 3945 wireless card

Please help a newbie!

---

