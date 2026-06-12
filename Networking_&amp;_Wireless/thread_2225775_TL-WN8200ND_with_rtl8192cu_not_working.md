---
title: "TL-WN8200ND with rtl8192cu not working"
date: 2014-05-23
forum: Networking &amp; Wireless
---

### Post by schribl on 2014-05-23
Hello everybody,

I installed the rtl8192cu driver from this repository: [https://github.com/dz0ny/rt8192cu](https://github.com/dz0ny/rt8192cu)

However, when trying to connect to the router it keeps asking for the password forever.

This is the output of the network-script:
```


	======== Wireless-Info START ========

System-Info ~~~~~~~~~~~~~~~~~~~~~~~~

thomas-PC 3.13.0-24-generic x86_64,  Ubuntu 14.04 LTS, trusty

CPU    : Intel(R) Core(TM) i7 CPU         860  @ 2.80GHz
Memory : 7975 MB
Uptime : 13:18:32 up 41 min,  4 users,  load average: 0,52, 0,40, 0,42


lspci ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

05:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 03)
	Subsystem: ASUSTeK Computer Inc. Device [1043:833a]
	Kernel driver in use: r8169
06:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 03)
	Subsystem: ASUSTeK Computer Inc. Device [1043:833a]
	Kernel driver in use: r8169


lsusb ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Bus 002 Device 006: ID 0fcf:1009 Dynastream Innovations, Inc. 
Bus 002 Device 007: ID 046d:c21f Logitech, Inc. F710 Wireless Gamepad [XInput Mode]
Bus 002 Device 005: ID 0424:2514 Standard Microsystems Corp. USB 2.0 Hub
Bus 002 Device 004: ID 041e:0403 Creative Technology, Ltd 
Bus 002 Device 003: ID 2357:0100  
Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


PCMCIA Card Info ~~~~~~~~~~~~~~~~~~~



iwconfig ~~~~~~~~~~~~~~~~~~~~~~~~~~~

wlan0     unassociated  Nickname:"<WIFI@REALTEK>"
          Mode:Managed  Frequency=2.447 GHz  Access Point: Not-Associated   
          Sensitivity:0/0  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0



rfkill ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~




lsmod ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

8192cu                628511  0 


module parameters ~~~~~~~~~~~~~~~~~~

8192cu       (37): if2name=wlan0 | ifname=wlan0 | rtw_80211d=0 | rtw_ampdu_amsdu=0 | rtw_ampdu_enable=1 | rtw_antdiv_cfg=2 | rtw_busy_thresh=40 | rtw_cbw40_enable=3 | rtw_channel=1 | rtw_channel_plan=65 | rtw_chip_version=0 | rtw_enusbss=0 | rtw_force_iol=N | rtw_ht_enable=1 | rtw_hwpdn_mode=2 | rtw_hwpwrp_detect=0 | rtw_hw_wps_pbc=1 | rtw_initmac=(null) | rtw_ips_mode=1 | rtw_lbkmode=0 | rtw_low_power=0 | rtw_lowrate_two_xmit=1 | rtw_mac_phy_mode=0 | rtw_max_roaming_times=2 | rtw_mc2u_disable=0 | rtw_mp_mode=0 | rtw_network_mode=0 | rtw_notch_filter=0 | rtw_power_mgnt=1 | rtw_rf_config=5 | rtw_rfintfs=2 | rtw_rx_stbc=1 | rtw_special_rf_path=0 | rtw_vcs_type=1 | rtw_vrtl_carrier_sense=2 | rtw_wifi_spec=0 | rtw_wmm_enable=1


nm-tool ~~~~~~~~~~~~~~~~~~~~~~~~~~~~

State: connected (global)
============================o=============o===========o==============o=========o===========o==============o===========
 Interface & ID             | Type        | Driver    | State        | Default | Speed     | Support      | HW Addr   
============================o=============o===========o==============o=========o===========o==============o===========
 wlan0                      | 802.11 WiFi | rtl8192cu | disconnected | no      |           | WEP/WPA/WPA2 | <MAC wlan0>

    FRITZ!Box Fon WLAN 7390: Infra, <MAC C-01 FRITZ!Box Fon WLAN 7390>, Freq 2412 MHz, Rate 44 Mb/s, Strength 72 WPA WPA2
    Homeland:        Infra, <MAC C-02 Homeland>, Freq 2447 MHz, Rate 44 Mb/s, Strength 96 WPA2
----------------------------+-------------+-----------+--------------+---------+-----------+--------------+-----------
 eth1  [Wired connection 2] | Wired       | r8169     | connected    | yes     | 100 Mb/s  |              | <MAC eth1>

    Address:         192.168.1.21
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1
    DNS:             192.168.1.1
----------------------------+-------------+-----------+--------------+---------+-----------+--------------+-----------
 eth0                       | Wired       | r8169     | unavailable  | no      |           |              | <MAC eth0>
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

Homeland             : ssid=Homeland | permissions=user:thomas:; | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 
Homeland             : ssid=Homeland | permissions=user:thomas:; | mac-address=<MAC wlan0> | ipv6=auto | ipv4=auto 


interfaces ~~~~~~~~~~~~~~~~~~~~~~~~~

# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback

resolv.conf ~~~~~~~~~~~~~~~~~~~~~~~~

nameserver 127.0.1.1
search localdomain


Routes & Ping ~~~~~~~~~~~~~~~~~~~~~~

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 eth1
192.168.1.0     0.0.0.0         255.255.255.0   U     1      0        0 eth1

--- 192.168.1.1 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 1001ms
rtt min/avg/max/mdev = 135.464/137.097/138.730/1.633 ms

--- 127.0.1.1 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 999ms
rtt min/avg/max/mdev = 0.016/0.019/0.023/0.005 ms


iw reg get ~~~~~~~~~~~~~~~~~~~~~~~~~

(Region : de_DE.UTF-8)
country 00:
	(2402 - 2472 @ 40), (3, 20)
	(2457 - 2482 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
	(2474 - 2494 @ 20), (3, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
	(5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
	(5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS


iwlist chan ~~~~~~~~~~~~~~~~~~~~~~~~

wlan0     13 channels in total; available frequencies :
          Channel 01 (2.412 GHz) - 13 (2.472 GHz)

          Current Frequency:2.447 GHz (Channel 8)


iwlist scan ~~~~~~~~~~~~~~~~~~~~~~~~

wlan0     Scan completed :
          Cell 01 - Address: <MAC C-01 FRITZ!Box Fon WLAN 7390>
                    ESSID:"FRITZ!Box Fon WLAN 7390"
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Encryption key:on
                    Bit Rates:300 Mb/s
                    Extra:wpa_ie=dd160050f20101000050f20201000050f20201000050f202
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    Extra:rsn_ie=30140100000fac020100000fac040100000fac020000
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    Quality=100/100  Signal level=70/100  
          Cell 02 - Address: <MAC C-02 Homeland>
                    ESSID:"Homeland"
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.447 GHz (Channel 8)
                    Encryption key:on
                    Bit Rates:300 Mb/s
                    Extra:rsn_ie=30140100000fac040100000fac040100000fac020100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                       Preauthentication Supported
                    Quality=100/100  Signal level=100/100  


blacklist ~~~~~~~~~~~~~~~~~~~~~~~~~~

[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci

[/etc/modprobe.d/blacklist.conf]
blacklist rtl8192cu

[/etc/modprobe.d/blacklist-native-rtl8192.conf]
blacklist rtl8192cu
blacklist rtl8192c_common
blacklist rtlwifi


modinfo ~~~~~~~~~~~~~~~~~~~~~~~~~~~~

[8192cu]
filename:       /lib/modules/3.13.0-24-generic/updates/dkms/8192cu.ko
version:        v4.0.2_9000.20130911
srcversion:     98913FB8609F2F16E0996C2
depends:        
parm:           rtw_ips_mode:The default IPS mode (int)
parm:           ifname:The default name to allocate for first interface (charp)
parm:           if2name:The default name to allocate for second interface (charp)
parm:           rtw_initmac:charp
parm:           rtw_channel_plan:int
parm:           rtw_chip_version:int
parm:           rtw_rfintfs:int
parm:           rtw_lbkmode:int
parm:           rtw_network_mode:int
parm:           rtw_channel:int
parm:           rtw_mp_mode:int
parm:           rtw_wmm_enable:int
parm:           rtw_vrtl_carrier_sense:int
parm:           rtw_vcs_type:int
parm:           rtw_busy_thresh:int
parm:           rtw_ht_enable:int
parm:           rtw_cbw40_enable:int
parm:           rtw_ampdu_enable:int
parm:           rtw_rx_stbc:int
parm:           rtw_ampdu_amsdu:int
parm:           rtw_lowrate_two_xmit:int
parm:           rtw_rf_config:int
parm:           rtw_power_mgnt:int
parm:           rtw_low_power:int
parm:           rtw_wifi_spec:int
parm:           rtw_special_rf_path:int
parm:           rtw_antdiv_cfg:int
parm:           rtw_enusbss:int
parm:           rtw_hwpdn_mode:int
parm:           rtw_hwpwrp_detect:int
parm:           rtw_hw_wps_pbc:int
parm:           rtw_max_roaming_times:The max roaming times to try (uint)
parm:           rtw_force_iol:Force to enable IOL (bool)
parm:           rtw_mc2u_disable:int
parm:           rtw_mac_phy_mode:int
parm:           rtw_80211d:int
parm:           rtw_notch_filter:0:Disable, 1:Enable, 2:Enable only for P2P (uint)


udev rules ~~~~~~~~~~~~~~~~~~~~~~~~~

# PCI device 0x10ec:0x8168 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC eth1>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth1"

# PCI device 0x10ec:0x8168 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC eth0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

# USB device 0x:0x (rtl8192cu)
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

BOOT_IMAGE=/vmlinuz-3.13.0-24-generic root=UUID=03002a85-e9bc-4724-aa5c-bd8f674f6a62 ro quiet splash


dmesg ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

[    0.866545] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[    0.866885] audit: initializing netlink socket (disabled)
[    1.846509] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    1.846860] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    1.847139] r8169 0000:05:00.0 eth1: RTL8168d/8111d at 0xffffc90000c6c000, <MAC eth1>, XID 083000c0 IRQ 46
[    1.847141] r8169 0000:05:00.0 eth1: jumbo features [frames: 9200 bytes, tx checksumming: ko]
[   11.176461] IPv6: ADDRCONF(NETDEV_UP): eth1: link is not ready
[   11.686618] rtl8192cu driver version=v4.0.2_9000.20130911
[   11.686675] register rtw_netdev_ops to netdev_ops
[   11.827098] _rtw_drv_register_netdev, MAC Address (if1) = <MAC wlan0>
[   12.742234] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   13.322448] r8169 0000:05:00.0 eth1: link down
[   13.322466] r8169 0000:05:00.0 eth1: link down
[   13.322480] IPv6: ADDRCONF(NETDEV_UP): eth1: link is not ready
[   13.323003] IPv6: ADDRCONF(NETDEV_UP): eth1: link is not ready
[   13.339850] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   14.921184] r8169 0000:05:00.0 eth1: link up
[   14.921193] IPv6: ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
[ 1908.274659] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1908.274800] IPv6: ADDRCONF(NETDEV_UP): eth1: link is not ready
[ 1908.517184] r8169 0000:05:00.0 eth1: link down
[ 1908.517194] r8169 0000:05:00.0 eth1: link down
[ 1908.517215] IPv6: ADDRCONF(NETDEV_UP): eth1: link is not ready
[ 1908.517562] IPv6: ADDRCONF(NETDEV_UP): eth1: link is not ready
[ 1908.518872] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1910.095325] r8169 0000:05:00.0 eth1: link up
[ 1910.095337] IPv6: ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
[ 1928.679868] rtl8192cu_hal_init in 572ms
[ 1928.693112] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1979.726054] issue_deauth_ex(wlan0) to <MAC C-02 Homeland>, ch:8, 5/5 in 496 ms
[ 1981.261577] rtl8192c_set_FwJoinBssReport_cmd mstatus(0)
[ 1983.208445] issue_deauth_ex(wlan0) to <MAC C-02 Homeland>, ch:8, 5/5 in 512 ms
[ 1984.751854] rtl8192c_set_FwJoinBssReport_cmd mstatus(0)
[ 1986.683012] issue_deauth_ex(wlan0) to <MAC C-02 Homeland>, ch:8, 5/5 in 496 ms
[ 1988.234055] rtl8192c_set_FwJoinBssReport_cmd mstatus(0)
[ 1990.160980] issue_deauth_ex(wlan0) to <MAC C-02 Homeland>, ch:8, 5/5 in 496 ms
[ 1991.716367] rtl8192c_set_FwJoinBssReport_cmd mstatus(0)
[ 1995.267993] ==> rtl8192cu_hal_deinit 
[ 1998.146590] ===> ips_netdrv_open.........
[ 1998.717700] rtl8192cu_hal_init in 572ms
[ 2000.759130] ==> rtl8192cu_hal_deinit 
[ 2015.259115] ===> ips_netdrv_open.........
[ 2015.832967] rtl8192cu_hal_init in 576ms
[ 2017.695089] issue_deauth_ex(wlan0) to <MAC C-02 Homeland>, ch:8, 5/5 in 500 ms
[ 2019.294405] rtl8192c_set_FwJoinBssReport_cmd mstatus(0)
[ 2023.891779] ==> rtl8192cu_hal_deinit 
[ 2025.729283] ===> ips_netdrv_open.........
[ 2026.305828] rtl8192cu_hal_init in 576ms
[ 2028.348454] ==> rtl8192cu_hal_deinit 
[ 2032.652474] ===> ips_netdrv_open.........
[ 2033.226311] rtl8192cu_hal_init in 576ms
[ 2035.073000] issue_deauth_ex(wlan0) to <MAC C-02 Homeland>, ch:8, 5/5 in 496 ms
[ 2036.621275] rtl8192c_set_FwJoinBssReport_cmd mstatus(0)
[ 2041.287657] ==> rtl8192cu_hal_deinit 
[ 2042.253284] ===> ips_netdrv_open.........
[ 2042.821031] rtl8192cu_hal_init in 568ms
[ 2044.863764] ==> rtl8192cu_hal_deinit 
[ 2045.521419] ===> ips_netdrv_open.........
[ 2046.092670] rtl8192cu_hal_init in 572ms
[ 2048.135428] ==> rtl8192cu_hal_deinit 
[ 2068.550680] ===> ips_netdrv_open.........
[ 2069.119438] rtl8192cu_hal_init in 568ms
[ 2071.161996] ==> rtl8192cu_hal_deinit 
[ 2101.587859] ===> ips_netdrv_open.........
[ 2102.157687] rtl8192cu_hal_init in 572ms
[ 2104.200297] ==> rtl8192cu_hal_deinit 
[ 2144.634814] ===> ips_netdrv_open.........
[ 2145.210923] rtl8192cu_hal_init in 576ms
[ 2147.253860] ==> rtl8192cu_hal_deinit 
[ 2197.695671] ===> ips_netdrv_open.........
[ 2198.271883] rtl8192cu_hal_init in 576ms
[ 2200.314409] ==> rtl8192cu_hal_deinit 
[ 2260.773167] ===> ips_netdrv_open.........
[ 2261.364736] rtl8192cu_hal_init in 592ms
[ 2263.407881] ==> rtl8192cu_hal_deinit 
[ 2323.844259] ===> ips_netdrv_open.........
[ 2324.421929] rtl8192cu_hal_init in 576ms
[ 2326.464215] ==> rtl8192cu_hal_deinit 
[ 2386.919856] ===> ips_netdrv_open.........
[ 2387.493846] rtl8192cu_hal_init in 576ms
[ 2389.536935] ==> rtl8192cu_hal_deinit 
[ 2449.986765] ===> ips_netdrv_open.........
[ 2450.562539] rtl8192cu_hal_init in 576ms
[ 2452.605358] ==> rtl8192cu_hal_deinit 
[ 2501.132600] ===> ips_netdrv_open.........
[ 2501.713361] rtl8192cu_hal_init in 580ms

	======== Done ========

```

If more information is needed I will provide it!

Thanks!

---

### Post by varunendra on 2014-05-27
Welcome to the forums schribl!

Please try this driver : [https://github.com/pvaret/rtl8192cu-fixes](https://github.com/pvaret/rtl8192cu-fixes)

And in the router, try setting the channel to 1 or 11. Reboot the router after saving the change.

If this makes no difference, please post back a fresh report of the wireless_script.

---

