---
title: "ath0 and eth0 on br0 cant communicate."
date: 2007-09-17
forum: Networking &amp; Wireless
---

### Post by tufkal on 2007-09-17
I have a very simple router setup on a server install of Feisty.  Here is my setup.

```

tufkal@tux:~$ cat /etc/network/interfaces
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

auto eth1
iface eth1 inet dhcp
pre-up /etc/init.d/custom-firewall

auto ath0
iface ath0 inet manual
wireless-mode master
wireless-essid 6908
wireless-key 

auto br0
iface br0 inet static
address 192.168.7.1
network 192.168.7.0
netmask 255.255.255.0
broadcast 192.168.7.255
bridge-ports eth0 ath0
tufkal@tux:~$

```

The custom-firewall script that is run on ifup is : 

```

tufkal@tux:~$ cat /etc/init.d/custom-firewall
#Clear iptables rules
iptables -P INPUT ACCEPT
iptables -F INPUT
iptables -P OUTPUT ACCEPT
iptables -F OUTPUT
iptables -P FORWARD DROP
iptables -F FORWARD
iptables -t nat -F

#Setup Router
echo 1 > /proc/sys/net/ipv4/ip_forward
iptables -A FORWARD -i eth1 -o br0 -m state --state ESTABLISHED,RELATED -j ACCEPT
iptables -A FORWARD -o eth1 -i br0 -j ACCEPT
iptables -A FORWARD -j LOG
iptables -t nat -A POSTROUTING -o eth1 -j MASQUERADE

#Custom for PPTP
iptables -t nat -A PREROUTING -i eth1 -p tcp --dport 1723 -j DNAT --to 192.168.7.2
iptables -A FORWARD -i eth1 -p tcp --dport 1723 -d 192.168.7.2 -j ACCEPT
iptables -t nat -A PREROUTING -i eth1 -p 47 -j DNAT --to 192.168.7.2
iptables -A FORWARD -i eth1 -p 47 -d 192.168.7.2 -j ACCEPT
tufkal@tux:~$

```

The problem is, wireless clients cannot communicate with wired clients.  This almost never is an issue, but when I have my laptop in my bedroom and I want to access my NAS (which is wired), I cannot.  

What is the solution to make this bridge route packets not just to the gateway, but to each other?

---

### Post by tufkal on 2007-09-17
No one? :(

---

### Post by netztier on 2007-09-18
> **tufkal said:**
> I have a very simple router setup on a server install of Feisty.  Here is my setup.

```

tufkal@tux:~$ cat /etc/network/interfaces
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

auto eth1
[COLOR="Red"]iface eth1 inet dhcp[/COLOR]
pre-up /etc/init.d/custom-firewall

auto ath0
iface ath0 inet manual
wireless-mode master
wireless-essid 6908
wireless-key 

auto br0
iface br0 inet static
address 192.168.7.1
network 192.168.7.0
netmask 255.255.255.0
broadcast 192.168.7.255
[COLOR="Red"]bridge-ports eth0 ath0[/COLOR]
tufkal@tux:~$

```


ehm.. I'm missing the lines for eth0 in that **/etc/network/interfaces** file. I assume that eth1 connects to your ISP, while eth0 and ath0 are meant to form a bridge for the "inside" network, right?
So is there some configuration for eth0 and you forgot to copy&paste it?

At first I was confused - an interface that is part of a bridge should not get an IP address via DHCP - it's the bridge interface that should have an IP address, but then I spotted that it was eth**1** that was DHCP client.

best regards

Marc

---

### Post by tufkal on 2007-09-18
Yes eth1 is the Internet connection, and eth0/ath0 are the inside connection.  Eth0 needs no config in interfaces since its just a 'dumb' part of the bridge.  So in essence.

Eth1 is the wan
Br0 is the lan (which consists of the ethernet and the wireless bridged)

And again, the problem is that the 2 part of the bridge cant contact each other.

---

### Post by netztier on 2007-09-19
> **tufkal said:**
> 
Eth0 needs no config in interfaces since its just a 'dumb' part of the bridge. 


What does **ifconfig eth0** give as result? There should be the "UP" keyword in there:

```
marc@blaze:~$ ifconfig eth0
eth0      Link encap:Ethernet  HWaddr 00:0E:0C:D0:B4:D3  
          inet addr:172.20.125.30  Bcast:172.20.125.255  Mask:255.255.255.0
          inet6 addr: fe80::20e:cff:fed0:b4d3/64 Scope:Link
          **UP** BROADCAST RUNNING MULTICAST  MTU:9000  Metric:1
          RX packets:647406 errors:0 dropped:0 overruns:0 frame:0
          TX packets:651667 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:117556045 (112.1 MiB)  TX bytes:3261371928 (3.0 GiB)
          Base address:0xe800 Memory:e2020000-e2040000 

```

From a gut feeling, I think that there should at least be an "auto eth0" line in /etc/interfaces so that eth0 is brought up (unless it's being brought up by another mechanism such as network-manager).

Grepping through **dmesg**'s output for "eth0" or br0 might also help to see what's been happening during system startup:

```
marc@blaze:~$ **dmesg | grep eth0**
[   47.308065] e1000: eth0: e1000_probe: Intel(R) PRO/1000 Network Connection
[   18.750000] e1000: eth0: e1000_watchdog: NIC Link is Up 1000 Mbps Full Duplex
[   20.160000] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   21.530000] e1000: eth0: e1000_watchdog: NIC Link is Up 1000 Mbps Full Duplex
[   21.530000] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   31.690000] eth0: no IPv6 routers present
marc@blaze:~$ **dmesg | grep br0**
...
```


best regards

Marc

---

