---
title: "Wireless Keeps Conking Out"
date: 2008-07-22
forum: Networking &amp; Wireless
---

### Post by slugicide on 2008-07-22
It looks like my connection to the wireless modem causes it to freak out and reset (it happens whenever I need to download anything more than a small Web page).  I wouldn't suspect it was Ubuntu, except my computer is the only one that causes this.  Here is the modem log, in case anyone can tell me if it's me or if I should call the cable guy.  Thanks for bothering!

```
Time  	Priority  	Description
 2008-07-22 12:20:03 	 critical 	 No UCD's Received - Timeout 
 2008-07-22 12:19:52 	 critical 	 SYNC Timing Synchronization failure - Failed to acquire QAM/QPSK symbol timing 
 2008-07-22 12:19:51 	 critical 	 SYNC Timing Synchronization failure - Failed to acquire FEC framing 
 2008-07-22 12:11:26 	 critical 	 Received Response to Broadcast Maintenance Request, But no Unicast Maintenance opportunities received - T4 timeout 
 2008-07-22 12:00:32 	 critical 	 No UCD's Received - Timeout 
 2008-07-22 11:55:42 	 critical 	 Received Response to Broadcast Maintenance Request, But no Unicast Maintenance opportunities received - T4 timeout 
 2008-07-22 11:12:39 	 critical 	 No UCD's Received - Timeout 
 2008-07-22 11:10:38 	 critical 	 Received Response to Broadcast Maintenance Request, But no Unicast Maintenance opportunities received - T4 timeout 
 2008-07-22 10:57:51 	 critical 	 No UCD's Received - Timeout 
 2008-07-22 10:53:45 	 critical 	 Received Response to Broadcast Maintenance Request, But no Unicast Maintenance opportunities received - T4 timeout 
 2008-07-22 09:03:25 	 critical 	 No UCD's Received - Timeout 
 2008-07-22 08:59:19 	 critical 	 Received Response to Broadcast Maintenance Request, But no Unicast Maintenance opportunities received - T4 timeout 
 2008-07-21 11:47:37 	 critical 	 No UCD's Received - Timeout 
 2008-07-21 11:03:10 	 critical 	 Received Response to Broadcast Maintenance Request, But no Unicast Maintenance opportunities received - T4 timeout 
 2008-07-21 10:49:04 	 critical 	 No UCD's Received - Timeout 
 2008-07-21 10:43:51 	 critical 	 Received Response to Broadcast Maintenance Request, But no Unicast Maintenance opportunities received - T4 timeout 
 2008-07-20 09:30:27 	 critical 	 No UCD's Received - Timeout 
 2008-07-20 09:24:52 	 critical 	 Received Response to Broadcast Maintenance Request, But no Unicast Maintenance opportunities received - T4 timeout 
 2008-07-19 22:59:59 	 critical 	 No UCD's Received - Timeout 
 2008-07-19 22:54:56 	 critical 	 Received Response to Broadcast Maintenance Request, But no Unicast Maintenance opportunities received - T4 timeout 
 2008-07-18 23:15:17 	 critical 	 No UCD's Received - Timeout 
 2008-07-18 10:43:08 	 critical 	 Received Response to Broadcast Maintenance Request, But no Unicast Maintenance opportunities received - T4 timeout 
 2008-07-18 09:15:00 	 critical 	 No UCD's Received - Timeout 
 2008-07-18 09:10:32 	 critical 	 Received Response to Broadcast Maintenance Request, But no Unicast Maintenance opportunities received - T4 timeout 
 2008-07-18 09:02:31 	 critical 	 No UCD's Received - Timeout 
 2008-07-18 08:59:00 	 critical 	 Received Response to Broadcast Maintenance Request, But no Unicast Maintenance opportunities received - T4 timeout 
 1970-01-01 00:00:27 	 critical 	 No Ranging Response received - T3 time-out 
 1970-01-01 00:00:10 	 critical 	 No Ranging Response received - T3 time-out 
```

---

### Post by slugicide on 2008-07-23
Can anyone tell me where the problem lies here?

---

### Post by stevenius on 2009-12-17
I'm having the exact same problem. I have a Sony VAIO with an Intel PRO 3945ABG integrated wireless card. I'm using Ubuntu 9.10, and I have reason to suspect the drivers are the source of the problem because I also have 9.10 on a desktop with a different wireless card (a Broadcom variant) that doesn't exhibit this problem.

I'm fairly sure this is an Ubuntu-specific driver issue because I'm using the same computer now (via Windows 7) and there are no problems. I'm also able to connect directly to my cable modem in Ubuntu via Ethernet without issue. This just started happening today, in fact; I was having a problem with the network manager not automatically connecting to my hidden wireless network and somehow today it miraculously works.

Did you find a solution to the problem?

---

