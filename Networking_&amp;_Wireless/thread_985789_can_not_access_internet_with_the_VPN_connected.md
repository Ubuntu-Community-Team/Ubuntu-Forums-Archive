---
title: "can not access internet with the VPN connected"
date: 2008-11-18
forum: Networking &amp; Wireless
---

### Post by nashjiang on 2008-11-18
Hello,

I have a PC with Ubuntu 8.1 I need to connect to my office through VPN (PPTP). Right now, I have a question: 

When the VPN is connected, I can not access internet via my local gateway.  If the VPN is disconnected, the internet is ok. 

I guess the route table was changed or something once VPN connected.

Could you please tell me how can I access internet via my local gateway with the VPN connected?



Thanks in advance

---

### Post by Songwind on 2008-11-23
I just went through this same problem with my work VPN, and wrote up what I did to fix it on my blog.  [http://dragonseptarts.com/blog/?p=159](http://dragonseptarts.com/blog/?p=159)

---

### Post by manhattan on 2011-04-02
I also cannot access the internet with the VPN connected -using Ubuntu 10.10 And I can't view blogs, because I am in China -by and large non-domestic blogs are off limits in China ergo my need for VPN. The VPN provider hasn't gotten back to me on how to connect, since I requested assistance 4 days ago (few commercial VPN providers support linux proper). Below I've posted what I could gather of the log.

> Mar 31 23:18:42 Hasee-A-i7 NetworkManager[954]: <info> Starting VPN service 'org.freedesktop.NetworkManager.openvpn'...
Mar 31 23:18:42 Hasee-A-i7 NetworkManager[954]: <info> VPN service 'org.freedesktop.NetworkManager.openvpn' started (org.freedesktop.NetworkManager.openvpn), PID 6408
Mar 31 23:18:42 Hasee-A-i7 NetworkManager[954]: <info> VPN service 'org.freedesktop.NetworkManager.openvpn' appeared, activating connections
Mar 31 23:18:42 Hasee-A-i7 NetworkManager[954]: <info> VPN plugin state changed: 1
Mar 31 23:18:42 Hasee-A-i7 NetworkManager[954]: <info> VPN plugin state changed: 3
Mar 31 23:18:42 Hasee-A-i7 NetworkManager[954]: <info> VPN connection '01-LosAngeles_BEST_FOR_ASIA' (Connect) reply received.
Mar 31 23:18:42 Hasee-A-i7 nm-openvpn[6411]: OpenVPN 2.1.0 i686-pc-linux-gnu [SSL] [LZO2] [EPOLL] [PKCS11] [MH] [PF_INET6] [eurephia] built on Jul 12 2010
Mar 31 23:18:42 Hasee-A-i7 nm-openvpn[6411]: WARNING: Make sure you understand the semantics of --tls-remote before using it (see the man page).
Mar 31 23:18:42 Hasee-A-i7 nm-openvpn[6411]: NOTE: the current --script-security setting may allow this configuration to call user-defined scripts
Mar 31 23:18:42 Hasee-A-i7 nm-openvpn[6411]: /usr/bin/openssl-vulnkey -q -b 1024 -m <modulus omitted>
Mar 31 23:18:42 Hasee-A-i7 nm-openvpn[6411]: Control Channel Authentication: using '/home/harlan/expressVPN/23065365692472246836865/ssl/ta.key' as a OpenVPN static key file
Mar 31 23:18:42 Hasee-A-i7 nm-openvpn[6411]: RESOLVE: NOTE: la-cluster4.expressnetwork.net resolves to 2 addresses, choosing one by random
Mar 31 23:18:42 Hasee-A-i7 nm-openvpn[6411]: UDPv4 link local: [undef]
Mar 31 23:18:42 Hasee-A-i7 nm-openvpn[6411]: UDPv4 link remote: [AF_INET]174.34.143.179:1194
Mar 31 23:18:46 Hasee-A-i7 nm-openvpn[6411]: WARNING: 'link-mtu' is used inconsistently, local='link-mtu 1545', remote='link-mtu 1546'
Mar 31 23:18:46 Hasee-A-i7 nm-openvpn[6411]: WARNING: 'comp-lzo' is present in remote config but missing in local config, remote='comp-lzo'
Mar 31 23:18:46 Hasee-A-i7 nm-openvpn[6411]: [server] Peer Connection Initiated with [AF_INET]174.34.143.179:1194
Mar 31 23:18:49 Hasee-A-i7 nm-openvpn[6411]: TUN/TAP device tun0 opened
Mar 31 23:18:49 Hasee-A-i7 nm-openvpn[6411]: /sbin/ifconfig tun0 10.10.37.82 pointopoint 10.10.37.81 mtu 1500
Mar 31 23:18:49 Hasee-A-i7 NetworkManager[954]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/tun0, iface: tun0)
Mar 31 23:18:49 Hasee-A-i7 NetworkManager[954]:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/tun0, iface: tun0): no ifupdown configuration found.
Mar 31 23:18:49 Hasee-A-i7 kernel: [ 7788.491215] tun0: Disabled Privacy Extensions
Mar 31 23:18:49 Hasee-A-i7 modem-manager: (net/tun0): could not get port's parent device
Mar 31 23:18:49 Hasee-A-i7 nm-openvpn[6411]: /usr/lib/network-manager-openvpn/nm-openvpn-service-openvpn-helper tun0 1500 1545 10.10.37.82 10.10.37.81 init
Mar 31 23:18:49 Hasee-A-i7 NetworkManager[954]: <info> VPN connection '01-LosAngeles_BEST_FOR_ASIA' (IP Config Get) reply received.
Mar 31 23:18:49 Hasee-A-i7 NetworkManager[954]: <info> VPN Gateway: 174.34.143.179
Mar 31 23:18:49 Hasee-A-i7 NetworkManager[954]: <info> Internal Gateway: 10.10.37.81
Mar 31 23:18:49 Hasee-A-i7 NetworkManager[954]: <info> Tunnel Device: tun0
Mar 31 23:18:49 Hasee-A-i7 NetworkManager[954]: <info> Internal IP4 Address: 10.10.37.82
Mar 31 23:18:49 Hasee-A-i7 NetworkManager[954]: <info> Internal IP4 Prefix: 32
Mar 31 23:18:49 Hasee-A-i7 NetworkManager[954]: <info> Internal IP4 Point-to-Point Address: 10.10.37.81
Mar 31 23:18:49 Hasee-A-i7 NetworkManager[954]: <info> Maximum Segment Size (MSS): 0
Mar 31 23:18:49 Hasee-A-i7 NetworkManager[954]: <info> Static Route: 10.10.0.1/32   Next Hop: 10.10.0.1
Mar 31 23:18:49 Hasee-A-i7 NetworkManager[954]: <info> Internal IP4 DNS: 8.8.8.8
Mar 31 23:18:49 Hasee-A-i7 NetworkManager[954]: <info> Internal IP4 DNS: 68.94.157.1
Mar 31 23:18:49 Hasee-A-i7 NetworkManager[954]: <info> DNS Domain: '(none)'
Mar 31 23:18:49 Hasee-A-i7 nm-openvpn[6411]: Initialization Sequence Completed
Mar 31 23:18:50 Hasee-A-i7 NetworkManager[954]: <info> VPN connection '01-LosAngeles_BEST_FOR_ASIA' (IP Config Get) complete.
Mar 31 23:18:50 Hasee-A-i7 NetworkManager[954]: <info> Policy set '01-LosAngeles_BEST_FOR_ASIA' (tun0) as default for IPv4 routing and DNS.
Mar 31 23:18:50 Hasee-A-i7 NetworkManager[954]: <info> VPN plugin state changed: 4
Mar 31 23:18:50 Hasee-A-i7 nm-dispatcher.action: Script '/etc/NetworkManager/dispatcher.d/01ifupdown' exited with error status 1.
Mar 31 23:18:58 Hasee-A-i7 nm-openvpn[6411]: write to TUN/TAP : Invalid argument (code=22)
Mar 31 23:19:49 Hasee-A-i7 nm-openvpn[6411]: last message repeated 4 times
Mar 31 23:19:49 Hasee-A-i7 kernel: [ 7847.851449] NVRM: os_raise_smp_barrier(), invalid context!
Mar 31 23:19:49 Hasee-A-i7 kernel: [ 7847.867919] NVRM: os_raise_smp_barrier(), invalid context!
Mar 31 23:19:53 Hasee-A-i7 nm-openvpn[6411]: write to TUN/TAP : Invalid argument (code=22)
Mar 31 23:19:54 Hasee-A-i7 kernel: [ 7852.858254] NVRM: os_raise_smp_barrier(), invalid context!
Mar 31 23:19:54 Hasee-A-i7 kernel: [ 7852.873101] NVRM: os_raise_smp_barrier(), invalid context!

