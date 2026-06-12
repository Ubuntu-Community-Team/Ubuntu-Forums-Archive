---
title: "Dropped packets with static IP address"
date: 2015-04-22
forum: Networking &amp; Wireless
---

### Post by knoxy2 on 2015-04-22
Hi,

I've got several machines running either ubuntu 12.04 or 14.04. All of these machines are showing huge amounts of dropped RX packets, > 50%, for example:

```

eth0      Link encap:Ethernet  HWaddr 00:01:05:1a:e8:fc  
          inet addr:172.24.0.22  Bcast:172.24.255.255  Mask:255.255.0.0
          inet6 addr: fe80::201:5ff:fe1a:e8fc/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:108421686 errors:0 [COLOR=#ff0000]**dropped:62892958**[/COLOR] overruns:0 frame:0
          TX packets:68473201 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:9260306050 (9.2 GB)  TX bytes:71181524432 (71.1 GB)
          Interrupt:20 Memory:f7d00000-f7d20000 

```


These all have the same networking hardware:

```

00:19.0 Ethernet controller: Intel Corporation 82579LM Gigabit Network Connection (rev fa)
02:00.0 Ethernet controller: Intel Corporation 82574L Gigabit Network Connection

```

I originally noticed the issue when running 12.04 but after upgrading some machines to 14.04, the problem persists. 

I've confirmed all the cabling and connected switches are performing correctly.
I've tried updating the kernel and e1000e driver to the latest available.
There are no IP or MAC address conflicts on the network. 

The only thing that stops the massive packet drops are to use a DHCP assigned address.

Despite the huge number of dropped packets reported, network performance is otherwise fine. There are no errors in the logs. Ping shows no packet loss and response times are good.

Note that, strangely, the packet loss also occurs on an interface even if no address is configured.

I can reliably reproduce this with a fresh install. Just set a static IP in /etc/network/interfaces, for example:

```

# The primary network interface
auto eth0 
iface eth0 inet static
        address 10.0.10.201
        netmask 255.255.255.0
        broadcast 10.0.10.255
        gateway 10.0.10.1

```

I found 1 old thread in the entire ;) internet that discusses this, but alas, no resolution:

[https://www.raspberrypi.org/forums/viewtopic.php?f=28&t=16797](https://www.raspberrypi.org/forums/viewtopic.php?f=28&t=16797)

I'm at a total loss as to what's going on here. Anyone else seen this before? Any suggestions for resolving it?

Thanks!

---

### Post by TheFu on 2015-04-23
Bad connectors in the cards?
Do any other OSes on the same hardware NOT show this issue?

---

### Post by knoxy2 on 2015-04-23
> **TheFu said:**
> Bad connectors in the cards?
Do any other OSes on the same hardware NOT show this issue?

These are some embedded SBCs. The NICs are on the boards. I've got 4 systems all showing these symptoms, and only with a static IP. With DHCP addresses there are zero dropped packets.  These particular boards are all running Ubuntu 12.04 or 14.04.

We have a variant of the same board (more RAM & bigger CPU, same NICs) running in some other systems. These are running RHEL 6. They also have static IPs, but without this issue.

---

### Post by TheFu on 2015-04-23
Thanks for the clarity.  Here's what I use on 14.04 simple boxes, those without multiple networks, multiple NICs, or bridges:
```
auto lo
iface lo inet loopback

auto eth0
#iface eth0 inet dhcp
iface eth0 inet static
  address 172.22.22.20
  gateway 172.22.22.1
  netmask 255.255.255.0
  #mtu 9014
  dns-nameservers 172.22.22.200
  dns-search jdpfu.com jdpfu.lan
```

Doubt it will be helpful to you.  If you use DHCP, are the subnets/netmasks the same?  I'm still reaching/guess at ideas here.

---

### Post by chili555 on 2015-04-23
May I assume, and I only mention this because I am a bit OCD, that the declared address x.201 is outside the range of the DHCP server, if any?

Is the result the same with:```
# The primary network interface
auto eth0 
iface eth0 inet static
        address 10.0.10.201
        netmask 255.255.255.0
        #broadcast 10.0.10.255
        gateway 10.0.10.1
```Where are DNS nameservers declared? I suggest:```
# The primary network interface
auto eth0 
iface eth0 inet static
        address 10.0.10.201
        netmask 255.255.255.0
        gateway 10.0.10.1
        dns-nameservers 10.0.10.1 8.8.4.4
```

---

### Post by TheFu on 2015-04-23
Great point Chili!  Some DHCP servers don't like it when static IPs are assigned inside their IP management range.

---

### Post by knoxy2 on 2015-04-23
> **chili555 said:**
> May I assume, and I only mention this because I am a bit OCD, that the declared address x.201 is outside the range of the DHCP server, if any?

> **TheFu said:**
> Great point Chili!  Some DHCP servers don't like  it when static IPs are assigned inside their IP management  range.
Yes, .201 is outside the DHCP range on that network.

This also occurs on networks without DHCP, which is the normal operating mode for these devices. One of these is running 1000 miles away, completely isolated from my regular development network.

I only discovered that the static IP was the issue when I brought up a new system on the network serving DHCP. It got the DHCP address and had no issues, until I set it's static IP. I then reproduced it on the other boards as well.

Thanks for sharing some thought on this.

---

### Post by knoxy2 on 2015-04-23
Also note that when trying to sniff out the issue with wireshark, the dropped packets stop.

---

### Post by knoxy2 on 2015-04-23
More wierdness...

If I've got a static IP set, with the associated dropped packets, then attempt to acquire an address via dhclient, the DHCP acquisition fails and I retain the static IP. However, no more dropped packets are indicated by ifconfig and the network continues to function just fine.

I just don't know anymore....:cry:

Hope I don't end up like this guy: ;)
[http://www.bizjournals.com/denver/blog/broadway_17th/2015/04/rage-against-the-machine-fed-up-man-shoots.html](http://www.bizjournals.com/denver/blog/broadway_17th/2015/04/rage-against-the-machine-fed-up-man-shoots.html)

---

### Post by knoxy2 on 2015-04-23
Also, FWIW, if I remove the static IP config from /etc/network/interfaces and set it up via network manager, the problem persists.

---

### Post by SeijiSensei on 2015-04-23
If you can examine the entries in the DHCP server's lease table, make sure the problematic machine's Ethernet address, 00:01:05:1a:e8:fc, is not among them.  If it is, delete the entry and see if that fixes the problem.

Otherwise you might consider deleting all the existing leases on the DHCP server and forcing all the machines to get new ones.  Keep the problematic machine off the network until all the other machines have finished getting addresses.  Then see what happens.

If you can query the server's ARP table, see what entries it has for the machine's Ethernet address.  Have both the DHCP server and any upstream routers been rebooted?   It's possible that there is a duplicate entry in an ARP table somewhere.  You can look at the ARP table in Linux with the command "sudo arp -vn".  Works for DDWRT routers as well; here's mine:
```

root@DD-WRT:~# arp -nv
? (192.168.10.21) at 2c:27:d7:b2:a5:38 [ether]  on br0
? (192.168.10.100) at 00:11:11:30:33:c3 [ether]  on br0
? (192.168.10.46) at f8:d1:11:19:52:66 [ether]  on br0
? (192.168.1.1) at 18:1b:eb:8e:b9:9c [ether]  on vlan2

```
The router sees four Ethernet devices, one pointing to the upstream router connected on interface vlan2, and three LAN machines on a bridge.

---

### Post by matt_symes on 2015-04-23
Hi

> Also note that when trying to sniff out the issue with wireshark, the dropped packets stop.

Odd ! Is Wireshark turning on promiscuous mode on the card ?

Does it stop dropping packets if you turn it on manually ?

```
sudo ifconfig eth0 promisc
```

You can turn promiscuous off by putting a using *-promisc*.

Are many packets still being dropped when in promiscuous mode ?

Kind regards

---

### Post by knoxy2 on 2015-04-23
> **SeijiSensei said:**
> If you can examine the entries in the DHCP server's lease table, make sure the problematic machine's Ethernet address, 00:01:05:1a:e8:fc, is not among them.  If it is, delete the entry and see if that fixes the problem.

Otherwise you might consider deleting all the existing leases on the DHCP server and forcing all the machines to get new ones.  Keep the problematic machine off the network until all the other machines have finished getting addresses.  Then see what happens.

If you can query the server's ARP table, see what entries it has for the machine's Ethernet address.  Have both the DHCP server and any upstream routers been rebooted?   It's possible that there is a duplicate entry in an ARP table somewhere.  You can look at the ARP table in Linux with the command "sudo arp -vn".  Works for DDWRT routers as well; here's mine:
```

root@DD-WRT:~# arp -nv
? (192.168.10.21) at 2c:27:d7:b2:a5:38 [ether]  on br0
? (192.168.10.100) at 00:11:11:30:33:c3 [ether]  on br0
? (192.168.10.46) at f8:d1:11:19:52:66 [ether]  on br0
? (192.168.1.1) at 18:1b:eb:8e:b9:9c [ether]  on vlan2

```
The router sees four Ethernet devices, one pointing to the upstream router connected on interface vlan2, and three LAN machines on a bridge.


Hi SeijiSensei,

These devices normally operate on a network without DHCP. This is where the problem shows itself normally.

I've confirmed that there are no dupe'd arp table entries.

I only noticed the problem go away when I brought one of them up in a network with DHCP, before configuring it's static IP.

I did put the latest system on a small isolated network without DHCP to limit other network variables.

---

### Post by knoxy2 on 2015-04-23
Hi Matt,

> **matt_symes said:**
> Hi



Odd ! Is Wireshark turning on promiscuous mode on the card ?


I'm using tcpdump at the moment since the system is headless. It does not put the NIC in promiscuous mode, according to ifconfig. It seems to "capture" all the dropped packets.

I do see alot of "Unknown" packet types being broadcast in the tcpdump spew. These roughly correlate  to the amount of packet drop I'm seeing. Not sure if that's the real issue or not.

> **matt_symes said:**
> 
Does it stop dropping packets if you turn it on manually ?

```
sudo ifconfig eth0 promisc
```

You can turn promiscuous off by putting a using *-promisc*.

Are many packets still being dropped when in promiscuous mode ?

Kind regards

If I manually enable promiscuous mode, it does not affect the dropped packet rate. :(

---

### Post by knoxy2 on 2015-04-23
Despite the large amount of dropped packets, I'm not experiencing any other adverse issues on the network. I've run a bunch of tests with iperf and the throughput is ~940Mbits/sec through a Gbit switch.

Thanks everyone for your help so far.

---

### Post by matt_symes on 2015-04-23
Hi

Another stab in the dark....

Is it a DNS resolving issue ? Are you setting a DNS server in the interfaces file ? 

I assume one is being assigned by DHCP.

Kind regards

---

