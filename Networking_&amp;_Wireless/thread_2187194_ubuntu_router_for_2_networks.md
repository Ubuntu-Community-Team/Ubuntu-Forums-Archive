---
title: "ubuntu router for 2 networks"
date: 2013-11-11
forum: Networking &amp; Wireless
---

### Post by Master-JCF on 2013-11-11
Hi,

i'm new here. So please be a little bit patient.
I searched this topic about 2 days and couldn't found any solution for me. So I want to try it here.

I have the following configuration:

**Gateway:**
  192.168.151.1

**Workstation:**
  192.168.150.10

**Interfaces:**
  auto eth0
  iface eth0 inet static
  address 192.168.151.55
  netmask 255.255.255.0
  network 192.168.151.0
  broadcast 192.168.151.255
  gateway 192.168.151.1

  auto eth1
  iface eth1 inet static
  address 192.168.150.2
  netmask 255.255.255.0
  network 192.168.150.0
  broadcast 192.168.150.255
  gateway ?.?.?.?
  
**resolve.conf:**
  nameserver IP_OF_NS1
  nameserver ÎP_OF_NS2

**cat /proc/sys/net/ipv4/ip_forward**
  1

gateway x.x.151.1 is working and Ubuntu can reach internet over eth0

What do I have to do, to connect my workstation to the gateway?
I don't know what I do have to set as gateway for eth1 or what else I must do.

any ideas?

---

### Post by Lars Noodén on 2013-11-11
Can you draw out a simple diagram of exactly how you have the machines connected together?

---

### Post by Master-JCF on 2013-11-11
is this ok?

[IMG]http://www.nur8.de/ubuntu.jpg[/IMG]

192.168.150.x should be connected to 151.x with no limits. And it should work in both directions.

---

### Post by nebileix on 2013-11-11
Based on assumption, you need the following:

1. You need static router on the internet-router for 192.168.151.x to communicate 192.168.150.x.
2. Run ```
# /sbin/iptables -t nat -A POSTROUTING -o eth0 -j MASQUERADE
``` on ubuntu server. That was assuming you didn't have any DROP policy.

---

### Post by Lars Noodén on 2013-11-11
Will that go both directions, or just one?

---

### Post by Master-JCF on 2013-11-11
> **nebileix said:**
> ... That was assuming you didn't have any DROP policy.
It's a blank new ubuntu 12.04.3 server.
Only OpenSSH is installed and I have configured nothing else but eth0/1 (as seen above)

---

### Post by nebileix on 2013-11-11
1. I mean static route. Your internet-router should have the option to configure that. You need to specify the network(192.168.150.0)/netmask(255.255.255.0) and gateway (should be your eth0 ip on your ubuntu server).
2. Should enable 192.168.150.x to reach 192.168.151.x. the iptables command basically route all unknown traffic to upstream router(internet-router)

---

### Post by Master-JCF on 2013-11-11
I tried some configurations and it looks like it now works for some tasks.

1. I did the iptables from nebileix

2. I set the gateway of eth1 to 192.168.151.1

3. 
At the workstation I set the following:
IP: 192.168.150.10
Mask: 255.255.255.0
Gateway: 192.168.150.2 (ubuntu)

Internet, Windows-Update etc. work fine.

But: ping from 151.x <-> 150.x still doesn't work. But that's not so important to me at the moment. Would be great to solve this too, but for now internet on 150.x is ok :)

---

### Post by nebileix on 2013-11-11
2. I set the gateway of eth1 to 192.168.151.1 <=== shouldn't be required.

But: ping from 151.x <-> 150.x still doesn't work. But that's not so important to me at the moment. Would be great to solve this too, but for now internet on 150.x is ok :) <== consult your internet-router documentation on how to configure static route.

---

### Post by Master-JCF on 2013-11-11
> **nebileix said:**
> 1. I mean static route. Your internet-router should have the option to configure that.
I don't have access to the internet-router. So no option.

but: ping from 150 to 151 works now (at first I only tired hostnames instead of IPs....#-o). Remote-Desktop also works :D
ping form 151 to 150 is still not possible.

---

### Post by nebileix on 2013-11-11
Too bad then. You need that to work if you're not going to change the hardware setup.

Else you need to add static route on individual computer in the 192.168.151.x network.

---

### Post by Master-JCF on 2013-11-11
> **nebileix said:**
> 2. Run ```
# /sbin/iptables -t nat -A POSTROUTING -o eth0 -j MASQUERADE
``` on ubuntu server. That was assuming you didn't have any DROP policy.how do I make this static/reboot-safe?

> **nebileix said:**
> Too bad then. You need that to work if you're not going to change the hardware setup.
Else you need to add static route on individual computer in the 192.168.151.x network.
It's ok. Internet for 150.x was the goal. Everything else would be nice but not nessesary.

I just wonder why 150 can ping 151 but 151 not 150?

---

### Post by nebileix on 2013-11-11
To make it persistent across reboot: ```
# iptables-save > /etc/myiptables.conf
```
Add "/sbin/iptables-restore < /etc/myiptables.conf" to /etc/rc.local.
Please add it before the "exit 0" line.

You might be interested to read up on [routing and how it works]("http://computer.howstuffworks.com/router.htm").

---

### Post by Master-JCF on 2013-11-12
thanks a lot for the fast help. :)

---

