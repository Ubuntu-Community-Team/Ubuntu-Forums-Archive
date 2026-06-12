---
title: "HP / Ralink / Realtek WiFi problem, but with a fun new twist!"
date: 2014-07-16
forum: Networking &amp; Wireless
---

### Post by manifestDensity on 2014-07-16
The specifics:  I'm running on an HP Pavilion G6.  The problem first appeared as I was running 13.10, so I updated to 14.04 in the hope that the new kernel would fix the problem.  This was not to be.  So the basics.  System cannot maintain a wireless connection.  It connects for maybe 90 seconds and then drops the connection.  If it helps, I have noted that when the connection is dropped the wifi network itself disappears from the list.  The only way to address the issue is to disable wifi, wait a few seconds, and then re-enable wifi.  It will immediately find the original network and connect without a problem.  For about 90 seconds and then, well.. you get the idea.  I have run "the script" and will display the results below.  It should be noted that I attempted to right this problem by downloading and installing the backport drivers.  This was not to be.  I had no problem with the defconfig and the make, but the make install kept coming up with ERROR 2, whatever that means.   So if that's where this ultimately points we need to address that issue as well.  Anyway, the results of "the script':

```


    ======== Wireless-Info START ========


System-Info ~~~~~~~~~~~~~~~~~~~~~~~~


Boudicca 3.13.0-32-generic x86_64,  Ubuntu 14.04 LTS, trusty


CPU    : AMD A4-4300M APU with Radeon(tm) HD Graphics
Memory : 5371 MB
Uptime : 21:30:14 up  1:01,  2 users,  load average: 0.61, 0.46, 0.42




lspci ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~


02:00.0 Network controller [0280]: Ralink corp. RT3290 Wireless 802.11n 1T/1R PCIe [1814:3290]
    Subsystem: Hewlett-Packard Company Ralink RT3290LE 802.11bgn 1x1 Wi-Fi and Bluetooth 4.0 Combo Adapter [103c:18ec]
    Kernel driver in use: rt2800pci
--
05:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 05)
    Subsystem: Hewlett-Packard Company Device [103c:1849]
    Kernel driver in use: r8169




lsusb ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~


Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 1bcf:2c1e Sunplus Innovation Technology Inc. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 008 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 007 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 005 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub




PCMCIA Card Info ~~~~~~~~~~~~~~~~~~~






iwconfig ~~~~~~~~~~~~~~~~~~~~~~~~~~~


wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          




rfkill ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~


      Interface        Soft blocked  Hard blocked
0: phy0: Wireless LAN      no            no




lsmod ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~


hp_wmi                 14062  0 
sparse_keymap          13948  1 hp_wmi
rt2800pci              13606  0 
rt2800mmio             20986  1 rt2800pci
rt2800lib              89076  2 rt2800pci,rt2800mmio
rt2x00pci              13287  1 rt2800pci
rt2x00mmio             13603  2 rt2800pci,rt2800mmio
rt2x00lib              55307  5 rt2x00pci,rt2800lib,rt2800pci,rt2800mmio,rt2x00mmio
mac80211              630653  3 rt2x00lib,rt2x00pci,rt2800lib
cfg80211              484040  2 mac80211,rt2x00lib
eeprom_93cx6           13344  1 rt2800pci
crc_ccitt              12707  1 rt2800lib
wmi                    19177  1 hp_wmi




module parameters ~~~~~~~~~~~~~~~~~~


cfg80211      (2): cfg80211_disable_40mhz_24ghz=N | ieee80211_regdom=00
mac80211      (5): beacon_loss_count=7 | ieee80211_default_rc_algo=minstrel_ht | max_nullfunc_tries=2 | max_probe_tries=5 | probe_wait_ms=500
rt2800pci     (1): nohwcrypt=N
wmi           (2): debug_dump_wdg=N | debug_event=N




nm-tool ~~~~~~~~~~~~~~~~~~~~~~~~~~~~


State: connected (global)
============================o=============o===========o==============o=========o===========o==============o===========
 Interface & ID             | Type        | Driver    | State        | Default | Speed     | Support      | HW Addr   
============================o=============o===========o==============o=========o===========o==============o===========
 eth0  [Wired connection 1] | Wired       | r8169     | connected    | yes     | 100 Mb/s  |              | <MAC eth0>


    Address:         192.168.0.18
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.0.1
    DNS:             192.168.0.1
----------------------------+-------------+-----------+--------------+---------+-----------+--------------+-----------
 wlan0                      | 802.11 WiFi | rt2800pci | disconnected | no      |           | WEP/WPA/WPA2 | <MAC wlan0>


    BELL748:         Infra, <MAC C-04 BELL748>, Freq 2412 MHz, Rate 54 Mb/s, Strength 65 WPA2
    TheRouter:       Infra, <MAC C-05 TheRouter>, Freq 2462 MHz, Rate 54 Mb/s, Strength 27 WPA WPA2
    BELL754:         Infra, <MAC C-02 BELL754>, Freq 2437 MHz, Rate 54 Mb/s, Strength 30 WPA2
    FreeWiFi:        Infra, <MAC C-01 FreeWiFi>, Freq 2462 MHz, Rate 54 Mb/s, Strength 82 WPA WPA2
    Bambajops:       Infra, <MAC C-03 Bambajops>, Freq 2412 MHz, Rate 54 Mb/s, Strength 17 WPA2
----------------------------+-------------+-----------+--------------+---------+-----------+--------------+-----------




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


BELL748              : ssid=BELL748 | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 
BELL754              : ssid=BELL754 | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 
FreeWiFi             : ssid=FreeWiFi | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 




interfaces ~~~~~~~~~~~~~~~~~~~~~~~~~


# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback


resolv.conf ~~~~~~~~~~~~~~~~~~~~~~~~


nameserver 127.0.1.1
search vlan1.phub.net.cable.rogers.com




Routes & Ping ~~~~~~~~~~~~~~~~~~~~~~


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.0.1     0.0.0.0         UG    0      0        0 eth0
192.168.0.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0


--- 192.168.0.1 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 1001ms
rtt min/avg/max/mdev = 0.899/0.952/1.005/0.053 ms


--- 127.0.1.1 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 999ms
rtt min/avg/max/mdev = 0.040/0.044/0.049/0.008 ms




iw reg get ~~~~~~~~~~~~~~~~~~~~~~~~~


(Region : "en_CA.UTF-8")
country 00:
    (2402 - 2472 @ 40), (3, 20)
    (2457 - 2482 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (2474 - 2494 @ 20), (3, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
    (5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS




iwlist chan ~~~~~~~~~~~~~~~~~~~~~~~~


wlan0     14 channels in total; available frequencies :
          Channel 01 (2.412 GHz) - 14 (2.484 GHz)




iwlist scan ~~~~~~~~~~~~~~~~~~~~~~~~


wlan0     Scan completed :
          Cell 01 - Address: <MAC C-01 FreeWiFi>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=61/70  Signal level=-49 dBm  
                    Encryption key:on
                    ESSID:"FreeWiFi"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000b5b2abaec
                    Extra: Last beacon: 364ms ago
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC C-02 BELL754>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=34/70  Signal level=-76 dBm  
                    Encryption key:on
                    ESSID:"BELL754"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000031b36175e
                    Extra: Last beacon: 688ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: <MAC C-03 Bambajops>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=42/70  Signal level=-68 dBm  
                    Encryption key:on
                    ESSID:"Bambajops"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000001d0ae64
                    Extra: Last beacon: 1004ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 04 - Address: <MAC C-04 BELL748>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=40/70  Signal level=-70 dBm  
                    Encryption key:on
                    ESSID:"BELL748"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000008fad930fc
                    Extra: Last beacon: 1004ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 05 - Address: <MAC C-05 TheRouter>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=46/70  Signal level=-64 dBm  
                    Encryption key:on
                    ESSID:"TheRouter"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000b5d51e151
                    Extra: Last beacon: 368ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK




blacklist ~~~~~~~~~~~~~~~~~~~~~~~~~~


[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci




modinfo ~~~~~~~~~~~~~~~~~~~~~~~~~~~~


[rt2800pci]
filename:       /lib/modules/3.13.0-32-generic/kernel/drivers/net/wireless/rt2x00/rt2800pci.ko
firmware:       rt2860.bin
version:        2.3.0
srcversion:     D876F002AA85529257D61EB
depends:        rt2x00lib,rt2800lib,rt2800mmio,rt2x00mmio,rt2x00pci,eeprom_93cx6
parm:           nohwcrypt:Disable hardware encryption. (bool)


[rt2800mmio]
filename:       /lib/modules/3.13.0-32-generic/kernel/drivers/net/wireless/rt2x00/rt2800mmio.ko
version:        2.3.0
srcversion:     F196893F5F72140CA847345
depends:        rt2800lib,rt2x00lib,rt2x00mmio


[rt2800lib]
filename:       /lib/modules/3.13.0-32-generic/kernel/drivers/net/wireless/rt2x00/rt2800lib.ko
version:        2.3.0
srcversion:     9BD0087B6943A41E7FD8EDA
depends:        rt2x00lib,mac80211,crc-ccitt


[rt2x00pci]
filename:       /lib/modules/3.13.0-32-generic/kernel/drivers/net/wireless/rt2x00/rt2x00pci.ko
version:        2.3.0
srcversion:     9B9D0D0D0F8571AF43705FD
depends:        rt2x00lib,mac80211


[rt2x00mmio]
filename:       /lib/modules/3.13.0-32-generic/kernel/drivers/net/wireless/rt2x00/rt2x00mmio.ko
version:        2.3.0
srcversion:     07530604F5CE4EF69872C75
depends:        rt2x00lib


[rt2x00lib]
filename:       /lib/modules/3.13.0-32-generic/kernel/drivers/net/wireless/rt2x00/rt2x00lib.ko
version:        2.3.0
srcversion:     CC69EE39E7D673974A21C0A
depends:        mac80211,cfg80211


[mac80211]
filename:       /lib/modules/3.13.0-32-generic/kernel/net/mac80211/mac80211.ko
srcversion:     8ADA881D348148A3358334C
depends:        cfg80211
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)


[cfg80211]
filename:       /lib/modules/3.13.0-32-generic/kernel/net/wireless/cfg80211.ko
srcversion:     E786D076B61F97809B04B64
depends:        
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)


[eeprom_93cx6]
filename:       /lib/modules/3.13.0-32-generic/kernel/drivers/misc/eeprom/eeprom_93cx6.ko
version:        1.0
srcversion:     215D8C1284A3C33B4A5A1C5
depends:        


[crc_ccitt]
filename:       /lib/modules/3.13.0-32-generic/kernel/lib/crc-ccitt.ko
srcversion:     2294FCAD06D727386004EEB
depends:        




udev rules ~~~~~~~~~~~~~~~~~~~~~~~~~


# PCI device 0x10ec:0x8136 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC eth0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"


# PCI device 0x1814:0x3290 (rt2800pci)
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


BOOT_IMAGE=/boot/vmlinuz-3.13.0-32-generic.efi.signed root=UUID=4f444891-8c93-46df-a5d0-d9e4e64ac20f ro quiet splash vt.handoff=7




dmesg ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~


[    5.169347] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[    5.169726] audit: initializing netlink socket (disabled)
[    5.858474] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[   17.059671] wmi: Mapper loaded
[   18.117073] ieee80211 phy0: rt2x00_set_rt: Info - RT chipset 3290, rev 0015 detected
[   18.120479] ieee80211 phy0: rt2x00_set_rf: Info - RF chipset 3290 detected
[   32.915359] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   35.146070] ieee80211 phy0: rt2x00lib_request_firmware: Info - Loading firmware file 'rt3290.bin'
[   35.208401] ieee80211 phy0: rt2x00lib_request_firmware: Info - Firmware detected - version: 0.37
[   35.265039] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   35.265415] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   37.739368] wlan0: authenticate with <MAC C-01 FreeWiFi>
[   37.754763] wlan0: send auth to <MAC C-01 FreeWiFi> (try 1/3)
[   37.757978] wlan0: authenticated
[   37.758681] wlan0: associate with <MAC C-01 FreeWiFi> (try 1/3)
[   37.774832] wlan0: RX AssocResp from <MAC C-01 FreeWiFi> (capab=0xc11 status=0 aid=3)
[   37.774905] wlan0: associated
[   37.774951] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  182.364434] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  265.049284] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  267.191884] wlan0: authenticate with <MAC C-01 FreeWiFi>
[  267.207204] wlan0: send auth to <MAC C-01 FreeWiFi> (try 1/3)
[  267.209701] wlan0: authenticated
[  267.210853] wlan0: associate with <MAC C-01 FreeWiFi> (try 1/3)
[  267.226893] wlan0: RX AssocResp from <MAC C-01 FreeWiFi> (capab=0xc11 status=0 aid=3)
[  267.226964] wlan0: associated
[  267.227011] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  267.444026] wlan0: deauthenticating from <MAC C-01 FreeWiFi> by local choice (reason=2)
[  267.467018] wlan0: authenticate with <MAC C-01 FreeWiFi>
[  267.474945] wlan0: send auth to <MAC C-01 FreeWiFi> (try 1/3)
[  267.476665] wlan0: authenticated
[  267.478614] wlan0: associate with <MAC C-01 FreeWiFi> (try 1/3)
[  267.494740] wlan0: RX AssocResp from <MAC C-01 FreeWiFi> (capab=0xc11 status=0 aid=3)
[  267.494874] wlan0: associated
[  412.035221] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  435.552607] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  436.731391] wlan0: authenticate with <MAC C-01 FreeWiFi>
[  436.739125] wlan0: send auth to <MAC C-01 FreeWiFi> (try 1/3)
[  436.741667] wlan0: authenticated
[  436.743163] wlan0: associate with <MAC C-01 FreeWiFi> (try 1/3)
[  436.759194] wlan0: RX AssocResp from <MAC C-01 FreeWiFi> (capab=0xc11 status=0 aid=3)
[  436.759265] wlan0: associated
[  436.759801] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  439.343466] wlan0: deauthenticating from <MAC C-01 FreeWiFi> by local choice (reason=3)
[  440.068997] wlan0: authenticate with <MAC C-01 FreeWiFi>
[  440.076240] wlan0: send auth to <MAC C-01 FreeWiFi> (try 1/3)
[  440.078302] wlan0: authenticated
[  440.084120] wlan0: associate with <MAC C-01 FreeWiFi> (try 1/3)
[  440.100139] wlan0: RX AssocResp from <MAC C-01 FreeWiFi> (capab=0xc11 status=0 aid=3)
[  440.100217] wlan0: associated
[  440.341589] wlan0: deauthenticating from <MAC C-01 FreeWiFi> by local choice (reason=2)
[  440.363958] wlan0: authenticate with <MAC C-01 FreeWiFi>
[  440.371886] wlan0: send auth to <MAC C-01 FreeWiFi> (try 1/3)
[  440.376791] wlan0: authenticated
[  440.381526] wlan0: associate with <MAC C-01 FreeWiFi> (try 1/3)
[  440.382003] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  440.382249] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  440.401777] wlan0: RX AssocResp from <MAC C-01 FreeWiFi> (capab=0xc11 status=0 aid=3)
[  440.401871] wlan0: associated
[  440.402054] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  513.681691] wlan0: authenticate with <MAC C-01 FreeWiFi>
[  513.697007] wlan0: send auth to <MAC C-01 FreeWiFi> (try 1/3)
[  513.710478] wlan0: send auth to <MAC C-01 FreeWiFi> (try 2/3)
[  513.751420] wlan0: send auth to <MAC C-01 FreeWiFi> (try 3/3)
[  513.784818] wlan0: authentication with <MAC C-01 FreeWiFi> timed out
[  527.923080] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  576.332273] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  578.462776] wlan0: authenticate with <MAC C-01 FreeWiFi>
[  578.478330] wlan0: send auth to <MAC C-01 FreeWiFi> (try 1/3)
[  578.480771] wlan0: authenticated
[  578.482151] wlan0: associate with <MAC C-01 FreeWiFi> (try 1/3)
[  578.499902] wlan0: RX AssocResp from <MAC C-01 FreeWiFi> (capab=0xc11 status=0 aid=3)
[  578.499982] wlan0: associated
[  578.500041] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  578.738210] wlan0: deauthenticating from <MAC C-01 FreeWiFi> by local choice (reason=2)
[  578.762057] wlan0: authenticate with <MAC C-01 FreeWiFi>
[  578.769994] wlan0: send auth to <MAC C-01 FreeWiFi> (try 1/3)
[  578.773231] wlan0: authenticated
[  578.773924] wlan0: associate with <MAC C-01 FreeWiFi> (try 1/3)
[  578.790030] wlan0: RX AssocResp from <MAC C-01 FreeWiFi> (capab=0xc11 status=0 aid=3)
[  578.790138] wlan0: associated
[  710.491048] wlan0: authenticate with <MAC C-01 FreeWiFi>
[  710.506308] wlan0: send auth to <MAC C-01 FreeWiFi> (try 1/3)
[  710.530638] wlan0: send auth to <MAC C-01 FreeWiFi> (try 2/3)
[  710.569769] wlan0: send auth to <MAC C-01 FreeWiFi> (try 3/3)
[  710.601399] wlan0: authentication with <MAC C-01 FreeWiFi> timed out
[  724.738913] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  735.691645] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  736.841324] wlan0: authenticate with <MAC C-01 FreeWiFi>
[  736.846260] wlan0: send auth to <MAC C-01 FreeWiFi> (try 1/3)
[  736.848736] wlan0: authenticated
[  736.850255] wlan0: associate with <MAC C-01 FreeWiFi> (try 1/3)
[  736.877708] wlan0: RX AssocResp from <MAC C-01 FreeWiFi> (capab=0xc11 status=0 aid=3)
[  736.877779] wlan0: associated
[  736.877823] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  882.586454] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  893.656300] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  894.819983] wlan0: authenticate with <MAC C-01 FreeWiFi>
[  894.827188] wlan0: send auth to <MAC C-01 FreeWiFi> (try 1/3)
[  894.830146] wlan0: authenticated
[  894.831086] wlan0: associate with <MAC C-01 FreeWiFi> (try 1/3)
[  894.849297] wlan0: RX AssocResp from <MAC C-01 FreeWiFi> (capab=0xc11 status=0 aid=3)
[  894.849363] wlan0: associated
[  894.849404] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  966.268421] wlan0: authenticate with <MAC C-01 FreeWiFi>
[  966.283558] wlan0: send auth to <MAC C-01 FreeWiFi> (try 1/3)
[  966.316631] wlan0: send auth to <MAC C-01 FreeWiFi> (try 2/3)
[  966.349499] wlan0: send auth to <MAC C-01 FreeWiFi> (try 3/3)
[  966.394290] wlan0: authentication with <MAC C-01 FreeWiFi> timed out
[  980.501350] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  995.577000] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  997.703940] wlan0: authenticate with <MAC C-01 FreeWiFi>
[  997.719084] wlan0: send auth to <MAC C-01 FreeWiFi> (try 1/3)
[  997.721711] wlan0: authenticated
[  997.722913] wlan0: associate with <MAC C-01 FreeWiFi> (try 1/3)
[  997.739187] wlan0: RX AssocResp from <MAC C-01 FreeWiFi> (capab=0xc11 status=0 aid=3)
[  997.739268] wlan0: associated
[  997.739351] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 1067.169418] wlan0: authenticate with <MAC C-01 FreeWiFi>
[ 1067.184812] wlan0: send auth to <MAC C-01 FreeWiFi> (try 1/3)
[ 1067.212948] wlan0: send auth to <MAC C-01 FreeWiFi> (try 2/3)
[ 1067.243304] wlan0: send auth to <MAC C-01 FreeWiFi> (try 3/3)
[ 1067.282074] wlan0: authentication with <MAC C-01 FreeWiFi> timed out
[ 1081.412910] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1093.448963] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1095.591693] wlan0: authenticate with <MAC C-01 FreeWiFi>
[ 1095.606861] wlan0: send auth to <MAC C-01 FreeWiFi> (try 1/3)
[ 1095.616189] wlan0: authenticated
[ 1095.618887] wlan0: associate with <MAC C-01 FreeWiFi> (try 1/3)
[ 1095.647316] wlan0: RX AssocResp from <MAC C-01 FreeWiFi> (capab=0xc11 status=0 aid=3)
[ 1095.647382] wlan0: associated
[ 1095.647421] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 1098.986965] wlan0: deauthenticated from <MAC C-01 FreeWiFi> (Reason: 15)
[ 1099.008641] wlan0: authenticate with <MAC C-01 FreeWiFi>
[ 1099.015992] wlan0: send auth to <MAC C-01 FreeWiFi> (try 1/3)
[ 1099.018364] wlan0: authenticated
[ 1099.019630] wlan0: associate with <MAC C-01 FreeWiFi> (try 1/3)
[ 1099.038032] wlan0: RX AssocResp from <MAC C-01 FreeWiFi> (capab=0xc11 status=0 aid=3)
[ 1099.038136] wlan0: associated
[ 1165.078010] wlan0: authenticate with <MAC C-01 FreeWiFi>
[ 1165.093295] wlan0: send auth to <MAC C-01 FreeWiFi> (try 1/3)
[ 1165.132873] wlan0: send auth to <MAC C-01 FreeWiFi> (try 2/3)
[ 1165.157786] wlan0: send auth to <MAC C-01 FreeWiFi> (try 3/3)
[ 1165.187371] wlan0: authentication with <MAC C-01 FreeWiFi> timed out
[ 1179.347987] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1192.920086] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1195.046667] wlan0: authenticate with <MAC C-01 FreeWiFi>
[ 1195.062078] wlan0: send auth to <MAC C-01 FreeWiFi> (try 1/3)
[ 1195.064622] wlan0: authenticated
[ 1195.065926] wlan0: associate with <MAC C-01 FreeWiFi> (try 1/3)
[ 1195.169829] wlan0: associate with <MAC C-01 FreeWiFi> (try 2/3)
[ 1195.273726] wlan0: associate with <MAC C-01 FreeWiFi> (try 3/3)
[ 1195.377630] wlan0: association with <MAC C-01 FreeWiFi> timed out
[ 1196.545224] wlan0: authenticate with <MAC C-01 FreeWiFi>
[ 1196.560717] wlan0: send auth to <MAC C-01 FreeWiFi> (try 1/3)
[ 1196.562235] wlan0: authenticated
[ 1196.564571] wlan0: associate with <MAC C-01 FreeWiFi> (try 1/3)
[ 1196.600592] wlan0: RX AssocResp from <MAC C-01 FreeWiFi> (capab=0xc11 status=0 aid=3)
[ 1196.600665] wlan0: associated
[ 1196.600721] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 1409.860193] wlan0: authenticate with <MAC C-01 FreeWiFi>
[ 1409.875279] wlan0: send auth to <MAC C-01 FreeWiFi> (try 1/3)
[ 1409.899552] wlan0: send auth to <MAC C-01 FreeWiFi> (try 2/3)
[ 1409.943323] wlan0: send auth to <MAC C-01 FreeWiFi> (try 3/3)
[ 1409.974283] wlan0: authentication with <MAC C-01 FreeWiFi> timed out
[ 1424.102985] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1443.369301] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1444.570048] wlan0: authenticate with <MAC C-01 FreeWiFi>
[ 1444.575794] wlan0: send auth to <MAC C-01 FreeWiFi> (try 1/3)
[ 1444.578432] wlan0: authenticated
[ 1444.579682] wlan0: associate with <MAC C-01 FreeWiFi> (try 1/3)
[ 1444.683784] wlan0: associate with <MAC C-01 FreeWiFi> (try 2/3)
[ 1444.787678] wlan0: associate with <MAC C-01 FreeWiFi> (try 3/3)
[ 1444.891579] wlan0: association with <MAC C-01 FreeWiFi> timed out
[ 1446.059779] wlan0: authenticate with <MAC C-01 FreeWiFi>
[ 1446.074439] wlan0: send auth to <MAC C-01 FreeWiFi> (try 1/3)
[ 1446.075898] wlan0: authenticated
[ 1446.078323] wlan0: associate with <MAC C-01 FreeWiFi> (try 1/3)
[ 1446.182293] wlan0: associate with <MAC C-01 FreeWiFi> (try 2/3)
[ 1446.286188] wlan0: associate with <MAC C-01 FreeWiFi> (try 3/3)
[ 1446.390066] wlan0: association with <MAC C-01 FreeWiFi> timed out
[ 1447.957974] wlan0: authenticate with <MAC C-01 FreeWiFi>
[ 1447.972710] wlan0: send auth to <MAC C-01 FreeWiFi> (try 1/3)
[ 1447.974264] wlan0: authenticated
[ 1447.976621] wlan0: associate with <MAC C-01 FreeWiFi> (try 1/3)
[ 1448.080738] wlan0: associate with <MAC C-01 FreeWiFi> (try 2/3)
[ 1448.103328] wlan0: RX AssocResp from <MAC C-01 FreeWiFi> (capab=0xc11 status=0 aid=3)
[ 1448.103400] wlan0: associated
[ 1448.103478] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 1493.989779] wlan0: deauthenticating from <MAC C-01 FreeWiFi> by local choice (reason=3)
[ 1496.838903] wlan0: authenticate with <MAC C-01 FreeWiFi>
[ 1496.844472] wlan0: send auth to <MAC C-01 FreeWiFi> (try 1/3)
[ 1496.845921] wlan0: authenticated
[ 1496.848474] wlan0: associate with <MAC C-01 FreeWiFi> (try 1/3)
[ 1496.868314] wlan0: RX AssocResp from <MAC C-01 FreeWiFi> (capab=0xc11 status=0 aid=3)
[ 1496.868386] wlan0: associated
[ 1501.088695] wlan0: deauthenticated from <MAC C-01 FreeWiFi> (Reason: 15)
[ 1505.929257] wlan0: authenticate with <MAC C-01 FreeWiFi>
[ 1505.944468] wlan0: send auth to <MAC C-01 FreeWiFi> (try 1/3)
[ 1505.949711] wlan0: authenticated
[ 1505.952161] wlan0: associate with <MAC C-01 FreeWiFi> (try 1/3)
[ 1506.056049] wlan0: associate with <MAC C-01 FreeWiFi> (try 2/3)
[ 1506.160075] wlan0: associate with <MAC C-01 FreeWiFi> (try 3/3)
[ 1506.263869] wlan0: association with <MAC C-01 FreeWiFi> timed out
[ 1507.843339] wlan0: authenticate with <MAC C-01 FreeWiFi>
[ 1507.858766] wlan0: send auth to <MAC C-01 FreeWiFi> (try 1/3)
[ 1507.862237] wlan0: authenticated
[ 1507.866558] wlan0: associate with <MAC C-01 FreeWiFi> (try 1/3)
[ 1507.970508] wlan0: associate with <MAC C-01 FreeWiFi> (try 2/3)
[ 1508.074237] wlan0: associate with <MAC C-01 FreeWiFi> (try 3/3)
[ 1508.178260] wlan0: association with <MAC C-01 FreeWiFi> timed out
[ 1510.253099] wlan0: authenticate with <MAC C-01 FreeWiFi>
[ 1510.268522] wlan0: send auth to <MAC C-01 FreeWiFi> (try 1/3)
[ 1510.272487] wlan0: authenticated
[ 1510.276403] wlan0: associate with <MAC C-01 FreeWiFi> (try 1/3)
[ 1510.380311] wlan0: associate with <MAC C-01 FreeWiFi> (try 2/3)
[ 1510.484219] wlan0: associate with <MAC C-01 FreeWiFi> (try 3/3)
[ 1510.538253] wlan0: RX AssocResp from <MAC C-01 FreeWiFi> (capab=0xc11 status=0 aid=3)
[ 1510.538328] wlan0: associated
[ 1513.552802] wlan0: deauthenticated from <MAC C-01 FreeWiFi> (Reason: 15)


    ======== Done ========
```

