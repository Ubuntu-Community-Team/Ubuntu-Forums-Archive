---
title: "Can't ping router, no outside/inet access"
date: 2007-02-11
forum: Networking &amp; Wireless
---

### Post by TANGUN on 2007-02-11
Ok, I had some issues getting Ubuntu to use my NIC. Now it sees it as 'eth0'. Good. However, I now cannot ping anything other than my own IP (127.0.0.1) My 'iftab' file is empty and I think it should contain something. Luckily this isn't a wireless problem. I'm using 6.10 server. I know I need to see my router, but it's not seeing anything else. I'm not sure of the router's IP, I'll work on finding it. Once I can ping the router, I'll of course want to ping some site to test outside access. Once that is done...there's more to do....

ifconfig
eth0 
Link encap:Ethernet HW addr 00:10:5A:C6:1B:68
inet6 addr: fe80::210:5aff:fec6:1b68/64 Scope:Link
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1 
RX packets: 0 err:0 dro:0 ovr:0 fr:0
TX packets: 47 err:0 dro:0 ovr:0 car:0
coll: 0 txqueuelen:1000
RX bytes: 0  TX bytes: 14490
IRQ: 5 Base:0x220

lo
Link endcap: Local Loopback
inet addr: 127.0.0.1  Mask: 255.0.0.0
inet6 addr: ::1/128 Scope: Host
UP LOOPBACK RUNNING  MTU:16436 Metric:1
RX packets: 32 err:0 dro:0 ovr:0 fr:0
TX packets: 32 err:0 dro:0 ovr:0 car:0
coll: 0 txqueuelen:0
RX bytes: 2440 TX bytes:2440

---

### Post by kidders on 2007-02-11
Hi there,

Your eth0 has no IP address, so it's essentially useless. At a minimum, you will need to assign it an IP in the same subnet as your router in order to access anything over it.

---

### Post by TANGUN on 2007-02-11
Once I find my router IP, what should I edit to assign that subnet to 'eth0'? Say my router is 192.168.0.10, I'll have to give my NIC the 192.168.0.X address right?

---

### Post by koenn on 2007-02-11
setup eth0 by adding something like this to /etc/network/interfaces

```
auto eth0
iface eth0 inet static
        address 192.168.0.25
        netmask 255.255.255.0
        network 192.168.0.0
        broadcast 192.168.0.255
        gateway 192.168.0.**10**

```

then restart the network card
```

ifdown
ifup

```

---

