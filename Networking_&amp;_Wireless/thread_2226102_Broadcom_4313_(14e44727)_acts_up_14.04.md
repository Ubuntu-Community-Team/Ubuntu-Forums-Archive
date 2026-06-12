---
title: "Broadcom 4313 (14e4:4727) acts up 14.04"
date: 2014-05-25
forum: Networking &amp; Wireless
---

### Post by Rob Sayer on 2014-05-25
Just finished installing xubuntu 14.04 this morning.  Mostly works fine AFAIK.  But the wireless is acting up a bit again.  Not as bad as 12.04, mind you ...

I went to the cafe hotspot I had big problems with in 12.04 (it overloaded their router) and it connected fine.  But after a coupkke of minutes it stopped working (though it stayed connected).  It wouldn't stay connected long enough to update my software sources.

So I rebooted and installed linux-firmware-nonfree.  It worked long enough to download it.  But it didn't help.

I'm now using another cafe hotspot and it works better, but seems a bit slow.  Though it's hard to tell that sort of thing.

There's a message on boot involving b43 that I never had before.  Here's an extract from the kernel log (I don't think the last line is relevant):

```
May 24 16:47:43 WeePuter kernel: [   13.423932] [drm] Initialized gma500 1.0.0 2011-06-06 for 0000:00:02.0 on minor 0
May 24 16:47:43 WeePuter kernel: [   13.424435] snd_hda_intel 0000:00:1b.0: irq 47 for MSI/MSI-X
May 24 16:47:43 WeePuter kernel: [   13.507493] Support for cores revisions 0x17 and 0x18 disabled by module param allhwsupport=0. Try b43.allhwsupport=1
May 24 16:47:43 WeePuter kernel: [   13.507503] b43: probe of bcma0:0 failed with error -524
May 24 16:47:43 WeePuter kernel: [   13.510013] Broadcom 43xx driver loaded [ Features: PNL ]
May 24 16:47:43 WeePuter kernel: [   13.584337] hda_codec: ALC269VB: SKU not ready 0x598301f0
```

I found another thread where it was recommended to install linux-firmware.  Apparently that's included in the nonfree firmware because I tried to install it and it was already there.

Here's the output of:

sudo lshw -C network

```
  *-network               
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: eth0
       version: 05
       serial: 04:7d:7b:50:97:53
       size: 10Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=rtl_nic/rtl8105e-1.fw latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:44 ioport:4000(size=256) memory:40004000-40004fff memory:40000000-40003fff
  *-network
       description: Network controller
       product: BCM4313 802.11bgn Wireless Network Adapter
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=bcma-pci-bridge latency=0
       resources: irq:17 memory:44000000-44003fff
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: c0:18:85:0e:f5:ac
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=brcmsmac driverversion=3.13.0-24-generic firmware=610.812 ip=192.168.65.50 link=yes multicast=yes wireless=IEEE 802.11bgn
```

And here's the output of wireless-info script (I deleted the iwlist info for nodes I wasn't connected to for brevity):

