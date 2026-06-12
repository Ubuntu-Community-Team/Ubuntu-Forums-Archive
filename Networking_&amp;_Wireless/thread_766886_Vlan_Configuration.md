---
title: "Vlan Configuration"
date: 2008-04-25
forum: Networking &amp; Wireless
---

### Post by Rathish2k2 on 2008-04-25
Can anybody help me how to configure VLAN I have tried the following steps but it doesnt work

I have tried this in ubuntu-6.06.1-server-i386 as well as ubuntu-8.04-rc-server-i386

sudo apt-get install vlan

# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
auto vlan4
auto vlan5
auto vlan101

# VLAN 4
iface vlan4 inet static
address 192.168.0.8
netmask 255.255.255.192
network 192.168.0.0
broadcast 192.168.0.63
mtu 1500
vlan_raw_device eth1

# VLAN 5
iface vlan5 inet static
address 10.0.111.8
netmask 255.255.255.0
network 10.0.111.0
broadcast 10.0.111.255
mtu 1500
vlan_raw_device eth2

# VLAN 101
iface vlan101 inet static
address 172.12.101.8
netmask 255.255.255.0
network 172.12.101.0
broadcast 172.12.101.255
gateway 172.12.101.1
mtu 1500
vlan_raw_device eth3

sudo /etc/init.d/networking restart

Set name-type for VLAN subsystem. Should be visible in /proc/net/vlan/config
Added VLAN with VID == 4 to IF -:eth1:-
Set name-type for VLAN subsystem. Should be visible in /proc/net/vlan/config
Added VLAN with VID == 5 to IF -:eth2:-
Set name-type for VLAN subsystem. Should be visible in /proc/net/vlan/config
Added VLAN with VID == 101 to IF -:eth3:-


my client machine connected to each network are unable to ping the VLAN IP address of eth1 eth2 eth3 and it does not work wat could be the problem suggest me

---

### Post by netztier on 2008-04-25
> **Rathish2k2 said:**
> 

my client machine connected to each network are unable to ping the VLAN IP address of eth1 eth2 eth3 and it does not work wat could be the problem suggest me

Why would you want to configure VLANs if you have multiple physical interfaces already? You speak of eth1, eth2, eth3 ...

Just give them IP addresses from different networks and go, there's no need for VLANs. So your /etc/network/interfaces could simply look like this:

```

iface eth1 inet static
address 192.168.0.8
netmask 255.255.255.192
network 192.168.0.0
broadcast 192.168.0.63
mtu 1500

iface eth2 inet static
address 10.0.111.8
netmask 255.255.255.0
network 10.0.111.0
broadcast 10.0.111.255
mtu 1500

iface eth3 inet static
address 172.12.101.8
netmask 255.255.255.0
network 172.12.101.0
broadcast 172.12.101.255
gateway 172.12.101.1
mtu 1500
```

Connect each Interface to a separate hub or switch and there you go! Multiple Networks to one Box without any need for VLANs.

Configuring VLANs is something you do if you want multiple "virtual" networks on one **single** physical interface. So your vlan_raw_device statements should all point to one interface only.

The port your NIC is connected to must be a "802.1q trunk" port on your LAN switch. That trunk port must accept VLAN tags in the frames it receives, and it must add the VLAN tags to the frames it sends out.

See also [this LinuxJournal article]("http://www.linuxjournal.com/node/7268/print")
regards

Marc

---

### Post by soddengecko on 2008-11-26
Hi

I too have multiple physical NIC's in an ubuntu machine. 3 in total. 

eth0 is the external connection
eth1 will carry vlan20 and vlan50
eth2 will carry vlan30 and vlan40

I am having some trouble getting these to communicate with the dhcp server on the ubuntu box and of course I cannot get it to talk to the external interface on eth0. does anyone have any suggestions?

@netztier
I followed what you said about having each interface as a connection point and got that working no problem. I just cannot seem to get the vlan side of things working. 

I have installed vlan and turned 8021q on for trunking.

My switch is a cisco 24 port managed switch with vlan capability and I have marked off the vlans and assigned ports to each of them.

Can anyone give me some pointers?

Thank you

---