### Post by TANGUN on 2007-02-11
Hmmmm. I found the router address as 192.168.2.1   I set the 'interfaces' file to contain address: 192.168.2.25
netmask: 255.255.255.0
broadcast: 192.168.2.255
gateway: 192.168.2.X    (I've tried both 1 and 10)

Restarted networking and....still can't ping out.

---

### Post by sdide on 2007-02-11
Can you ping 192.168.2.1? 

Sounds to me like you need a default route.

```
ip route add defualt via 192.168.2.1
```

---

### Post by koenn on 2007-02-11
> gateway: 192.168.2.X (I've tried both 1 and 10)
should be 192.168.2.1, the address of the router.
don't forget to restart the nic if you changed something here

---

### Post by TANGUN on 2007-02-11
Tried both, no luck. I restarted both networking and the machine. I do get a 'Destination Host Unreachable' error, which is good (I think) as it help me track the error. I had thought that the 192.168.2.1 was set as the default. How can confirm that? I do notice that my router shows the error light on the 3rd plug (the Ubuntu PC) while the XP and 98 lights (2 and 4) are good. I can see my NIC, I can ping myself both by IP and as 'localhost'. I still can't see the router. I think I'm still having issues visualizing the relationships between the 'ifconfig' and 'default gateways' and 'interfaces' and how to really track down the error. Gee, why whould I be frustrated when I don't know what I'm doing?

[rant]I really, really, REALLY don't want to put XP on there as I'd rather have a fast server. But a slow server is better than a non-functional one. Why isn't this as easy on Ubuntu? I would have been up and running weeks ago with AnotherOS. Really, I'm trying to be a believer. Sigh.[/rant]

---

### Post by TANGUN on 2007-02-11
I'm also not sure my 'netstat -r' is showing the right info.
netstat -r
Destination       Gateway         Genmask         Flags     MSS Window  irtt    iface
192.168.2.0           *               255.255.255.0   U            0   0            0       eth0
default              192.168.2.1     0.0.0.0            UG          0   0            0        eth0

---

### Post by koenn on 2007-02-11
You have to be sure of what the default gateway address is. Check it on one of the other machines, it 's the same address. run
```
ipconfig /all
```
on the windows XP  machine in a command window (start : run : cmd.exe )

I had thought that the 192.168.2.1 was set as the default. How can confirm that? 
```
route -n
```
or the netstat you just did

> I do notice that my router shows the error light on the 3rd plug (the Ubuntu PC) while the XP and 98 lights (2 and 4) are good.
That can't be good, right ? Did you try plugging the ubuntu in to one of the ports that you are sure they work ? Or swapped cables to make sure the cable you're using is good ? etc. 

you could also ```
sudo apt-get install ethtool
```, then do ```
ethtool ethx
``` - where ethx is your ubuntu nic (eth0 ?)
it verifies the datalink -  the level below the IP addresses and gateway stuff.

---

### Post by sdide on 2007-02-11
Hey,

First you need to establish link.

for that you can use ethtool.

```
# ethtool eth0
```

it will report Link status and duplex and speed settings.
(if you do not have ethtool, you can use "ip link show eth0" instead. 
if you see  eth0: <NO-CARRIER,...> you do not have link.)

if you have link, you should be able to see your layer 2 neighbours with:

```
# ip neigh
```

which should essentially be your router (default gw)

please tell me how these commands respond.

---

### Post by TANGUN on 2007-02-11
Ran the ipconfig on XP machine: Confirmed the gateway is correct. 192.168.2.1
Both route -n and netstat -r show the same info.

I know all the ports are good. The cable was good earlier. I'll try testing it later, but I expect it to be good.

Did the apt-get and ethtool was current. 
ethtool eth0
Supported probes: [ TP ]
Supported link modes:  10baseT/Half 10baseT/Full
Supports auto-negotiation: No
Advertised link modes: Not reported
Adveritsed auto-negotiation: No
Speed: 10Mb/s
Duplex: Half
Port: Twisted pair
PYHAD:0
Tranciever: internal
Auto-negotiation: off
Current message level: 0x00000002 (2)
Link detected: yes

Thoughts?

---

### Post by TANGUN on 2007-02-11
ip neigh

Shows nothing.

ip link show eth0 gives:
2: eth0: <BROADCAST,MULTICAST,UP,10000> mtu 1500 qdisc pfifo_fast 
qlen 1000 link/ether 00:10:5a:c6:1b:68 brd ff:ff:ff:ff:ff:ff

---

### Post by koenn on 2007-02-11
I find these interseting :

> Supports auto-negotiation: No
Speed: 10Mb/s
Duplex: Half

Can you see on your router how the port is set ? Can it be set to match your card - i.e. no auto-sensing, 10 mbps, half duplex ?

---

### Post by sdide on 2007-02-11
Hey, 

you're running 10Mbit/s half duplex.
It seems your NIC can at least do 10Mbit/s Full duplex.

as root:

# ethtool -s eth0 duplex full

then try  "ip neigh" again.

---

### Post by TANGUN on 2007-02-11
Odd, I tried to set it to full duplex, but the change won't stick. Running ethtool eth0 still lists it as half duplex. Even after a full reboot. I think I may try swapping it out for a newer PCI NIC.

---

### Post by TANGUN on 2007-02-11
Ok, swapped out the ISA for PCI NIC. Now I have a D-Link DE-528. I have made the following changes:
removed the '3c509' driver from /etc/modules and added the 'ne' (Should I use the 'ne2k-pci' instead?)

Rebooted.

ifconfig now shows:
eth0
Link endcap:Ethernet	HWaddr 00:80:C8:FE:44:9E
inet addr:192.168.2.25 Bcast:192.168.2.255 Mask:255.255.255.0
inet6 addr: fe80::280:c8ff:fefe:449e/64 Scope:Link
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:0 TX bytes: 468
Interrupt: 11 Base address:0xef40

lo
Link endcap:Local loopback
inet addr:127.0.0.1 Mask:255.0.0.0
inet6 addr: ::1/128 Scope:Host
UP LOOPBACK RUNNING MTU:16436 Metric:1
RX packets:24 errors:0 dropped:0 overruns:0 frame:0
TX packets:24 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0
RX bytes:1856 TX bytes: 1856

Ok. Yet I still can't ping the router. I would also prefer that DHCP gets the correct info. So then I switched the 
'iface eth0 inet static' to 'iface  eth0 inet dhcp'
Restarted networking and got:
There is already a pid file /var/run/dhclient.eth0.pid with pid 3559
killed old process, removed PID file
(Stuff)
Listening on LPF/eth0/00:80:c8:fe:44:9e
Sending on LPF/eth0/00:80:c8:fe:44:9e
Sending on Socket/fallback
There is already a pid file /var/run/dhclient.eth0.pid with pid 134993416
(Stuff)

Listening on LPF/eth0/00:80:c8:fe:44:9e
Sending on LPF/eth0/00:80:c8:fe:44:9e
Sending on Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 21
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 14
No DHCPOFFERS received.
No working leases in persistant database - sleeping. [ ok ]

Hmmmm. Rerunning 'ifconfig' gives exact same info as above EXCEPT there is no inet-broadcast-gateway line in the report.

Trying a 'netstat -r' gives nothing. Trying to reboot.

---

### Post by TANGUN on 2007-02-11
Now 'ifconfig' doesn't show 'eth0' 
Did I use the wrong driver? I'm changing to the 'ne2k-pci'. Hope it helps.
I'm sure that if I try the various utils, I won't see anything as eth0 is gone. (Yup, eth0 not recognized)

---

### Post by TANGUN on 2007-02-11
Ok, so I switched to the 'ne2k-pci' driver. I can see 'eth0' again.
The /etc/network/interfaces is set to:
...
iface eth0 inet dhcp

as I want the server to get the settings from the router as it changes from the ISP.

Running lspci gives:
Ethernet controller: Realtek Semiconductor Co RTL-8029(AS)

ifconfig
eth0
Link endcap:Ethernet	HWaddr 00:80:C8:FE:44:9E
inet addr:192.168.2.25 Bcast:192.168.2.255 Mask:255.255.255.0
inet6 addr: fe80::280:c8ff:fefe:449e/64 Scope:Link
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:0 TX bytes: 468
Interrupt: 11 Base address:0xef40

lo
Link endcap:Local loopback
inet addr:127.0.0.1 Mask:255.0.0.0
inet6 addr: ::1/128 Scope:Host
UP LOOPBACK RUNNING MTU:16436 Metric:1
RX packets:24 errors:0 dropped:0 overruns:0 frame:0
TX packets:24 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0
RX bytes:1856 TX bytes: 1856

Good. Running 'ethtool eth0' gives:
Settings for eth0:
No data available

Uh oh. What about 'netstat -r'?

The table is blank. Crappy. Uhhhh how about...

dmesg | tail
FDC 0 is a National Semiconductor PC87306
lp0: using parport0 (interrupt driven)
Adding 843372k swap on dev/disk/by-uuid/77b51773-aad5-4f41-9022-b5af9bda97c1. 
Priority:-1 extents:1 across: 843372k
EXT3 FS on hda1, internal journal
NET: Registered protocol family 17
NET: Registered protocol family 10
lo: disabled privacy extentions
IPv6 overIPv4 tunneling driver
eth0: no IPv6 routers present

Sadly I don't know how to interpret that.

I can still ping myself by IP and as localhost. But still no router or internet. Help?

---

### Post by Vortec62 on 2007-02-11
I'm having nearly identical issues....

I've been running ethtool, ip, ifconfig etc and getting the same results as TANGUN except my NIC is at full duplex.

I have it set for DHCP and when I run 'ifup -a -v' I can see DHCPDISCOVER not getting a reply.  I have a linksys router and I can look at my local network in the status menu and see it giving out a 1 minute lease to the hardware address on my ubuntu box everytime there is a DHCP request.

I also tried setting it up as static but that doesn't seem to work either.  

The NIC seems to be able to send but it is not recieving...

I'm using the NIC that is onboard an EPIA-sp13000 itx board if that makes a difference.

---

### Post by TANGUN on 2007-02-12
Similarly, I don't get a DHCP reply. However, it's not getting to the router even. I see nothing in the log on the router and the router is up to date. There is nothing blocking any IP addresses there either. Maybe I have a driver issue? Is the 'de2k-pci' the correct driver for the card? Based on the fact that DHCP seems to not be answering, I'm beginning to think of DHCP problems. I'd still like to try other things before trying to fiddle with DHCP. Can anyone troubleshoot DHCP issues on both the client and server ends?

---

### Post by sdide on 2007-02-12
Hey, 

TANGUN : 

Just to write up what we are trying to do here: 

a: Establish link to your local router 192.168.2.1. To test we do "ip neigh".
a2: Test if the router responds to DHCP requests.
b: Make sure  your default route is directed towards 192.168.2.1
c: Make sure you use DNS to resolve names. 

1:)
Please do 
```
# ethtool eth0 
```
again and post output. 

2) 
```
# ip neigh
```
output ? 

