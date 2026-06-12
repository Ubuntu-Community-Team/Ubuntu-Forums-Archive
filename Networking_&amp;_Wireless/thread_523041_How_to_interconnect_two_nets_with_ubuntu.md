---
title: "How to interconnect two nets with ubuntu"
date: 2007-08-11
forum: Networking &amp; Wireless
---

### Post by donpaolo on 2007-08-11
I have an ubuntu pc connected through eth0 to net 10.152.58.*, and I added eth1 in order to connect it to net 10.0.2.*, I configured the interfaces and I see the two networks from my pc.

Now I want to see the second net from the first, i.e. transform the pc into a router between the two nets.

What should I do in order to get it working?

Thank you!

---

### Post by PaulFr on 2007-08-11
1. You have to tell other hosts on the two networks that the gateway to the other net is your Ubuntu machine.

2. Then you have to look for ```
# Uncomment the next line to enable packet forwarding for IPv4
#net.ipv4.conf.default.forwarding=1

# Uncomment the next line to enable packet forwarding for IPv6
#net.ipv6.conf.default.forwarding=1
``` in **/etc/sysctl.conf** and uncomment the lines you require. Reboot your machine and you should be able to see the other network.

3. If you want to try this first without rebooting, ```
echo 1 > /proc/sys/net/ipv4/ip_forward
```

4. If you want to check current state, ```
cat /proc/sys/net/ipv4/ip_forward
```

---

### Post by donpaolo on 2007-08-11
Shouldn't I change routing or modifying IPTABLEs on the pc?

---

### Post by PaulFr on 2007-08-11
1. By PC, do you mean the Ubuntu PC ? The commands above are for enabling forwarding. The Ubuntu PC does not need any routes since it is directly connected to both the networks. Use ```
netstat -rn
``` to see the current routes defined on your Ubuntu PC.

2. Whereas the other systems do need a route to the other network (since they are not **directly** connected to that network), and you do have to add a route to those systems. One special case is where the Ubuntu PC will act as the default gateway for one or both networks. The instructions for these also depend on what operating system (Win,Linux,Unix) you are running on those systems.

3. Unfortunately, I have no idea about iptables other than AFAIK it is by default setup in Ubuntu to forward everything, so if you have not changed it, you should not have to do anything with iptables.

---

