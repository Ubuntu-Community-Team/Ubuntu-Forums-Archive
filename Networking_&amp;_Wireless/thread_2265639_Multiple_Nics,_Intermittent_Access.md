---
title: "Multiple Nics, Intermittent Access"
date: 2015-02-16
forum: Networking &amp; Wireless
---

### Post by drkilra on 2015-02-16
Hello everyone,

I have a intel chipset with 4 nic's on-board and I have been seeing some strange intermittent behaviors with our ips working. We start our system up and all of our nic cards will be up and running and leased ips will work but for some reason after a reboot or change of ip on one nic, the ip is unpingable and wont work although the card says that it is up and running. Below is my ifconfig, interface configuration and mii-tool. For some reason they will work when they want, but eth0 always seems to function. I'm so confused on why one day we can boot the server and everything is fine and the next the interface shows they are up and running but the ips are unreachable from outside, and we cant even ping out from the interfaces (eth1 eth2). And as you also see below the eth3 interface appears to not even be working unlike the rest, which was working fine before we rebooted. We are running Ubuntu 14.04.1 LTS. If anyone can help me understand what is going on I would be so grateful.. I just want to thank you in advance for your time..

[update] The eth3 cable was magicly unplugged by the host so now that is not an issue anymore.. However the ips dont work. I also will update this with a reply to more strange behavior.

```
 
***/etc/network/interfaces***

# LOCALauto lo
iface lo inet loopback
# NIC Cards WAN


## dom0 Xen Project
auto eth0
iface eth0 inet static
        address 61.98.103.106
        network 61.98.103.104
        netmask 255.255.255.248
        broadcast 61.98.103.111
        gateway 61.98.103.105
        dns-nameservers 8.8.8.8 8.8.4.4


auto eth1
iface eth1 inet static
        address 61.98.103.107
        network 61.98.103.104
        netmask 255.255.255.248
        broadcast 61.98.103.111
auto eth2
iface eth2 inet static
        address 61.98.103.108
        network 61.98.103.104
        netmask 255.255.255.248
        broadcast 61.98.103.111


auto eth3
iface eth3 inet static
        address 61.98.103.110
        network 61.98.103.104
        netmask 255.255.255.248
        broadcast 61.98.103.111



*root@web1:/home/web1# **ifconfig*** 

eth0      Link encap:Ethernet  HWaddr 00:1e:67:9a:2c:54          
          inet addr:61.98.103.106  Bcast:61.98.103.111  Mask:255.255.255.248
          inet6 addr: fe80::21e:67ff:fe9a:2c54/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:947707 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2386944 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:159043316 (159.0 MB)  TX bytes:3112189669 (3.1 GB)
          Memory:d0960000-d0980000


eth1      Link encap:Ethernet  HWaddr 00:1e:67:9a:2c:55
          inet addr:61.98.103.107  Bcast:61.98.103.111  Mask:255.255.255.248
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:267194 errors:0 dropped:0 overruns:0 frame:0
          TX packets:111 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:22979084 (22.9 MB)  TX bytes:7692 (7.6 KB)
          Memory:d0940000-d0960000


eth2      Link encap:Ethernet  HWaddr 00:1e:67:9a:2c:56
          inet addr:61.98.103.108  Bcast:61.98.103.111  Mask:255.255.255.248
          inet6 addr: fe80::21e:67ff:fe9a:2c56/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:17595 errors:0 dropped:0 overruns:0 frame:0
          TX packets:237 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:1676970 (1.6 MB)  TX bytes:29619 (29.6 KB)
          Memory:d0920000-d0940000


eth3      Link encap:Ethernet  HWaddr 00:1e:67:9a:2c:57
          inet addr:61.98.103.110  Bcast:61.98.103.111  Mask:255.255.255.248
          inet6 addr: fe80::21e:67ff:fe9a:2c57/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:5 errors:0 dropped:0 overruns:0 frame:0
          TX packets:24 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:620 (620.0 B)  TX bytes:3985 (3.9 KB)
          Memory:d0900000-d0920000


*root@web1:/home/web1# **mii-tool***
eth0: negotiated 1000baseT-FD flow-control, link ok
eth1: negotiated 1000baseT-FD flow-control, link ok
eth2: negotiated 1000baseT-FD flow-control, link ok
eth3: no link



```

---

### Post by drkilra on 2015-02-18
Okay guys so things have gotten really strange. Ips are all working again.. If I run mii-tool which i know is depreciated now, I get this:

eth0: negotiated 1000baseT-FD flow-control, link ok
eth1: negotiated 1000baseT-FD flow-control, link ok
eth2: no link
eth3: no link

