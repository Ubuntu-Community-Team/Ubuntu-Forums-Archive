---
title: "[SOLVED] NAT problem?"
date: 2008-10-09
forum: Networking &amp; Wireless
---

### Post by StOoZ on 2008-10-09
im connecting to the web via ADSL , I set up my modem (also a router) that it will dial up automatically.
now bittorent says that I have a problem with the NAT , when I enter to the modem web-based configuration utility (10.0.0.138) , I see that it has NAT enabled , so what is the issue?

---

### Post by superprash2003 on 2008-10-09
please mention the model of your modem.. you need to open ports for bit torrent.. most routers have the virtual server option where you type in port no and the pc where you want the port to be forwarded to.. if your modem has virtual server option then you can try this to open ports [http://prash-babu.blogspot.com/2008/05/portforwarding-through-virtual-server.html](http://prash-babu.blogspot.com/2008/05/portforwarding-through-virtual-server.html)
if not it should have NAT-DMZ.. then try this [http://prash-babu.blogspot.com/2008/04/port-forwarding-in-ut300r2u-adsl-modem.html](http://prash-babu.blogspot.com/2008/04/port-forwarding-in-ut300r2u-adsl-modem.html)

---

### Post by StOoZ on 2008-10-09
ok to be more precise :
I have a Aztech DSL600E , which set to PPPoE to dial up automatically , to it , I connect another wireless router , which physically connected to my PC (not wirelessly) , now Im getting lowID on emule , bad NAT on torrents... I have no idea what to do.
so in this case , both the wireless router and the modem (which is also a router) should be configured right?

---

### Post by StOoZ on 2008-10-10
soved it with DMZ from the modem to the router , and then again DMZ to the static ip of the computer.

---

