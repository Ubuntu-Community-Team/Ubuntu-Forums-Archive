---
title: "Openvpn connection problem"
date: 2008-08-20
forum: Networking &amp; Wireless
---

### Post by vcbranco on 2008-08-20
Hy all,

I configured the openvpn server and client.

I can connect to the server but I can not connect to any machine or service on the remote network.

I'm not an openvpn or linux expert.

Where can I start to solve this issue?


This is the connection log from the client

Wed Aug 20 18:03:49 2008 OpenVPN 2.1_rc9 i686-pc-mingw32 [SSL] [LZO2] [PKCS11] built on Jul 31 2008
Wed Aug 20 18:03:49 2008 WARNING: Make sure you understand the semantics of --tls-remote before using it (see the man page).
Wed Aug 20 18:03:49 2008 LZO compression initialized
Wed Aug 20 18:03:49 2008 Control Channel MTU parms [ L:1574 D:138 EF:38 EB:0 ET:0 EL:0 ]
Wed Aug 20 18:03:49 2008 Data Channel MTU parms [ L:1574 D:1450 EF:42 EB:135 ET:32 EL:0 AF:3/1 ]
Wed Aug 20 18:03:49 2008 Local Options hash (VER=V4): 'd79ca330'
Wed Aug 20 18:03:49 2008 Expected Remote Options hash (VER=V4): 'f7df56b8'
Wed Aug 20 18:03:49 2008 Socket Buffers: R=[0->0] S=[0->0]
Wed Aug 20 18:03:49 2008 UDPv4 link local: [undef]
Wed Aug 20 18:03:49 2008 UDPv4 link remote: XXX.XXX.XXX.XXX:1194
Wed Aug 20 18:03:49 2008 TLS: Initial packet from XXX.XXX.XXX.XXX:1194, sid=0be7a611 803c058f
Wed Aug 20 18:03:49 2008 VERIFY OK: depth=1, /C=ES/ST=Nation/L=Nowhere/O=site/CN=Certification_Authority_Certificate
Wed Aug 20 18:03:49 2008 VERIFY X509NAME OK: /C=ES/ST=Nation/L=Nowhere/O=site/CN=server
Wed Aug 20 18:03:49 2008 VERIFY OK: depth=0, /C=ES/ST=Nation/L=Nowhere/O=site/CN=server
Wed Aug 20 18:03:50 2008 Data Channel Encrypt: Cipher 'BF-CBC' initialized with 128 bit key
Wed Aug 20 18:03:50 2008 Data Channel Encrypt: Using 160 bit message hash 'SHA1' for HMAC authentication
Wed Aug 20 18:03:50 2008 Data Channel Decrypt: Cipher 'BF-CBC' initialized with 128 bit key
Wed Aug 20 18:03:50 2008 Data Channel Decrypt: Using 160 bit message hash 'SHA1' for HMAC authentication
Wed Aug 20 18:03:50 2008 Control Channel: TLSv1, cipher TLSv1/SSLv3 DHE-RSA-AES256-SHA, 1024 bit RSA
Wed Aug 20 18:03:50 2008 [server] Peer Connection Initiated with 89.152.37.167:1194
Wed Aug 20 18:03:51 2008 SENT CONTROL [server]: 'PUSH_REQUEST' (status=1)
Wed Aug 20 18:03:51 2008 PUSH: Received control message: 'PUSH_REPLY,route 192.168.1.0 255.255.255.0,route-gateway 192.168.2.1,ping 10,ping-restart 120,ifconfig 192.168.2.2 255.255.255.0'
Wed Aug 20 18:03:51 2008 OPTIONS IMPORT: timers and/or timeouts modified
Wed Aug 20 18:03:51 2008 OPTIONS IMPORT: --ifconfig/up options modified
Wed Aug 20 18:03:51 2008 OPTIONS IMPORT: route options modified
Wed Aug 20 18:03:51 2008 OPTIONS IMPORT: route-related options modified
Wed Aug 20 18:03:51 2008 TAP-WIN32 device [Ligação de Área Local 2] opened: \\.\Global\{12512EED-582F-4AEB-A642-65C117F951FD}.tap
Wed Aug 20 18:03:51 2008 TAP-Win32 Driver Version 9.4 
Wed Aug 20 18:03:51 2008 TAP-Win32 MTU=1500
Wed Aug 20 18:03:51 2008 Notified TAP-Win32 driver to set a DHCP IP/netmask of 192.168.2.2/255.255.255.0 on interface {12512EED-582F-4AEB-A642-65C117F951FD} [DHCP-serv: 192.168.2.0, lease-time: 31536000]
Wed Aug 20 18:03:51 2008 Successful ARP Flush on interface [18] {12512EED-582F-4AEB-A642-65C117F951FD}
Wed Aug 20 18:03:56 2008 TEST ROUTES: 0/0 succeeded len=1 ret=0 a=0 u/d=down
Wed Aug 20 18:03:56 2008 Route: Waiting for TUN/TAP interface to come up...
Wed Aug 20 18:04:01 2008 TEST ROUTES: 1/1 succeeded len=1 ret=1 a=0 u/d=up
Wed Aug 20 18:04:01 2008 C:\WINDOWS\system32\route.exe ADD 192.168.1.0 MASK 255.255.255.0 192.168.2.1
Wed Aug 20 18:04:01 2008 ROUTE: CreateIpForwardEntry succeeded with dwForwardMetric1=30 and dwForwardType=4
Wed Aug 20 18:04:01 2008 Route addition via IPAPI succeeded [adaptive]
Wed Aug 20 18:04:01 2008 Initialization Sequence Completed



Many thanks in advance

---

### Post by SpaceTeddy on 2008-08-20
can you please post your server and client config, as supply info about the server OS (the client is obviously windows). Furthermore - have you IP forwarding and nat enabled at your remote site or have you set the appropriate routes for packets to find their way back ?

hope we can figure this out :)

---

### Post by renegadeandy on 2008-08-21
Space teddy - i am having a very similar problem, client is windows, server is ubuntu:

[http://ubuntuforums.org/showthread.php?p=5634159#post5634159](http://ubuntuforums.org/showthread.php?p=5634159#post5634159)

---

### Post by SpaceTeddy on 2008-08-22
i don't think i can help much without the server and client config...

---

