---
title: "Installing Intel Centrino Wireless-N 1000 [Condor Peak] card"
date: 2015-04-19
forum: Networking &amp; Wireless
---

### Post by John Pye on 2015-04-19
Hi

After having intermittent problems with the Broadcom BCM4312 installed in my Dell mini 10V I decided to try a new wifi card so I replaced it with a second hand one as above.  On starting up it seemed to work for a couple of days but after I left it unused for about a week then when started up yesterday Firefox and email failed to connect despite the connection to the router being shown as connected in Network Manager.

I have tried
[LIST]
[*]disabling n mode as per ([http://ubuntuforums.org/showthread.php?t=2219014](http://ubuntuforums.org/showthread.php?t=2219014)) 
[*]deleting the connection in Network manager and restarting 
[/LIST]
without success

Output of wireless script-

```
########## wireless info START ##########

Report from: 19 Apr 2015 13:46 BST +0100

Script from: 05 Sep 2014 22:42 UTC +0000

##### release #####

Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.2 LTS
Release:    14.04
Codename:    trusty

##### kernel #####

Linux 3.2.0-29-generic #46-Ubuntu SMP Fri Jul 27 17:04:05 UTC 2012 i686 i686 i686 GNU/Linux

, ro, quiet, splash, 

##### desktop #####

GNOME Flashback (Metacity)

##### lspci #####

03:00.0 Network controller [0280]: Intel Corporation Centrino Wireless-N 1000 [Condor Peak] [8086:0083]
    Subsystem: Intel Corporation Centrino Wireless-N 1000 BGN [8086:1305]
    Kernel driver in use: iwlwifi

04:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 02)
    Subsystem: Dell Device [1028:02f4]
    Kernel driver in use: r8169

##### lsusb #####

Bus 001 Device 003: ID 174f:1403 Syntek Integrated Webcam
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 413c:3016 Dell Computer Corp. Optical 5-Button Wheel Mouse
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

##### PCMCIA card info #####

##### rfkill #####

0: compal-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: compal-bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no
2: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

##### lsmod #####

iwlwifi               287811  0 
mac80211              436455  1 iwlwifi
cfg80211              178679  2 mac80211,iwlwifi

##### interfaces #####

auto lo
iface lo inet loopback

##### ifconfig #####

eth0      Link encap:Ethernet  HWaddr <MAC addr eth0>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:43 

wlan1     Link encap:Ethernet  HWaddr <MAC addr wlan1>  
          inet6 addr: fe80::226:c7ff:fe91:c45a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:279 errors:0 dropped:0 overruns:0 frame:0
          TX packets:620 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:84213 (84.2 KB)  TX bytes:122064 (122.0 KB)

##### iwconfig #####

lo        no wireless extensions.

eth0      no wireless extensions.

wlan1     IEEE 802.11bgn  ESSID:"virginmedia8622770"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: <MAC addr virginmedia8622770>   
          Bit Rate=1 Mb/s   Tx-Power=14 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=51/70  Signal level=-59 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:13  Invalid misc:21   Missed beacon:0

##### route #####

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface

##### resolv.conf #####

##### nm-tool #####

NetworkManager Tool

State: connecting

- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             unavailable
  Default:           no
  HW Address:        <MAC addr eth0>

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off

- Device: wlan1  [virginmedia8622770 1] ----------------------------------------
  Type:              802.11 WiFi
  Driver:            iwlwifi
  State:             connecting (getting IP configuration)
  Default:           no
  HW Address:        <MAC addr wlan1>

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 
    TALKTALK-1181B3: Infra, <MAC addr TALKTALK-1181B3>, Freq 2422 MHz, Rate 54 Mb/s, Strength 65 WPA WPA2
    SKYD41E2:        Infra, <MAC addr SKYD41E2>, Freq 2437 MHz, Rate 54 Mb/s, Strength 54 WPA WPA2
    BTHub3-WZ2R:     Infra, <MAC addr BTHub3-WZ2R>, Freq 2462 MHz, Rate 54 Mb/s, Strength 19 WPA WPA2
    BTWiFi-with-FON: Infra, <MAC addr BTWiFi-with-FON>, Freq 2462 MHz, Rate 54 Mb/s, Strength 34
    SoP:             Infra, <MAC addr SoP>, Freq 2422 MHz, Rate 54 Mb/s, Strength 25 WPA WPA2
    BTWifi-with-FON: Infra, <MAC addr BTWifi-with-FON>, Freq 2437 MHz, Rate 54 Mb/s, Strength 20
    VM233523-2G:     Infra, <MAC addr VM233523-2G>, Freq 2412 MHz, Rate 54 Mb/s, Strength 25 WPA WPA2
    BTWifi-X:        Infra, <MAC addr BTWifi-X>, Freq 2437 MHz, Rate 54 Mb/s, Strength 19 WPA WPA2 Enterprise
    Zeus:            Infra, <MAC addr Zeus>, Freq 2437 MHz, Rate 54 Mb/s, Strength 20 WPA2
    virginmedia8622770: Infra, <MAC addr virginmedia8622770>, Freq 2462 MHz, Rate 54 Mb/s, Strength 72 WPA2

##### NetworkManager.state #####

[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true

##### NetworkManager.conf #####

[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq

[ifupdown]
managed=false

##### iw reg get #####

country GB:
    (2402 - 2482 @ 40), (N/A, 20)
    (5170 - 5250 @ 40), (N/A, 20)
    (5250 - 5330 @ 40), (N/A, 20), DFS
    (5490 - 5710 @ 40), (N/A, 27), DFS
    (57240 - 65880 @ 2160), (N/A, 40), NO-OUTDOOR

##### iwlist channels #####

lo        no frequency information.

eth0      no frequency information.

wlan1     13 channels in total; available frequencies :
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
          Current Frequency=2.462 GHz (Channel 11)

##### iwlist scan #####

lo        Interface doesn't support scanning.

wlan1     Interface doesn't support scanning : Device or resource busy

eth0      Interface doesn't support scanning.

##### module infos #####

[iwlwifi]
filename:       /lib/modules/3.2.0-29-generic/kernel/drivers/net/wireless/iwlwifi/iwlwifi.ko
license:        GPL
author:         Copyright(c) 2003-2011 Intel Corporation <ilw@linux.intel.com>
version:        in-tree:
description:    Intel(R) Wireless WiFi Link AGN driver for Linux
firmware:       iwlwifi-5150-2.ucode
firmware:       iwlwifi-5000-5.ucode
firmware:       iwlwifi-6000g2b-6.ucode
firmware:       iwlwifi-6000g2a-5.ucode
firmware:       iwlwifi-6050-5.ucode
firmware:       iwlwifi-6000-4.ucode
firmware:       iwlwifi-100-5.ucode
firmware:       iwlwifi-1000-5.ucode
firmware:       iwlwifi-135-6.ucode
firmware:       iwlwifi-105-6.ucode
firmware:       iwlwifi-2030-6.ucode
firmware:       iwlwifi-2000-6.ucode
srcversion:     FA59DCECC20E2AB6A93E663
depends:        mac80211,cfg80211
intree:         Y
vermagic:       3.2.0-29-generic SMP mod_unload modversions 686 
parm:           swcrypto:using crypto in software (default 0 [hardware]) (int)
parm:           queues_num:number of hw queues. (int)
parm:           11n_disable:disable 11n functionality (int)
parm:           amsdu_size_8K:enable 8K amsdu size (int)
parm:           fw_restart:restart firmware in case of error (int)
parm:           ucode_alternative:specify ucode alternative to use from ucode file (int)
parm:           antenna_coupling:specify antenna coupling in dB (defualt: 0 dB) (int)
parm:           bt_ch_inhibition:Enable BT channel inhibition (default: enable) (bool)
parm:           plcp_check:Check plcp health (default: 1 [enabled]) (bool)
parm:           ack_check:Check ack health (default: 0 [disabled]) (bool)
parm:           wd_disable:Disable stuck queue watchdog timer 0=system default, 1=disable, 2=enable (default: 0) (int)
parm:           bt_coex_active:enable wifi/bt co-exist (default: enable) (bool)
parm:           led_mode:0=system default, 1=On(RF On)/Off(RF Off), 2=blinking (default: 0) (int)
parm:           power_save:enable WiFi power management (default: disable) (bool)
parm:           power_level:default power save level (range from 1 - 5, default: 1) (int)
parm:           auto_agg:enable agg w/o check traffic load (default: enable) (bool)
parm:           no_sleep_autoadjust:don't automatically adjust sleep level according to maximum network latency (default: true) (bool)

##### module parameters #####

[iwlwifi]
11n_disable: 0
ack_check: N
amsdu_size_8K: 1
antenna_coupling: 0
auto_agg: Y
bt_ch_inhibition: Y
bt_coex_active: Y
fw_restart: 1
led_mode: 0
no_sleep_autoadjust: Y
plcp_check: Y
power_level: 0
power_save: N
queues_num: 0
swcrypto: 0
ucode_alternative: 1
wd_disable: 0

##### /etc/modules #####

lp

##### blacklists #####

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

[/etc/modprobe.d/libpisock9.conf]
blacklist visor

[/etc/modprobe.d/osspd.conf]
blacklist snd-pcm-oss
blacklist snd-mixer-oss
blacklist snd-seq-oss

##### rc.local #####

exit 0

##### udev rules #####

[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x10ec:0x8136 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC addr eth0>", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# PCI device 0x14e4:0x4315 (wl)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address>", ATTR{type}=="1", KERNEL=="eth*", NAME="eth1"
# USB device 0x0bb4:0x0303 (usb)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth2"
# PCI device 0x14e4:/sys/devices/pci0000:00/0000:00:1c.1/0000:03:00.0/ssb0:0 (b43-pci-bridge)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"
# PCI device 0x8086:0x0083 (iwlwifi)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC addr wlan1>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan1"

##### dmesg #####

[    7.815589] iwlwifi 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    7.815632] iwlwifi 0000:03:00.0: setting latency timer to 64
[    7.815702] iwlwifi 0000:03:00.0: pci_resource_len = 0x00002000
[    7.815712] iwlwifi 0000:03:00.0: pci_resource_base = f805c000
[    7.815720] iwlwifi 0000:03:00.0: HW Revision ID = 0x0
[    7.816079] iwlwifi 0000:03:00.0: irq 44 for MSI/MSI-X
[    7.816244] iwlwifi 0000:03:00.0: Detected Intel(R) Centrino(R) Wireless-N 1000 BGN, REV=0x6C
[    7.816467] iwlwifi 0000:03:00.0: L1 Enabled; Disabling L0S
[    7.838767] iwlwifi 0000:03:00.0: device EEPROM VER=0x15d, CALIB=0x6
[    7.838780] iwlwifi 0000:03:00.0: Device SKU: 0X50
[    7.838788] iwlwifi 0000:03:00.0: Valid Tx ant: 0X1, Valid Rx ant: 0X3
[    8.028115] iwlwifi 0000:03:00.0: Tunable channels: 13 802.11bg, 0 802.11a channels
[   10.197532] iwlwifi 0000:03:00.0: loaded firmware version 39.31.5.1 build 35138
[   10.267722] ieee80211 phy0: Selected rate control algorithm 'iwl-agn-rs'
[   10.349629] systemd-udevd[449]: renamed network interface wlan0 to wlan1
[   18.716764] iwlwifi 0000:03:00.0: L1 Enabled; Disabling L0S (repeated 2 times)
[   18.874192] ADDRCONF(NETDEV_UP): wlan1: link is not ready (repeated 2 times)
[   20.321014] wlan1: direct probe to <MAC addr virginmedia8622770> (try 1/3)
[   20.326868] wlan1: direct probe responded
[   20.340108] wlan1: authenticate with <MAC addr virginmedia8622770> (try 1)
[   20.343563] wlan1: authenticated
[   20.357066] wlan1: associate with <MAC addr virginmedia8622770> (try 1)
[   20.362546] wlan1: RX AssocResp from <MAC addr virginmedia8622770> (capab=0x411 status=0 aid=2)
[   20.362559] wlan1: associated
[   20.373472] ADDRCONF(NETDEV_CHANGE): wlan1: link becomes ready
[   31.120059] wlan1: no IPv6 routers present
[   66.232982] wlan1: deauthenticating from <MAC addr virginmedia8622770> by local choice (reason=3)
[   69.230686] wlan1: authenticate with <MAC addr virginmedia8622770> (try 1)
[   69.233556] wlan1: authenticated
[   69.235225] wlan1: associate with <MAC addr virginmedia8622770> (try 1)
[   69.238931] wlan1: RX AssocResp from <MAC addr virginmedia8622770> (capab=0x411 status=0 aid=2)
[   69.238944] wlan1: associated
[   79.960051] wlan1: no IPv6 routers present
[  115.227389] wlan1: deauthenticating from <MAC addr virginmedia8622770> by local choice (reason=3)
[  118.196139] wlan1: authenticate with <MAC addr virginmedia8622770> (try 1)
[  118.199037] wlan1: authenticated
[  118.200216] wlan1: associate with <MAC addr virginmedia8622770> (try 1)
[  118.205641] wlan1: RX AssocResp from <MAC addr virginmedia8622770> (capab=0x411 status=0 aid=2)
[  118.205654] wlan1: associated
[  131.762240] wlan1: deauthenticated from <MAC addr virginmedia8622770> (Reason: 15)
[  132.353595] wlan1: authenticate with <MAC addr virginmedia8622770> (try 1)
[  132.357437] wlan1: authenticated
[  132.359245] wlan1: associate with <MAC addr virginmedia8622770> (try 1)
[  132.362893] wlan1: RX AssocResp from <MAC addr virginmedia8622770> (capab=0x411 status=0 aid=2)
[  132.362906] wlan1: associated
[  134.912092] wlan1: no IPv6 routers present
[  209.881346] wlan1: authenticate with <MAC addr virginmedia8622770> (try 1)
[  209.884981] wlan1: authenticated
[  209.886183] wlan1: associate with <MAC addr virginmedia8622770> (try 1)
[  209.889850] wlan1: RX AssocResp from <MAC addr virginmedia8622770> (capab=0x411 status=0 aid=2)
[  209.889866] wlan1: associated
[  272.679726] wlan1: authenticate with <MAC addr virginmedia8622770> (try 1)
[  272.683513] wlan1: authenticated
[  272.684741] wlan1: associate with <MAC addr virginmedia8622770> (try 1)
[  272.688396] wlan1: RX AssocResp from <MAC addr virginmedia8622770> (capab=0x411 status=0 aid=2)
[  272.688410] wlan1: associated
[  355.680496] wlan1: authenticate with <MAC addr virginmedia8622770> (try 1)
[  355.695053] wlan1: authenticated
[  355.695975] wlan1: associate with <MAC addr virginmedia8622770> (try 1)
[  355.701503] wlan1: RX AssocResp from <MAC addr virginmedia8622770> (capab=0x411 status=0 aid=2)
[  355.701526] wlan1: associated
[  459.459906] wlan1: authenticate with <MAC addr virginmedia8622770> (try 1)
[  459.462781] wlan1: authenticated
[  459.469038] wlan1: associate with <MAC addr virginmedia8622770> (try 1)
[  459.472699] wlan1: RX AssocResp from <MAC addr virginmedia8622770> (capab=0x411 status=0 aid=2)
[  459.472712] wlan1: associated
[  578.598226] wlan1: authenticate with <MAC addr virginmedia8622770> (try 1)
[  578.601131] wlan1: authenticated
[  578.602324] wlan1: associate with <MAC addr virginmedia8622770> (try 1)
[  578.610185] wlan1: RX AssocResp from <MAC addr virginmedia8622770> (capab=0x411 status=0 aid=2)
[  578.610199] wlan1: associated
[  586.351372] wlan1: deauthenticated from <MAC addr virginmedia8622770> (Reason: 15)
[  591.934856] wlan1: authenticate with <MAC addr virginmedia8622770> (try 1)
[  592.132147] wlan1: authenticate with <MAC addr virginmedia8622770> (try 2)
[  592.332103] wlan1: authenticate with <MAC addr virginmedia8622770> (try 3)
[  592.532091] wlan1: authentication with <MAC addr virginmedia8622770> timed out
[  604.624363] wlan1: direct probe to <MAC addr virginmedia8622770> (try 1/3)
[  604.824083] wlan1: direct probe to <MAC addr virginmedia8622770> (try 2/3)
[  605.024107] wlan1: direct probe to <MAC addr virginmedia8622770> (try 3/3)
[  605.224137] wlan1: direct probe to <MAC addr virginmedia8622770> timed out
[  616.029055] wlan1: direct probe to <MAC addr virginmedia8622770> (try 1/3)
[  616.228164] wlan1: direct probe to <MAC addr virginmedia8622770> (try 2/3)
[  616.428121] wlan1: direct probe to <MAC addr virginmedia8622770> (try 3/3)
[  616.628110] wlan1: direct probe to <MAC addr virginmedia8622770> timed out
[  617.214696] ADDRCONF(NETDEV_UP): wlan1: link is not ready
[  631.419887] wlan1: authenticate with <MAC addr virginmedia8622770> (try 1)
[  631.437294] wlan1: authenticated
[  631.438518] wlan1: associate with <MAC addr virginmedia8622770> (try 1)
[  631.446429] wlan1: RX AssocResp from <MAC addr virginmedia8622770> (capab=0x411 status=0 aid=2)
[  631.446441] wlan1: associated
[  631.458465] ADDRCONF(NETDEV_CHANGE): wlan1: link becomes ready
[  645.618595] wlan1: deauthenticated from <MAC addr virginmedia8622770> (Reason: 15)
[  646.106215] wlan1: authenticate with <MAC addr virginmedia8622770> (try 1)
[  646.115258] wlan1: authenticated
[  646.117649] wlan1: associate with <MAC addr virginmedia8622770> (try 1)
[  646.121524] wlan1: RX AssocResp from <MAC addr virginmedia8622770> (capab=0x411 status=0 aid=2)
[  646.121539] wlan1: associated

########## wireless info END ############
```

Many thanks to anyone willing to help.

---

### Post by praseodym on 2015-04-20
Deactivate IPv6 in the network profile settings

---

### Post by John Pye on 2015-04-21
Many thanks.  

I have had IPv6 settings set to ignore in  connection settings. I hope that's what you mean?  Still working for 5 mins then failing to load pages whilst still saying wifi connected.

John

---

### Post by praseodym on 2015-04-21
Try to deactivate the queue, too:
```

echo "options iwlwifi 11n_disable=1 wd_disable=1" | sudo tee /etc/modprobe.d/iwlwifi.conf
sudo modprobe -rfv iwlwifi
sudo modprobe -v iwlwifi
```

---

### Post by John Pye on 2015-04-25
Seems stable now, Many Thanks

---

