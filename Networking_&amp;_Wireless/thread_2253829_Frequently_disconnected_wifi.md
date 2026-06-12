---
title: "Frequently disconnected wifi"
date: 2014-11-22
forum: Networking &amp; Wireless
---

### Post by starkshaw on 2014-11-22
Hi all,
      I am currently using Ubuntu 14.04 LTS and my WIFI status is pretty unstable. Frequently disconnected, approx. 10 minutes per time. I had met this problem when I use 13.10 in last year. And normally need to disable WIFI and turn it on again to connect again. How to deal with this issue? It seems I have to stay with Ubuntu for study in a while so I need to figure out what can I do. Does anyone have some idea?

      Here are some hardware information

 ```


    ======== Wireless-Info START ========


System-Info ~~~~~~~~~~~~~~~~~~~~~~~~


stark-jarvis 3.13.0-32-generic x86_64,  Ubuntu 14.04.1 LTS, trusty


CPU    : Intel(R) Core(TM) i7-4700MQ CPU @ 2.40GHz
Memory : 15969 MB
Uptime : 17:14:37 up 38 min,  2 users,  load average: 0.21, 0.43, 0.66




lspci ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~


03:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8723AE PCIe Wireless Network Adapter [10ec:8723]
    Subsystem: Realtek Semiconductor Co., Ltd. Device [10ec:0726]
    Kernel driver in use: rtl8723ae
--
04:00.1 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 12)
    Subsystem: CLEVO/KAPOK Computer Device [1558:0230]
    Kernel driver in use: r8169




lsusb ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~


Bus 002 Device 002: ID 8087:8000 Intel Corp. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:8008 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 004: ID 0bda:8723 Realtek Semiconductor Corp. 
Bus 003 Device 003: ID 1bcf:08d9 Sunplus Innovation Technology Inc. 
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub




PCMCIA Card Info ~~~~~~~~~~~~~~~~~~~






iwconfig ~~~~~~~~~~~~~~~~~~~~~~~~~~~


wlan0     IEEE 802.11bgn  ESSID:"eircom87005608"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: <MAC C-01 eircom87005608>   
          Bit Rate=18 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          Link Quality=30/70  Signal level=-80 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:10   Missed beacon:0






rfkill ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~


      Interface        Soft blocked  Hard blocked
0: hci0: Bluetooth         no            no
1: phy0: Wireless LAN      no            no




lsmod ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~


rtl8723ae              81882  0 
rtl8723_common         23361  1 rtl8723ae
rtl_pci                26690  1 rtl8723ae
rtlwifi                63475  2 rtl_pci,rtl8723ae
mac80211              630653  3 rtl_pci,rtlwifi,rtl8723ae
cfg80211              484040  2 mac80211,rtlwifi
mxm_wmi                13021  1 nouveau
wmi                    19177  2 mxm_wmi,nouveau




module parameters ~~~~~~~~~~~~~~~~~~


cfg80211      (2): cfg80211_disable_40mhz_24ghz=N | ieee80211_regdom=00
mac80211      (5): beacon_loss_count=7 | ieee80211_default_rc_algo=minstrel_ht | max_nullfunc_tries=2 | max_probe_tries=5 | probe_wait_ms=500
rtl8723ae     (5): debug=0 | fwlps=Y | ips=Y | swenc=N | swlps=N
wmi           (2): debug_dump_wdg=N | debug_event=N




nm-tool ~~~~~~~~~~~~~~~~~~~~~~~~~~~~


State: connected (global)
=========================o=============o===========o=============o=========o===========o==============o===========
 Interface & ID          | Type        | Driver    | State       | Default | Speed     | Support      | HW Addr   
=========================o=============o===========o=============o=========o===========o==============o===========
 eth0                    | Wired       | r8169     | unavailable | no      |           |              | <MAC eth0>
-------------------------+-------------+-----------+-------------+---------+-----------+--------------+-----------
 wlan0  [eircom87005608] | 802.11 WiFi | rtl8723ae | connected   | yes     | 18 Mb/s   | WEP/WPA/WPA2 | <MAC wlan0>


    *eircom87005608: Infra, <MAC C-01 eircom87005608>, Freq 2412 MHz, Rate 54 Mb/s, Strength 40 WPA


    Address:         192.168.1.5
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.254
    DNS:             192.168.1.254
-------------------------+-------------+-----------+-------------+---------+-----------+--------------+-----------




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


eircom87005608       : ssid=eircom87005608 | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 




interfaces ~~~~~~~~~~~~~~~~~~~~~~~~~


# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback


resolv.conf ~~~~~~~~~~~~~~~~~~~~~~~~


nameserver 127.0.1.1




Routes & Ping ~~~~~~~~~~~~~~~~~~~~~~


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.254   0.0.0.0         UG    0      0        0 wlan0
192.168.1.0     0.0.0.0         255.255.255.0   U     9      0        0 wlan0


--- 192.168.1.254 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 1001ms
rtt min/avg/max/mdev = 3.012/3.202/3.392/0.190 ms


--- 127.0.1.1 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 999ms
rtt min/avg/max/mdev = 0.034/0.037/0.041/0.007 ms




iw reg get ~~~~~~~~~~~~~~~~~~~~~~~~~


(Region : "en_IE.UTF-8")
country GB:
    (2402 - 2482 @ 40), (N/A, 20)
    (5170 - 5250 @ 40), (N/A, 20)
    (5250 - 5330 @ 40), (N/A, 20), DFS
    (5490 - 5710 @ 40), (N/A, 27), DFS
    (57240 - 65880 @ 2160), (N/A, 40), NO-OUTDOOR




iwlist chan ~~~~~~~~~~~~~~~~~~~~~~~~


wlan0     13 channels in total; available frequencies :
          Channel 01 (2.412 GHz) - 13 (2.472 GHz)


          Current Frequency:2.412 GHz (Channel 1)




iwlist scan ~~~~~~~~~~~~~~~~~~~~~~~~


wlan0     Scan completed :
          Cell 01 - Address: <MAC C-01 eircom87005608>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=30/70  Signal level=-80 dBm  
                    Encryption key:on
                    ESSID:"eircom87005608"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000005489f7612
                    Extra: Last beacon: 56ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK




blacklist ~~~~~~~~~~~~~~~~~~~~~~~~~~


[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci




modinfo ~~~~~~~~~~~~~~~~~~~~~~~~~~~~


[rtl8723ae]
filename:       /lib/modules/3.13.0-32-generic/kernel/drivers/net/wireless/rtlwifi/rtl8723ae/rtl8723ae.ko
firmware:       rtlwifi/rtl8723fw_B.bin
firmware:       rtlwifi/rtl8723fw.bin
srcversion:     618CBEE84D8321009FAA0B0
depends:        rtlwifi,rtl8723-common,rtl_pci,mac80211
parm:           swenc:Set to 1 for software crypto (default 0)
parm:           ips:Set to 0 to not use link power save (default 1)
parm:           swlps:Set to 1 to use SW control power save (default 0)
parm:           fwlps:Set to 1 to use FW control power save (default 1)
parm:           debug:Set debug level (0-5) (default 0) (int)


[rtl8723_common]
filename:       /lib/modules/3.13.0-32-generic/kernel/drivers/net/wireless/rtlwifi/rtl8723com/rtl8723-common.ko
srcversion:     D1807280DBDC9B8A7EBDAB7
depends:        


[rtl_pci]
filename:       /lib/modules/3.13.0-32-generic/kernel/drivers/net/wireless/rtlwifi/rtl_pci.ko
srcversion:     D5E4890DC428FA5A1BF92DF
depends:        mac80211,rtlwifi


[rtlwifi]
filename:       /lib/modules/3.13.0-32-generic/kernel/drivers/net/wireless/rtlwifi/rtlwifi.ko
srcversion:     E1F4663325225EE8DBA54CA
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


[mxm_wmi]
filename:       /lib/modules/3.13.0-32-generic/kernel/drivers/platform/x86/mxm-wmi.ko
srcversion:     62CBD37DE87DF0C4CD7FBA3
depends:        wmi


[wmi]
filename:       /lib/modules/3.13.0-32-generic/kernel/drivers/platform/x86/wmi.ko
srcversion:     CED5410F008DC70DF5F064B
depends:        
parm:           debug_event:Log WMI Events [0/1] (bool)
parm:           debug_dump_wdg:Dump available WMI interfaces [0/1] (bool)




udev rules ~~~~~~~~~~~~~~~~~~~~~~~~~


# PCI device 0x10ec:0x8168 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC eth0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"


# PCI device 0x10ec:0x8723 (rtl8723ae)
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


BOOT_IMAGE=/boot/vmlinuz-3.13.0-32-generic root=UUID=a5a60ae0-ea5c-40bd-8ed8-29d1ce1ac736 ro quiet splash vt.handoff=7




dmesg ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~


[    0.463786] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[    0.463977] audit: initializing netlink socket (disabled)
[    0.833811] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    9.127273] wmi: Mapper loaded
[   11.464914] rtl8723ae: Using firmware rtlwifi/rtl8723fw_B.bin
[   11.530699] ieee80211 phy0: Selected rate control algorithm 'rtl_rc'
[   11.530828] rtlwifi: wireless switch is on
[   15.622690] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   19.206653] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   19.581975] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   21.551129] wlan0: authenticate with <MAC C-01 eircom87005608>
[   21.560135] wlan0: send auth to <MAC C-01 eircom87005608> (try 1/3)
[   21.563070] wlan0: authenticated
[   21.563147] rtl8723ae 0000:03:00.0 wlan0: disabling HT/VHT due to WEP/TKIP use
[   21.563149] rtl8723ae 0000:03:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[   21.563150] rtl8723ae 0000:03:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[   21.563938] wlan0: associate with <MAC C-01 eircom87005608> (try 1/3)
[   21.566338] wlan0: RX AssocResp from <MAC C-01 eircom87005608> (capab=0x431 status=0 aid=2)
[   21.566578] wlan0: associated
[   21.566585] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   21.665113] wlan0: Limiting TX power to 20 (20 - 0) dBm as advertised by <MAC C-01 eircom87005608>
[  265.185767] wlan0: Connection to AP <MAC C-01 eircom87005608> lost
[  266.246453] wlan0: authenticate with <MAC C-01 eircom87005608>
[  266.262179] wlan0: send auth to <MAC C-01 eircom87005608> (try 1/3)
[  266.365994] wlan0: send auth to <MAC C-01 eircom87005608> (try 2/3)
[  266.470072] wlan0: send auth to <MAC C-01 eircom87005608> (try 3/3)
[  266.574062] wlan0: authentication with <MAC C-01 eircom87005608> timed out
[  268.015245] wlan0: authenticate with <MAC C-01 eircom87005608>
[  268.030788] wlan0: send auth to <MAC C-01 eircom87005608> (try 1/3)
[  268.134570] wlan0: send auth to <MAC C-01 eircom87005608> (try 2/3)
[  268.238606] wlan0: send auth to <MAC C-01 eircom87005608> (try 3/3)
[  268.342637] wlan0: authentication with <MAC C-01 eircom87005608> timed out
[  270.283861] wlan0: authenticate with <MAC C-01 eircom87005608>
[  270.299455] wlan0: send auth to <MAC C-01 eircom87005608> (try 1/3)
[  270.301373] wlan0: authenticated
[  270.301494] rtl8723ae 0000:03:00.0 wlan0: disabling HT/VHT due to WEP/TKIP use
[  270.301498] rtl8723ae 0000:03:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[  270.301501] rtl8723ae 0000:03:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[  270.303219] wlan0: associate with <MAC C-01 eircom87005608> (try 1/3)
[  270.305651] wlan0: RX AssocResp from <MAC C-01 eircom87005608> (capab=0x431 status=0 aid=3)
[  270.305894] wlan0: associated
[  270.349058] wlan0: Limiting TX power to 20 (20 - 0) dBm as advertised by <MAC C-01 eircom87005608>
[  291.245738] wlan0: Connection to AP <MAC C-01 eircom87005608> lost
[  292.658946] wlan0: authenticate with <MAC C-01 eircom87005608>
[  292.674360] wlan0: send auth to <MAC C-01 eircom87005608> (try 1/3)
[  292.675811] wlan0: authenticated
[  292.675951] rtl8723ae 0000:03:00.0 wlan0: disabling HT/VHT due to WEP/TKIP use
[  292.675955] rtl8723ae 0000:03:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[  292.675957] rtl8723ae 0000:03:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[  292.678088] wlan0: associate with <MAC C-01 eircom87005608> (try 1/3)
[  292.680512] wlan0: RX AssocResp from <MAC C-01 eircom87005608> (capab=0x431 status=0 aid=3)
[  292.680753] wlan0: associated
[  292.695759] wlan0: Limiting TX power to 20 (20 - 0) dBm as advertised by <MAC C-01 eircom87005608>
[  299.744358] wlan0: Connection to AP <MAC C-01 eircom87005608> lost
[  301.157291] wlan0: authenticate with <MAC C-01 eircom87005608>
[  301.172944] wlan0: send auth to <MAC C-01 eircom87005608> (try 1/3)
[  301.174533] wlan0: authenticated
[  301.174647] rtl8723ae 0000:03:00.0 wlan0: disabling HT/VHT due to WEP/TKIP use
[  301.174650] rtl8723ae 0000:03:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[  301.174652] rtl8723ae 0000:03:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[  301.176704] wlan0: associate with <MAC C-01 eircom87005608> (try 1/3)
[  301.179141] wlan0: RX AssocResp from <MAC C-01 eircom87005608> (capab=0x431 status=0 aid=3)
[  301.179400] wlan0: associated
[  301.203970] wlan0: Limiting TX power to 20 (20 - 0) dBm as advertised by <MAC C-01 eircom87005608>
[  496.679496] wlan0: Connection to AP <MAC C-01 eircom87005608> lost
[  498.093449] wlan0: authenticate with <MAC C-01 eircom87005608>
[  498.109370] wlan0: send auth to <MAC C-01 eircom87005608> (try 1/3)
[  498.110868] wlan0: authenticated
[  498.110969] rtl8723ae 0000:03:00.0 wlan0: disabling HT/VHT due to WEP/TKIP use
[  498.110972] rtl8723ae 0000:03:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[  498.110973] rtl8723ae 0000:03:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[  498.113208] wlan0: associate with <MAC C-01 eircom87005608> (try 1/3)
[  498.115602] wlan0: RX AssocResp from <MAC C-01 eircom87005608> (capab=0x431 status=0 aid=3)
[  498.115844] wlan0: associated
[  498.121448] wlan0: Limiting TX power to 20 (20 - 0) dBm as advertised by <MAC C-01 eircom87005608>
[  505.175441] wlan0: Connection to AP <MAC C-01 eircom87005608> lost
[  506.588002] wlan0: authenticate with <MAC C-01 eircom87005608>
[  506.603959] wlan0: send auth to <MAC C-01 eircom87005608> (try 1/3)
[  506.605411] wlan0: authenticated
[  506.605522] rtl8723ae 0000:03:00.0 wlan0: disabling HT/VHT due to WEP/TKIP use
[  506.605526] rtl8723ae 0000:03:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[  506.605528] rtl8723ae 0000:03:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[  506.607773] wlan0: associate with <MAC C-01 eircom87005608> (try 1/3)
[  506.610141] wlan0: RX AssocResp from <MAC C-01 eircom87005608> (capab=0x431 status=0 aid=3)
[  506.610385] wlan0: associated
[  506.629594] wlan0: Limiting TX power to 20 (20 - 0) dBm as advertised by <MAC C-01 eircom87005608>
[  513.670009] wlan0: Connection to AP <MAC C-01 eircom87005608> lost
[  515.082747] wlan0: authenticate with <MAC C-01 eircom87005608>
[  515.098613] wlan0: send auth to <MAC C-01 eircom87005608> (try 1/3)
[  515.100070] wlan0: authenticated
[  515.100193] rtl8723ae 0000:03:00.0 wlan0: disabling HT/VHT due to WEP/TKIP use
[  515.100196] rtl8723ae 0000:03:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[  515.100198] rtl8723ae 0000:03:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[  515.102409] wlan0: associate with <MAC C-01 eircom87005608> (try 1/3)
[  515.104819] wlan0: RX AssocResp from <MAC C-01 eircom87005608> (capab=0x431 status=0 aid=3)
[  515.105071] wlan0: associated
[  515.137756] wlan0: Limiting TX power to 20 (20 - 0) dBm as advertised by <MAC C-01 eircom87005608>
[  522.168623] wlan0: Connection to AP <MAC C-01 eircom87005608> lost
[  523.581296] wlan0: authenticate with <MAC C-01 eircom87005608>
[  523.597217] wlan0: send auth to <MAC C-01 eircom87005608> (try 1/3)
[  523.598679] wlan0: authenticated
[  523.598768] rtl8723ae 0000:03:00.0 wlan0: disabling HT/VHT due to WEP/TKIP use
[  523.598772] rtl8723ae 0000:03:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[  523.598774] rtl8723ae 0000:03:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[  523.601070] wlan0: associate with <MAC C-01 eircom87005608> (try 1/3)
[  523.603586] wlan0: RX AssocResp from <MAC C-01 eircom87005608> (capab=0x431 status=0 aid=3)
[  523.603845] wlan0: associated
[  523.645970] wlan0: Limiting TX power to 20 (20 - 0) dBm as advertised by <MAC C-01 eircom87005608>
[  530.667294] wlan0: Connection to AP <MAC C-01 eircom87005608> lost
[  532.079892] wlan0: authenticate with <MAC C-01 eircom87005608>
[  532.095845] wlan0: send auth to <MAC C-01 eircom87005608> (try 1/3)
[  532.097313] wlan0: authenticated
[  532.097435] rtl8723ae 0000:03:00.0 wlan0: disabling HT/VHT due to WEP/TKIP use
[  532.097438] rtl8723ae 0000:03:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[  532.097439] rtl8723ae 0000:03:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[  532.099611] wlan0: associate with <MAC C-01 eircom87005608> (try 1/3)
[  532.102048] wlan0: RX AssocResp from <MAC C-01 eircom87005608> (capab=0x431 status=0 aid=3)
[  532.102289] wlan0: associated
[  532.154062] wlan0: Limiting TX power to 20 (20 - 0) dBm as advertised by <MAC C-01 eircom87005608>
[  661.447379] wlan0: Connection to AP <MAC C-01 eircom87005608> lost
[  662.860074] wlan0: authenticate with <MAC C-01 eircom87005608>
[  662.875959] wlan0: send auth to <MAC C-01 eircom87005608> (try 1/3)
[  662.877374] wlan0: authenticated
[  662.877480] rtl8723ae 0000:03:00.0 wlan0: disabling HT/VHT due to WEP/TKIP use
[  662.877482] rtl8723ae 0000:03:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[  662.877483] rtl8723ae 0000:03:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[  662.879810] wlan0: associate with <MAC C-01 eircom87005608> (try 1/3)
[  662.882202] wlan0: RX AssocResp from <MAC C-01 eircom87005608> (capab=0x431 status=0 aid=3)
[  662.882455] wlan0: associated
[  662.954032] wlan0: Limiting TX power to 20 (20 - 0) dBm as advertised by <MAC C-01 eircom87005608>
[  687.987592] wlan0: Connection to AP <MAC C-01 eircom87005608> lost
[  689.404189] wlan0: authenticate with <MAC C-01 eircom87005608>
[  689.420196] wlan0: send auth to <MAC C-01 eircom87005608> (try 1/3)
[  689.421696] wlan0: authenticated
[  689.421775] rtl8723ae 0000:03:00.0 wlan0: disabling HT/VHT due to WEP/TKIP use
[  689.421777] rtl8723ae 0000:03:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[  689.421779] rtl8723ae 0000:03:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[  689.423943] wlan0: associate with <MAC C-01 eircom87005608> (try 1/3)
[  689.426340] wlan0: RX AssocResp from <MAC C-01 eircom87005608> (capab=0x431 status=0 aid=3)
[  689.426580] wlan0: associated
[  689.503562] wlan0: Limiting TX power to 20 (20 - 0) dBm as advertised by <MAC C-01 eircom87005608>
[  712.527068] wlan0: Connection to AP <MAC C-01 eircom87005608> lost
[  713.963855] wlan0: authenticate with <MAC C-01 eircom87005608>
[  713.979697] wlan0: send auth to <MAC C-01 eircom87005608> (try 1/3)
[  714.083544] wlan0: send auth to <MAC C-01 eircom87005608> (try 2/3)
[  714.187546] wlan0: send auth to <MAC C-01 eircom87005608> (try 3/3)
[  714.291597] wlan0: authentication with <MAC C-01 eircom87005608> timed out
[  715.732389] wlan0: authenticate with <MAC C-01 eircom87005608>
[  715.748233] wlan0: send auth to <MAC C-01 eircom87005608> (try 1/3)
[  715.852059] wlan0: send auth to <MAC C-01 eircom87005608> (try 2/3)
[  715.956063] wlan0: send auth to <MAC C-01 eircom87005608> (try 3/3)
[  716.060087] wlan0: authentication with <MAC C-01 eircom87005608> timed out
[  718.008936] wlan0: authenticate with <MAC C-01 eircom87005608>
[  718.024903] wlan0: send auth to <MAC C-01 eircom87005608> (try 1/3)
[  718.128726] wlan0: send auth to <MAC C-01 eircom87005608> (try 2/3)
[  718.232805] wlan0: send auth to <MAC C-01 eircom87005608> (try 3/3)
[  718.336807] wlan0: authentication with <MAC C-01 eircom87005608> timed out
[  728.564813] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  827.476306] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  829.378568] wlan0: authenticate with <MAC C-01 eircom87005608>
[  829.394497] wlan0: send auth to <MAC C-01 eircom87005608> (try 1/3)
[  829.396844] wlan0: authenticated
[  829.396949] rtl8723ae 0000:03:00.0 wlan0: disabling HT/VHT due to WEP/TKIP use
[  829.396953] rtl8723ae 0000:03:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[  829.396956] rtl8723ae 0000:03:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[  829.398340] wlan0: associate with <MAC C-01 eircom87005608> (try 1/3)
[  829.400675] wlan0: RX AssocResp from <MAC C-01 eircom87005608> (capab=0x431 status=0 aid=4)
[  829.400922] wlan0: associated
[  829.400932] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  829.426705] wlan0: Limiting TX power to 20 (20 - 0) dBm as advertised by <MAC C-01 eircom87005608>
[  835.483278] wlan0: Connection to AP <MAC C-01 eircom87005608> lost
[  835.515672] wlan0: authenticate with <MAC C-01 eircom87005608>
[  835.515748] wlan0: send auth to <MAC C-01 eircom87005608> (try 1/3)
[  835.619327] wlan0: send auth to <MAC C-01 eircom87005608> (try 2/3)
[  835.723407] wlan0: send auth to <MAC C-01 eircom87005608> (try 3/3)
[  835.827505] wlan0: authentication with <MAC C-01 eircom87005608> timed out
[  846.832627] wlan0: authenticate with <MAC C-01 eircom87005608>
[  846.848587] wlan0: send auth to <MAC C-01 eircom87005608> (try 1/3)
[  846.850228] wlan0: authenticated
[  846.850351] rtl8723ae 0000:03:00.0 wlan0: disabling HT/VHT due to WEP/TKIP use
[  846.850354] rtl8723ae 0000:03:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[  846.850355] rtl8723ae 0000:03:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[  846.852405] wlan0: associate with <MAC C-01 eircom87005608> (try 1/3)
[  846.856167] wlan0: RX AssocResp from <MAC C-01 eircom87005608> (capab=0x431 status=0 aid=4)
[  846.856410] wlan0: associated
[  846.955543] wlan0: Limiting TX power to 20 (20 - 0) dBm as advertised by <MAC C-01 eircom87005608>
[  853.529894] wlan0: Connection to AP <MAC C-01 eircom87005608> lost
[  853.570328] wlan0: authenticate with <MAC C-01 eircom87005608>
[  853.570423] wlan0: send auth to <MAC C-01 eircom87005608> (try 1/3)
[  853.673956] wlan0: send auth to <MAC C-01 eircom87005608> (try 2/3)
[  853.778022] wlan0: send auth to <MAC C-01 eircom87005608> (try 3/3)
[  853.882081] wlan0: authentication with <MAC C-01 eircom87005608> timed out
[  871.750297] wlan0: authenticate with <MAC C-01 eircom87005608>
[  871.764862] wlan0: send auth to <MAC C-01 eircom87005608> (try 1/3)
[  871.768677] wlan0: authenticated
[  871.768814] rtl8723ae 0000:03:00.0 wlan0: disabling HT/VHT due to WEP/TKIP use
[  871.768817] rtl8723ae 0000:03:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[  871.768819] rtl8723ae 0000:03:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[  871.772475] wlan0: associate with <MAC C-01 eircom87005608> (try 1/3)
[  871.776410] wlan0: RX AssocResp from <MAC C-01 eircom87005608> (capab=0x431 status=0 aid=3)
[  871.776668] wlan0: associated
[  871.967429] wlan0: Limiting TX power to 20 (20 - 0) dBm as advertised by <MAC C-01 eircom87005608>
[  925.752157] wlan0: Connection to AP <MAC C-01 eircom87005608> lost
[  927.162261] wlan0: authenticate with <MAC C-01 eircom87005608>
[  927.178160] wlan0: send auth to <MAC C-01 eircom87005608> (try 1/3)
[  927.179636] wlan0: authenticated
[  927.179756] rtl8723ae 0000:03:00.0 wlan0: disabling HT/VHT due to WEP/TKIP use
[  927.179760] rtl8723ae 0000:03:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[  927.179762] rtl8723ae 0000:03:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[  927.181963] wlan0: associate with <MAC C-01 eircom87005608> (try 1/3)
[  927.184392] wlan0: RX AssocResp from <MAC C-01 eircom87005608> (capab=0x431 status=0 aid=3)
[  927.184631] wlan0: associated
[  927.219138] wlan0: Limiting TX power to 20 (20 - 0) dBm as advertised by <MAC C-01 eircom87005608>
[  962.356026] wlan0: Connection to AP <MAC C-01 eircom87005608> lost
[  963.422119] wlan0: authenticate with <MAC C-01 eircom87005608>
[  963.437689] wlan0: send auth to <MAC C-01 eircom87005608> (try 1/3)
[  963.541518] wlan0: send auth to <MAC C-01 eircom87005608> (try 2/3)
[  963.645561] wlan0: send auth to <MAC C-01 eircom87005608> (try 3/3)
[  963.749766] wlan0: authentication with <MAC C-01 eircom87005608> timed out
[  965.192428] wlan0: authenticate with <MAC C-01 eircom87005608>
[  965.207987] wlan0: direct probe to <MAC C-01 eircom87005608> (try 1/3)
[  965.411912] wlan0: direct probe to <MAC C-01 eircom87005608> (try 2/3)
[  965.616256] wlan0: direct probe to <MAC C-01 eircom87005608> (try 3/3)
[  965.820526] wlan0: authentication with <MAC C-01 eircom87005608> timed out
[  967.763492] wlan0: authenticate with <MAC C-01 eircom87005608>
[  967.779225] wlan0: send auth to <MAC C-01 eircom87005608> (try 1/3)
[  967.779259] wlan0: authenticated
[  967.779495] rtl8723ae 0000:03:00.0 wlan0: disabling HT/VHT due to WEP/TKIP use
[  967.779499] rtl8723ae 0000:03:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[  967.779502] rtl8723ae 0000:03:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[  967.783037] wlan0: associate with <MAC C-01 eircom87005608> (try 1/3)
[  967.788770] wlan0: RX AssocResp from <MAC C-01 eircom87005608> (capab=0x431 status=0 aid=3)
[  967.789007] wlan0: associated
[  967.812223] wlan0: Limiting TX power to 20 (20 - 0) dBm as advertised by <MAC C-01 eircom87005608>
[  974.395754] wlan0: Connection to AP <MAC C-01 eircom87005608> lost
[  980.135893] wlan0: authenticate with <MAC C-01 eircom87005608>
[  980.151529] wlan0: send auth to <MAC C-01 eircom87005608> (try 1/3)
[  980.152992] wlan0: authenticated
[  980.153191] rtl8723ae 0000:03:00.0 wlan0: disabling HT/VHT due to WEP/TKIP use
[  980.153197] rtl8723ae 0000:03:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[  980.153200] rtl8723ae 0000:03:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[  980.155165] wlan0: associate with <MAC C-01 eircom87005608> (try 1/3)
[  980.157632] wlan0: RX AssocResp from <MAC C-01 eircom87005608> (capab=0x431 status=0 aid=3)
[  980.157874] wlan0: associated
[  980.215793] wlan0: Limiting TX power to 20 (20 - 0) dBm as advertised by <MAC C-01 eircom87005608>
[ 1063.467792] wlan0: Connection to AP <MAC C-01 eircom87005608> lost
[ 1064.532833] wlan0: authenticate with <MAC C-01 eircom87005608>
[ 1064.548848] wlan0: send auth to <MAC C-01 eircom87005608> (try 1/3)
[ 1064.652638] wlan0: send auth to <MAC C-01 eircom87005608> (try 2/3)
[ 1064.756734] wlan0: send auth to <MAC C-01 eircom87005608> (try 3/3)
[ 1064.860831] wlan0: authentication with <MAC C-01 eircom87005608> timed out
[ 1066.302427] wlan0: authenticate with <MAC C-01 eircom87005608>
[ 1066.318226] wlan0: send auth to <MAC C-01 eircom87005608> (try 1/3)
[ 1066.422047] wlan0: send auth to <MAC C-01 eircom87005608> (try 2/3)
[ 1066.526180] wlan0: send auth to <MAC C-01 eircom87005608> (try 3/3)
[ 1066.630255] wlan0: authentication with <MAC C-01 eircom87005608> timed out
[ 1068.568511] wlan0: authenticate with <MAC C-01 eircom87005608>
[ 1068.584053] wlan0: send auth to <MAC C-01 eircom87005608> (try 1/3)
[ 1068.586427] wlan0: authenticated
[ 1068.586569] rtl8723ae 0000:03:00.0 wlan0: disabling HT/VHT due to WEP/TKIP use
[ 1068.586572] rtl8723ae 0000:03:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[ 1068.586573] rtl8723ae 0000:03:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[ 1068.587778] wlan0: associate with <MAC C-01 eircom87005608> (try 1/3)
[ 1068.591339] wlan0: RX AssocResp from <MAC C-01 eircom87005608> (capab=0x431 status=0 aid=3)
[ 1068.591586] wlan0: associated
[ 1068.679944] wlan0: Limiting TX power to 20 (20 - 0) dBm as advertised by <MAC C-01 eircom87005608>
[ 1075.501446] wlan0: Connection to AP <MAC C-01 eircom87005608> lost
[ 1076.911102] wlan0: authenticate with <MAC C-01 eircom87005608>
[ 1076.926752] wlan0: send auth to <MAC C-01 eircom87005608> (try 1/3)
[ 1076.928215] wlan0: authenticated
[ 1076.928333] rtl8723ae 0000:03:00.0 wlan0: disabling HT/VHT due to WEP/TKIP use
[ 1076.928336] rtl8723ae 0000:03:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[ 1076.928338] rtl8723ae 0000:03:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[ 1076.930571] wlan0: associate with <MAC C-01 eircom87005608> (try 1/3)
[ 1076.932982] wlan0: RX AssocResp from <MAC C-01 eircom87005608> (capab=0x431 status=0 aid=3)
[ 1076.933226] wlan0: associated
[ 1076.983083] wlan0: Limiting TX power to 20 (20 - 0) dBm as advertised by <MAC C-01 eircom87005608>
[ 1118.095837] wlan0: Connection to AP <MAC C-01 eircom87005608> lost
[ 1119.164884] wlan0: authenticate with <MAC C-01 eircom87005608>
[ 1119.180828] wlan0: send auth to <MAC C-01 eircom87005608> (try 1/3)
[ 1119.284692] wlan0: send auth to <MAC C-01 eircom87005608> (try 2/3)
[ 1119.388776] wlan0: send auth to <MAC C-01 eircom87005608> (try 3/3)
[ 1119.492860] wlan0: authentication with <MAC C-01 eircom87005608> timed out
[ 1120.934797] wlan0: authenticate with <MAC C-01 eircom87005608>
[ 1120.950417] wlan0: send auth to <MAC C-01 eircom87005608> (try 1/3)
[ 1121.054173] wlan0: send auth to <MAC C-01 eircom87005608> (try 2/3)
[ 1121.158258] wlan0: send auth to <MAC C-01 eircom87005608> (try 3/3)
[ 1121.262335] wlan0: authentication with <MAC C-01 eircom87005608> timed out
[ 1123.216193] wlan0: authenticate with <MAC C-01 eircom87005608>
[ 1123.232079] wlan0: send auth to <MAC C-01 eircom87005608> (try 1/3)
[ 1123.233521] wlan0: authenticated
[ 1123.233617] rtl8723ae 0000:03:00.0 wlan0: disabling HT/VHT due to WEP/TKIP use
[ 1123.233620] rtl8723ae 0000:03:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[ 1123.233622] rtl8723ae 0000:03:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[ 1123.235888] wlan0: associate with <MAC C-01 eircom87005608> (try 1/3)
[ 1123.238224] wlan0: RX AssocResp from <MAC C-01 eircom87005608> (capab=0x431 status=0 aid=3)
[ 1123.238473] wlan0: associated
[ 1123.290982] wlan0: Limiting TX power to 20 (20 - 0) dBm as advertised by <MAC C-01 eircom87005608>
[ 1188.299083] wlan0: Connection to AP <MAC C-01 eircom87005608> lost
[ 1189.709872] wlan0: authenticate with <MAC C-01 eircom87005608>
[ 1189.725808] wlan0: send auth to <MAC C-01 eircom87005608> (try 1/3)
[ 1189.727259] wlan0: authenticated
[ 1189.727459] rtl8723ae 0000:03:00.0 wlan0: disabling HT/VHT due to WEP/TKIP use
[ 1189.727463] rtl8723ae 0000:03:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[ 1189.727466] rtl8723ae 0000:03:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[ 1189.729549] wlan0: associate with <MAC C-01 eircom87005608> (try 1/3)
[ 1189.731924] wlan0: RX AssocResp from <MAC C-01 eircom87005608> (capab=0x431 status=0 aid=3)
[ 1189.732160] wlan0: associated
[ 1189.818537] wlan0: Limiting TX power to 20 (20 - 0) dBm as advertised by <MAC C-01 eircom87005608>
[ 1248.945444] wlan0: Connection to AP <MAC C-01 eircom87005608> lost
[ 1250.362977] wlan0: authenticate with <MAC C-01 eircom87005608>
[ 1250.378744] wlan0: send auth to <MAC C-01 eircom87005608> (try 1/3)
[ 1250.381625] wlan0: authenticated
[ 1250.381814] rtl8723ae 0000:03:00.0 wlan0: disabling HT/VHT due to WEP/TKIP use
[ 1250.381821] rtl8723ae 0000:03:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[ 1250.381825] rtl8723ae 0000:03:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[ 1250.382468] wlan0: associate with <MAC C-01 eircom87005608> (try 1/3)
[ 1250.384961] wlan0: RX AssocResp from <MAC C-01 eircom87005608> (capab=0x431 status=0 aid=3)
[ 1250.385211] wlan0: associated
[ 1250.400665] wlan0: Limiting TX power to 20 (20 - 0) dBm as advertised by <MAC C-01 eircom87005608>
[ 1267.480332] wlan0: Connection to AP <MAC C-01 eircom87005608> lost
[ 1268.541543] wlan0: authenticate with <MAC C-01 eircom87005608>
[ 1268.557336] wlan0: send auth to <MAC C-01 eircom87005608> (try 1/3)
[ 1268.661206] wlan0: send auth to <MAC C-01 eircom87005608> (try 2/3)
[ 1268.765327] wlan0: send auth to <MAC C-01 eircom87005608> (try 3/3)
[ 1268.869383] wlan0: authentication with <MAC C-01 eircom87005608> timed out
[ 1270.310837] wlan0: authenticate with <MAC C-01 eircom87005608>
[ 1270.326747] wlan0: direct probe to <MAC C-01 eircom87005608> (try 1/3)
[ 1270.530690] wlan0: direct probe to <MAC C-01 eircom87005608> (try 2/3)
[ 1270.734883] wlan0: direct probe to <MAC C-01 eircom87005608> (try 3/3)
[ 1270.939059] wlan0: authentication with <MAC C-01 eircom87005608> timed out
[ 1278.821993] wlan0: authenticate with <MAC C-01 eircom87005608>
[ 1278.837726] wlan0: send auth to <MAC C-01 eircom87005608> (try 1/3)
[ 1278.839334] wlan0: authenticated
[ 1278.839562] rtl8723ae 0000:03:00.0 wlan0: disabling HT/VHT due to WEP/TKIP use
[ 1278.839569] rtl8723ae 0000:03:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[ 1278.839572] rtl8723ae 0000:03:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[ 1278.841446] wlan0: associate with <MAC C-01 eircom87005608> (try 1/3)
[ 1278.843930] wlan0: RX AssocResp from <MAC C-01 eircom87005608> (capab=0x431 status=0 aid=3)
[ 1278.844186] wlan0: associated
[ 1278.897864] wlan0: Limiting TX power to 20 (20 - 0) dBm as advertised by <MAC C-01 eircom87005608>
[ 1349.710657] wlan0: Connection to AP <MAC C-01 eircom87005608> lost
[ 1350.771673] wlan0: authenticate with <MAC C-01 eircom87005608>
[ 1350.787647] wlan0: send auth to <MAC C-01 eircom87005608> (try 1/3)
[ 1350.891551] wlan0: send auth to <MAC C-01 eircom87005608> (try 2/3)
[ 1350.995659] wlan0: send auth to <MAC C-01 eircom87005608> (try 3/3)
[ 1351.099696] wlan0: authentication with <MAC C-01 eircom87005608> timed out
[ 1352.537209] wlan0: authenticate with <MAC C-01 eircom87005608>
[ 1352.553111] wlan0: send auth to <MAC C-01 eircom87005608> (try 1/3)
[ 1352.656962] wlan0: send auth to <MAC C-01 eircom87005608> (try 2/3)
[ 1352.761069] wlan0: send auth to <MAC C-01 eircom87005608> (try 3/3)
[ 1352.865119] wlan0: authentication with <MAC C-01 eircom87005608> timed out
[ 1354.803313] wlan0: authenticate with <MAC C-01 eircom87005608>
[ 1354.819044] wlan0: send auth to <MAC C-01 eircom87005608> (try 1/3)
[ 1354.820586] wlan0: authenticated
[ 1354.820822] rtl8723ae 0000:03:00.0 wlan0: disabling HT/VHT due to WEP/TKIP use
[ 1354.820830] rtl8723ae 0000:03:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[ 1354.820833] rtl8723ae 0000:03:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[ 1354.822731] wlan0: associate with <MAC C-01 eircom87005608> (try 1/3)
[ 1354.825247] wlan0: RX AssocResp from <MAC C-01 eircom87005608> (capab=0x431 status=0 aid=1)
[ 1354.825495] wlan0: associated
[ 1354.856175] wlan0: Limiting TX power to 20 (20 - 0) dBm as advertised by <MAC C-01 eircom87005608>
[ 1445.980338] wlan0: Connection to AP <MAC C-01 eircom87005608> lost
[ 1447.393864] wlan0: authenticate with <MAC C-01 eircom87005608>
[ 1447.409615] wlan0: send auth to <MAC C-01 eircom87005608> (try 1/3)
[ 1447.411779] wlan0: authenticated
[ 1447.411899] rtl8723ae 0000:03:00.0 wlan0: disabling HT/VHT due to WEP/TKIP use
[ 1447.411902] rtl8723ae 0000:03:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[ 1447.411904] rtl8723ae 0000:03:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[ 1447.413392] wlan0: associate with <MAC C-01 eircom87005608> (try 1/3)
[ 1447.415845] wlan0: RX AssocResp from <MAC C-01 eircom87005608> (capab=0x431 status=0 aid=1)
[ 1447.416082] wlan0: associated
[ 1447.422392] wlan0: Limiting TX power to 20 (20 - 0) dBm as advertised by <MAC C-01 eircom87005608>
[ 1504.623670] wlan0: Connection to AP <MAC C-01 eircom87005608> lost
[ 1506.037516] wlan0: authenticate with <MAC C-01 eircom87005608>
[ 1506.053044] wlan0: send auth to <MAC C-01 eircom87005608> (try 1/3)
[ 1506.055765] wlan0: authenticated
[ 1506.055908] rtl8723ae 0000:03:00.0 wlan0: disabling HT/VHT due to WEP/TKIP use
[ 1506.055911] rtl8723ae 0000:03:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[ 1506.055913] rtl8723ae 0000:03:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[ 1506.056710] wlan0: associate with <MAC C-01 eircom87005608> (try 1/3)
[ 1506.059148] wlan0: RX AssocResp from <MAC C-01 eircom87005608> (capab=0x431 status=0 aid=1)
[ 1506.059374] wlan0: associated
[ 1506.157752] wlan0: Limiting TX power to 20 (20 - 0) dBm as advertised by <MAC C-01 eircom87005608>
[ 1629.452450] wlan0: Connection to AP <MAC C-01 eircom87005608> lost
[ 1630.866123] wlan0: authenticate with <MAC C-01 eircom87005608>
[ 1630.881703] wlan0: send auth to <MAC C-01 eircom87005608> (try 1/3)
[ 1630.883202] wlan0: authenticated
[ 1630.883352] rtl8723ae 0000:03:00.0 wlan0: disabling HT/VHT due to WEP/TKIP use
[ 1630.883356] rtl8723ae 0000:03:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[ 1630.883357] rtl8723ae 0000:03:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[ 1630.885457] wlan0: associate with <MAC C-01 eircom87005608> (try 1/3)
[ 1630.888140] wlan0: RX AssocResp from <MAC C-01 eircom87005608> (capab=0x431 status=0 aid=1)
[ 1630.888372] wlan0: associated
[ 1630.909726] wlan0: Limiting TX power to 20 (20 - 0) dBm as advertised by <MAC C-01 eircom87005608>
[ 1690.101360] wlan0: Connection to AP <MAC C-01 eircom87005608> lost
[ 1691.515167] wlan0: authenticate with <MAC C-01 eircom87005608>
[ 1691.530721] wlan0: send auth to <MAC C-01 eircom87005608> (try 1/3)
[ 1691.532259] wlan0: authenticated
[ 1691.532581] rtl8723ae 0000:03:00.0 wlan0: disabling HT/VHT due to WEP/TKIP use
[ 1691.532590] rtl8723ae 0000:03:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[ 1691.532594] rtl8723ae 0000:03:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[ 1691.534446] wlan0: associate with <MAC C-01 eircom87005608> (try 1/3)
[ 1691.536990] wlan0: RX AssocResp from <MAC C-01 eircom87005608> (capab=0x431 status=0 aid=1)
[ 1691.537253] wlan0: associated
[ 1691.594389] wlan0: Limiting TX power to 20 (20 - 0) dBm as advertised by <MAC C-01 eircom87005608>
[ 1724.677245] wlan0: Connection to AP <MAC C-01 eircom87005608> lost
[ 1726.090909] wlan0: authenticate with <MAC C-01 eircom87005608>
[ 1726.106547] wlan0: send auth to <MAC C-01 eircom87005608> (try 1/3)
[ 1726.108021] wlan0: authenticated
[ 1726.108310] rtl8723ae 0000:03:00.0 wlan0: disabling HT/VHT due to WEP/TKIP use
[ 1726.108319] rtl8723ae 0000:03:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[ 1726.108323] rtl8723ae 0000:03:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[ 1726.110329] wlan0: associate with <MAC C-01 eircom87005608> (try 1/3)
[ 1726.112910] wlan0: RX AssocResp from <MAC C-01 eircom87005608> (capab=0x431 status=0 aid=1)
[ 1726.113173] wlan0: associated
[ 1726.139428] wlan0: Limiting TX power to 20 (20 - 0) dBm as advertised by <MAC C-01 eircom87005608>
[ 1733.180035] wlan0: Connection to AP <MAC C-01 eircom87005608> lost
[ 1734.598023] wlan0: authenticate with <MAC C-01 eircom87005608>
[ 1734.613407] wlan0: send auth to <MAC C-01 eircom87005608> (try 1/3)
[ 1734.615708] wlan0: authenticated
[ 1734.615844] rtl8723ae 0000:03:00.0 wlan0: disabling HT/VHT due to WEP/TKIP use
[ 1734.615848] rtl8723ae 0000:03:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[ 1734.615850] rtl8723ae 0000:03:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[ 1734.617082] wlan0: associate with <MAC C-01 eircom87005608> (try 1/3)
[ 1734.619466] wlan0: RX AssocResp from <MAC C-01 eircom87005608> (capab=0x431 status=0 aid=1)
[ 1734.619711] wlan0: associated
[ 1734.647551] wlan0: Limiting TX power to 20 (20 - 0) dBm as advertised by <MAC C-01 eircom87005608>
[ 1741.686973] wlan0: Connection to AP <MAC C-01 eircom87005608> lost
[ 1743.100589] wlan0: authenticate with <MAC C-01 eircom87005608>
[ 1743.116208] wlan0: send auth to <MAC C-01 eircom87005608> (try 1/3)
[ 1743.117949] wlan0: authenticated
[ 1743.118106] rtl8723ae 0000:03:00.0 wlan0: disabling HT/VHT due to WEP/TKIP use
[ 1743.118110] rtl8723ae 0000:03:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[ 1743.118113] rtl8723ae 0000:03:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[ 1743.120007] wlan0: associate with <MAC C-01 eircom87005608> (try 1/3)
[ 1743.122579] wlan0: RX AssocResp from <MAC C-01 eircom87005608> (capab=0x431 status=0 aid=1)
[ 1743.122803] wlan0: associated
[ 1743.155731] wlan0: Limiting TX power to 20 (20 - 0) dBm as advertised by <MAC C-01 eircom87005608>
[ 1760.224469] wlan0: Connection to AP <MAC C-01 eircom87005608> lost
[ 1761.631571] wlan0: authenticate with <MAC C-01 eircom87005608>
[ 1761.647189] wlan0: send auth to <MAC C-01 eircom87005608> (try 1/3)
[ 1761.649215] wlan0: authenticated
[ 1761.649338] rtl8723ae 0000:03:00.0 wlan0: disabling HT/VHT due to WEP/TKIP use
[ 1761.649342] rtl8723ae 0000:03:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[ 1761.649344] rtl8723ae 0000:03:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[ 1761.650903] wlan0: associate with <MAC C-01 eircom87005608> (try 1/3)
[ 1761.653377] wlan0: RX AssocResp from <MAC C-01 eircom87005608> (capab=0x431 status=0 aid=1)
[ 1761.653629] wlan0: associated
[ 1761.709660] wlan0: Limiting TX power to 20 (20 - 0) dBm as advertised by <MAC C-01 eircom87005608>
[ 1768.720640] wlan0: Connection to AP <MAC C-01 eircom87005608> lost
[ 1770.134262] wlan0: authenticate with <MAC C-01 eircom87005608>
[ 1770.150018] wlan0: send auth to <MAC C-01 eircom87005608> (try 1/3)
[ 1770.151499] wlan0: authenticated
[ 1770.151665] rtl8723ae 0000:03:00.0 wlan0: disabling HT/VHT due to WEP/TKIP use
[ 1770.151668] rtl8723ae 0000:03:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[ 1770.151670] rtl8723ae 0000:03:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[ 1770.153779] wlan0: associate with <MAC C-01 eircom87005608> (try 1/3)
[ 1770.156266] wlan0: RX AssocResp from <MAC C-01 eircom87005608> (capab=0x431 status=0 aid=1)
[ 1770.156498] wlan0: associated
[ 1770.217862] wlan0: Limiting TX power to 20 (20 - 0) dBm as advertised by <MAC C-01 eircom87005608>
[ 1813.320615] wlan0: Connection to AP <MAC C-01 eircom87005608> lost
[ 1814.730041] wlan0: authenticate with <MAC C-01 eircom87005608>
[ 1814.745955] wlan0: send auth to <MAC C-01 eircom87005608> (try 1/3)
[ 1814.747441] wlan0: authenticated
[ 1814.747597] rtl8723ae 0000:03:00.0 wlan0: disabling HT/VHT due to WEP/TKIP use
[ 1814.747602] rtl8723ae 0000:03:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[ 1814.747604] rtl8723ae 0000:03:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[ 1814.749726] wlan0: associate with <MAC C-01 eircom87005608> (try 1/3)
[ 1814.752090] wlan0: RX AssocResp from <MAC C-01 eircom87005608> (capab=0x431 status=0 aid=1)
[ 1814.752338] wlan0: associated
[ 1814.808670] wlan0: Limiting TX power to 20 (20 - 0) dBm as advertised by <MAC C-01 eircom87005608>
[ 1930.122935] wlan0: Connection to AP <MAC C-01 eircom87005608> lost
[ 1931.536777] wlan0: authenticate with <MAC C-01 eircom87005608>
[ 1931.552406] wlan0: send auth to <MAC C-01 eircom87005608> (try 1/3)
[ 1931.656129] wlan0: send auth to <MAC C-01 eircom87005608> (try 2/3)
[ 1931.760223] wlan0: send auth to <MAC C-01 eircom87005608> (try 3/3)
[ 1931.864307] wlan0: authentication with <MAC C-01 eircom87005608> timed out
[ 1933.302166] wlan0: authenticate with <MAC C-01 eircom87005608>
[ 1933.317809] wlan0: send auth to <MAC C-01 eircom87005608> (try 1/3)
[ 1933.421568] wlan0: send auth to <MAC C-01 eircom87005608> (try 2/3)
[ 1933.525649] wlan0: send auth to <MAC C-01 eircom87005608> (try 3/3)
[ 1933.629728] wlan0: authentication with <MAC C-01 eircom87005608> timed out
[ 1935.571994] wlan0: authenticate with <MAC C-01 eircom87005608>
[ 1935.587656] wlan0: send auth to <MAC C-01 eircom87005608> (try 1/3)
[ 1935.691293] wlan0: send auth to <MAC C-01 eircom87005608> (try 2/3)
[ 1935.795430] wlan0: send auth to <MAC C-01 eircom87005608> (try 3/3)
[ 1935.899562] wlan0: authentication with <MAC C-01 eircom87005608> timed out
[ 1945.512044] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1983.551929] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1985.460194] wlan0: authenticate with <MAC C-01 eircom87005608>
[ 1985.475681] wlan0: send auth to <MAC C-01 eircom87005608> (try 1/3)
[ 1985.477349] wlan0: authenticated
[ 1985.477453] rtl8723ae 0000:03:00.0 wlan0: disabling HT/VHT due to WEP/TKIP use
[ 1985.477456] rtl8723ae 0000:03:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[ 1985.477457] rtl8723ae 0000:03:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[ 1985.479460] wlan0: associate with <MAC C-01 eircom87005608> (try 1/3)
[ 1985.484769] wlan0: RX AssocResp from <MAC C-01 eircom87005608> (capab=0x431 status=0 aid=2)
[ 1985.485004] wlan0: associated
[ 1985.485014] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 1989.550937] wlan0: Connection to AP <MAC C-01 eircom87005608> lost
[ 1989.579359] wlan0: authenticate with <MAC C-01 eircom87005608>
[ 1989.579457] wlan0: send auth to <MAC C-01 eircom87005608> (try 1/3)
[ 1989.682891] wlan0: send auth to <MAC C-01 eircom87005608> (try 2/3)
[ 1989.787000] wlan0: send auth to <MAC C-01 eircom87005608> (try 3/3)
[ 1989.891062] wlan0: authentication with <MAC C-01 eircom87005608> timed out
[ 2003.206761] wlan0: authenticate with <MAC C-01 eircom87005608>
[ 2003.222023] wlan0: send auth to <MAC C-01 eircom87005608> (try 1/3)
[ 2003.223535] wlan0: authenticated
[ 2003.223692] rtl8723ae 0000:03:00.0 wlan0: disabling HT/VHT due to WEP/TKIP use
[ 2003.223696] rtl8723ae 0000:03:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[ 2003.223698] rtl8723ae 0000:03:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[ 2003.225830] wlan0: associate with <MAC C-01 eircom87005608> (try 1/3)
[ 2003.228288] wlan0: RX AssocResp from <MAC C-01 eircom87005608> (capab=0x431 status=0 aid=2)
[ 2003.228547] wlan0: associated
[ 2003.320581] wlan0: Limiting TX power to 20 (20 - 0) dBm as advertised by <MAC C-01 eircom87005608>
[ 2010.379623] wlan0: deauthenticating from <MAC C-01 eircom87005608> by local choice (reason=3)
[ 2011.389057] wlan0: authenticate with <MAC C-01 eircom87005608>
[ 2011.404675] wlan0: send auth to <MAC C-01 eircom87005608> (try 1/3)
[ 2011.406232] wlan0: authenticated
[ 2011.406383] rtl8723ae 0000:03:00.0 wlan0: disabling HT/VHT due to WEP/TKIP use
[ 2011.406387] rtl8723ae 0000:03:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[ 2011.406389] rtl8723ae 0000:03:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[ 2011.408372] wlan0: associate with <MAC C-01 eircom87005608> (try 1/3)
[ 2011.410862] wlan0: RX AssocResp from <MAC C-01 eircom87005608> (capab=0x431 status=0 aid=2)
[ 2011.411115] wlan0: associated
[ 2011.418665] wlan0: Limiting TX power to 20 (20 - 0) dBm as advertised by <MAC C-01 eircom87005608>
[ 2039.680230] wlan0: Connection to AP <MAC C-01 eircom87005608> lost
[ 2041.093284] wlan0: authenticate with <MAC C-01 eircom87005608>
[ 2041.108942] wlan0: send auth to <MAC C-01 eircom87005608> (try 1/3)
[ 2041.110424] wlan0: authenticated
[ 2041.110592] rtl8723ae 0000:03:00.0 wlan0: disabling HT/VHT due to WEP/TKIP use
[ 2041.110598] rtl8723ae 0000:03:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[ 2041.110602] rtl8723ae 0000:03:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[ 2041.112605] wlan0: associate with <MAC C-01 eircom87005608> (try 1/3)
[ 2041.115006] wlan0: RX AssocResp from <MAC C-01 eircom87005608> (capab=0x431 status=0 aid=2)
[ 2041.115258] wlan0: associated
[ 2041.145925] wlan0: Limiting TX power to 20 (20 - 0) dBm as advertised by <MAC C-01 eircom87005608>
[ 2046.917749] wlan0: disassociated from <MAC C-01 eircom87005608> (Reason: 1)
[ 2046.922791] wlan0: deauthenticating from <MAC C-01 eircom87005608> by local choice (reason=3)
[ 2048.311245] wlan0: authenticate with <MAC C-01 eircom87005608>
[ 2048.327063] wlan0: send auth to <MAC C-01 eircom87005608> (try 1/3)
[ 2048.328469] wlan0: authenticated
[ 2048.328601] rtl8723ae 0000:03:00.0 wlan0: disabling HT/VHT due to WEP/TKIP use
[ 2048.328604] rtl8723ae 0000:03:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[ 2048.328605] rtl8723ae 0000:03:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[ 2048.330842] wlan0: associate with <MAC C-01 eircom87005608> (try 1/3)
[ 2048.333350] wlan0: RX AssocResp from <MAC C-01 eircom87005608> (capab=0x431 status=0 aid=2)
[ 2048.333594] wlan0: associated
[ 2048.424000] wlan0: Limiting TX power to 20 (20 - 0) dBm as advertised by <MAC C-01 eircom87005608>
[ 2069.437845] wlan0: Connection to AP <MAC C-01 eircom87005608> lost
[ 2070.852250] wlan0: authenticate with <MAC C-01 eircom87005608>
[ 2070.867905] wlan0: send auth to <MAC C-01 eircom87005608> (try 1/3)
[ 2070.869551] wlan0: authenticated
[ 2070.869714] rtl8723ae 0000:03:00.0 wlan0: disabling HT/VHT due to WEP/TKIP use
[ 2070.869719] rtl8723ae 0000:03:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[ 2070.869721] rtl8723ae 0000:03:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[ 2070.871568] wlan0: associate with <MAC C-01 eircom87005608> (try 1/3)
[ 2070.875104] wlan0: RX AssocResp from <MAC C-01 eircom87005608> (capab=0x431 status=0 aid=2)
[ 2070.875348] wlan0: associated
[ 2070.975715] wlan0: Limiting TX power to 20 (20 - 0) dBm as advertised by <MAC C-01 eircom87005608>
[ 2154.153582] wlan0: Connection to AP <MAC C-01 eircom87005608> lost
[ 2155.572520] wlan0: authenticate with <MAC C-01 eircom87005608>
[ 2155.588252] wlan0: send auth to <MAC C-01 eircom87005608> (try 1/3)
[ 2155.590313] wlan0: authenticated
[ 2155.590605] rtl8723ae 0000:03:00.0 wlan0: disabling HT/VHT due to WEP/TKIP use
[ 2155.590616] rtl8723ae 0000:03:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[ 2155.590622] rtl8723ae 0000:03:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[ 2155.591965] wlan0: associate with <MAC C-01 eircom87005608> (try 1/3)
[ 2155.594363] wlan0: RX AssocResp from <MAC C-01 eircom87005608> (capab=0x431 status=0 aid=2)
[ 2155.594624] wlan0: associated
[ 2155.647154] wlan0: Limiting TX power to 20 (20 - 0) dBm as advertised by <MAC C-01 eircom87005608>
[ 2178.705497] wlan0: Connection to AP <MAC C-01 eircom87005608> lost
[ 2180.116040] wlan0: authenticate with <MAC C-01 eircom87005608>
[ 2180.132063] wlan0: send auth to <MAC C-01 eircom87005608> (try 1/3)
[ 2180.133498] wlan0: authenticated
[ 2180.133791] rtl8723ae 0000:03:00.0 wlan0: disabling HT/VHT due to WEP/TKIP use
[ 2180.133800] rtl8723ae 0000:03:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[ 2180.133804] rtl8723ae 0000:03:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[ 2180.135817] wlan0: associate with <MAC C-01 eircom87005608> (try 1/3)
[ 2180.138347] wlan0: RX AssocResp from <MAC C-01 eircom87005608> (capab=0x431 status=0 aid=2)
[ 2180.138579] wlan0: associated
[ 2180.146545] wlan0: Limiting TX power to 20 (20 - 0) dBm as advertised by <MAC C-01 eircom87005608>
[ 2193.222375] wlan0: Connection to AP <MAC C-01 eircom87005608> lost
[ 2194.631689] wlan0: authenticate with <MAC C-01 eircom87005608>
[ 2194.647656] wlan0: send auth to <MAC C-01 eircom87005608> (try 1/3)
[ 2194.649087] wlan0: authenticated
[ 2194.649179] rtl8723ae 0000:03:00.0 wlan0: disabling HT/VHT due to WEP/TKIP use
[ 2194.649181] rtl8723ae 0000:03:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[ 2194.649183] rtl8723ae 0000:03:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[ 2194.651403] wlan0: associate with <MAC C-01 eircom87005608> (try 1/3)
[ 2194.653804] wlan0: RX AssocResp from <MAC C-01 eircom87005608> (capab=0x431 status=0 aid=2)
[ 2194.654047] wlan0: associated
[ 2194.702683] wlan0: Limiting TX power to 20 (20 - 0) dBm as advertised by <MAC C-01 eircom87005608>
[ 2235.816832] wlan0: Connection to AP <MAC C-01 eircom87005608> lost
[ 2237.230545] wlan0: authenticate with <MAC C-01 eircom87005608>
[ 2237.246204] wlan0: send auth to <MAC C-01 eircom87005608> (try 1/3)
[ 2237.247654] wlan0: authenticated
[ 2237.247920] rtl8723ae 0000:03:00.0 wlan0: disabling HT/VHT due to WEP/TKIP use
[ 2237.247932] rtl8723ae 0000:03:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[ 2237.247939] rtl8723ae 0000:03:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[ 2237.249882] wlan0: associate with <MAC C-01 eircom87005608> (try 1/3)
[ 2237.252347] wlan0: RX AssocResp from <MAC C-01 eircom87005608> (capab=0x431 status=0 aid=2)
[ 2237.252579] wlan0: associated
[ 2237.345904] wlan0: Limiting TX power to 20 (20 - 0) dBm as advertised by <MAC C-01 eircom87005608>
[ 2244.319619] wlan0: Connection to AP <MAC C-01 eircom87005608> lost
[ 2245.729499] wlan0: authenticate with <MAC C-01 eircom87005608>
[ 2245.745031] wlan0: send auth to <MAC C-01 eircom87005608> (try 1/3)
[ 2245.746587] wlan0: authenticated
[ 2245.746939] rtl8723ae 0000:03:00.0 wlan0: disabling HT/VHT due to WEP/TKIP use
[ 2245.746950] rtl8723ae 0000:03:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[ 2245.746955] rtl8723ae 0000:03:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[ 2245.748739] wlan0: associate with <MAC C-01 eircom87005608> (try 1/3)
[ 2245.752299] wlan0: RX AssocResp from <MAC C-01 eircom87005608> (capab=0x431 status=0 aid=2)
[ 2245.752548] wlan0: associated
[ 2245.854091] wlan0: Limiting TX power to 20 (20 - 0) dBm as advertised by <MAC C-01 eircom87005608>


    ======== Done ========

```

---

### Post by wildmanne39 on 2014-11-22
Hi, let's try two driver parameters that may help with your issue.
Just copy and paste the command into the terminal.
```
sudo -i
echo "options rtl8723ae fwlps=0 swlps=0 " | sudo tee /etc/modprobe.d/rtl8723ae.conf
exit
```
Thanks

---

### Post by starkshaw on 2014-11-22
Woo! Probably your method really works! It didn't lost in last hour! But what is that mean? :)

---

### Post by wildmanne39 on 2014-11-22
Glad to hear it! That command turns off keeps your wifi device from going into power saver mode which is what is causing your issue.

---

