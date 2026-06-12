---
title: "Intel 3945abg wireless problem"
date: 2013-09-12
forum: Networking &amp; Wireless
---

### Post by steli2 on 2013-09-12
I have similar problem with my wireless card, Intel Pro Wireless 3945abg.It shows all the wireless networks around, included mine, but when I try to connect, it asking me the password again and again.There are no hardware or software blocked.
   Here are the outputs of :
   
```
lspci -nnk | grep -iA2 net
dmesg | grep iwl


   qwerty@qwerty-T12J:~$ lspci -nnk | grep -iA2 net

03:00.0 Network controller [0280]: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection [8086:4222] (rev 02)
    Subsystem: Intel Corporation PRO/Wireless 3945ABG Network Connection [8086:1001]
    Kernel driver in use: iwl3945
    Kernel modules: iwl3945
--
06:07.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ [10ec:8139] (rev 10)
    Subsystem: Packard Bell B.V. Device [1631:c022]
    Kernel driver in use: 8139too

qwerty@qwerty-T12J:~$ dmesg | grep iwl

[   21.280622] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, in-tree:s
[   21.280627] iwl3945: Copyright(c) 2003-2011 Intel Corporation
[   21.280701] iwl3945 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   21.280718] iwl3945 0000:03:00.0: setting latency timer to 64
[   21.884749] iwl3945 0000:03:00.0: Tunable channels: 13 802.11bg, 23 802.11a channels
[   21.884754] iwl3945 0000:03:00.0: Detected Intel Wireless WiFi Link 3945ABG
[   21.884917] iwl3945 0000:03:00.0: irq 44 for MSI/MSI-X
[   21.916499] ieee80211 phy0: Selected rate control algorithm 'iwl-3945-rs'
[   22.513960] iwl3945 0000:03:00.0: loaded firmware version 15.32.2.9
[ 3238.096060] iwl3945 0000:03:00.0: Queue 0 stuck for 2000 ms.
[ 3238.096072] iwl3945 0000:03:00.0: On demand firmware reload
[ 3247.160053] iwl3945 0000:03:00.0: Queue 0 stuck for 2000 ms.
[ 3247.160065] iwl3945 0000:03:00.0: On demand firmware reload
[ 3256.224073] iwl3945 0000:03:00.0: Queue 0 stuck for 2000 ms.
[ 3256.224085] iwl3945 0000:03:00.0: On demand firmware reload
[ 3265.792060] iwl3945 0000:03:00.0: Queue 0 stuck for 2000 ms.
[ 3265.792072] iwl3945 0000:03:00.0: On demand firmware reload
[ 3274.856059] iwl3945 0000:03:00.0: Queue 0 stuck for 2000 ms.
[ 3274.856070] iwl3945 0000:03:00.0: On demand firmware reload
[ 3283.920074] iwl3945 0000:03:00.0: Queue 0 stuck for 2000 ms.
[ 3283.920086] iwl3945 0000:03:00.0: On demand firmware reload
[ 3292.984058] iwl3945 0000:03:00.0: Queue 0 stuck for 2000 ms.
[ 3292.984065] iwl3945 0000:03:00.0: On demand firmware reload
[ 3306.548061] iwl3945 0000:03:00.0: Queue 0 stuck for 2000 ms.
[ 3306.548073] iwl3945 0000:03:00.0: On demand firmware reload
[ 3315.612052] iwl3945 0000:03:00.0: Queue 0 stuck for 2000 ms.
[ 3315.612064] iwl3945 0000:03:00.0: On demand firmware reload
[ 3324.676059] iwl3945 0000:03:00.0: Queue 0 stuck for 2000 ms.
[ 3324.676071] iwl3945 0000:03:00.0: On demand firmware reload
[ 3333.740074] iwl3945 0000:03:00.0: Queue 0 stuck for 2000 ms.
[ 3333.740086] iwl3945 0000:03:00.0: On demand firmware reload
[ 3343.308065] iwl3945 0000:03:00.0: Queue 0 stuck for 2000 ms.
[ 3343.308077] iwl3945 0000:03:00.0: On demand firmware reload
[ 3352.372060] iwl3945 0000:03:00.0: Queue 0 stuck for 2000 ms.
[ 3352.372072] iwl3945 0000:03:00.0: On demand firmware reload
[ 3361.436079] iwl3945 0000:03:00.0: Queue 0 stuck for 2000 ms.
[ 3361.436086] iwl3945 0000:03:00.0: On demand firmware reload 
```

I do not want to open a new thread so I posted here.Thank you!

---

### Post by varunendra on 2013-09-12
Welcome to the forums steli2 !

Since the topic of this thread is kinda misleading and irrelevant (we don't want to install a driver, because we haven't found one that promises to work better, we want to fix the existing one), so I think it would have been better to start a new thread of your own. I'd request a mod to kindly do that if they concur with my opinion.

> **steli2 said:**
> 
[ 3361.436079] iwl3945 0000:03:00.0: [COLOR="#FF0000"]Queue 0 stuck for 2000 ms[/COLOR].
[ 3361.436086] iwl3945 0000:03:00.0: On demand firmware reload

