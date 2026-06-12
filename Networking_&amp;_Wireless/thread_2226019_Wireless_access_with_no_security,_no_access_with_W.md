---
title: "Wireless access with no security, no access with WPA set"
date: 2014-05-24
forum: Networking &amp; Wireless
---

### Post by radloui on 2014-05-24
I have reviewed the posts in this part of the forum for answers to my issue.  Running Ubuntu 12.04 LTS on a Dell Inspiron E1505 laptop. Wireless card has a Broadcom BCM 4311 chip set. Been using Ubuntu since 2006. In the early days I used ndwrapper and a broadcom driver to get the wireless adapter to work. With 12.04 LTS I have had no issues until recently.

I can access the net on my router (Linksys E2500) using the guest account with no security set. Unable to get to the net using the standard account which has security set at WPA & WPA2 Personal.

I ran the recommended wireless script and the results are below.

```


########## wireless info START ##########


##### release #####


Distributor ID:    Ubuntu
Description:    Ubuntu 12.04.4 LTS
Release:    12.04
Codename:    precise


##### kernel #####


Linux spock 3.2.0-61-generic-pae #93-Ubuntu SMP Fri May 2 21:46:08 UTC 2014 i686 i686 i386 GNU/Linux


##### lspci #####


03:00.0 Ethernet controller [0200]: Broadcom Corporation BCM4401-B0 100Base-TX [14e4:170c] (rev 02)
    Subsystem: Dell Inspiron 6400 [1028:01af]
    Kernel driver in use: b44


0b:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311] (rev 01)
    Subsystem: Dell Wireless 1390 WLAN Mini-Card [1028:0007]
    Kernel driver in use: b43-pci-bridge


##### lsusb #####


Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 046d:c018 Logitech, Inc. Optical Wheel Mouse
Bus 005 Device 002: ID 413c:8103 Dell Computer Corp. Wireless 350 Bluetooth


##### PCMCIA Card Info #####


##### rfkill #####


0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
1: dell-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: no
2: dell-bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no
3: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no


##### iw reg get #####


country 00:
    (2402 - 2472 @ 40), (3, 20)
    (2457 - 2482 @ 20), (3, 20), PASSIVE-SCAN, NO-IBSS
    (2474 - 2494 @ 20), (3, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
    (5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS


##### interfaces #####


auto lo
iface lo inet loopback


##### iwconfig #####


wlan0     IEEE 802.11bg  ESSID:"raddecay"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: <MAC address removed>   
          Bit Rate=54 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=70/70  Signal level=-40 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:6  Invalid misc:65   Missed beacon:0


##### route #####


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 eth1
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 wlan0
192.168.1.0     0.0.0.0         255.255.255.0   U     1      0        0 eth1
192.168.1.0     0.0.0.0         255.255.255.0   U     2      0        0 wlan0


##### resolv.conf #####


nameserver 127.0.0.1
search roc.mn.charter.com


##### nm-tool #####


NetworkManager Tool


State: connected (global)


- Device: eth1  [Wired connection 1] -------------------------------------------
  Type:              Wired
  Driver:            b44
  State:             connected
  Default:           yes
  HW Address:        <MAC address removed>


  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s


  Wired Properties
    Carrier:         on


  IPv4 Settings:
    Address:         192.168.1.144
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1


    DNS:             24.159.193.40
    DNS:             24.205.224.36
    DNS:             68.190.192.35


- Device: wlan0  [raddecay] ----------------------------------------------------
  Type:              802.11 WiFi
  Driver:            b43
  State:             connected
  Default:           no
  HW Address:        <MAC address removed>


  Capabilities:
    Speed:           54 Mb/s


  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes


  Wireless Access Points (* = current AP)
    *raddecay:       Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 79 WPA2
    Ehlers4268:      Infra, <MAC address removed>, Freq 2422 MHz, Rate 54 Mb/s, Strength 79 WPA2
    Video_Link:      Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 75 WPA2
    CenturyLink0551: Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 74 WPA WPA2
    NETGEAR35:       Infra, <MAC address removed>, Freq 2417 MHz, Rate 54 Mb/s, Strength 70 WPA2
    TORTUGA:         Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 55 WPA2
    A-Squared:       Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 64 WPA2
    Taggaz:          Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 60 WPA2
    MyCharterWiFib8-2G: Infra, <MAC address removed>, Freq 2457 MHz, Rate 54 Mb/s, Strength 60 WPA2
    NETGEAR32:       Infra, <MAC address removed>, Freq 2452 MHz, Rate 54 Mb/s, Strength 59 WPA2
    NAS_EXT:         Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 55 WPA2
    NAS:             Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 55 WPA2
    Nighthawk 2.4_EXT: Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 54 WPA2
    Brr2359Spruce:   Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 54 WPA WPA2
    CenturyLink0034: Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 52 WPA WPA2
    Ackborn:         Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 50 WPA WPA2
    NETGEAR68:       Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 50 WPA2
    belkin.bfa:      Infra, <MAC address removed>, Freq 2452 MHz, Rate 54 Mb/s, Strength 47 WPA2
    belkin.de6:      Infra, <MAC address removed>, Freq 2417 MHz, Rate 54 Mb/s, Strength 45 WPA2
    Nighthawk 2.4:   Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 45 WPA WPA2
    NETGEAR79:       Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 45 WPA2
    belkin.8d0:      Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 49 WPA2
    raddecay-guest:  Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 89


  IPv4 Settings:
    Address:         192.168.1.146
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1


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
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=69/70  Signal level=-41 dBm  
                    Encryption key:on
                    ESSID:"raddecay"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000039d4304f
                    Extra: Last beacon: 0ms ago
                    IE: Unknown: 00087261646465636179
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030106
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1AFC181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1606001700000000000000000000000000000000000000
                    IE: Unknown: DD840050F204104A0001101044000102103B000103104700107C6151DF45802A980C0C9241BB38973D10210005436973636F1023000D4C696E6B7379732045323530301024000776312E302E30331042000234321054000800060050F20400011011000D4C696E6B73797320453235303010080002228C103C0001031049000600372A000120
                    IE: Unknown: DD090010180202F0040000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 02 - Address: <MAC address removed>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=70/70  Signal level=-40 dBm  
                    Encryption key:off
                    ESSID:"raddecay-guest"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000039ccea14
                    Extra: Last beacon: 480ms ago
                    IE: Unknown: 000E72616464656361792D6775657374
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030106
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1AFC181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1606001700000000000000000000000000000000000000
                    IE: Unknown: DD090010180202F0040000
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
          Current Frequency=2.437 GHz (Channel 6)


##### lsmod #####


b43                   342801  0 
mac80211              436493  1 b43
cfg80211              178877  2 b43,mac80211
bcma                   25651  1 b43
ssb                    50691  2 b43,b44


##### modinfo #####


filename:       /lib/modules/3.2.0-61-generic-pae/kernel/drivers/net/wireless/b43/b43.ko
firmware:       b43/ucode9.fw
firmware:       b43/ucode5.fw
firmware:       b43/ucode16_mimo.fw
firmware:       b43/ucode15.fw
firmware:       b43/ucode14.fw
firmware:       b43/ucode13.fw
firmware:       b43/ucode11.fw
license:        GPL
author:         Rafa&#322; Mi&#322;ecki
author:         Gábor Stefanik
author:         Michael Buesch
author:         Stefano Brivio
author:         Martin Langer
description:    Broadcom B43 wireless driver
srcversion:     86DC7EAD5064E99821DBACC
alias:          bcma:m04BFid0812rev1Dcl*
alias:          bcma:m04BFid0812rev18cl*
alias:          bcma:m04BFid0812rev17cl*
alias:          bcma:m04BFid0812rev11cl*
alias:          ssb:v4243id0812rev10*
alias:          ssb:v4243id0812rev0F*
alias:          ssb:v4243id0812rev0D*
alias:          ssb:v4243id0812rev0C*
alias:          ssb:v4243id0812rev0B*
alias:          ssb:v4243id0812rev0A*
alias:          ssb:v4243id0812rev09*
alias:          ssb:v4243id0812rev07*
alias:          ssb:v4243id0812rev06*
alias:          ssb:v4243id0812rev05*
depends:        ssb,mac80211,bcma,cfg80211
intree:         Y
vermagic:       3.2.0-61-generic-pae SMP mod_unload modversions 686 
parm:           bad_frames_preempt:enable(1) / disable(0) Bad Frames Preemption (int)
parm:           fwpostfix:Postfix for the .fw files to load. (string)
parm:           hwpctl:Enable hardware-side power control (default off) (int)
parm:           nohwcrypt:Disable hardware encryption. (int)
parm:           hwtkip:Enable hardware tkip. (int)
parm:           qos:Enable QOS support (default on) (int)
parm:           btcoex:Enable Bluetooth coexistence (default on) (int)
parm:           verbose:Log message verbosity: 0=error, 1=warn, 2=info(default), 3=debug (int)
parm:           pio:Use PIO accesses by default: 0=DMA, 1=PIO (int)


filename:       /lib/modules/3.2.0-61-generic-pae/kernel/drivers/bcma/bcma.ko
license:        GPL
description:    Broadcom's specific AMBA driver
srcversion:     722AA6B08A43CF879452476
alias:          pci:v000014E4d00004727sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004357sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004353sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004331sv*sd*bc*sc*i*
alias:          pci:v000014E4d00000576sv*sd*bc*sc*i*
depends:        
intree:         Y
vermagic:       3.2.0-61-generic-pae SMP mod_unload modversions 686 


filename:       /lib/modules/3.2.0-61-generic-pae/kernel/drivers/ssb/ssb.ko
license:        GPL
description:    Sonics Silicon Backplane driver
srcversion:     9F5D4A88A58D2831D296FA3
alias:          pci:v000014E4d0000432Bsv*sd*bc*sc*i*
alias:          pci:v000014E4d00004329sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004328sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004325sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004324sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004321sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004320sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004319sv*sd*bc*sc*i*
alias:          pci:v000014A4d00004318sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004318sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004315sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004312sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004311sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004307sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004306sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004301sv*sd*bc*sc*i*
depends:        
intree:         Y
vermagic:       3.2.0-61-generic-pae SMP mod_unload modversions 686 


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


[/etc/modprobe.d/blacklist-local.conf]
blacklist wl


##### udev rules #####


# PCI device 0x14e4:/sys/devices/pci0000:00/0000:00:1e.0/0000:03:00.0/ssb1:0 (b44)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"


# PCI device 0x14e4:/sys/devices/pci0000:00/0000:00:1c.0/0000:0b:00.0/ssb0:0 (b43-pci-bridge)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"


# PCI device 0x14e4:/sys/devices/pci0000:00/0000:00:1e.0/0000:03:00.0/ssb1:0 (b44)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth1"


##### dmesg #####


[    1.284598] b43-pci-bridge 0000:0b:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.284612] b43-pci-bridge 0000:0b:00.0: setting latency timer to 64
[    1.304150] ssb: Core 0 found: ChipCommon (cc 0x800, rev 0x11, vendor 0x4243)
[    1.304167] ssb: Core 1 found: IEEE 802.11 (cc 0x812, rev 0x0A, vendor 0x4243)
[    1.304181] ssb: Core 2 found: USB 1.1 Host (cc 0x817, rev 0x03, vendor 0x4243)
[    1.304191] ssb: Core 3 found: PCI-E (cc 0x820, rev 0x01, vendor 0x4243)
[    1.368144] ssb: Sonics Silicon Backplane found on PCI device 0000:0b:00.0
[    1.440064] ssb: Core 0 found: Fast Ethernet (cc 0x806, rev 0x07, vendor 0x4243)
[    1.440074] ssb: Core 1 found: V90 (cc 0x807, rev 0x03, vendor 0x4243)
[    1.440082] ssb: Core 2 found: PCI (cc 0x804, rev 0x0A, vendor 0x4243)
[    1.491331] ssb: Sonics Silicon Backplane found on PCI device 0000:03:00.0
[    1.509110] b44 ssb1:0: eth0: Broadcom 44xx/47xx 10/100 PCI ethernet driver <MAC address removed>
[   20.131975] b43-phy0: Broadcom 4311 WLAN found (core revision 10)
[   20.279556] Registered led device: b43-phy0::tx
[   20.279617] Registered led device: b43-phy0::rx
[   20.279681] Registered led device: b43-phy0::radio
[   21.020057] b43-phy0: Loading firmware version 666.2 (2011-02-23 01:15:07)
[   21.140910] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   21.142100] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   21.174354] ADDRCONF(NETDEV_UP): eth1: link is not ready
[   21.180266] ADDRCONF(NETDEV_UP): eth1: link is not ready
[   24.648090] wlan0: authenticate with <MAC address removed> (try 1)
[   24.649586] wlan0: authenticated
[   24.672116] wlan0: associate with <MAC address removed> (try 1)
[   24.674882] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=1)
[   24.674887] wlan0: associated
[   24.680440] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  704.000224] b44 ssb1:0: eth1: Link is up at 100 Mbps, full duplex
[  704.000232] b44 ssb1:0: eth1: Flow control is off for TX and off for RX
[  704.000698] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready


########## wireless info END ############

```

