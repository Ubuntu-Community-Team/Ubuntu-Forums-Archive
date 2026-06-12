---
title: "[SOLVED] Atheros in AMD64 Gutsy: Needs roaming enabled"
date: 2008-01-26
forum: Networking &amp; Wireless
---

### Post by edantes on 2008-01-26
I have an Atheros PCI WiFi card in an Ubuntu Gutsy AMD64 box.  The WiFi interface works fine with Roaming Mode enabled, but fails to aquire an IP from DHCP server if I use  the manual configuration.  This happens with and without encryption (WEP,WPA) enabled.

For me, the advantage of having the manual configuration working is that works at boot time.

In case one of the kind knowledgeable souls visiting this topic could help, here are some details. 


Output for route:
```

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
link-local      *               255.255.0.0     U     0      0        0 ath0
default         *               0.0.0.0         U     1000   0        0 ath0

```

iwconfig:
```

ath0      IEEE 802.11g  ESSID:"XXXXX"  Nickname:""
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated   
          Bit Rate:48 Mb/s   Tx-Power:18 dBm   Sensitivity=1/1  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=20/70  Signal level=-73 dBm  Noise level=-93 dBm
          Rx invalid nwid:164507  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

iwlist scan:
```

Cell 02 - Address: 00:90:4C:70:00:10
                    ESSID:"XXXXX"
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Quality=21/70  Signal level=-74 dBm  Noise level=-95 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:bcn_int=100
                    IE: WPA Version 1
                        Group Cipher : WEP-40
                        Pairwise Ciphers (1) : WEP-40
                        Authentication Suites (1) : PSK

```

lshw -C network:
```

  *-network:0             
       description: Wireless interface
       product: AR5212/AR5213 Multiprotocol MAC/baseband processor
       vendor: Atheros Communications, Inc.
       physical id: 7
       bus info: pci@0000:02:07.0
       logical name: wifi0
       version: 01
       serial: 00:18:e7:25:4d:32
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath_pci driverversion=0.9.4.5 (0.9.3.2) latency=168 maxlatency=28 mingnt=10 module=ath_pci multicast=yes wireless=IEEE 802.11g

```

/etc/network/interfaces:

```

auto lo
iface lo inet loopback
auto ath0
iface ath0 inet dhcp
wpa-driver madwifi
wpa-ssid XXXXXX
wpa-ap-scan 1
wpa-proto WPA
wpa-pairwise TKIP
wpa-group TKIP
wpa-key-mgmt WPA-PSK
wpa-psk XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXx

```

ifdown -v ath0
```

Configuring interface ath0=ath0 (inet)
run-parts --verbose /etc/network/if-down.d
run-parts: executing /etc/network/if-down.d/avahi-autoipd
run-parts: executing /etc/network/if-down.d/wpasupplicant
dhclient3 -r -pf /var/run/dhclient.ath0.pid -lf /var/lib/dhcp3/dhclient.ath0.leases ath0
There is already a pid file /var/run/dhclient.ath0.pid with pid 14722
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

wifi0: unknown hardware address type 801
wifi0: unknown hardware address type 801
Listening on LPF/ath0/00:18:e7:25:4d:32
Sending on   LPF/ath0/00:18:e7:25:4d:32
Sending on   Socket/fallback
DHCPRELEASE on ath0 to 192.168.1.1 port 67
ifconfig ath0 down
run-parts --verbose /etc/network/if-post-down.d
run-parts: executing /etc/network/if-post-down.d/avahi-daemon
run-parts: executing /etc/network/if-post-down.d/wireless-tools
run-parts: executing /etc/network/if-post-down.d/wpasupplicant
wpa_supplicant: terminating wpa_supplicant daemon via pidfile /var/run/wpa_supplicant.ath0.pid
Stopped /sbin/wpa_supplicant (pid 14690).

```

ifup -v ath0:
```

Configuring interface ath0=ath0 (inet)
run-parts --verbose /etc/network/if-pre-up.d
run-parts: executing /etc/network/if-pre-up.d/wireless-tools
run-parts: executing /etc/network/if-pre-up.d/wpasupplicant
wpa_supplicant: wpa-driver madwifi
wpa_supplicant: /sbin/wpa_supplicant -B -P /var/run/wpa_supplicant.ath0.pid -i ath0 -D madwifi -C /var/run/wpa_supplicant
Starting /sbin/wpa_supplicant...
wpa_supplicant: ctrl_interface socket located at /var/run/wpa_supplicant/ath0
wpa_supplicant: wpa-ap-scan 1 -- OK
wpa_supplicant: configuring network block -- 0
wpa_supplicant: wpa-ssid "XXXXX" -- OK
wpa_supplicant: wpa-psk ***** -- OK
wpa_supplicant: wpa-pairwise TKIP -- OK
wpa_supplicant: wpa-group TKIP -- OK
wpa_supplicant: wpa-key-mgmt WPA-PSK -- OK
wpa_supplicant: wpa-proto WPA -- OK
wpa_supplicant: enabling network block 0 -- OK