The above is the very same infamous bug I mentioned in my previous post - the firmware just gets stuck ! Nobody could ever confirm a fixed cause and a fixed remedy for it.

We may try a few workarounds, but let's do some diagnostics first, please follow the "Wireless Script" link in my signature, follow the instructions in the linked post, and post back the report (or it's pastebin link) that the script generates.

Apart from the report, please also post the outputs of -
```
grep -iR [0-9a-z] /sys/module/iwl3945/parameters
grep -iR [0-9a-z] /sys/module/iwl_legacy/parameters
```

While posting the outputs, please wrap them within 'Code' tags. Follow the "Using Code Tags" link in my sig. to see how.

---

### Post by coffeecat on 2013-09-12
Moved to own thread and retitled.

---

### Post by steli2 on 2013-09-12
Thank you for reply! Here is the report from Wireless script:


```

*************** info trace ***************

***** uname -a *****

Linux qwerty-T12J 3.2.0-53-generic-pae #81-Ubuntu SMP Thu Aug 22 21:23:47 UTC 2013 i686 i686 i386 GNU/Linux

***** lsb_release *****

Distributor ID:    Ubuntu
Description:    Ubuntu 12.04.3 LTS
Release:    12.04
Codename:    precise

***** lspci *****

03:00.0 Network controller [0280]: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection [8086:4222] (rev 02)
    Subsystem: Intel Corporation PRO/Wireless 3945ABG Network Connection [8086:1001]
    Kernel driver in use: iwl3945
    Kernel modules: iwl3945
--
06:07.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ [10ec:8139] (rev 10)
    Subsystem: Packard Bell B.V. Device [1631:c022]
    Kernel driver in use: 8139too

***** lsusb *****

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 174f:a821 Syntek Web Cam - Packard Bell BU45, PB Easynote MX66-208W
Bus 002 Device 002: ID 0458:003a KYE Systems Corp. (Mouse Systems) NetScroll+ Mini Traveler / Genius NetScroll 120

***** PCMCIA Card Info *****


***** iwconfig *****

wlan0     IEEE 802.11abg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          

***** rfkill *****

0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

***** lsmod *****

iwlwifi               366509  0 
iwl3945                73186  0 
iwl_legacy             71187  1 iwl3945
mac80211              436493  3 iwlwifi,iwl3945,iwl_legacy
cfg80211              178877  4 iwlwifi,iwl3945,iwl_legacy,mac80211

***** nm-tool *****

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
    Address:         192.168.1.4
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1

    DNS:             192.168.1.1


- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            iwl3945
  State:             disconnected
  Default:           no
  HW Address:        <MAC address removed>

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 
    Iasmina's Network: Infra, <MAC address removed>, Freq 2447 MHz, Rate 54 Mb/s, Strength 62 WPA WPA2
    Lazar:           Infra, <MAC address removed>, Freq 2427 MHz, Rate 54 Mb/s, Strength 52 WPA2
    default:         Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 74 WEP
    Clicknet-9229:   Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 72 WPA2
    dd-wrt:          Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 32 WPA



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
                    Channel:4
                    Frequency:2.427 GHz (Channel 4)
                    Quality=39/70  Signal level=-71 dBm  
                    Encryption key on
                    ESSID:"Lazar"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000002054d4dadfe
                    Extra: Last beacon: 3212ms ago
                    IE: Unknown: 00054C617A6172
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030104
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD180050F2020101860003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C334E101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 2D1A4E101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C34040D0800000000000000000000000000000000000000
                    IE: Unknown: 3D16040D0800000000000000000000000000000000000000
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: Unknown: DD0A00037F04010000004000
                    IE: Unknown: DD0E0050F204104A0001101044000101
          Cell 02 - Address: <MAC address removed>
                    Channel:8
                    Frequency:2.447 GHz (Channel 8)
                    Quality=38/70  Signal level=-72 dBm  
                    Encryption key on
                    ESSID:"Iasmina's Network"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000556ec3a180
                    Extra: Last beacon: 3012ms ago
                    IE: Unknown: 00114961736D696E612773204E6574776F726B
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030108
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32043048606C
                    IE: Unknown: 2D1AEF1103FFFF0000000000000000000000000000000406E6E70D00
                    IE: Unknown: 3D1608071100000000000000000000000000000000000000
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101830003A4000027A4000042435E0062322F00
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: Unknown: DD260050F204104A0001101044000102104900140024E26002000101600000020001600100020001
          Cell 03 - Address: <MAC address removed>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=50/70  Signal level=-60 dBm  
                    Encryption key on
                    ESSID:"default"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000148977b816c
                    Extra: Last beacon: 2728ms ago
                    IE: Unknown: 000764656661756C74
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 03010B
                    IE: Unknown: 32040C183060
                    IE: Unknown: 050402030000
                    IE: Unknown: 2A0104
                    IE: Unknown: DD07000C4304000000
          Cell 04 - Address: <MAC address removed>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=48/70  Signal level=-62 dBm  
                    Encryption key on
                    ESSID:"Clicknet-9229"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000079429419d
                    Extra: Last beacon: 3344ms ago
                    IE: Unknown: 000D436C69636B6E65742D39323239
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030101
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD090010180200F02C0000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 05 - Address: <MAC address removed>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=25/70  Signal level=-85 dBm  
                    Encryption key on
                    ESSID:"dd-wrt"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000080338825f
                    Extra: Last beacon: 8068ms ago
                    IE: Unknown: 000664642D777274
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030106
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD090010180200F0000000
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00


***** resolv.conf *****

nameserver 127.0.0.1

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

filename:       /lib/modules/3.2.0-53-generic-pae/kernel/drivers/net/wireless/iwlwifi/iwlwifi.ko
alias:          iwlagn
license:        GPL
author:         Copyright(c) 2003-2011 Intel Corporation <ilw@linux.intel.com>
version:        in-tree:
description:    Intel(R) Wireless WiFi Link AGN driver for Linux
firmware:       iwlwifi-5150-2.ucode
firmware:       iwlwifi-5000-5.ucode
firmware:       iwlwifi-6000g2b-6.ucode
firmware:       iwlwifi-6000g2a-5.ucode
firmware:       iwlwifi-6050-5.ucode
firmware:       iwlwifi-6000-4.ucode
firmware:       iwlwifi-100-5.ucode
firmware:       iwlwifi-1000-5.ucode
firmware:       iwlwifi-135-6.ucode
firmware:       iwlwifi-105-6.ucode
firmware:       iwlwifi-2030-6.ucode
firmware:       iwlwifi-2000-6.ucode
srcversion:     50F8AB588F76D8CB83B1F60
alias:          pci:v00008086d00000892sv*sd00000466bc*sc*i*
alias:          pci:v00008086d00000893sv*sd00000266bc*sc*i*
alias:          pci:v00008086d00000892sv*sd00000066bc*sc*i*
alias:          pci:v00008086d00000892sv*sd00000462bc*sc*i*
alias:          pci:v00008086d00000893sv*sd00000262bc*sc*i*
alias:          pci:v00008086d00000892sv*sd00000062bc*sc*i*
alias:          pci:v00008086d00000894sv*sd00000822bc*sc*i*
alias:          pci:v00008086d00000894sv*sd00000426bc*sc*i*
alias:          pci:v00008086d00000895sv*sd00000226bc*sc*i*
alias:          pci:v00008086d00000894sv*sd00000026bc*sc*i*
alias:          pci:v00008086d00000894sv*sd00000422bc*sc*i*
alias:          pci:v00008086d00000895sv*sd00000222bc*sc*i*
alias:          pci:v00008086d00000894sv*sd00000022bc*sc*i*
alias:          pci:v00008086d0000088Esv*sd00004466bc*sc*i*
alias:          pci:v00008086d0000088Fsv*sd00004266bc*sc*i*
alias:          pci:v00008086d0000088Esv*sd00004066bc*sc*i*
alias:          pci:v00008086d0000088Esv*sd00004464bc*sc*i*
alias:          pci:v00008086d0000088Fsv*sd00004264bc*sc*i*
alias:          pci:v00008086d0000088Esv*sd00004064bc*sc*i*
alias:          pci:v00008086d0000088Esv*sd00004460bc*sc*i*
alias:          pci:v00008086d0000088Fsv*sd00004260bc*sc*i*
alias:          pci:v00008086d0000088Esv*sd00004060bc*sc*i*
alias:          pci:v00008086d00000887sv*sd00004466bc*sc*i*
alias:          pci:v00008086d00000888sv*sd00004266bc*sc*i*
alias:          pci:v00008086d00000887sv*sd00004066bc*sc*i*
alias:          pci:v00008086d00000887sv*sd00004462bc*sc*i*
alias:          pci:v00008086d00000888sv*sd00004262bc*sc*i*
alias:          pci:v00008086d00000887sv*sd00004062bc*sc*i*
alias:          pci:v00008086d00000890sv*sd00004822bc*sc*i*
alias:          pci:v00008086d00000890sv*sd00004426bc*sc*i*
alias:          pci:v00008086d00000891sv*sd00004226bc*sc*i*
alias:          pci:v00008086d00000890sv*sd00004026bc*sc*i*
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
alias:          pci:v00008086d00000082sv*sd00001341bc*sc*i*
alias:          pci:v00008086d00000085sv*sd0000C220bc*sc*i*
alias:          pci:v00008086d00000082sv*sd0000C020bc*sc*i*
alias:          pci:v00008086d00000085sv*sd00001316bc*sc*i*
alias:          pci:v00008086d00000085sv*sd00001311bc*sc*i*
alias:          pci:v00008086d00000082sv*sd00001326bc*sc*i*
alias:          pci:v00008086d00000082sv*sd00001321bc*sc*i*
alias:          pci:v00008086d00000082sv*sd00001307bc*sc*i*
alias:          pci:v00008086d00000082sv*sd00001306bc*sc*i*
alias:          pci:v00008086d00000082sv*sd00001301bc*sc*i*
alias:          pci:v00008086d00004239sv*sd00001316bc*sc*i*
alias:          pci:v00008086d00004239sv*sd00001311bc*sc*i*
alias:          pci:v00008086d00004238sv*sd00001111bc*sc*i*
alias:          pci:v00008086d0000422Csv*sd00001326bc*sc*i*
alias:          pci:v00008086d0000422Csv*sd00001321bc*sc*i*
alias:          pci:v00008086d0000422Csv*sd00001307bc*sc*i*
alias:          pci:v00008086d0000422Csv*sd00001306bc*sc*i*
alias:          pci:v00008086d0000422Csv*sd00001301bc*sc*i*
alias:          pci:v00008086d0000422Bsv*sd00001121bc*sc*i*
alias:          pci:v00008086d0000422Bsv*sd00001101bc*sc*i*
alias:          pci:v00008086d0000423Dsv*sd00001316bc*sc*i*
alias:          pci:v00008086d0000423Dsv*sd00001216bc*sc*i*
alias:          pci:v00008086d0000423Dsv*sd00001311bc*sc*i*
alias:          pci:v00008086d0000423Dsv*sd00001211bc*sc*i*
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
depends:        mac80211,cfg80211
intree:         Y
vermagic:       3.2.0-53-generic-pae SMP mod_unload modversions 686 
parm:           swcrypto:using crypto in software (default 0 [hardware]) (int)
parm:           queues_num:number of hw queues. (int)
parm:           11n_disable:disable 11n functionality (int)
parm:           amsdu_size_8K:enable 8K amsdu size (int)
parm:           fw_restart:restart firmware in case of error (int)
parm:           ucode_alternative:specify ucode alternative to use from ucode file (int)
parm:           antenna_coupling:specify antenna coupling in dB (defualt: 0 dB) (int)
parm:           bt_ch_inhibition:Enable BT channel inhibition (default: enable) (bool)
parm:           plcp_check:Check plcp health (default: 1 [enabled]) (bool)
parm:           ack_check:Check ack health (default: 0 [disabled]) (bool)
parm:           wd_disable:Disable stuck queue watchdog timer 0=system default, 1=disable, 2=enable (default: 0) (int)
parm:           bt_coex_active:enable wifi/bt co-exist (default: enable) (bool)
parm:           led_mode:0=system default, 1=On(RF On)/Off(RF Off), 2=blinking (default: 0) (int)
parm:           power_save:enable WiFi power management (default: disable) (bool)
parm:           power_level:default power save level (range from 1 - 5, default: 1) (int)
parm:           auto_agg:enable agg w/o check traffic load (default: enable) (bool)
parm:           no_sleep_autoadjust:don't automatically adjust sleep level according to maximum network latency (default: true) (bool)

filename:       /lib/modules/3.2.0-53-generic-pae/kernel/drivers/net/wireless/iwlegacy/iwl3945.ko
firmware:       iwlwifi-3945-2.ucode
license:        GPL
author:         Copyright(c) 2003-2011 Intel Corporation <ilw@linux.intel.com>
version:        in-tree:s
description:    Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux
srcversion:     301B04B4010DED41B0830D0
alias:          pci:v00008086d00004227sv*sd*bc*sc*i*
alias:          pci:v00008086d00004222sv*sd*bc*sc*i*
alias:          pci:v00008086d00004227sv*sd00001014bc*sc*i*
alias:          pci:v00008086d00004222sv*sd00001044bc*sc*i*
alias:          pci:v00008086d00004222sv*sd00001034bc*sc*i*
alias:          pci:v00008086d00004222sv*sd00001005bc*sc*i*
depends:        iwl-legacy,cfg80211,mac80211
intree:         Y
vermagic:       3.2.0-53-generic-pae SMP mod_unload modversions 686 
parm:           antenna:select antenna (1=Main, 2=Aux, default 0 [both]) (int)
parm:           swcrypto:using software crypto (default 1 [software]) (int)
parm:           disable_hw_scan:disable hardware scanning (default 1) (int)
parm:           fw_restart:restart firmware in case of error (int)

filename:       /lib/modules/3.2.0-53-generic-pae/kernel/drivers/net/wireless/iwlegacy/iwl-legacy.ko
license:        GPL
author:         Copyright(c) 2003-2011 Intel Corporation <ilw@linux.intel.com>
version:        in-tree:
description:    iwl-legacy: common functions for 3945 and 4965
srcversion:     D949E7611CAAE3FC9AEDE7D
depends:        mac80211,cfg80211
intree:         Y
vermagic:       3.2.0-53-generic-pae SMP mod_unload modversions 686 
parm:           led_mode:0=system default, 1=On(RF On)/Off(RF Off), 2=blinking (int)
parm:           bt_coex_active:enable wifi/bluetooth co-exist (bool)


***** udev rules *****

# PCI device 0x10ec:/sys/devices/pci0000:00/0000:00:1e.0/0000:06:07.0 (8139too)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

# PCI device 0x8086:/sys/devices/pci0000:00/0000:00:1c.1/0000:03:00.0 (iwl3945)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

# USB device 0x148f:0x2573 (usb)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan1"

***** dmesg *****

[   21.280622] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, in-tree:s
[   21.280627] iwl3945: Copyright(c) 2003-2011 Intel Corporation
[   21.280701] iwl3945 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   21.280718] iwl3945 0000:03:00.0: setting latency timer to 64
[   21.884749] iwl3945 0000:03:00.0: Tunable channels: 13 802.11bg, 23 802.11a channels
[   21.884754] iwl3945 0000:03:00.0: Detected Intel Wireless WiFi Link 3945ABG
[   21.884917] iwl3945 0000:03:00.0: irq 44 for MSI/MSI-X
[   21.916499] ieee80211 phy0: Selected rate control algorithm 'iwl-3945-rs'
[   22.513960] iwl3945 0000:03:00.0: loaded firmware version 15.32.2.9
[   22.591234] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   22.591622] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 3235.764178] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 3235.964086] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 3236.164095] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 3236.364086] wlan0: direct probe to <MAC address removed> timed out
[ 3238.096060] iwl3945 0000:03:00.0: Queue 0 stuck for 2000 ms.
[ 3238.096072] iwl3945 0000:03:00.0: On demand firmware reload
[ 3244.950422] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 3245.148089] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 3245.348082] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 3245.548086] wlan0: direct probe to <MAC address removed> timed out
[ 3247.160053] iwl3945 0000:03:00.0: Queue 0 stuck for 2000 ms.
[ 3247.160065] iwl3945 0000:03:00.0: On demand firmware reload
[ 3254.134467] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 3254.332087] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 3254.532094] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 3254.732085] wlan0: direct probe to <MAC address removed> timed out
[ 3256.224073] iwl3945 0000:03:00.0: Queue 0 stuck for 2000 ms.
[ 3256.224085] iwl3945 0000:03:00.0: On demand firmware reload
[ 3263.315621] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 3263.512070] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 3263.712081] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 3263.912728] wlan0: direct probe to <MAC address removed> timed out
[ 3265.792060] iwl3945 0000:03:00.0: Queue 0 stuck for 2000 ms.
[ 3265.792072] iwl3945 0000:03:00.0: On demand firmware reload
[ 3272.503911] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 3272.700081] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 3272.900062] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 3273.100050] wlan0: direct probe to <MAC address removed> timed out
[ 3274.856059] iwl3945 0000:03:00.0: Queue 0 stuck for 2000 ms.
[ 3274.856070] iwl3945 0000:03:00.0: On demand firmware reload
[ 3281.694475] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 3281.892058] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 3282.092086] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 3282.292089] wlan0: direct probe to <MAC address removed> timed out
[ 3283.920074] iwl3945 0000:03:00.0: Queue 0 stuck for 2000 ms.
[ 3283.920086] iwl3945 0000:03:00.0: On demand firmware reload
[ 3290.880408] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 3291.080092] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 3291.280085] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 3291.480092] wlan0: direct probe to <MAC address removed> timed out
[ 3292.984058] iwl3945 0000:03:00.0: Queue 0 stuck for 2000 ms.
[ 3292.984065] iwl3945 0000:03:00.0: On demand firmware reload
[ 3304.109019] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 3304.308092] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 3304.508086] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 3304.708097] wlan0: direct probe to <MAC address removed> timed out
[ 3306.548061] iwl3945 0000:03:00.0: Queue 0 stuck for 2000 ms.
[ 3306.548073] iwl3945 0000:03:00.0: On demand firmware reload
[ 3313.298423] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 3313.496078] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 3313.696080] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 3313.896062] wlan0: direct probe to <MAC address removed> timed out
[ 3315.612052] iwl3945 0000:03:00.0: Queue 0 stuck for 2000 ms.
[ 3315.612064] iwl3945 0000:03:00.0: On demand firmware reload
[ 3322.486546] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 3322.684084] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 3322.884073] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 3323.084066] wlan0: direct probe to <MAC address removed> timed out
[ 3324.676059] iwl3945 0000:03:00.0: Queue 0 stuck for 2000 ms.
[ 3324.676071] iwl3945 0000:03:00.0: On demand firmware reload
[ 3331.678278] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 3331.876052] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 3332.076051] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 3332.280050] wlan0: direct probe to <MAC address removed> timed out
[ 3333.740074] iwl3945 0000:03:00.0: Queue 0 stuck for 2000 ms.
[ 3333.740086] iwl3945 0000:03:00.0: On demand firmware reload
[ 3340.876129] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 3341.076083] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 3341.276094] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 3341.476087] wlan0: direct probe to <MAC address removed> timed out
[ 3343.308065] iwl3945 0000:03:00.0: Queue 0 stuck for 2000 ms.
[ 3343.308077] iwl3945 0000:03:00.0: On demand firmware reload
[ 3350.070469] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 3350.268084] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 3350.468095] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 3350.668080] wlan0: direct probe to <MAC address removed> timed out
[ 3352.372060] iwl3945 0000:03:00.0: Queue 0 stuck for 2000 ms.
[ 3352.372072] iwl3945 0000:03:00.0: On demand firmware reload
[ 3359.246447] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 3359.444095] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 3359.644080] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 3359.844083] wlan0: direct probe to <MAC address removed> timed out
[ 3361.436079] iwl3945 0000:03:00.0: Queue 0 stuck for 2000 ms.
[ 3361.436086] iwl3945 0000:03:00.0: On demand firmware reload
```

