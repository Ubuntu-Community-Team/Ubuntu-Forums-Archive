---
title: "Sierra Wireless 595U"
date: 2007-08-30
forum: Networking &amp; Wireless
---

### Post by Jalke on 2007-08-30
Hi all,
If anyone could help me, that'd be great!  I'm really keen to get internet on my linux setup.

I seem to almost have the usb modem going.  I downloaded the driver supplied on the website and added my password and username to the /etc/ppp/options and /etc/ppp/pap-secrets files.  The device is making a connection and communicating - I got past the authentication step.  However that's where the modem and I seem to get stuck.  Any tips??

Here's the log:

Starting Sierra Wireless CDMA connect script...



Setting the abort string



Initializing modem



Dialing...

Serial connection established.

using channel 16

Using interface ppp0

Connect: ppp0 <--> /dev/ttyUSB0

rcvd [LCP ConfReq id=0x1 <asyncmap 0x0> <auth pap> <magic 0x288af29e>]

sent [LCP ConfReq id=0x1 <asyncmap 0x0> <magic 0x5b233965> <pcomp> <accomp>]

sent [LCP ConfAck id=0x1 <asyncmap 0x0> <auth pap> <magic 0x288af29e>]

rcvd [LCP ConfAck id=0x1 <asyncmap 0x0> <magic 0x5b233965> <pcomp> <accomp>]

sent [LCP EchoReq id=0x0 magic=0x5b233965]

sent [PAP AuthReq id=0x1 user="mobile@jamamobile" password=<hidden>]

rcvd [LCP EchoRep id=0x0 magic=0x288af29e]

rcvd [PAP AuthAck id=0x1 ""]

PAP authentication succeeded

sent [CCP ConfReq id=0x1 <deflate 15> <deflate(old#) 15> <bsd v1 15>]

sent [IPCP ConfReq id=0x1 <compress VJ 0f 01> <addr 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns3 0.0.0.0>]

rcvd [LCP ProtRej id=0xac 80 fd 01 01 00 0f 1a 04 78 00 18 04 78 00 15 03 2f]

Protocol-Reject for 'Compression Control Protocol' (0x80fd) received

rcvd [IPCP ConfRej id=0x1 <compress VJ 0f 01>]

sent [IPCP ConfReq id=0x2 <addr 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns3 0.0.0.0>]

rcvd [IPCP ConfReq id=0xf7 <addr 166.179.16.1>]

sent [IPCP ConfAck id=0xf7 <addr 166.179.16.1>]

rcvd [IPCP ConfNak id=0x2 <addr 166.179.28.76> <ms-dns1 202.27.158.40> <ms-dns3 202.27.156.72>]

sent [IPCP ConfReq id=0x3 <addr 166.179.28.76> <ms-dns1 202.27.158.40> <ms-dns3 202.27.156.72>]

rcvd [IPCP ConfAck id=0x3 <addr 166.179.28.76> <ms-dns1 202.27.158.40> <ms-dns3 202.27.156.72>]

Cannot determine ethernet address for proxy ARP

local  IP address 166.179.28.76

remote IP address 166.179.16.1

primary   DNS address 202.27.158.40

secondary DNS address 202.27.156.72

Script /etc/ppp/ip-up started (pid 8978)

Script /etc/ppp/ip-up finished (pid 8978), status = 0x0

sent [LCP EchoReq id=0x1 magic=0x5b233965]

rcvd [LCP EchoRep id=0x1 magic=0x288af29e]

sent [LCP EchoReq id=0x2 magic=0x5b233965]

rcvd [LCP EchoRep id=0x2 magic=0x288af29e]

sent [LCP EchoReq id=0x3 magic=0x5b233965]

rcvd [LCP EchoRep id=0x3 magic=0x288af29e]


This just continues without me being able do anything with internet.  I'm not sure what the log output all means.  If anyone can translate and give some advice, that'd be great!

Jalke

---

### Post by Jalke on 2007-08-31
So far, I understand that I have a healthy connection going.  However, I still can't seem to figure out how to do something with it.  Someone mentioned that it might have to do with DNS settings.  But I can't seem to find the /etc/resolv.conf file.  Any ideas??
Thanks a lot.

Jalke

---

### Post by Jalke on 2007-08-31
I did it :guitar:  !!  I created the (empty) /etc/resolv.conf file and added in the appropriate DNS addresses.  And it works!  

Jalke

---

