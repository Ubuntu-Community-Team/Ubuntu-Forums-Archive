---
title: "Unsuccessful attempts to add some static IPs"
date: 2008-06-08
forum: Networking &amp; Wireless
---

### Post by volmark on 2008-06-08
Added following lines to /etc/network/interfaces

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet dhcp

iface eth0 inet static
	address 192.168.1.222
	netmask 255.255.255.0
	gateway 192.168.1.4
	
 iface eth0 inet static
	address 192.168.111.222
	netmask 255.255.255.0
	gateway 192.168.111.111 

Got following error messages trying restart with sudo /etc/init.d/networking restart

* Reconfiguring network interfaces...                                                                                         /etc/network/interfaces:13: duplicate interface
ifdown: couldn't read interfaces file "/etc/network/interfaces"
/etc/network/interfaces:13: duplicate interface
ifup: couldn't read interfaces file "/etc/network/interfaces"

My /etc/resolv.conf looks like

search cust.cdnet.dk
nameserver 85.218.184.3
nameserver 85.218.129.11
nameserver 85.218.128.141

What I’m doing wrong????????????

---

### Post by gug@fnal.gov on 2008-06-08
iface eth0 inet static
address 192.168.1.222

iface eth0 inet static
address 192.168.111.222

why is eth0 defined twice? Shouldn't the second one be eth1? This at least also seems to be the complaint from the OS, "/etc/network/interfaces:13: duplicate interface". Just for fun try changing the second eth0 to eth1 and see what happens.

---

### Post by volmark on 2008-06-08
As I understand eth represents a physical networks card. I have only one physical interface on my system. Besides that I have moved the host machine to the basement and no display or keyboard is connected to. The only option to manage the system is SSH &#8211; Putty.
If I do something wrong with network I&#8217;ll be forced to do a lot of physical work to recreate the system.

Generally I need to bind only one interface to some networks with different IP ranges.

---

