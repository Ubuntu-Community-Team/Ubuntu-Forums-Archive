---
title: "Do not understand about IP Forwarding"
date: 2015-02-23
forum: Networking &amp; Wireless
---

### Post by n3wguys on 2015-02-23
Hi everyone,

I need your help about IP Forwarding

here my topology


HOST A_eth1(192.168.1.2) <-------------------------->(192.168.1.3)eth0_HOST-B_eth1(192.168.0/24)   <---------> SW <-----> PC Client(192.168.0.13)
      	                                    


I do not understand how to prepare ip forward on HOST-B, and my plan, from PC client which used an IP DHCP from host-B_eth1, it will be access Host A.
that I have done :

for HOST B configure:

sysctl:
net.ipv4.conf.default.forwarding=1
net.ipv4.conf.all.forwarding=1
net.ipv4.ip forward=1


configure IP forwarding:

iptables -t nat -A POSTROUTING -o eth0 -j MASQUERADE



after that, ping from pc client to host A, unsuccess.

please help me.

---

### Post by kpatz on 2015-02-23
What is SW in between HOST B and PC Client?  A switch?

Is the DHCP server configured to supply the gateway IP to the PC clients as the IP address of eth1?  (You don't have that shown, just the IP range 192.168.0/24).  Assuming eth1 is assigned 192.168.0.1, the DHCP server should be configured to give that out to the PCs as gateway.

Can the PCs ping host B?

Are there any other iptables rules besides the NAT rule you show?

In your list of sysctls, did you miss an underscore on the last one (ip forward should be ip_forward)?

---

### Post by SeijiSensei on 2015-02-23
> **n3wguys said:**
> 
```

HOST A_eth1(192.168.1.2) <-------------------------->(192.168.1.3)eth0_HOST-B_eth1(192.168.0/24)   <---------> SW <-----> PC Client(192.168.0.13)
iptables -t nat -A POSTROUTING -o eth0 -j MASQUERADE

```

If you want to masquerade traffic on 192.168.1.0/24 to 192.168.0.0/24, you need to specify the interface that points to the latter network.  That appears to be eth1 on the diagram.  So try replacing eth0 with eth1 in your masquerading rule.

---

### Post by n3wguys on 2015-02-23
Oups sorry,

SW = Switch
range IP 192.168.1.0/24 which I have configure is : 192.168.1.11-192.168.1.240.

yes, I can do to ping from pc client to Host B and Host B to PC client be smoothly. and also I can Ping from Host B to Host A and ping host A to Host B.

Just ping from PC Client to Host A I can't do it because there I do not know how to make IP Forward(NAT rule) or something configure that make PC Client can ping to host A.

---

### Post by n3wguys on 2015-03-03
like what the command ???

---

### Post by Doug S on 2015-03-03
Please post your entire iptables rule set. Please post the output for:```
sudo iptables -v -x -n -L
sudo iptables -t nat -v -x -n -L
```

---

