---
title: "Wifi Issue with Inspiron 9300 with internal Intel 200bg card"
date: 2014-10-28
forum: Networking &amp; Wireless
---

### Post by orcldba8 on 2014-10-28
I installed ubuntu 14.04 (32.bit) on this PC, back in July 2014.  It worked fine for a while, but around 10/1/14, the wifi stopped working correctly.   I can connect to non-secured networks (Panera, starbucks etc), but I cannot connect to sucured networks.  I get the panel to supply the password, but that just loops and get sback to the same point.   I can see all of the networks in my area in the network manager.

After banging around for a while, trying stuff from this forum and other places without success, 
--I completely re-installed 14.04 earlier today, without using the updates.   still no WPA wifi
--Applied the updates and rebooted.  Still no WPA wifi

I have run several of the diagnostics suggested including the wireless script and will post the results below.


sudo lshw -C network
```
[sudo] password for patrick: 
  *-network:0             
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 02
       serial: 00:12:3f:e6:35:cd
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=2.0 duplex=full ip=192.168.2.17 latency=64 link=yes multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:18 memory:dcffe000-dcffffff
  *-network:1
       description: Wireless interface
       product: PRO/Wireless 2200BG [Calexico2] Network Connection
       vendor: Intel Corporation
       physical id: 3
       bus info: pci@0000:03:03.0
       logical name: eth1
       version: 05
       serial: 00:13:ce:33:85:43
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ipw2200 driverversion=1.2.2kmprq firmware=ABG:9.0.5.27 (Dec 12 2007) latency=64 link=no maxlatency=24 mingnt=3 multicast=yes wireless=IEEE 802.11bg
       resources: irq:17 memory:dcffd000-dcffdfff
patrick@patrick-Inspiron-9300:~$ 
```

patrick@patrick-Inspiron-9300:~$ modinfo ipw2200
```
filename:       /lib/modules/3.13.0-37-generic/kernel/drivers/net/wireless/ipw2x00/ipw2200.ko
firmware:       ipw2200-bss.fw
firmware:       ipw2200-sniffer.fw
firmware:       ipw2200-ibss.fw
license:        GPL
author:         Copyright(c) 2003-2006 Intel Corporation
version:        1.2.2kmprq
description:    Intel(R) PRO/Wireless 2200/2915 Network Driver
srcversion:     6432FDB1497A8B2EC025CB2
alias:          pci:v00008086d00004224sv*sd*bc*sc*i*
alias:          pci:v00008086d00004223sv*sd*bc*sc*i*
alias:          pci:v00008086d00004221sv*sd*bc*sc*i*
alias:          pci:v00008086d00004220sv*sd*bc*sc*i*
alias:          pci:v00008086d0000104Fsv*sd*bc*sc*i*
alias:          pci:v00008086d00001043sv00008086sd00002762bc*sc*i*
alias:          pci:v00008086d00001043sv00008086sd00002761bc*sc*i*
alias:          pci:v00008086d00001043sv00008086sd00002754bc*sc*i*
alias:          pci:v00008086d00001043sv00008086sd00002753bc*sc*i*
alias:          pci:v00008086d00001043sv00008086sd00002752bc*sc*i*
alias:          pci:v00008086d00001043sv00008086sd00002751bc*sc*i*
alias:          pci:v00008086d00001043sv00008086sd00002742bc*sc*i*
alias:          pci:v00008086d00001043sv0000103Csd00002741bc*sc*i*
alias:          pci:v00008086d00001043sv00008086sd00002741bc*sc*i*
alias:          pci:v00008086d00001043sv00008086sd00002732bc*sc*i*
alias:          pci:v00008086d00001043sv00008086sd00002731bc*sc*i*
alias:          pci:v00008086d00001043sv00008086sd00002722bc*sc*i*
alias:          pci:v00008086d00001043sv00008086sd00002721bc*sc*i*
alias:          pci:v00008086d00001043sv00008086sd00002712bc*sc*i*
alias:          pci:v00008086d00001043sv00008086sd00002711bc*sc*i*
alias:          pci:v00008086d00001043sv00008086sd00002702bc*sc*i*
alias:          pci:v00008086d00001043sv00008086sd00002701bc*sc*i*
depends:        cfg80211,libipw,lib80211
intree:         Y
vermagic:       3.13.0-37-generic SMP mod_unload modversions 686 
signer:         Magrathea: Glacier signing key
sig_key:        7A:CF:8E:D9:48:D7:7B:6A:80:F2:4F:59:D5:D8:ED:03:87:AA:B4:26
sig_hashalgo:   sha512
parm:           disable:manually disable the radio (default 0 [radio on]) (int)
parm:           associate:auto associate when scanning (default off) (int)
parm:           auto_create:auto create adhoc network (default on) (int)
parm:           led:enable led control on some systems (default 1 on) (int)
parm:           debug:debug output mask (int)
parm:           channel:channel to limit associate to (default 0 [ANY]) (int)
parm:           rtap_iface:create the rtap interface (1 - create, default 0) (int)
parm:           qos_enable:enable all QoS functionalitis (int)
parm:           qos_burst_enable:enable QoS burst mode (int)
parm:           qos_no_ack_mask:mask Tx_Queue to no ack (int)
parm:           burst_duration_CCK:set CCK burst value (int)
parm:           burst_duration_OFDM:set OFDM burst value (int)
parm:           mode:network mode (0=BSS,1=IBSS,2=Monitor) (int)
parm:           bt_coexist:enable bluetooth coexistence (default off) (int)
parm:           hwcrypto:enable hardware crypto (default off) (int)
parm:           cmdlog:allocate a ring buffer for logging firmware commands (int)
parm:           roaming:enable roaming support (default on) (int)
parm:           antenna:select antenna 1=Main, 3=Aux, default 0 [both], 2=slow_diversity (choose the one with lower background noise) (int)
patrick@patrick-Inspiron-9300:~$ 

```

