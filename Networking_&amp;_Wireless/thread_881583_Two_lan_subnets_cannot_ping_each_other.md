---
title: "Two lan subnets cannot ping each other"
date: 2008-08-06
forum: Networking &amp; Wireless
---

### Post by SillyChild on 2008-08-06
Hi all,

My gateway has two Ethernet cards:
eth0: connected to Internet

eth1: connected to switch where I'm maintaining two subnets.
```
eth1      Link encap:Ethernet  HWaddr 00:50:8B:0B:09:10  
          inet addr:10.0.1.100  Bcast:10.255.255.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:11645533 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8271964 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:235476038 (224.5 MiB)  TX bytes:1989243176 (1.8 GiB)
          Interrupt:11 Base address:0xdf40 

eth1:0    Link encap:Ethernet  HWaddr 00:50:8B:0B:09:10  
          inet addr:10.0.2.100  Bcast:10.255.255.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interrupt:11 Base address:0xdf40
```

All the machines in both the subnets can connect to the Internet. However, the machines cannot ping other machines in different subnet. They can only ping machines in their own subnet.

I believe this is a very simple issue, but at the moment struggling to work out a solution.

For your reference, part of the firewall script is posted below:
```

#
# Set default policies
#
iptables -P INPUT DROP
iptables -P FORWARD DROP
iptables -P OUTPUT ACCEPT

#
# Flush (-F) all specific rules
#
iptables -F INPUT
iptables -F FORWARD
iptables -F OUTPUT
iptables -F -t nat

#
# Define variables
#
lan=eth1
wan_ip=123.123.123.123
wan=eth0
lan_net1=10.0.1.0/255.255.255.0
lan_net2=10.0.2.0/255.255.255.0

#
# Allow all inputs to firewall from the internal network and local interfaces
#
iptables -A INPUT -i eth1 -s 0/0 -d 0/0 -j ACCEPT
iptables -A INPUT -i lo -s 0/0 -d 0/0 -j ACCEPT
iptables -A FORWARD -i lo -s 0/0 -d 0/0 -j ACCEPT

#
# Direct connection to internet snat
#
iptables -t nat -A POSTROUTING -o ${wan} -j SNAT --to-source ${wan_ip}

#
# Masquerade rule
#
iptables -t nat -A POSTROUTING -o eth0 -j MASQUERADE -s ${lan_net1}
iptables -t nat -A POSTROUTING -o eth0 -j MASQUERADE -s ${lan_net2}
iptables -t nat -A POSTROUTING -d 10.0.1.0/255.255.255.0 -j MASQUERADE -o eth1
iptables -t nat -A POSTROUTING -d 10.0.2.0/255.255.255.0 -j MASQUERADE -o eth1


```

Any suggestion will be very helpful.

---

### Post by Iowan on 2008-08-06
Broadcast addresses don't look right for subnets - shouldn't they be 10.0.1.255 and 10.0.2.255?

---

### Post by SillyChild on 2008-08-06
Figured out the problem. Just had to add the following line:

iptables -A FORWARD -i eth1 -s 0/0 -d 0/0 -j ACCEPT

It's all working now.

Thanks anyway :)

---

