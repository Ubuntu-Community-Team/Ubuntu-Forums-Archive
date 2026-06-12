---
title: "Wireless adapter issues with Qualcomm Atheros [168c:0042] (rev 30)"
date: 2016-03-15
forum: Networking &amp; Wireless
---

### Post by mmccauleyjr on 2016-03-15
I'm a relative novice when it comes to this stuff, so bare with me. I recent bought an Acer E5-574-597Q. I installed a fresh version of ubuntu 14.04 and followed the [guide]("http://askubuntu.com/questions/708061/qualcomm-atheros-device-168c0042-rev-30-wi-fi-driver-installation/708103#708103") posted in a previous thread on how to get my wireless adapter working. Very helpful, but now I've run in to another problem. The wireless network shows up, I can select and connect to it (and I've confirmed that I indeed connected by checking on my router). However I now have two issues:



[LIST]
[*]I can connect, but only have two bars. All my other wireless devices work fine.
[*]Even tho it says I'm connected, and the router says I'm connected, I cannot actually connect to web sites.
[/LIST]

Here's my info using lspci:
```
00:00.0 Host bridge [0600]: Intel Corporation Sky Lake Host Bridge/DRAM   Registers [8086:1904] (rev 08)

00:02.0 VGA compatible controller [0300]: Intel Corporation Sky Lake Integrated Graphics [8086:1916] (rev 07)


00:14.0 USB controller [0c03]: Intel Corporation Device [8086:9d2f] (rev 21)


00:14.2 Signal processing controller [1180]: Intel Corporation Device [8086:9d31] (rev 21)


00:15.0 Signal processing controller [1180]: Intel Corporation Device [8086:9d60] (rev 21)


00:16.0 Communication controller [0780]: Intel Corporation Device [8086:9d3a] (rev 21)


00:17.0 SATA controller [0106]: Intel Corporation Device [8086:9d03] (rev 21)


00:1c.0 PCI bridge [0604]: Intel Corporation Device [8086:9d14] (rev f1)


00:1c.5 PCI bridge [0604]: Intel Corporation Device [8086:9d15] (rev f1)


00:1f.0 ISA bridge [0601]: Intel Corporation Device [8086:9d48] (rev 21)


00:1f.2 Memory controller [0580]: Intel Corporation Device [8086:9d21] (rev 21)


00:1f.3 Audio device [0403]: Intel Corporation Device [8086:9d70] (rev 21)


00:1f.4 SMBus [0c05]: Intel Corporation Device [8086:9d23] (rev 21)


01:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 15)


**02:00.0 Network controller [0280]: Qualcomm Atheros Device [168c:0042] (rev 30)**
```
----------------------------------------------------------------------------------------------------------------
and I also did a discover and got conflicting results:
```
**168c 0042 unknown unknown**

10ec 8168 Realtek Semiconductor Co., Ltd. RTL8111/8168 PCI Express Gigabit Ethernet controller 


10ec 8168 Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller 


10ec 8168 Realtek Semiconductor Co., Ltd. RTL8111/8168 PCI Express Gigabit Ethernet controller 


10ec 8168 Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller 


10ec 8168 Realtek Semiconductor Co., Ltd. RTL8111/8168 PCI Express Gigabit Ethernet controller 


10ec 8168 Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller 


10ec 8168 Realtek Semiconductor Co., Ltd. RTL8111/8168 PCI Express Gigabit Ethernet controller 


10ec 8168 Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller 


10ec 8168 Realtek Semiconductor Co., Ltd. RTL8111/8168 PCI Express Gigabit Ethernet controller 
```
------------------------------------------------------------------------------------------------
finally I did a lspci -C network to see if the card was recognized:
```
*-network

description: Wireless interface


product: Qualcomm Atheros


vendor: Qualcomm Atheros


physical id: 0


bus info: pci@0000:02:00.0


logical name: wlan0


version: 30


serial: 30:52:cb:44:d9:81


width: 64 bits


clock: 33MHz


capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath10k_pci driverversion=4.2.0-30-generic firmware=WLAN.TF.1.0-00267-1 ip=192.168.0.12 latency=0 link=yes multicast=yes wireless=IEEE 802.11abgn


resources: irq:130 memory:a1000000-a11fffff
```
--------------------------------------------------------------------------------
I also did a dmesg to see if there were any issues with the ath10k drivers I installed:

```
[   11.491799] ath10k_pci 0000:02:00.0: pci irq msi-x interrupts 8 irq_mode 0 reset_mode 0

**[   11.777472] ath10k_pci 0000:02:00.0: Direct firmware load for ath10k/cal-pci-0000:02:00.0.bin failed with error -2**


[   13.874911] ath10k_pci 0000:02:00.0: qca9377 hw1.0 (0x05020000, 0x003820ff sub 11ad:0806) fw WLAN.TF.1.0-00267-1 fwapi 5 bdapi 2 htt-ver 3.1 wmi-op 4 htt-op 3 cal otp max-sta 32 raw 0 hwcrypto 1 features ignore-otp


[   13.874915] ath10k_pci 0000:02:00.0: debug 1 debugfs 1 tracing 0 dfs 0 testmode 0


01:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 15)
Subsystem: Acer Incorporated [ALI] Device [1025:100c]
Kernel driver in use: r8169


02:00.0 Network controller [0280]: Qualcomm Atheros Device [168c:0042] (rev 30)
Subsystem: Lite-On Communications Inc Device [11ad:0806]
Kernel driver in use: ath10k_pci

```

I should add, that in the guide I posted, I also did the last bit and used the 4.4.2 kernel that was suggested if I got slow speeds.


I know that's a lot to read, and I appreciate any help and input on the matter.

---

### Post by jeremy31 on 2016-03-15
Run the wireless scrip
```
wget -N -t 5 -T 10 https://github.com/UbuntuForums/wireless-info/raw/master/wireless-info && chmod +x wireless-info && ./wireless-info
```

Post the contents or the wireless-info.**txt** file

---

### Post by mmccauleyjr on 2016-03-15
```

########## wireless info START ##########

Report from: 15 Mar 2016 13:14 EDT -0400

Booted last: 15 Mar 2016 12:52 EDT -0400

Script from: 27 Sep 2015 00:34 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.4 LTS
Release:    14.04
Codename:    trusty

##### kernel ############################

Linux 4.2.0-30-generic #36~14.04.1-Ubuntu SMP Fri Feb 26 18:49:23 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Ubuntu

##### lspci #############################

01:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 15)
    Subsystem: Acer Incorporated [ALI] Device [1025:100c]
    Kernel driver in use: r8169

02:00.0 Network controller [0280]: Qualcomm Atheros Device [168c:0042] (rev 30)
    Subsystem: Lite-On Communications Inc Device [11ad:0806]
    Kernel driver in use: ath10k_pci

##### lsusb #############################

Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 004: ID 0bda:0129 Realtek Semiconductor Corp. RTS5129 Card Reader Controller
Bus 001 Device 003: ID 04f2:b51f Chicony Electronics Co., Ltd 
Bus 001 Device 002: ID 04ca:3015 Lite-On Technology Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
1: acer-wireless: Wireless LAN
    Soft blocked: no
    Hard blocked: no
2: acer-bluetooth: Bluetooth
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
video                  40960  2 i915,acer_wmi

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

eth0      Link encap:Ethernet  HWaddr <MAC 'eth0' [IF]>  
          inet addr:192.168.0.14  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fd00:bc4d:fb9f:80c2:<IP6 'eth0' [IF]>/64 Scope:Global
          inet6 addr: fe80::<IP6 'eth0' [IF]>/64 Scope:Link
          inet6 addr: fd00:bc4d:fb9f:80c2:348e:81da:6c8e:5cff/64 Scope:Global
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:437 errors:0 dropped:0 overruns:0 frame:0
          TX packets:156 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:67437 (67.4 KB)  TX bytes:21633 (21.6 KB)

wlan0     Link encap:Ethernet  HWaddr <MAC 'wlan0' [IF]>  
          inet6 addr: fe80::<IP6 'wlan0' [IF]>/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:304 errors:0 dropped:0 overruns:0 frame:0
          TX packets:743 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:109457 (109.4 KB)  TX bytes:100593 (100.5 KB)

##### iwconfig ##########################

eth0      no wireless extensions.

lo        no wireless extensions.

wlan0     IEEE 802.11abgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.0.1     0.0.0.0         UG    0      0        0 eth0
192.168.0.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0

##### resolv.conf #######################

nameserver 127.0.1.1
search hitronhub.home

##### network managers ##################

Installed:

    NetworkManager

Running:

root       786     1  0 12:52 ?        00:00:02 NetworkManager

##### NetworkManager info ###############

NetworkManager Tool

State: connected (global)

- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            ath10k_pci
  State:             disconnected
  Default:           no
  HW Address:        <MAC 'wlan0' [IF]>

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 

- Device: eth0  [Wired connection 1] -------------------------------------------
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
    Address:         192.168.0.14
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.0.1

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

[[/etc/NetworkManager/system-connections/Rogers01318]] (600 root)
[connection] id=Rogers01318 | type=802-11-wireless
[802-11-wireless] ssid=Rogers01318 | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Rogers01318-5G]] (600 root)
[connection] id=Rogers01318-5G | type=802-11-wireless
[802-11-wireless] ssid=Rogers01318-5G | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

##### iw reg get ########################

Region: America/Toronto (based on set time zone)

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

lo        Interface doesn't support scanning.

Channel occupancy:

      1   APs on   Frequency:2.412 GHz (Channel 1)
      1   APs on   Frequency:5.765 GHz

wlan0     Scan completed :
          Cell 01 - Address: <MAC 'Rogers01318' [AC1]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=30/70  Signal level=-80 dBm  
                    Encryption key:on
                    ESSID:"Rogers01318"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000238f61a180
                    Extra: Last beacon: 4720ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC 'Rogers01318-5G' [AC2]>
                    Channel:153
                    Frequency:5.765 GHz
                    Quality=31/70  Signal level=-79 dBm  
                    Encryption key:on
                    ESSID:"Rogers01318-5G"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000023915be03b
                    Extra: Last beacon: 576ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK

##### module infos ######################

[ath10k_pci]
filename:       /lib/modules/4.2.0-30-generic/updates/drivers/net/wireless/ath/ath10k/ath10k_pci.ko
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
version:        backported from Linux (v4.4.2-0-g1cb8570) using backports v4.4.2-1-0-gbec4037
srcversion:     EBB3D4E36DE49B7EC8057D0
depends:        ath10k_core,compat
vermagic:       4.2.0-30-generic SMP mod_unload modversions 
parm:           irq_mode:0: auto, 1: legacy, 2: msi (default: 0) (uint)
parm:           reset_mode:0: auto, 1: warm only (default: 0) (uint)

[ath10k_core]
filename:       /lib/modules/4.2.0-30-generic/updates/drivers/net/wireless/ath/ath10k/ath10k_core.ko
license:        Dual BSD/GPL
description:    Core module for QCA988X PCIe devices.
author:         Qualcomm Atheros
srcversion:     27000DBD292A446A6D969C2
depends:        mac80211,cfg80211,ath
vermagic:       4.2.0-30-generic SMP mod_unload modversions 
parm:           debug_mask:Debugging mask (uint)
parm:           uart_print:Uart target debugging (bool)
parm:           skip_otp:Skip otp failure for calibration in testmode (bool)
parm:           cryptmode:Crypto mode: 0-hardware, 1-software (uint)
parm:           rawmode:Use raw 802.11 frame datapath (bool)

[ath]
filename:       /lib/modules/4.2.0-30-generic/updates/drivers/net/wireless/ath/ath.ko
license:        Dual BSD/GPL
description:    Shared library for Atheros wireless LAN cards.
author:         Atheros Communications
srcversion:     6A988397A204F65CDF45A3C
depends:        cfg80211
vermagic:       4.2.0-30-generic SMP mod_unload modversions 

[mac80211]
filename:       /lib/modules/4.2.0-30-generic/updates/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
version:        backported from Linux (v4.4.2-0-g1cb8570) using backports v4.4.2-1-0-gbec4037
srcversion:     E7DE97DC420ABD89A9888A8
depends:        cfg80211,compat
vermagic:       4.2.0-30-generic SMP mod_unload modversions 
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[cfg80211]
filename:       /lib/modules/4.2.0-30-generic/updates/net/wireless/cfg80211.ko
version:        backported from Linux (v4.4.2-0-g1cb8570) using backports v4.4.2-1-0-gbec4037
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     5C90ABE0CCC4BAA64E8582A
depends:        compat
vermagic:       4.2.0-30-generic SMP mod_unload modversions 
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
# PCI device 0x168c:0x0042 (ath10k_pci)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

##### dmesg #############################

[   17.280528] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   23.194791] wlan0: authenticate with <MAC 'Rogers01318-5G' [AC2]>
[   23.226242] wlan0: send auth to <MAC 'Rogers01318-5G' [AC2]> (try 1/3)
[   23.226844] wlan0: authenticated
[   23.228269] wlan0: associate with <MAC 'Rogers01318-5G' [AC2]> (try 1/3)
[   23.229721] wlan0: RX AssocResp from <MAC 'Rogers01318-5G' [AC2]> (capab=0x411 status=0 aid=2)
[   23.231729] wlan0: associated
[   23.231797] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   23.618331] wlan0: Limiting TX power to 27 (30 - 3) dBm as advertised by <MAC 'Rogers01318-5G' [AC2]>
[   23.619071] ath: EEPROM regdomain: 0x8348
[   23.619075] ath: EEPROM indicates we should expect a country code
[   23.619077] ath: doing EEPROM country->regdmn map search
[   23.619079] ath: country maps to regdmn code: 0x3a
[   23.619081] ath: Country alpha2 being used: US
[   23.619082] ath: Regpair used: 0x3a
[   23.619084] ath: regdomain 0x8348 dynamically updated by country IE
[  603.187904] wlan0: deauthenticating from <MAC 'Rogers01318-5G' [AC2]> by local choice (Reason: 3=DEAUTH_LEAVING)
[  608.196578] ath10k_pci 0000:02:00.0: failed to flush transmit queue (skip 0 ar-state 1): 0
[  612.966229] wlan0: authenticate with <MAC 'Rogers01318' [AC1]>
[  613.006730] wlan0: send auth to <MAC 'Rogers01318' [AC1]> (try 1/3)
[  613.010015] wlan0: authenticated
[  613.012428] wlan0: associate with <MAC 'Rogers01318' [AC1]> (try 1/3)
[  613.025735] wlan0: RX AssocResp from <MAC 'Rogers01318' [AC1]> (capab=0x431 status=0 aid=1)
[  613.028370] wlan0: associated
[  613.036678] ath: EEPROM regdomain: 0x8348
[  613.036690] ath: EEPROM indicates we should expect a country code
[  613.036698] ath: doing EEPROM country->regdmn map search
[  613.036704] ath: country maps to regdmn code: 0x3a
[  613.036710] ath: Country alpha2 being used: US
[  613.036716] ath: Regpair used: 0x3a
[  613.036724] ath: regdomain 0x8348 dynamically updated by country IE
[  910.160569] wlan0: deauthenticated from <MAC 'Rogers01318' [AC1]> (Reason: 6=CLASS2_FRAME_FROM_NONAUTH_STA)
[  991.702314] r8169 0000:01:00.0 eth0: link up
[  991.702347] IPv6: ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[ 1345.275735] wlan0: authenticate with <MAC 'Rogers01318-5G' [AC2]>
[ 1345.307339] wlan0: send auth to <MAC 'Rogers01318-5G' [AC2]> (try 1/3)
[ 1345.307993] wlan0: authenticated
[ 1345.310710] wlan0: associate with <MAC 'Rogers01318-5G' [AC2]> (try 1/3)
[ 1345.313210] wlan0: RX AssocResp from <MAC 'Rogers01318-5G' [AC2]> (capab=0x411 status=0 aid=2)
[ 1345.315631] wlan0: associated
[ 1345.324220] wlan0: deauthenticating from <MAC 'Rogers01318-5G' [AC2]> by local choice (Reason: 2=PREV_AUTH_NOT_VALID)
[ 1345.331335] wlan0: authenticate with <MAC 'Rogers01318-5G' [AC2]>
[ 1345.362703] wlan0: send auth to <MAC 'Rogers01318-5G' [AC2]> (try 1/3)
[ 1345.365692] wlan0: send auth to <MAC 'Rogers01318-5G' [AC2]> (try 2/3)
[ 1345.367124] wlan0: send auth to <MAC 'Rogers01318-5G' [AC2]> (try 3/3)
[ 1345.368513] wlan0: authentication with <MAC 'Rogers01318-5G' [AC2]> timed out

########## wireless info END ############


```

Note worthy, my wireless disconnected, and even if it didn't I wouldn't be able to resolve the host to use wget. Had to use wired.

---

### Post by jeremy31 on 2016-03-15
A couple things stand out, you wireless networks are using a TKIP enabled mixed mode encryption, see if you can change it to WPA2 only with no TKIP, it may be called compatibility mode

The second is that power management is enabled on the wireless ```
sudo iwconfig wlan0 power off
```

It wouldn't hurt to edit the connections in Network Manager and set the IPv6 to ignore and set the country code, it appears you are in Canada so ```
sudo iw reg set CA
```

---

### Post by mmccauleyjr on 2016-03-15
> **jeremy31 said:**
> A couple things stand out, you wireless networks are using a TKIP enabled mixed mode encryption, see if you can change it to WPA2 only with no TKIP, it may be called compatibility mode

The second is that power management is enabled on the wireless ```
sudo iwconfig wlan0 power off
```

It wouldn't hurt to edit the connections in Network Manager and set the IPv6 to ignore and set the country code, it appears you are in Canada so ```
sudo iw reg set CA
```


Hey, thanks for the help. I did what you mentioned , and unfortunately no guano. It worked for a few minutes and then I the connection got dropped. Currently I have my router set to WPA/WPA2 personal, with AES encryption (there are no options for changing encryption).

While looking at my wireless clients connecting to the router I got the following:

[computername]l-Aspire-E5-574	[mac:address]	1	-10dBm	1Mbps	11NGHT20	Channel: 6) 	20MHz
iPad	[mac:address]	1	-35dBm	300Mbps	11ACVHT80	  (Channel: 36)	80MHz

---

### Post by jeremy31 on 2016-03-15
Can you choose just WPA2 Personal on the router.  In the Network Manager settings under General for your connections, is Automatically connect checked for both networks as that may allow it to roam from 2GHz to 5GHz

---

### Post by mmccauleyjr on 2016-03-15
Router doesn't let me choose wpa2-personal. security mode is stuck at wpa-personal (it's an isp router). changing the auth mode to wpa2-psk or wpa-psk doesn't work (wpa-psk seems to disagree with apple devices). I have automatically connected checked for both networks (but I unchecked it for 5g to see if whether or not it would effect anything).

---

