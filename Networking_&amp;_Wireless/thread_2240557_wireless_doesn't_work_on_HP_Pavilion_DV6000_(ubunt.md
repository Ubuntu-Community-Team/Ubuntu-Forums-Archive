---
title: "wireless doesn't work on HP Pavilion DV6000 (ubuntu 12.04)"
date: 2014-08-20
forum: Networking &amp; Wireless
---

### Post by Enrique_Medina on 2014-08-20
```
########## wireless info START ##########

Report from: 20 Aug 2014 18:42 ART -0300

Script from: 17 Aug 2014 02:46 UTC +0000

##### release #####

Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.1 LTS
Release:    14.04
Codename:    trusty

##### kernel #####

Linux 3.13.0-34-generic #60-Ubuntu SMP Wed Aug 13 15:49:09 UTC 2014 i686 athlon i686 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop #####

Ubuntu

##### lspci #####

06:02.0 Network controller [0280]: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller [14e4:4318] (rev 02)
    Subsystem: Hewlett-Packard Company Broadcom 802.11b/g WLAN [103c:1355]
    Kernel driver in use: b43-pci-bridge

06:06.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL-8100/8101L/8139 PCI Fast Ethernet Adapter [10ec:8139] (rev 10)
    Subsystem: Hewlett-Packard Company Device [103c:30a4]
    Kernel driver in use: 8139too

##### lsusb #####

Bus 001 Device 002: ID 0781:5577 SanDisk Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

##### PCMCIA card info #####

PRODID_1=""
PRODID_2=""
PRODID_3=""
PRODID_4=""
MANFID=0000,0000
FUNCID=255

##### rfkill #####

##### lsmod #####

b43                   356470  0 
bcma                   42043  1 b43
mac80211              546051  1 b43
cfg80211              409394  2 b43,mac80211
wmi                    18673  0 
ssb                    51854  1 b43

##### interfaces #####

auto lo
iface lo inet loopback

##### ifconfig #####

eth0      Link encap:Ethernet  HWaddr <MAC addr eth0>  
          inet addr:192.168.0.106  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::216:d4ff:fe37:69d4/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:11066 errors:0 dropped:0 overruns:0 frame:0
          TX packets:9738 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:8350103 (8.3 MB)  TX bytes:1064829 (1.0 MB)

##### iwconfig #####

lo        no wireless extensions.

eth0      no wireless extensions.

##### route #####

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.0.1     0.0.0.0         UG    0      0        0 eth0
192.168.0.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0

##### resolv.conf #####

nameserver 127.0.1.1

##### nm-tool #####

NetworkManager Tool

State: connected (global)

- Device: eth0  [Conexión cableada 1] -----------------------------------------
  Type:              Wired
  Driver:            8139too
  State:             connected
  Default:           yes
  HW Address:        <MAC addr eth0>

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.0.106
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.0.1

    DNS:             192.168.0.1

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

lo        no frequency information.

eth0      no frequency information.

##### iwlist scan #####

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

##### module infos #####

[b43]
filename:       /lib/modules/3.13.0-34-generic/kernel/drivers/net/wireless/b43/b43.ko
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
srcversion:     42BAE2DB9BADE3E7ECA2CC0
depends:        bcma,ssb,mac80211,cfg80211
intree:         Y
vermagic:       3.13.0-34-generic SMP mod_unload modversions 686 
signer:         Magrathea: Glacier signing key
sig_key:        1B:7C:0F:16:16:8C:4B:25:C3:A0:5A:6A:43:09:1C:85:06:E3:73:DF
sig_hashalgo:   sha512
parm:           bad_frames_preempt:enable(1) / disable(0) Bad Frames Preemption (int)
parm:           fwpostfix:Postfix for the .fw files to load. (string)
parm:           hwpctl:Enable hardware-side power control (default off) (int)
parm:           nohwcrypt:Disable hardware encryption. (int)
parm:           hwtkip:Enable hardware tkip. (int)
parm:           qos:Enable QOS support (default on) (int)
parm:           btcoex:Enable Bluetooth coexistence (default on) (int)
parm:           verbose:Log message verbosity: 0=error, 1=warn, 2=info(default), 3=debug (int)
parm:           pio:Use PIO accesses by default: 0=DMA, 1=PIO (int)
parm:           allhwsupport:Enable support for all hardware (even it if overlaps with the brcmsmac driver) (int)

[bcma]
filename:       /lib/modules/3.13.0-34-generic/kernel/drivers/bcma/bcma.ko
license:        GPL
description:    Broadcom's specific AMBA driver
srcversion:     E41B811D88783DD5BC38565
depends:        
intree:         Y
vermagic:       3.13.0-34-generic SMP mod_unload modversions 686 
signer:         Magrathea: Glacier signing key
sig_key:        1B:7C:0F:16:16:8C:4B:25:C3:A0:5A:6A:43:09:1C:85:06:E3:73:DF
sig_hashalgo:   sha512

[ssb]
filename:       /lib/modules/3.13.0-34-generic/kernel/drivers/ssb/ssb.ko
license:        GPL
description:    Sonics Silicon Backplane driver
srcversion:     3DE188310F77C566C2E8CB3
depends:        
intree:         Y
vermagic:       3.13.0-34-generic SMP mod_unload modversions 686 
signer:         Magrathea: Glacier signing key
sig_key:        1B:7C:0F:16:16:8C:4B:25:C3:A0:5A:6A:43:09:1C:85:06:E3:73:DF
sig_hashalgo:   sha512

##### module parameters #####

[b43]
allhwsupport: 0
bad_frames_preempt: 0
btcoex: 1
hwpctl: 0
hwtkip: 0
nohwcrypt: 0
pio: 0
qos: 1
verbose: 2

##### /etc/modules #####

lp

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

##### udev rules #####

[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x10ec:0x8139 (8139too)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC addr eth0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

##### dmesg #####

[    1.637963] ssb: Found chip with id 0x4318, rev 0x02 and package 0x02
[    1.637981] ssb: Core 0 found: ChipCommon (cc 0x800, rev 0x0D, vendor 0x4243)
[    1.637990] ssb: Core 1 found: IEEE 802.11 (cc 0x812, rev 0x09, vendor 0x4243)
[    1.637999] ssb: Core 2 found: PCI (cc 0x804, rev 0x0C, vendor 0x4243)
[    1.638008] ssb: Core 3 found: PCMCIA (cc 0x80D, rev 0x07, vendor 0x4243)
[    1.681161] ssb: Sonics Silicon Backplane found on PCI device 0000:06:02.0
[   14.003896] b43-phy0: Broadcom 4318 WLAN found (core revision 9)
[   14.052037] b43-phy0: Found PHY: Analog 3, Type 2 (G), Revision 7
[   14.605079] b43 ssb0:0: Direct firmware load failed with error -2
[   14.605087] b43 ssb0:0: Falling back to user helper
[   14.606117] b43 ssb0:0: Direct firmware load failed with error -2
[   14.606121] b43 ssb0:0: Falling back to user helper
[   14.609523] b43 ssb0:0: Direct firmware load failed with error -2
[   14.609528] b43 ssb0:0: Falling back to user helper
[   14.610199] b43 ssb0:0: Direct firmware load failed with error -2
[   14.610203] b43 ssb0:0: Falling back to user helper
[   14.613339] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found
[   14.613348] b43-phy0 ERROR: Firmware file "b43-open/ucode5.fw" not found
[   14.613353] b43-phy0 ERROR: You must go to http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware and download the correct firmware for this driver version. Please carefully read all instructions on this website.

########## wireless info END ############


```

