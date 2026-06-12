---
title: "No DHCPOFFERS received... again!"
date: 2007-12-14
forum: Networking &amp; Wireless
---

### Post by ipainchaud on 2007-12-14
I am currently configuring an AMD 64bits server. It has 2 Ethernet cards and has Ubuntu 7.10 64bits server installed. One of my ethernet cards is on board, the second one is a D-Link DFE-550TX (a PCI Ethernet card). The "on board interface" is working fine, but when I plug the second on my lan, nothing.

------- ifconfig eth1 gives:
eth1     Link encap:Ethernet   HWaddr 00:17:9A:BA:F1:AD
            inet6 addr: fe80::217:9aff:feba:f1ad/64 Scope:Link
            UP BROADCAST RUNNING MULTICAST MTU:1500  Metric:1
            RX packets:0 errors:0 dropped:0 overruns:0 frame:0
            TX packets:107 errors:0 dropped:0 overruns:0 carrier:0
            collisions:0 txqueuelen:1000
            RX bytes:0 (0.0 b)  TX bytes:6858 (6.6 KB)
            Interrupt:16 Base address:0x9c00

------- lspci | grep Ethernet gives:
00:14:0 Bridge: nVidia Corporation MCP51 Ethernet Controller (rev a3)
04:08:0 Ethernet controller: VIA Technologies, Inc. VT6105 [Rhine-III] (rev86)

------- lsmod | grep -i via gives:
via_rhine               36104  0
mii                          14592  1 via_rhine

------- dmesg | grep eth1 gives:
[   117.189383] eth1: no IPv6 routers present
[   128.487590] eth1: link up, 100Mbps, full-duplex, lpa 0x45E1

------- cat /etc/network/interfaces gives:
auto lo eth0 eth1
iface lo ineth loopback
iface eth0 inet dhcp
iface eth1 inet dhcp

------- ifup eth1 gives:
sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 5
..... interval 13
..... interval 13
No DHCPOFFERS received.
No working leases in persistent database - sleeping.


I tried to put a static address on eth1, it seems to be fine when I ifconfig, but when I ping [www.google.ca:](www.google.ca:) it gives a message of unreachable host

I almost installed the driver that comes with the network card's CD, but still other problems like "Unable to find kernel source" when I try to compile it. I went into the Makefile to realise that it is another Rhine driver that looks quite similar to the one already installed...

Please help! I read every other threads of the same title and still no answer...

Thanks

Israel

---

### Post by mellowd on 2007-12-14
I assume you getting an IP address via some sort of router? Are you able to check the logs of this device to see if it's even getting any sort of dhcp request?

---

### Post by Sav on 2007-12-17
I have problem with the same ethernet chipset.
It's weird becasue with feisty all was ok.

