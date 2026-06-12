---
title: "wireless very slow"
date: 2014-04-30
forum: Networking &amp; Wireless
---

### Post by debroos on 2014-04-30
I have 12.04 running nicely on all fronts dual booted on an xp pc. I have just re-installed 12.04 on my eee pc netbook to try and fix an incredibly slow wireless feed.  The re-install has made no difference.  Youtube videos are choppy on full screen, where once they were fine and vimeo won't play at all, although they do on the pc. At the minute, the netbook is a metre away from the router, so distance isn't a factor.  Could anyone please give me some idea where to look to fix it.  I've seen umpteen threads from people with a similar problem, but there as many different answers, it seems, and I'm not sure which route to follow.  Many thanks :(

---

### Post by mörgæs on 2014-04-30
Please run the wireless script found in the sticky notes and post the results.

---

### Post by debroos on 2014-05-06
[FONT=arial]Thanks very much for your attention to this.   I was given one solution on the launchpad forum which seems to have fixed the problem.,  Vimeo videos on full screen still have AV out of sync, but only by a fraction of a second so I can live with that.  The solution came following a reboot after entering this line of code - "[COLOR=#333333]echo "options ath5k nohwcrypt=1" | sudo tee /etc/modprobe.[/COLOR][COLOR=#333333]d/ath5k-[/COLOR][COLOR=#333333]fix.conf > /dev/null". [SIZE=2] Doubtless it will mean something to you..

I regret I don't know where to find the sticky note within which is the wireless script you mentioned.  I've followed the two links at the foot of your message but I'm unable to find any wireless references there. [/SIZE][/COLOR][/FONT]

---

### Post by mörgæs on 2014-05-06
The sticky notes are the top threads here: 
[http://ubuntuforums.org/forumdisplay.php?f=336](http://ubuntuforums.org/forumdisplay.php?f=336)

Please mark the thread 'solved' using 'thread tools'.

---

### Post by debroos on 2014-05-07
Thanks for that - 'sticky notes' did ring bells but I couldn't locate the source of the sound.  I'll mark the thread solved straight away.  I ran the wireless script which came up with the following:-
```
 

########## wireless info START ##########


##### release #####


Distributor ID:	Ubuntu
Description:	Ubuntu 12.04.4 LTS
Release:	12.04
Codename:	precise


##### kernel #####


Linux ubuntu 3.11.0-20-generic #35~precise1-Ubuntu SMP Fri May 2 21:35:48 UTC 2014 i686 i686 i386 GNU/Linux


##### lspci #####


01:00.0 Ethernet controller [0200]: Qualcomm Atheros AR242x / AR542x Wireless Network Adapter (PCI-Express) [168c:001c] (rev 01)
	Subsystem: AzureWave AW-GE780 802.11bg Wireless Mini PCIe Card [1a3b:1026]
	Kernel driver in use: ath5k


03:00.0 Ethernet controller [0200]: Qualcomm Atheros AR8121/AR8113/AR8114 Gigabit or Fast Ethernet [1969:1026] (rev b0)
	Subsystem: ASUSTeK Computer Inc. Device [1043:8324]
	Kernel driver in use: ATL1E


##### lsusb #####


Bus 001 Device 003: ID 058f:6335 Alcor Micro Corp. SD/MMC Card Reader
Bus 001 Device 004: ID 04f2:b071 Chicony Electronics Co., Ltd 2.0M UVC Webcam / CNF7129
Bus 003 Device 002: ID 046d:c51b Logitech, Inc. V220 Cordless Optical Mouse for Notebooks
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


##### PCMCIA Card Info #####


##### rfkill #####


0: eeepc-wlan: Wireless LAN
	Soft blocked: no
	Hard blocked: no
1: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no


##### iw reg get #####


##### interfaces #####


# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback


##### iwconfig #####


wlan0     IEEE 802.11bg  ESSID:"kimbo"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: <MAC address removed>   
          Bit Rate=54 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=35/70  Signal level=-75 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:161   Missed beacon:0


##### route #####


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.0.1     0.0.0.0         UG    0      0        0 wlan0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 wlan0
192.168.0.0     0.0.0.0         255.255.255.0   U     2      0        0 wlan0


##### resolv.conf #####


nameserver 127.0.0.1


##### nm-tool #####


NetworkManager Tool


State: connected (global)


- Device: wlan0  [kimbo] -------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            ath5k
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
    BTHub4-F98P:     Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 47 WPA WPA2
    BTWifi-with-FON: Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 35
    *kimbo:          Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 43 WEP


  IPv4 Settings:
    Address:         192.168.0.7
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.0.1


    DNS:             192.168.0.1


- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            ATL1E
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
                    Quality=35/70  Signal level=-75 dBm  
                    Encryption key:on
                    ESSID:"kimbo"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 22 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000007849ac2af3
                    Extra: Last beacon: 20ms ago
                    IE: Unknown: 00056B696D626F
                    IE: Unknown: 010582848B962C
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0100
                    IE: Unknown: 32080C1218243048606C
          Cell 02 - Address: <MAC address removed>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=26/70  Signal level=-84 dBm  
                    Encryption key:off
                    ESSID:"BTWifi-with-FON"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000c8d82ce370
                    Extra: Last beacon: 20ms ago
                    IE: Unknown: 000F4254576966692D776974682D464F4E
                    IE: Unknown: 010482848B96
                    IE: Unknown: 030106
                    IE: Unknown: 0706474220010D12
                    IE: Unknown: 200100
                    IE: Unknown: 2A0100
                    IE: Unknown: 2D1A2C001EFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 32080C1218243048606C
                    IE: Unknown: 3D1606000400000000000000000000000000000000000000
                    IE: Unknown: 7F0100
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD050009860100
          Cell 03 - Address: <MAC address removed>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=26/70  Signal level=-84 dBm  
                    Encryption key:on
                    ESSID:"BTHub4-F98P"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000c8d82cf8d0
                    Extra: Last beacon: 20ms ago
                    IE: Unknown: 000B4254487562342D46393850
                    IE: Unknown: 010482848B96
                    IE: Unknown: 030106
                    IE: Unknown: 0706474220010D12
                    IE: Unknown: 200100
                    IE: Unknown: 2A0100
                    IE: Unknown: 2D1A2C001EFFFF000000000000000000000000000000000000000000
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32080C1218243048606C
                    IE: Unknown: 3D1606000400000000000000000000000000000000000000
                    IE: Unknown: 7F0100
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD050009860100
                    IE: Unknown: DD8E0050F204104A000110104400010210570001001041000100103B0001031047001081A89DFE576858A09381D341817413F110210002425410230005487562203410240009425420487562203441104200122B3036383334312B4E5133313734313433301054000800060050F204000110110010425420486F6D652048756220342E3041100800020084103C000101


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


ath5k                 141236  0 
ath                    19435  1 ath5k
mac80211              534922  1 ath5k
cfg80211              416271  3 ath5k,ath,mac80211


##### modinfo #####


filename:       /lib/modules/3.11.0-20-generic/kernel/drivers/net/wireless/ath/ath5k/ath5k.ko
license:        Dual BSD/GPL
description:    Support for 5xxx series of Atheros 802.11 wireless LAN cards.
author:         Nick Kossifidis
author:         Jiri Slaby
srcversion:     68167C5D7C0F1F5FF5D8D62
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
vermagic:       3.11.0-20-generic SMP mod_unload modversions 686 
parm:           nohwcrypt:Disable hardware encryption. (bool)
parm:           fastchanswitch:Enable fast channel switching for AR2413/AR5413 radios. (bool)
parm:           no_hw_rfkill_switch:Ignore the GPIO RFKill switch state (bool)


filename:       /lib/modules/3.11.0-20-generic/kernel/drivers/net/wireless/ath/ath.ko
license:        Dual BSD/GPL
description:    Shared library for Atheros wireless LAN cards.
author:         Atheros Communications
srcversion:     A890CDBC88E6EF28CD751DD
depends:        cfg80211
intree:         Y
vermagic:       3.11.0-20-generic SMP mod_unload modversions 686 


##### modules #####


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


# PCI device 0x1969:/sys/devices/pci0000:00/0000:00:1c.1/0000:03:00.0 (ATL1E)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"


# PCI device 0x168c:/sys/devices/pci0000:00/0000:00:1c.3/0000:01:00.0 (ath5k)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"


##### dmesg #####


[   19.567102] psmouse serio1: elantech: assuming hardware version 2 (with firmware version 0x020030)
[   21.221415] ath5k 0000:01:00.0: can't disable ASPM; OS doesn't have ASPM control
[   21.221442] ath5k 0000:01:00.0: enabling device (0000 -> 0002)
[   21.221679] ath5k 0000:01:00.0: registered as 'phy0'
[   21.850659] ath: EEPROM regdomain: 0x60
[   21.850663] ath: EEPROM indicates we should expect a direct regpair map
[   21.850668] ath: Country alpha2 being used: 00
[   21.850671] ath: Regpair used: 0x60
[   22.551039] ath5k: phy0: Atheros AR2425 chip found (MAC: 0xe2, PHY: 0x70)
[   28.438901] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   28.439772] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   31.893908] wlan0: authenticate with <MAC address removed>
[   31.902007] wlan0: send auth to <MAC address removed> (try 1/3)
[   31.904838] wlan0: authenticated
[   31.905844] ath5k 0000:01:00.0 wlan0: disabling HT/VHT due to WEP/TKIP use
[   31.905861] ath5k 0000:01:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[   31.905869] ath5k 0000:01:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[   31.908187] wlan0: associate with <MAC address removed> (try 1/3)
[   31.909979] wlan0: RX AssocResp from <MAC address removed> (capab=0x471 status=0 aid=3)
[   31.910781] wlan0: associated
[   31.910869] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready


########## wireless info END ############
```

---

