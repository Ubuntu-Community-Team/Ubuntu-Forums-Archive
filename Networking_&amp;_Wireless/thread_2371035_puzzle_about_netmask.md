---
title: "puzzle about netmask"
date: 2017-09-09
forum: Networking &amp; Wireless
---

### Post by holiday2 on 2017-09-09
My LAN address range is 192.168.0.* There's a better way of putting that but I'm not sure of it.

However I have one host that must have 192.168.56.n.

Here's the puzzle:

192.168.56.200/24 can ping 192.168.0.212/24

but the 0.212 host can not ping the 56.200 host. 

I guess the fix is to switch the masks  to 255.255.0.0  and that's just fine with me, but I think if I knew the answer to this puzzle I would understand something worth understanding. 

Thank you very much.

---

### Post by SeijiSensei on 2017-09-10
Are these machines on the same physical network?  Please show us the output from "route -n" on each machine inside [noparse]```

```[/noparse] tags.

---

### Post by TheFu on 2017-09-10
How smart is your switch and/or router? Those can solve things that shouldn't work.

---

### Post by holiday2 on 2017-09-10
> **SeijiSensei said:**
> Are these machines on the same physical network?  Please show us the output from "route -n" on each machine inside [noparse]```

```[/noparse] tags.

Thank you. Yes a bit of context is in order and after consideration of that perhaps this should move to virtualization. 

I'm working with a number of virtual machines - VirtualBox. Until recently I've been using a bridged adapter and all has been well.

However in  trying out Budgie 17.10Beta1, I, could not assign a working static IP to the bridged adapter and had to resort to a 2-adapter solution with Host Only in the first slot and NAT in the second. And through that discovered my puzzle. 
I could have tossed the Budgie beta but I am interested in the puzzle. 

Why can the 192.168.56 hosts ping the 192.168.0 hosts but not vice versa..

In answer to your question:

```
From 192.168.56.215 on Asus Machine #1
Budgie 17.04 VB 5.1.26
Adapters
Host Only enp0s3 inet 192.168.56.215  netmask 255.255.255.0  broadcast 192.168.56.255
NAT       enp0s8 inet 10.0.3.15  netmask 255.255.255.0  broadcast 10.0.3.255




Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         10.0.3.2        0.0.0.0         UG    0      0        0 enp0s8
10.0.3.0        0.0.0.0         255.255.255.0   U     0      0        0 enp0s8
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 enp0s3
172.17.0.0      0.0.0.0         255.255.0.0     U     0      0        0 docker0
192.168.56.0    0.0.0.0         255.255.255.0   U     0      0        0 enp0s3


stephen@vm-budgie-1704:~$ ping 192.168.0.212
PING 192.168.0.212 (192.168.0.212) 56(84) bytes of data.
64 bytes from 192.168.0.212: icmp_seq=1 ttl=63 time=1.78 ms

```

```
From 192.168.0.212 on Asus Machine #1
Mate 17.04 on VB 5.1.26
Adapters
Bridged enp0s3 inet 192.168.0.211  netmask 255.255.255.0  broadcast 192.168.0.255


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.0.1     0.0.0.0         UG    0      0        0 enp0s3
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 enp0s3
192.168.0.0     0.0.0.0         255.255.255.0   U     0      0        0 enp0s3


stephen@vm-asus-mate-1704:~$ ping 192.168.56.215
PING 192.168.56.215 (192.168.56.215) 56(84) bytes of data.

```.....

---

### Post by holiday2 on 2017-09-10
> **TheFu said:**
> How smart is your switch and/or router? Those can solve things that shouldn't work.

It's a Hitron, supplied by my ISP. A Modem/Router combo. Not a lot to it. But I can see this:

