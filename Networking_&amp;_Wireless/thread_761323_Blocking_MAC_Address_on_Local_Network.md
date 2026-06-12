---
title: "Blocking MAC Address on Local Network"
date: 2008-04-21
forum: Networking &amp; Wireless
---

### Post by goandeatsomestuff on 2008-04-21
Hello, I've been searching for hours and have not found a solution to my problem that works.  My network has a linux-based router that handles shaping (wshaper2) and DHCP duties (ipmasq).  I have a computer on my own network that is causing severe bandwidth issues and am trying to simply stop the flow of all traffic to and from his computer.

Using ipmasq, I couldn't find an appropriate .rul file to block traffic to/from his ip/MAC, and I tried the following commands to no avail:
iptables -A INPUT -m mac --mac-source 00:13:a9:c3:ae:8f -j DROP
iptables -A OUTPUT -m mac --mac-source 00:13:a9:c3:ae:8f -j DROP
iptables -A INPUT -j DROP -i eth1 -d 192.168.0.194
iptables -A OUTPUT -j DROP -o eth1 -d 192.168.0.194
iptables -A INPUT -j DROP -i eth0 -d 192.168.0.194
iptables -A OUTPUT -j DROP -o eth0 -d 192.168.0.194

eth1 goes to the modem, and eth0 goes to the switch.  If you can give any help, it's much appreciated!

---

### Post by Kevbert on 2008-04-21
If you go into your router setup (something like [http://192.168.0.1](http://192.168.0.1)) you may be able set an option to allow only certain MAC addresses.  I've done this with my wireless router as there are about 10 wireless networks that I can pick up and if I can see them then they can probably see me.

---

### Post by goandeatsomestuff on 2008-04-21
Kevbert, thanks for your input, but my linux machine is my router, and I don't want to allow only certain MAC Addresses, I want to stop traffic from flowing to a specific one.

---

### Post by mpokrywka on 2008-04-21
Use:
```

iptables -t raw -A PREROUTING -i eth0 -m mac --mac-source 00:13:a9:c3:ae:8f -j DROP

```

I suggest using raw table to drop packets before they even reach kernel's connection tracking.
This is poor man's solution against determined users but better than nothing.

Your rules didn't work because INPUT and OUTPUT works for packets that are destined FOR this machine. If packets are only routed then you can use "FORWARD" iptables chain (there are also PREROUTING and POSTROUTING chains that applies for all packets - at least in "mangle" table, "nat" table is completely different story).

---

