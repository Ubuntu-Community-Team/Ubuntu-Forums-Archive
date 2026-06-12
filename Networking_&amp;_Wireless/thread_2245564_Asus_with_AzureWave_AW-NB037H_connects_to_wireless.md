---
title: "Asus with AzureWave AW-NB037H connects to wireless network but has no internet"
date: 2014-09-24
forum: Networking &amp; Wireless
---

### Post by sebastin2 on 2014-09-24
Hi

I'm having some trouble connecting this computer to the internet in a particular place, the wireless connection seems fine, the computer connects to the wireless network successfully, but when i try to access a page to the browser or ping an ip it doesn't work (the webpage displays an error, and the ping says I'm not connected, i think that is what it said). The internet connection in the same place works fine using a cable, and also the wireless connection works on other places, I can access internet from my house using the wireless connection.

Below is the result of the wireless script:

```


########## wireless info START ##########


Report from: 24 Sep 2014 10:57 COT -0500


Script from: 05 Sep 2014 22:42 UTC +0000


##### release #####


Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.1 LTS
Release:    14.04
Codename:    trusty


##### kernel #####


Linux 3.13.0-35-generic #62-Ubuntu SMP Fri Aug 15 01:58:42 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux


Parameters: ro, quiet, splash, vt.handoff=7


##### desktop #####


Ubuntu


##### lspci #####


02:00.0 Network controller [0280]: Qualcomm Atheros AR9285 Wireless Network Adapter (PCI-Express) [168c:002b] (rev 01)
    Subsystem: AzureWave AW-NB037H 802.11bgn Wireless Half-size Mini PCIe Card [AR9002WB-1NGCD] [1a3b:2c37]
    Kernel driver in use: ath9k


03:00.0 Ethernet controller [0200]: Qualcomm Atheros AR8151 v2.0 Gigabit Ethernet [1969:1083] (rev c0)
    Subsystem: ASUSTeK Computer Inc. Device [1043:1851]
    Kernel driver in use: atl1c


##### lsusb #####


Bus 002 Device 003: ID 0458:003a KYE Systems Corp. (Mouse Systems) NetScroll+ Mini Traveler / Genius NetScroll 120
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 004: ID 13d3:5120 IMC Networks 
Bus 001 Device 005: ID 0cf3:3005 Atheros Communications, Inc. AR3011 Bluetooth
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


##### PCMCIA card info #####


##### rfkill #####


0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: asus-wlan: Wireless LAN
    Soft blocked: no
    Hard blocked: no
2: asus-bluetooth: Bluetooth
    Soft blocked: yes
    Hard blocked: no
3: hci0: Bluetooth
    Soft blocked: yes
    Hard blocked: no


##### lsmod #####


asus_nb_wmi            16990  0 
asus_wmi               24191  1 asus_nb_wmi
sparse_keymap          13948  1 asus_wmi
ath9k                 164164  0 
ath9k_common           13551  1 ath9k
ath9k_hw              453856  2 ath9k_common,ath9k
ath                    28698  3 ath9k_common,ath9k,ath9k_hw
mac80211              630653  1 ath9k
ath3k                  13318  0 
bluetooth             391136  23 bnep,ath3k,btusb,rfcomm
cfg80211              484040  3 ath,ath9k,mac80211
wmi                    19177  1 asus_wmi
video                  19476  2 i915,asus_wmi


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
          inet6 addr: fdae:4b8f:9c0b:1:f4a7:613c:8308:23da/64 Scope:Global
          inet6 addr: fdae:4b8f:9c0b:1:e2b9:a5ff:fe9a:ac22/64 Scope:Global
          inet6 addr: fe80::e2b9:a5ff:fe9a:ac22/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:227 errors:0 dropped:30 overruns:0 frame:0
          TX packets:242 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:22429 (22.4 KB)  TX bytes:74430 (74.4 KB)


##### iwconfig #####


eth0      no wireless extensions.


lo        no wireless extensions.


wlan0     IEEE 802.11bgn  ESSID:"Movistar_18575724"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: <MAC addr Movistar_18575724>   
          Bit Rate=9 Mb/s   Tx-Power=16 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=56/70  Signal level=-54 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:12   Missed beacon:0


##### route #####


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface


##### resolv.conf #####


nameserver 127.0.1.1
search home


##### nm-tool #####


NetworkManager Tool


State: connected (global)


- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            atl1c
  State:             unavailable
  Default:           no
  HW Address:        <MAC addr eth0>


  Capabilities:
    Carrier Detect:  yes


  Wired Properties
    Carrier:         off


- Device: wlan0  [Movistar_18575724] -------------------------------------------
  Type:              802.11 WiFi
  Driver:            ath9k
  State:             connected
  Default:           no
  HW Address:        <MAC addr wlan0>


  Capabilities:
    Speed:           54 Mb/s


  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes


  Wireless Access Points (* = current AP)
    Movistar_18575089: Infra, <MAC addr Movistar_18575089>, Freq 2422 MHz, Rate 54 Mb/s, Strength 64 WPA
    netdocom:        Infra, <MAC addr netdocom>, Freq 2447 MHz, Rate 54 Mb/s, Strength 52 WPA2
    Movistar_18575202: Infra, <MAC addr Movistar_18575202>, Freq 2437 MHz, Rate 54 Mb/s, Strength 27 WPA
    FamiliaPe2014:   Infra, <MAC addr FamiliaPe2014>, Freq 2412 MHz, Rate 54 Mb/s, Strength 17 WPA WPA2
    Familia Infante: Infra, <MAC addr Familia Infante>, Freq 2452 MHz, Rate 54 Mb/s, Strength 27 WPA
    REYES GARCIA:    Infra, <MAC addr REYES GARCIA>, Freq 2462 MHz, Rate 54 Mb/s, Strength 14 WPA
    *Movistar_18575724: Infra, <MAC addr Movistar_18575724>, Freq 2412 MHz, Rate 54 Mb/s, Strength 71 WPA


  IPv6 Settings:
    Address:         fdae:4b8f:9c0b:1:f4a7:613c:8308:23da
    Prefix:          64
    Gateway:         ::


    Address:         fdae:4b8f:9c0b:1:e2b9:a5ff:fe9a:ac22
    Prefix:          64
    Gateway:         ::


    Address:         fe80::e2b9:a5ff:fe9a:ac22
    Prefix:          64
    Gateway:         ::


    DNS:             fdae:4b8f:9c0b:1:7eb7:33ff:fe0e:76d1


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


no-auto-default=<MAC addr eth0>,


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
          Current Frequency:2.412 GHz (Channel 1)


##### iwlist scan #####


Channel occupancy:


     2   WLAPs on   Frequency:2.412 GHz (Channel 1)
     1   WLAPs on   Frequency:2.422 GHz (Channel 3)
     1   WLAPs on   Frequency:2.437 GHz (Channel 6)
     1   WLAPs on   Frequency:2.447 GHz (Channel 8)


no talloc stackframe at ../source3/param/loadparm.c:4864, leaking memory
WARNING: Ignoring invalid value 'share' for parameter 'security'
eth0      Interface doesn't support scanning.


lo        Interface doesn't support scanning.


wlan0     Scan completed :
          Cell 01 - Address: <MAC addr Movistar_18575724>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=60/70  Signal level=-50 dBm  
                    Encryption key:on
                    ESSID:"Movistar_18575724"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000008c6848cbf1
                    Extra: Last beacon: 68ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC addr Movistar_18575089>
                    Channel:3
                    Frequency:2.422 GHz (Channel 3)
                    Quality=51/70  Signal level=-59 dBm  
                    Encryption key:on
                    ESSID:"Movistar_18575089"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000ae6c50d92
                    Extra: Last beacon: 68ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: <MAC addr Movistar_18575202>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=31/70  Signal level=-79 dBm  
                    Encryption key:on
                    ESSID:"Movistar_18575202"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000011b0644d8e
                    Extra: Last beacon: 68ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
          Cell 04 - Address: <MAC addr netdocom>
                    Channel:8
                    Frequency:2.447 GHz (Channel 8)
                    Quality=37/70  Signal level=-73 dBm  
                    Encryption key:on
                    ESSID:"netdocom"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000018e96561180
                    Extra: Last beacon: 1608ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 05 - Address: <MAC addr FamiliaPe2014>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=19/70  Signal level=-91 dBm  
                    Encryption key:on
                    ESSID:"FamiliaPe2014"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000001f2936e5161
                    Extra: Last beacon: 192ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK


##### module infos #####


[ath9k]
filename:       /lib/modules/3.13.0-35-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k.ko
license:        Dual BSD/GPL
description:    Support for Atheros 802.11n wireless LAN cards.
author:         Atheros Communications
srcversion:     DF02272C2FA4678C49046E5
depends:        ath9k_hw,mac80211,ath9k_common,cfg80211,ath
intree:         Y
vermagic:       3.13.0-35-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        B1:41:4A:E9:6C:1B:0E:BB:7C:14:1F:A4:05:C1:F6:C9:8E:8A:66:F0
sig_hashalgo:   sha512
parm:           debug:Debugging mask (uint)
parm:           nohwcrypt:Disable hardware encryption (int)
parm:           blink:Enable LED blink on activity (int)
parm:           btcoex_enable:Enable wifi-BT coexistence (int)
parm:           bt_ant_diversity:Enable WLAN/BT RX antenna diversity (int)
parm:           ps_enable:Enable WLAN PowerSave (int)


[ath9k_common]
filename:       /lib/modules/3.13.0-35-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_common.ko
license:        Dual BSD/GPL
description:    Shared library for Atheros wireless 802.11n LAN cards.
author:         Atheros Communications
srcversion:     696B00A6C59713EC0966997
depends:        ath,ath9k_hw
intree:         Y
vermagic:       3.13.0-35-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        B1:41:4A:E9:6C:1B:0E:BB:7C:14:1F:A4:05:C1:F6:C9:8E:8A:66:F0
sig_hashalgo:   sha512


[ath9k_hw]
filename:       /lib/modules/3.13.0-35-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_hw.ko
license:        Dual BSD/GPL
description:    Support for Atheros 802.11n wireless LAN cards.
author:         Atheros Communications
srcversion:     4809F3842A0542CD6B556D3
depends:        ath
intree:         Y
vermagic:       3.13.0-35-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        B1:41:4A:E9:6C:1B:0E:BB:7C:14:1F:A4:05:C1:F6:C9:8E:8A:66:F0
sig_hashalgo:   sha512


[ath]
filename:       /lib/modules/3.13.0-35-generic/kernel/drivers/net/wireless/ath/ath.ko
license:        Dual BSD/GPL
description:    Shared library for Atheros wireless LAN cards.
author:         Atheros Communications
srcversion:     88A67C5359B02C5A710AFCF
depends:        cfg80211
intree:         Y
vermagic:       3.13.0-35-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        B1:41:4A:E9:6C:1B:0E:BB:7C:14:1F:A4:05:C1:F6:C9:8E:8A:66:F0
sig_hashalgo:   sha512


[ath3k]
filename:       /lib/modules/3.13.0-35-generic/kernel/drivers/bluetooth/ath3k.ko
firmware:       ath3k-1.fw
license:        GPL
version:        1.0
description:    Atheros AR30xx firmware driver
author:         Atheros Communications
srcversion:     98A5245588C09E5E41690D0
depends:        bluetooth
intree:         Y
vermagic:       3.13.0-35-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        B1:41:4A:E9:6C:1B:0E:BB:7C:14:1F:A4:05:C1:F6:C9:8E:8A:66:F0
sig_hashalgo:   sha512


##### module parameters #####


[ath9k]
blink: 0
bt_ant_diversity: 0
btcoex_enable: 0
nohwcrypt: 1
ps_enable: 0


##### /etc/modules #####


loop
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
# PCI device 0x1969:/sys/devices/pci0000:00/0000:00:1c.5/0000:03:00.0 (atl1c)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC addr eth0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# PCI device 0x168c:/sys/devices/pci0000:00/0000:00:1c.1/0000:02:00.0 (ath9k)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC addr wlan0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"


##### dmesg #####


[    2.057490] psmouse serio4: elantech: assuming hardware version 3 (with firmware version 0x450f01)
[   22.308068] ath: phy0: Set BT/WLAN RX diversity capability
[   22.360233] ath: phy0: ASPM enabled: 0x42
[   22.360238] ath: EEPROM regdomain: 0x60
[   22.360240] ath: EEPROM indicates we should expect a direct regpair map
[   22.360244] ath: Country alpha2 being used: 00
[   22.360245] ath: Regpair used: 0x60
[   25.274283] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready (repeated 2 times)
[   26.439807] wlan0: authenticate with <MAC addr Movistar_18575724>
[   26.449416] wlan0: send auth to <MAC addr Movistar_18575724> (try 1/3)
[   26.451290] wlan0: authenticated
[   26.451461] ath9k 0000:02:00.0 wlan0: disabling HT/VHT due to WEP/TKIP use
[   26.451465] ath9k 0000:02:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[   26.451467] ath9k 0000:02:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[   26.453514] wlan0: associate with <MAC addr Movistar_18575724> (try 1/3)
[   26.463739] wlan0: RX AssocResp from <MAC addr Movistar_18575724> (capab=0x411 status=0 aid=3)
[   26.463943] wlan0: associated
[   26.463972] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   57.509354] wlan0: deauthenticating from <MAC addr Movistar_18575724> by local choice (reason=3)
[   62.781690] wlan0: authenticate with <MAC addr Movistar_18575724>
[   62.791221] wlan0: send auth to <MAC addr Movistar_18575724> (try 1/3)
[   62.793134] wlan0: authenticated
[   62.793308] ath9k 0000:02:00.0 wlan0: disabling HT/VHT due to WEP/TKIP use
[   62.793312] ath9k 0000:02:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[   62.793314] ath9k 0000:02:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[   62.793763] wlan0: associate with <MAC addr Movistar_18575724> (try 1/3)
[   62.803426] wlan0: RX AssocResp from <MAC addr Movistar_18575724> (capab=0x411 status=0 aid=3)
[   62.803657] wlan0: associated


########## wireless info END ############
```

I have browsed through some of the other posts and tried some of the advice in them, but didn't found a solution, so I'm sorry if is a duplicate post.

Thanks in advance.

---

### Post by jeremy31 on 2014-09-24
Try changing your router security settings to WPA2-AES and in network manager change the IPv6 to ignore

---

### Post by h.hittini on 2014-09-24
Maybe that place doesn't allow people associated with that access point to access the internet.

---

### Post by sebastin2 on 2014-09-24
Jeremy

Thanks for answering.

Regretfully I do not have a easy access to my router security system, I would have to talk to the internet provider here. Meanwhile i tried changing the IPv6 to ignore, but seems like the computer is now unable to connect to the network, the connection icon on the status bar keeps moving (switching the highlighted bar, like looking for the network) and the computer says is not connected, from time to time. I will try to talk to my internet provider too see if i can change the router security settings.

---

### Post by sebastin2 on 2014-09-24
Hittini, 

thanks for the reply

I'm not sure what you meant by "people associated with that access point  to access internet" (probably my lack of knowledge) but i don't think it is a network constraint issue (if that is what you mean), the network is a lot like a house network, and besides the password to access the network, it doesn't has any other constraints. Also I have brought another laptops here (windows and mac) and have used the network with internet without any issues.

---

### Post by jeremy31 on 2014-09-24
> **sebastin2 said:**
> Hittini, 

thanks for the reply

I'm not sure what you meant by "people associated with that access point  to access internet" (probably my lack of knowledge) but i don't think it is a network constraint issue (if that is what you mean), the network is a lot like a house network, and besides the password to access the network, it doesn't has any other constraints. Also I have brought another laptops here (windows and mac) and have used the network with internet without any issues.

Have you happened to check the internet config on those other laptops to see if they just had IPv6 settings?

One more thing to try is to enable IPv6 and add ```
[FONT=inherit]2001:4860:4860::8888
``` as an additional DNS server and see if you can get internet access that way[/FONT]

---

### Post by sebastin2 on 2014-09-24
Jeremy.

I only managed to check one other laptop and the IPv6 seems to be in automatic just like the one on the laptop with the issue is.

I reactivated the IPv6 on this laptop and added the additional DNS server (all through the settings of the connection in the network manager of ubuntu not by terminal), but didn't help, the connection with the network works but there is no internet.

Thanks again.

---

