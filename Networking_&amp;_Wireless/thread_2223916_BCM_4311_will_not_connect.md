---
title: "BCM 4311 will not connect"
date: 2014-05-13
forum: Networking &amp; Wireless
---

### Post by Shoalster on 2014-05-13
```
########## wireless info START ##########

##### release #####

Distributor ID: Ubuntu
Description: Ubuntu 14.04 LTS
Release: 14.04
Codename: trusty

##### kernel #####

Linux doug-MM061 3.13.0-24-generic #46-Ubuntu SMP Thu Apr 10 19:08:14 UTC 2014 i686 i686 i686 GNU/Linux

##### lspci #####

03:00.0 Ethernet controller [0200]: Broadcom Corporation BCM4401-B0 100Base-TX [14e4:170c] (rev 02)
 Subsystem: Dell Inspiron 6400 [1028:01af]
 Kernel driver in use: b44

0b:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311] (rev 01)
 Subsystem: Dell Wireless 1390 WLAN Mini-Card [1028:0007]
 Kernel driver in use: b43-pci-bridge

##### lsusb #####

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

##### PCMCIA Card Info #####

##### rfkill #####

0: phy0: Wireless LAN
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

wlan0 IEEE 802.11bg ESSIDff/any 
 Mode:Managed Access Point: Not-Associated Tx-Power=20 dBm 
 Retry long limit:7 RTS thrff Fragment thrff
 Power Managementff
 

##### route #####

Kernel IP routing table
Destination Gateway Genmask Flags Metric Ref Use Iface
0.0.0.0 192.168.1.1 0.0.0.0 UG 0 0 0 eth0
192.168.1.0 0.0.0.0 255.255.255.0 U 0 0 0 eth0

##### resolv.conf #####

nameserver 192.168.1.1
nameserver 127.0.1.1
search zyxel.com

##### nm-tool #####

NetworkManager Tool

State: connected (global)

- Device: eth0 [Wired connection 1] -------------------------------------------
 Type: Wired
 Driver: b44
 State: connected
 Default: yes
 HW Address: <MAC address removed>

 Capabilities:
 Carrier Detect: yes
 Speed: 100 Mb/s

 Wired Properties
 Carrier: on

 IPv4 Settings:
 Address: 192.168.1.36
 Prefix: 24 (255.255.255.0)
 Gateway: 192.168.1.1

 DNS: 192.168.1.1

- Device: wlan0 ----------------------------------------------------------------
 Type: 802.11 WiFi
 Driver: b43
 State: disconnected
 Default: no
 HW Address: <MAC address removed>

 Capabilities:

 Wireless Properties
 WEP Encryption: yes
 WPA Encryption: yes
 WPA2 Encryption: yes

 Wireless Access Points 
 ZyXEL: Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 100

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

wlan0 Scan completed :
 Cell 01 - Address: <MAC address removed>
 Channel:1
 Frequency:2.412 GHz (Channel 1)
 Quality=70/70 Signal level=-12 dBm 
 Encryption keyff
 ESSID:"ZyXEL"
 Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
 18 Mb/s; 36 Mb/s; 54 Mb/s
 Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
 Mode:Master
 Extra:tsf=00000023a12eb335
 Extra: Last beacon: 44ms ago
 IE: Unknown: 00055A7958454C
 IE: Unknown: 010882848B961224486C
 IE: Unknown: 030101
 IE: Unknown: 2A0104
 IE: Unknown: 32040C183060
 IE: Unknown: 2D1AEE1117FFFF0000010000000000000000000000000C0000000000
 IE: Unknown: 3D1601050600000000000000000000000000000000000000
 IE: Unknown: 3E0100
 IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
 IE: Unknown: 0B05020000127A
 IE: Unknown: 7F0101
 IE: Unknown: DD07000C4307000000
 IE: Unknown: 0706465220010D10
 IE: Unknown: DD1E00904C33EE1117FFFF0000010000000000000000000000000C0000000000
 IE: Unknown: DD1A00904C3401050600000000000000000000000000000000000000
 IE: Unknown: DD8C0050F204104A0001101044000101103B000103104700102880288028801880A8800023F830FE481021001A5A7958454C20436F6D6D756E69636174696F6E7320436F72702E102300084E42472D3431394E102400084E42472D3431394E1042000831323334353637381054000800060050F2040001101100084E42472D3431394E100800020084103C000101

##### iwlist channel #####

wlan0 14 channels in total; available frequencies :
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

##### lsmod #####

b43 356470 0 
bcma 42043 1 b43
mac80211 545990 1 b43
cfg80211 409394 2 b43,mac80211
ssb_hcd 12749 0 
ssb 51854 3 b43,b44,ssb_hcd

##### modinfo #####

filename: /lib/modules/3.13.0-24-generic/kernel/drivers/net/wireless/b43/b43.ko
firmware: b43/ucode9.fw
firmware: b43/ucode5.fw
firmware: b43/ucode16_mimo.fw
firmware: b43/ucode15.fw
firmware: b43/ucode14.fw
firmware: b43/ucode13.fw
firmware: b43/ucode11.fw
license: GPL
author: Rafa&#322; Mi&#322;ecki
author: Gábor Stefanik
author: Michael Buesch
author: Stefano Brivio
author: Martin Langer
description: Broadcom B43 wireless driver
srcversion: BED87D210887FFC71A4BDE0
alias: bcma:m04BFid0812rev1Dcl*
alias: bcma:m04BFid0812rev18cl*
alias: bcma:m04BFid0812rev17cl*
alias: bcma:m04BFid0812rev11cl*
alias: ssb:v4243id0812rev10*
alias: ssb:v4243id0812rev0F*
alias: ssb:v4243id0812rev0D*
alias: ssb:v4243id0812rev0C*
alias: ssb:v4243id0812rev0B*
alias: ssb:v4243id0812rev0A*
alias: ssb:v4243id0812rev09*
alias: ssb:v4243id0812rev07*
alias: ssb:v4243id0812rev06*
alias: ssb:v4243id0812rev05*
depends: bcma,ssb,mac80211,cfg80211
intree: Y
vermagic: 3.13.0-24-generic SMP mod_unload modversions 686 
signer: Magrathea: Glacier signing key
sig_key: <MAC address removed>:96C:92:B0:1D:75:9D:3E:85:62:EA:32:A1:C7
sig_hashalgo: sha512
parm: bad_frames_preempt:enable(1) / disable(0) Bad Frames Preemption (int)
parm: fwpostfixostfix for the .fw files to load. (string)
parm: hwpctl:Enable hardware-side power control (default off) (int)
parm: nohwcryptisable hardware encryption. (int)
parm: hwtkip:Enable hardware tkip. (int)
parm: qos:Enable QOS support (default on) (int)
parm: btcoex:Enable Bluetooth coexistence (default on) (int)
parm: verbose:Log message verbosity: 0=error, 1=warn, 2=info(default), 3=debug (int)
parm: pio:Use PIO accesses by default: 0=DMA, 1=PIO (int)
parm: allhwsupport:Enable support for all hardware (even it if overlaps with the brcmsmac driver) (int)

filename: /lib/modules/3.13.0-24-generic/kernel/drivers/bcma/bcma.ko
license: GPL
description: Broadcom's specific AMBA driver
srcversion: E41B811D88783DD5BC38565
alias: pci:v000014E4d00004727sv*sd*bc*sc*i*
alias: pci:v000014E4d00004365sv*sd*bc*sc*i*
alias: pci:v000014E4d00004359sv*sd*bc*sc*i*
alias: pci:v000014E4d00004358sv*sd*bc*sc*i*
alias: pci:v000014E4d00004357sv*sd*bc*sc*i*
alias: pci:v000014E4d00004353sv*sd*bc*sc*i*
alias: pci:v000014E4d00004331sv*sd*bc*sc*i*
alias: pci:v000014E4d0000A8D8sv*sd*bc*sc*i*
alias: pci:v000014E4d00004313sv*sd*bc*sc*i*
alias: pci:v000014E4d00000576sv*sd*bc*sc*i*
depends: 
intree: Y
vermagic: 3.13.0-24-generic SMP mod_unload modversions 686 
signer: Magrathea: Glacier signing key
sig_key: <MAC address removed>:96C:92:B0:1D:75:9D:3E:85:62:EA:32:A1:C7
sig_hashalgo: sha512

filename: /lib/modules/3.13.0-24-generic/kernel/drivers/usb/host/ssb-hcd.ko
license: GPL
description: Common USB driver for SSB Bus
author: Hauke Mehrtens
srcversion: 2A4C0EB5791EE9A11133FCB
alias: ssb:v4243id0819rev*
alias: ssb:v4243id0817rev*
alias: ssb:v4243id0808rev*
depends: ssb
intree: Y
vermagic: 3.13.0-24-generic SMP mod_unload modversions 686 
signer: Magrathea: Glacier signing key
sig_key: <MAC address removed>:96C:92:B0:1D:75:9D:3E:85:62:EA:32:A1:C7
sig_hashalgo: sha512

filename: /lib/modules/3.13.0-24-generic/kernel/drivers/ssb/ssb.ko
license: GPL
description: Sonics Silicon Backplane driver
srcversion: 3DE188310F77C566C2E8CB3
alias: pci:v000014E4d00004350sv*sd*bc*sc*i*
alias: pci:v000014E4d0000432Csv*sd*bc*sc*i*
alias: pci:v000014E4d0000432Bsv*sd*bc*sc*i*
alias: pci:v000014E4d00004329sv*sd*bc*sc*i*
alias: pci:v000014E4d00004328sv*sd*bc*sc*i*
alias: pci:v000014E4d00004325sv*sd*bc*sc*i*
alias: pci:v000014E4d00004324sv*sd*bc*sc*i*
alias: pci:v000014E4d0000A8D6sv*sd*bc*sc*i*
alias: pci:v000014E4d00004322sv*sd*bc*sc*i*
alias: pci:v000014E4d00004321sv*sd*bc*sc*i*
alias: pci:v000014E4d00004320sv*sd*bc*sc*i*
alias: pci:v000014E4d00004319sv*sd*bc*sc*i*
alias: pci:v000014A4d00004318sv*sd*bc*sc*i*
alias: pci:v000014E4d00004318sv*sd*bc*sc*i*
alias: pci:v000014E4d00004315sv*sd*bc*sc*i*
alias: pci:v000014E4d00004312sv*sd*bc*sc*i*
alias: pci:v000014E4d00004311sv*sd*bc*sc*i*
alias: pci:v000014E4d00004307sv*sd*bc*sc*i*
alias: pci:v000014E4d00004306sv*sd*bc*sc*i*
alias: pci:v000014E4d00004301sv*sd*bc*sc*i*
depends: 
intree: Y
vermagic: 3.13.0-24-generic SMP mod_unload modversions 686 
signer: Magrathea: Glacier signing key
sig_key: <MAC address removed>:96C:92:B0:1D:75:9D:3E:85:62:EA:32:A1:C7
sig_hashalgo: sha512

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

# PCI device 0x14e4:0x170c (b44)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

# PCI device 0x14e4:0x4311 (b43)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

##### dmesg #####

[ 1.805593] ssb: Found chip with id 0x4311, rev 0x01 and package 0x00
[ 1.805618] ssb: Core 0 found: ChipCommon (cc 0x800, rev 0x11, vendor 0x4243)
[ 1.805628] ssb: Core 1 found: IEEE 802.11 (cc 0x812, rev 0x0A, vendor 0x4243)
[ 1.805648] ssb: Core 2 found: USB 1.1 Host (cc 0x817, rev 0x03, vendor 0x4243)
[ 1.805660] ssb: Core 3 found: PCI-E (cc 0x820, rev 0x01, vendor 0x4243)
[ 1.872384] ssb: Sonics Silicon Backplane found on PCI device 0000:0b:00.0
[ 1.932099] ssb: Found chip with id 0x4401, rev 0x02 and package 0x00
[ 1.932119] ssb: Core 0 found: Fast Ethernet (cc 0x806, rev 0x07, vendor 0x4243)
[ 1.932127] ssb: Core 1 found: V90 (cc 0x807, rev 0x03, vendor 0x4243)
[ 1.932145] ssb: Core 2 found: PCI (cc 0x804, rev 0x0A, vendor 0x4243)
[ 1.972271] ssb: Sonics Silicon Backplane found on PCI device 0000:03:00.0
[ 1.992939] b44 ssb1:0 eth0: Broadcom 44xx/47xx 10/100 PCI ethernet driver <MAC address removed>
[ 17.469201] b43-phy0: Broadcom 4311 WLAN found (core revision 10)
[ 17.512069] b43-phy0: Found PHY: Analog 4, Type 2 (G), Revision 8
[ 30.120102] b43-phy0: Loading firmware version 666.2 (2011-02-23 01:15:07)
[ 30.204446] b43-phy0: Radio hardware status changed to DISABLED
[ 30.212056] b43-phy0: Radio turned on by software
[ 30.212064] b43-phy0: The hardware RF-kill button still turns the radio physically off. Press the button to turn it on.
[ 30.212596] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 30.328641] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 33.816223] b44 ssb1:0 eth0: Link is up at 100 Mbps, full duplex
[ 33.816232] b44 ssb1:0 eth0: Flow control is off for TX and off for RX
[ 90.852110] b43-phy0: Radio hardware status changed to ENABLED
[ 91.008128] b43-phy0: Loading firmware version 666.2 (2011-02-23 01:15:07)
[ 91.081175] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 91.460113] b43-phy0: Loading firmware version 666.2 (2011-02-23 01:15:07)
[ 91.533143] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 137.816167] b44 ssb1:0 eth0: Link is down
[ 164.020698] wlan0: authenticate with <MAC address removed>
[ 164.032607] wlan0: send auth to <MAC address removed> (try 1/3)
[ 164.034368] wlan0: authenticated
[ 164.036127] wlan0: associate with <MAC address removed> (try 1/3)
[ 164.037606] wlan0: RX AssocResp from <MAC address removed> (capab=0x401 status=18 aid=4752)
[ 164.037613] wlan0: <MAC address removed> denied association (code=18)
[ 164.061895] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 165.260933] wlan0: authenticate with <MAC address removed>
[ 165.272544] wlan0: send auth to <MAC address removed> (try 1/3)
[ 165.273733] wlan0: authenticated
[ 165.276103] wlan0: associate with <MAC address removed> (try 1/3)
[ 165.277744] wlan0: RX AssocResp from <MAC address removed> (capab=0x401 status=18 aid=4752)
[ 165.277750] wlan0: <MAC address removed> denied association (code=18)
[ 165.300472] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 166.896896] wlan0: authenticate with <MAC address removed>
[ 166.908594] wlan0: send auth to <MAC address removed> (try 1/3)
[ 167.112104] wlan0: send auth to <MAC address removed> (try 2/3)
[ 167.113310] wlan0: authenticated
[ 167.116090] wlan0: associate with <MAC address removed> (try 1/3)
[ 167.117788] wlan0: RX AssocResp from <MAC address removed> (capab=0x401 status=18 aid=4752)
[ 167.117796] wlan0: <MAC address removed> denied association (code=18)
[ 167.134508] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 169.232831] wlan0: authenticate with <MAC address removed>
[ 169.244574] wlan0: send auth to <MAC address removed> (try 1/3)
[ 169.246330] wlan0: authenticated
[ 169.248124] wlan0: associate with <MAC address removed> (try 1/3)
[ 169.249626] wlan0: RX AssocResp from <MAC address removed> (capab=0x401 status=18 aid=4752)
[ 169.249633] wlan0: <MAC address removed> denied association (code=18)
[ 169.294778] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 181.492876] wlan0: authenticate with <MAC address removed>
[ 181.504603] wlan0: send auth to <MAC address removed> (try 1/3)
[ 181.506419] wlan0: authenticated
[ 181.508114] wlan0: associate with <MAC address removed> (try 1/3)
[ 181.509903] wlan0: RX AssocResp from <MAC address removed> (capab=0x401 status=18 aid=4752)
[ 181.509911] wlan0: <MAC address removed> denied association (code=18)
[ 181.584506] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 211.516893] wlan0: authenticate with <MAC address removed>
[ 211.528566] wlan0: send auth to <MAC address removed> (try 1/3)
[ 211.529958] wlan0: authenticated
[ 211.532100] wlan0: associate with <MAC address removed> (try 1/3)
[ 211.533542] wlan0: RX AssocResp from <MAC address removed> (capab=0x401 status=18 aid=4752)
[ 211.533551] wlan0: <MAC address removed> denied association (code=18)
[ 211.553502] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 222.656858] wlan0: authenticate with <MAC address removed>
[ 222.676585] wlan0: send auth to <MAC address removed> (try 1/3)
[ 222.678578] wlan0: authenticated
[ 222.680115] wlan0: associate with <MAC address removed> (try 1/3)
[ 222.681626] wlan0: RX AssocResp from <MAC address removed> (capab=0x401 status=18 aid=4752)
[ 222.681633] wlan0: <MAC address removed> denied association (code=18)
[ 222.699360] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 394.957189] wlan0: authenticate with <MAC address removed>
[ 394.968556] wlan0: send auth to <MAC address removed> (try 1/3)
[ 394.969989] wlan0: authenticated
[ 394.972123] wlan0: associate with <MAC address removed> (try 1/3)
[ 394.973707] wlan0: RX AssocResp from <MAC address removed> (capab=0x401 status=18 aid=4752)
[ 394.973714] wlan0: <MAC address removed> denied association (code=18)
[ 394.990578] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 406.088851] wlan0: authenticate with <MAC address removed>
[ 406.108584] wlan0: send auth to <MAC address removed> (try 1/3)
[ 406.110256] wlan0: authenticated
[ 406.112084] wlan0: associate with <MAC address removed> (try 1/3)
[ 406.113828] wlan0: RX AssocResp from <MAC address removed> (capab=0x401 status=18 aid=4752)
[ 406.113836] wlan0: <MAC address removed> denied association (code=18)
[ 406.144495] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 446.016090] b43-phy0: Radio hardware status changed to DISABLED
[ 451.028129] b43-phy0: Radio hardware status changed to ENABLED
[ 451.192145] b43-phy0: Loading firmware version 666.2 (2011-02-23 01:15:07)
[ 451.272964] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 511.620828] wlan0: authenticate with <MAC address removed>
[ 511.640601] wlan0: send auth to <MAC address removed> (try 1/3)
[ 511.642339] wlan0: authenticated
[ 511.644121] wlan0: associate with <MAC address removed> (try 1/3)
[ 511.645745] wlan0: RX AssocResp from <MAC address removed> (capab=0x401 status=18 aid=7056)
[ 511.645753] wlan0: <MAC address removed> denied association (code=18)
[ 511.690271] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 512.885213] wlan0: authenticate with <MAC address removed>
[ 512.904598] wlan0: send auth to <MAC address removed> (try 1/3)
[ 512.907457] wlan0: authenticated
[ 512.908079] wlan0: associate with <MAC address removed> (try 1/3)
[ 512.909579] wlan0: RX AssocResp from <MAC address removed> (capab=0x401 status=18 aid=7056)
[ 512.909586] wlan0: <MAC address removed> denied association (code=18)
[ 512.927048] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 514.524809] wlan0: authenticate with <MAC address removed>
[ 514.544601] wlan0: send auth to <MAC address removed> (try 1/3)
[ 514.546543] wlan0: authenticated
[ 514.548117] wlan0: associate with <MAC address removed> (try 1/3)
[ 514.549891] wlan0: RX AssocResp from <MAC address removed> (capab=0x401 status=18 aid=7056)
[ 514.549898] wlan0: <MAC address removed> denied association (code=18)
[ 514.576474] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 516.688943] wlan0: authenticate with <MAC address removed>
[ 516.700556] wlan0: send auth to <MAC address removed> (try 1/3)
[ 516.701693] wlan0: authenticated
[ 516.704117] wlan0: associate with <MAC address removed> (try 1/3)
[ 516.705923] wlan0: RX AssocResp from <MAC address removed> (capab=0x401 status=18 aid=7056)
[ 516.705933] wlan0: <MAC address removed> denied association (code=18)
[ 516.721358] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 528.928982] wlan0: authenticate with <MAC address removed>
[ 528.940581] wlan0: send auth to <MAC address removed> (try 1/3)
[ 528.942396] wlan0: authenticated
[ 528.944117] wlan0: associate with <MAC address removed> (try 1/3)
[ 528.945652] wlan0: RX AssocResp from <MAC address removed> (capab=0x401 status=18 aid=7056)
[ 528.945661] wlan0: <MAC address removed> denied association (code=18)
[ 528.963574] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 997.401094] wlan0: authenticate with <MAC address removed>
[ 997.412586] wlan0: send auth to <MAC address removed> (try 1/3)
[ 997.414317] wlan0: authenticated
[ 997.416129] wlan0: associate with <MAC address removed> (try 1/3)
[ 997.417729] wlan0: RX AssocResp from <MAC address removed> (capab=0x401 status=18 aid=7056)
[ 997.417736] wlan0: <MAC address removed> denied association (code=18)
[ 997.434618] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 1008.536878] wlan0: authenticate with <MAC address removed>
[ 1008.556608] wlan0: send auth to <MAC address removed> (try 1/3)
[ 1008.559400] wlan0: authenticated
[ 1008.560083] wlan0: associate with <MAC address removed> (try 1/3)
[ 1008.561766] wlan0: RX AssocResp from <MAC address removed> (capab=0x401 status=18 aid=7056)
[ 1008.561774] wlan0: <MAC address removed> denied association (code=18)
[ 1008.578883] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 1035.000249] b44 ssb1:0 eth0: Link is up at 100 Mbps, full duplex
[ 1035.000260] b44 ssb1:0 eth0: Flow control is off for TX and off for RX
[ 1048.792826] wlan0: authenticate with <MAC address removed>
[ 1048.820445] wlan0: send auth to <MAC address removed> (try 1/3)
[ 1048.821539] wlan0: authenticated
[ 1048.824087] wlan0: associate with <MAC address removed> (try 1/3)
[ 1048.825634] wlan0: RX AssocResp from <MAC address removed> (capab=0x401 status=18 aid=7056)
[ 1048.825643] wlan0: <MAC address removed> denied association (code=18)
[ 1048.864507] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 1059.968823] wlan0: authenticate with <MAC address removed>
[ 1059.980569] wlan0: send auth to <MAC address removed> (try 1/3)
[ 1059.982279] wlan0: authenticated
[ 1059.984201] wlan0: associate with <MAC address removed> (try 1/3)
[ 1059.985623] wlan0: RX AssocResp from <MAC address removed> (capab=0x401 status=18 aid=7056)
[ 1059.985633] wlan0: <MAC address removed> denied association (code=18)
[ 1060.002847] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 1108.652872] wlan0: authenticate with <MAC address removed>
[ 1108.664558] wlan0: send auth to <MAC address removed> (try 1/3)
[ 1108.666364] wlan0: authenticated
[ 1108.668082] wlan0: associate with <MAC address removed> (try 1/3)
[ 1108.669668] wlan0: RX AssocResp from <MAC address removed> (capab=0x401 status=18 aid=7056)
[ 1108.669676] wlan0: <MAC address removed> denied association (code=18)
[ 1108.688576] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 1119.800865] wlan0: authenticate with <MAC address removed>
[ 1119.820581] wlan0: send auth to <MAC address removed> (try 1/3)
[ 1119.822320] wlan0: authenticated
[ 1119.824160] wlan0: associate with <MAC address removed> (try 1/3)
[ 1119.825981] wlan0: RX AssocResp from <MAC address removed> (capab=0x401 status=18 aid=7056)
[ 1119.825989] wlan0: <MAC address removed> denied association (code=18)
[ 1119.848388] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 1172.000143] b44 ssb1:0 eth0: Link is down
[ 1180.868593] wlan0: authenticate with <MAC address removed>
[ 1180.888598] wlan0: send auth to <MAC address removed> (try 1/3)
[ 1180.889985] wlan0: authenticated
[ 1180.892103] wlan0: associate with <MAC address removed> (try 1/3)
[ 1180.893751] wlan0: RX AssocResp from <MAC address removed> (capab=0x401 status=18 aid=4708)
[ 1180.893759] wlan0: <MAC address removed> denied association (code=18)
[ 1180.917273] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 1192.024836] wlan0: authenticate with <MAC address removed>
[ 1192.044587] wlan0: send auth to <MAC address removed> (try 1/3)
[ 1192.046515] wlan0: authenticated
[ 1192.048123] wlan0: associate with <MAC address removed> (try 1/3)
[ 1192.049790] wlan0: RX AssocResp from <MAC address removed> (capab=0x401 status=18 aid=7056)
[ 1192.049797] wlan0: <MAC address removed> denied association (code=18)
[ 1192.096498] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 1312.669057] wlan0: authenticate with <MAC address removed>
[ 1312.688594] wlan0: send auth to <MAC address removed> (try 1/3)
[ 1312.690187] wlan0: authenticated
[ 1312.692080] wlan0: associate with <MAC address removed> (try 1/3)
[ 1312.693702] wlan0: RX AssocResp from <MAC address removed> (capab=0x401 status=18 aid=7056)
[ 1312.693709] wlan0: <MAC address removed> denied association (code=18)
[ 1312.712469] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 1323.808899] wlan0: authenticate with <MAC address removed>
[ 1323.820569] wlan0: send auth to <MAC address removed> (try 1/3)
[ 1323.822089] wlan0: authenticated
[ 1323.824100] wlan0: associate with <MAC address removed> (try 1/3)
[ 1323.825698] wlan0: RX AssocResp from <MAC address removed> (capab=0x401 status=18 aid=7056)
[ 1323.825706] wlan0: <MAC address removed> denied association (code=18)
[ 1323.842469] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 1324.000247] b44 ssb1:0 eth0: Link is up at 100 Mbps, full duplex
[ 1324.000259] b44 ssb1:0 eth0: Flow control is off for TX and off for RX
[ 3782.616880] wlan0: authenticate with <MAC address removed>
[ 3782.617145] wlan0: send auth to <MAC address removed> (try 1/3)
[ 3782.618317] wlan0: authenticated
[ 3782.620060] wlan0: associate with <MAC address removed> (try 1/3)
[ 3782.621447] wlan0: RX AssocResp from <MAC address removed> (capab=0x401 status=18 aid=7056)
[ 3782.621452] wlan0: <MAC address removed> denied association (code=18)
[ 3782.689149] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 3793.792835] wlan0: authenticate with <MAC address removed>
[ 3793.812584] wlan0: send auth to <MAC address removed> (try 1/3)
[ 3793.814490] wlan0: authenticated
[ 3793.816115] wlan0: associate with <MAC address removed> (try 1/3)
[ 3793.817818] wlan0: RX AssocResp from <MAC address removed> (capab=0x401 status=18 aid=7056)
[ 3793.817826] wlan0: <MAC address removed> denied association (code=18)
[ 3793.835385] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 4391.109086] wlan0: authenticate with <MAC address removed>
[ 4391.128470] wlan0: send auth to <MAC address removed> (try 1/3)
[ 4391.129811] wlan0: authenticated
[ 4391.132035] wlan0: associate with <MAC address removed> (try 1/3)
[ 4391.133724] wlan0: RX AssocResp from <MAC address removed> (capab=0x401 status=18 aid=7056)
[ 4391.133731] wlan0: <MAC address removed> denied association (code=18)
[ 4391.145633] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 4402.248813] wlan0: authenticate with <MAC address removed>
[ 4402.268607] wlan0: send auth to <MAC address removed> (try 1/3)
[ 4402.270451] wlan0: authenticated
[ 4402.272130] wlan0: associate with <MAC address removed> (try 1/3)
[ 4402.273860] wlan0: RX AssocResp from <MAC address removed> (capab=0x401 status=18 aid=7056)
[ 4402.273866] wlan0: <MAC address removed> denied association (code=18)
[ 4402.296820] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)

########## wireless info END ############ 
```

