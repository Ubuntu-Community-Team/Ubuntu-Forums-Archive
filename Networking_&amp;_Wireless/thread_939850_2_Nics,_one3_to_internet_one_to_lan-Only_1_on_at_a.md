---
title: "2 Nics, one3 to internet one to lan-Only 1 on at any 1 time"
date: 2008-10-06
forum: Networking &amp; Wireless
---

### Post by pfbroome on 2008-10-06
Greetings all,

I have looked and cannot find my problem so here goes:

I have an Ubuntu server (current released version) with 2 nic's in it, an internet connection via RoadRunner, a small Ethernet switch and my internal hardware firewall.

This server will, generally, need to be accessible via the internet. Sometimes, we may want to connect it to our internal LAN but we NEVER want both nic's enabled simultaneously. I want to use a script that will turn off the nic connected to our internal LAN and ONLY THEN turn on the nic for the our internet connection. Of course, I also need a script to do the reverse.

The reason, of course, is security. I REALLY don't want this machine to have logical access to our internal LAN while it is accessible over the net.

Now, please be patient with me; I know most everyone here knows ALL of what comes next but I am the kind of person who need to "write out" all the significant processes or steps, to help me insure I am not missing something or that I don't really understand a particular step.

RoadRunner will assign up to (I think) 5 DHCP addresses per physical cable/cable modem connection.  Our current wiring has the output from the cable modem feeding into a small 100Mbs switch. Connected to this switch is my internal hardware firewall device. When the firewall device boots, RoadRunner will assign DHCP address to the WAN connection on the firewall. 

When the server is properly configured it also will connect to the small Ethernet switch. Likewise, when the server boots, it will request a DHCP address from RoadRunner and be assigned one. 

So, complication number one is that I have to have a DHCP client interface in my Ubuntu server to connect to RoadRunner.  The server interface that connects to my internal LAN, however, is a static address (easier name resolution,maintenance etc.).

Turning the nic's on or off is clear (ifconfig...) but I am not sure about the other configuration parameters. I must support DHCP on one nic and static addressing on the other. My belief is that I just need to put the appropriate lines into /etc/network/interfaces but looking at some of the other threads in this forum that seem to have some similarity to my situation is making me think there is more to this than that....Of course, It is entirely possible that I am wrong and it is that simple (PLEASE, tell me it is that simple...).

Any and all help is greatly appreciated.

Many thanks,

Pete

---

### Post by superprash2003 on 2008-10-06
well using ifup and ifdown you can switch on and switch off as and when wanted.. and adding lines to the interfaces file as you said, is possible..

---

### Post by Iowan on 2008-10-06
Check out **man interfaces**. There's an interesting section on mapping that I don't completely understand, but it sounds something like what you want.

---

### Post by pfbroome on 2008-10-09
Greetings all,

Well, I decided to do some testing. My network does have a DHCP server so I connected both nic's to my main Ethernet switch. In the interfaces file I configured eth1 static (my DNS server knows this address as the name of the server) and eth0 as a DHCP client.  The text of the interfaces file is below:

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

#
# eth1 is the primary interface
#

auto eth1
iface eth1 inet static
        address 10.192.12.116
        netmask 255.255.255.0
        network 10.192.12.0
        broadcast 10.192.12.255
        gateway 10.192.12.113


So, I can ifup and ifdown both interfaces. The DHCP provisioned interface works just fine as does the static apparently.

My problem is this; If I ifdown the static interface (eth1) and do an ifconfig, all I see are the lo and the eth0 interfaces (as I should). If I do an ifconfig -a I see all three interfaces but the eth1 interface does NOT indicate as up/running. See the following:


peter@bfhost:/etc/network$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:04:5a:8d:db:94  
          inet addr:10.192.12.27  Bcast:10.255.255.255  Mask:255.0.0.0
          inet6 addr: fe80::204:5aff:fe8d:db94/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1113 errors:0 dropped:0 overruns:0 frame:0
          TX packets:678 errors:4 dropped:0 overruns:0 carrier:8
          collisions:0 txqueuelen:1000 
          RX bytes:109339 (106.7 KB)  TX bytes:96674 (94.4 KB)
          Interrupt:21 Base address:0xde00 

eth1      Link encap:Ethernet  HWaddr 00:19:21:4c:3d:fb  
          inet addr:10.192.12.116  Bcast:10.192.12.255  Mask:255.255.255.0
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:135609 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6825 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:15318671 (14.6 MB)  TX bytes:874979 (854.4 KB)
          Interrupt:17 Base address:0xdc00 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:54 errors:0 dropped:0 overruns:0 frame:0
          TX packets:54 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:4192 (4.0 KB)  TX bytes:4192 (4.0 KB)

However, with eth1 ifdown-ed, if I ping that static interface (the one that says it is NOT configured/enabled/up) the interface responds as normal (i.e. up) and I can ssh to it no problem.

I have tried repeatedly to ifdown the interface but when I do the server tells me it's not configured:

peter@bfhost:/etc/network$ sudo ifdown eht1
ifdown: interface eht1 not configured
peter@bfhost:/etc/network$ 


Which is right, so, how am I getting a response from an un-configured (i.e. down) interface?


I am at a loss here so ANY help will be greatly appreciated,

Many thanks,

Pete

---

### Post by superprash2003 on 2008-10-09
note the typo.. its eth1 or eht1

---

### Post by pfbroome on 2008-10-11
Greetings all,

Thanks for the typo catch (it IS eth1).

I am beginning to suspect some kind of problem with my workstation I used in this test. The Ubuntu server responds as you would expect to the ifup/down commands. The workstation is what appears to produce more random (or perhaps just delayed) results.

When I use another workstation (call it workstation B) or another Ubuntu server (call it server B), things appear to respond correctly. That is, if I ifup an interface, the workstation B and Server B ping it fine. Both interfaces up, the server B and workstation B ping fine. Down one or both of the interfaces, workstation B and server B work fine and as expected.

I will dig into my original test workstation and see if I can find a reason for this behavior. If I find anything else out I will post it here but at present I think the ifup/down interfaces are going to work fine.

Thanks everyone,

Pete

---

