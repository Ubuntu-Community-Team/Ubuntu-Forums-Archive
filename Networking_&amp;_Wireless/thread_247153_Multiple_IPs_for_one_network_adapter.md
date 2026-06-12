---
title: "Multiple IPs for one network adapter"
date: 2006-08-30
forum: Networking &amp; Wireless
---

### Post by jmirick on 2006-08-30
I can't figure out how to assign more than one IP to a network adapter.  The System | Administration | Networking panel just gives you room for one IP, yet to serve multiple SSL websites from one Apache I need the adapter, and hence Apache, to respond to more than one IP.  We're doing this now on Windows, in the Network Properties, you can just list all the IPs that it should respond to, but I can't find the comparable place in Ubuntu.

I appologize in advance if this is somehwere obvious and I have just overlooked it.  :)

---

### Post by WhimpyPeon on 2006-08-30
You will want to alias the interface:
(ie eth0:0 eth0:1 ...)

See this link:

[http://www.cyberciti.biz/tips/ubuntu-linux-creating-ethernet-alias-for-eth0-network-device.html](http://www.cyberciti.biz/tips/ubuntu-linux-creating-ethernet-alias-for-eth0-network-device.html)

---

### Post by jmirick on 2006-08-30
Thank you kindly.  I would sponsor you to be promoted to "a full percolator" instead of "first cup".

---

