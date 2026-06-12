---
title: "Asus RT-68U router with openvpn setup - no handshake - dh key too small"
date: 2015-08-01
forum: Networking &amp; Wireless
---

### Post by makem2 on 2015-08-01
The client.ovpn was produced from the web page access to the router and is working on Android OS machines. I cannot get a working handshake on Ubuntu or Windows 7 & 8.1. For each connection the error message is identical. As it works on some I think the problem lies with the client machines but I cannot figure out what.

The Ubuntu computer IP is 192.168.1.12 and the router log show the failed connection attempt followed by a successful connect from and Android phone
Client error:

```

makem@MakemUbuntu:~$ sudo openvpn --config /etc/openvpn/client.ovpn
Sat Aug  1 12:43:59 2015 TLS Error: TLS object -> incoming plaintext read error
Sat Aug  1 12:43:59 2015 TLS Error: TLS handshake failed
Sat Aug  1 12:43:59 2015 SIGUSR1[soft,tls-error] received, process restarting
Sat Aug  1 12:44:01 2015 UDPv4 link local: [undef]
Sat Aug  1 12:44:01 2015 UDPv4 link remote: [AF_INET]xx.xxx.xx.xxx:1194
Sat Aug  1 12:44:01 2015 TLS_ERROR: BIO read tls_read_plaintext error: error:14082174:SSL routines:SSL3_CHECK_CERT_AND_ALGORITHM:dh key too small
Sat Aug  1 12:44:01 2015 TLS Error: TLS object -> incoming plaintext read error
Sat Aug  1 12:44:01 2015 TLS Error: TLS handshake failed
Sat Aug  1 12:44:01 2015 SIGUSR1[soft,tls-error] received, process restarting
Sat Aug  1 12:44:03 2015 UDPv4 link local: [undef]
Sat Aug  1 12:44:03 2015 UDPv4 link remote: [AF_INET]xx.xxx.xx.xxx:1194
Sat Aug  1 12:44:03 2015 TLS_ERROR: BIO read tls_read_plaintext error: error:14082174:SSL routines:SSL3_CHECK_CERT_AND_ALGORITHM:dh key too small
Sat Aug  1 12:44:03 2015 TLS Error: TLS object -> incoming plaintext read error
Sat Aug  1 12:44:03 2015 TLS Error: TLS handshake failed
Sat Aug  1 12:44:03 2015 SIGUSR1[soft,tls-error] received, process restarting
^CSat Aug  1 12:44:03 2015 SIGINT[hard,init_instance] received, process exiting
makem@MakemUbuntu:~$ 
```

I don't see any connection log here and I have not changed its location:

```
makem@MakemUbuntu:~$ cd /etc/openvpn
makem@MakemUbuntu:/etc/openvpn$ ls -la
total 24
drwxr-xr-x   2 root root  4096 Jul 31 18:26 .
drwxr-xr-x 132 root root 12288 Aug  1 12:01 ..
-rw-r--r--   1 root root  3574 Jul 31 18:26 client.ovpn
-rwxr-xr-x   1 root root  1301 Dec  1  2014 update-resolv-conf
```

Router log:

