---
title: "Bridged OpenVPN Connection-how to create secure vpn connection with Ubuntu 14"
date: 2015-02-07
forum: Networking &amp; Wireless
---

### Post by greatlakes09 on 2015-02-07
Looking at my syslogs on the client and server, it appears they are connecting on openvpn -restart. But I am unable to figure out how to make a secure VPN Connection. I am trying to use the Connection Manager, but it times out. I am not even sure you can connect that way, but that is what I have tried (VPN Connections -> Configure VPN).


My server log looks like:
eb  7 11:56:54 a9000 ovpn-server[1390]: XX.99.XXX.54:60771 Data Channel Encrypt: Cipher 'BF-CBC' initialized with 128 bit key
Feb  7 11:56:54 a9000 ovpn-server[1390]: XX.99.XXX.54:60771 Data Channel Encrypt: Using 160 bit message hash 'SHA1' for HMAC authentication
Feb  7 11:56:54 a9000 ovpn-server[1390]: XX.99.XXX.54:60771 Data Channel Decrypt: Cipher 'BF-CBC' initialized with 128 bit key
Feb  7 11:56:54 a9000 ovpn-server[1390]: XX.99.XXX.54:60771 Data Channel Decrypt: Using 160 bit message hash 'SHA1' for HMAC authentication
Feb  7 11:56:54 a9000 ovpn-server[1390]: XX.99.XXX.54:60771 Control Channel: TLSv1, cipher TLSv1/SSLv3 DHE-RSA-AES256-SHA, 2048 bit RSA
Feb  7 11:56:54 a9000 ovpn-server[1390]: XX.99.XXX.54:60771 [client] Peer Connection Initiated with [AF_INET]XX.99.XXX.54:60771
Feb  7 11:56:54 a9000 ovpn-server[1390]: MULTI: new connection by client 'client' will cause previous active sessions by this client to be dropped.  Remember to use the --duplicate-cn option if you want multiple clients using the same certificate or username to concurrently connect.
Feb  7 11:56:54 a9000 ovpn-server[1390]: MULTI_sva: pool returned IPv4=192.168.1.100, IPv6=(Not enabled)
Feb  7 11:56:56 a9000 ovpn-server[1390]: client/XX.99.XXX.54:60771 PUSH: Received control message: 'PUSH_REQUEST'
Feb  7 11:56:56 a9000 ovpn-server[1390]: client/XX.99.XXX.54:60771 send_push_reply(): safe_cap=940
Feb  7 11:56:56 a9000 ovpn-server[1390]: client/XX.99.XXX.54:60771 SENT CONTROL [client]: 'PUSH_REPLY,route-gateway 192.168.1.107,ping 10,ping-restart 120,ifconfig 192.168.1.100 255.255.255.0' (status=1)
Feb  7 11:57:04 a9000 ovpn-server[1390]: client/XX.99.XXX.54:60771 MULTI: Learn: 9a:51:db:08:a6:e2 -> client/XX.99.XXX.54:60771


and the client looks like:
Feb  7 11:57:44 K55A nm-openvpn[6161]: Control Channel Authentication: using '/etc/openvpn/ta.key' as a OpenVPN static key file
Feb  7 11:57:44 K55A nm-openvpn[6161]: UDPv4 link local: [undef]
Feb  7 11:57:44 K55A nm-openvpn[6161]: UDPv4 link remote: [AF_INET]192.168.1.100:1194
Feb  7 11:58:24 K55A NetworkManager[1189]: <warn> VPN connection 'VPN connection 1' (IP Config Get) timeout exceeded.
Feb  7 11:58:24 K55A nm-openvpn[6161]: SIGTERM[hard,] received, process exiting
Feb  7 11:58:29 K55A NetworkManager[1189]: <info> VPN service 'openvpn' disappeared
Feb  7 12:03:53 K55A NetworkManager[1189]: <info> Starting VPN service 'openvpn'...
Feb  7 12:03:53 K55A NetworkManager[1189]: <info> VPN service 'openvpn' started (org.freedesktop.NetworkManager.openvpn), PID 6207
Feb  7 12:03:53 K55A NetworkManager[1189]: <info> VPN service 'openvpn' appeared; activating connections
Feb  7 12:03:53 K55A NetworkManager[1189]: <info> VPN plugin state changed: starting (3)
Feb  7 12:03:53 K55A NetworkManager[1189]: <info> VPN connection 'VPN connection 1' (Connect) reply received.
Feb  7 12:03:53 K55A nm-openvpn[6210]: OpenVPN 2.3.2 x86_64-pc-linux-gnu [SSL (OpenSSL)] [LZO] [EPOLL] [PKCS11] [eurephia] [MH] [IPv6] built on Dec  1 2014
Feb  7 12:03:53 K55A nm-openvpn[6210]: WARNING: No server certificate verification method has been enabled.  See [http://openvpn.net/howto.html#mitm](http://openvpn.net/howto.html#mitm) for more info.
Feb  7 12:03:53 K55A nm-openvpn[6210]: NOTE: the current --script-security setting may allow this configuration to call user-defined scripts
Feb  7 12:03:53 K55A nm-openvpn[6210]: WARNING: file '/etc/openvpn/client.key' is group or others accessible
Feb  7 12:03:53 K55A nm-openvpn[6210]: WARNING: file '/etc/openvpn/ta.key' is group or others accessible
Feb  7 12:03:53 K55A nm-openvpn[6210]: Control Channel Authentication: using '/etc/openvpn/ta.key' as a OpenVPN static key file
Feb  7 12:03:53 K55A nm-openvpn[6210]: UDPv4 link local: [undef]
Feb  7 12:03:53 K55A nm-openvpn[6210]: UDPv4 link remote: [AF_INET]192.168.1.254:1194




Any help is appreciated!

---

### Post by greatlakes09 on 2015-02-12
so I went back, uninstalled everything, and just set up a non-bridged vpn following the steps outlined here: [http://openvpn.net/index.php/open-source/documentation/howto.html#install](http://openvpn.net/index.php/open-source/documentation/howto.html#install) . My connection is successful returning "Initialization Sequence Completed" on both the client and server.  I am also able to ping 10.8.0.1. But now what? How can I send files from the client to the server and use the servers internet connection when I am on an open wifi (this is why I setup my bridged vpn before).  I have tried using the network manager to establish the connection, tried using the access manager on openvpn.net (ubuntu said the package was unsafe .. it didn't work regardless). I have also searched high and low for what to do next.

Your help is appreciated!  This is day 10000000 of trying to figure this out. Thanks!

---

### Post by greatlakes09 on 2015-02-23
This can be marked as solved. 

To answer my question, after you start the server's openvpn and then the client's openvpn and they return initialized the connection is established.  Further, when configuring a bridged vpn adding push "redirect-gateway def1" to the server.conf and the directives --client and --pull to the client.conf route all traffic through OpenVPN  including the Internet. This can be tested using 'route', Traceroute, or using whatismyip.org.

---

