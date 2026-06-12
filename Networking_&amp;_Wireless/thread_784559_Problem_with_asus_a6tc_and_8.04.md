---
title: "Problem with asus a6tc and 8.04"
date: 2008-05-06
forum: Networking &amp; Wireless
---

### Post by pabloatilio on 2008-05-06
Friends:

I installed the 8.04 version AMD64 from scratch, not an upgrade, a notebook asus A6tc before was 7.01 and there were no problems with the plate ethernet network, but now yes, if I am not mistaken the driver is using the RTL8168B/811B.

The problem is the following, apparently there is some sort of connectivity because the router (I have a small home network) recognizes the name of the notebook, assigned an IP address (everything works under dhcp), but up and down connection permanently and that sometimes appears in the summary of equipment connected to the network and sometimes not.

It is impossible to get even with ping to the router. I tried to use the network-manager, then tried to disable and configure / etc / network / interfaces as follows:

auto eth0

iface eth0 INET DHCP

As I said earlier, the dhcp is not really that important because even came to the router with ping.

With the lspci I get the following:

01:00.0 Ethernet controller: Realtek Semiconductor Co.. Ltd. RTL8111/8168 PCI Express Gigabit Ethernet controller (rev 1)

With the ifconfig command goes:

Link encap: Ethernet direcciónHW 00: xx: xx: xx: xx: xx
inet6 address: fexx: xxx: dxff: fxcx: dxxf / xx Reach: Link
MULTICAST arribar dissemination are MTU: 1500 Metric: 1
RX packets: 4 errors: 0 dropped: 0 overruns: 0 frame: 0
TX packets: 0 errors: 0 dropped: 46 overruns: 0 carrier: 0
collisions: 0 txqueuelen: 1000
RX bytes: 2360 (2.3 KB) TX bytes: 0 (0.0 MB)
Interruption: 253 base address: 0x6000

As can be seen not leave any information like "inet address: xxx.xxx.x.xx Dissemination: xxx.xxx.x.xxx Mask: xxx.xxx.xxx.xxx" and also no information sent or anything of that.

I tried to install the driver from the manufacturer's page [http://www.realtek.com.tw/downloads/](http://www.realtek.com.tw/downloads/) etc., but I give the file make mistake. What I annoyed becasuse walking well in ubuntu 7.01 and without touching anything amiss in the "unspeakable" mr gates. In order ... thanks for your time and your help. Greetings.

last notice : If i shutdown (deactivate) the net-connection and up again , i can read the host in the summary router , but only for one minute or less, then the host disappear again  

Pablo Atilio


SOLVED 

The solution in : [http://www.jamesonwilliams.com/hardy-r8168.html](http://www.jamesonwilliams.com/hardy-r8168.html)

---

