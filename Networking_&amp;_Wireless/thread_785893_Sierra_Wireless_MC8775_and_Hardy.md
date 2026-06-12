---
title: "Sierra Wireless MC8775 and Hardy"
date: 2008-05-07
forum: Networking &amp; Wireless
---

### Post by jevel on 2008-05-07
I am trying to get the WWAN adapter built into my X61 to work with Ubuntu 8.04 Hardy here.

As I don't have an application to control it (like Access Connection), I have turned off PIN to be able to steer it via a PPP dialer.

I have established that the card is detected by the kernel and initialised with three ports, but no matter what I do, I cannot make it connect the PPP session.

Here's the output from dmesg:
```

[    3.817169] usb 4-1: new full speed USB device using uhci_hcd and address 3
[    3.969022] ADDRCONF(NETDEV_UP): eth0: link is not ready
[    3.989298] usb 4-1: configuration #1 chosen from 1 choice
[    3.994036] sierra 4-1:1.0: Sierra USB modem (3 port) converter detected
[    3.994759] usb 4-1: Sierra USB modem (3 port) converter now attached to ttyUSB0
[    3.994803] usb 4-1: Sierra USB modem (3 port) converter now attached to ttyUSB1
[    3.994846] usb 4-1: Sierra USB modem (3 port) converter now attached to ttyUSB2
```

and the output from trying to dial with pppd:

```
Dialing...
Serial connection established.
using channel 6
Using interface ppp0
Connect: ppp0 <--> /dev/ttyUSB0
Warning - secret file /etc/ppp/pap-secrets has world and/or group access
sent [LCP ConfReq id=0x1 <asyncmap 0x0> <magic 0xe0cf92a> <pcomp> <accomp>]
rcvd [LCP ConfReq id=0x10 <asyncmap 0x0> <auth chap MD5> <magic 0xf9343e> <pcomp> <accomp>]
sent [LCP ConfNak id=0x10 <auth pap>]
rcvd [LCP ConfAck id=0x1 <asyncmap 0x0> <magic 0xe0cf92a> <pcomp> <accomp>]
rcvd [LCP ConfReq id=0x11 <asyncmap 0x0> <auth pap> <magic 0xf9343e> <pcomp> <accomp>]
sent [LCP ConfAck id=0x11 <asyncmap 0x0> <auth pap> <magic 0xf9343e> <pcomp> <accomp>]
sent [LCP EchoReq id=0x0 magic=0xe0cf92a]
Warning - secret file /etc/ppp/pap-secrets has world and/or group access
sent [PAP AuthReq id=0x1 user="kjlX61" password=<hidden>]
rcvd [LCP DiscReq id=0x12 magic=0xf9343e]
rcvd [LCP EchoRep id=0x0 magic=0xf9343e 0e 0c f9 2a]
rcvd [PAP AuthAck id=0x1 ""]
PAP authentication succeeded
sent [CCP ConfReq id=0x1 <deflate 15> <deflate(old#) 15> <bsd v1 15>]
sent [IPCP ConfReq id=0x1 <compress VJ 0f 01> <addr 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns3 0.0.0.0>]
rcvd [LCP ProtRej id=0x13 80 fd 01 01 00 0f 1a 04 78 00 18 04 78 00 15 03 2f]
Protocol-Reject for 'Compression Control Protocol' (0x80fd) received
Modem hangup
Connection terminated.
```


I see that CCP gets rejected, but I am unable to sort out what it means. Any and all help would be appreciated.

-KJ

---

### Post by aboothe726 on 2008-06-08
Sorry I didn't see your post earlier.  I had a similar problem with my T61.  I got it working after a little fiddling.  My results are [here]("http://ubuntuforums.org/showthread.php?t=780345").  Good luck!

---

