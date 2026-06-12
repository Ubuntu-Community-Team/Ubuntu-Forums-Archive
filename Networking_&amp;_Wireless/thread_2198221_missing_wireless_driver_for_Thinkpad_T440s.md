---
title: "missing wireless driver for Thinkpad T440s?"
date: 2014-01-07
forum: Networking &amp; Wireless
---

### Post by Niles M on 2014-01-07
I have installed 12.04LTS on my Lenovo T440s, but I simply can't get the wireless to work. I have tried writing ```
lshw
``` 

and it only displays PCIPCI (sysfs). Somehow I don't think any/all the drivers were installed during installation, because some of the hotkeys (such as screen brightness etc...) don't work either -- but I'm not sure if this is correct. I have tried updating, but to no avail. What can I do here to test further?

---

### Post by varunendra on 2014-01-08
Hello Niles !

Please follow the "Wireless Script" link in my signature, download and run the script as per instructions there, and post back the report it generates.

---

### Post by sharon-talbot on 2014-01-11
Hi.

I also have the T440s, and wireless does not work out of the box in Ubuntu.  I have tried some other solutions in other threads, but they did not work.  I have attached the results of the wireless_script as requested.

[ATTACH]249371[/ATTACH]

---

### Post by chili555 on 2014-01-11
Please check here: [http://askubuntu.com/questions/376732/thinkpad-t440p-wireless-network-controller](http://askubuntu.com/questions/376732/thinkpad-t440p-wireless-network-controller) You have the same wireless device 10ec:818b.

---

### Post by sharon-talbot on 2014-01-11
Bummer.  For the time being I have ordered a usb mini-dongle for wi-fi from the raspberry pi community: [http://www.adafruit.com/products/814](http://www.adafruit.com/products/814)

---

### Post by chili555 on 2014-01-11
Check back in a few months. Things change for the better. I'll be glad to help if I can.

---

### Post by programmer-x on 2014-02-08
After continuous search for RTL8192EE driver, I found it here.
[http://netbook-remix.archive.canonical.com/updates/pool/public/o/oem-wireless-rtl-92ce-92se-92de-8723ae-88ee-8723be-92ee-dkms/](http://netbook-remix.archive.canonical.com/updates/pool/public/o/oem-wireless-rtl-92ce-92se-92de-8723ae-88ee-8723be-92ee-dkms/)
I'm able to compile and load rtl8192ee on my lenovo t440s laptop.
However, transmitt speed very slow. For couple of times I got too many Invalid misc: and practically the connection is useless.
After few reboots and it seems to be fine. I'm sending this note from t440s loaded with 8192ee internet connection. Main drawback right now, I'm able to get only at max 60kB/s.

~$ iwconfig
wlan1 IEEE 802.11bgn ESSID:"myap"
          Mode:Managed Frequency:2.462 GHz Access Point: 58:6D:8F:64:22:FF
          Bit Rate=144.4 Mb/s Tx-Power=20 dBm
          Retry long limit:7 RTS thr=2347 B Fragment thr:off
          Power Management:off
          Link Quality=70/70 Signal level=-34 dBm
          Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
          Tx excessive retries:0 Invalid misc:247 Missed beacon:0

$ uptime
 23:28:08 up 15 min, 3 users, load average: 0.39, 0.61, 0.45

$ ifconfig wlan1
wlan1 Link encap:Ethernet HWaddr XXXXXXXXXX
          inet addr:192.168.1.92 Bcast:192.168.1.127 Mask:255.255.255.128
          inet6 addr: XXXXXXXXXXXX/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
          RX packets:35328 errors:0 dropped:0 overruns:0 frame:0
          TX packets:26022 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:49315226 (49.3 MB) TX bytes:3186066 (3.1 MB)

---

### Post by varunendra on 2014-02-09
Welcome to the forums programmer-x! :)

> **programmer-x said:**
> I'm sending this note from t440s loaded with 8192ee internet connection. Main drawback right now, I'm able to get only at max 60kB/s.
A few quick suggestions (try one at a time, or together if needed) -

- Try disabling N-channel in your router.
- Make sure "IPv6" is set to "Ignore" in Network Manager. Or permanently disable it following this post : [http://ubuntuforums.org/showpost.php?p=12640479](http://ubuntuforums.org/showpost.php?p=12640479)

If these don't help, please follow the "Wireless Script" link in my signature, download and run the script as per instructions there, and post back the report it generates.

While posting the outputs, please use '**Code**' tags. It preserves the output's formatting and makes the post cleaner, compact and more readable. To see a quick 'HowTo' with screenshots, please follow the "Using Code Tags" link in my signature.

**PS:**
Please use normal fonts for easier readability.

---

### Post by programmer-x on 2014-02-09
Varun,

Appreciate your help. I tried disabling N in my router and it didnt improve the situation. Rather it brought down my connection completely.

I put my router to Auto mode and changed back to my SSID. This time, momentarily the connection speed was 10Mbps and last only for few seconds. Again it got dropped significantly. Most of the time I notice Invalid Misc: counter hikes up large. 

Basically its very unstable driver at the moment. I know that driver is not yet available in mainstream linux firmware and Adam Lee is working on it. 
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1239578](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1239578)


```



*************** info trace ***************


***** uname -a *****


Linux mylaptop-t440s 3.11.0-15-generic #25-Ubuntu SMP AP20hu Jan 30 17:22:01 UAP20C 2014 x86_64 x86_64 x86_64 GNU/Linux


***** lsb_release *****


Distributor ID:    Ubuntu
Description:    Ubuntu 13.10
Release:    13.10
Codename:    saucy


***** lspci *****


00:19.0 Ethernet controller [0200]: Intel Corporation Ethernet Connection I218-V [8086:1559] (rev 04)
    Subsystem: Lenovo Device [17aa:2214]
    Kernel driver in use: e1000e
--
03:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. Device [10ec:818b]
    Subsystem: Realtek Semiconductor Co., Ltd. Device [10ec:001b]
    Kernel driver in use: rtl8192ee


***** lsusb *****


Bus 001 Device 002: ID 8087:8000 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 002 Device 005: ID 5986:026a Acer, Inc 
Bus 002 Device 004: ID 0bda:8761 Realtek Semiconductor Corp. 
Bus 002 Device 003: ID 138a:0017 Validity Sensors, Inc. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


***** PCMCIA Card Info *****




***** iwconfig *****


wlan1     IEEE 802.11bgn  ESSID:"Woody"
          Mode:Managed  Frequency:2.437 GHz  Access Point: <MAC address removed>   
          Bit Rate=144.4 Mb/s   AP20x-Power=20 dBm   
          Retry  long limit:7   RAP20S thr:off   Fragment thr:off
          Power Management:off
          Link Quality=70/70  Signal level=-34 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          AP20x excessive retries:0  Invalid misc:153   Missed beacon:0




***** rfkill *****


0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
1: tpacpi_bluetooth_sw: Bluetooth
    Soft blocked: no
    Hard blocked: no
2: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no


***** lsmod *****


rtl8192ee             139274  0 
btcoexist             105039  1 rtl8192ee
rtlwifi               129442  1 rtl8192ee
mac80211              597268  2 rtlwifi,rtl8192ee
cfg80211              480503  2 mac80211,rtlwifi


***** nm-tool *****


NetworkManager Tool


State: connected (global)


- Device: wlan1  [Woody] -----------------------------------------------
  Type:              802.11 WiFi
  Driver:            rtl8192ee
  State:             connected
  Default:           yes
  HW Address:        <MAC address removed>


  Capabilities:
    Speed:           144 Mb/s


  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes


  Wireless Access Points (* = current AP)
    Woody_Guest:    Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 100 WPA WPA2
    AP16:        Infra, <MAC address removed>, Freq 2427 MHz, Rate 54 Mb/s, Strength 97 WPA WPA2
    AP2:        Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 97 WPA2
    AP0:        Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 84 WPA
    AP16:        Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 77 WPA WPA2
    AP2:        Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 64 WPA WPA2
    AP17:        Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 64 WPA WPA2
    AP4:        Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 64 WPA WPA2
    AP5:        Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 64 WPA WPA2
    AP6:        Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 64 WPA WPA2
    AP7:        Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 57 WPA WPA2
    AP8:        Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 64 WPA WPA2
    AP9:        Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 50 WPA WPA2
    AP160:        Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 50 WPA WPA2
    AP19:        Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 50 WPA WPA2
    AP162:        Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 44 WPA2
    AP163 2:        Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 50 WPA WPA2
    AP164:        Infra, <MAC address removed>, Freq 2427 MHz, Rate 54 Mb/s, Strength 44 WPA WPA2
    AP165:        Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 44 WPA2
    AP16:        Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 84
    AP17:        Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 64
    AP18:        Infra, <MAC address removed>, Freq 2457 MHz, Rate 54 Mb/s, Strength 64
    AP19-1052:        Infra, <MAC address removed>, Freq 2457 MHz, Rate 54 Mb/s, Strength 84 WPA WPA2
    AP20-321:        Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 44 WPA WPA2
    AP21:        Infra, <MAC address removed>, Freq 2452 MHz, Rate 54 Mb/s, Strength 37 WPA WPA2
    AP22:        Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 44 WPA WPA2
    AP23:        Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 30 WPA WPA2
    AP24:        Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 37
    AP25!:        Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 27 WPA2
    *Woody:        Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 86 WPA WPA2


  IPv4 Settings:
    Address:         192.168.1.92
    Prefix:          25 (255.255.255.128)
    Gateway:         192.168.1.1


    DNS:             192.168.1.1




- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            e1000e
  State:             unavailable
  Default:           no
  HW Address:        <MAC address removed>


  Capabilities:
    Carrier Detect:  yes


  Wired Properties
    Carrier:         off






