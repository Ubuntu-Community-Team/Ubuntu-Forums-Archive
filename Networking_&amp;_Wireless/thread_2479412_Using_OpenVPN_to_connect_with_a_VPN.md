---
title: "Using OpenVPN to connect with a VPN"
date: 2022-09-23
forum: Networking &amp; Wireless
---

### Post by stavroblofeld on 2022-09-23
Greetings,

I am attempting to connect to a VPN I am registered with - using OpenVPN

I am using Ubuntu 22.04.1 LTS
I have OpenSSL version 3.0.2 and OpenVPN version 2.5.5 installed.

When I attempt to connect to the VPN using OpenVPN this is the output displayed:

openvpn --config openvpn_config_file.ovpn
2022-09-23 19:59:05 DEPRECATED OPTION: --cipher set to 'AES-256-CBC' but missing in --data-ciphers (AES-256-GCM:AES-128-GCM). Future OpenVPN version will ignore --cipher for cipher negotiations. Add 'AES-256-CBC' to --data-ciphers or change --cipher 'AES-256-CBC' to --data-ciphers-fallback 'AES-256-CBC' to silence this warning.
2022-09-23 19:59:05 OpenVPN 2.5.5 x86_64-pc-linux-gnu [SSL (OpenSSL)] [LZO] [LZ4] [EPOLL] [PKCS11] [MH/PKTINFO] [AEAD] built on Mar 22 2022
2022-09-23 19:59:05 library versions: OpenSSL 3.0.2 15 Mar 2022, LZO 2.10
2022-09-23 19:59:05 OpenSSL: error:0A00018E:SSL routines::ca md too weak
2022-09-23 19:59:05 Cannot load inline certificate file
2022-09-23 19:59:05 Exiting due to fatal error


Any Ideas ?

Thanks !

---

### Post by TheFu on 2022-09-24
Just a guess, but ... 

I vaguely recall that 2 other files need to be installed, provided by the VPN provider to support 256-bit AES.

ca.rsa.4096.crt  crl.rsa.4096.pem are the files. 
These need to be added in the settings - I modified the login.cf files for each exit node for those files to be used.  Also, often the VPN provider will require the use of different ports to support 256-AES rather than 128-AES connections.  My VPN provider has a list of ports, protocols, encryption, auth, hash, root CAs and CRLs somewhere on their site for people choosing the more secure encryption, which isn't their default.

---

