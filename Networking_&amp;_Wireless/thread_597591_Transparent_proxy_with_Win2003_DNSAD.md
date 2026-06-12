---
title: "Transparent proxy with Win2003 DNS/AD"
date: 2007-10-30
forum: Networking &amp; Wireless
---

### Post by ChamPro on 2007-10-30
I'm trying to take the idea in [this post]("http://ubuntuforums.org/showthread.php?t=327097") a little further. The idea is to get a setup that's mapped like [this]("http://www.isaserver.org/img/upl/image0141182945471604.gif") but with different components.

I want to have the DNS requests go to our Windows 2003 ActiveDirectory/DNS server (inside the LAN) first. The requests then go to the proxy/cache running Ubuntu (maybe Squid?) and then the go outside the firewall (a SonicWall device). I can do the transparent proxy with Squid, but have having issues with it redirecting the traffic correctly with IPtables.

I found [this howto]("http://www.cyberciti.biz/tips/linux-setup-transparent-proxy-squid-howto.html"), but I need to put Squid on port 80 for the incoming request interface just so the DNS server redirects correctly.

Any pointers on the setup?

---

