---
title: "Wi-Fi disconnects unexpectedly - Ubuntu 14.04 - Intel Centrino Wireless N-1030"
date: 2014-09-18
forum: Networking &amp; Wireless
---

### Post by 10barabas on 2014-09-18
Hello,
   Nothing helped me. I've tried all recomended module parameters. Such as bt_coex_active=N swcrypto=1 11n_disable=1. Parameter 11n_disable makes things even much worth it doesn't connect at all with it. And also changing my router configuration. But the connection is dropped after 5 minutes I start the computer. Only restart helps to reconnect again.

There is a wireless script output:
```
    ======== Wireless-Info START ========

System-Info ~~~~~~~~~~~~~~~~~~~~~~~~

user-R508 3.13.0-35-generic i686,  Ubuntu 14.04.1 LTS, trusty

CPU    : Intel(R) Core(TM) i5-2410M CPU @ 2.30GHz
Memory : 7994 MB
Uptime : 08:19:05 up 18 min,  2 users,  load average: 0.40, 0.33, 0.31


lspci ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

02:00.0 Network controller [0280]: Intel Corporation Centrino Wireless-N 1030 [Rainbow Peak] [8086:008a] (rev ff)
    Kernel driver in use: iwlwifi
03:00.0 USB controller [0c03]: ASMedia Technology Inc. ASM1042 SuperSpeed USB Host Controller [1b21:1042]
--
04:00.0 Ethernet controller [0200]: Qualcomm Atheros AR8151 v2.0 Gigabit Ethernet [1969:1083] (rev c0)
    Subsystem: ASUSTeK Computer Inc. Device [1043:1851]
    Kernel driver in use: atl1c


lsusb ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 004: ID 058f:6366 Alcor Micro Corp. Multi Flash Reader
Bus 001 Device 003: ID 058f:a014 Alcor Micro Corp. Asus Integrated Webcam
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


PCMCIA Card Info ~~~~~~~~~~~~~~~~~~~



iwconfig ~~~~~~~~~~~~~~~~~~~~~~~~~~~

wlan1     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          


rfkill ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

      Interface             Soft blocked  Hard blocked
0: asus-wlan: Wireless LAN      no            no
1: phy0: Wireless LAN           no            no


lsmod ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

iwldvm                214950  0 
mac80211              546051  1 iwldvm
iwlwifi               152049  1 iwldvm
asus_nb_wmi            16862  0 
asus_wmi               23495  1 asus_nb_wmi
sparse_keymap          13708  1 asus_wmi
cfg80211              409394  3 iwlwifi,mac80211,iwldvm
wmi                    18673  1 asus_wmi
video                  18903  2 i915,asus_wmi


module parameters ~~~~~~~~~~~~~~~~~~

asus_nb_wmi   (1): wapf=0
cfg80211      (2): cfg80211_disable_40mhz_24ghz=N | ieee80211_regdom=00
iwlwifi      (11): 11n_disable=0 | amsdu_size_8K=0 | antenna_coupling=0 | bt_coex_active=N | fw_restart=Y | led_mode=0 | nvm_file=(null) | power_level=0 | power_save=N | swcrypto=1 | wd_disable=1
mac80211      (5): beacon_loss_count=7 | ieee80211_default_rc_algo=minstrel_ht | max_nullfunc_tries=2 | max_probe_tries=5 | probe_wait_ms=500
video         (3): allow_duplicates=N | brightness_switch_enabled=Y | use_native_backlight=-1
wmi           (2): debug_dump_wdg=N | debug_event=N


nm-tool ~~~~~~~~~~~~~~~~~~~~~~~~~~~~

State: connected (global)
=======================o=============o=========o==  =========o=========o===========o==============o===  ========
 Interface & ID        | Type        | Driver  | State     | Default | Speed     | Support      | HW Addr   
=======================o=============o=========o==  =========o=========o===========o==============o===  ========
 eth1  [Auto Ethernet] | Wired       | atl1c   | connected | yes     | 1000 Mb/s |              | <MAC eth1>

    Address:         77.123.171.140
    Prefix:          21 (255.255.248.0)
    Gateway:         77.123.168.1
    DNS:             77.120.32.21
    DNS:             77.120.32.6
-----------------------+-------------+---------+-----------+---------+-----------+--------------+-----------
 wlan1  [volia23 1]    | 802.11 WiFi | iwlwifi | connected | no      |           | WEP/WPA/WPA2 | <MAC wlan1>

    Manu:            Infra, <MAC C-NA Manu 1>, Freq 2457 MHz, Rate 54 Mb/s, Strength 47 WPA WPA2
    kyivstar105:     Infra, <MAC C-NA kyivstar105 1>, Freq 2437 MHz, Rate 54 Mb/s, Strength 42 WPA WPA2
    TP-LINK_F26E2C:  Infra, <MAC C-NA TP-LINK_F26E2C 1>, Freq 2427 MHz, Rate 54 Mb/s, Strength 30 WPA2
    ROMA:            Infra, <MAC C-NA ROMA 1>, Freq 2412 MHz, Rate 54 Mb/s, Strength 25 WPA2
    oksfancy:        Infra, <MAC C-NA oksfancy 1>, Freq 2417 MHz, Rate 54 Mb/s, Strength 22 WPA WPA2
    volia16:         Infra, <MAC C-NA volia16 1>, Freq 2437 MHz, Rate 54 Mb/s, Strength 20 WPA WPA2
    Volia_9:         Infra, <MAC C-NA Volia_9 1>, Freq 2437 MHz, Rate 54 Mb/s, Strength 19 WPA
    dlink:           Infra, <MAC C-NA dlink 1>, Freq 2412 MHz, Rate 54 Mb/s, Strength 22 WEP
    HALLA MADRID:    Infra, <MAC C-NA HALLA MADRID 1>, Freq 2447 MHz, Rate 54 Mb/s, Strength 20 WEP
    volia23:         Infra, <MAC C-NA volia23 1>, Freq 2462 MHz, Rate 54 Mb/s, Strength 49 WPA2
    Graf_34Nestor:   Infra, <MAC C-NA Graf_34Nestor 1>, Freq 2412 MHz, Rate 54 Mb/s, Strength 25 WPA WPA2
    odeko12:         Infra, <MAC C-NA odeko12 1>, Freq 2412 MHz, Rate 54 Mb/s, Strength 19 WPA WPA2
    TP-LINK_4CEF36:  Infra, <MAC C-NA TP-LINK_4CEF36 1>, Freq 2437 MHz, Rate 54 Mb/s, Strength 19 WPA2
    ogo:             Infra, <MAC C-NA ogo 1>, Freq 2412 MHz, Rate 54 Mb/s, Strength 24 WPA WPA2
    VOLIA5:          Infra, <MAC C-NA VOLIA5 1>, Freq 2432 MHz, Rate 54 Mb/s, Strength 15 WPA WPA2
    APs:             Infra, <MAC C-NA APs 1>, Freq 2417 MHz, Rate 54 Mb/s, Strength 20 WPA WPA2
    UKrtelecom_sApT5z: Infra, <MAC C-NA UKrtelecom_sApT5z 1>, Freq 2462 MHz, Rate 54 Mb/s, Strength 20 WPA2
    IEEE802.11n:     Infra, <MAC C-NA IEEE802.11n 1>, Freq 2462 MHz, Rate 54 Mb/s, Strength 17 WPA WPA2

    Address:         192.168.0.104
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.0.1
    DNS:             192.168.0.1
-----------------------+-------------+---------+-----------+---------+-----------+--------------+-----------


NetworkManager.state ~~~~~~~~~~~~~~~

[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true


NetworkManager.conf ~~~~~~~~~~~~~~~~

[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq

[ifupdown]
managed=false


NM WiFi Profiles ~~~~~~~~~~~~~~~~~~~

BEKTOP               : ssid=BEKTOP | mac-address=<MAC wlan0> | ipv6=auto | ipv4=auto 
BHome2               : ssid=BHome2 | mac-address=<MAC wlan1> | ipv4=auto | ipv6=auto 
bnet                 : ssid=bnet | mac-address=<MAC wlan1> | ipv4=auto | ipv6=auto 
bnet1                : ssid=bnet1 | mac-address=<MAC wlan1> | ipv4=auto | ipv6=auto 
bnet1 1              : ssid=bnet1 | mac-address=<MAC wlan1> | ipv6=auto | ipv4=auto 
bnet1 2              : ssid=bnet1 | mac-address=<MAC wlan1> | ipv4=auto | ipv6=auto 
default              : ssid=default | bssid=<MAC ID removed> | mac-address=<MAC wlan1> | ipv6=auto | ipv4=auto 
DIMA                 : ssid=DIMA | mac-address=<MAC wlan1> | ipv4=auto | ipv6=auto 
dom70                : ssid=dom70 | mac-address=<MAC wlan1> | ipv4=auto | ipv6=auto 
dom71                : ssid=dom71 | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 
dom71 1              : ssid=dom71 | autoconnect=false | mac-address=<MAC wlan1> | ipv4=auto | ipv6=auto 
Fly IQ446            : ssid=Fly IQ446 | mac-address=<MAC wlan1> | ipv6=auto | ipv4=auto 
Fly IQ446 1          : ssid=Fly IQ446 | mac-address=<MAC wlan1> | ipv4=auto | ipv6=auto 
Fly IQ450 Quattro    : ssid=Fly IQ450 Quattro | mac-address=<MAC wlan1> | ipv4=auto | ipv6=auto 
g2224                : ssid=g2224 | mac-address=<MAC wlan1> | ipv4=auto | ipv6=auto 
gurzuf               : ssid=gurzuf | mac-address=<MAC wlan1> | ipv4=auto | ipv6=auto 
hello                : ssid=hello | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 
hello 1              : ssid=hello | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 
hello 2              : ssid=hello | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 
hello 3              : ssid=hello | mac-address=<MAC wlan1> | ipv4=auto | ipv6=auto 
hello 4              : ssid=hello | mac-address=<MAC wlan2> | ipv4=auto | ipv6=auto 
home                 : ssid=home | mac-address=<MAC wlan1> | ipv4=auto | ipv6=auto 
Huawei_HG530_09BC0   : ssid=Huawei_HG530_09BC0 | mac-address=<MAC wlan1> | ipv4=auto | ipv6=auto 
Huawei_HG530_0AEAC   : ssid=Huawei_HG530_0AEAC | mac-address=<MAC wlan1> | ipv4=auto | ipv6=auto 
kovalenko            : ssid=kovalenko | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 
Nina                 : ssid=Nina | mac-address=<MAC wlan1> | ipv4=auto | ipv6=auto 
NINA                 : ssid=NINA | mac-address=<MAC wlan1> | ipv4=auto | ipv6=auto 
Pomidoro             : ssid=Pomidoro | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 
Tenda_339B90         : ssid=Tenda_339B90 | mac-address=<MAC wlan1> | ipv4=auto | ipv6=auto 
Tenda_339B90 1       : ssid=Tenda_339B90 | mac-address=<MAC wlan1> | ipv6=auto | ipv4=auto 
volia23              : ssid=volia23 | ipv6=auto | ipv4=auto 
volia23 1            : ssid=volia23 | mac-address=<MAC wlan1> | ipv4=auto | ipv6=ignore 
Xperia C_89e6        : ssid=Xperia C_89e6 | mac-address=<MAC wlan1> | ipv4=auto | ipv6=auto 
Zahidtelecom         : ssid=Zahidtelecom | mac-address=<MAC wlan1> | ipv4=auto | ipv6=auto 
ZXDSL531BII-F3F0FE   : ssid=ZXDSL531BII-F3F0FE | mac-address=<MAC wlan1> | ipv4=auto | ipv6=auto 


interfaces ~~~~~~~~~~~~~~~~~~~~~~~~~

auto lo
iface lo inet loopback


resolv.conf ~~~~~~~~~~~~~~~~~~~~~~~~

domain isd.dp.ua
nameserver 10.98.0.2
nameserver 10.98.0.1
nameserver 127.0.1.1
search isd.dp.ua 


Routes & Ping ~~~~~~~~~~~~~~~~~~~~~~

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         77.123.168.1    0.0.0.0         UG    0      0        0 eth1
10.98.0.0       0.0.0.0         255.255.0.0     U     0      0        0 cscotun0
10.98.16.0      0.0.0.0         255.255.255.0   U     0      0        0 cscotun0
10.99.0.0       0.0.0.0         255.255.0.0     U     0      0        0 cscotun0
10.100.0.0      0.0.0.0         255.255.0.0     U     0      0        0 cscotun0
77.123.168.0    0.0.0.0         255.255.248.0   U     1      0        0 eth1
77.123.168.1    0.0.0.0         255.255.255.255 UH    0      0        0 eth1
80.51.168.0     0.0.0.0         255.255.255.0   U     0      0        0 cscotun0
172.26.0.0      0.0.0.0         255.255.0.0     U     0      0        0 cscotun0
172.27.0.0      0.0.0.0         255.255.0.0     U     0      0        0 cscotun0
172.28.1.0      0.0.0.0         255.255.255.0   U     0      0        0 cscotun0
172.29.0.0      0.0.0.0         255.255.0.0     U     0      0        0 cscotun0
192.168.0.0     0.0.0.0         255.255.255.0   U     9      0        0 wlan1
193.93.100.0    0.0.0.0         255.255.252.0   U     0      0        0 cscotun0
193.93.102.3    77.123.168.1    255.255.255.255 UGH   0      0        0 eth1
193.108.162.0   0.0.0.0         255.255.254.0   U     0      0        0 cscotun0
195.116.122.0   0.0.0.0         255.255.255.0   U     0      0        0 cscotun0
205.172.68.0    0.0.0.0         255.255.252.0   U     0      0        0 cscotun0
208.86.236.0    0.0.0.0         255.255.252.0   U     0      0        0 cscotun0

--- 77.123.168.1 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 1001ms
rtt min/avg/max/mdev = 16.775/18.584/20.394/1.814 ms

--- 10.98.0.2 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 1001ms
rtt min/avg/max/mdev = 32.617/34.524/36.432/1.916 ms

--- 10.98.0.1 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 1001ms
rtt min/avg/max/mdev = 31.969/33.810/35.652/1.850 ms

--- 127.0.1.1 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 999ms
rtt min/avg/max/mdev = 0.063/0.069/0.076/0.010 ms


iw reg get ~~~~~~~~~~~~~~~~~~~~~~~~~

(Region : "en_US.UTF-8")
country 00:
    (2402 - 2472 @ 40), (3, 20)
    (2457 - 2482 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (2474 - 2494 @ 20), (3, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
    (5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS


iwlist chan ~~~~~~~~~~~~~~~~~~~~~~~~

wlan1     13 channels in total; available frequencies :
          Channel 01 (2.412 GHz) - 13 (2.472 GHz)


iwlist scan ~~~~~~~~~~~~~~~~~~~~~~~~



blacklist ~~~~~~~~~~~~~~~~~~~~~~~~~~

[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci


modinfo ~~~~~~~~~~~~~~~~~~~~~~~~~~~~

[iwldvm]
filename:       /lib/modules/3.13.0-35-generic/kernel/drivers/net/wireless/iwlwifi/dvm/iwldvm.ko
version:        in-tree:
srcversion:     CC4D1BA11C1EF73A6ABDE53
depends:        iwlwifi,mac80211,cfg80211

[mac80211]
filename:       /lib/modules/3.13.0-35-generic/kernel/net/mac80211/mac80211.ko
srcversion:     D491AB7C521706DA5F4BE7C
depends:        cfg80211
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[iwlwifi]
filename:       /lib/modules/3.13.0-35-generic/kernel/drivers/net/wireless/iwlwifi/iwlwifi.ko
version:        in-tree:
firmware:       iwlwifi-100-5.ucode
firmware:       iwlwifi-1000-5.ucode
firmware:       iwlwifi-135-6.ucode
firmware:       iwlwifi-105-6.ucode
firmware:       iwlwifi-2030-6.ucode
firmware:       iwlwifi-2000-6.ucode
firmware:       iwlwifi-5150-2.ucode
firmware:       iwlwifi-5000-5.ucode
firmware:       iwlwifi-6000g2b-6.ucode
firmware:       iwlwifi-6000g2a-5.ucode
firmware:       iwlwifi-6050-5.ucode
firmware:       iwlwifi-6000-4.ucode
firmware:       iwlwifi-7265-7.ucode
firmware:       iwlwifi-3160-7.ucode
firmware:       iwlwifi-7260-7.ucode
srcversion:     C2D0F3DFCA289585C100E36
depends:        cfg80211
parm:           swcrypto:using crypto in software (default 0 [hardware]) (int)
parm:           11n_disable:disable 11n functionality, bitmap: 1: full, 2: disable agg TX, 4: disable agg RX, 8 enable agg TX (uint)
parm:           amsdu_size_8K:enable 8K amsdu size (default 0) (int)
parm:           fw_restart:restart firmware in case of error (default true) (bool)
parm:           antenna_coupling:specify antenna coupling in dB (defualt: 0 dB) (int)
parm:           wd_disable:Disable stuck queue watchdog timer 0=system default, 1=disable, 2=enable (default: 0) (int)
parm:           nvm_file:NVM file name (charp)
parm:           bt_coex_active:enable wifi/bt co-exist (default: enable) (bool)
parm:           led_mode:0=system default, 1=On(RF On)/Off(RF Off), 2=blinking, 3=Off (default: 0) (int)
parm:           power_save:enable WiFi power management (default: disable) (bool)
parm:           power_level:default power save level (range from 1 - 5, default: 1) (int)

[asus_nb_wmi]
filename:       /lib/modules/3.13.0-35-generic/kernel/drivers/platform/x86/asus-nb-wmi.ko
srcversion:     67514DF02FC4A206C47D0F5
depends:        asus-wmi
parm:           wapf:WAPF value (uint)

[asus_wmi]
filename:       /lib/modules/3.13.0-35-generic/kernel/drivers/platform/x86/asus-wmi.ko
srcversion:     222BD5E26B3EE82CC433FF2
depends:        sparse-keymap,wmi,video

[cfg80211]
filename:       /lib/modules/3.13.0-35-generic/kernel/net/wireless/cfg80211.ko
srcversion:     C2478077E22138832B71659
depends:        
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

[wmi]
filename:       /lib/modules/3.13.0-35-generic/kernel/drivers/platform/x86/wmi.ko
srcversion:     CED5410F008DC70DF5F064B
depends:        
parm:           debug_event:Log WMI Events [0/1] (bool)
parm:           debug_dump_wdg:Dump available WMI interfaces [0/1] (bool)

[video]
filename:       /lib/modules/3.13.0-35-generic/kernel/drivers/acpi/video.ko
srcversion:     3D537E78F15014033076CAC
depends:        
parm:           brightness_switch_enabled:bool
parm:           allow_duplicates:bool
parm:           use_native_backlight:int


udev rules ~~~~~~~~~~~~~~~~~~~~~~~~~

# PCI device 0x11ab:/sys/devices/pci0000:00/0000:00:1c.3/0000:06:00.0 (sky2)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC eth0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

# PCI device 0x168c:/sys/devices/pci0000:00/0000:00:1c.0/0000:02:00.0 (ath5k)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC wlan0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

# PCI device 0x8086:/sys/devices/pci0000:00/0000:00:1c.1/0000:02:00.0 (iwlwifi)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC wlan1>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan1"

# USB device 0x7392:0x7711 (usb)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC wlan2>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan2"

# PCI device 0x1969:/sys/devices/pci0000:00/0000:00:1c.5/0000:04:00.0 (atl1c)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC eth1>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth1"


Custom files/entries ~~~~~~~~~~~~~~~

/etc/modules        : Default
/etc/rc.local       : Default
/etc/modprobe.d     : Not Default
/etc/pm/(cnf|pw|sl) : Default

[/etc/modprobe.d]
iwlwifi.conf      : options iwlwifi bt_coex_active=N swcrypto=1
mlx4.conf         : softdep mlx4_core post: mlx4_en
qemu-kvm.conf     : options kvm_intel nested=1
qemu-system-x86.conf: options kvm_intel nested=1


Kernel boot line ~~~~~~~~~~~~~~~~~~~

BOOT_IMAGE=/boot/vmlinuz-3.13.0-35-generic root=UUID=fea3f4e7-9562-42ac-a394-6578371f3d2e ro quiet splash vt.handoff=7


dmesg ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

[    1.002742] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[    1.003082] audit: initializing netlink socket (disabled)
[    1.546536] wmi: Mapper loaded
[    2.546870] psmouse serio4: elantech: assuming hardware version 3 (with firmware version 0x450f01)
[   18.016317] systemd-udevd[342]: renamed network interface eth0 to eth1
[   18.289062] asus_wmi: ASUS WMI generic driver loaded
[   18.294084] asus_wmi: Initialization: 0x1
[   18.294127] asus_wmi: BIOS WMI version: 7.6
[   18.294189] asus_wmi: SFUN value: 0x1a0877
[   18.295061] input: Asus WMI hotkeys as /devices/platform/asus-nb-wmi/input/input16
[   18.359600] iwlwifi 0000:02:00.0: can't disable ASPM; OS doesn't have ASPM control
[   18.359662] iwlwifi 0000:02:00.0: irq 53 for MSI/MSI-X
[   18.388806] asus_wmi: Backlight controlled by ACPI video driver
[   18.664784] iwlwifi 0000:02:00.0: loaded firmware version 18.168.6.1 op_mode iwldvm
[   18.807873] iwlwifi 0000:02:00.0: CONFIG_IWLWIFI_DEBUG disabled
[   18.807878] iwlwifi 0000:02:00.0: CONFIG_IWLWIFI_DEBUGFS enabled
[   18.807880] iwlwifi 0000:02:00.0: CONFIG_IWLWIFI_DEVICE_TRACING enabled
[   18.807883] iwlwifi 0000:02:00.0: Detected Intel(R) Centrino(R) Wireless-N 1030 BGN, REV=0xB0
[   18.807939] iwlwifi 0000:02:00.0: L1 Disabled; Enabling L0S
[   18.870644] ieee80211 phy0: Selected rate control algorithm 'iwl-agn-rs'
[   18.979285] systemd-udevd[342]: renamed network interface wlan0 to wlan1
[   22.441668] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   24.908490] iwlwifi 0000:02:00.0: L1 Disabled; Enabling L0S
[   24.915288] iwlwifi 0000:02:00.0: Radio type=0x2-0x2-0x1
[   24.984100] iwlwifi 0000:02:00.0: L1 Disabled; Enabling L0S
[   24.990891] iwlwifi 0000:02:00.0: Radio type=0x2-0x2-0x1
[   25.076789] IPv6: ADDRCONF(NETDEV_UP): wlan1: link is not ready
[   25.084867] IPv6: ADDRCONF(NETDEV_UP): wlan1: link is not ready
[   25.109014] IPv6: ADDRCONF(NETDEV_UP): eth1: link is not ready
[   25.111834] IPv6: ADDRCONF(NETDEV_UP): eth1: link is not ready
[   26.423943] wlan1: authenticate with <MAC C-NA volia23 1>
[   26.434796] wlan1: send auth to <MAC C-NA volia23 1> (try 1/3)
[   26.437199] wlan1: authenticated
[   26.439364] wlan1: associate with <MAC C-NA volia23 1> (try 1/3)
[   26.443494] wlan1: RX AssocResp from <MAC C-NA volia23 1> (capab=0x431 status=0 aid=4)
[   26.450406] wlan1: associated
[   26.450417] IPv6: ADDRCONF(NETDEV_CHANGE): wlan1: link becomes ready
[  278.360126] iwlwifi 0000:02:00.0: Error sending POWER_TABLE_CMD: time out after 2000ms.
[  278.360139] iwlwifi 0000:02:00.0: Current CMD queue read_ptr 243 write_ptr 244
[  278.360146] iwlwifi 0000:02:00.0: Loaded firmware version: 18.168.6.1
[  278.377477] WARNING: CPU: 0 PID: 141 at /build/buildd/linux-3.13.0/drivers/net/wireless/iwlwifi/pcie/trans.c:1008 iwl_trans_pcie_grab_nic_access+0xc6/0xd0 [iwlwifi]()
[  278.377485] Modules linked in: nf_conntrack_ipv6 nf_defrag_ipv6 xt_tcpudp nf_conntrack_ipv4 nf_defrag_ipv4 xt_conntrack nf_conntrack nls_iso8859_1 xt_multiport ip6table_filter ip6_tables iptable_filter ip_tables x_tables ctr ccm pci_stub vboxpci(OF) vboxnetadp(OF) vboxnetflt(OF) vboxdrv(OF) rfcomm bnep bluetooth binfmt_misc dm_crypt arc4 iwldvm mac80211 uvcvideo videobuf2_vmalloc videobuf2_memops videobuf2_core videodev iwlwifi asus_nb_wmi asus_wmi sparse_keymap snd_hda_codec_hdmi snd_hda_codec_realtek snd_hda_intel snd_hda_codec snd_hwdep cfg80211 snd_pcm intel_rapl x86_pkg_temp_thermal intel_powerclamp snd_page_alloc coretemp snd_seq_midi kvm_intel snd_seq_midi_event snd_rawmidi kvm snd_seq snd_seq_device snd_timer crc32_pclmul snd joydev serio_raw lpc_ich soundcore mei_me mac_hid mei parport_pc ppdev lp parport usb_storage i915 i2c_algo_bit drm_kms_helper drm ahci atl1c psmouse libahci wmi video
[  278.377766]  [<f87458f6>] ? iwl_trans_pcie_grab_nic_access+0xc6/0xd0 [iwlwifi]
[  278.377782]  [<f87458f6>] ? iwl_trans_pcie_grab_nic_access+0xc6/0xd0 [iwlwifi]
[  278.377807]  [<f87458f6>] iwl_trans_pcie_grab_nic_access+0xc6/0xd0 [iwlwifi]
[  278.377825]  [<f87466f2>] iwl_trans_pcie_read_mem+0x22/0x100 [iwlwifi]
[  278.377841]  [<f95670fe>] iwl_dump_nic_error_log+0xbe/0x890 [iwldvm]
[  278.377902]  [<f873afb6>] ? __iwl_err+0x46/0xa0 [iwlwifi]
[  278.377918]  [<f956a543>] iwl_nic_error+0x43/0x60 [iwldvm]
[  278.377936]  [<f8743c47>] iwl_trans_pcie_send_hcmd+0x547/0x710 [iwlwifi]
[  278.377966]  [<f9573483>] iwl_dvm_send_cmd+0x43/0x110 [iwldvm]
[  278.377982]  [<f957384f>] iwl_dvm_send_cmd_pdu+0x3f/0x50 [iwldvm]
[  278.378000]  [<f957bada>] iwl_power_set_mode+0x1fa/0x340 [iwldvm]
[  278.378018]  [<f957bcb6>] iwl_power_update_mode+0x96/0x150 [iwldvm]
[  278.378036]  [<f957f903>] iwlagn_mac_config+0x2e3/0x3a0 [iwldvm]
[  278.378317] iwlwifi 0000:02:00.0: Start IWL Error Log Dump:
[  278.378324] iwlwifi 0000:02:00.0: Status: 0x0000204C, count: 64
[  278.378330] iwlwifi 0000:02:00.0: 0xF7B7E4E8 | ADVANCED_SYSASSERT          
[  278.378335] iwlwifi 0000:02:00.0: 0xF7B7E4B8 | uPc
[  278.378339] iwlwifi 0000:02:00.0: 0xF7B7E488 | branchlink1
[  278.378344] iwlwifi 0000:02:00.0: 0x00000003 | branchlink2
[  278.378349] iwlwifi 0000:02:00.0: 0x781C4C56 | interruptlink1
[  278.378363] iwlwifi 0000:02:00.0: 0x1394EFF3 | interruptlink2
[  278.378381] iwlwifi 0000:02:00.0: 0xC1B87C00 | data1
[  278.378395] iwlwifi 0000:02:00.0: 0x866228AF | data2
[  278.378409] iwlwifi 0000:02:00.0: 0xF0371F20 | line
[  278.378424] iwlwifi 0000:02:00.0: 0xF8750430 | beacon time
[  278.378438] iwlwifi 0000:02:00.0: 0xEF85BE80 | tsf low
[  278.378453] iwlwifi 0000:02:00.0: 0xF5DD5C54 | tsf hi
[  278.378467] iwlwifi 0000:02:00.0: 0xC1409A0F | time gp1
[  278.378482] iwlwifi 0000:02:00.0: 0xF5DD5C68 | time gp2
[  278.378496] iwlwifi 0000:02:00.0: 0xF5DD5C7C | time gp3
[  278.378510] iwlwifi 0000:02:00.0: 0xC1409DA8 | uCode version
[  278.378522] iwlwifi 0000:02:00.0: 0x00000003 | hw version
[  278.378536] iwlwifi 0000:02:00.0: 0xF03A1864 | board version
[  278.378551] iwlwifi 0000:02:00.0: 0xF5DD5C88 | hcmd
[  278.378562] iwlwifi 0000:02:00.0: 0xEB024DE8 | isr0
[  278.378567] iwlwifi 0000:02:00.0: 0xF5DD5CA8 | isr1
[  278.378571] iwlwifi 0000:02:00.0: 0xF5DD5C90 | isr2
[  278.378576] iwlwifi 0000:02:00.0: 0xC1409EDD | isr3
[  278.378580] iwlwifi 0000:02:00.0: 0xF5DD5CA0 | isr4
[  278.378585] iwlwifi 0000:02:00.0: 0xF875023D | isr_pref
[  278.378589] iwlwifi 0000:02:00.0: 0xF5DD5C84 | wait_event
[  278.378594] iwlwifi 0000:02:00.0: 0xF5DD5CB8 | l2p_control
[  278.378598] iwlwifi 0000:02:00.0: 0xF873AFB6 | l2p_duration
[  278.378603] iwlwifi 0000:02:00.0: 0xF03A1864 | l2p_mhvalid
[  278.378607] iwlwifi 0000:02:00.0: 0xF875023D | l2p_addr_match
[  278.378612] iwlwifi 0000:02:00.0: 0xF5DD5CA8 | lmpm_pmg_sel
[  278.378619] iwlwifi 0000:02:00.0: 0xF5DD5CD0 | timestamp
[  278.378633] iwlwifi 0000:02:00.0: 0xF958D7EC | flow_handler
[  278.395992] WARNING: CPU: 0 PID: 141 at /build/buildd/linux-3.13.0/drivers/net/wireless/iwlwifi/dvm/../iwl-trans.h:743 iwl_dump_nic_event_log+0x33b/0x380 [iwldvm]()
[  278.395995] Modules linked in: nf_conntrack_ipv6 nf_defrag_ipv6 xt_tcpudp nf_conntrack_ipv4 nf_defrag_ipv4 xt_conntrack nf_conntrack nls_iso8859_1 xt_multiport ip6table_filter ip6_tables iptable_filter ip_tables x_tables ctr ccm pci_stub vboxpci(OF) vboxnetadp(OF) vboxnetflt(OF) vboxdrv(OF) rfcomm bnep bluetooth binfmt_misc dm_crypt arc4 iwldvm mac80211 uvcvideo videobuf2_vmalloc videobuf2_memops videobuf2_core videodev iwlwifi asus_nb_wmi asus_wmi sparse_keymap snd_hda_codec_hdmi snd_hda_codec_realtek snd_hda_intel snd_hda_codec snd_hwdep cfg80211 snd_pcm intel_rapl x86_pkg_temp_thermal intel_powerclamp snd_page_alloc coretemp snd_seq_midi kvm_intel snd_seq_midi_event snd_rawmidi kvm snd_seq snd_seq_device snd_timer crc32_pclmul snd joydev serio_raw lpc_ich soundcore mei_me mac_hid mei parport_pc ppdev lp parport usb_storage i915 i2c_algo_bit drm_kms_helper drm ahci atl1c psmouse libahci wmi video
[  278.396241]  [<f956a4bb>] ? iwl_dump_nic_event_log+0x33b/0x380 [iwldvm]
[  278.396254]  [<f956a4bb>] ? iwl_dump_nic_event_log+0x33b/0x380 [iwldvm]
[  278.396277]  [<f956a4bb>] iwl_dump_nic_event_log+0x33b/0x380 [iwldvm]
[  278.396304]  [<f873afb6>] ? __iwl_err+0x46/0xa0 [iwlwifi]
[  278.396319]  [<f956a54e>] iwl_nic_error+0x4e/0x60 [iwldvm]
[  278.396338]  [<f8743c47>] iwl_trans_pcie_send_hcmd+0x547/0x710 [iwlwifi]
[  278.396368]  [<f9573483>] iwl_dvm_send_cmd+0x43/0x110 [iwldvm]
[  278.396384]  [<f957384f>] iwl_dvm_send_cmd_pdu+0x3f/0x50 [iwldvm]
[  278.396402]  [<f957bada>] iwl_power_set_mode+0x1fa/0x340 [iwldvm]
[  278.396420]  [<f957bcb6>] iwl_power_update_mode+0x96/0x150 [iwldvm]
[  278.396439]  [<f957f903>] iwlagn_mac_config+0x2e3/0x3a0 [iwldvm]
[  278.414062] WARNING: CPU: 0 PID: 141 at /build/buildd/linux-3.13.0/drivers/net/wireless/iwlwifi/dvm/../iwl-trans.h:743 iwl_dump_nic_event_log+0x320/0x380 [iwldvm]()
[  278.414082] Modules linked in: nf_conntrack_ipv6 nf_defrag_ipv6 xt_tcpudp nf_conntrack_ipv4 nf_defrag_ipv4 xt_conntrack nf_conntrack nls_iso8859_1 xt_multiport ip6table_filter ip6_tables iptable_filter ip_tables x_tables ctr ccm pci_stub vboxpci(OF) vboxnetadp(OF) vboxnetflt(OF) vboxdrv(OF) rfcomm bnep bluetooth binfmt_misc dm_crypt arc4 iwldvm mac80211 uvcvideo videobuf2_vmalloc videobuf2_memops videobuf2_core videodev iwlwifi asus_nb_wmi asus_wmi sparse_keymap snd_hda_codec_hdmi snd_hda_codec_realtek snd_hda_intel snd_hda_codec snd_hwdep cfg80211 snd_pcm intel_rapl x86_pkg_temp_thermal intel_powerclamp snd_page_alloc coretemp snd_seq_midi kvm_intel snd_seq_midi_event snd_rawmidi kvm snd_seq snd_seq_device snd_timer crc32_pclmul snd joydev serio_raw lpc_ich soundcore mei_me mac_hid mei parport_pc ppdev lp parport usb_storage i915 i2c_algo_bit drm_kms_helper drm ahci atl1c psmouse libahci wmi video
[  278.414497]  [<f956a4a0>] ? iwl_dump_nic_event_log+0x320/0x380 [iwldvm]
[  278.414509]  [<f956a4a0>] ? iwl_dump_nic_event_log+0x320/0x380 [iwldvm]
[  278.414533]  [<f956a4a0>] iwl_dump_nic_event_log+0x320/0x380 [iwldvm]
[  278.414559]  [<f873afb6>] ? __iwl_err+0x46/0xa0 [iwlwifi]
[  278.414573]  [<f956a54e>] iwl_nic_error+0x4e/0x60 [iwldvm]
[  278.414593]  [<f8743c47>] iwl_trans_pcie_send_hcmd+0x547/0x710 [iwlwifi]
[  278.414623]  [<f9573483>] iwl_dvm_send_cmd+0x43/0x110 [iwldvm]
[  278.414667]  [<f957384f>] iwl_dvm_send_cmd_pdu+0x3f/0x50 [iwldvm]
[  278.414712]  [<f957bada>] iwl_power_set_mode+0x1fa/0x340 [iwldvm]
[  278.414762]  [<f957bcb6>] iwl_power_update_mode+0x96/0x150 [iwldvm]
[  278.414792]  [<f957f903>] iwlagn_mac_config+0x2e3/0x3a0 [iwldvm]
[  278.432476] WARNING: CPU: 0 PID: 141 at /build/buildd/linux-3.13.0/drivers/net/wireless/iwlwifi/dvm/../iwl-trans.h:743 iwl_dump_nic_event_log+0x356/0x380 [iwldvm]()
[  278.432481] Modules linked in: nf_conntrack_ipv6 nf_defrag_ipv6 xt_tcpudp nf_conntrack_ipv4 nf_defrag_ipv4 xt_conntrack nf_conntrack nls_iso8859_1 xt_multiport ip6table_filter ip6_tables iptable_filter ip_tables x_tables ctr ccm pci_stub vboxpci(OF) vboxnetadp(OF) vboxnetflt(OF) vboxdrv(OF) rfcomm bnep bluetooth binfmt_misc dm_crypt arc4 iwldvm mac80211 uvcvideo videobuf2_vmalloc videobuf2_memops videobuf2_core videodev iwlwifi asus_nb_wmi asus_wmi sparse_keymap snd_hda_codec_hdmi snd_hda_codec_realtek snd_hda_intel snd_hda_codec snd_hwdep cfg80211 snd_pcm intel_rapl x86_pkg_temp_thermal intel_powerclamp snd_page_alloc coretemp snd_seq_midi kvm_intel snd_seq_midi_event snd_rawmidi kvm snd_seq snd_seq_device snd_timer crc32_pclmul snd joydev serio_raw lpc_ich soundcore mei_me mac_hid mei parport_pc ppdev lp parport usb_storage i915 i2c_algo_bit drm_kms_helper drm ahci atl1c psmouse libahci wmi video
[  278.432746]  [<f956a4d6>] ? iwl_dump_nic_event_log+0x356/0x380 [iwldvm]
[  278.432759]  [<f956a4d6>] ? iwl_dump_nic_event_log+0x356/0x380 [iwldvm]
[  278.432782]  [<f956a4d6>] iwl_dump_nic_event_log+0x356/0x380 [iwldvm]
[  278.432807]  [<f956a54e>] iwl_nic_error+0x4e/0x60 [iwldvm]
[  278.432826]  [<f8743c47>] iwl_trans_pcie_send_hcmd+0x547/0x710 [iwlwifi]
[  278.432854]  [<f9573483>] iwl_dvm_send_cmd+0x43/0x110 [iwldvm]
[  278.432870]  [<f957384f>] iwl_dvm_send_cmd_pdu+0x3f/0x50 [iwldvm]
[  278.432887]  [<f957bada>] iwl_power_set_mode+0x1fa/0x340 [iwldvm]
[  278.432904]  [<f957bcb6>] iwl_power_update_mode+0x96/0x150 [iwldvm]
[  278.432922]  [<f957f903>] iwlagn_mac_config+0x2e3/0x3a0 [iwldvm]
[  278.450522] WARNING: CPU: 0 PID: 141 at /build/buildd/linux-3.13.0/drivers/net/wireless/iwlwifi/dvm/../iwl-trans.h:743 iwl_dump_nic_event_log+0x371/0x380 [iwldvm]()
[  278.450541] Modules linked in: nf_conntrack_ipv6 nf_defrag_ipv6 xt_tcpudp nf_conntrack_ipv4 nf_defrag_ipv4 xt_conntrack nf_conntrack nls_iso8859_1 xt_multiport ip6table_filter ip6_tables iptable_filter ip_tables x_tables ctr ccm pci_stub vboxpci(OF) vboxnetadp(OF) vboxnetflt(OF) vboxdrv(OF) rfcomm bnep bluetooth binfmt_misc dm_crypt arc4 iwldvm mac80211 uvcvideo videobuf2_vmalloc videobuf2_memops videobuf2_core videodev iwlwifi asus_nb_wmi asus_wmi sparse_keymap snd_hda_codec_hdmi snd_hda_codec_realtek snd_hda_intel snd_hda_codec snd_hwdep cfg80211 snd_pcm intel_rapl x86_pkg_temp_thermal intel_powerclamp snd_page_alloc coretemp snd_seq_midi kvm_intel snd_seq_midi_event snd_rawmidi kvm snd_seq snd_seq_device snd_timer crc32_pclmul snd joydev serio_raw lpc_ich soundcore mei_me mac_hid mei parport_pc ppdev lp parport usb_storage i915 i2c_algo_bit drm_kms_helper drm ahci atl1c psmouse libahci wmi video
[  278.450975]  [<f956a4f1>] ? iwl_dump_nic_event_log+0x371/0x380 [iwldvm]
[  278.450988]  [<f956a4f1>] ? iwl_dump_nic_event_log+0x371/0x380 [iwldvm]
[  278.451011]  [<f956a4f1>] iwl_dump_nic_event_log+0x371/0x380 [iwldvm]
[  278.451035]  [<f956a54e>] iwl_nic_error+0x4e/0x60 [iwldvm]
[  278.451055]  [<f8743c47>] iwl_trans_pcie_send_hcmd+0x547/0x710 [iwlwifi]
[  278.451083]  [<f9573483>] iwl_dvm_send_cmd+0x43/0x110 [iwldvm]
[  278.451098]  [<f957384f>] iwl_dvm_send_cmd_pdu+0x3f/0x50 [iwldvm]
[  278.451115]  [<f957bada>] iwl_power_set_mode+0x1fa/0x340 [iwldvm]
[  278.451132]  [<f957bcb6>] iwl_power_update_mode+0x96/0x150 [iwldvm]
[  278.451150]  [<f957f903>] iwlagn_mac_config+0x2e3/0x3a0 [iwldvm]
[  278.451379] iwlwifi 0000:02:00.0: Log capacity -1515870811 is bogus, limit to 1 entries
[  278.451385] iwlwifi 0000:02:00.0: Log write index -1515870811 is bogus, limit to 1
[  278.451390] iwlwifi 0000:02:00.0: Start IWL Event Log Dump: display last 1 entries
[  278.468737] iwlwifi 0000:02:00.0: set power fail, ret = -110
[  280.228935] iwlwifi 0000:02:00.0: Failing on timeout while stopping DMA channel 0 [0x5a5a5a5a]
[  282.002101] iwlwifi 0000:02:00.0: Failing on timeout while stopping DMA channel 2 [0x5a5a5a5a]
[  283.809424] iwlwifi 0000:02:00.0: Failing on timeout while stopping DMA channel 5 [0x5a5a5a5a]
[  285.582557] iwlwifi 0000:02:00.0: Failing on timeout while stopping DMA channel 7 [0x5a5a5a5a]
[  287.347160] iwlwifi 0000:02:00.0: iwl_trans_wait_tx_queue_empty bad state = 0
[  287.347218] iwlwifi 0000:02:00.0: Fw not loaded - dropping CMD: 18
[  287.347225] wlan1: HW problem - can not stop rx aggregation for <MAC C-NA volia23 1> tid 0
[  287.347234] iwlwifi 0000:02:00.0: Fw not loaded - dropping CMD: 18
[  287.347238] wlan1: HW problem - can not stop rx aggregation for <MAC C-NA volia23 1> tid 4
[  287.347410] iwlwifi 0000:02:00.0: iwl_trans_wait_tx_queue_empty bad state = 0
[  287.348517] iwlwifi 0000:02:00.0: L1 Enabled; Disabling L0S
[  287.417777] iwlwifi 0000:02:00.0: Radio type=0x2-0x2-0x1
[  293.090544] iwlwifi 0000:02:00.0: Failed to load firmware chunk!
[  293.090559] iwlwifi 0000:02:00.0: Could not load the [0] uCode section
[  293.090572] iwlwifi 0000:02:00.0: Failed to start RT ucode: -110
[  294.872937] iwlwifi 0000:02:00.0: Failing on timeout while stopping DMA channel 0 [0x5a5a5a5a]
[  296.649627] iwlwifi 0000:02:00.0: Failing on timeout while stopping DMA channel 2 [0x5a5a5a5a]
[  298.456821] iwlwifi 0000:02:00.0: Failing on timeout while stopping DMA channel 5 [0x5a5a5a5a]
[  300.230035] iwlwifi 0000:02:00.0: Failing on timeout while stopping DMA channel 7 [0x5a5a5a5a]
[  301.994745] iwlwifi 0000:02:00.0: Unable to initialize device.
[  301.996940] iwlwifi 0000:02:00.0: Request scan called when driver not ready.
[  435.642555] atl1c 0000:04:00.0: atl1c: eth1 NIC Link is Up<1000 Mbps Full Duplex>
[  435.642591] IPv6: ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
[ 1144.341592] iwlwifi 0000:02:00.0: Request scan called when driver not ready.

    ======== Done ========
```