---

### Post by manhattan on 2011-04-03
So far I have tried 
iptables -t nat -A POSTROUTING -o eth0 -j MASQUERADE
--nothing


sudo apt-get install kvpn
-- When I run Kvpn I get an error message telling me that ca.crt path isn't valid -but as far as I can tell ca.crt is in the listed directory.

sudo apt-get remove openvpn -y
--Foollowed by a reboot and then...

sudo apt-get install openvpn network-manager-openvpn -y
--Then I imported the VPN information into openVPN manager.

The only thing I can think of is to go back to Windows7 which is an officially supported OS by the VPN provider and stop goofing around with an OS that is clearly way out of my league.

---

### Post by Sven6210 on 2011-04-06
> **manhattan said:**
> I also cannot access the internet with the VPN connected -using Ubuntu 10.10 And I can't view blogs, because I am in China -by and large non-domestic blogs are off limits in China ergo my need for VPN. The VPN provider hasn't gotten back to me on how to connect, since I requested assistance 4 days ago (few commercial VPN providers support linux proper). Below I've posted what I could gather of the log.

Do you use a commercial VPN Provider? I also live in China and use Witopia.org and a private VPN (openVPN) running on my private VServer. Both work Fine in China, for Witopia.org some changes are required. 

Feel free to let me Know in case you are interested in details.

Good luck

Sven

---

### Post by manhattan on 2011-04-13
Thanks for the response Sven,

Yes, I am talking about a commercial VPN.

The provider I'm using is not witopia, but judging by the software interface on Windows, it's not terribly different from witopia.

If you think you've got anything that may shed light on the situation, I may be willing to give Ubuntu another shot.

Thanks

---

