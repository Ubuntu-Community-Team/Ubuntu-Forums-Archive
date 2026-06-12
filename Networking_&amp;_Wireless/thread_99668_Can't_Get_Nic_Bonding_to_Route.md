---
title: "Can't Get Nic Bonding to Route"
date: 2005-12-06
forum: Networking &amp; Wireless
---

### Post by ubusole on 2005-12-06
Hi All.  This is my first post / question.  

I configured bonding on my system according to the only how-to guid I could find: [http://www.howtoforge.org/nic_bonding]("http://www.howtoforge.org/nic_bonding")

After two debian to ubuntu changes (fonts and aliases) I got it to work.  The problem is it only works on the local subnet.  I cant get it to go through my router.

I can ping local host
I can ping bond0
I can ping local subnet addresses
I can ping the gateway

I can't ping anything outside the gateway.  I get "Destination Host Unreachable"

I would greatly appreciate any help.  Thanks!

Here's my /etc/network/interfaces:

[FONT="Courier New"]
# NIC Bonding interface
auto bond0
iface bond0 inet static
	hwaddress ether 00:06:5B:3F:40:AE
	address 10.1.1.31
	netmask 255.255.255.0
	gateway 10.1.1.1
	dns-nameservers 10.1.1.10
	up ifenslave bond0 eth0 eth1
	down ifenslave -d bond0 eth0 eth1

# The primary network interface
auto eth0
iface eth0 inet static
	address 10.1.1.31
	netmask 255.255.255.0
	gateway 10.1.1.1

# The second network interface
auto eth1
iface eth1 inet static
	address 10.1.1.31
	netmask 255.255.255.0
	gateway 10.1.1.1
[/FONT]

Here's my running ifconfig:

[FONT="Courier New"]
bond0     Link encap:Ethernet  HWaddr 00:06:5B:3F:40:AE
          inet addr:10.1.1.31  Bcast:10.1.1.255  Mask:255.255.255.0
          inet6 addr: fe80::206:5bff:fe3f:40ae/64 Scope:Link
          UP BROADCAST RUNNING MASTER MULTICAST  MTU:1500  Metric:1
          RX packets:9400 errors:0 dropped:0 overruns:0 frame:0
          TX packets:9204 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:877574 (857.0 KiB)  TX bytes:7323994 (6.9 MiB)

eth0      Link encap:Ethernet  HWaddr 00:06:5B:3F:40:AE
          inet addr:10.1.1.31  Bcast:10.255.255.255  Mask:255.255.255.0
          inet6 addr: fe80::206:5bff:fe3f:40ae/64 Scope:Link
          UP BROADCAST RUNNING SLAVE MULTICAST  MTU:1500  Metric:1
          RX packets:4725 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4592 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:424823 (414.8 KiB)  TX bytes:3656093 (3.4 MiB)
          Interrupt:28

eth1      Link encap:Ethernet  HWaddr 00:06:5B:3F:40:AE
          inet addr:10.1.1.31  Bcast:10.255.255.255  Mask:255.255.255.0
          inet6 addr: fe80::206:5bff:fe3f:40ae/64 Scope:Link
          UP BROADCAST RUNNING SLAVE MULTICAST  MTU:1500  Metric:1
          RX packets:4675 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4612 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:452751 (442.1 KiB)  TX bytes:3667901 (3.4 MiB)
          Interrupt:29

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:379623 errors:0 dropped:0 overruns:0 frame:0
          TX packets:379623 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:2016871056 (1.8 GiB)  TX bytes:2016871056 (1.8 GiB)[/FONT]

Here's my route

[FONT="Courier New"]
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
localnet        *               255.255.255.0   U     0      0        0 bond0
localnet        *               255.255.255.0   U     0      0        0 eth0
localnet        *               255.255.255.0   U     0      0        0 eth1
default         10.1.1.1        0.0.0.0         UG    0      0        0 eth1
default         10.1.1.1        0.0.0.0         UG    0      0        0 eth0
default         10.1.1.1        0.0.0.0         UG    0      0        0 bond0
[/FONT]

I have a dual Broadcom BCM5701 Gigabit card

---

### Post by mips on 2005-12-06
Never done or tried this but I think i know what is causing the problem.

Lets first try and explain what is happening here. With NIC bonding/teaming you want both NIC's to appear as one and basically double (in theory) your network throughput.

What happens is that by bonding you are actually creating a virtual/phantom interface. This is the interface that must handle all the traffic and be configured for TCP/IP stack. The physical interfaces only do Layer 2 stuff.

You now have three interfaces with the same IP address, that is going to confuse the router like hell. It wuold not know where to send the returning packet. Looking in its ARP table it will find three MAC address for that one IP address. IP address conflict is the word here.

You must only configure the **bond0** interface with the IP address, netmask, gateway, DNS etc. 

**The physical interfaces (eth0 & eth1) do NOT get configured except for ensuring they run exactly the same Speed & Duplex.**

Try this and let us know what happens.

---

### Post by ubusole on 2005-12-06
Thanks!

It's working now - even after a reboot.  I removed ALL references to eth0 and eth1 from the /etc/network/interfaces file.

For anyone else interested, here's my config and what I did:

(1) installed ifenslave-2.6
(2) made changes to the files below
(3) ran update-modules
(4) ran modprobe bonding
(4) restarted the network - It works!

**/etc/network/interfaces**

[FONT="Courier New"]auto lo
iface lo inet loopback
# NIC Bonding interface
auto bond0
iface bond0 inet static
        hwaddress ether 00:04:7B:30:4A:AC
        address 10.1.1.101
        netmask 255.255.255.0
        gateway 10.1.1.1
        dns-nameservers 10.1.1.1
        up ifenslave bond0 eth0 eth1
        down ifenslave -d bond0 eth0 eth1[/FONT]

**/etc/modprobe.d/aliases ** (made the following add/remove)

[FONT="Courier New"]# alias net-pf-10 ipv6
alias bond0 bonding
alias eth0 e100
alias eth1 e100
options bonding mode=0 miimon=100[/FONT]

**/etc/modutils/actions**

[FONT="Courier New"]probeall bond0 eth0 eth1 bonding[/FONT]

---

### Post by trubblemaker on 2007-01-10
any idea if this works for wireless cards, or of one that will work for wireless cards?

---

### Post by mips on 2007-01-10
Hmm, why not try it and let us know ?

The principal is the same but i dont know if this is something supported by wireless.

---

### Post by trubblemaker on 2007-01-10
yeah working on it, small issue's keep popping up, ifenslave only want's ethN and wireless like to pick different names, 

also they need to associated to an ap and ifenslave doesn't want them up at all before using them, in otherwords I let you know.

---

### Post by trubblemaker on 2007-01-10
little tricky you need to rename your interfaces correctly (ethN not wlan0)
you need to use the arp option instead of mii 
and you need to change the essids to what you want them to be but... it works.
l'm getting a second faster download on average, (reported by [stopwatch feature of this site]("http://www.numion.com/Stopwatch/index.html?")  will try and write up a howto for all that are interested later and post it here for those that happen to get an extra wireless card and want more reliable and sometimes faster downloads.

---

### Post by mips on 2007-01-11
> **trubblemaker said:**
> little tricky you need to rename your interfaces correctly (ethN not wlan0)
you need to use the arp option instead of mii 
and you need to change the essids to what you want them to be but... it works.
l'm getting a second faster download on average, (reported by [stopwatch feature of this site]("http://www.numion.com/Stopwatch/index.html?")  will try and write up a howto for all that are interested later and post it here for those that happen to get an extra wireless card and want more reliable and sometimes faster downloads.

Nice! Thx ;)

