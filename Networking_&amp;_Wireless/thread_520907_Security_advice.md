---
title: "Security advice"
date: 2007-08-08
forum: Networking &amp; Wireless
---

### Post by woodr0w on 2007-08-08
Howdy, Id like to have some advice on setting up my network. First off let me give you guys and gals a little map on my setup.  6 computers , 3 Ubuntu, 1 OSX, 1 Gentoo, and 1 m$ win2k3 server " i know i should switch, but there are some applications i require that ONLY work in windows " basicaly all i really would like to do is make the windows machine total blind from the internet, either via host file, or some other means , I dont need it to access the internet, is there a way possible to configure a linksys router to BLOCK all incoming traffic from the internet to one IP while still allowing access to it from the lan/intranet ? thanks in advance !!!
:guitar:

---

### Post by solar george on 2007-08-08
From behind a router the internet can only access computers that you have allowed it to and then only the ports on that computer that you have specifically forwarded.

---

### Post by woodr0w on 2007-08-08
Router doesnt really stop internet traffic, or so as I understand them, because for one i can still ping say [www.yahoo.com](www.yahoo.com), i dont wont any way possible for that to happen. I dont quite know of a way to explain what im asking really.

---

### Post by splintercellguy on 2007-08-08
Just add a firewall rule in the router to block outgoing packets from the machine?

---

### Post by solar george on 2007-08-08
> Router doesnt really stop internet traffic

Sorry I thought you meant incoming traffic.

---

### Post by xzero1 on 2007-08-08
If you don't allow your blocked machine to get an IP address it cannot access the internet. It depends on how secure you want to be. If your machine cannot access the internet, then how will security and other patches be applied to it? The only way to be totally secure is to disconnect the machine from the network!

---

### Post by woodr0w on 2007-08-09
for example , if you setup an ftp server, you can restrict access to that particular port/service to just ONE ip address. There has to be a way to make a computer unavalible to the internet and still avalible to the intranet/lan . LIke i said, maybe im asking the question wrong :confused:

---

### Post by xzero1 on 2007-08-25
Let me try to clarify. A properly setup nat router will block all unsolicited incomming ip packets to the computers behind the router. How? It gives computer(s) on your network internal local network IP addresses that are not accessible from the internet say 10.10.10.1. Your computer will be isolated UNTIL it sends something out to the internet via the router which then expects a return and remembers what computer (local IP number) to send the return to. Note: many programs will access the internet without you knowing it but the communication is still initiated by your computer. 


> There has to be a way to make a computer unavalible to the internet and still avalible to the intranet/lan .

If you don't allow your computer a local IP (internet protocol) address then you cannot connect to the internet but you could use another protocol for internal network communication.

---

