---
title: "Internet Connection Quit. Shows Connected but there is no Access"
date: 2016-08-21
forum: Networking &amp; Wireless
---

### Post by asker3 on 2016-08-21
Hello,

I have upgraded Ubuntu after an absence.

It all worked fine, was going great, until the browser crashed. Now, sudo service network-manager restart shows connected. No internet to the browser, email, or command line downloads. I am getting into dead ends on this. No amount of restarts help.

Thank you for your help.

---

### Post by Bucky Ball on 2016-08-21
Welcome back. Which release of Ubuntu are you using?

---

### Post by asker3 on 2016-08-21
Thank you. It is 14.04.5

---

### Post by &amp;KyT$0P# on 2016-08-21
What is said in right-click Network Manager > Connection information?

Are you starting a firejail sandbox or the like while it's connecting but before it's finished connecting?

---

### Post by Bucky Ball on 2016-08-21
Thread moved to Networking and Wireless.

Better support here. Could you run the wirelessinfo script from the second link in my signature at the bottom of this post and give us the [output here]("http://paste.ubuntu.com/"), please?

In the meantime, perhaps post the output of this between ```
 tags.

[code]sudo lshw -C network 
```

---

### Post by asker3 on 2016-08-21
I cannot find an interface to Network Manager. I type the command and a disconnected/connected notice appears but does not open anything.
No, I run the command and wait until it says connected.

---

### Post by &amp;KyT$0P# on 2016-08-21
Wait, you mean you don't even have a panel icon to NetworkManager?
What flavor of Ubuntu are you using?  (Do you even have a GUI at all or just a terminal?)
Can you please post a screenshot of your entire desktop (with all windows minimized or closed)?

---

### Post by banceu_sergiu_ione on 2016-08-21
try restart it

```
sudo systemctl restart network-manager 
```

---

### Post by asker3 on 2016-08-21
It is Trusty Tahr

I had to jump through hoops to get the screenshot.

---