and also the outputs from:

grep -iR [0-9a-z] /sys/module/iwl3945/parameters
grep -iR [0-9a-z] /sys/module/iwl_legacy/parameters

```
qwerty@qwerty-T12J:~$ grep -iR [0-9a-z] /sys/module/iwl3945/parameters

/sys/module/iwl3945/parameters/fw_restart:1
/sys/module/iwl3945/parameters/disable_hw_scan:1
/sys/module/iwl3945/parameters/swcrypto:1
/sys/module/iwl3945/parameters/antenna:0

qwerty@qwerty-T12J:~$ grep -iR [0-9a-z] /sys/module/iwl_legacy/parameters

/sys/module/iwl_legacy/parameters/bt_coex_active:Y
/sys/module/iwl_legacy/parameters/led_mode:0
```

---

### Post by varunendra on 2013-09-13
> **steli2 said:**
> 
```

***** lsmod *****

**[COLOR="#FF0000"]iwlwifi  [/COLOR]**             366509  0 
iwl3945                73186  0 
iwl_legacy             71187  1 iwl3945
mac80211              436493  3 **[COLOR="#FF0000"]iwlwifi[/COLOR]**,iwl3945,iwl_legacy
cfg80211              178877  4 **[COLOR="#FF0000"]iwlwifi[/COLOR]**,iwl3945,iwl_legacy,mac80211
....
....
  Wireless Access Points 
    **Iasmina's Network**: Infra, <MAC address removed>, Freq 2447 MHz, Rate 54 Mb/s, Strength 62 **[COLOR="#FF0000"]WPA WPA2[/COLOR]**
    Lazar:           Infra, <MAC address removed>, Freq 2427 MHz, Rate 54 Mb/s, Strength 52 WPA2
    **default**:         Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 74 [COLOR="#FF0000"]WEP[/COLOR]
    Clicknet-9229:   Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 72 WPA2
    dd-wrt:          Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 32 WPA
....
```

