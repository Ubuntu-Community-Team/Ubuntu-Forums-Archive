---
title: "connexion problem with xubuntu 14.04 after upgrade with rt2500pci driver"
date: 2015-03-06
forum: Networking &amp; Wireless
---

### Post by john374 on 2015-03-06
Hello
i'm John, and my english is very bad, i'm sorry for this.
i've  a problem since i have done an upgrade from xubuntu 12.10 to xubuntu 14.04. My wifi connexion is very slow and often jumped off. I have to clic on the wifi icon to reconnect. I'm not an expert in ubuntu and linux, and i've read many things about similar problems, but i can't find the solution. Does anyone can help me ?

i put informations about my computer. Thanks a lot !

```

    ======== Wireless-Info START ========

System-Info ~~~~~~~~~~~~~~~~~~~~~~~~

cottin-MS-7507 3.13.0-46-generic i686,  Ubuntu 14.04.2 LTS, trusty

CPU    : Intel(R) Celeron(R) CPU        E1200  @ 1.60GHz
Memory : 993 MB
Uptime : 19:27:44 up 19 min,  2 users,  load average: 0,06, 0,23, 0,31


lspci ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 01)
    Subsystem: Micro-Star International Co., Ltd. [MSI] Device [1462:507c]
    Kernel driver in use: r8169
--
03:01.0 Network controller [0280]: Ralink corp. RT2500 Wireless 802.11bg [1814:0201] (rev 01)
    Subsystem: Hercules Device [1681:0050]
    Kernel driver in use: rt2500pci


lsusb ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 0603:00f2 Novatek Microelectronics Corp. 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 1c4f:0003 SiGma Micro HID controller
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


PCMCIA Card Info ~~~~~~~~~~~~~~~~~~~



iwconfig ~~~~~~~~~~~~~~~~~~~~~~~~~~~

wlan0     IEEE 802.11bg  ESSID:"Freebox-5C8D49"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: <MAC C-01 Freebox-5C8D49>   
          Bit Rate=36 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=70/70  Signal level=-33 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:378  Invalid misc:180   Missed beacon:0



rfkill ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

      Interface        Soft blocked  Hard blocked
0: phy0: Wireless LAN      no            no


lsmod ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

rt2500pci              22723  0 
rt2x00pci              13111  1 rt2500pci
rt2x00mmio             13395  1 rt2500pci
rt2x00lib              48886  3 rt2x00pci,rt2500pci,rt2x00mmio
mac80211              546067  2 rt2x00lib,rt2x00pci
cfg80211              409394  2 mac80211,rt2x00lib
eeprom_93cx6           13168  1 rt2500pci


module parameters ~~~~~~~~~~~~~~~~~~

cfg80211      (2): cfg80211_disable_40mhz_24ghz=N | ieee80211_regdom=00
mac80211      (5): beacon_loss_count=7 | ieee80211_default_rc_algo=minstrel_ht | max_nullfunc_tries=2 | max_probe_tries=5 | probe_wait_ms=500


nm-tool ~~~~~~~~~~~~~~~~~~~~~~~~~~~~

State: connected (global)
===========================o=============o===========o=============o=========o===========o==============o===========
 Interface & ID            | Type        | Driver    | State       | Default | Speed     | Support      | HW Addr   
===========================o=============o===========o=============o=========o===========o==============o===========
 wlan0  [Freebox-5C8D49 1] | 802.11 WiFi | rt2500pci | connected   | yes     | 36 Mb/s   | WEP/WPA/WPA2 | <MAC wlan0>

    freebox_SB_DH:   Infra, <MAC C-04 freebox_SB_DH>, Freq 2462 MHz, Rate 54 Mb/s, Strength 34 WPA
    FreeWifi_secure: Infra, <MAC C-07 FreeWifi_secure>, Freq 2462 MHz, Rate 54 Mb/s, Strength 34 WPA Enterprise
    FreeWifi_secure: Infra, <MAC C-03 FreeWifi_secure>, Freq 2412 MHz, Rate 54 Mb/s, Strength 19 WPA2 Enterprise
    Livebox-d6ac:    Infra, <MAC C-NA Livebox-d6ac 1>, Freq 2412 MHz, Rate 54 Mb/s, Strength 19 WPA WPA2
    FreeWifi:        Infra, <MAC C-02 FreeWifi>, Freq 2412 MHz, Rate 54 Mb/s, Strength 100
    FreeWifi:        Infra, <MAC C-06 FreeWifi>, Freq 2462 MHz, Rate 54 Mb/s, Strength 34
    *Freebox-5C8D49: Infra, <MAC C-01 Freebox-5C8D49>, Freq 2412 MHz, Rate 54 Mb/s, Strength 81 WPA2
    orange:          Infra, <MAC C-NA orange 1>, Freq 2412 MHz, Rate 54 Mb/s, Strength 7

    Address:         192.168.1.23
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.254
    DNS:             192.168.1.254
---------------------------+-------------+-----------+-------------+---------+-----------+--------------+-----------
 eth0                      | Wired       | r8169     | unavailable | no      |           |              | <MAC eth0>
---------------------------+-------------+-----------+-------------+---------+-----------+--------------+-----------


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

Freebox-5C8D49       : ssid=Freebox-5C8D49 | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 
Freebox-5C8D49 1     : ssid=Freebox-5C8D49 | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 
Livebox-bbac         : ssid=Livebox-bbac | mac-address=<MAC wlan0> | ipv4=manual | ipv6=auto 


interfaces ~~~~~~~~~~~~~~~~~~~~~~~~~

auto lo
iface lo inet loopback


resolv.conf ~~~~~~~~~~~~~~~~~~~~~~~~

nameserver 127.0.1.1


Routes & Ping ~~~~~~~~~~~~~~~~~~~~~~

Table de routage IP du noyau
Destination     Passerelle      Genmask         Indic Metric Ref    Use Iface
0.0.0.0         192.168.1.254   0.0.0.0         UG    0      0        0 wlan0
192.168.1.0     0.0.0.0         255.255.255.0   U     9      0        0 wlan0

--- 192.168.1.254 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 1001ms
rtt min/avg/max/mdev = 14.038/35.390/56.743/21.353 ms

--- 127.0.1.1 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 999ms
rtt min/avg/max/mdev = 0.038/0.041/0.045/0.007 ms


iw reg get ~~~~~~~~~~~~~~~~~~~~~~~~~

(Region : fr_FR.UTF-8)
country 00:
    (2402 - 2472 @ 40), (3, 20)
    (2457 - 2482 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (2474 - 2494 @ 20), (3, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
    (5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS


iwlist chan ~~~~~~~~~~~~~~~~~~~~~~~~

wlan0     14 channels in total; available frequencies :
          Channel 01 (2.412 GHz) - 14 (2.484 GHz)

          Current Frequency=2.412 GHz (Channel 1)


iwlist scan ~~~~~~~~~~~~~~~~~~~~~~~~

wlan0     Scan completed :
          Cell 01 - Address: <MAC C-01 Freebox-5C8D49>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=70/70  Signal level=-39 dBm  
                    Encryption key:on
                    ESSID:"Freebox-5C8D49"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 22 Mb/s
                              6 Mb/s; 9 Mb/s; 12 Mb/s
                    Bit Rates:18 Mb/s; 24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000055852059d16
                    Extra: Last beacon: 40ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC C-02 FreeWifi>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=70/70  Signal level=-39 dBm  
                    Encryption key:off
                    ESSID:"FreeWifi"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 22 Mb/s
                              6 Mb/s; 9 Mb/s; 12 Mb/s
                    Bit Rates:18 Mb/s; 24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000055851d7c019
                    Extra: Last beacon: 40ms ago
          Cell 03 - Address: <MAC C-03 FreeWifi_secure>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=70/70  Signal level=-33 dBm  
                    Encryption key:on
                    ESSID:"FreeWifi_secure"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 22 Mb/s
                              6 Mb/s; 9 Mb/s; 12 Mb/s
                    Bit Rates:18 Mb/s; 24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000055851d7473f
                    Extra: Last beacon: 40ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : 802.1x
          Cell 04 - Address: <MAC C-04 freebox_SB_DH>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=31/70  Signal level=-79 dBm  
                    Encryption key:on
                    ESSID:"freebox_SB_DH"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000015f12b8499a
                    Extra: Last beacon: 40ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
          Cell 05 - Address: <MAC C-05 >
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=32/70  Signal level=-78 dBm  
                    Encryption key:on
                    ESSID:""
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000015f12b82b18
                    Extra: Last beacon: 1184ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 06 - Address: <MAC C-06 FreeWifi>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=32/70  Signal level=-78 dBm  
                    Encryption key:off
                    ESSID:"FreeWifi"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000015f12b8545f
                    Extra: Last beacon: 40ms ago
          Cell 07 - Address: <MAC C-07 FreeWifi_secure>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=31/70  Signal level=-79 dBm  
                    Encryption key:on
                    ESSID:"FreeWifi_secure"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000015f12b85dd4
                    Extra: Last beacon: 40ms ago
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x


blacklist ~~~~~~~~~~~~~~~~~~~~~~~~~~

[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci

[/etc/modprobe.d/rt2500pci.conf]
blacklist rt2500pci


modinfo ~~~~~~~~~~~~~~~~~~~~~~~~~~~~

[rt2500pci]
filename:       /lib/modules/3.13.0-46-generic/kernel/drivers/net/wireless/rt2x00/rt2500pci.ko
version:        2.3.0
srcversion:     9139759CB5805AC8220A8D0
depends:        rt2x00lib,rt2x00mmio,rt2x00pci,eeprom_93cx6

[rt2x00pci]
filename:       /lib/modules/3.13.0-46-generic/kernel/drivers/net/wireless/rt2x00/rt2x00pci.ko
version:        2.3.0
srcversion:     1B9A9CB4CAAB78DFE7974EA
depends:        rt2x00lib,mac80211

[rt2x00mmio]
filename:       /lib/modules/3.13.0-46-generic/kernel/drivers/net/wireless/rt2x00/rt2x00mmio.ko
version:        2.3.0
srcversion:     37A76810C0FE9E4E11476DA
depends:        rt2x00lib

[rt2x00lib]
filename:       /lib/modules/3.13.0-46-generic/kernel/drivers/net/wireless/rt2x00/rt2x00lib.ko
version:        2.3.0
srcversion:     09822BD19555F112E3902D4
depends:        mac80211,cfg80211

[mac80211]
filename:       /lib/modules/3.13.0-46-generic/kernel/net/mac80211/mac80211.ko
srcversion:     B8DF1ECC076C2FCEAC70533
depends:        cfg80211
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[cfg80211]
filename:       /lib/modules/3.13.0-46-generic/kernel/net/wireless/cfg80211.ko
srcversion:     5C139B156678DB83EDA757D
depends:        
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

[eeprom_93cx6]
filename:       /lib/modules/3.13.0-46-generic/kernel/drivers/misc/eeprom/eeprom_93cx6.ko
version:        1.0
srcversion:     215D8C1284A3C33B4A5A1C5
depends:        


udev rules ~~~~~~~~~~~~~~~~~~~~~~~~~

# PCI device 0x10ec:/sys/devices/pci0000:00/0000:00:1c.1/0000:02:00.0 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC eth0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

# PCI device 0x1814:/sys/devices/pci0000:00/0000:00:1e.0/0000:03:01.0 (rt2500pci)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC wlan0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"


Custom files/entries ~~~~~~~~~~~~~~~

/etc/modules        : Default
/etc/rc.local       : Default
/etc/modprobe.d     : Not Default
/etc/pm/(cnf|pw|sl) : Default

[/etc/modprobe.d]
iwlmvm.conf       : options iwlmvm power_scheme=1
iwlwifi.conf      : options iwlwifi bt_coex_active=N swcrypto=1 11n_disable=1
mlx4.conf         : softdep mlx4_core post: mlx4_en


Kernel boot line ~~~~~~~~~~~~~~~~~~~

BOOT_IMAGE=/boot/vmlinuz-3.13.0-46-generic root=UUID=d1c4ad95-95d3-43ec-bc9e-189855c9d36e ro quiet splash vt.handoff=7


dmesg ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

[    0.705645] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[    0.706145] audit: initializing netlink socket (disabled)
[    1.278990] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[   18.087498] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   72.325884] ieee80211 phy0: rt2x00_set_chip: Info - Chipset detected - rt: 2560, rf: 0003, rev: 0004
[   72.365107] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   72.370593] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   74.596653] wlan0: authenticate with <MAC C-01 Freebox-5C8D49>
[   74.605222] wlan0: send auth to <MAC C-01 Freebox-5C8D49> (try 1/3)
[   74.607375] wlan0: authenticated
[   74.608115] wlan0: associate with <MAC C-01 Freebox-5C8D49> (try 1/3)
[   74.612608] wlan0: RX AssocResp from <MAC C-01 Freebox-5C8D49> (capab=0x411 status=0 aid=1)
[   74.612915] wlan0: associated
[   74.612959] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   74.651393] wlan0: deauthenticating from <MAC C-01 Freebox-5C8D49> by local choice (reason=2)
[   74.664766] wlan0: authenticate with <MAC C-01 Freebox-5C8D49>
[   74.665202] wlan0: send auth to <MAC C-01 Freebox-5C8D49> (try 1/3)
[   74.667652] wlan0: authenticated
[   74.672357] wlan0: associate with <MAC C-01 Freebox-5C8D49> (try 1/3)
[   74.676984] wlan0: RX AssocResp from <MAC C-01 Freebox-5C8D49> (capab=0x411 status=0 aid=1)
[   74.677287] wlan0: associated
[   96.488062] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[   96.968055] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[   97.448237] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[   97.992038] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[   98.456045] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[   98.984037] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[  100.172036] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[  100.688034] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[  139.452194] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[  139.932037] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[  140.460064] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[  140.972051] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[  141.516054] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[  141.996035] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[  142.476040] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[  142.972045] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[  143.452041] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[  143.932070] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[  144.428060] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[  144.960057] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[  145.492049] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[  202.452050] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[  203.652087] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[  204.564083] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[  205.400033] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[  205.932038] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[  298.320038] ieee80211 phy0: wlan0: No probe response from AP <MAC C-01 Freebox-5C8D49> after 500ms, disconnecting.
[  299.520761] wlan0: authenticate with <MAC C-01 Freebox-5C8D49>
[  299.529243] wlan0: send auth to <MAC C-01 Freebox-5C8D49> (try 1/3)
[  299.732078] wlan0: send auth to <MAC C-01 Freebox-5C8D49> (try 2/3)
[  299.936074] wlan0: send auth to <MAC C-01 Freebox-5C8D49> (try 3/3)
[  300.140027] wlan0: authentication with <MAC C-01 Freebox-5C8D49> timed out
[  314.267082] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  321.720527] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  323.934416] wlan0: authenticate with <MAC C-01 Freebox-5C8D49>
[  323.941243] wlan0: send auth to <MAC C-01 Freebox-5C8D49> (try 1/3)
[  323.943178] wlan0: authenticated
[  323.944063] wlan0: associate with <MAC C-01 Freebox-5C8D49> (try 1/3)
[  323.948035] wlan0: RX AssocResp from <MAC C-01 Freebox-5C8D49> (capab=0x411 status=0 aid=1)
[  323.948351] wlan0: associated
[  323.948409] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  345.384065] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[  345.864058] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[  346.344082] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[  346.856052] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[  347.368067] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[  347.880039] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[  348.392035] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[  348.920064] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[  349.432045] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[  351.152044] ieee80211 phy0: rt2500pci_set_device_state: Error - Device failed to enter state 1 (-16)
[  351.816050] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[  352.360035] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[  352.940068] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[  353.488066] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[  388.828051] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[  389.308038] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[  389.852041] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[  390.316047] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[  390.784047] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[  391.280058] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[  391.776049] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[  392.272032] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[  392.752059] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[  393.300051] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[  395.056043] ieee80211 phy0: rt2500pci_set_device_state: Error - Device failed to enter state 1 (-16)
[  451.460026] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[  452.660036] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[  453.188024] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[  454.036024] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[  454.908024] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[  520.504050] ieee80211 phy0: wlan0: No probe response from AP <MAC C-01 Freebox-5C8D49> after 500ms, disconnecting.
[  521.696748] wlan0: authenticate with <MAC C-01 Freebox-5C8D49>
[  521.705220] wlan0: send auth to <MAC C-01 Freebox-5C8D49> (try 1/3)
[  521.908040] wlan0: send auth to <MAC C-01 Freebox-5C8D49> (try 2/3)
[  522.112079] wlan0: send auth to <MAC C-01 Freebox-5C8D49> (try 3/3)
[  522.316028] wlan0: authentication with <MAC C-01 Freebox-5C8D49> timed out
[  536.301408] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  552.700522] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  553.862135] wlan0: authenticate with <MAC C-01 Freebox-5C8D49>
[  553.862575] wlan0: send auth to <MAC C-01 Freebox-5C8D49> (try 1/3)
[  553.864367] wlan0: authenticated
[  553.868062] wlan0: associate with <MAC C-01 Freebox-5C8D49> (try 1/3)
[  553.874879] wlan0: RX AssocResp from <MAC C-01 Freebox-5C8D49> (capab=0x411 status=0 aid=1)
[  553.875189] wlan0: associated
[  553.875243] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  576.464035] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[  576.992047] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[  577.888024] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[  578.784026] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[  621.640052] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[  682.832025] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[  766.488058] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[  768.044085] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[  768.560032] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[  868.820036] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[  869.364027] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[  869.844040] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[  870.308040] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[  871.220032] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[  872.108026] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[  937.860038] ieee80211 phy0: rt2500pci_set_device_state: Error - Device failed to enter state 1 (-16)

    ======== Done ========


```

---

