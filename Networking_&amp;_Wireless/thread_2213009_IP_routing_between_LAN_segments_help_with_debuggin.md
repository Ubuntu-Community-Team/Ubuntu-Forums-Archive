---
title: "IP routing between LAN segments: help with debugging?"
date: 2014-03-24
forum: Networking &amp; Wireless
---

### Post by henrylaw on 2014-03-24
I'm setting up an Ubuntu server to act as a router between a subsidiary network segment and the rest of the LAN.  It's running 12.04 server and has two NICs, thus:

  [FONT=courier new]MAIN LAN (172.24.0.192/26)
      |
      | 172.24.0.240 (eth1)
    Server
      | 10.18.78.254 (eth0)
      |
  SUBSIDIARY SEGMENT (10.18.78.0/24)
      |
    Test PC (10.18.78.55 by DHCP)[/FONT]

The Test PC can ping the server and vice versa.  The server can ping stations elsewhere on the main LAN, and vice versa, but the Test PC cannot see any address on the main LAN.  Can someone help me diagnose this?  Details follow.

I have the two NICs set up in /etc/network/interfaces thus:

```
auto eth1
iface eth1 inet static
  address        172.24.0.240
  netmask        255.255.255.192
  gateway        172.24.0.254
  dns-nameservers    172.24.0.254
 auto eth0
 iface eth0 inet static
   address        10.18.78.254
   netmask        255.255.255.0
```

After extensive Googling I've used these policy-based routing commands:

```
ip route add 10.18.78.0/24 dev eth0 src 10.18.78.254 table admin
ip route add default via 10.18.78.254 dev eth0 table admin
ip rule add from 10.18.78.254 table admin
ip rule add to 10.18.78.254 table admin
```
(There's a "1 admin" table set up in /etc/iproute2/rt_tables)

I have enabled ip forwarding:
[FONT=courier new]$ sudo sysctl net.ipv4.ip_forward
net.ipv4.ip_forward = 1[/FONT]

I've installed xinetd, which was suggested by one of the posts I read; it's running  but I have not configured it.

My routing tables and rules now look like this:
```
$ ip route show
default via 172.24.0.254 dev eth1  metric 100 
10.18.78.0/24 dev eth0  proto kernel  scope link  src 10.18.78.254 
172.24.0.192/26 dev eth1  proto kernel  scope link  src 172.24.0.240

$ ip rule show
0:    from all lookup local 
32764:    from all to 10.18.78.254 lookup admin 
32765:    from 10.18.78.254 lookup admin 
32766:    from all lookup main 
32767:    from all lookup default

$ ip route show table admin
default via 10.18.78.254 dev eth0 
10.18.78.0/24 dev eth0  scope link  src 10.18.78.254
```

(Though netstat doesn't show all this, which is worrying)
```
$ netstat -rn
Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
0.0.0.0         172.24.0.254    0.0.0.0         UG        0 0          0 eth1
10.18.78.0      0.0.0.0         255.255.255.0   U         0 0          0 eth0
172.24.0.192    0.0.0.0         255.255.255.192 U         0 0          0 eth1
```

I'm doing something wrong, plainly, but I have no idea either what it is or how to debug it.  Is there some way of commanding Ubuntu to tell me what routing decisions it's making?

---

### Post by The Cog on 2014-03-24
I can't think of a good reason to meddle with the forwarding tables at the moment. I would be inclined to go with just the default forwarding tables.

Are your devices on the LANs aware that they have to use your Ubuntu server as the gateway to get to the other LAN? You should check the routing tables of both the test PC and the main LAN. Of course, if they have a router elsewhere as their default gateway (e.g router 172.24.0.254 on the main LAN) then this defautlt gateway is the one that needs to know that 10.18.78.0/24 is via 172.24.0.240 in its routing tables. I would guess that you have something missing in these other devices's routing tables.

You can check what packets are coming in and out of the Ubuntu server with tcpdump, like this:
```
sudo tcpdump -np -i eth0
```
(or eth1 of course) to verify whether:
* devices are sending packets to you to be forwarded, 
* that you are forwarding the packets to the destination on the other interface,
* that the replies are being sent to you for forwarding to to the original PC, and
* that you are correctly forwarding the replies.

Also, look to make sure you don't have firewall rules that are stopping things:
```
sudo iptables -nvL
```

You can also see how it thinks it route a hypothetical packet (not including firewall effects):
```
ip route get 172.24.0.123 from 10.18.78.123 iif eth1
```

---

### Post by henrylaw on 2014-03-24
Thank you for impressively quick response.  

You said "*You should check the routing tables of both the test PC and the main LAN"*.  The routing tables on the test pc (xxx.55) are 
[FONT=courier new]default via 10.18.78.254 dev eth0 proto static
10.18.78.0 dev eth0 proto kernel scope link src 10.18.78.55 metric 1
169.254.0.0/16 dev eth0 scope link metric 1000[/FONT]
... which looks OK to me (matches the workstation I'm typing on)

You suggested *"You can check what packets are coming in and out of the Ubuntu server with tcpdump"* which I did.  Using the log produced on the server Wireshark shows packets coming in on eth1 from 10.18.78.55 with destination 172.24.0.249 (another server on the main LAN), both TCP and ICMP (I attempted to SSH to that server from the test PC, and also ping it).

You mentioned iptables.  I should have said in my original post that only the default (null) iptables entries are in force.

Lastly you suggested using "[FONT=courier new]ip route get[/FONT]".  On the server that produced something interesting:
[FONT=courier new]$ ip route get to 172.24.0.249 from 10.18.78.55 iif eth1
RTNETLINK answers: Invalid cross-device link[/FONT]

I googled that error message, to find that it's rather obscure, and that nobody seems to have a good interpretation of it.  Any suggestions of where to go from here?

---

### Post by SeijiSensei on 2014-03-24
Take a look in /etc/sysctl.conf and make sure "net.ipv4.ip_forward" is set to one.  By default, Ubuntu will not forward packets between interfaces as a security precaution.

You can enable forwarding on the fly by entering the command:
```
sudo echo '1' > /proc/sys/net/ipv4/ip_forward
```
but it will revert at the next boot unless you change sysctl.conf.

You shouldn't need any special routing rules if the interfaces have IP addresses in the correct subnets, and the hosts have the correct default gateways specified.  Hosts in 10.18.78.0/24 need to have 10.18.78.254 as their default gateway; hosts in 172.24.0.192/26 need to use 172.24.0.240.

---

### Post by henrylaw on 2014-03-24
IP forwarding was already enabled, as I said in my original post.  But what Seiji Sensei later said -- "hosts in 172.24.0.192/26 need to use 172.24.0.240" -- is the key to it.  

For those reading this later, the problem is not in the gateway server at all: it's that other hosts on the main (172.24.0.192/26) LAN don't know how to send a response back to a host on the 10.18.78.0 LAN.  This is, of course, blindingly obvious to me now ... especially since The Cog already said "Are your devices on the LANs aware that they have to use your Ubuntu server as the gateway to get to the other LAN?", which is the same point.   Duh ...

On the target machine (172.24.0.249 in the narrative so far) I issued 
```
sudo ip route add 10.18.78.0/24 via 172.24.0.240
```
... and everything works!  (Of course I need to make that permanent, but that's easy).

Thank you very much, all.  [Edited a few minutes after posting to recognise that I had to be told this twice, not once ...]

---

