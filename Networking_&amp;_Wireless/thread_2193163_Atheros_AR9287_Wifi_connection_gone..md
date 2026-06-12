---
title: "Atheros AR9287: Wifi connection gone."
date: 2013-12-11
forum: Networking &amp; Wireless
---

### Post by Mark de J on 2013-12-11
Hello,

My Wifi connection is gone away on a random moment, I must restart my computer to get it back, is there a way to stop this?

---

### Post by Kirboosy on 2013-12-11
Is this something that just recently started or has Ubuntu always done this on your computer?

Also we will need more details on the computer. What version of Ubuntu are you running and what Wifi card does the computer have?

Hope that helps!
~Caboose

---

### Post by mörgæs on 2013-12-11
[http://ubuntuforums.org/showthread.php?t=1422475](http://ubuntuforums.org/showthread.php?t=1422475)

---

### Post by Mark de J on 2013-12-12
mark@mark:~$ lspci | grep Wireless
03:00.0 Network controller: Qualcomm Atheros AR9287 Wireless Network Adapter (PCI-Express) (rev 01)
mark@mark:~$ 
Wireless card.

I use Ubuntu 13.10 and solved the problem for now, network card was turned off and didn't get on.

---

### Post by varunendra on 2013-12-12
Please mark the thread as **[SOLVED]** now that it is.

If you need help with wireless again, please try the "wireless_script" from the link in my signature. It doesn't fix anything, but creates a detailed report that helps in getting better and to-the-point help. :)

---

### Post by Mark de J on 2013-12-12
Done, forgot it sorry. Will chek that link! ;)

---

