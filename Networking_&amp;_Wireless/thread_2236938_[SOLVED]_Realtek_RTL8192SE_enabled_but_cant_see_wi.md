---
title: "[SOLVED] Realtek RTL8192SE enabled but cant see wifi networks"
date: 2014-07-29
forum: Networking &amp; Wireless
---

### Post by razor7 on 2014-07-29
Hi I just finished installing Lubuntu 14.04 on my netbook and works great! In the installation process I have enabled wifi and all the update proccess was made through it.

After installation finished, I rebooted, but the WIFI stopped working!

I managed to add Network Manager Applet and my WIFI adapter appears there, but when clicking the WIFI icon, no networks appear!

I'm really missed here, because on installation, my WIFI was working just fine, but after reboot, is stopped working

Here is the output of Wireless Info Script
```

	======== Wireless-Info START ========

System-Info ~~~~~~~~~~~~~~~~~~~~~~~~

chabela-netbook 3.13.0-24-generic x86_64,  Ubuntu 14.04.1 LTS, trusty

CPU    : Intel(R) Atom(TM) CPU N450   @ 1.66GHz
Memory : 983 MB
Uptime : 20:46:35 up  2:21,  2 users,  load average: 0,96, 0,63, 0,61


lspci ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

07:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 02)
	Subsystem: Elitegroup Computer Systems Device [1019:90c0]
	Kernel driver in use: r8169
09:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8191SEvB Wireless LAN Controller [10ec:8172] (rev 10)
	Subsystem: Realtek Semiconductor Co., Ltd. RTL8191SEvB Wireless LAN Controller [10ec:8172]
	Kernel driver in use: rtl8192se


lsusb ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Bus 001 Device 002: ID 04f2:b191 Chicony Electronics Co., Ltd 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


PCMCIA Card Info ~~~~~~~~~~~~~~~~~~~



iwconfig ~~~~~~~~~~~~~~~~~~~~~~~~~~~

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          


rfkill ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

      Interface               Soft blocked  Hard blocked
0: cmpc_rfkill: Wireless LAN      no            no
1: phy0: Wireless LAN             no            no


lsmod ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

rtl8192se              63196  0 
rtl_pci                26690  1 rtl8192se
rtlwifi                63475  2 rtl_pci,rtl8192se
mac80211              626489  3 rtl_pci,rtlwifi,rtl8192se
cfg80211              484040  2 mac80211,rtlwifi


module parameters ~~~~~~~~~~~~~~~~~~

cfg80211      (2): cfg80211_disable_40mhz_24ghz=N | ieee80211_regdom=00
mac80211      (5): beacon_loss_count=7 | ieee80211_default_rc_algo=minstrel_ht | max_nullfunc_tries=2 | max_probe_tries=5 | probe_wait_ms=500
rtl8192se     (5): debug=0 | fwlps=N | ips=Y | swenc=N | swlps=Y


nm-tool ~~~~~~~~~~~~~~~~~~~~~~~~~~~~

State: connected (global)
=============================o=============o===========o==============o=========o===========o==============o===========
 Interface & ID              | Type        | Driver    | State        | Default | Speed     | Support      | HW Addr   
=============================o=============o===========o==============o=========o===========o==============o===========
 wlan0                       | 802.11 WiFi | rtl8192se | disconnected | no      |           | WEP/WPA/WPA2 | <MAC wlan0>
-----------------------------+-------------+-----------+--------------+---------+-----------+--------------+-----------
 eth0  [Conexión cableada 1]| Wired       | r8169     | connected    | yes     | 100 Mb/s  |              | <MAC eth0>

    Address:         10.0.0.102
    Prefix:          24 (255.255.255.0)
    Gateway:         10.0.0.1
    DNS:             208.67.222.222
    DNS:             208.67.220.220
-----------------------------+-------------+-----------+--------------+---------+-----------+--------------+-----------


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

Tabla de rutas IP del núcleo
Destino         Pasarela        Genmask         Indic Métric Ref    Uso Interfaz
0.0.0.0         10.0.0.1        0.0.0.0         UG    0      0        0 eth0
10.0.0.0        0.0.0.0         255.255.255.0   U     1      0        0 eth0

--- 10.0.0.1 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 999ms
rtt min/avg/max/mdev = 0.583/0.619/0.655/0.036 ms

--- 127.0.1.1 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 999ms
rtt min/avg/max/mdev = 0.088/0.088/0.089/0.009 ms


iw reg get ~~~~~~~~~~~~~~~~~~~~~~~~~

(Region : "es_AR.UTF-8")


iwlist chan ~~~~~~~~~~~~~~~~~~~~~~~~

wlan0     13 channels in total; available frequencies :
          Channel 01 (2.412 GHz) - 13 (2.472 GHz)


iwlist scan ~~~~~~~~~~~~~~~~~~~~~~~~

wlan0     No scan results


blacklist ~~~~~~~~~~~~~~~~~~~~~~~~~~

[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci

[/etc/modprobe.d/libpisock9.conf]
blacklist visor


modinfo ~~~~~~~~~~~~~~~~~~~~~~~~~~~~

[rtl8192se]
filename:       /lib/modules/3.13.0-24-generic/kernel/drivers/net/wireless/rtlwifi/rtl8192se/rtl8192se.ko
firmware:       rtlwifi/rtl8192sefw.bin
srcversion:     B9B9518158623D8BAB67493
depends:        rtlwifi,rtl_pci,mac80211
parm:           swenc:Set to 1 for software crypto (default 0)
parm:           ips:Set to 0 to not use link power save (default 1)
parm:           swlps:Set to 1 to use SW control power save (default 0)
parm:           fwlps:Set to 1 to use FW control power save (default 1)
parm:           debug:Set debug level (0-5) (default 0) (int)

[rtl_pci]
filename:       /lib/modules/3.13.0-24-generic/kernel/drivers/net/wireless/rtlwifi/rtl_pci.ko
srcversion:     B6B8AA929B5F982954A6DE1
depends:        mac80211,rtlwifi

[rtlwifi]
filename:       /lib/modules/3.13.0-24-generic/kernel/drivers/net/wireless/rtlwifi/rtlwifi.ko
srcversion:     C21FC2F90947540319DE390
depends:        mac80211,cfg80211

[mac80211]
filename:       /lib/modules/3.13.0-24-generic/kernel/net/mac80211/mac80211.ko
srcversion:     C0F95BBF832E05DEFD722F4
depends:        cfg80211
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[cfg80211]
filename:       /lib/modules/3.13.0-24-generic/kernel/net/wireless/cfg80211.ko
srcversion:     8B3D642D1F2E6406EF33F74
depends:        
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)


udev rules ~~~~~~~~~~~~~~~~~~~~~~~~~

# PCI device 0x10ec:0x8136 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC eth0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

# PCI device 0x10ec:0x8172 (rtl8192se)
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

BOOT_IMAGE=/boot/vmlinuz-3.13.0-24-generic root=UUID=75c73ec1-5611-4781-be4e-8645940a570e ro quiet splash vt.handoff=7


dmesg ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

[    0.982893] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[    0.983617] audit: initializing netlink socket (disabled)
[    1.771562] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[   10.520089] rtl8192se: FW Power Save off (module option)
[   10.520249] rtl8192se: Driver for Realtek RTL8192SE/RTL8191SE
[   10.520249] Loading firmware rtlwifi/rtl8192sefw.bin
[   10.819415] ieee80211 phy0: Selected rate control algorithm 'rtl_rc'
[   18.633719] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   21.878167] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   21.879819] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 7593.140236] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready

	======== Done ========

```

Thanks in advise!

---

### Post by razor7 on 2014-07-29
Hi, well, after rebooting several times, I got the Connections Manager system tray icon and was able to connect to my wifi networks.

Thanks anyway.

---

