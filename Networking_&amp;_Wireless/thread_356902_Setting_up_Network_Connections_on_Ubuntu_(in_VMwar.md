---
title: "Setting up Network Connections on Ubuntu (in VMware)"
date: 2007-02-08
forum: Networking &amp; Wireless
---

### Post by m|sha on 2007-02-08
Hi all,
I'm using VMWare Workstation 5 and I have Ubuntu Edgy installed onto it. I was wondering how I could get Ubuntu to just use the internet my Windows 2000 is providing.. I know it has to do with the Virtual Network Settings in VMWare and that's about it.. I'm not sure what to do. Any help is appreciated

Here's what I get when I do an IpConfig in Windows

[SIZE="1"]


Windows 2000 IP Configuration



	Host Name . . . . . . . . . . . . : cheynespc
	Primary DNS Suffix  . . . . . . . : 
	Node Type . . . . . . . . . . . . : Broadcast

	IP Routing Enabled. . . . . . . . : No

	WINS Proxy Enabled. . . . . . . . : No


Ethernet adapter Local Area Connection:



	Connection-specific DNS Suffix  . : 
	Description . . . . . . . . . . . : Compact Wireless-G USB Adapter
	Physical Address. . . . . . . . . : 00-18-39-08-82-38

	DHCP Enabled. . . . . . . . . . . : Yes

	Autoconfiguration Enabled . . . . : Yes

	IP Address. . . . . . . . . . . . : 192.168.1.35

	Subnet Mask . . . . . . . . . . . : 255.255.255.0

	Default Gateway . . . . . . . . . : 192.168.1.1

	DHCP Server . . . . . . . . . . . : 192.168.1.1

	DNS Servers . . . . . . . . . . . : 192.168.1.1
	Lease Obtained. . . . . . . . . . : Thursday, February 08, 2007 9:04:31 PM

	Lease Expires . . . . . . . . . . : Friday, February 09, 2007 9:04:31 PM


Ethernet adapter VMware Network Adapter VMnet1:



	Connection-specific DNS Suffix  . : 
	Description . . . . . . . . . . . : VMware Virtual Ethernet Adapter for VMnet1
	Physical Address. . . . . . . . . : 00-50-56-C0-00-01

	DHCP Enabled. . . . . . . . . . . : No

	IP Address. . . . . . . . . . . . : 192.168.116.1

	Subnet Mask . . . . . . . . . . . : 255.255.255.0

	Default Gateway . . . . . . . . . : 

	DNS Servers . . . . . . . . . . . : 

Ethernet adapter VMware Network Adapter VMnet8:



	Connection-specific DNS Suffix  . : 
	Description . . . . . . . . . . . : VMware Virtual Ethernet Adapter for VMnet8
	Physical Address. . . . . . . . . : 00-50-56-C0-00-08

	DHCP Enabled. . . . . . . . . . . : No

	IP Address. . . . . . . . . . . . : 192.168.168.1

	Subnet Mask . . . . . . . . . . . : 255.255.255.0

	Default Gateway . . . . . . . . . : 

	DNS Servers . . . . . . . . . . . : 
[/SIZE]

Thanks,
Misha

---

### Post by gradedcheese on 2007-02-08
I don't know how VMware works in Windows but VMWare in general will provide a virtual interface to Ubuntu that it can easily use (ie: even though the real one is a WiFi interface, the Ubuntu one will just be a network card).  Is it not working for you?  If it's not, try powering down the virtual machine and then pressing "edit virtual machine settings" -- there you can edit the network card (and connect it to the right one in Windows) or "Add" it if it's not there yet.

---

