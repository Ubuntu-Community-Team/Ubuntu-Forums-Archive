---
title: "Bridge wireless and lan"
date: 2008-11-24
forum: Networking &amp; Wireless
---

### Post by de_mts on 2008-11-24
Hi,

I want to bridge my wireless network from my notebook with a lan so I can use internet on an other device that doesn't has a wireless card.

How can I do that this is mij /etc/network/interfaces
```
auto lo
iface lo inet loopback

auto eth0
#iface eth0 inet dhcp

auto eth1
#iface eth1 inet dhcp

auto eth2
#iface eth2 inet dhcp

auto ath0
#iface ath0 inet dhcp

auto wlan0
#iface wlan0 inet dhcp

auto tap0
iface tap0 inet manual
tunctl_user tim 

auto br0
iface br0 inet dhcp
bridge-ports eth0 tap0
```

---

### Post by SpaceTeddy on 2008-11-25
to brigde two (or more) interfaces you need to bring the physical interfaces ip in promisc mode WITHOUT any ip-assigned to them. The you add them to the bridge and assign the ip-configuration to the bridge device... 
in your case, you are probably looking for these entries in your /etc/network/interfaces:


```

auto tap0
iface tap0 inet manual
up ifconfig $IFACE 0.0.0.0 up
up ip link set $IFACE promisc on
down ip link set $IFACE promisc off
down ifconfig $IFACE down 

auto eth1
iface eth1 inet manual
up ifconfig $IFACE 0.0.0.0 up
up ip link set $IFACE promisc on
down ip link set $IFACE promisc off
down ifconfig $IFACE down 

auto br0
iface br0 inet static
address 192.168.1.1
netmask 255.255.255.0
broadcast 192.168.1.255
network 192.168.1.0
bridge_ports eth1 tap0
```

this will bring up the two interfaces you want to bridge in promisc mode without an ip upon booting and then join them together on the bridge br0.
configure br0 as if it is a normal network card - but the settings apply to eth1 as well as tap0.

cheers.

BTW: why tap0 ??? that is not a physcial interface that usually needs to be bridged... i have only seen this done in openvpn network bridging servers or embedded vpn configurations...

---

### Post by de_mts on 2008-11-26
I am rather new with ubuntu and just trying alot.


Don't know why tap0 it was the first time I saw /etc/network/interfaces perhaps from VirtualBox?

I changed /etc/network/interfaces to the code you gave and it doesn't do what I thought. At my other device I can't access the network but it doesn't have an IP-adres so I think I need a DHCP server?

---

### Post by SpaceTeddy on 2008-11-26
so... where does the tap0 device in your interfaces come from if you did not put it there ? i thought that was the virtual device (VPN ?) that you are trying to bridge... 

what exactly are to trying to accomplish and which interfaces do you want to act as one ? i am confused...

---

### Post by de_mts on 2008-11-27
Ok I'll try to explain.

I have a notebook with a wireless card inside. This works.
On this notebook I work with Ubuntu 8.10 and I have a VirtualMachine with XP. On this virtual machine my network works.

Now I have a Digicorder (to see digital tv) on my room. I need to connect this device to my network so it's interactive. It doesn't have an IP-adres so I supose it need to get his IP from a DHCP server.

What I want to do is to bridge the wireless network from my notebook to the ethernet port so I can connect my Digicorder to my notebook so it is in my netwerk and I can get on internet with the digicorder.

I hope you understand it and all ready thanks for your patience.

---