```
########## wireless info START ##########

##### release #####

Distributor ID:    Ubuntu
Description:    Ubuntu 14.04 LTS
Release:    14.04
Codename:    trusty

##### kernel #####

Linux WeePuter 3.13.0-24-generic #47-Ubuntu SMP Fri May 2 23:31:42 UTC 2014 i686 i686 i686 GNU/Linux

##### lspci #####

01:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 05)
    Subsystem: Acer Incorporated [ALI] Device [1025:061f]
    Kernel driver in use: r8169
02:00.0 Network controller [0280]: Broadcom Corporation BCM4313 802.11bgn Wireless Network Adapter [14e4:4727] (rev 01)
    Subsystem: Foxconn International, Inc. Device [105b:e042]
    Kernel driver in use: bcma-pci-bridge

##### lsusb #####

Bus 001 Device 004: ID 0781:5530 SanDisk Corp. Cruzer
Bus 001 Device 002: ID 1bcf:288a Sunplus Innovation Technology Inc. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 045e:0745 Microsoft Corp. Nano Transceiver v1.0 for Bluetooth
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

##### PCMCIA Card Info #####

##### rfkill #####

0: acer-wireless: Wireless LAN
    Soft blocked: no
    Hard blocked: no
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

wlan0     IEEE 802.11bgn  ESSID:"JustUs! Wolfville"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: <MAC address removed>   
          Bit Rate=57.8 Mb/s   Tx-Power=19 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=49/70  Signal level=-61 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:1874  Invalid misc:18357   Missed beacon:0

##### route #####

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.65.1    0.0.0.0         UG    0      0        0 wlan0
192.168.65.0    0.0.0.0         255.255.255.0   U     9      0        0 wlan0

##### resolv.conf #####

nameserver 127.0.1.1

##### nm-tool #####

NetworkManager Tool

State: connected (global)

- Device: wlan0  [JustUs! Wolfville] -------------------------------------------
  Type:              802.11 WiFi
  Driver:            brcmsmac
  State:             connected
  Default:           yes
  HW Address:        <MAC address removed>

  Capabilities:
    Speed:           57 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    AlWhittleTheatre:Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 60 WPA WPA2
    AcadiaCinemaCoop:Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 52 WPA WPA2
    ALittleIneptAndNotTrained: Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 42 WPA
    BellAliant5:     Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 34 WPA WPA2
    *JustUs! Wolfville: Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 65 WPA2
    DIME:            Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 29 WPA2
    MOTOROLA-981CA:  Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 39 WPA2
    MOTOROLA-22CD6:  Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 22 WPA2
    HerbinPublic:    Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 27 WPA2
    Lady Ga Ga:      Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 35 WEP

  IPv4 Settings:
    Address:         192.168.65.50
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.65.1

    DNS:             192.168.65.1

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
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=54/70  Signal level=-56 dBm  
                    Encryption key:on
                    ESSID:"JustUs! Wolfville"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000085ba77b691
                    Extra: Last beacon: 84ms ago
                    IE: Unknown: 00114A75737455732120576F6C6676696C6C65
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030106
                    IE: Unknown: 2A0104
                    IE: Unknown: 2F0104
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1AFC191BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1606001700000000000000000000000000000000000000
                    IE: Unknown: DD09001018020EF02C0000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00

##### iwlist channel #####

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
          Current Frequency=2.437 GHz (Channel 6)

##### lsmod #####

brcmsmac              529837  0 
cordic                 12518  1 brcmsmac
brcmutil               15066  1 brcmsmac
b43                   356470  0 
mac80211              545990  2 b43,brcmsmac
cfg80211              409394  3 b43,brcmsmac,mac80211
ssb                    51854  1 b43
bcma                   42043  3 b43,brcmsmac

##### modinfo #####

filename:       /lib/modules/3.13.0-24-generic/kernel/drivers/net/wireless/brcm80211/brcmsmac/brcmsmac.ko
firmware:       brcm/bcm43xx_hdr-0.fw
firmware:       brcm/bcm43xx-0.fw
license:        Dual BSD/GPL
description:    Broadcom 802.11n wireless LAN driver.
author:         Broadcom Corporation
srcversion:     43D6897F7EB716081DF69BE
alias:          bcma:m04BFid0812rev18cl*
alias:          bcma:m04BFid0812rev17cl*
alias:          bcma:m04BFid0812rev11cl*
depends:        bcma,mac80211,brcmutil,cfg80211,cordic
intree:         Y
vermagic:       3.13.0-24-generic SMP mod_unload modversions 686 
signer:         Magrathea: Glacier signing key
sig_key:        <MAC address removed>:A1:7E:EF:58:C6:AC:5E:9A:85:71:2C:92:08:DF
sig_hashalgo:   sha512

filename:       /lib/modules/3.13.0-24-generic/kernel/drivers/net/wireless/brcm80211/brcmutil/brcmutil.ko
license:        Dual BSD/GPL
description:    Broadcom 802.11n wireless LAN driver utilities.
author:         Broadcom Corporation
srcversion:     E81EE4CBB6A7A689150D93D
depends:        
intree:         Y
vermagic:       3.13.0-24-generic SMP mod_unload modversions 686 
signer:         Magrathea: Glacier signing key
sig_key:        <MAC address removed>:A1:7E:EF:58:C6:AC:5E:9A:85:71:2C:92:08:DF
sig_hashalgo:   sha512

filename:       /lib/modules/3.13.0-24-generic/kernel/drivers/net/wireless/b43/b43.ko
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
srcversion:     BED87D210887FFC71A4BDE0
alias:          bcma:m04BFid0812rev1Dcl*
alias:          bcma:m04BFid0812rev18cl*
alias:          bcma:m04BFid0812rev17cl*
alias:          bcma:m04BFid0812rev11cl*
alias:          ssb:v4243id0812rev10*
alias:          ssb:v4243id0812rev0F*
alias:          ssb:v4243id0812rev0D*
alias:          ssb:v4243id0812rev0C*
alias:          ssb:v4243id0812rev0B*
alias:          ssb:v4243id0812rev0A*
alias:          ssb:v4243id0812rev09*
alias:          ssb:v4243id0812rev07*
alias:          ssb:v4243id0812rev06*
alias:          ssb:v4243id0812rev05*
depends:        bcma,ssb,mac80211,cfg80211
intree:         Y
vermagic:       3.13.0-24-generic SMP mod_unload modversions 686 
signer:         Magrathea: Glacier signing key
sig_key:        <MAC address removed>:A1:7E:EF:58:C6:AC:5E:9A:85:71:2C:92:08:DF
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

filename:       /lib/modules/3.13.0-24-generic/kernel/drivers/ssb/ssb.ko
license:        GPL
description:    Sonics Silicon Backplane driver
srcversion:     3DE188310F77C566C2E8CB3
alias:          pci:v000014E4d00004350sv*sd*bc*sc*i*
alias:          pci:v000014E4d0000432Csv*sd*bc*sc*i*
alias:          pci:v000014E4d0000432Bsv*sd*bc*sc*i*
alias:          pci:v000014E4d00004329sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004328sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004325sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004324sv*sd*bc*sc*i*
alias:          pci:v000014E4d0000A8D6sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004322sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004321sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004320sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004319sv*sd*bc*sc*i*
alias:          pci:v000014A4d00004318sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004318sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004315sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004312sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004311sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004307sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004306sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004301sv*sd*bc*sc*i*
depends:        
intree:         Y
vermagic:       3.13.0-24-generic SMP mod_unload modversions 686 
signer:         Magrathea: Glacier signing key
sig_key:        <MAC address removed>:A1:7E:EF:58:C6:AC:5E:9A:85:71:2C:92:08:DF
sig_hashalgo:   sha512

filename:       /lib/modules/3.13.0-24-generic/kernel/drivers/bcma/bcma.ko
license:        GPL
description:    Broadcom's specific AMBA driver
srcversion:     E41B811D88783DD5BC38565
alias:          pci:v000014E4d00004727sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004365sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004359sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004358sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004357sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004353sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004331sv*sd*bc*sc*i*
alias:          pci:v000014E4d0000A8D8sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004313sv*sd*bc*sc*i*
alias:          pci:v000014E4d00000576sv*sd*bc*sc*i*
depends:        
intree:         Y
vermagic:       3.13.0-24-generic SMP mod_unload modversions 686 
signer:         Magrathea: Glacier signing key
sig_key:        <MAC address removed>:A1:7E:EF:58:C6:AC:5E:9A:85:71:2C:92:08:DF
sig_hashalgo:   sha512

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

# PCI device 0x10ec:0x8136 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

# PCI device 0x14e4:0x4727 (brcmsmac)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

##### dmesg #####

[    4.861905] psmouse serio2: elantech: assuming hardware version 3 (with firmware version 0x250f00)
[   16.397868] bcma: bus0: Found chip with id 0x4313, rev 0x01 and package 0x08
[   16.397914] bcma: bus0: Core 0 found: ChipCommon (manuf 0x4BF, id 0x800, rev 0x24, class 0x0)
[   16.397950] bcma: bus0: Core 1 found: IEEE 802.11 (manuf 0x4BF, id 0x812, rev 0x18, class 0x0)
[   16.398014] bcma: bus0: Core 2 found: PCIe (manuf 0x4BF, id 0x820, rev 0x11, class 0x0)
[   16.452964] bcma: bus0: Bus registered
[   17.611735] Support for cores revisions 0x17 and 0x18 disabled by module param allhwsupport=0. Try b43.allhwsupport=1
[   17.611747] b43: probe of bcma0:0 failed with error -524
[   17.742331] brcmsmac bcma0:0: mfg 4bf core 812 rev 24 class 0 irq 17
[   17.809859] ieee80211 phy0: registered radio enabled led device: brcmsmac-phy0:radio gpio: 243
[   20.712492] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: false (implement)
[   20.713075] brcmsmac bcma0:0: brcms_ops_config: change power-save mode: false (implement)
[   20.714470] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   20.715399] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   72.624138] wlan0: authenticate with <MAC address removed>
[   72.629646] wlan0: send auth to <MAC address removed> (try 1/3)
[   72.631922] wlan0: authenticated
[   72.634363] wlan0: associate with <MAC address removed> (try 1/3)
[   72.640470] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=19)
[   72.641106] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: associated
[   72.641122] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: true (implement)
[   72.641155] wlan0: associated
[   72.641240] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   78.862193] brcmsmac bcma0:0: brcms_ops_bss_info_changed: arp filtering: 1 addresses (implement)
[ 8703.347130] brcmsmac bcma0:0: START: tid 1 is not agg'able
[ 9132.048743] brcmsmac bcma0:0: START: tid 1 is not agg'able
[ 9132.111154] brcmsmac bcma0:0: START: tid 1 is not agg'able
[ 9295.548186] brcmsmac bcma0:0: START: tid 1 is not agg'able
[ 9295.630964] brcmsmac bcma0:0: START: tid 1 is not agg'able
[ 9303.288791] brcmsmac bcma0:0: START: tid 2 is not agg'able
[ 9303.336835] brcmsmac bcma0:0: START: tid 2 is not agg'able

########## wireless info END ############
```

