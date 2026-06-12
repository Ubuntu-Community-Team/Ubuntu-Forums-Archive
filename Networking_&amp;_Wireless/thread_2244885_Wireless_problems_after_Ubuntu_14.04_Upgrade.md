---
title: "Wireless problems after Ubuntu 14.04 Upgrade"
date: 2014-09-19
forum: Networking &amp; Wireless
---

### Post by rade2 on 2014-09-19
After upgrading to Ubuntu 14.04 I can no longer access internet via Wireless. I am able to establish connection to the network but can't load any pages. Using ethernet cable however works. Here is the info:
```

    ======== Wireless-Info START ========

System-Info ~~~~~~~~~~~~~~~~~~~~~~~~

mrpotson-MS-16Y1 3.13.0-35-generic x86_64,  Ubuntu 14.04.1 LTS, trusty

CPU    : Intel(R) Core(TM) i3-2310M CPU @ 2.10GHz
Memory : 3863 MB
Uptime : 15:18:10 up 5 min,  2 users,  load average: 1.21, 0.82, 0.40


lspci ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

03:00.0 Network controller [0280]: Qualcomm Atheros AR9285 Wireless Network Adapter (PCI-Express) [168c:002b] (rev 01)
    Subsystem: XAVi Technologies Corp. XW204E 802.11bgn Wireless Half-size Mini PCIe Card [1b9a:0401]
    Kernel driver in use: ath9k
--
05:00.0 Ethernet controller [0200]: Qualcomm Atheros AR8151 v2.0 Gigabit Ethernet [1969:1083] (rev c0)
    Subsystem: Micro-Star International Co., Ltd. [MSI] Device [1462:109c]
    Kernel driver in use: atl1c


lsusb ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 002: ID 0603:0002 Novatek Microelectronics Corp. 
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 05c8:030d Cheng Uei Precision Industry Co., Ltd (Foxlink) 
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


PCMCIA Card Info ~~~~~~~~~~~~~~~~~~~



iwconfig ~~~~~~~~~~~~~~~~~~~~~~~~~~~

wlan0     IEEE 802.11bgn  ESSID:"AirforceOne"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: <MAC C-01 AirforceOne>   
          Bit Rate=24 Mb/s   Tx-Power=15 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=70/70  Signal level=-32 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:2  Invalid misc:82   Missed beacon:0



rfkill ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

      Interface        Soft blocked  Hard blocked
0: phy0: Wireless LAN      no            no


lsmod ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

ath9k                 100324  0 
ath9k_common           13550  1 ath9k
ath9k_hw              424499  2 ath9k_common,ath9k
ath                    29006  3 ath9k_common,ath9k,ath9k_hw
mac80211              540025  1 ath9k
cfg80211              493923  3 ath,ath9k,mac80211
mxm_wmi                13021  0 
compat                 13849  4 cfg80211,ath9k_common,ath9k,mac80211
wmi                    19177  1 mxm_wmi


module parameters ~~~~~~~~~~~~~~~~~~

ath9k         (5): blink=0 | bt_ant_diversity=0 | btcoex_enable=0 | nohwcrypt=1 | ps_enable=0
cfg80211      (2): cfg80211_disable_40mhz_24ghz=N | ieee80211_regdom=00
compat        (3): 
mac80211      (5): beacon_loss_count=7 | ieee80211_default_rc_algo=minstrel_ht | max_nullfunc_tries=2 | max_probe_tries=5 | probe_wait_ms=500
wmi           (2): debug_dump_wdg=N | debug_event=N


nm-tool ~~~~~~~~~~~~~~~~~~~~~~~~~~~~

State: connected (global)
=======================o=============o========o===========o=========o===========o==============o===========
 Interface & ID        | Type        | Driver | State     | Default | Speed     | Support      | HW Addr   
=======================o=============o========o===========o=========o===========o==============o===========
 eth0  [Auto Ethernet] | Wired       | atl1c  | connected | yes     | 100 Mb/s  |              | <MAC eth0>

    Address:         46.40.18.205
    Prefix:          21 (255.255.248.0)
    Gateway:         46.40.23.254
    DNS:             81.24.247.61
    DNS:             91.102.231.242
-----------------------+-------------+--------+-----------+---------+-----------+--------------+-----------
 wlan0  [AirforceOne]  | 802.11 WiFi | ath9k  | connected | no      | 24 Mb/s   | WEP/WPA/WPA2 | <MAC wlan0>

    *AirforceOne:    Infra, <MAC C-01 AirforceOne>, Freq 2412 MHz, Rate 54 Mb/s, Strength 88 WPA WPA2

    Address:         192.168.1.102
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1
    DNS:             192.168.1.1
-----------------------+-------------+--------+-----------+---------+-----------+--------------+-----------


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

AirforceOne          : ssid=AirforceOne | bssid=<MAC C-01 AirforceOne> | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 
airlive              : ssid=airlive | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 
AndroidAP            : ssid=AndroidAP | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 
qwerty               : ssid=qwerty | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 
WiPlus               : ssid=WiPlus | mac-address=<MAC wlan0> | ipv6=auto | ipv4=auto 


interfaces ~~~~~~~~~~~~~~~~~~~~~~~~~

auto lo
iface lo inet loopback


resolv.conf ~~~~~~~~~~~~~~~~~~~~~~~~

nameserver 127.0.1.1


Routes & Ping ~~~~~~~~~~~~~~~~~~~~~~

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         46.40.23.254    0.0.0.0         UG    0      0        0 eth0
46.40.16.0      0.0.0.0         255.255.248.0   U     1      0        0 eth0
192.168.1.0     0.0.0.0         255.255.255.0   U     9      0        0 wlan0

--- 46.40.23.254 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 1001ms
rtt min/avg/max/mdev = 8.029/25.832/43.635/17.803 ms

--- 127.0.1.1 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 999ms
rtt min/avg/max/mdev = 0.045/0.053/0.061/0.008 ms


iw reg get ~~~~~~~~~~~~~~~~~~~~~~~~~

(Region : "en_US.UTF-8")
country 00:
    (2402 - 2472 @ 40), (3, 20)
    (2457 - 2482 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (2474 - 2494 @ 20), (3, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
    (5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS


iwlist chan ~~~~~~~~~~~~~~~~~~~~~~~~

wlan0     14 channels in total; available frequencies :
          Channel 01 (2.412 GHz) - 14 (2.484 GHz)

          Current Frequency:2.412 GHz (Channel 1)


iwlist scan ~~~~~~~~~~~~~~~~~~~~~~~~

wlan0     Scan completed :
          Cell 01 - Address: <MAC C-01 AirforceOne>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=70/70  Signal level=-37 dBm  
                    Encryption key:on
                    ESSID:"AirforceOne"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s
                    Bit Rates:9 Mb/s; 18 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000000e8ecb68
                    Extra: Last beacon: 68ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                       Preauthentication Supported
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK


blacklist ~~~~~~~~~~~~~~~~~~~~~~~~~~

[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci


modinfo ~~~~~~~~~~~~~~~~~~~~~~~~~~~~

[ath9k]
filename:       /lib/modules/3.13.0-35-generic/updates/drivers/net/wireless/ath/ath9k/ath9k.ko
version:        backported from Linux (v3.14-0-g455c6fd) using backports v3.14-1-0-g369d49a
srcversion:     F7DDA521CEAEE5DEF62FC70
depends:        ath9k_hw,mac80211,ath9k_common,compat,cfg80211,ath
parm:           debug:Debugging mask (uint)
parm:           nohwcrypt:Disable hardware encryption (int)
parm:           blink:Enable LED blink on activity (int)
parm:           btcoex_enable:Enable wifi-BT coexistence (int)
parm:           bt_ant_diversity:Enable WLAN/BT RX antenna diversity (int)
parm:           ps_enable:Enable WLAN PowerSave (int)

[ath9k_common]
filename:       /lib/modules/3.13.0-35-generic/updates/drivers/net/wireless/ath/ath9k/ath9k_common.ko
version:        backported from Linux (v3.14-0-g455c6fd) using backports v3.14-1-0-g369d49a
srcversion:     4495C58DC0B9E6476467D04
depends:        compat,ath,ath9k_hw

[ath9k_hw]
filename:       /lib/modules/3.13.0-35-generic/updates/drivers/net/wireless/ath/ath9k/ath9k_hw.ko
srcversion:     F9FF70E90C75F9983425CE9
depends:        ath

[ath]
filename:       /lib/modules/3.13.0-35-generic/updates/drivers/net/wireless/ath/ath.ko
srcversion:     FC2763E34FD681F8F393032
depends:        cfg80211

[mac80211]
filename:       /lib/modules/3.13.0-35-generic/updates/net/mac80211/mac80211.ko
version:        backported from Linux (v3.14-0-g455c6fd) using backports v3.14-1-0-g369d49a
srcversion:     756C8FBA12B1BEB7E161820
depends:        cfg80211,compat
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[cfg80211]
filename:       /lib/modules/3.13.0-35-generic/updates/net/wireless/cfg80211.ko
version:        backported from Linux (v3.14-0-g455c6fd) using backports v3.14-1-0-g369d49a
srcversion:     F7B2F7E7671DF62D4084360
depends:        compat
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

[mxm_wmi]
filename:       /lib/modules/3.13.0-35-generic/kernel/drivers/platform/x86/mxm-wmi.ko
srcversion:     62CBD37DE87DF0C4CD7FBA3
depends:        wmi

[compat]
filename:       /lib/modules/3.13.0-35-generic/updates/compat/compat.ko
version:        backported from Linux (v3.14-0-g455c6fd) using backports v3.14-1-0-g369d49a
srcversion:     7D59133EBA3FA7BD54139E3
depends:        
parm:           backported_kernel_name:The kernel tree name that was used for this backport (Linux) (charp)
parm:           backported_kernel_version:The kernel version that was used for this backport (v3.14-0-g455c6fd) (charp)
parm:           backports_version:The git version of the backports tree used to generate this backport (v3.14-1-0-g369d49a) (charp)

[wmi]
filename:       /lib/modules/3.13.0-35-generic/kernel/drivers/platform/x86/wmi.ko
srcversion:     CED5410F008DC70DF5F064B
depends:        
parm:           debug_event:Log WMI Events [0/1] (bool)
parm:           debug_dump_wdg:Dump available WMI interfaces [0/1] (bool)


udev rules ~~~~~~~~~~~~~~~~~~~~~~~~~

# PCI device 0x1969:/sys/devices/pci0000:00/0000:00:1c.5/0000:05:00.0 (atl1c)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC eth0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

# PCI device 0x168c:/sys/devices/pci0000:00/0000:00:1c.1/0000:03:00.0 (ath9k)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC wlan0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"


Custom files/entries ~~~~~~~~~~~~~~~

/etc/modules        : Default
/etc/rc.local       : Default
/etc/modprobe.d     : Not Default
/etc/pm/(cnf|pw|sl) : Default

[/etc/modprobe.d]
ath9k.conf        : options ath9k nohwcrypt=1
iwlwifi.conf      : remove iwlwifi \
                    (/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
                    && /sbin/modprobe -r mac80211
mlx4.conf         : softdep mlx4_core post: mlx4_en


Kernel boot line ~~~~~~~~~~~~~~~~~~~

BOOT_IMAGE=/boot/vmlinuz-3.13.0-35-generic root=UUID=107238b8-8c8e-4ac7-8b60-b0b7c78130a8 ro radeon.audio=1 quiet splash vt.handoff=7


dmesg ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

[    0.619063] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[    0.619464] audit: initializing netlink socket (disabled)
[   18.129913] wmi: Mapper loaded
[   19.350790] ath: phy0: Enable LNA combining
[   19.353412] ath: phy0: ASPM enabled: 0x43
[   19.353415] ath: EEPROM regdomain: 0x60
[   19.353416] ath: EEPROM indicates we should expect a direct regpair map
[   19.353418] ath: Country alpha2 being used: 00
[   19.353419] ath: Regpair used: 0x60
[   22.486796] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   25.415848] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   25.418710] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   28.471855] wlan0: authenticate with <MAC C-01 AirforceOne>
[   28.482122] wlan0: send auth to <MAC C-01 AirforceOne> (try 1/3)
[   28.485481] wlan0: authenticated
[   28.485634] ath9k 0000:03:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[   28.485640] ath9k 0000:03:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[   28.486220] wlan0: associate with <MAC C-01 AirforceOne> (try 1/3)
[   28.490525] wlan0: RX AssocResp from <MAC C-01 AirforceOne> (capab=0x431 status=0 aid=3)
[   28.490627] wlan0: associated
[   28.490646] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   80.556052] wlan0: deauthenticating from <MAC C-01 AirforceOne> by local choice (reason=3)
[   98.094259] wlan0: authenticate with <MAC C-01 AirforceOne>
[   98.100888] wlan0: send auth to <MAC C-01 AirforceOne> (try 1/3)
[   98.102657] wlan0: authenticated
[   98.102932] ath9k 0000:03:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[   98.102940] ath9k 0000:03:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[   98.105306] wlan0: associate with <MAC C-01 AirforceOne> (try 1/3)
[   98.107893] wlan0: RX AssocResp from <MAC C-01 AirforceOne> (capab=0x431 status=0 aid=2)
[   98.108022] wlan0: associated

    ======== Done ========
```

---

### Post by praseodym on 2014-09-19
Change to pure WPA2-AES (CCMCP) encryption. Check the router manual

---

