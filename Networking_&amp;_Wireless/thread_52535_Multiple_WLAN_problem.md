---
title: "Multiple WLAN problem"
date: 2005-07-28
forum: Networking &amp; Wireless
---

### Post by lawi on 2005-07-28
Hi all, newbe problem...
I have a WLAN at work and one at home both WEP encrypted but with different keys...

Problem is that Ubuntu dosen't manage to swap between the two networks...

If I use essid any it looks like it hooks up to first available WLAN (offcourse using the wrong key :)) and then just stop there instead of trying the next available WLAN.

When I do a iwlist scanning I see multiple WLANs but it looks like it only tries the first one found??

Right now I have to manually edit /etc/network/interfaces and then restart networking

Thanx in advance
Lars

---

### Post by spd106 on 2005-07-30
Hi, you can setup different locations in the network admin tool, then it's just a case of opening it up and switching between them. 

There's also something in the man pages for interfaces. I'm just not confident enough to try to work it out though. I'm still a bit of a newb.

Alternatively you might try the GTK wifi project. I've not tried it yet but they are working towards something that works automatically.

I've also heard that breezy uses a new system that should work better. But that's two months away.

I hope this helps. Please post back if you work it out.

---

### Post by lawi on 2005-08-01
I found an easy solution... Install and use Whereami

---

