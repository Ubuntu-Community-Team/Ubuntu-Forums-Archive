---
title: "Help needed using mobile phone as gprs modem through bluetooth"
date: 2007-08-15
forum: Networking &amp; Wireless
---

### Post by KenSentMe on 2007-08-15
For some time i've been trying to use my Nokia E61 phone as a gprs modem for my Ubuntu system. I've found some howto's on this forum, but they all didn't work for me. I use the following files:

/etc/bluetooth/rfcomm.conf:
```
rfcomm0 {
        device 00:12:D2:B4:55:1E;
        channel 2;
        comment "Nokia E61";
}
```I think these settings are right because something happens on my phone when i try to get a connection.

/etc/ppp/peers/vodafone
```
/dev/rfcomm0 115200
connect '/usr/sbin/chat -v -f /etc/chatscripts/chat-gprs'
crtscts
modem -detach
noccp
defaultroute
usepeerdns
user vodafone
ipcp-accept-remote
ipcp-accept-local
noipdefault
debug
```

This file directs to /etc/chatscripts/chat-gprs:
```
'' ATZ OK
AT+CGDCONT=1,"IP","live.vodafone.nl","0.0.0.0",0,0 
OK "ATD*99#"
CONNECT ''
```
The settings for this file came from a dutch Palm forum from a topic with a howto on connecting to vodafone in Holland (same as i should use): [http://www.palmclub.nl/forums/internet-communicatie/15351-vodafone-gprs-z600-t610-tungsten-t-kijk-hier.html](http://www.palmclub.nl/forums/internet-communicatie/15351-vodafone-gprs-z600-t610-tungsten-t-kijk-hier.html)
I also tried using *ATD*99***1#, but that also didn't help. 

I get these errors when running 'pppd call vodafone'

In /var/log/syslog:
> Aug 15 22:21:09 lisa2-ubuntu NetworkManager: <debug info>^I[1187209269.711858] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_b05_1712_0194E8_5B_0002_if0_bluetooth_hci_bluetooth_hci'). 
Aug 15 22:21:13 lisa2-ubuntu hcid[5619]: link_key_request (sba=00:18:F3:8D:1F:17, dba=00:12:D2:B4:55:1E)
Aug 15 22:21:14 lisa2-ubuntu chat[14324]: send (ATZ^M)
Aug 15 22:21:14 lisa2-ubuntu chat[14324]: expect (OK)
Aug 15 22:21:14 lisa2-ubuntu chat[14324]: ATZ^M^M
Aug 15 22:21:14 lisa2-ubuntu chat[14324]: OK
Aug 15 22:21:14 lisa2-ubuntu chat[14324]:  -- got it 
Aug 15 22:21:14 lisa2-ubuntu chat[14324]: send (AT+CGDCONT=1,"IP","live.vodafone.nl","0.0.0.0",0,0^M)
Aug 15 22:21:14 lisa2-ubuntu chat[14324]: expect (OK)
Aug 15 22:21:14 lisa2-ubuntu chat[14324]: ^M
Aug 15 22:21:14 lisa2-ubuntu chat[14324]: AT+CGDCONT=1,"IP","live.vodafone.nl","0.0.0.0",0,0^M^M
Aug 15 22:21:14 lisa2-ubuntu chat[14324]: OK
Aug 15 22:21:14 lisa2-ubuntu chat[14324]:  -- got it 
Aug 15 22:21:14 lisa2-ubuntu chat[14324]: send (ATD*99#^M)
Aug 15 22:21:14 lisa2-ubuntu chat[14324]: expect (CONNECT)
Aug 15 22:21:14 lisa2-ubuntu chat[14324]: ^M
Aug 15 22:21:14 lisa2-ubuntu chat[14324]: ATD*99#^M^M
Aug 15 22:21:14 lisa2-ubuntu chat[14324]: NO CARRIER^M
Aug 15 22:21:59 lisa2-ubuntu chat[14324]: alarm
Aug 15 22:21:59 lisa2-ubuntu chat[14324]: Failed
Aug 15 22:21:59 lisa2-ubuntu pppd[14313]: Connect script failed
Aug 15 22:22:00 lisa2-ubuntu pppd[14313]: Exit.

In terminal i get:
> jeroen@lisa2-ubuntu:/etc/chatscripts$ pppd call vodafone
Serial connection established.
using channel 5
Using interface ppp0
Connect: ppp0 <--> /dev/rfcomm0
rcvd [LCP ConfReq id=0x0 <auth pap> <mru 1500> <asyncmap 0xa0000>]
sent [LCP ConfReq id=0x1 <asyncmap 0x0> <magic 0x695cadc6> <pcomp> <accomp>]
sent [LCP ConfAck id=0x0 <auth pap> <mru 1500> <asyncmap 0xa0000>]
rcvd [LCP ConfRej id=0x1 <magic 0x695cadc6> <pcomp> <accomp>]
sent [LCP ConfReq id=0x2 <asyncmap 0x0>]
rcvd [LCP ConfAck id=0x2 <asyncmap 0x0>]
sent [LCP EchoReq id=0x0 magic=0x0]
sent [PAP AuthReq id=0x1 user="vodafone" password=<hidden>]
rcvd [LCP EchoRep id=0x0 magic=0x0]
rcvd [PAP AuthAck id=0x1 ""]
PAP authentication succeeded
sent [IPCP ConfReq id=0x1 <compress VJ 0f 01> <addr 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns3 0.0.0.0>]
rcvd [IPCP ConfReq id=0x0 <addr 10.6.6.6>]
sent [IPCP ConfAck id=0x0 <addr 10.6.6.6>]
rcvd [LCP TermReq id=0x1]
LCP terminated by peer
sent [LCP TermAck id=0x1]
Connection terminated.
Modem hangup

Is there anyone that got this working with vodafone in the Netherlands, and who can tell mehow, or does somebody know what i can do to use my phone as a modem?

---

### Post by ihristov on 2007-08-17
You are actually a little further along than me. Which file is the log for the chat? How did you manage to log the chat session to that file? I could not do that. I was able to run the script interactevely - not via "pppd"

In my case I am in the USA and connecting to T-Mobile, but I see exactly the same. There is no CONNECT after the ATD

I gave up and connected from a WinXP virtual machine. I wrote a little script to switch the network interfaces of the VM so that it uses the Linux box as a router when connected to a wired network or the WinXP VM provides the routing to the Linux box when connected via GPRS

---

