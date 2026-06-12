---
title: "Wireless Network Hosting"
date: 2007-09-07
forum: Networking &amp; Wireless
---

### Post by peterbrewer on 2007-09-07
Hi, I'm off to university shortly.  My uni provides lan sockets in each room but not wireless.  I have a pda which connects through wireless and was wondering if anyone can tell me how i host a wireless network using my laptop and the wireless card inside.  Thanks.

---

### Post by rivalarrival on 2007-09-07
The EASIEST way to do it is to pick up a wireless router like the Linksys WRT54G. (Which is a fun toy anyway, once you install OpenWRT or DD-WRT firmware...  Google it)

If you want to do it with your laptop, though, you'll either have to set up the wireless card on your laptop as an access point or configure both your laptop and PDA for ad-hoc connections. I've never done this in Ubuntu, but this site looks like a good starting point:

[https://help.ubuntu.com/community/WifiDocs/Adhoc](https://help.ubuntu.com/community/WifiDocs/Adhoc)

You'll also have to setup some means of sharing your wired internet connection. The only way I know of is to configure your laptop as a NAT gateway using Shorewall.  I know other methods exist, I just never bothered to learn them once I got this working properly.

This link gives you a step-by-step for the configuration you need.
[http://www.shorewall.net/two-interface.htm](http://www.shorewall.net/two-interface.htm)

If I was doing it, I'd pick up the router or make friends with someone in the building who already has one.

---

