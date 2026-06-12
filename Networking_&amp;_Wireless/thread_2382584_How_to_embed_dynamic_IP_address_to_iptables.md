---
title: "How to embed dynamic IP address to iptables?"
date: 2018-01-15
forum: Networking &amp; Wireless
---

### Post by vooteleaer on 2018-01-15
OK, here's the situation
I have one application, which sends udp data over OpenVPN connection to my server (192.168.1.2). And the problem is, it writes wrong source IP into udp packets, creating a big mess.
To correct the problem, I added following to iptables:
iptables -I POSTROUTING -t nat -p udp -d 192.168.1.2 --dport 14550 -j SNAT --to 192.168.1.5

The problem is, 192.168.1.5 is dynamic address of tap0 (OpenVPN TAP interface).
How to automatically substitute this ip to current one?
Obiously, this has to happen after OpenVPN connects to server.

---

### Post by vooteleaer on 2018-01-15
Is this script ok to call after openvpn connecting?
ip="$(ifconfig | grep -A 1 'tap0' | tail -1 | cut -d ':' -f 2 | cut -d ' ' -f 1)"
iptables -I POSTROUTING -t nat -p udp -d 192.168.1.2 --dport 14550 -j SNAT --to $ip

---

### Post by SeijiSensei on 2018-01-15
Create a file using vooteleaer's command like this
```

#!/bin/bash 
ip="$(ifconfig | grep -A 1 'tap0' | tail -1 | cut -d ':' -f 2 | cut -d ' ' -f 1)"
iptables -I POSTROUTING -t nat -p udp -d 192.168.1.2 --dport 14550 -j SNAT --to $ip

```
and mark it executable with chmod +x.  In the OpenVPN configuration file for this connection, use the "up" command to run the script when the VPN comes up. 
```
up /path/to/the/script
```

---

