---
title: "sharing wireless network card"
date: 2008-11-30
forum: Networking &amp; Wireless
---

### Post by dmcbob on 2008-11-30
I have a computer which I'd like to hook up to the net, via its connection to another computer (i.e. share the second computer's wireless NIC). Is this possible?

My setup is as follows:
COMPUTER1 ---- wired router1  ---- COMPUTER2 ------wireless router2 to the internet 

I only have the one wireless usb key, so I'd like to somehow divide its internet connection between the computers. Wiring computer1 to the wireless router is not an option.

Thanks for any help.

---

### Post by Tom--d on 2008-11-30
Best bet is to install firestarter (the easy way) and enable internet connection sharing.

The other way is through manual (easy actually).

on computer2, put this in /etc/rc.local
```
ifconfig eth0 192.168.0.1
iptables -A FORWARD -i wlan0 -o eth0 -s 192.168.0.0/24 -m state --state NEW -j ACCEPT
iptables -A FORWARD -m state --state ESTABLISHED,RELATED -j ACCEPT
iptables -A POSTROUTING -t nat -j MASQUERADE
sh -c "echo 1 > /proc/sys/net/ipv4/ip_forward"
```

And then in computer 1, you will need a static ip.

IP: 192.168.0.2
subnet: 255.255.255.0
Gateway: 192.168.0.1
DNS: Your dns severs from computer2.

That should do it.

---

### Post by dmcbob on 2008-11-30
Thanks for the reply.

I guess I had the wrong idea originally. I had router1 at 192.168.0.1 and router2 at 192.168.1.1.

To try to conform with what you said, I changed router1 to have address 192.168.1.12 and no longer function as a DHCP server. I also put router1 in "Router mode" from "Gateway mode".

Computer1 is at 192.168.1.13 via static IP. Computer2 eth0 is assigned 192.168.1.1 (as is router2).

Does this seem right? It's not working yet, but I just want to know whether the above setup is at all what you're proposing.

---

### Post by Tom--d on 2008-11-30
You need the Computer1 to be on a seperate Subnet.

For example:
Computer1: 192.168.1.3
Computer2: 192.168.1.2

Will not work!

however, this will:
Computer1: 192.168.0.2
Computer2: 192.168.1.2

---