dhclient3 -e IF_METRIC=100 -pf /var/run/dhclient.ath0.pid -lf /var/lib/dhcp3/dhclient.ath0.leases ath0
There is already a pid file /var/run/dhclient.ath0.pid with pid 0
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

wifi0: unknown hardware address type 801
wifi0: unknown hardware address type 801
Listening on LPF/ath0/00:18:e7:25:4d:32
Sending on   LPF/ath0/00:18:e7:25:4d:32
Sending on   Socket/fallback
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 11
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
run-parts --verbose /etc/network/if-up.d
run-parts: executing /etc/network/if-up.d/avahi-autoipd
run-parts: executing /etc/network/if-up.d/avahi-daemon
run-parts: executing /etc/network/if-up.d/mountnfs
run-parts: executing /etc/network/if-up.d/ntpdate
run-parts: executing /etc/network/if-up.d/wpasupplicant

```

---

### Post by b4y03sky on 2008-01-26
Can you tell me how to enable atheros wireless in my laptop ?

I use Acer 5052 laptop

Atheros AR5006eg + Ubuntu Gutsy

I try to use ndiswrapper and madwifi but there's still no wireless in my network list..

Help.. I need it

---

### Post by bwtranch on 2008-01-26
Well, it's not enabling your ath0 and I can't tell why, there is an entry about an old address or something. That might be something to take a look at.  Did you change users or drivers in the past? 

Does it have an ESSID number or did you blank that out for the post?

Well anyway, try and re-install the driver. I've got to go heat up some chicken.

---

### Post by edantes on 2008-01-26
> **b4y03sky said:**
> Can you tell me how to enable atheros wireless in my laptop ?

I use Acer 5052 laptop

Atheros AR5006eg + Ubuntu Gutsy

I try to use ndiswrapper and madwifi but there's still no wireless in my network list..

Help.. I need it

I have two Atheros devices working with madwifi (I assume):

This one is a  AR5212/AR5213 PCI card in a desktop AMD64 Ubuntu 7.10.  After booting, I enabled the corresponding restricted driver.  The nm-applet started automatically and offered the list of available networks.  I clicked on mine, entered the authentication info and everything worked.

By default, it had "Roaming Mode" enabled.  When I tried to switch it off and enter the manual configuration, that's when it fails.

The other is a D-Lnk DWL-G650 PCMCI card in an older Dell notebook with Ubuntu 7.10.  It is also an Atheros AR5212/AR5213.  It also started automatically.  This one worked with  "Roaming Mode" disabled, untill I switched to WPA.  Now only works in Roaming Mode.

---

### Post by edantes on 2008-01-26
I blocked out the ESSID and PSK.  Tough neighborhood :twisted:

I tried disabling and enabling the restricted driver, no change. 

What could the  nm-applet be doing  right and /etc/init.d/networking is not?

> **bwtranch said:**
> Well, it's not enabling your ath0 and I can't tell why, there is an entry about an old address or something. That might be something to take a look at.  Did you change users or drivers in the past? 

Does it have an ESSID number or did you blank that out for the post?

Well anyway, try and re-install the driver. I've got to go heat up some chicken.

---

### Post by edantes on 2008-01-28
In the network-admin app, the "Manual Configuration" option for the Wireless Connection generates an incorrect[FONT="Courier New"] /etc/network/interfaces[/FONT] for my wifi device.   By adding this section, the wifi interface starts correctly at boot time:

[FONT="Courier New"] /etc/network/interfaces[/FONT]
```

auto ath0
iface ath0 inet dhcp
wpa-driver madwifi
wpa-ssid XXXXXX
wpa-ap-scan 1
wpa-proto WPA
wpa-pairwise TKIP
wpa-group TKIP
wpa-key-mgmt WPA-PSK
wpa-psk XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX

```

---

### Post by b4y03sky on 2008-02-01
I got my driver installed but in restricted driver manager it says not in use.

And in my network manager there's no wireless network...

when I configured ath0 it replies error, no wireless extention.. how?

---

