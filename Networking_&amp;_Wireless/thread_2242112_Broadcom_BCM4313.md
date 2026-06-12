---
title: "Broadcom BCM4313"
date: 2014-08-30
forum: Networking &amp; Wireless
---

### Post by wn1ytw on 2014-08-30
```
======== Wireless-Info START ========

System-Info ~~~~~~~~~~~~~~~~~~~~~~~~

scott-1015E 3.13.0-34-generic x86_64,  Ubuntu 14.04.1 LTS, trusty

CPU    : Intel(R) Celeron(R) CPU 847 @ 1.10GHz
Memory : 1819 MB
Uptime : 13:25:38 up  2:11,  2 users,  load average: 0.00, 0.03, 0.09


lspci ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

02:00.0 Network controller [0280]: Broadcom Corporation BCM4313 802.11bgn Wireless Network Adapter [14e4:4727] (rev 01)
    Subsystem: AzureWave Device [1a3b:2047]
    Kernel driver in use: wl
03:00.0 Ethernet controller [0200]: Qualcomm Atheros AR8162 Fast Ethernet [1969:1090] (rev 10)
    Subsystem: ASUSTeK Computer Inc. Device [1043:115d]
    Kernel driver in use: alx


lsusb ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 13d3:5188 IMC Networks 
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


PCMCIA Card Info ~~~~~~~~~~~~~~~~~~~



iwconfig ~~~~~~~~~~~~~~~~~~~~~~~~~~~

wlan0     IEEE 802.11abg  ESSID off/any  
          Mode:Managed  Access Point: Not-Associated   
          Retry  long limit:7   RTS thr off   Fragment thr off
          Power Management off
          


rfkill ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

      Interface             Soft blocked  Hard blocked
0: asus-wlan: Wireless LAN      no            no
1: phy0: Wireless LAN           no            no
2: brcmwl-0: Wireless LAN       no            no


lsmod ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

wl                   4207846  0 
lib80211               14381  2 wl,lib80211_crypt_tkip
cfg80211              484040  1 wl
asus_nb_wmi            16990  0 
asus_wmi               24191  1 asus_nb_wmi
sparse_keymap          13948  1 asus_wmi
wmi                    19177  1 asus_wmi
video                  19476  2 i915,asus_wmi


module parameters ~~~~~~~~~~~~~~~~~~

asus_nb_wmi   (1): wapf=4
cfg80211      (2): cfg80211_disable_40mhz_24ghz=N | ieee80211_regdom=00
video         (3): allow_duplicates=N | brightness_switch_enabled=Y | use_native_backlight=-1
wmi           (2): debug_dump_wdg=N | debug_event=N


nm-tool ~~~~~~~~~~~~~~~~~~~~~~~~~~~~

State: disconnected
================o=============o========o==========  ====o=========o===========o==============o========  ===
 Interface & ID | Type        | Driver | State        | Default | Speed     | Support      | HW Addr   
================o=============o========o==========  ====o=========o===========o==============o========  ===
 eth0           | Wired       | alx    | unavailable  | no      |           |              | <MAC eth0>
----------------+-------------+--------+--------------+---------+-----------+--------------+-----------
 wlan0          | 802.11 WiFi | wl     | disconnected | no      |           | WEP/WPA/WPA2 | <MAC wlan0>

    Worcester:       Infra, <MAC C-03 Worcester>, Freq 2462 MHz, Rate 54 Mb/s, Strength 94 WPA WPA2
    Worcester:       Infra, <MAC C-05 Worcester>, Freq 2462 MHz, Rate 54 Mb/s, Strength 84 WPA WPA2
    Worcester:       Infra, <MAC C-10 Worcester>, Freq 2412 MHz, Rate 54 Mb/s, Strength 69 WPA WPA2
    Worcester:       Infra, <MAC C-01 Worcester>, Freq 2437 MHz, Rate 54 Mb/s, Strength 64 WPA WPA2
    Worcester:       Infra, <MAC C-07 Worcester>, Freq 2412 MHz, Rate 54 Mb/s, Strength 62 WPA WPA2
    Worcester:       Infra, <MAC C-11 Worcester>, Freq 2437 MHz, Rate 54 Mb/s, Strength 49 WPA WPA2
    Worcester:       Infra, <MAC C-13 Worcester>, Freq 2462 MHz, Rate 54 Mb/s, Strength 20 WPA WPA2
    Worcester-Guest: Infra, <MAC C-02 Worcester-Guest>, Freq 2462 MHz, Rate 54 Mb/s, Strength 84
    Worcester-Guest: Infra, <MAC C-04 Worcester-Guest>, Freq 2462 MHz, Rate 54 Mb/s, Strength 84
    Worcester-Guest: Infra, <MAC C-08 Worcester-Guest>, Freq 2412 MHz, Rate 54 Mb/s, Strength 70
    Worcester-Guest: Infra, <MAC C-06 Worcester-Guest>, Freq 2437 MHz, Rate 54 Mb/s, Strength 62
    Worcester-Guest: Infra, <MAC C-09 Worcester-Guest>, Freq 2412 MHz, Rate 54 Mb/s, Strength 59
    Worcester-Guest: Infra, <MAC C-12 Worcester-Guest>, Freq 2437 MHz, Rate 54 Mb/s, Strength 50
    Worcester-Guest: Infra, <MAC C-14 Worcester-Guest>, Freq 2462 MHz, Rate 54 Mb/s, Strength 32
    Worcester:       Infra, <MAC C-15 Worcester>, Freq 2462 MHz, Rate 54 Mb/s, Strength 24 WPA WPA2
    Hydro XTRM 9465: Infra, <MAC C-NA Hydro XTRM 9465 1>, Freq 2412 MHz, Rate 54 Mb/s, Strength 37 WPA2
    Worcester-Guest: Infra, <MAC C-NA Worcester-Guest 2>, Freq 2462 MHz, Rate 54 Mb/s, Strength 22
----------------+-------------+--------+--------------+---------+-----------+--------------+-----------


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

Worcester            : ssid=Worcester | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 
Worcester-Guest      : ssid=Worcester-Guest | mac-address=<MAC wlan0> | ipv6=auto | ipv4=auto 


interfaces ~~~~~~~~~~~~~~~~~~~~~~~~~

# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback

resolv.conf ~~~~~~~~~~~~~~~~~~~~~~~~



Routes & Ping ~~~~~~~~~~~~~~~~~~~~~~

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface


iw reg get ~~~~~~~~~~~~~~~~~~~~~~~~~

(Region : "en_US.UTF-8")
country 00:
    (2402 - 2472 @ 40), (3, 20)
    (2457 - 2482 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (2474 - 2494 @ 20), (3, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
    (5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS


iwlist chan ~~~~~~~~~~~~~~~~~~~~~~~~

wlan0     26 channels in total; available frequencies :
          Channel 01 (2.412 GHz) - 14 (2.484 GHz)
          Channel 36 (5.18 GHz)
          Channel 38 (5.19 GHz)
          Channel 40 (5.2 GHz)
          Channel 42 (5.21 GHz)
          Channel 44 (5.22 GHz)
          Channel 46 (5.23 GHz)
          Channel 48 (5.24 GHz)
          Channel 149 (5.745 GHz)
          Channel 153 (5.765 GHz)
          Channel 157 (5.785 GHz)
          Channel 161 (5.805 GHz)
          Channel 165 (5.825 GHz) - 14 (2.484 GHz)


iwlist scan ~~~~~~~~~~~~~~~~~~~~~~~~

wlan0     Scan completed :
          Cell 01 - Address: <MAC C-01 Worcester>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=44/70  Signal level=-66 dBm  
                    Encryption key on
                    ESSID:"Worcester"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 4ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC C-02 Worcester-Guest>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=66/70  Signal level=-44 dBm  
                    Encryption key off
                    ESSID:"Worcester-Guest"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 4ms ago
          Cell 03 - Address: <MAC C-03 Worcester>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=66/70  Signal level=-44 dBm  
                    Encryption key on
                    ESSID:"Worcester"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 4ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 04 - Address: <MAC C-04 Worcester-Guest>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=59/70  Signal level=-51 dBm  
                    Encryption key off
                    ESSID:"Worcester-Guest"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 4ms ago
          Cell 05 - Address: <MAC C-05 Worcester>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=60/70  Signal level=-50 dBm  
                    Encryption key on
                    ESSID:"Worcester"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 4ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 06 - Address: <MAC C-06 Worcester-Guest>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=47/70  Signal level=-63 dBm  
                    Encryption key off
                    ESSID:"Worcester-Guest"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 4ms ago
          Cell 07 - Address: <MAC C-07 Worcester>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=42/70  Signal level=-68 dBm  
                    Encryption key on
                    ESSID:"Worcester"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 4ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 08 - Address: <MAC C-08 Worcester-Guest>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=40/70  Signal level=-70 dBm  
                    Encryption key off
                    ESSID:"Worcester-Guest"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 4ms ago
          Cell 09 - Address: <MAC C-09 Worcester-Guest>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=41/70  Signal level=-69 dBm  
                    Encryption key off
                    ESSID:"Worcester-Guest"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 4ms ago
          Cell 10 - Address: <MAC C-10 Worcester>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=40/70  Signal level=-70 dBm  
                    Encryption key on
                    ESSID:"Worcester"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 4ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 11 - Address: <MAC C-11 Worcester>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=34/70  Signal level=-76 dBm  
                    Encryption key on
                    ESSID:"Worcester"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 5356ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 12 - Address: <MAC C-12 Worcester-Guest>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=36/70  Signal level=-74 dBm  
                    Encryption key off
                    ESSID:"Worcester-Guest"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 4ms ago
          Cell 13 - Address: <MAC C-13 Worcester>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=28/70  Signal level=-82 dBm  
                    Encryption key on
                    ESSID:"Worcester"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 4ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 14 - Address: <MAC C-14 Worcester-Guest>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=30/70  Signal level=-80 dBm  
                    Encryption key off
                    ESSID:"Worcester-Guest"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 4ms ago
          Cell 15 - Address: <MAC C-15 Worcester>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=21/70  Signal level=-89 dBm  
                    Encryption key on
                    ESSID:"Worcester"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 4ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK


blacklist ~~~~~~~~~~~~~~~~~~~~~~~~~~

[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci

[/etc/modprobe.d/blacklist-bcm43.conf]
blacklist b43
blacklist b43legacy
blacklist ssb
blacklist brcm80211
blacklist brcmfmac
blacklist brcmsmac
blacklist bcma


modinfo ~~~~~~~~~~~~~~~~~~~~~~~~~~~~

[wl]
filename:       /lib/modules/3.13.0-34-generic/updates/dkms/wl.ko
srcversion:     FF25FE784DC6BDFF69DAFCB
depends:        cfg80211,lib80211
parm:           wl_txq_thresh:int
parm:           oneonly:int
parm:           piomode:int
parm:           instance_base:int
parm:           nompc:int
parm:           intf_name:string

[lib80211]
filename:       /lib/modules/3.13.0-34-generic/kernel/net/wireless/lib80211.ko
srcversion:     84DEF767F03D28E373F18E5
depends:        

[cfg80211]
filename:       /lib/modules/3.13.0-34-generic/kernel/net/wireless/cfg80211.ko
srcversion:     E786D076B61F97809B04B64
depends:        
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

[asus_nb_wmi]
filename:       /lib/modules/3.13.0-34-generic/kernel/drivers/platform/x86/asus-nb-wmi.ko
srcversion:     67514DF02FC4A206C47D0F5
depends:        asus-wmi
parm:           wapf:WAPF value (uint)

[asus_wmi]
filename:       /lib/modules/3.13.0-34-generic/kernel/drivers/platform/x86/asus-wmi.ko
srcversion:     222BD5E26B3EE82CC433FF2
depends:        sparse-keymap,wmi,video

[wmi]
filename:       /lib/modules/3.13.0-34-generic/kernel/drivers/platform/x86/wmi.ko
srcversion:     CED5410F008DC70DF5F064B
depends:        
parm:           debug_event:Log WMI Events [0/1] (bool)
parm:           debug_dump_wdg  dump available WMI interfaces [0/1] (bool)

[video]
filename:       /lib/modules/3.13.0-34-generic/kernel/drivers/acpi/video.ko
srcversion:     274A2250DEAB415D412A67C
depends:        
parm:           brightness_switch_enabled:bool
parm:           allow_duplicates:bool
parm:           use_native_backlight:int


udev rules ~~~~~~~~~~~~~~~~~~~~~~~~~

# PCI device 0x1969:0x1090 (alx)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC eth0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

# PCI device 0x14e4:0x4727 (brcmsmac)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC wlan0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"


Custom files/entries ~~~~~~~~~~~~~~~

/etc/modules        : Default
/etc/rc.local       : Default
/etc/modprobe.d     : Not Default
/etc/pm/(cnf|pw|sl) : Default

[/etc/modprobe.d]
iwlwifi.conf      : remove iwlwifi \
                    (/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
                    && /sbin/modprobe -r mac80211
mlx4.conf         : softdep mlx4_core post: mlx4_en


Kernel boot line ~~~~~~~~~~~~~~~~~~~

BOOT_IMAGE=/boot/vmlinuz-3.13.0-34-generic.efi.signed root=UUID=7c9fde11-c07e-4151-bdee-03c78293fd1d ro quiet splash vt.handoff=7


dmesg ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

[    1.075653] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[    1.076157] audit: initializing netlink socket (disabled)
[    1.437258] alx 0000:03:00.0 eth0: Qualcomm Atheros AR816x/AR817x Ethernet [<MAC eth0>]
[    2.019679] psmouse serio4: elantech: assuming hardware version 4 (with firmware version 0x361f03)
[   17.485737] wmi: Mapper loaded
[   18.054602] asus_wmi: ASUS WMI generic driver loaded
[   18.066339] asus_wmi: Initialization: 0x1
[   18.066404] asus_wmi: BIOS WMI version: 7.9
[   18.066479] asus_wmi: SFUN value: 0x4a1877
[   18.068348] input: Asus WMI hotkeys as /devices/platform/asus-nb-wmi/input/input12
[   18.129313] asus_wmi: Backlight controlled by ACPI video driver
[   21.066628] wl: module license 'MIXED/Proprietary' taints kernel.
[   21.069539] wl: module verification failed: signature and/or  required key missing - tainting kernel
[   21.114430] INFO @wl_cfg80211_attach : Registered CFG80211 phy
[   21.436784] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   21.741051] wlan0: Broadcom BCM4727 802.11 Hybrid Wireless Controller 6.30.223.141 (r415941)
[  977.218145] alx 0000:03:00.0 eth0: Qualcomm Atheros AR816x/AR817x Ethernet [<MAC eth0>]
[ 1672.089070] alx 0000:03:00.0 eth0: Qualcomm Atheros AR816x/AR817x Ethernet [<MAC eth0>]
[ 1751.730158] ERROR @wl_dev_intvar_get : error (-1)
[ 1751.730169] ERROR @wl_cfg80211_get_tx_power : error (-1)
[ 2887.351761] alx 0000:03:00.0 eth0: Qualcomm Atheros AR816x/AR817x Ethernet [<MAC eth0>]
[ 3595.655305] ERROR @wl_dev_intvar_get : error (-1)
[ 3595.655313] ERROR @wl_cfg80211_get_tx_power : error (-1)

    ======== Done ========
```

