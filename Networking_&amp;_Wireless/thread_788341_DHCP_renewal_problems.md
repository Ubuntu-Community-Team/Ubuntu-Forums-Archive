---
title: "DHCP renewal problems"
date: 2008-05-09
forum: Networking &amp; Wireless
---

### Post by gedden on 2008-05-09
I am having this problem, at this house I am house sitting for the weekend. I have to use static nameservers, and it seems to be overwritten every minute and a half. I read in a different thread that a guy had a corrupted 'dhclient.eth0.leases'. How can I find out if my file is corrupt also? From my syslog I see that my dhcp renewal is set for 113 seconds or so. Is there a way to set the time before a renewal? I have in the past edited my dhcp3 file to remove the request for a nameserver, but my file was still not working after a renewal. 
I am using 8.04 on a compaq armada m300 and WICD as my network manager. Could it be an incomplete install and/or uninstall of network manager?

So I thought I fixed the most annoying part of it by running the instructions on  [OpenDNS Ubuntu instructions.]("https://www.opendns.com/start?device=ubuntu#step1"). They had a little section to follow to not have your dns overwritten constantly. However I'm still having problems when I renew, and the time is still very slow. 


```
May  9 15:19:41 gedden-laptop dhclient: receive_packet failed on eth0: Network is down
May  9 15:19:41 gedden-laptop avahi-daemon[4869]: Interface eth0.IPv4 no longer relevant for mDNS.
May  9 15:19:41 gedden-laptop avahi-daemon[4869]: Leaving mDNS multicast group on interface eth0.IPv4 with address 192.168.1.100.
May  9 15:19:41 gedden-laptop avahi-daemon[4869]: Withdrawing address record for fe80::2d0:59ff:fe91:c3ff on eth0.
May  9 15:19:41 gedden-laptop avahi-daemon[4869]: Withdrawing address record for 192.168.1.100 on eth0.
May  9 15:19:41 gedden-laptop kernel: [  810.258635] ADDRCONF(NETDEV_UP): eth0: link is not ready
May  9 15:19:41 gedden-laptop kernel: [  810.262409] e100: eth0: e100_watchdog: link up, 100Mbps, half-duplex
May  9 15:19:41 gedden-laptop kernel: [  810.267116] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
May  9 15:19:41 gedden-laptop dhclient: There is already a pid file /var/run/dhclient.pid with pid 14398
May  9 15:19:41 gedden-laptop dhclient: removed stale PID file
May  9 15:19:41 gedden-laptop dhclient: Internet Systems Consortium DHCP Client V3.0.6
May  9 15:19:41 gedden-laptop dhclient: Copyright 2004-2007 Internet Systems Consortium.
May  9 15:19:41 gedden-laptop dhclient: All rights reserved.
May  9 15:19:41 gedden-laptop dhclient: For info, please visit http://www.isc.org/sw/dhcp/
May  9 15:19:41 gedden-laptop dhclient: 
May  9 15:19:41 gedden-laptop dhclient: wifi0: unknown hardware address type 801
May  9 15:19:43 gedden-laptop dhclient: wifi0: unknown hardware address type 801
May  9 15:19:43 gedden-laptop dhclient: Listening on LPF/eth0/00:d0:59:91:c3:ff
May  9 15:19:43 gedden-laptop dhclient: Sending on   LPF/eth0/00:d0:59:91:c3:ff
May  9 15:19:43 gedden-laptop dhclient: Sending on   Socket/fallback
May  9 15:19:43 gedden-laptop dhclient: DHCPREQUEST of 192.168.1.100 on eth0 to 255.255.255.255 port 67
May  9 15:19:43 gedden-laptop avahi-daemon[4869]: Registering new address record for fe80::2d0:59ff:fe91:c3ff on eth0.*.
May  9 15:19:44 gedden-laptop dhclient: DHCPACK of 192.168.1.100 from 192.168.1.1
May  9 15:19:44 gedden-laptop avahi-daemon[4869]: Joining mDNS multicast group on interface eth0.IPv4 with address 192.168.1.100.
May  9 15:19:44 gedden-laptop avahi-daemon[4869]: New relevant interface eth0.IPv4 for mDNS.
May  9 15:19:44 gedden-laptop avahi-daemon[4869]: Registering new address record for 192.168.1.100 on eth0.IPv4.
May  9 15:19:44 gedden-laptop dhclient: bound to 192.168.1.100 -- renewal in 134 seconds.
May  9 15:19:52 gedden-laptop kernel: [  818.989406] eth0: no IPv6 routers present
May  9 15:21:58 gedden-laptop dhclient: DHCPREQUEST of <null address> on eth0 to 192.168.1.1 port 67
May  9 15:21:58 gedden-laptop dhclient: DHCPACK of 192.168.1.100 from 192.168.1.1
May  9 15:21:58 gedden-laptop dhclient: bound to 192.168.1.100 -- renewal in 141 seconds.
```

I also threw up a question on a solved thread, and I thought that might be confusing. Therefore I decided it might be easier to start this new thread.

---

### Post by chili555 on 2008-05-09
I believe the DHCP lease and time are given out by the router, access point or modem. My WRT54G, for example, has a field called *Client Lease Time*, which I set to one day. Have you checked the setup page in your router?

---