```
########## wireless info START ##########

Report from: 20 Aug 2014 18:42 ART -0300

Script from: 17 Aug 2014 02:46 UTC +0000

##### release #####

Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.1 LTS
Release:    14.04
Codename:    trusty

##### kernel #####

Linux 3.13.0-34-generic #60-Ubuntu SMP Wed Aug 13 15:49:09 UTC 2014 i686 athlon i686 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop #####

Ubuntu

##### lspci #####

06:02.0 Network controller [0280]: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller [14e4:4318] (rev 02)
    Subsystem: Hewlett-Packard Company Broadcom 802.11b/g WLAN [103c:1355]
    Kernel driver in use: b43-pci-bridge

06:06.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL-8100/8101L/8139 PCI Fast Ethernet Adapter [10ec:8139] (rev 10)
    Subsystem: Hewlett-Packard Company Device [103c:30a4]
    Kernel driver in use: 8139too

##### lsusb #####

Bus 001 Device 002: ID 0781:5577 SanDisk Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

##### PCMCIA card info #####

PRODID_1=""
PRODID_2=""
PRODID_3=""
PRODID_4=""
MANFID=0000,0000
FUNCID=255

##### rfkill #####

##### lsmod #####

b43                   356470  0 
bcma                   42043  1 b43
mac80211              546051  1 b43
cfg80211              409394  2 b43,mac80211
wmi                    18673  0 
ssb                    51854  1 b43

##### interfaces #####

auto lo
iface lo inet loopback

##### ifconfig #####

eth0      Link encap:Ethernet  HWaddr <MAC addr eth0>  
          inet addr:192.168.0.106  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::216:d4ff:fe37:69d4/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:11066 errors:0 dropped:0 overruns:0 frame:0
          TX packets:9738 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:8350103 (8.3 MB)  TX bytes:1064829 (1.0 MB)

##### iwconfig #####

lo        no wireless extensions.

eth0      no wireless extensions.

##### route #####

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.0.1     0.0.0.0         UG    0      0        0 eth0
192.168.0.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0

##### resolv.conf #####

nameserver 127.0.1.1

##### nm-tool #####

NetworkManager Tool

State: connected (global)

- Device: eth0  [Conexión cableada 1] -----------------------------------------
  Type:              Wired
  Driver:            8139too
  State:             connected
  Default:           yes
  HW Address:        <MAC addr eth0>

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.0.106
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.0.1

    DNS:             192.168.0.1

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

lo        no frequency information.

eth0      no frequency information.

##### iwlist scan #####

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

##### module infos #####

[b43]
filename:       /lib/modules/3.13.0-34-generic/kernel/drivers/net/wireless/b43/b43.ko
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
srcversion:     42BAE2DB9BADE3E7ECA2CC0
depends:        bcma,ssb,mac80211,cfg80211
intree:         Y
vermagic:       3.13.0-34-generic SMP mod_unload modversions 686 
signer:         Magrathea: Glacier signing key
sig_key:        1B:7C:0F:16:16:8C:4B:25:C3:A0:5A:6A:43:09:1C:85:06:E3:73:DF
sig_hashalgo:   sha512
parm:           bad_frames_preempt:enable(1) / disable(0) Bad Frames Preemption (int)
parm:           fwpostfix:Postfix for the .fw files to load. (string)
parm:           hwpctl:Enable hardware-side power control (default off) (int)
parm:           nohwcrypt:Disable hardware encryption. (int)
parm:           hwtkip:Enable hardware tkip. (int)
parm:           qos:Enable QOS support (default on) (int)
parm:           btcoex:Enable Bluetooth coexistence (default on) (int)
parm:           verbose:Log message verbosity: 0=error, 1=warn, 2=info(default), 3=debug (int)
parm:           pio:Use PIO accesses by default: 0=DMA, 1=PIO (int)
parm:           allhwsupport:Enable support for all hardware (even it if overlaps with the brcmsmac driver) (int)

[bcma]
filename:       /lib/modules/3.13.0-34-generic/kernel/drivers/bcma/bcma.ko
license:        GPL
description:    Broadcom's specific AMBA driver
srcversion:     E41B811D88783DD5BC38565
depends:        
intree:         Y
vermagic:       3.13.0-34-generic SMP mod_unload modversions 686 
signer:         Magrathea: Glacier signing key
sig_key:        1B:7C:0F:16:16:8C:4B:25:C3:A0:5A:6A:43:09:1C:85:06:E3:73:DF
sig_hashalgo:   sha512

[ssb]
filename:       /lib/modules/3.13.0-34-generic/kernel/drivers/ssb/ssb.ko
license:        GPL
description:    Sonics Silicon Backplane driver
srcversion:     3DE188310F77C566C2E8CB3
depends:        
intree:         Y
vermagic:       3.13.0-34-generic SMP mod_unload modversions 686 
signer:         Magrathea: Glacier signing key
sig_key:        1B:7C:0F:16:16:8C:4B:25:C3:A0:5A:6A:43:09:1C:85:06:E3:73:DF
sig_hashalgo:   sha512

##### module parameters #####

[b43]
allhwsupport: 0
bad_frames_preempt: 0
btcoex: 1
hwpctl: 0
hwtkip: 0
nohwcrypt: 0
pio: 0
qos: 1
verbose: 2

##### /etc/modules #####

lp

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

##### udev rules #####

[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x10ec:0x8139 (8139too)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC addr eth0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

##### dmesg #####

[    1.637963] ssb: Found chip with id 0x4318, rev 0x02 and package 0x02
[    1.637981] ssb: Core 0 found: ChipCommon (cc 0x800, rev 0x0D, vendor 0x4243)
[    1.637990] ssb: Core 1 found: IEEE 802.11 (cc 0x812, rev 0x09, vendor 0x4243)
[    1.637999] ssb: Core 2 found: PCI (cc 0x804, rev 0x0C, vendor 0x4243)
[    1.638008] ssb: Core 3 found: PCMCIA (cc 0x80D, rev 0x07, vendor 0x4243)
[    1.681161] ssb: Sonics Silicon Backplane found on PCI device 0000:06:02.0
[   14.003896] b43-phy0: Broadcom 4318 WLAN found (core revision 9)
[   14.052037] b43-phy0: Found PHY: Analog 3, Type 2 (G), Revision 7
[   14.605079] b43 ssb0:0: Direct firmware load failed with error -2
[   14.605087] b43 ssb0:0: Falling back to user helper
[   14.606117] b43 ssb0:0: Direct firmware load failed with error -2
[   14.606121] b43 ssb0:0: Falling back to user helper
[   14.609523] b43 ssb0:0: Direct firmware load failed with error -2
[   14.609528] b43 ssb0:0: Falling back to user helper
[   14.610199] b43 ssb0:0: Direct firmware load failed with error -2
[   14.610203] b43 ssb0:0: Falling back to user helper
[   14.613339] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found
[   14.613348] b43-phy0 ERROR: Firmware file "b43-open/ucode5.fw" not found
[   14.613353] b43-phy0 ERROR: You must go to http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware and download the correct firmware for this driver version. Please carefully read all instructions on this website.

########## wireless info END ############


```

---

### Post by westie457 on 2014-08-20
Welcome Enrique

You have the wrong driver installed, in theory easy enough to rectify.

Plug in an ethernet cable and open a terminal (Ctrl+Alt+T is the quick way), then type in and run ```
sudo apt-get purge b43-fwcutter firmware-b43-installer
sudo apt-get update
sudo apt-get install linux-firmware-nonfree
sudo reboot
```
While the computer is rebooting unplug the cable.

Let us know what happens.

ps I am going to ask one of the moderators to move your post and this answer to its own thread. So if you cannot find it easily after click on 'Quick Links' at the top of the page and select 'Find My Posts'

---

### Post by overdrank on 2014-08-20
Hi and welcome, moved to own thread. :)

---

### Post by QIII on 2014-08-20
Simultaneous moderator action on both the move and the text cleanup!

Woot!

---

