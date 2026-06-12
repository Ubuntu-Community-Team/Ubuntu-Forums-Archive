---
title: "Wifi connect problem (TP-Link TL-WN8200ND)"
date: 2014-09-13
forum: Networking &amp; Wireless
---

### Post by belarrius on 2014-09-13
Hello, 

I recently purchase a Wifi "TP-Link TL-WN8200ND" antenna 

OS: Ubuntu 14.04, Kernel 3.13 

I plug in, it is recognized, it detects wireless networks. I connect it can not connect ... 

I'm rtl8192cu Ubuntu base. I even tested with the 3.17 kernel but does not change its ... 

Do you have any idea?

---

### Post by varunendra on 2014-09-14
Have you tried the "rtl8192cu-fixes" yet? If not, please try : [http://ubuntuforums.org/showpost.php?p=13026049](http://ubuntuforums.org/showpost.php?p=13026049)

---

### Post by belarrius on 2014-09-14
> **varunendra said:**
> Have you tried the "rtl8192cu-fixes" yet? If not, please try : [http://ubuntuforums.org/showpost.php?p=13026049](http://ubuntuforums.org/showpost.php?p=13026049)

Hi! :D

Yes, i have already test that, i have search on google since 2 days... 

See [http://linux-wless.passys.nl/query_part.php?brandname=TP-Link](http://linux-wless.passys.nl/query_part.php?brandname=TP-Link) It's yellow :/





   I will change my wifi with another

---

### Post by varunendra on 2014-09-14
Please show us a wireless_script report : [http://ubuntuforums.org/showpost.php?p=13024222](http://ubuntuforums.org/showpost.php?p=13024222)

---

### Post by belarrius on 2014-09-14
```

    ======== Wireless-Info START ========

System-Info ~~~~~~~~~~~~~~~~~~~~~~~~

belarrius-computer 3.17.0-031700rc4-generic x86_64,  Ubuntu 14.04.1 LTS, trusty

CPU    : AMD FX(tm)-8320 Eight-Core Processor
Memory : 7900 MB
Uptime : 00:44:30 up 11:31,  2 users,  load average: 0,89, 1,03, 1,39


lspci ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 09)
    Subsystem: ASUSTeK Computer Inc. P8H77-I Motherboard [1043:8505]
    Kernel driver in use: r8169


lsusb ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 011 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 010 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 003: ID 2357:0100  
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 009 Device 004: ID 046d:c222 Logitech, Inc. G15 Keyboard / LCD
Bus 009 Device 003: ID 046d:c221 Logitech, Inc. G11/G15 Keyboard / Keyboard
Bus 009 Device 002: ID 046d:c223 Logitech, Inc. G11/G15 Keyboard / USB Hub
Bus 009 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 046d:0805 Logitech, Inc. Webcam C300
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 008 Device 002: ID e0ff:0002  
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 006 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 002: ID 04e8:61b6 Samsung Electronics Co., Ltd 
Bus 005 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 004 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


PCMCIA Card Info ~~~~~~~~~~~~~~~~~~~



iwconfig ~~~~~~~~~~~~~~~~~~~~~~~~~~~

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry short limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          


rfkill ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

      Interface        Soft blocked  Hard blocked
0: phy0: Wireless LAN      no            no


lsmod ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

eeepc_wmi              13151  0 
asus_wmi               24697  1 eeepc_wmi
sparse_keymap          13890  1 asus_wmi
video                  20569  1 asus_wmi
mxm_wmi                13021  0 
wmi                    19379  2 mxm_wmi,asus_wmi
rtl8192cu              68579  0 
rtl_usb                22809  1 rtl8192cu
rtlwifi                69157  2 rtl_usb,rtl8192cu
rtl8192c_common        58270  1 rtl8192cu
mac80211              696913  3 rtl_usb,rtlwifi,rtl8192cu
cfg80211              514757  2 mac80211,rtlwifi


module parameters ~~~~~~~~~~~~~~~~~~

cfg80211      (2): cfg80211_disable_40mhz_24ghz=N | ieee80211_regdom=00
eeepc_wmi     (1): hotplug_wireless=N
mac80211      (5): beacon_loss_count=7 | ieee80211_default_rc_algo=minstrel_ht | max_nullfunc_tries=2 | max_probe_tries=5 | probe_wait_ms=500
rtl8192cu     (2): debug=0 | swenc=N
video         (3): allow_duplicates=N | brightness_switch_enabled=Y | use_native_backlight=-1
wmi           (2): debug_dump_wdg=N | debug_event=N


nm-tool ~~~~~~~~~~~~~~~~~~~~~~~~~~~~

State: disconnected
================o=============o===========o=======  =======o=========o===========o==============o=====  ======
 Interface & ID | Type        | Driver    | State        | Default | Speed     | Support      | HW Addr   
================o=============o===========o=======  =======o=========o===========o==============o=====  ======
 wlan0          | 802.11 WiFi | rtl8192cu | disconnected | no      |           | WEP/WPA/WPA2 | <MAC wlan0>

    FreeWifi_secure: Infra, <MAC C-NA FreeWifi_secure 1>, Freq 2462 MHz, Rate 54 Mb/s, Strength 64 WPA2 Enterprise
    Belarrius Wi-Fi: Infra, <MAC C-01 Belarrius Wi-Fi>, Freq 2422 MHz, Rate 54 Mb/s, Strength 94 WPA2
----------------+-------------+-----------+--------------+---------+-----------+--------------+-----------
 eth0           | Wired       | r8169     | unavailable  | no      | 100 Mb/s  |              | <MAC eth0>
----------------+-------------+-----------+--------------+---------+-----------+--------------+-----------


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

no-auto-default=<MAC eth0>,

[ifupdown]
managed=false


NM WiFi Profiles ~~~~~~~~~~~~~~~~~~~

Belarrius Wi-Fi      : ssid=Belarrius Wi-Fi | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 


interfaces ~~~~~~~~~~~~~~~~~~~~~~~~~

# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback

resolv.conf ~~~~~~~~~~~~~~~~~~~~~~~~



Routes & Ping ~~~~~~~~~~~~~~~~~~~~~~

Table de routage IP du noyau
Destination     Passerelle      Genmask         Indic Metric Ref    Use Iface


iw reg get ~~~~~~~~~~~~~~~~~~~~~~~~~

(Region : "fr_FR.UTF-8")
country 00:
    (2402 - 2472 @ 40), (3, 20)
    (2457 - 2482 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (2474 - 2494 @ 20), (3, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
    (5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS


iwlist chan ~~~~~~~~~~~~~~~~~~~~~~~~

wlan0     11 channels in total; available frequencies :
          Channel 01 (2.412 GHz) - 11 (2.462 GHz)


iwlist scan ~~~~~~~~~~~~~~~~~~~~~~~~

wlan0     Scan completed :
          Cell 01 - Address: <MAC C-01 Belarrius Wi-Fi>
                    Channel:3
                    Frequency:2.422 GHz (Channel 3)
                    Quality=70/70  Signal level=-40 dBm  
                    Encryption key:on
                    ESSID:"Belarrius Wi-Fi"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 22 Mb/s
                              6 Mb/s; 9 Mb/s; 12 Mb/s
                    Bit Rates:18 Mb/s; 24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000007a124f015f
                    Extra: Last beacon: 468ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK


blacklist ~~~~~~~~~~~~~~~~~~~~~~~~~~

[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci

[/etc/modprobe.d/blacklist.conf]
blacklist rtl8192cu

[/etc/modprobe.d/blacklist-native-rtl8192.conf]
blacklist rtl8192cu
blacklist rtl8192c_common
blacklist rtlwifi


modinfo ~~~~~~~~~~~~~~~~~~~~~~~~~~~~

[eeepc_wmi]
filename:       /lib/modules/3.17.0-031700rc4-generic/kernel/drivers/platform/x86/eeepc-wmi.ko
srcversion:     063DC0AB014AC1813C17B93
depends:        asus-wmi
parm:           hotplug_wireless:Enable hotplug for wireless device. If your laptop needs that, please report to acpi4asus-user@lists.sourceforge.net. (bool)

[asus_wmi]
filename:       /lib/modules/3.17.0-031700rc4-generic/kernel/drivers/platform/x86/asus-wmi.ko
srcversion:     CC6EE6D8DF9D9328BC6DBBD
depends:        sparse-keymap,wmi,video

[video]
filename:       /lib/modules/3.17.0-031700rc4-generic/kernel/drivers/acpi/video.ko
srcversion:     E5235B51CFF85D5358B8FB6
depends:        
parm:           brightness_switch_enabled:bool
parm:           allow_duplicates:bool
parm:           use_native_backlight:int

[mxm_wmi]
filename:       /lib/modules/3.17.0-031700rc4-generic/kernel/drivers/platform/x86/mxm-wmi.ko
srcversion:     D566C16ECB7E11FB9DF5C84
depends:        wmi

[wmi]
filename:       /lib/modules/3.17.0-031700rc4-generic/kernel/drivers/platform/x86/wmi.ko
srcversion:     2E987FE96F7EBB6BFC7E2B2
depends:        
parm:           debug_event:Log WMI Events [0/1] (bool)
parm:           debug_dump_wdg:Dump available WMI interfaces [0/1] (bool)

[rtl8192cu]
filename:       /lib/modules/3.17.0-031700rc4-generic/kernel/drivers/net/wireless/rtlwifi/rtl8192cu/rtl8192cu.ko
firmware:       rtlwifi/rtl8192cufw_TMSC.bin
firmware:       rtlwifi/rtl8192cufw_B.bin
firmware:       rtlwifi/rtl8192cufw_A.bin
firmware:       rtlwifi/rtl8192cufw.bin
srcversion:     F02D535EF2955F1BB6EE7F3
depends:        rtlwifi,rtl8192c-common,rtl_usb,mac80211
parm:           swenc:Set to 1 for software crypto (default 0)
parm:           debug:Set debug level (0-5) (default 0) (int)

[rtl_usb]
filename:       /lib/modules/3.17.0-031700rc4-generic/kernel/drivers/net/wireless/rtlwifi/rtl_usb.ko
srcversion:     085B283910CF6CA0B4CAE2C
depends:        rtlwifi,mac80211

[rtlwifi]
filename:       /lib/modules/3.17.0-031700rc4-generic/kernel/drivers/net/wireless/rtlwifi/rtlwifi.ko
srcversion:     6105E22C048121BA62ED173
depends:        mac80211,cfg80211

[rtl8192c_common]
filename:       /lib/modules/3.17.0-031700rc4-generic/kernel/drivers/net/wireless/rtlwifi/rtl8192c/rtl8192c-common.ko
srcversion:     A279C50E29ED7F277EAF738
depends:        

[mac80211]
filename:       /lib/modules/3.17.0-031700rc4-generic/kernel/net/mac80211/mac80211.ko
srcversion:     39B2146B20C3BFC7FCCD1E7
depends:        cfg80211
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[cfg80211]
filename:       /lib/modules/3.17.0-031700rc4-generic/kernel/net/wireless/cfg80211.ko
srcversion:     84135F1CCA8E99FC4C5E687
depends:        
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)


udev rules ~~~~~~~~~~~~~~~~~~~~~~~~~

# PCI device 0x10ec:0x8168 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC eth0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

# USB device 0x:0x (rtl8192cu)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC wlan0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

# USB device 0x:0x (rt2800usb)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC wlan1>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan1"


Custom files/entries ~~~~~~~~~~~~~~~

/etc/modules        : Not Default
/etc/rc.local       : Not Default
/etc/modprobe.d     : Not Default
/etc/pm/(cnf|pw|sl) : Default

[/etc/modules]
rtl8192cu
rtl8192cu
8192cu

[/etc/rc.local]
echo "2001 330D" | tee /sys/bus/usb/drivers/rtl8192cu/new_id
exit 0

[/etc/modprobe.d]
iwlwifi.conf      : remove iwlwifi \
                    (/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
                    && /sbin/modprobe -r mac80211
mlx4.conf         : softdep mlx4_core post: mlx4_en


Kernel boot line ~~~~~~~~~~~~~~~~~~~

BOOT_IMAGE=/boot/vmlinuz-3.17.0-031700rc4-generic root=UUID=4928974c-0607-4865-91b4-ccedc391c8e8 ro quiet splash


dmesg ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

[    0.274058] Initializing cgroup subsys net_cls
[    0.274065] Initializing cgroup subsys net_prio
[    1.399126] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[    1.399640] audit: initializing netlink subsys (disabled)
[    1.681491] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[   12.260540] 8192cu: module verification failed: signature and/or  required key missing - tainting kernel
[   12.261405] rtl8192cu driver version=v4.0.2_9000.20130911
[   12.261409] Error: Driver 'rtl8192cu' is already registered, aborting...
[   12.358243] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   12.361850] wmi: Mapper loaded
[   12.631480] asus_wmi: ASUS WMI generic driver loaded
[   12.635002] asus_wmi: Initialization: 0x0
[   12.635031] asus_wmi: BIOS WMI version: 0.9
[   12.635093] asus_wmi: SFUN value: 0x0
[   12.635551] input: Eee PC WMI hotkeys as /devices/platform/eeepc-wmi/input/input10
[   12.637592] asus_wmi: Disabling ACPI video driver
[41489.968447] rtl8192cu: Chip version 0x11
[41490.045041] rtl8192cu: MAC address: <MAC wlan0>
[41490.045046] rtl8192cu: Board Type 0
[41490.045290] rtl_usb: rx_max_size 15360, rx_urb_num 8, in_ep 1
[41490.045336] rtl8192cu: Loading firmware rtlwifi/rtl8192cufw_TMSC.bin
[41490.057355] ieee80211 phy0: Selected rate control algorithm 'rtl_rc'
[41490.061041] rtlwifi: wireless switch is on
[41490.080087] rtl8192cu: MAC auto ON okay!
[41490.113253] rtl8192cu: Tx queue select: 0x05
[41490.484656] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[41509.749984] wlan0: authenticate with <MAC C-01 Belarrius Wi-Fi>
[41509.774610] wlan0: direct probe to <MAC C-01 Belarrius Wi-Fi> (try 1/3)
[41509.978018] wlan0: direct probe to <MAC C-01 Belarrius Wi-Fi> (try 2/3)
[41510.182299] wlan0: direct probe to <MAC C-01 Belarrius Wi-Fi> (try 3/3)
[41510.386591] wlan0: authentication with <MAC C-01 Belarrius Wi-Fi> timed out
[41511.228044] wlan0: authenticate with <MAC C-01 Belarrius Wi-Fi>
[41511.252702] wlan0: direct probe to <MAC C-01 Belarrius Wi-Fi> (try 1/3)
[41511.456071] wlan0: direct probe to <MAC C-01 Belarrius Wi-Fi> (try 2/3)
[41511.660347] wlan0: direct probe to <MAC C-01 Belarrius Wi-Fi> (try 3/3)
[41511.864631] wlan0: authentication with <MAC C-01 Belarrius Wi-Fi> timed out
[41513.106642] wlan0: authenticate with <MAC C-01 Belarrius Wi-Fi>
[41513.131187] wlan0: direct probe to <MAC C-01 Belarrius Wi-Fi> (try 1/3)
[41513.334652] wlan0: direct probe to <MAC C-01 Belarrius Wi-Fi> (try 2/3)
[41513.538953] wlan0: direct probe to <MAC C-01 Belarrius Wi-Fi> (try 3/3)
[41513.743220] wlan0: authentication with <MAC C-01 Belarrius Wi-Fi> timed out
[41515.505944] wlan0: authenticate with <MAC C-01 Belarrius Wi-Fi>
[41515.530431] wlan0: direct probe to <MAC C-01 Belarrius Wi-Fi> (try 1/3)
[41515.733975] wlan0: direct probe to <MAC C-01 Belarrius Wi-Fi> (try 2/3)
[41515.938265] wlan0: direct probe to <MAC C-01 Belarrius Wi-Fi> (try 3/3)
[41516.142542] wlan0: authentication with <MAC C-01 Belarrius Wi-Fi> timed out
[41527.618701] wlan0: authenticate with <MAC C-01 Belarrius Wi-Fi>
[41527.643343] wlan0: direct probe to <MAC C-01 Belarrius Wi-Fi> (try 1/3)
[41527.846734] wlan0: direct probe to <MAC C-01 Belarrius Wi-Fi> (try 2/3)
[41528.051017] wlan0: direct probe to <MAC C-01 Belarrius Wi-Fi> (try 3/3)
[41528.255288] wlan0: authentication with <MAC C-01 Belarrius Wi-Fi> timed out

    ======== Done ========


```

---

### Post by varunendra on 2014-09-15
The native rtl8192cu driver is still the one loading and the intended '8192cu' is not. Please make sure it is installed properly -
```
modinfo 8192cu
```
Does it return any outputs? If yes, proceed with deleting unwanted 'rtl8192cu' entries in /etc/modprobe.d/blacklist.conf and /etc/modules file -

```
sudo sed -i '/rtl8192cu/ d' /etc/modules
sudo sed -i '/^blacklist rtl8192cu/ d' /etc/modprobe.d/blacklist.conf
```

Reboot and check -
```
lsmod | grep **8192cu**
```
..does it show up in the outptut?

---

### Post by belarrius on 2014-09-16
Ok, now :

```
belarrius@belarrius-computer:~$ lsmod | grep 8192cu
8192cu                628527  0 


```

i retry your script

---

### Post by belarrius on 2014-09-16
```

    ======== Wireless-Info START ========

System-Info ~~~~~~~~~~~~~~~~~~~~~~~~

belarrius-computer 3.17.0-031700rc4-generic x86_64,  Ubuntu 14.04.1 LTS, trusty

CPU    : AMD FX(tm)-8320 Eight-Core Processor
Memory : 7900 MB
Uptime : 13:06:15 up 44 min,  2 users,  load average: 0,10, 0,10, 0,08


lspci ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 09)
    Subsystem: ASUSTeK Computer Inc. P8H77-I Motherboard [1043:8505]
    Kernel driver in use: r8169


lsusb ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 011 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 010 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 005: ID 2357:0100  
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 009 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 046d:0805 Logitech, Inc. Webcam C300
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 008 Device 005: ID 046d:c222 Logitech, Inc. G15 Keyboard / LCD
Bus 008 Device 004: ID 046d:c221 Logitech, Inc. G11/G15 Keyboard / Keyboard
Bus 008 Device 003: ID 046d:c223 Logitech, Inc. G11/G15 Keyboard / USB Hub
Bus 008 Device 002: ID e0ff:0002  
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 006 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 002: ID 04e8:61b6 Samsung Electronics Co., Ltd 
Bus 005 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 004 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


PCMCIA Card Info ~~~~~~~~~~~~~~~~~~~



iwconfig ~~~~~~~~~~~~~~~~~~~~~~~~~~~

wlan0     unassociated  Nickname:"<WIFI@REALTEK>"
          Mode:Managed  Frequency=2.412 GHz  Access Point: Not-Associated   
          Sensitivity:0/0  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0



rfkill ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~




lsmod ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

eeepc_wmi              13151  0 
asus_wmi               24697  1 eeepc_wmi
sparse_keymap          13890  1 asus_wmi
mxm_wmi                13021  0 
video                  20569  1 asus_wmi
wmi                    19379  2 mxm_wmi,asus_wmi
8192cu                628527  0 


module parameters ~~~~~~~~~~~~~~~~~~

8192cu       (37): if2name=wlan0 | ifname=wlan0 | rtw_80211d=0 | rtw_ampdu_amsdu=0 | rtw_ampdu_enable=1 | rtw_antdiv_cfg=2 | rtw_busy_thresh=40 | rtw_cbw40_enable=3 | rtw_channel=1 | rtw_channel_plan=65 | rtw_chip_version=0 | rtw_enusbss=0 | rtw_force_iol=N | rtw_ht_enable=1 | rtw_hwpdn_mode=2 | rtw_hwpwrp_detect=0 | rtw_hw_wps_pbc=1 | rtw_initmac=(null) | rtw_ips_mode=1 | rtw_lbkmode=0 | rtw_low_power=0 | rtw_lowrate_two_xmit=1 | rtw_mac_phy_mode=0 | rtw_max_roaming_times=2 | rtw_mc2u_disable=0 | rtw_mp_mode=0 | rtw_network_mode=0 | rtw_notch_filter=0 | rtw_power_mgnt=1 | rtw_rf_config=5 | rtw_rfintfs=2 | rtw_rx_stbc=1 | rtw_special_rf_path=0 | rtw_vcs_type=1 | rtw_vrtl_carrier_sense=2 | rtw_wifi_spec=0 | rtw_wmm_enable=1
eeepc_wmi     (1): hotplug_wireless=N
video         (3): allow_duplicates=N | brightness_switch_enabled=Y | use_native_backlight=-1
wmi           (2): debug_dump_wdg=N | debug_event=N


nm-tool ~~~~~~~~~~~~~~~~~~~~~~~~~~~~

State: disconnected
================o=============o===========o=======  =======o=========o===========o==============o=====  ======
 Interface & ID | Type        | Driver    | State        | Default | Speed     | Support      | HW Addr   
================o=============o===========o=======  =======o=========o===========o==============o=====  ======
 wlan0          | 802.11 WiFi | rtl8192cu | disconnected | no      |           | WEP/WPA/WPA2 | <MAC wlan0>

    FreeWifi_secure: Infra, <MAC C-01 FreeWifi_secure>, Freq 2462 MHz, Rate 16 Mb/s, Strength 63 WPA2 Enterprise
    FREEBOX_NATALIA_XH: Infra, <MAC C-02 FREEBOX_NATALIA_XH>, Freq 2462 MHz, Rate 16 Mb/s, Strength 63 WPA
    freebox_KIXOQC:  Infra, <MAC C-08 freebox_KIXOQC>, Freq 2462 MHz, Rate 16 Mb/s, Strength 56 WPA
    Freebox-9FD668:  Infra, <MAC C-06 Freebox-9FD668>, Freq 2457 MHz, Rate 16 Mb/s, Strength 56 WPA2
    FreeWifi_secure: Infra, <MAC C-05 FreeWifi_secure>, Freq 2462 MHz, Rate 16 Mb/s, Strength 56 WPA2 Enterprise
    FreeWifi_secure: Infra, <MAC C-09 FreeWifi_secure>, Freq 2457 MHz, Rate 16 Mb/s, Strength 47 WPA2 Enterprise
    FreeWifi:        Infra, <MAC C-03 FreeWifi>, Freq 2462 MHz, Rate 16 Mb/s, Strength 62
    FreeWifi:        Infra, <MAC C-07 FreeWifi>, Freq 2462 MHz, Rate 16 Mb/s, Strength 57
    FreeWifi:        Infra, <MAC C-10 FreeWifi>, Freq 2457 MHz, Rate 16 Mb/s, Strength 56
    Livebox-E3EC:    Infra, <MAC C-04 Livebox-E3EC>, Freq 2412 MHz, Rate 16 Mb/s, Strength 62 WPA WPA2
    Livebox-b014:    Infra, <MAC C-NA Livebox-b014 1>, Freq 2457 MHz, Rate 54 Mb/s, Strength 47 WPA
    Livebox-f513:    Infra, <MAC C-NA Livebox-f513 1>, Freq 2437 MHz, Rate 2 Mb/s, Strength 47 WPA WPA2
----------------+-------------+-----------+--------------+---------+-----------+--------------+-----------
 eth0           | Wired       | r8169     | unavailable  | no      | 100 Mb/s  |              | <MAC eth0>
----------------+-------------+-----------+--------------+---------+-----------+--------------+-----------


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

no-auto-default=<MAC eth0>,

[ifupdown]
managed=false


NM WiFi Profiles ~~~~~~~~~~~~~~~~~~~

Belarrius Wi-Fi      : ssid=Belarrius Wi-Fi | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 


interfaces ~~~~~~~~~~~~~~~~~~~~~~~~~

# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback

resolv.conf ~~~~~~~~~~~~~~~~~~~~~~~~



Routes & Ping ~~~~~~~~~~~~~~~~~~~~~~

Table de routage IP du noyau
Destination     Passerelle      Genmask         Indic Metric Ref    Use Iface


iw reg get ~~~~~~~~~~~~~~~~~~~~~~~~~

(Region : "fr_FR.UTF-8")
country 00:
    (2402 - 2472 @ 40), (3, 20)
    (2457 - 2482 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (2474 - 2494 @ 20), (3, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
    (5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS


iwlist chan ~~~~~~~~~~~~~~~~~~~~~~~~

wlan0     13 channels in total; available frequencies :
          Channel 01 (2.412 GHz) - 13 (2.472 GHz)

          Current Frequency:2.412 GHz (Channel 1)


iwlist scan ~~~~~~~~~~~~~~~~~~~~~~~~

wlan0     Scan completed :
          Cell 01 - Address: <MAC C-01 FreeWifi_secure>
                    ESSID:"FreeWifi_secure"
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Encryption key:on
                    Bit Rates:144 Mb/s
                    Extra:rsn_ie=30180100000fac020200000fac04000fac020  100000fac010c00
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : 802.1x
                    Quality=58/100  Signal level=66/100  
          Cell 02 - Address: <MAC C-02 FREEBOX_NATALIA_XH>
                    ESSID:"FREEBOX_NATALIA_XH"
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Encryption key:on
                    Bit Rates:144 Mb/s
                    Extra:wpa_ie=dd1a0050f20101000050f20202000050f2040  050f20201000050f202
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    Quality=58/100  Signal level=66/100  
          Cell 03 - Address: <MAC C-03 FreeWifi>
                    ESSID:"FreeWifi"
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Encryption key:off
                    Bit Rates:144 Mb/s
                    Quality=53/100  Signal level=66/100  
          Cell 04 - Address: <MAC C-04 Livebox-E3EC>
                    ESSID:"Livebox-E3EC"
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Encryption key:on
                    Bit Rates:144 Mb/s
                    Extra:wpa_ie=dd1a0050f20101000050f20202000050f2040  050f20201000050f202
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    Extra:rsn_ie=30180100000fac020200000fac04000fac020  100000fac020c00
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    Quality=0/100  Signal level=62/100  
          Cell 05 - Address: <MAC C-05 FreeWifi_secure>
                    ESSID:"FreeWifi_secure"
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Encryption key:on
                    Bit Rates:144 Mb/s
                    Extra:rsn_ie=30180100000fac020200000fac04000fac020  100000fac010c00
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : 802.1x
                    Quality=16/100  Signal level=54/100  
          Cell 06 - Address: <MAC C-06 Freebox-9FD668>
                    ESSID:"Freebox-9FD668"
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.457 GHz (Channel 10)
                    Encryption key:on
                    Bit Rates:144 Mb/s
                    Extra:rsn_ie=30140100000fac040100000fac040100000fa  c020c00
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    Quality=80/100  Signal level=54/100  
          Cell 07 - Address: <MAC C-07 FreeWifi>
                    ESSID:"FreeWifi"
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Encryption key:off
                    Bit Rates:144 Mb/s
                    Quality=32/100  Signal level=56/100  
          Cell 08 - Address: <MAC C-08 freebox_KIXOQC>
                    ESSID:"freebox_KIXOQC"
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Encryption key:on
                    Bit Rates:144 Mb/s
                    Extra:wpa_ie=dd1a0050f20101000050f20202000050f2040  050f20201000050f202
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    Quality=47/100  Signal level=56/100  
          Cell 09 - Address: <MAC C-09 FreeWifi_secure>
                    ESSID:"FreeWifi_secure"
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.457 GHz (Channel 10)
                    Encryption key:on
                    Bit Rates:144 Mb/s
                    Extra:rsn_ie=30180100000fac020200000fac04000fac020  100000fac010c00
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : 802.1x
                    Quality=65/100  Signal level=48/100  
          Cell 10 - Address: <MAC C-10 FreeWifi>
                    ESSID:"FreeWifi"
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.457 GHz (Channel 10)
                    Encryption key:off
                    Bit Rates:144 Mb/s
                    Quality=36/100  Signal level=48/100  


blacklist ~~~~~~~~~~~~~~~~~~~~~~~~~~

[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci

[/etc/modprobe.d/blacklist-native-rtl8192.conf]
blacklist rtl8192cu
blacklist rtl8192c_common
blacklist rtlwifi


modinfo ~~~~~~~~~~~~~~~~~~~~~~~~~~~~

[eeepc_wmi]
filename:       /lib/modules/3.17.0-031700rc4-generic/kernel/drivers/platform/x86/eeepc-wmi.ko
srcversion:     063DC0AB014AC1813C17B93
depends:        asus-wmi
parm:           hotplug_wireless:Enable hotplug for wireless device. If your laptop needs that, please report to acpi4asus-user@lists.sourceforge.net. (bool)

[asus_wmi]
filename:       /lib/modules/3.17.0-031700rc4-generic/kernel/drivers/platform/x86/asus-wmi.ko
srcversion:     CC6EE6D8DF9D9328BC6DBBD
depends:        sparse-keymap,wmi,video

[mxm_wmi]
filename:       /lib/modules/3.17.0-031700rc4-generic/kernel/drivers/platform/x86/mxm-wmi.ko
srcversion:     D566C16ECB7E11FB9DF5C84
depends:        wmi

[video]
filename:       /lib/modules/3.17.0-031700rc4-generic/kernel/drivers/acpi/video.ko
srcversion:     E5235B51CFF85D5358B8FB6
depends:        
parm:           brightness_switch_enabled:bool
parm:           allow_duplicates:bool
parm:           use_native_backlight:int

[wmi]
filename:       /lib/modules/3.17.0-031700rc4-generic/kernel/drivers/platform/x86/wmi.ko
srcversion:     2E987FE96F7EBB6BFC7E2B2
depends:        
parm:           debug_event:Log WMI Events [0/1] (bool)
parm:           debug_dump_wdg:Dump available WMI interfaces [0/1] (bool)

[8192cu]
filename:       /lib/modules/3.17.0-031700rc4-generic/updates/dkms/8192cu.ko
version:        v4.0.2_9000.20130911
srcversion:     98913FB8609F2F16E0996C2
depends:        
parm:           rtw_ips_mode:The default IPS mode (int)
parm:           ifname:The default name to allocate for first interface (charp)
parm:           if2name:The default name to allocate for second interface (charp)
parm:           rtw_initmac:charp
parm:           rtw_channel_plan:int
parm:           rtw_chip_version:int
parm:           rtw_rfintfs:int
parm:           rtw_lbkmode:int
parm:           rtw_network_mode:int
parm:           rtw_channel:int
parm:           rtw_mp_mode:int
parm:           rtw_wmm_enable:int
parm:           rtw_vrtl_carrier_sense:int
parm:           rtw_vcs_type:int
parm:           rtw_busy_thresh:int
parm:           rtw_ht_enable:int
parm:           rtw_cbw40_enable:int
parm:           rtw_ampdu_enable:int
parm:           rtw_rx_stbc:int
parm:           rtw_ampdu_amsdu:int
parm:           rtw_lowrate_two_xmit:int
parm:           rtw_rf_config:int
parm:           rtw_power_mgnt:int
parm:           rtw_low_power:int
parm:           rtw_wifi_spec:int
parm:           rtw_special_rf_path:int
parm:           rtw_antdiv_cfg:int
parm:           rtw_enusbss:int
parm:           rtw_hwpdn_mode:int
parm:           rtw_hwpwrp_detect:int
parm:           rtw_hw_wps_pbc:int
parm:           rtw_max_roaming_times:The max roaming times to try (uint)
parm:           rtw_force_iol:Force to enable IOL (bool)
parm:           rtw_mc2u_disable:int
parm:           rtw_mac_phy_mode:int
parm:           rtw_80211d:int
parm:           rtw_notch_filter:0:Disable, 1:Enable, 2:Enable only for P2P (uint)


udev rules ~~~~~~~~~~~~~~~~~~~~~~~~~

# PCI device 0x10ec:0x8168 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC eth0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

# USB device 0x:0x (rtl8192cu)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC wlan0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

# USB device 0x:0x (rt2800usb)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC wlan1>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan1"


Custom files/entries ~~~~~~~~~~~~~~~

/etc/modules        : Not Default
/etc/rc.local       : Not Default
/etc/modprobe.d     : Not Default
/etc/pm/(cnf|pw|sl) : Default

[/etc/modules]
8192cu

[/etc/rc.local]
echo "2001 330D" | tee /sys/bus/usb/drivers/rtl8192cu/new_id
exit 0

[/etc/modprobe.d]
iwlwifi.conf      : remove iwlwifi \
                    (/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
                    && /sbin/modprobe -r mac80211
mlx4.conf         : softdep mlx4_core post: mlx4_en


Kernel boot line ~~~~~~~~~~~~~~~~~~~

BOOT_IMAGE=/boot/vmlinuz-3.17.0-031700rc4-generic root=UUID=4928974c-0607-4865-91b4-ccedc391c8e8 ro quiet splash


dmesg ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

[    1.395847] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[    1.396368] audit: initializing netlink subsys (disabled)
[    1.682339] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[   10.958013] 8192cu: module verification failed: signature and/or  required key missing - tainting kernel
[   10.958906] rtl8192cu driver version=v4.0.2_9000.20130911
[   11.096523] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   11.174001] wmi: Mapper loaded
[   11.393665] asus_wmi: ASUS WMI generic driver loaded
[   11.401041] asus_wmi: Initialization: 0x0
[   11.401075] asus_wmi: BIOS WMI version: 0.9
[   11.401164] asus_wmi: SFUN value: 0x0
[   11.401686] input: Eee PC WMI hotkeys as /devices/platform/eeepc-wmi/input/input7
[   11.403122] asus_wmi: Disabling ACPI video driver
[  404.326800] register rtw_netdev_ops to netdev_ops
[  404.461562] _rtw_drv_register_netdev, MAC Address (if1) = <MAC wlan0>
[  405.117950] rtl8192cu_hal_init in 564ms
[  405.131688] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  405.139123] rtl8192c_set_FwJoinBssReport_cmd mstatus(0)
[  405.140521] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  409.184075] ==> rtl8192cu_hal_deinit 
[  417.720260] ===> ips_netdrv_open.........
[  418.281526] rtl8192cu_hal_init in 564ms
[  420.116324] issue_deauth_ex(wlan0) to <MAC ID removed>, ch:3, 5/5 in 496 ms
[  421.668187] rtl8192c_set_FwJoinBssReport_cmd mstatus(0)
[  423.587288] issue_deauth_ex(wlan0) to <MAC ID removed>, ch:3, 5/5 in 496 ms
[  425.111217] rtl8192c_set_FwJoinBssReport_cmd mstatus(0)
[  427.030339] issue_deauth_ex(wlan0) to <MAC ID removed>, ch:3, 5/5 in 496 ms
[  428.558263] rtl8192c_set_FwJoinBssReport_cmd mstatus(0)
[  430.477396] issue_deauth_ex(wlan0) to <MAC ID removed>, ch:3, 5/5 in 496 ms
[  432.001329] rtl8192c_set_FwJoinBssReport_cmd mstatus(0)
[  436.523497] ==> rtl8192cu_hal_deinit 
[  438.421357] ===> ips_netdrv_open.........
[  438.983774] rtl8192cu_hal_init in 564ms
[  441.031504] ==> rtl8192cu_hal_deinit 
[  453.156785] ===> ips_netdrv_open.........
[  453.720819] rtl8192cu_hal_init in 564ms
[  455.555615] issue_deauth_ex(wlan0) to <MAC ID removed>, ch:3, 5/5 in 496 ms
[  457.107502] rtl8192c_set_FwJoinBssReport_cmd mstatus(0)
[  461.785818] ==> rtl8192cu_hal_deinit 
[  463.525285] ===> ips_netdrv_open.........
[  464.090027] rtl8192cu_hal_init in 564ms
[  466.131984] ==> rtl8192cu_hal_deinit 
[  470.427504] ===> ips_netdrv_open.........
[  470.988147] rtl8192cu_hal_init in 560ms
[  472.822820] issue_deauth_ex(wlan0) to <MAC ID removed>, ch:3, 5/5 in 496 ms
[  474.330729] rtl8192c_set_FwJoinBssReport_cmd mstatus(0)
[  479.050270] ==> rtl8192cu_hal_deinit 
[  491.757745] ===> ips_netdrv_open.........
[  492.318931] rtl8192cu_hal_init in 564ms
[  494.153728] issue_deauth_ex(wlan0) to <MAC ID removed>, ch:3, 5/5 in 496 ms
[  495.693605] rtl8192c_set_FwJoinBssReport_cmd mstatus(0)
[  500.383930] ==> rtl8192cu_hal_deinit 
[  502.115423] ===> ips_netdrv_open.........
[  502.676126] rtl8192cu_hal_init in 560ms
[  504.718081] ==> rtl8192cu_hal_deinit 
[  509.009446] ===> ips_netdrv_open.........
[  509.570240] rtl8192cu_hal_init in 560ms
[  511.404913] issue_deauth_ex(wlan0) to <MAC ID removed>, ch:3, 5/5 in 496 ms
[  512.920837] rtl8192c_set_FwJoinBssReport_cmd mstatus(0)
[  517.635237] ==> rtl8192cu_hal_deinit 
[  518.352424] ===> ips_netdrv_open.........
[  518.914543] rtl8192cu_hal_init in 564ms
[  520.962138] ==> rtl8192cu_hal_deinit 
[  521.851353] ===> ips_netdrv_open.........
[  522.413541] rtl8192cu_hal_init in 564ms
[  524.248336] issue_deauth_ex(wlan0) to <MAC ID removed>, ch:3, 5/5 in 496 ms
[  525.660148] rtw_sta_flush(wlan0)
[  525.660273] =====> rtl8192c_free_hal_data =====
[  525.660274] <===== rtl8192c_free_hal_data =====
[  525.660281] -r871xu_dev_remove, done
[  528.985001] register rtw_netdev_ops to netdev_ops
[  529.119893] _rtw_drv_register_netdev, MAC Address (if1) = <MAC wlan0>
[  529.772139] rtl8192cu_hal_init in 560ms
[  529.785894] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  529.793306] rtl8192c_set_FwJoinBssReport_cmd mstatus(0)
[  529.794451] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  533.838263] ==> rtl8192cu_hal_deinit 
[  534.600946] ===> ips_netdrv_open.........
[  535.160872] rtl8192cu_hal_init in 560ms
[  535.682403] issue_deauth_ex(wlan0) to <MAC ID removed>, ch:3, 5/5 in 496 ms
[  537.234334] rtl8192c_set_FwJoinBssReport_cmd mstatus(0)
[  539.157495] issue_deauth_ex(wlan0) to <MAC ID removed>, ch:3, 5/5 in 500 ms
[  540.681380] rtl8192c_set_FwJoinBssReport_cmd mstatus(0)
[  542.600548] issue_deauth_ex(wlan0) to <MAC ID removed>, ch:3, 5/5 in 496 ms
[  544.128430] rtl8192c_set_FwJoinBssReport_cmd mstatus(0)
[  546.047605] issue_deauth_ex(wlan0) to <MAC ID removed>, ch:3, 5/5 in 496 ms
[  547.571478] rtl8192c_set_FwJoinBssReport_cmd mstatus(0)
[  551.248896] ==> rtl8192cu_hal_deinit 
[  553.989529] ===> ips_netdrv_open.........
[  554.549976] rtl8192cu_hal_init in 560ms
[  556.591936] ==> rtl8192cu_hal_deinit 
[  679.997323] ===> ips_netdrv_open.........
[  680.557438] rtl8192cu_hal_init in 560ms
[  682.605041] ==> rtl8192cu_hal_deinit 
[  682.992664] ===> ips_netdrv_open.........
[  683.552056] rtl8192cu_hal_init in 560ms
[  685.599658] ==> rtl8192cu_hal_deinit 
[  706.014541] ===> ips_netdrv_open.........
[  706.576326] rtl8192cu_hal_init in 564ms
[  708.624054] ==> rtl8192cu_hal_deinit 
[  739.046296] ===> ips_netdrv_open.........
[  739.605598] rtl8192cu_hal_init in 560ms
[  741.653202] ==> rtl8192cu_hal_deinit 
[  782.085253] ===> ips_netdrv_open.........
[  782.647629] rtl8192cu_hal_init in 564ms
[  784.689582] ==> rtl8192cu_hal_deinit 
[  835.131861] ===> ips_netdrv_open.........
[  835.694539] rtl8192cu_hal_init in 564ms
[  837.742142] ==> rtl8192cu_hal_deinit 
[  898.184486] ===> ips_netdrv_open.........
[  898.746198] rtl8192cu_hal_init in 564ms
[  900.788278] ==> rtl8192cu_hal_deinit 
[  961.237862] ===> ips_netdrv_open.........
[  961.797979] rtl8192cu_hal_init in 560ms
[  963.842842] ==> rtl8192cu_hal_deinit 
[ 1024.313442] ===> ips_netdrv_open.........
[ 1024.875417] rtl8192cu_hal_init in 564ms
[ 1026.918374] ==> rtl8192cu_hal_deinit 
[ 1087.403200] ===> ips_netdrv_open.........
[ 1087.962617] rtl8192cu_hal_init in 560ms
[ 1090.011222] ==> rtl8192cu_hal_deinit 
[ 1150.487500] ===> ips_netdrv_open.........
[ 1151.049941] rtl8192cu_hal_init in 564ms
[ 1153.092893] ==> rtl8192cu_hal_deinit 
[ 1213.577720] ===> ips_netdrv_open.........
[ 1214.137138] rtl8192cu_hal_init in 560ms
[ 1216.185869] ==> rtl8192cu_hal_deinit 
[ 1276.659858] ===> ips_netdrv_open.........
[ 1277.220454] rtl8192cu_hal_init in 560ms
[ 1279.269061] ==> rtl8192cu_hal_deinit 
[ 1339.752289] ===> ips_netdrv_open.........
[ 1340.311655] rtl8192cu_hal_init in 560ms
[ 1342.354738] ==> rtl8192cu_hal_deinit 
[ 1402.835123] ===> ips_netdrv_open.........
[ 1403.394971] rtl8192cu_hal_init in 560ms
[ 1405.440823] ==> rtl8192cu_hal_deinit 
[ 1465.927009] ===> ips_netdrv_open.........
[ 1466.486298] rtl8192cu_hal_init in 560ms
[ 1468.534894] ==> rtl8192cu_hal_deinit 
[ 1529.011659] ===> ips_netdrv_open.........
[ 1529.573491] rtl8192cu_hal_init in 564ms
[ 1531.622220] ==> rtl8192cu_hal_deinit 
[ 1592.097382] ===> ips_netdrv_open.........
[ 1592.656803] rtl8192cu_hal_init in 560ms
[ 1594.702655] ==> rtl8192cu_hal_deinit 
[ 1655.198953] ===> ips_netdrv_open.........
[ 1655.761519] rtl8192cu_hal_init in 564ms
[ 1657.805476] ==> rtl8192cu_hal_deinit 
[ 1718.320641] ===> ips_netdrv_open.........
[ 1718.880272] rtl8192cu_hal_init in 560ms
[ 1720.924338] ==> rtl8192cu_hal_deinit 
[ 1781.436901] ===> ips_netdrv_open.........
[ 1781.999106] rtl8192cu_hal_init in 564ms
[ 1784.043187] ==> rtl8192cu_hal_deinit 
[ 1844.539344] ===> ips_netdrv_open.........
[ 1845.098688] rtl8192cu_hal_init in 560ms
[ 1847.147418] ==> rtl8192cu_hal_deinit 
[ 1907.627577] ===> ips_netdrv_open.........
[ 1908.190009] rtl8192cu_hal_init in 564ms
[ 1910.238614] ==> rtl8192cu_hal_deinit 
[ 1970.717855] ===> ips_netdrv_open.........
[ 1971.277200] rtl8192cu_hal_init in 560ms
[ 1973.325930] ==> rtl8192cu_hal_deinit 
[ 2033.802415] ===> ips_netdrv_open.........
[ 2034.364516] rtl8192cu_hal_init in 564ms
[ 2036.413119] ==> rtl8192cu_hal_deinit 
[ 2096.892446] ===> ips_netdrv_open.........
[ 2097.451831] rtl8192cu_hal_init in 560ms
[ 2099.494787] ==> rtl8192cu_hal_deinit 
[ 2159.976700] ===> ips_netdrv_open.........
[ 2160.539022] rtl8192cu_hal_init in 564ms
[ 2162.587749] ==> rtl8192cu_hal_deinit 
[ 2223.067295] ===> ips_netdrv_open.........
[ 2223.626334] rtl8192cu_hal_init in 560ms
[ 2225.674939] ==> rtl8192cu_hal_deinit 
[ 2286.150632] ===> ips_netdrv_open.........
[ 2286.709644] rtl8192cu_hal_init in 560ms
[ 2288.752470] ==> rtl8192cu_hal_deinit 
[ 2349.241413] ===> ips_netdrv_open.........
[ 2349.800839] rtl8192cu_hal_init in 560ms
[ 2351.849569] ==> rtl8192cu_hal_deinit 
[ 2412.325400] ===> ips_netdrv_open.........
[ 2412.908181] rtl8192cu_hal_init in 584ms
[ 2414.956782] ==> rtl8192cu_hal_deinit 
[ 2475.415721] ===> ips_netdrv_open.........
[ 2475.975469] rtl8192cu_hal_init in 560ms
[ 2478.018427] ==> rtl8192cu_hal_deinit 
[ 2538.500005] ===> ips_netdrv_open.........
[ 2539.062658] rtl8192cu_hal_init in 564ms
[ 2541.105739] ==> rtl8192cu_hal_deinit 
[ 2601.588465] ===> ips_netdrv_open.........
[ 2602.149972] rtl8192cu_hal_init in 564ms
[ 2604.198574] ==> rtl8192cu_hal_deinit 
[ 2622.160586] ===> ips_netdrv_open.........
[ 2622.722424] rtl8192cu_hal_init in 564ms
[ 2624.768269] ==> rtl8192cu_hal_deinit 
[ 2629.062173] ===> ips_netdrv_open.........
[ 2629.623920] rtl8192cu_hal_init in 564ms
[ 2631.667002] ==> rtl8192cu_hal_deinit 
[ 2635.091193] ===> ips_netdrv_open.........
[ 2635.091234] rtl8192cu_hal_init in 0ms
[ 2635.091236] -ips_netdrv_open - drv_open failure, bup=1
[ 2635.123307] rtw_sta_flush(wlan0)
[ 2635.123342] rtw_cmd_thread(wlan0) stop_req:1, break
[ 2635.123431] =====> rtl8192c_free_hal_data =====
[ 2635.123432] <===== rtl8192c_free_hal_data =====
[ 2635.123438] -r871xu_dev_remove, done
[ 2640.372662] register rtw_netdev_ops to netdev_ops
[ 2640.507432] _rtw_drv_register_netdev, MAC Address (if1) = <MAC wlan0>
[ 2641.119837] rtl8192cu_hal_init in 560ms
[ 2641.133577] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 2641.141017] rtl8192c_set_FwJoinBssReport_cmd mstatus(0)
[ 2641.142384] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 2645.186837] ==> rtl8192cu_hal_deinit 
[ 2661.809309] ===> ips_netdrv_open.........
[ 2662.369257] rtl8192cu_hal_init in 560ms
[ 2664.415104] ==> rtl8192cu_hal_deinit 
[ 2664.673622] ===> ips_netdrv_open.........
[ 2665.233211] rtl8192cu_hal_init in 560ms
[ 2667.276293] ==> rtl8192cu_hal_deinit 
[ 2683.971915] ===> ips_netdrv_open.........
[ 2684.531945] rtl8192cu_hal_init in 560ms

    ======== Done ========


```

---

### Post by belarrius on 2014-09-16
The LED of wifi works, but i can't connect. Similar to old

---

### Post by belarrius on 2014-09-17
Any news?

---

### Post by varunendra on 2014-09-17
> **belarrius said:**
> Any news?
Got one, almost 24 hrs. ago, wasn't a good one so tried to think of alternative, but am lacking both time and energy at the moment..

Looks like we have hit a deadlock, at least for now. Those who are involved in the driver's development think some of the newer cards, including this one, can't work with current versions of either the native or the proprietary drivers : [http://www.spinics.net/lists/linux-wireless/msg111656.html](http://www.spinics.net/lists/linux-wireless/msg111656.html)

Although that message is dated 27/08/13, I couldn't find any updates regarding it.

There are plenty of driver parameters available with this particular driver, but their description in the source '.c' file is not very clear (actually looks inconsistent and misleading to me), and I'm sure the developers must have tried the reasonable ones already before posting the above conclusion. So guessing and trying them may prove to be a wild-goose chase.

If you wish to try them anyway, or try possible alternatives, I may find some time tomorrow to post an entire list of what parameters and alternatives could be tried. But frankly, I'm not very hopeful with whatever little info I could find about your card on the net.

Unless there are updates that I might have missed, I think a good alternative for now is to get a different, well supported card/usb-adapter for now.

I'll ask for help to see if others know any better about it.

---

### Post by praseodym on 2014-09-18
Please show:

```
modprobe -c | grep -i "2357.*0100"
dmesg | grep 8192
```

---

### Post by belarrius on 2014-09-18
> **varunendra said:**
> Got one, almost 24 hrs. ago, wasn't a good one so tried to think of alternative, but am lacking both time and energy at the moment..

Looks like we have hit a deadlock, at least for now. Those who are involved in the driver's development think some of the newer cards, including this one, can't work with current versions of either the native or the proprietary drivers : [http://www.spinics.net/lists/linux-wireless/msg111656.html](http://www.spinics.net/lists/linux-wireless/msg111656.html)

Although that message is dated 27/08/13, I couldn't find any updates regarding it.

There are plenty of driver parameters available with this particular driver, but their description in the source '.c' file is not very clear (actually looks inconsistent and misleading to me), and I'm sure the developers must have tried the reasonable ones already before posting the above conclusion. So guessing and trying them may prove to be a wild-goose chase.

If you wish to try them anyway, or try possible alternatives, I may find some time tomorrow to post an entire list of what parameters and alternatives could be tried. But frankly, I'm not very hopeful with whatever little info I could find about your card on the net.

Unless there are updates that I might have missed, I think a good alternative for now is to get a different, well supported card/usb-adapter for now.

I'll ask for help to see if others know any better about it.

Ow, I'm sorry :/ I do not want to waste your time

---

### Post by belarrius on 2014-09-18
> **praseodym said:**
> Please show:

```
modprobe -c | grep -i "2357.*0100"
dmesg | grep 8192
```




```

belarrius@belarrius-computer:~$ modprobe -c | grep -i "2357.*0100"
alias usb:v2357p0100d*dc*dsc*dp*ic*isc*ip* ndiswrapper
alias usb:v2357p0100d*dc*dsc*dp*ic*isc*ip*in* rtl8192cu
alias usb:v2357p0100d*dc*dsc*dp*ic*isc*ip*in* 8192cu
belarrius@belarrius-computer:~$ dmesg | grep 8192
[    0.000000] PERCPU: Embedded 29 pages/cpu @ffff88022fc00000 s86784 r8192 d23808 u262144
[    0.000000] pcpu-alloc: s86784 r8192 d23808 u262144 alloc=1*2097152
[    2.781927] sd 5:0:0:0: Attached scsi generic sg3 type 0
[    9.416291] 8192cu: module verification failed: signature and/or  required key missing - tainting kernel
[    9.418612] rtl8192cu driver version=v4.0.2_9000.20130911
[    9.418673] usbcore: registered new interface driver rtl8192cu
[   38.595678] ata6.00: cmd 61/10:a0:e0:f9:8f/00:00:0a:00:00/40 tag 20 ncq 8192 out
[   39.112385] ata6.00: cmd 61/10:b8:e0:f9:8f/00:00:0a:00:00/40 tag 23 ncq 8192 out
[   39.112412] ata6.00: cmd 60/10:d0:30:af:44/00:00:06:00:00/40 tag 26 ncq 8192 in
[  373.290027] ata6.00: cmd 61/10:08:00:f9:8f/00:00:0a:00:00/40 tag 1 ncq 8192 out
[ 3829.817239] CHIP TYPE: RTL8188C_8192C
[ 3829.817859] ====> ReadAdapterInfo8192C
[ 3829.951544] readAdapterInfo_8192CU(): REPLACEMENT = 1
[ 3829.951546] <==== ReadAdapterInfo8192C in 136 ms
[ 3830.600713] rtl8192cu_hal_init in 560ms
[ 3830.621884] rtl8192c_set_FwJoinBssReport_cmd mstatus(0)
[ 3834.663449] ==> rtl8192cu_hal_deinit 



```

---

### Post by praseodym on 2014-09-18
So, ndiswrapper is (still) installed?
```

sudo modprobe -rfv ndiswrapper
sudo apt-get remove --purge ndisgtk ndiswrapper*
```
Reboot.

---

### Post by belarrius on 2014-09-18
> **praseodym said:**
> So, ndiswrapper is (still) installed?
```

sudo modprobe -rfv ndiswrapper
sudo apt-get remove --purge ndisgtk ndiswrapper*
```
Reboot.

No changements :(

The wifi requir password, done, try to connect and password, try, password etc.... Don't connect successfull :/

---

### Post by belarrius on 2014-09-20
I abandone.

---

### Post by Mehmet_Yelken on 2015-01-24
> **belarrius said:**
> I abandone.
Hi.
I have same device.
I had same prbolem.
I tried every possible solutions that I can find.
I'm losing my will too..

---

### Post by belarrius on 2015-04-29
Ubuntu 15.04 with kernel 3.19... The problem is always here.

Now, i search a new Wi-fi with 7-9dBi for a good connection, i don't really find [http://ubuntuforums.org/showthread.php?t=2275810](http://ubuntuforums.org/showthread.php?t=2275810)

---

