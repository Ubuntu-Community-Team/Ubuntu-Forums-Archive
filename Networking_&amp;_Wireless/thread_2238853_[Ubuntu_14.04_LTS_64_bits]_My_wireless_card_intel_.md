---
title: "[Ubuntu 14.04 LTS 64 bits] My wireless card intel 7260 isn't detectable"
date: 2014-08-10
forum: Networking &amp; Wireless
---

### Post by Ilumizi on 2014-08-10
Hi! After reading thousands of tutorials about how to make my wireless card work I gave up trying alone and decided to ask for help. Please and thanks!


My info:
```



########## wireless info START ##########


Report from: 10 Aug 2014 11:00 PDT -0700


Script from: 04 Aug 2014 18:47 UTC +0000


##### release #####


Distributor ID:	Ubuntu
Description:	Ubuntu 14.04.1 LTS
Release:	14.04
Codename:	trusty


##### kernel #####


Linux 3.13.0-32-generic #57-Ubuntu SMP Tue Jul 15 03:51:08 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux


Parameters: ro, find_preseed=/preseed.cfg, auto, noprompt, priority=critical, locale=en_US, quiet


##### desktop #####


Ubuntu


##### lspci #####


02:01.0 Ethernet controller [0200]: Intel Corporation 82545EM Gigabit Ethernet Controller (Copper) [8086:100f] (rev 01)
	Subsystem: VMware PRO/1000 MT Single Port Adapter [15ad:0750]
	Kernel driver in use: e1000


##### lsusb #####


Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 004: ID 0e0f:0008 VMware, Inc. 
Bus 002 Device 003: ID 0e0f:0002 VMware, Inc. Virtual USB Hub
Bus 002 Device 002: ID 0e0f:0003 VMware, Inc. Virtual Mouse
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


##### PCMCIA Card Info #####


##### rfkill #####


0: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no


##### lsmod #####


##### interfaces #####


auto lo
iface lo inet loopback


##### ifconfig #####


eth0      Link encap:Ethernet  HWaddr <MAC addr eth0>  
          inet addr:192.168.72.138  Bcast:192.168.72.255  Mask:255.255.255.0
          inet6 addr: fe80::20c:29ff:fee0:72b2/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:37484 errors:0 dropped:0 overruns:0 frame:0
          TX packets:18075 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:53261774 (53.2 MB)  TX bytes:1192300 (1.1 MB)


##### iwconfig #####


eth0      no wireless extensions.


lo        no wireless extensions.


##### route #####


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.72.2    0.0.0.0         UG    0      0        0 eth0
192.168.72.0    0.0.0.0         255.255.255.0   U     1      0        0 eth0


##### resolv.conf #####


nameserver 127.0.1.1
search localdomain


##### nm-tool #####


NetworkManager Tool


State: connected (global)


- Device: eth0  [Wired connection 1] -------------------------------------------
  Type:              Wired
  Driver:            e1000
  State:             connected
  Default:           yes
  HW Address:        <MAC addr eth0>


  Capabilities:
    Carrier Detect:  yes
    Speed:           1000 Mb/s


  Wired Properties
    Carrier:         on


  IPv4 Settings:
    Address:         192.168.72.138
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.72.2


    DNS:             192.168.72.2


##### NetworkManager.state #####


[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true


##### NetworkManager.conf #####


[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq


[ifupdown]
managed=false


##### iw reg get #####


country 00:
	(2402 - 2472 @ 40), (6, 20)
	(2457 - 2482 @ 40), (6, 20), PASSIVE-SCAN, NO-IBSS
	(2474 - 2494 @ 20), (6, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
	(5170 - 5250 @ 160), (6, 20), PASSIVE-SCAN, NO-IBSS
	(5250 - 5330 @ 160), (6, 20), DFS, PASSIVE-SCAN, NO-IBSS
	(5490 - 5730 @ 160), (6, 20), DFS, PASSIVE-SCAN, NO-IBSS


##### iwlist channels #####


eth0      no frequency information.


lo        no frequency information.


##### iwlist scan #####


eth0      Interface doesn't support scanning.


lo        Interface doesn't support scanning.


##### module infos #####


##### module parameters #####


##### /etc/modules #####


lp
rtc


##### blacklists #####


[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci


[/etc/modprobe.d/blacklist.conf]
blacklist evbug
blacklist usbmouse
blacklist usbkbd
blacklist eepro100
blacklist de4x5
blacklist eth1394
blacklist snd_intel8x0m
blacklist snd_aw2
blacklist i2c_i801
blacklist prism54
blacklist bcm43xx
blacklist garmin_gps
blacklist asus_acpi
blacklist snd_pcsp
blacklist pcspkr
blacklist amd76x_edac


##### udev rules #####


egrep: /etc/udev/rules.d/70-persistent-net.rules: No such file or directory


##### dmesg #####


[    4.977791] e1000: Intel(R) PRO/1000 Network Driver - version 7.3.21-k8-NAPI
[    5.351881] e1000 0000:02:01.0 eth0: Intel(R) PRO/1000 Network Connection
[   31.212418] type=1400 audit(1407692029.305:3): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=572 comm="apparmor_parser"
[   31.212735] type=1400 audit(1407692029.305:5): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=572 comm="apparmor_parser"
[   36.743769] type=1400 audit(1407692034.841:15): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=864 comm="apparmor_parser"
[   36.744124] type=1400 audit(1407692034.841:17): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=864 comm="apparmor_parser"


########## wireless info END ############




```

---

### Post by praseodym on 2014-08-10
Check in your BIOS if
[LIST]
[*]
[*]the card is "on" or switchable there
[*]
[*]the network can be booted before the OS
[/LIST]

---

