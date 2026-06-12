---
title: "LAN stopped working WiFi still OK. Ubuntu 14.04 64 bit"
date: 2016-01-12
forum: Networking &amp; Wireless
---

### Post by john509 on 2016-01-12
I posted this too soon: The problem was elsewhere! Just in case it helps someone else: I rebooted (unplugged and replugged) the TP-Link Powerlan adapter and my ehternet connection is working again. I had already rebooted the powerlan adapter at my my end but I hadn't done the same at router end. Just gave it a try and it solved the problem.

You don't need to respond to the problem below anymore. Thanks anyway.

----------------------------


Hello everyone,

I have finally made the definite move to Ubuntu about 6 months ago and I am loving it so far. No U-Turns here!

However I have hit a very strange issue, in the sense that, it happened without any obvious reason like an update or change, just out of the blue, literally in the middle of browsing:

My ethernet connection stopped working.. just like that!

Thankfully I have enabled my wireless card and my connection was restored.

I have tried a couple of things I have read on forums here but frankly I do not know really know what I am doing.

Can anyone please help me? I copy the  the output of wireless-info file further below.

Any guidance will be much appreciated.

Thanks
John

```

########## wireless info START ##########

Report from: 12 Jan 2016 18:50 CET +0100

Booted last: 12 Jan 2016 17:41 CET +0100

Script from: 27 Sep 2015 00:34 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.3 LTS
Release:    14.04
Codename:    trusty

##### kernel ############################

Linux 3.19.0-43-generic #49~14.04.1-Ubuntu SMP Thu Dec 31 15:44:49 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash

##### desktop ###########################

Ubuntu

##### lspci #############################

02:00.0 Ethernet controller [0200]: Qualcomm Atheros Attansic L1 Gigabit Ethernet [1969:1048] (rev b0)
    Subsystem: ASUSTeK Computer Inc. P5KPL-VM Motherboard [1043:8226]
    Kernel driver in use: atl1

05:02.0 Network controller [0280]: Ralink corp. RT2561/RT61 802.11g PCI [1814:0301]
    Subsystem: Ralink corp. EW-7108PCg/EW-7128g [1814:2561]
    Kernel driver in use: rt61pci

##### lsusb #############################

Bus 004 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 010 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 009 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 0480:a207 Toshiba America Info. Systems, Inc. 
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 005: ID 05ac:0250 Apple, Inc. Aluminium Keyboard (ISO)
Bus 003 Device 004: ID 05ac:1006 Apple, Inc. Hub in Aluminum Keyboard
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 002: ID 0458:001b KYE Systems Corp. (Mouse Systems) 
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 002: ID 04e8:326c Samsung Electronics Co., Ltd ML-2010P Mono Laser Printer
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

##### lsmod #############################

rt61pci                32768  0 
rt2x00pci              16384  1 rt61pci
rt2x00mmio             16384  1 rt61pci
rt2x00lib              57344  3 rt61pci,rt2x00pci,rt2x00mmio
mac80211              708608  2 rt2x00lib,rt2x00pci
cfg80211              524288  2 mac80211,rt2x00lib
eeprom_93cx6           16384  1 rt61pci
crc_itu_t              16384  1 rt61pci

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

eth0      Link encap:Ethernet  HWaddr <MAC 'eth0' [IF]>  
          inet6 addr: fe80::<IP6 'eth0' [IF]>/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:14918 errors:0 dropped:0 overruns:0 frame:0
          TX packets:61 errors:0 dropped:0 overruns:0 carrier:1
          collisions:0 txqueuelen:1000 
          RX bytes:897005 (897.0 KB)  TX bytes:14741 (14.7 KB)

wlan0     Link encap:Ethernet  HWaddr <MAC 'wlan0' [IF]>  
          inet addr:192.168.2.46  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::<IP6 'wlan0' [IF]>/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:97675 errors:0 dropped:0 overruns:0 frame:0
          TX packets:65219 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:127066625 (127.0 MB)  TX bytes:19043361 (19.0 MB)

##### iwconfig ##########################

eth0      no wireless extensions.

lo        no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:"homehub"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: <MAC 'homehub' [AC1]>   
          Bit Rate=24 Mb/s   Tx-Power=27 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=68/70  Signal level=-42 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:23  Invalid misc:877   Missed beacon:0

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.2.1     0.0.0.0         UG    0      0        0 wlan0
192.168.2.0     0.0.0.0         255.255.255.0   U     9      0        0 wlan0

##### resolv.conf #######################

nameserver 127.0.1.1
search Belkin

##### network managers ##################

Installed:

    NetworkManager

Running:

root       863     1  0 17:41 ?        00:00:00 NetworkManager

##### NetworkManager info ###############

NetworkManager Tool

State: connected (global)

- Device: wlan0  [homehub] -----------------------------------------------------
  Type:              802.11 WiFi
  Driver:            rt61pci
  State:             connected
  Default:           yes
  HW Address:        <MAC 'wlan0' [IF]>

  Capabilities:
    Speed:           24 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    FRITZ!Box Fon WLAN 7390: Infra, <MAC 'FRITZ!Box Fon WLAN 7390' [AC3]>, Freq 2452 MHz, Rate 54 Mb/s, Strength 40 WPA WPA2
    *homehub:        Infra, <MAC 'homehub' [AC1]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 80 WPA WPA2
    Blumengarten:    Infra, <MAC 'Blumengarten' [AN3]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 30 WPA2
    o2-WLAN69:       Infra, <MAC 'o2-WLAN69' [AC2]>, Freq 2432 MHz, Rate 54 Mb/s, Strength 34 WPA2

  IPv4 Settings:
    Address:         192.168.2.46
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.2.1

    DNS:             192.168.2.1

- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            atl1
  State:             disconnected
  Default:           no
  HW Address:        <MAC 'eth0' [IF]>

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

##### NetworkManager.state ##############

[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true

##### NetworkManager.conf ###############

[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq

no-auto-default=<MAC 'eth0' [IF]>,

[ifupdown]
managed=false

##### NetworkManager profiles ###########

[[/etc/NetworkManager/system-connections/homehub]] (600 root)
[connection] id=homehub | type=802-11-wireless
[802-11-wireless] ssid=homehub | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=ignore

```

---

