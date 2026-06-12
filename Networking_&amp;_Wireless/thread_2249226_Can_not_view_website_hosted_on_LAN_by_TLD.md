---
title: "Can not view website hosted on LAN by TLD"
date: 2014-10-20
forum: Networking &amp; Wireless
---

### Post by barroncm on 2014-10-20
You can view the website outside the local network, but when I am connected to the same network the server is I can not view the page. How ever I can ping the domain name from inside the network with no issues.
So here is the setup:

Server A Hosts the website in question, as well as isc-dhcp-server, and some other stuff that is unrelated.
Server B Hosts more stuff that is unrelated.
Laptop A
Laptop B
Desktop A
Router A
Router B
Router C
Router D
(BIG HOUSE)
All routers point back to Server A for DHCP leases and share the same SSID and PW on Different channels.
All Routers are also running DD-WRT
Router A (Gateway) has NAT port forwards to the appropriate IP's.
All devices can surf the web without issue
Im sure I am missing something small that is preventing me from viewing my website by url but dont know what it is, any ideas would be appreciated.

Chris

---

### Post by barroncm on 2014-10-21
BUMP

No Ideas anyone?

---

### Post by sandyd on 2014-10-21
> **barroncm said:**
> BUMP

No Ideas anyone?

Do you have hairpin nat setup?

If you don't, consider either using hairpin nat, or a local DNS server such as dnsmasq. Without hairpin NAT, the gateway will not route requests to the servers on the network properly.

For hairpin NAT on dd-wrt, see [http://arstechnica.com/civis/viewtopic.php?p=1106767#p1106767](http://arstechnica.com/civis/viewtopic.php?p=1106767#p1106767)

---

### Post by papibe on 2014-10-21
Hi barroncm. Welcome to the forum ):P

The ability to connect to a machine from your local network using its public name, or IP, is called **NAT loopback** (read about it [here]("http://opensimulator.org/wiki/NAT_Loopback_Routers")). This an advance feature and it is not supported by most consumer routers.

Nevertheless, I believe DD-WRT does support it. I would start by checking DD-WRT's documentation and forums to learn how to do it.

Note that you could easily access the server from inside the LAN either using its LAN short name, or its LAN IP (e.g. 192.168.1.50).

I hope that helps. Let us know how it goes.
Regards.

---

### Post by barroncm on 2014-10-24
So after a few days of not being able to mess with this issue, I have it resolved. In dd-wrt Filter WAN NAT Redirection MUST be unchecked and a reboot of the router is preferred. I also turned off SPI Firewall, I had toyed with and attempted to do my own DNS server and lets just say things did not go well. Alas a project for another time.
Thanks for the replies.

---

