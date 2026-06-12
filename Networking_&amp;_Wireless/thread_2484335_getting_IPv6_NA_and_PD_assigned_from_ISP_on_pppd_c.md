---
title: "getting IPv6 NA and PD assigned from ISP on pppd connection"
date: 2023-02-23
forum: Networking &amp; Wireless
---

### Post by brookiemonsta on 2023-02-23
Here's the fix for a problem that I have scoured the internet high and low for, but found nowhere.

[FONT=arial black]**Background**
[/FONT]The situation is an Ubuntu box is being used as a firewall/router to connect a home network to a UK ISP. Normal instructions have been followed to configure pppd to log in and acquire an IPv4 address. So /etc/ppp/peers/dsl-provider looks like this:```

noipdefault
defaultroute
defaultroute6
replacedefaultroute
hide-password
noauth
persist
maxfail 0
plugin rp-pppoe.so
nic-enp1s0
usepeerdns
user "xxxx@zzzz"
```

We have also asked the ISP nicely to assign us an IPv6 /48. ISP has assigned us exactly this, and tells us that we need to acquire NA and PD via a DHCPv6 mechanism rather than manually configuring it. So wide-dhcpv6-client has been configured correctly to request and handle this, /etc/wide-dhcpv6/dhcp6c.conf looks like this:```

interface ppp0 {
        send ia-na 0;
        send ia-pd 1;
};
id-assoc na 0 { };
id-assoc pd 1 { };

```

Firewall rules have also been configured to protect the router and local network from the big bad internet, but without blocking necessary DHCPv6 traffic.

[B][FONT=arial black]The problem
[/FONT][/B]
The problem is that despite setting everything up to work, it doesn't. IPv4 address is configured correctly, but IPv6 only sometimes configures. When the temporary IPv6 address expires renewal often doesn't happen, and frequently IPv6 does not configure at all.

[B][FONT=arial black]The Fix
[/FONT][/B]
It's relatively simple:

Configure pppd interface (ppp0 in my case) to configure an IPv6 address using SLAAC.
In the case where you are not forwarding traffic you can use sysctl to set net.ipv6.conf.ppp0.accept_ra to 1 to make it accept router advertisements. However, in the case where forwarding is enabled (which I want because this device is a router), accept_ra=1 is not enough, router advertisements will be rejected. Instead we need to set accept_ra = 2, which forces the interface to accept router advertisements despite also being set to forward packets.

We also need to set pppd interface as the default route.

These two steps allow the DHCPv6 process to work as required and NA and PD address assignments can then happen.

**Create and edit** a new file /etc/ppp/if-up.d/1accept_ra```

#!/bin/sh
# Ensure accept_ra = 2 so that we slaac our ppp interface.

sysctl -w net.ipv6.conf."$PPP_IFACE".accept_ra=2
ip -6 route add default dev ppp0

```

This file is run every time pppd brings up the ppp0 interface, so that it correctly configures itself and picks up the relevant addresses.

---

### Post by droidfreak2 on 2023-11-04
Thank you!
This was exactly what I was looking for :)

---

