---
title: "ULi PCI Card : internet problems"
date: 2008-07-23
forum: Networking &amp; Wireless
---

### Post by Lendon on 2008-07-23
Hi all, first post here.

As the title says I have a ULi 1689,1573 integrated ethernet card but can't access the internet. I've search the forums and followed multiple instructions trying to enable it. When through the Network settings, entered my IP address, gateway, dns servers, etc.
Still nothing. 

This is what I get with *lshw -C network*

```
 *-network               
       
description: Ethernet interface
       
product: ULi 1689,1573 integrated ethernet.
       
vendor: ALi Corporation
       
physical id: 12
       
bus info: pci@0000:00:12.0
       
logical name: eth0
       
version: 60
       
serial: 00:16:17:70:88:f4
       
width: 32 bits
       
clock: 33MHz
       
capabilities: bus_master cap_list ethernet physical
       
configuration: broadcast=yes 
driver=uli526x driverversion=0.9.3 
latency=64 
maxlatency=40 
mingnt=20 
module=uli526x 
multicast=yes
```

Any more help appreciated. I'm a total linux newbie and don't really know what else to do.

Thanks

---

### Post by I.Am.Sid on 2008-10-19
Hi Lendon, i just had the same problem.

This is what i did after alot of googling

first i killed the nm-applet process. i'm using Xbuntu so from the menu i selected System->System Monitor clicked on the Processes tab, found nm-applet right-clicked and selected kill process.

then using Synaptic i completely removed:
libnm-util0
network-manager
network-manager-gnome

then in the terminal i edited /etc/resolv.conf by
```
sudo vim /etc/resolv.conf
```
(i think ubuntu uses gedit instead of vim)

i added the line
```
nameserver 192.168.x.x
```

your resolv.conf will probably be blank

the 192.168.x.x should be the address of your router eg 192.168.1.1

next
```
sudo vim /etc/network/interfaces
```

edit to look like this

```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address		192.168.1.20
netmask		255.255.255.0
network		192.168.1.0
broadcast	192.168.1.255
gateway		192.168.1.1
```

finally at the terminal type
```
sudo /etc/init.d/networking restart
```

this should restart your network but i had to restart my pc

I tryed to set up my network for dhcp but when i did ifconfig i got this
```
eth0      Link encap:Ethernet  HWaddr 00:13:8f:1b:f6:fa  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:58 errors:0 dropped:0 overruns:0 frame:0
          TX packets:165 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:18022 (17.5 KB)  TX bytes:14903 (14.5 KB)
          Interrupt:17 Base address:0xe400 

eth0:avahi Link encap:Ethernet  HWaddr 00:13:8f:1b:f6:fa  
          inet addr:169.254.10.61  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Interrupt:17 Base address:0xe400 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:27 errors:0 dropped:0 overruns:0 frame:0
          TX packets:27 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1471 (1.4 KB)  TX bytes:1471 (1.4 KB)

```
i don't know what eth0:avahi is, anybody want to educate me?

Hope this helps

sid

---