### Post by Mark de J on 2013-12-12
Again my WiFi is again getting away... The test...
```


*************** info trace ***************


***** uname -a *****


Linux mark 3.11.0-14-generic #21-Ubuntu SMP Tue Nov 12 17:04:55 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux


***** lsb_release *****


Distributor ID:	Ubuntu
Description:	Ubuntu 13.10
Release:	13.10
Codename:	saucy


***** lspci *****


02:00.0 Ethernet controller [0200]: Broadcom Corporation NetLink BCM57785 Gigabit Ethernet PCIe [14e4:16b5] (rev 10)
	Subsystem: Acer Incorporated [ALI] Device [1025:0504]
	Kernel driver in use: tg3
--
03:00.0 Network controller [0280]: Qualcomm Atheros AR9287 Wireless Network Adapter (PCI-Express) [168c:002e] (rev 01)
	Subsystem: Foxconn International, Inc. Device [105b:e034]
	Kernel driver in use: ath9k


***** lsusb *****


Bus 002 Device 003: ID 04fc:05da Sunplus Technology Co., Ltd 
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 064e:d20c Suyin Corp. 
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


***** PCMCIA Card Info *****




***** iwconfig *****


wlan0     IEEE 802.11bgn  ESSID:"zo4cg0"  
          Mode:Managed  Frequency:2.432 GHz  Access Point: <MAC address removed>   
          Bit Rate=104 Mb/s   Tx-Power=16 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=68/70  Signal level=-42 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:161   Missed beacon:0




***** rfkill *****


0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
1: acer-wireless: Wireless LAN
	Soft blocked: no
	Hard blocked: no


***** lsmod *****


ath9k                 151173  0 
ath9k_common           13859  1 ath9k
ath9k_hw              444645  2 ath9k_common,ath9k
ath                    23827  3 ath9k_common,ath9k,ath9k_hw
mac80211              596969  1 ath9k
cfg80211              479757  3 ath,ath9k,mac80211


***** nm-tool *****


NetworkManager Tool


State: connected (global)


- Device: wlan0  [zo4cg0] ------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            ath9k
  State:             connected
  Default:           yes
  HW Address:        <MAC address removed>


  Capabilities:
    Speed:           104 Mb/s


  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes


  Wireless Access Points (* = current AP)
    H220N82A625:     Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 57 WPA WPA2
    AvandenBos:      Infra, <MAC address removed>, Freq 2472 MHz, Rate 54 Mb/s, Strength 44 WPA2
    *zo4cg0:         Infra, <MAC address removed>, Freq 2432 MHz, Rate 54 Mb/s, Strength 76 WPA WPA2
    *ð\0\0Ý\0Pò\0\0: Infra, <MAC address removed>, Freq 2432 MHz, Rate 46 Mb/s, Strength 78 WEP
    CARIN-PC_Network:Infra, <MAC address removed>, Freq 2472 MHz, Rate 54 Mb/s, Strength 37 WPA2
    SMC:             Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 44 WEP
    ThomsonCC60DB:   Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 29 WPA WPA2
    FRITZ!Box Fon WLAN 7270: Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 34 WPA WPA2
    NETGEAR:         Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 24 WPA


  IPv4 Settings:
    Address:         192.168.2.1
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.2.254


    DNS:             192.168.2.254




- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            tg3
  State:             unavailable
  Default:           no
  HW Address:        <MAC address removed>


  Capabilities:
    Carrier Detect:  yes


  Wired Properties
    Carrier:         off






***** NetworkManager.state *****
[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true


***** NetworkManager.conf *****


[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq


[ifupdown]
managed=false


***** interfaces *****


# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback


***** iwlist *****


wlan0     Scan completed :
          Cell 01 - Address: <MAC address removed>
                    Channel:5
                    Frequency:2.432 GHz (Channel 5)
                    Quality=68/70  Signal level=-42 dBm  
                    Encryption key:on
                    ESSID:"zo4cg0"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000002c0f2b99f4c
                    Extra: Last beacon: 104ms ago
                    IE: Unknown: 00067A6F34636730
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030105
                    IE: Unknown: 2A0104
                    IE: Unknown: 2F0104
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1A1C181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1605080400000000000000000000000000000000000000
                    IE: Unknown: DD6D0050F204104A00011010440001021041000100103B00010310470010DF4C795BCA0FCF304CC5FF1410E06AA5102100035A544510230005483232304E1024000631323334353610420004313233341054000800060050F2040001101100095A544520483232304E100800020088
                    IE: Unknown: DD090010180207F0050000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C331C181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C3405080400000000000000000000000000000000000000
          Cell 02 - Address: <MAC address removed>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=45/70  Signal level=-65 dBm  
                    Encryption key:on
                    ESSID:"H220N82A625"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000004e71907cdd3
                    Extra: Last beacon: 96ms ago
                    IE: Unknown: 000B483232304E383241363235
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030106
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1A1C181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1606081500000000000000000000000000000000000000
                    IE: Unknown: DD6D0050F204104A00011010440001021041000100103B00010310470010122D239B40A8AEE9E85B7B032F25590A102100035A544510230005483232304E1024000631323334353610420004313233341054000800060050F2040001101100095A544520483232304E100800020088
                    IE: Unknown: DD090010180201F0050000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C331C181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C3406081500000000000000000000000000000000000000
          Cell 03 - Address: <MAC address removed>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=32/70  Signal level=-78 dBm  
                    Encryption key:on
                    ESSID:"SMC"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 22 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000001a7a0a4bbba
                    Extra: Last beacon: 196ms ago
                    IE: Unknown: 0003534D43
                    IE: Unknown: 010582848B962C
                    IE: Unknown: 030106
                    IE: Unknown: 2A0100
                    IE: Unknown: 32080C1218243048606C
          Cell 04 - Address: <MAC address removed>
                    Channel:13
                    Frequency:2.472 GHz (Channel 13)
                    Quality=32/70  Signal level=-78 dBm  
                    Encryption key:on
                    ESSID:"AvandenBos"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000001ab1437e18
                    Extra: Last beacon: 24ms ago
                    IE: Unknown: 000A4176616E64656E426F73
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 03010D
                    IE: Unknown: 0706474220010D14
                    IE: Unknown: 200100
                    IE: Unknown: 2A0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32043048606C
                    IE: Unknown: 2D1AEF1103FFFF000000000000000000000000000000000000000000
                    IE: Unknown: 331AEF1103FFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D160D0F0000000000000000000000000000000000000000
                    IE: Unknown: 34160D0F0000000000000000000000000000000000000000
                    IE: Unknown: DD180050F2020101810003A4000027A4000042435E0062322F00
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: Unknown: DDB10050F204104A0001101044000102103B0001031047001018DE43F8677C4D3A892064D1A30116B21021001A53697465636F6D20546563686E6F6C6F676965732C20496E632E1023001A53697465636F6D20576972656C65737320415020526F7574657210240008574C522D333130301042000A313237333439343839201054000800060050F20400011011001953697465636F6D203830322E31316E20415020526F7574657210080002010C103C000101
          Cell 05 - Address: <MAC address removed>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=30/70  Signal level=-80 dBm  
                    Encryption key:on
                    ESSID:"ThomsonCC60DB"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000002474d4adfb8
                    Extra: Last beacon: 0ms ago
                    IE: Unknown: 000D54686F6D736F6E434336304442
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030101
                    IE: Unknown: 2A0104
                    IE: Unknown: 2F0104
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD090010180201F0000000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101880003A4000027A4000042435E0062322F00
          Cell 06 - Address: <MAC address removed>
                    Channel:2
                    Frequency:2.417 GHz (Channel 2)
                    Quality=28/70  Signal level=-82 dBm  
                    Encryption key:on
                    ESSID:"Zy_private_U39994"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000cf5f7e7dcf
                    Extra: Last beacon: 2164ms ago
                    IE: Unknown: 00115A795F707269766174655F553339393934
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 030102
                    IE: Unknown: 2A0104
                    IE: Unknown: 32040C183060
                    IE: Unknown: 2D1A6E1017FF000000010000000000000000000000000C0000000000
                    IE: Unknown: 3D1602050600000000000000000000000000000000000000
                    IE: Unknown: 3E0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: 0B050001427A12
                    IE: Unknown: 7F0101
                    IE: Unknown: DD07000C4304000000
                    IE: Unknown: 07064E4C20010D10
                    IE: Unknown: DD1E00904C336E1017FF000000010000000000000000000000000C0000000000
                    IE: Unknown: DD1A00904C3402050600000000000000000000000000000000000000
          Cell 07 - Address: <MAC address removed>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=37/70  Signal level=-73 dBm  
                    Encryption key:on
                    ESSID:"NETGEAR"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000004b4f457b81
                    Extra: Last beacon: 608ms ago
                    IE: Unknown: 00074E455447454152
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD06001018020100
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 08 - Address: <MAC address removed>
                    Channel:13
                    Frequency:2.472 GHz (Channel 13)
                    Quality=28/70  Signal level=-82 dBm  
                    Encryption key:on
                    ESSID:"CARIN-PC_Network"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master




***** resolv.conf *****


nameserver 127.0.1.1
search lan


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


[/etc/modprobe.d/bumblebee.conf]
blacklist nouveau
blacklist nvidia
blacklist nvidia-current
blacklist nvidia-current-updates
blacklist nvidia-304
blacklist nvidia-304-updates
blacklist nvidia-experimental-304
blacklist nvidia-310
blacklist nvidia-310-updates
blacklist nvidia-experimental-310
blacklist nvidia-313
blacklist nvidia-313-updates
blacklist nvidia-experimental-313
blacklist nvidia-319
blacklist nvidia-319-updates
blacklist nvidia-experimental-319
blacklist nvidia-325
blacklist nvidia-325-updates
blacklist nvidia-experimental-325


***** modinfo *****


filename:       /lib/modules/3.11.0-14-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k.ko
license:        Dual BSD/GPL
description:    Support for Atheros 802.11n wireless LAN cards.
author:         Atheros Communications
srcversion:     3C8D10ED309094E2B73D591
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
vermagic:       3.11.0-14-generic SMP mod_unload modversions 
parm:           debug:Debugging mask (uint)
parm:           nohwcrypt:Disable hardware encryption (int)
parm:           blink:Enable LED blink on activity (int)
parm:           btcoex_enable:Enable wifi-BT coexistence (int)
parm:           enable_diversity:Enable Antenna diversity for AR9565 (int)


filename:       /lib/modules/3.11.0-14-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_common.ko
license:        Dual BSD/GPL
description:    Shared library for Atheros wireless 802.11n LAN cards.
author:         Atheros Communications
srcversion:     2DB88A2876852DC1D8C5A1D
depends:        ath,ath9k_hw
intree:         Y
vermagic:       3.11.0-14-generic SMP mod_unload modversions 


filename:       /lib/modules/3.11.0-14-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_hw.ko
license:        Dual BSD/GPL
description:    Support for Atheros 802.11n wireless LAN cards.
author:         Atheros Communications
srcversion:     57A1E15BE088B8A5C4BE74F
depends:        ath
intree:         Y
vermagic:       3.11.0-14-generic SMP mod_unload modversions 


filename:       /lib/modules/3.11.0-14-generic/kernel/drivers/net/wireless/ath/ath.ko
license:        Dual BSD/GPL
description:    Shared library for Atheros wireless LAN cards.
author:         Atheros Communications
srcversion:     A890CDBC88E6EF28CD751DD
depends:        cfg80211
intree:         Y
vermagic:       3.11.0-14-generic SMP mod_unload modversions 




***** udev rules *****


# PCI device 0x14e4:0x16b5 (tg3)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"


# PCI device 0x168c:0x002e (ath9k)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"


***** dmesg *****


[   11.516047] ath: phy0: ASPM enabled: 0x42
[   11.516049] ath: EEPROM regdomain: 0x65
[   11.516050] ath: EEPROM indicates we should expect a direct regpair map
[   11.516051] ath: Country alpha2 being used: 00
[   11.516051] ath: Regpair used: 0x65
[   11.751139] psmouse serio1: elantech: assuming hardware version 3 (with firmware version 0x450f01)
[   24.255659] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   24.255908] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   26.841145] wlan0: authenticate with <MAC address removed>
[   26.868558] wlan0: send auth to <MAC address removed> (try 1/3)
[   26.937016] wlan0: authenticated
[   26.940599] wlan0: associate with <MAC address removed> (try 1/3)
[   26.952937] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=8)
[   26.952991] wlan0: associated
[   26.953000] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   27.096500] bridge-wlan0: device is wireless, enabling SMAC
[   27.096502] bridge-wlan0: up
[   27.096504] bridge-wlan0: attached
[   39.078359] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:4c:ac:0a:23:67:f1:08:00 SRC=69.171.248.16 DST=192.168.2.1 LEN=201 TOS=0x00 PREC=0x40 TTL=85 ID=548 DF PROTO=TCP SPT=443 DPT=45778 WINDOW=129 RES=0x00 ACK PSH URGP=0 
[   57.189368] bridge-wlan0: disabling the bridge
[   57.202310] bridge-wlan0: down
[   57.202321] bridge-wlan0: detached
[   77.421318] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:00:90:d0:63:ff:00:08:00 SRC=10.60.29.8 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0xC0 TTL=1 ID=0 PROTO=2 
[   88.328578] bridge-wlan0: device is wireless, enabling SMAC
[   88.328580] bridge-wlan0: up
[   88.328583] bridge-wlan0: attached
[  202.596964] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:00:90:d0:63:ff:00:08:00 SRC=10.60.29.8 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0xC0 TTL=1 ID=0 PROTO=2 
[  327.670049] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:00:90:d0:63:ff:00:08:00 SRC=10.60.29.8 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0xC0 TTL=1 ID=0 PROTO=2 
[  452.845452] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:00:90:d0:63:ff:00:08:00 SRC=10.60.29.8 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0xC0 TTL=1 ID=0 PROTO=2 
[  578.021147] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:00:90:d0:63:ff:00:08:00 SRC=10.60.29.8 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0xC0 TTL=1 ID=0 PROTO=2 
[  703.094429] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:00:90:d0:63:ff:00:08:00 SRC=10.60.29.8 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0xC0 TTL=1 ID=0 PROTO=2 
[  823.970099] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:c4:46:19:9d:66:2e:08:00 SRC=192.168.2.2 DST=192.168.2.1 LEN=52 TOS=0x00 PREC=0x00 TTL=128 ID=13493 DF PROTO=TCP SPT=54518 DPT=135 WINDOW=8192 RES=0x00 SYN URGP=0 
[  826.917720] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:c4:46:19:9d:66:2e:08:00 SRC=192.168.2.2 DST=192.168.2.1 LEN=52 TOS=0x00 PREC=0x00 TTL=128 ID=13497 DF PROTO=TCP SPT=54518 DPT=135 WINDOW=8192 RES=0x00 SYN URGP=0 
[  828.269766] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:00:90:d0:63:ff:00:08:00 SRC=10.60.29.8 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0xC0 TTL=1 ID=0 PROTO=2 
[  832.924532] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:c4:46:19:9d:66:2e:08:00 SRC=192.168.2.2 DST=192.168.2.1 LEN=48 TOS=0x00 PREC=0x00 TTL=128 ID=13499 DF PROTO=TCP SPT=54518 DPT=135 WINDOW=8192 RES=0x00 SYN URGP=0 
[  844.942431] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:c4:46:19:9d:66:2e:08:00 SRC=192.168.2.2 DST=192.168.2.1 LEN=52 TOS=0x00 PREC=0x00 TTL=128 ID=13505 DF PROTO=TCP SPT=54519 DPT=135 WINDOW=8192 RES=0x00 SYN URGP=0 
[  847.945279] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:c4:46:19:9d:66:2e:08:00 SRC=192.168.2.2 DST=192.168.2.1 LEN=52 TOS=0x00 PREC=0x00 TTL=128 ID=13506 DF PROTO=TCP SPT=54519 DPT=135 WINDOW=8192 RES=0x00 SYN URGP=0 
[  853.952669] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:c4:46:19:9d:66:2e:08:00 SRC=192.168.2.2 DST=192.168.2.1 LEN=48 TOS=0x00 PREC=0x00 TTL=128 ID=13507 DF PROTO=TCP SPT=54519 DPT=135 WINDOW=8192 RES=0x00 SYN URGP=0 
[  953.445362] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:00:90:d0:63:ff:00:08:00 SRC=10.60.29.8 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0xC0 TTL=1 ID=0 PROTO=2 
[ 1037.557558] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 1037.571951] bridge-wlan0: disabling the bridge
[ 1037.602545] bridge-wlan0: down
[ 1037.602555] bridge-wlan0: detached
[ 1041.417895] ath: phy0: ASPM enabled: 0x42
[ 1045.977005] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1048.781404] wlan0: authenticate with <MAC address removed>
[ 1048.809410] wlan0: send auth to <MAC address removed> (try 1/3)
[ 1048.817320] wlan0: authenticated
[ 1048.820827] wlan0: associate with <MAC address removed> (try 1/3)
[ 1048.832570] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=10)
[ 1048.832673] wlan0: associated
[ 1048.832685] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 1048.869900] bridge-wlan0: device is wireless, enabling SMAC
[ 1048.869909] bridge-wlan0: up
[ 1048.869919] bridge-wlan0: attached
[ 1135.996699] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:00:90:d0:63:ff:00:08:00 SRC=10.60.29.8 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0xC0 TTL=1 ID=0 PROTO=2 
[ 1386.245431] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:00:90:d0:63:ff:00:08:00 SRC=10.60.29.8 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0xC0 TTL=1 ID=0 PROTO=2 
[ 1511.420848] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:00:90:d0:63:ff:00:08:00 SRC=10.60.29.8 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0xC0 TTL=1 ID=0 PROTO=2 
[ 1636.494111] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:00:90:d0:63:ff:00:08:00 SRC=10.60.29.8 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0xC0 TTL=1 ID=0 PROTO=2 
[ 1761.669712] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:00:90:d0:63:ff:00:08:00 SRC=10.60.29.8 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0xC0 TTL=1 ID=0 PROTO=2 
[ 1886.742646] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:00:90:d0:63:ff:00:08:00 SRC=10.60.29.8 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0xC0 TTL=1 ID=0 PROTO=2 
[ 2008.951024] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:c4:46:19:9d:66:2e:08:00 SRC=192.168.2.2 DST=192.168.2.1 LEN=52 TOS=0x00 PREC=0x00 TTL=128 ID=14299 DF PROTO=TCP SPT=54943 DPT=135 WINDOW=8192 RES=0x00 SYN URGP=0 
[ 2011.918674] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:00:90:d0:63:ff:00:08:00 SRC=10.60.29.8 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0xC0 TTL=1 ID=0 PROTO=2 
[ 2011.995597] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:c4:46:19:9d:66:2e:08:00 SRC=192.168.2.2 DST=192.168.2.1 LEN=52 TOS=0x00 PREC=0x00 TTL=128 ID=14300 DF PROTO=TCP SPT=54943 DPT=135 WINDOW=8192 RES=0x00 SYN URGP=0 
[ 2018.003306] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:c4:46:19:9d:66:2e:08:00 SRC=192.168.2.2 DST=192.168.2.1 LEN=48 TOS=0x00 PREC=0x00 TTL=128 ID=14301 DF PROTO=TCP SPT=54943 DPT=135 WINDOW=8192 RES=0x00 SYN URGP=0 
[ 2030.078014] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:c4:46:19:9d:66:2e:08:00 SRC=192.168.2.2 DST=192.168.2.1 LEN=52 TOS=0x00 PREC=0x00 TTL=128 ID=14310 DF PROTO=TCP SPT=54944 DPT=135 WINDOW=8192 RES=0x00 SYN URGP=0 
[ 2033.081019] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:c4:46:19:9d:66:2e:08:00 SRC=192.168.2.2 DST=192.168.2.1 LEN=52 TOS=0x00 PREC=0x00 TTL=128 ID=14312 DF PROTO=TCP SPT=54944 DPT=135 WINDOW=8192 RES=0x00 SYN URGP=0 
[ 2039.088630] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:c4:46:19:9d:66:2e:08:00 SRC=192.168.2.2 DST=192.168.2.1 LEN=48 TOS=0x00 PREC=0x00 TTL=128 ID=14314 DF PROTO=TCP SPT=54944 DPT=135 WINDOW=8192 RES=0x00 SYN URGP=0 
[ 2137.094028] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:00:90:d0:63:ff:00:08:00 SRC=10.60.29.8 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0xC0 TTL=1 ID=0 PROTO=2 
[ 2262.167039] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:00:90:d0:63:ff:00:08:00 SRC=10.60.29.8 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0xC0 TTL=1 ID=0 PROTO=2 
[ 2387.342663] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:00:90:d0:63:ff:00:08:00 SRC=10.60.29.8 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0xC0 TTL=1 ID=0 PROTO=2 
[ 2512.518150] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:00:90:d0:63:ff:00:08:00 SRC=10.60.29.8 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0xC0 TTL=1 ID=0 PROTO=2 
[ 2637.591234] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:00:90:d0:63:ff:00:08:00 SRC=10.60.29.8 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0xC0 TTL=1 ID=0 PROTO=2 
[ 2762.766748] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:00:90:d0:63:ff:00:08:00 SRC=10.60.29.8 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0xC0 TTL=1 ID=0 PROTO=2 
[ 2887.942466] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:00:90:d0:63:ff:00:08:00 SRC=10.60.29.8 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0xC0 TTL=1 ID=0 PROTO=2 
[ 3013.015601] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:00:90:d0:63:ff:00:08:00 SRC=10.60.29.8 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0xC0 TTL=1 ID=0 PROTO=2 
[ 3138.191118] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:00:90:d0:63:ff:00:08:00 SRC=10.60.29.8 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0xC0 TTL=1 ID=0 PROTO=2 
[ 3263.366643] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:00:90:d0:63:ff:00:08:00 SRC=10.60.29.8 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0xC0 TTL=1 ID=0 PROTO=2 
[ 3388.439840] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:00:90:d0:63:ff:00:08:00 SRC=10.60.29.8 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0xC0 TTL=1 ID=0 PROTO=2 


****************** done ******************



```

