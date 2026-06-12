---
title: "Network Manager does not detect my wireless device"
date: 2006-10-28
forum: Networking &amp; Wireless
---

### Post by Chris107 on 2006-10-28
I followed nbound's tutorial on setting up my bcm4318 in my HP L2000 and everything works fine.  However Network-Manager keeps telling me no network devices were found so it won't scan for networks.  I can connect to my router by manually typing in the name when configuring it but it won't scan for other routers and display them.  Anything I can do to fix it?

---

### Post by gotgenes on 2006-10-28
Did you comment everything out of /etc/network/interfaces except the following lines?
```

auto lo
iface lo inet loopback

```
Everything else should have a "#" in front of it.

---

### Post by Chris107 on 2006-10-28
Thank you so much.  I put a # to comment all devices except my loopback and the WLAN settings that showed up.  My applications now pick up my device and mainly Network-Manger works now.

Thanks again.

---

### Post by saxsux on 2006-10-31
Hi :-)
I'm having the same problem as Chris107; Network Manager is only detecting my wired interface, not my wireless one.
I've commented out everything except loopback in /etc/network/interfaces, but that hasn't done anything.
If it makes any difference, my wireless card is running via ndiswrapper.

---

### Post by -Chi.0 on 2006-10-31
Check this link for help w/ NdisWrapper on Edgy](*,) 
[http://ubuntuforums.org/showthread.php?p=1692550#post1692550]("http://ubuntuforums.org/showthread.php?p=1692550#post1692550")
I hope this helps:-k

---

