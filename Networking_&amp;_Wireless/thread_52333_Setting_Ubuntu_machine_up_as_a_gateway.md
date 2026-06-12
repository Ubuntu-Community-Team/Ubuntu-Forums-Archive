---
title: "Setting Ubuntu machine up as a gateway"
date: 2005-07-27
forum: Networking &amp; Wireless
---

### Post by joker5000 on 2005-07-27
I have very recently switched over to Ubuntu from WinXP.

I was wondering if it was possible (and easy) to share a network connection through this machine.

I have two network cards installed in it and one is connected to another computer via cross-over cable and the other NIC is connected to a DSL modem.

Any help would be greatly appreciated.

---

### Post by PhilippWollermann on 2005-07-27
Hi,

unfortunately I don't know a secure and simple one-click solution for sharing the internet access.. but there is Shorewall ([http://www.shorewall.net/)](http://www.shorewall.net/)), which isn't that hard to configure (you have to read the very good documentation) and worked perfectly, when I sat up a router for my home network. If there is any Ubuntu-specific solution, I unfortunately do not know about it, yet. :)

Philipp

---

### Post by tom-ubuntu on 2005-07-27
Setup both of your network cards and then install firestarter; it includes a wizard for internet connection sharing. 

You can also setup firewall rules graphically, and it includes also a DCHP server, I think. But haven't tried this. The rest work like a charme and is really easy to setup.

[http://www.fs-security.com/](http://www.fs-security.com/)

---

### Post by joker5000 on 2005-07-27
Thank you both for the speedy reply!

---

