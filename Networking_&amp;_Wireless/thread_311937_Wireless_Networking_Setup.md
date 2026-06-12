---
title: "Wireless Networking Setup"
date: 2006-12-03
forum: Networking &amp; Wireless
---

### Post by JPMaximilian on 2006-12-03
I'm running ubuntu 6.10.  I'm trying to connect to a WPA2-Personal wireless network.  I think that my wireless network adapter is not working.  Here part of the output for sudo lshw:

           *-network:1 UNCLAIMED
                description: Ethernet controller
                product: AR5005G 802.11abg NIC
                vendor: Atheros Communications, Inc.
                physical id: 6
                bus info: pci@0a:06.0
                version: 01
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list
                resources: iomemory:d0200000-d020ffff irq:11

THe output of ifconfig

eth0      Link encap:Ethernet  HWaddr 00:16:D3:42:8A:F5  
          inet addr:207.63.255.11  Bcast:207.63.255.255  Mask:255.255.254.0
          inet6 addr: fe80::216:d3ff:fe42:8af5/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:5291 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1918 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2055860 (1.9 MiB)  TX bytes:360529 (352.0 KiB)
          Interrupt:233 Base address:0x8000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:200 (200.0 b)  TX bytes:200 (200.0 b)

I think that I need to use wpa supplicant, but I'm not sure what wpa_supplicant.conf should be, and it seems like I need to install anth0 before wpa_supplicant will work.  I'm really quite lost and searching through the forums and help docs hasn't seemed to get me to any answers.

---

### Post by JPMaximilian on 2006-12-04
So I installed the restricted kernel module and now wireless connection shows up in system->administration->networking

I then run  

sudo wpa_supplicant -Dmadwifi -iwifi0 -cwpa_supplicant.conf

and get the errors:

ioctl[SIOCSIWPMKSA]: Invalid argument
ioctl[SIOCSIWMODE]: Invalid argument
Could not configure driver to use managed mode
ioctl[SIOCGIWRANGE]: Invalid argument
ioctl[IEEE80211_IOCTL_SETPARAM]: Invalid argument
ioctl[SIOCSIWAP]: Invalid argument
Failed to initialize driver interface

I'm not sure if wifi0 is the right name of the interface I want or if that name is arbitrary.

Again, any help would be appreciated.

---

### Post by JPMaximilian on 2006-12-06
I installed gtkWifi and I can see networks, so I know my wireless card is working.  But I'm unable to connect to unbroadcasted networks, and I don't know if WPA will work.

---

### Post by JPMaximilian on 2006-12-07
It was a long hard road, but I finally got wireless working on my Acer TravelMate 2440.  

I had been working on it for so long I don't remember the exact steps I took initially, but I'll try to explain what I did for progeny.  

The first step was to download the restricted kernel module.  Before I did this my wireless adapter did not show up in system->administration->networking

After doing this, not that order matters, I installed wpa_supplicant from synaptic.

You'll need to setup a config file for wpa_supplicant here is what mine looks like (I omitted some stuff for security):

# Minimal /etc/wpa_supplicant.conf to associate with open
#  access points. Please see 
#  /usr/share/doc/wpasupplicant/examples/wpa_supplicant.conf.gz for more
#  complete configuration parameters.
#
# Also see the other files in /usr/share/doc/wpasupplicant/examples/ for
#  specific configuration examples.

ctrl_interface=/var/run/wpa_supplicant
ctrl_interface_group=0

eapol_version=1
ap_scan=1
fast_reauth=1

### Example of basic WPA-PSK secured AP
#network={
#    ssid="ournet"
#    psk="w243sd5f324asdf5123sadf54324"
#}

### Associate with any open access point
###  Scans/ESSID changes can be done with wpa_cli
#network={
#        ssid=""
#        key_mgmt=NONE
#	priority=4
#{

##UIUCnet
network={
	ssid="UIUCnet"
	key_mgmt=NONE
	priority=1
}

##The Wireless Network
network={
	ssid="thewirelessnetwork name"
	scan_ssid=1
	#proto=RSN
	#key_mgmt=WPA-PSK
	#pairwise=CCMP
	#group=CCMP
	psk="your psk code stuff"
	#psk=abbastuff8353c
	priority=2
}

Your config file will vary, the first network is a broadcasted ssid, and the second is a WPK2 supplicant that is not broadcasted.  

After setting this up edit /etc/network/interfaces

Mine looks like this:

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface

iface eth0 inet dhcp

iface ath0 inet dhcp
wireless-essid UIUCnet
wireless-key s:

You need to run ifconfig to see which interface to use, mine is "ath0".

So then I run:

sudo wpa_supplicant -D wext -i ath0 -c ~/wpa_supplicant.conf

I then refresh/get a DHCP address by running:
sudo dhclient ath0


This is pretty general, you've got to figure out what the name of your wireless interface is, and you need to setup your wpa_supplicant.conf correctly.

---