Thanks in advance for any help you can provide.

Tony

---

### Post by Hadaka on 2014-05-25
hi please do.
```
sudo rm /etc/udev/rules.d/70-persistent-net.rules
```
BOOT <_Mandatory
then do to set your country code which is currently not set,,
locate your country code...input of country code must be UPPERCASE
DE not de (Gremany)
```
cat /usr/share/zoneinfo/zone.tab
```
*Replace XX with YOUR country code.
```
sed -i 's/^REG.*=$/&XX/' /etc/default/crda
```
BOOT <_Mandatory
```
sudo iw reg set XX
```
BOOT<-Mandatory
to verify please do and post
```
cat /etc/default/crda
iw reg get
```
thanks.

---

### Post by radloui on 2014-05-25
Hadaka,
I followed your instructions, here is the code:

cat /etc/default/crda
```

# Set REGDOMAIN to a ISO/IEC 3166-1 alpha2 country code so that iw(8) may set
# the initial regulatory domain setting for IEEE 802.11 devices which operate
# on this system.
#
# Governments assert the right to regulate usage of radio spectrum within
# their respective territories so make sure you select a ISO/IEC 3166-1 alpha2
# country code suitable for your location or you may infringe on local
# legislature. See `/usr/share/zoneinfo/zone.tab' for a table of timezone
# descriptions containing ISO/IEC 3166-1 alpha2 country codes.