In previous versions I used backports for the wireless module, which I don't think are available now.

It worked quite well in 13.10 with the backport.  I had hoped I was done with this crap.  Sigh ...

---

### Post by praseodym on 2014-05-25
For this driver you need **linux-firmware-nonfree**

Check "dmesg | grep b43"

---

### Post by Rob Sayer on 2014-05-25
I did install linux-firmware-nonfree, that's the first thing I tried.  It didn't help.

Output of:

```
dmesg | grep b43
```

```
[   17.611735] Support for cores revisions 0x17 and 0x18 disabled by module param allhwsupport=0. Try b43.allhwsupport=1
[   17.611747] b43: probe of bcma0:0 failed with error -524
```

Thanks for the quick reply.

---

### Post by praseodym on 2014-05-25
Obviously, this (special) chip is not supported?! Try the station driver.

---

### Post by Hadaka on 2014-05-25
Hi, your wireless card runs best on the native
brcmsmac -but it can sometimes still be
tricky to get it going. please do..
```
sudo modprobe -rf b43
sudo modprobe -rf ssb
sudo modprobe -rf bcma
sudo modprobe brcmsmac 
```
BOOT
does that help?

---

### Post by Rob Sayer on 2014-05-26
Thanks for the responses.

Actually, I'm sitting right now in the hotspot that was giving men trouble before.  I'm still getting the b43 message on boot but it's working now.  No idea why ... digital communications is *not* my strong suit, and cafe hotspots can be iffy.