***** NetworkManager.state *****
[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true


***** NetworkManager.conf *****


[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq


[ifupdown]
managed=false


***** interfaces *****


# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback


***** iwlist *****


wlan1     Scan completed :
      Cell 01 - Address: <MAC address removed>
            Channel:6
            Frequency:2.437 GHz (Channel 6)
            Quality=70/70  Signal level=-28 dBm
            Encryption key:on
            ESSID:"Woody"
            Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                  24 Mb/s; 36 Mb/s; 54 Mb/s
            Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
            Mode:Master
            Extra:tsf=00000000284e4f53
            Extra: Last beacon: 36ms ago
            IE: Unknown: 000D73735F73776565745F686F6D65
            IE: Unknown: 010882848B962430486C
            IE: Unknown: 030106
            IE: Unknown: 2A0100
            IE: Unknown: 2F0100
            IE: IEEE 802.11i/WPA2 Version 1
            Group Cipher : CCMP
            Pairwise Ciphers (1) : CCMP
            Authentication Suites (1) : PSK
            IE: Unknown: 32040C121860
            IE: Unknown: 2D1AEC181BFFFF000000000000000000000000000000000000000000
            IE: Unknown: 3D1606080400000000000000000000000000000000000000
            IE: Unknown: DD090010180202F02C0000
            IE: WPA Version 1
            Group Cipher : CCMP
            Pairwise Ciphers (1) : CCMP
            Authentication Suites (1) : PSK
            IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
      Cell 02 - Address: <MAC address removed>
            Channel:6
            Frequency:2.437 GHz (Channel 6)
            Quality=44/70  Signal level=-66 dBm
            Encryption key:on
            ESSID:"AP19-F09C"
            Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                  24 Mb/s; 36 Mb/s; 54 Mb/s
            Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
            Mode:Master
            Extra:tsf=00000059871b1dbf
            Extra: Last beacon: 36ms ago
            IE: Unknown: 0009484F4D452D46303943
            IE: Unknown: 010882848B9624B0486C
            IE: Unknown: 030106
            IE: Unknown: 2A0100
            IE: Unknown: 2F0100
            IE: IEEE 802.11i/WPA2 Version 1
            Group Cipher : TKIP
            Pairwise Ciphers (2) : CCMP TKIP
            Authentication Suites (1) : PSK
            IE: Unknown: 32048C129860
            IE: Unknown: 2D1AFD181BFFFFFF0000000000000000000000000000000000000000
            IE: Unknown: 3D1606081500000000000000000000000000000000000000
            IE: Unknown: DD8C0050F204104A0001101044000102103B0001031047001099F8C471A5AB69AB761168B3E91DF8751021000B546563686E69636F6C6F721023000B546563686E69636F6C6F721024000631323334353610420007303030303030311054000800060050F20400011011000D546563686E69636F6C6F724150100800022008103C0001011049000600372A000120
            IE: Unknown: DD090010180203F03C0000
            IE: WPA Version 1
            Group Cipher : TKIP
            Pairwise Ciphers (2) : CCMP TKIP
            Authentication Suites (1) : PSK
            IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
      Cell 03 - Address: <MAC address removed>
            Channel:6
            Frequency:2.437 GHz (Channel 6)
            Quality=40/70  Signal level=-70 dBm
            Encryption key:on
            ESSID:"AP5"
            Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                  24 Mb/s; 36 Mb/s; 54 Mb/s
            Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
            Mode:Master
            Extra:tsf=0000000d02780184
            Extra: Last beacon: 192ms ago
            IE: Unknown: 00066261626C6F6F
            IE: Unknown: 010882848B962430486C
            IE: Unknown: 030106
            IE: Unknown: 050400010000
            IE: Unknown: 2A0104
            IE: Unknown: 2F0104
            IE: IEEE 802.11i/WPA2 Version 1
            Group Cipher : TKIP
            Pairwise Ciphers (2) : CCMP TKIP
            Authentication Suites (1) : PSK
            IE: Unknown: 32040C121860
            IE: Unknown: DD06001018020304
            IE: WPA Version 1
            Group Cipher : TKIP
            Pairwise Ciphers (2) : CCMP TKIP
            Authentication Suites (1) : PSK
      Cell 04 - Address: <MAC address removed>
            Channel:4
            Frequency:2.427 GHz (Channel 4)
            Quality=40/70  Signal level=-70 dBm
            Encryption key:on
            ESSID:"AP164"
            Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                  11 Mb/s; 12 Mb/s; 18 Mb/s
            Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
            Mode:Master
            Extra:tsf=0000000d69ea15e1
            Extra: Last beacon: 36ms ago
            IE: Unknown: 00083257495245363435
            IE: Unknown: 010882848B0C12961824
            IE: Unknown: 030104
            IE: Unknown: 0706555320010B1B
            IE: IEEE 802.11i/WPA2 Version 1
            Group Cipher : TKIP
            Pairwise Ciphers (2) : CCMP TKIP
            Authentication Suites (1) : PSK
            IE: WPA Version 1
            Group Cipher : TKIP
            Pairwise Ciphers (2) : CCMP TKIP
            Authentication Suites (1) : PSK
            IE: Unknown: 2A0100
            IE: Unknown: 32043048606C
      Cell 05 - Address: <MAC address removed>
            Channel:6
            Frequency:2.437 GHz (Channel 6)
            Quality=56/70  Signal level=-54 dBm
            Encryption key:on
            ESSID:"AP4"
            Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                  9 Mb/s; 12 Mb/s; 18 Mb/s
            Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
            Mode:Master
            Extra:tsf=00000dba98beae62
            Extra: Last beacon: 36ms ago
            IE: Unknown: 0007766972616C3834
            IE: Unknown: 010882848B960C121824
            IE: Unknown: 030106
            IE: Unknown: 0406000200000000
            IE: Unknown: 2A0100
            IE: Unknown: 32043048606C
            IE: IEEE 802.11i/WPA2 Version 1
            Group Cipher : TKIP
            Pairwise Ciphers (1) : CCMP
            Authentication Suites (1) : PSK
            IE: Unknown: 2D1A6C1017FFFFFF0000000000000000000000000000000000000000
            IE: Unknown: 3D1606000500000000000000000000000000000000000000
            IE: Unknown: 4A0E14000A00B400C800140005001900
            IE: Unknown: 7F0101
            IE: Unknown: DD1E00904C336C1017FFFFFF0000000000000000000000000000000000000000
            IE: Unknown: DD1A00904C3406000500000000000000000000000000000000000000
            IE: Unknown: DD06005043030000
            IE: WPA Version 1
            Group Cipher : TKIP
            Pairwise Ciphers (1) : TKIP
            Authentication Suites (1) : PSK
            IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
            IE: Unknown: DD730050F204104A0001101044000102103B000103104700101F64A5CA511F481786DAF1E6D55FC1F210210005436973636F10230003574150102400033132331042000531323334351054000800060050F204000110110007766972616C383410080002200C103C0001011049000600372A000120
      Cell 06 - Address: <MAC address removed>
            Channel:6
            Frequency:2.437 GHz (Channel 6)
            Quality=70/70  Signal level=-30 dBm
            Encryption key:on
            ESSID:"Woody_Guest"
            Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                  24 Mb/s; 36 Mb/s; 54 Mb/s
            Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
            Mode:Master
            Extra:tsf=00000000284318b4
            Extra: Last beacon: 36ms ago
            IE: Unknown: 000873735F6775657374
            IE: Unknown: 010882848B962430486C
            IE: Unknown: 030106
            IE: Unknown: 2A0100
            IE: Unknown: 2F0100
            IE: IEEE 802.11i/WPA2 Version 1
            Group Cipher : CCMP
            Pairwise Ciphers (1) : CCMP
            Authentication Suites (1) : PSK
            IE: Unknown: 32040C121860
            IE: Unknown: 2D1AEC181BFFFF000000000000000000000000000000000000000000
            IE: Unknown: 3D1606081100000000000000000000000000000000000000
            IE: Unknown: DD090010180200F02C0000
            IE: WPA Version 1
            Group Cipher : CCMP
            Pairwise Ciphers (1) : CCMP
            Authentication Suites (1) : PSK
            IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
      Cell 07 - Address: <MAC address removed>
            Channel:6
            Frequency:2.437 GHz (Channel 6)
            Quality=48/70  Signal level=-62 dBm
            Encryption key:on
            ESSID:"AP6"
            Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                  24 Mb/s; 36 Mb/s; 54 Mb/s
            Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
            Mode:Master
            Extra:tsf=0000016cc6cacc77
            Extra: Last beacon: 36ms ago
            IE: Unknown: 0006415454313932
            IE: Unknown: 010882848B962430486C
            IE: Unknown: 030106
            IE: Unknown: 2A0104
            IE: Unknown: 2F0104
            IE: IEEE 802.11i/WPA2 Version 1
            Group Cipher : TKIP
            Pairwise Ciphers (2) : CCMP TKIP
            Authentication Suites (1) : PSK
            IE: Unknown: 32040C121860
            IE: Unknown: 2D1A7C181BFFFF000000000000000000000000000000000000000000
            IE: Unknown: 3D1606081500000000000000000000000000000000000000
            IE: Unknown: 4A0E14000A002C01C800140005001900
            IE: Unknown: 7F0101
            IE: Unknown: DD090010180203F02C0000
            IE: WPA Version 1
            Group Cipher : TKIP
            Pairwise Ciphers (2) : CCMP TKIP
            Authentication Suites (1) : PSK
            IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
      Cell 08 - Address: <MAC address removed>
            Channel:6
            Frequency:2.437 GHz (Channel 6)
            Quality=56/70  Signal level=-54 dBm
            Encryption key:on
            ESSID:"AP0"
            Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                  12 Mb/s; 24 Mb/s; 36 Mb/s
            Bit Rates:9 Mb/s; 18 Mb/s; 48 Mb/s; 54 Mb/s
            Mode:Master
            Extra:tsf=000000821c12864d
            Extra: Last beacon: 36ms ago
            IE: Unknown: 000668616C636F6E
            IE: Unknown: 010882848B960C183048
            IE: Unknown: 030106
            IE: Unknown: 2A0100
            IE: Unknown: 32041224606C
            IE: WPA Version 1
            Group Cipher : TKIP
            Pairwise Ciphers (1) : TKIP
            Authentication Suites (1) : PSK
            IE: Unknown: DD0900037F0101001DFF7F
            IE: Unknown: DD0C00037F020101000002A44000
            IE: Unknown: DD1A00037F0301000000001B2F65C37A021B2F65C37A64002C011D08
      Cell 09 - Address: <MAC address removed>
            Channel:6
            Frequency:2.437 GHz (Channel 6)
            Quality=32/70  Signal level=-78 dBm
            Encryption key:on
            ESSID:"AP23"
            Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                  24 Mb/s; 36 Mb/s; 54 Mb/s
            Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
            Mode:Master
            Extra:tsf=00000001a2048183
            Extra: Last beacon: 1964ms ago
            IE: Unknown: 0006415454353834
            IE: Unknown: 010882848B962430486C
            IE: Unknown: 030106
            IE: Unknown: 050402030000
            IE: Unknown: 2A0100
            IE: Unknown: 2F0100
            IE: IEEE 802.11i/WPA2 Version 1
            Group Cipher : TKIP
            Pairwise Ciphers (2) : CCMP TKIP
            Authentication Suites (1) : PSK
            IE: Unknown: 32040C121860
            IE: Unknown: 2D1A7C181BFFFF000000000000000000000000000000000000000000
            IE: Unknown: 3D1606001300000000000000000000000000000000000000
            IE: Unknown: 4A0E14000A002C01C800140005001900
            IE: Unknown: 7F0101
            IE: Unknown: DD090010180203F02C0000
            IE: WPA Version 1
            Group Cipher : TKIP
            Pairwise Ciphers (2) : CCMP TKIP
            Authentication Suites (1) : PSK
            IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
      Cell 10 - Address: <MAC address removed>
            Channel:4
            Frequency:2.427 GHz (Channel 4)
            Quality=69/70  Signal level=-41 dBm
            Encryption key:on
            ESSID:"AP16"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000e48d5dcf40
                    Extra: Last beacon: 36ms ago
                    IE: Unknown: 0008636F6C6C696E7377
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 030104
                    IE: Unknown: 2A0104
                    IE: Unknown: 32048C98B060
                    IE: Unknown: 2D1A8E1117FFFF000001000000000000000000000000000000000000
                    IE: Unknown: 3D1604050500000000000000000000000000000000000000
                    IE: Unknown: 3E0100
                    IE: WPA Version 1
            Group Cipher : TKIP
            Pairwise Ciphers (2) : TKIP CCMP
            Authentication Suites (1) : PSK
            IE: IEEE 802.11i/WPA2 Version 1
            Group Cipher : TKIP
            Pairwise Ciphers (2) : TKIP CCMP
            Authentication Suites (1) : PSK
            IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
            IE: Unknown: 0B05010015127A
            IE: Unknown: 4A0E14000A002C01C800140005001900
            IE: Unknown: 7F0101
            IE: Unknown: DD07000C4303000000
            IE: Unknown: 0706555320010B10
            IE: Unknown: DD870050F204104A0001101044000102103B000103104700102880288028801880A880F8EDA5984D9010210005415252495310230006544738363247102400065254323836301042000831323334353637381054000800060050F204000110110012415252495320544738363220526F7574657210080002210C103C0001011049000600372A000120
      Cell 11 - Address: <MAC address removed>
            Channel:4
            Frequency:2.427 GHz (Channel 4)
            Quality=68/70  Signal level=-42 dBm
            Encryption key:on
            ESSID:""
            Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                  18 Mb/s; 36 Mb/s; 54 Mb/s
            Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
            Mode:Master
            Extra:tsf=000000e48d8bcbd7
            Extra: Last beacon: 216ms ago
            IE: Unknown: 0000
            IE: Unknown: 010882848B961224486C
            IE: Unknown: 030104
            IE: Unknown: 32048C98B060
            IE: Unknown: 070C55532001010F0209110B010F
            IE: Unknown: 050400010000
            IE: Unknown: 2A0104
            IE: Unknown: 2D1A8E1117FFFF000001000000000000000000000000000000000000
            IE: Unknown: 3D1604050500000000000000000000000000000000000000
            IE: Unknown: 4A0E14000A002C01C800140005001900
            IE: Unknown: 7F0101
            IE: IEEE 802.11i/WPA2 Version 1
            Group Cipher : CCMP
            Pairwise Ciphers (1) : CCMP
            Authentication Suites (1) : PSK
            IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
            IE: Unknown: 0B05010018127A
            IE: Unknown: DD07000C4303000000
      Cell 12 - Address: <MAC address removed>
            Channel:6
            Frequency:2.437 GHz (Channel 6)
            Quality=70/70  Signal level=-25 dBm
            Encryption key:on
            ESSID:"Woody_Guest"
            Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                  24 Mb/s; 36 Mb/s; 54 Mb/s
            Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
            Mode:Master
            Extra:tsf=00000000281cc9aa
            Extra: Last beacon: 4344ms ago
            IE: Unknown: 000873735F6775657374
            IE: Unknown: 010882848B962430486C
            IE: Unknown: 030106
            IE: Unknown: 050400010000
            IE: Unknown: 2A0100
            IE: Unknown: 2F0100
            IE: IEEE 802.11i/WPA2 Version 1
            Group Cipher : CCMP
            Pairwise Ciphers (1) : CCMP
            Authentication Suites (1) : PSK
            IE: Unknown: 32040C121860
            IE: Unknown: 2D1AEC181BFFFF000000000000000000000000000000000000000000
            IE: Unknown: 3D1606081100000000000000000000000000000000000000
            IE: Unknown: DD090010180200F02C0000
            IE: WPA Version 1
            Group Cipher : CCMP
            Pairwise Ciphers (1) : CCMP
            Authentication Suites (1) : PSK
            IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
      Cell 13 - Address: <MAC address removed>
            Channel:1
            Frequency:2.412 GHz (Channel 1)
            Quality=28/70  Signal level=-82 dBm
            Encryption key:on
            ESSID:"AP165_guest 2"
            Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                  9 Mb/s; 12 Mb/s; 18 Mb/s
            Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
            Mode:Master
            Extra:tsf=0000004900bba4d6
            Extra: Last beacon: 3576ms ago
            IE: Unknown: 00165765737465726E4469676974616C5F67756573742032
            IE: Unknown: 010882848B960C121824
            IE: Unknown: 030101
            IE: Unknown: 050400010000
            IE: Unknown: 0706555320010B1E
            IE: Unknown: 2A0102
            IE: IEEE 802.11i/WPA2 Version 1
            Group Cipher : CCMP
            Pairwise Ciphers (1) : CCMP
            Authentication Suites (1) : PSK
            IE: Unknown: 32043048606C
            IE: Unknown: 2D1AAD011BFFFFFF0000000000000000000000000000000000000000
            IE: Unknown: 3D1601001500000000000000000000000000000000000000
            IE: Unknown: 4A0E14000A002C01C800140005001900
            IE: Unknown: 7F0101
            IE: Unknown: DD180050F2020101820003A4000027A4000042435E0062322F00
            IE: Unknown: DD0900037F01010000FF7F
      Cell 14 - Address: <MAC address removed>
            Channel:1
            Frequency:2.412 GHz (Channel 1)
            Quality=52/70  Signal level=-58 dBm
            Encryption key:on
            ESSID:"AP16"
            Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                  24 Mb/s; 36 Mb/s; 54 Mb/s
            Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
            Mode:Master
            Extra:tsf=000002b5c73de4a9
            Extra: Last beacon: 36ms ago
            IE: Unknown: 0008596F756E67446F67
            IE: Unknown: 010882848B962430486C
            IE: Unknown: 030101
            IE: Unknown: 2A0102
            IE: Unknown: 2F0102
            IE: IEEE 802.11i/WPA2 Version 1
            Group Cipher : TKIP
            Pairwise Ciphers (2) : CCMP TKIP
            Authentication Suites (1) : PSK
            IE: Unknown: 32040C121860
            IE: Unknown: 2D1A7C181BFFFF000000000000000000000000000000000000000000
            IE: Unknown: 3D1601001700000000000000000000000000000000000000
            IE: Unknown: DD670050F204104A00011010440001021041000100103B00010310470010C7DD8E1AC730AE8335A7A207A74B2FFC102100074C696E6B737973102300034D3230102400063132333435361042000234321054000800060050F2040001101100034D3230100800020084
            IE: Unknown: DD090010180202F0050000
            IE: WPA Version 1
            Group Cipher : TKIP
            Pairwise Ciphers (2) : CCMP TKIP
            Authentication Suites (1) : PSK
            IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
            IE: Unknown: DD1E00904C337C181BFFFF000000000000000000000000000000000000000000
            IE: Unknown: DD1A00904C3401001700000000000000000000000000000000000000
      Cell 15 - Address: <MAC address removed>
            Channel:1
            Frequency:2.412 GHz (Channel 1)
            Quality=56/70  Signal level=-54 dBm
            Encryption key:off
            ESSID:"AP16-guest"
            Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                  24 Mb/s; 36 Mb/s; 54 Mb/s
            Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
            Mode:Master
            Extra:tsf=000002b5c73dfd33
            Extra: Last beacon: 36ms ago
            IE: Unknown: 000E596F756E67446F672D6775657374
            IE: Unknown: 010882848B962430486C
            IE: Unknown: 030101
            IE: Unknown: 2A0102
            IE: Unknown: 2F0102
            IE: Unknown: 32040C121860
            IE: Unknown: 2D1A7C181BFFFF000000000000000000000000000000000000000000
            IE: Unknown: 3D1601001700000000000000000000000000000000000000
            IE: Unknown: DD090010180202F0050000
            IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
            IE: Unknown: DD1E00904C337C181BFFFF000000000000000000000000000000000000000000
            IE: Unknown: DD1A00904C3401001700000000000000000000000000000000000000
      Cell 16 - Address: <MAC address removed>
            Channel:1
            Frequency:2.412 GHz (Channel 1)
            Quality=52/70  Signal level=-58 dBm
            Encryption key:on
            ESSID:"AP2"
            Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                  24 Mb/s; 36 Mb/s; 54 Mb/s
            Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
            Mode:Master
            Extra:tsf=0000058c44d18188
            Extra: Last beacon: 3924ms ago
            IE: Unknown: 000976656C617A7175657A
            IE: Unknown: 010882848B9624B0486C
            IE: Unknown: 030101
            IE: Unknown: 050400010000
            IE: Unknown: 2A0102
            IE: Unknown: 2F0102
            IE: IEEE 802.11i/WPA2 Version 1
            Group Cipher : TKIP
            Pairwise Ciphers (2) : CCMP TKIP
            Authentication Suites (1) : PSK
            IE: Unknown: 32048C129860
            IE: Unknown: 2D1AFD181BFFFFFF0000000000000000000000000000000000000000
            IE: Unknown: 3D1601001700000000000000000000000000000000000000
            IE: Unknown: DD180050F204104A00011010440001021049000600372A000120
            IE: Unknown: DD090010180205F03C0000
            IE: WPA Version 1
            Group Cipher : TKIP
            Pairwise Ciphers (2) : CCMP TKIP
            Authentication Suites (1) : PSK
            IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
      Cell 17 - Address: <MAC address removed>
            Channel:1
            Frequency:2.412 GHz (Channel 1)
            Quality=56/70  Signal level=-54 dBm
            Encryption key:off
            ESSID:"AP17-guest"
            Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                  24 Mb/s; 36 Mb/s; 54 Mb/s
            Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
            Mode:Master
            Extra:tsf=0000009536e28845
            Extra: Last beacon: 36ms ago
            IE: Unknown: 00124672616E6B656E737465696E2D6775657374
            IE: Unknown: 010882848B962430486C
            IE: Unknown: 030101
            IE: Unknown: 2A0106
            IE: Unknown: 2F0106
            IE: Unknown: 32040C121860
            IE: Unknown: 2D1A7C181BFFFF000000000000000000000000000000000000000000
            IE: Unknown: 3D1601001700000000000000000000000000000000000000
            IE: Unknown: DD090010180201F0050000
            IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
            IE: Unknown: DD1E00904C337C181BFFFF000000000000000000000000000000000000000000
            IE: Unknown: DD1A00904C3401001700000000000000000000000000000000000000
      Cell 18 - Address: <MAC address removed>
            Channel:1
            Frequency:2.412 GHz (Channel 1)
            Quality=56/70  Signal level=-54 dBm
            Encryption key:on
            ESSID:"AP17"
            Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                  24 Mb/s; 36 Mb/s; 54 Mb/s
            Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
            Mode:Master
            Extra:tsf=0000009536e279fd
            Extra: Last beacon: 36ms ago
            IE: Unknown: 000C4672616E6B656E737465696E
            IE: Unknown: 010882848B962430486C
            IE: Unknown: 030101
            IE: Unknown: 2A0106
            IE: Unknown: 2F0106
            IE: IEEE 802.11i/WPA2 Version 1
            Group Cipher : TKIP
            Pairwise Ciphers (2) : CCMP TKIP
            Authentication Suites (1) : PSK
            IE: Unknown: 32040C121860
            IE: Unknown: 2D1A7C181BFFFF000000000000000000000000000000000000000000
            IE: Unknown: 3D1601001700000000000000000000000000000000000000
            IE: Unknown: DD670050F204104A00011010440001021041000100103B00010310470010910F336A6AF2DD8E57728D58B7168EFF102100074C696E6B737973102300034D3130102400063132333435361042000234321054000800060050F2040001101100034D3130100800020084
            IE: Unknown: DD090010180201F0050000
            IE: WPA Version 1
            Group Cipher : TKIP
            Pairwise Ciphers (2) : CCMP TKIP
            Authentication Suites (1) : PSK
            IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
            IE: Unknown: DD1E00904C337C181BFFFF000000000000000000000000000000000000000000
            IE: Unknown: DD1A00904C3401001700000000000000000000000000000000000000
      Cell 19 - Address: <MAC address removed>
            Channel:10
            Frequency:2.457 GHz (Channel 10)
            Quality=56/70  Signal level=-54 dBm
            Encryption key:on
            ESSID:"AP19-1052"
            Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                  18 Mb/s; 36 Mb/s; 54 Mb/s
            Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
            Mode:Master
            Extra:tsf=000000e4910caa99
            Extra: Last beacon: 440ms ago
            IE: Unknown: 0009484F4D452D31303532
            IE: Unknown: 010882848B961224486C
            IE: Unknown: 03010A
            IE: Unknown: 32048C98B060
            IE: Unknown: 070C55532001010F0209110B010F
            IE: Unknown: 050400010010
            IE: Unknown: DD310050F204104A0001101044000102104700102880288028801880A880CCA4620E1050103C0001011049000600372A000120
            IE: Unknown: 2A0104
            IE: Unknown: 2D1A0C0017FFFF000000000000000000000000000000000000000000
            IE: Unknown: 3D160A000400000000000000000000000000000000000000
            IE: Unknown: 7F0101
            IE: WPA Version 1
            Group Cipher : TKIP
            Pairwise Ciphers (2) : TKIP CCMP
            Authentication Suites (1) : PSK
            IE: IEEE 802.11i/WPA2 Version 1
            Group Cipher : TKIP
            Pairwise Ciphers (2) : TKIP CCMP
            Authentication Suites (1) : PSK
            IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
            IE: Unknown: 0B0501002D127A
            IE: Unknown: DD07000C4303000000
      Cell 20 - Address: <MAC address removed>
            Channel:10
            Frequency:2.457 GHz (Channel 10)
            Quality=52/70  Signal level=-58 dBm
            Encryption key:on
            ESSID:""
            Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                  18 Mb/s; 36 Mb/s; 54 Mb/s
            Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
            Mode:Master
            Extra:tsf=000000e49101c344
            Extra: Last beacon: 1152ms ago
            IE: Unknown: 0000
            IE: Unknown: 010882848B961224486C
            IE: Unknown: 03010A
            IE: Unknown: 32048C98B060
            IE: Unknown: 070C55532001010F0209110B010F
            IE: Unknown: 050400010000
            IE: Unknown: 2A0104
            IE: Unknown: 2D1A0C0017FFFF000000000000000000000000000000000000000000
            IE: Unknown: 3D160A000400000000000000000000000000000000000000
            IE: Unknown: 7F0101
            IE: IEEE 802.11i/WPA2 Version 1
            Group Cipher : CCMP
            Pairwise Ciphers (1) : CCMP
            Authentication Suites (1) : PSK
            IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
            IE: Unknown: 0B0501002D127A
            IE: Unknown: DD07000C4303000000
      Cell 21 - Address: <MAC address removed>
            Channel:11
            Frequency:2.462 GHz (Channel 11)
            Quality=64/70  Signal level=-46 dBm
            Encryption key:on
            ESSID:"AP2"
            Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                  24 Mb/s; 36 Mb/s; 54 Mb/s
            Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
            Mode:Master
            Extra:tsf=00000152068e5449
            Extra: Last beacon: 36ms ago
            IE: Unknown: 00085661646150616176
            IE: Unknown: 010882848B962430486C
            IE: Unknown: 03010B
            IE: Unknown: 2A0104
            IE: Unknown: 2F0104
            IE: IEEE 802.11i/WPA2 Version 1
            Group Cipher : CCMP
            Pairwise Ciphers (1) : CCMP
            Authentication Suites (1) : PSK
            IE: Unknown: 32040C121860
            IE: Unknown: 2D1AFC181BFFFF000000000000000000000000000000000000000000
            IE: Unknown: 3D160B081500000000000000000000000000000000000000
            IE: Unknown: DD840050F204104A0001101044000102103B00010310470010EE10FDCFB13312A67AD9AFD6EA21D2A610210005436973636F1023000D4C696E6B7379732045323530301024000776312E302E30371042000234321054000800060050F20400011011000D4C696E6B737973204532353030100800022688103C0001031049000600372A000120
            IE: Unknown: DD090010180201F0040000
            IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
      Cell 22 - Address: <MAC address removed>
            Channel:10
            Frequency:2.457 GHz (Channel 10)
            Quality=52/70  Signal level=-58 dBm
            Encryption key:off
            ESSID:"AP18"
            Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                  18 Mb/s; 36 Mb/s; 54 Mb/s
            Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
            Mode:Master
            Extra:tsf=000000e49101ca6d
            Extra: Last beacon: 1152ms ago
            IE: Unknown: 000B7866696E69747977696669
            IE: Unknown: 010882848B961224486C
            IE: Unknown: 03010A
            IE: Unknown: 32048C98B060
            IE: Unknown: 070C55532001010F0209110B010F
            IE: Unknown: 05040001004C
            IE: Unknown: 2A0104
            IE: Unknown: 2D1A0C0017FFFF000000000000000000000000000000000000000000
            IE: Unknown: 3D160A000400000000000000000000000000000000000000
            IE: Unknown: 7F0101
            IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
            IE: Unknown: 0B0501002D127A
            IE: Unknown: DD07000C4303000000
      Cell 23 - Address: <MAC address removed>
            Channel:11
            Frequency:2.462 GHz (Channel 11)
            Quality=70/70  Signal level=-25 dBm
            Encryption key:on
            ESSID:"AP8 Roll"
            Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                  9 Mb/s; 12 Mb/s; 18 Mb/s
            Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
            Mode:Master
            Extra:tsf=0000046753e6c06a
            Extra: Last beacon: 36ms ago
            IE: Unknown: 000B50616E65657220526F6C6C
            IE: Unknown: 010882848B960C121824
            IE: Unknown: 03010B
            IE: Unknown: 0706555320010B1E
            IE: Unknown: 2A0100
            IE: IEEE 802.11i/WPA2 Version 1
            Group Cipher : TKIP
            Pairwise Ciphers (2) : CCMP TKIP
            Authentication Suites (1) : PSK
            IE: Unknown: 32043048606C
            IE: Unknown: 2D1AAD0103FF7F000000000000000000000000000000000000000000
            IE: Unknown: 331AAD0103FF7F000000000000000000000000000000000000000000
            IE: Unknown: 3D160B001500000000000000000000000000000000000000
            IE: Unknown: 34160B001500000000000000000000000000000000000000
            IE: Unknown: 4A0E14000A002C01C800140005001900
            IE: Unknown: 7F0101
            IE: WPA Version 1
            Group Cipher : TKIP
            Pairwise Ciphers (2) : CCMP TKIP
            Authentication Suites (1) : PSK
            IE: Unknown: DD180050F2020101810003A4000027A4000042435E0062322F00
            IE: Unknown: DD0900037F01010000FF7F
            IE: Unknown: DDA00050F204104A0001101044000102103B00010310470010E3A950DA9B67150161890090A9CD85201021001B5765737465726E204469676974616C20436F72706F726174696F6E1023000B4D79204E6574204E373530102400094D794E65744E3735301042000C574E4E3433313630333331321054000800060050F2040001101100094D794E65744E37353010080002278C103C0001011049000600372A000120
      Cell 24 - Address: <MAC address removed>
            Channel:6
            Frequency:2.437 GHz (Channel 6)
            Quality=64/70  Signal level=-46 dBm
            Encryption key:off
            Mode:Master
            Extra:tsf=22000000005a6183
            Extra: Last beacon: 532ms ago
            IE: Unknown: 0CFFB3764CD9C50DE3D312E41B7C01F7CA191F639C634BD00BB05882DE5DEB13D06D2A36C94C6C0D9B0F00000FAC04000FAC020100000FAC020C0032040C1218602D1A7C181BFFFF0000000000000000000000000000000000000000003D16060013000000000000000000000000000000000000004A0E14000A002C01C8001400050019007F0101DD090010180203F02C0000DD1C0050F20101000050F20202000050F2040050F20201000050F2020C00DD180050F2020101800003A4000027A4000042435E0062322F00
      Cell 25 - Address: <MAC address removed>
            Channel:11
            Frequency:2.462 GHz (Channel 11)
            Quality=40/70  Signal level=-70 dBm
            Encryption key:on
            ESSID:"AP7"
            Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                  24 Mb/s; 36 Mb/s; 54 Mb/s
            Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
            Mode:Master
            Extra:tsf=0000005c13ad60e9
            Extra: Last beacon: 36ms ago
            IE: Unknown: 000C47757074615F50616E646579
            IE: Unknown: 010882848B962430486C
            IE: Unknown: 03010B
            IE: Unknown: 2A0100
            IE: Unknown: 2F0100
            IE: IEEE 802.11i/WPA2 Version 1
            Group Cipher : TKIP
            Pairwise Ciphers (2) : CCMP TKIP
            Authentication Suites (1) : PSK
            IE: Unknown: 32040C121860
            IE: Unknown: 2D1A7C181BFFFF000000000000000000000000000000000000000000
            IE: Unknown: 3D160B081100000000000000000000000000000000000000
            IE: Unknown: DD740050F204104A0001101044000102103B00010310470010D20830EBA35A8161C61BD59BE4AB7AB3102100074C696E6B73797310230004453930301024000776312E302E30341042000234321054000800060050F20400011011000445393030100800022688103C0001011049000600372A000120
            IE: Unknown: DD090010180200F02C0000
            IE: WPA Version 1
            Group Cipher : TKIP
            Pairwise Ciphers (2) : CCMP TKIP
            Authentication Suites (1) : PSK
            IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
      Cell 26 - Address: <MAC address removed>
            Channel:11
            Frequency:2.462 GHz (Channel 11)
            Quality=36/70  Signal level=-74 dBm
            Encryption key:on
            ESSID:"AP9"
            Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                  24 Mb/s; 36 Mb/s; 54 Mb/s
            Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
            Mode:Master
            Extra:tsf=000000388f5aa25c
            Extra: Last beacon: 36ms ago
            IE: Unknown: 000F466C79696E672050616E63616B6573
            IE: Unknown: 010882848B9624B0486C
            IE: Unknown: 03010B
            IE: Unknown: 2A0100
            IE: Unknown: 2F0100
            IE: IEEE 802.11i/WPA2 Version 1
            Group Cipher : TKIP
            Pairwise Ciphers (2) : CCMP TKIP
            Authentication Suites (1) : PSK
            IE: Unknown: 32048C129860
            IE: Unknown: 2D1AFD181BFFFFFF0000000000000000000000000000000000000000
            IE: Unknown: 3D160B081500000000000000000000000000000000000000
            IE: Unknown: DD8C0050F204104A0001101044000102103B000103104700102FA86151C0ED45BFA082831C37598C6A1021000B546563686E69636F6C6F721023000B546563686E69636F6C6F721024000631323334353610420007303030303030311054000800060050F20400011011000D546563686E69636F6C6F724150100800022008103C0001011049000600372A000120
            IE: Unknown: DD090010180206F03C0000
            IE: WPA Version 1
            Group Cipher : TKIP
            Pairwise Ciphers (2) : CCMP TKIP
            Authentication Suites (1) : PSK
            IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00




***** resolv.conf *****


nameserver 127.0.1.1


***** blacklist *****


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


***** modinfo *****


filename:       /lib/modules/3.11.0-15-generic/kernel/drivers/net/wireless/rtlwifi/rtl8192ee/rtl8192ee.ko
firmware:       rtlwifi/rtl8192eefw.bin
description:    Realtek 8192E 802.11n PCI wireless
license:        GPL
author:         Larry Finger    <Larry.Finger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         ping_yan    <ping_yan@realsil.com.cn>
srcversion:     26D9932D2E06D253C556338
alias:          pci:v000010ECd0000818Bsv*sd*bc*sc*i*
depends:        rtlwifi,btcoexist,mac80211
vermagic:       3.11.0-15-generic SMP mod_unload modversions
parm:           swlps:bool
parm:           swenc:using hardware crypto (default 0 [hardware])
 (bool)
parm:           ips:using no link power save (default 1 is open)
 (bool)
parm:           fwlps:using linked fw control power save (default 1 is open)
 (bool)


filename:       /lib/modules/3.11.0-15-generic/kernel/drivers/net/wireless/rtlwifi/rtlwifi.ko
description:    Realtek 802.11n PCI wireless core
license:        GPL
author:         Larry Finger    <Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         lizhaoming    <chaoming_li@realsil.com.cn>
srcversion:     8F98FFE1417D632790A6234
depends:        mac80211,cfg80211
vermagic:       3.11.0-15-generic SMP mod_unload modversions




***** udev rules *****


# PCI device 0x8086:0x1559 (e1000e)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"


# USB device 0x:0x (r8188eu)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"


# PCI device 0x10ec:0x818b (rtl8192ee)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan1"


***** dmesg *****


[    8.936951] rtlwifi: module verification failed: signature and/or required key missing - tainting kernel
[    8.939727] rtlwifi-0:rtl_pci_probe():<0-0> mem mapped space: start: 0xf0400000 len:00004000 flags:00140204, after map:0xffffc90000670000
[    8.939744] rtlwifi-0:_rtl_pci_find_adapter():<0-0> Pci Bridge Vendor is found index: 0
[    8.939748] rtlwifi-0:_rtl_pci_find_adapter():<0-0> pcidev busnumber:devnumber:funcnumber:vendor:link_ctl 3:0:0:10ec:0
[    8.939751] rtlwifi-0:_rtl_pci_find_adapter():<0-0> pci_bridge busnumber:devnumber:funcnumber:vendor:pcie_cap:link_ctl_reg:amd 0:28:1:8086:40:42:0
[    8.939776] rtl8192ee-0:rtl92ee_read_eeprom_info():<0-0> Boot from EFUSE
[    8.947101] rtl8192ee:
[    8.947385] rtl8192ee-0:_rtl92ee_read_adapter_info():<0-0> dev_addr: <MAC address removed>
[    8.947394] rtl8192ee-0:_rtl92ee_hal_customized_behavior():<0-0> RT Customized ID: 0x12
[    9.077560] btcoexist-0:rtl_btc_init_hal_vars():<0-0> rtl_btc_init_hal_vars, antNum is 2
[    9.077561] btcoexist-0:rtl_btc_init_hal_vars():<0-0> rtl_btc_init_hal_vars, bt_exist is 0
[    9.077562] btcoexist-0:rtl_btc_init_hal_vars():<0-0> rtl_btc_init_hal_vars, bt_type is 0
[    9.077720] rtlwifi-0:_rtl_init_hw_ht_capab():<0-0> 1T2R or 2T2R
[    9.080841] ieee80211 phy0: Selected rate control algorithm 'rtl_rc'
[    9.081055] rtlwifi: wireless switch is on
[    9.081083] rtl8192ee 0000:03:00.0: irq 62 for MSI/MSI-X
[    9.081114] rtlwifi-0:rtl_pci_intr_mode_msi():<0-0> MSI Interrupt Mode!
[   12.447146] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   12.447478] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   12.453461] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   12.659845] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   12.662535] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   12.664962] rtlwifi-0:rtl_pci_start():<0-0>  rtl_pci_start
[   12.669333] rtl8192ee-0:rtl92ee_download_fw():<0-0> normal Firmware SIZE 32754
[   12.669335] rtl8192ee-0:rtl92ee_download_fw():<0-0> Firmware Version(14), Signature(0x92e1),Size(32)
[   13.175525] rtl8192ee-0:rtl92ee_enable_hw_security_config():<0-0> PairwiseEncAlgorithm = 0 GroupEncAlgorithm = 0
[   13.175532] rtl8192ee-0:rtl92ee_enable_hw_security_config():<0-0> The SECR-value cc
[   13.341189] rtlwifi-0:rtl_pci_start():<0-0> rtl_pci_start OK
[   13.359950] IPv6: ADDRCONF(NETDEV_UP): wlan1: link is not ready
[   13.360236] IPv6: ADDRCONF(NETDEV_UP): wlan1: link is not ready
[   13.903310] psmouse serio2: trackpoint: IBM TrackPoint firmware: 0x0e, buttons: 3/3
[   15.424621] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   16.379351] wlan1: authenticate with <MAC address removed>
[   16.416127] rtlwifi-0:rtl_op_bss_info_changed():<0-0> bssid: <MAC address removed>
[   16.416529] wlan1: direct probe to <MAC address removed> (try 1/3)
[   16.618782] wlan1: direct probe to <MAC address removed> (try 2/3)
[   16.822650] wlan1: direct probe to <MAC address removed> (try 3/3)
[   17.026531] wlan1: authentication with <MAC address removed> timed out
[   17.035060] rtlwifi-0:rtl_op_bss_info_changed():<0-0> bssid: <MAC address removed>
[   24.037220] wlan1: authenticate with <MAC address removed>
[   24.072927] rtlwifi-0:rtl_op_bss_info_changed():<0-0> bssid: <MAC address removed>
[   24.073335] wlan1: send auth to <MAC address removed> (try 1/3)
[   24.073343] rtlwifi-0:rtl_tx_mgmt_proc():<200-1> MAC80211_LINKING
[   24.174607] wlan1: send auth to <MAC address removed> (try 2/3)
[   24.174619] rtlwifi-0:rtl_tx_mgmt_proc():<200-1> MAC80211_LINKING
[   24.278517] wlan1: send auth to <MAC address removed> (try 3/3)
[   24.278529] rtlwifi-0:rtl_tx_mgmt_proc():<200-1> MAC80211_LINKING
[   24.280975] wlan1: authenticated
[   24.282522] wlan1: associate with <MAC address removed> (try 1/3)
[   24.289134] rtlwifi-0:rtl_action_proc():<10000-1> Rx ACT_ADDBAREQ From :<MAC address removed>
[   24.289139] rtlwifi:
[   24.289163] rtlwifi-0:rtl_action_proc():<10000-1> sta is NULL
[   24.289709] rtlwifi-0:rtl_rx_agg_start():<0-0> on ra = <MAC address removed> tid = 0 seq:0
[   24.289718] rtlwifi-0:rtl_action_proc():<200-1> Tx ACT_ADDBARSP From :<MAC address removed>
[   24.386490] wlan1: associate with <MAC address removed> (try 2/3)
[   24.390370] wlan1: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=3)
[   24.390378] rtlwifi-0:rtl_op_sta_add():<0-0> Add sta addr is <MAC address removed>
[   24.390381] rtl8192ee-0:rtl92ee_update_hal_rate_mask():<0-0> ratr_bitmap :ffff005
[   24.390383] rtl8192ee-0:rtl92ee_update_hal_rate_mask():<0-0> Rate_index:2, ratr_val:ffff005, 0:82:0:5:f0:ff:f
[   24.390961] rtl8192ee-0:rtl92ee_update_hal_rate_mask():<0-0> ratr_bitmap :ffff005
[   24.390963] rtl8192ee-0:rtl92ee_update_hal_rate_mask():<0-0> Rate_index:2, ratr_val:ffff005, 0:82:0:5:f0:ff:f
[   24.391329] rtlwifi-0:rtl_op_bss_info_changed():<0-0> BSS_CHANGED_ASSOC
[   24.392053] rtl8192ee-0:rtl92ee_set_hw_reg():<0-0> switch case not process 5b
[   24.392254] rtl8192ee:
[   24.392256] In process "kworker/u16:1" (pid 76):rtl92ee_set_fw_rsvdpagepkt(): HW_VAR_SET_TX_CMD: ALL
[   24.392262] rtl8192ee:
[   24.399756] rtl8192ee:
[   24.399768] In process "kworker/u16:1" (pid 76):rtl92ee_set_fw_rsvdpagepkt(): HW_VAR_SET_TX_CMD: ALL
[   24.399790] rtlwifi-0:rtl_is_special_data():<10000-1> 802.1X Rx EAPOL pkt!!
[   24.400149] rtl8192ee:
[   24.408377] rtl8192ee:
[   24.408378] In process "kworker/u16:1" (pid 76):rtl92ee_set_fw_rsvdpagepkt(): HW_VAR_SET_TX_CMD: ALL
[   24.408381] rtl8192ee:
[   24.416620] rtl8192ee:
[   24.416621] In process "kworker/u16:1" (pid 76):rtl92ee_set_fw_rsvdpagepkt(): HW_VAR_SET_TX_CMD: ALL
[   24.416624] rtl8192ee:
[   24.424823] rtl8192ee:
[   24.424824] In process "kworker/u16:1" (pid 76):rtl92ee_set_fw_rsvdpagepkt(): HW_VAR_SET_TX_CMD: ALL
[   24.424827] rtl8192ee:
[   24.433422] wlan1: associated
[   24.433428] IPv6: ADDRCONF(NETDEV_CHANGE): wlan1: link becomes ready
[   24.503188] rtlwifi-0:rtl_is_special_data():<200-1> 802.1X Tx EAPOL pkt!!
[   24.503588] rtlwifi-0:rtl_is_special_data():<100-1> 802.1X Tx EAPOL pkt!!
[   25.358413] rtl8192ee-0:rtl92ee_update_hal_rate_mask():<0-0> ratr_bitmap :ffff005
[   25.358418] rtl8192ee-0:rtl92ee_update_hal_rate_mask():<0-0> Rate_index:2, ratr_val:ffff005, 0:82:0:5:f0:ff:f
[   25.509442] rtlwifi-0:rtl_is_special_data():<10000-1> 802.1X Rx EAPOL pkt!!
[   25.626370] rtlwifi-0:rtl_is_special_data():<200-1> 802.1X Tx EAPOL pkt!!
[   25.626758] rtlwifi-0:rtl_is_special_data():<100-1> 802.1X Tx EAPOL pkt!!
[   25.626798] rtlwifi-0:rtl_op_set_key():<0-0> Using hardware based encryption for keyidx: 0, mac: <MAC address removed>
[   25.626801] rtlwifi-0:rtl_op_set_key():<0-0> alg:CCMP
[   25.626802] rtlwifi-0:rtl_op_set_key():<0-0> set enable_hw_sec, key_type:4(OPEN:0 WEP40:1 TKIP:2 AES:4 WEP104:5)
[   25.626804] rtl8192ee-0:rtl92ee_enable_hw_security_config():<0-0> PairwiseEncAlgorithm = 4 GroupEncAlgorithm = 0
[   25.627157] rtl8192ee-0:rtl92ee_enable_hw_security_config():<0-0> The SECR-value cc
[   25.627350] rtlwifi-0:rtl_op_set_key():<0-0> set pairwise key
[   25.627351] rtl8192ee-0:rtl92ee_set_key():<0-0> add one entry
[   25.627353] rtl8192ee-0:rtl92ee_set_key():<0-0> set Pairwiase key
[   25.627354] rtlwifi-0:rtl_cam_add_one_entry():<0-0> EntryNo:4, ulKeyId=0, ulEncAlg=4, ulUseDK=0 MacAddr <MAC address removed>
[   25.627356] rtlwifi:
[   25.630061] rtlwifi-0:rtl_cam_add_one_entry():<0-0> end
[   25.630170] rtlwifi-0:rtl_op_set_key():<0-0> Using hardware based encryption for keyidx: 2, mac: <MAC address removed>
[   25.630184] rtlwifi-0:rtl_op_set_key():<0-0> alg:CCMP
[   25.630186] rtlwifi-0:rtl_op_set_key():<0-0> set group key
[   25.630188] rtl8192ee-0:rtl92ee_set_key():<0-0> add one entry
[   25.630190] rtl8192ee-0:rtl92ee_set_key():<0-0> set group key
[   25.630193] rtlwifi-0:rtl_cam_add_one_entry():<0-0> EntryNo:2, ulKeyId=2, ulEncAlg=4, ulUseDK=0 MacAddr <MAC address removed>
[   25.630195] rtlwifi:
[   25.633095] rtlwifi-0:rtl_cam_add_one_entry():<0-0> end
[   25.901776] rtlwifi-0:rtl_is_special_data():<200-1> dhcp Tx !!
[   27.361242] rtl8192ee-0:rtl92ee_update_hal_rate_mask():<0-0> ratr_bitmap :f8f0000
[   27.361247] rtl8192ee-0:rtl92ee_update_hal_rate_mask():<0-0> Rate_index:2, ratr_val:f8f0000, 0:82:0:0:0:8f:f
[   29.369154] rtlwifi-0:rtl_is_special_data():<200-1> dhcp Tx !!
[   29.405831] rtlwifi-0:rtl_is_special_data():<200-1> dhcp Tx !!
[   30.563973] rtlwifi-0:rtl_tx_agg_start():<0-0> on ra = <MAC address removed> tid = 0 seq:31
[   30.563990] rtlwifi-0:rtl_action_proc():<200-1> Tx ACT_ADDBAREQ From :<MAC address removed>
[   30.563993] rtlwifi:
[   30.581762] rtlwifi-0:rtl_action_proc():<10000-1> Rx ACT_ADDBARSP From :<MAC address removed>
[   30.582164] rtlwifi-0:rtl_tx_agg_oper():<0-0> on ra = <MAC address removed> tid = 0
[   33.371707] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[   33.371712] rtl8192ee:
[   33.371714] In process "kworker/0:0" (pid 4):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode
[   33.507775] rtlwifi-0:rtl_rx_agg_stop():<0-0> on ra = <MAC address removed> tid = 0
[   33.507785] rtlwifi-0:rtl_action_proc():<200-1> ACT_ADDBADEL From :<MAC address removed>
[   34.848807] rtlwifi-0:rtl_lps_set_psmode():<10000-1> FW LPS leave ps_mode:0
[   34.849155] rtl8192ee:
[   34.849157] In process "swapper/0" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode
[   35.553258] rtlwifi-0:rtl_action_proc():<10000-1> Rx ACT_ADDBAREQ From :<MAC address removed>
[   35.553263] rtlwifi:
[   35.553684] rtlwifi-0:rtl_rx_agg_start():<0-0> on ra = <MAC address removed> tid = 0 seq:44
[   35.553697] rtlwifi-0:rtl_action_proc():<200-1> Tx ACT_ADDBARSP From :<MAC address removed>
[   37.379555] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[   37.379560] rtl8192ee:
[   37.379562] In process "kworker/0:0" (pid 4):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode
[   37.532256] rtlwifi-0:rtl_lps_set_psmode():<10000-1> FW LPS leave ps_mode:0
[   37.532607] rtl8192ee:
[   37.532608] In process "swapper/0" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode
[   49.402829] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[   49.402835] rtl8192ee:
[   49.402837] In process "kworker/0:0" (pid 4):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode
[   52.146679] rtlwifi-0:rtl_tx_agg_stop():<0-0> on ra = <MAC address removed> tid = 0
[   52.146698] rtlwifi-0:rtl_action_proc():<400-1> ACT_ADDBADEL From :<MAC address removed>
[   62.962185] rtlwifi-0:rtl_tx_agg_start():<0-0> on ra = <MAC address removed> tid = 0 seq:63
[   62.962208] rtlwifi-0:rtl_action_proc():<200-1> Tx ACT_ADDBAREQ From :<MAC address removed>
[   62.962210] rtlwifi:
[   62.964764] rtlwifi-0:rtl_action_proc():<10000-1> Rx ACT_ADDBARSP From :<MAC address removed>
[   62.965343] rtlwifi-0:rtl_tx_agg_oper():<0-0> on ra = <MAC address removed> tid = 0
[   68.036234] rtlwifi-0:rtl_lps_set_psmode():<10000-1> FW LPS leave ps_mode:0
[   68.036243] rtl8192ee:
[   68.036245] In process "swapper/3" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode
[   71.445621] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[   71.445627] rtl8192ee:
[   71.445629] In process "kworker/0:0" (pid 4):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode
[   72.961867] rtlwifi-0:rtl_lps_set_psmode():<300-1> FW LPS leave ps_mode:0
[   72.962213] rtl8192ee:
[   72.962215] In process "swapper/2" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode
[   75.453453] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[   75.453463] rtl8192ee:
[   75.453467] In process "kworker/0:0" (pid 4):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode
[   84.071773] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS leave ps_mode:0
[   84.072127] rtl8192ee:
[   84.072131] In process "wpa_supplicant" (pid 1077):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode
[  103.773865] rtlwifi-0:rtl_tx_agg_start():<0-0> on ra = <MAC address removed> tid = 1 seq:2
[  103.773900] rtlwifi-0:rtl_action_proc():<200-1> Tx ACT_ADDBAREQ From :<MAC address removed>
[  103.773908] rtlwifi:
[  103.776341] rtlwifi-0:rtl_action_proc():<10000-1> Rx ACT_ADDBARSP From :<MAC address removed>
[  103.776780] rtlwifi-0:rtl_tx_agg_oper():<0-0> on ra = <MAC address removed> tid = 1
[  106.466067] rtlwifi-0:rtl_action_proc():<10000-1> Rx ACT_ADDBAREQ From :<MAC address removed>
[  106.466073] rtlwifi:
[  106.466322] rtlwifi-0:rtl_rx_agg_start():<0-0> on ra = <MAC address removed> tid = 1 seq:2
[  106.466335] rtlwifi-0:rtl_action_proc():<200-1> Tx ACT_ADDBARSP From :<MAC address removed>
[  108.927094] rtlwifi-0:rtl_tx_agg_stop():<0-0> on ra = <MAC address removed> tid = 1
[  108.927146] rtlwifi-0:rtl_action_proc():<400-1> ACT_ADDBADEL From :<MAC address removed>
[  127.540683] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[  127.540693] rtl8192ee:
[  127.540697] In process "kworker/0:0" (pid 4):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode
[  129.582269] rtlwifi-0:rtl_lps_set_psmode():<10000-1> FW LPS leave ps_mode:0
[  129.582619] rtl8192ee:
[  129.582620] In process "bamfdaemon" (pid 2119):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode
[  152.346836] rtlwifi-0:rtl_tx_agg_start():<0-0> on ra = <MAC address removed> tid = 1 seq:4
[  152.346869] rtlwifi-0:rtl_action_proc():<200-1> Tx ACT_ADDBAREQ From :<MAC address removed>
[  152.346876] rtlwifi:
[  152.349075] rtlwifi-0:rtl_action_proc():<10100-1> Rx ACT_ADDBARSP From :<MAC address removed>
[  152.349483] rtlwifi-0:rtl_tx_agg_oper():<0-0> on ra = <MAC address removed> tid = 1
[  158.199692] rtlwifi-0:rtl_tx_agg_stop():<0-0> on ra = <MAC address removed> tid = 1
[  158.199736] rtlwifi-0:rtl_action_proc():<400-1> ACT_ADDBADEL From :<MAC address removed>
[  161.589620] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[  161.589625] rtl8192ee:
[  161.589626] In process "kworker/0:0" (pid 4):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode
[  169.537386] rtlwifi-0:rtl_tx_agg_stop():<0-0> on ra = <MAC address removed> tid = 0
[  169.537429] rtlwifi-0:rtl_action_proc():<400-1> ACT_ADDBADEL From :<MAC address removed>
[  171.464215] rtlwifi-0:rtl_tx_agg_start():<0-0> on ra = <MAC address removed> tid = 0 seq:956
[  171.464230] rtlwifi-0:rtl_action_proc():<200-1> Tx ACT_ADDBAREQ From :<MAC address removed>
[  171.464232] rtlwifi:
[  171.466745] rtlwifi-0:rtl_action_proc():<10000-1> Rx ACT_ADDBARSP From :<MAC address removed>
[  171.467113] rtlwifi-0:rtl_tx_agg_oper():<0-0> on ra = <MAC address removed> tid = 0
[  172.345048] rtlwifi-0:rtl_lps_set_psmode():<10000-1> FW LPS leave ps_mode:0
[  172.345395] rtl8192ee:
[  172.345397] In process "swapper/0" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode
[  172.535657] rtlwifi-0:rtl_tx_agg_start():<0-0> on ra = <MAC address removed> tid = 1 seq:8
[  172.535676] rtlwifi-0:rtl_action_proc():<200-1> Tx ACT_ADDBAREQ From :<MAC address removed>
[  172.535679] rtlwifi:
[  172.538603] rtlwifi-0:rtl_action_proc():<10000-1> Rx ACT_ADDBARSP From :<MAC address removed>
[  172.538988] rtlwifi-0:rtl_tx_agg_oper():<0-0> on ra = <MAC address removed> tid = 1
[  177.728728] rtlwifi-0:rtl_tx_agg_stop():<0-0> on ra = <MAC address removed> tid = 1
[  177.728772] rtlwifi-0:rtl_action_proc():<400-1> ACT_ADDBADEL From :<MAC address removed>
[  179.615711] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[  179.615722] rtl8192ee:
[  179.615725] In process "kworker/0:0" (pid 4):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode
[  179.916879] rtlwifi-0:rtl_lps_set_psmode():<10000-1> FW LPS leave ps_mode:0
[  179.916896] rtl8192ee:
[  179.916900] In process "swapper/0" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode
[  185.624381] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[  185.624391] rtl8192ee:
[  185.624395] In process "kworker/0:0" (pid 4):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode
[  187.259469] rtlwifi-0:rtl_lps_set_psmode():<10000-1> FW LPS leave ps_mode:0
[  187.259822] rtl8192ee:
[  187.259825] In process "swapper/0" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode
[  189.630121] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[  189.630126] rtl8192ee:
[  189.630128] In process "kworker/0:0" (pid 4):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode
[  197.150113] rtlwifi-0:rtl_tx_agg_stop():<0-0> on ra = <MAC address removed> tid = 0
[  197.150152] rtlwifi-0:rtl_action_proc():<400-1> ACT_ADDBADEL From :<MAC address removed>
[  199.005001] rtlwifi-0:rtl_tx_agg_start():<0-0> on ra = <MAC address removed> tid = 0 seq:1160
[  199.005036] rtlwifi-0:rtl_action_proc():<200-1> Tx ACT_ADDBAREQ From :<MAC address removed>
[  199.005042] rtlwifi:
[  199.011940] rtlwifi-0:rtl_action_proc():<10000-1> Rx ACT_ADDBARSP From :<MAC address removed>
[  199.012597] rtlwifi-0:rtl_tx_agg_oper():<0-0> on ra = <MAC address removed> tid = 0
[  204.006470] rtlwifi-0:rtl_lps_set_psmode():<300-1> FW LPS leave ps_mode:0
[  204.006484] rtl8192ee:
[  204.006488] In process "swapper/0" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode
[  207.656116] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[  207.656126] rtl8192ee:
[  207.656130] In process "kworker/0:0" (pid 4):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode
[  209.155335] rtlwifi-0:rtl_tx_agg_stop():<0-0> on ra = <MAC address removed> tid = 0
[  209.155374] rtlwifi-0:rtl_action_proc():<400-1> ACT_ADDBADEL From :<MAC address removed>
[  211.758180] rtlwifi-0:rtl_tx_agg_start():<0-0> on ra = <MAC address removed> tid = 0 seq:1164
[  211.758201] rtlwifi-0:rtl_action_proc():<200-1> Tx ACT_ADDBAREQ From :<MAC address removed>
[  211.758204] rtlwifi:
[  211.764437] rtlwifi-0:rtl_action_proc():<10000-1> Rx ACT_ADDBARSP From :<MAC address removed>
[  211.764803] rtlwifi-0:rtl_tx_agg_oper():<0-0> on ra = <MAC address removed> tid = 0
[  211.787381] rtlwifi-0:rtl_lps_set_psmode():<10000-1> FW LPS leave ps_mode:0
[  211.787728] rtl8192ee:
[  211.787730] In process "swapper/0" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode
[  225.682091] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[  225.682101] rtl8192ee:
[  225.682104] In process "kworker/0:0" (pid 4):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode
[  227.993170] rtlwifi-0:rtl_lps_set_psmode():<500-1> FW LPS leave ps_mode:0
[  227.993525] rtl8192ee:
[  227.993528] In process "swapper/0" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode
[  234.717067] rtlwifi-0:rtl_tx_agg_start():<0-0> on ra = <MAC address removed> tid = 1 seq:9
[  234.717134] rtlwifi-0:rtl_action_proc():<200-1> Tx ACT_ADDBAREQ From :<MAC address removed>
[  234.717140] rtlwifi:
[  234.721138] rtlwifi-0:rtl_action_proc():<10000-1> Rx ACT_ADDBARSP From :<MAC address removed>
[  234.721562] rtlwifi-0:rtl_tx_agg_oper():<0-0> on ra = <MAC address removed> tid = 1
[  240.086010] rtlwifi-0:rtl_tx_agg_stop():<0-0> on ra = <MAC address removed> tid = 1
[  240.086027] rtlwifi-0:rtl_action_proc():<400-1> ACT_ADDBADEL From :<MAC address removed>
[  249.717482] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[  249.717491] rtl8192ee:
[  249.717494] In process "kworker/0:0" (pid 4):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode
[  249.950545] rtlwifi-0:rtl_lps_set_psmode():<10000-1> FW LPS leave ps_mode:0
[  249.950898] rtl8192ee:
[  249.950902] In process "swapper/0" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode
[  253.722496] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[  253.722506] rtl8192ee:
[  253.722509] In process "kworker/0:0" (pid 4):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode
[  259.420544] rtlwifi-0:rtl_lps_set_psmode():<10000-1> FW LPS leave ps_mode:0
[  259.420901] rtl8192ee:
[  259.420905] In process "swapper/0" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode
[  263.736863] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[  263.736874] rtl8192ee:
[  263.736877] In process "kworker/0:0" (pid 4):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode
[  266.371471] rtlwifi-0:rtl_tx_agg_stop():<0-0> on ra = <MAC address removed> tid = 0
[  266.371497] rtlwifi-0:rtl_action_proc():<400-1> ACT_ADDBADEL From :<MAC address removed>
[  268.170524] rtlwifi-0:rtl_tx_agg_start():<0-0> on ra = <MAC address removed> tid = 0 seq:2026
[  268.170559] rtlwifi-0:rtl_action_proc():<200-1> Tx ACT_ADDBAREQ From :<MAC address removed>
[  268.170564] rtlwifi:
[  268.173142] rtlwifi-0:rtl_action_proc():<10000-1> Rx ACT_ADDBARSP From :<MAC address removed>
[  268.173571] rtlwifi-0:rtl_tx_agg_oper():<0-0> on ra = <MAC address removed> tid = 0
[  268.902878] rtlwifi-0:rtl_lps_set_psmode():<10000-1> FW LPS leave ps_mode:0
[  268.903233] rtl8192ee:
[  268.903235] In process "unity-scope-hom" (pid 2580):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode
[  287.771494] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[  287.771506] rtl8192ee:
[  287.771511] In process "kworker/0:0" (pid 4):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode
[  288.837333] rtlwifi-0:rtl_lps_set_psmode():<10000-1> FW LPS leave ps_mode:0
[  288.837692] rtl8192ee:
[  288.837695] In process "swapper/0" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode
[  291.777343] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[  291.777354] rtl8192ee:
[  291.777358] In process "kworker/0:0" (pid 4):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode
[  299.756956] rtlwifi-0:rtl_tx_agg_stop():<0-0> on ra = <MAC address removed> tid = 0
[  299.756998] rtlwifi-0:rtl_action_proc():<400-1> ACT_ADDBADEL From :<MAC address removed>
[  302.031688] rtlwifi-0:rtl_tx_agg_start():<0-0> on ra = <MAC address removed> tid = 0 seq:2339
[  302.031733] rtlwifi-0:rtl_action_proc():<200-1> Tx ACT_ADDBAREQ From :<MAC address removed>
[  302.031738] rtlwifi:
[  302.040154] rtlwifi-0:rtl_action_proc():<10000-1> Rx ACT_ADDBARSP From :<MAC address removed>
[  302.040612] rtlwifi-0:rtl_tx_agg_oper():<0-0> on ra = <MAC address removed> tid = 0
[  311.234437] rtlwifi-0:rtl_tx_agg_stop():<0-0> on ra = <MAC address removed> tid = 0
[  311.234466] rtlwifi-0:rtl_action_proc():<400-1> ACT_ADDBADEL From :<MAC address removed>
[  311.926127] rtlwifi-0:rtl_tx_agg_start():<0-0> on ra = <MAC address removed> tid = 0 seq:2348
[  311.926159] rtlwifi-0:rtl_action_proc():<200-1> Tx ACT_ADDBAREQ From :<MAC address removed>
[  311.926163] rtlwifi:
[  311.928704] rtlwifi-0:rtl_action_proc():<10000-1> Rx ACT_ADDBARSP From :<MAC address removed>
[  311.929089] rtlwifi-0:rtl_tx_agg_oper():<0-0> on ra = <MAC address removed> tid = 0
[  321.924143] rtlwifi-0:rtl_lps_set_psmode():<500-1> FW LPS leave ps_mode:0
[  321.924157] rtl8192ee:
[  321.924160] In process "swapper/0" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode
[  333.050451] rtlwifi-0:rtl_tx_agg_stop():<0-0> on ra = <MAC address removed> tid = 0
[  337.295729] rtlwifi-0:rtl_action_proc():<400-1> ACT_ADDBADEL From :<MAC address removed>
[  337.311934] rtlwifi-0:rtl_tx_agg_start():<0-0> on ra = <MAC address removed> tid = 0 seq:2550
[  337.311947] rtlwifi-0:rtl_action_proc():<200-1> Tx ACT_ADDBAREQ From :<MAC address removed>
[  337.311949] rtlwifi:
[  337.315256] rtlwifi-0:rtl_action_proc():<10000-1> Rx ACT_ADDBARSP From :<MAC address removed>
[  337.315477] rtlwifi-0:rtl_tx_agg_oper():<0-0> on ra = <MAC address removed> tid = 0
[  364.692710] rtlwifi-0:rtl_tx_agg_stop():<0-0> on ra = <MAC address removed> tid = 0
[  364.692732] rtlwifi-0:rtl_action_proc():<400-1> ACT_ADDBADEL From :<MAC address removed>
[  365.884068] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[  365.884077] rtl8192ee:
[  365.884080] In process "kworker/0:0" (pid 4):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode
[  368.114875] rtlwifi-0:rtl_tx_agg_start():<0-0> on ra = <MAC address removed> tid = 0 seq:3427
[  368.114904] rtlwifi-0:rtl_action_proc():<200-1> Tx ACT_ADDBAREQ From :<MAC address removed>
[  368.114909] rtlwifi:
[  368.117653] rtlwifi-0:rtl_action_proc():<10000-1> Rx ACT_ADDBARSP From :<MAC address removed>
[  368.118076] rtlwifi-0:rtl_tx_agg_oper():<0-0> on ra = <MAC address removed> tid = 0
[  376.022548] rtlwifi-0:rtl_tx_agg_stop():<0-0> on ra = <MAC address removed> tid = 0
[  376.022594] rtlwifi-0:rtl_action_proc():<400-1> ACT_ADDBADEL From :<MAC address removed>
[  379.117396] rtlwifi-0:rtl_tx_agg_start():<0-0> on ra = <MAC address removed> tid = 0 seq:3429
[  379.117425] rtlwifi-0:rtl_action_proc():<200-1> Tx ACT_ADDBAREQ From :<MAC address removed>
[  379.117429] rtlwifi:
[  379.121452] rtlwifi-0:rtl_action_proc():<10100-1> Rx ACT_ADDBARSP From :<MAC address removed>
[  379.121901] rtlwifi-0:rtl_tx_agg_oper():<0-0> on ra = <MAC address removed> tid = 0
[  379.300905] rtlwifi-0:rtl_lps_set_psmode():<10000-1> FW LPS leave ps_mode:0
[  379.300922] rtl8192ee:
[  379.300926] In process "swapper/0" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode
[  391.921637] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[  391.921648] rtl8192ee:
[  391.921651] In process "kworker/0:0" (pid 4):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode
[  393.825953] rtlwifi-0:rtl_lps_set_psmode():<10000-1> FW LPS leave ps_mode:0
[  393.825967] rtl8192ee:
[  393.825970] In process "swapper/0" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode
[  401.936079] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[  401.936089] rtl8192ee:
[  401.936093] In process "kworker/0:0" (pid 4):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode
[  411.490820] rtlwifi-0:rtl_tx_agg_stop():<0-0> on ra = <MAC address removed> tid = 0
[  411.490863] rtlwifi-0:rtl_action_proc():<400-1> ACT_ADDBADEL From :<MAC address removed>
[  413.177881] rtlwifi-0:rtl_tx_agg_start():<0-0> on ra = <MAC address removed> tid = 0 seq:3961
[  413.177923] rtlwifi-0:rtl_action_proc():<200-1> Tx ACT_ADDBAREQ From :<MAC address removed>
[  413.177928] rtlwifi:
[  413.183616] rtlwifi-0:rtl_action_proc():<10000-1> Rx ACT_ADDBARSP From :<MAC address removed>
[  413.184100] rtlwifi-0:rtl_tx_agg_oper():<0-0> on ra = <MAC address removed> tid = 0
[  413.454579] rtlwifi-0:rtl_lps_set_psmode():<500-1> FW LPS leave ps_mode:0
[  413.454935] rtl8192ee:
[  413.454938] In process "swapper/0" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode
[  415.956280] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[  415.956290] rtl8192ee:
[  415.956293] In process "kworker/0:0" (pid 4):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode
[  421.693439] rtlwifi-0:rtl_lps_set_psmode():<300-1> FW LPS leave ps_mode:0
[  421.693793] rtl8192ee:
[  421.693797] In process "ksoftirqd/0" (pid 3):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode
[  423.967820] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[  423.967833] rtl8192ee:
[  423.967836] In process "kworker/0:0" (pid 4):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode
[  427.477912] rtlwifi-0:rtl_tx_agg_stop():<0-0> on ra = <MAC address removed> tid = 0
[  427.477959] rtlwifi-0:rtl_action_proc():<400-1> ACT_ADDBADEL From :<MAC address removed>
[  427.761694] rtlwifi-0:rtl_tx_agg_start():<0-0> on ra = <MAC address removed> tid = 0 seq:3965
[  427.761725] rtlwifi-0:rtl_action_proc():<200-1> Tx ACT_ADDBAREQ From :<MAC address removed>
[  427.761730] rtlwifi:
[  427.763961] rtlwifi-0:rtl_action_proc():<10000-1> Rx ACT_ADDBARSP From :<MAC address removed>
[  427.764387] rtlwifi-0:rtl_tx_agg_oper():<0-0> on ra = <MAC address removed> tid = 0
[  432.894875] rtlwifi-0:rtl_tx_agg_stop():<0-0> on ra = <MAC address removed> tid = 0
[  432.894913] rtlwifi-0:rtl_action_proc():<400-1> ACT_ADDBADEL From :<MAC address removed>
[  437.240493] rtlwifi-0:rtl_tx_agg_start():<0-0> on ra = <MAC address removed> tid = 0 seq:3966
[  437.240532] rtlwifi-0:rtl_action_proc():<200-1> Tx ACT_ADDBAREQ From :<MAC address removed>
[  437.240537] rtlwifi:
[  437.243534] rtlwifi-0:rtl_action_proc():<10000-1> Rx ACT_ADDBARSP From :<MAC address removed>
[  437.243959] rtlwifi-0:rtl_tx_agg_oper():<0-0> on ra = <MAC address removed> tid = 0
[  439.541544] rtlwifi-0:rtl_lps_set_psmode():<10000-1> FW LPS leave ps_mode:0
[  439.541904] rtl8192ee:
[  439.541908] In process "swapper/0" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode
[  443.996671] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[  443.996681] rtl8192ee:
[  443.996685] In process "kworker/0:0" (pid 4):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode
[  446.063857] rtlwifi-0:rtl_lps_set_psmode():<300-1> FW LPS leave ps_mode:0
[  446.064213] rtl8192ee:
[  446.064217] In process "swapper/0" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode
[  465.460797] rtlwifi-0:rtl_tx_agg_stop():<0-0> on ra = <MAC address removed> tid = 0
[  465.460850] rtlwifi-0:rtl_action_proc():<400-1> ACT_ADDBADEL From :<MAC address removed>
[  467.671563] rtlwifi-0:rtl_tx_agg_start():<0-0> on ra = <MAC address removed> tid = 0 seq:3987
[  467.671612] rtlwifi-0:rtl_action_proc():<200-1> Tx ACT_ADDBAREQ From :<MAC address removed>
[  467.671620] rtlwifi:
[  467.676433] rtlwifi-0:rtl_action_proc():<10000-1> Rx ACT_ADDBARSP From :<MAC address removed>
[  467.677068] rtlwifi-0:rtl_tx_agg_oper():<0-0> on ra = <MAC address removed> tid = 0
[  476.042814] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[  476.042823] rtl8192ee:
[  476.042826] In process "kworker/0:0" (pid 4):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode
[  477.953784] rtlwifi-0:rtl_tx_agg_stop():<0-0> on ra = <MAC address removed> tid = 0
[  477.953822] rtlwifi-0:rtl_action_proc():<400-1> ACT_ADDBADEL From :<MAC address removed>
[  479.828805] rtlwifi-0:rtl_tx_agg_start():<0-0> on ra = <MAC address removed> tid = 0 seq:3991
[  479.828834] rtlwifi-0:rtl_action_proc():<200-1> Tx ACT_ADDBAREQ From :<MAC address removed>
[  479.828839] rtlwifi:
[  479.839963] rtlwifi-0:rtl_action_proc():<10000-1> Rx ACT_ADDBARSP From :<MAC address removed>
[  479.840593] rtlwifi-0:rtl_tx_agg_oper():<0-0> on ra = <MAC address removed> tid = 0
[  483.716176] rtlwifi-0:rtl_lps_set_psmode():<10000-1> FW LPS leave ps_mode:0
[  483.716537] rtl8192ee:
[  483.716541] In process "swapper/0" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode
[  491.446372] rtlwifi-0:rtl_tx_agg_stop():<0-0> on ra = <MAC address removed> tid = 0
[  491.446414] rtlwifi-0:rtl_action_proc():<400-1> ACT_ADDBADEL From :<MAC address removed>
[  492.065877] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[  492.065886] rtl8192ee:
[  492.065890] In process "kworker/0:0" (pid 4):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode
[  493.067018] rtlwifi-0:rtl_lps_set_psmode():<10000-1> FW LPS leave ps_mode:0
[  493.067369] rtl8192ee:
[  493.067372] In process "swapper/0" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode
[  493.517188] rtlwifi-0:rtl_tx_agg_start():<0-0> on ra = <MAC address removed> tid = 0 seq:4001
[  493.517228] rtlwifi-0:rtl_action_proc():<200-1> Tx ACT_ADDBAREQ From :<MAC address removed>
[  493.517233] rtlwifi:
[  493.526040] rtlwifi-0:rtl_action_proc():<10000-1> Rx ACT_ADDBARSP From :<MAC address removed>
[  493.526501] rtlwifi-0:rtl_tx_agg_oper():<0-0> on ra = <MAC address removed> tid = 0
[  496.071716] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[  496.071728] rtl8192ee:
[  496.071738] In process "kworker/0:0" (pid 4):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode
[  498.890166] rtlwifi-0:rtl_tx_agg_stop():<0-0> on ra = <MAC address removed> tid = 0
[  498.890199] rtlwifi-0:rtl_action_proc():<400-1> ACT_ADDBADEL From :<MAC address removed>
[  503.239791] rtlwifi-0:rtl_tx_agg_start():<0-0> on ra = <MAC address removed> tid = 0 seq:4003
[  503.239828] rtlwifi-0:rtl_action_proc():<200-1> Tx ACT_ADDBAREQ From :<MAC address removed>
[  503.239834] rtlwifi:
[  503.248419] rtlwifi-0:rtl_action_proc():<10100-1> Rx ACT_ADDBARSP From :<MAC address removed>
[  503.249431] rtlwifi-0:rtl_tx_agg_oper():<0-0> on ra = <MAC address removed> tid = 0
[  508.237283] rtlwifi-0:rtl_lps_set_psmode():<300-1> FW LPS leave ps_mode:0
[  508.237302] rtl8192ee:
[  508.237306] In process "swapper/1" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode
[  524.112086] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[  524.112096] rtl8192ee:
[  524.112100] In process "kworker/0:0" (pid 4):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode
[  525.267797] rtlwifi-0:rtl_lps_set_psmode():<10000-1> FW LPS leave ps_mode:0
[  525.268151] rtl8192ee:
[  525.268155] In process "swapper/0" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode
[  530.120707] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[  530.120712] rtl8192ee:
[  530.120714] In process "kworker/0:0" (pid 4):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode
[  533.327277] rtlwifi-0:rtl_lps_set_psmode():<300-1> FW LPS leave ps_mode:0
[  533.327467] rtl8192ee:
[  533.327469] In process "swapper/3" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode
[  536.129371] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[  536.129381] rtl8192ee:
[  536.129384] In process "kworker/0:0" (pid 4):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode
[  538.821406] rtlwifi-0:rtl_lps_set_psmode():<10000-1> FW LPS leave ps_mode:0
[  538.821759] rtl8192ee:
[  538.821762] In process "swapper/0" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode
[  546.143841] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[  546.143852] rtl8192ee:
[  546.143855] In process "kworker/0:0" (pid 4):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode
[  556.693931] rtlwifi-0:rtl_tx_agg_stop():<0-0> on ra = <MAC address removed> tid = 0
[  556.693953] rtlwifi-0:rtl_action_proc():<400-1> ACT_ADDBADEL From :<MAC address removed>
[  557.321639] rtlwifi-0:rtl_tx_agg_start():<0-0> on ra = <MAC address removed> tid = 0 seq:4
[  557.321670] rtlwifi-0:rtl_action_proc():<200-1> Tx ACT_ADDBAREQ From :<MAC address removed>
[  557.321675] rtlwifi:
[  558.325144] rtlwifi-0:rtl_tx_agg_stop():<0-0> on ra = <MAC address removed> tid = 0
[  558.325200] rtlwifi-0:rtl_action_proc():<400-1> ACT_ADDBADEL From :<MAC address removed>
[  558.337111] rtlwifi-0:rtl_tx_agg_start():<0-0> on ra = <MAC address removed> tid = 0 seq:5
[  558.337138] rtlwifi-0:rtl_action_proc():<200-1> Tx ACT_ADDBAREQ From :<MAC address removed>
[  558.337144] rtlwifi:
[  558.341069] rtlwifi-0:rtl_action_proc():<10100-1> Rx ACT_ADDBARSP From :<MAC address removed>
[  558.341730] rtlwifi-0:rtl_tx_agg_oper():<0-0> on ra = <MAC address removed> tid = 0
[  562.319206] rtlwifi-0:rtl_lps_set_psmode():<300-1> FW LPS leave ps_mode:0
[  562.319561] rtl8192ee:
[  562.319564] In process "swapper/0" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode
[  566.172724] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[  566.172734] rtl8192ee:
[  566.172738] In process "kworker/0:0" (pid 4):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode
[  572.013622] rtlwifi-0:rtl_lps_set_psmode():<10000-1> FW LPS leave ps_mode:0
[  572.013976] rtl8192ee:
[  572.013979] In process "compiz" (pid 2257):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode
[  584.198688] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[  584.198698] rtl8192ee:
[  584.198702] In process "kworker/0:0" (pid 4):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode
[  587.872991] rtlwifi-0:rtl_lps_set_psmode():<300-1> FW LPS leave ps_mode:0
[  587.873346] rtl8192ee:
[  587.873349] In process "swapper/0" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode
[  592.210233] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[  592.210243] rtl8192ee:
[  592.210247] In process "kworker/0:0" (pid 4):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode
[  593.013788] rtlwifi-0:rtl_tx_agg_stop():<0-0> on ra = <MAC address removed> tid = 0
[  593.013856] rtlwifi-0:rtl_action_proc():<400-1> ACT_ADDBADEL From :<MAC address removed>
[  593.301699] rtlwifi-0:rtl_tx_agg_start():<0-0> on ra = <MAC address removed> tid = 0 seq:32
[  593.301734] rtlwifi-0:rtl_action_proc():<200-1> Tx ACT_ADDBAREQ From :<MAC address removed>
[  593.301739] rtlwifi:
[  593.310309] rtlwifi-0:rtl_action_proc():<10000-1> Rx ACT_ADDBARSP From :<MAC address removed>
[  593.310544] rtlwifi-0:rtl_tx_agg_oper():<0-0> on ra = <MAC address removed> tid = 0
[  601.640983] rtlwifi-0:rtl_tx_agg_stop():<0-0> on ra = <MAC address removed> tid = 0
[  601.641019] rtlwifi-0:rtl_action_proc():<400-1> ACT_ADDBADEL From :<MAC address removed>
[  606.478366] rtlwifi-0:rtl_tx_agg_start():<0-0> on ra = <MAC address removed> tid = 0 seq:37
[  606.478402] rtlwifi-0:rtl_action_proc():<200-1> Tx ACT_ADDBAREQ From :<MAC address removed>
[  606.478407] rtlwifi:
[  607.485728] rtlwifi-0:rtl_tx_agg_stop():<0-0> on ra = <MAC address removed> tid = 0
[  607.485772] rtlwifi-0:rtl_action_proc():<400-1> ACT_ADDBADEL From :<MAC address removed>
[  607.885572] rtlwifi-0:rtl_tx_agg_start():<0-0> on ra = <MAC address removed> tid = 0 seq:38
[  607.885609] rtlwifi-0:rtl_action_proc():<200-1> Tx ACT_ADDBAREQ From :<MAC address removed>
[  607.885614] rtlwifi:
[  607.892529] rtlwifi-0:rtl_action_proc():<10000-1> Rx ACT_ADDBARSP From :<MAC address removed>
[  607.892960] rtlwifi-0:rtl_tx_agg_oper():<0-0> on ra = <MAC address removed> tid = 0
[  611.261024] rtlwifi-0:rtl_lps_set_psmode():<10000-1> FW LPS leave ps_mode:0
[  611.261377] rtl8192ee:
[  611.261380] In process "swapper/0" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode
[  618.247730] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[  618.247740] rtl8192ee:
[  618.247744] In process "kworker/0:0" (pid 4):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode
[  619.024815] rtlwifi-0:rtl_lps_set_psmode():<10000-1> FW LPS leave ps_mode:0
[  619.025175] rtl8192ee:
[  619.025179] In process "compiz" (pid 2257):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode
[  634.270856] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[  634.270873] rtl8192ee:
[  634.270882] In process "kworker/0:0" (pid 4):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode
[  637.045831] rtlwifi-0:rtl_lps_set_psmode():<10000-1> FW LPS leave ps_mode:0
[  637.046188] rtl8192ee:
[  637.046191] In process "swapper/0" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode
[  650.293875] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[  650.293885] rtl8192ee:
[  650.293888] In process "kworker/0:0" (pid 4):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode
[  652.924098] rtlwifi-0:rtl_lps_set_psmode():<10000-1> FW LPS leave ps_mode:0
[  652.924453] rtl8192ee:
[  652.924457] In process "swapper/0" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode
[  662.311176] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[  662.311185] rtl8192ee:
[  662.311188] In process "kworker/0:0" (pid 4):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode
[  662.501646] rtlwifi-0:rtl_lps_set_psmode():<10000-1> FW LPS leave ps_mode:0
[  662.502009] rtl8192ee:
[  662.502012] In process "swapper/0" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode
[  670.322730] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[  670.322736] rtl8192ee:
[  670.322738] In process "kworker/0:0" (pid 4):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode
[  670.459762] wlan1: deauthenticating from <MAC address removed> by local choice (reason=3)
[  670.460196] rtlwifi-0:rtl_tx_agg_stop():<0-0> on ra = <MAC address removed> tid = 0
[  670.460209] rtlwifi-0:rtl_rx_agg_stop():<0-0> on ra = <MAC address removed> tid = 0
[  670.460225] rtlwifi-0:rtl_rx_agg_stop():<0-0> on ra = <MAC address removed> tid = 1
[  670.460256] rtlwifi-0:rtl_op_set_key():<0-0> Disabling hardware based encryption for keyidx: 0, mac: <MAC address removed>
[  670.460265] rtlwifi-0:rtl_op_set_key():<0-0> alg:CCMP
[  670.460271] rtlwifi-0:rtl_op_set_key():<0-0> set enable_hw_sec, key_type:4(OPEN:0 WEP40:1 TKIP:2 AES:4 WEP104:5)
[  670.460278] rtl8192ee-0:rtl92ee_enable_hw_security_config():<0-0> PairwiseEncAlgorithm = 4 GroupEncAlgorithm = 4
[  670.460635] rtl8192ee-0:rtl92ee_enable_hw_security_config():<0-0> The SECR-value cc
[  670.460824] rtlwifi-0:rtl_op_set_key():<0-0> disable key delete one entry
[  670.460831] rtlwifi-0:rtl_cam_delete_one_entry():<0-0> key_idx:0
[  670.461025] rtlwifi-0:rtl_cam_delete_one_entry():<0-0> rtl_cam_delete_one_entry(): WRITE A4: 0
[  670.461031] rtlwifi-0:rtl_cam_delete_one_entry():<0-0> rtl_cam_delete_one_entry(): WRITE A0: 80010000
[  670.461115] rtlwifi-0:rtl_op_sta_remove():<0-0> Remove sta addr is <MAC address removed>
[  670.461594] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS leave ps_mode:0
[  670.461925] rtl8192ee:
[  670.461930] In process "wpa_supplicant" (pid 1077):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode
[  670.462160] rtlwifi-0:rtl_op_bss_info_changed():<0-0> BSS_CHANGED_UN_ASSOC
[  670.462512] rtl8192ee-0:rtl92ee_set_hw_reg():<0-0> switch case not process 1c
[  670.463071] rtl8192ee-0:rtl92ee_set_hw_reg():<0-0> switch case not process 1b
[  670.463428] rtlwifi-0:rtl_op_bss_info_changed():<0-0> bssid: <MAC address removed>
[  670.483829] rtlwifi-0:rtl_op_set_key():<0-0> Disabling hardware based encryption for keyidx: 2, mac: <MAC address removed>
[  670.483844] rtlwifi-0:rtl_op_set_key():<0-0> alg:CCMP
[  670.483846] rtlwifi-0:rtl_op_set_key():<0-0> disable key delete one entry
[  670.483849] rtlwifi-0:rtl_cam_delete_one_entry():<0-0> key_idx:2
[  670.484199] rtlwifi-0:rtl_cam_delete_one_entry():<0-0> rtl_cam_delete_one_entry(): WRITE A4: 0
[  670.484201] rtlwifi-0:rtl_cam_delete_one_entry():<0-0> rtl_cam_delete_one_entry(): WRITE A0: 80010010
[  671.556493] wlan1: authenticate with <MAC address removed>
[  671.594737] rtlwifi-0:rtl_op_bss_info_changed():<0-0> bssid: <MAC address removed>
[  671.595149] wlan1: send auth to <MAC address removed> (try 1/3)
[  671.595159] rtlwifi-0:rtl_tx_mgmt_proc():<200-1> MAC80211_LINKING
[  671.602448] wlan1: authenticated
[  671.606000] wlan1: associate with <MAC address removed> (try 1/3)
[  671.611034] wlan1: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=1)
[  671.611043] rtlwifi-0:rtl_op_sta_add():<0-0> Add sta addr is <MAC address removed>
[  671.611047] rtl8192ee-0:rtl92ee_update_hal_rate_mask():<0-0> ratr_bitmap :ffff005
[  671.611049] rtl8192ee-0:rtl92ee_update_hal_rate_mask():<0-0> Rate_index:2, ratr_val:ffff005, 0:82:0:5:f0:ff:f
[  671.611427] rtl8192ee-0:rtl92ee_update_hal_rate_mask():<0-0> ratr_bitmap :ffff005
[  671.611429] rtl8192ee-0:rtl92ee_update_hal_rate_mask():<0-0> Rate_index:2, ratr_val:ffff005, 0:82:0:5:f0:ff:f
[  671.611795] rtlwifi-0:rtl_op_bss_info_changed():<0-0> BSS_CHANGED_ASSOC
[  671.611813] rtl8192ee-0:rtl92ee_set_hw_reg():<0-0> switch case not process 5b
[  671.611834] rtl8192ee:
[  671.611836] In process "kworker/u16:4" (pid 155):rtl92ee_set_fw_rsvdpagepkt(): HW_VAR_SET_TX_CMD: ALL
[  671.611844] rtl8192ee:
[  671.613377] rtlwifi-0:rtl_action_proc():<10000-1> Rx ACT_ADDBAREQ From :<MAC address removed>
[  671.613381] rtlwifi:
[  671.619988] rtl8192ee:
[  671.619991] In process "kworker/u16:4" (pid 155):rtl92ee_set_fw_rsvdpagepkt(): HW_VAR_SET_TX_CMD: ALL
[  671.620003] rtl8192ee:
[  671.628183] rtl8192ee:
[  671.628187] In process "kworker/u16:4" (pid 155):rtl92ee_set_fw_rsvdpagepkt(): HW_VAR_SET_TX_CMD: ALL
[  671.628195] rtl8192ee:
[  671.636407] rtl8192ee:
[  671.636410] In process "kworker/u16:4" (pid 155):rtl92ee_set_fw_rsvdpagepkt(): HW_VAR_SET_TX_CMD: ALL
[  671.636417] rtl8192ee:
[  671.644701] rtl8192ee:
[  671.644702] In process "kworker/u16:4" (pid 155):rtl92ee_set_fw_rsvdpagepkt(): HW_VAR_SET_TX_CMD: ALL
[  671.644709] rtl8192ee:
[  671.653179] wlan1: associated
[  671.653199] rtlwifi-0:rtl_rx_agg_start():<0-0> on ra = <MAC address removed> tid = 0 seq:0
[  671.653209] rtlwifi-0:rtl_action_proc():<200-1> Tx ACT_ADDBARSP From :<MAC address removed>
[  671.657333] rtlwifi-0:rtl_is_special_data():<10000-1> 802.1X Rx EAPOL pkt!!
[  671.658546] rtlwifi-0:rtl_is_special_data():<200-1> 802.1X Tx EAPOL pkt!!
[  671.658941] rtlwifi-0:rtl_is_special_data():<100-1> 802.1X Tx EAPOL pkt!!
[  671.668710] rtlwifi-0:rtl_is_special_data():<10000-1> 802.1X Rx EAPOL pkt!!
[  671.669155] rtlwifi-0:rtl_is_special_data():<200-1> 802.1X Tx EAPOL pkt!!
[  671.669559] rtlwifi-0:rtl_is_special_data():<100-1> 802.1X Tx EAPOL pkt!!
[  671.669622] rtlwifi-0:rtl_op_set_key():<0-0> Using hardware based encryption for keyidx: 0, mac: <MAC address removed>
[  671.669624] rtlwifi-0:rtl_op_set_key():<0-0> alg:CCMP
[  671.669626] rtlwifi-0:rtl_op_set_key():<0-0> set enable_hw_sec, key_type:4(OPEN:0 WEP40:1 TKIP:2 AES:4 WEP104:5)
[  671.669627] rtl8192ee-0:rtl92ee_enable_hw_security_config():<0-0> PairwiseEncAlgorithm = 4 GroupEncAlgorithm = 0
[  671.670340] rtl8192ee-0:rtl92ee_enable_hw_security_config():<0-0> The SECR-value cc
[  671.670345] rtlwifi-0:rtl_op_set_key():<0-0> set pairwise key
[  671.670348] rtl8192ee-0:rtl92ee_set_key():<0-0> add one entry
[  671.670350] rtl8192ee-0:rtl92ee_set_key():<0-0> set Pairwiase key
[  671.670352] rtlwifi-0:rtl_cam_add_one_entry():<0-0> EntryNo:4, ulKeyId=0, ulEncAlg=4, ulUseDK=0 MacAddr <MAC address removed>
[  671.670354] rtlwifi:
[  671.673205] rtlwifi-0:rtl_cam_add_one_entry():<0-0> end
[  671.673308] rtlwifi-0:rtl_op_set_key():<0-0> Using hardware based encryption for keyidx: 2, mac: <MAC address removed>
[  671.673311] rtlwifi-0:rtl_op_set_key():<0-0> alg:CCMP
[  671.673312] rtlwifi-0:rtl_op_set_key():<0-0> set group key
[  671.673314] rtl8192ee-0:rtl92ee_set_key():<0-0> add one entry
[  671.673316] rtl8192ee-0:rtl92ee_set_key():<0-0> set group key
[  671.673318] rtlwifi-0:rtl_cam_add_one_entry():<0-0> EntryNo:2, ulKeyId=2, ulEncAlg=4, ulUseDK=0 MacAddr <MAC address removed>
[  671.673319] rtlwifi:
[  671.676378] rtlwifi-0:rtl_cam_add_one_entry():<0-0> end
[  671.734096] rtlwifi-0:rtl_is_special_data():<200-1> dhcp Tx !!
[  675.019487] rtlwifi-0:rtl_is_special_data():<200-1> dhcp Tx !!
[  676.460152] rtlwifi-0:rtl_action_proc():<10000-1> Rx ACT_ADDBAREQ From :<MAC address removed>
[  676.460162] rtlwifi:
[  676.460650] rtlwifi-0:rtl_rx_agg_start():<0-0> on ra = <MAC address removed> tid = 1 seq:0
[  676.460671] rtlwifi-0:rtl_action_proc():<200-1> Tx ACT_ADDBARSP From :<MAC address removed>
[  676.523400] rtlwifi-0:rtl_tx_agg_start():<0-0> on ra = <MAC address removed> tid = 0 seq:37
[  676.523428] rtlwifi-0:rtl_action_proc():<200-1> Tx ACT_ADDBAREQ From :<MAC address removed>
[  676.523432] rtlwifi:
[  676.525648] rtlwifi-0:rtl_action_proc():<10000-1> Rx ACT_ADDBARSP From :<MAC address removed>
[  676.525945] rtlwifi-0:rtl_tx_agg_oper():<0-0> on ra = <MAC address removed> tid = 0
[  703.383748] rtlwifi-0:rtl_action_proc():<10000-1> ACT_ADDBADEL From :<MAC address removed>
[  703.386963] rtlwifi-0:rtl_action_proc():<10000-1> ACT_ADDBADEL From :<MAC address removed>
[  705.831287] rtlwifi-0:rtl_rx_agg_stop():<0-0> on ra = <MAC address removed> tid = 1
[  706.203200] rtlwifi-0:rtl_action_proc():<10000-1> Rx ACT_ADDBAREQ From :<MAC address removed>
[  706.203207] rtlwifi:
[  706.203642] rtlwifi-0:rtl_rx_agg_start():<0-0> on ra = <MAC address removed> tid = 1 seq:0
[  706.203655] rtlwifi-0:rtl_action_proc():<200-1> Tx ACT_ADDBARSP From :<MAC address removed>
[  743.845171] rtlwifi-0:_rtl_pci_interrupt():<10000-1> rx overflow !
[  808.498061] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[  808.498072] rtl8192ee:
[  808.498075] In process "kworker/0:0" (pid 4):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode
[  808.713916] rtlwifi-0:rtl_tx_agg_stop():<0-0> on ra = <MAC address removed> tid = 0
[  808.713954] rtlwifi-0:rtl_action_proc():<400-1> ACT_ADDBADEL From :<MAC address removed>
[  812.051308] rtlwifi-0:rtl_lps_set_psmode():<10000-1> FW LPS leave ps_mode:0
[  812.051658] rtl8192ee:
[  812.051662] In process "swapper/0" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode
[  812.164076] rtlwifi-0:rtl_tx_agg_start():<0-0> on ra = <MAC address removed> tid = 0 seq:1297
[  812.164109] rtlwifi-0:rtl_action_proc():<200-1> Tx ACT_ADDBAREQ From :<MAC address removed>
[  812.164114] rtlwifi:
[  812.166539] rtlwifi-0:rtl_action_proc():<10000-1> Rx ACT_ADDBARSP From :<MAC address removed>
[  812.166802] rtlwifi-0:rtl_tx_agg_oper():<0-0> on ra = <MAC address removed> tid = 0
[  816.509597] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[  816.509607] rtl8192ee:
[  816.509610] In process "kworker/0:0" (pid 4):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode
[  817.161499] rtlwifi-0:rtl_lps_set_psmode():<300-1> FW LPS leave ps_mode:0
[  817.161689] rtl8192ee:
[  817.161691] In process "swapper/0" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode
[  820.515345] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[  820.515350] rtl8192ee:
[  820.515352] In process "kworker/0:0" (pid 4):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode
[  821.341849] rtlwifi-0:rtl_lps_set_psmode():<10000-1> FW LPS leave ps_mode:0
[  821.342198] rtl8192ee:
[  821.342199] In process "compiz" (pid 2257):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode
[  836.538401] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[  836.538411] rtl8192ee:
[  836.538414] In process "kworker/0:0" (pid 4):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode
[  838.013706] rtlwifi-0:rtl_tx_agg_stop():<0-0> on ra = <MAC address removed> tid = 0
[  838.013750] rtlwifi-0:rtl_action_proc():<400-1> ACT_ADDBADEL From :<MAC address removed>
[  839.268941] rtlwifi-0:rtl_tx_agg_start():<0-0> on ra = <MAC address removed> tid = 0 seq:1365
[  839.268971] rtlwifi-0:rtl_action_proc():<200-1> Tx ACT_ADDBAREQ From :<MAC address removed>
[  839.268975] rtlwifi:
[  839.272069] rtlwifi-0:rtl_action_proc():<10100-1> Rx ACT_ADDBARSP From :<MAC address removed>
[  839.272478] rtlwifi-0:rtl_tx_agg_oper():<0-0> on ra = <MAC address removed> tid = 0
[  839.755753] rtlwifi-0:rtl_lps_set_psmode():<10000-1> FW LPS leave ps_mode:0
[  839.756106] rtl8192ee:
[  839.756109] In process "swapper/0" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode
[  844.549900] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[  844.549904] rtl8192ee:
[  844.549905] In process "kworker/0:0" (pid 4):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode
[  846.337234] rtlwifi-0:rtl_lps_set_psmode():<10000-1> FW LPS leave ps_mode:0
[  846.337251] rtl8192ee:
[  846.337256] In process "swapper/0" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode
[  864.578840] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[  864.578851] rtl8192ee:
[  864.578854] In process "kworker/0:0" (pid 4):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode
[  865.869016] rtlwifi-0:rtl_lps_set_psmode():<10000-1> FW LPS leave ps_mode:0
[  865.869369] rtl8192ee:
[  865.869371] In process "swapper/0" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode
[  868.584635] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[  868.584645] rtl8192ee:
[  868.584648] In process "kworker/0:0" (pid 4):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode
[  869.517820] wlan1: deauthenticating from <MAC address removed> by local choice (reason=3)
[  869.518290] rtlwifi-0:rtl_tx_agg_stop():<0-0> on ra = <MAC address removed> tid = 0
[  869.518309] rtlwifi-0:rtl_rx_agg_stop():<0-0> on ra = <MAC address removed> tid = 0
[  869.518318] rtlwifi-0:rtl_rx_agg_stop():<0-0> on ra = <MAC address removed> tid = 1
[  869.518349] rtlwifi-0:rtl_op_set_key():<0-0> Disabling hardware based encryption for keyidx: 0, mac: <MAC address removed>
[  869.518358] rtlwifi-0:rtl_op_set_key():<0-0> alg:CCMP
[  869.518364] rtlwifi-0:rtl_op_set_key():<0-0> set enable_hw_sec, key_type:4(OPEN:0 WEP40:1 TKIP:2 AES:4 WEP104:5)
[  869.518371] rtl8192ee-0:rtl92ee_enable_hw_security_config():<0-0> PairwiseEncAlgorithm = 4 GroupEncAlgorithm = 4
[  869.518726] rtl8192ee-0:rtl92ee_enable_hw_security_config():<0-0> The SECR-value cc
[  869.518916] rtlwifi-0:rtl_op_set_key():<0-0> disable key delete one entry
[  869.518923] rtlwifi-0:rtl_cam_delete_one_entry():<0-0> key_idx:0
[  869.519127] rtlwifi-0:rtl_cam_delete_one_entry():<0-0> rtl_cam_delete_one_entry(): WRITE A4: 0
[  869.519134] rtlwifi-0:rtl_cam_delete_one_entry():<0-0> rtl_cam_delete_one_entry(): WRITE A0: 80010000
[  869.519218] rtlwifi-0:rtl_op_sta_remove():<0-0> Remove sta addr is <MAC address removed>
[  869.519705] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS leave ps_mode:0
[  869.520063] rtl8192ee:
[  869.520068] In process "wpa_supplicant" (pid 1077):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode
[  869.520502] rtlwifi-0:rtl_op_bss_info_changed():<0-0> BSS_CHANGED_UN_ASSOC
[  869.520853] rtl8192ee-0:rtl92ee_set_hw_reg():<0-0> switch case not process 1c
[  869.521047] rtl8192ee-0:rtl92ee_set_hw_reg():<0-0> switch case not process 1b
[  869.521407] rtlwifi-0:rtl_op_bss_info_changed():<0-0> bssid: <MAC address removed>
[  869.540252] rtlwifi-0:rtl_op_set_key():<0-0> Disabling hardware based encryption for keyidx: 2, mac: <MAC address removed>
[  869.540258] rtlwifi-0:rtl_op_set_key():<0-0> alg:CCMP
[  869.540261] rtlwifi-0:rtl_op_set_key():<0-0> disable key delete one entry
[  869.540264] rtlwifi-0:rtl_cam_delete_one_entry():<0-0> key_idx:2
[  869.540803] rtlwifi-0:rtl_cam_delete_one_entry():<0-0> rtl_cam_delete_one_entry(): WRITE A4: 0
[  869.540805] rtlwifi-0:rtl_cam_delete_one_entry():<0-0> rtl_cam_delete_one_entry(): WRITE A0: 80010010
[  870.536160] wlan1: authenticate with <MAC address removed>
[  870.576983] rtlwifi-0:rtl_op_bss_info_changed():<0-0> bssid: <MAC address removed>
[  870.577197] wlan1: send auth to <MAC address removed> (try 1/3)
[  870.577206] rtlwifi-0:rtl_tx_mgmt_proc():<200-1> MAC80211_LINKING
[  870.582547] wlan1: authenticated
[  870.583417] wlan1: associate with <MAC address removed> (try 1/3)
[  870.588174] wlan1: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=1)
[  870.588183] rtlwifi-0:rtl_op_sta_add():<0-0> Add sta addr is <MAC address removed>
[  870.588187] rtl8192ee-0:rtl92ee_update_hal_rate_mask():<0-0> ratr_bitmap :ffff005
[  870.588190] rtl8192ee-0:rtl92ee_update_hal_rate_mask():<0-0> Rate_index:2, ratr_val:ffff005, 0:82:0:5:f0:ff:f
[  870.588239] rtl8192ee-0:rtl92ee_update_hal_rate_mask():<0-0> ratr_bitmap :ffff005
[  870.588241] rtl8192ee-0:rtl92ee_update_hal_rate_mask():<0-0> Rate_index:2, ratr_val:ffff005, 0:82:0:5:f0:ff:f
[  870.588266] rtlwifi-0:rtl_op_bss_info_changed():<0-0> BSS_CHANGED_ASSOC
[  870.588284] rtl8192ee-0:rtl92ee_set_hw_reg():<0-0> switch case not process 5b
[  870.588470] rtl8192ee:
[  870.588472] In process "kworker/u16:0" (pid 3685):rtl92ee_set_fw_rsvdpagepkt(): HW_VAR_SET_TX_CMD: ALL
[  870.588481] rtl8192ee:
[  870.596031] rtl8192ee:
[  870.596038] In process "kworker/u16:0" (pid 3685):rtl92ee_set_fw_rsvdpagepkt(): HW_VAR_SET_TX_CMD: ALL
[  870.596060] rtl8192ee:
[  870.599671] rtlwifi-0:rtl_action_proc():<10000-1> Rx ACT_ADDBAREQ From :<MAC address removed>
[  870.599679] rtlwifi:
[  870.604191] rtl8192ee:
[  870.604195] In process "kworker/u16:0" (pid 3685):rtl92ee_set_fw_rsvdpagepkt(): HW_VAR_SET_TX_CMD: ALL
[  870.604208] rtl8192ee:
[  870.612512] rtl8192ee:
[  870.612515] In process "kworker/u16:0" (pid 3685):rtl92ee_set_fw_rsvdpagepkt(): HW_VAR_SET_TX_CMD: ALL
[  870.612527] rtl8192ee:
[  870.620476] rtl8192ee:
[  870.620484] In process "kworker/u16:0" (pid 3685):rtl92ee_set_fw_rsvdpagepkt(): HW_VAR_SET_TX_CMD: ALL
[  870.620503] rtl8192ee:
[  870.629289] wlan1: associated
[  870.629367] rtlwifi-0:rtl_rx_agg_start():<0-0> on ra = <MAC address removed> tid = 0 seq:0
[  870.629381] rtlwifi-0:rtl_action_proc():<200-1> Tx ACT_ADDBARSP From :<MAC address removed>
[  870.633688] rtlwifi-0:rtl_is_special_data():<10000-1> 802.1X Rx EAPOL pkt!!
[  870.634883] rtlwifi-0:rtl_is_special_data():<200-1> 802.1X Tx EAPOL pkt!!
[  870.635270] rtlwifi-0:rtl_is_special_data():<100-1> 802.1X Tx EAPOL pkt!!
[  870.652326] rtlwifi-0:rtl_is_special_data():<10000-1> 802.1X Rx EAPOL pkt!!
[  870.652796] rtlwifi-0:rtl_is_special_data():<200-1> 802.1X Tx EAPOL pkt!!
[  870.653186] rtlwifi-0:rtl_is_special_data():<100-1> 802.1X Tx EAPOL pkt!!
[  870.653243] rtlwifi-0:rtl_op_set_key():<0-0> Using hardware based encryption for keyidx: 0, mac: <MAC address removed>
[  870.653247] rtlwifi-0:rtl_op_set_key():<0-0> alg:CCMP
[  870.653249] rtlwifi-0:rtl_op_set_key():<0-0> set enable_hw_sec, key_type:4(OPEN:0 WEP40:1 TKIP:2 AES:4 WEP104:5)
[  870.653251] rtl8192ee-0:rtl92ee_enable_hw_security_config():<0-0> PairwiseEncAlgorithm = 4 GroupEncAlgorithm = 0
[  870.653602] rtl8192ee-0:rtl92ee_enable_hw_security_config():<0-0> The SECR-value cc
[  870.653606] rtlwifi-0:rtl_op_set_key():<0-0> set pairwise key
[  870.653608] rtl8192ee-0:rtl92ee_set_key():<0-0> add one entry
[  870.653610] rtl8192ee-0:rtl92ee_set_key():<0-0> set Pairwiase key
[  870.653612] rtlwifi-0:rtl_cam_add_one_entry():<0-0> EntryNo:4, ulKeyId=0, ulEncAlg=4, ulUseDK=0 MacAddr <MAC address removed>
[  870.653614] rtlwifi:
[  870.656540] rtlwifi-0:rtl_cam_add_one_entry():<0-0> end
[  870.656839] rtlwifi-0:rtl_op_set_key():<0-0> Using hardware based encryption for keyidx: 2, mac: <MAC address removed>
[  870.656850] rtlwifi-0:rtl_op_set_key():<0-0> alg:CCMP
[  870.656856] rtlwifi-0:rtl_op_set_key():<0-0> set group key
[  870.656862] rtl8192ee-0:rtl92ee_set_key():<0-0> add one entry
[  870.656868] rtl8192ee-0:rtl92ee_set_key():<0-0> set group key
[  870.656874] rtlwifi-0:rtl_cam_add_one_entry():<0-0> EntryNo:2, ulKeyId=2, ulEncAlg=4, ulUseDK=0 MacAddr <MAC address removed>
[  870.656881] rtlwifi:
[  870.659381] rtlwifi-0:rtl_cam_add_one_entry():<0-0> end
[  870.695995] rtlwifi-0:rtl_is_special_data():<200-1> dhcp Tx !!
[  873.422569] rtlwifi-0:rtl_is_special_data():<200-1> dhcp Tx !!
[  874.737941] rtlwifi-0:rtl_action_proc():<10000-1> Rx ACT_ADDBAREQ From :<MAC address removed>
[  874.737951] rtlwifi:
[  874.738633] rtlwifi-0:rtl_rx_agg_start():<0-0> on ra = <MAC address removed> tid = 1 seq:0
[  874.738655] rtlwifi-0:rtl_action_proc():<200-1> Tx ACT_ADDBARSP From :<MAC address removed>
[  876.720147] rtlwifi-0:rtl_tx_agg_start():<0-0> on ra = <MAC address removed> tid = 0 seq:58
[  876.720181] rtlwifi-0:rtl_action_proc():<200-1> Tx ACT_ADDBAREQ From :<MAC address removed>
[  876.720186] rtlwifi:
[  876.723472] rtlwifi-0:rtl_action_proc():<10000-1> Rx ACT_ADDBARSP From :<MAC address removed>
[  876.724123] rtlwifi-0:rtl_tx_agg_oper():<0-0> on ra = <MAC address removed> tid = 0
[  880.097535] wlan1: deauthenticating from <MAC address removed> by local choice (reason=3)
[  880.098361] rtlwifi-0:rtl_tx_agg_stop():<0-0> on ra = <MAC address removed> tid = 0
[  880.098381] rtlwifi-0:rtl_rx_agg_stop():<0-0> on ra = <MAC address removed> tid = 0
[  880.098389] rtlwifi-0:rtl_rx_agg_stop():<0-0> on ra = <MAC address removed> tid = 1
[  880.098421] rtlwifi-0:rtl_op_set_key():<0-0> Disabling hardware based encryption for keyidx: 0, mac: <MAC address removed>
[  880.098430] rtlwifi-0:rtl_op_set_key():<0-0> alg:CCMP
[  880.098436] rtlwifi-0:rtl_op_set_key():<0-0> set enable_hw_sec, key_type:4(OPEN:0 WEP40:1 TKIP:2 AES:4 WEP104:5)
[  880.098451] rtl8192ee-0:rtl92ee_enable_hw_security_config():<0-0> PairwiseEncAlgorithm = 4 GroupEncAlgorithm = 4
[  880.098809] rtl8192ee-0:rtl92ee_enable_hw_security_config():<0-0> The SECR-value cc
[  880.099000] rtlwifi-0:rtl_op_set_key():<0-0> disable key delete one entry
[  880.099005] rtlwifi-0:rtl_cam_delete_one_entry():<0-0> key_idx:0
[  880.099015] rtlwifi-0:rtl_cam_delete_one_entry():<0-0> rtl_cam_delete_one_entry(): WRITE A4: 0
[  880.099021] rtlwifi-0:rtl_cam_delete_one_entry():<0-0> rtl_cam_delete_one_entry(): WRITE A0: 80010000
[  880.099425] rtlwifi-0:rtl_op_sta_remove():<0-0> Remove sta addr is <MAC address removed>
[  880.099561] rtlwifi-0:rtl_op_bss_info_changed():<0-0> BSS_CHANGED_UN_ASSOC
[  880.099918] rtl8192ee-0:rtl92ee_set_hw_reg():<0-0> switch case not process 1c
[  880.100280] rtl8192ee-0:rtl92ee_set_hw_reg():<0-0> switch case not process 1b
[  880.100642] rtlwifi-0:rtl_op_bss_info_changed():<0-0> bssid: <MAC address removed>
[  880.118988] rtlwifi-0:rtl_op_set_key():<0-0> Disabling hardware based encryption for keyidx: 2, mac: <MAC address removed>
[  880.118993] rtlwifi-0:rtl_op_set_key():<0-0> alg:CCMP
[  880.118994] rtlwifi-0:rtl_op_set_key():<0-0> disable key delete one entry
[  880.118996] rtlwifi-0:rtl_cam_delete_one_entry():<0-0> key_idx:2
[  880.119347] rtlwifi-0:rtl_cam_delete_one_entry():<0-0> rtl_cam_delete_one_entry(): WRITE A4: 0
[  880.119349] rtlwifi-0:rtl_cam_delete_one_entry():<0-0> rtl_cam_delete_one_entry(): WRITE A0: 80010010
[  910.127820] wlan1: authenticate with <MAC address removed>
[  910.164938] rtlwifi-0:rtl_op_bss_info_changed():<0-0> bssid: <MAC address removed>
[  910.165345] wlan1: send auth to <MAC address removed> (try 1/3)
[  910.165354] rtlwifi-0:rtl_tx_mgmt_proc():<200-1> MAC80211_LINKING
[  910.171072] wlan1: authenticated
[  910.175067] wlan1: associate with <MAC address removed> (try 1/3)
[  910.186662] wlan1: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=1)
[  910.186677] rtlwifi-0:rtl_op_sta_add():<0-0> Add sta addr is <MAC address removed>
[  910.186684] rtl8192ee-0:rtl92ee_update_hal_rate_mask():<0-0> ratr_bitmap :ffff005
[  910.186689] rtl8192ee-0:rtl92ee_update_hal_rate_mask():<0-0> Rate_index:2, ratr_val:ffff005, 0:82:0:5:f0:ff:f
[  910.187451] rtl8192ee-0:rtl92ee_update_hal_rate_mask():<0-0> ratr_bitmap :ffff005
[  910.187457] rtl8192ee-0:rtl92ee_update_hal_rate_mask():<0-0> Rate_index:2, ratr_val:ffff005, 0:82:0:5:f0:ff:f
[  910.188216] rtlwifi-0:rtl_op_bss_info_changed():<0-0> BSS_CHANGED_ASSOC
[  910.188956] rtl8192ee-0:rtl92ee_set_hw_reg():<0-0> switch case not process 5b
[  910.189680] rtl8192ee:
[  910.189685] In process "kworker/u16:1" (pid 76):rtl92ee_set_fw_rsvdpagepkt(): HW_VAR_SET_TX_CMD: ALL
[  910.189709] rtl8192ee:
[  910.198215] rtl8192ee:
[  910.198218] In process "kworker/u16:1" (pid 76):rtl92ee_set_fw_rsvdpagepkt(): HW_VAR_SET_TX_CMD: ALL
[  910.198229] rtl8192ee:
[  910.206644] rtl8192ee:
[  910.206648] In process "kworker/u16:1" (pid 76):rtl92ee_set_fw_rsvdpagepkt(): HW_VAR_SET_TX_CMD: ALL
[  910.206661] rtl8192ee:
[  910.215414] rtl8192ee:
[  910.215421] In process "kworker/u16:1" (pid 76):rtl92ee_set_fw_rsvdpagepkt(): HW_VAR_SET_TX_CMD: ALL
[  910.215437] rtl8192ee:
[  910.217795] rtlwifi-0:rtl_action_proc():<10000-1> Rx ACT_ADDBAREQ From :<MAC address removed>
[  910.217803] rtlwifi:
[  910.224241] rtl8192ee:
[  910.224246] In process "kworker/u16:1" (pid 76):rtl92ee_set_fw_rsvdpagepkt(): HW_VAR_SET_TX_CMD: ALL
[  910.224259] rtl8192ee:
[  910.232633] wlan1: associated
[  910.232662] rtlwifi-0:rtl_rx_agg_start():<0-0> on ra = <MAC address removed> tid = 0 seq:0
[  910.232673] rtlwifi-0:rtl_action_proc():<200-1> Tx ACT_ADDBARSP From :<MAC address removed>
[  910.245641] rtlwifi-0:rtl_is_special_data():<10000-1> 802.1X Rx EAPOL pkt!!
[  910.246731] rtlwifi-0:rtl_is_special_data():<200-1> 802.1X Tx EAPOL pkt!!
[  910.247141] rtlwifi-0:rtl_is_special_data():<100-1> 802.1X Tx EAPOL pkt!!
[  910.263922] rtlwifi-0:rtl_is_special_data():<10000-1> 802.1X Rx EAPOL pkt!!
[  910.264703] rtlwifi-0:rtl_is_special_data():<200-1> 802.1X Tx EAPOL pkt!!
[  910.265129] rtlwifi-0:rtl_is_special_data():<100-1> 802.1X Tx EAPOL pkt!!
[  910.265251] rtlwifi-0:rtl_op_set_key():<0-0> Using hardware based encryption for keyidx: 0, mac: <MAC address removed>
[  910.265259] rtlwifi-0:rtl_op_set_key():<0-0> alg:CCMP
[  910.265263] rtlwifi-0:rtl_op_set_key():<0-0> set enable_hw_sec, key_type:4(OPEN:0 WEP40:1 TKIP:2 AES:4 WEP104:5)
[  910.265268] rtl8192ee-0:rtl92ee_enable_hw_security_config():<0-0> PairwiseEncAlgorithm = 4 GroupEncAlgorithm = 0
[  910.265619] rtl8192ee-0:rtl92ee_enable_hw_security_config():<0-0> The SECR-value cc
[  910.265625] rtlwifi-0:rtl_op_set_key():<0-0> set pairwise key
[  910.265629] rtl8192ee-0:rtl92ee_set_key():<0-0> add one entry
[  910.265633] rtl8192ee-0:rtl92ee_set_key():<0-0> set Pairwiase key
[  910.265637] rtlwifi-0:rtl_cam_add_one_entry():<0-0> EntryNo:4, ulKeyId=0, ulEncAlg=4, ulUseDK=0 MacAddr <MAC address removed>
[  910.265642] rtlwifi:
[  910.267984] rtlwifi-0:rtl_cam_add_one_entry():<0-0> end
[  910.268302] rtlwifi-0:rtl_op_set_key():<0-0> Using hardware based encryption for keyidx: 2, mac: <MAC address removed>
[  910.268314] rtlwifi-0:rtl_op_set_key():<0-0> alg:CCMP
[  910.268320] rtlwifi-0:rtl_op_set_key():<0-0> set group key
[  910.268327] rtl8192ee-0:rtl92ee_set_key():<0-0> add one entry
[  910.268334] rtl8192ee-0:rtl92ee_set_key():<0-0> set group key
[  910.268340] rtlwifi-0:rtl_cam_add_one_entry():<0-0> EntryNo:2, ulKeyId=2, ulEncAlg=4, ulUseDK=0 MacAddr <MAC address removed>
[  910.268348] rtlwifi:
[  910.270640] rtlwifi-0:rtl_cam_add_one_entry():<0-0> end
[  910.327141] rtlwifi-0:rtl_is_special_data():<200-1> dhcp Tx !!
[  913.154091] rtlwifi-0:rtl_is_special_data():<200-1> dhcp Tx !!
[  914.658595] rtlwifi-0:rtl_action_proc():<10000-1> Rx ACT_ADDBAREQ From :<MAC address removed>
[  914.658605] rtlwifi:
[  914.658827] rtlwifi-0:rtl_rx_agg_start():<0-0> on ra = <MAC address removed> tid = 1 seq:0
[  914.658866] rtlwifi-0:rtl_action_proc():<200-1> Tx ACT_ADDBARSP From :<MAC address removed>
[  914.659934] rtlwifi-0:rtl_action_proc():<10000-1> Rx ACT_ADDBAREQ From :<MAC address removed>
[  914.659942] rtlwifi:
[  914.659995] rtlwifi:
[  914.660435] rtlwifi-0:rtl_rx_agg_stop():<0-0> on ra = <MAC address removed> tid = 1
[  914.660475] rtlwifi-0:rtl_rx_agg_start():<0-0> on ra = <MAC address removed> tid = 1 seq:0
[  914.660494] rtlwifi-0:rtl_action_proc():<200-1> Tx ACT_ADDBARSP From :<MAC address removed>
[  914.660843] rtlwifi-0:rtl_action_proc():<10000-1> Rx ACT_ADDBAREQ From :<MAC address removed>
[  914.660850] rtlwifi:
[  914.660913] rtlwifi:
[  914.661327] rtlwifi-0:rtl_rx_agg_stop():<0-0> on ra = <MAC address removed> tid = 1
[  914.661339] rtlwifi-0:rtl_rx_agg_start():<0-0> on ra = <MAC address removed> tid = 1 seq:0
[  914.661353] rtlwifi-0:rtl_action_proc():<200-1> Tx ACT_ADDBARSP From :<MAC address removed>
[  914.662376] rtlwifi-0:rtl_action_proc():<10000-1> Rx ACT_ADDBAREQ From :<MAC address removed>
[  914.662381] rtlwifi:
[  914.662428] rtlwifi:
[  914.662848] rtlwifi-0:rtl_rx_agg_stop():<0-0> on ra = <MAC address removed> tid = 1
[  914.662861] rtlwifi-0:rtl_rx_agg_start():<0-0> on ra = <MAC address removed> tid = 1 seq:0
[  914.662876] rtlwifi-0:rtl_action_proc():<200-1> Tx ACT_ADDBARSP From :<MAC address removed>
[  914.664390] rtlwifi-0:rtl_action_proc():<10000-1> Rx ACT_ADDBAREQ From :<MAC address removed>
[  914.664399] rtlwifi:
[  914.664480] rtlwifi:
[  914.664933] rtlwifi-0:rtl_rx_agg_stop():<0-0> on ra = <MAC address removed> tid = 1
[  914.664947] rtlwifi-0:rtl_rx_agg_start():<0-0> on ra = <MAC address removed> tid = 1 seq:0
[  914.664963] rtlwifi-0:rtl_action_proc():<200-1> Tx ACT_ADDBARSP From :<MAC address removed>
[  914.676115] rtlwifi-0:rtl_action_proc():<10000-1> Rx ACT_ADDBAREQ From :<MAC address removed>
[  914.676126] rtlwifi:
[  914.676180] rtlwifi:
[  914.676848] rtlwifi-0:rtl_rx_agg_stop():<0-0> on ra = <MAC address removed> tid = 1
[  914.676884] rtlwifi-0:rtl_rx_agg_start():<0-0> on ra = <MAC address removed> tid = 1 seq:0
[  914.676907] rtlwifi-0:rtl_action_proc():<200-1> Tx ACT_ADDBARSP From :<MAC address removed>
[  914.702268] rtlwifi-0:rtl_tx_agg_start():<0-0> on ra = <MAC address removed> tid = 0 seq:34
[  914.702301] rtlwifi-0:rtl_action_proc():<200-1> Tx ACT_ADDBAREQ From :<MAC address removed>
[  914.702307] rtlwifi:
[  914.704325] rtlwifi-0:rtl_action_proc():<10000-1> Rx ACT_ADDBARSP From :<MAC address removed>
[  914.704777] rtlwifi-0:rtl_tx_agg_oper():<0-0> on ra = <MAC address removed> tid = 0
[  917.095862] rtlwifi-0:rtl_tx_agg_start():<0-0> on ra = <MAC address removed> tid = 1 seq:1
[  917.095906] rtlwifi-0:rtl_action_proc():<200-1> Tx ACT_ADDBAREQ From :<MAC address removed>
[  917.095912] rtlwifi:
[  917.100174] rtlwifi-0:rtl_action_proc():<10000-1> Rx ACT_ADDBARSP From :<MAC address removed>
[  917.100813] rtlwifi-0:rtl_tx_agg_oper():<0-0> on ra = <MAC address removed> tid = 1
[  922.242310] rtlwifi-0:rtl_tx_agg_stop():<0-0> on ra = <MAC address removed> tid = 1
[  922.242330] rtlwifi-0:rtl_action_proc():<400-1> ACT_ADDBADEL From :<MAC address removed>
[  924.649066] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[  924.649079] rtl8192ee:
[  924.649083] In process "kworker/0:0" (pid 4):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode
[  931.376203] rtlwifi-0:rtl_lps_set_psmode():<500-1> FW LPS leave ps_mode:0
[  931.376219] rtl8192ee:
[  931.376224] In process "swapper/0" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode
[  934.668576] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[  934.668594] rtl8192ee:
[  934.668598] In process "kworker/0:0" (pid 4):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode
[  936.061554] rtlwifi-0:rtl_lps_set_psmode():<10000-1> FW LPS leave ps_mode:0
[  936.061906] rtl8192ee:
[  936.061910] In process "swapper/0" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode
[  938.676278] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[  938.676288] rtl8192ee:
[  938.676292] In process "kworker/0:0" (pid 4):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode
[  939.570371] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS leave ps_mode:0
[  939.570726] rtl8192ee:
[  939.570728] In process "wpa_supplicant" (pid 1077):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode
[  948.695743] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[  948.695749] rtl8192ee:
[  948.695750] In process "kworker/0:0" (pid 4):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode
[  949.292355] rtlwifi-0:rtl_lps_set_psmode():<10100-1> FW LPS leave ps_mode:0
[  949.292677] rtl8192ee:
[  949.292679] In process "swapper/0" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode
[  958.715186] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[  958.715192] rtl8192ee:
[  958.715194] In process "kworker/0:0" (pid 4):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode
[  959.512645] rtlwifi-0:rtl_lps_set_psmode():<10000-1> FW LPS leave ps_mode:0
[  959.512999] rtl8192ee:
[  959.513002] In process "swapper/0" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode
[  963.730938] rtlwifi-0:rtl_tx_agg_start():<0-0> on ra = <MAC address removed> tid = 1 seq:2
[  963.730975] rtlwifi-0:rtl_action_proc():<200-1> Tx ACT_ADDBAREQ From :<MAC address removed>
[  963.730980] rtlwifi:
[  963.733643] rtlwifi-0:rtl_action_proc():<10000-1> Rx ACT_ADDBARSP From :<MAC address removed>
[  963.734226] rtlwifi-0:rtl_tx_agg_oper():<0-0> on ra = <MAC address removed> tid = 1
[  969.522683] rtlwifi-0:rtl_tx_agg_stop():<0-0> on ra = <MAC address removed> tid = 1
[  969.522731] rtlwifi-0:rtl_action_proc():<400-1> ACT_ADDBADEL From :<MAC address removed>
[  978.754106] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[  978.754121] rtl8192ee:
[  978.754128] In process "kworker/0:0" (pid 4):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode
[  979.522949] rtlwifi-0:rtl_lps_set_psmode():<10000-1> FW LPS leave ps_mode:0
[  979.522965] rtl8192ee:
[  979.522969] In process "chromium-browse" (pid 2647):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode
[  987.661576] rtlwifi-0:rtl_tx_agg_start():<0-0> on ra = <MAC address removed> tid = 1 seq:6
[  987.661602] rtlwifi-0:rtl_action_proc():<200-1> Tx ACT_ADDBAREQ From :<MAC address removed>
[  987.661607] rtlwifi:
[  987.663995] rtlwifi-0:rtl_action_proc():<10000-1> Rx ACT_ADDBARSP From :<MAC address removed>
[  987.664384] rtlwifi-0:rtl_tx_agg_oper():<0-0> on ra = <MAC address removed> tid = 1
[  992.780644] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[  992.780654] rtl8192ee:
[  992.780657] In process "kworker/0:0" (pid 4):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode
[  992.968689] rtlwifi-0:rtl_tx_agg_stop():<0-0> on ra = <MAC address removed> tid = 1
[  992.968729] rtlwifi-0:rtl_action_proc():<400-1> ACT_ADDBADEL From :<MAC address removed>
[  993.313189] rtlwifi-0:rtl_lps_set_psmode():<10100-1> FW LPS leave ps_mode:0
[  993.313550] rtl8192ee:
[  993.313555] In process "swapper/0" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode
[  998.789324] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[  998.789333] rtl8192ee:
[  998.789337] In process "kworker/0:0" (pid 4):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode
[  999.782013] rtlwifi-0:rtl_lps_set_psmode():<10100-1> FW LPS leave ps_mode:0
[  999.782029] rtl8192ee:
[  999.782034] In process "chromium-browse" (pid 2647):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode
[ 1012.809569] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[ 1012.809579] rtl8192ee:
[ 1012.809582] In process "kworker/0:0" (pid 4):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode
[ 1013.771732] rtlwifi-0:rtl_lps_set_psmode():<10000-1> FW LPS leave ps_mode:0
[ 1013.771741] rtl8192ee:
[ 1013.771743] In process "swapper/0" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode
[ 1022.824026] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[ 1022.824037] rtl8192ee:
[ 1022.824040] In process "kworker/0:0" (pid 4):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode
[ 1024.433060] rtlwifi-0:rtl_lps_set_psmode():<10000-1> FW LPS leave ps_mode:0
[ 1024.433413] rtl8192ee:
[ 1024.433417] In process "compiz" (pid 2257):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode
[ 1050.864431] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[ 1050.864441] rtl8192ee:
[ 1050.864445] In process "kworker/0:0" (pid 4):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode
[ 1051.568642] rtlwifi-0:rtl_lps_set_psmode():<10100-1> FW LPS leave ps_mode:0
[ 1051.568993] rtl8192ee:
[ 1051.568994] In process "swapper/0" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode
[ 1096.127224] rtlwifi-0:rtl_tx_agg_start():<0-0> on ra = <MAC address removed> tid = 1 seq:7
[ 1096.127250] rtlwifi-0:rtl_action_proc():<200-1> Tx ACT_ADDBAREQ From :<MAC address removed>
[ 1096.127254] rtlwifi:
[ 1096.129849] rtlwifi-0:rtl_action_proc():<10000-1> Rx ACT_ADDBARSP From :<MAC address removed>
[ 1096.130226] rtlwifi-0:rtl_tx_agg_oper():<0-0> on ra = <MAC address removed> tid = 1
[ 1106.197651] rtlwifi-0:rtl_tx_agg_stop():<0-0> on ra = <MAC address removed> tid = 1
[ 1106.197671] rtlwifi-0:rtl_action_proc():<400-1> ACT_ADDBADEL From :<MAC address removed>
[ 1108.952017] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[ 1108.952023] rtl8192ee:
[ 1108.952024] In process "kworker/0:0" (pid 4):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode
[ 1109.665760] rtlwifi-0:rtl_lps_set_psmode():<10000-1> FW LPS leave ps_mode:0
[ 1109.665771] rtl8192ee:
[ 1109.665774] In process "swapper/0" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode
[ 1111.394747] rtlwifi-0:rtl_tx_agg_start():<0-0> on ra = <MAC address removed> tid = 1 seq:28
[ 1111.394779] rtlwifi-0:rtl_action_proc():<200-1> Tx ACT_ADDBAREQ From :<MAC address removed>
[ 1111.394786] rtlwifi:
[ 1111.399231] rtlwifi-0:rtl_action_proc():<10000-1> Rx ACT_ADDBARSP From :<MAC address removed>
[ 1111.399819] rtlwifi-0:rtl_tx_agg_oper():<0-0> on ra = <MAC address removed> tid = 1
[ 1116.551887] rtlwifi-0:rtl_tx_agg_stop():<0-0> on ra = <MAC address removed> tid = 1
[ 1116.551923] rtlwifi-0:rtl_action_proc():<400-1> ACT_ADDBADEL From :<MAC address removed>
[ 1161.027104] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[ 1161.027113] rtl8192ee:
[ 1161.027117] In process "kworker/0:0" (pid 4):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode
[ 1161.478737] rtlwifi-0:rtl_lps_set_psmode():<10000-1> FW LPS leave ps_mode:0
[ 1161.479100] rtl8192ee:
[ 1161.479105] In process "chromium-browse" (pid 3819):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode
[ 1177.050201] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[ 1177.050213] rtl8192ee:
[ 1177.050218] In process "kworker/0:0" (pid 4):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode
[ 1179.672876] rtlwifi-0:rtl_lps_set_psmode():<10700-1> FW LPS leave ps_mode:0
[ 1179.673232] rtl8192ee:
[ 1179.673235] In process "swapper/0" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode
[ 1187.064602] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[ 1187.064612] rtl8192ee:
[ 1187.064615] In process "kworker/0:0" (pid 4):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode
[ 1187.940614] rtlwifi-0:rtl_lps_set_psmode():<10100-1> FW LPS leave ps_mode:0
[ 1187.940951] rtl8192ee:
[ 1187.940955] In process "swapper/0" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode
[ 1249.154110] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[ 1249.154115] rtl8192ee:
[ 1249.154117] In process "kworker/0:0" (pid 4):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode
[ 1249.460171] rtlwifi-0:rtl_lps_set_psmode():<10100-1> FW LPS leave ps_mode:0
[ 1249.460501] rtl8192ee:
[ 1249.460505] In process "swapper/0" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode
[ 1253.159861] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[ 1253.159867] rtl8192ee:
[ 1253.159869] In process "kworker/0:0" (pid 4):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode
[ 1253.467664] rtlwifi-0:rtl_lps_set_psmode():<10100-1> FW LPS leave ps_mode:0
[ 1253.468018] rtl8192ee:
[ 1253.468023] In process "swapper/0" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode
[ 1270.598234] rtlwifi-0:rtl_tx_agg_start():<0-0> on ra = <MAC address removed> tid = 1 seq:30
[ 1270.598253] rtlwifi-0:rtl_action_proc():<200-1> Tx ACT_ADDBAREQ From :<MAC address removed>
[ 1270.598256] rtlwifi:
[ 1270.600715] rtlwifi-0:rtl_action_proc():<10000-1> Rx ACT_ADDBARSP From :<MAC address removed>
[ 1270.601113] rtlwifi-0:rtl_tx_agg_oper():<0-0> on ra = <MAC address removed> tid = 1
[ 1275.755299] rtlwifi-0:rtl_tx_agg_stop():<0-0> on ra = <MAC address removed> tid = 1
[ 1275.755320] rtlwifi-0:rtl_action_proc():<400-1> ACT_ADDBADEL From :<MAC address removed>
[ 1281.116380] rtlwifi-0:rtl_tx_agg_start():<0-0> on ra = <MAC address removed> tid = 1 seq:34
[ 1281.116410] rtlwifi-0:rtl_action_proc():<200-1> Tx ACT_ADDBAREQ From :<MAC address removed>
[ 1281.116415] rtlwifi:
[ 1281.118631] rtlwifi-0:rtl_action_proc():<10000-1> Rx ACT_ADDBARSP From :<MAC address removed>
[ 1281.118918] rtlwifi-0:rtl_tx_agg_oper():<0-0> on ra = <MAC address removed> tid = 1
[ 1288.899975] rtlwifi-0:rtl_tx_agg_stop():<0-0> on ra = <MAC address removed> tid = 1
[ 1288.900003] rtlwifi-0:rtl_action_proc():<400-1> ACT_ADDBADEL From :<MAC address removed>
[ 1289.211840] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[ 1289.211847] rtl8192ee:
[ 1289.211850] In process "kworker/0:0" (pid 4):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode
[ 1289.441930] rtlwifi-0:rtl_lps_set_psmode():<10000-1> FW LPS leave ps_mode:0
[ 1289.442258] rtl8192ee:
[ 1289.442259] In process "swapper/0" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode
[ 1293.217641] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[ 1293.217651] rtl8192ee:
[ 1293.217654] In process "kworker/0:0" (pid 4):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode
[ 1293.505107] rtlwifi-0:rtl_lps_set_psmode():<10000-1> FW LPS leave ps_mode:0
[ 1293.505463] rtl8192ee:
[ 1293.505464] In process "chromium-browse" (pid 2647):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode
[ 1297.223323] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[ 1297.223328] rtl8192ee:
[ 1297.223330] In process "kworker/0:0" (pid 4):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode
[ 1298.511926] rtlwifi-0:rtl_lps_set_psmode():<10000-1> FW LPS leave ps_mode:0
[ 1298.512278] rtl8192ee:
[ 1298.512282] In process "swapper/0" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode
[ 1309.240695] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[ 1309.240707] rtl8192ee:
[ 1309.240712] In process "kworker/0:0" (pid 4):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode
[ 1310.392007] rtlwifi-0:rtl_lps_set_psmode():<10100-1> FW LPS leave ps_mode:0
[ 1310.392353] rtl8192ee:
[ 1310.392355] In process "chromium-browse" (pid 3657):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode
[ 1313.246503] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[ 1313.246513] rtl8192ee:
[ 1313.246517] In process "kworker/0:0" (pid 4):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode
[ 1313.921129] rtlwifi-0:rtl_lps_set_psmode():<10000-1> FW LPS leave ps_mode:0
[ 1313.921490] rtl8192ee:
[ 1313.921495] In process "chromium-browse" (pid 2647):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode
[ 1333.275326] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[ 1333.275336] rtl8192ee:
[ 1333.275339] In process "kworker/0:0" (pid 4):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode
[ 1334.181981] rtlwifi-0:rtl_lps_set_psmode():<10000-1> FW LPS leave ps_mode:0
[ 1334.182330] rtl8192ee:
[ 1334.182332] In process "Xorg" (pid 1072):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode
[ 1349.298444] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[ 1349.298454] rtl8192ee:
[ 1349.298458] In process "kworker/0:0" (pid 4):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode
[ 1351.370400] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS leave ps_mode:0
[ 1351.370762] rtl8192ee:
[ 1351.370767] In process "wpa_supplicant" (pid 1077):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode
[ 1359.312823] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[ 1359.312829] rtl8192ee:
[ 1359.312831] In process "kworker/0:0" (pid 4):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode
[ 1361.103902] rtlwifi-0:rtl_tx_agg_stop():<0-0> on ra = <MAC address removed> tid = 0
[ 1361.103926] rtlwifi-0:rtl_action_proc():<400-1> ACT_ADDBADEL From :<MAC address removed>
[ 1361.939485] rtlwifi-0:rtl_tx_agg_start():<0-0> on ra = <MAC address removed> tid = 0 seq:2168
[ 1361.939524] rtlwifi-0:rtl_action_proc():<200-1> Tx ACT_ADDBAREQ From :<MAC address removed>
[ 1361.939529] rtlwifi:
[ 1361.943537] rtlwifi-0:rtl_action_proc():<10000-1> Rx ACT_ADDBARSP From :<MAC address removed>
[ 1361.943811] rtlwifi-0:rtl_tx_agg_oper():<0-0> on ra = <MAC address removed> tid = 0
[ 1362.287041] rtlwifi-0:rtl_lps_set_psmode():<10000-1> FW LPS leave ps_mode:0
[ 1362.287389] rtl8192ee:
[ 1362.287392] In process "swapper/0" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode
[ 1367.324399] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[ 1367.324410] rtl8192ee:
[ 1367.324415] In process "kworker/0:0" (pid 4):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode
[ 1368.323487] rtlwifi-0:rtl_lps_set_psmode():<10000-1> FW LPS leave ps_mode:0
[ 1368.323841] rtl8192ee:
[ 1368.323843] In process "swapper/0" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode
[ 1379.341715] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[ 1379.341723] rtl8192ee:
[ 1379.341726] In process "kworker/0:0" (pid 4):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode
[ 1379.461788] rtlwifi-0:rtl_lps_set_psmode():<10000-1> FW LPS leave ps_mode:0
[ 1379.461805] rtl8192ee:
[ 1379.461810] In process "swapper/0" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode
[ 1389.356130] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[ 1389.356140] rtl8192ee:
[ 1389.356143] In process "kworker/0:0" (pid 4):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode
[ 1391.123176] rtlwifi-0:rtl_tx_agg_stop():<0-0> on ra = <MAC address removed> tid = 0
[ 1391.123227] rtlwifi-0:rtl_action_proc():<400-1> ACT_ADDBADEL From :<MAC address removed>
[ 1393.881666] rtlwifi-0:rtl_tx_agg_start():<0-0> on ra = <MAC address removed> tid = 0 seq:2241
[ 1393.881691] rtlwifi-0:rtl_action_proc():<200-1> Tx ACT_ADDBAREQ From :<MAC address removed>
[ 1393.881696] rtlwifi:
[ 1393.887647] rtlwifi-0:rtl_action_proc():<10000-1> Rx ACT_ADDBARSP From :<MAC address removed>
[ 1393.888252] rtlwifi-0:rtl_tx_agg_oper():<0-0> on ra = <MAC address removed> tid = 0
[ 1403.248468] rtlwifi-0:rtl_tx_agg_stop():<0-0> on ra = <MAC address removed> tid = 0
[ 1403.248490] rtlwifi-0:rtl_action_proc():<400-1> ACT_ADDBADEL From :<MAC address removed>
[ 1403.868099] rtlwifi-0:rtl_tx_agg_start():<0-0> on ra = <MAC address removed> tid = 0 seq:2243
[ 1403.868119] rtlwifi-0:rtl_action_proc():<200-1> Tx ACT_ADDBAREQ From :<MAC address removed>
[ 1403.868121] rtlwifi:
[ 1403.875933] rtlwifi-0:rtl_action_proc():<10000-1> Rx ACT_ADDBARSP From :<MAC address removed>
[ 1403.876322] rtlwifi-0:rtl_tx_agg_oper():<0-0> on ra = <MAC address removed> tid = 0
[ 1405.927240] rtlwifi-0:rtl_lps_set_psmode():<10000-1> FW LPS leave ps_mode:0
[ 1405.927254] rtl8192ee:
[ 1405.927257] In process "swapper/0" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode
[ 1413.390716] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[ 1413.390722] rtl8192ee:
[ 1413.390724] In process "kworker/0:0" (pid 4):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode
[ 1413.771922] rtlwifi-0:rtl_lps_set_psmode():<10400-1> FW LPS leave ps_mode:0
[ 1413.772272] rtl8192ee:
[ 1413.772275] In process "Chrome_IOThread" (pid 2678):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode
[ 1417.396529] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[ 1417.396538] rtl8192ee:
[ 1417.396542] In process "kworker/0:0" (pid 4):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode
[ 1422.629290] wlan1: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 1422.629751] rtlwifi-0:rtl_tx_agg_stop():<0-0> on ra = <MAC address removed> tid = 0
[ 1422.629760] rtlwifi-0:rtl_rx_agg_stop():<0-0> on ra = <MAC address removed> tid = 0
[ 1422.629767] rtlwifi-0:rtl_rx_agg_stop():<0-0> on ra = <MAC address removed> tid = 1
[ 1422.630883] rtlwifi-0:rtl_op_set_key():<0-0> Disabling hardware based encryption for keyidx: 0, mac: <MAC address removed>
[ 1422.630893] rtlwifi-0:rtl_op_set_key():<0-0> alg:CCMP
[ 1422.630897] rtlwifi-0:rtl_op_set_key():<0-0> set enable_hw_sec, key_type:4(OPEN:0 WEP40:1 TKIP:2 AES:4 WEP104:5)
[ 1422.630902] rtl8192ee-0:rtl92ee_enable_hw_security_config():<0-0> PairwiseEncAlgorithm = 4 GroupEncAlgorithm = 4
[ 1422.631253] rtl8192ee-0:rtl92ee_enable_hw_security_config():<0-0> The SECR-value cc
[ 1422.631260] rtlwifi-0:rtl_op_set_key():<0-0> disable key delete one entry
[ 1422.631264] rtlwifi-0:rtl_cam_delete_one_entry():<0-0> key_idx:0
[ 1422.631612] rtlwifi-0:rtl_cam_delete_one_entry():<0-0> rtl_cam_delete_one_entry(): WRITE A4: 0
[ 1422.631616] rtlwifi-0:rtl_cam_delete_one_entry():<0-0> rtl_cam_delete_one_entry(): WRITE A0: 80010000
[ 1422.631678] rtlwifi-0:rtl_op_sta_remove():<0-0> Remove sta addr is <MAC address removed>
[ 1422.632133] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS leave ps_mode:0
[ 1422.632324] rtl8192ee:
[ 1422.632329] In process "wpa_supplicant" (pid 1077):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode
[ 1422.632695] rtlwifi-0:rtl_op_bss_info_changed():<0-0> BSS_CHANGED_UN_ASSOC
[ 1422.632706] rtl8192ee-0:rtl92ee_set_hw_reg():<0-0> switch case not process 1c
[ 1422.632722] rtl8192ee-0:rtl92ee_set_hw_reg():<0-0> switch case not process 1b
[ 1422.632921] rtlwifi-0:rtl_op_bss_info_changed():<0-0> bssid: <MAC address removed>
[ 1422.652359] rtlwifi-0:rtl_op_set_key():<0-0> Disabling hardware based encryption for keyidx: 2, mac: <MAC address removed>
[ 1422.652365] rtlwifi-0:rtl_op_set_key():<0-0> alg:CCMP
[ 1422.652367] rtlwifi-0:rtl_op_set_key():<0-0> disable key delete one entry
[ 1422.652369] rtlwifi-0:rtl_cam_delete_one_entry():<0-0> key_idx:2
[ 1422.652716] rtlwifi-0:rtl_cam_delete_one_entry():<0-0> rtl_cam_delete_one_entry(): WRITE A4: 0
[ 1422.652718] rtlwifi-0:rtl_cam_delete_one_entry():<0-0> rtl_cam_delete_one_entry(): WRITE A0: 80010010
[ 1450.346391] rtlwifi-0:rtl_pci_start():<0-0>  rtl_pci_start
[ 1450.352408] rtl8192ee-0:rtl92ee_download_fw():<0-0> normal Firmware SIZE 32754
[ 1450.352411] rtl8192ee-0:rtl92ee_download_fw():<0-0> Firmware Version(14), Signature(0x92e1),Size(32)
[ 1450.859245] rtl8192ee-0:rtl92ee_enable_hw_security_config():<0-0> PairwiseEncAlgorithm = 0 GroupEncAlgorithm = 0
[ 1450.859258] rtl8192ee-0:rtl92ee_enable_hw_security_config():<0-0> The SECR-value cc
[ 1450.995074] rtlwifi-0:rtl_pci_start():<0-0> rtl_pci_start OK
[ 1451.012848] IPv6: ADDRCONF(NETDEV_UP): wlan1: link is not ready
[ 1467.353556] wlan1: authenticate with <MAC address removed>
[ 1467.390510] rtlwifi-0:rtl_op_bss_info_changed():<0-0> bssid: <MAC address removed>
[ 1467.390923] wlan1: send auth to <MAC address removed> (try 1/3)
[ 1467.390934] rtlwifi-0:rtl_tx_mgmt_proc():<200-1> MAC80211_LINKING
[ 1467.395724] wlan1: authenticated
[ 1467.396774] wlan1: associate with <MAC address removed> (try 1/3)
[ 1467.400893] wlan1: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=1)
[ 1467.400900] rtlwifi-0:rtl_op_sta_add():<0-0> Add sta addr is <MAC address removed>
[ 1467.400904] rtl8192ee-0:rtl92ee_update_hal_rate_mask():<0-0> ratr_bitmap :ff5
[ 1467.400906] rtl8192ee-0:rtl92ee_update_hal_rate_mask():<0-0> Rate_index:6, ratr_val:ff5, 0:6:0:f5:f:0:0
[ 1467.401279] rtl8192ee-0:rtl92ee_update_hal_rate_mask():<0-0> ratr_bitmap :ff5
[ 1467.401282] rtl8192ee-0:rtl92ee_update_hal_rate_mask():<0-0> Rate_index:6, ratr_val:ff5, 0:6:0:f5:f:0:0
[ 1467.401649] rtlwifi-0:rtl_op_bss_info_changed():<0-0> BSS_CHANGED_ASSOC
[ 1467.401666] rtl8192ee-0:rtl92ee_set_hw_reg():<0-0> switch case not process 5b
[ 1467.401685] rtl8192ee:
[ 1467.401686] In process "kworker/u16:0" (pid 4338):rtl92ee_set_fw_rsvdpagepkt(): HW_VAR_SET_TX_CMD: ALL
[ 1467.401695] rtl8192ee:
[ 1467.409883] rtl8192ee:
[ 1467.409886] In process "kworker/u16:0" (pid 4338):rtl92ee_set_fw_rsvdpagepkt(): HW_VAR_SET_TX_CMD: ALL
[ 1467.409893] rtl8192ee:
[ 1467.410675] rtlwifi-0:rtl_is_special_data():<10000-1> 802.1X Rx EAPOL pkt!!
[ 1467.418428] rtl8192ee:
[ 1467.418430] In process "kworker/u16:0" (pid 4338):rtl92ee_set_fw_rsvdpagepkt(): HW_VAR_SET_TX_CMD: ALL
[ 1467.418437] rtl8192ee:
[ 1467.426716] rtl8192ee:
[ 1467.426720] In process "kworker/u16:0" (pid 4338):rtl92ee_set_fw_rsvdpagepkt(): HW_VAR_SET_TX_CMD: ALL
[ 1467.426728] rtl8192ee:
[ 1467.434963] rtl8192ee:
[ 1467.434966] In process "kworker/u16:0" (pid 4338):rtl92ee_set_fw_rsvdpagepkt(): HW_VAR_SET_TX_CMD: ALL
[ 1467.434975] rtl8192ee:
[ 1467.443594] wlan1: associated
[ 1467.443605] IPv6: ADDRCONF(NETDEV_CHANGE): wlan1: link becomes ready
[ 1467.444818] rtlwifi-0:rtl_is_special_data():<200-1> 802.1X Tx EAPOL pkt!!
[ 1467.445213] rtlwifi-0:rtl_is_special_data():<100-1> 802.1X Tx EAPOL pkt!!
[ 1467.458079] rtlwifi-0:rtl_is_special_data():<10000-1> 802.1X Rx EAPOL pkt!!
[ 1467.458544] rtlwifi-0:rtl_is_special_data():<200-1> 802.1X Tx EAPOL pkt!!
[ 1467.458919] rtlwifi-0:rtl_is_special_data():<100-1> 802.1X Tx EAPOL pkt!!
[ 1467.459024] rtlwifi-0:rtl_op_set_key():<0-0> Using hardware based encryption for keyidx: 0, mac: <MAC address removed>
[ 1467.459027] rtlwifi-0:rtl_op_set_key():<0-0> alg:CCMP
[ 1467.459029] rtlwifi-0:rtl_op_set_key():<0-0> set enable_hw_sec, key_type:4(OPEN:0 WEP40:1 TKIP:2 AES:4 WEP104:5)
[ 1467.459032] rtl8192ee-0:rtl92ee_enable_hw_security_config():<0-0> PairwiseEncAlgorithm = 4 GroupEncAlgorithm = 0
[ 1467.459385] rtl8192ee-0:rtl92ee_enable_hw_security_config():<0-0> The SECR-value cc
[ 1467.459390] rtlwifi-0:rtl_op_set_key():<0-0> set pairwise key
[ 1467.459392] rtl8192ee-0:rtl92ee_set_key():<0-0> add one entry
[ 1467.459394] rtl8192ee-0:rtl92ee_set_key():<0-0> set Pairwiase key
[ 1467.459396] rtlwifi-0:rtl_cam_add_one_entry():<0-0> EntryNo:4, ulKeyId=0, ulEncAlg=4, ulUseDK=0 MacAddr <MAC address removed>
[ 1467.459398] rtlwifi:
[ 1467.462170] rtlwifi-0:rtl_cam_add_one_entry():<0-0> end
[ 1467.462269] rtlwifi-0:rtl_op_set_key():<0-0> Using hardware based encryption for keyidx: 1, mac: <MAC address removed>
[ 1467.462271] rtlwifi-0:rtl_op_set_key():<0-0> alg:CCMP
[ 1467.462272] rtlwifi-0:rtl_op_set_key():<0-0> set group key
[ 1467.462274] rtl8192ee-0:rtl92ee_set_key():<0-0> add one entry
[ 1467.462275] rtl8192ee-0:rtl92ee_set_key():<0-0> set group key
[ 1467.462276] rtlwifi-0:rtl_cam_add_one_entry():<0-0> EntryNo:1, ulKeyId=1, ulEncAlg=4, ulUseDK=0 MacAddr <MAC address removed>
[ 1467.462278] rtlwifi:
[ 1467.465167] rtlwifi-0:rtl_cam_add_one_entry():<0-0> end
[ 1467.492817] rtlwifi-0:rtl_is_special_data():<200-1> dhcp Tx !!
[ 1469.020291] rtl8192ee-0:rtl92ee_update_hal_rate_mask():<0-0> ratr_bitmap :f00
[ 1469.020300] rtl8192ee-0:rtl92ee_update_hal_rate_mask():<0-0> Rate_index:6, ratr_val:f00, 0:6:0:0:f:0:0
[ 1470.245388] rtlwifi-0:rtl_is_special_data():<200-1> dhcp Tx !!
[ 1470.265581] rtlwifi-0:rtl_is_special_data():<200-1> dhcp Tx !!
[ 1470.339066] Modules linked in: parport_pc ppdev bnep rfcomm nls_iso8859_1 snd_hda_codec_realtek snd_hda_codec_hdmi x86_pkg_temp_thermal coretemp kvm_intel kvm crct10dif_pclmul crc32_pclmul ghash_clmulni_intel aesni_intel aes_x86_64 lrw gf128mul glue_helper ablk_helper cryptd joydev uvcvideo videobuf2_vmalloc videobuf2_memops videobuf2_core videodev 8188eu(OF) arc4 rtsx_pci_ms snd_hda_intel snd_hda_codec snd_hwdep snd_pcm microcode thinkpad_acpi nvram rtl8192ee(OF) btcoexist(OF) rtlwifi(OF) snd_page_alloc memstick snd_seq_midi psmouse snd_seq_midi_event snd_rawmidi serio_raw mac80211 cfg80211 lpc_ich btusb bluetooth snd_seq snd_seq_device snd_timer snd i915 soundcore tpm_tis drm_kms_helper video mei_me drm mei i2c_algo_bit wmi intel_smartconnect mac_hid lp parport rtsx_pci_sdmmc e1000e ahci libahci ptp rtsx_pci pps_core
[ 1477.031377] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[ 1477.031386] rtl8192ee:
[ 1477.031390] In process "kworker/1:0" (pid 4343):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode
[ 1481.515268] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS leave ps_mode:0
[ 1481.515631] rtl8192ee:
[ 1481.515636] In process "wpa_supplicant" (pid 1077):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode
[ 1487.045830] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[ 1487.045840] rtl8192ee:
[ 1487.045843] In process "kworker/1:0" (pid 4343):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode
[ 1495.713287] rtlwifi-0:rtl_lps_set_psmode():<300-1> FW LPS leave ps_mode:0
[ 1495.713642] rtl8192ee:
[ 1495.713645] In process "swapper/1" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode
[ 1499.063091] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[ 1499.063101] rtl8192ee:
[ 1499.063104] In process "kworker/1:0" (pid 4343):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode
[ 1520.739368] rtlwifi-0:rtl_lps_set_psmode():<300-1> FW LPS leave ps_mode:0
[ 1520.739713] rtl8192ee:
[ 1520.739716] In process "swapper/0" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode
[ 1523.097713] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[ 1523.097723] rtl8192ee:
[ 1523.097727] In process "kworker/1:0" (pid 4343):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode
[ 1524.271240] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS leave ps_mode:0
[ 1524.271606] rtl8192ee:
[ 1524.271608] In process "wpa_supplicant" (pid 1077):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode
[ 1529.106458] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[ 1529.106468] rtl8192ee:
[ 1529.106471] In process "kworker/1:0" (pid 4343):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode
[ 1546.181254] rtlwifi-0:rtl_lps_set_psmode():<300-1> FW LPS leave ps_mode:0
[ 1546.181609] rtl8192ee:
[ 1546.181612] In process "swapper/2" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode
[ 1549.135271] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[ 1549.135281] rtl8192ee:
[ 1549.135284] In process "kworker/1:0" (pid 4343):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode
[ 1561.666642] wlan1: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 1561.667845] rtlwifi-0:rtl_op_set_key():<0-0> Disabling hardware based encryption for keyidx: 0, mac: <MAC address removed>
[ 1561.667852] rtlwifi-0:rtl_op_set_key():<0-0> alg:CCMP
[ 1561.667854] rtlwifi-0:rtl_op_set_key():<0-0> set enable_hw_sec, key_type:4(OPEN:0 WEP40:1 TKIP:2 AES:4 WEP104:5)
[ 1561.667857] rtl8192ee-0:rtl92ee_enable_hw_security_config():<0-0> PairwiseEncAlgorithm = 4 GroupEncAlgorithm = 4
[ 1561.668205] rtl8192ee-0:rtl92ee_enable_hw_security_config():<0-0> The SECR-value cc
[ 1561.668209] rtlwifi-0:rtl_op_set_key():<0-0> disable key delete one entry
[ 1561.668211] rtlwifi-0:rtl_cam_delete_one_entry():<0-0> key_idx:0
[ 1561.668402] rtlwifi-0:rtl_cam_delete_one_entry():<0-0> rtl_cam_delete_one_entry(): WRITE A4: 0
[ 1561.668405] rtlwifi-0:rtl_cam_delete_one_entry():<0-0> rtl_cam_delete_one_entry(): WRITE A0: 80010000
[ 1561.668441] rtlwifi-0:rtl_op_sta_remove():<0-0> Remove sta addr is <MAC address removed>
[ 1561.668844] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS leave ps_mode:0
[ 1561.668851] rtl8192ee:
[ 1561.668852] In process "wpa_supplicant" (pid 1077):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode
[ 1561.669223] rtlwifi-0:rtl_op_bss_info_changed():<0-0> BSS_CHANGED_UN_ASSOC
[ 1561.669230] rtl8192ee-0:rtl92ee_set_hw_reg():<0-0> switch case not process 1c
[ 1561.669243] rtl8192ee-0:rtl92ee_set_hw_reg():<0-0> switch case not process 1b
[ 1561.669256] rtlwifi-0:rtl_op_bss_info_changed():<0-0> bssid: <MAC address removed>
[ 1561.669344] rtlwifi-0:rtl_op_set_key():<0-0> Disabling hardware based encryption for keyidx: 1, mac: <MAC address removed>
[ 1561.669354] rtlwifi-0:rtl_op_set_key():<0-0> alg:CCMP
[ 1561.669359] rtlwifi-0:rtl_op_set_key():<0-0> disable key delete one entry
[ 1561.669365] rtlwifi-0:rtl_cam_delete_one_entry():<0-0> key_idx:1
[ 1561.669714] rtlwifi-0:rtl_cam_delete_one_entry():<0-0> rtl_cam_delete_one_entry(): WRITE A4: 0
[ 1561.669720] rtlwifi-0:rtl_cam_delete_one_entry():<0-0> rtl_cam_delete_one_entry(): WRITE A0: 80010008
[ 1566.236489] wlan1: authenticate with <MAC address removed>
[ 1566.253173] rtlwifi-0:rtl_op_bss_info_changed():<0-0> bssid: <MAC address removed>
[ 1566.253584] wlan1: send auth to <MAC address removed> (try 1/3)
[ 1566.253592] rtlwifi-0:rtl_tx_mgmt_proc():<200-1> MAC80211_LINKING
[ 1566.275546] wlan1: authenticated
[ 1566.277747] wlan1: associate with <MAC address removed> (try 1/3)
[ 1566.299493] wlan1: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=1)
[ 1566.299499] rtlwifi-0:rtl_op_sta_add():<0-0> Add sta addr is <MAC address removed>
[ 1566.299502] rtl8192ee-0:rtl92ee_update_hal_rate_mask():<0-0> ratr_bitmap :ff5
[ 1566.299503] rtl8192ee-0:rtl92ee_update_hal_rate_mask():<0-0> Rate_index:6, ratr_val:ff5, 0:6:0:f5:f:0:0
[ 1566.299875] rtl8192ee-0:rtl92ee_update_hal_rate_mask():<0-0> ratr_bitmap :ff5
[ 1566.299876] rtl8192ee-0:rtl92ee_update_hal_rate_mask():<0-0> Rate_index:6, ratr_val:ff5, 0:6:0:f5:f:0:0
[ 1566.299897] rtlwifi-0:rtl_op_bss_info_changed():<0-0> BSS_CHANGED_ASSOC
[ 1566.299912] rtl8192ee-0:rtl92ee_set_hw_reg():<0-0> switch case not process 5b
[ 1566.299931] rtl8192ee:
[ 1566.299932] In process "kworker/u16:4" (pid 155):rtl92ee_set_fw_rsvdpagepkt(): HW_VAR_SET_TX_CMD: ALL
[ 1566.299938] rtl8192ee:
[ 1566.308187] rtl8192ee:
[ 1566.308190] In process "kworker/u16:4" (pid 155):rtl92ee_set_fw_rsvdpagepkt(): HW_VAR_SET_TX_CMD: ALL
[ 1566.308197] rtl8192ee:
[ 1566.316309] rtl8192ee:
[ 1566.316311] In process "kworker/u16:4" (pid 155):rtl92ee_set_fw_rsvdpagepkt(): HW_VAR_SET_TX_CMD: ALL
[ 1566.316315] rtl8192ee:
[ 1566.316713] rtlwifi-0:rtl_is_special_data():<10000-1> 802.1X Rx EAPOL pkt!!
[ 1566.324010] rtl8192ee:
[ 1566.324012] In process "kworker/u16:4" (pid 155):rtl92ee_set_fw_rsvdpagepkt(): HW_VAR_SET_TX_CMD: ALL
[ 1566.324019] rtl8192ee:
[ 1566.332078] rtl8192ee:
[ 1566.332080] In process "kworker/u16:4" (pid 155):rtl92ee_set_fw_rsvdpagepkt(): HW_VAR_SET_TX_CMD: ALL
[ 1566.332086] rtl8192ee:
[ 1566.341226] wlan1: associated
[ 1566.346228] rtlwifi-0:rtl_is_special_data():<200-1> 802.1X Tx EAPOL pkt!!
[ 1566.346609] rtlwifi-0:rtl_is_special_data():<100-1> 802.1X Tx EAPOL pkt!!
[ 1566.370745] rtlwifi-0:rtl_is_special_data():<10000-1> 802.1X Rx EAPOL pkt!!
[ 1566.371488] rtlwifi-0:rtl_is_special_data():<200-1> 802.1X Tx EAPOL pkt!!
[ 1566.371873] rtlwifi-0:rtl_is_special_data():<100-1> 802.1X Tx EAPOL pkt!!
[ 1566.372059] rtlwifi-0:rtl_op_set_key():<0-0> Using hardware based encryption for keyidx: 0, mac: <MAC address removed>
[ 1566.372066] rtlwifi-0:rtl_op_set_key():<0-0> alg:CCMP
[ 1566.372069] rtlwifi-0:rtl_op_set_key():<0-0> set enable_hw_sec, key_type:4(OPEN:0 WEP40:1 TKIP:2 AES:4 WEP104:5)
[ 1566.372075] rtl8192ee-0:rtl92ee_enable_hw_security_config():<0-0> PairwiseEncAlgorithm = 4 GroupEncAlgorithm = 0
[ 1566.372423] rtl8192ee-0:rtl92ee_enable_hw_security_config():<0-0> The SECR-value cc
[ 1566.372431] rtlwifi-0:rtl_op_set_key():<0-0> set pairwise key
[ 1566.372437] rtl8192ee-0:rtl92ee_set_key():<0-0> add one entry
[ 1566.372441] rtl8192ee-0:rtl92ee_set_key():<0-0> set Pairwiase key
[ 1566.372448] rtlwifi-0:rtl_cam_add_one_entry():<0-0> EntryNo:4, ulKeyId=0, ulEncAlg=4, ulUseDK=0 MacAddr <MAC address removed>
[ 1566.372454] rtlwifi:
[ 1566.375925] rtlwifi-0:rtl_cam_add_one_entry():<0-0> end
[ 1566.376235] rtlwifi-0:rtl_op_set_key():<0-0> Using hardware based encryption for keyidx: 1, mac: <MAC address removed>
[ 1566.376242] rtlwifi-0:rtl_op_set_key():<0-0> alg:CCMP
[ 1566.376246] rtlwifi-0:rtl_op_set_key():<0-0> set group key
[ 1566.376250] rtl8192ee-0:rtl92ee_set_key():<0-0> add one entry
[ 1566.376254] rtl8192ee-0:rtl92ee_set_key():<0-0> set group key
[ 1566.376257] rtlwifi-0:rtl_cam_add_one_entry():<0-0> EntryNo:1, ulKeyId=1, ulEncAlg=4, ulUseDK=0 MacAddr <MAC address removed>
[ 1566.376261] rtlwifi:
[ 1566.378983] rtlwifi-0:rtl_cam_add_one_entry():<0-0> end
[ 1566.405858] rtlwifi-0:rtl_is_special_data():<200-1> dhcp Tx !!
[ 1567.369242] rtlwifi-0:rtl_is_special_data():<10000-1> 802.1X Rx EAPOL pkt!!
[ 1567.370291] rtlwifi-0:rtl_is_special_data():<200-1> 802.1X Tx EAPOL pkt!!
[ 1567.370814] rtlwifi-0:rtl_op_set_key():<0-0> Disabling hardware based encryption for keyidx: 0, mac: <MAC address removed>
[ 1567.370822] rtlwifi-0:rtl_op_set_key():<0-0> alg:CCMP
[ 1567.370826] rtlwifi-0:rtl_op_set_key():<0-0> set enable_hw_sec, key_type:4(OPEN:0 WEP40:1 TKIP:2 AES:4 WEP104:5)
[ 1567.370831] rtl8192ee-0:rtl92ee_enable_hw_security_config():<0-0> PairwiseEncAlgorithm = 4 GroupEncAlgorithm = 4
[ 1567.371178] rtl8192ee-0:rtl92ee_enable_hw_security_config():<0-0> The SECR-value cc
[ 1567.371368] rtlwifi-0:rtl_op_set_key():<0-0> disable key delete one entry
[ 1567.371375] rtlwifi-0:rtl_cam_delete_one_entry():<0-0> key_idx:0
[ 1567.372264] rtlwifi-0:rtl_cam_delete_one_entry():<0-0> rtl_cam_delete_one_entry(): WRITE A4: 0
[ 1567.372270] rtlwifi-0:rtl_cam_delete_one_entry():<0-0> rtl_cam_delete_one_entry(): WRITE A0: 80010000
[ 1567.372402] rtlwifi-0:rtl_op_set_key():<0-0> Using hardware based encryption for keyidx: 0, mac: <MAC address removed>
[ 1567.372410] rtlwifi-0:rtl_op_set_key():<0-0> alg:CCMP
[ 1567.372415] rtlwifi-0:rtl_op_set_key():<0-0> set enable_hw_sec, key_type:4(OPEN:0 WEP40:1 TKIP:2 AES:4 WEP104:5)
[ 1567.372421] rtl8192ee-0:rtl92ee_enable_hw_security_config():<0-0> PairwiseEncAlgorithm = 4 GroupEncAlgorithm = 4
[ 1567.372813] rtl8192ee-0:rtl92ee_enable_hw_security_config():<0-0> The SECR-value cc
[ 1567.373198] rtlwifi-0:rtl_op_set_key():<0-0> set pairwise key
[ 1567.373205] rtl8192ee-0:rtl92ee_set_key():<0-0> add one entry
[ 1567.373210] rtl8192ee-0:rtl92ee_set_key():<0-0> set Pairwiase key
[ 1567.373216] rtlwifi-0:rtl_cam_add_one_entry():<0-0> EntryNo:4, ulKeyId=0, ulEncAlg=4, ulUseDK=0 MacAddr <MAC address removed>
[ 1567.373223] rtlwifi:
[ 1567.375958] rtlwifi-0:rtl_cam_add_one_entry():<0-0> end
[ 1567.376153] rtlwifi-0:rtl_op_set_key():<0-0> Disabling hardware based encryption for keyidx: 1, mac: <MAC address removed>
[ 1567.376159] rtlwifi-0:rtl_op_set_key():<0-0> alg:CCMP
[ 1567.376162] rtlwifi-0:rtl_op_set_key():<0-0> disable key delete one entry
[ 1567.376165] rtlwifi-0:rtl_cam_delete_one_entry():<0-0> key_idx:1
[ 1567.376514] rtlwifi-0:rtl_cam_delete_one_entry():<0-0> rtl_cam_delete_one_entry(): WRITE A4: 0
[ 1567.376517] rtlwifi-0:rtl_cam_delete_one_entry():<0-0> rtl_cam_delete_one_entry(): WRITE A0: 80010008
[ 1567.376586] rtlwifi-0:rtl_op_set_key():<0-0> Using hardware based encryption for keyidx: 1, mac: <MAC address removed>
[ 1567.376590] rtlwifi-0:rtl_op_set_key():<0-0> alg:CCMP
[ 1567.376593] rtlwifi-0:rtl_op_set_key():<0-0> set group key
[ 1567.376597] rtl8192ee-0:rtl92ee_set_key():<0-0> add one entry
[ 1567.376600] rtl8192ee-0:rtl92ee_set_key():<0-0> set group key
[ 1567.376602] rtlwifi-0:rtl_cam_add_one_entry():<0-0> EntryNo:1, ulKeyId=1, ulEncAlg=4, ulUseDK=0 MacAddr <MAC address removed>
[ 1567.376606] rtlwifi:
[ 1567.379339] rtlwifi-0:rtl_cam_add_one_entry():<0-0> end
[ 1569.848581] rtlwifi-0:rtl_is_special_data():<200-1> dhcp Tx !!
[ 1574.934645] rtlwifi-0:rtl_is_special_data():<200-1> dhcp Tx !!
[ 1577.175706] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[ 1577.175717] rtl8192ee:
[ 1577.175720] In process "kworker/1:0" (pid 4343):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode
[ 1580.446740] rtlwifi-0:rtl_is_special_data():<200-1> dhcp Tx !!
[ 1580.447089] rtlwifi-0:rtl_lps_set_psmode():<200-1> FW LPS leave ps_mode:0
[ 1580.447278] rtl8192ee:
[ 1580.447280] In process "dhclient" (pid 4543):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode
[ 1583.184303] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[ 1583.184309] rtl8192ee:
[ 1583.184312] In process "kworker/1:0" (pid 4343):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode
[ 1583.536260] rtlwifi-0:rtl_is_special_data():<200-1> dhcp Tx !!
[ 1583.536620] rtlwifi-0:rtl_lps_set_psmode():<200-1> FW LPS leave ps_mode:0
[ 1583.536810] rtl8192ee:
[ 1583.536812] In process "dhclient" (pid 4543):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode
[ 1587.190083] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[ 1587.190096] rtl8192ee:
[ 1587.190101] In process "kworker/1:0" (pid 4343):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode
[ 1590.626360] rtlwifi-0:rtl_is_special_data():<200-1> dhcp Tx !!
[ 1590.626716] rtlwifi-0:rtl_lps_set_psmode():<200-1> FW LPS leave ps_mode:0
[ 1590.626905] rtl8192ee:
[ 1590.626908] In process "dhclient" (pid 4543):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode
[ 1593.198786] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[ 1593.198796] rtl8192ee:
[ 1593.198800] In process "kworker/1:0" (pid 4343):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode
[ 1598.703907] rtlwifi-0:rtl_is_special_data():<200-1> dhcp Tx !!
[ 1598.704264] rtlwifi-0:rtl_lps_set_psmode():<200-1> FW LPS leave ps_mode:0
[ 1598.704453] rtl8192ee:
[ 1598.704455] In process "dhclient" (pid 4543):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode
[ 1601.210337] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[ 1601.210347] rtl8192ee:
[ 1601.210351] In process "kworker/1:0" (pid 4343):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode
[ 1611.428386] wlan1: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 1611.428910] rtlwifi-0:rtl_op_set_key():<0-0> Disabling hardware based encryption for keyidx: 0, mac: <MAC address removed>
[ 1611.428916] rtlwifi-0:rtl_op_set_key():<0-0> alg:CCMP
[ 1611.428918] rtlwifi-0:rtl_op_set_key():<0-0> set enable_hw_sec, key_type:4(OPEN:0 WEP40:1 TKIP:2 AES:4 WEP104:5)
[ 1611.428921] rtl8192ee-0:rtl92ee_enable_hw_security_config():<0-0> PairwiseEncAlgorithm = 4 GroupEncAlgorithm = 4
[ 1611.429274] rtl8192ee-0:rtl92ee_enable_hw_security_config():<0-0> The SECR-value cc
[ 1611.429278] rtlwifi-0:rtl_op_set_key():<0-0> disable key delete one entry
[ 1611.429281] rtlwifi-0:rtl_cam_delete_one_entry():<0-0> key_idx:0
[ 1611.429468] rtlwifi-0:rtl_cam_delete_one_entry():<0-0> rtl_cam_delete_one_entry(): WRITE A4: 0
[ 1611.429470] rtlwifi-0:rtl_cam_delete_one_entry():<0-0> rtl_cam_delete_one_entry(): WRITE A0: 80010000
[ 1611.429509] rtlwifi-0:rtl_op_sta_remove():<0-0> Remove sta addr is <MAC address removed>
[ 1611.429914] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS leave ps_mode:0
[ 1611.429921] rtl8192ee:
[ 1611.429923] In process "wpa_supplicant" (pid 4532):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode
[ 1611.430095] rtlwifi-0:rtl_op_bss_info_changed():<0-0> BSS_CHANGED_UN_ASSOC
[ 1611.430257] rtl8192ee-0:rtl92ee_set_hw_reg():<0-0> switch case not process 1c
[ 1611.430266] rtl8192ee-0:rtl92ee_set_hw_reg():<0-0> switch case not process 1b
[ 1611.430279] rtlwifi-0:rtl_op_bss_info_changed():<0-0> bssid: <MAC address removed>
[ 1611.432358] rtlwifi-0:rtl_op_set_key():<0-0> Disabling hardware based encryption for keyidx: 1, mac: <MAC address removed>
[ 1611.432371] rtlwifi-0:rtl_op_set_key():<0-0> alg:CCMP
[ 1611.432376] rtlwifi-0:rtl_op_set_key():<0-0> disable key delete one entry
[ 1611.432382] rtlwifi-0:rtl_cam_delete_one_entry():<0-0> key_idx:1
[ 1611.433098] rtlwifi-0:rtl_cam_delete_one_entry():<0-0> rtl_cam_delete_one_entry(): WRITE A4: 0
[ 1611.433103] rtlwifi-0:rtl_cam_delete_one_entry():<0-0> rtl_cam_delete_one_entry(): WRITE A0: 80010008
[ 1615.183834] wlan1: authenticate with <MAC address removed>
[ 1615.201290] rtlwifi-0:rtl_op_bss_info_changed():<0-0> bssid: <MAC address removed>
[ 1615.201739] wlan1: direct probe to <MAC address removed> (try 1/3)
[ 1615.402471] wlan1: send auth to <MAC address removed> (try 2/3)
[ 1615.402493] rtlwifi-0:rtl_tx_mgmt_proc():<200-1> MAC80211_LINKING
[ 1615.406938] wlan1: authenticated
[ 1615.410456] wlan1: associate with <MAC address removed> (try 1/3)
[ 1615.434451] wlan1: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=1)
[ 1615.434461] rtlwifi-0:rtl_op_sta_add():<0-0> Add sta addr is <MAC address removed>
[ 1615.434465] rtl8192ee-0:rtl92ee_update_hal_rate_mask():<0-0> ratr_bitmap :ff5
[ 1615.434467] rtl8192ee-0:rtl92ee_update_hal_rate_mask():<0-0> Rate_index:6, ratr_val:ff5, 0:6:0:f5:f:0:0
[ 1615.434838] rtl8192ee-0:rtl92ee_update_hal_rate_mask():<0-0> ratr_bitmap :ff5
[ 1615.434840] rtl8192ee-0:rtl92ee_update_hal_rate_mask():<0-0> Rate_index:6, ratr_val:ff5, 0:6:0:f5:f:0:0
[ 1615.435043] rtlwifi-0:rtl_op_bss_info_changed():<0-0> BSS_CHANGED_ASSOC
[ 1615.435059] rtl8192ee-0:rtl92ee_set_hw_reg():<0-0> switch case not process 5b
[ 1615.435078] rtl8192ee:
[ 1615.435080] In process "kworker/u16:4" (pid 155):rtl92ee_set_fw_rsvdpagepkt(): HW_VAR_SET_TX_CMD: ALL
[ 1615.435087] rtl8192ee:
[ 1615.441563] rtlwifi-0:rtl_is_special_data():<10000-1> 802.1X Rx EAPOL pkt!!
[ 1615.443533] rtl8192ee:
[ 1615.443534] In process "kworker/u16:4" (pid 155):rtl92ee_set_fw_rsvdpagepkt(): HW_VAR_SET_TX_CMD: ALL
[ 1615.443538] rtl8192ee:
[ 1615.451847] rtl8192ee:
[ 1615.451851] In process "kworker/u16:4" (pid 155):rtl92ee_set_fw_rsvdpagepkt(): HW_VAR_SET_TX_CMD: ALL
[ 1615.451859] rtl8192ee:
[ 1615.460367] rtl8192ee:
[ 1615.460371] In process "kworker/u16:4" (pid 155):rtl92ee_set_fw_rsvdpagepkt(): HW_VAR_SET_TX_CMD: ALL
[ 1615.460378] rtl8192ee:
[ 1615.468644] rtl8192ee:
[ 1615.468648] In process "kworker/u16:4" (pid 155):rtl92ee_set_fw_rsvdpagepkt(): HW_VAR_SET_TX_CMD: ALL
[ 1615.468657] rtl8192ee:
[ 1615.476938] wlan1: associated
[ 1615.477844] rtlwifi-0:rtl_is_special_data():<200-1> 802.1X Tx EAPOL pkt!!
[ 1615.478235] rtlwifi-0:rtl_is_special_data():<100-1> 802.1X Tx EAPOL pkt!!
[ 1615.492224] rtlwifi-0:rtl_is_special_data():<10000-1> 802.1X Rx EAPOL pkt!!
[ 1615.492720] rtlwifi-0:rtl_is_special_data():<200-1> 802.1X Tx EAPOL pkt!!
[ 1615.492767] rtlwifi-0:rtl_is_special_data():<100-1> 802.1X Tx EAPOL pkt!!
[ 1615.492839] rtlwifi-0:rtl_op_set_key():<0-0> Using hardware based encryption for keyidx: 0, mac: <MAC address removed>
[ 1615.492845] rtlwifi-0:rtl_op_set_key():<0-0> alg:CCMP
[ 1615.492849] rtlwifi-0:rtl_op_set_key():<0-0> set enable_hw_sec, key_type:4(OPEN:0 WEP40:1 TKIP:2 AES:4 WEP104:5)
[ 1615.492853] rtl8192ee-0:rtl92ee_enable_hw_security_config():<0-0> PairwiseEncAlgorithm = 4 GroupEncAlgorithm = 0
[ 1615.493200] rtl8192ee-0:rtl92ee_enable_hw_security_config():<0-0> The SECR-value cc
[ 1615.493205] rtlwifi-0:rtl_op_set_key():<0-0> set pairwise key
[ 1615.493209] rtl8192ee-0:rtl92ee_set_key():<0-0> add one entry
[ 1615.493212] rtl8192ee-0:rtl92ee_set_key():<0-0> set Pairwiase key
[ 1615.493216] rtlwifi-0:rtl_cam_add_one_entry():<0-0> EntryNo:4, ulKeyId=0, ulEncAlg=4, ulUseDK=0 MacAddr <MAC address removed>
[ 1615.493219] rtlwifi:
[ 1615.496178] rtlwifi-0:rtl_cam_add_one_entry():<0-0> end
[ 1615.496305] rtlwifi-0:rtl_op_set_key():<0-0> Using hardware based encryption for keyidx: 1, mac: <MAC address removed>
[ 1615.496309] rtlwifi-0:rtl_op_set_key():<0-0> alg:CCMP
[ 1615.496311] rtlwifi-0:rtl_op_set_key():<0-0> set group key
[ 1615.496313] rtl8192ee-0:rtl92ee_set_key():<0-0> add one entry
[ 1615.496315] rtl8192ee-0:rtl92ee_set_key():<0-0> set group key
[ 1615.496317] rtlwifi-0:rtl_cam_add_one_entry():<0-0> EntryNo:1, ulKeyId=1, ulEncAlg=4, ulUseDK=0 MacAddr <MAC address removed>
[ 1615.496319] rtlwifi:
[ 1615.499428] rtlwifi-0:rtl_cam_add_one_entry():<0-0> end
[ 1615.527540] rtlwifi-0:rtl_is_special_data():<200-1> dhcp Tx !!
[ 1618.873663] rtlwifi-0:rtl_is_special_data():<200-1> dhcp Tx !!
[ 1625.244974] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[ 1625.244984] rtl8192ee:
[ 1625.244987] In process "kworker/1:0" (pid 4343):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode
[ 1629.930405] rtlwifi-0:rtl_is_special_data():<10000-1> dhcp Rx !!
[ 1637.207815] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS leave ps_mode:0
[ 1637.208167] rtl8192ee:
[ 1637.208170] In process "wpa_supplicant" (pid 4532):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode
[ 1641.268073] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[ 1641.268086] rtl8192ee:
[ 1641.268093] In process "kworker/1:0" (pid 4343):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode
[ 1645.070274] rtlwifi-0:rtl_lps_set_psmode():<300-1> FW LPS leave ps_mode:0
[ 1645.070464] rtl8192ee:
[ 1645.070465] In process "swapper/3" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode
[ 1647.276695] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[ 1647.276701] rtl8192ee:
[ 1647.276703] In process "kworker/1:0" (pid 4343):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode
[ 1674.909643] rtlwifi-0:rtl_lps_set_psmode():<300-1> FW LPS leave ps_mode:0
[ 1674.909999] rtl8192ee:
[ 1674.910000] In process "swapper/0" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode
[ 1677.319981] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[ 1677.319993] rtl8192ee:
[ 1677.319998] In process "kworker/1:0" (pid 4343):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode
[ 1680.184239] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS leave ps_mode:0
[ 1680.184594] rtl8192ee:
[ 1680.184597] In process "wpa_supplicant" (pid 4532):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode
[ 1685.331567] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[ 1685.331577] rtl8192ee:
[ 1685.331580] In process "kworker/1:0" (pid 4343):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode
[ 1699.008302] rtlwifi-0:rtl_lps_set_psmode():<300-1> FW LPS leave ps_mode:0
[ 1699.008665] rtl8192ee:
[ 1699.008670] In process "swapper/3" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode
[ 1701.354642] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[ 1701.354652] rtl8192ee:
[ 1701.354655] In process "kworker/1:0" (pid 4343):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode
[ 1724.018375] rtlwifi-0:rtl_lps_set_psmode():<300-1> FW LPS leave ps_mode:0
[ 1724.018730] rtl8192ee:
[ 1724.018733] In process "swapper/2" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode
[ 1727.396158] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[ 1727.396168] rtl8192ee:
[ 1727.396172] In process "kworker/1:0" (pid 4343):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode
[ 1727.396540] rtlwifi-0:rtl_watchdog_wq_callback():<0-0> AP off for 2 s
[ 1729.399309] rtlwifi-0:rtl_watchdog_wq_callback():<0-0> AP off for 4 s
[ 1731.402278] rtlwifi-0:rtl_watchdog_wq_callback():<0-0> AP off for 6 s
[ 1733.405149] rtlwifi-0:rtl_watchdog_wq_callback():<0-0> AP off for 8 s
[ 1735.408037] rtlwifi-0:rtl_watchdog_wq_callback():<0-0> AP off for 10 s
[ 1735.408042] rtlwifi-0:rtl_watchdog_wq_callback():<0-0> AP off, try to reconnect now
[ 1735.408057] wlan1: Connection to AP <MAC address removed> lost
[ 1735.415709] rtlwifi-0:rtl_op_set_key():<0-0> Disabling hardware based encryption for keyidx: 0, mac: <MAC address removed>
[ 1735.415715] rtlwifi-0:rtl_op_set_key():<0-0> alg:CCMP
[ 1735.415718] rtlwifi-0:rtl_op_set_key():<0-0> set enable_hw_sec, key_type:4(OPEN:0 WEP40:1 TKIP:2 AES:4 WEP104:5)
[ 1735.415721] rtl8192ee-0:rtl92ee_enable_hw_security_config():<0-0> PairwiseEncAlgorithm = 4 GroupEncAlgorithm = 4
[ 1735.416066] rtl8192ee-0:rtl92ee_enable_hw_security_config():<0-0> The SECR-value cc
[ 1735.416071] rtlwifi-0:rtl_op_set_key():<0-0> disable key delete one entry
[ 1735.416074] rtlwifi-0:rtl_cam_delete_one_entry():<0-0> key_idx:0
[ 1735.416415] rtlwifi-0:rtl_cam_delete_one_entry():<0-0> rtl_cam_delete_one_entry(): WRITE A4: 0
[ 1735.416417] rtlwifi-0:rtl_cam_delete_one_entry():<0-0> rtl_cam_delete_one_entry(): WRITE A0: 80010000
[ 1735.416466] rtlwifi-0:rtl_op_sta_remove():<0-0> Remove sta addr is <MAC address removed>
[ 1735.416885] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS leave ps_mode:0
[ 1735.417074] rtl8192ee:
[ 1735.417076] In process "kworker/u16:1" (pid 5018):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode
[ 1735.417263] rtlwifi-0:rtl_op_bss_info_changed():<0-0> BSS_CHANGED_UN_ASSOC
[ 1735.417426] rtl8192ee-0:rtl92ee_set_hw_reg():<0-0> switch case not process 1c
[ 1735.417783] rtl8192ee-0:rtl92ee_set_hw_reg():<0-0> switch case not process 1b
[ 1735.417796] rtlwifi-0:rtl_op_bss_info_changed():<0-0> bssid: <MAC address removed>
[ 1735.447703] rtlwifi-0:rtl_op_set_key():<0-0> Disabling hardware based encryption for keyidx: 1, mac: <MAC address removed>
[ 1735.447718] rtlwifi-0:rtl_op_set_key():<0-0> alg:CCMP
[ 1735.447724] rtlwifi-0:rtl_op_set_key():<0-0> disable key delete one entry
[ 1735.447730] rtlwifi-0:rtl_cam_delete_one_entry():<0-0> key_idx:1
[ 1735.448080] rtlwifi-0:rtl_cam_delete_one_entry():<0-0> rtl_cam_delete_one_entry(): WRITE A4: 0
[ 1735.448086] rtlwifi-0:rtl_cam_delete_one_entry():<0-0> rtl_cam_delete_one_entry(): WRITE A0: 80010008
[ 1751.397282] IPv6: ADDRCONF(NETDEV_UP): wlan1: link is not ready
[ 1752.404447] wlan1: authenticate with <MAC address removed>
[ 1752.441053] rtlwifi-0:rtl_op_bss_info_changed():<0-0> bssid: <MAC address removed>
[ 1752.441805] wlan1: send auth to <MAC address removed> (try 1/3)
[ 1752.441820] rtlwifi-0:rtl_tx_mgmt_proc():<200-1> MAC80211_LINKING
[ 1752.448283] wlan1: authenticated
[ 1752.450146] wlan1: associate with <MAC address removed> (try 1/3)
[ 1752.464330] wlan1: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=1)
[ 1752.464336] rtlwifi-0:rtl_op_sta_add():<0-0> Add sta addr is <MAC address removed>
[ 1752.464339] rtl8192ee-0:rtl92ee_update_hal_rate_mask():<0-0> ratr_bitmap :ffff005
[ 1752.464340] rtl8192ee-0:rtl92ee_update_hal_rate_mask():<0-0> Rate_index:2, ratr_val:ffff005, 0:82:0:5:f0:ff:f
[ 1752.464718] rtl8192ee-0:rtl92ee_update_hal_rate_mask():<0-0> ratr_bitmap :ffff005
[ 1752.464720] rtl8192ee-0:rtl92ee_update_hal_rate_mask():<0-0> Rate_index:2, ratr_val:ffff005, 0:82:0:5:f0:ff:f
[ 1752.464923] rtlwifi-0:rtl_op_bss_info_changed():<0-0> BSS_CHANGED_ASSOC
[ 1752.464939] rtl8192ee-0:rtl92ee_set_hw_reg():<0-0> switch case not process 5b
[ 1752.464960] rtl8192ee:
[ 1752.464961] In process "kworker/u16:1" (pid 5018):rtl92ee_set_fw_rsvdpagepkt(): HW_VAR_SET_TX_CMD: ALL
[ 1752.464970] rtl8192ee:
[ 1752.473218] rtl8192ee:
[ 1752.473222] In process "kworker/u16:1" (pid 5018):rtl92ee_set_fw_rsvdpagepkt(): HW_VAR_SET_TX_CMD: ALL
[ 1752.473231] rtl8192ee:
[ 1752.473949] rtlwifi-0:rtl_action_proc():<10000-1> Rx ACT_ADDBAREQ From :<MAC address removed>
[ 1752.473953] rtlwifi:
[ 1752.481974] rtl8192ee:
[ 1752.481977] In process "kworker/u16:1" (pid 5018):rtl92ee_set_fw_rsvdpagepkt(): HW_VAR_SET_TX_CMD: ALL
[ 1752.481983] rtl8192ee:
[ 1752.491285] rtl8192ee:
[ 1752.491289] In process "kworker/u16:1" (pid 5018):rtl92ee_set_fw_rsvdpagepkt(): HW_VAR_SET_TX_CMD: ALL
[ 1752.491297] rtl8192ee:
[ 1752.499896] rtl8192ee:
[ 1752.499900] In process "kworker/u16:1" (pid 5018):rtl92ee_set_fw_rsvdpagepkt(): HW_VAR_SET_TX_CMD: ALL
[ 1752.499908] rtl8192ee:
[ 1752.508235] wlan1: associated
[ 1752.508245] IPv6: ADDRCONF(NETDEV_CHANGE): wlan1: link becomes ready
[ 1752.508568] rtlwifi-0:rtl_rx_agg_start():<0-0> on ra = <MAC address removed> tid = 0 seq:0
[ 1752.508579] rtlwifi-0:rtl_action_proc():<200-1> Tx ACT_ADDBARSP From :<MAC address removed>
[ 1752.514449] rtlwifi-0:rtl_is_special_data():<10000-1> 802.1X Rx EAPOL pkt!!
[ 1752.515362] rtlwifi-0:rtl_is_special_data():<200-1> 802.1X Tx EAPOL pkt!!
[ 1752.515736] rtlwifi-0:rtl_is_special_data():<100-1> 802.1X Tx EAPOL pkt!!
[ 1752.525632] rtlwifi-0:rtl_is_special_data():<10000-1> 802.1X Rx EAPOL pkt!!
[ 1752.526506] rtlwifi-0:rtl_is_special_data():<200-1> 802.1X Tx EAPOL pkt!!
[ 1752.526904] rtlwifi-0:rtl_is_special_data():<100-1> 802.1X Tx EAPOL pkt!!
[ 1752.526982] rtlwifi-0:rtl_op_set_key():<0-0> Using hardware based encryption for keyidx: 0, mac: <MAC address removed>
[ 1752.526988] rtlwifi-0:rtl_op_set_key():<0-0> alg:CCMP
[ 1752.526990] rtlwifi-0:rtl_op_set_key():<0-0> set enable_hw_sec, key_type:4(OPEN:0 WEP40:1 TKIP:2 AES:4 WEP104:5)
[ 1752.526993] rtl8192ee-0:rtl92ee_enable_hw_security_config():<0-0> PairwiseEncAlgorithm = 4 GroupEncAlgorithm = 0
[ 1752.527345] rtl8192ee-0:rtl92ee_enable_hw_security_config():<0-0> The SECR-value cc
[ 1752.527349] rtlwifi-0:rtl_op_set_key():<0-0> set pairwise key
[ 1752.527350] rtl8192ee-0:rtl92ee_set_key():<0-0> add one entry
[ 1752.527351] rtl8192ee-0:rtl92ee_set_key():<0-0> set Pairwiase key
[ 1752.527353] rtlwifi-0:rtl_cam_add_one_entry():<0-0> EntryNo:4, ulKeyId=0, ulEncAlg=4, ulUseDK=0 MacAddr <MAC address removed>
[ 1752.527355] rtlwifi:
[ 1752.530070] rtlwifi-0:rtl_cam_add_one_entry():<0-0> end
[ 1752.530565] rtlwifi-0:rtl_op_set_key():<0-0> Using hardware based encryption for keyidx: 1, mac: <MAC address removed>
[ 1752.530577] rtlwifi-0:rtl_op_set_key():<0-0> alg:CCMP
[ 1752.530584] rtlwifi-0:rtl_op_set_key():<0-0> set group key
[ 1752.530591] rtl8192ee-0:rtl92ee_set_key():<0-0> add one entry
[ 1752.530597] rtl8192ee-0:rtl92ee_set_key():<0-0> set group key
[ 1752.530604] rtlwifi-0:rtl_cam_add_one_entry():<0-0> EntryNo:1, ulKeyId=1, ulEncAlg=4, ulUseDK=0 MacAddr <MAC address removed>
[ 1752.530611] rtlwifi:
[ 1752.533352] rtlwifi-0:rtl_cam_add_one_entry():<0-0> end
[ 1752.570349] rtlwifi-0:rtl_is_special_data():<200-1> dhcp Tx !!
[ 1755.784433] rtlwifi-0:rtl_is_special_data():<200-1> dhcp Tx !!
[ 1757.236192] rtlwifi-0:rtl_action_proc():<10000-1> Rx ACT_ADDBAREQ From :<MAC address removed>
[ 1757.236202] rtlwifi:
[ 1757.236870] rtlwifi-0:rtl_rx_agg_start():<0-0> on ra = <MAC address removed> tid = 1 seq:0
[ 1757.236891] rtlwifi-0:rtl_action_proc():<200-1> Tx ACT_ADDBARSP From :<MAC address removed>
[ 1759.090601] rtlwifi-0:rtl_tx_agg_start():<0-0> on ra = <MAC address removed> tid = 0 seq:44
[ 1759.090627] rtlwifi-0:rtl_action_proc():<200-1> Tx ACT_ADDBAREQ From :<MAC address removed>
[ 1759.090630] rtlwifi:
[ 1759.102778] rtlwifi-0:rtl_action_proc():<10000-1> Rx ACT_ADDBARSP From :<MAC address removed>
[ 1759.103180] rtlwifi-0:rtl_tx_agg_oper():<0-0> on ra = <MAC address removed> tid = 0
[ 1769.454992] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[ 1769.455004] rtl8192ee:
[ 1769.455010] In process "kworker/1:0" (pid 4343):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode
[ 1778.126455] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS leave ps_mode:0
[ 1778.126817] rtl8192ee:
[ 1778.126822] In process "wpa_supplicant" (pid 4532):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode
[ 1779.336624] rtlwifi-0:rtl_tx_agg_stop():<0-0> on ra = <MAC address removed> tid = 0
[ 1782.485673] rtlwifi-0:rtl_action_proc():<400-1> ACT_ADDBADEL From :<MAC address removed>
[ 1783.468740] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[ 1783.468751] rtl8192ee:
[ 1783.468754] In process "kworker/1:0" (pid 4343):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode
[ 1796.473519] rtlwifi-0:rtl_tx_agg_start():<0-0> on ra = <MAC address removed> tid = 0 seq:67
[ 1796.473549] rtlwifi-0:rtl_action_proc():<200-1> Tx ACT_ADDBAREQ From :<MAC address removed>
[ 1796.473554] rtlwifi:
[ 1796.480846] rtlwifi-0:rtl_action_proc():<10000-1> Rx ACT_ADDBARSP From :<MAC address removed>
[ 1796.481228] rtlwifi-0:rtl_tx_agg_oper():<0-0> on ra = <MAC address removed> tid = 0
[ 1800.396032] rtlwifi-0:rtl_lps_set_psmode():<10000-1> FW LPS leave ps_mode:0
[ 1800.396386] rtl8192ee:
[ 1800.396389] In process "swapper/0" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode
[ 1811.509150] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[ 1811.509160] rtl8192ee:
[ 1811.509164] In process "kworker/1:0" (pid 4343):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode
[ 1814.259623] rtlwifi-0:rtl_tx_agg_stop():<0-0> on ra = <MAC address removed> tid = 0
[ 1814.259665] rtlwifi-0:rtl_action_proc():<400-1> ACT_ADDBADEL From :<MAC address removed>
[ 1816.866192] rtlwifi-0:rtl_tx_agg_start():<0-0> on ra = <MAC address removed> tid = 0 seq:100
[ 1816.866224] rtlwifi-0:rtl_action_proc():<200-1> Tx ACT_ADDBAREQ From :<MAC address removed>
[ 1816.866228] rtlwifi:
[ 1816.885625] rtlwifi-0:rtl_action_proc():<10000-1> Rx ACT_ADDBARSP From :<MAC address removed>
[ 1816.886243] rtlwifi-0:rtl_tx_agg_oper():<0-0> on ra = <MAC address removed> tid = 0
[ 1816.954243] rtlwifi-0:rtl_lps_set_psmode():<10000-1> FW LPS leave ps_mode:0
[ 1816.954411] rtl8192ee:
[ 1816.954414] In process "swapper/0" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode
[ 1833.540866] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[ 1833.540876] rtl8192ee:
[ 1833.540879] In process "kworker/1:0" (pid 4343):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode
[ 1834.426247] rtlwifi-0:rtl_lps_set_psmode():<10000-1> FW LPS leave ps_mode:0
[ 1834.426603] rtl8192ee:
[ 1834.426607] In process "swapper/0" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode
[ 1837.546627] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[ 1837.546639] rtl8192ee:
[ 1837.546643] In process "kworker/1:0" (pid 4343):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode
[ 1838.120814] rtlwifi-0:rtl_lps_set_psmode():<10000-1> FW LPS leave ps_mode:0
[ 1838.121162] rtl8192ee:
[ 1838.121165] In process "swapper/0" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode
[ 1862.109015] rtlwifi-0:_rtl_pci_interrupt():<10000-1> rx overflow !
[ 1897.930831] rtlwifi-0:rtl_action_proc():<10500-1> ACT_ADDBADEL From :<MAC address removed>
[ 1897.931902] rtlwifi-0:rtl_rx_agg_stop():<0-0> on ra = <MAC address removed> tid = 1
[ 1897.935300] rtlwifi-0:rtl_action_proc():<10000-1> Rx ACT_ADDBAREQ From :<MAC address removed>
[ 1897.935310] rtlwifi:
[ 1897.935784] rtlwifi-0:rtl_rx_agg_start():<0-0> on ra = <MAC address removed> tid = 1 seq:0
[ 1897.935802] rtlwifi-0:rtl_action_proc():<200-1> Tx ACT_ADDBARSP From :<MAC address removed>
[ 1897.964227] rtlwifi-0:rtl_action_proc():<10000-1> Rx ACT_ADDBAREQ From :<MAC address removed>
[ 1897.964232] rtlwifi:
[ 1897.964259] rtlwifi:
[ 1897.964658] rtlwifi-0:rtl_rx_agg_stop():<0-0> on ra = <MAC address removed> tid = 1
[ 1897.964669] rtlwifi-0:rtl_rx_agg_start():<0-0> on ra = <MAC address removed> tid = 1 seq:0
[ 1897.964681] rtlwifi-0:rtl_action_proc():<200-1> Tx ACT_ADDBARSP From :<MAC address removed>
[ 1923.670713] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[ 1923.670725] rtl8192ee:
[ 1923.670730] In process "kworker/1:0" (pid 4343):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode
[ 1924.512269] rtlwifi-0:rtl_lps_set_psmode():<10000-1> FW LPS leave ps_mode:0
[ 1924.512460] rtl8192ee:
[ 1924.512462] In process "swapper/0" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode
[ 1941.696686] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[ 1941.696698] rtl8192ee:
[ 1941.696703] In process "kworker/1:0" (pid 4343):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode
[ 1941.927478] rtlwifi-0:rtl_lps_set_psmode():<10000-1> FW LPS leave ps_mode:0
[ 1941.927834] rtl8192ee:
[ 1941.927837] In process "swapper/0" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode
[ 1951.711102] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[ 1951.711108] rtl8192ee:
[ 1951.711110] In process "kworker/1:0" (pid 4343):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode
[ 1953.730017] rtlwifi-0:rtl_tx_agg_stop():<0-0> on ra = <MAC address removed> tid = 0
[ 1953.730052] rtlwifi-0:rtl_action_proc():<400-1> ACT_ADDBADEL From :<MAC address removed>
[ 1953.838030] rtlwifi-0:rtl_tx_agg_start():<0-0> on ra = <MAC address removed> tid = 0 seq:3747
[ 1953.838053] rtlwifi-0:rtl_action_proc():<200-1> Tx ACT_ADDBAREQ From :<MAC address removed>
[ 1953.838057] rtlwifi:
[ 1953.843443] rtlwifi-0:rtl_action_proc():<10000-1> Rx ACT_ADDBARSP From :<MAC address removed>
[ 1953.843805] rtlwifi-0:rtl_tx_agg_oper():<0-0> on ra = <MAC address removed> tid = 0
[ 1953.879143] rtlwifi-0:rtl_lps_set_psmode():<10000-1> FW LPS leave ps_mode:0
[ 1953.879307] rtl8192ee:
[ 1953.879309] In process "swapper/0" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode
[ 1987.763736] rtlwifi-0:rtl_watchdog_wq_callback():<0-0> AP off for 2 s
[ 1989.766580] rtlwifi-0:rtl_watchdog_wq_callback():<0-0> AP off for 4 s
[ 1991.769310] rtlwifi-0:rtl_watchdog_wq_callback():<0-0> AP off for 6 s
[ 1993.771696] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[ 1993.771700] rtl8192ee:
[ 1993.771702] In process "kworker/1:0" (pid 4343):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode
[ 1993.772054] rtlwifi-0:rtl_watchdog_wq_callback():<0-0> AP off for 8 s
[ 1995.774941] rtlwifi-0:rtl_watchdog_wq_callback():<0-0> AP off for 10 s
[ 1995.774946] rtlwifi-0:rtl_watchdog_wq_callback():<0-0> AP off, try to reconnect now
[ 1995.774975] wlan1: Connection to AP <MAC address removed> lost
[ 1997.777901] rtlwifi-0:rtl_watchdog_wq_callback():<0-0> AP off for 2 s
[ 1999.780788] rtlwifi-0:rtl_watchdog_wq_callback():<0-0> AP off for 4 s
[ 2000.572028] rtlwifi-0:rtl_tx_agg_stop():<0-0> on ra = <MAC address removed> tid = 0
[ 2000.572038] rtlwifi-0:rtl_rx_agg_stop():<0-0> on ra = <MAC address removed> tid = 0
[ 2000.572047] rtlwifi-0:rtl_rx_agg_stop():<0-0> on ra = <MAC address removed> tid = 1
[ 2000.572078] rtlwifi-0:rtl_op_set_key():<0-0> Disabling hardware based encryption for keyidx: 0, mac: <MAC address removed>
[ 2000.572088] rtlwifi-0:rtl_op_set_key():<0-0> alg:CCMP
[ 2000.572089] rtlwifi-0:rtl_op_set_key():<0-0> set enable_hw_sec, key_type:4(OPEN:0 WEP40:1 TKIP:2 AES:4 WEP104:5)
[ 2000.572092] rtl8192ee-0:rtl92ee_enable_hw_security_config():<0-0> PairwiseEncAlgorithm = 4 GroupEncAlgorithm = 4
[ 2000.572437] rtl8192ee-0:rtl92ee_enable_hw_security_config():<0-0> The SECR-value cc
[ 2000.572441] rtlwifi-0:rtl_op_set_key():<0-0> disable key delete one entry
[ 2000.572443] rtlwifi-0:rtl_cam_delete_one_entry():<0-0> key_idx:0
[ 2000.572604] rtlwifi-0:rtl_cam_delete_one_entry():<0-0> rtl_cam_delete_one_entry(): WRITE A4: 0
[ 2000.572606] rtlwifi-0:rtl_cam_delete_one_entry():<0-0> rtl_cam_delete_one_entry(): WRITE A0: 80010000
[ 2000.572641] rtlwifi-0:rtl_op_sta_remove():<0-0> Remove sta addr is <MAC address removed>
[ 2000.573045] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS leave ps_mode:0
[ 2000.573052] rtl8192ee:
[ 2000.573053] In process "kworker/u16:4" (pid 155):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode
[ 2000.573091] rtlwifi-0:rtl_op_bss_info_changed():<0-0> BSS_CHANGED_UN_ASSOC
[ 2000.573099] rtl8192ee-0:rtl92ee_set_hw_reg():<0-0> switch case not process 1c
[ 2000.573111] rtl8192ee-0:rtl92ee_set_hw_reg():<0-0> switch case not process 1b
[ 2000.573133] rtlwifi-0:rtl_op_bss_info_changed():<0-0> bssid: <MAC address removed>
[ 2000.576418] rtlwifi-0:_rtl_pci_interrupt():<10000-1> rx overflow !
[ 2000.592519] rtlwifi-0:rtl_op_set_key():<0-0> Disabling hardware based encryption for keyidx: 1, mac: <MAC address removed>
[ 2000.592522] rtlwifi-0:rtl_op_set_key():<0-0> alg:CCMP
[ 2000.592524] rtlwifi-0:rtl_op_set_key():<0-0> disable key delete one entry
[ 2000.592525] rtlwifi-0:rtl_cam_delete_one_entry():<0-0> key_idx:1
[ 2000.592883] rtlwifi-0:rtl_cam_delete_one_entry():<0-0> rtl_cam_delete_one_entry(): WRITE A4: 0
[ 2000.592884] rtlwifi-0:rtl_cam_delete_one_entry():<0-0> rtl_cam_delete_one_entry(): WRITE A0: 80010008
[ 2001.633799] wlan1: authenticate with <MAC address removed>
[ 2001.668723] rtlwifi-0:rtl_op_bss_info_changed():<0-0> bssid: <MAC address removed>
[ 2001.669178] wlan1: send auth to <MAC address removed> (try 1/3)
[ 2001.669194] rtlwifi-0:rtl_tx_mgmt_proc():<200-1> MAC80211_LINKING
[ 2001.672190] wlan1: authenticated
[ 2001.677300] wlan1: associate with <MAC address removed> (try 1/3)
[ 2001.682012] wlan1: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=1)
[ 2001.682025] rtlwifi-0:rtl_op_sta_add():<0-0> Add sta addr is <MAC address removed>
[ 2001.682032] rtl8192ee-0:rtl92ee_update_hal_rate_mask():<0-0> ratr_bitmap :ffff005
[ 2001.682036] rtl8192ee-0:rtl92ee_update_hal_rate_mask():<0-0> Rate_index:2, ratr_val:ffff005, 0:82:0:5:f0:ff:f
[ 2001.682404] rtlwifi-0:rtl_action_proc():<10000-1> Rx ACT_ADDBAREQ From :<MAC address removed>
[ 2001.682408] rtlwifi:
[ 2001.682458] rtlwifi-0:rtl_action_proc():<10000-1> sta is NULL
[ 2001.683186] rtl8192ee-0:rtl92ee_update_hal_rate_mask():<0-0> ratr_bitmap :ffff005
[ 2001.683190] rtl8192ee-0:rtl92ee_update_hal_rate_mask():<0-0> Rate_index:2, ratr_val:ffff005, 0:82:0:5:f0:ff:f
[ 2001.683929] rtlwifi-0:rtl_op_bss_info_changed():<0-0> BSS_CHANGED_ASSOC
[ 2001.684293] rtl8192ee-0:rtl92ee_set_hw_reg():<0-0> switch case not process 5b
[ 2001.684499] rtlwifi-0:rtl_action_proc():<10000-1> Rx ACT_ADDBAREQ From :<MAC address removed>
[ 2001.684502] rtlwifi:
[ 2001.685107] rtl8192ee:
[ 2001.685110] In process "kworker/u16:0" (pid 4338):rtl92ee_set_fw_rsvdpagepkt(): HW_VAR_SET_TX_CMD: ALL
[ 2001.685122] rtl8192ee:
[ 2001.693480] rtl8192ee:
[ 2001.693484] In process "kworker/u16:0" (pid 4338):rtl92ee_set_fw_rsvdpagepkt(): HW_VAR_SET_TX_CMD: ALL
[ 2001.693497] rtl8192ee:
[ 2001.701858] rtl8192ee:
[ 2001.701864] In process "kworker/u16:0" (pid 4338):rtl92ee_set_fw_rsvdpagepkt(): HW_VAR_SET_TX_CMD: ALL
[ 2001.701879] rtl8192ee:
[ 2001.710236] rtl8192ee:
[ 2001.710241] In process "kworker/u16:0" (pid 4338):rtl92ee_set_fw_rsvdpagepkt(): HW_VAR_SET_TX_CMD: ALL
[ 2001.710254] rtl8192ee:
[ 2001.718592] rtl8192ee:
[ 2001.718595] In process "kworker/u16:0" (pid 4338):rtl92ee_set_fw_rsvdpagepkt(): HW_VAR_SET_TX_CMD: ALL
[ 2001.718609] rtl8192ee:
[ 2001.727212] wlan1: associated
[ 2001.727371] rtlwifi-0:rtl_rx_agg_start():<0-0> on ra = <MAC address removed> tid = 0 seq:0
[ 2001.727387] rtlwifi-0:rtl_action_proc():<200-1> Tx ACT_ADDBARSP From :<MAC address removed>
[ 2001.736017] rtlwifi-0:rtl_is_special_data():<10000-1> 802.1X Rx EAPOL pkt!!
[ 2001.737217] rtlwifi-0:rtl_is_special_data():<200-1> 802.1X Tx EAPOL pkt!!
[ 2001.737596] rtlwifi-0:rtl_is_special_data():<100-1> 802.1X Tx EAPOL pkt!!
[ 2001.744279] rtlwifi-0:rtl_is_special_data():<10000-1> 802.1X Rx EAPOL pkt!!
[ 2001.745019] rtlwifi-0:rtl_is_special_data():<200-1> 802.1X Tx EAPOL pkt!!
[ 2001.745406] rtlwifi-0:rtl_is_special_data():<100-1> 802.1X Tx EAPOL pkt!!
[ 2001.745597] rtlwifi-0:rtl_op_set_key():<0-0> Using hardware based encryption for keyidx: 0, mac: <MAC address removed>
[ 2001.745604] rtlwifi-0:rtl_op_set_key():<0-0> alg:CCMP
[ 2001.745608] rtlwifi-0:rtl_op_set_key():<0-0> set enable_hw_sec, key_type:4(OPEN:0 WEP40:1 TKIP:2 AES:4 WEP104:5)
[ 2001.745613] rtl8192ee-0:rtl92ee_enable_hw_security_config():<0-0> PairwiseEncAlgorithm = 4 GroupEncAlgorithm = 0
[ 2001.745960] rtl8192ee-0:rtl92ee_enable_hw_security_config():<0-0> The SECR-value cc
[ 2001.745966] rtlwifi-0:rtl_op_set_key():<0-0> set pairwise key
[ 2001.745970] rtl8192ee-0:rtl92ee_set_key():<0-0> add one entry
[ 2001.745974] rtl8192ee-0:rtl92ee_set_key():<0-0> set Pairwiase key
[ 2001.745978] rtlwifi-0:rtl_cam_add_one_entry():<0-0> EntryNo:4, ulKeyId=0, ulEncAlg=4, ulUseDK=0 MacAddr <MAC address removed>
[ 2001.745982] rtlwifi:
[ 2001.749423] rtlwifi-0:rtl_cam_add_one_entry():<0-0> end
[ 2001.749649] rtlwifi-0:rtl_op_set_key():<0-0> Using hardware based encryption for keyidx: 1, mac: <MAC address removed>
[ 2001.749655] rtlwifi-0:rtl_op_set_key():<0-0> alg:CCMP
[ 2001.749659] rtlwifi-0:rtl_op_set_key():<0-0> set group key
[ 2001.749663] rtl8192ee-0:rtl92ee_set_key():<0-0> add one entry
[ 2001.749666] rtl8192ee-0:rtl92ee_set_key():<0-0> set group key
[ 2001.749670] rtlwifi-0:rtl_cam_add_one_entry():<0-0> EntryNo:1, ulKeyId=1, ulEncAlg=4, ulUseDK=0 MacAddr <MAC address removed>
[ 2001.749674] rtlwifi:
[ 2001.752533] rtlwifi-0:rtl_cam_add_one_entry():<0-0> end
[ 2003.441154] rtlwifi-0:rtl_action_proc():<10000-1> Rx ACT_ADDBAREQ From :<MAC address removed>
[ 2003.441164] rtlwifi:
[ 2003.441836] rtlwifi-0:rtl_rx_agg_start():<0-0> on ra = <MAC address removed> tid = 1 seq:0
[ 2003.441860] rtlwifi-0:rtl_action_proc():<200-1> Tx ACT_ADDBARSP From :<MAC address removed>
[ 2008.355729] rtlwifi-0:rtl_tx_agg_start():<0-0> on ra = <MAC address removed> tid = 0 seq:4
[ 2008.355759] rtlwifi-0:rtl_action_proc():<200-1> Tx ACT_ADDBAREQ From :<MAC address removed>
[ 2008.355764] rtlwifi:
[ 2008.359816] rtlwifi-0:rtl_action_proc():<10000-1> Rx ACT_ADDBARSP From :<MAC address removed>
[ 2008.360405] rtlwifi-0:rtl_tx_agg_oper():<0-0> on ra = <MAC address removed> tid = 0
[ 2013.800624] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[ 2013.800634] rtl8192ee:
[ 2013.800637] In process "kworker/1:0" (pid 4343):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode
[ 2014.276971] rtlwifi-0:rtl_lps_set_psmode():<10000-1> FW LPS leave ps_mode:0
[ 2014.276986] rtl8192ee:
[ 2014.276989] In process "swapper/0" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode
[ 2031.826636] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[ 2031.826646] rtl8192ee:
[ 2031.826649] In process "kworker/1:0" (pid 4343):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode
[ 2033.184652] rtlwifi-0:rtl_lps_set_psmode():<500-1> FW LPS leave ps_mode:0
[ 2033.185008] rtl8192ee:
[ 2033.185012] In process "swapper/0" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode
[ 2043.843891] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[ 2043.843900] rtl8192ee:
[ 2043.843904] In process "kworker/1:0" (pid 4343):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode
[ 2045.398564] rtlwifi-0:rtl_lps_set_psmode():<10000-1> FW LPS leave ps_mode:0
[ 2045.398917] rtl8192ee:
[ 2045.398920] In process "swapper/0" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode
[ 2053.858359] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[ 2053.858373] rtl8192ee:
[ 2053.858378] In process "kworker/1:0" (pid 4343):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode
[ 2054.709910] rtlwifi-0:rtl_lps_set_psmode():<10100-1> FW LPS leave ps_mode:0
[ 2054.710263] rtl8192ee:
[ 2054.710266] In process "swapper/0" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode
[ 2057.864440] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[ 2057.864451] rtl8192ee:
[ 2057.864457] In process "kworker/1:0" (pid 4343):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode
[ 2064.935153] rtlwifi-0:rtl_lps_set_psmode():<10000-1> FW LPS leave ps_mode:0
[ 2064.935505] rtl8192ee:
[ 2064.935509] In process "swapper/0" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode
[ 2067.878516] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[ 2067.878526] rtl8192ee:
[ 2067.878529] In process "kworker/1:0" (pid 4343):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode
[ 2069.960024] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS leave ps_mode:0
[ 2069.960379] rtl8192ee:
[ 2069.960381] In process "wpa_supplicant" (pid 4532):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode
[ 2077.893004] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[ 2077.893015] rtl8192ee:
[ 2077.893018] In process "kworker/1:0" (pid 4343):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode
[ 2079.963772] rtlwifi-0:rtl_tx_agg_stop():<0-0> on ra = <MAC address removed> tid = 0
[ 2079.963791] rtlwifi-0:rtl_action_proc():<400-1> ACT_ADDBADEL From :<MAC address removed>
[ 2080.971300] rtlwifi-0:rtl_tx_agg_start():<0-0> on ra = <MAC address removed> tid = 0 seq:1540
[ 2080.971331] rtlwifi-0:rtl_action_proc():<200-1> Tx ACT_ADDBAREQ From :<MAC address removed>
[ 2080.971335] rtlwifi:
[ 2080.973578] rtlwifi-0:rtl_action_proc():<10000-1> Rx ACT_ADDBARSP From :<MAC address removed>
[ 2080.973882] rtlwifi-0:rtl_tx_agg_oper():<0-0> on ra = <MAC address removed> tid = 0
[ 2081.746777] rtlwifi-0:rtl_lps_set_psmode():<10000-1> FW LPS leave ps_mode:0
[ 2081.747132] rtl8192ee:
[ 2081.747135] In process "swapper/0" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode
[ 2083.178116] rtlwifi-0:rtl_tx_agg_start():<0-0> on ra = <MAC address removed> tid = 1 seq:3
[ 2083.178149] rtlwifi-0:rtl_action_proc():<200-1> Tx ACT_ADDBAREQ From :<MAC address removed>
[ 2083.178154] rtlwifi:
[ 2083.186412] rtlwifi-0:rtl_action_proc():<10000-1> Rx ACT_ADDBARSP From :<MAC address removed>
[ 2083.186825] rtlwifi-0:rtl_tx_agg_oper():<0-0> on ra = <MAC address removed> tid = 1
[ 2087.907359] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[ 2087.907369] rtl8192ee:
[ 2087.907373] In process "kworker/1:0" (pid 4343):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode
[ 2088.359267] rtlwifi-0:rtl_tx_agg_stop():<0-0> on ra = <MAC address removed> tid = 1
[ 2088.359310] rtlwifi-0:rtl_action_proc():<400-1> ACT_ADDBADEL From :<MAC address removed>
[ 2091.989240] rtlwifi-0:rtl_tx_agg_stop():<0-0> on ra = <MAC address removed> tid = 0
[ 2091.989292] rtlwifi-0:rtl_action_proc():<400-1> ACT_ADDBADEL From :<MAC address removed>
[ 2094.287881] rtlwifi-0:rtl_tx_agg_start():<0-0> on ra = <MAC address removed> tid = 0 seq:1567
[ 2094.287920] rtlwifi-0:rtl_action_proc():<200-1> Tx ACT_ADDBAREQ From :<MAC address removed>
[ 2094.287927] rtlwifi:
[ 2094.289876] rtlwifi-0:rtl_action_proc():<10000-1> Rx ACT_ADDBARSP From :<MAC address removed>
[ 2094.290319] rtlwifi-0:rtl_tx_agg_oper():<0-0> on ra = <MAC address removed> tid = 0
[ 2094.309273] rtlwifi-0:rtl_lps_set_psmode():<10000-1> FW LPS leave ps_mode:0
[ 2094.309634] rtl8192ee:
[ 2094.309638] In process "swapper/0" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode
[ 2097.921877] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[ 2097.921888] rtl8192ee:
[ 2097.921891] In process "kworker/1:0" (pid 4343):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode
[ 2103.950434] rtlwifi-0:rtl_tx_agg_stop():<0-0> on ra = <MAC address removed> tid = 0
[ 2103.950456] rtlwifi-0:rtl_action_proc():<400-1> ACT_ADDBADEL From :<MAC address removed>
[ 2104.290396] rtlwifi-0:rtl_tx_agg_start():<0-0> on ra = <MAC address removed> tid = 0 seq:1572
[ 2104.290447] rtlwifi-0:rtl_action_proc():<200-1> Tx ACT_ADDBAREQ From :<MAC address removed>
[ 2104.290455] rtlwifi:
[ 2104.293109] rtlwifi-0:rtl_action_proc():<10000-1> Rx ACT_ADDBARSP From :<MAC address removed>
[ 2104.293406] rtlwifi-0:rtl_tx_agg_oper():<0-0> on ra = <MAC address removed> tid = 0
[ 2104.774585] rtlwifi-0:rtl_lps_set_psmode():<10000-1> FW LPS leave ps_mode:0
[ 2104.774946] rtl8192ee:
[ 2104.774951] In process "swapper/0" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode
[ 2117.950634] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[ 2117.950638] rtl8192ee:
[ 2117.950639] In process "kworker/1:0" (pid 4343):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode
[ 2126.784983] rtlwifi-0:rtl_lps_set_psmode():<10000-1> FW LPS leave ps_mode:0
[ 2126.785336] rtl8192ee:
[ 2126.785339] In process "swapper/0" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode
[ 2129.967963] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[ 2129.967969] rtl8192ee:
[ 2129.967971] In process "kworker/1:0" (pid 4343):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode
[ 2132.734593] rtlwifi-0:rtl_tx_agg_stop():<0-0> on ra = <MAC address removed> tid = 0
[ 2132.734638] rtlwifi-0:rtl_action_proc():<400-1> ACT_ADDBADEL From :<MAC address removed>
[ 2134.749457] rtlwifi-0:rtl_tx_agg_start():<0-0> on ra = <MAC address removed> tid = 0 seq:1607
[ 2134.749491] rtlwifi-0:rtl_action_proc():<200-1> Tx ACT_ADDBAREQ From :<MAC address removed>
[ 2134.749498] rtlwifi:
[ 2134.751958] rtlwifi-0:rtl_action_proc():<10000-1> Rx ACT_ADDBARSP From :<MAC address removed>
[ 2134.752381] rtlwifi-0:rtl_tx_agg_oper():<0-0> on ra = <MAC address removed> tid = 0
[ 2141.570466] rtlwifi-0:rtl_lps_set_psmode():<10000-1> FW LPS leave ps_mode:0
[ 2141.570819] rtl8192ee:
[ 2141.570823] In process "swapper/0" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode
[ 2143.988263] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[ 2143.988273] rtl8192ee:
[ 2143.988277] In process "kworker/1:0" (pid 4343):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode
[ 2144.284090] rtlwifi-0:rtl_lps_set_psmode():<10000-1> FW LPS leave ps_mode:0
[ 2144.284104] rtl8192ee:
[ 2144.284108] In process "swapper/0" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode
[ 2147.994019] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[ 2147.994029] rtl8192ee:
[ 2147.994033] In process "kworker/1:0" (pid 4343):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode
[ 2149.781007] rtlwifi-0:rtl_tx_agg_stop():<0-0> on ra = <MAC address removed> tid = 0
[ 2149.781044] rtlwifi-0:rtl_action_proc():<400-1> ACT_ADDBADEL From :<MAC address removed>
[ 2149.861055] rtlwifi-0:rtl_tx_agg_start():<0-0> on ra = <MAC address removed> tid = 0 seq:1617
[ 2149.861107] rtlwifi-0:rtl_action_proc():<200-1> Tx ACT_ADDBAREQ From :<MAC address removed>
[ 2149.861119] rtlwifi:
[ 2149.863880] rtlwifi-0:rtl_action_proc():<10000-1> Rx ACT_ADDBARSP From :<MAC address removed>
[ 2149.864482] rtlwifi-0:rtl_tx_agg_oper():<0-0> on ra = <MAC address removed> tid = 0
[ 2153.163210] rtlwifi-0:rtl_tx_agg_start():<0-0> on ra = <MAC address removed> tid = 1 seq:5
[ 2153.163246] rtlwifi-0:rtl_action_proc():<200-1> Tx ACT_ADDBAREQ From :<MAC address removed>
[ 2153.163251] rtlwifi:
[ 2153.166825] rtlwifi-0:rtl_action_proc():<10100-1> Rx ACT_ADDBARSP From :<MAC address removed>
[ 2153.167467] rtlwifi-0:rtl_tx_agg_oper():<0-0> on ra = <MAC address removed> tid = 1
[ 2154.688905] rtlwifi-0:rtl_lps_set_psmode():<10000-1> FW LPS leave ps_mode:0
[ 2154.689264] rtl8192ee:
[ 2154.689268] In process "swapper/0" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode
[ 2158.308376] rtlwifi-0:rtl_tx_agg_stop():<0-0> on ra = <MAC address removed> tid = 1
[ 2158.308418] rtlwifi-0:rtl_action_proc():<400-1> ACT_ADDBADEL From :<MAC address removed>
[ 2160.011322] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[ 2160.011332] rtl8192ee:
[ 2160.011335] In process "kworker/1:0" (pid 4343):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode
[ 2163.141662] rtlwifi-0:rtl_tx_agg_stop():<0-0> on ra = <MAC address removed> tid = 0
[ 2163.141702] rtlwifi-0:rtl_action_proc():<400-1> ACT_ADDBADEL From :<MAC address removed>
[ 2164.257033] rtlwifi-0:rtl_tx_agg_start():<0-0> on ra = <MAC address removed> tid = 0 seq:1627
[ 2164.257067] rtlwifi-0:rtl_action_proc():<200-1> Tx ACT_ADDBAREQ From :<MAC address removed>
[ 2164.257072] rtlwifi:
[ 2164.261149] rtlwifi-0:rtl_action_proc():<10000-1> Rx ACT_ADDBARSP From :<MAC address removed>
[ 2164.261608] rtlwifi-0:rtl_tx_agg_oper():<0-0> on ra = <MAC address removed> tid = 0
[ 2164.679830] rtlwifi-0:rtl_lps_set_psmode():<10000-1> FW LPS leave ps_mode:0
[ 2164.680182] rtl8192ee:
[ 2164.680186] In process "swapper/0" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode
[ 2168.022810] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[ 2168.022815] rtl8192ee:
[ 2168.022818] In process "kworker/1:0" (pid 4343):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode
[ 2169.757954] rtlwifi-0:rtl_tx_agg_stop():<0-0> on ra = <MAC address removed> tid = 0
[ 2169.757996] rtlwifi-0:rtl_action_proc():<400-1> ACT_ADDBADEL From :<MAC address removed>
[ 2169.977793] rtlwifi-0:rtl_tx_agg_start():<0-0> on ra = <MAC address removed> tid = 0 seq:1629
[ 2169.977809] rtlwifi-0:rtl_action_proc():<200-1> Tx ACT_ADDBAREQ From :<MAC address removed>
[ 2169.977813] rtlwifi:
[ 2169.979927] rtlwifi-0:rtl_action_proc():<10100-1> Rx ACT_ADDBARSP From :<MAC address removed>
[ 2169.980312] rtlwifi-0:rtl_tx_agg_oper():<0-0> on ra = <MAC address removed> tid = 0
[ 2171.937265] rtlwifi-0:rtl_lps_set_psmode():<10000-1> FW LPS leave ps_mode:0
[ 2171.937617] rtl8192ee:
[ 2171.937620] In process "chromium-browse" (pid 3819):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode
[ 2194.725377] rtlwifi-0:rtl_action_proc():<10000-1> ACT_ADDBADEL From :<MAC address removed>
[ 2223.016363] rtlwifi-0:rtl_rx_agg_stop():<0-0> on ra = <MAC address removed> tid = 1
[ 2259.806809] rtlwifi-0:rtl_action_proc():<10000-1> Rx ACT_ADDBAREQ From :<MAC address removed>
[ 2259.806820] rtlwifi:
[ 2259.807287] rtlwifi-0:rtl_rx_agg_start():<0-0> on ra = <MAC address removed> tid = 1 seq:11
[ 2259.807309] rtlwifi-0:rtl_action_proc():<200-1> Tx ACT_ADDBARSP From :<MAC address removed>
[ 2278.181926] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[ 2278.181939] rtl8192ee:
[ 2278.181944] In process "kworker/1:0" (pid 4343):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode
[ 2278.741793] rtlwifi-0:rtl_lps_set_psmode():<10100-1> FW LPS leave ps_mode:0
[ 2278.742143] rtl8192ee:
[ 2278.742146] In process "swapper/0" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode
[ 2290.199320] rtlwifi-0:rtl_watchdog_wq_callback():<0-0> AP off for 2 s
[ 2292.202242] rtlwifi-0:rtl_watchdog_wq_callback():<0-0> AP off for 4 s
[ 2293.325151] rtlwifi-0:rtl_tx_agg_stop():<0-0> on ra = <MAC address removed> tid = 0
[ 2293.325206] rtlwifi-0:rtl_action_proc():<400-1> ACT_ADDBADEL From :<MAC address removed>
[ 2294.205109] rtlwifi-0:rtl_watchdog_wq_callback():<0-0> AP off for 6 s
[ 2296.207977] rtlwifi-0:rtl_watchdog_wq_callback():<0-0> AP off for 8 s
[ 2298.210437] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[ 2298.210446] rtl8192ee:
[ 2298.210450] In process "kworker/1:0" (pid 4343):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode
[ 2298.210815] rtlwifi-0:rtl_watchdog_wq_callback():<0-0> AP off for 10 s
[ 2298.210819] rtlwifi-0:rtl_watchdog_wq_callback():<0-0> AP off, try to reconnect now
[ 2298.210841] wlan1: Connection to AP <MAC address removed> lost
[ 2300.213641] rtlwifi-0:rtl_watchdog_wq_callback():<0-0> AP off for 2 s
[ 2302.216172] rtlwifi-0:rtl_watchdog_wq_callback():<0-0> AP off for 4 s
[ 2303.007745] rtlwifi-0:rtl_rx_agg_stop():<0-0> on ra = <MAC address removed> tid = 0
[ 2303.007761] rtlwifi-0:rtl_rx_agg_stop():<0-0> on ra = <MAC address removed> tid = 1
[ 2303.007816] rtlwifi-0:rtl_op_set_key():<0-0> Disabling hardware based encryption for keyidx: 0, mac: <MAC address removed>
[ 2303.007823] rtlwifi-0:rtl_op_set_key():<0-0> alg:CCMP
[ 2303.007827] rtlwifi-0:rtl_op_set_key():<0-0> set enable_hw_sec, key_type:4(OPEN:0 WEP40:1 TKIP:2 AES:4 WEP104:5)
[ 2303.007832] rtl8192ee-0:rtl92ee_enable_hw_security_config():<0-0> PairwiseEncAlgorithm = 4 GroupEncAlgorithm = 4
[ 2303.007840] rtl8192ee-0:rtl92ee_enable_hw_security_config():<0-0> The SECR-value cc
[ 2303.007847] rtlwifi-0:rtl_op_set_key():<0-0> disable key delete one entry
[ 2303.007851] rtlwifi-0:rtl_cam_delete_one_entry():<0-0> key_idx:0
[ 2303.007859] rtlwifi-0:rtl_cam_delete_one_entry():<0-0> rtl_cam_delete_one_entry(): WRITE A4: 0
[ 2303.007863] rtlwifi-0:rtl_cam_delete_one_entry():<0-0> rtl_cam_delete_one_entry(): WRITE A0: 80010000
[ 2303.007926] rtlwifi-0:rtl_op_sta_remove():<0-0> Remove sta addr is <MAC address removed>
[ 2303.008058] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS leave ps_mode:0
[ 2303.008068] rtl8192ee:
[ 2303.008071] In process "kworker/u16:0" (pid 4338):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode
[ 2303.011319] rtlwifi-0:_rtl_pci_interrupt():<10000-1> rx descriptor unavailable!
[ 2303.012151] rtlwifi-0:_rtl_pci_interrupt():<10000-1> rx overflow !
[ 2303.012765] rtlwifi-0:rtl_op_bss_info_changed():<0-0> BSS_CHANGED_UN_ASSOC
[ 2303.013121] rtl8192ee-0:rtl92ee_set_hw_reg():<0-0> switch case not process 1c
[ 2303.013130] rtl8192ee-0:rtl92ee_set_hw_reg():<0-0> switch case not process 1b
[ 2303.013143] rtlwifi-0:rtl_op_bss_info_changed():<0-0> bssid: <MAC address removed>
[ 2305.430413] rtlwifi-0:rtl_op_set_key():<0-0> Disabling hardware based encryption for keyidx: 1, mac: <MAC address removed>
[ 2305.430419] rtlwifi-0:rtl_op_set_key():<0-0> alg:CCMP
[ 2305.430421] rtlwifi-0:rtl_op_set_key():<0-0> disable key delete one entry
[ 2305.430423] rtlwifi-0:rtl_cam_delete_one_entry():<0-0> key_idx:1
[ 2305.430777] rtlwifi-0:rtl_cam_delete_one_entry():<0-0> rtl_cam_delete_one_entry(): WRITE A4: 0
[ 2305.430779] rtlwifi-0:rtl_cam_delete_one_entry():<0-0> rtl_cam_delete_one_entry(): WRITE A0: 80010008
[ 2311.265194] wlan1: authenticate with <MAC address removed>
[ 2313.696868] rtlwifi-0:rtl_op_bss_info_changed():<0-0> bssid: <MAC address removed>
[ 2313.697347] wlan1: send auth to <MAC address removed> (try 1/3)
[ 2313.697368] rtlwifi-0:rtl_tx_mgmt_proc():<200-1> MAC80211_LINKING
[ 2313.702915] wlan1: authenticated
[ 2313.705769] wlan1: associate with <MAC address removed> (try 1/3)
[ 2313.716117] wlan1: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=1)
[ 2313.716124] rtlwifi-0:rtl_op_sta_add():<0-0> Add sta addr is <MAC address removed>
[ 2313.716128] rtl8192ee-0:rtl92ee_update_hal_rate_mask():<0-0> ratr_bitmap :ffff005
[ 2313.716130] rtl8192ee-0:rtl92ee_update_hal_rate_mask():<0-0> Rate_index:2, ratr_val:ffff005, 0:82:0:5:f0:ff:f
[ 2313.716503] rtl8192ee-0:rtl92ee_update_hal_rate_mask():<0-0> ratr_bitmap :ffff005
[ 2313.716504] rtl8192ee-0:rtl92ee_update_hal_rate_mask():<0-0> Rate_index:2, ratr_val:ffff005, 0:82:0:5:f0:ff:f
[ 2313.716708] rtlwifi-0:rtl_op_bss_info_changed():<0-0> BSS_CHANGED_ASSOC
[ 2313.716724] rtl8192ee-0:rtl92ee_set_hw_reg():<0-0> switch case not process 5b
[ 2313.716743] rtl8192ee:
[ 2313.716745] In process "kworker/u16:4" (pid 155):rtl92ee_set_fw_rsvdpagepkt(): HW_VAR_SET_TX_CMD: ALL
[ 2313.716752] rtl8192ee:
[ 2313.718624] rtlwifi-0:rtl_action_proc():<10000-1> Rx ACT_ADDBAREQ From :<MAC address removed>
[ 2313.718627] rtlwifi:
[ 2313.726444] rtl8192ee:
[ 2313.726446] In process "kworker/u16:4" (pid 155):rtl92ee_set_fw_rsvdpagepkt(): HW_VAR_SET_TX_CMD: ALL
[ 2313.726453] rtl8192ee:
[ 2313.734701] rtl8192ee:
[ 2313.734704] In process "kworker/u16:4" (pid 155):rtl92ee_set_fw_rsvdpagepkt(): HW_VAR_SET_TX_CMD: ALL
[ 2313.734710] rtl8192ee:
[ 2313.742802] rtl8192ee:
[ 2313.742805] In process "kworker/u16:4" (pid 155):rtl92ee_set_fw_rsvdpagepkt(): HW_VAR_SET_TX_CMD: ALL
[ 2313.742813] rtl8192ee:
[ 2313.750955] rtl8192ee:
[ 2313.750958] In process "kworker/u16:4" (pid 155):rtl92ee_set_fw_rsvdpagepkt(): HW_VAR_SET_TX_CMD: ALL
[ 2313.750965] rtl8192ee:
[ 2313.759264] wlan1: associated
[ 2313.759284] rtlwifi-0:rtl_rx_agg_start():<0-0> on ra = <MAC address removed> tid = 0 seq:0
[ 2313.759294] rtlwifi-0:rtl_action_proc():<200-1> Tx ACT_ADDBARSP From :<MAC address removed>
[ 2313.763413] rtlwifi-0:rtl_is_special_data():<10000-1> 802.1X Rx EAPOL pkt!!
[ 2313.764610] rtlwifi-0:rtl_is_special_data():<200-1> 802.1X Tx EAPOL pkt!!
[ 2313.764996] rtlwifi-0:rtl_is_special_data():<100-1> 802.1X Tx EAPOL pkt!!
[ 2313.784016] rtlwifi-0:rtl_is_special_data():<10000-1> 802.1X Rx EAPOL pkt!!
[ 2313.784604] rtlwifi-0:rtl_is_special_data():<200-1> 802.1X Tx EAPOL pkt!!
[ 2313.785003] rtlwifi-0:rtl_is_special_data():<100-1> 802.1X Tx EAPOL pkt!!
[ 2313.785175] rtlwifi-0:rtl_op_set_key():<0-0> Using hardware based encryption for keyidx: 0, mac: <MAC address removed>
[ 2313.785187] rtlwifi-0:rtl_op_set_key():<0-0> alg:CCMP
[ 2313.785193] rtlwifi-0:rtl_op_set_key():<0-0> set enable_hw_sec, key_type:4(OPEN:0 WEP40:1 TKIP:2 AES:4 WEP104:5)
[ 2313.785201] rtl8192ee-0:rtl92ee_enable_hw_security_config():<0-0> PairwiseEncAlgorithm = 4 GroupEncAlgorithm = 0
[ 2313.785556] rtl8192ee-0:rtl92ee_enable_hw_security_config():<0-0> The SECR-value cc
[ 2313.785927] rtlwifi-0:rtl_op_set_key():<0-0> set pairwise key
[ 2313.785934] rtl8192ee-0:rtl92ee_set_key():<0-0> add one entry
[ 2313.785938] rtl8192ee-0:rtl92ee_set_key():<0-0> set Pairwiase key
[ 2313.785943] rtlwifi-0:rtl_cam_add_one_entry():<0-0> EntryNo:4, ulKeyId=0, ulEncAlg=4, ulUseDK=0 MacAddr <MAC address removed>
[ 2313.785949] rtlwifi:
[ 2313.788641] rtlwifi-0:rtl_cam_add_one_entry():<0-0> end
[ 2313.788903] rtlwifi-0:rtl_op_set_key():<0-0> Using hardware based encryption for keyidx: 1, mac: <MAC address removed>
[ 2313.788914] rtlwifi-0:rtl_op_set_key():<0-0> alg:CCMP
[ 2313.788920] rtlwifi-0:rtl_op_set_key():<0-0> set group key
[ 2313.788926] rtl8192ee-0:rtl92ee_set_key():<0-0> add one entry
[ 2313.788932] rtl8192ee-0:rtl92ee_set_key():<0-0> set group key
[ 2313.788938] rtlwifi-0:rtl_cam_add_one_entry():<0-0> EntryNo:1, ulKeyId=1, ulEncAlg=4, ulUseDK=0 MacAddr <MAC address removed>
[ 2313.788944] rtlwifi:
[ 2313.792051] rtlwifi-0:rtl_cam_add_one_entry():<0-0> end
[ 2316.112128] rtlwifi-0:rtl_action_proc():<10000-1> Rx ACT_ADDBAREQ From :<MAC address removed>
[ 2316.112137] rtlwifi:
[ 2316.112597] rtlwifi-0:rtl_rx_agg_start():<0-0> on ra = <MAC address removed> tid = 1 seq:0
[ 2316.112616] rtlwifi-0:rtl_action_proc():<200-1> Tx ACT_ADDBARSP From :<MAC address removed>
[ 2325.179421] rtlwifi-0:rtl_tx_agg_start():<0-0> on ra = <MAC address removed> tid = 0 seq:653
[ 2325.179437] rtlwifi-0:rtl_action_proc():<200-1> Tx ACT_ADDBAREQ From :<MAC address removed>
[ 2325.179440] rtlwifi:
[ 2325.184207] rtlwifi-0:rtl_action_proc():<10000-1> Rx ACT_ADDBARSP From :<MAC address removed>
[ 2325.184577] rtlwifi-0:rtl_tx_agg_oper():<0-0> on ra = <MAC address removed> tid = 0
[ 2338.720027] rtlwifi-0:rtl_tx_agg_start():<0-0> on ra = <MAC address removed> tid = 1 seq:2
[ 2338.720063] rtlwifi-0:rtl_action_proc():<200-1> Tx ACT_ADDBAREQ From :<MAC address removed>
[ 2338.720069] rtlwifi:
[ 2338.722657] rtlwifi-0:rtl_action_proc():<10000-1> Rx ACT_ADDBARSP From :<MAC address removed>
[ 2338.723062] rtlwifi-0:rtl_tx_agg_oper():<0-0> on ra = <MAC address removed> tid = 1
[ 2342.273886] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[ 2342.273895] rtl8192ee:
[ 2342.273899] In process "kworker/1:0" (pid 4343):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode
[ 2344.156904] rtlwifi-0:rtl_tx_agg_stop():<0-0> on ra = <MAC address removed> tid = 1
[ 2344.156940] rtlwifi-0:rtl_action_proc():<400-1> ACT_ADDBADEL From :<MAC address removed>
[ 2344.162470] rtlwifi-0:rtl_lps_set_psmode():<10000-1> FW LPS leave ps_mode:0
[ 2344.162795] rtl8192ee:
[ 2344.162798] In process "swapper/0" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode
[ 2348.282559] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[ 2348.282569] rtl8192ee:
[ 2348.282573] In process "kworker/1:0" (pid 4343):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode
[ 2350.042288] rtlwifi-0:rtl_lps_set_psmode():<500-1> FW LPS leave ps_mode:0
[ 2350.042478] rtl8192ee:
[ 2350.042479] In process "gdbus" (pid 2063):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode
[ 2363.518281] rtlwifi-0:rtl_tx_agg_stop():<0-0> on ra = <MAC address removed> tid = 0
[ 2363.518313] rtlwifi-0:rtl_action_proc():<400-1> ACT_ADDBADEL From :<MAC address removed>
[ 2364.305684] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[ 2364.305698] rtl8192ee:
[ 2364.305703] In process "kworker/1:0" (pid 4343):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode
[ 2370.758099] rtlwifi-0:rtl_tx_agg_start():<0-0> on ra = <MAC address removed> tid = 0 seq:1605
[ 2370.758131] rtlwifi-0:rtl_action_proc():<200-1> Tx ACT_ADDBAREQ From :<MAC address removed>
[ 2370.758135] rtlwifi:
[ 2370.760326] rtlwifi-0:rtl_action_proc():<10000-1> Rx ACT_ADDBARSP From :<MAC address removed>
[ 2370.760740] rtlwifi-0:rtl_tx_agg_oper():<0-0> on ra = <MAC address removed> tid = 0
[ 2370.819930] rtlwifi-0:rtl_lps_set_psmode():<10000-1> FW LPS leave ps_mode:0
[ 2370.820472] rtl8192ee:
[ 2370.820473] In process "swapper/0" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode
[ 2376.322960] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[ 2376.322973] rtl8192ee:
[ 2376.322978] In process "kworker/1:0" (pid 4343):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode
[ 2378.941848] rtlwifi-0:rtl_lps_set_psmode():<300-1> FW LPS leave ps_mode:0
[ 2378.942203] rtl8192ee:
[ 2378.942207] In process "swapper/2" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode
[ 2382.331643] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[ 2382.331653] rtl8192ee:
[ 2382.331657] In process "kworker/1:0" (pid 4343):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode
[ 2385.505965] rtlwifi-0:rtl_tx_agg_stop():<0-0> on ra = <MAC address removed> tid = 0
[ 2385.506007] rtlwifi-0:rtl_action_proc():<400-1> ACT_ADDBADEL From :<MAC address removed>
[ 2388.867107] rtlwifi-0:rtl_lps_set_psmode():<10000-1> FW LPS leave ps_mode:0
[ 2388.867467] rtl8192ee:
[ 2388.867472] In process "swapper/0" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode
[ 2389.855457] rtlwifi-0:rtl_tx_agg_start():<0-0> on ra = <MAC address removed> tid = 0 seq:1629
[ 2389.855489] rtlwifi-0:rtl_action_proc():<200-1> Tx ACT_ADDBAREQ From :<MAC address removed>
[ 2389.855496] rtlwifi:
[ 2389.860925] rtlwifi-0:rtl_action_proc():<10000-1> Rx ACT_ADDBARSP From :<MAC address removed>
[ 2389.861334] rtlwifi-0:rtl_tx_agg_oper():<0-0> on ra = <MAC address removed> tid = 0
[ 2392.346058] rtlwifi-0:rtl_lps_set_psmode():<0-0> FW LPS enter ps_mode:3
[ 2392.346071] rtl8192ee:
[ 2392.346077] In process "kworker/1:0" (pid 4343):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode
[ 2393.260743] rtlwifi-0:rtl_lps_set_psmode():<10000-1> FW LPS leave ps_mode:0
[ 2393.261095] rtl8192ee:
[ 2393.261098] In process "swapper/0" (pid 0):rtl92c_set_fw_pwrmode(): u1_h2c_set_pwrmode
[ 2395.060582] rtlwifi-0:rtl_tx_agg_stop():<0-0> on ra = <MAC address removed> tid = 0
[ 2395.060618] rtlwifi-0:rtl_action_proc():<400-1> ACT_ADDBADEL From :<MAC address removed>
[ 2395.676222] rtlwifi-0:rtl_tx_agg_start():<0-0> on ra = <MAC address removed> tid = 0 seq:1630
[ 2395.676245] rtlwifi-0:rtl_action_proc():<200-1> Tx ACT_ADDBAREQ From :<MAC address removed>
[ 2395.676250] rtlwifi:
[ 2395.679150] rtlwifi-0:rtl_action_proc():<10000-1> Rx ACT_ADDBARSP From :<MAC address removed>
[ 2395.679549] rtlwifi-0:rtl_tx_agg_oper():<0-0> on ra = <MAC address removed> tid = 0