---

### Post by varunendra on 2013-12-12
Please define "getting away". As per the dmesg part, there is clearly some intentional blocking from the firewall (UFW). Are you sure you have configured it properly and those blockings are as intended?

If not, you'd appear to be connected, but no traffic (or some particular traffic) won't get through. Is that what you are experiencing?

---

### Post by Mark de J on 2013-12-12
> **varunendra said:**
> Please define "getting away". As per the dmesg part, there is clearly some intentional blocking from the firewall (UFW). Are you sure you have configured it properly and those blockings are as intended?

If not, you'd appear to be connected, but no traffic (or some particular traffic) won't get through. Is that what you are experiencing?
I lose my connection, can´t turn it back on. Wifi card is going out?

---

### Post by varunendra on 2013-12-12
As per the script output, you seem to be connected. Is the report from when it was working? Maybe one from the non-working state could give us some more clues.

For now, please try these -

[indent]

1) Try disabling the firewall. If this helps, maybe your firewall configuration is causing troubles. To disable it -
```
sudo ufw disable
```

2) Try these parameters (one at a time) -
```
sudo modprobe -rv ath9k
sudo modprobe -v ath9k nohwcrypt=1 enable_diversity=1
```
This will be a temporary change and will be lost at next boot. If it seems to help, we can make it permanent. Also, try only one of the parameters first (either "nohwcrypt=1" or "enable_diversity=1"). Both together if trying them separately doesn't seem to help (although none of them is guaranteed to help)