If negative: 3a:) we need to establish a proper link to your router. What router is it?

if positive: 3b):

Try 

```
# dhclient eth0
```

if that goes well: you'll get something like :

```
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
DHCPOFFER from 192.168.2.1
DHCPREQUEST on eth0 to 255.255.255.255 port 67
DHCPACK from 192.168.2.1
bound to 192.168.2.25 -- renewal in 13696 seconds.

```
if it goes bad you should recieve something like:

```
DHCPREQUEST on eth1 to 255.255.255.255 port 67
DHCPREQUEST on eth1 to 255.255.255.255 port 67
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 17
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 9
No DHCPOFFERS received.
```

If you get no DHCP offers, we need to set  ip-address, set default route, get DNS manually.

Tell what you get.

---

### Post by koenn on 2007-02-12
> Can anyone troubleshoot DHCP issues on both the client and server ends?
client-side, there's nothing to configure; that's what dhcp is for.
server-side - I could have a look at your dgcpd config file if you post it.

However, i don't think it's really a dhcp problem (yet). The reason that you don't receive dhcpoffers is that the dhcp server (running on your router) can't reach the colmputer - as the computer can also not reach the router (your pings fail). 

So my guess is you should be able to get this going with a manual (static) configuration, and worry about dhcp later. 
```

auto eth0
iface eth0 inet static
        address 192.168.2.25
        netmask 255.255.255.0
        network 192.168.2.0
        broadcast 192.168.2.255
        gateway 192.168.2.1
```

