---
title: "Networking from eth1 to eth0"
date: 2015-08-22
forum: Networking &amp; Wireless
---

### Post by ibizatunes on 2015-08-22
Basically I want to pass all traffic from  172.16.1.2 eth1 to 192.168.0.1 eth0
172.16.1.2 is the ip address of eth1
192.168.0.1 is my internet connected router connected on eth0

Routing table

```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
default         10.200.100.161  128.0.0.0       UG    0      0        0 tun0
10.200.0.1      10.200.100.161  255.255.255.255 UGH   1      0        0 tun0
10.200.100.161  *               255.255.255.255 UH    0      0        0 tun0
2-65-245-77.rac 192.168.0.1     255.255.255.255 UGH   0      0        0 eth0
128.0.0.0       10.200.100.161  128.0.0.0       UG    0      0        0 tun0
link-local      *               255.255.0.0     U     1000   0        0 eth1
172.16.0.0      *               255.255.0.0     U     0      0        0 eth1
192.168.0.0     *               255.255.255.0   U     0      0        0 eth0
```

The 10.0.0.0 are my VPN client software i have 


Im running the following command


```
sudo route add -net 172.16.0.0 netmask 255.255.0.0 gw 192.168.0.1 eth0
```

As soon as run the above command i cant ping my switch on the network address 172.16.1.1

I also want the route to last after reboot

---

### Post by matt_symes on 2015-08-22
Hi

You need to set the ip_forward sysctl to turn the machine into a router. There is also a /sys file you can write to as well but this is temporary and is lost after a reboot.

Then you need to create some iptables rules to MASQURADE the packets from one subnet to another.

EDIT: I'm at a BBQ so...

Kind regards

---

### Post by ibizatunes on 2015-08-22
Thanks i now have this running and have made it permanent

/etc/sysctl.conf:
net.ipv4.ip_forward = 1


Trying to setup the iptable i ran the following command

```
sudo ufw enable 
```

now i have run the computer with ufw disable otherwise i cant ping 172.168.1.1

My iptables are in a bit of mess and im stuck on how to get them fixed and simply to do two way communication from eth1 to eth0 of different ip ranges

```

Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination         

Chain ufw-after-forward (0 references)
target     prot opt source               destination         

Chain ufw-after-input (0 references)
target     prot opt source               destination         

Chain ufw-after-logging-forward (0 references)
target     prot opt source               destination         

Chain ufw-after-logging-input (0 references)
target     prot opt source               destination         

Chain ufw-after-logging-output (0 references)
target     prot opt source               destination         

Chain ufw-after-output (0 references)
target     prot opt source               destination         

Chain ufw-before-forward (0 references)
target     prot opt source               destination         

Chain ufw-before-input (0 references)
target     prot opt source               destination         

Chain ufw-before-logging-forward (0 references)
target     prot opt source               destination         

Chain ufw-before-logging-input (0 references)
target     prot opt source               destination         

Chain ufw-before-logging-output (0 references)
target     prot opt source               destination         

Chain ufw-before-output (0 references)
target     prot opt source               destination         

Chain ufw-reject-forward (0 references)
target     prot opt source               destination         

Chain ufw-reject-input (0 references)
target     prot opt source               destination         

Chain ufw-reject-output (0 references)
target     prot opt source               destination         

Chain ufw-track-forward (0 references)
target     prot opt source               destination         

Chain ufw-track-input (0 references)
target     prot opt source               destination         

Chain ufw-track-output (0 references)
target     prot opt source               destination 
```

Any help would be most helpful!!

---

### Post by matt_symes on 2015-08-22
Hi

Firstly disable and flush all your IP tables and rules on your server/router for testing.

My test setup:

Box a(192.168.0.1) => (192.168.0.100) eth0 router eth1 (10.55.7.1) => laptop (10.77.5.150)

The laptop (10.55.7.150) is connected via Ethernet to eth1 (10.55.7.1) on the router.

Box a (192.168.0.1) is connected to eth0 (192.168.0.100) on the router.

As you can see the router contains 2 network cards on different subnets.

I want to be able to ping box a from the laptop.

Consider box a on the Internet somewhere.

In the router I first enable IP forwarding.

```
echo net.ipv4.ip_forward=1 |sudo tee -a /etc/sysctl.conf
```

I think you have done this step though.

You then need to reboot your PC. The above step allows packets to be forwarded from eth0 to eth1 and back ( after a bit more work). If effectively allows the router to NAT traffic from one subnet to the other.

Now you need to add an IP tables rule to the router PC.

```
sudo iptables -t nat -A POSTROUTING -o eth1 -j MASQUERADE
```

I can now ping box a from the laptop.

Does that help ?

Kind regards

---

### Post by matt_symes on 2015-08-22
Hi

Anyway, if the above helps you out then you'll want to make the IP tables rule persistent as it'll be lost after reboot.

Also read up on what I have done and on IP tables as you'll most likely want to tweak it but you get the general idea.

Kind regards

---

### Post by ibizatunes on 2015-08-23
Still having issues
```
echo net.ipv4.ip_forward=1 |sudo tee -a /etc/sysctl.conf
net.ipv4.ip_forward=1
```

```
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         
ACCEPT     all  --  anywhere             anywhere            
ACCEPT     all  --  anywhere             anywhere            

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         
ACCEPT     all  --  anywhere             anywhere            
ACCEPT     all  --  anywhere             anywhere            

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination
```


```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
default         SkyRouter.Home  0.0.0.0         UG    1024   0        0 eth0
link-local      *               255.255.0.0     U     1000   0        0 eth1
172.16.0.0      *               255.255.0.0     U     0      0        0 eth1
192.168.0.0     *               255.255.255.0   U     0      0        0 eth0
```

Successful ping device from 172.168.1.3 laptop
Sucess - Server 172.16.1.2  Server eth1
Sucess - Router 172.168.1.1   (basically for WIFI access on 172.16.1.1 network)   
Router has a static route configured of Destination IP Address 172.168.1.2 Subnet 255.255.255.255 Gateway 172.168.1.1

CANT ping 192.168.0.16 - Servers eth0
CANT ping 192.168.0.1 Internet Router


Succesfully ping from address 192.168.0.7  laptop 
Sucess - Ping 192.168.0.1 router
Sucess - Ping 192.168.0.16 server address on eth0
CANT ping 172.168.1.1 or any other devices on this network

---

### Post by matt_symes on 2015-08-23
Hi

Can you draw some ascii art of an ascii block diagram of exactly what is connected to what, the IP addresses on each interface and what you are trying to ping from where.

It's Sunday, the day I try not to think too hard :)

Kind regards

---

### Post by ibizatunes on 2015-08-23
[ATTACH]264016[/ATTACH]

13.7k is the lastest picture
Drawing of the network, basically want to route between the 172.16.0.0 to 192.168.0.0 network, and from 192.168.0.0 to 172.16.0.0

---

### Post by ODTech on 2015-08-23
I found using UFW very limiting so i uninstalled it and started using iptables directly.

[http://ubuntuforums.org/showthread.php?t=926001](http://ubuntuforums.org/showthread.php?t=926001)

Here's a complete guide.

---

