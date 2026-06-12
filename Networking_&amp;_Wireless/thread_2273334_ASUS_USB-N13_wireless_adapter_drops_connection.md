---
title: "ASUS USB-N13 wireless adapter drops connection"
date: 2015-04-12
forum: Networking &amp; Wireless
---

### Post by paul142 on 2015-04-12
Just loaded Xubuntu on my Dell Dimension 9200 desktop and all seems ok except I lose my connection to the internet frequently. My wifi connection shows clearly I'm still connected but I have to disconnect and re-enable wifi to get it to work again. Here is the output results from the wireless troubleshooting script, any help is appreciated:

```

########## wireless info START ##########

Report from: 12 Apr 2015 10:22 EDT -0400

Booted last: 12 Apr 2015 09:38 EDT -0400

Script from: 06 Apr 2015 17:23 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.2 LTS
Release:    14.04
Codename:    trusty

##### kernel ############################

Linux 3.16.0-34-generic #45~14.04.1-Ubuntu SMP Tue Mar 24 11:13:52 UTC 2015 i686 i686 i686 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Xubuntu

##### lspci #############################

00:19.0 Ethernet controller [0200]: Intel Corporation 82566DC Gigabit Network Connection [8086:104b] (rev 02)
    Subsystem: Dell Device [1028:01db]
    Kernel driver in use: e1000e

##### lsusb #############################

Bus 002 Device 003: ID 0b05:17ab ASUSTek Computer, Inc. USB-N13 802.11n Network Adapter (rev. B1) [Realtek RTL8192CU]
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 002: ID 04f2:0111 Chicony Electronics Co., Ltd KU-9908 Keyboard
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 05dc:a81d Lexar Media, Inc. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 002: ID 05b8:3166 Agiler, Inc. 
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

##### lsmod #############################

rtl8192cu              62597  0 
rtl_usb                18072  1 rtl8192cu
rtlwifi                53487  2 rtl_usb,rtl8192cu
rtl8192c_common        47340  1 rtl8192cu
mac80211              559049  3 rtl_usb,rtlwifi,rtl8192cu
cfg80211              418839  2 mac80211,rtlwifi
mxm_wmi                12893  1 nouveau
wmi                    18689  2 mxm_wmi,nouveau

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

eth0      Link encap:Ethernet  HWaddr <MAC 'eth0' [IF]>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:21 Memory:dffe0000-e0000000 

wlan0     Link encap:Ethernet  HWaddr <MAC 'wlan0' [IF]>  
          inet addr:10.0.0.6  Bcast:10.0.0.255  Mask:255.255.255.0
          inet6 addr: fe80::3285:a9ff:fef3:c4af/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:23139 errors:0 dropped:0 overruns:0 frame:0
          TX packets:18667 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:13660844 (13.6 MB)  TX bytes:6618426 (6.6 MB)

##### iwconfig ##########################

lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"HOME"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: <MAC 'HOME' [AC1]>   
          Bit Rate=72.2 Mb/s   Tx-Power=20 dBm   
          Retry short limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          Link Quality=42/70  Signal level=-68 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:7   Missed beacon:0

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         10.0.0.1        0.0.0.0         UG    0      0        0 wlan0
10.0.0.0        0.0.0.0         255.255.255.0   U     9      0        0 wlan0

##### resolv.conf #######################

nameserver 127.0.1.1

##### NetworkManager info ###############

NetworkManager Tool

State: connected (global)

- Device: wlan0  [HOME] ------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            rtl8192cu
  State:             connected
  Default:           yes
  HW Address:        <MAC 'wlan0' [IF]>

  Capabilities:
    Speed:           72 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    HOME-7944-2.4:   Infra, <MAC 'HOME-7944-2.4' [AC7]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 54 WPA WPA2
    TOWN Home:    Infra, <MAC 'TOWN Home' [AN2]>, Freq 2422 MHz, Rate 54 Mb/s, Strength 44 WPA WPA2
    HP-Print-92-ENVY 4500 series: Infra, <MAC 'HP-Print-92-ENVY 4500 series' [AC2]>, Freq 2422 MHz, Rate 54 Mb/s, Strength 4 WPA2
    belkin.366:      Infra, <MAC 'belkin.366' [AC4]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 20 WPA WPA2
    HOME:            Infra, <MAC 'HOME' [AC3]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 17 WPA WPA2
    xfinitywifi:     Infra, <MAC 'xfinitywifi' [AC6]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 74
    xfinitywifi:     Infra, <MAC 'xfinitywifi' [AC9]>, Freq 2422 MHz, Rate 54 Mb/s, Strength 52
    *HOME:         Infra, <MAC 'HOME' [AC1]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 52 WPA WPA2
    default:         Infra, <MAC 'default' [AN9]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 4
    HOME-BA25:       Infra, <MAC 'HOME-BA25' [AN10]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 4 WPA WPA2
    8J6CK:           Infra, <MAC '8J6CK' [AN11]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 4 WPA2

  IPv4 Settings:
    Address:         10.0.0.6
    Prefix:          24 (255.255.255.0)
    Gateway:         10.0.0.1

    DNS:             75.75.75.75
    DNS:             75.75.76.76

- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            e1000e
  State:             unavailable
  Default:           no
  HW Address:        <MAC 'eth0' [IF]>

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

[[/etc/NetworkManager/system-connections/HOME]] (600 root)
[connection] id=HOME | type=802-11-wireless
[802-11-wireless] ssid=HOME | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

##### iw reg get ########################

Region: America/New_York (based on set time zone)

country 00:
    (2402 - 2472 @ 40), (3, 20)
    (2457 - 2482 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (2474 - 2494 @ 20), (3, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
    (5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS

##### iwlist channels ###################

lo        no frequency information.

eth0      no frequency information.

wlan0     11 channels in total; available frequencies :
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

      2   APs on   Frequency:2.412 GHz (Channel 1)
      2   APs on   Frequency:2.422 GHz (Channel 3)
      5   APs on   Frequency:2.462 GHz (Channel 11)

wlan0     Scan completed :
          Cell 01 - Address: <MAC 'HOME' [AC1]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=36/70  Signal level=-74 dBm  
                    Encryption key:on
                    ESSID:"HOME"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000005a406c0e14
                    Extra: Last beacon: 24ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC 'HP-Print-92-ENVY 4500 series' [AC2]>
                    Channel:3
                    Frequency:2.422 GHz (Channel 3)
                    Quality=20/70  Signal level=-90 dBm  
                    Encryption key:on
                    ESSID:"HP-Print-92-ENVY 4500 series"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000020f72957842
                    Extra: Last beacon: 1368ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: <MAC 'HOME' [AC3]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=12/70  Signal level=-98 dBm  
                    Encryption key:on
                    ESSID:"HOME"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000007d0f107640
                    Extra: Last beacon: 1708ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 04 - Address: <MAC 'belkin.366' [AC4]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=36/70  Signal level=-74 dBm  
                    Encryption key:on
                    ESSID:"belkin.366"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000006a55bb7e32
                    Extra: Last beacon: 1356ms ago
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 05 - Address: <MAC '

```