REGDOMAIN=US

```

iw reg get
```

country US:
        (2402 - 2472 @ 40), (3, 27)
        (5170 - 5250 @ 40), (3, 17)
        (5250 - 5330 @ 40), (3, 20), DFS
        (5490 - 5600 @ 40), (3, 20), DFS
        (5650 - 5710 @ 40), (3, 20), DFS
        (5735 - 5835 @ 40), (3, 30)

```

To help me learn more about Linux, why did I make changes? Part of the changes you directed deal with country code. What does deleting the file, [COLOR=#000000][FONT=Ubuntu Mono]/etc/udev/rules.d/70-persistent-net.rules, do?

Thanks for the quick reply and assitance,
Tony[/FONT][/COLOR]

---

### Post by Hadaka on 2014-05-25
Hi, adding the country code helps your internet
access direct your data better. deleteing the
 [COLOR=#000000][FONT=Ubuntu Mono]/etc/udev/rules.d/70-persistent-net.rules file
was to eliminate any confusion that might be caused
by you having 2 ethernet definitions on the same piece
of hardware.when that file is deleted it gets re-written
with the current and correct ethernet entries.

if your problem is solved,please mark this thread solves
thanks.
[/FONT][/COLOR]

---

### Post by radloui on 2014-05-25
Hadaka,
Thanks for the explanation. Issue still exists. I have access by Ethernet, I can see the wireless connection. I can access the internet using a guest account with no security. I cannot access the net using the main wireless account with WPA/WPA2 Personal security set.

Tony

---

### Post by Hadaka on 2014-05-25
your data dump shows you are attached and working
on the secure wpa2 connection...
```
Wireless Access Points (* = current AP)
    *raddecay:       Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 79 WPA2