The first and obvious thing that isn't good is the presence of both iwlwifi and iwl3845 drivers. As you can notice above, they are fighting for mac.. and cfg.. drivers. I don't think iwlwifi is correct driver for your card, so let's first prevent it from loading. Please do -
```
echo "blacklist iwlwifi" | sudo tee -a /etc/modprobe.d/blacklist.conf
sudo modprobe -rfv iwlwifi
sudo modprobe -rfv iwl3945
sudo modprobe -v iwl3945
```
Any improvement?

Next, which one of the above listed ones is/are your access point(s)? Since it is an already troubled driver, everything else should be at optimal setting to avoid external factors aiding the problem.

Usually, the optimal encryption setting (in the router/access-point) for Linux drivers is Pure **WPA2-PSK** with **AES** encryption. WPA/WPA2 mixed mode should be avoided at all costs (although it does work, but is mostly troublesome). Same for encryption algorithm - TKIP. It is outdated, weak and inefficient, so AES is recommended over TKIP.

This one is a legacy driver, so I'm not very sure which type of encryption should be optimal for it, but make it pure WPA2-PSK (AES) for now.

Also, if your router/AP supports N-channel, disable it (use b/g mode) in the router.

Please try these changes and post back the result.

**PS:**
If necessary, do a reboot after making above changes.

