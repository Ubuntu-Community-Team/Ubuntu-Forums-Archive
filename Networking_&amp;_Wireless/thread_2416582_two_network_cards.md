---
title: "two network cards"
date: 2019-04-11
forum: Networking &amp; Wireless
---

### Post by novio8 on 2019-04-11
I'v just installed my first Linux machine on a Win machine with two
network cards
One is working fine IP 198.162.0.6. For Octoprint I connected Webcam to the second network card and I gave it IP 192.168.0.103. Subnet mask 255.255.255.0
Unfortunatelly I can't see my Webcam. If I connect Webcam to the first Card it works flawlessly. Any suggestions ?
thank you

---

### Post by DuckHook on 2019-04-11
Very confusing post:

[LIST=1]
[*]What do you mean by "Linux machine on a Win machine"? Is Linux running in a VM on Windows? Did you add two virtual NICs to the VM?
[*]Or is the "Windows machine" description superfluous? Does it just mean you are dual-booting with Windows as your other OS?
[*]Which 'buntu flavour and version?
[*]Why two NICs? What are you trying to do?
[/LIST]
Pls provide complete description, details and background.

Assuming you are running Linux on bare metal and further depending on your needs:

[https://help.ubuntu.com/lts/serverguide/network-configuration.html.en](https://help.ubuntu.com/lts/serverguide/network-configuration.html.en)	&#8230;especially the section on "bridging".
[https://help.ubuntu.com/community/Internet/ConnectionSharing](https://help.ubuntu.com/community/Internet/ConnectionSharing)	&#8230;if sharing

Also, if bridging:
[https://wiki.linuxfoundation.org/networking/bridge](https://wiki.linuxfoundation.org/networking/bridge)

For a more general overview (it's dated but still useful for the concepts):
[https://wiki.ubuntu.com/Networking](https://wiki.ubuntu.com/Networking)

---

### Post by novio8 on 2019-04-12
It is just a PC that used to have Win7 installed.
I installed Ubutu 18.04[
Machine has two network ports that are visible and configurable
in Ubuntu Network Manager. Both network Ports work individually
but they dont function at the same time.
Port one is connected to Router, port two has an IP WebCam
I would like to stream WebCam to other Computers on the Network

I would like to use Network Manager to configure this setup and rather avoid
Terminal. 


QUOTE=DuckHook;13851174]Very confusing post:

[LIST=1]
[*]What do you mean by "Linux machine on a Win machine"? Is Linux running in a VM on Windows? Did you add two virtual NICs to the VM?
[*]Or is the "Windows machine" description superfluous? Does it just mean you are dual-booting with Windows as your other OS?
[*]Which 'buntu flavour and version?
[*]Why two NICs? What are you trying to do?
[/LIST]
Pls provide complete description, details and background.

Assuming you are running Linux on bare metal and further depending on your needs:

[https://help.ubuntu.com/lts/serverguide/network-configuration.html.en](https://help.ubuntu.com/lts/serverguide/network-configuration.html.en)	…especially the section on "bridging".
[https://help.ubuntu.com/community/Internet/ConnectionSharing](https://help.ubuntu.com/community/Internet/ConnectionSharing)	…if sharing

Also, if bridging:
[https://wiki.linuxfoundation.org/networking/bridge](https://wiki.linuxfoundation.org/networking/bridge)

For a more general overview (it's dated but still useful for the concepts):
[https://wiki.ubuntu.com/Networking](https://wiki.ubuntu.com/Networking)[/QUOTE]

---

### Post by SeijiSensei on 2019-04-12
1) The two interfaces need to be in separate subnets.  You would need to manually assign an IP to the second interface in another subnet, say 192.168.1.1.

2) You need to enable packet forwarding on the PC by editing (as root with sudo) /etc/sysctl.conf and removing the hash mark from the line that reads
```
net.ipv4.ip_forward=1
```

Ubuntu, like most Linux distribution will not pass packets between interfaces by default as a security measure.  Reboot to activate this change.

You should give the camera an address in the second subnet, e.g, 192.168.1.2, and set its default gateway to point to the address of the PC to which it is connected.

There's no need for bridging.

---

### Post by novio8 on 2019-04-12
SeijiSensei Thanx,
I followed your instructions. It seems that it works to a point.
I can't see Wbcam from Computers that are on the 192.168.0. network and I cant ping the camera. 
Ubuntu can show Webcam stream that is on 192.168.1. second network interface.
From Ubuntu I can access disks that are on 192.168.0.
Any suggestions ?

---

### Post by SeijiSensei on 2019-04-12
Probably need to add some routes.

For the machines on the .0 network, what are their default gateways?  If they point to a router upstream (one that connects to the Internet for example), then they are sending the traffic for 192.168.1 to that device rather than the PC.  Does the PC have another interface that connects to the router?

Please show us the results of the command "route -n" in [noparse]```

```[/noparse] tags on the Ubuntu PC acting as a router, and from one of the computers on the .0 network if it is running Linux.  If all those machines run Windows, pick one, type "route print" at the command prompt, and give us just the IPv4 routing table.

The simplest solution might be to add static routes in the upstream router for .0 and .1, but that only works if the router can talk to the PC.  So let's see the routing tables, and we'll go from there.

(As an example, all my computers point to the same router.  I also have a VPN that interconnects one machine in my office to a number of virtual machines out in the cloud.  On my default router, there is a static route that forwards traffic for the cloud machines over to the computer that is the endpoint of the VPN.  When I connect to one of those remote machines, the traffic passes first though the main router, then is passed to the local endpoint machine which forwards it to the VPN hosts.)

---

### Post by novio8 on 2019-04-13
UBUNTU

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.0.88    0.0.0.0         UG    101    0        0 enp5s0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 enp3s0
192.168.0.0     0.0.0.0         255.255.255.0   U     101    0        0 enp5s0
192.168.1.0     0.0.0.0         255.255.255.0   U     102    0        0 enp3s0

OSX Machine

Routing tables

Internet:
Destination        Gateway            Flags        Refs      Use   Netif Expire
default            192.168.0.88       UGSc          305        0     en0
127                localhost          UCS             0        0     lo0
localhost          localhost          UH             22     1346     lo0
169.254            link#8             UCS             1        0     en0
192.168.0          link#8             UCS             6        0     en0
192.168.0.6        			  UHLWIi          1       21     en0    773
192.168.0.29/32    link#8             UCS             0        0     en0
192.168.0.88/32    link#8             UCS             1        0     en0
192.168.0.88      				  UHLWIir       151        0     en0   1169
192.168.0.255     		 UHLWbI          0        1     en0
224.0.0/4          link#8             UmCS            1        0     en0
224.0.0.251       			   UHmLWI          0        0     en0
255.255.255.255/32 link#8             UCS             0        0     en0

---

### Post by SeijiSensei on 2019-04-15
So is 192.168.0.88 a router, perhaps one connected to the Internet? Since it's the default gateway all traffic gets sent to it.  It has no rule for traffic in 192.168.1.0/24 so it tries to send it upstream, not to the PC where the camera is connected.

Your best solution to this is to add a static route to 192.168.0.88.  The route should forward traffic for 192.168.1.0/24 to 192.168.0.6, if that is still the address of the Ubuntu PC.  You'll need to read the router documentation to figure out how to do this.

---

### Post by novio8 on 2019-04-15
thank you SeijiSensei,
yes 192.168.0.88 is just a modem that is connected to internet. I have separate router IP 192.168.0.1.
I can see WebCam On Ubuntu PC.
Is there anything that I can do inside Ubuntu Network Manager?

---

### Post by SeijiSensei on 2019-04-16
One thing you can try is making the PC the default gateway for all the machines.  (You say 192.168.0.1 is a router, but from the routing tables above, no machine ever sends traffic directly to it. They use 192.168.0.88 as their default gateway, the one associated with the 0.0.0.0 network address in the tables you posted.)

If you make the PC the clients' default gateway, then they will all send traffic there.  Packets for the .0 and .1 networks will be routed accordingly.  Packets for other addresses will be sent to the PC's default gateway and presumably out to the Internet.

If the machines get their IP information from a DHCP server, you can change 192.168.0.88 to 192.168.0.6 there.  If you do this, I'd make sure the PC has a static IP address at .0.6.  You can do this by configuring the PC to have static addresses (my choice), or you can "reserve" the .0.6 address in the DHCP server and attach it to the PC's MAC address so it always gets the same IP.

---

### Post by novio8 on 2019-04-17
Again, thank you SeijiSensei.
I'm still confused. 
If I have two NC on Ubuntu Machine and just one of them is connected to the router and 
the rest of the network IP 192.168.0.1, how then the traffic from the second NC (IP 192.168.1.1) will go
through the first NC an then to the rest of the Network. 
Obviously I'm not good at setting networks and I would prefer using Network Manager, especially as
I might corrupt my installation.

---

### Post by SeijiSensei on 2019-04-17
Does the camera also have a setting for "default gateway?" Set it to 192.168.1.1.  

If both the camera and the networked computers on 192.168.0.0/24 use the PC as their default gateway rather than 192.168.0.88, then the traffic should be routed correctly.

---

### Post by novio8 on 2019-04-18
I already set camera's default gateway to 192.168.1.1.
And computers on 192.168.0.0 are all pointed to 192.168.0.1

---

### Post by SeijiSensei on 2019-04-18
Well, then it won't work.  As I said, all the machines need to have the PC to which the camera is connected as their default gateway.  

Try changing one client PC's network configuration manually to use the Ubuntu PC as its gateway.  Does that work?

---

### Post by novio8 on 2019-04-18
thanx again, I will follow your advice and point  OSX Machine to Ubuntu as GAteaway

---

### Post by novio8 on 2019-04-19
Result:
from OSX I can ping the second NC IP 192.168.1.1, and the first NC IP 192.168.0.6
but I can't ping camera IP 192.168.1.44
Camera is connected and working as expected on Ubuntu PC

---

