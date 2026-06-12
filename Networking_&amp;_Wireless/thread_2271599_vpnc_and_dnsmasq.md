---
title: "vpnc and dnsmasq"
date: 2015-03-31
forum: Networking &amp; Wireless
---

### Post by veda3 on 2015-03-31
Hi all,

I use vpnc combined with network-manager-openconnect to have the graphical stuff. Since a week or so I have the problem that my dns servers are not updated anymore when I connect to vpn. The internal hostnames just do not work.

When I go to the network widget and go to network information, my companies dns hosts are not shown.

When I add the nameserver to /etc/resolv.conf, everything works ok.

Some questions:
- How do I see which nameservers dnsmasq uses?
- How can I fix the problem where vpnc does not correcly update ndsmasq (which is I think the problem, which I want to check with question 1)?

When I connect to vpn I get the following in the syslog (important part at the bottom I think):

```
Mar 31 11:41:31 Houten NetworkManager[898]: <info> Starting VPN service 'openconnect'...Mar 31 11:41:31 Houten NetworkManager[898]: <info> VPN service 'openconnect' started (org.freedesktop.NetworkManager.openconnect), PID 22969
Mar 31 11:41:31 Houten NetworkManager[898]: <info> VPN service 'openconnect' appeared; activating connections
Mar 31 11:41:40 Houten NetworkManager[898]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/vpn0, iface: vpn0)
Mar 31 11:41:40 Houten NetworkManager[898]:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/vpn0, iface: vpn0): no ifupdown configurati
on found.
Mar 31 11:41:40 Houten NetworkManager[898]: <warn> /sys/devices/virtual/net/vpn0: couldn't determine device driver; ignoring...
Mar 31 11:41:40 Houten NetworkManager[898]: <info> VPN plugin state changed: starting (3)
Mar 31 11:41:40 Houten NetworkManager[898]: <info> VPN connection 'company vpn' (Connect) reply received.
Mar 31 11:41:40 Houten openconnect[23078]: Attempting to connect to server 144.24.19.23:443
Mar 31 11:41:40 Houten openconnect[23078]: SSL negotiation with somehostname.companyhost.com
Mar 31 11:41:40 Houten openconnect[23078]: Connected to HTTPS on somehostname.companyhost.com
Mar 31 11:41:40 Houten openconnect[23078]: Got CONNECT response: HTTP/1.1 200 OK
Mar 31 11:41:40 Houten openconnect[23078]: CSTP connected. DPD 30, Keepalive 20
Mar 31 11:41:40 Houten NetworkManager[898]: <info> VPN connection 'company vpn' (IP Config Get) reply received.
Mar 31 11:41:40 Houten NetworkManager[898]: <info> VPN connection 'company vpn' (IP4 Config Get) reply received.
Mar 31 11:41:40 Houten NetworkManager[898]: <info> VPN connection 'company vpn' (IP6 Config Get) reply received.
Mar 31 11:41:40 Houten NetworkManager[898]: <info> VPN Gateway: 144.24.19.23
Mar 31 11:41:40 Houten NetworkManager[898]: <info> Tunnel Device: vpn0
Mar 31 11:41:40 Houten NetworkManager[898]: <info> IPv4 configuration:
Mar 31 11:41:40 Houten NetworkManager[898]: <info>   Internal Address: 10.175.228.254
Mar 31 11:41:40 Houten NetworkManager[898]: <info>   Internal Prefix: 19
Mar 31 11:41:40 Houten NetworkManager[898]: <info>   Internal Point-to-Point Address: 10.175.228.254
Mar 31 11:41:40 Houten NetworkManager[898]: <info>   Maximum Segment Size (MSS): 0
Mar 31 11:41:40 Houten NetworkManager[898]: <info>   Forbid Default Route: no
Mar 31 11:41:40 Houten NetworkManager[898]: <info>   Internal DNS: 192.135.82.44
Mar 31 11:41:40 Houten NetworkManager[898]: <info>   Internal DNS: 192.135.82.60
Mar 31 11:41:40 Houten NetworkManager[898]: <info>   Internal DNS: 10.161.221.2
Mar 31 11:41:40 Houten NetworkManager[898]: <info>   DNS Domain: 'something.company.com'
Mar 31 11:41:40 Houten NetworkManager[898]: <info> IPv6 configuration:
Mar 31 11:41:40 Houten NetworkManager[898]: <info>   Internal Address: 2606:b400:8f0:82:8000::263
Mar 31 11:41:40 Houten NetworkManager[898]: <info>   Internal Prefix: 64
Mar 31 11:41:40 Houten NetworkManager[898]: <info>   Internal Point-to-Point Address: 2606:b400:8f0:82:8000::263
Mar 31 11:41:40 Houten NetworkManager[898]: <info>   Maximum Segment Size (MSS): 0
Mar 31 11:41:40 Houten NetworkManager[898]: <info>   Forbid Default Route: no
Mar 31 11:41:40 Houten NetworkManager[898]: <info>   DNS Domain: 'something.company.com'
Mar 31 11:41:40 Houten openconnect[23078]: Connected vpn0 as 10.175.228.254 + 2606:b400:8f0:82:8000::263, using SSL
Mar 31 11:41:40 Houten openconnect[23078]: Established DTLS connection (using OpenSSL)
Mar 31 11:41:42 Houten NetworkManager[898]: <info> VPN connection 'company vpn' (IP Config Get) complete.
Mar 31 11:41:42 Houten NetworkManager[898]: <info> Policy set 'company vpn' (vpn0) as default for IPv4 routing and DNS.
Mar 31 11:41:42 Houten NetworkManager[898]: <info> Policy set 'company vpn' (vpn0) as default for IPv6 routing and DNS.
Mar 31 11:41:42 Houten NetworkManager[898]: <info> Writing DNS information to /sbin/resolvconf
Mar 31 11:41:42 Houten dnsmasq[2305]: setting upstream servers from DBus
Mar 31 11:41:42 Houten dnsmasq[2305]: using nameserver 10.161.221.2#53 for domain 10.in-addr.arpa
Mar 31 11:41:42 Houten dnsmasq[2305]: using nameserver 10.161.221.2#53 for domain somehting.company.com
Mar 31 11:41:42 Houten dnsmasq[2305]: using nameserver 192.135.82.60#53 for domain 10.in-addr.arpa
Mar 31 11:41:42 Houten dnsmasq[2305]: using nameserver 192.135.82.60#53 for domain somehting.company.com
Mar 31 11:41:42 Houten dnsmasq[2305]: using nameserver 192.135.82.44#53 for domain 10.in-addr.arpa
Mar 31 11:41:42 Houten dnsmasq[2305]: using nameserver 192.135.82.44#53 for domain somehting.company.com
Mar 31 11:41:42 Houten dbus[804]: [system] Activating service name='org.freedesktop.nm_dispatcher' (using servicehelper)
Mar 31 11:41:42 Houten NetworkManager[898]: <info> VPN plugin state changed: started (4)
Mar 31 11:41:42 Houten dbus[804]: [system] Successfully activated service 'org.freedesktop.nm_dispatcher'
Mar 31 11:41:42 Houten named[1239]: received control channel command 'reconfig'
Mar 31 11:41:42 Houten named[1239]: loading configuration from '/etc/bind/named.conf'
Mar 31 11:41:42 Houten named[1239]: reading built-in trusted keys from file '/etc/bind/bind.keys'
Mar 31 11:41:42 Houten named[1239]: using default UDP/IPv4 port range: [1024, 65535]
Mar 31 11:41:42 Houten named[1239]: using default UDP/IPv6 port range: [1024, 65535]
Mar 31 11:41:42 Houten named[1239]: listening on IPv4 interface vpn0, 10.175.228.254#53


```

---

