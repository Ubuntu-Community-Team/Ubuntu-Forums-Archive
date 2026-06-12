---
title: "Wireless networking works for one network, but not another"
date: 2014-06-14
forum: Networking &amp; Wireless
---

### Post by jdix123 on 2014-06-14
I have a small office setup with Windows 8.1, Apple, and Linux PCs (Edubuntu 14.04), iOS devices, and Android devices.  Up until this week we'd been connecting through a MiFi wireless hotspot, which worked fine.  We just installed a new service provider, and the Apple and Windows PCs, iOS and Android devices connect fine to the new network.  Linux PCs see the network but are unable to connect.  I have no idea what is happening.

I ran the wireless diagnostic script suggested on the forum sticky on ONE of the Linux laptops we have, it looks like this:

```

########## wireless info START ##########

##### release #####

Distributor ID:	Ubuntu
Description:	Ubuntu 14.04 LTS
Release:	14.04
Codename:	trusty

##### kernel #####

Linux jas-ThinkPad-Edge-E440 3.13.0-27-generic #50-Ubuntu SMP Thu May 15 18:06:16 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux

##### lspci #####

03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 10)
	Subsystem: Lenovo Device [17aa:5028]
	Kernel driver in use: r8169
04:00.0 Network controller [0280]: Intel Corporation Wireless 7260 [8086:08b2] (rev 73)
	Subsystem: Intel Corporation Wireless-N 7260 [8086:4262]
	Kernel driver in use: iwlwifi

##### lsusb #####

Bus 002 Device 002: ID 8087:8000 Intel Corp. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:8008 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 003: ID 8087:07dc Intel Corp. 
Bus 003 Device 002: ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 003 Device 005: ID 04f2:b398 Chicony Electronics Co., Ltd 
Bus 003 Device 004: ID 138a:0011 Validity Sensors, Inc. VFS5011 Fingerprint Reader
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA Card Info #####

##### rfkill #####

0: tpacpi_bluetooth_sw: Bluetooth
	Soft blocked: no
	Hard blocked: no
2: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
10: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no

##### iw reg get #####

country US:
	(2402 - 2472 @ 40), (3, 27)
	(5170 - 5250 @ 40), (3, 17)
	(5250 - 5330 @ 40), (3, 20), DFS
	(5490 - 5600 @ 40), (3, 20), DFS
	(5650 - 5710 @ 40), (3, 20), DFS
	(5735 - 5835 @ 40), (3, 30)
	(57240 - 63720 @ 2160), (N/A, 40)

##### interfaces #####

# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback

##### iwconfig #####

wlan0     IEEE 802.11bgn  ESSID:"UNITE-8D9B"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: <MAC address removed>   
          Bit Rate=72.2 Mb/s   Tx-Power=16 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=41/70  Signal level=-69 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:97   Missed beacon:0

##### route #####

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 wlan0
192.168.1.0     0.0.0.0         255.255.255.0   U     9      0        0 wlan0

##### resolv.conf #####

nameserver 127.0.1.1
search lan

##### nm-tool #####

NetworkManager Tool

State: connected (global)

- Device: wlan0  [UNITE-8D9B] --------------------------------------------------
  Type:              802.11 WiFi
  Driver:            iwlwifi
  State:             connected
  Default:           yes
  HW Address:        <MAC address removed>

  Capabilities:
    Speed:           72 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    Peter Lecca DDS: Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 65 WPA2
    Peter Lecca Guest: Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 65 WPA2
    DDW3654F:        Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 100 WPA2
    *UNITE-8D9B:     Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 54 WPA2

  IPv4 Settings:
    Address:         192.168.1.81
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1

    DNS:             192.168.1.1

- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             unavailable
  Default:           no
  HW Address:        <MAC address removed>

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off

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

##### iwlist #####

wlan0     Scan completed :
          Cell 01 - Address: <MAC address removed>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=42/70  Signal level=-68 dBm  
                    Encryption key:on
                    ESSID:"UNITE-8D9B"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000002c54634c6c
                    Extra: Last beacon: 80ms ago
                    IE: Unknown: 000A554E4954452D38443942
                    IE: Unknown: 010882848B0C12961824
                    IE: Unknown: 03010B
                    IE: Unknown: 0706555320010B1B
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: 2D1A2C4001FF00000000000000000000000000000000000000000000
                    IE: Unknown: 3D160B000000000000000000000000000000000000000000
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: DD730050F204104A00011010440001021057000101103B0001031047001058950A5B82A55999AA377806D6D6028E102100085155414C434F4D4D10230006415236303078102400012010420001201054000800060050F2040001101100074152364B2D415010080002238E1049000600372A000120
          Cell 02 - Address: <MAC address removed>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=51/70  Signal level=-59 dBm  
                    Encryption key:on
                    ESSID:"Peter Lecca Guest"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000002c3e08a9cb1
                    Extra: Last beacon: 80ms ago
                    IE: Unknown: 00115065746572204C65636361204775657374
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030106
                    IE: Unknown: 0706555320010B1E
                    IE: Unknown: 200100
                    IE: Unknown: 23021900
                    IE: Unknown: 2A0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1AAD1917FFFFFF0000000000000000000000000000000000000000
                    IE: Unknown: 3D1606081500000000000000000000000000000000000000
                    IE: Unknown: 7F080000000000000040
                    IE: Unknown: DD0700039301780208
                    IE: Unknown: DD0E0017F2070001010680EA96F063FD
                    IE: Unknown: DD090010180201001C0000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: 46050200010000
          Cell 03 - Address: <MAC address removed>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=52/70  Signal level=-58 dBm  
                    Encryption key:on
                    ESSID:"Peter Lecca DDS"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000002c3e089fb3e
                    Extra: Last beacon: 80ms ago
                    IE: Unknown: 000F5065746572204C6563636120444453
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030106
                    IE: Unknown: 0706555320010B1E
                    IE: Unknown: 200100
                    IE: Unknown: 23021900
                    IE: Unknown: 2A0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1AAD1917FFFFFF0000000000000000000000000000000000000000
                    IE: Unknown: 3D1606081500000000000000000000000000000000000000
                    IE: Unknown: 7F080000000000000040
                    IE: Unknown: DD0B0017F20100010100000007
                    IE: Unknown: DD0700039301780320
                    IE: Unknown: DD0E0017F2070001010680EA96F063FD
                    IE: Unknown: DD090010180201001C0000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: 46050200010000
          Cell 04 - Address: <MAC address removed>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=69/70  Signal level=-41 dBm  
                    Encryption key:on
                    ESSID:"DDW3654F"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000001c99faf1d4
                    Extra: Last beacon: 80ms ago
                    IE: Unknown: 00084444573336353446
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0104
                    IE: Unknown: 2F0104
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1ABD1817FFFFFF0000000000000000000000000000000000000000
                    IE: Unknown: 3D160B080400000000000000000000000000000000000000
                    IE: Unknown: DD770050F204104A0001101044000102103B000103104700105F746AA3CFCE488F2B25503967027635102100045562656510230004556265651024000631323334353610420007303030303030311054000800060050F204000110110006556265654150100800022008103C0001011049000600372A000120
                    IE: Unknown: DD090010180203001C0000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00

##### iwlist channel #####

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
          Current Frequency:2.462 GHz (Channel 11)

##### lsmod #####

iwlmvm                189774  0 
mac80211              626511  1 iwlmvm
iwlwifi               169932  1 iwlmvm
cfg80211              484040  3 iwlwifi,mac80211,iwlmvm

##### modinfo #####

filename:       /lib/modules/3.13.0-27-generic/kernel/drivers/net/wireless/iwlwifi/mvm/iwlmvm.ko
license:        GPL
author:         Copyright(c) 2003-2013 Intel Corporation <ilw@linux.intel.com>
version:        in-tree:
description:    The new Intel(R) wireless AGN driver for Linux
srcversion:     964B69F7EBC572BE39F5C50
depends:        iwlwifi,mac80211,cfg80211
intree:         Y
vermagic:       3.13.0-27-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        <MAC address removed>:43:25:CC:F7:B9:5B:51:F6:C1:19:38:0E:B9:33
sig_hashalgo:   sha512
parm:           init_dbg:set to true to debug an ASSERT in INIT fw (default: false (bool)
parm:           power_scheme:power management scheme: 1-active, 2-balanced, 3-low power, default: 2 (int)

filename:       /lib/modules/3.13.0-27-generic/kernel/drivers/net/wireless/iwlwifi/iwlwifi.ko
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
firmware:       iwlwifi-3160-7.ucode
firmware:       iwlwifi-7260-7.ucode
srcversion:     1E6912E109D5A43B310FB34
alias:          pci:v00008086d0000095Asv*sd00005490bc*sc*i*
alias:          pci:v00008086d0000095Bsv*sd00005290bc*sc*i*
alias:          pci:v00008086d0000095Asv*sd00005590bc*sc*i*
alias:          pci:v00008086d0000095Asv*sd00005190bc*sc*i*
alias:          pci:v00008086d0000095Asv*sd00005090bc*sc*i*
alias:          pci:v00008086d0000095Asv*sd00005420bc*sc*i*
alias:          pci:v00008086d0000095Asv*sd0000502Abc*sc*i*
alias:          pci:v00008086d0000095Asv*sd00005020bc*sc*i*
alias:          pci:v00008086d0000095Asv*sd00009410bc*sc*i*
alias:          pci:v00008086d0000095Asv*sd00009310bc*sc*i*
alias:          pci:v00008086d0000095Asv*sd00009510bc*sc*i*
alias:          pci:v00008086d0000095Asv*sd00009210bc*sc*i*
alias:          pci:v00008086d0000095Asv*sd00009112bc*sc*i*
alias:          pci:v00008086d0000095Asv*sd00009110bc*sc*i*
alias:          pci:v00008086d0000095Asv*sd00009012bc*sc*i*
alias:          pci:v00008086d0000095Asv*sd00009010bc*sc*i*
alias:          pci:v00008086d0000095Bsv*sd00005202bc*sc*i*
alias:          pci:v00008086d0000095Asv*sd00005002bc*sc*i*
alias:          pci:v00008086d0000095Bsv*sd00005200bc*sc*i*
alias:          pci:v00008086d0000095Asv*sd0000500Abc*sc*i*
alias:          pci:v00008086d0000095Asv*sd00005000bc*sc*i*
alias:          pci:v00008086d0000095Asv*sd00001010bc*sc*i*
alias:          pci:v00008086d0000095Asv*sd00005400bc*sc*i*
alias:          pci:v00008086d0000095Asv*sd00005410bc*sc*i*
alias:          pci:v00008086d0000095Asv*sd00005012bc*sc*i*
alias:          pci:v00008086d0000095Bsv*sd00005210bc*sc*i*
alias:          pci:v00008086d0000095Bsv*sd00005302bc*sc*i*
alias:          pci:v00008086d0000095Bsv*sd00005310bc*sc*i*
alias:          pci:v00008086d0000095Asv*sd0000510Abc*sc*i*
alias:          pci:v00008086d0000095Asv*sd00005100bc*sc*i*
alias:          pci:v00008086d0000095Asv*sd00005112bc*sc*i*
alias:          pci:v00008086d0000095Asv*sd00005110bc*sc*i*
alias:          pci:v00008086d0000095Asv*sd00005010bc*sc*i*
alias:          pci:v00008086d000008B3sv*sd00008570bc*sc*i*
alias:          pci:v00008086d000008B3sv*sd00008470bc*sc*i*
alias:          pci:v00008086d000008B4sv*sd00008270bc*sc*i*
alias:          pci:v00008086d000008B3sv*sd00008062bc*sc*i*
alias:          pci:v00008086d000008B3sv*sd00008060bc*sc*i*
alias:          pci:v00008086d000008B3sv*sd00008172bc*sc*i*
alias:          pci:v00008086d000008B3sv*sd00008170bc*sc*i*
alias:          pci:v00008086d000008B3sv*sd00008072bc*sc*i*
alias:          pci:v00008086d000008B3sv*sd00008070bc*sc*i*
alias:          pci:v00008086d000008B4sv*sd00000370bc*sc*i*
alias:          pci:v00008086d000008B3sv*sd00000472bc*sc*i*
alias:          pci:v00008086d000008B3sv*sd00000470bc*sc*i*
alias:          pci:v00008086d000008B4sv*sd00000272bc*sc*i*
alias:          pci:v00008086d000008B4sv*sd00000270bc*sc*i*
alias:          pci:v00008086d000008B3sv*sd00000062bc*sc*i*
alias:          pci:v00008086d000008B3sv*sd00000060bc*sc*i*
alias:          pci:v00008086d000008B3sv*sd00000172bc*sc*i*
alias:          pci:v00008086d000008B3sv*sd00000170bc*sc*i*
alias:          pci:v00008086d000008B3sv*sd00000072bc*sc*i*
alias:          pci:v00008086d000008B3sv*sd00000070bc*sc*i*
alias:          pci:v00008086d000008B1sv*sd0000C420bc*sc*i*
alias:          pci:v00008086d000008B2sv*sd0000C220bc*sc*i*
alias:          pci:v00008086d000008B1sv*sd0000C02Abc*sc*i*
alias:          pci:v00008086d000008B1sv*sd0000C020bc*sc*i*
alias:          pci:v00008086d000008B1sv*sd0000C360bc*sc*i*
alias:          pci:v00008086d000008B2sv*sd0000C370bc*sc*i*
alias:          pci:v00008086d000008B1sv*sd0000C560bc*sc*i*
alias:          pci:v00008086d000008B1sv*sd0000C570bc*sc*i*
alias:          pci:v00008086d000008B1sv*sd0000C462bc*sc*i*
alias:          pci:v00008086d000008B1sv*sd0000C460bc*sc*i*
alias:          pci:v00008086d000008B1sv*sd0000C472bc*sc*i*
alias:          pci:v00008086d000008B1sv*sd0000C470bc*sc*i*
alias:          pci:v00008086d000008B2sv*sd0000C262bc*sc*i*
alias:          pci:v00008086d000008B2sv*sd0000C26Abc*sc*i*
alias:          pci:v00008086d000008B2sv*sd0000C260bc*sc*i*
alias:          pci:v00008086d000008B2sv*sd0000C272bc*sc*i*
alias:          pci:v00008086d000008B2sv*sd0000C270bc*sc*i*
alias:          pci:v00008086d000008B1sv*sd0000C760bc*sc*i*
alias:          pci:v00008086d000008B1sv*sd0000C770bc*sc*i*
alias:          pci:v00008086d000008B1sv*sd0000C162bc*sc*i*
alias:          pci:v00008086d000008B1sv*sd0000C062bc*sc*i*
alias:          pci:v00008086d000008B1sv*sd0000C160bc*sc*i*
alias:          pci:v00008086d000008B1sv*sd0000C06Abc*sc*i*
alias:          pci:v00008086d000008B1sv*sd0000C060bc*sc*i*
alias:          pci:v00008086d000008B1sv*sd0000C170bc*sc*i*
alias:          pci:v00008086d000008B1sv*sd0000C072bc*sc*i*
alias:          pci:v00008086d000008B1sv*sd0000C070bc*sc*i*
alias:          pci:v00008086d000008B1sv*sd00004420bc*sc*i*
alias:          pci:v00008086d000008B2sv*sd00004220bc*sc*i*
alias:          pci:v00008086d000008B1sv*sd0000402Abc*sc*i*
alias:          pci:v00008086d000008B1sv*sd00004020bc*sc*i*
alias:          pci:v00008086d000008B1sv*sd00005070bc*sc*i*
alias:          pci:v00008086d000008B2sv*sd00004360bc*sc*i*
alias:          pci:v00008086d000008B2sv*sd00004370bc*sc*i*
alias:          pci:v00008086d000008B1sv*sd00004560bc*sc*i*
alias:          pci:v00008086d000008B1sv*sd00004570bc*sc*i*
alias:          pci:v00008086d000008B1sv*sd00004A6Cbc*sc*i*
alias:          pci:v00008086d000008B1sv*sd00004A6Ebc*sc*i*
alias:          pci:v00008086d000008B1sv*sd00004A70bc*sc*i*
alias:          pci:v00008086d000008B1sv*sd0000486Ebc*sc*i*
alias:          pci:v00008086d000008B1sv*sd00004870bc*sc*i*
alias:          pci:v00008086d000008B1sv*sd00004462bc*sc*i*
alias:          pci:v00008086d000008B1sv*sd0000446Abc*sc*i*
alias:          pci:v00008086d000008B1sv*sd00004460bc*sc*i*
alias:          pci:v00008086d000008B1sv*sd00004472bc*sc*i*
alias:          pci:v00008086d000008B1sv*sd00004470bc*sc*i*
alias:          pci:v00008086d000008B2sv*sd00004262bc*sc*i*
alias:          pci:v00008086d000008B2sv*sd0000426Abc*sc*i*
alias:          pci:v00008086d000008B2sv*sd00004260bc*sc*i*
alias:          pci:v00008086d000008B2sv*sd00004272bc*sc*i*
alias:          pci:v00008086d000008B2sv*sd00004270bc*sc*i*
alias:          pci:v00008086d000008B1sv*sd00004162bc*sc*i*
alias:          pci:v00008086d000008B1sv*sd00004062bc*sc*i*
alias:          pci:v00008086d000008B1sv*sd00004160bc*sc*i*
alias:          pci:v00008086d000008B1sv*sd0000406Abc*sc*i*
alias:          pci:v00008086d000008B1sv*sd00004060bc*sc*i*
alias:          pci:v00008086d000008B1sv*sd00004170bc*sc*i*
alias:          pci:v00008086d000008B1sv*sd00004072bc*sc*i*
alias:          pci:v00008086d000008B1sv*sd00004070bc*sc*i*
alias:          pci:v00008086d00000892sv*sd00000462bc*sc*i*
alias:          pci:v00008086d00000893sv*sd00000262bc*sc*i*
alias:          pci:v00008086d00000892sv*sd00000062bc*sc*i*
alias:          pci:v00008086d00000894sv*sd00000822bc*sc*i*
alias:          pci:v00008086d00000894sv*sd00000422bc*sc*i*
alias:          pci:v00008086d00000895sv*sd00000222bc*sc*i*
alias:          pci:v00008086d00000894sv*sd00000022bc*sc*i*
alias:          pci:v00008086d0000088Fsv*sd00005260bc*sc*i*
alias:          pci:v00008086d0000088Esv*sd00004860bc*sc*i*
alias:          pci:v00008086d0000088Esv*sd0000446Abc*sc*i*
alias:          pci:v00008086d0000088Esv*sd00004460bc*sc*i*
alias:          pci:v00008086d0000088Fsv*sd0000426Abc*sc*i*
alias:          pci:v00008086d0000088Fsv*sd00004260bc*sc*i*
alias:          pci:v00008086d0000088Esv*sd0000406Abc*sc*i*
alias:          pci:v00008086d0000088Esv*sd00004060bc*sc*i*
alias:          pci:v00008086d00000887sv*sd00004462bc*sc*i*
alias:          pci:v00008086d00000888sv*sd00004262bc*sc*i*
alias:          pci:v00008086d00000887sv*sd00004062bc*sc*i*
alias:          pci:v00008086d00000890sv*sd00004822bc*sc*i*
alias:          pci:v00008086d00000890sv*sd00004422bc*sc*i*
alias:          pci:v00008086d00000891sv*sd00004222bc*sc*i*
alias:          pci:v00008086d00000890sv*sd00004022bc*sc*i*
alias:          pci:v00008086d00000896sv*sd00005027bc*sc*i*
alias:          pci:v00008086d00000896sv*sd00005025bc*sc*i*
alias:          pci:v00008086d00000897sv*sd00005017bc*sc*i*
alias:          pci:v00008086d00000897sv*sd00005015bc*sc*i*
alias:          pci:v00008086d00000896sv*sd00005007bc*sc*i*
alias:          pci:v00008086d00000896sv*sd00005005bc*sc*i*
alias:          pci:v00008086d000008AEsv*sd00001027bc*sc*i*
alias:          pci:v00008086d000008AEsv*sd00001025bc*sc*i*
alias:          pci:v00008086d000008AFsv*sd00001017bc*sc*i*
alias:          pci:v00008086d000008AFsv*sd00001015bc*sc*i*
alias:          pci:v00008086d000008AEsv*sd00001007bc*sc*i*
alias:          pci:v00008086d000008AEsv*sd00001005bc*sc*i*
alias:          pci:v00008086d00000084sv*sd00001316bc*sc*i*
alias:          pci:v00008086d00000084sv*sd00001216bc*sc*i*
alias:          pci:v00008086d00000083sv*sd00001326bc*sc*i*
alias:          pci:v00008086d00000083sv*sd00001226bc*sc*i*
alias:          pci:v00008086d00000083sv*sd00001306bc*sc*i*
alias:          pci:v00008086d00000083sv*sd00001206bc*sc*i*
alias:          pci:v00008086d00000084sv*sd00001315bc*sc*i*
alias:          pci:v00008086d00000084sv*sd00001215bc*sc*i*
alias:          pci:v00008086d00000083sv*sd00001325bc*sc*i*
alias:          pci:v00008086d00000083sv*sd00001225bc*sc*i*
alias:          pci:v00008086d00000083sv*sd00001305bc*sc*i*
alias:          pci:v00008086d00000083sv*sd00001205bc*sc*i*
alias:          pci:v00008086d00000886sv*sd00001317bc*sc*i*
alias:          pci:v00008086d00000886sv*sd00001315bc*sc*i*
alias:          pci:v00008086d00000885sv*sd00001327bc*sc*i*
alias:          pci:v00008086d00000885sv*sd00001325bc*sc*i*
alias:          pci:v00008086d00000885sv*sd00001307bc*sc*i*
alias:          pci:v00008086d00000885sv*sd00001305bc*sc*i*
alias:          pci:v00008086d00000089sv*sd00001316bc*sc*i*
alias:          pci:v00008086d00000089sv*sd00001311bc*sc*i*
alias:          pci:v00008086d00000087sv*sd00001326bc*sc*i*
alias:          pci:v00008086d00000087sv*sd00001321bc*sc*i*
alias:          pci:v00008086d00000087sv*sd00001306bc*sc*i*
alias:          pci:v00008086d00000087sv*sd00001301bc*sc*i*
alias:          pci:v00008086d00000091sv*sd00005226bc*sc*i*
alias:          pci:v00008086d00000091sv*sd00005225bc*sc*i*
alias:          pci:v00008086d00000091sv*sd00005221bc*sc*i*
alias:          pci:v00008086d00000091sv*sd00005207bc*sc*i*
alias:          pci:v00008086d00000091sv*sd00005206bc*sc*i*
alias:          pci:v00008086d00000091sv*sd00005205bc*sc*i*
alias:          pci:v00008086d00000091sv*sd00005201bc*sc*i*
alias:          pci:v00008086d00000090sv*sd00005216bc*sc*i*
alias:          pci:v00008086d00000090sv*sd00005215bc*sc*i*
alias:          pci:v00008086d00000090sv*sd00005211bc*sc*i*
alias:          pci:v00008086d0000008Bsv*sd00005317bc*sc*i*
alias:          pci:v00008086d0000008Bsv*sd00005315bc*sc*i*
alias:          pci:v00008086d0000008Asv*sd00005327bc*sc*i*
alias:          pci:v00008086d0000008Asv*sd00005325bc*sc*i*
alias:          pci:v00008086d0000008Asv*sd00005307bc*sc*i*
alias:          pci:v00008086d0000008Asv*sd00005305bc*sc*i*
alias:          pci:v00008086d00000082sv*sd00001305bc*sc*i*
alias:          pci:v00008086d00000082sv*sd00001304bc*sc*i*
alias:          pci:v00008086d00000082sv*sd00004820bc*sc*i*
alias:          pci:v00008086d00000085sv*sd0000C228bc*sc*i*
alias:          pci:v00008086d00000085sv*sd0000C220bc*sc*i*
alias:          pci:v00008086d00000082sv*sd0000C020bc*sc*i*
alias:          pci:v00008086d00000085sv*sd00001316bc*sc*i*
alias:          pci:v00008086d00000085sv*sd00001318bc*sc*i*
alias:          pci:v00008086d00000085sv*sd00001311bc*sc*i*
alias:          pci:v00008086d00000082sv*sd00001328bc*sc*i*
alias:          pci:v00008086d00000082sv*sd00001326bc*sc*i*
alias:          pci:v00008086d00000082sv*sd00001321bc*sc*i*
alias:          pci:v00008086d00000082sv*sd00001308bc*sc*i*
alias:          pci:v00008086d00000082sv*sd00001307bc*sc*i*
alias:          pci:v00008086d00000082sv*sd00001306bc*sc*i*
alias:          pci:v00008086d00000082sv*sd00001301bc*sc*i*
alias:          pci:v00008086d00004239sv*sd00001316bc*sc*i*
alias:          pci:v00008086d00004239sv*sd00001311bc*sc*i*
alias:          pci:v00008086d00004238sv*sd00001118bc*sc*i*
alias:          pci:v00008086d00004238sv*sd00001111bc*sc*i*
alias:          pci:v00008086d0000422Csv*sd00001326bc*sc*i*
alias:          pci:v00008086d0000422Csv*sd00001321bc*sc*i*
alias:          pci:v00008086d0000422Csv*sd00001307bc*sc*i*
alias:          pci:v00008086d0000422Csv*sd00001306bc*sc*i*
alias:          pci:v00008086d0000422Csv*sd00001301bc*sc*i*
alias:          pci:v00008086d0000422Bsv*sd00001128bc*sc*i*
alias:          pci:v00008086d0000422Bsv*sd00001121bc*sc*i*
alias:          pci:v00008086d0000422Bsv*sd00001108bc*sc*i*
alias:          pci:v00008086d0000422Bsv*sd00001101bc*sc*i*
alias:          pci:v00008086d0000423Dsv*sd00001316bc*sc*i*
alias:          pci:v00008086d0000423Dsv*sd00001216bc*sc*i*
alias:          pci:v00008086d0000423Dsv*sd00001311bc*sc*i*
alias:          pci:v00008086d0000423Dsv*sd00001211bc*sc*i*
alias:          pci:v00008086d0000423Csv*sd00001326bc*sc*i*
alias:          pci:v00008086d0000423Csv*sd00001321bc*sc*i*
alias:          pci:v00008086d0000423Csv*sd00001221bc*sc*i*
alias:          pci:v00008086d0000423Csv*sd00001306bc*sc*i*
alias:          pci:v00008086d0000423Csv*sd00001206bc*sc*i*
alias:          pci:v00008086d0000423Csv*sd00001301bc*sc*i*
alias:          pci:v00008086d0000423Csv*sd00001201bc*sc*i*
alias:          pci:v00008086d0000423Bsv*sd00001011bc*sc*i*
alias:          pci:v00008086d0000423Asv*sd00001021bc*sc*i*
alias:          pci:v00008086d0000423Asv*sd00001001bc*sc*i*
alias:          pci:v00008086d00004236sv*sd00001114bc*sc*i*
alias:          pci:v00008086d00004236sv*sd00001014bc*sc*i*
alias:          pci:v00008086d00004236sv*sd00001111bc*sc*i*
alias:          pci:v00008086d00004236sv*sd00001011bc*sc*i*
alias:          pci:v00008086d00004235sv*sd00001104bc*sc*i*
alias:          pci:v00008086d00004235sv*sd00001004bc*sc*i*
alias:          pci:v00008086d00004235sv*sd00001101bc*sc*i*
alias:          pci:v00008086d00004235sv*sd00001001bc*sc*i*
alias:          pci:v00008086d00004235sv*sd00001124bc*sc*i*
alias:          pci:v00008086d00004235sv*sd00001024bc*sc*i*
alias:          pci:v00008086d00004235sv*sd00001121bc*sc*i*
alias:          pci:v00008086d00004235sv*sd00001021bc*sc*i*
alias:          pci:v00008086d00004237sv*sd00001316bc*sc*i*
alias:          pci:v00008086d00004237sv*sd00001216bc*sc*i*
alias:          pci:v00008086d00004237sv*sd00001315bc*sc*i*
alias:          pci:v00008086d00004237sv*sd00001215bc*sc*i*
alias:          pci:v00008086d00004237sv*sd00001314bc*sc*i*
alias:          pci:v00008086d00004237sv*sd00001214bc*sc*i*
alias:          pci:v00008086d00004237sv*sd00001311bc*sc*i*
alias:          pci:v00008086d00004237sv*sd00001211bc*sc*i*
alias:          pci:v00008086d00004232sv*sd00001326bc*sc*i*
alias:          pci:v00008086d00004232sv*sd00001226bc*sc*i*
alias:          pci:v00008086d00004232sv*sd00001325bc*sc*i*
alias:          pci:v00008086d00004232sv*sd00001225bc*sc*i*
alias:          pci:v00008086d00004232sv*sd00001324bc*sc*i*
alias:          pci:v00008086d00004232sv*sd00001224bc*sc*i*
alias:          pci:v00008086d00004232sv*sd00001321bc*sc*i*
alias:          pci:v00008086d00004232sv*sd00001221bc*sc*i*
alias:          pci:v00008086d00004232sv*sd00001306bc*sc*i*
alias:          pci:v00008086d00004232sv*sd00001206bc*sc*i*
alias:          pci:v00008086d00004232sv*sd00001305bc*sc*i*
alias:          pci:v00008086d00004232sv*sd00001205bc*sc*i*
alias:          pci:v00008086d00004232sv*sd00001304bc*sc*i*
alias:          pci:v00008086d00004232sv*sd00001204bc*sc*i*
alias:          pci:v00008086d00004232sv*sd00001301bc*sc*i*
alias:          pci:v00008086d00004232sv*sd00001201bc*sc*i*
depends:        cfg80211
intree:         Y
vermagic:       3.13.0-27-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        <MAC address removed>:43:25:CC:F7:B9:5B:51:F6:C1:19:38:0E:B9:33
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

##### modules #####

lp
rtc

##### blacklist #####

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

[/etc/modprobe.d/fbdev-blacklist.conf]
blacklist arkfb
blacklist aty128fb
blacklist atyfb
blacklist radeonfb
blacklist cirrusfb
blacklist cyber2000fb
blacklist gx1fb
blacklist gxfb
blacklist kyrofb
blacklist matroxfb_base
blacklist mb862xxfb
blacklist neofb
blacklist nvidiafb
blacklist pm2fb
blacklist pm3fb
blacklist s3fb
blacklist savagefb
blacklist sisfb
blacklist tdfxfb
blacklist tridentfb
blacklist viafb
blacklist vt8623fb

##### udev rules #####

# PCI device 0x10ec:0x8168 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

# PCI device 0x8086:0x08b2 (iwlwifi)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

##### dmesg #####

[    7.665750] psmouse serio2: trackpoint: IBM TrackPoint firmware: 0x0e, buttons: 3/3
[   12.382930] iwlwifi 0000:04:00.0: irq 44 for MSI/MSI-X
[   12.628939] iwlwifi 0000:04:00.0: Direct firmware load failed with error -2
[   12.628940] iwlwifi 0000:04:00.0: Falling back to user helper
[   12.696263] Bluetooth: hci0: Intel Bluetooth firmware file: intel/ibt-hw-37.7.10-fw-1.80.2.3.d.bseq
[   12.795288] Bluetooth: hci0: Intel Bluetooth firmware patch completed and activated
[   12.872767] iwlwifi 0000:04:00.0: loaded firmware version 22.1.7.0 op_mode iwlmvm
[   12.882936] iwlwifi 0000:04:00.0: Detected Intel(R) Wireless N 7260, REV=0x144
[   12.883004] iwlwifi 0000:04:00.0: L1 Enabled; Disabling L0S
[   12.883247] iwlwifi 0000:04:00.0: L1 Enabled; Disabling L0S
[   13.086114] ieee80211 phy0: Selected rate control algorithm 'iwl-mvm-rs'
[   17.246209] iwlwifi 0000:04:00.0: L1 Enabled; Disabling L0S
[   17.246464] iwlwifi 0000:04:00.0: L1 Enabled; Disabling L0S
[   17.258023] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   17.258263] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   18.039959] wlan0: authenticate with <MAC address removed>
[   18.040831] wlan0: send auth to <MAC address removed> (try 1/3)
[   18.045054] wlan0: authenticated
[   18.046761] wlan0: associate with <MAC address removed> (try 1/3)
[   18.050015] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=5)
[   18.050740] wlan0: associated
[   18.050762] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 3351.705737] wlan0: authenticate with <MAC address removed>
[ 3351.706837] wlan0: send auth to <MAC address removed> (try 1/3)
[ 3351.756622] wlan0: send auth to <MAC address removed> (try 2/3)
[ 3351.824197] wlan0: send auth to <MAC address removed> (try 3/3)
[ 3351.894535] wlan0: authentication with <MAC address removed> timed out
[ 3366.700179] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 3427.192407] wlan0: authenticate with <MAC address removed>
[ 3427.193273] wlan0: send auth to <MAC address removed> (try 1/3)
[ 3427.195534] wlan0: authenticated
[ 3427.195739] wlan0: associate with <MAC address removed> (try 1/3)
[ 3427.198933] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=6)
[ 3427.199377] wlan0: associated
[ 3427.199384] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 4726.433915] wlan0: authenticate with <MAC address removed>
[ 4726.434923] wlan0: send auth to <MAC address removed> (try 1/3)
[ 4726.742543] iwlwifi 0000:04:00.0: No association and the time event is over already...
[ 4726.742607] wlan0: Connection to AP <MAC address removed> lost
[ 4727.566662] wlan0: send auth to <MAC address removed> (try 2/3)
[ 4727.681362] wlan0: send auth to <MAC address removed> (try 3/3)
[ 4727.760704] wlan0: authentication with <MAC address removed> timed out
[ 4729.017068] wlan0: authenticate with <MAC address removed>
[ 4729.018073] wlan0: send auth to <MAC address removed> (try 1/3)
[ 4729.129285] wlan0: send auth to <MAC address removed> (try 2/3)
[ 4729.247800] wlan0: send auth to <MAC address removed> (try 3/3)
[ 4729.375118] wlan0: authentication with <MAC address removed> timed out
[ 4731.135512] wlan0: authenticate with <MAC address removed>
[ 4731.136523] wlan0: send auth to <MAC address removed> (try 1/3)
[ 4731.248957] wlan0: send auth to <MAC address removed> (try 2/3)
[ 4731.334386] wlan0: authenticated
[ 4731.337937] wlan0: associate with <MAC address removed> (try 1/3)
[ 4731.547113] wlan0: associate with <MAC address removed> (try 2/3)
[ 4731.700560] wlan0: associate with <MAC address removed> (try 3/3)
[ 4731.772018] wlan0: association with <MAC address removed> timed out
[ 4741.056749] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 4743.833168] wlan0: authenticate with <MAC address removed>
[ 4743.833969] wlan0: send auth to <MAC address removed> (try 1/3)
[ 4743.890077] wlan0: send auth to <MAC address removed> (try 2/3)
[ 4743.950824] wlan0: send auth to <MAC address removed> (try 3/3)
[ 4744.010812] wlan0: authentication with <MAC address removed> timed out
[ 4756.720688] iwlwifi 0000:04:00.0: L1 Enabled; Disabling L0S
[ 4756.721001] iwlwifi 0000:04:00.0: L1 Enabled; Disabling L0S
[ 4756.734193] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 4758.176444] wlan0: authenticate with <MAC address removed>
[ 4758.177421] wlan0: send auth to <MAC address removed> (try 1/3)
[ 4758.179256] wlan0: <MAC address removed> denied authentication (status 17)
[ 4758.194323] wlan0: authenticate with <MAC address removed>
[ 4758.195170] wlan0: send auth to <MAC address removed> (try 1/3)
[ 4758.196950] wlan0: <MAC address removed> denied authentication (status 17)
[ 4759.463873] wlan0: authenticate with <MAC address removed>
[ 4759.464927] wlan0: send auth to <MAC address removed> (try 1/3)
[ 4759.466791] wlan0: <MAC address removed> denied authentication (status 17)
[ 4761.229698] wlan0: authenticate with <MAC address removed>
[ 4761.230600] wlan0: send auth to <MAC address removed> (try 1/3)
[ 4761.232382] wlan0: <MAC address removed> denied authentication (status 17)
[ 4772.757562] wlan0: authenticate with <MAC address removed>
[ 4772.758484] wlan0: send auth to <MAC address removed> (try 1/3)
[ 4772.760361] wlan0: <MAC address removed> denied authentication (status 17)
[ 4785.871776] wlan0: authenticate with <MAC address removed>
[ 4785.872615] wlan0: send auth to <MAC address removed> (try 1/3)
[ 4785.874320] wlan0: <MAC address removed> denied authentication (status 17)
[ 4796.652884] wlan0: authenticate with <MAC address removed>
[ 4796.653630] wlan0: send auth to <MAC address removed> (try 1/3)
[ 4796.655413] wlan0: <MAC address removed> denied authentication (status 17)
[ 4813.907566] wlan0: authenticate with <MAC address removed>
[ 4813.908526] wlan0: send auth to <MAC address removed> (try 1/3)
[ 4813.912650] wlan0: <MAC address removed> denied authentication (status 17)
[ 4824.695205] wlan0: authenticate with <MAC address removed>
[ 4824.696327] wlan0: send auth to <MAC address removed> (try 1/3)
[ 4824.698230] wlan0: <MAC address removed> denied authentication (status 17)
[ 4867.450866] iwlwifi 0000:04:00.0: L1 Enabled; Disabling L0S
[ 4867.451137] iwlwifi 0000:04:00.0: L1 Enabled; Disabling L0S
[ 4867.464487] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 4870.603695] wlan0: authenticate with <MAC address removed>
[ 4870.604633] wlan0: send auth to <MAC address removed> (try 1/3)
[ 4870.619222] wlan0: <MAC address removed> denied authentication (status 17)
[ 4871.475207] wlan0: authenticate with <MAC address removed>
[ 4871.476523] wlan0: send auth to <MAC address removed> (try 1/3)
[ 4871.478276] wlan0: <MAC address removed> denied authentication (status 17)
[ 4872.740866] wlan0: authenticate with <MAC address removed>
[ 4872.742130] wlan0: send auth to <MAC address removed> (try 1/3)
[ 4872.743896] wlan0: <MAC address removed> denied authentication (status 17)
[ 4874.515413] wlan0: authenticate with <MAC address removed>
[ 4874.516600] wlan0: send auth to <MAC address removed> (try 1/3)
[ 4874.518453] wlan0: <MAC address removed> denied authentication (status 17)
[ 4886.048453] wlan0: authenticate with <MAC address removed>
[ 4886.049244] wlan0: send auth to <MAC address removed> (try 1/3)
[ 4886.051063] wlan0: <MAC address removed> denied authentication (status 17)
[ 4993.063956] wlan0: authenticate with <MAC address removed>
[ 4993.064910] wlan0: send auth to <MAC address removed> (try 1/3)
[ 4993.066795] wlan0: authenticated
[ 4993.067913] wlan0: associate with <MAC address removed> (try 1/3)
[ 4993.071212] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=2)
[ 4993.072210] wlan0: associated
[ 4993.072256] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 9192.910660] wlan0: authenticate with <MAC address removed>
[ 9192.911585] wlan0: send auth to <MAC address removed> (try 1/3)
[ 9192.934667] wlan0: authenticated
[ 9192.937389] wlan0: associate with <MAC address removed> (try 1/3)
[ 9192.985192] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=2)
[ 9192.998693] wlan0: associated
[ 9845.507170] wlan0: authenticate with <MAC address removed>
[ 9845.508191] wlan0: send auth to <MAC address removed> (try 1/3)
[ 9845.625960] wlan0: send auth to <MAC address removed> (try 2/3)
[ 9845.759261] wlan0: send auth to <MAC address removed> (try 3/3)
[ 9845.867095] wlan0: authentication with <MAC address removed> timed out
[ 9847.141492] wlan0: authenticate with <MAC address removed>
[ 9847.142329] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 9847.345010] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 9847.559779] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 9847.760975] wlan0: authentication with <MAC address removed> timed out
[ 9849.528574] wlan0: authenticate with <MAC address removed>
[ 9849.529331] wlan0: send auth to <MAC address removed> (try 1/3)
[ 9849.531085] wlan0: authenticated
[ 9849.534713] wlan0: associate with <MAC address removed> (try 1/3)
[ 9849.537924] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=2)
[ 9849.540546] wlan0: associated
[10393.817051] wlan0: disassociated from <MAC address removed> (Reason: 4)
[10393.843954] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[10393.886235] wlan0: authenticate with <MAC address removed>
[10393.887487] wlan0: send auth to <MAC address removed> (try 1/3)
[10393.894787] wlan0: <MAC address removed> denied authentication (status 17)
[10409.727966] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[14645.439755] iwlwifi 0000:04:00.0: L1 Enabled; Disabling L0S
[14645.440107] iwlwifi 0000:04:00.0: L1 Enabled; Disabling L0S
[14645.453016] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[14646.900216] wlan0: authenticate with <MAC address removed>
[14646.901115] wlan0: send auth to <MAC address removed> (try 1/3)
[14646.903035] wlan0: <MAC address removed> denied authentication (status 17)
[14646.911243] wlan0: authenticate with <MAC address removed>
[14646.912208] wlan0: send auth to <MAC address removed> (try 1/3)
[14646.914046] wlan0: <MAC address removed> denied authentication (status 17)
[14648.172816] wlan0: authenticate with <MAC address removed>
[14648.173911] wlan0: send auth to <MAC address removed> (try 1/3)
[14648.175817] wlan0: <MAC address removed> denied authentication (status 17)
[14649.935024] wlan0: authenticate with <MAC address removed>
[14649.936050] wlan0: send auth to <MAC address removed> (try 1/3)
[14649.938038] wlan0: <MAC address removed> denied authentication (status 17)
[14661.466462] wlan0: authenticate with <MAC address removed>
[14661.467502] wlan0: send auth to <MAC address removed> (try 1/3)
[14661.469378] wlan0: <MAC address removed> denied authentication (status 17)
[14674.773021] wlan0: authenticate with <MAC address removed>
[14674.773843] wlan0: send auth to <MAC address removed> (try 1/3)
[14674.775644] wlan0: <MAC address removed> denied authentication (status 17)
[14685.562191] wlan0: authenticate with <MAC address removed>
[14685.563392] wlan0: send auth to <MAC address removed> (try 1/3)
[14685.565263] wlan0: <MAC address removed> denied authentication (status 17)
[14702.805784] wlan0: authenticate with <MAC address removed>
[14702.806636] wlan0: send auth to <MAC address removed> (try 1/3)
[14702.808429] wlan0: <MAC address removed> denied authentication (status 17)
[14713.592657] wlan0: authenticate with <MAC address removed>
[14713.593893] wlan0: send auth to <MAC address removed> (try 1/3)
[14713.596202] wlan0: <MAC address removed> denied authentication (status 17)
[14737.780021] wlan0: authenticate with <MAC address removed>
[14737.781222] wlan0: send auth to <MAC address removed> (try 1/3)
[14737.783149] wlan0: <MAC address removed> denied authentication (status 17)
[14748.551205] wlan0: authenticate with <MAC address removed>
[14748.552435] wlan0: send auth to <MAC address removed> (try 1/3)
[14748.554274] wlan0: <MAC address removed> denied authentication (status 17)
[14818.581350] wlan0: authenticate with <MAC address removed>
[14818.582554] wlan0: send auth to <MAC address removed> (try 1/3)
[14818.584456] wlan0: <MAC address removed> denied authentication (status 17)
[14829.350462] wlan0: authenticate with <MAC address removed>
[14829.351584] wlan0: send auth to <MAC address removed> (try 1/3)
[14829.365415] wlan0: <MAC address removed> denied authentication (status 17)
[14856.706970] iwlwifi 0000:04:00.0: L1 Enabled; Disabling L0S
[14856.707234] iwlwifi 0000:04:00.0: L1 Enabled; Disabling L0S
[14856.720140] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[14857.474458] wlan0: authenticate with <MAC address removed>
[14857.475352] wlan0: send auth to <MAC address removed> (try 1/3)
[14857.494510] wlan0: <MAC address removed> denied authentication (status 17)
[14858.350118] wlan0: authenticate with <MAC address removed>
[14858.351398] wlan0: send auth to <MAC address removed> (try 1/3)
[14858.353254] wlan0: <MAC address removed> denied authentication (status 17)
[14859.616261] wlan0: authenticate with <MAC address removed>
[14859.617484] wlan0: send auth to <MAC address removed> (try 1/3)
[14859.622074] wlan0: <MAC address removed> denied authentication (status 17)
[14861.378653] wlan0: authenticate with <MAC address removed>
[14861.379713] wlan0: send auth to <MAC address removed> (try 1/3)
[14861.386014] wlan0: <MAC address removed> denied authentication (status 17)
[14872.915598] wlan0: authenticate with <MAC address removed>
[14872.916841] wlan0: send auth to <MAC address removed> (try 1/3)
[14872.918680] wlan0: <MAC address removed> denied authentication (status 17)
[14885.987811] wlan0: authenticate with <MAC address removed>
[14885.988634] wlan0: send auth to <MAC address removed> (try 1/3)
[14885.990375] wlan0: <MAC address removed> denied authentication (status 17)
[14896.772123] wlan0: authenticate with <MAC address removed>
[14896.773439] wlan0: send auth to <MAC address removed> (try 1/3)
[14896.775273] wlan0: <MAC address removed> denied authentication (status 17)
[14914.016392] wlan0: authenticate with <MAC address removed>
[14914.017303] wlan0: send auth to <MAC address removed> (try 1/3)
[14914.030895] wlan0: <MAC address removed> denied authentication (status 17)
[14918.583427] wlan0: authenticate with <MAC address removed>
[14918.584372] wlan0: send auth to <MAC address removed> (try 1/3)
[14918.586111] wlan0: <MAC address removed> denied authentication (status 17)
[14929.360178] wlan0: authenticate with <MAC address removed>
[14929.361421] wlan0: send auth to <MAC address removed> (try 1/3)
[14929.363707] wlan0: <MAC address removed> denied authentication (status 17)
[14947.051198] wlan0: authenticate with <MAC address removed>
[14947.052118] wlan0: send auth to <MAC address removed> (try 1/3)
[14947.056318] wlan0: <MAC address removed> denied authentication (status 17)
[14957.821618] wlan0: authenticate with <MAC address removed>
[14957.822901] wlan0: send auth to <MAC address removed> (try 1/3)
[14957.824763] wlan0: <MAC address removed> denied authentication (status 17)
[15173.199582] wlan0: authenticate with <MAC address removed>
[15173.200586] wlan0: send auth to <MAC address removed> (try 1/3)
[15173.202402] wlan0: <MAC address removed> denied authentication (status 17)
[15183.973416] wlan0: authenticate with <MAC address removed>
[15183.974628] wlan0: send auth to <MAC address removed> (try 1/3)
[15183.978444] wlan0: <MAC address removed> denied authentication (status 17)
[15349.516601] wlan0: authenticate with <MAC address removed>
[15349.517605] wlan0: send auth to <MAC address removed> (try 1/3)
[15349.519469] wlan0: <MAC address removed> denied authentication (status 17)
[15360.290556] wlan0: authenticate with <MAC address removed>
[15360.291625] wlan0: send auth to <MAC address removed> (try 1/3)
[15360.293462] wlan0: <MAC address removed> denied authentication (status 17)
[15383.007716] wlan0: authenticate with <MAC address removed>
[15383.008731] wlan0: send auth to <MAC address removed> (try 1/3)
[15383.011070] wlan0: <MAC address removed> denied authentication (status 17)
[15393.789449] wlan0: authenticate with <MAC address removed>
[15393.790611] wlan0: send auth to <MAC address removed> (try 1/3)
[15393.792569] wlan0: <MAC address removed> denied authentication (status 17)
[15488.234766] iwlwifi 0000:04:00.0: L1 Enabled; Disabling L0S
[15488.235021] iwlwifi 0000:04:00.0: L1 Enabled; Disabling L0S
[15488.246815] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[15488.983767] wlan0: authenticate with <MAC address removed>
[15488.984719] wlan0: send auth to <MAC address removed> (try 1/3)
[15488.986503] wlan0: <MAC address removed> denied authentication (status 17)
[15489.847991] wlan0: authenticate with <MAC address removed>
[15489.849157] wlan0: send auth to <MAC address removed> (try 1/3)
[15489.854598] wlan0: <MAC address removed> denied authentication (status 17)
[15491.116613] wlan0: authenticate with <MAC address removed>
[15491.117759] wlan0: send auth to <MAC address removed> (try 1/3)
[15491.119691] wlan0: authenticated
[15491.122812] wlan0: associate with <MAC address removed> (try 1/3)
[15491.126091] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=1)
[15491.127082] wlan0: associated
[15491.127123] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[19363.946286] wlan0: authenticate with <MAC address removed>
[19363.947539] wlan0: send auth to <MAC address removed> (try 1/3)
[19363.949356] wlan0: authenticated
[19363.952777] wlan0: associate with <MAC address removed> (try 1/3)
[19363.956129] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=1)
[19363.957147] wlan0: associated
[24333.995170] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[24342.893939] Bluetooth: hci0: Intel Bluetooth firmware file: intel/ibt-hw-37.7.10-fw-1.80.2.3.d.bseq
[24343.041110] Bluetooth: hci0: Intel Bluetooth firmware patch completed and activated
[24343.254603] iwlwifi 0000:04:00.0: L1 Enabled; Disabling L0S
[24343.254860] iwlwifi 0000:04:00.0: L1 Enabled; Disabling L0S
[24343.266364] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[24344.036746] wlan0: authenticate with <MAC address removed>
[24344.037627] wlan0: send auth to <MAC address removed> (try 1/3)
[24344.040755] wlan0: authenticated
[24344.044158] wlan0: associate with <MAC address removed> (try 1/3)
[24344.047338] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=1)
[24344.047994] wlan0: associated
[24344.048014] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[27479.827204] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[27482.471896] Modules linked in: ctr ccm bnep rfcomm binfmt_misc snd_hda_codec_hdmi snd_hda_codec_conexant arc4 iwlmvm mac80211 uvcvideo videobuf2_vmalloc videobuf2_memops videobuf2_core videodev x86_pkg_temp_thermal intel_powerclamp coretemp kvm crct10dif_pclmul crc32_pclmul ghash_clmulni_intel aesni_intel aes_x86_64 lrw gf128mul glue_helper ablk_helper cryptd joydev serio_raw iwlwifi rtsx_pci_ms cfg80211 lpc_ich memstick snd_hda_intel btusb snd_hda_codec bluetooth snd_hwdep mei_me snd_pcm mei snd_page_alloc snd_seq_midi snd_seq_midi_event snd_rawmidi i915 thinkpad_acpi nvram snd_seq snd_seq_device snd_timer drm_kms_helper video wmi drm snd mac_hid intel_smartconnect soundcore i2c_algo_bit parport_pc ppdev lp parport hid_logitech_dj usbhid hid rtsx_pci_sdmmc rtsx_pci ahci r8169 psmouse libahci mii
[27485.899888] Bluetooth: hci0: Intel Bluetooth firmware file: intel/ibt-hw-37.7.10-fw-1.80.2.3.d.bseq
[27486.017940] Bluetooth: hci0: Intel Bluetooth firmware patch completed and activated
[27486.192573] iwlwifi 0000:04:00.0: L1 Enabled; Disabling L0S
[27486.192834] iwlwifi 0000:04:00.0: L1 Enabled; Disabling L0S
[27486.204352] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[27487.647271] wlan0: authenticate with <MAC address removed>
[27487.648242] wlan0: send auth to <MAC address removed> (try 1/3)
[27487.653066] wlan0: authenticated
[27487.654643] wlan0: associate with <MAC address removed> (try 1/3)
[27487.657856] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=1)
[27487.658560] wlan0: associated
[27487.658577] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[27487.677334] wlan0: deauthenticating from <MAC address removed> by local choice (reason=2)
[27487.678962] wlan0: authenticate with <MAC address removed>
[27487.679606] wlan0: send auth to <MAC address removed> (try 1/3)
[27487.681394] wlan0: authenticated
[27487.682687] wlan0: associate with <MAC address removed> (try 1/3)
[27487.685933] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=1)
[27487.686692] wlan0: associated
[27491.716886] wlan0: disassociated from <MAC address removed> (Reason: 2)
[27491.724453] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[27492.574804] wlan0: authenticate with <MAC address removed>
[27492.575524] wlan0: send auth to <MAC address removed> (try 1/3)
[27492.577291] wlan0: authenticated
[27492.579618] wlan0: associate with <MAC address removed> (try 1/3)
[27492.582880] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=1)
[27492.583600] wlan0: associated
[46517.846777] wlan0: authenticate with <MAC address removed>
[46517.847740] wlan0: send auth to <MAC address removed> (try 1/3)
[46517.853501] wlan0: authenticated
[46517.854434] wlan0: associate with <MAC address removed> (try 1/3)
[46517.947883] wlan0: associate with <MAC address removed> (try 2/3)
[46518.016867] wlan0: associate with <MAC address removed> (try 3/3)
[46518.098569] wlan0: association with <MAC address removed> timed out
[46519.348607] wlan0: authenticate with <MAC address removed>
[46519.349569] wlan0: direct probe to <MAC address removed> (try 1/3)
[46519.552860] wlan0: send auth to <MAC address removed> (try 2/3)
[46519.624296] wlan0: send auth to <MAC address removed> (try 3/3)
[46519.626146] wlan0: authenticated
[46519.628261] wlan0: associate with <MAC address removed> (try 1/3)
[46519.693969] wlan0: associate with <MAC address removed> (try 2/3)
[46519.697920] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=1)
[46519.700783] wlan0: associated
[46523.965669] wlan0: authenticate with <MAC address removed>
[46523.966693] wlan0: send auth to <MAC address removed> (try 1/3)
[46524.031927] wlan0: send auth to <MAC address removed> (try 2/3)
[46524.086640] wlan0: send auth to <MAC address removed> (try 3/3)
[46524.158945] wlan0: authentication with <MAC address removed> timed out
[46531.166488] wlan0: authenticate with <MAC address removed>
[46531.167667] wlan0: send auth to <MAC address removed> (try 1/3)
[46531.169467] wlan0: authenticated
[46531.171787] wlan0: associate with <MAC address removed> (try 1/3)
[46531.175113] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=1)
[46531.177749] wlan0: associated
[46532.578869] wlan0: authenticate with <MAC address removed>
[46532.580172] wlan0: send auth to <MAC address removed> (try 1/3)
[46532.629488] wlan0: send auth to <MAC address removed> (try 2/3)
[46532.690937] wlan0: send auth to <MAC address removed> (try 3/3)
[46532.743343] wlan0: authentication with <MAC address removed> timed out
[46547.039720] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[79181.207317] wlan0: authenticate with <MAC address removed>
[79181.208252] wlan0: send auth to <MAC address removed> (try 1/3)
[79181.212171] wlan0: authenticated
[79181.214784] wlan0: associate with <MAC address removed> (try 1/3)
[79181.217968] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=3)
[79181.218614] wlan0: associated
[79181.218630] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[94597.919707] wlan0: authenticate with <MAC address removed>
[94597.920514] wlan0: send auth to <MAC address removed> (try 1/3)
[94597.922354] wlan0: authenticated
[94597.924385] wlan0: associate with <MAC address removed> (try 1/3)
[94597.932331] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=3)
[94597.933622] wlan0: associated
[94760.156410] wlan0: authenticate with <MAC address removed>
[94760.157227] wlan0: send auth to <MAC address removed> (try 1/3)
[94760.161816] wlan0: authenticated
[94760.162757] wlan0: associate with <MAC address removed> (try 1/3)
[94760.165950] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=3)
[94760.166680] wlan0: associated
[94896.092165] wlan0: authenticate with <MAC address removed>
[94896.093333] wlan0: send auth to <MAC address removed> (try 1/3)
[94896.101707] wlan0: authenticated
[94896.102861] wlan0: associate with <MAC address removed> (try 1/3)
[94896.106244] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=3)
[94896.107409] wlan0: associated
[94932.868210] wlan0: authenticate with <MAC address removed>
[94932.869186] wlan0: send auth to <MAC address removed> (try 1/3)
[94932.881546] wlan0: authenticated
[94932.883711] wlan0: associate with <MAC address removed> (try 1/3)
[94932.947822] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=3)
[94932.949350] wlan0: associated
[94938.378558] wlan0: authenticate with <MAC address removed>
[94938.379758] wlan0: send auth to <MAC address removed> (try 1/3)
[94938.381568] wlan0: authenticated
[94938.385268] wlan0: associate with <MAC address removed> (try 1/3)
[94938.388666] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=3)
[94938.390248] wlan0: associated
[95034.835079] wlan0: disassociated from <MAC address removed> (Reason: 4)
[95034.865999] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[95034.866760] wlan0: authenticate with <MAC address removed>
[95034.867920] wlan0: send auth to <MAC address removed> (try 1/3)
[95034.869705] wlan0: <MAC address removed> denied authentication (status 17)
[95036.132603] wlan0: authenticate with <MAC address removed>
[95036.133717] wlan0: send auth to <MAC address removed> (try 1/3)
[95036.135617] wlan0: <MAC address removed> denied authentication (status 17)
[95037.898521] wlan0: authenticate with <MAC address removed>
[95037.899413] wlan0: send auth to <MAC address removed> (try 1/3)
[95037.978840] wlan0: send auth to <MAC address removed> (try 2/3)
[95038.045088] wlan0: send auth to <MAC address removed> (try 3/3)
[95038.106197] wlan0: authentication with <MAC address removed> timed out
[95049.975587] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[95110.528814] wlan0: authenticate with <MAC address removed>
[95110.529619] wlan0: send auth to <MAC address removed> (try 1/3)
[95110.531437] wlan0: authenticated
[95110.533483] wlan0: associate with <MAC address removed> (try 1/3)
[95110.536718] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=3)
[95110.537399] wlan0: associated
[95110.537416] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[97441.627498] wlan0: disassociated from <MAC address removed> (Reason: 4)
[97441.653584] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[97441.705203] wlan0: authenticate with <MAC address removed>
[97441.706442] wlan0: send auth to <MAC address removed> (try 1/3)
[97441.708283] wlan0: <MAC address removed> denied authentication (status 17)
[97457.439507] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[99941.490737] iwlwifi 0000:04:00.0: L1 Enabled; Disabling L0S
[99941.491035] iwlwifi 0000:04:00.0: L1 Enabled; Disabling L0S
[99941.503286] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[99942.252720] wlan0: authenticate with <MAC address removed>
[99942.253569] wlan0: send auth to <MAC address removed> (try 1/3)
[99942.255382] wlan0: authenticated
[99942.256841] wlan0: associate with <MAC address removed> (try 1/3)
[99942.260052] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=3)
[99942.260765] wlan0: associated
[99942.260781] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[104515.571931] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[104518.521289] iwlwifi 0000:04:00.0: L1 Enabled; Disabling L0S
[104518.521555] iwlwifi 0000:04:00.0: L1 Enabled; Disabling L0S
[104518.532897] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[104519.978521] wlan0: authenticate with <MAC address removed>
[104519.979669] wlan0: send auth to <MAC address removed> (try 1/3)
[104519.981552] wlan0: authenticated
[104519.984018] wlan0: associate with <MAC address removed> (try 1/3)
[104519.987326] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=3)
[104519.988287] wlan0: associated
[104519.988345] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[104520.006286] wlan0: deauthenticating from <MAC address removed> by local choice (reason=2)
[104520.008066] wlan0: authenticate with <MAC address removed>
[104520.008871] wlan0: send auth to <MAC address removed> (try 1/3)
[104520.010657] wlan0: authenticated
[104520.012063] wlan0: associate with <MAC address removed> (try 1/3)
[104520.015301] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=3)
[104520.016120] wlan0: associated
[105532.790821] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[105555.009599] wlan0: authenticate with <MAC address removed>
[105555.010411] wlan0: direct probe to <MAC address removed> (try 1/3)
[105555.213085] wlan0: direct probe to <MAC address removed> (try 2/3)
[105555.416976] wlan0: direct probe to <MAC address removed> (try 3/3)
[105555.620728] wlan0: authentication with <MAC address removed> timed out
[105582.355318] wlan0: authenticate with <MAC address removed>
[105582.356450] wlan0: send auth to <MAC address removed> (try 1/3)
[105582.358176] wlan0: authenticated
[105582.359387] wlan0: associate with <MAC address removed> (try 1/3)
[105582.362598] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=8)
[105582.363388] wlan0: associated
[105599.602702] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[105600.374682] wlan0: authenticate with <MAC address removed>
[105600.375438] wlan0: send auth to <MAC address removed> (try 1/3)
[105600.406584] wlan0: send auth to <MAC address removed> (try 2/3)
[105600.474688] wlan0: send auth to <MAC address removed> (try 3/3)
[105600.547633] wlan0: authentication with <MAC address removed> timed out
[105600.695412] wlan0: authenticate with <MAC address removed>
[105600.696487] wlan0: direct probe to <MAC address removed> (try 1/3)
[105600.898041] wlan0: direct probe to <MAC address removed> (try 2/3)
[105601.102356] wlan0: direct probe to <MAC address removed> (try 3/3)
[105601.306045] wlan0: authentication with <MAC address removed> timed out
[105628.404994] wlan0: authenticate with <MAC address removed>
[105628.405856] wlan0: send auth to <MAC address removed> (try 1/3)
[105628.409544] wlan0: authenticated
[105628.410686] wlan0: associate with <MAC address removed> (try 1/3)
[105628.413895] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=8)
[105628.414547] wlan0: associated
[106114.491473] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[106598.294965] iwlwifi 0000:04:00.0: L1 Enabled; Disabling L0S
[106598.295299] iwlwifi 0000:04:00.0: L1 Enabled; Disabling L0S
[106598.307655] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[106599.742818] wlan0: authenticate with <MAC address removed>
[106599.743688] wlan0: send auth to <MAC address removed> (try 1/3)
[106599.758338] wlan0: authenticated
[106599.759681] wlan0: associate with <MAC address removed> (try 1/3)
[106599.762915] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=3)
[106599.764677] wlan0: associated
[106599.764702] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[106599.785787] wlan0: deauthenticating from <MAC address removed> by local choice (reason=2)
[106599.787571] wlan0: authenticate with <MAC address removed>
[106599.788438] wlan0: send auth to <MAC address removed> (try 1/3)
[106599.790152] wlan0: authenticated
[106599.791729] wlan0: associate with <MAC address removed> (try 1/3)
[106599.794981] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=3)
[106599.796632] wlan0: associated
[106603.823850] wlan0: disassociated from <MAC address removed> (Reason: 2)
[106603.829474] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[106604.678634] wlan0: authenticate with <MAC address removed>
[106604.679830] wlan0: send auth to <MAC address removed> (try 1/3)
[106604.681778] wlan0: authenticated
[106604.684660] wlan0: associate with <MAC address removed> (try 1/3)
[106604.687976] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=3)
[106604.689000] wlan0: associated
[108461.339827] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[108463.877015] Modules linked in: usblp usb_storage ctr ccm bnep rfcomm binfmt_misc snd_hda_codec_hdmi snd_hda_codec_conexant arc4 iwlmvm mac80211 uvcvideo videobuf2_vmalloc videobuf2_memops videobuf2_core videodev x86_pkg_temp_thermal intel_powerclamp coretemp kvm crct10dif_pclmul crc32_pclmul ghash_clmulni_intel aesni_intel aes_x86_64 lrw gf128mul glue_helper ablk_helper cryptd joydev serio_raw iwlwifi rtsx_pci_ms cfg80211 lpc_ich memstick snd_hda_intel btusb snd_hda_codec bluetooth snd_hwdep mei_me snd_pcm mei snd_page_alloc snd_seq_midi snd_seq_midi_event snd_rawmidi i915 thinkpad_acpi nvram snd_seq snd_seq_device snd_timer drm_kms_helper video wmi drm snd mac_hid intel_smartconnect soundcore i2c_algo_bit parport_pc ppdev lp parport hid_logitech_dj usbhid hid rtsx_pci_sdmmc rtsx_pci ahci r8169 psmouse libahci mii
[108467.372003] Bluetooth: hci0: Intel Bluetooth firmware file: intel/ibt-hw-37.7.10-fw-1.80.2.3.d.bseq
[108467.477058] Bluetooth: hci0: Intel Bluetooth firmware patch completed and activated
[108468.205889] iwlwifi 0000:04:00.0: L1 Enabled; Disabling L0S
[108468.206149] iwlwifi 0000:04:00.0: L1 Enabled; Disabling L0S
[108468.218461] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[108469.658281] wlan0: authenticate with <MAC address removed>
[108469.659353] wlan0: send auth to <MAC address removed> (try 1/3)
[108469.661181] wlan0: authenticated
[108469.664411] wlan0: associate with <MAC address removed> (try 1/3)
[108469.667671] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=2)
[108469.675400] wlan0: associated
[108469.675421] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[108469.686132] wlan0: deauthenticating from <MAC address removed> by local choice (reason=2)
[108469.689041] wlan0: authenticate with <MAC address removed>
[108469.689736] wlan0: send auth to <MAC address removed> (try 1/3)
[108469.695529] wlan0: authenticated
[108469.696427] wlan0: associate with <MAC address removed> (try 1/3)
[108469.699676] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=2)
[108469.700892] wlan0: associated
[108473.728991] wlan0: disassociated from <MAC address removed> (Reason: 2)
[108473.733949] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[108474.582726] wlan0: authenticate with <MAC address removed>
[108474.583741] wlan0: send auth to <MAC address removed> (try 1/3)
[108474.585490] wlan0: authenticated
[108474.589344] wlan0: associate with <MAC address removed> (try 1/3)
[108474.592651] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=2)
[108474.593632] wlan0: associated
[111900.797479] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[111903.791463] Modules linked in: usblp usb_storage ctr ccm bnep rfcomm binfmt_misc snd_hda_codec_hdmi snd_hda_codec_conexant arc4 iwlmvm mac80211 uvcvideo videobuf2_vmalloc videobuf2_memops videobuf2_core videodev x86_pkg_temp_thermal intel_powerclamp coretemp kvm crct10dif_pclmul crc32_pclmul ghash_clmulni_intel aesni_intel aes_x86_64 lrw gf128mul glue_helper ablk_helper cryptd joydev serio_raw iwlwifi rtsx_pci_ms cfg80211 lpc_ich memstick snd_hda_intel btusb snd_hda_codec bluetooth snd_hwdep mei_me snd_pcm mei snd_page_alloc snd_seq_midi snd_seq_midi_event snd_rawmidi i915 thinkpad_acpi nvram snd_seq snd_seq_device snd_timer drm_kms_helper video wmi drm snd mac_hid intel_smartconnect soundcore i2c_algo_bit parport_pc ppdev lp parport hid_logitech_dj usbhid hid rtsx_pci_sdmmc rtsx_pci ahci r8169 psmouse libahci mii
[111907.272546] Bluetooth: hci0: Intel Bluetooth firmware file: intel/ibt-hw-37.7.10-fw-1.80.2.3.d.bseq
[111907.421583] Bluetooth: hci0: Intel Bluetooth firmware patch completed and activated
[111907.556881] iwlwifi 0000:04:00.0: L1 Enabled; Disabling L0S
[111907.557207] iwlwifi 0000:04:00.0: L1 Enabled; Disabling L0S
[111907.569324] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[111908.323386] wlan0: authenticate with <MAC address removed>
[111908.324210] wlan0: send auth to <MAC address removed> (try 1/3)
[111908.326646] wlan0: authenticated
[111908.329587] wlan0: associate with <MAC address removed> (try 1/3)
[111908.332830] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=3)
[111908.333545] wlan0: associated
[111908.333559] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[112156.143276] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[112156.915352] wlan0: authenticate with <MAC address removed>
[112156.916500] wlan0: send auth to <MAC address removed> (try 1/3)
[112156.986967] wlan0: send auth to <MAC address removed> (try 2/3)
[112157.048482] wlan0: send auth to <MAC address removed> (try 3/3)
[112157.118115] wlan0: authentication with <MAC address removed> timed out
[112184.405260] wlan0: authenticate with <MAC address removed>
[112184.406165] wlan0: send auth to <MAC address removed> (try 1/3)
[112184.418323] wlan0: authenticated
[112184.421718] wlan0: associate with <MAC address removed> (try 1/3)
[112184.424989] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=3)
[112184.425808] wlan0: associated
[114057.045121] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[114057.818858] wlan0: authenticate with <MAC address removed>
[114057.820083] wlan0: send auth to <MAC address removed> (try 1/3)
[114057.859739] wlan0: send auth to <MAC address removed> (try 2/3)
[114057.930025] wlan0: send auth to <MAC address removed> (try 3/3)
[114057.976266] wlan0: authentication with <MAC address removed> timed out
[114058.127979] wlan0: authenticate with <MAC address removed>
[114058.128941] wlan0: direct probe to <MAC address removed> (try 1/3)
[114058.330773] wlan0: direct probe to <MAC address removed> (try 2/3)
[114058.534986] wlan0: direct probe to <MAC address removed> (try 3/3)
[114058.738641] wlan0: authentication with <MAC address removed> timed out
[114085.874266] wlan0: authenticate with <MAC address removed>
[114085.875246] wlan0: send auth to <MAC address removed> (try 1/3)
[114085.890662] wlan0: authenticated
[114085.893751] wlan0: associate with <MAC address removed> (try 1/3)
[114085.896999] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=3)
[114085.897721] wlan0: associated
[123413.328479] wlan0: authenticate with <MAC address removed>
[123413.329535] wlan0: send auth to <MAC address removed> (try 1/3)
[123413.511290] wlan0: send auth to <MAC address removed> (try 2/3)
[123413.520471] wlan0: authenticated
[123413.522678] wlan0: associate with <MAC address removed> (try 1/3)
[123413.525931] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=2)
[123413.526756] wlan0: associated
[123459.559830] wlan0: authenticate with <MAC address removed>
[123459.560699] wlan0: send auth to <MAC address removed> (try 1/3)
[123459.562748] wlan0: authenticated
[123459.564734] wlan0: associate with <MAC address removed> (try 1/3)
[123459.568011] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=2)
[123459.568640] wlan0: associated
[136135.620716] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[136143.532625] Bluetooth: hci0: Intel Bluetooth firmware file: intel/ibt-hw-37.7.10-fw-1.80.2.3.d.bseq
[136143.672772] Bluetooth: hci0: Intel Bluetooth firmware patch completed and activated
[136144.408878] iwlwifi 0000:04:00.0: L1 Enabled; Disabling L0S
[136144.409142] iwlwifi 0000:04:00.0: L1 Enabled; Disabling L0S
[136144.420964] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[136145.187694] wlan0: authenticate with <MAC address removed>
[136145.188536] wlan0: send auth to <MAC address removed> (try 1/3)
[136145.193160] wlan0: authenticated
[136145.194348] wlan0: associate with <MAC address removed> (try 1/3)
[136145.197721] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=2)
[136145.198379] wlan0: associated
[136145.198403] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[137391.047874] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[137393.729705] iwlwifi 0000:04:00.0: L1 Enabled; Disabling L0S
[137393.729975] iwlwifi 0000:04:00.0: L1 Enabled; Disabling L0S
[137393.743086] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[137395.182556] wlan0: authenticate with <MAC address removed>
[137395.183675] wlan0: send auth to <MAC address removed> (try 1/3)
[137395.185431] wlan0: authenticated
[137395.185808] wlan0: associate with <MAC address removed> (try 1/3)
[137395.189112] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=2)
[137395.190035] wlan0: associated
[137395.190067] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[137395.216116] wlan0: deauthenticating from <MAC address removed> by local choice (reason=2)
[137395.217719] wlan0: authenticate with <MAC address removed>
[137395.218533] wlan0: send auth to <MAC address removed> (try 1/3)
[137395.220224] wlan0: authenticated
[137395.221784] wlan0: associate with <MAC address removed> (try 1/3)
[137395.225030] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=2)
[137395.225814] wlan0: associated
[137399.251008] wlan0: disassociated from <MAC address removed> (Reason: 2)
[137399.267599] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[137400.116663] wlan0: authenticate with <MAC address removed>
[137400.117687] wlan0: send auth to <MAC address removed> (try 1/3)
[137400.119532] wlan0: authenticated
[137400.122718] wlan0: associate with <MAC address removed> (try 1/3)
[137400.127478] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=2)
[137400.130351] wlan0: associated
[137406.710783] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[137407.538826] wlan0: authenticate with <MAC address removed>
[137407.539618] wlan0: send auth to <MAC address removed> (try 1/3)
[137407.612108] wlan0: send auth to <MAC address removed> (try 2/3)
[137407.686667] wlan0: send auth to <MAC address removed> (try 3/3)
[137407.753160] wlan0: authentication with <MAC address removed> timed out
[137407.905707] wlan0: authenticate with <MAC address removed>
[137407.906677] wlan0: direct probe to <MAC address removed> (try 1/3)
[137408.112352] wlan0: direct probe to <MAC address removed> (try 2/3)
[137408.317412] wlan0: direct probe to <MAC address removed> (try 3/3)
[137408.519139] wlan0: authentication with <MAC address removed> timed out
[137435.357555] wlan0: authenticate with <MAC address removed>
[137435.358430] wlan0: send auth to <MAC address removed> (try 1/3)
[137435.360215] wlan0: authenticated
[137435.361674] wlan0: associate with <MAC address removed> (try 1/3)
[137435.364887] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=2)
[137435.365564] wlan0: associated
[138731.206028] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[138734.596328] Modules linked in: usblp usb_storage ctr ccm bnep rfcomm binfmt_misc snd_hda_codec_hdmi snd_hda_codec_conexant arc4 iwlmvm mac80211 uvcvideo videobuf2_vmalloc videobuf2_memops videobuf2_core videodev x86_pkg_temp_thermal intel_powerclamp coretemp kvm crct10dif_pclmul crc32_pclmul ghash_clmulni_intel aesni_intel aes_x86_64 lrw gf128mul glue_helper ablk_helper cryptd joydev serio_raw iwlwifi rtsx_pci_ms cfg80211 lpc_ich memstick snd_hda_intel btusb snd_hda_codec bluetooth snd_hwdep mei_me snd_pcm mei snd_page_alloc snd_seq_midi snd_seq_midi_event snd_rawmidi i915 thinkpad_acpi nvram snd_seq snd_seq_device snd_timer drm_kms_helper video wmi drm snd mac_hid intel_smartconnect soundcore i2c_algo_bit parport_pc ppdev lp parport hid_logitech_dj usbhid hid rtsx_pci_sdmmc rtsx_pci ahci r8169 psmouse libahci mii
[138738.116440] Bluetooth: hci0: Intel Bluetooth firmware file: intel/ibt-hw-37.7.10-fw-1.80.2.3.d.bseq
[138738.218458] Bluetooth: hci0: Intel Bluetooth firmware patch completed and activated
[138738.513732] iwlwifi 0000:04:00.0: L1 Enabled; Disabling L0S
[138738.514030] iwlwifi 0000:04:00.0: L1 Enabled; Disabling L0S
[138738.526571] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[138740.024637] wlan0: authenticate with <MAC address removed>
[138740.025924] wlan0: send auth to <MAC address removed> (try 1/3)
[138740.029262] wlan0: authenticated
[138740.031387] wlan0: associate with <MAC address removed> (try 1/3)
[138740.034681] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=2)
[138740.035561] wlan0: associated
[138740.035665] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[138740.063923] wlan0: deauthenticating from <MAC address removed> by local choice (reason=2)
[138740.065945] wlan0: authenticate with <MAC address removed>
[138740.066835] wlan0: send auth to <MAC address removed> (try 1/3)
[138740.068711] wlan0: authenticated
[138740.071411] wlan0: associate with <MAC address removed> (try 1/3)
[138740.074701] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=2)
[138740.075566] wlan0: associated
[140981.480812] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[140985.028559] iwlwifi 0000:04:00.0: L1 Enabled; Disabling L0S
[140985.028814] iwlwifi 0000:04:00.0: L1 Enabled; Disabling L0S
[140985.041309] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[140986.472043] wlan0: authenticate with <MAC address removed>
[140986.472817] wlan0: send auth to <MAC address removed> (try 1/3)
[140986.478153] wlan0: authenticated
[140986.480338] wlan0: associate with <MAC address removed> (try 1/3)
[140986.483559] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=2)
[140986.484314] wlan0: associated
[140986.484346] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[140986.507397] wlan0: deauthenticating from <MAC address removed> by local choice (reason=2)
[140986.509195] wlan0: authenticate with <MAC address removed>
[140986.509928] wlan0: send auth to <MAC address removed> (try 1/3)
[140986.511670] wlan0: authenticated
[140986.512355] wlan0: associate with <MAC address removed> (try 1/3)
[140986.515604] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=2)
[140986.516500] wlan0: associated
[140988.523857] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[140989.237454] wlan0: authenticate with <MAC address removed>
[140989.238603] wlan0: send auth to <MAC address removed> (try 1/3)
[140989.310217] wlan0: send auth to <MAC address removed> (try 2/3)
[140989.391922] wlan0: send auth to <MAC address removed> (try 3/3)
[140989.479849] wlan0: authentication with <MAC address removed> timed out
[141339.257576] Modules linked in: usblp usb_storage ctr ccm bnep rfcomm binfmt_misc snd_hda_codec_hdmi snd_hda_codec_conexant arc4 iwlmvm mac80211 uvcvideo videobuf2_vmalloc videobuf2_memops videobuf2_core videodev x86_pkg_temp_thermal intel_powerclamp coretemp kvm crct10dif_pclmul crc32_pclmul ghash_clmulni_intel aesni_intel aes_x86_64 lrw gf128mul glue_helper ablk_helper cryptd joydev serio_raw iwlwifi rtsx_pci_ms cfg80211 lpc_ich memstick snd_hda_intel btusb snd_hda_codec bluetooth snd_hwdep mei_me snd_pcm mei snd_page_alloc snd_seq_midi snd_seq_midi_event snd_rawmidi i915 thinkpad_acpi nvram snd_seq snd_seq_device snd_timer drm_kms_helper video wmi drm snd mac_hid intel_smartconnect soundcore i2c_algo_bit parport_pc ppdev lp parport hid_logitech_dj usbhid hid rtsx_pci_sdmmc rtsx_pci ahci r8169 psmouse libahci mii
[141342.680414] Bluetooth: hci0: Intel Bluetooth firmware file: intel/ibt-hw-37.7.10-fw-1.80.2.3.d.bseq
[141342.813572] Bluetooth: hci0: Intel Bluetooth firmware patch completed and activated
[141343.014186] iwlwifi 0000:04:00.0: L1 Enabled; Disabling L0S
[141343.014447] iwlwifi 0000:04:00.0: L1 Enabled; Disabling L0S
[141343.027281] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[141343.778126] wlan0: authenticate with <MAC address removed>
[141343.779205] wlan0: send auth to <MAC address removed> (try 1/3)
[141343.792563] wlan0: authenticated
[141343.795695] wlan0: associate with <MAC address removed> (try 1/3)
[141343.798925] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=2)
[141343.799589] wlan0: associated
[141343.799615] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[141365.593281] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[141366.369741] wlan0: authenticate with <MAC address removed>
[141366.370693] wlan0: direct probe to <MAC address removed> (try 1/3)
[141366.575250] wlan0: direct probe to <MAC address removed> (try 2/3)
[141366.779524] wlan0: direct probe to <MAC address removed> (try 3/3)
[141366.982968] wlan0: authentication with <MAC address removed> timed out
[141394.355839] wlan0: authenticate with <MAC address removed>
[141394.356673] wlan0: send auth to <MAC address removed> (try 1/3)
[141394.358469] wlan0: authenticated
[141394.362316] wlan0: associate with <MAC address removed> (try 1/3)
[141394.365531] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=2)
[141394.366366] wlan0: associated
[150214.523088] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[150220.463764] Bluetooth: hci0: Intel Bluetooth firmware file: intel/ibt-hw-37.7.10-fw-1.80.2.3.d.bseq
[150220.604691] Bluetooth: hci0: Intel Bluetooth firmware patch completed and activated
[150220.837002] iwlwifi 0000:04:00.0: L1 Enabled; Disabling L0S
[150220.837308] iwlwifi 0000:04:00.0: L1 Enabled; Disabling L0S
[150220.849118] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[150221.597132] wlan0: authenticate with <MAC address removed>
[150221.598114] wlan0: send auth to <MAC address removed> (try 1/3)
[150221.603493] wlan0: authenticated
[150221.605833] wlan0: associate with <MAC address removed> (try 1/3)
[150221.610189] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=2)
[150221.611388] wlan0: associated
[150221.611406] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[150309.212546] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[150309.310533] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[150310.265516] iwlwifi 0000:04:00.0: L1 Enabled; Disabling L0S
[150310.265785] iwlwifi 0000:04:00.0: L1 Enabled; Disabling L0S
[150310.278316] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[150310.278528] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[150311.049268] wlan0: authenticate with <MAC address removed>
[150311.050304] wlan0: send auth to <MAC address removed> (try 1/3)
[150311.052145] wlan0: authenticated
[150311.055393] wlan0: associate with <MAC address removed> (try 1/3)
[150311.058611] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=2)
[150311.059330] wlan0: associated
[150311.059373] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[150316.101938] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[150316.820399] wlan0: authenticate with <MAC address removed>
[150316.821610] wlan0: send auth to <MAC address removed> (try 1/3)
[150316.895047] wlan0: send auth to <MAC address removed> (try 2/3)
[150316.987595] wlan0: send auth to <MAC address removed> (try 3/3)
[150317.068568] wlan0: authentication with <MAC address removed> timed out
[150317.220758] wlan0: authenticate with <MAC address removed>
[150317.221976] wlan0: direct probe to <MAC address removed> (try 1/3)
[150317.426637] wlan0: direct probe to <MAC address removed> (try 2/3)
[150317.630839] wlan0: direct probe to <MAC address removed> (try 3/3)
[150317.834226] wlan0: authentication with <MAC address removed> timed out
[150344.302901] wlan0: authenticate with <MAC address removed>
[150344.303831] wlan0: send auth to <MAC address removed> (try 1/3)
[150344.307414] wlan0: authenticated
[150344.308685] wlan0: associate with <MAC address removed> (try 1/3)
[150344.313337] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=2)
[150344.314520] wlan0: associated

########## wireless info END ############

```

