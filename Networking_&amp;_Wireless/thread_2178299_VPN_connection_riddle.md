---
title: "VPN connection riddle"
date: 2013-10-02
forum: Networking &amp; Wireless
---

### Post by costis on 2013-10-02
Hello,

I would like to ask if you can help me with a peculiar VPN connection problem.

The problem is this one:
1. I have a VPN connection named "myVPN" in KDE
2. I have access to a home network named "my-home" and to a wireless public network named "public-wifi" in KDE
3. Windows 7 dual boot.

The problem is that when I connect to the VPN through "public-wifi" in KDE or Windows 7 everything is ok. But when through "my-home" it fails to connect.

/var/log/syslog while attempting a failed connection to the vpn through "my-home" is this:
```
Oct  2 18:44:27 mint NetworkManager[2379]: <info> Starting VPN service 'pptp'...
Oct  2 18:44:27 mint NetworkManager[2379]: <info> VPN service 'pptp' started (org.freedesktop.NetworkManager.pptp), PID 8003
Oct  2 18:44:27 mint NetworkManager[2379]: <info> VPN service 'pptp' appeared; activating connections
Oct  2 18:44:27 mint NetworkManager[2379]: <info> VPN plugin state changed: init (1)
Oct  2 18:44:27 mint NetworkManager[2379]: <info> VPN plugin state changed: starting (3)
Oct  2 18:44:27 mint NetworkManager[2379]: <info> VPN connection 'New VPN Connection' (Connect) reply received.
Oct  2 18:44:27 mint pppd[8004]: Plugin /usr/lib/pppd/2.4.5/nm-pptp-pppd-plugin.so loaded.
Oct  2 18:44:27 mint pppd[8004]: pppd 2.4.5 started by root, uid 0
Oct  2 18:44:27 mint pppd[8004]: Using interface ppp0
Oct  2 18:44:27 mint pppd[8004]: Connect: ppp0 <--> /dev/pts/5
Oct  2 18:44:27 mint NetworkManager[2379]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/ppp0, iface: ppp0)
Oct  2 18:44:27 mint NetworkManager[2379]:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/ppp0, iface: ppp0): no ifupdown configuration found.
Oct  2 18:44:27 mint NetworkManager[2379]: <warn> /sys/devices/virtual/net/ppp0: couldn't determine device driver; ignoring...
Oct  2 18:44:27 mint pptp[8007]: nm-pptp-service-8003 log[main:pptp.c:314]: The synchronous pptp option is NOT activated
Oct  2 18:44:27 mint pptp[8016]: nm-pptp-service-8003 log[ctrlp_rep:pptp_ctrl.c:251]: Sent control packet type is 1 'Start-Control-Connection-Request'
Oct  2 18:44:28 mint pptp[8016]: nm-pptp-service-8003 log[ctrlp_disp:pptp_ctrl.c:739]: Received Start Control Connection Reply
Oct  2 18:44:28 mint pptp[8016]: nm-pptp-service-8003 log[ctrlp_disp:pptp_ctrl.c:773]: Client connection established.
Oct  2 18:44:28 mint pptp[8016]: nm-pptp-service-8003 log[ctrlp_rep:pptp_ctrl.c:251]: Sent control packet type is 7 'Outgoing-Call-Request'
Oct  2 18:44:28 mint pptp[8016]: nm-pptp-service-8003 log[ctrlp_disp:pptp_ctrl.c:858]: Received Outgoing Call Reply.
Oct  2 18:44:28 mint pptp[8016]: nm-pptp-service-8003 log[ctrlp_disp:pptp_ctrl.c:897]: Outgoing call established (call ID 0, peer's call ID 22839).
Oct  2 18:44:58 mint pppd[8004]: LCP: timeout sending Config-Requests
Oct  2 18:44:58 mint pppd[8004]: Connection terminated.
Oct  2 18:44:58 mint avahi-daemon[6928]: Withdrawing workstation service for ppp0.
Oct  2 18:44:58 mint NetworkManager[2379]: <warn> VPN plugin failed: 1
Oct  2 18:44:58 mint NetworkManager[2379]:    SCPlugin-Ifupdown: devices removed (path: /sys/devices/virtual/net/ppp0, iface: ppp0)
Oct  2 18:44:58 mint pptp[8007]: nm-pptp-service-8003 warn[decaps_hdlc:pptp_gre.c:204]: short read (-1): Input/output error
Oct  2 18:44:58 mint pptp[8007]: nm-pptp-service-8003 warn[decaps_hdlc:pptp_gre.c:216]: pppd may have shutdown, see pppd log
Oct  2 18:44:58 mint pppd[8004]: Modem hangup
Oct  2 18:44:58 mint pptp[8016]: nm-pptp-service-8003 log[callmgr_main:pptp_callmgr.c:234]: Closing connection (unhandled)
Oct  2 18:44:58 mint pptp[8016]: nm-pptp-service-8003 log[ctrlp_rep:pptp_ctrl.c:251]: Sent control packet type is 12 'Call-Clear-Request'
Oct  2 18:44:58 mint pptp[8016]: nm-pptp-service-8003 log[call_callback:pptp_callmgr.c:79]: Closing connection (call state)
Oct  2 18:44:58 mint NetworkManager[2379]: <warn> VPN plugin failed: 1
Oct  2 18:44:58 mint pppd[8004]: Exit.
Oct  2 18:44:58 mint NetworkManager[2379]: <warn> VPN plugin failed: 1
Oct  2 18:44:58 mint NetworkManager[2379]: <info> VPN plugin state changed: stopped (6)
Oct  2 18:44:58 mint NetworkManager[2379]: <info> VPN plugin state change reason: 0
Oct  2 18:44:58 mint NetworkManager[2379]: <info> Policy set 'spitarona' (wlan0) as default for IPv4 routing and DNS.
Oct  2 18:44:58 mint NetworkManager[2379]: <warn> error disconnecting VPN: Could not process the request because no VPN connection was active.
Oct  2 18:45:03 mint NetworkManager[2379]: <info> VPN service 'pptp' disappeared
```

