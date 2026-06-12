---
title: "Help! wrt54g died, need help setting up a temp ad-hoc"
date: 2007-06-07
forum: Networking &amp; Wireless
---

### Post by phin on 2007-06-07
Ok, so i have a wrt54g v1.0 Router with dd-wrt on it. for some reason now when i go to plug it in, it does nothing, no lights, or sometimes the lights blink really quick and then die. I'm assuming it's dead.

So until i can get some extra money to buy a new one, i need to setup a temp ad-hoc or ap setup with my ubuntu box.

what i have is a headless ubutu edgy server box connected to the network that i use just for misc stuff and my screened irssi setup. after digging in some boxes i found a usr 54g usb adaptor that i have, model 5422.

so i went and tried to set the thing in ap mode, no luck, so i tried ad-hoc and it seemed to work but i cannot connect to it from my ubuntu feisty laptop via network manager.

this is what i did to get things going...

iwconfig eth1 mode Ad-Hoc
iwconfig eth1 essid Junglist
modprobe iptable_nat
iptables -t nat -A POSTROUTING -o eth0 -j MASQUERADE
echo 1 > /proc/sys/net/ipv4/ip_forward

no luck. also, can i just set this into ap mode somehow? 

what seems to be the issue is that i cannot force my laptop's network manager mode to work, i also tried installing network manager on the edgy server but seems there are no cli utils. i will remove if thats the improper route to go.

any help or step by step instructions would help, as i just need some wifi in my room!!

---

### Post by spd106 on 2007-06-08
So you say the USB wifi adaptor is a usr 5422, is that the one with a prism54 chip? 

You don't say what chip/driver your laptop has. If it's using ndiswrapper then it will probably work in adhoc mode. I suggest you kill Network Manager and use the cli, it's far more reliable for me.

Obligatory wiki link [https://help.ubuntu.com/community/WifiDocs/Adhoc](https://help.ubuntu.com/community/WifiDocs/Adhoc)

---

