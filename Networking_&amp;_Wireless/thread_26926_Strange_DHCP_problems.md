---
title: "Strange DHCP problems"
date: 2005-04-14
forum: Networking &amp; Wireless
---

### Post by jlbrt on 2005-04-14
My friend is having an inconsistent network behavior on an old Celeron machine running Ubuntu Hoary. At my house the Celeron's network connection is working fine, but at my friend's house the machine doesn't receive an IP address. I checked this with ifconfig. Both of us are using DHCP, but my friend has a direct LAN connection and I have a cable modem. Knoppix 3.8.1 didn't work either. I've singled out any hardware problems. I've used the same ethernet cable and even tried changing the network card. The network at my friend's house should be fine, because I can surf the net on my PowerBook running Mac OS X.

Any ideas how can I fix this problem?

---

### Post by ubuntu_demon on 2005-04-14
more details please

---

### Post by jlbrt on 2005-04-14
I gave as many details I could. I'd be happy if you could tell me what kind of diagnosis should I run. I'll post the results once I get back to my friend's house.

---

### Post by ubuntu_demon on 2005-04-14
[QUOTE=jlbrt]I gave as many details I could. I'd be happy if you could tell me what kind of diagnosis should I run. I'll post the results once I get back to my friend's house.[/QUOTE]

check these threads:

[http://www.ubuntuforums.org/showthread.php?t=26515](http://www.ubuntuforums.org/showthread.php?t=26515)

[http://www.ubuntuforums.org/showthread.php?t=22263](http://www.ubuntuforums.org/showthread.php?t=22263)

If these threads don't solve your situation :

 so at your place you plug your celeron machine directly at your cable modem ? The cable modem has gives your pc an ip when you are at home.

And at your friends place you plug it in at the network ? And do you get an ip ? check with ifconfig if you get an ip but can't browse the internet you should specify the dns servers your friend uses in your /etc/network/resolv.conf (also make sure the workgroup is right in this file)

If you can't get an IP at all you should post your /etc/network/interfaces and ifconfig and route and mii-tool

To see the type of connection your network card has do this :

$ sudo mii-tool

sudo man mii-tool for more about this. you should be able to set the connection type yourself with this tool. try 10mbit halfduplex and try if this solves your problems.

---

### Post by jlbrt on 2005-04-14
[QUOTE=demon666_nl]check these threads:
[http://www.ubuntuforums.org/showthread.php?t=26515](http://www.ubuntuforums.org/showthread.php?t=26515)
[http://www.ubuntuforums.org/showthread.php?t=22263](http://www.ubuntuforums.org/showthread.php?t=22263)
If these threads don't solve your situation :
[/QUOTE]Thanks, I already checked those. My problem isn't exactly similar. Those guys did get an IP address.

> 
so at your place you plug your celeron machine directly at your cable modem ? The cable modem has gives your pc an ip when you are at home. And at your friends place you plug it in at the network ? And do you get an ip ? check with ifconfig if you get an ip but can't browse the internet you should specify the dns servers your friend uses in your /etc/network/resolv.conf (also make sure the workgroup is right in this file)
As I said before: at my place the network is working fine on the Celeron machine. E.g. I get an IP address from the cable modem, I can surf the net, etc.

At my friend's place the Celeron machine doesn't get an IP address. Actually it found no DNS servers either. It appeared to get no kind of connection from the outside, although the machine tried to do a lot of sniffing when I ran "dhclient eth0".

> 
If you can't get an IP at all you should post your /etc/network/interfaces and ifconfig and route and mii-tool
It'll be at least a couple of days until I get to visit my friend again. But thanks a lot for your support so far. I'll get back to you when I get more details.

---

### Post by ubuntu_demon on 2005-04-14
okay 
be sure to try out the suggestions from the other threads too.
good luck!

---

### Post by jlbrt on 2005-04-16
Today I visited my friend's house. After a couple of hours of tweaking I still couldn't get the Celeron machine's network to work. I tried many possible solutions I found from these forums. Here's some details from what I did, after I found out that the links you provided didn't help me:

First I ran mii-tool as you suggested and got a discouraging response:
```
$ sudo mii-tool
eth0: no link

```
So I moved on and set the connection type as you suggested:
```
$ sudo mii-tool -A 10baseT-HD eth0

```
Then I checked that the connection type had actually changed:
```
$ sudo ethtool eth0
Settings for eth0:
	Supported ports: [ TP MII ]
	Supported link modes:   10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	Supports auto-negotiation: Yes
	Advertised link modes:  10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	Advertised auto-negotiation: Yes
	Speed: 10Mb/s
	Duplex: Half
	Port: MII
	PHYAD: 32
	Transceiver: internal
	Auto-negotiation: on
	Supports Wake-on: pumbg
	Wake-on: d
	Current message level: 0x00000007 (7)
	Link detected: no

```
The connection type had changed, so I ran:
```
$ sudo dhclient eth0
Internet Systems Consortium DHCP Client V3.0.1
Copyright 2004 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/products/DHCP

sit0: unknown hardware address type 776
sit0: unknown hardware address type 776
Listening on LPF/eth0/00:05:1c:xx:xx:xx
Sending on   LPF/eth0/00:05:1c:xx:xx:xx
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 18
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 12
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

```
The dhclient found nothing so I ran ifconfig to see if I was still standing where I started:
```
$ sudo ifconfig
eth0      Link encap:Ethernet  HWaddr 00:05:1C:04:79:32  
          inet6 addr: fe80::205:1cff:fe04:7932/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:10 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:2088 (2.0 KiB)
          Interrupt:11 Base address:0x1000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:890 errors:0 dropped:0 overruns:0 frame:0
          TX packets:890 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:79810 (77.9 KiB)  TX bytes:79810 (77.9 KiB)

```
Obviously eth0 had no IP address and I had made no progress. Here are the rest of the details I gathered:
```
$ cat /etc/network/interfaces
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
	script grep
	map eth0

# The primary network interface
iface eth0 inet dhcp

auto eth0

```
/etc/network/interfaces looked normal to me, but the route command's output wasn't very encouraging:
```
$ sudo route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface

```
When I had made these diagnoses I tried using dhcpcd and pump instead of dhclient, but they weren't of any help. After many fruitless attempts I'm inclined to think that the problem is in the kernel. What baffled me was that at my friend's house the network wasn't even working in Knoppix. Hoary and Knoppix 3.8.1 both use the 2.6 series of kernels. Maybe I should try the 2.4 series or some completely different non-Debian based distribution. It would be very sad to give up Ubuntu, but in my three years with Linux I've never had a problem as nasty as this one. It doesn't help either that I can't just work this out at my own house.

Thanks for reading this far. Any help is very much appreciated.

---

### Post by jlbrt on 2005-04-16
Today I visited my friend's house. After a couple of hours of tweaking I still couldn't get the Celeron machine's network to work. I tried many possible solutions I found from these forums. Here are some details of what I did after I found out that the links you provided didn't help me:

First I ran mii-tool as you suggested and got a discouraging response:
```
$ sudo mii-tool
eth0: no link

```
So I moved on and set the connection type as you suggested:
```
$ sudo mii-tool -A 10baseT-HD eth0

```
Then I checked that the connection type had actually changed:
```
$ sudo ethtool eth0
Settings for eth0:
	Supported ports: [ TP MII ]
	Supported link modes:   10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	Supports auto-negotiation: Yes
	Advertised link modes:  10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	Advertised auto-negotiation: Yes
	Speed: 10Mb/s
	Duplex: Half
	Port: MII
	PHYAD: 32
	Transceiver: internal
	Auto-negotiation: on
	Supports Wake-on: pumbg
	Wake-on: d
	Current message level: 0x00000007 (7)
	Link detected: no

```
The connection type had changed, so I ran dhclient:
```
$ sudo dhclient eth0
Internet Systems Consortium DHCP Client V3.0.1
Copyright 2004 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/products/DHCP

sit0: unknown hardware address type 776
sit0: unknown hardware address type 776
Listening on LPF/eth0/01:23:45:67:89:10
Sending on   LPF/eth0/01:23:45:67:89:10
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 18
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 12
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

```
The dhclient found nothing so I ran ifconfig to see if I was still standing where I started:
```
$ sudo ifconfig
eth0      Link encap:Ethernet  HWaddr 01:23:45:67:89:10  
          inet6 addr: 1234::567:8910:1112:1314/15 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:10 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:2088 (2.0 KiB)
          Interrupt:11 Base address:0x1000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:890 errors:0 dropped:0 overruns:0 frame:0
          TX packets:890 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:79810 (77.9 KiB)  TX bytes:79810 (77.9 KiB)

```
Obviously eth0 had no IP address and I had made no progress. Here are the rest of the details I gathered:
```
$ cat /etc/network/interfaces
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
	script grep
	map eth0

# The primary network interface
iface eth0 inet dhcp

auto eth0

```
/etc/network/interfaces looked normal to me, but the route command's output wasn't very encouraging:
```
$ sudo route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface

```
When I had made these diagnoses I tried using dhcpcd and pump instead of dhclient, but they weren't of any help. After many fruitless attempts I'm inclined to think that the problem is in the kernel. What baffled me was that at my friend's house the network wasn't even working in Knoppix. Hoary and Knoppix 3.8.1 both use the 2.6 series of kernels. Maybe I should try the 2.4 series or some completely different non-Debian based distribution. It would be very sad to give up Ubuntu, but in my three years with Linux I've never had a problem as nasty as this one. It doesn't help either that I can't just work this out at my own house.

Thanks for reading this far. Any help is very much appreciated.

---

### Post by ubuntu_demon on 2005-04-16
You should try to swap cables and network cards

---

### Post by jlbrt on 2005-04-17
I've changed the network card once. Both cards worked at my place. So it's unlikely that the problem is in the network card. The cable worked in my PowerBook and it worked at my place in the Celeron machine. So I doubt that the problem is in the cable. But I'll try another one. It's going to be one of my desperate last resort measures.

Thanks.

---

### Post by ubuntu_demon on 2005-04-17
[QUOTE=jlbrt]I've changed the network card once. Both cards worked at my place. So it's unlikely that the problem is in the network card. The cable worked in my PowerBook and it worked at my place in the Celeron machine. So I doubt that the problem is in the cable. But I'll try another one. It's going to be one of my desperate last resort measures.

Thanks.[/QUOTE]
 from this part I guess it's a laptop with a pcmcia network card ?

```

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
	script grep
	map eth0

```

---

### Post by jlbrt on 2005-04-18
[QUOTE=demon666_nl]from this part I guess it's a laptop with a pcmcia network card ?[/QUOTE]
It's not a laptop. Which raises some questions: Could those lines cause the problem? Why would they work in one place but not in another? Why does ubuntu install those lines by default? I've installed Ubuntu on two other desktop machines (non-pcmcia) and both got those lines too.

Well, another thing to check out. Thanks.

---

### Post by ubuntu_demon on 2005-04-18
[QUOTE=jlbrt]It's not a laptop. Which raises some questions: Could those lines cause the problem? Why would they work in one place but not in another? Why does ubuntu install those lines by default? I've installed Ubuntu on two other desktop machines (non-pcmcia) and both got those lines too.

Well, another thing to check out. Thanks.[/QUOTE]
 I don't have those lines but I edited my /etc/network/interfaces myself a long time ago. Try to remove them.

I'm afraid this is as far as my networking knowledge goes. Let's hope there's somebody else who can help you if this doesn't work.

---

### Post by awaldram on 2005-04-18
it maybe your dhcp provider expects you to supply a hostname (ala windows) with the request

therfore try adding
'send host-name "mymachine.domain";

to your /etc/dhcp/dhclient.conf

I assume from you text you pick up your ip address from your provider so maybe you could tell us who the two providers are.?

If not give some description as to what the dhcp servers are

---

