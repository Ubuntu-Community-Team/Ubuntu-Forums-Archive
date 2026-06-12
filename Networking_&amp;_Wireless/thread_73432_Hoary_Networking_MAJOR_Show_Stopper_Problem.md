---
title: "Hoary Networking MAJOR Show Stopper Problem"
date: 2005-10-09
forum: Networking &amp; Wireless
---

### Post by kalarr on 2005-10-09
This is a long one, and its probably going to be a freaky one for many people. We're talking significant networking issues here and its really starting to annoy me endlessly. And I consider myself fluent in Linux networking. :confused:

Lets begin :-)

A client of mine has a workshop + office space. In this building are 5 different companies renting office space off my client. In order to keep costs down, they are all sharing the same DSL connection and just paying for their share of the bandwidth.

I have a server running Hoary. The machine is a P3 800. Until Saturday it was running with a single NIC as a proxy/dns/dhcp server. Previously, all the machines on the network were on 192.168.1.0/24 which was connected directly to a DSL router with NAT at 192.168.1.1. The proxy was at 192.168.1.253. The various machines on the network were split into several groups all getting their IP via DHCP. The proxy was set as the gateway and forwarded the packets on to the DSL router so that traffic accounting could be done. This way everyone could see how much bandwidth they used and pay for their share of the month cost. 

This past week my client has asked me to split the network up in to 3. He's finally taken my hint that the risk of viruses could affect him adversely with all these other companies sharing his network space.

The proxy has now become a full blown router/gateway. On Saturday I added 2 more NICs to the machine. Now we have 3 different networks.

192.168.1.0/24 (eth0) now has only the proxy at 192.168.1.253 and the DSL router at 192.168.1.1. There are no other hosts on this network.

192.168.2.0/24 (eth1) now has my clients network on it. All his hosts are now on this network to provide a physical separation from the other companies computers.

192.168.3.0/24 (eth2) is the new home for all the other companies using the single DSL connection. If they want to protect their hosts or whatever, its up to them to do so.

The DSL router does NAT between the Internet and 192.168.1.0/24 and I have now set up the proxy machine to do NAT/Masq between 192.168.1.0/24 and the other 2 networks. Basically, 192.168.1.0/24 has become a buffer and DMZ. Its been set up so that any persons that visit can connect to 192.168.1.0/24 but get completely blocked from the other hosts. Once finished, this will all be managed and controlled with iptables and tc/iproute2. Still, gotta get that far first.

This is pretty straight forward. But the problem now comes that eth1 and eth2 refuse to talk to the other hosts on their network. Before I go on, here is the current config details.

> 
root@proxy:~ # ip addr ls
1: lo: <LOOPBACK,UP> mtu 16436 qdisc noqueue
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
    inet6 ::1/128 scope host
       valid_lft forever preferred_lft forever
2: eth0: <BROADCAST,MULTICAST,UP> mtu 1500 qdisc pfifo_fast qlen 1000
    link/ether 00:c0:df:e5:27:ef brd ff:ff:ff:ff:ff:ff
    inet 192.168.1.253/24 brd 192.168.1.255 scope global eth0
    inet6 fe80::2c0:dfff:fee5:27ef/64 scope link
       valid_lft forever preferred_lft forever
3: eth1: <BROADCAST,MULTICAST,UP> mtu 1500 qdisc pfifo_fast qlen 1000
    link/ether 00:00:b4:a0:2b:4b brd ff:ff:ff:ff:ff:ff
    inet 192.168.2.254/24 brd 192.168.2.255 scope global eth1
    inet6 fe80::200:b4ff:fea0:2b4b/64 scope link
       valid_lft forever preferred_lft forever
4: eth2: <BROADCAST,MULTICAST,UP> mtu 1500 qdisc pfifo_fast qlen 1000
    link/ether 00:60:08:39:69:7e brd ff:ff:ff:ff:ff:ff
    inet 192.168.3.254/24 brd 192.168.3.255 scope global eth2
    inet6 fe80::260:8ff:fe39:697e/64 scope link
       valid_lft forever preferred_lft forever
5: sit0: <NOARP> mtu 1480 qdisc noop
    link/sit 0.0.0.0 brd 0.0.0.0
root@proxy:~ # ip route ls
192.168.3.0/24 dev eth2  proto kernel  scope link  src 192.168.3.254
192.168.2.0/24 dev eth1  proto kernel  scope link  src 192.168.2.254
192.168.1.0/24 dev eth0  proto kernel  scope link  src 192.168.1.253
default via 192.168.1.1 dev eth0
root@proxy:~ # cat /etc/network/options
ip_forward=yes
spoofprotect=yes
syncookies=yes
root@proxy:~ # cat /etc/network/interfaces
# The loopback network interface
auto lo eth0 eth1 eth2
iface lo inet loopback
iface eth0 inet static
    address 192.168.1.253
    netmask 255.255.255.0
    broadcast 192.168.1.255
    gateway 192.168.1.1
