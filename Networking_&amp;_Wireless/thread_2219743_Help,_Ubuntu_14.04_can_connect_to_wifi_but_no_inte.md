---
title: "Help, Ubuntu 14.04 can connect to wifi but no internet"
date: 2014-04-25
forum: Networking &amp; Wireless
---

### Post by Nguyen_Xuan_Loc on 2014-04-25
Hi everyone,

I'm new to Ubuntu. This is the first time i use Ubuntu. Therefore i'm really newbie with Ubuntu. I have succeed install Ubuntu 14.04 on my Asus K46CA a long with a Win 7. My problem is that i can connect to my wifi but there is no internet on Ubuntu. The wifi icon is on. I have tried connect the web through browser but cannot. I also try to ping google.com on terminal but can only get unresolved host. I also try to configure the DNS to Google DNS but still no internet. 

My Win 7 can connect to the internet through Wifi normally. Please help me.

Thanks

---

### Post by varunendra on 2014-04-27
Hi, Welcome to Ubuntu Forums!

Please follow the "Wireless Script" link in my signature, download and run the script as per instructions there, and post back the report it generates.

While posting the outputs, please use '**Code**' tags. It preserves the output's formatting and makes the post cleaner, compact and more readable. To see a quick 'HowTo' with screenshots, please follow the "Use Code Tags" link in my signature.

---

