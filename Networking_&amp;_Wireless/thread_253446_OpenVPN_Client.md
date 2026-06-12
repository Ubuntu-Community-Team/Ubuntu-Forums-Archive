---
title: "OpenVPN Client"
date: 2006-09-08
forum: Networking &amp; Wireless
---

### Post by kw1502 on 2006-09-08
I’m a new Dapper Drake user. I’m trying to setup an OpenVPN client on Ubuntu using certificates. I’ve installed the OpenVPN package but have not changed any other system configuration files and/or parameters. My OpenVPN server and client configuration files are the same ones that work under Windows XP. Is there sometime else I need to do to make this work under Dapper? I’ve attached the terminal output from an attempt to establish the VPN. Any suggestions would be greatly appreciated.

ken@ubuntu:~$ cd /etc/openvpn
ken@ubuntu:/etc/openvpn$ sudo openvpn --config ipcop.ovpn
Wed Sep 6 23:14:01 2006 OpenVPN 2.0.6 i486-pc-linux-gnu [SSL] [LZO] [EPOLL] bui lt on Apr 10 2006
Wed Sep 6 23:14:01 2006 IMPORTANT: OpenVPN's default port number is now 1194, b ased on an official port number assignment by IANA. OpenVPN 2.0-beta16 and earl ier used 5000 as the default port.
Enter Private Key Password:
Wed Sep 6 23:14:08 2006 LZO compression initialized
Wed Sep 6 23:14:08 2006 WARNING: normally if you use --mssfix and/or --fragment , you should also set --tun-mtu 1500 (currently it is 1400)
Wed Sep 6 23:14:08 2006 Control Channel MTU parms [ L:1442 D:138 EF:38 EB:0 ET: 0 EL:0 ]
Wed Sep 6 23:14:08 2006 Data Channel MTU parms [ L:1442 D:1442 EF:42 EB:135 ET: 0 EL:0 AF:3/1 ]
Wed Sep 6 23:14:08 2006 Local Options hash (VER=V4): 'a6ae7d69'
Wed Sep 6 23:14:08 2006 Expected Remote Options hash (VER=V4): '006a55ce'
Wed Sep 6 23:14:08 2006 UDPv4 link local (bound): [undef]:1194
Wed Sep 6 23:14:08 2006 UDPv4 link remote: 192.168.1.1:1194
Wed Sep 6 23:15:08 2006 TLS Error: TLS key negotiation failed to occur within 60 seconds (check your network connectivity)
Wed Sep 6 23:15:08 2006 TLS Error: TLS handshake failed
Wed Sep 6 23:15:08 2006 TCP/UDP: Closing socket
Wed Sep 6 23:15:08 2006 SIGUSR1[soft,tls-error] received, process restarting
Wed Sep 6 23:15:08 2006 Restart pause, 2 second(s)
Wed Sep 6 23:15:10 2006 IMPORTANT: OpenVPN's default port number is now 1194, based on an official port number assignment by IANA. OpenVPN 2.0-beta16 and earlier used 5000 as the default port.
Wed Sep 6 23:15:10 2006 LZO compression initialized
Wed Sep 6 23:15:10 2006 WARNING: normally if you use --mssfix and/or --fragment, you should also set --tun-mtu 1500 (currently it is 1400)
Wed Sep 6 23:15:10 2006 Control Channel MTU parms [ L:1442 D:138 EF:38 EB:0 ET:0 EL:0 ]
Wed Sep 6 23:15:10 2006 Data Channel MTU parms [ L:1442 D:1442 EF:42 EB:135 ET:0 EL:0 AF:3/1 ]
Wed Sep 6 23:15:10 2006 Local Options hash (VER=V4): 'a6ae7d69'
Wed Sep 6 23:15:10 2006 Expected Remote Options hash (VER=V4): '006a55ce'
Wed Sep 6 23:15:10 2006 UDPv4 link local (bound): [undef]:1194
Wed Sep 6 23:15:10 2006 UDPv4 link remote: 192.168.1.1:1194
Wed Sep 6 23:16:10 2006 TLS Error: TLS key negotiation failed to occur within 60 seconds (check your network connectivity)
Wed Sep 6 23:16:10 2006 TLS Error: TLS handshake failed
Wed Sep 6 23:16:10 2006 TCP/UDP: Closing socket
Wed Sep 6 23:16:10 2006 SIGUSR1[soft,tls-error] received, process restarting
Wed Sep 6 23:16:10 2006 Restart pause, 2 second(s)

