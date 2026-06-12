---
title: "Ubuntu 12.04 OpenVPN client"
date: 2015-10-07
forum: Networking &amp; Wireless
---

### Post by Justin_Slay on 2015-10-07
So I have gone through all the stuff to get my VPS setup to allow it VPN access. I start the service, the OpenVPN server sees the connection and assigns the virtual address, but in ifconfig there is no tun0, and it drops the VPN connection instantly after it has connected.

Is there something I am missing here?

I built out all the crt and key files from then ovpn file. 

```
sudo service openvpn start
 * Starting virtual private network daemon(s)...                                                                                                                                                                                                                                
 *   Autostarting VPN 'client' 
```

Never get an OK or anything. Set permission of all files to 755 root:root

**EDIT:** Looks like it is an issue with my VPS, talking with support to see if I can have them resolve the issue.

```
Oct  7 10:40:08 ps473328 ovpn-client[9362]: OpenVPN 2.2.1 x86_64-linux-gnu [SSL] [LZO2] [EPOLL] [PKCS11] [eurephia] [MH] [PF_INET6] [IPv6 payload 20110424-2 (2.2RC2)] built on Dec  1 2014Oct  7 10:40:08 ps473328 ovpn-client[9362]: NOTE: the current --script-security setting may allow this configuration to call user-defined scripts
Oct  7 10:40:08 ps473328 ovpn-client[9362]: LZO compression initialized
Oct  7 10:40:08 ps473328 ovpn-client[9362]: Control Channel MTU parms [ L:1542 D:138 EF:38 EB:0 ET:0 EL:0 ]
Oct  7 10:40:08 ps473328 ovpn-client[9362]: Socket Buffers: R=[120832->131072] S=[120832->131072]
Oct  7 10:40:08 ps473328 ovpn-client[9362]: Data Channel MTU parms [ L:1542 D:1450 EF:42 EB:135 ET:0 EL:0 AF:3/1 ]
Oct  7 10:40:08 ps473328 ovpn-client[9362]: Local Options hash (VER=V4): '41690919'
Oct  7 10:40:08 ps473328 ovpn-client[9362]: Expected Remote Options hash (VER=V4): '530fdded'
Oct  7 10:40:08 ps473328 ovpn-client[9370]: UDPv4 link local: [undef]
Oct  7 10:40:08 ps473328 ovpn-client[9370]: UDPv4 link remote: [AF_INET]************
Oct  7 10:40:08 ps473328 ovpn-client[9370]: TLS: Initial packet from [AF_INET]**********, sid=3f68337c 11f18a40
Oct  7 10:40:09 ps473328 ovpn-client[9370]: VERIFY OK: depth=1, /C=TW/ST=TW/L=Taipei/O=ASUS/CN=RT-AC3200/emailAddress=me@myhost.mydomain
Oct  7 10:40:09 ps473328 ovpn-client[9370]: VERIFY OK: nsCertType=SERVER
Oct  7 10:40:09 ps473328 ovpn-client[9370]: VERIFY OK: depth=0, /C=TW/ST=TW/L=Taipei/O=ASUS/CN=RT-AC3200/emailAddress=me@myhost.mydomain
Oct  7 10:40:09 ps473328 ovpn-client[9370]: Data Channel Encrypt: Cipher 'BF-CBC' initialized with 128 bit key
Oct  7 10:40:09 ps473328 ovpn-client[9370]: Data Channel Encrypt: Using 160 bit message hash 'SHA1' for HMAC authentication
Oct  7 10:40:09 ps473328 ovpn-client[9370]: Data Channel Decrypt: Cipher 'BF-CBC' initialized with 128 bit key
Oct  7 10:40:09 ps473328 ovpn-client[9370]: Data Channel Decrypt: Using 160 bit message hash 'SHA1' for HMAC authentication
Oct  7 10:40:09 ps473328 ovpn-client[9370]: Control Channel: TLSv1, cipher TLSv1/SSLv3 DHE-RSA-AES256-SHA, 1024 bit RSA
Oct  7 10:40:09 ps473328 ovpn-client[9370]: [RT-AC3200] Peer Connection Initiated with [AF_INET]**********
Oct  7 10:40:12 ps473328 ovpn-client[9370]: SENT CONTROL [RT-AC3200]: 'PUSH_REQUEST' (status=1)
Oct  7 10:40:12 ps473328 ovpn-client[9370]: PUSH: Received control message: 'PUSH_REPLY,route 192.168.2.0 255.255.255.0,route-gateway 10.9.0.1,topology subnet,ping 15,ping-restart 60,ifconfig 10.9.0.2 255.255.255.0'
Oct  7 10:40:12 ps473328 ovpn-client[9370]: OPTIONS IMPORT: timers and/or timeouts modified
Oct  7 10:40:12 ps473328 ovpn-client[9370]: OPTIONS IMPORT: --ifconfig/up options modified
Oct  7 10:40:12 ps473328 ovpn-client[9370]: OPTIONS IMPORT: route options modified
Oct  7 10:40:12 ps473328 ovpn-client[9370]: OPTIONS IMPORT: route-related options modified
Oct  7 10:40:12 ps473328 ovpn-client[9370]: ROUTE default_gateway=*********
Oct  7 10:40:12 ps473328 ovpn-client[9370]: Note: Cannot open TUN/TAP dev /dev/net/tun: No such file or directory (errno=2)
Oct  7 10:40:12 ps473328 ovpn-client[9370]: do_ifconfig, tt->ipv6=0, tt->did_ifconfig_ipv6_setup=0
Oct  7 10:40:12 ps473328 ovpn-client[9370]: /sbin/ifconfig  10.9.0.2 netmask 255.255.255.0 mtu 1500 broadcast 10.9.0.255
Oct  7 10:40:12 ps473328 ovpn-client[9370]: Linux ifconfig failed: external program exited with error status: 255
Oct  7 10:40:12 ps473328 ovpn-client[9370]: Exiting



```

---

