---
title: "How to skip misconfigured interface in interfaces file?"
date: 2015-11-26
forum: Networking &amp; Wireless
---

### Post by canavaroski90 on 2015-11-26
Hi all,

I'm working on Ubuntu Server 14.04.03 and trying to configure multiple network interfaces in interfaces file (/etc/network/interfaces).

Here is the interfaces file;
```
# The loopback network interfaceauto lo iface lo inet loopback


# The primary network interface
auto eth0 
allow-hotplug eth0 
iface eth0 inet static
	address 192.168.5.100
	netmask 255.255.255.0
	gateway 192.168.0.1
	dns-nameservers 8.8.8.8


# The primary network interface ARP address
auto eth0:0
iface eth0:0 inet static
allow-hotplug eth0:0
	address 169.254.200.100
	netmask 255.255.0.0




# Secondary network interface
auto eth1
allow-hotplug eth1
iface eth1 inet static
	address 192.168.250.100
	netmask 255.255.255.0
```


The problem is, if eth1 configuration fails (i.e. lack of eth1 interface, wrong ip assignment etc.), eth0 is also not being configured. So I can not reach device from any interface.

Question: How can I configure ubuntu to skip misconfigured interfaces and continue to configure others? 

Thanks in advance.

---

### Post by canavaroski90 on 2015-11-26
Found answer in following link;

[https://www.debian.org/doc/manuals/debian-reference/ch05.en.html#_the_basic_syntax_of_etc_network_interfaces](https://www.debian.org/doc/manuals/debian-reference/ch05.en.html#_the_basic_syntax_of_etc_network_interfaces)

I removed auto eth* lines from the file and it started to run fluently. The mistake that I did was using auto and allow-hotplug options together. While allow-hotplug waits for detection of the interface, auto eth* persistently tries to configure the interface as "up". 

May help for other googlers.

---

