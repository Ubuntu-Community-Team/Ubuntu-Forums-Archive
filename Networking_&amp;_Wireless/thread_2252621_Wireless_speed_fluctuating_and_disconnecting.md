---
title: "Wireless speed fluctuating and disconnecting"
date: 2014-11-13
forum: Networking &amp; Wireless
---

### Post by iPhantom on 2014-11-13
I've got a problem with my Wireless on Ubuntu. It doesn't work at full speed (tested on Windows, my wireless internet connection is fine), and sometimes it randomly disconnects (note that it only disconnects when there' internet activity, otherwise it stays connected).

Laptop model is HP 15-r038ca.

I ran the wireless script, here's the output:

```


	======== Wireless-Info START ========


System-Info ~~~~~~~~~~~~~~~~~~~~~~~~


glend-HP-15-Notebook-PC 3.14.0-031400-generic x86_64,  Ubuntu 14.04.1 LTS, trusty


CPU    : Intel(R) Pentium(R) CPU  N3530  @ 2.16GHz
Memory : 7873 MB
Uptime : 12:36:41 up 42 min,  1 user,  load average: 0,91, 0,76, 0,90




lspci ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~


02:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8188EE Wireless Network Adapter [10ec:8179] (rev 01)
	Subsystem: Hewlett-Packard Company Device [103c:197d]
	Kernel driver in use: rtl8188ee
--
04:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 07)
	Subsystem: Hewlett-Packard Company Device [103c:2213]
	Kernel driver in use: r8169




lsusb ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~


Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 004: ID 04f2:b40e Chicony Electronics Co., Ltd 
Bus 001 Device 005: ID 046d:c05a Logitech, Inc. M90/M100 Optical Mouse
Bus 001 Device 003: ID 1a40:0101 Terminus Technology Inc. 4-Port HUB
Bus 001 Device 002: ID 413c:2101 Dell Computer Corp. SmartCard Reader Keyboard
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub




PCMCIA Card Info ~~~~~~~~~~~~~~~~~~~






iwconfig ~~~~~~~~~~~~~~~~~~~~~~~~~~~


wlan0     IEEE 802.11bgn  ESSID:"Aledia"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:18:84:88:A0:44   
          Bit Rate=72.2 Mb/s   Tx-Power=20 dBm   
          Retry short limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          Link Quality=68/70  Signal level=-42 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:8   Missed beacon:0






rfkill ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~


      Interface        Soft blocked  Hard blocked
0: phy0: Wireless LAN      no            no




lsmod ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~


rtl8188ee              96048  0 
rtl_pci                27261  1 rtl8188ee
rtlwifi                64281  2 rtl_pci,rtl8188ee
mac80211              676864  3 rtl_pci,rtlwifi,rtl8188ee
cfg80211              531467  2 mac80211,rtlwifi
hp_wmi                 18202  0 
sparse_keymap          13890  1 hp_wmi
wmi                    19363  1 hp_wmi




module parameters ~~~~~~~~~~~~~~~~~~


cfg80211      (2): cfg80211_disable_40mhz_24ghz=N | ieee80211_regdom=00
mac80211      (5): beacon_loss_count=7 | ieee80211_default_rc_algo=minstrel_ht | max_nullfunc_tries=2 | max_probe_tries=5 | probe_wait_ms=500
rtl8188ee     (5): debug=0 | fwlps=Y | ips=Y | swenc=N | swlps=N
wmi           (2): debug_dump_wdg=N | debug_event=N




nm-tool ~~~~~~~~~~~~~~~~~~~~~~~~~~~~


State: connected (global)
=================o=============o===========o=============o=========o===========o==============o===========
 Interface & ID  | Type        | Driver    | State       | Default | Speed     | Support      | HW Addr   
=================o=============o===========o=============o=========o===========o==============o===========
 eth0            | Wired       | r8169     | unavailable | no      |           |              | F8:A9:63:93:BD:ED
-----------------+-------------+-----------+-------------+---------+-----------+--------------+-----------
 wlan0  [Aledia] | 802.11 WiFi | rtl8188ee | connected   | yes     | 72 Mb/s   | WEP/WPA/WPA2 | 00:71:CC:83:F4:A5


    Mattia:          Infra, 00:24:D1:86:F5:20, Freq 2462 MHz, Rate 54 Mb/s, Strength 84 WPA WPA2
    NETGEAR:         Infra, 00:22:3F:95:D8:07, Freq 2437 MHz, Rate 54 Mb/s, Strength 100 WPA2
    ALBtelecom-gezim:Infra, 54:22:F8:08:9B:F6, Freq 2447 MHz, Rate 54 Mb/s, Strength 30 WPA
    mcn-tch:         Infra, E8:94:F6:33:08:90, Freq 2472 MHz, Rate 54 Mb/s, Strength 36 WPA2
    ALBtelecom-Edlira2014: Infra, 14:60:80:69:1D:60, Freq 2462 MHz, Rate 54 Mb/s, Strength 30 WPA WPA2
    Kush Te Vuri Kujdestar: Infra, E8:94:F6:33:09:80, Freq 2472 MHz, Rate 54 Mb/s, Strength 30 WPA2
    Easy Club:       Infra, 00:23:EE:FB:FB:7E, Freq 2412 MHz, Rate 54 Mb/s, Strength 100 WPA WPA2
    Steko:           Infra, 00:24:D1:86:F8:22, Freq 2412 MHz, Rate 54 Mb/s, Strength 80 WPA WPA2
    tirana:          Infra, 74:EA:3A:E6:DD:CB, Freq 2412 MHz, Rate 54 Mb/s, Strength 80 WPA2
    Ola-is-back-home!: Infra, 54:22:F8:08:DD:C0, Freq 2412 MHz, Rate 54 Mb/s, Strength 80 WPA
    MD-H:            Infra, 06:27:22:0B:C3:90, Freq 2437 MHz, Rate 54 Mb/s, Strength 27 WPA WPA2
    telenet-7046A:   Infra, 00:25:F2:F6:B0:B2, Freq 2437 MHz, Rate 54 Mb/s, Strength 27 WPA
    SONIA:           Infra, C8:D5:FE:7C:BC:12, Freq 2437 MHz, Rate 54 Mb/s, Strength 27 WPA
    SWL:             Infra, 00:11:50:B5:47:58, Freq 2462 MHz, Rate 54 Mb/s, Strength 27 WPA
    ORANGE:          Infra, 00:23:ED:8E:E5:1C, Freq 2462 MHz, Rate 54 Mb/s, Strength 27 WPA
    Topnet 3:        Infra, 00:19:BE:00:01:80, Freq 2437 MHz, Rate 11 Mb/s, Strength 27
    *Aledia:         Infra, 00:18:84:88:A0:44, Freq 2437 MHz, Rate 54 Mb/s, Strength 74 WPA WPA2
    NONI:            Infra, A0:F3:C1:81:16:AB, Freq 2472 MHz, Rate 54 Mb/s, Strength 30 WPA
    mcn.al:          Infra, 6C:FD:B9:86:00:52, Freq 2462 MHz, Rate 54 Mb/s, Strength 100 WPA WPA2
    DION:            Infra, 00:24:D1:86:3E:55, Freq 2437 MHz, Rate 54 Mb/s, Strength 100 WPA WPA2
    MD-G:            Infra, 0A:27:22:0B:C3:90, Freq 2437 MHz, Rate 54 Mb/s, Strength 100 WPA WPA2
    ALBtelecom-Rita: Infra, 54:22:F8:08:7A:9E, Freq 2447 MHz, Rate 54 Mb/s, Strength 100 WPA
    ALBtelecom-Sovali: Infra, 14:60:80:69:80:94, Freq 2457 MHz, Rate 54 Mb/s, Strength 100 WPA WPA2
    BEVI:            Infra, 00:26:24:BA:8A:B2, Freq 2462 MHz, Rate 54 Mb/s, Strength 100 WPA WPA2
    ALBtelecom-dolce-vita: Infra, 54:22:F8:08:DD:BE, Freq 2412 MHz, Rate 54 Mb/s, Strength 74 WPA WPA2
    ALBtelecomZTE:   Infra, 0C:96:BF:A4:44:FC, Freq 2412 MHz, Rate 54 Mb/s, Strength 34 WPA WPA2
    albtelekom:      Infra, 00:15:EC:1B:D4:79, Freq 2437 MHz, Rate 54 Mb/s, Strength 30 WPA2
    ENEA:            Infra, 74:EA:3A:EF:C4:56, Freq 2437 MHz, Rate 54 Mb/s, Strength 97 WPA2
    Topnet 4:        Infra, 00:19:BE:00:01:28, Freq 2462 MHz, Rate 11 Mb/s, Strength 50
    dri:             Infra, F8:1A:67:84:0A:45, Freq 2467 MHz, Rate 54 Mb/s, Strength 30
    dolce-vita:      Infra, 54:22:F8:08:DD:BF, Freq 2412 MHz, Rate 54 Mb/s, Strength 47 WPA WPA2


    Address:         192.168.10.245
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.10.1
    DNS:             192.168.10.1
-----------------+-------------+-----------+-------------+---------+-----------+--------------+-----------




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
search lan




Routes & Ping ~~~~~~~~~~~~~~~~~~~~~~


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.10.1    0.0.0.0         UG    0      0        0 wlan0
172.17.0.0      0.0.0.0         255.255.0.0     U     0      0        0 docker0
192.168.10.0    0.0.0.0         255.255.255.0   U     9      0        0 wlan0


--- 192.168.10.1 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 1001ms
rtt min/avg/max/mdev = 10.420/10.781/11.143/0.376 ms


--- 127.0.1.1 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 1000ms
rtt min/avg/max/mdev = 0.059/0.074/0.089/0.015 ms




iw reg get ~~~~~~~~~~~~~~~~~~~~~~~~~


(Region : sq_AL.UTF-8)
country AL:
	(2402 - 2482 @ 20), (N/A, 20)




iwlist chan ~~~~~~~~~~~~~~~~~~~~~~~~


wlan0     13 channels in total; available frequencies :
          Channel 01 (2.412 GHz) - 13 (2.472 GHz)


          Current Frequency:2.437 GHz (Channel 6)




iwlist scan ~~~~~~~~~~~~~~~~~~~~~~~~


No way to aquire root rights found.




blacklist ~~~~~~~~~~~~~~~~~~~~~~~~~~


[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci




modinfo ~~~~~~~~~~~~~~~~~~~~~~~~~~~~


[rtl8188ee]
filename:       /lib/modules/3.14.0-031400-generic/kernel/drivers/net/wireless/rtlwifi/rtl8188ee/rtl8188ee.ko
firmware:       rtlwifi/rtl8188efw.bin
srcversion:     9294C4318714C04CF9E0321
depends:        rtlwifi,rtl_pci,mac80211
parm:           swenc:Set to 1 for software crypto (default 0)
parm:           ips:Set to 0 to not use link power save (default 1)
parm:           swlps:Set to 1 to use SW control power save (default 0)
parm:           fwlps:Set to 1 to use FW control power save (default 1)
parm:           debug:Set debug level (0-5) (default 0) (int)


[rtl_pci]
filename:       /lib/modules/3.14.0-031400-generic/kernel/drivers/net/wireless/rtlwifi/rtl_pci.ko
srcversion:     B07D1002FC86501951333AE
depends:        mac80211,rtlwifi


[rtlwifi]
filename:       /lib/modules/3.14.0-031400-generic/kernel/drivers/net/wireless/rtlwifi/rtlwifi.ko
srcversion:     BACE38460F5E5294FE27C59
depends:        mac80211,cfg80211


[mac80211]
filename:       /lib/modules/3.14.0-031400-generic/kernel/net/mac80211/mac80211.ko
srcversion:     AF71C11DB75127119B9AB7B
depends:        cfg80211
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)


[cfg80211]
filename:       /lib/modules/3.14.0-031400-generic/kernel/net/wireless/cfg80211.ko
srcversion:     0739D3437930A94073358B8
depends:        
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)


[hp_wmi]
filename:       /lib/modules/3.14.0-031400-generic/kernel/drivers/platform/x86/hp-wmi.ko
srcversion:     22DCD1B7DA09178B45B1068
depends:        wmi,sparse-keymap


[wmi]
filename:       /lib/modules/3.14.0-031400-generic/kernel/drivers/platform/x86/wmi.ko
srcversion:     347CF30B94B5549A75865A8
depends:        
parm:           debug_event:Log WMI Events [0/1] (bool)
parm:           debug_dump_wdg:Dump available WMI interfaces [0/1] (bool)




udev rules ~~~~~~~~~~~~~~~~~~~~~~~~~


# PCI device 0x10ec:0x8136 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="f8:a9:63:93:bd:ed", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"


# PCI device 0x10ec:0x8179 (rtl8188ee)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:71:cc:83:f4:a5", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"




Custom files/entries ~~~~~~~~~~~~~~~


/etc/modules        : Default
/etc/rc.local       : Default
/etc/modprobe.d     : Not Default
/etc/pm/(cnf|pw|sl) : Default


[/etc/modprobe.d]
iwlwifi.conf      : options iwlwifi 11n_disable=1
mlx4.conf         : softdep mlx4_core post: mlx4_en




Kernel boot line ~~~~~~~~~~~~~~~~~~~


BOOT_IMAGE=/boot/vmlinuz-3.14.0-031400-generic root=UUID=743e1a2c-43f7-4f0f-95a5-4281766f9429 ro quiet splash vt.handoff=7




dmesg ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~


[    0.033520] Initializing cgroup subsys net_cls
[    3.733108] audit: initializing netlink subsys (disabled)
[    4.064844] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[   12.052870] wmi: Mapper loaded
[   12.685165] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[   13.412651] rtl8188ee: Using firmware rtlwifi/rtl8188efw.bin
[   13.617666] ieee80211 phy0: Selected rate control algorithm 'rtl_rc'
[   13.618037] rtlwifi: wireless switch is on
[   22.280177] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   26.757767] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   29.270912] wlan0: authenticate with e8:94:f6:33:08:90
[   29.289608] wlan0: send auth to e8:94:f6:33:08:90 (try 1/3)
[   29.290961] wlan0: authenticated
[   29.293409] wlan0: associate with e8:94:f6:33:08:90 (try 1/3)
[   29.297577] wlan0: RX AssocResp from e8:94:f6:33:08:90 (capab=0x411 status=0 aid=7)
[   29.297694] wlan0: associated
[   29.297710] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   29.855931] wlan0: deauthenticating from e8:94:f6:33:08:90 by local choice (reason=2)
[   29.888206] wlan0: authenticate with e8:94:f6:33:08:90
[   29.898321] wlan0: send auth to e8:94:f6:33:08:90 (try 1/3)
[   29.900068] wlan0: authenticated
[   29.901855] wlan0: associate with e8:94:f6:33:08:90 (try 1/3)
[   29.904943] wlan0: RX AssocResp from e8:94:f6:33:08:90 (capab=0x411 status=0 aid=7)
[   29.905055] wlan0: associated
[   64.853348] wlan0: Connection to AP e8:94:f6:33:08:90 lost
[   66.216822] wlan0: authenticate with e8:94:f6:33:08:90
[   66.227048] wlan0: send auth to e8:94:f6:33:08:90 (try 1/3)
[   66.228757] wlan0: authenticated
[   66.231403] wlan0: associate with e8:94:f6:33:08:90 (try 1/3)
[   66.234259] wlan0: RX AssocResp from e8:94:f6:33:08:90 (capab=0x411 status=0 aid=7)
[   66.234383] wlan0: associated
[  171.676223] wlan0: Connection to AP e8:94:f6:33:08:90 lost
[  173.043143] wlan0: authenticate with e8:94:f6:33:08:90
[  173.053304] wlan0: send auth to e8:94:f6:33:08:90 (try 1/3)
[  173.056442] wlan0: authenticated
[  173.058248] wlan0: associate with e8:94:f6:33:08:90 (try 1/3)
[  173.066560] wlan0: RX AssocResp from e8:94:f6:33:08:90 (capab=0x411 status=0 aid=4)
[  173.066699] wlan0: associated
[  222.349414] wlan0: Connection to AP e8:94:f6:33:08:90 lost
[  223.745265] wlan0: authenticate with e8:94:f6:33:08:90
[  223.755420] wlan0: send auth to e8:94:f6:33:08:90 (try 1/3)
[  223.757659] wlan0: authenticated
[  223.759408] wlan0: associate with e8:94:f6:33:08:90 (try 1/3)
[  223.761513] wlan0: RX AssocResp from e8:94:f6:33:08:90 (capab=0x411 status=0 aid=4)
[  223.761629] wlan0: associated
[  252.990439] wlan0: Connection to AP e8:94:f6:33:08:90 lost
[  254.349787] wlan0: authenticate with e8:94:f6:33:08:90
[  254.359978] wlan0: send auth to e8:94:f6:33:08:90 (try 1/3)
[  254.362534] wlan0: authenticated
[  254.364408] wlan0: associate with e8:94:f6:33:08:90 (try 1/3)
[  254.369486] wlan0: RX AssocResp from e8:94:f6:33:08:90 (capab=0x411 status=0 aid=4)
[  254.369631] wlan0: associated
[  265.548927] wlan0: Connection to AP e8:94:f6:33:08:90 lost
[  266.907381] wlan0: authenticate with e8:94:f6:33:08:90
[  266.917511] wlan0: send auth to e8:94:f6:33:08:90 (try 1/3)
[  267.018698] wlan0: send auth to e8:94:f6:33:08:90 (try 2/3)
[  267.019990] wlan0: authenticated
[  267.022588] wlan0: associate with e8:94:f6:33:08:90 (try 1/3)
[  267.029113] wlan0: RX AssocResp from e8:94:f6:33:08:90 (capab=0x411 status=0 aid=4)
[  267.029246] wlan0: associated
[  793.549738] wlan0: Connection to AP e8:94:f6:33:08:90 lost
[  794.905739] wlan0: authenticate with e8:94:f6:33:08:90
[  794.915899] wlan0: send auth to e8:94:f6:33:08:90 (try 1/3)
[  794.917550] wlan0: authenticated
[  794.923671] wlan0: associate with e8:94:f6:33:08:90 (try 1/3)
[  794.928443] wlan0: RX AssocResp from e8:94:f6:33:08:90 (capab=0x411 status=0 aid=4)
[  794.928562] wlan0: associated
[  834.174844] wlan0: Connection to AP e8:94:f6:33:08:90 lost
[  835.530749] wlan0: authenticate with e8:94:f6:33:08:90
[  835.540891] wlan0: send auth to e8:94:f6:33:08:90 (try 1/3)
[  835.543034] wlan0: authenticated
[  835.544738] wlan0: associate with e8:94:f6:33:08:90 (try 1/3)
[  835.550494] wlan0: RX AssocResp from e8:94:f6:33:08:90 (capab=0x411 status=0 aid=4)
[  835.550611] wlan0: associated
[  846.726124] wlan0: Connection to AP e8:94:f6:33:08:90 lost
[  848.088079] wlan0: authenticate with e8:94:f6:33:08:90
[  848.098274] wlan0: send auth to e8:94:f6:33:08:90 (try 1/3)
[  848.100611] wlan0: authenticated
[  848.103046] wlan0: associate with e8:94:f6:33:08:90 (try 1/3)
[  848.116482] wlan0: RX AssocResp from e8:94:f6:33:08:90 (capab=0x411 status=0 aid=4)
[  848.116617] wlan0: associated
[  863.298397] wlan0: Connection to AP e8:94:f6:33:08:90 lost
[  864.661518] wlan0: authenticate with e8:94:f6:33:08:90
[  864.671746] wlan0: send auth to e8:94:f6:33:08:90 (try 1/3)
[  864.675184] wlan0: authenticated
[  864.676366] wlan0: associate with e8:94:f6:33:08:90 (try 1/3)
[  864.703763] wlan0: RX AssocResp from e8:94:f6:33:08:90 (capab=0x411 status=0 aid=4)
[  864.703908] wlan0: associated
[  889.900424] wlan0: Connection to AP e8:94:f6:33:08:90 lost
[  891.255474] wlan0: authenticate with e8:94:f6:33:08:90
[  891.265653] wlan0: send auth to e8:94:f6:33:08:90 (try 1/3)
[  891.267097] wlan0: authenticated
[  891.270098] wlan0: associate with e8:94:f6:33:08:90 (try 1/3)
[  891.275281] wlan0: RX AssocResp from e8:94:f6:33:08:90 (capab=0x411 status=0 aid=4)
[  891.275488] wlan0: associated
[  962.623231] wlan0: Connection to AP e8:94:f6:33:08:90 lost
[  963.982203] wlan0: authenticate with e8:94:f6:33:08:90
[  963.992341] wlan0: send auth to e8:94:f6:33:08:90 (try 1/3)
[  963.995413] wlan0: authenticated
[  963.997123] wlan0: associate with e8:94:f6:33:08:90 (try 1/3)
[  964.013438] wlan0: RX AssocResp from e8:94:f6:33:08:90 (capab=0x411 status=0 aid=4)
[  964.013562] wlan0: associated
[ 1041.367048] wlan0: Connection to AP e8:94:f6:33:08:90 lost
[ 1042.726166] wlan0: authenticate with e8:94:f6:33:08:90
[ 1042.736758] wlan0: send auth to e8:94:f6:33:08:90 (try 1/3)
[ 1042.738832] wlan0: authenticated
[ 1042.741173] wlan0: associate with e8:94:f6:33:08:90 (try 1/3)
[ 1042.748650] wlan0: RX AssocResp from e8:94:f6:33:08:90 (capab=0x411 status=0 aid=4)
[ 1042.748774] wlan0: associated
[ 1053.925277] wlan0: Connection to AP e8:94:f6:33:08:90 lost
[ 1055.256409] wlan0: authenticate with e8:94:f6:33:08:90
[ 1055.266567] wlan0: send auth to e8:94:f6:33:08:90 (try 1/3)
[ 1055.267972] wlan0: authenticated
[ 1055.271321] wlan0: associate with e8:94:f6:33:08:90 (try 1/3)
[ 1055.277396] wlan0: RX AssocResp from e8:94:f6:33:08:90 (capab=0x411 status=0 aid=4)
[ 1055.277544] wlan0: associated
[ 1088.517430] wlan0: Connection to AP e8:94:f6:33:08:90 lost
[ 1089.884330] wlan0: authenticate with e8:94:f6:33:08:90
[ 1089.894475] wlan0: send auth to e8:94:f6:33:08:90 (try 1/3)
[ 1089.897823] wlan0: authenticated
[ 1089.903680] wlan0: associate with e8:94:f6:33:08:90 (try 1/3)
[ 1089.909116] wlan0: RX AssocResp from e8:94:f6:33:08:90 (capab=0x411 status=0 aid=4)
[ 1089.909272] wlan0: associated
[ 1097.231801] wlan0: deauthenticating from e8:94:f6:33:08:90 by local choice (reason=3)
[ 1098.615518] wlan0: authenticate with 00:18:84:88:a0:44
[ 1098.625642] wlan0: direct probe to 00:18:84:88:a0:44 (try 1/3)
[ 1098.826683] wlan0: send auth to 00:18:84:88:a0:44 (try 2/3)
[ 1099.703582] wlan0: send auth to 00:18:84:88:a0:44 (try 3/3)
[ 1100.716222] wlan0: authentication with 00:18:84:88:a0:44 timed out
[ 1102.435085] wlan0: authenticate with 00:18:84:88:a0:44
[ 1102.454114] wlan0: send auth to 00:18:84:88:a0:44 (try 1/3)
[ 1102.459536] wlan0: authenticated
[ 1102.461644] wlan0: associate with 00:18:84:88:a0:44 (try 1/3)
[ 1102.464047] wlan0: RX AssocResp from 00:18:84:88:a0:44 (capab=0xc11 status=0 aid=7)
[ 1102.464161] wlan0: associated
[ 1153.746487] wlan0: Connection to AP 00:18:84:88:a0:44 lost
[ 1155.121853] wlan0: authenticate with 00:18:84:88:a0:44
[ 1155.140771] wlan0: send auth to 00:18:84:88:a0:44 (try 1/3)
[ 1155.143265] wlan0: authenticated
[ 1155.144500] wlan0: associate with 00:18:84:88:a0:44 (try 1/3)
[ 1155.148020] wlan0: RX AssocResp from 00:18:84:88:a0:44 (capab=0xc11 status=0 aid=7)
[ 1155.148156] wlan0: associated
[ 2439.721103] wlan0: deauthenticating from 00:18:84:88:a0:44 by local choice (reason=3)
[ 2441.764827] wlan0: authenticate with e8:94:f6:33:08:90
[ 2442.161256] wlan0: send auth to e8:94:f6:33:08:90 (try 1/3)
[ 2442.165107] wlan0: authenticated
[ 2442.166569] wlan0: associate with e8:94:f6:33:08:90 (try 1/3)
[ 2442.171111] wlan0: RX AssocResp from e8:94:f6:33:08:90 (capab=0x411 status=0 aid=8)
[ 2442.171225] wlan0: associated
[ 2460.204424] wlan0: Connection to AP e8:94:f6:33:08:90 lost
[ 2461.565345] wlan0: authenticate with e8:94:f6:33:08:90
[ 2461.575496] wlan0: send auth to e8:94:f6:33:08:90 (try 1/3)
[ 2461.588592] wlan0: authenticated
[ 2461.591033] wlan0: associate with e8:94:f6:33:08:90 (try 1/3)
[ 2461.596869] wlan0: RX AssocResp from e8:94:f6:33:08:90 (capab=0x411 status=0 aid=8)
[ 2461.596988] wlan0: associated
[ 2463.775146] wlan0: deauthenticating from e8:94:f6:33:08:90 by local choice (reason=3)
[ 2464.729354] wlan0: authenticate with 00:18:84:88:a0:44
[ 2464.742603] wlan0: send auth to 00:18:84:88:a0:44 (try 1/3)
[ 2464.744549] wlan0: authenticated
[ 2464.747254] wlan0: associate with 00:18:84:88:a0:44 (try 1/3)
[ 2464.751438] wlan0: RX AssocResp from 00:18:84:88:a0:44 (capab=0xc11 status=0 aid=7)
[ 2464.751571] wlan0: associated
[ 2465.105158] wlan0: deauthenticating from 00:18:84:88:a0:44 by local choice (reason=2)
[ 2465.138383] wlan0: authenticate with 00:18:84:88:a0:44
[ 2465.148516] wlan0: send auth to 00:18:84:88:a0:44 (try 1/3)
[ 2465.153520] wlan0: authenticated
[ 2465.155619] wlan0: associate with 00:18:84:88:a0:44 (try 1/3)
[ 2465.161149] wlan0: RX AssocResp from 00:18:84:88:a0:44 (capab=0xc11 status=0 aid=7)
[ 2465.161266] wlan0: associated


	======== Done ========



```

---

### Post by dargaud2 on 2014-11-14
Out of curiosity, what is this diagnostics script that you are running ? It seems useful.

---

### Post by westie457 on 2014-11-14
> **dargaud2 said:**
> Out of curiosity, what is this diagnostics script that you are running ? It seems useful.

This is the link for the script and how to use it. [http://ubuntuforums.org/showthread.php?p=13024222#post13024222](http://ubuntuforums.org/showthread.php?p=13024222#post13024222)

---

### Post by iPhantom on 2014-11-14
any idea what might be wrong?

---

