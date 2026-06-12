---
title: "AWUSO36h wireless adapter not working properly"
date: 2015-05-10
forum: Networking &amp; Wireless
---

### Post by adhd2 on 2015-05-10
So i purchased a AWUS036H wireless adapter for my macbook which is currently running BackBox, and everywhere i read that no drivers are needed, its just plug and play. well i guess that is true, but my wifi connection is HORRIBLE. Even now when im 10 feet from my own router, its so slow. It picks up ALOT of ESSID's but my connection is slow. and on the notification bar, its showing full bars.

---

### Post by wildmanne39 on 2015-05-10
Hi, please click on the wireless script in my signature and follow the directions for running the script and posting the results here. 
Thanks

---

### Post by adhd2 on 2015-05-11
```
########## wireless info START ##########


Report from: 10 May 2015 23:36 PDT -0700


Booted last: 10 May 2015 23:12 PDT -0700


Script from: 30 Apr 2015 17:23 UTC +0000


##### release ###########################


Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.2 LTS
Release:    14.04
Codename:    trusty


##### kernel ############################


Linux 3.16.0-37-generic #51~14.04.1-Ubuntu SMP Wed May 6 15:23:14 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux


Parameters: ro, quiet, splash, vt.handoff=7


##### desktop ###########################


BackBox


##### lspci #############################


02:00.0 Ethernet controller [0200]: Broadcom Corporation NetXtreme BCM57765 Gigabit Ethernet PCIe [14e4:16b4] (rev 10)
    Subsystem: Broadcom Corporation NetXtreme BCM57765 Gigabit Ethernet PCIe [14e4:16b4]
    Kernel driver in use: tg3


03:00.0 Network controller [0280]: Broadcom Corporation BCM4331 802.11a/b/g/n [14e4:4331] (rev 02)
    Subsystem: Apple Inc. AirPort Extreme [106b:00d6]
    Kernel driver in use: wl


##### lsusb #############################


Bus 002 Device 003: ID 05ac:8242 Apple, Inc. Built-in IR Receiver
Bus 002 Device 002: ID 0424:2513 Standard Microsystems Corp. 2.0 Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 05ac:8509 Apple, Inc. FaceTime HD Camera
Bus 001 Device 009: ID 0bda:8187 Realtek Semiconductor Corp. RTL8187 Wireless Adapter
Bus 001 Device 005: ID 05ac:0252 Apple, Inc. Internal Keyboard/Trackpad (ANSI)
Bus 001 Device 008: ID 05ac:821a Apple, Inc. Bluetooth Host Controller
Bus 001 Device 004: ID 0a5c:4500 Broadcom Corp. BCM2046B1 USB 2.0 Hub (part of BCM2046 Bluetooth)
Bus 001 Device 002: ID 0424:2513 Standard Microsystems Corp. 2.0 Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


##### PCMCIA card info ##################


##### rfkill ############################


0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
2: brcmwl-0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
3: phy1: Wireless LAN
    Soft blocked: no
    Hard blocked: no


##### lsmod #############################


rtl8187                64924  0 
mac80211              652718  1 rtl8187
eeprom_93cx6           13344  1 rtl8187
wl                   6367833  0 
cfg80211              494362  3 wl,mac80211,rtl8187


##### interfaces ########################


auto lo
iface lo inet loopback


##### ifconfig ##########################


eth0      Link encap:Ethernet  HWaddr <MAC 'eth0' [IF]>  
          inet addr:192.168.0.3  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::3e07:54ff:fe21:7a81/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:109844 errors:0 dropped:0 overruns:0 frame:0
          TX packets:63035 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:140009808 (140.0 MB)  TX bytes:19572623 (19.5 MB)
          Interrupt:16 


wlan0     Link encap:Ethernet  HWaddr <MAC 'wlan0' [IF]>  
          inet addr:192.168.0.10  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::2c0:caff:fe6d:fe21/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:459 errors:0 dropped:0 overruns:0 frame:0
          TX packets:50 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:45873 (45.8 KB)  TX bytes:11863 (11.8 KB)


wlan1     Link encap:Ethernet  HWaddr <MAC 'wlan1' [IF]>  
          inet addr:192.168.0.11  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::62c5:47ff:fe8b:3026/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2261 errors:0 dropped:0 overruns:0 frame:5419
          TX packets:78 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:153351 (153.3 KB)  TX bytes:17980 (17.9 KB)
          Interrupt:17 


##### iwconfig ##########################


eth0      no wireless extensions.


lo        no wireless extensions.


wlan0     IEEE 802.11bg  ESSID:"A269D3"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: <MAC 'A269D3' [AC1]>   
          Bit Rate=48 Mb/s   Tx-Power=20 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=70/70  Signal level=-28 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:5  Invalid misc:22   Missed beacon:0


wlan1     IEEE 802.11abg  ESSID:"A269D3"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: <MAC 'A269D3' [AC1]>   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          


##### route #############################


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.0.1     0.0.0.0         UG    0      0        0 eth0
192.168.0.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0
192.168.0.0     0.0.0.0         255.255.255.0   U     9      0        0 wlan1
192.168.0.0     0.0.0.0         255.255.255.0   U     9      0        0 wlan0


##### resolv.conf #######################


nameserver 127.0.1.1


##### NetworkManager info ###############


NetworkManager Tool


State: connected (global)


- Device: wlan0  [Wi-Fi connection 1] ------------------------------------------
  Type:              802.11 WiFi
  Driver:            rtl8187
  State:             connected
  Default:           no
  HW Address:        <MAC 'wlan0' [IF]>


  Capabilities:
    Speed:           48 Mb/s


  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes


  Wireless Access Points (* = current AP)
    2WIRE668:        Infra, <MAC '2WIRE668' [AC6]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 72 WPA WPA2
    Samsung Galaxy S II_3592: Infra, <MAC 'Samsung Galaxy S II_3592' [AC2]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 65 WPA2
    29aa37:          Infra, <MAC '29aa37' [AC5]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 62 WPA WPA2
    wenzel2013:      Infra, <MAC 'wenzel2013' [AN4]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 59 WPA WPA2
    2WIRE447:        Infra, <MAC '2WIRE447' [AN5]>, Freq 2442 MHz, Rate 54 Mb/s, Strength 57 WPA WPA2
    HP-Print-FB-Officejet 6600: Infra, <MAC 'HP-Print-FB-Officejet 6600' [AC4]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 54 WPA2
    HP-Print-AD-Officejet 6800: Infra, <MAC 'HP-Print-AD-Officejet 6800' [AC3]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 99
    *A269D3:         Infra, <MAC 'A269D3' [AC1]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 87 WPA WPA2
    A-Blast_FREE_WiFi: Infra, <MAC 'A-Blast_FREE_WiFi' [AN9]>, Freq 2432 MHz, Rate 54 Mb/s, Strength 49
    linksys:         Infra, <MAC 'linksys' [AN10]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 55 WPA
    2WIRE077:        Infra, <MAC '2WIRE077' [AN11]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 55 WPA WPA2


  IPv4 Settings:
    Address:         192.168.0.10
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.0.1


    DNS:             68.105.28.12
    DNS:             68.105.29.12
    DNS:             68.105.28.11


- Device: wlan1  [Wi-Fi connection 1] ------------------------------------------
  Type:              802.11 WiFi
  Driver:            wl
  State:             connected
  Default:           no
  HW Address:        <MAC 'wlan1' [IF]>


  Capabilities:
    Speed:           78 Mb/s


  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes


  Wireless Access Points (* = current AP)
    *A269D3:         Infra, <MAC 'A269D3' [AC1]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 67 WPA WPA2
    Samsung Galaxy S II_3592: Infra, <MAC 'Samsung Galaxy S II_3592' [AC2]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 37 WPA2
    29aa37:          Infra, <MAC '29aa37' [AC5]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 27 WPA WPA2
    HP-Print-FB-Officejet 6600: Infra, <MAC 'HP-Print-FB-Officejet 6600' [AC4]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 24 WPA2
    HP-Print-AD-Officejet 6800: Infra, <MAC 'HP-Print-AD-Officejet 6800' [AC3]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 77


  IPv4 Settings:
    Address:         192.168.0.11
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.0.1


    DNS:             68.105.28.12
    DNS:             68.105.29.12
    DNS:             68.105.28.11


- Device: eth0  [Wired connection 1] -------------------------------------------
  Type:              Wired
  Driver:            tg3
  State:             connected
  Default:           yes
  HW Address:        <MAC 'eth0' [IF]>


  Capabilities:
    Carrier Detect:  yes
    Speed:           1000 Mb/s


  Wired Properties
    Carrier:         on


  IPv4 Settings:
    Address:         192.168.0.3
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.0.1


    DNS:             68.105.28.12
    DNS:             68.105.29.12
    DNS:             68.105.28.11
```