---

### Post by Shoalster on 2014-05-14
.

---

### Post by praseodym on 2014-05-14
Please try to load the driver one after another at boot-up:
```

echo -e "blacklist b43\nblacklist b44\nblacklist ssb\nblacklist bcma" | sudo tee -a /etc/modprobe.d/blacklist-broadcom.conf 
sudo sed -i "s/exit 0/# starting order for the broadcom drivers/g" /etc/rc.local
echo -e "modprobe ssb\nmodprobe bcma\nmodprobe b43\nmodprobe b44\nexit 0" | sudo tee -a /etc/rc.local
```
Reboot and check:
```

lsmod
cat /etc/rc.local
dmesg | egrep 'b43|b44'
nm-tool
```

---

### Post by wildmanne39 on 2014-05-14
Please use code tags - if you are using New Reply button - highlight text and use the # button in the text box header. 
 
If using Quick Reply then [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.

---

### Post by Shoalster on 2014-05-14
```
Not sure what you meant by load the driver one after another but I ran  the commands and rebooted.  Still showing driver disconnected.

- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            b43
  State:             disconnected
  Default:           no
  HW Address:        00:16:CE:1F:1F:6F 				
```

---

### Post by Shoalster on 2014-05-16
I guess we're done here.   I'll mark the problem UNRESOLVED.
  
     Thanks

---

### Post by praseodym on 2014-05-17
Why don&#8217;t you show the outputs?

---

