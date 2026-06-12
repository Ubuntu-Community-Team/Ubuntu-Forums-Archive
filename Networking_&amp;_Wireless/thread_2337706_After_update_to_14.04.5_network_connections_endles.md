---
title: "After update to 14.04.5: network connections endlessly waiting for temp IP?"
date: 2016-09-20
forum: Networking &amp; Wireless
---

### Post by blondmammuth on 2016-09-20
This is my first posting here, so I hope I get it right in accordance with the guidlines!

I run Lubuntu on an old ASUS notebook with a Qualcomm Atheros AR9485 Wireless Network Adapter (and as far as I understand this also handles the Ethernet connection?). Recently I had an automated updated to .. (whatever is important in this context?) .. Linux 3.13.0-95-generic (x86_64), built #142-Ubuntu SMP Fri Aug 12 17:00:09 UTC 2016, GNU C Compiler version 4.8.4 (Ubuntu 4.8.4-2ubuntu1~14.04.3), Ubuntu 14.04.5 LTS.

Since then, I can choose network connections (all kinds) from the network manager as usual, I can even switch on and of networking and/or wireless, but none of the connections are established. All attempts run (as far as I have tried) infinitely, telling that they try to receive temporary IP addresses.

I have tried going back to previous kernals (I think 14.04.3), and it doesn't work there either.

I have dual booted windows 8 on the same laptop, which immediately connects to wireless, so there is no hardware problem, and since other devices connect as well, it is also not a problem of the wireless router. I have tried to connect via ethernet, but that didn't work either under Lubuntu.

This is quite an uncomfortable problem, because I have no network connection at all, so whatever I do, I will have to do per USB stick or CD. I have been looking for solutions for quite some time, but there are many, and most of the problems described look somewhat different from mine. I do have the network manager, the connections, and the signal strength show well, so many of the problems I have found are seemingly not comparable.

However, there is an interesting symptom:

When I start the latest kernal in recovery mode, and try to activate the network from the menu, the modem manager tells me that two PCI devices cannot be started because no plugin for them could be found. I don't know whether there is a connection to the main problem (and unluckily this has caused another, because when I tried this, and it did not terminate, I had to interrupt the procedure, and since then my windows partition cannot be mounted any more).

Please ask for more information I might have missed to provide, and thanks in advance for any enlightening answer!

---

### Post by mörgæs on 2016-09-21
Hi, welcome to the fora.

If it were my hardware I would use it as an occasion for doing a fresh install of 16.04.1.

Not saying it's the only solution but as Lubuntu 14.04 only has a little more than half a year left then I wouldn't put much effort into saving it.

---

### Post by blondmammuth on 2016-09-22
Thanks for the suggestion! I might upgrade, but then I don't know whether this would solve the one and only problem: Network access. I have no other problem, but this problem is so severe that it keeps me from doing anything useful easily from the running system - but if I upgrade, then please from the running system, and not destructively from outside!

I am not an expert, so my question might seem trivial, but here it is: Is it possible to make a software update from a newer version with the networking problem solved? I think so (this is a typical RTFM), but what I don't know: How likely will this problem be solved in the next version? How can I know?

Without network, I am basically trapped, that's the point.

---

### Post by mörgæs on 2016-09-22
A fresh install (as opposed to an upgrade in-place) does two things:

[LIST=1]
[*]It gives you new software.
[*]It resets wrong configuration.
[/LIST]
Without going deeper into what the problem is the fresh install often 'just works' and it's not easy to know if it's because or 1) or 2). That's my usual first step if we are dealing with old stuff like 14.04.

If you in stead want to analyse the situation then I suggest that you read the sticky notes and post the output requested.

---

### Post by blondmammuth on 2016-09-22
This is the output. I hope it is OK to paste it here (if not please tell me where). Thanks!

