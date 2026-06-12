---
title: "Planex Ug 1000t Usb Ethernet Adapter"
date: 2008-02-15
forum: Networking &amp; Wireless
---

### Post by digitalkarabao on 2008-02-15
Hello guys. The built-in Intel lan card on my laptop gave up and I had to use a USB Ethernet adapter to access the Internet. I bought a PLANEX UG 1000T USB ethernet adapter which works nicely under Windows but unfortunately I cant make it work in Ubuntu 7.10. 

lsusb shows the following lines pertaining to the device.

```
Bus 004 Device 020: ID 0b95:1780 ASIX Electronics Corp.
```

It loads the following modules when I plug it in:

```
asix                   18304  0 
usbnet                 19976  1 asix
```

However, I cannot seem to get an IP from DHCP everytime I try to connect to the Internet. ifconfig shows the following lines.

```
eth2      Link encap:Ethernet  HWaddr 00:90:CC:EF:B2:EC  
          inet6 addr: fe80::290:ccff:feef:b2ec/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:46 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:5505 (5.3 KB)

eth2:avah Link encap:Ethernet  HWaddr 00:90:CC:EF:B2:EC  
          inet addr:169.254.12.90  Bcast:169.254.255.255  Mask:255.255.0.0
```


I also tried to set it up for a static IP but it still does not connect to the Internet.

My /etc/network/interfaces contains the following:

```
auto lo
iface lo inet loopback

mapping hotplug
        script grep
        map eth2

auto eth2
iface eth2 inet dhcp
	address 192.168.1.194
	netmask 255.255.255.0
	gateway 192.168.1.1
```

Mt /etc/hosts contain these lines:

```
127.0.0.1 localhost
127.0.1.1 penguin

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

```

What am I not doing right? Is the device recognized as a LAN card by the system? Is there a way to get this device to work under Ubuntu?  Do I need to load certain modules for it to work? Driver perhaps? I am stuck guys. Suggestions are appreciated. Thanks a lot.

---

