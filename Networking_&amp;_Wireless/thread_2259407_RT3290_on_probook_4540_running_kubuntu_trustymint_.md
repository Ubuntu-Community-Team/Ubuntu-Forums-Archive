---
title: "RT3290 on probook 4540 running kubuntu trusty/mint qiana"
date: 2015-01-04
forum: Networking &amp; Wireless
---

### Post by apog2 on 2015-01-04
hello to all

i am running mint qiana kde (based on ubuntu 14.04) on a hp probook 4540

everything is working (it was complicated to installe due to uefi/gpt) but i have persistent  wifi disconexions. sometimes it is easy to reconnect even automatically, sometimes, i have to restart the wifi in the network manager applet in the taskbar (deactivate wireless/reactivate wireless)

I am not sure when it started, this was working fine a year ago. Trying to solve this, i have installed the latest kernel available as stable :

```

caty@pkat:~ >uname -a 
Linux pkat 3.18.1-031801-generic #201412170637 SMP Wed Dec 17 11:38:50 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux

```

result of wireless_script below :

```

########## wireless info START ##########

Report from: 04 Jan 2015 14:51 CET +0100

Booted last: 03 Jan 2015 12:07 CET +0100

Script from: 20 Sep 2014 23:04 UTC +0000

##### release ###########################

Distributor ID:    LinuxMint
Description:    Linux Mint 17 Qiana
Release:    17
Codename:    qiana

##### kernel ############################

Linux 3.18.1-031801-generic #201412170637 SMP Wed Dec 17 11:38:50 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

default

##### lspci #############################

03:00.0 Network controller [0280]: Ralink corp. RT3290 Wireless 802.11n 1T/1R PCIe [1814:3290]
    Subsystem: Hewlett-Packard Company Ralink RT3290LE 802.11bgn 1x1 Wi-Fi and Bluetooth 4.0 Combo Adapter [103c:18ec]
    Kernel driver in use: rt2800pci

04:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 07)
    Subsystem: Hewlett-Packard Company Device [103c:17f6]
    Kernel driver in use: r8169

##### lsusb #############################

Bus 004 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 004 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 003: ID 04f2:b370 Chicony Electronics Co., Ltd 
Bus 003 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

##### lsmod #############################

hp_wmi                 14017  0 
sparse_keymap          13890  1 hp_wmi
rt2800pci              13674  0 
rt2800mmio             21082  1 rt2800pci
rt2800lib              95583  2 rt2800pci,rt2800mmio
rt2x00pci              13287  1 rt2800pci
rt2x00mmio             13661  2 rt2800pci,rt2800mmio
rt2x00lib              56113  5 rt2x00pci,rt2800lib,rt2800pci,rt2800mmio,rt2x00mmio
mac80211              697159  3 rt2x00lib,rt2x00pci,rt2800lib
cfg80211              520257  2 mac80211,rt2x00lib
eeprom_93cx6           13344  1 rt2800pci
crc_ccitt              12707  1 rt2800lib
wmi                    19379  1 hp_wmi

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

eth0      Link encap:Ethernet  HWaddr <MAC 'eth0' [IF]>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wlan0     Link encap:Ethernet  HWaddr <MAC 'wlan0' [IF]>  
          inet addr:192.168.0.21  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::4a5a:b6ff:fe42:2ffd/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:250834 errors:0 dropped:0 overruns:0 frame:0
          TX packets:188210 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:283919550 (283.9 MB)  TX bytes:24722633 (24.7 MB)

##### iwconfig ##########################

eth0      no wireless extensions.

lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"freebox_blauves"  
          Mode:Managed  Frequency:2.472 GHz  Access Point: <MAC 'freebox_blauves' [AC1]>   
          Bit Rate=36 Mb/s   Tx-Power=20 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=48/70  Signal level=-62 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:14   Missed beacon:0

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.0.254   0.0.0.0         UG    0      0        0 wlan0
192.168.0.0     0.0.0.0         255.255.255.0   U     9      0        0 wlan0

##### resolv.conf #######################

nameserver 127.0.1.1

##### nm-tool ###########################

** (process:12317): WARNING **: error: cannot retrieve connection: uid 1000 has no permission to perform this operation

NetworkManager Tool

State: connected (global)

- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             unavailable
  Default:           no
  HW Address:        <MAC 'eth0' [IF]>

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off

- Device: wlan0  [freebox_blauves] ---------------------------------------------
  Type:              802.11 WiFi
  Driver:            rt2800pci
  State:             connected
  Default:           yes
  HW Address:        <MAC 'wlan0' [IF]>

  Capabilities:
    Speed:           36 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    *freebox_blauves:Infra, <MAC 'freebox_blauves' [AC1]>, Freq 2472 MHz, Rate 54 Mb/s, Strength 60 WPA

  IPv4 Settings:
    Address:         192.168.0.21
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.0.254

    DNS:             212.27.40.241
    DNS:             212.27.40.240

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

[[/etc/NetworkManager/system-connections/FreeWifi]] (600 root)
[connection] id=FreeWifi | type=802-11-wireless | permissions=user:caty:;
[802-11-wireless] ssid=FreeWifi | mac-address=<MAC 'wlan0' [IF]>
[ipv6] method=auto
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/freebox_KFPEBC-afc685ca-1bf0-43dd-b734-087d5d17ea65]] (600 root)
[connection] id=freebox_KFPEBC | type=802-11-wireless | permissions=user:caty:;
[802-11-wireless] ssid=freebox_KFPEBC | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=ignore

[[/etc/NetworkManager/system-connections/freebox_blauves]] (600 root)
[connection] id=freebox_blauves | type=802-11-wireless | permissions=user:caty:;
[802-11-wireless] ssid=freebox_blauves | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/freebox_KFPEBC]] (600 root)
[connection] id=freebox_KFPEBC | type=802-11-wireless | permissions=user:mint:;
[802-11-wireless] ssid=freebox_KFPEBC | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

##### iw reg get ########################

Region: Europe/Paris (based on set time zone)

country 00:
    (2402 - 2472 @ 40), (3, 20)
    (2457 - 2482 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (2474 - 2494 @ 20), (3, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
    (5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS

##### iwlist channels ###################

eth0      no frequency information.

lo        no frequency information.

wlan0     14 channels in total; available frequencies :
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
          Current Frequency:2.472 GHz (Channel 13)

##### iwlist scan #######################

Channel occupancy:

      1   APs on   Frequency:2.472 GHz (Channel 13)

eth0      Interface doesn't support scanning.

lo        Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: <MAC 'freebox_blauves' [AC1]>
                    Channel:13
                    Frequency:2.472 GHz (Channel 13)
                    Quality=48/70  Signal level=-62 dBm  
                    Encryption key:on
                    ESSID:"freebox_blauves"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000007a223f3dbf
                    Extra: Last beacon: 36ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK

##### module infos ######################

[rt2800pci]
filename:       /lib/modules/3.18.1-031801-generic/kernel/drivers/net/wireless/rt2x00/rt2800pci.ko
license:        GPL
firmware:       rt2860.bin
description:    Ralink RT2800 PCI & PCMCIA Wireless LAN driver.
version:        2.3.0
author:         http://rt2x00.serialmonkey.com
srcversion:     3FF1176BB7F7770CA8BC1EE
depends:        rt2x00lib,rt2800lib,rt2800mmio,rt2x00mmio,rt2x00pci,eeprom_93cx6
intree:         Y
vermagic:       3.18.1-031801-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        36:AD:A8:5E:F7:73:2C:DD:67:A9:EC:A3:4F:31:D5:0F:E6:75:FD:11
sig_hashalgo:   sha512
parm:           nohwcrypt:Disable hardware encryption. (bool)

[rt2800mmio]
filename:       /lib/modules/3.18.1-031801-generic/kernel/drivers/net/wireless/rt2x00/rt2800mmio.ko
license:        GPL
description:    rt2800 MMIO library
version:        2.3.0
author:         http://rt2x00.serialmonkey.com
srcversion:     5E8DE289EF26F4FFC0BAE56
depends:        rt2800lib,rt2x00lib,rt2x00mmio
intree:         Y
vermagic:       3.18.1-031801-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        36:AD:A8:5E:F7:73:2C:DD:67:A9:EC:A3:4F:31:D5:0F:E6:75:FD:11
sig_hashalgo:   sha512

[rt2800lib]
filename:       /lib/modules/3.18.1-031801-generic/kernel/drivers/net/wireless/rt2x00/rt2800lib.ko
license:        GPL
description:    Ralink RT2800 library
version:        2.3.0
author:         http://rt2x00.serialmonkey.com, Bartlomiej Zolnierkiewicz
srcversion:     5A3FAD96F0E24DA9DF06D17
depends:        rt2x00lib,mac80211,crc-ccitt
intree:         Y
vermagic:       3.18.1-031801-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        36:AD:A8:5E:F7:73:2C:DD:67:A9:EC:A3:4F:31:D5:0F:E6:75:FD:11
sig_hashalgo:   sha512

[rt2x00pci]
filename:       /lib/modules/3.18.1-031801-generic/kernel/drivers/net/wireless/rt2x00/rt2x00pci.ko
license:        GPL
description:    rt2x00 pci library
version:        2.3.0
author:         http://rt2x00.serialmonkey.com
srcversion:     2AE29A8EC35C16DFCABA32E
depends:        rt2x00lib,mac80211
intree:         Y
vermagic:       3.18.1-031801-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        36:AD:A8:5E:F7:73:2C:DD:67:A9:EC:A3:4F:31:D5:0F:E6:75:FD:11
sig_hashalgo:   sha512

[rt2x00mmio]
filename:       /lib/modules/3.18.1-031801-generic/kernel/drivers/net/wireless/rt2x00/rt2x00mmio.ko
license:        GPL
description:    rt2x00 mmio library
version:        2.3.0
author:         http://rt2x00.serialmonkey.com
srcversion:     B297AFAD070E693659C4908
depends:        rt2x00lib
intree:         Y
vermagic:       3.18.1-031801-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        36:AD:A8:5E:F7:73:2C:DD:67:A9:EC:A3:4F:31:D5:0F:E6:75:FD:11
sig_hashalgo:   sha512

[rt2x00lib]
filename:       /lib/modules/3.18.1-031801-generic/kernel/drivers/net/wireless/rt2x00/rt2x00lib.ko
license:        GPL
description:    rt2x00 library
version:        2.3.0
author:         http://rt2x00.serialmonkey.com
srcversion:     BA57869D6451486D8D7903E
depends:        mac80211,cfg80211
intree:         Y
vermagic:       3.18.1-031801-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        36:AD:A8:5E:F7:73:2C:DD:67:A9:EC:A3:4F:31:D5:0F:E6:75:FD:11
sig_hashalgo:   sha512

[mac80211]
filename:       /lib/modules/3.18.1-031801-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     7EEF5988245D414BA91F27D
depends:        cfg80211
intree:         Y
vermagic:       3.18.1-031801-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        36:AD:A8:5E:F7:73:2C:DD:67:A9:EC:A3:4F:31:D5:0F:E6:75:FD:11
sig_hashalgo:   sha512
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[cfg80211]
filename:       /lib/modules/3.18.1-031801-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     C8543A08D2650C7BC1B7107
depends:        
intree:         Y
vermagic:       3.18.1-031801-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        36:AD:A8:5E:F7:73:2C:DD:67:A9:EC:A3:4F:31:D5:0F:E6:75:FD:11
sig_hashalgo:   sha512
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

##### module parameters #################

[rt2800pci]
nohwcrypt: N

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
# PCI device 0x1814:0x3290 (rt2800pci)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

##### dmesg #############################

[15805.003198] wlan0: authenticate with <MAC 'freebox_blauves' [AC1]>
[15805.018913] wlan0: direct probe to <MAC 'freebox_blauves' [AC1]> (try 1/3)
[15805.222993] wlan0: direct probe to <MAC 'freebox_blauves' [AC1]> (try 2/3)
[15805.427111] wlan0: send auth to <MAC 'freebox_blauves' [AC1]> (try 3/3)
[15805.429414] wlan0: authenticated
[15805.429624] rt2800pci 0000:03:00.0 wlan0: disabling HT/VHT due to WEP/TKIP use
[15805.431147] wlan0: associate with <MAC 'freebox_blauves' [AC1]> (try 1/3)
[15805.441008] wlan0: RX AssocResp from <MAC 'freebox_blauves' [AC1]> (capab=0x411 status=0 aid=1)
[15805.441112] wlan0: associated
[15841.868170] wlan0: deauthenticating from <MAC 'freebox_blauves' [AC1]> by local choice (Reason: 3=DEAUTH_LEAVING)
[15845.742266] wlan0: authenticate with <MAC 'freebox_blauves' [AC1]>
[15845.757998] wlan0: send auth to <MAC 'freebox_blauves' [AC1]> (try 1/3)
[15845.759373] wlan0: authenticated
[15845.759520] rt2800pci 0000:03:00.0 wlan0: disabling HT/VHT due to WEP/TKIP use
[15845.761880] wlan0: associate with <MAC 'freebox_blauves' [AC1]> (try 1/3)
[15845.764477] wlan0: RX AssocResp from <MAC 'freebox_blauves' [AC1]> (capab=0x411 status=0 aid=3)
[15845.764590] wlan0: associated

########## wireless info END ############


```

before to install 3.18.1 i have tried several tricks included compilation of driver with absolutely no success.

the alternative would be if no solution shows up to use a nano-usb dongle so if somebody would suggest a good one this might be the poor(s man solution (before opening the laptop and replacing the wireless adapter !)

thanks for your advices

---

### Post by praseodym on 2015-01-04
Hi,

deactivate IPv6 in the network-manager setting and change to a fixed channel with WPA2-AES (CCMP) encryption

---

