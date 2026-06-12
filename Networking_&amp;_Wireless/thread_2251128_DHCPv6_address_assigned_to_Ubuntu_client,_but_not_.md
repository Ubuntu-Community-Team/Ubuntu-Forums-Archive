---
title: "DHCPv6 address assigned to Ubuntu client, but not set on interface"
date: 2014-11-02
forum: Networking &amp; Wireless
---

### Post by fullofhope2 on 2014-11-02
**TL;DR:** DHCPv6 server assigns two IPv6 addresses to my Xubuntu client, only one IPv6 address is set on the interface.

Hello,
My network is configured with native IPv6 and my router runs DHCPv6 as well.  When a client requests DHCPv6, the DHCP server will assign a local (fde2) and internet (2601) address, in addition to the autoconfigured (temporary) IPv6 addresses.  The DHCP-assigned addresses become visible over DNS.  For example, this is what my Windows desktop looks like in DNS (all IP addresses are reachable):
**$ **host desktop
desktop has address 192.168.1.40
desktop has IPv6 address fde2::96c
desktop has IPv6 address 2601::96c


Using Xubuntu 14.04 and the default NetworkManager IPv6 configuration, the DHCPv6 request is made, the DHCPv6 server sends both addresses, but ultimately only the fde2: address is set on the interface.  If I look at ifconfig at the right moment, I can actually see the 2601 address set momentarily, but it looks like NetworkManager is unsetting it.

Based on logs, the DHCP client is receiving both addresses but NetworkManager is removing the 2601: address after setting the fde2: address. (middle parts of addresses removed)
Nov  2 05:35:36 filecenter NetworkManager[1498]: <info> (eth0): DHCPv6 state changed preinit6 -> bound6
Nov  2 05:35:36 filecenter NetworkManager[1498]: <info>   address 2601::212/128
Nov  2 05:35:36 filecenter NetworkManager[1498]: <info>   nameserver '2601::1'


Nov  2 05:35:37 filecenter NetworkManager[1498]: <info> (eth0): DHCPv6 state changed bound6 -> bound6
Nov  2 05:35:37 filecenter NetworkManager[1498]: <info>   address fde2::212/128
Nov  2 05:35:37 filecenter NetworkManager[1498]: <info>   nameserver '2601::1'

My router is running OpenWrt Barrier Breaker 14.07.

Any ideas?  Is this a NetworkManager bug?

---

### Post by fullofhope2 on 2014-11-02
Also, I couldn't manage to get NetworkManager to not use DHCPv6 (for auto config) without disabling IPv6 altogether.

I tried using /etc/network/interfaces instead.  With DHCPv6 enabled, I got an address from the DHCPv6 server but it didn't send the hostname in the request and didn't set up automatic addressing either (required for routing!)  With just IPv6 auto enabled, I have full IPv6 connectivity but without the DHCPv6 addresses, which is good enough for now.

---

