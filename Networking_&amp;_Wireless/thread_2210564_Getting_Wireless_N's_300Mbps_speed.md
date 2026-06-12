---
title: "Getting Wireless N's 300Mbps speed"
date: 2014-03-11
forum: Networking &amp; Wireless
---

### Post by pqwoerituytrueiwoq on 2014-03-11
I realize i am not going to get a true 300Mbps, my connection info read i am only getting a theoretical 150Mbps on my laptops side
My router is running DD-WRT, i got it set using WPA2 and the Turbo 40mhz frequenzy, wireless mode is set to support a mix of G and N devices
Currently i am getting anywher from 3.5-9MB/s (using wget over local network) and i was only 5ft (~1.5 meters) from the router

This is my wireless card's info on my laptop
```
02:00.0 Network controller: Ralink corp. RT5390 Wireless 802.11n 1T/1R PCIe
    Subsystem: Foxconn International, Inc. Device e054
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0, Cache Line Size: 64 bytes
    Interrupt: pin A routed to IRQ 17
    Region 0: Memory at de800000 (32-bit, non-prefetchable) [size=64K]
    Capabilities: [40] Power Management version 3
        Flags: PMEClk- DSI- D1- D2- AuxCurrent=375mA PME(D0-,D1-,D2-,D3hot-,D3cold-)
        Status: D0 NoSoftRst- PME-Enable- DSel=0 DScale=0 PME-
    Capabilities: [50] MSI: Enable- Count=1/32 Maskable- 64bit+
        Address: 0000000000000000  Data: 0000
    Capabilities: [70] Express (v2) Endpoint, MSI 00
        DevCap:    MaxPayload 128 bytes, PhantFunc 0, Latency L0s <512ns, L1 unlimited
            ExtTag- AttnBtn- AttnInd- PwrInd- RBE+ FLReset-
        DevCtl:    Report errors: Correctable- Non-Fatal- Fatal- Unsupported-
            RlxdOrd+ ExtTag- PhantFunc- AuxPwr- NoSnoop-
            MaxPayload 128 bytes, MaxReadReq 512 bytes
        DevSta:    CorrErr+ UncorrErr- FatalErr- UnsuppReq+ AuxPwr- TransPend-
        LnkCap:    Port #0, Speed 2.5GT/s, Width x1, ASPM L0s L1, Latency L0 <512ns, L1 <64us
            ClockPM+ Surprise- LLActRep- BwNot-
        LnkCtl:    ASPM Disabled; RCB 64 bytes Disabled- Retrain- CommClk+
            ExtSynch- ClockPM- AutWidDis- BWInt- AutBWInt-
        LnkSta:    Speed 2.5GT/s, Width x1, TrErr- Train- SlotClk+ DLActive- BWMgmt- ABWMgmt-
        DevCap2: Completion Timeout: Not Supported, TimeoutDis+
        DevCtl2: Completion Timeout: 50us to 50ms, TimeoutDis-
        LnkCtl2: Target Link Speed: 2.5GT/s, EnterCompliance- SpeedDis-, Selectable De-emphasis: -6dB
             Transmit Margin: Normal Operating Range, EnterModifiedCompliance- ComplianceSOS-
             Compliance De-emphasis: -6dB
        LnkSta2: Current De-emphasis Level: -6dB, EqualizationComplete-, EqualizationPhase1-
             EqualizationPhase2-, EqualizationPhase3-, LinkEqualizationRequest-
    Capabilities: [100 v1] Advanced Error Reporting
        UESta:    DLP- SDES- TLP- FCP- CmpltTO- CmpltAbrt- UnxCmplt- RxOF- MalfTLP- ECRC- UnsupReq- ACSViol-
        UEMsk:    DLP- SDES- TLP- FCP- CmpltTO- CmpltAbrt- UnxCmplt- RxOF- MalfTLP- ECRC- UnsupReq- ACSViol-
        UESvrt:    DLP+ SDES+ TLP- FCP+ CmpltTO- CmpltAbrt- UnxCmplt- RxOF+ MalfTLP+ ECRC- UnsupReq- ACSViol-
        CESta:    RxErr- BadTLP- BadDLLP- Rollover- Timeout- NonFatalErr+
        CEMsk:    RxErr- BadTLP- BadDLLP- Rollover- Timeout- NonFatalErr+
        AERCap:    First Error Pointer: 00, GenCap+ CGenEn- ChkCap+ ChkEn-
    Capabilities: [140 v1] Device Serial Number 00-00-00-9d-68-e6-06-e0
    Kernel driver in use: rt2800pci
```

---

### Post by varunendra on 2014-03-14
Kernel 3.11 ?

Please follow the "Wireless Script" link in my signature, download and run the script as per instructions there, and post back the report it generates.

