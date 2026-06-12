---
title: "How to setup static IP on Ubuntu 14.04 desktop"
date: 2015-05-27
forum: Networking &amp; Wireless
---

### Post by satimis on 2015-05-27
Hi all,

I encountered problem on setting up static IP without via router

/etc/network/interfaces```

# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
	address xxx.xxx.xx1 #static_IP
	nameserver xxx.xxx.xxx.xx1
	nameserver xxx.xxx.xxx.xx2
	netmask 255.255.255.xxx
	broadcast xxx.xxx.xxx.xx3
	gateway xxx.xxx.xxx.xx2

```

Above setting worked for me previously on another box running Ubuntu 12.04

I can ping the static_IP and gateway.

$ ifconfig -a | grep eth```

eth0      Link encap:Ethernet  HWaddr f0:79:59:65:2f:bb  

```

$ sudo lshw -class network```

  *-network               
       description: Ethernet interface
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 09
       serial: f0:79:59:65:2f:bb
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=rtl8168f-1_0.0.5 06/18/12 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
       resources: irq:80 ioport:d000(size=256) memory:fa104000-fa104fff memory:fa100000-fa103fff

```

Please advise.  Thanks

Regards
satimis

---

### Post by Bucky Ball on 2015-05-27
You don't need to do anything to set up a static IP in the router. Set the router to serve IPs via DHCP in a given range, say 192.168.0.100-110. Do NOT enable static IPs function for your router. Just leave it set to serve via DHCP in your chosen range (DHCP enabled). Set your static IP locally (on your device) outside that range (for instance, 192.168.0.111) via Network Manager.

Click on the network icon> Edit> highlight your wireless or wired connection and 'Edit'> on the IPv4 tab, set to 'Manual'> input your static IP, netmask IP (genrally 255.255.255.0) and gateway, or router, IP. Next, add the DNS server IPs which will be available from your ISP.

A note: Set the static up in Network Manager rather than tweaking the /etc/network/interfaces file. Be aware that tweaking that will NOT tweak Network Manager and vice versa. They are not one and the same and not 'interactive'. If you are getting a good connection already, all is good with /etc/network/interfaces, leave that file alone and set up the static in Network Manager. Good luck and let us know how it goes.

---

### Post by satimis on 2015-05-27
Hi,

Thanks for your advice.

> **Bucky Ball said:**
> You don't need to do anything to set up a static IP in the router. Set the router to serve IPs via DHCP in a given range, say 192.168.0.100-110. Do NOT enable static IPs function for your router. Just leave it set to serve via DHCP in your chosen range (DHCP enabled). Set your static IP locally (on your device) outside that range (for instance, 192.168.0.111) via Network Manager.

I have no problem to set Static_IP on router.

> 
Click on the network icon> Edit> highlight your wireless or wired connection and 'Edit'> on the IPv4 tab, set to 'Manual'> input your static IP, netmask IP (genrally 255.255.255.0) and gateway, or router, IP. Next, add the DNS server IPs which will be available from your ISP.

A note: Set the static up in Network Manager rather than tweaking the /etc/network/interfaces file. Be aware that tweaking that will NOT tweak Network Manager and vice versa. They are not one and the same and not 'interactive'. If you are getting a good connection already, all is good with /etc/network/interfaces, leave that file alone and set up the static in Network Manager. Good luck and let us know how it goes.
This is NOT my first time to setup Static IP on network with direct connection without going through the router.  Previously all the work was done by me on editing /etc/network/interfaces.  I don't understand why I fail this time?

Whether you meant;
System Settings - Network (icon) -> high-light Wired```

Wired
Unmanaged - 100 Mb/s
Hardware Address F0:79:59:65:2F:BB

```

click [+] tab```

Select the interface to use the new service
Interface [VPN]

```
No other options.   Whether click [Create] to continue?

In case failure how to remove/delete all data input?

Thanks

Regards
satimis

---

### Post by satimis on 2015-05-27
Hi all,

I found the cause of problem.  The network is connected but unable to ping domain.  Ping IP address without problem.

$ ping google.com
unknown host google.com

$ ping 74.125.203.139```

64 bytes from 74.125.203.139: icmp_seq=6 ttl=47 time=27.5ms
....

```

$ ping 68.142.255.16```

64 bytes from 68.142.255.16: icmp_seq=1 ttl=57 time=204 ms
...

```

$ ping yahoo.com
unknown host yahoo.com

IP addresses of nameserver are correct.  I have double checked with ISP.

Additionally I have tried adding them to /etc/resolv.cfg without result.

/etc/network/interfaces```

# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
address 61.xxx.xxx.xx1
nameserver 203.xxx.xxx.xxx
nameserver 203.xxx.xxx.xxx
netmask 255.255.255.252
gateway 61.xxx.xxx.xx2

```

Please help.  Thanks

Remark:
The network is without problem via router

Regards
satimis

---

### Post by chili555 on 2015-05-27
I suggest:```
# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
address 61.xxx.xxx.xx1
[COLOR="#FF0000"]dns-[/COLOR]nameserver[COLOR="#FF0000"]s[/COLOR] 203.xxx.xxx.xxx 203.xxx.xxx.xxx
netmask 255.255.255[COLOR="#FF0000"].0[/COLOR]
gateway 61.xxx.xxx.xx2
```Restart the inteface so that the system re-reads the file:```
sudo ifdown eth0 && sudo ifup -v eth0
```And test:```
ping -c3 www.ubuntu.com
```

---

### Post by satimis on 2015-05-27
> **chili555 said:**
> I suggest:```
# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
address 61.xxx.xxx.xx1
[COLOR="#FF0000"]dns-[/COLOR]nameserver[COLOR="#FF0000"]s[/COLOR] 203.xxx.xxx.xxx 203.xxx.xxx.xxx
netmask 255.255.255[COLOR="#FF0000"].0[/COLOR]
gateway 61.xxx.xxx.xx2
```Restart the inteface so that the system re-reads the file:```
sudo ifdown eth0 && sudo ifup -v eth0
```And test:```
ping -c3 www.ubuntu.com
```
Hi,

Lot of thanks for your advice which works here, saving me hours of work in googling around.

I can't resolve;
1) netmask 255.255.255.0
255.255.255.252 was provided by my ISP

2) 
dns-nameservers 203.xxx.xxx.xxx 203.xxx.xxx.xxx

Why have to adding dns in front?

Please advise.  Thanks

Regards
satimis

---

### Post by chili555 on 2015-05-27
> 255.255.255.252 was provided by my ISPBy all means, use it.> 2)
dns-nameservers 203.xxx.xxx.xxx 203.xxx.xxx.xxx

Why have to adding dns in front?

Please advise. ThanksBecause that's the term that the system understands. You can't just use 'nameserver' interchangeably with 'dns-nameservers.' Linux knows what dns-nameservers means. It does not know what nameserver means.

---

### Post by satimis on 2015-05-27
> **chili555 said:**
> By all means, use it.Because that's the term that the system understands. You can't just use 'nameserver' interchangeably with 'dns-nameservers.' Linux knows what dns-nameservers means. It does not know what nameserver means.
Hi,

Advice noted.  Thanks

Regards
satimis

---

