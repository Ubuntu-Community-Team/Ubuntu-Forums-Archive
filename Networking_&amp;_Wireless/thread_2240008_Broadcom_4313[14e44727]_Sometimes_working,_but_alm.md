---
title: "Broadcom 4313[14e4:4727] Sometimes working, but almost not working."
date: 2014-08-17
forum: Networking &amp; Wireless
---

### Post by bclee on 2014-08-17
I bought a laptop recently, due to my old laptop is too slow for use, and I have looked forward to using the Thinkpad Series. (I bought Thinkpad Edge S430)

The seller of my new laptop warned me about using the broadcom wireless card on linux, but I thought I can fix it by googling and reading documents related to the Broadcom wireless.

But making the wireless lan card of my laptop is really challenging and annoying me. So I need a help.

Symptom:
Before rebooting my laptop, I read a sticky Thread: "How to install a driver for the Broadcom series of PCI wireless cards". I blacklistd the b43 ssb module. After doing that, Everything works fine.

But, After rebooting my laptop once more, nothing works. On NetworkManager, I can find my wireless connection, but it does not connect automatically. I manually enabled it, but connection never established.

Here is the result of the wireless_script. I wonder why /etc/modprobe.d/blacklist-b43.conf is disappered.
Also, I want to know why my 5Ghz Wifi connection is gone.
```


########## wireless info START ##########

Report from: 17 Aug 2014 21:41 KST +0900

Script from: 16 Aug 2014 22:12 UTC +0000

##### release #####

Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.1 LTS
Release:    14.04
Codename:    trusty

##### kernel #####

Linux 3.13.0-34-generic #60-Ubuntu SMP Wed Aug 13 15:45:27 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop #####

Ubuntu

##### lspci #####

03:00.0 Network controller [0280]: Broadcom Corporation BCM4313 802.11bgn Wireless Network Adapter [14e4:4727] (rev 01)
    Subsystem: Broadcom Corporation Device [14e4:0608]
    Kernel driver in use: bcma-pci-bridge

04:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 07)
    Subsystem: Lenovo Device [17aa:21fc]
    Kernel driver in use: r8169

##### lsusb #####

Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 002: ID 045e:0745 Microsoft Corp. Nano Transceiver v1.0 for Bluetooth
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info #####

##### rfkill #####

0: tpacpi_bluetooth_sw: Bluetooth
    Soft blocked: yes
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

##### lsmod #####

brcmsmac              563041  0 
cordic                 12574  1 brcmsmac
brcmutil               15618  1 brcmsmac
mac80211              630653  1 brcmsmac
wl                   4207846  0 
lib80211               14381  1 wl
cfg80211              484040  3 wl,brcmsmac,mac80211
bcma                   52096  2 brcmsmac
wmi                    19177  0 

##### interfaces #####

auto lo
iface lo inet loopback

##### ifconfig #####

eth0      Link encap:Ethernet  HWaddr <MAC addr eth0>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wlan0     Link encap:Ethernet  HWaddr <MAC addr wlan0>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

##### iwconfig #####

eth0      no wireless extensions.

lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=19 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          

##### route #####

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface

##### resolv.conf #####

##### nm-tool #####

NetworkManager Tool

State: disconnected

- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             unavailable
  Default:           no
  HW Address:        <MAC addr eth0>

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off

- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            brcmsmac
  State:             disconnected
  Default:           no
  HW Address:        <MAC addr wlan0>

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 
    iptime_Yooji:    Infra, <MAC addr iptime_Yooji>, Freq 2442 MHz, Rate 54 Mb/s, Strength 62 WPA WPA2

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

##### iw reg get #####

country 00:
    (2402 - 2472 @ 40), (3, 20)
    (2457 - 2482 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (2474 - 2494 @ 20), (3, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
    (5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS

##### iwlist channels #####

eth0      no frequency information.

lo        no frequency information.

wlan0     13 channels in total; available frequencies :
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

##### iwlist scan #####

eth0      Interface doesn't support scanning.

lo        Interface doesn't support scanning.

Channel occupancy:
     1   WLAPs on   Frequency:2.427 GHz (Channel 4)
     1   WLAPs on   Frequency:2.442 GHz (Channel 7)

wlan0     Scan completed :
          Cell 01 - Address: <MAC addr iptime_Yooji>
                    Channel:7
                    Frequency:2.442 GHz (Channel 7)
                    Quality=47/70  Signal level=-63 dBm  
                    Encryption key:on
                    ESSID:"iptime_Yooji"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000cab106a173
                    Extra: Last beacon: 13588ms ago
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC address>
                    Channel:4
                    Frequency:2.427 GHz (Channel 4)
                    Quality=44/70  Signal level=-66 dBm  
                    Encryption key:on
                    ESSID:"301"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000711907173
                    Extra: Last beacon: 452ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK

##### module infos #####

[brcmsmac]
filename:       /lib/modules/3.13.0-34-generic/kernel/drivers/net/wireless/brcm80211/brcmsmac/brcmsmac.ko
firmware:       brcm/bcm43xx_hdr-0.fw
firmware:       brcm/bcm43xx-0.fw
license:        Dual BSD/GPL
description:    Broadcom 802.11n wireless LAN driver.
author:         Broadcom Corporation
srcversion:     43D6897F7EB716081DF69BE
depends:        bcma,mac80211,brcmutil,cfg80211,cordic
intree:         Y
vermagic:       3.13.0-34-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        50:0B:C5:C8:7D:4B:11:5C:F3:C1:50:4F:7A:92:E2:33:C6:14:3D:58
sig_hashalgo:   sha512

[brcmutil]
filename:       /lib/modules/3.13.0-34-generic/kernel/drivers/net/wireless/brcm80211/brcmutil/brcmutil.ko
license:        Dual BSD/GPL
description:    Broadcom 802.11n wireless LAN driver utilities.
author:         Broadcom Corporation
srcversion:     E81EE4CBB6A7A689150D93D
depends:        
intree:         Y
vermagic:       3.13.0-34-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        50:0B:C5:C8:7D:4B:11:5C:F3:C1:50:4F:7A:92:E2:33:C6:14:3D:58
sig_hashalgo:   sha512

[wl]
filename:       /lib/modules/3.13.0-34-generic/updates/dkms/wl.ko
license:        MIXED/Proprietary
srcversion:     FF25FE784DC6BDFF69DAFCB
depends:        cfg80211,lib80211
vermagic:       3.13.0-34-generic SMP mod_unload modversions 
parm:           wl_txq_thresh:int
parm:           oneonly:int
parm:           piomode:int
parm:           instance_base:int
parm:           nompc:int
parm:           intf_name:string

[bcma]
filename:       /lib/modules/3.13.0-34-generic/kernel/drivers/bcma/bcma.ko
license:        GPL
description:    Broadcom's specific AMBA driver
srcversion:     E41B811D88783DD5BC38565
depends:        
intree:         Y
vermagic:       3.13.0-34-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        50:0B:C5:C8:7D:4B:11:5C:F3:C1:50:4F:7A:92:E2:33:C6:14:3D:58
sig_hashalgo:   sha512

##### module parameters #####

##### /etc/modules #####

lp
rtc
brcmsmac

##### blacklists #####

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
blacklist b43
blacklist ssb
blacklist garmin_gps
blacklist asus_acpi
blacklist snd_pcsp
blacklist pcspkr
blacklist amd76x_edac

##### udev rules #####

[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x10ec:0x8168 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC addr eth0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# PCI device 0x14e4:0x4727 (brcmsmac)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC addr wlan0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

##### dmesg #####

[    9.158559] psmouse serio2: trackpoint: IBM TrackPoint firmware: 0x0e, buttons: 3/3
[   11.816609] bcma: bus0: Found chip with id 0x4313, rev 0x01 and package 0x08
[   11.816647] bcma: bus0: Core 0 found: ChipCommon (manuf 0x4BF, id 0x800, rev 0x24, class 0x0)
[   11.816677] bcma: bus0: Core 1 found: IEEE 802.11 (manuf 0x4BF, id 0x812, rev 0x18, class 0x0)
[   11.816738] bcma: bus0: Core 2 found: PCIe (manuf 0x4BF, id 0x820, rev 0x11, class 0x0)
[   11.828568] bcma: bus0: Bus registered
[   11.836586] wl: module license 'MIXED/Proprietary' taints kernel.
[   11.837577] wl: module verification failed: signature and/or  required key missing - tainting kernel
[   12.231809] brcmsmac bcma0:0: mfg 4bf core 812 rev 24 class 0 irq 17
[   12.254305] ieee80211 phy0: registered radio enabled led device: brcmsmac-phy0:radio gpio: 243
[   16.241549] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: false (implement)
[   16.241558] brcmsmac bcma0:0: brcms_ops_config: change power-save mode: false (implement)
[   16.242182] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready (repeated 2 times)
[   54.030388] wlan0: authenticate with <MAC address>
[   54.033986] wlan0: direct probe to <MAC address> (try 1/3)

########## wireless info END ############

```

---

### Post by Hadaka on 2014-08-17
Hi, please do..
```
sudo apt-get remove --purge bcmwl-kernel-source
```

 the wl module got loaded.

---

### Post by bclee on 2014-08-17
Well.. I removed bcmwl-kernel-source, but still no luck.
Do I need to install the property driver of broadcom? I already installed linux-firmware-nonfree packages.

---