Help me please.

---

### Post by praseodym on 2014-09-18
> ```
resolv.conf ~~~~~~~~~~~~~~~~~~~~~~~~

domain isd.dp.ua
nameserver 10.98.0.2
nameserver 10.98.0.1
nameserver 127.0.1.1
search isd.dp.ua 
```
These are your nameservers and domains?

---

### Post by weatherman2 on 2014-09-18
> **10barabas said:**
> Hello,
   Nothing helped me. I've tried all recomended module parameters. Such as bt_coex_active=N swcrypto=1 11n_disable=1. Parameter 11n_disable makes things even much worth it doesn't connect at all with it. 

We've seen several reports here that for 14.04, this parameter can work better for the Intel iwlwifi driver when you are having problems:

```

[COLOR=#000000]modprobe -v iwlwifi 11n_disable=8

```

[/COLOR]

---

### Post by jeremy31 on 2014-09-18
```
WARNING: CPU: 0 PID: 141 at /build/buildd/linux-3.13.0/drivers/net/wireless/iwlwifi/pcie/trans.c:1008 iwl_trans_pcie_grab_nic_access+0xc6/0xd0 [iwlwifi]()
[  278.377485] Modules linked in: nf_conntrack_ipv6 nf_defrag_ipv6 xt_tcpudp nf_conntrack_ipv4 nf_defrag_ipv4 xt_conntrack nf_conntrack nls_iso8859_1 xt_multiport ip6table_filter ip6_tables iptable_filter ip_tables x_tables ctr ccm pci_stub vboxpci(OF) vboxnetadp(OF) vboxnetflt(OF) vboxdrv(OF) rfcomm bnep bluetooth binfmt_misc dm_crypt arc4 iwldvm mac80211 uvcvideo videobuf2_vmalloc videobuf2_memops videobuf2_core videodev iwlwifi asus_nb_wmi asus_wmi sparse_keymap snd_hda_codec_hdmi snd_hda_codec_realtek snd_hda_intel snd_hda_codec snd_hwdep cfg80211 snd_pcm intel_rapl x86_pkg_temp_thermal intel_powerclamp snd_page_alloc coretemp snd_seq_midi kvm_intel snd_seq_midi_event snd_rawmidi kvm snd_seq snd_seq_device snd_timer crc32_pclmul snd joydev serio_raw lpc_ich soundcore mei_me mac_hid mei parport_pc ppdev lp parport usb_storage i915 i2c_algo_bit drm_kms_helper drm ahci atl1c psmouse libahci wmi video
[  278.377766]  [<f87458f6>] ? iwl_trans_pcie_grab_nic_access+0xc6/0xd0 [iwlwifi]
[  278.377782]  [<f87458f6>] ? iwl_trans_pcie_grab_nic_access+0xc6/0xd0 [iwlwifi]
[  278.377807]  [<f87458f6>] iwl_trans_pcie_grab_nic_access+0xc6/0xd0 [iwlwifi]
[  278.377825]  [<f87466f2>] iwl_trans_pcie_read_mem+0x22/0x100 [iwlwifi]
[  278.377841]  [<f95670fe>] iwl_dump_nic_error_log+0xbe/0x890 [iwldvm]
[  278.377902]  [<f873afb6>] ? __iwl_err+0x46/0xa0 [iwlwifi]
[  278.377918]  [<f956a543>] iwl_nic_error+0x43/0x60 [iwldvm]
[  278.377936]  [<f8743c47>] iwl_trans_pcie_send_hcmd+0x547/0x710 [iwlwifi]
[  278.377966]  [<f9573483>] iwl_dvm_send_cmd+0x43/0x110 [iwldvm]
[  278.377982]  [<f957384f>] iwl_dvm_send_cmd_pdu+0x3f/0x50 [iwldvm]
[  278.378000]  [<f957bada>] iwl_power_set_mode+0x1fa/0x340 [iwldvm]
[  278.378018]  [<f957bcb6>] iwl_power_update_mode+0x96/0x150 [iwldvm]
[  278.378036]  [<f957f903>] iwlagn_mac_config+0x2e3/0x3a0 [iwldvm]
[  278.378317] iwlwifi 0000:02:00.0: Start IWL Error Log Dump:
```

Might be a sign of a hardware issue

---

### Post by 10barabas on 2014-09-19
[**[COLOR=#000000]weatherman2[/COLOR]**]("http://ubuntuforums.org/member.php?u=1931279"), I've added 11n_disable=8 and nothing changed. The problem still exists.
[**[COLOR=#000000]jeremy31[/COLOR]**]("http://ubuntuforums.org/member.php?u=1924242"), the issue appeared just after upgrade to 14.04.

---

### Post by jeremy31 on 2014-09-19
What did you upgrade from?  Do you still have the install disc/USB/whatever from the previous version to see if it works properly then?

---

