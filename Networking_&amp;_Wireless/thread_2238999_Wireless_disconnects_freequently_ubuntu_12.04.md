---
title: "Wireless disconnects freequently ubuntu 12.04"
date: 2014-08-11
forum: Networking &amp; Wireless
---

### Post by pantelis2 on 2014-08-11
Hello, I'm new to Ubuntu and this problem gets on my nerves. Wireless keeps disconnecting after 10-15 minutes and I have to disable and re-enable wirelless to get connected. I tried some random solutions found on the net but didnt work. I found a script and run it. Maybe it helps


    ======== Wireless-Info START ========

System-Info ~~~~~~~~~~~~~~~~~~~~~~~~

artemisPC 3.5.0-54-generic x86_64,  Ubuntu 12.04.5 LTS, precise

CPU    : Intel(R) Core(TM) i3-3110M CPU @ 2.40GHz
Memory : 3849 MB
Uptime : 16:59:47 up 20 min,  2 users,  load average: 0.37, 0.33, 0.24


lspci ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

01:00.0 Network controller [0280]: Ralink corp. RT3290 Wireless 802.11n 1T/1R PCIe [1814:3290]
    Subsystem: Hewlett-Packard Company Device [103c:18ec]
    Kernel driver in use: rt2800pci
--
08:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 07)
    Subsystem: Hewlett-Packard Company Device [103c:1854]
    Kernel driver in use: r8168


lsusb ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 003: ID 064e:e263 Suyin Corp. 


PCMCIA Card Info ~~~~~~~~~~~~~~~~~~~



iwconfig ~~~~~~~~~~~~~~~~~~~~~~~~~~~

wlan0     IEEE 802.11bgn  ESSID:"TA PSARADIKA"  
          Mode:Managed  Frequency:2.447 GHz  Access Point: <MAC C-01 TA PSARADIKA>   
          Bit Rate=54 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=50/70  Signal level=-60 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:7  Invalid misc:27   Missed beacon:0



rfkill ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

      Interface             Soft blocked  Hard blocked
0: phy0: Wireless LAN           no            no
1: hci0: Bluetooth              no            no
2: hp-wifi: Wireless LAN        no            no
3: hp-bluetooth: Bluetooth      no            no


lsmod ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

hp_wmi                 18093  0 
sparse_keymap          13891  1 hp_wmi
wmi                    19106  1 hp_wmi
rt2800pci              18522  0 
rt2800lib              62728  1 rt2800pci
crc_ccitt              12708  1 rt2800lib
rt2x00pci              14477  1 rt2800pci
rt2x00lib              54856  3 rt2800pci,rt2800lib,rt2x00pci
mac80211              557966  3 rt2800lib,rt2x00pci,rt2x00lib
cfg80211              211292  2 rt2x00lib,mac80211
compat                 14957  3 rt2800pci,mac80211,cfg80211
eeprom_93cx6           13345  1 rt2800pci


module parameters ~~~~~~~~~~~~~~~~~~

cfg80211      (2): cfg80211_disable_40mhz_24ghz=N | ieee80211_regdom=00
compat        (4): 
mac80211      (4): ieee80211_default_rc_algo=minstrel_ht | max_nullfunc_tries=2 | max_probe_tries=5 | probe_wait_ms=500
rt2800pci     (1): nohwcrypt=N
wmi           (2): debug_dump_wdg=N | debug_event=N


nm-tool ~~~~~~~~~~~~~~~~~~~~~~~~~~~~

State: connected (global)
=======================o=============o===========o=============o=========o===========o==============o===========
 Interface & ID        | Type        | Driver    | State       | Default | Speed     | Support      | HW Addr   
=======================o=============o===========o=============o=========o===========o==============o===========
 eth0                  | Wired       | r8168     | unavailable | no      |           |              | <MAC eth0>