3) Try changing the encryption type in your router to pure WPA-PSK with AES/CCMP. No WPA/WPA2 mixed mode, no TKIP

4) Try changing the channel to 1 or 11 in the router, and disable the N-channel in it. Currently it is set to channel 5, using b/g/n mode it seems. Do this in combination to above.
[/indent]

Whether the above ones help or not, keep the firewall disabled at least until the problem is sorted out. Those [UFW BLOCK] messages don't look good to me and you don't seem to have any explanation for them as well.

---

### Post by Mark de J on 2013-12-13
Are you sure I need disable my firewall because I am using a lot of open netwoks where everyone got access.

---

### Post by varunendra on 2013-12-13
Disabling firewall is just to make sure it is not the firewall preventing the connection/authentication. If configured correctly, it shouldn't affect the connectivity, means the problem lies elsewhere and disabling it won't make any difference.

But if disabling it lets you connect and browse smoothly, maybe you need to reconfigure it, with rules that don't interfere with the normal traffic.

Pin pointing a problem becomes a lot easier when things are in their simplest state, and complexities are kept aside, temporarily or permanently as required. Once the problem is identified and fixed, you can reinstate everything as required.

---

### Post by Mark de J on 2013-12-13
If I disable my firewall my firewall, must I retest?

---

### Post by varunendra on 2013-12-13
Shouldn't be required, but shouldn't hurt either.. :)