And I've been getting wireless messages on boot and shutdown pretty consistently with this netbook on 12.04, 13.04 and 13.10, even when it works properly.

My issues happened immediately after installation ... I had just installed 14.04.  I prefer not to update during install, and decided to update in a cafe because it's mostly a lot of waiting and ... well ... they have *coffee* there ....

When I had problems here yesterday ... it'd connect and work for a short time and then not be able to access anything, though it didn't disconnect ... I rebooted and then installed linux-firmware-nonfree while it still could connect.  Which didn't seem to help.

It may be possible that I should have done the initial system update first.

Then I went to another cafe hotspot, which is more reliable (they actually have a real tech support person, believe it or not) and did the updates.  It worked OK there.  A couple of reboots can fix things too.

At this point it's working where it didn't before.  And I don't understand modprobe enough to start doing a bunch of things that may bork the wireless when it's working, since I don't have a wired connection.

Plus, I have absolutely no idea what a "station driver" is, and a quick search didn't yield anything.

I guess I feel I'm dealing with too many variables here.  Too many things changed at once.

So,unless it stops working again I think I'll just leave well enough alone.  Though I don't know whether I should mark this solved or not.

I *know* I should probably just get a USB dongle that has a better supported wireless adapter ... jeez, there are similar problems reported for this one in windoze.  But it doesn't seem to be that simple either.  They often change the actual adapter in the same model.

