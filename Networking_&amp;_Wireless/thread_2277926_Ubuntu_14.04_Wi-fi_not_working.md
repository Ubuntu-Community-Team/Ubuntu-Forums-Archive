---
title: "Ubuntu 14.04 Wi-fi not working"
date: 2015-05-12
forum: Networking &amp; Wireless
---

### Post by Vivek_Iyer on 2015-05-12
Hi all,

My Wi-Fi is not working on a fresh install of Ubuntu 14.04. Need help please. I believe the problem is related to the broadcom 4311 driver. The output for the wireless script is below.

I have tried the basic steps of removing the bcm kernel source and also installing the nonfree firmware. Additional drivers have the broadcom driver disabled. I am using a wired connection and that is working fine. Rfkill is returning no responses and the kernel in use with the Wi-Fi card is bcm-pci-bridge, which seems to be the correct one per other forums.

Request your help please.

Regards,

Vivek


```
########## wireless info START ##########

Report from: 12 May 2015 20:16 IST +0530

Booted last: 12 May 2015 20:11 IST +0530

Script from: 30 Apr 2015 17:23 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.2 LTS
Release:    14.04
Codename:    trusty

##### kernel ############################

Linux 3.16.0-30-generic #40~14.04.1-Ubuntu SMP Thu Jan 15 17:45:15 UTC 2015 i686 i686 i686 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Ubuntu

##### lspci #############################

03:00.0 Ethernet controller [0200]: Broadcom Corporation BCM4401-B0 100Base-TX [14e4:170c] (rev 02)
    Subsystem: Dell Inspiron 6400 [1028:01af]
    Kernel driver in use: b44

0b:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311] (rev 01)
    Subsystem: Dell Wireless 1390 WLAN Mini-Card [1028:0007]
    Kernel driver in use: b43-pci-bridge

##### lsusb #############################

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

##### PCMCIA card info ##################

##### rfkill ############################

##### lsmod #############################

dell_wmi               12665  0 
sparse_keymap          13708  1 dell_wmi
dell_laptop            17808  0 
dcdbas                 14448  1 dell_laptop
b43                   369555  0 
bcma                   46331  1 b43
mac80211              559049  1 b43
cfg80211              418811  2 b43,mac80211
ssb_hcd                12764  0 
wmi                    18689  1 dell_wmi
ssb                    51835  3 b43,b44,ssb_hcd

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

eth0      Link encap:Ethernet  HWaddr <MAC 'eth0' [IF]>  
          inet addr:192.168.1.140  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::215:c5ff:fe19:33dd/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1188 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1119 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:756966 (756.9 KB)  TX bytes:125900 (125.9 KB)
          Interrupt:17 

##### iwconfig ##########################

lo        no wireless extensions.

eth0      no wireless extensions.

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 eth0
192.168.1.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0

##### resolv.conf #######################

nameserver 127.0.1.1
search Gateway

##### NetworkManager info ###############

NetworkManager Tool

State: connected (global)

- Device: eth0  [Wired connection 1] -------------------------------------------
  Type:              Wired
  Driver:            b44
  State:             connected
  Default:           yes
  HW Address:        <MAC 'eth0' [IF]>

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.1.140
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1

    DNS:             192.168.0.1

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

[[/etc/NetworkManager/system-connections/Wi-Fi connection 1]] (600 root)
[connection] id=Wi-Fi connection 1 | type=802-11-wireless
[802-11-wireless] ssid=Cisco19634
[ipv4] method=auto
[ipv6] method=auto

##### iw reg get ########################

Region: Asia/Kolkata (based on set time zone)

country 00:
    (2402 - 2472 @ 40), (3, 20)
    (2457 - 2482 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (2474 - 2494 @ 20), (3, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
    (5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS

##### iwlist channels ###################

lo        no frequency information.

eth0      no frequency information.

##### iwlist scan #######################

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

##### module infos ######################

[b43]
filename:       /lib/modules/3.16.0-30-generic/kernel/drivers/net/wireless/b43/b43.ko
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
srcversion:     3CEE8C37D02010CA66D9311
depends:        bcma,ssb,mac80211,cfg80211
intree:         Y
vermagic:       3.16.0-30-generic SMP mod_unload modversions 686 
signer:         Magrathea: Glacier signing key
sig_key:        3C:66:A9:3E:B5:D1:A5:68:11:66:B6:81:A5:17:93:8D:08:1E:4D:C7
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
filename:       /lib/modules/3.16.0-30-generic/kernel/drivers/bcma/bcma.ko
license:        GPL
description:    Broadcom's specific AMBA driver
srcversion:     D52E980A55E0AC3C372382C
depends:        
intree:         Y
vermagic:       3.16.0-30-generic SMP mod_unload modversions 686 
signer:         Magrathea: Glacier signing key
sig_key:        3C:66:A9:3E:B5:D1:A5:68:11:66:B6:81:A5:17:93:8D:08:1E:4D:C7
sig_hashalgo:   sha512

[mac80211]
filename:       /lib/modules/3.16.0-30-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     D421794D4F30DF3A540FD24
depends:        cfg80211
intree:         Y
vermagic:       3.16.0-30-generic SMP mod_unload modversions 686 
signer:         Magrathea: Glacier signing key
sig_key:        3C:66:A9:3E:B5:D1:A5:68:11:66:B6:81:A5:17:93:8D:08:1E:4D:C7
sig_hashalgo:   sha512
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[cfg80211]
filename:       /lib/modules/3.16.0-30-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     DEE8EAA48495E392CD51C2D
depends:        
intree:         Y
vermagic:       3.16.0-30-generic SMP mod_unload modversions 686 
signer:         Magrathea: Glacier signing key
sig_key:        3C:66:A9:3E:B5:D1:A5:68:11:66:B6:81:A5:17:93:8D:08:1E:4D:C7
sig_hashalgo:   sha512
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

[ssb_hcd]
filename:       /lib/modules/3.16.0-30-generic/kernel/drivers/usb/host/ssb-hcd.ko
license:        GPL
description:    Common USB driver for SSB Bus
author:         Hauke Mehrtens
srcversion:     2A4C0EB5791EE9A11133FCB
depends:        ssb
intree:         Y
vermagic:       3.16.0-30-generic SMP mod_unload modversions 686 
signer:         Magrathea: Glacier signing key
sig_key:        3C:66:A9:3E:B5:D1:A5:68:11:66:B6:81:A5:17:93:8D:08:1E:4D:C7
sig_hashalgo:   sha512

[ssb]
filename:       /lib/modules/3.16.0-30-generic/kernel/drivers/ssb/ssb.ko
license:        GPL
description:    Sonics Silicon Backplane driver
srcversion:     2055C3093DA2EE9DEB5572C
depends:        
intree:         Y
vermagic:       3.16.0-30-generic SMP mod_unload modversions 686 
signer:         Magrathea: Glacier signing key
sig_key:        3C:66:A9:3E:B5:D1:A5:68:11:66:B6:81:A5:17:93:8D:08:1E:4D:C7
sig_hashalgo:   sha512

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

[/etc/modprobe.d/modesetting.conf]
options cirrus modeset=1
options mgag200 modeset=1

##### rc.local ##########################

exit 0

##### pm-utils ##########################

##### udev rules ########################

[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x14e4:0x170c (b44)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

##### dmesg #############################

[   10.763098] b43-phy0: Broadcom 4311 WLAN found (core revision 10)
[   10.802243] b43-phy0: Found PHY: Analog 4, Type 2 (G), Revision 8
[   10.802267] b43-phy0 warning: 5 GHz band is unsupported on this PHY
[   10.906549] b43 ssb0:0: Direct firmware load failed with error -2
[   10.906558] b43 ssb0:0: Falling back to user helper
[   11.153919] b43 ssb0:0: Direct firmware load failed with error -2
[   11.153924] b43 ssb0:0: Falling back to user helper
[   11.265711] b43 ssb0:0: Direct firmware load failed with error -2
[   11.265718] b43 ssb0:0: Falling back to user helper
[   11.266562] b43 ssb0:0: Direct firmware load failed with error -2
[   11.266567] b43 ssb0:0: Falling back to user helper
[   11.267738] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" request failed (err=-12)
[   11.267744] b43-phy0 ERROR: Firmware file "b43-open/ucode5.fw" request failed (err=-12)
[   11.267747] b43-phy0 ERROR: You must go to http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware and download the correct firmware for this driver version. Please carefully read all instructions on this website.
[   18.804233] b44 ssb1:0 eth0: Link is up at 100 Mbps, full duplex
[   18.804244] b44 ssb1:0 eth0: Flow control is off for TX and off for RX
[   87.804148] b44 ssb1:0 eth0: Link is down
[  162.804238] b44 ssb1:0 eth0: Link is up at 100 Mbps, full duplex
[  162.804250] b44 ssb1:0 eth0: Flow control is off for TX and off for RX

########## wireless info END ############
```

---

### Post by wildmanne39 on 2015-05-12
Please do:
```
sudo apt-get purge linux-firmware-nonfree
```
Then
```
sudo apt-get install firmware-b43-installer
```
Reboot

---

### Post by Vivek_Iyer on 2015-05-12
Thanks that worked

---

### Post by wildmanne39 on 2015-05-12
Your welcome!
Enjoy!

---

### Post by Vivek_Iyer on 2015-05-12
Just a conceptual question - what line in the script out made you give this recommendation? There were posts where they had recommended the opposite. Purge the bcm firmware and install the nonfree stuff. How does one take a call one way or the other?

Thanks

---

### Post by wildmanne39 on 2015-05-12
When it comes down to it, it is about keeping up with the changing times, however sometimes I am behind because I my personal life.

In this case > linux-firmware-nonfreehad the firmware needed by your device removed last year because of legal reasons, and it required going back to installing it this way:
> sudo apt-get install firmware-b43-installer
The reason I knew which firmware you needed is because your device is a 4311 according to the information in the:
> lspci
output.

I knew the firmware was missing because:
> dmesg
in the file said it was missing.

---

### Post by Vivek_Iyer on 2015-05-12
Got it. Thank you.

---

