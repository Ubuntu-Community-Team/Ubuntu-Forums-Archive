---
title: "Atheros LAN &amp; WIFI problem"
date: 2014-03-08
forum: Networking &amp; Wireless
---

### Post by mike156 on 2014-03-08
Hey,

I use ubuntu 12.04 LTS and I have problems with the internet...LAN or WiFi. I can create connections, view wifi networks etc...just wown't connect.

LAN Card: Atheros AR8152 PCI-E Fast Ethernet Controller
WiFi Card: Atheros AR2985 802.11b/g/n WiFi Adapter

my internet requires a pppoe which i can't setup with LAN cable and my wifi just keeps asking for password, and stay 20 sec on connecting and asking again for password and so on.

Don't tell me to remove security on router/make new connection on LAN. I have tried every single setting out there, it's a driver problem...i just don't know how to fix it :)

thanks

---

### Post by varunendra on 2014-03-08
Please follow the "Wireless Script" link in my signature, download and run the script as per instructions there, and post back the report it generates. It will give us a detailed information about your wireless setup.

For the ethernet issue, please post the output of -
```
sudo lshw -numeric -C network -sanitize
```
And WHY can't you setup the PPPoE with the LAN cable? Because it is not working or because you don't want to?

While posting the outputs, please use '**Code**' tags. It preserves the output's formatting and makes the post cleaner, compact and more readable. To see a quick 'HowTo' with screenshots, please follow the "Using Code Tags" link in my signature.

---

### Post by lisati on 2014-03-08
*Thread moved to **Networking & Wireless**.*

---

### Post by mike156 on 2014-03-08
For ```
sudo lshw -numeric -C network -sanitize
``` I get the following output:

```
*-network               
       description: Wireless interface
       product: AR9285 Wireless Network Adapter (PCI-Express) [168C:2B]
       vendor: Qualcomm Atheros [168C]
       physical id: 0
       bus info: pci@0000:0c:00.0
       logical name: wlan0
       version: 01
       serial: [REMOVED]
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath9k driverversion=3.11.0-15-generic firmware=N/A latency=0 link=no multicast=yes wireless=IEEE 802.11bgn
       resources: irq:17 memory:f69f0000-f69fffff
  *-network
       description: Ethernet interface
       product: AR8152 v2.0 Fast Ethernet [1969:2062]
       vendor: Qualcomm Atheros [1969]
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: c1
       serial: [REMOVED]
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=atl1c driverversion=1.0.1.1-NAPI latency=0 link=no multicast=yes port=twisted pair
       resources: irq:47 memory:f68c0000-f68fffff ioport:df00(size=128)
```

As for the wireless script the created file content is the following:

