---
title: "Centrino Wireless"
date: 2005-08-17
forum: Networking &amp; Wireless
---

### Post by EpiLePTiC FaiRY on 2005-08-17
I'm having an absolute nightmare of a time trying to get my Centrino laptop set up to access the wireless network in my home. I'll try and tell you everything but I'm afraid I'm a bit new and I'll probably forget something so ask for anything extra.

First of all - my hardware:
```
dmesg | grep ipw
> ipw2100: Intel(R) PRO/Wireless 2100 Network Driver, 1.0.2
> ipw2100: Copyright(c) 2003-2004 Intel Corporation
> ipw2100: Detected Intel PRO/Wireless 2100 Network Connection
```

This is trying to connect to a Linksys [WRT54GS](http://www.linksys.com/servlet/Satellite?childpagename=US%2FLayout&packedargs=c%3DL_Product_C2%26cid%3D1115416825841&pagename=Linksys%2FCommon%2FVisitorWrapper)  with WPA-PSK encryption enabled (Algorithm TKIP) and showing the SSID for the time being because I was told that might be one of the problems. Before I installed wpasupplicant (through apt-get) the wireless network card told me that it had an excellent signal from the router, but could not connect for obvious reasons. Since then the connection never works and the signal strength is permanently 0. I know the card works and that I am in range because XP on dual boot connects without a probem.

/etc/network/interfaces
```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface

iface eth0 inet dhcp
name Ethernet LAN card

#auto eth1
#iface eth1 inet dhcp
#name Wireless LAN card
#wireless-essid homestar
#wireless-key ****-****-**

auto eth1
iface eth1 inet dhcp
#iface eth1 inet static
#	address 192.168.1.3
#	netmask 255.255.255.0
pre-up /usr/sbin/wpa_supplicant -Bw -iwlan0 -c /etc/wpa_supplicant.conf
post-down killall -q wpa_supplicant
```

I don't know if that pre-up script is wrong, that's the best I could work out for myself!

Which leads us to /etc/wpa_supplicant.conf
```
ctrl_interface=/var/run/wpa_supplicant
ap_scan=2
network={
	scan_ssid=1
        ssid="homestar"
        psk=mylongpskthatiwouldrathernotsharethanks
	key_mgmt=WPA-PSK
	pairwise=TKIP
	proto=WPA
}
```

So finally when I try to bring up the wireless network:
```
ifup eth1
> Internet Systems Consortium DHCP Client V3.0.1
> Copyright 2004 Internet Systems Consortium.
> All rights reserved.
> For info, please visit http://www.isc.org/products/DHCP
> 
> sit0: unknown hardware address type 776
> sit0: unknown hardware address type 776
> Listening on LPF/eth1/00:04:23:49:9c:f3
> Sending on   LPF/eth1/00:04:23:49:9c:f3
> Sending on   Socket/fallback
> DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 5
> DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 7
> DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 10
> DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 18
> DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 10
> DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 11
> No DHCPOFFERS received.
> No working leases in persistent database - sleeping.
```

If anyone can tell me why I have this problem I would be very grateful. Like I say, if you need any more information, please ask. By the way, my network runs on the default subnet 255.255.255.0 so I don't know why this DHCPDISCOVER method is trying that subnet, and I don't know how to change it.

Thanks in advance  :-)

---

### Post by npaladin2000 on 2005-08-18
I don't think the Intel 802.11b supports WPA-PSK....the ipw2100 is older. The ipw2200 does but not the version supplied with Hoary.

You might want to check the HOWTO section for the ipw2200 and WPA HowTo...it's going to involve some compiling though.  But the 2200 driver (supposedly) also supports the 2100 (and now the new AG chip...2915 or something?)

---

### Post by luca_linux on 2005-08-18
Follow the following HowTo, but installing ipw2100 instead of ipw2200: [http://www.ubuntuforums.org/showthread.php?t=26623](http://www.ubuntuforums.org/showthread.php?t=26623)

---

### Post by EpiLePTiC FaiRY on 2005-10-22
I gave that a go and now my wireless card doesn't appear as a network device.

It's still there in the Device Manager but not in the Gnome network manager. I'm going to try and take it back to the 2100 driver unless anyone has any other ideas?

---

### Post by Psquared on 2005-10-22
[QUOTE=EpiLePTiC FaiRY]I gave that a go and now my wireless card doesn't appear as a network device.

It's still there in the Device Manager but not in the Gnome network manager. I'm going to try and take it back to the 2100 driver unless anyone has any other ideas?[/QUOTE]


Uh uh .... don't do that yet.

Try this first.

1) turn off all networking devices - including eth0 (ethernet)

2) see if you have a file called /etc/modprobe.d/ipw2200.

3) if not, create the file using sudo gedit or sudo nano

4) add the line:

options ipw2200 hwcrypto=0

5) save the file

6) run these commands:  sudo modprobe -r ipw2200
                                  sudo modprobe ipw2200 hwcyrpto=0

See if the wireless comes back up. 

I've tried everything known to man and this is the solution that finally worked for me. BTW, I do have the latest firmware, ieee80211 and ipw2200 1.0.6.

---

### Post by EpiLePTiC FaiRY on 2005-10-22
Oops. Thanks for the suggestion but I already removed the driver. I looked back on the sourceforge ipw2100 driver and there was an interesting little script written by someone called Pedro. It has brought my wireless back and connected it to the WPA network.

All hail Pedro.

**Update**
Well it worked for 20 seconds to send that message anyway. Back on wired again now. I'll head back to square 1 and try again.

---

