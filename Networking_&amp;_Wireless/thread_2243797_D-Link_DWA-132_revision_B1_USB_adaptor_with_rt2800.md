---
title: "D-Link DWA-132 revision B1 USB adaptor with rt2800usb problem"
date: 2014-09-11
forum: Networking &amp; Wireless
---

### Post by Boon_Khang_Hua on 2014-09-11
Good evening to all of you,
[B][COLOR=#ff0000]
[SIZE=4]Problem Description:[/SIZE][/COLOR][/B][SIZE=4]
[/SIZE]
            I bought an wireless adapter recently. It is [COLOR=#ff0000]D-Link DWA-132 revision B1 European Model[/COLOR]. It has [COLOR=#ff0000]Ralink chipset RT5372 chipset[/COLOR]. I am using [COLOR=#ff0000]Ubuntu 14.04 LTS 64 Bit[/COLOR]. I can be detected on my Ubuntu through RT2800USB. However there is a huge problem: the wireless speed is half of the internet speed. For example, suppose the internet speed is 1M bandwith, it only able to download at 512kB/s. I browse a ton of forum and know this problem is caused by Excessive Retry and Invalid Misc as shown as highlighted information below. 

```
wlan0 IEEE 802.11bgn ESSID:"wibon1" 
    Mode:Managed Frequency:2.437 GHz Access Point: 10:FE:ED:C2:F2:06 
    Bit Rate=135 Mb/s Tx-Power=20 dBm 
    Retry short limit:7 RTS thrff Fragment thrff
    Power Managementff
    Link Quality=70/70 Signal level=-39 dBm 
    Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
    **[COLOR=#ff0000]Tx excessive retries:4 Invalid misc:62 Missed beacon:0[/COLOR]**
```

              As you can see, the Tx excessive retries and Invalid misc show up within a few second after i connect to internet. When i use for few minutes, these number will increase exponentially.


[SIZE=4]**[COLOR=#ff0000]Attempted solution:[/COLOR]**
[/SIZE]
I followed the guide from this link: [COLOR=#800000]https://help.ubuntu.com/community/WifiDocs/Device/Tenda_W311M [/COLOR]to solve my problem. However, i cannot compile driver provided by official mediatek: [COLOR=#8b4513]http://www.ralinktech.com/en/04_support/support.php?sn=501[/COLOR]. As a result, i download the driver package called [COLOR=#8b4513]4365112-2011_0719_RT3070_RT3370_RT5370_RT5372_V2.5.0.3_prepared.tar.gz from guide : [/COLOR][COLOR=#ff0000]http://harkko.lattu.biz/notes/rt5370_ubuntu.html[/COLOR]. This driver package can be compiled but do not have my wireless device id. So, i add my usb id 2001:3c22 to the /Besides, i also add a USB device id as shown as information below before i compile the driver provided by the link.

   ```
boon1987@boon1987-System-Product-Name:~$ **[COLOR=#ff0000]lsusb[/COLOR]**
   Bus 002 Device 003: ID 046d:c05a Logitech, Inc. M90/M100 Optical Mouse
   Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
   Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
   Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
   Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
   Bus 001 Device 005: ID 22b8:2e24 Motorola PCS 
**[COLOR=#ff0000]   Bus 001 Device 003: ID 2001:3c22 D-Link Corp. [/COLOR]**
   Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
   Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```

                The file named rtusb_dev_id.c (located in driver_package/common/rtusb_dev_id.c) in the driver package is used to store the ID of USB wireless adapter. So I put 2001:3c22 according to the guide on the website. I also did try to put under section #ifdef RT5372 section but same issue.
    
   ```
#ifdef RT5370
   {USB_DEVICE(0x148F,0x5370)}, /* Ralink 5370 */    
   {USB_DEVICE(0x148F,0x5372)}, /* Ralink 5370 */    
   {USB_DEVICE(0x13D3,0x3365)}, /* Azurewave */
   {USB_DEVICE(0x13D3,0x3329)}, /* Azurewave */
   {USB_DEVICE(0x2001,0x3C15)}, /* Alpha */
   {USB_DEVICE(0x2001,0x3C19)}, /* Alpha */ 
   {USB_DEVICE(0x2001,0x3C1C)}, /* DLink */
   {USB_DEVICE(0x2001,0x3C1D)}, /* DLink */
[COLOR=#ff0000]**   {USB_DEVICE(0x2001,0x3c22)}, /* D-Link DWA-132 revision B1 */**[/COLOR]
   {USB_DEVICE(0x043E,0x7A12)}, /* Arcadyan */
   {USB_DEVICE(0x043E,0x7A22)}, /* LG innotek */
   #endif // RT5370 //
   #ifdef RT5372
   {USB_DEVICE(0x148F,0x5372)}, /* Ralink 5372 */
   {USB_DEVICE(0x13D3,0x3365)}, /* Azurewave */
   #endif /* RT5372 */
```

           After all steps above, i [COLOR=#ff0000]succeed to compile[/COLOR]. And then modprobe the rt5370sta. This driver[COLOR=#ff0000]** can detect my Wireless card**[/COLOR] **[COLOR=#ff0000]but it cause my system crash and show kernel panic in black screen. I have no choice but restart my system using reset swith on my PC case physical button[/COLOR]**.


[SIZE=4]**[COLOR=#ff0000]Question:[/COLOR]**
[/SIZE]
             Since i cannot compile the driver from the official website of mediatek, i just can try to use the driver package provided by other developer as shown in step above. But it does not work. So i hope somebody can guide me to solve this problem or give me some suggestion.


Thank You,

---

### Post by varunendra on 2014-09-11
I suggest you revert all the changes you have made, that is, purge the proprietary driver, its data and conf files, remove the native driver from blacklist to get back to default state.

Then try to connect and let it fail (or connect). Then follow this post to download and run wireless_script (online or offline) and post back the report it generates : [http://ubuntuforums.org/showpost.php?p=13024222](http://ubuntuforums.org/showpost.php?p=13024222)

---

### Post by Boon_Khang_Hua on 2014-09-12
varun,

          I run the cleaning on my system. Here is my result after ran the script and its attachment.
[B][SIZE=3][B]
[/B][/SIZE][/B]

```
########## wireless info START ##########


Report from: 12 Sep 2014 12:54 MYT +0800


Script from: 05 Sep 2014 22:42 UTC +0000


##### release #####


Distributor ID:	Ubuntu
Description:	Ubuntu 14.04.1 LTS
Release:	14.04
Codename:	trusty


##### kernel #####


Linux 3.13.0-35-generic #62-Ubuntu SMP Fri Aug 15 01:58:42 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux


Parameters: ro, quiet, splash, vt.handoff=7


##### desktop #####


Ubuntu


##### lspci #####


03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 06)
	Subsystem: ASUSTeK Computer Inc. P8P67 and other motherboards [1043:8432]
	Kernel driver in use: r8169


##### lsusb #####


Bus 002 Device 003: ID 046d:c05a Logitech, Inc. M90/M100 Optical Mouse
Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 2001:3c22 D-Link Corp. 
Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


##### PCMCIA card info #####


##### rfkill #####


0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no


##### lsmod #####


rt2800usb              27026  0 
rt2x00usb              20742  1 rt2800usb
rt2800lib              88776  1 rt2800usb
rt2x00lib              55307  3 rt2x00usb,rt2800lib,rt2800usb
mac80211              540025  3 rt2x00lib,rt2x00usb,rt2800lib
cfg80211              493923  2 mac80211,rt2x00lib
compat                 13849  3 cfg80211,mac80211,rt2800usb
crc_ccitt              12707  1 rt2800lib


##### interfaces #####


auto lo
iface lo inet loopback


##### ifconfig #####


eth0      Link encap:Ethernet  HWaddr <MAC addr eth0>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


wlan0     Link encap:Ethernet  HWaddr <MAC addr wlan0>  
          inet addr:10.210.87.40  Bcast:10.210.255.255  Mask:255.255.0.0
          inet6 addr: fe80::7262:b8ff:fed1:af04/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:7528 errors:0 dropped:0 overruns:0 frame:0
          TX packets:525 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:697356 (697.3 KB)  TX bytes:67815 (67.8 KB)


##### iwconfig #####


eth0      no wireless extensions.


lo        no wireless extensions.


wlan0     IEEE 802.11bgn  ESSID:"4G WiFi by Yes @ UTM"  
          Mode:Managed  Frequency:2.457 GHz  Access Point: <MAC addr 4G WiFi by Yes @ UTM>   
          Bit Rate=13 Mb/s   Tx-Power=20 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=55/70  Signal level=-55 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:81  Invalid misc:1390   Missed beacon:0


##### route #####


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         10.210.0.5      0.0.0.0         UG    0      0        0 wlan0
10.210.0.0      0.0.0.0         255.255.0.0     U     9      0        0 wlan0


##### resolv.conf #####


nameserver 127.0.1.1
search wifi.yes.my


##### nm-tool #####


NetworkManager Tool


State: connected (global)


- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             unavailable
  Default:           no
  HW Address:        <MAC addr eth0>


  Capabilities:
    Carrier Detect:  yes


  Wired Properties
    Carrier:         off


- Device: wlan0  [4G WiFi by Yes @ UTM 1] --------------------------------------
  Type:              802.11 WiFi
  Driver:            rt2800usb
  State:             connected
  Default:           yes
  HW Address:        <MAC addr wlan0>


  Capabilities:
    Speed:           13 Mb/s


  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes


  Wireless Access Points (* = current AP)
    wibon1:          Infra, <MAC addr wibon1>, Freq 2437 MHz, Rate 54 Mb/s, Strength 100 WPA WPA2
    banana:          Infra, <MAC addr banana>, Freq 2432 MHz, Rate 54 Mb/s, Strength 39 WPA2
    4G WiFi by Yes @ UTM: Infra, <MAC addr 4G WiFi by Yes @ UTM>, Freq 2442 MHz, Rate 54 Mb/s, Strength 59
    4G WiFi by Yes @ UTM: Infra, <MAC addr 4G WiFi by Yes @ UTM>, Freq 2417 MHz, Rate 54 Mb/s, Strength 52
    4G WiFi by Yes @ UTM: Infra, <MAC addr 4G WiFi by Yes @ UTM>, Freq 2412 MHz, Rate 54 Mb/s, Strength 49
    4G WiFi by Yes @ UTM: Infra, <MAC addr 4G WiFi by Yes @ UTM>, Freq 2437 MHz, Rate 54 Mb/s, Strength 49
    4G WiFi by Yes @ UTM: Infra, <MAC addr 4G WiFi by Yes @ UTM>, Freq 2422 MHz, Rate 54 Mb/s, Strength 39
    4G WiFi by Yes @ UTM: Infra, <MAC addr 4G WiFi by Yes @ UTM>, Freq 2422 MHz, Rate 54 Mb/s, Strength 35
    4G WiFi by Yes @ UTM: Infra, <MAC addr 4G WiFi by Yes @ UTM>, Freq 2422 MHz, Rate 54 Mb/s, Strength 32
    4G WiFi by Yes @ UTM: Infra, <MAC addr 4G WiFi by Yes @ UTM>, Freq 2447 MHz, Rate 54 Mb/s, Strength 32
    4G WiFi by Yes @ UTM: Infra, <MAC addr 4G WiFi by Yes @ UTM>, Freq 2437 MHz, Rate 54 Mb/s, Strength 25
    4G WiFi by Yes @ UTM: Infra, <MAC addr 4G WiFi by Yes @ UTM>, Freq 2412 MHz, Rate 54 Mb/s, Strength 22
    *4G WiFi by Yes @ UTM: Infra, <MAC addr 4G WiFi by Yes @ UTM>, Freq 2457 MHz, Rate 54 Mb/s, Strength 75
    4G WiFi by Yes @ UTM: Infra, <MAC addr 4G WiFi by Yes @ UTM>, Freq 2422 MHz, Rate 54 Mb/s, Strength 42
    4G WiFi by Yes @ UTM: Infra, <MAC addr 4G WiFi by Yes @ UTM>, Freq 2432 MHz, Rate 54 Mb/s, Strength 39
    4G WiFi by Yes @ UTM: Infra, <MAC addr 4G WiFi by Yes @ UTM>, Freq 2462 MHz, Rate 54 Mb/s, Strength 39
    4G WiFi by Yes @ UTM: Infra, <MAC addr 4G WiFi by Yes @ UTM>, Freq 2457 MHz, Rate 54 Mb/s, Strength 29
    4G WiFi by Yes @ UTM: Infra, <MAC addr 4G WiFi by Yes @ UTM>, Freq 2422 MHz, Rate 54 Mb/s, Strength 29
    4G WiFi by Yes @ UTM: Infra, <MAC addr 4G WiFi by Yes @ UTM>, Freq 2412 MHz, Rate 54 Mb/s, Strength 32
    4G WiFi by Yes @ UTM: Infra, <MAC addr 4G WiFi by Yes @ UTM>, Freq 2457 MHz, Rate 54 Mb/s, Strength 25
    4G WiFi by Yes @ UTM: Infra, <MAC addr 4G WiFi by Yes @ UTM>, Freq 2437 MHz, Rate 54 Mb/s, Strength 25


  IPv4 Settings:
    Address:         10.210.87.40
    Prefix:          16 (255.255.0.0)
    Gateway:         10.210.0.5


    DNS:             10.210.64.1


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
	(2402 - 2472 @ 40), (3, 20)
	(2457 - 2482 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
	(2474 - 2494 @ 20), (3, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
	(5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
	(5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS


##### iwlist channels #####


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
          Current Frequency:2.457 GHz (Channel 10)


##### iwlist scan #####


Channel occupancy:


     1   WLAPs on   Frequency:2.412 GHz (Channel 1)
     1   WLAPs on   Frequency:2.422 GHz (Channel 3)
     2   WLAPs on   Frequency:2.432 GHz (Channel 5)
     2   WLAPs on   Frequency:2.437 GHz (Channel 6)
     2   WLAPs on   Frequency:2.457 GHz (Channel 10)
     1   WLAPs on   Frequency:2.462 GHz (Channel 11)


eth0      Interface doesn't support scanning.


lo        Interface doesn't support scanning.


wlan0     Scan completed :
          Cell 01 - Address: <MAC addr 4G WiFi by Yes @ UTM>
                    Channel:10
                    Frequency:2.457 GHz (Channel 10)
                    Quality=57/70  Signal level=-53 dBm  
                    Encryption key:off
                    ESSID:"4G WiFi by Yes @ UTM"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000070e020fe
                    Extra: Last beacon: 556ms ago
          Cell 02 - Address: <MAC addr 4G WiFi by Yes @ UTM>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=35/70  Signal level=-75 dBm  
                    Encryption key:off
                    ESSID:"4G WiFi by Yes @ UTM"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000000f60223a9
                    Extra: Last beacon: 4008ms ago
          Cell 03 - Address: <MAC addr 4G WiFi by Yes @ UTM>
                    Channel:10
                    Frequency:2.457 GHz (Channel 10)
                    Quality=33/70  Signal level=-77 dBm  
                    Encryption key:off
                    ESSID:"4G WiFi by Yes @ UTM"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000000d39be181
                    Extra: Last beacon: 960ms ago
          Cell 04 - Address: <MAC addr 4G WiFi by Yes @ UTM>
                    Channel:5
                    Frequency:2.432 GHz (Channel 5)
                    Quality=33/70  Signal level=-77 dBm  
                    Encryption key:off
                    ESSID:"4G WiFi by Yes @ UTM"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000021fa89180
                    Extra: Last beacon: 3072ms ago
          Cell 05 - Address: <MAC addr banana>
                    Channel:5
                    Frequency:2.432 GHz (Channel 5)
                    Quality=35/70  Signal level=-75 dBm  
                    Encryption key:on
                    ESSID:"banana"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000003927369f
                    Extra: Last beacon: 32ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 06 - Address: <MAC addr 4G WiFi by Yes @ UTM>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=39/70  Signal level=-71 dBm  
                    Encryption key:off
                    ESSID:"4G WiFi by Yes @ UTM"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000028ff523d
                    Extra: Last beacon: 2752ms ago
          Cell 07 - Address: <MAC addr wibon1>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=70/70  Signal level=-39 dBm  
                    Encryption key:on
                    ESSID:"wibon1"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000034cee71f1a
                    Extra: Last beacon: 32ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 08 - Address: <MAC addr 4G WiFi by Yes @ UTM>
                    Channel:3
                    Frequency:2.422 GHz (Channel 3)
                    Quality=35/70  Signal level=-75 dBm  
                    Encryption key:off
                    ESSID:"4G WiFi by Yes @ UTM"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000007fa4c81a0
                    Extra: Last beacon: 3672ms ago
          Cell 09 - Address: <MAC address>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=25/70  Signal level=-85 dBm  
                    Encryption key:off
                    ESSID:"4G WiFi by Yes @ UTM"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000388e84482
                    Extra: Last beacon: 1180ms ago


##### module infos #####


[rt2800usb]
filename:       /lib/modules/3.13.0-35-generic/updates/drivers/net/wireless/rt2x00/rt2800usb.ko
version:        backported from Linux (v3.14-0-g455c6fd) using backports v3.14-1-0-g369d49a
license:        GPL
firmware:       rt2870.bin
description:    Ralink RT2800 USB Wireless LAN driver.
version:        2.3.0
author:         http://rt2x00.serialmonkey.com
srcversion:     2F7279339983D5ADCCC73D8
depends:        rt2x00lib,rt2800lib,rt2x00usb,compat
vermagic:       3.13.0-35-generic SMP mod_unload modversions 
parm:           nohwcrypt:Disable hardware encryption. (bool)


[rt2x00usb]
filename:       /lib/modules/3.13.0-35-generic/updates/drivers/net/wireless/rt2x00/rt2x00usb.ko
license:        GPL
description:    rt2x00 usb library
version:        2.3.0
author:         http://rt2x00.serialmonkey.com
srcversion:     ABD89D8A2EFC7332A08E9A2
depends:        rt2x00lib,mac80211
vermagic:       3.13.0-35-generic SMP mod_unload modversions 


[rt2800lib]
filename:       /lib/modules/3.13.0-35-generic/updates/drivers/net/wireless/rt2x00/rt2800lib.ko
license:        GPL
description:    Ralink RT2800 library
version:        2.3.0
author:         http://rt2x00.serialmonkey.com, Bartlomiej Zolnierkiewicz
srcversion:     DB972D2EAD76EDD9E489A9D
depends:        rt2x00lib,mac80211,crc-ccitt
vermagic:       3.13.0-35-generic SMP mod_unload modversions 


[rt2x00lib]
filename:       /lib/modules/3.13.0-35-generic/updates/drivers/net/wireless/rt2x00/rt2x00lib.ko
license:        GPL
description:    rt2x00 library
version:        2.3.0
author:         http://rt2x00.serialmonkey.com
srcversion:     DB35855FD885183C1508D31
depends:        mac80211,cfg80211
vermagic:       3.13.0-35-generic SMP mod_unload modversions 


##### module parameters #####


[rt2800usb]
nohwcrypt: N


##### /etc/modules #####


w83627ehf
coretemp


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


##### rc.local #####


exit 0


##### udev rules #####


[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x10ec:0x8168 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC addr eth0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# USB device 0x:0x (rt2800usb)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC addr wlan0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"


##### dmesg #####


[   13.387789] ieee80211 phy0: rt2x00_set_rt: Info - RT chipset 5392, rev 0223 detected
[   13.416016] ieee80211 phy0: rt2x00_set_rf: Info - RF chipset 5372 detected
[   17.630392] ieee80211 phy0: rt2x00lib_request_firmware: Info - Loading firmware file 'rt2870.bin'
[   17.685363] ieee80211 phy0: rt2x00lib_request_firmware: Info - Firmware detected - version: 0.29
[   17.944096] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready (repeated 2 times)
[   20.152590] wlan0: authenticate with <MAC addr 4G WiFi by Yes @ UTM>
[   20.181360] wlan0: send auth to <MAC addr 4G WiFi by Yes @ UTM> (try 1/3)
[   20.182743] wlan0: authenticated
[   20.185648] wlan0: associate with <MAC addr 4G WiFi by Yes @ UTM> (try 1/3)
[   20.191491] wlan0: RX AssocResp from <MAC addr 4G WiFi by Yes @ UTM> (capab=0x421 status=0 aid=40)
[   20.200227] wlan0: associated
[   20.200237] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready


########## wireless info END ############



```

---

### Post by varunendra on 2014-09-12
The driver is still not really the default one, instead a backported one. The few that I have seen here working nicely were the default ones that come with the kernel.

But anyway, please try the only available parameter for your driver -
```
echo "options rt2800usb nohwcrypt=Y" | sudo tee /etc/modprobe.d/rt2800usb.conf
```
Reboot and reconnect. Does it make the connection any better?

---

### Post by Boon_Khang_Hua on 2014-09-12
Varun,

        I execute the command given by you and reboot. The wifi connection still slow as before. Besides, i also revert back to rt2800usb driver by uninstalled the backported driver. But problem remain.

---

### Post by Boon_Khang_Hua on 2014-09-12
> **varunendra said:**
> The driver is still not really the default one, instead a backported one. The few that I have seen here working nicely were the default ones that come with the kernel.

But anyway, please try the only available parameter for your driver -
```
echo "options rt2800usb nohwcrypt=Y" | sudo tee /etc/modprobe.d/rt2800usb.conf
```
Reboot and reconnect. Does it make the connection any better?

I ran the script again. The result are attached with this reply.

---

### Post by varunendra on 2014-09-12
You are connected to a different AP in the new report? The connection speed looks good in it (81 Mb/s), albeit those 'Invalid misc' are still there.

I had something different in mind regarding the previous report, but in the current one (with the new AP), there are two obvious problems/bottlenecks that should be fixed (or rather 'tweaked') first -

First, please try -
```
sudo iwconfig wlan0 power off
```
..to turn "Power Management" off on the card. Keep checking the output of "iwconfig" after short intervals (or especially if you notice a sudden speed drop) to make sure it remains off. If it turns on automatically, we can force it to stay off.

Next, if you have admin access to the router/AP you seem to be connected to, please change the encryption in it to pure WPA2-PSK with AES (CCMP). It is currently using WPA/WPA2 mixed mode which may confuse the driver sometimes, besides, the combination WPA/AES is not standard at all. Reboot the router after saving the changes.

As an additional measure, please set "IPv6" to "Ignore" in Network Manager. You can turn it permanently off systemwide following this post : [http://ubuntuforums.org/showpost.php?p=12640479](http://ubuntuforums.org/showpost.php?p=12640479)

If the speed is still flaky, please post a fresh report with the above changes applied. Preferably run this version of the script as it provides slightly more info that may be useful sometimes : [http://ubuntuforums.org/showpost.php?p=13024222](http://ubuntuforums.org/showpost.php?p=13024222)

---

### Post by Boon_Khang_Hua on 2014-09-12
> **varunendra said:**
> You are connected to a different AP in the new report? The connection speed looks good in it (81 Mb/s), albeit those 'Invalid misc' are still there.

I had something different in mind regarding the previous report, but in the current one (with the new AP), there are two obvious problems/bottlenecks that should be fixed (or rather 'tweaked') first -

First, please try -
```
sudo iwconfig wlan0 power off
```
..to turn "Power Management" off on the card. Keep checking the output of "iwconfig" after short intervals (or especially if you notice a sudden speed drop) to make sure it remains off. If it turns on automatically, we can force it to stay off.

Next, if you have admin access to the router/AP you seem to be connected to, please change the encryption in it to pure WPA2-PSK with AES (CCMP). It is currently using WPA/WPA2 mixed mode which may confuse the driver sometimes, besides, the combination WPA/AES is not standard at all. Reboot the router after saving the changes.

As an additional measure, please set "IPv6" to "Ignore" in Network Manager. You can turn it permanently off systemwide following this post : [http://ubuntuforums.org/showpost.php?p=12640479](http://ubuntuforums.org/showpost.php?p=12640479)

If the speed is still flaky, please post a fresh report with the above changes applied. Preferably run this version of the script as it provides slightly more info that may be useful sometimes : [http://ubuntuforums.org/showpost.php?p=13024222](http://ubuntuforums.org/showpost.php?p=13024222)


Varun,


       I follow your instruction:
1. Disable IP6
2. reboot.
3. sudo iwconfig wlan0 power off
4. Attached the report by running the script given by the link you posted.
5. The invalid misc and Tx excessive retry are very large in number.


      Problem still persisit. Besides, i don't have access to AP router because i live in college. The AP is provided by them. So i cannot change the encryption method.


Thank You.

---

### Post by varunendra on 2014-09-12
I have started to suspect something wrong on the access-point side, but since you don't have admin access to them, there are only a few things to experiment with.

Do you have access to ANY such router/access-point to which you have, or can get admin access? If there are none, can you at least experiment with some android phone working as a hotspot? Does the slow speed problem occurs with that connection too?

For now, seeing the fluctuating state of your regdomain setting, let's make it permanent first -
```
sudo sed -i 's/^REG.*=$/&MY/' /etc/default/crda
sudo iw reg set MY
```

And since the "nohwcrypt=Y" parameter doesn't seem to be helping, let's reset it by deleting the conf file we created -
```
sudo rm /etc/modprobe.d/rt2800usb.conf
```

Next, I am thinking of experimenting with 40 MHz compatibility of cfg80211 driver, but try this only if the above two changes don't make any difference (even after a reboot) -
```
echo "options cfg80211 cfg80211_disable_40mhz_24ghz=Y" | sudo tee /etc/modprobe.d/cfg80211.conf
```
..followed by a reboot. In many cases, this may completely disable the connectivity. If that happens, revert it by deleting the conf file -
```
sudo rm /etc/modprobe.d/cfg80211.conf
```

---

### Post by Boon_Khang_Hua on 2014-09-13
> **varunendra said:**
> I have started to suspect something wrong on the access-point side, but since you don't have admin access to them, there are only a few things to experiment with.Do you have access to ANY such router/access-point to which you have, or can get admin access? If there are none, can you at least experiment with some android phone working as a hotspot? Does the slow speed problem occurs with that connection too?For now, seeing the fluctuating state of your regdomain setting, let's make it permanent first -```
sudo sed -i 's/^REG.*=$/&MY/' /etc/default/crdasudo iw reg set MY
```And since the "nohwcrypt=Y" parameter doesn't seem to be helping, let's reset it by deleting the conf file we created -```
sudo rm /etc/modprobe.d/rt2800usb.conf
```Next, I am thinking of experimenting with 40 MHz compatibility of cfg80211 driver, but try this only if the above two changes don't make any difference (even after a reboot) -```
echo "options cfg80211 cfg80211_disable_40mhz_24ghz=Y" | sudo tee /etc/modprobe.d/cfg80211.conf
```..followed by a reboot. In many cases, this may completely disable the connectivity. If that happens, revert it by deleting the conf file -```
sudo rm /etc/modprobe.d/cfg80211.conf
```

Varun, 

      I have followed your advice. I did following steps when connected to my college AP:
1. sudo sed -i 's/^REG.*=$/&MY/' /etc/default/crda 
2. sudo iw reg set MY
3. connect to college AP and problem remain
4. reboot, then connect to college AP and problem remain
5. echo "options cfg80211 cfg80211_disable_40mhz_24ghz=Y" | sudo tee /etc/modprobe.d/cfg80211.conf
6. reboot, connect and problem remain.

HOWEVER, after all previous steps, i switched on my android hot spot and connected to it. Then i did with following steps:
1. sudo rm /etc/modprobe.d/cfg80211.conf
2. connect to my android phone wireless hotspot.
3. This wifi adapter able to download with **90-95% of download speed** that achieved by android download speed. (Both test using speedtest.net)
4. BUT with **minor TX excessive tries and invalid misc when connected to android phone hot-spo**t **COMPARED TO** when **connected to college AP**.
5. I [B]attached the report when i connected my wifi adapter to android phone hot-spot and test with speedtest.net .

[/B]My speculation from these tests is that the encryption stuff affect the performance and causing the large Tx excessive retries and Invalid Misc. I also think it should be link to rt2800usb issue.

 Is there a way to fix it? What is your opinion?

I don't have access to the router setting of college.Thank You.

Note: I connected this wifi adapter to college AP under window environment. I am using the driver come together with the DISC. It work fine with good download speed.

ADDING:Another report after apply the changes you posted in previous post when connected to college AP is attached.

---

### Post by Boon_Khang_Hua on 2014-09-14
I found a official driver with version 2.6.1.3 from mediatek website: [http://www.mediatek.com/en/downloads/](http://www.mediatek.com/en/downloads/). It supports RT5372/RT5572. However, i cannot compile it under ubuntu 14.04. Has anyone compiled it before? I attached the official driver with this reply.

I hope someone manage to compile the driver and share it process with us.

---

### Post by praseodym on 2014-09-14
```
sudo apt-get install build-essential linux-headers-$(uname -r)
wget media.cdn.ubuntu-de.org/forum/attachments/27/08/5364732-DPO_RT5572_LinuxSTA_2.6.1.3_20121022_prepared.tar.gz
tar xvf 5364732-DPO_RT5572_LinuxSTA_2.6.1.3_20121022_prepared.tar.gz
cd DPO_RT5572_LinuxSTA_2.6.1.3_20121022_prepared
make
sudo make install
sudo depmod -a
sudo update-initramfs -u 
```
Try this "prepared" one. Changes in source code here:

[http://forum.ubuntuusers.de/topic/fritz-wlan-usb-stick-n-v2-usb-id-057c-8501-chi/9/#post-6697257](http://forum.ubuntuusers.de/topic/fritz-wlan-usb-stick-n-v2-usb-id-057c-8501-chi/9/#post-6697257)

---

### Post by varunendra on 2014-09-14
Thanks for dropping in praseodym! I was thinking of digging out one of your above posts. :)

---

### Post by Boon_Khang_Hua on 2014-09-14
Hi, 

    I installed [COLOR=#000000][FONT=Ubuntu Mono]5364732-DPO_RT5572_LinuxSTA_2.6.1.3_20121022_prepared.tar.gz and blacklist rt2800usb. After i reboot and connect adapter to PC, the new driver able to detect my adapter. However, my PC crashed immediately after i opened my browser. I found the user in the forum posted by praseodym has the same crash issue.[/FONT][/COLOR][URL="http://ubuntuforums.org/member.php?u=1411497"]
[/URL]

---

### Post by Boon_Khang_Hua on 2014-09-14
Here is the driver that i downloaded from [http://forum.ubuntuusers.de/topic/herstellung-der-wlan-verbindung-dauert-sehr-la/#post-4040812](http://forum.ubuntuusers.de/topic/herstellung-der-wlan-verbindung-dauert-sehr-la/#post-4040812).

---

### Post by Boon_Khang_Hua on 2014-09-14
I grabbed some message from /var/log/syslog. This message was registered in syslog before my PC crash. I hope it provides some clues to you guys.

```
Sep 14 21:16:07 boon1987-System-Product-Name kernel: [   20.289267] /home/boon1987/Desktop/Debug/DPO_RT5572_LinuxSTA_2.6.1.3_20121022_prepared/os/linux/../../common/cmm_asic.c:2630 assert KeyIdx < 4failed
Sep 14 21:16:07 boon1987-System-Product-Name kernel: [   20.289889] /home/boon1987/Desktop/Debug/DPO_RT5572_LinuxSTA_2.6.1.3_20121022_prepared/os/linux/../../common/cmm_asic.c:2630 assert KeyIdx < 4failed
Sep 14 21:16:07 boon1987-System-Product-Name NetworkManager[868]: <info> Added default wired connection 'Wired connection 1' for /sys/devices/pci0000:00/0000:00:1c.4/0000:03:00.0/net/eth0
Sep 14 21:16:07 boon1987-System-Product-Name NetworkManager[868]: <warn> /sys/devices/virtual/net/lo: couldn't determine device driver; ignoring...
Sep 14 21:16:07 boon1987-System-Product-Name NetworkManager[868]: <warn> /sys/devices/virtual/net/lo: couldn't determine device driver; ignoring...
Sep 14 21:16:07 boon1987-System-Product-Name NetworkManager[868]: <info> urfkill disappeared from the bus
Sep 14 21:16:07 boon1987-System-Product-Name NetworkManager[868]: <info> wpa_supplicant started
Sep 14 21:16:07 boon1987-System-Product-Name whoopsie[1069]: offline
Sep 14 21:16:07 boon1987-System-Product-Name NetworkManager[868]: <info> (ra0) supports 1 scan SSIDs
Sep 14 21:16:07 boon1987-System-Product-Name NetworkManager[868]: <warn> Trying to remove a non-existant call id.
Sep 14 21:16:07 boon1987-System-Product-Name NetworkManager[868]: <info> (ra0): supplicant interface state: starting -> ready
Sep 14 21:16:07 boon1987-System-Product-Name NetworkManager[868]: <info> (ra0): device state change: unavailable -> disconnected (reason 'supplicant-available') [20 30 42]
Sep 14 21:16:07 boon1987-System-Product-Name wpa_supplicant[1193]: ra0: Reject scan trigger since one is already pending
Sep 14 21:16:07 boon1987-System-Product-Name NetworkManager[868]: <info> (ra0): supplicant interface state: ready -> disconnected
Sep 14 21:16:07 boon1987-System-Product-Name NetworkManager[868]: <info> (ra0) supports 1 scan SSIDs
Sep 14 21:16:07 boon1987-System-Product-Name NetworkManager[868]: <info> ModemManager available in the bus
Sep 14 21:16:07 boon1987-System-Product-Name dbus[694]: [system] Activating service name='org.freedesktop.UPower' (using servicehelper)
Sep 14 21:16:07 boon1987-System-Product-Name dbus[694]: [system] Successfully activated service 'org.freedesktop.UPower'
Sep 14 21:16:08 boon1987-System-Product-Name dbus[694]: [system] Activating service name='org.freedesktop.RealtimeKit1' (using servicehelper)
Sep 14 21:16:08 boon1987-System-Product-Name dbus[694]: [system] Successfully activated service 'org.freedesktop.RealtimeKit1'
Sep 14 21:16:08 boon1987-System-Product-Name rtkit-daemon[1344]: Successfully called chroot.
Sep 14 21:16:08 boon1987-System-Product-Name rtkit-daemon[1344]: Successfully dropped privileges.
Sep 14 21:16:08 boon1987-System-Product-Name rtkit-daemon[1344]: Successfully limited resources.
Sep 14 21:16:08 boon1987-System-Product-Name rtkit-daemon[1344]: Running.
Sep 14 21:16:08 boon1987-System-Product-Name rtkit-daemon[1344]: Watchdog thread running.
Sep 14 21:16:08 boon1987-System-Product-Name rtkit-daemon[1344]: Canary thread running.
Sep 14 21:16:08 boon1987-System-Product-Name rtkit-daemon[1344]: Successfully made thread 1341 of process 1341 (n/a) owned by '112' high priority at nice level -11.
Sep 14 21:16:08 boon1987-System-Product-Name rtkit-daemon[1344]: Supervising 1 threads of 1 processes of 1 users.
Sep 14 21:16:08 boon1987-System-Product-Name anacron[1411]: Anacron 2.3 started on 2014-09-14
Sep 14 21:16:08 boon1987-System-Product-Name anacron[1411]: Normal exit (0 jobs run)
Sep 14 21:16:08 boon1987-System-Product-Name rtkit-daemon[1344]: Successfully made thread 1417 of process 1341 (n/a) owned by '112' RT at priority 5.
Sep 14 21:16:08 boon1987-System-Product-Name rtkit-daemon[1344]: Supervising 2 threads of 1 processes of 1 users.
Sep 14 21:16:08 boon1987-System-Product-Name rtkit-daemon[1344]: Successfully made thread 1542 of process 1341 (n/a) owned by '112' RT at priority 5.
Sep 14 21:16:08 boon1987-System-Product-Name rtkit-daemon[1344]: Supervising 3 threads of 1 processes of 1 users.
Sep 14 21:16:08 boon1987-System-Product-Name rtkit-daemon[1344]: Successfully made thread 1543 of process 1341 (n/a) owned by '112' RT at priority 5.
Sep 14 21:16:08 boon1987-System-Product-Name rtkit-daemon[1344]: Supervising 4 threads of 1 processes of 1 users.
Sep 14 21:16:08 boon1987-System-Product-Name rtkit-daemon[1344]: Successfully made thread 1545 of process 1545 (n/a) owned by '112' high priority at nice level -11.
Sep 14 21:16:08 boon1987-System-Product-Name rtkit-daemon[1344]: Supervising 5 threads of 2 processes of 1 users.
Sep 14 21:16:08 boon1987-System-Product-Name pulseaudio[1545]: [pulseaudio] pid.c: Daemon already running.
Sep 14 21:16:09 boon1987-System-Product-Name kernel: [   22.610456] ===>rt_ioctl_giwscan. 12(12) BSS returned, data->length = 2017
Sep 14 21:16:09 boon1987-System-Product-Name NetworkManager[868]: <info> Auto-activating connection 'wibon1'.
Sep 14 21:16:09 boon1987-System-Product-Name NetworkManager[868]: <info> Activation (ra0) starting connection 'wibon1'
Sep 14 21:16:09 boon1987-System-Product-Name NetworkManager[868]: <info> (ra0): device state change: disconnected -> prepare (reason 'none') [30 40 0]
Sep 14 21:16:09 boon1987-System-Product-Name NetworkManager[868]: <info> NetworkManager state is now CONNECTING
Sep 14 21:16:09 boon1987-System-Product-Name NetworkManager[868]: <info> Activation (ra0) Stage 1 of 5 (Device Prepare) scheduled...
Sep 14 21:16:09 boon1987-System-Product-Name NetworkManager[868]: <info> Activation (ra0) Stage 1 of 5 (Device Prepare) started...
Sep 14 21:16:09 boon1987-System-Product-Name NetworkManager[868]: <info> Activation (ra0) Stage 2 of 5 (Device Configure) scheduled...
Sep 14 21:16:09 boon1987-System-Product-Name NetworkManager[868]: <info> Activation (ra0) Stage 1 of 5 (Device Prepare) complete.
Sep 14 21:16:09 boon1987-System-Product-Name NetworkManager[868]: <info> Activation (ra0) Stage 2 of 5 (Device Configure) starting...
Sep 14 21:16:09 boon1987-System-Product-Name NetworkManager[868]: <info> (ra0): device state change: prepare -> config (reason 'none') [40 50 0]
Sep 14 21:16:09 boon1987-System-Product-Name NetworkManager[868]: <info> Activation (ra0/wireless): connection 'wibon1' has security, and secrets exist.  No new secrets needed.
Sep 14 21:16:09 boon1987-System-Product-Name NetworkManager[868]: <info> Config: added 'ssid' value 'wibon1'
Sep 14 21:16:09 boon1987-System-Product-Name NetworkManager[868]: <info> Config: added 'scan_ssid' value '1'
Sep 14 21:16:09 boon1987-System-Product-Name NetworkManager[868]: <info> Config: added 'key_mgmt' value 'WPA-PSK'
Sep 14 21:16:09 boon1987-System-Product-Name NetworkManager[868]: <info> Config: added 'psk' value '<omitted>'
Sep 14 21:16:09 boon1987-System-Product-Name NetworkManager[868]: <info> Activation (ra0) Stage 2 of 5 (Device Configure) complete.
Sep 14 21:16:09 boon1987-System-Product-Name NetworkManager[868]: <info> Config: set interface ap_scan to 1
Sep 14 21:16:09 boon1987-System-Product-Name NetworkManager[868]: <info> (ra0): supplicant interface state: disconnected -> inactive
Sep 14 21:16:09 boon1987-System-Product-Name wpa_supplicant[1193]: ra0: Trying to associate with 10:fe:ed:c2:f2:06 (SSID='wibon1' freq=2412 MHz)
Sep 14 21:16:09 boon1987-System-Product-Name wpa_supplicant[1193]: ra0: Association request to the driver failed
Sep 14 21:16:09 boon1987-System-Product-Name kernel: [   22.621251] ==>rt_ioctl_siwfreq::SIOCSIWFREQ(Channel=1)
Sep 14 21:16:09 boon1987-System-Product-Name NetworkManager[868]: <info> (ra0): supplicant interface state: inactive -> associating
Sep 14 21:16:09 boon1987-System-Product-Name wpa_supplicant[1193]: ra0: Associated with 10:fe:ed:c2:f2:06
Sep 14 21:16:09 boon1987-System-Product-Name NetworkManager[868]: <info> (ra0): supplicant interface state: associating -> associated
Sep 14 21:16:10 boon1987-System-Product-Name NetworkManager[868]: <info> (ra0): supplicant interface state: associated -> 4-way handshake
Sep 14 21:16:10 boon1987-System-Product-Name wpa_supplicant[1193]: ra0: WPA: Key negotiation completed with 10:fe:ed:c2:f2:06 [PTK=CCMP GTK=CCMP]
Sep 14 21:16:10 boon1987-System-Product-Name wpa_supplicant[1193]: ra0: CTRL-EVENT-CONNECTED - Connection to 10:fe:ed:c2:f2:06 completed [id=0 id_str=]
Sep 14 21:16:10 boon1987-System-Product-Name NetworkManager[868]: <info> (ra0): supplicant interface state: 4-way handshake -> completed
Sep 14 21:16:10 boon1987-System-Product-Name NetworkManager[868]: <info> Activation (ra0/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to wireless network 'wibon1'.
Sep 14 21:16:10 boon1987-System-Product-Name NetworkManager[868]: <info> Activation (ra0) Stage 3 of 5 (IP Configure Start) scheduled.
Sep 14 21:16:10 boon1987-System-Product-Name NetworkManager[868]: <info> Activation (ra0) Stage 3 of 5 (IP Configure Start) started...
Sep 14 21:16:10 boon1987-System-Product-Name NetworkManager[868]: <info> (ra0): device state change: config -> ip-config (reason 'none') [50 70 0]
Sep 14 21:16:10 boon1987-System-Product-Name NetworkManager[868]: <info> Activation (ra0) Beginning DHCPv4 transaction (timeout in 45 seconds)
Sep 14 21:16:10 boon1987-System-Product-Name NetworkManager[868]: <info> dhclient started with pid 1588
Sep 14 21:16:10 boon1987-System-Product-Name NetworkManager[868]: <info> Activation (ra0) Stage 3 of 5 (IP Configure Start) complete.
Sep 14 21:16:10 boon1987-System-Product-Name dhclient: Internet Systems Consortium DHCP Client 4.2.4
Sep 14 21:16:10 boon1987-System-Product-Name dhclient: Copyright 2004-2012 Internet Systems Consortium.
Sep 14 21:16:10 boon1987-System-Product-Name dhclient: All rights reserved.
Sep 14 21:16:10 boon1987-System-Product-Name dhclient: For info, please visit https://www.isc.org/software/dhcp/
Sep 14 21:16:10 boon1987-System-Product-Name dhclient: 
Sep 14 21:16:10 boon1987-System-Product-Name NetworkManager[868]: <info> (ra0): DHCPv4 state changed nbi -> preinit
Sep 14 21:16:10 boon1987-System-Product-Name dhclient: Listening on LPF/ra0/70:62:b8:d1:af:04
Sep 14 21:16:10 boon1987-System-Product-Name dhclient: Sending on   LPF/ra0/70:62:b8:d1:af:04
Sep 14 21:16:10 boon1987-System-Product-Name dhclient: Sending on   Socket/fallback
Sep 14 21:16:10 boon1987-System-Product-Name dhclient: DHCPREQUEST of 192.168.0.100 on ra0 to 255.255.255.255 port 67 (xid=0x5b242dd3)
Sep 14 21:16:10 boon1987-System-Product-Name kernel: [   23.780482] RTMP_TimerListAdd: add timer obj ffffc90004d12ce0!
Sep 14 21:16:10 boon1987-System-Product-Name dhclient: DHCPACK of 192.168.0.100 from 192.168.0.254
Sep 14 21:16:10 boon1987-System-Product-Name kernel: [   23.786121] Rcv Wcid(1) AddBAReq
Sep 14 21:16:10 boon1987-System-Product-Name kernel: [   23.786125] Start Seq = 00000000
Sep 14 21:16:10 boon1987-System-Product-Name kernel: [   23.786128] RTMP_TimerListAdd: add timer obj ffffc90004d17500!
Sep 14 21:16:10 boon1987-System-Product-Name dhclient: bound to 192.168.0.100 -- renewal in 3507 seconds.
Sep 14 21:16:10 boon1987-System-Product-Name NetworkManager[868]: <info> (ra0): DHCPv4 state changed preinit -> reboot
Sep 14 21:16:10 boon1987-System-Product-Name NetworkManager[868]: <info>   address 192.168.0.100
Sep 14 21:16:10 boon1987-System-Product-Name NetworkManager[868]: <info>   prefix 24 (255.255.255.0)
Sep 14 21:16:10 boon1987-System-Product-Name NetworkManager[868]: <info>   gateway 192.168.0.254
Sep 14 21:16:10 boon1987-System-Product-Name NetworkManager[868]: <info>   nameserver '192.168.0.254'
Sep 14 21:16:10 boon1987-System-Product-Name NetworkManager[868]: <info> Activation (ra0) Stage 5 of 5 (IPv4 Configure Commit) scheduled...
Sep 14 21:16:10 boon1987-System-Product-Name NetworkManager[868]: <info> Activation (ra0) Stage 5 of 5 (IPv4 Commit) started...
Sep 14 21:16:10 boon1987-System-Product-Name avahi-daemon[765]: Joining mDNS multicast group on interface ra0.IPv4 with address 192.168.0.100.
Sep 14 21:16:10 boon1987-System-Product-Name avahi-daemon[765]: New relevant interface ra0.IPv4 for mDNS.
Sep 14 21:16:10 boon1987-System-Product-Name avahi-daemon[765]: Registering new address record for 192.168.0.100 on ra0.IPv4.
Sep 14 21:16:10 boon1987-System-Product-Name kernel: [   23.796267] RTMP_TimerListAdd: add timer obj ffffc90004d12d70!
Sep 14 21:16:11 boon1987-System-Product-Name NetworkManager[868]: <info> (ra0): device state change: ip-config -> secondaries (reason 'none') [70 90 0]
Sep 14 21:16:11 boon1987-System-Product-Name NetworkManager[868]: <info> Activation (ra0) Stage 5 of 5 (IPv4 Commit) complete.
Sep 14 21:16:11 boon1987-System-Product-Name NetworkManager[868]: <info> (ra0): device state change: secondaries -> activated (reason 'none') [90 100 0]
Sep 14 21:16:11 boon1987-System-Product-Name NetworkManager[868]: <info> NetworkManager state is now CONNECTED_GLOBAL
Sep 14 21:16:11 boon1987-System-Product-Name NetworkManager[868]: <info> Policy set 'wibon1' (ra0) as default for IPv4 routing and DNS.
Sep 14 21:16:11 boon1987-System-Product-Name NetworkManager[868]: <info> DNS: starting dnsmasq...
Sep 14 21:16:11 boon1987-System-Product-Name NetworkManager[868]: <warn> dnsmasq not available on the bus, can't update servers.
Sep 14 21:16:11 boon1987-System-Product-Name NetworkManager[868]: <error> [1410700571.539444] [nm-dns-dnsmasq.c:396] update(): dnsmasq owner not found on bus: Could not get owner of name 'org.freedesktop.NetworkManager.dnsmasq': no such name
Sep 14 21:16:11 boon1987-System-Product-Name NetworkManager[868]: <warn> DNS: plugin dnsmasq update failed
Sep 14 21:16:11 boon1987-System-Product-Name NetworkManager[868]: <info> Writing DNS information to /sbin/resolvconf
Sep 14 21:16:11 boon1987-System-Product-Name dnsmasq[1600]: started, version 2.68 cache disabled
Sep 14 21:16:11 boon1987-System-Product-Name dnsmasq[1600]: compile time options: IPv6 GNU-getopt DBus i18n IDN DHCP DHCPv6 no-Lua TFTP conntrack ipset auth
Sep 14 21:16:11 boon1987-System-Product-Name dnsmasq[1600]: DBus support enabled: connected to system bus
Sep 14 21:16:11 boon1987-System-Product-Name dnsmasq[1600]: warning: no upstream servers configured
Sep 14 21:16:13 boon1987-System-Product-Name dbus[694]: [system] Activating service name='org.freedesktop.systemd1' (using servicehelper)
Sep 14 21:16:13 boon1987-System-Product-Name dbus[694]: [system] Successfully activated service 'org.freedesktop.systemd1'
Sep 14 21:16:13 boon1987-System-Product-Name NetworkManager[868]: <info> Activation (ra0) successful, device activated.
Sep 14 21:16:13 boon1987-System-Product-Name dbus[694]: [system] Activating service name='org.freedesktop.nm_dispatcher' (using servicehelper)
Sep 14 21:16:13 boon1987-System-Product-Name NetworkManager[868]: <warn> dnsmasq appeared on DBus: :1.44
Sep 14 21:16:13 boon1987-System-Product-Name NetworkManager[868]: <info> Writing DNS information to /sbin/resolvconf
Sep 14 21:16:13 boon1987-System-Product-Name dnsmasq[1600]: setting upstream servers from DBus
Sep 14 21:16:13 boon1987-System-Product-Name dnsmasq[1600]: using nameserver 192.168.0.254#53
Sep 14 21:16:13 boon1987-System-Product-Name dbus[694]: [system] Successfully activated service 'org.freedesktop.nm_dispatcher'
Sep 14 21:16:13 boon1987-System-Product-Name NetworkManager[868]: <warn> error requesting auth for org.freedesktop.NetworkManager.wifi.share.protected: (3) GDBus.Error:org.freedesktop.DBus.Error.NameHasNoOwner: GDBus.Error:org.freedesktop.DBus.Error.NameHasNoOwner: Could not get UID of name ':1.27': no such name
Sep 14 21:16:13 boon1987-System-Product-Name NetworkManager[868]: <warn> error requesting auth for org.freedesktop.NetworkManager.wifi.share.open: (3) GDBus.Error:org.freedesktop.DBus.Error.NameHasNoOwner: GDBus.Error:org.freedesktop.DBus.Error.NameHasNoOwner: Could not get UID of name ':1.27': no such name
Sep 14 21:16:13 boon1987-System-Product-Name NetworkManager[868]: <warn> error requesting auth for org.freedesktop.NetworkManager.wifi.share.protected: (3) GDBus.Error:org.freedesktop.DBus.Error.NameHasNoOwner: GDBus.Error:org.freedesktop.DBus.Error.NameHasNoOwner: Could not get UID of name ':1.27': no such name
Sep 14 21:16:13 boon1987-System-Product-Name NetworkManager[868]: <warn> error requesting auth for org.freedesktop.NetworkManager.wifi.share.open: (3) GDBus.Error:org.freedesktop.DBus.Error.NameHasNoOwner: GDBus.Error:org.freedesktop.DBus.Error.NameHasNoOwner: Could not get UID of name ':1.27': no such name
Sep 14 21:16:13 boon1987-System-Product-Name NetworkManager[868]: <warn> error requesting auth for org.freedesktop.NetworkManager.wifi.share.protected: (3) GDBus.Error:org.freedesktop.DBus.Error.NameHasNoOwner: GDBus.Error:org.freedesktop.DBus.Error.NameHasNoOwner: Could not get UID of name ':1.27': no such name
Sep 14 21:16:13 boon1987-System-Product-Name NetworkManager[868]: <warn> error requesting auth for org.freedesktop.NetworkManager.wifi.share.open: (3) GDBus.Error:org.freedesktop.DBus.Error.NameHasNoOwner: GDBus.Error:org.freedesktop.DBus.Error.NameHasNoOwner: Could not get UID of name ':1.27': no such name
Sep 14 21:16:13 boon1987-System-Product-Name NetworkManager[868]: <warn> error requesting auth for org.freedesktop.NetworkManager.wifi.share.protected: (3) GDBus.Error:org.freedesktop.DBus.Error.NameHasNoOwner: GDBus.Error:org.freedesktop.DBus.Error.NameHasNoOwner: Could not get UID of name ':1.27': no such name
Sep 14 21:16:13 boon1987-System-Product-Name NetworkManager[868]: <warn> error requesting auth for org.freedesktop.NetworkManager.wifi.share.open: (3) GDBus.Error:org.freedesktop.DBus.Error.NameHasNoOwner: GDBus.Error:org.freedesktop.DBus.Error.NameHasNoOwner: Could not get UID of name ':1.27': no such name
Sep 14 21:16:13 boon1987-System-Product-Name NetworkManager[868]: <warn> error requesting auth for org.freedesktop.NetworkManager.wifi.share.protected: (3) GDBus.Error:org.freedesktop.DBus.Error.NameHasNoOwner: GDBus.Error:org.freedesktop.DBus.Error.NameHasNoOwner: Could not get UID of name ':1.27': no such name
Sep 14 21:16:13 boon1987-System-Product-Name NetworkManager[868]: <warn> error requesting auth for org.freedesktop.NetworkManager.wifi.share.open: (3) GDBus.Error:org.freedesktop.DBus.Error.NameHasNoOwner: GDBus.Error:org.freedesktop.DBus.Error.NameHasNoOwner: Could not get UID of name ':1.27': no such name
Sep 14 21:16:13 boon1987-System-Product-Name NetworkManager[868]: <warn> error requesting auth for org.freedesktop.NetworkManager.wifi.share.protected: (3) GDBus.Error:org.freedesktop.DBus.Error.NameHasNoOwner: GDBus.Error:org.freedesktop.DBus.Error.NameHasNoOwner: Could not get UID of name ':1.27': no such name
Sep 14 21:16:13 boon1987-System-Product-Name NetworkManager[868]: <warn> error requesting auth for org.freedesktop.NetworkManager.wifi.share.open: (3) GDBus.Error:org.freedesktop.DBus.Error.NameHasNoOwner: GDBus.Error:org.freedesktop.DBus.Error.NameHasNoOwner: Could not get UID of name ':1.27': no such name
Sep 14 21:16:14 boon1987-System-Product-Name rtkit-daemon[1344]: Successfully made thread 2009 of process 2009 (n/a) owned by '1000' high priority at nice level -11.
Sep 14 21:16:14 boon1987-System-Product-Name rtkit-daemon[1344]: Supervising 5 threads of 2 processes of 2 users.
Sep 14 21:16:14 boon1987-System-Product-Name rtkit-daemon[1344]: Successfully made thread 2010 of process 2009 (n/a) owned by '1000' RT at priority 5.
Sep 14 21:16:14 boon1987-System-Product-Name rtkit-daemon[1344]: Supervising 6 threads of 2 processes of 2 users.
Sep 14 21:16:14 boon1987-System-Product-Name rtkit-daemon[1344]: Successfully made thread 2013 of process 2009 (n/a) owned by '1000' RT at priority 5.
Sep 14 21:16:14 boon1987-System-Product-Name rtkit-daemon[1344]: Supervising 7 threads of 2 processes of 2 users.
Sep 14 21:16:14 boon1987-System-Product-Name rtkit-daemon[1344]: Successfully made thread 2014 of process 2009 (n/a) owned by '1000' RT at priority 5.
Sep 14 21:16:14 boon1987-System-Product-Name rtkit-daemon[1344]: Supervising 8 threads of 2 processes of 2 users.
Sep 14 21:16:14 boon1987-System-Product-Name dbus[694]: [system] Activating service name='org.freedesktop.ColorManager' (using servicehelper)
Sep 14 21:16:14 boon1987-System-Product-Name dbus[694]: [system] Activating service name='org.freedesktop.locale1' (using servicehelper)
Sep 14 21:16:14 boon1987-System-Product-Name dbus[694]: [system] Successfully activated service 'org.freedesktop.locale1'
Sep 14 21:16:13 boon1987-System-Product-Name whoopsie[1069]: message repeated 2 times: [ offline]
Sep 14 21:16:14 boon1987-System-Product-Name whoopsie[1069]: online
Sep 14 21:16:14 boon1987-System-Product-Name colord: Using config file /etc/colord.conf
Sep 14 21:16:14 boon1987-System-Product-Name colord: Using mapping database file /var/lib/colord/mapping.db
Sep 14 21:16:14 boon1987-System-Product-Name colord: Using device database file /var/lib/colord/storage.db
Sep 14 21:16:14 boon1987-System-Product-Name colord: loaded plugin libcd_plugin_camera.so
Sep 14 21:16:14 boon1987-System-Product-Name colord: plugin /usr/lib/x86_64-linux-gnu/colord-plugins/libcd_plugin_sane.so not loaded: plugin refused to load
Sep 14 21:16:14 boon1987-System-Product-Name colord: loaded plugin libcd_plugin_scanner.so
Sep 14 21:16:14 boon1987-System-Product-Name colord: Daemon ready for requests
Sep 14 21:16:14 boon1987-System-Product-Name dbus[694]: [system] Successfully activated service 'org.freedesktop.ColorManager'
Sep 14 21:16:14 boon1987-System-Product-Name colord: Profile added: icc-0383c34650771ce95ef93fe916867725
Sep 14 21:16:14 boon1987-System-Product-Name colord: Profile added: icc-d4a7a2bd8ddaacf10e275e3db31d72b8
Sep 14 21:16:14 boon1987-System-Product-Name colord: Profile added: icc-72f5b1cba915b68ea75cc843e270df5a
Sep 14 21:16:14 boon1987-System-Product-Name colord: Profile added: icc-654b99c87e67edb1c1cfb0dcb7fa9d04
Sep 14 21:16:14 boon1987-System-Product-Name colord: Profile added: icc-6a245ab2d8892e2e56232af93cd48b81
Sep 14 21:16:14 boon1987-System-Product-Name colord: Profile added: icc-ea421e3a65cfa796e2732ce36086e327
Sep 14 21:16:14 boon1987-System-Product-Name colord: Profile added: icc-c3e6382fa9b2d31b01b736f6f97aac3a
Sep 14 21:16:14 boon1987-System-Product-Name colord: Profile added: icc-3a34aa6c3d1fb1ef63ff41e04ee00979
Sep 14 21:16:14 boon1987-System-Product-Name colord: Profile added: icc-2f1f11ecd613fe5551420fcaf5b11ff8
Sep 14 21:16:14 boon1987-System-Product-Name colord: Profile added: icc-df7c0067b1eb9bcc9fc9b33bc3a797eb
Sep 14 21:16:14 boon1987-System-Product-Name colord: Profile added: icc-f64a1f19ce07290b35a752b00217b684
Sep 14 21:16:14 boon1987-System-Product-Name colord: Profile added: icc-b0701c2ccf059287d0b067464df8bda9
Sep 14 21:16:14 boon1987-System-Product-Name colord: Profile added: icc-a1d13bd5309e0f06ceda6f0d75367823
Sep 14 21:16:14 boon1987-System-Product-Name colord: Profile added: icc-523e494bc2f53c53d51d0758b07f4879
Sep 14 21:16:14 boon1987-System-Product-Name colord: Profile added: icc-0720e7cdbc792b77c0740c39f325ef9e
Sep 14 21:16:14 boon1987-System-Product-Name colord: Profile added: icc-526fbc9bdf0d7156c553998d47a3b5fc
Sep 14 21:16:14 boon1987-System-Product-Name colord: Profile added: icc-57f0d896250f6f98f77ca1b0d19019c0
Sep 14 21:16:14 boon1987-System-Product-Name colord: Profile added: icc-3bd2261b1125a0fd9ebf827a2d1bed84
Sep 14 21:16:14 boon1987-System-Product-Name colord: Profile added: icc-c227f46f246694ba9971f270cb61a0c1
Sep 14 21:16:14 boon1987-System-Product-Name colord: Profile added: icc-353a6bcabda00f04b6988f89126ce6f5
Sep 14 21:16:14 boon1987-System-Product-Name colord: Profile added: icc-fb0ac62618f016ed9b92ce239258efa8
Sep 14 21:16:14 boon1987-System-Product-Name colord: Profile added: icc-a10be98be58460669fcdc6946939b7cf
Sep 14 21:16:14 boon1987-System-Product-Name colord: Profile added: icc-d6490883a866e4059370e1de1d840283
Sep 14 21:16:14 boon1987-System-Product-Name colord: Profile added: icc-6ad6d63767ce0393245528ada92f1cb2
Sep 14 21:16:14 boon1987-System-Product-Name colord: Device added: sysfs-motorola-XT1033
Sep 14 21:16:14 boon1987-System-Product-Name colord: Device added: sysfs-(null)
Sep 14 21:16:14 boon1987-System-Product-Name colord: Device added: xrandr-Philips Consumer Electronics Company-Philips 192E-DL5104149310
Sep 14 21:16:14 boon1987-System-Product-Name colord: Automatic metadata add icc-80dcf8969842cfa9115f833bcd563e89 to xrandr-Philips Consumer Electronics Company-Philips 192E-DL5104149310
Sep 14 21:16:14 boon1987-System-Product-Name colord: Profile added: icc-80dcf8969842cfa9115f833bcd563e89
Sep 14 21:16:14 boon1987-System-Product-Name NetworkManager[868]: <info> WiFi hardware radio set enabled
Sep 14 21:16:15 boon1987-System-Product-Name dbus[694]: [system] Activating service name='org.freedesktop.UDisks2' (using servicehelper)
Sep 14 21:16:15 boon1987-System-Product-Name udisksd[2229]: udisks daemon version 2.1.3 starting
Sep 14 21:16:16 boon1987-System-Product-Name dbus[694]: [system] Successfully activated service 'org.freedesktop.UDisks2'
Sep 14 21:16:16 boon1987-System-Product-Name udisksd[2229]: Acquired the name org.freedesktop.UDisks2 on the system message bus
Sep 14 21:16:27 boon1987-System-Product-Name ntpdate[1950]: no server suitable for synchronization found
Sep 14 21:16:32 boon1987-System-Product-Name kernel: [   46.043895] ===>rt_ioctl_giwscan. 14(14) BSS returned, data->length = 2329
Sep 14 21:16:33 boon1987-System-Product-Name kernel: [   46.643223] audit_printk_skb: 132 callbacks suppressed
Sep 14 21:16:33 boon1987-System-Product-Name kernel: [   46.643226] type=1400 audit(1410700593.371:68): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/cups/backend/cups-pdf" pid=2551 comm="apparmor_parser"
Sep 14 21:16:33 boon1987-System-Product-Name kernel: [   46.643231] type=1400 audit(1410700593.371:69): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/sbin/cupsd" pid=2551 comm="apparmor_parser"
Sep 14 21:16:33 boon1987-System-Product-Name kernel: [   46.643539] type=1400 audit(1410700593.371:70): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/sbin/cupsd" pid=2551 comm="apparmor_parser"
Sep 14 21:16:45 boon1987-System-Product-Name gnome-session[1828]: GLib-CRITICAL: g_environ_setenv: assertion 'value != NULL' failed

```

---

### Post by praseodym on 2014-09-14
Obviously, it doesn't work properly, uninstall it
```

sudo make uninstall
```
and try mainline kernel 3.16:
[http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.16-utopic/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.16-utopic/)

---

### Post by Boon_Khang_Hua on 2014-09-14
I am using Ubuntu 14.04 LTS. I can use the mainline kernel?

---

### Post by varunendra on 2014-09-14
@praseodym,

Don't you think it would be easier and safer to just install the driver [backported]("http://drvbp1.linux-foundation.org/~mcgrof/rel-html/backports/") from 3.16? It had a compiling problem for kernel 3.13.0-35, but I think chili555 reported it to have been fixed in the later versions.

---

### Post by Boon_Khang_Hua on 2014-09-14
varun and praseodym,

I think i had tried backported 3.16 driver. But the problem remains.

---

### Post by varunendra on 2014-09-14
I didn't see any reference to it. The only trace of you having tried a backported version in this thread was in post #3, and that was from kernel 3.14 -
```
filename:       /lib/modules/3.13.0-35-generic/updates/drivers/net/wireless/rt2x00/rt2800usb.ko
version:        backported from Linux (v**3.14**-0-g455c6fd) using **backports v3.14**-1-0-g369d49a
```

---

### Post by Boon_Khang_Hua on 2014-09-14
Actually i did try 3.14, 3.15, 3.16 and 3.17rc3. I found out 3.14 most stable so i sticked with it. But now i uninstalled it too for debug purpose.

---

### Post by varunendra on 2014-09-14
Then I think I'm out of ideas. Can you show us a speedtest.net result of your download and upload results with the native rt2800usb driver?

Tx excessive retries and 'Invalid misc' are usual, only their excess is not. It would be interesting to see your practical speeds.

---

### Post by praseodym on 2014-09-14
Ok, so try the kernel. You may need to reinstall any proprietary VGA driver afterwards, though.

---

### Post by Boon_Khang_Hua on 2014-09-14
Alright, i will upload the speedtest  afterward. Practically, the download speed is half of full download speed. For example, if both android phone and this wifi adapter connected to same wifil. My pc connected to android able to download at 0.96Mbps while connected to wifi adapter only able to download at 0.5-0.56 Mbps or lower.

Besides, is there a good guide for updating the kernel from 3.13.35 to 3.16? My version of Ubuntu is 14.04 LTS. Is it able to use mainline kernel? I never do it because i am using Ubuntu system since one month ago.

---

### Post by phanhan on 2014-09-15
Hello every body.
I installed 5364732-DPO_RT5572_LinuxSTA_2.6.1.3_20121022_prepared.tar. gz and blacklist rt2800usb. After i reboot and connect adapter to PC, the new driver able to detect my adapter. However, my PC crashed immediately after i opened my browser. I found the user in the forum posted by praseodym has the same crash issue.

[COLOR=#000000]ads: VinaHost là công ty cung c&#7845;p d&#7883;ch v&#7909; [/COLOR][thuê máy ch&#7911;]("http://vinahost.vn/may-chu-rieng.html")[COLOR=#000000] và cho thuê máy ch&#7911; và [/COLOR][thuê pvs]("http://vinahost.vn/gioi-thieu-cong-nghe-cloud.html")[COLOR=#000000] và [/COLOR][Hosting doanh nghi&#7879;p]("http://vinahost.vn/business_hosting.php")[COLOR=#000000] và [/COLOR][d&#7883;ch v&#7909; email hosting]("http://vinahost.vn/email-hosting.html")[COLOR=#000000] [/COLOR]
[COLOR=#000000]và [/COLOR][ki&#7875;m tra tên mi&#7873;n]("http://vinahost.vn/ho-tro-ten-mien.html")[COLOR=#000000] và [/COLOR][&#273;&#259;ng ký tên mi&#7873;n]("http://vinahost.vn/vndomain.php")[COLOR=#000000] và tên mi&#7873;n vi&#7879;t nam và l&#432;u tr&#7919; website chuyên nghi&#7879;p v&#7899;i h&#417;n 8 n&#259;m kinh nghi&#7879;m trên th&#7883; tr&#432;&#7901;ng Vi&#7879;t Nam và B&#7855;c M&#7929;.[/COLOR]

---

### Post by varunendra on 2014-09-16
Hello phanhan!

Did you try to tweak the native driver first? If not, I recommend you purge the proprietary driver, and post a report of the [wireless_script]("http://ubuntuforums.org/showpost.php?p=13024222") in a new thread of your own with a relevant title.

---

