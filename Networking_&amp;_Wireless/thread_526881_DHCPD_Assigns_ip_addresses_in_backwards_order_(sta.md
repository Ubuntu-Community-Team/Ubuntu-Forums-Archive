---
title: "DHCPD Assigns ip addresses in backwards order (starts with 192.168.0.254)"
date: 2007-08-16
forum: Networking &amp; Wireless
---

### Post by statictonic on 2007-08-16
[http://www.pcraider.com/dhcp](http://www.pcraider.com/dhcp)

That's a link to my config file since it's rather long.

The first IP address that dhcpd assigns is 192.168.0.254 then 253 252 and so on as opposed to starting with 1.

Anyone have any idea why it is doing this?

---

### Post by noob12 on 2007-08-16
Your range spec starts at 0 on the subnet and extends to 254.  This overlaps your fixed addresses and your gateway on that subnet.  You should start the range of dynamic addresses well above the fixed ones, say at 192.168.0.100.

Try the range change and see if that makes any difference.  You shouldn't have them overlap fixed assignments in any case.

I have a very similar config on one of my boxes  but I start mine above the fixed addresses and dhcpd does assign going up from the bottom.  It's running a slightly different version of the ISC dhcpd though which might behave differently.

---

### Post by statictonic on 2007-08-18
I changed(edited config file and restarted dhcp-server) it so that the range doesn't  overlapped with the manually assigned one, so it should start at 100 now, but it still is giving out .254 as the first address.

Any other ideas?

---

### Post by noob12 on 2007-08-18
Sorry.  No other ideas.   Also, it sounds like it's not behavior you should count on.  I checked a more recent version of ISC dhcpd on my Fedora box and it says in its dhcpd.conf man page that not only are addresses no longer assigned in ascending order, it assigns them based on a hash, so they will be in a seemingly random order.   So at some future upgrade, you'll probably see that behavior as well.

---