iface eth1 inet static
    address 192.168.2.254
    netmask 255.255.255.0
    broadcast 192.168.2.255
    gateway 192.168.1.253
iface eth2 inet static
    address 192.168.3.254
    netmask 255.255.255.0
    broadcast 192.168.3.255
    gateway 192.168.1.253
root@proxy:~ # ping -c1 192.168.1.253
PING 192.168.1.253 (192.168.1.253) 56(84) bytes of data.
64 bytes from 192.168.1.253: icmp_seq=1 ttl=64 time=0.121 ms

--- 192.168.1.253 ping statistics ---
1 packets transmitted, 1 received, 0% packet loss, time 0ms
rtt min/avg/max/mdev = 0.121/0.121/0.121/0.000 ms
root@proxy:~ # ping -c1 192.168.2.254
PING 192.168.2.254 (192.168.2.254) 56(84) bytes of data.
64 bytes from 192.168.2.254: icmp_seq=1 ttl=64 time=0.126 ms

--- 192.168.2.254 ping statistics ---
1 packets transmitted, 1 received, 0% packet loss, time 0ms
rtt min/avg/max/mdev = 0.126/0.126/0.126/0.000 ms
root@proxy:~ # ping -c1 192.168.3.254
PING 192.168.3.254 (192.168.3.254) 56(84) bytes of data.
64 bytes from 192.168.3.254: icmp_seq=1 ttl=64 time=0.140 ms

--- 192.168.3.254 ping statistics ---
1 packets transmitted, 1 received, 0% packet loss, time 0ms
rtt min/avg/max/mdev = 0.140/0.140/0.140/0.000 ms


Nothing spectacular there. The network doesn't use IPv6 so thats not an issue. The network interfaces are loading as expected at boot time. As you can see, the machine does talk to each interface. They are configured properly as far as I can see.

I should also point out that at the moment, until such time as things are working properly, these are the settings for iptables.

> 
root@proxy:~ # iptables -t nat -L
Chain PREROUTING (policy ACCEPT)
target     prot opt source               destination
REDIRECT   tcp  --  anywhere             anywhere            tcp dpt:www redir ports 3128

Chain POSTROUTING (policy ACCEPT)
target     prot opt source               destination
MASQUERADE  all  --  anywhere             anywhere

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination
root@proxy:~ # iptables -L
Chain INPUT (policy ACCEPT)
target     prot opt source               destination

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination


So essentially we have NAT implemented and yes, I do have it set to work as a transparent proxy through SQUID. Thats been there all along from the old days before I started these changes and it doesn't really have any impact on the problem here. The netfilter is basically WIDE open to make sure it is not a possible cause of the problem.

Now here comes the problem.

> 
root@proxy:~ # ping -c1 192.168.1.1
PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.
64 bytes from 192.168.1.1: icmp_seq=1 ttl=155 time=0.610 ms

--- 192.168.1.1 ping statistics ---
1 packets transmitted, 1 received, 0% packet loss, time 0ms
rtt min/avg/max/mdev = 0.610/0.610/0.610/0.000 ms
root@proxy:~ # ping -c1 192.168.2.1
PING 192.168.2.1 (192.168.2.1) 56(84) bytes of data.
From 192.168.2.254 icmp_seq=1 Destination Host Unreachable

--- 192.168.2.1 ping statistics ---
1 packets transmitted, 0 received, +1 errors, 100% packet loss, time 0ms

root@proxy:~ # ping -c1 192.168.3.1
PING 192.168.3.1 (192.168.3.1) 56(84) bytes of data.
From 192.168.3.254 icmp_seq=1 Destination Host Unreachable

--- 192.168.3.1 ping statistics ---
1 packets transmitted, 0 received, +1 errors, 100% packet loss, time 0ms

root@proxy:~ #


These hosts exist and are definitely turned on and plugged in to the switch. Hosts on those segments can ping each other, but the proxy can only talk to the DSL router at 192.168.1.1 (eth0). It can't talk to any other host on any of the other 2 networks.

So I figured I'd shut the interfaces down and bring them back online again. See if that improved things...

> 
root@proxy:~ # ifconfig eth1
eth1      Link encap:Ethernet  HWaddr 00:00:B4:A0:2B:4B
          inet addr:192.168.2.254  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::200:b4ff:fea0:2b4b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:21 dropped:0 overruns:0 carrier:42
          collisions:357 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:1406 (1.3 KiB)
          Interrupt:12 Base address:0xc800

