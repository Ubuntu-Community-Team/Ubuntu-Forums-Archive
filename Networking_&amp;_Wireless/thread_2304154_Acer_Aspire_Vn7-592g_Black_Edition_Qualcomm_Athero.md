---
title: "Acer Aspire Vn7-592g Black Edition Qualcomm Atheros 003e (rev 32) not working"
date: 2015-11-24
forum: Networking &amp; Wireless
---

### Post by db-d on 2015-11-24
Hi

I have a new Acer Aspire VN7-592g Black Edition with the following configuration:

[LIST]
[*]Item number: 5606957 
[*]Screen size: 17.30 " 
[*]Processor type: Intel Core i7-6700HQ 
[*]Graphics card model: nVidia GeForce GTX 960M 
[*]Memory: 32 GB 
[*]Capacity SSD: 256 GB 
[/LIST]

I use Ubuntu 14.04 and expect wireless and the touchpad it works quite good.

When I am right it has a Qualcomm Atheros qca61x4 wireless chip.

Here some more infos:

```

########## wireless info START ##########

Report from: 22 Nov 2015 21:13 CET +0100

Booted last: 22 Nov 2015 21:07 CET +0100

Script from: 27 Sep 2015 00:34 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.3 LTS
Release:    14.04
Codename:    trusty

##### kernel ############################

Linux 4.2.0-18-generic #22~14.04.1-Ubuntu SMP Fri Nov 6 22:20:11 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

sed: can't read /root/.dmrc: No such file or directory

Could not be determined.

##### lspci #############################

07:00.0 Network controller [0280]: Qualcomm Atheros Device [168c:003e] (rev 32)
    Subsystem: Lite-On Communications Inc Device [11ad:0807]

08:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 15)
    Subsystem: Acer Incorporated [ALI] Device [1025:103b]
    Kernel driver in use: r8169

##### lsusb #############################

Bus 002 Device 005: ID 17e9:436e DisplayLink 
Bus 002 Device 004: ID 2109:0812  
Bus 002 Device 003: ID 17e9:436e DisplayLink 
Bus 002 Device 002: ID 2109:0812  
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 005: ID 0bda:57cc Realtek Semiconductor Corp. 
Bus 001 Device 003: ID 04ca:3016 Lite-On Technology Corp. 
Bus 001 Device 010: ID 046d:c317 Logitech, Inc. Wave Corded Keyboard
Bus 001 Device 009: ID 0d8c:0102 C-Media Electronics, Inc. CM106 Like Sound Device
Bus 001 Device 008: ID 1a40:0101 Terminus Technology Inc. 4-Port HUB
Bus 001 Device 006: ID 046d:c51a Logitech, Inc. MX Revolution/G7 Cordless Mouse
Bus 001 Device 004: ID 2109:2812  
Bus 001 Device 002: ID 2109:2812  
Bus 001 Device 007: ID 0bda:0129 Realtek Semiconductor Corp. RTS5129 Card Reader Controller
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: acer-wireless: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no

##### lsmod #############################

acer_wmi               20480  0 
sparse_keymap          16384  1 acer_wmi
mac80211              626688  0 
cfg80211              536576  1 mac80211
compat                 16384  2 cfg80211,mac80211
wmi                    20480  1 acer_wmi
video                  36864  2 i915,acer_wmi

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

eth0      Link encap:Ethernet  HWaddr <MAC 'eth0' [IF]>  
          inet addr:192.168.1.32  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::<IP6 'eth0' [IF]>/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2423 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1993 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1260270 (1.2 MB)  TX bytes:464982 (464.9 KB)

usb0      Link encap:Ethernet  HWaddr <MAC 'usb0' [IF]>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

##### iwconfig ##########################

eth0      no wireless extensions.

usb0      no wireless extensions.

lo        no wireless extensions.

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 eth0
192.168.1.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0

##### resolv.conf #######################

nameserver 127.0.1.1

##### network managers ##################

Installed:

    NetworkManager

Running:

root       801     1  0 21:07 ?        00:00:00 NetworkManager

##### NetworkManager info ###############

NetworkManager Tool

State: connected (global)

- Device: eth0  [Kabelnetzwerkverbindung 2] ------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             connected
  Default:           yes
  HW Address:        <MAC 'eth0' [IF]>

  Capabilities:
    Carrier Detect:  yes
    Speed:           1000 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.1.32
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1

    DNS:             192.168.1.1

- Device: usb0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            cdc_ncm
  State:             unavailable
  Default:           no
  HW Address:        <MAC 'usb0' [IF]>

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off

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

Region: Europe/Zurich (based on set time zone)

country 00:
    (2402 - 2472 @ 40), (3, 20)
    (2457 - 2482 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (2474 - 2494 @ 20), (3, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
    (5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS

##### iwlist channels ###################

eth0      no frequency information.

usb0      no frequency information.

lo        no frequency information.

##### iwlist scan #######################

eth0      Interface doesn't support scanning.

usb0      Interface doesn't support scanning.

lo        Interface doesn't support scanning.

##### module infos ######################

[mac80211]
filename:       /lib/modules/4.2.0-18-generic/updates/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
version:        backported from Linux (v3.2-rc1-274977-g89cac0b) using backports backports-20151115-0-g732e101
srcversion:     0446510E653ADEC3C24D1C8
depends:        cfg80211,compat
vermagic:       4.2.0-18-generic SMP mod_unload modversions 
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[cfg80211]
filename:       /lib/modules/4.2.0-18-generic/updates/net/wireless/cfg80211.ko
version:        backported from Linux (v3.2-rc1-274977-g89cac0b) using backports backports-20151115-0-g732e101
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     42F5632EB87D32503B42224
depends:        compat
vermagic:       4.2.0-18-generic SMP mod_unload modversions 
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

##### module parameters #################

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

[/etc/modprobe.d/ath10k.conf]
options ath10k_core skip_otp=y

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
# PCI device 0x10ec:0x8168 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# PCI device 0x168c:0x003e (ath10k_pci)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

##### dmesg #############################

[  104.456077] cdc_ncm 2-2.3:1.5 usb0: kevent 12 may have been dropped
[  104.456081] IPv6: ADDRCONF(NETDEV_UP): usb0: link is not ready
[  104.474267] r8169 0000:08:00.0 eth0: link down
[  104.474345] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[  104.474347] r8169 0000:08:00.0 eth0: link down
[  108.268638] r8169 0000:08:00.0 eth0: link up
[  108.268648] IPv6: ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready

########## wireless info END ############

```