/var/log/syslog while attempting a successful connection to the vpn through "public-wifi" is this:
```

Oct  2 18:47:13 mint ntpdate[8201]: adjust time server 131.211.8.244 offset -0.025585 sec
Oct  2 18:47:13 mint ntpd[8229]: ntpd 4.2.6p5@1.2349-o Thu Apr  4 22:25:14 UTC 2013 (1)
Oct  2 18:47:13 mint ntpd[8230]: proto: precision = 0.105 usec
Oct  2 18:47:13 mint ntpd[8230]: ntp_io: estimated max descriptors: 2144, initial socket boundary: 16
Oct  2 18:47:13 mint ntpd[8230]: Listen and drop on 0 v4wildcard 0.0.0.0 UDP 123
Oct  2 18:47:13 mint ntpd[8230]: Listen and drop on 1 v6wildcard :: UDP 123
Oct  2 18:47:13 mint ntpd[8230]: Listen normally on 2 lo 127.0.0.1 UDP 123
Oct  2 18:47:13 mint ntpd[8230]: Listen normally on 3 wlan0 192.168.2.15 UDP 123
Oct  2 18:47:13 mint ntpd[8230]: Listen normally on 4 lo ::1 UDP 123
Oct  2 18:47:13 mint ntpd[8230]: Listen normally on 5 eth0 fe80::be5f:f4ff:fe97:b16e UDP 123
Oct  2 18:47:13 mint ntpd[8230]: Listen normally on 6 wlan0 fe80::92f6:52ff:fecc:494b UDP 123
Oct  2 18:47:13 mint ntpd[8230]: peers refreshed
Oct  2 18:47:13 mint ntpd[8230]: Listening on routing socket on fd #23 for interface updates
Oct  2 18:47:24 mint NetworkManager[2379]: <info> Starting VPN service 'pptp'...
Oct  2 18:47:24 mint NetworkManager[2379]: <info> VPN service 'pptp' started (org.freedesktop.NetworkManager.pptp), PID 8233
Oct  2 18:47:24 mint NetworkManager[2379]: <info> VPN service 'pptp' appeared; activating connections
Oct  2 18:47:24 mint NetworkManager[2379]: <info> VPN plugin state changed: starting (3)
Oct  2 18:47:24 mint NetworkManager[2379]: <info> VPN connection 'New VPN Connection' (Connect) reply received.
Oct  2 18:47:24 mint pppd[8234]: Plugin /usr/lib/pppd/2.4.5/nm-pptp-pppd-plugin.so loaded.
Oct  2 18:47:24 mint pppd[8234]: pppd 2.4.5 started by root, uid 0
Oct  2 18:47:24 mint pppd[8234]: Using interface ppp0
Oct  2 18:47:24 mint pppd[8234]: Connect: ppp0 <--> /dev/pts/5
Oct  2 18:47:24 mint NetworkManager[2379]: <warn> /sys/devices/virtual/net/ppp0: couldn't determine device driver; ignoring...
Oct  2 18:47:24 mint NetworkManager[2379]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/ppp0, iface: ppp0)
Oct  2 18:47:24 mint NetworkManager[2379]:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/ppp0, iface: ppp0): no ifupdown configuration found.
Oct  2 18:47:24 mint pptp[8237]: nm-pptp-service-8233 log[main:pptp.c:314]: The synchronous pptp option is NOT activated
Oct  2 18:47:24 mint pptp[8246]: nm-pptp-service-8233 log[ctrlp_rep:pptp_ctrl.c:251]: Sent control packet type is 1 'Start-Control-Connection-Request'
Oct  2 18:47:24 mint pptp[8246]: nm-pptp-service-8233 log[ctrlp_disp:pptp_ctrl.c:739]: Received Start Control Connection Reply
Oct  2 18:47:24 mint pptp[8246]: nm-pptp-service-8233 log[ctrlp_disp:pptp_ctrl.c:773]: Client connection established.
Oct  2 18:47:25 mint pptp[8246]: nm-pptp-service-8233 log[ctrlp_rep:pptp_ctrl.c:251]: Sent control packet type is 7 'Outgoing-Call-Request'
Oct  2 18:47:25 mint pptp[8246]: nm-pptp-service-8233 log[ctrlp_disp:pptp_ctrl.c:858]: Received Outgoing Call Reply.
Oct  2 18:47:25 mint pptp[8246]: nm-pptp-service-8233 log[ctrlp_disp:pptp_ctrl.c:897]: Outgoing call established (call ID 0, peer's call ID 60190).
Oct  2 18:47:28 mint pppd[8234]: CHAP authentication succeeded
Oct  2 18:47:28 mint pppd[8234]: MPPE 128-bit stateless compression enabled
Oct  2 18:47:31 mint pppd[8234]: local  IP address *.*.*.*
Oct  2 18:47:31 mint pppd[8234]: remote IP address *.*.*.*
Oct  2 18:47:31 mint pppd[8234]: primary   DNS address *.*.*.*
Oct  2 18:47:31 mint pppd[8234]: secondary DNS address *.*.*.*
Oct  2 18:47:31 mint NetworkManager[2379]: <info> VPN connection 'New VPN Connection' (IP4 Config Get) reply received from old-style plugin.
Oct  2 18:47:31 mint NetworkManager[2379]: <info> VPN Gateway: *.*.*.*
Oct  2 18:47:31 mint NetworkManager[2379]: <info> Tunnel Device: ppp0
Oct  2 18:47:31 mint NetworkManager[2379]: <info> IPv4 configuration:
Oct  2 18:47:31 mint NetworkManager[2379]: <info>   Internal Address: *.*.*.*
Oct  2 18:47:31 mint NetworkManager[2379]: <info>   Internal Prefix: 32
Oct  2 18:47:31 mint NetworkManager[2379]: <info>   Internal Point-to-Point Address: *.*.*.*
Oct  2 18:47:31 mint NetworkManager[2379]: <info>   Maximum Segment Size (MSS): 0
Oct  2 18:47:31 mint NetworkManager[2379]: <info>   Forbid Default Route: no
Oct  2 18:47:31 mint NetworkManager[2379]: <info>   Internal DNS: *.*.*.*
Oct  2 18:47:31 mint NetworkManager[2379]: <info>   Internal DNS: *.*.*.*
Oct  2 18:47:31 mint NetworkManager[2379]: <info>   DNS Domain: '(none)'
Oct  2 18:47:31 mint NetworkManager[2379]: <info> No IPv6 configuration
Oct  2 18:47:32 mint NetworkManager[2379]: <info> VPN connection 'New VPN Connection' (IP Config Get) complete.
Oct  2 18:47:32 mint NetworkManager[2379]: <info> Policy set 'New VPN Connection' (ppp0) as default for IPv4 routing and DNS.
Oct  2 18:47:32 mint NetworkManager[2379]: <info> Writing DNS information to /sbin/resolvconf
Oct  2 18:47:32 mint dnsmasq[3733]: setting upstream servers from DBus
Oct  2 18:47:32 mint dnsmasq[3733]: using nameserver *.*.*.*#53
Oct  2 18:47:32 mint dnsmasq[3733]: using nameserver *.*.*.*#53
Oct  2 18:47:32 mint dbus[1797]: [system] Activating service name='org.freedesktop.nm_dispatcher' (using servicehelper)
Oct  2 18:47:32 mint NetworkManager[2379]: <info> VPN plugin state changed: started (4)
Oct  2 18:47:32 mint dbus[1797]: [system] Successfully activated service 'org.freedesktop.nm_dispatcher'
Oct  2 18:47:33 mint avahi-daemon[6928]: Got SIGTERM, quitting.
Oct  2 18:47:33 mint avahi-daemon[6928]: Leaving mDNS multicast group on interface wlan0.IPv6 with address fe80::92f6:52ff:fecc:494b.
Oct  2 18:47:33 mint avahi-daemon[6928]: Leaving mDNS multicast group on interface wlan0.IPv4 with address *.*.*.*.
Oct  2 18:47:33 mint avahi-daemon[6928]: Leaving mDNS multicast group on interface eth0.IPv6 with address fe80::be5f:f4ff:fe97:b16e.
Oct  2 18:47:33 mint avahi-daemon[6928]: avahi-daemon 0.6.31 exiting.
Oct  2 18:47:33 mint avahi: Avahi detected that your currently configured local DNS server serves
Oct  2 18:47:33 mint avahi: a domain .local. This is inherently incompatible with Avahi and thus
Oct  2 18:47:33 mint avahi: Avahi disabled itself. If you want to use Avahi in this network, please
Oct  2 18:47:33 mint avahi: contact your administrator and convince him to use a different DNS domain,
Oct  2 18:47:33 mint avahi: since .local should be used exclusively for Zeroconf technology.
Oct  2 18:47:33 mint avahi: For more information, see http://avahi.org/wiki/AvahiAndUnicastDotLocal
Oct  2 18:47:33 mint ntpd[8230]: ntpd exiting on signal 15
Oct  2 18:47:45 mint ntpdate[8368]: adjust time server 192.87.110.2 offset -0.057458 sec
Oct  2 18:47:45 mint ntpd[8396]: ntpd 4.2.6p5@1.2349-o Thu Apr  4 22:25:14 UTC 2013 (1)
Oct  2 18:47:45 mint ntpd[8397]: proto: precision = 0.105 usec
Oct  2 18:47:45 mint ntpd[8397]: ntp_io: estimated max descriptors: 2144, initial socket boundary: 16
Oct  2 18:47:45 mint ntpd[8397]: Listen and drop on 0 v4wildcard 0.0.0.0 UDP 123
Oct  2 18:47:45 mint ntpd[8397]: Listen and drop on 1 v6wildcard :: UDP 123
Oct  2 18:47:45 mint ntpd[8397]: Listen normally on 2 lo 127.0.0.1 UDP 123
Oct  2 18:47:45 mint ntpd[8397]: Listen normally on 3 wlan0 *.*.*.* UDP 123
Oct  2 18:47:45 mint ntpd[8397]: Listen normally on 4 ppp0 *.*.*.* UDP 123
Oct  2 18:47:45 mint ntpd[8397]: Listen normally on 5 lo ::1 UDP 123
Oct  2 18:47:45 mint ntpd[8397]: Listen normally on 6 eth0 fe80::be5f:f4ff:fe97:b16e UDP 123
Oct  2 18:47:45 mint ntpd[8397]: Listen normally on 7 wlan0 fe80::92f6:52ff:fecc:494b UDP 123
Oct  2 18:47:45 mint ntpd[8397]: peers refreshed
Oct  2 18:47:45 mint ntpd[8397]: Listening on routing socket on fd #24 for interface updates
Oct  2 18:47:52 mint NetworkManager[2379]: <info> Policy set 'VGV7519AD4FA3' (wlan0) as default for IPv4 routing and DNS.
Oct  2 18:47:52 mint NetworkManager[2379]: <info> Writing DNS information to /sbin/resolvconf
Oct  2 18:47:52 mint dnsmasq[3733]: setting upstream servers from DBus
Oct  2 18:47:52 mint dnsmasq[3733]: using nameserver *.*.*.*#53
Oct  2 18:47:52 mint dnsmasq[3733]: using nameserver *.*.*.*#53
Oct  2 18:47:52 mint dnsmasq[3733]: using nameserver *.*.*.*#53
Oct  2 18:47:52 mint dbus[1797]: [system] Activating service name='org.freedesktop.nm_dispatcher' (using servicehelper)
Oct  2 18:47:52 mint pppd[8234]: Terminating on signal 15
Oct  2 18:47:52 mint pppd[8234]: Child process /usr/sbin/pptp *.*.*.* --nolaunchpppd --loglevel 0 --logstring nm-pptp-service-8233 (pid 8236) terminated with signal 15
Oct  2 18:47:52 mint pppd[8234]: Connect time 0.4 minutes.
Oct  2 18:47:52 mint pppd[8234]: Sent 35680719 bytes, received 10402 bytes.
Oct  2 18:47:52 mint pppd[8234]: MPPE disabled
Oct  2 18:47:52 mint dbus[1797]: [system] Successfully activated service 'org.freedesktop.nm_dispatcher'
Oct  2 18:47:52 mint pppd[8234]: Connection terminated.
Oct  2 18:47:52 mint NetworkManager[2379]:    SCPlugin-Ifupdown: devices removed (path: /sys/devices/virtual/net/ppp0, iface: ppp0)
Oct  2 18:47:52 mint pppd[8234]: Exit.
Oct  2 18:47:52 mint pptp[8237]: nm-pptp-service-8233 warn[decaps_hdlc:pptp_gre.c:204]: short read (-1): Input/output error
Oct  2 18:47:52 mint pptp[8237]: nm-pptp-service-8233 warn[decaps_hdlc:pptp_gre.c:216]: pppd may have shutdown, see pppd log
Oct  2 18:47:52 mint pptp[8246]: nm-pptp-service-8233 log[callmgr_main:pptp_callmgr.c:234]: Closing connection (unhandled)
Oct  2 18:47:52 mint pptp[8246]: nm-pptp-service-8233 log[ctrlp_rep:pptp_ctrl.c:251]: Sent control packet type is 12 'Call-Clear-Request'
Oct  2 18:47:52 mint pptp[8246]: nm-pptp-service-8233 log[call_callback:pptp_callmgr.c:79]: Closing connection (call state)
Oct  2 18:47:57 mint ntpd[8397]: Deleting interface #4 ppp0, 130.115.76.1#123, interface stats: received=0, sent=0, dropped=0, active_time=2 secs
Oct  2 18:47:57 mint ntpd[8397]: peers refreshed

```


