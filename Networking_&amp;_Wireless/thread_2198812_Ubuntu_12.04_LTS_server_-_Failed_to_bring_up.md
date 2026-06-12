---
title: "Ubuntu 12.04 LTS server - Failed to bring up"
date: 2014-01-10
forum: Networking &amp; Wireless
---

### Post by mr.lioncava on 2014-01-10
I am using Ubuntu 12.04. running in vmware
My /etc/network/interfaces file consists of:

```
# The loopback network interface  
auto lo  
iface lo inet loopback  


# The primary network interface  
auto eth0 
iface eth0 inet static  
address 192.168.3.15
netmask 255.255.255.0
network 192.168.3.0  
broadcast 192.168.3.255
gateway 192.168.3.254
dns-nameservers 66.212.63.228 66.212.48.10 

auto eth1
iface eth1 inet static  
address 192.168.3.40
netmask 255.255.255.0
network 192.168.3.0  
broadcast 192.168.3.255
gateway 192.168.3.15
dns-nameservers 66.212.63.228 66.212.48.10 
```

I ran the command: /etc/init.d/networking restart
  Which responded with: 


*Running /etc/init.d/networking restart is deprecated because it may not enable again some interfaces  
*Reconfiguring network interfaces...  
RTNETLINK answers: File exists  
Failed to bring up eth1
[ OK ]

---

### Post by praseodym on 2014-01-11
Two different gateways?

---

### Post by mr.lioncava on 2014-01-11
> **praseodym said:**
> Two different gateways?

if i delet gateway eth1 also same problem

---

### Post by praseodym on 2014-01-11
Add the same gateway.

---

### Post by houstonbofh on 2014-01-11
1) Only use one gateway.

2) Are the virtual nice in VMware connected to the same v-switch?

3) What is the result of "ifconfig" both before and after restart?

4) What is the result of "sudo ifup eth1" and "sudo ifdown eth1"

I would use this config...

```
# The loopback network interface
auto lo
iface lo inet loopback


# The primary network interface
auto eth0
iface eth0 inet static
address 192.168.3.15
netmask 255.255.255.0
gateway 192.168.3.254
dns-nameservers 66.212.63.228 66.212.48.10

auto eth1
iface eth1 inet static
address 192.168.3.40
netmask 255.255.255.0

```
Both network and broadcast are derived from the subnet mask.

---

