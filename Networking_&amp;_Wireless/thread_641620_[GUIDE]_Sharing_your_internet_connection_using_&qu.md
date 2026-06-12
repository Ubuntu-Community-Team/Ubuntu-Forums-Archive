---
title: "[GUIDE] Sharing your internet connection using &quot;ip route add&quot;"
date: 2007-12-15
forum: Networking &amp; Wireless
---

### Post by komputes on 2007-12-15
I was given these instructions to share my internet connection. This is not bridging but masquerading which is great if you do not have a DHCPd running and your ISP only gives you 1 IP address.
[CENTER]
**[CENTER]Material needed:[/CENTER]**
-2 computers (one computer must have 2 network interfaces)
-Crossover cable (special cable that allows two computes to talk to each other)

Your connection will look like this:

**[CENTER][modem]====>(eth0)[PC1](eth1)====>(eth0)[PC2][/CENTER]**
*note: perhaps your ethernet controllers have different numbers, simply replace them below:*
[/CENTER]

Open a terminal window on both machines.

ON PC1
```

sudo iptables -F
sudo iptables -t nat -F
sudo iptables -X
sudo iptables -t nat -X

```

Masquerade access to INTERNAL
```
sudo iptables -t nat -A POSTROUTING -o eth0 -j MASQUERADE
sudo iptables -A FORWARD -i eth1 -j ACCEPT
```

```
echo 1 | sudo tee /proc/sys/net/ipv4/ip_forward
sudo ifconfig eth1 192.168.5.1 netmask 255.255.255.0 broadcast 192.168.5.255 up

```

ON PC2
```
sudo ifconfig eth0 192.168.5.2 netmask 255.255.255.0 broadcast 192.168.5.255 up
sudo route add default gateway 192.168.5.1
```

You will then need to find out the DNS address for your ISP and plug it into System > Administration > Network (DNS Tab).
You can get this info from the first computer.

ON PC2 (if running Widoze)
```
Control Panel > Network Connections > (Your network adapter) > Properties
In the list you wil find "Internet Protocol (TCP/IP)", go into that and select "Use the following IP address"

IP address:192.168.5.2
Submet mask:255.255.255.0
Default gateway:192.168.5.1

Then select Use the following DNS server address:
Prefered DNS: (your DNS Server IP)
```

At any time, you can do
```
ifconfig
```
or
```
netstat -rn
```
to find out more information on you interfaces and routing.

I hope this guide will help people in the same situation as me. I am now easily able to share and monitor (sniffing using wireshark) my second computer's internet connection without my ISP or PC#2 knowing about it. THIS IS AWESOME! (...such a geek!)

:guitar: Have you ever been experienced?

UPDATE: The one thing I need help with is setting this up when the computer starts up. It seems that any time that I reboot PC1, the routing tables get flushed. It shouldn't be too hard, but I'm just getting into shell scripting, so bare with me.

---