question : who decided to use 192.168.**2**.0 for network, and why ?

you have to be sure 192.168.2.25 is not being used by an other computer. 
If you can ping 192.168.2.25 from the computer itself, you're quite sure it's setup correctly and you can focus on the router - Is there a way you can get basic info about it (eg in a web interface on an other computer that is able to connect to the router ?)

---

### Post by TANGUN on 2007-02-12
Let's get the basics out of the way.
The cable is good. The card is good. Both confirmed by another computer.

Is this the correct driver?
In the'modules' file I have:
lp
ne2k-pci

In 'Interfaces' I have:
auto lo
iface lo inet loopback
auto eth0
iface eth0 inet dhcp

lspci shows:
Ethernet controller: Realtek Semiconductor Co RTL-8029(AS)

Ok, on to the good stuff.
ethtool eth0 returns:
Settings for eth0:
No data available

Interesting.
ip neigh returns...nothing. This makes me suspect that ethtool and eth0 aren't communicating correctly. Driver?

The router is a Belkin F5D6231-4, it has wireless, but I'm only using wired at this point. I can access the router directly on the other two computers, neither of which have an IP conflict. What info would you like? The settings I've tried have been confirmed by the two other PCs and the router itself. Who decided on 192.168.2.X? I dunno. Capt. Crunch? I do note that the router knows a cable is in the port where the Ubuntu box is, and the NIC knows the cable is there as well. Both the router and card have a light on. On the router the color is wrong, orange = good connection, green = uhhhh not...good connection?

Ok, so lets switch to 'static'
In the'modules' file I have:
lp
ne2k-pci

In 'Interfaces' I have:
auto lo
iface lo inet loopback
auto eth0
iface eth0 inet static
address 192.168.2.25
netmask 255.255.255.0
network 192.168.2.0    *never had this before
broadcast 192.168.2.0
gateway 192.168.2.1

A full reboot and....

ethtool eth0 shows
Settings for eth0:
No data available

ip neigh returns nothing still.

A test of 'dhclient' returns the obvious 'NO OFFER'

I just can't buy that all three NICs I've tried are bad. (Side note: Seems my CD drive isn't able to boot. Otherwise I'd try a clean install)

Thoughts? I'm leaning (obviously) toward a driver or DHCP problem. Whether the problem is with the settings I've chosen, or are inherent to Ubuntu...I don't have the experience to say. However, based on the number of 'I have networking issues' threads on this site... I can't rule out that the problem is with Ubuntu. Static settings don't work. DHCP doesn't work. What now?

---

### Post by TANGUN on 2007-02-12
I read something about Belkin routers being Windows devices and requiring 'ndiswrapper-utils' Thoughts?
Also, elsewhere, I read that 'some routers' (including unnamed Belkins) don't like giving out DHCP/DNS to certain kernels (either Linux or Win). The 'easy' fix is just to swap routers. Sure, let me crap out $100 for a new one. GMAB.

---

### Post by sdide on 2007-02-13
Hey, 

Seems strange that you do not get any result from ethtool eth0. (You got a result earlier ?)

