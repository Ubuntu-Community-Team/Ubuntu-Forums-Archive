---
title: "Intel Corporation Centrino Wireless-N 1000 disconnects when not very far from router"
date: 2014-11-16
forum: Networking &amp; Wireless
---

### Post by Kivrin on 2014-11-16
Hi all. I have a Toshiba Portege R835 that I dual-boot on Ubuntu and Windows 7. A few weeks ago, for no apparent reason, the computer stopped being able to connect to the internet unless it was ridiculously close to the router. This means that all the places where I've been able to connect without problems for years are now dead zones. This occurs everywhere (home, office, campus, random other locations) so it's not just a router issue. Often it's a matter of feet -- I'm connected to the internet ~5 feet from the router, but lose connection if I move 5 feet further away. It doesn't appear to be a loss of *signal* (I still have the bars), but the internet slows to a crawl or refuses to connect. This problem occurs on both Windows and Ubuntu. 

Wireless info below. Thanks!



```

########## wireless info START ##########

Report from: 16 Nov 2014 10:20 EST -0500

Booted last: 16 Nov 2014 08:52 EST -0500

Script from: 20 Sep 2014 23:04 UTC +0000

##### release ###########################

Distributor ID:	Ubuntu
Description:	Ubuntu 14.04.1 LTS
Release:	14.04
Codename:	trusty

##### kernel ############################

Linux 3.13.0-39-generic #66-Ubuntu SMP Tue Oct 28 13:30:27 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Ubuntu

##### lspci #############################


00:19.0 Ethernet controller [0200]: Intel Corporation 82579V Gigabit Network Connection [8086:1503] (rev 04)
	Subsystem: Toshiba America Info Systems Device [1179:0001]
	Kernel driver in use: e1000e

04:00.0 Network controller [0280]: Intel Corporation Centrino Wireless-N 1000 [Condor Peak] [8086:0083]
	Subsystem: Intel Corporation Centrino Wireless-N 1000 BGN [8086:1305]
	Kernel driver in use: iwlwifi

##### lsusb #############################

Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 1bcf:288e Sunplus Innovation Technology Inc. 
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################


##### rfkill ############################

0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no

##### lsmod #############################

iwldvm                232285  0 
mac80211              630653  1 iwldvm
iwlwifi               169932  1 iwldvm
cfg80211              484040  3 iwlwifi,mac80211,iwldvm
wmi                    19177  1 toshiba_acpi

##### interfaces ########################

auto lo
iface lo inet loopback


##### ifconfig ##########################

eth0      Link encap:Ethernet  HWaddr e8:e0:b7:9d:10:54  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:20 Memory:c4800000-c4820000 

wlan0     Link encap:Ethernet  HWaddr 74:e5:0b:a2:af:72  
          inet addr:192.168.0.6  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::76e5:bff:fea2:af72/64 Scope:Link
          inet6 addr: 2604:2000:80a4:df00:409b:954b:42e1:82c/64 Scope:Global
          inet6 addr: 2604:2000:80a4:df00:76e5:bff:fea2:af72/64 Scope:Global
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:69683 errors:0 dropped:0 overruns:0 frame:0
          TX packets:59149 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:53387629 (53.3 MB)  TX bytes:13664832 (13.6 MB)


##### iwconfig ##########################

eth0      no wireless extensions.

lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"TG852G62"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: AC:B3:13:75:58:F0   
          Bit Rate=26 Mb/s   Tx-Power=14 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=70/70  Signal level=-33 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:1155  Invalid misc:24   Missed beacon:0


##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.0.1     0.0.0.0         UG    0      0        0 wlan0
192.168.0.0     0.0.0.0         255.255.255.0   U     9      0        0 wlan0

##### resolv.conf #######################

nameserver 127.0.1.1

##### nm-tool ###########################


NetworkManager Tool

State: connected (global)

- Device: wlan0  [TG852G62 1] --------------------------------------------------
  Type:              802.11 WiFi
  Driver:            iwlwifi
  State:             connected
  Default:           yes
  HW Address:        74:E5:0B:A2:AF:72

  Capabilities:
    Speed:           1 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    Washnasty:       Infra, 00:26:5A:B7:50:D0, Freq 2462 MHz, Rate 54 Mb/s, Strength 49 WPA2
    NETGEAR91:       Infra, E8:FC:AF:95:D5:AF, Freq 2462 MHz, Rate 54 Mb/s, Strength 82 WPA2
    TG1672GD2:       Infra, 8C:09:F4:C7:04:D0, Freq 2462 MHz, Rate 54 Mb/s, Strength 52 WPA2
    *TG852G62:       Infra, AC:B3:13:75:58:F0, Freq 2412 MHz, Rate 54 Mb/s, Strength 87 WPA2
    boweryboys:      Infra, 90:84:0D:E0:CA:DF, Freq 2462 MHz, Rate 54 Mb/s, Strength 50 WPA2
    Shiva:           Infra, DC:9B:9C:F3:1A:F2, Freq 2412 MHz, Rate 54 Mb/s, Strength 57 WPA2
    TaoNet:          Infra, 04:A1:51:D3:29:60, Freq 2412 MHz, Rate 54 Mb/s, Strength 25 WPA2
    TG1672G12:       Infra, 90:1A:CA:FF:1E:10, Freq 2437 MHz, Rate 54 Mb/s, Strength 29 WPA2
    FINSTER:         Infra, C0:3F:0E:B6:2D:8A, Freq 2437 MHz, Rate 54 Mb/s, Strength 32 WPA WPA2
    Fortunately:     Infra, D8:50:E6:CE:DE:90, Freq 2437 MHz, Rate 54 Mb/s, Strength 22 WPA2
    DG1670A22:       Infra, AC:B3:13:AB:12:20, Freq 2412 MHz, Rate 54 Mb/s, Strength 17 WPA2
    The Smiths:      Infra, 28:37:37:46:D9:24, Freq 2412 MHz, Rate 54 Mb/s, Strength 25 WPA2

  IPv4 Settings:
    Address:         192.168.0.6
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.0.1

    DNS:             209.18.47.61
    DNS:             209.18.47.62


- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            e1000e
  State:             unavailable
  Default:           no
  HW Address:        E8:E0:B7:9D:10:54

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off



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

[ifupdown]
managed=false

##### NetworkManager profiles ###########

```

---

### Post by jeremy31 on 2014-11-16
Have you opened the laptop and checked the antenna connections on the card

---

### Post by Kivrin on 2014-11-16
> **jeremy31 said:**
> Have you opened the laptop and checked the antenna connections on the card

Oh, good idea. I haven't, no -- should I just be looking to make sure they are firmly connected, or should I be paying attention to something specific?

---

### Post by Kivrin on 2014-11-16
Aha. The antenna connections/cables look fine, but I unplugged main cable and plugged in the aux cable to the main port -- problem fixed!

---

