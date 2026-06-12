---
title: "[SOLVED] ADSL Modem &amp;gt; Computer1 &amp;gt; Computer2"
date: 2008-07-12
forum: Networking &amp; Wireless
---

### Post by thehkv on 2008-07-12
Hi everyone, I've just switched to ubuntu, and wanted my two computers to share internet connection as well as files.

I have an ADSL modem which provides my 1st computer with internet through a LAN wire. I have two lan cards in this computer, so that 1st can be used to connect to the modem and other one to another computer.
Configuration page of modem is accessed through 192.168.1.1
Now i want internet connection in the second computer as well as ability to share files between two computers. 

So I've assigned following settings to both the computers : 

> adsl modem
accessed by 192.168.1.1

1st comp 
ubuntu
	lan 1 [eth0] ( connected to modem)
		ip address : 192.168.1.2
		subnet mask: 255.255.255.0
		def gateway: 192.168.1.1
	lan 2 [eth1] ( connected to 2nd computer )
		ip address : 192.168.2.3
		subnet mask: 255.255.255.0
		def gateway: 192.168.1.2

2nd computer
ubuntu
	lan 1 [eth0] (connected to 1st computer)
		ip address : 192.168.2.4
		subnet mask: 255.255.255.0
		def gateway: 192.168.2.3

I'm able to ping 
192.168.2.4 from 1st computer
192.168.2.3 from 2nd computer
192.168.1.2 from 2nd computer
I cant ping 
192.168.1.1 from 2nd computer

So what changes do I need to do to
1. share internet
2. share files
I'm having Ubuntu 8.04 in both computers
Any help greatly appreciated, thanks in advance.

---

### Post by nixscripter on 2008-07-13
You have to set up forwarding the packets through the first computer. You might want to read this thread about IP masquerading:

[http://linux.about.com/od/ubusrv_doc/a/ubusg18t03.htm](http://linux.about.com/od/ubusrv_doc/a/ubusg18t03.htm)

Hope this helps.

---

### Post by thehkv on 2008-07-14
Got it, thanks :)

---

