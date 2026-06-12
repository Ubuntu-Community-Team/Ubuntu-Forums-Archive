---
title: "Confirming dhcpd.conf changes have been applied"
date: 2014-06-01
forum: Networking &amp; Wireless
---

### Post by martech on 2014-06-01
Long time reader, first time poster.I just added a second range of ip addresses to my dhcp server by editing /etc/dhcp/dhcpd.conf.I restarted the isc-dhcp-server service.How can I confirm that it worked? viewing the dhcpd.conf file just shows me the changes I made, but I want to be sure that the server that is running will assign from that range.  Is there a way to make the service report on it's pools, or available addresses?  I checked /var/lib/dhcp/dhcpd.leases and it doesn't have any leases for the new addresses, but maybe they don't show up until they are actually leased?I wasn't sure if it the isc-server was using dhcp or dhcp3 so I edited both, but the dhcpd.leases file in dhcp3 hasn't been updated in over a year, so I figured it wasn't using that one.I referenced these pages to help me out:[https://help.ubuntu.com/community/dhcp3-serverhttps://help.ubuntu.com/community/isc-dhcp-serverThanks](https://help.ubuntu.com/community/dhcp3-serverhttps://help.ubuntu.com/community/isc-dhcp-serverThanks).

---

