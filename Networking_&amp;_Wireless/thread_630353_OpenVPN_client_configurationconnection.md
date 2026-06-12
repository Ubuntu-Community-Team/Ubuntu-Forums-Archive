---
title: "OpenVPN client configuration/connection"
date: 2007-12-03
forum: Networking &amp; Wireless
---

### Post by MrDetermination on 2007-12-03
Novice Linux guy here...

I have an OpenVPN server running on DD-WRT.  The Windows OpenVPN GUI connects to it just fine with the following config:

```
client

dev tap

proto udp

remote my.dynamic-ip.org 9876

resolv-retry infinite

nobind

persist-key

persist-tun

ca ca.crt

cert laptop.crt

key laptop.key

ns-cert-type server

comp-lzo

verb 3

route-gateway 192.168.0.1

redirect-gateway
```

The VPN login failed because the VPN program received an invalid configuration from the VPN server.[/quote]

I've tried x.509 with and without password authentication as the auth type.  When I created the cert/key pairs I created a "challenge" pw I am not required to use to connect with from Windows.  When I try to connect with the "with password" connection type I am asked for a password and certificate password.  I have tried both connection types with every possible combination of passwords but had no luck.

The best case scenario always results in the following:

*Could not start the VPN connection 'Home' because the VPN server did not return an adequate network configuration.*

I have tried the GUI config manually and via importing a manual config.  The paths to the certificates is absolutely correct.

---

### Post by MrDetermination on 2007-12-07
bump

---

### Post by secure bit on 2007-12-15
can you post the clients log here ?

---

### Post by justifiedandancient on 2008-07-02
Well I have a similar problem to this. I am trying to connect to my work's VPN server running on whatever it runs. I a have a perfectly working Windows XP client and I have copie dthe configuration file to my Linux machine. The windows specific dev-node line has been commented out. I then try to connect by issuing the following command:

sudo openvpn config-file

This seems to repeatedly attempt to establish a connection but fail for some reason, here is part of the log:

[FONT="Courier New"]Wed Jul  2 12:09:32 2008 Restart pause, 5 second(s)
Wed Jul  2 12:09:37 2008 WARNING: No server certificate verification method has been enabled.  See [http://openvpn.net/howto.html#mitm](http://openvpn.net/howto.html#mitm) for more info.
Wed Jul  2 12:09:37 2008 Re-using SSL/TLS context
Wed Jul  2 12:09:37 2008 LZO compression initialized
Wed Jul  2 12:09:37 2008 Control Channel MTU parms [ L:1544 D:140 EF:40 EB:0 ET:0 EL:0 ]
Wed Jul  2 12:09:37 2008 Data Channel MTU parms [ L:1544 D:1450 EF:44 EB:135 ET:0 EL:0 AF:3/1 ]
Wed Jul  2 12:09:37 2008 Local Options hash (VER=V4): '69109d17'
Wed Jul  2 12:09:37 2008 Expected Remote Options hash (VER=V4): 'c0103fa8'
Wed Jul  2 12:09:37 2008 Attempting to establish TCP connection with 195.188.250.62:443 [nonblock]
Wed Jul  2 12:09:38 2008 TCP connection established with 195.188.250.62:443
Wed Jul  2 12:09:38 2008 Socket Buffers: R=[87380->131072] S=[16384->131072]
Wed Jul  2 12:09:38 2008 TCPv4_CLIENT link local: [undef]
Wed Jul  2 12:09:38 2008 TCPv4_CLIENT link remote: 195.188.250.62:443
Wed Jul  2 12:09:38 2008 TLS: Initial packet from 195.188.250.62:443, sid=50a5f194 a2a5c81b
Wed Jul  2 12:09:38 2008 VERIFY OK: depth=1, /C=DE/ST=Hessen/L=Frankfurt/O=IS.Teledata_AG/CN=IS.Teledata_Mail_CA
Wed Jul  2 12:09:38 2008 VERIFY OK: depth=0, /C=UK/ST=England/L=Cheltenham/O=Interactive_Data_Managed_Solutions_Ltd/CN=FWall.is-uk.com
Wed Jul  2 12:09:39 2008 WARNING: 'link-mtu' is used inconsistently, local='link-mtu 1544', remote='link-mtu 1526'
Wed Jul  2 12:09:39 2008 WARNING: 'tun-mtu' is used inconsistently, local='tun-mtu 1500', remote='tun-mtu 1482'
Wed Jul  2 12:09:39 2008 Data Channel Encrypt: Cipher 'BF-CBC' initialized with 128 bit key
Wed Jul  2 12:09:39 2008 Data Channel Encrypt: Using 160 bit message hash 'SHA1' for HMAC authentication
Wed Jul  2 12:09:39 2008 Data Channel Decrypt: Cipher 'BF-CBC' initialized with 128 bit key
Wed Jul  2 12:09:39 2008 Data Channel Decrypt: Using 160 bit message hash 'SHA1' for HMAC authentication
Wed Jul  2 12:09:39 2008 Control Channel: TLSv1, cipher TLSv1/SSLv3 DHE-RSA-AES256-SHA, 1024 bit RSA
Wed Jul  2 12:09:39 2008 [FWall.is-uk.com] Peer Connection Initiated with 195.188.250.62:443
Wed Jul  2 12:09:40 2008 SENT CONTROL [FWall.is-uk.com]: 'PUSH_REQUEST' (status=1)
Wed Jul  2 12:09:40 2008 PUSH: Received control message: 'PUSH_REPLY,route 10.44.2.1,ping 10,ping-restart 120,route 195.188.250.32 255.255.255.240,route 10.44.1.0 255.255.255.0,ifconfig 10.44.2.14 10.44.2.13'
Wed Jul  2 12:09:40 2008 OPTIONS IMPORT: timers and/or timeouts modified
Wed Jul  2 12:09:40 2008 OPTIONS IMPORT: --ifconfig/up options modified
Wed Jul  2 12:09:40 2008 OPTIONS IMPORT: route options modified
Wed Jul  2 12:09:40 2008 Preserving previous TUN/TAP instance: tun0
Wed Jul  2 12:09:40 2008 Initialization Sequence Completed
Wed Jul  2 12:09:47 2008 Connection reset, restarting [0]
Wed Jul  2 12:09:47 2008 TCP/UDP: Closing socket
Wed Jul  2 12:09:47 2008 SIGUSR1[soft,connection-reset] received, process restarting
Wed Jul  2 12:09:47 2008 Restart pause, 5 second(s)
[/FONT]

Any ideas what I am doing wrong or have failed to do?

---

### Post by justifiedandancient on 2008-07-02
Now I am answering my own question! It seems as though openvpn couldn't handle concurrent connections from both Windows XP and my Linux machine. They are both behind a router with NAT & firewall. Anyway, when I disconnected the openvpn client on Windows XP the openvpn config-file just worked.

---

