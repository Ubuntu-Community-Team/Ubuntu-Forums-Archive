---
title: "Cable connection only works after reboot"
date: 2007-05-31
forum: Networking &amp; Wireless
---

### Post by ivancruz on 2007-05-31
Two months ago I signed up for a cable broadband connection and for some time it worked just fine. In the last 3 or 4 weeks, I started experiencing a strange problem: my connection stopped working in the morning, just after the boot. In the begining it was intermitent but in the last days it becames norm.

It doesn't matter how much time I wait for. Also, turning off and on or disconnecting and reconnecting the cable modem does not help. The only way to have my intenet again is rebooting Ubuntu.

Since I believe rebooting is not an acceptable solution for any problem I started sniffing packets and monitoring logs looking for a better solution. I found 3 facts:

1. I am receiving packtes. Hundreds per minute. Almost all are ARP packets.
2. It takes around 4 or 5 minutes after booting to receive an DHCP offer.
3. Only after the reboot, dhclient prints the message "isc-dhclient-V3.0.4"

dhclient lines extracted from syslog follows:

> -------------------- first boot --------------------
May 31 09:55:21 IvanAMD32 dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
May 31 09:55:29 IvanAMD32 dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10
May 31 09:55:39 IvanAMD32 dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 15
May 31 09:55:54 IvanAMD32 dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 16
May 31 09:56:10 IvanAMD32 dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 12
May 31 09:56:22 IvanAMD32 dhclient: No DHCPOFFERS received.
May 31 09:56:22 IvanAMD32 dhclient: No working leases in persistent database - sleeping.
May 31 10:00:52 IvanAMD32 dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
May 31 10:00:58 IvanAMD32 dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 12
May 31 10:00:58 IvanAMD32 dhclient: DHCPOFFER from 10.13.0.1
May 31 10:00:58 IvanAMD32 dhclient: DHCPREQUEST on eth0 to 255.255.255.255 port 67
May 31 10:00:58 IvanAMD32 dhclient: DHCPACK from 10.13.0.1
May 31 10:00:58 IvanAMD32 dhclient: bound to 201.17.124.187 -- renewal in 5042 seconds.
------------------------ reboot ------------------------
May 31 10:43:43 IvanAMD32 dhclient: isc-dhclient-V3.0.4
May 31 12:05:50 IvanAMD32 dhclient: DHCPREQUEST on eth0 to 201.17.0.14 port 67
May 31 12:05:50 IvanAMD32 dhclient: DHCPACK from 201.17.0.14
May 31 12:05:50 IvanAMD32 dhclient: bound to 201.17.124.187 -- renewal in 4853 seconds.


I am using Ubuntu 6.10.
Cable modem is Motorola SURFBoard SBV5120 connected via eth0.
Broadband provider is Virtua in Brazil.

Any ideas?

Ivan.

---