Regardless of the what the report shows us, I think my suggestion would be to try backports-3.12... driver anyway, but let's see if something else can be adjusted to make it better..

By the way, by " 3.5-9MB/s ", you do mean that much, right? Means approx 28-73 Mb/s. I don't know much about overall performance of this card, so can't say what we can/should expect from it with Linux drivers.

---

### Post by Vladlenin5000 on 2014-03-14
*RT5390 Wireless 802.11n 1T/1R PCIe* can't do better than the theoretical 150Mbps (both Tx and Rx).

---

### Post by pqwoerituytrueiwoq on 2014-03-14
> **varunendra said:**
> Kernel 3.11 ?

Please follow the "Wireless Script" link in my signature, download and run the script as per instructions there, and post back the report it generates.

Regardless of the what the report shows us, I think my suggestion would be to try backports-3.12... driver anyway, but let's see if something else can be adjusted to make it better..

By the way, by " 3.5-9MB/s ", you do mean that much, right? Means approx 28-73 Mb/s. I don't know much about overall performance of this card, so can't say what we can/should expect from it with Linux drivers.
the 3.11 kernel is pretty old, i am using 3.14rc6
```
*************** info trace ***************

***** uname -a *****

Linux A54C-NB91 3.14.0-031400rc6-generic #201403100035 SMP Mon Mar 10 04:36:54 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux

***** lsb_release *****

Distributor ID:    Ubuntu
Description:    Ubuntu 13.10
Release:    13.10
Codename:    saucy

***** lspci *****

02:00.0 Network controller [0280]: Ralink corp. RT5390 Wireless 802.11n 1T/1R PCIe [1814:5390]
    Subsystem: Foxconn International, Inc. Device [105b:e054]
    Kernel driver in use: rt2800pci
--
04:00.0 Ethernet controller [0200]: Qualcomm Atheros AR8151 v2.0 Gigabit Ethernet [1969:1083] (rev c0)
    Subsystem: ASUSTeK Computer Inc. Device [1043:13c7]
    Kernel driver in use: atl1c

***** lsusb *****

Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 13d3:5710 IMC Networks UVC VGA Webcam
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

***** PCMCIA Card Info *****


***** iwconfig *****

wlan0     IEEE 802.11bgn  ESSID:"Chad's WiFi"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: <MAC address removed>   
          Bit Rate=58.5 Mb/s   Tx-Power=20 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=43/70  Signal level=-67 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:59  Invalid misc:36   Missed beacon:0


***** rfkill *****

0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: asus-wlan: Wireless LAN
    Soft blocked: no
    Hard blocked: no

***** modules *****

loop
lp
rtc

***** iw reg get *****

country 00:
    (2402 - 2472 @ 40), (3, 20)
    (2457 - 2482 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (2474 - 2494 @ 20), (3, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
    (5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS

***** route -n *****

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         10.0.0.1        0.0.0.0         UG    0      0        0 wlan0
10.0.0.0        0.0.0.0         255.255.255.0   U     9      0        0 wlan0

***** lsmod *****


***** iwlist chan *****

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
          Current Frequency:2.462 GHz (Channel 11)

rt2800pci              13650  0 
rt2800mmio             21082  1 rt2800pci
rt2800lib              95492  2 rt2800pci,rt2800mmio
rt2x00pci              13287  1 rt2800pci
rt2x00mmio             13661  2 rt2800pci,rt2800mmio
rt2x00lib              56125  5 rt2x00pci,rt2800lib,rt2800pci,rt2800mmio,rt2x00mmio
mac80211              676864  3 rt2x00lib,rt2x00pci,rt2800lib
cfg80211              531467  2 mac80211,rt2x00lib
eeprom_93cx6           13344  1 rt2800pci
crc_ccitt              12707  1 rt2800lib

***** nm-tool *****

NetworkManager Tool

State: connected (global)

- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            atl1c
  State:             unavailable
  Default:           no
  HW Address:        <MAC address removed>

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off


- Device: wlan0  [Chad's WiFi] -------------------------------------------------
  Type:              802.11 WiFi
  Driver:            rt2800pci
  State:             connected
  Default:           yes
  HW Address:        <MAC address removed>

  Capabilities:
    Speed:           58 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    *Chad's WiFi:    Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 53 WPA2

  IPv4 Settings:
    Address:         10.0.0.103
    Prefix:          24 (255.255.255.0)
    Gateway:         10.0.0.1

    DNS:             10.0.0.1



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
                    Quality=39/70  Signal level=-71 dBm  
                    Encryption key:on
                    ESSID:"Chad's WiFi"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000014f0afa978
                    Extra: Last beacon: 216ms ago
                    IE: Unknown: 000B4368616427732057694669
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0104
                    IE: Unknown: 32043048606C
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 2D1ACC111BFFFF000000000000000000000100000000000000000000
                    IE: Unknown: 3D160B000000000000000000000000000000000000000000
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
          Cell 02 - Address: <MAC address removed>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=41/70  Signal level=-69 dBm  
                    Encryption key:on
                    ESSID:""
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000014f0bcd580
                    Extra: Last beacon: 204ms ago
                    IE: Unknown: 0000
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 03010B
                    IE: Unknown: 050400020000
                    IE: Unknown: 2A0104
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00


***** resolv.conf *****

nameserver 127.0.1.1

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
blacklist ppdev
blacklist bnep
blacklist btusb
blacklist bluetooth

***** modinfo *****

filename:       /lib/modules/3.14.0-031400rc6-generic/kernel/drivers/net/wireless/rt2x00/rt2800pci.ko
license:        GPL
firmware:       rt2860.bin
description:    Ralink RT2800 PCI & PCMCIA Wireless LAN driver.
version:        2.3.0
author:         http://rt2x00.serialmonkey.com
srcversion:     D876F002AA85529257D61EB
alias:          pci:v00001814d0000539Fsv*sd*bc*sc*i*
alias:          pci:v00001814d0000539Bsv*sd*bc*sc*i*
alias:          pci:v00001814d0000539Asv*sd*bc*sc*i*
alias:          pci:v00001814d00005392sv*sd*bc*sc*i*
alias:          pci:v00001814d00005390sv*sd*bc*sc*i*
alias:          pci:v00001814d00005362sv*sd*bc*sc*i*
alias:          pci:v00001814d00005360sv*sd*bc*sc*i*
alias:          pci:v00001814d0000359Fsv*sd*bc*sc*i*
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
depends:        rt2x00lib,rt2800lib,rt2800mmio,rt2x00mmio,rt2x00pci,eeprom_93cx6
intree:         Y
vermagic:       3.14.0-031400rc6-generic SMP mod_unload modversions 
parm:           nohwcrypt:Disable hardware encryption. (bool)

filename:       /lib/modules/3.14.0-031400rc6-generic/kernel/drivers/net/wireless/rt2x00/rt2800mmio.ko
license:        GPL
description:    rt2800 MMIO library
version:        2.3.0
author:         http://rt2x00.serialmonkey.com
srcversion:     F196893F5F72140CA847345
depends:        rt2800lib,rt2x00lib,rt2x00mmio
intree:         Y
vermagic:       3.14.0-031400rc6-generic SMP mod_unload modversions 

filename:       /lib/modules/3.14.0-031400rc6-generic/kernel/drivers/net/wireless/rt2x00/rt2800lib.ko
license:        GPL
description:    Ralink RT2800 library
version:        2.3.0
author:         http://rt2x00.serialmonkey.com, Bartlomiej Zolnierkiewicz
srcversion:     01E9836C94BA9BB7EF723F5
depends:        rt2x00lib,mac80211,crc-ccitt
intree:         Y
vermagic:       3.14.0-031400rc6-generic SMP mod_unload modversions 

filename:       /lib/modules/3.14.0-031400rc6-generic/kernel/drivers/net/wireless/rt2x00/rt2x00pci.ko
license:        GPL
description:    rt2x00 pci library
version:        2.3.0
author:         http://rt2x00.serialmonkey.com
srcversion:     E940DB1895D1B7E99CD4B46
depends:        rt2x00lib,mac80211
intree:         Y
vermagic:       3.14.0-031400rc6-generic SMP mod_unload modversions 

filename:       /lib/modules/3.14.0-031400rc6-generic/kernel/drivers/net/wireless/rt2x00/rt2x00mmio.ko
license:        GPL
description:    rt2x00 mmio library
version:        2.3.0
author:         http://rt2x00.serialmonkey.com
srcversion:     07530604F5CE4EF69872C75
depends:        rt2x00lib
intree:         Y
vermagic:       3.14.0-031400rc6-generic SMP mod_unload modversions 

filename:       /lib/modules/3.14.0-031400rc6-generic/kernel/drivers/net/wireless/rt2x00/rt2x00lib.ko
license:        GPL
description:    rt2x00 library
version:        2.3.0
author:         http://rt2x00.serialmonkey.com
srcversion:     8F17D921F45A99A96062F2E
depends:        mac80211,cfg80211
intree:         Y
vermagic:       3.14.0-031400rc6-generic SMP mod_unload modversions 


***** udev rules *****

# PCI device 0x1969:/sys/devices/pci0000:00/0000:00:1c.5/0000:04:00.0 (atl1c)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

# PCI device 0x1814:/sys/devices/pci0000:00/0000:00:1c.1/0000:02:00.0 (rt2800pci)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

***** dmesg *****

[    5.500031] ieee80211 phy0: rt2x00_set_rt: Info - RT chipset 5390, rev 1502 detected
[    5.507201] ieee80211 phy0: rt2x00_set_rf: Info - RF chipset 5390 detected
[    7.491024] ieee80211 phy0: rt2x00lib_request_firmware: Info - Loading firmware file 'rt2860.bin'
[    7.492013] ieee80211 phy0: rt2x00lib_request_firmware: Info - Firmware detected - version: 0.34
[    9.820323] wlan0: authenticate with <MAC address removed>
[    9.836666] wlan0: send auth to <MAC address removed> (try 1/3)
[    9.838849] wlan0: authenticated
[    9.839908] wlan0: associate with <MAC address removed> (try 1/3)
[    9.843183] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=1)
[    9.843249] wlan0: associated

****************** done ******************


```

