---
title: "Atheros AR9485 with ath9k not working after upgrade"
date: 2015-02-05
forum: Networking &amp; Wireless
---

### Post by andyhelloween on 2015-02-05
Hello,

A couple of days ago I upgraded my server from Ubuntu 12.04.4 to 14.04.1. Everything went fine until the following day, in which the wireless decided to stop working. I can still scan APs, but can't connect to them. The interface that's not working is wlan0. I'm trying to connecto to the AP in 10.0.0.1. There's another interface eth0, which access a different network 192.168.1.0.

Below is the network script results. I appreciate your time in looking into this.

Kind regards,
Andy.

```

    ======== Wireless-Info START ========

System-Info ~~~~~~~~~~~~~~~~~~~~~~~~

domuyo 3.13.0-45-generic x86_64,  Ubuntu 14.04.1 LTS, trusty

CPU    : Intel(R) Core(TM) i3-3220 CPU @ 3.30GHz
Memory : 15926 MB
Uptime : 21:48:25 up 2 days,  2:58,  2 users,  load average: 0.13, 0.14, 0.14


lspci ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

01:00.0 Network controller [0280]: Qualcomm Atheros AR9485 Wireless Network Adapter [168c:0032] (rev 01)
    Subsystem: Qualcomm Atheros Device [168c:3118]
    Kernel driver in use: ath9k
--
07:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 06)
    Subsystem: Micro-Star International Co., Ltd. [MSI] Device [1462:7681]
    Kernel driver in use: r8169


lsusb ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Bus 002 Device 003: ID 03f0:0024 Hewlett-Packard KU-0316 Keyboard
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 005 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 03f0:2404 Hewlett-Packard Deskjet F2280 series
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


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

ath9k                 164164  0
ath9k_common           13551  1 ath9k
ath9k_hw              453856  2 ath9k_common,ath9k
ath                    28698  3 ath9k_common,ath9k,ath9k_hw
mac80211              630669  1 ath9k
cfg80211              484040  3 ath,ath9k,mac80211
mxm_wmi                13021  0
wmi                    19177  1 mxm_wmi


module parameters ~~~~~~~~~~~~~~~~~~

ath9k         (5): nohwcrypt=1
cfg80211      (2):
mac80211      (5):
wmi           (2):


nm-tool ~~~~~~~~~~~~~~~~~~~~~~~~~~~~


================o======o========o========o=========o===========o==============o===========
 Interface & ID | Type | Driver | State  | Default | Speed     | Support      | HW Addr  
================o======o========o========o=========o===========o==============o===========
                |      |        |        |         |           |              |          
----------------+------+--------+--------+---------+-----------+--------------+-----------


NetworkManager.state ~~~~~~~~~~~~~~~


NetworkManager.conf ~~~~~~~~~~~~~~~~



NM WiFi Profiles ~~~~~~~~~~~~~~~~~~~
 


interfaces ~~~~~~~~~~~~~~~~~~~~~~~~~

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo wlan0 eth0
iface lo inet loopback

# The primary network interface
iface wlan0 inet static
    address 10.0.0.2
    netmask 255.255.255.0
    broadcast 10.0.0.255
    network 10.0.0.0
    gateway 10.0.0.1
    metric 0
    dns-nameservers 10.0.0.1
    wpa-ssid ABCDE
    wpa-psk <WPA key removed>

iface eth0 inet static
    address 192.168.1.100
    netmask 255.255.255.0
    network 192.168.1.0
    gateway 192.168.1.2
    metric 1
    dns-nameservers 10.0.0.1


resolv.conf ~~~~~~~~~~~~~~~~~~~~~~~~

nameserver 10.0.0.1


Routes & Ping ~~~~~~~~~~~~~~~~~~~~~~

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         10.0.0.1        0.0.0.0         UG    0      0        0 wlan0
0.0.0.0         192.168.1.2     0.0.0.0         UG    1      0        0 eth0
10.0.0.0        0.0.0.0         255.255.255.0   U     0      0        0 wlan0
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0

--- 10.0.0.1 ping statistics ---
3 packets transmitted, 0 received, +3 errors, 100% packet loss, time 2015ms
pipe 3

--- 10.0.0.1 ping statistics ---
2 packets transmitted, 0 received, 100% packet loss, time 1006ms



iw reg get ~~~~~~~~~~~~~~~~~~~~~~~~~

(Region : en_NZ.UTF-8)
country AU:
    (2402 - 2482 @ 40), (N/A, 20)
    (5170 - 5250 @ 40), (3, 23)
    (5250 - 5330 @ 40), (3, 23), DFS
    (5735 - 5835 @ 40), (3, 30)


iwlist chan ~~~~~~~~~~~~~~~~~~~~~~~~

wlan0     13 channels in total; available frequencies :
          Channel 01 (2.412 GHz) - 13 (2.472 GHz)


iwlist scan ~~~~~~~~~~~~~~~~~~~~~~~~

wlan0     Scan completed :
          Cell 01 - Address: <MAC C-01 Winery>
                    Channel:3
                    Frequency:2.422 GHz (Channel 3)
                    Quality=66/70  Signal level=-44 dBm  
                    Encryption key:on
                    ESSID:"Winery"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000239562f4d02
                    Extra: Last beacon: 8ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC C-02 ABCDE>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=33/70  Signal level=-77 dBm  
                    Encryption key:on
                    ESSID:"ABCDE"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000336bb91ee5
                    Extra: Last beacon: 8ms ago
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

[ath9k]
filename:       /lib/modules/3.13.0-45-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k.ko
srcversion:     EABAC052C3DF339FA6E716C
depends:        ath9k_hw,mac80211,ath9k_common,cfg80211,ath
parm:           debug:Debugging mask (uint)
parm:           nohwcrypt:Disable hardware encryption (int)
parm:           blink:Enable LED blink on activity (int)
parm:           btcoex_enable:Enable wifi-BT coexistence (int)
parm:           bt_ant_diversity:Enable WLAN/BT RX antenna diversity (int)
parm:           ps_enable:Enable WLAN PowerSave (int)

[ath9k_common]
filename:       /lib/modules/3.13.0-45-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_common.ko
srcversion:     5ED2DF2BD124A3813829DA8
depends:        ath,ath9k_hw

[ath9k_hw]
filename:       /lib/modules/3.13.0-45-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_hw.ko
srcversion:     94B3813AF84C49B115229AD
depends:        ath

[ath]
filename:       /lib/modules/3.13.0-45-generic/kernel/drivers/net/wireless/ath/ath.ko
srcversion:     88A67C5359B02C5A710AFCF
depends:        cfg80211

[mac80211]
filename:       /lib/modules/3.13.0-45-generic/kernel/net/mac80211/mac80211.ko
srcversion:     385697223F8285F67C93A06
depends:        cfg80211
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[cfg80211]
filename:       /lib/modules/3.13.0-45-generic/kernel/net/wireless/cfg80211.ko
srcversion:     C2478077E22138832B71659
depends:        
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

[mxm_wmi]
filename:       /lib/modules/3.13.0-45-generic/kernel/drivers/platform/x86/mxm-wmi.ko
srcversion:     62CBD37DE87DF0C4CD7FBA3
depends:        wmi

[wmi]
filename:       /lib/modules/3.13.0-45-generic/kernel/drivers/platform/x86/wmi.ko
srcversion:     CED5410F008DC70DF5F064B
depends:        
parm:           debug_event:Log WMI Events [0/1] (bool)
parm:           debug_dump_wdg:Dump available WMI interfaces [0/1] (bool)


udev rules ~~~~~~~~~~~~~~~~~~~~~~~~~

# PCI device 0x10ec:/sys/devices/pci0000:00/0000:00:1c.6/0000:07:00.0 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC eth0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

# PCI device 0x168c:/sys/devices/pci0000:00/0000:00:1c.0/0000:01:00.0 (ath9k)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC wlan0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"


Custom files/entries ~~~~~~~~~~~~~~~

/etc/modules        : Not Default
/etc/rc.local       : Default
/etc/modprobe.d     : Not Default
/etc/pm/(cnf|pw|sl) : Default

[/etc/modules]
loop
coretemp
f71882fg
sha512
aes

[/etc/modprobe.d]
ath9k.conf        : options ath9k nohwcrypt=1
iwlwifi.conf      : remove iwlwifi \
                    (/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
                    && /sbin/modprobe -r mac80211
mlx4.conf         : softdep mlx4_core post: mlx4_en


Kernel boot line ~~~~~~~~~~~~~~~~~~~

BOOT_IMAGE=/boot/vmlinuz-3.13.0-45-generic root=UUID=2440bb8a-45bb-4dcd-98ae-a550cc82f841 ro


dmesg ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

[    0.481787] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[    0.481988] audit: initializing netlink socket (disabled)
[    3.411315] wmi: Mapper loaded
[    3.445596] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[   40.815615] ath: EEPROM regdomain: 0x21
[   40.815618] ath: EEPROM indicates we should expect a direct regpair map
[   40.815619] ath: Country alpha2 being used: AU
[   40.815620] ath: Regpair used: 0x21
[   41.951690] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   64.032614] init: z_network_restart main process (1382) terminated with status 1

    ======== Done ========

```

---

### Post by andyhelloween on 2015-02-07
For what it's worth, it appears to be a problem with the configuration of /etc/network/interfaces.

I fixed it with the below thread:
[http://askubuntu.com/questions/464507/ubuntu-14-04-server-wifi-wpa2-personal](http://askubuntu.com/questions/464507/ubuntu-14-04-server-wifi-wpa2-personal)

---