---

### Post by tbonius on 2006-09-08
Can you post your OpenVPN client config?

T

---

### Post by kw1502 on 2006-09-08
Here is more detail on my setup:

I’m a new Ubuntu (Dapper Drake) user. I’m trying to setup an OpenVPN client on Ubuntu using certificates. I’ve installed the OpenVPN package but have not changed any other system configuration files and/or parameters. My OpenVPN server and client configuration files are the same ones that work under Windows XP. I’m including the system messages and the configuration files from the server and client side of the connection. Any suggestions on how to make this work be greatly appreciated.

#OpenVPN Server conf
daemon openvpnserver
writepid /var/run/openvpn.pid
#DAN prepare ZERINA for listening on blue and orange
;local ool-18bb255a.dyn.optonline.net
dev tun
tun-mtu 1400
proto udp
port 1194
tls-server
ca /var/ipcop/ovpn/ca/cacert.pem
cert /var/ipcop/ovpn/certs/servercert.pem
key /var/ipcop/ovpn/certs/serverkey.pem
dh /var/ipcop/ovpn/ca/dh1024.pem
server 10.217.53.0 255.255.255.0
push "route 192.168.0.0 255.255.255.0"
keepalive 10 60
status-version 1
status /var/ipcop/ovpn/server.log 30
cipher BF-CBC
comp-lzo
push "redirect-gateway def1"
push "dhcp-option DNS 192.168.0.1"
max-clients 100
tls-verify /var/ipcop/ovpn/verify
crl-verify /var/ipcop/ovpn/crls/cacrl.pem
user nobody
group nobody
persist-key
persist-tun
verb 3

#OpenVPN Server conf
tls-client
client
dev tun
proto udp
tun-mtu 1400
remote 192.168.1.1 1194
pkcs12 toshiba.p12
cipher BF-CBC
comp-lzo
verb 3
ns-cert-type server

