---
title: "AWUS036H disconnects"
date: 2015-01-25
forum: Networking &amp; Wireless
---

### Post by ImTroyMiller on 2015-01-25
I have an Alfa AWUS036H as my only network connection on Ubuntu 14.04 and it disconnects after a hour or so of use.  The only way to reconnect is to unplug it and then plug it back in.  I searched and found a couple of answers that look outdated...

[http://askubuntu.com/questions/453110/rtl8187-wireless-card-drops-signal-within-seconds](http://askubuntu.com/questions/453110/rtl8187-wireless-card-drops-signal-within-seconds)

[http://askubuntu.com/questions/178009/how-do-i-install-drivers-for-the-alfa-awus036h-usb-wireless-adapter](http://askubuntu.com/questions/178009/how-do-i-install-drivers-for-the-alfa-awus036h-usb-wireless-adapter)

Both of these have links to downloads for older kernal versions(I have 3.13.0-44-generic).

I have also found one answer that mentioned the channel could be interfering with another signal, but I have no other network connections on this PC.

What should I do?

---

### Post by praseodym on 2015-01-25
Do you have an USB-hub with current source? Often there is a power problem with this one.

---

### Post by ImTroyMiller on 2015-01-25
I have it plugged into a USB 3.0 port on my motherboard.

---

### Post by ImTroyMiller on 2015-01-31
Bump.

Here is my diagnostics...

```



########## wireless info START ##########


Report from: 30 Jan 2015 21:44 PST -0800


Booted last: 30 Jan 2015 20:48 PST -0800


Script from: 20 Sep 2014 23:04 UTC +0000


##### release ###########################


Distributor ID:	Ubuntu
Description:	Ubuntu 14.04.1 LTS
Release:	14.04
Codename:	trusty


##### kernel ############################


Linux 3.13.0-44-generic #73-Ubuntu SMP Tue Dec 16 00:22:43 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux


Parameters: ro, quiet, splash


##### desktop ###########################


Ubuntu


##### lspci #############################


02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 06)
	Subsystem: Gigabyte Technology Co., Ltd Motherboard [1458:e000]
	Kernel driver in use: r8169


##### lsusb #############################


Bus 003 Device 005: ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 003 Device 004: ID 1a40:0101 Terminus Technology Inc. 4-Port HUB
Bus 003 Device 007: ID 0bda:8187 Realtek Semiconductor Corp. RTL8187 Wireless Adapter
Bus 003 Device 002: ID 0955:0007 NVidia Corp. 
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 002: ID 0a5c:21e8 Broadcom Corp. BCM20702A0 Bluetooth 4.0
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 003: ID 056a:00dd Wacom Co., Ltd Bamboo Pen (CTL-470)
Bus 004 Device 002: ID 046d:0a1f Logitech, Inc. G930
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 009 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 008 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


##### PCMCIA card info ##################


##### rfkill ############################


0: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no
3: phy2: Wireless LAN
	Soft blocked: no
	Hard blocked: no


##### lsmod #############################


rtl8187                64909  0 
mac80211              630669  1 rtl8187
cfg80211              484040  2 mac80211,rtl8187
eeprom_93cx6           13344  1 rtl8187


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


wlan0     Link encap:Ethernet  HWaddr <MAC 'wlan0' [IF]>  
          inet addr:192.168.0.42  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::2c0:caff:fe52:3736/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1989 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2115 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1345442 (1.3 MB)  TX bytes:427197 (427.1 KB)


##### iwconfig ##########################


eth0      no wireless extensions.


lo        no wireless extensions.


wlan0     IEEE 802.11bg  ESSID:"Network"  
          Mode:Managed  Frequency:2.422 GHz  Access Point: <MAC 'Network' [AC1]>   
          Bit Rate=54 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=70/70  Signal level=-16 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:28   Missed beacon:0


##### route #############################


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.0.1     0.0.0.0         UG    0      0        0 wlan0
192.168.0.0     0.0.0.0         255.255.255.0   U     9      0        0 wlan0


##### resolv.conf #######################


nameserver 127.0.1.1
search lan


##### nm-tool ###########################


NetworkManager Tool


State: connected (global)


- Device: wlan0  [Network] -----------------------------------------------------
  Type:              802.11 WiFi
  Driver:            rtl8187
  State:             connected
  Default:           yes
  HW Address:        <MAC 'wlan0' [IF]>


  Capabilities:
    Speed:           54 Mb/s


  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes


  Wireless Access Points (* = current AP)
    myqwest6325:     Infra, <MAC 'myqwest6325' [AC7]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 100 WPA WPA2
    CenturyLink5806: Infra, <MAC 'CenturyLink5806' [AN2]>, Freq 2452 MHz, Rate 54 Mb/s, Strength 100 WPA WPA2
    CenturyLink9332: Infra, <MAC 'CenturyLink9332' [AN3]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 99 WPA WPA2
    HOME-D664-2.4:   Infra, <MAC 'HOME-D664-2.4' [AN4]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 94 WPA WPA2
    belkin.97e:      Infra, <MAC 'belkin.97e' [AN5]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 94 WPA2
    CenturyLink2426: Infra, <MAC 'CenturyLink2426' [AC5]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 87 WPA WPA2
    FBI Security Van 3: Infra, <MAC 'FBI Security Van 3' [AN7]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 85 WPA WPA2
    IraqVet2003:     Infra, <MAC 'IraqVet2003' [AC2]>, Freq 2417 MHz, Rate 54 Mb/s, Strength 84 WPA WPA2
    KKE Network:     Infra, <MAC 'KKE Network' [AN9]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 82 WPA WPA2
    HOME-0772:       Infra, <MAC 'HOME-0772' [AN10]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 72 WPA WPA2
    CenturyLink2253: Infra, <MAC 'CenturyLink2253' [AN11]>, Freq 2417 MHz, Rate 54 Mb/s, Strength 70 WPA WPA2
    snowflake:       Infra, <MAC 'snowflake' [AN12]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 69 WPA WPA2
    HOME-9682:       Infra, <MAC 'HOME-9682' [AN13]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 65 WPA WPA2
    Taylor's & Tails 2.4 Ghz: Infra, <MAC 'Taylor's <MAC 'Taylor's <MAC address> Tails 2.4 Ghz' [AN14]> Tails 2.4 Ghz' [AC8]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 60 WPA2
    <(^.^)>:         Infra, <MAC '<(^.^)>' [AC9]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 97 WEP
    belkin.97e.guests: Infra, <MAC 'belkin.97e.guests' [AN16]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 99
    xfinitywifi:     Infra, <MAC 'xfinitywifi' [AN17]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 84
    xfinitywifi:     Infra, <MAC 'xfinitywifi' [AN18]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 82
    xfinitywifi:     Infra, <MAC 'xfinitywifi' [AN19]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 80
    HOME-FD2F:       Infra, <MAC 'HOME-FD2F' [AC11]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 80 WPA WPA2
    HOME-0548:       Infra, <MAC 'HOME-0548' [AN21]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 75 WPA WPA2
    TrappedInBasement: Infra, <MAC 'TrappedInBasement' [AN22]>, Freq 2417 MHz, Rate 54 Mb/s, Strength 72 WPA2
    HOME-21F3:       Infra, <MAC 'HOME-21F3' [AN23]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 72 WPA WPA2
    xfinitywifi:     Infra, <MAC 'xfinitywifi' [AC10]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 79
    *Network:        Infra, <MAC 'Network' [AC1]>, Freq 2422 MHz, Rate 54 Mb/s, Strength 100 WPA WPA2
    HOME-B527:       Infra, <MAC 'HOME-B527' [AC3]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 80 WPA WPA2
    xfinitywifi:     Infra, <MAC 'xfinitywifi' [AC4]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 77
    BrokenSpirit-2.4:Infra, <MAC 'BrokenSpirit-2.4' [AN28]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 80 WPA WPA2
    xfinitywifi:     Infra, <MAC 'xfinitywifi' [AN29]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 72
    HOME-196C:       Infra, <MAC 'HOME-196C' [AN30]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 79 WPA WPA2


  IPv4 Settings:
    Address:         192.168.0.42
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.0.1


    DNS:             192.168.0.1


- Device: <MAC address> ----------------------------------------------------
  Type:              Bluetooth
  Driver:            bluez
  State:             disconnected
  Default:           no


  Capabilities:


- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            r8169
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


no-auto-default=<MAC 'eth0' [IF]>,


[ifupdown]
managed=false


##### NetworkManager profiles ###########


[[/etc/NetworkManager/system-connections/Network]] (600 root)
[connection] id=Network | type=802-11-wireless
[802-11-wireless] ssid=Network | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/HOME-5022]] (600 root)
[connection] id=HOME-5022 | type=802-11-wireless
[802-11-wireless] ssid=HOME-5022 | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/BrokenSpirit-2.4]] (600 root)
[connection] id=BrokenSpirit-2.4 | type=802-11-wireless
[802-11-wireless] ssid=BrokenSpirit-2.4 | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/<(^.^)>]] (600 root)
[connection] id=<(^.^)> | type=802-11-wireless
[802-11-wireless] ssid=<(^.^)> | mac-address=<MAC 'wlan0' [IF]>
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
          Current Frequency:2.422 GHz (Channel 3)


##### iwlist scan #######################


Channel occupancy:


      2   APs on   Frequency:2.412 GHz (Channel 1)
      1   APs on   Frequency:2.417 GHz (Channel 2)
      1   APs on   Frequency:2.422 GHz (Channel 3)
      3   APs on   Frequency:2.437 GHz (Channel 6)
      1   APs on   Frequency:2.442 GHz (Channel 7)
      3   APs on   Frequency:2.462 GHz (Channel 11)


eth0      Interface doesn't support scanning.


lo        Interface doesn't support scanning.


wlan0     Scan completed :
          Cell 01 - Address: <MAC 'Network' [AC1]>
                    Channel:3
                    Frequency:2.422 GHz (Channel 3)
                    Quality=70/70  Signal level=-16 dBm  
                    Encryption key:on
                    ESSID:"Network"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000000c20ecad1
                    Extra: Last beacon: 196ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC 'IraqVet2003' [AC2]>
                    Channel:2
                    Frequency:2.417 GHz (Channel 2)
                    Quality=59/70  Signal level=-51 dBm  
                    Encryption key:on
                    ESSID:"IraqVet2003"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000016eaa9b0cb
                    Extra: Last beacon: 5236ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: <MAC 'HOME-B527' [AC3]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=52/70  Signal level=-58 dBm  
                    Encryption key:on
                    ESSID:"HOME-B527"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000024d2f614805
                    Extra: Last beacon: 6168ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 04 - Address: <MAC 'xfinitywifi' [AC4]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=55/70  Signal level=-55 dBm  
                    Encryption key:off
                    ESSID:"xfinitywifi"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000024d2f615698
                    Extra: Last beacon: 6164ms ago
          Cell 05 - Address: <MAC 'CenturyLink2426' [AC5]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=64/70  Signal level=-46 dBm  
                    Encryption key:on
                    ESSID:"CenturyLink2426"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=8002aa92c1cbfbdb
                    Extra: Last beacon: 3876ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 06 - Address: <MAC '' [AC6]>
                    Channel:7
                    Frequency:2.442 GHz (Channel 7)
                    Quality=50/70  Signal level=-60 dBm  
                    Encryption key:on
                    ESSID:""
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000a458b3eecb
                    Extra: Last beacon: 3412ms ago
          Cell 07 - Address: <MAC 'myqwest6325' [AC7]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=70/70  Signal level=-36 dBm  
                    Encryption key:on
                    ESSID:"myqwest6325"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000002612fd71f23
                    Extra: Last beacon: 2956ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 08 - Address: <MAC 'Taylor's <MAC 'Taylor's <MAC address> Tails 2.4 Ghz' [AN14]> Tails 2.4 Ghz' [AC8]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=56/70  Signal level=-54 dBm  
                    Encryption key:on
                    ESSID:"Taylor's & Tails 2.4 Ghz"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000011a1891fc7a
                    Extra: Last beacon: 2936ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 09 - Address: <MAC '<(^.^)>' [AC9]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=68/70  Signal level=-42 dBm  
                    Encryption key:on
                    ESSID:"<(^.^)>"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s
                    Bit Rates:9 Mb/s; 18 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000920cd5cba0
                    Extra: Last beacon: 1576ms ago
          Cell 10 - Address: <MAC 'xfinitywifi' [AC10]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=60/70  Signal level=-50 dBm  
                    Encryption key:off
                    ESSID:"xfinitywifi"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000001ae4460da
                    Extra: Last beacon: 1572ms ago
          Cell 11 - Address: <MAC 'HOME-FD2F' [AC11]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=59/70  Signal level=-51 dBm  
                    Encryption key:on
                    ESSID:"HOME-FD2F"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000001ae446887
                    Extra: Last beacon: 1568ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK


##### module infos ######################


[rtl8187]
filename:       /lib/modules/3.13.0-44-generic/kernel/drivers/net/wireless/rtl818x/rtl8187/rtl8187.ko
license:        GPL
description:    RTL8187/RTL8187B USB wireless driver
author:         Larry Finger <Larry.Finger@lwfinger.net>
author:         Hin-Tak Leung <htl10@users.sourceforge.net>
author:         Herton Ronaldo Krzesinski <herton@mandriva.com.br>
author:         Andrea Merello <andrea.merello@gmail.com>
author:         Michael Wu <flamingice@sourmilk.net>
srcversion:     A707FEC6B464A70F7A04C69
depends:        mac80211,eeprom_93cx6,cfg80211
intree:         Y
vermagic:       3.13.0-44-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        50:8C:3B:4B:F1:08:ED:36:B6:06:2F:81:27:82:F7:7C:37:B9:85:37
sig_hashalgo:   sha512


[mac80211]
filename:       /lib/modules/3.13.0-44-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     385697223F8285F67C93A06
depends:        cfg80211
intree:         Y
vermagic:       3.13.0-44-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        50:8C:3B:4B:F1:08:ED:36:B6:06:2F:81:27:82:F7:7C:37:B9:85:37
sig_hashalgo:   sha512
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)


[cfg80211]
filename:       /lib/modules/3.13.0-44-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     C2478077E22138832B71659
depends:        
intree:         Y
vermagic:       3.13.0-44-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        50:8C:3B:4B:F1:08:ED:36:B6:06:2F:81:27:82:F7:7C:37:B9:85:37
sig_hashalgo:   sha512
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)


##### module parameters #################


[mac80211]
beacon_loss_count: 7
ieee80211_default_rc_algo: minstrel_ht
max_nullfunc_tries: 2
max_probe_tries: 5
probe_wait_ms: 500


[cfg80211]
cfg80211_disable_40mhz_24ghz: N
ieee80211_regdom: 00


##### /etc/modules ######################


lp
rtc


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
# PCI device 0x10ec:0x8168 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# USB device 0x:0x (rtl8187)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"
# USB device 0x:0x (rtl8192cu)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan1"


##### dmesg #############################


[   18.370901] wlan0: direct probe to <MAC 'Network' [AC1]> (try 3/3)
[   18.574743] wlan0: authentication with <MAC 'Network' [AC1]> timed out
[   20.534322] wlan0: authenticate with <MAC 'Network' [AC1]>
[   20.703265] wlan0: send auth to <MAC 'Network' [AC1]> (try 1/3)
[   20.711600] wlan0: authenticated
[   20.713058] wlan0: associate with <MAC 'Network' [AC1]> (try 1/3)
[   20.720466] wlan0: RX AssocResp from <MAC 'Network' [AC1]> (capab=0x431 status=0 aid=1)
[   20.721214] wlan0: associated
[   20.721234] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  243.664715] wlan0: deauthenticated from <MAC 'Network' [AC1]> (Reason: 2)
[  245.544711] wlan0: authenticate with <MAC 'Network' [AC1]>
[  245.699714] wlan0: send auth to <MAC 'Network' [AC1]> (try 1/3)
[  245.901557] wlan0: send auth to <MAC 'Network' [AC1]> (try 2/3)
[  245.955828] wlan0: authenticated
[  245.957515] wlan0: associate with <MAC 'Network' [AC1]> (try 1/3)
[  245.961903] wlan0: RX AssocResp from <MAC 'Network' [AC1]> (capab=0x431 status=0 aid=1)
[  245.962753] wlan0: associated
[  344.555457] wlan0: deauthenticated from <MAC 'Network' [AC1]> (Reason: 2)
[  346.439671] wlan0: authenticate with <MAC 'Network' [AC1]>
[  346.599376] wlan0: send auth to <MAC 'Network' [AC1]> (try 1/3)
[  346.604677] wlan0: authenticated
[  346.605174] wlan0: associate with <MAC 'Network' [AC1]> (try 1/3)
[  346.619209] wlan0: RX AssocResp from <MAC 'Network' [AC1]> (capab=0x431 status=0 aid=1)
[  346.620014] wlan0: associated
[ 2530.967786] ieee80211 phy0: wlan0: No probe response from AP <MAC 'Network' [AC1]> after 500ms, disconnecting.
[ 2546.413427] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 2890.382205] ieee80211 phy1: hwaddr <MAC 'wlan0' [IF]>, RTL8187vB (default) V1 + rtl8225z2, rfkill mask 2
[ 2890.393524] rtl8187: Customer ID is 0xFF
[ 2890.394138] rtl8187: wireless switch is on
[ 2892.460659] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready (repeated 2 times)
[ 2896.059066] wlan0: authenticate with <MAC 'Network' [AC1]>
[ 2896.266599] wlan0: direct probe to <MAC 'Network' [AC1]> (try 1/3)
[ 2896.468441] wlan0: direct probe to <MAC 'Network' [AC1]> (try 2/3)
[ 2896.672278] wlan0: direct probe to <MAC 'Network' [AC1]> (try 3/3)
[ 2896.876015] wlan0: authentication with <MAC 'Network' [AC1]> timed out
[ 2897.020106] wlan0: authenticate with <MAC 'Network' [AC1]>
[ 2897.130154] wlan0: direct probe to <MAC 'Network' [AC1]> (try 1/3)
[ 2897.331751] wlan0: direct probe to <MAC 'Network' [AC1]> (try 2/3)
[ 2897.535539] wlan0: direct probe to <MAC 'Network' [AC1]> (try 3/3)
[ 2897.739424] wlan0: authentication with <MAC 'Network' [AC1]> timed out
[ 3051.166224] ieee80211 phy2: hwaddr <MAC 'wlan0' [IF]>, RTL8187vB (default) V1 + rtl8225z2, rfkill mask 2
[ 3051.177838] rtl8187: Customer ID is 0xFF
[ 3051.178450] rtl8187: wireless switch is on
[ 3053.256637] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready (repeated 2 times)
[ 3059.490053] wlan0: authenticate with <MAC 'Network' [AC1]>
[ 3059.596524] wlan0: direct probe to <MAC 'Network' [AC1]> (try 1/3)
[ 3059.798228] wlan0: direct probe to <MAC 'Network' [AC1]> (try 2/3)
[ 3060.002065] wlan0: send auth to <MAC 'Network' [AC1]> (try 3/3)
[ 3060.100391] wlan0: authenticated
[ 3060.101944] wlan0: associate with <MAC 'Network' [AC1]> (try 1/3)
[ 3060.105379] wlan0: RX AssocResp from <MAC 'Network' [AC1]> (capab=0x431 status=0 aid=1)
[ 3060.106579] wlan0: associated
[ 3060.106629] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready


########## wireless info END ############



```

---

### Post by ImTroyMiller on 2015-01-31
It's not the network adapter.  I tried another adapter and I'm having the exact same problems.  Only one is plugged in at a time.

I should add that I am connecting to a mobile hot spot.

---

### Post by praseodym on 2015-02-09
Can you change the encryption mode to pure WPA2-AES (CCMP) in the router? If no, try Wicd instead of the network-manager:

```
wget http://www.elektronenblitz63.de/download/wicd-1.6.x_addon01441.tar.gz
sudo apt-get install --reinstall wicd
tar xvf wicd-1.6.x_addon01441.tar.gz
cd wicd-1.6.x_addon01441
sudo ./install_wicd_addon
sudo service network-manager stop
sudo killall wpa_supplicant
sudo service wicd restart
```
Chose wlan0 as interface name and wext as driver. You can choose mixed WPA/WPA2 there, too.

---

### Post by ImTroyMiller on 2015-02-12
^That seems to fix it.  Thank you.

Just out of curiosity, why does this fix it?  Is it just one of those "learn with experience" type of things, or is this a common issue that people with mobile hot-spots have?

---

