---
title: "Networking:  Default Gateway Specification when External Address is via DHCP"
date: 2014-02-14
forum: Networking &amp; Wireless
---

### Post by dc-spyder on 2014-02-14
Running Ubuntu 10.04 LTS configured as a router/gateway/filter between my in-home network and the internet via FIOS.

QUESTION:  How do I set up a default gateway to route traffic from the in-home network to the internet via 2 NICs when the "outward facing" NIC gets its IP number dynamically through DHCP from Verizon FIOS?



Physical Setup:

FIOS ONT --CAT5-- NIC1 on Ubuntu Server
HOME PCs --CAT5-- SWITCH --CAT5-- NIC2 on Ubuntu Server

NIC1 is therefore my "outward facing" card and NIC2 is my "inward facing" card

This server is running Squid and DansGuardian in transparent proxy mode to filter stuff in my home network for the kids

NIC1 (eth1) gets its IP address via DHCP from Verizon FIOS
NIC2 (eth0) gets a static IP (192.168.2.1)

IFCONFIG output:
```
eth0      Link encap:Ethernet  HWaddr 00:40:f4:a6:09:6c
          inet addr:192.168.2.1  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::240:f4ff:fea6:96c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1447746 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1641315 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:243999342 (243.9 MB)  TX bytes:982892261 (982.8 MB)
          Interrupt:21 Base address:0x1000


eth0:1    Link encap:Ethernet  HWaddr 00:40:f4:a6:09:6c
          inet addr:192.168.2.2  Bcast:192.168.2.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interrupt:21 Base address:0x1000


eth1      Link encap:Ethernet  HWaddr 70:71:bc:18:22:10
          inet addr:72.66.10.121  Bcast:72.66.10.255  Mask:255.255.255.0
          inet6 addr: fe80::7271:bcff:fe18:2210/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1606434 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1344333 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:994245307 (994.2 MB)  TX bytes:232342460 (232.3 MB)
          Interrupt:28 Base address:0xe000


eth1:1    Link encap:Ethernet  HWaddr 70:71:bc:18:22:10
          inet addr:192.168.1.1  Bcast:192.168.1.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interrupt:28 Base address:0xe000


lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:262325 errors:0 dropped:0 overruns:0 frame:0
          TX packets:262325 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:334090356 (334.0 MB)  TX bytes:334090356 (334.0 MB)


virbr0    Link encap:Ethernet  HWaddr de:52:a2:ef:4d:05
          inet addr:192.168.122.1  Bcast:192.168.122.255  Mask:255.255.255.0
          inet6 addr: fe80::dc52:a2ff:feef:4d05/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:30 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 B)  TX bytes:4772 (4.7 KB)
```

ROUTE output:
```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.2.0     *               255.255.255.0   U     0      0        0 eth0
192.168.1.0     *               255.255.255.0   U     0      0        0 eth1
72.66.10.0      *               255.255.255.0   U     0      0        0 eth1
192.168.122.0   *               255.255.255.0   U     0      0        0 virbr0
default         L100.WASHDC-VFT 0.0.0.0         UG    0      0        0 eth1
```



----------------------------------------------------------------------------------

When I set up the default gateway to the IP address assigned to me by Verizon (72.66.10.X) I get the above setup and everything works great.

What I'm concerned about is when Verizon decides to give me a new (via DHCP) IP number.  I assume that my default gateway definition will now be wrong and access to the internet will be broken.

I thought I'd create a virtual network (192.168.1.0) and assign a static IP of 192.168.1.1 to eth1:1.  Then I'd create a default gateway to 192.168.1.1 and no matter what IP number Verizon sets me up with, my static IP (192.168.1.1) will always be assigned to the same NIC.

But this doesn't work.  I'm assuming that it is because I am not explicitly forwarding packets from 192.168.1.1 to Verizon's assigned IP number.  What do I have to do to pass all traffic from 192.168.1.1 to whatever IP Verizon FIOS sets me up with on the same NIC (as eth1)?

