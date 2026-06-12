---
title: "OpenVPN hanging"
date: 2016-05-17
forum: Networking &amp; Wireless
---

### Post by steve258 on 2016-05-17
I've tried for the past three days attempting to solve this. I normally  connect to my VPN on windows but now I dualboot with Ubuntu. The first  day I set up OpenVPN with Ubuntu everything worked fine. But now it just  hangs with the message [B]Initialization Sequence Complete
[/B]
Here's the output:

[HTML]Tue May 17 19:11:46 2016 OpenVPN 2.3.2 i686-pc-linux-gnu [SSL (OpenSSL)] [LZO] [EPOLL] [PKCS11] [eurephia] [MH] [IPv6] built on Dec  1 2014
Tue May 17 19:11:46 2016 NOTE: the current --script-security setting may allow this configuration to call user-defined scripts
Tue May 17 19:11:46 2016 Socket Buffers: R=[163840->131072] S=[163840->131072]
Tue May 17 19:11:46 2016 NOTE: UID/GID downgrade will be delayed because of --client, --pull, or --up-delay
Tue May 17 19:11:46 2016 UDPv4 link local: [undef]
Tue May 17 19:11:46 2016 UDPv4 link remote: [AF_INET]42.93.119.189:1194
Tue May 17 19:11:46 2016 TLS: Initial packet from [AF_INET]42.93.119.189:1194, sid=03bfd43f c4283825
Tue May 17 19:11:47 2016 VERIFY OK: depth=1, C=US, ST=CA, L=SanFrancisco, O=odin, OU=odin, CN=odin CA, name=server, emailAddress=edds32334@gmail.com
Tue May 17 19:11:47 2016 VERIFY OK: nsCertType=SERVER
Tue May 17 19:11:47 2016 VERIFY OK: depth=0, C=US, ST=CA, L=SanFrancisco, O=odin, OU=odin, CN=server, name=server, emailAddress=edds32334@gmail.com
Tue May 17 19:11:48 2016 Data Channel Encrypt: Cipher 'BF-CBC' initialized with 128 bit key
Tue May 17 19:11:48 2016 Data Channel Encrypt: Using 160 bit message hash 'SHA1' for HMAC authentication
Tue May 17 19:11:48 2016 Data Channel Decrypt: Cipher 'BF-CBC' initialized with 128 bit key
Tue May 17 19:11:48 2016 Data Channel Decrypt: Using 160 bit message hash 'SHA1' for HMAC authentication
Tue May 17 19:11:48 2016 Control Channel: TLSv1, cipher TLSv1/SSLv3 DHE-RSA-AES256-SHA, 2048 bit RSA
Tue May 17 19:11:48 2016 [server] Peer Connection Initiated with [AF_INET]42.93.119.189:1194
Tue May 17 19:11:50 2016 SENT CONTROL [server]: 'PUSH_REQUEST' (status=1)
Tue May 17 19:11:50 2016 PUSH: Received control message: 'PUSH_REPLY,redirect-gateway,dhcp-option DNS 8.8.8.8,dhcp-option DNS 8.8.4.4,route 10.8.0.1,topology net30,ping 10,ping-restart 120,ifconfig 10.8.0.10 10.8.0.9'
Tue May 17 19:11:50 2016 OPTIONS IMPORT: timers and/or timeouts modified
Tue May 17 19:11:50 2016 OPTIONS IMPORT: --ifconfig/up options modified
Tue May 17 19:11:50 2016 OPTIONS IMPORT: route options modified
Tue May 17 19:11:50 2016 OPTIONS IMPORT: --ip-win32 and/or --dhcp-option options modified
Tue May 17 19:11:50 2016 ROUTE_GATEWAY 10.0.0.1/255.255.255.0 IFACE=eth0 HWADDR=22:73:e3:1b:8c:33
Tue May 17 19:11:50 2016 TUN/TAP device tun0 opened
Tue May 17 19:11:50 2016 TUN/TAP TX queue length set to 100
Tue May 17 19:11:50 2016 do_ifconfig, tt->ipv6=0, tt->did_ifconfig_ipv6_setup=0
Tue May 17 19:11:50 2016 /sbin/ip link set dev tun0 up mtu 1500
Tue May 17 19:11:50 2016 /sbin/ip addr add dev tun0 local 10.8.0.10 peer 10.8.0.9
Tue May 17 19:11:50 2016 update-resolve-conf.sh tun0 1500 1542 10.8.0.10 10.8.0.9 init
dhcp-option DNS 8.8.8.8
dhcp-option DNS 8.8.8.8
dhcp-option DNS 8.8.4.4
Illegal option -x
Tue May 17 19:11:50 2016 /sbin/ip route add 42.93.119.189/32 via 10.0.0.1
Tue May 17 19:11:50 2016 /sbin/ip route del 0.0.0.0/0
Tue May 17 19:11:50 2016 /sbin/ip route add 0.0.0.0/0 via 10.8.0.9
Tue May 17 19:11:50 2016 /sbin/ip route add 10.8.0.1/32 via 10.8.0.9
Tue May 17 19:11:50 2016 GID set to nogroup
Tue May 17 19:11:50 2016 UID set to nobody
Tue May 17 19:11:50 2016 Initialization Sequence Completed[/HTML]

And here's** ifconfig**:

[HTML]tun0      Link encap:UNSPEC  HWaddr 00-00-00-00-00-00-00-00-00-00-00-00-00-00-00-00  
          inet addr:10.8.0.10  P-t-P:10.8.0.9  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:144 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100 
          RX bytes:0 (0.0 B)  TX bytes:10127 (10.1 KB)[/HTML]

---