[http://ubuntuforums.org/showthread.php?p=3967002#post3967002](http://ubuntuforums.org/showthread.php?p=3967002#post3967002)

---

### Post by ipainchaud on 2007-12-18
Yes, I was supposed to get an address from a DHCP server to whom I have no access (lets call this DCHP server: Weirdo).

I made another test this morning and got something very interesting and, unfortunately, very confusing to me!

Since I don't have access to the Weirdo DHCP I made my own little lan with a router/DHCP server to whom I have access and guess what, my second network card (D-Link, eth1, RhineIII) did get a DHCPOFFER!

This confuses me big time since the same ethernet card with the very same configuration is not able to get a DHCP offer from the Weirdo DHCP Server but has no problem with my router. All this would normally lead me to beleive that the problem is with the DHCP(client/Server) configuration but my configuration seems to be the same for my 2 network cards... And, with my first "on board" ethernet card, no problem to connect to the weirdo DHCP server.

Does anybody have any idea of the problem?

---

### Post by mellowd on 2007-12-18
Can you give the full spec of your network? I'm a bit confused as to where this other dhcp server lies

---

### Post by HermanAB on 2007-12-18
One of your DHCP servers *must* be 'Authoritative'.  The default install of the DHCP is 'non-authoritative'.  You got to read up on that to understand what, how and why.

Cheers,

Herman

---

### Post by ipainchaud on 2007-12-18
I don't have many specs to give! But here is what I have:

I am configuring a mirror server. It is going to be plugged on a lan and to a router that leads to an ISP.

I did my first test having only one cable that led to our only lan. This cable leads to a switch and after that, I am not so sure who is the DHCP server... I only know that their is a DHCP server out their that is supposed to give me an IP address. Then I plugged my lan cable to the first Network Card and looked if this network cable worked correctly and it did. A little while later, I plugged this same cable on my second Network Card. I renewed the connection and found out that it didn't worked!

At this point I thought that my problem was at the network card level. Then, thanks to you mellowd, I wanted to see the logging of that DHCP server but didn't have access to that one, so I used a router that I can access and plugged it into the non working ethernet card to realise that this time it worked! (I received an IP address this time and could ping the only other computer plugged to the router)

Now, I don't know anything about Authoritative and non Authoritative DHCP servers. I will look at what that meens, but while I do that, if these details can help anybody understand out their, I'll appreciate very much.

---

### Post by mellowd on 2007-12-18
I assume this is at work and not at home? You never said at the start. First of all you could use wireshark to check exactly where you might be getting any IP address. Secondly, it's usually best practice for a server to have a fixed IP, not a dynamic one. This helps a lot when trying to troubleshoot further connection problems.

---

### Post by ipainchaud on 2007-12-18
As said earlier:
  I tried to put a static address on eth1, it seems to be fine when I ifconfig, but when I ping [www.google.ca:](www.google.ca:) it gives a message of unreachable host.

Ok, I feel now that I have to retest that one but can't do it now. I'll come back on that one.

---

### Post by mellowd on 2007-12-18
> **ipainchaud said:**
> As said earlier:
  I tried to put a static address on eth1, it seems to be fine when I ifconfig, but when I ping [www.google.ca:](www.google.ca:) it gives a message of unreachable host.

Ok, I feel now that I have to retest that one but can't do it now. I'll come back on that one.

Have you configured your gateway correctly?  If you put a static address on and do a traceroute to google, how far do you get?

---

### Post by trobbins on 2007-12-18
I had a similar problem with my desktop Gusty install on a PC with two NICs.  Both nics were set to DHCP but sometimes one would get an IP and the other would refuse to do so.  I even ran "sudo dhclient" or "sudo dhclient eth0"  I had to reboot the computer in order to obtain an IP, which I thought was weird.  So, I went to :
System > Administration > Network > Properties and disabled "enable roaming mode"

This resolved my problems.  Now, all my NICs update via DHCP without issues.  I don't know what roaming mode is, but I found it's important to turn it off and set each NIC to static or DHCP.

---

### Post by HermanAB on 2007-12-18
Note that to have a successful connection to the internet, you need more than just an IP address.  You need the address(es) of one or more DNS.  You also need a default route to the gateway.  

A properly configured DHCP server will give you all that information, but if you assign the IP address manually, then you also need to configure the DNS (/etc/resolv.conf) and route manually (route add default gw w.x.y.z eth0).

Cheers,

Herman

---

### Post by ipainchaud on 2007-12-19
Well, I have tried a static address again and, no change!

Our network uses an address I know not being the best: 192.168.0.0

I have updated /etc/network/interfaces with:
auto lo eth0 eth1
...
iface eth1 inet static
  address 192.168.0.197              # a free address
  netmask 255.255.255.0

I ifdowned eth0 so it doesn't interfere
ifconfig gives something that looks very fine

/etc/resolv.conf looks fine to me:
search colmatec.int              # which is our domain name
nameserver 192.168.0.4
nameserver 192.168.0.1

my routing wasn't totally fine since no default route was there, but I fixed that one so that it gives:
Destination              Gateway              Genmask                  Flags Metric Ref      Use Iface
192.168.0.0            *                          255.255.255.0        U        0        0             0  eth1
default                    192.168.0.1        0.0.0.0                     UG     100    0             0 eth1

which is exactly the same as one other ubuntu box who is working fine!

With that configuration, I can't ping anyone! "Destination Host Unreachable". Same when I traceroute!

About the "roaming mode", first time I hear anything about that!

---

