---
title: "send a website request through nat?"
date: 2008-09-04
forum: Networking &amp; Wireless
---

### Post by tumandro on 2008-09-04
I have a server running a VM for my enterprise program at MTU. I cannot get a bridged connection for this VM because the school doesn't want to give me a second IP address, so I have the license server that's required to run on Windows on a NAT behind the linux box. In order to get to use this license, you have to use the web portal (IE: [http://yourhostname/example](http://yourhostname/example)) to connect. However I cannot seem to get it to send through to the vm using iptables. The script I'm using to configure it is as follows:

#!/bin/sh

iptables -t nat -A PREROUTING -i eth0 -p tcp  --dport 80 -j DNAT --to-destination 192.168.1.3

iptables -I FORWARD -p tcp -d 192.168.1.3 --dport 80 -j ACCEPT

Anyone have any suggestions? Also can I make the starting port say 4020 instead of 80? I have a few websites running on the linux box that I can't have going back to the other machine.

---