---

### Post by steli2 on 2013-09-13
No, there's no improvement.
My acces point is Clicknet-9229.I changed the security mode to WPA2-PSK with AES encryption.Rebooted the laptop.Nothing have been changed.It still ask me for password on and on.

---

### Post by varunendra on 2013-09-13
Okay, leave the encryption that way and try saving your security key in Network Manager :
NM drop-down list > Edit Connections.. > Wireless tab > double-click your connection > Wireless Security tab

In the same setting box, under "Wireless" tab, save your access point's MAC ID in the BSSID field

Save and close the settings and retry to connect. Does it help?

If not, then just for a test disable your wireless security in the router. Accordingly, make the changes in the NM saved settings too. Save, close and retry. If it connects, re-enable the security, and post back the progress.

After each change, check dmesg -
```
dmesg | grep iwl
```
Do the "...Queue 0 stuck for 2000 ms." and "On demand firmware reload" messages still occur? Does any of the changes cause it to stop?

Also, make sure iwlwifi is not loading now -
```
lsmod | grep iwl
```
It should show only iwl3945, not iwlwifi.

---

### Post by steli2 on 2013-09-13
Nothing's change.I disabled the router security but didn't connect.I save the router MAC in BSSID field.Nothing.
I tryed about some time ago to connect to an other acces point at work,which is a free network but same simptoms.
The "Queue 0 stuck for 2000 ms." and "On demand firmware reload" messages is still occur.
```
qwerty@qwerty-T12J:~$ dmesg | grep iwl
[   21.178325] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, in-tree:s
[   21.178331] iwl3945: Copyright(c) 2003-2011 Intel Corporation
[   21.178450] iwl3945 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   21.178467] iwl3945 0000:03:00.0: setting latency timer to 64
[   21.234393] iwl3945 0000:03:00.0: Tunable channels: 13 802.11bg, 23 802.11a channels
[   21.234398] iwl3945 0000:03:00.0: Detected Intel Wireless WiFi Link 3945ABG
[   21.234564] iwl3945 0000:03:00.0: irq 44 for MSI/MSI-X
[   21.252384] ieee80211 phy0: Selected rate control algorithm 'iwl-3945-rs'
[   22.329024] iwl3945 0000:03:00.0: loaded firmware version 15.32.2.9
[   39.924032] iwl3945 0000:03:00.0: Queue 0 stuck for 2000 ms.
[   39.924039] iwl3945 0000:03:00.0: On demand firmware reload
[   48.992039] iwl3945 0000:03:00.0: Queue 0 stuck for 2000 ms.
[   48.992046] iwl3945 0000:03:00.0: On demand firmware reload
[   58.556031] iwl3945 0000:03:00.0: Queue 0 stuck for 2000 ms.
[   58.556038] iwl3945 0000:03:00.0: On demand firmware reload
[   67.620046] iwl3945 0000:03:00.0: Queue 0 stuck for 2000 ms.
[   67.620058] iwl3945 0000:03:00.0: On demand firmware reload
[   76.684038] iwl3945 0000:03:00.0: Queue 0 stuck for 2000 ms.
[   76.684050] iwl3945 0000:03:00.0: On demand firmware reload
[   85.748047] iwl3945 0000:03:00.0: Queue 0 stuck for 2000 ms.
[   85.748058] iwl3945 0000:03:00.0: On demand firmware reload
[   95.312045] iwl3945 0000:03:00.0: Queue 0 stuck for 2000 ms.
[   95.312052] iwl3945 0000:03:00.0: On demand firmware reload
[  134.380035] iwl3945 0000:03:00.0: Queue 0 stuck for 2000 ms.
[  134.380041] iwl3945 0000:03:00.0: On demand firmware reload
[  143.448044] iwl3945 0000:03:00.0: Queue 0 stuck for 2000 ms.
[  143.448056] iwl3945 0000:03:00.0: On demand firmware reload
[  153.020046] iwl3945 0000:03:00.0: Queue 0 stuck for 2000 ms.
[  153.020058] iwl3945 0000:03:00.0: On demand firmware reload
[  162.088036] iwl3945 0000:03:00.0: Queue 0 stuck for 2000 ms.
[  162.088048] iwl3945 0000:03:00.0: On demand firmware reload
[  170.656040] iwl3945 0000:03:00.0: Queue 0 stuck for 2000 ms.
[  170.656052] iwl3945 0000:03:00.0: On demand firmware reload
[  180.220064] iwl3945 0000:03:00.0: Queue 0 stuck for 2000 ms.
[  180.220076] iwl3945 0000:03:00.0: On demand firmware reload
[  180.224592] iwl3945 0000:03:00.0: Can't stop Rx DMA.
[  189.792054] iwl3945 0000:03:00.0: Queue 0 stuck for 2000 ms.
[  189.792061] iwl3945 0000:03:00.0: On demand firmware reload
[  498.860061] iwl3945 0000:03:00.0: Queue 0 stuck for 2000 ms.
[  498.860072] iwl3945 0000:03:00.0: On demand firmware reload
[  507.928045] iwl3945 0000:03:00.0: Queue 0 stuck for 2000 ms.
[  507.928052] iwl3945 0000:03:00.0: On demand firmware reload
[  517.492052] iwl3945 0000:03:00.0: Queue 0 stuck for 2000 ms.
[  517.492063] iwl3945 0000:03:00.0: On demand firmware reload
[  526.556057] iwl3945 0000:03:00.0: Queue 0 stuck for 2000 ms.
[  526.556069] iwl3945 0000:03:00.0: On demand firmware reload
[  535.624041] iwl3945 0000:03:00.0: Queue 0 stuck for 2000 ms.
[  535.624053] iwl3945 0000:03:00.0: On demand firmware reload
[  544.692038] iwl3945 0000:03:00.0: Queue 0 stuck for 2000 ms.
[  544.692046] iwl3945 0000:03:00.0: On demand firmware reload
[  554.264031] iwl3945 0000:03:00.0: Queue 0 stuck for 2000 ms.
[  554.264039] iwl3945 0000:03:00.0: On demand firmware reload
[  554.268666] iwl3945 0000:03:00.0: Can't stop Rx DMA.
[  879.836059] iwl3945 0000:03:00.0: Queue 0 stuck for 2000 ms.
[  879.836071] iwl3945 0000:03:00.0: On demand firmware reload
[  888.904065] iwl3945 0000:03:00.0: Queue 0 stuck for 2000 ms.
[  888.904077] iwl3945 0000:03:00.0: On demand firmware reload
[  898.468051] iwl3945 0000:03:00.0: Queue 0 stuck for 2000 ms.
[  898.468062] iwl3945 0000:03:00.0: On demand firmware reload
[  907.532062] iwl3945 0000:03:00.0: Queue 0 stuck for 2000 ms.
[  907.532074] iwl3945 0000:03:00.0: On demand firmware reload
[  916.596050] iwl3945 0000:03:00.0: Queue 0 stuck for 2000 ms.
[  916.596062] iwl3945 0000:03:00.0: On demand firmware reload
[  925.660054] iwl3945 0000:03:00.0: Queue 0 stuck for 2000 ms.
[  925.660065] iwl3945 0000:03:00.0: On demand firmware reload
[ 7333.236053] iwl3945 0000:03:00.0: Queue 0 stuck for 2000 ms.
[ 7333.236060] iwl3945 0000:03:00.0: On demand firmware reload
[ 8173.800058] iwl3945 0000:03:00.0: Queue 0 stuck for 2000 ms.
[ 8173.800070] iwl3945 0000:03:00.0: On demand firmware reload
[ 8182.864063] iwl3945 0000:03:00.0: Queue 0 stuck for 2000 ms.
[ 8182.864075] iwl3945 0000:03:00.0: On demand firmware reload
[ 8191.932068] iwl3945 0000:03:00.0: Queue 0 stuck for 2000 ms.
[ 8191.932080] iwl3945 0000:03:00.0: On demand firmware reload
[ 8201.500045] iwl3945 0000:03:00.0: Queue 0 stuck for 2000 ms.
[ 8201.500056] iwl3945 0000:03:00.0: On demand firmware reload
[ 8210.564057] iwl3945 0000:03:00.0: Queue 0 stuck for 2000 ms.
[ 8210.564069] iwl3945 0000:03:00.0: On demand firmware reload
[ 8219.628070] iwl3945 0000:03:00.0: Queue 0 stuck for 2000 ms.
[ 8219.628082] iwl3945 0000:03:00.0: On demand firmware reload
[ 8229.192033] iwl3945 0000:03:00.0: Queue 0 stuck for 2000 ms.
[ 8229.192040] iwl3945 0000:03:00.0: On demand firmware reload

``` 

