---
title: "Problem on setting Static IP address"
date: 2016-02-29
forum: Networking &amp; Wireless
---

### Post by satimis on 2016-02-29
Hi all,

Ubuntu 14.04

Previously before adding a router following entry on
/etc/network/interfaces worked to connect Internet without problem;
```

auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
        address         aaa.aaa.aaa.aaa
        dns-nameservers bbb.bbb.bbb.bbb ccc.ccc.ccc.ccc
        netmask         255.255.255.0
        broadcast       aaa.aaa.aaa.15
        gateway         aaa.aaa.aaa.13

# add bridge ports
auto br0
iface br0 inet static
        address         192.168.0.100
        dns-nameservers bbb.bbb.bbb.bbb ccc.ccc.ccc.ccc
        network         192.168.0.0
        netmask         255.255.255.0
        broadcast       192.168.0.255
        gateway         192.168.0.1
        bridge_ports    eth0
        bridge_fd       9
        bridge_hello    2
        bridge_maxage   12
        bridge_stop     off

```
The addresses "aaa.aaa.aaa.aaa bbb.bbb.bbb.bbb ccc.ccc.ccc.ccc 255.255.255.0 aaa.aaa.aaa.15 aaa.aaa.aaa.13" all were provided by ISP.

I haven't used the captioned settings at least more than ONE year after adding a router.

I just tested it lately and found it didn't work.  Please help.

Thanks in advance.

Regards
satimis

---

### Post by Bucky Ball on 2016-02-29
Not sure what version you were using previously, but if you were talking about a desktop version, you leave the /interfaces file alone. Messing with that messes with Network Manager and you get problems. Think you need to tweak one or the other. 

Your /interfaces file should look like:
```

# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback
```

... and then click the network icon> Edit> choose connection> IPv4 tab> set Auto to Manual and set the static IP address in there. Once you're done, reboot and check you are using the static.

Looks like you are going for something somewhat more exotic where you need to tweak /interfaces, though, so maybe your experiments with that file in combination with Network Manager are causing a conflict.

* Ah, they were provided by ISP! You need to replace the aaaa etc. with the correct details for your set up.

If you just got the router, that is a different story altogether so best to stop there for a moment and let us know.

---

### Post by satimis on 2016-02-29
> **Bucky Ball said:**
> Not sure what version you were using previously, but if you were talking about a desktop version, you leave the /interfaces file alone. Messing with that messes with Network Manager and you get problems. Think you need to tweak one or the other. 

Your /interfaces file should look like:
```

# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback
```

... and then click the network icon> Edit> choose connection> IPv4 tab> set Auto to Manual and set the static IP address in there. Once you're done, reboot and check you are using the static.

Looks like you are going for something somewhat more exotic where you need to tweak /interfaces, though, so maybe your experiments with that file in combination with Network Manager are causing a conflict.

* Ah, they were provided by ISP! You need to replace the aaaa etc. with the correct details for your set up.

If you just got the router, that is a different story altogether so best to stop there for a moment and let us know.
Hi,

Thanks for your advice.

Whether you meant the network icon on right top bar
right click it
-> Edit Connection > Add
Choose a Connection Type
Under Hardware```

DSL
Ethernet (default)
infiniBand
etc.

```
Which of above shall I choose before clicking [Create]

Currently I'm subscribing PTTC fibre broadband 100Mbps upload/download, static IP.  The last section is an Ethernet cable which I use to plugin to the router or to the network card of PC.  

The contract shall end at early April, 2016.  I shall switch my subscription to another ISP of PTTH 1000Mbps fibre broadband upload/download, dynamic IP.

The settings mentioned above worked seamlessly for me.  I just edited /etc/network/interfaces and rebooted the PC.  Then network can be connected and Internet can be browsed without problem.  I don't know why it couldn't work after 1 year.

Regards
satimis

---

### Post by satimis on 2016-02-29
Hi all,

Problem solved as follow;

Contacted ISP.  I was informed that DNS addresses have been changed.

After changing DNS to new addresses and deleting bridge network settings rebooted PC.  Now Internet can be connected.

/etc/network/interfaces```

# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
        address         aaa.aaa.aaa.aaa
        dns-nameservers bbb.bbb.bbb.bbb ccc.ccc.ccc.ccc (new)
        netmask         255.255.255.0
        broadcast       aaa.aaa.aaa.15
        gateway         aaa.aaa.aaa.13

```

Delete following setting```

# add bridge ports
auto br0
iface br0 inet static
      address         192.168.0.200
      network         192.168.0.0
      netmask         255.255.255.0
      broadcast       192.168.0.255
      gateway         192.168.0.1
      bridge_ports    eth0
      bridge_fd       9
      bridge_hello    2
      bridge_maxage   12
      bridge_stop     off

```

Before I have HAProxy installed.

Regards
satimis

---