****************** done ******************



```

---

### Post by varunendra on 2014-02-09
I think I'm desperately gonna need Dr. Chili's help with this one. :)

Your wireless-info report is one of the most interesting ones I've seen, partly because of the latest driver, and partly because of the settings and dmesg messages.

Suggestions however, are more or less the same, based on the following -
> **programmer-x said:**
> ```

wlan1     IEEE 802.11**[COLOR="#006400"]bg[/COLOR][COLOR="#FF0000"]n[/COLOR]**  ESSID:"Woody"
          Mode:Managed  Frequency:2.437 GHz  Access Point: <MAC address removed>   
          Bit Rate=**[COLOR="#FF0000"]144.4 Mb/s[/COLOR]**   AP20x-Power=20 dBm
....
....
rtl8192ee             139274  0 
**[COLOR="#FF0000"]btcoexist[/COLOR]**             105039  1 rtl8192ee
....
....
    *Woody:        Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 86 **[COLOR="#FF0000"]WPA WPA2[/COLOR]**
....
....
wlan1     Scan completed :
      Cell 01 - Address: <MAC address removed>
            **Channel:6**
            ....
            ....
            IE: IEEE 802.11i/**[COLOR="#006400"]WPA2 Version 1[/COLOR]**
            Group Cipher : **CCMP**
            ....
            IE: **[COLOR="#FF0000"]WPA Version 1[/COLOR]**
            Group Cipher : **[COLOR="#FF0000"]CCMP[/COLOR]**
....
....
filename:       /lib/modules/3.11.0-15-generic/kernel/drivers/net/wireless/rtlwifi/rtl8192ee/**rtl8192ee.ko**
firmware:       rtlwifi/rtl8192eefw.bin
....
parm:           swlps:bool
parm:           **swenc**:using hardware crypto (default 0 [hardware])
 (bool)
parm:           **ips**:using no link power save (default 1 is open)
 (bool)
parm:           **fwlps**:using linked fw control power save (default 1 is open)
 (bool)
....
....
[   12.447146] **[COLOR="#FF0000"]IPv6[/COLOR]**: ADDRCONF(NETDEV_UP): wlan0: link is not ready
....
[   25.626798] rtlwifi-0:rtl_op_set_key():<0-0> **[COLOR="#800000"]Using hardware based encryption[/COLOR]** for keyidx: 0, mac: <MAC address removed>
[   25.626801] rtlwifi-0:rtl_op_set_key():<0-0> alg:**CCMP**
[   25.626802] rtlwifi-0:rtl_op_set_key():<0-0> set enable_hw_sec, **key_type:[COLOR="#006400"]4[/COLOR]**(OPEN:0 WEP40:1 TKIP:2 **[COLOR="#006400"]AES:4[/COLOR]** WEP104:5)
....
[   37.379555] rtlwifi-0:rtl_lps_set_psmode():<0-0> **FW LPS enter ps_mode:[COLOR="#FF0000"]3[/COLOR]**
....
[   37.532256] rtlwifi-0:rtl_lps_set_psmode():<10000-1> **FW LPS leave ps_mode:[COLOR="#FF0000"]0[/COLOR]**
*[COLOR="#FF0000"]<then continuously fluctuating between ps_mode 3 and 0 throught the dmesg>[/COLOR]*
*<some of the interesting parts later might have been ignored>*
...

```

**1)** Unless your router is buggy, disabling N-channel (in other words, setting it to b/g mode only) shouldn't bring the whole network down, it should only reduce the speed from 150+Mb/s to 54 Mb/s. So... did you reboot the router after saving the change? Could you access its web interface from any system afterwards? Did it show **b/g-only** mode? Reboot the connected system(s) too after saving the changes, just to be extra sure.

**2)** Apart from trying the b/g-only mode again, simultaneously also change its encryption type to **pure WPA2-only with AES (CCMP)**. Currently you are using WPA/WPA2 mixed mode, which, according to my limited knowledge (which may have become rusty) depends upon **[COLOR="#FF0000"]TKIP[/COLOR]** for the WPA part. As such, these kind of routers surprise me when they allow AES (CCMP) only with the WPA/WPA2 mixed mode. _Keep this setting to pure WPA2-AES even if it doesn't seem to help_.

**3)** Another change you *should* (not necessary, but sometimes does the miracle) try is to change from channel 6 to channel 1 (or 11).

Make all of three changes above simultaneously > Save > reboot both the router and the system. If the network seems to go down again (to me, it would certify it a buggy router), revert the first change only, or the 3rd one also if seems to make things worse (otherwise keep it to channel 1 or 11). Keep the encryption to pure WPA2-AES as suggested.

Apart from the above changes in the router, try the following in Ubuntu -

**4)** To try switching from "Hardware based Encryption" to Software based encryption -
```
sudo modprobe -rv rtl8192ee
sudo modprobe -v rtl8192ee swenc=1
```

**5)** If the above doesn't help, then to try disabling the firmware control power-save mode -
```
sudo modprobe -rv rtl8192ee
sudo modprobe -v rtl8192ee fwlps=0
```

**6)** And to also disable "No-Link" power save mode -
```
sudo modprobe -rv rtl8192ee
sudo modprobe -v rtl8192ee fwlps=0 ips=0
```

**7)** If the above don't help, then try all three parameters simultaneously (to disable all power save modes, and use software based encryption)-
```
sudo modprobe -rv rtl8192ee
sudo modprobe -v rtl8192ee swenc=1 fwlps=0 ips=0
```
These will be temporary changes that would be lost at next boot. So try using the connection without rebooting after above parameter changes. If any of them seems to help, we can make it permanent.

And lastly, if none of the suggestions above could help, please post a fresh report of wireless_script with the recommended settings applied (the N-channel may be reverted if necessary). With that, please also post the output of the following separately -
```
modinfo btcoexist
```
(hmm.. never expected that 'Feature' could come as an independent driver, hmm..)

**EDIT:** Oh, and did you also try Completely disabling IPv6 as per the post I linked to? Perhaps not much significant here, but just to eliminate the usual suspects..

**PS:**
Dr. Chili, help!!

---

### Post by chili555 on 2014-02-09
I think your suggestions are all quite correct, Varun. I might just look in the log to see what the driver and NM are doing at this time.```
cat /var/log/syslog | grep -e rtl -e etwork | tail -n20
```> For couple of times I got too many Invalid misc:I don't think that's terribly serious, unless you are losing data. Are you?

My wireless is, as far as I am concerned, near perfect. It says:> wlan0     IEEE 802.11abgn  ESSID:"my_router"  
          Mode:Managed  Frequency:5.805 GHz  Access Point: xx:D7:19:41:54:xx
          Bit Rate=108 Mb/s   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=50/70  Signal level=-60 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          [COLOR="#FF0000"]Tx excessive retries:3919  Invalid misc:119  [/COLOR] Missed beacon:0

---

### Post by programmer-x on 2014-02-10
Thanks for the help Ubuntians. Appreciated. 

I did try what Varun suggested by disabling hw encryption, ips, fwlps. Didnt help. Right now, I've loaded RTL8192EE on separate ubuntu installation so that my current wont be affected. Also, since this driver also new and not ready, will it brick the hardware by anychance ?.

---

### Post by chili555 on 2014-02-10
> since this driver also new and not ready, will it brick the hardware by anychance ?While anything is theoretically possible, I highly doubt it. I have never seen it in my brief career.

---

### Post by chris-ostrouchov on 2014-09-09
I want to confirm that the wifi works in Ubuntu 14.10 (I am running the beta version) on the "Network controller: Realtek Semiconductor Co., Ltd. RTL8192EE PCIe Wireless Network Adapter" which is what people are having issues with for the lenovo t440s

---

### Post by dangillmor on 2014-10-25
Confirmed: I did the 14.10 update and it now works. Thank you to the folks who made this happen.

---

### Post by damianonly on 2014-10-27
That is interesting. Which kernel versions are you guys using? Is the r8192ee module in use?

Under Ubuntu 14.04 with custom kernel 3.16.2-031602-generic and the drivers from [https://github.com/lwfinger/rtlwifi_new/]("https://github.com/lwfinger/rtlwifi_new/") I cannot get the wireless to work properly (random disconnections, low speed, system freezes).

---

### Post by chili555 on 2014-10-27
> **damianonly said:**
> That is interesting. Which kernel versions are you guys using? Is the r8192ee module in use?

Under Ubuntu 14.04 with custom kernel 3.16.2-031602-generic and the drivers from [https://github.com/lwfinger/rtlwifi_new/]("https://github.com/lwfinger/rtlwifi_new/") I cannot get the wireless to work properly (random disconnections, low speed, system freezes).The latest kernel in 14.10 is:```
$ uname -r
3.16.0-23-generic
```Did you try the upgrade?

There are three branches at the github. Which did you try? (Hint, hint!)

---

### Post by damianonly on 2014-10-29
> Did you try the upgrade?
No I haven't. My first idea was to wait till the 14.10 release became a bit stable, but what the hell, I'm running an experimental kernel with experimental drivers under ubuntu 14.04, so I might as well give 14.10 a try. 

>  There are three branches at the github. Which did you try? (Hint, hint!) 
I overlooked that! I tried only the master branch. I could give the other ones a try, though I wouldn't know which one to use. The ``troy`` branch seems to be the one used by the Realtek engineer, so it may be ondergoing heavy development.

---

### Post by chili555 on 2014-10-29
I would try both. The nice thing about compiling from source code is that, until you 'sudo make install,' everything is a trial run confined to the folder where you are running 'make.' You can see if you get errors or warnings before you install. You can even install it, reboot and try it and, if it's unsatisfactory, 'sudo make uninstall.'

*kernel-version* builds with one small warning on my 14.10 system. I haven't the device, so I can test no further.

---

### Post by damianonly on 2014-10-29
> **chili555 said:**
> I would try both. The nice thing about compiling from source code is that, until you 'sudo make install,' everything is a trial run confined to the folder where you are running 'make.' You can see if you get errors or warnings before you install. You can even install it, reboot and try it and, if it's unsatisfactory, 'sudo make uninstall.'

*kernel-version* builds with one small warning on my 14.10 system. I haven't the device, so I can test no further.

I'll try first the other two branches, and if that does not work I'll upgrade to 14.10.

---

### Post by christos-dimitrakakis on 2014-11-20
Actually, on my thinkpad L440, it seems to not be working either. I have the same controller, 8192ee, and the 3.16.0-24-generic kernel shipped with ubuntu 14.10 doesn't seem to work. It connects to a wifi, but the connection is dropped.

---

### Post by christos-dimitrakakis on 2014-11-20
More info on L440 with 8192ee, ubuntu 14.10, 3.16.0-24-generic. I tried all combinations of ipv6, software encryption, powersave, etc, to no avail. Here's a dmsg log during my attempts. I keep getting connected and disconnected. I also tried to connect to an open wifi - same problems.

[  379.368861] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  389.447113] wlan0: authenticate with ec:43:f6:37:33:a4
[  389.463847] wlan0: direct probe to ec:43:f6:37:33:a4 (try 1/3)
[  389.665353] wlan0: send auth to ec:43:f6:37:33:a4 (try 2/3)
[  389.668011] wlan0: authenticated
[  394.475639] wlan0: aborting authentication with ec:43:f6:37:33:a4 by local choice (Reason: 3=DEAUTH_LEAVING)
[  404.612327] wlan0: authenticate with ec:43:f6:37:33:a4
[  404.629147] wlan0: send auth to ec:43:f6:37:33:a4 (try 1/3)
[  404.630974] wlan0: authenticated
[  409.636074] wlan0: aborting authentication with ec:43:f6:37:33:a4 by local choice (Reason: 3=DEAUTH_LEAVING)
[  420.168966] wlan0: authenticate with ec:43:f6:37:33:a4
[  420.185814] wlan0: send auth to ec:43:f6:37:33:a4 (try 1/3)
[  420.188718] wlan0: authenticated
[  436.239609] wlan0: authenticate with ec:43:f6:37:33:a4
[  436.256366] wlan0: send auth to ec:43:f6:37:33:a4 (try 1/3)
[  436.259007] wlan0: authenticated
[  441.264860] wlan0: aborting authentication with ec:43:f6:37:33:a4 by local choice (Reason: 3=DEAUTH_LEAVING)
[  452.559212] wlan0: authenticate with ec:43:f6:37:33:a4
[  452.575991] wlan0: send auth to ec:43:f6:37:33:a4 (try 1/3)
[  452.578680] wlan0: authenticated
[  662.890342] cfg80211: Calling CRDA to update world regulatory domain
[  662.893359] cfg80211: World regulatory domain updated:
[  662.893363] cfg80211:  DFS Master region: unset
[  662.893364] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp), (dfs_cac_time)
[  662.893366] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm), (N/A)
[  662.893368] cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (300 mBi, 2000 mBm), (N/A)
[  662.893369] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm), (N/A)
[  662.893370] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm), (N/A)
[  662.893371] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm), (N/A)
[  662.906872] r8192ee: module is from the staging directory, the quality is unknown, you have been warned.
[  662.908148] mem mapped space: start: 0xf2400000 len:00004000 flags:00140204, after map:0xffffc900047b8000
[  662.908161] Pci Bridge Vendor is found index: 0
[  662.908163] pcidev busnumber:devnumber:funcnumber:vendor:link_ctl 2:0:0:10ec:0
[  662.908165] pci_bridge busnumber:devnumber:funcnumber:vendor:pcie_cap:link_ctl_reg:amd 0:28:1:8086:40:40:0
[  662.908190] Boot from EFUSE
[  662.915579] dev_addr: 38:b1:db:5e:e2:79
[  662.915588] RT Customized ID: 0x12
[  662.916653] ieee80211 phy0: Selected rate control algorithm 'minstrel_ht'
[  662.916998] cfg80211: Calling CRDA for country: EC
[  662.917031] rtlwifi: wireless switch is on
[  662.917164] r8192ee 0000:02:00.0: irq 47 for MSI/MSI-X
[  663.614017] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  663.614100] cfg80211: Regulatory domain changed to country: EC
[  663.614102] cfg80211:  DFS Master region: unset
[  663.614103] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp), (dfs_cac_time)
[  663.614105] cfg80211:   (2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A, 2000 mBm), (N/A)
[  663.614107] cfg80211:   (5170000 KHz - 5250000 KHz @ 20000 KHz), (300 mBi, 1700 mBm), (N/A)
[  663.614108] cfg80211:   (5250000 KHz - 5330000 KHz @ 20000 KHz), (300 mBi, 2300 mBm), (0 s)
[  663.614110] cfg80211:   (5735000 KHz - 5835000 KHz @ 20000 KHz), (300 mBi, 3000 mBm), (N/A)
[  729.871478] wlan0: authenticate with ec:43:f6:37:33:a4
[  729.888283] wlan0: direct probe to ec:43:f6:37:33:a4 (try 1/3)
[  730.090131] wlan0: send auth to ec:43:f6:37:33:a4 (try 2/3)
[  730.092155] wlan0: authenticated
[  734.893752] wlan0: aborting authentication with ec:43:f6:37:33:a4 by local choice (Reason: 3=DEAUTH_LEAVING)
[  745.021503] wlan0: authenticate with ec:43:f6:37:33:a4
[  745.038453] wlan0: send auth to ec:43:f6:37:33:a4 (try 1/3)
[  745.040283] wlan0: authenticated
[  749.883961] wlan0: aborting authentication with ec:43:f6:37:33:a4 by local choice (Reason: 3=DEAUTH_LEAVING)
[  770.357348] systemd-hostnamed[3136]: Warning: nss-myhostname is not installed. Changing the local hostname might make it unresolveable. Please install nss-myhostname!
[  813.443749] wlan0: authenticate with ec:43:f6:37:33:a4
[  813.460482] wlan0: send auth to ec:43:f6:37:33:a4 (try 1/3)
[  813.462576] wlan0: authenticated
[  818.465406] wlan0: aborting authentication with ec:43:f6:37:33:a4 by local choice (Reason: 3=DEAUTH_LEAVING)
[  831.968046] wlan0: authenticate with ec:43:f6:37:33:a4
[  831.984805] wlan0: send auth to ec:43:f6:37:33:a4 (try 1/3)
[  831.986729] wlan0: authenticated
[  836.992125] wlan0: aborting authentication with ec:43:f6:37:33:a4 by local choice (Reason: 3=DEAUTH_LEAVING)
[  848.023322] wlan0: authenticate with ec:43:f6:37:33:a4
[  848.040147] wlan0: send auth to ec:43:f6:37:33:a4 (try 1/3)
[  848.042752] wlan0: authenticated
[  866.981483] wlan0: authenticate with ec:43:f6:37:33:a4
[  866.998194] wlan0: send auth to ec:43:f6:37:33:a4 (try 1/3)
[  867.000524] wlan0: authenticated
[  872.004563] wlan0: aborting authentication with ec:43:f6:37:33:a4 by local choice (Reason: 3=DEAUTH_LEAVING)
[  873.852553] cfg80211: Calling CRDA to update world regulatory domain
[  873.855638] cfg80211: World regulatory domain updated:
[  873.855642] cfg80211:  DFS Master region: unset
[  873.855644] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp), (dfs_cac_time)
[  873.855647] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm), (N/A)
[  873.855649] cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (300 mBi, 2000 mBm), (N/A)
[  873.855651] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm), (N/A)
[  873.855653] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm), (N/A)
[  873.855655] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm), (N/A)
[  873.868646] r8192ee: module is from the staging directory, the quality is unknown, you have been warned.
[  873.869916] mem mapped space: start: 0xf2400000 len:00004000 flags:00140204, after map:0xffffc900047b8000
[  873.869929] Pci Bridge Vendor is found index: 0
[  873.869932] pcidev busnumber:devnumber:funcnumber:vendor:link_ctl 2:0:0:10ec:0
[  873.869933] pci_bridge busnumber:devnumber:funcnumber:vendor:pcie_cap:link_ctl_reg:amd 0:28:1:8086:40:40:0
[  873.869971] Boot from EFUSE
[  873.877556] dev_addr: 38:b1:db:5e:e2:79
[  873.877564] RT Customized ID: 0x12
[  873.877756] 1T2R or 2T2R
[  873.878495] ieee80211 phy0: Selected rate control algorithm 'minstrel_ht'
[  873.878791] cfg80211: Calling CRDA for country: EC
[  873.878822] rtlwifi: wireless switch is on
[  873.878948] r8192ee 0000:02:00.0: irq 47 for MSI/MSI-X
[  873.879040] MSI Interrupt Mode!
[  873.881459]  rtl_pci_start
[  873.881463] rtl92e_btc_init_hal_vars, antNum is 2
[  873.881464] rtl92e_btc_init_hal_vars, bt_exist is 1
[  873.881465] rtl92e_btc_init_hal_vars, bt_type is 9
[  873.887286] normal Firmware SIZE 32754
[  873.887290] Firmware Version(14), Signature(0x92e1), Size(32)
[  874.399102] PairwiseEncAlgorithm = 0 GroupEncAlgorithm = 0
[  874.399105] not open hw encryption
[  874.558435] rtl_pci_start OK
[  874.575250] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  874.575273] cfg80211: Regulatory domain changed to country: EC
[  874.575275] cfg80211:  DFS Master region: unset
[  874.575277] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp), (dfs_cac_time)
[  874.575280] cfg80211:   (2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A, 2000 mBm), (N/A)
[  874.575282] cfg80211:   (5170000 KHz - 5250000 KHz @ 20000 KHz), (300 mBi, 1700 mBm), (N/A)
[  874.575284] cfg80211:   (5250000 KHz - 5330000 KHz @ 20000 KHz), (300 mBi, 2300 mBm), (0 s)
[  874.575286] cfg80211:   (5735000 KHz - 5835000 KHz @ 20000 KHz), (300 mBi, 3000 mBm), (N/A)
[  884.647194] wlan0: authenticate with ec:43:f6:37:33:a4
[  884.663865] bssid: ec:43:f6:37:33:a4
[  884.663922] wlan0: send auth to ec:43:f6:37:33:a4 (try 1/3)
[  884.663930] MAC80211_LINKING
[  884.665799] wlan0: authenticated
[  889.674978] bssid: 00:00:00:00:00:00
[  899.806160] wlan0: authenticate with ec:43:f6:37:33:a4
[  899.822908] bssid: ec:43:f6:37:33:a4
[  899.822965] wlan0: send auth to ec:43:f6:37:33:a4 (try 1/3)
[  899.822974] MAC80211_LINKING
[  899.824727] wlan0: authenticated
[  904.827413] wlan0: aborting authentication with ec:43:f6:37:33:a4 by local choice (Reason: 3=DEAUTH_LEAVING)

---

### Post by Peter_Warwick-Maho on 2014-11-24
I can confirm updating from 14.04 to 14.10 fixed this issue on my own Thinkpad T440p.

As an aside, the update did wreck havoc with my boot loader, and I had to resolve it via a live cd.

However, it was worth the 15 minutes of inconvenience to get the wifi sorted.

---