---

### Post by adhd2 on 2015-05-11
```
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


[[/etc/NetworkManager/system-connections/Wi-Fi connection 1]] (600 root)
[connection] id=Wi-Fi connection 1 | type=802-11-wireless
[802-11-wireless] ssid=A269D3
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/belkin.f23 1]] (600 root)
[connection] id=belkin.f23 1 | type=802-11-wireless | permissions=user:seph80hd:;
[802-11-wireless] ssid=belkin.f23 | mac-address=<MAC 'wlan1' [IF]>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/belkin.f23]] (600 root)
[connection] id=belkin.f23 | type=802-11-wireless
[802-11-wireless] ssid=belkin.f23 | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto


##### iw reg get ########################


Region: America/Los_Angeles (based on set time zone)


country 00:
    (2402 - 2472 @ 40), (3, 20)
    (2457 - 2482 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (2474 - 2494 @ 20), (3, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
    (5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS


##### iwlist channels ###################


eth0      no frequency information.


lo        no frequency information.


wlan0     14 channels in total; available frequencies :
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
          Channel 12 : 2.467 GHz
          Channel 13 : 2.472 GHz
          Channel 14 : 2.484 GHz
          Current Frequency:2.437 GHz (Channel 6)


wlan1     26 channels in total; available frequencies :
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
          Channel 12 : 2.467 GHz
          Channel 13 : 2.472 GHz
          Channel 14 : 2.484 GHz
          Channel 36 : 5.18 GHz
          Channel 38 : 5.19 GHz
          Channel 40 : 5.2 GHz
          Channel 42 : 5.21 GHz
          Channel 44 : 5.22 GHz
          Channel 46 : 5.23 GHz
          Channel 48 : 5.24 GHz
          Channel 149 : 5.745 GHz
          Channel 153 : 5.765 GHz
          Channel 157 : 5.785 GHz
          Channel 161 : 5.805 GHz
          Channel 165 : 5.825 GHz
          Current Frequency:2.437 GHz (Channel 6)


##### iwlist scan #######################


Channel occupancy:


      2   APs on   Frequency:2.412 GHz (Channel 1)
      4   APs on   Frequency:2.437 GHz (Channel 6)


eth0      Interface doesn't support scanning.


wlan0     Interface doesn't support scanning : Device or resource busy


lo        Interface doesn't support scanning.


wlan1     Scan completed :
          Cell 01 - Address: <MAC 'A269D3' [AC1]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=61/70  Signal level=-49 dBm  
                    Encryption key:on
                    ESSID:"A269D3"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 76ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC 'Samsung Galaxy S II_3592' [AC2]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=32/70  Signal level=-78 dBm  
                    Encryption key:on
                    ESSID:"Samsung Galaxy S II_3592"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 76ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: <MAC 'HP-Print-AD-Officejet 6800' [AC3]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=55/70  Signal level=-55 dBm  
                    Encryption key:off
                    ESSID:"HP-Print-AD-Officejet 6800"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 76ms ago
          Cell 04 - Address: <MAC 'HP-Print-FB-Officejet 6600' [AC4]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=24/70  Signal level=-86 dBm  
                    Encryption key:on
                    ESSID:"HP-Print-FB-Officejet 6600"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 10320ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 05 - Address: <MAC '29aa37' [AC5]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=26/70  Signal level=-84 dBm  
                    Encryption key:on
                    ESSID:"29aa37"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 10320ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 06 - Address: <MAC '2WIRE668' [AC6]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=35/70  Signal level=-75 dBm  
                    Encryption key:on
                    ESSID:"2WIRE668"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 76ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
```

---

### Post by Bucky Ball on 2015-05-11
Please use [code] tags. See last link in my signature for how. Thanks.

---

### Post by wildmanne39 on 2015-05-11
It is hard to tell from what you posted what is going on because the whole file is not there and you have two drivers loaded.
What is wrong with the internal card? usually they work pretty well.
If you do want to use just the usb adapter then run this command in the terminal:
```
sudo apt-get purge bcmwl-kernel-source
```
if you want to troubleshoot the internal device then unplug the usb adapter and make sure the drivers for it is not loaded then with ethernet disabled run the script again.

Please following the directions in my signature for using code tags, and please edit your previous post and add code tags to them.
Thanks

---

