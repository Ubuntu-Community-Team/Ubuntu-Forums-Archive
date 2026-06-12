---
title: "VPN password not accepted by network manager"
date: 2018-02-17
forum: Networking &amp; Wireless
---

### Post by nickjhs on 2018-02-17
Whenever I try to connect to my VPN the Authentication box pops up, I put in the password, the box disappears for a few seconds then pops up again. No error message. but no connection either.

---

### Post by TheFu on 2018-02-18
Which VPN is being used?  tinc, openvpn, libreswan, pptp (NEVER use that!!!!) will need different responses from people with different expertise.

Is the VPN server something you setup?  Or is it a paid service?

Have you tried running the VPN from a shell with debug messages (verbosity) enabled?  
Also, what do the log files show?

And did this ever work?

---

### Post by nickjhs on 2018-02-18
Thanks for the reply. I am using IPVANISH, setting it up using the "import from file" option in Ubuntu 17.10. I do have option of using open vpn

---

### Post by nickjhs on 2018-02-18
Also how do I run the VPN from a shell with debug messages (verbosity) enabled"  

To answer your question yes it did used to work under 16.04

---

### Post by nickjhs on 2018-02-18
To answer your question yes it did used to work under 16.04 sudo openvpn --config ipvanish-AT-Vienna-vie-c04.ovpn
Mon Feb 19 15:03:05 2018 OpenVPN 2.4.3 x86_64-pc-linux-gnu [SSL (OpenSSL)] [LZO] [LZ4] [EPOLL] [PKCS11] [MH/PKTINFO] [AEAD] built on Jul  3 2017
Mon Feb 19 15:03:05 2018 library versions: OpenSSL 1.0.2g  1 Mar 2016, LZO 2.08
Enter Auth Username: nick                 
Enter Auth Password: ***********
Mon Feb 19 15:04:25 2018 TCP/UDP: Preserving recently used remote address: [AF_INET]185.180.12.98:443
Mon Feb 19 15:04:25 2018 Socket Buffers: R=[212992->212992] S=[212992->212992]
Mon Feb 19 15:04:25 2018 UDP link local: (not bound)
Mon Feb 19 15:04:25 2018 UDP link remote: [AF_INET]185.180.12.98:443
Mon Feb 19 15:04:25 2018 TLS: Initial packet from [AF_INET]185.180.12.98:443, sid=f152135f d77f8b1d
Mon Feb 19 15:04:25 2018 WARNING: this configuration may cache passwords in memory -- use the auth-nocache option to prevent this
Mon Feb 19 15:04:25 2018 VERIFY OK: depth=1, C=US, ST=FL, L=Winter Park, O=IPVanish, OU=IPVanish VPN, CN=IPVanish CA, emailAddress=support@ipvanish.com
Mon Feb 19 15:04:25 2018 VERIFY X509NAME OK: C=US, ST=FL, L=Winter Park, O=IPVanish, OU=IPVanish VPN, CN=vie-c04.ipvanish.com, emailAddress=support@ipvanish.com
Mon Feb 19 15:04:25 2018 VERIFY OK: depth=0, C=US, ST=FL, L=Winter Park, O=IPVanish, OU=IPVanish VPN, CN=vie-c04.ipvanish.com, emailAddress=support@ipvanish.com
Mon Feb 19 15:04:27 2018 Control Channel: TLSv1.2, cipher TLSv1/SSLv3 DHE-RSA-AES256-SHA, 2048 bit RSA
Mon Feb 19 15:04:27 2018 [vie-c04.ipvanish.com] Peer Connection Initiated with [AF_INET]185.180.12.98:443
Mon Feb 19 15:04:28 2018 SENT CONTROL [vie-c04.ipvanish.com]: 'PUSH_REQUEST' (status=1)
Mon Feb 19 15:04:29 2018 AUTH: Received control message: AUTH_FAILED
Mon Feb 19 15:04:29 2018 SIGTERM[soft,auth-failure] received, process exiting

---

### Post by TheFu on 2018-02-19
I don't know anything about ipvanish or 17.10. 
I run my own openvpn (openssl-based) VPN and use 16.04. I only use TLS releases.
Sorry.

Does ipvanish have new instructions for 17.10?  Maybe the openvpn version you are using and they provide aren't compatible?

---

