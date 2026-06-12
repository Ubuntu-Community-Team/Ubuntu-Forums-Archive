---
title: "wlan0 configured, but dhclient can't get offer"
date: 2006-10-11
forum: Networking &amp; Wireless
---

### Post by fulat2k on 2006-10-11
Hi folks,

I've been trying to configure Dapper to use a wifi connection secured using WEP.  I'm able to see that it's able to locate the base and the signal is rather strong.  However, dhclient just doesn't seem to work when trying to obtain a dhcp address from the router.  

I have another eth0 interface which I've disabled.  I've used eth0 previously and it didn't have any problems getting the address via dhcp.  Could having 2 network interface be the problem or do I have to disable WEP?

Any help is greatly appreciated.


Thanks.

---

### Post by fulat2k on 2006-10-12
Hi folks,

A bit of findings which is even stranger.  After a fresh reboot and with the wlan0 interface configured as static, I was able to ping the router for a couple of seconds after the system has booted.  

However, I started getting "Destination Host Unreachable" after 1-2 mins the system has started.

Anyone knows what's going on?



Thanks.

---