---

### Post by Hadaka on 2014-07-16
Hi,give this a try and see if it stops the 90 second  disconnect problem.
keep in mind this is only good untill the first boot,,,so after you enter
the command, let it run awhile to see if it helps.
```
sudo modprobe -rf rt2800pci
sudo modprobe rt2800pci nohwcrypt=1
```
*If this stops your drops, to make it permenant do,,
```
sudo gedit /etc/modprobe.d/rt2800pci.conf
```
enter one line of code,,
```
options rt2800pci nohwcrypt=1
```
close and save gedit
thanks

---

### Post by Hadaka on 2014-07-16
Hi,give this a try and see if it stops the 90 second  disconnect problem.
keep in mind this is only good untill the first boot,,,so after you enter
the command, let it run awhile to see if it helps.
```
sudo modprobe -rf rt2800pci
sudo modprobe rt2800pci nohwcrypt=1
```
*If this stops your drops, to make it permenant do,,
```
sudo gedit /etc/modprobe.d/rt2800pci.conf
```
enter one line of code,,
```
options rt2800pci nohwcrypt=1
```
close and save gedit
thanks

somehow got a double post,,,sorry

---

### Post by manifestDensity on 2014-07-17
This was absolutely not the answer.  After running this I went from connecting and dropping to be unable to connect at all.

