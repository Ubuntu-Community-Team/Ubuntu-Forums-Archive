---
title: "Problem with Verizon DSL PPPOE, with DHCP"
date: 2006-08-10
forum: Networking &amp; Wireless
---

### Post by wfwh3rd on 2006-08-10
When I type ifconfig this is my print-out:
etho: line encap: ethernet hwaddr: 00:15:58:36:BO:62
inet6:fe80:215:58ff:fe36:bo62/64 Scpe:Link up Broadcast Runing multcast: mtu:1500 Metric:1
RX Packets: 276 errors 0: 0 drropped: 0overuns: 0frame:0
tx packet: 0 errors: 0 dropped: 622 overuns:0 :carrier 0
rx bytes: 78806 (76.9 kib) tx bytes:0 (bytes:0 (0.0b)
interrupt: 225 base address: 0xa000

lo: Link loopback
inet addr:127.0.0.1 mask :255.0.0.0
inet6 addr: 1/128 scope: Host
up loopback running mtu:16436 Metric:1
rx packet: 210 errors:0 dropped 0 :frame:0
tx packets: 210 errors:0 dropped 0 overruns 0 carrier 0
collisions: 0
rxbytes 19334 (18.8 K:B) tx bytes: 19334 (18.8 K:B)
When I type in sudo pppoeconf, I get: access concentrator of your provider didnot respond. reason for the scan failure may also be another PPPOE process which controls modem. Please help, I would like to put XP away and use Ubuntu but I do like the internet:-({|=

---

### Post by The Uniphobiac on 2006-08-10
What DSL Modem do you have, is it a bridge or a bridge/router?  If it is a router, it could already be configured for PPPoE.

---

### Post by wfwh3rd on 2006-08-10
Thank you for repling to my question (Uniphobiac.) I used the {dpkg -s pppoeconf} and the status came by install ok installed. My modem came with Verizon DSL kit, which is Westell Veralink model 327w. My DSL phone line goes into the Westell modem and my cable goes from modem to computer. All is well with the connection on xp but no connection with ubuntu. When I try the pppoe package it tells me that {another running pppoe process which controls the modem is in use) What the process is I have no idea. The only ping that comes back is 127.0.0.1. My other i.p addresses come back cannot find network. My nvidia nforce networking contoller physical address shows-up in the ifconfig but the ppp.adapter dsl physical address is nowhere to be seen. I wish I could give you the correct information to fix this problem but I think it is going to take some more questions from you to find the right answers. Thanks again for spending time on this problem.

---

### Post by The Uniphobiac on 2006-08-10
I assume your modem is doing the PPPoE connection, what does ifconfig show as your IP?

---

### Post by wfwh3rd on 2006-08-10
The only ip addresses I get back is on the lo: local loopback: inet addr:127.0.01 & mask: 255.0.0.0. The inet6 addr:: 1/128 scope: Host up loopback running. On the eth0, I get the Hwaddr: 00:15:58:36:B0:62 and the inet6: fe80:215:58ff:fe36:b062/64. I believe my ip addy for the ethernet adapter Local area connetion is 192.168.1.47 and the ip addy for ppp. adapter dsl is 64.223.237.87.  The two ip addresses above are from doing a ipconfig on xp but there is no ip addresses from the ifconfig on ubuntu except for the 127.0.0.01. Thanks for taking the time.

---

### Post by RRS on 2006-08-10
Generally most DSL modems handle the PPPoE configuration and act as a DHCP server.

Try setting eth0 to dhcp instead of running pppoeconf.

---

### Post by wfwh3rd on 2006-08-11
I have tried the dhcp tool in networking but I still get the same error message in firefox. thanks for the help but the answer must be somewhere else!

---