Again, thanks.

---

### Post by Rob Sayer on 2014-07-18
Still having some issues in that same hotspot ... it starts fine but stops for a while and starts again after a few minutes.  If there are any new backports for this stupid adapter in 14.04 I can't find them.

But with some trepidation I used hadaka's commands from post #5:

```
sudo modprobe -rf b43sudo modprobe -rf ssb
sudo modprobe -rf bcma
sudo modprobe brcmsmac
```

... and nothing broke (I'm very leery of using terminal commands I don't understand, which is not unusual with comms related stuff).

It's working, maybe better ... it's too soon to tell ... I'll change this to solved if so.

---

### Post by Hadaka on 2014-07-18
Hi Rob
this sticky on the wireless network page..
[http://ubuntuforums.org/showthread.php?t=2214110&](http://ubuntuforums.org/showthread.php?t=2214110&)
is a guide for broadcom drivers. your dirver is the last in the list...and 14.04 is special case#1
the term linux-firmware does NOT mean linux-firmware-nonfree. Linux-frimware contains the native driver
linux-firmware-nonfree contains the b43,ssb.bcma and other goodies. but is NOT for your card .
the terminal commands i suggested, remove the b43 components only via the -rf (remove-force) and
can be eaisly restored with the same command without the -rf i.e. sudo modprobe b43. Anytime you are
unsure of a terminal command suggested by anyone, you can use the man pages to find out what it is,
google it. or simply post a question for explination on the forum.
hope this clears some things up for you.

---

### Post by varunendra on 2014-07-18
Since the 'bcma' driver has become a dependency of "brcmsmac" also, I have been seeing something that I personally consider a bug - the loading of "b43" with this particular card. So far, this is my understanding - the correct driver - brcmsmac loads 'bcma' as its dependency, then 'bcma' loads 'b43' as has been doing for years. Now loading of both brcmsmac and b43 creates a conflict situation.

Fortunately, the solution is very easy - just blacklist the "b43" and "ssb" drivers. A single command to do that is -
```
echo -e "blacklist b43\nblacklist ssb" | sudo tee -a /etc/modprobe.d/blacklist.conf
```
On next boot, the b43 driver won't load, only brcmsmac will. To confirm that -
```
lsmod | egrep 'b43|ssb|brcm'
```
..the output should only be "brcmsmac" and its supporting drivers. No b43 or ssb.

---

### Post by exsencon on 2014-07-18
I am very happy I am not the only guy having problems with wireless and Ubuntu.
I have a broadcom 4311 802.11b/g 14e4:4311(rev 01) card on my Dell Inspiron 1501 laptop and up to Ubuntu 10.10 I always got very good wireless and even didn't have much to do to get it. It was just there-period.Now with the later Ubuntu's there seems to be a problem. So I tried slackware, Centos and Mepis and even Sabayon and got a good wireless in no time.
Now, simple question: Why is it so difficult to get a wireless with Ubuntu now (and Mint for that matter)? They are supposed to be mainstream Linuxes. In the meantime I am still happy with Ubuntu 10.10 and...Slackware!

---

### Post by Hadaka on 2014-07-18
@exsencon here is a good guide to hep you with your wireless problem
[http://ubuntuforums.org/showthread.php?t=2214110](http://ubuntuforums.org/showthread.php?t=2214110)
your card is not the same as this thread, i would suggest you start a new
thread for your issue. your card is very easy to get working properly
and the above link should be all you need, if however you need help
let us know.
thanks.

---

### Post by Rob Sayer on 2014-07-20
> **varunendra said:**
> Since the 'bcma' driver has become a dependency of "brcmsmac" also, I have been seeing something that I personally consider a bug - the loading of "b43" with this particular card. So far, this is my understanding - the correct driver - brcmsmac loads 'bcma' as its dependency, then 'bcma' loads 'b43' as has been doing for years. Now loading of both brcmsmac and b43 creates a conflict situation.

Fortunately, the solution is very easy - just blacklist the "b43" and "ssb" drivers. A single command to do that is -
```
echo -e "blacklist b43\nblacklist ssb" | sudo tee -a /etc/modprobe.d/blacklist.conf
```
On next boot, the b43 driver won't load, only brcmsmac will. To confirm that -
```
lsmod | egrep 'b43|ssb|brcm'
```
..the output should only be "brcmsmac" and its supporting drivers. No b43 or ssb.

OK, I tried that just now ... it still works.  Can't tell if it's any better or not but it's at least as good.  Result of the 2nd command:

```
lsmod | egrep 'b43|ssb|brcm'brcmsmac              529837  0 
cordic                 12518  1 brcmsmac
brcmutil               15066  1 brcmsmac
mac80211              546051  1 brcmsmac
cfg80211              409394  2 brcmsmac,mac80211
bcma                   42043  2 brcmsmac
```

I'll definitely mark this <solved> after some more use if it doesn't bork ...

Thanks for the responses.

---

### Post by Rob Sayer on 2014-07-20
> **exsencon said:**
> I am very happy I am not the only guy having problems with wireless and Ubuntu.
I have a broadcom 4311 802.11b/g 14e4:4311(rev 01) card on my Dell Inspiron 1501 laptop and up to Ubuntu 10.10 I always got very good wireless and even didn't have much to do to get it. It was just there-period.Now with the later Ubuntu's there seems to be a problem. So I tried slackware, Centos and Mepis and even Sabayon and got a good wireless in no time.
Now, simple question: Why is it so difficult to get a wireless with Ubuntu now (and Mint for that matter)? They are supposed to be mainstream Linuxes. In the meantime I am still happy with Ubuntu 10.10 and...Slackware!

My current ubuntu kernel version in 14.04 is 3.13.0-32, which is based on the 3.13.4 mainline according to this ...

[http://people.canonical.com/~kernel/info/kernel-version-map.html](http://people.canonical.com/~kernel/info/kernel-version-map.html)

The slackware 14.0 kernel version according to this ...

[http://www.slackware.com/announce/14.0.php](http://www.slackware.com/announce/14.0.php)

... is 3.2.29.  That's pretty old.  I guess that's why it's often recommended for ancient hardware.

SO I guess the point I'm trying to make is: don't blame ubuntu because you can't be bothered to try to get proper support.

Of course, you can't get support for ubuntu 10.whatever anymore ...

---

### Post by Rob Sayer on 2014-07-20
OK ... I've been using this for a while now and used 2 different hotspots.  Sunday morning coffee.  It works fine.

This message:

```
Support for cores revisions 0x17 and 0x18 disabled by module param allhwsupport=0. Try b43.allhwsupport=1
```

appeared on boot before.  It's not there anymore.

I'm going to mark this <solved>.

Thanks all.

---

### Post by Hadaka on 2014-07-20
GREAT ! Glad you got it working.

---