but the  iwlwifi is not loading now

```
qwerty@qwerty-T12J:~$ lsmod | grep iwl
iwl3945                73186  0 
iwl_legacy             71187  1 iwl3945
mac80211              436493  2 iwl3945,iwl_legacy
cfg80211              178877  3 iwl3945,iwl_legacy,mac80211

```

My opinion is that not the router settings are problem here.I can acces my wireless network with other laptop witch is running Windows and also with a couple of smartphones without changing the router or devices settings.

---

### Post by varunendra on 2013-09-13
Hmm.. only one more logical fix remaining, let's try that as well -

Please do -
```
echo "options iwl_legacy bt_coex_active=N" | sudo tee /etc/modprobe.d/iwl_legacy.conf
sudo modprobe -rfv iwl3945
sudo modprobe -v iwl3945
```
The second command should also remove the iwl_legacy driver, post back if it doesn't. It should be shown in the terminal.

Any difference in connectivity or "Queue stuck.." errors?

If not, then I'm afraid we can only try a few more shots, in the dark this time.

Oh, and please report back what channel modes are available in your router and what is the current setting (a/b/g/n, I believe **b/g** mode is best for this driver).


**PS:**
Just noticed your edit. Yes, the router may not be the problem, in fact in most cases it is not. But it is the driver you are using that is too crippled. We are making the router changes to possibly make it happy.

