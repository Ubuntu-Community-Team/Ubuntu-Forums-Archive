---
title: "can't set essid"
date: 2006-09-26
forum: Networking &amp; Wireless
---

### Post by sheik482 on 2006-09-26
For the last few days I have been trying to install a linksys wmp11 v4.  I am using ndiswrapper and loaded the drivers just fine.

```

root@Urkle:/home/scott/linksys# ndiswrapper -l
Installed ndis drivers:
lsbcmnds                driver present
lsipnds         driver present, hardware present
wmp11nds                driver present

```

I then scan for my AP using iwlist and I get:

```

root@Urkle:/home/scott/linksys# iwlist wlan0 scan
wlan0     Scan completed :
          Cell 01 - Address: 00:11:95:19:20:CA
                    ESSID:"winslow"
                    Protocol:IEEE 802.11b
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:0/100  Signal level:-53 dBm  Noise level:-256 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0

```

so I then configure it using iwconfig and get the following output

```

root@Urkle:/home/scott/linksys# sudo iwconfig wlan0 essid winslow
root@Urkle:/home/scott/linksys# sudo iwconfig wlan0 mode Managed
root@Urkle:/home/scott/linksys# sudo iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.

wlan0     IEEE 802.11b  ESSID:off/any
          Mode:Managed  Frequency:2.437 GHz  Access Point: Not-Associated
          Bit Rate:1 Mb/s   Tx-Power:17 dBm
          RTS thr:2347 B   Fragment thr:2346 B
          Encryption key:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

as you see essid is still off/any and not winslow.  I tried setting the essid using quotes and still nothing.  I do not have WEP on to try to simplify things.  I also ran the following commands.

```

root@Urkle:/home/scott/linksys# sudo ifdown wlan0
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/products/DHCP

Listening on LPF/wlan0/00:13:10:05:59:f0
Sending on   LPF/wlan0/00:13:10:05:59:f0
Sending on   Socket/fallback
root@Urkle:/home/scott/linksys# sudo ifup wlan0
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/products/DHCP

Listening on LPF/wlan0/00:13:10:05:59:f0
Sending on   LPF/wlan0/00:13:10:05:59:f0
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 17
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 4
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

```

I am out of ideas. does anyone know how to set the essid and make it stick?

---

### Post by wieman01 on 2006-09-26
Post the contents of "/etc/network/interfaces" and we'll see. This file controls your wireless interface.

Do you use a firewall? Just asking...

---

### Post by sheik482 on 2006-09-26
I do not use a firewall.  The AP I am using is a DL-524
Here aer the contents of the interface file.

```

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp

```

---

### Post by wieman01 on 2006-09-26
The try this:
> sudo gedit /etc/network/interfaces
Then replace the contents with this (don't worry, it's safe):
> auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto wlan0
iface wlan0 inet dhcp
wireless-essid winslow
And restart the network:
> sudo /etc/init.d/networking restart
That's it. You can achieve the same by using Gnome's networking applet.

---

### Post by sheik482 on 2006-09-26
I made those changes however it still does not want to work.

---

### Post by wieman01 on 2006-09-26
What's the output when you run the command?

Also try to use the networking applet that you find in Gnome. Disable and enable you network card... That sometimes helps.

One more thing: Have you wpa_supplicant installed? Then perhaps also do:
> sudo killall wpa_supplicant

---

### Post by sheik482 on 2006-09-26
Here is the output of the command

```

root@Urkle:~# sudo killall wpa_supplicant
wpa_supplicant: no process killed
root@Urkle:~# sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces... Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/products/DHCP

Listening on LPF/eth0/00:e0:4c:f4:32:8d
Sending on   LPF/eth0/00:e0:4c:f4:32:8d
Sending on   Socket/fallback
DHCPRELEASE on eth0 to 192.168.0.1 port 67
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/products/DHCP

Listening on LPF/wlan0/00:13:10:05:59:f0
Sending on   LPF/wlan0/00:13:10:05:59:f0
Sending on   Socket/fallback
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/products/DHCP

Listening on LPF/eth0/00:e0:4c:f4:32:8d
Sending on   LPF/eth0/00:e0:4c:f4:32:8d
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
DHCPOFFER from 192.168.0.1
DHCPREQUEST on eth0 to 255.255.255.255 port 67
DHCPACK from 192.168.0.1
bound to 192.168.0.102 -- renewal in 277560 seconds.
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/products/DHCP

Listening on LPF/wlan0/00:13:10:05:59:f0
Sending on   LPF/wlan0/00:13:10:05:59:f0
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
                                                                         [ ok ]

```

when I go to system->admin->network tools I click on Wlna0 and configure is greyed out.  However if I click on eth0 and then back to wlan0 I can click on configure.  Typing the settings in there does nothing :(  How to you disable and enable the network card?

---

### Post by wieman01 on 2006-09-26
Mmm... But your router is set to DHCP?

---

### Post by wieman01 on 2006-09-26
Mmm... Something odd... The signal strength of your wireless network is more than poor, it's zero. Is there anything wrong with the router?
> **[COLOR="Red"]Quality:0/100[/COLOR]**  Signal level:-53 dBm  Noise level:-256 dBm
Or is your PC too far apart from the router?

---

### Post by sheik482 on 2006-09-26
The PC is probobly 3 feet from the router.  I have a PC running win XP probobly 50 feet away using another wmp11 card.  Right now I have the linux box connected using Cat5.   DHCP is enabled on the router.  I am using a DI-524 router if that helps?

---

### Post by wieman01 on 2006-09-26
Ok, I see your wireless card is 11 MBit. Is the router running on the same bit-rate? If not, set it to 11 MBit and try to restart the network.

---

