---
title: "configured additional DNS server in VPN connection not being used"
date: 2016-12-10
forum: Networking &amp; Wireless
---

### Post by dccarson2 on 2016-12-10
I'm pretty sure this stopped working when I upgraded from Ubuntu 16.04 to 16.10.

I have a VPN connection, configured via NetworkManager, with an additional DNS server.   I can also see this value in [SIZE=1][FONT=courier new]/etc/NetworkManager/system-connection/VPN connection 1[/FONT][/SIZE].

```
[ipv4]
dns=10.6.24.31;
dns-search=mycorp.com;
method=auto
never-default=true
route1=10.0.0.0/8

```

Before my upgrade to 16.10, I would connect to the VPN and would immediately be able to resolve hostnames inside the VPN.  Now, I cannot.  Unfortunately, this is all complicated by the use of dnsmasq, making it very difficult to know how to debug or work around the problem.  For example, I cannot look in [SIZE=1][FONT=courier new]/etc/resolv.conf[/FONT][/SIZE] and expect to see 10.6.24.31 (our nameserver inside the VPN).

Can someone tell me where to start looking, perhaps?  I'm happy to provide more information here.

---

### Post by david224 on 2017-02-02
A general solution, so that the VPN uses the correct DNS settings, is to comment out the line '[COLOR=#111111][FONT=Consolas]dns=dnsmasq[/FONT][/COLOR]' in [COLOR=#111111][FONT=Consolas]/etc/NetworkManager/NetworkManager.conf and then restart network manager.[/FONT][/COLOR]

---