root@proxy:~ # ifdown eth1
ifdown: interface eth1 not configured
root@proxy:~ # ifconfig eth1 down
root@proxy:~ # ifconfig
eth0      Link encap:Ethernet  HWaddr 00:C0:DF:E5:27:EF
          inet addr:192.168.1.253  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::2c0:dfff:fee5:27ef/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:994 errors:0 dropped:0 overruns:0 frame:0
          TX packets:676 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:93680 (91.4 KiB)  TX bytes:86010 (83.9 KiB)
          Interrupt:10 Base address:0xcc00

eth2      Link encap:Ethernet  HWaddr 00:60:08:39:69:7E
          inet addr:192.168.3.254  Bcast:192.168.3.255  Mask:255.255.255.0
          inet6 addr: fe80::260:8ff:fe39:697e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:136 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:11384 (11.1 KiB)  TX bytes:558 (558.0 b)
          Interrupt:9 Base address:0xc400

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:19 errors:0 dropped:0 overruns:0 frame:0
          TX packets:19 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:1800 (1.7 KiB)  TX bytes:1800 (1.7 KiB)
root@proxy:~ # ifup eth1
SIOCADDRT: Network is unreachable
Failed to bring up eth1.
root@proxy:~ # ifconfig eth1 up
root@proxy:~ # ifconfig eth1
eth1      Link encap:Ethernet  HWaddr 00:00:B4:A0:2B:4B
          inet addr:192.168.2.254  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::200:b4ff:fea0:2b4b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:27 dropped:0 overruns:0 carrier:54
          collisions:459 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:1854 (1.8 KiB)
          Interrupt:12 Base address:0xc800


I won't paste it, but the exact same errors happen for eth2 as well. The only interface there is no such error for is eth0.

So maybe its a hardware issue? I've checked the cables. I even made new cables and tested them to make sure it wasn't them. All the pins are correct according to my tester and the link lights on the NICs and the Switches show up as expected.

Maybe it was a driver or IRQ or I/O error?

> 
Oct  9 16:49:46 proxy kernel: ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 10
Oct  9 16:49:46 proxy kernel: PCI: setting IRQ 10 as level-triggered
Oct  9 16:49:46 proxy kernel: ACPI: PCI interrupt 0000:00:07.5[C] -> GSI 10 (level, low) -> IRQ 10
Oct  9 16:49:46 proxy kernel: PCI: Setting latency timer of device 0000:00:07.5 to 64
Oct  9 16:49:46 proxy kernel: ne2k-pci.c:v1.03 9/22/2003 D. Becker/P. Gortmaker
Oct  9 16:49:46 proxy kernel:   [http://www.scyld.com/network/ne2k-pci.html](http://www.scyld.com/network/ne2k-pci.html)
Oct  9 16:49:46 proxy kernel: ACPI: PCI interrupt 0000:00:10.0[A] -> GSI 10 (level, low) -> IRQ 10
Oct  9 16:49:46 proxy kernel: eth0: RealTek RTL-8029 found at 0xcc00, IRQ 10, 00:C0:DF:E5:27:EF.
Oct  9 16:49:46 proxy kernel: ACPI: PCI interrupt 0000:00:11.0[A] -> GSI 12 (level, low) -> IRQ 12
Oct  9 16:49:46 proxy kernel: eth1: RealTek RTL-8029 found at 0xc800, IRQ 12, 00:00:B4:A0:2B:4B.
Oct  9 16:49:46 proxy kernel: ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 9
Oct  9 16:49:46 proxy kernel: PCI: setting IRQ 9 as level-triggered
Oct  9 16:49:46 proxy kernel: ACPI: PCI interrupt 0000:00:12.0[A] -> GSI 9 (level, low) -> IRQ 9
Oct  9 16:49:46 proxy kernel: 3c59x: Donald Becker and others. [www.scyld.com/network/vortex.html](www.scyld.com/network/vortex.html)
Oct  9 16:49:46 proxy kernel: 0000:00:12.0: 3Com PCI 3c905 Boomerang 100baseTx at 0xc400. Vers LK1.1.19
Oct  9 16:49:46 proxy kernel: eth2: Dropping NETIF_F_SG since no checksum feature.
Oct  9 16:49:46 proxy kernel: ACPI: PCI interrupt 0000:00:12.0[A] -> GSI 9 (level, low) -> IRQ 9


So the cards are all running on different IRQs and different addresses. They're all PCI cards and so the computer/OS are dealing with the IRQs anyway. The only other card in the machine is a video card. Everything else is onboard and unused.

So heres my problem. The NICs are configured in /etc/network/interfaces and they are managed by ifconfig. ifup/ifdown both spit the dummy but the interfaces can be pinged. Just no other hosts that can be.

Thinking it might be the cards themselves, I took them out and tried them individually in another machine. They do work in the other machine. Admittedly, I didn't try them all together in the other machine before I left the clients site.

If anyone has a suggestion or ideas, I can log in to the site via SSH and try any changes as long as eth0 is able to take traffic. I'd really appreciate some help on this as its got me stumped. I can think of no valid reason as to why this sort of behaviour is happening.

For the value of it, the network is still firewalled by the DSL router. So having the proxy open as it is isn't a major issue just yet. I just want to get this working. Worst case scenario is that things go back to the way they were, and ultimately thats not really acceptable.

If this fails, I'm gonna have to go spend a few hundred on an appliance firewall to do this. My client is a small business so that an expense I'm going to truly struggle to convince them of. I've done this before using other distros and identical NICs so I am confused. On Monday I'm going to replace the 3com NIC with another one identical to eth1, but its only a minor change and doesn't explain why things are playing the way they are now.

Please Help.

---

### Post by kalarr on 2005-10-09
Anyone? Please? This really has got me stumped and thats not something I like to admit.

---

### Post by kalarr on 2005-10-09
After spending all weekend thinking about it, I think I might have nailed it.

In /etc/network/interfaces I specified a gateway directive for each NIC. I can't confirm it tonight because the machine has shutdown SSH for the night (I run a cron job to start/stop SSH so that it only runs at hours I'm likely to log in to it) but I'm pretty certain that if I remove the gateway definitions for eth1 and eth2 the problem will be resolved.

