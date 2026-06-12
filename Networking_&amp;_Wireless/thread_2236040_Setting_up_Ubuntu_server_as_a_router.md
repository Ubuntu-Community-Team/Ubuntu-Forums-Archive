---
title: "Setting up Ubuntu server as a router"
date: 2014-07-24
forum: Networking &amp; Wireless
---

### Post by **FuSeD** on 2014-07-24
I have followed almost every tutorial out there and I cannot get this damn thing to work! I can get the connected computers to be assigned an IP address by the server but when I try to load a webpage it just times out. I've reinstalled about 5 times, tried about 5 different tutorials. I know the server is connected to the internet it returns every single ping to google.com. Can someone please help.

Update:

I've fixed the problem, Using Squid transparent proxy now and all working ok :)

---

### Post by sedawk on 2014-07-24
Sounds like you have setup a DHCP-Server on your Ubuntu machine?
Are you sending your clients a default gateway together with the IP-address?
Is that default gateway your Ubuntu machine?
What kind of debugging have you done? Ping? Traceroute? Tcpdump?
What about IP forwarding?

---

### Post by **FuSeD** on 2014-07-24
I followed the instructions from here [https://help.ubuntu.com/community/Router](https://help.ubuntu.com/community/Router)
When i send a ping from the server side there is no problem but when i send it to any computer connected to the server it just times out. The instructions weren't very clear on the DNS, Says to send back to the server and to your isp's servers or router. I think it's a dns problem but I have no clue. I tried sending it to the isps DNS (194.168.4.100) and nothing, I tried just sending it back to the router (192.168.0.1) and still nothing. :(

---

### Post by Lars Noodén on 2014-07-24
Did you get forwarding turned on properly?  What is the output of sysctl in that regard?

```

sysctl net.ipv4.ip_forward 

```

---

### Post by **FuSeD** on 2014-07-24
I uncommented it in the file, do i need to run that code too?

---

### Post by Lars Noodén on 2014-07-24
The kernel needs to know that it should be forwarding packets.  Otherwise, if it is not told to, it won't.  Is *net.ipv4.ip_forward* set to 1 or 0?

---

### Post by **FuSeD** on 2014-07-24
it's set to 1

---

### Post by **FuSeD** on 2014-07-24
I've reinstalled again to start from fresh and still having the same problem. I think it's just not forwarding the ports. I've uncommented line 28 in /etc/sysctl.conf to read: "net.ipv4.ip_forward=1" the connected computers are being given an IP address by the server and the server IP as one DNS server and the ISP's as another.  and added [HTML]/sbin/iptables --table nat --append POSTROUTING --out-interface eth1 -j
MASQUERADE
/sbin/iptables --append FORWARD --in-interface eth0 -j ACCEPT
[/HTML] to /etc/init.d/router which didn't even exist.

---

### Post by Lars Noodén on 2014-07-24
> ****FuSeD** said:**
> ```
/sbin/iptables --table nat --append POSTROUTING --out-interface eth1 -j
MASQUERADE

```

eth1 should be the external interface.  Are those rules visible if you run *sudo iptables -L* or *sudo iptables-save*?

The postrouting rule and setting net.ipv4.ip_forward were the only two changes I had to make.

---

### Post by **FuSeD** on 2014-07-24
The output of sudo iptables -L is
```
Chain INPUT (policy ACCEPT)
target    prot opt source        destination

Chain FORWARD (policy ACCEPT)
target    prot opt source        destination
ACCEPT    all -- anywhere        anywhere

Chain OUTPUT (policy ACCEPT)
target    prot opt source        destination
```

I have no idea what any of this means lol.

---

### Post by **FuSeD** on 2014-07-24
OK, now i'm not sure if it is the port forwarding haha, this is really confusing me. When I type into the browser of the computer connected to the server 192.168.0.1 it accesses the gui of the router at the beginning of the network, so it is forwarding internally just not externally.

---

### Post by Lars Noodén on 2014-07-26
What about from *sudo iptables-save*? That should show the NAT rules.

---

### Post by SeijiSensei on 2014-07-26
Or just "sudo iptables -t nat -L -nv".  The last two switches tell iptables not to resolve IP addresses ("n") and to provide a verbose output.

---

