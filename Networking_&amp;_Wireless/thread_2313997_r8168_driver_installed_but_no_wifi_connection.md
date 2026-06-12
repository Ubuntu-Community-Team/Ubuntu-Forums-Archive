---
title: "r8168 driver installed but no wifi connection"
date: 2016-02-17
forum: Networking &amp; Wireless
---

### Post by gareth15 on 2016-02-17
Hi, I'm new to Ubuntu, trying to get wifi to work.

System76 computer came with the card:

RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller

lspci:
```

00:00.0 Host bridge: Intel Corporation Device 1910 (rev 07)
00:02.0 VGA compatible controller: Intel Corporation Device 191b (rev 06)
00:14.0 USB controller: Intel Corporation Device a12f (rev 31)
00:14.2 Signal processing controller: Intel Corporation Device a131 (rev 31)
00:16.0 Communication controller: Intel Corporation Device a13a (rev 31)
00:17.0 SATA controller: Intel Corporation Device a103 (rev 31)
00:1c.0 PCI bridge: Intel Corporation Device a114 (rev f1)
00:1c.6 PCI bridge: Intel Corporation Device a116 (rev f1)
00:1f.0 ISA bridge: Intel Corporation Device a14e (rev 31)
00:1f.2 Memory controller: Intel Corporation Device a121 (rev 31)
00:1f.3 Audio device: Intel Corporation Device a170 (rev 31)
00:1f.4 SMBus: Intel Corporation Device a123 (rev 31)
01:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. Device 5287 (rev 01)
01:00.1 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 12)

```
lshw -c network: 
```

  *-network               
       description: Ethernet interface
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0.1
       bus info: pci@0000:01:00.1
       logical name: eth0
       version: 12
       serial: 80:fa:5b:29:34:4b
       size: 10Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8168 driverversion=8.041.01-NAPI duplex=half latency=0 link=no multicast=yes port=twisted pair speed=10Mbit/s
       resources: irq:123 ioport:e000(size=256) memory:df114000-df114fff memory:df110000-df113fff
```


but I do iwconfig and get:

```
eth0      no wireless extensions.

lo        no wireless extensions.
```


I've seen on forums I can modify etc/dev/rules.d/ as well as etc/network/interfaces... 

I'm currently using a D-link to get internet which shows up as wlan0 when I connect, while my inbuilt wireless card comes up as eth0. Why is that?

Any pointers would be much appreciated.

---

### Post by Hadaka on 2016-02-17
Hi, your RTL8168 card is not the wireless card.
RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller

It is your Ethernet wired card and should be eth0 . that is normal.
You can test if its working by plugging into your router port with a cable.
"I've seen on forums I can modify etc/dev/rules.d/ as well as etc/network/interfaces"
As you dont yet have enough information I would advise against changing those files.
Please Copy and paste into a terminal then post the output of..
```
lspci -nnk | grep -iA2 net
lspci -n | awk '/0200|0280/{print$2,$3}'
lsusb
rfkill list all
```
thanks.

---

### Post by gareth15 on 2016-02-18
Thanks for your quick reply. Here's the output of those commands: 

```
gareth@gareth:~$ lspci -nnk | grep -iA2 net
01:00.1 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 12)
    Subsystem: CLEVO/KAPOK Computer Device [1558:6507]
    Kernel driver in use: r8168
02:00.0 Network controller [0280]: Intel Corporation Wireless 8260 [8086:24f3] (rev 3a)
    Subsystem: Intel Corporation Device [8086:1010]
gareth@gareth:~$ lspci -n | awk '/0200|0280/{print$2$3}'
0200:10ec:8168
0280:8086:24f3
gareth@gareth:~$ lsusb
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 004: ID 07d1:3c16 D-Link System DWA-125 Wireless N 150 Adapter(rev.A2) [Ralink RT3070]
Bus 001 Device 003: ID 8087:0a2b Intel Corp. 
Bus 001 Device 002: ID 5986:066d Acer, Inc 
Bus 001 Device 005: ID 045e:0040 Microsoft Corp. Wheel Mouse Optical
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
gareth@gareth:~$ rfkill list all
0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
```

The D-Link USB I'm just using to connect for now

---

### Post by Hadaka on 2016-02-18
Hi, These are your current network cards..

```
 #Wired----------RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168]
 #Wireless--------Network controller [0280]: Intel Corporation Wireless 8260 [8086:24f3]
  #USB Wireless--D-Link System DWA-125 Wireless N 150 Adapter(rev.A2) [Ralink RT3070]
```

