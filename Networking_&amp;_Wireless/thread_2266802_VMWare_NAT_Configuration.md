---
title: "VMWare NAT Configuration"
date: 2015-02-25
forum: Networking &amp; Wireless
---

### Post by Mitch_Miller on 2015-02-25
[TABLE]
[TR]
[TD="class: votecell"][/TD]
[TD="class: postcell"]I am trying to run the latest Ubuntu Desktop as a guest inside VMWare Workstation. I need to use NAT for internet access and access to the other Virtual Machines. This works flawlessly on all of my Windows guest machines. On the Windows host I have the following ipconfig information for my VMNet8 adapter. 

```
Ethernet adapter VMware Network Adapter VMnet8:

Connection-specific DNS Suffix  . :
Description . . . . . . . . . . . : VMware Virtual Ethernet Adapter for VMnet8
Physical Address. . . . . . . . . : 00-50-56-C0-00-08
DHCP Enabled. . . . . . . . . . . : No
Autoconfiguration Enabled . . . . : Yes
IPv4 Address. . . . . . . . . . . : 192.168.28.1(Preferred)
Subnet Mask . . . . . . . . . . . : 255.255.255.0
Default Gateway . . . . . . . . . :
NetBIOS over Tcpip. . . . . . . . : Enabled
```


For my Ubuntu machine I have put the following in /etc/network/interfaces
```
auth eth0
iface eth0 inet static
address 192.168.28.12
netmask 255.255.255.0
gateway 192.168.28.2
dns-nameservers 192.168.28.2

```With this information I can only ping other virtual machines and the internet by IP address. Using the machine name or [www.google.com]("http://www.google.com") will not work. 
If I add 8.8.8.8 as a dns-nameserver as well I can of course hit the internet by using google.com, but I still have to use an IP for my internal network. I need some help on this, I have tried multiple things. I have to believe it's not an issue with my Hosts configuration since it works on my Windows machines just fine. 


[/TD]
[/TR]
[/TABLE]

---