Does this accomplish my goal of having my network continue to work if/when Verizon sets me up with a new IP address via DHCP?

Thanks.

---

### Post by ian-weisser on 2014-02-14
> **dc-spyder said:**
> QUESTION:  How do I set up a default gateway to route traffic from the in-home network to the internet via 2 NICs when the "outward facing" NIC gets its IP number dynamically through DHCP[...]?

Well, when I used Ubuntu to create a router, I simply assigned the WAN (outward-facing) interface to be DHCP in /etc/network/interfaces.

The route command was not used at all. Since your kernel's iptables will handle NAT and MASQUERADE, and since your kernel is set to pass through packets, the kernel will handle proper routing automatically.

I didn't use the extra complexity of a VPN.

---

### Post by bab1 on 2014-02-14
> **dc-spyder said:**
> 

```
ROUTE output:


Kernel IP routing table
Destination    Gateway         Genmask         Flags Metric   Ref    Use   Iface
[COLOR="#FF0000"]default        L100.WASHDC-VFT 0.0.0.0         UG    0      0        0     eth1[/COLOR]
```

Did you configure the above setting?  This appears to be your FIOS gateway the: [COLOR="#FF0000"]UG[/COLOR] flag is the Up Gateway for the iface eth1

---

### Post by dc-spyder on 2014-02-15
> **bab1 said:**
> Did you configure the above setting?  This appears to be your FIOS gateway the: [COLOR=#FF0000]UG[/COLOR] flag is the Up Gateway for the iface eth1

Yes, I created that default route manually, [sudo route add default gw 72.66.10.XXX) as it was the only way that I could get internet connectivity from within my home network.

Where else could I define that I want all traffic on 192.168.2.* (on eth0) that is destined for the internet to go through eth1 with the wrinkle that I don't know when the actual IP number assigned to eth1 from Verizon FIOS DHCP will change?

---

### Post by bab1 on 2014-02-15
> **dc-spyder said:**
> Yes, I created that default route manually, [sudo route add default gw 72.66.10.XXX) as it was the only way that I could get internet connectivity from within my home network.

Where else could I define that I want all traffic on 192.168.2.* (on eth0) that is destined for the internet to go through eth1 with the wrinkle that I don't know when the actual IP number assigned to eth1 from Verizon FIOS DHCP will change?

Typically the term gateway refers to the nearside (LAN) interface of the network.  You don't need to manage the WAN side.  The router is the dividing point between your network and the FIOS network.  The router itself should forward all traffic to eth1 via forwarding.  I assume you did set forwarding to on when you configured the router, if not then you need to do that first.  Then I would try setting the gateway on your LAN hosts to the eth0 interface of your router.

---

### Post by dc-spyder on 2014-02-15
Where do I set forwarding in Ubuntu?  And does this in any way undermine the firewall/content filtering aspects of the server?

---

### Post by bab1 on 2014-02-15
> **dc-spyder said:**
> Where do I set forwarding in Ubuntu?  

Edit sysctl.conf to make sure ipv4 forwards correctly:
```
#sudo vi /etc/sysctl.conf

```
Change the =0 to a =1 and remove the comment:
```
# Uncomment the next line to enable packet forwarding for IPv4
net.ipv4.ip_forward=1

```
Add this as well:
```
# sudo echo 1 > /proc/sys/net/ipv4/ip_forward
```
You can see a reference to setting forwarding in [this article]("http://www.larmeir.com/2010/09/configuring-a-router-with-content-filtering-on-ubuntu-10-04-lts/").

> 
And does this in any way undermine the firewall/content filtering aspects of the server?

The short answer is, YES!  

You have no choice.  You *must to set forwarding to have the Ubuntu host work as a router*.  A routers primary function is to transition IP traffic from one IP network to another.  

The purpose of the firewall is to allow only traffic you desire.  The router/firewall is built in to the Linux kernel.  The interface is IPTables.  This operates on both interfaces.  You have control over incoming and outgoing traffic.  In addition you need to setup NAT'ing to map the single WAN side IP address to the internal private network IP addresses.

You can use UFW, or Shorewall or directly configure IPTables if you wish.  These are not trivial matters.  If you do not understand what you are doing you can leave your network unprotected.

If you have the money I would buy a dd-wrt (Linux) enabled router ($75 to $200) and set it up via the simple GUI interface to IPTables.  Simple and secure.  You just configure and connect your hosts to the Ethernet ports.  If you have a lot of physical machines you may need a simple 8 port unmanaged Ethernet switch to increase connection ports.

---

### Post by dc-spyder on 2014-02-16
Thanks for the references.  I will try to configure it when I get home soon.  

Up until recently, I had a Verizon FIOS Actiontec Router handling the routing and a Linux 10.04 box handling the web server (Apache2), firewall, proxy (Squid), and content filtering (DansGuardian) functions.  

I was having trouble getting traffic to pass through both the router and the firewall/proxy to get my DirecTV GenieGo service to work.  I thought if I could just get rid of the Actiontec Router, it would be easier to figure out how to open up the right ports and get traffic in and out of the home network and be able to use my remote-TV watching application.  

Thanks again.

---

### Post by dc-spyder on 2014-02-16
Well, my Ubuntu system already had forwarding turned on, so that is not my problem.

I'm also having a bit of trouble trying to figure out how to get ports 8082 and 8083 through the Linux Firewall (IPTables).

In the INPUT section, I have it accepting protocol TCP and destination ports 8082 and 8083
In the FORWARD section, I have it accepting protocol TCP on interface eth1 and destination ports 8082 and 8083

Is there a need to specify which IP address to forward these ports through to?  Or does that customarily get done by the outside service?

---

### Post by dc-spyder on 2014-02-16
"[COLOR=#000000]In addition you need to setup NAT'ing to map the single WAN side IP address to the internal private network IP addresses."

By this you mean I have to put in a POSTROUTING Masqurade setting?
[/COLOR]

---

### Post by bab1 on 2014-02-16
> **dc-spyder said:**
> Well, my Ubuntu system already had forwarding turned on, so that is not my problem.

I'm also having a bit of trouble trying to figure out how to get ports 8082 and 8083 through the Linux Firewall (IPTables).

In the INPUT section, I have it accepting protocol TCP and destination ports 8082 and 8083
In the FORWARD section, I have it accepting protocol TCP on interface eth1 and destination ports 8082 and 8083

Is there a need to specify which IP address to forward these ports through to?  Or does that customarily get done by the outside service?

Let me say upfront, I'm certainly no IPTables expert.  You can temporarily try a simple experiment to see if the gateway is correct for all hosts in the LANfirst.  Turn off the web server and any other services that are listening on the network.  You can see what is listening with this command```
sudo netstat -tupl
```
Enable NAT in  IPTables.  See [here]("http://linuxers.org/howto/how-set-nat-linux-using-iptables") for instructions.  Look for the section that has: *ptables -t nat -A POSTROUTING * for the complete instructions.  Once you have set up NAT you can the three tables (INPUT OUTPUT and FORWARD) to ACCEPT *with no rules*.  *Note that this will allow **all** traffic* while NAT maps all the LAN private addresses to the WAN interface IP address.  So at this point all IP traffic should pass in both directions and DirecTV GenieGo service should be working.

I think your questions have morphed enough for you to open a new thread.  I would put it in the Security section and let the experts have at it.  Maybe a title like: How do I configure IPTables to allow DirecTV GenieGo service.  Then you can explain what you have done so far.

You can also search with Google.  I got [this]("https://www.google.com/search?q=IPTables+forward+all&btnG=Go!#q=iptables+for+private+network") using "iptables for private network".  :-)

---

