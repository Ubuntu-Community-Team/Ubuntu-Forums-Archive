---
title: "HowTo: Connect to WatchGuard Firebox X firewall IPSec VPN"
date: 2008-10-03
forum: Networking &amp; Wireless
---

### Post by jabley on 2008-10-03
Any suggestions? I've tried using PPTP, but the WatchGuard PPTP implementation doesn't appear to be very stable. I get lots of output in /var/log/syslog like this:

```

Oct  3 18:33:28 miq-jabley pppd[10207]: rcvd [CCP ResetReq id=0x3]
Oct  3 18:33:28 miq-jabley pppd[10207]: sent [CCP ResetAck id=0x3]
Oct  3 18:33:28 miq-jabley pppd[10207]: rcvd [CCP ResetReq id=0x4]
Oct  3 18:33:28 miq-jabley pppd[10207]: sent [CCP ResetAck id=0x4]
Oct  3 18:33:29 miq-jabley pppd[10207]: rcvd [CCP ResetReq id=0x5]
Oct  3 18:33:29 miq-jabley pppd[10207]: sent [CCP ResetAck id=0x5]
Oct  3 18:33:33 miq-jabley pppd[10207]: rcvd [CCP ResetReq id=0x6]
Oct  3 18:33:33 miq-jabley pppd[10207]: sent [CCP ResetAck id=0x6]
Oct  3 18:33:33 miq-jabley pppd[10207]: rcvd [CCP ResetReq id=0x7]
Oct  3 18:33:33 miq-jabley pppd[10207]: sent [CCP ResetAck id=0x7]
Oct  3 18:33:33 miq-jabley pppd[10207]: rcvd [CCP ResetReq id=0x8]
Oct  3 18:33:33 miq-jabley pppd[10207]: sent [CCP ResetAck id=0x8]
Oct  3 18:33:34 miq-jabley pppd[10207]: rcvd [CCP ResetReq id=0x9]
Oct  3 18:33:34 miq-jabley pppd[10207]: sent [CCP ResetAck id=0x9]
Oct  3 18:33:34 miq-jabley pppd[10207]: rcvd [CCP ResetReq id=0xa]
Oct  3 18:33:34 miq-jabley pppd[10207]: sent [CCP ResetAck id=0xa]
Oct  3 18:33:34 miq-jabley pppd[10207]: rcvd [CCP ResetReq id=0xb]
Oct  3 18:33:34 miq-jabley pppd[10207]: sent [CCP ResetAck id=0xb]
Oct  3 18:33:35 miq-jabley pppd[10207]: rcvd [CCP ResetReq id=0xc]
Oct  3 18:33:35 miq-jabley pppd[10207]: sent [CCP ResetAck id=0xc]
Oct  3 18:33:37 miq-jabley pppd[10207]: rcvd [CCP ResetReq id=0xd]
Oct  3 18:33:37 miq-jabley pppd[10207]: sent [CCP ResetAck id=0xd]
Oct  3 18:33:39 miq-jabley pppd[10207]: rcvd [CCP ResetReq id=0xe]
Oct  3 18:33:39 miq-jabley pppd[10207]: sent [CCP ResetAck id=0xe]
Oct  3 18:33:39 miq-jabley pppd[10207]: rcvd [CCP ResetReq id=0xf]
Oct  3 18:33:39 miq-jabley pppd[10207]: sent [CCP ResetAck id=0xf]
Oct  3 18:33:39 miq-jabley pppd[10207]: rcvd [CCP ResetReq id=0x10]
Oct  3 18:33:39 miq-jabley pppd[10207]: sent [CCP ResetAck id=0x10]
Oct  3 18:33:39 miq-jabley pppd[10207]: rcvd [CCP ResetReq id=0x11]
Oct  3 18:33:39 miq-jabley pppd[10207]: sent [CCP ResetAck id=0x11]
Oct  3 18:33:39 miq-jabley pppd[10207]: rcvd [CCP ResetReq id=0x12]
Oct  3 18:33:39 miq-jabley pppd[10207]: sent [CCP ResetAck id=0x12]
Oct  3 18:33:39 miq-jabley pppd[10207]: rcvd [CCP ResetReq id=0x13]
Oct  3 18:33:39 miq-jabley pppd[10207]: sent [CCP ResetAck id=0x13]
Oct  3 18:33:39 miq-jabley pppd[10207]: rcvd [CCP ResetReq id=0x14]
Oct  3 18:33:39 miq-jabley pppd[10207]: sent [CCP ResetAck id=0x14]
Oct  3 18:33:40 miq-jabley pppd[10207]: rcvd [CCP ResetReq id=0x15]
Oct  3 18:33:40 miq-jabley pppd[10207]: sent [CCP ResetAck id=0x15]
Oct  3 18:33:40 miq-jabley pppd[10207]: rcvd [CCP ResetReq id=0x16]
Oct  3 18:33:40 miq-jabley pppd[10207]: sent [CCP ResetAck id=0x16]
Oct  3 18:33:41 miq-jabley pppd[10207]: rcvd [CCP ResetReq id=0x17]
Oct  3 18:33:41 miq-jabley pppd[10207]: sent [CCP ResetAck id=0x17]
Oct  3 18:33:42 miq-jabley pppd[10207]: rcvd [CCP ResetReq id=0x18]
Oct  3 18:33:42 miq-jabley pppd[10207]: sent [CCP ResetAck id=0x18]
Oct  3 18:33:42 miq-jabley pppd[10207]: rcvd [CCP ResetReq id=0x19]
Oct  3 18:33:42 miq-jabley pppd[10207]: sent [CCP ResetAck id=0x19]
Oct  3 18:33:46 miq-jabley pppd[10207]: rcvd [CCP ResetReq id=0x1a]
Oct  3 18:33:46 miq-jabley pppd[10207]: sent [CCP ResetAck id=0x1a]
Oct  3 18:33:57 miq-jabley pptp[10212]: anon log[logecho:pptp_ctrl.c:676]: Echo Reply received.
Oct  3 18:34:41 miq-jabley pppd[10207]: rcvd [LCP ProtRej id=0x3 00 cd 61 28 9d 28 ac de 2c e7 4c 24 3d 5b ad 14 e4 52 6b b6 ba 6a 07 59 26 59 91 ed f9 7b a6 44 ...]
Oct  3 18:34:41 miq-jabley pppd[10207]: Protocol-Reject for unsupported protocol 0xcd
Oct  3 18:34:41 miq-jabley pppd[10207]: rcvd [LCP ProtRej id=0x4 00 17 7f cb e4 eb b7 cf 4b 0f b3 84 d4 69 ff 57 9f c6 2f 39 22 22 8a 6d f0 34 1c c4 89 70 25 d4 ...]
Oct  3 18:34:41 miq-jabley pppd[10207]: Protocol-Reject for unsupported protocol 0x17
Oct  3 18:34:41 miq-jabley pppd[10207]: rcvd [LCP ProtRej id=0x5 00 c5 1c a8 5f 40 1f ac a3 3d 42 12 ab 99 7d b9 70 a9 5a 25 6b 7b 15 6c 86 bb 31 fa 84 da b1 ec ...]
Oct  3 18:34:41 miq-jabley pppd[10207]: Protocol-Reject for unsupported protocol 0xc5
Oct  3 18:34:41 miq-jabley pppd[10207]: rcvd [LCP ProtRej id=0x6 96 af ea 83 d4 53 1a 8e a0 93 a1 3c ce 27 27 aa fe 89 f1 0e 92 35 db c2 48 9b 12 fc 0e bf 20 fe ...]
Oct  3 18:34:41 miq-jabley pppd[10207]: Protocol-Reject for unsupported protocol 0x96af
Oct  3 18:34:41 miq-jabley pppd[10207]: rcvd [LCP ProtRej id=0x7 44 b2 df bf 2e 7e 9e 30 b2 30 99 e8 5a 5a 9a ff 9e c6 20 61 97 c3 c7 fa 4b bc 91 8e a3 54 82 04 ...]
Oct  3 18:34:41 miq-jabley pppd[10207]: Protocol-Reject for unsupported protocol 0x44b2
Oct  3 18:34:42 miq-jabley pppd[10207]: rcvd [LCP ProtRej id=0x8 00 0f c3 9c aa 08 d7 db 04 2d 10 2a 75 f7 14 1c ed 49 0a 0e 19 59 b2 77 85 3a 9d 6c 9d 74 03 66 ...]
Oct  3 18:34:42 miq-jabley pppd[10207]: Protocol-Reject for unsupported protocol 0xf
Oct  3 18:34:43 miq-jabley pppd[10207]: rcvd [LCP ProtRej id=0x9 b8 94 7f 88 72 c4 8d 43 c4 49 96 2f 37 5b 7b 64 90 ab 5e 0c 0a 57 cd 50 a5 cb 98 bf d5 9f 40 ba ...]
Oct  3 18:34:43 miq-jabley pppd[10207]: Protocol-Reject for unsupported protocol 0xb894
Oct  3 18:34:46 miq-jabley pppd[10207]: rcvd [LCP ProtRej id=0xa 00 87 cf d4 b3 07 d5 59 5b 04 d6 e9 ca 0c 2b bc e7 d5 a9 66 28 19 7d 2e 62 9d 69 74 50 60 37 e3 ...]
Oct  3 18:34:46 miq-jabley pppd[10207]: Protocol-Reject for unsupported protocol 0x87
Oct  3 18:34:52 miq-jabley pppd[10207]: rcvd [LCP ProtRej id=0xb 00 8f dd ef 6e 33 4f 5d 37 89 a7 ec 46 bc 10 d9 f9 95 11 01 7c cc 52 0d 47 6a 69 19 20 5b 19 47 ...]
Oct  3 18:34:52 miq-jabley pppd[10207]: Protocol-Reject for unsupported protocol 0x8f
Oct  3 18:34:57 miq-jabley pptp[10212]: anon log[logecho:pptp_ctrl.c:676]: Echo Reply received.
Oct  3 18:35:02 miq-jabley pppd[10207]: rcvd [LCP ProtRej id=0xc c6 8b b7 eb 1f 61 b0 53 79 de 54 38 02 4c 1c 1c a5 23 19 1e 7c 4d b5 e2 c0 fb 30 70 df f8 41 17 ...]
Oct  3 18:35:02 miq-jabley pppd[10207]: Protocol-Reject for unsupported protocol 0xc68b

```

Colleagues using Windows to connect to the WatchGuard PPTP find it similarly unreliable. I've not had problems with PPTP before, when connecting to a Windows server. So my presumption is that it is a WatchGuard PPTP issue.

Again, my colleagues on Windows find that the WatchGuard IPSec VPN is much more stable. But I've really struggled to get it working. I've tried using OpenVPN via NetworkManager. Most of the documentation seems to talk about OpenVPN and its ilk as a server product, rather than a client connecting to an IPSec implementation (which is an RFC, so you'd hope it would be reasonably standardised!).

I'm trying using SHA1-HMAC and AES with a shared key. From what I've read, I think I may have more success on the client using a certificate, but I haven't been able to get that working either.

Is anyone using Ubuntu as a client to this IPSec implementation and could they share how please?

Thanks in advance.

---

### Post by Cubus on 2009-07-23
I'd like to bump this topic, as I too would like to connect to our Firebox by IPSec.

Edit:
I did manage to set up SSL-VPN tho, works great. I used this guide (German, sorry):

[http://www.stoeps.de/ssl-vpn-von-ubuntu-zu-watchguard-firebox](http://www.stoeps.de/ssl-vpn-von-ubuntu-zu-watchguard-firebox)

---