Now the strange thing is, eth2 & 3 appear to be up because I can now externally ping those addresses as set in the /etc/network/interface above and an nmap scan proves that it is infact my server the ip rests on. If i ifdown the eth2, I am no longer able to externally ping.. Rebooting the system still shows the link as dead. So I started using ethool and that also shows theres no link. I'm totally baffled at this point! WTF? Why do theses say no link yet still work?

So anyway I dig deeper and see the TX mode is OFF on eth0 & eth1 which work fine but TX is ON with eth2 & eth3, so i try to turn TX OFF and restart the interfaces and TX remains on anyway, with no link being reported in mii-tool or ethtool. I just dont understand, is it my drivers, is it the speed not being supported? they are 1Gb Ethernet ports.. Is it a bug in ubuntu?

```

ethtool -a eth0
Pause parameters for eth0:
Autonegotiate:  on
RX:             on
TX:             off


ethtool -a eth2
Pause parameters for eth2:
Autonegotiate:  on
RX:             on
TX:             on

```
I need some kinda help before I go bonkers..

---

### Post by SeijiSensei on 2015-02-18
Having all the NICs on the same network subnet can cause routing problems of various kinds.  Usually in these situations people use virtual interfaces (eth0:0, eth0:1, etc.) on a single interface and assign each of them an IP.  If you want to use them all for bandwidth purposes, you can use "[bonding]("https://help.ubuntu.com/community/UbuntuBonding")" to create a single device from the four and assign that the addresses.

Try replacing /etc/network/interfaces with this:
```

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
        address 61.98.103.106
        network 61.98.103.104
        netmask 255.255.255.248
        broadcast 61.98.103.111
        gateway 61.98.103.105
        dns-nameservers 8.8.8.8 8.8.4.4


auto eth0:1
iface eth0:1 inet static
        address 61.98.103.107
        network 61.98.103.104
        netmask 255.255.255.248
        broadcast 61.98.103.111

auto eth0:2
iface eth0:2 inet static
        address 61.98.103.108
        network 61.98.103.104
        netmask 255.255.255.248
        broadcast 61.98.103.111


auto eth0:3
iface eth0:3 inet static
        address 61.98.103.110
        network 61.98.103.104
        netmask 255.255.255.248
        broadcast 61.98.103.111


```

After rebooting, only one card should be active, eth0, but it should answer for all four addresses.  Other than the lower bandwidth of a single adapter, does this work as you expect?

---

### Post by drkilra on 2015-02-18
SeijiSensei,

Thank you for your reply I really do appreciate it. My initial goal was to have all four interfaces active so that I could route the traffic to particular instances on xen via iptables. I did setup xenbridge at one point which worked great but I wasnt sure if my iptables would work correctly had I not had everything on dom0. So I then tried setting up sub-interfaces but had all kinds of weird intermittent problems with the ips being pingable and then suddenly not for a few days at a time, although I think that was between two interface cards like eth0:1 eth0:2 eth1:1 eth1:2, but I cant recall right now because I cleared out the hashed interface settings. 

So I have reconfigured and rebooted and it does appears some ips work, and some do not as well as a strange report from mii-tools

```


mii-tool
eth0: negotiated 1000baseT-FD flow-control, link ok
eth1: negotiated 1000baseT-FD flow-control, link ok
eth2: no link
eth3: no link

```

I dont know how its saying eth1 is there, yea its plugged in but its not in the interface config

```


auto eth0
iface eth0 inet static
        address 61.98.103.106
        network 61.98.103.104
        netmask 255.255.255.248
        broadcast 61.98.103.111
        gateway 61.98.103.105
        dns-nameservers 8.8.8.8 8.8.4.4


auto eth0:1
iface eth0:1 inet static
        address 61.98.103.107
        network 61.98.103.104
        netmask 255.255.255.248
        broadcast 61.98.103.111


auto eth0:2
iface eth0:2 inet static
        address 61.98.103.108
        network 61.98.103.104
        netmask 255.255.255.248
        broadcast 61.98.103.111


auto eth0:3
iface eth0:3 inet static
        address 61.98.103.109
        network 61.98.103.104
        netmask 255.255.255.248
        broadcast 61.98.103.111


auto eth0:4
iface eth0:4 inet static
        address 61.98.103.110
        network 61.98.103.104
        netmask 255.255.255.248
        broadcast 61.98.103.111

```


So after doing as you said surprisingly all ip's EXCEPT .107 were pingable.. I'm not sure if its because the subinterface needs to start with 0:0 or 0:2 *(edit: that was not the issue, i started from 0:0 and up and the problem persisted)* or if its that weird intermittent problem I was telling you about . I can tell you we do pay for these 6 ips and they arent in use by anyone else so I can't think of any other reason why this is happening.. Before I changed the interface config 107 was pingable now its not. Very strange.

I will read further into this bonding you mentioned, this was just a quick reply to you to let you know the results..

---

