---
title: "Acer Aspire V; Atheros AR9462 Can't connect to wifi networks"
date: 2014-10-31
forum: Networking &amp; Wireless
---

### Post by samuel21 on 2014-10-31
I am a new user of ubuntu. I started with mint 17 with the same problem, i tried couple suggested solutions but none helped. Now i freshly installed ubuntu and updated the problem still exsists. I can find wifi networks, but as i try to connect it just times out after a while. In my schools open network i could get it working once (Mint) but after that i could not get connected anymore. 

Script output:
```


    ======== Wireless-Info START ========

System-Info ~~~~~~~~~~~~~~~~~~~~~~~~

bubbis 3.13.0-39-generic x86_64,  Ubuntu 14.04.1 LTS, trusty

CPU    : Intel(R) Pentium(R) 3556U @ 1.70GHz
Memory : 3876 MB
Uptime : 00:23:05 up 21 min,  2 users,  load average: 0,13, 0,66, 0,66


lspci ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

01:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 0c)
    Subsystem: Acer Incorporated [ALI] Device [1025:0918]
    Kernel driver in use: r8169
02:00.0 Network controller [0280]: Qualcomm Atheros AR9462 Wireless Network Adapter [168c:0034] (rev 01)
    Subsystem: Lite-On Communications Inc Device [11ad:0802]
    Kernel driver in use: ath9k


lsusb ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Bus 001 Device 002: ID 8087:8000 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 002 Device 004: ID 0bda:0129 Realtek Semiconductor Corp. RTS5129 Card Reader Controller
Bus 002 Device 003: ID 04f2:b469 Chicony Electronics Co., Ltd 
Bus 002 Device 002: ID 04ca:300d Lite-On Technology Corp. 
Bus 002 Device 005: ID 1af3:0001  
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


PCMCIA Card Info ~~~~~~~~~~~~~~~~~~~



iwconfig ~~~~~~~~~~~~~~~~~~~~~~~~~~~

wlan0     IEEE 802.11abgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=16 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          


rfkill ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

      Interface                 Soft blocked  Hard blocked
0: hci0: Bluetooth                  yes           no
1: phy0: Wireless LAN               no            no
2: acer-wireless: Wireless LAN      no            no


lsmod ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

acer_wmi               32522  0 
sparse_keymap          13948  1 acer_wmi
ath9k                 164164  0 
ath9k_common           13551  1 ath9k
ath9k_hw              453856  2 ath9k_common,ath9k
ath                    28698  3 ath9k_common,ath9k,ath9k_hw
mac80211              630653  1 ath9k
cfg80211              484040  3 ath,ath9k,mac80211
wmi                    19177  1 acer_wmi
video                  19476  2 i915,acer_wmi


module parameters ~~~~~~~~~~~~~~~~~~

acer_wmi      (5): brightness=-1 | ec_raw_mode=N | force_series=0 | mailled=-1 | threeg=-1
ath9k         (5): blink=0 | bt_ant_diversity=0 | btcoex_enable=0 | nohwcrypt=0 | ps_enable=0
cfg80211      (2): cfg80211_disable_40mhz_24ghz=N | ieee80211_regdom=00
mac80211      (5): beacon_loss_count=7 | ieee80211_default_rc_algo=minstrel_ht | max_nullfunc_tries=2 | max_probe_tries=5 | probe_wait_ms=500
video         (3): allow_duplicates=N | brightness_switch_enabled=Y | use_native_backlight=-1
wmi           (2): debug_dump_wdg=N | debug_event=N


nm-tool ~~~~~~~~~~~~~~~~~~~~~~~~~~~~

State: connected (global)
============================o=============o=======  =o==============o=========o===========o===========  ===o===========
 Interface & ID             | Type        | Driver | State        | Default | Speed     | Support      | HW Addr   
============================o=============o=======  =o==============o=========o===========o===========  ===o===========
 wlan0                      | 802.11 WiFi | ath9k  | disconnected | no      |           | WEP/WPA/WPA2 | <MAC wlan0>
----------------------------+-------------+--------+--------------+---------+-----------+--------------+-----------
 eth0  [Wired connection 1] | Wired       | r8169  | connected    | yes     | 100 Mb/s  |              | <MAC eth0>

    Address:         192.168.0.107
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.0.254
    DNS:             192.168.0.254
----------------------------+-------------+--------+--------------+---------+-----------+--------------+-----------


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

HTC network          : ssid=HTC network | mac-address=<MAC wlan0> | ipv6=ignore | ipv4=auto 
Su_Wlan       : ssid=Su_Wlan | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 


interfaces ~~~~~~~~~~~~~~~~~~~~~~~~~

# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback

resolv.conf ~~~~~~~~~~~~~~~~~~~~~~~~

nameserver 127.0.1.1
search TeleWell.gateway


Routes & Ping ~~~~~~~~~~~~~~~~~~~~~~

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.0.254   0.0.0.0         UG    0      0        0 eth0
192.168.0.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0

--- 192.168.0.254 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 1001ms
rtt min/avg/max/mdev = 3.731/3.899/4.068/0.179 ms

--- 127.0.1.1 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 999ms
rtt min/avg/max/mdev = 0.032/0.041/0.050/0.009 ms


iw reg get ~~~~~~~~~~~~~~~~~~~~~~~~~

(Region : fi_FI.UTF-8)
country 00:
    (2402 - 2472 @ 40), (3, 20)
    (2457 - 2482 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (2474 - 2494 @ 20), (3, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
    (5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS


iwlist chan ~~~~~~~~~~~~~~~~~~~~~~~~

wlan0     32 channels in total; available frequencies :
          Channel 01 (2.412 GHz) - 13 (2.472 GHz)
          Channel 36 (5.18 GHz)
          Channel 40 (5.2 GHz)
          Channel 44 (5.22 GHz)
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
          Channel 120 (5.6 GHz)
          Channel 124 (5.62 GHz)
          Channel 128 (5.64 GHz)
          Channel 132 (5.66 GHz)
          Channel 136 (5.68 GHz)
          Channel 140 (5.7 GHz) - 13 (2.472 GHz)


iwlist scan ~~~~~~~~~~~~~~~~~~~~~~~~

wlan0     No scan results


blacklist ~~~~~~~~~~~~~~~~~~~~~~~~~~

[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci


modinfo ~~~~~~~~~~~~~~~~~~~~~~~~~~~~

[acer_wmi]
filename:       /lib/modules/3.13.0-39-generic/kernel/drivers/platform/x86/acer-wmi.ko
srcversion:     15371DC0E403E93954B38E5
depends:        wmi,sparse-keymap,video
parm:           mailled:Set initial state of Mail LED (int)
parm:           brightness:Set initial LCD backlight brightness (int)
parm:           threeg:Set initial state of 3G hardware (int)
parm:           force_series:Force a different laptop series (int)
parm:           ec_raw_mode:Enable EC raw mode (bool)

[ath9k]
filename:       /lib/modules/3.13.0-39-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k.ko
srcversion:     DF02272C2FA4678C49046E5
depends:        ath9k_hw,mac80211,ath9k_common,cfg80211,ath
parm:           debug:Debugging mask (uint)
parm:           nohwcrypt:Disable hardware encryption (int)
parm:           blink:Enable LED blink on activity (int)
parm:           btcoex_enable:Enable wifi-BT coexistence (int)
parm:           bt_ant_diversity:Enable WLAN/BT RX antenna diversity (int)
parm:           ps_enable:Enable WLAN PowerSave (int)

[ath9k_common]
filename:       /lib/modules/3.13.0-39-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_common.ko
srcversion:     696B00A6C59713EC0966997
depends:        ath,ath9k_hw

[ath9k_hw]
filename:       /lib/modules/3.13.0-39-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_hw.ko
srcversion:     4809F3842A0542CD6B556D3
depends:        ath

[ath]
filename:       /lib/modules/3.13.0-39-generic/kernel/drivers/net/wireless/ath/ath.ko
srcversion:     88A67C5359B02C5A710AFCF
depends:        cfg80211

[mac80211]
filename:       /lib/modules/3.13.0-39-generic/kernel/net/mac80211/mac80211.ko
srcversion:     B822641624778B987844F6F
depends:        cfg80211
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[cfg80211]
filename:       /lib/modules/3.13.0-39-generic/kernel/net/wireless/cfg80211.ko
srcversion:     C2478077E22138832B71659
depends:        
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

[wmi]
filename:       /lib/modules/3.13.0-39-generic/kernel/drivers/platform/x86/wmi.ko
srcversion:     CED5410F008DC70DF5F064B
depends:        
parm:           debug_event:Log WMI Events [0/1] (bool)
parm:           debug_dump_wdg:Dump available WMI interfaces [0/1] (bool)

[video]
filename:       /lib/modules/3.13.0-39-generic/kernel/drivers/acpi/video.ko
srcversion:     FBDB15F61F4F35FB6EE9AC8
depends:        
parm:           brightness_switch_enabled:bool
parm:           allow_duplicates:bool
parm:           use_native_backlight:int


udev rules ~~~~~~~~~~~~~~~~~~~~~~~~~

# PCI device 0x10ec:0x8168 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC eth0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

# PCI device 0x168c:0x0034 (ath9k)
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

BOOT_IMAGE=/boot/vmlinuz-3.13.0-39-generic.efi.signed root=UUID=d0af4c19-a959-46bf-ab07-4584e2ab70f2 ro quiet splash vt.handoff=7


dmesg ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

[    0.694863] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[    0.695211] audit: initializing netlink socket (disabled)
[    0.865288] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    9.150735] wmi: Mapper loaded
[    9.503332] ath: EEPROM regdomain: 0x6a
[    9.503332] ath: EEPROM indicates we should expect a direct regpair map
[    9.503334] ath: Country alpha2 being used: 00
[    9.503335] ath: Regpair used: 0x6a
[    9.628657] acer_wmi: Acer Laptop ACPI-WMI Extras
[    9.628747] acer_wmi: Function bitmap for Communication Button: 0x801
[    9.631166] acer_wmi: Brightness must be controlled by acpi video driver
[    9.643174] acer_wmi: Enabling Launch Manager failed: 0xe2 - 0x0
[   12.055961] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   13.383281] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  114.889935] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  144.443668] wlan0: authenticate with <MAC ID removed>
[  144.450859] wlan0: direct probe to <MAC ID removed> (try 1/3)
[  144.653686] wlan0: send auth to <MAC ID removed> (try 2/3)
[  145.866221] wlan0: send auth to <MAC ID removed> (try 3/3)
[  146.454356] wlan0: authentication with <MAC ID removed> timed out
[  149.992296] wlan0: authenticate with <MAC ID removed>
[  150.006112] wlan0: direct probe to <MAC ID removed> (try 1/3)
[  150.208085] wlan0: send auth to <MAC ID removed> (try 2/3)
[  150.868295] wlan0: send auth to <MAC ID removed> (try 3/3)
[  151.880797] wlan0: authentication with <MAC ID removed> timed out
[  156.235241] wlan0: authenticate with <MAC ID removed>
[  156.245912] wlan0: direct probe to <MAC ID removed> (try 1/3)
[  156.245955] wlan0: direct probe to <MAC ID removed> (try 2/3)
[  156.446716] wlan0: send auth to <MAC ID removed> (try 3/3)
[  157.883290] wlan0: authentication with <MAC ID removed> timed out
[  162.733903] wlan0: authenticate with <MAC ID removed>
[  162.745087] wlan0: direct probe to <MAC ID removed> (try 1/3)
[  162.745276] wlan0: direct probe to <MAC ID removed> (try 2/3)
[  162.949424] wlan0: send auth to <MAC ID removed> (try 3/3)
[  163.873766] wlan0: authentication with <MAC ID removed> timed out

    ======== Done ========

```

---

### Post by samuel21 on 2014-11-05
After adding nm-acer(?) to blacklist and ath9k conf setup it has been working well in my school. Now only problem is my home network. I just realized that i can connect to wifi if i am attached to lan when connecting. After the wifi is succesfully connected and i plug the ethernet cable it seems to be working well. So i am not sure what the problem is to initializing the connection , it just tries to connect for a while and then says "disconnected"... Any help with this additional information?

---

