---
title: "Wireless looks fine but refuses to work"
date: 2007-06-15
forum: Networking &amp; Wireless
---

### Post by PhutterMan on 2007-06-15
I have an odd problem.

To begin, I recently updated to 7.04, and all was well, though I did not like Network Manager much, since I use my laptop both on campus (auto ip, a login page, no wep/wpa), my girlfriend's place (auto ip, wep) and home (manual ip, wep, and necessary to enter dns servers manually).  Network manager didn't seem to switch well between the different sets of setting.  In particular, it always forgot the DNS servers I needed at home.  But I digress.  I prefer wifi-radar.

So, today I removed network manager and went back to using wifi-radar.

Now, everything looks fine.  The connection looks like it is working, but it only seems to receive packets, not transmit any, and I cannot connect to any webpages or locations on the local network, nor can I ping anything.

If something *looked* wrong I'd have an idea of what to fix, but everything looks normal on ifconfig and iwconfig.  It even shows it as having transmitted a few packets, though not many, and having received tons.

So, any thoughts on this would be greatly appreciated.  I may just be overlooking the obvious, but nothing springs to mind.  The addresses, DNS, subnet mask, etc, are all correct, as is the key.  It tells me I'm connected!  But nothing.  And it isn't the network, I checked on another machine.

---

