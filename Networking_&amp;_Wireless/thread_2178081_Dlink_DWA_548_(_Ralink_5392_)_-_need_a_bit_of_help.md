---
title: "Dlink DWA 548 ( Ralink 5392 ) - need a bit of help getting proprietary driver to run"
date: 2013-10-01
forum: Networking &amp; Wireless
---

### Post by Ilya80 on 2013-10-01
Hello,

I need a bit of help with a Dlink DWA 548 ( based on Ralink 5392 ). Its installed in an old box I`m using as a home router/wifi ap.

It`s running debian with 3.11.1 kernel. The card works out of the box, but I`m having nasty issues with connection quality, even in a crowded wifi environment I`m getting up to 50% packet loss on client pc's and very low transfer speeds, merely ~10 m away from the router.

I`ve tried playing around with modes in hostapd.conf but b/g modes did no good to stability. So I figured I need to build/install the proprietary driver, and eventually failed at that.

Following Chilli's instructions in older posts I downloaded the latest version of proprietary driver, updated config.mk and makefiles appropriately ( had to get rid of some macros that are gone in later kernels ) and built the driver. I`m pertty sure I tried with [COLOR=#000000]*HAS_WPA_SUPPLICANT=y and  HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=y/n *[/COLOR]

After building the driver I installed it and blacklisted stock drivers in /etc/modprobe.d/blacklist.conf

However when I booted - hostapd refused to start, complaining about 

```
nl80211: 'nl80211' generic netlink not found
```

I tried editing the .dat file in /etc/Wireless, but the changes seemed to have no effect. 

Last thing I tried was poking around iwpriv commands as described in iwpriv_usage.txt in the driver docs, but to no success.

Right now I`m completely lost and need few pointers on how to correctly load & configure rt5390sta.ko driver that I build. I`ll gladly provide any log/config files needed.

Thanks in advance,
Ilya.

---

### Post by Ilya80 on 2013-10-02
Bump and here's output of Varunendra's wireless script:

```

*************** info trace ***************

***** uname -a *****

Linux island 3.11.1 #2 SMP Mon Sep 23 21:57:11 MSK 2013 x86_64 GNU/Linux

***** lsb_release *****

Distributor ID: Debian
Description:    Debian GNU/Linux 7.1 (wheezy)
Release:        7.1
Codename:       wheezy

***** lspci *****

00:07.0 Bridge [0680]: NVIDIA Corporation MCP61 Ethernet [10de:03ef] (rev a2)
        Subsystem: ASRock Incorporation 939NF6G-VSTA Board [1849:03ef]
        Kernel driver in use: forcedeth
--
01:08.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ [10ec:8139] (rev 10)
        Subsystem: Allied Telesyn International Device [1259:c10f]
        Kernel driver in use: 8139too
03:00.0 Network controller [0280]: Ralink corp. Device [1814:5392]
        Subsystem: D-Link System Inc Device [1186:3c06]
        Kernel driver in use: rt2860

***** lsusb *****

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

***** PCMCIA Card Info *****


***** iwconfig *****

ra0       Ralink STA  ESSID:""  Nickname:"RT2860STA"
          Mode:Auto  Frequency=2.412 GHz  Bit Rate:1 Mb/s   
          RTS thr:off   Fragment thr:off
          Encryption key:off
          Link Quality=10/100  Signal level:0 dBm  Noise level:0 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


***** rfkill *****


***** lsmod *****

rt5390sta            1406521  1 

***** nm-tool *****

***** NetworkManager.state *****

***** NetworkManager.conf *****


***** interfaces *****

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface // WAN
auto eth1
iface eth1 inet dhcp

#Bridged local network // LAN
auto br0
iface br0 inet static
    bridge_ports eth0 ra0
    address 192.168.1.1
    network 192.168.1.0
    netmask 255.255.255.0
    broadcast 192.168.1.255


# The secondary network interface // LAN, wired
auto eth0
iface eth0 inet static
    address 192.168.1.2
    network 192.168.1.0
    netmask 255.255.255.0
    broadcast 192.168.1.255
    post-up ip route del 192.168.1.0/24 dev eth0

#The third network inteface // LAN, wifi
auto ra0
iface ra0 inet static
    address 192.168.1.3
    network 192.168.1.0
    netmask 255.255.255.0
    broadcast 192.168.1.255
    post-up ip route del 192.168.1.0/24 dev ra0


***** iwlist *****

ra0       Scan completed :
          Cell 01 - Address: <MAC address removed>
                    Protocol:802.11b/g/n
                    ESSID:"TP-LINK_58B272"
                    Mode:Managed
                    Frequency:2.452 GHz (Channel 9)
                    Quality=52/100  Signal level=-69 dBm  Noise level=-92 dBm
                    Encryption key:on
                    Bit Rates:54 Mb/s
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD0E0050F204104A0001101044000101
          Cell 02 - Address: <MAC address removed>
                    Protocol:802.11b/g
                    ESSID:"nw-express.ru"
                    Mode:Managed
                    Frequency:2.462 GHz (Channel 11)
                    Quality=31/100  Signal level=-77 dBm  Noise level=-82 dBm
                    Encryption key:on
                    Bit Rates:54 Mb/s
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: <MAC address removed>
                    Protocol:802.11b/g/n
                    ESSID:"Ekran13FSB"
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality=42/100  Signal level=-73 dBm  Noise level=-68 dBm
                    Encryption key:on
                    Bit Rates:150 Mb/s
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F204104A00011010440001021049000600372A000120
          Cell 04 - Address: <MAC address removed>
                    Protocol:802.11b/g
                    ESSID:"linksys"
                    Mode:Managed
                    Frequency:2.462 GHz (Channel 11)
                    Quality=23/100  Signal level=-81 dBm  Noise level=-86 dBm
                    Encryption key:on
                    Bit Rates:54 Mb/s
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 05 - Address: <MAC address removed>
                    Protocol:802.11b/g
                    ESSID:"20145"
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality=18/100  Signal level=-83 dBm  Noise level=-78 dBm
                    Encryption key:on
                    Bit Rates:54 Mb/s
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD0E0050F204104A0001101044000102
          Cell 06 - Address: <MAC address removed>
                    Protocol:802.11g/n
                    ESSID:"ZyXEL_KEENETIC_4AA572"
                    Mode:Managed
                    Frequency:2.432 GHz (Channel 5)
                    Quality=23/100  Signal level=-81 dBm  Noise level=-76 dBm
                    Encryption key:on
                    Bit Rates:54 Mb/s
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD270050F204104A0001101044000102104700102880288028801880A880CC5D4E4AA572103C000101
          Cell 07 - Address: <MAC address removed>
                    Protocol:802.11b/g/n
                    ESSID:"JWAR"
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality=42/100  Signal level=-73 dBm  Noise level=-68 dBm
                    Encryption key:on
                    Bit Rates:144 Mb/s
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD0E0050F204104A0001101044000102
          Cell 08 - Address: <MAC address removed>
                    Protocol:802.11b/g
                    ESSID:"aliden186"
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality=18/100  Signal level=-83 dBm  Noise level=-78 dBm
                    Encryption key:on
                    Bit Rates:54 Mb/s
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK


***** resolv.conf *****

nameserver 94.19.255.2
nameserver 93.100.1.3

***** blacklist *****

[/etc/modprobe.d/blacklist.conf]
blacklist rt2800pci
blacklist rt2800lib
blacklist rt2x00usb
blacklist rt2x00pci
blacklist rt2x00lib
blacklist rt2860sta
blacklist rt3090sta

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

***** modinfo *****

filename:       /lib/modules/3.11.1/kernel/drivers/net/wireless/rt5390sta.ko
version:        2.6.0.0
srcversion:     D3FCF2F656E3CA98D53C20C
alias:          pci:v00001186d00003C05sv*sd*bc*sc*i*
alias:          pci:v00001814d00005362sv*sd*bc*sc*i*
alias:          pci:v00001814d00005392sv*sd*bc*sc*i*
alias:          pci:v00001814d0000539Fsv*sd*bc*sc*i*
alias:          pci:v00001814d00005390sv*sd*bc*sc*i*
alias:          pci:v00001814d00003390sv*sd*bc*sc*i*
alias:          pci:v00001814d00003092sv*sd*bc*sc*i*
alias:          pci:v00001814d00003091sv*sd*bc*sc*i*
alias:          pci:v00001814d00003090sv*sd*bc*sc*i*
depends:        
vermagic:       3.11.1 SMP mod_unload modversions 
parm:           mac:rt28xx: wireless mac addr (charp)


***** udev rules *****

# PCI device 0x10de:/sys/devices/pci0000:00/0000:00:07.0 (forcedeth)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

# PCI device 0x10ec:/sys/devices/pci0000:00/0000:00:04.0/0000:01:08.0 (8139too)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth1"

# PCI device 0x1814:/sys/devices/pci0000:00/0000:00:0b.0/0000:03:00.0 (rt2800pci)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="ra0"

***** dmesg *****

[    1.180974] forcedeth 0000:00:07.0: ifname eth1, PHY OUI 0x732 @ 1, addr <MAC address removed>
[    8.689453] rt5390sta: module license 'unspecified' taints kernel.
[   15.157699] 8139too 0000:01:08.0 eth1: link up, 100Mbps, full-duplex, lpa 0x41E1
[   15.692338] Modules linked in: bridge stp llc xt_tcpudp xt_state iptable_filter ipt_MASQUERADE iptable_nat nf_conntrack_ipv4 nf_defrag_ipv4 nf_nat_ipv4 nf_nat nf_conntrack ip_tables x_tables w83627ehf hwmon_vid loop rt5390sta(PO) nouveau mxm_wmi wmi video ttm drm_kms_helper snd_pcsp drm kvm_amd kvm snd_pcm i2c_algo_bit ohci_pci snd_page_alloc ohci_hcd ehci_pci snd_timer ehci_hcd snd usbcore soundcore serio_raw mperf i2c_nforce2 evdev edac_mce_amd usb_common k8temp i2c_core edac_core processor button thermal_sys sg sd_mod crc_t10dif ata_generic 8139too 8139cp mii sata_nv pata_amd forcedeth libata scsi_mod
[   15.692431]  [<ffffffffa043be2b>] ? RtmpAsicSendCommandToMcu+0x75b/0x890 [rt5390sta]
[   15.692445]  [<ffffffffa03be924>] ? AsicSendCommandToMcuBBP+0x24/0x30 [rt5390sta]
[   15.692455]  [<ffffffffa0393850>] ? NICInitBBP+0x1280/0x2af0 [rt5390sta]
[   15.692466]  [<ffffffffa039574b>] ? NICInitializeAsic+0x2eb/0x590 [rt5390sta]
[   15.692475]  [<ffffffffa0395b78>] ? NICInitializeAdapter+0x188/0x690 [rt5390sta]
[   15.692486]  [<ffffffffa039cc94>] ? rt28xx_init+0x294/0x710 [rt5390sta]
[   15.692497]  [<ffffffffa0418bbc>] ? rt28xx_open+0x8c/0xf0 [rt5390sta]
[   15.692510]  [<ffffffffa03ac4cb>] ? RTMP_COM_IoctlHandle+0x52b/0x580 [rt5390sta]
[   15.692524]  [<ffffffffa041862e>] ? MainVirtualIF_open+0x3e/0xd0 [rt5390sta]
[   15.692535]  [<ffffffffa0418b30>] ? RtmpOSIRQRequest+0xe0/0xe0 [rt5390sta]
[   15.692545]  [<ffffffffa0418560>] ? RtmpNetEthConvertDevSearch+0x70/0x70 [rt5390sta]
[   15.770797] <==== rt28xx_init, Status=0
[   15.770917] ====> rt30xx Read PowerLevelMode =  0x3.
[   15.770919] ====> rt30xx F Write 0x83 Command = 0x3.

****************** done ******************


```

---

### Post by Ilya80 on 2013-10-02
Oh this is bad. It seems the driver is way too outdated to support AP mode. 

I found the config options HAS_APCLI and HAS_APCLI_WPA_SUPPLICANT in config.mk and set them both to =y

To build the driver I had to patch the source to conform to new definition of [http://wireless.kernel.org/80211books/API-ieee80211-channel-to-frequency.html](http://wireless.kernel.org/80211books/API-ieee80211-channel-to-frequency.html) and also the struct [http://wireless.kernel.org/80211books/API-struct-cfg80211-ops.html](http://wireless.kernel.org/80211books/API-struct-cfg80211-ops.html) 

The driver built successfully, and hostapd now successfuly found it, but now it failed to initialize it:

kalujny@island:~$ sudo hostapd -d /etc/hostapd/hostapd.conf 
random: Trying to read entropy from /dev/random
Configuration file: /etc/hostapd/hostapd.conf
nl80211: interface ra0 in phy phy0
rfkill: initial event: idx=0 type=1 op=0 soft=0 hard=0
nl80211: Register frame command failed (type=208): ret=-95 (Operation not supported)
nl80211: Register frame match - hexdump(len=2): 04 0a
nl80211: Failed to register Action frame processing - ignore for now
nl80211: Add own interface ifindex 5
nl80211: Add own interface ifindex 4
nl80211: Set mode ifindex 4 iftype 3 (AP)
nl80211: Failed to set interface 4 to mode 3: -95 (Operation not supported)
nl80211: Interface already in requested mode - ignore error
nl80211: Create interface iftype 6 (MONITOR)
Failed to create interface mon.ra0: -95 (Operation not supported)
nl80211: Driver does not support monitor interface type - try to run without it
nl80211: Adding interface ra0 into bridge br0
Could not add interface ra0 into bridge br0: Operation not supported
nl80211: Failed to add interface ra0 into bridge br0: Operation not supported
netlink: Operstate: linkmode=0, operstate=6
nl80211: Set mode ifindex 4 iftype 2 (STATION)
nl80211 driver initialization failed.


Diagnostic script now ouputs:

```

*************** info trace ***************

***** uname -a *****

Linux island 3.11.1 #2 SMP Mon Sep 23 21:57:11 MSK 2013 x86_64 GNU/Linux

***** lsb_release *****

Distributor ID: Debian
Description:    Debian GNU/Linux 7.1 (wheezy)
Release:        7.1
Codename:       wheezy

***** lspci *****

00:07.0 Bridge [0680]: NVIDIA Corporation MCP61 Ethernet [10de:03ef] (rev a2)
        Subsystem: ASRock Incorporation 939NF6G-VSTA Board [1849:03ef]
        Kernel driver in use: forcedeth
--
01:08.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ [10ec:8139] (rev 10)
        Subsystem: Allied Telesyn International Device [1259:c10f]
        Kernel driver in use: 8139too
03:00.0 Network controller [0280]: Ralink corp. Device [1814:5392]
        Subsystem: D-Link System Inc Device [1186:3c06]
        Kernel driver in use: rt2860

***** lsusb *****

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

***** PCMCIA Card Info *****


***** iwconfig *****

ra0       Ralink STA  
          Power Management:on
          

***** rfkill *****


***** lsmod *****

rt5390sta            1429778  0 
cfg80211              394207  1 rt5390sta

***** nm-tool *****

***** NetworkManager.state *****

***** NetworkManager.conf *****


***** interfaces *****

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface // WAN
auto eth1
iface eth1 inet dhcp

#Bridged local network // LAN
auto br0
iface br0 inet static
    bridge_ports eth0 ra0
    address 192.168.1.1
    network 192.168.1.0
    netmask 255.255.255.0
    broadcast 192.168.1.255


# The secondary network interface // LAN, wired
auto eth0
iface eth0 inet static
    address 192.168.1.2
    network 192.168.1.0
    netmask 255.255.255.0
    broadcast 192.168.1.255
    post-up ip route del 192.168.1.0/24 dev eth0

#The third network inteface // LAN, wifi
auto ra0
iface ra0 inet static
    address 192.168.1.3
    network 192.168.1.0
    netmask 255.255.255.0
    broadcast 192.168.1.255
    post-up ip route del 192.168.1.0/24 dev ra0


***** iwlist *****


***** resolv.conf *****

nameserver 94.19.255.2
nameserver 93.100.1.3

***** blacklist *****

[/etc/modprobe.d/blacklist.conf]
blacklist rt2800pci
blacklist rt2800lib
blacklist rt2x00usb
blacklist rt2x00pci
blacklist rt2x00lib
blacklist rt2860sta
blacklist rt3090sta

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

***** modinfo *****

filename:       /lib/modules/3.11.1/kernel/drivers/net/wireless/rt5390sta.ko
version:        2.6.0.0
srcversion:     D2B0CAEAB951671446F0A70
alias:          pci:v00001186d00003C05sv*sd*bc*sc*i*
alias:          pci:v00001814d00005362sv*sd*bc*sc*i*
alias:          pci:v00001814d00005392sv*sd*bc*sc*i*
alias:          pci:v00001814d0000539Fsv*sd*bc*sc*i*
alias:          pci:v00001814d00005390sv*sd*bc*sc*i*
alias:          pci:v00001814d00003390sv*sd*bc*sc*i*
alias:          pci:v00001814d00003092sv*sd*bc*sc*i*
alias:          pci:v00001814d00003091sv*sd*bc*sc*i*
alias:          pci:v00001814d00003090sv*sd*bc*sc*i*
depends:        cfg80211
vermagic:       3.11.1 SMP mod_unload modversions 
parm:           mac:rt28xx: wireless mac addr (charp)


***** udev rules *****

# PCI device 0x10de:/sys/devices/pci0000:00/0000:00:07.0 (forcedeth)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

# PCI device 0x10ec:/sys/devices/pci0000:00/0000:00:04.0/0000:01:08.0 (8139too)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth1"

# PCI device 0x1814:/sys/devices/pci0000:00/0000:00:0b.0/0000:03:00.0 (rt2800pci)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="ra0"

***** dmesg *****

[    1.200988] forcedeth 0000:00:07.0: ifname eth1, PHY OUI 0x732 @ 1, addr <MAC address removed>
[    8.741879] rt5390sta: module license 'unspecified' taints kernel.
[   14.958009] 8139too 0000:01:08.0 eth1: link up, 100Mbps, full-duplex, lpa 0x41E1
[   15.500301] Modules linked in: bridge stp llc xt_tcpudp xt_state iptable_filter ipt_MASQUERADE iptable_nat nf_conntrack_ipv4 nf_defrag_ipv4 nf_nat_ipv4 nf_nat nf_conntrack ip_tables x_tables w83627ehf hwmon_vid loop rt5390sta(PO) nouveau mxm_wmi wmi video ttm drm_kms_helper snd_pcsp drm kvm_amd ohci_pci kvm snd_pcm ohci_hcd ehci_pci i2c_algo_bit ehci_hcd snd_page_alloc usbcore snd_timer cfg80211 snd usb_common i2c_nforce2 soundcore edac_mce_amd rfkill mperf serio_raw i2c_core evdev edac_core k8temp processor button thermal_sys sg sd_mod crc_t10dif pata_amd 8139too 8139cp ata_generic mii forcedeth sata_nv libata scsi_mod
[   15.500397]  [<ffffffffa049ed1b>] ? RtmpAsicSendCommandToMcu+0x75b/0x890 [rt5390sta]
[   15.500411]  [<ffffffffa041df64>] ? AsicSendCommandToMcuBBP+0x24/0x30 [rt5390sta]
[   15.500421]  [<ffffffffa03f28e0>] ? NICInitBBP+0x1280/0x2af0 [rt5390sta]
[   15.500432]  [<ffffffffa03f47db>] ? NICInitializeAsic+0x2eb/0x590 [rt5390sta]
[   15.500441]  [<ffffffffa03f4c08>] ? NICInitializeAdapter+0x188/0x690 [rt5390sta]
[   15.500453]  [<ffffffffa03fbdf4>] ? rt28xx_init+0x294/0x710 [rt5390sta]
[   15.500465]  [<ffffffffa0478f2c>] ? rt28xx_open+0x8c/0xf0 [rt5390sta]
[   15.500477]  [<ffffffffa040b62f>] ? RTMP_COM_IoctlHandle+0x53f/0x590 [rt5390sta]
[   15.500492]  [<ffffffffa047899e>] ? MainVirtualIF_open+0x3e/0xd0 [rt5390sta]
[   15.500503]  [<ffffffffa0478ea0>] ? RtmpOSIRQRequest+0xe0/0xe0 [rt5390sta]
[   15.500513]  [<ffffffffa04788d0>] ? RtmpNetEthConvertDevSearch+0x70/0x70 [rt5390sta]
[   15.604131] <==== rt28xx_init, Status=0
[   15.604292] ====> rt30xx Read PowerLevelMode =  0x3.
[   15.604294] ====> rt30xx F Write 0x83 Command = 0x3.

****************** done ******************

```

---

### Post by Ilya80 on 2013-10-03
Marking this as solved since in the end it turns out I`m far better off with a driver that comes with the kernel.

---

