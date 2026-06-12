---
title: "Multiple IP addresses on one NIC?"
date: 2006-10-25
forum: Networking &amp; Wireless
---

### Post by seasteve on 2006-10-25
Windows XP allows multiple IP addresses to be assigned to a single adapter, allowing connection to different networks without changing addresses.  How can I do this in Ubuntu?

I have a PC connected to an Ethernet Wireless Bridge which has a private IP address in it, 10.0.X.X, so to access it I need to add a second IP address into my Ubuntu box.  

I have a "public" static IP address, 12.214.x.x, and connect to the Internet via the wireless Ethernet bridge.

---

### Post by studentism on 2006-10-25
IP aliasing for the win.  I've only set it up on other distributions, but I don't see why this wouldn't work.  There's a quick and dirty guide to it here:
[http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch03_:_Linux_Networking#Multiple_IP_Addresses_on_a_Single_NIC](http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch03_:_Linux_Networking#Multiple_IP_Addresses_on_a_Single_NIC)

You'll have to alter the section on 
"/etc/sysconfig/network-scripts/ifcfg-wlan0:0" to use the "/etc/network/interfaces" file and formatting in Ubuntu, I believe.

Let me know how that works out for you/if there are any other questions (I'm assuming a certain level of proficiency in configuring interfaces in Ubuntu, my apologies if that's not the case).

---

### Post by mips on 2006-10-25
Here is an example. You have to change the gateways, subnet masks etc to suit your environment.

/etc/network/interfaces file
```

iface eth0:1 inet static
address 10.0.0.100 
netmask 255.255.0.0
network 10.0.0.0
broadcast 10.0.0.255
gateway 10.0.0.1

iface eth0:2 inet static
address 12.214.x.x
netmask 255.0.0.0
network 12.214.x.0
broadcast 12.214.x.x255
gateway 12.214.x.1
```

---

### Post by seasteve on 2006-10-26
Here's my interfaces file with the recommended changes.  With these entries nothing works.  

```

auto lo
iface lo inet loopback

auto eth0
iface eth0:1 inet static
address 12.175.x.x
netmask 255.255.254.0
network 12.175.x.x
broadcast 12.175.x.x
gateway 12.175.x.x

iface eth0:2 inet static
address 10.0.214.135
netmask 255.255.254.0
network 10.0.x.x
broadcast 10.0.x.x
gateway 10.0.x.x

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp
```

If I change "iface eth0:1"  to "iface eth0" it works for my public network but not my private network.  I can test with a ping to known good IPs on both networks.
 
One thing to add here; the private network dosn't have an actual gateway.  I jsut use the 10.0.x.x network to manage wireless bridges.

---

### Post by mips on 2006-10-27
What output do you get from **route -n** ?

---

### Post by seasteve on 2006-10-27
Before we go any further...how do I "reload" the new interface settings without re-booting?

And I just want to say thanks for helping me with this.

---

