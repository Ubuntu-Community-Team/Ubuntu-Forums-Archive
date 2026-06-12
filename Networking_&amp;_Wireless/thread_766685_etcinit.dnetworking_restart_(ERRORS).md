---
title: "/etc/init.d/networking restart (ERRORS)"
date: 2008-04-25
forum: Networking &amp; Wireless
---

### Post by LRT on 2008-04-25
i have two interfaces both assigned static ip addresses. here is /etc/network/interfaces

```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 192.168.1.102
netmask 255.255.255.0
network 192.168.1.0
gateway 192.168.1.1

auto eth1
iface eth1 inet static
address 192.168.2.1
netmask 255.255.255.0
network 192.168.2.0
gateway 192.168.1.102
```

eth1 is serving dhcp addresses. here is my subnet declaration in dhcpd.conf

```
subnet 192.168.2.0 netmask 255.255.255.0 {
  range 192.168.2.10 192.168.2.50;
  option routers 192.168.2.1;
}
```

when i try to start the network i get the following error:


```
root@pandion:/home/leandro# /etc/init.d/networking restart
 * Reconfiguring network interfaces...
SIOCADDRT: No such process
Failed to bring up eth1.
[ OK ]
```

my theory is that i don't think it likes the gateway address for eth1 (which is the ip address of eth0). if i comment the gateway line for eth1 in the interfaces file and then restart networking i get a different error:

```

root@pandion:/etc/default# /etc/init.d/networking restart
 * Reconfiguring network interfaces... 
RTNETLINK answers: No such process
[ OK ]
```

i'm also doing ip forwarding and internet connection sharing from eth1 to eth0 with syscntl.conf and some iptables rules. this works fine because all my dhcp clients can browse the web and receive leased addresses.

what i don't understand is why i am getting those errors when i restart networking????? is the gateway address wrong???

---

### Post by LRT on 2008-04-25
by the way, this is not a problem related to a hardy heron upgrade... i'm still using 7.10

---

### Post by LRT on 2008-04-28
haven't received much attention on this post but thats ok... i like to figure things out on my own (most of the time)... come to find out my gateway address for eth1 is wrong because the address should be on the same subnet as the interface. so a gateway address of 192.168.1.1 for eth1 is wrong because it is not the 192.168.2.0 network which eth1 is on.

so my question is... if i am statically assigning all addresses for eth1, what should the gateway address be??? eth1 is supposed to be forwarding all traffic to eth0 (which is why i thought the gateway address should be 192.168.1.1, the ip address of eth0's gateway)... 

i'm a bit confused do to my lack of networking knowledge, any help would be appreciated! thanks.

---

### Post by LRT on 2008-04-28
this >>>[post]("http://www.computing.net/answers/windows-2003/default-gateway-2-nics/3810.html")<<< (unfortunately not on ubuntuforums) has answered my question pretty thoroughly.. apparently i don't even need a gateway address set for eth1. the only gateway address i need to assign is for eth0.. dhcp clients on the eth1 subnet will receive a gateway address of my eth1 ip address (192.168.2.1).

the post was specific to windows 2003 server... but it was a networking question so i assume it still applies to my problem... if anyone could confirm this solution that would be great... 

HOWEVER, when i do a /etc/init.d/networking restart, i still get this error message:

```
RTNETLINK answers: No such process
```

i'm not sure what this means, but now i am pretty sure it has nothing to do with my gateway address setting since i know the setting is correct...

any posts on this thread other than mine would be welcome... thanks!

---

