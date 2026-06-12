---
title: "No DHCPOFFERS received"
date: 2007-03-03
forum: Networking &amp; Wireless
---

### Post by lge on 2007-03-03
Hello!
I instaled Ubuntu 6.10 and I configured interfaces WiFi and everything worked.
I updated ubuntu & WiFi is not working

I read many forums and I tried to configure everywhere
1. uninstall:
dhcp3-common, dhcp3-client
2. reinstall dhcdbd and dhcpcd
and WiFi still not working
2. again install:
dhcp3-common, dhcp3-client
and WiFi still not working

I still have this prompt
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

Any ideas?
PLEASE HELP

This is my configuration:

My WiFi card is Ralink 2500 i its works (I check 'lsmod  greep rt2500')

ifconfig
```

eth0      Link encap:Ethernet  HWaddr 00:15:F2:28:8D:81 
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:217

lo        Link encap:Local Loopback 
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

ra0       Link encap:Ethernet  HWaddr 00:0E:2E:57:4F:F3 
          inet6 addr: fe80::20e:2eff:fe57:4ff3/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:58501 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:3861066 (3.6 MiB)
          Interrupt:58 Base address:0x4000

```,


iwconfig
```

lo        no wireless extensions.

eth0      no wireless extensions.

ra0       RT2500 Wireless  ESSID:"RESMAN 22-2 tel_0177483333" 
          Mode:Managed  Frequency=2.412 GHz  Bit Rate:11 Mb/s   Tx-Power:0 dBm   
          RTS thr:off   Fragment thr:off
          Link Quality=0/100  Signal level=-120 dBm  Noise level:-192 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions

```,

ifdown ra0
```

There is already a pid file /var/run/dhclient.ra0.pid with pid 5086
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit

Listening on LPF/ra0/00:0e:2e:57:4f:f3
Sending on   LPF/ra0/00:0e:2e:57:4f:f3
Sending on   Socket/fallback
DHCPRELEASE on ra0 to 192.168.0.1 port 67
send_packet: Network is unreachable
send_packet: please consult README file regarding broadcast address

```,

ifup ra0
```

There is already a pid file /var/run/dhclient.ra0.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit

Listening on LPF/ra0/00:0e:2e:57:4f:f3
Sending on   LPF/ra0/00:0e:2e:57:4f:f3
Sending on   Socket/fallback
DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 21
DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 16
DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 16
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

```,


sudo /etc/init.d/dbus restart
```

 * Stopping System Tools Backends system-tools-backends                             ok 
 * Stopping NetworkManager dispatcher                                               ok 
 * Stopping Avahi mDNS/DNS-SD Daemon: avahi-daemon                                  ok 
 * Stopping NetworkManager daemon                                                   ok 
 * Stopping DBUS aware dhcp client: dhcdbd                                          ok 
 * Stopping Hardware abstraction layer hald                                         ok 
 * Stopping system message bus dbus                                                 ok 
 * Starting system message bus dbus                                                 ok 
 * Starting Hardware abstraction layer hald                                         ok 
 * Starting DBUS aware dhcp client: dhcdbd                                          ok 
 * Starting NetworkManager daemon                                                   ok 
 * Starting NetworkManager dispatcher                                               ok 
 * Starting System Tools Backends system-tools-backends                                   run-parts: /etc/dbus-1/event.d/70system-tools-backends exited with return code 1

```

---

### Post by chili555 on 2007-03-03
How about letting us see the output of sudo iwconfig ra0 , please? I am suspicious about your ESSID: ```
RESMAN 22-2 tel_0177483333
``` Obscure most of any WEP codes, etc., if any.

Post back and we'll get you going.

---

### Post by lge on 2007-03-03
First time I configured my WiFi:

Install:
wpasupplicant
network-manager-gnome
network-manager

Configured:
1. Create a file called /etc/default/wpasupplicant, add entry ENABLED=0 and save the file
2. File /etc/network/interfaces
```

## Interface: localhost
auto lo
iface lo inet loopback

## Interface: WiFi
auto ra0
iface ra0 inet dhcp 
pre-up ifconfig ra0 up
pre-up ifconfig ra0 down
pre-up ifconfig ra0 up
pre-up ifconfig ra0 down
pre-up iwconfig ra0 essid "RESMAN 22-2 tel_0177483333"
pre-up iwconfig ra0 mode Managed
pre-up iwpriv ra0 set AuthMode=WPAPSK
pre-up iwpriv ra0 set EncrypType=TKIP
pre-up iwpriv ra0 set WPAPSK="MyKey"
pre-up ifconfig ra0 up

"MyKey" I created command"
wpa_passphrase 'RESMAN 22-2 tel_0177483333' '1111111111'
##----------------------------------------------------------------------------

# Interface: Sieciowka
iface eth0 inet dhcp
auto eth0

```

And My WiFi works fine :) but I updated Ubuntu (118 packages) restart and WiFi is not working :-(
My ESSID "RESMAN 22-2 tel_0177483333" is correct I used it under WinXP and work before updated Ubuntu.
I searched for 3 days any information on google but is no information when working
I am beginneg Ubuntu user and I am stuck!

(In WindowsXP) ipconfig -all
```

Opis . . . . . . . . . . . . . . :  Ralink RT2500 Wireless LAN Card
Adres fizyczny. . . . . . . . . . : <MyMAC-Address>
DHCP wlaczone . . . . . . . . . . : Tak
Autokonfiguracja wlaczona . . . . : Tak
Adres IP. . . . . . . . . . . . . : 10.4.22.75
Maska podsieci. . . . . . . . . . : 255.255.255.128
Brama domyslna. . . . . . . . . . : 10.4.22.126
Serwer DHCP . . . . . . . . . . . : 10.4.22.126
Serwery DNS . . . . . . . . . . . : 84.38.160.69
                                    84.38.160.77

```

iwconfig ra0
```

ra0       RT2500 Wireless  ESSID:"RESMAN 22-2 tel_0177483333"  
          Mode:Managed  Frequency=2.412 GHz  Bit Rate:11 Mb/s   Tx-Power:0 dBm   
          RTS thr:off   Fragment thr:off
          Link Quality=0/100  Signal level=-120 dBm  Noise level:-197 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

lspci | grep RT
```

05:08.0 Network controller: RaLink RT2500 802.11g Cardbus/mini-PCI (rev 01)

```

iwlist scan
```

ra0       Scan completed :
          Cell 01 - Address: 00:02:6F:23:87:7B
                    Mode:Managed
                    ESSID:"RESMAN 22-2 tel_0177483333"
                    Encryption key:on
                    Channel:10
                    Quality:0/100  Signal level:-67 dBm  Noise level:-196 dBm

```

---

