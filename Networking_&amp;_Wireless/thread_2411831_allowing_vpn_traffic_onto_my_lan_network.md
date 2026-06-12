---
title: "allowing vpn traffic onto my lan network"
date: 2019-02-04
forum: Networking &amp; Wireless
---

### Post by sniper8752 on 2019-02-04
I have openvpn running on my ubuntu server, with iptables. I am able to vpn into my server. I notice that the client (my phone) grabs a valid IP, but it can't contact anything. I tried pinging the host from the server, and it responded. I could not ping 10.8.0.1 from the client device. 
```
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface0.0.0.0         <external, 75.x address>      0.0.0.0         UG    0      0        0 p2p1
10.8.0.0        10.8.0.2        255.255.255.0   UG    0      0        0 tun0
10.8.0.2        0.0.0.0         255.255.255.255 UH    0      0        0 tun0
<external, 75.x address>      0.0.0.0         255.255.248.0   U     0      0        0 p2p1
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 p5p1

```
I have a tun0 interface, at 10.8.0.1.
Weird thing is, when I view devices on my lan on the client, I see the server, but it times out, or something like that. 
I've added a few rules to my iptables to try and get it to work (input, forward, and output):
```
ACCEPT     all  --  anywhere             anywhere             state RELATED,ESTABLISHED
ACCEPT     all  --  anywhere             anywhere             state NEW,RELATED,ESTABLISHED
ACCEPT     all  --  anywhere             anywhere             state NEW,RELATED,ESTABLISHED
```

---

### Post by SeijiSensei on 2019-02-04
Did you enable IPv4 forwarding in the file /etc/sysctl.conf?  By default Ubuntu (and most other distros) will not forward packets between interfaces for security reasons.

If you run the command "cat /proc/sys/net/ipv4/ip_forward" and get a zero in response, then forwarding is disabled.  Remove the hash mark (as root with sudo) from the beginning of the line in /etc/sysctl.conf that reads

```
net.ipv4.ip_forward=1
```

and reboot.  Any better?

---

### Post by sniper8752 on 2019-02-04
It is already set to 1.

---

### Post by The Cog on 2019-02-04
Your iptables rules look wrong to me (if that's all of them). Please post the complete output of the command **sudo iptables-save**. And please include the command you type - it really helps when diagnosing issues.

---

### Post by sniper8752 on 2019-02-09
Sorry, but I would rather not paste my FULL iptables. I can share with you relevant information though. The default policy is to drop. I have no drop rules. The relevant rules for this issue include (after doing the "sudo iptables -L" command):

```

INPUT
ACCEPT     udp  --  anywhere             anywhere             state NEW,ESTABLISHED udp dpt:openvpn

OUTPUT
ACCEPT     udp  --  anywhere             anywhere             state ESTABLISHED udp spt:openvpn


```

What ports should I be aware of, or look for?

---

### Post by sniper8752 on 2019-02-12
*bump*

---

### Post by SeijiSensei on 2019-02-13
Remove all the iptables rules.  Does it work then?

---

