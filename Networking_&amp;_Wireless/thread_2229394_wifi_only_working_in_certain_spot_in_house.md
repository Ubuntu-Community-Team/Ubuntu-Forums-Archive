---
title: "wifi only working in certain spot in house"
date: 2014-06-12
forum: Networking &amp; Wireless
---

### Post by punkhunter18 on 2014-06-12
Im using ubuntu 14.04LTS, I had an update, restarted, when it turned back on, the wifi worked for about 5 mins then cut out. I tried the guide here [https://sites.google.com/site/easylinuxtipsproject/internet](https://sites.google.com/site/easylinuxtipsproject/internet) Nothing, i then reinstalled ubuntu still nothing after fresh install, updated, nothing, then tried the guide again, nothing. Im right next to the router, its an AT&T u-verse router. Today i was in my sons room on the other side of the house, and my wifi connects right away, but as soon as i go back to the living room where the router is the wifi stays connected but cant load any webpages. My windows partition connects fine, wifi connects fine anywhere in the house with a dongle, just wont connect with ubuntu using the original card. BCM 4352 802.11ac wirless network adapter, bcmwl-kernel-source is the additional driver, ive tried turning it off and back on, nothing. If anyone can help i would appreciate it.

---

### Post by punkhunter18 on 2014-06-14
is their anyone that would be able to help me?

---

### Post by varunendra on 2014-06-15
Welcome to the forums punkhunter18 !

Not sure if I can offer 'Any' help with such a new card using sta driver, but at least let's take a look at your overall setup. Please follow the instructions in this post to download and run 'wireless_script' (experimental version) and post back the report it generates : [http://ubuntuforums.org/showpost.php?p=13024222](http://ubuntuforums.org/showpost.php?p=13024222)

While posting the outputs, please use '**Code**' tags. It preserves the output's formatting and makes the post cleaner, compact and more readable. To see a quick 'HowTo' with screenshots, please follow the "Use Code Tags" link in my signature.

---

### Post by punkhunter18 on 2014-06-16
```

    ======== Wireless-Info START ========

System-Info ~~~~~~~~~~~~~~~~~~~~~~~~

kenneth-Aspire-M5-583P 3.13.0-29-generic x86_64,  Ubuntu 14.04 LTS, trusty

CPU    : Intel(R) Core(TM) i5-4200U CPU @ 1.60GHz
Memory : 5849 MB
Uptime : 14:35:18 up 6 min,  2 users,  load average: 0.38, 0.52, 0.30


lspci ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

04:00.0 Network controller [0280]: Broadcom Corporation BCM4352 802.11ac Wireless Network Adapter [14e4:43b1] (rev 03)
    Subsystem: Lite-On Communications Inc Device [11ad:6606]
    Kernel driver in use: wl
--
05:00.1 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 14)
    Subsystem: Acer Incorporated [ALI] Device [1025:079b]
    Kernel driver in use: r8169


lsusb ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Bus 001 Device 002: ID 8087:8000 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 002 Device 019: ID 04f3:0085 Elan Microelectronics Corp. 
Bus 002 Device 020: ID 07d1:3c16 D-Link System DWA-125 Wireless N 150 Adapter(rev.A2) [Ralink RT3070]
Bus 002 Device 003: ID 04ca:200a Lite-On Technology Corp. 
Bus 002 Device 002: ID 04f2:b3f6 Chicony Electronics Co., Ltd 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


PCMCIA Card Info ~~~~~~~~~~~~~~~~~~~



iwconfig ~~~~~~~~~~~~~~~~~~~~~~~~~~~

wlan1     IEEE 802.11bgn  ESSID:"ATT7q8j4h5"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: <MAC C-01 ATT7q8j4h5>   
          Bit Rate=52 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=70/70  Signal level=-39 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:247  Invalid misc:184   Missed beacon:0

wlan0     IEEE 802.11abg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          


rfkill ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

      Interface                 Soft blocked  Hard blocked
0: phy0: Wireless LAN               no            no
1: brcmwl-0: Wireless LAN           no            no
2: acer-wireless: Wireless LAN      no            no
3: acer-bluetooth: Bluetooth        no            no
4: phy1: Wireless LAN               no            no


lsmod ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

rt2800usb              27034  0 
rt2x00usb              20742  1 rt2800usb
rt2800lib              89076  1 rt2800usb
rt2x00lib              55307  3 rt2x00usb,rt2800lib,rt2800usb
mac80211              626557  3 rt2x00lib,rt2x00usb,rt2800lib
crc_ccitt              12707  1 rt2800lib
acer_wmi               32522  0 
sparse_keymap          13948  1 acer_wmi
wl                   4207846  0 
lib80211               14381  2 wl,lib80211_crypt_tkip
wmi                    19177  1 acer_wmi
cfg80211              484040  3 wl,mac80211,rt2x00lib
video                  19476  2 i915,acer_wmi


module parameters ~~~~~~~~~~~~~~~~~~

acer_wmi      (5): brightness=-1 | ec_raw_mode=N | force_series=0 | mailled=-1 | threeg=-1
cfg80211      (2): cfg80211_disable_40mhz_24ghz=N | ieee80211_regdom=00
mac80211      (5): beacon_loss_count=7 | ieee80211_default_rc_algo=minstrel_ht | max_nullfunc_tries=2 | max_probe_tries=5 | probe_wait_ms=500
rt2800usb     (1): nohwcrypt=N
video         (3): allow_duplicates=N | brightness_switch_enabled=Y | use_native_backlight=-1
wmi           (2): debug_dump_wdg=N | debug_event=N


nm-tool ~~~~~~~~~~~~~~~~~~~~~~~~~~~~

State: connected (global)
=======================o=============o===========o==============o=========o===========o==============o===========
 Interface & ID        | Type        | Driver    | State        | Default | Speed     | Support      | HW Addr   
=======================o=============o===========o==============o=========o===========o==============o===========
 wlan1  [ATT7q8j4h5 1] | 802.11 WiFi | rt2800usb | connected    | yes     | 52 Mb/s   | WEP/WPA/WPA2 | <MAC wlan1>

    HP-Print-FA-Photosmart 5520: Infra, <MAC C-02 HP-Print-FA-Photosmart 5520>, Freq 2437 MHz, Rate 54 Mb/s, Strength 85
    *ATT7q8j4h5:     Infra, <MAC C-01 ATT7q8j4h5>, Freq 2437 MHz, Rate 54 Mb/s, Strength 75 WPA WPA2
    2WIRE671:        Infra, <MAC C-03 2WIRE671>, Freq 2437 MHz, Rate 54 Mb/s, Strength 35 WPA WPA2
    ATT4s2j4d8:      Infra, <MAC C-NA ATT4s2j4d8 1>, Freq 2437 MHz, Rate 54 Mb/s, Strength 29 WPA WPA2

    Address:         192.168.1.150
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.254
    DNS:             192.168.1.254

    Address:         2602:306:cecf:d720::28
    Prefix:          128
    Gateway:         fe80::923e:abff:fea7:4ff0

    Address:         2602:306:cecf:d720:e9ed:7349:64d9:9038
    Prefix:          64
    Gateway:         fe80::923e:abff:fea7:4ff0

    Address:         2602:306:cecf:d720:1eaf:f7ff:fe10:5f4a
    Prefix:          64
    Gateway:         fe80::923e:abff:fea7:4ff0

    Address:         fe80::1eaf:f7ff:fe10:5f4a
    Prefix:          64
    Gateway:         fe80::923e:abff:fea7:4ff0

    Address:         2602:306:cecf:d720::28
    Prefix:          128
    Gateway:         ::
-----------------------+-------------+-----------+--------------+---------+-----------+--------------+-----------
 eth0                  | Wired       | r8169     | unavailable  | no      |           |              | <MAC eth0>
-----------------------+-------------+-----------+--------------+---------+-----------+--------------+-----------
 wlan0                 | 802.11 WiFi | wl        | disconnected | no      |           | WEP/WPA/WPA2 | <MAC wlan0>

    HP-Print-FA-Photosmart 5520: Infra, <MAC C-02 HP-Print-FA-Photosmart 5520>, Freq 2437 MHz, Rate 54 Mb/s, Strength 92
    ATT7q8j4h5:      Infra, <MAC C-01 ATT7q8j4h5>, Freq 2437 MHz, Rate 54 Mb/s, Strength 100 WPA WPA2
-----------------------+-------------+-----------+--------------+---------+-----------+--------------+-----------


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

2WIRE671             : ssid=2WIRE671 | mac-address=<MAC wlan1> | ipv4=auto | ipv6=auto 
ATT4s2j4d8           : ssid=ATT4s2j4d8 | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 
ATT7q8j4h5           : ssid=ATT7q8j4h5 | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 
ATT7q8j4h5 1         : ssid=ATT7q8j4h5 | mac-address=<MAC wlan1> | ipv4=auto | ipv6=auto 


interfaces ~~~~~~~~~~~~~~~~~~~~~~~~~

# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback

resolv.conf ~~~~~~~~~~~~~~~~~~~~~~~~

nameserver 127.0.1.1
search att.net


Routes & Ping ~~~~~~~~~~~~~~~~~~~~~~

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.254   0.0.0.0         UG    0      0        0 wlan1
192.168.1.0     0.0.0.0         255.255.255.0   U     9      0        0 wlan1

--- 192.168.1.254 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 1001ms
rtt min/avg/max/mdev = 2.628/2.714/2.801/0.100 ms

--- 127.0.1.1 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 999ms
rtt min/avg/max/mdev = 0.040/0.042/0.044/0.002 ms


iw reg get ~~~~~~~~~~~~~~~~~~~~~~~~~

(Region : "en_US.UTF-8")
country 00:
    (2402 - 2472 @ 40), (3, 20)
    (2457 - 2482 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (2474 - 2494 @ 20), (3, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
    (5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS


iwlist chan ~~~~~~~~~~~~~~~~~~~~~~~~

wlan1     14 channels in total; available frequencies :
          Channel 01 (2.412 GHz) - 14 (2.484 GHz)

          Current Frequency:2.437 GHz (Channel 6)
          Channel 01 (2.412 GHz) - 14 (2.484 GHz)
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

wlan1     Scan completed :
          Cell 01 - Address: <MAC C-01 ATT7q8j4h5>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=67/70  Signal level=-43 dBm  
                    Encryption key:on
                    ESSID:"ATT7q8j4h5"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000ae8caf92d9
                    Extra: Last beacon: 160ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC C-02 HP-Print-FA-Photosmart 5520>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=61/70  Signal level=-49 dBm  
                    Encryption key:off
                    ESSID:"HP-Print-FA-Photosmart 5520"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000ae95e58302
                    Extra: Last beacon: 172ms ago
          Cell 03 - Address: <MAC C-03 2WIRE671>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=29/70  Signal level=-81 dBm  
                    Encryption key:on
                    ESSID:"2WIRE671"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000000173e182
                    Extra: Last beacon: 212ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK

wlan0     Scan completed :
          Cell 01 - Address: <MAC C-01 ATT7q8j4h5>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=65/70  Signal level=-45 dBm  
                    Encryption key:on
                    ESSID:"ATT7q8j4h5"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 48ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC C-02 HP-Print-FA-Photosmart 5520>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=59/70  Signal level=-51 dBm  
                    Encryption key:off
                    ESSID:"HP-Print-FA-Photosmart 5520"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 48ms ago


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

[rt2800usb]
filename:       /lib/modules/3.13.0-29-generic/kernel/drivers/net/wireless/rt2x00/rt2800usb.ko
firmware:       rt2870.bin
version:        2.3.0
srcversion:     D6F814DAF78F2BEA3DA12CB
depends:        rt2x00lib,rt2800lib,rt2x00usb
parm:           nohwcrypt:Disable hardware encryption. (bool)

[rt2x00usb]
filename:       /lib/modules/3.13.0-29-generic/kernel/drivers/net/wireless/rt2x00/rt2x00usb.ko
version:        2.3.0
srcversion:     44768071492503F8EFE1EED
depends:        rt2x00lib,mac80211

[rt2800lib]
filename:       /lib/modules/3.13.0-29-generic/kernel/drivers/net/wireless/rt2x00/rt2800lib.ko
version:        2.3.0
srcversion:     9BD0087B6943A41E7FD8EDA
depends:        rt2x00lib,mac80211,crc-ccitt

[rt2x00lib]
filename:       /lib/modules/3.13.0-29-generic/kernel/drivers/net/wireless/rt2x00/rt2x00lib.ko
version:        2.3.0
srcversion:     C57F87A3569F5363E79FD42
depends:        mac80211,cfg80211

[mac80211]
filename:       /lib/modules/3.13.0-29-generic/kernel/net/mac80211/mac80211.ko
srcversion:     6F23437712851B1B0563BCB
depends:        cfg80211
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[crc_ccitt]
filename:       /lib/modules/3.13.0-29-generic/kernel/lib/crc-ccitt.ko
srcversion:     2294FCAD06D727386004EEB
depends:        

[wl]
filename:       /lib/modules/3.13.0-29-generic/updates/dkms/wl.ko
srcversion:     FF25FE784DC6BDFF69DAFCB
depends:        cfg80211,lib80211
parm:           wl_txq_thresh:int
parm:           oneonly:int
parm:           piomode:int
parm:           instance_base:int
parm:           nompc:int
parm:           intf_name:string

[lib80211]
filename:       /lib/modules/3.13.0-29-generic/kernel/net/wireless/lib80211.ko
srcversion:     84DEF767F03D28E373F18E5
depends:        

[cfg80211]
filename:       /lib/modules/3.13.0-29-generic/kernel/net/wireless/cfg80211.ko
srcversion:     8B3D642D1F2E6406EF33F74
depends:        
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)


udev rules ~~~~~~~~~~~~~~~~~~~~~~~~~

# PCI device 0x10ec:0x8168 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC eth0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

# PCI device 0x14e4:0x43b1 (wl)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC wlan0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

# USB device 0x:0x (rt2800usb)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC wlan1>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan1"


Custom files/entries ~~~~~~~~~~~~~~~

/etc/modules        : Default
/etc/rc.local       : Default
/etc/modprobe.d     : Not Default
/etc/pm/(cnf|pw|sl) : Not Default

[/etc/modprobe.d]
iwlwifi.conf      : remove iwlwifi \
                    (/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
                    && /sbin/modprobe -r mac80211
mlx4.conf         : softdep mlx4_core post: mlx4_en

[/etc/pm/power.d/95hdparm-apm] [executable]
#!/bin/sh
# tlp - if tlp is enabled, override corresponding script
#       in /usr/lib*/pm-utils/power.d/

CONFFILE=/etc/default/tlp
LIBDIRS='/usr/lib /usr/lib64'

for d in ${LIBDIRS}; do
    if [ -d "${d}/pm-utils/power.d" ]; then
        blocked="${d}/pm-utils/power.d/${0##*/}"
        break
    fi
done

if [ -n "$blocked" ] && [ -x "$blocked" ]; then
    # else nothing to disable -> don't read $CONFFILE

    if [ -e "$CONFFILE" ] && . "$CONFFILE" -- && [ "$TLP_ENABLE" = '1' ]; then
        # TLP is enabled -> disable $blocked
        echo "Notice: '${blocked}' disabled by TLP."
    else
        exec "$blocked" $*
    fi
fi

exit 0

[/etc/pm/power.d/disable_wol] [executable]
#!/bin/sh
# tlp - if tlp is enabled, override corresponding script
#       in /usr/lib*/pm-utils/power.d/

CONFFILE=/etc/default/tlp
LIBDIRS='/usr/lib /usr/lib64'

for d in ${LIBDIRS}; do
    if [ -d "${d}/pm-utils/power.d" ]; then
        blocked="${d}/pm-utils/power.d/${0##*/}"
        break
    fi
done

if [ -n "$blocked" ] && [ -x "$blocked" ]; then
    # else nothing to disable -> don't read $CONFFILE

    if [ -e "$CONFFILE" ] && . "$CONFFILE" -- && [ "$TLP_ENABLE" = '1' ]; then
        # TLP is enabled -> disable $blocked
        echo "Notice: '${blocked}' disabled by TLP."
    else
        exec "$blocked" $*
    fi
fi

exit 0

[/etc/pm/power.d/intel-audio-powersave] [executable]
#!/bin/sh
# tlp - if tlp is enabled, override corresponding script
#       in /usr/lib*/pm-utils/power.d/

CONFFILE=/etc/default/tlp
LIBDIRS='/usr/lib /usr/lib64'

for d in ${LIBDIRS}; do
    if [ -d "${d}/pm-utils/power.d" ]; then
        blocked="${d}/pm-utils/power.d/${0##*/}"
        break
    fi
done

if [ -n "$blocked" ] && [ -x "$blocked" ]; then
    # else nothing to disable -> don't read $CONFFILE

    if [ -e "$CONFFILE" ] && . "$CONFFILE" -- && [ "$TLP_ENABLE" = '1' ]; then
        # TLP is enabled -> disable $blocked
        echo "Notice: '${blocked}' disabled by TLP."
    else
        exec "$blocked" $*
    fi
fi

exit 0

[/etc/pm/power.d/laptop-mode] [executable]
#!/bin/sh
# tlp - if tlp is enabled, override corresponding script
#       in /usr/lib*/pm-utils/power.d/

CONFFILE=/etc/default/tlp
LIBDIRS='/usr/lib /usr/lib64'

for d in ${LIBDIRS}; do
    if [ -d "${d}/pm-utils/power.d" ]; then
        blocked="${d}/pm-utils/power.d/${0##*/}"
        break
    fi
done

if [ -n "$blocked" ] && [ -x "$blocked" ]; then
    # else nothing to disable -> don't read $CONFFILE

    if [ -e "$CONFFILE" ] && . "$CONFFILE" -- && [ "$TLP_ENABLE" = '1' ]; then
        # TLP is enabled -> disable $blocked
        echo "Notice: '${blocked}' disabled by TLP."
    else
        exec "$blocked" $*
    fi
fi

exit 0

[/etc/pm/power.d/pci_devices] [executable]
#!/bin/sh
# tlp - if tlp is enabled, override corresponding script
#       in /usr/lib*/pm-utils/power.d/

CONFFILE=/etc/default/tlp
LIBDIRS='/usr/lib /usr/lib64'

for d in ${LIBDIRS}; do
    if [ -d "${d}/pm-utils/power.d" ]; then
        blocked="${d}/pm-utils/power.d/${0##*/}"
        break
    fi
done

if [ -n "$blocked" ] && [ -x "$blocked" ]; then
    # else nothing to disable -> don't read $CONFFILE

    if [ -e "$CONFFILE" ] && . "$CONFFILE" -- && [ "$TLP_ENABLE" = '1' ]; then
        # TLP is enabled -> disable $blocked
        echo "Notice: '${blocked}' disabled by TLP."
    else
        exec "$blocked" $*
    fi
fi

exit 0

[/etc/pm/power.d/pcie_aspm] [executable]
#!/bin/sh
# tlp - if tlp is enabled, override corresponding script
#       in /usr/lib*/pm-utils/power.d/

CONFFILE=/etc/default/tlp
LIBDIRS='/usr/lib /usr/lib64'

for d in ${LIBDIRS}; do
    if [ -d "${d}/pm-utils/power.d" ]; then
        blocked="${d}/pm-utils/power.d/${0##*/}"
        break
    fi
done

if [ -n "$blocked" ] && [ -x "$blocked" ]; then
    # else nothing to disable -> don't read $CONFFILE

    if [ -e "$CONFFILE" ] && . "$CONFFILE" -- && [ "$TLP_ENABLE" = '1' ]; then
        # TLP is enabled -> disable $blocked
        echo "Notice: '${blocked}' disabled by TLP."
    else
        exec "$blocked" $*
    fi
fi

exit 0

[/etc/pm/power.d/sata_alpm] [executable]
#!/bin/sh
# tlp - if tlp is enabled, override corresponding script
#       in /usr/lib*/pm-utils/power.d/

CONFFILE=/etc/default/tlp
LIBDIRS='/usr/lib /usr/lib64'

for d in ${LIBDIRS}; do
    if [ -d "${d}/pm-utils/power.d" ]; then
        blocked="${d}/pm-utils/power.d/${0##*/}"
        break
    fi
done

if [ -n "$blocked" ] && [ -x "$blocked" ]; then
    # else nothing to disable -> don't read $CONFFILE

    if [ -e "$CONFFILE" ] && . "$CONFFILE" -- && [ "$TLP_ENABLE" = '1' ]; then
        # TLP is enabled -> disable $blocked
        echo "Notice: '${blocked}' disabled by TLP."
    else
        exec "$blocked" $*
    fi
fi

exit 0

[/etc/pm/power.d/sched-powersave] [executable]
#!/bin/sh
# tlp - if tlp is enabled, override corresponding script
#       in /usr/lib*/pm-utils/power.d/

CONFFILE=/etc/default/tlp
LIBDIRS='/usr/lib /usr/lib64'

for d in ${LIBDIRS}; do
    if [ -d "${d}/pm-utils/power.d" ]; then
        blocked="${d}/pm-utils/power.d/${0##*/}"
        break
    fi
done

if [ -n "$blocked" ] && [ -x "$blocked" ]; then
    # else nothing to disable -> don't read $CONFFILE

    if [ -e "$CONFFILE" ] && . "$CONFFILE" -- && [ "$TLP_ENABLE" = '1' ]; then
        # TLP is enabled -> disable $blocked
        echo "Notice: '${blocked}' disabled by TLP."
    else
        exec "$blocked" $*
    fi
fi

exit 0

[/etc/pm/power.d/usb_bluetooth] [executable]
#!/bin/sh
# tlp - if tlp is enabled, override corresponding script
#       in /usr/lib*/pm-utils/power.d/

CONFFILE=/etc/default/tlp
LIBDIRS='/usr/lib /usr/lib64'

for d in ${LIBDIRS}; do
    if [ -d "${d}/pm-utils/power.d" ]; then
        blocked="${d}/pm-utils/power.d/${0##*/}"
        break
    fi
done

if [ -n "$blocked" ] && [ -x "$blocked" ]; then
    # else nothing to disable -> don't read $CONFFILE

    if [ -e "$CONFFILE" ] && . "$CONFFILE" -- && [ "$TLP_ENABLE" = '1' ]; then
        # TLP is enabled -> disable $blocked
        echo "Notice: '${blocked}' disabled by TLP."
    else
        exec "$blocked" $*
    fi
fi

exit 0

[/etc/pm/power.d/wireless] [executable]
#!/bin/sh
# tlp - if tlp is enabled, override corresponding script
#       in /usr/lib*/pm-utils/power.d/

CONFFILE=/etc/default/tlp
LIBDIRS='/usr/lib /usr/lib64'

for d in ${LIBDIRS}; do
    if [ -d "${d}/pm-utils/power.d" ]; then
        blocked="${d}/pm-utils/power.d/${0##*/}"
        break
    fi
done

if [ -n "$blocked" ] && [ -x "$blocked" ]; then
    # else nothing to disable -> don't read $CONFFILE

    if [ -e "$CONFFILE" ] && . "$CONFFILE" -- && [ "$TLP_ENABLE" = '1' ]; then
        # TLP is enabled -> disable $blocked
        echo "Notice: '${blocked}' disabled by TLP."
    else
        exec "$blocked" $*
    fi
fi

exit 0

[/etc/pm/power.d/xfs_buffer] [executable]
#!/bin/sh
# tlp - if tlp is enabled, override corresponding script
#       in /usr/lib*/pm-utils/power.d/

CONFFILE=/etc/default/tlp
LIBDIRS='/usr/lib /usr/lib64'

for d in ${LIBDIRS}; do
    if [ -d "${d}/pm-utils/power.d" ]; then
        blocked="${d}/pm-utils/power.d/${0##*/}"
        break
    fi
done

if [ -n "$blocked" ] && [ -x "$blocked" ]; then
    # else nothing to disable -> don't read $CONFFILE

    if [ -e "$CONFFILE" ] && . "$CONFFILE" -- && [ "$TLP_ENABLE" = '1' ]; then
        # TLP is enabled -> disable $blocked
        echo "Notice: '${blocked}' disabled by TLP."
    else
        exec "$blocked" $*
    fi
fi

exit 0


Kernel boot line ~~~~~~~~~~~~~~~~~~~

BOOT_IMAGE=/boot/vmlinuz-3.13.0-29-generic.efi.signed root=UUID=fede0f5e-fa46-4eec-925d-32cea07968d1 ro quiet splash vt.handoff=7


dmesg ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

[    0.737912] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[    0.738309] audit: initializing netlink socket (disabled)
[    0.914045] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[   11.232348] wmi: Mapper loaded
[   11.238433] wl: module license 'MIXED/Proprietary' taints kernel.
[   11.239908] wl: module verification failed: signature and/or  required key missing - tainting kernel
[   11.263256] INFO @wl_cfg80211_attach : Registered CFG80211 phy
[   11.314473] wlan0: Broadcom BCM43b1 802.11 Hybrid Wireless Controller 6.30.223.141 (r415941)
[   11.466516] acer_wmi: Acer Laptop ACPI-WMI Extras
[   11.466615] acer_wmi: Function bitmap for Communication Button: 0x801
[   11.466758] acer_wmi: Brightness must be controlled by acpi video driver
[   11.489226] acer_wmi: Enabling Launch Manager failed: 0xe2 - 0x0
[   19.327518] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   26.199194] ERROR @wl_inform_single_bss : cfg80211_inform_bss_frame error
[   49.226854] ERROR @wl_inform_single_bss : cfg80211_inform_bss_frame error
[   74.504322] ERROR @wl_inform_single_bss : cfg80211_inform_bss_frame error
[   79.729416] ERROR @wl_inform_single_bss : cfg80211_inform_bss_frame error
[   85.558786] ERROR @wl_inform_single_bss : cfg80211_inform_bss_frame error
[  116.261270] ERROR @wl_inform_single_bss : cfg80211_inform_bss_frame error
[  125.704093] rtsx_pci 0000:05:00.0: vpd r/w failed.  This is likely a firmware bug on this device.  Contact the card vendor for a firmware update.
[  126.343732] rtsx_pci 0000:05:00.0: vpd r/w failed.  This is likely a firmware bug on this device.  Contact the card vendor for a firmware update.
[  126.499467] ERROR @wl_inform_single_bss : cfg80211_inform_bss_frame error
[  130.049970] ieee80211 phy1: rt2x00_set_rt: Info - RT chipset 3070, rev 0201 detected
[  130.060270] ieee80211 phy1: rt2x00_set_rf: Info - RF chipset 0005 detected
[  130.071586] ieee80211 phy1: rt2x00lib_request_firmware: Info - Loading firmware file 'rt2870.bin'
[  130.080633] ieee80211 phy1: rt2x00lib_request_firmware: Info - Firmware detected - version: 0.29
[  130.332917] IPv6: ADDRCONF(NETDEV_UP): wlan1: link is not ready
[  130.333727] IPv6: ADDRCONF(NETDEV_UP): wlan1: link is not ready
[  131.576533] wlan1: authenticate with <MAC C-01 ATT7q8j4h5>
[  131.599899] wlan1: send auth to <MAC C-01 ATT7q8j4h5> (try 1/3)
[  131.601392] wlan1: authenticated
[  131.604909] wlan1: associate with <MAC C-01 ATT7q8j4h5> (try 1/3)
[  131.607887] wlan1: RX AssocResp from <MAC C-01 ATT7q8j4h5> (capab=0x411 status=0 aid=3)
[  131.611455] wlan1: associated
[  131.611505] IPv6: ADDRCONF(NETDEV_CHANGE): wlan1: link becomes ready
[  132.432435] ERROR @wl_inform_single_bss : cfg80211_inform_bss_frame error
[  133.599685] rtsx_pci 0000:05:00.0: vpd r/w failed.  This is likely a firmware bug on this device.  Contact the card vendor for a firmware update.
[  134.079437] rtsx_pci 0000:05:00.0: vpd r/w failed.  This is likely a firmware bug on this device.  Contact the card vendor for a firmware update.
[  143.399789] rtsx_pci 0000:05:00.0: vpd r/w failed.  This is likely a firmware bug on this device.  Contact the card vendor for a firmware update.
[  143.871763] rtsx_pci 0000:05:00.0: vpd r/w failed.  This is likely a firmware bug on this device.  Contact the card vendor for a firmware update.
[  159.144491] ERROR @wl_inform_single_bss : cfg80211_inform_bss_frame error
[  192.201640] ERROR @wl_inform_single_bss : cfg80211_inform_bss_frame error
[  235.187230] ERROR @wl_inform_single_bss : cfg80211_inform_bss_frame error
[  264.245096] ieee80211 phy1: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 4 in queue 2
[  264.245123] ieee80211 phy1: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 4 in queue 2
[  264.245130] ieee80211 phy1: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 4 in queue 2
[  288.200513] ERROR @wl_inform_single_bss : cfg80211_inform_bss_frame error
[  351.141468] ERROR @wl_inform_single_bss : cfg80211_inform_bss_frame error
[  406.141214] ERROR @wl_dev_intvar_get : error (-1)
[  406.141217] ERROR @wl_cfg80211_get_tx_power : error (-1)
[  414.186255] ERROR @wl_inform_single_bss : cfg80211_inform_bss_frame error
[  421.144838] ERROR @wl_inform_single_bss : cfg80211_inform_bss_frame error

    ======== Done ========
```

---

### Post by punkhunter18 on 2014-06-16
```

    ======== Wireless-Info START ========

System-Info ~~~~~~~~~~~~~~~~~~~~~~~~

kenneth-Aspire-M5-583P 3.13.0-29-generic x86_64,  Ubuntu 14.04 LTS, trusty

CPU    : Intel(R) Core(TM) i5-4200U CPU @ 1.60GHz
Memory : 5849 MB
Uptime : 17:42:20 up 4 min,  2 users,  load average: 0.43, 0.48, 0.24


lspci ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

04:00.0 Network controller [0280]: Broadcom Corporation BCM4352 802.11ac Wireless Network Adapter [14e4:43b1] (rev 03)
    Subsystem: Lite-On Communications Inc Device [11ad:6606]
    Kernel driver in use: wl
--
05:00.1 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 14)
    Subsystem: Acer Incorporated [ALI] Device [1025:079b]
    Kernel driver in use: r8169


lsusb ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Bus 001 Device 002: ID 8087:8000 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 002 Device 019: ID 04f3:0085 Elan Microelectronics Corp. 
Bus 002 Device 003: ID 04ca:200a Lite-On Technology Corp. 
Bus 002 Device 002: ID 04f2:b3f6 Chicony Electronics Co., Ltd 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


PCMCIA Card Info ~~~~~~~~~~~~~~~~~~~



iwconfig ~~~~~~~~~~~~~~~~~~~~~~~~~~~

wlan0     IEEE 802.11abg  ESSID:"ATT7q8j4h5"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: <MAC C-01 ATT7q8j4h5>   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          


rfkill ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

      Interface                 Soft blocked  Hard blocked
0: phy0: Wireless LAN               no            no
1: brcmwl-0: Wireless LAN           no            no
2: acer-wireless: Wireless LAN      no            no
3: acer-bluetooth: Bluetooth        no            no


lsmod ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

acer_wmi               32522  0 
sparse_keymap          13948  1 acer_wmi
wl                   4207846  0 
lib80211               14381  2 wl,lib80211_crypt_tkip
cfg80211              484040  1 wl
wmi                    19177  1 acer_wmi
video                  19476  2 i915,acer_wmi


module parameters ~~~~~~~~~~~~~~~~~~

acer_wmi      (5): brightness=-1 | ec_raw_mode=N | force_series=0 | mailled=-1 | threeg=-1
cfg80211      (2): cfg80211_disable_40mhz_24ghz=N | ieee80211_regdom=00
video         (3): allow_duplicates=N | brightness_switch_enabled=Y | use_native_backlight=-1
wmi           (2): debug_dump_wdg=N | debug_event=N


nm-tool ~~~~~~~~~~~~~~~~~~~~~~~~~~~~

State: connected (global)
=====================o=============o========o==============o=========o===========o==============o===========
 Interface & ID      | Type        | Driver | State        | Default | Speed     | Support      | HW Addr   
=====================o=============o========o==============o=========o===========o==============o===========
 eth0                | Wired       | r8169  | unavailable  | no      |           |              | <MAC eth0>
---------------------+-------------+--------+--------------+---------+-----------+--------------+-----------
 wlan0  [ATT7q8j4h5] | 802.11 WiFi | wl     | connected    | yes     | 144 Mb/s  | WEP/WPA/WPA2 | <MAC wlan0>

    HP-Print-FA-Photosmart 5520: Infra, <MAC C-02 HP-Print-FA-Photosmart 5520>, Freq 2437 MHz, Rate 54 Mb/s, Strength 89
    NETGEAR74:       Infra, <MAC C-04 NETGEAR74>, Freq 2412 MHz, Rate 54 Mb/s, Strength 39 WPA2
    Marlon y Telesa: Infra, <MAC C-03 Marlon y Telesa>, Freq 2412 MHz, Rate 54 Mb/s, Strength 34 WPA
    2WIRE671:        Infra, <MAC C-NA 2WIRE671 1>, Freq 2437 MHz, Rate 54 Mb/s, Strength 32 WPA WPA2
    Cisco_10C55B2A:  Infra, <MAC C-NA Cisco_10C55B2A 1>, Freq 5785 MHz, Rate 54 Mb/s, Strength 19 WPA2
    *ATT7q8j4h5:     Infra, <MAC C-01 ATT7q8j4h5>, Freq 2437 MHz, Rate 54 Mb/s, Strength 78 WPA WPA2
    2WIRE471:        Infra, <MAC C-NA 2WIRE471 1>, Freq 2462 MHz, Rate 54 Mb/s, Strength 25 WPA WPA2

    Address:         192.168.1.137
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.254
    DNS:             192.168.1.254

    Address:         2602:306:cecf:d720::18
    Prefix:          128
    Gateway:         fe80::923e:abff:fea7:4ff0

    Address:         2602:306:cecf:d720:1d85:a9bf:a715:854d
    Prefix:          64
    Gateway:         fe80::923e:abff:fea7:4ff0

    Address:         2602:306:cecf:d720:2ae3:47ff:fec8:a64b
    Prefix:          64
    Gateway:         fe80::923e:abff:fea7:4ff0

    Address:         fe80::2ae3:47ff:fec8:a64b
    Prefix:          64
    Gateway:         fe80::923e:abff:fea7:4ff0

    Address:         2602:306:cecf:d720::18
    Prefix:          128
    Gateway:         ::
---------------------+-------------+--------+--------------+---------+-----------+--------------+-----------


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

2WIRE671             : ssid=2WIRE671 | mac-address=<MAC wlan1> | ipv4=auto | ipv6=auto 
ATT4s2j4d8           : ssid=ATT4s2j4d8 | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 
ATT7q8j4h5           : ssid=ATT7q8j4h5 | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 


interfaces ~~~~~~~~~~~~~~~~~~~~~~~~~

# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback

resolv.conf ~~~~~~~~~~~~~~~~~~~~~~~~

nameserver 127.0.1.1
search att.net


Routes & Ping ~~~~~~~~~~~~~~~~~~~~~~

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.254   0.0.0.0         UG    0      0        0 wlan0
192.168.1.0     0.0.0.0         255.255.255.0   U     9      0        0 wlan0

--- 192.168.1.254 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 1001ms
rtt min/avg/max/mdev = 1.143/1.894/2.645/0.751 ms

--- 127.0.1.1 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 999ms
rtt min/avg/max/mdev = 0.023/0.029/0.035/0.006 ms


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
          Channel 165 (5.825 GHz)

          Current Frequency:2.437 GHz (Channel 6)


iwlist scan ~~~~~~~~~~~~~~~~~~~~~~~~

wlan0     Scan completed :
          Cell 01 - Address: <MAC C-01 ATT7q8j4h5>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=67/70  Signal level=-43 dBm  
                    Encryption key:on
                    ESSID:"ATT7q8j4h5"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 20ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC C-02 HP-Print-FA-Photosmart 5520>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=65/70  Signal level=-45 dBm  
                    Encryption key:off
                    ESSID:"HP-Print-FA-Photosmart 5520"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 20ms ago
          Cell 03 - Address: <MAC C-03 Marlon y Telesa>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=30/70  Signal level=-80 dBm  
                    Encryption key:on
                    ESSID:"Marlon y Telesa"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 20ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 04 - Address: <MAC C-04 NETGEAR74>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=28/70  Signal level=-82 dBm  
                    Encryption key:on
                    ESSID:"NETGEAR74"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 23348ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
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
filename:       /lib/modules/3.13.0-29-generic/updates/dkms/wl.ko
srcversion:     FF25FE784DC6BDFF69DAFCB
depends:        cfg80211,lib80211
parm:           wl_txq_thresh:int
parm:           oneonly:int
parm:           piomode:int
parm:           instance_base:int
parm:           nompc:int
parm:           intf_name:string

[lib80211]
filename:       /lib/modules/3.13.0-29-generic/kernel/net/wireless/lib80211.ko
srcversion:     84DEF767F03D28E373F18E5
depends:        

[cfg80211]
filename:       /lib/modules/3.13.0-29-generic/kernel/net/wireless/cfg80211.ko
srcversion:     8B3D642D1F2E6406EF33F74
depends:        
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)


udev rules ~~~~~~~~~~~~~~~~~~~~~~~~~

# PCI device 0x10ec:0x8168 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC eth0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

# PCI device 0x14e4:0x43b1 (wl)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC wlan0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

# USB device 0x:0x (rt2800usb)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC wlan1>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan1"


Custom files/entries ~~~~~~~~~~~~~~~

/etc/modules        : Default
/etc/rc.local       : Default
/etc/modprobe.d     : Not Default
/etc/pm/(cnf|pw|sl) : Not Default

[/etc/modprobe.d]
iwlwifi.conf      : remove iwlwifi \
                    (/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
                    && /sbin/modprobe -r mac80211
mlx4.conf         : softdep mlx4_core post: mlx4_en

[/etc/pm/power.d/95hdparm-apm] [executable]
#!/bin/sh
# tlp - if tlp is enabled, override corresponding script
#       in /usr/lib*/pm-utils/power.d/

CONFFILE=/etc/default/tlp
LIBDIRS='/usr/lib /usr/lib64'

for d in ${LIBDIRS}; do
    if [ -d "${d}/pm-utils/power.d" ]; then
        blocked="${d}/pm-utils/power.d/${0##*/}"
        break
    fi
done

if [ -n "$blocked" ] && [ -x "$blocked" ]; then
    # else nothing to disable -> don't read $CONFFILE

    if [ -e "$CONFFILE" ] && . "$CONFFILE" -- && [ "$TLP_ENABLE" = '1' ]; then
        # TLP is enabled -> disable $blocked
        echo "Notice: '${blocked}' disabled by TLP."
    else
        exec "$blocked" $*
    fi
fi

exit 0

[/etc/pm/power.d/disable_wol] [executable]
#!/bin/sh
# tlp - if tlp is enabled, override corresponding script
#       in /usr/lib*/pm-utils/power.d/

CONFFILE=/etc/default/tlp
LIBDIRS='/usr/lib /usr/lib64'

for d in ${LIBDIRS}; do
    if [ -d "${d}/pm-utils/power.d" ]; then
        blocked="${d}/pm-utils/power.d/${0##*/}"
        break
    fi
done

if [ -n "$blocked" ] && [ -x "$blocked" ]; then
    # else nothing to disable -> don't read $CONFFILE

    if [ -e "$CONFFILE" ] && . "$CONFFILE" -- && [ "$TLP_ENABLE" = '1' ]; then
        # TLP is enabled -> disable $blocked
        echo "Notice: '${blocked}' disabled by TLP."
    else
        exec "$blocked" $*
    fi
fi

exit 0

[/etc/pm/power.d/intel-audio-powersave] [executable]
#!/bin/sh
# tlp - if tlp is enabled, override corresponding script
#       in /usr/lib*/pm-utils/power.d/

CONFFILE=/etc/default/tlp
LIBDIRS='/usr/lib /usr/lib64'

for d in ${LIBDIRS}; do
    if [ -d "${d}/pm-utils/power.d" ]; then
        blocked="${d}/pm-utils/power.d/${0##*/}"
        break
    fi
done

if [ -n "$blocked" ] && [ -x "$blocked" ]; then
    # else nothing to disable -> don't read $CONFFILE

    if [ -e "$CONFFILE" ] && . "$CONFFILE" -- && [ "$TLP_ENABLE" = '1' ]; then
        # TLP is enabled -> disable $blocked
        echo "Notice: '${blocked}' disabled by TLP."
    else
        exec "$blocked" $*
    fi
fi

exit 0

[/etc/pm/power.d/laptop-mode] [executable]
#!/bin/sh
# tlp - if tlp is enabled, override corresponding script
#       in /usr/lib*/pm-utils/power.d/

CONFFILE=/etc/default/tlp
LIBDIRS='/usr/lib /usr/lib64'

for d in ${LIBDIRS}; do
    if [ -d "${d}/pm-utils/power.d" ]; then
        blocked="${d}/pm-utils/power.d/${0##*/}"
        break
    fi
done

if [ -n "$blocked" ] && [ -x "$blocked" ]; then
    # else nothing to disable -> don't read $CONFFILE

    if [ -e "$CONFFILE" ] && . "$CONFFILE" -- && [ "$TLP_ENABLE" = '1' ]; then
        # TLP is enabled -> disable $blocked
        echo "Notice: '${blocked}' disabled by TLP."
    else
        exec "$blocked" $*
    fi
fi

exit 0

[/etc/pm/power.d/pci_devices] [executable]
#!/bin/sh
# tlp - if tlp is enabled, override corresponding script
#       in /usr/lib*/pm-utils/power.d/

CONFFILE=/etc/default/tlp
LIBDIRS='/usr/lib /usr/lib64'

for d in ${LIBDIRS}; do
    if [ -d "${d}/pm-utils/power.d" ]; then
        blocked="${d}/pm-utils/power.d/${0##*/}"
        break
    fi
done

if [ -n "$blocked" ] && [ -x "$blocked" ]; then
    # else nothing to disable -> don't read $CONFFILE

    if [ -e "$CONFFILE" ] && . "$CONFFILE" -- && [ "$TLP_ENABLE" = '1' ]; then
        # TLP is enabled -> disable $blocked
        echo "Notice: '${blocked}' disabled by TLP."
    else
        exec "$blocked" $*
    fi
fi

exit 0

[/etc/pm/power.d/pcie_aspm] [executable]
#!/bin/sh
# tlp - if tlp is enabled, override corresponding script
#       in /usr/lib*/pm-utils/power.d/

CONFFILE=/etc/default/tlp
LIBDIRS='/usr/lib /usr/lib64'

for d in ${LIBDIRS}; do
    if [ -d "${d}/pm-utils/power.d" ]; then
        blocked="${d}/pm-utils/power.d/${0##*/}"
        break
    fi
done

if [ -n "$blocked" ] && [ -x "$blocked" ]; then
    # else nothing to disable -> don't read $CONFFILE

    if [ -e "$CONFFILE" ] && . "$CONFFILE" -- && [ "$TLP_ENABLE" = '1' ]; then
        # TLP is enabled -> disable $blocked
        echo "Notice: '${blocked}' disabled by TLP."
    else
        exec "$blocked" $*
    fi
fi

exit 0

[/etc/pm/power.d/sata_alpm] [executable]
#!/bin/sh
# tlp - if tlp is enabled, override corresponding script
#       in /usr/lib*/pm-utils/power.d/

CONFFILE=/etc/default/tlp
LIBDIRS='/usr/lib /usr/lib64'

for d in ${LIBDIRS}; do
    if [ -d "${d}/pm-utils/power.d" ]; then
        blocked="${d}/pm-utils/power.d/${0##*/}"
        break
    fi
done

if [ -n "$blocked" ] && [ -x "$blocked" ]; then
    # else nothing to disable -> don't read $CONFFILE

    if [ -e "$CONFFILE" ] && . "$CONFFILE" -- && [ "$TLP_ENABLE" = '1' ]; then
        # TLP is enabled -> disable $blocked
        echo "Notice: '${blocked}' disabled by TLP."
    else
        exec "$blocked" $*
    fi
fi

exit 0

[/etc/pm/power.d/sched-powersave] [executable]
#!/bin/sh
# tlp - if tlp is enabled, override corresponding script
#       in /usr/lib*/pm-utils/power.d/

CONFFILE=/etc/default/tlp
LIBDIRS='/usr/lib /usr/lib64'

for d in ${LIBDIRS}; do
    if [ -d "${d}/pm-utils/power.d" ]; then
        blocked="${d}/pm-utils/power.d/${0##*/}"
        break
    fi
done

if [ -n "$blocked" ] && [ -x "$blocked" ]; then
    # else nothing to disable -> don't read $CONFFILE

    if [ -e "$CONFFILE" ] && . "$CONFFILE" -- && [ "$TLP_ENABLE" = '1' ]; then
        # TLP is enabled -> disable $blocked
        echo "Notice: '${blocked}' disabled by TLP."
    else
        exec "$blocked" $*
    fi
fi

exit 0

[/etc/pm/power.d/usb_bluetooth] [executable]
#!/bin/sh
# tlp - if tlp is enabled, override corresponding script
#       in /usr/lib*/pm-utils/power.d/

CONFFILE=/etc/default/tlp
LIBDIRS='/usr/lib /usr/lib64'

for d in ${LIBDIRS}; do
    if [ -d "${d}/pm-utils/power.d" ]; then
        blocked="${d}/pm-utils/power.d/${0##*/}"
        break
    fi
done

if [ -n "$blocked" ] && [ -x "$blocked" ]; then
    # else nothing to disable -> don't read $CONFFILE

    if [ -e "$CONFFILE" ] && . "$CONFFILE" -- && [ "$TLP_ENABLE" = '1' ]; then
        # TLP is enabled -> disable $blocked
        echo "Notice: '${blocked}' disabled by TLP."
    else
        exec "$blocked" $*
    fi
fi

exit 0

[/etc/pm/power.d/wireless] [executable]
#!/bin/sh
# tlp - if tlp is enabled, override corresponding script
#       in /usr/lib*/pm-utils/power.d/

CONFFILE=/etc/default/tlp
LIBDIRS='/usr/lib /usr/lib64'

for d in ${LIBDIRS}; do
    if [ -d "${d}/pm-utils/power.d" ]; then
        blocked="${d}/pm-utils/power.d/${0##*/}"
        break
    fi
done

if [ -n "$blocked" ] && [ -x "$blocked" ]; then
    # else nothing to disable -> don't read $CONFFILE

    if [ -e "$CONFFILE" ] && . "$CONFFILE" -- && [ "$TLP_ENABLE" = '1' ]; then
        # TLP is enabled -> disable $blocked
        echo "Notice: '${blocked}' disabled by TLP."
    else
        exec "$blocked" $*
    fi
fi

exit 0

[/etc/pm/power.d/xfs_buffer] [executable]
#!/bin/sh
# tlp - if tlp is enabled, override corresponding script
#       in /usr/lib*/pm-utils/power.d/

CONFFILE=/etc/default/tlp
LIBDIRS='/usr/lib /usr/lib64'

for d in ${LIBDIRS}; do
    if [ -d "${d}/pm-utils/power.d" ]; then
        blocked="${d}/pm-utils/power.d/${0##*/}"
        break
    fi
done

if [ -n "$blocked" ] && [ -x "$blocked" ]; then
    # else nothing to disable -> don't read $CONFFILE

    if [ -e "$CONFFILE" ] && . "$CONFFILE" -- && [ "$TLP_ENABLE" = '1' ]; then
        # TLP is enabled -> disable $blocked
        echo "Notice: '${blocked}' disabled by TLP."
    else
        exec "$blocked" $*
    fi
fi

exit 0


Kernel boot line ~~~~~~~~~~~~~~~~~~~

BOOT_IMAGE=/boot/vmlinuz-3.13.0-29-generic.efi.signed root=UUID=fede0f5e-fa46-4eec-925d-32cea07968d1 ro quiet splash vt.handoff=7


dmesg ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

[    0.737888] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[    0.738291] audit: initializing netlink socket (disabled)
[    0.920520] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[   11.240155] wmi: Mapper loaded
[   11.279203] wl: module license 'MIXED/Proprietary' taints kernel.
[   11.282601] wl: module verification failed: signature and/or  required key missing - tainting kernel
[   11.319521] INFO @wl_cfg80211_attach : Registered CFG80211 phy
[   11.370243] wlan0: Broadcom BCM43b1 802.11 Hybrid Wireless Controller 6.30.223.141 (r415941)
[   11.454181] acer_wmi: Acer Laptop ACPI-WMI Extras
[   11.454281] acer_wmi: Function bitmap for Communication Button: 0x801
[   11.454395] acer_wmi: Brightness must be controlled by acpi video driver
[   11.481311] acer_wmi: Enabling Launch Manager failed: 0xe2 - 0x0
[   18.669826] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   25.255782] ERROR @wl_inform_single_bss : cfg80211_inform_bss_frame error
[   47.935717] ERROR @wl_inform_single_bss : cfg80211_inform_bss_frame error
[   80.994454] ERROR @wl_inform_single_bss : cfg80211_inform_bss_frame error
[  154.273121] ERROR @wl_inform_single_bss : cfg80211_inform_bss_frame error
[  178.255059] ERROR @wl_inform_single_bss : cfg80211_inform_bss_frame error
[  221.376913] ERROR @wl_inform_single_bss : cfg80211_inform_bss_frame error
[  284.252913] ERROR @wl_inform_single_bss : cfg80211_inform_bss_frame error
[  295.589539] ERROR @wl_dev_intvar_get : error (-1)
[  295.589544] ERROR @wl_cfg80211_get_tx_power : error (-1)
[  307.580101] ERROR @wl_inform_single_bss : cfg80211_inform_bss_frame error


```

from my sons room with the laptop wifi

---

### Post by varunendra on 2014-06-17
Try changing the encryption type in the router to pure WPA2-PSK with AES (CCMP). Currently it is using WPA/WPA2 mixed mode with TKIP which is not recommended (is meant only for backward compatibility with ancient wireless devices). Also try changing the channel to 1 or 11 (if the router is in 2.4 GHz mode).

If the router supports dual band (2.4/5 GHz), try them separately, one at a time, not in auto/mixed mode. Some drivers may work better with 5 GHz, but some may not work at all. I'm not sure which category the "wl" driver falls in.

**PS:**
Additionally, if the above don't work, try disabling the power management script for wireless -
```
sudo chmod -x /etc/pm/power.d/wireless
```
Then reboot, and check -
```
iwconfig
```
The "Power Management" on wlan0 should appear to be "off". If so, does it help connecting?

---