```

---

### Post by radloui on 2014-05-26
> **Hadaka said:**
> your data dump shows you are attached and working
on the secure wpa2 connection...


Yep, I can see the router. I can access the net using the guest account by submitting a password at the router login page. I just cannot access the net using the standard router WPA account. I have reached out to the Linksys community to see if there is anything they know on their end. All my other devices (Windows 7 laptop, android tablet and DVD player) are able to access the net using the standard wireless account. 

Here is the iwlist <ssid> scan code dump. Could there be an issue with how Ubuntu communicates with the router's implementation of WPA?

```

wlan0     Scan completed :
          Cell 01 - Address: 20:AA:4B:32:8E:6F
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=67/70  Signal level=-43 dBm  
                    Encryption key:on
                    ESSID:"raddecay"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000c23fa9444
                    Extra: Last beacon: 104ms ago
                    IE: Unknown: 00087261646465636179
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030106
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1AFC181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1606001700000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F0101
                    IE: Unknown: DD840050F204104A0001101044000102103B000103104700107C6151DF45802A980C0C9241BB38973D10210005436973636F1023000D4C696E6B7379732045323530301024000776312E302E30331042000234321054000800060050F20400011011000D4C696E6B73797320453235303010080002228C103C0001031049000600372A000120
                    IE: Unknown: DD090010180203F0040000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00



```

---

