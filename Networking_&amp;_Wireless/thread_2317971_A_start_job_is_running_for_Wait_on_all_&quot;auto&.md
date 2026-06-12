---
title: "A start job is running for Wait on all &quot;auto&quot;"
date: 2016-03-21
forum: Networking &amp; Wireless
---

### Post by ryan209 on 2016-03-21
just joined the ubuntu server world, im trying to set my server to a static ip.  When i restart my server i get the error
```
[COLOR=#000000][FONT=Ubuntu Mono]A start job is running for Wait on all "auto" /etc/network/interfaces to be up for network-online.target[/FONT][/COLOR]
```

my /etc/network/interfaces looks like:(the non commented out lines)
```
source /etc/network interfaces.d/*

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 192.168.1.66
netmask 255.255.255.0
network 192.168.1.1
dns-nameserver 192.168.1.1
```

here is a screenshot of the info i grabbed: [http://i.imgur.com/BsmOyp5.jpg](http://i.imgur.com/BsmOyp5.jpg)

---

### Post by papibe on 2016-03-21
Hi ryan209.

I believe you're following some tutorial to set an static IP?

Most single network cards will be name eth0, thus the instructions to use 'eth0' work well... in general.

From your 'ifconfig' command I see that the network card is not eth0, but **enp0s7**. Try using that on your 'interfaces' file and see how it goes.

Also, network should be 192.168.1.0

In order for the 'dns-nameservers' line to work make sure there is a machine in your network with that address, and that it is serving DNS.

Does that help? Let us know how that goes, and if you need more help.
Regards.

---