### Post by &amp;KyT$0P# on 2016-08-21
Since your post is not visible on the thread for whatever reason, link to your attachment: [https://ubuntuforums.org/attachment.php?attachmentid=270790]("https://ubuntuforums.org/attachment.php?attachmentid=270790")

NetworkManager is the up-and-down arrows in the upper right.  Not sure if left-click or right-click in Unity.

---

### Post by ajgreeny on 2016-08-21
Don't worry; we've seen your screenshot.
The network manager icon is the up/down arrows top right in your picture.
Left click on that, not right click, and go to "Connection information" and either show another screenshot of that window, or just carefully copy the information it shows you back here for us to see.

---

### Post by asker3 on 2016-08-21
One more time!

[ATTACH=CONFIG]270792[/ATTACH]

---

### Post by asker3 on 2016-08-21
Here is the output from C Network

```
C Network Output

 *-network               
       description: Ethernet interface
       product: 82566DC-2 Gigabit Network Connection
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       logical name: eth0
       version: 02
       serial: 00:1c:c0:24:28:05
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=2.3.2-k duplex=full firmware=1.3-0 ip=192.168.1.109 latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:45 memory:90380000-9039ffff memory:903a4000-903a4fff ioport:20e0(size=32)
  *-network
       description: Wireless interface
       physical id: 1
       bus info: usb@2:1
       logical name: wlan0
       serial: 00:1d:7e:07:f0:e2
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=rt2500usb driverversion=3.16.0-77-generic firmware=N/A link=no multicast=yes wireless=IEEE 802.11bg

```

---

### Post by jeremy31 on 2016-08-21
Please post the wireless-info.**txt** file as that is the script itself

---

### Post by asker3 on 2016-08-21
Also it turns out that the resolution was wong and I could not see the upper top right icons. They showed up in the screenshot! I have been very bothered about not having that there.

---

### Post by asker3 on 2016-08-21
Well, the last post seems to not have shown up...

Wireless-info.txt output...

```

########## wireless info START ##########

Report from: 21 Aug 2016 11:49 PDT -0700

Booted last: 21 Aug 2016 08:11 PDT -0700

Script from: 08 Jul 2016 02:16 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.5 LTS
Release:    14.04
Codename:    trusty

##### kernel ############################

Linux 3.16.0-77-generic #99~14.04.1-Ubuntu SMP Tue Jun 28 19:17:10 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Ubuntu

##### lspci #############################

00:19.0 Ethernet controller [0200]: Intel Corporation 82566DC-2 Gigabit Network Connection [8086:294c] (rev 02)
    Subsystem: Intel Corporation Device [8086:0001]
    Kernel driver in use: e1000e

##### lsusb #############################

Bus 002 Device 002: ID 13b1:000d Linksys WUSB54G v4 802.11g Adapter [Ralink RT2500USB]
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 004: ID 0ea0:2209 Ours Technology, Inc. 
Bus 001 Device 007: ID 05dc:a81d Lexar Media, Inc. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 093a:2510 Pixart Imaging, Inc. Optical Mouse
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 04d9:1605 Holtek Semiconductor, Inc. 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

##### lsmod #############################

rt2500usb              31447  0 
rt2x00usb              20742  1 rt2500usb
rt2x00lib              55307  2 rt2x00usb,rt2500usb
mac80211              660855  2 rt2x00lib,rt2x00usb
cfg80211              506619  2 mac80211,rt2x00lib

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

eth0      Link encap:Ethernet  HWaddr <MAC 'eth0' [IF1]>  
          inet addr:192.168.1.109  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::<IP6 'eth0' [IF1]>/64 Scope:Link
          inet6 addr: 2602:306:ced4:c490:a578:c0dd:e703:1ced/64 Scope:Global
          inet6 addr: 2602:306:ced4:c490:<IP6 'eth0' [IF1]>/64 Scope:Global
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:18751 errors:0 dropped:2 overruns:0 frame:0
          TX packets:6052 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2010569 (2.0 MB)  TX bytes:604359 (604.3 KB)
          Interrupt:20 Memory:90380000-903a0000 

wlan0     Link encap:Ethernet  HWaddr <MAC 'wlan0' [IF2]>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

##### iwconfig ##########################

eth0      no wireless extensions.

lo        no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.254   0.0.0.0         UG    0      0        0 eth0
192.168.1.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0

##### resolv.conf #######################

search expressvpn
nameserver 10.12.0.1

##### network managers ##################

Installed:

    NetworkManager

Running:

root      3982     1  0 09:39 ?        00:00:01 NetworkManager

##### NetworkManager info ###############

NetworkManager Tool

State: connected (global)

- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            rt2500usb
  State:             disconnected
  Default:           no
  HW Address:        <MAC 'wlan0' [IF2]>

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 
    17753:           Infra, <MAC '17753' [AC2]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 100 WPA WPA2
    HP-Print-D8-Officejet Pro 6830: Infra, <MAC 'HP-Print-D8-Officejet Pro 6830' [AC1]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 77 WPA2
    HOME-6FA2:       Infra, <MAC 'HOME-6FA2' [AN3]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 45 WPA WPA2
    Snow:            Infra, <MAC 'Snow' [AN4]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 37 WPA WPA2
    HOME-66E2:       Infra, <MAC 'HOME-66E2' [AC3]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 30 WPA WPA2
    2WIRE745:        Infra, <MAC '2WIRE745' [AC9]>, Freq 2452 MHz, Rate 54 Mb/s, Strength 39 WPA
    HOME-5C88:       Infra, <MAC 'HOME-5C88' [AC8]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 30 WPA WPA2
    ATT4W9a9b4:      Infra, <MAC 'ATT4W9a9b4' [AC10]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 39 WPA WPA2
    xfinitywifi:     Infra, <MAC 'xfinitywifi' [AN9]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 49
    xfinitywifi:     Infra, <MAC 'xfinitywifi' [AC4]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 32
    xfinitywifi:     Infra, <MAC 'xfinitywifi' [AC5]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 37
    xfinitywifi:     Infra, <MAC 'xfinitywifi' [AN12]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 27
    ATT2raP6D8:      Infra, <MAC 'ATT2raP6D8' [AN13]>, Freq 2442 MHz, Rate 54 Mb/s, Strength 27 WPA2
    ATT3HhA3Rd:      Infra, <MAC 'ATT3HhA3Rd' [AN14]>, Freq 2427 MHz, Rate 54 Mb/s, Strength 27 WPA WPA2
    HOME-4C02:       Infra, <MAC 'HOME-4C02' [AN15]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 30 WPA WPA2
    ATT743:          Infra, <MAC 'ATT743' [AN16]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 25 WPA WPA2
    xfinitywifi:     Infra, <MAC 'xfinitywifi' [AN17]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 30
    ATT127:          Infra, <MAC 'ATT127' [AN18]>, Freq 2427 MHz, Rate 54 Mb/s, Strength 25 WPA WPA2
    HP-Print-AA-Officejet Pro 8620: Infra, <MAC 'HP-Print-AA-Officejet Pro 8620' [AN19]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 44 WPA2

- Device: eth0  [Wired connection 1] -------------------------------------------
  Type:              Wired
  Driver:            e1000e
  State:             connected
  Default:           yes
  HW Address:        <MAC 'eth0' [IF1]>

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.1.109
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.254

    DNS:             192.168.1.254

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

##### iwlist scan #######################

eth0      Interface doesn't support scanning.

lo        Interface doesn't support scanning.

Channel occupancy:

      5   APs on   Frequency:2.412 GHz (Channel 1)
      3   APs on   Frequency:2.437 GHz (Channel 6)
      1   APs on   Frequency:2.452 GHz (Channel 9)
      1   APs on   Frequency:2.462 GHz (Channel 11)

wlan0     Scan completed :
          Cell 01 - Address: <MAC 'HP-Print-D8-Officejet Pro 6830' [AC1]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=64/70  Signal level=-46 dBm  
                    Encryption key:on
                    ESSID:"HP-Print-D8-Officejet Pro 6830"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000046290abc814
                    Extra: Last beacon: 56ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC '17753' [AC2]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=70/70  Signal level=-26 dBm  
                    Encryption key:on
                    ESSID:"17753"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000029792ad73
                    Extra: Last beacon: 56ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: <MAC 'HOME-66E2' [AC3]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=30/70  Signal level=-80 dBm  
                    Encryption key:on
                    ESSID:"HOME-66E2"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000b5221defbe
                    Extra: Last beacon: 56ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
          Cell 04 - Address: <MAC 'xfinitywifi' [AC4]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=31/70  Signal level=-79 dBm  
                    Encryption key:off
                    ESSID:"xfinitywifi"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000b5221e2cce
                    Extra: Last beacon: 56ms ago
          Cell 05 - Address: <MAC 'xfinitywifi' [AC5]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=33/70  Signal level=-77 dBm  
                    Encryption key:off
                    ESSID:"xfinitywifi"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000014537398181
                    Extra: Last beacon: 1120ms ago
          Cell 06 - Address: <MAC '' [AC6]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=40/70  Signal level=-70 dBm  
                    Encryption key:on
                    ESSID:""
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000012738dc2f2
                    Extra: Last beacon: 812ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
          Cell 07 - Address: <MAC '' [AC7]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=40/70  Signal level=-70 dBm  
                    Encryption key:on
                    ESSID:""
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000012738dcb54
                    Extra: Last beacon: 808ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
          Cell 08 - Address: <MAC 'HOME-5C88' [AC8]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=27/70  Signal level=-83 dBm  
                    Encryption key:on
                    ESSID:"HOME-5C88"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000012738e23fb
                    Extra: Last beacon: 56ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
          Cell 09 - Address: <MAC '2WIRE745' [AC9]>
                    Channel:9
                    Frequency:2.452 GHz (Channel 9)
                    Quality=33/70  Signal level=-77 dBm  
                    Encryption key:on
                    ESSID:"2WIRE745"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000d338af27ab9
                    Extra: Last beacon: 56ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 10 - Address: <MAC 'ATT4W9a9b4' [AC10]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=29/70  Signal level=-81 dBm  
                    Encryption key:on
                    ESSID:"ATT4W9a9b4"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000b52e0f52e8
                    Extra: Last beacon: 56ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK

##### module infos ######################

[rt2500usb]
filename:       /lib/modules/3.16.0-77-generic/kernel/drivers/net/wireless/rt2x00/rt2500usb.ko
license:        GPL
description:    Ralink RT2500 USB Wireless LAN driver.
version:        2.3.0
author:         http://rt2x00.serialmonkey.com
srcversion:     42E3E7F229ED13A20C1A619
depends:        rt2x00lib,rt2x00usb
intree:         Y
vermagic:       3.16.0-77-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        4A:94:AF:F5:EF:F7:B5:39:90:6B:3F:2A:9D:0C:CA:00:DA:C4:CB:B0
sig_hashalgo:   sha512
parm:           nohwcrypt:Disable hardware encryption. (bool)

[rt2x00usb]
filename:       /lib/modules/3.16.0-77-generic/kernel/drivers/net/wireless/rt2x00/rt2x00usb.ko
license:        GPL
description:    rt2x00 usb library
version:        2.3.0
author:         http://rt2x00.serialmonkey.com
srcversion:     21417B97E30FD4E6E469E1F
depends:        rt2x00lib,mac80211
intree:         Y
vermagic:       3.16.0-77-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        4A:94:AF:F5:EF:F7:B5:39:90:6B:3F:2A:9D:0C:CA:00:DA:C4:CB:B0
sig_hashalgo:   sha512

[rt2x00lib]
filename:       /lib/modules/3.16.0-77-generic/kernel/drivers/net/wireless/rt2x00/rt2x00lib.ko
license:        GPL
description:    rt2x00 library
version:        2.3.0
author:         http://rt2x00.serialmonkey.com
srcversion:     71EFA3CA86D02D0528C49EE
depends:        mac80211,cfg80211
intree:         Y
vermagic:       3.16.0-77-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        4A:94:AF:F5:EF:F7:B5:39:90:6B:3F:2A:9D:0C:CA:00:DA:C4:CB:B0
sig_hashalgo:   sha512

[mac80211]
filename:       /lib/modules/3.16.0-77-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     563074BC9E04A4D9CE8255D
depends:        cfg80211
intree:         Y
vermagic:       3.16.0-77-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        4A:94:AF:F5:EF:F7:B5:39:90:6B:3F:2A:9D:0C:CA:00:DA:C4:CB:B0
sig_hashalgo:   sha512
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[cfg80211]
filename:       /lib/modules/3.16.0-77-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     824E0EB9924EE6A387D5395
depends:        
intree:         Y
vermagic:       3.16.0-77-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        4A:94:AF:F5:EF:F7:B5:39:90:6B:3F:2A:9D:0C:CA:00:DA:C4:CB:B0
sig_hashalgo:   sha512
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

##### module parameters #################

[rt2500usb]
nohwcrypt: N

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

[/etc/modprobe.d/modesetting.conf]
options cirrus modeset=1
options mgag200 modeset=1

##### rc.local ##########################

exit 0

##### pm-utils ##########################

##### udev rules ########################

[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x8086:0x294c (e1000e)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF1]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# USB device 0x:0x (rt2500usb)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan0' [IF2]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

##### dmesg #############################

[ 1905.896139] e1000e: eth0 NIC Link is Down
[ 1907.644888] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: Rx/Tx
[ 1907.645001] e1000e 0000:00:19.0 eth0: 10/100 speed: disabling TSO
[ 1918.824150] e1000e: eth0 NIC Link is Down
[ 1920.492882] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: Rx/Tx
[ 1920.492995] e1000e 0000:00:19.0 eth0: 10/100 speed: disabling TSO
[ 1991.000111] e1000e: eth0 NIC Link is Down
[ 1991.776244] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[ 1991.973000] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1993.144926] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: Rx/Tx
[ 1993.145038] e1000e 0000:00:19.0 eth0: 10/100 speed: disabling TSO
[ 1993.149036] IPv6: ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[ 2829.184078] e1000e: eth0 NIC Link is Down
[ 2829.956243] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[ 2830.150724] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 2831.348894] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: Rx/Tx
[ 2831.349006] e1000e 0000:00:19.0 eth0: 10/100 speed: disabling TSO
[ 2831.349044] IPv6: ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[ 2894.108145] e1000e: eth0 NIC Link is Down
[ 2894.872242] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[ 2895.064264] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 2896.232895] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: Rx/Tx
[ 2896.233009] e1000e 0000:00:19.0 eth0: 10/100 speed: disabling TSO
[ 2896.233049] IPv6: ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[ 5280.388079] e1000e: eth0 NIC Link is Down
[ 5281.152244] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[ 5281.345143] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 5282.704897] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: Rx/Tx
[ 5282.705008] e1000e 0000:00:19.0 eth0: 10/100 speed: disabling TSO
[ 5282.705046] IPv6: ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready

########## wireless info END ############


```

---

### Post by asker3 on 2016-08-21
"Connection information" screenshot

---

### Post by asker3 on 2016-08-21
I am using a wired connection.

---

### Post by &amp;KyT$0P# on 2016-08-21
Hmm I wonder if it's a DNS issue, are you able to access stuff by IP?  Try pinging your router.  Use this command in Terminal to ping -
```
ping -c 4 <ip_address>
```

If that works, try accessing a site by IP address, for example
```
http://82.103.134.102/
```
(that is the IP address for noscript.net - if it works you should see "Sciò")

---

### Post by asker3 on 2016-08-21
Yes. It shows "Sciò"

---

### Post by &amp;KyT$0P# on 2016-08-21
Yeah, that'd be a DNS issue.  Your /etc/resolv.conf as reported by the script looks odd for someone using NetworkManager.  My /etc/resolv.conf looks like this:
```
# Dynamic resolv.conf(5) file for glibc resolver(3) generated by resolvconf(8)
#     DO NOT EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN
nameserver 127.0.1.1

```

Please post the output of this command
```
ps aux | grep -i dnsmasq
```

---

### Post by asker3 on 2016-08-21
```
nobody    1410  0.0  0.1  35224  3340 ?        S    16:04   0:00  /usr/sbin/dnsmasq --no-resolv --keep-in-foreground --no-hosts  --bind-interfaces  --pid-file=/run/sendsigs.omit.d/network-manager.dnsmasq.pid  --listen-address=127.0.1.1  --conf-file=/var/run/NetworkManager/dnsmasq.conf --cache-size=0  --proxy-dnssec --enable-dbus=org.freedesktop.NetworkManager.dnsmasq  --conf-dir=/etc/NetworkManager/dnsmasq.d
endlyss   3044  0.0  0.1  15948  2404 pts/1    S+   17:27   0:00 grep --color=auto -i dnsmasq
```

---

### Post by &amp;KyT$0P# on 2016-08-21
Ok, so the fix is to change your /etc/resolv.conf to what I posted (some other action e.g. restarting NetworkManager or rebooting maybe required for the change to take effect).
But I think it's maybe not smart to do that without knowing what happened to get your /etc/resolv.conf got the way it is, and I have no idea what to suggest there.

Do you know why your /etc/resolv.conf is non-default?

---

### Post by asker3 on 2016-08-21
I have no idea

---

### Post by asker3 on 2016-08-21
I think it needs to be changed but I am unable to figure out how to get the permission.

---

### Post by asker3 on 2016-08-21
I tried sudo -i and got root

Then nano /etc/resolv.conf  Made the changes but it still won't save and gives the permissions reason.

---

### Post by asker3 on 2016-08-21
I remember now. I was trying to get a vpn running  Then later it acted up. The resolv.conf says it was generated by that program.

---

### Post by &amp;KyT$0P# on 2016-08-22
If you're sure that VPN is uninstalled then you can safely fix permissions and change it back.  Can you please post the output of these commands?
```
ls -la /etc/resolv.conf
```
```
ls -la /run/resolvconf
```

---

### Post by steeldriver on 2016-08-22
You should probably probably dpkg-reconfigure the resolvconf package rather than trying to edit the /etc/resolv.conf file manually

---

### Post by asker3 on 2016-08-22
Here is the output...

```
root@main:~# _**ls -la /etc/resolv.conf**_
-rw-r--r-- 1 root root 65 Aug 20 18:31 /etc/resolv.conf

root@main:~# _**ls -la /run/resolvconf**_
total 4
drwxr-xr-x  3 root root 100 Aug 21 16:19 .
drwxr-xr-x 28 root root 920 Aug 22 16:56 ..
-rw-r--r--  1 root root   0 Aug 21 16:04 enable-updates
drwxr-xr-x  2 root root  60 Aug 21 16:19 interface
-rw-r--r--  1 root root 187 Aug 21 16:19 resolv.conf

```

I also did give dpkg-reconfigure a shot but got stuck on the error: "illegal package name in specifier '/etc/resolv.conf': must start with an alphanumeric character"

---

### Post by steeldriver on 2016-08-22
That would be

```

sudo dpkg-reconfigure resolvconf

```

---

### Post by asker3 on 2016-08-22
There is a big warning regarding the sudo dpkg-reconfigure resolvconf about symbolic links. It sounds like I shouldaccept the option to install a sybolic link from /etc/resolv.conf to /run/resolvconf/resolv.com correct?

---

### Post by steeldriver on 2016-08-22
Yes you should accept that

I will likely then ask you if you want to save your current configuration as /etc/resolvconf/resolv.conf.d/original in case you wish to revert

---

### Post by asker3 on 2016-08-22
I am replying from ubuntu at last. The reconfigure worked.

Thank you all so much! [URL="https://ubuntuforums.org/member.php?u=2034672"][COLOR=#000000]Halogen2, you helped a huge amount and thank you for your patience. You figured it out. I'm sure you've all heard it before.

[/COLOR][/URL]Whew. The cobwebs sure got blown out of the ubuntu room of my brain.

Thanks again.

Yes,I will mark thread as solved.

---

### Post by &amp;KyT$0P# on 2016-08-22
You're welcome, glad it's working for you again!  :KS

---

