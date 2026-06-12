---
title: "Wireless: WG111v2 Associated with AP, but DHCP not working"
date: 2007-02-25
forum: Networking &amp; Wireless
---

### Post by t_anjan on 2007-02-25
```
anjan@Supernal:~$ **iwlist scan**
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:14:6C:F0:03:06
                    ESSID:"AnjanWireless"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:5
                    **Encryption key:off**
                    Bit Rates:54 Mb/s
                    Extra: Rates (Mb/s): 1 2 5.5 6 9 11 12 18 22 24 36 48 54 
                    [COLOR="Red"]Quality:22  Signal level:0  Noise level:7[/COLOR]
                    Extra: Last beacon: 12ms ago

sit0      Interface doesn't support scanning.
```

My router is no more than 3 feet away from the computer, so I don't understand why the signal quality is so low.

```
anjan@Supernal:~$ **sudo iwconfig**

lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     802.11b/g linked  ESSID:"AnjanWireless"  
          Mode:Master  Channel=5  **Access Point: 00:18:4D:08:C7:0E**   
          Bit Rate=11 Mb/s   
          Retry:on   Fragment thr:off
          **Encryption key:off**
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.
```

```
anjan@Supernal:~$ **sudo ifconfig wlan0**

wlan0     Link encap:Ethernet  HWaddr 00:18:4D:08:C7:0E  
         [COLOR="Red"]** inet6 addr:**[/COLOR] fe80::218:4dff:fe08:c70e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:27 dropped:0 overruns:0 frame:0
          TX packets:269 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:39838 (38.9 KiB)
```

```
anjan@Supernal:~$ **sudo ifup wlan0**

ifup: interface wlan0 already configured
```

```
anjan@Supernal:~$ **sudo dhclient wlan0**

There is already a pid file /var/run/dhclient.pid with pid 5798864
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/wlan0/00:18:4d:08:c7:0e
Sending on   LPF/wlan0/00:18:4d:08:c7:0e
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 16
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 20
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 15
[COLOR="#ff0000"]No DHCPOFFERS received[/COLOR].
No working leases in persistent database - sleeping.
```

```
**/etc/network/interfaces**

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp


#auto eth1
#iface eth1 inet dhcp

#auto eth2
#iface eth2 inet dhcp

#auto ath0
#iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp
pre-up ifconfig wlan0 up
wireless-essid AnjanWireless
wireless-mode Master
```

I have **not done anything about the drivers** for the Netgear WG111v2. The dongle is still **operating on the built-in drivers**.

The only other point worth mentioning is that I'm using **Edgy [COLOR="#ff0000"]x64[/COLOR]**.

I have been thrashing about this problem for 2 solid months now, and still am not any closer to gettting an IP address from my router (which is the Netgear DG834G v3 and working fine on Windows).

I've also tried static IP address without success. Right now I'm using a wired connection.

All you experts, please lend a helping hand..........

---

### Post by zekus on 2007-04-10
The problem is in the router. I've the same problems with it but wireless works well with other APs

---

### Post by t_anjan on 2007-04-10
Really? Do u have the same combination: Netgear WG111v2 and Netgear DG834G? Does the WG111v2 work on Edgy x64 with other APs, but not with the DG834G?

---