Will update tomorrow with results onces I've confirmed it. Its now 12:35am so I'm going to stop thinking about it and go to bed now.

---

### Post by dnapper on 2005-10-09
I have a similar problem with the 3com905 TX and 3com905B TX,
They seem to be found and recognized as network cards, but ubuntu aparently cannot use them,
I have tried both ubuntu 5.04 and the upcoming 5.10,

Initialy I tried to use them configured as DHCP,
and then by setting a static address.
sometimes when set as a static address, a long ping session will result in a second or so of returned pings. and then nothing for minutes.

I will be changing the network card again, to some other 3com model, in the hope it will work.

BTW I am writing this on Mepis, and had no problems with ether card,
Knoppix was Ok to, and they are both debian based, - so whats missing in the ubuntu distribution?


David.

---

### Post by kalarr on 2005-10-09
[QUOTE=kalarr]After spending all weekend thinking about it, I think I might have nailed it.

In /etc/network/interfaces I specified a gateway directive for each NIC. I can't confirm it tonight because the machine has shutdown SSH for the night (I run a cron job to start/stop SSH so that it only runs at hours I'm likely to log in to it) but I'm pretty certain that if I remove the gateway definitions for eth1 and eth2 the problem will be resolved.

Will update tomorrow with results onces I've confirmed it. Its now 12:35am so I'm going to stop thinking about it and go to bed now.[/QUOTE]

Okay, after putting this in to practice it has improved things mildly. eth2 now talks to machines on the 192.168.3.0/24 network, but eth1 doesn't. In fact, the weirdest part is that eth1 is doing nothing but get collisions on that interface. This is strange because there is only 4 other hosts on that segment and they're numbered statically from 1-4. The unfortunate part about this is that this is the network my client is actually on. eth2 is the rest of the building.
Anyone have any ideas? This is really frustrating me.

---

### Post by kalarr on 2005-10-09
Well, I finally gave in. I rebuilt the machine from scratch and put in 3 brand new NICs that were all identical. Set the machine running and now it all works as it should have.

I have no idea what caused the problem originally, but I did everything manually this time doing a very base install of Hoary. Things now work as they should and I can now start to work on the iptables and tc rulesets to start firewall and traffic shaping.

---

### Post by dnapper on 2005-10-10
I just found this in bugzilla:
[https://bugzilla.ubuntu.com/show_bug.cgi?id=11517](https://bugzilla.ubuntu.com/show_bug.cgi?id=11517)

--Quote--
Bugzilla Bug 11517 - No support for 3c509 in instaler

I tried instaling Hoary on a system with a 3c509 nic. The standard installer
would not find it, and the expert installer would allow me to select it from a
list of cards.
This enables it during installation but I had to put 3c509 in /etc/modules to
enable it in the installed system.

3c509 is an isapnp card so it should be safe to probe it (loading the module
fails if the card is not present).
--End Quote--

I know this is a different card than stated in the posts, but...
Maybe we are all suffering from a missing module in the ubuntu distribution.

David.

---

