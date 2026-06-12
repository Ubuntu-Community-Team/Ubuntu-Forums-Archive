---
title: "webmin, port forwarding"
date: 2008-07-20
forum: Networking &amp; Wireless
---

### Post by longcatspace on 2008-07-20
i use ubuntu 8.04 through webmin 1.410 to route the internet in this flat

i need to forward the UDP port 58116 to my XP machine,

so i 1st gave my XP machine a static IP address in the DHCP server part of webmin

then i went to the linux firewall part of webmin the "network address translation" IPtable,

i put a rule into the "packets before routing" (PRE-ROUTING)

in "Chain and action details"

action to take is: Destination NAT
IP's & Ports for DNAT is: IP range 192.168.0.5 (XP box) Port range 58116

and then in "Condition Details"

Network PROTOCOL = udp
source TCP or UDP port = 58116

it's not working and i don't know why... any help?

x

---

### Post by kevdog on 2008-07-20
Are you trying to internet connection share?


Just wondering so I can understand first what you want to do before typing a bunch of illrelevent info.

---

### Post by longcatspace on 2008-07-20
i already share the internet with webmin,

what i'm trying to do is use something called digital musician.net...

with cubase on my XP box, to receive a connection from the world and record from the internet,

it sets up a peer to peer connection between computers...

and to recieve a connection you need to have UDP port 58116 forwarded to the XP box with cubase,

so, being as my ubuntu box is my router, i'm trying to make webmin forward that port x

---

