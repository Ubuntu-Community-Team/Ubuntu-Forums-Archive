---
title: "Wireless in Acer Aspire 5051, Broadcom BCM4318 card"
date: 2014-08-10
forum: Networking &amp; Wireless
---

### Post by mferreira2 on 2014-08-10
Hi

I have install Ubuntu in old laptop (Aspire 5051 AWXMi from Acer). I can't setup the wireless connection and I can't figure out why. Any help would be greatly appreciated!

This is the output of the Wireless script:

```

########## wireless info START ##########

Report from: 10 Aug 2014 23:46 WEST +0100

Script from: 04 Aug 2014 18:47 UTC +0000

##### release #####

Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.1 LTS
Release:    14.04
Codename:    trusty

##### kernel #####

Linux 3.13.0-32-generic #57-Ubuntu SMP Tue Jul 15 03:51:12 UTC 2014 i686 athlon i686 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop #####

Ubuntu

##### lspci #####

08:02.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL-8100/8101L/8139 PCI Fast Ethernet Adapter [10ec:8139] (rev 10)
    Subsystem: Acer Incorporated [ALI] Device [1025:010f]
    Kernel driver in use: 8139too

08:04.0 Network controller [0280]: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller [14e4:4318] (rev 02)
    Subsystem: AMBIT Microsystem Corp. TravelMate 2410 [1468:0312]
    Kernel driver in use: wl

##### lsusb #####

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

##### PCMCIA Card Info #####

PRODID_1=""
PRODID_2=""
PRODID_3=""
PRODID_4=""
MANFID=0000,0000
FUNCID=255

##### rfkill #####

0: acer-wireless: Wireless LAN
    Soft blocked: no
    Hard blocked: no

##### lsmod #####

acer_wmi               31735  0 
sparse_keymap          13708  1 acer_wmi
video                  18903  1 acer_wmi
wl                   3999690  1 
lib80211               14040  1 wl
cfg80211              409394  1 wl
wmi                    18673  1 acer_wmi

##### interfaces #####

auto lo
iface lo inet loopback

##### ifconfig #####

eth0      Link encap:Ethernet  HWaddr <MAC addr eth0>  
          inet addr:192.168.1.86  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::216:36ff:fe90:2b3f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:95862 errors:5 dropped:52 overruns:5 frame:0
          TX packets:50360 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:118014587 (118.0 MB)  TX bytes:5516102 (5.5 MB)

##### iwconfig #####

lo        no wireless extensions.

eth0      no wireless extensions.

##### route #####

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.254   0.0.0.0         UG    0      0        0 eth0
192.168.1.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0

##### resolv.conf #####

nameserver 127.0.1.1
search lan

##### nm-tool #####

NetworkManager Tool

State: connected (global)

- Device: eth0  [Conexão cabeada 1] -------------------------------------------
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
    Address:         192.168.1.86
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.254

    DNS:             192.168.1.254

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

[wl]
filename:       /lib/modules/3.13.0-32-generic/updates/dkms/wl.ko
license:        MIXED/Proprietary
srcversion:     FF25FE784DC6BDFF69DAFCB
alias:          pci:v*d*sv*sd*bc02sc80i*
depends:        cfg80211,lib80211
vermagic:       3.13.0-32-generic SMP mod_unload modversions 686 
parm:           wl_txq_thresh:int
parm:           oneonly:int
parm:           piomode:int
parm:           instance_base:int
parm:           nompc:int
parm:           intf_name:string

##### module parameters #####

##### /etc/modules #####

lp

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

# PCI device 0x10ec:0x8139 (8139too)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC addr eth0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

##### dmesg #####

[   16.848832] type=1400 audit(1407706167.755:3): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=440 comm="apparmor_parser"
[   16.849506] type=1400 audit(1407706167.755:5): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=440 comm="apparmor_parser"
[   17.463301] wl: module license 'MIXED/Proprietary' taints kernel.
[   17.503917] wl: module verification failed: signature and/or  required key missing - tainting kernel
[   17.596650] Modules linked in: wl(POF+) kvm_amd snd_seq rfcomm pcmcia bnep bluetooth snd_seq_device kvm snd_timer lib80211 snd joydev yenta_socket pcmcia_rsrc cfg80211 k8temp serio_raw pcmcia_core soundcore i2c_piix4 shpchp mac_hid parport_pc ppdev lp parport pata_acpi radeon i2c_algo_bit 8139too ttm 8139cp sdhci_pci drm_kms_helper psmouse mii sdhci pata_atiixp sata_sil drm ati_agp wmi
[   17.596805]  [<f97c1e2a>] ? wl_pci_probe+0x1da/0x630 [wl]
[   17.596850]  [<f97c1e2a>] ? wl_pci_probe+0x1da/0x630 [wl]
[   17.596890]  [<f97c1e2a>] wl_pci_probe+0x1da/0x630 [wl]
[   17.596975]  [<f8888017>] wl_module_init+0x17/0x1000 [wl]
[   17.781754] wl driver 6.30.223.141 (r415941) failed with code 21
[   17.782005] Modules linked in: snd_rawmidi(+) wl(POF+) kvm_amd snd_seq rfcomm pcmcia bnep bluetooth snd_seq_device kvm snd_timer lib80211 snd joydev yenta_socket pcmcia_rsrc cfg80211 k8temp serio_raw pcmcia_core soundcore i2c_piix4 shpchp mac_hid parport_pc ppdev lp parport pata_acpi radeon i2c_algo_bit 8139too ttm 8139cp sdhci_pci drm_kms_helper psmouse mii sdhci pata_atiixp sata_sil drm ati_agp wmi
[   17.783093] EIP is at wdev_priv.part.9+0x3/0x5 [wl]
[   17.783999]  [<f97c89d7>] wl_cfg80211_detach+0xf7/0x100 [wl]
[   17.784001]  [<f97c13c3>] wl_free_if.isra.12+0x23/0xa0 [wl]
[   17.784001]  [<f97c1a68>] wl_free+0x78/0x260 [wl]
[   17.784001]  [<f97c1f5e>] wl_pci_probe+0x30e/0x630 [wl]
[   17.784001]  [<f8888017>] wl_module_init+0x17/0x1000 [wl]
[   17.784001] EIP: [<f97c8fb6>] wdev_priv.part.9+0x3/0x5 [wl] SS:ESP 0068:f084bbb8

########## wireless info END ############
```