---

### Post by Hadaka on 2014-07-17
Yes the first command.. 
```
sudo modprobe -rf rt2800pci
```
ABOLUTELY prevents the wireless from connecting
because the dirver module is removed.
The second command..
```
sudo modprobe rt2800pci nohwcrypt=1
```
reinserts the driver module with the nohwcrypt set to a value of 1
what this does is turns off your N speed which is likely dropping your connection.
so if you entered the first command correctly,,that shuts down wifi
if there was a typo in the second command it would remain off
if the command was entered correctly, it would not prevent the wifi from working,
i suggest try again and COPY  and paste the commands,
thanks.

---

### Post by manifestDensity on 2014-07-17
Copied and pasted the above commands.  This renders the machine unable to connect at all.  The wifi is enabled, but it cannot actually connect to a network.  It tries and disconnects immediately.

---

### Post by manifestDensity on 2014-07-17
Marking this as solved and depositing a link to an AskUbuntu posting that fixed this problem.   Just in case anyone else with a similar issue stumbles into this thread.

[http://askubuntu.com/questions/455030/ralink-rt3290-wifi-driver-is-not-working-in-ubuntu-14-04](http://askubuntu.com/questions/455030/ralink-rt3290-wifi-driver-is-not-working-in-ubuntu-14-04)

---

