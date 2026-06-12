---
title: "two netword configuration in the same ethernet"
date: 2008-11-11
forum: Networking &amp; Wireless
---

### Post by Claus7 on 2008-11-11
Hello,

a friend of mine has kubuntu and he wants to configure his network settings so as to have different addresses in his work and his house, yet on the same ethernet. Is this possible without having to modify the network settings every time he switches places?

Regards!

---

### Post by superprash2003 on 2008-11-11
which version of ubuntu is he running?

---

### Post by netztier on 2008-11-11
> **Claus7 said:**
> Hello,

a friend of mine has kubuntu and he wants to configure his network settings so as to have different addresses in his work and his house, yet on the same ethernet. Is this possible without having to modify the network settings every time he switches places?

Regards!

Well, having a proper DHCP setup both at home and at work would help a lot. DHCP servers can be configured to reserve a certain IP address for a given MAC address, so that his device always gets the same address when in the office, and the same address when at home.

Normally, every broadband router has an integrated - although basic - DHCP server, an most of them have the possibility to do "address reservations", so there (probably) is no need to run a separate Server for DHCP.

regards

Marc

---

### Post by netztier on 2008-11-11
[Double post removed. Delay/reload problem]

---

### Post by Iowan on 2008-11-11
dhclient.conf has a setting that *looks* like it should provide such an option, but I haven't researched it enough to say for sure.

---

### Post by puppywhacker on 2008-11-11
Hi,

you can make alias'es out of your interface so you can assign 2 ip addresses to the same physical interface. In my sample below I configured a virtual eth2:0 to serve my internal network.

Just beware that in the routing table the default gateway to connect to the internet may cause problems.

```

/etc/network/interfaces
auto lo eth1 eth2  eth2:0

iface eth2 inet dhcp

iface eth2:0 inet static
        address 192.168.1.2
        netmask 255.255.255.0

```

```
eth2      Link encap:Ethernet  HWaddr 00:11:24:A1:79:C5  
          inet addr:88.193.123.21  Bcast:88.193.12.255  Mask:255.255.240.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1

eth2:0    Link encap:Ethernet  HWaddr 00:11:24:A1:79:C5  
          inet addr:192.168.1.2  Bcast:192.168.1.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1

```

---

### Post by Claus7 on 2008-11-12
Hello,

thank you all for your answers.

*puppywhacker * I have to say that your configuration is exactly what we are having here. 
If I understand correctly from what you provide, you have one configuration with dhcp and one with a static IP address, which is our case. 

I can go inside the file you provide and add a line with the configuration that is missing (here the place at home which has the dhcp).

What I didn't understand is the alias'es that you mentioned. Do I have to make them in bash. And if so, how I will be able to discern between the two, depending on the place my friend is?

Regards!

---

### Post by puppywhacker on 2008-11-12
hi,

The interfaces file though is the permanent one. From a commandline you could add the alias like this:

ifconfig eth0:0 add 192.168.1.2

you don't have to make a distinction between on which network you are. Both will be active. In the static location you would still do a DHCP that would fail, but that's OK since you still have your static config.

In the dhcp location you would have an ip-address and default route and dns resolvers set up by the dhcp server. Effectively overwriting the static settings.

It's not a perfect foolproof solution, since it depends a bit on the startup order. for instance waiting for the dhcp timeout may take half a minute extra boot-time, and the dns /etc/resolv.conf might be overwritten by the dhcp server everytime.

The more perfect situation would be that you have a dhcp server on both networks providing the settings.

goodluck

---

### Post by Claus7 on 2008-11-15
Hello,

I have found out also this link:
[http://www.ubuntugeek.com/ubuntu-networking-configuration-using-command-line.html](http://www.ubuntugeek.com/ubuntu-networking-configuration-using-command-line.html)

Thanks for your response once again. He has to use it so as to be able to comfirm exactly what he did.

Regards!

---

