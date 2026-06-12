---
title: "Routing on Virtualbox Guest"
date: 2014-11-19
forum: Networking &amp; Wireless
---

### Post by Donn_Edwards on 2014-11-19
Hi, I'm a Linux Newbie, so please forgive such a simple question, but it really has me stumped. I'm running Ubuntu 14.04 LTS Server as a guest in Virtualbox. Virtualbox has two network cards set up.

The first card is a standard NAT adapter, the second is a Host-Only card, with 192.168.56.1 set as the gateway.
Everything works fine if I remove the second card and set up /etc/network/interfaces as follows:
```

# The loopback network interface
auto lo
iface lo inet loopback


# The primary network interface


auto eth0
iface eth0 inet dhcp

```
Then I can connect to the internet and stuff.

My problem is that adding the second network card causes it to be the default gateway and I can't connect to the internet. ping 8.8.8.8 doesn't work.

My /etc/network/interfaces file currently looks like this:
```

# The loopback network interface
auto lo
iface lo inet loopback


# The primary network interface


auto eth1
iface eth1 inet static
        address 192.168.56.100
        netmast 255.255.255.0
        gateway 192.168.56.1
        up route add -net 192.168.56.0 netmask 255.255.255.0 gw 192.168.56.1


auto eth0
iface eth0 inet dhcp



```
I put eth0 second in the hope that this will become the default gateway, but no go. The route settings are:
```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
default         192.168.56.1    0.0.0.0         UG    0      0        0 eth1
10.0.2.0        *               255.255.255.0   U     0      0        0 eth0
192.168.56.0    192.168.56.1    255.255.255.0   UG    0      0        0 eth1
192.168.56.0    *               255.255.255.0   U     0      0        0 eth1

```


What do I have to do to get traffic to the 192.168.56.x subnet to use eth1, but all the internet traffic must use eth0 ?

I'm sure this is easy-peasy for someone who understands Ubuntu a bit better, but I'm out of my depth here. Please help!

---

### Post by sheldon-corey on 2014-11-20
host only is  as it sounds you are visible on the host lan ONLY not to the big bad interwebs  eth1 is that host only connect 


also for full networking functionality vbox need the guest additions iso from the guest (14.04 LTS server in oyur case)  as well as the expansion pack which carries previously mentioned pkg
[https://www.virtualbox.org/wiki/Downloads](https://www.virtualbox.org/wiki/Downloads)   the second indented like   VM expansion pack  part is what oyu need...

---

### Post by Donn_Edwards on 2014-11-20
I'm sorry I forgot to mention that Guest Additions is installed and running. The 192.168.56.x adapter is the hosts only network. My problem is how to tell Ubuntu to use the *other* network card for the interwebs, i.e. the 10.0.2.x network is the internet gateway.

---