```
*************** info trace ***************

***** uname -a *****

Linux Dell 3.11.0-15-generic #25~precise1-Ubuntu SMP Thu Jan 30 17:39:31 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux

***** lsb_release *****

Distributor ID:    Ubuntu
Description:    Ubuntu 12.04.4 LTS
Release:    12.04
Codename:    precise

***** lspci *****

09:00.0 Ethernet controller [0200]: Qualcomm Atheros AR8152 v2.0 Fast Ethernet [1969:2062] (rev c1)
    Subsystem: Dell Device [1028:04a6]
    Kernel driver in use: atl1c
--
0c:00.0 Network controller [0280]: Qualcomm Atheros AR9285 Wireless Network Adapter (PCI-Express) [168c:002b] (rev 01)
    Subsystem: Wistron NeWeb Corp. DNXA-95 802.11bgn Wireless Half-size Mini PCIe Card [185f:30af]
    Kernel driver in use: ath9k

***** lsusb *****

Bus 001 Device 002: ID 0c45:6422 Microdia 
Bus 008 Device 002: ID 0a5c:4500 Broadcom Corp. BCM2046B1 USB 2.0 Hub (part of BCM2046 Bluetooth)
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 008 Device 003: ID 413c:8161 Dell Computer Corp. Integrated Keyboard
Bus 008 Device 004: ID 413c:8162 Dell Computer Corp. Integrated Touchpad [Synaptics]

***** PCMCIA Card Info *****


***** iwconfig *****

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          

***** rfkill *****

0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

***** iw reg get *****


***** route -n *****

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface

***** lsmod *****

ath9k                 161996  0 
mac80211              619465  1 ath9k
ath9k_common           13859  1 ath9k
ath9k_hw              457667  2 ath9k,ath9k_common
ath                    24123  3 ath9k,ath9k_common,ath9k_hw
cfg80211              499466  3 ath9k,mac80211,ath

***** nm-tool *****

NetworkManager Tool

State: disconnected

- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            atl1c
  State:             unavailable
  Default:           no
  HW Address:        <MAC address removed>

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off


- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            ath9k
  State:             disconnected
  Default:           no
  HW Address:        <MAC address removed>

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 
    UPC757326:       Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 59 WPA2
    Next-Gen:        Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 34 WPA WPA2
    TP-LINK_8066EA:  Infra, <MAC address removed>, Freq 2457 MHz, Rate 54 Mb/s, Strength 24 WPA2
    Mike2.4:         Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 97 WPA WPA2
    Clicknet-EE70:   Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 12 WPA2
    CANYON_333D50:   Infra, <MAC address removed>, Freq 2427 MHz, Rate 54 Mb/s, Strength 17 WPA WPA2



***** NetworkManager.state *****
[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true

***** NetworkManager.conf *****

[main]
plugins=ifupdown,keyfile
dns=dnsmasq

[ifupdown]
managed=false

***** interfaces *****

auto lo
iface lo inet loopback


***** iwlist *****

wlan0     Scan completed :
          Cell 01 - Address: <MAC address removed>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=39/70  Signal level=-71 dBm  
                    Encryption key:on
                    ESSID:"UPC757326"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000002594f3b9c6d
                    Extra: Last beacon: 12ms ago
                    IE: Unknown: 0009555043373537333236
                    IE: Unknown: 010482848B96
                    IE: Unknown: 030106
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32080C1218243048606C
                    IE: Unknown: 2D1AFC181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1606080400000000000000000000000000000000000000
                    IE: Unknown: DD790050F204104A0001101044000102103B00010310470010824A5CD146E0381597C4F619F6DB90BB10210005436973636F10230005436973636F1024000631323334353610420007303030303030311054000800060050F204000110110006373537333236100800022008103C0001011049000600372A000120
                    IE: Unknown: DD090010180201F02C0000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 02 - Address: <MAC address removed>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=35/70  Signal level=-75 dBm  
                    Encryption key:on
                    ESSID:"Next-Gen"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000002cc18668b1b
                    Extra: Last beacon: 12ms ago
                    IE: Unknown: 00084E6578742D47656E
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030106
                    IE: Unknown: 0706524F20010D14
                    IE: Unknown: 2A0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32043048606C
                    IE: Unknown: 2D1A6E1103FF00000000000000000000000000000000000000000000
                    IE: Unknown: 3D1606071100000000000000000000000000000000000000
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101830003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C336E1103FF00000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C3406071100000000000000000000000000000000000000
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: Unknown: DD990050F204104A0001101044000102103B0001031047001000000000000010000000F81A67BF48101021000754502D4C494E4B10230009544C2D57523734304E10240003342E3010420003312E301054000800060050F204000110110019576972656C65737320526F7574657220544C2D57523734304E100800020086103C000101104900140024E26002000101600000020001600100020001
          Cell 03 - Address: <MAC address removed>
                    Channel:10
                    Frequency:2.457 GHz (Channel 10)
                    Quality=23/70  Signal level=-87 dBm  
                    Encryption key:on
                    ESSID:"TP-LINK_8066EA"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000005cf4694c659
                    Extra: Last beacon: 12ms ago
                    IE: Unknown: 000E54502D4C494E4B5F383036364541
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 03010A
                    IE: Unknown: 2A0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32043048606C
                    IE: Unknown: 2D1AEF1103FFFF0000000000000000000000000000000406E6E70D00
                    IE: Unknown: 331AEF1103FFFF0000000000000000000000000000000406E6E70D00
                    IE: Unknown: 3D160A071100000000000000000000000000000000000000
                    IE: Unknown: 34160A071100000000000000000000000000000000000000
                    IE: Unknown: DD180050F2020101830003A4000027A4000042435E0062322F00
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: Unknown: DD990050F204104A0001101044000102103B00010310470010000102030405060708090A0B0C0D0E0F1021000754502D4C494E4B10230009544C2D57523834314E10240003382E3010420003312E301054000800060050F204000110110019576972656C65737320526F7574657220544C2D57523834314E100800020086103C000101104900140024E26002000101600000020001600100020001
          Cell 04 - Address: <MAC address removed>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=70/70  Signal level=-38 dBm  
                    Encryption key:on
                    ESSID:"Mike2.4"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000416e305bff
                    Extra: Last beacon: 12ms ago
                    IE: Unknown: 00074D696B65322E34
                    IE: Unknown: 010882840B162430486C
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1A7E181BFFFF000001000000000000000000000000000000000000
                    IE: Unknown: 3D160B0F0000000000000000000000000000000000000000
                    IE: Unknown: DD990050F204104A00011010440001021041000100103B000103104700108E14BBC1B584C95EC21FBFF8952377711021001442656C6B696E20496E7465726E6174696F6E616C1023000A4637443433303220763110240007312E30302E32381042000E31323130313347343132343531351054000800060050F204000110110014506C617920576972656C65737320526F75746572100800020084
                    IE: Unknown: DD090010180200F0010000
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD1E00904C337E181BFFFF000001000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C340B0F0000000000000000000000000000000000000000
          Cell 05 - Address: <MAC address removed>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=17/70  Signal level=-93 dBm  
                    Encryption key:on
                    ESSID:"Clicknet-EE70"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000004075abc9721
                    Extra: Last beacon: 12ms ago
                    IE: Unknown: 000D436C69636B6E65742D45453730
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030101
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1AFC181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1601001100000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F0101
                    IE: Unknown: DD800050F204104A0001101044000102103B00010310470010C114FE08FAED93AE5061E142867DBDC01021000842726F6164636F6D1023000842726F6164636F6D1024000631323334353610420004313233341054000800060050F20400011011000A42726F6164636F6D4150100800020000103C0001011049000600372A000120
                    IE: Unknown: DD090010180200F02C0000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00


***** resolv.conf *****


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

filename:       /lib/modules/3.11.0-15-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k.ko
license:        Dual BSD/GPL
description:    Support for Atheros 802.11n wireless LAN cards.
author:         Atheros Communications
srcversion:     9960BB0B644BE14E4A2F42B
alias:          platform:qca955x_wmac
alias:          platform:ar934x_wmac
alias:          platform:ar933x_wmac
alias:          platform:ath9k
alias:          pci:v0000168Cd00000036sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000037sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000034sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000034sv000010CFsd00001783bc*sc*i*
alias:          pci:v0000168Cd00000034sv000014CDsd00000064bc*sc*i*
alias:          pci:v0000168Cd00000034sv000014CDsd00000063bc*sc*i*
alias:          pci:v0000168Cd00000034sv0000103Csd00001864bc*sc*i*
alias:          pci:v0000168Cd00000034sv000011ADsd00006641bc*sc*i*
alias:          pci:v0000168Cd00000034sv000011ADsd00006631bc*sc*i*
alias:          pci:v0000168Cd00000034sv00001043sd0000850Ebc*sc*i*
alias:          pci:v0000168Cd00000034sv00001A3Bsd00002110bc*sc*i*
alias:          pci:v0000168Cd00000034sv00001969sd00000091bc*sc*i*
alias:          pci:v0000168Cd00000034sv000017AAsd00003214bc*sc*i*
alias:          pci:v0000168Cd00000034sv0000168Csd00003117bc*sc*i*
alias:          pci:v0000168Cd00000034sv000011ADsd00006661bc*sc*i*
alias:          pci:v0000168Cd00000034sv00001A3Bsd00002116bc*sc*i*
alias:          pci:v0000168Cd00000033sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000032sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000032sv0000105Bsd0000E075bc*sc*i*
alias:          pci:v0000168Cd00000032sv00001A3Bsd00002152bc*sc*i*
alias:          pci:v0000168Cd00000032sv00001A3Bsd00002126bc*sc*i*
alias:          pci:v0000168Cd00000032sv00001A3Bsd00001237bc*sc*i*
alias:          pci:v0000168Cd00000032sv00001A3Bsd00002086bc*sc*i*
alias:          pci:v0000168Cd00000030sv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000002Esv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000002Dsv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000002Csv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000002Bsv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000002Asv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000029sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000027sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000024sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000023sv*sd*bc*sc*i*
depends:        ath9k_hw,ath9k_common,mac80211,ath,cfg80211
intree:         Y
vermagic:       3.11.0-15-generic SMP mod_unload modversions 
parm:           debug:Debugging mask (uint)
parm:           nohwcrypt:Disable hardware encryption (int)
parm:           blink:Enable LED blink on activity (int)
parm:           btcoex_enable:Enable wifi-BT coexistence (int)
parm:           enable_diversity:Enable Antenna diversity for AR9565 (int)

filename:       /lib/modules/3.11.0-15-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_common.ko
license:        Dual BSD/GPL
description:    Shared library for Atheros wireless 802.11n LAN cards.
author:         Atheros Communications
srcversion:     2DB88A2876852DC1D8C5A1D
depends:        ath,ath9k_hw
intree:         Y
vermagic:       3.11.0-15-generic SMP mod_unload modversions 

filename:       /lib/modules/3.11.0-15-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_hw.ko
license:        Dual BSD/GPL
description:    Support for Atheros 802.11n wireless LAN cards.
author:         Atheros Communications
srcversion:     57A1E15BE088B8A5C4BE74F
depends:        ath
intree:         Y
vermagic:       3.11.0-15-generic SMP mod_unload modversions 

filename:       /lib/modules/3.11.0-15-generic/kernel/drivers/net/wireless/ath/ath.ko
license:        Dual BSD/GPL
description:    Shared library for Atheros wireless LAN cards.
author:         Atheros Communications
srcversion:     A890CDBC88E6EF28CD751DD
depends:        cfg80211
intree:         Y
vermagic:       3.11.0-15-generic SMP mod_unload modversions 


***** udev rules *****

# PCI device 0x1969:/sys/devices/pci0000:00/0000:00:1c.2/0000:09:00.0 (atl1c)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

# PCI device 0x168c:/sys/devices/pci0000:00/0000:00:1c.1/0000:0c:00.0 (ath9k)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

***** dmesg *****

[   12.410579] ath: phy0: ASPM enabled: 0x43
[   12.410582] ath: EEPROM regdomain: 0x65
[   12.410583] ath: EEPROM indicates we should expect a direct regpair map
[   12.410585] ath: Country alpha2 being used: 00
[   12.410586] ath: Regpair used: 0x65
[   18.935014] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   18.936224] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   21.961904] wlan0: authenticate with <MAC address removed>
[   21.979289] wlan0: send auth to <MAC address removed> (try 1/3)
[   21.981357] wlan0: authenticated
[   21.981534] ath9k 0000:0c:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[   21.981538] ath9k 0000:0c:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[   21.988039] wlan0: associate with <MAC address removed> (try 1/3)
[   21.990524] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=18 aid=0)
[   21.990530] wlan0: <MAC address removed> denied association (code=18)
[   22.014946] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[   22.961181] wlan0: authenticate with <MAC address removed>
[   22.982812] wlan0: send auth to <MAC address removed> (try 1/3)
[   22.984813] wlan0: authenticated
[   22.984980] ath9k 0000:0c:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[   22.984984] ath9k 0000:0c:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[   22.988095] wlan0: associate with <MAC address removed> (try 1/3)
[   22.990577] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=18 aid=0)
[   22.990583] wlan0: <MAC address removed> denied association (code=18)
[   23.002915] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[   23.948722] wlan0: authenticate with <MAC address removed>
[   23.970872] wlan0: send auth to <MAC address removed> (try 1/3)
[   23.972886] wlan0: authenticated
[   23.973113] ath9k 0000:0c:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[   23.973117] ath9k 0000:0c:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[   23.976072] wlan0: associate with <MAC address removed> (try 1/3)
[   23.978594] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=18 aid=0)
[   23.978598] wlan0: <MAC address removed> denied association (code=18)
[   23.994992] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[   24.940505] wlan0: authenticate with <MAC address removed>
[   24.962898] wlan0: send auth to <MAC address removed> (try 1/3)
[   24.964908] wlan0: authenticated
[   24.965075] ath9k 0000:0c:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[   24.965079] ath9k 0000:0c:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[   24.968059] wlan0: associate with <MAC address removed> (try 1/3)
[   24.970594] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=18 aid=0)
[   24.970598] wlan0: <MAC address removed> denied association (code=18)
[   24.982918] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[   25.928486] wlan0: authenticate with <MAC address removed>
[   25.950984] wlan0: send auth to <MAC address removed> (try 1/3)
[   25.952980] wlan0: authenticated
[   25.953268] ath9k 0000:0c:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[   25.953272] ath9k 0000:0c:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[   25.956053] wlan0: associate with <MAC address removed> (try 1/3)
[   25.958573] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=18 aid=0)
[   25.958578] wlan0: <MAC address removed> denied association (code=18)
[   25.983118] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[   26.936427] wlan0: authenticate with <MAC address removed>
[   26.958891] wlan0: send auth to <MAC address removed> (try 1/3)
[   26.960887] wlan0: authenticated
[   26.961104] ath9k 0000:0c:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[   26.961108] ath9k 0000:0c:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[   26.964065] wlan0: associate with <MAC address removed> (try 1/3)
[   26.966573] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=18 aid=0)
[   26.966577] wlan0: <MAC address removed> denied association (code=18)
[   26.979038] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[   27.924903] wlan0: authenticate with <MAC address removed>
[   27.947095] wlan0: send auth to <MAC address removed> (try 1/3)
[   27.949130] wlan0: authenticated
[   27.949354] ath9k 0000:0c:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[   27.949358] ath9k 0000:0c:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[   27.952069] wlan0: associate with <MAC address removed> (try 1/3)
[   27.954635] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=18 aid=0)
[   27.954639] wlan0: <MAC address removed> denied association (code=18)
[   27.970981] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[   28.920416] wlan0: authenticate with <MAC address removed>
[   28.942805] wlan0: send auth to <MAC address removed> (try 1/3)
[   28.944869] wlan0: authenticated
[   28.945039] ath9k 0000:0c:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[   28.945043] ath9k 0000:0c:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[   28.948067] wlan0: associate with <MAC address removed> (try 1/3)
[   28.950594] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=18 aid=0)
[   28.950600] wlan0: <MAC address removed> denied association (code=18)
[   28.967007] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[   29.924331] wlan0: authenticate with <MAC address removed>
[   29.941095] wlan0: send auth to <MAC address removed> (try 1/3)
[   29.943153] wlan0: authenticated
[   29.943323] ath9k 0000:0c:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[   29.943327] ath9k 0000:0c:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[   29.944065] wlan0: associate with <MAC address removed> (try 1/3)
[   29.946550] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=18 aid=0)
[   29.946555] wlan0: <MAC address removed> denied association (code=18)
[   29.966969] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[   30.916213] wlan0: authenticate with <MAC address removed>
[   30.934983] wlan0: send auth to <MAC address removed> (try 1/3)
[   30.937059] wlan0: authenticated
[   30.937235] ath9k 0000:0c:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[   30.937239] ath9k 0000:0c:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[   30.940072] wlan0: associate with <MAC address removed> (try 1/3)
[   30.942623] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=18 aid=0)
[   30.942626] wlan0: <MAC address removed> denied association (code=18)
[   30.963014] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[   31.912432] wlan0: authenticate with <MAC address removed>
[   31.935897] wlan0: send auth to <MAC address removed> (try 1/3)
[   31.937888] wlan0: authenticated
[   31.938102] ath9k 0000:0c:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[   31.938105] ath9k 0000:0c:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[   31.940158] wlan0: associate with <MAC address removed> (try 1/3)
[   31.942734] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=18 aid=0)
[   31.942738] wlan0: <MAC address removed> denied association (code=18)
[   31.974912] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[   32.932467] wlan0: authenticate with <MAC address removed>
[   32.955089] wlan0: send auth to <MAC address removed> (try 1/3)
[   32.957078] wlan0: authenticated
[   32.957339] ath9k 0000:0c:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[   32.957343] ath9k 0000:0c:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[   32.960100] wlan0: associate with <MAC address removed> (try 1/3)
[   32.962599] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=18 aid=0)
[   32.962602] wlan0: <MAC address removed> denied association (code=18)
[   32.978965] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[   33.924508] wlan0: authenticate with <MAC address removed>
[   33.947003] wlan0: send auth to <MAC address removed> (try 1/3)
[   33.949006] wlan0: authenticated
[   33.949239] ath9k 0000:0c:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[   33.949242] ath9k 0000:0c:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[   33.952076] wlan0: associate with <MAC address removed> (try 1/3)
[   33.955963] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=18 aid=0)
[   33.955969] wlan0: <MAC address removed> denied association (code=18)
[   33.974998] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[   34.928502] wlan0: authenticate with <MAC address removed>
[   34.951126] wlan0: send auth to <MAC address removed> (try 1/3)
[   34.955922] wlan0: authenticated
[   34.956181] ath9k 0000:0c:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[   34.956184] ath9k 0000:0c:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[   34.960061] wlan0: associate with <MAC address removed> (try 1/3)
[   34.962556] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=18 aid=0)
[   34.962563] wlan0: <MAC address removed> denied association (code=18)
[   34.978918] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[   35.924474] wlan0: authenticate with <MAC address removed>
[   35.947076] wlan0: send auth to <MAC address removed> (try 1/3)
[   35.949080] wlan0: authenticated
[   35.949308] ath9k 0000:0c:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[   35.949311] ath9k 0000:0c:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[   35.952058] wlan0: associate with <MAC address removed> (try 1/3)
[   35.954555] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=18 aid=0)
[   35.954558] wlan0: <MAC address removed> denied association (code=18)
[   35.970933] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[   36.924504] wlan0: authenticate with <MAC address removed>
[   36.946870] wlan0: send auth to <MAC address removed> (try 1/3)
[   36.948862] wlan0: authenticated
[   36.949040] ath9k 0000:0c:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[   36.949044] ath9k 0000:0c:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[   36.952121] wlan0: associate with <MAC address removed> (try 1/3)
[   36.954648] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=18 aid=0)
[   36.954655] wlan0: <MAC address removed> denied association (code=18)
[   36.978968] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[   37.940411] wlan0: authenticate with <MAC address removed>
[   37.964113] wlan0: send auth to <MAC address removed> (try 1/3)
[   37.966113] wlan0: authenticated
[   37.966253] ath9k 0000:0c:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[   37.966256] ath9k 0000:0c:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[   37.968051] wlan0: associate with <MAC address removed> (try 1/3)
[   37.970669] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=18 aid=0)
[   37.970676] wlan0: <MAC address removed> denied association (code=18)
[   37.991014] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[   38.936429] wlan0: authenticate with <MAC address removed>
[   38.959671] wlan0: send auth to <MAC address removed> (try 1/3)
[   38.961698] wlan0: authenticated
[   38.961845] ath9k 0000:0c:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[   38.961848] ath9k 0000:0c:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[   38.964071] wlan0: associate with <MAC address removed> (try 1/3)
[   38.966597] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=18 aid=0)
[   38.966602] wlan0: <MAC address removed> denied association (code=18)
[   39.002968] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[   39.952528] wlan0: authenticate with <MAC address removed>
[   39.975251] wlan0: send auth to <MAC address removed> (try 1/3)
[   39.977302] wlan0: authenticated
[   39.977481] ath9k 0000:0c:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[   39.977485] ath9k 0000:0c:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[   39.980073] wlan0: associate with <MAC address removed> (try 1/3)
[   39.982678] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=18 aid=0)
[   39.982684] wlan0: <MAC address removed> denied association (code=18)
[   40.003046] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[   40.948489] wlan0: authenticate with <MAC address removed>
[   40.970916] wlan0: send auth to <MAC address removed> (try 1/3)
[   40.972930] wlan0: authenticated
[   40.973125] ath9k 0000:0c:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[   40.973132] ath9k 0000:0c:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[   40.976193] wlan0: associate with <MAC address removed> (try 1/3)
[   40.978695] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=18 aid=0)
[   40.978700] wlan0: <MAC address removed> denied association (code=18)
[   40.995065] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[   41.949753] wlan0: authenticate with <MAC address removed>
[   41.972219] wlan0: send auth to <MAC address removed> (try 1/3)
[   41.974214] wlan0: authenticated
[   41.974481] ath9k 0000:0c:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[   41.974484] ath9k 0000:0c:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[   41.976064] wlan0: associate with <MAC address removed> (try 1/3)
[   41.978657] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=18 aid=0)
[   41.978663] wlan0: <MAC address removed> denied association (code=18)
[   41.998976] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[   42.944509] wlan0: authenticate with <MAC address removed>
[   42.966923] wlan0: send auth to <MAC address removed> (try 1/3)
[   42.968933] wlan0: authenticated
[   42.969106] ath9k 0000:0c:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[   42.969110] ath9k 0000:0c:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[   42.972072] wlan0: associate with <MAC address removed> (try 1/3)
[   42.974651] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=18 aid=0)
[   42.974657] wlan0: <MAC address removed> denied association (code=18)
[   42.990945] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[   43.948457] wlan0: authenticate with <MAC address removed>
[   43.970985] wlan0: send auth to <MAC address removed> (try 1/3)
[   43.972979] wlan0: authenticated
[   43.973256] ath9k 0000:0c:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[   43.973260] ath9k 0000:0c:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[   43.976105] wlan0: associate with <MAC address removed> (try 1/3)
[   43.978655] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=18 aid=0)
[   43.978659] wlan0: <MAC address removed> denied association (code=18)
[   44.003120] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[   44.952484] wlan0: authenticate with <MAC address removed>
[   44.975314] wlan0: send auth to <MAC address removed> (try 1/3)
[   44.977403] wlan0: authenticated
[   44.977725] ath9k 0000:0c:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[   44.977729] ath9k 0000:0c:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[   44.980273] wlan0: associate with <MAC address removed> (try 1/3)
[   44.982935] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=18 aid=0)
[   44.982947] wlan0: <MAC address removed> denied association (code=18)
[   44.995095] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[   45.940682] wlan0: authenticate with <MAC address removed>
[   45.964924] wlan0: send auth to <MAC address removed> (try 1/3)
[   45.967019] wlan0: authenticated
[   45.967192] ath9k 0000:0c:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[   45.967196] ath9k 0000:0c:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[   45.972075] wlan0: associate with <MAC address removed> (try 1/3)
[   45.974682] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=18 aid=0)
[   45.974689] wlan0: <MAC address removed> denied association (code=18)
[   45.990975] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[   46.940469] wlan0: authenticate with <MAC address removed>
[   46.969567] wlan0: send auth to <MAC address removed> (try 1/3)
[   46.971573] wlan0: authenticated
[   46.971989] ath9k 0000:0c:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[   46.971993] ath9k 0000:0c:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[   46.972034] wlan0: associate with <MAC address removed> (try 1/3)
[   46.974529] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=18 aid=0)
[   46.974537] wlan0: <MAC address removed> denied association (code=18)
[   46.995181] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[   47.948653] wlan0: authenticate with <MAC address removed>
[   47.971352] wlan0: send auth to <MAC address removed> (try 1/3)
[   47.973494] wlan0: authenticated
[   47.973737] ath9k 0000:0c:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[   47.973742] ath9k 0000:0c:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[   47.976259] wlan0: associate with <MAC address removed> (try 1/3)
[   47.978836] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=18 aid=0)
[   47.978842] wlan0: <MAC address removed> denied association (code=18)
[   47.995201] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[   48.948741] wlan0: authenticate with <MAC address removed>
[   48.972021] wlan0: send auth to <MAC address removed> (try 1/3)
[   48.974098] wlan0: authenticated
[   48.974275] ath9k 0000:0c:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[   48.974279] ath9k 0000:0c:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[   48.976244] wlan0: associate with <MAC address removed> (try 1/3)
[   48.978811] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=18 aid=0)
[   48.978817] wlan0: <MAC address removed> denied association (code=18)
[   48.995149] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[   49.944823] wlan0: authenticate with <MAC address removed>
[   49.969271] wlan0: send auth to <MAC address removed> (try 1/3)
[   49.971299] wlan0: authenticated
[   49.972873] ath9k 0000:0c:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[   49.972879] ath9k 0000:0c:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[   49.976192] wlan0: associate with <MAC address removed> (try 1/3)
[   49.978761] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=18 aid=0)
[   49.978767] wlan0: <MAC address removed> denied association (code=18)
[   49.999043] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[   50.952438] wlan0: authenticate with <MAC address removed>
[   50.980048] wlan0: send auth to <MAC address removed> (try 1/3)
[   50.982159] wlan0: authenticated
[   50.982527] ath9k 0000:0c:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[   50.982532] ath9k 0000:0c:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[   50.984054] wlan0: associate with <MAC address removed> (try 1/3)
[   50.986618] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=18 aid=0)
[   50.986633] wlan0: <MAC address removed> denied association (code=18)
[   51.015028] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[   51.964733] wlan0: authenticate with <MAC address removed>
[   51.987769] wlan0: send auth to <MAC address removed> (try 1/3)
[   51.989871] wlan0: authenticated
[   51.990272] ath9k 0000:0c:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[   51.990276] ath9k 0000:0c:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[   51.992038] wlan0: associate with <MAC address removed> (try 1/3)
[   51.994644] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=18 aid=0)
[   51.994650] wlan0: <MAC address removed> denied association (code=18)
[   52.032267] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[   52.984435] wlan0: authenticate with <MAC address removed>
[   53.007405] wlan0: send auth to <MAC address removed> (try 1/3)
[   53.009522] wlan0: authenticated
[   53.009730] ath9k 0000:0c:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[   53.009734] ath9k 0000:0c:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[   53.012071] wlan0: associate with <MAC address removed> (try 1/3)
[   53.014571] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=18 aid=0)
[   53.014576] wlan0: <MAC address removed> denied association (code=18)
[   53.039043] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[   53.995301] wlan0: authenticate with <MAC address removed>
[   54.014390] wlan0: send auth to <MAC address removed> (try 1/3)
[   54.016503] wlan0: authenticated
[   54.016671] ath9k 0000:0c:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[   54.016675] ath9k 0000:0c:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[   54.020059] wlan0: associate with <MAC address removed> (try 1/3)
[   54.022590] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=18 aid=0)
[   54.022594] wlan0: <MAC address removed> denied association (code=18)
[   54.051271] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[   55.004467] wlan0: authenticate with <MAC address removed>
[   55.040129] wlan0: send auth to <MAC address removed> (try 1/3)
[   55.042361] wlan0: authenticated
[   55.042775] ath9k 0000:0c:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[   55.042779] ath9k 0000:0c:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[   55.044046] wlan0: associate with <MAC address removed> (try 1/3)
[   55.046582] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=18 aid=0)
[   55.046588] wlan0: <MAC address removed> denied association (code=18)
[   55.080140] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[   56.036578] wlan0: authenticate with <MAC address removed>
[   56.058926] wlan0: send auth to <MAC address removed> (try 1/3)
[   56.061033] wlan0: authenticated
[   56.061278] ath9k 0000:0c:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[   56.061282] ath9k 0000:0c:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[   56.064259] wlan0: associate with <MAC address removed> (try 1/3)
[   56.066762] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=18 aid=0)
[   56.066766] wlan0: <MAC address removed> denied association (code=18)
[   56.079281] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[   57.032439] wlan0: authenticate with <MAC address removed>
[   57.055723] wlan0: send auth to <MAC address removed> (try 1/3)
[   57.057827] wlan0: authenticated
[   57.058001] ath9k 0000:0c:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[   57.058005] ath9k 0000:0c:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[   57.060115] wlan0: associate with <MAC address removed> (try 1/3)
[   57.062678] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=18 aid=0)
[   57.062684] wlan0: <MAC address removed> denied association (code=18)
[   57.078967] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[   58.024433] wlan0: authenticate with <MAC address removed>
[   58.048524] wlan0: send auth to <MAC address removed> (try 1/3)
[   58.050603] wlan0: authenticated
[   58.050905] ath9k 0000:0c:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[   58.050909] ath9k 0000:0c:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[   58.052243] wlan0: associate with <MAC address removed> (try 1/3)
[   58.054811] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=18 aid=0)
[   58.054817] wlan0: <MAC address removed> denied association (code=18)
[   58.079118] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[   59.024726] wlan0: authenticate with <MAC address removed>
[   59.047546] wlan0: send auth to <MAC address removed> (try 1/3)
[   59.050157] wlan0: authenticated
[   59.050338] ath9k 0000:0c:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[   59.050342] ath9k 0000:0c:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[   59.052261] wlan0: associate with <MAC address removed> (try 1/3)
[   59.054801] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=18 aid=0)
[   59.054807] wlan0: <MAC address removed> denied association (code=18)
[   59.071068] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[   60.023205] wlan0: authenticate with <MAC address removed>
[   60.052429] wlan0: send auth to <MAC address removed> (try 1/3)
[   60.054469] wlan0: authenticated
[   60.056265] ath9k 0000:0c:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[   60.056269] ath9k 0000:0c:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[   60.060125] wlan0: associate with <MAC address removed> (try 1/3)
[   60.062615] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=18 aid=0)
[   60.062621] wlan0: <MAC address removed> denied association (code=18)
[   60.086961] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[   61.040562] wlan0: authenticate with <MAC address removed>
[   61.063293] wlan0: send auth to <MAC address removed> (try 1/3)
[   61.066795] wlan0: authenticated
[   61.067084] ath9k 0000:0c:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[   61.067088] ath9k 0000:0c:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[   61.068058] wlan0: associate with <MAC address removed> (try 1/3)
[   61.070563] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=18 aid=0)
[   61.070569] wlan0: <MAC address removed> denied association (code=18)
[   61.082945] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[   62.032491] wlan0: authenticate with <MAC address removed>
[   62.055625] wlan0: send auth to <MAC address removed> (try 1/3)
[   62.059771] wlan0: authenticated
[   62.059960] ath9k 0000:0c:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[   62.059964] ath9k 0000:0c:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[   62.060202] wlan0: associate with <MAC address removed> (try 1/3)
[   62.062827] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=18 aid=0)
[   62.062835] wlan0: <MAC address removed> denied association (code=18)
[   62.091026] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[   63.036743] wlan0: authenticate with <MAC address removed>
[   63.059082] wlan0: send auth to <MAC address removed> (try 1/3)
[   63.061143] wlan0: authenticated
[   63.061490] ath9k 0000:0c:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[   63.061494] ath9k 0000:0c:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[   63.064454] wlan0: associate with <MAC address removed> (try 1/3)
[   63.066976] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=18 aid=0)
[   63.066981] wlan0: <MAC address removed> denied association (code=18)
[   63.091209] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[   64.036589] wlan0: authenticate with <MAC address removed>
[   64.059106] wlan0: send auth to <MAC address removed> (try 1/3)
[   64.061281] wlan0: authenticated
[   64.061475] ath9k 0000:0c:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[   64.061479] ath9k 0000:0c:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[   64.064294] wlan0: associate with <MAC address removed> (try 1/3)
[   64.066835] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=18 aid=0)
[   64.066840] wlan0: <MAC address removed> denied association (code=18)
[   64.095234] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[   65.048447] wlan0: authenticate with <MAC address removed>
[   65.080125] wlan0: send auth to <MAC address removed> (try 1/3)
[   65.082207] wlan0: authenticated
[   65.082839] ath9k 0000:0c:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[   65.082844] ath9k 0000:0c:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[   65.084042] wlan0: associate with <MAC address removed> (try 1/3)
[   65.087688] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=18 aid=0)
[   65.087695] wlan0: <MAC address removed> denied association (code=18)
[   65.119003] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[   66.064687] wlan0: authenticate with <MAC address removed>
[   66.087246] wlan0: send auth to <MAC address removed> (try 1/3)
[   66.089224] wlan0: authenticated
[   66.090464] ath9k 0000:0c:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[   66.090469] ath9k 0000:0c:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[   66.092049] wlan0: associate with <MAC address removed> (try 1/3)
[   66.094654] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=18 aid=0)
[   66.094660] wlan0: <MAC address removed> denied association (code=18)
[   66.119341] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[   67.068694] wlan0: authenticate with <MAC address removed>
[   67.091225] wlan0: send auth to <MAC address removed> (try 1/3)
[   67.093208] wlan0: authenticated
[   67.093368] ath9k 0000:0c:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[   67.093371] ath9k 0000:0c:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[   67.096187] wlan0: associate with <MAC address removed> (try 1/3)
[   67.098909] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=18 aid=0)
[   67.098915] wlan0: <MAC address removed> denied association (code=18)
[   67.118938] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[   68.070831] wlan0: authenticate with <MAC address removed>
[   68.091899] wlan0: send auth to <MAC address removed> (try 1/3)
[   68.094022] wlan0: authenticated
[   68.094399] ath9k 0000:0c:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[   68.094403] ath9k 0000:0c:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[   68.096163] wlan0: associate with <MAC address removed> (try 1/3)
[   68.101271] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=18 aid=0)
[   68.101277] wlan0: <MAC address removed> denied association (code=18)
[   68.123182] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[   69.076517] wlan0: authenticate with <MAC address removed>
[   69.098902] wlan0: send auth to <MAC address removed> (try 1/3)
[   69.100923] wlan0: authenticated
[   69.101099] ath9k 0000:0c:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[   69.101103] ath9k 0000:0c:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[   69.104065] wlan0: associate with <MAC address removed> (try 1/3)
[   69.106544] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=18 aid=0)
[   69.106548] wlan0: <MAC address removed> denied association (code=18)
[   69.134931] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[   70.088476] wlan0: authenticate with <MAC address removed>
[   70.107140] wlan0: send auth to <MAC address removed> (try 1/3)
[   70.109223] wlan0: authenticated
[   70.109599] ath9k 0000:0c:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[   70.109603] ath9k 0000:0c:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[   70.112156] wlan0: associate with <MAC address removed> (try 1/3)
[   70.114922] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=18 aid=0)
[   70.114928] wlan0: <MAC address removed> denied association (code=18)
[   70.147377] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[   71.096787] wlan0: authenticate with <MAC address removed>
[   71.119247] wlan0: send auth to <MAC address removed> (try 1/3)
[   71.121322] wlan0: authenticated
[   71.121616] ath9k 0000:0c:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[   71.121619] ath9k 0000:0c:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[   71.124058] wlan0: associate with <MAC address removed> (try 1/3)
[   71.126604] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=18 aid=0)
[   71.126610] wlan0: <MAC address removed> denied association (code=18)
[   71.147222] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[   72.107890] wlan0: authenticate with <MAC address removed>
[   72.128847] wlan0: send auth to <MAC address removed> (try 1/3)
[   72.131821] wlan0: authenticated
[   72.132538] ath9k 0000:0c:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[   72.132544] ath9k 0000:0c:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[   72.136181] wlan0: associate with <MAC address removed> (try 1/3)
[   72.139291] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=18 aid=0)
[   72.139297] wlan0: <MAC address removed> denied association (code=18)
[   72.164899] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[   73.120687] wlan0: authenticate with <MAC address removed>
[   73.143237] wlan0: send auth to <MAC address removed> (try 1/3)
[   73.145252] wlan0: authenticated
[   73.145603] ath9k 0000:0c:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[   73.145606] ath9k 0000:0c:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[   73.148053] wlan0: associate with <MAC address removed> (try 1/3)
[   73.150692] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=18 aid=0)
[   73.150698] wlan0: <MAC address removed> denied association (code=18)
[   73.171240] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[   74.131303] wlan0: authenticate with <MAC address removed>
[   74.148935] wlan0: send auth to <MAC address removed> (try 1/3)
[   74.151053] wlan0: authenticated
[   74.151696] ath9k 0000:0c:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[   74.151703] ath9k 0000:0c:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[   74.152547] wlan0: associate with <MAC address removed> (try 1/3)
[   74.156601] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=18 aid=0)
[   74.156608] wlan0: <MAC address removed> denied association (code=18)
[   74.183106] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[   75.140698] wlan0: authenticate with <MAC address removed>
[   75.163449] wlan0: send auth to <MAC address removed> (try 1/3)
[   75.167315] wlan0: authenticated
[   75.168548] ath9k 0000:0c:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[   75.168553] ath9k 0000:0c:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[   75.172204] wlan0: associate with <MAC address removed> (try 1/3)
[   75.174786] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=18 aid=0)
[   75.174793] wlan0: <MAC address removed> denied association (code=18)
[   75.199194] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[   76.148497] wlan0: authenticate with <MAC address removed>
[   76.173903] wlan0: send auth to <MAC address removed> (try 1/3)
[   76.176078] wlan0: authenticated
[   76.176427] ath9k 0000:0c:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[   76.176431] ath9k 0000:0c:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[   76.180057] wlan0: associate with <MAC address removed> (try 1/3)
[   76.182692] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=18 aid=0)
[   76.182700] wlan0: <MAC address removed> denied association (code=18)
[   76.203081] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[   77.152685] wlan0: authenticate with <MAC address removed>
[   77.175516] wlan0: send auth to <MAC address removed> (try 1/3)
[   77.178482] wlan0: authenticated
[   77.178865] ath9k 0000:0c:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[   77.178870] ath9k 0000:0c:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[   77.180046] wlan0: associate with <MAC address removed> (try 1/3)
[   77.182535] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=18 aid=0)
[   77.182541] wlan0: <MAC address removed> denied association (code=18)
[   77.203016] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[   78.152704] wlan0: authenticate with <MAC address removed>
[   78.175099] wlan0: send auth to <MAC address removed> (try 1/3)
[   78.177206] wlan0: authenticated
[   78.177405] ath9k 0000:0c:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[   78.177409] ath9k 0000:0c:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[   78.180240] wlan0: associate with <MAC address removed> (try 1/3)
[   78.182934] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=18 aid=0)
[   78.182940] wlan0: <MAC address removed> denied association (code=18)
[   78.207200] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[   79.171247] wlan0: authenticate with <MAC address removed>
[   79.200116] wlan0: send auth to <MAC address removed> (try 1/3)
[   79.202329] wlan0: authenticated
[   79.202798] ath9k 0000:0c:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[   79.202802] ath9k 0000:0c:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[   79.204773] wlan0: associate with <MAC address removed> (try 1/3)
[   79.207338] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=18 aid=0)
[   79.207344] wlan0: <MAC address removed> denied association (code=18)
[   79.226964] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[   80.179152] wlan0: authenticate with <MAC address removed>
[   80.196676] wlan0: send auth to <MAC address removed> (try 1/3)
[   80.200877] wlan0: authenticated
[   80.201216] ath9k 0000:0c:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[   80.201220] ath9k 0000:0c:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[   80.204536] wlan0: associate with <MAC address removed> (try 1/3)
[   80.207029] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=18 aid=0)
[   80.207036] wlan0: <MAC address removed> denied association (code=18)
[   80.224571] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)

****************** done ******************
```