---

### Post by mörgæs on 2014-08-10
Did you read the sticky note on Broadcom?

---

### Post by wildmanne39 on 2014-08-10
Please do:
```
sudo apt-get purge bcmwl-kernel-source
sudo apt-get install linux-firmware-nonfree
```
Reboot

---

### Post by mferreira2 on 2014-08-13
That worked!!

Many thanks Wild Man!

---

### Post by mferreira2 on 2014-10-07
Hi again

After an update (didn't find out which) I've lost the connection and can't figure out why. As far I can see the drivers are there and are updated.

Didn't know if it's better to start a new thread or continue this one.

Here's the output of the wirelesses script:

```

########## wireless info START ##########

Report from: 08 Oct 2014 00:08 WEST +0100

Booted last: 07 Oct 2014 22:03 WEST +0100

Script from: 20 Sep 2014 23:04 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.1 LTS
Release:    14.04
Codename:    trusty

##### kernel ############################

Linux 3.13.0-36-generic #63-Ubuntu SMP Wed Sep 3 21:30:45 UTC 2014 i686 athlon i686 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Ubuntu

##### lspci #############################

08:02.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL-8100/8101L/8139 PCI Fast Ethernet Adapter [10ec:8139] (rev 10)
    Subsystem: Acer Incorporated [ALI] Device [1025:010f]
    Kernel driver in use: 8139too

08:04.0 Network controller [0280]: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller [14e4:4318] (rev 02)
    Subsystem: AMBIT Microsystem Corp. TravelMate 2410 [1468:0312]
    Kernel driver in use: b43-pci-bridge

##### lsusb #############################

Bus 001 Device 002: ID 1058:1010 Western Digital Technologies, Inc. Elements External HDD
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

##### PCMCIA card info ##################

PRODID_1=""
PRODID_2=""
PRODID_3=""
PRODID_4=""
MANFID=0000,0000
FUNCID=255

##### rfkill ############################

0: acer-wireless: Wireless LAN
    Soft blocked: no
    Hard blocked: no

##### lsmod #############################

acer_wmi               31735  0 
sparse_keymap          13708  1 acer_wmi
video                  18903  1 acer_wmi
b43                   356470  0 
bcma                   42043  1 b43
mac80211              546051  1 b43
cfg80211              409394  2 b43,mac80211
ssb                    51854  1 b43
wmi                    18673  1 acer_wmi

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

eth0      Link encap:Ethernet  HWaddr <MAC 'eth0' [IF]>  
          inet addr:192.168.1.86  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::216:36ff:fe90:2b3f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:63679 errors:0 dropped:0 overruns:0 frame:0
          TX packets:49453 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:58007958 (58.0 MB)  TX bytes:7507023 (7.5 MB)

##### iwconfig ##########################

lo        no wireless extensions.

eth0      no wireless extensions.

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.254   0.0.0.0         UG    0      0        0 eth0
192.168.1.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0

##### resolv.conf #######################

nameserver 127.0.1.1
search lan

##### nm-tool ###########################

NetworkManager Tool

State: connected (global)

- Device: eth0  [Conexão cabeada 1] -------------------------------------------
  Type:              Wired
  Driver:            8139too
  State:             connected
  Default:           yes
  HW Address:        <MAC 'eth0' [IF]>

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.1.86
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.254

    DNS:             192.168.1.254

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

[[/etc/NetworkManager/system-connections/Vodafone-3C5A43]] (600 root)
[connection] id=Vodafone-3C5A43 | type=802-11-wireless
[802-11-wireless] ssid=Vodafone-3C5A43 | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/VodafoneSharingDock_C54B15]] (600 root)
[connection] id=VodafoneSharingDock_C54B15 | type=802-11-wireless
[802-11-wireless] ssid=VodafoneSharingDock_C54B15 | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/botanica]] (600 root)
[connection] id=botanica | type=802-11-wireless
[802-11-wireless] ssid=botanica | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Thomson67F7EA]] (600 root)
[connection] id=Thomson67F7EA | type=802-11-wireless
[802-11-wireless] ssid=Thomson67F7EA | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto

##### iw reg get ########################

Region: Europe/Lisbon (based on set time zone)

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
filename:       /lib/modules/3.13.0-36-generic/kernel/drivers/net/wireless/b43/b43.ko
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
srcversion:     7ABBDDCA84C087640B27AE6
depends:        bcma,ssb,mac80211,cfg80211
intree:         Y
vermagic:       3.13.0-36-generic SMP mod_unload modversions 686 
signer:         Magrathea: Glacier signing key
sig_key:        FF:9A:DA:11:B8:55:51:6A:72:98:65:9D:4E:3F:BB:76:C5:4A:D3:30
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
filename:       /lib/modules/3.13.0-36-generic/kernel/drivers/bcma/bcma.ko
license:        GPL
description:    Broadcom's specific AMBA driver
srcversion:     E41B811D88783DD5BC38565
depends:        
intree:         Y
vermagic:       3.13.0-36-generic SMP mod_unload modversions 686 
signer:         Magrathea: Glacier signing key
sig_key:        FF:9A:DA:11:B8:55:51:6A:72:98:65:9D:4E:3F:BB:76:C5:4A:D3:30
sig_hashalgo:   sha512

[mac80211]
filename:       /lib/modules/3.13.0-36-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     B822641624778B987844F6F
depends:        cfg80211
intree:         Y
vermagic:       3.13.0-36-generic SMP mod_unload modversions 686 
signer:         Magrathea: Glacier signing key
sig_key:        FF:9A:DA:11:B8:55:51:6A:72:98:65:9D:4E:3F:BB:76:C5:4A:D3:30
sig_hashalgo:   sha512
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[cfg80211]
filename:       /lib/modules/3.13.0-36-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     C2478077E22138832B71659
depends:        
intree:         Y
vermagic:       3.13.0-36-generic SMP mod_unload modversions 686 
signer:         Magrathea: Glacier signing key
sig_key:        FF:9A:DA:11:B8:55:51:6A:72:98:65:9D:4E:3F:BB:76:C5:4A:D3:30
sig_hashalgo:   sha512
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

[ssb]
filename:       /lib/modules/3.13.0-36-generic/kernel/drivers/ssb/ssb.ko
license:        GPL
description:    Sonics Silicon Backplane driver
srcversion:     3DE188310F77C566C2E8CB3
depends:        
intree:         Y
vermagic:       3.13.0-36-generic SMP mod_unload modversions 686 
signer:         Magrathea: Glacier signing key
sig_key:        FF:9A:DA:11:B8:55:51:6A:72:98:65:9D:4E:3F:BB:76:C5:4A:D3:30
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

##### rc.local ##########################

exit 0

##### pm-utils ##########################

##### udev rules ########################

[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x10ec:0x8139 (8139too)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# PCI device 0x14e4:0x4318 (b43)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

##### dmesg #############################

[   23.227064] b43 ssb0:0: Direct firmware load failed with error -2
[   23.227071] b43 ssb0:0: Falling back to user helper
[   23.352953] b43 ssb0:0: Direct firmware load failed with error -2
[   23.352960] b43 ssb0:0: Falling back to user helper
[   23.425871] b43 ssb0:0: Direct firmware load failed with error -2
[   23.425878] b43 ssb0:0: Falling back to user helper
[   23.431302] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found
[   23.431309] b43-phy0 ERROR: Firmware file "b43-open/ucode5.fw" not found
[   23.431312] b43-phy0 ERROR: You must go to http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware and download the correct firmware for this driver version. Please carefully read all instructions on this website.

########## wireless info END ############

```

---

### Post by Hadaka on 2014-10-07
Hi, from a wired connection..conneted to the internet please do.
```
sudo apt-get remove --purge linux-firmware-nonfree
sudo apt-get install b43-fwcutter firmware-b43-installer
sudo modprobe b43
```
thanks.

---

### Post by mferreira2 on 2014-10-08
> **Hadaka said:**
> Hi, from a wired connection..conneted to the internet please do.
```
sudo apt-get remove --purge linux-firmware-nonfree
sudo apt-get install b43-fwcutter firmware-b43-installer
sudo modprobe b43
```
thanks.

Hi Hadaka

It didn't work. Don't know why.

Here's the output of terminal. it's in Portuguese, but it says that Package 'linux-firmware-nonfree' is not installed and that the b43-fwcutter is already in it's lattest release.

Any ideas?

```

mario@Aspire-5050:~$ sudo apt-get remove --purge linux-firmware-nonfree
A ler as listas de pacotes... Pronto
A construir árvore de dependências       
A ler a informação de estado... Pronto
Package 'linux-firmware-nonfree' is not installed, so not removed
0 pacotes actualizados, 0 pacotes novos instalados, 0 a remover e 0 não actualizados.
mario@Aspire-5050:~$ sudo apt-get install b43-fwcutter firmware-b43-installer
A ler as listas de pacotes... Pronto
A construir árvore de dependências       
A ler a informação de estado... Pronto
b43-fwcutter já está na versão mais recente.
firmware-b43-installer já está na versão mais recente.
0 pacotes actualizados, 0 pacotes novos instalados, 0 a remover e 0 não actualizados.
mario@Aspire-5050:~$ sudo modprobe b43
mario@Aspire-5050:~$ 


```

---

### Post by Hadaka on 2014-10-08
Hi,looking at your last wireess script it shows the firmware is missing
that should have worked. Let's try this, make sure you are connected
to the internet via your ethernet cable and do,,
```
sudo apt-get remove --purge b43-fwcutter firmware-b43-installer
sudo apt-get install b43-fwcutter firmware-b43-installer
sudo modprobe -rf b43
sudo modprobe -v b43
```
ignore any moans and groans about files not found
also, go into networkmgr, and change your IPv6 to Ignore
thanks,

---

### Post by mferreira2 on 2014-10-08
Thanks it worked. Any ideia of it stopo working in the frist place?

---

### Post by Hadaka on 2014-10-08
Glad that worked ! The driver you were using..linux-firmware-nonfree
was kinda,sorta, in a way,,,on loan from broadcom, and they decided
to not support it and removed it. kinda,,

---

### Post by mferreira2 on 2014-10-08
LOL :P afterall it says non-free... Eh eh

Thanks again!!

---

### Post by Hadaka on 2014-10-08
forgot to add,,,mark it solved

how to0>[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

### Post by westie457 on 2014-10-08
> **Hadaka said:**
> Glad that worked ! The driver you were using..linux-firmware-nonfree
was kinda,sorta, in a way,,,on loan from broadcom, and they decided
to not support it and removed it. kinda,,
Just like the kid in the playground, 'Its my ball and you are not playing with it. So there'!

---

### Post by mattydizzle on 2014-10-12
How can I reverse this? It didn't work and made things worse for me.

---

### Post by mferreira2 on 2014-10-12
Hi

You should probably put the output of the wireless script so people can help you.

It's here:
[http://ubuntuforums.org/showthread.php?t=370108](http://ubuntuforums.org/showthread.php?t=370108)

Cheers

---

### Post by mörgæs on 2014-10-13
> **mattydizzle said:**
> How can I reverse this? It didn't work and made things worse for me.

Did you read the link in #12?

---

### Post by mattydizzle on 2014-10-13
My bad. Appreciate you guys! :p

---