---

### Post by steli2 on 2013-09-13
> Please do -
     Code:
     echo "options iwl_legacy bt_coex_active=N" | sudo tee /etc/modprobe.d/iwl_legacy.conf
sudo modprobe -rfv iwl3945
sudo modprobe -v iwl3945 
The second command should also remove the iwl_legacy driver, post back if it doesn't. It should be shown in the terminal.

After I do the command above, I've been instantly connected to my wireless network.I'm working without wired connection now.
**Varunendra,billion of thanks to you for helping and for patience. **Now I have to see if I can connect with the router defaults settings,cause I changed the channels to b/g.

It seems to me that there was a conflict between iwl_legacy driver and iwl3945 driver?

---

### Post by varunendra on 2013-09-13
> **steli2 said:**
> It seems to me that there was a conflict between iwl_legacy driver and iwl3945 driver?

Nope, iwl_legacy is a dependency of iwl3945. They, combined with others like mac80211, cfg80211.. work like a team to make wifi work.

Like I mentioned in the beginning, the firmware that your card uses is buggy from the very begging since Intel released it, and they never cared to fix it. And that, combined with some other shortcomings in the iwl_legacy driver, make its functionality a matter of hit and miss. Sometimes it keeps working for years without a problem. But when it starts showing its bugs, only trial and error is a way to make it work, if at all..

So.. Congratulations for now, and hope it stays working nicely from now on. :)

**PS:**
Hope it is working with security key on. If not, try the recommended one (WPA2-PSK (AES)) first, and if it gives problems, try WPA, then WEP last.

---

### Post by steli2 on 2013-09-13
Yes, it is working after a series of rebooting both the laptop and router.Many thanks to **Varunendra** for help! \\:D/

---

### Post by varunendra on 2013-09-13
You're welcome ! And it's my pleasure to have this one solved. :)

---

