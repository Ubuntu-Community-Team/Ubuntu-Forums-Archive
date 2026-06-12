---
title: "WiFi Problem in Ubuntu 14.04 LTS"
date: 2015-01-27
forum: Networking &amp; Wireless
---

### Post by rohan7 on 2015-01-27
This is the wireless info of my Dell inspiron 15 laptop:

```


########## wireless info START ##########


Report from: 28 Jan 2015 23:35 IST +0530


Booted last: 28 Jan 2015 23:31 IST +0530


Script from: 20 Sep 2014 23:04 UTC +0000


##### release ###########################


Distributor ID: Ubuntu
Description: Ubuntu 14.04 LTS
Release: 14.04
Codename: trusty


##### kernel ############################


Linux 3.13.0-24-generic #46-Ubuntu SMP Thu Apr 10 19:11:08 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux


Parameters: ro, quiet, splash, vt.handoff=7


##### desktop ###########################


Ubuntu


##### lspci #############################


09:00.0 Ethernet controller [0200]: Marvell Technology Group Ltd. 88E8040 PCI-E Fast Ethernet Controller [11ab:4354] (rev 13)
Subsystem: Dell Device [1028:02aa]
Kernel driver in use: sky2


0c:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g LP-PHY [14e4:4315] (rev 01)
Subsystem: Dell Wireless 1397 WLAN Mini-Card [1028:000c]
Kernel driver in use: b43-pci-bridge


##### lsusb #############################


Bus 002 Device 004: ID 0fce:0173 Sony Ericsson Mobile Communications AB 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 002: ID 046d:c52f Logitech, Inc. Unifying Receiver
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 004: ID 0c45:63ee Microdia 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 004: ID 413c:8162 Dell Computer Corp. Integrated Touchpad [Synaptics]
Bus 003 Device 003: ID 413c:8161 Dell Computer Corp. Integrated Keyboard
Bus 003 Device 002: ID 0a5c:4500 Broadcom Corp. BCM2046B1 USB 2.0 Hub (part of BCM2046 Bluetooth)
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


##### PCMCIA card info ##################


##### rfkill ############################


##### lsmod #############################


dell_wmi 12761 0 
sparse_keymap 13948 1 dell_wmi
dell_laptop 18168 0 
dcdbas 14928 1 dell_laptop
b43 387371 0 
bcma 52096 1 b43
mac80211 626489 1 b43
cfg80211 484040 2 b43,mac80211
wmi 19177 1 dell_wmi
ssb 62379 1 b43


##### interfaces ########################


auto lo
iface lo inet loopback


##### ifconfig ##########################


eth0 Link encap:Ethernet HWaddr <MAC 'eth0' [IF]> 
UP BROADCAST MULTICAST MTU:1500 Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000 
RX bytes:0 (0.0 B) TX bytes:0 (0.0 B)
Interrupt:18 


##### iwconfig ##########################


eth0 no wireless extensions.


lo no wireless extensions.


##### route #############################


Kernel IP routing table
Destination Gateway Genmask Flags Metric Ref Use Iface


##### resolv.conf #######################


##### nm-tool ###########################


NetworkManager Tool


State: disconnected


- Device: eth0 -----------------------------------------------------------------
Type: Wired
Driver: sky2
State: unavailable
Default: no
HW Address: <MAC 'eth0' [IF]>


Capabilities:
Carrier Detect: yes


Wired Properties
Carrier: off


##### NetworkManager.state ##############


[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true


##### NetworkManager.conf ###############


[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq


[ifupdown]
managed=false


##### NetworkManager profiles ###########


##### iw reg get ########################


Region: Asia/Kolkata (based on set time zone)


country 00:
(2402 - 2472 @ 40), (3, 20)
(2457 - 2482 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
(2474 - 2494 @ 20), (3, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
(5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
(5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS


##### iwlist channels ###################


eth0 no frequency information.


lo no frequency information.


##### iwlist scan #######################


eth0 Interface doesn't support scanning.


lo Interface doesn't support scanning.


##### module infos ######################


[b43]
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
depends: bcma,ssb,mac80211,cfg80211
intree: Y
vermagic: 3.13.0-24-generic SMP mod_unload modversions 
signer: Magrathea: Glacier signing key
sig_key: 00:A5:A6:57:59:E:47:4B:C5:C4:31:20:88:0C:1B:94:A5:39:F4:31
sig_hashalgo: sha512
parm: bad_frames_preempt:enable(1) / disable(0) Bad Frames Preemption (int)
parm: fwpostfix postfix for the .fw files to load. (string)
parm: hwpctl:Enable hardware-side power control (default off) (int)
parm: nohwcrypt disable hardware encryption. (int)
parm: hwtkip:Enable hardware tkip. (int)
parm: qos:Enable QOS support (default on) (int)
parm: btcoex:Enable Bluetooth coexistence (default on) (int)
parm: verbose:Log message verbosity: 0=error, 1=warn, 2=info(default), 3=debug (int)
parm: pio:Use PIO accesses by default: 0=DMA, 1=PIO (int)
parm: allhwsupport:Enable support for all hardware (even it if overlaps with the brcmsmac driver) (int)


[bcma]
filename: /lib/modules/3.13.0-24-generic/kernel/drivers/bcma/bcma.ko
license: GPL
description: Broadcom's specific AMBA driver
srcversion: E41B811D88783DD5BC38565
depends: 
intree: Y
vermagic: 3.13.0-24-generic SMP mod_unload modversions 
signer: Magrathea: Glacier signing key
sig_key: 00:A5:A6:57:59:E:47:4B:C5:C4:31:20:88:0C:1B:94:A5:39:F4:31
sig_hashalgo: sha512


[mac80211]
filename: /lib/modules/3.13.0-24-generic/kernel/net/mac80211/mac80211.ko
license: GPL
description: IEEE 802.11 subsystem
srcversion: C0F95BBF832E05DEFD722F4
depends: cfg80211
intree: Y
vermagic: 3.13.0-24-generic SMP mod_unload modversions 
signer: Magrathea: Glacier signing key
sig_key: 00:A5:A6:57:59:E:47:4B:C5:C4:31:20:88:0C:1B:94:A5:39:F4:31
sig_hashalgo: sha512
parm: max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm: max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm: beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm: probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm: ieee80211_default_rc_algodefault rate control algorithm for mac80211 to use (charp)


[cfg80211]
filename: /lib/modules/3.13.0-24-generic/kernel/net/wireless/cfg80211.ko
description: wireless configuration support
license: GPL
author: Johannes Berg
srcversion: 8B3D642D1F2E6406EF33F74
depends: 
intree: Y
vermagic: 3.13.0-24-generic SMP mod_unload modversions 
signer: Magrathea: Glacier signing key
sig_key: 00:A5:A6:57:59:E:47:4B:C5:C4:31:20:88:0C:1B:94:A5:39:F4:31
sig_hashalgo: sha512
parm: ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm: cfg80211_disable_40mhz_24ghzdisable 40MHz support in the 2.4GHz band (bool)


[ssb]
filename: /lib/modules/3.13.0-24-generic/kernel/drivers/ssb/ssb.ko
license: GPL
description: Sonics Silicon Backplane driver
srcversion: 3DE188310F77C566C2E8CB3
depends: 
intree: Y
vermagic: 3.13.0-24-generic SMP mod_unload modversions 
signer: Magrathea: Glacier signing key
sig_key: 00:A5:A6:57:59:E:47:4B:C5:C4:31:20:88:0C:1B:94:A5:39:F4:31
sig_hashalgo: sha512


##### module parameters #################


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


[mac80211]
beacon_loss_count: 7
ieee80211_default_rc_algo: minstrel_ht
max_nullfunc_tries: 2
max_probe_tries: 5
probe_wait_ms: 500


[cfg80211]
cfg80211_disable_40mhz_24ghz: N
ieee80211_regdom: 00


##### /etc/modules ######################


lp
rtc


##### modprobe options ##################


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


[/etc/modprobe.d/blacklist-rare-network.conf]
alias net-pf-3 off
alias net-pf-6 off
alias net-pf-9 off
alias net-pf-11 off
alias net-pf-12 off
alias net-pf-19 off
alias net-pf-21 off
alias net-pf-36 off


[/etc/modprobe.d/iwlwifi.conf]
remove iwlwifi \
(/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
&& /sbin/modprobe -r mac80211


[/etc/modprobe.d/mlx4.conf]
softdep mlx4_core post: mlx4_en


##### rc.local ##########################


exit 0


##### pm-utils ##########################


##### udev rules ########################


[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x11ab:0x4354 (sky2)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"


##### dmesg #############################


[ 13.063577] b43-phy0: Broadcom 4312 WLAN found (core revision 15)
[ 13.128235] b43-phy0: Found PHY: Analog 6, Type 5 (LP), Revision 1
[ 13.239099] b43 ssb0:0: Direct firmware load failed with error -2
[ 13.239101] b43 ssb0:0: Falling back to user helper
[ 13.788988] b43 ssb0:0: Direct firmware load failed with error -2
[ 13.788990] b43 ssb0:0: Falling back to user helper
[ 13.850193] b43 ssb0:0: Direct firmware load failed with error -2
[ 13.850195] b43 ssb0:0: Falling back to user helper
[ 13.869016] b43 ssb0:0: Direct firmware load failed with error -2
[ 13.869018] b43 ssb0:0: Falling back to user helper
[ 13.870410] b43-phy0 ERROR: Firmware file "b43/ucode15.fw" not found
[ 13.870411] b43-phy0 ERROR: Firmware file "b43-open/ucode15.fw" not found
[ 13.870414] b43-phy0 ERROR: You must go to [http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware](http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware for this driver version. Please carefully read all instructions on this website.


########## wireless info END ############


```

---

### Post by howefield on 2015-01-27
Post moved to it's own thread in the "*Networking & Wireless*" forum and code tags corrected.

---

