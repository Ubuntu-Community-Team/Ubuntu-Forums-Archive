---
title: "Wireless connected, no internet after clean install of 14.04 LTS"
date: 2014-09-23
forum: Networking &amp; Wireless
---

### Post by nickniebaum on 2014-09-23
I've read countless post after post about this... tried a lot of different things, but I simply don't understand enough to diagnose my problem. Here is my "wireless_script" output, after connecting to my router. I can connect via ethernet and wirelessly with Windows (dual booting). I'm on a Lenovo IdeaPad N586.

```

    ======== Wireless-Info START ========

System-Info ~~~~~~~~~~~~~~~~~~~~~~~~

nicks-laptop 3.13.0-35-generic i686,  Ubuntu 14.04.1 LTS, trusty

CPU    : AMD A6-4400M APU with Radeon(tm) HD Graphics
Memory : 3504 MB
Uptime : 21:03:21 up 1 min,  2 users,  load average: 1.12, 0.47, 0.18


lspci ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

01:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 07)
    Subsystem: Lenovo Device [17aa:3971]
    Kernel driver in use: r8169
02:00.0 Network controller [0280]: Broadcom Corporation BCM4313 802.11bgn Wireless Network Adapter [14e4:4727] (rev 01)
    Subsystem: Broadcom Corporation Device [14e4:051b]
    Kernel driver in use: wl


lsusb ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Bus 002 Device 002: ID 0bda:0129 Realtek Semiconductor Corp. RTS5129 Card Reader Controller
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 5986:0294 Acer, Inc 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 005 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


PCMCIA Card Info ~~~~~~~~~~~~~~~~~~~



iwconfig ~~~~~~~~~~~~~~~~~~~~~~~~~~~

wlan0     IEEE 802.11abg  ESSID:"suddenlink.net-E0A0"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: <MAC C-01 suddenlink.net-E0A0>   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          


rfkill ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

      Interface                Soft blocked  Hard blocked
0: ideapad_wlan: Wireless LAN      no            no
1: phy0: Wireless LAN              no            no
2: brcmwl-0: Wireless LAN          no            no


lsmod ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

wl                   3999690  0 
lib80211               14040  2 wl,lib80211_crypt_tkip
cfg80211              409394  1 wl


module parameters ~~~~~~~~~~~~~~~~~~

cfg80211      (2): cfg80211_disable_40mhz_24ghz=N | ieee80211_regdom=00


nm-tool ~~~~~~~~~~~~~~~~~~~~~~~~~~~~

State: connected (global)
==============================o=============o========o=============o=========o===========o==============o===========
 Interface & ID               | Type        | Driver | State       | Default | Speed     | Support      | HW Addr   
==============================o=============o========o=============o=========o===========o==============o===========
 wlan0  [suddenlink.net-E0A0] | 802.11 WiFi | wl     | connected   | yes     | 72 Mb/s   | WEP/WPA/WPA2 | <MAC wlan0>

    RSS-351540:      Infra, <MAC C-02 RSS-351540>, Freq 2462 MHz, Rate 54 Mb/s, Strength 100 WPA2
    RSS-351540:      Infra, <MAC C-03 RSS-351540>, Freq 2412 MHz, Rate 54 Mb/s, Strength 95 WPA2
    RSS-351540:      Infra, <MAC C-NA RSS-351540 3>, Freq 2462 MHz, Rate 54 Mb/s, Strength 19 WPA2
    Terri's Chromecast: Infra, <MAC C-NA Terri's Chromecast 1>, Freq 2427 MHz, Rate 54 Mb/s, Strength 25
    suddenlink.net-7B60: Infra, <MAC C-04 suddenlink.net-7B60>, Freq 2412 MHz, Rate 54 Mb/s, Strength 92 WPA2
    RSS-351540:      Infra, <MAC C-NA RSS-351540 2>, Freq 2437 MHz, Rate 54 Mb/s, Strength 20 WPA2
    suddenlink.net-2EE0: Infra, <MAC C-NA suddenlink.net-2EE0 1>, Freq 2462 MHz, Rate 54 Mb/s, Strength 10 WPA2
    linksys_SES_52484: Infra, <MAC C-NA linksys_SES_52484 1>, Freq 2437 MHz, Rate 54 Mb/s, Strength 25 WPA
    *suddenlink.net-E0A0: Infra, <MAC C-01 suddenlink.net-E0A0>, Freq 2462 MHz, Rate 54 Mb/s, Strength 100 WPA2

    Address:         192.168.0.12
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.0.1
    DNS:             192.168.0.1
------------------------------+-------------+--------+-------------+---------+-----------+--------------+-----------
 eth0                         | Wired       | r8169  | unavailable | no      |           |              | <MAC eth0>
------------------------------+-------------+--------+-------------+---------+-----------+--------------+-----------


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

suddenlink.net-E0A0  : ssid=suddenlink.net-E0A0 | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 


interfaces ~~~~~~~~~~~~~~~~~~~~~~~~~

# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback

resolv.conf ~~~~~~~~~~~~~~~~~~~~~~~~

nameserver 127.0.1.1
search suddenlink.net


Routes & Ping ~~~~~~~~~~~~~~~~~~~~~~

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.0.1     0.0.0.0         UG    0      0        0 wlan0
192.168.0.0     0.0.0.0         255.255.255.0   U     9      0        0 wlan0

--- 192.168.0.1 ping statistics ---
5 packets transmitted, 0 received, 100% packet loss, time 3999ms


--- 127.0.1.1 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 999ms
rtt min/avg/max/mdev = 0.031/0.033/0.036/0.006 ms


iw reg get ~~~~~~~~~~~~~~~~~~~~~~~~~

(Region : "en_US.UTF-8")
country US:
    (2402 - 2472 @ 40), (3, 27)
    (5170 - 5250 @ 40), (3, 17)
    (5250 - 5330 @ 40), (3, 20), DFS
    (5490 - 5600 @ 40), (3, 20), DFS
    (5650 - 5710 @ 40), (3, 20), DFS
    (5735 - 5835 @ 40), (3, 30)
    (57240 - 63720 @ 2160), (N/A, 40)


iwlist chan ~~~~~~~~~~~~~~~~~~~~~~~~

wlan0     32 channels in total; available frequencies :
          Channel 01 (2.412 GHz) - 11 (2.462 GHz)
          Channel 36 (5.18 GHz)
          Channel 38 (5.19 GHz)
          Channel 40 (5.2 GHz)
          Channel 42 (5.21 GHz)
          Channel 44 (5.22 GHz)
          Channel 46 (5.23 GHz)
          Channel 48 (5.24 GHz)
          Channel 52 (5.26 GHz)
          Channel 56 (5.28 GHz)
          Channel 60 (5.3 GHz)
          Channel 64 (5.32 GHz)
          Channel 100 (5.5 GHz)
          Channel 104 (5.52 GHz)
          Channel 108 (5.54 GHz)
          Channel 112 (5.56 GHz)
          Channel 116 (5.58 GHz)
          Channel 132 (5.66 GHz)
          Channel 136 (5.68 GHz)
          Channel 140 (5.7 GHz)
          Channel 149 (5.745 GHz)
          Channel 153 (5.765 GHz)

          Current Frequency=2.462 GHz (Channel 11)


iwlist scan ~~~~~~~~~~~~~~~~~~~~~~~~

wlan0     Scan completed :
          Cell 01 - Address: <MAC C-01 suddenlink.net-E0A0>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=70/70  Signal level=-27 dBm  
                    Encryption key:on
                    ESSID:"suddenlink.net-E0A0"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 20ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC C-02 RSS-351540>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=70/70  Signal level=-27 dBm  
                    Encryption key:on
                    ESSID:"RSS-351540"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 20ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: <MAC C-03 RSS-351540>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=67/70  Signal level=-43 dBm  
                    Encryption key:on
                    ESSID:"RSS-351540"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 20ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 04 - Address: <MAC C-04 suddenlink.net-7B60>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=68/70  Signal level=-42 dBm  
                    Encryption key:on
                    ESSID:"suddenlink.net-7B60"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 20ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
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
filename:       /lib/modules/3.13.0-35-generic/updates/dkms/wl.ko
srcversion:     FF25FE784DC6BDFF69DAFCB
depends:        cfg80211,lib80211
parm:           wl_txq_thresh:int
parm:           oneonly:int
parm:           piomode:int
parm:           instance_base:int
parm:           nompc:int
parm:           intf_name:string

[lib80211]
filename:       /lib/modules/3.13.0-35-generic/kernel/net/wireless/lib80211.ko
srcversion:     84DEF767F03D28E373F18E5
depends:        

[cfg80211]
filename:       /lib/modules/3.13.0-35-generic/kernel/net/wireless/cfg80211.ko
srcversion:     C2478077E22138832B71659
depends:        
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)


udev rules ~~~~~~~~~~~~~~~~~~~~~~~~~

# PCI device 0x10ec:0x8168 (r8169)
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

BOOT_IMAGE=/boot/vmlinuz-3.13.0-35-generic root=UUID=1951a3e5-9969-4773-bdc2-db6b33114713 ro quiet splash vt.handoff=7


dmesg ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

[    0.913284] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[    0.913715] audit: initializing netlink socket (disabled)
[    2.455468] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    3.653283] psmouse serio1: elantech: assuming hardware version 3 (with firmware version 0x450f02)
[   15.879477] wl: module license 'MIXED/Proprietary' taints kernel.
[   15.882763] wl: module verification failed: signature and/or  required key missing - tainting kernel
[   15.977724] INFO @wl_cfg80211_attach : Registered CFG80211 phy
[   16.154602] wlan0: Broadcom BCM4727 802.11 Hybrid Wireless Controller 6.30.223.141 (r415941)
[   20.751003] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[  114.386567] ERROR @wl_dev_intvar_get : error (-1)
[  114.386573] ERROR @wl_cfg80211_get_tx_power : error (-1)

    ======== Done ========
```
 
