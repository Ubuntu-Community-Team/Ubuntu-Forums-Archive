---
title: "DHCP &amp; DNS Management Software"
date: 2014-07-22
forum: Networking &amp; Wireless
---

### Post by oxsyn on 2014-07-22
I just received an enterprise class firewall (Cisco ASA) for my home (I work from home) network. My personal class firewall had features for static DHCP bindings based on MAC addresses and local DNS resolution - however this firewall does not - so I'll need to setup a separate server.

I will probably use Ubuntu - does anyone have any recommendations for any web-based management applications for DHCP & DNS services?

---

### Post by bab1 on 2014-07-22
> **oxsyn said:**
> I just received an enterprise class firewall (Cisco ASA) for my home (I work from home) network. My personal class firewall had features for static DHCP bindings based on MAC addresses and local DNS resolution - however this firewall does not - so I'll need to setup a separate server.

I will probably use Ubuntu - does anyone have any recommendations for any web-based management applications for DHCP & DNS services?

I believe you can handle DHCP reservations via MAC address in a Cisco ASA unless it is a Cisco ASA 5505 (maybe).  See [here]("http://www.bigsoft.co.uk/blog/index.php/2013/02/02/configuring-a-permanant-dhcp-reservation-on-a-cisco-asa-pix").  See [http://ccie-or-null.net/2013/02/06/dhcp-reservations-on-a-cisco-asa-5505-maybe/](http://ccie-or-null.net/2013/02/06/dhcp-reservations-on-a-cisco-asa-5505-maybe/) for the Cisco ASA 5505 limitation.  A quick [Google Search]("https://www.google.com/search?client=ubuntu&channel=fs&q=Cisco+ASA&ie=utf-8&oe=utf-8#channel=fs&q=cisco+asa+dhcp+reservation") reveals lots to read.

On the other hand if you are managing a small home network it might be just as easy to set static IP addresses at each host and use /etc/host files for IP to hostname resolution.  Apple, Windows and Linux all understand /etc/hosts

---

### Post by oxsyn on 2014-07-22
It's a 5512-X. Yeah, I saw the static arp workaround, but it still won't do DDNS (which I would really like to have again) and I'd like to have some kind of management app for configuring the bindings - though copy and paste to the CLI from a text file is certainly easy.
There's ~ 40 devices on the network, I'm using /etc/hosts atm, but it's really not fun to maintain and still won't allow for DDNS updates w/ DHCP.

Honestly, your solution may be the best and it may be what I end up going with - I'm hoping to try get something a little more sophisticated up and running though.
ATM I'm looking at this: [http://www.gestioip.net/](http://www.gestioip.net/).

---

### Post by bab1 on 2014-07-22
> **oxsyn said:**
> It's a 5512-X. Yeah, I saw the static arp workaround, but it still won't do DDNS (which I would really like to have again) and I'd like to have some kind of management app for configuring the bindings - though copy and paste to the CLI from a text file is certainly easy.
There's ~ 40 devices on the network, I'm using /etc/hosts atm, but it's really not fun to maintain and still won't allow for DDNS updates w/ DHCP.

Honestly, your solution may be the best and it may be what I end up going with - I'm hoping to try get something a little more sophisticated up and running though.
ATM I'm looking at this: [http://www.gestioip.net/](http://www.gestioip.net/).

Have you thought of Cisco's Adaptive Security Device Manager (ASDM)?  See [here]("http://www.cisco.com/c/en/us/products/security/adaptive-security-device-manager/index.html").

---