Your internal Intel wireless card should work with your current kernel.
Please remove the USB Wireless module,then from a working wired connection
open a terminal ctrl/alt/t and do..
```
sudo apt-get update
sudo apt-get dist-upgrade
```
boot,remove the wired connection and test wireless.
**If your internal wireless card is still not working go here
[http://ubuntuforums.org/showthread.php?t=370108](http://ubuntuforums.org/showthread.php?t=370108)
then post your wireless-info.txt file that will be created in your home directory
thanks.

---

### Post by gareth15 on 2016-02-18
Hi,

I did as you said, wifi still not coming up.

Wireless.txt gives```

########## wireless info START ##########

Report from: 18 Feb 2016 13:01 EST -0500

Booted last: 18 Feb 2016 12:59 EST -0500

Script from: 27 Sep 2015 00:34 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.4 LTS
Release:    14.04
Codename:    trusty

##### kernel ############################

Linux 3.19.0-49-generic #55~14.04.1-Ubuntu SMP Fri Jan 22 11:24:31 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, noprompt, persistent, quiet, splash, vt.handoff=7

##### desktop ###########################

Ubuntu

##### lspci #############################

01:00.1 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 12)
    Subsystem: CLEVO/KAPOK Computer Device [1558:6507]
    Kernel driver in use: r8169

02:00.0 Network controller [0280]: Intel Corporation Wireless 8260 [8086:24f3] (rev 3a)
    Subsystem: Intel Corporation Device [8086:1010]

##### lsusb #############################

Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 004: ID 07d1:3c16 D-Link System DWA-125 Wireless N 150 Adapter(rev.A2) [Ralink RT3070]
Bus 001 Device 003: ID 8087:0a2b Intel Corp. 
Bus 001 Device 002: ID 5986:066d Acer, Inc 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

##### lsmod #############################

rt2800usb              28672  0 
rt2x00usb              24576  1 rt2800usb
rt2800lib              90112  1 rt2800usb
rt2x00lib              57344  3 rt2x00usb,rt2800lib,rt2800usb
mac80211              712704  3 rt2x00lib,rt2x00usb,rt2800lib
cfg80211              524288  2 mac80211,rt2x00lib
crc_ccitt              16384  1 rt2800lib
wmi                    20480  0 

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
          inet addr:142.157.92.73  Bcast:142.157.93.255  Mask:255.255.254.0
          inet6 addr: fe80::<IP6 'wlan0' [IF]>/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:597 errors:0 dropped:0 overruns:0 frame:0
          TX packets:580 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:509903 (509.9 KB)  TX bytes:72301 (72.3 KB)

##### iwconfig ##########################

eth0      no wireless extensions.

lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"mcgill.ca"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: <MAC 'mcgill.ca' [AC1]>   
          Bit Rate=48 Mb/s   Tx-Power=20 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=55/70  Signal level=-55 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         142.157.92.1    0.0.0.0         UG    0      0        0 wlan0
142.157.92.0    0.0.0.0         255.255.254.0   U     9      0        0 wlan0

##### resolv.conf #######################

nameserver 127.0.1.1
search campus.MCGILL.CA

##### network managers ##################

Installed:

    NetworkManager

Running:

root       796     1  0 12:59 ?        00:00:00 NetworkManager

##### NetworkManager info ###############

NetworkManager Tool

State: connected (global)

- Device: wlan0  [mcgill.ca] ---------------------------------------------------
  Type:              802.11 WiFi
  Driver:            rt2800usb
  State:             connected
  Default:           yes
  HW Address:        <MAC 'wlan0' [IF]>

  Capabilities:
    Speed:           48 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    Mascarillons_2:  Infra, <MAC 'Mascarillons_2' [AC10]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 100 WPA2
    SharfNahonLab:   Infra, <MAC 'SharfNahonLab' [AC8]>, Freq 2417 MHz, Rate 54 Mb/s, Strength 100 WPA WPA2
    wpa.mcgill.ca:   Infra, <MAC 'wpa.mcgill.ca' [AC2]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 82 WPA2 Enterprise
    eduroam:         Infra, <MAC 'eduroam' [AC3]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 82 WPA2 Enterprise
    wpa.mcgill.ca:   Infra, <MAC 'wpa.mcgill.ca' [AC4]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 69 WPA2 Enterprise
    eduroam:         Infra, <MAC 'eduroam' [AC5]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 69 WPA2 Enterprise
    samprada:        Infra, <MAC 'samprada' [AC9]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 52 WPA2
    wpa.mcgill.ca:   Infra, <MAC 'wpa.mcgill.ca' [AC7]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 49 WPA2 Enterprise
    mcgill.ca:       Infra, <MAC 'mcgill.ca' [AC6]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 49
    wpa.mcgill.ca:   Infra, <MAC 'wpa.mcgill.ca' [AC16]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 52 WPA2 Enterprise
    eduroam:         Infra, <MAC 'eduroam' [AC17]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 52 WPA2 Enterprise
    mcgill.ca:       Infra, <MAC 'mcgill.ca' [AC15]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 49
    mcgill.ca:       Infra, <MAC 'mcgill.ca' [AC11]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 45
    eduroam:         Infra, <MAC 'eduroam' [AC13]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 32 WPA2 Enterprise
    mcgill.ca:       Infra, <MAC 'mcgill.ca' [AC12]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 35
    *mcgill.ca:      Infra, <MAC 'mcgill.ca' [AC1]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 67

  IPv4 Settings:
    Address:         142.157.92.73
    Prefix:          23 (255.255.254.0)
    Gateway:         142.157.92.1

    DNS:             132.206.85.18
    DNS:             132.206.85.19
    DNS:             132.206.85.20
    DNS:             132.206.85.36

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

[ifupdown]
managed=false

##### NetworkManager profiles ###########

[[/etc/NetworkManager/system-connections/mcgill.ca]] (600 root)
[connection] id=mcgill.ca | type=802-11-wireless
[802-11-wireless] ssid=mcgill.ca | mac-address=<MAC 'wlan0' [IF]>
[ipv6] method=auto
[ipv4] method=auto

##### iw reg get ########################

Region: America/New_York (based on set time zone)

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
          Current Frequency:2.412 GHz (Channel 1)

##### iwlist scan #######################

eth0      Interface doesn't support scanning.

lo        Interface doesn't support scanning.

Channel occupancy:

      19   APs on   Frequency:2.412 GHz (Channel 1)
      1   APs on   Frequency:2.417 GHz (Channel 2)
      2   APs on   Frequency:2.437 GHz (Channel 6)

wlan0     Scan completed :
          Cell 01 - Address: <MAC 'mcgill.ca' [AC1]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=59/70  Signal level=-51 dBm  
                    Encryption key:off
                    ESSID:"mcgill.ca"
                    Bit Rates:9 Mb/s; 11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000009e5fa337e
                    Extra: Last beacon: 52ms ago
          Cell 02 - Address: <MAC 'wpa.mcgill.ca' [AC2]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=61/70  Signal level=-49 dBm  
                    Encryption key:on
                    ESSID:"wpa.mcgill.ca"
                    Bit Rates:9 Mb/s; 11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000009e5fa3568
                    Extra: Last beacon: 52ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
          Cell 03 - Address: <MAC 'eduroam' [AC3]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=59/70  Signal level=-51 dBm  
                    Encryption key:on
                    ESSID:"eduroam"
                    Bit Rates:9 Mb/s; 11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000009e5fa3765
                    Extra: Last beacon: 52ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
          Cell 04 - Address: <MAC 'wpa.mcgill.ca' [AC4]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=39/70  Signal level=-71 dBm  
                    Encryption key:on
                    ESSID:"wpa.mcgill.ca"
                    Bit Rates:9 Mb/s; 11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000002b42da74a
                    Extra: Last beacon: 296ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
          Cell 05 - Address: <MAC 'eduroam' [AC5]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=41/70  Signal level=-69 dBm  
                    Encryption key:on
                    ESSID:"eduroam"
                    Bit Rates:9 Mb/s; 11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000002b48bc6ec
                    Extra: Last beacon: 296ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
          Cell 06 - Address: <MAC 'mcgill.ca' [AC6]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=35/70  Signal level=-75 dBm  
                    Encryption key:off
                    ESSID:"mcgill.ca"
                    Bit Rates:11 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000d346d1181
                    Extra: Last beacon: 296ms ago
          Cell 07 - Address: <MAC 'wpa.mcgill.ca' [AC7]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=35/70  Signal level=-75 dBm  
                    Encryption key:on
                    ESSID:"wpa.mcgill.ca"
                    Bit Rates:11 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000d346d1291
                    Extra: Last beacon: 296ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
          Cell 08 - Address: <MAC 'SharfNahonLab' [AC8]>
                    Channel:2
                    Frequency:2.417 GHz (Channel 2)
                    Quality=63/70  Signal level=-47 dBm  
                    Encryption key:on
                    ESSID:"SharfNahonLab"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000009e6f4ce1327
                    Extra: Last beacon: 52ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
          Cell 09 - Address: <MAC 'samprada' [AC9]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=35/70  Signal level=-75 dBm  
                    Encryption key:on
                    ESSID:"samprada"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000415697776
                    Extra: Last beacon: 26316ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 10 - Address: <MAC 'Mascarillons_2' [AC10]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=70/70  Signal level=-39 dBm  
                    Encryption key:on
                    ESSID:"Mascarillons_2"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000071fe51352
                    Extra: Last beacon: 52ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 11 - Address: <MAC 'mcgill.ca' [AC11]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=37/70  Signal level=-73 dBm  
                    Encryption key:off
                    ESSID:"mcgill.ca"
                    Bit Rates:9 Mb/s; 11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000002b3e01d2d
                    Extra: Last beacon: 296ms ago
          Cell 12 - Address: <MAC 'mcgill.ca' [AC12]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=29/70  Signal level=-81 dBm  
                    Encryption key:off
                    ESSID:"mcgill.ca"
                    Bit Rates:11 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000008e960d181
                    Extra: Last beacon: 2008ms ago
          Cell 13 - Address: <MAC 'eduroam' [AC13]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=29/70  Signal level=-81 dBm  
                    Encryption key:on
                    ESSID:"eduroam"
                    Bit Rates:11 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000008e9671e78
                    Extra: Last beacon: 1596ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
          Cell 14 - Address: <MAC 'eduroam' [AC14]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=33/70  Signal level=-77 dBm  
                    Encryption key:on
                    ESSID:"eduroam"
                    Bit Rates:11 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000d346d13b4
                    Extra: Last beacon: 292ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
          Cell 15 - Address: <MAC 'mcgill.ca' [AC15]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=35/70  Signal level=-75 dBm  
                    Encryption key:off
                    ESSID:"mcgill.ca"
                    Bit Rates:11 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000d2312e181
                    Extra: Last beacon: 1004ms ago
          Cell 16 - Address: <MAC 'wpa.mcgill.ca' [AC16]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=35/70  Signal level=-75 dBm  
                    Encryption key:on
                    ESSID:"wpa.mcgill.ca"
                    Bit Rates:11 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000d2312e291
                    Extra: Last beacon: 1004ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
          Cell 17 - Address: <MAC 'eduroam' [AC17]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=35/70  Signal level=-75 dBm  
                    Encryption key:on
                    ESSID:"eduroam"
                    Bit Rates:11 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000d2312e3b4
                    Extra: Last beacon: 1004ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
          Cell 18 - Address: <MAC 'eduroam' [AC18]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=29/70  Signal level=-81 dBm  
                    Encryption key:on
                    ESSID:"eduroam"
                    Bit Rates:11 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000072e1f63b4
                    Extra: Last beacon: 2208ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
          Cell 19 - Address: <MAC 'mcgill.ca' [AC19]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=29/70  Signal level=-81 dBm  
                    Encryption key:off
                    ESSID:"mcgill.ca"
                    Bit Rates:11 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000072e228181
                    Extra: Last beacon: 2000ms ago
          Cell 20 - Address: <MAC 'wpa.mcgill.ca' [AC20]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=33/70  Signal level=-77 dBm  
                    Encryption key:on
                    ESSID:"wpa.mcgill.ca"
                    Bit Rates:11 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000008e960d291
                    Extra: Last beacon: 2008ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
          Cell 21 - Address: <MAC 'wpa.mcgill.ca' [AC21]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=29/70  Signal level=-81 dBm  
                    Encryption key:on
                    ESSID:"wpa.mcgill.ca"
                    Bit Rates:11 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000072e228291
                    Extra: Last beacon: 2000ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
          Cell 22 - Address: <MAC 'eduroam' [AC22]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=31/70  Signal level=-79 dBm  
                    Encryption key:on
                    ESSID:"eduroam"
                    Bit Rates:11 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s

##### module infos ######################

[rt2800usb]
filename:       /lib/modules/3.19.0-49-generic/kernel/drivers/net/wireless/rt2x00/rt2800usb.ko
license:        GPL
firmware:       rt2870.bin
description:    Ralink RT2800 USB Wireless LAN driver.
version:        2.3.0
author:         http://rt2x00.serialmonkey.com
srcversion:     CDB4A56A88AAEC3126F6347
depends:        rt2x00lib,rt2800lib,rt2x00usb
intree:         Y
vermagic:       3.19.0-49-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        A9:32:DC:23:78:95:A4:4D:39:59:BF:91:A3:56:6A:20:EE:21:1F:37
sig_hashalgo:   sha512
parm:           nohwcrypt:Disable hardware encryption. (bool)

[rt2x00usb]
filename:       /lib/modules/3.19.0-49-generic/kernel/drivers/net/wireless/rt2x00/rt2x00usb.ko
license:        GPL
description:    rt2x00 usb library
version:        2.3.0
author:         http://rt2x00.serialmonkey.com
srcversion:     B51D09F4F13F9196B61EBE4
depends:        rt2x00lib,mac80211
intree:         Y
vermagic:       3.19.0-49-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        A9:32:DC:23:78:95:A4:4D:39:59:BF:91:A3:56:6A:20:EE:21:1F:37
sig_hashalgo:   sha512

[rt2800lib]
filename:       /lib/modules/3.19.0-49-generic/kernel/drivers/net/wireless/rt2x00/rt2800lib.ko
license:        GPL
description:    Ralink RT2800 library
version:        2.3.0
author:         http://rt2x00.serialmonkey.com, Bartlomiej Zolnierkiewicz
srcversion:     491D0D9622C1740D95E8041
depends:        rt2x00lib,mac80211,crc-ccitt
intree:         Y
vermagic:       3.19.0-49-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        A9:32:DC:23:78:95:A4:4D:39:59:BF:91:A3:56:6A:20:EE:21:1F:37
sig_hashalgo:   sha512

[rt2x00lib]
filename:       /lib/modules/3.19.0-49-generic/kernel/drivers/net/wireless/rt2x00/rt2x00lib.ko
license:        GPL
description:    rt2x00 library
version:        2.3.0
author:         http://rt2x00.serialmonkey.com
srcversion:     7C3B03973B59C2A2A136B6C
depends:        mac80211,cfg80211
intree:         Y
vermagic:       3.19.0-49-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        A9:32:DC:23:78:95:A4:4D:39:59:BF:91:A3:56:6A:20:EE:21:1F:37
sig_hashalgo:   sha512

[mac80211]
filename:       /lib/modules/3.19.0-49-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     1261743510839D352D1D895
depends:        cfg80211
intree:         Y
vermagic:       3.19.0-49-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        A9:32:DC:23:78:95:A4:4D:39:59:BF:91:A3:56:6A:20:EE:21:1F:37
sig_hashalgo:   sha512
parm:           minstrel_vht_only:Use only VHT rates when VHT is supported by sta. (bool)
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[cfg80211]
filename:       /lib/modules/3.19.0-49-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     EF182B558008C23DD85EF03
depends:        
intree:         Y
vermagic:       3.19.0-49-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        A9:32:DC:23:78:95:A4:4D:39:59:BF:91:A3:56:6A:20:EE:21:1F:37
sig_hashalgo:   sha512
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

##### module parameters #################

[rt2800usb]
nohwcrypt: N

[mac80211]
beacon_loss_count: 7
ieee80211_default_rc_algo: minstrel_ht
max_nullfunc_tries: 2
max_probe_tries: 5
minstrel_vht_only: Y
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
# USB device 0x:0x (rt2800usb)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

##### dmesg #############################

[   12.582417] r8169 0000:01:00.1 eth0: link down
[   12.582455] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   67.682656] ieee80211 phy0: rt2x00_set_rt: Info - RT chipset 3070, rev 0201 detected
[   67.692333] ieee80211 phy0: rt2x00_set_rf: Info - RF chipset 0005 detected
[   67.709346] ieee80211 phy0: rt2x00lib_request_firmware: Info - Loading firmware file 'rt2870.bin'
[   67.738969] ieee80211 phy0: rt2x00lib_request_firmware: Info - Firmware detected - version: 0.29
[   67.978444] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   70.435428] wlan0: authenticate with <MAC 'mcgill.ca' [AC1]>
[   70.469741] wlan0: send auth to <MAC 'mcgill.ca' [AC1]> (try 1/3)
[   70.575218] wlan0: send auth to <MAC 'mcgill.ca' [AC1]> (try 2/3)
[   70.579311] wlan0: authenticated
[   70.579451] rt2800usb 1-6:1.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[   70.579455] rt2800usb 1-6:1.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[   70.583274] wlan0: associate with <MAC 'mcgill.ca' [AC1]> (try 1/3)
[   70.591678] wlan0: RX AssocResp from <MAC 'mcgill.ca' [AC1]> (capab=0x421 status=0 aid=2)
[   70.595034] wlan0: associated
[   70.595060] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   70.595484] wlan0: deauthenticating from <MAC 'mcgill.ca' [AC1]> by local choice (Reason: 2=PREV_AUTH_NOT_VALID)
[   70.633784] wlan0: authenticate with <MAC 'mcgill.ca' [AC1]>
[   70.653453] wlan0: send auth to <MAC 'mcgill.ca' [AC1]> (try 1/3)
[   70.662379] wlan0: authenticated
[   70.662588] rt2800usb 1-6:1.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[   70.662593] rt2800usb 1-6:1.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[   70.663201] wlan0: associate with <MAC 'mcgill.ca' [AC1]> (try 1/3)
[   70.675253] wlan0: RX AssocResp from <MAC 'mcgill.ca' [AC1]> (capab=0x421 status=0 aid=2)
[   70.678404] wlan0: associated
[   80.679834] wlan0: deauthenticating from <MAC 'mcgill.ca' [AC1]> by local choice (Reason: 3=DEAUTH_LEAVING)
[   93.191524] wlan0: authenticate with <MAC 'mcgill.ca' [AC1]>
[   93.225958] wlan0: send auth to <MAC 'mcgill.ca' [AC1]> (try 1/3)
[   93.229722] wlan0: authenticated
[   93.229896] rt2800usb 1-6:1.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[   93.229900] rt2800usb 1-6:1.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[   93.231693] wlan0: associate with <MAC 'mcgill.ca' [AC1]> (try 1/3)
[   93.241988] wlan0: RX AssocResp from <MAC 'mcgill.ca' [AC1]> (capab=0x421 status=0 aid=2)
[   93.244923] wlan0: associated

########## wireless info END ############


```

---

### Post by Hadaka on 2016-02-18
OK, please open a terminal then Copy and paste..
```
sudo iw reg set US
sudo sed -i 's/^REG.*=$/&US/' /etc/default/crda
```
Once that is complete REMOVE the  Wireless USB .. you will
not have an internet connection as expected, for the following it is not needed.
***IF you can have a wired connection that would be fine but do not insert the wireless USB
open a terminal and do..
```
sudo modprobe -r iwldvm
sudo modprobe -r iwlwifi
sudo modprobe -v iwlwifi
```
then do and post..
```
modinfo iwlwifi | grep -i 24F3
modinfo iwlwifi | grep -i 1010
dmesg | grep iwl
```
still hopefully with NO usb inserted
remove the wired connection if you had one,boot and test the wireless
thanks.

---

### Post by gareth15 on 2016-02-24
Hi, sorry for the delayed response, I was away. 

The first time I tried ```
modprobe -r iwlwifi 

``` it gave me a fatal error, but I retried those three modprobe commands and they then generated no errors. 

Then I checked out these info:

```
 gareth@gareth:~$modinfo iwlwifi | grep -i 24F3alias:         pci:v00008086d000024F3sv*sd00000004bc*sc*i* 
alias:         pci:v00008086d000024F3sv*sd00000010bc*sc*i* 
gareth@gareth:~$modinfo iwlwifi | grep -i 1010 
alias:         pci:v00008086d0000095Asv*sd00001010bc*sc*i* 
gareth@gareth:~$dmesg | grep iwl 
gareth@gareth:~$  
```

then unplugged wired connection and rebooted, no cigar.

Btw I'm in Canada, should I replace the 'US' with 'CA'?

Thanks so much

---

### Post by gareth15 on 2016-02-24
The error I got again when trying 'CA' instead of 'US'  is this: 

```
 gareth@gareth:~$ sudo iw reg set CA[sudo] password for gareth: 
gareth@gareth:~$ sudo sed -i 's/^REG.*=$/&CA/' /etc/default/crda
gareth@gareth:~$ sudo modprobe -r iwldvm
gareth@gareth:~$ sudo modprobe -r iwlwifi
rmmod: ERROR: missing module name.
modprobe: FATAL: Error running remove command for iwlwifi
gareth@gareth:~$ sudo modprobe -v iwlwifi
insmod /lib/modules/3.19.0-49-generic/kernel/drivers/net/wireless/iwlwifi/iwlwifi.ko 
gareth@gareth:~$ 

```

---

### Post by praseodym on 2016-02-25
Try installing the latest firmware files from 15.10:

[http://security.ubuntu.com/ubuntu/pool/main/l/linux-firmware/linux-firmware_1.149.2_all.deb](http://security.ubuntu.com/ubuntu/pool/main/l/linux-firmware/linux-firmware_1.149.2_all.deb)

Reboot afterwards and run
```

dmesg >> dmesg.txt
```
It creates a file "dmesg.txt" in your /home directory. Please upload it or use any paste service. You may want to run the wireless-script again

---

### Post by jeremy31 on 2016-02-25
Post ```
lspci
``` as there is a simple solution but I don't want to use it if you have hybrid graphics as it could cause issues I might not be able to fix

---

### Post by gareth15 on 2016-02-26
```
gareth@gareth:~$ lspci00:00.0 Host bridge: Intel Corporation Sky Lake Host Bridge/DRAM Registers (rev 07)
00:02.0 VGA compatible controller: Intel Corporation Device 191b (rev 06)
00:14.0 USB controller: Intel Corporation Sunrise Point-H USB 3.0 xHCI Controller (rev 31)
00:14.2 Signal processing controller: Intel Corporation Sunrise Point-H Thermal subsystem (rev 31)
00:16.0 Communication controller: Intel Corporation Sunrise Point-H CSME HECI #1 (rev 31)
00:17.0 SATA controller: Intel Corporation Sunrise Point-H SATA Controller [AHCI mode] (rev 31)
00:1c.0 PCI bridge: Intel Corporation Sunrise Point-H PCI Express Root Port #5 (rev f1)
00:1c.6 PCI bridge: Intel Corporation Sunrise Point-H PCI Express Root Port #7 (rev f1)
00:1f.0 ISA bridge: Intel Corporation Sunrise Point-H LPC Controller (rev 31)
00:1f.2 Memory controller: Intel Corporation Sunrise Point-H PMC (rev 31)
00:1f.3 Audio device: Intel Corporation Sunrise Point-H HD Audio (rev 31)
00:1f.4 SMBus: Intel Corporation Sunrise Point-H SMBus (rev 31)
01:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. Device 5287 (rev 01)
01:00.1 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 12)
02:00.0 Network controller: Intel Corporation Wireless 8260 (rev 3a)



```

---

### Post by jeremy31 on 2016-02-26
```
sudo apt-get install linux-lts-wily
```
Reboot when it finishes.
This will install the 4.2 kernel from Ubuntu and it will work for your wifi

---

### Post by gareth15 on 2016-03-01
Hi, sorry for the delay, I'm using 15.10 now alongside 14.04 w/ internet working, but I still need to get 14.04 working:

Here's dmesg.txt after upgrading firmware
```
[    0.000000] Initializing cgroup subsys cpuset[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Initializing cgroup subsys cpuacct
[    0.000000] Linux version 3.19.0-49-generic (buildd@lgw01-08) (gcc version 4.8.2 (Ubuntu 4.8.2-19ubuntu1) ) #55~14.04.1-Ubuntu SMP Fri Jan 22 11:24:31 UTC 2016 (Ubuntu 3.19.0-49.55~14.04.1-generic 3.19.8-ckt12)
[    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-3.19.0-49-generic.efi.signed root=UUID=36c53fe2-ecb8-4e55-8151-e2738fbd062f ro noprompt persistent quiet splash
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   Centaur CentaurHauls
[    0.000000] e820: BIOS-provided physical RAM map:
[    0.000000] BIOS-e820: [mem 0x0000000000000000-0x0000000000057fff] usable
[    0.000000] BIOS-e820: [mem 0x0000000000058000-0x0000000000058fff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000000059000-0x000000000009dfff] usable
[    0.000000] BIOS-e820: [mem 0x000000000009e000-0x000000000009ffff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000000100000-0x0000000084013fff] usable
[    0.000000] BIOS-e820: [mem 0x0000000084014000-0x0000000084014fff] ACPI NVS
[    0.000000] BIOS-e820: [mem 0x0000000084015000-0x000000008405efff] reserved
[    0.000000] BIOS-e820: [mem 0x000000008405f000-0x0000000086dedfff] usable
[    0.000000] BIOS-e820: [mem 0x0000000086dee000-0x0000000087768fff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000087769000-0x000000008785cfff] usable
[    0.000000] BIOS-e820: [mem 0x000000008785d000-0x0000000087babfff] ACPI NVS
[    0.000000] BIOS-e820: [mem 0x0000000087bac000-0x0000000087fa3fff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000087fa4000-0x0000000087ffdfff] type 20
[    0.000000] BIOS-e820: [mem 0x0000000087ffe000-0x0000000087ffefff] usable
[    0.000000] BIOS-e820: [mem 0x0000000088000000-0x00000000880fffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000e0000000-0x00000000efffffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fe000000-0x00000000fe010fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fec00000-0x00000000fec00fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fee00000-0x00000000fee00fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000ff000000-0x00000000ffffffff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000100000000-0x0000000471ffffff] usable
[    0.000000] NX (Execute Disable) protection: active
[    0.000000] efi: EFI v2.40 by American Megatrends
[    0.000000] efi:  ESRT=0x87eeaf98  ACPI=0x87b73000  ACPI 2.0=0x87b73000  SMBIOS=0x87ee9000  SMBIOS 3.0=0x87ee8000 
[    0.000000] esrt: Reserving ESRT space from 0x0000000087eeaf98 to 0x0000000087eeafd0.
[    0.000000] SMBIOS 3.0 present.
[    0.000000] e820: update [mem 0x00000000-0x00000fff] usable ==> reserved
[    0.000000] e820: remove [mem 0x000a0000-0x000fffff] usable
[    0.000000] AGP: No AGP bridge found
[    0.000000] e820: last_pfn = 0x472000 max_arch_pfn = 0x400000000
[    0.000000] MTRR default type: write-back
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 00C0000000 mask 7FC0000000 uncachable
[    0.000000]   1 base 00A0000000 mask 7FE0000000 uncachable
[    0.000000]   2 base 0090000000 mask 7FF0000000 uncachable
[    0.000000]   3 base 008C000000 mask 7FFC000000 uncachable
[    0.000000]   4 base 008A000000 mask 7FFE000000 uncachable
[    0.000000]   5 base 0089000000 mask 7FFF000000 uncachable
[    0.000000]   6 base 0088800000 mask 7FFF800000 uncachable
[    0.000000]   7 disabled
[    0.000000]   8 disabled
[    0.000000]   9 disabled
[    0.000000] PAT configuration [0-7]: WB  WC  UC- UC  WB  WC  UC- UC  
[    0.000000] e820: last_pfn = 0x87fff max_arch_pfn = 0x400000000
[    0.000000] Scanning 1 areas for low memory corruption
[    0.000000] Base memory trampoline at [ffff880000098000] 98000 size 24576
[    0.000000] Using GB pages for direct mapping
[    0.000000] init_memory_mapping: [mem 0x00000000-0x000fffff]
[    0.000000]  [mem 0x00000000-0x000fffff] page 4k
[    0.000000] BRK [0x02fd4000, 0x02fd4fff] PGTABLE
[    0.000000] BRK [0x02fd5000, 0x02fd5fff] PGTABLE
[    0.000000] BRK [0x02fd6000, 0x02fd6fff] PGTABLE
[    0.000000] init_memory_mapping: [mem 0x471e00000-0x471ffffff]
[    0.000000]  [mem 0x471e00000-0x471ffffff] page 2M
[    0.000000] BRK [0x02fd7000, 0x02fd7fff] PGTABLE
[    0.000000] init_memory_mapping: [mem 0x460000000-0x471dfffff]
[    0.000000]  [mem 0x460000000-0x471dfffff] page 2M
[    0.000000] init_memory_mapping: [mem 0x440000000-0x45fffffff]
[    0.000000]  [mem 0x440000000-0x45fffffff] page 2M
[    0.000000] init_memory_mapping: [mem 0x00100000-0x84013fff]
[    0.000000]  [mem 0x00100000-0x001fffff] page 4k
[    0.000000]  [mem 0x00200000-0x3fffffff] page 2M
[    0.000000]  [mem 0x40000000-0x7fffffff] page 1G
[    0.000000]  [mem 0x80000000-0x83ffffff] page 2M
[    0.000000]  [mem 0x84000000-0x84013fff] page 4k
[    0.000000] init_memory_mapping: [mem 0x8405f000-0x86dedfff]
[    0.000000]  [mem 0x8405f000-0x841fffff] page 4k
[    0.000000]  [mem 0x84200000-0x86bfffff] page 2M
[    0.000000]  [mem 0x86c00000-0x86dedfff] page 4k
[    0.000000] BRK [0x02fd8000, 0x02fd8fff] PGTABLE
[    0.000000] init_memory_mapping: [mem 0x87769000-0x8785cfff]
[    0.000000]  [mem 0x87769000-0x8785cfff] page 4k
[    0.000000] BRK [0x02fd9000, 0x02fd9fff] PGTABLE
[    0.000000] init_memory_mapping: [mem 0x87ffe000-0x87ffefff]
[    0.000000]  [mem 0x87ffe000-0x87ffefff] page 4k
[    0.000000] init_memory_mapping: [mem 0x100000000-0x43fffffff]
[    0.000000]  [mem 0x100000000-0x43fffffff] page 1G
[    0.000000] RAMDISK: [mem 0x35a26000-0x36d0afff]
[    0.000000] ACPI: Early table checksum verification disabled
[    0.000000] ACPI: RSDP 0x0000000087B73000 000024 (v02 ALASKA)
[    0.000000] ACPI: XSDT 0x0000000087B73090 00009C (v01 ALASKA A M I    01072009 AMI  00010013)
[    0.000000] ACPI: FACP 0x0000000087B8D548 00010C (v05 ALASKA A M I    01072009 AMI  00010013)
[    0.000000] ACPI: DSDT 0x0000000087B731C0 01A381 (v02 ALASKA A M I    01072009 INTL 20120913)
[    0.000000] ACPI: FACS 0x0000000087BABF80 000040
[    0.000000] ACPI: APIC 0x0000000087B8D658 0000BC (v03 ALASKA A M I    01072009 AMI  00010013)
[    0.000000] ACPI: FPDT 0x0000000087B8D718 000044 (v01 ALASKA A M I    01072009 AMI  00010013)
[    0.000000] ACPI: FIDT 0x0000000087B8D760 00009C (v01 ALASKA A M I    01072009 AMI  00010013)
[    0.000000] ACPI: MCFG 0x0000000087B8D800 00003C (v01 ALASKA A M I    01072009 MSFT 00000097)
[    0.000000] ACPI: HPET 0x0000000087B8D840 000038 (v01 ALASKA A M I    01072009 AMI. 0005000B)
[    0.000000] ACPI: SSDT 0x0000000087B8D878 000315 (v01 SataRe SataTabl 00001000 INTL 20120913)
[    0.000000] ACPI: DBGP 0x0000000087B8DB90 000034 (v01 INTEL           00000000 MSFT 0000005F)
[    0.000000] ACPI: DBG2 0x0000000087B8DBC8 000054 (v00 INTEL           00000000 MSFT 0000005F)
[    0.000000] ACPI: SSDT 0x0000000087B8DC20 0056B2 (v02 SaSsdt SaSsdt   00003000 INTL 20120913)
[    0.000000] ACPI: UEFI 0x0000000087B932D8 000042 (v01                 00000000      00000000)
[    0.000000] ACPI: SSDT 0x0000000087B93320 000E58 (v02 CpuRef CpuSsdt  00003000 INTL 20120913)
[    0.000000] ACPI: BGRT 0x0000000087B94178 000038 (v01 ALASKA A M I    01072009 AMI  00010013)
[    0.000000] ACPI: DMAR 0x0000000087B941B0 0000A8 (v01 INTEL  SKL      00000001 INTL 00000001)
[    0.000000] ACPI: ASF! 0x0000000087B94258 0000A5 (v32 INTEL   HCG     00000001 TFSM 000F4240)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at [mem 0x0000000000000000-0x0000000471ffffff]
[    0.000000] NODE_DATA(0) allocated [mem 0x471ff7000-0x471ffbfff]
[    0.000000]  [ffffea0000000000-ffffea0011dfffff] PMD -> [ffff880461600000-ffff8804715fffff] on node 0
[    0.000000] Zone ranges:
[    0.000000]   DMA      [mem 0x00001000-0x00ffffff]
[    0.000000]   DMA32    [mem 0x01000000-0xffffffff]
[    0.000000]   Normal   [mem 0x100000000-0x471ffffff]
[    0.000000] Movable zone start for each node
[    0.000000] Early memory node ranges
[    0.000000]   node   0: [mem 0x00001000-0x00057fff]
[    0.000000]   node   0: [mem 0x00059000-0x0009dfff]
[    0.000000]   node   0: [mem 0x00100000-0x84013fff]
[    0.000000]   node   0: [mem 0x8405f000-0x86dedfff]
[    0.000000]   node   0: [mem 0x87769000-0x8785cfff]
[    0.000000]   node   0: [mem 0x87ffe000-0x87ffefff]
[    0.000000]   node   0: [mem 0x100000000-0x471ffffff]
[    0.000000] Initmem setup node 0 [mem 0x00001000-0x471ffffff]
[    0.000000] On node 0 totalpages: 4165172
[    0.000000]   DMA zone: 64 pages used for memmap
[    0.000000]   DMA zone: 22 pages reserved
[    0.000000]   DMA zone: 3996 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 8571 pages used for memmap
[    0.000000]   DMA32 zone: 548504 pages, LIFO batch:31
[    0.000000]   Normal zone: 56448 pages used for memmap
[    0.000000]   Normal zone: 3612672 pages, LIFO batch:31
[    0.000000] Reserving Intel graphics stolen memory at 0x89000000-0x8cffffff
[    0.000000] ACPI: PM-Timer IO Port: 0x1808
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x02] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x04] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x06] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x05] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x06] lapic_id[0x03] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x07] lapic_id[0x05] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x08] lapic_id[0x07] enabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x02] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x03] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x04] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x05] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x06] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x07] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x08] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-119
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x8086a701 base: 0xfed00000
[    0.000000] smpboot: Allowing 8 CPUs, 0 hotplug CPUs
[    0.000000] PM: Registered nosave memory: [mem 0x00000000-0x00000fff]
[    0.000000] PM: Registered nosave memory: [mem 0x00058000-0x00058fff]
[    0.000000] PM: Registered nosave memory: [mem 0x0009e000-0x0009ffff]
[    0.000000] PM: Registered nosave memory: [mem 0x000a0000-0x000fffff]
[    0.000000] PM: Registered nosave memory: [mem 0x84014000-0x84014fff]
[    0.000000] PM: Registered nosave memory: [mem 0x84015000-0x8405efff]
[    0.000000] PM: Registered nosave memory: [mem 0x86dee000-0x87768fff]
[    0.000000] PM: Registered nosave memory: [mem 0x8785d000-0x87babfff]
[    0.000000] PM: Registered nosave memory: [mem 0x87bac000-0x87fa3fff]
[    0.000000] PM: Registered nosave memory: [mem 0x87fa4000-0x87ffdfff]
[    0.000000] PM: Registered nosave memory: [mem 0x87fff000-0x87ffffff]
[    0.000000] PM: Registered nosave memory: [mem 0x88000000-0x880fffff]
[    0.000000] PM: Registered nosave memory: [mem 0x88100000-0x88ffffff]
[    0.000000] PM: Registered nosave memory: [mem 0x89000000-0x8cffffff]
[    0.000000] PM: Registered nosave memory: [mem 0x8d000000-0xdfffffff]
[    0.000000] PM: Registered nosave memory: [mem 0xe0000000-0xefffffff]
[    0.000000] PM: Registered nosave memory: [mem 0xf0000000-0xfdffffff]
[    0.000000] PM: Registered nosave memory: [mem 0xfe000000-0xfe010fff]
[    0.000000] PM: Registered nosave memory: [mem 0xfe011000-0xfebfffff]
[    0.000000] PM: Registered nosave memory: [mem 0xfec00000-0xfec00fff]
[    0.000000] PM: Registered nosave memory: [mem 0xfec01000-0xfedfffff]
[    0.000000] PM: Registered nosave memory: [mem 0xfee00000-0xfee00fff]
[    0.000000] PM: Registered nosave memory: [mem 0xfee01000-0xfeffffff]
[    0.000000] PM: Registered nosave memory: [mem 0xff000000-0xffffffff]
[    0.000000] e820: [mem 0x8d000000-0xdfffffff] available for PCI devices
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:256 nr_cpumask_bits:256 nr_cpu_ids:8 nr_node_ids:1
[    0.000000] PERCPU: Embedded 31 pages/cpu @ffff880471c00000 s86144 r8192 d32640 u262144
[    0.000000] pcpu-alloc: s86144 r8192 d32640 u262144 alloc=1*2097152
[    0.000000] pcpu-alloc: [0] 0 1 2 3 4 5 6 7 
[    0.000000] Built 1 zonelists in Node order, mobility grouping on.  Total pages: 4100067
[    0.000000] Policy zone: Normal
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.19.0-49-generic.efi.signed root=UUID=36c53fe2-ecb8-4e55-8151-e2738fbd062f ro noprompt persistent quiet splash
[    0.000000] PID hash table entries: 4096 (order: 3, 32768 bytes)
[    0.000000] xsave: enabled xstate_bv 0x1f, cntxt size 0x440 using standard form
[    0.000000] AGP: Checking aperture...
[    0.000000] AGP: No AGP bridge found
[    0.000000] Calgary: detecting Calgary via BIOS EBDA area
[    0.000000] Calgary: Unable to locate Rio Grande table in EBDA - bailing!
[    0.000000] Memory: 16238244K/16660688K available (7923K kernel code, 1174K rwdata, 3760K rodata, 1408K init, 1292K bss, 422444K reserved, 0K cma-reserved)
[    0.000000] SLUB: HWalign=64, Order=0-3, MinObjects=0, CPUs=8, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000] 	RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000] 	RCU restricting CPUs from NR_CPUS=256 to nr_cpu_ids=8.
[    0.000000] RCU: Adjusting geometry for rcu_fanout_leaf=16, nr_cpu_ids=8
[    0.000000] NR_IRQS:16640 nr_irqs:2048 16
[    0.000000] 	Offload RCU callbacks from all CPUs
[    0.000000] 	Offload RCU callbacks from CPUs: 0-7.
[    0.000000] spurious 8259A interrupt: IRQ7.
[    0.000000] Console: colour dummy device 80x25
[    0.000000] console [tty0] enabled
[    0.000000] hpet clockevent registered
[    0.000000] tsc: Fast TSC calibration failed
[    0.000000] tsc: PIT calibration matches HPET. 1 loops
[    0.000000] tsc: Detected 2590.856 MHz processor
[    0.000023] Calibrating delay loop (skipped), value calculated using timer frequency.. 5181.71 BogoMIPS (lpj=10363424)
[    0.000025] pid_max: default: 32768 minimum: 301
[    0.000029] ACPI: Core revision 20141107
[    0.019495] ACPI: All ACPI Tables successfully acquired
[    0.020936] Security Framework initialized
[    0.020947] AppArmor: AppArmor initialized
[    0.020948] Yama: becoming mindful.
[    0.021686] Dentry cache hash table entries: 2097152 (order: 12, 16777216 bytes)
[    0.024006] Inode-cache hash table entries: 1048576 (order: 11, 8388608 bytes)
[    0.024968] Mount-cache hash table entries: 32768 (order: 6, 262144 bytes)
[    0.024981] Mountpoint-cache hash table entries: 32768 (order: 6, 262144 bytes)
[    0.025153] Initializing cgroup subsys memory
[    0.025156] Initializing cgroup subsys devices
[    0.025158] Initializing cgroup subsys freezer
[    0.025159] Initializing cgroup subsys net_cls
[    0.025160] Initializing cgroup subsys blkio
[    0.025162] Initializing cgroup subsys perf_event
[    0.025163] Initializing cgroup subsys net_prio
[    0.025164] Initializing cgroup subsys hugetlb
[    0.025183] CPU: Physical Processor ID: 0
[    0.025184] CPU: Processor Core ID: 0
[    0.025187] ENERGY_PERF_BIAS: Set to 'normal', was 'performance'
[    0.025187] ENERGY_PERF_BIAS: View and update with x86_energy_perf_policy(8)
[    0.026085] mce: CPU supports 10 MCE banks
[    0.026098] CPU0: Thermal monitoring enabled (TM1)
[    0.026106] process: using mwait in idle threads
[    0.026108] Last level iTLB entries: 4KB 64, 2MB 8, 4MB 8
[    0.026108] Last level dTLB entries: 4KB 64, 2MB 0, 4MB 0, 1GB 4
[    0.026387] Freeing SMP alternatives memory: 32K (ffffffff81e87000 - ffffffff81e8f000)
[    0.029581] ftrace: allocating 30034 entries in 118 pages
[    0.039048] dmar: Host address width 39
[    0.039050] dmar: DRHD base: 0x000000fed90000 flags: 0x0
[    0.039056] dmar: IOMMU 0: reg_base_addr fed90000 ver 1:0 cap 1c0000c40660462 ecap 7e3ff0501e
[    0.039057] dmar: DRHD base: 0x000000fed91000 flags: 0x1
[    0.039061] dmar: IOMMU 1: reg_base_addr fed91000 ver 1:0 cap d2008c40660462 ecap f050da
[    0.039062] dmar: RMRR base: 0x000000874e3000 end: 0x00000087502fff
[    0.039063] dmar: RMRR base: 0x00000088800000 end: 0x0000008cffffff
[    0.040318] IOAPIC id 2 under DRHD base  0xfed91000 IOMMU 1
[    0.040319] HPET id 0 under DRHD base 0xfed91000
[    0.040320] Queued invalidation will be enabled to support x2apic and Intr-remapping.
[    0.040320] Your BIOS is broken and requested that x2apic be disabled.
[    0.040320] This will slightly decrease performance.
[    0.040320] Use 'intremap=no_x2apic_optout' to override BIOS request.
[    0.040449] Enabled IRQ remapping in xapic mode
[    0.040450] x2apic not enabled, IRQ remapping is in xapic mode
[    0.044503] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.084163] smpboot: CPU0: Intel(R) Core(TM) i7-6700HQ CPU @ 2.60GHz (fam: 06, model: 5e, stepping: 03)
[    0.084170] TSC deadline timer enabled
[    0.084190] Performance Events: no PEBS fmt3+, generic architected perfmon, full-width counters, Intel PMU driver.
[    0.084194] ... version:                4
[    0.084194] ... bit width:              48
[    0.084195] ... generic registers:      4
[    0.084196] ... value mask:             0000ffffffffffff
[    0.084196] ... max period:             0000ffffffffffff
[    0.084197] ... fixed-purpose events:   3
[    0.084197] ... event mask:             000000070000000f
[    0.084836] x86: Booting SMP configuration:
[    0.084837] .... node  #0, CPUs:      #1
[    0.098918] NMI watchdog: enabled on all CPUs, permanently consumes one hw-PMU counter.
[    0.099001]  #2 #3 #4 #5 #6 #7
[    0.183856] x86: Booted up 1 node, 8 CPUs
[    0.183859] smpboot: Total of 8 processors activated (41453.69 BogoMIPS)
[    0.190074] devtmpfs: initialized
[    0.192354] evm: security.selinux
[    0.192356] evm: security.SMACK64
[    0.192356] evm: security.SMACK64EXEC
[    0.192357] evm: security.SMACK64TRANSMUTE
[    0.192357] evm: security.SMACK64MMAP
[    0.192358] evm: security.ima
[    0.192358] evm: security.capability
[    0.192392] PM: Registering ACPI NVS region [mem 0x84014000-0x84014fff] (4096 bytes)
[    0.192393] PM: Registering ACPI NVS region [mem 0x8785d000-0x87babfff] (3469312 bytes)
[    0.192561] pinctrl core: initialized pinctrl subsystem
[    0.192701] RTC time: 19:49:28, date: 03/01/16
[    0.192791] NET: Registered protocol family 16
[    0.193900] cpuidle: using governor ladder
[    0.197902] cpuidle: using governor menu
[    0.197948] ACPI FADT declares the system doesn't support PCIe ASPM, so disable it
[    0.197949] ACPI: bus type PCI registered
[    0.197950] acpiphp: ACPI Hot Plug PCI Controller Driver version: 0.5
[    0.198010] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)
[    0.198011] PCI: MMCONFIG at [mem 0xe0000000-0xefffffff] reserved in E820
[    0.198253] PCI: Using configuration type 1 for base access
[    0.202164] ACPI: Added _OSI(Module Device)
[    0.202165] ACPI: Added _OSI(Processor Device)
[    0.202166] ACPI: Added _OSI(3.0 _SCP Extensions)
[    0.202167] ACPI: Added _OSI(Processor Aggregator Device)
[    0.207268] ACPI: Executed 23 blocks of module-level executable AML code
[    0.212735] ACPI: Dynamic OEM Table Load:
[    0.212739] ACPI: SSDT 0xFFFF88045EF14800 00037F (v02 PmRef  Cpu0Cst  00003001 INTL 20120913)
[    0.213360] ACPI: Dynamic OEM Table Load:
[    0.213363] ACPI: SSDT 0xFFFF88045EF1B000 0005DC (v02 PmRef  Cpu0Ist  00003000 INTL 20120913)
[    0.214765] ACPI: Dynamic OEM Table Load:
[    0.214768] ACPI: SSDT 0xFFFF88045EF1B800 0005AA (v02 PmRef  ApIst    00003000 INTL 20120913)
[    0.215522] ACPI: Dynamic OEM Table Load:
[    0.215524] ACPI: SSDT 0xFFFF88045EF0FA00 000119 (v02 PmRef  ApCst    00003000 INTL 20120913)
[    0.223589] ACPI: Interpreter enabled
[    0.223610] ACPI Exception: AE_NOT_FOUND, While evaluating Sleep State [\_S1_] (20141107/hwxface-580)
[    0.223616] ACPI Exception: AE_NOT_FOUND, While evaluating Sleep State [\_S2_] (20141107/hwxface-580)
[    0.223629] ACPI: (supports S0 S3 S4 S5)
[    0.223630] ACPI: Using IOAPIC for interrupt routing
[    0.223652] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    0.224917] ACPI: Power Resource [PG00] (on)
[    0.224934] ACPI: Power Resource [PG02] (on)
[    0.225163] ACPI: Power Resource [PG01] (on)
[    0.225364] ACPI: Power Resource [PG02] (on)
[    0.233877] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-fe])
[    0.233882] acpi PNP0A08:00: _OSC: OS supports [ExtendedConfig ASPM ClockPM Segments MSI]
[    0.233903] \_SB_.PCI0:_OSC invalid UUID
[    0.233903] _OSC request data:1 1f 0 
[    0.233906] acpi PNP0A08:00: _OSC failed (AE_ERROR); disabling ASPM
[    0.234323] PCI host bridge to bus 0000:00
[    0.234325] pci_bus 0000:00: root bus resource [bus 00-fe]
[    0.234326] pci_bus 0000:00: root bus resource [io  0x0000-0x0cf7]
[    0.234327] pci_bus 0000:00: root bus resource [io  0x0d00-0xffff]
[    0.234328] pci_bus 0000:00: root bus resource [mem 0x000a0000-0x000bffff]
[    0.234329] pci_bus 0000:00: root bus resource [mem 0x000c0000-0x000c3fff]
[    0.234330] pci_bus 0000:00: root bus resource [mem 0x000c4000-0x000c7fff]
[    0.234331] pci_bus 0000:00: root bus resource [mem 0x000c8000-0x000cbfff]
[    0.234332] pci_bus 0000:00: root bus resource [mem 0x000cc000-0x000cffff]
[    0.234333] pci_bus 0000:00: root bus resource [mem 0x000d0000-0x000d3fff]
[    0.234334] pci_bus 0000:00: root bus resource [mem 0x000d4000-0x000d7fff]
[    0.234335] pci_bus 0000:00: root bus resource [mem 0x000d8000-0x000dbfff]
[    0.234336] pci_bus 0000:00: root bus resource [mem 0x000dc000-0x000dffff]
[    0.234337] pci_bus 0000:00: root bus resource [mem 0x000e0000-0x000e3fff]
[    0.234338] pci_bus 0000:00: root bus resource [mem 0x000e4000-0x000e7fff]
[    0.234339] pci_bus 0000:00: root bus resource [mem 0x000e8000-0x000ebfff]
[    0.234340] pci_bus 0000:00: root bus resource [mem 0x000ec000-0x000effff]
[    0.234341] pci_bus 0000:00: root bus resource [mem 0x000f0000-0x000fffff]
[    0.234342] pci_bus 0000:00: root bus resource [mem 0x8d000000-0xdfffffff]
[    0.234343] pci_bus 0000:00: root bus resource [mem 0xfd000000-0xfe7fffff]
[    0.234348] pci 0000:00:00.0: [8086:1910] type 00 class 0x060000
[    0.234424] pci 0000:00:02.0: [8086:191b] type 00 class 0x030000
[    0.234430] pci 0000:00:02.0: reg 0x10: [mem 0xde000000-0xdeffffff 64bit]
[    0.234435] pci 0000:00:02.0: reg 0x18: [mem 0xc0000000-0xcfffffff 64bit pref]
[    0.234438] pci 0000:00:02.0: reg 0x20: [io  0xf000-0xf03f]
[    0.234567] pci 0000:00:14.0: [8086:a12f] type 00 class 0x0c0330
[    0.234584] pci 0000:00:14.0: reg 0x10: [mem 0xdf210000-0xdf21ffff 64bit]
[    0.234641] pci 0000:00:14.0: PME# supported from D3hot D3cold
[    0.234684] pci 0000:00:14.0: System wakeup disabled by ACPI
[    0.234712] pci 0000:00:14.2: [8086:a131] type 00 class 0x118000
[    0.234729] pci 0000:00:14.2: reg 0x10: [mem 0xdf22e000-0xdf22efff 64bit]
[    0.234853] pci 0000:00:16.0: [8086:a13a] type 00 class 0x078000
[    0.234874] pci 0000:00:16.0: reg 0x10: [mem 0xdf22d000-0xdf22dfff 64bit]
[    0.234941] pci 0000:00:16.0: PME# supported from D3hot
[    0.235025] pci 0000:00:17.0: [8086:a103] type 00 class 0x010601
[    0.235038] pci 0000:00:17.0: reg 0x10: [mem 0xdf228000-0xdf229fff]
[    0.235044] pci 0000:00:17.0: reg 0x14: [mem 0xdf22c000-0xdf22c0ff]
[    0.235050] pci 0000:00:17.0: reg 0x18: [io  0xf090-0xf097]
[    0.235056] pci 0000:00:17.0: reg 0x1c: [io  0xf080-0xf083]
[    0.235062] pci 0000:00:17.0: reg 0x20: [io  0xf060-0xf07f]
[    0.235069] pci 0000:00:17.0: reg 0x24: [mem 0xdf22b000-0xdf22b7ff]
[    0.235104] pci 0000:00:17.0: PME# supported from D3hot
[    0.235172] pci 0000:00:1c.0: [8086:a114] type 01 class 0x060400
[    0.235224] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.235262] pci 0000:00:1c.0: System wakeup disabled by ACPI
[    0.235301] pci 0000:00:1c.6: [8086:a116] type 01 class 0x060400
[    0.235354] pci 0000:00:1c.6: PME# supported from D0 D3hot D3cold
[    0.235393] pci 0000:00:1c.6: System wakeup disabled by ACPI
[    0.235423] pci 0000:00:1f.0: [8086:a14e] type 00 class 0x060100
[    0.235566] pci 0000:00:1f.2: [8086:a121] type 00 class 0x058000
[    0.235574] pci 0000:00:1f.2: reg 0x10: [mem 0xdf224000-0xdf227fff]
[    0.235665] pci 0000:00:1f.3: [8086:a170] type 00 class 0x040300
[    0.235685] pci 0000:00:1f.3: reg 0x10: [mem 0xdf220000-0xdf223fff 64bit]
[    0.235707] pci 0000:00:1f.3: reg 0x20: [mem 0xdf200000-0xdf20ffff 64bit]
[    0.235751] pci 0000:00:1f.3: PME# supported from D3hot D3cold
[    0.235796] pci 0000:00:1f.3: System wakeup disabled by ACPI
[    0.235825] pci 0000:00:1f.4: [8086:a123] type 00 class 0x0c0500
[    0.235871] pci 0000:00:1f.4: reg 0x10: [mem 0xdf22a000-0xdf22a0ff 64bit]
[    0.235940] pci 0000:00:1f.4: reg 0x20: [io  0xf040-0xf05f]
[    0.236129] pci 0000:01:00.0: [10ec:5287] type 00 class 0xff0000
[    0.236143] pci 0000:01:00.0: reg 0x10: [mem 0xdf115000-0xdf115fff]
[    0.236181] pci 0000:01:00.0: reg 0x30: [mem 0xdf100000-0xdf10ffff pref]
[    0.236257] pci 0000:01:00.0: supports D1 D2
[    0.236258] pci 0000:01:00.0: PME# supported from D1 D2 D3hot D3cold
[    0.236292] pci 0000:01:00.0: System wakeup disabled by ACPI
[    0.236326] pci 0000:01:00.1: [10ec:8168] type 00 class 0x020000
[    0.236342] pci 0000:01:00.1: reg 0x10: [io  0xe000-0xe0ff]
[    0.236366] pci 0000:01:00.1: reg 0x18: [mem 0xdf114000-0xdf114fff 64bit]
[    0.236381] pci 0000:01:00.1: reg 0x20: [mem 0xdf110000-0xdf113fff 64bit]
[    0.236460] pci 0000:01:00.1: supports D1 D2
[    0.236461] pci 0000:01:00.1: PME# supported from D0 D1 D2 D3hot D3cold
[    0.241904] pci 0000:00:1c.0: PCI bridge to [bus 01]
[    0.241906] pci 0000:00:1c.0:   bridge window [io  0xe000-0xefff]
[    0.241909] pci 0000:00:1c.0:   bridge window [mem 0xdf100000-0xdf1fffff]
[    0.242009] pci 0000:02:00.0: [8086:24f3] type 00 class 0x028000
[    0.242046] pci 0000:02:00.0: reg 0x10: [mem 0xdf000000-0xdf001fff 64bit]
[    0.242218] pci 0000:02:00.0: PME# supported from D0 D3hot D3cold
[    0.242276] pci 0000:02:00.0: System wakeup disabled by ACPI
[    0.249916] pci 0000:00:1c.6: PCI bridge to [bus 02]
[    0.249920] pci 0000:00:1c.6:   bridge window [mem 0xdf000000-0xdf0fffff]
[    0.250701] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 10 *11 12 14 15)
[    0.250741] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 *10 11 12 14 15)
[    0.250779] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 10 *11 12 14 15)
[    0.250817] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 10 *11 12 14 15)
[    0.250854] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 10 *11 12 14 15)
[    0.250891] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 10 *11 12 14 15)
[    0.250928] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 10 *11 12 14 15)
[    0.250965] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 10 *11 12 14 15)
[    0.251181] ACPI: Enabled 5 GPEs in block 00 to 7F
[    0.251247] ACPI : EC: GPE = 0x3, I/O: command/status = 0x66, data = 0x62
[    0.251324] vgaarb: setting as boot device: PCI:0000:00:02.0
[    0.251326] vgaarb: device added: PCI:0000:00:02.0,decodes=io+mem,owns=io+mem,locks=none
[    0.251328] vgaarb: loaded
[    0.251329] vgaarb: bridge control possible 0000:00:02.0
[    0.251471] SCSI subsystem initialized
[    0.251499] libata version 3.00 loaded.
[    0.251516] ACPI: bus type USB registered
[    0.251528] usbcore: registered new interface driver usbfs
[    0.251534] usbcore: registered new interface driver hub
[    0.251550] usbcore: registered new device driver usb
[    0.251683] PCI: Using ACPI for IRQ routing
[    0.279868] PCI: pci_cache_line_size set to 64 bytes
[    0.279933] e820: reserve RAM buffer [mem 0x00058000-0x0005ffff]
[    0.279934] e820: reserve RAM buffer [mem 0x0009e000-0x0009ffff]
[    0.279935] e820: reserve RAM buffer [mem 0x84014000-0x87ffffff]
[    0.279936] e820: reserve RAM buffer [mem 0x86dee000-0x87ffffff]
[    0.279937] e820: reserve RAM buffer [mem 0x8785d000-0x87ffffff]
[    0.279938] e820: reserve RAM buffer [mem 0x87fff000-0x87ffffff]
[    0.279939] e820: reserve RAM buffer [mem 0x472000000-0x473ffffff]
[    0.280014] NetLabel: Initializing
[    0.280015] NetLabel:  domain hash size = 128
[    0.280016] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.280023] NetLabel:  unlabeled traffic allowed by default
[    0.280101] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0, 0, 0, 0, 0
[    0.280104] hpet0: 8 comparators, 64-bit 24.000000 MHz counter
[    0.282157] Switched to clocksource hpet
[    0.286109] AppArmor: AppArmor Filesystem Enabled
[    0.286215] pnp: PnP ACPI init
[    0.286334] system 00:00: [io  0x0680-0x069f] has been reserved
[    0.286335] system 00:00: [io  0xffff] has been reserved
[    0.286336] system 00:00: [io  0xffff] has been reserved
[    0.286337] system 00:00: [io  0xffff] has been reserved
[    0.286339] system 00:00: [io  0x1800-0x18fe] could not be reserved
[    0.286340] system 00:00: [io  0x164e-0x164f] has been reserved
[    0.286341] system 00:00: [io  0x3322-0x3323] has been reserved
[    0.286343] system 00:00: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.286391] system 00:01: [io  0x0800-0x087f] has been reserved
[    0.286392] system 00:01: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.286413] pnp 00:02: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.286435] system 00:03: [io  0x1854-0x1857] has been reserved
[    0.286436] system 00:03: Plug and Play ACPI device, IDs INT3f0d PNP0c02 (active)
[    0.286457] pnp 00:04: Plug and Play ACPI device, IDs PNP0303 (active)
[    0.286526] pnp 00:05: Plug and Play ACPI device, IDs SYN1218 PNP0f13 (active)
[    0.286648] system 00:06: [mem 0xfed10000-0xfed17fff] has been reserved
[    0.286649] system 00:06: [mem 0xfed18000-0xfed18fff] has been reserved
[    0.286651] system 00:06: [mem 0xfed19000-0xfed19fff] has been reserved
[    0.286652] system 00:06: [mem 0xe0000000-0xefffffff] has been reserved
[    0.286653] system 00:06: [mem 0xfed20000-0xfed3ffff] has been reserved
[    0.286654] system 00:06: [mem 0xfed90000-0xfed93fff] could not be reserved
[    0.286655] system 00:06: [mem 0xfed45000-0xfed8ffff] has been reserved
[    0.286656] system 00:06: [mem 0xff000000-0xffffffff] has been reserved
[    0.286657] system 00:06: [mem 0xfee00000-0xfeefffff] could not be reserved
[    0.286658] system 00:06: [mem 0xdffe0000-0xdfffffff] has been reserved
[    0.286660] system 00:06: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.286685] system 00:07: [mem 0xfd000000-0xfdabffff] has been reserved
[    0.286686] system 00:07: [mem 0xfdad0000-0xfdadffff] has been reserved
[    0.286687] system 00:07: [mem 0xfdb00000-0xfdffffff] has been reserved
[    0.286688] system 00:07: [mem 0xfe000000-0xfe01ffff] could not be reserved
[    0.286689] system 00:07: [mem 0xfe036000-0xfe03bfff] has been reserved
[    0.286691] system 00:07: [mem 0xfe03d000-0xfe3fffff] has been reserved
[    0.286692] system 00:07: [mem 0xfe410000-0xfe7fffff] has been reserved
[    0.286693] system 00:07: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.286848] system 00:08: [io  0xff00-0xfffe] has been reserved
[    0.286849] system 00:08: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.287434] system 00:09: [mem 0xfdaf0000-0xfdafffff] has been reserved
[    0.287435] system 00:09: [mem 0xfdae0000-0xfdaeffff] has been reserved
[    0.287436] system 00:09: [mem 0xfdac0000-0xfdacffff] has been reserved
[    0.287438] system 00:09: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.287771] pnp: PnP ACPI: found 10 devices
[    0.296584] pci 0000:00:1c.0: PCI bridge to [bus 01]
[    0.296586] pci 0000:00:1c.0:   bridge window [io  0xe000-0xefff]
[    0.296589] pci 0000:00:1c.0:   bridge window [mem 0xdf100000-0xdf1fffff]
[    0.296594] pci 0000:00:1c.6: PCI bridge to [bus 02]
[    0.296597] pci 0000:00:1c.6:   bridge window [mem 0xdf000000-0xdf0fffff]
[    0.296602] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
[    0.296603] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
[    0.296605] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
[    0.296607] pci_bus 0000:00: resource 7 [mem 0x000c0000-0x000c3fff]
[    0.296608] pci_bus 0000:00: resource 8 [mem 0x000c4000-0x000c7fff]
[    0.296609] pci_bus 0000:00: resource 9 [mem 0x000c8000-0x000cbfff]
[    0.296610] pci_bus 0000:00: resource 10 [mem 0x000cc000-0x000cffff]
[    0.296611] pci_bus 0000:00: resource 11 [mem 0x000d0000-0x000d3fff]
[    0.296612] pci_bus 0000:00: resource 12 [mem 0x000d4000-0x000d7fff]
[    0.296613] pci_bus 0000:00: resource 13 [mem 0x000d8000-0x000dbfff]
[    0.296614] pci_bus 0000:00: resource 14 [mem 0x000dc000-0x000dffff]
[    0.296615] pci_bus 0000:00: resource 15 [mem 0x000e0000-0x000e3fff]
[    0.296616] pci_bus 0000:00: resource 16 [mem 0x000e4000-0x000e7fff]
[    0.296617] pci_bus 0000:00: resource 17 [mem 0x000e8000-0x000ebfff]
[    0.296617] pci_bus 0000:00: resource 18 [mem 0x000ec000-0x000effff]
[    0.296618] pci_bus 0000:00: resource 19 [mem 0x000f0000-0x000fffff]
[    0.296619] pci_bus 0000:00: resource 20 [mem 0x8d000000-0xdfffffff]
[    0.296620] pci_bus 0000:00: resource 21 [mem 0xfd000000-0xfe7fffff]
[    0.296621] pci_bus 0000:01: resource 0 [io  0xe000-0xefff]
[    0.296622] pci_bus 0000:01: resource 1 [mem 0xdf100000-0xdf1fffff]
[    0.296623] pci_bus 0000:02: resource 1 [mem 0xdf000000-0xdf0fffff]
[    0.296638] NET: Registered protocol family 2
[    0.296788] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.296962] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    0.297052] TCP: Hash tables configured (established 131072 bind 65536)
[    0.297072] TCP: reno registered
[    0.297085] UDP hash table entries: 8192 (order: 6, 262144 bytes)
[    0.297120] UDP-Lite hash table entries: 8192 (order: 6, 262144 bytes)
[    0.297168] NET: Registered protocol family 1
[    0.297178] pci 0000:00:02.0: Video device with shadowed ROM
[    0.297989] PCI: CLS 0 bytes, default 64
[    0.298021] Trying to unpack rootfs image as initramfs...
[    0.521502] Freeing initrd memory: 19348K (ffff880035a26000 - ffff880036d0b000)
[    0.521520] PCI-DMA: Using software bounce buffering for IO (SWIOTLB)
[    0.521522] software IO TLB [mem 0x7f32d000-0x8332d000] (64MB) mapped at [ffff88007f32d000-ffff88008332cfff]
[    0.521891] microcode: CPU0 sig=0x506e3, pf=0x20, revision=0x55
[    0.521898] microcode: CPU1 sig=0x506e3, pf=0x20, revision=0x55
[    0.521922] microcode: CPU2 sig=0x506e3, pf=0x20, revision=0x55
[    0.521945] microcode: CPU3 sig=0x506e3, pf=0x20, revision=0x55
[    0.521955] microcode: CPU4 sig=0x506e3, pf=0x20, revision=0x55
[    0.521965] microcode: CPU5 sig=0x506e3, pf=0x20, revision=0x55
[    0.521974] microcode: CPU6 sig=0x506e3, pf=0x20, revision=0x55
[    0.521984] microcode: CPU7 sig=0x506e3, pf=0x20, revision=0x55
[    0.522058] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[    0.522076] Scanning for low memory corruption every 60 seconds
[    0.522547] futex hash table entries: 2048 (order: 5, 131072 bytes)
[    0.522564] Initialise system trusted keyring
[    0.522580] audit: initializing netlink subsys (disabled)
[    0.522589] audit: type=2000 audit(1456861767.528:1): initialized
[    0.522853] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    0.523757] zpool: loaded
[    0.523758] zbud: loaded
[    0.523936] VFS: Disk quotas dquot_6.5.2
[    0.523958] VFS: Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    0.524409] fuse init (API version 7.23)
[    0.524550] Key type big_key registered
[    0.526088] Key type asymmetric registered
[    0.526090] Asymmetric key parser 'x509' registered
[    0.526164] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 252)
[    0.526385] io scheduler noop registered
[    0.526387] io scheduler deadline registered (default)
[    0.526405] io scheduler cfq registered
[    0.526660] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.526669] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.526693] efifb: probing for efifb
[    0.526708] efifb: framebuffer at 0xc0000000, mapped to 0xffffc90011c00000, using 8128k, total 8128k
[    0.526709] efifb: mode is 1920x1080x32, linelength=7680, pages=1
[    0.526709] efifb: scrolling: redraw
[    0.526710] efifb: Truecolor: size=8:8:8:8, shift=24:16:8:0
[    0.529706] Console: switching to colour frame buffer device 240x67
[    0.532688] fb0: EFI VGA frame buffer device
[    0.532694] intel_idle: does not run on family 6 model 94
[    0.533708] ACPI: AC Adapter [AC] (off-line)
[    0.534004] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0
[    0.534007] ACPI: Power Button [PWRB]
[    0.534030] input: Sleep Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0E:00/input/input1
[    0.534031] ACPI: Sleep Button [SLPB]
[    0.534052] input: Lid Switch as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0D:00/input/input2
[    0.534074] ACPI: Lid Switch [LID0]
[    0.534095] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input3
[    0.534096] ACPI: Power Button [PWRF]
[    0.534380] Monitor-Mwait will be used to enter C-1 state
[    0.534427] Monitor-Mwait will be used to enter C-2 state
[    0.534473] Monitor-Mwait will be used to enter C-3 state
[    0.534504] ACPI: acpi_idle registered with cpuidle
[    0.537215] thermal LNXTHERM:00: registered as thermal_zone0
[    0.537216] ACPI: Thermal Zone [TZ0] (45 C)
[    0.537253] GHES: HEST is not enabled!
[    0.537368] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    0.537697] ACPI: Battery Slot [BAT0] (battery present)
[    0.540188] Linux agpgart interface v0.103
[    0.541629] brd: module loaded
[    0.542397] loop: module loaded
[    0.542666] libphy: Fixed MDIO Bus: probed
[    0.542668] tun: Universal TUN/TAP device driver, 1.6
[    0.542669] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.542718] PPP generic driver version 2.4.2
[    0.542859] xhci_hcd 0000:00:14.0: xHCI Host Controller
[    0.542863] xhci_hcd 0000:00:14.0: new USB bus registered, assigned bus number 1
[    0.543934] xhci_hcd 0000:00:14.0: cache line size of 64 is not supported
[    0.543986] usb usb1: New USB device found, idVendor=1d6b, idProduct=0002
[    0.543987] usb usb1: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.543988] usb usb1: Product: xHCI Host Controller
[    0.543989] usb usb1: Manufacturer: Linux 3.19.0-49-generic xhci-hcd
[    0.543990] usb usb1: SerialNumber: 0000:00:14.0
[    0.544075] hub 1-0:1.0: USB hub found
[    0.544089] hub 1-0:1.0: 16 ports detected
[    0.550304] xhci_hcd 0000:00:14.0: xHCI Host Controller
[    0.550306] xhci_hcd 0000:00:14.0: new USB bus registered, assigned bus number 2
[    0.550326] usb usb2: New USB device found, idVendor=1d6b, idProduct=0003
[    0.550327] usb usb2: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.550328] usb usb2: Product: xHCI Host Controller
[    0.550329] usb usb2: Manufacturer: Linux 3.19.0-49-generic xhci-hcd
[    0.550330] usb usb2: SerialNumber: 0000:00:14.0
[    0.550496] hub 2-0:1.0: USB hub found
[    0.550504] hub 2-0:1.0: 8 ports detected
[    0.552359] usb: failed to peer usb2-port5 and usb1-port7 by location (usb2-port5:none) (usb1-port7:usb2-port4)
[    0.552360] usb usb2-port5: failed to peer to usb1-port7 (-16)
[    0.552360] usb: port power management may be unreliable
[    0.553095] usb: failed to peer usb2-port7 and usb1-port7 by location (usb2-port7:none) (usb1-port7:usb2-port4)
[    0.553096] usb usb2-port7: failed to peer to usb1-port7 (-16)
[    0.553463] usb: failed to peer usb2-port8 and usb1-port1 by location (usb2-port8:none) (usb1-port1:usb2-port1)
[    0.553464] usb usb2-port8: failed to peer to usb1-port1 (-16)
[    0.553542] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.553546] ehci-pci: EHCI PCI platform driver
[    0.553554] ehci-platform: EHCI generic platform driver
[    0.553559] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.553562] ohci-pci: OHCI PCI platform driver
[    0.553567] ohci-platform: OHCI generic platform driver
[    0.553572] uhci_hcd: USB Universal Host Controller Interface driver
[    0.553603] i8042: PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:SYNM] at 0x60,0x64 irq 1,12
[    1.101910] i8042: Detected active multiplexing controller, rev 1.1
[    1.103764] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.103766] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[    1.103781] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[    1.103809] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[    1.103819] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[    1.104088] mousedev: PS/2 mouse device common for all mice
[    1.104714] rtc_cmos 00:02: RTC can wake from S4
[    1.105186] rtc_cmos 00:02: rtc core: registered rtc_cmos as rtc0
[    1.105278] rtc_cmos 00:02: alarms up to one month, y3k, 242 bytes nvram, hpet irqs
[    1.105284] i2c /dev entries driver
[    1.105322] device-mapper: uevent: version 1.0.3
[    1.105431] device-mapper: ioctl: 4.29.0-ioctl (2014-10-28) initialised: dm-devel@redhat.com
[    1.105446] ledtrig-cpu: registered to indicate activity on CPUs
[    1.105467] EFI Variables Facility v0.08 2004-May-17
[    1.108256] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input4
[    1.112538] PCCT header not found.
[    1.112593] TCP: cubic registered
[    1.112650] NET: Registered protocol family 10
[    1.113181] NET: Registered protocol family 17
[    1.113201] Key type dns_resolver registered
[    1.113960] Loading compiled-in X.509 certificates
[    1.114550] Loaded X.509 cert 'Magrathea: Glacier signing key: a932dc237895a44d3959bf91a3566a20ee211f37'
[    1.114557] registered taskstats version 1
[    1.116922] Key type trusted registered
[    1.121419] Key type encrypted registered
[    1.121423] AppArmor: AppArmor sha1 policy hashing enabled
[    1.121425] ima: No TPM chip found, activating TPM-bypass!
[    1.121440] evm: HMAC attrs: 0x1
[    1.122405]   Magic number: 8:857:848
[    1.122772] rtc_cmos 00:02: setting system clock to 2016-03-01 19:49:29 UTC (1456861769)
[    1.124525] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.124527] EDD information not available.
[    1.124626] PM: Hibernation image not present or could not be loaded.
[    1.125311] Freeing unused kernel memory: 1408K (ffffffff81d27000 - ffffffff81e87000)
[    1.125313] Write protecting the kernel read-only data: 12288k
[    1.126186] Freeing unused kernel memory: 256K (ffff8800027c0000 - ffff880002800000)
[    1.126584] Freeing unused kernel memory: 336K (ffff880002bac000 - ffff880002c00000)
[    1.141184] systemd-udevd[152]: starting version 204
[    1.173173] rtsx_pci 0000:01:00.0: enabling device (0000 -> 0002)
[    1.173339] rtsx_pci 0000:01:00.0: rtsx_pci_acquire_irq: pcr->msi_en = 1, pci->irq = 123
[    1.176689] ahci 0000:00:17.0: version 3.0
[    1.177502] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    1.177522] r8169 0000:01:00.1: can't disable ASPM; OS doesn't have ASPM control
[    1.183307] r8169 0000:01:00.1 eth0: RTL8411 at 0xffffc900018d4000, 80:fa:5b:29:34:4b, XID 1c800880 IRQ 125
[    1.183312] r8169 0000:01:00.1 eth0: jumbo features [frames: 9200 bytes, tx checksumming: ko]
[    1.190339] ahci 0000:00:17.0: AHCI 0001.0301 32 slots 2 ports 6 Gbps 0xc impl SATA mode
[    1.190346] ahci 0000:00:17.0: flags: 64bit ncq sntf pm led clo only pio slum part ems deso sadm sds apst 
[    1.199345] scsi host0: ahci
[    1.199942] scsi host1: ahci
[    1.200495] scsi host2: ahci
[    1.200862] scsi host3: ahci
[    1.200952] ata1: DUMMY
[    1.200955] ata2: DUMMY
[    1.200959] ata3: SATA max UDMA/133 abar m2048@0xdf22b000 port 0xdf22b200 irq 124
[    1.200962] ata4: SATA max UDMA/133 abar m2048@0xdf22b000 port 0xdf22b280 irq 124
[    1.310084] usb 1-2: new high-speed USB device number 2 using xhci_hcd
[    1.486761] usb 1-2: New USB device found, idVendor=5986, idProduct=066d
[    1.486765] usb 1-2: New USB device strings: Mfr=3, Product=1, SerialNumber=2
[    1.486768] usb 1-2: Product: BisonCam, NB Pro
[    1.486770] usb 1-2: Manufacturer: Generic
[    1.486771] usb 1-2: SerialNumber: 200901010001
[    1.518068] ata3: SATA link up 6.0 Gbps (SStatus 133 SControl 300)
[    1.518076] tsc: Refined TSC clocksource calibration: 2591.999 MHz
[    1.518139] ata4: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    1.519001] ata3.00: ATA-8: HGST HTS725050A7E630, GS2OA230, max UDMA/133
[    1.519005] ata3.00: 976773168 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
[    1.519203] ata4.00: ATAPI: Slimtype DVD A  DS8ACSH, LX11, max UDMA/133
[    1.520019] ata3.00: configured for UDMA/133
[    1.520089] ata4.00: configured for UDMA/133
[    1.520282] scsi 2:0:0:0: Direct-Access     ATA      HGST HTS725050A7 A230 PQ: 0 ANSI: 5
[    1.520753] sd 2:0:0:0: Attached scsi generic sg0 type 0
[    1.520762] sd 2:0:0:0: [sda] 976773168 512-byte logical blocks: (500 GB/465 GiB)
[    1.520766] sd 2:0:0:0: [sda] 4096-byte physical blocks
[    1.521254] sd 2:0:0:0: [sda] Write Protect is off
[    1.521258] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.521386] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.521859] scsi 3:0:0:0: CD-ROM            Slimtype DVD A  DS8ACSH   LX11 PQ: 0 ANSI: 5
[    1.536524] sr 3:0:0:0: [sr0] scsi3-mmc drive: 10x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[    1.536527] cdrom: Uniform CD-ROM driver Revision: 3.20
[    1.536745] sr 3:0:0:0: Attached scsi CD-ROM sr0
[    1.536932] sr 3:0:0:0: Attached scsi generic sg1 type 5
[    1.595970]  sda: sda1 sda2 sda3 sda4
[    1.597345] sd 2:0:0:0: [sda] Attached SCSI disk
[    1.654022] usb 1-3: new full-speed USB device number 3 using xhci_hcd
[    1.783156] usb 1-3: New USB device found, idVendor=8087, idProduct=0a2b
[    1.783159] usb 1-3: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[    1.949970] usb 1-6: new high-speed USB device number 4 using xhci_hcd
[    2.150558] usb 1-6: New USB device found, idVendor=07d1, idProduct=3c16
[    2.150561] usb 1-6: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[    2.150564] usb 1-6: Product: 11n Adapter
[    2.150566] usb 1-6: Manufacturer: Ralink
[    2.150567] usb 1-6: SerialNumber: 1.0
[    2.211770] EXT4-fs (sda2): mounted filesystem with ordered data mode. Opts: (null)
[    2.409456] psmouse serio2: synaptics: queried max coordinates: x [..5674], y [..4758]
[    2.518476] Switched to clocksource tsc
[    2.526977] psmouse serio2: synaptics: queried min coordinates: x [1268..], y [1096..]
[    2.670067] psmouse serio2: synaptics: Touchpad model: 1, fw: 8.2, id: 0x1e2b1, caps: 0xf00123/0x840300/0x26800, board id: 3189, fw id: 1944273
[    2.695154] random: nonblocking pool is initialized
[    2.706748] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio2/input/input10
[    3.167016] init: plymouth-upstart-bridge main process (228) terminated with status 1
[    3.167028] init: plymouth-upstart-bridge main process ended, respawning
[    3.169912] init: plymouth-upstart-bridge main process (239) terminated with status 1
[    3.169922] init: plymouth-upstart-bridge main process ended, respawning
[    3.171854] init: plymouth-upstart-bridge main process (241) terminated with status 1
[    3.171866] init: plymouth-upstart-bridge main process ended, respawning
[    3.174587] init: plymouth-upstart-bridge main process (242) terminated with status 1
[    3.174598] init: plymouth-upstart-bridge main process ended, respawning
[    3.176502] init: plymouth-upstart-bridge main process (244) terminated with status 1
[    3.176514] init: plymouth-upstart-bridge main process ended, respawning
[    3.179196] init: plymouth-upstart-bridge main process (245) terminated with status 1
[    3.179207] init: plymouth-upstart-bridge main process ended, respawning
[    3.181115] init: plymouth-upstart-bridge main process (247) terminated with status 1
[    3.181127] init: plymouth-upstart-bridge main process ended, respawning
[    3.183841] init: plymouth-upstart-bridge main process (248) terminated with status 1
[    3.183851] init: plymouth-upstart-bridge main process ended, respawning
[    3.185922] init: plymouth-upstart-bridge main process (250) terminated with status 1
[    3.185933] init: plymouth-upstart-bridge main process ended, respawning
[    3.188616] init: plymouth-upstart-bridge main process (251) terminated with status 1
[    3.188627] init: plymouth-upstart-bridge main process ended, respawning
[    3.190573] init: plymouth-upstart-bridge main process (253) terminated with status 1
[    3.190585] init: plymouth-upstart-bridge respawning too fast, stopped
[    9.047625] Adding 16660476k swap on /dev/sda3.  Priority:-1 extents:1 across:16660476k FS
[    9.165261] systemd-udevd[358]: starting version 204
[    9.225999] lp: driver loaded but no devices found
[    9.232208] ppdev: user-space parallel port driver
[    9.344204] hidraw: raw HID events driver (C) Jiri Kosina
[    9.364271] wmi: Mapper loaded
[    9.367965] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[    9.376429] [drm] Initialized drm 1.1.0 20060810
[    9.382402] Bluetooth: Core ver 2.20
[    9.382423] NET: Registered protocol family 31
[    9.382425] Bluetooth: HCI device and connection manager initialized
[    9.382430] Bluetooth: HCI socket layer initialized
[    9.382433] Bluetooth: L2CAP socket layer initialized
[    9.382440] Bluetooth: SCO socket layer initialized
[    9.410853] AVX2 version of gcm_enc/dec engaged.
[    9.410856] AES CTR mode by8 optimization enabled
[    9.413368] usbcore: registered new interface driver btusb
[    9.414071] [drm] Memory usable by graphics device = 4096M
[    9.414077] checking generic (c0000000 7f0000) vs hw (c0000000 10000000)
[    9.414079] fb: switching to inteldrmfb from EFI VGA
[    9.414109] Console: switching to colour dummy device 80x25
[    9.414228] [drm] Replacing VGA console driver
[    9.424383] [drm] Supports vblank timestamp caching Rev 2 (21.10.2013).
[    9.424388] [drm] Driver supports precise vblank timestamp query.
[    9.436563] vgaarb: device changed decodes: PCI:0000:00:02.0,olddecodes=io+mem,decodes=io+mem:owns=io+mem
[    9.500443] fbcon: inteldrmfb (fb0) is primary device
[    9.501656] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
[    9.651571] audit: type=1400 audit(1456861778.025:2): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/sbin/dhclient" pid=508 comm="apparmor_parser"
[    9.651576] audit: type=1400 audit(1456861778.025:3): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=508 comm="apparmor_parser"
[    9.651580] audit: type=1400 audit(1456861778.025:4): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=508 comm="apparmor_parser"
[    9.651591] audit: type=1400 audit(1456861778.025:5): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/sbin/dhclient" pid=507 comm="apparmor_parser"
[    9.651597] audit: type=1400 audit(1456861778.025:6): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=507 comm="apparmor_parser"
[    9.651601] audit: type=1400 audit(1456861778.025:7): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=507 comm="apparmor_parser"
[    9.652039] audit: type=1400 audit(1456861778.025:8): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=508 comm="apparmor_parser"
[    9.652043] audit: type=1400 audit(1456861778.025:9): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=508 comm="apparmor_parser"
[    9.652060] audit: type=1400 audit(1456861778.025:10): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=507 comm="apparmor_parser"
[    9.652063] audit: type=1400 audit(1456861778.025:11): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=507 comm="apparmor_parser"
[    9.652816] media: Linux media interface: v0.10
[    9.657435] Linux video capture interface: v2.00
[    9.666004] uvcvideo: Found UVC 1.00 device BisonCam, NB Pro (5986:066d)
[    9.668568] input: BisonCam, NB Pro as /devices/pci0000:00/0000:00:14.0/usb1/1-2/1-2:1.0/input/input13
[    9.668676] usbcore: registered new interface driver uvcvideo
[    9.668677] USB Video Class driver (1.1.1)
[    9.818552] cfg80211: Calling CRDA to update world regulatory domain
[   10.083672] cfg80211: World regulatory domain updated:
[   10.083674] cfg80211:  DFS Master region: unset
[   10.083674] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp), (dfs_cac_time)
[   10.083676] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm), (N/A)
[   10.083678] cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (300 mBi, 2000 mBm), (N/A)
[   10.083679] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm), (N/A)
[   10.083680] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm), (N/A)
[   10.083681] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm), (N/A)
[   10.244814] usb 1-6: reset high-speed USB device number 4 using xhci_hcd
[   10.438772] xhci_hcd 0000:00:14.0: xHCI xhci_drop_endpoint called with disabled ep ffff88045b390248
[   10.438774] xhci_hcd 0000:00:14.0: xHCI xhci_drop_endpoint called with disabled ep ffff88045b390200
[   10.438775] xhci_hcd 0000:00:14.0: xHCI xhci_drop_endpoint called with disabled ep ffff88045b390290
[   10.438776] xhci_hcd 0000:00:14.0: xHCI xhci_drop_endpoint called with disabled ep ffff88045b3902d8
[   10.438777] xhci_hcd 0000:00:14.0: xHCI xhci_drop_endpoint called with disabled ep ffff88045b390320
[   10.438778] xhci_hcd 0000:00:14.0: xHCI xhci_drop_endpoint called with disabled ep ffff88045b390368
[   10.438779] xhci_hcd 0000:00:14.0: xHCI xhci_drop_endpoint called with disabled ep ffff88045b3903b0
[   10.439106] ieee80211 phy0: rt2x00_set_rt: Info - RT chipset 3070, rev 0201 detected
[   10.449270] ieee80211 phy0: rt2x00_set_rf: Info - RF chipset 0005 detected
[   10.477198] ieee80211 phy0: Selected rate control algorithm 'minstrel_ht'
[   10.477519] usbcore: registered new interface driver rt2800usb
[   10.742900] cfg80211: Calling CRDA for country: US
[   10.746781] EXT4-fs (sda2): re-mounted. Opts: errors=remount-ro
[   10.760833] cfg80211: Regulatory domain changed to country: US
[   10.760834] cfg80211:  DFS Master region: unset
[   10.760834] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp), (dfs_cac_time)
[   10.760837] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm), (N/A)
[   10.760838] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 1700 mBm), (N/A)
[   10.760839] cfg80211:   (5250000 KHz - 5330000 KHz @ 40000 KHz), (300 mBi, 2000 mBm), (0 s)
[   10.760840] cfg80211:   (5490000 KHz - 5600000 KHz @ 40000 KHz), (300 mBi, 2000 mBm), (0 s)
[   10.760841] cfg80211:   (5650000 KHz - 5710000 KHz @ 40000 KHz), (300 mBi, 2000 mBm), (0 s)
[   10.760842] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 3000 mBm), (N/A)
[   10.760843] cfg80211:   (57240000 KHz - 63720000 KHz @ 2160000 KHz), (N/A, 4000 mBm), (N/A)
[   10.780834] [drm] RC6 on
[   11.544637] Console: switching to colour frame buffer device 240x67
[   11.550527] i915_bpo 0000:00:02.0: fb0: inteldrmfb frame buffer device
[   11.550529] i915_bpo 0000:00:02.0: registered panic notifier
[   11.550646] acpi device:0f: registered as cooling_device8
[   11.550775] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/LNXVIDEO:00/input/input14
[   11.550963] [drm] Initialized i915_bpo 1.6.0 20150522 for 0000:00:02.0 on minor 0
[   11.551039] snd_hda_intel 0000:00:1f.3: enabling device (0000 -> 0002)
[   11.551751] snd_hda_intel 0000:00:1f.3: bound 0000:00:02.0 (ops i915_audio_component_bind_ops [i915_bpo])
[   11.574887] sound hdaudioC0D0: autoconfig: line_outs=1 (0x14/0x0/0x0/0x0/0x0) type:speaker
[   11.574891] sound hdaudioC0D0:    speaker_outs=0 (0x0/0x0/0x0/0x0/0x0)
[   11.574894] sound hdaudioC0D0:    hp_outs=1 (0x15/0x0/0x0/0x0/0x0)
[   11.574896] sound hdaudioC0D0:    mono: mono_out=0x0
[   11.574897] sound hdaudioC0D0:    inputs:
[   11.574899] sound hdaudioC0D0:      Mic=0x18
[   11.574901] sound hdaudioC0D0:      Internal Mic=0x12
[   11.579532] init: failsafe main process (690) killed by TERM signal
[   11.584347] input: HDA Intel PCH Mic as /devices/pci0000:00/0000:00:1f.3/sound/card0/input15
[   11.584462] input: HDA Intel PCH Front Headphone as /devices/pci0000:00/0000:00:1f.3/sound/card0/input16
[   11.584582] input: HDA Intel PCH HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:1f.3/sound/card0/input17
[   11.998639] Bluetooth: RFCOMM TTY layer initialized
[   11.998648] Bluetooth: RFCOMM socket layer initialized
[   11.998655] Bluetooth: RFCOMM ver 1.11
[   11.999935] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   11.999939] Bluetooth: BNEP filters: protocol multicast
[   11.999942] Bluetooth: BNEP socket layer initialized
[   12.171854] init: cups main process (865) killed by HUP signal
[   12.171865] init: cups main process ended, respawning
[   12.872367] ieee80211 phy0: rt2x00lib_request_firmware: Info - Loading firmware file 'rt2870.bin'
[   12.897951] ieee80211 phy0: rt2x00lib_request_firmware: Info - Firmware detected - version: 0.29
[   13.163188] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   13.334265] r8169 0000:01:00.1 eth0: link down
[   13.334301] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   14.251138] wlan0: authenticate with 00:1a:1e:9c:0b:20
[   14.286279] wlan0: send auth to 00:1a:1e:9c:0b:20 (try 1/3)
[   14.288662] wlan0: authenticated
[   14.288811] rt2800usb 1-6:1.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[   14.288816] rt2800usb 1-6:1.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[   14.292045] wlan0: associate with 00:1a:1e:9c:0b:20 (try 1/3)
[   14.298981] wlan0: RX AssocResp from 00:1a:1e:9c:0b:20 (capab=0x421 status=0 aid=1)
[   14.301797] wlan0: associated
[   14.301818] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   17.906457] init: anacron main process (1047) killed by TERM signal
[   42.209305] audit_printk_skb: 168 callbacks suppressed
[   42.209308] audit: type=1400 audit(1456861810.589:68): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/cups/backend/cups-pdf" pid=1675 comm="apparmor_parser"
[   42.209317] audit: type=1400 audit(1456861810.589:69): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/sbin/cupsd" pid=1675 comm="apparmor_parser"
[   42.209777] audit: type=1400 audit(1456861810.589:70): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/sbin/cupsd" pid=1675 comm="apparmor_parser"
```

---

### Post by gareth15 on 2016-03-01
Oh woops I didn't see your other response on this thread.

Hm, I try the sudo apt-get but it says unable to locate package....

---

### Post by gareth15 on 2016-03-01
Did apt-get update and updated distro, rebooted. Here's my wireless status info:

```


########## wireless info START ##########


Report from: 01 Mar 2016 15:27 EST -0500


Booted last: 01 Mar 2016 15:21 EST -0500


Script from: 27 Sep 2015 00:34 UTC +0000


##### release ###########################


Distributor ID:	Ubuntu
Description:	Ubuntu 14.04.4 LTS
Release:	14.04
Codename:	trusty


##### kernel ############################


Linux 3.19.0-49-generic #55~14.04.1-Ubuntu SMP Fri Jan 22 11:24:31 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux


Parameters: ro, noprompt, persistent, quiet, splash


##### desktop ###########################


Ubuntu


##### lspci #############################


01:00.1 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 12)
	Subsystem: CLEVO/KAPOK Computer Device [1558:6507]
	Kernel driver in use: r8169


02:00.0 Network controller [0280]: Intel Corporation Wireless 8260 [8086:24f3] (rev 3a)
	Subsystem: Intel Corporation Device [8086:1010]


##### lsusb #############################


Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 006: ID 07d1:3c16 D-Link System DWA-125 Wireless N 150 Adapter(rev.A2) [Ralink RT3070]
Bus 001 Device 004: ID 8087:0a2b Intel Corp. 
Bus 001 Device 003: ID 5986:066d Acer, Inc 
Bus 001 Device 002: ID 045e:0040 Microsoft Corp. Wheel Mouse Optical
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


##### PCMCIA card info ##################


##### rfkill ############################


0: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no
2: phy1: Wireless LAN
	Soft blocked: no
	Hard blocked: no


##### lsmod #############################


rt2800usb              28672  0 
rt2x00usb              24576  1 rt2800usb
rt2800lib              90112  1 rt2800usb
rt2x00lib              57344  3 rt2x00usb,rt2800lib,rt2800usb
mac80211              712704  3 rt2x00lib,rt2x00usb,rt2800lib
cfg80211              524288  2 mac80211,rt2x00lib
crc_ccitt              16384  1 rt2800lib
wmi                    20480  0 


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
          inet addr:192.168.0.118  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::<IP6 'wlan0' [IF]>/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1050 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1070 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:640053 (640.0 KB)  TX bytes:190341 (190.3 KB)


##### iwconfig ##########################


eth0      no wireless extensions.


lo        no wireless extensions.


wlan0     IEEE 802.11bgn  ESSID:"SharfNahonLab"  
          Mode:Managed  Frequency:2.417 GHz  Access Point: <MAC 'SharfNahonLab' [AC1]>   
          Bit Rate=65 Mb/s   Tx-Power=27 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=70/70  Signal level=-39 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:9  Invalid misc:66   Missed beacon:0


##### route #############################


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.0.99    0.0.0.0         UG    0      0        0 wlan0
192.168.0.0     0.0.0.0         255.255.255.0   U     9      0        0 wlan0


##### resolv.conf #######################


nameserver 127.0.1.1


##### network managers ##################


Installed:


	NetworkManager


Running:


root       874     1  0 15:21 ?        00:00:00 NetworkManager


##### NetworkManager info ###############


NetworkManager Tool


State: connected (global)


- Device: wlan0  [SharfNahonLab] -----------------------------------------------
  Type:              802.11 WiFi
  Driver:            rt2800usb
  State:             connected
  Default:           yes
  HW Address:        <MAC 'wlan0' [IF]>


  Capabilities:
    Speed:           43 Mb/s


  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes


  Wireless Access Points (* = current AP)
    eduroam:         Infra, <MAC 'eduroam' [AN1]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 59 WPA2 Enterprise
    mcgill.ca:       Infra, <MAC 'mcgill.ca' [AN2]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 52
    mcgill.ca:       Infra, <MAC 'mcgill.ca' [AN3]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 45
    *SharfNahonLab:  Infra, <MAC 'SharfNahonLab' [AC1]>, Freq 2417 MHz, Rate 54 Mb/s, Strength 77 WPA WPA2
    wpa.mcgill.ca:   Infra, <MAC 'wpa.mcgill.ca' [AC5]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 65 WPA2 Enterprise
    wpa.mcgill.ca:   Infra, <MAC 'wpa.mcgill.ca' [AN6]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 42 WPA2 Enterprise
    eduroam:         Infra, <MAC 'eduroam' [AN7]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 35 WPA2 Enterprise
    samprada:        Infra, <MAC 'samprada' [AC8]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 35 WPA2
    mcgill.ca:       Infra, <MAC 'mcgill.ca' [AC2]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 65
    eduroam:         Infra, <MAC 'eduroam' [AC6]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 55 WPA2 Enterprise
    eduroam:         Infra, <MAC 'eduroam' [AC4]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 52 WPA2 Enterprise
    wpa.mcgill.ca:   Infra, <MAC 'wpa.mcgill.ca' [AC3]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 49 WPA2 Enterprise
    Unel-Service:    Infra, <MAC 'Unel-Service' [AC7]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 35 WEP


  IPv4 Settings:
    Address:         192.168.0.118
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.0.99


    DNS:             192.168.0.99


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


[ifupdown]
managed=false


##### NetworkManager profiles ###########


[[/etc/NetworkManager/system-connections/mcgill.ca]] (600 root)
[connection] id=mcgill.ca | type=802-11-wireless
[802-11-wireless] ssid=mcgill.ca | mac-address=<MAC 'wlan0' [IF]>
[ipv6] method=auto
[ipv4] method=auto


[[/etc/NetworkManager/system-connections/SharfNahonLab]] (600 root)
[connection] id=SharfNahonLab | type=802-11-wireless
[802-11-wireless] ssid=SharfNahonLab | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto


##### iw reg get ########################


Region: America/New_York (based on set time zone)


country US:
	(2402 - 2472 @ 40), (3, 27)
	(5170 - 5250 @ 40), (3, 17)
	(5250 - 5330 @ 40), (3, 20), DFS
	(5490 - 5600 @ 40), (3, 20), DFS
	(5650 - 5710 @ 40), (3, 20), DFS
	(5735 - 5835 @ 40), (3, 30)
	(57240 - 63720 @ 2160), (N/A, 40)


##### iwlist channels ###################


eth0      no frequency information.


lo        no frequency information.


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
          Current Frequency:2.417 GHz (Channel 2)


##### iwlist scan #######################


eth0      Interface doesn't support scanning.


lo        Interface doesn't support scanning.


Channel occupancy:


      5   APs on   Frequency:2.412 GHz (Channel 1)
      1   APs on   Frequency:2.417 GHz (Channel 2)
      1   APs on   Frequency:2.437 GHz (Channel 6)
      1   APs on   Frequency:2.462 GHz (Channel 11)


wlan0     Scan completed :
          Cell 01 - Address: <MAC 'SharfNahonLab' [AC1]>
                    Channel:2
                    Frequency:2.417 GHz (Channel 2)
                    Quality=70/70  Signal level=-39 dBm  
                    Encryption key:on
                    ESSID:"SharfNahonLab"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000ada6183f220
                    Extra: Last beacon: 268ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC 'mcgill.ca' [AC2]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=51/70  Signal level=-59 dBm  
                    Encryption key:off
                    ESSID:"mcgill.ca"
                    Bit Rates:9 Mb/s; 11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000083ab5ca34
                    Extra: Last beacon: 20ms ago
          Cell 03 - Address: <MAC 'wpa.mcgill.ca' [AC3]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=39/70  Signal level=-71 dBm  
                    Encryption key:on
                    ESSID:"wpa.mcgill.ca"
                    Bit Rates:11 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000003b7b27063
                    Extra: Last beacon: 18496ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
          Cell 04 - Address: <MAC 'eduroam' [AC4]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=41/70  Signal level=-69 dBm  
                    Encryption key:on
                    ESSID:"eduroam"
                    Bit Rates:11 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000003b7b2767e
                    Extra: Last beacon: 18496ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
          Cell 05 - Address: <MAC 'wpa.mcgill.ca' [AC5]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=51/70  Signal level=-59 dBm  
                    Encryption key:on
                    ESSID:"wpa.mcgill.ca"
                    Bit Rates:9 Mb/s; 11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000083ab5cc1e
                    Extra: Last beacon: 20ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
          Cell 06 - Address: <MAC 'eduroam' [AC6]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=49/70  Signal level=-61 dBm  
                    Encryption key:on
                    ESSID:"eduroam"
                    Bit Rates:9 Mb/s; 11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000083ab5ce1b
                    Extra: Last beacon: 20ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
          Cell 07 - Address: <MAC 'Unel-Service' [AC7]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=31/70  Signal level=-79 dBm  
                    Encryption key:on
                    ESSID:"Unel-Service"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000976e4b45a7
                    Extra: Last beacon: 20ms ago
          Cell 08 - Address: <MAC 'samprada' [AC8]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=29/70  Signal level=-81 dBm  
                    Encryption key:on
                    ESSID:"samprada"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000001540f908e0
                    Extra: Last beacon: 20ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK


##### module infos ######################


[rt2800usb]
filename:       /lib/modules/3.19.0-49-generic/kernel/drivers/net/wireless/rt2x00/rt2800usb.ko
license:        GPL
firmware:       rt2870.bin
description:    Ralink RT2800 USB Wireless LAN driver.
version:        2.3.0
author:         http://rt2x00.serialmonkey.com
srcversion:     CDB4A56A88AAEC3126F6347
depends:        rt2x00lib,rt2800lib,rt2x00usb
intree:         Y
vermagic:       3.19.0-49-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        A9:32:DC:23:78:95:A4:4D:39:59:BF:91:A3:56:6A:20:EE:21:1F:37
sig_hashalgo:   sha512
parm:           nohwcrypt:Disable hardware encryption. (bool)


[rt2x00usb]
filename:       /lib/modules/3.19.0-49-generic/kernel/drivers/net/wireless/rt2x00/rt2x00usb.ko
license:        GPL
description:    rt2x00 usb library
version:        2.3.0
author:         http://rt2x00.serialmonkey.com
srcversion:     B51D09F4F13F9196B61EBE4
depends:        rt2x00lib,mac80211
intree:         Y
vermagic:       3.19.0-49-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        A9:32:DC:23:78:95:A4:4D:39:59:BF:91:A3:56:6A:20:EE:21:1F:37
sig_hashalgo:   sha512


[rt2800lib]
filename:       /lib/modules/3.19.0-49-generic/kernel/drivers/net/wireless/rt2x00/rt2800lib.ko
license:        GPL
description:    Ralink RT2800 library
version:        2.3.0
author:         http://rt2x00.serialmonkey.com, Bartlomiej Zolnierkiewicz
srcversion:     491D0D9622C1740D95E8041
depends:        rt2x00lib,mac80211,crc-ccitt
intree:         Y
vermagic:       3.19.0-49-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        A9:32:DC:23:78:95:A4:4D:39:59:BF:91:A3:56:6A:20:EE:21:1F:37
sig_hashalgo:   sha512


[rt2x00lib]
filename:       /lib/modules/3.19.0-49-generic/kernel/drivers/net/wireless/rt2x00/rt2x00lib.ko
license:        GPL
description:    rt2x00 library
version:        2.3.0
author:         http://rt2x00.serialmonkey.com
srcversion:     7C3B03973B59C2A2A136B6C
depends:        mac80211,cfg80211
intree:         Y
vermagic:       3.19.0-49-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        A9:32:DC:23:78:95:A4:4D:39:59:BF:91:A3:56:6A:20:EE:21:1F:37
sig_hashalgo:   sha512


[mac80211]
filename:       /lib/modules/3.19.0-49-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     1261743510839D352D1D895
depends:        cfg80211
intree:         Y
vermagic:       3.19.0-49-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        A9:32:DC:23:78:95:A4:4D:39:59:BF:91:A3:56:6A:20:EE:21:1F:37
sig_hashalgo:   sha512
parm:           minstrel_vht_only:Use only VHT rates when VHT is supported by sta. (bool)
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)


[cfg80211]
filename:       /lib/modules/3.19.0-49-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     EF182B558008C23DD85EF03
depends:        
intree:         Y
vermagic:       3.19.0-49-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        A9:32:DC:23:78:95:A4:4D:39:59:BF:91:A3:56:6A:20:EE:21:1F:37
sig_hashalgo:   sha512
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)


##### module parameters #################


[rt2800usb]
nohwcrypt: N


[mac80211]
beacon_loss_count: 7
ieee80211_default_rc_algo: minstrel_ht
max_nullfunc_tries: 2
max_probe_tries: 5
minstrel_vht_only: Y
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
# USB device 0x:0x (rt2800usb)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"


##### dmesg #############################


[   13.324191] ieee80211 phy0: rt2x00lib_request_firmware: Info - Loading firmware file 'rt2870.bin'
[   13.345924] ieee80211 phy0: rt2x00lib_request_firmware: Info - Firmware detected - version: 0.29
[   13.591308] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   13.698246] r8169 0000:01:00.1 eth0: link down
[   13.698290] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   14.779303] wlan0: authenticate with <MAC 'mcgill.ca' [AC2]>
[   14.814623] wlan0: send auth to <MAC 'mcgill.ca' [AC2]> (try 1/3)
[   14.817002] wlan0: authenticated
[   14.817158] rt2800usb 1-6:1.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[   14.817162] rt2800usb 1-6:1.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[   14.820000] wlan0: associate with <MAC 'mcgill.ca' [AC2]> (try 1/3)
[   14.827364] wlan0: RX AssocResp from <MAC 'mcgill.ca' [AC2]> (capab=0x421 status=0 aid=1)
[   14.830462] wlan0: associated
[   14.830488] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  301.059194] ieee80211 phy0: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0xffffffff]
[  301.067333] wlan0: deauthenticating from <MAC 'mcgill.ca' [AC2]> by local choice (Reason: 3=DEAUTH_LEAVING)
[  320.259319] ieee80211 phy1: rt2x00_set_rt: Info - RT chipset 3070, rev 0201 detected
[  320.269492] ieee80211 phy1: rt2x00_set_rf: Info - RF chipset 0005 detected
[  320.280384] ieee80211 phy1: rt2x00lib_request_firmware: Info - Loading firmware file 'rt2870.bin'
[  320.280423] ieee80211 phy1: rt2x00lib_request_firmware: Info - Firmware detected - version: 0.29
[  320.531189] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  321.382127] wlan0: authenticate with <MAC 'SharfNahonLab' [AC1]>
[  321.402934] wlan0: send auth to <MAC 'SharfNahonLab' [AC1]> (try 1/3)
[  321.404383] wlan0: authenticated
[  321.407929] wlan0: associate with <MAC 'SharfNahonLab' [AC1]> (try 1/3)
[  321.411815] wlan0: RX AssocResp from <MAC 'SharfNahonLab' [AC1]> (capab=0x431 status=0 aid=6)
[  321.414589] wlan0: associated
[  321.414611] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready


########## wireless info END ############



```

I didn't do sudo apt-get install linux-lts-wily because it couldn't find the package - do you know why I can't find it?

Thanks so much

---

### Post by ajc0 on 2016-07-31
Hi gareth15,

Sorry to hijack your thread. Did you get your webcam working? ([COLOR=#000000][FONT=&quot]BisonCam, NB Pro (5986:066d)[/FONT][/COLOR]) What make of laptop do you have?

Background: Webcam isn't on the supported UVC devices list and I can't get mine to work. Have already posted on relevant forums. Trying to eliminate other options before hacking on the uvcvideo module myself.

Many thanks

---

