---
title: "Still more sharing/dhcp-ing - iMac &gt; Ubuntu"
date: 2005-09-14
forum: Networking &amp; Wireless
---

### Post by dj_flx on 2005-09-14
OK, I think I've pounded away on this to the limits of my ability.

Still have an iMac, cabled to a Ubuntu box. The Ubuntu accesses the D-link wireless router via belkin usb wireless. All I want is the Ubuntu to share internet access with the iMac. I thought this would be easy. I sit corrected.

I've tried installing dhcp and bridge-utilities, but I'm afraid there's something I'm not catching on to.

The iMac seems to try to get the info from DHCP but it fails (well, once I got a correct address through DHCPD). I know there's talking going on, the mac will at least complain that there's another computer with the same IP on its little network.

I know the NIC, iMac ethernet port, router and usb link all work, I've used them all mix & match.

Here is what I have going on so far:

# wlan0 gets the wireless connection from d-link hooked to cable downstairs #
# eth0 to iMac ethernet port via crossover cable (no hub/switch) #


# ifconfig output #

root@cdburner:/home/felix # ifconfig
eth0      Link encap:Ethernet  HWaddr 00:0C:41:EE:E4:4F
          inet addr:192.168.0.160  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::20c:41ff:feee:e44f/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:82 errors:0 dropped:0 overruns:0 frame:0
          TX packets:214 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:33270 (32.4 KiB)  TX bytes:10444 (10.1 KiB)
          Interrupt:5 Base address:0x1800

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:668043 errors:0 dropped:0 overruns:0 frame:0
          TX packets:668043 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:77728485 (74.1 MiB)  TX bytes:77728485 (74.1 MiB)

wlan0     Link encap:Ethernet  HWaddr 00:30:BD:65:F1:F9
          inet addr:192.168.0.100  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::230:bdff:fe65:f1f9/64 Scope:Link
          UP BROADCAST RUNNING  MTU:1500  Metric:1
          RX packets:61254 errors:0 dropped:0 overruns:0 frame:0
          TX packets:26091 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:43330699 (41.3 MiB)  TX bytes:3456824 (3.2 MiB)



# lspci output in current condition #

root@cdburner:/home/felix # lspci
0000:00:00.0 Host bridge: VIA Technologies, Inc. VT82C693A/694x [Apollo PRO133x] (rev 03)
0000:00:01.0 PCI bridge: VIA Technologies, Inc. VT8363/8365 [KT133/KM133 AGP]
0000:00:03.0 SCSI storage controller: Adaptec AHA-2940U/UW/D / AIC-7881U
0000:00:04.0 USB Controller: OPTi Inc. 82C861 (rev 10)
0000:00:05.0 Ethernet controller: Linksys NC100 Network Everywhere Fast Ethernet 10/100 (rev 11)
0000:00:14.0 ISA bridge: VIA Technologies, Inc. VT82C686 [Apollo Super South] (rev 22)
0000:00:14.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 10)
0000:00:14.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 10)
0000:00:14.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 10)
0000:00:14.4 Bridge: VIA Technologies, Inc. VT82C686 [Apollo Super ACPI] (rev 30)
0000:00:14.5 Multimedia audio controller: VIA Technologies, Inc. VT82C686 AC97 Audio Controller (rev 20)
0000:01:00.0 VGA compatible controller: nVidia Corporation NV6 [Vanta/Vanta LT] (rev 15)
root@cdburner:/home/felix #



# dhcpd3 startup message #

root@cdburner:/etc/dhcp3 # dhcpd3
Internet Systems Consortium DHCP Server V3.0.1
Copyright 2004 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)
Wrote 0 leases to leases file.
Multiple interfaces match the same subnet: eth0 wlan0
Multiple interfaces match the same shared network: eth0 wlan0
Listening on LPF/wlan0/00:30:bd:65:f1:f9/192.168.0.0/24
Sending on   LPF/wlan0/00:30:bd:65:f1:f9/192.168.0.0/24
Listening on LPF/eth0/00:0c:41:ee:e4:4f/192.168.0.0/24
Sending on   LPF/eth0/00:0c:41:ee:e4:4f/192.168.0.0/24
Sending on   Socket/fallback/fallback-net
root@cdburner:/etc/dhcp3 # dmesg | tail
0000:00:05.0: tulip_stop_rxtx() failed
0000:00:05.0: tulip_stop_rxtx() failed
eth0: Setting full-duplex based on MII#1 link partner capability of 41e1.
eth0: no IPv6 routers present



# my probably wrong .conf file #

# DHCP configuration
ddns-update-style interim;
ignore client-updates;

subnet 192.168.0.0 netmask 255.255.255.0 {
	option routers 69.245.192.1;
	option subnet-mask 255.255.25.0;
	option domain-name-servers 68.87.66.196, 68.87.64.196;
	option ip-forwarding off;
	option domain-name-servers hsd1.in.comcast.net;
#	range dynamic-bootp 192.168.0.20; 192.168.0.254;
	default-lease-time 21600;
	max-lease-time 43200;
}



# d-link info #

LAN
MAC Address 00-13-46-11-2F-88
IP Address  192.168.0.1
Subnet Mask 255.255.255.0
DHCP Server Enabled
  	 
WAN
MAC Address 00-13-46-11-2F-89
Connection  DHCP Client Connected  
IP Address  69.245.192.179
Subnet Mask 255.255.252.0
Default Gateway 69.245.192.1
DNS 	    68.87.66.196   68.87.64.196
  	
Wireless
SSID    default
Channel 1
WEP     Disabled

Bear in mind that I know just enough to cause trouble - I'm still working on havoc.

Mad props in advance to anyone who can help me out!

---

### Post by s_p_a_r_k_y on 2005-09-14
why even use dhcp for a network of 2 computers? Static seams to make more sense

---

### Post by mlomker on 2005-09-14
It would be way less trouble to just buy a wireless adapter for the other box...you've already got a wireless network in the house!  I was at Best Buy the other day and was amazed by how inexpensive they were.

---

