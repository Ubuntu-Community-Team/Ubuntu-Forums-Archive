---
title: "Realtek Semiconductor RTL8187SE Wireless LAN Controller really slow wifi speed"
date: 2014-07-01
forum: Networking &amp; Wireless
---

### Post by Dean_Godwin on 2014-07-01
Hi, i'm new to ubutu, loving it so far except for the really slow download speed, I get 20mbs on Windows 7, but when I boot into ubuntu this is the result I get.....



[IMG]http://www.speedtest.net/result/3598353915.png[/IMG]

Here is the result of the Wireless Script
```


########## wireless info START ##########

##### release #####

Distributor ID:    Ubuntu
Description:    Ubuntu 14.04 LTS
Release:    14.04
Codename:    trusty

##### kernel #####

Linux dean-I41IL 3.13.0-24-generic #46-Ubuntu SMP Thu Apr 10 19:08:14 UTC 2014 i686 i686 i686 GNU/Linux

##### lspci #####

04:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8187SE Wireless LAN Controller [10ec:8199] (rev 22)
    Subsystem: Micro-Star International Co., Ltd. [MSI] MN54G2 / MS-6894 Wireless Mini PCIe Card [1462:6894]
    Kernel driver in use: r8180
05:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 03)
    Subsystem: Elitegroup Computer Systems Device [1019:90b5]
    Kernel driver in use: r8169

##### lsusb #####

Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 002: ID 0000:0538  
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

##### PCMCIA Card Info #####

##### rfkill #####

##### lsmod #####

r8187se               155125  0 
eeprom_93cx6           13168  1 r8187se

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

wlan0     802.11b/g  link  ESSID:"EE-BrightBox-ch5c6y"  
          Mode:Managed  Frequency=2.437 GHz  Access Point: <MAC address removed>   
          Bit Rate=48 Mb/s   
          Retry min limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=79/100  Signal level=-40 dBm  Noise level=-106 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

##### route #####

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 wlan0
192.168.1.0     0.0.0.0         255.255.255.0   U     9      0        0 wlan0

##### resolv.conf #####

nameserver 127.0.1.1
search default

##### nm-tool #####

NetworkManager Tool

State: connected (global)

- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             unavailable
  Default:           no
  HW Address:        <MAC address removed>

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off

- Device: wlan0  [EE-BrightBox-ch5c6y] -----------------------------------------
  Type:              802.11 WiFi
  Driver:            r8180
  State:             connected
  Default:           yes
  HW Address:        <MAC address removed>

  Capabilities:
    Speed:           48 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    *EE-BrightBox-ch5c6y: Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 78 WPA WPA2

  IPv4 Settings:
    Address:         192.168.1.168
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
                    ESSID:"EE-BrightBox-ch5c6y"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:6
                    Encryption key:on
                    Bit Rates:54 Mb/s
                    Extra: Rates (Mb/s): 1 2 5.5 6 9 11 12 18 24 36 48 54 
                    Quality=79/100  Signal level=-40 dBm  Noise level=-106 dBm
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    Extra: Last beacon: 87ms ago

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
          Current Channel=6

##### modinfo #####

filename:       /lib/modules/3.13.0-24-generic/kernel/drivers/staging/rtl8187se/r8187se.ko
description:    Linux driver for Realtek RTL8187SE WiFi cards
author:         Andrea Merello <andrea.merello@gmail.com>
license:        GPL
license:        GPL
author:         Copyright (C) 2004 Intel Corporation <jketreno@linux.intel.com>
description:    802.11 data/management/control stack
license:        GPL
description:    HostAP crypto
author:         Jouni Malinen
license:        GPL
description:    Host AP crypt: TKIP
author:         Jouni Malinen
license:        GPL
description:    Host AP crypt: CCMP
author:         Jouni Malinen
license:        GPL
description:    Host AP crypt: WEP
author:         Jouni Malinen
srcversion:     7BE01256633B67BF1ADB4FF
alias:          pci:v000010ECd00008199sv*sd*bc*sc*i*
depends:        eeprom_93cx6
staging:        Y
intree:         Y
vermagic:       3.13.0-24-generic SMP mod_unload modversions 686 
signer:         Magrathea: Glacier signing key
sig_key:        <MAC address removed>:96:DC:92:B0:1D:75:9D:3E:85:62:EA:32:A1:C7
sig_hashalgo:   sha512
parm:           ifname:string
parm:           hwwep: Try to use hardware WEP support. Still broken and not available on all cards (int)

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

##### udev rules #####

# PCI device 0x10ec:0x8168 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

# PCI device 0x10ec:0x8199 (r8180)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

##### dmesg #####

[    8.619458] r8187se: module is from the staging directory, the quality is unknown, you have been warned.
[    8.659568] r8187se: 
[    8.659572] r8187se: Copyright (c) 2004-2005, Andrea Merello
[    8.659574] r8180: Initializing module
[    8.659575] r8180: Wireless extensions version 22
[    8.659576] r8180: Initializing proc filesystem
[    8.659606] r8180: Configuring chip resources
[    8.669821] r8180: Channel plan is 2
[    8.669828] r8180: MAC controller is a RTL8187SE b/g
[    8.671983] r8180: usValue is 0x0
[    8.710737] r8180: WW:**PLEASE** REPORT SUCCESSFUL/UNSUCCESSFUL TO Realtek!
[    8.713890] r8180: IRQ 17
[    8.720286] r8180: Driver probe completed
[   16.249933] r8180: Bringing up iface
[   16.448419] r8180: Card successfully reset
[   17.186367] r8180: WIRELESS_MODE_G
[   17.202662] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   17.202967] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   39.988355] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  192.388151] r8180: WW:Error: no descriptor left by previous TX (avail 4) 
[  201.837093] r8180: WW:Error: no descriptor left by previous TX (avail 4) 
[  201.837202] r8180: WW:Error: no descriptor left by previous TX (avail 3) 

########## wireless info END ############

```
I really hope someone can help me, I would love to continue using Ubuntu but WiFi is a necessity for me.

Thanks in advance....... Hopefully ;)

---

### Post by Dean_Godwin on 2014-07-02
Also, the wired connection doesn't work :( dunno what to do I am lost.

---

