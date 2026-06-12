---
title: "Wireless Troubles"
date: 2007-01-13
forum: Networking &amp; Wireless
---

### Post by richiemcintosh on 2007-01-13
I have Ubuntu 6.10 installed with a dual boot (windows 2000 professional). The problem is it won't let me connect to my wireless connection. I used iwconfig and ifconfig in terminal and it appears that it detects my connection as it shows info about the router and it shows a signal rate.

wlan0 is active in the network settings menu.

I can't add Network Manager or WLanAssistant in the add/remove programs menu.

I'm not even sure if they would help.

My router is Belkin 802.11g

I have a PCI Wireless card.

Help!

---

### Post by hectare on 2007-01-13
please post the result of **iwconfig** or **iwconfig wlan0** replace wlan0 with your wireless device.
please post how you connect to internet , does the wireless router assigns you the ip address or you have to do it manually .


here are some commands which may help , type this in console :
Substitute Red with what ever you have in your system.

**sudo iwconfig [color="red"]wlan0[/color] mode managed**
**sudo iwconfig [color="red"]wlan0[/color] essid [color="red"]"myessid"[/color]**

to add ip address and gateway to wireless card do this:
 
** sudo ip link set dev [color="red"]wlan0[/color] up **
**sudo  ip addr add [color="red"]192.168.1.3/24[/color] dev [color="red"]wlan0[/color] brd + **
** sudo ip route add default via [color="red"]192.168.1.1[/color] dev [color="red"]wlan0[/color] **

Some steps to diagnose 
Ping wireless router
Ping any external ip address
Ping yahoo.com
Check if you have entered dns servers

---

### Post by Floppyjoe on 2007-01-13
What happens when you do the following command?

```
sudo dhclient wlan0
```

Can you post the result?

---

### Post by richiemcintosh on 2007-01-13
richie@richie-desktop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11b+/g+  ESSID:"STA1BE603"  Nickname:"acx v0.3.21"
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated
          Bit Rate:54 Mb/s   Tx-Power=15 dBm   Sensitivity=1/3
          Retry min limit:7   RTS thr:off
          Power Management:off
          Link Quality=47/100  Signal level=26/100  Noise level=0/100
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.

richie@richie-desktop:~$ sudo dhclient wlan0
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

Listening on LPF/wlan0/00:12:0e:1b:e6:03
Sending on   LPF/wlan0/00:12:0e:1b:e6:03
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 4
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
richie@richie-desktop:~$

---

### Post by Floppyjoe on 2007-01-13
Can you post the results of:

```
lspci
```

To see what your wireless card chipset is.

Also post the result of your /etc/network/interfaces file:
```
sudo gedit /etc/network/interfaces
```

---

