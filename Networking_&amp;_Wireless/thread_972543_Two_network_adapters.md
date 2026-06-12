---
title: "Two network adapters"
date: 2008-11-05
forum: Networking &amp; Wireless
---

### Post by RMSe17 on 2008-11-05
I am setting up a server using Ubuntu Desktop 8.04.1.  The server has two network adapters, one of which is connected to the standard network and the outside internet.  The second network adapter is connected to an iSCSI storage device over a switch.  

I set up eth0 with DHCP, and can access the internet just fine.  I then proceeded to give a static address to eth1 (192.168.157.10).  The iSCSI device is configured with an IP of 192.168.157.30.  When I tried to ping the iSCSI device, but could not get a response.  I wonder if maybe the ping command is trying to use eth0, and thus failing to locate the device.  
How do I specify which adapter a command should use?  Or do I need to somehow set up an IP range, whereby if I am addressing a certain IP, Ubuntu will know to use eth1 as opposed to eth0? 

Basically, the end goal is to be able to access the network storage over eth1, and everyting else over eth0.

Thanks for your help!

---

### Post by evilspoons on 2008-11-05
I may be mistaken, but I think you might have to set the second card to a different local subnet (192.168.1.x vs 192.168.2.x) for this to work. Then the subnet mask of each adapter "blocks off" what that card is responsible for and everything automatically goes the right way. There is no way to tell a program that uses TCP/IP or whatever which network card to use.

---

### Post by ciscosurfer on 2008-11-05
RMSe17,

You can use the -I switch with ping to specify which interface you'd like ping to use.  So you can use```
ping -I eth1 192.168.157.30
```  Also, check the subnet mask you set on the eth1 interface to make sure it matches or in range with the snm of the interface on the iSCSI device.

Check **man ping** for more info.

---

### Post by RMSe17 on 2008-11-06
> **evilspoons said:**
> I may be mistaken, but I think you might have to set the second card to a different local subnet (192.168.1.x vs 192.168.2.x) for this to work. Then the subnet mask of each adapter "blocks off" what that card is responsible for and everything automatically goes the right way. There is no way to tell a program that uses TCP/IP or whatever which network card to use.

I believe it is.  eth0 is getting 128.227.x.x a real IP, while eth1 is set up with 192.168.157.10.     I dont think the subnet mask is forcing the ping 192.168.157.30 to go to eth1, I think it just sends it over eth0, trying to find it on the internet, kinda like when I ping google.com, it automatically tries eth0 and not eth1. I think it does the same in both cases, and does not try eth1.  I could be wrong though..   


Is there a way to basically lock 192.168.157.30 communication to eth1 only?  I was looking at the route command, and I think it might help me, but not quite sure.  I also dont know what the subnet mask should be, other than 255.255.255.0, I don't quite understand the concept behind it.

---

### Post by RMSe17 on 2008-11-06
> **ciscosurfer said:**
> RMSe17,

You can use the -I switch with ping to specify which interface you'd like ping to use.  So you can use```
ping -I eth1 192.168.157.30
```  Also, check the subnet mask you set on the eth1 interface to make sure it matches or in range with the snm of the interface on the iSCSI device.

Check **man ping** for more info.

Thanks, I tried that, and got no response. So I guess something else is set up wrong, maybe the subnet mask.  As I said in the above reply, I dont really understand subnet mask, and what it means, I know the subnet mask for eth1 is currently set to 255.255.255.0.  Also, what should the gateway address be set for eth1?  To the local address of eth1 (192.168.157.10)?

---

### Post by berdux on 2008-12-13
the subnet mask is a number of 32 ones and zeros, where there are some ones followed by some zeros, examples:

11111111111111111111111100000000
this one is 255.255.255.0

11111111111111110000000000000000
this one is 255.255.0.0

11111111111111111111111111110000
this one is 255.255.255.240

11111111111111111111111111000000
this one is 255.255.255.192

11111111111111111111100000000000
this one is 255.255.248.0

the 32 digit binary nymber cannot be something with random ones and zeros, they must be something like the examples, some ones folloewd by some zeros, in total 32 digits.
You divide the binary number in 4 parts of 8 digits, you find the Dec number for every part and you put dots between them. (11111111 is 255, 00000000 is 0, and 11111000 is 248 8) ).
if the subnet mask is 255.255.255.0 it is a C class subnet and is the most commonly used in local area networks.
if the subnet is 255.255.0.0 it is a B class subnet. it means that the folowing 3 IPs are in the same subnet: 
192.168.36.34 
192.168.143.12 
192.168.5.0 (yes in case we have a b class subnet this is a valid ip address)

if our subnet is 255.255.255.252 then the ip addresses below are in different subnets:
192.168.1.1
192.168.1.5
192.168.1.10
and you cannot put (for example) 192.168.1.3 as an ip address in this network because it is the broadcast address for the subnet, the subnet in this case would be brom 0 to 3 (4 ips),or from 4 to 7,or from 8 to 11 (and so on) where the first and the last address of the subnet cannot be used.

sorry for my bad english :)
i hope i helped :)

---

### Post by The Cog on 2008-12-13
This thread is more than a month old, so I guess the problem is over now. But for the record, the routing table is what decides what destinations are reached via which interface. The command **route -n** will show the current routing table, and **sudo route add ...** can be used to add routes. Your default route (the route used for destinations not covered by more specific routes) is 0.0.0.0.

---

