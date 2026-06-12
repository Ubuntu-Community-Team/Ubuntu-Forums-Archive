---
title: "connection problem"
date: 2007-02-21
forum: Networking &amp; Wireless
---

### Post by sarwatj on 2007-02-21
Hi !
I am a total newbie and am having trouble with network connections
I have installed ubuntu lamp server in order to use the desktop I have used apt-get update and later apt-get install ubuntu-desktop both don’t work probably some error with the internet connection.

The internet connection is via (college’s)Lan I can successfully ping to this server. And parallel windows OS on this system can connect to the net.

During installation dhcp was not detected and static ips have been specified. 
Also usb is not mounted automatically here   

Please help…after viewing some google results cant see anything going anywhere if I cant get apt-get to work
:confused: :confused: :confused:

---

### Post by ukripper on 2007-02-21
> **sarwatj said:**
> Hi !
I am a total newbie and am having trouble with network connections
I have installed ubuntu lamp server in order to use the desktop I have used apt-get update and later apt-get install ubuntu-desktop both don&#8217;t work probably some error with the internet connection.

The internet connection is via (college&#8217;s)Lan I can successfully ping to this server. And parallel windows OS on this system can connect to the net.

During installation dhcp was not detected and static ips have been specified. 
Also usb is not mounted automatically here   

Please help&#8230;after viewing some google results cant see anything going anywhere if I cant get apt-get to work
:confused: :confused: :confused:

Paste your interfaces file here:
$ sudo gedit /etc/network/interfaces

---