---

### Post by jeremy31 on 2015-04-12
Have you tried this [https://github.com/pvaret/rtl8192cu-fixes](https://github.com/pvaret/rtl8192cu-fixes)

Instructions are on the page

---

### Post by markohrastovec on 2015-04-12
rtl8192cu driver supplied with the kernel is known to drop connections. There is already a link to one of many fixed drivers posted. I am using this fix [https://github.com/dz0ny/rt8192cu/](https://github.com/dz0ny/rt8192cu/).

However, I have been using a fixed rtl8192cu driver for about 6 months now without any problem. Suddenly, two weeks ago the drivers started to drop connection. I tried many drivers and nothing helps. I tought the USB wifi dongle broke. So I bought another one and unlucky as I am I bought a one with bad reception (no antenna) but it works out of the box. Because the reception was bad I bought another one with antenna. And go figure. It is a dongle with rtl8192cu chipset. It proved that nothing is wrong with my original rtl8192cu. I still don't know what is wrong with the drivers and why it suddenly stopped working???

---

### Post by paul142 on 2015-04-12
> **jeremy31 said:**
> Have you tried this [https://github.com/pvaret/rtl8192cu-fixes](https://github.com/pvaret/rtl8192cu-fixes)

Instructions are on the page

I just ran your suggested fix, and thank you by the way, one thing off the bat is my wifi speed doubled from 74mb to 144mb! Thats worth it right there thanks! I'll play awhile and see if the connection holds steady then we'll know if the problem is fixed thanks! I'll report back shortly.

---

### Post by paul142 on 2015-04-12
I think the problem is fixed! Its fast, its consistent, what more can I ask for! Thank you for the help.

---

