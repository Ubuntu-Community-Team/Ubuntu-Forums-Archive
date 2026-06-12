---
title: "Slow wireless through Zbox"
date: 2014-04-11
forum: Networking &amp; Wireless
---

### Post by Ron_Teeple on 2014-04-11
First, just want to say thanks to this forum I have been lurking for about 6 months now always been able to find a fix and tweaks to the system before now.

Second I have a Zbox that I use for multimedia through my TV running Ubuntu 12.04.  It has been working great but the wireless has been running slower for about a week.  Laptops get about 20mg/s that are placed in the same spot and the Zbox gets about 5mg/s.  I never had to test what the speed was before but the amount of buffering at all times of the day has increased significantly.  

Third still I'm a major noob to Ubuntu and the terminal is very foreign to me but will type what you tell me to.

Thanks again

(I will post the wireless script at the end of this post from the Zbox in a few min also I have disable "n" from the router already)

```


########## wireless info START ##########


##### release #####


Distributor ID:    Ubuntu
Description:    Ubuntu 12.04.4 LTS
Release:    12.04
Codename:    precise


##### kernel #####


Linux zbox-ZBOXSD-ID12-ID13 3.8.0-38-generic #56~precise1-Ubuntu SMP Thu Mar 13 16:23:47 UTC 2014 i686 i686 i386 GNU/Linux


##### lspci #####


01:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 03)
    Subsystem: ZOTAC International (MCO) Ltd. Device [19da:0123]
    Kernel driver in use: r8169


02:00.0 Network controller [0280]: Qualcomm Atheros Device [168c:0037] (rev 01)
    Subsystem: AzureWave Device [1a3b:1195]
    Kernel driver in use: ath9k


##### lsusb #####


Bus 001 Device 002: ID 05e3:0608 Genesys Logic, Inc. USB-2.0 4-Port HUB
Bus 005 Device 002: ID 0c45:7000 Microdia 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


##### PCMCIA Card Info #####


##### rfkill #####


0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no


##### iw reg get #####


##### interfaces #####


auto lo
iface lo inet loopback


##### iwconfig #####


wlan0     IEEE 802.11bgn  ESSID:"internet"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: <MAC address removed>   
          Bit Rate=54 Mb/s   Tx-Power=16 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=47/70  Signal level=-63 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:963  Invalid misc:10205   Missed beacon:0


##### route #####


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 wlan0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 wlan0
192.168.1.0     0.0.0.0         255.255.255.0   U     2      0        0 wlan0


##### resolv.conf #####


nameserver 127.0.0.1
search neo.rr.com


##### nm-tool #####


NetworkManager Tool


State: connected (global)


- Device: wlan0  [internet] ----------------------------------------------------
  Type:              802.11 WiFi
  Driver:            ath9k
  State:             connected
  Default:           yes
  HW Address:        <MAC address removed>


  Capabilities:
    Speed:           54 Mb/s


  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes


  Wireless Access Points (* = current AP)
    NETGEAR93:       Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 54 WPA2
    *internet:       Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 57 WPA
    ATT335:          Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 27 WPA WPA2
    FBI Surveillance:Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 32 WPA2
    DG860AA2:        Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 20 WPA2
    FBI Surveillance:Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 19 WPA2
    WRT54GS2:        Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 25 WPA2


  IPv4 Settings:
    Address:         192.168.1.138
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1


    DNS:             209.18.47.61
    DNS:             209.18.47.62


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
plugins=ifupdown,keyfile
dns=dnsmasq


[ifupdown]
managed=false


##### iwlist #####


wlan0     Scan completed :
          Cell 01 - Address: <MAC address removed>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=45/70  Signal level=-65 dBm  
                    Encryption key:on
                    ESSID:"internet"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000001ec6d3b186
                    Extra: Last beacon: 172ms ago
                    IE: Unknown: 0008696E7465726E6574
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD810050F204104A00011010440001021041000100103B00010310470010CDEFB33CC4A63C6B1788DE222D42C7481021000C4C696E6B73797320496E632E1023000D4C696E6B7379732045323030301024000776312E302E30341042000234321054000800060050F20400011011000D4C696E6B737973204532303030100800020084
                    IE: Unknown: DD090010180205F0040000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 02 - Address: <MAC address removed>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=23/70  Signal level=-87 dBm  
                    Encryption key:on
                    ESSID:"WRT54GS2"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000ba9751dbb1
                    Extra: Last beacon: 3628ms ago
                    IE: Unknown: 00085752543534475332
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030101
                    IE: Unknown: 2A0104
                    IE: Unknown: 2F0104
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD760050F204104A0001101044000102103B00010310470010E1BBB2B46DFCC171F1E62F77679A8C9A102100074C696E6B73797310230006526F757465721024000857525435344753321042000C43555130314A3437363732311054000800060050F2040001101100085752543534475332100800020084
                    IE: Unknown: DD090010180200F5000000
          Cell 03 - Address: <MAC address removed>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=29/70  Signal level=-81 dBm  
                    Encryption key:on
                    ESSID:"FBI Surveillance"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000099f693e387
                    Extra: Last beacon: 3620ms ago
                    IE: Unknown: 0010464249205375727665696C6C616E6365
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030101
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: 2D1AEF1103FFFF0000000000000000000000000000000406E6E70D00
                    IE: Unknown: 3D1601001500000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F0101
                    IE: Unknown: DD180050F2020101820003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C33EF1103FFFF0000000000000000000000000000000406E6E70D00
                    IE: Unknown: DD1A00904C3401001500000000000000000000000000000000000000
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: Unknown: DD900050F204104A0001101044000102103B00010310470010427974EECF6C52788C94000000000000102100046E6F6E65102300046E6F6E65102400046E6F6E651042001253657269616C204E756D62657220486572651054000800060050F204000110110016574E5232303030763428576972656C65737320415029100800022008103C0001011049000600372A000120
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 04 - Address: <MAC address removed>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=23/70  Signal level=-87 dBm  
                    Encryption key:on
                    ESSID:"DG860AA2"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000ba93c044d8
                    Extra: Last beacon: 3612ms ago
                    IE: Unknown: 00084447383630414132
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 030101
                    IE: Unknown: 2A0104
                    IE: Unknown: 32040C183060
                    IE: Unknown: 2D1A6C0017FFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1601000700000000000000000000000000000000000000
                    IE: Unknown: 3E0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: 0B0501001D127A
                    IE: Unknown: 7F0101
                    IE: Unknown: DD07000C4303000000
                    IE: Unknown: 0706555320010B10
                    IE: Unknown: DD870050F204104A0001101044000102103B000103104700102880288028801880A880F8EDA52306A010210005415252495310230006544738363247102400065254323836301042000831323334353637381054000800060050F204000110110012415252495320544738363220526F7574657210080002210C103C0001011049000600372A000120
          Cell 05 - Address: <MAC address removed>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=22/70  Signal level=-88 dBm  
                    Encryption key:on
                    ESSID:"NETGEAR18"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000024ab6d4976
                    Extra: Last beacon: 1484ms ago
                    IE: Unknown: 00094E4554474541523138
                    IE: Unknown: 010882840B162430486C
                    IE: Unknown: 03010B
                    IE: Unknown: 050401020000
                    IE: Unknown: 2A0104
                    IE: Unknown: 2F0104
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1AFC181FFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D160B001700000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F0101
                    IE: Unknown: DD310050F204104A000110104400010210470010D80ABF671096945121DFAF78D7F9767A103C0001031049000600372A000120
                    IE: Unknown: DD090010180207F0040000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 06 - Address: <MAC address removed>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=47/70  Signal level=-63 dBm  
                    Encryption key:on
                    ESSID:"NETGEAR93"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000ba94326183
                    Extra: Last beacon: 2044ms ago
                    IE: Unknown: 00094E4554474541523933
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030106
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1AFD191BFFFFFF0000000000000000000000000000000000000000
                    IE: Unknown: 3D1606081500000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F0101
                    IE: Unknown: DD8B0050F204104A0001101044000102103B00010310470010ABD220552BDF5ED8A4FA9C4198CC13981021000D4E4554474541522C20496E632E1023000A574E44523435303076321024000A574E445234353030763210420004343533361054000800060050F20400011011000A574E4452343530307632100800020004103C0001031049000600372A000120
                    IE: Unknown: DD090010180202F03C0000
                    IE: Unknown: DD180050F2020101800003A4000027A400004243BC0062326600
          Cell 07 - Address: <MAC address removed>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=29/70  Signal level=-81 dBm  
                    Encryption key:on
                    ESSID:"ATT335"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000ba92cf31b5
                    Extra: Last beacon: 2068ms ago
                    IE: Unknown: 0006415454333335
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030106
                    IE: Unknown: 0706555320010B1E
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1A1C181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1606001100000000000000000000000000000000000000
                    IE: Unknown: DD090010180200F02C0000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00


##### iwlist channel #####


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
          Current Frequency=2.462 GHz (Channel 11)


##### lsmod #####


ath9k                 136683  0 
mac80211              546061  1 ath9k
ath9k_common           13781  1 ath9k
ath9k_hw              406677  2 ath9k,ath9k_common
ath                    19435  3 ath9k,ath9k_common,ath9k_hw
cfg80211              454468  3 ath9k,mac80211,ath


##### modinfo #####


filename:       /lib/modules/3.8.0-38-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k.ko
license:        Dual BSD/GPL
description:    Support for Atheros 802.11n wireless LAN cards.
author:         Atheros Communications
srcversion:     E312829772C1F7035ACC133
alias:          platform:qca955x_wmac
alias:          platform:ar934x_wmac
alias:          platform:ar933x_wmac
alias:          platform:ath9k
alias:          pci:v0000168Cd00000036sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000037sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000034sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000033sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000032sv*sd*bc*sc*i*
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
vermagic:       3.8.0-38-generic SMP mod_unload modversions 686 
parm:           debug:Debugging mask (uint)
parm:           nohwcrypt:Disable hardware encryption (int)
parm:           blink:Enable LED blink on activity (int)
parm:           btcoex_enable:Enable wifi-BT coexistence (int)
parm:           enable_diversity:Enable Antenna diversity for AR9565 (int)
parm:           ps_enable:Enable WLAN PowerSave (int)


filename:       /lib/modules/3.8.0-38-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_common.ko
license:        Dual BSD/GPL
description:    Shared library for Atheros wireless 802.11n LAN cards.
author:         Atheros Communications
srcversion:     3D03F9DDA976A5AB5EAA737
depends:        ath,ath9k_hw
intree:         Y
vermagic:       3.8.0-38-generic SMP mod_unload modversions 686 


filename:       /lib/modules/3.8.0-38-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_hw.ko
license:        Dual BSD/GPL
description:    Support for Atheros 802.11n wireless LAN cards.
author:         Atheros Communications
srcversion:     CCE4DE0B5B797FACEF3BB03
depends:        ath
intree:         Y
vermagic:       3.8.0-38-generic SMP mod_unload modversions 686 


filename:       /lib/modules/3.8.0-38-generic/kernel/drivers/net/wireless/ath/ath.ko
license:        Dual BSD/GPL
description:    Shared library for Atheros wireless LAN cards.
author:         Atheros Communications
srcversion:     5627B8DA4AC105006A960BE
depends:        cfg80211
intree:         Y
vermagic:       3.8.0-38-generic SMP mod_unload modversions 686 


##### modules #####


lp


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


##### udev rules #####


# PCI device 0x10ec:/sys/devices/pci0000:00/0000:00:1c.0/0000:01:00.0 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"


# PCI device 0x168c:/sys/devices/pci0000:00/0000:00:1c.1/0000:02:00.0 (ath9k)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"


##### dmesg #####


[   12.344817] ath: EEPROM regdomain: 0x60
[   12.344819] ath: EEPROM indicates we should expect a direct regpair map
[   12.344823] ath: Country alpha2 being used: 00
[   12.344824] ath: Regpair used: 0x60
[   21.043053] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   21.046597] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   25.051345] wlan0: authenticate with <MAC address removed>
[   25.059059] wlan0: send auth to <MAC address removed> (try 1/3)
[   25.063745] wlan0: authenticated
[   25.064190] ath9k 0000:02:00.0 wlan0: disabling HT/VHT due to WEP/TKIP use
[   25.068061] wlan0: associate with <MAC address removed> (try 1/3)
[   25.071220] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=5)
[   25.071755] wlan0: associated
[   25.071775] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready


########## wireless info END ############
```

---

### Post by varunendra on 2014-04-12
Welcome to the forums Ron!

You are currently using "WPA + TKIP" encryption in your router/access-point. TKIP is an inefficient encryption algorithm and often causes speed issues. So please log into your router's admin web interface and change the encryption to "**WPA[COLOR="#0000CD"]2[/COLOR] + AES (CCMP)**". That is the most advanced encryption type and offers better security with better performance. Make sure to select pure WPA2, not WPA/WPA2 mixed mode! Reboot the router after saving the change.

If this alone doesn't help, try the following driver parameter in Ubuntu. Open a terminal (Ctrl-Alt-T) and run this command in it -
```
sudo modprobe -rv ath9k
sudo modprobe -v ath9k nohwcrypt=1
```
This will be a temporary change that will be lost at next boot. If it helps, we can make it permanent.

Post back how it goes. We may try a newer driver if required, but keep the encryption as recommended above.

---

