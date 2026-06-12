---
title: "enable wireless disappeared"
date: 2006-10-17
forum: Networking &amp; Wireless
---

### Post by motrennoc on 2006-10-17
HELP
I finally got my wirless card working. (Dell true mobile 1300 mini PCI)
I finally got the WEP key at home working, it worked at the coffee shop and picked up wireless signals everywhere.
Things were good
Then, all of the sudden the "enable wireless" tick has disappeared from the Network manager aplet.
I've gone into network settings and tried to activate and deactivate eth1 (it says it is active)
I think it may be something I did by typing "sudo nm-applet" (I'm new to linux and thought it would run the network mangager.) All it did was sit there with no new command line and that's about the time the "enable wireless disappeared" I've searched around and haven't been able to find any information on this. Any ideas?

---

### Post by Chua-Chua on 2006-10-17
Did you check that the wireless card is turned on?
There is usually a button/hotkey/switch which will turn it on for you.

That's the first thing I could think of.

You might also check your network interfaces.

---

### Post by motrennoc on 2006-10-17
Hmm, that's a good thought. It would be hard to accidentally hit (function and #1 key) but entirely possible.
thanks

---

### Post by motrennoc on 2006-10-18
Nope, Unfortunatly not the problem, good thought though.

---

### Post by motrennoc on 2006-10-22
So, I finally figured out why my wireless network "disappeared" from network manager.

I found this in _Ubuntu Hacks_ by Jonathan Oxer, Kyle Rankin and Bill Childers.

In Hack #42
"NetworkManager cannot manage any cards that have entries in */etc/network/interfaces*. If you've added your network card to that file, make sure you remove it before you start working with Network manager."

I removed this from the /etc/network/interfaces file

"auto eth1
iface eth1 inet dhcp
wireless-essid home"

It worked like a charm, well almost, I'm still struggling with the WEP encryption. But, the wireless networks available are listed by network manager and the "enable wireless" selection is back.

---

### Post by squibT on 2006-10-22
I had the same problem...even reboot didnt bring it back...ran the same cmd too with the same results. I fixed it by disabling my wireless connection in Network Settings and reboot brought it back. My wireless signa meter was also missing till I did this. Funny thing is now my Eth0 wireless connection in Network Settings is still disabled but NWM and wireless signal meter are working fine along with my wireless access. BIZZARE.

---

### Post by motin on 2007-08-15
> **motrennoc said:**
> So, I finally figured out why my wireless network "disappeared" from network manager.

I found this in _Ubuntu Hacks_ by Jonathan Oxer, Kyle Rankin and Bill Childers.

In Hack #42
"NetworkManager cannot manage any cards that have entries in */etc/network/interfaces*. If you've added your network card to that file, make sure you remove it before you start working with Network manager."

I removed this from the /etc/network/interfaces file

"auto eth1
iface eth1 inet dhcp
wireless-essid home"

It worked like a charm, well almost, I'm still struggling with the WEP encryption. But, the wireless networks available are listed by network manager and the "enable wireless" selection is back.

Thanks a million! I had been running pppoeconf and afterwards the mentioned tick disappeared just the same. Apparently it modified /etc/network/interfaces so now when everything there is commented the tick is back after a restart of NetworkManager. 

Hope you got that WEP going! Tip: If you just changed security level of your WLAN (like enabling WEP/WPA) you might need a reboot or Ubuntu will not get the hang of it.

---