patrick@patrick-Inspiron-9300:~$ dmesg | grep ipw
```
[   12.570177] libipw: 802.11 data/management/control stack, git-1.1.13
[   12.570182] libipw: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
[   12.810762] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.2.2kmprq
[   12.810767] ipw2200: Copyright(c) 2003-2006 Intel Corporation
[   12.811033] ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection
[   13.628512] ipw2200: Detected geography ZZM (11 802.11bg channels, 0 802.11a channels)
[  284.275778] ipw2200: Failed to send SYSTEM_CONFIG: Already sending a command.
patrick@patrick-Inspiron-9300:~$ 

```

Set the ipw2200.conf as suggested by Chili55
patrick@patrick-Inspiron-9300:~$ gksudo gedit /etc/modprobe.d/ipw2200.conf
```

(gedit:3212): Gtk-WARNING **: Calling Inhibit failed: GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: The name org.gnome.SessionManager was not provided by any .service files

(gedit:3212): Gtk-WARNING **: Calling Inhibit failed: GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: The name org.gnome.SessionManager was not provided by any .service files
patrick@patrick-Inspiron-9300:~$ 
```

--------------------actual file ipw2200.conf
```
options ipw2200 associate=1
```

patrick@patrick-Inspiron-9300:~$ sudo iw reg get
```
country 00:
    (2402 - 2472 @ 40), (3, 20)
    (2457 - 2482 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (2474 - 2494 @ 20), (3, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
    (5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
patrick@patrick-Inspiron-9300:~$ 

```

output from wireless-script


