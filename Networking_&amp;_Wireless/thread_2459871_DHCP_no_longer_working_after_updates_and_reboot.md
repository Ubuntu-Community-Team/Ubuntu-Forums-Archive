---
title: "DHCP no longer working after updates and reboot"
date: 2021-03-28
forum: Networking &amp; Wireless
---

### Post by sniper8752 on 2021-03-28
I am running Ubuntu 20 on my server.  I did updates, of which the following were done: 
isc-dhcp-common:amd64 (4.4.1-2.1ubuntu5, 4.4.1-2.1ubuntu5.20.04.1)
  isc-dhcp-client:amd64 (4.4.1-2.1ubuntu5, 4.4.1-2.1ubuntu5.20.04.1)
   isc-dhcp-server:amd64 (4.4.1-2.1ubuntu5, 4.4.1-2.1ubuntu5.20.04.1)

Upon reboot, I can no longer pull an IP address with DHCP.  I am running iptables, but added rules to allow the traffic through, and accept it.  
Could the updates have broken this?

---

### Post by Doug S on 2021-03-30
I have those same versions for common and client:

```
doug@s19:~$ dpkg -l | grep dhcp
ii  isc-dhcp-client                                  4.4.1-2.1ubuntu5.20.04.1              amd64        DHCP client for automatically obtaining an IP address
ii  isc-dhcp-common                                  4.4.1-2.1ubuntu5.20.04.1              amd64        common manpages relevant to all of the isc-dhcp packages
```And it seems to be working fine:

```
doug@s19:~$ grep -i dhcp /var/log/syslog
Mar 30 08:26:23 s19 systemd-networkd[531]: enp3s0: DHCPv4 address 192.168.111.136/24 via 192.168.111.1
```

My dhcp server is debian based:

```
doug@s15:~$ dpkg -l | grep dhcp
ii  isc-dhcp-client                      4.4.1-2.2                      amd64        DHCP client for automatically obtaining an IP address
ii  isc-dhcp-common                      4.4.1-2.2                      amd64        common manpages relevant to all of the isc-dhcp packages
ii  isc-dhcp-server                      4.4.1-2.2                      amd64        ISC DHCP server for automatic IP address assignment
```

Likely a tangent:
And I do observe duplicate messages, which is something I thought I solved years ago, at least with my old 16.04 Ubuntu based server:

```
Mar 30 08:26:22 s15 dhcpd[2584]: uid lease 192.168.111.50 for client 3c:7c:3f:0d:99:83 is duplicate on 192.168.111.0/24
Mar 30 08:26:22 s15 dhcpd[2584]: DHCPDISCOVER from 3c:7c:3f:0d:99:83 via br0
Mar 30 08:26:22 s15 dhcpd[2584]: DHCPOFFER on 192.168.111.136 to 3c:7c:3f:0d:99:83 via br0
Mar 30 08:26:22 s15 dhcpd[2584]: uid lease 192.168.111.50 for client 3c:7c:3f:0d:99:83 is duplicate on 192.168.111.0/24
Mar 30 08:26:22 s15 dhcpd[2584]: DHCPREQUEST for 192.168.111.136 (192.168.111.1) from 3c:7c:3f:0d:99:83 via br0
Mar 30 08:26:22 s15 dhcpd[2584]: DHCPACK on 192.168.111.136 to 3c:7c:3f:0d:99:83 via br0
```

s19 = 192.168.111.136 (it was assigned 192.168.111.50 from the dynamic pool, before I did it via MAC)
s15 = 192.168.111.1

---