[TABLE="class: table table-bordered table-striped success, width: 100%"]
[TR]
[TD]Host Name[/TD]
[TD]IP Address[/TD]
[TD]MAC Address[/TD]
[TD]type[/TD]
[TD]Interface[/TD]
[TD]Status[/TD]
[/TR]
[TR]
[TD="bgcolor: #F5F5F5"]Unknown[/TD]
[TD="bgcolor: #F5F5F5"]192.168.0.200[/TD]
[TD="bgcolor: #F5F5F5"]00:22:fb:d1:e5:6e[/TD]
[TD="bgcolor: #F5F5F5"]Self-assigned[/TD]
[TD="bgcolor: #F5F5F5"]WiFi-2.4G[/TD]
[TD="bgcolor: #F5F5F5"][COLOR=#FFFFFF]**Active**[/COLOR]
[/TD]
[/TR]
[TR]
[TD]SamsungPC-PC[/TD]
[TD]192.168.0.203[/TD]
[TD]00:26:b6:86:c5:4c[/TD]
[TD]DHCP-Reserved[/TD]
[TD]WiFi-2.4G[/TD]
[TD][COLOR=#FFFFFF]**Active**[/COLOR]
[/TD]
[/TR]
[TR]
[TD="bgcolor: #F9F9F9"]Asus[/TD]
[TD="bgcolor: #F9F9F9"]192.168.0.202[/TD]
[TD="bgcolor: #F9F9F9"]a4:02:b9:b0:02:fc[/TD]
[TD="bgcolor: #F9F9F9"]DHCP-Reserved[/TD]
[TD="bgcolor: #F9F9F9"]WiFi-5G[/TD]
[TD="bgcolor: #F9F9F9"][COLOR=#FFFFFF]**Active**[/COLOR]
[/TD]
[/TR]
[TR]
[TD]192.168.0.212[/TD]
[TD]Self-assigned[/TD]
[TD]WiFi-5G[/TD]
[TD][COLOR=#FFFFFF]**Active**[/COLOR]
[/TD]
[/TR]
[TR]
[TD="bgcolor: #F9F9F9"]Unknown[/TD]
[/TR]
[/TABLE]


Now Perhaps this is where I should be setting the netmask. 
[h=2]Private LAN Setting[/h][COLOR=#333333][FONT=&quot][TABLE="class: table table-bordered table-striped, width: 100%"]
[TR]
[TD]Private LAN IP Address[/TD]
[TD="class: control-group, bgcolor: #F9F9F9"][/TD]
[/TR]
[TR]
[TD]Subnet Mask[/TD]
[TD="class: control-group"][/TD]
[/TR]
[TR]
[TD="bgcolor: #F9F9F9"]LAN DHCP Status[/TD]
[TD="class: control-group, bgcolor: #F9F9F9"]EnabledDisabledDHCP Reservation
[/TD]
[/TR]
[TR]
[TD]DHCP Lease Time[/TD]
[TD="class: control-group"] 30 Minutes 1 Hour 2 Hours 6 Hours 1 Day 2 Days 1 Week 2 Weeks Forever [/TD]
[/TR]
[TR]
[TD="bgcolor: #F5F5F5"]DHCP Start IP[/TD]
[TD="class: control-group, bgcolor: #F5F5F5"][/TD]
[/TR]
[TR]
[TD]DHCP End IP[/TD]
[TD="class: control-group"][/TD]
[/TR]
[/TABLE]

[/FONT][/COLOR]
[COLOR=#333333][FONT=&quot][/FONT][/COLOR]

---

### Post by SeijiSensei on 2017-09-10
Use traceroute instead of ping to see where the connection stops.  I'll take a look at the routing tables in a little while.

You might need to install the traceroute package.

---

### Post by SeijiSensei on 2017-09-10
OK, in the first instance where you can ping, there is a default route via 10.0.3.2, which I suspect is the address given to the VB host providing NAT services.  Those packets get rewritten by the host and sent out on the network with the host's IP address.  Your router knows what to do with that traffic since it handles 192.168.0.0/24.

In the second instance packets go to your Hiltron router at 192.168.0.1.  It has no idea what to do with packets addressed to 192.168.56.0/24.  It treats them like all other "default" traffic and sends them upstream to the ISP whereupon they are eaten.  You could try adding a static route on the Hiltron to send traffic for 192.168.56.0/24 to the correct location.  Sadly I'm not sure what the "correct location" would be in your case.  I've never used a host-only adapter and have no idea how packets are routed to such a device.

---

### Post by holiday2 on 2017-09-10
Thanks. What do you think of setting the router's netmask to 16 bits? I'm wary of fiddling with it. Worst case I'd have to reset it but I'd like to avoid setting it all up again. IPs to MAC address... and all that toodley doo. 

Here's your traceroute if you're still interested:
> root@vm-asus-mate-1704:/home/stephen# traceroute 192.168.56.205
traceroute to 192.168.56.205 (192.168.56.205), 30 hops max, 60 byte packets
 1  gateway (192.168.0.1)  4.392 ms  4.338 ms  4.329 ms
 2  184.66.224.1 (184.66.224.1)  16.722 ms  24.917 ms *
 3  rd2cv-be101-1.gv.shawcable.net (64.59.162.137)  29.831 ms  25.731 ms  29.803 ms
 4  rd2bb-be50.no.shawcable.net (66.163.72.9)  32.137 ms  32.086 ms  33.063 ms
 5  rc1st-be60.vc.shawcable.net (66.163.68.129)  31.087 ms  31.089 ms  31.082 ms
 6  rc3no-be11-1.cg.shawcable.net (66.163.72.69)  54.640 ms  28.896 ms *
 7  * * *
...
30  ***


> root@vm-budgie-1710b:/hd2/projects/linux# traceroute -T 192.168.0.212
traceroute to 192.168.0.212 (192.168.0.212), 30 hops max, 60 byte packets
 1  gateway (10.0.3.2)  1.100 ms  0.996 ms  0.896 ms
 2  192.168.0.212 (192.168.0.212)  1003.655 ms  1003.901 ms  1003.474 ms



Interesting that without the -T for the second snip, traceoute runs off the edge. For the first it makes no difference.

---

### Post by TheFu on 2017-09-10
hostonly networking is for VM-to-VM communications.  They will not leave the host.  The vbox manpage explains that.
[https://www.virtualbox.org/manual/ch06.html#network_hostonly](https://www.virtualbox.org/manual/ch06.html#network_hostonly)

I would always use a bridged-network myself, unless I wanted to block all outside access, then I'd run NAT and not do any specific port forwarding.

In your situation, this really isn't a network question for 1/3rd of the issue. It is a virtualbox network config question/understanding issue.

---

### Post by holiday2 on 2017-09-10
Yes. Host only uses a virtual network managed by the hypervisor. In this case the virtual network is on the 192.168.56 subnet. 
So how is it that the virtual network can see the network accessed by the bridged adapters, but the bridged adapters cannot see the virtual network? 

That's another way of putting the puzzle. 

My experience is that host only adapters are necessary where you want a static IP in network simulation within a network that refuses requests for static IPs -- such as an enterprise managed network. This is how I started to use host only -- at work where I was working with some network tools. 

Then recently I found that with some versions of Ubuntu, my bridged adapters were not going internet. So I tried the dual adapter approach: host only in slot one and NAT in slot two. 

That's when I came across this puzzle. At home now I have enough inter-host communication for my experiments -- using the dual adapter approach -- but I still have this puzzle.

---

### Post by TheFu on 2017-09-11
The bridged-network is how to make your VMs like regular physical machine connections.  If networking that way isn't working, it is probably something outside the VMs causing the issue.

You can't just change the subnet if the router doesn't understand that too.  If you want complex routing on the single physical host with all VMs doing strange things, perhaps running a routerOS inside the VM can do what you want?  I run pfSense on a VM for my internal network stuff managing 3 subnets.

---

### Post by SeijiSensei on 2017-09-11
The first traceroute shows the problem I described. Without a static route for the 192.168.56.0/24 network the router sends that traffic upstream to your ISP.

---

### Post by holiday2 on 2017-09-11
Thanks. 
It looks like my ISP-provided hitron does not support static routing. I may have to get my own router.
I have found discussion on my ISP's forum I'll follow up on that. 

theFu suggests a routerOS. That sounds interesting. I'll look into that too.

Thanks very much for your help SeijiSensei. Much appreciated.

---

### Post by holiday2 on 2017-09-11
Thank you, TheFu. I will look into pfSense. It sounds interesting. 
Thanks again.
All the best.

---

### Post by SeijiSensei on 2017-09-12
I use routers that support the open-source Linux distribution called DD-WRT.  It can do pretty much everything you'd want, and it has a web-based interface.

Here's the (long) list of supported routers: [http://www.dd-wrt.com/wiki/index.php/Supported_Devices](http://www.dd-wrt.com/wiki/index.php/Supported_Devices)

You can also look up specific models in the database: [http://www.dd-wrt.com/site/support/router-database](http://www.dd-wrt.com/site/support/router-database)

---

### Post by holiday2 on 2017-09-12
Thanks!

---

### Post by TheFu on 2017-09-12
I'd run a linux or BSD-based router OS inside a VM for internal routing. No need for more hardware.
But if you do go with hardware, beware that just because the openwrt or dd-wrt lists something in their supported list, that doesn't mean any recent version is available.  For example, my old hardware didn't get any new releases in the last 5 years!  

When it comes to WAN routers, I've given up on any pre-purchased HW from any of the famous brands.  They just don't make patches quickly enough or long enough to support their $150 price tags, IMHO.  I'd rather spend $140 for a general x86 router machine and load a minimal Linux or BSD then configure it to be a router.  Then I know that the kernel is patched as often as needed and any support programs, network tools, firewall stuff is patched as quickly as the base OS.  I'm happy to spend $140 for a 10+ year lifespan on a router.  I love that swapping wifi-APs because they are external to the router is trivial too.  

But I'd load up a few router OSes into VMs to see which does what you want, but not too much (added complexity is bad), assuming you don't want to just do it yourself based on a minimal Ubuntu Server. [https://arstechnica.com/gadgets/2016/04/the-ars-guide-to-building-a-linux-router-from-scratch/](https://arstechnica.com/gadgets/2016/04/the-ars-guide-to-building-a-linux-router-from-scratch/)  pfsense, opensense, smoothwall, ipcop, openwrt, dd-wrt all have x86 releases.   

I happen to prefer pfSense, but only use the core functionality. The upgrade process for it is pretty great.

---

### Post by holiday2 on 2017-09-12
Hmm... Thanks TheFu. The arstechnica sounds like a very interesting project. Certainly a challenge but worth the try. 

Thanks again.

---

