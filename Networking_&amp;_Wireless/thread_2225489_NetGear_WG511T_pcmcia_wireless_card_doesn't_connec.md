---
title: "NetGear WG511T pcmcia wireless card doesn't connect, Lubuntu 14.04"
date: 2014-05-21
forum: Networking &amp; Wireless
---

### Post by bill41 on 2014-05-21
I'm new to Linux and recently installed Lubuntu 14.04 on an old Toshiba Satellite laptop. When I try to connect to my wireless network using the Manage Networks panel applet and enter the password, nothing happens. Lubuntu is installed in a dual boot setup on the laptop with Windows 7. The NetGear WG511T card connects ok when using Windows 7. The card uses an Atheros chipset.

I followed the instructions from [http://ubuntuforums.org/showthread.php?t=370108](http://ubuntuforums.org/showthread.php?t=370108) , updating my system and running the recommended wireless script to generate wireless-info.txt:

```


########## wireless info START ##########

##### release #####

Distributor ID:    Ubuntu
Description:    Ubuntu 14.04 LTS
Release:    14.04
Codename:    trusty

##### kernel #####

Linux toshiba-a45-s120 3.13.0-24-generic #47-Ubuntu SMP Fri May 2 23:31:42 UTC 2014 i686 i686 i686 GNU/Linux

##### arch #####

i686

##### lspci #####

01:08.0 Ethernet controller [0200]: Intel Corporation 82801DB PRO/100 VE (MOB) Ethernet Controller [8086:103d] (rev 83)
    Subsystem: Toshiba America Info Systems Device [1179:0001]
    Kernel driver in use: e100

02:00.0 Ethernet controller [0200]: Qualcomm Atheros AR5212/AR5213 Wireless Network Adapter [168c:0013] (rev 01)
    Subsystem: Netgear WG511T 108 Mbps Wireless PC Card (rev.C) [1385:5b00]
    Kernel driver in use: ath5k

##### lsusb #####

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

##### PCMCIA Card Info #####

##### rfkill #####

0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

##### iw reg get #####

##### interfaces #####

# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback

##### iwconfig #####

wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=27 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          

##### route #####

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 eth0
192.168.1.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0

##### resolv.conf #####

nameserver 127.0.1.1

##### nm-tool #####

NetworkManager Tool

State: connected (global)

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
    T1tb0fW95:       Infra, <MAC address removed>, Freq 2447 MHz, Rate 54 Mb/s, Strength 95 WPA2
    MTF172:          Infra, <MAC address removed>, Freq 2457 MHz, Rate 54 Mb/s, Strength 50 WPA WPA2
    kublakhan:       Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 27 WPA WPA2
    2WIRE675:        Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 35 WPA WPA2
    WAPLNEK:         Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 17 WPA
    NETGEAR:         Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 27 WPA2
    Connor Network:  Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 17 WPA2
    2WIRE600:        Infra, <MAC address removed>, Freq 2457 MHz, Rate 54 Mb/s, Strength 14 WPA WPA2
    WAPsjb:          Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 12 WPA

- Device: eth0  [Wired connection 1] -------------------------------------------
  Type:              Wired
  Driver:            e100
  State:             connected
  Default:           yes
  HW Address:        <MAC address removed>

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.1.5
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1

    DNS:             192.168.1.1

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
                    Channel:8
                    Frequency:2.447 GHz (Channel 8)
                    Quality=70/70  Signal level=-40 dBm  
                    Encryption key:on
                    ESSID:"T1tb0fW95"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s
                    Bit Rates:9 Mb/s; 18 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000001c3fe7e7d2
                    Extra: Last beacon: 76ms ago
                    IE: Unknown: 0009543174623066573935
                    IE: Unknown: 010882848B960C183048
                    IE: Unknown: 030108
                    IE: Unknown: 2A0100
                    IE: Unknown: 32041224606C
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                       Preauthentication Supported
                    IE: Unknown: DD0900037F0101000EFF7F
                    IE: Unknown: DD1A00037F030100000000146C19722402146C19722464002C010E08
          Cell 02 - Address: <MAC address removed>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=31/70  Signal level=-79 dBm  
                    Encryption key:on
                    ESSID:"2WIRE675"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00001130af08e249
                    Extra: Last beacon: 76ms ago
                    IE: Unknown: 00083257495245363735
                    IE: Unknown: 010882848B0C12961824
                    IE: Unknown: 030101
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
          Cell 03 - Address: <MAC address removed>
                    Channel:10
                    Frequency:2.457 GHz (Channel 10)
                    Quality=41/70  Signal level=-69 dBm  
                    Encryption key:on
                    ESSID:"MTF172"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000007e88c1f0
                    Extra: Last beacon: 76ms ago
                    IE: Unknown: 00064D5446313732
                    IE: Unknown: 010882848B0C12961824
                    IE: Unknown: 03010A
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
          Cell 04 - Address: <MAC address removed>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=29/70  Signal level=-81 dBm  
                    Encryption key:on
                    ESSID:"kublakhan"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000007b86ea58db
                    Extra: Last beacon: 76ms ago
                    IE: Unknown: 00096B75626C616B68616E
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030106
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1A6C181BFF00000000000000000000000000000000000000000000
                    IE: Unknown: 3D1606081100000000000000000000000000000000000000
                    IE: Unknown: DD7F0050F204104A00011010440001021041000100103B0001031047001041551EA310847BDA11FC2F30FD2CA9871021000D4E4554474541522C20496E632E10230009574E5231303030763310240009574E523130303076331042000538333235381054000800060050F204000110110009574E52313030307633100800020084
                    IE: Unknown: DD090010180200F0050000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C336C181BFF00000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C3406081100000000000000000000000000000000000000
          Cell 05 - Address: <MAC address removed>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=18/70  Signal level=-92 dBm  
                    Encryption key:on
                    ESSID:"WAPLNEK"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000013904b973e8b
                    Extra: Last beacon: 76ms ago
                    IE: Unknown: 00075741504C4E454B
                    IE: Unknown: 010882848B0C12961824
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: 851E01008C000F00FF0319006E656B2D7761702D686F6D650000000002000027
                    IE: Unknown: 9606004096001400
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101830003A4000027A4000042435E0062322F00
                    IE: Unknown: DD06004096010100
                    IE: Unknown: DD050040960305
                    IE: Unknown: DD050040960B09
                    IE: Unknown: DD050040961400
          Cell 06 - Address: <MAC address removed>
                    Channel:10
                    Frequency:2.457 GHz (Channel 10)
                    Quality=18/70  Signal level=-92 dBm  
                    Encryption key:on
                    ESSID:"2WIRE600"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000fb831acdd81
                    Extra: Last beacon: 160ms ago
                    IE: Unknown: 00083257495245363030
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 03010A
                    IE: Unknown: 050400010000
                    IE: Unknown: 0706555320010B1B
                    IE: Unknown: 2A0102
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32043048606C

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

[/etc/modprobe.d/libpisock9.conf]
blacklist visor

##### udev rules #####

# PCI device 0x8086:0x103d (e100)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

# PCI device 0x168c:0x0013 (ath5k)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

##### dmesg #####

[   21.696723] ath5k 0000:02:00.0: enabling device (0000 -> 0002)
[   21.696982] ath5k 0000:02:00.0: registered as 'phy0'
[   22.648923] ath: EEPROM regdomain: 0x0
[   22.648933] ath: EEPROM indicates default country code should be used
[   22.648935] ath: doing EEPROM country->regdmn map search
[   22.648939] ath: country maps to regdmn code: 0x3a
[   22.648942] ath: Country alpha2 being used: US
[   22.648944] ath: Regpair used: 0x3a
[   23.080895] ath5k: phy0: Atheros AR2414 chip found (MAC: 0x79, PHY: 0x45)
[   33.614540] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   33.616779] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready

########## wireless info END ############


```

---

### Post by varunendra on 2014-05-22
Welcome to the forums bill41!

Which one of the listed Access Points is yours? The recommended encryption setting for the router/access-point is pure 'WPA2' with AES (CCMP). The recommended channels are 1 and 11 (unless they are already too congested due to many neighbouring APs using same channels). If the settings are different in your router, please try changing them as suggested. Reboot the router after saving the changes.

Apart from above, try a driver parameter in Ubuntu as follows :

Open a terminal (Ctrl-Alt-T) and run the following command in it -
```
echo "options ath5k nohwcrypt=Y" | sudo tee /etc/modprobe.d/ath5k.conf
```
Then either reboot, or manually reload the driver with following commands -
```
sudo modprobe -rv ath5k
sudo modprobe -v ath5k
```

If these don't help, please follow the instructions in this post to download and run 'wireless_script' (new, experimental version, not the one you already posted output of), and post back the report it generates : [http://ubuntuforums.org/showpost.php?p=13024222](http://ubuntuforums.org/showpost.php?p=13024222)

---

### Post by bill41 on 2014-05-22
Thanks Varun. My access point is T1tb0fW95. The encryption was already set to 'WPA2-PSK [AES]', I assume this is pure 'WPA2'. I changed the channel from 8 to 11 (channel 1 was congested) and rebooted the router, but this had no effect.

I ran the command you suggested:

```

echo "options ath5k nohwcrypt=Y" | sudo tee /etc/modprobe.d/ath5k.conf
```

and manually reloaded the driver but still no luck.

Here is the report generated from the new 'wireless_script':

```


    ======== Wireless-Info START ========

System-Info ~~~~~~~~~~~~~~~~~~~~~~~~

toshiba-a45-s120 3.13.0-24-generic i686,  Ubuntu 14.04 LTS, trusty

CPU    : Intel(R) Celeron(R) CPU 2.60GHz
Memory : 1238 MB
Uptime : 12:58:17 up 10 min,  2 users,  load average: 0.12, 0.29, 0.22


lspci ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

01:08.0 Ethernet controller [0200]: Intel Corporation 82801DB PRO/100 VE (MOB) Ethernet Controller [8086:103d] (rev 83)
    Subsystem: Toshiba America Info Systems Device [1179:0001]
    Kernel driver in use: e100
--
02:00.0 Ethernet controller [0200]: Qualcomm Atheros AR5212/AR5213 Wireless Network Adapter [168c:0013] (rev 01)
    Subsystem: Netgear WG511T 108 Mbps Wireless PC Card (rev.C) [1385:5b00]
    Kernel driver in use: ath5k


lsusb ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


PCMCIA Card Info ~~~~~~~~~~~~~~~~~~~



iwconfig ~~~~~~~~~~~~~~~~~~~~~~~~~~~

wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=27 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          


rfkill ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

      Interface        Soft blocked  Hard blocked
0: phy0: Wireless LAN      no            no


lsmod ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

ath5k                 134977  0 
ath                    23922  1 ath5k
mac80211              545990  1 ath5k
cfg80211              409394  3 ath,ath5k,mac80211
wmi                    18673  1 toshiba_acpi


module parameters ~~~~~~~~~~~~~~~~~~

ath5k         (3): fastchanswitch=N | nohwcrypt=Y | no_hw_rfkill_switch=N
cfg80211      (2): cfg80211_disable_40mhz_24ghz=N | ieee80211_regdom=00
mac80211      (5): beacon_loss_count=7 | ieee80211_default_rc_algo=minstrel_ht | max_nullfunc_tries=2 | max_probe_tries=5 | probe_wait_ms=500
wmi           (2): debug_dump_wdg=N | debug_event=N


nm-tool ~~~~~~~~~~~~~~~~~~~~~~~~~~~~

State: connected (global)
============================o=============o========o==============o=========o===========o==============o===========
 Interface & ID             | Type        | Driver | State        | Default | Speed     | Support      | HW Addr   
============================o=============o========o==============o=========o===========o==============o===========
 wlan0                      | 802.11 WiFi | ath5k  | disconnected | no      |           | WEP/WPA/WPA2 | <MAC wlan0>

    T1tb0fW95:       Infra, <MAC C-02 T1tb0fW95>, Freq 2462 MHz, Rate 54 Mb/s, Strength 95 WPA2
    MTF172:          Infra, <MAC C-01 MTF172>, Freq 2457 MHz, Rate 54 Mb/s, Strength 50 WPA WPA2
    kublakhan:       Infra, <MAC C-03 kublakhan>, Freq 2437 MHz, Rate 54 Mb/s, Strength 30 WPA WPA2
    WAPLNEK:         Infra, <MAC C-04 WAPLNEK>, Freq 2462 MHz, Rate 54 Mb/s, Strength 17 WPA
    2WIRE675:        Infra, <MAC C-NA 2WIRE675 1>, Freq 2412 MHz, Rate 54 Mb/s, Strength 22 WPA WPA2
    Connor Network:  Infra, <MAC C-NA Connor Network 1>, Freq 2412 MHz, Rate 54 Mb/s, Strength 24 WPA2
    NETGEAR:         Infra, <MAC C-NA NETGEAR 1>, Freq 2412 MHz, Rate 54 Mb/s, Strength 19 WPA2
    2WIRE817:        Infra, <MAC C-NA 2WIRE817 1>, Freq 2437 MHz, Rate 54 Mb/s, Strength 12 WPA WPA2
    2WIRE600:        Infra, <MAC C-NA 2WIRE600 1>, Freq 2457 MHz, Rate 54 Mb/s, Strength 10 WPA WPA2
----------------------------+-------------+--------+--------------+---------+-----------+--------------+-----------
 eth0  [Wired connection 1] | Wired       | e100   | connected    | yes     | 100 Mb/s  |              | <MAC eth0>

    Address:         192.168.1.3
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1
    DNS:             192.168.1.1
----------------------------+-------------+--------+--------------+---------+-----------+--------------+-----------


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
 


interfaces ~~~~~~~~~~~~~~~~~~~~~~~~~

# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback

resolv.conf ~~~~~~~~~~~~~~~~~~~~~~~~

nameserver 127.0.1.1


Routes & Ping ~~~~~~~~~~~~~~~~~~~~~~

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 eth0
192.168.1.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0

--- 192.168.1.1 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 999ms
rtt min/avg/max/mdev = 0.757/0.820/0.883/0.063 ms

--- 127.0.1.1 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 999ms
rtt min/avg/max/mdev = 0.082/0.082/0.082/0.000 ms


iw reg get ~~~~~~~~~~~~~~~~~~~~~~~~~

(Region : "en_US.UTF-8")


iwlist chan ~~~~~~~~~~~~~~~~~~~~~~~~

wlan0     11 channels in total; available frequencies :
          Channel 01 (2.412 GHz) - 11 (2.462 GHz)


iwlist scan ~~~~~~~~~~~~~~~~~~~~~~~~

wlan0     Scan completed :
          Cell 01 - Address: <MAC C-01 MTF172>
                    Channel:10
                    Frequency:2.457 GHz (Channel 10)
                    Quality=41/70  Signal level=-69 dBm  
                    Encryption key:on
                    ESSID:"MTF172"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000000298378a4
                    Extra: Last beacon: 76ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC C-02 T1tb0fW95>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=64/70  Signal level=-46 dBm  
                    Encryption key:on
                    ESSID:"T1tb0fW95"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s
                    Bit Rates:9 Mb/s; 18 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000006937de84
                    Extra: Last beacon: 76ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                       Preauthentication Supported
          Cell 03 - Address: <MAC C-03 kublakhan>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=30/70  Signal level=-80 dBm  
                    Encryption key:on
                    ESSID:"kublakhan"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000009eacafd618
                    Extra: Last beacon: 76ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 04 - Address: <MAC C-04 WAPLNEK>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=18/70  Signal level=-92 dBm  
                    Encryption key:on
                    ESSID:"WAPLNEK"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000013b37148718c
                    Extra: Last beacon: 132ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK


blacklist ~~~~~~~~~~~~~~~~~~~~~~~~~~

[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci

[/etc/modprobe.d/libpisock9.conf]
blacklist visor


modinfo ~~~~~~~~~~~~~~~~~~~~~~~~~~~~

[ath5k]
filename:       /lib/modules/3.13.0-24-generic/kernel/drivers/net/wireless/ath/ath5k/ath5k.ko
srcversion:     F36818A2F0BCB2B0CC9BB8C
depends:        mac80211,cfg80211,ath
parm:           nohwcrypt:Disable hardware encryption. (bool)
parm:           fastchanswitch:Enable fast channel switching for AR2413/AR5413 radios. (bool)
parm:           no_hw_rfkill_switch:Ignore the GPIO RFKill switch state (bool)

[ath]
filename:       /lib/modules/3.13.0-24-generic/kernel/drivers/net/wireless/ath/ath.ko
srcversion:     88A67C5359B02C5A710AFCF
depends:        cfg80211

[mac80211]
filename:       /lib/modules/3.13.0-24-generic/kernel/net/mac80211/mac80211.ko
srcversion:     C0F95BBF832E05DEFD722F4
depends:        cfg80211
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[cfg80211]
filename:       /lib/modules/3.13.0-24-generic/kernel/net/wireless/cfg80211.ko
srcversion:     8B3D642D1F2E6406EF33F74
depends:        
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)


udev rules ~~~~~~~~~~~~~~~~~~~~~~~~~

# PCI device 0x8086:0x103d (e100)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC eth0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

# PCI device 0x168c:0x0013 (ath5k)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC wlan0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"


Custom files/entries ~~~~~~~~~~~~~~~

/etc/modules        : Default
/etc/rc.local       : Default
/etc/modprobe.d     : Not Default
/etc/pm/(cnf|pw|sl) : Default

[/etc/modprobe.d]
ath5k.conf        : options ath5k nohwcrypt=Y
iwlwifi.conf      : remove iwlwifi \
                    (/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
                    && /sbin/modprobe -r mac80211
mlx4.conf         : softdep mlx4_core post: mlx4_en


Kernel boot line ~~~~~~~~~~~~~~~~~~~

BOOT_IMAGE=/boot/vmlinuz-3.13.0-24-generic root=UUID=2d6c4920-ef06-4dc8-b11c-d86e8caed23c ro quiet splash vt.handoff=7


dmesg ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

[    0.911110] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[    0.911878] audit: initializing netlink socket (disabled)
[   23.501097] wmi: Mapper loaded
[   25.764512] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   30.340983] ath5k 0000:02:00.0: enabling device (0000 -> 0002)
[   30.341244] ath5k 0000:02:00.0: registered as 'phy0'
[   31.275495] ath: EEPROM regdomain: 0x0
[   31.275507] ath: EEPROM indicates default country code should be used
[   31.275509] ath: doing EEPROM country->regdmn map search
[   31.275512] ath: country maps to regdmn code: 0x3a
[   31.275515] ath: Country alpha2 being used: US
[   31.275517] ath: Regpair used: 0x3a
[   31.369990] ath5k: phy0: Atheros AR2414 chip found (MAC: 0x79, PHY: 0x45)
[   31.951309] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   31.963448] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready

    ======== Done ========


```

---

### Post by varunendra on 2014-05-23
While being connected to internet via Ethernet cable, please install "iw"  -
```
sudo apt-get install iw
```
Then disconnect the Ethernet cable, and do -
```
sudo iw reg set US
```
..assuming you are in US. If you are in a different country, please use its code instead. You can find the country codes here : [http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2#Decoding_table](http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2#Decoding_table)

Then retry connecting to wifi. If it still fails, please try a newer version of the driver as suggested here : [http://ubuntuforums.org/showpost.php?p=13028924](http://ubuntuforums.org/showpost.php?p=13028924)

---

### Post by bill41 on 2014-05-23
I installed 'iw' and set my country code after disconnecting the ethernet cable. Then retried the wifi connection but same result. Then I followed the instructions for trying a newer version of the driver but still no change.

You mentioned disconnecting the ethernet. I haven't been disconnecting the ethernet during the troubleshooting process unless specifically instructed. Don't know if this is significant or not.

I'm recording everything in the command prompt and including it here in case it might be useful:


```

bill@toshiba-a45-s120:~$ echo "options ath5k nohwcrypt=Y" | sudo tee /etc/modprobe.d/ath5k.conf
[sudo] password for bill: 
options ath5k nohwcrypt=Y
bill@toshiba-a45-s120:~$ sudo modprobe -rv ath5k
rmmod ath5k
rmmod mac80211
rmmod ath
rmmod cfg80211
bill@toshiba-a45-s120:~$ sudo modprobe -v ath5k
insmod /lib/modules/3.13.0-24-generic/kernel/net/wireless/cfg80211.ko 
insmod /lib/modules/3.13.0-24-generic/kernel/net/mac80211/mac80211.ko 
insmod /lib/modules/3.13.0-24-generic/kernel/drivers/net/wireless/ath/ath.ko 
insmod /lib/modules/3.13.0-24-generic/kernel/drivers/net/wireless/ath/ath5k/ath5k.ko nohwcrypt=Y 
bill@toshiba-a45-s120:~$ 


bill@toshiba-a45-s120:~$ sudo apt-get install iw
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  iw
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 51.9 kB of archives.
After this operation, 152 kB of additional disk space will be used.
Get:1 http://us.archive.ubuntu.com/ubuntu/ trusty/main iw i386 3.4-1 [51.9 kB]
Fetched 51.9 kB in 0s (274 kB/s)
Selecting previously unselected package iw.
(Reading database ... 109781 files and directories currently installed.)
Preparing to unpack .../apt/archives/iw_3.4-1_i386.deb ...
Unpacking iw (3.4-1) ...
Processing triggers for man-db (2.6.7.1-1) ...
Setting up iw (3.4-1) ...
bill@toshiba-a45-s120:~$ 


bill@toshiba-a45-s120:~$ sudo iw reg set US
bill@toshiba-a45-s120:~$ 


bill@toshiba-a45-s120:~$ cd ~/Downloads/backports-3.15-rc1-1
bill@toshiba-a45-s120:~/Downloads/backports-3.15-rc1-1$ make defconfig-ath5k
Generating local configuration database from kernel ... done.
cc -Wall -Wmissing-prototypes -Wstrict-prototypes -O2 -fomit-frame-pointer   -c -o conf.o conf.c
cc -Wall -Wmissing-prototypes -Wstrict-prototypes -O2 -fomit-frame-pointer   -c -o zconf.tab.o zconf.tab.c
cc   conf.o zconf.tab.o   -o conf
boolean symbol HWMON tested for 'm'? test forced to 'n'
boolean symbol HWMON tested for 'm'? test forced to 'n'
#
# configuration written to .config
#
bill@toshiba-a45-s120:~/Downloads/backports-3.15-rc1-1$ make
make[5]: `conf' is up to date.
boolean symbol HWMON tested for 'm'? test forced to 'n'
boolean symbol HWMON tested for 'm'? test forced to 'n'
#
# configuration written to .config
#
Building backport-include/backport/autoconf.h ... done.
  CC [M]  /home/bill/Downloads/backports-3.15-rc1-1/compat/main.o
  CC [M]  /home/bill/Downloads/backports-3.15-rc1-1/compat/backport-3.14.o
  CC [M]  /home/bill/Downloads/backports-3.15-rc1-1/compat/backport-3.15.o
  LD [M]  /home/bill/Downloads/backports-3.15-rc1-1/compat/compat.o
  CC [M]  /home/bill/Downloads/backports-3.15-rc1-1/drivers/net/wireless/ath/main.o
  CC [M]  /home/bill/Downloads/backports-3.15-rc1-1/drivers/net/wireless/ath/regd.o
  CC [M]  /home/bill/Downloads/backports-3.15-rc1-1/drivers/net/wireless/ath/hw.o
  CC [M]  /home/bill/Downloads/backports-3.15-rc1-1/drivers/net/wireless/ath/key.o
  CC [M]  /home/bill/Downloads/backports-3.15-rc1-1/drivers/net/wireless/ath/dfs_pattern_detector.o
  CC [M]  /home/bill/Downloads/backports-3.15-rc1-1/drivers/net/wireless/ath/dfs_pri_detector.o
  LD [M]  /home/bill/Downloads/backports-3.15-rc1-1/drivers/net/wireless/ath/ath.o
  CC [M]  /home/bill/Downloads/backports-3.15-rc1-1/drivers/net/wireless/ath/ath5k/caps.o
  CC [M]  /home/bill/Downloads/backports-3.15-rc1-1/drivers/net/wireless/ath/ath5k/initvals.o
  CC [M]  /home/bill/Downloads/backports-3.15-rc1-1/drivers/net/wireless/ath/ath5k/eeprom.o
  CC [M]  /home/bill/Downloads/backports-3.15-rc1-1/drivers/net/wireless/ath/ath5k/gpio.o
  CC [M]  /home/bill/Downloads/backports-3.15-rc1-1/drivers/net/wireless/ath/ath5k/desc.o
  CC [M]  /home/bill/Downloads/backports-3.15-rc1-1/drivers/net/wireless/ath/ath5k/dma.o
  CC [M]  /home/bill/Downloads/backports-3.15-rc1-1/drivers/net/wireless/ath/ath5k/qcu.o
  CC [M]  /home/bill/Downloads/backports-3.15-rc1-1/drivers/net/wireless/ath/ath5k/pcu.o
  CC [M]  /home/bill/Downloads/backports-3.15-rc1-1/drivers/net/wireless/ath/ath5k/phy.o
  CC [M]  /home/bill/Downloads/backports-3.15-rc1-1/drivers/net/wireless/ath/ath5k/reset.o
  CC [M]  /home/bill/Downloads/backports-3.15-rc1-1/drivers/net/wireless/ath/ath5k/attach.o
  CC [M]  /home/bill/Downloads/backports-3.15-rc1-1/drivers/net/wireless/ath/ath5k/base.o
  CC [M]  /home/bill/Downloads/backports-3.15-rc1-1/drivers/net/wireless/ath/ath5k/led.o
  CC [M]  /home/bill/Downloads/backports-3.15-rc1-1/drivers/net/wireless/ath/ath5k/rfkill.o
  CC [M]  /home/bill/Downloads/backports-3.15-rc1-1/drivers/net/wireless/ath/ath5k/ani.o
  CC [M]  /home/bill/Downloads/backports-3.15-rc1-1/drivers/net/wireless/ath/ath5k/sysfs.o
  CC [M]  /home/bill/Downloads/backports-3.15-rc1-1/drivers/net/wireless/ath/ath5k/mac80211-ops.o
  CC [M]  /home/bill/Downloads/backports-3.15-rc1-1/drivers/net/wireless/ath/ath5k/pci.o
  LD [M]  /home/bill/Downloads/backports-3.15-rc1-1/drivers/net/wireless/ath/ath5k/ath5k.o
  CC [M]  /home/bill/Downloads/backports-3.15-rc1-1/net/mac80211/main.o
  CC [M]  /home/bill/Downloads/backports-3.15-rc1-1/net/mac80211/status.o
  CC [M]  /home/bill/Downloads/backports-3.15-rc1-1/net/mac80211/sta_info.o
  CC [M]  /home/bill/Downloads/backports-3.15-rc1-1/net/mac80211/wep.o
  CC [M]  /home/bill/Downloads/backports-3.15-rc1-1/net/mac80211/wpa.o
  CC [M]  /home/bill/Downloads/backports-3.15-rc1-1/net/mac80211/scan.o
  CC [M]  /home/bill/Downloads/backports-3.15-rc1-1/net/mac80211/offchannel.o
  CC [M]  /home/bill/Downloads/backports-3.15-rc1-1/net/mac80211/ht.o
  CC [M]  /home/bill/Downloads/backports-3.15-rc1-1/net/mac80211/agg-tx.o
  CC [M]  /home/bill/Downloads/backports-3.15-rc1-1/net/mac80211/agg-rx.o
  CC [M]  /home/bill/Downloads/backports-3.15-rc1-1/net/mac80211/vht.o
  CC [M]  /home/bill/Downloads/backports-3.15-rc1-1/net/mac80211/ibss.o
  CC [M]  /home/bill/Downloads/backports-3.15-rc1-1/net/mac80211/iface.o
/home/bill/Downloads/backports-3.15-rc1-1/net/mac80211/iface.c:1080:2: warning: initialization from incompatible pointer type [enabled by default]
  .ndo_select_queue = ieee80211_netdev_select_queue,
  ^
/home/bill/Downloads/backports-3.15-rc1-1/net/mac80211/iface.c:1080:2: warning: (near initialization for &#8216;ieee80211_dataif_ops.ndo_select_queue&#8217;) [enabled by default]
/home/bill/Downloads/backports-3.15-rc1-1/net/mac80211/iface.c:1122:2: warning: initialization from incompatible pointer type [enabled by default]
  .ndo_select_queue = ieee80211_monitor_select_queue,
  ^
/home/bill/Downloads/backports-3.15-rc1-1/net/mac80211/iface.c:1122:2: warning: (near initialization for &#8216;ieee80211_monitorif_ops.ndo_select_queue&#8217;) [enabled by default]
  CC [M]  /home/bill/Downloads/backports-3.15-rc1-1/net/mac80211/rate.o
  CC [M]  /home/bill/Downloads/backports-3.15-rc1-1/net/mac80211/michael.o
  CC [M]  /home/bill/Downloads/backports-3.15-rc1-1/net/mac80211/tkip.o
  CC [M]  /home/bill/Downloads/backports-3.15-rc1-1/net/mac80211/aes_ccm.o
  CC [M]  /home/bill/Downloads/backports-3.15-rc1-1/net/mac80211/aes_cmac.o
  CC [M]  /home/bill/Downloads/backports-3.15-rc1-1/net/mac80211/cfg.o
  CC [M]  /home/bill/Downloads/backports-3.15-rc1-1/net/mac80211/rx.o
  CC [M]  /home/bill/Downloads/backports-3.15-rc1-1/net/mac80211/spectmgmt.o
  CC [M]  /home/bill/Downloads/backports-3.15-rc1-1/net/mac80211/tx.o
  CC [M]  /home/bill/Downloads/backports-3.15-rc1-1/net/mac80211/key.o
  CC [M]  /home/bill/Downloads/backports-3.15-rc1-1/net/mac80211/util.o
  CC [M]  /home/bill/Downloads/backports-3.15-rc1-1/net/mac80211/wme.o
  CC [M]  /home/bill/Downloads/backports-3.15-rc1-1/net/mac80211/event.o
  CC [M]  /home/bill/Downloads/backports-3.15-rc1-1/net/mac80211/chan.o
  CC [M]  /home/bill/Downloads/backports-3.15-rc1-1/net/mac80211/trace.o
  CC [M]  /home/bill/Downloads/backports-3.15-rc1-1/net/mac80211/mlme.o
  CC [M]  /home/bill/Downloads/backports-3.15-rc1-1/net/mac80211/led.o
  CC [M]  /home/bill/Downloads/backports-3.15-rc1-1/net/mac80211/mesh.o
  CC [M]  /home/bill/Downloads/backports-3.15-rc1-1/net/mac80211/mesh_pathtbl.o
  CC [M]  /home/bill/Downloads/backports-3.15-rc1-1/net/mac80211/mesh_plink.o
  CC [M]  /home/bill/Downloads/backports-3.15-rc1-1/net/mac80211/mesh_hwmp.o
  CC [M]  /home/bill/Downloads/backports-3.15-rc1-1/net/mac80211/mesh_sync.o
  CC [M]  /home/bill/Downloads/backports-3.15-rc1-1/net/mac80211/mesh_ps.o
  CC [M]  /home/bill/Downloads/backports-3.15-rc1-1/net/mac80211/pm.o
  CC [M]  /home/bill/Downloads/backports-3.15-rc1-1/net/mac80211/rc80211_minstrel.o
  CC [M]  /home/bill/Downloads/backports-3.15-rc1-1/net/mac80211/rc80211_minstrel_ht.o
  LD [M]  /home/bill/Downloads/backports-3.15-rc1-1/net/mac80211/mac80211.o
  CC [M]  /home/bill/Downloads/backports-3.15-rc1-1/net/wireless/core.o
  CC [M]  /home/bill/Downloads/backports-3.15-rc1-1/net/wireless/sysfs.o
  CC [M]  /home/bill/Downloads/backports-3.15-rc1-1/net/wireless/radiotap.o
  CC [M]  /home/bill/Downloads/backports-3.15-rc1-1/net/wireless/util.o
  CC [M]  /home/bill/Downloads/backports-3.15-rc1-1/net/wireless/reg.o
  CC [M]  /home/bill/Downloads/backports-3.15-rc1-1/net/wireless/scan.o
  CC [M]  /home/bill/Downloads/backports-3.15-rc1-1/net/wireless/nl80211.o
  CC [M]  /home/bill/Downloads/backports-3.15-rc1-1/net/wireless/mlme.o
  CC [M]  /home/bill/Downloads/backports-3.15-rc1-1/net/wireless/ibss.o
  CC [M]  /home/bill/Downloads/backports-3.15-rc1-1/net/wireless/sme.o
  CC [M]  /home/bill/Downloads/backports-3.15-rc1-1/net/wireless/chan.o
  CC [M]  /home/bill/Downloads/backports-3.15-rc1-1/net/wireless/ethtool.o
  CC [M]  /home/bill/Downloads/backports-3.15-rc1-1/net/wireless/mesh.o
  CC [M]  /home/bill/Downloads/backports-3.15-rc1-1/net/wireless/ap.o
  CC [M]  /home/bill/Downloads/backports-3.15-rc1-1/net/wireless/trace.o
  CC [M]  /home/bill/Downloads/backports-3.15-rc1-1/net/wireless/wext-compat.o
  CC [M]  /home/bill/Downloads/backports-3.15-rc1-1/net/wireless/wext-sme.o
  LD [M]  /home/bill/Downloads/backports-3.15-rc1-1/net/wireless/cfg80211.o
  Building modules, stage 2.
  MODPOST 5 modules
  CC      /home/bill/Downloads/backports-3.15-rc1-1/compat/compat.mod.o
  LD [M]  /home/bill/Downloads/backports-3.15-rc1-1/compat/compat.ko
  CC      /home/bill/Downloads/backports-3.15-rc1-1/drivers/net/wireless/ath/ath.mod.o
  LD [M]  /home/bill/Downloads/backports-3.15-rc1-1/drivers/net/wireless/ath/ath.ko
  CC      /home/bill/Downloads/backports-3.15-rc1-1/drivers/net/wireless/ath/ath5k/ath5k.mod.o
  LD [M]  /home/bill/Downloads/backports-3.15-rc1-1/drivers/net/wireless/ath/ath5k/ath5k.ko
  CC      /home/bill/Downloads/backports-3.15-rc1-1/net/mac80211/mac80211.mod.o
  LD [M]  /home/bill/Downloads/backports-3.15-rc1-1/net/mac80211/mac80211.ko
  CC      /home/bill/Downloads/backports-3.15-rc1-1/net/wireless/cfg80211.mod.o
  LD [M]  /home/bill/Downloads/backports-3.15-rc1-1/net/wireless/cfg80211.ko
bill@toshiba-a45-s120:~/Downloads/backports-3.15-rc1-1$ 


bill@toshiba-a45-s120:~/Downloads/backports-3.15-rc1-1$ sudo make install
[sudo] password for bill: 
  Building modules, stage 2.
  MODPOST 5 modules
  INSTALL /home/bill/Downloads/backports-3.15-rc1-1/compat/compat.ko
Can't read private key
  INSTALL /home/bill/Downloads/backports-3.15-rc1-1/drivers/net/wireless/ath/ath.ko
Can't read private key
  INSTALL /home/bill/Downloads/backports-3.15-rc1-1/drivers/net/wireless/ath/ath5k/ath5k.ko
Can't read private key
  INSTALL /home/bill/Downloads/backports-3.15-rc1-1/net/mac80211/mac80211.ko
Can't read private key
  INSTALL /home/bill/Downloads/backports-3.15-rc1-1/net/wireless/cfg80211.ko
Can't read private key
  DEPMOD  3.13.0-24-generic
depmod will prefer updates/ over kernel/ -- OK!
Note:
You may or may not need to update your initramfs, you should if
any of the modules installed are part of your initramfs. To add
support for your distribution to do this automatically send a
patch against "update-initramfs.sh". If your distribution does not
require this send a patch with the '/usr/bin/lsb_release -i -s'
("Ubuntu") tag for your distribution to avoid this warning.

Your backported driver modules should be installed now.
Reboot.

bill@toshiba-a45-s120:~/Downloads/backports-3.15-rc1-1$ sudo modprobe -rv ath5k
rmmod ath5k
rmmod mac80211
rmmod ath
rmmod cfg80211
bill@toshiba-a45-s120:~/Downloads/backports-3.15-rc1-1$ sudo modprobe -v ath5k
insmod /lib/modules/3.13.0-24-generic/updates/compat/compat.ko 
insmod /lib/modules/3.13.0-24-generic/updates/net/wireless/cfg80211.ko 
insmod /lib/modules/3.13.0-24-generic/updates/net/mac80211/mac80211.ko 
insmod /lib/modules/3.13.0-24-generic/updates/drivers/net/wireless/ath/ath.ko 
insmod /lib/modules/3.13.0-24-generic/updates/drivers/net/wireless/ath/ath5k/ath5k.ko nohwcrypt=Y 
bill@toshiba-a45-s120:~/Downloads/backports-3.15-rc1-1$ 


```

---

### Post by varunendra on 2014-05-24
The outputs look normal to me, including the warning messages.

Please run the command -
```
sudo sed -i 's/^REG.*=$/&US/' /etc/default/crda
```
Then reboot, and run the wireless_script again. Let us see what its report (the freshly generated one) says this time. (delete the previous report to avoid confusion while posting back)

---

### Post by bill41 on 2014-05-24
Completed. Here is the new report:
```


    ======== Wireless-Info START ========

System-Info ~~~~~~~~~~~~~~~~~~~~~~~~

toshiba-a45-s120 3.13.0-24-generic i686,  Ubuntu 14.04 LTS, trusty

CPU    : Intel(R) Celeron(R) CPU 2.60GHz
Memory : 1238 MB
Uptime : 09:19:40 up 5 min,  2 users,  load average: 0.24, 0.53, 0.30


lspci ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

01:08.0 Ethernet controller [0200]: Intel Corporation 82801DB PRO/100 VE (MOB) Ethernet Controller [8086:103d] (rev 83)
    Subsystem: Toshiba America Info Systems Device [1179:0001]
    Kernel driver in use: e100
--
02:00.0 Ethernet controller [0200]: Qualcomm Atheros AR5212/AR5213 Wireless Network Adapter [168c:0013] (rev 01)
    Subsystem: Netgear WG511T 108 Mbps Wireless PC Card (rev.C) [1385:5b00]
    Kernel driver in use: ath5k


lsusb ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


PCMCIA Card Info ~~~~~~~~~~~~~~~~~~~



iwconfig ~~~~~~~~~~~~~~~~~~~~~~~~~~~

wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=27 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          


rfkill ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

      Interface        Soft blocked  Hard blocked
0: phy0: Wireless LAN      no            no


lsmod ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

ath5k                 134808  0 
ath                    24182  1 ath5k
mac80211              474862  1 ath5k
cfg80211              419580  3 ath,ath5k,mac80211
compat                 13965  3 cfg80211,ath5k,mac80211
wmi                    18673  1 toshiba_acpi


module parameters ~~~~~~~~~~~~~~~~~~

ath5k         (3): fastchanswitch=N | nohwcrypt=Y | no_hw_rfkill_switch=N
cfg80211      (2): cfg80211_disable_40mhz_24ghz=N | ieee80211_regdom=00
compat        (3): 
mac80211      (5): beacon_loss_count=7 | ieee80211_default_rc_algo=minstrel_ht | max_nullfunc_tries=2 | max_probe_tries=5 | probe_wait_ms=500
wmi           (2): debug_dump_wdg=N | debug_event=N


nm-tool ~~~~~~~~~~~~~~~~~~~~~~~~~~~~

State: connected (global)
============================o=============o========o==============o=========o===========o==============o===========
 Interface & ID             | Type        | Driver | State        | Default | Speed     | Support      | HW Addr   
============================o=============o========o==============o=========o===========o==============o===========
 wlan0                      | 802.11 WiFi | ath5k  | disconnected | no      |           | WEP/WPA/WPA2 | <MAC wlan0>

    T1tb0fW95:       Infra, <MAC C-02 T1tb0fW95>, Freq 2462 MHz, Rate 54 Mb/s, Strength 97 WPA2
    MTF172:          Infra, <MAC C-01 MTF172>, Freq 2457 MHz, Rate 54 Mb/s, Strength 59 WPA WPA2
    kublakhan:       Infra, <MAC C-05 kublakhan>, Freq 2412 MHz, Rate 54 Mb/s, Strength 34 WPA WPA2
    2WIRE600:        Infra, <MAC C-NA 2WIRE600 1>, Freq 2457 MHz, Rate 54 Mb/s, Strength 20 WPA WPA2
    2WIRE675:        Infra, <MAC C-03 2WIRE675>, Freq 2412 MHz, Rate 54 Mb/s, Strength 30 WPA WPA2
    NETGEAR:         Infra, <MAC C-04 NETGEAR>, Freq 2412 MHz, Rate 54 Mb/s, Strength 25 WPA2
    WAPLNEK:         Infra, <MAC C-06 WAPLNEK>, Freq 2462 MHz, Rate 54 Mb/s, Strength 25 WPA
----------------------------+-------------+--------+--------------+---------+-----------+--------------+-----------
 eth0  [Wired connection 1] | Wired       | e100   | connected    | yes     | 100 Mb/s  |              | <MAC eth0>

    Address:         192.168.1.3
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1
    DNS:             192.168.1.1
----------------------------+-------------+--------+--------------+---------+-----------+--------------+-----------


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
 


interfaces ~~~~~~~~~~~~~~~~~~~~~~~~~

# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback

resolv.conf ~~~~~~~~~~~~~~~~~~~~~~~~

nameserver 127.0.1.1


Routes & Ping ~~~~~~~~~~~~~~~~~~~~~~

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 eth0
192.168.1.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0

--- 192.168.1.1 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 1001ms
rtt min/avg/max/mdev = 0.848/0.871/0.894/0.023 ms

--- 127.0.1.1 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 999ms
rtt min/avg/max/mdev = 0.076/0.076/0.077/0.008 ms


iw reg get ~~~~~~~~~~~~~~~~~~~~~~~~~

(Region : "en_US.UTF-8")
country US:
    (2402 - 2472 @ 40), (3, 27)
    (5170 - 5250 @ 40), (3, 17)
    (5250 - 5330 @ 40), (3, 20), DFS
    (5490 - 5600 @ 40), (3, 20), DFS
    (5650 - 5710 @ 40), (3, 20), DFS
    (5735 - 5835 @ 40), (3, 30)
    (57240 - 63720 @ 2160), (N/A, 40)


iwlist chan ~~~~~~~~~~~~~~~~~~~~~~~~

wlan0     11 channels in total; available frequencies :
          Channel 01 (2.412 GHz) - 11 (2.462 GHz)


iwlist scan ~~~~~~~~~~~~~~~~~~~~~~~~

wlan0     Scan completed :
          Cell 01 - Address: <MAC C-01 MTF172>
                    Channel:10
                    Frequency:2.457 GHz (Channel 10)
                    Quality=42/70  Signal level=-68 dBm  
                    Encryption key:on
                    ESSID:"MTF172"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000019e40a0a
                    Extra: Last beacon: 84ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC C-02 T1tb0fW95>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=67/70  Signal level=-43 dBm  
                    Encryption key:on
                    ESSID:"T1tb0fW95"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s
                    Bit Rates:9 Mb/s; 18 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000740317e98
                    Extra: Last beacon: 84ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                       Preauthentication Supported
          Cell 03 - Address: <MAC C-03 2WIRE675>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=22/70  Signal level=-88 dBm  
                    Encryption key:on
                    ESSID:"2WIRE675"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000117901173fae
                    Extra: Last beacon: 24024ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 04 - Address: <MAC C-04 NETGEAR>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=23/70  Signal level=-87 dBm  
                    Encryption key:on
                    ESSID:"NETGEAR"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000adda2b3fb9
                    Extra: Last beacon: 24024ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 05 - Address: <MAC C-05 kublakhan>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=27/70  Signal level=-83 dBm  
                    Encryption key:on
                    ESSID:"kublakhan"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000018caf3517
                    Extra: Last beacon: 84ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 06 - Address: <MAC C-06 WAPLNEK>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=25/70  Signal level=-85 dBm  
                    Encryption key:on
                    ESSID:"WAPLNEK"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000013d89d883c38
                    Extra: Last beacon: 108ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK


blacklist ~~~~~~~~~~~~~~~~~~~~~~~~~~

[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci

[/etc/modprobe.d/libpisock9.conf]
blacklist visor


modinfo ~~~~~~~~~~~~~~~~~~~~~~~~~~~~

[ath5k]
filename:       /lib/modules/3.13.0-24-generic/updates/drivers/net/wireless/ath/ath5k/ath5k.ko
version:        backported from Linux (v3.15-rc1-0-gc9eaa44) using backports v3.15-rc1-1-0-g2a25483
srcversion:     03A8D89E8F327C65EE5E5A8
depends:        mac80211,compat,cfg80211,ath
parm:           nohwcrypt:Disable hardware encryption. (bool)
parm:           fastchanswitch:Enable fast channel switching for AR2413/AR5413 radios. (bool)
parm:           no_hw_rfkill_switch:Ignore the GPIO RFKill switch state (bool)

[ath]
filename:       /lib/modules/3.13.0-24-generic/updates/drivers/net/wireless/ath/ath.ko
srcversion:     62CCE3A0B4A1CC9207A10E0
depends:        cfg80211

[mac80211]
filename:       /lib/modules/3.13.0-24-generic/updates/net/mac80211/mac80211.ko
version:        backported from Linux (v3.15-rc1-0-gc9eaa44) using backports v3.15-rc1-1-0-g2a25483
srcversion:     BDDF1FB5DBA6A5BCAD8614A
depends:        cfg80211,compat
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[cfg80211]
filename:       /lib/modules/3.13.0-24-generic/updates/net/wireless/cfg80211.ko
version:        backported from Linux (v3.15-rc1-0-gc9eaa44) using backports v3.15-rc1-1-0-g2a25483
srcversion:     7F5DF7FC430B6F41B27560E
depends:        compat
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

[compat]
filename:       /lib/modules/3.13.0-24-generic/updates/compat/compat.ko
version:        backported from Linux (v3.15-rc1-0-gc9eaa44) using backports v3.15-rc1-1-0-g2a25483
srcversion:     0B4E75B519E5E2015024D8D
depends:        
parm:           backported_kernel_name:The kernel tree name that was used for this backport (Linux) (charp)
parm:           backported_kernel_version:The kernel version that was used for this backport (v3.15-rc1-0-gc9eaa44) (charp)
parm:           backports_version:The git version of the backports tree used to generate this backport (v3.15-rc1-1-0-g2a25483) (charp)


udev rules ~~~~~~~~~~~~~~~~~~~~~~~~~

# PCI device 0x8086:0x103d (e100)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC eth0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

# PCI device 0x168c:0x0013 (ath5k)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC wlan0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"


Custom files/entries ~~~~~~~~~~~~~~~

/etc/modules        : Default
/etc/rc.local       : Default
/etc/modprobe.d     : Not Default
/etc/pm/(cnf|pw|sl) : Default

[/etc/modprobe.d]
ath5k.conf        : options ath5k nohwcrypt=Y
iwlwifi.conf      : remove iwlwifi \
                    (/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
                    && /sbin/modprobe -r mac80211
mlx4.conf         : softdep mlx4_core post: mlx4_en


Kernel boot line ~~~~~~~~~~~~~~~~~~~

BOOT_IMAGE=/boot/vmlinuz-3.13.0-24-generic root=UUID=81bc7e59-c4de-4579-b806-10d68a6ed598 ro quiet splash vt.handoff=7


dmesg ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

[    0.909796] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[    0.910556] audit: initializing netlink socket (disabled)
[   20.168164] wmi: Mapper loaded
[   23.104199] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   28.984291] ath5k 0000:02:00.0: enabling device (0000 -> 0002)
[   28.984552] ath5k 0000:02:00.0: registered as 'phy0'
[   30.021854] ath: EEPROM regdomain: 0x0
[   30.021864] ath: EEPROM indicates default country code should be used
[   30.021866] ath: doing EEPROM country->regdmn map search
[   30.021869] ath: country maps to regdmn code: 0x3a
[   30.021872] ath: Country alpha2 being used: US
[   30.021874] ath: Regpair used: 0x3a
[   30.123841] ath5k: phy0: Atheros AR2414 chip found (MAC: 0x79, PHY: 0x45)
[   30.916715] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   30.918568] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready

    ======== Done ========


```

---

### Post by varunendra on 2014-05-26
Sorry for the delay in response, sometimes even sundays become busier than weekdays..

I can see no problems in the output, it seems the system is not even attempting to connect to the wireless network.

When you click on Network Manager's icon (nm-applet), do you see available networks in the drop-down list? If yes, does anything happen when you click YOUR network?

If you don't see available networks in the drop-down menu, try clicking on "Connect to Hidden Wireless Network..", and enter your wireless network credentials in the opened dialogue box.

And yes, keep the ethernet cable unplugged while trying all this. Network Manager may not attempt the wireless connection when the wired connection is detected. Both ethernet and wireless can be used at the same time, but I can't say very confidently when it works when it doesn't. So at least for now, it is best to keep it unplugged when trying to connect to the wireless network.

Also try saving the network configuration in Network Manager by manually creating a connection there as follows :

Network Manager menu > Edit Connections.. > "Wireless" tab > click "Add" button > Enter correct "SSID" under "Wireless" tab, choose "WPA & WPA2 Personal" under "Wireless Security", Save the password > Make sure "Connect Automatically" and "Available to all users" are enabled (have tick marks in relevant boxes) > Save connection > Exit

**[COLOR="#FF0000"]Edit:[/COLOR]** Lubuntu has a bug in its latest versions due to which the Network Manager's icon ("nm-applet" at the top-right corner) doesn't come up at all by default. To bring it up, press 'Alt-F2' > type (without quotes) "nm-applet" > press 'Enter'

---

### Post by bill41 on 2014-05-26
No need to apologize, I'm grateful for your time and your help!

Yes regarding the Network Manager icon not showing by default, when I first installed Lubuntu 14.04, I noticed there was no icon visible for connecting to a wireless network. Didn't know at the time it was supposed to be the Network Manager icon specifically. I did the following to correct that: right-click Panel... clicked Add/Remove Panel Items... brings up the Panel Applets tab of the Panel Preferences dialog box... clicked Add button... chose "Manage Networks" plugin... clicked Add button.

The Manage Networks applet shows 2 icons on the Panel (lower-right corner): the 1st icon for the ethernet, the 2nd one for the wireless. The icon for wireless has an exclamation point and when I hover over it, the message "wlan0 - Connection has limited or no connectivity" appears.

When I click on the icon for wireless, I see the available wireless networks (just a padlock icon, the SSID, and a signal strength bar indicator for each network; no "Connect to Hidden Wireless Network"). When I select my network, I'm asked for my "encryption key". When I type that in nothing happens. The Panel icon for wireless still has the exclamation point. I'm sure I'm typing the correct key, I have other wireless devices that connect to this network.

The icon for ethernet correctly changes from exclamation point to no exclamation point if I plug in the ethernet cable.

I'm now trying to run the Network Manager applet instead of the "Manage Networks" applet assuming they're different. Unfortunately "Alt+F2" is not recognized in Lubuntu (because Lubuntu uses LDXE and OpenBox instead of Gnome?). Then I found this article: [http://www.webupd8.org/2014/04/fix-lubuntu-1404-network-manager.html](http://www.webupd8.org/2014/04/fix-lubuntu-1404-network-manager.html) to get the Network Manager icon to show in Lubuntu 14.04. In the article I tried both fix 1 and fix 2.

Network Manager now seems to be running: when I log in, I see temporary pop-up messages about the ethernet and wireless networks which I didn't see before, but I still don't see an icon for Network Manager on the Panel. I checked to see if Network Manager is now available to be added to the Panel (right-click Panel... click Add/Remove Panel Items...) but I don't see it listed there.

So Network Manager appears to be running in the background but I can't interact with it.

I also tried running nm-applet from a terminal (is "Alt+F2" a way of using a terminal asynchronously?). The temporary pop-up messages for ethernet and wireless appeared again and in the terminal I got the message "nm-applet-Message: using fallback from indicator to GTKStatusICon". Then I did a ctrl+C to get back to a prompt.

Regarding manually creating a connection, I don't have a Network Manager menu, but I created a connection this way: Menu in lower-left corner... Preferences... Network Connections... clicked Add button... chose Wifi connection type... clicked Create button... and I got a similar UI to what you described. I entered the settings you listed with "Connect automatically" and "Available to all users" enabled. Other settings I left as default: Mode - Infrastructure, BSSID - blank, Device MAC address - blank, Cloned MAC address - blank, MTU - automatic.

After creating the connection I rebooted for good measure but still can't connect. When I go back to Preferences... Network Connections... the new manual wifi connection is listed but Last Used shows as "never".

**Edit:** I managed to get the Network Manager icon to show in the Panel. The reason it wasn't showing was a result of a self-inflicted wound... I had removed the System Tray applet from the Panel :) .  Adding back the System Tray applet now displays the Network Manager icon. I went ahead and removed the "Manage Networks" applet from the Panel.

When I click on the Network Manager icon, I now see the Network Manager menu. All available networks are visible as before (but now with "Connect to Hidden Wi-Fi Network" and other items), and when I click on my network, it requests authentication as before. After entering the password, it seems to try to connect, but after about a half minute, asks for the password again.

I also tried connecting with WPA2 security removed from the router. Other than obviously not asking for a password, it still won't connect.

Also these messages are showing up on boot up:
```

cfg80211: module has bad taint, not creating trace events
mac80211: module has bad taint, not creating trace events

```
Don't know when they first started showing but I think it's been a few days. They appear momentarily and then disappear.

---

### Post by varunendra on 2014-05-27
So evidently there were discrepancies in my instructions, because I have no idea of differences in Lubuntu, but you did great in finding the correct ways.

Whatever you have mentioned sounds good and as intended. Let us see a fresh report of the wireless_script. Delete the older report to avoid confusion, generate a fresh one and post it back please.

The "taint" messages you posted don't look too serious, but they are certainly not normal either.

---

### Post by bill41 on 2014-05-27
Here is the new report:
```


    ======== Wireless-Info START ========

System-Info ~~~~~~~~~~~~~~~~~~~~~~~~

toshiba-a45-s120 3.13.0-24-generic i686,  Ubuntu 14.04 LTS, trusty

CPU    : Intel(R) Celeron(R) CPU 2.60GHz
Memory : 1238 MB
Uptime : 10:12:03 up 16:53,  2 users,  load average: 0.64, 0.26, 0.13


lspci ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

01:08.0 Ethernet controller [0200]: Intel Corporation 82801DB PRO/100 VE (MOB) Ethernet Controller [8086:103d] (rev 83)
    Subsystem: Toshiba America Info Systems Device [1179:0001]
    Kernel driver in use: e100
--
02:00.0 Ethernet controller [0200]: Qualcomm Atheros AR5212/AR5213 Wireless Network Adapter [168c:0013] (rev 01)
    Subsystem: Netgear WG511T 108 Mbps Wireless PC Card (rev.C) [1385:5b00]
    Kernel driver in use: ath5k


lsusb ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


PCMCIA Card Info ~~~~~~~~~~~~~~~~~~~



iwconfig ~~~~~~~~~~~~~~~~~~~~~~~~~~~

wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=27 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          


rfkill ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

      Interface        Soft blocked  Hard blocked
1: phy1: Wireless LAN      no            no


lsmod ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

ath5k                 134808  0 
ath                    24182  1 ath5k
mac80211              474862  1 ath5k
cfg80211              419580  3 ath,ath5k,mac80211
compat                 13965  3 cfg80211,ath5k,mac80211
wmi                    18673  1 toshiba_acpi


module parameters ~~~~~~~~~~~~~~~~~~

ath5k         (3): fastchanswitch=N | nohwcrypt=Y | no_hw_rfkill_switch=N
cfg80211      (2): cfg80211_disable_40mhz_24ghz=N | ieee80211_regdom=00
compat        (3): 
mac80211      (5): beacon_loss_count=7 | ieee80211_default_rc_algo=minstrel_ht | max_nullfunc_tries=2 | max_probe_tries=5 | probe_wait_ms=500
wmi           (2): debug_dump_wdg=N | debug_event=N


nm-tool ~~~~~~~~~~~~~~~~~~~~~~~~~~~~

State: connected (global)
============================o=============o========o==============o=========o===========o==============o===========
 Interface & ID             | Type        | Driver | State        | Default | Speed     | Support      | HW Addr   
============================o=============o========o==============o=========o===========o==============o===========
 wlan0                      | 802.11 WiFi | ath5k  | disconnected | no      |           | WEP/WPA/WPA2 | <MAC wlan0>

    T1tb0fW95:       Infra, <MAC C-02 T1tb0fW95>, Freq 2462 MHz, Rate 54 Mb/s, Strength 92 WPA2
    MTF172:          Infra, <MAC C-01 MTF172>, Freq 2457 MHz, Rate 54 Mb/s, Strength 49 WPA WPA2
    2WIRE675:        Infra, <MAC C-03 2WIRE675>, Freq 2412 MHz, Rate 54 Mb/s, Strength 37 WPA WPA2
    kublakhan:       Infra, <MAC C-04 kublakhan>, Freq 2437 MHz, Rate 54 Mb/s, Strength 32 WPA WPA2
    WAPLNEK:         Infra, <MAC C-05 WAPLNEK>, Freq 2462 MHz, Rate 54 Mb/s, Strength 14 WPA
    Connor Network:  Infra, <MAC C-07 Connor Network>, Freq 2412 MHz, Rate 54 Mb/s, Strength 22 WPA2
    NETGEAR:         Infra, <MAC C-06 NETGEAR>, Freq 2412 MHz, Rate 54 Mb/s, Strength 19 WPA2
----------------------------+-------------+--------+--------------+---------+-----------+--------------+-----------
 eth0  [Wired connection 1] | Wired       | e100   | connected    | yes     | 100 Mb/s  |              | <MAC eth0>

    Address:         192.168.1.3
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1
    DNS:             192.168.1.1
----------------------------+-------------+--------+--------------+---------+-----------+--------------+-----------


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

T1tb0fW95            : ssid=T1tb0fW95 | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 


interfaces ~~~~~~~~~~~~~~~~~~~~~~~~~

# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback

resolv.conf ~~~~~~~~~~~~~~~~~~~~~~~~

nameserver 127.0.1.1


Routes & Ping ~~~~~~~~~~~~~~~~~~~~~~

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 eth0
192.168.1.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0

--- 192.168.1.1 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 999ms
rtt min/avg/max/mdev = 0.766/0.796/0.826/0.030 ms

--- 127.0.1.1 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 999ms
rtt min/avg/max/mdev = 0.075/0.077/0.080/0.009 ms


iw reg get ~~~~~~~~~~~~~~~~~~~~~~~~~

(Region : "en_US.UTF-8")
country US:
    (2402 - 2472 @ 40), (3, 27)
    (5170 - 5250 @ 40), (3, 17)
    (5250 - 5330 @ 40), (3, 20), DFS
    (5490 - 5600 @ 40), (3, 20), DFS
    (5650 - 5710 @ 40), (3, 20), DFS
    (5735 - 5835 @ 40), (3, 30)
    (57240 - 63720 @ 2160), (N/A, 40)


iwlist chan ~~~~~~~~~~~~~~~~~~~~~~~~

wlan0     11 channels in total; available frequencies :
          Channel 01 (2.412 GHz) - 11 (2.462 GHz)


iwlist scan ~~~~~~~~~~~~~~~~~~~~~~~~

wlan0     Scan completed :
          Cell 01 - Address: <MAC C-01 MTF172>
                    Channel:10
                    Frequency:2.457 GHz (Channel 10)
                    Quality=38/70  Signal level=-72 dBm  
                    Encryption key:on
                    ESSID:"MTF172"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000000167156da
                    Extra: Last beacon: 80ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC C-02 T1tb0fW95>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=67/70  Signal level=-43 dBm  
                    Encryption key:on
                    ESSID:"T1tb0fW95"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s
                    Bit Rates:9 Mb/s; 18 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000e3096884f
                    Extra: Last beacon: 80ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                       Preauthentication Supported
          Cell 03 - Address: <MAC C-03 2WIRE675>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=28/70  Signal level=-82 dBm  
                    Encryption key:on
                    ESSID:"2WIRE675"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000011b617444175
                    Extra: Last beacon: 80ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 04 - Address: <MAC C-04 kublakhan>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=23/70  Signal level=-87 dBm  
                    Encryption key:on
                    ESSID:"kublakhan"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000001954fcfd0a
                    Extra: Last beacon: 80ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 05 - Address: <MAC C-05 WAPLNEK>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=24/70  Signal level=-86 dBm  
                    Encryption key:on
                    ESSID:"WAPLNEK"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00001415b295b33d
                    Extra: Last beacon: 17332ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 06 - Address: <MAC C-06 NETGEAR>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=21/70  Signal level=-89 dBm  
                    Encryption key:on
                    ESSID:"NETGEAR"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000003672ea0eb4
                    Extra: Last beacon: 17332ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 07 - Address: <MAC C-07 Connor Network>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=24/70  Signal level=-86 dBm  
                    Encryption key:on
                    ESSID:"Connor Network"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000004af0379c1b2
                    Extra: Last beacon: 80ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
          Cell 08 - Address: <MAC C-08 WAPsjb>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=21/70  Signal level=-89 dBm  
                    Encryption key:on
                    ESSID:"WAPsjb"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000001deba349189
                    Extra: Last beacon: 432ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK


blacklist ~~~~~~~~~~~~~~~~~~~~~~~~~~

[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci

[/etc/modprobe.d/libpisock9.conf]
blacklist visor


modinfo ~~~~~~~~~~~~~~~~~~~~~~~~~~~~

[ath5k]
filename:       /lib/modules/3.13.0-24-generic/updates/drivers/net/wireless/ath/ath5k/ath5k.ko
version:        backported from Linux (v3.15-rc1-0-gc9eaa44) using backports v3.15-rc1-1-0-g2a25483
srcversion:     03A8D89E8F327C65EE5E5A8
depends:        mac80211,compat,cfg80211,ath
parm:           nohwcrypt:Disable hardware encryption. (bool)
parm:           fastchanswitch:Enable fast channel switching for AR2413/AR5413 radios. (bool)
parm:           no_hw_rfkill_switch:Ignore the GPIO RFKill switch state (bool)

[ath]
filename:       /lib/modules/3.13.0-24-generic/updates/drivers/net/wireless/ath/ath.ko
srcversion:     62CCE3A0B4A1CC9207A10E0
depends:        cfg80211

[mac80211]
filename:       /lib/modules/3.13.0-24-generic/updates/net/mac80211/mac80211.ko
version:        backported from Linux (v3.15-rc1-0-gc9eaa44) using backports v3.15-rc1-1-0-g2a25483
srcversion:     BDDF1FB5DBA6A5BCAD8614A
depends:        cfg80211,compat
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[cfg80211]
filename:       /lib/modules/3.13.0-24-generic/updates/net/wireless/cfg80211.ko
version:        backported from Linux (v3.15-rc1-0-gc9eaa44) using backports v3.15-rc1-1-0-g2a25483
srcversion:     7F5DF7FC430B6F41B27560E
depends:        compat
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

[compat]
filename:       /lib/modules/3.13.0-24-generic/updates/compat/compat.ko
version:        backported from Linux (v3.15-rc1-0-gc9eaa44) using backports v3.15-rc1-1-0-g2a25483
srcversion:     0B4E75B519E5E2015024D8D
depends:        
parm:           backported_kernel_name:The kernel tree name that was used for this backport (Linux) (charp)
parm:           backported_kernel_version:The kernel version that was used for this backport (v3.15-rc1-0-gc9eaa44) (charp)
parm:           backports_version:The git version of the backports tree used to generate this backport (v3.15-rc1-1-0-g2a25483) (charp)


udev rules ~~~~~~~~~~~~~~~~~~~~~~~~~

# PCI device 0x8086:0x103d (e100)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC eth0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

# PCI device 0x168c:0x0013 (ath5k)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC wlan0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"


Custom files/entries ~~~~~~~~~~~~~~~

/etc/modules        : Default
/etc/rc.local       : Default
/etc/modprobe.d     : Not Default
/etc/pm/(cnf|pw|sl) : Default

[/etc/modprobe.d]
ath5k.conf        : options ath5k nohwcrypt=Y
iwlwifi.conf      : remove iwlwifi \
                    (/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
                    && /sbin/modprobe -r mac80211
mlx4.conf         : softdep mlx4_core post: mlx4_en


Kernel boot line ~~~~~~~~~~~~~~~~~~~

BOOT_IMAGE=/boot/vmlinuz-3.13.0-24-generic root=UUID=81bc7e59-c4de-4579-b806-10d68a6ed598 ro quiet splash vt.handoff=7


dmesg ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

[    0.905505] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[    0.906282] audit: initializing netlink socket (disabled)
[   20.761466] wmi: Mapper loaded
[   22.824223] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   27.798592] ath5k 0000:02:00.0: enabling device (0000 -> 0002)
[   27.798847] ath5k 0000:02:00.0: registered as 'phy0'
[   28.849902] ath: EEPROM regdomain: 0x0
[   28.849912] ath: EEPROM indicates default country code should be used
[   28.849914] ath: doing EEPROM country->regdmn map search
[   28.849917] ath: country maps to regdmn code: 0x3a
[   28.849920] ath: Country alpha2 being used: US
[   28.849922] ath: Regpair used: 0x3a
[   28.991552] ath5k: phy0: Atheros AR2414 chip found (MAC: 0x79, PHY: 0x45)
[   29.408834] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   29.411105] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  810.385003] wlan0: authenticate with <MAC C-02 T1tb0fW95>
[  810.396070] wlan0: send auth to <MAC C-02 T1tb0fW95> (try 1/3)
[  810.397784] wlan0: authenticated
[  810.400746] ath5k 0000:02:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[  810.400757] ath5k 0000:02:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[  810.404502] wlan0: associate with <MAC C-02 T1tb0fW95> (try 1/3)
[  810.508069] wlan0: associate with <MAC C-02 T1tb0fW95> (try 2/3)
[  810.612060] wlan0: associate with <MAC C-02 T1tb0fW95> (try 3/3)
[  810.716090] wlan0: association with <MAC C-02 T1tb0fW95> timed out
[  811.483830] wlan0: authenticate with <MAC C-02 T1tb0fW95>
[  811.484814] wlan0: send auth to <MAC C-02 T1tb0fW95> (try 1/3)
[  811.487630] wlan0: authenticated
[  811.495436] ath5k 0000:02:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[  811.495448] ath5k 0000:02:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[  811.496484] wlan0: associate with <MAC C-02 T1tb0fW95> (try 1/3)
[  811.600069] wlan0: associate with <MAC C-02 T1tb0fW95> (try 2/3)
[  811.704070] wlan0: associate with <MAC C-02 T1tb0fW95> (try 3/3)
[  811.808065] wlan0: association with <MAC C-02 T1tb0fW95> timed out
[  812.980298] wlan0: authenticate with <MAC C-02 T1tb0fW95>
[  812.980512] wlan0: send auth to <MAC C-02 T1tb0fW95> (try 1/3)
[  812.985949] wlan0: authenticated
[  812.989869] ath5k 0000:02:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[  812.989882] ath5k 0000:02:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[  812.992488] wlan0: associate with <MAC C-02 T1tb0fW95> (try 1/3)
[  813.100063] wlan0: associate with <MAC C-02 T1tb0fW95> (try 2/3)
[  813.204067] wlan0: associate with <MAC C-02 T1tb0fW95> (try 3/3)
[  813.308065] wlan0: association with <MAC C-02 T1tb0fW95> timed out
[  814.976331] wlan0: authenticate with <MAC C-02 T1tb0fW95>
[  814.976983] wlan0: send auth to <MAC C-02 T1tb0fW95> (try 1/3)
[  814.978969] wlan0: authenticated
[  814.983773] ath5k 0000:02:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[  814.983785] ath5k 0000:02:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[  814.984522] wlan0: associate with <MAC C-02 T1tb0fW95> (try 1/3)
[  815.092104] wlan0: associate with <MAC C-02 T1tb0fW95> (try 2/3)
[  815.196099] wlan0: associate with <MAC C-02 T1tb0fW95> (try 3/3)
[  815.300064] wlan0: association with <MAC C-02 T1tb0fW95> timed out
[  826.636919] wlan0: authenticate with <MAC C-02 T1tb0fW95>
[  826.637585] wlan0: send auth to <MAC C-02 T1tb0fW95> (try 1/3)
[  826.641714] wlan0: authenticated
[  826.646974] ath5k 0000:02:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[  826.646985] ath5k 0000:02:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[  826.648113] wlan0: associate with <MAC C-02 T1tb0fW95> (try 1/3)
[  826.752071] wlan0: associate with <MAC C-02 T1tb0fW95> (try 2/3)
[  826.856064] wlan0: associate with <MAC C-02 T1tb0fW95> (try 3/3)
[  826.960067] wlan0: association with <MAC C-02 T1tb0fW95> timed out
[  851.651692] wlan0: authenticate with <MAC C-02 T1tb0fW95>
[  851.652854] wlan0: send auth to <MAC C-02 T1tb0fW95> (try 1/3)
[  851.654978] wlan0: authenticated
[  851.659859] ath5k 0000:02:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[  851.659871] ath5k 0000:02:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[  851.660529] wlan0: associate with <MAC C-02 T1tb0fW95> (try 1/3)
[  851.764068] wlan0: associate with <MAC C-02 T1tb0fW95> (try 2/3)
[  851.868069] wlan0: associate with <MAC C-02 T1tb0fW95> (try 3/3)
[  851.972064] wlan0: association with <MAC C-02 T1tb0fW95> timed out
[  862.641807] wlan0: authenticate with <MAC C-02 T1tb0fW95>
[  862.642015] wlan0: send auth to <MAC C-02 T1tb0fW95> (try 1/3)
[  862.645681] wlan0: authenticated
[  862.651020] ath5k 0000:02:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[  862.651032] ath5k 0000:02:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[  862.652485] wlan0: associate with <MAC C-02 T1tb0fW95> (try 1/3)
[  862.756067] wlan0: associate with <MAC C-02 T1tb0fW95> (try 2/3)
[  862.860069] wlan0: associate with <MAC C-02 T1tb0fW95> (try 3/3)
[  862.984068] wlan0: association with <MAC C-02 T1tb0fW95> timed out
[ 5532.706027] ath5k 0000:02:00.0: registered as 'phy1'
[ 5533.330308] ath: EEPROM regdomain: 0x0
[ 5533.330312] ath: EEPROM indicates default country code should be used
[ 5533.330312] ath: doing EEPROM country->regdmn map search
[ 5533.330335] ath: country maps to regdmn code: 0x3a
[ 5533.330337] ath: Country alpha2 being used: US
[ 5533.330338] ath: Regpair used: 0x3a
[ 5533.331791] ath5k: phy1: Atheros AR2414 chip found (MAC: 0x79, PHY: 0x45)
[ 5534.521357] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 5534.523448] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready

    ======== Done ========

```

---

### Post by varunendra on 2014-05-28
Hmm.. no more hints, no more ideas. The only things I can think of are -

**1)** The Ethernet is showing up as the interface currently in use. Like mentioned earlier, try the wifi interface after unplugging the Ethernet cable and rebooting (leave the cable unplugged).

**2)** Try an additional parameter with one of the helping drivers -
```
echo "options mac80211 probe_wait_ms=1000" | sudo tee /etc/modprobe.d/mac80211.conf
```
Reboot and see if it helps. If not, also try value '2000' with the same above command.

**3)** Check your router and see if there is an option "WMM" in it (usually it is under 'QoS' settings). If there is, make sure it is disabled. Reboot the router as always, if the change is made.

With these, I think I'm out of ideas already.

---

### Post by bill41 on 2014-05-28
I followed the first 2 suggestions but there was no change. Regarding the 3rd suggestion, my router (NetGear WGT624 v3) apparently doesn't support QoS, there isn't a 'WMM' option.

THANK YOU Varun. You are generous with your time and I have appreciated your assistance.

---

### Post by varunendra on 2014-05-30
I was suggested by my guru mr. chili555 almost immediately after my last post two more possibilities, I couldn't find time to post them here. So here they are now -

**1)** The device you have may be too old to support WPA2. So try older encryption types in the router, that is, WPA(1) or WEP.

**2)** Look into 'syslog' file for further clues. Particularly -
```
cat /var/log/syslog | grep -e wlan -e etwork
```

In case of no luck with different encryption, or no further hints, we have nothing more to add at least for now.

---

### Post by bill41 on 2014-05-31
I'm dual booting with Lubuntu and Win7 and the wireless card works ok on Win7 using WPA2. I think it originally only supported WEP but it's upgradable to WPA2 and I must have upgraded it. I tried WPA(1) and WEP anyway but it still wouldn't connect.

Switching back to WPA2, here are the results of the 2nd suggestion, just displaying the results from the last boot forward, trying to connect, and ethernet unplugged:
```

cat /var/log/syslog | grep -e wlan -e etwork

May 31 12:14:18 toshiba-a45-s120 kernel: [    1.838132] e100: Intel(R) PRO/100 Network Driver, 3.5.24-k2-NAPI
May 31 12:14:19 toshiba-a45-s120 kernel: [   23.199045] type=1400 audit(1401552859.268:6): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=437 comm="apparmor_parser"
May 31 12:14:19 toshiba-a45-s120 kernel: [   23.214323] type=1400 audit(1401552859.284:8): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=437 comm="apparmor_parser"
May 31 12:14:24 toshiba-a45-s120 NetworkManager[618]: <info> NetworkManager (version 0.9.8.8) is starting...
May 31 12:14:24 toshiba-a45-s120 NetworkManager[618]: <info> Read config file /etc/NetworkManager/NetworkManager.conf
May 31 12:14:24 toshiba-a45-s120 NetworkManager[618]: <info> WEXT support is enabled
May 31 12:14:24 toshiba-a45-s120 NetworkManager[618]: <info> DNS: loaded plugin dnsmasq
May 31 12:14:25 toshiba-a45-s120 kernel: [   28.986627] type=1400 audit(1401552865.056:16): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=653 comm="apparmor_parser"
May 31 12:14:25 toshiba-a45-s120 kernel: [   28.987864] type=1400 audit(1401552865.056:18): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=653 comm="apparmor_parser"
May 31 12:14:25 toshiba-a45-s120 NetworkManager[618]:    SCPlugin-Ifupdown: init!
May 31 12:14:25 toshiba-a45-s120 NetworkManager[618]:    SCPlugin-Ifupdown: update_system_hostname
May 31 12:14:25 toshiba-a45-s120 NetworkManager[618]:       interface-parser: parsing file /etc/network/interfaces
May 31 12:14:25 toshiba-a45-s120 NetworkManager[618]:       interface-parser: finished parsing file /etc/network/interfaces
May 31 12:14:25 toshiba-a45-s120 NetworkManager[618]:    SCPluginIfupdown: management mode: unmanaged
May 31 12:14:25 toshiba-a45-s120 NetworkManager[618]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:1e.0/0000:01:08.0/net/eth0, iface: eth0)
May 31 12:14:25 toshiba-a45-s120 NetworkManager[618]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:1e.0/0000:01:08.0/net/eth0, iface: eth0): no ifupdown configuration found.
May 31 12:14:25 toshiba-a45-s120 NetworkManager[618]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:1e.0/0000:01:0b.0/0000:02:00.0/net/wlan0, iface: wlan0)
May 31 12:14:25 toshiba-a45-s120 NetworkManager[618]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:1e.0/0000:01:0b.0/0000:02:00.0/net/wlan0, iface: wlan0): no ifupdown configuration found.
May 31 12:14:25 toshiba-a45-s120 NetworkManager[618]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/lo, iface: lo)
May 31 12:14:25 toshiba-a45-s120 NetworkManager[618]:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/lo, iface: lo): no ifupdown configuration found.
May 31 12:14:25 toshiba-a45-s120 NetworkManager[618]:    SCPlugin-Ifupdown: end _init.
May 31 12:14:25 toshiba-a45-s120 NetworkManager[618]: <info> Loaded plugin ifupdown: (C) 2008 Canonical Ltd.  To report bugs please use the NetworkManager mailing list.
May 31 12:14:25 toshiba-a45-s120 NetworkManager[618]: <info> Loaded plugin keyfile: (c) 2007 - 2010 Red Hat, Inc.  To report bugs please use the NetworkManager mailing list.
May 31 12:14:25 toshiba-a45-s120 NetworkManager[618]:    SCPlugin-Ofono: Acquired D-Bus service com.canonical.NMOfono
May 31 12:14:25 toshiba-a45-s120 NetworkManager[618]:    SCPlugin-Ofono: init!
May 31 12:14:25 toshiba-a45-s120 NetworkManager[618]:    SCPlugin-Ofono: end _init.
May 31 12:14:25 toshiba-a45-s120 NetworkManager[618]: <info> Loaded plugin (null): (null)
May 31 12:14:25 toshiba-a45-s120 NetworkManager[618]:    Ifupdown: get unmanaged devices count: 0
May 31 12:14:25 toshiba-a45-s120 NetworkManager[618]:    SCPlugin-Ifupdown: (156908384) ... get_connections.
May 31 12:14:25 toshiba-a45-s120 NetworkManager[618]:    SCPlugin-Ifupdown: (156908384) ... get_connections (managed=false): return empty list.
May 31 12:14:25 toshiba-a45-s120 NetworkManager[618]:    SCPlugin-Ofono: (156765840) ... get_connections.
May 31 12:14:25 toshiba-a45-s120 NetworkManager[618]:    SCPlugin-Ofono: (156765840) connections count: 0
May 31 12:14:25 toshiba-a45-s120 NetworkManager[618]:    Ifupdown: get unmanaged devices count: 0
May 31 12:14:25 toshiba-a45-s120 NetworkManager[618]: <info> monitoring kernel firmware directory '/lib/firmware'.
May 31 12:14:25 toshiba-a45-s120 NetworkManager[618]: <info> rfkill0: found WiFi radio killswitch (at /sys/devices/pci0000:00/0000:00:1e.0/0000:01:0b.0/0000:02:00.0/ieee80211/phy0/rfkill0) (driver ath5k)
May 31 12:14:25 toshiba-a45-s120 NetworkManager[618]: <info> WiFi enabled by radio killswitch; enabled by state file
May 31 12:14:25 toshiba-a45-s120 NetworkManager[618]: <info> WWAN enabled by radio killswitch; enabled by state file
May 31 12:14:25 toshiba-a45-s120 NetworkManager[618]: <info> WiMAX enabled by radio killswitch; enabled by state file
May 31 12:14:25 toshiba-a45-s120 NetworkManager[618]: <info> Networking is enabled by state file
May 31 12:14:25 toshiba-a45-s120 NetworkManager[618]: <warn> failed to allocate link cache: (-12) Object not found
May 31 12:14:25 toshiba-a45-s120 NetworkManager[618]: <info> (eth0): carrier is OFF
May 31 12:14:25 toshiba-a45-s120 NetworkManager[618]: <info> (eth0): new Ethernet device (driver: 'e100' ifindex: 2)
May 31 12:14:25 toshiba-a45-s120 NetworkManager[618]: <info> (eth0): exported as /org/freedesktop/NetworkManager/Devices/0
May 31 12:14:25 toshiba-a45-s120 NetworkManager[618]: <info> (eth0): device state change: unmanaged -> unavailable (reason 'managed') [10 20 2]
May 31 12:14:25 toshiba-a45-s120 NetworkManager[618]: <info> (eth0): bringing up device.
May 31 12:14:25 toshiba-a45-s120 NetworkManager[618]: <info> (eth0): preparing device.
May 31 12:14:25 toshiba-a45-s120 NetworkManager[618]: <info> (eth0): deactivating device (reason 'managed') [2]
May 31 12:14:25 toshiba-a45-s120 NetworkManager[618]: <info> Added default wired connection 'Wired connection 1' for /sys/devices/pci0000:00/0000:00:1e.0/0000:01:08.0/net/eth0
May 31 12:14:25 toshiba-a45-s120 NetworkManager[618]: <info> (wlan0): using nl80211 for WiFi device control
May 31 12:14:25 toshiba-a45-s120 NetworkManager[618]: <info> (wlan0): driver supports Access Point (AP) mode
May 31 12:14:25 toshiba-a45-s120 NetworkManager[618]: <info> (wlan0): new 802.11 WiFi device (driver: 'ath5k' ifindex: 3)
May 31 12:14:25 toshiba-a45-s120 NetworkManager[618]: <info> (wlan0): exported as /org/freedesktop/NetworkManager/Devices/1
May 31 12:14:25 toshiba-a45-s120 NetworkManager[618]: <info> (wlan0): device state change: unmanaged -> unavailable (reason 'managed') [10 20 2]
May 31 12:14:25 toshiba-a45-s120 NetworkManager[618]: <info> (wlan0): bringing up device.
May 31 12:14:25 toshiba-a45-s120 NetworkManager[618]: <info> (wlan0): preparing device.
May 31 12:14:25 toshiba-a45-s120 kernel: [   29.853648] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
May 31 12:14:25 toshiba-a45-s120 NetworkManager[618]: <info> (wlan0): deactivating device (reason 'managed') [2]
May 31 12:14:25 toshiba-a45-s120 kernel: [   29.857127] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
May 31 12:14:25 toshiba-a45-s120 NetworkManager[618]: <warn> /sys/devices/virtual/net/lo: couldn't determine device driver; ignoring...
May 31 12:14:25 toshiba-a45-s120 NetworkManager[618]: <warn> /sys/devices/virtual/net/lo: couldn't determine device driver; ignoring...
May 31 12:14:26 toshiba-a45-s120 NetworkManager[618]: <info> urfkill disappeared from the bus
May 31 12:14:26 toshiba-a45-s120 NetworkManager[618]: <info> ModemManager available in the bus
May 31 12:14:26 toshiba-a45-s120 NetworkManager[618]: <info> wpa_supplicant started
May 31 12:14:26 toshiba-a45-s120 NetworkManager[618]: <info> (wlan0) supports 4 scan SSIDs
May 31 12:14:26 toshiba-a45-s120 NetworkManager[618]: <warn> Trying to remove a non-existant call id.
May 31 12:14:26 toshiba-a45-s120 NetworkManager[618]: <info> (wlan0): supplicant interface state: starting -> ready
May 31 12:14:26 toshiba-a45-s120 NetworkManager[618]: <info> (wlan0): device state change: unavailable -> disconnected (reason 'supplicant-available') [20 30 42]
May 31 12:14:26 toshiba-a45-s120 wpa_supplicant[697]: wlan0: CTRL-EVENT-SCAN-STARTED 
May 31 12:14:26 toshiba-a45-s120 NetworkManager[618]: <info> (wlan0): supplicant interface state: ready -> disconnected
May 31 12:14:26 toshiba-a45-s120 wpa_supplicant[697]: wlan0: Reject scan trigger since one is already pending
May 31 12:14:26 toshiba-a45-s120 NetworkManager[618]: <info> (wlan0) supports 4 scan SSIDs
May 31 12:14:26 toshiba-a45-s120 NetworkManager[618]: <info> (wlan0): supplicant interface state: disconnected -> inactive
May 31 12:14:36 toshiba-a45-s120 NetworkManager[618]: <info> WiFi hardware radio set enabled
May 31 12:14:49 toshiba-a45-s120 wpa_supplicant[697]: wlan0: CTRL-EVENT-SCAN-STARTED 
May 31 12:15:18 toshiba-a45-s120 NetworkManager[618]: <info> Activation (wlan0) starting connection 'T1tb0fW95'
May 31 12:15:18 toshiba-a45-s120 NetworkManager[618]: <info> (wlan0): device state change: disconnected -> prepare (reason 'none') [30 40 0]
May 31 12:15:18 toshiba-a45-s120 NetworkManager[618]: <info> NetworkManager state is now CONNECTING
May 31 12:15:18 toshiba-a45-s120 NetworkManager[618]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
May 31 12:15:18 toshiba-a45-s120 NetworkManager[618]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
May 31 12:15:18 toshiba-a45-s120 NetworkManager[618]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
May 31 12:15:18 toshiba-a45-s120 NetworkManager[618]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
May 31 12:15:18 toshiba-a45-s120 NetworkManager[618]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
May 31 12:15:18 toshiba-a45-s120 NetworkManager[618]: <info> (wlan0): device state change: prepare -> config (reason 'none') [40 50 0]
May 31 12:15:18 toshiba-a45-s120 NetworkManager[618]: <info> Activation (wlan0/wireless): access point 'T1tb0fW95' has security, but secrets are required.
May 31 12:15:18 toshiba-a45-s120 NetworkManager[618]: <info> (wlan0): device state change: config -> need-auth (reason 'none') [50 60 0]
May 31 12:15:18 toshiba-a45-s120 NetworkManager[618]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
May 31 12:15:35 toshiba-a45-s120 NetworkManager[618]: get_secret_flags: assertion 'is_secret_prop (setting, secret_name, error)' failed
May 31 12:15:35 toshiba-a45-s120 NetworkManager[618]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
May 31 12:15:35 toshiba-a45-s120 NetworkManager[618]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
May 31 12:15:35 toshiba-a45-s120 NetworkManager[618]: <info> (wlan0): device state change: need-auth -> prepare (reason 'none') [60 40 0]
May 31 12:15:35 toshiba-a45-s120 NetworkManager[618]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
May 31 12:15:35 toshiba-a45-s120 NetworkManager[618]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
May 31 12:15:35 toshiba-a45-s120 NetworkManager[618]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
May 31 12:15:35 toshiba-a45-s120 NetworkManager[618]: <info> (wlan0): device state change: prepare -> config (reason 'none') [40 50 0]
May 31 12:15:35 toshiba-a45-s120 NetworkManager[618]: <info> Activation (wlan0/wireless): connection 'T1tb0fW95' has security, and secrets exist.  No new secrets needed.
May 31 12:15:35 toshiba-a45-s120 NetworkManager[618]: <info> Config: added 'ssid' value 'T1tb0fW95'
May 31 12:15:35 toshiba-a45-s120 NetworkManager[618]: <info> Config: added 'scan_ssid' value '1'
May 31 12:15:35 toshiba-a45-s120 NetworkManager[618]: <info> Config: added 'key_mgmt' value 'WPA-PSK'
May 31 12:15:35 toshiba-a45-s120 NetworkManager[618]: <info> Config: added 'auth_alg' value 'OPEN'
May 31 12:15:35 toshiba-a45-s120 NetworkManager[618]: <info> Config: added 'psk' value '<omitted>'
May 31 12:15:35 toshiba-a45-s120 NetworkManager[618]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
May 31 12:15:35 toshiba-a45-s120 NetworkManager[618]: <info> Config: set interface ap_scan to 1
May 31 12:15:35 toshiba-a45-s120 NetworkManager[618]: <info> (wlan0): supplicant interface state: inactive -> scanning
May 31 12:15:35 toshiba-a45-s120 wpa_supplicant[697]: wlan0: CTRL-EVENT-SCAN-STARTED 
May 31 12:15:36 toshiba-a45-s120 wpa_supplicant[697]: wlan0: SME: Trying to authenticate with <MAC ID removed> (SSID='T1tb0fW95' freq=2462 MHz)
May 31 12:15:36 toshiba-a45-s120 kernel: [  100.105370] wlan0: authenticate with <MAC ID removed>
May 31 12:15:36 toshiba-a45-s120 kernel: [  100.114181] wlan0: send auth to <MAC ID removed> (try 1/3)
May 31 12:15:36 toshiba-a45-s120 kernel: [  100.115841] wlan0: authenticated
May 31 12:15:36 toshiba-a45-s120 wpa_supplicant[697]: wlan0: Trying to associate with <MAC ID removed> (SSID='T1tb0fW95' freq=2462 MHz)
May 31 12:15:36 toshiba-a45-s120 NetworkManager[618]: <info> (wlan0): supplicant interface state: scanning -> authenticating
May 31 12:15:36 toshiba-a45-s120 kernel: [  100.122003] ath5k 0000:02:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
May 31 12:15:36 toshiba-a45-s120 kernel: [  100.122016] ath5k 0000:02:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
May 31 12:15:36 toshiba-a45-s120 kernel: [  100.124487] wlan0: associate with <MAC ID removed> (try 1/3)
May 31 12:15:36 toshiba-a45-s120 NetworkManager[618]: <info> (wlan0): supplicant interface state: authenticating -> associating
May 31 12:15:36 toshiba-a45-s120 kernel: [  100.228069] wlan0: associate with <MAC ID removed> (try 2/3)
May 31 12:15:36 toshiba-a45-s120 kernel: [  100.332074] wlan0: associate with <MAC ID removed> (try 3/3)
May 31 12:15:36 toshiba-a45-s120 kernel: [  100.436065] wlan0: association with <MAC ID removed> timed out
May 31 12:15:36 toshiba-a45-s120 NetworkManager[618]: <info> (wlan0): supplicant interface state: associating -> disconnected
May 31 12:15:36 toshiba-a45-s120 wpa_supplicant[697]: wlan0: CTRL-EVENT-SCAN-STARTED 
May 31 12:15:36 toshiba-a45-s120 NetworkManager[618]: <info> (wlan0): supplicant interface state: disconnected -> scanning
May 31 12:15:37 toshiba-a45-s120 wpa_supplicant[697]: wlan0: SME: Trying to authenticate with <MAC ID removed> (SSID='T1tb0fW95' freq=2462 MHz)
May 31 12:15:37 toshiba-a45-s120 kernel: [  101.209263] wlan0: authenticate with <MAC ID removed>
May 31 12:15:37 toshiba-a45-s120 kernel: [  101.209470] wlan0: send auth to <MAC ID removed> (try 1/3)
May 31 12:15:37 toshiba-a45-s120 kernel: [  101.211558] wlan0: authenticated
May 31 12:15:37 toshiba-a45-s120 wpa_supplicant[697]: wlan0: Trying to associate with <MAC ID removed> (SSID='T1tb0fW95' freq=2462 MHz)
May 31 12:15:37 toshiba-a45-s120 NetworkManager[618]: <info> (wlan0): supplicant interface state: scanning -> authenticating
May 31 12:15:37 toshiba-a45-s120 kernel: [  101.217112] ath5k 0000:02:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
May 31 12:15:37 toshiba-a45-s120 kernel: [  101.217124] ath5k 0000:02:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
May 31 12:15:37 toshiba-a45-s120 kernel: [  101.220474] wlan0: associate with <MAC ID removed> (try 1/3)
May 31 12:15:37 toshiba-a45-s120 NetworkManager[618]: <info> (wlan0): supplicant interface state: authenticating -> associating
May 31 12:15:37 toshiba-a45-s120 kernel: [  101.324068] wlan0: associate with <MAC ID removed> (try 2/3)
May 31 12:15:37 toshiba-a45-s120 kernel: [  101.428067] wlan0: associate with <MAC ID removed> (try 3/3)
May 31 12:15:37 toshiba-a45-s120 kernel: [  101.540064] wlan0: association with <MAC ID removed> timed out
May 31 12:15:37 toshiba-a45-s120 NetworkManager[618]: <info> (wlan0): supplicant interface state: associating -> disconnected
May 31 12:15:38 toshiba-a45-s120 wpa_supplicant[697]: wlan0: CTRL-EVENT-SCAN-STARTED 
May 31 12:15:38 toshiba-a45-s120 NetworkManager[618]: <info> (wlan0): supplicant interface state: disconnected -> scanning
May 31 12:15:38 toshiba-a45-s120 wpa_supplicant[697]: wlan0: SME: Trying to authenticate with <MAC ID removed> (SSID='T1tb0fW95' freq=2462 MHz)
May 31 12:15:38 toshiba-a45-s120 kernel: [  102.712534] wlan0: authenticate with <MAC ID removed>
May 31 12:15:38 toshiba-a45-s120 kernel: [  102.712742] wlan0: send auth to <MAC ID removed> (try 1/3)
May 31 12:15:38 toshiba-a45-s120 kernel: [  102.714311] wlan0: authenticated
May 31 12:15:38 toshiba-a45-s120 wpa_supplicant[697]: wlan0: Trying to associate with <MAC ID removed> (SSID='T1tb0fW95' freq=2462 MHz)
May 31 12:15:38 toshiba-a45-s120 kernel: [  102.719778] ath5k 0000:02:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
May 31 12:15:38 toshiba-a45-s120 kernel: [  102.719790] ath5k 0000:02:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
May 31 12:15:38 toshiba-a45-s120 NetworkManager[618]: <info> (wlan0): supplicant interface state: scanning -> authenticating
May 31 12:15:38 toshiba-a45-s120 kernel: [  102.720448] wlan0: associate with <MAC ID removed> (try 1/3)
May 31 12:15:38 toshiba-a45-s120 NetworkManager[618]: <info> (wlan0): supplicant interface state: authenticating -> associating
May 31 12:15:38 toshiba-a45-s120 kernel: [  102.824070] wlan0: associate with <MAC ID removed> (try 2/3)
May 31 12:15:39 toshiba-a45-s120 kernel: [  102.932068] wlan0: associate with <MAC ID removed> (try 3/3)
May 31 12:15:39 toshiba-a45-s120 kernel: [  103.036065] wlan0: association with <MAC ID removed> timed out
May 31 12:15:39 toshiba-a45-s120 NetworkManager[618]: <info> (wlan0): supplicant interface state: associating -> disconnected
May 31 12:15:40 toshiba-a45-s120 wpa_supplicant[697]: wlan0: CTRL-EVENT-SCAN-STARTED 
May 31 12:15:40 toshiba-a45-s120 NetworkManager[618]: <info> (wlan0): supplicant interface state: disconnected -> scanning
May 31 12:15:40 toshiba-a45-s120 wpa_supplicant[697]: wlan0: SME: Trying to authenticate with <MAC ID removed> (SSID='T1tb0fW95' freq=2462 MHz)
May 31 12:15:40 toshiba-a45-s120 kernel: [  104.704687] wlan0: authenticate with <MAC ID removed>
May 31 12:15:40 toshiba-a45-s120 kernel: [  104.704894] wlan0: send auth to <MAC ID removed> (try 1/3)
May 31 12:15:40 toshiba-a45-s120 NetworkManager[618]: <info> (wlan0): supplicant interface state: scanning -> authenticating
May 31 12:15:40 toshiba-a45-s120 kernel: [  104.710332] wlan0: authenticated
May 31 12:15:40 toshiba-a45-s120 wpa_supplicant[697]: wlan0: Trying to associate with <MAC ID removed> (SSID='T1tb0fW95' freq=2462 MHz)
May 31 12:15:40 toshiba-a45-s120 kernel: [  104.717120] ath5k 0000:02:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
May 31 12:15:40 toshiba-a45-s120 kernel: [  104.717133] ath5k 0000:02:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
May 31 12:15:40 toshiba-a45-s120 kernel: [  104.720103] wlan0: associate with <MAC ID removed> (try 1/3)
May 31 12:15:40 toshiba-a45-s120 NetworkManager[618]: <info> (wlan0): supplicant interface state: authenticating -> associating
May 31 12:15:40 toshiba-a45-s120 kernel: [  104.824069] wlan0: associate with <MAC ID removed> (try 2/3)
May 31 12:15:41 toshiba-a45-s120 kernel: [  104.932067] wlan0: associate with <MAC ID removed> (try 3/3)
May 31 12:15:41 toshiba-a45-s120 wpa_supplicant[697]: wlan0: CTRL-EVENT-SSID-TEMP-DISABLED id=0 ssid="T1tb0fW95" auth_failures=1 duration=10
May 31 12:15:41 toshiba-a45-s120 kernel: [  105.036064] wlan0: association with <MAC ID removed> timed out
May 31 12:15:41 toshiba-a45-s120 NetworkManager[618]: <info> (wlan0): supplicant interface state: associating -> disconnected
May 31 12:15:46 toshiba-a45-s120 wpa_supplicant[697]: wlan0: CTRL-EVENT-SCAN-STARTED 
May 31 12:15:46 toshiba-a45-s120 NetworkManager[618]: <info> (wlan0): supplicant interface state: disconnected -> scanning
May 31 12:15:51 toshiba-a45-s120 wpa_supplicant[697]: wlan0: CTRL-EVENT-SCAN-STARTED 
May 31 12:15:52 toshiba-a45-s120 wpa_supplicant[697]: wlan0: CTRL-EVENT-SSID-REENABLED id=0 ssid="T1tb0fW95"
May 31 12:15:52 toshiba-a45-s120 wpa_supplicant[697]: wlan0: SME: Trying to authenticate with <MAC ID removed> (SSID='T1tb0fW95' freq=2462 MHz)
May 31 12:15:52 toshiba-a45-s120 kernel: [  116.369591] wlan0: authenticate with <MAC ID removed>
May 31 12:15:52 toshiba-a45-s120 kernel: [  116.372770] wlan0: send auth to <MAC ID removed> (try 1/3)
May 31 12:15:52 toshiba-a45-s120 NetworkManager[618]: <info> (wlan0): supplicant interface state: scanning -> authenticating
May 31 12:15:52 toshiba-a45-s120 wpa_supplicant[697]: wlan0: Trying to associate with <MAC ID removed> (SSID='T1tb0fW95' freq=2462 MHz)
May 31 12:15:52 toshiba-a45-s120 kernel: [  116.380461] wlan0: authenticated
May 31 12:15:52 toshiba-a45-s120 kernel: [  116.382717] ath5k 0000:02:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
May 31 12:15:52 toshiba-a45-s120 kernel: [  116.382729] ath5k 0000:02:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
May 31 12:15:52 toshiba-a45-s120 kernel: [  116.384492] wlan0: associate with <MAC ID removed> (try 1/3)
May 31 12:15:52 toshiba-a45-s120 NetworkManager[618]: <info> (wlan0): supplicant interface state: authenticating -> associating
May 31 12:15:52 toshiba-a45-s120 kernel: [  116.488066] wlan0: associate with <MAC ID removed> (try 2/3)
May 31 12:15:52 toshiba-a45-s120 kernel: [  116.592067] wlan0: associate with <MAC ID removed> (try 3/3)
May 31 12:15:52 toshiba-a45-s120 wpa_supplicant[697]: wlan0: CTRL-EVENT-SSID-TEMP-DISABLED id=0 ssid="T1tb0fW95" auth_failures=2 duration=20
May 31 12:15:52 toshiba-a45-s120 kernel: [  116.696064] wlan0: association with <MAC ID removed> timed out
May 31 12:15:52 toshiba-a45-s120 NetworkManager[618]: <info> (wlan0): supplicant interface state: associating -> disconnected
May 31 12:16:01 toshiba-a45-s120 NetworkManager[618]: <warn> Activation (wlan0/wireless): association took too long.
May 31 12:16:01 toshiba-a45-s120 NetworkManager[618]: <info> (wlan0): device state change: config -> need-auth (reason 'none') [50 60 0]
May 31 12:16:01 toshiba-a45-s120 NetworkManager[618]: <warn> Activation (wlan0/wireless): asking for new secrets
May 31 12:16:02 toshiba-a45-s120 NetworkManager[618]: <info> (wlan0): supplicant interface state: disconnected -> inactive
May 31 12:16:11 toshiba-a45-s120 NetworkManager[618]: <warn> No agents were available for this request.
May 31 12:16:11 toshiba-a45-s120 NetworkManager[618]: <info> (wlan0): device state change: need-auth -> failed (reason 'no-secrets') [60 120 7]
May 31 12:16:11 toshiba-a45-s120 NetworkManager[618]: <info> NetworkManager state is now DISCONNECTED
May 31 12:16:11 toshiba-a45-s120 NetworkManager[618]: <info> Marking connection 'T1tb0fW95' invalid.
May 31 12:16:11 toshiba-a45-s120 NetworkManager[618]: <warn> Activation (wlan0) failed for connection 'T1tb0fW95'
May 31 12:16:11 toshiba-a45-s120 NetworkManager[618]: <info> (wlan0): device state change: failed -> disconnected (reason 'none') [120 30 0]
May 31 12:16:11 toshiba-a45-s120 NetworkManager[618]: <info> (wlan0): deactivating device (reason 'none') [0]
May 31 12:16:11 toshiba-a45-s120 wpa_supplicant[697]: wlan0: CTRL-EVENT-SCAN-STARTED 
bill@toshiba-a45-s120:~$ 

```
Thanks again.

---

