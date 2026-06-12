---
title: "ipv4 dhcp fails and assigns ipv6 address instead"
date: 2006-10-17
forum: Networking &amp; Wireless
---

### Post by briswolf on 2006-10-17
Hi, I am hoping somebody out there can help me out.

I have only recently started using ubuntu. After numerous problems with the liveCD, I am finally in an installed version. The first thing I notice is that the network doesn't work, which is strange as it worked fine on the liveCD.

I checked out ifconfig and it showed an ipv6 address for eth0, and eth1 shows no address (I have an nforce board which has 10/100 and gigabit ports - eth0 is I believe the 10/100 port and is the only one plugged in to a cable). I have checked /etc/network/interfaces and indeed the eth0 interface is set to "auto eth0 inet dhcp" which the man page assures me will give me an ipv4 address. eth1 is set exactly the same.

What is going on here? My dhcp server is running fine as 3 other machines can get addresses from windows and indeed the PC running ubuntu can get an address when using the liveCD. I can use the network when given a static configuration.

Below is /var/log/sysinfo:
Oct 17 23:26:04 Hawking syslogd 1.4.1#17ubuntu7: restart.
Oct 17 23:26:04 Hawking anacron[4760]: Job `cron.daily' terminated
Oct 17 23:29:38 Hawking dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 5
Oct 17 23:29:43 Hawking dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 8
Oct 17 23:29:51 Hawking dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 10
Oct 17 23:30:01 Hawking dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 11
Oct 17 23:30:12 Hawking dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 19
Oct 17 23:30:31 Hawking dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 8
Oct 17 23:30:39 Hawking dhclient: No DHCPOFFERS received.
Oct 17 23:30:39 Hawking dhclient: No working leases in persistent database - sleeping.
Oct 17 23:30:51 Hawking anacron[4760]: Job `cron.weekly' started
Oct 17 23:30:51 Hawking anacron[5816]: Updated timestamp for job `cron.weekly' to 2006-10-17
Oct 17 23:30:51 Hawking exiting on signal 15
Oct 17 23:30:52 Hawking syslogd 1.4.1#17ubuntu7: restart.
Oct 17 23:30:52 Hawking anacron[4760]: Job `cron.weekly' terminated
Oct 17 23:31:49 Hawking dhclient: Internet Systems Consortium DHCP Client V3.0.3
Oct 17 23:31:49 Hawking dhclient: Copyright 2004-2005 Internet Systems Consortium.
Oct 17 23:31:49 Hawking dhclient: All rights reserved.
Oct 17 23:31:49 Hawking dhclient: For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)
Oct 17 23:31:49 Hawking dhclient:
Oct 17 23:31:49 Hawking dhclient: Listening on LPF/eth1/00:11:d8:51:74:df
Oct 17 23:31:49 Hawking dhclient: Sending on   LPF/eth1/00:11:d8:51:74:df
Oct 17 23:31:49 Hawking dhclient: Sending on   Socket/fallback
Oct 17 23:31:49 Hawking kernel: [17180261.476000] skge eth1: disabling interface
Oct 17 23:32:48 Hawking dhclient: receive_packet failed on eth0: Network is down
Oct 17 23:32:50 Hawking dhclient: Internet Systems Consortium DHCP Client V3.0.3
Oct 17 23:32:50 Hawking dhclient: Copyright 2004-2005 Internet Systems Consortium.
Oct 17 23:32:50 Hawking dhclient: All rights reserved.
Oct 17 23:32:50 Hawking dhclient: For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)
Oct 17 23:32:50 Hawking dhclient:
Oct 17 23:32:50 Hawking dhclient: Listening on LPF/eth0/04:4b:80:80:80:03
Oct 17 23:32:50 Hawking dhclient: Sending on   LPF/eth0/04:4b:80:80:80:03
Oct 17 23:32:50 Hawking dhclient: Sending on   Socket/fallback
Oct 17 23:32:50 Hawking dhclient: receive_packet failed on eth0: Network is down
Oct 17 23:32:32 Hawking ntpdate[6168]: step time server 82.211.81.145 offset -19.796170 sec
Oct 17 23:32:40 Hawking kernel: [17180332.740000] eth0: no IPv6 routers present
Oct 17 23:33:45 Hawking kernel: [17180397.664000] NTFS driver 2.1.25 [Flags: R/O MODULE].
Oct 17 23:33:45 Hawking kernel: [17180397.732000] NTFS volume version 3.1.
Oct 17 23:35:31 Hawking anacron[4760]: Job `cron.monthly' started
Oct 17 23:35:31 Hawking anacron[6318]: Updated timestamp for job `cron.monthly' to 2006-10-17
Oct 17 23:37:31 Hawking anacron[4760]: Job `cron.monthly' terminated
Oct 17 23:37:31 Hawking anacron[4760]: Normal exit (3 jobs run)
Oct 17 23:50:33 Hawking -- MARK --



It seems that by the time it gets around to looking on eth0 for DCHP, it is already using an ipv6 address for something. I am not at all familiar with  ipv6. Is there some way I can configure my system so there is no support for ipv6 at all?

Thanks for your help.

---

### Post by mips on 2006-10-17
Disable IPv6 **globally**. Many posts here, just search.

---

### Post by Iowan on 2006-10-17
When I get home I'll check my system to verify an option to set a default interface - then I'll probably ask about yours.

---

