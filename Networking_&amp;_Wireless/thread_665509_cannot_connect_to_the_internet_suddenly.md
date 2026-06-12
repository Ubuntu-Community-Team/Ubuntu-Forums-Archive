---
title: "cannot connect to the internet suddenly"
date: 2008-01-12
forum: Networking &amp; Wireless
---

### Post by Setee on 2008-01-12
I have connected to the internet before. If been using ubuntu for a few months without error. The only out of place thing me and my bro could find is under eth0:avah. It says my inet addr is 169.254.6.204 that my bcast is 169.254.255.255 and that my mask is 255.255.0.0. The thing is my router adresses should be 192.168.1.2-9

---

### Post by amo-ej1 on 2008-01-12
You have received an ip address that lies in the so called APIPA range (see [http://compnetworking.about.com/cs/protocolsdhcp/g/bldef_apipa.htm](http://compnetworking.about.com/cs/protocolsdhcp/g/bldef_apipa.htm) ) this happens (more often on windows than on linux) when no dhcp lease was received within an amount of time. So you should check your cabling and if the other end is handing out ip addresses.

---

### Post by Setee on 2008-01-12
Thanks slot man

---

