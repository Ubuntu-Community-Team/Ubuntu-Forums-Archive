---
title: "Iptables port forwarding through ICS"
date: 2008-11-22
forum: Networking &amp; Wireless
---

### Post by Tom--d on 2008-11-22
Hello,

I need some or all (if possible) ports forward from wlan0 (My internet) to eth0 (My Ethernet card which is connected to the Xbox360).
I need 88 (UDP), 3074 (UDP), and 3074 (TCP) all forwarded to eth0 (thus the 360). I will forward them in my router as well.
I do my ICS through Iptables in the command line (more of a script).
I have a static IP on eth0 and as well as my Xbox360. My Wireless card is Static.

Here is he script:
```
#!/bin/bash

sudo ifconfig eth0 192.168.0.1
sudo iptables -A FORWARD -i wlan0 -o eth0 -s 192.168.0.0/24 -m state --state NEW -j ACCEPT
sudo iptables -A FORWARD -m state --state ESTABLISHED,RELATED -j ACCEPT
sudo iptables -A POSTROUTING -t nat -j MASQUERADE
sudo sh -c "echo 1 > /proc/sys/net/ipv4/ip_forward"
```

It works, but the connection is poor due to the xbox needs ports opened, which at the moment aren't.

IP of the Xbox is:
IP: 192.168.0.2
Subnet: 255.255.255.0
Gateway: 192.168.0.1

Eth0:
IP:192.168.0.1
Subnet: 255.255.255.0
Gateway: 0.0.0.0

wlan0:
IP: 192.168.1.2
Subnet: 255.255.255.0
Gateway: 192.168.1.1

Could someone please help my forward all my ports on wlan0 to eth0.
Thanks! :)

---

### Post by puppywhacker on 2008-11-22
These rules are the contain the ingredients, but I can't test them, so start troubleshooting from there. goodluck

```

iptables -A FORWARD -i wlan0 -d 192.168.0.2 -p tcp --dport 3074 -j ACCEPT
iptables -t nat -A PREROUTING -p tcp -i wlan0 -d 192.168.0.2 --dport 3074 -j DNAT --to 192.168.0.2:3074

iptables -A FORWARD -i wlan0 -d 192.168.0.2 -p udp --dport 88 -j ACCEPT
iptables -t nat -A PREROUTING -p udp -i wlan0 -d 192.168.0.2 --dport 88 -j DNAT --to 192.168.0.2:88

iptables -A FORWARD -i wlan0 -d 192.168.0.2 -p udp --dport 3074 -j ACCEPT
iptables -t nat -A PREROUTING -p udp -i wlan0 -d 192.168.0.2 --dport 3074 -j DNAT --to 192.168.0.2:3074

```

---

### Post by Tom--d on 2008-11-22
> **puppywhacker said:**
> These rules are the contain the ingredients, but I can't test them, so start troubleshooting from there. goodluck

```

iptables -A FORWARD -i wlan0 -d 192.168.0.2 -p tcp --dport 3074 -j ACCEPT
iptables -t nat -A PREROUTING -p tcp -i wlan0 -d 192.168.0.2 --dport 3074 -j DNAT --to 192.168.0.2:3074

iptables -A FORWARD -i wlan0 -d 192.168.0.2 -p udp --dport 88 -j ACCEPT
iptables -t nat -A PREROUTING -p udp -i wlan0 -d 192.168.0.2 --dport 88 -j DNAT --to 192.168.0.2:88

iptables -A FORWARD -i wlan0 -d 192.168.0.2 -p udp --dport 3074 -j ACCEPT
iptables -t nat -A PREROUTING -p udp -i wlan0 -d 192.168.0.2 --dport 3074 -j DNAT --to 192.168.0.2:3074

```

Thanks but my Xbox still says the NAT is strict (which makes it really slow connecting to people).
How can I make it better?
Can I forward everything from wlan0 to eth0? and allow everything to and from eth0?

---

### Post by puppywhacker on 2008-11-22
You could bridge your ethernet interface into a virtual br0 interface like described in one of the [HOWTO's]("http://tldp.org/HOWTO/Ethernet-Bridge-netfilter-HOWTO-3.html")

Install the bridge-utils, flush your iptables and reconfigure your interfaces

apt-get install bridge-utils

---

### Post by Tom--d on 2008-11-22
I followed that howto and I don't know if it worked :S because.. I had no internet from my wireless (Use wifi-radar to connect and it did. but no internet (or there was just it was blocked because I did something wrong?)

Br0 was up, so was eth0 and wlan0 (I guess under br0?)

Whats the benfits of bridging and can you give me baby steps on how to do it ;)

Thanks :)

---

