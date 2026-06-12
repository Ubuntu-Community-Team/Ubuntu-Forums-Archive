---
title: "Ubuntu 14.04 - wifi stops working after suspend/logout (Acer 5536)"
date: 2015-04-30
forum: Networking &amp; Wireless
---

### Post by mani3 on 2015-04-30
Hi all!

My first post here.):P

Since my recent upgrade from 12.04 LTS to 14.04, I've had wifi issues when trying to reconnect from suspend or from a disconnected signal.  Previous Ubuntu version have been superb with my wifi!  I've adjusted channels on my router, which made some difference in the beginning. Restarting the network-manager sometimes had results.  Only a cold boot or router reset reconnects properly though.  I have read about using older kernel ath9k drivers as a workaround?

I would be grateful if anyone can shed any light.


Wifi disconnected output:


```


    ======== Wireless-Info START ========

System-Info ~~~~~~~~~~~~~~~~~~~~~~~~

Aspire-5536 3.13.0-49-generic x86_64,  Ubuntu 14.04.2 LTS, trusty

CPU    : AMD Turion(tm) X2 Dual-Core Mobile RM-72
Memory : 3700 MB
Uptime : 23:45:58 up 38 min,  2 users,  load average: 0.64, 0.52, 0.50


lspci ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

03:00.0 Ethernet controller [0200]: Broadcom Corporation NetLink BCM5784M Gigabit Ethernet PCIe [14e4:1698] (rev 10)
    Subsystem: Acer Incorporated [ALI] Device [1025:0207]
    Kernel driver in use: tg3
06:00.0 Network controller [0280]: Qualcomm Atheros AR928X Wireless Network Adapter (PCI-Express) [168c:002a] (rev 01)
    Subsystem: Quanta Microsystems, Inc EM303 802.11bgn Wireless Mini PCIe Card [AR9281] [1a32:0303]
    Kernel driver in use: ath9k


lsusb ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Bus 002 Device 003: ID 064e:a103 Suyin Corp. Acer/HP Integrated Webcam [CN0314]
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 002: ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


PCMCIA Card Info ~~~~~~~~~~~~~~~~~~~



iwconfig ~~~~~~~~~~~~~~~~~~~~~~~~~~~

wlan0     IEEE 802.11bgn  ESSID:"VM058157-2G"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=16 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          


rfkill ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

      Interface                 Soft blocked  Hard blocked
0: phy0: Wireless LAN               no            no
1: acer-wireless: Wireless LAN      no            no


lsmod ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

acer_wmi               32522  0 
sparse_keymap          13948  1 acer_wmi
ath9k                 164164  0 
ath9k_common           13551  1 ath9k
ath9k_hw              453856  2 ath9k_common,ath9k
wmi                    19177  1 acer_wmi
ath                    28698  3 ath9k_common,ath9k,ath9k_hw
mac80211              630669  1 ath9k
cfg80211              484040  3 ath,ath9k,mac80211
video                  19476  1 acer_wmi


module parameters ~~~~~~~~~~~~~~~~~~

acer_wmi      (5): brightness=-1 | ec_raw_mode=N | force_series=0 | mailled=-1 | threeg=-1
ath9k         (5): blink=0 | bt_ant_diversity=0 | btcoex_enable=0 | nohwcrypt=1 | ps_enable=0
cfg80211      (2): cfg80211_disable_40mhz_24ghz=N | ieee80211_regdom=00
mac80211      (5): beacon_loss_count=7 | ieee80211_default_rc_algo=minstrel_ht | max_nullfunc_tries=2 | max_probe_tries=5 | probe_wait_ms=500
video         (3): allow_duplicates=N | brightness_switch_enabled=Y | use_native_backlight=-1
wmi           (2): debug_dump_wdg=N | debug_event=N


nm-tool ~~~~~~~~~~~~~~~~~~~~~~~~~~~~

State: disconnected
================o=============o========o==========  ===o=========o===========o==============o=========  ==
 Interface & ID | Type        | Driver | State       | Default | Speed     | Support      | HW Addr   
================o=============o========o==========  ===o=========o===========o==============o=========  ==
 wlan0          | 802.11 WiFi | ath9k  | unavailable | no      |           | WEP/WPA/WPA2 | <MAC wlan0>
----------------+-------------+--------+-------------+---------+-----------+--------------+-----------
 eth0           | Wired       | tg3    | unavailable | no      |           |              | <MAC eth0>
----------------+-------------+--------+-------------+---------+-----------+--------------+-----------


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

AndroidAP            : ssid=AndroidAP | mac-address=<MAC wlan0> | ipv6=auto | ipv4=auto 
BUFFALO              : ssid=BUFFALO | mac-address=0:17:c4:7c:6a:dc | ipv4=auto | ipv6=auto 
HTC Portable Hotspot : ssid=HTC Portable Hotspot | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 
NETGEAR2             : ssid=NETGEAR2 | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 
portthru             : ssid=portthru | mac-address=<MAC wlan0> | ipv6=auto | ipv4=auto 
SKY5F336             : ssid=SKY5F336 | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 
stargate12           : ssid=stargate12 | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 
TALKTALK-5A8B3C      : ssid=TALKTALK-5A8B3C | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 
virginmedia2356741   : ssid=virginmedia2356741 | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 
virginmedia6433998   : ssid=virginmedia6433998 | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 
VM058157-2G          : ssid=VM058157-2G | bssid=<MAC C-12 VM058157-2G> | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 
VM338431-2G          : ssid=VM338431-2G | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 


interfaces ~~~~~~~~~~~~~~~~~~~~~~~~~

auto lo
iface lo inet loopback


resolv.conf ~~~~~~~~~~~~~~~~~~~~~~~~



Routes & Ping ~~~~~~~~~~~~~~~~~~~~~~

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface


iw reg get ~~~~~~~~~~~~~~~~~~~~~~~~~

(Region : "en_GB.UTF-8")
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
          Cell 01 - Address: <MAC C-01 EE-BrightBox-bq2dhh>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=37/70  Signal level=-73 dBm  
                    Encryption key:on
                    ESSID:"EE-BrightBox-bq2dhh"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000003d7efb5dbe
                    Extra: Last beacon: 12ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC C-02 TALKTALK-0F5877>
                    Channel:5
                    Frequency:2.432 GHz (Channel 5)
                    Quality=28/70  Signal level=-82 dBm  
                    Encryption key:on
                    ESSID:"TALKTALK-0F5877"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000ca82cc4179
                    Extra: Last beacon: 12ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: <MAC C-03 VM338431-2G>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=22/70  Signal level=-88 dBm  
                    Encryption key:on
                    ESSID:"VM338431-2G"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000000d28945d
                    Extra: Last beacon: 12ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 04 - Address: <MAC C-04 SKY45130>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=33/70  Signal level=-77 dBm  
                    Encryption key:on
                    ESSID:"SKY45130"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000037cf48d2b
                    Extra: Last beacon: 12ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 05 - Address: <MAC C-05 SKY5F336>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=47/70  Signal level=-63 dBm  
                    Encryption key:on
                    ESSID:"SKY5F336"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000051ad6e258
                    Extra: Last beacon: 12ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 06 - Address: <MAC C-06 BTHub3-FFKQ>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=37/70  Signal level=-73 dBm  
                    Encryption key:on
                    ESSID:"BTHub3-FFKQ"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000066ddd71a1
                    Extra: Last beacon: 12ms ago
          Cell 07 - Address: <MAC C-07 BTWiFi-with-FON>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=37/70  Signal level=-73 dBm  
                    Encryption key:off
                    ESSID:"BTWiFi-with-FON"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000066ddd8664
                    Extra: Last beacon: 12ms ago
          Cell 08 - Address: <MAC C-08 virginmedia2356741>
                    Channel:13
                    Frequency:2.472 GHz (Channel 13)
                    Quality=31/70  Signal level=-79 dBm  
                    Encryption key:on
                    ESSID:"virginmedia2356741"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000363a2496c
                    Extra: Last beacon: 4088ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 09 - Address: <MAC C-09 stargate12>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=21/70  Signal level=-89 dBm  
                    Encryption key:on
                    ESSID:"stargate12"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000001d68852c148
                    Extra: Last beacon: 18472ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
          Cell 10 - Address: <MAC C-10 TALKTALK-5A8B3C>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=22/70  Signal level=-88 dBm  
                    Encryption key:on
                    ESSID:"TALKTALK-5A8B3C"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000003ac63727176
                    Extra: Last beacon: 12040ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
          Cell 11 - Address: <MAC C-11 VM058157-2G>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=65/70  Signal level=-45 dBm  
                    Encryption key:on
                    ESSID:"VM058157-2G"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000b67b46ed7
                    Extra: Last beacon: 12ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 12 - Address: <MAC C-12 VM058157-2G>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=63/70  Signal level=-47 dBm  
                    Encryption key:on
                    ESSID:"VM058157-2G"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000b67b3c180
                    Extra: Last beacon: 800ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK


blacklist ~~~~~~~~~~~~~~~~~~~~~~~~~~

[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci

[/etc/modprobe.d/blacklist.conf]
blacklist asus_wmi
blacklist asus_wmi
blacklist asus_wmi

[/etc/modprobe.d/osspd.conf]
blacklist snd-pcm-oss
blacklist snd-mixer-oss
blacklist snd-seq-oss


modinfo ~~~~~~~~~~~~~~~~~~~~~~~~~~~~

[acer_wmi]
filename:       /lib/modules/3.13.0-49-generic/kernel/drivers/platform/x86/acer-wmi.ko
srcversion:     67298645909B235E329C186
depends:        wmi,sparse-keymap,video
parm:           mailled:Set initial state of Mail LED (int)
parm:           brightness:Set initial LCD backlight brightness (int)
parm:           threeg:Set initial state of 3G hardware (int)
parm:           force_series:Force a different laptop series (int)
parm:           ec_raw_mode:Enable EC raw mode (bool)

[ath9k]
filename:       /lib/modules/3.13.0-49-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k.ko
srcversion:     274594FBD61F5DF88102A4C
depends:        ath9k_hw,mac80211,ath9k_common,cfg80211,ath
parm:           debug:Debugging mask (uint)
parm:           nohwcrypt:Disable hardware encryption (int)
parm:           blink:Enable LED blink on activity (int)
parm:           btcoex_enable:Enable wifi-BT coexistence (int)
parm:           bt_ant_diversity:Enable WLAN/BT RX antenna diversity (int)
parm:           ps_enable:Enable WLAN PowerSave (int)

[ath9k_common]
filename:       /lib/modules/3.13.0-49-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_common.ko
srcversion:     93644B269B570BC55CF5154
depends:        ath,ath9k_hw

[ath9k_hw]
filename:       /lib/modules/3.13.0-49-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_hw.ko
srcversion:     65C14EF588BF1A68181643C
depends:        ath

[wmi]
filename:       /lib/modules/3.13.0-49-generic/kernel/drivers/platform/x86/wmi.ko
srcversion:     CED5410F008DC70DF5F064B
depends:        
parm:           debug_event:Log WMI Events [0/1] (bool)
parm:           debug_dump_wdg:Dump available WMI interfaces [0/1] (bool)

[ath]
filename:       /lib/modules/3.13.0-49-generic/kernel/drivers/net/wireless/ath/ath.ko
srcversion:     88A67C5359B02C5A710AFCF
depends:        cfg80211

[mac80211]
filename:       /lib/modules/3.13.0-49-generic/kernel/net/mac80211/mac80211.ko
srcversion:     29A87AE7782ED3657631C32
depends:        cfg80211
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[cfg80211]
filename:       /lib/modules/3.13.0-49-generic/kernel/net/wireless/cfg80211.ko
srcversion:     176113E009F723E69BE9BAB
depends:        
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

[video]
filename:       /lib/modules/3.13.0-49-generic/kernel/drivers/acpi/video.ko
srcversion:     FD364E86295EDCA7831C8FB
depends:        
parm:           brightness_switch_enabled:bool
parm:           allow_duplicates:bool
parm:           use_native_backlight:int


udev rules ~~~~~~~~~~~~~~~~~~~~~~~~~

# PCI device 0x14e4:0x1698 (tg3)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC eth0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

# PCI device 0x168c:0x002a (ath9k)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC wlan0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"


Custom files/entries ~~~~~~~~~~~~~~~

/etc/modules        : Not Default
/etc/rc.local       : Default
/etc/modprobe.d     : Not Default
/etc/pm/(cnf|pw|sl) : Not Default

[/etc/modules]
ath9k

[/etc/modprobe.d]
ath9k.conf        : options ath9k nohwcrypt=1
                    options ath9k nohwcrypt=1
ath9k.conf~       : options ath9k nohwcrypt=1
                    options ath9k nohwcrypt=1
                    options ath9k nohwcrypt=1
                    options ath9k nohwcrypt=1
                    options ath9k nohwcrypt=1
                    options ath9k nohwcrypt=1
                    options ath9k nohwcrypt=1
ath9k.conf.save   : options ath9k nohwcrypt=1
                    options ath9k nohwcrypt=1
                    options ath9k nohwcrypt=1
                    options ath9k nohwcrypt=1
                    options ath9k nohwcrypt=1
                    options ath9k nohwcrypt=1
hp.conf           : options hp_wmi wireless=1
iwlwifi.conf      : options iwlwifi 11n_disable=1
mlx4.conf         : softdep mlx4_core post: mlx4_en

[/etc/pm/sleep.d/wakenet.sh]

[/etc/pm/sleep.d/10_resume_wifi]
#!/bin/sh

case "${1}" in
  resume|thaw)
    nmcli r wifi off && nmcli r wifi on;
esac


Kernel boot line ~~~~~~~~~~~~~~~~~~~

BOOT_IMAGE=/boot/vmlinuz-3.13.0-49-generic root=UUID=8b1161dc-3dba-4ad7-94ba-5f865556fe08 ro quiet splash vt.handoff=7


dmesg ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

[    0.662644] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[    0.663033] audit: initializing netlink socket (disabled)
[    1.550244] tg3 0000:03:00.0 eth0: attached PHY is 5784 (10/100/1000Base-T Ethernet) (WireSpeed[1], EEE[0])
[   22.241795] wmi: Mapper loaded
[   22.706649] ath: EEPROM regdomain: 0x65
[   22.706656] ath: EEPROM indicates we should expect a direct regpair map
[   22.706661] ath: Country alpha2 being used: 00
[   22.706663] ath: Regpair used: 0x65
[   23.819905] acer_wmi: Acer Laptop ACPI-WMI Extras
[   23.824148] acer_wmi: Function bitmap for Communication Device: 0x3
[   23.824725] acer_wmi: Brightness must be controlled by acpi video driver
[   26.708177] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   29.029395] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   29.032847] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   30.128065] wlan0: authenticate with <MAC C-12 VM058157-2G>
[   30.145439] wlan0: send auth to <MAC C-12 VM058157-2G> (try 1/3)
[   30.147704] wlan0: authenticated
[   30.152075] wlan0: associate with <MAC C-12 VM058157-2G> (try 1/3)
[   30.159109] wlan0: RX AssocResp from <MAC C-12 VM058157-2G> (capab=0x411 status=0 aid=1)
[   30.159171] wlan0: associated
[   30.159209] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   30.163747] ath: EEPROM regdomain: 0x833a
[   30.163755] ath: EEPROM indicates we should expect a country code
[   30.163757] ath: doing EEPROM country->regdmn map search
[   30.163759] ath: country maps to regdmn code: 0x37
[   30.163761] ath: Country alpha2 being used: GB
[   30.163763] ath: Regpair used: 0x37
[   30.163766] ath: regdomain 0x833a dynamically updated by country IE
[  273.416484] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=62.252.232.55 DST=192.168.0.3 LEN=40 TOS=0x00 PREC=0x00 TTL=58 ID=978 PROTO=TCP SPT=443 DPT=36226 WINDOW=0 RES=0x00 RST URGP=0 
[  273.416555] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=62.252.232.55 DST=192.168.0.3 LEN=40 TOS=0x00 PREC=0x00 TTL=58 ID=979 PROTO=TCP SPT=443 DPT=36226 WINDOW=0 RES=0x00 RST URGP=0 
[  284.408158] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=62.252.170.163 DST=192.168.0.3 LEN=40 TOS=0x00 PREC=0x00 TTL=58 ID=35571 PROTO=TCP SPT=443 DPT=42954 WINDOW=0 RES=0x00 RST URGP=0 
[ 2128.662673] wlan0: deauthenticating from <MAC C-12 VM058157-2G> by local choice (reason=3)
[ 2131.609623] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 2137.675592] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 2138.388339] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 2141.426214] wlan0: authenticate with <MAC C-12 VM058157-2G>
[ 2141.444254] wlan0: send auth to <MAC C-12 VM058157-2G> (try 1/3)
[ 2141.446637] wlan0: authenticated
[ 2141.448126] wlan0: associate with <MAC C-12 VM058157-2G> (try 1/3)
[ 2141.452594] wlan0: RX AssocResp from <MAC C-12 VM058157-2G> (capab=0x411 status=0 aid=1)
[ 2141.452687] wlan0: associated
[ 2141.452708] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 2141.465361] ath: EEPROM regdomain: 0x833a
[ 2141.465369] ath: EEPROM indicates we should expect a country code
[ 2141.465372] ath: doing EEPROM country->regdmn map search
[ 2141.465374] ath: country maps to regdmn code: 0x37
[ 2141.465376] ath: Country alpha2 being used: GB
[ 2141.465378] ath: Regpair used: 0x37
[ 2141.465380] ath: regdomain 0x833a dynamically updated by country IE
[ 2171.819072] wlan0: deauthenticating from <MAC C-12 VM058157-2G> by local choice (reason=3)
[ 2171.922990] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 2172.050148] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 2172.174782] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 2172.269846] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 2172.375028] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 2172.473600] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 2172.590252] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 2172.691280] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 2172.801097] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 2182.877225] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 2185.660612] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 2186.323592] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 2188.494188] wlan0: authenticate with <MAC C-12 VM058157-2G>
[ 2188.511552] wlan0: send auth to <MAC C-12 VM058157-2G> (try 1/3)
[ 2188.513991] wlan0: authenticated
[ 2188.516110] wlan0: associate with <MAC C-12 VM058157-2G> (try 1/3)
[ 2188.520545] wlan0: RX AssocResp from <MAC C-12 VM058157-2G> (capab=0x411 status=0 aid=1)
[ 2188.520693] wlan0: associated
[ 2188.520778] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 2188.539943] ath: EEPROM regdomain: 0x833a
[ 2188.539963] ath: EEPROM indicates we should expect a country code
[ 2188.539973] ath: doing EEPROM country->regdmn map search
[ 2188.539980] ath: country maps to regdmn code: 0x37
[ 2188.539987] ath: Country alpha2 being used: GB
[ 2188.539994] ath: Regpair used: 0x37
[ 2188.540151] ath: regdomain 0x833a dynamically updated by country IE
[ 2198.198724] wlan0: deauthenticating from <MAC C-12 VM058157-2G> by local choice (reason=3)
[ 2201.622284] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 2202.395985] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 2202.556659] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 2207.256778] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 2209.682766] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 2209.784278] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 2210.492282] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 2223.580416] wlan0: authenticate with <MAC C-12 VM058157-2G>
[ 2223.625389] wlan0: send auth to <MAC C-12 VM058157-2G> (try 1/3)
[ 2223.630085] wlan0: authenticated
[ 2223.632156] wlan0: associate with <MAC C-12 VM058157-2G> (try 1/3)
[ 2223.636681] wlan0: RX AssocResp from <MAC C-12 VM058157-2G> (capab=0x411 status=0 aid=1)
[ 2223.636770] wlan0: associated
[ 2223.636920] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 2223.643931] ath: EEPROM regdomain: 0x833a
[ 2223.643939] ath: EEPROM indicates we should expect a country code
[ 2223.643942] ath: doing EEPROM country->regdmn map search
[ 2223.643944] ath: country maps to regdmn code: 0x37
[ 2223.643946] ath: Country alpha2 being used: GB
[ 2223.643948] ath: Regpair used: 0x37
[ 2223.643951] ath: regdomain 0x833a dynamically updated by country IE
[ 2224.188676] wlan0: deauthenticating from <MAC C-12 VM058157-2G> by local choice (reason=3)
[ 2224.305148] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 2224.891071] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 2224.995464] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 2226.993345] wlan0: authenticate with <MAC C-12 VM058157-2G>
[ 2227.048464] wlan0: send auth to <MAC C-12 VM058157-2G> (try 1/3)
[ 2227.050775] wlan0: authenticated
[ 2227.056090] wlan0: associate with <MAC C-12 VM058157-2G> (try 1/3)
[ 2227.060614] wlan0: RX AssocResp from <MAC C-12 VM058157-2G> (capab=0x411 status=0 aid=1)
[ 2227.060737] wlan0: associated
[ 2227.060804] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 2227.069308] ath: EEPROM regdomain: 0x833a
[ 2227.069319] ath: EEPROM indicates we should expect a country code
[ 2227.069322] ath: doing EEPROM country->regdmn map search
[ 2227.069324] ath: country maps to regdmn code: 0x37
[ 2227.069327] ath: Country alpha2 being used: GB
[ 2227.069329] ath: Regpair used: 0x37
[ 2227.069332] ath: regdomain 0x833a dynamically updated by country IE
[ 2227.086542] wlan0: deauthenticating from <MAC C-12 VM058157-2G> by local choice (reason=2)
[ 2227.107809] wlan0: authenticate with <MAC C-12 VM058157-2G>
[ 2227.126438] wlan0: send auth to <MAC C-12 VM058157-2G> (try 1/3)
[ 2251.058676] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 2251.128485] wlan0: authenticate with <MAC C-12 VM058157-2G>
[ 2251.148413] wlan0: send auth to <MAC C-12 VM058157-2G> (try 1/3)
[ 2251.252131] wlan0: send auth to <MAC C-12 VM058157-2G> (try 2/3)
[ 2251.356078] wlan0: send auth to <MAC C-12 VM058157-2G> (try 3/3)
[ 2251.460045] wlan0: authentication with <MAC C-12 VM058157-2G> timed out
[ 2257.926312] wlan0: authenticate with <MAC C-12 VM058157-2G>
[ 2257.946885] wlan0: direct probe to <MAC C-12 VM058157-2G> (try 1/3)
[ 2258.148138] wlan0: direct probe to <MAC C-12 VM058157-2G> (try 2/3)
[ 2258.352346] wlan0: direct probe to <MAC C-12 VM058157-2G> (try 3/3)
[ 2258.556059] wlan0: authentication with <MAC C-12 VM058157-2G> timed out
[ 2272.561108] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 2273.319244] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 2274.377131] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 2275.435380] wlan0: authenticate with <MAC C-12 VM058157-2G>
[ 2275.453961] wlan0: direct probe to <MAC C-12 VM058157-2G> (try 1/3)
[ 2275.473155] wlan0: deauthenticating from <MAC C-12 VM058157-2G> by local choice (reason=3)
[ 2275.480391] wlan0: authenticate with <MAC C-11 VM058157-2G>
[ 2275.496957] wlan0: send auth to <MAC C-11 VM058157-2G> (try 1/3)
[ 2275.600116] wlan0: send auth to <MAC C-11 VM058157-2G> (try 2/3)
[ 2275.704133] wlan0: send auth to <MAC C-11 VM058157-2G> (try 3/3)
[ 2275.808121] wlan0: authentication with <MAC C-11 VM058157-2G> timed out
[ 2280.454992] wlan0: authenticate with <MAC C-12 VM058157-2G>
[ 2280.473412] wlan0: direct probe to <MAC C-12 VM058157-2G> (try 1/3)
[ 2280.473612] wlan0: deauthenticating from <MAC C-12 VM058157-2G> by local choice (reason=3)
[ 2281.425880] wlan0: authenticate with <MAC C-12 VM058157-2G>
[ 2281.448274] wlan0: direct probe to <MAC C-12 VM058157-2G> (try 1/3)
[ 2281.652084] wlan0: direct probe to <MAC C-12 VM058157-2G> (try 2/3)
[ 2281.856290] wlan0: direct probe to <MAC C-12 VM058157-2G> (try 3/3)
[ 2282.060087] wlan0: authentication with <MAC C-12 VM058157-2G> timed out

    ======== Done ========

```

---