As I mentioned, we have multiple devices, but as all devices except the Edubuntu 14.04s are connecting, I'm assuming a fix for this machine will work for the others.

I don't know if its relevant, but the network I am trying to access is "DDW3654F"

---

### Post by varunendra on 2014-06-15
Can you post a report of **[This script]("http://ubuntuforums.org/showpost.php?p=13024222")** please? From a laptop which tries and fails to connect to the AP in question, and not connected to any other connection.

In the meanwhile, please try -
```
sudo modprobe -rv iwlmvm
sudo modprobe -v iwlwifi bt_coex_active=N swcrypto=1
sudo modprobe -v iwlmvm power_scheme=1
```
This will be a temporary change that will be lost at next boot. If it helps, we can determine exactly which parameter(s) helped, and make it permanent.

---

### Post by jdix123 on 2014-06-16
Ok, the business with the modprobe did not produce any noticeable results.  Still no connection.

I'm confused about running that script without a connection, because doesn't wget require an internet connection?  So I downloaded the script, then disconnected from the connection, and then ran the script.

```


	======== Wireless-Info START ========

System-Info ~~~~~~~~~~~~~~~~~~~~~~~~

SEDToshiba5 3.13.0-29-generic x86_64,  Ubuntu 14.04 LTS, trusty

CPU    : AMD E2-3800 APU with Radeon(TM) HD Graphics
Memory : 3335 MB
Uptime : 15:46:58 up  2:02,  2 users,  load average: 0.23, 0.45, 0.33


lspci ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

01:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 07)
	Subsystem: Toshiba America Info Systems Device [1179:ff1e]
	Kernel driver in use: r8169
05:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8188EE Wireless Network Adapter [10ec:8179] (rev 01)
	Subsystem: Realtek Semiconductor Co., Ltd. Device [10ec:0181]
	Kernel driver in use: rtl8188ee


lsusb ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Bus 002 Device 003: ID 10f1:1a52 Importek 
Bus 002 Device 002: ID 0bda:0129 Realtek Semiconductor Corp. RTS5129 Card Reader Controller
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 005 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


PCMCIA Card Info ~~~~~~~~~~~~~~~~~~~



iwconfig ~~~~~~~~~~~~~~~~~~~~~~~~~~~

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          


rfkill ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

      Interface        Soft blocked  Hard blocked
0: phy0: Wireless LAN      no            no


lsmod ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

iwlmvm                189774  0 
iwlwifi               169932  1 iwlmvm
rtl8188ee              89601  0 
rtl_pci                26690  1 rtl8188ee
rtlwifi                63475  2 rtl_pci,rtl8188ee
mac80211              626557  4 rtl_pci,rtlwifi,iwlmvm,rtl8188ee
cfg80211              484040  4 iwlwifi,mac80211,rtlwifi,iwlmvm


module parameters ~~~~~~~~~~~~~~~~~~

cfg80211      (2): cfg80211_disable_40mhz_24ghz=N | ieee80211_regdom=00
iwlmvm        (2): init_dbg=N | power_scheme=1
iwlwifi      (11): 11n_disable=0 | amsdu_size_8K=0 | antenna_coupling=0 | bt_coex_active=N | fw_restart=Y | led_mode=0 | nvm_file=(null) | power_level=0 | power_save=N | swcrypto=1 | wd_disable=1
mac80211      (5): beacon_loss_count=7 | ieee80211_default_rc_algo=minstrel_ht | max_nullfunc_tries=2 | max_probe_tries=5 | probe_wait_ms=500
rtl8188ee     (5): debug=0 | fwlps=Y | ips=Y | swenc=N | swlps=N


nm-tool ~~~~~~~~~~~~~~~~~~~~~~~~~~~~

State: disconnected
================o=============o===========o==============o=========o===========o==============o===========
 Interface & ID | Type        | Driver    | State        | Default | Speed     | Support      | HW Addr   
================o=============o===========o==============o=========o===========o==============o===========
 wlan0          | 802.11 WiFi | rtl8188ee | disconnected | no      |           | WEP/WPA/WPA2 | <MAC wlan0>

    Peter Lecca DDS: Infra, <MAC C-04 Peter Lecca DDS>, Freq 2437 MHz, Rate 54 Mb/s, Strength 60 WPA2
    Peter Lecca Guest: Infra, <MAC C-03 Peter Lecca Guest>, Freq 2437 MHz, Rate 54 Mb/s, Strength 37 WPA2
    10FX11206343:    Infra, <MAC C-05 10FX11206343>, Freq 2437 MHz, Rate 54 Mb/s, Strength 27 WEP
    DDW3654F:        Infra, <MAC C-06 DDW3654F>, Freq 2462 MHz, Rate 54 Mb/s, Strength 67 WPA2
    UNITE-8D9B:      Infra, <MAC C-01 UNITE-8D9B>, Freq 2412 MHz, Rate 54 Mb/s, Strength 74 WPA2
----------------+-------------+-----------+--------------+---------+-----------+--------------+-----------
 eth0           | Wired       | r8169     | unavailable  | no      |           |              | <MAC eth0>
----------------+-------------+-----------+--------------+---------+-----------+--------------+-----------


NetworkManager.state ~~~~~~~~~~~~~~~
[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true


NetworkManager.conf ~~~~~~~~~~~~~~~~

[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq

[ifupdown]
managed=false


NM WiFi Profiles ~~~~~~~~~~~~~~~~~~~

DDW3654F             : ssid=DDW3654F | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 
MCCGM                : ssid=MCCGM | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 
MCCGM 1              : ssid=MCCGM | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 
UNITE-8D9B           : ssid=UNITE-8D9B | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 


interfaces ~~~~~~~~~~~~~~~~~~~~~~~~~

# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback

resolv.conf ~~~~~~~~~~~~~~~~~~~~~~~~



Routes & Ping ~~~~~~~~~~~~~~~~~~~~~~

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface


iw reg get ~~~~~~~~~~~~~~~~~~~~~~~~~

(Region : "en_US.UTF-8")
country 00:
	(2402 - 2472 @ 40), (3, 20)
	(2457 - 2482 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
	(2474 - 2494 @ 20), (3, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
	(5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
	(5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS


iwlist chan ~~~~~~~~~~~~~~~~~~~~~~~~

wlan0     13 channels in total; available frequencies :
          Channel 01 (2.412 GHz) - 13 (2.472 GHz)


iwlist scan ~~~~~~~~~~~~~~~~~~~~~~~~

wlan0     Scan completed :
          Cell 01 - Address: <MAC C-01 UNITE-8D9B>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=66/70  Signal level=-44 dBm  
                    Encryption key:on
                    ESSID:"UNITE-8D9B"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000000151a4f5c
                    Extra: Last beacon: 8ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC C-02 DDW3654F>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=70/70  Signal level=-36 dBm  
                    Encryption key:on
                    ESSID:"DDW3654F"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000259334e3fc
                    Extra: Last beacon: 8ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: <MAC C-03 Peter Lecca Guest>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=36/70  Signal level=-74 dBm  
                    Encryption key:on
                    ESSID:"Peter Lecca Guest"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000002eaad58e6f5
                    Extra: Last beacon: 8ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 04 - Address: <MAC C-04 Peter Lecca DDS>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=36/70  Signal level=-74 dBm  
                    Encryption key:on
                    ESSID:"Peter Lecca DDS"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000002eaad590885
                    Extra: Last beacon: 8ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 05 - Address: <MAC C-05 10FX11206343>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=70/70  Signal level=12 dBm  
                    Encryption key:on
                    ESSID:"10FX11206343"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000ef6ce3c031
                    Extra: Last beacon: 14724ms ago
          Cell 06 - Address: <MAC C-06 DDW3654F>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=70/70  Signal level=-36 dBm  
                    Encryption key:on
                    ESSID:"DDW3654F"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000259335318b
                    Extra: Last beacon: 24ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK


blacklist ~~~~~~~~~~~~~~~~~~~~~~~~~~

[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci


modinfo ~~~~~~~~~~~~~~~~~~~~~~~~~~~~

[iwlmvm]
filename:       /lib/modules/3.13.0-29-generic/kernel/drivers/net/wireless/iwlwifi/mvm/iwlmvm.ko
version:        in-tree:
srcversion:     964B69F7EBC572BE39F5C50
depends:        iwlwifi,mac80211,cfg80211
parm:           init_dbg:set to true to debug an ASSERT in INIT fw (default: false (bool)
parm:           power_scheme:power management scheme: 1-active, 2-balanced, 3-low power, default: 2 (int)

[iwlwifi]
filename:       /lib/modules/3.13.0-29-generic/kernel/drivers/net/wireless/iwlwifi/iwlwifi.ko
version:        in-tree:
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
firmware:       iwlwifi-3160-7.ucode
firmware:       iwlwifi-7260-7.ucode
srcversion:     1E6912E109D5A43B310FB34
depends:        cfg80211
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

[rtl8188ee]
filename:       /lib/modules/3.13.0-29-generic/kernel/drivers/net/wireless/rtlwifi/rtl8188ee/rtl8188ee.ko
firmware:       rtlwifi/rtl8188efw.bin
srcversion:     4BAAAC4E05987841F4E03EA
depends:        rtlwifi,rtl_pci,mac80211
parm:           swenc:Set to 1 for software crypto (default 0)
parm:           ips:Set to 0 to not use link power save (default 1)
parm:           swlps:Set to 1 to use SW control power save (default 0)
parm:           fwlps:Set to 1 to use FW control power save (default 1)
parm:           debug:Set debug level (0-5) (default 0) (int)

[rtl_pci]
filename:       /lib/modules/3.13.0-29-generic/kernel/drivers/net/wireless/rtlwifi/rtl_pci.ko
srcversion:     9B7F19319428FF0EFE7E350
depends:        mac80211,rtlwifi

[rtlwifi]
filename:       /lib/modules/3.13.0-29-generic/kernel/drivers/net/wireless/rtlwifi/rtlwifi.ko
srcversion:     27E91755814596D634B7709
depends:        mac80211,cfg80211

[mac80211]
filename:       /lib/modules/3.13.0-29-generic/kernel/net/mac80211/mac80211.ko
srcversion:     6F23437712851B1B0563BCB
depends:        cfg80211
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[cfg80211]
filename:       /lib/modules/3.13.0-29-generic/kernel/net/wireless/cfg80211.ko
srcversion:     8B3D642D1F2E6406EF33F74
depends:        
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)


udev rules ~~~~~~~~~~~~~~~~~~~~~~~~~

# PCI device 0x10ec:0x8136 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC eth0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

# PCI device 0x10ec:0x8179 (rtl8188ee)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC wlan0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"


Custom files/entries ~~~~~~~~~~~~~~~

/etc/modules        : Default
/etc/rc.local       : Default
/etc/modprobe.d     : Not Default
/etc/pm/(cnf|pw|sl) : Default

[/etc/modprobe.d]
iwlwifi.conf      : remove iwlwifi \
                    (/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
                    && /sbin/modprobe -r mac80211
mlx4.conf         : softdep mlx4_core post: mlx4_en


Kernel boot line ~~~~~~~~~~~~~~~~~~~

BOOT_IMAGE=/boot/vmlinuz-3.13.0-29-generic.efi.signed root=UUID=f6865643-d58f-4b6d-b813-2a8e05351553 ro quiet splash vt.handoff=7


dmesg ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

[    1.313644] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[    1.314372] audit: initializing netlink socket (disabled)
[    1.724026] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[   11.994109] rtl8188ee: Using firmware rtlwifi/rtl8188efw.bin
[   12.202806] ieee80211 phy0: Selected rate control algorithm 'rtl_rc'
[   12.203303] rtlwifi: wireless switch is on
[   14.798183] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   16.506951] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   16.507641] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   95.950569] wlan0: authenticate with <MAC C-02 DDW3654F>
[   95.969609] wlan0: send auth to <MAC C-02 DDW3654F> (try 1/3)
[   96.073190] wlan0: send auth to <MAC C-02 DDW3654F> (try 2/3)
[   96.177145] wlan0: send auth to <MAC C-02 DDW3654F> (try 3/3)
[   96.281135] wlan0: authentication with <MAC C-02 DDW3654F> timed out
[   96.426265] wlan0: authenticate with <MAC C-06 DDW3654F>
[   96.436478] wlan0: direct probe to <MAC C-06 DDW3654F> (try 1/3)
[   96.637065] wlan0: direct probe to <MAC C-06 DDW3654F> (try 2/3)
[   96.841020] wlan0: direct probe to <MAC C-06 DDW3654F> (try 3/3)
[   97.044973] wlan0: authentication with <MAC C-06 DDW3654F> timed out
[  447.286757] wlan0: authenticate with <MAC C-06 DDW3654F>
[  447.305935] wlan0: direct probe to <MAC C-06 DDW3654F> (try 1/3)
[  447.509527] wlan0: direct probe to <MAC C-06 DDW3654F> (try 2/3)
[  447.713468] wlan0: direct probe to <MAC C-06 DDW3654F> (try 3/3)
[  447.917424] wlan0: authentication with <MAC C-06 DDW3654F> timed out
[  489.479466] rtlwifi: wireless switch is on
[  492.814836] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  525.772682] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  683.361345] wlan0: authenticate with <MAC C-02 DDW3654F>
[  683.755941] wlan0: send auth to <MAC C-02 DDW3654F> (try 1/3)
[  683.856694] wlan0: send auth to <MAC C-02 DDW3654F> (try 2/3)
[  683.960732] wlan0: send auth to <MAC C-02 DDW3654F> (try 3/3)
[  684.064708] wlan0: authentication with <MAC C-02 DDW3654F> timed out
[  684.205742] wlan0: authenticate with <MAC C-06 DDW3654F>
[  684.216027] wlan0: direct probe to <MAC C-06 DDW3654F> (try 1/3)
[  684.416480] wlan0: direct probe to <MAC C-06 DDW3654F> (try 2/3)
[  684.620583] wlan0: direct probe to <MAC C-06 DDW3654F> (try 3/3)
[  684.824543] wlan0: authentication with <MAC C-06 DDW3654F> timed out
[  685.777816] wlan0: authenticate with <MAC C-06 DDW3654F>
[  685.796780] wlan0: direct probe to <MAC C-06 DDW3654F> (try 1/3)
[  686.000270] wlan0: direct probe to <MAC C-06 DDW3654F> (try 2/3)
[  686.204247] wlan0: direct probe to <MAC C-06 DDW3654F> (try 3/3)
[  686.408197] wlan0: authentication with <MAC C-06 DDW3654F> timed out
[  781.825233] wlan0: authenticate with <MAC C-01 UNITE-8D9B>
[  781.844110] wlan0: send auth to <MAC C-01 UNITE-8D9B> (try 1/3)
[  781.845564] wlan0: authenticated
[  781.847509] wlan0: associate with <MAC C-01 UNITE-8D9B> (try 1/3)
[  781.850461] wlan0: RX AssocResp from <MAC C-01 UNITE-8D9B> (capab=0x431 status=0 aid=3)
[  781.850598] wlan0: associated
[  781.850620] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 1096.904339] wlan0: deauthenticating from <MAC C-01 UNITE-8D9B> by local choice (reason=3)

	======== Done ========

```

---

### Post by varunendra on 2014-06-17
A few more questions -

Have you tried deleting all previously saved connections pertaining to that Access Point? Try it if you haven't already.
Why are there two APs appearing in 'iwlist scan' (Cell - 02 and Cell - 06)? Are there two APs with same SSID?
Is only the service provider changed or the router/access-point too? Can you provide link to the user manual of the AP?

---

### Post by jdix123 on 2014-06-17
This is a brand new AP for the office, and it is 6 laptops of identical make, model, and installs of edubuntu, plus one other make and model of laptop with the same version of edubuntu that are failing to connect.  As far as I know, there is just the one AP with the name DDW3654F.

As much as I'd love to know what happened just for the sake of my curiosity, surprisingly enough something that tech support did over the phone actually fixed it, I think they just changed the channel of the router.  Of course they wouldn't tell me how to log in myself and change the settings, but at least it is working now.  I appreciate the help!

---

