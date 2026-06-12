---
title: "Ethernet wi-fi adapter automatic configuration"
date: 2021-10-16
forum: Networking &amp; Wireless
---

### Post by cardinalidiego on 2021-10-16
[h=1]20.04 Kde user here: I usually get online using my android phone as a tethering wifi hotspot. I have a TP-Link [TL-wa501g]("https://www.tp-link.com/it/support/download/tl-wa501g/") repeater that I don't use as a repeater, but as a client: it's basically a device with an ethernet port that can connect to wi-fi. I can easily reach that device as a router, through its ip, and if I manually configure dns, my ip and gateway ip (the latter changes everytime) it works rather smoothly. Oddly, the same pc configures itself perfectly when I work with the win10 installation, but when I'm using linux And I set the connection to auto configure itself I get the message "this device seems to be connected to a network but it can't reach internet", and with the command 
ip a
I can see it didn't get any ipv4 assigned. Anybody has any idea about how I can make dhcp work, or at least why it doesn't? After all this time I'm even curious![/h]
I've tried with other distros and got the same result

---

