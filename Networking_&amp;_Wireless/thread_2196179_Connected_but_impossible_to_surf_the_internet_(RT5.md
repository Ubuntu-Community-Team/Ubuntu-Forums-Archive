---
title: "Connected but impossible to surf the internet (RT5390)"
date: 2013-12-28
forum: Networking &amp; Wireless
---

### Post by makkekkazzo on 2013-12-28
Hi to everybody,
my laptop is an ASUS F55A and the wireless internet connection sometimes works and sometimes doesn't work for long times. The wireless icon says that I'm always connected, even when is not working, but it doesn't charge any page. I've already followed the solution written in the 13th post in this thread ([http://ubuntuforums.org/showthread.php?t=2173907&page=2&highlight=rt5390](http://ubuntuforums.org/showthread.php?t=2173907&page=2&highlight=rt5390)) and here is the result from the code wget -N -t 5 -T 10 [http://dl.dropbox.com/u/57264241/wireless_script](http://dl.dropbox.com/u/57264241/wireless_script) && chmod +x wireless_script && ./wireless_script

```
*************** info trace ***************

***** uname -a *****

Linux fra 3.8.0-34-generic #49~precise1-Ubuntu SMP Wed Nov 13 18:05:00 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux

***** lsb_release *****

Distributor ID:    Ubuntu
Description:    Ubuntu 12.04.3 LTS
Release:    12.04
Codename:    precise

***** lspci *****

02:00.0 Network controller [0280]: Ralink corp. RT5390 Wireless 802.11n 1T/1R PCIe [1814:5390]
    Subsystem: Foxconn International, Inc. Device [105b:e054]
    Kernel driver in use: rt2800pci
--
03:00.0 Ethernet controller [0200]: Qualcomm Atheros AR8161 Gigabit Ethernet [1969:1091] (rev 10)
    Subsystem: ASUSTeK Computer Inc. Device [1043:14c7]
    Kernel driver in use: alx

***** lsusb *****

Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 003 Device 005: ID 0b05:4c92 ASUSTek Computer, Inc. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 003: ID 1bcf:2883 Sunplus Innovation Technology Inc. 

***** PCMCIA Card Info *****


***** iwconfig *****

wlan0     IEEE 802.11bgn  ESSID:"o2-WLAN09"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: <MAC address removed>   
          Bit Rate=39 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=51/70  Signal level=-59 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:1  Invalid misc:10   Missed beacon:0


***** rfkill *****

0: asus-wlan: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

***** lsmod *****

rt5390sta            1451810  0 
rt2800pci              18754  0 
rt2800lib              67481  1 rt2800pci
crc_ccitt              12707  1 rt2800lib
rt2x00pci              14621  1 rt2800pci
rt2x00lib              55559  3 rt2800pci,rt2800lib,rt2x00pci
mac80211              630977  3 rt2800lib,rt2x00pci,rt2x00lib
cfg80211              525326  2 rt2x00lib,mac80211
eeprom_93cx6           13344  1 rt2800pci

***** nm-tool *****

NetworkManager Tool

State: connected (global)

- Device: usb0  [Connessione via cavo 1] ---------------------------------------
  Type:              Wired
  Driver:            rndis_host
  State:             connected
  Default:           yes
  HW Address:        <MAC address removed>

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.42.190
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.42.129

    DNS:             192.168.42.129


- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            alx
  State:             unavailable
  Default:           no
  HW Address:        <MAC address removed>

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off


- Device: wlan0  [o2-WLAN09] ---------------------------------------------------
  Type:              802.11 WiFi
  Driver:            rt2800pci
  State:             connected
  Default:           no
  HW Address:        <MAC address removed>

  Capabilities:
    Speed:           39 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    FRITZ!Box 7362 SL: Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 52 WPA2
    Schranktuerwand: Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 42 WPA WPA2
    Apple Network b74be0: Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 42 WPA WPA2
    my:              Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 15 WPA WPA2
    The Great Gatsby 2: Infra, <MAC address removed>, Freq 2422 MHz, Rate 54 Mb/s, Strength 15 WEP
    SEDA-PC_Network: Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 19
    *o2-WLAN09:      Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 57 WPA2
    slunce:          Infra, <MAC address removed>, Freq 2422 MHz, Rate 54 Mb/s, Strength 19 WPA WPA2
    Apple Network b74be0: Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 19 WPA WPA2
    HITRON-DD40:     Infra, <MAC address removed>, Freq 2467 MHz, Rate 54 Mb/s, Strength 5 WPA WPA2
    FRITZ!Box WLAN 3370: Infra, <MAC address removed>, Freq 2427 MHz, Rate 54 Mb/s, Strength 9 WPA2
    in the house:    Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 9 WPA WPA2
    Apple Network b74be0: Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 5 WPA WPA2

  IPv4 Settings:
    Address:         192.168.1.5
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1

    DNS:             192.168.1.1



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

no-auto-default=<MAC address removed>,30:85:A9:2E:0F:F0,

[ifupdown]
managed=false

***** interfaces *****

auto lo
iface lo inet loopback


***** iwlist *****

wlan0     Scan completed :
          Cell 01 - Address: <MAC address removed>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=45/70  Signal level=-65 dBm  
                    Encryption key:on
                    ESSID:"o2-WLAN09"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000156e783b16c
                    Extra: Last beacon: 460ms ago
                    IE: Unknown: 00096F322D574C414E3039
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 030101
                    IE: Unknown: 2A0104
                    IE: Unknown: 32040C183060
                    IE: Unknown: 2D1A6E1017FFFF000001000000000000000000000000000000000000
                    IE: Unknown: 3D1601050600000000000000000000000000000000000000
                    IE: Unknown: 3E0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                       Preauthentication Supported
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: 0B0500020B7A12
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F0101
                    IE: Unknown: DD8D0050F204104A00011010440001021041000100103B00010310470010000000000000000300008803550D4366102100066F3220426F781023000941525637353244505710240007312E30312E32331042000A333034333031373730391054000800060050F20400011011001B6F3220426F7820576972656C65737320526F757465722857464129100800020084
                    IE: Unknown: 0706444520010D10
                    IE: Unknown: DD1E00904C336E1017FFFF000001000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C3401050600000000000000000000000000000000000000
          Cell 02 - Address: <MAC address removed>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=37/70  Signal level=-73 dBm  
                    Encryption key:on
                    ESSID:"FRITZ!Box 7362 SL"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000b2daa541c3
                    Extra: Last beacon: 480ms ago
                    IE: Unknown: 0011465249545A21426F78203733363220534C
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030101
                    IE: Unknown: 050400010000
                    IE: Unknown: 0706444520010D14
                    IE: Unknown: 2A0102
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32043048606C
                    IE: Unknown: 2D1AEF111BFFFFFF00000000000000000000000000000406E6E70D00
                    IE: Unknown: 3D1601051100000000000000000000000000000000000000
                    IE: Unknown: DD180050F2020101010003A4000027A4000042435E0062322F00
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: Unknown: DD0C00040E010102010000000000
                    IE: Unknown: DD270050F204104A0001101044000102104700102CF634386FB1071721510896D7071E10103C000103
          Cell 03 - Address: <MAC address removed>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=25/70  Signal level=-85 dBm  
                    Encryption key:off
                    ESSID:"SEDA-PC_Network"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000008cffc85147
                    Extra: Last beacon: 796ms ago
                    IE: Unknown: 000F534544412D50435F4E6574776F726B
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 030106
                    IE: Unknown: 32040C183060
                    IE: Unknown: 0706474220010D10
                    IE: Unknown: 33082001020304050607
                    IE: Unknown: 33082105060708090A0B
                    IE: Unknown: DD050050F20500
                    IE: Unknown: DD0E0050F204104A0001101044000102
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0100
                    IE: Unknown: 2D1AEE1117FFFF0000010000000000000000000000000C0000000000
                    IE: Unknown: 3D1606070700000000000000000000000000000000000000
                    IE: Unknown: 7F0101
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: 0B0506002C127A
                    IE: Unknown: DD1E00904C33EE1117FFFF0000010000000000000000000000000C0000000000
                    IE: Unknown: DD1A00904C3406070700000000000000000000000000000000000000
                    IE: Unknown: DD07000C4307000000
          Cell 04 - Address: <MAC address removed>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=31/70  Signal level=-79 dBm  
                    Encryption key:on
                    ESSID:"Apple Network b74be0"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000015e01db5f7e
                    Extra: Last beacon: 68ms ago
                    IE: Unknown: 00144170706C65204E6574776F726B20623734626530
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 03010B
                    IE: Unknown: 0706444520010D1E
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 2D1A2C4017FFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3302510B
                    IE: Unknown: 3D160B000400000000000000000000000000000000000000
                    IE: Unknown: 46050200010000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101050003A4000027A4000042435E0062322F00
                    IE: Unknown: DD07000393016A0320
                    IE: Unknown: DD0E0017F207000101060021E9B74BE0
                    IE: Unknown: DD0B0017F20100010100000007
          Cell 05 - Address: <MAC address removed>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=29/70  Signal level=-81 dBm  
                    Encryption key:on
                    ESSID:"Schranktuerwand"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000980be2d50f
                    Extra: Last beacon: 68ms ago
                    IE: Unknown: 000F53636872616E6B7475657277616E64
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0100
                    IE: Unknown: 32040C183060
                    IE: Unknown: 2D1AEE1117FFFF0000010000000000000000000000000C0000000000
                    IE: Unknown: 3D160B000600000000000000000000000000000000000000
                    IE: Unknown: 3E0100
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: 7F0101
                    IE: Unknown: DD07000C4307000000
                    IE: Unknown: 0706474220010D10
                    IE: Unknown: DD1E00904C33EE1117FFFF0000010000000000000000000000000C0000000000
                    IE: Unknown: DD1A00904C340B000600000000000000000000000000000000000000
                    IE: Unknown: DD050050F20500
                    IE: Unknown: DD750050F204104A00011010440001021041000100103B000103104700107414147BF659369F798F340804C11EBC10210006442D4C696E6B102300074449522D363135102400074449522D3631351042000830303030303030301054000800060050F2040001101100074449522D363135100800020086


***** resolv.conf *****

nameserver 127.0.0.1
search localdomain

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
blacklist rt2x00usb
blacklist rt2860sta
blacklist rt3090sta

***** modinfo *****

filename:       /lib/modules/3.8.0-34-generic/kernel/drivers/net/wireless/rt5390sta.ko
version:        2.6.0.0
srcversion:     D3FCF2F656E3CA98D53C20C
alias:          pci:v00001186d00003C05sv*sd*bc*sc*i*
alias:          pci:v00001814d00005362sv*sd*bc*sc*i*
alias:          pci:v00001814d00005392sv*sd*bc*sc*i*
alias:          pci:v00001814d0000539Fsv*sd*bc*sc*i*
alias:          pci:v00001814d00005390sv*sd*bc*sc*i*
alias:          pci:v00001814d00003390sv*sd*bc*sc*i*
alias:          pci:v00001814d00003092sv*sd*bc*sc*i*
alias:          pci:v00001814d00003091sv*sd*bc*sc*i*
alias:          pci:v00001814d00003090sv*sd*bc*sc*i*
depends:        
vermagic:       3.8.0-34-generic SMP mod_unload modversions 
parm:           mac:rt28xx: wireless mac addr (charp)

filename:       /lib/modules/3.8.0-34-generic/kernel/drivers/net/wireless/rt2x00/rt2800pci.ko
license:        GPL
firmware:       rt2860.bin
description:    Ralink RT2800 PCI & PCMCIA Wireless LAN driver.
version:        2.3.0
author:         http://rt2x00.serialmonkey.com
srcversion:     A40A95D1558A66562B223A2
alias:          pci:v00001814d0000539Fsv*sd*bc*sc*i*
alias:          pci:v00001814d0000539Bsv*sd*bc*sc*i*
alias:          pci:v00001814d0000539Asv*sd*bc*sc*i*
alias:          pci:v00001814d00005392sv*sd*bc*sc*i*
alias:          pci:v00001814d00005390sv*sd*bc*sc*i*
alias:          pci:v00001814d00005362sv*sd*bc*sc*i*
alias:          pci:v00001814d00005360sv*sd*bc*sc*i*
alias:          pci:v00001814d00003593sv*sd*bc*sc*i*
alias:          pci:v00001814d00003592sv*sd*bc*sc*i*
alias:          pci:v00001814d00003562sv*sd*bc*sc*i*
alias:          pci:v00001814d00003062sv*sd*bc*sc*i*
alias:          pci:v00001814d00003060sv*sd*bc*sc*i*
alias:          pci:v00001432d00007722sv*sd*bc*sc*i*
alias:          pci:v00001432d00007711sv*sd*bc*sc*i*
alias:          pci:v00001814d00003390sv*sd*bc*sc*i*
alias:          pci:v00001814d00003290sv*sd*bc*sc*i*
alias:          pci:v00001A3Bd00001059sv*sd*bc*sc*i*
alias:          pci:v00001462d0000891Asv*sd*bc*sc*i*
alias:          pci:v00001432d00007768sv*sd*bc*sc*i*
alias:          pci:v00001432d00007758sv*sd*bc*sc*i*
alias:          pci:v00001432d00007748sv*sd*bc*sc*i*
alias:          pci:v00001432d00007738sv*sd*bc*sc*i*
alias:          pci:v00001432d00007728sv*sd*bc*sc*i*
alias:          pci:v00001432d00007727sv*sd*bc*sc*i*
alias:          pci:v00001432d00007708sv*sd*bc*sc*i*
alias:          pci:v00001814d00003092sv*sd*bc*sc*i*
alias:          pci:v00001814d00003091sv*sd*bc*sc*i*
alias:          pci:v00001814d00003090sv*sd*bc*sc*i*
alias:          pci:v00001814d00000781sv*sd*bc*sc*i*
alias:          pci:v00001814d00000701sv*sd*bc*sc*i*
alias:          pci:v00001814d00000681sv*sd*bc*sc*i*
alias:          pci:v00001814d00000601sv*sd*bc*sc*i*
depends:        rt2x00lib,rt2800lib,rt2x00pci,eeprom_93cx6
intree:         Y
vermagic:       3.8.0-34-generic SMP mod_unload modversions 
parm:           nohwcrypt:Disable hardware encryption. (bool)

filename:       /lib/modules/3.8.0-34-generic/kernel/drivers/net/wireless/rt2x00/rt2800lib.ko
license:        GPL
description:    Ralink RT2800 library
version:        2.3.0
author:         http://rt2x00.serialmonkey.com, Bartlomiej Zolnierkiewicz
srcversion:     B68330971444C000132AEFA
depends:        rt2x00lib,mac80211,crc-ccitt
intree:         Y
vermagic:       3.8.0-34-generic SMP mod_unload modversions 

filename:       /lib/modules/3.8.0-34-generic/kernel/drivers/net/wireless/rt2x00/rt2x00pci.ko
license:        GPL
description:    rt2x00 pci library
version:        2.3.0
author:         http://rt2x00.serialmonkey.com
srcversion:     4C55FBC01E873875F9583CA
depends:        rt2x00lib,mac80211
intree:         Y
vermagic:       3.8.0-34-generic SMP mod_unload modversions 

filename:       /lib/modules/3.8.0-34-generic/kernel/drivers/net/wireless/rt2x00/rt2x00lib.ko
license:        GPL
description:    rt2x00 library
version:        2.3.0
author:         http://rt2x00.serialmonkey.com
srcversion:     101F39DDF5F96BC8EA5BF21
depends:        mac80211,cfg80211
intree:         Y
vermagic:       3.8.0-34-generic SMP mod_unload modversions 


***** udev rules *****

# PCI device 0x1969:/sys/devices/pci0000:00/0000:00:1c.3/0000:03:00.0 (alx)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

# PCI device 0x1814:/sys/devices/pci0000:00/0000:00:1c.1/0000:02:00.0 (rt2800pci)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

***** dmesg *****

[   14.124695] psmouse serio4: elantech: assuming hardware version 4 (with firmware version 0x361f03)
[   15.002972] rt5390sta: module license 'unspecified' taints kernel.
[   25.035863] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   25.036067] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   28.511319] wlan0: authenticate with <MAC address removed>
[   28.528093] wlan0: send auth to <MAC address removed> (try 1/3)
[   28.529488] wlan0: authenticated
[   28.530274] wlan0: associate with <MAC address removed> (try 1/3)
[   28.573793] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=3)
[   28.573880] wlan0: associated
[   28.573890] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   77.486210] wlan0: deauthenticated from <MAC address removed> (Reason: 3)
[   78.699850] wlan0: authenticate with <MAC address removed>
[   78.715730] wlan0: send auth to <MAC address removed> (try 1/3)
[   78.717900] wlan0: authenticated
[   78.719497] wlan0: associate with <MAC address removed> (try 1/3)
[   78.747121] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=3)
[   78.747212] wlan0: associated
[   97.578636] wlan0: deauthenticated from <MAC address removed> (Reason: 3)
[   98.794152] wlan0: authenticate with <MAC address removed>
[   98.809973] wlan0: send auth to <MAC address removed> (try 1/3)
[   98.811351] wlan0: authenticated
[   98.813589] wlan0: associate with <MAC address removed> (try 1/3)
[   98.860539] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=3)
[   98.860637] wlan0: associated
[  459.450961] wlan0: deauthenticated from <MAC address removed> (Reason: 3)
[  460.676111] wlan0: authenticate with <MAC address removed>
[  460.691593] wlan0: send auth to <MAC address removed> (try 1/3)
[  460.693220] wlan0: authenticated
[  460.694997] wlan0: associate with <MAC address removed> (try 1/3)
[  460.751922] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=3)
[  460.752024] wlan0: associated
[  501.688948] wlan0: deauthenticated from <MAC address removed> (Reason: 3)
[  502.897184] wlan0: authenticate with <MAC address removed>
[  502.912290] wlan0: send auth to <MAC address removed> (try 1/3)
[  502.913654] wlan0: authenticated
[  502.916164] wlan0: associate with <MAC address removed> (try 1/3)
[  502.943829] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=3)
[  502.943914] wlan0: associated
[  544.919669] wlan0: deauthenticated from <MAC address removed> (Reason: 3)
[  546.128768] wlan0: authenticate with <MAC address removed>
[  546.144210] wlan0: send auth to <MAC address removed> (try 1/3)
[  546.145607] wlan0: authenticated
[  546.147755] wlan0: associate with <MAC address removed> (try 1/3)
[  546.175409] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=3)
[  546.175494] wlan0: associated

****************** done ******************

```

and here what I get from other codes I'll find surfing around (I think they are superfluous, aren't they?)

```
makkekkazzo@fra:~$ lspci -nnk
00:00.0 Host bridge [0600]: Intel Corporation 3rd Gen Core processor DRAM Controller [8086:0154] (rev 09)
    Subsystem: ASUSTeK Computer Inc. Device [1043:14c7]
00:02.0 VGA compatible controller [0300]: Intel Corporation 3rd Gen Core processor Graphics Controller [8086:0156] (rev 09)
    Subsystem: ASUSTeK Computer Inc. Device [1043:14c7]
    Kernel driver in use: i915
    Kernel modules: i915
00:14.0 USB controller [0c03]: Intel Corporation 7 Series/C210 Series Chipset Family USB xHCI Host Controller [8086:1e31] (rev 04)
    Subsystem: ASUSTeK Computer Inc. Device [1043:14c7]
    Kernel driver in use: xhci_hcd
00:16.0 Communication controller [0780]: Intel Corporation 7 Series/C210 Series Chipset Family MEI Controller #1 [8086:1e3a] (rev 04)
    Subsystem: ASUSTeK Computer Inc. Device [1043:14c7]
    Kernel driver in use: mei
    Kernel modules: mei
00:1a.0 USB controller [0c03]: Intel Corporation 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #2 [8086:1e2d] (rev 04)
    Subsystem: ASUSTeK Computer Inc. Device [1043:14c7]
    Kernel driver in use: ehci-pci
00:1b.0 Audio device [0403]: Intel Corporation 7 Series/C210 Series Chipset Family High Definition Audio Controller [8086:1e20] (rev 04)
    Subsystem: ASUSTeK Computer Inc. Device [1043:1c33]
    Kernel driver in use: snd_hda_intel
    Kernel modules: snd-hda-intel
00:1c.0 PCI bridge [0604]: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 1 [8086:1e10] (rev c4)
    Kernel driver in use: pcieport
    Kernel modules: shpchp
00:1c.1 PCI bridge [0604]: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 2 [8086:1e12] (rev c4)
    Kernel driver in use: pcieport
    Kernel modules: shpchp
00:1c.3 PCI bridge [0604]: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 4 [8086:1e16] (rev c4)
    Kernel driver in use: pcieport
    Kernel modules: shpchp
00:1d.0 USB controller [0c03]: Intel Corporation 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #1 [8086:1e26] (rev 04)
    Subsystem: ASUSTeK Computer Inc. Device [1043:14c7]
    Kernel driver in use: ehci-pci
00:1f.0 ISA bridge [0601]: Intel Corporation 7 Series Chipset Family LPC Controller [8086:1e5e] (rev 04)
    Subsystem: ASUSTeK Computer Inc. Device [1043:14c7]
    Kernel driver in use: lpc_ich
    Kernel modules: lpc_ich
00:1f.2 SATA controller [0106]: Intel Corporation 7 Series Chipset Family 6-port SATA Controller [AHCI mode] [8086:1e03] (rev 04)
    Subsystem: ASUSTeK Computer Inc. Device [1043:14c7]
    Kernel driver in use: ahci
    Kernel modules: ahci
00:1f.3 SMBus [0c05]: Intel Corporation 7 Series/C210 Series Chipset Family SMBus Controller [8086:1e22] (rev 04)
    Subsystem: ASUSTeK Computer Inc. Device [1043:14c7]
    Kernel modules: i2c-i801
02:00.0 Network controller [0280]: Ralink corp. RT5390 Wireless 802.11n 1T/1R PCIe [1814:5390]
    Subsystem: Foxconn International, Inc. Device [105b:e054]
    Kernel driver in use: rt2800pci
    Kernel modules: rt5390sta, rt2800pci
03:00.0 Ethernet controller [0200]: Qualcomm Atheros AR8161 Gigabit Ethernet [1969:1091] (rev 10)
    Subsystem: ASUSTeK Computer Inc. Device [1043:14c7]
    Kernel driver in use: alx
    Kernel modules: alx
makkekkazzo@fra:~$ ifconfig wlan0
wlan0     Link encap:Ethernet  IndirizzoHW 08:3e:8e:0b:9e:8e  
          indirizzo inet:192.168.1.5  Bcast:192.168.1.255  Maschera:255.255.255.0
          indirizzo inet6: fe80::a3e:8eff:fe0b:9e8e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:494664 errors:0 dropped:0 overruns:0 frame:0
          TX packets:291576 errors:0 dropped:0 overruns:0 carrier:0
          collisioni:0 txqueuelen:1000 
          Byte RX:707994049 (707.9 MB)  Byte TX:30415768 (30.4 MB)

makkekkazzo@fra:~$ iwconfig wlan0
wlan0     IEEE 802.11bgn  ESSID:"o2-WLAN09"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 88:03:55:0D:43:67   
          Bit Rate=21.7 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=43/70  Signal level=-67 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

makkekkazzo@fra:~$ sudo lshw -short -C network
[sudo] password for makkekkazzo: 
Sorry, try again.
[sudo] password for makkekkazzo: 
H/W path       Device      Class          Description
=====================================================
/0/100/1c.1/0  wlan0       network        RT5390 Wireless 802.11n 1T/1R PCIe
/0/100/1c.3/0  eth0        network        AR8161 Gigabit Ethernet
makkekkazzo@fra:~$ lspci -nnk | grep -iA2 net
02:00.0 Network controller [0280]: Ralink corp. RT5390 Wireless 802.11n 1T/1R PCIe [1814:5390]
    Subsystem: Foxconn International, Inc. Device [105b:e054]
    Kernel driver in use: rt2800pci
--
03:00.0 Ethernet controller [0200]: Qualcomm Atheros AR8161 Gigabit Ethernet [1969:1091] (rev 10)
    Subsystem: ASUSTeK Computer Inc. Device [1043:14c7]
    Kernel driver in use: alx
makkekkazzo@fra:~$ nm-tool

NetworkManager Tool

State: connected (global)

- Device: wlan0  [o2-WLAN09] ---------------------------------------------------
  Type:              802.11 WiFi
  Driver:            rt2800pci
  State:             connected
  Default:           yes
  HW Address:        08:3E:8E:0B:9E:8E

  Capabilities:
    Speed:           1 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    Schranktuerwand: Infra, 34:08:04:C1:1E:BC, Freq 2462 MHz, Rate 54 Mb/s, Strength 42 WPA WPA2
    Apple Network b74be0: Infra, 00:21:E9:B7:4B:E0, Freq 2462 MHz, Rate 54 Mb/s, Strength 42 WPA WPA2
    Apple Network b74be0: Infra, 00:25:4B:09:B2:9B, Freq 2462 MHz, Rate 54 Mb/s, Strength 15 WPA WPA2
    my:              Infra, 00:18:E7:FD:7A:C6, Freq 2437 MHz, Rate 54 Mb/s, Strength 9 WPA WPA2
    ALICE-WLAN98:    Infra, 00:1C:28:67:0B:F7, Freq 2442 MHz, Rate 54 Mb/s, Strength 9 WPA2
    The Great Gatsby 2: Infra, 34:08:04:25:EF:8C, Freq 2422 MHz, Rate 54 Mb/s, Strength 22 WEP
    SEDA-PC_Network: Infra, 00:24:01:FB:32:6E, Freq 2437 MHz, Rate 54 Mb/s, Strength 29
    *o2-WLAN09:      Infra, 88:03:55:0D:43:67, Freq 2412 MHz, Rate 54 Mb/s, Strength 47 WPA2
    FRITZ!Box 7362 SL: Infra, 08:96:D7:07:1E:F8, Freq 2412 MHz, Rate 54 Mb/s, Strength 52 WPA2
    HITRON-DD40:     Infra, BC:14:01:88:DD:48, Freq 2467 MHz, Rate 54 Mb/s, Strength 9 WPA WPA2
    in the house:    Infra, F0:7D:68:53:2E:CC, Freq 2437 MHz, Rate 54 Mb/s, Strength 15 WPA WPA2

  IPv4 Settings:
    Address:         192.168.1.5
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1

    DNS:             192.168.1.1


- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            alx
  State:             unavailable
  Default:           no
  HW Address:        30:85:A9:2E:0F:F0

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off

makkekkazzo@fra:~$ route
Tabella di routing IP del kernel
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
default         192.168.1.1     0.0.0.0         UG    0      0        0 wlan0
link-local      *               255.255.0.0     U     1000   0        0 wlan0
192.168.1.0     *               255.255.255.0   U     2      0        0 wlan0


```

Does anybody could say to me what is happening here?

Thanks

---

### Post by wildmanne39 on 2013-12-28
Please try:
```
sudo modprobe -rv rt2800pci
sudo modprobe -rv rt5390sta
sudo modprobe rt5390sta
```
Thanks

---

### Post by makkekkazzo on 2013-12-28
It didn't work

---

### Post by makkekkazzo on 2013-12-28
In a similar thread they posted these others codes.


```
makkekkazzo@fra:~$  ifconfig
eth0      Link encap:Ethernet  IndirizzoHW 30:85:a9:2e:0f:f0  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisioni:0 txqueuelen:1000 
          Byte RX:0 (0.0 B)  Byte TX:0 (0.0 B)
          Interrupt:19 

lo        Link encap:Loopback locale  
          indirizzo inet:127.0.0.1  Maschera:255.0.0.0
          indirizzo inet6: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:1290 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1290 errors:0 dropped:0 overruns:0 carrier:0
          collisioni:0 txqueuelen:0 
          Byte RX:116060 (116.0 KB)  Byte TX:116060 (116.0 KB)

wlan0     Link encap:Ethernet  IndirizzoHW 08:3e:8e:0b:9e:8e  
          indirizzo inet:192.168.1.5  Bcast:192.168.1.255  Maschera:255.255.255.0
          indirizzo inet6: fe80::a3e:8eff:fe0b:9e8e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:417 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1106 errors:0 dropped:0 overruns:0 carrier:0
          collisioni:0 txqueuelen:1000 
          Byte RX:51939 (51.9 KB)  Byte TX:125746 (125.7 KB)

makkekkazzo@fra:~$ sudo route -n
[sudo] password for makkekkazzo: 
Tabella di routing IP del kernel
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 wlan0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 wlan0
192.168.1.0     0.0.0.0         255.255.255.0   U     2      0        0 wlan0

makkekkazzo@fra:~$ cat /etc/resolv.conf
# Dynamic resolv.conf(5) file for glibc resolver(3) generated by resolvconf(8)
#     DO NOT EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN
nameserver 127.0.0.1
search localdomain

makkekkazzo@fra:~$  nm-tool | grep DNS
    DNS:             192.168.1.1

makkekkazzo@fra:~$  cat /etc/modprobe.d/iwlwifi.conf
cat: /etc/modprobe.d/iwlwifi.conf: File o directory non esistente

makkekkazzo@fra:~$ mtr -nrc2 8.8.8.8
HOST: fra                         Loss%   Snt   Last   Avg  Best  Wrst StDev

makkekkazzo@fra:~$ ip route show
default via 192.168.1.1 dev wlan0  proto static 
169.254.0.0/16 dev wlan0  scope link  metric 1000 
192.168.1.0/24 dev wlan0  proto kernel  scope link  src 192.168.1.5  metric 2 


```

And trying "ping 192.168.1.1" the rectangle blinks without any output. 

The network works very good with the others devices (other laptops, mobile phone and tablet, connecting through it for posting these)

---

### Post by wildmanne39 on 2013-12-28
Please try:
```
sudo modprobe -rv rt2800pci
sudo modprobe -rv rt5390sta
sudo modprobe rt2800pci nohwcrypt=1
```
if this works we will make it permanent, please do not reboot.
Thanks

---

### Post by makkekkazzo on 2013-12-28
Really thank you for your help, but unfortunately doesn't work.

---