I am running
```

KDE Development Platform: 4.10.4
KWin: 4.10.4
Linux mint 3.8.0-26-generic #38-Ubuntu SMP Mon Jun 17 21:43:33 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux
Linux Mint 15 Olivia

```


Thanks in advance!


----------------


I would also like to add the following debug information from pptp:

Attempting successful VPN connection through "public-wifi":
```

# pon myvpn nodetach debug dump logfd 2 nodetach
pppd options in effect:
debug           # (from command line)
nodetach                # (from command line)
logfd 2         # (from command line)
linkname myvpn          # (from /etc/ppp/peers/myvpn)
dump            # (from command line)
noauth          # (from /etc/ppp/options.pptp)
refuse-pap              # (from /etc/ppp/options.pptp)
refuse-chap             # (from /etc/ppp/options.pptp)
refuse-mschap           # (from /etc/ppp/options.pptp)
refuse-eap              # (from /etc/ppp/options.pptp)
name ******            # (from /etc/ppp/peers/myvpn)
remotename myvpn                # (from /etc/ppp/peers/myvpn)
                # (from /etc/ppp/options.pptp)
pty pptp vpn-******.** --nolaunchpppd             # (from /etc/ppp/peers/myvpn)
crtscts         # (from /etc/ppp/options)
                # (from /etc/ppp/options)
asyncmap 0              # (from /etc/ppp/options)
lcp-echo-failure 4              # (from /etc/ppp/options)
lcp-echo-interval 30            # (from /etc/ppp/options)
hide-password           # (from /etc/ppp/options)
ipparam myvpn           # (from /etc/ppp/peers/myvpn)
usepeerdns              # (from /etc/ppp/peers/myvpn)
nobsdcomp               # (from /etc/ppp/options.pptp)
nodeflate               # (from /etc/ppp/options.pptp)
require-mppe            # (from /etc/ppp/peers/myvpn)
noipx           # (from /etc/ppp/options)
using channel 60
Using interface ppp0
Connect: ppp0 <--> /dev/pts/13
sent [LCP ConfReq id=0x1 <asyncmap 0x0> <magic 0xfc49d3bf> <pcomp> <accomp>]
rcvd [LCP ConfRej id=0x1 <accomp>]
sent [LCP ConfReq id=0x2 <asyncmap 0x0> <magic 0xfc49d3bf> <pcomp>]
rcvd [LCP ConfRej id=0x2 <pcomp>]
sent [LCP ConfReq id=0x3 <asyncmap 0x0> <magic 0xfc49d3bf>]
rcvd [LCP ConfAck id=0x3 <asyncmap 0x0> <magic 0xfc49d3bf>]
rcvd [LCP ConfReq id=0x1 <auth chap MS-v2>]
sent [LCP ConfAck id=0x1 <auth chap MS-v2>]
sent [LCP EchoReq id=0x0 magic=0xfc49d3bf]
rcvd [CHAP Challenge id=0x1 <f290f002c65279dd740e1a8317d6da7b>, name = ""]
sent [CHAP Response id=0x1 <dc6df16ec406c22725e7f19f8db5c6df00000000000000007f5144a708fc347b0f51b0ecbef1334050a5cede7e9bfc8400>, name = "********"]
rcvd [LCP EchoRep id=0x0 magic=0x0]
rcvd [CHAP Challenge id=0x2 <bdf54feb72a079a9740e1a8317d6da7b>, name = ""]
sent [CHAP Response id=0x2 <9a5e97e2ae790fdbe55825450fa5c32f0000000000000000d7a6fdcfba979170717d6dd7739a0efa1785815bb06e14c200>, name = "********"]]
rcvd [CHAP Success id=0x2 "S=B4922E7D4A2F3925AA1F839B202784BDB5997DAA"]
CHAP authentication succeeded
sent [CCP ConfReq id=0x1 <mppe +H -M +S +L -D -C>]
rcvd [IPCP ConfReq id=0x0 <addr *.*.*.*>]
sent [IPCP TermAck id=0x0]
rcvd [CCP ConfReq id=0x0 <mppe +H -M +S +L -D -C>]
sent [CCP ConfNak id=0x0 <mppe +H -M +S -L -D -C>]
rcvd [CCP ConfNak id=0x1 <mppe +H -M +S -L -D -C>]
sent [CCP ConfReq id=0x2 <mppe +H -M +S -L -D -C>]
rcvd [CCP ConfReq id=0x1 <mppe +H -M +S -L -D -C>]
sent [CCP ConfAck id=0x1 <mppe +H -M +S -L -D -C>]
rcvd [CCP ConfAck id=0x2 <mppe +H -M +S -L -D -C>]
MPPE 128-bit stateless compression enabled
sent [IPCP ConfReq id=0x1 <compress VJ 0f 01> <addr 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns2 0.0.0.0>]
rcvd [IPCP ConfReq id=0x1 <addr *.*.*.*>]
sent [IPCP ConfAck id=0x1 <addr *.*.*.*>]
sent [IPCP ConfReq id=0x1 <compress VJ 0f 01> <addr 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns2 0.0.0.0>]
rcvd [IPCP ConfRej id=0x1 <compress VJ 0f 01>]
sent [IPCP ConfReq id=0x2 <addr 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns2 0.0.0.0>]
rcvd [IPCP ConfNak id=0x2 <addr *.*.*.*> <ms-dns1 *.*.*.*> <ms-dns2 *.*.*.*>]
sent [IPCP ConfReq id=0x3 <addr *.*.*.*> <ms-dns1 *.*.*.*> <ms-dns2 *.*.*.*>]
rcvd [IPCP ConfAck id=0x3 <addr *.*.*.*> <ms-dns1 *.*.*.*> <ms-dns2 *.*.*.*>]
local  IP address *.*.*.*
remote IP address *.*.*.*
primary   DNS address *.*.*.*
secondary DNS address *.*.*.*
Script /etc/ppp/ip-up started (pid 16644)
Script /etc/ppp/ip-up finished (pid 16644), status = 0x0
^CTerminating on signal 2
Connect time 0.2 minutes.
Sent 0 bytes, received 373 bytes.
Script /etc/ppp/ip-down started (pid 16705)
MPPE disabled
sent [LCP TermReq id=0x4 "MPPE disabled"]
sent [LCP TermReq id=0x5 "MPPE disabled"]
Child process pptp vpn-******.** --nolaunchpppd  (pid 16599) terminated with signal 2
Modem hangup
Connection terminated.
Waiting for 1 child processes...
  script /etc/ppp/ip-down, pid 16705
Script /etc/ppp/ip-down finished (pid 16705), status = 0x0

```

