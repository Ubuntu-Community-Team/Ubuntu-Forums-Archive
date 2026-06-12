---
title: "No Internet on Kubuntu 6.06!"
date: 2007-02-08
forum: Networking &amp; Wireless
---

### Post by Captain Insano on 2007-02-08
I'm frustrated. I'm very frustrated.

I changed my ISP this week, and now Internet isn't working on Kubuntu 6.06. The ISP doesn't support DHCP, so I had to manually configure the network settings (IP, netmask, broadcast, gateway and DNS), but I can't browse or use IM or IRC.

From shell, I can ping IP addresses, but can't ping domain names. When I try use IP address instead of domain name on my browser, it ends up with a error page. I know this a DNS problem, but can't figure out what's wrong -- everything works perfectly on Window$ with the same settings.

I got rid of Window$ after installing Kubuntu, but I had to install Window$ once again. Everything worked OK with the DHCP settings of my prior ISP, but can't figure out why it isn't working now.

Please help me out guys. As I said, I'm very frustrated. :(

---

### Post by Iowan on 2007-02-08
I doubt I can provide as much assistance as you're looking for, but maybe it's a start.  What's in your **/etc/resolv.conf**?  While we're at it - what's in **/etc/network/interfaces**?

---

### Post by Captain Insano on 2007-02-09
Thanks for replying. Here you go:

**/etc/network/interfaces:**
```
auto lo
iface lo inet loopback
address 127.0.0.1
netmask 255.0.0.0

auto eth0
iface eth0 inet static
address 10.0.20.249
netmask 255.255.255.0
gateway 10.0.20.1
```

**/etc/resolv.conf**
```
nameserver 124.109.16.7
nameserver 4.2.2.1
```

---

### Post by Captain Insano on 2007-02-10
No body is there who can help me out??? :confused:

---

### Post by koenn on 2007-02-10
try
```
dig www.google.com
```
to see if you get a return (servers, addresses)

---

### Post by Captain Insano on 2007-02-10
> **koenn said:**
> try
```
dig www.google.com
```
to see if you get a return (servers, addresses)

This is what it returns:

```
<<>> DiG 9.3.2 <<>> www.google.com
;; global options:  printcmd
;; connection timed out; no servers could be reached
```

:(

---

### Post by koenn on 2007-02-10
yep, there's your dns problem. Apparently the servers you have listed in /etc/resolv.conf don't work.

I can ping them from here, so either you can't reach them (firewall ?) or they're not dns servers. 

Try pinging those servers first.

---

### Post by Captain Insano on 2007-02-10
> **koenn said:**
> yep, there's your dns problem. Apparently the servers you have listed in /etc/resolv.conf don't work.

I can ping them from here, so either you can't reach them (firewall ?) or they're not dns servers. 

Try pinging those servers first.
I can ping both the DNS from Kubuntu. These must be the correct DNS, since Internet works properly on Windows.

Regarding firewall, I'm not aware of one... I didn't install any, but there must be a built-in one (iptables?) that comes with Kubuntu? If so, how do I disable it?

BTW, I'm not using a router at my end.

---

### Post by koenn on 2007-02-10
let's see if it works with another server:
put this :
```
nameserver 195.130.131.2
```
as first dns server in /etc/resolv.conf. It's one of my IPS's DNS servers.

BTW, how do you connect to the internet - you have a 10.0. .. address, there must be something between you and the internet.

---

### Post by Captain Insano on 2007-02-10
> **koenn said:**
> let's see if it works with another server:
put this :
```
nameserver 195.130.131.2
```
as first dns server in /etc/resolv.conf. It's one of my IPS's DNS servers.

BTW, how do you connect to the internet - you have a 10.0. .. address, there must be something between you and the internet.
No, still the same... can't resolve domain names.

There's a mikrotik router running on the ISP end (10.0.20.1)... any problem on it maybe?

I still can't understand why/how everything is alright OK on Windows.

---

### Post by koenn on 2007-02-10
> There's a mikrotik router running on the ISP end (10.0.20.1)... any problem on it maybe?
Just trying to picture the layout of your network / internet connection. 
These are private addresses - rather unusual for an ISP
How do you connect to that router ?

> I still can't understand why/how everything is alright OK on Windows.
Me neither. I think I'll go and sleep on it.

---