> **Vladlenin5000 said:**
> *RT5390 Wireless 802.11n 1T/1R PCIe* can't do better than the theoretical 150Mbps (both Tx and Rx).
thanks, what is strange is when my router is running at 300Mbit, my speeds are at most wireless g level 20Mbit or less throughput (that is 2ft from the router)
i managed to get a fairly solid 4-5MB/s by setting it to Full 20Mhz instead of Turbo 40Mhz or dynamic 20/40Mhz
this dropped my router's speed to theoretical 144.4444Mbps
using the higher speed settings results in speeds even below 1Mbps

on a side note i noticed my laptop's hardwire can only do 58MB/s, that is in a ram to ram test

---

### Post by varunendra on 2014-03-15
Have you tried the "nohwcrypt" parameter available with the driver yet?

Keep it to 20MHz band but try changing the channel to 1 or 14. As apparent in "iwlist scan", a neighbourhood access point is using the same channel as you (11), and has almost same signal strength (is it yours?). That may be causing some interference.

Apart from that, try this if you haven't already -
```
echo "options rt2800pci nohwcrypt=Y" | sudo tee /etc/modprobe.d/rt2800pci.conf
```

Followed by a reboot or -
```
sudo modprobe -rv rt2800pci
sudo modprobe -v rt2800pci
```

