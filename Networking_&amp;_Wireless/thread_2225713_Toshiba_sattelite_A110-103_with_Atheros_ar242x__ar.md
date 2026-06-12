---
title: "Toshiba sattelite A110-103 with Atheros ar242x / ar542x wifi card problem connecting"
date: 2014-05-22
forum: Networking &amp; Wireless
---

### Post by sander5 on 2014-05-22
Hi all,

I'm trying to get this old laptop to run Ubuntu. It installed just fine and i can ' see' my wireless network. Any if i try to connect to them it does not work.
The card has AR5BB61 / PA3501u-1MPC printed on it

I did some lookig around and tried some of the solutions offered but none worked yet. I found this wifi troubleshoting script though, output below this message.
It seems to indicate an authentication error but i triple checked the passwords so that can't be it.
Hope someone can shine some light on this problem. Thanks in advance for your time.


########## wireless info START ##########

##### release #####

Distributor ID:    Ubuntu
Description:    Ubuntu 14.04 LTS
Release:    14.04
Codename:    trusty

##### kernel #####

Linux Satellite-A110 3.13.0-24-generic #47-Ubuntu SMP Fri May 2 23:31:42 UTC 2014 i686 i686 i686 GNU/Linux

##### arch #####

i686

##### lspci #####

02:00.0 Ethernet controller [0200]: Qualcomm Atheros AR242x / AR542x Wireless Network Adapter (PCI-Express) [168c:001c] (rev 01)
    Subsystem: Askey Computer Corp. WLL3140 (Toshiba PA3501U-1MPC) 802.11bg Wireless Mini PCIe Card [144f:7106]
    Kernel driver in use: ath5k

09:06.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL-8100/8101L/8139 PCI Fast Ethernet Adapter [10ec:8139] (rev 10)
    Subsystem: Toshiba America Info Systems Device [1179:ff00]
    Kernel driver in use: 8139too

##### lsusb #####

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

##### PCMCIA Card Info #####

PRODID_1=""
PRODID_2=""
PRODID_3=""
PRODID_4=""
MANFID=0000,0000
FUNCID=255

##### rfkill #####

0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

##### iw reg get #####

