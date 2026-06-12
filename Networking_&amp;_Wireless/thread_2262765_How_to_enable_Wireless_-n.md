---
title: "How to enable Wireless -n"
date: 2015-01-27
forum: Networking &amp; Wireless
---

### Post by m_ghv_geo on 2015-01-27
Hello,
My laptop has Centrino Advanced-N 6235This wifi had compatibility issues with kernel that were implemented with ubuntu 14.04 at it's 1st lunch
Someone suggested to disable the [FONT=arial][SIZE=2][COLOR=#545454]802.11n. This solved the problem but with b/g LAN is really slow.
[/COLOR][/SIZE][/FONT]
[FONT=arial][SIZE=2][COLOR=#545454]this were the some of the commands that I used(as you can see i had trouble with it instructions)[/COLOR][/SIZE][/FONT]
```
echo "options iwlwifi 11n_disable=1" | sudo tee /etc/modprobe.d/iwlwifi.confdo modprobe -rfv iwlwifi
sudo modprobe -rfv iwlwifi
sudo modprobe -v iwlwifi
ping 192.168.1.1
echo "options iwlwifi 11n_disable=1" | sudo tee /etc/modprobe.d/iwlwifi.conf
sudo modprobe -rfv iwlwifi
ifconfig
ifconfig wlano down
sudo ifconfig wlan0 down
sudo modprobe -rfv iwlwifi
ifconfig
sudo ifconfig wlan0 up

```[COLOR=#545454][FONT=arial]

[/FONT][/COLOR]

[FONT=arial][COLOR=#545454]1st I would like re-enable the [/COLOR][/FONT][COLOR=#545454][FONT=arial]802.11n
[/FONT][/COLOR]2nd If this problem is not resolved in 3.13.0-44-generic kernel I need help to fix it.

---

### Post by jeremy31 on 2015-01-27
> **m_ghv_geo said:**
> Hello,
My laptop has Centrino Advanced-N 6235This wifi had compatibility issues with kernel that were implemented with ubuntu 14.04 at it's 1st lunch
Someone suggested to disable the [FONT=arial][SIZE=2][COLOR=#545454]802.11n. This solved the problem but with b/g LAN is really slow.
[/COLOR][/SIZE][/FONT]
[FONT=arial][SIZE=2][COLOR=#545454]this were the some of the commands that I used(as you can see i had trouble with it instructions)[/COLOR][/SIZE][/FONT]
```
echo "options iwlwifi 11n_disable=1" | sudo tee /etc/modprobe.d/iwlwifi.confdo modprobe -rfv iwlwifi
sudo modprobe -rfv iwlwifi
sudo modprobe -v iwlwifi
ping 192.168.1.1
echo "options iwlwifi 11n_disable=1" | sudo tee /etc/modprobe.d/iwlwifi.conf
sudo modprobe -rfv iwlwifi
ifconfig
ifconfig wlano down
sudo ifconfig wlan0 down
sudo modprobe -rfv iwlwifi
ifconfig
sudo ifconfig wlan0 up

```[COLOR=#545454][FONT=arial]

[/FONT][/COLOR]

[FONT=arial][COLOR=#545454]1st I would like re-enable the [/COLOR][/FONT][COLOR=#545454][FONT=arial]802.11n
[/FONT][/COLOR]2nd If this problem is not resolved in 3.13.0-44-generic kernel I need help to fix it.

What is the result of ```
cat /etc/modprobe.d/iwlwifi.conf
```

---

### Post by m_ghv_geo on 2015-01-27
options iwlwifi 11n_disable=1

---

### Post by weatherman2 on 2015-01-27
Try changing it to:

```
options iwlwifi 11n_disable=8
```

(1 changed to 8)

---

### Post by m_ghv_geo on 2015-01-27
why 8?

---

### Post by jeremy31 on 2015-01-27
> **m_ghv_geo said:**
> why 8?
It actually works to enable agg TX which is needed with some chips to even connect to a wireless n only access point

---

### Post by m_ghv_geo on 2015-01-27
```
mike@mike-UX32VD:~$ cat /etc/modprobe.d/iwlwifi.conf
options iwlwifi 11n_disable=8

```

How ever I can not connect to working 5Ghz which is set to N mode
so there must more than that

---

### Post by jeremy31 on 2015-01-28
```
wget -N -t 5 -T 10 http://dl.dropbox.com/u/57264241/wireless_script && chmod +x wireless_script && ./wireless_script
```
And paste the resulting wireless-info file

---

### Post by m_ghv_geo on 2015-01-28
```


########## wireless info START ##########


Report from: 28 Jan 2015 18:47 EST -0500


Booted last: 26 Jan 2015 06:21 EST -0500


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


03:00.0 Network controller [0280]: Intel Corporation Centrino Advanced-N 6235 [8086:088e] (rev 24)
	Subsystem: Intel Corporation Centrino Advanced-N 6235 AGN [8086:4060]
	Kernel driver in use: iwlwifi


##### lsusb #############################


Bus 002 Device 005: ID 8087:07da Intel Corp. 
Bus 002 Device 003: ID 04f2:b330 Chicony Electronics Co., Ltd Asus 720p CMOS webcam
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 0bda:0139 Realtek Semiconductor Corp. RTS5139 Card Reader Controller
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


##### PCMCIA card info ##################


##### rfkill ############################


1: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
2: asus-wlan: Wireless LAN
	Soft blocked: no
	Hard blocked: no
3: asus-bluetooth: Bluetooth
	Soft blocked: yes
	Hard blocked: no
8: hci0: Bluetooth
	Soft blocked: yes
	Hard blocked: no


##### lsmod #############################


iwldvm                232285  0 
asus_nb_wmi            16990  0 
asus_wmi               24191  1 asus_nb_wmi
sparse_keymap          13948  1 asus_wmi
mac80211              630669  1 iwldvm
mxm_wmi                13021  0 
iwlwifi               169932  1 iwldvm
cfg80211              484040  3 iwlwifi,mac80211,iwldvm
wmi                    19177  2 mxm_wmi,asus_wmi
video                  19476  2 i915,asus_wmi


##### interfaces ########################


auto lo
iface lo inet loopback


##### ifconfig ##########################


wlan0     Link encap:Ethernet  HWaddr <MAC 'wlan0' [IF]>  
          inet addr:192.168.1.77  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::c685:8ff:fe46:e60f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:5719564 errors:0 dropped:46289 overruns:0 frame:0
          TX packets:3324309 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:8151762175 (8.1 GB)  TX bytes:370908187 (370.9 MB)


##### iwconfig ##########################


lo        no wireless extensions.


wlan0     IEEE 802.11abg  ESSID:"M_GHV_GEO"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: <MAC 'M_GHV_GEO' [AC1]>   
          Bit Rate=54 Mb/s   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=70/70  Signal level=-37 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:10  Invalid misc:188   Missed beacon:0


##### route #############################


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 wlan0
192.168.1.0     0.0.0.0         255.255.255.0   U     9      0        0 wlan0


##### resolv.conf #######################


nameserver 127.0.1.1


##### nm-tool ###########################


NetworkManager Tool


State: connected (global)


- Device: wlan0  [M_GHV_GEO] ---------------------------------------------------
  Type:              802.11 WiFi
  Driver:            iwlwifi
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
    Amped_REC10:     Infra, <MAC 'Amped_REC10' [AC9]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 92 WPA WPA2
    M_GHV_GEO5:      Infra, <MAC 'M_GHV_GEO5' [AC15]>, Freq 5745 MHz, Rate 54 Mb/s, Strength 82 WPA2
    DE7D3E:          Infra, <MAC 'DE7D3E' [AC2]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 87 WPA WPA2
    QSQ3R:           Infra, <MAC 'QSQ3R' [AN4]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 62 WPA2
    DE7D3E:          Infra, <MAC 'DE7D3E' [AC16]>, Freq 5745 MHz, Rate 54 Mb/s, Strength 52 WPA WPA2
    optimumwifi:     Infra, <MAC 'optimumwifi' [AC3]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 87
    optimumwifi:     Infra, <MAC 'optimumwifi' [AC17]>, Freq 5745 MHz, Rate 54 Mb/s, Strength 50
    M_GHV_GEO:       Infra, <MAC 'M_GHV_GEO' [AC4]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 60 WPA WPA2
    139270 2.4GHz:   Infra, <MAC '139270 2.4GHz' [AC5]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 55 WPA WPA2
    Chris_Rob:       Infra, <MAC 'Chris_Rob' [AC13]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 47 WPA
    NETGEAR58:       Infra, <MAC 'NETGEAR58' [AN11]>, Freq 2452 MHz, Rate 54 Mb/s, Strength 35 WPA2
    optimumwifi:     Infra, <MAC 'optimumwifi' [AC10]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 57
    optimumwifi:     Infra, <MAC 'optimumwifi' [AC7]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 54
    *M_GHV_GEO:      Infra, <MAC 'M_GHV_GEO' [AC1]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 83 WPA2
    01A4A0:          Infra, <MAC '01A4A0' [AC11]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 59 WPA WPA2
    mr2's Network:   Infra, <MAC 'mr2's Network' [AC12]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 45 WPA2
    mr2's Guest Network: Infra, <MAC 'mr2's Guest Network' [AC14]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 44 WPA2
    NETGEAR09:       Infra, <MAC 'NETGEAR09' [AN18]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 42 WPA2
    TheLink:         Infra, <MAC 'TheLink' [AN19]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 40 WPA2
    E4C03E:          Infra, <MAC 'E4C03E' [AC6]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 39 WPA WPA2
    optimumwifi:     Infra, <MAC 'optimumwifi' [AC8]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 42


  IPv4 Settings:
    Address:         192.168.1.77
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1


    DNS:             192.168.1.1


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


[[/etc/NetworkManager/system-connections/M_GHV_GEO5]] (600 root)
[connection] id=M_GHV_GEO5 | type=802-11-wireless
[802-11-wireless] ssid=M_GHV_GEO5 | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/Belkin.565B]] (600 root)
[connection] id=Belkin.565B | type=802-11-wireless
[802-11-wireless] ssid=Belkin.565B | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/NINOairport]] (600 root)
[connection] id=NINOairport | type=802-11-wireless
[802-11-wireless] ssid=NINOairport | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/TCI320 ]] (600 root)
[connection] id=TCI320  | type=802-11-wireless
[802-11-wireless] ssid=TCI320  | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/Amped_REC10]] (600 root)
[connection] id=Amped_REC10 | type=802-11-wireless
[802-11-wireless] ssid=Amped_REC10 | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/M_GHV_GEO]] (600 root)
[connection] id=M_GHV_GEO | type=802-11-wireless
[802-11-wireless] ssid=M_GHV_GEO | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=manual
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


wlan0     32 channels in total; available frequencies :
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
          Channel 36 : 5.18 GHz
          Channel 40 : 5.2 GHz
          Channel 44 : 5.22 GHz
          Channel 48 : 5.24 GHz
          Channel 52 : 5.26 GHz
          Channel 56 : 5.28 GHz
          Channel 60 : 5.3 GHz
          Channel 64 : 5.32 GHz
          Channel 100 : 5.5 GHz
          Channel 104 : 5.52 GHz
          Channel 108 : 5.54 GHz
          Channel 112 : 5.56 GHz
          Channel 116 : 5.58 GHz
          Channel 120 : 5.6 GHz
          Channel 124 : 5.62 GHz
          Channel 128 : 5.64 GHz
          Channel 132 : 5.66 GHz
          Channel 136 : 5.68 GHz
          Channel 140 : 5.7 GHz
          Current Frequency:2.437 GHz (Channel 6)


##### iwlist scan #######################


Channel occupancy:


      7   APs on   Frequency:2.412 GHz (Channel 1)
      4   APs on   Frequency:2.437 GHz (Channel 6)
      3   APs on   Frequency:2.462 GHz (Channel 11)
      3   APs on   Frequency:5.745 GHz


lo        Interface doesn't support scanning.


wlan0     Scan completed :
          Cell 01 - Address: <MAC 'M_GHV_GEO' [AC1]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=37/70  Signal level=-73 dBm  
                    Encryption key:on
                    ESSID:"M_GHV_GEO"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000077eacb0ec
                    Extra: Last beacon: 56ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC 'DE7D3E' [AC2]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=56/70  Signal level=-54 dBm  
                    Encryption key:on
                    ESSID:"DE7D3E"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000096d38ef02b
                    Extra: Last beacon: 56ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: <MAC 'optimumwifi' [AC3]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=55/70  Signal level=-55 dBm  
                    Encryption key:off
                    ESSID:"optimumwifi"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000096d38f7e09
                    Extra: Last beacon: 56ms ago
          Cell 04 - Address: <MAC 'M_GHV_GEO' [AC4]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=46/70  Signal level=-64 dBm  
                    Encryption key:on
                    ESSID:"M_GHV_GEO"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000005057192df0
                    Extra: Last beacon: 56ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 05 - Address: <MAC '139270 2.4GHz' [AC5]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=41/70  Signal level=-69 dBm  
                    Encryption key:on
                    ESSID:"139270 2.4GHz"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000633c6a2f5e
                    Extra: Last beacon: 56ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 06 - Address: <MAC 'E4C03E' [AC6]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=34/70  Signal level=-76 dBm  
                    Encryption key:on
                    ESSID:"E4C03E"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000003af7bafc6d
                    Extra: Last beacon: 56ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 07 - Address: <MAC 'optimumwifi' [AC7]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=41/70  Signal level=-69 dBm  
                    Encryption key:off
                    ESSID:"optimumwifi"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000633c6a589a
                    Extra: Last beacon: 56ms ago
          Cell 08 - Address: <MAC 'optimumwifi' [AC8]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=34/70  Signal level=-76 dBm  
                    Encryption key:off
                    ESSID:"optimumwifi"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000003af7bb253b
                    Extra: Last beacon: 56ms ago
          Cell 09 - Address: <MAC 'Amped_REC10' [AC9]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=66/70  Signal level=-44 dBm  
                    Encryption key:on
                    ESSID:"Amped_REC10"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000030b825e49
                    Extra: Last beacon: 56ms ago
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 10 - Address: <MAC 'optimumwifi' [AC10]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=44/70  Signal level=-66 dBm  
                    Encryption key:off
                    ESSID:"optimumwifi"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000007eb9dfb68a
                    Extra: Last beacon: 56ms ago
          Cell 11 - Address: <MAC '01A4A0' [AC11]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=39/70  Signal level=-71 dBm  
                    Encryption key:on
                    ESSID:"01A4A0"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000007eb9df0f31
                    Extra: Last beacon: 56ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 12 - Address: <MAC 'mr2's Network' [AC12]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=36/70  Signal level=-74 dBm  
                    Encryption key:on
                    ESSID:"mr2's Network"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00002111a5517ee9
                    Extra: Last beacon: 56ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 13 - Address: <MAC 'Chris_Rob' [AC13]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=37/70  Signal level=-73 dBm  
                    Encryption key:on
                    ESSID:"Chris_Rob"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s
                    Bit Rates:9 Mb/s; 18 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000002ec749518
                    Extra: Last beacon: 56ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 14 - Address: <MAC 'mr2's Guest Network' [AC14]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=37/70  Signal level=-73 dBm  
                    Encryption key:on
                    ESSID:"mr2's Guest Network"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00002111a5519b3e
                    Extra: Last beacon: 56ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 15 - Address: <MAC 'M_GHV_GEO5' [AC15]>
                    Channel:149
                    Frequency:5.745 GHz
                    Quality=63/70  Signal level=-47 dBm  
                    Encryption key:on
                    ESSID:"M_GHV_GEO5"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000028348f50790
                    Extra: Last beacon: 56ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 16 - Address: <MAC 'DE7D3E' [AC16]>
                    Channel:149
                    Frequency:5.745 GHz
                    Quality=39/70  Signal level=-71 dBm  
                    Encryption key:on
                    ESSID:"DE7D3E"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000096d3e83af6
                    Extra: Last beacon: 56ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 17 - Address: <MAC 'optimumwifi' [AC17]>
                    Channel:149
                    Frequency:5.745 GHz
                    Quality=40/70  Signal level=-70 dBm  
                    Encryption key:off
                    ESSID:"optimumwifi"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000096d3e83dc7
                    Extra: Last beacon: 56ms ago


##### module infos ######################


[iwldvm]
filename:       /lib/modules/3.13.0-44-generic/kernel/drivers/net/wireless/iwlwifi/dvm/iwldvm.ko
license:        GPL
author:         Copyright(c) 2003-2013 Intel Corporation <ilw@linux.intel.com>
version:        in-tree:
description:    Intel(R) Wireless WiFi Link AGN driver for Linux
srcversion:     9ABCB275EC05F363D958754
depends:        iwlwifi,mac80211,cfg80211
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


[iwlwifi]
filename:       /lib/modules/3.13.0-44-generic/kernel/drivers/net/wireless/iwlwifi/iwlwifi.ko
license:        GPL
author:         Copyright(c) 2003-2013 Intel Corporation <ilw@linux.intel.com>
version:        in-tree:
description:    Intel(R) Wireless WiFi driver for Linux
firmware:       iwlwifi-100-5.ucode
firmware:       iwlwifi-1000-5.ucode
firmware:       iwlwifi-135-6.ucode
firmware:       iwlwifi-105-6.ucode
firmware:       iwlwifi-2030-6.ucode
firmware:       iwlwifi-2000-6.ucode
firmware:       iwlwifi-5150-2.ucode
firmware:       iwlwifi-5000-5.ucode
firmware:       iwlwifi-6000g2b-6.ucode
firmware:       iwlwifi-6000g2a-5.ucode
firmware:       iwlwifi-6050-5.ucode
firmware:       iwlwifi-6000-4.ucode
firmware:       iwlwifi-7265-7.ucode
firmware:       iwlwifi-3160-7.ucode
firmware:       iwlwifi-7260-7.ucode
srcversion:     716D089263B1757F5069E63
depends:        cfg80211
intree:         Y
vermagic:       3.13.0-44-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        50:8C:3B:4B:F1:08:ED:36:B6:06:2F:81:27:82:F7:7C:37:B9:85:37
sig_hashalgo:   sha512
parm:           swcrypto:using crypto in software (default 0 [hardware]) (int)
parm:           11n_disable:disable 11n functionality, bitmap: 1: full, 2: disable agg TX, 4: disable agg RX, 8 enable agg TX (uint)
parm:           amsdu_size_8K:enable 8K amsdu size (default 0) (int)
parm:           fw_restart:restart firmware in case of error (default true) (bool)
parm:           antenna_coupling:specify antenna coupling in dB (defualt: 0 dB) (int)
parm:           wd_disable:Disable stuck queue watchdog timer 0=system default, 1=disable, 2=enable (default: 0) (int)
parm:           nvm_file:NVM file name (charp)
parm:           bt_coex_active:enable wifi/bt co-exist (default: enable) (bool)
parm:           led_mode:0=system default, 1=On(RF On)/Off(RF Off), 2=blinking, 3=Off (default: 0) (int)
parm:           power_save:enable WiFi power management (default: disable) (bool)
parm:           power_level:default power save level (range from 1 - 5, default: 1) (int)


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


[iwlwifi]
11n_disable: 1
amsdu_size_8K: 0
antenna_coupling: 0
bt_coex_active: Y
fw_restart: Y
led_mode: 0
nvm_file: (null)
power_level: 0
power_save: N
swcrypto: 0
wd_disable: 1


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
options iwlwifi 11n_disable=8


[/etc/modprobe.d/mlx4.conf]
softdep mlx4_core post: mlx4_en


##### rc.local ##########################


exit 0


##### pm-utils ##########################


##### udev rules ########################


[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x8086:0x088e (iwlwifi)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"


##### dmesg #############################


[93444.225194] iwlwifi 0000:03:00.0: L1 Disabled - LTR Disabled
[93444.232178] iwlwifi 0000:03:00.0: Radio type=0x2-0x1-0x0
[93444.316115] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[93450.739338] wlan0: authenticate with <MAC 'M_GHV_GEO' [AC1]>
[93450.741874] wlan0: send auth to <MAC 'M_GHV_GEO' [AC1]> (try 1/3)
[93450.744609] wlan0: authenticated
[93450.745164] wlan0: associate with <MAC 'M_GHV_GEO' [AC1]> (try 1/3)
[93450.748053] wlan0: RX AssocResp from <MAC 'M_GHV_GEO' [AC1]> (capab=0x411 status=0 aid=5)
[93450.750234] wlan0: associated
[93450.750259] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[93450.768172] wlan0: deauthenticating from <MAC 'M_GHV_GEO' [AC1]> by local choice (reason=2)
[93450.770573] wlan0: authenticate with <MAC 'M_GHV_GEO' [AC1]>
[93450.772902] wlan0: send auth to <MAC 'M_GHV_GEO' [AC1]> (try 1/3)
[93450.775688] wlan0: authenticated
[93450.777148] wlan0: associate with <MAC 'M_GHV_GEO' [AC1]> (try 1/3)
[93450.780456] wlan0: RX AssocResp from <MAC 'M_GHV_GEO' [AC1]> (capab=0x411 status=0 aid=5)
[93450.797876] wlan0: associated


########## wireless info END ############



```

---

### Post by jeremy31 on 2015-01-28
Have you tried to disable the 2.4GHz mode of the router/access point to see if there is any difference?

---

### Post by m_ghv_geo on 2015-01-28
The router itself has no problem I am able to connect to it's 5Ghz with others computers and phones also I have 2nd router that also has 5Ghz. Same.
I am not able to connect to 5Ghz, because the router's 5Ghz is set to N mode, and the commands I entered in this laptop disabled N mode on this laptop.
If I will set 2.4Ghz to N mode only. This laptop will not be able to connect to it.

---

### Post by chili555 on 2015-01-28
> **jeremy31 said:**
> What is the result of ```
cat /etc/modprobe.d/iwlwifi.conf
```> options iwlwifi 11n_disable=1There is supposed to be more than that. I suspect you did a sudo tee thereby overwriting the contents, instead of sudo tee -a, thereby appending the line.

Mine reads:```
# /etc/modprobe.d/iwlwifi.conf
# iwlwifi will dyamically load either iwldvm or iwlmvm depending on the
# microcode file installed on the system.  When removing iwlwifi, first
# remove the iwl?vm module and then iwlwifi.
remove iwlwifi \
(/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
&& /sbin/modprobe -r mac80211

```Although I have an Intel wireless device, I don't need the options line to connect to N speeds.

We now return to our regularly scheduled expert.

---

### Post by m_ghv_geo on 2015-01-28
No i did not. It only contains options iwlwifi 11n_disable=8
```
mike@mike-UX32VD:/etc/modprobe.d$ cat iwlwifi.conf
options iwlwifi 11n_disable=8
mike@mike-UX32VD:/etc/modprobe.d$ 

```

---

### Post by chili555 on 2015-01-28
No matter the cause; as it stands now it is incorrect. The file, on a clean, default install of 14.04, is as I quoted above. I recommend you correct yours to:```
# /etc/modprobe.d/iwlwifi.conf
# iwlwifi will dyamically load either iwldvm or iwlmvm depending on the
# microcode file installed on the system.  When removing iwlwifi, first
# remove the iwl?vm module and then iwlwifi.
remove iwlwifi \
(/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
&& /sbin/modprobe -r mac80211
options iwlwifi 11n_disable=1
```

---

### Post by m_ghv_geo on 2015-01-28
repeated post due to error

---

### Post by m_ghv_geo on 2015-01-28
repeated post due to error

---

### Post by m_ghv_geo on 2015-01-28
Do i need to run any commands after making those changes?


```

mike@mike-UX32VD:/etc/modprobe.d$ ls -l iwlwifi.conf
-rw-r--r-- 1 root root 377 Jan 28 22:05 iwlwifi.conf
mike@mike-UX32VD:/etc/modprobe.d$ cat iwlwifi.conf
# /etc/modprobe.d/iwlwifi.conf
# iwlwifi will dyamically load either iwldvm or iwlmvm depending on the
# microcode file installed on the system.  When removing iwlwifi, first
# remove the iwl?vm module and then iwlwifi.
remove iwlwifi \
(/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
&& /sbin/modprobe -r mac80211
options iwlwifi 11n_disable=1
mike@mike-UX32VD:/etc/modprobe.d$ 
```

---

### Post by jeremy31 on 2015-01-29
> **m_ghv_geo said:**
> Do i need to run any commands after making those changes?


```

mike@mike-UX32VD:/etc/modprobe.d$ ls -l iwlwifi.conf
-rw-r--r-- 1 root root 377 Jan 28 22:05 iwlwifi.conf
mike@mike-UX32VD:/etc/modprobe.d$ cat iwlwifi.conf
# /etc/modprobe.d/iwlwifi.conf
# iwlwifi will dyamically load either iwldvm or iwlmvm depending on the
# microcode file installed on the system.  When removing iwlwifi, first
# remove the iwl?vm module and then iwlwifi.
remove iwlwifi \
(/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
&& /sbin/modprobe -r mac80211
options iwlwifi 11n_disable=1
mike@mike-UX32VD:/etc/modprobe.d$ 
```


You should be able to connect to N speed only with 11n_disable=8, it must be a firmware issue as my 6250 needs the same parameter but my 7260 doesn't.
Just noticed another possible issue, you are in New York but you have the default location of 00 from iw reg get so ```
sudo iw reg set US
``` Reboot and see if 5GHz works

---

### Post by m_ghv_geo on 2015-01-29
issue solved with 
```

mike@mike-UX32VD:/etc/modprobe.d$ cat iwlwifi.conf
# /etc/modprobe.d/iwlwifi.conf
# iwlwifi will dyamically load either iwldvm or iwlmvm depending on the
# microcode file installed on the system.  When removing iwlwifi, first
# remove the iwl?vm module and then iwlwifi.
remove iwlwifi \
(/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
&& /sbin/modprobe -r mac80211
options iwlwifi 11n_disable=8
mike@mike-UX32VD:/etc/modprobe.d$ 

```

and ```
 sudo iw reg set US
```

---

### Post by chili555 on 2015-01-29
Awesome! Jeremy will tell you how to make the country code permanent.

---

### Post by m_ghv_geo on 2015-01-29
Thank you, I was able to connect to N mode.
Connection to router seems stable. Average latency is less than 1ms

---

### Post by jeremy31 on 2015-01-29
You can edit a file ```
gksudo gedit /etc/default/crda
``` Scroll to the last line that begins with REGDOMAIN and make it be ```
REDOMAIN=US
``` then save and exit

---