Assuming you have tested the speed over local network, not Internet, I think there is nothing else I can think of to optimizing. If it is the internet-only problem, I would also suggest to try changing the DNS to a relatively faster one in the computer itself (not relying of DNS forwarding in the router).

**PS:**
I am still on the 'Stone-age' kernel 3.2.., and the "ath9k" driver for my card is happier than the one in any of the newer/latest kernels :p (may not apply on RT5390 though, it seems the open source driver for that one has got better now).

---

### Post by pqwoerituytrueiwoq on 2014-03-15
only channels 1 and 6 are in use near me and those are really weak signals that go in and out 
while it seems may card supports ch 14, i think some rule in the US is to only use 1-13

i have a virtual SSID on using WEP for my ancient Nintendo DS that supports WEP security at best
128bit encryption + mac filter (a white list of 1) + 1 max client
i don't think i can make a wep access any harder to gain unauthorized access to

[[IMG]http://www.zimagez.com/miniature/screenshot-03152014-081304am.php[/IMG]]("http://www.zimagez.com/zimage/screenshot-03152014-081304am.php")

---

### Post by pqwoerituytrueiwoq on 2014-03-15
> **varunendra said:**
> 
Apart from that, try this if you haven't already -
```
echo "options rt2800pci nohwcrypt=Y" | sudo tee /etc/modprobe.d/rt2800pci.conf
```

Followed by a reboot or -
```
sudo modprobe -rv rt2800pci
sudo modprobe -v rt2800pci
```


i tried the -rv one and everything froze not even reisub worked
rebooted and it worked, switched to 40Mhz and got 7MB/s (edit distance killed the speed to below what i had)

looks like that config does what i suspected and moves the security work to the cpu

---

### Post by xicarusx on 2014-03-15
The problem probably is not your wireless card or driver. It is the fact you are using mixed mode on your Wireless Access Point. Turn off mixed N/G mode, and your problem should go away. 

You cannot have 802.11G on the same wireless network as 802.11N and expect speeds faster then 802.11G. In mixed mode it allows N to connect at a higher speed, but only if there are no clients connected that are using the G standard.

---

### Post by pqwoerituytrueiwoq on 2014-03-15
at this time there are no G clients connected, a speed drop while G clients (wii/nds/old laptop) are connected is ok with me
i ordered a new nic for my laptop that is rated for 300Mbit, so i can put my old card in that old laptop

speaking of that old laptop, using it on WPA2+ASE seems to reduced throughput on it by 25%

idealy what i want to do is have the router operate at 300Mbit and this laptops nic to run like it does if the router is running at 144.444Mbit

---

