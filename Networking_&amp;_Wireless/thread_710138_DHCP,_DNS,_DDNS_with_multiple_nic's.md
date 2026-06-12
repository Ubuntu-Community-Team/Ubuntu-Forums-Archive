---
title: "DHCP, DNS, DDNS with multiple nic's"
date: 2008-02-28
forum: Networking &amp; Wireless
---

### Post by tnat on 2008-02-28
Hello,

i have the default dhcpd and bind9 up and running at ubuntu 7.04. The dhcpd listens on multiple vlans on this machine and is configured to update the bind9 dns-server. All addresses are dynamically given by the dhcp-server.

[FONT="Lucida Console"]ddns-update-style interim;
ignore client-updates;
get-lease-hostnames true;
update-static-leases on;
update-optimization off;
[/FONT]
My problem now is, that we have notebooks with 2 network interfaces. When i boot the notebook using the lan-interface, it gets a new address from the dhcp. The dhcp-server updates the zone:

[FONT="Lucida Console"]Feb 28 11:34:34 gate01 dhcpd: DHCPDISCOVER from 00:16:cf:95:c4:16 (testlaptop) via eth0.1
Feb 28 11:34:34 gate01 dhcpd: DHCPOFFER on 10.3.0.248 to 00:16:cf:95:c4:16 (testlaptop) via eth0.1
Feb 28 11:34:34 gate01 named[10342]: client 10.10.1.100#34558: updating zone 'almi.at/IN': update unsuccessful: testlaptop.almi.at: 'name not in use' prerequisite not satisfied (YXDOMAIN)
Feb 28 11:34:34 gate01 named[10342]: client 10.10.1.100#34558: updating zone 'almi.at/IN': deleting rrset at 'testlaptop.almi.at' A
Feb 28 11:34:34 gate01 named[10342]: client 10.10.1.100#34558: updating zone 'almi.at/IN': adding an RR at 'testlaptop.almi.at' A
Feb 28 11:34:34 gate01 dhcpd: Added new forward map from testlaptop.almi.at to 10.3.0.248
Feb 28 11:34:34 gate01 named[10342]: client 10.10.1.100#34558: updating zone '10.in-addr.arpa/IN': deleting rrset at '248.0.3.10.in-addr.arpa' PTR
Feb 28 11:34:34 gate01 named[10342]: client 10.10.1.100#34558: updating zone '10.in-addr.arpa/IN': adding an RR at '248.0.3.10.in-addr.arpa' PTR
Feb 28 11:34:34 gate01 dhcpd: added reverse map from 248.0.3.10.in-addr.arpa. to testlaptop.almi.at
Feb 28 11:34:34 gate01 dhcpd: DHCPREQUEST for 10.3.0.248 (127.0.0.1) from 00:16:cf:95:c4:16 (testlaptop) via eth0.1
Feb 28 11:34:34 gate01 dhcpd: DHCPACK on 10.3.0.248 to 00:16:cf:95:c4:16 (testlaptop) via eth0.1
[/FONT]

When i switch to the other interface, the dhcpd offers a new address, but does not update the dns-zone.

[FONT="Lucida Console"]Feb 28 11:35:23 gate01 last message repeated 24 times
Feb 28 11:35:49 gate01 dhcpd: DHCPDISCOVER from 00:16:36:9a:69:67 (testlaptop) via eth0.6
Feb 28 11:35:50 gate01 dhcpd: DHCPOFFER on 10.10.18.254 to 00:16:36:9a:69:67 (testlaptop) via eth0.6
Feb 28 11:35:50 gate01 named[10342]: client 10.10.1.100#34558: updating zone 'almi.at/IN': update unsuccessful: testlaptop.almi.at: 'name not in use' prerequisite not satisfied (YXDOMAIN)
Feb 28 11:35:50 gate01 named[10342]: client 10.10.1.100#34558: updating zone 'almi.at/IN': update unsuccessful: testlaptop.almi.at/TXT: 'RRset exists (value dependent)' prerequisite not satisfied (NXRRSET)
Feb 28 11:35:50 gate01 dhcpd: Forward map from testlaptop.almi.at to 10.10.18.254 FAILED: Has an A record but no DHCID, not mine.
Feb 28 11:35:50 gate01 dhcpd: DHCPREQUEST for 10.10.18.254 (127.0.0.1) from 00:16:36:9a:69:67 (testlaptop) via eth0.6
Feb 28 11:35:50 gate01 dhcpd: DHCPACK on 10.10.18.254 to 00:16:36:9a:69:67 (testlaptop) via eth0.6[/FONT]

How is it possible to force the update of the zone?

Thanks,
tom

---

