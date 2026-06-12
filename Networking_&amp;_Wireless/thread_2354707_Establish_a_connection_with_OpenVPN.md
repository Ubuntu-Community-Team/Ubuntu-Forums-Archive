---
title: "Establish a connection with OpenVPN"
date: 2017-03-05
forum: Networking &amp; Wireless
---

### Post by artouf06 on 2017-03-05
[COLOR=#141414][FONT=Georgia]I am trying to establish a VPN connection on a Raspberry Pi. But I cannot make this work.[/FONT][/COLOR]
[COLOR=#141414][FONT=Georgia]
[/FONT][/COLOR]
[COLOR=#141414][FONT=Georgia]I am using VPNBook and I downloaded the .ovpn file in order to use OpenVPN.[/FONT][/COLOR]
[COLOR=#141414][FONT=Georgia]
[/FONT][/COLOR]
[COLOR=#141414][FONT=Georgia]Here is the content of the .ovpn file:[/FONT][/COLOR]
```

[COLOR=#141414][FONT=Georgia]    client[/FONT][/COLOR]
[COLOR=#141414][FONT=Georgia]    dev tun3[/FONT][/COLOR]
[COLOR=#141414][FONT=Georgia]    proto tcp[/FONT][/COLOR]
[COLOR=#141414][FONT=Georgia]    remote 176.126.237.217 80[/FONT][/COLOR]
[COLOR=#141414][FONT=Georgia]    remote euro217.vpnbook.com 80[/FONT][/COLOR]
[COLOR=#141414][FONT=Georgia]    resolv-retry infinite[/FONT][/COLOR]
[COLOR=#141414][FONT=Georgia]    nobind[/FONT][/COLOR]
[COLOR=#141414][FONT=Georgia]    persist-key[/FONT][/COLOR]
[COLOR=#141414][FONT=Georgia]    persist-tun[/FONT][/COLOR]
[COLOR=#141414][FONT=Georgia]    auth-user-pass pass.txt[/FONT][/COLOR]
[COLOR=#141414][FONT=Georgia]    comp-lzo[/FONT][/COLOR]
[COLOR=#141414][FONT=Georgia]    verb 3[/FONT][/COLOR]
[COLOR=#141414][FONT=Georgia]    cipher AES-128-CBC[/FONT][/COLOR]
[COLOR=#141414][FONT=Georgia]    fast-io[/FONT][/COLOR]
[COLOR=#141414][FONT=Georgia]    pull[/FONT][/COLOR]
[COLOR=#141414][FONT=Georgia]    redirect-gateway[/FONT][/COLOR]
[COLOR=#141414][FONT=Georgia]    script-security 2[/FONT][/COLOR]

```
[COLOR=#141414][FONT=Georgia]Here is the output I get:[/FONT][/COLOR]
```

[COLOR=#141414][FONT=Georgia]    pi@raspberrypi:/etc/openvpn/vpnbook $ sudo openvpn --config vpnbook-euro1-tcp80.ovpn[/FONT][/COLOR]
[COLOR=#141414][FONT=Georgia]    Wed Feb  8 00:07:45 2017 OpenVPN 2.3.4 arm-unknown-linux-gnueabihf [SSL (OpenSSL)] [LZO] [EPOLL] [PKCS11] [MH] [IPv6] built on Jan 23 2016[/FONT][/COLOR]
[COLOR=#141414][FONT=Georgia]    Wed Feb  8 00:07:45 2017 library versions: OpenSSL 1.0.1t  3 May 2016, LZO 2.08[/FONT][/COLOR]
[COLOR=#141414][FONT=Georgia]    Wed Feb  8 00:07:45 2017 WARNING: file 'pass.txt' is group or others accessible[/FONT][/COLOR]
[COLOR=#141414][FONT=Georgia]    Wed Feb  8 00:07:45 2017 WARNING: No server certificate verification method has been enabled.  See http://openvpn.net/howto.html#mitm for more info.[/FONT][/COLOR]
[COLOR=#141414][FONT=Georgia]    Wed Feb  8 00:07:45 2017 NOTE: --fast-io is disabled since we are not using UDP[/FONT][/COLOR]
[COLOR=#141414][FONT=Georgia]    Wed Feb  8 00:07:45 2017 Socket Buffers: R=[87380->131072] S=[16384->131072][/FONT][/COLOR]
[COLOR=#141414][FONT=Georgia]    Wed Feb  8 00:07:45 2017 Attempting to establish TCP connection with [AF_INET]176.126.237.217:80 [nonblock][/FONT][/COLOR]
[COLOR=#141414][FONT=Georgia]    Wed Feb  8 00:07:46 2017 TCP connection established with [AF_INET]176.126.237.217:80[/FONT][/COLOR]
[COLOR=#141414][FONT=Georgia]    Wed Feb  8 00:07:46 2017 TCPv4_CLIENT link local: [undef][/FONT][/COLOR]
[COLOR=#141414][FONT=Georgia]    Wed Feb  8 00:07:46 2017 TCPv4_CLIENT link remote: [AF_INET]176.126.237.217:80[/FONT][/COLOR]
[COLOR=#141414][FONT=Georgia]    Wed Feb  8 00:07:46 2017 TLS: Initial packet from [AF_INET]176.126.237.217:80, sid=f8773375 a8e3c418[/FONT][/COLOR]
[COLOR=#141414][FONT=Georgia]    Wed Feb  8 00:07:46 2017 WARNING: this configuration may cache passwords in memory -- use the auth-nocache option to prevent this[/FONT][/COLOR]
[COLOR=#141414][FONT=Georgia]    Wed Feb  8 00:07:47 2017 VERIFY OK: depth=1, C=CH, ST=Zurich, L=Zurich, O=vpnbook.com, OU=IT, CN=vpnbook.com, name=vpnbook.com, emailAddress=admin@vpnbook.com[/FONT][/COLOR]
[COLOR=#141414][FONT=Georgia]    Wed Feb  8 00:07:47 2017 VERIFY OK: depth=0, C=CH, ST=Zurich, L=Zurich, O=vpnbook.com, OU=IT, CN=vpnbook.com, name=vpnbook.com, emailAddress=admin@vpnbook.com[/FONT][/COLOR]
[COLOR=#141414][FONT=Georgia]    Wed Feb  8 00:07:48 2017 Data Channel Encrypt: Cipher 'AES-128-CBC' initialized with 128 bit key[/FONT][/COLOR]
[COLOR=#141414][FONT=Georgia]    Wed Feb  8 00:07:48 2017 Data Channel Encrypt: Using 160 bit message hash 'SHA1' for HMAC authentication[/FONT][/COLOR]
[COLOR=#141414][FONT=Georgia]    Wed Feb  8 00:07:48 2017 Data Channel Decrypt: Cipher 'AES-128-CBC' initialized with 128 bit key[/FONT][/COLOR]
[COLOR=#141414][FONT=Georgia]    Wed Feb  8 00:07:48 2017 Data Channel Decrypt: Using 160 bit message hash 'SHA1' for HMAC authentication[/FONT][/COLOR]
[COLOR=#141414][FONT=Georgia]    Wed Feb  8 00:07:48 2017 Control Channel: TLSv1, cipher TLSv1/SSLv3 DHE-RSA-AES256-SHA, 1024 bit RSA[/FONT][/COLOR]
[COLOR=#141414][FONT=Georgia]    Wed Feb  8 00:07:48 2017 [vpnbook.com] Peer Connection Initiated with [AF_INET]176.126.237.217:80[/FONT][/COLOR]
[COLOR=#141414][FONT=Georgia]    Wed Feb  8 00:07:50 2017 SENT CONTROL [vpnbook.com]: 'PUSH_REQUEST' (status=1)[/FONT][/COLOR]
[COLOR=#141414][FONT=Georgia]    Wed Feb  8 00:07:50 2017 PUSH: Received control message: 'PUSH_REPLY,redirect-gateway def1,dhcp-option DNS  89.233.43.71,dhcp-option DNS  91.239.100.100,route 10.12.0.1,topology net30,ping 5,ping-restart 30,ifconfig 10.12.0.6 10.12.0.5'[/FONT][/COLOR]
[COLOR=#141414][FONT=Georgia]    Wed Feb  8 00:07:50 2017 OPTIONS IMPORT: timers and/or timeouts modified[/FONT][/COLOR]
[COLOR=#141414][FONT=Georgia]    Wed Feb  8 00:07:50 2017 OPTIONS IMPORT: --ifconfig/up options modified[/FONT][/COLOR]
[COLOR=#141414][FONT=Georgia]    Wed Feb  8 00:07:50 2017 OPTIONS IMPORT: route options modified[/FONT][/COLOR]
[COLOR=#141414][FONT=Georgia]    Wed Feb  8 00:07:50 2017 OPTIONS IMPORT: --ip-win32 and/or --dhcp-option options modified[/FONT][/COLOR]
[COLOR=#141414][FONT=Georgia]    Wed Feb  8 00:07:50 2017 ROUTE_GATEWAY 192.168.0.1/255.255.255.0 IFACE=wlan0 HWADDR=b8:27:eb:e3:f8:56[/FONT][/COLOR]
[COLOR=#141414][FONT=Georgia]    Wed Feb  8 00:07:50 2017 TUN/TAP device tun3 opened[/FONT][/COLOR]
[COLOR=#141414][FONT=Georgia]    Wed Feb  8 00:07:50 2017 TUN/TAP TX queue length set to 100[/FONT][/COLOR]
[COLOR=#141414][FONT=Georgia]    Wed Feb  8 00:07:50 2017 do_ifconfig, tt->ipv6=0, tt->did_ifconfig_ipv6_setup=0[/FONT][/COLOR]
[COLOR=#141414][FONT=Georgia]    Wed Feb  8 00:07:50 2017 /sbin/ip link set dev tun3 up mtu 1500[/FONT][/COLOR]
[COLOR=#141414][FONT=Georgia]    Wed Feb  8 00:07:50 2017 /sbin/ip addr add dev tun3 local 10.12.0.6 peer 10.12.0.5[/FONT][/COLOR]
[COLOR=#141414][FONT=Georgia]    Wed Feb  8 00:07:50 2017 /sbin/ip route add 176.126.237.217/32 via 192.168.0.1[/FONT][/COLOR]
[COLOR=#141414][FONT=Georgia]    Wed Feb  8 00:07:50 2017 /sbin/ip route add 0.0.0.0/1 via 10.12.0.5[/FONT][/COLOR]
[COLOR=#141414][FONT=Georgia]    Wed Feb  8 00:07:50 2017 /sbin/ip route add 128.0.0.0/1 via 10.12.0.5[/FONT][/COLOR]
[COLOR=#141414][FONT=Georgia]    Wed Feb  8 00:07:50 2017 /sbin/ip route add 10.12.0.1/32 via 10.12.0.5[/FONT][/COLOR]
[COLOR=#141414][FONT=Georgia]    Wed Feb  8 00:07:50 2017 Initialization Sequence Completed[/FONT][/COLOR]

```
[COLOR=#141414][FONT=Georgia]At this point, I cannot access any website (by putting name or IP address). However, I can ping some IP addresses like 216.58.212.99 but not hostnames like [www.google.fr]("http://www.google.fr/").[/FONT][/COLOR]
[COLOR=#141414][FONT=Georgia]
[/FONT][/COLOR]
[COLOR=#141414][FONT=Georgia]I thought it was a DNS issue, I tried to search for it and updated my .ovpn file with the following lines:[/FONT][/COLOR]
```

[COLOR=#141414][FONT=Georgia]    up /etc/openvpn/update-resolv-conf[/FONT][/COLOR]
[COLOR=#141414][FONT=Georgia]    down /etc/openvpn/update-resolv-conf[/FONT][/COLOR]

```
[COLOR=#141414][FONT=Georgia]This didn't change anything.[/FONT][/COLOR]
[COLOR=#141414][FONT=Georgia]
[/FONT][/COLOR]
[COLOR=#141414][FONT=Georgia]I also tried with another VPN (VPNGate) but I have the same behaviour.[/FONT][/COLOR]
[COLOR=#141414][FONT=Georgia]
[/FONT][/COLOR]
[COLOR=#141414][FONT=Georgia]Everything about the network is painfully slow once openvpn is launch. And I don't even know if the tunnel is working. How to be sure without being able to load a single website? Everything is just really slow and I don't know why. It probably comes from my configuration because I guess I'm not the only one using VPNBook, and also tried with another VPN provider with the same result.[/FONT][/COLOR]
[COLOR=#141414][FONT=Georgia]
[/FONT][/COLOR]
[COLOR=#141414][FONT=Georgia]Having been stuck with this problem for 2 months now, I am reading a tutorial to fully understand how a network is working.[/FONT][/COLOR]
[COLOR=#141414][FONT=Georgia]For what I can say at the moment, I see 2 strange things in my configuration when the VPN is activated.[/FONT][/COLOR]
[COLOR=#141414][FONT=Georgia]
[/FONT][/COLOR]
[COLOR=#141414][FONT=Georgia]First, on the "tun3" interface created for the connection with the VPN, the MAC address is full of 0. Shouldn't it be the same as my other interface?[/FONT][/COLOR]
```

[COLOR=#141414][FONT=Georgia]    tun3      Link encap:UNSPEC  HWaddr 00-00-00-00-00-00-00-00-00-00-00-00-00-00-00-00[/FONT][/COLOR]
[COLOR=#141414][FONT=Georgia]              inet addr:10.12.0.170  P-t-P:10.12.0.169  Mask:255.255.255.255[/FONT][/COLOR]
[COLOR=#141414][FONT=Georgia]              UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1500  Metric:1[/FONT][/COLOR]
[COLOR=#141414][FONT=Georgia]              RX packets:126 errors:0 dropped:0 overruns:0 frame:0[/FONT][/COLOR]
[COLOR=#141414][FONT=Georgia]              TX packets:358 errors:0 dropped:0 overruns:0 carrier:0[/FONT][/COLOR]
[COLOR=#141414][FONT=Georgia]              collisions:0 txqueuelen:100[/FONT][/COLOR]
[COLOR=#141414][FONT=Georgia]              RX bytes:16864 (16.4 KiB)  TX bytes:35559 (34.7 KiB)[/FONT][/COLOR]
[COLOR=#141414][FONT=Georgia]
[/FONT][/COLOR]
[COLOR=#141414][FONT=Georgia]    wlan0     Link encap:Ethernet  HWaddr b8:27:eb:e3:f8:56[/FONT][/COLOR]
[COLOR=#141414][FONT=Georgia]              inet addr:192.168.0.17  Bcast:192.168.0.255  Mask:255.255.255.0[/FONT][/COLOR]
[COLOR=#141414][FONT=Georgia]              inet6 addr: fe80::6dfb:5d45:2ae7:fe43/64 Scope:Link[/FONT][/COLOR]
[COLOR=#141414][FONT=Georgia]              UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1[/FONT][/COLOR]
[COLOR=#141414][FONT=Georgia]              RX packets:24791 errors:0 dropped:7790 overruns:0 frame:0[/FONT][/COLOR]
[COLOR=#141414][FONT=Georgia]              TX packets:19963 errors:0 dropped:0 overruns:0 carrier:0[/FONT][/COLOR]
[COLOR=#141414][FONT=Georgia]              collisions:0 txqueuelen:1000[/FONT][/COLOR]
[COLOR=#141414][FONT=Georgia]              RX bytes:4974169 (4.7 MiB)  TX bytes:2843776 (2.7 MiB)[/FONT][/COLOR]

```
[COLOR=#141414][FONT=Georgia]
[/FONT][/COLOR]
[COLOR=#141414][FONT=Georgia]Second, the route table (which is displayed very slowly when the VPN is on):[/FONT][/COLOR]
[COLOR=#141414][FONT=Georgia]
[/FONT][/COLOR]
[COLOR=#141414][FONT=Georgia]Without VPN:[/FONT][/COLOR]
```

[COLOR=#141414][FONT=Georgia]    Destination     Gateway         Genmask         Flags Metric Ref    Use Iface[/FONT][/COLOR]
[COLOR=#141414][FONT=Georgia]    default         192.168.0.1     0.0.0.0         UG    303    0        0 wlan0[/FONT][/COLOR]
[COLOR=#141414][FONT=Georgia]    192.168.0.0     *               255.255.255.0   U     303    0        0 wlan0[/FONT][/COLOR]

```
[COLOR=#141414][FONT=Georgia]
[/FONT][/COLOR]
[COLOR=#141414][FONT=Georgia]With VPN:[/FONT][/COLOR]
```

[COLOR=#141414][FONT=Georgia]    Destination     Gateway         Genmask         Flags Metric Ref    Use Iface[/FONT][/COLOR]
[COLOR=#141414][FONT=Georgia]    default         10.12.0.169     128.0.0.0       UG    0      0        0 tun3[/FONT][/COLOR]
[COLOR=#141414][FONT=Georgia]    default         192.168.0.1     0.0.0.0         UG    303    0        0 wlan0[/FONT][/COLOR]
[COLOR=#141414][FONT=Georgia]    10.12.0.1       10.12.0.169     255.255.255.255 UGH   0      0        0 tun3[/FONT][/COLOR]
[COLOR=#141414][FONT=Georgia]    10.12.0.169     *               255.255.255.255 UH    0      0        0 tun3[/FONT][/COLOR]
[COLOR=#141414][FONT=Georgia]    128.0.0.0       10.12.0.169     128.0.0.0       UG    0      0        0 tun3[/FONT][/COLOR]
[COLOR=#141414][FONT=Georgia]    176.126.237.217 192.168.0.1     255.255.255.255 UGH   0      0        0 wlan0[/FONT][/COLOR]
[COLOR=#141414][FONT=Georgia]    192.168.0.0     *               255.255.255.0   U     303    0        0 wlan0[/FONT][/COLOR]

```
[COLOR=#141414][FONT=Georgia]Here there is 1 gateaway that I can't even ping: 10.12.0.169. Actually I don't even understand why I have this new IP address completely different from the rest of my network. Shouldn't "tun3" also have an IP address like 192.168.0.xxx? Also, except for the route toward my own local network, shouldn't the gateway be 192.168.0.1 (my internet provider) for all the destinations?[/FONT][/COLOR]
[COLOR=#141414][FONT=Georgia]
[/FONT][/COLOR]
[COLOR=#141414][FONT=Georgia]My ISP blocked the VPN connection, but I have now activated the PPTP, IPSEC and MULTICAST pass-through, and I still have the same behaviour.[/FONT][/COLOR]

---

### Post by artouf06 on 2017-03-16
[COLOR=#242729][FONT=Arial]What can I do step by step to understand my problem? I've tried thousand of things I found on the internet, without any success. I definitely can't tell all the things I've tried. I actually manage to connect to a single website, cisco, but only with its IP address 72.163.4.161. The "same" configuration (but obviously not the same) on my Windows PC on the same local network works perfectly fine.[/FONT][/COLOR]

---