### Post by Hadaka on 2014-08-17
follow this guide..
[http://ubuntuforums.org/showthread.php?t=2214110](http://ubuntuforums.org/showthread.php?t=2214110)
your card is the last one on the list,,,also do special case #1

---

### Post by bclee on 2014-08-17
> **Hadaka said:**
> follow this guide..
[http://ubuntuforums.org/showthread.php?t=2214110](http://ubuntuforums.org/showthread.php?t=2214110)
your card is the last one on the list,,,also do special case #1

Yes. I read the guide post, and I did things in the guide.

I blacklisted b43 and wl (although I removed the property driver) and added brcmsmac in /etc/modules, so brcmsmac, brcmutil, bcma are loaded.
( I also read [http://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#Known_Issues](http://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#Known_Issues) )

Still not working... APs are detected (very slowly) and not connected. (I`m using AP named '301', using WPA2 / AES)

Here is the latest one of the result of script. Thanks in advance.

```


########## wireless info START ##########

Report from: 18 Aug 2014 03:35 KST +0900

Script from: 16 Aug 2014 22:12 UTC +0000

##### release #####

Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.1 LTS
Release:    14.04
Codename:    trusty

##### kernel #####

Linux 3.13.0-34-generic #60-Ubuntu SMP Wed Aug 13 15:45:27 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop #####

Ubuntu (from ~/.dmrc)

##### lspci #####

03:00.0 Network controller [0280]: Broadcom Corporation BCM4313 802.11bgn Wireless Network Adapter [14e4:4727] (rev 01)
    Subsystem: Broadcom Corporation Device [14e4:0608]
    Kernel driver in use: bcma-pci-bridge

04:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 07)
    Subsystem: Lenovo Device [17aa:21fc]
    Kernel driver in use: r8169

##### lsusb #####

Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 002: ID 045e:0745 Microsoft Corp. Nano Transceiver v1.0 for Bluetooth
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info #####

##### rfkill #####

0: tpacpi_bluetooth_sw: Bluetooth
    Soft blocked: yes
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

##### lsmod #####

brcmsmac              563041  0 
wmi                    19177  0 
cordic                 12574  1 brcmsmac
brcmutil               15618  1 brcmsmac
bcma                   52096  2 brcmsmac
mac80211              630653  1 brcmsmac
cfg80211              484040  2 brcmsmac,mac80211

##### interfaces #####

auto lo
iface lo inet loopback

##### ifconfig #####

eth0      Link encap:Ethernet  HWaddr <MAC addr eth0>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wlan0     Link encap:Ethernet  HWaddr <MAC addr wlan0>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

##### iwconfig #####

eth0      no wireless extensions.

lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=19 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          

##### route #####

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface

##### resolv.conf #####

##### nm-tool #####

NetworkManager Tool

State: disconnected

- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             unavailable
  Default:           no
  HW Address:        <MAC addr eth0>

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off

- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            brcmsmac
  State:             disconnected
  Default:           no
  HW Address:        <MAC addr wlan0>

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 
    iptime:          Infra, <MAC addr iptime>, Freq 2462 MHz, Rate 54 Mb/s, Strength 54 WPA2

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

##### iw reg get #####

country 00:
    (2402 - 2472 @ 40), (3, 20)
    (2457 - 2482 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (2474 - 2494 @ 20), (3, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
    (5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS

##### iwlist channels #####

eth0      no frequency information.

lo        no frequency information.

wlan0     13 channels in total; available frequencies :
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

##### iwlist scan #####

eth0      Interface doesn't support scanning.

lo        Interface doesn't support scanning.

Channel occupancy:
     1   WLAPs on   Frequency:2.442 GHz (Channel 7)

wlan0     Scan completed :
          Cell 01 - Address: <MAC address>
                    Channel:7
                    Frequency:2.442 GHz (Channel 7)
                    Quality=70/70  Signal level=-183 dBm  
                    Encryption key:on
                    ESSID:"iptime_Yooji"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000cfa4464173
                    Extra: Last beacon: 556ms ago
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK

##### module infos #####

[brcmsmac]
filename:       /lib/modules/3.13.0-34-generic/kernel/drivers/net/wireless/brcm80211/brcmsmac/brcmsmac.ko
firmware:       brcm/bcm43xx_hdr-0.fw
firmware:       brcm/bcm43xx-0.fw
license:        Dual BSD/GPL
description:    Broadcom 802.11n wireless LAN driver.
author:         Broadcom Corporation
srcversion:     43D6897F7EB716081DF69BE
depends:        bcma,mac80211,brcmutil,cfg80211,cordic
intree:         Y
vermagic:       3.13.0-34-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        50:0B:C5:C8:7D:4B:11:5C:F3:C1:50:4F:7A:92:E2:33:C6:14:3D:58
sig_hashalgo:   sha512

[brcmutil]
filename:       /lib/modules/3.13.0-34-generic/kernel/drivers/net/wireless/brcm80211/brcmutil/brcmutil.ko
license:        Dual BSD/GPL
description:    Broadcom 802.11n wireless LAN driver utilities.
author:         Broadcom Corporation
srcversion:     E81EE4CBB6A7A689150D93D
depends:        
intree:         Y
vermagic:       3.13.0-34-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        50:0B:C5:C8:7D:4B:11:5C:F3:C1:50:4F:7A:92:E2:33:C6:14:3D:58
sig_hashalgo:   sha512

[bcma]
filename:       /lib/modules/3.13.0-34-generic/kernel/drivers/bcma/bcma.ko
license:        GPL
description:    Broadcom's specific AMBA driver
srcversion:     E41B811D88783DD5BC38565
depends:        
intree:         Y
vermagic:       3.13.0-34-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        50:0B:C5:C8:7D:4B:11:5C:F3:C1:50:4F:7A:92:E2:33:C6:14:3D:58
sig_hashalgo:   sha512

##### module parameters #####

##### /etc/modules #####

lp
rtc
brcmsmac

##### blacklists #####

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
blacklist b43
blacklist wl

##### udev rules #####

[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x10ec:0x8168 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC addr eth0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# PCI device 0x14e4:0x4727 (brcmsmac)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC addr wlan0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

##### dmesg #####

[    8.701651] psmouse serio2: trackpoint: IBM TrackPoint firmware: 0x0e, buttons: 3/3
[   11.175721] bcma: bus0: Found chip with id 0x4313, rev 0x01 and package 0x08
[   11.175756] bcma: bus0: Core 0 found: ChipCommon (manuf 0x4BF, id 0x800, rev 0x24, class 0x0)
[   11.175784] bcma: bus0: Core 1 found: IEEE 802.11 (manuf 0x4BF, id 0x812, rev 0x18, class 0x0)
[   11.175838] bcma: bus0: Core 2 found: PCIe (manuf 0x4BF, id 0x820, rev 0x11, class 0x0)
[   11.188417] bcma: bus0: Bus registered
[   11.393104] brcmsmac bcma0:0: mfg 4bf core 812 rev 24 class 0 irq 17
[   11.453868] ieee80211 phy0: registered radio enabled led device: brcmsmac-phy0:radio gpio: 243
[   15.066734] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: false (implement)
[   15.066743] brcmsmac bcma0:0: brcms_ops_config: change power-save mode: false (implement)
[   15.067353] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready (repeated 2 times)

########## wireless info END ############

```

---

### Post by chili555 on 2014-08-17
Anything interesting in the logs?```
cat /var/log/syslog | grep -e wlan -e etwork
```

---

### Post by bclee on 2014-08-17
> **chili555 said:**
> Anything interesting in the logs?```
cat /var/log/syslog | grep -e wlan -e etwork
```

/var/log/syslog is fulled with lots of logs, most of them are generated by NetworkManager.

I differed with other logs, and I found some *wrong* behavior.
```

NetworkManager[974]: <info> Config: set interface ap_scan to 1
NetworkManager[974]: <info> (wlan0): supplicant interface state: disconnected -> inactive
wpa_supplicant[1079]: wlan0: SME: Trying to authenticate with <my AP`s mac> (SSID='301' freq=2462 MHz)
kernel: [   17.138375] wlan0: authenticate with c4:a8:1d:8c:bc:68
kernel: [   17.141976] wlan0: direct probe to <my AP`s mac> (try 1/3)
NetworkManager[974]: <info> (wlan0): supplicant interface state: inactive -> authenticating
kernel: [   17.342730] wlan0: direct probe to <my AP`s mac> (try 2/3)
kernel: [   17.546724] wlan0: direct probe to <my AP`s mac> (try 3/3)
kernel: [   17.750830] wlan0: authentication with <my AP`s mac> timed out
NetworkManager[974]: <info> (wlan0): supplicant interface state: authenticating -> disconnected

```

After authenticating, it has to associate with an AP. But my wlan card is direct probing, instead of associating. Finally they drop the connection, and repeat what it did indefinitely.

Any ideas?

---

### Post by chili555 on 2014-08-17
> /var/log/syslog is fulled with lots of logs, most of them are generated by NetworkManager.

I differed with other logs, and I found some *wrong* behavior.Meaning what? That you provided only what you thought I needed instead of what I requested?

In your scan, I don't see your network; evidently named 301. Please try again as we'd like to see how it's configured:```
sudo iwlist wlan0 scan
```

---

### Post by bclee on 2014-08-18
[COLOR=#000000][FONT=Arial]> **chili555 said:**
> Meaning what? That you provided only what you thought I needed instead of what I requested?[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]Okay I see. I posted all things below, but I cannot find any strange lines related to recoging wireless card. The problem (symptom) is behaviors of my wireless card.[/FONT][/COLOR] It is trying to connect indefinitely, so log is so long. I have to cut off rest of the log.

```

[COLOR=#000000][FONT=Arial]kernel: [   11.583806] type=1400 audit(1408337597.660:3): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=373 comm="apparmor_parser"[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]kernel: [   11.584101] type=1400 audit(1408337597.660:5): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=373 comm="apparmor_parser"[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]avahi-daemon[720]: Network interface enumeration completed.[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]NetworkManager[789]: <info> NetworkManager (version 0.9.8.8) is starting...[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]NetworkManager[789]: <info> Read config file /etc/NetworkManager/NetworkManager.conf[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]NetworkManager[789]: <info> WEXT support is enabled[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]NetworkManager[789]: <info> VPN: loaded org.freedesktop.NetworkManager.pptp[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]NetworkManager[789]: <info> DNS: loaded plugin dnsmasq[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]NetworkManager[789]:[/FONT][/COLOR][COLOR=#000000][FONT=Arial]SCPlugin-Ifupdown: init![/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]NetworkManager[789]:[/FONT][/COLOR][COLOR=#000000][FONT=Arial]SCPlugin-Ifupdown: update_system_hostname[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]NetworkManager[789]:   [/FONT][/COLOR][COLOR=#000000][FONT=Arial]interface-parser: parsing file /etc/network/interfaces[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]NetworkManager[789]:   [/FONT][/COLOR][COLOR=#000000][FONT=Arial]interface-parser: finished parsing file /etc/network/interfaces[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]NetworkManager[789]:[/FONT][/COLOR][COLOR=#000000][FONT=Arial]SCPluginIfupdown: management mode: unmanaged[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]NetworkManager[789]:[/FONT][/COLOR][COLOR=#000000][FONT=Arial]SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:1c.1/0000:03:00.0/bcma0:0/net/wlan0, iface: wlan0)[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]NetworkManager[789]:[/FONT][/COLOR][COLOR=#000000][FONT=Arial]SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:1c.1/0000:03:00.0/bcma0:0/net/wlan0, iface: wlan0): no ifupdown configuration found.[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]NetworkManager[789]:[/FONT][/COLOR][COLOR=#000000][FONT=Arial]SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:1c.3/0000:04:00.0/net/eth0, iface: eth0)[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]NetworkManager[789]:[/FONT][/COLOR][COLOR=#000000][FONT=Arial]SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:1c.3/0000:04:00.0/net/eth0, iface: eth0): no ifupdown configuration found.[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]NetworkManager[789]:[/FONT][/COLOR][COLOR=#000000][FONT=Arial]SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/lo, iface: lo)[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]NetworkManager[789]:[/FONT][/COLOR][COLOR=#000000][FONT=Arial]SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/lo, iface: lo): no ifupdown configuration found.[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]NetworkManager[789]:[/FONT][/COLOR][COLOR=#000000][FONT=Arial]SCPlugin-Ifupdown: end _init.[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]NetworkManager[789]: <info> Loaded plugin ifupdown: (C) 2008 Canonical Ltd.  To report bugs please use the NetworkManager mailing list.[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]NetworkManager[789]: <info> Loaded plugin keyfile: (c) 2007 - 2010 Red Hat, Inc.  To report bugs please use the NetworkManager mailing list.[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]NetworkManager[789]:[/FONT][/COLOR][COLOR=#000000][FONT=Arial]SCPlugin-Ofono: Acquired D-Bus service com.canonical.NMOfono[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]NetworkManager[789]:[/FONT][/COLOR][COLOR=#000000][FONT=Arial]SCPlugin-Ofono: init![/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]NetworkManager[789]:[/FONT][/COLOR][COLOR=#000000][FONT=Arial]SCPlugin-Ofono: end _init.[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]NetworkManager[789]: <info> Loaded plugin (null): (null)[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]NetworkManager[789]:[/FONT][/COLOR][COLOR=#000000][FONT=Arial]Ifupdown: get unmanaged devices count: 0[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]NetworkManager[789]:[/FONT][/COLOR][COLOR=#000000][FONT=Arial]SCPlugin-Ifupdown: (13474544) ... get_connections.[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]NetworkManager[789]:[/FONT][/COLOR][COLOR=#000000][FONT=Arial]SCPlugin-Ifupdown: (13474544) ... get_connections (managed=false): return empty list.[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]NetworkManager[789]:[/FONT][/COLOR][COLOR=#000000][FONT=Arial]keyfile: parsing 301 ...[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]NetworkManager[789]:[/FONT][/COLOR][COLOR=#000000][FONT=Arial]keyfile: [/FONT][/COLOR][COLOR=#000000][FONT=Arial]read connection '301'[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]NetworkManager[789]:[/FONT][/COLOR][COLOR=#000000][FONT=Arial]keyfile: parsing 123 ...[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]NetworkManager[789]:[/FONT][/COLOR][COLOR=#000000][FONT=Arial]keyfile: [/FONT][/COLOR][COLOR=#000000][FONT=Arial]read connection '123'[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]NetworkManager[789]:[/FONT][/COLOR][COLOR=#000000][FONT=Arial]SCPlugin-Ofono: (13256128) ... get_connections.[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]NetworkManager[789]:[/FONT][/COLOR][COLOR=#000000][FONT=Arial]SCPlugin-Ofono: (13256128) connections count: 0[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]NetworkManager[789]:[/FONT][/COLOR][COLOR=#000000][FONT=Arial]Ifupdown: get unmanaged devices count: 0[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]NetworkManager[789]: <info> monitoring kernel firmware directory '/lib/firmware'.[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]NetworkManager[789]: <info> rfkill1: found WiFi radio killswitch (at /sys/devices/pci0000:00/0000:00:1c.1/0000:03:00.0/bcma0:0/ieee80211/phy0/rfkill1) (driver brcmsmac)[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]NetworkManager[789]: <info> WiFi enabled by radio killswitch; enabled by state file[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]NetworkManager[789]: <info> WWAN enabled by radio killswitch; enabled by state file[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]NetworkManager[789]: <info> WiMAX enabled by radio killswitch; enabled by state file[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]NetworkManager[789]: <info> Networking is enabled by state file[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]NetworkManager[789]: <info> (wlan0): using nl80211 for WiFi device control[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]NetworkManager[789]: <info> (wlan0): driver supports Access Point (AP) mode[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]NetworkManager[789]: <info> (wlan0): new 802.11 WiFi device (driver: 'brcmsmac' ifindex: 3)[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]NetworkManager[789]: <info> (wlan0): exported as /org/freedesktop/NetworkManager/Devices/0[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]NetworkManager[789]: <info> (wlan0): device state change: unmanaged -> unavailable (reason 'managed') [10 20 2][/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]NetworkManager[789]: <info> (wlan0): bringing up device.[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]NetworkManager[789]: <info> (wlan0): preparing device.[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]NetworkManager[789]: <info> (wlan0): deactivating device (reason 'managed') [2][/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]NetworkManager[789]: <warn> failed to allocate link cache: (-12) Object not found[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]NetworkManager[789]: <info> (eth0): carrier is OFF[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]NetworkManager[789]: <info> (eth0): new Ethernet device (driver: 'r8169' ifindex: 2)[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]NetworkManager[789]: <info> (eth0): exported as /org/freedesktop/NetworkManager/Devices/1[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]NetworkManager[789]: <info> (eth0): device state change: unmanaged -> unavailable (reason 'managed') [10 20 2][/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]NetworkManager[789]: <info> (eth0): bringing up device.[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]kernel: [   14.975217] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]kernel: [   14.975482] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]NetworkManager[789]: <info> (eth0): preparing device.[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]NetworkManager[789]: <info> (eth0): deactivating device (reason 'managed') [2][/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]NetworkManager[789]: <info> Added default wired connection '&#50976;&#49440; &#50672;&#44208; 1' for /sys/devices/pci0000:00/0000:00:1c.3/0000:04:00.0/net/eth0[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]NetworkManager[789]: <warn> /sys/devices/virtual/net/lo: couldn't determine device driver; ignoring...[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]NetworkManager[789]: <warn> /sys/devices/virtual/net/lo: couldn't determine device driver; ignoring...[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]NetworkManager[789]: <info> urfkill disappeared from the bus[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]NetworkManager[789]: <info> wpa_supplicant started[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]NetworkManager[789]: <info> ModemManager available in the bus[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]NetworkManager[789]: <info> (wlan0) supports 4 scan SSIDs[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]NetworkManager[789]: <warn> Trying to remove a non-existant call id.[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]NetworkManager[789]: <info> (wlan0): supplicant interface state: starting -> ready[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]NetworkManager[789]: <info> (wlan0): device state change: unavailable -> disconnected (reason 'supplicant-available') [20 30 42][/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]wpa_supplicant[803]: wlan0: Reject scan trigger since one is already pending[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]NetworkManager[789]: <info> (wlan0): supplicant interface state: ready -> disconnected[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]NetworkManager[789]: <info> (wlan0) supports 4 scan SSIDs[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]wpa_supplicant[803]: wlan0: CTRL-EVENT-SCAN-STARTED[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]NetworkManager[789]: <info> Auto-activating connection '301'.[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]NetworkManager[789]: <info> Activation (wlan0) starting connection '301'[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]NetworkManager[789]: <info> (wlan0): device state change: disconnected -> prepare (reason 'none') [30 40 0][/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]NetworkManager[789]: <info> NetworkManager state is now CONNECTING[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]NetworkManager[789]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]NetworkManager[789]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]NetworkManager[789]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]NetworkManager[789]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]NetworkManager[789]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]NetworkManager[789]: <info> (wlan0): device state change: prepare -> config (reason 'none') [40 50 0][/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]NetworkManager[789]: <info> Activation (wlan0/wireless): connection '301' has security, and secrets exist.  No new secrets needed.[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]NetworkManager[789]: <info> Config: added 'ssid' value '301'[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]NetworkManager[789]: <info> Config: added 'scan_ssid' value '1'[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]NetworkManager[789]: <info> Config: added 'key_mgmt' value 'WPA-PSK'[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]NetworkManager[789]: <info> Config: added 'psk' value '<omitted>'[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]NetworkManager[789]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]NetworkManager[789]: <info> Config: set interface ap_scan to 1[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]NetworkManager[789]: <info> (wlan0): supplicant interface state: disconnected -> inactive[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]wpa_supplicant[803]: wlan0: SME: Trying to authenticate with c4:a8:1d:8c:bc:68 (SSID='301' freq=2462 MHz)[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]kernel: [   16.023339] wlan0: authenticate with c4:a8:1d:8c:bc:68[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]NetworkManager[789]: <info> (wlan0): supplicant interface state: inactive -> authenticating[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]kernel: [   16.026968] wlan0: direct probe to c4:a8:1d:8c:bc:68 (try 1/3)[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]kernel: [   16.230214] wlan0: direct probe to c4:a8:1d:8c:bc:68 (try 2/3)[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]kernel: [   16.434270] wlan0: direct probe to c4:a8:1d:8c:bc:68 (try 3/3)[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]kernel: [   16.638358] wlan0: authentication with c4:a8:1d:8c:bc:68 timed out[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]NetworkManager[789]: <info> (wlan0): supplicant interface state: authenticating -> disconnected[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]wpa_supplicant[803]: wlan0: CTRL-EVENT-SCAN-STARTED[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]NetworkManager[789]: <info> (wlan0): supplicant interface state: disconnected -> scanning[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]wpa_supplicant[803]: wlan0: SME: Trying to authenticate with c4:a8:1d:8c:bc:68 (SSID='301' freq=2462 MHz)[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]kernel: [   17.583014] wlan0: authenticate with c4:a8:1d:8c:bc:68[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]kernel: [   17.586347] wlan0: direct probe to c4:a8:1d:8c:bc:68 (try 1/3)[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]NetworkManager[789]: <info> (wlan0): supplicant interface state: scanning -> authenticating[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]kernel: [   17.786668] wlan0: direct probe to c4:a8:1d:8c:bc:68 (try 2/3)[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]kernel: [   17.990695] wlan0: direct probe to c4:a8:1d:8c:bc:68 (try 3/3)[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]kernel: [   18.194779] wlan0: authentication with c4:a8:1d:8c:bc:68 timed out[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]NetworkManager[789]: <info> (wlan0): supplicant interface state: authenticating -> disconnected[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]wpa_supplicant[803]: wlan0: CTRL-EVENT-SCAN-STARTED[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]NetworkManager[789]: <info> (wlan0): supplicant interface state: disconnected -> scanning[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]NetworkManager[789]: <info> WiFi hardware radio set enabled[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]wpa_supplicant[803]: wlan0: CTRL-EVENT-SCAN-STARTED[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]wpa_supplicant[803]: wlan0: SME: Trying to authenticate with c4:a8:1d:8c:bc:68 (SSID='301' freq=2462 MHz)[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]kernel: [   25.376986] wlan0: authenticate with c4:a8:1d:8c:bc:68[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]kernel: [   25.380271] wlan0: direct probe to c4:a8:1d:8c:bc:68 (try 1/3)[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]NetworkManager[789]: <info> (wlan0): supplicant interface state: scanning -> authenticating[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]kernel: [   25.580720] wlan0: direct probe to c4:a8:1d:8c:bc:68 (try 2/3)[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]kernel: [   25.784751] wlan0: direct probe to c4:a8:1d:8c:bc:68 (try 3/3)[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]kernel: [   25.988810] wlan0: authentication with c4:a8:1d:8c:bc:68 timed out[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]NetworkManager[789]: <info> (wlan0): supplicant interface state: authenticating -> disconnected[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]wpa_supplicant[803]: wlan0: CTRL-EVENT-SCAN-STARTED[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]NetworkManager[789]: <info> (wlan0): supplicant interface state: disconnected -> scanning[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]NetworkManager[789]: <warn> error requesting auth for org.freedesktop.NetworkManager.wifi.share.protected: (3) GDBus.Error:org.freedesktop.DBus.Error.NameHasNoOwner: GDBus.Error:org.freedesktop.DBus.Error.NameHasNoOwner: Could not get UID of name ':1.24': no such name[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]NetworkManager[789]: <warn> error requesting auth for org.freedesktop.NetworkManager.wifi.share.open: (3) GDBus.Error:org.freedesktop.DBus.Error.NameHasNoOwner: GDBus.Error:org.freedesktop.DBus.Error.NameHasNoOwner: Could not get UID of name ':1.24': no such name[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]wpa_supplicant[803]: message repeated 2 times: [ wlan0: CTRL-EVENT-SCAN-STARTED ][/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]wpa_supplicant[803]: wlan0: SME: Trying to authenticate with c4:a8:1d:8c:bc:68 (SSID='301' freq=2462 MHz)[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]kernel: [   39.504859] wlan0: authenticate with c4:a8:1d:8c:bc:68[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]kernel: [   39.508076] wlan0: direct probe to c4:a8:1d:8c:bc:68 (try 1/3)[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]NetworkManager[789]: <info> (wlan0): supplicant interface state: scanning -> authenticating[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]kernel: [   39.708476] wlan0: direct probe to c4:a8:1d:8c:bc:68 (try 2/3)[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]kernel: [   39.912527] wlan0: direct probe to c4:a8:1d:8c:bc:68 (try 3/3)[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]kernel: [   40.116569] wlan0: authentication with c4:a8:1d:8c:bc:68 timed out[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]wpa_supplicant[803]: wlan0: CTRL-EVENT-SSID-TEMP-DISABLED id=0 ssid="301" auth_failures=1 duration=10[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]NetworkManager[789]: <info> (wlan0): supplicant interface state: authenticating -> disconnected[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]NetworkManager[789]: <warn> Activation (wlan0/wireless): association took too long, failing activation.[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]NetworkManager[789]: <info> (wlan0): device state change: config -> failed (reason 'SSID not found') [50 120 53][/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]NetworkManager[789]: <info> NetworkManager state is now DISCONNECTED[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]NetworkManager[789]: <warn> Activation (wlan0) failed for connection '301'[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]NetworkManager[789]: <info> (wlan0): device state change: failed -> disconnected (reason 'none') [120 30 0][/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]NetworkManager[789]: <info> (wlan0): deactivating device (reason 'none') [0][/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]wpa_supplicant[803]: wlan0: CTRL-EVENT-SCAN-STARTED[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]NetworkManager[789]: <info> (wlan0): supplicant interface state: disconnected -> inactive[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]NetworkManager[789]: <info> Auto-activating connection '301'.[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]NetworkManager[789]: <info> Activation (wlan0) starting connection '301'[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]NetworkManager[789]: <info> (wlan0): device state change: disconnected -> prepare (reason 'none') [30 40 0][/FONT][/COLOR]

```


[COLOR=#000000][FONT=Arial]> **chili555 said:**
> In/ your scan, I don't see your network; evidently named 301.[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]That is the problem. I have two laptop, first one is what I want to fix wifi, and another is what I used for 5 months. They are located in same desk and latter one takes lots of WIFI signal.[/FONT][/COLOR]
```

[COLOR=#000000][FONT=Arial]wlan0 [/FONT][/COLOR][COLOR=#000000][FONT=Arial]Scan completed :[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Cell 01 - Address: C4:A8:1D:8C:BC:68[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Channel:11[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Frequency:2.462 GHz (Channel 11)[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Quality=60/70  Signal level=-50 dBm  [/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Encryption key:on[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]ESSID:"301"[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]9 Mb/s; 12 Mb/s; 18 Mb/s[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Mode:Master[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Extra:tsf=0000000972027ee2[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Extra: Last beacon: 4ms ago[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]IE: Unknown: 0003333031[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]IE: Unknown: 010882848B960C121824[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]IE: Unknown: 03010B[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]IE: Unknown: 2A0100[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]IE: Unknown: 32043048606C[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]IE: Unknown: 2D1A6E101EFFFF000000000000000000000000000000000000000000[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]IE: Unknown: 3D160B071100000000000000000000000000000000000000[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]IE: IEEE 802.11i/WPA2 Version 1[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Group Cipher : CCMP[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Pairwise Ciphers (1) : CCMP[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Authentication Suites (1) : PSK[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]IE: Unknown: DD1E00904C336E101EFFFF000000000000000000000000000000000000000000[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]IE: Unknown: DD1A00904C340B071100000000000000000000000000000000000000[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]IE: Unknown: DD0600E04C020160[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]IE: Unknown: DD8E0050F204104A0001101044000102103B000103104700107AB7D1D3EA8F86DD6A46C4A81D8CBC6810210012442D4C696E6B20436F72706F726174696F6E102300084449522D3835304C1024000830303030303030301042000830303030303030301054000800060050F2040001101100084449522D3835304C10080002278C103C0001031049000600372A000120[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Cell 02 - Address: 00:1D:93:36:91:C8[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Channel:1[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Frequency:2.412 GHz (Channel 1)[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Quality=45/70  Signal level=-65 dBm  [/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Encryption key:on[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]ESSID:"ollehEgg_000"[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]11 Mb/s; 12 Mb/s; 18 Mb/s[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Mode:Master[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Extra:tsf=00000035b5a6f1ff[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Extra: Last beacon: 2220ms ago[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]IE: Unknown: 000C6F6C6C65684567675F303030[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]IE: Unknown: 010882848B0C12961824[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]IE: Unknown: 030101[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]IE: Unknown: 050400010000[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]IE: Unknown: 2A0100[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]IE: Unknown: 32043048606C[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]IE: WPA Version 1[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Group Cipher : TKIP[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Pairwise Ciphers (2) : CCMP TKIP[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Authentication Suites (1) : PSK[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]IE: Unknown: DD06000A3B000000[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]IE: Unknown: DD180050F202010100000364000027A4000041435E0061322F00[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Cell 03 - Address: 00:26:66:E1:72:9E[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Channel:1[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Frequency:2.412 GHz (Channel 1)[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Quality=50/70  Signal level=-60 dBm  [/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Encryption key:on[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]ESSID:"alvert"[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]24 Mb/s; 36 Mb/s; 54 Mb/s[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Mode:Master[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Extra:tsf=000007fbe086c0ad[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Extra: Last beacon: 4ms ago[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]IE: Unknown: 0006616C76657274[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]IE: Unknown: 010882840B162430486C[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]IE: Unknown: 030101[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]IE: Unknown: 2A0100[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]IE: Unknown: 2F0100[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]IE: IEEE 802.11i/WPA2 Version 1[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Group Cipher : CCMP[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Pairwise Ciphers (1) : CCMP[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Authentication Suites (1) : PSK[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]IE: Unknown: 32040C121860[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]IE: Unknown: 2D1AF2181BFFFF000001000000000000000000000000000000000000[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]IE: Unknown: 3D16010D0000000000000000000000000000000000000000[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]IE: Unknown: DD750050F204104A0001101044000102103B00010310470010D96C7EFC2F8938F1EFBD6E5148BFA81210210006697054494D4510230008697054494D4541501024000A31323334353637383930104200033336301054000800060050F204000110110008697054494D454150100800020084103C000101[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]IE: Unknown: DD090010180200F02C0000[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Cell 04 - Address: 64:E5:99:89:78:D4[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Channel:11[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Frequency:2.462 GHz (Channel 11)[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Quality=42/70  Signal level=-68 dBm  [/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Encryption key:on[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]ESSID:"iptime"[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]9 Mb/s; 12 Mb/s; 18 Mb/s[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Mode:Master[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Extra:tsf=00000003250b6472[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Extra: Last beacon: 4ms ago[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]IE: Unknown: 0006697074696D65[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]IE: Unknown: 010882848B960C121824[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]IE: Unknown: 03010B[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]IE: Unknown: 2A0100[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]IE: Unknown: 32043048606C[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]IE: Unknown: 2D1A6F181FFFFF000000000000000000000000000000000000000000[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]IE: Unknown: 3D160B070000000000000000000000000000000000000000[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]IE: IEEE 802.11i/WPA2 Version 1[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Group Cipher : CCMP[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Pairwise Ciphers (1) : CCMP[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Authentication Suites (1) : PSK[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]IE: Unknown: DD1E00904C336F181FFFFF000000000000000000000000000000000000000000[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]IE: Unknown: DD1A00904C340B070000000000000000000000000000000000000000[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]IE: Unknown: DD0600E04C020160[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]IE: Unknown: DD9E0050F204104A0001101044000102103B0001031047001063041253101920061228AABBCCDDEEFF1021001B5265616C74656B2053656D69636F6E647563746F7220436F72702E1023000752544C387878781024000D45562D323030392D30322D30361042000F3132333435363738393031323334371054000800060050F2040001101100135265616C74656B20576972656C657373204150100800020080[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Cell 05 - Address: 10:F9:6F:F0:92:79[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Channel:4[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Frequency:2.427 GHz (Channel 4)[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Quality=20/70  Signal level=-90 dBm  [/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Encryption key:on[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]ESSID:"U+Net927B"[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]9 Mb/s; 12 Mb/s; 18 Mb/s[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Mode:Master[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Extra:tsf=000000cb14686115[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Extra: Last beacon: 4ms ago[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]IE: Unknown: 0009552B4E657439323742[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]IE: Unknown: 010882848B960C121824[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]IE: Unknown: 030104[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]IE: IEEE 802.11i/WPA2 Version 1[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Group Cipher : CCMP[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Pairwise Ciphers (1) : CCMP[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Authentication Suites (1) : PSK[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]IE: Unknown: 2A0100[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]IE: Unknown: 32043048606C[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]IE: Unknown: DD180050F2020101040003A4000027A4000042435E0062322F00[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]IE: Unknown: DD1E00904C334E101BFFFF000000000000000000000000000000000000000000[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]IE: Unknown: 2D1A4E101BFFFF000000000000000000000000000000000000000000[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]IE: Unknown: DD1A00904C3404051B00000000000000000000000000000000000000[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]IE: Unknown: 3D1604051B00000000000000000000000000000000000000[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]IE: Unknown: DD0900037F01010000FF7F[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]IE: Unknown: DD0A00037F04010000004000[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Cell 06 - Address: 10:F9:6F:F0:92:7A[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Channel:4[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Frequency:2.427 GHz (Channel 4)[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Quality=20/70  Signal level=-90 dBm  [/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Encryption key:on[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]ESSID:"U+zone"[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]9 Mb/s; 12 Mb/s; 18 Mb/s[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Mode:Master[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Extra:tsf=000000cb14687683[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Extra: Last beacon: 4ms ago[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]IE: Unknown: 0006552B7A6F6E65[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]IE: Unknown: 010882848B960C121824[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]IE: Unknown: 030104[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]IE: IEEE 802.11i/WPA2 Version 1[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Group Cipher : CCMP[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Pairwise Ciphers (1) : CCMP[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Authentication Suites (1) : 802.1x[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]IE: Unknown: 2A0100[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]IE: Unknown: 32043048606C[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]IE: Unknown: DD180050F2020101040003A4000027A4000042435E0062322F00[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]IE: Unknown: DD1E00904C334E101BFFFF000000000000000000000000000000000000000000[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]IE: Unknown: 2D1A4E101BFFFF000000000000000000000000000000000000000000[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]IE: Unknown: DD1A00904C3404051B00000000000000000000000000000000000000[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]IE: Unknown: 3D1604051B00000000000000000000000000000000000000[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]IE: Unknown: DD0900037F01010000FF7F[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]IE: Unknown: DD0A00037F04010000004000[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Cell 07 - Address: 00:08:9F:B9:C3:2C[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Channel:7[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Frequency:2.442 GHz (Channel 7)[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Quality=40/70  Signal level=-70 dBm  [/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Encryption key:on[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]ESSID:"iptime_Yooji"[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]9 Mb/s; 12 Mb/s; 18 Mb/s[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Mode:Master[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Extra:tsf=000000d8900f5a54[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Extra: Last beacon: 4ms ago[/FONT][/COLOR]

```

[COLOR=#000000][FONT=Arial]As you can see, it can detect 7 different APs, which is quite common in urban area.[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]But my BCM4313 works poory. Only 3 of them are detected (at current) and sometimes no wifi detected.[/FONT][/COLOR]
```

[COLOR=#000000][FONT=Arial]wlan0 [/FONT][/COLOR][COLOR=#000000][FONT=Arial]Scan completed :[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Cell 01 - Address: C4:A8:1D:8C:BC:68[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Channel:11[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Frequency:2.462 GHz (Channel 11)[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Quality=70/70  Signal level=-186 dBm  [/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Encryption key:on[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]ESSID:"301"[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]9 Mb/s; 12 Mb/s; 18 Mb/s[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Mode:Master[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Extra:tsf=000000097ab3f173[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Extra: Last beacon: 9112ms ago[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]IE: Unknown: 0003333031[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]IE: Unknown: 010882848B960C121824[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]IE: Unknown: 03010B[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]IE: Unknown: 050400010000[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]IE: Unknown: 2A0104[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]IE: Unknown: 32043048606C[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]IE: Unknown: 2D1A6E101EFFFF000000000000000000000000000000000000000000[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]IE: Unknown: 3D160B070000000000000000000000000000000000000000[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]IE: IEEE 802.11i/WPA2 Version 1[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Group Cipher : CCMP[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Pairwise Ciphers (1) : CCMP[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Authentication Suites (1) : PSK[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]IE: Unknown: DD1E00904C336E101EFFFF000000000000000000000000000000000000000000[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]IE: Unknown: DD1A00904C340B070000000000000000000000000000000000000000[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]IE: Unknown: DD0600E04C020160[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]IE: Unknown: DD1D0050F204104A0001101044000102103C0001031049000600372A000120[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Cell 02 - Address: 00:08:9F:B9:C3:2C[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Channel:7[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Frequency:2.442 GHz (Channel 7)[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Quality=70/70  Signal level=-188 dBm  [/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Encryption key:on[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]ESSID:"iptime_Yooji"[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]9 Mb/s; 12 Mb/s; 18 Mb/s[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Mode:Master[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Extra:tsf=000000d8980c0173[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Extra: Last beacon: 21600ms ago[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]IE: Unknown: 000C697074696D655F596F6F6A69[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]IE: Unknown: 010882848B960C121824[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]IE: Unknown: 030107[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]IE: Unknown: 050402030000[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]IE: Unknown: 2A0104[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]IE: Unknown: 32043048606C[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]IE: Unknown: 2D1A6E181EFFFF000000000000000000000000000000000000000000[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]IE: Unknown: 3D1607070000000000000000000000000000000000000000[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]IE: WPA Version 1[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Group Cipher : CCMP[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Pairwise Ciphers (1) : CCMP[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Authentication Suites (1) : PSK[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]IE: IEEE 802.11i/WPA2 Version 1[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Group Cipher : CCMP[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Pairwise Ciphers (1) : CCMP[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Authentication Suites (1) : PSK[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]IE: Unknown: DD1E00904C336E181EFFFF000000000000000000000000000000000000000000[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]IE: Unknown: DD1A00904C3407070000000000000000000000000000000000000000[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]IE: Unknown: DD0600E04C020160[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]IE: Unknown: DD0E0050F204104A0001101044000102[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Cell 03 - Address: 64:E5:99:89:78:D4[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Channel:11[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Frequency:2.462 GHz (Channel 11)[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Quality=70/70  Signal level=53 dBm  [/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Encryption key:on[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]ESSID:"iptime"[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]9 Mb/s; 12 Mb/s; 18 Mb/s[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Mode:Master[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Extra:tsf=000000032d03417e[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Extra: Last beacon: 21272ms ago[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]IE: Unknown: 0006697074696D65[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]IE: Unknown: 010882848B960C121824[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]IE: Unknown: 03010B[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]IE: Unknown: 050402030000[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]IE: Unknown: 2A0104[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]IE: Unknown: 32043048606C[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]IE: Unknown: 2D1A6F181FFFFF000000000000000000000000000000000000000000[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]IE: Unknown: 3D160B070000000000000000000000000000000000000000[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]IE: IEEE 802.11i/WPA2 Version 1[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Group Cipher : CCMP[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Pairwise Ciphers (1) : CCMP[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Authentication Suites (1) : PSK[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]IE: Unknown: DD1E00904C336F181FFFFF000000000000000000000000000000000000000000[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]IE: Unknown: DD1A00904C340B070000000000000000000000000000000000000000[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]IE: Unknown: DD0600E04C020160[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]IE: Unknown: DD0E0050F204104A0001101044000102[/FONT][/COLOR]

```

[COLOR=#000000][FONT=Arial]Aha.... Signal level=-188 dBm . It is almost unusable. Right?[/FONT][/COLOR]

What I want to know is..
1) Does my wifi card(BCM4313) look like well-configured?
2) DO I have to use open-source driver(bcma / brcmsmac)? How about closed one?

---

### Post by bclee on 2014-08-18
Also, the property-driver is almost not working, but better than bcma/brcmsmac. It can be connected :) but it works with absolutely slow speed. (less than 20Kb/s, with loss > 50%)

Below is the result of loading of the property-driver(wl).
```


########## wireless info START ##########

Report from: 18 Aug 2014 17:43 KST +0900

Script from: 16 Aug 2014 22:12 UTC +0000

##### release #####

Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.1 LTS
Release:    14.04
Codename:    trusty

##### kernel #####

Linux 3.13.0-34-generic #60-Ubuntu SMP Wed Aug 13 15:45:27 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop #####

Ubuntu

##### lspci #####

03:00.0 Network controller [0280]: Broadcom Corporation BCM4313 802.11bgn Wireless Network Adapter [14e4:4727] (rev 01)
    Subsystem: Broadcom Corporation Device [14e4:0608]
    Kernel driver in use: wl

04:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 07)
    Subsystem: Lenovo Device [17aa:21fc]
    Kernel driver in use: r8169

##### lsusb #####

Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 002: ID 045e:0745 Microsoft Corp. Nano Transceiver v1.0 for Bluetooth
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info #####

##### rfkill #####

0: tpacpi_bluetooth_sw: Bluetooth
    Soft blocked: yes
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
2: brcmwl-0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

##### lsmod #####

wl                   4207846  0 
lib80211               14381  2 wl,lib80211_crypt_tkip
cfg80211              484040  1 wl
wmi                    19177  0 

##### interfaces #####

auto lo
iface lo inet loopback

##### ifconfig #####

eth0      Link encap:Ethernet  HWaddr <MAC addr eth0>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wlan0     Link encap:Ethernet  HWaddr <MAC addr wlan0>  
          inet addr:192.168.1.18  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::aed:b9ff:fee2:cdb7/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:7 errors:0 dropped:0 overruns:0 frame:767
          TX packets:64 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1444 (1.4 KB)  TX bytes:9469 (9.4 KB)
          Interrupt:17 

##### iwconfig #####

eth0      no wireless extensions.

lo        no wireless extensions.

wlan0     IEEE 802.11abg  ESSID:"301"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: <MAC addr 301>   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          

##### route #####

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 wlan0
192.168.1.0     0.0.0.0         255.255.255.0   U     9      0        0 wlan0

##### resolv.conf #####

nameserver 127.0.1.1

##### nm-tool #####

NetworkManager Tool

State: connected (global)

- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             unavailable
  Default:           no
  HW Address:        <MAC addr eth0>

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off

- Device: wlan0  [301] ---------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            wl
  State:             connected
  Default:           yes
  HW Address:        <MAC addr wlan0>

  Capabilities:
    Speed:           72 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    alvert:          Infra, <MAC addr alvert>, Freq 2412 MHz, Rate 54 Mb/s, Strength 68 WPA2
    iptime:          Infra, <MAC addr iptime>, Freq 2462 MHz, Rate 54 Mb/s, Strength 46 WPA2
    U+Net927B:       Infra, <MAC addr U+Net927B>, Freq 2427 MHz, Rate 54 Mb/s, Strength 38 WPA2
    iptime_Yooji:    Infra, <MAC addr iptime_Yooji>, Freq 2442 MHz, Rate 54 Mb/s, Strength 38 WPA WPA2
    ollehEgg_000:    Infra, <MAC addr ollehEgg_000>, Freq 2412 MHz, Rate 54 Mb/s, Strength 35 WPA
    *301:            Infra, <MAC addr 301>, Freq 2462 MHz, Rate 54 Mb/s, Strength 100 WPA2

  IPv4 Settings:
    Address:         192.168.1.18
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1

    DNS:             210.94.0.73
    DNS:             168.188.1.1
    DNS:             8.8.8.8

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

##### iw reg get #####

country 00:
    (2402 - 2472 @ 40), (3, 20)
    (2457 - 2482 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (2474 - 2494 @ 20), (3, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
    (5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS

##### iwlist channels #####

eth0      no frequency information.

lo        no frequency information.

wlan0     26 channels in total; available frequencies :
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
          Channel 36 : 5.18 GHz
          Channel 38 : 5.19 GHz
          Channel 40 : 5.2 GHz
          Channel 42 : 5.21 GHz
          Channel 44 : 5.22 GHz
          Channel 46 : 5.23 GHz
          Channel 48 : 5.24 GHz
          Channel 149 : 5.745 GHz
          Channel 153 : 5.765 GHz
          Channel 157 : 5.785 GHz
          Channel 161 : 5.805 GHz
          Channel 165 : 5.825 GHz
          Current Frequency:2.462 GHz (Channel 11)

##### iwlist scan #####

eth0      Interface doesn't support scanning.

lo        Interface doesn't support scanning.

Channel occupancy:
     3   WLAPs on   Frequency:2.412 GHz (Channel 1)
     1   WLAPs on   Frequency:2.442 GHz (Channel 7)
     2   WLAPs on   Frequency:2.462 GHz (Channel 11)

wlan0     Scan completed :
          Cell 01 - Address: <MAC addr ollehEgg_000>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=27/70  Signal level=-83 dBm  
                    Encryption key:on
                    ESSID:"ollehEgg_000"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 32ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC addr alvert>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=70/70  Signal level=-185 dBm  
                    Encryption key:on
                    ESSID:"alvert"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 32ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: <MAC addr iptime_Yooji>
                    Channel:7
                    Frequency:2.442 GHz (Channel 7)
                    Quality=70/70  Signal level=43 dBm  
                    Encryption key:on
                    ESSID:"iptime_Yooji"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 32ms ago
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 04 - Address: <MAC addr 301>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=70/70  Signal level=-161 dBm  
                    Encryption key:on
                    ESSID:"301"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 32ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 05 - Address: <MAC addr iptime>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=70/70  Signal level=58 dBm  
                    Encryption key:on
                    ESSID:"iptime"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 32ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 06 - Address: <MAC address>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=70/70  Signal level=44 dBm  
                    Encryption key:on
                    ESSID:"\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 29980ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK

##### module infos #####

[wl]
filename:       /lib/modules/3.13.0-34-generic/updates/dkms/wl.ko
license:        MIXED/Proprietary
srcversion:     FF25FE784DC6BDFF69DAFCB
depends:        cfg80211,lib80211
vermagic:       3.13.0-34-generic SMP mod_unload modversions 
parm:           wl_txq_thresh:int
parm:           oneonly:int
parm:           piomode:int
parm:           instance_base:int
parm:           nompc:int
parm:           intf_name:string

##### module parameters #####

##### /etc/modules #####

lp
rtc

##### blacklists #####

[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci

[/etc/modprobe.d/blacklist-bcm43.conf]
blacklist b43
blacklist b43legacy
blacklist ssb
blacklist bcm43xx
blacklist brcm80211
blacklist brcmfmac
blacklist brcmsmac
blacklist bcma

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

[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x10ec:0x8168 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC addr eth0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# PCI device 0x14e4:0x4727 (brcmsmac)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC addr wlan0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

##### dmesg #####

[    8.707185] psmouse serio2: trackpoint: IBM TrackPoint firmware: 0x0e, buttons: 3/3
[   11.615097] wl: module license 'MIXED/Proprietary' taints kernel.
[   11.616277] wl: module verification failed: signature and/or  required key missing - tainting kernel
[   11.665560] INFO @wl_cfg80211_attach : Registered CFG80211 phy
[   11.797960] wlan0: Broadcom BCM4727 802.11 Hybrid Wireless Controller 6.30.223.141 (r415941)
[   44.551047] ERROR @wl_dev_intvar_get : error (-1)
[   44.551050] ERROR @wl_cfg80211_get_tx_power : error (-1)

########## wireless info END ############

```

---

### Post by bclee on 2014-08-18
Also, the property-driver is almost not working, but better than  bcma/brcmsmac. It can be connected :) but it works with absolutely slow  speed. (less than 20Kb/s, with loss > 50%)

Below is the result of loading of the property-driver(wl).
```


########## wireless info START ##########

Report from: 18 Aug 2014 17:43 KST +0900

Script from: 16 Aug 2014 22:12 UTC +0000

##### release #####

Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.1 LTS
Release:    14.04
Codename:    trusty

##### kernel #####

Linux 3.13.0-34-generic #60-Ubuntu SMP Wed Aug 13 15:45:27 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop #####

Ubuntu

##### lspci #####

03:00.0 Network controller [0280]: Broadcom Corporation BCM4313 802.11bgn Wireless Network Adapter [14e4:4727] (rev 01)
    Subsystem: Broadcom Corporation Device [14e4:0608]
    Kernel driver in use: wl

04:00.0  Ethernet controller [0200]: Realtek Semiconductor Co., Ltd.  RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168]  (rev 07)
    Subsystem: Lenovo Device [17aa:21fc]
    Kernel driver in use: r8169

##### lsusb #####

Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 002: ID 045e:0745 Microsoft Corp. Nano Transceiver v1.0 for Bluetooth
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info #####

##### rfkill #####

0: tpacpi_bluetooth_sw: Bluetooth
    Soft blocked: yes
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
2: brcmwl-0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

##### lsmod #####

wl                   4207846  0 
lib80211               14381  2 wl,lib80211_crypt_tkip
cfg80211              484040  1 wl
wmi                    19177  0 

##### interfaces #####

auto lo
iface lo inet loopback

##### ifconfig #####

eth0      Link encap:Ethernet  HWaddr <MAC addr eth0>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wlan0     Link encap:Ethernet  HWaddr <MAC addr wlan0>  
          inet addr:192.168.1.18  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::aed:b9ff:fee2:cdb7/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:7 errors:0 dropped:0 overruns:0 frame:767
          TX packets:64 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1444 (1.4 KB)  TX bytes:9469 (9.4 KB)
          Interrupt:17 

##### iwconfig #####

eth0      no wireless extensions.

lo        no wireless extensions.

wlan0     IEEE 802.11abg  ESSID:"301"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: <MAC addr 301>   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          

##### route #####

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 wlan0
192.168.1.0     0.0.0.0         255.255.255.0   U     9      0        0 wlan0

##### resolv.conf #####

nameserver 127.0.1.1

##### nm-tool #####

NetworkManager Tool

State: connected (global)

- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             unavailable
  Default:           no
  HW Address:        <MAC addr eth0>

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off

- Device: wlan0  [301] ---------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            wl
  State:             connected
  Default:           yes
  HW Address:        <MAC addr wlan0>

  Capabilities:
    Speed:           72 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    alvert:          Infra, <MAC addr alvert>, Freq 2412 MHz, Rate 54 Mb/s, Strength 68 WPA2
    iptime:          Infra, <MAC addr iptime>, Freq 2462 MHz, Rate 54 Mb/s, Strength 46 WPA2
    U+Net927B:       Infra, <MAC addr U+Net927B>, Freq 2427 MHz, Rate 54 Mb/s, Strength 38 WPA2
    iptime_Yooji:    Infra, <MAC addr iptime_Yooji>, Freq 2442 MHz, Rate 54 Mb/s, Strength 38 WPA WPA2
    ollehEgg_000:    Infra, <MAC addr ollehEgg_000>, Freq 2412 MHz, Rate 54 Mb/s, Strength 35 WPA
    *301:            Infra, <MAC addr 301>, Freq 2462 MHz, Rate 54 Mb/s, Strength 100 WPA2

  IPv4 Settings:
    Address:         192.168.1.18
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1

    DNS:             210.94.0.73
    DNS:             168.188.1.1
    DNS:             8.8.8.8

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

##### iw reg get #####

country 00:
    (2402 - 2472 @ 40), (3, 20)
    (2457 - 2482 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (2474 - 2494 @ 20), (3, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
    (5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS

##### iwlist channels #####

eth0      no frequency information.

lo        no frequency information.

wlan0     26 channels in total; available frequencies :
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
          Channel 36 : 5.18 GHz
          Channel 38 : 5.19 GHz
          Channel 40 : 5.2 GHz
          Channel 42 : 5.21 GHz
          Channel 44 : 5.22 GHz
          Channel 46 : 5.23 GHz
          Channel 48 : 5.24 GHz
          Channel 149 : 5.745 GHz
          Channel 153 : 5.765 GHz
          Channel 157 : 5.785 GHz
          Channel 161 : 5.805 GHz
          Channel 165 : 5.825 GHz
          Current Frequency:2.462 GHz (Channel 11)

##### iwlist scan #####

eth0      Interface doesn't support scanning.

lo        Interface doesn't support scanning.

Channel occupancy:
     3   WLAPs on   Frequency:2.412 GHz (Channel 1)
     1   WLAPs on   Frequency:2.442 GHz (Channel 7)
     2   WLAPs on   Frequency:2.462 GHz (Channel 11)

wlan0     Scan completed :
          Cell 01 - Address: <MAC addr ollehEgg_000>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=27/70  Signal level=-83 dBm  
                    Encryption key:on
                    ESSID:"ollehEgg_000"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 32ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC addr alvert>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=70/70  Signal level=-185 dBm  
                    Encryption key:on
                    ESSID:"alvert"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 32ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: <MAC addr iptime_Yooji>
                    Channel:7
                    Frequency:2.442 GHz (Channel 7)
                    Quality=70/70  Signal level=43 dBm  
                    Encryption key:on
                    ESSID:"iptime_Yooji"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 32ms ago
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 04 - Address: <MAC addr 301>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=70/70  Signal level=-161 dBm  
                    Encryption key:on
                    ESSID:"301"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 32ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 05 - Address: <MAC addr iptime>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=70/70  Signal level=58 dBm  
                    Encryption key:on
                    ESSID:"iptime"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 32ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 06 - Address: <MAC address>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=70/70  Signal level=44 dBm  
                    Encryption key:on
                    ESSID:"\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 29980ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK

##### module infos #####

[wl]
filename:       /lib/modules/3.13.0-34-generic/updates/dkms/wl.ko
license:        MIXED/Proprietary
srcversion:     FF25FE784DC6BDFF69DAFCB
depends:        cfg80211,lib80211
vermagic:       3.13.0-34-generic SMP mod_unload modversions 
parm:           wl_txq_thresh:int
parm:           oneonly:int
parm:           piomode:int
parm:           instance_base:int
parm:           nompc:int
parm:           intf_name:string

##### module parameters #####

##### /etc/modules #####

lp
rtc

##### blacklists #####

[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci

[/etc/modprobe.d/blacklist-bcm43.conf]
blacklist b43
blacklist b43legacy
blacklist ssb
blacklist bcm43xx
blacklist brcm80211
blacklist brcmfmac
blacklist brcmsmac
blacklist bcma

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

[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x10ec:0x8168 (r8169)
SUBSYSTEM=="net",  ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC addr eth0>",  ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# PCI device 0x14e4:0x4727 (brcmsmac)
SUBSYSTEM=="net",  ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC addr wlan0>",  ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

##### dmesg #####

[    8.707185] psmouse serio2: trackpoint: IBM TrackPoint firmware: 0x0e, buttons: 3/3
[   11.615097] wl: module license 'MIXED/Proprietary' taints kernel.
[   11.616277] wl: module verification failed: signature and/or  required key missing - tainting kernel
[   11.665560] INFO @wl_cfg80211_attach : Registered CFG80211 phy
[   11.797960] wlan0: Broadcom BCM4727 802.11 Hybrid Wireless Controller 6.30.223.141 (r415941)
[   44.551047] ERROR @wl_dev_intvar_get : error (-1)
[   44.551050] ERROR @wl_cfg80211_get_tx_power : error (-1)

########## wireless info END ############

```

---

### Post by chili555 on 2014-08-18
The prevailing wisdom is that the proprietary driver is not the optimum driver for your 14e4:4727 device. If it were me, I'd purge it and take a look at a few other things. 

First, check the settings in the router. WPA2-AES is preferred; not any WPA and WPA2 mixed mode and certainly not TKIP. Second, if your router is capable of N speeds, I have better luck with a channel width of 20 MHz in the 2.4 GHz band instead of automatic 20/40 MHz. I also have better luck with a fixed channel, either 1, 6 or 11, rather than automatic channel selection. After making these changes, reboot the router. Looking at your scan results, I suggest you try channel 11 or higher first.

Next, I recommend that your regulatory domain be set explicitly. Check yours:```
sudo iw reg get
```If you get 00, that is a one-size-maybe-fits-all setting. Find yours here: [http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2](http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2) Then set it temporarily:```
sudo iw reg set IS
```Of course, substitute your country code if not Iceland. Set it permanently:```
gksudo gedit /etc/default/crda
```Use nano or kate or leafpad if you don't have the text editor gedit.

Change the last line to read:```
REGDOMAIN=IS
```Proofread carefully, save and close the text editor.

Next, I'd set IPv6 to Ignore in Network Manager: [http://docs.fedoraproject.org/en-US/Fedora/18/html/Installation_Guide/images/netconfig/network-connections-ipv6-ignore.png](http://docs.fedoraproject.org/en-US/Fedora/18/html/Installation_Guide/images/netconfig/network-connections-ipv6-ignore.png)  This example is for ethernet, but you want wireless.

---

### Post by bclee on 2014-08-18
> **chili555 said:**
> 
Next, I recommend that your regulatory domain be set explicitly. Check yours:```
sudo iw reg get
```If you get 00, that is a one-size-maybe-fits-all setting. Find yours here: [http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2](http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2) Then set it temporarily:```
sudo iw reg set IS
```Of course, substitute your country code if not Iceland. Set it permanently:```
gksudo gedit /etc/default/crda
```Use nano or kate or leafpad if you don't have the text editor gedit.

Change the last line to read:```
REGDOMAIN=IS
```Proofread carefully, save and close the text editor.

Next, I'd set IPv6 to Ignore in Network Manager: [http://docs.fedoraproject.org/en-US/Fedora/18/html/Installation_Guide/images/netconfig/network-connections-ipv6-ignore.png](http://docs.fedoraproject.org/en-US/Fedora/18/html/Installation_Guide/images/netconfig/network-connections-ipv6-ignore.png)  This example is for ethernet, but you want wireless.

To be frankly, I didn`t think that can be a solution. Who cares about country code for wireless adaptor? 2.4Ghz channels from 1 to (at least) 11 is universal, and my AP set for channel 1, I never thought It can be a solution.
But, after removing the proprietary driver and set up the open source driver with country code, It works flawlessly. Although the connection speed is a little bit low, (it tells 72Mb/s, while my previous laptop with Qualcomm Atheros AR9565 (1tx1rx) gives 150Mb/s.
I`ll test it for Arch linux, and take my laptop for testing. (I thin the most challenging AP is in the school, which uses WPA-PEAP with MSCHAPv2) Thank you!

---

### Post by chili555 on 2014-08-18
Yeah, who cares. Until it works!!

---

### Post by bclee on 2014-08-18
Sadly speaking, my wifi adaptor won`t work after turning off my laptop. It does not connect to my AP. (It seems it does not even detected.)

I`ve changed my AP to be unencrypted, and changed channnel 1, 6, 11, but none of them working.
```


########## wireless info START ##########

Report from: 19 Aug 2014 11:30 KST +0900

Script from: 16 Aug 2014 22:12 UTC +0000

##### release #####

Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.1 LTS
Release:    14.04
Codename:    trusty

##### kernel #####

Linux 3.13.0-34-generic #60-Ubuntu SMP Wed Aug 13 15:45:27 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop #####

Ubuntu

##### lspci #####

03:00.0 Network controller [0280]: Broadcom Corporation BCM4313 802.11bgn Wireless Network Adapter [14e4:4727] (rev 01)
    Subsystem: Broadcom Corporation Device [14e4:0608]
    Kernel driver in use: bcma-pci-bridge

04:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 07)
    Subsystem: Lenovo Device [17aa:21fc]
    Kernel driver in use: r8169

##### lsusb #####

Bus 002 Device 003: ID 5986:02d2 Acer, Inc 
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 147e:1002 Upek Biometric Touchchip/Touchstrip Fingerprint Sensor
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 002: ID 045e:0745 Microsoft Corp. Nano Transceiver v1.0 for Bluetooth
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info #####

##### rfkill #####

0: tpacpi_bluetooth_sw: Bluetooth
    Soft blocked: yes
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

##### lsmod #####

wmi                    19177  0 
brcmsmac              563041  0 
cordic                 12574  1 brcmsmac
brcmutil               15618  1 brcmsmac
bcma                   52096  2 brcmsmac
mac80211              630653  1 brcmsmac
cfg80211              484040  2 brcmsmac,mac80211

##### interfaces #####

auto lo
iface lo inet loopback

##### ifconfig #####

eth0      Link encap:Ethernet  HWaddr <MAC addr eth0>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wlan0     Link encap:Ethernet  HWaddr <MAC addr wlan0>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

##### iwconfig #####

eth0      no wireless extensions.

lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=19 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          

##### route #####

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface

##### resolv.conf #####

##### nm-tool #####

NetworkManager Tool

State: connecting

- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             unavailable
  Default:           no
  HW Address:        <MAC addr eth0>

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off

- Device: wlan0  [301] ---------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            brcmsmac
  State:             connecting (configuring)
  Default:           no
  HW Address:        <MAC addr wlan0>

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 
    301:             Infra, <MAC addr 301>, Freq 2462 MHz, Rate 54 Mb/s, Strength 100 WPA2
    iptime:          Infra, <MAC addr iptime>, Freq 2462 MHz, Rate 54 Mb/s, Strength 67 WPA2

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

##### iw reg get #####

country KR:
    (2402 - 2482 @ 20), (N/A, 20)
    (5170 - 5250 @ 20), (3, 20)
    (5250 - 5330 @ 20), (3, 20), DFS
    (5490 - 5630 @ 20), (3, 30), DFS
    (5735 - 5815 @ 20), (3, 30)

##### iwlist channels #####

eth0      no frequency information.

lo        no frequency information.

wlan0     13 channels in total; available frequencies :
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

##### iwlist scan #####

eth0      Interface doesn't support scanning.

lo        Interface doesn't support scanning.

Channel occupancy:
     1   WLAPs on   Frequency:2.462 GHz (Channel 11)

wlan0     Scan completed :
          Cell 01 - Address: <MAC addr iptime>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=50/70  Signal level=-60 dBm  
                    Encryption key:on
                    ESSID:"iptime"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000014f9d4917e
                    Extra: Last beacon: 4156ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK

##### module infos #####

[brcmsmac]
filename:       /lib/modules/3.13.0-34-generic/kernel/drivers/net/wireless/brcm80211/brcmsmac/brcmsmac.ko
firmware:       brcm/bcm43xx_hdr-0.fw
firmware:       brcm/bcm43xx-0.fw
license:        Dual BSD/GPL
description:    Broadcom 802.11n wireless LAN driver.
author:         Broadcom Corporation
srcversion:     43D6897F7EB716081DF69BE
depends:        bcma,mac80211,brcmutil,cfg80211,cordic
intree:         Y
vermagic:       3.13.0-34-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        50:0B:C5:C8:7D:4B:11:5C:F3:C1:50:4F:7A:92:E2:33:C6:14:3D:58
sig_hashalgo:   sha512

[brcmutil]
filename:       /lib/modules/3.13.0-34-generic/kernel/drivers/net/wireless/brcm80211/brcmutil/brcmutil.ko
license:        Dual BSD/GPL
description:    Broadcom 802.11n wireless LAN driver utilities.
author:         Broadcom Corporation
srcversion:     E81EE4CBB6A7A689150D93D
depends:        
intree:         Y
vermagic:       3.13.0-34-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        50:0B:C5:C8:7D:4B:11:5C:F3:C1:50:4F:7A:92:E2:33:C6:14:3D:58
sig_hashalgo:   sha512

[bcma]
filename:       /lib/modules/3.13.0-34-generic/kernel/drivers/bcma/bcma.ko
license:        GPL
description:    Broadcom's specific AMBA driver
srcversion:     E41B811D88783DD5BC38565
depends:        
intree:         Y
vermagic:       3.13.0-34-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        50:0B:C5:C8:7D:4B:11:5C:F3:C1:50:4F:7A:92:E2:33:C6:14:3D:58
sig_hashalgo:   sha512

##### module parameters #####

##### /etc/modules #####

lp
rtc
brcmsmac

##### blacklists #####

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
blacklist b43
blacklist wl

##### udev rules #####

[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x10ec:0x8168 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC addr eth0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# PCI device 0x14e4:0x4727 (brcmsmac)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC addr wlan0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

##### dmesg #####

[   10.690515] psmouse serio2: trackpoint: IBM TrackPoint firmware: 0x0e, buttons: 3/3
[   13.266807] bcma: bus0: Found chip with id 0x4313, rev 0x01 and package 0x08
[   13.266842] bcma: bus0: Core 0 found: ChipCommon (manuf 0x4BF, id 0x800, rev 0x24, class 0x0)
[   13.266870] bcma: bus0: Core 1 found: IEEE 802.11 (manuf 0x4BF, id 0x812, rev 0x18, class 0x0)
[   13.266925] bcma: bus0: Core 2 found: PCIe (manuf 0x4BF, id 0x820, rev 0x11, class 0x0)
[   13.279562] bcma: bus0: Bus registered
[   13.415281] brcmsmac bcma0:0: mfg 4bf core 812 rev 24 class 0 irq 17
[   13.437633] ieee80211 phy0: registered radio enabled led device: brcmsmac-phy0:radio gpio: 243
[   17.391354] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: false (implement)
[   17.391389] brcmsmac bcma0:0: brcms_ops_config: change power-save mode: false (implement)
[   17.392027] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready (repeated 2 times)
[   19.275421] wlan0: authenticate with <MAC addr 301>
[   19.279578] wlan0: direct probe to <MAC addr 301> (try 1/3)
[   19.479787] wlan0: direct probe to <MAC addr 301> (try 2/3)
[   19.683782] wlan0: direct probe to <MAC addr 301> (try 3/3)
[   19.887855] wlan0: authentication with <MAC addr 301> timed out
[   20.828654] wlan0: authenticate with <MAC addr 301>
[   20.832515] wlan0: direct probe to <MAC addr 301> (try 1/3)
[   21.036218] wlan0: direct probe to <MAC addr 301> (try 2/3)
[   21.240271] wlan0: direct probe to <MAC addr 301> (try 3/3)
[   21.444323] wlan0: authentication with <MAC addr 301> timed out
[   22.789156] wlan0: authenticate with <MAC addr 301>
[   22.792333] wlan0: direct probe to <MAC addr 301> (try 1/3)
[   22.992744] wlan0: send auth to <MAC addr 301> (try 2/3)
[   23.013604] wlan0: send auth to <MAC addr 301> (try 3/3)
[   23.094571] wlan0: authentication with <MAC addr 301> timed out

########## wireless info END ############

```

---