Related to LAN is due to the fact that it simply doesn't work. I mostly want to be able to use WiFi but I would like to be able to use LAN too.

---

### Post by varunendra on 2014-03-08
Which one is your access-point? Based on signal strength and name, it seems it is "Mike2.4".

If so, please try changing the encryption type in the router to pure WPA2-AES(CCMP). Currently it is using WPA/WPA2 mixed mode which can be confusing for many linux drivers. Save the change and reboot the router. Remember - no mixed mode, no TKIP.

However, these messages -
```
[   79.204773] wlan0: associate with <MAC address removed> (try 1/3)
[   79.207338] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=18 aid=0)
[   79.207344] wlan0: <MAC address removed> **[COLOR="#FF0000"]denied association[/COLOR]** (code=18)
```
..indicate that possibly there may also be a security key problem. I recommend you reset the passkey in the router, delete the saved connection in Network Manager in Ubuntu, and make sure it is typed correctly the next time you save it.

For some reason, the router is outright denying association. If the passkey and encryption type are correct, then it may be some kind of filter in the router doing this. Is MAC filter or any such custom service enabled in it?


As for the wired connection, was the cable connected when you ran the commands? Have you cross-checked the obvious? That is - making sure the cable and header plugs are okay, changing cable with a tested one etc.

The lshw output shows "**link=no**", while the card is a common one and the correct driver is loaded for it.