I did tried two things until now. I use the upstream kernel from ubuntu 15.10 and I tried to install the newest Backports from [https://wireless.wiki.kernel.org/en/users/drivers/ath10k/backports](https://wireless.wiki.kernel.org/en/users/drivers/ath10k/backports).
But until now without luck. I still dont get any wireless connection.

Has anyone experience with this laptop and ubuntu or does someone know how i get this wireless card model to run?

---

### Post by chili555 on 2015-11-24
Please load the driver:```
sudo modprobe ath10k_pci
```Check the log for messages:```
dmesg | grep ath
```Is the firmware missing? If so, do:```
sudo mkdir /lib/firmware/ath10k/QCA6174/hw2.1
cd /lib/firmware/ath10k/QCA6174/hw2.1
sudo wget https://git.kernel.org/cgit/linux/kernel/git/firmware/linux-firmware.git/plain/ath10k/QCA6174/hw2.1/firmware-5.bin
sudo wget https://git.kernel.org/cgit/linux/kernel/git/firmware/linux-firmware.git/plain/ath10k/QCA6174/hw2.1/board.bin
```Reboot and your wireless should be working.

If there are other, more interesting messages, post them and we'll fire up the surgical theater!

---

### Post by db-d on 2015-11-26
Thx for your help.

I did what you said.

the output of dmesg | grep ath is:
```

[    2.450565] ath10k_pci 0000:07:00.0: pci irq msi-x interrupts 8 irq_mode 0 reset_mode 0
[    2.690182] ath10k_pci 0000:07:00.0: Direct firmware load for ath10k/cal-pci-0000:07:00.0.bin failed with error -2
[    2.694457] ath10k_pci 0000:07:00.0: Direct firmware load for ath10k/QCA6174/hw3.0/firmware-5.bin failed with error -2
[    2.694463] ath10k_pci 0000:07:00.0: could not fetch firmware file 'ath10k/QCA6174/hw3.0/firmware-5.bin': -2
[    2.764769] ath10k_pci 0000:07:00.0: Direct firmware load for ath10k/QCA6174/hw3.0/board-2.bin failed with error -2
[    4.912176] ath10k_pci 0000:07:00.0: qca6174 hw3.2 (0x05030000, 0x00340aff sub 11ad:0807) fw WLAN.RM.2.0-00180-QCARMSWPZ-1 fwapi 4 bdapi 1 htt-ver 3.26 wmi-op 4 htt-op 3 cal otp max-sta 32 raw 0 hwcrypto 1 features wowlan,ignore-otp,no-4addr-pad
[    4.912179] ath10k_pci 0000:07:00.0: debug 1 debugfs 1 tracing 0 dfs 0 testmode 0
[    4.979562] ath: EEPROM regdomain: 0x6c
[    4.979564] ath: EEPROM indicates we should expect a direct regpair map
[    4.979565] ath: Country alpha2 being used: 00
[    4.979566] ath: Regpair used: 0x6c
```

I did not figure out what error -2 means, but it does not look good.
The other interesting thin is that it uses hw3.0.

I also tried to copy the firmware 3.0 files from 
[https://git.kernel.org/cgit/linux/kernel/git/firmware/linux-firmware.git/plain/ath10k/QCA6174/hw3.0/board.bin](https://git.kernel.org/cgit/linux/kernel/git/firmware/linux-firmware.git/plain/ath10k/QCA6174/hw3.0/board.bin)

Maybe you have another hint where to search the error.


Here the actual output of wireless_info:
```

########## wireless info START ##########

Report from: 26 Nov 2015 20:43 CET +0100

Booted last: 26 Nov 2015 20:37 CET +0100

Script from: 27 Sep 2015 00:34 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.3 LTS
Release:    14.04
Codename:    trusty

##### kernel ############################

Linux 4.2.0-18-generic #22~14.04.1-Ubuntu SMP Fri Nov 6 22:20:11 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

sed: can't read /root/.dmrc: No such file or directory

Could not be determined.

##### lspci #############################

07:00.0 Network controller [0280]: Qualcomm Atheros Device [168c:003e] (rev 32)
    Subsystem: Lite-On Communications Inc Device [11ad:0807]
    Kernel driver in use: ath10k_pci

08:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 15)
    Subsystem: Acer Incorporated [ALI] Device [1025:103b]
    Kernel driver in use: r8169

##### lsusb #############################

Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 005: ID 0bda:57cc Realtek Semiconductor Corp. 
Bus 001 Device 003: ID 04ca:3016 Lite-On Technology Corp. 
Bus 001 Device 008: ID 046d:c51a Logitech, Inc. MX Revolution/G7 Cordless Mouse
Bus 001 Device 006: ID 046d:c317 Logitech, Inc. Wave Corded Keyboard
Bus 001 Device 004: ID 0d8c:0102 C-Media Electronics, Inc. CM106 Like Sound Device
Bus 001 Device 002: ID 1a40:0101 Terminus Technology Inc. 4-Port HUB
Bus 001 Device 007: ID 0bda:0129 Realtek Semiconductor Corp. RTS5129 Card Reader Controller
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: acer-wireless: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
2: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

##### lsmod #############################

acer_wmi               20480  0 
sparse_keymap          16384  1 acer_wmi
ath10k_pci             45056  0 
ath10k_core           294912  1 ath10k_pci
ath                    32768  1 ath10k_core
mac80211              630784  1 ath10k_core
cfg80211              536576  3 ath,mac80211,ath10k_core
compat                 16384  3 cfg80211,mac80211,ath10k_pci
wmi                    20480  1 acer_wmi
video                  36864  2 i915,acer_wmi

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

eth0      Link encap:Ethernet  HWaddr <MAC 'eth0' [IF]>  
          inet6 addr: fe80::<IP6 'eth0' [IF]>/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:1818 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1587 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:958153 (958.1 KB)  TX bytes:391282 (391.2 KB)

wlan0     Link encap:Ethernet  HWaddr <MAC 'wlan0' [IF]>  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

##### iwconfig ##########################

eth0      no wireless extensions.

lo        no wireless extensions.

wlan0     IEEE 802.11abgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=0 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:on
          

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface

##### resolv.conf #######################

##### network managers ##################

Installed:

    NetworkManager

Running:

root       801     1  0 20:37 ?        00:00:02 NetworkManager

##### NetworkManager info ###############

NetworkManager Tool

State: disconnected

- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            ath10k_pci
  State:             unavailable
  Default:           no
  HW Address:        <MAC 'wlan0' [IF]>

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 

- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             unavailable
  Default:           no
  HW Address:        <MAC 'eth0' [IF]>

  Capabilities:
    Carrier Detect:  yes
    Speed:           1000 Mb/s

  Wired Properties
    Carrier:         off

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

Region: Europe/Zurich (based on set time zone)

country 00:
    (2402 - 2472 @ 40), (3, 20)
    (2457 - 2482 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (2474 - 2494 @ 20), (3, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
    (5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS

##### iwlist channels ###################

eth0      no frequency information.

lo        no frequency information.

wlan0     32 channels in total; available frequencies :
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
          Channel 36 : 5.18 GHz
          Channel 40 : 5.2 GHz
          Channel 44 : 5.22 GHz
          Channel 48 : 5.24 GHz
          Channel 52 : 5.26 GHz
          Channel 56 : 5.28 GHz
          Channel 60 : 5.3 GHz
          Channel 64 : 5.32 GHz
          Channel 100 : 5.5 GHz
          Channel 104 : 5.52 GHz
          Channel 108 : 5.54 GHz
          Channel 112 : 5.56 GHz
          Channel 116 : 5.58 GHz
          Channel 120 : 5.6 GHz
          Channel 124 : 5.62 GHz
          Channel 128 : 5.64 GHz
          Channel 132 : 5.66 GHz
          Channel 136 : 5.68 GHz
          Channel 140 : 5.7 GHz

##### iwlist scan #######################

eth0      Interface doesn't support scanning.

wlan0     Interface doesn't support scanning : Network is down

lo        Interface doesn't support scanning.

##### module infos ######################

[ath10k_pci]
filename:       /lib/modules/4.2.0-18-generic/updates/drivers/net/wireless/ath/ath10k/ath10k_pci.ko
firmware:       ath10k/QCA9377/hw1.0/board.bin
firmware:       ath10k/QCA9377/hw1.0/firmware-5.bin
firmware:       ath10k/QCA6174/hw3.0/board-2.bin
firmware:       ath10k/QCA6174/hw3.0/board.bin
firmware:       ath10k/QCA6174/hw3.0/firmware-5.bin
firmware:       ath10k/QCA6174/hw3.0/firmware-4.bin
firmware:       ath10k/QCA6174/hw2.1/board-2.bin
firmware:       ath10k/QCA6174/hw2.1/board.bin
firmware:       ath10k/QCA6174/hw2.1/firmware-5.bin
firmware:       ath10k/QCA6174/hw2.1/firmware-4.bin
firmware:       ath10k/QCA988X/hw2.0/board-2.bin
firmware:       ath10k/QCA988X/hw2.0/board.bin
firmware:       ath10k/QCA988X/hw2.0/firmware-5.bin
firmware:       ath10k/QCA988X/hw2.0/firmware-4.bin
firmware:       ath10k/QCA988X/hw2.0/firmware-3.bin
firmware:       ath10k/QCA988X/hw2.0/firmware-2.bin
firmware:       ath10k/QCA988X/hw2.0/firmware.bin
license:        Dual BSD/GPL
description:    Driver support for Atheros QCA988X PCIe devices
author:         Qualcomm Atheros
version:        backported from Linux (next-20151120-0-ga78de01) using backports backports-20151120-0-g906a6b3
srcversion:     EBB3D4E36DE49B7EC8057D0
depends:        ath10k_core,compat
vermagic:       4.2.0-18-generic SMP mod_unload modversions 
parm:           irq_mode:0: auto, 1: legacy, 2: msi (default: 0) (uint)
parm:           reset_mode:0: auto, 1: warm only (default: 0) (uint)

[ath10k_core]
filename:       /lib/modules/4.2.0-18-generic/updates/drivers/net/wireless/ath/ath10k/ath10k_core.ko
license:        Dual BSD/GPL
description:    Core module for QCA988X PCIe devices.
author:         Qualcomm Atheros
srcversion:     27000DBD292A446A6D969C2
depends:        mac80211,cfg80211,ath
vermagic:       4.2.0-18-generic SMP mod_unload modversions 
parm:           debug_mask:Debugging mask (uint)
parm:           uart_print:Uart target debugging (bool)
parm:           skip_otp:Skip otp failure for calibration in testmode (bool)
parm:           cryptmode:Crypto mode: 0-hardware, 1-software (uint)
parm:           rawmode:Use raw 802.11 frame datapath (bool)

[ath]
filename:       /lib/modules/4.2.0-18-generic/updates/drivers/net/wireless/ath/ath.ko
license:        Dual BSD/GPL
description:    Shared library for Atheros wireless LAN cards.
author:         Atheros Communications
srcversion:     6A988397A204F65CDF45A3C
depends:        cfg80211
vermagic:       4.2.0-18-generic SMP mod_unload modversions 

[mac80211]
filename:       /lib/modules/4.2.0-18-generic/updates/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
version:        backported from Linux (next-20151120-0-ga78de01) using backports backports-20151120-0-g906a6b3
srcversion:     2C80E97047B792154BF55FA
depends:        cfg80211,compat
vermagic:       4.2.0-18-generic SMP mod_unload modversions 
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[cfg80211]
filename:       /lib/modules/4.2.0-18-generic/updates/net/wireless/cfg80211.ko
version:        backported from Linux (next-20151120-0-ga78de01) using backports backports-20151120-0-g906a6b3
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     23A01DB42292FFA2C48ACC7
depends:        compat
vermagic:       4.2.0-18-generic SMP mod_unload modversions 
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

##### module parameters #################

[ath10k_pci]
irq_mode: 0
reset_mode: 0

[ath10k_core]
cryptmode: 0
debug_mask: 0
rawmode: N
skip_otp: N
uart_print: N

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
# PCI device 0x10ec:0x8168 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# PCI device 0x168c:0x003e (ath10k_pci)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

##### dmesg #############################

[   80.153472] ath10k_pci 0000:07:00.0: failed to enable dynamic BW: -11
[   86.149550] ath10k_pci 0000:07:00.0: could not suspend target (-11)
[  295.829141] r8169 0000:08:00.0 eth0: link down

########## wireless info END ############


```

---

### Post by chili555 on 2015-11-26
Let me just amend my faulty firmware instructions. Please do:```
sudo apt-get install git
git clone https://github.com/kvalo/ath10k-firmware.git
sudo mkdir /lib/firmware/ath10k/QCA6174/hw3.0
cd ath10k-firmware/QCA6174/hw3.0
sudo cp board.bin  /lib/firmware/ath10k/QCA6174/hw3.0
sudo cp firmware-4.bin_WLAN.RM.2.0-00180-QCARMSWPZ-1 /lib/firmware/ath10k/QCA6174/hw3.0/firmware-4.bin 
```Check the contents and permissions:```
ls -al   /lib/firmware/ath10k/QCA6174/hw3.0
```It ought to read:```
drwxr-xr-x 2 root root   4096 Nov 21 10:22 .
drwxr-xr-x 4 root root   4096 Nov 21 10:23 ..
-rw-r--r-- 1 root root   8124 Nov 26 21:01 board.bin
-rw-r--r-- 1 root root 733784 Nov 26 21:01 firmware-4.bin

```Unload and reload the driver:```
sudo modprobe -r ath10k_pci
sudo modprobe ath10k_pci
```It may take a reboot.

---

### Post by db-d on 2015-11-28
OK i did exactly what you wrote. But without luck.


```
ls -al   /lib/firmware/ath10k/QCA6174/hw3.0
drwxr-xr-x 2 root root   4096 Nov 28 08:10 .
drwxr-xr-x 4 root root   4096 Nov 22 18:14 ..
-rw-r--r-- 1 root root   8124 Nov 28 08:09 board.bin
-rw-r--r-- 1 root root 733784 Nov 28 08:10 firmware-4.bin


```

```
dmesg | grep ath

[    1.699249] ath10k_pci 0000:07:00.0: pci irq msi-x interrupts 8 irq_mode 0 reset_mode 0
[    1.932932] ath10k_pci 0000:07:00.0: Direct firmware load for ath10k/cal-pci-0000:07:00.0.bin failed with error -2
[    1.933736] ath10k_pci 0000:07:00.0: Direct firmware load for ath10k/QCA6174/hw3.0/firmware-5.bin failed with error -2
[    1.933739] ath10k_pci 0000:07:00.0: could not fetch firmware file 'ath10k/QCA6174/hw3.0/firmware-5.bin': -2
[    1.998063] ath10k_pci 0000:07:00.0: Direct firmware load for ath10k/QCA6174/hw3.0/board-2.bin failed with error -2
[    4.116596] ath10k_pci 0000:07:00.0: qca6174 hw3.2 (0x05030000, 0x00340aff sub 11ad:0807) fw WLAN.RM.2.0-00180-QCARMSWPZ-1 fwapi 4 bdapi 1 htt-ver 3.26 wmi-op 4 htt-op 3 cal otp max-sta 32 raw 0 hwcrypto 1 features wowlan,ignore-otp,no-4addr-pad
[    4.116599] ath10k_pci 0000:07:00.0: debug 1 debugfs 1 tracing 0 dfs 0 testmode 0
[    7.115743] ath10k_pci 0000:07:00.0: could not suspend target (-11)
[    7.183670] ath: EEPROM regdomain: 0x6c
[    7.183673] ath: EEPROM indicates we should expect a direct regpair map
[    7.183675] ath: Country alpha2 being used: 00
[    7.183676] ath: Regpair used: 0x6c
[   12.463064] ath10k_pci 0000:07:00.0: failed to enable dynamic BW: -11
[   18.464132] ath10k_pci 0000:07:00.0: could not suspend target (-11)
[   23.781965] ath10k_pci 0000:07:00.0: failed to enable dynamic BW: -11
[   29.784038] ath10k_pci 0000:07:00.0: could not suspend target (-11)
[   35.093844] ath10k_pci 0000:07:00.0: failed to enable dynamic BW: -11
[   41.095877] ath10k_pci 0000:07:00.0: could not suspend target (-11)
[   46.409658] ath10k_pci 0000:07:00.0: failed to set rx-chainmask: -11, req 0x3
[   49.410728] ath10k_pci 0000:07:00.0: failed to set arp ac override parameter: -11
[   55.412770] ath10k_pci 0000:07:00.0: could not suspend target (-11)
[   60.722589] ath10k_pci 0000:07:00.0: failed to enable dynamic BW: -11
[   66.724682] ath10k_pci 0000:07:00.0: could not suspend target (-11)
[   72.034458] ath10k_pci 0000:07:00.0: failed to enable dynamic BW: -11


```

It looks like the driver is loaded but dont work properly.

---

### Post by jeremy31 on 2015-11-28
There is one parameter setting that may help
```
echo "options ath10k_core skip_otp=Y" | sudo tee /etc/modprobe.d/ath10k_core.conf
```
Reboot

---

### Post by db-d on 2015-11-29
thank you for the new hint. But it didn’t change anything.
I changed the setting like you wrote.

wireless info
```

########## wireless info START ##########

Report from: 29 Nov 2015 09:29 CET +0100

Booted last: 29 Nov 2015 09:22 CET +0100

Script from: 27 Sep 2015 00:34 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.3 LTS
Release:    14.04
Codename:    trusty

##### kernel ############################

Linux 4.2.0-18-generic #22~14.04.1-Ubuntu SMP Fri Nov 6 22:20:11 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

sed: can't read /root/.dmrc: No such file or directory

Could not be determined.

##### lspci #############################

07:00.0 Network controller [0280]: Qualcomm Atheros Device [168c:003e] (rev 32)
    Subsystem: Lite-On Communications Inc Device [11ad:0807]
    Kernel driver in use: ath10k_pci

08:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 15)
    Subsystem: Acer Incorporated [ALI] Device [1025:103b]
    Kernel driver in use: r8169

##### lsusb #############################

Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 004: ID 0bda:57cc Realtek Semiconductor Corp. 
Bus 001 Device 003: ID 04ca:3016 Lite-On Technology Corp. 
Bus 001 Device 002: ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 001 Device 005: ID 0bda:0129 Realtek Semiconductor Corp. RTS5129 Card Reader Controller
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: acer-wireless: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
3: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

##### lsmod #############################

ath10k_pci             45056  0 
ath10k_core           294912  1 ath10k_pci
ath                    32768  1 ath10k_core
mac80211              630784  1 ath10k_core
cfg80211              536576  3 ath,mac80211,ath10k_core
compat                 16384  3 cfg80211,mac80211,ath10k_pci
acer_wmi               20480  0 
sparse_keymap          16384  1 acer_wmi
wmi                    20480  1 acer_wmi
video                  36864  2 i915,acer_wmi

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

eth0      Link encap:Ethernet  HWaddr <MAC 'eth0' [IF]>  
          inet addr:192.168.1.32  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::<IP6 'eth0' [IF]>/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:6533 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5119 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:5516208 (5.5 MB)  TX bytes:724186 (724.1 KB)

wlan0     Link encap:Ethernet  HWaddr <MAC 'wlan0' [IF]>  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

##### iwconfig ##########################

eth0      no wireless extensions.

lo        no wireless extensions.

wlan0     IEEE 802.11abgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=0 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:on
          

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 eth0
192.168.1.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0

##### resolv.conf #######################

nameserver 127.0.1.1

##### network managers ##################

Installed:

    NetworkManager

Running:

root       824     1  1 09:22 ?        00:00:06 NetworkManager

##### NetworkManager info ###############

NetworkManager Tool

State: connected (global)

- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            ath10k_pci
  State:             unavailable
  Default:           no
  HW Address:        <MAC 'wlan0' [IF]>

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 

- Device: eth0  [Kabelnetzwerkverbindung 1] ------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             connected
  Default:           yes
  HW Address:        <MAC 'eth0' [IF]>

  Capabilities:
    Carrier Detect:  yes
    Speed:           1000 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.1.32
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1

    DNS:             192.168.1.1

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

Region: Europe/Zurich (based on set time zone)

country 00:
    (2402 - 2472 @ 40), (3, 20)
    (2457 - 2482 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (2474 - 2494 @ 20), (3, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
    (5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS

##### iwlist channels ###################

eth0      no frequency information.

lo        no frequency information.

wlan0     32 channels in total; available frequencies :
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
          Channel 36 : 5.18 GHz
          Channel 40 : 5.2 GHz
          Channel 44 : 5.22 GHz
          Channel 48 : 5.24 GHz
          Channel 52 : 5.26 GHz
          Channel 56 : 5.28 GHz
          Channel 60 : 5.3 GHz
          Channel 64 : 5.32 GHz
          Channel 100 : 5.5 GHz
          Channel 104 : 5.52 GHz
          Channel 108 : 5.54 GHz
          Channel 112 : 5.56 GHz
          Channel 116 : 5.58 GHz
          Channel 120 : 5.6 GHz
          Channel 124 : 5.62 GHz
          Channel 128 : 5.64 GHz
          Channel 132 : 5.66 GHz
          Channel 136 : 5.68 GHz
          Channel 140 : 5.7 GHz

##### iwlist scan #######################

eth0      Interface doesn't support scanning.

wlan0     Interface doesn't support scanning : Network is down

lo        Interface doesn't support scanning.

##### module infos ######################

[ath10k_pci]
filename:       /lib/modules/4.2.0-18-generic/updates/drivers/net/wireless/ath/ath10k/ath10k_pci.ko
firmware:       ath10k/QCA9377/hw1.0/board.bin
firmware:       ath10k/QCA9377/hw1.0/firmware-5.bin
firmware:       ath10k/QCA6174/hw3.0/board-2.bin
firmware:       ath10k/QCA6174/hw3.0/board.bin
firmware:       ath10k/QCA6174/hw3.0/firmware-5.bin
firmware:       ath10k/QCA6174/hw3.0/firmware-4.bin
firmware:       ath10k/QCA6174/hw2.1/board-2.bin
firmware:       ath10k/QCA6174/hw2.1/board.bin
firmware:       ath10k/QCA6174/hw2.1/firmware-5.bin
firmware:       ath10k/QCA6174/hw2.1/firmware-4.bin
firmware:       ath10k/QCA988X/hw2.0/board-2.bin
firmware:       ath10k/QCA988X/hw2.0/board.bin
firmware:       ath10k/QCA988X/hw2.0/firmware-5.bin
firmware:       ath10k/QCA988X/hw2.0/firmware-4.bin
firmware:       ath10k/QCA988X/hw2.0/firmware-3.bin
firmware:       ath10k/QCA988X/hw2.0/firmware-2.bin
firmware:       ath10k/QCA988X/hw2.0/firmware.bin
license:        Dual BSD/GPL
description:    Driver support for Atheros QCA988X PCIe devices
author:         Qualcomm Atheros
version:        backported from Linux (next-20151120-0-ga78de01) using backports backports-20151120-0-g906a6b3
srcversion:     EBB3D4E36DE49B7EC8057D0
depends:        ath10k_core,compat
vermagic:       4.2.0-18-generic SMP mod_unload modversions 
parm:           irq_mode:0: auto, 1: legacy, 2: msi (default: 0) (uint)
parm:           reset_mode:0: auto, 1: warm only (default: 0) (uint)

[ath10k_core]
filename:       /lib/modules/4.2.0-18-generic/updates/drivers/net/wireless/ath/ath10k/ath10k_core.ko
license:        Dual BSD/GPL
description:    Core module for QCA988X PCIe devices.
author:         Qualcomm Atheros
srcversion:     27000DBD292A446A6D969C2
depends:        mac80211,cfg80211,ath
vermagic:       4.2.0-18-generic SMP mod_unload modversions 
parm:           debug_mask:Debugging mask (uint)
parm:           uart_print:Uart target debugging (bool)
parm:           skip_otp:Skip otp failure for calibration in testmode (bool)
parm:           cryptmode:Crypto mode: 0-hardware, 1-software (uint)
parm:           rawmode:Use raw 802.11 frame datapath (bool)

[ath]
filename:       /lib/modules/4.2.0-18-generic/updates/drivers/net/wireless/ath/ath.ko
license:        Dual BSD/GPL
description:    Shared library for Atheros wireless LAN cards.
author:         Atheros Communications
srcversion:     6A988397A204F65CDF45A3C
depends:        cfg80211
vermagic:       4.2.0-18-generic SMP mod_unload modversions 

[mac80211]
filename:       /lib/modules/4.2.0-18-generic/updates/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
version:        backported from Linux (next-20151120-0-ga78de01) using backports backports-20151120-0-g906a6b3
srcversion:     2C80E97047B792154BF55FA
depends:        cfg80211,compat
vermagic:       4.2.0-18-generic SMP mod_unload modversions 
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[cfg80211]
filename:       /lib/modules/4.2.0-18-generic/updates/net/wireless/cfg80211.ko
version:        backported from Linux (next-20151120-0-ga78de01) using backports backports-20151120-0-g906a6b3
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     23A01DB42292FFA2C48ACC7
depends:        compat
vermagic:       4.2.0-18-generic SMP mod_unload modversions 
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

##### module parameters #################

[ath10k_pci]
irq_mode: 0
reset_mode: 0

[ath10k_core]
cryptmode: 0
debug_mask: 0
rawmode: N
skip_otp: Y
uart_print: N

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

[/etc/modprobe.d/ath10k_core.conf]
options ath10k_core skip_otp=Y

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
# PCI device 0x10ec:0x8168 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# PCI device 0x168c:0x003e (ath10k_pci)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

##### dmesg #############################

[    1.928511] ath10k_pci 0000:07:00.0: Direct firmware load for ath10k/QCA6174/hw3.0/board-2.bin failed with error -2
[    2.139673] r8169 0000:08:00.0 eth0: link down
[    2.139726] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[    4.050893] ath10k_pci 0000:07:00.0: qca6174 hw3.2 (0x05030000, 0x00340aff sub 11ad:0807) fw WLAN.RM.2.0-00180-QCARMSWPZ-1 fwapi 4 bdapi 1 htt-ver 3.26 wmi-op 4 htt-op 3 cal otp max-sta 32 raw 0 hwcrypto 1 features wowlan,ignore-otp,no-4addr-pad
[    4.050896] ath10k_pci 0000:07:00.0: debug 1 debugfs 1 tracing 0 dfs 0 testmode 0
[    4.115800] ath: EEPROM regdomain: 0x6c
[    4.115802] ath: EEPROM indicates we should expect a direct regpair map
[    4.115804] ath: Country alpha2 being used: 00
[    4.115804] ath: Regpair used: 0x6c
[   20.881427] ath10k_pci 0000:07:00.0: failed to set rx-chainmask: -11, req 0x3
[   23.881041] ath10k_pci 0000:07:00.0: failed to set arp ac override parameter: -11
[   29.880049] ath10k_pci 0000:07:00.0: could not suspend target (-11)
[  130.519350] ath10k_pci 0000:07:00.0: pci irq msi-x interrupts 8 irq_mode 0 reset_mode 0
[  130.754082] ath10k_pci 0000:07:00.0: Direct firmware load for ath10k/cal-pci-0000:07:00.0.bin failed with error -2
[  130.754107] ath10k_pci 0000:07:00.0: Direct firmware load for ath10k/QCA6174/hw3.0/firmware-5.bin failed with error -2
[  130.754109] ath10k_pci 0000:07:00.0: could not fetch firmware file 'ath10k/QCA6174/hw3.0/firmware-5.bin': -2
[  130.816364] ath10k_pci 0000:07:00.0: Direct firmware load for ath10k/QCA6174/hw3.0/board-2.bin failed with error -2
[  132.933923] ath10k_pci 0000:07:00.0: qca6174 hw3.2 (0x05030000, 0x00340aff sub 11ad:0807) fw WLAN.RM.2.0-00180-QCARMSWPZ-1 fwapi 4 bdapi 1 htt-ver 3.26 wmi-op 4 htt-op 3 cal otp max-sta 32 raw 0 hwcrypto 1 features wowlan,ignore-otp,no-4addr-pad
[  132.933927] ath10k_pci 0000:07:00.0: debug 1 debugfs 1 tracing 0 dfs 0 testmode 0
[  135.931869] ath10k_pci 0000:07:00.0: could not suspend target (-11)
[  135.999538] ath: EEPROM regdomain: 0x6c
[  135.999540] ath: EEPROM indicates we should expect a direct regpair map
[  135.999541] ath: Country alpha2 being used: 00
[  135.999542] ath: Regpair used: 0x6c
[  141.247065] ath10k_pci 0000:07:00.0: failed to set tx-chainmask: -11, req 0x3
[  144.246688] ath10k_pci 0000:07:00.0: failed to set arp ac override parameter: -11
[  150.245759] ath10k_pci 0000:07:00.0: could not suspend target (-11)
[  155.564872] ath10k_pci 0000:07:00.0: failed to enable dynamic BW: -11
[  161.563947] ath10k_pci 0000:07:00.0: could not suspend target (-11)
[  166.871134] ath10k_pci 0000:07:00.0: failed to enable dynamic BW: -11
[  172.870226] ath10k_pci 0000:07:00.0: could not suspend target (-11)
[  178.181426] ath10k_pci 0000:07:00.0: failed to enable dynamic BW: -11
[  184.180481] ath10k_pci 0000:07:00.0: could not suspend target (-11)
[  189.487681] ath10k_pci 0000:07:00.0: failed to enable dynamic BW: -11
[  195.486751] ath10k_pci 0000:07:00.0: could not suspend target (-11)
[  200.793940] ath10k_pci 0000:07:00.0: failed to enable dynamic BW: -11
[  206.792956] ath10k_pci 0000:07:00.0: could not suspend target (-11)
[  212.100153] ath10k_pci 0000:07:00.0: failed to enable dynamic BW: -11
[  218.099292] ath10k_pci 0000:07:00.0: could not suspend target (-11)
[  223.410484] ath10k_pci 0000:07:00.0: failed to set tx-chainmask: -11, req 0x3
[  226.410015] ath10k_pci 0000:07:00.0: failed to set arp ac override parameter: -11
[  232.409096] ath10k_pci 0000:07:00.0: could not suspend target (-11)
[  237.732282] ath10k_pci 0000:07:00.0: failed to enable dynamic BW: -11
[  243.731365] ath10k_pci 0000:07:00.0: could not suspend target (-11)
[  249.042549] ath10k_pci 0000:07:00.0: failed to enable dynamic BW: -11
[  255.041633] ath10k_pci 0000:07:00.0: could not suspend target (-11)
[  282.320406] r8169 0000:08:00.0 eth0: link up
[  282.320414] IPv6: ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready

########## wireless info END ############


```

Maybe you have another idea where the problem could be?

And thank you aniway for you help, its nice to have peaple helping!

---

### Post by db-d on 2015-11-29
in this moment i found this bug report. Maybe thats the problem:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1520343?comments=all](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1520343?comments=all)

---

### Post by jeremy31 on 2015-11-29
```
cd /lib/firmware/ath10k/QCA6174/hw3.0
wget https://github.com/FireWalkerX/ath10k-firmware/blob/7e56cbb94182a2fdab110cf5bfeded8fd1d44d30/QCA6174/hw3.0/board-2.bin
```

Reboot

---

### Post by infomorph on 2016-01-04
I fixed this by upgrading my kernel to 4.3.0. Wireless works fine now.

---