```

Aug  1 12:43:57 openvpn[11479]: 192.168.1.12:34651 TLS: Initial packet from [AF_INET]192.168.1.12:34651, sid=6ffaa814 fbc5da00
Aug  1 12:43:59 openvpn[11479]: 192.168.1.12:58736 TLS: Initial packet from [AF_INET]192.168.1.12:58736, sid=0ad97a76 2591a3fa
Aug  1 12:44:01 openvpn[11479]: 192.168.1.12:58273 TLS: Initial packet from [AF_INET]192.168.1.12:58273, sid=b3c81334 e7494903
Aug  1 12:44:03 openvpn[11479]: 192.168.1.12:46899 TLS: Initial packet from [AF_INET]192.168.1.12:46899, sid=31fbb506 46408f46
Aug  1 12:44:57 openvpn[11479]: 192.168.1.12:34651 TLS Error: TLS key negotiation failed to occur within 60 seconds (check your network connectivity)
Aug  1 12:44:57 openvpn[11479]: 192.168.1.12:34651 TLS Error: TLS handshake failed
Aug  1 12:44:57 openvpn[11479]: 192.168.1.12:34651 SIGUSR1[soft,tls-error] received, client-instance restarting
Aug  1 12:44:59 openvpn[11479]: 192.168.1.12:58736 TLS Error: TLS key negotiation failed to occur within 60 seconds (check your network connectivity)
Aug  1 12:44:59 openvpn[11479]: 192.168.1.12:58736 TLS Error: TLS handshake failed
Aug  1 12:44:59 openvpn[11479]: 192.168.1.12:58736 SIGUSR1[soft,tls-error] received, client-instance restarting
Aug  1 12:45:01 openvpn[11479]: 192.168.1.12:58273 TLS Error: TLS key negotiation failed to occur within 60 seconds (check your network connectivity)
Aug  1 12:45:01 openvpn[11479]: 192.168.1.12:58273 TLS Error: TLS handshake failed
Aug  1 12:45:01 openvpn[11479]: 192.168.1.12:58273 SIGUSR1[soft,tls-error] received, client-instance restarting
Aug  1 12:45:03 openvpn[11479]: 192.168.1.12:46899 TLS Error: TLS key negotiation failed to occur within 60 seconds (check your network connectivity)
Aug  1 12:45:03 openvpn[11479]: 192.168.1.12:46899 TLS Error: TLS handshake failed
Aug  1 12:45:03 openvpn[11479]: 192.168.1.12:46899 SIGUSR1[soft,tls-error] received, client-instance restarting
Aug  1 12:52:26 openvpn[11479]: 192.168.1.5:49719 TLS: Initial packet from [AF_INET]192.168.1.5:49719, sid=fbb6537b e314dfe2
Aug  1 12:52:29 openvpn[11479]: 192.168.1.5:49719 VERIFY OK: depth=1, C=TW, ST=TW, L=Taipei, O=ASUS, CN=RT-AC68U, emailAddress=me@myhost.mydomain
Aug  1 12:52:29 openvpn[11479]: 192.168.1.5:49719 VERIFY OK: depth=0, C=TW, ST=TW, L=Taipei, O=ASUS, CN=client, emailAddress=me@myhost.mydomain
Aug  1 12:52:30 openvpn[11479]: 192.168.1.5:49719 PLUGIN_CALL: POST /usr/lib/openvpn-plugin-auth-pam.so/PLUGIN_AUTH_USER_PASS_VERIFY status=0
Aug  1 12:52:30 openvpn[11479]: 192.168.1.5:49719 TLS: Username/Password authentication succeeded for username 'pi' 
Aug  1 12:52:30 openvpn[11479]: 192.168.1.5:49719 Data Channel Encrypt: Cipher 'BF-CBC' initialized with 128 bit key
Aug  1 12:52:30 openvpn[11479]: 192.168.1.5:49719 Data Channel Encrypt: Using 160 bit message hash 'SHA1' for HMAC authentication
Aug  1 12:52:30 openvpn[11479]: 192.168.1.5:49719 Data Channel Decrypt: Cipher 'BF-CBC' initialized with 128 bit key
Aug  1 12:52:30 openvpn[11479]: 192.168.1.5:49719 Data Channel Decrypt: Using 160 bit message hash 'SHA1' for HMAC authentication
Aug  1 12:52:30 openvpn[11479]: 192.168.1.5:49719 Control Channel: TLSv1, cipher TLSv1/SSLv3 DHE-RSA-AES256-SHA, 1024 bit RSA
Aug  1 12:52:30 openvpn[11479]: 192.168.1.5:49719 [client] Peer Connection Initiated with [AF_INET]192.168.1.5:49719
Aug  1 12:52:30 openvpn[11479]: client/192.168.1.5:49719 MULTI_sva: pool returned IPv4=10.8.0.6, IPv6=(Not enabled)
Aug  1 12:52:30 openvpn[11479]: client/192.168.1.5:49719 MULTI: Learn: 10.8.0.6 -> client/192.168.1.5:49719
Aug  1 12:52:30 openvpn[11479]: client/192.168.1.5:49719 MULTI: primary virtual IP for client/192.168.1.5:49719: 10.8.0.6
Aug  1 12:53:00 openvpn[11479]: client/192.168.1.5:49719 PUSH: Received control message: 'PUSH_REQUEST'
Aug  1 12:53:00 openvpn[11479]: client/192.168.1.5:49719 send_push_reply(): safe_cap=940
Aug  1 12:53:00 openvpn[11479]: client/192.168.1.5:49719 SENT CONTROL [client]: 'PUSH_REPLY,route 192.168.1.0 255.255.255.0,route 10.8.0.1,topology net30,ping 15,ping-restart 60,ifconfig 10.8.0.6 10.8.0.5' (status=1)
Aug  1 12:59:57 ntp: start NTP update
Aug  1 13:01:46 openvpn[11479]: client/192.168.1.5:49719 [client] Inactivity timeout (--ping-restart), restarting
Aug  1 13:01:46 openvpn[11479]: client/192.168.1.5:49719 SIGUSR1[soft,ping-restart] received, client-instance restarting


```

[edit] It would appear this error message is generic in that I can duplicate it by entering no password or a false password to connect. Very unhelpful imo

---

