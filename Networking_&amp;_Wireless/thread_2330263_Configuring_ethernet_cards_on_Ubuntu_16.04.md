---
title: "Configuring ethernet cards on Ubuntu 16.04"
date: 2016-07-09
forum: Networking &amp; Wireless
---

### Post by Raging_Cascadoo on 2016-07-09
Hi, I just recently added two realtec ethernet nics into my home server for the purpose of creating a pfsense VM to act as my router. I have a total of three ethernet nics, including the onboard nic. I am having difficulties in getting the two additional nics to work properly.

I actually reinstalled Ubuntu server from scratch using the onboard nic (enp1s0) as the primary for the install. After installation i configured enp1s as a static Ip address through /etc/network/interfaces and this worked fine. 

I then installed a gui (sudo apt-get install --no-install-recommends lubuntu-desktop) and used the GUI network manager to configure the addon nics, enp2s0 and enp3s0 as DHCP. As a quick and dirty way of testing, I connected the addon nics to my hardware router (tplink) that gives out DHCP addresses. 
I tried each nic one at a time. Enp2s0 and enp3s0 both get DHCP addresses but at that point I don't get internet via the connection, nor am I able to ping the DHCP IP address displayed on ifconfig from any machine on my network. 
Only the onboard nic, enp1s0 works which I am able to get internet on and also successful pings to it on my network.

I then decided to manually enter the configurations for enp2s and enp3s in /etc/network/interfaces but that yielded the same results of me getting a DHCP ip address but no internet or network connectivity.
 
I am not sure if I am overlooking something simple, but can anyone provide me some guidance on what I may be doing wrong or missing completely. I have posted the results of the ifconfig and the interfaces file below. 

*Note- each time I made a change to the network, I either restarted the machine or restarted the network service.

```
ifconfig:

enp1s0    Link encap:Ethernet  HWaddr 44:8a:5b:8b:95:56  
          inet addr:192.168.0.100  Bcast:192.168.0.255  Mask:255.255.255.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

enp2s0    Link encap:Ethernet  HWaddr e8:de:27:a7:9a:27  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

enp3s0    Link encap:Ethernet  HWaddr 00:08:54:71:e9:46  
          inet addr:192.168.0.6  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::4fca:a83c:ef5b:a6fe/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:29 errors:0 dropped:0 overruns:0 frame:0
          TX packets:27 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2304 (2.3 KB)  TX bytes:5602 (5.6 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:808 errors:0 dropped:0 overruns:0 frame:0
          TX packets:808 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1 
          RX bytes:65521 (65.5 KB)  TX bytes:65521 (65.5 KB)

/etc/network/interfaces

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

source /etc/network/interfaces.d/*

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto enp1s0
iface enp1s0 inet static
 address 192.168.0.100
 netmask 255.255.255.0
 network 192.168.0.0
 broadcast 192.168.0.255
 gateway 192.168.0.1
 dns-nameservers 192.168.0.1 0.0.0.0

```

---

### Post by wildmanne39 on 2016-07-09
Please use the default font color and properties unless you need to highlight or draw attention to a part of your post, but they are not intended to be used for an entire post.

Please use code tags - if you are using New Reply button - highlight text and use the # button in the text box header. 
 
If using Quick Reply then [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.

---

### Post by &amp;KyT$0P# on 2016-07-09
NetworkManager can handle static IP addresses.  Since you now have NetworkManager try removing enp1s0 from /etc/network/interfaces and just enter that configuration in a NetworkManager connection for the enp1s0 interface?

---

### Post by Raging_Cascadoo on 2016-07-09
I will try that in case it's causing a problem but right now enp1s0 is the only interface that works.

---

### Post by gordintoronto on 2016-07-10
Have you tried just installing pfSense? I assume the three NICs are for WAN, LAN and a DMZ?

---

### Post by Raging_Cascadoo on 2016-07-10
I actually got this resolved today. I ended up commenting out my entry for enp1s0 from /etc/network/interfaces and then rebooted. All 3 wired connections then appeared through the network manager GUI. I then used the network manager instead to configure the connections. Enps1s0 as static, enps2s0 and enps3s0 as DHCP. I had to manually set the DNS for the DHCP connections before they started working though. Once that was done I was able to get the Pfsense VM working. I am guessing that you have to use either the interfaces file or network manager and not both?

Before changing the network configurations, Pfsense would actually get the WAN DHCP address and distribute IPs through the LAN connection. The problem was even though the clients connected to the router got IPs they were unable to get internet access or even be able to ping the router interface IP, which I couldn't understand. 

As for the usage, the on board Ethernet is used for access to samba shares I have on a mdadm partition and the two add-on ethernets are to be used for the WAN and LAN connection for the Pfsense VM. I just wanted to have the traffic separate.

---

### Post by &amp;KyT$0P# on 2016-07-11
> I am guessing that you have to use either the interfaces file or network manager and not both?
I don't think you "have to" use exclusively one or the other, but it gets really messy to mix the two, especially if they're both used for a same interface.
(I've found NetworkManager generally more "forgiving".  Also you might be interested to know that NetworkManager does not require a GUI and has a terminal interface - it's [FONT=Courier New]nmtui[/FONT] in 16.04 but I forget what it's called in earlier versions.)

---

### Post by Raging_Cascadoo on 2016-07-11
> **halogen2 said:**
> I don't think you "have to" use exclusively one or the other, but it gets really messy to mix the two, especially if they're both used for a same interface.
(I've found NetworkManager generally more "forgiving".  Also you might be interested to know that NetworkManager does not require a GUI and has a terminal interface - it's [FONT=Courier New]nmtui[/FONT] in 16.04 but I forget what it's called in earlier versions.)

Thanks for the info, I will look into network manager terminal interface.

---

