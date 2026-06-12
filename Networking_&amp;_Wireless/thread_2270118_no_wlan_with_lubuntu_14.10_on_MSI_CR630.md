---
title: "no wlan with lubuntu 14.10 on MSI CR630"
date: 2015-03-20
forum: Networking &amp; Wireless
---

### Post by Thom518 on 2015-03-20
Hi, I have installed Lubuntu 14.10 32 bit on my laptop msi CR630 and the wlan connection does not work.  I run the wireless_script, the result is below. it says the wlan is "hard blocked", what can I do about this? Coud a driver be missing?

```


    ======== Wireless-Info START ========

System-Info ~~~~~~~~~~~~~~~~~~~~~~~~

thomas-CR630 3.16.0-23-generic i686,  Ubuntu 14.10, utopic

CPU    : AMD V120 Processor
Memory : 1762 MB
Uptime : 12:57:41 up 7 min,  2 users,  load average: 0,07, 0,21, 0,14


lspci ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

02:00.0 Network controller [0280]: Ralink corp. RT3090 Wireless 802.11n 1T/1R PCIe [1814:3090]
    Subsystem: Micro-Star International Co., Ltd. [MSI] Device [1462:6891]
    Kernel driver in use: rt2800pci
03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 06)
    Subsystem: Micro-Star International Co., Ltd. [MSI] Device [1462:106e]
    Kernel driver in use: r8169


lsusb ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 002: ID 045e:0745 Microsoft Corp. Nano Transceiver v1.0 for Bluetooth
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


PCMCIA Card Info ~~~~~~~~~~~~~~~~~~~



iwconfig ~~~~~~~~~~~~~~~~~~~~~~~~~~~

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=off   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          


rfkill ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

      Interface        Soft blocked  Hard blocked
0: phy0: Wireless LAN      no            yes


lsmod ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

msi_wmi                13130  0 
sparse_keymap          13708  1 msi_wmi
rt2800pci              13398  0 
rt2800mmio             20244  1 rt2800pci
rt2800lib              87254  2 rt2800pci,rt2800mmio
rt2x00pci              13111  1 rt2800pci
rt2x00mmio             13395  2 rt2800pci,rt2800mmio
rt2x00lib              48794  5 rt2x00pci,rt2800lib,rt2800pci,rt2800mmio,rt2x00mmio
mac80211              567098  3 rt2x00lib,rt2x00pci,rt2800lib
cfg80211              430618  2 mac80211,rt2x00lib
eeprom_93cx6           13168  1 rt2800pci
crc_ccitt              12627  1 rt2800lib
wmi                    18689  1 msi_wmi


module parameters ~~~~~~~~~~~~~~~~~~

cfg80211      (2): 
mac80211      (5): 
rt2800pci     (1): 
wmi           (2): 


nm-tool ~~~~~~~~~~~~~~~~~~~~~~~~~~~~

State: connected (global)
============================o=============o===========o=============o=========o===========o==============o===========
 Interface & ID             | Type        | Driver    | State       | Default | Speed     | Support      | HW Addr   
============================o=============o===========o=============o=========o===========o==============o===========
 eth0  [Wired connection 1] | Wired       | r8169     | connected   | yes     | 100 Mb/s  |              | <MAC eth0>

    Address:         192.168.2.111
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.2.1
    DNS:             192.168.2.1
----------------------------+-------------+-----------+-------------+---------+-----------+--------------+-----------
 wlan0                      | 802.11 WiFi | rt2800pci | unavailable | no      |           | WEP/WPA/WPA2 | <MAC wlan0>
----------------------------+-------------+-----------+-------------+---------+-----------+--------------+-----------


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
 


interfaces ~~~~~~~~~~~~~~~~~~~~~~~~~

# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback

resolv.conf ~~~~~~~~~~~~~~~~~~~~~~~~

nameserver 127.0.1.1


Routes & Ping ~~~~~~~~~~~~~~~~~~~~~~

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.2.1     0.0.0.0         UG    0      0        0 eth0
192.168.2.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0

--- 192.168.2.1 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 1001ms
rtt min/avg/max/mdev = 0.615/0.742/0.870/0.130 ms

--- 127.0.1.1 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 999ms
rtt min/avg/max/mdev = 0.043/0.043/0.043/0.000 ms


iw reg get ~~~~~~~~~~~~~~~~~~~~~~~~~

(Region : "de_DE.UTF-8")


iwlist chan ~~~~~~~~~~~~~~~~~~~~~~~~

wlan0     14 channels in total; available frequencies :
          Channel 01 (2.412 GHz) - 14 (2.484 GHz)


iwlist scan ~~~~~~~~~~~~~~~~~~~~~~~~



blacklist ~~~~~~~~~~~~~~~~~~~~~~~~~~

[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci

[/etc/modprobe.d/libpisock9.conf]
blacklist visor


modinfo ~~~~~~~~~~~~~~~~~~~~~~~~~~~~

[msi_wmi]
filename:       /lib/modules/3.16.0-23-generic/kernel/drivers/platform/x86/msi-wmi.ko
srcversion:     DDF9307A2E9F8A49A15BC8E
depends:        wmi,sparse-keymap

[rt2800pci]
filename:       /lib/modules/3.16.0-23-generic/kernel/drivers/net/wireless/rt2x00/rt2800pci.ko
firmware:       rt2860.bin
version:        2.3.0
srcversion:     F8D3E83728CFFB1CC77557E
depends:        rt2x00lib,rt2800lib,rt2800mmio,rt2x00mmio,rt2x00pci,eeprom_93cx6
parm:           nohwcrypt:Disable hardware encryption. (bool)

[rt2800mmio]
filename:       /lib/modules/3.16.0-23-generic/kernel/drivers/net/wireless/rt2x00/rt2800mmio.ko
version:        2.3.0
srcversion:     63729A11A0371D38A62802F
depends:        rt2800lib,rt2x00lib,rt2x00mmio

[rt2800lib]
filename:       /lib/modules/3.16.0-23-generic/kernel/drivers/net/wireless/rt2x00/rt2800lib.ko
version:        2.3.0
srcversion:     8D9F59A658EAF90D8F1EF97
depends:        rt2x00lib,mac80211,crc-ccitt

[rt2x00pci]
filename:       /lib/modules/3.16.0-23-generic/kernel/drivers/net/wireless/rt2x00/rt2x00pci.ko
version:        2.3.0
srcversion:     7856EF56F97508465F566A2
depends:        rt2x00lib,mac80211

[rt2x00mmio]
filename:       /lib/modules/3.16.0-23-generic/kernel/drivers/net/wireless/rt2x00/rt2x00mmio.ko
version:        2.3.0
srcversion:     37A76810C0FE9E4E11476DA
depends:        rt2x00lib

[rt2x00lib]
filename:       /lib/modules/3.16.0-23-generic/kernel/drivers/net/wireless/rt2x00/rt2x00lib.ko
version:        2.3.0
srcversion:     02B2F4D2982AACC016889FC
depends:        mac80211,cfg80211

[mac80211]
filename:       /lib/modules/3.16.0-23-generic/kernel/net/mac80211/mac80211.ko
srcversion:     0D5DBE66E4CC44B010DB516
depends:        cfg80211
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[cfg80211]
filename:       /lib/modules/3.16.0-23-generic/kernel/net/wireless/cfg80211.ko
srcversion:     DEE8EAA48495E392CD51C2D
depends:        
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

[eeprom_93cx6]
filename:       /lib/modules/3.16.0-23-generic/kernel/drivers/misc/eeprom/eeprom_93cx6.ko
version:        1.0
srcversion:     215D8C1284A3C33B4A5A1C5
depends:        

[crc_ccitt]
filename:       /lib/modules/3.16.0-23-generic/kernel/lib/crc-ccitt.ko
srcversion:     2294FCAD06D727386004EEB
depends:        

[wmi]
filename:       /lib/modules/3.16.0-23-generic/kernel/drivers/platform/x86/wmi.ko
srcversion:     347CF30B94B5549A75865A8
depends:        
parm:           debug_event:Log WMI Events [0/1] (bool)
parm:           debug_dump_wdg:Dump available WMI interfaces [0/1] (bool)


udev rules ~~~~~~~~~~~~~~~~~~~~~~~~~

# PCI device 0x10ec:0x8168 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC eth0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

# PCI device 0x1814:0x3090 (rt2800pci)
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
modesetting.conf  : options cirrus modeset=1
                    options mgag200 modeset=1


Kernel boot line ~~~~~~~~~~~~~~~~~~~

BOOT_IMAGE=/boot/vmlinuz-3.16.0-23-generic root=UUID=f39b3af7-da58-434c-82b7-23362ea0a716 ro quiet splash vt.handoff=7


dmesg ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

[    0.016162] Initializing cgroup subsys net_cls
[    0.016178] Initializing cgroup subsys net_prio
[    1.434560] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[    1.435027] audit: initializing netlink subsys (disabled)
[    2.114409] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[   12.879361] wmi: Mapper loaded
[   13.882474] ieee80211 phy0: rt2x00_set_rt: Info - RT chipset 3090, rev 3212 detected
[   13.886381] ieee80211 phy0: rt2x00_set_rf: Info - RF chipset 0005 detected
[   17.730228] Bluetooth: BNEP (Ethernet Emulation) ver 1.3

    ======== Done ========


```

---