The Realtek 8029AS is an oldtimer. I'm not sure if its supported. Its a 10Mbit/s NIC... you should be able to get a 100MBit/s  for almost free.

---

### Post by TANGUN on 2007-02-13
Well, these cards were free. The only others I had were ISA while this is a PCI. I wouldn't be surprised if a newer NIC would help. It just seems that many people here are trying to run this off of spare parts from older PCs. I need a couple of fans for a video card and processor (the fans are dying and buzzing loudly at times) so maybe I'll try to get a newer NIC too.

---

### Post by koenn on 2007-02-13
OK, i'm beginning t lean towards "driver problem" nowl. 

[http://directory.fsf.org/all/ethtool.html](http://directory.fsf.org/all/ethtool.html)  :
> Ethtool is a GNU/Linux net driver diagnostic and tuning tool for the Linux 2.4.x (or later) series of kernels. It obtains information and diagnostics related to media, link status, driver version, PCI (or other) bus location, and more. 
I guess that it ethtool doesn't return anything because the driver is not able to talk to the nic - especially when it's confirmed that cables etc are OK

Don't worry about the dhcp - we've ruled that out by setting a static nic config - and dhcp would not work by lack of network connection (not the other way around). 

> I read something about *_Belkin routers _*being Windows devices and requiring 'ndiswrapper-utils' Thoughts? Sounds bizarre. routers process ip packets based on source ip address and destination ip address. They have no way of knowing whether the packet comes from a Windows or a Ubuntu machine, a Cisco router, a Debian web server, or whatever - and if they did know, they wouldn't care : IP is a standard, platform-independent protocol. (ndis wrapper is - to my knowledge - a technique to use Windows 'ndis' drivers for **network cards** on linux systems - nothing to do with routers)

So it may be a driver issue after all. unfortunately, i don't have any experience with those - I usually do network installs so the network card gets a driver and is configured even before the OS is fully installed - and I've never had to change anything afterwards.

So, reviewing the NIC's
ISA nic using 3c509 driver. Was it a real 3C509 or another 3com that uses the same driver ? I've used 3C509 ISA myself - they have 2 modes : PnP or not - I've you're interested, I took some notes at the time i used 2 or 3 of those in the same machine and needed a way to identify them using IRQ and I/O addresses : [http://users.pandora.be/mydotcom/howto/lanconnect/router/linux.htm](http://users.pandora.be/mydotcom/howto/lanconnect/router/linux.htm)


D-Link DE-528 (PCI). driver should be 'ne' or  ne2k-pci'  - probably the latter
Realtek Semiconductor Co RTL-8029 : also 'ne' or  ne2k-pci' 

I don't see what could be wrong here, except maybe that the driver isn't loaded correctly ? Wild guess : maybe remove any referennces to it (in /etc/modules), reboot, and see if the nic gets autodetected + driver loaded ?

---

### Post by TANGUN on 2007-02-14
Well, after buying a new NIC (DFE-530TX+ with driver '8039too') and running through the motions...sadly I'm now either leaning toward:
1.) The router.
For whatever reason it's not 'returning the call' I can see the lights blink when DHCPDISCOVER runs. I see that the router and NIC detect a connection. Neither a static or dhcp configuration works. I still can't ping the router. I don't know why Linux vs Windows would make a difference...but I bet if I throw XP on there I'll be online in no time.

2.) Ubuntu 6.10 server.
I'm guessing this is kinda the (current) flagship OS for Ubuntu users. I certainly didn't leap in light with no Linux experience...but you have to try if you want to switch. I'll try to reinstall...but the CD drive is no longer working after installing Ubuntu. Where exactly the blame is...I don't know. It's just easy to blame Ubuntu when things don't work. 

I could post the readouts of whatever program you want me to run. I can alter whatever setting is needed. Sadly I guess there just isn't the broad range support for hardware in Ubuntu yet. Once this hurdle is overcome maybe I'll try again. I hope by Ubuntu Zippy Zebra the kinks are worked out.

---

### Post by sdide on 2007-02-14
"Don't give up
	'Cause you have friends
	Don't give up
	You're not beaten yet
	Don't give up
	I know you can make it good"

I hate to quote Kate Bush, but I had to! Don't give up!

We can still make this work ... I mean 

What does 

# ethtool eth0 

give with your new NIC?

---