Server Log:
23:14:04 openvpnserver MULTI: multi_create_instance called
23:14:04 openvpnserver 192.168.1.200:1194 Re-using SSL/TLS context
23:14:04 openvpnserver 192.168.1.200:1194 LZO compression initialized
23:14:04 openvpnserver 192.168.1.200:1194 WARNING: normally if you use --mssfix and/or --fragment, you should also set --tun-mtu 1500 (currently it is 1400)
23:14:04 openvpnserver 192.168.1.200:1194 Control Channel MTU parms [ L:1442 D:138 EF:38 EB:0 ET:0 EL:0 ]
23:14:04 openvpnserver 192.168.1.200:1194 Data Channel MTU parms [ L:1442 D:1442 EF:42 EB:135 ET:0 EL:0 AF:3/1 ]
23:14:04 openvpnserver 192.168.1.200:1194 Local Options hash (VER=V4): '006a55ce'
23:14:04 openvpnserver 192.168.1.200:1194 Expected Remote Options hash (VER=V4): 'a6ae7d69'
23:14:04 openvpnserver 192.168.1.200:1194 TLS: Initial packet from 192.168.1.200:1194, sid=0e05be1f aa2d8e2b
23:15:04 openvpnserver 192.168.1.200:1194 TLS Error: TLS key negotiation failed to occur within 60 seconds (check your network connectivity)
23:15:04 openvpnserver 192.168.1.200:1194 TLS Error: TLS handshake failed
23:15:04 openvpnserver 192.168.1.200:1194 SIGUSR1[soft,tls-error] received, client-instance restarting
23:15:05 openvpnserver MULTI: multi_create_instance called
23:15:05 openvpnserver 192.168.1.200:1194 Re-using SSL/TLS context
23:15:05 openvpnserver 192.168.1.200:1194 LZO compression initialized
23:15:05 openvpnserver 192.168.1.200:1194 WARNING: normally if you use --mssfix and/or --fragment, you should also set --tun-mtu 1500 (currently it is 1400)
23:15:05 openvpnserver 192.168.1.200:1194 Control Channel MTU parms [ L:1442 D:138 EF:38 EB:0 ET:0 EL:0 ]
23:15:05 openvpnserver 192.168.1.200:1194 Data Channel MTU parms [ L:1442 D:1442 EF:42 EB:135 ET:0 EL:0 AF:3/1 ]
23:15:05 openvpnserver 192.168.1.200:1194 Local Options hash (VER=V4): '006a55ce'
23:15:05 openvpnserver 192.168.1.200:1194 Expected Remote Options hash (VER=V4): 'a6ae7d69'
23:15:05 openvpnserver 192.168.1.200:1194 TLS: Initial packet from 192.168.1.200:1194, sid=b5e2a987 3c5debf1
23:16:05 openvpnserver 192.168.1.200:1194 TLS Error: TLS key negotiation failed to occur within 60 seconds (check your network connectivity)
23:16:05 openvpnserver 192.168.1.200:1194 TLS Error: TLS handshake failed
23:16:05 openvpnserver 192.168.1.200:1194 SIGUSR1[soft,tls-error] received, client-instance restarting
23:16:07 openvpnserver MULTI: multi_create_instance called
23:16:07 openvpnserver 192.168.1.200:1194 Re-using SSL/TLS context
23:16:07 openvpnserver 192.168.1.200:1194 LZO compression initialized
23:16:07 openvpnserver 192.168.1.200:1194 WARNING: normally if you use --mssfix and/or --fragment, you should also set --tun-mtu 1500 (currently it is 1400)
23:16:07 openvpnserver 192.168.1.200:1194 Control Channel MTU parms [ L:1442 D:138 EF:38 EB:0 ET:0 EL:0 ]
23:16:07 openvpnserver 192.168.1.200:1194 Data Channel MTU parms [ L:1442 D:1442 EF:42 EB:135 ET:0 EL:0 AF:3/1 ]
23:16:07 openvpnserver 192.168.1.200:1194 Local Options hash (VER=V4): '006a55ce'
23:16:07 openvpnserver 192.168.1.200:1194 Expected Remote Options hash (VER=V4): 'a6ae7d69'
23:16:07 openvpnserver 192.168.1.200:1194 TLS: Initial packet from 192.168.1.200:1194, sid=1c34b2c3 2a1ae578
23:17:07 openvpnserver 192.168.1.200:1194 TLS Error: TLS key negotiation failed to occur within 60 seconds (check your network connectivity)
23:17:07 openvpnserver 192.168.1.200:1194 TLS Error: TLS handshake failed
23:17:07 openvpnserver 192.168.1.200:1194 SIGUSR1[soft,tls-error] received, client-instance restarting
23:17:10 openvpnserver MULTI: multi_create_instance called
23:17:10 openvpnserver 192.168.1.200:1194 Re-using SSL/TLS context
23:17:10 openvpnserver 192.168.1.200:1194 LZO compression initialized
23:17:10 openvpnserver 192.168.1.200:1194 WARNING: normally if you use --mssfix and/or --fragment, you should also set --tun-mtu 1500 (currently it is 1400)
23:17:10 openvpnserver 192.168.1.200:1194 Control Channel MTU parms [ L:1442 D:138 EF:38 EB:0 ET:0 EL:0 ]
23:17:10 openvpnserver 192.168.1.200:1194 Data Channel MTU parms [ L:1442 D:1442 EF:42 EB:135 ET:0 EL:0 AF:3/1 ]
23:17:10 openvpnserver 192.168.1.200:1194 Local Options hash (VER=V4): '006a55ce'
23:17:10 openvpnserver 192.168.1.200:1194 Expected Remote Options hash (VER=V4): 'a6ae7d69'
23:17:10 openvpnserver 192.168.1.200:1194 TLS: Initial packet from 192.168.1.200:1194, sid=49390270 47996eeb
23:18:10 openvpnserver 192.168.1.200:1194 TLS Error: TLS key negotiation failed to occur within 60 seconds (check your network connectivity)
23:18:10 openvpnserver 192.168.1.200:1194 TLS Error: TLS handshake failed
23:18:10 openvpnserver 192.168.1.200:1194 SIGUSR1[soft,tls-error] received, client-instance restarting
23:18:12 openvpnserver MULTI: multi_create_instance called
23:18:12 openvpnserver 192.168.1.200:1194 Re-using SSL/TLS context
23:18:12 openvpnserver 192.168.1.200:1194 LZO compression initialized
23:18:12 openvpnserver 192.168.1.200:1194 WARNING: normally if you use --mssfix and/or --fragment, you should also set --tun-mtu 1500 (currently it is 1400)
23:18:12 openvpnserver 192.168.1.200:1194 Control Channel MTU parms [ L:1442 D:138 EF:38 EB:0 ET:0 EL:0 ]
23:18:12 openvpnserver 192.168.1.200:1194 Data Channel MTU parms [ L:1442 D:1442 EF:42 EB:135 ET:0 EL:0 AF:3/1 ]
23:18:12 openvpnserver 192.168.1.200:1194 Local Options hash (VER=V4): '006a55ce'
23:18:12 openvpnserver 192.168.1.200:1194 Expected Remote Options hash (VER=V4): 'a6ae7d69'
23:18:12 openvpnserver 192.168.1.200:1194 TLS: Initial packet from 192.168.1.200:1194, sid=35b0d9b3 58d035eb
23:19:12 openvpnserver 192.168.1.200:1194 TLS Error: TLS key negotiation failed to occur within 60 seconds (check your network connectivity)
23:19:12 openvpnserver 192.168.1.200:1194 TLS Error: TLS handshake failed
23:19:12 openvpnserver 192.168.1.200:1194 SIGUSR1[soft,tls-error] received, client-instance restarting
23:19:13 openvpnserver MULTI: multi_create_instance called
23:19:13 openvpnserver 192.168.1.200:1194 Re-using SSL/TLS context
23:19:13 openvpnserver 192.168.1.200:1194 LZO compression initialized
23:19:13 openvpnserver 192.168.1.200:1194 WARNING: normally if you use --mssfix and/or --fragment, you should also set --tun-mtu 1500 (currently it is 1400)
23:19:13 openvpnserver 192.168.1.200:1194 Control Channel MTU parms [ L:1442 D:138 EF:38 EB:0 ET:0 EL:0 ]
23:19:13 openvpnserver 192.168.1.200:1194 Data Channel MTU parms [ L:1442 D:1442 EF:42 EB:135 ET:0 EL:0 AF:3/1 ]
23:19:13 openvpnserver 192.168.1.200:1194 Local Options hash (VER=V4): '006a55ce'
23:19:13 openvpnserver 192.168.1.200:1194 Expected Remote Options hash (VER=V4): 'a6ae7d69'
23:19:13 openvpnserver 192.168.1.200:1194 TLS: Initial packet from 192.168.1.200:1194, sid=eec6329f 4740cd5a
23:20:13 openvpnserver 192.168.1.200:1194 TLS Error: TLS key negotiation failed to occur within 60 seconds (check your network connectivity)
23:20:13 openvpnserver 192.168.1.200:1194 TLS Error: TLS handshake failed
23:20:13 openvpnserver 192.168.1.200:1194 SIGUSR1[soft,tls-error] received, client-instance restarting
23:20:16 openvpnserver MULTI: multi_create_instance called
23:20:16 openvpnserver 192.168.1.200:1194 Re-using SSL/TLS context
23:20:16 openvpnserver 192.168.1.200:1194 LZO compression initialized
23:20:16 openvpnserver 192.168.1.200:1194 WARNING: normally if you use --mssfix and/or --fragment, you should also set --tun-mtu 1500 (currently it is 1400)
23:20:16 openvpnserver 192.168.1.200:1194 Control Channel MTU parms [ L:1442 D:138 EF:38 EB:0 ET:0 EL:0 ]
23:20:16 openvpnserver 192.168.1.200:1194 Data Channel MTU parms [ L:1442 D:1442 EF:42 EB:135 ET:0 EL:0 AF:3/1 ]
23:20:16 openvpnserver 192.168.1.200:1194 Local Options hash (VER=V4): '006a55ce'
23:20:16 openvpnserver 192.168.1.200:1194 Expected Remote Options hash (VER=V4): 'a6ae7d69'
23:20:16 openvpnserver 192.168.1.200:1194 TLS: Initial packet from 192.168.1.200:1194, sid=5a4a871d f47258b8
23:21:17 openvpnserver 192.168.1.200:1194 TLS Error: TLS key negotiation failed to occur within 60 seconds (check your network connectivity)
23:21:17 openvpnserver 192.168.1.200:1194 TLS Error: TLS handshake failed
23:21:17 openvpnserver 192.168.1.200:1194 SIGUSR1[soft,tls-error] received, client-instance restarting
23:21:18 openvpnserver MULTI: multi_create_instance called
23:21:18 openvpnserver 192.168.1.200:1194 Re-using SSL/TLS context
23:21:18 openvpnserver 192.168.1.200:1194 LZO compression initialized
23:21:18 openvpnserver 192.168.1.200:1194 WARNING: normally if you use --mssfix and/or --fragment, you should also set --tun-mtu 1500 (currently it is 1400)
23:21:18 openvpnserver 192.168.1.200:1194 Control Channel MTU parms [ L:1442 D:138 EF:38 EB:0 ET:0 EL:0 ]
23:21:18 openvpnserver 192.168.1.200:1194 Data Channel MTU parms [ L:1442 D:1442 EF:42 EB:135 ET:0 EL:0 AF:3/1 ]
23:21:18 openvpnserver 192.168.1.200:1194 Local Options hash (VER=V4): '006a55ce'
23:21:18 openvpnserver 192.168.1.200:1194 Expected Remote Options hash (VER=V4): 'a6ae7d69'
23:21:18 openvpnserver 192.168.1.200:1194 TLS: Initial packet from 192.168.1.200:1194, sid=ee8a397c f7590c24
23:22:18 openvpnserver 192.168.1.200:1194 TLS Error: TLS key negotiation failed to occur within 60 seconds (check your network connectivity)
23:22:18 openvpnserver 192.168.1.200:1194 TLS Error: TLS handshake failed
23:22:18 openvpnserver 192.168.1.200:1194 SIGUSR1[soft,tls-error] received, client-instance restarting
23:22:20 openvpnserver MULTI: multi_create_instance called
23:22:20 openvpnserver 192.168.1.200:1194 Re-using SSL/TLS context
23:22:20 openvpnserver 192.168.1.200:1194 LZO compression initialized
23:22:20 openvpnserver 192.168.1.200:1194 WARNING: normally if you use --mssfix and/or --fragment, you should also set --tun-mtu 1500 (currently it is 1400)
23:22:20 openvpnserver 192.168.1.200:1194 Control Channel MTU parms [ L:1442 D:138 EF:38 EB:0 ET:0 EL:0 ]
23:22:20 openvpnserver 192.168.1.200:1194 Data Channel MTU parms [ L:1442 D:1442 EF:42 EB:135 ET:0 EL:0 AF:3/1 ]
23:22:20 openvpnserver 192.168.1.200:1194 Local Options hash (VER=V4): '006a55ce'
23:22:20 openvpnserver 192.168.1.200:1194 Expected Remote Options hash (VER=V4): 'a6ae7d69'
23:22:20 openvpnserver 192.168.1.200:1194 TLS: Initial packet from 192.168.1.200:1194, sid=32e3efe5 22cda689
23:23:20 openvpnserver 192.168.1.200:1194 TLS Error: TLS key negotiation failed to occur within 60 seconds (check your network connectivity)
23:23:20 openvpnserver 192.168.1.200:1194 TLS Error: TLS handshake failed
23:23:20 openvpnserver 192.168.1.200:1194 SIGUSR1[soft,tls-error] received, client-instance restarting