-----------------------+-------------+-----------+-------------+---------+-----------+--------------+-----------
 wlan0  [TA PSARADIKA] | 802.11 WiFi | rt2800pci | connected   | yes     | 54 Mb/s   | WEP/WPA/WPA2 | <MAC wlan0>

    *TA PSARADIKA:   Infra, <MAC C-01 TA PSARADIKA>, Freq 2447 MHz, Rate 54 Mb/s, Strength 62 WPA

    Address:         192.168.1.5
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1
    DNS:             192.168.1.1
-----------------------+-------------+-----------+-------------+---------+-----------+--------------+-----------


NetworkManager.state ~~~~~~~~~~~~~~~

[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true


NetworkManager.conf ~~~~~~~~~~~~~~~~

[main]
plugins=ifupdown,keyfile
dns=dnsmasq

[ifupdown]
managed=false


NM WiFi Profiles ~~~~~~~~~~~~~~~~~~~

TA PSARADIKA         : ssid=TA PSARADIKA | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 


interfaces ~~~~~~~~~~~~~~~~~~~~~~~~~

auto lo
iface lo inet loopback


resolv.conf ~~~~~~~~~~~~~~~~~~~~~~~~

nameserver 127.0.0.1


Routes & Ping ~~~~~~~~~~~~~~~~~~~~~~

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 wlan0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 wlan0
192.168.1.0     0.0.0.0         255.255.255.0   U     2      0        0 wlan0

--- 192.168.1.1 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 1002ms
rtt min/avg/max/mdev = 1.859/1.870/1.881/0.011 ms


iw reg get ~~~~~~~~~~~~~~~~~~~~~~~~~

(Region : "en_US.UTF-8")
country 00:
    (2402 - 2472 @ 40), (3, 20)
    (2457 - 2482 @ 20), (3, 20), PASSIVE-SCAN, NO-IBSS
    (2474 - 2494 @ 20), (3, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
    (5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS


iwlist chan ~~~~~~~~~~~~~~~~~~~~~~~~

wlan0     14 channels in total; available frequencies :
          Channel 01 (2.412 GHz) - 14 (2.484 GHz)

          Current Frequency:2.447 GHz (Channel 8)


iwlist scan ~~~~~~~~~~~~~~~~~~~~~~~~

wlan0     Scan completed :
          Cell 01 - Address: <MAC C-01 TA PSARADIKA>
                    Channel:8
                    Frequency:2.447 GHz (Channel 8)
                    Quality=48/70  Signal level=-62 dBm  
                    Encryption key:on
                    ESSID:"TA PSARADIKA"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000001353a46f73
                    Extra: Last beacon: 12ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK


blacklist ~~~~~~~~~~~~~~~~~~~~~~~~~~

[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci

[/etc/modprobe.d/blacklist-opensource-graphics.conf]
blacklist nouveau
blacklist radeon 
blacklist lbm-nouveau
blacklist lbm-radeon 

[/etc/modprobe.d/dkms.conf]
blacklist r8169


modinfo ~~~~~~~~~~~~~~~~~~~~~~~~~~~~

[hp_wmi]
filename:       /lib/modules/3.5.0-54-generic/kernel/drivers/platform/x86/hp-wmi.ko
srcversion:     D7CCE17CEE5F03AEE3CB656
depends:        wmi,sparse-keymap

[wmi]
filename:       /lib/modules/3.5.0-54-generic/updates/dkms/wmi.ko
srcversion:     5BB94E00820BEDCC7EBA34E
depends:        
parm:           debug_event:Log WMI Events [0/1] (bool)
parm:           debug_dump_wdg:Dump available WMI interfaces [0/1] (bool)

[rt2800pci]
filename:       /lib/modules/3.5.0-54-generic/updates/dkms/rt2800pci.ko
firmware:       rt2860.bin
version:        3.0.0
srcversion:     41B14A95C58ED67B6FB5F4C
depends:        rt2x00lib,rt2800lib,rt2x00pci,compat,eeprom_93cx6
parm:           nohwcrypt:Disable hardware encryption. (bool)

[rt2800lib]
filename:       /lib/modules/3.5.0-54-generic/updates/dkms/rt2800lib.ko
version:        3.0.0
srcversion:     93046BBEA3A727AD14A7985
depends:        rt2x00lib,mac80211,crc-ccitt

[crc_ccitt]
filename:       /lib/modules/3.5.0-54-generic/kernel/lib/crc-ccitt.ko
srcversion:     2294FCAD06D727386004EEB
depends:        

[rt2x00pci]
filename:       /lib/modules/3.5.0-54-generic/updates/dkms/rt2x00pci.ko
version:        3.0.0
srcversion:     93FC24DCA03D0CF9FAB79E7
depends:        rt2x00lib,mac80211

[rt2x00lib]
filename:       /lib/modules/3.5.0-54-generic/updates/dkms/rt2x00lib.ko
version:        3.0.0
srcversion:     FB31228361305FD1C6A3C11
depends:        mac80211,cfg80211

[mac80211]
filename:       /lib/modules/3.5.0-54-generic/updates/dkms/mac80211.ko
srcversion:     20383BD89331C672F84C85C
depends:        cfg80211,compat
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[cfg80211]
filename:       /lib/modules/3.5.0-54-generic/updates/dkms/cfg80211.ko
srcversion:     03EDA848F991DF674681216
depends:        compat
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

[compat]
filename:       /lib/modules/3.5.0-54-generic/updates/dkms/compat.ko
srcversion:     2CD47A74B03CA273BB5DDE9
depends:        
parm:           compat_base:charp
parm:           compat_base_tree:The upstream verion of compat.git used (charp)
parm:           compat_base_tree_version:The git-describe of the upstream base tree (charp)
parm:           compat_version:Version of the kernel compat backport work (charp)

[eeprom_93cx6]
filename:       /lib/modules/3.5.0-54-generic/updates/dkms/eeprom_93cx6.ko
version:        2.0
srcversion:     91545D10816B1B0B9B19B55
depends:        


udev rules ~~~~~~~~~~~~~~~~~~~~~~~~~

# PCI device 0x10ec:/sys/devices/pci0000:00/0000:00:1c.3/0000:08:00.0 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC eth0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

# PCI device 0x1814:/sys/devices/pci0000:00/0000:00:1c.0/0000:01:00.0 (rt2800pci)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC wlan0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"


Custom files/entries ~~~~~~~~~~~~~~~

/etc/modules        : Not Default
/etc/rc.local       : Not Default
/etc/modprobe.d     : Not Default
/etc/pm/(cnf|pw|sl) : Default

[/etc/modules]
kbccmnd
disable_mmc
disable_mmc

[/etc/rc.local]
echo 0 > /sys/module/video/parameters/brightness_switch_enabled
exit 0

[/etc/modprobe.d]
disable-mmc.conf  : install rtsx_pci /sbin/modprobe disable_mmc; /sbin/modprobe --ignore-install rtsx_pci
snd-hda-intel.conf: options snd-hda-intel power_save_controller=N


Kernel boot line ~~~~~~~~~~~~~~~~~~~

BOOT_IMAGE=/boot/vmlinuz-3.5.0-54-generic root=UUID=7cec91c4-2fc6-4e22-a17e-ef0d16c7eb70 ro i915.modeset=1 quiet splash vt.handoff=7


dmesg ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

[    0.909852] audit: initializing netlink socket (disabled)
[   12.197058] r8168 Gigabit Ethernet driver 8.035.00-NAPI loaded
[   12.413692] Registered led device: rt2800pci-phy0::radio
[   12.413733] Registered led device: rt2800pci-phy0::assoc
[   12.413774] Registered led device: rt2800pci-phy0::quality
[   12.423608] wmi: Mapper loaded
[   12.546466] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[   12.690790] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   12.824094] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   12.824561] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   15.847526] wlan0: authenticate with <MAC C-01 TA PSARADIKA>
[   15.863247] wlan0: send auth to <MAC C-01 TA PSARADIKA> (try 1/3)
[   15.864736] wlan0: authenticated
[   15.875072] wlan0: associate with <MAC C-01 TA PSARADIKA> (try 1/3)
[   15.878818] wlan0: RX AssocResp from <MAC C-01 TA PSARADIKA> (capab=0x411 status=0 aid=3)
[   15.878925] wlan0: associated
[   15.879295] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready

    ======== Done ========

---

### Post by pantelis2 on 2014-08-11
sorry I just found the code window

```


    ======== Wireless-Info START ========

System-Info ~~~~~~~~~~~~~~~~~~~~~~~~

artemisPC 3.5.0-54-generic x86_64,  Ubuntu 12.04.5 LTS, precise

CPU    : Intel(R) Core(TM) i3-3110M CPU @ 2.40GHz
Memory : 3849 MB
Uptime : 16:59:47 up 20 min,  2 users,  load average: 0.37, 0.33, 0.24


lspci ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

01:00.0 Network controller [0280]: Ralink corp. RT3290 Wireless 802.11n 1T/1R PCIe [1814:3290]
    Subsystem: Hewlett-Packard Company Device [103c:18ec]
    Kernel driver in use: rt2800pci
--
08:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 07)
    Subsystem: Hewlett-Packard Company Device [103c:1854]
    Kernel driver in use: r8168


lsusb ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 003: ID 064e:e263 Suyin Corp. 


PCMCIA Card Info ~~~~~~~~~~~~~~~~~~~



iwconfig ~~~~~~~~~~~~~~~~~~~~~~~~~~~

wlan0     IEEE 802.11bgn  ESSID:"TA PSARADIKA"  
          Mode:Managed  Frequency:2.447 GHz  Access Point: <MAC C-01 TA PSARADIKA>   
          Bit Rate=54 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=50/70  Signal level=-60 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:7  Invalid misc:27   Missed beacon:0



rfkill ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

      Interface             Soft blocked  Hard blocked
0: phy0: Wireless LAN           no            no
1: hci0: Bluetooth              no            no
2: hp-wifi: Wireless LAN        no            no
3: hp-bluetooth: Bluetooth      no            no


lsmod ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

hp_wmi                 18093  0 
sparse_keymap          13891  1 hp_wmi
wmi                    19106  1 hp_wmi
rt2800pci              18522  0 
rt2800lib              62728  1 rt2800pci
crc_ccitt              12708  1 rt2800lib
rt2x00pci              14477  1 rt2800pci
rt2x00lib              54856  3 rt2800pci,rt2800lib,rt2x00pci
mac80211              557966  3 rt2800lib,rt2x00pci,rt2x00lib
cfg80211              211292  2 rt2x00lib,mac80211
compat                 14957  3 rt2800pci,mac80211,cfg80211
eeprom_93cx6           13345  1 rt2800pci


module parameters ~~~~~~~~~~~~~~~~~~

cfg80211      (2): cfg80211_disable_40mhz_24ghz=N | ieee80211_regdom=00
compat        (4): 
mac80211      (4): ieee80211_default_rc_algo=minstrel_ht | max_nullfunc_tries=2 | max_probe_tries=5 | probe_wait_ms=500
rt2800pci     (1): nohwcrypt=N
wmi           (2): debug_dump_wdg=N | debug_event=N


nm-tool ~~~~~~~~~~~~~~~~~~~~~~~~~~~~

State: connected (global)
=======================o=============o===========o=============o=========o===========o==============o===========
 Interface & ID        | Type        | Driver    | State       | Default | Speed     | Support      | HW Addr   
=======================o=============o===========o=============o=========o===========o==============o===========
 eth0                  | Wired       | r8168     | unavailable | no      |           |              | <MAC eth0>
-----------------------+-------------+-----------+-------------+---------+-----------+--------------+-----------
 wlan0  [TA PSARADIKA] | 802.11 WiFi | rt2800pci | connected   | yes     | 54 Mb/s   | WEP/WPA/WPA2 | <MAC wlan0>

    *TA PSARADIKA:   Infra, <MAC C-01 TA PSARADIKA>, Freq 2447 MHz, Rate 54 Mb/s, Strength 62 WPA

    Address:         192.168.1.5
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1
    DNS:             192.168.1.1
-----------------------+-------------+-----------+-------------+---------+-----------+--------------+-----------


NetworkManager.state ~~~~~~~~~~~~~~~

[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true


NetworkManager.conf ~~~~~~~~~~~~~~~~

[main]
plugins=ifupdown,keyfile
dns=dnsmasq

[ifupdown]
managed=false


NM WiFi Profiles ~~~~~~~~~~~~~~~~~~~

TA PSARADIKA         : ssid=TA PSARADIKA | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 


interfaces ~~~~~~~~~~~~~~~~~~~~~~~~~

auto lo
iface lo inet loopback


resolv.conf ~~~~~~~~~~~~~~~~~~~~~~~~

nameserver 127.0.0.1


Routes & Ping ~~~~~~~~~~~~~~~~~~~~~~

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 wlan0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 wlan0
192.168.1.0     0.0.0.0         255.255.255.0   U     2      0        0 wlan0

--- 192.168.1.1 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 1002ms
rtt min/avg/max/mdev = 1.859/1.870/1.881/0.011 ms


iw reg get ~~~~~~~~~~~~~~~~~~~~~~~~~

(Region : "en_US.UTF-8")
country 00:
    (2402 - 2472 @ 40), (3, 20)
    (2457 - 2482 @ 20), (3, 20), PASSIVE-SCAN, NO-IBSS
    (2474 - 2494 @ 20), (3, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
    (5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS


iwlist chan ~~~~~~~~~~~~~~~~~~~~~~~~

wlan0     14 channels in total; available frequencies :
          Channel 01 (2.412 GHz) - 14 (2.484 GHz)

          Current Frequency:2.447 GHz (Channel 8)


iwlist scan ~~~~~~~~~~~~~~~~~~~~~~~~

wlan0     Scan completed :
          Cell 01 - Address: <MAC C-01 TA PSARADIKA>
                    Channel:8
                    Frequency:2.447 GHz (Channel 8)
                    Quality=48/70  Signal level=-62 dBm  
                    Encryption key:on
                    ESSID:"TA PSARADIKA"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000001353a46f73
                    Extra: Last beacon: 12ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK


blacklist ~~~~~~~~~~~~~~~~~~~~~~~~~~

[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci

[/etc/modprobe.d/blacklist-opensource-graphics.conf]
blacklist nouveau
blacklist radeon 
blacklist lbm-nouveau
blacklist lbm-radeon 

[/etc/modprobe.d/dkms.conf]
blacklist r8169


modinfo ~~~~~~~~~~~~~~~~~~~~~~~~~~~~

[hp_wmi]
filename:       /lib/modules/3.5.0-54-generic/kernel/drivers/platform/x86/hp-wmi.ko
srcversion:     D7CCE17CEE5F03AEE3CB656
depends:        wmi,sparse-keymap

[wmi]
filename:       /lib/modules/3.5.0-54-generic/updates/dkms/wmi.ko
srcversion:     5BB94E00820BEDCC7EBA34E
depends:        
parm:           debug_event:Log WMI Events [0/1] (bool)
parm:           debug_dump_wdg:Dump available WMI interfaces [0/1] (bool)

[rt2800pci]
filename:       /lib/modules/3.5.0-54-generic/updates/dkms/rt2800pci.ko
firmware:       rt2860.bin
version:        3.0.0
srcversion:     41B14A95C58ED67B6FB5F4C
depends:        rt2x00lib,rt2800lib,rt2x00pci,compat,eeprom_93cx6
parm:           nohwcrypt:Disable hardware encryption. (bool)

[rt2800lib]
filename:       /lib/modules/3.5.0-54-generic/updates/dkms/rt2800lib.ko
version:        3.0.0
srcversion:     93046BBEA3A727AD14A7985
depends:        rt2x00lib,mac80211,crc-ccitt

[crc_ccitt]
filename:       /lib/modules/3.5.0-54-generic/kernel/lib/crc-ccitt.ko
srcversion:     2294FCAD06D727386004EEB
depends:        

[rt2x00pci]
filename:       /lib/modules/3.5.0-54-generic/updates/dkms/rt2x00pci.ko
version:        3.0.0
srcversion:     93FC24DCA03D0CF9FAB79E7
depends:        rt2x00lib,mac80211

[rt2x00lib]
filename:       /lib/modules/3.5.0-54-generic/updates/dkms/rt2x00lib.ko
version:        3.0.0
srcversion:     FB31228361305FD1C6A3C11
depends:        mac80211,cfg80211

[mac80211]
filename:       /lib/modules/3.5.0-54-generic/updates/dkms/mac80211.ko
srcversion:     20383BD89331C672F84C85C
depends:        cfg80211,compat
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[cfg80211]
filename:       /lib/modules/3.5.0-54-generic/updates/dkms/cfg80211.ko
srcversion:     03EDA848F991DF674681216
depends:        compat
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

[compat]
filename:       /lib/modules/3.5.0-54-generic/updates/dkms/compat.ko
srcversion:     2CD47A74B03CA273BB5DDE9
depends:        
parm:           compat_base:charp
parm:           compat_base_tree:The upstream verion of compat.git used (charp)
parm:           compat_base_tree_version:The git-describe of the upstream base tree (charp)
parm:           compat_version:Version of the kernel compat backport work (charp)

[eeprom_93cx6]
filename:       /lib/modules/3.5.0-54-generic/updates/dkms/eeprom_93cx6.ko
version:        2.0
srcversion:     91545D10816B1B0B9B19B55
depends:        


udev rules ~~~~~~~~~~~~~~~~~~~~~~~~~

# PCI device 0x10ec:/sys/devices/pci0000:00/0000:00:1c.3/0000:08:00.0 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC eth0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

# PCI device 0x1814:/sys/devices/pci0000:00/0000:00:1c.0/0000:01:00.0 (rt2800pci)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC wlan0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"


Custom files/entries ~~~~~~~~~~~~~~~

/etc/modules        : Not Default
/etc/rc.local       : Not Default
/etc/modprobe.d     : Not Default
/etc/pm/(cnf|pw|sl) : Default

[/etc/modules]
kbccmnd
disable_mmc
disable_mmc

[/etc/rc.local]
echo 0 > /sys/module/video/parameters/brightness_switch_enabled
exit 0

[/etc/modprobe.d]
disable-mmc.conf  : install rtsx_pci /sbin/modprobe disable_mmc; /sbin/modprobe --ignore-install rtsx_pci
snd-hda-intel.conf: options snd-hda-intel power_save_controller=N


Kernel boot line ~~~~~~~~~~~~~~~~~~~

BOOT_IMAGE=/boot/vmlinuz-3.5.0-54-generic root=UUID=7cec91c4-2fc6-4e22-a17e-ef0d16c7eb70 ro i915.modeset=1 quiet splash vt.handoff=7


dmesg ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

[    0.909852] audit: initializing netlink socket (disabled)
[   12.197058] r8168 Gigabit Ethernet driver 8.035.00-NAPI loaded
[   12.413692] Registered led device: rt2800pci-phy0::radio
[   12.413733] Registered led device: rt2800pci-phy0::assoc
[   12.413774] Registered led device: rt2800pci-phy0::quality
[   12.423608] wmi: Mapper loaded
[   12.546466] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[   12.690790] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   12.824094] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   12.824561] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   15.847526] wlan0: authenticate with <MAC C-01 TA PSARADIKA>
[   15.863247] wlan0: send auth to <MAC C-01 TA PSARADIKA> (try 1/3)
[   15.864736] wlan0: authenticated
[   15.875072] wlan0: associate with <MAC C-01 TA PSARADIKA> (try 1/3)
[   15.878818] wlan0: RX AssocResp from <MAC C-01 TA PSARADIKA> (capab=0x411 status=0 aid=3)
[   15.878925] wlan0: associated
[   15.879295] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready

    ======== Done ========


```

---