### Post by TANGUN on 2007-02-14
I haven't given up yet. But it is frustrating. I'm at 'work' but here's what I remember from ethtool
Supported probes: [ TP MII ]
Supported link modes: 100baseT/Half 100baseT/Full
Supports auto-negotiation: Yes
Advertised link modes: 100baseT/Half 100baseT/Full
Adveritsed auto-negotiation: Yes (Pretty sure but don't remember)
Speed: 100Mb/s
Duplex: Full (Pretty sure)
Port: Twisted pair
PYHAD:0
Tranciever: internal
Auto-negotiation: On
Current message level: 0x00000001 (1)
Link detected: yes

I think that's about 99% correct. Not sure about those two items though. I'll check when I get home. I do notice that the light on the router is now the correct color. It was green (bad) now it's amber (like the others that have access, good). I know that for the old card I think it was supposed to be in Half duplex mode. Now it's Full duplex. I hadn't thought to try changing it. Hopefully I don't need to and I'm just overlooking something. I'm fairly certain that Ubuntu is sending packets, I know the router is getting them, both LEDs on each side flash during 'dhclient'. But I don't know if the router is sending anything back to Ubuntu. Is there any way to get a better readout (verbose mode for 'dhclient'?) of both the Ubuntu side and anything the router may be sending? Can I use another PC to check what the router is sending during a DHCP update? Can I use another computer to see what dhclient is sending? Can I route all packets, text, etc to a file and read it? I know that there would be no dhcp response but I'd like to see the output I guess.

---

### Post by koenn on 2007-02-14
> But I don't know if the router is sending anything back to Ubuntu. Is there any way to get a better readout (verbose mode for 'dhclient'?) of both the Ubuntu side and anything the router may be sending? Can I use another PC to check what the router is sending during a DHCP update? Can I use another computer to see what dhclient is sending? Can I route all packets, text, etc to a file and read it? I
ethereal, aka wireshark (i think you can get it from universe)

you could run it on the ubuntu and see what it sends and what it receives, if anything.

There's a version for Windows as well. you could run that  while the ubuntu tries to get dhcp from the router - dhcp are boadcasts so you might capture them. If nut, it would be best to get hold of a hub - hubs repeat packets to all their ports so you could see the entire conversation between any two hosts connected to that hub - in this case your router and the ubuntu pc.

---

### Post by sdide on 2007-02-14
Hey,

I'd use tcpdump

open one terminal and do 

# tcpdump -nli eth0

open another and do 

# dhclient eth0

should be interesting.

---

### Post by Vortec62 on 2007-02-14
I got mine working...sort of.  I gave up on the ethernet and started in on ndiswrapper and my wireless card.  When I did ifup ra0 the ethernet port started working.  If I ifdown ra0 the ethernet port will stop working again.  I've been suspecting some sort of IRQ problem. lspci -vv tells me that my onboard ethernet and wireless PCI card are on interrupt pin A routed to IRQ 11.  lspci -vv -b says the onboard ethernet is interrupt pin A routed to IRQ 15 and the wireless card is still pin A IRQ 11 (the onboard video is pin A IRQ 15 with or w/o the -b arrgument on lspci)

This uncharted territory for me but I thought it might help someone else out...or maybe someone can tell me what to do to get the two cards to play nice together.

---

### Post by TANGUN on 2007-02-14
It was quite interesting. Thanks for showing me that tool. 

The ethtool eth0 shows:
Supported probes: [ TP MII ]
Supported link modes:  100baseT/Half 100baseT/Full
Supports auto-negotiation: Yes
Advertised link modes: 100baseT/Half 100baseT/Full
Adveritsed auto-negotiation: Yes
Speed: 100Mb/s
Duplex: Full
Port: MII
PYHAD:1
Tranciever: internal
Auto-negotiation: on
Current message level: 0x00000001 (1)
Link detected: yes

That's the correct data.

The tcpdump showed this:
tcpdump: verbose output suppressed, use -v or -vv for full protocol decode listening on eth0, link-type EN10MB (Ethernet), capture size 96 bytes
17:53:02.186767 IP 0.0.0.0.68 > 255.255.255.255.67: BOOTP/DHCP, Request from 00:19:5b:30:fc:28, length 300
17:53:07.013192 IP 0.0.0.0.68 > 255.255.255.255.67: BOOTP/DHCP, Request from 00:19:5b:30:fc:28, length 300
xxxxxxxxxxxxxx IP 0.0.0.0.68 > 255.255.255.255.67: BOOTP/DHCP, Request from 00:19:5b:30:fc:28, length 300
xxxxxxxxxxxxxx IP 0.0.0.0.68 > 255.255.255.255.67: BOOTP/DHCP, Request from 00:19:5b:30:fc:28, length 300
xxxxxxxxxxxxxx IP 0.0.0.0.68 > 255.255.255.255.67: BOOTP/DHCP, Request from 00:19:5b:30:fc:28, length 300
xxxxxxxxxxxxxx IP 0.0.0.0.68 > 255.255.255.255.67: BOOTP/DHCP, Request from 00:19:5b:30:fc:28, length 300

6 packets captured
12 packets received by filter
0 packets dropped by kernel

That's interesting. Where did the packets go? Does this mean that the router IS sending data to the PC? If so, then the router is fine and there's a software issue. One more piece of the puzzle...now, what does it mean?

---

### Post by TANGUN on 2007-02-14
I tried 'ifup 8139too' but got:
Ignoring unknown interface 8139too=8139too.

Wierd.

---

### Post by TANGUN on 2007-02-15
> **TANGUN said:**
> Does this mean that the router IS sending data to the PC? If so, then the router is fine and there's a software issue....now, what does it mean?

First and foremost: Thanks to all of you who tried to help.

I'm 100% sure that Ubuntu IS THE PROBLEM. I'm guessing that the problem lies in how DHCP requests are handled. Something at a *fundamental* level is wrong with Ubuntu. It still, regardless of what you change or if you reinstall the OS, will not receive the DHCP packets from the router and access the internet. 

After spending the last 3 weeks working on this one problem I have to say I'm disappointed that something as stable as Linux is failing. Here's hoping that the final try tomorrow works out. Otherwise...different distro or to XP I go.

---

### Post by koenn on 2007-02-15
I think you're exagetaring somewhat. Not getting things to work right is frustrating, but
> Something at a fundamental level is wrong with Ubuntu
seriously ... At this very moment I have 6 ubuntu systems running - 1 gets dhcp from a dhcp daemon on a Debian sustem, 4 get dhcp from a Windows 2000 dhcp server, and 1 gets its dhcp from an adsl router. All of that worked from the initial install - before that, actually, dhcp configured the network during the setup so the installer could get updates from the repo's. 

now, looking at your tcpdump

dhcp uses port 67/udp for the server side, and 68/udp for the client side.
```
0.0.0.0.68 > 255.255.255.255.67: BOOTP/DHCP, Request from 00:19:5b:30:fc:28, length 300
```
what you're seeing here are broadcasts from your computer - same as
```
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 21
``` that you had before. 

Your nic seems to be working at least - but either
- the router is not giving out replies to the dhcpdiscover
- your computer doesn't receive the dhcpoffer
- your computer doesn't process the dhcpoffers it receives

I'd say 1 and 2 are more likely. 

to see replies from the router - if any - you'd have to run tcpdump (or ethereal or a similar packet sniffer) *between* the router and the ubuntu compuiter - eg by using a hub. It *might* also work from an other computer plugged into the router, but that's rather unlikely. 

you could post your /etc/dhcp3/dhclient.conf
 to see if something in there keeps the router from processing the resuests

Also, you could try to get the dhcpserver config from your router, to see which dhcp leases it has given out, or anything else that might indicate a reason not to reply to the resuests it receives.

Still, there may be something else going on here, as a static configuration also doesn't seem to work. 
btw, 
>  I tried 'ifup 8139too' but got:
Ignoring unknown interface 8139too=8139too. - this is never going to work. do
```
ifup eth0
```

---

### Post by TANGUN on 2007-02-15
> **koenn said:**
> I think you're exagetaring somewhat. Not getting things to work right is frustrating, but

seriously ... At this very moment I have 6 ubuntu systems running - 1 gets dhcp from a dhcp daemon on a Debian sustem, 4 get dhcp from a Windows 2000 dhcp server, and 1 gets its dhcp from an adsl router. All of that worked from the initial install - before that, actually, dhcp configured the network during the setup so the installer could get updates from the repo's. 

I don't need 6, I just need one to work. Wish mine was that easy. I reinstalled 6.10 and since it picked up the network card (but not the network), it messed up all the settings.


> **koenn said:**
> 
Your nic seems to be working at least - but either
- the router is not giving out replies to the dhcpdiscover
- your computer doesn't receive the dhcpoffer
- your computer doesn't process the dhcpoffers it receives

I'd say 1 and 2 are more likely. 


I'm banking more on 2 and 3. So, let's start at 2. How can I confirm that the router IS sending a DHCP packet? 

> **koenn said:**
> 
you could post your /etc/dhcp3/dhclient.conf
 to see if something in there keeps the router from processing the resuests

The file says
send host-name "192.168.2.1";

> **koenn said:**
> 
Also, you could try to get the dhcpserver config from your router, to see which dhcp leases it has given out, or anything else that might indicate a reason not to reply to the requests it receives.

I've poked around the router's page but don't see much info.

> **koenn said:**
> 
Still, there may be something else going on here, as a static configuration also doesn't seem to work. 

btw, 
 - this is never going to work.
I just need to find someone with the same router using 6.10. That would show whether the router is just incompatible or not. I know it won't work but at this point I'll try just about anything. I'm more curious as to why it's not working.

---

### Post by sdide on 2007-02-16
in /etc/dhcp3/dhclient.conf

i have :

request subnet-mask, broadcast-address, time-offset, routers,
        domain-name, domain-name-servers, host-name,
        netbios-name-servers, netbios-scope;

or you could just do a 

request;

The 
send host-name "192.168.2.1";
puzzles me.

From "man dhclient.conf"
 
The send statement

        send { [ option declaration ] [, ... option declaration ]}

       The  send  statement  causes the client to send the specified options to the server with the specified values....

and then from  "man dhcp-option" 

option host-name string;

          This option specifies the name of the client. 

 To me it seems, you're trying to send to the dhcp-server, that your host-name is 192.168.2.1..

You need to do a "request;" instead.

---

### Post by koenn on 2007-02-16
re /etc.dhcp3/dhclient.conf
mine is 

```
request subnet-mask, broadcast-address, time-offset, routers,
        domain-name, domain-name-servers, host-name,
        netbios-name-servers, netbios-scope;

send host-name "nix";
```

I would definitely comment out the '  send host-name "192.168.2.1"; ' or replace it with the hostname of the ubuntu-pc. Having the router's ip address there is just wrong.

If you have anything different from the above, it would be wise to replace the dhclient.conf (at least temporarily) : to give 1 exemple : if you use the 'require' statement, and the router is not able to provide the required option, the dhcp dialogue will fail completely. 


> I know it won't work 
I meant that your "ifup 8139too" statement will never work, because ifup expects an interface name (like eth0), and doesn't work with driver / package names (such as 8139too)


> So, let's start at 2. How can I confirm that the router IS sending a DHCP packet? 
As I explained before : to see replies from the router - if any - you'd have to run tcpdump (or ethereal or a similar packet sniffer) between the router and the ubuntu computer - eg by using a hub : connect the router, the ubuntu problem pc, and a 3rd pc running ethereal (or similar program) to a hub. Then run ethereal, while it runs, boot the ubuntu problem pc. 

hub : [http://en.wikipedia.org/wiki/Ethernet_hub](http://en.wikipedia.org/wiki/Ethernet_hub)  (read the section "usefulness" - the first paragraph describes what you're trying to do)

What you can expect is something as shown in figure 2 (page 4) of this paper : [http://gaia.cs.umass.edu/ethereal-labs/labs/Ethereal_DHCP.pdf](http://gaia.cs.umass.edu/ethereal-labs/labs/Ethereal_DHCP.pdf)

---

### Post by TANGUN on 2007-02-17
Well, no luck. Ubuntu seems really nice but if it won't work with my hardware I can't use it. The router is sending DHCP info to the other PCs and I can't see any reason why it wouldn't be sending the info to the Ubuntu box. There's nothing on the router itself that limits who would get an IP address from it. I think that either the driver I have isn't allowing Ubuntu to process what it gets or Ubuntu can't process what the router is sending.

---

### Post by TANGUN on 2007-02-17
Ok, I decided to try the 7.04 release. I was hoping that whatever the issue is would be fixed but it wasn't. It's not a server either but at least I can play Nibbles. It doesn't detect the correct refresh rate and I have to change it every time I restart. And still...no networking. :( I'll repost every single command I've run (later) to show how things are setup now. I'm hoping that maybe someone will notice something odd and everything will click into place.

---

### Post by TANGUN on 2007-02-24
HOLY SHAZBOT!!!

I'm now typing this on a full fledged Ubuntu 7.04 computer. This feels like a real accomplishment. All I did to finally get it to work was

Edit out crap in /etc/network/interfaces:

There were a bunch of interfaces listed in there. I deleted everything except the loopback (lo) and eth0 which I left at dhcp.

Then I restarted the computer.

That didn't work so I set the eth0 line in /etc/interfaces to static and gave it the appropriate information for my network. Then I restarted the computer.

That didn't work so I reset eth0 to dhcp and....yeah, restarted.

Magically I could pull up Google, CNN, and all the good stuff I wanted. Then I came here to let everyone know that somehow, the combination of upgrading to 7.04 and fiddling with the files and a series of restarts worked. I'll be waiting for the full release server edition.

---

### Post by koenn on 2007-02-25
:)

---