Attempting failed VPN connection through "my-home", using same computer/linux installation:
```

# pon myvpn nodetach debug dump logfd 2 nodetach
pppd options in effect:
debug           # (from command line)
nodetach                # (from command line)
logfd 2         # (from command line)
linkname myvpn          # (from /etc/ppp/peers/myvpn)
dump            # (from command line)
noauth          # (from /etc/ppp/options.pptp)
refuse-pap              # (from /etc/ppp/options.pptp)
refuse-chap             # (from /etc/ppp/options.pptp)
refuse-mschap           # (from /etc/ppp/options.pptp)
refuse-eap              # (from /etc/ppp/options.pptp)
name *******           # (from /etc/ppp/peers/myvpn)
remotename myvpn                # (from /etc/ppp/peers/myvpn)
                # (from /etc/ppp/options.pptp)
pty pptp vpn-*******.** --nolaunchpppd             # (from /etc/ppp/peers/myvpn)
crtscts         # (from /etc/ppp/options)
                # (from /etc/ppp/options)
asyncmap 0              # (from /etc/ppp/options)
lcp-echo-failure 4              # (from /etc/ppp/options)
lcp-echo-interval 30            # (from /etc/ppp/options)
hide-password           # (from /etc/ppp/options)
ipparam myvpn           # (from /etc/ppp/peers/myvpn)
usepeerdns              # (from /etc/ppp/peers/myvpn)
nobsdcomp               # (from /etc/ppp/options.pptp)
nodeflate               # (from /etc/ppp/options.pptp)
require-mppe            # (from /etc/ppp/peers/myvpn)
noipx           # (from /etc/ppp/options)
using channel 59
Using interface ppp0
Connect: ppp0 <--> /dev/pts/13
sent [LCP ConfReq id=0x1 <asyncmap 0x0> <magic 0xf35fb83b> <pcomp> <accomp>]
sent [LCP ConfReq id=0x1 <asyncmap 0x0> <magic 0xf35fb83b> <pcomp> <accomp>]
sent [LCP ConfReq id=0x1 <asyncmap 0x0> <magic 0xf35fb83b> <pcomp> <accomp>]
sent [LCP ConfReq id=0x1 <asyncmap 0x0> <magic 0xf35fb83b> <pcomp> <accomp>]
sent [LCP ConfReq id=0x1 <asyncmap 0x0> <magic 0xf35fb83b> <pcomp> <accomp>]
sent [LCP ConfReq id=0x1 <asyncmap 0x0> <magic 0xf35fb83b> <pcomp> <accomp>]
sent [LCP ConfReq id=0x1 <asyncmap 0x0> <magic 0xf35fb83b> <pcomp> <accomp>]
sent [LCP ConfReq id=0x1 <asyncmap 0x0> <magic 0xf35fb83b> <pcomp> <accomp>]
sent [LCP ConfReq id=0x1 <asyncmap 0x0> <magic 0xf35fb83b> <pcomp> <accomp>]
sent [LCP ConfReq id=0x1 <asyncmap 0x0> <magic 0xf35fb83b> <pcomp> <accomp>]
LCP: timeout sending Config-Requests
Connection terminated.
Modem hangup
Waiting for 1 child processes...
  script pptp vpn-*******.** --nolaunchpppd , pid 16278
Script pptp vpn-*******.** --nolaunchpppd  finished (pid 16278), status = 0x0


```

---

### Post by costis on 2014-05-12
There must be a problem with the router. I do not understand why a laptop with Windows can connect through the same router, though. I've tried enabling ip_gre kernel module but nothing.... Running ```
sudo hping3 -0 -H 47 -d 10 --traceroute   server.ip.address
``` is not working either...

---

### Post by costis on 2014-05-12
Ok, it is finally, after many months and frustration solved. I recompiled the kernel with the default configuration and it finally works! The kernel version is 3.14.3. For future reference, it did not work with the generic ubuntu kernel, but I cannot afford verifying why the generic did not work. I have uploaded a configuration file of the kernel with the non-default values (I reconfigured it for my needs) at ```
/proc/config.gz
``` on [http://filebin.ca/1MBwfEUqmgUV/config.gz]("http://filebin.ca/1MBwfEUqmgUV/config.gz") if somebody is interested in that.

---

### Post by costis on 2015-02-26
I finally (lol) understood what was going on. Both "nf_conntrack_proto_gre" and "nf_conntrack_pptp" modules must be enabled in the kernel:
Code:
```
$ sudo modprobe nf_conntrack_proto_gre nf_conntrack_pptp
```

---

