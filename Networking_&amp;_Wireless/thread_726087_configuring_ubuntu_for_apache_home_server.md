---
title: "configuring ubuntu for apache home server"
date: 2008-03-16
forum: Networking &amp; Wireless
---

### Post by methodtwo on 2008-03-16
hi all.My setup at present is a hp pavillion dv2000 laptop running ubuntu 6.10 edgy eft that is connected to a router which in turn is connected to a cable modem.The router dynamically assigns my ip address from its pool of addresses.Am i right in thinking that i need to configure ubuntu and the router to use a static ip address in order for me to receive inbound requests for apache and to enable stable port forwarding from the router?.Therefore Please could someone tell me how to configure ubuntu-6.10 edgy to come up on the same static address for every boot.I mean the file(s) to put the static address in and the syntax for that file or failing that a way to configure this via a GUI.
Also if static(or is that sticky)dhcp is easier or preferable could someone tell me how to configure that.
Thankx in advance

---

### Post by superprash2003 on 2008-03-16
you can assign a static ip by using the command 
ifconfig eth0 192.168.1.10
where eth0 is your network adapter and 192.168.1.10 is the static ip

---

### Post by Iowan on 2008-03-17
Check your router manual - it may be possible to have it assign a static lease based on MAC address.

---