To check it is disabled or not -
```
sudo ufw status
```

---

### Post by Mark de J on 2013-12-13
Will try later, my wireless card was turned off again and didn't get on, also not after a reboot. Started from a USB with a 32 bit version of Ubuntu solved the problem, I have again wireless on my laptop on the normal Ubuntu. :s

And I lost WiFi connection and can't get the connection back, WiFi is on, getted a cable now.

---

### Post by varunendra on 2013-12-13
When you say "the card turned off" does it show up as "blocked" in the output of -
```
rfkill list
```
??

If yes, that's a different problem that didn't show up in the report you posted earlier.

---

### Post by Mark de J on 2013-12-13
Connection of WiFi drops when I enter that command:
[COLOR=#222222][FONT=Verdana]Connectionof WiFi is slow...[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana]Rfkill:[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana]rmark@mark:~$rfkill list[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana]0:acer-wireless: Wireless LAN[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana]Softblocked: no[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana]Hardblocked: no[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana]1:phy0: Wireless LAN[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana]Softblocked: no[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana]Hardblocked: no[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana]mark@mark:~$
 
EDIT: Lost connection default now... Is it because the bad wifi?

State of wireless connection:
[/FONT][/COLOR][ATTACH=CONFIG]248565[/ATTACH]

---

### Post by Mark de J on 2013-12-13
Here at home it drops one time but is working fine now, :s?

No problems here at home, can you pleas tell me why my computer is trolling me?

---

### Post by varunendra on 2013-12-14
It is not uncommon for networking to work on one network and not on another.
But in order to investigate a problem, we need the problem first, do we have one now? :P

---

### Post by Mark de J on 2013-12-14
> **varunendra said:**
> It is not uncommon for networking to work on one network and not on another.
But in order to investigate a problem, we need the problem first, do we have one now? :P
No, my home network is working fine.

---

### Post by varunendra on 2013-12-14
Too bad we couldn't determine the reason and fix for the problem we had with the other network. :(

But glad to know at least currently it is working fine.

---

### Post by Mark de J on 2013-12-14
> **varunendra said:**
> Too bad we couldn't determine the reason and fix for the problem we had with the other network. :(

But glad to know at least currently it is working fine.
Yes, but I use that school network 5 days a week.

---

### Post by varunendra on 2013-12-15
I'd be happy to help if I could, if you still need and wish to troubleshoot it when dealing with it again.

---

### Post by Mark de J on 2013-12-15
Wil let you Monday know how it does.

---

### Post by Mark de J on 2013-12-16
The problem here is also here solved for now, when this change I will let it know! For now, prefix changed to **Solved**&#8203;. :)

---

