---
title: "my system started sending bootp/dhcp requests"
date: 2019-07-11
forum: Networking &amp; Wireless
---

### Post by Skaperen on 2019-07-11
my system started sending bootp/dhcp requests.  it is sending them over the wifi connection.  the wifi and internet are still up and working.  anyone know why this is happening?  it is sending them out with my VPN IP address and my wifi MAC address.

---

### Post by SeijiSensei on 2019-07-12
By default Ubuntu uses DHCP unless you specify a static configuration. So I'm not sure why you find this behavior surprising. The default for dhclient is to send requests on all interfaces, so that would include your VPN. From the [man page for dhclient]("https://linux.die.net/man/8/dhclient"):

> On startup, dhclient reads the dhclient.conf for configuration instructions.  It then gets a list of all the network interfaces that are configured in the current system.  For each interface, it attempts to configure the interface using the DHCP protocol.

I believe dhclient checks in periodically with the DHCP server based on the expiration time of the lease. That's determined by the server settings.

---

### Post by Skaperen on 2019-07-14
i have been seeing packets like this flying over my host network.  192.0.2.2 is the local end of a VPN with the remote end on my server reached over the network.  these do not happen all the time but at times they do get started.  10.2.1.8 is not routed anywhere on my laptop so i suspect it goes out over the wifi connection which has an address of 172.31.51.36 (see the reply address). the network and the VPN had been working fine and are still working.  this tcpdump was filtered just to show these packets only.  the network is very busy with videos going all the time.  the MAC address is my wifi.

the VPN is based on OpenVPN.  the server is running Ubuntu 16.04 and my laptop is running Xubuntu 18.04.

anyone know why these would be sent and why they don't get answered for a period as long as at least 3.5 hours?  how can i find out what process is sending them and which would get the reply?  where is it getting 10.2.1.8 and what could it be?  could the DHCP daemon be confused?  the command "[FONT=courier new]netstat -anup[/FONT]" shows nothing related.

this is just a few at the end:

```
...
22:39:52.600670 IP 192.0.2.2.68 > 10.2.1.8.67: BOOTP/DHCP, Request from f8:16:54:2c:d7:06, length 300
22:40:13.892667 IP 192.0.2.2.68 > 10.2.1.8.67: BOOTP/DHCP, Request from f8:16:54:2c:d7:06, length 300
22:40:24.801362 IP 192.0.2.2.68 > 10.2.1.8.67: BOOTP/DHCP, Request from f8:16:54:2c:d7:06, length 300
22:40:34.201088 IP 192.0.2.2.68 > 10.2.1.8.67: BOOTP/DHCP, Request from f8:16:54:2c:d7:06, length 300
22:40:44.336669 IP 192.0.2.2.68 > 10.2.1.8.67: BOOTP/DHCP, Request from f8:16:54:2c:d7:06, length 300
22:40:56.793656 IP 192.0.2.2.68 > 10.2.1.8.67: BOOTP/DHCP, Request from f8:16:54:2c:d7:06, length 300
22:41:11.633581 IP 10.2.1.8.67 > 172.31.51.36.68: BOOTP/DHCP, Reply, length 319

```

this is earlier showing the previous run's end and the start of this run:

```
...
15:39:15.604642 IP 192.0.2.2.68 > 10.2.1.8.67: BOOTP/DHCP, Request from f8:16:54:2c:d7:06, length 300
15:39:26.416834 IP 192.0.2.2.68 > 10.2.1.8.67: BOOTP/DHCP, Request from f8:16:54:2c:d7:06, length 300
15:39:42.905342 IP 192.0.2.2.68 > 10.2.1.8.67: BOOTP/DHCP, Request from f8:16:54:2c:d7:06, length 300
15:40:02.368153 IP 192.0.2.2.68 > 10.2.1.8.67: BOOTP/DHCP, Request from f8:16:54:2c:d7:06, length 300
15:40:23.835990 IP 192.0.2.2.68 > 10.2.1.8.67: BOOTP/DHCP, Request from f8:16:54:2c:d7:06, length 300
15:40:38.372986 IP 192.0.2.2.68 > 10.2.1.8.67: BOOTP/DHCP, Request from f8:16:54:2c:d7:06, length 300
15:40:58.812035 IP 10.2.1.8.67 > 172.31.51.36.68: BOOTP/DHCP, Reply, length 319
19:07:33.803373 IP 192.0.2.2.68 > 10.2.1.8.67: BOOTP/DHCP, Request from f8:16:54:2c:d7:06, length 300
19:07:36.144789 IP 192.0.2.2.68 > 10.2.1.8.67: BOOTP/DHCP, Request from f8:16:54:2c:d7:06, length 300
19:07:44.996807 IP 192.0.2.2.68 > 10.2.1.8.67: BOOTP/DHCP, Request from f8:16:54:2c:d7:06, length 300
19:07:56.596786 IP 192.0.2.2.68 > 10.2.1.8.67: BOOTP/DHCP, Request from f8:16:54:2c:d7:06, length 300
...
```

here is my VPN and wifi from ifconfig:

```

tun2kepler: flags=4305<UP,POINTOPOINT,RUNNING,NOARP,MULTICAST>  mtu 1360
        inet 192.0.2.2  netmask 255.255.255.255  destination 192.0.2.1
        inet6 fdff::2  prefixlen 64  scopeid 0x0<global>
        inet6 fe80::adcb:d28a:9e66:3010  prefixlen 64  scopeid 0x20<link>
        unspec 00-00-00-00-00-00-00-00-00-00-00-00-00-00-00-00  txqueuelen 100  (UNSPEC)
        RX packets 34832270  bytes 46953650847 (46.9 GB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 15235447  bytes 954461701 (954.4 MB)
        TX errors 0  dropped 4801 overruns 0  carrier 0  collisions 0

wlp4s0: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 172.31.51.36  netmask 255.255.0.0  broadcast 172.31.255.255
        inet6 fe80::4b89:2f75:2203:6fa0  prefixlen 64  scopeid 0x20<link>
        ether f8:16:54:2c:d7:06  txqueuelen 1000  (Ethernet)
        RX packets 35011817  bytes 50193810975 (50.1 GB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 15255012  bytes 2644880600 (2.6 GB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

```

---

### Post by Skaperen on 2019-07-14
i posted a new thread with more details ... because i forgot that i posted this one ... and wondering why it is coming from my VPN.

---

### Post by wildmanne39 on 2019-07-14
Threads Merged!

---

### Post by Skaperen on 2019-07-14
i did "tcpdump -lni tun2kepler" and filtered out most of the traffic and i can see these BOOTP/DHCP packets really are going over the VPN.  the VPN is statically configured.  i still don't know what 10.2.1.8 is or where it got that IP address.

---

### Post by Skaperen on 2019-07-14
my routing table:
```

default via 192.0.2.1 dev tun2kepler metric 6 
default via 172.31.0.1 dev wlp4s0 metric 106 
default via 172.31.0.1 dev wlp4s0 proto dhcp metric 600 
8.8.4.4 via 172.31.0.1 dev wlp4s0 
<<an instance at AWS>> via 172.31.0.1 dev wlp4s0 
74.125.0.0/16 via 172.31.0.1 dev wlp4s0 
108.177.0.0/17 via 172.31.0.1 dev wlp4s0 
151.101.0.0/16 via 172.31.0.1 dev wlp4s0 
169.254.0.0/16 dev wlp4s0 scope link metric 1000 
172.31.0.0/16 dev wlp4s0 proto kernel scope link src 172.31.51.36 metric 600 
172.217.0.0/16 via 172.31.0.1 dev wlp4s0 
173.194.0.0/16 via 172.31.0.1 dev wlp4s0 
<<server IP>> via 172.31.0.1 dev wlp4s0 
192.0.2.1 dev tun2kepler proto kernel scope link src 192.0.2.2 

```
the first default would send 10.2.1.8 over the VPN (tun2kepler).  it eventually got an answer there.

---