Please help, I miss my Ubuntu.

---

### Post by nickniebaum on 2014-09-23
Also, I wanted to mention that I tried the suggestion in the sticky about blacklisting b43 and ssb. It did not work.. however I did run wireless_script under those conditions; it is below. For now, I've reverted back, so the blacklists have been removed.

```

    ======== Wireless-Info START ========

System-Info ~~~~~~~~~~~~~~~~~~~~~~~~

nicks-laptop 3.13.0-35-generic i686,  Ubuntu 14.04.1 LTS, trusty

CPU    : AMD A6-4400M APU with Radeon(tm) HD Graphics
Memory : 3504 MB
Uptime : 21:26:08 up 1 min,  2 users,  load average: 1.10, 0.43, 0.16


lspci ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

01:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 07)
    Subsystem: Lenovo Device [17aa:3971]
    Kernel driver in use: r8169
02:00.0 Network controller [0280]: Broadcom Corporation BCM4313 802.11bgn Wireless Network Adapter [14e4:4727] (rev 01)
    Subsystem: Broadcom Corporation Device [14e4:051b]
    Kernel driver in use: wl


lsusb ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Bus 002 Device 002: ID 0bda:0129 Realtek Semiconductor Corp. RTS5129 Card Reader Controller
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 5986:0294 Acer, Inc 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 005 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


PCMCIA Card Info ~~~~~~~~~~~~~~~~~~~



iwconfig ~~~~~~~~~~~~~~~~~~~~~~~~~~~

wlan0     IEEE 802.11abg  ESSID:"suddenlink.net-E0A0"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: <MAC C-01 suddenlink.net-E0A0>   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          


rfkill ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

      Interface                Soft blocked  Hard blocked
0: ideapad_wlan: Wireless LAN      no            no
1: phy0: Wireless LAN              no            no
2: brcmwl-0: Wireless LAN          no            no


lsmod ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

wl                   3999690  0 
lib80211               14040  2 wl,lib80211_crypt_tkip
cfg80211              409394  1 wl


module parameters ~~~~~~~~~~~~~~~~~~

cfg80211      (2): cfg80211_disable_40mhz_24ghz=N | ieee80211_regdom=00


nm-tool ~~~~~~~~~~~~~~~~~~~~~~~~~~~~

State: connected (global)
==============================o=============o========o=============o=========o===========o==============o===========
 Interface & ID               | Type        | Driver | State       | Default | Speed     | Support      | HW Addr   
==============================o=============o========o=============o=========o===========o==============o===========
 wlan0  [suddenlink.net-E0A0] | 802.11 WiFi | wl     | connected   | yes     | 72 Mb/s   | WEP/WPA/WPA2 | <MAC wlan0>

    RSS-351540:      Infra, <MAC C-02 RSS-351540>, Freq 2462 MHz, Rate 54 Mb/s, Strength 100 WPA2
    suddenlink.net-7B60: Infra, <MAC C-03 suddenlink.net-7B60>, Freq 2412 MHz, Rate 54 Mb/s, Strength 90 WPA2
    RSS-351540:      Infra, <MAC C-04 RSS-351540>, Freq 2412 MHz, Rate 54 Mb/s, Strength 90 WPA2
    *suddenlink.net-E0A0: Infra, <MAC C-01 suddenlink.net-E0A0>, Freq 2462 MHz, Rate 54 Mb/s, Strength 100 WPA2
    linksys_SES_52484: Infra, <MAC C-NA linksys_SES_52484 1>, Freq 2437 MHz, Rate 54 Mb/s, Strength 17 WPA

    Address:         192.168.0.12
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.0.1
    DNS:             192.168.0.1
------------------------------+-------------+--------+-------------+---------+-----------+--------------+-----------
 eth0                         | Wired       | r8169  | unavailable | no      |           |              | <MAC eth0>
------------------------------+-------------+--------+-------------+---------+-----------+--------------+-----------


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

suddenlink.net-E0A0  : ssid=suddenlink.net-E0A0 | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 


interfaces ~~~~~~~~~~~~~~~~~~~~~~~~~

# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback

resolv.conf ~~~~~~~~~~~~~~~~~~~~~~~~

nameserver 127.0.1.1
search suddenlink.net


Routes & Ping ~~~~~~~~~~~~~~~~~~~~~~

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.0.1     0.0.0.0         UG    0      0        0 wlan0
192.168.0.0     0.0.0.0         255.255.255.0   U     9      0        0 wlan0

--- 192.168.0.1 ping statistics ---
5 packets transmitted, 0 received, 100% packet loss, time 3999ms


--- 127.0.1.1 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 999ms
rtt min/avg/max/mdev = 0.027/0.031/0.036/0.007 ms


iw reg get ~~~~~~~~~~~~~~~~~~~~~~~~~

(Region : "en_US.UTF-8")
country US:
    (2402 - 2472 @ 40), (3, 27)
    (5170 - 5250 @ 40), (3, 17)
    (5250 - 5330 @ 40), (3, 20), DFS
    (5490 - 5600 @ 40), (3, 20), DFS
    (5650 - 5710 @ 40), (3, 20), DFS
    (5735 - 5835 @ 40), (3, 30)
    (57240 - 63720 @ 2160), (N/A, 40)


iwlist chan ~~~~~~~~~~~~~~~~~~~~~~~~

wlan0     32 channels in total; available frequencies :
          Channel 01 (2.412 GHz) - 11 (2.462 GHz)
          Channel 36 (5.18 GHz)
          Channel 38 (5.19 GHz)
          Channel 40 (5.2 GHz)
          Channel 42 (5.21 GHz)
          Channel 44 (5.22 GHz)
          Channel 46 (5.23 GHz)
          Channel 48 (5.24 GHz)
          Channel 52 (5.26 GHz)
          Channel 56 (5.28 GHz)
          Channel 60 (5.3 GHz)
          Channel 64 (5.32 GHz)
          Channel 100 (5.5 GHz)
          Channel 104 (5.52 GHz)
          Channel 108 (5.54 GHz)
          Channel 112 (5.56 GHz)
          Channel 116 (5.58 GHz)
          Channel 132 (5.66 GHz)
          Channel 136 (5.68 GHz)
          Channel 140 (5.7 GHz)
          Channel 149 (5.745 GHz)
          Channel 153 (5.765 GHz)

          Current Frequency=2.462 GHz (Channel 11)


iwlist scan ~~~~~~~~~~~~~~~~~~~~~~~~

wlan0     Scan completed :
          Cell 01 - Address: <MAC C-01 suddenlink.net-E0A0>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=70/70  Signal level=-23 dBm  
                    Encryption key:on
                    ESSID:"suddenlink.net-E0A0"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 20ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC C-02 RSS-351540>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=70/70  Signal level=-23 dBm  
                    Encryption key:on
                    ESSID:"RSS-351540"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 20ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: <MAC C-03 suddenlink.net-7B60>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=68/70  Signal level=-42 dBm  
                    Encryption key:on
                    ESSID:"suddenlink.net-7B60"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 20ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
          Cell 04 - Address: <MAC C-04 RSS-351540>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=69/70  Signal level=-41 dBm  
                    Encryption key:on
                    ESSID:"RSS-351540"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 20ms ago
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

[/etc/modprobe.d/blacklist.conf]
blacklist b43
blacklist ssb


modinfo ~~~~~~~~~~~~~~~~~~~~~~~~~~~~

[wl]
filename:       /lib/modules/3.13.0-35-generic/updates/dkms/wl.ko
srcversion:     FF25FE784DC6BDFF69DAFCB
depends:        cfg80211,lib80211
parm:           wl_txq_thresh:int
parm:           oneonly:int
parm:           piomode:int
parm:           instance_base:int
parm:           nompc:int
parm:           intf_name:string

[lib80211]
filename:       /lib/modules/3.13.0-35-generic/kernel/net/wireless/lib80211.ko
srcversion:     84DEF767F03D28E373F18E5
depends:        

[cfg80211]
filename:       /lib/modules/3.13.0-35-generic/kernel/net/wireless/cfg80211.ko
srcversion:     C2478077E22138832B71659
depends:        
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)


udev rules ~~~~~~~~~~~~~~~~~~~~~~~~~

# PCI device 0x10ec:0x8168 (r8169)
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

BOOT_IMAGE=/boot/vmlinuz-3.13.0-35-generic root=UUID=1951a3e5-9969-4773-bdc2-db6b33114713 ro quiet splash vt.handoff=7


dmesg ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

[    0.911029] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[    0.911444] audit: initializing netlink socket (disabled)
[    2.373870] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    3.573831] psmouse serio1: elantech: assuming hardware version 3 (with firmware version 0x450f02)
[   16.207320] wl: module license 'MIXED/Proprietary' taints kernel.
[   16.212675] wl: module verification failed: signature and/or  required key missing - tainting kernel
[   16.395216] INFO @wl_cfg80211_attach : Registered CFG80211 phy
[   16.608875] wlan0: Broadcom BCM4727 802.11 Hybrid Wireless Controller 6.30.223.141 (r415941)
[   19.703804] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[  112.170813] ERROR @wl_dev_intvar_get : error (-1)
[  112.170822] ERROR @wl_cfg80211_get_tx_power : error (-1)

    ======== Done ========
```