---

### Post by trubblemaker on 2007-01-12
Got to do more work on ifenslave parameters, I have a 'fast 54M/bs' and a 'slow 54M/bs' wireless cards.  with nic bonding the I can get a faster download than just using the slow card, but it still can't beat my 'fast 54M/bs' card on it's own.

**faster card** driver: rt73  driver card: d-link g 122 
and 
**slow card** driver: ndiswrapper card: bcm4318 

native driver may or may not explain the faster 54M/bs card, as theoretically if both are set to 54M/bs as the rate I'd expect the same speed downloading.

I'll see if changing the bonding driver parameter at boot can increase the speed at all.  right now it's the default which I believe to be round robin packets.

update this when I can

---

### Post by illuniel on 2007-05-31
Hi, 
I am creating my own Load Balancing Router running ubuntu feisty now.  I followed the tutorial at: [http://www.howtoforge.com/network_bonding_ubuntu_6.10](http://www.howtoforge.com/network_bonding_ubuntu_6.10)
Thing is, i got a more than couple a questions on this:

this is my config
eth0 -> wifi router, ?? static ip/dhcp
eth1 -> pppoe (i tried replacing the ppp0 and i can't find out if it pings out or not), DHCP
eth2 -> has a connection linked to the MAC address of the device, DHCP

do you think it would work if i replace all references to eth1 to ppp0?
do you think it work if both isp's use dhcp and thus ppp0 and eth2 have different ip addresses?
do you think it would work if i set the mode to 5 or 6 instead of the default 0 (round robin)?

eth0 connects to a wifi router. should i install dhcp for that or is it automatic? or is it better to have a static ip for both so that they remain in the same subnet? 

do you think all those would run if i don't log in... (i am thinking of a box set up without a monitor, without a keyb and mouse, i mean it is a load balancing router)

Oh, lastly, i am not using this type of machine for this project yet but do you think i can make use of my almost 20yr old p133mhz/32mb EDO ram for this? :D

---

### Post by trubblemaker on 2007-05-31
> **illuniel said:**
> Hi, 
I am creating my own Load Balancing Router running ubuntu feisty now.  I followed the tutorial at: [http://www.howtoforge.com/network_bonding_ubuntu_6.10](http://www.howtoforge.com/network_bonding_ubuntu_6.10)
Thing is, i got a more than couple a questions on this:

this is my config
eth0 -> wifi router, ?? static ip/dhcp
eth1 -> pppoe (i tried replacing the ppp0 and i can't find out if it pings out or not), DHCP
eth2 -> has a connection linked to the MAC address of the device, DHCP

do you think it would work if i replace all references to eth1 to ppp0?

no idea, looks like it's worth a shot.
> **illuniel said:**
> 
do you think it work if both isp's use dhcp and thus ppp0 and eth2 have different ip addresses?

can't help you with ppp0 don't know it.
> **illuniel said:**
> 

do you think it would work if i set the mode to 5 or 6 instead of the default 0 (round robin)?

eth0 connects to a wifi router. should i install dhcp for that or is it automatic? 

should be automatic, be aware that bonding uses the same mac address for all devices, (I think that it will use eth0's mac.) so if you have any mac firewalls, or specail setup be aware..
> **illuniel said:**
> 
or is it better to have a static ip for both so that they remain in the same subnet? 

as stated before they will try and obtain the same ip because they will have the same mac... 
you will have to manually set the essid for the wirless after brining up bond0.... it's a definiately not straight forward to get wirless to work with bond0 I've done it.... but my results so far aren't encouraging....
> **illuniel said:**
> 

do you think all those would run if i don't log in... (i am thinking of a box set up without a monitor, without a keyb and mouse, i mean it is a load balancing router)

yep no worries, it will run without you logged in
> **illuniel said:**
> 


Oh, lastly, i am not using this type of machine for this project yet but do you think i can make use of my almost 20yr old p133mhz/32mb EDO ram for this? :D

hell yeah if that's it's only job should be fine....

---

### Post by illuniel on 2007-05-31
whoa! thanks for that really speedy reply!

anyway....

i wanted to note that the eth0 is output to a router. it would supply  the internet connection to my  wireless network.  Would the feisty box give the router an ip (dhcp) or do i need to set both to use static ip's?

also, if eth1 and eth2 are  different isp's and both are dhcp by default(can't set static), how would that affect the bond0?

thanks much!

---

### Post by mips on 2007-06-01
> **illuniel said:**
> 
also, if eth1 and eth2 are  different isp's and both are dhcp by default(can't set static), how would that affect the bond0?


**[COLOR="Red"]Bonding will not work for you and it is not what you are looking for. You need to look into diverse routing/dual gateways instead.[/COLOR]**

[http://www.linux.org/docs/ldp/howto/Adv-Routing-HOWTO/lartc.rpdb.multiple-links.html](http://www.linux.org/docs/ldp/howto/Adv-Routing-HOWTO/lartc.rpdb.multiple-links.html)
[http://gentoo-wiki.com/Dual_internet_connections](http://gentoo-wiki.com/Dual_internet_connections)
[http://gentoo-wiki.com/TIP_Dual-Homed_Gentoo_Server](http://gentoo-wiki.com/TIP_Dual-Homed_Gentoo_Server)

---

### Post by illuniel on 2007-06-03
hey cool! 
thanks for the redirect! now reading on that.

---

### Post by weenis on 2008-05-19
There is a wireless internet service at my apartment complex offering 3 static IPs for one price. The connection speed is 3 Mbps. I don't know yet if this is per IP or for all 3 combined.

Regardless, I would like to pool all 3 into one connection. All 3 connections will likely be on the same subnet since they are on the same AP. Would I do nic bonding or a dual home/loading balanced setup? 

Thanks

---

### Post by trubblemaker on 2008-05-20
You can do nic bonding here but my experiments only show an averaging of the speeds of both nics and I didn't get a boost in speed as I wished.  Maybe with some tweaking you can get better speed than I did.  Certainly it's worth a shot.

---

