---
title: "[SOLVED] Continuous network traffic on wireless internet"
date: 2008-02-21
forum: Networking &amp; Wireless
---

### Post by harry000 on 2008-02-21
Hi,

Recently, I installed netspeed applet. This applets monitors the network traffic. I am using Ubuntu Gutsy.

After installing it, it stated showing continuous traffic (both IN and OUT). Usually, this traffic is more than 100 kB/s (and reaches 300 kB/s too). OUT traffic also soemtimes cross 1MB/s

I also checked the network traffic using System Monitor and it shows the same IN and OUT speed.

I pretty sure that no application is using so much bandwidth. I installed Firestarter (a firewall). It shows same traffic (but there is no connections).

I have a Broadcom BCM43xx wireless card. 

As I have a wireless card, this traffic might just be the from that (because, my card would be getting all IN and OUT traffic from the router). But in that case, System Monitor, netspeed applet and Firestarer should not display any network traffic because it is not from my computer.

I am confused.

Any help on this topic will be appreciated.

Thanks

---

### Post by Beefeater on 2008-02-22
Install wireshark and look at the traffic, maybe that will shed some light.

---

### Post by harry000 on 2008-02-23
> **Beefeater said:**
> Install wireshark and look at the traffic, maybe that will shed some light.

yes, i did that. the traffic seems to be from all local IP address.. that mean... it is displaying total network traffic that my wireless card is receiving (and not the traffic that I AM USING)...

but, I am still confused. Why would it display that other traffic.

---

### Post by harry000 on 2008-02-23
Hi,

The problem is resolved.

I was using bcmw43xx-fwcutter for wireless card. This seems to be buggy. I just installed ndiswrapper and now there is no extra traffic on my connection.

---