If the cable was tested and connected, then check your BIOS to make sure Ethernet is enabled there. If it is NOT a UEFI based installation, you may also try resetting the BIOS.
Also, see if there is a feature called "IOMMU" in the BIOS. If there is, try changing its state (usually is disabled by default, if so, enable it).

Try these and confirm the sanity checks. Post back how it goes and we'll proceed accordingly.

---

### Post by mike156 on 2014-03-08
Removed any security (open access, no password required) on router (it's a Belkin if it matters), made sure the cable has power and ran the tests again.

```
sudo lshw -numeric -C network -sanitize

*-network               
       description: Wireless interface
       product: AR9285 Wireless Network Adapter (PCI-Express) [168C:2B]
       vendor: Qualcomm Atheros [168C]
       physical id: 0
       bus info: pci@0000:0c:00.0
       logical name: wlan0
       version: 01
       serial: [REMOVED]
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath9k driverversion=3.11.0-15-generic firmware=N/A latency=0 link=no multicast=yes wireless=IEEE 802.11bgn
       resources: irq:17 memory:f69f0000-f69fffff
  *-network
       description: Ethernet interface
       product: AR8152 v2.0 Fast Ethernet [1969:2062]
       vendor: Qualcomm Atheros [1969]
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: c1
       serial: [REMOVED]
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=atl1c driverversion=1.0.1.1-NAPI duplex=full latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:47 memory:f68c0000-f68fffff ioport:df00(size=128)


```

```
Wireless Script


*************** info trace ***************

***** uname -a *****

Linux Dell 3.11.0-15-generic #25~precise1-Ubuntu SMP Thu Jan 30 17:39:31 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux

***** lsb_release *****

Distributor ID:    Ubuntu
Description:    Ubuntu 12.04.4 LTS
Release:    12.04
Codename:    precise

***** lspci *****

09:00.0 Ethernet controller [0200]: Qualcomm Atheros AR8152 v2.0 Fast Ethernet [1969:2062] (rev c1)
    Subsystem: Dell Device [1028:04a6]
    Kernel driver in use: atl1c
--
0c:00.0 Network controller [0280]: Qualcomm Atheros AR9285 Wireless Network Adapter (PCI-Express) [168c:002b] (rev 01)
    Subsystem: Wistron NeWeb Corp. DNXA-95 802.11bgn Wireless Half-size Mini PCIe Card [185f:30af]
    Kernel driver in use: ath9k

***** lsusb *****

Bus 001 Device 002: ID 0c45:6422 Microdia 
Bus 008 Device 002: ID 0a5c:4500 Broadcom Corp. BCM2046B1 USB 2.0 Hub (part of BCM2046 Bluetooth)
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 008 Device 003: ID 413c:8161 Dell Computer Corp. Integrated Keyboard
Bus 008 Device 004: ID 413c:8162 Dell Computer Corp. Integrated Touchpad [Synaptics]

***** PCMCIA Card Info *****


***** iwconfig *****

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          

***** rfkill *****

0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

***** iw reg get *****


***** route -n *****

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface

***** lsmod *****

ath9k                 161996  0 
mac80211              619465  1 ath9k
ath9k_common           13859  1 ath9k
ath9k_hw              457667  2 ath9k,ath9k_common
ath                    24123  3 ath9k,ath9k_common,ath9k_hw
cfg80211              499466  3 ath9k,mac80211,ath

***** nm-tool *****

NetworkManager Tool

State: connecting

- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            atl1c
  State:             unavailable
  Default:           no
  HW Address:        <MAC address removed>

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off


- Device: wlan0  [Mike2.4] -----------------------------------------------------
  Type:              802.11 WiFi
  Driver:            ath9k
  State:             connecting (configuring)
  Default:           no
  HW Address:        <MAC address removed>

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 
    UPC757326:       Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 50 WPA2
    Next-Gen:        Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 40 WPA WPA2
    TP-LINK_8066EA:  Infra, <MAC address removed>, Freq 2457 MHz, Rate 54 Mb/s, Strength 19 WPA2
    CANYON_333D50:   Infra, <MAC address removed>, Freq 2427 MHz, Rate 54 Mb/s, Strength 15 WPA WPA2
    Clicknet-EE70:   Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 17 WPA2
    Mike2.4:         Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 97



***** NetworkManager.state *****
[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true

***** NetworkManager.conf *****

[main]
plugins=ifupdown,keyfile
dns=dnsmasq

no-auto-default=<MAC address removed>,

[ifupdown]
managed=false

***** interfaces *****

auto lo
iface lo inet loopback


***** iwlist *****


***** resolv.conf *****


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

filename:       /lib/modules/3.11.0-15-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k.ko
license:        Dual BSD/GPL
description:    Support for Atheros 802.11n wireless LAN cards.
author:         Atheros Communications
srcversion:     9960BB0B644BE14E4A2F42B
alias:          platform:qca955x_wmac
alias:          platform:ar934x_wmac
alias:          platform:ar933x_wmac
alias:          platform:ath9k
alias:          pci:v0000168Cd00000036sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000037sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000034sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000034sv000010CFsd00001783bc*sc*i*
alias:          pci:v0000168Cd00000034sv000014CDsd00000064bc*sc*i*
alias:          pci:v0000168Cd00000034sv000014CDsd00000063bc*sc*i*
alias:          pci:v0000168Cd00000034sv0000103Csd00001864bc*sc*i*
alias:          pci:v0000168Cd00000034sv000011ADsd00006641bc*sc*i*
alias:          pci:v0000168Cd00000034sv000011ADsd00006631bc*sc*i*
alias:          pci:v0000168Cd00000034sv00001043sd0000850Ebc*sc*i*
alias:          pci:v0000168Cd00000034sv00001A3Bsd00002110bc*sc*i*
alias:          pci:v0000168Cd00000034sv00001969sd00000091bc*sc*i*
alias:          pci:v0000168Cd00000034sv000017AAsd00003214bc*sc*i*
alias:          pci:v0000168Cd00000034sv0000168Csd00003117bc*sc*i*
alias:          pci:v0000168Cd00000034sv000011ADsd00006661bc*sc*i*
alias:          pci:v0000168Cd00000034sv00001A3Bsd00002116bc*sc*i*
alias:          pci:v0000168Cd00000033sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000032sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000032sv0000105Bsd0000E075bc*sc*i*
alias:          pci:v0000168Cd00000032sv00001A3Bsd00002152bc*sc*i*
alias:          pci:v0000168Cd00000032sv00001A3Bsd00002126bc*sc*i*
alias:          pci:v0000168Cd00000032sv00001A3Bsd00001237bc*sc*i*
alias:          pci:v0000168Cd00000032sv00001A3Bsd00002086bc*sc*i*
alias:          pci:v0000168Cd00000030sv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000002Esv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000002Dsv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000002Csv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000002Bsv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000002Asv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000029sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000027sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000024sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000023sv*sd*bc*sc*i*
depends:        ath9k_hw,ath9k_common,mac80211,ath,cfg80211
intree:         Y
vermagic:       3.11.0-15-generic SMP mod_unload modversions 
parm:           debug:Debugging mask (uint)
parm:           nohwcrypt:Disable hardware encryption (int)
parm:           blink:Enable LED blink on activity (int)
parm:           btcoex_enable:Enable wifi-BT coexistence (int)
parm:           enable_diversity:Enable Antenna diversity for AR9565 (int)

filename:       /lib/modules/3.11.0-15-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_common.ko
license:        Dual BSD/GPL
description:    Shared library for Atheros wireless 802.11n LAN cards.
author:         Atheros Communications
srcversion:     2DB88A2876852DC1D8C5A1D
depends:        ath,ath9k_hw
intree:         Y
vermagic:       3.11.0-15-generic SMP mod_unload modversions 

filename:       /lib/modules/3.11.0-15-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_hw.ko
license:        Dual BSD/GPL
description:    Support for Atheros 802.11n wireless LAN cards.
author:         Atheros Communications
srcversion:     57A1E15BE088B8A5C4BE74F
depends:        ath
intree:         Y
vermagic:       3.11.0-15-generic SMP mod_unload modversions 

filename:       /lib/modules/3.11.0-15-generic/kernel/drivers/net/wireless/ath/ath.ko
license:        Dual BSD/GPL
description:    Shared library for Atheros wireless LAN cards.
author:         Atheros Communications
srcversion:     A890CDBC88E6EF28CD751DD
depends:        cfg80211
intree:         Y
vermagic:       3.11.0-15-generic SMP mod_unload modversions 


***** udev rules *****

# PCI device 0x1969:/sys/devices/pci0000:00/0000:00:1c.2/0000:09:00.0 (atl1c)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

# PCI device 0x168c:/sys/devices/pci0000:00/0000:00:1c.1/0000:0c:00.0 (ath9k)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

***** dmesg *****

[   12.551059] ath: phy0: ASPM enabled: 0x43
[   12.551062] ath: EEPROM regdomain: 0x65
[   12.551063] ath: EEPROM indicates we should expect a direct regpair map
[   12.551066] ath: Country alpha2 being used: 00
[   12.551066] ath: Regpair used: 0x65
[   19.180122] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   19.181911] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   79.952824] wlan0: authenticate with <MAC address removed>
[   79.975300] wlan0: send auth to <MAC address removed> (try 1/3)
[   79.977360] wlan0: authenticated
[   79.977903] ath9k 0000:0c:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[   79.977908] ath9k 0000:0c:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[   79.980048] wlan0: associate with <MAC address removed> (try 1/3)
[   79.982505] wlan0: RX AssocResp from <MAC address removed> (capab=0x401 status=18 aid=0)
[   79.982512] wlan0: <MAC address removed> denied association (code=18)
[   80.003178] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[   80.948671] wlan0: authenticate with <MAC address removed>
[   80.971131] wlan0: send auth to <MAC address removed> (try 1/3)
[   80.973272] wlan0: authenticated
[   80.973516] ath9k 0000:0c:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[   80.973519] ath9k 0000:0c:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[   80.976086] wlan0: associate with <MAC address removed> (try 1/3)
[   80.978394] wlan0: RX AssocResp from <MAC address removed> (capab=0x401 status=18 aid=0)
[   80.978399] wlan0: <MAC address removed> denied association (code=18)
[   81.003185] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[   82.352828] wlan0: authenticate with <MAC address removed>
[   82.375264] wlan0: send auth to <MAC address removed> (try 1/3)
[   82.377333] wlan0: authenticated
[   82.377507] ath9k 0000:0c:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[   82.377510] ath9k 0000:0c:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[   82.380274] wlan0: associate with <MAC address removed> (try 1/3)
[   82.382904] wlan0: RX AssocResp from <MAC address removed> (capab=0x401 status=18 aid=0)
[   82.382910] wlan0: <MAC address removed> denied association (code=18)
[   82.411111] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[   83.360938] wlan0: authenticate with <MAC address removed>
[   83.380028] wlan0: send auth to <MAC address removed> (try 1/3)
[   83.382142] wlan0: authenticated
[   83.382324] ath9k 0000:0c:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[   83.382328] ath9k 0000:0c:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[   83.384283] wlan0: associate with <MAC address removed> (try 1/3)
[   83.386721] wlan0: RX AssocResp from <MAC address removed> (capab=0x401 status=18 aid=0)
[   83.386728] wlan0: <MAC address removed> denied association (code=18)
[   83.411093] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[   84.756829] wlan0: authenticate with <MAC address removed>
[   84.779435] wlan0: send auth to <MAC address removed> (try 1/3)
[   84.781547] wlan0: authenticated
[   84.781705] ath9k 0000:0c:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[   84.781708] ath9k 0000:0c:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[   84.784244] wlan0: associate with <MAC address removed> (try 1/3)
[   84.786645] wlan0: RX AssocResp from <MAC address removed> (capab=0x401 status=18 aid=0)
[   84.786653] wlan0: <MAC address removed> denied association (code=18)
[   84.804233] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[   85.748839] wlan0: authenticate with <MAC address removed>
[   85.770999] wlan0: send auth to <MAC address removed> (try 1/3)
[   85.774563] wlan0: authenticated
[   85.774767] ath9k 0000:0c:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[   85.774771] ath9k 0000:0c:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[   85.776274] wlan0: associate with <MAC address removed> (try 1/3)
[   85.778647] wlan0: RX AssocResp from <MAC address removed> (capab=0x401 status=18 aid=0)
[   85.778653] wlan0: <MAC address removed> denied association (code=18)
[   85.791173] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[   87.136621] wlan0: authenticate with <MAC address removed>
[   87.159191] wlan0: send auth to <MAC address removed> (try 1/3)
[   87.161246] wlan0: authenticated
[   87.161420] ath9k 0000:0c:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[   87.161423] ath9k 0000:0c:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[   87.168066] wlan0: associate with <MAC address removed> (try 1/3)
[   87.170477] wlan0: RX AssocResp from <MAC address removed> (capab=0x401 status=18 aid=0)
[   87.170483] wlan0: <MAC address removed> denied association (code=18)
[   87.191239] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[   88.137745] wlan0: authenticate with <MAC address removed>
[   88.160686] wlan0: send auth to <MAC address removed> (try 1/3)
[   88.162684] wlan0: authenticated
[   88.163025] ath9k 0000:0c:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[   88.163029] ath9k 0000:0c:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[   88.164198] wlan0: associate with <MAC address removed> (try 1/3)
[   88.166621] wlan0: RX AssocResp from <MAC address removed> (capab=0x401 status=18 aid=0)
[   88.166626] wlan0: <MAC address removed> denied association (code=18)
[   88.195001] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[   89.544293] wlan0: authenticate with <MAC address removed>
[   89.565361] wlan0: send auth to <MAC address removed> (try 1/3)
[   89.567396] wlan0: authenticated
[   89.567536] ath9k 0000:0c:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[   89.567540] ath9k 0000:0c:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[   89.572144] wlan0: associate with <MAC address removed> (try 1/3)
[   89.574658] wlan0: RX AssocResp from <MAC address removed> (capab=0x401 status=18 aid=0)
[   89.574665] wlan0: <MAC address removed> denied association (code=18)
[   89.599225] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[   90.552587] wlan0: authenticate with <MAC address removed>
[   90.576264] wlan0: send auth to <MAC address removed> (try 1/3)
[   90.578348] wlan0: authenticated
[   90.578487] ath9k 0000:0c:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[   90.578490] ath9k 0000:0c:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[   90.580240] wlan0: associate with <MAC address removed> (try 1/3)
[   90.582716] wlan0: RX AssocResp from <MAC address removed> (capab=0x401 status=18 aid=0)
[   90.582722] wlan0: <MAC address removed> denied association (code=18)
[   90.599197] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[   91.949204] wlan0: authenticate with <MAC address removed>
[   91.973905] wlan0: send auth to <MAC address removed> (try 1/3)
[   91.975896] wlan0: authenticated
[   91.976489] ath9k 0000:0c:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[   91.976494] ath9k 0000:0c:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[   91.980246] wlan0: associate with <MAC address removed> (try 1/3)
[   91.982742] wlan0: RX AssocResp from <MAC address removed> (capab=0x401 status=18 aid=0)
[   91.982749] wlan0: <MAC address removed> denied association (code=18)
[   92.015219] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[   92.973462] wlan0: authenticate with <MAC address removed>
[   92.992052] wlan0: send auth to <MAC address removed> (try 1/3)
[   92.994123] wlan0: authenticated
[   92.994292] ath9k 0000:0c:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[   92.994296] ath9k 0000:0c:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[   92.996063] wlan0: associate with <MAC address removed> (try 1/3)
[   92.998484] wlan0: RX AssocResp from <MAC address removed> (capab=0x401 status=18 aid=0)
[   92.998491] wlan0: <MAC address removed> denied association (code=18)
[   93.019281] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[   94.364856] wlan0: authenticate with <MAC address removed>
[   94.390882] wlan0: send auth to <MAC address removed> (try 1/3)
[   94.392890] wlan0: authenticated
[   94.393308] ath9k 0000:0c:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[   94.393312] ath9k 0000:0c:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[   94.396106] wlan0: associate with <MAC address removed> (try 1/3)
[   94.398608] wlan0: RX AssocResp from <MAC address removed> (capab=0x401 status=18 aid=0)
[   94.398615] wlan0: <MAC address removed> denied association (code=18)
[   94.427213] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[   95.376619] wlan0: authenticate with <MAC address removed>
[   95.399172] wlan0: send auth to <MAC address removed> (try 1/3)
[   95.401151] wlan0: authenticated
[   95.401442] ath9k 0000:0c:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[   95.401446] ath9k 0000:0c:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[   95.404302] wlan0: associate with <MAC address removed> (try 1/3)
[   95.406714] wlan0: RX AssocResp from <MAC address removed> (capab=0x401 status=18 aid=0)
[   95.406721] wlan0: <MAC address removed> denied association (code=18)
[   95.435253] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[   96.780842] wlan0: authenticate with <MAC address removed>
[   96.807014] wlan0: send auth to <MAC address removed> (try 1/3)
[   96.809185] wlan0: authenticated
[   96.809445] ath9k 0000:0c:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[   96.809449] ath9k 0000:0c:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[   96.812255] wlan0: associate with <MAC address removed> (try 1/3)
[   96.814675] wlan0: RX AssocResp from <MAC address removed> (capab=0x401 status=18 aid=0)
[   96.814680] wlan0: <MAC address removed> denied association (code=18)
[   96.839178] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[   97.784846] wlan0: authenticate with <MAC address removed>
[   97.807359] wlan0: send auth to <MAC address removed> (try 1/3)
[   97.812038] wlan0: authenticated
[   97.812398] ath9k 0000:0c:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[   97.812402] ath9k 0000:0c:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[   97.816078] wlan0: associate with <MAC address removed> (try 1/3)
[   97.818577] wlan0: RX AssocResp from <MAC address removed> (capab=0x401 status=18 aid=0)
[   97.818584] wlan0: <MAC address removed> denied association (code=18)
[   97.843338] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[   99.192635] wlan0: authenticate with <MAC address removed>
[   99.215234] wlan0: send auth to <MAC address removed> (try 1/3)
[   99.217319] wlan0: authenticated
[   99.217477] ath9k 0000:0c:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[   99.217481] ath9k 0000:0c:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[   99.221119] wlan0: associate with <MAC address removed> (try 1/3)
[   99.223716] wlan0: RX AssocResp from <MAC address removed> (capab=0x401 status=18 aid=0)
[   99.223722] wlan0: <MAC address removed> denied association (code=18)
[   99.251029] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[  100.200855] wlan0: authenticate with <MAC address removed>
[  100.230717] wlan0: send auth to <MAC address removed> (try 1/3)
[  100.232708] wlan0: authenticated
[  100.233138] ath9k 0000:0c:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[  100.233142] ath9k 0000:0c:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[  100.236055] wlan0: associate with <MAC address removed> (try 1/3)
[  100.238939] wlan0: RX AssocResp from <MAC address removed> (capab=0x401 status=18 aid=0)
[  100.238948] wlan0: <MAC address removed> denied association (code=18)
[  100.267151] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[  101.616628] wlan0: authenticate with <MAC address removed>
[  101.646695] wlan0: send auth to <MAC address removed> (try 1/3)
[  101.648689] wlan0: authenticated
[  101.657290] ath9k 0000:0c:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[  101.657297] ath9k 0000:0c:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[  101.660262] wlan0: associate with <MAC address removed> (try 1/3)
[  101.662883] wlan0: RX AssocResp from <MAC address removed> (capab=0x401 status=18 aid=0)
[  101.662889] wlan0: <MAC address removed> denied association (code=18)
[  101.679215] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[  102.624461] wlan0: authenticate with <MAC address removed>
[  102.647461] wlan0: send auth to <MAC address removed> (try 1/3)
[  102.651523] wlan0: authenticated
[  102.651728] ath9k 0000:0c:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[  102.651731] ath9k 0000:0c:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[  102.652048] wlan0: associate with <MAC address removed> (try 1/3)
[  102.654422] wlan0: RX AssocResp from <MAC address removed> (capab=0x401 status=18 aid=0)
[  102.654429] wlan0: <MAC address removed> denied association (code=18)
[  102.675057] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[  104.020852] wlan0: authenticate with <MAC address removed>
[  104.043087] wlan0: send auth to <MAC address removed> (try 1/3)
[  104.045166] wlan0: authenticated
[  104.045418] ath9k 0000:0c:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[  104.045426] ath9k 0000:0c:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[  104.052249] wlan0: associate with <MAC address removed> (try 1/3)
[  104.054679] wlan0: RX AssocResp from <MAC address removed> (capab=0x401 status=18 aid=0)
[  104.054687] wlan0: <MAC address removed> denied association (code=18)
[  104.067253] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[  105.023328] wlan0: authenticate with <MAC address removed>
[  105.040393] wlan0: send auth to <MAC address removed> (try 1/3)
[  105.042396] wlan0: authenticated
[  105.042668] ath9k 0000:0c:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[  105.042671] ath9k 0000:0c:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[  105.044083] wlan0: associate with <MAC address removed> (try 1/3)
[  105.046427] wlan0: RX AssocResp from <MAC address removed> (capab=0x401 status=18 aid=0)
[  105.046432] wlan0: <MAC address removed> denied association (code=18)
[  105.058967] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[  106.408475] wlan0: authenticate with <MAC address removed>
[  106.434861] wlan0: send auth to <MAC address removed> (try 1/3)
[  106.436899] wlan0: authenticated
[  106.437096] ath9k 0000:0c:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[  106.437100] ath9k 0000:0c:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[  106.440069] wlan0: associate with <MAC address removed> (try 1/3)
[  106.442395] wlan0: RX AssocResp from <MAC address removed> (capab=0x401 status=18 aid=0)
[  106.442401] wlan0: <MAC address removed> denied association (code=18)
[  106.475082] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[  107.424468] wlan0: authenticate with <MAC address removed>
[  107.446954] wlan0: send auth to <MAC address removed> (try 1/3)
[  107.448955] wlan0: authenticated
[  107.449218] ath9k 0000:0c:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[  107.449222] ath9k 0000:0c:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[  107.452138] wlan0: associate with <MAC address removed> (try 1/3)
[  107.454463] wlan0: RX AssocResp from <MAC address removed> (capab=0x401 status=18 aid=0)
[  107.454468] wlan0: <MAC address removed> denied association (code=18)
[  107.491033] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[  108.852487] wlan0: authenticate with <MAC address removed>
[  108.874913] wlan0: send auth to <MAC address removed> (try 1/3)
[  108.876903] wlan0: authenticated
[  108.877078] ath9k 0000:0c:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[  108.877082] ath9k 0000:0c:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[  108.880087] wlan0: associate with <MAC address removed> (try 1/3)
[  108.882491] wlan0: RX AssocResp from <MAC address removed> (capab=0x401 status=18 aid=0)
[  108.882496] wlan0: <MAC address removed> denied association (code=18)
[  108.899016] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[  109.844466] wlan0: authenticate with <MAC address removed>
[  109.867276] wlan0: send auth to <MAC address removed> (try 1/3)
[  109.869259] wlan0: authenticated
[  109.869404] ath9k 0000:0c:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[  109.869408] ath9k 0000:0c:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[  109.872042] wlan0: associate with <MAC address removed> (try 1/3)
[  109.874368] wlan0: RX AssocResp from <MAC address removed> (capab=0x401 status=18 aid=0)
[  109.874373] wlan0: <MAC address removed> denied association (code=18)
[  109.890952] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[  111.243453] wlan0: authenticate with <MAC address removed>
[  111.265212] wlan0: send auth to <MAC address removed> (try 1/3)
[  111.267198] wlan0: authenticated
[  111.267391] ath9k 0000:0c:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[  111.267394] ath9k 0000:0c:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[  111.268195] wlan0: associate with <MAC address removed> (try 1/3)
[  111.270522] wlan0: RX AssocResp from <MAC address removed> (capab=0x401 status=18 aid=0)
[  111.270528] wlan0: <MAC address removed> denied association (code=18)
[  111.290911] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[  112.240962] wlan0: authenticate with <MAC address removed>
[  112.264132] wlan0: send auth to <MAC address removed> (try 1/3)
[  112.266223] wlan0: authenticated
[  112.267230] ath9k 0000:0c:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[  112.267236] ath9k 0000:0c:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[  112.268095] wlan0: associate with <MAC address removed> (try 1/3)
[  112.270486] wlan0: RX AssocResp from <MAC address removed> (capab=0x401 status=18 aid=0)
[  112.270493] wlan0: <MAC address removed> denied association (code=18)
[  112.303004] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[  113.648413] wlan0: authenticate with <MAC address removed>
[  113.673223] wlan0: send auth to <MAC address removed> (try 1/3)
[  113.675258] wlan0: authenticated
[  113.675452] ath9k 0000:0c:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[  113.675459] ath9k 0000:0c:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[  113.676059] wlan0: associate with <MAC address removed> (try 1/3)
[  113.678393] wlan0: RX AssocResp from <MAC address removed> (capab=0x401 status=18 aid=0)
[  113.678399] wlan0: <MAC address removed> denied association (code=18)
[  113.714973] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[  114.663058] wlan0: authenticate with <MAC address removed>
[  114.683378] wlan0: send auth to <MAC address removed> (try 1/3)
[  114.685499] wlan0: authenticated
[  114.685669] ath9k 0000:0c:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[  114.685673] ath9k 0000:0c:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[  114.688105] wlan0: associate with <MAC address removed> (try 1/3)
[  114.690503] wlan0: RX AssocResp from <MAC address removed> (capab=0x401 status=18 aid=0)
[  114.690509] wlan0: <MAC address removed> denied association (code=18)
[  114.715016] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[  116.068411] wlan0: authenticate with <MAC address removed>
[  116.092880] wlan0: send auth to <MAC address removed> (try 1/3)
[  116.094950] wlan0: authenticated
[  116.095306] ath9k 0000:0c:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[  116.095310] ath9k 0000:0c:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[  116.096221] wlan0: associate with <MAC address removed> (try 1/3)
[  116.098544] wlan0: RX AssocResp from <MAC address removed> (capab=0x401 status=18 aid=0)
[  116.098549] wlan0: <MAC address removed> denied association (code=18)
[  116.119019] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[  117.072673] wlan0: authenticate with <MAC address removed>
[  117.096210] wlan0: send auth to <MAC address removed> (try 1/3)
[  117.098335] wlan0: authenticated
[  117.098523] ath9k 0000:0c:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[  117.098527] ath9k 0000:0c:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[  117.100332] wlan0: associate with <MAC address removed> (try 1/3)
[  117.102645] wlan0: RX AssocResp from <MAC address removed> (capab=0x401 status=18 aid=0)
[  117.102652] wlan0: <MAC address removed> denied association (code=18)
[  117.123147] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[  118.472463] wlan0: authenticate with <MAC address removed>
[  118.505891] wlan0: send auth to <MAC address removed> (try 1/3)
[  118.507872] wlan0: authenticated
[  118.509128] ath9k 0000:0c:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[  118.509133] ath9k 0000:0c:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[  118.512055] wlan0: associate with <MAC address removed> (try 1/3)
[  118.514631] wlan0: RX AssocResp from <MAC address removed> (capab=0x401 status=18 aid=0)
[  118.514637] wlan0: <MAC address removed> denied association (code=18)
[  118.537380] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[  119.507204] wlan0: authenticate with <MAC address removed>
[  119.536106] wlan0: send auth to <MAC address removed> (try 1/3)
[  119.538087] wlan0: authenticated
[  119.538212] ath9k 0000:0c:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[  119.538216] ath9k 0000:0c:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[  119.540056] wlan0: associate with <MAC address removed> (try 1/3)
[  119.542666] wlan0: RX AssocResp from <MAC address removed> (capab=0x401 status=18 aid=0)
[  119.542673] wlan0: <MAC address removed> denied association (code=18)
[  119.571050] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[  120.920862] wlan0: authenticate with <MAC address removed>
[  120.943352] wlan0: send auth to <MAC address removed> (try 1/3)
[  120.945468] wlan0: authenticated
[  120.945643] ath9k 0000:0c:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[  120.945647] ath9k 0000:0c:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[  120.948405] wlan0: associate with <MAC address removed> (try 1/3)
[  120.950811] wlan0: RX AssocResp from <MAC address removed> (capab=0x401 status=18 aid=0)
[  120.950817] wlan0: <MAC address removed> denied association (code=18)
[  120.967233] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[  121.912624] wlan0: authenticate with <MAC address removed>
[  121.937758] wlan0: send auth to <MAC address removed> (try 1/3)
[  121.939735] wlan0: authenticated
[  121.939892] ath9k 0000:0c:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[  121.939896] ath9k 0000:0c:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[  121.940099] wlan0: associate with <MAC address removed> (try 1/3)
[  121.942574] wlan0: RX AssocResp from <MAC address removed> (capab=0x401 status=18 aid=0)
[  121.942581] wlan0: <MAC address removed> denied association (code=18)
[  121.967289] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[  123.312670] wlan0: authenticate with <MAC address removed>
[  123.335165] wlan0: send auth to <MAC address removed> (try 1/3)
[  123.337256] wlan0: authenticated
[  123.337617] ath9k 0000:0c:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[  123.337621] ath9k 0000:0c:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[  123.340061] wlan0: associate with <MAC address removed> (try 1/3)
[  123.342433] wlan0: RX AssocResp from <MAC address removed> (capab=0x401 status=18 aid=0)
[  123.342439] wlan0: <MAC address removed> denied association (code=18)
[  123.371222] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[  124.324709] wlan0: authenticate with <MAC address removed>
[  124.350900] wlan0: send auth to <MAC address removed> (try 1/3)
[  124.352934] wlan0: authenticated
[  124.353112] ath9k 0000:0c:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[  124.353115] ath9k 0000:0c:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[  124.356079] wlan0: associate with <MAC address removed> (try 1/3)
[  124.358518] wlan0: RX AssocResp from <MAC address removed> (capab=0x401 status=18 aid=0)
[  124.358523] wlan0: <MAC address removed> denied association (code=18)
[  124.387209] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[  125.733264] wlan0: authenticate with <MAC address removed>
[  125.755337] wlan0: send auth to <MAC address removed> (try 1/3)
[  125.757713] wlan0: authenticated
[  125.757877] ath9k 0000:0c:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[  125.757881] ath9k 0000:0c:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[  125.760204] wlan0: associate with <MAC address removed> (try 1/3)
[  125.762607] wlan0: RX AssocResp from <MAC address removed> (capab=0x401 status=18 aid=0)
[  125.762611] wlan0: <MAC address removed> denied association (code=18)
[  125.791039] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[  126.740687] wlan0: authenticate with <MAC address removed>
[  126.763979] wlan0: send auth to <MAC address removed> (try 1/3)
[  126.766004] wlan0: authenticated
[  126.766167] ath9k 0000:0c:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[  126.766171] ath9k 0000:0c:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[  126.768057] wlan0: associate with <MAC address removed> (try 1/3)
[  126.770402] wlan0: RX AssocResp from <MAC address removed> (capab=0x401 status=18 aid=0)
[  126.770407] wlan0: <MAC address removed> denied association (code=18)
[  126.798951] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[  128.144643] wlan0: authenticate with <MAC address removed>
[  128.167321] wlan0: send auth to <MAC address removed> (try 1/3)
[  128.169303] wlan0: authenticated
[  128.172220] ath9k 0000:0c:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[  128.172226] ath9k 0000:0c:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[  128.176069] wlan0: associate with <MAC address removed> (try 1/3)
[  128.178516] wlan0: RX AssocResp from <MAC address removed> (capab=0x401 status=18 aid=0)
[  128.178524] wlan0: <MAC address removed> denied association (code=18)
[  128.195114] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[  129.144847] wlan0: authenticate with <MAC address removed>
[  129.167220] wlan0: send auth to <MAC address removed> (try 1/3)
[  129.169213] wlan0: authenticated
[  129.169374] ath9k 0000:0c:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[  129.169378] ath9k 0000:0c:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[  129.172945] wlan0: associate with <MAC address removed> (try 1/3)
[  129.175284] wlan0: RX AssocResp from <MAC address removed> (capab=0x401 status=18 aid=0)
[  129.175291] wlan0: <MAC address removed> denied association (code=18)
[  129.211142] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[  130.556851] wlan0: authenticate with <MAC address removed>
[  130.579239] wlan0: send auth to <MAC address removed> (try 1/3)
[  130.581273] wlan0: authenticated
[  130.581658] ath9k 0000:0c:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[  130.581662] ath9k 0000:0c:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[  130.584325] wlan0: associate with <MAC address removed> (try 1/3)
[  130.601833] wlan0: RX AssocResp from <MAC address removed> (capab=0x401 status=18 aid=0)
[  130.601842] wlan0: <MAC address removed> denied association (code=18)
[  130.639144] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[  131.584411] wlan0: authenticate with <MAC address removed>
[  131.609497] wlan0: send auth to <MAC address removed> (try 1/3)
[  131.611573] wlan0: authenticated
[  131.611739] ath9k 0000:0c:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[  131.611743] ath9k 0000:0c:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[  131.616233] wlan0: associate with <MAC address removed> (try 1/3)
[  131.618615] wlan0: RX AssocResp from <MAC address removed> (capab=0x401 status=18 aid=0)
[  131.618623] wlan0: <MAC address removed> denied association (code=18)
[  131.647103] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[  132.994368] wlan0: authenticate with <MAC address removed>
[  133.016126] wlan0: send auth to <MAC address removed> (try 1/3)
[  133.018107] wlan0: authenticated
[  133.018278] ath9k 0000:0c:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[  133.018282] ath9k 0000:0c:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[  133.020110] wlan0: associate with <MAC address removed> (try 1/3)
[  133.022559] wlan0: RX AssocResp from <MAC address removed> (capab=0x401 status=18 aid=0)
[  133.022565] wlan0: <MAC address removed> denied association (code=18)
[  133.051194] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[  134.000829] wlan0: authenticate with <MAC address removed>
[  134.025847] wlan0: send auth to <MAC address removed> (try 1/3)
[  134.030156] wlan0: authenticated
[  134.030353] ath9k 0000:0c:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[  134.030357] ath9k 0000:0c:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[  134.032243] wlan0: associate with <MAC address removed> (try 1/3)
[  134.034617] wlan0: RX AssocResp from <MAC address removed> (capab=0x401 status=18 aid=0)
[  134.034624] wlan0: <MAC address removed> denied association (code=18)
[  134.063156] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[  135.408843] wlan0: authenticate with <MAC address removed>
[  135.431286] wlan0: send auth to <MAC address removed> (try 1/3)
[  135.436250] wlan0: authenticated
[  135.436862] ath9k 0000:0c:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[  135.436866] ath9k 0000:0c:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[  135.444263] wlan0: associate with <MAC address removed> (try 1/3)
[  135.446676] wlan0: RX AssocResp from <MAC address removed> (capab=0x401 status=18 aid=0)
[  135.446684] wlan0: <MAC address removed> denied association (code=18)
[  135.479177] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[  136.439119] wlan0: authenticate with <MAC address removed>
[  136.469714] wlan0: send auth to <MAC address removed> (try 1/3)
[  136.471767] wlan0: authenticated
[  136.472237] ath9k 0000:0c:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[  136.472240] ath9k 0000:0c:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[  136.476345] wlan0: associate with <MAC address removed> (try 1/3)
[  136.478889] wlan0: RX AssocResp from <MAC address removed> (capab=0x401 status=18 aid=0)
[  136.478898] wlan0: <MAC address removed> denied association (code=18)
[  136.495036] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[  137.847102] wlan0: authenticate with <MAC address removed>
[  137.873594] wlan0: send auth to <MAC address removed> (try 1/3)
[  137.876425] wlan0: authenticated
[  137.877183] ath9k 0000:0c:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[  137.877187] ath9k 0000:0c:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[  137.880199] wlan0: associate with <MAC address removed> (try 1/3)
[  137.882686] wlan0: RX AssocResp from <MAC address removed> (capab=0x401 status=18 aid=0)
[  137.882692] wlan0: <MAC address removed> denied association (code=18)
[  137.903053] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[  138.855067] wlan0: authenticate with <MAC address removed>
[  138.884110] wlan0: send auth to <MAC address removed> (try 1/3)
[  138.886243] wlan0: authenticated
[  138.887040] ath9k 0000:0c:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[  138.887047] ath9k 0000:0c:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[  138.888296] wlan0: associate with <MAC address removed> (try 1/3)
[  138.890652] wlan0: RX AssocResp from <MAC address removed> (capab=0x401 status=18 aid=0)
[  138.890660] wlan0: <MAC address removed> denied association (code=18)
[  138.927508] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[  142.872732] wlan0: authenticate with <MAC address removed>
[  142.895001] wlan0: send auth to <MAC address removed> (try 1/3)
[  142.897109] wlan0: authenticated
[  142.897283] ath9k 0000:0c:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[  142.897287] ath9k 0000:0c:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[  142.900203] wlan0: associate with <MAC address removed> (try 1/3)
[  142.902613] wlan0: RX AssocResp from <MAC address removed> (capab=0x401 status=18 aid=0)
[  142.902618] wlan0: <MAC address removed> denied association (code=18)
[  142.927004] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[  143.884715] wlan0: authenticate with <MAC address removed>
[  143.908252] wlan0: send auth to <MAC address removed> (try 1/3)
[  143.910354] wlan0: authenticated
[  143.910752] ath9k 0000:0c:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[  143.910756] ath9k 0000:0c:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[  143.916113] wlan0: associate with <MAC address removed> (try 1/3)
[  143.918817] wlan0: RX AssocResp from <MAC address removed> (capab=0x401 status=18 aid=0)
[  143.918824] wlan0: <MAC address removed> denied association (code=18)
[  143.951332] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[  145.300908] wlan0: authenticate with <MAC address removed>
[  145.323083] wlan0: send auth to <MAC address removed> (try 1/3)
[  145.325160] wlan0: authenticated
[  145.325366] ath9k 0000:0c:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[  145.325373] ath9k 0000:0c:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[  145.328145] wlan0: associate with <MAC address removed> (try 1/3)
[  145.330569] wlan0: RX AssocResp from <MAC address removed> (capab=0x401 status=18 aid=0)
[  145.330578] wlan0: <MAC address removed> denied association (code=18)
[  145.343204] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[  146.288755] wlan0: authenticate with <MAC address removed>
[  146.311169] wlan0: send auth to <MAC address removed> (try 1/3)
[  146.313668] wlan0: authenticated
[  146.313846] ath9k 0000:0c:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[  146.313850] ath9k 0000:0c:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[  146.316241] wlan0: associate with <MAC address removed> (try 1/3)
[  146.319567] wlan0: RX AssocResp from <MAC address removed> (capab=0x401 status=18 aid=0)
[  146.319571] wlan0: <MAC address removed> denied association (code=18)
[  146.327219] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[  147.674183] wlan0: authenticate with <MAC address removed>
[  147.697278] wlan0: send auth to <MAC address removed> (try 1/3)
[  147.699302] wlan0: authenticated
[  147.699477] ath9k 0000:0c:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[  147.699481] ath9k 0000:0c:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[  147.700068] wlan0: associate with <MAC address removed> (try 1/3)
[  147.702372] wlan0: RX AssocResp from <MAC address removed> (capab=0x401 status=18 aid=0)
[  147.702379] wlan0: <MAC address removed> denied association (code=18)
[  147.718988] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[  148.665182] wlan0: authenticate with <MAC address removed>
[  148.687256] wlan0: send auth to <MAC address removed> (try 1/3)
[  148.689277] wlan0: authenticated
[  148.689626] ath9k 0000:0c:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[  148.689630] ath9k 0000:0c:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[  148.692044] wlan0: associate with <MAC address removed> (try 1/3)
[  148.694388] wlan0: RX AssocResp from <MAC address removed> (capab=0x401 status=18 aid=0)
[  148.694394] wlan0: <MAC address removed> denied association (code=18)
[  148.727249] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[  150.079315] wlan0: authenticate with <MAC address removed>
[  150.099381] wlan0: send auth to <MAC address removed> (try 1/3)
[  150.101374] wlan0: authenticated
[  150.101524] ath9k 0000:0c:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[  150.101528] ath9k 0000:0c:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[  150.104078] wlan0: associate with <MAC address removed> (try 1/3)
[  150.108243] wlan0: RX AssocResp from <MAC address removed> (capab=0x401 status=18 aid=0)
[  150.108249] wlan0: <MAC address removed> denied association (code=18)
[  150.139322] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[  151.084842] wlan0: authenticate with <MAC address removed>
[  151.108095] wlan0: send auth to <MAC address removed> (try 1/3)
[  151.110151] wlan0: authenticated
[  151.110325] ath9k 0000:0c:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[  151.110328] ath9k 0000:0c:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[  151.112049] wlan0: associate with <MAC address removed> (try 1/3)
[  151.114443] wlan0: RX AssocResp from <MAC address removed> (capab=0x401 status=18 aid=0)
[  151.114450] wlan0: <MAC address removed> denied association (code=18)
[  151.139477] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[  152.488830] wlan0: authenticate with <MAC address removed>
[  152.511220] wlan0: send auth to <MAC address removed> (try 1/3)
[  152.513216] wlan0: authenticated
[  152.513356] ath9k 0000:0c:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[  152.513360] ath9k 0000:0c:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[  152.516256] wlan0: associate with <MAC address removed> (try 1/3)
[  152.518561] wlan0: RX AssocResp from <MAC address removed> (capab=0x401 status=18 aid=0)
[  152.518567] wlan0: <MAC address removed> denied association (code=18)
[  152.551122] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[  153.497478] wlan0: authenticate with <MAC address removed>
[  153.519197] wlan0: send auth to <MAC address removed> (try 1/3)
[  153.521296] wlan0: authenticated
[  153.522255] ath9k 0000:0c:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[  153.522263] ath9k 0000:0c:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[  153.524075] wlan0: associate with <MAC address removed> (try 1/3)
[  153.526468] wlan0: RX AssocResp from <MAC address removed> (capab=0x401 status=18 aid=0)
[  153.526475] wlan0: <MAC address removed> denied association (code=18)
[  153.547050] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[  154.897412] wlan0: authenticate with <MAC address removed>
[  154.919128] wlan0: send auth to <MAC address removed> (try 1/3)
[  154.921241] wlan0: authenticated
[  154.921417] ath9k 0000:0c:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[  154.921422] ath9k 0000:0c:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[  154.924241] wlan0: associate with <MAC address removed> (try 1/3)
[  154.926659] wlan0: RX AssocResp from <MAC address removed> (capab=0x401 status=18 aid=0)
[  154.926665] wlan0: <MAC address removed> denied association (code=18)
[  154.955390] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[  155.904845] wlan0: authenticate with <MAC address removed>
[  155.927193] wlan0: send auth to <MAC address removed> (try 1/3)
[  155.929320] wlan0: authenticated
[  155.929535] ath9k 0000:0c:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[  155.929539] ath9k 0000:0c:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[  155.932264] wlan0: associate with <MAC address removed> (try 1/3)
[  155.934595] wlan0: RX AssocResp from <MAC address removed> (capab=0x401 status=18 aid=0)
[  155.934601] wlan0: <MAC address removed> denied association (code=18)
[  155.963112] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[  157.319331] wlan0: authenticate with <MAC address removed>
[  157.335909] wlan0: send auth to <MAC address removed> (try 1/3)
[  157.337918] wlan0: authenticated
[  157.338113] ath9k 0000:0c:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[  157.338120] ath9k 0000:0c:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[  157.340237] wlan0: associate with <MAC address removed> (try 1/3)
[  157.342682] wlan0: RX AssocResp from <MAC address removed> (capab=0x401 status=18 aid=0)
[  157.342691] wlan0: <MAC address removed> denied association (code=18)
[  157.375049] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[  158.320864] wlan0: authenticate with <MAC address removed>
[  158.342880] wlan0: send auth to <MAC address removed> (try 1/3)
[  158.344867] wlan0: authenticated
[  158.345064] ath9k 0000:0c:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[  158.345068] ath9k 0000:0c:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[  158.348231] wlan0: associate with <MAC address removed> (try 1/3)
[  158.350623] wlan0: RX AssocResp from <MAC address removed> (capab=0x401 status=18 aid=0)
[  158.350630] wlan0: <MAC address removed> denied association (code=18)
[  158.371690] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[  159.732436] wlan0: authenticate with <MAC address removed>
[  159.760115] wlan0: send auth to <MAC address removed> (try 1/3)
[  159.762105] wlan0: authenticated
[  159.762428] ath9k 0000:0c:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[  159.762432] ath9k 0000:0c:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[  159.764048] wlan0: associate with <MAC address removed> (try 1/3)
[  159.766470] wlan0: RX AssocResp from <MAC address removed> (capab=0x401 status=18 aid=0)
[  159.766476] wlan0: <MAC address removed> denied association (code=18)
[  159.803162] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[  160.752458] wlan0: authenticate with <MAC address removed>
[  160.775408] wlan0: send auth to <MAC address removed> (try 1/3)
[  160.777380] wlan0: authenticated
[  160.780505] ath9k 0000:0c:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[  160.780511] ath9k 0000:0c:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[  160.784052] wlan0: associate with <MAC address removed> (try 1/3)
[  160.786366] wlan0: RX AssocResp from <MAC address removed> (capab=0x401 status=18 aid=0)
[  160.786373] wlan0: <MAC address removed> denied association (code=18)
[  160.811247] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[  162.160912] wlan0: authenticate with <MAC address removed>
[  162.183009] wlan0: send auth to <MAC address removed> (try 1/3)
[  162.185002] wlan0: authenticated
[  162.185219] ath9k 0000:0c:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[  162.185222] ath9k 0000:0c:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[  162.188287] wlan0: associate with <MAC address removed> (try 1/3)
[  162.191674] wlan0: RX AssocResp from <MAC address removed> (capab=0x401 status=18 aid=0)
[  162.191684] wlan0: <MAC address removed> denied association (code=18)
[  162.219059] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[  163.176819] wlan0: authenticate with <MAC address removed>
[  163.199190] wlan0: send auth to <MAC address removed> (try 1/3)
[  163.201413] wlan0: authenticated
[  163.201589] ath9k 0000:0c:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[  163.201593] ath9k 0000:0c:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[  163.204054] wlan0: associate with <MAC address removed> (try 1/3)
[  163.206558] wlan0: RX AssocResp from <MAC address removed> (capab=0x401 status=18 aid=0)
[  163.206565] wlan0: <MAC address removed> denied association (code=18)
[  163.235212] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[  164.580860] wlan0: authenticate with <MAC address removed>
[  164.603103] wlan0: send auth to <MAC address removed> (try 1/3)
[  164.605255] wlan0: authenticated
[  164.605496] ath9k 0000:0c:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[  164.605500] ath9k 0000:0c:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[  164.608207] wlan0: associate with <MAC address removed> (try 1/3)
[  164.610639] wlan0: RX AssocResp from <MAC address removed> (capab=0x401 status=18 aid=0)
[  164.610648] wlan0: <MAC address removed> denied association (code=18)
[  164.647115] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[  165.596913] wlan0: authenticate with <MAC address removed>
[  165.619270] wlan0: send auth to <MAC address removed> (try 1/3)
[  165.621387] wlan0: authenticated
[  165.622068] ath9k 0000:0c:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[  165.622072] ath9k 0000:0c:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[  165.625110] wlan0: associate with <MAC address removed> (try 1/3)
[  165.627430] wlan0: RX AssocResp from <MAC address removed> (capab=0x401 status=18 aid=0)
[  165.627436] wlan0: <MAC address removed> denied association (code=18)
[  165.643238] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[  166.988863] wlan0: authenticate with <MAC address removed>
[  167.011028] wlan0: send auth to <MAC address removed> (try 1/3)
[  167.013116] wlan0: authenticated
[  167.013400] ath9k 0000:0c:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[  167.013404] ath9k 0000:0c:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[  167.016269] wlan0: associate with <MAC address removed> (try 1/3)
[  167.018689] wlan0: RX AssocResp from <MAC address removed> (capab=0x401 status=18 aid=0)
[  167.018695] wlan0: <MAC address removed> denied association (code=18)
[  167.027212] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[  167.976857] wlan0: authenticate with <MAC address removed>
[  167.999055] wlan0: send auth to <MAC address removed> (try 1/3)
[  168.001110] wlan0: authenticated
[  168.001289] ath9k 0000:0c:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[  168.001292] ath9k 0000:0c:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[  168.004302] wlan0: associate with <MAC address removed> (try 1/3)
[  168.006610] wlan0: RX AssocResp from <MAC address removed> (capab=0x401 status=18 aid=0)
[  168.006616] wlan0: <MAC address removed> denied association (code=18)
[  168.019171] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[  169.364624] wlan0: authenticate with <MAC address removed>
[  169.389742] wlan0: send auth to <MAC address removed> (try 1/3)
[  169.391800] wlan0: authenticated
[  169.391976] ath9k 0000:0c:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[  169.391980] ath9k 0000:0c:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[  169.392178] wlan0: associate with <MAC address removed> (try 1/3)
[  169.394562] wlan0: RX AssocResp from <MAC address removed> (capab=0x401 status=18 aid=0)
[  169.394567] wlan0: <MAC address removed> denied association (code=18)
[  169.423147] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[  170.372813] wlan0: authenticate with <MAC address removed>
[  170.391551] wlan0: send auth to <MAC address removed> (try 1/3)
[  170.393612] wlan0: authenticated
[  170.393858] ath9k 0000:0c:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[  170.393863] ath9k 0000:0c:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[  170.396272] wlan0: associate with <MAC address removed> (try 1/3)
[  170.398739] wlan0: RX AssocResp from <MAC address removed> (capab=0x401 status=18 aid=0)
[  170.398744] wlan0: <MAC address removed> denied association (code=18)
[  170.431186] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[  171.779213] wlan0: authenticate with <MAC address removed>
[  171.799670] wlan0: send auth to <MAC address removed> (try 1/3)
[  171.801764] wlan0: authenticated
[  171.801938] ath9k 0000:0c:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[  171.801942] ath9k 0000:0c:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[  171.804238] wlan0: associate with <MAC address removed> (try 1/3)
[  171.806719] wlan0: RX AssocResp from <MAC address removed> (capab=0x401 status=18 aid=0)
[  171.806725] wlan0: <MAC address removed> denied association (code=18)
[  171.827161] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[  172.772631] wlan0: authenticate with <MAC address removed>
[  172.796594] wlan0: send auth to <MAC address removed> (try 1/3)
[  172.798592] wlan0: authenticated
[  172.799789] ath9k 0000:0c:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[  172.799793] ath9k 0000:0c:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[  172.800041] wlan0: associate with <MAC address removed> (try 1/3)
[  172.802403] wlan0: RX AssocResp from <MAC address removed> (capab=0x401 status=18 aid=0)
[  172.802408] wlan0: <MAC address removed> denied association (code=18)
[  172.835328] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[  174.180715] wlan0: authenticate with <MAC address removed>
[  174.210768] wlan0: send auth to <MAC address removed> (try 1/3)
[  174.212852] wlan0: authenticated
[  174.213325] ath9k 0000:0c:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[  174.213329] ath9k 0000:0c:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[  174.216459] wlan0: associate with <MAC address removed> (try 1/3)
[  174.218827] wlan0: RX AssocResp from <MAC address removed> (capab=0x401 status=18 aid=0)
[  174.218834] wlan0: <MAC address removed> denied association (code=18)
[  174.247133] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[  175.196847] wlan0: authenticate with <MAC address removed>
[  175.223993] wlan0: send auth to <MAC address removed> (try 1/3)
[  175.228059] wlan0: authenticated
[  175.229536] ath9k 0000:0c:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[  175.229542] ath9k 0000:0c:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[  175.232123] wlan0: associate with <MAC address removed> (try 1/3)
[  175.234606] wlan0: RX AssocResp from <MAC address removed> (capab=0x401 status=18 aid=0)
[  175.234613] wlan0: <MAC address removed> denied association (code=18)
[  175.263316] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[  176.612443] wlan0: authenticate with <MAC address removed>
[  176.633247] wlan0: send auth to <MAC address removed> (try 1/3)
[  176.635293] wlan0: authenticated
[  176.635470] ath9k 0000:0c:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[  176.635474] ath9k 0000:0c:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[  176.636244] wlan0: associate with <MAC address removed> (try 1/3)
[  176.638632] wlan0: RX AssocResp from <MAC address removed> (capab=0x401 status=18 aid=0)
[  176.638638] wlan0: <MAC address removed> denied association (code=18)
[  176.651194] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[  177.596630] wlan0: authenticate with <MAC address removed>
[  177.619132] wlan0: send auth to <MAC address removed> (try 1/3)
[  177.621620] wlan0: authenticated
[  177.621951] ath9k 0000:0c:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[  177.621955] ath9k 0000:0c:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[  177.624053] wlan0: associate with <MAC address removed> (try 1/3)
[  177.626425] wlan0: RX AssocResp from <MAC address removed> (capab=0x401 status=18 aid=0)
[  177.626432] wlan0: <MAC address removed> denied association (code=18)
[  177.655161] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[  179.004868] wlan0: authenticate with <MAC address removed>
[  179.027134] wlan0: send auth to <MAC address removed> (try 1/3)
[  179.029274] wlan0: authenticated
[  179.029645] ath9k 0000:0c:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[  179.029650] ath9k 0000:0c:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[  179.032046] wlan0: associate with <MAC address removed> (try 1/3)
[  179.034390] wlan0: RX AssocResp from <MAC address removed> (capab=0x401 status=18 aid=0)
[  179.034395] wlan0: <MAC address removed> denied association (code=18)
[  179.067144] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[  180.016874] wlan0: authenticate with <MAC address removed>
[  180.039240] wlan0: send auth to <MAC address removed> (try 1/3)
[  180.041230] wlan0: authenticated
[  180.041370] ath9k 0000:0c:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[  180.041374] ath9k 0000:0c:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[  180.044067] wlan0: associate with <MAC address removed> (try 1/3)
[  180.047526] wlan0: RX AssocResp from <MAC address removed> (capab=0x401 status=18 aid=0)
[  180.047532] wlan0: <MAC address removed> denied association (code=18)
[  180.079289] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[  181.428807] wlan0: authenticate with <MAC address removed>
[  181.451306] wlan0: send auth to <MAC address removed> (try 1/3)
[  181.454290] wlan0: authenticated
[  181.455307] ath9k 0000:0c:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[  181.455312] ath9k 0000:0c:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[  181.456334] wlan0: associate with <MAC address removed> (try 1/3)
[  181.458677] wlan0: RX AssocResp from <MAC address removed> (capab=0x401 status=18 aid=0)
[  181.458684] wlan0: <MAC address removed> denied association (code=18)
[  181.487369] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[  182.432881] wlan0: authenticate with <MAC address removed>
[  182.455283] wlan0: send auth to <MAC address removed> (try 1/3)
[  182.457371] wlan0: authenticated
[  182.464104] ath9k 0000:0c:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[  182.464110] ath9k 0000:0c:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[  182.468252] wlan0: associate with <MAC address removed> (try 1/3)
[  182.470673] wlan0: RX AssocResp from <MAC address removed> (capab=0x401 status=18 aid=0)
[  182.470680] wlan0: <MAC address removed> denied association (code=18)
[  182.503257] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[  183.848926] wlan0: authenticate with <MAC address removed>
[  183.871413] wlan0: send auth to <MAC address removed> (try 1/3)
[  183.873396] wlan0: authenticated
[  183.873535] ath9k 0000:0c:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[  183.873539] ath9k 0000:0c:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[  183.876057] wlan0: associate with <MAC address removed> (try 1/3)
[  183.878362] wlan0: RX AssocResp from <MAC address removed> (capab=0x401 status=18 aid=0)
[  183.878367] wlan0: <MAC address removed> denied association (code=18)
[  183.899413] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[  184.844855] wlan0: authenticate with <MAC address removed>
[  184.867338] wlan0: send auth to <MAC address removed> (try 1/3)
[  184.869615] wlan0: authenticated
[  184.869883] ath9k 0000:0c:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[  184.869887] ath9k 0000:0c:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[  184.872258] wlan0: associate with <MAC address removed> (try 1/3)
[  184.874662] wlan0: RX AssocResp from <MAC address removed> (capab=0x401 status=18 aid=0)
[  184.874671] wlan0: <MAC address removed> denied association (code=18)
[  184.891045] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[  186.236444] wlan0: authenticate with <MAC address removed>
[  186.259181] wlan0: send auth to <MAC address removed> (try 1/3)
[  186.261284] wlan0: authenticated
[  186.261461] ath9k 0000:0c:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[  186.261465] ath9k 0000:0c:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[  186.264094] wlan0: associate with <MAC address removed> (try 1/3)
[  186.266454] wlan0: RX AssocResp from <MAC address removed> (capab=0x401 status=18 aid=0)
[  186.266460] wlan0: <MAC address removed> denied association (code=18)
[  186.283081] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[  187.239291] wlan0: authenticate with <MAC address removed>
[  187.262924] wlan0: send auth to <MAC address removed> (try 1/3)
[  187.264911] wlan0: authenticated
[  187.265162] ath9k 0000:0c:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[  187.265166] ath9k 0000:0c:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[  187.268157] wlan0: associate with <MAC address removed> (try 1/3)
[  187.270566] wlan0: RX AssocResp from <MAC address removed> (capab=0x401 status=18 aid=0)
[  187.270571] wlan0: <MAC address removed> denied association (code=18)
[  187.296166] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[  188.648909] wlan0: authenticate with <MAC address removed>
[  188.671139] wlan0: send auth to <MAC address removed> (try 1/3)
[  188.673288] wlan0: authenticated
[  188.673916] ath9k 0000:0c:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[  188.673920] ath9k 0000:0c:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[  188.676156] wlan0: associate with <MAC address removed> (try 1/3)
[  188.678530] wlan0: RX AssocResp from <MAC address removed> (capab=0x401 status=18 aid=0)
[  188.678538] wlan0: <MAC address removed> denied association (code=18)
[  188.699225] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[  189.644823] wlan0: authenticate with <MAC address removed>
[  189.667151] wlan0: send auth to <MAC address removed> (try 1/3)
[  189.669226] wlan0: authenticated
[  189.669474] ath9k 0000:0c:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[  189.669478] ath9k 0000:0c:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[  189.672244] wlan0: associate with <MAC address removed> (try 1/3)
[  189.674664] wlan0: RX AssocResp from <MAC address removed> (capab=0x401 status=18 aid=0)
[  189.674670] wlan0: <MAC address removed> denied association (code=18)
[  189.683210] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[  191.039452] wlan0: authenticate with <MAC address removed>
[  191.056713] wlan0: send auth to <MAC address removed> (try 1/3)
[  191.059361] wlan0: authenticated
[  191.059527] ath9k 0000:0c:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[  191.059531] ath9k 0000:0c:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[  191.064232] wlan0: associate with <MAC address removed> (try 1/3)
[  191.068778] wlan0: RX AssocResp from <MAC address removed> (capab=0x401 status=18 aid=0)
[  191.068784] wlan0: <MAC address removed> denied association (code=18)
[  191.095145] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[  192.049116] wlan0: authenticate with <MAC address removed>
[  192.067446] wlan0: send auth to <MAC address removed> (try 1/3)
[  192.069452] wlan0: authenticated
[  192.069816] ath9k 0000:0c:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[  192.069820] ath9k 0000:0c:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[  192.076064] wlan0: associate with <MAC address removed> (try 1/3)
[  192.078581] wlan0: RX AssocResp from <MAC address removed> (capab=0x401 status=18 aid=0)
[  192.078587] wlan0: <MAC address removed> denied association (code=18)
[  192.095214] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[  193.444653] wlan0: authenticate with <MAC address removed>
[  193.467279] wlan0: send auth to <MAC address removed> (try 1/3)
[  193.469350] wlan0: authenticated
[  193.469522] ath9k 0000:0c:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[  193.469526] ath9k 0000:0c:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[  193.476233] wlan0: associate with <MAC address removed> (try 1/3)
[  193.478547] wlan0: RX AssocResp from <MAC address removed> (capab=0x401 status=18 aid=0)
[  193.478551] wlan0: <MAC address removed> denied association (code=18)
[  193.487210] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[  194.436793] wlan0: authenticate with <MAC address removed>
[  194.459365] wlan0: send auth to <MAC address removed> (try 1/3)
[  194.462992] wlan0: authenticated
[  194.463158] ath9k 0000:0c:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[  194.463162] ath9k 0000:0c:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[  194.464049] wlan0: associate with <MAC address removed> (try 1/3)
[  194.466407] wlan0: RX AssocResp from <MAC address removed> (capab=0x401 status=18 aid=0)
[  194.466412] wlan0: <MAC address removed> denied association (code=18)
[  194.503159] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[  195.852846] wlan0: authenticate with <MAC address removed>
[  195.875678] wlan0: send auth to <MAC address removed> (try 1/3)
[  195.877681] wlan0: authenticated
[  195.877829] ath9k 0000:0c:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[  195.877833] ath9k 0000:0c:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[  195.880049] wlan0: associate with <MAC address removed> (try 1/3)
[  195.882449] wlan0: RX AssocResp from <MAC address removed> (capab=0x401 status=18 aid=0)
[  195.882455] wlan0: <MAC address removed> denied association (code=18)
[  195.899171] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[  196.848815] wlan0: authenticate with <MAC address removed>
[  196.871099] wlan0: send auth to <MAC address removed> (try 1/3)
[  196.873322] wlan0: authenticated
[  196.873486] ath9k 0000:0c:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[  196.873489] ath9k 0000:0c:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[  196.876065] wlan0: associate with <MAC address removed> (try 1/3)
[  196.878402] wlan0: RX AssocResp from <MAC address removed> (capab=0x401 status=18 aid=0)
[  196.878409] wlan0: <MAC address removed> denied association (code=18)
[  196.903215] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[  198.252844] wlan0: authenticate with <MAC address removed>
[  198.275073] wlan0: send auth to <MAC address removed> (try 1/3)
[  198.277126] wlan0: authenticated
[  198.277300] ath9k 0000:0c:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[  198.277304] ath9k 0000:0c:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[  198.280144] wlan0: associate with <MAC address removed> (try 1/3)
[  198.282969] wlan0: RX AssocResp from <MAC address removed> (capab=0x401 status=18 aid=0)
[  198.282975] wlan0: <MAC address removed> denied association (code=18)
[  198.311102] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[  199.256727] wlan0: authenticate with <MAC address removed>
[  199.279961] wlan0: send auth to <MAC address removed> (try 1/3)
[  199.282107] wlan0: authenticated
[  199.282281] ath9k 0000:0c:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[  199.282285] ath9k 0000:0c:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[  199.284237] wlan0: associate with <MAC address removed> (try 1/3)
[  199.286581] wlan0: RX AssocResp from <MAC address removed> (capab=0x401 status=18 aid=0)
[  199.286587] wlan0: <MAC address removed> denied association (code=18)
[  199.307123] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[  200.660816] wlan0: authenticate with <MAC address removed>
[  200.683076] wlan0: send auth to <MAC address removed> (try 1/3)
[  200.685151] wlan0: authenticated
[  200.685322] ath9k 0000:0c:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[  200.685325] ath9k 0000:0c:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[  200.688073] wlan0: associate with <MAC address removed> (try 1/3)
[  200.690481] wlan0: RX AssocResp from <MAC address removed> (capab=0x401 status=18 aid=0)
[  200.690488] wlan0: <MAC address removed> denied association (code=18)
[  200.703986] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[  201.648733] wlan0: authenticate with <MAC address removed>
[  201.671206] wlan0: send auth to <MAC address removed> (try 1/3)
[  201.673254] wlan0: authenticated
[  201.673428] ath9k 0000:0c:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[  201.673432] ath9k 0000:0c:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[  201.676233] wlan0: associate with <MAC address removed> (try 1/3)
[  201.678661] wlan0: RX AssocResp from <MAC address removed> (capab=0x401 status=18 aid=0)
[  201.678671] wlan0: <MAC address removed> denied association (code=18)
[  201.691116] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[  205.872850] wlan0: authenticate with <MAC address removed>
[  205.895154] wlan0: send auth to <MAC address removed> (try 1/3)
[  205.897201] wlan0: authenticated
[  205.897377] ath9k 0000:0c:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[  205.897381] ath9k 0000:0c:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[  205.900229] wlan0: associate with <MAC address removed> (try 1/3)
[  205.902622] wlan0: RX AssocResp from <MAC address removed> (capab=0x401 status=18 aid=0)
[  205.902628] wlan0: <MAC address removed> denied association (code=18)
[  205.923266] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[  206.868818] wlan0: authenticate with <MAC address removed>
[  206.891054] wlan0: send auth to <MAC address removed> (try 1/3)
[  206.893171] wlan0: authenticated
[  206.893340] ath9k 0000:0c:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[  206.893344] ath9k 0000:0c:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[  206.896240] wlan0: associate with <MAC address removed> (try 1/3)
[  206.898631] wlan0: RX AssocResp from <MAC address removed> (capab=0x401 status=18 aid=0)
[  206.898638] wlan0: <MAC address removed> denied association (code=18)
[  206.911133] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[  208.264825] wlan0: authenticate with <MAC address removed>
[  208.287200] wlan0: send auth to <MAC address removed> (try 1/3)
[  208.289284] wlan0: authenticated
[  208.289477] ath9k 0000:0c:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[  208.289481] ath9k 0000:0c:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[  208.292257] wlan0: associate with <MAC address removed> (try 1/3)
[  208.294747] wlan0: RX AssocResp from <MAC address removed> (capab=0x401 status=18 aid=0)
[  208.294753] wlan0: <MAC address removed> denied association (code=18)
[  208.315171] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[  209.264699] wlan0: authenticate with <MAC address removed>
[  209.287076] wlan0: send auth to <MAC address removed> (try 1/3)
[  209.289125] wlan0: authenticated
[  209.289306] ath9k 0000:0c:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[  209.289310] ath9k 0000:0c:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[  209.292245] wlan0: associate with <MAC address removed> (try 1/3)
[  209.296281] wlan0: RX AssocResp from <MAC address removed> (capab=0x401 status=18 aid=0)
[  209.296288] wlan0: <MAC address removed> denied association (code=18)
[  209.323121] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[  210.671052] wlan0: authenticate with <MAC address removed>
[  210.691701] wlan0: send auth to <MAC address removed> (try 1/3)
[  210.693843] wlan0: authenticated
[  210.694015] ath9k 0000:0c:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[  210.694019] ath9k 0000:0c:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[  210.696329] wlan0: associate with <MAC address removed> (try 1/3)
[  210.698769] wlan0: RX AssocResp from <MAC address removed> (capab=0x401 status=18 aid=0)
[  210.698774] wlan0: <MAC address removed> denied association (code=18)
[  210.727273] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[  211.676514] wlan0: authenticate with <MAC address removed>
[  211.700572] wlan0: send auth to <MAC address removed> (try 1/3)
[  211.702698] wlan0: authenticated
[  211.702872] ath9k 0000:0c:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[  211.702875] ath9k 0000:0c:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[  211.704408] wlan0: associate with <MAC address removed> (try 1/3)
[  211.706829] wlan0: RX AssocResp from <MAC address removed> (capab=0x401 status=18 aid=0)
[  211.706836] wlan0: <MAC address removed> denied association (code=18)
[  211.735284] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[  213.084589] wlan0: authenticate with <MAC address removed>
[  213.107109] wlan0: send auth to <MAC address removed> (try 1/3)
[  213.109182] wlan0: authenticated
[  213.109357] ath9k 0000:0c:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[  213.109361] ath9k 0000:0c:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[  213.112231] wlan0: associate with <MAC address removed> (try 1/3)
[  213.114647] wlan0: RX AssocResp from <MAC address removed> (capab=0x401 status=18 aid=0)
[  213.114653] wlan0: <MAC address removed> denied association (code=18)
[  213.127229] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[  214.083525] wlan0: authenticate with <MAC address removed>
[  214.100913] wlan0: send auth to <MAC address removed> (try 1/3)
[  214.102929] wlan0: authenticated
[  214.103241] ath9k 0000:0c:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[  214.103245] ath9k 0000:0c:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[  214.104198] wlan0: associate with <MAC address removed> (try 1/3)
[  214.108708] wlan0: RX AssocResp from <MAC address removed> (capab=0x401 status=18 aid=0)
[  214.108715] wlan0: <MAC address removed> denied association (code=18)
[  214.127358] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[  215.480850] wlan0: authenticate with <MAC address removed>
[  215.503569] wlan0: send auth to <MAC address removed> (try 1/3)
[  215.505563] wlan0: authenticated
[  215.505703] ath9k 0000:0c:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[  215.505707] ath9k 0000:0c:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[  215.508068] wlan0: associate with <MAC address removed> (try 1/3)
[  215.510373] wlan0: RX AssocResp from <MAC address removed> (capab=0x401 status=18 aid=0)
[  215.510379] wlan0: <MAC address removed> denied association (code=18)
[  215.543292] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[  216.488700] wlan0: authenticate with <MAC address removed>
[  216.511234] wlan0: send auth to <MAC address removed> (try 1/3)
[  216.513214] wlan0: authenticated
[  216.513881] ath9k 0000:0c:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[  216.513887] ath9k 0000:0c:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[  216.516058] wlan0: associate with <MAC address removed> (try 1/3)
[  216.518490] wlan0: RX AssocResp from <MAC address removed> (capab=0x401 status=18 aid=0)
[  216.518496] wlan0: <MAC address removed> denied association (code=18)
[  216.547237] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[  217.892426] wlan0: authenticate with <MAC address removed>
[  217.916082] wlan0: send auth to <MAC address removed> (try 1/3)
[  217.918106] wlan0: authenticated
[  217.918265] ath9k 0000:0c:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[  217.918269] ath9k 0000:0c:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[  217.924483] wlan0: associate with <MAC address removed> (try 1/3)
[  217.926915] wlan0: RX AssocResp from <MAC address removed> (capab=0x401 status=18 aid=0)
[  217.926922] wlan0: <MAC address removed> denied association (code=18)
[  217.955057] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[  218.900844] wlan0: authenticate with <MAC address removed>
[  218.923086] wlan0: send auth to <MAC address removed> (try 1/3)
[  218.925154] wlan0: authenticated
[  218.925329] ath9k 0000:0c:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[  218.925333] ath9k 0000:0c:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[  218.928064] wlan0: associate with <MAC address removed> (try 1/3)
[  218.930517] wlan0: RX AssocResp from <MAC address removed> (capab=0x401 status=18 aid=0)
[  218.930523] wlan0: <MAC address removed> denied association (code=18)
[  218.959115] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[  220.304825] wlan0: authenticate with <MAC address removed>
[  220.327211] wlan0: send auth to <MAC address removed> (try 1/3)
[  220.329385] wlan0: authenticated
[  220.329556] ath9k 0000:0c:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[  220.329560] ath9k 0000:0c:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[  220.332243] wlan0: associate with <MAC address removed> (try 1/3)
[  220.334623] wlan0: RX AssocResp from <MAC address removed> (capab=0x401 status=18 aid=0)
[  220.334629] wlan0: <MAC address removed> denied association (code=18)
[  220.355746] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[  221.300853] wlan0: authenticate with <MAC address removed>
[  221.327103] wlan0: send auth to <MAC address removed> (try 1/3)
[  221.329246] wlan0: authenticated
[  221.329420] ath9k 0000:0c:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[  221.329424] ath9k 0000:0c:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[  221.332062] wlan0: associate with <MAC address removed> (try 1/3)
[  221.334493] wlan0: RX AssocResp from <MAC address removed> (capab=0x401 status=18 aid=0)
[  221.334499] wlan0: <MAC address removed> denied association (code=18)
[  221.371107] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)

****************** done ******************


```

---

### Post by varunendra on 2014-03-08
Hmm.. the Ethernet seems to be activated now (link=yes), while no improvement with wireless.

For Ethernet, it should be connected now. Please confirm -
Does your router have DHCP enabled?
Is the Ethernet unable to get IP from DHCP?
If you are not sure, or if the DHCP is not working as expected, have you tried manually saving a valid IP,Gateway,DNS in Network Manager?

We can try a temporary IP to see if you are able to connect via cable now -
```
sudo ifconfig eth0 down
sudo ifconfig eth0 *192.168.1.100*
```
..where the IP 192.168.1.100 is just an example. Change it with a valid and available IP address on you network.
Can you ping your router after this? (for example, "ping 192.168.1.1" assuming your router's IP is 192.168.1.1)

As for the wireless, the "denied association" messages are still there. We can try a few other things, but these messages are making me skeptical of your router settings.

You didn't confirm my previous questions -
Did you check the BIOS?
Did you make sure no custom features are enabled in the router? Or if there are some, please post here what they are.

---

### Post by mike156 on 2014-03-09
Reinstalled Ubuntu, factory resseted the router, made same configuration and magically works :| thanks for help

---

### Post by varunendra on 2014-03-09
Keep it on test bed for a while, and if remains stable and fast, please mark the thread as [SOLVED] using "Thread Tools" link above the top post.

If the problem returns, let me know and we

---

