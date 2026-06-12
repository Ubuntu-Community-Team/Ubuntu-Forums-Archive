---
title: "Cannot get eth1 to work."
date: 2014-10-31
forum: Networking &amp; Wireless
---

### Post by shadragon on 2014-10-31
Morning, 

I&#7743; setting up a 14.04 server with KDE on ESXi. I was able to config eth0 through the Ubuntu server set-up and it works fine. However, when I added eth1 manually by editing the INTERFACES file, I lost all network access. I have two NIC&#347; defined in VMWare. 

I need this server to access two networks. Our corperate network eth0 (and gateway to the Internet) is for faculty and is on one subnet. eth1 will go to students on the guest sub-net. 

The INTERFACE file is below (I have edited the sub-nets to remove specifics.) Where did I screw up?

# The primary network interface - (This works without eth1)
auto eth0
iface eth0 inet static
    address 192.168.xx.28
    netmask 255.255.255.0
    network 192.168.xx.0
    broadcast 192.168.xx.255
    gateway 192.168.xx.1
    # dns-* options are implemented by the resolvconf package, if installed
    dns-nameservers 192.168.xx.9 192.168.xx.20
    dns-search (DOMAIN)
    
# The secondary network interface
auto eth1
iface eth1 inet static
    address 192.168.yy.28
    netmask 255.255.254.0
    network 192.168.yy.0
    gateway 192.168.yy.1
    broadcast 192.168.yy.255
    # dns-* options are implemented by the resolvconf package, if installed
    dns-nameservers 192.168.yy.193 192.168.yy.3
    dns-search (DOMAIN)


I thought the second gateway may have been the issue, but deleting it made no difference. 

All help appreciatted. Thanks in advance.

---

### Post by The Cog on 2014-10-31
There is no point in hiding the IP addresses - they are in private address space and not directly reachable from the internet anyway.

I think you should try removing the eth1 nameservers as well as the default gateway. It may be name lookups that are now failing.

Are the students all on 192.168.yy or are there other subnets beyond that one? If there are other subnets then you need to add specific routes for them, pointing to the router on yy that can forward the traffic for you.

---

### Post by SeijiSensei on 2014-10-31
Remember you need to enable packet forwarding by uncommenting the line "net.ipv4.ip_forward=1" in /etc/sysctl.conf and rebooting.  

For the secondary network on eth1, you should specify only the address, netmask, and broadcast address.  Linux will figure out routing from there.  There should be only one default gateway, presumably upstream from the eth0 interface.

Also are you sure this is the correct mask for eth1: "netmask 255.255.254.0"?  That generates a /23 with 510 available addresses.  Is that what you want, or should there be another 255 in the third octet?

---

### Post by shadragon on 2014-10-31
Thanks for the fast replies. 

I found eth0 was actually being seen as eth1 in the system so I amended the INTERFACES to reflect that. 

The Cog - by school IT policy I cannot post internal details of our networks publically so I&#7743; forced to mask detail. It&#347; a PIA for me as well. :)

SeijiSensei - I uncommented the "net.ipv4.ip_forward=1" line and rebooted. I can use Internet on this server now with the below settings. I can ping 192.168.xx.28 from my workstation, but not ping 192.168.yy.28      This is my INTERFACE now:

# The primary network interface
auto eth1
iface eth1 inet static
    address 192.168.xx.28
    netmask 255.255.255.0
    network 192.168.xx.0
    broadcast 192.168.xx.255
    gateway 192.168.xx.1
    # dns-* options are implemented by the resolvconf package, if installed
    dns-nameservers 192.168.xx.9 192.168.xx.20
    dns-search (DOMAIN)
    
#The secondary network interface
auto eth0
iface eth0 inet static
    address 192.168.yy.28
    netmask 255.255.254.0      #This netmask is correct. We have 300+ student PC&#347; on this network. 
    broadcast 192.168.yy.255

So eth1 is working fine, but eth2 is unresponsive and does not show on ifconfig. Only eth1 is shown. More info. 

```
route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.xx.1    0.0.0.0         UG    0      0        0 eth1
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth1
192.168.xx.0    0.0.0.0         255.255.255.0   U     0      0        0 eth1
```


```
ifconfig
eth1      Link encap:Ethernet  HWaddr 00:50:46:ae:44:57  
          inet addr:192.168.xx.28  Bcast:192.168.xx.255  Mask:255.255.255.0
          inet6 addr: fe80::250:56ff:fe4e:74a7/64 Scope:Link                    
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1                    
          RX packets:11130 errors:0 dropped:3 overruns:0 frame:0                
          TX packets:655 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1286024 (1.2 MB)  TX bytes:161180 (161.1 KB)
```

lo is there too, but I left it out.

---

### Post by shadragon on 2014-10-31
Here&#347; the ip link result as well. 

```
ip link
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN mode DEFAULT group default 
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
2: eth0: <BROADCAST,MULTICAST> mtu 1500 qdisc noop state DOWN mode DEFAULT group default qlen 1000
    link/ether 00:50:57:ae:63:18 brd ff:ff:ff:ff:ff:ff
3: eth1: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast state UP mode DEFAULT group default qlen 1000
    link/ether 00:50:57:ae:75:a7 brd ff:ff:ff:ff:ff:ff
```

The virtual LAN interfaces (For eth0 and 1) are set to both be E1000 type in the VM settings.

---

### Post by The Cog on 2014-11-03
In "ip link", eth0 is not showing as LOWER_UP. Check the cable. Try plugging the cable from eth1 in there for a short while to see if it comes up then - to decide whether it's the cable of the ethernet card that's the problem.

---

### Post by shadragon on 2014-11-05
> **The Cog said:**
> In "ip link", eth0 is not showing as LOWER_UP. Check the cable. Try plugging the cable from eth1 in there for a short while to see if it comes up then - to decide whether it's the cable of the ethernet card that's the problem.

It was neither. The switch port I was plugged into had not been set up for the Guest VLan. Once that was configured all was well and pings rang out into the world. 

Thanks.

---

