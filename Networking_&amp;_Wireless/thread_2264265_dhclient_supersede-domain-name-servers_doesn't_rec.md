---
title: "dhclient supersede-domain-name-servers doesn't recognize IPv6 addresses"
date: 2015-02-06
forum: Networking &amp; Wireless
---

### Post by kpatz on 2015-02-06
I recently replaced my old 8.04 firewall box with a new one running 14.04 server.

The box provides DNS for my home network, so I have dhclient configured to supersede the DNS servers to use its own instead of the ISP's.

Last night I did updates, and there was a kernel update so I rebooted afterward.  Then today I discovered my DNS wasn't working right--I couldn't resolve any of my internal DNS names while logged into the server.  After doing some digging, I found that /etc/resolv.conf had the ISP DNS servers instead of the ones I included in my dhclient.conf.  When I checked the syslog from last night's reboot, I found this:

```

Feb  5 21:18:32 mordac dhclient: /etc/dhcp/dhclient.conf line 21: : (58): expecting IP address or hostname
Feb  5 21:18:32 mordac dhclient: supersede domain-name-servers :
Feb  5 21:18:32 mordac dhclient:                                ^
Feb  5 21:18:32 mordac dhclient: /etc/dhcp/dhclient.conf line 21: expecting a statement.
Feb  5 21:18:32 mordac dhclient: supersede domain-name-servers ::1, 127.0.0.1;
Feb  5 21:18:32 mordac dhclient:                                              ^
Feb  5 21:18:32 mordac dhclient: /etc/dhcp/dhclient.conf line 27: semicolon expected.
Feb  5 21:18:32 mordac dhclient:
Feb  5 21:18:32 mordac dhclient: ^

```

My dhclient.conf has this in it, to override my DNS servers to be my own, and I provided both IPv6 and IPv4 addresses.  Apparently dhclient doesn't recognize the IPv6 address:

```

supersede domain-name-servers ::1, 127.0.0.1;

```

According to this: [https://bugs.debian.org/cgi-bin/bugreport.cgi?bug=537159](https://bugs.debian.org/cgi-bin/bugreport.cgi?bug=537159)

IPv6 support was added in 4.0.  I'm running isc-dhclient-4.2.4 so it should recognize an IPv6 address in a prepend or supersede line, right?  Apparently it doesn't.

Any suggestions?  I temporarily "fixed" the issue by editing /etc/resolv.conf by hand, and removing the IPv6 address from the dhclient.conf.  But it would be nice to be able to specify both the IPv4 and IPv6 addresses in the supersede line.

---

