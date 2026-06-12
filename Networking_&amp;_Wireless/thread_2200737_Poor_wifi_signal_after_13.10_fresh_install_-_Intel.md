---
title: "Poor wifi signal after 13.10 fresh install - Intel Centrino Advanced-N 6230"
date: 2014-01-20
forum: Networking &amp; Wireless
---

### Post by glynhudson on 2014-01-20
Hello all,

I'm having problems with my wifi after upgrading to 13.10 64bit after rocksolid wifi performance on 12.04. The upgrade also coincided with me upgrading to an SSD (not sure if this could be linked? SSD degrading wifi signal?..SDD does sit very close to wifi card inside my laptop (Samsung 300U)).

sometimes wifi works well for about 5-10 min then slows to a crawl and often won't connect at all. It's as if the signal is really weak although I am right next to my router. Wifi is working well on my Android and windows devices.

Here's the output from my logs:

[http://paste.ubuntu.com/6789017/](http://paste.ubuntu.com/6789017/)

I've tried 

sudo modprobe -rv iwldvm
sudo modprobe -v iwlwifi 11n_disable=1
sudo modprobe -v iwldvm

but it didn't make any difference.

Many thanks for your help. I've been enjoying using Ubuntu as my daily driver for over 5 years without any major issue. Have enjoyed seeing it mature over that time. To all the devs, keep up the good work! 

Here are my logs:

```



*************** info trace ***************


***** uname -a *****


Linux glyn-laptop 3.11.0-15-generic #23-Ubuntu SMP Mon Dec 9 18:17:04 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux


***** lsb_release *****


Distributor ID:    Ubuntu
Description:    Ubuntu 13.10
Release:    13.10
Codename:    saucy


***** lspci *****


01:00.0 Network controller [0280]: Intel Corporation Centrino Advanced-N 6230 [Rainbow Peak] [8086:0090] (rev 34)
    Subsystem: Intel Corporation Centrino Advanced-N 6230 AGN [8086:5211]
    Kernel driver in use: iwlwifi
02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 06)
    Subsystem: Samsung Electronics Co Ltd Device [144d:c604]
    Kernel driver in use: r8169


***** lsusb *****


Bus 002 Device 004: ID 8086:0189 Intel Corp. 
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 2232:1008  
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


***** PCMCIA Card Info *****




***** iwconfig *****


wlan0     IEEE 802.11abgn  ESSID:"Muesli"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: <MAC address removed>   
          Bit Rate=1 Mb/s   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=41/70  Signal level=-69 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:24  Invalid misc:33   Missed beacon:0




***** rfkill *****


0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
5: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no


***** lsmod *****


iwldvm                237469  0 
mac80211              597268  1 iwldvm
iwlwifi               165675  1 iwldvm
cfg80211              480503  3 iwlwifi,mac80211,iwldvm


***** nm-tool *****


NetworkManager Tool


State: connected (global)


- Device: eth0  [Wired connection 1] -------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             connected
  Default:           yes
  HW Address:        <MAC address removed>


  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s


  Wired Properties
    Carrier:         on


  IPv4 Settings:
    Address:         192.168.1.104
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.254


    DNS:             192.168.1.254




- Device: wlan0  [Muesli] ------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            iwlwifi
  State:             connected
  Default:           no
  HW Address:        <MAC address removed>


  Capabilities:
    Speed:           1 Mb/s


  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes


  Wireless Access Points (* = current AP)
    *Muesli:         Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 49


  IPv4 Settings:
    Address:         192.168.1.111
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.254


    DNS:             192.168.1.254






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
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=42/70  Signal level=-68 dBm  
                    Encryption key:off
                    ESSID:"Muesli"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000011c4c0793c2
                    Extra: Last beacon: 36ms ago
                    IE: Unknown: 00064D7565736C69
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0104
                    IE: Unknown: 32040C183060
                    IE: Unknown: 2D1A6E1017FFFF000001000000000000000000000000000000000000
                    IE: Unknown: 3D160B070600000000000000000000000000000000000000
                    IE: Unknown: 3E0100
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: 0B05050007127A
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: DD07000C4300000000
                    IE: Unknown: 0706455520010E10




***** resolv.conf *****


nameserver 127.0.1.1
search home.gateway


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


filename:       /lib/modules/3.11.0-15-generic/kernel/drivers/net/wireless/iwlwifi/dvm/iwldvm.ko
license:        GPL
author:         Copyright(c) 2003-2013 Intel Corporation <ilw@linux.intel.com>
version:        in-tree:
description:    Intel(R) Wireless WiFi Link AGN driver for Linux
srcversion:     189D6366522149BFF40DA25
depends:        iwlwifi,mac80211,cfg80211
intree:         Y
vermagic:       3.11.0-15-generic SMP mod_unload modversions 


filename:       /lib/modules/3.11.0-15-generic/kernel/drivers/net/wireless/iwlwifi/iwlwifi.ko
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
srcversion:     B690FF1883B2CA894BA5B6C
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
vermagic:       3.11.0-15-generic SMP mod_unload modversions 
parm:           swcrypto:using crypto in software (default 0 [hardware]) (int)
parm:           11n_disable:disable 11n functionality, bitmap: 1: full, 2: agg TX, 4: agg RX (uint)
parm:           amsdu_size_8K:enable 8K amsdu size (default 0) (int)
parm:           fw_restart:restart firmware in case of error (default true) (bool)
parm:           antenna_coupling:specify antenna coupling in dB (defualt: 0 dB) (int)
parm:           wd_disable:Disable stuck queue watchdog timer 0=system default, 1=disable, 2=enable (default: 0) (int)
parm:           nvm_file:NVM file name (charp)
parm:           bt_coex_active:enable wifi/bt co-exist (default: enable) (bool)
parm:           led_mode:0=system default, 1=On(RF On)/Off(RF Off), 2=blinking, 3=Off (default: 0) (int)
parm:           power_save:enable WiFi power management (default: disable) (bool)
parm:           power_level:default power save level (range from 1 - 5, default: 1) (int)




***** udev rules *****


# PCI device 0x10ec:0x8168 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"


# PCI device 0x8086:0x0090 (iwlwifi)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"


***** dmesg *****


[    3.872203] iwlwifi 0000:01:00.0: enabling device (0000 -> 0002)
[    3.872311] iwlwifi 0000:01:00.0: can't disable ASPM; OS doesn't have ASPM control
[    3.872617] iwlwifi 0000:01:00.0: irq 43 for MSI/MSI-X
[    3.881048] iwlwifi 0000:01:00.0: loaded firmware version 18.168.6.1 op_mode iwldvm
[    3.935045] iwlwifi 0000:01:00.0: CONFIG_IWLWIFI_DEBUG disabled
[    3.935051] iwlwifi 0000:01:00.0: CONFIG_IWLWIFI_DEBUGFS enabled
[    3.935054] iwlwifi 0000:01:00.0: CONFIG_IWLWIFI_DEVICE_TRACING enabled
[    3.935057] iwlwifi 0000:01:00.0: CONFIG_IWLWIFI_P2P disabled
[    3.935061] iwlwifi 0000:01:00.0: Detected Intel(R) Centrino(R) Advanced-N 6230 AGN, REV=0xB0
[    3.935268] iwlwifi 0000:01:00.0: L1 Enabled; Disabling L0S
[    4.054470] ieee80211 phy0: Selected rate control algorithm 'iwl-agn-rs'
[    5.084990] psmouse serio1: elantech: assuming hardware version 3 (with firmware version 0x450f00)
[    6.464515] iwlwifi 0000:01:00.0: L1 Enabled; Disabling L0S
[    6.474370] iwlwifi 0000:01:00.0: Radio type=0x1-0x2-0x0
[    6.748978] iwlwifi 0000:01:00.0: L1 Enabled; Disabling L0S
[    6.756331] iwlwifi 0000:01:00.0: Radio type=0x1-0x2-0x0
[    6.833313] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[    6.833819] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   13.360661] wlan0: authenticate with <MAC address removed>
[   13.365592] wlan0: send auth to <MAC address removed> (try 1/3)
[   13.368343] wlan0: authenticated
[   13.368545] wlan0: waiting for beacon from <MAC address removed>
[   13.416145] wlan0: associate with <MAC address removed> (try 1/3)
[   13.419621] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=5)
[   13.422110] wlan0: associated
[   13.422149] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 2485.495006] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 2487.118444] iwlwifi 0000:01:00.0: RF_KILL bit toggled to enable radio.
[ 2488.320672] iwlwifi 0000:01:00.0: L1 Enabled; Disabling L0S
[ 2488.327968] iwlwifi 0000:01:00.0: Radio type=0x1-0x2-0x0
[ 2488.415516] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 2494.916875] wlan0: authenticate with <MAC address removed>
[ 2494.920654] wlan0: send auth to <MAC address removed> (try 1/3)
[ 2494.924520] wlan0: authenticated
[ 2494.926191] wlan0: associate with <MAC address removed> (try 1/3)
[ 2494.932414] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=5)
[ 2494.935384] wlan0: associated
[ 2494.935446] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 2510.489850] wlan0: authenticate with <MAC address removed>
[ 2510.492322] wlan0: send auth to <MAC address removed> (try 1/3)
[ 2510.498291] wlan0: authenticated
[ 2510.500433] wlan0: associate with <MAC address removed> (try 1/3)
[ 2510.608602] wlan0: associate with <MAC address removed> (try 2/3)
[ 2510.752692] wlan0: associate with <MAC address removed> (try 3/3)
[ 2510.924702] wlan0: association with <MAC address removed> timed out
[ 2522.318074] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 2531.719501] wlan0: authenticate with <MAC address removed>
[ 2531.722356] wlan0: send auth to <MAC address removed> (try 1/3)
[ 2531.726070] wlan0: authenticated
[ 2531.726595] wlan0: associate with <MAC address removed> (try 1/3)
[ 2531.904643] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=5)
[ 2531.907249] wlan0: associated
[ 2531.907610] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 2542.519895] wlan0: authenticate with <MAC address removed>
[ 2542.522879] wlan0: send auth to <MAC address removed> (try 1/3)
[ 2542.525821] wlan0: authenticated
[ 2542.529531] wlan0: associate with <MAC address removed> (try 1/3)
[ 2542.533175] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=5)
[ 2542.536023] wlan0: associated
[ 2549.460927] wlan0: authenticate with <MAC address removed>
[ 2549.462721] wlan0: send auth to <MAC address removed> (try 1/3)
[ 2549.464641] wlan0: authenticated
[ 2549.466682] wlan0: associate with <MAC address removed> (try 1/3)
[ 2549.548583] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=5)
[ 2549.552168] wlan0: associated
[ 2679.077524] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 2682.314091] wlan0: authenticate with <MAC address removed>
[ 2682.320055] wlan0: send auth to <MAC address removed> (try 1/3)
[ 2682.322910] wlan0: authenticated
[ 2682.325341] wlan0: associate with <MAC address removed> (try 1/3)
[ 2682.334257] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=5)
[ 2682.336871] wlan0: associated
[ 4437.632688] wlan0: authenticate with <MAC address removed>
[ 4437.634548] wlan0: send auth to <MAC address removed> (try 1/3)
[ 4437.637615] wlan0: authenticated
[ 4437.638412] wlan0: associate with <MAC address removed> (try 1/3)
[ 4437.643107] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=5)
[ 4437.646018] wlan0: associated
[ 4442.640473] wlan0: authenticate with <MAC address removed>
[ 4442.642365] wlan0: send auth to <MAC address removed> (try 1/3)
[ 4442.645196] wlan0: authenticated
[ 4442.649484] wlan0: associate with <MAC address removed> (try 1/3)
[ 4442.654389] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=5)
[ 4442.657619] wlan0: associated
[ 4480.678310] wlan0: authenticate with <MAC address removed>
[ 4480.681410] wlan0: send auth to <MAC address removed> (try 1/3)
[ 4480.684379] wlan0: authenticated
[ 4480.686479] wlan0: associate with <MAC address removed> (try 1/3)
[ 4480.690257] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=5)
[ 4480.693994] wlan0: associated
[ 4757.023932] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 4760.255394] wlan0: authenticate with <MAC address removed>
[ 4760.263413] wlan0: send auth to <MAC address removed> (try 1/3)
[ 4760.370311] wlan0: send auth to <MAC address removed> (try 2/3)
[ 4760.372219] wlan0: authenticated
[ 4760.376259] wlan0: associate with <MAC address removed> (try 1/3)
[ 4760.380318] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=5)
[ 4760.383112] wlan0: associated
[ 5269.172270] wlan0: authenticate with <MAC address removed>
[ 5269.177202] wlan0: send auth to <MAC address removed> (try 1/3)
[ 5269.181043] wlan0: authenticated
[ 5269.184918] wlan0: associate with <MAC address removed> (try 1/3)
[ 5269.197531] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=5)
[ 5269.203387] wlan0: associated
[ 5353.218738] wlan0: authenticate with <MAC address removed>
[ 5353.221251] wlan0: send auth to <MAC address removed> (try 1/3)
[ 5353.224406] wlan0: authenticated
[ 5353.228102] wlan0: associate with <MAC address removed> (try 1/3)
[ 5353.233798] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=5)
[ 5353.236729] wlan0: associated
[ 5537.367783] wlan0: authenticate with <MAC address removed>
[ 5537.369739] wlan0: send auth to <MAC address removed> (try 1/3)
[ 5537.372722] wlan0: authenticated
[ 5537.373251] wlan0: associate with <MAC address removed> (try 1/3)
[ 5537.377334] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=5)
[ 5537.381001] wlan0: associated
[ 5576.379625] wlan0: authenticate with <MAC address removed>
[ 5576.382436] wlan0: send auth to <MAC address removed> (try 1/3)
[ 5576.385259] wlan0: authenticated
[ 5576.386790] wlan0: associate with <MAC address removed> (try 1/3)
[ 5576.390377] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=5)
[ 5576.393269] wlan0: associated
[ 5583.399183] wlan0: authenticate with <MAC address removed>
[ 5583.401533] wlan0: send auth to <MAC address removed> (try 1/3)
[ 5583.403597] wlan0: authenticated
[ 5583.407408] wlan0: associate with <MAC address removed> (try 1/3)
[ 5583.414846] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=5)
[ 5583.417505] wlan0: associated
[ 5600.403268] wlan0: authenticate with <MAC address removed>
[ 5600.404849] wlan0: send auth to <MAC address removed> (try 1/3)
[ 5600.406840] wlan0: authenticated
[ 5600.410566] wlan0: associate with <MAC address removed> (try 1/3)
[ 5600.422493] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=5)
[ 5600.425258] wlan0: associated
[ 5616.413120] wlan0: authenticate with <MAC address removed>
[ 5616.415154] wlan0: send auth to <MAC address removed> (try 1/3)
[ 5616.521244] wlan0: send auth to <MAC address removed> (try 2/3)
[ 5616.525143] wlan0: authenticated
[ 5616.529155] wlan0: associate with <MAC address removed> (try 1/3)
[ 5616.551188] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=5)
[ 5616.555167] wlan0: associated
[ 5633.409060] wlan0: authenticate with <MAC address removed>
[ 5633.412955] wlan0: send auth to <MAC address removed> (try 1/3)
[ 5633.415066] wlan0: authenticated
[ 5633.416431] wlan0: associate with <MAC address removed> (try 1/3)
[ 5633.421167] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=5)
[ 5633.424302] wlan0: associated
[ 5640.417439] wlan0: authenticate with <MAC address removed>
[ 5640.419856] wlan0: send auth to <MAC address removed> (try 1/3)
[ 5640.422017] wlan0: authenticated
[ 5640.424860] wlan0: associate with <MAC address removed> (try 1/3)
[ 5640.435251] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=5)
[ 5640.437980] wlan0: associated
[ 5645.308983] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 6058.998334] wlan0: authenticate with <MAC address removed>
[ 6059.001697] wlan0: send auth to <MAC address removed> (try 1/3)
[ 6059.007274] wlan0: authenticated
[ 6059.008133] wlan0: associate with <MAC address removed> (try 1/3)
[ 6060.372973] wlan0: associate with <MAC address removed> (try 2/3)
[ 6060.781388] wlan0: associate with <MAC address removed> (try 3/3)
[ 6060.789135] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=5)
[ 6060.792659] wlan0: associated
[ 6060.792725] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 6353.877432] wlan0: authenticate with <MAC address removed>
[ 6353.880336] wlan0: send auth to <MAC address removed> (try 1/3)
[ 6353.883135] wlan0: authenticated
[ 6353.885640] wlan0: associate with <MAC address removed> (try 1/3)
[ 6353.889211] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=5)
[ 6353.892132] wlan0: associated
[ 6368.886923] wlan0: authenticate with <MAC address removed>
[ 6368.889969] wlan0: send auth to <MAC address removed> (try 1/3)
[ 6368.892940] wlan0: authenticated
[ 6368.895564] wlan0: associate with <MAC address removed> (try 1/3)
[ 6368.899435] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=5)
[ 6368.903233] wlan0: associated
[ 6390.880732] wlan0: authenticate with <MAC address removed>
[ 6390.883727] wlan0: send auth to <MAC address removed> (try 1/3)
[ 6390.885782] wlan0: authenticated
[ 6390.889996] wlan0: associate with <MAC address removed> (try 1/3)
[ 6390.895346] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=5)
[ 6390.898206] wlan0: associated
[ 6395.886702] wlan0: authenticate with <MAC address removed>
[ 6395.889366] wlan0: send auth to <MAC address removed> (try 1/3)
[ 6395.892194] wlan0: authenticated
[ 6395.893247] wlan0: associate with <MAC address removed> (try 1/3)
[ 6395.897503] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=5)
[ 6395.901312] wlan0: associated
[ 6401.903077] wlan0: authenticate with <MAC address removed>
[ 6401.906007] wlan0: send auth to <MAC address removed> (try 1/3)
[ 6402.013273] wlan0: send auth to <MAC address removed> (try 2/3)
[ 6402.015202] wlan0: authenticated
[ 6402.017293] wlan0: associate with <MAC address removed> (try 1/3)
[ 6402.023803] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=5)
[ 6402.026751] wlan0: associated
[ 6407.996312] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 6411.448753] wlan0: authenticate with <MAC address removed>
[ 6411.456816] wlan0: send auth to <MAC address removed> (try 1/3)
[ 6411.460686] wlan0: authenticated
[ 6411.463651] wlan0: associate with <MAC address removed> (try 1/3)
[ 6411.467223] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=5)
[ 6411.470268] wlan0: associated
[ 6426.122459] wlan0: authenticate with <MAC address removed>
[ 6426.124140] wlan0: send auth to <MAC address removed> (try 1/3)
[ 6426.127018] wlan0: authenticated
[ 6426.129130] wlan0: associate with <MAC address removed> (try 1/3)
[ 6426.132697] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=5)
[ 6426.135487] wlan0: associated
[ 6510.964471] wlan0: authenticate with <MAC address removed>
[ 6510.967013] wlan0: send auth to <MAC address removed> (try 1/3)
[ 6511.074411] wlan0: send auth to <MAC address removed> (try 2/3)
[ 6511.136574] wlan0: authenticated
[ 6511.138496] wlan0: associate with <MAC address removed> (try 1/3)
[ 6511.310608] wlan0: associate with <MAC address removed> (try 2/3)
[ 6511.442630] wlan0: associate with <MAC address removed> (try 3/3)
[ 6511.578709] wlan0: association with <MAC address removed> timed out
[ 6522.846556] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 6879.904583] iwlwifi 0000:01:00.0: L1 Enabled; Disabling L0S
[ 6879.911175] iwlwifi 0000:01:00.0: Radio type=0x1-0x2-0x0
[ 6880.004684] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 6886.390988] wlan0: authenticate with <MAC address removed>
[ 6886.394210] wlan0: send auth to <MAC address removed> (try 1/3)
[ 6886.397052] wlan0: authenticated
[ 6886.401062] wlan0: associate with <MAC address removed> (try 1/3)
[ 6886.404658] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=5)
[ 6886.407604] wlan0: associated
[ 6886.407667] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 6911.543549] iwlwifi 0000:01:00.0: fail to flush all tx fifo queues Q 11
[ 6911.543562] iwlwifi 0000:01:00.0: Current SW read_ptr 73 write_ptr 100
[ 6911.543640] iwl data: 00000000: 00 fe ff ff 00 f8 03 00 00 00 00 00 00 00 00 00  ................
[ 6911.543690] iwlwifi 0000:01:00.0: FH TRBs(0) = 0x00000000
[ 6911.543730] iwlwifi 0000:01:00.0: FH TRBs(1) = 0xc010b05f
[ 6911.543769] iwlwifi 0000:01:00.0: FH TRBs(2) = 0x00000000
[ 6911.543814] iwlwifi 0000:01:00.0: FH TRBs(3) = 0x80300009
[ 6911.543854] iwlwifi 0000:01:00.0: FH TRBs(4) = 0x00000000
[ 6911.543909] iwlwifi 0000:01:00.0: FH TRBs(5) = 0x00000000
[ 6911.543961] iwlwifi 0000:01:00.0: FH TRBs(6) = 0x00000000
[ 6911.544006] iwlwifi 0000:01:00.0: FH TRBs(7) = 0x007090ae
[ 6911.544124] iwlwifi 0000:01:00.0: Q 0 is active and mapped to fifo 3 ra_tid 0x0000 [10,10]
[ 6911.544235] iwlwifi 0000:01:00.0: Q 1 is active and mapped to fifo 2 ra_tid 0x0000 [0,0]
[ 6911.544333] iwlwifi 0000:01:00.0: Q 2 is active and mapped to fifo 1 ra_tid 0x0000 [173,173]
[ 6911.544438] iwlwifi 0000:01:00.0: Q 3 is active and mapped to fifo 0 ra_tid 0x0000 [0,0]
[ 6911.544555] iwlwifi 0000:01:00.0: Q 4 is active and mapped to fifo 0 ra_tid 0x0000 [0,0]
[ 6911.544658] iwlwifi 0000:01:00.0: Q 5 is active and mapped to fifo 4 ra_tid 0x0000 [0,0]
[ 6911.544762] iwlwifi 0000:01:00.0: Q 6 is active and mapped to fifo 2 ra_tid 0x0000 [0,0]
[ 6911.544859] iwlwifi 0000:01:00.0: Q 7 is active and mapped to fifo 5 ra_tid 0x0000 [0,0]
[ 6911.544968] iwlwifi 0000:01:00.0: Q 8 is active and mapped to fifo 4 ra_tid 0x0000 [0,0]
[ 6911.545072] iwlwifi 0000:01:00.0: Q 9 is active and mapped to fifo 7 ra_tid 0x0000 [175,175]
[ 6911.545180] iwlwifi 0000:01:00.0: Q 10 is active and mapped to fifo 5 ra_tid 0x0000 [0,0]
[ 6911.545281] iwlwifi 0000:01:00.0: Q 11 is active and mapped to fifo 1 ra_tid 0x0000 [73,100]
[ 6911.545379] iwlwifi 0000:01:00.0: Q 12 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[ 6911.545487] iwlwifi 0000:01:00.0: Q 13 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[ 6911.545580] iwlwifi 0000:01:00.0: Q 14 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[ 6911.545685] iwlwifi 0000:01:00.0: Q 15 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[ 6911.545788] iwlwifi 0000:01:00.0: Q 16 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[ 6911.545888] iwlwifi 0000:01:00.0: Q 17 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[ 6911.546003] iwlwifi 0000:01:00.0: Q 18 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[ 6911.546112] iwlwifi 0000:01:00.0: Q 19 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[ 7103.107694] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 7104.696117] iwlwifi 0000:01:00.0: RF_KILL bit toggled to enable radio.
[ 7105.968705] iwlwifi 0000:01:00.0: L1 Enabled; Disabling L0S
[ 7105.976392] iwlwifi 0000:01:00.0: Radio type=0x1-0x2-0x0
[ 7106.068052] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 7112.531358] wlan0: authenticate with <MAC address removed>
[ 7112.534903] wlan0: send auth to <MAC address removed> (try 1/3)
[ 7112.537720] wlan0: authenticated
[ 7112.541295] wlan0: associate with <MAC address removed> (try 1/3)
[ 7112.545068] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=5)
[ 7112.548341] wlan0: associated
[ 7112.548401] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 8558.076530] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 8559.785798] iwlwifi 0000:01:00.0: RF_KILL bit toggled to enable radio.
[ 8561.275466] iwlwifi 0000:01:00.0: L1 Enabled; Disabling L0S
[ 8561.282346] iwlwifi 0000:01:00.0: Radio type=0x1-0x2-0x0
[ 8561.366247] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 8961.914675] wlan0: authenticate with <MAC address removed>
[ 8961.919036] wlan0: send auth to <MAC address removed> (try 1/3)
[ 8961.954160] wlan0: send auth to <MAC address removed> (try 2/3)
[ 8961.967091] wlan0: authenticated
[ 8961.967459] wlan0: waiting for beacon from <MAC address removed>
[ 8965.326935] wlan0: authenticate with <MAC address removed>
[ 8965.331097] wlan0: send auth to <MAC address removed> (try 1/3)
[ 8965.355113] wlan0: send auth to <MAC address removed> (try 2/3)
[ 8965.380118] wlan0: send auth to <MAC address removed> (try 3/3)
[ 8965.403889] wlan0: authentication with <MAC address removed> timed out
[ 9773.025228] wlan0: authenticate with <MAC address removed>
[ 9773.029204] wlan0: send auth to <MAC address removed> (try 1/3)
[ 9773.051612] wlan0: send auth to <MAC address removed> (try 2/3)
[ 9773.073655] wlan0: send auth to <MAC address removed> (try 3/3)
[ 9773.094173] wlan0: authentication with <MAC address removed> timed out
[10451.073649] iwlwifi 0000:01:00.0: RF_KILL bit toggled to enable radio.
[10452.252791] iwlwifi 0000:01:00.0: L1 Enabled; Disabling L0S
[10452.259745] iwlwifi 0000:01:00.0: Radio type=0x1-0x2-0x0
[10452.349039] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[10576.473226] iwlwifi 0000:01:00.0: L1 Enabled; Disabling L0S
[10576.479997] iwlwifi 0000:01:00.0: Radio type=0x1-0x2-0x0
[10576.571822] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[11147.224145] wlan0: authenticate with <MAC address removed>
[11147.229194] wlan0: send auth to <MAC address removed> (try 1/3)
[11147.236885] wlan0: authenticated
[11147.237160] wlan0: waiting for beacon from <MAC address removed>
[11150.625879] wlan0: authenticate with <MAC address removed>
[11150.629799] wlan0: send auth to <MAC address removed> (try 1/3)
[11150.636174] wlan0: authenticated
[11150.636506] wlan0: waiting for beacon from <MAC address removed>
[11150.709633] wlan0: associate with <MAC address removed> (try 1/3)
[11150.740003] wlan0: associate with <MAC address removed> (try 2/3)
[11150.743779] wlan0: RX AssocResp from <MAC address removed> (capab=0x401 status=0 aid=5)
[11150.750027] wlan0: associated
[11150.750073] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[11316.002483] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[19374.536748] iwlwifi 0000:01:00.0: L1 Enabled; Disabling L0S
[19374.545529] iwlwifi 0000:01:00.0: Radio type=0x1-0x2-0x0
[19374.637643] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[19381.002437] wlan0: authenticate with <MAC address removed>
[19381.007618] wlan0: send auth to <MAC address removed> (try 1/3)
[19381.022265] wlan0: authenticated
[19381.022954] wlan0: associate with <MAC address removed> (try 1/3)
[19381.027781] wlan0: RX AssocResp from <MAC address removed> (capab=0x401 status=0 aid=6)
[19381.032907] wlan0: associated
[19381.032975] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[20076.269281] wlan0: authenticate with <MAC address removed>
[20076.271952] wlan0: send auth to <MAC address removed> (try 1/3)
[20076.549993] wlan0: send auth to <MAC address removed> (try 2/3)
[20076.557882] wlan0: authenticated
[20076.561990] wlan0: associate with <MAC address removed> (try 1/3)
[20076.565805] wlan0: RX AssocResp from <MAC address removed> (capab=0x401 status=0 aid=6)
[20076.574050] wlan0: associated
[20178.478076] wlan0: authenticate with <MAC address removed>
[20178.481590] wlan0: send auth to <MAC address removed> (try 1/3)
[20178.483101] wlan0: authenticated
[20178.483285] wlan0: waiting for beacon from <MAC address removed>
[20178.500944] wlan0: associate with <MAC address removed> (try 1/3)
[20178.504757] wlan0: RX AssocResp from <MAC address removed> (capab=0x401 status=0 aid=6)
[20178.510639] wlan0: associated
[20352.564600] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[20362.614617] wlan0: authenticate with <MAC address removed>
[20362.618062] wlan0: send auth to <MAC address removed> (try 1/3)
[20362.629106] wlan0: authenticated
[20362.629448] wlan0: waiting for beacon from <MAC address removed>
[20362.734198] wlan0: associate with <MAC address removed> (try 1/3)
[20362.740203] wlan0: RX AssocResp from <MAC address removed> (capab=0x401 status=0 aid=6)
[20362.747028] wlan0: associated
[20362.747072] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[20492.094264] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[20495.341048] wlan0: authenticate with <MAC address removed>
[20495.343278] wlan0: send auth to <MAC address removed> (try 1/3)
[20495.351075] wlan0: authenticated
[20495.355069] wlan0: associate with <MAC address removed> (try 1/3)
[20495.359009] wlan0: RX AssocResp from <MAC address removed> (capab=0x401 status=0 aid=6)
[20495.363804] wlan0: associated
[20637.788643] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[21114.133210] wlan0: authenticate with <MAC address removed>
[21114.139299] wlan0: send auth to <MAC address removed> (try 1/3)
[21114.196938] wlan0: send auth to <MAC address removed> (try 2/3)
[21114.203432] wlan0: authenticated
[21114.203835] wlan0: waiting for beacon from <MAC address removed>
[21114.212563] wlan0: associate with <MAC address removed> (try 1/3)
[21114.239397] wlan0: associate with <MAC address removed> (try 2/3)
[21114.247122] wlan0: RX AssocResp from <MAC address removed> (capab=0x401 status=0 aid=5)
[21114.251491] wlan0: associated
[21114.252415] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[21138.976823] wlan0: authenticate with <MAC address removed>
[21138.980889] wlan0: send auth to <MAC address removed> (try 1/3)
[21139.081038] wlan0: send auth to <MAC address removed> (try 2/3)
[21139.197148] wlan0: send auth to <MAC address removed> (try 3/3)
[21139.286985] wlan0: authentication with <MAC address removed> timed out
[21151.099162] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[21312.279450] wlan0: authenticate with <MAC address removed>
[21312.283424] wlan0: send auth to <MAC address removed> (try 1/3)
[21312.295053] wlan0: authenticated
[21312.298738] wlan0: associate with <MAC address removed> (try 1/3)
[21312.327240] wlan0: associate with <MAC address removed> (try 2/3)
[21312.331181] wlan0: RX AssocResp from <MAC address removed> (capab=0x401 status=0 aid=5)
[21312.341944] wlan0: associated
[21312.342015] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready


****************** done ******************



```

---

### Post by glynhudson on 2014-01-21
This is really strange, I think the issue might be to do with the SSD having an effect on the wifi signal. The wifi performance was slightly better with the SSD hanging out of the laptop (still not as good as on 12.04). Has anyone else experienced an SSD adversely effecting wifi signal? If anyone with more knowledge of wifi drivers than me could let me know if everything (software wise) looks ok from the above logs I will have to assume it's the SSD causing the issue, which is a shame since my laptop is now very fast with the SSD but very less functional without working network connectivity :-(

---

### Post by NexusZA on 2014-03-28
Everything I have seen for this problem is related to the built-in wifi drivers in the newer kernel for 13.10. If this was an SSD issue then you would have seen it before the upgrade. When trouble-shooting you look at what has changed and the only thing that changed was your OS so the problem lies there.

Unfortunately, knowing what is causing the problem is only the first step. As of yet I have yet to find a solution to the problem. I have tried many different things (upgrading kernel, downgrading kernel, upgrading drivers, patching kernel, etc etc) but none have worked as of yet.

The only solution I have seen that would result in success is to look at getting a cheap little wifi-dongle to plug into your laptop. If anyone else has any other advice that would be great.

---

