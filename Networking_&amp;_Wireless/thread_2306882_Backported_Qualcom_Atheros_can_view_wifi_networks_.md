---
title: "Backported Qualcom Atheros can view wifi networks but cannot connect"
date: 2015-12-19
forum: Networking &amp; Wireless
---

### Post by ananori99 on 2015-12-19
I have a Lenovo U31-70 that I recently purchased and installed Ubuntu 15.10 onto, after removing Windows 10. Out of the box, wifi on Ubuntu did not work- but with the solution decrbed it post #74 of bug  #1436940.
 This solution use file from [https://www.kernel.org/pub/linux/kernel/projects/backports/2015/09/03/backports-20150903.tar.gz](https://www.kernel.org/pub/linux/kernel/projects/backports/2015/09/03/backports-20150903.tar.gz)
 and
 [https://github.com/atondwal/ath10k-firmware.git](https://github.com/atondwal/ath10k-firmware.git)
 After doing this the wifi (and my ability to connect to secured networks I had the password for) worked perfectly.
 The last day I used the laptops wifi and it worked was the 13[SUP]th[/SUP] of December.
 I did not try to use it again until the 16[SUP]th[/SUP] . I had selected all updates to be done.
 Then on the 16[SUP]th[/SUP] when I did try to use it, I had the problem that I could see wifi networks and their details, but the buttons in network-manager-gnome (save, connect) are “grayed out” and do not permit me to click on them…
 
 
 I have tried reinstalling Ubuntu 15.10 (from the original thumb-drive) and applying the back port, I still could not click connect.
 I have purged and reinstalled network-manager-gnome, did not work.
 Have done update and dist-upgrade.
 The things that other 15.10 users could do to get network-manager-gnome to work for them had no effect for me, and I am wondering if my back ports and atheros could be the reason?  
 
 
 Here is the output of the wireless script, I'm not really used to Ubuntu and don't know about networking-
 so if it turns out there's an obvious reason for this, sorry.
 
 
 As another bit of info, I just tried to connect with wicd network manager, and it can see the networks and save the passwords- but when told to connect, it'll spend a long time saying “authenticating password” and then just stop and say bad password. I checked with my wifi, so I know I gave the right encryption and password.


```
 


########## wireless info START ##########

Report from: 18 Dec 2015 21:55 CST -0600

Booted last: 18 Dec 2015 00:00 CST -0600

Script from: 27 Sep 2015 00:34 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 15.10
Release:    15.10
Codename:    wily

##### kernel ############################

Linux 4.2.0-22-generic #27-Ubuntu SMP Thu Dec 17 22:57:08 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Ubuntu

##### lspci #############################

02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 15)
    Subsystem: Lenovo Device [17aa:3828]
    Kernel driver in use: r8169

03:00.0 Network controller [0280]: Qualcomm Atheros Device [168c:0041] (rev 20)
    Subsystem: Lenovo Device [17aa:3545]
    Kernel driver in use: ath10k_pci

##### lsusb #############################

Bus 003 Device 002: ID 8087:8001 Intel Corp. 
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 004: ID 0cf3:e300 Atheros Communications, Inc. 
Bus 001 Device 003: ID 5986:0670 Acer, Inc 
Bus 001 Device 002: ID 0bda:0129 Realtek Semiconductor Corp. RTS5129 Card Reader Controller
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: ideapad_wlan: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: ideapad_bluetooth: Bluetooth
    Soft blocked: yes
    Hard blocked: no
2: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
3: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

##### lsmod #############################

ath10k_pci             45056  0
ath10k_core           278528  1 ath10k_pci
snd_soc_rt286          40960  0
snd_soc_rl6347a        16384  1 snd_soc_rt286
ath                    32768  1 ath10k_core
snd_soc_core          200704  1 snd_soc_rt286
mac80211              638976  1 ath10k_core
snd_pcm               106496  7 snd_soc_core,snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel,snd_soc_rt286,snd_pcm_dmaengine,snd_hda_core
cfg80211              540672  3 ath,mac80211,ath10k_core
compat                 16384  3 cfg80211,mac80211,ath10k_pci
ideapad_laptop         24576  0
sparse_keymap          16384  1 ideapad_laptop
wmi                    20480  0
video                  36864  2 i915,ideapad_laptop

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

enp2s0    Link encap:Ethernet  HWaddr <MAC 'enp2s0' [IF]>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wlp3s0    Link encap:Ethernet  HWaddr <MAC 'wlp3s0' [IF]>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

##### iwconfig ##########################

enp2s0    no wireless extensions.

lo        no wireless extensions.

wlp3s0    IEEE 802.11abgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=0 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface

##### resolv.conf #######################

##### network managers ##################

Installed:

    NetworkManager

Running:

root       630     1  0 21:40 ?        00:00:01 /usr/sbin/NetworkManager --no-daemon

##### NetworkManager info ###############

GENERAL.DEVICE:                         wlp3s0
GENERAL.TYPE:                           wifi
GENERAL.NM-TYPE:                        NMDeviceWifi
GENERAL.VENDOR:                         Qualcomm Atheros
GENERAL.PRODUCT:                        Wildcat Point-LP PCI Express Root Port
GENERAL.DRIVER:                         ath10k_pci
GENERAL.DRIVER-VERSION:                 4.2.0-22-generic
GENERAL.FIRMWARE-VERSION:               atheros-12.0.0.102-fw
GENERAL.HWADDR:                         <MAC 'wlp3s0' [IF]>
GENERAL.MTU:                            0
GENERAL.STATE:                          30 (disconnected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.3/0000:03:00.0/net/wlp3s0
GENERAL.IP-IFACE:                       
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     --
GENERAL.CON-UUID:                       --
GENERAL.CON-PATH:                       --
CAPABILITIES.CARRIER-DETECT:            no
CAPABILITIES.SPEED:                     unknown
CAPABILITIES.IS-SOFTWARE:               no
WIFI-PROPERTIES.WEP:                    yes
WIFI-PROPERTIES.WPA:                    yes
WIFI-PROPERTIES.WPA2:                   yes
WIFI-PROPERTIES.TKIP:                   yes
WIFI-PROPERTIES.CCMP:                   yes
WIFI-PROPERTIES.AP:                     yes
WIFI-PROPERTIES.ADHOC:                  yes
WIFI-PROPERTIES.2GHZ:                   yes
WIFI-PROPERTIES.5GHZ:                   yes
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{0}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   1a688ec0-8007-4c35-ad54-743eb3db4524 | TURBONETT_15AA70

GENERAL.DEVICE:                         enp2s0
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Realtek Semiconductor Co., Ltd.
GENERAL.PRODUCT:                        RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
GENERAL.DRIVER:                         r8169
GENERAL.DRIVER-VERSION:                 2.3LK-NAPI
GENERAL.FIRMWARE-VERSION:               
GENERAL.HWADDR:                         <MAC 'enp2s0' [IF]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          20 (unavailable)
GENERAL.REASON:                         2 (Device is now managed)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.2/0000:02:00.0/net/enp2s0
GENERAL.IP-IFACE:                       
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     --
GENERAL.CON-UUID:                       --
GENERAL.CON-PATH:                       --
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     unknown
CAPABILITIES.IS-SOFTWARE:               no
WIRED-PROPERTIES.CARRIER:               off
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: 

SSID              BSSID              MODE   CHAN  FREQ      RATE       SIGNAL  BARS  SECURITY   ACTIVE  * 
--                <MAC '' [AC3]>  Infra  9     2452 MHz  54 Mbit/s  37      &#9602;&#9604;__  WPA1 WPA2  no        
--                <MAC '' [AC4]>  Infra  9     2452 MHz  54 Mbit/s  37      &#9602;&#9604;__  WPA1 WPA2  no        
TURBONETT_15AA70  <MAC 'TURBONETT_15AA70' [AC1]>  Infra  1     2412 MHz  54 Mbit/s  62      &#9602;&#9604;&#9606;_  WEP        no        
TEJADA_TURBONETT  <MAC 'TEJADA_TURBONETT' [AC2]>  Infra  9     2452 MHz  54 Mbit/s  40      &#9602;&#9604;__  WEP        no        

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

[[/etc/NetworkManager/system-connections/TURBONETT_15AA70~]] (600 root)
[connection] id=TURBONETT_15AA70 | type=wifi | permissions=
[wifi] mac-address=<MAC 'wlp3s0' [IF]> | mac-address-blacklist= | ssid=TURBONETT_15AA70
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/TURBONETT_15AA70]] (600 root)
[connection] id=TURBONETT_15AA70 | type=wifi | permissions=
[wifi] mac-address=<MAC 'wlp3s0' [IF]> | mac-address-blacklist= | ssid=TURBONETT_15AA70
[ipv4] method=auto
[ipv6] method=auto

##### iw reg get ########################

Region: America/El_Salvador (based on set time zone)

country 00: DFS-UNSET
    (2402 - 2472 @ 40), (N/A, 20), (N/A)
    (2457 - 2482 @ 40), (N/A, 20), (N/A), NO-IR
    (2474 - 2494 @ 20), (N/A, 20), (N/A), NO-OFDM, NO-IR
    (5170 - 5250 @ 80), (N/A, 20), (N/A), NO-IR
    (5250 - 5330 @ 80), (N/A, 20), (0 ms), DFS, NO-IR
    (5490 - 5730 @ 160), (N/A, 20), (0 ms), DFS, NO-IR
    (5735 - 5835 @ 80), (N/A, 20), (N/A), NO-IR
    (57240 - 63720 @ 2160), (N/A, 0), (N/A)

##### iwlist channels ###################

enp2s0    no frequency information.

lo        no frequency information.

wlp3s0    32 channels in total; available frequencies :
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

enp2s0    Interface doesn't support scanning.

lo        Interface doesn't support scanning.

Channel occupancy:

      1   APs on   Frequency:2.412 GHz (Channel 1)
      4   APs on   Frequency:2.452 GHz (Channel 9)

wlp3s0    Scan completed :
          Cell 01 - Address: <MAC 'TURBONETT_15AA70' [AC1]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=45/70  Signal level=-65 dBm  
                    Encryption key:on
                    ESSID:"TURBONETT_15AA70"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000585db1d5d
                    Extra: Last beacon: 80ms ago
          Cell 02 - Address: <MAC 'TEJADA_TURBONETT' [AC2]>
                    Channel:9
                    Frequency:2.452 GHz (Channel 9)
                    Quality=34/70  Signal level=-76 dBm  
                    Encryption key:on
                    ESSID:"TEJADA_TURBONETT"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000007e133302db0
                    Extra: Last beacon: 80ms ago
          Cell 03 - Address: <MAC '' [AC3]>
                    Channel:9
                    Frequency:2.452 GHz (Channel 9)
                    Quality=32/70  Signal level=-78 dBm  
                    Encryption key:on
                    ESSID:""
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000007e133314098
                    Extra: Last beacon: 4256ms ago
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 04 - Address: <MAC '' [AC4]>
                    Channel:9
                    Frequency:2.452 GHz (Channel 9)
                    Quality=32/70  Signal level=-78 dBm  
                    Encryption key:on
                    ESSID:""
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000007e1333136b6
                    Extra: Last beacon: 4260ms ago
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 05 - Address: <MAC '' [AC5]>
                    Channel:9
                    Frequency:2.452 GHz (Channel 9)
                    Quality=34/70  Signal level=-76 dBm  
                    Encryption key:on
                    ESSID:""
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000007e133314a7b
                    Extra: Last beacon: 4256ms ago
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK

##### module infos ######################

[ath10k_pci]
filename:       /lib/modules/4.2.0-22-generic/updates/drivers/net/wireless/ath/ath10k/ath10k_pci.ko
firmware:       ath10k/QCA6174/hw3.0/board.bin
firmware:       ath10k/QCA6174/hw3.0/firmware-5.bin
firmware:       ath10k/QCA6174/hw3.0/firmware-4.bin
firmware:       ath10k/QCA6174/hw2.1/board.bin
firmware:       ath10k/QCA6174/hw2.1/firmware-5.bin
firmware:       ath10k/QCA6174/hw2.1/firmware-4.bin
firmware:       ath10k/QCA988X/hw2.0/board.bin
firmware:       ath10k/QCA988X/hw2.0/firmware-5.bin
firmware:       ath10k/QCA988X/hw2.0/firmware-4.bin
firmware:       ath10k/QCA988X/hw2.0/firmware-3.bin
firmware:       ath10k/QCA988X/hw2.0/firmware-2.bin
firmware:       ath10k/QCA988X/hw2.0/firmware.bin
license:        Dual BSD/GPL
description:    Driver support for Atheros QCA988X PCIe devices
author:         Qualcomm Atheros
version:        backported from Linux (next-20150903-0-ga672f92) using backports backports-20150903-0-g7b34ea2
srcversion:     2C3D5FA5797C89E8231F86B
depends:        ath10k_core,compat
vermagic:       4.2.0-22-generic SMP mod_unload modversions 
parm:           irq_mode:0: auto, 1: legacy, 2: msi (default: 0) (uint)
parm:           reset_mode:0: auto, 1: warm only (default: 0) (uint)

[ath10k_core]
filename:       /lib/modules/4.2.0-22-generic/updates/drivers/net/wireless/ath/ath10k/ath10k_core.ko
license:        Dual BSD/GPL
description:    Core module for QCA988X PCIe devices.
author:         Qualcomm Atheros
srcversion:     2CEAB76811A0B05C303317D
depends:        mac80211,cfg80211,ath
vermagic:       4.2.0-22-generic SMP mod_unload modversions 
parm:           debug_mask:Debugging mask (uint)
parm:           uart_print:Uart target debugging (bool)
parm:           skip_otp:Skip otp failure for calibration in testmode (bool)
parm:           cryptmode:Crypto mode: 0-hardware, 1-software (uint)

[ath]
filename:       /lib/modules/4.2.0-22-generic/updates/drivers/net/wireless/ath/ath.ko
license:        Dual BSD/GPL
description:    Shared library for Atheros wireless LAN cards.
author:         Atheros Communications
srcversion:     599C4ECEE9D167A7F2EDD5C
depends:        cfg80211
vermagic:       4.2.0-22-generic SMP mod_unload modversions 

[mac80211]
filename:       /lib/modules/4.2.0-22-generic/updates/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
version:        backported from Linux (next-20150903-0-ga672f92) using backports backports-20150903-0-g7b34ea2
srcversion:     BEF453E7AC487F911F8EDBF
depends:        cfg80211,compat
vermagic:       4.2.0-22-generic SMP mod_unload modversions 
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[cfg80211]
filename:       /lib/modules/4.2.0-22-generic/updates/net/wireless/cfg80211.ko
version:        backported from Linux (next-20150903-0-ga672f92) using backports backports-20150903-0-g7b34ea2
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     F6775E4370E54D5795E4BE2
depends:        compat
vermagic:       4.2.0-22-generic SMP mod_unload modversions 
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

##### module parameters #################

[ath10k_pci]
irq_mode: 0
reset_mode: 0

[ath10k_core]
cryptmode: 0
debug_mask: 0
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

[/etc/modprobe.d/intel-microcode-blacklist.conf]
blacklist microcode

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

grep: /etc/udev/rules.d/*net*.rules: No such file or directory

##### dmesg #############################

[   27.146851] IPv6: ADDRCONF(NETDEV_UP): enp2s0: link is not ready
[   27.262923] r8169 0000:02:00.0 enp2s0: link down
[   27.262962] IPv6: ADDRCONF(NETDEV_UP): enp2s0: link is not ready
[   27.265515] IPv6: ADDRCONF(NETDEV_UP): wlp3s0: link is not ready (repeated 5 times)
[  606.351589] ath10k_pci 0000:03:00.0: no channel configured; ignoring frame(s)!

########## wireless info END ############



```

---

### Post by jeremy31 on 2015-12-20
Can you post the result of ```
ls [COLOR=#333333][FONT=monospace]/lib/firmware/[/FONT][/COLOR][COLOR=#333333][FONT=monospace]ath10k/[/FONT][/COLOR][COLOR=#333333][FONT=monospace]QCA6174/[/FONT][/COLOR][COLOR=#333333][FONT=monospace]hw2.1; dmesg | grep ath10k
```[/FONT][/COLOR]

---

### Post by ananori99 on 2015-12-20
Thanks for taking the time,
 here it is:


```

ana@mini-mu:~$ ls /lib/firmware/ath10k/QCA6174/hw2.1
board.bin  firmware-5.bin  notice_ath10k_firmware-5.txt
ana@mini-mu:~$ dmesg | grep ath10k
[   13.813006] ath10k_pci 0000:03:00.0: pci irq msi-x interrupts 8 irq_mode 0 reset_mode 0
[   14.084121] ath10k_pci 0000:03:00.0: Direct firmware load for ath10k/cal-pci-0000:03:00.0.bin failed with error -2
[   14.130141] ath10k_pci 0000:03:00.0: Direct firmware load for ath10k/QCA6174/hw2.1/board-pci-168c:0041:17aa:3545.bin failed with error -2
[   14.130158] ath10k_pci 0000:03:00.0: failed to load spec board file, falling back to generic: -2
[   15.633718] ath10k_pci 0000:03:00.0: qca6174 hw2.1 (0x05010000, 0x003405ff, 168c:0041:17aa:3545 fallback) fw atheros-12.0.0.102-fw api 5 htt-ver 3.25 wmi-op 4 htt-op 3 cal otp max-sta 32 raw 0 hwcrypto 1 features 
[   15.633723] ath10k_pci 0000:03:00.0: debug 1 debugfs 1 tracing 0 dfs 0 testmode 0
[   15.814778] ath10k_pci 0000:03:00.0 wlp3s0: renamed from wlan0
[   42.277570] ath10k_pci 0000:03:00.0: no channel configured; ignoring frame(s)!
[   42.641500] ath10k_pci 0000:03:00.0: no channel configured; ignoring frame(s)!
[  135.351587] ath10k_pci 0000:03:00.0: no channel configured; ignoring frame(s)!
[  135.715536] ath10k_pci 0000:03:00.0: no channel configured; ignoring frame(s)!
[  135.819648] ath10k_pci 0000:03:00.0: no channel configured; ignoring frame(s)!
ana@mini-mu:~$ 

```

---

### Post by jeremy31 on 2015-12-20
I would try uninstalling the current backports
```
cd backports-20150903
sudo make uninstall
```

Reboot

Then ```
wget https://www.kernel.org/pub/linux/kernel/projects/backports/2015/12/03/backports-20151203.tar.gz
tar -zxvf backports-20151203.tar.gz
cd backports-20151203
make defconfig-ath10k
make
sudo make install
```

Reboot

---

### Post by ananori99 on 2015-12-20
Hi, thank you.

That didn't work, however at the stage of typing "make defconfig ath-10k" warnings for missing prototypes and "can't find defconfig/ath10k" came up.

So after that, for "make" I did an option "make oldconfig" in which I choose all ath options as install.

My wifi card couldn't be detected after reboot, 
however when I opened hw.c in the ath sub folder of backports, it has qca6174 but not 6164... So maybe that's why?
I'm kind of tempted to cut and paste a 6164 in.

I'll try and rerun and post the error stuff when I get to an Ethernet tomorrow...
Thanks for helping

---

### Post by jeremy31 on 2015-12-21
There is much mentioned of QCA6164 in the source code since it looks for firmware in the QCA6174 directory for firmware
Try ```
sudo modprobe ath10k_pci
``` and see if wifi works

---

### Post by ananori99 on 2015-12-21
Not yet, It says 
```

modprobe: ERROR: could not insert 'ath10k_pci' : Exec format error

```

---

### Post by jeremy31 on 2015-12-21
That is the result of old config rather than using defconfig.  You should be able to ```
cd backports-20151203
sudo make uninstall
make clean
make defconfig-wifi
make
sudo make install
```

Reboot

---

### Post by ananori99 on 2015-12-22
hi, again thanks for helping.
the defconfig options it lets me chose from don't include just wifi, they are

```


  	 	 	 	   ana@mini-mu:~/backports-20151203$ make defconfig-wifi
 Generating local configuration database from kernel ... done.
 cc -Wall -Wmissing-prototypes -Wstrict-prototypes -O2 -fomit-frame-pointer   -c -o conf.o conf.c
 cc -Wall -Wmissing-prototypes -Wstrict-prototypes -O2 -fomit-frame-pointer   -c -o zconf.tab.o zconf.tab.c
 cc   conf.o zconf.tab.o   -o conf
 boolean symbol HWMON tested for 'm'? test forced to 'n'
 boolean symbol HWMON tested for 'm'? test forced to 'n'
 ***
 *** Can't find default configuration "defconfigs/wifi"!
 ***
 Makefile.real:41: recipe for target 'defconfig-wifi' failed
 make[1]: *** [defconfig-wifi] Error 1
 Makefile:40: recipe for target 'defconfig-wifi' failed
 make: *** [defconfig-wifi] Error 2
 ana@mini-mu:~/backports-20151203$ 
 
 
 
 
 
 
 
 
 ana@mini-mu:~/backports-20151203$ make
 /--------------
 | Your backport package isn't configured, please configure it
 | using one of the following options:
 | To configure manually:
 |     make oldconfig
 |     make menuconfig
 |
 | To get defaults for certain drivers:
 |     make defconfig-alx
 |     make defconfig-b43
 |     make defconfig-b43legacy
 |     make defconfig-brcmfmac
 |     make defconfig-brcmsmac
 |     make defconfig-cw1200
 |     make defconfig-hwsim
 |     make defconfig-ieee802154
 |     make defconfig-igb
 |     make defconfig-iwlwifi
 |     make defconfig-media
 |     make defconfig-nfc
 |     make defconfig-rtlwifi
 |     make defconfig-wwan
 \--
 Makefile.real:45: recipe for target '.config' failed
 make[2]: *** [.config] Error 1
 Makefile:40: recipe for target 'modules' failed
 make[1]: *** [modules] Error 2
 Makefile:30: recipe for target 'default' failed
 make: *** [default] Error 2
 ana@mini-mu:~/backports-20151203$ 
 
 
 
 
  

```

I tried iwlwifi and rtlwifi
where :

```


  	 	 	 	   modprobe: ERROR: could not insert 'ath10k_pci': Invalid argument
  

```

could there be a problem with my downloaded version, is there another source?

Thanks again

---

### Post by jeremy31 on 2015-12-22
I just looked at those backports earlier and noticed that the ath10k and wifi defconfigs files missing, so I checked others and this is the latest available with ath10k support.  It is strange that those options are missing

```
wget https://www.kernel.org/pub/linux/kernel/projects/backports/stable/v4.3/backports-4.3-1.tar.gz
tar -zxvf backports-4.3-1.tar.gz
cd backports-4.3-1
make defconfig-ath10k
make
sudo make install
```

---

### Post by ananori99 on 2015-12-28
Hasn't worked yet, but dmsg gives this:

```

dmesg | grep ath
[   23.743698] ath10k_pci 0000:03:00.0: pci irq msi-x interrupts 8 irq_mode 0 reset_mode 0
[   24.016849] ath10k_pci 0000:03:00.0: Direct firmware load for ath10k/cal-pci-0000:03:00.0.bin failed with error -2
[   24.036754] ath10k_pci 0000:03:00.0: Direct firmware load for ath10k/QCA6174/hw2.1/board-pci-168c:0041:17aa:3545.bin failed with error -2
[   24.036761] ath10k_pci 0000:03:00.0: failed to load spec board file, falling back to generic: -2
[   25.284076] ath10k_pci 0000:03:00.0: firmware crashed! (uuid 625d1ded-caf8-4c44-9d69-0503c4172b10)
[   25.284088] ath10k_pci 0000:03:00.0: qca6174 hw2.1 (0x05010000, 0x003405ff, 168c:0041:17aa:3545 fallback) fw WLAN.RM.1.1-00141 api 5 htt-ver 0.0 wmi-op 4 htt-op 3 cal otp max-sta 32 raw 0 hwcrypto 1 features ignore-otp,no-4addr-pad
[   25.284091] ath10k_pci 0000:03:00.0: debug 1 debugfs 1 tracing 0 dfs 0 testmode 0
[   25.286490] ath10k_pci 0000:03:00.0: firmware register dump:
[   25.286493] ath10k_pci 0000:03:00.0: [00]: 0x05010000 0x000015B3 0x000A012D 0x00955B31
[   25.286495] ath10k_pci 0000:03:00.0: [04]: 0x000A012D 0x00060330 0x00000016 0x88685006
[   25.286497] ath10k_pci 0000:03:00.0: [08]: 0x00000000 0x00400000 0x00400600 0x00000001
[   25.286499] ath10k_pci 0000:03:00.0: [12]: 0x00000009 0x00000000 0x00931C61 0x00931C7D
[   25.286501] ath10k_pci 0000:03:00.0: [16]: 0x0096BDBC 0x009287BD 0x00000000 0x00000000
[   25.286503] ath10k_pci 0000:03:00.0: [20]: 0x400A012D 0x0040E2B0 0x00955A00 0x00404590
[   25.286505] ath10k_pci 0000:03:00.0: [24]: 0x809287D9 0x0040E310 0x7A5087F8 0xC00A012D
[   25.286506] ath10k_pci 0000:03:00.0: [28]: 0x809288D7 0x0040E340 0x00000000 0xFFF08040
[   25.286508] ath10k_pci 0000:03:00.0: [32]: 0x809290FE 0x0040E360 0x00400000 0x00400600
[   25.286510] ath10k_pci 0000:03:00.0: [36]: 0x80929205 0x0040E380 0x00000000 0x00400600
[   25.286513] ath10k_pci 0000:03:00.0: [40]: 0x40928024 0x0040E3B0 0x0040D3D0 0x0040D3D0
[   25.286514] ath10k_pci 0000:03:00.0: [44]: 0x00000000 0x0040E3D0 0x009BB001 0x00040020
[   25.286516] ath10k_pci 0000:03:00.0: [48]: 0x00401BF0 0x00000001 0x00404B9C 0x00400000
[   25.286518] ath10k_pci 0000:03:00.0: [52]: 0x40928024 0x0040E3B0 0x0040D3D0 0x0040D3D0
[   25.286520] ath10k_pci 0000:03:00.0: [56]: 0x90E38400 0x500D53C0 0x58A26E80 0x02F3012B
[   26.280938] ath10k_pci 0000:03:00.0: failed to receive control response completion, polling..
[   27.281936] ath10k_pci 0000:03:00.0: ctl_resp never came in (-110)
[   27.281941] ath10k_pci 0000:03:00.0: failed to connect to HTC: -110
[   27.350160] ath10k_pci 0000:03:00.0: could not init core (-110)
[   27.350185] ath10k_pci 0000:03:00.0: could not probe fw (-110)
[   27.358148] ath10k_pci 0000:03:00.0: cannot restart a device that hasn't been started

```

---