country 00:
    (2402 - 2472 @ 40), (3, 20)
    (2457 - 2482 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (2474 - 2494 @ 20), (3, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
    (5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS

##### interfaces #####

# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback

##### iwconfig #####

wlan0     IEEE 802.11bg  ESSIDoff/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS throff   Fragment thoff
          Power Management off
          
  
##### route #####

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         10.14.1.1       0.0.0.0         UG    0      0        0 eth0
10.14.1.0       0.0.0.0         255.255.255.0   U     1      0        0 eth0

##### resolv.conf #####

nameserver 127.0.1.1

##### nm-tool #####

NetworkManager Tool

State: connected (global)

- Device: eth0  [Wired connection 1] -------------------------------------------
  Type:              Wired
  Driver:            8139too
  State:             connected
  Default:           yes
  HW Address:        <MAC address removed>

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         10.14.1.101
    Prefix:          24 (255.255.255.0)
    Gateway:         10.14.1.1

    DNS:             212.54.35.25
    DNS:             212.54.40.25

- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            ath5k
  State:             disconnected
  Default:           no
  HW Address:        <MAC address removed>

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 
    Avalon-Guest:    Infra, <MAC address removed>, Freq 2457 MHz, Rate 54 Mb/s, Strength 99 WPA2
    Avalon:          Infra, <MAC address removed>, Freq 2457 MHz, Rate 54 Mb/s, Strength 99 WPA2

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
                    Channel:10
                    Frequency:2.457 GHz (Channel 10)
                    Quality=67/70  Signal level=-43 dBm  
                    Encryption key:on
                    ESSID:"Avalon-Guest"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000008f30ea585d
                    Extra: Last beacon: 140ms ago
                    IE: Unknown: 000C4176616C6F6E2D4775657374
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 03010A
                    IE: Unknown: 050400030000
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1AFF191BFFFFFF0001000000000000000000000000000000000000
                    IE: Unknown: 3D160A0F0000000000000000000000000000000000000000
                    IE: Unknown: DD090010180200F03C0000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 02 - Address: <MAC address removed>
                    Channel:10
                    Frequency:2.457 GHz (Channel 10)
                    Quality=65/70  Signal level=-45 dBm  
                    Encryption key:on
                    ESSID:"Avalon"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000008f30e8c19b
                    Extra: Last beacon: 244ms ago
                    IE: Unknown: 00064176616C6F6E
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 03010A
                    IE: Unknown: 050401030000
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1AFF191BFFFFFF0001000000000000000000000000000000000000
                    IE: Unknown: 3D160A0F1600000000000000000000000000000000000000
                    IE: Unknown: DD090010180201F03C0000
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

##### lsmod #####

ath5k                 134977  0 
ath                    23922  1 ath5k
mac80211              545990  1 ath5k
cfg80211              409394  3 ath,ath5k,mac80211

##### modinfo #####

filename:       /lib/modules/3.13.0-24-generic/kernel/drivers/net/wireless/ath/ath5k/ath5k.ko
license:        Dual BSD/GPL
description:    Support for 5xxx series of Atheros 802.11 wireless LAN cards.
author:         Nick Kossifidis
author:         Jiri Slaby
srcversion:     F36818A2F0BCB2B0CC9BB8C
alias:          pci:v0000168Cd0000FF1Bsv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000001Dsv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000001Csv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000001Bsv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000001Asv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000019sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000018sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000017sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000016sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000015sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000014sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00001014sv*sd*bc*sc*i*
alias:          pci:v000010B7d00000013sv*sd*bc*sc*i*
alias:          pci:v0000A727d00000013sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000013sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000012sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000011sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000007sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000207sv*sd*bc*sc*i*
depends:        mac80211,cfg80211,ath
intree:         Y
vermagic:       3.13.0-24-generic SMP mod_unload modversions 686 
signer:         Magrathea: Glacier signing key
sig_key:        <MAC address removed>:A1:7E:EF:58:C6:AC:5E:9A:85:71:2C:92:08:DF
sig_hashalgo:   sha512
parm:           nohwcrypt:Disable hardware encryption. (bool)
parm:           fastchanswitch:Enable fast channel switching for AR2413/AR5413 radios. (bool)
parm:           no_hw_rfkill_switch:Ignore the GPIO RFKill switch state (bool)

filename:       /lib/modules/3.13.0-24-generic/kernel/drivers/net/wireless/ath/ath.ko
license:        Dual BSD/GPL
description:    Shared library for Atheros wireless LAN cards.
author:         Atheros Communications
srcversion:     88A67C5359B02C5A710AFCF
depends:        cfg80211
intree:         Y
vermagic:       3.13.0-24-generic SMP mod_unload modversions 686 
signer:         Magrathea: Glacier signing key
sig_key:        <MAC address removed>:A1:7E:EF:58:C6:AC:5E:9A:85:71:2C:92:08:DF
sig_hashalgo:   sha512

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
blacklist acer_wmi

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

# PCI device 0x10ec:0x8139 (8139too)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

# PCI device 0x168c:0x001c (ath5k)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

##### dmesg #####

[   12.954285] ath5k 0000:02:00.0: can't disable ASPM; OS doesn't have ASPM control
[   12.954510] ath5k 0000:02:00.0: registered as 'phy0'
[   14.483498] ath: EEPROM regdomain: 0x64
[   14.483504] ath: EEPROM indicates we should expect a direct regpair map
[   14.483509] ath: Country alpha2 being used: 00
[   14.483511] ath: Regpair used: 0x64
[   14.667854] ath5k: phy0: Atheros AR5414 chip found (MAC: 0xa0, PHY: 0x61)
[   22.242025] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   22.242796] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  292.601415] wlan0: authenticate with <MAC address removed>
[  292.610495] wlan0: direct probe to <MAC address removed> (try 1/3)
[  292.812048] wlan0: direct probe to <MAC address removed> (try 2/3)
[  293.016047] wlan0: direct probe to <MAC address removed> (try 3/3)
[  293.220043] wlan0: authentication with <MAC address removed> timed out
[  293.985429] wlan0: authenticate with <MAC address removed>
[  293.990214] wlan0: direct probe to <MAC address removed> (try 1/3)
[  294.192069] wlan0: direct probe to <MAC address removed> (try 2/3)
[  294.396042] wlan0: direct probe to <MAC address removed> (try 3/3)
[  294.600040] wlan0: authentication with <MAC address removed> timed out
[  295.756683] wlan0: authenticate with <MAC address removed>
[  295.762223] wlan0: direct probe to <MAC address removed> (try 1/3)
[  295.964041] wlan0: direct probe to <MAC address removed> (try 2/3)
[  296.168039] wlan0: direct probe to <MAC address removed> (try 3/3)
[  296.372079] wlan0: authentication with <MAC address removed> timed out
[  298.029406] wlan0: authenticate with <MAC address removed>
[  298.034172] wlan0: direct probe to <MAC address removed> (try 1/3)
[  298.236037] wlan0: direct probe to <MAC address removed> (try 2/3)
[  298.440041] wlan0: direct probe to <MAC address removed> (try 3/3)
[  298.644035] wlan0: authentication with <MAC address removed> timed out
[  309.969420] wlan0: authenticate with <MAC address removed>
[  309.974245] wlan0: direct probe to <MAC address removed> (try 1/3)
[  310.176036] wlan0: direct probe to <MAC address removed> (try 2/3)
[  310.380043] wlan0: direct probe to <MAC address removed> (try 3/3)
[  310.584043] wlan0: authentication with <MAC address removed> timed out
[ 2731.397391] wlan0: authenticate with <MAC address removed>
[ 2731.402138] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 2731.605493] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 2731.808050] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 2732.012063] wlan0: authentication with <MAC address removed> timed out
[ 2742.681428] wlan0: authenticate with <MAC address removed>
[ 2742.686227] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 2742.888041] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 2743.092042] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 2743.296035] wlan0: authentication with <MAC address removed> timed out
[ 3065.145415] wlan0: authenticate with <MAC address removed>
[ 3065.150445] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 3065.352059] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 3065.556043] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 3065.760039] wlan0: authentication with <MAC address removed> timed out
[ 3076.421416] wlan0: authenticate with <MAC address removed>
[ 3076.426203] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 3076.628038] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 3076.832042] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 3077.036049] wlan0: authentication with <MAC address removed> timed out

########## wireless info END ############

---

### Post by sander5 on 2014-05-23
Problem seems to be solved, reason unknown..

---