```

########## wireless info START ##########

Report from: 28 Oct 2014 16:31 CDT -0500

Booted last: 28 Oct 2014 15:05 CDT -0500

Script from: 20 Sep 2014 23:04 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.1 LTS
Release:    14.04
Codename:    trusty

##### kernel ############################

Linux 3.13.0-37-generic #64-Ubuntu SMP Mon Sep 22 21:30:01 UTC 2014 i686 i686 i686 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Ubuntu

##### lspci #############################

03:00.0 Ethernet controller [0200]: Broadcom Corporation BCM4401-B0 100Base-TX [14e4:170c] (rev 02)
    Subsystem: Dell Device [1028:0189]
    Kernel driver in use: b44

03:03.0 Network controller [0280]: Intel Corporation PRO/Wireless 2200BG [Calexico2] Network Connection [8086:4220] (rev 05)
    Subsystem: Intel Corporation Dell B130 laptop integrated WLAN [8086:2721]
    Kernel driver in use: ipw2200

##### lsusb #############################

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 002: ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

##### PCMCIA card info ##################

PRODID_1=""
PRODID_2=""
PRODID_3=""
PRODID_4=""
MANFID=0000,0000
FUNCID=255

##### rfkill ############################

0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

##### lsmod #############################

mxm_wmi                12893  1 nouveau
wmi                    18673  2 mxm_wmi,nouveau
ipw2200               136401  0 
libipw                 33144  1 ipw2200
lib80211               14040  2 libipw,ipw2200
dell_laptop            17808  0 
cfg80211              409394  2 libipw,ipw2200
dcdbas                 14448  1 dell_laptop
ssb                    51854  1 b44

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

eth0      Link encap:Ethernet  HWaddr <MAC 'eth0' [IF]>  
          inet addr:192.168.2.17  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::212:3fff:fee6:35cd/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:28030 errors:0 dropped:0 overruns:0 frame:0
          TX packets:21235 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:22420377 (22.4 MB)  TX bytes:3350089 (3.3 MB)
          Interrupt:18 

eth1      Link encap:Ethernet  HWaddr <MAC 'eth1' [IF]>  
          inet6 addr: fe80::213:ceff:fe33:8543/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:14 errors:6 dropped:6 overruns:0 frame:0
          TX packets:38 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1582 (1.5 KB)  TX bytes:5849 (5.8 KB)

##### iwconfig ##########################

lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power=20 dBm   Sensitivity=8/0  
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.2.1     0.0.0.0         UG    0      0        0 eth0
192.168.2.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0

##### resolv.conf #######################

nameserver 127.0.1.1
search Belkin

##### nm-tool ###########################

NetworkManager Tool

State: connected (global)

- Device: eth1 -----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            ipw2200
  State:             disconnected
  Default:           no
  HW Address:        <MAC 'eth1' [IF]>

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 
    belkin.664:      Infra, <MAC 'belkin.664' [AC3]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 100 WPA WPA2
    Dumpsters:       Infra, <MAC 'Dumpsters' [AC5]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 87 WPA WPA2
    HOME-940A:       Infra, <MAC 'HOME-940A' [AN3]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 84 WPA WPA2
    The Patels:      Infra, <MAC 'The Patels' [AC1]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 62 WPA WPA2
    brick:           Infra, <MAC 'brick' [AC7]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 49 WPA
    DIRECT-v7SCX-3400: Infra, <MAC 'DIRECT-v7SCX-3400' [AC4]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 44 WPA2
    Polabear:        Infra, <MAC 'Polabear' [AC8]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 100 WPA WPA2
    belkin.664:      Infra, <MAC 'belkin.664' [AC6]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 100 WPA2
    Rich 2.4:        Infra, <MAC 'Rich 2.4' [AC9]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 89 WPA WPA2
    ltbhome:         Infra, <MAC 'ltbhome' [AC11]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 92 WPA2
    Curly Shirley:   Infra, <MAC 'Curly Shirley' [AC12]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 84 WPA WPA2
    HOME-A2B2:       Infra, <MAC 'HOME-A2B2' [AC14]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 64 WPA WPA2
    Curly Shirley-guest: Infra, <MAC 'Curly Shirley-guest' [AC13]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 79
    NETGEAR52:       Infra, <MAC 'NETGEAR52' [AN14]>, Freq 2422 MHz, Rate 54 Mb/s, Strength 64 WPA2
    2WIRE601:        Infra, <MAC '2WIRE601' [AC2]>, Freq 2427 MHz, Rate 54 Mb/s, Strength 69 WPA WPA2
    HOME-8E12:       Infra, <MAC 'HOME-8E12' [AN16]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 44 WPA WPA2
    NETGEARLOW:      Infra, <MAC 'NETGEARLOW' [AN17]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 62 WPA2

- Device: eth0  [Wired connection 1] -------------------------------------------
  Type:              Wired
  Driver:            b44
  State:             connected
  Default:           yes
  HW Address:        <MAC 'eth0' [IF]>

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.2.17
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.2.1

    DNS:             192.168.2.1

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

[[/etc/NetworkManager/system-connections/brick]] (600 root)
[connection] id=brick | type=802-11-wireless
[802-11-wireless] ssid=brick | mac-address=<MAC 'eth1' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/belkin.664]] (600 root)
[connection] id=belkin.664 | type=802-11-wireless
[802-11-wireless] ssid=belkin.664 | mac-address=<MAC 'eth1' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Dumpsters]] (600 root)
[connection] id=Dumpsters | type=802-11-wireless
[802-11-wireless] ssid=Dumpsters | mac-address=<MAC 'eth1' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Curly Shirley-guest]] (600 root)
[connection] id=Curly Shirley-guest | type=802-11-wireless
[802-11-wireless] ssid=Curly Shirley-guest | mac-address=<MAC 'eth1' [IF]>
[ipv6] method=auto
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/ATTnkTR4Fi]] (600 root)
[connection] id=ATTnkTR4Fi | type=802-11-wireless
[802-11-wireless] ssid=ATTnkTR4Fi | mac-address=<MAC 'eth1' [IF]>
[ipv4] method=auto
[ipv6] method=auto

##### iw reg get ########################

Region: America/Chicago (based on set time zone)

country 00:
    (2402 - 2472 @ 40), (3, 20)
    (2457 - 2482 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (2474 - 2494 @ 20), (3, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
    (5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS

##### iwlist channels ###################

lo        no frequency information.

eth0      no frequency information.

eth1      11 channels in total; available frequencies :
          Channel 01 : 2.412 GHz
          Channel 02 : 2.417 GHz
          Channel 03 : 2.422 GHz
          Channel 04 : 2.427 GHz
          Channel 05 : 2.432 GHz
          Channel 06 : 2.437 GHz
          Channel 07 : 2.442 GHz
          Channel 08 : 2.447 GHz
          Channel 09 : 2.452 GHz
          Channel 10 : 2.457 GHz
          Channel 11 : 2.462 GHz
          Current Frequency=2.462 GHz (Channel 11)

##### iwlist scan #######################

Channel occupancy:

      1   APs on   Frequency:2.412 GHz (Channel 1)
      1   APs on   Frequency:2.427 GHz (Channel 4)
      12   APs on   Frequency:2.462 GHz (Channel 11)

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      Scan completed :
          Cell 01 - Address: <MAC 'The Patels' [AC1]>
                    ESSID:"The Patels"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=61/100  Signal level=-64 dBm  
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    Extra: Last beacon: 212ms ago
          Cell 02 - Address: <MAC '2WIRE601' [AC2]>
                    ESSID:"2WIRE601"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.427 GHz (Channel 4)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=70/100  Signal level=-58 dBm  
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    Extra: Last beacon: 136ms ago
          Cell 03 - Address: <MAC 'belkin.664' [AC3]>
                    ESSID:"belkin.664"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 11 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=89/100  Signal level=-40 dBm  
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    Extra: Last beacon: 268ms ago
          Cell 04 - Address: <MAC 'DIRECT-v7SCX-3400' [AC4]>
                    ESSID:"DIRECT-v7SCX-3400"
                    Protocol:IEEE 802.11g
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Encryption key:on
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Quality=87/100  Signal level=-42 dBm  
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    Extra: Last beacon: 292ms ago
          Cell 05 - Address: <MAC 'Dumpsters' [AC5]>
                    ESSID:"Dumpsters"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=86/100  Signal level=-43 dBm  
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    Extra: Last beacon: 4ms ago
          Cell 06 - Address: <MAC 'belkin.664' [AC6]>
                    ESSID:"belkin.664"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 11 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=77/100  Signal level=-48 dBm  
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    Extra: Last beacon: 388ms ago
          Cell 07 - Address: <MAC 'brick' [AC7]>
                    ESSID:"brick"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=86/100  Signal level=-43 dBm  
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    Extra: Last beacon: 264ms ago
          Cell 08 - Address: <MAC 'Polabear' [AC8]>
                    ESSID:"Polabear"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=76/100  Signal level=-53 dBm  
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    Extra: Last beacon: 528ms ago
          Cell 09 - Address: <MAC 'Rich 2.4' [AC9]>
                    ESSID:"Rich 2.4"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=61/100  Signal level=-64 dBm  
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    Extra: Last beacon: 1720ms ago
          Cell 10 - Address: <MAC '' [AC10]>
                    ESSID:""
                    Protocol:IEEE 802.11g
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 11 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=83/100  Signal level=-47 dBm  
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    Extra: Last beacon: 404ms ago
          Cell 11 - Address: <MAC 'ltbhome' [AC11]>
                    ESSID:"ltbhome"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=67/100  Signal level=-60 dBm  
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    Extra: Last beacon: 924ms ago
          Cell 12 - Address: <MAC 'Curly Shirley' [AC12]>
                    ESSID:"Curly Shirley"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=71/100  Signal level=-57 dBm  
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    Extra: Last beacon: 800ms ago
          Cell 13 - Address: <MAC 'Curly Shirley-guest' [AC13]>
                    ESSID:"Curly Shirley-guest"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=68/100  Signal level=-59 dBm  
                    Extra: Last beacon: 696ms ago
          Cell 14 - Address: <MAC 'HOME-A2B2' [AC14]>
                    ESSID:"HOME-A2B2"
                    Protocol:IEEE 802.11g
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 11 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=65/100  Signal level=-61 dBm  
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    Extra: Last beacon: 916ms ago

##### module infos ######################

[ipw2200]
filename:       /lib/modules/3.13.0-37-generic/kernel/drivers/net/wireless/ipw2x00/ipw2200.ko
firmware:       ipw2200-bss.fw
firmware:       ipw2200-sniffer.fw
firmware:       ipw2200-ibss.fw
license:        GPL
author:         Copyright(c) 2003-2006 Intel Corporation
version:        1.2.2kmprq
description:    Intel(R) PRO/Wireless 2200/2915 Network Driver
srcversion:     6432FDB1497A8B2EC025CB2
depends:        cfg80211,libipw,lib80211
intree:         Y
vermagic:       3.13.0-37-generic SMP mod_unload modversions 686 
signer:         Magrathea: Glacier signing key
sig_key:        7A:CF:8E:D9:48:D7:7B:6A:80:F2:4F:59:D5:D8:ED:03:87:AA:B4:26
sig_hashalgo:   sha512
parm:           disable:manually disable the radio (default 0 [radio on]) (int)
parm:           associate:auto associate when scanning (default off) (int)
parm:           auto_create:auto create adhoc network (default on) (int)
parm:           led:enable led control on some systems (default 1 on) (int)
parm:           debug:debug output mask (int)
parm:           channel:channel to limit associate to (default 0 [ANY]) (int)
parm:           rtap_iface:create the rtap interface (1 - create, default 0) (int)
parm:           qos_enable:enable all QoS functionalitis (int)
parm:           qos_burst_enable:enable QoS burst mode (int)
parm:           qos_no_ack_mask:mask Tx_Queue to no ack (int)
parm:           burst_duration_CCK:set CCK burst value (int)
parm:           burst_duration_OFDM:set OFDM burst value (int)
parm:           mode:network mode (0=BSS,1=IBSS,2=Monitor) (int)
parm:           bt_coexist:enable bluetooth coexistence (default off) (int)
parm:           hwcrypto:enable hardware crypto (default off) (int)
parm:           cmdlog:allocate a ring buffer for logging firmware commands (int)
parm:           roaming:enable roaming support (default on) (int)
parm:           antenna:select antenna 1=Main, 3=Aux, default 0 [both], 2=slow_diversity (choose the one with lower background noise) (int)

[cfg80211]
filename:       /lib/modules/3.13.0-37-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     C2478077E22138832B71659
depends:        
intree:         Y
vermagic:       3.13.0-37-generic SMP mod_unload modversions 686 
signer:         Magrathea: Glacier signing key
sig_key:        7A:CF:8E:D9:48:D7:7B:6A:80:F2:4F:59:D5:D8:ED:03:87:AA:B4:26
sig_hashalgo:   sha512
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

[ssb]
filename:       /lib/modules/3.13.0-37-generic/kernel/drivers/ssb/ssb.ko
license:        GPL
description:    Sonics Silicon Backplane driver
srcversion:     3DE188310F77C566C2E8CB3
depends:        
intree:         Y
vermagic:       3.13.0-37-generic SMP mod_unload modversions 686 
signer:         Magrathea: Glacier signing key
sig_key:        7A:CF:8E:D9:48:D7:7B:6A:80:F2:4F:59:D5:D8:ED:03:87:AA:B4:26
sig_hashalgo:   sha512

##### module parameters #################

[ipw2200]
antenna: 0
associate: 0
auto_create: 1
bt_coexist: 0
burst_duration_CCK: 0
burst_duration_OFDM: 0
channel: 0
cmdlog: 0
debug: 0
disable: 0
hwcrypto: 0
led: 1
mode: 0
qos_burst_enable: 0
qos_enable: 0
qos_no_ack_mask: 0
roaming: 1
rtap_iface: 0

[cfg80211]
cfg80211_disable_40mhz_24ghz: N
ieee80211_regdom: 00

##### /etc/modules ######################

lp

##### modprobe options ##################

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

[/etc/modprobe.d/blacklist-rare-network.conf]
alias net-pf-3 off
alias net-pf-6 off
alias net-pf-9 off
alias net-pf-11 off
alias net-pf-12 off
alias net-pf-19 off
alias net-pf-21 off
alias net-pf-36 off

[/etc/modprobe.d/iwlwifi.conf]
remove iwlwifi \
(/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
&& /sbin/modprobe -r mac80211

[/etc/modprobe.d/mlx4.conf]
softdep mlx4_core post: mlx4_en

##### rc.local ##########################

exit 0

##### pm-utils ##########################

##### udev rules ########################

[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x14e4:0x170c (b44)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# PCI device 0x8086:0x4220 (ipw2200)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth1' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth1"

##### dmesg #############################

[   28.816198] b44 ssb0:0 eth0: Link is up at 100 Mbps, full duplex
[   28.816206] b44 ssb0:0 eth0: Flow control is off for TX and off for RX
[  284.275778] ipw2200: Failed to send SYSTEM_CONFIG: Already sending a command.

########## wireless info END ############
```

HELPPPP
Thanks in advance

---

### Post by slickymaster on 2014-10-28
*Moved to the ***Networking & Wireless*** sub-forum*

---

### Post by orcldba8 on 2014-10-28
Correcting Title.

---

