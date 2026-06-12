---
title: "No DHCP Offer / no IPv6 routers present"
date: 2006-07-24
forum: Networking &amp; Wireless
---

### Post by karasu on 2006-07-24
It isn't for lack of trying, but I can't get wireless to work on a Ubuntu 6.06 install using an Atheros AR5212 802.11abg NIC with madwifi. 

The access point picks up fine:

```
root@yoshi:~# iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

ath0      Scan completed :
          Cell 01 - Address: mm:mm:mm:mm:mm:mm
                    ESSID:"mmmm mmmm"
                    Mode:Master
                    Frequency:2.442 GHz (Channel 7)
                    Quality=33/94  Signal level=-62 dBm  Noise level=-95 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 22 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100

sit0      Interface doesn't support scanning.
```

But I won't get an IP from the DHCP server:

```
root@yoshi:~# dhclient
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/products/DHCP

Listening on LPF/ath0/00:16:ce:29:f3:6f
Sending on   LPF/ath0/00:16:ce:29:f3:6f
Listening on LPF/eth0/00:01:4a:f8:e0:ba
Sending on   LPF/eth0/00:01:4a:f8:e0:ba
Sending on   Socket/fallback
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 21
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
```

Here's the /etc/network/interfaces:


```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
#mapping hotplug
#	script grep
#	map eth0

iface ath0 inet dhcp
wireless-essid mmmmmmmm


auto ath0

# iface eth0 inet dhcp

# auto eth0
```

Configurations:

```
root@yoshi:~# ifconfig
ath0      Link encap:Ethernet  HWaddr 00:16:CE:29:F3:6F
          inet6 addr: fe80::216:ceff:fe29:f36f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:722 dropped:0 overruns:0 frame:722
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:200
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:217 Memory:d0420000-d0430000

eth0      Link encap:Ethernet  HWaddr 00:01:4A:F8:E0:BA
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:225 Base address:0x8000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:6065 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6065 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:494488 (482.8 KiB)  TX bytes:494488 (482.8 KiB)
```

```
root@yoshi:~# iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

ath0      IEEE 802.11  ESSID:"mmmmmmmm"
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated
          Bit Rate:1 Mb/s   Tx-Power:18 dBm   Sensitivity=0/3
          Retry:off   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality=0/94  Signal level=-95 dBm  Noise level=-95 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.
```


A few lines from dmesg:

```
root@yoshi:~# dmesg | grep ath
[17179588.052000] ath_hal: module license 'Proprietary' taints kernel.
[17179588.052000] ath_hal: 0.9.14.9 (AR5210, AR5211, AR5212, RF5111, RF5112, RF2413)
[17179588.188000] ath_rate_sample: 1.2
[17179588.212000] ath_pci: 0.9.6.0 (EXPERIMENTAL)
[17179589.536000] ath0: 11b rates: 1Mbps 2Mbps 5.5Mbps 11Mbps
[17179589.536000] ath0: 11g rates: 1Mbps 2Mbps 5.5Mbps 11Mbps 6Mbps 9Mbps 12Mbps 18Mbps 24Mbps 36Mbps 48Mbps 54Mbps
[17179589.536000] ath0: H/W encryption support: WEP AES AES_CCM TKIP
[17179589.536000] ath0: mac 7.9 phy 4.5 radio 5.6
[17179589.536000] ath0: Use hw queue 1 for WME_AC_BE traffic
[17179589.536000] ath0: Use hw queue 0 for WME_AC_BK traffic
[17179589.536000] ath0: Use hw queue 2 for WME_AC_VI traffic
[17179589.536000] ath0: Use hw queue 3 for WME_AC_VO traffic
[17179589.536000] ath0: Use hw queue 8 for CAB traffic
[17179589.536000] ath0: Use hw queue 9 for beacons
[17179589.536000] ath0: Atheros 5212: mem=0xb0100000, irq=217
[17179729.812000] ath0: no IPv6 routers present
```

Thanks for any help!

---

### Post by karasu on 2006-07-25
I've switched the router to a static IP, and I can see the access point: 

```
karasu@yoshi:~$ iwlist ath0 ap
ath0      Peers/Access-Points in range:
    mm:mm:mm:mm:mm:mm : Quality=33/94  Signal level=-62 dBm  Noise level=-95 dBm
```

I can't ping though.

---

### Post by CVDpr on 2006-07-25
keep waiting..

---

### Post by kreegor on 2008-03-04
I have the same issue. Been trying this for about 4 hours now and decided to leave it while I went to work. So I will check it when I get home.

My wireless card is a TP-Link with an Atheros chipset so there is no issue with the drivers. It can see the router (Netgear DG834G v3) and the router can see the wireless card (appears under the access list) but cannot connect via DHCP.

> ath0: no IPv6 routers present

This is the thing that is confusing me. I am not too knowledgeable about the intricate details of hardware but maybe my router is IPv4 and my wlan card is IPv6 and can't talk to each other via wireless? If so, how can I fix that.

EDIT: Running Gutsy 7.10 :)

---

### Post by The Cog on 2008-03-04
I can't help with the wireless I'm afraid. But I can tell you that you can ignore the message about no ipv6 router present - there almost certainly isn't one, and you don't need one for normal ipv4 to work.

---

### Post by chili555 on 2008-03-04
Your scan says the essid is ```
ESSID:"mmmm mmmm"
```Your interfaces file says```
wireless-essid mmmmmmmm
```With and without a space will not be interpreted as the same. If there *is* a space in the scanned essid, you will probably need to modify your interfaces file thus:```
wireless-essid "mmmm mmmm"
```

Or is this a typo?

---

### Post by kreegor on 2008-03-04
Probably should add that even when I manually assign an IP address and netmask etc etc I am still unable to connect to the router. I can see its name, see the MAC address, see the fact that it has security etc etc but just can't connect to it.

---

### Post by ryecomp on 2008-03-05
I don't use wireless, but I had the same errors occurring in 3com 905c nic. Solution was inserting my mac address to /etc/dhcp3/dhclient.conf. I posted detailed condition & procedures to this forum.

---

### Post by opsimath on 2008-03-31
Ubuntu is configured by default for ipv6.  It wants an ipv6 router.  Most routers
until today, Mar '08, are ipv4.   Add:  alias ipv6 disable=true by toggling the entry in the  alias file.  Use: [http://help.ubuntu.com/community/WiFiDocs/WirelessTroubleShootingGuide](http://help.ubuntu.com/community/WiFiDocs/WirelessTroubleShootingGuide).  Change the file blacklist in the /etc/modprobe.d folder: 
 gksudo gedit/etc/modprobe.d/blacklist, 
by adding the line: blacklist ipv6
You might also want to change Firefox to use ipv4, by editing: about:config.
Take the connection down with:  sudo ifdown eth0: and then back up with:
sudo ifup eth0; and then do: sudo dhclient eth0.

---

