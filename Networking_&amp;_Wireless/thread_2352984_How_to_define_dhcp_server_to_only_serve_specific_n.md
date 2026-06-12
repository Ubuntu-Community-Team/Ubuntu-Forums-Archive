---
title: "How to define dhcp server to only serve specific nic"
date: 2017-02-17
forum: Networking &amp; Wireless
---

### Post by Tadaen_Sylvermane on 2017-02-17
I'm looking at a guide to add a squid transparent proxy to my network. [http://www.purplealienplanet.com/node/25](http://www.purplealienplanet.com/node/25) is the guide I am looking into. What I need though since everything is on a common switch, how can I instruct the dhcp server (using isc-dhcp-server) to only serve dhcp addresses on the virtual network interface. In my case enp2s0:0. Not on the default enp2s0. I don't want to knock out the network at my home as it is serving a number of smaller apartments on my property (grandparents, parents, and my place on a shared piece of land). I need to get it right the first time.

---

### Post by papibe on 2017-02-17
Hi Tadaen_Sylvermane.

You should be able to list the interfaces you want to serve in this file:
```
/etc/default/isc-dhcp-server
```
Look for the line that looks like this:
```
INTERFACES=""
```
and change it appropriately. For example:
```
INTERFACES="enp2s0:0" 
```
Then restart the dhcp ervice:
```
sudo systemctl restart isc-dhcp-server.service
```
Hope it helps. Let us know how it goes.
Regards

---

### Post by Tadaen_Sylvermane on 2017-02-17
Thank you. I figured that was it but wanted to be sure, as mentioned gotta get it right the first time :) thank you very much.

---

