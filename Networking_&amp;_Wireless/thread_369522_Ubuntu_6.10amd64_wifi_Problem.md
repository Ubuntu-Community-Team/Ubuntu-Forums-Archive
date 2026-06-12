---
title: "Ubuntu 6.10amd64 wifi Problem"
date: 2007-02-24
forum: Networking &amp; Wireless
---

### Post by dlkb1240 on 2007-02-24
Ok I just installed 6.10 on my x64 box with a ZyAir G-302 Wireless network card. Everything works fine and linux sees the card and the card can see my network but I cant get a ip address from it.
iwconfig looks like this:
> wlan0     802.11b/g  ESSID:"JD"  
          Mode:Managed  Frequency=2.447 GHz  Access Point: Not-Associated   
          Bit Rate=54 Mb/s   
          Retry:on   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


ifconfig looks like this
> wlan0     Link encap:Ethernet  HWaddr 00:13:49:89:90:76  
          inet6 addr: fe80::213:49ff:fe89:9076/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:7827 errors:661 dropped:483 overruns:0 frame:0
          TX packets:414 errors:250 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1461470 (1.3 MiB)  TX bytes:68561 (66.9 KiB)
          Interrupt:201 Memory:ffffc200000dae00-ffffc200000daf00 


and dhclient looks like this
> Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/wlan0/00:13:49:89:90:76
Sending on   LPF/wlan0/00:13:49:89:90:76
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 15

I haven't found anyone else that has had problems with this card. Any help would be appreciated thanks.

---

### Post by Floppyjoe on 2007-02-24
Make sure only your wireless interface is activated and not any other interface like your wired ethernet is active. In other words disable your wired ethernet device to use wireless.

then:
```
sudo dhclient wlan0
```
should work.

---

### Post by dlkb1240 on 2007-02-24
I did have my wired conection active so i shut it down with sudo ifconfig eth0 down and ran sudo dhclient wlan0 and got the same results:
> Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/wlan0/00:13:49:89:90:76
Sending on   LPF/wlan0/00:13:49:89:90:76
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 12


---

### Post by Floppyjoe on 2007-02-24
Can you post your /etc/network/interfaces file with any sensitive information omitted.

---

### Post by dlkb1240 on 2007-02-24
Here ya go:
> auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp



iface wlan0 inet dhcp
address 192.168.0.100
netmask 255.255.255.0
gateway 192.168.0.1
wireless-essid JD


---

### Post by Floppyjoe on 2007-02-24
> iface wlan0 inet dhcp
address 192.168.0.100
netmask 255.255.255.0
gateway 192.168.0.1
wireless-essid JD 
This tells me that you are trying to get a dhcp address but are also giving static IP addresses.

It should be:
```
iface wlan0 inet static
address 192.168.0.100
netmask 255.255.255.0
gateway 192.168.0.1
wireless-essid JD 
```
 
If you are trying to get a static address from the router. I'm not sure if the router needs to be set up to give out static IPs here.
or:
```
iface wlan0 inet dhcp
#address 192.168.0.100
#netmask 255.255.255.0
#gateway 192.168.0.1
wireless-essid JD 
```
comment out the static entries if you are trying to get a dhcp address.

---

### Post by dlkb1240 on 2007-02-24
Got it... but It still isn't getting an IP saddress
> Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/wlan0/00:13:49:89:90:76
Sending on   LPF/wlan0/00:13:49:89:90:76
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 11



---

### Post by Floppyjoe on 2007-02-24
A couple of other lines that may make it work are:
```
wireless-channel 7
wireless-mode managed
```

Where you use your router channel instead of the one here.

---

### Post by dlkb1240 on 2007-02-24
Everything is set right channel 6 mode is managed but for some reason the signal is 0. Any more ideas would be appreciated. Thanks

---

### Post by rhum on 2007-02-24
u should try to d/l wlassistant and connect with it  

sudo apt-get install wlassistant

---

### Post by dlkb1240 on 2007-03-03
Thats just a GUI frontend for iwconfig. Still can't get it to work any other ideas?

---

