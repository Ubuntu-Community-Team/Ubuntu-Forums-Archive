---
title: "Connect four PC'S without Router"
date: 2015-10-20
forum: Networking &amp; Wireless
---

### Post by David_Bunga on 2015-10-20
Hi Guys, having some trouble in Networking.

Here is my network 
PC1 : Window 7/ubuntu, IP: 192.168.8.2 gtwy: 192.168.8.1
PC2 (2 nic cards) using ubuntu : eth0 : 192.168.8.1
eth1: 192.168.9.1 gtwy: 192.168.9.2
PC3 (2 nic cards) using ubuntu : eth0 : 192.168.10.1
eth1: 192.168.9.2 gtwy: 192.168.9.1
PC4: Win/ubuntu, IP: 192.168.10.2 GTWY: 192.168.10.1

My problem is i cannot ping to the host systems i.e pc1 to pc4 and vice versa.

can someone please help me out !!

---

### Post by michi1983 on 2015-10-20
Hi,

no surprise.
When you wanna ping PC4 (192.168.10.2) from PC1 (192.168.8.2), PC1 looks in his routing table if 192.168.10.2 is in his subnet.
It's not, so he sends the packet to his gateway 192.168.8.1 and lands on PC2.
PC2 does the same and as 192.168.10.2 is not in it's subnet either, he sends it to it's gateway 192.168.9.2 and lands on PC3.
PC3 does the same and as 192.168.10.2 is not in it's subnet either, he sends it to it's gateway which is 192.168.9.1, so you land on PC2 again, so you create kind of a loop here.
And if you want the ping echo reply to come back to PC1 you will have to set a def gateway on PC4 to PC3 as well.
And then a static route from PC3 to 192.18.8.0 via 192.168.9.1.

A much simpler procedure would be if you install/enable RIP or OSPF on all machines.
They will then broadcast all their routes automatically to all other members on the network.
Quagga and Bird are the packets you should look for.

Apart from that you have to enable IP forwarding on your Ubuntu machines.
Edit /etc/sysctl.conf to
```
net.ipv4.ip_forward=1
```

---