```



########## wireless info START ##########


Report from: 22 Sep 2016 22:10 CEST +0200


Booted last: 21 Sep 2016 01:26 CEST +0200


Script from: 08 Jul 2016 02:16 UTC +0000


##### release ###########################


Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.5 LTS
Release:    14.04
Codename:    trusty


##### kernel ############################


Linux 3.13.0-87-generic #133-Ubuntu SMP Tue May 24 18:32:09 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux


Parameters: ro, quiet, splash, vt.handoff=7


##### desktop ###########################


Lubuntu Netbook


##### lspci #############################


02:00.0 Network controller [0280]: Qualcomm Atheros AR9485 Wireless Network Adapter [168c:0032] (rev 01)
    Subsystem: AzureWave Device [1a3b:1186]
    Kernel driver in use: ath9k


03:00.2 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller [10ec:8136] (rev 06)
    Subsystem: ASUSTeK Computer Inc. Device [1043:200f]
    Kernel driver in use: r8169


##### lsusb #############################


Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 013: ID 0000:0000  
Bus 001 Device 007: ID 413c:2003 Dell Computer Corp. Keyboard
Bus 001 Device 008: ID 093a:2510 Pixart Imaging, Inc. Optical Mouse
Bus 001 Device 005: ID 05e3:0608 Genesys Logic, Inc. Hub
Bus 001 Device 004: ID 05e3:0608 Genesys Logic, Inc. Hub
Bus 001 Device 003: ID 0bda:5605 Realtek Semiconductor Corp. 
Bus 001 Device 002: ID 0457:1029 Silicon Integrated Systems Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


##### PCMCIA card info ##################


'pccardctl' is not installed (package "pcmciautils").


##### rfkill ############################


0: asus-wlan: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no


##### lsmod #############################


ath9k                 164164  0 
ath9k_common           13551  1 ath9k
ath9k_hw              453856  2 ath9k_common,ath9k
ath                    28698  3 ath9k_common,ath9k,ath9k_hw
mac80211              638901  1 ath9k
asus_nb_wmi            16990  0 
asus_wmi               24191  1 asus_nb_wmi
sparse_keymap          13948  1 asus_wmi
cfg80211              496328  3 ath,ath9k,mac80211
wmi                    19177  1 asus_wmi
video                  19476  2 i915_bdw,asus_wmi


##### interfaces ########################


auto lo
iface lo inet loopback


##### ifconfig ##########################


eth0      Link encap:Ethernet  HWaddr <MAC 'eth0' [IF1]>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


wlan0     Link encap:Ethernet  HWaddr <MAC 'wlan0' [IF2]>  
          inet6 addr: fe80::<IP6 'wlan0' [IF2]>/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:204153 errors:0 dropped:0 overruns:0 frame:0
          TX packets:41229 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:64592810 (64.5 MB)  TX bytes:8247872 (8.2 MB)


##### iwconfig ##########################


eth0      no wireless extensions.


lo        no wireless extensions.


wlan0     IEEE 802.11bgn  ESSID:"NETGEAR"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: <MAC 'NETGEAR' [AC2]>   
          Bit Rate=58.5 Mb/s   Tx-Power=16 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=66/70  Signal level=-44 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:11   Missed beacon:0


##### route #############################


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface


##### resolv.conf #######################


##### network managers ##################


Installed:


    NetworkManager


Running:


root       885     1  0 Sep21 ?        00:02:34 NetworkManager


##### NetworkManager info ###############


NetworkManager Tool


State: connecting


- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             unavailable
  Default:           no
  HW Address:        <MAC 'eth0' [IF1]>


  Capabilities:
    Carrier Detect:  yes


  Wired Properties
    Carrier:         off


- Device: wlan0  [NETGEAR] -----------------------------------------------------
  Type:              802.11 WiFi
  Driver:            ath9k
  State:             connecting (getting IP configuration)
  Default:           no
  HW Address:        <MAC 'wlan0' [IF2]>


  Capabilities:


  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes


  Wireless Access Points 
    UPC6258951:      Infra, <MAC 'UPC6258951' [AC4]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 59 WPA WPA2
    3MobileWiFi-2E9D:Infra, <MAC '3MobileWiFi-2E9D' [AC1]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 54 WPA WPA2
    LSKD-WL:         Infra, <MAC 'LSKD-WL' [AC5]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 17 WPA2
    Castorfiber:     Infra, <MAC 'Castorfiber' [AN4]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 29 WPA2
    UPC0048451:      Infra, <MAC 'UPC0048451' [AC9]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 22 WPA WPA2
    Bahar:           Infra, <MAC 'Bahar' [AC6]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 24 WPA WPA2
    UPC Wi-Free:     Infra, <MAC 'UPC Wi-Free' [AN7]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 27 WPA2 Enterprise
    UPC0049642:      Infra, <MAC 'UPC0049642' [AC7]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 29 WPA WPA2
    UPC Wi-Free:     Infra, <MAC 'UPC Wi-Free' [AC8]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 14 WPA2 Enterprise
    Reservat_E53F79: Infra, <MAC 'Reservat_E53F79' [AC3]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 79 WPA WPA2
    NETGEAR:         Infra, <MAC 'NETGEAR' [AC2]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 80 WPA WPA2


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


no-auto-default=<MAC 'eth0' [IF1]>,


[ifupdown]
managed=false


##### NetworkManager profiles ###########


[[/etc/NetworkManager/system-connections/NETGEAR]] (600 root)
[connection] id=NETGEAR | type=802-11-wireless
[802-11-wireless] ssid=NETGEAR | bssid=<MAC 'NETGEAR' [AC2]> | mac-address=<MAC 'wlan0' [IF2]>
[ipv4] method=auto
[ipv6] method=ignore


[[/etc/NetworkManager/system-connections/Reservat_E53F79]] (600 root)
[connection] id=Reservat_E53F79 | type=802-11-wireless
[802-11-wireless] ssid=Reservat_E53F79 | mac-address=<MAC 'wlan0' [IF2]>
[ipv4] method=auto
[ipv6] method=auto


##### iw reg get ########################


'iw' is not installed (package "iw").


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
          Current Frequency:2.412 GHz (Channel 1)


##### iwlist scan #######################


eth0      Interface doesn't support scanning.


lo        Interface doesn't support scanning.


Channel occupancy:


      3   APs on   Frequency:2.412 GHz (Channel 1)
      5   APs on   Frequency:2.437 GHz (Channel 6)
      1   APs on   Frequency:2.462 GHz (Channel 11)


wlan0     Scan completed :
          Cell 01 - Address: <MAC '3MobileWiFi-2E9D' [AC1]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=39/70  Signal level=-71 dBm  
                    Encryption key:on
                    ESSID:"3MobileWiFi-2E9D"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000054d2326ed1
                    Extra: Last beacon: 68ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC 'NETGEAR' [AC2]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=68/70  Signal level=-42 dBm  
                    Encryption key:on
                    ESSID:"NETGEAR"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000017c931b157
                    Extra: Last beacon: 68ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: <MAC 'Reservat_E53F79' [AC3]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=53/70  Signal level=-57 dBm  
                    Encryption key:on
                    ESSID:"Reservat_E53F79"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000536f59e750
                    Extra: Last beacon: 68ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 04 - Address: <MAC 'UPC6258951' [AC4]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=36/70  Signal level=-74 dBm  
                    Encryption key:on
                    ESSID:"UPC6258951"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000192186bc862
                    Extra: Last beacon: 68ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 05 - Address: <MAC 'LSKD-WL' [AC5]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=26/70  Signal level=-84 dBm  
                    Encryption key:on
                    ESSID:"LSKD-WL"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000008c7fcd4999
                    Extra: Last beacon: 68ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 06 - Address: <MAC 'Bahar' [AC6]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=24/70  Signal level=-86 dBm  
                    Encryption key:on
                    ESSID:"Bahar"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000004583ee53ec
                    Extra: Last beacon: 68ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 07 - Address: <MAC 'UPC0049642' [AC7]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=21/70  Signal level=-89 dBm  
                    Encryption key:on
                    ESSID:"UPC0049642"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000191d2ef732
                    Extra: Last beacon: 68ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 08 - Address: <MAC 'UPC Wi-Free' [AC8]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=22/70  Signal level=-88 dBm  
                    Encryption key:on
                    ESSID:"UPC Wi-Free"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000001092b7a45d2
                    Extra: Last beacon: 68ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : 802.1x
          Cell 09 - Address: <MAC 'UPC0048451' [AC9]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=20/70  Signal level=-90 dBm  
                    Encryption key:on
                    ESSID:"UPC0048451"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000001092b7a58da
                    Extra: Last beacon: 1040ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK


##### module infos ######################


[ath9k]
filename:       /lib/modules/3.13.0-87-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k.ko
license:        Dual BSD/GPL
description:    Support for Atheros 802.11n wireless LAN cards.
author:         Atheros Communications
srcversion:     1F2BE74683868C04A429DFF
depends:        ath9k_hw,mac80211,ath9k_common,cfg80211,ath
intree:         Y
vermagic:       3.13.0-87-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        EB:17:8A:95:D5:8F:38:DB:A1:2B:AD:4C:52:C4:25:7E:44:D6:AB:5B
sig_hashalgo:   sha512
parm:           debug:Debugging mask (uint)
parm:           nohwcrypt:Disable hardware encryption (int)
parm:           blink:Enable LED blink on activity (int)
parm:           btcoex_enable:Enable wifi-BT coexistence (int)
parm:           bt_ant_diversity:Enable WLAN/BT RX antenna diversity (int)
parm:           ps_enable:Enable WLAN PowerSave (int)


[ath9k_common]
filename:       /lib/modules/3.13.0-87-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_common.ko
license:        Dual BSD/GPL
description:    Shared library for Atheros wireless 802.11n LAN cards.
author:         Atheros Communications
srcversion:     93644B269B570BC55CF5154
depends:        ath,ath9k_hw
intree:         Y
vermagic:       3.13.0-87-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        EB:17:8A:95:D5:8F:38:DB:A1:2B:AD:4C:52:C4:25:7E:44:D6:AB:5B
sig_hashalgo:   sha512


[ath9k_hw]
filename:       /lib/modules/3.13.0-87-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_hw.ko
license:        Dual BSD/GPL
description:    Support for Atheros 802.11n wireless LAN cards.
author:         Atheros Communications
srcversion:     4D7E3FBEBDFF649364222B3
depends:        ath
intree:         Y
vermagic:       3.13.0-87-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        EB:17:8A:95:D5:8F:38:DB:A1:2B:AD:4C:52:C4:25:7E:44:D6:AB:5B
sig_hashalgo:   sha512


[ath]
filename:       /lib/modules/3.13.0-87-generic/kernel/drivers/net/wireless/ath/ath.ko
license:        Dual BSD/GPL
description:    Shared library for Atheros wireless LAN cards.
author:         Atheros Communications
srcversion:     88A67C5359B02C5A710AFCF
depends:        cfg80211
intree:         Y
vermagic:       3.13.0-87-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        EB:17:8A:95:D5:8F:38:DB:A1:2B:AD:4C:52:C4:25:7E:44:D6:AB:5B
sig_hashalgo:   sha512


[mac80211]
filename:       /lib/modules/3.13.0-87-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     C31A92A72ADA65F2F8247FB
depends:        cfg80211
intree:         Y
vermagic:       3.13.0-87-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        EB:17:8A:95:D5:8F:38:DB:A1:2B:AD:4C:52:C4:25:7E:44:D6:AB:5B
sig_hashalgo:   sha512
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)


[cfg80211]
filename:       /lib/modules/3.13.0-87-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     0055529745EF9A8A3E57FC3
depends:        
intree:         Y
vermagic:       3.13.0-87-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        EB:17:8A:95:D5:8F:38:DB:A1:2B:AD:4C:52:C4:25:7E:44:D6:AB:5B
sig_hashalgo:   sha512
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)


##### module parameters #################


[ath9k]
blink: 0
bt_ant_diversity: 0
btcoex_enable: 0
nohwcrypt: 0
ps_enable: 0


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


[/etc/modprobe.d/libpisock9.conf]
blacklist visor


[/etc/modprobe.d/mlx4.conf]
softdep mlx4_core post: mlx4_en


##### rc.local ##########################


exit 0


##### pm-utils ##########################


##### udev rules ########################


[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x10ec:0x8136 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF1]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# PCI device 0x168c:0x0032 (ath9k)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan0' [IF2]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"


##### dmesg #############################


[161051.620176] wlan0: authenticated
[161051.624242] wlan0: associate with <MAC 'Reservat_E53F79' [AC3]> (try 1/3)
[161051.628453] wlan0: RX AssocResp from <MAC 'Reservat_E53F79' [AC3]> (capab=0x411 status=0 aid=1)
[161051.628523] wlan0: associated
[161096.799871] wlan0: deauthenticating from <MAC 'Reservat_E53F79' [AC3]> by local choice (reason=3)
[161108.589891] wlan0: authenticate with <MAC 'NETGEAR' [AC2]>
[161108.612880] wlan0: send auth to <MAC 'NETGEAR' [AC2]> (try 1/3)
[161108.614950] wlan0: authenticated
[161108.615871] wlan0: associate with <MAC 'NETGEAR' [AC2]> (try 1/3)
[161108.619523] wlan0: RX AssocResp from <MAC 'NETGEAR' [AC2]> (capab=0x531 status=0 aid=3)
[161108.619586] wlan0: associated
[161108.624488] ath: EEPROM regdomain: 0x8348
[161108.624494] ath: EEPROM indicates we should expect a country code
[161108.624498] ath: doing EEPROM country->regdmn map search
[161108.624500] ath: country maps to regdmn code: 0x3a
[161108.624503] ath: Country alpha2 being used: US
[161108.624505] ath: Regpair used: 0x3a
[161108.624508] ath: regdomain 0x8348 dynamically updated by country IE
[161153.843851] wlan0: deauthenticating from <MAC 'NETGEAR' [AC2]> by local choice (reason=3)
[161156.665054] wlan0: authenticate with <MAC 'NETGEAR' [AC2]>
[161156.682623] wlan0: send auth to <MAC 'NETGEAR' [AC2]> (try 1/3)
[161156.686177] wlan0: authenticated
[161156.688697] wlan0: associate with <MAC 'NETGEAR' [AC2]> (try 1/3)
[161156.693330] wlan0: RX AssocResp from <MAC 'NETGEAR' [AC2]> (capab=0x531 status=0 aid=3)
[161156.693482] wlan0: associated
[161156.704962] ath: EEPROM regdomain: 0x8348
[161156.704970] ath: EEPROM indicates we should expect a country code
[161156.704975] ath: doing EEPROM country->regdmn map search
[161156.704979] ath: country maps to regdmn code: 0x3a
[161156.704983] ath: Country alpha2 being used: US
[161156.704986] ath: Regpair used: 0x3a
[161156.704990] ath: regdomain 0x8348 dynamically updated by country IE
[161201.882359] wlan0: deauthenticating from <MAC 'NETGEAR' [AC2]> by local choice (reason=3)
[161204.711996] wlan0: authenticate with <MAC 'NETGEAR' [AC2]>
[161204.729610] wlan0: send auth to <MAC 'NETGEAR' [AC2]> (try 1/3)
[161204.732534] wlan0: authenticated
[161204.733565] wlan0: associate with <MAC 'NETGEAR' [AC2]> (try 1/3)
[161204.738989] wlan0: RX AssocResp from <MAC 'NETGEAR' [AC2]> (capab=0x531 status=0 aid=3)
[161204.739052] wlan0: associated
[161204.745473] ath: EEPROM regdomain: 0x8348
[161204.745486] ath: EEPROM indicates we should expect a country code
[161204.745494] ath: doing EEPROM country->regdmn map search
[161204.745500] ath: country maps to regdmn code: 0x3a
[161204.745506] ath: Country alpha2 being used: US
[161204.745512] ath: Regpair used: 0x3a
[161204.745572] ath: regdomain 0x8348 dynamically updated by country IE


########## wireless info END ############



```

---

### Post by mörgæs on 2016-09-23
It's fine to post here.
I can't make sense of the output but I'm sure somebody else can.

---

### Post by blondmammuth on 2016-09-23
News: I have tried to use a Realtek WiFi Stick. It has shown precisely the same behavior. That is bad for me, because I have no net connection at all on my ASUS, and will have to transfer any file somehow, but it is good, because it definitely shows that the problem lies somewhere else. Only that I have no clue how to solve that .. I might try to download a Lubuntu CD and make a fresh system install. I will report whether it has been successful.

---

### Post by blondmammuth on 2016-09-24
I have to apologize to the community: The problem did not lie with Lubuntu at all, but within my chaos of network hardware. Stopped working with more and more devices, but after a complete restart of everything, it works.

Now this thread is definitely solved, but of no use for others probably (except to remind them to take utmost care of checking the environment before they post here). I leave it to the admins to delete it or keep it. But it should not cost the time of other users looking for solutions only to find out there never was a "real" OS problem.

Thanks anyway for this site and the work it means!

---