---

### Post by Hadaka on 2014-08-30
Hi, from a wired connection please do,,,
COPY  and paste...
```
sudo apt-get update
sudo apt-get remove --purge bcmwl-kernel-source
sudo rm /etc/modprobe.d/blacklist-bcm43.conf
sudo apt-get install linux-firmware-nonfree 
```
then do..
```
sudo su
echo "blacklist b43" >>  /etc/modprobe.d/blacklist.conf
echo "blacklist ssb" >>  /etc/modprobe.d/blacklist.conf
exit 0
```
then do.
```
sudo modprobe bcma
sudo modprobe brcmsmac
```
May as well clean up your country code while you are at it,
```
sed -i 's/^REG.*=$/&US/' /etc/default/crda
echo -e "iw reg set US\niwlist scan\nexit0" | sudo tee -a /etc/rc.local
```
remove ethernet cable
boot and test

---

### Post by wn1ytw on 2014-08-30
thanks, but no wired connection is available (I'm a resident in a nursing home - wifi is it. And no 'teckies' on staff here)

---

### Post by weatherman2 on 2014-08-30
Go to this page:

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)

and page down to the section labeled "STA - No internet access"

---

### Post by wildmanne39 on 2014-08-30
Hi, just do:
```
sudo apt-get purge bcmwl-kernel-source
```
Then:
```
sudo su
echo "blacklist b43" >>  /etc/modprobe.d/blacklist.conf
echo "blacklist ssb" >>  /etc/modprobe.d/blacklist.conf
exit 0
```
```
sudo modprobe bcma
sudo modprobe brcmsmac
```
You do not need an internet connection because the brcmsmac driver is included in the kernel modules of ubuntu.

If it does not connect post click on the wireless scrit inmy signature nd post the file here.
Thanks

---

### Post by Hadaka on 2014-08-30
Hi wn1ytw, the wild man is correct please follow his suggestion.
then once you do get a valid internet connection please do.

```
sudo apt-get update
```
this will get you up to date with the current load
then do
```
sed -i 's/^REG.*=$/&US/' /etc/default/crda
echo -e "iw reg set US\niwlist scan\nexit 0" | sudo tee -a /etc/rc.local
```
thanks.

---

### Post by wn1ytw on 2014-08-30
Thank you both! I was just coming to say that I fixed it. The wired connection1 got corrupted. probably my jumpy finger on the mouse.

My note to myself:
wired connection



Somehow the 'wired connection 1' setting in ipv6 
'method' box got set from 'ignore' to 'automatic'

The wireless settings had stayed correct. My mouse finger must have jumped... it does that sadly.

Going to proceed with the other suggestions now. 
scott

EDIT Everything working nicely now, Thank you Hadaka and Wild Man!!

---

### Post by Hadaka on 2014-08-31
GREAT !!  We are pleased that worked for you .
 Enjoy.

---

