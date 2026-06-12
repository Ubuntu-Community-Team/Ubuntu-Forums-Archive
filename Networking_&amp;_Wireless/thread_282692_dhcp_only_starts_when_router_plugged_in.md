---
title: "dhcp only starts when router plugged in"
date: 2006-10-23
forum: Networking &amp; Wireless
---

### Post by phil79 on 2006-10-23
Can someone please explain this.....

My DHCP server will not start unless I have my router plugged in...but it ONLY starts if the router is also running DHCP...

If I try and start DHCP manually in Ubuntu I get:

ubuntu:~>  sudo /usr/sbin/dhcpd3  eth0 -pf /var/run/dhcp3-server/dhcpd.pid -cf /etc/dhcp3/dhcpd.conf
Internet Systems Consortium DHCP Server V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)
Wrote 0 deleted host decls to leases file.
Wrote 0 new dynamic host decls to leases file.
Wrote 7 leases to leases file.

No subnet declaration for eth0 (0.0.0.0).
** Ignoring requests on eth0.  If this is not what
   you want, please write a subnet declaration
   in your dhcpd.conf file for the network segment
   to which interface eth0 is attached. **


Not configured to listen on any interfaces!


The eth0 works fine but just can't get DHCP to work unless the router is plugged in running DHCP...

](*,) 

Thanks

---