### Post by N_G_Sai_Prasanth on 2014-06-05
```


########## wireless info START ##########


##### release #####


Distributor ID:	Ubuntu
Description:	Ubuntu 14.04 LTS
Release:	14.04
Codename:	trusty


##### kernel #####


Linux ubuntu 3.13.0-27-generic #50-Ubuntu SMP Thu May 15 18:06:16 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux


##### lspci #####


03:00.0 Network controller [0280]: Broadcom Corporation BCM4313 802.11bgn Wireless Network Adapter [14e4:4727] (rev 01)
	Subsystem: Wistron NeWeb Corp. Device [185f:051a]
	Kernel driver in use: bcma-pci-bridge
05:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 06)
	Subsystem: Samsung Electronics Co Ltd Device [144d:c600]
	Kernel driver in use: r8169


##### lsusb #####


Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 2232:1008  
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 006: ID 18d1:4ee3 Google Inc. Nexus 4 (tether)
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


##### PCMCIA Card Info #####


##### rfkill #####


1: samsung-wlan: Wireless LAN
	Soft blocked: no
	Hard blocked: no
2: samsung-bluetooth: Bluetooth
	Soft blocked: yes
	Hard blocked: no
3: phy0: Wireless LAN
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


wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=27 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          


##### route #####


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.42.129  0.0.0.0         UG    0      0        0 usb0
192.168.42.0    0.0.0.0         255.255.255.0   U     1      0        0 usb0


##### resolv.conf #####


nameserver 127.0.1.1


##### nm-tool #####


NetworkManager Tool


State: connected (global)


- Device: usb0  [Wired connection 2] -------------------------------------------
  Type:              Wired
  Driver:            rndis_host
  State:             connected
  Default:           yes
  HW Address:        <MAC address removed>


  Capabilities:
    Carrier Detect:  yes


  Wired Properties
    Carrier:         on


  IPv4 Settings:
    Address:         192.168.42.117
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.42.129


    DNS:             192.168.42.129


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


- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            brcmsmac
  State:             disconnected
  Default:           no
  HW Address:        <MAC address removed>


  Capabilities:


  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes


  Wireless Access Points 
    DIVYA SAI MENS:  Infra, <MAC address removed>, Freq 2427 MHz, Rate 54 Mb/s, Strength 61 WPA WPA2


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
                    Channel:4
                    Frequency:2.427 GHz (Channel 4)
                    Quality=49/70  Signal level=-61 dBm  
                    Encryption key:on
                    ESSID:"DIVYA SAI MENS"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000046653cb60
                    Extra: Last beacon: 4ms ago
                    IE: Unknown: 000E444956594120534149204D454E53
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030104
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: 2D1A2C181EFF00000000000000000000000000000000000000000000
                    IE: Unknown: 3D1604000100000000000000000000000000000000000000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C332C181EFF00000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C3404000100000000000000000000000000000000000000
                    IE: Unknown: DD0600E04C020160
                    IE: Unknown: DD930050F204104A0001101044000102103B0001031047001063041253101920061228C0A0BBC92ED810210012442D4C696E6B20436F72706F726174696F6E1023000D442D4C696E6B20526F75746572102400084449522D3630304C1042000D32303037303431332D303030311054000800060050F2040001101100084449522D3630304C1008000226881049000600372A000120


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


##### lsmod #####


brcmsmac              563041  0 
cordic                 12574  1 brcmsmac
brcmutil               15618  1 brcmsmac
b43                   387371  0 
mac80211              626511  2 b43,brcmsmac
cfg80211              484040  3 b43,brcmsmac,mac80211
ssb                    62379  1 b43
bcma                   52096  3 b43,brcmsmac


##### modinfo #####


filename:       /lib/modules/3.13.0-27-generic/kernel/drivers/net/wireless/brcm80211/brcmsmac/brcmsmac.ko
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
vermagic:       3.13.0-27-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        <MAC address removed>:43:25:CC:F7:B9:5B:51:F6:C1:19:38:0E:B9:33
sig_hashalgo:   sha512


filename:       /lib/modules/3.13.0-27-generic/kernel/drivers/net/wireless/brcm80211/brcmutil/brcmutil.ko
license:        Dual BSD/GPL
description:    Broadcom 802.11n wireless LAN driver utilities.
author:         Broadcom Corporation
srcversion:     E81EE4CBB6A7A689150D93D
depends:        
intree:         Y
vermagic:       3.13.0-27-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        <MAC address removed>:43:25:CC:F7:B9:5B:51:F6:C1:19:38:0E:B9:33
sig_hashalgo:   sha512


filename:       /lib/modules/3.13.0-27-generic/kernel/drivers/net/wireless/b43/b43.ko
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
vermagic:       3.13.0-27-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        <MAC address removed>:43:25:CC:F7:B9:5B:51:F6:C1:19:38:0E:B9:33
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


filename:       /lib/modules/3.13.0-27-generic/kernel/drivers/ssb/ssb.ko
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
vermagic:       3.13.0-27-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        <MAC address removed>:43:25:CC:F7:B9:5B:51:F6:C1:19:38:0E:B9:33
sig_hashalgo:   sha512


filename:       /lib/modules/3.13.0-27-generic/kernel/drivers/bcma/bcma.ko
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
vermagic:       3.13.0-27-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        <MAC address removed>:43:25:CC:F7:B9:5B:51:F6:C1:19:38:0E:B9:33
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


# PCI device 0x14e4:0x4727 (brcmsmac)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"


##### dmesg #####


[   17.681998] bcma: bus0: Found chip with id 0x4313, rev 0x01 and package 0x08
[   17.682031] bcma: bus0: Core 0 found: ChipCommon (manuf 0x4BF, id 0x800, rev 0x24, class 0x0)
[   17.682055] bcma: bus0: Core 1 found: IEEE 802.11 (manuf 0x4BF, id 0x812, rev 0x18, class 0x0)
[   17.682099] bcma: bus0: Core 2 found: PCIe (manuf 0x4BF, id 0x820, rev 0x11, class 0x0)
[   17.694849] bcma: bus0: Bus registered
[   21.154983] psmouse serio1: elantech: assuming hardware version 3 (with firmware version 0x450f00)
[   21.843807] Support for cores revisions 0x17 and 0x18 disabled by module param allhwsupport=0. Try b43.allhwsupport=1
[   21.843834] b43: probe of bcma0:0 failed with error -524
[   22.192574] brcmsmac bcma0:0: mfg 4bf core 812 rev 24 class 0 irq 16
[   22.272162] ieee80211 phy0: registered radio enabled led device: brcmsmac-phy0:radio gpio: 243
[   22.826306] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: false (implement)
[   22.826423] brcmsmac bcma0:0: brcms_ops_config: change power-save mode: false (implement)
[   22.826683] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   22.827614] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   52.950499] wlan0: authenticate with <MAC address removed>
[   52.955667] wlan0: direct probe to <MAC address removed> (try 1/3)
[   53.157208] wlan0: direct probe to <MAC address removed> (try 2/3)
[   53.361359] wlan0: direct probe to <MAC address removed> (try 3/3)
[   53.565144] wlan0: authentication with <MAC address removed> timed out
[   61.415095] wlan0: authenticate with <MAC address removed>
[   61.417061] wlan0: direct probe to <MAC address removed> (try 1/3)
[   61.618169] wlan0: direct probe to <MAC address removed> (try 2/3)
[   61.822188] wlan0: direct probe to <MAC address removed> (try 3/3)
[   62.026195] wlan0: authentication with <MAC address removed> timed out
[   64.647295] wlan0: authenticate with <MAC address removed>
[   64.648536] wlan0: send auth to <MAC address removed> (try 1/3)
[   65.946671] wlan0: send auth to <MAC address removed> (try 2/3)
[   66.934788] wlan0: send auth to <MAC address removed> (try 3/3)
[   67.946936] wlan0: authentication with <MAC address removed> timed out
[   71.075978] wlan0: authenticate with <MAC address removed>
[   71.077275] wlan0: direct probe to <MAC address removed> (try 1/3)
[   71.077327] wlan0: direct probe to <MAC address removed> (try 2/3)
[   71.279273] wlan0: direct probe to <MAC address removed> (try 3/3)
[   71.483294] wlan0: authentication with <MAC address removed> timed out
[  947.069703] wlan0: authenticate with <MAC address removed>
[  947.070518] wlan0: send auth to <MAC address removed> (try 1/3)
[  947.099615] wlan0: authenticated
[  947.101165] wlan0: associate with <MAC address removed> (try 1/3)
[  947.412466] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=4)
[  947.413021] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: associated
[  947.413037] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: true (implement)
[  947.413068] wlan0: associated
[  947.413153] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  968.160501] brcmsmac bcma0:0: brcms_ops_bss_info_changed: arp filtering: 1 addresses (implement)
[ 1036.794511] brcmsmac bcma0:0: brcms_ops_bss_info_changed: arp filtering: 0 addresses (implement)
[ 1036.797790] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 1037.085493] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: disassociated
[ 1037.085523] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: false (implement)
[ 1041.591491] wlan0: authenticate with <MAC address removed>
[ 1041.592042] wlan0: send auth to <MAC address removed> (try 1/3)
[ 1041.663905] wlan0: authenticated
[ 1041.667433] wlan0: associate with <MAC address removed> (try 1/3)
[ 1042.396298] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=4)
[ 1042.398466] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: associated
[ 1042.398481] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: true (implement)
[ 1042.398510] wlan0: associated
[ 1088.272130] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 1089.273132] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: disassociated
[ 1089.273162] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: false (implement)
[ 1091.619324] wlan0: authenticate with <MAC address removed>
[ 1091.620908] wlan0: send auth to <MAC address removed> (try 1/3)
[ 1091.705093] wlan0: authenticated
[ 1091.706275] wlan0: associate with <MAC address removed> (try 1/3)
[ 1092.291251] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=4)
[ 1092.291790] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: associated
[ 1092.291805] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: true (implement)
[ 1092.291833] wlan0: associated
[ 1100.289858] brcmsmac bcma0:0: brcms_ops_bss_info_changed: arp filtering: 1 addresses (implement)
[ 1415.807383] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 1415.914954] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: disassociated
[ 1415.914983] brcmsmac bcma0:0: brcms_ops_bss_info_changed: arp filtering: 1 addresses (implement)
[ 1415.914993] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: false (implement)


########## wireless info END ############
```

---

### Post by varunendra on 2014-06-05
Please open a terminal (Ctrl-Alt-T) and run the following command (you may copy-paste it to avoid errors) -
```
echo -e "blacklist b43\nblacklist ssb" | sudo tee -a /etc/modprobe.d/blacklist.conf
```
Then reboot and check the output of -
```
lsmod | egrep 'b43|ssb|brcm'
```
You shouldn't see "b43" or "ssb" in the output, only brcmsmac and its supporting drivers. If so, does the wifi work now?

---

### Post by pbarya on 2015-05-12
For the time being you can do this.
Just get the DNS address from some device which is connected to internet. 
Now edit /etc/resolve.conf 
nameserver <your dns>

But remember you have to change this as soon as you go to some other network.

---

