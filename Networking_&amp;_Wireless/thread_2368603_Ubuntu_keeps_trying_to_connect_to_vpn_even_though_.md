---
title: "Ubuntu keeps trying to connect to vpn even though i haven't got it enabled."
date: 2017-08-12
forum: Networking &amp; Wireless
---

### Post by Thekow on 2017-08-12
Hi there!

ubuntu 14.04

I have a weird problem. I have openvpn connection to PIA which i no longer need to use on a constant basis.
I still need the vpn only sometimes but for the most part i moved the vpn services to another appliance.
So I have unchecked all the connect to vpn automatically in NM edit connection settings.

But still even though i have deleted my ethernet connections and reinstalled them every 30 minutes it's trying to reconnect to the vpn I had previously.
I am wondering what configuration files i need to check to see if some watchdog timer is trying to connect to the specific VPN.
I removed the ifdownup configuration for testing it still is trying to connect to the vpn. 

I'm assuming it's a NM issue rather than a openvpn issue. 

I manually take down the vpn at 8:33

```

Aug 13 08:33:23 mediaserver dbus[673]: [system] Successfully activated service 'org.freedesktop.nm_dispatcher'
Aug 13 08:33:23 mediaserver ntpd[30958]: Listen normally on 7 tun0 10.34.1.6 UDP 123
Aug 13 08:33:23 mediaserver ntpd[30958]: 91.189.89.198 interface 192.168.1.10 -> 10.34.1.6
Aug 13 08:33:23 mediaserver ntpd[30958]: 81.93.163.23 interface 192.168.1.10 -> 10.34.1.6
Aug 13 08:33:23 mediaserver ntpd[30958]: 108.61.56.35 interface 192.168.1.10 -> 10.34.1.6
Aug 13 08:33:23 mediaserver ntpd[30958]: 81.175.5.182 interface 192.168.1.10 -> 10.34.1.6
Aug 13 08:33:23 mediaserver ntpd[30958]: 109.247.139.196 interface 192.168.1.10 -> 10.34.1.6
Aug 13 08:33:23 mediaserver ntpd[30958]: peers refreshed
Aug 13 08:33:23 mediaserver ntpd[30958]: new interface(s) found: waking up resolver
Aug 13 08:33:27 mediaserver avahi-daemon[837]: Withdrawing address record for 192.168.1.10 on eth0.
Aug 13 08:33:27 mediaserver avahi-daemon[837]: Leaving mDNS multicast group on interface eth0.IPv4 with address 192.168.1.10.
Aug 13 08:33:27 mediaserver avahi-daemon[837]: Interface eth0.IPv4 no longer relevant for mDNS.
Aug 13 08:33:27 mediaserver avahi-daemon[837]: Joining mDNS multicast group on interface eth0.IPv4 with address 192.168.1.10.
Aug 13 08:33:27 mediaserver avahi-daemon[837]: New relevant interface eth0.IPv4 for mDNS.
Aug 13 08:33:27 mediaserver avahi-daemon[837]: Registering new address record for 192.168.1.10 on eth0.IPv4.
Aug 13 08:33:28 mediaserver NetworkManager[1199]: <info> Policy set 'Ethernet connection 1' (eth0) as default for IPv4 routing and DNS.
Aug 13 08:33:28 mediaserver NetworkManager[1199]: <info> Writing DNS information to /sbin/resolvconf
Aug 13 08:33:29 mediaserver avahi-daemon[837]: Withdrawing workstation service for tun0.
Aug 13 08:33:29 mediaserver NetworkManager[1199]: <warn> (54) failed to find interface name for index
Aug 13 08:33:29 mediaserver NetworkManager[1199]: nm_system_iface_flush_routes: assertion 'iface != NULL' failed
Aug 13 08:33:29 mediaserver NetworkManager[1199]: <warn> (54) failed to find interface name for index
Aug 13 08:33:29 mediaserver NetworkManager[1199]:    SCPlugin-Ifupdown: devices removed (path: /sys/devices/virtual/net/tun0, iface: tun0)
Aug 13 08:33:29 mediaserver nm-openvpn[31171]: SIGTERM[hard,] received, process exiting
Aug 13 08:33:30 mediaserver ntpd[30958]: Deleting interface #7 tun0, 10.34.1.6#123, interface stats: received=5, sent=5, dropped=0, active_tim                                      e=7 secs
Aug 13 08:33:30 mediaserver ntpd[30958]: 109.247.139.196 interface 10.34.1.6 -> (none)
Aug 13 08:33:30 mediaserver ntpd[30958]: 81.175.5.182 interface 10.34.1.6 -> (none)
Aug 13 08:33:30 mediaserver ntpd[30958]: 108.61.56.35 interface 10.34.1.6 -> (none)
Aug 13 08:33:30 mediaserver ntpd[30958]: 81.93.163.23 interface 10.34.1.6 -> (none)
Aug 13 08:33:30 mediaserver ntpd[30958]: 91.189.89.198 interface 10.34.1.6 -> (none)
Aug 13 08:33:30 mediaserver ntpd[30958]: peers refreshed
Aug 13 08:33:34 mediaserver NetworkManager[1199]: <info> VPN service 'openvpn' disappeared
Aug 13 08:39:01 mediaserver CRON[31434]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -x /usr/lib/php5/sessionclean ] && [ -d /var/lib/                                      php5 ] && /usr/lib/php5/sessionclean /var/lib/php5 $(/usr/lib/php5/maxlifetime))
Aug 13 08:51:03 mediaserver NetworkManager[1199]: <info> Starting VPN service 'openvpn'...
Aug 13 08:51:03 mediaserver NetworkManager[1199]: <info> VPN service 'openvpn' started (org.freedesktop.NetworkManager.openvpn), PID 31501
Aug 13 08:51:03 mediaserver NetworkManager[1199]: <info> VPN service 'openvpn' appeared; activating connections
Aug 13 08:51:03 mediaserver nm-openvpn[31504]: OpenVPN 2.3.2 i686-pc-linux-gnu [SSL (OpenSSL)] [LZO] [EPOLL] [PKCS11] [eurephia] [MH] [IPv6] b                                      uilt on Dec  1 2014
Aug 13 08:51:03 mediaserver NetworkManager[1199]: <info> VPN plugin state changed: starting (3)
Aug 13 08:51:03 mediaserver NetworkManager[1199]: <info> VPN connection 'PIA - Norway' (Connect) reply received.
Aug 13 08:51:03 mediaserver nm-openvpn[31504]: WARNING: No server certificate verification method has been enabled.  See http://openvpn.net/ho                                      wto.html#mitm for more info.
Aug 13 08:51:03 mediaserver nm-openvpn[31504]: NOTE: the current --script-security setting may allow this configuration to call user-defined s                                      cripts
Aug 13 08:51:04 mediaserver nm-openvpn[31504]: Attempting to establish TCP connection with [AF_INET]192.40.88.73:502 [nonblock]
Aug 13 08:51:05 mediaserver nm-openvpn[31504]: TCP connection established with [AF_INET]192.40.88.73:502
Aug 13 08:51:05 mediaserver nm-openvpn[31504]: TCPv4_CLIENT link local: [undef]
Aug 13 08:51:05 mediaserver nm-openvpn[31504]: TCPv4_CLIENT link remote: [AF_INET]192.40.88.73:502
Aug 13 08:51:10 mediaserver nm-openvpn[31504]: WARNING: 'link-mtu' is used inconsistently, local='link-mtu 1560', remote='link-mtu 1544'
Aug 13 08:51:10 mediaserver nm-openvpn[31504]: WARNING: 'cipher' is used inconsistently, local='cipher AES-128-CBC', remote='cipher BF-CBC'
Aug 13 08:51:10 mediaserver nm-openvpn[31504]: [a91745a3fc8ba96220bdced8a0de80d0] Peer Connection Initiated with [AF_INET]192.40.88.73:502
Aug 13 08:51:13 mediaserver nm-openvpn[31504]: TUN/TAP device tun0 opened
Aug 13 08:51:13 mediaserver nm-openvpn[31504]: /usr/lib/NetworkManager/nm-openvpn-service-openvpn-helper tun0 1500 1560 10.33.1.10 10.33.1.9 i                                      nit
Aug 13 08:51:13 mediaserver NetworkManager[1199]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/tun0, iface: tun0)
Aug 13 08:51:13 mediaserver NetworkManager[1199]:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/tun0, iface: tun0): no if                                      updown configuration found.
Aug 13 08:51:13 mediaserver NetworkManager[1199]: <warn> /sys/devices/virtual/net/tun0: couldn't determine device driver; ignoring...
Aug 13 08:51:13 mediaserver NetworkManager[1199]: <info> VPN connection 'PIA - Norway' (IP Config Get) reply received.
Aug 13 08:51:13 mediaserver NetworkManager[1199]: <info> VPN connection 'PIA - Norway' (IP4 Config Get) reply received.
Aug 13 08:51:13 mediaserver NetworkManager[1199]: <info> VPN Gateway: 192.40.88.73
Aug 13 08:51:13 mediaserver NetworkManager[1199]: <info> Tunnel Device: tun0
Aug 13 08:51:13 mediaserver NetworkManager[1199]: <info> IPv4 configuration:



```

---