---

### Post by chili555 on 2014-09-24
Please consult the sticky again. I believe you have the wrong driver and it must be purged.

---

### Post by nickniebaum on 2014-09-24
> **chili555 said:**
> Please consult the sticky again. I believe you have the wrong driver and it must be purged.

Thank you for your response to my question, I realize there a ton of these posts and answering them gets redundant, but I do appreciate it.

As I mentioned, I tried blacklisting those two drivers, but I did not try one at a time. I will go ahead and try that. Other than that, I'm not sure what else to try other than installing and removing some of the other driver packages listed for the other pci.ids. I assume my pci.id is 1434:4727, and I should be doing special case #1. What am I missing?

Thank you again.

---

### Post by jeremy31 on 2014-09-24
I think chili means, is that you have to ```
sudo apt-get purge bcmwl-kernel-source
``` and reboot.  If it doesn't work, then try the instructions for blacklisting b43 and ssb if they show in```
lsmod
``` and reboot again

---

### Post by nickniebaum on 2014-09-24
Before running that command, I tried running lsmod and grepping for b43 and ssb and was unable to find anything. Below is my lsmod... so maybe these aren't even installed?

```
Module                  Size  Used by
michael_mic            12540  4 
arc4                   12536  2 
snd_hda_codec_conexant    47785  1 
snd_hda_codec_hdmi     45440  1 
rfcomm                 53664  0 
bnep                   18895  2 
bluetooth             342208  10 bnep,rfcomm
uvcvideo               71309  0 
videobuf2_vmalloc      13048  1 uvcvideo
videobuf2_memops       13170  1 videobuf2_vmalloc
videobuf2_core         39258  1 uvcvideo
rts5139               269330  0 
videodev              108503  2 uvcvideo,videobuf2_core
kvm_amd                50537  0 
kvm                   388084  1 kvm_amd
snd_hda_intel          42730  5 
crc32_pclmul           12967  0 
aesni_intel            18156  0 
snd_hda_codec         164067  3 snd_hda_codec_hdmi,snd_hda_codec_conexant,snd_hda_intel
aes_i586               16995  1 aesni_intel
xts                    12749  1 aesni_intel
snd_hwdep              13272  1 snd_hda_codec
snd_pcm                85501  3 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
lrw                    13057  1 aesni_intel
snd_seq_midi           13132  0 
snd_seq_midi_event     14475  1 snd_seq_midi
snd_rawmidi            25135  1 snd_seq_midi
gf128mul               14503  2 lrw,xts
snd_page_alloc         14230  2 snd_pcm,snd_hda_intel
ablk_helper            13357  1 aesni_intel
cryptd                 15578  1 ablk_helper
snd_seq                55383  2 snd_seq_midi_event,snd_seq_midi
lib80211_crypt_tkip    17456  0 
snd_seq_device         14137  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              28584  2 snd_pcm,snd_seq
radeon               1420570  3 
joydev                 17101  0 
snd                    60939  21 snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_hda_codec_conexant,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_seq_midi
wl                   3999690  0 
k10temp                12958  0 
lib80211               14040  2 wl,lib80211_crypt_tkip
serio_raw              13230  0 
i2c_piix4              17723  0 
ttm                    72698  1 radeon
cfg80211              409394  1 wl
drm_kms_helper         47182  1 radeon
drm                   244037  5 ttm,drm_kms_helper,radeon
i2c_algo_bit           13197  1 radeon
soundcore              12600  1 snd
ideapad_laptop         17872  0 
sparse_keymap          13708  1 ideapad_laptop
mac_hid                13037  0 
video                  18903  0 
parport_pc             31981  0 
ppdev                  17391  0 
lp                     13299  0 
parport                40836  3 lp,ppdev,parport_pc
psmouse                91329  0 
ahci                   25579  2 
r8169                  61562  0 
libahci                27214  1 ahci
mii                    13654  1 r8169
```

---

### Post by nickniebaum on 2014-09-25
Solved the issue - while I wasn't quite sure what chili555 meant by "drivers must be purged", he was right, and jeremy31's clarification led me to running

```
sudo apt-get purge bcmwl-kernel-source
```

Which after rebooting, wireless began showing connectivity again. Thank you guys, I will mark this as solved!

---

