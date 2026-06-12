---
title: "cannot reach local services"
date: 2017-07-11
forum: Networking &amp; Wireless
---

### Post by hundred1906 on 2017-07-11
Using my browser (firefox) I am unable to reach the admin page of my Linksys router from my Ubuntu 16.04 desktop via my wired LAN. I can get there from my wifi connected phone. Similarly I can no longer reach the web pages for services on my local file server.

The router is at 192.168.0.1

Somewhere/Sometime I have repaired/changed something and have not noticed the change in access capability because it is rarely used. I can access external services (Google, Ubuntu Forums, etc) so I have DNS capability via the router.

Right now my /etc/networks/interfaces file contains:

> # interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback



When I type 192.168.0.1 into the browser address page I get a blank page. But I can access it from my router wifi.

Ping responses are ok.

I am guessing that this is going to be a stupid error on my part but I can't find it as yet.

---

### Post by BenginM on 2017-07-12
[FONT=courier new]Salutations!

The contains of your /etc/networks/interfaces is identical to mine and it's the default . so at least we know so far  the interfaces and capabilities are workin' for the most part!

first i'd check the router ip gateway by running : $ route -n , and then route .. if it's [FONT=courier new]192.168.0.1 [/FONT]

I suppose you could Assign a static IP address manually .. While Ethernet cable attached , trun off the wifi and go to system settings **Network** -> **Wired**, then **select IPv4**, Addresses and select "**Manual"**, fill in the parameters like below, and click **Apply**.

[/FONT]```
[FONT=courier new]**IP Address:** 192.168.0.100
[/FONT]
[FONT=courier new]**Subnet Mask:** 255.255.255.0
[/FONT]
```
[FONT=courier new]
Make sure you type the router ip in the browser as 192.168.0.1 without http:// . later you should switch back the setting for wired to auto DHCP.


You might have to factory rest the router and start all over again on your settings. See your manual for details.
[/FONT]

---

### Post by hundred1906 on 2017-07-24
Thank you BenginM but the route trick showed the correct gateway. Found I could access the router by adding /admin to the address (192.168.0.1/admin). After that I can access it without the /admin - so I have no idea. Maybe power cycling at some stage has fixed it.

Turns out the server issue is about port 80 denial, so is a distinct problem with the server that I have not got to the bottom of yet.

I am marking this as solved.

---

