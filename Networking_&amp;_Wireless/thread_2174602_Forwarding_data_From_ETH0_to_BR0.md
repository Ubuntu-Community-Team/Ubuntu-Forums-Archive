---
title: "Forwarding data From ETH0 to BR0"
date: 2013-09-15
forum: Networking &amp; Wireless
---

### Post by fcc-soc on 2013-09-15
Hello,

I'm trying to forward traffic from my server's unique NIC to br0.

[COLOR=#000000][FONT=Arial]My goal is to route a block of public IP's  (already routed over the server's main IP) to my virtual machines (which are connected to virtual bridge br0).
The block of ip's is /32.

[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Host Configuration:[/FONT][/COLOR]
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
        address 87.xxx.xxx.xxx
        netmask 255.255.255.0
        network 87.xxx.xxx.0
        broadcast 87.xxx.xxx.255
        gateway 87.xxx.xxx.254
        dns-nameservers 8.8.8.8

auto eth0:0
iface eth0:0 inet static
        address 157.xxx.xxx.xxx
        netmask 255.255.255.255
        broadcast 157.xxx.xxx.xxx
        gateway 192.168.0.1
        post-up route add -host address 157.xxx.xxx.xxx dev br0

auto br0
iface br0 inet static
        address 192.168.0.1  
        netmask 255.255.255.0
        broadcast:192.168.0.255
        bridge_ports vmachine
        address 192.168.0.1
        broadcast 192.168.0.255
        netmask 255.255.255.0


[COLOR=#000000][FONT=Arial]Virtual Machine Configuration:
[/FONT][/COLOR]
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
        address 192.168.0.2
        netmask 255.255.255.0
        broadcast 192.168.0.255

auto eth0:0
iface eth0:0 inet static
        address 157.xxx.xxx.xxx
        netmask 255.255.255.255
        broadcast 157.xxx.xxx.xxx
        gateway 192.168.0.1
        post-up route add default gw 192.168.0.1


[COLOR=#000000][FONT=Arial]I can ping every single ip inside the server and all public ip's are reacheable as expected but the traffic coming from outside world isn't getting routed to the virtual machine...
Such as ssh [EMAIL="user@157.xxx.xxx.xxx"]user@157.xxx.xxx.xxx[/EMAIL] is reaching the server.[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]
Forwarding has been enabled.[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]
Host Routing table entry's:[/FONT][/COLOR]

Kernel IP routing table
Destination       Gateway         Genmask         Flags Metric Ref    Use Iface
default           rbx-34-m0.fr.eu 0.0.0.0         UG    0      0        0 eth0
87.xxx.xxx.xxx    *               255.255.255.0   U     0      0        0 eth0
157.xxx.xxx.xxx.o *               255.255.255.255 UH    0      0        0 br0
192.168.0.0       *               255.255.255.0   U     0      0        0 br0
[COLOR=#000000][FONT=Arial]
Virtual Machine routing entry's:[/FONT][/COLOR]

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
default         192.168.0.1     0.0.0.0         UG    0      0        0 eth0
192.168.0.0     *               255.255.255.0   U     0      0        0 eth0


[COLOR=#000000][FONT=Arial]I don't want to use routing across isp provider for security reasons.
Thank you all.[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]


[/FONT][/COLOR]

---

### Post by s-bodet on 2013-09-15
> [COLOR=#000000][FONT=Arial]I can ping every  single ip inside the server and all public ip's are reacheable as  expected but the traffic coming from outside world isn't getting routed  to the virtual machine...
Such as ssh [EMAIL="user@157.xxx.xxx.xxx"]user@157.xxx.xxx.xxx[/EMAIL] is reaching the server.[/FONT][/COLOR]


Since your virtual machines are in a RFC1918 address space (ie non routed over the Internet), you'll need to perform IP translation somewhere.
I then notice the /32 on your eth0:0, it means you'll have to implement TCP/UDP port forwarding as well.

Let's say you have two VM 192.168.0.10 and 192.168.0.20.

If you want to ssh these hosts from the outside world, you'll need to decide on the destination TCP ports, for example :

157.x.x.x:1310 -> 192.168.0.10:22
157.x.x.x:1320 -> 192.168.0.20:22

otherwise your server has no way to know where to send packets when receiving 157.x.x.x:22.
You can find lots of examples of port forwarding with iptables.

Steve

---

