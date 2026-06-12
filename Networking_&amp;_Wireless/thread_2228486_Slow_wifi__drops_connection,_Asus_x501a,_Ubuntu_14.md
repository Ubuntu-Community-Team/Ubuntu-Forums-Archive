---
title: "Slow wifi / drops connection, Asus x501a, Ubuntu 14.04 LTS, Ralink RT5390 Wireless"
date: 2014-06-07
forum: Networking &amp; Wireless
---

### Post by matthew43 on 2014-06-07
Hi everyone. 

I recently installed Ubuntu 14.04 LTS on my Asus X501A, having had enough of Windows 8 for one life. Until now I haven't had the opportunity to deal with the network issues I've encountered, and have simply used an Ethernet cable. I'm very new to Linux, but can use the terminal and understand basic concepts. 

As is, I got .10m/s: [https://www.dropbox.com/s/e2oaf0z0ol9o15x/Selection_006.png](https://www.dropbox.com/s/e2oaf0z0ol9o15x/Selection_006.png) -- whereas I got up to 15 on win 8. I'm assuming this has to do with my wireless card.

I tried searching "Edit > Software Sources > Additional Drivers" but got "No additional drivers available," unfortunately.

Greatly appreciate all help/advice on this one; I am hoping to stick with this until I figure it out.  

```
########## wireless info START ##########

##### release #####


Distributor ID:    Ubuntu
Description:    Ubuntu 14.04 LTS
Release:    14.04
Codename:    trusty


##### kernel #####


Linux matt-X501A 3.13.0-29-generic #53-Ubuntu SMP Wed Jun 4 21:00:20 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux


##### lspci #####


02:00.0 Network controller [0280]: Ralink corp. RT5390 Wireless 802.11n 1T/1R PCIe [1814:5390]
    Subsystem: Foxconn International, Inc. Device [105b:e054]
    Kernel driver in use: rt2800pci


03:00.2 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 0a)
    Subsystem: ASUSTeK Computer Inc. Device [1043:14f7]
    Kernel driver in use: r8169


##### lsusb #####


Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 0bda:5705 Realtek Semiconductor Corp. 
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 002: ID 03f0:8707 Hewlett-Packard 
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


##### PCMCIA Card Info #####


##### rfkill #####


1: phy0: Wireless LAN
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


wlan0     IEEE 802.11bgn  ESSID:"NETGEAR"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: <MAC address removed>   
          Bit Rate=36 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=70/70  Signal level=-31 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:84  Invalid misc:2298   Missed beacon:0


##### route #####


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 eth0
192.168.1.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0
192.168.1.0     0.0.0.0         255.255.255.0   U     9      0        0 wlan0


##### resolv.conf #####


nameserver 127.0.1.1


##### nm-tool #####


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
    Address:         192.168.1.6
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1


    DNS:             192.168.1.1


- Device: wlan0  [NETGEAR] -----------------------------------------------------
  Type:              802.11 WiFi
  Driver:            rt2800pci
  State:             connected
  Default:           no
  HW Address:        <MAC address removed>


  Capabilities:
    Speed:           36 Mb/s


  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes


  Wireless Access Points (* = current AP)
    *NETGEAR:        Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 89
    netgear:         Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 15 WPA WPA2


  IPv4 Settings:
    Address:         192.168.1.11
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
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=70/70  Signal level=-37 dBm  
                    Encryption key:off
                    ESSID:"NETGEAR"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000a88ff4912
                    Extra: Last beacon: 176ms ago
                    IE: Unknown: 00074E455447454152
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030101
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD090010180204F0000000
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
          Current Frequency:2.412 GHz (Channel 1)


##### lsmod #####


rt2800pci              13606  0 
rt2800mmio             20986  1 rt2800pci
rt2800lib              89076  2 rt2800pci,rt2800mmio
rt2x00pci              13287  1 rt2800pci
rt2x00mmio             13603  2 rt2800pci,rt2800mmio
rt2x00lib              55307  5 rt2x00pci,rt2800lib,rt2800pci,rt2800mmio,rt2x00mmio
mac80211              626557  3 rt2x00lib,rt2x00pci,rt2800lib
cfg80211              484040  2 mac80211,rt2x00lib
eeprom_93cx6           13344  1 rt2800pci
crc_ccitt              12707  1 rt2800lib


##### modinfo #####


filename:       /lib/modules/3.13.0-29-generic/kernel/drivers/net/wireless/rt2x00/rt2800pci.ko
license:        GPL
firmware:       rt2860.bin
description:    Ralink RT2800 PCI & PCMCIA Wireless LAN driver.
version:        2.3.0
author:         [http://rt2x00.serialmonkey.com](http://rt2x00.serialmonkey.com)
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
vermagic:       3.13.0-29-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        <MAC address removed>:3B:EA:01:C4:BD:A9:65:67:CF:A7:23:C9:70:D8
sig_hashalgo:   sha512
parm:           nohwcrypt:Disable hardware encryption. (bool)


filename:       /lib/modules/3.13.0-29-generic/kernel/drivers/net/wireless/rt2x00/rt2800mmio.ko
license:        GPL
description:    rt2800 MMIO library
version:        2.3.0
author:         [http://rt2x00.serialmonkey.com](http://rt2x00.serialmonkey.com)
srcversion:     F196893F5F72140CA847345
depends:        rt2800lib,rt2x00lib,rt2x00mmio
intree:         Y
vermagic:       3.13.0-29-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        <MAC address removed>:3B:EA:01:C4:BD:A9:65:67:CF:A7:23:C9:70:D8
sig_hashalgo:   sha512


filename:       /lib/modules/3.13.0-29-generic/kernel/drivers/net/wireless/rt2x00/rt2800lib.ko
license:        GPL
description:    Ralink RT2800 library
version:        2.3.0
author:         [http://rt2x00.serialmonkey.com](http://rt2x00.serialmonkey.com), Bartlomiej Zolnierkiewicz
srcversion:     9BD0087B6943A41E7FD8EDA
depends:        rt2x00lib,mac80211,crc-ccitt
intree:         Y
vermagic:       3.13.0-29-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        <MAC address removed>:3B:EA:01:C4:BD:A9:65:67:CF:A7:23:C9:70:D8
sig_hashalgo:   sha512


filename:       /lib/modules/3.13.0-29-generic/kernel/drivers/net/wireless/rt2x00/rt2x00pci.ko
license:        GPL
description:    rt2x00 pci library
version:        2.3.0
author:         [http://rt2x00.serialmonkey.com](http://rt2x00.serialmonkey.com)
srcversion:     9B9D0D0D0F8571AF43705FD
depends:        rt2x00lib,mac80211
intree:         Y
vermagic:       3.13.0-29-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        <MAC address removed>:3B:EA:01:C4:BD:A9:65:67:CF:A7:23:C9:70:D8
sig_hashalgo:   sha512


filename:       /lib/modules/3.13.0-29-generic/kernel/drivers/net/wireless/rt2x00/rt2x00mmio.ko
license:        GPL
description:    rt2x00 mmio library
version:        2.3.0
author:         [http://rt2x00.serialmonkey.com](http://rt2x00.serialmonkey.com)
srcversion:     07530604F5CE4EF69872C75
depends:        rt2x00lib
intree:         Y
vermagic:       3.13.0-29-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        <MAC address removed>:3B:EA:01:C4:BD:A9:65:67:CF:A7:23:C9:70:D8
sig_hashalgo:   sha512


filename:       /lib/modules/3.13.0-29-generic/kernel/drivers/net/wireless/rt2x00/rt2x00lib.ko
license:        GPL
description:    rt2x00 library
version:        2.3.0
author:         [http://rt2x00.serialmonkey.com](http://rt2x00.serialmonkey.com)
srcversion:     C57F87A3569F5363E79FD42
depends:        mac80211,cfg80211
intree:         Y
vermagic:       3.13.0-29-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        <MAC address removed>:3B:EA:01:C4:BD:A9:65:67:CF:A7:23:C9:70:D8
sig_hashalgo:   sha512


##### modules #####


lp
rtc


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


##### udev rules #####


# PCI device 0x10ec:0x8168 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"


# PCI device 0x1814:0x5390 (rt2800pci)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"


##### dmesg #####


[    1.785966] psmouse serio4: elantech: assuming hardware version 4 (with firmware version 0x361f03)
[   11.017085] ieee80211 phy0: rt2x00_set_rt: Info - RT chipset 5390, rev 1502 detected
[   11.020647] ieee80211 phy0: rt2x00_set_rf: Info - RF chipset 5390 detected
[   21.213329] ieee80211 phy0: rt2x00lib_request_firmware: Info - Loading firmware file 'rt2860.bin'
[   21.261817] ieee80211 phy0: rt2x00lib_request_firmware: Info - Firmware detected - version: 0.34
[   21.380495] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   21.380886] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   46.140174] wlan0: authenticate with <MAC address removed>
[   46.142286] wlan0: send auth to <MAC address removed> (try 1/3)
[   46.492024] wlan0: authenticated
[   46.494367] wlan0: associate with <MAC address removed> (try 1/3)
[   47.356400] wlan0: RX AssocResp from <MAC address removed> (capab=0x401 status=0 aid=3)
[   47.356583] wlan0: associated
[   47.356608] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   66.050437] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[  409.622570] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[  409.782774] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[  424.667316] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[  446.671413] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[  446.831615] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[  532.790948] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[  532.951114] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[  591.858395] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[  592.018581] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[  597.901309] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[  598.061493] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[  611.905318] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[  612.065489] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[  648.935632] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[  661.950483] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[  662.110654] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[  716.004247] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[  737.028242] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[  809.146710] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[  809.306885] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[  828.140409] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[  856.164386] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[  946.279380] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[ 1010.340563] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[ 1079.427490] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[ 1079.587673] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[ 1092.442312] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[ 1092.602499] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[ 1177.539528] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[ 1177.699694] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[ 1205.559508] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[ 1205.719702] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[ 1255.620737] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[ 1298.669924] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[ 1298.830143] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[ 1586.841324] wlan0: deauthenticated from <MAC address removed> (Reason: 7)
[ 1587.041546] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[ 1602.278348] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1681.610171] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1703.583263] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1704.677318] wlan0: authenticate with <MAC address removed>
[ 1704.677706] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 1704.880185] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 1705.084415] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 1705.288684] wlan0: authentication with <MAC address removed> timed out
[ 1705.452872] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[ 1705.713171] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[ 1705.873351] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[ 1706.927134] wlan0: authenticate with <MAC address removed>
[ 1706.935485] wlan0: send auth to <MAC address removed> (try 1/3)
[ 1707.867632] wlan0: send auth to <MAC address removed> (try 2/3)
[ 1707.905949] wlan0: authenticated
[ 1707.907654] wlan0: associate with <MAC address removed> (try 1/3)
[ 1708.880790] wlan0: associate with <MAC address removed> (try 2/3)
[ 1709.133929] wlan0: RX AssocResp from <MAC address removed> (capab=0x401 status=0 aid=3)
[ 1709.134115] wlan0: associated
[ 1709.134142] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 1709.544002] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 1710.621146] wlan0: authenticate with <MAC address removed>
[ 1710.627751] wlan0: send auth to <MAC address removed> (try 1/3)
[ 1711.872214] wlan0: send auth to <MAC address removed> (try 2/3)
[ 1711.932359] wlan0: authenticated
[ 1711.936256] wlan0: associate with <MAC address removed> (try 1/3)
[ 1711.948571] wlan0: RX AssocResp from <MAC address removed> (capab=0x401 status=0 aid=3)
[ 1711.948864] wlan0: associated
[ 1711.949794] wlan0: deauthenticating from <MAC address removed> by local choice (reason=2)
[ 1711.981032] wlan0: authenticate with <MAC address removed>
[ 1711.981353] wlan0: send auth to <MAC address removed> (try 1/3)
[ 1712.240604] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[ 1712.400784] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[ 1713.462361] wlan0: authenticated
[ 1713.466005] wlan0: associate with <MAC address removed> (try 1/3)
[ 1714.866630] wlan0: RX AssocResp from <MAC address removed> (capab=0x401 status=0 aid=3)
[ 1714.867074] wlan0: associated
[ 1724.879121] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 1726.113009] wlan0: authenticate with <MAC address removed>
[ 1726.121140] wlan0: send auth to <MAC address removed> (try 1/3)
[ 1726.749914] wlan0: authenticated
[ 1726.753185] wlan0: associate with <MAC address removed> (try 1/3)
[ 1727.902501] wlan0: associate with <MAC address removed> (try 2/3)
[ 1728.891635] wlan0: associate with <MAC address removed> (try 3/3)
[ 1729.916776] wlan0: association with <MAC address removed> timed out
[ 1730.092985] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[ 1735.258886] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[ 1735.419061] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[ 1745.247105] wlan0: authenticate with <MAC address removed>
[ 1745.255174] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 1745.458554] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 1745.662784] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 1745.867038] wlan0: authentication with <MAC address removed> timed out
[ 1746.039205] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[ 1757.108533] wlan0: authenticate with <MAC address removed>
[ 1757.116699] wlan0: send auth to <MAC address removed> (try 1/3)
[ 1757.924848] wlan0: send auth to <MAC address removed> (try 2/3)
[ 1757.995969] wlan0: authenticated
[ 1757.996884] wlan0: associate with <MAC address removed> (try 1/3)
[ 1758.873871] wlan0: associate with <MAC address removed> (try 2/3)
[ 1759.110241] wlan0: RX AssocResp from <MAC address removed> (capab=0x401 status=0 aid=3)
[ 1759.110569] wlan0: associated
[ 1861.257239] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[ 1862.246843] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[ 2159.061327] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[ 2159.557836] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[ 2159.718034] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[ 2160.583064] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[ 2161.079634] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[ 2161.239817] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[ 2161.784395] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[ 2162.268991] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[ 2162.429177] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[ 2162.913726] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[ 2163.073912] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush


########## wireless info END ############
```

---

### Post by matthew43 on 2014-06-11
Am I out of luck? Let me know if I can provide any other information.

---

### Post by elringo70 on 2014-09-18
did you get a solution?? I got the exact same problem with a ASUS x55a...

---

### Post by kd512d7 on 2015-07-24
Same here, ASUS X200M

---

### Post by janus44 on 2015-08-25
Hello I am having the same problem with my Asus X401U .I am using Ubuntu 15.04 .I have found some workarounds but I am complete newbie with linux and I am afraid to try.
Here are my fidings...
[http://www.techytalk.info/ubuntu/ralink-wireless/](http://www.techytalk.info/ubuntu/ralink-wireless/)
[https://launchpad.net/~marko-techytalk.info/+archive/ubuntu/ralink-wireless?field.series_filter=oneiric](https://launchpad.net/~marko-techytalk.info/+archive/ubuntu/ralink-wireless?field.series_filter=oneiric)
Seems prety easy to folow but I am not quite sure if this works at all or it is meant for older distributions.
If you have any idea please help ...

---

### Post by janus44 on 2015-08-25
Does this will update ralink rt5390 issues ? I am complete noob ...

---

