---
title: "SOS...repeating wlan connection drop:  thinkpad T41p, multiple wlan adapters..."
date: 2005-09-23
forum: Networking &amp; Wireless
---

### Post by xanderdad on 2005-09-23
"SOS" in this case seems to mean "same 'ol story" - after reading some of the similar posts in this forum today...

In my case I'm running Hoary, on a T41p, and *was* loving it for a while.  Then for some reason my home wlan connection started getting flaky.  Long DNS lookups - slow downloads, etc.

My WLAN components are:
DLink AirPlus 900 AP+ wireless access point connected to home LAN
Embedded thinkpad atheros wireless & a new Netgear WG511T wireless PCCard.

I can bring up a connection using either DHCP or fixed IP, on both the embedded atheros or the netgear pccard.  Using either wireless device, the most telling symptom for my connection problem seems to be this:

When I ping any other IP address, either on the home lan segment or out to the ISP  DNS host, the pings always experience ~25% packet loss.  And the dropped packets are in sequence.  IOWs, using a 1 sec ping interval, I'll get ~15-20 secs of successful pings, followed by 4-5 secs of failures. Then it picks up again for 15-20 secs, then fails again, and so on.  Is my wireless connection cycling up/down?

Should I invest in a different wireless access point device?  Is this a known problem with Ubuntu?  Should I wait for breezy?

BTW - when booting an XP partition on the same machine I get not ping failures.... the wlan connection ust stays up and fast.

---

