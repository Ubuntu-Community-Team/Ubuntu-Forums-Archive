---
title: "need help with 802.11n connection"
date: 2008-10-22
forum: Networking &amp; Wireless
---

### Post by tastybrains on 2008-10-22
**[SIZE="3"]HOWTO: Netgear WN121T 802.11n Wireless N Usb adapter[/SIZE]**
[**see my post#2 below**]("http://ubuntuforums.org/showpost.php?p=6016260&postcount=2")



i can't connect to my netgear wn121t but i must be close -  iwconfig can *see* my access point! i had it working before i had to reformat after "upgrading" to 8.04 doh

here's my configuration:
USB device: Netgear WN121T
Driver: ndiswrapper 1.53, netmw245.inf
using: WPA, PSK, TKIP
kernel 2.6.24-21
networkmanager not running

$ndiswrapper -l```
netmw245 : driver installed
	device (0846:7100) present
```
$iwconfig```
$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:"squishy"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:1B:2F:D5:FB:EA   
          Bit Rate=108 Mb/s   Sensitivity=-200 dBm  
          RTS thr=2346 B   Fragment thr=2346 B   
          Power Management:off
          Link Quality:43/100  Signal level:-68 dBm  Noise level:-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

$ifconfig```

eth0      Link encap:Ethernet  HWaddr 00:30:48:70:54:9e  
          inet addr:10.0.0.205  Bcast:10.0.0.255  Mask:255.255.255.0
          inet6 addr: fe80::230:48ff:fe70:549e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:499 errors:0 dropped:0 overruns:0 frame:0
          TX packets:498 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:527131 (514.7 KB)  TX bytes:57143 (55.8 KB)
          Base address:0x4040 Memory:d0300000-d0320000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:1b:2f:31:46:fe  
          inet addr:10.0.0.200  Bcast:10.255.255.255  Mask:255.0.0.0
          inet6 addr: fe80::21b:2fff:fe31:46fe/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:130 errors:0 dropped:0 overruns:0 frame:0
          TX packets:130 errors:0 dropped:31 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:14690 (14.3 KB)  TX bytes:18070 (17.6 KB)

```
$route```

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
10.0.0.0        *               255.255.255.0   U     0      0        0 eth0
link-local      *               255.255.0.0     U     1000   0        0 wlan0
10.0.0.0        *               255.0.0.0       U     0      0        0 wlan0
default         10.0.0.1        0.0.0.0         UG    0      0        0 eth0
default         10.0.0.1        0.0.0.0         UG    100    0        0 wlan0
```
$iwconfig```
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:1B:2F:D5:FB:EA
                    ESSID:"squishy"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:40/100  Signal level:-70 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK

```
$ sudo lshw -C network```

  *-network               
       description: Ethernet interface
       product: 82545EM Gigabit Ethernet Controller (Copper)
       vendor: Intel Corporation
       physical id: 3
       bus info: pci@0000:03:03.0
       logical name: eth0
       version: 01
       serial: 00:30:48:70:54:9e
       size: 1GB/s
       capacity: 1GB/s

       width: 64 bits
       clock: 66MHz
       capabilities: pm pcix msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000 driverversion=7.3.20-k2-NAPI duplex=full firmware=N/A ip=10.0.0.205 latency=64 link=yes mingnt=255 module=e1000 multicast=yes port=twisted pair speed=1GB/s
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:1b:2f:31:46:fe
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+netmw245 driverversion=1.53+Marvell,11/27/2006,1.0.4.9 ip=10.0.0.200 link=yes multicast=yes wireless=IEEE 802.11g

```

$ sudo more /etc/network/interfaces```

auto lo
iface lo inet loopback


iface wlan0 inet static
address 10.0.0.200
gateway 10.0.0.1
dns-nameservers 10.0.0.1
netmask 255.0.0.0
wpa-ap-scan 1
wpa-pairwise TKIP
wpa-group TKIP
wpa-psk de17e43e0f6497f99cdc567301223709e2e867d9b4b01c0fbcd6ac5751535ed3
wpa-driver wext
wpa-key-mgmt WPA-PSK
wpa-proto WPA
wpa-ssid squishy


auto wlan0

``` i am not able to ping the router, 10.0.0.1, nor the outside world. it seems the order of commands is important in bringing the interface up. i've tried this a number of ways and get the same No DHCPOFFERS message:
```
sudo ifconfig wlan0 
  sudo dhclient -r wlan0 
  sudo ifconfig up
  sudo route add default gw 10.0.0.1
  sudo iwconfig wlan0 essid "squishy"
  sudo iwconfig wlan0 mode Managed
  sudo dhclient wlan0

results in this message:

There is already a pid file /var/run/dhclient.pid with pid 134519072
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/wlan0/00:1b:2f:31:46:fe
Sending on   LPF/wlan0/00:1b:2f:31:46:fe
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
```

what else should i try? anything else i need to post? when i get this going i'd like to sticky this or add it to the ubuntu wiki as there are other people having probs getting started with this device and i know it works if you enter the commands in the magic order :)

thanks, tastybrains

---

### Post by tastybrains on 2008-10-22
holy crap i figured it out and can finally contribute something to the linux community!!!:guitar: 

###############################################################
HOWTO: GET THE NETGEAR WN121T, USB 802.11N WORKING
~~~~ brought to you by the Ubuntu Community & tastybrains
###############################################################

1) don't panic

2)remove ndiswrapper if it came with your distro and install from source. [the ubuntu ndiswrapper wiki has great info]("https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper")

3) download the netmw245.inf (Marvell driver) 
load it into ndiswrapper using the guide above

4) [follow these steps]("http://ubuntuforums.org/showthread.php?t=318539") to configure your /etc/network/interfaces file 

i'm using a static IP so here is my interfaces file:
```
auto lo
iface lo inet loopback

auto wlan0
iface wlan0 inet static
address 10.0.0.200
gateway 10.0.0.1
dns-nameservers 10.0.0.1
netmask 255.0.0.0
wpa-driver wext
wpa-ssid myessisd
wpa-ap-scan 1
wpa-pairwise TKIP
wpa-group TKIP
wpa-psk 61d3c8ab0f51482e909etc
wpa-key-mgmt WPA-PSK
wpa-proto WPA

```

sudo killall NetworkManager
sudo killall NetworkManagerDispatcher
sudo killall dhcdbd
sudo ifconfig wlan0 down
sudo dhclient -r wlan0
sudo ifconfig wlan0 <insert your ip> netmask <insert your netmask> up
sudo route add default gw <insert your gateway>
sudo iwconfig wlan0 mode Managed
sudo iwconfig wlan0 essid "<insert your gateway>"
sudo dhclient wlan0

should result in:

There is already a pid file /var/run/dhclient.pid with pid 134519072
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/wlan0/00:1b:2f:31:46:fe
Sending on   LPF/wlan0/00:1b:2f:31:46:fe
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 5
DHCPOFFER of 10.0.0.200 from 10.0.0.1
DHCPREQUEST of 10.0.0.200 on wlan0 to 255.255.255.255 port 67
DHCPACK of 10.0.0.200 from 10.0.0.1
bound to 10.0.0.200 -- renewal in 34752 seconds.

sweet! crazy as it sounds it was the iwconfig in the right order that did the trick (i tried at several dozen ways over the last couple nights...)

guides used to understand what these commands mean:
[How To: Manual Network Configuration without the need for Network Manager]("http://ubuntuforums.org/showthread.php?t=684495")

[HOWTO: Wireless Security - WPA1, WPA2, LEAP, etc.]("http://ubuntuforums.org/showthread.php?t=318539")

---

### Post by kooldino on 2008-11-22
Ok, I installed the ndiswrapper as well as the gtk frontend for it via apt-get.

I couldn't find "netmw245.inf", so what I tried to do was install the latest Netgear Software via WINE and grab the necessary files from there.  I couldn't find them this way though.

What do I do now?

---

