---
title: "I have two NICs but all LAN traffic uses the one randomly configured at boot."
date: 2014-09-30
forum: Networking &amp; Wireless
---

### Post by Shellbak3 on 2014-09-30
**Server 14.04 single boot.**

I have two NICs, em1 and p3p1.  They both connect to the same router.  I assign 192.168.1.211 to em1 and 192.168.219 to p3p1.  At boot either apparently one or the other becomes the default and I am unable to send LAN traffic on the other.  For instance ping with the -I option works with just one of them.  Is this a bug in 14.04?

Should /etc/network/interfaces be the configuration file?  If so, how should the entries differ? 

Is this a bug in 14.04?

I'm new to networking configuration.

---

### Post by tgalati4 on 2014-09-30
Don't mess with /etc/network/interfaces unless you know how to configure networkmanager.  You have not bonded the two interfaces together--otherwise you would not be asking this question.

[https://help.ubuntu.com/community/UbuntuBonding](https://help.ubuntu.com/community/UbuntuBonding)

[http://askubuntu.com/questions/382577/how-can-i-enable-bonded-network-interfaces-in-ubuntu-13-04-13-10-using-networkma](http://askubuntu.com/questions/382577/how-can-i-enable-bonded-network-interfaces-in-ubuntu-13-04-13-10-using-networkma)

---

### Post by Shellbak3 on 2014-09-30
Thanks for your reply.  I should have been more clear: bonding (which is new to me) is not what I want.  

I want p3p1 to be mapped to 192.168.1.219 and em1 to be mapped to 192.168.1.211  so that I can choose which NIC and, consequently which LAN cable will handle specific traffic. 

FYI
```
 
$ dmesg | grep eth0
[    0.756936] igb 0000:02:00.0: added PHC on eth0
[    0.759099] igb 0000:02:00.0: eth0: (PCIe:2.5Gb/s:Width x1) 00:01:05:19:7d:59
[    0.760097] igb 0000:02:00.0: eth0: PBA No: FFFFFF-0FF
[    0.776545] systemd-udevd[145]: renamed network interface eth0 to p3p1
[    0.873649] e1000e 0000:00:19.0 eth0: registered PHC clock
[    0.874560] e1000e 0000:00:19.0 eth0: (PCI Express:2.5GT/s:Width x1) 00:01:05:19:7d:58
[    0.875454] e1000e 0000:00:19.0 eth0: Intel(R) PRO/1000 Network Connection
[    0.876339] e1000e 0000:00:19.0 eth0: MAC: 11, PHY: 12, PBA No: FFFFFF-0FF
[    0.896659] systemd-udevd[146]: renamed network interface eth0 to em1

```

---

### Post by bab1 on 2014-09-30
> **Shellbak3 said:**
> Thanks for your reply.  I should have been more clear: bonding (which is new to me) is not what I want.  

I want p3p1 to be mapped to 192.168.1.219 and em1 to be mapped to 192.168.1.211  so that I can choose which NIC and, consequently which LAN cable will handle specific traffic. 


You can't have two IP addresses for a single host i**n the same network**.  Configure 1 of the NIC's with and IP address in a different network and they both should be active.  Use something like 10.0.1.0 (255.255.255.0).

---

### Post by Andy_Lawson on 2014-09-30
Hi,

What are you trying to achieve?

1. Network resiliency in case of hardware failure at NIC or switch.
2. Increased bandwidth between NIC and switch.
3. Traffic segregation.

If you connect two NICs to the same subnet as you have done both will be present in the routing table with the same cost, and the network stack will route traffic down one link only. Look at LACP or EtherChannel if you want increased bandwidth and hardware resiliency. I'm not sure how you could segregate traffic - maybe iptables, or interface specifications in the configuration of the software you're using.

Cheers,
Andy.

---

### Post by tgalati4 on 2014-09-30
Perhaps describe the Use Case.  What exactly are you trying to accomplish?  Why wouldn't bonding be sufficient to balance traffic between two lan cards?  If you have a Dual Core processor, you do not specify which core is to process which job--it is all handled quietly in the background.  If you are setting up your computer as a firewall/router/sniffer, then you would use a different topology, with different subnet IP's.

---

### Post by Shellbak3 on 2014-10-01
bab-1 - that didn't work.  I'm not sure what else, if anything, needs changing in the /etc/network/interface file.
Andy -I am attempting to segregate traffic.

The ultimate use will to have a tiny LAN on an aircraft which will use em1 and a router connected to that physical interface.  The other interface, p3p1, will connect directly to a custom research grade Ethernet enabled camera.  

At the moment the camera is in Colorado and I'm in California.  To test the camera and my Java code I'm connecting via a router - both em1 and p3p1 connect to the same router.  I *think* I've fixed one problem, a Ubuntu boot bug, that randomly made one or the other interface active.   I've rebooted a couple of times and the results were predictable: traffic goes out on em1. Ping specifying p3p1 doesn't work.  This doesn't cause a problem with the testing but just won't work when I have the camera in my lab or in the aircraft.

I'd sure like to demonstrate that I can send specific traffic on a specific interface.

Ubuntu bug:
[https://bugs.launchpad.net/ubuntu/+source/biosdevname/+bug/1284043](https://bugs.launchpad.net/ubuntu/+source/biosdevname/+bug/1284043)

---

### Post by SeijiSensei on 2014-10-01
Until you put each interface on its own subnet, you'll have routing problems.  If you did that, then routing will be set up to send packets for each network over the correct interface.  It happens without any extra effort on your part, though if you want to forward packets from one network to the other, you'd need to enable "net.ipv4.ip_forward=1" in /etc/sysctl.conf.

---

### Post by Shellbak3 on 2014-10-01
Thanks, I'm a real novice in networking.  I should use a net mask such as 255.255.255.208 ? 
What else would need changing in the file interfaces?

---

### Post by Shellbak3 on 2014-10-01
Thanks, but that didn't work, is other editing of interfaces required?

---

### Post by Shellbak3 on 2014-10-01
Thanks for the suggestions.  I've tried a new IP address but that didn't work and I've attempted to change the net mask to no avail.  It appears that don't have a complete understanding of all that needs to be changed.

---

### Post by bab1 on 2014-10-01
> **Shellbak3 said:**
> Thanks for the suggestions.  I've tried a new IP address but that didn't work and I've attempted to change the net mask to no avail.  It appears that don't have a complete understanding of all that needs to be changed.
There are a couple of things that we need to diagnose the problems you are having.  More details than just "that didn't work" would be helpful for us to understand what is not working and what to do about that
.
What specifically have you setup?  What is returned when you use these commands?  ```
ifconfig -a

route -n

cat /etc/network/interfaces

cat /proc/sys/net/ipv4/ip_forward
```

Is this a non-gui installation of Ubuntu (e.g. Ubuntu Server Edition)?

---

### Post by Shellbak3 on 2014-10-01
I tried to assign different networks in /etc/network/interfaces.  After rebooting only em1 is active, ping with p3p1 returns an error. Is this how the interfaces should be assigned to different networks and IP addresses?

Here's my interfaces file.
```

auto lo
iface lo inet loopback


auto em1
iface em1 inet static
address 192.168.1.211
netmask 255.255.255.0
network 192.168.1.0
gateway 192.168.1.1
dns-nameservers 99.99.99.53 8.8.8.8 8.8.4.4


auto p3p1
iface p3p1 inet static
address 192.168.2.219
network 192.168.2.0
netmask 255.255.255.0
gateway 192.168.1.1
dns-nameservers 99.99.99.53 8.8.8.8 8.8.4.4

```

---

### Post by Iowan on 2014-10-01
> **Shellbak3 said:**
>   After rebooting only em1 is active, ping with p3p1 returns an error. 
What is the error?
It may be the gateway for p3p1...
What are results of **ifconfig -a**?

---

### Post by bab1 on 2014-10-01
> **Shellbak3 said:**
> I tried to assign different networks in /etc/network/interfaces.  After rebooting only em1 is active, ping with p3p1 returns an error. 

Once again; what is the error message???  Specifically.  

Where is the data for the other commands?  it's all kind of interrelated, so it's all or nothing.
> 

Is this how the interfaces should be assigned to different networks and IP addresses?

Here's my interfaces file.
```

auto lo
iface lo inet loopback


auto em1
iface em1 inet static
address 192.168.1.211
netmask 255.255.255.0
network 192.168.1.0
gateway 192.168.1.1
dns-nameservers 99.99.99.53 8.8.8.8 8.8.4.4


auto p3p1
iface p3p1 inet static
address 192.168.2.219
network 192.168.2.0
netmask 255.255.255.0
gateway 192.168.1.1
dns-nameservers 99.99.99.53 8.8.8.8 8.8.4.4

```

Everything is okay as far as pinging the two interfaces from this host.  The dns is only needed if you are using DNS names outside of the LAN and the same is true regarding the gateway address.  I don't think you need a gatway address on the p3p1 interface anyway.  It should forward all traffic to the em1 interface.  I assume the p3p1 interface is the downstream side.

---

### Post by tgalati4 on 2014-10-01
The "network 192.168.1.0" stanza is deprecated and should be removed.  You are attempting to define a Class-C subnet, not Class-D, so your netmask should be 255.255.0.0 for both interfaces.

You may also need a *route* statement to specifically tell your computer to route traffic from one subnet to the other if there is no router between your devices.

I would have never guessed your Use Case from your original post, nor from the title of your thread.  A diagram showing the topology is helpful.

---

### Post by bab1 on 2014-10-01
> **tgalati4 said:**
> The "network 192.168.1.0" stanza is deprecated and should be removed.  You are attempting to define a Class-C subnet, not Class-D, so your netmask should be 255.255.0.0 for both interfaces.
These are **two different ** networks and as such the subnet mask of 255.255.255.0 on both is appropriate.

---

### Post by bab1 on 2014-10-01
> **tgalati4 said:**
> The "network 192.168.1.0" stanza is deprecated and should be removed.  You are attempting to define a Class-C subnet, not Class-D, so your netmask should be 255.255.0.0 for both interfaces.

You may also need a *route* statement to specifically tell your computer to route traffic from one subnet to the other if there is no router between your devices.

Any multi-homed (multiple NIC's) host that forwards packets between networks (inter-networking) is by definition a router.  The OP is indeed creating a router.  The upstream side (em1 I believe) could be considered the WAN side.  The other side is a network with only 1 device (the camera.  The OP will have one network consisting of two subnets inter-networked with a router.  
> 

I would have never guessed your Use Case from your original post, nor from the title of your thread.  I diagram showing the topology is helpful.

The real question is: Why do this?  There is no security need and there is no performance gain.  I would just connect the two devices (one of the Ubuntu hosts NIC's and the camera) via a simple switch.  However, I don't think we have all the facts.  Maybe there is an overriding concern that the OP can reveal.

---

### Post by Shellbak3 on 2014-10-02
Thanks for your help.  I think I have/had two problems:

 1. on boot there was a problem with the interface being named incorrectly at random.  After my first post I think I found a fix for that.

2. This machine has the 64 bit Ubutntu 14.04 server installed it.  I have installed a minimal Gnome for development and testing and start it from the command line.  When deployed Gnome won't start and there will be no GUI.  My software will start automatically after boot.  It will be deployed on a small twin engine aircraft and will run the camera and a couple other devices.  The user will supply a tablet or notebook and run it from the the LAN which is confined to the aircraft - probably using WiFi.  One port will be wired to a wireless router.

The other port connects to the camera whose embedded computer is constrained to use UDP for communications.  I can't have that connected to the router because UDP is not reliable.

The bottom line is one physical port must connect to the router for the tiny LAN and the other to the camera.

The current situation is that we are testing the camera and debugging from my lab which has a router that connects to a DSL router and then the internet.  I am attempting to simulate the direct connection (it's a kind of proof of concept, too) to the camera by sending camera commands and receiving camera data on one physical interface using TCP and everything else on the other interface but using one router.  (For this the camera in Colorado has another computer connected to it that acts as an interface.)

With the configuration I have only one interface actually transmits anything - I can disconnect the idle cable and there's no change but disconnecting the other means there's no internet connection. 

I've been writing software as an adjunct to my jobs for some time but I've not needed to learn much about networking and don't understand many details or lingo.

When I do have the camera in my possession I won't be able to modify the embedded code.

Requested information:

```

$ ifconfig -a
em1   Link encap:Ethernet  HWaddr 00:01:05:19:7d:58            inet addr:192.168.1.211  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::201:5ff:fe19:7d58/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:10268 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8203 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:8258797 (8.2 MB)  TX bytes:1574355 (1.5 MB)
          Interrupt:20 Memory:f7c00000-f7c20000 


lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:202 errors:0 dropped:0 overruns:0 frame:0
          TX packets:202 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:15695 (15.6 KB)  TX bytes:15695 (15.6 KB)


p3p1      Link encap:Ethernet  HWaddr 00:01:05:19:7d:59  
          inet addr:192.168.2.219  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::201:5ff:fe19:7d59/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:650 errors:0 dropped:0 overruns:0 frame:0
          TX packets:99 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:113767 (113.7 KB)  TX bytes:17071 (17.0 KB)
          Memory:f7b00000-f7b20000 

```

```

$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 em1
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 em1
192.168.2.0     0.0.0.0         255.255.255.0   U     0      0        0 p3p1

```

```

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).


# The loopback network interface
auto lo
iface lo inet loopback


# The primary network interface (first NIC)
auto em1
iface em1 inet static
address 192.168.1.211
netmask 255.255.255.0
network 192.168.1.0
gateway 192.168.1.1
dns-nameservers 99.99.99.53 8.8.8.8 8.8.4.4


# Secondary network interface (second NIC) needs edit for direct connection
auto p3p1
iface p3p1 inet static
address 192.168.2.219
network 192.168.2.0
netmask 255.255.255.0
gateway 192.168.1.1
dns-nameservers 99.99.99.53 8.8.8.8 8.8.4.4

```

```

$ cat /proc/sys/net/ipv4/ip_forward
0

```

```

 cat /etc/udev/rules.d/70-persistent-net.rules
SUBSYSTEM=="net", ATTR{address}=="00:01:05:19:7d:58", NAME="em1"
SUBSYSTEM=="net", ATTR{address}=="00:01:05:19:7d:59", NAME="p3p1"



```

```
 
$ dmesg | grep eth[    0.745018] igb 0000:02:00.0: added PHC on eth0
[    0.747039] igb 0000:02:00.0: eth0: (PCIe:2.5Gb/s:Width x1) 00:01:05:19:7d:59
[    0.747904] igb 0000:02:00.0: eth0: PBA No: FFFFFF-0FF
[    0.881798] e1000e 0000:00:19.0 eth1: registered PHC clock
[    0.882647] e1000e 0000:00:19.0 eth1: (PCI Express:2.5GT/s:Width x1) 00:01:05:19:7d:58
[    0.883478] e1000e 0000:00:19.0 eth1: Intel(R) PRO/1000 Network Connection
[    0.884334] e1000e 0000:00:19.0 eth1: MAC: 11, PHY: 12, PBA No: FFFFFF-0FF
[    1.477107] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[    1.477111] IPv6: ADDRCONF(NETDEV_UP): eth1: link is not ready
[    1.617409] systemd-udevd[381]: renamed network interface eth1 to em1
[    1.653889] systemd-udevd[379]: renamed network interface eth0 to p3p1

```

---

### Post by bab1 on 2014-10-02
> **Shellbak3 said:**
> Thanks for your help.  I think I have/had two problems:

 1. on boot there was a problem with the interface being named incorrectly at random.  After my first post I think I found a fix for that.

You can eliminate the renaming of the interfaces by killing the app ***biosdevname*** or you can just remove it completely.  This will leave you with eth0 and eth1 etc.  Just like it always has been in the past.
> 
2. This machine has the 64 bit Ubutntu 14.04 server installed it.  I have installed a minimal Gnome for development and testing and start it from the command line.  When deployed Gnome won't start and there will be no GUI.  My software will start automatically after boot.  It will be deployed on a small twin engine aircraft and will run the camera and a couple other devices.  

So how many devices is your software running on?  What are these devices? Is the "... machine [that] has the 64 bit Ubutntu 14.04 server installed it" a laptop?
> 
The user will supply a tablet or notebook and run it from the the LAN which is confined to the aircraft - probably using WiFi.  One port will be wired to a wireless router.

In theory you don't need a router at all.  You could conceivably run all of this off a 8 port switch and a wireless AP.   That sounds more like what you are doing when you use the above
> 
The other port connects to the camera whose embedded computer is constrained to use UDP for communications.  I can't have that connected to the router because UDP is not reliable.

This makes no networking sense.  If you know the line is good then the only difference is the error checking.  UDP is used when you don't  need error checking, such as broadcasts or where the user will as if there is no connection.  It's really not for data validation.
> 

The bottom line is one physical port must connect to the router for the tiny LAN and the other to the camera.

The current situation is that we are testing the camera and debugging from my lab which has a router that connects to a DSL router and then the internet.  I am attempting to simulate the direct connection (it's a kind of proof of concept, too) to the camera by sending camera commands and receiving camera data on one physical interface using TCP and everything else on the other interface but using one router.  (For this the camera in Colorado has another computer connected to it that acts as an interface.)

With the configuration I have only one interface actually transmits anything - I can disconnect the idle cable and there's no change but disconnecting the other means there's no internet connection. 

I've been writing software as an adjunct to my jobs for some time but I've not needed to learn much about networking and don't understand many details or lingo.

When I do have the camera in my possession I won't be able to modify the embedded code.

Requested information:

```

$ ifconfig -a
em1   Link encap:Ethernet  HWaddr 00:01:05:19:7d:58
           inet addr:192.168.1.211  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::201:5ff:fe19:7d58/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:10268 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8203 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:8258797 (8.2 MB)  TX bytes:1574355 (1.5 MB)
          Interrupt:20 Memory:f7c00000-f7c20000 


lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:202 errors:0 dropped:0 overruns:0 frame:0
          TX packets:202 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:15695 (15.6 KB)  TX bytes:15695 (15.6 KB)


p3p1      Link encap:Ethernet  HWaddr 00:01:05:19:7d:59  
          inet addr:192.168.2.219  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::201:5ff:fe19:7d59/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:650 errors:0 dropped:0 overruns:0 frame:0
          TX packets:99 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:113767 (113.7 KB)  TX bytes:17071 (17.0 KB)
          Memory:f7b00000-f7b20000 

```

This shows that both interfaces are active
> 
```

$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 em1
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 em1
192.168.2.0     0.0.0.0         255.255.255.0   U     0      0        0 p3p1

```

This shows that both interfaces are up and the gateway is on the 192.168.1.0 /24 network (em1)
>  
```

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).


# The loopback network interface
auto lo
iface lo inet loopback


# The primary network interface (first NIC)
auto em1
iface em1 inet static
address 192.168.1.211
netmask 255.255.255.0
network 192.168.1.0
gateway 192.168.1.1
dns-nameservers 99.99.99.53 8.8.8.8 8.8.4.4


# Secondary network interface (second NIC) needs edit for direct connection
auto p3p1
iface p3p1 inet static
address 192.168.2.219
network 192.168.2.0
netmask 255.255.255.0
gateway 192.168.1.1
dns-nameservers 99.99.99.53 8.8.8.8 8.8.4.4

```

This is good.
> 
```

$ cat /proc/sys/net/ipv4/ip_forward
0

```

This is not correct.  You need to forward all packets both to and from both networks (192.168.1.0 /24 and 192.168.12.0 /24).  See @ SeijiSensei's comments in post #8.  Most likely this is what is failing. 
> 
```

 cat /etc/udev/rules.d/70-persistent-net.rules
SUBSYSTEM=="net", ATTR{address}=="00:01:05:19:7d:58", NAME="em1"
SUBSYSTEM=="net", ATTR{address}=="00:01:05:19:7d:59", NAME="p3p1"


```

This is fine.  My own personal taste would be to rename them back to eth0 and eth1, but that's just me.
> 
```
 
$ dmesg | grep eth[    0.745018] igb 0000:02:00.0: added PHC on eth0
[    0.747039] igb 0000:02:00.0: eth0: (PCIe:2.5Gb/s:Width x1) 00:01:05:19:7d:59
[    0.747904] igb 0000:02:00.0: eth0: PBA No: FFFFFF-0FF
[    0.881798] e1000e 0000:00:19.0 eth1: registered PHC clock
[    0.882647] e1000e 0000:00:19.0 eth1: (PCI Express:2.5GT/s:Width x1) 00:01:05:19:7d:58
[    0.883478] e1000e 0000:00:19.0 eth1: Intel(R) PRO/1000 Network Connection
[    0.884334] e1000e 0000:00:19.0 eth1: MAC: 11, PHY: 12, PBA No: FFFFFF-0FF
[    1.477107] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[    1.477111] IPv6: ADDRCONF(NETDEV_UP): eth1: link is not ready
[    1.617409] systemd-udevd[381]: renamed network interface eth1 to em1
[    1.653889] systemd-udevd[379]: renamed network interface eth0 to p3p1

```
This shows the same interfaces up.  Note that IPv6 is not working nor is it needed.

Here is what I think.  You haven't provided a valid networking reason to have a 2 network LAN.  At this point my guess is that you really don't need this much complexity.  I have attached 2 JPG's that show the different topologies.  The one that you are currently favoring is the 2net.jpg version.  Note that the Ununtu host serves as a router and the DSL router is really 2 parts.  You really are only using the switch component of this router.  When you are aloft there will be no IP traffic on the WAN side.  I don't think Internet connectivity is needed.  Is it?

I don't really see any advantage over the single net solution I have diagrammed in  1net.jpg.  Almost all of your packet traffic will be Ethernet with no need to route anything.  UDP or TCP it doesn't matter at this point.

At the very least we can use these jpg's for common reference and terms.

 I understand your explanation at the top of this post.  Again, please explain why you need to separate the camera from the other devices by using the Ubuntu host as a router and 2 networks between the camera and the those devices.   In the beginning you were willing to put the camera on the same network.  What is the use case for the Ubuntu host?

---

### Post by Shellbak3 on 2014-10-03
Thanks, I've been a bit to busy to work on this problem today but was able to make diagrams of my two configuration.  One is the development configuration.  When the camera is delivered I'll move to the Aircraft configuration.  In either case I want to control which NIC carries which communication.  I'll reply again later.

---

### Post by bab1 on 2014-10-03
> **Shellbak3 said:**
> Thanks, I've been a bit to busy to work on this problem today but was able to make diagrams of my two configuration.  One is the development configuration.  When the camera is delivered I'll move to the Aircraft configuration.  In either case I want to control which NIC carries which communication.  I'll reply again later.

If you insist on this configuration, so be it.  You have been given the answer to the routing problem and the reasoning behind it. As you are going to use the Ubuntu Desktop as a router, you must set forwarding on.  Once that is done the Ubuntu host will forward all packets from one network to the other in both directions.  

It doesn't matter which diagram you use as we are only talking about the Ubuntu Desktop that is directly connected (DC) to the camera.  The host will pick the appropriate route.  If there is only one way to talk to the camera then it will use the DC interface.  You need to make sure there are no routing loops (multiple) routes to the host.  This is bad practice anyway.

What more is there to say?

---

