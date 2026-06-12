---
title: "Help me fix my openvpn!"
date: 2008-09-15
forum: Networking &amp; Wireless
---

### Post by erinspice on 2008-09-15
OpenVPN worked perfectly in FC8. I installed 8.04 last week, and openvpn won't start anymore. Please help me fix it!  I love all other aspects of Ubuntu, and I really want to stick with it.  However, my job depends on my VPN access, so please help me fix this!

Here's what I get:

```
erin@erin-laptop:~/scans$ sudo /etc/init.d/openvpn start company
[sudo] password for erin: 
 * Starting virtual private network daemon.                                                                                                                                                 /etc/init.d/openvpn: 181: STATUS: not found
erin@erin-laptop:~/scans$ sudo openvpn --config /etc/openvpn/company.conf
Mon Sep 15 15:02:16 2008 OpenVPN 2.1_rc7 x86_64-pc-linux-gnu [SSL] [LZO2] [EPOLL] built on Jun 11 2008
Mon Sep 15 15:02:16 2008 /usr/bin/openssl-vulnkey -q -b 1024 -m <modulus omitted>
Mon Sep 15 15:02:17 2008 LZO compression initialized
Mon Sep 15 15:02:17 2008 Control Channel MTU parms [ L:1542 D:138 EF:38 EB:0 ET:0 EL:0 ]
Mon Sep 15 15:02:17 2008 Data Channel MTU parms [ L:1542 D:1450 EF:42 EB:135 ET:0 EL:0 AF:3/1 ]
Mon Sep 15 15:02:17 2008 Local Options hash (VER=V4): '41690919'
Mon Sep 15 15:02:17 2008 Expected Remote Options hash (VER=V4): '530fdded'
Mon Sep 15 15:02:17 2008 Socket Buffers: R=[122880->131072] S=[122880->131072]
Mon Sep 15 15:02:17 2008 UDPv4 link local: [undef]
Mon Sep 15 15:02:17 2008 UDPv4 link remote: xx.xx.xx.xx:1194
Mon Sep 15 15:02:17 2008 TLS: Initial packet from xx.xx.xx.xx:1194, sid=bfee439c 0d685361
Mon Sep 15 15:02:17 2008 VERIFY OK: depth=1, /C=US/ST=Alabama/L=Huntsville/O=Company/OU=Information_Technology/CN=gw.company.com/emailAddress=informationtechnology@company.com
Mon Sep 15 15:02:17 2008 VERIFY OK: nsCertType=SERVER
Mon Sep 15 15:02:17 2008 VERIFY OK: depth=0, /C=US/ST=Alabama/O=Company/CN=vpn.company.com/emailAddress=informationtechnology@company.com
Mon Sep 15 15:02:17 2008 Data Channel Encrypt: Cipher 'BF-CBC' initialized with 128 bit key
Mon Sep 15 15:02:17 2008 Data Channel Encrypt: Using 160 bit message hash 'SHA1' for HMAC authentication
Mon Sep 15 15:02:17 2008 Data Channel Decrypt: Cipher 'BF-CBC' initialized with 128 bit key
Mon Sep 15 15:02:17 2008 Data Channel Decrypt: Using 160 bit message hash 'SHA1' for HMAC authentication
Mon Sep 15 15:02:17 2008 Control Channel: TLSv1, cipher TLSv1/SSLv3 DHE-RSA-AES256-SHA, 1024 bit RSA
Mon Sep 15 15:02:17 2008 [vpn.company.com] Peer Connection Initiated with xx.xx.xx.xx:1194
Mon Sep 15 15:02:19 2008 SENT CONTROL [vpn.company.com]: 'PUSH_REQUEST' (status=1)
Mon Sep 15 15:02:19 2008 PUSH: Received control message: 'PUSH_REPLY,route xx.xx.xx.xx 255.255.0.0,route xx.xx.xx.xx 255.255.255.0,route xx.xx.xx.xx 255.255.0.0,route xx.xx.xx.xx 255.255.252.0,route xx.xx.xx.xx 255.255.255.255,route xx.xx.xx.xx 255.255.0.0,route xx.xx.xx.xx 255.255.252.0,route xx.xx.xx.xx 255.255.255.0,route xx.xx.xx.xx 255.255.255.255,dhcp-option DNS xx.xx.xx.xx,dhcp-option WINS xx.xx.xx.xx,route xx.xx.xx.xx 255.255.252.0,ping 10,ping-restart 120,ifconfig xx.xx.xx.xx xx.xx.xx.xx'
Mon Sep 15 15:02:19 2008 OPTIONS IMPORT: timers and/or timeouts modified
Mon Sep 15 15:02:19 2008 OPTIONS IMPORT: --ifconfig/up options modified
Mon Sep 15 15:02:19 2008 OPTIONS IMPORT: route options modified
Mon Sep 15 15:02:19 2008 OPTIONS IMPORT: --ip-win32 and/or --dhcp-option options modified
Mon Sep 15 15:02:19 2008 TUN/TAP device tun1 opened
Mon Sep 15 15:02:19 2008 TUN/TAP TX queue length set to 100
Mon Sep 15 15:02:19 2008 ifconfig tun1 xx.xx.xx.xx pointopoint xx.xx.xx.xx mtu 1500


Mon Sep 15 15:02:19 2008 route add -net xx.xx.xx.0 netmask 255.255.252.0 gw xx.xx.xx.xx
SIOCADDRT: File exists
Mon Sep 15 15:02:19 2008 ERROR: Linux route add command failed: shell command exited with error status: 7

# repeated a bunch of times

Mon Sep 15 15:02:19 2008 Initialization Sequence Completed
Mon Sep 15 15:02:32 2008 event_wait : Interrupted system call (code=4)
Mon Sep 15 15:02:32 2008 TCP/UDP: Closing socket
Mon Sep 15 15:02:32 2008 Closing TUN/TAP interface
Mon Sep 15 15:02:32 2008 SIGINT[hard,] received, process exiting
erin@erin-laptop:~/scans$ 

```

---

### Post by undertakingyou on 2008-09-17
do you maintain this VPN?  It seems odd to have a gateway of 255.255.252.0 on the added routes.  Is that supposed to be that way?  I can't think of why you wouldn't want it to be 255.255.255.0
If the add routes are in your client.conf edit them.  If they are in your server.conf you could edit it there or have whoever maintains it do it for you.
Just a thought.

---

### Post by erinspice on 2008-09-17
Yes, I maintain it, but I haven't set anything up since I installed Ubuntu. All I did was copy over my company.conf, certs, and keys and start openvpn.  I don't have a "server.conf" on my  machine.

---

