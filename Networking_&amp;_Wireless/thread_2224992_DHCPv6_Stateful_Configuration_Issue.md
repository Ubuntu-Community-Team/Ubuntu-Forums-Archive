---
title: "DHCPv6 Stateful Configuration Issue"
date: 2014-05-19
forum: Networking &amp; Wireless
---

### Post by xWEkxhW on 2014-05-19
Hello

I'm using Ubuntu Trusty 14.04 (server) with isc-dhcp-server6 to statefully configure clients. It works fine, apart from one problem. My Windows 8.1 PC is losing it's stateful address after a certain period of time. For some reason it doesn't seem to be refreshing/renewing but I have no idea why.

When I attempt to manually renew:

```
C:\>ipconfig /renew6 Ethernet

Windows IP Configuration

An error occurred while renewing interface Ethernet : The semaphore timeout period has expired.
```

If I issue the same command for a 2nd time it works, dhcpd then logs the transactions and everything is fine (until the IPv6 address gets dropped again at some time in the future).

Does anyone have any idea what may be causing this problem? I'm completely out of ideas. I'm thinking it's possibly iptables rules but it's only a guess. I'm using these to allow DHCPv6:

```
# DHCPv6 requests
ip6tables -A INPUT -p udp --dport 547 --sport 546 -j ACCEPT
# DHCPv6 Multicast Groups
# RFC 3315 5.1 All_DHCP_Relay_Agents_and_Servers (FF02::1:2)
# RFC 3315 5.1 All_DHCP_Servers (FF05::1:3)
ip6tables -A INPUT -m udp -p udp -m multiport -s fe80::/16 -d ff02::1:2 --dports 547 -j ACCEPT
ip6tables -A INPUT -m udp -p udp -m multiport -s fe80::/16 -d ff05::1:3 --dports 547 -j ACCEPT
```

Do you folks have any ideas what might be wrong?

Thanks :)

---