Client Log:
ken@ubuntu:/etc/openvpn$ sudo openvpn --config ipcop.ovpn
Wed Sep 6 23:14:01 2006 OpenVPN 2.0.6 i486-pc-linux-gnu [SSL] [LZO] [EPOLL] bui lt on Apr 10 2006
Wed Sep 6 23:14:01 2006 IMPORTANT: OpenVPN's default port number is now 1194, b ased on an official port number assignment by IANA. OpenVPN 2.0-beta16 and earl ier used 5000 as the default port.
Enter Private Key Password:
Wed Sep 6 23:14:08 2006 LZO compression initialized
Wed Sep 6 23:14:08 2006 WARNING: normally if you use --mssfix and/or --fragment , you should also set --tun-mtu 1500 (currently it is 1400)
Wed Sep 6 23:14:08 2006 Control Channel MTU parms [ L:1442 D:138 EF:38 EB:0 ET: 0 EL:0 ]
Wed Sep 6 23:14:08 2006 Data Channel MTU parms [ L:1442 D:1442 EF:42 EB:135 ET: 0 EL:0 AF:3/1 ]
Wed Sep 6 23:14:08 2006 Local Options hash (VER=V4): 'a6ae7d69'
Wed Sep 6 23:14:08 2006 Expected Remote Options hash (VER=V4): '006a55ce'
Wed Sep 6 23:14:08 2006 UDPv4 link local (bound): [undef]:1194
Wed Sep 6 23:14:08 2006 UDPv4 link remote: 192.168.1.1:1194
Wed Sep 6 23:15:08 2006 TLS Error: TLS key negotiation failed to occur within 60 seconds (check your network connectivity)
Wed Sep 6 23:15:08 2006 TLS Error: TLS handshake failed
Wed Sep 6 23:15:08 2006 TCP/UDP: Closing socket
Wed Sep 6 23:15:08 2006 SIGUSR1[soft,tls-error] received, process restarting
Wed Sep 6 23:15:08 2006 Restart pause, 2 second(s)
Wed Sep 6 23:15:10 2006 IMPORTANT: OpenVPN's default port number is now 1194, based on an official port number assignment by IANA. OpenVPN 2.0-beta16 and earlier used 5000 as the default port.
Wed Sep 6 23:15:10 2006 LZO compression initialized
Wed Sep 6 23:15:10 2006 WARNING: normally if you use --mssfix and/or --fragment, you should also set --tun-mtu 1500 (currently it is 1400)
Wed Sep 6 23:15:10 2006 Control Channel MTU parms [ L:1442 D:138 EF:38 EB:0 ET:0 EL:0 ]
Wed Sep 6 23:15:10 2006 Data Channel MTU parms [ L:1442 D:1442 EF:42 EB:135 ET:0 EL:0 AF:3/1 ]
Wed Sep 6 23:15:10 2006 Local Options hash (VER=V4): 'a6ae7d69'
Wed Sep 6 23:15:10 2006 Expected Remote Options hash (VER=V4): '006a55ce'
Wed Sep 6 23:15:10 2006 UDPv4 link local (bound): [undef]:1194
Wed Sep 6 23:15:10 2006 UDPv4 link remote: 192.168.1.1:1194
Wed Sep 6 23:16:10 2006 TLS Error: TLS key negotiation failed to occur within 60 seconds (check your network connectivity)
Wed Sep 6 23:16:10 2006 TLS Error: TLS handshake failed
Wed Sep 6 23:16:10 2006 TCP/UDP: Closing socket
Wed Sep 6 23:16:10 2006 SIGUSR1[soft,tls-error] received, process restarting
Wed Sep 6 23:16:10 2006 Restart pause, 2 second(s)

---

### Post by kw1502 on 2006-10-26
Problem solved. I had an IPSec based VPN running on the same server protecting the same subnet. When I disabled IPSec everything "just worked".

---

