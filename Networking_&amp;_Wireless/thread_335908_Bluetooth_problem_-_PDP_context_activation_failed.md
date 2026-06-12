---
title: "Bluetooth problem - PDP context activation failed"
date: 2007-01-10
forum: Networking &amp; Wireless
---

### Post by chiefofthejojos on 2007-01-10
Hi,
All the function on my bluetooth adapter seem to work fine, so I'm hoping this is a simple mistake.  I followed the direction on this page ([https://help.ubuntu.com/community/BluetoothDialup](https://help.ubuntu.com/community/BluetoothDialup)) to set up my bluetooth dialup settings after I paired with my phone using bluez-passkey-gnome, but when I try to dialup it doesn't quite finish.  it definitely has quite a bit of success, but something goes wrong at the last minute.
Here's the relevant part of the syslog.

```
Jan 10 17:49:58 brad-laptop pppd[5249]: pppd 2.4.4 started by brad, uid 1000
Jan 10 17:50:02 brad-laptop hcid[4458]: link_key_request (sba=00:16:41:F2:D9:87, dba=00:16:DB:19:D4:72)
Jan 10 17:50:03 brad-laptop chat[5253]: timeout set to 35 seconds
Jan 10 17:50:03 brad-laptop chat[5253]: abort on (\nBUSY\r)
Jan 10 17:50:03 brad-laptop chat[5253]: abort on (\nERROR\r)
Jan 10 17:50:03 brad-laptop chat[5253]: abort on (\nNO ANSWER\r)
Jan 10 17:50:03 brad-laptop chat[5253]: abort on (\nNO CARRIER\r)
Jan 10 17:50:03 brad-laptop chat[5253]: abort on (\nNO DIALTONE\r)
Jan 10 17:50:03 brad-laptop chat[5253]: abort on (\nRINGING\r\n\r\nRINGING\r)
Jan 10 17:50:03 brad-laptop chat[5253]: send (^MAT^M)
Jan 10 17:50:03 brad-laptop chat[5253]: expect (OK)
Jan 10 17:50:03 brad-laptop chat[5253]: ^MAT^M^M
Jan 10 17:50:03 brad-laptop chat[5253]: OK
Jan 10 17:50:03 brad-laptop chat[5253]:  -- got it 
Jan 10 17:50:03 brad-laptop chat[5253]: send (AT+CGDCONT=1,"IP","internet3.voicestream.com"^M)
Jan 10 17:50:04 brad-laptop chat[5253]: expect (OK)
Jan 10 17:50:04 brad-laptop chat[5253]: ^M
Jan 10 17:50:04 brad-laptop chat[5253]: AT+CGDCONT=1,net3.voicestream.com^M
Jan 10 17:50:04 brad-laptop chat[5253]: OK
Jan 10 17:50:04 brad-laptop chat[5253]:  -- got it 
Jan 10 17:50:04 brad-laptop chat[5253]: send (ATD*99***1#^M)
Jan 10 17:50:04 brad-laptop chat[5253]: expect (CONNECT)
Jan 10 17:50:04 brad-laptop chat[5253]: ^M
Jan 10 17:50:08 brad-laptop chat[5253]: *99***1#^M^M
Jan 10 17:50:08 brad-laptop chat[5253]: CONNECT
Jan 10 17:50:08 brad-laptop chat[5253]:  -- got it 
Jan 10 17:50:08 brad-laptop chat[5253]: send (^M)
Jan 10 17:50:08 brad-laptop pppd[5249]: Serial connection established.
Jan 10 17:50:08 brad-laptop pppd[5249]: using channel 1
Jan 10 17:50:08 brad-laptop pppd[5249]: Using interface ppp0
Jan 10 17:50:08 brad-laptop pppd[5249]: Connect: ppp0 <--> /dev/rfcomm0
Jan 10 17:50:09 brad-laptop pppd[5249]: sent [LCP ConfReq id=0x1 <asyncmap 0x0> <magic 0x27eb6ad6> <pcomp> <accomp>]
Jan 10 17:50:09 brad-laptop pppd[5249]: rcvd [LCP ConfReq id=0x1 <asyncmap 0xa0000> <auth pap>]
Jan 10 17:50:09 brad-laptop pppd[5249]: sent [LCP ConfAck id=0x1 <asyncmap 0xa0000> <auth pap>]
Jan 10 17:50:09 brad-laptop pppd[5249]: rcvd [LCP ConfRej id=0x1 <magic 0x27eb6ad6> <pcomp> <accomp>]
Jan 10 17:50:09 brad-laptop pppd[5249]: sent [LCP ConfReq id=0x2 <asyncmap 0x0>]
Jan 10 17:50:09 brad-laptop pppd[5249]: rcvd [LCP ConfAck id=0x2 <asyncmap 0x0>]
Jan 10 17:50:09 brad-laptop pppd[5249]: sent [LCP EchoReq id=0x0 magic=0x0]
Jan 10 17:50:09 brad-laptop pppd[5249]: sent [PAP AuthReq id=0x1 user="brad-laptop" password=<hidden>]
Jan 10 17:50:09 brad-laptop pppd[5249]: rcvd [LCP EchoRep id=0x0 magic=0x0]
Jan 10 17:50:09 brad-laptop pppd[5249]: rcvd [PAP AuthAck id=0x1 "Login OK"]
Jan 10 17:50:09 brad-laptop pppd[5249]: Remote message: Login OK
Jan 10 17:50:09 brad-laptop pppd[5249]: PAP authentication succeeded
Jan 10 17:50:09 brad-laptop kernel: [  195.664628] PPP BSD Compression module registered
Jan 10 17:50:10 brad-laptop pppd[5249]: sent [CCP ConfReq id=0x1 <deflate 15> <deflate(old#) 15> <bsd v1 15>]
Jan 10 17:50:10 brad-laptop kernel: [  195.697597] PPP Deflate Compression module registered
Jan 10 17:50:10 brad-laptop pppd[5249]: sent [IPCP ConfReq id=0x1 <compress VJ 0f 01> <addr 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns3 0.0.0.0>]
Jan 10 17:50:10 brad-laptop pppd[5249]: rcvd [LCP ProtRej id=0x2 80 fd 01 01 00 0f 1a 04 78 00 18 04 78 00 15 03 2f]
Jan 10 17:50:10 brad-laptop pppd[5249]: Protocol-Reject for 'Compression Control Protocol' (0x80fd) received
Jan 10 17:50:10 brad-laptop pppd[5249]: rcvd [IPCP ConfRej id=0x1 <compress VJ 0f 01>]
Jan 10 17:50:10 brad-laptop pppd[5249]: sent [IPCP ConfReq id=0x2 <addr 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns3 0.0.0.0>]
Jan 10 17:50:12 brad-laptop pppd[5249]: rcvd [LCP TermReq id=0x3 "PDP context activation failed, no network protocol running"]
Jan 10 17:50:12 brad-laptop pppd[5249]: LCP terminated by peer (PDP context activation failed, no network protocol running)
Jan 10 17:50:12 brad-laptop pppd[5249]: sent [LCP TermAck id=0x3]
Jan 10 17:50:15 brad-laptop pppd[5249]: Connection terminated.
Jan 10 17:50:16 brad-laptop pppd[5249]: Modem hangup
Jan 10 17:50:16 brad-laptop pppd[5249]: Exit.

```

---

### Post by lingnoi on 2007-01-10
From reading this line

```
Jan 10 17:50:12 brad-laptop pppd[5249]: LCP terminated by peer (PDP context activation failed, no network protocol running)
```

My best guess is that your network operator doesn't support the protocol that you are trying to use. Are you trying to use IPv6?

Apart from that I have no idea since I am having problems connecting to my own network via BT.

---

### Post by chiefofthejojos on 2007-01-12
All right!  I finally have working bluetooth dialup in edgy!  (I'm writing this post over bluetooth dun, of course ;))  Your suggestion prompted me to look over my config files again and I noticed a comment I had overlooked before on the wiki.  On T-Mobile, I had to comment out ```
lcp-echo-failure 0
``` in the ```
/etc/ppp/peers/BluetoothDialup
``` file.  Thank you!!

---

