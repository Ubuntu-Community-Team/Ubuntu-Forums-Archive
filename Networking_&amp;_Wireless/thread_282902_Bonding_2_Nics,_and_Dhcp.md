---
title: "Bonding 2 Nics, and Dhcp"
date: 2006-10-23
forum: Networking &amp; Wireless
---

### Post by miked06 on 2006-10-23
Hi all,
Here is my hardware network wise, I have one onboard nic and three linksys pci nics ubuntu recognizes all of them and I can get internet through any of them.  What I want to do is take two incomming internet connections on two nics (eth0 and eth1) and bond them to create bond0. I have this step completed and I can get internet through bond0 however when I was doing this I thought that bonding would double my speed.  Both incoming connections are about one meg dl so i thought i would be getting 2megs dl but i'm still on one meg.  I have forced both nics to full duplex and tried messing with the different settings modes of bonding mode but some contrisct the speed and otheres only give 1 meg. here is the script that I run to bond the two cards:

```

mii-tool -F 10baseT-FD eth0
mii-tool -F 10baseT-FD eth1

modprobe bonding mode=0 miimon=100

ifconfig eth0 down
ifconfig eth1 down
ifconfig bond0 hw ether 00:11:22:33:44:66
ifconfig bond0 198.82.XXX.XXX up

ifenslave bond0 eth0 eth1

```

After i get this working properly I just need some help installing dhcp, I had it working properly(assigning different computers ip's), but something is wrong with the routing part?

Thanks

---

### Post by miked06 on 2006-10-23
bump^

---

### Post by BrianK on 2006-10-23
I'm having problems with bonding in Ubuntu as well (was just about to post about it when I searched & found your post... I may still).

A good way to see what's happening is to install iptraf & monitor all interfaces. Currently, iptraf only shows one of my four interfaces doing anything (eth2 in my case).

still researching this myself.

I don't think I would configure your interface like you are.  The more standard route is to do it in the init scripts.  I've added the following lines to /etc/network/interfaces:
```
# BK's link aggregation
auto bond0
iface bond0 inet static
        address 192.168.0.2
        netmask 255.255.255.0
        gateway 192.168.0.1
        up ifenslave bond0 eth2 eth3 eth4 eth5
        down ifenslave -d bond0 eth2 eth3 eth4 eth5

```

It would follow, then, that to use DHCP, you'd simply change "static" to "dynamic" and remove the address, netmask & gateway lines.  That said, you'll need some other DHCP server as the stuff coming from your two outbound connections won't apply.

Lot's of very good info here: [http://linux-net.osdl.org/index.php/Bonding#Bonding_Configuration](http://linux-net.osdl.org/index.php/Bonding#Bonding_Configuration)

---

### Post by miked06 on 2006-10-23
is that code segment correct becuase i can't get bond0 to be an acutal interface with that segment

---

### Post by netztier on 2006-10-25
> **miked06 said:**
> ```

mii-tool -F 10baseT-FD eth0
mii-tool -F 10baseT-FD eth1

```


Ehm.. 

are you absolutely shure you want to run your cards with **10Mbit full duplex**?

In 9 out of 10 cases this WILL result in a duplex mismatch that will cripple perfomance. The rare tenth case is the one where you actually have a switch at the other end of the cables that has it's interfaces also configured to 10Mbps full duplex.

**Ceterum censeo:** leave your NICs to "auto", unless you know you *can* and *will* configure full duplex on the switch ports, too. Classic ethernet hubs don't support full duplex, there's no point in configuring it in that case.

regards

Marc

---

### Post by miked06 on 2006-11-01
ya your right i actually set up my bonding another way that works and i did some reading and found that the switch your connected to must be able to support port trunking and apparently mine does not.

---

