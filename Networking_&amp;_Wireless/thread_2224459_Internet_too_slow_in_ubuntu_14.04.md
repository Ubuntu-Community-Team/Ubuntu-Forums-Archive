---
title: "Internet too slow in ubuntu 14.04"
date: 2014-05-16
forum: Networking &amp; Wireless
---

### Post by krust13579 on 2014-05-16
My internet(ethernet connection) is too slow. Normal download speed is 60kB/s but in ubuntu 14.04 the speed is reduced to 3 to 4kB/s. I cannot browse the web or install any softwares. Everything worked fine in ubuntu 12.04. I have done a clean install. I am facing this issue only in ubuntu 14.04. I am posting this thread from puppy linux.

---

### Post by varunendra on 2014-05-16
Please follow the "Wireless Script" link in my signature, download and run the script as per instructions there, and post back the report it generates.

While posting the outputs, please use '**Code**' tags. It preserves the output's formatting and makes the post cleaner, compact and more readable. To see a quick 'HowTo' with screenshots, please follow the "Use Code Tags" link in my signature.

---

### Post by jacek5 on 2014-11-28
Stumbled over this while researching my issues. I also see slow internet performance with 14.04 on my Thinkpad 440s. Maybe someone can help troubleshooting?

```


	======== Wireless-Info START ========


System-Info ~~~~~~~~~~~~~~~~~~~~~~~~


thinky 3.13.0-40-generic x86_64,  Ubuntu 14.04.1 LTS, trusty


CPU    : Intel(R) Core(TM) i5-4200U CPU @ 1.60GHz
Memory : 7692 MB
Uptime : 22:16:53 up 14:23,  2 users,  load average: 0.47, 0.41, 0.30




lspci ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~


00:19.0 Ethernet controller [0200]: Intel Corporation Ethernet Connection I218-V [8086:1559] (rev 04)
	Subsystem: Lenovo Device [17aa:2214]
	Kernel driver in use: e1000e
--
03:00.0 Network controller [0280]: Intel Corporation Wireless 7260 [8086:08b2] (rev 83)
	Subsystem: Intel Corporation Dual Band Wireless-N 7260 [8086:c260]
	Kernel driver in use: iwlwifi




lsusb ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~


Bus 001 Device 002: ID 8087:8000 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 002 Device 004: ID 04ca:7035 Lite-On Technology Corp. 
Bus 002 Device 003: ID 8087:07dc Intel Corp. 
Bus 002 Device 002: ID 138a:0017 Validity Sensors, Inc. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub




PCMCIA Card Info ~~~~~~~~~~~~~~~~~~~






iwconfig ~~~~~~~~~~~~~~~~~~~~~~~~~~~


wlan0     IEEE 802.11abgn  ESSID:"HokusPokus"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: <MAC C-NA *HokusPokus 1>   
          Bit Rate=54 Mb/s   Tx-Power=22 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=47/70  Signal level=-63 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:29  Invalid misc:1338   Missed beacon:0






rfkill ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~


      Interface                    Soft blocked  Hard blocked
0: tpacpi_bluetooth_sw: Bluetooth      no            no
2: phy0: Wireless LAN                  no            no
9: hci0: Bluetooth                     no            no




lsmod ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~


iwlmvm                189813  0 
mac80211              626557  1 iwlmvm
iwlwifi               169932  1 iwlmvm
cfg80211              484040  3 iwlwifi,mac80211,iwlmvm
wmi                    19177  0 




module parameters ~~~~~~~~~~~~~~~~~~


cfg80211      (2): cfg80211_disable_40mhz_24ghz=N | ieee80211_regdom=00
iwlmvm        (2): init_dbg=N | power_scheme=2
iwlwifi      (11): 11n_disable=0 | amsdu_size_8K=0 | antenna_coupling=0 | bt_coex_active=Y | fw_restart=Y | led_mode=0 | nvm_file=(null) | power_level=0 | power_save=N | swcrypto=0 | wd_disable=1
mac80211      (5): beacon_loss_count=7 | ieee80211_default_rc_algo=minstrel_ht | max_nullfunc_tries=2 | max_probe_tries=5 | probe_wait_ms=500
wmi           (2): debug_dump_wdg=N | debug_event=N




nm-tool ~~~~~~~~~~~~~~~~~~~~~~~~~~~~


State: connected (global)
=====================o=============o=========o=============o=========o===========o==============o===========
 Interface & ID      | Type        | Driver  | State       | Default | Speed     | Support      | HW Addr   
=====================o=============o=========o=============o=========o===========o==============o===========
 wlan0  [HokusPokus] | 802.11 WiFi | iwlwifi | connected   | yes     | 54 Mb/s   | WEP/WPA/WPA2 | <MAC wlan0>


    *HokusPokus:     Infra, <MAC C-NA *HokusPokus 1>, Freq 2462 MHz, Rate 54 Mb/s, Strength 57 WPA WPA2


    Address:         192.168.1.74
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.254
    DNS:             192.168.1.254
---------------------+-------------+---------+-------------+---------+-----------+--------------+-----------
 eth0                | Wired       | e1000e  | unavailable | no      |           |              | <MAC eth0>
---------------------+-------------+---------+-------------+---------+-----------+--------------+-----------




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


HokusPokus           : ssid=HokusPokus | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 




interfaces ~~~~~~~~~~~~~~~~~~~~~~~~~


# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback


resolv.conf ~~~~~~~~~~~~~~~~~~~~~~~~


nameserver 127.0.1.1
search attlocal.net




Routes & Ping ~~~~~~~~~~~~~~~~~~~~~~


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.254   0.0.0.0         UG    0      0        0 wlan0
192.168.1.0     0.0.0.0         255.255.255.0   U     9      0        0 wlan0


--- 192.168.1.254 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 1001ms
rtt min/avg/max/mdev = 2.437/2.728/3.019/0.291 ms


--- 127.0.1.1 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 1000ms
rtt min/avg/max/mdev = 0.016/0.037/0.059/0.022 ms




iw reg get ~~~~~~~~~~~~~~~~~~~~~~~~~


(Region : "en_US.UTF-8")
country US:
	(2402 - 2472 @ 40), (3, 27)
	(5170 - 5250 @ 40), (3, 17)
	(5250 - 5330 @ 40), (3, 20), DFS
	(5490 - 5600 @ 40), (3, 20), DFS
	(5650 - 5710 @ 40), (3, 20), DFS
	(5735 - 5835 @ 40), (3, 30)
	(57240 - 63720 @ 2160), (N/A, 40)




iwlist chan ~~~~~~~~~~~~~~~~~~~~~~~~


wlan0     32 channels in total; available frequencies :
          Channel 01 (2.412 GHz) - 11 (2.462 GHz)
          Channel 36 (5.18 GHz)
          Channel 40 (5.2 GHz)
          Channel 44 (5.22 GHz)
          Channel 48 (5.24 GHz)
          Channel 52 (5.26 GHz)
          Channel 56 (5.28 GHz)
          Channel 60 (5.3 GHz)
          Channel 64 (5.32 GHz)
          Channel 100 (5.5 GHz)
          Channel 104 (5.52 GHz)
          Channel 108 (5.54 GHz)
          Channel 112 (5.56 GHz)
          Channel 116 (5.58 GHz)
          Channel 132 (5.66 GHz)
          Channel 136 (5.68 GHz)
          Channel 140 (5.7 GHz)
          Channel 149 (5.745 GHz)
          Channel 153 (5.765 GHz)
          Channel 157 (5.785 GHz)
          Channel 161 (5.805 GHz)
          Channel 165 (5.825 GHz)


          Current Frequency:2.462 GHz (Channel 11)




iwlist scan ~~~~~~~~~~~~~~~~~~~~~~~~






blacklist ~~~~~~~~~~~~~~~~~~~~~~~~~~


[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci




modinfo ~~~~~~~~~~~~~~~~~~~~~~~~~~~~


[iwlmvm]
filename:       /lib/modules/3.13.0-40-generic/kernel/drivers/net/wireless/iwlwifi/mvm/iwlmvm.ko
version:        in-tree:
srcversion:     7AF85C9FBD17AD993F1CC33
depends:        iwlwifi,mac80211,cfg80211
parm:           init_dbg:set to true to debug an ASSERT in INIT fw (default: false (bool)
parm:           power_scheme:power management scheme: 1-active, 2-balanced, 3-low power, default: 2 (int)


[mac80211]
filename:       /lib/modules/3.13.0-40-generic/kernel/net/mac80211/mac80211.ko
srcversion:     123C230E7AC85A31E4CA28B
depends:        cfg80211
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)


[iwlwifi]
filename:       /lib/modules/3.13.0-40-generic/kernel/drivers/net/wireless/iwlwifi/iwlwifi.ko
version:        in-tree:
firmware:       iwlwifi-100-5.ucode
firmware:       iwlwifi-1000-5.ucode
firmware:       iwlwifi-135-6.ucode
firmware:       iwlwifi-105-6.ucode
firmware:       iwlwifi-2030-6.ucode
firmware:       iwlwifi-2000-6.ucode
firmware:       iwlwifi-5150-2.ucode
firmware:       iwlwifi-5000-5.ucode
firmware:       iwlwifi-6000g2b-6.ucode
firmware:       iwlwifi-6000g2a-5.ucode
firmware:       iwlwifi-6050-5.ucode
firmware:       iwlwifi-6000-4.ucode
firmware:       iwlwifi-7265-7.ucode
firmware:       iwlwifi-3160-7.ucode
firmware:       iwlwifi-7260-7.ucode
srcversion:     32519C773C87BE82120EF0D
depends:        cfg80211
parm:           swcrypto:using crypto in software (default 0 [hardware]) (int)
parm:           11n_disable:disable 11n functionality, bitmap: 1: full, 2: disable agg TX, 4: disable agg RX, 8 enable agg TX (uint)
parm:           amsdu_size_8K:enable 8K amsdu size (default 0) (int)
parm:           fw_restart:restart firmware in case of error (default true) (bool)
parm:           antenna_coupling:specify antenna coupling in dB (defualt: 0 dB) (int)
parm:           wd_disable:Disable stuck queue watchdog timer 0=system default, 1=disable, 2=enable (default: 0) (int)
parm:           nvm_file:NVM file name (charp)
parm:           bt_coex_active:enable wifi/bt co-exist (default: enable) (bool)
parm:           led_mode:0=system default, 1=On(RF On)/Off(RF Off), 2=blinking, 3=Off (default: 0) (int)
parm:           power_save:enable WiFi power management (default: disable) (bool)
parm:           power_level:default power save level (range from 1 - 5, default: 1) (int)


[cfg80211]
filename:       /lib/modules/3.13.0-40-generic/kernel/net/wireless/cfg80211.ko
srcversion:     C2478077E22138832B71659
depends:        
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)


[wmi]
filename:       /lib/modules/3.13.0-40-generic/kernel/drivers/platform/x86/wmi.ko
srcversion:     CED5410F008DC70DF5F064B
depends:        
parm:           debug_event:Log WMI Events [0/1] (bool)
parm:           debug_dump_wdg:Dump available WMI interfaces [0/1] (bool)




udev rules ~~~~~~~~~~~~~~~~~~~~~~~~~


# PCI device 0x8086:0x1559 (e1000e)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC eth0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"


# PCI device 0x8086:0x08b2 (iwlwifi)
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


BOOT_IMAGE=/boot/vmlinuz-3.13.0-40-generic root=UUID=9953bdc8-bbff-40d3-9878-d307408c0051 ro quiet splash vt.handoff=7




dmesg ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~


[    0.671823] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[    0.672174] audit: initializing netlink socket (disabled)
[    2.326087] wmi: Mapper loaded
[    2.394985] iwlwifi 0000:03:00.0: irq 61 for MSI/MSI-X
[    2.405960] iwlwifi 0000:03:00.0: loaded firmware version 22.24.8.0 op_mode iwlmvm
[    2.450516] iwlwifi 0000:03:00.0: Detected Intel(R) Dual Band Wireless N 7260, REV=0x144
[    2.451052] iwlwifi 0000:03:00.0: L1 Enabled; Disabling L0S
[    2.451497] iwlwifi 0000:03:00.0: L1 Enabled; Disabling L0S
[    2.464031] thinkpad_acpi: http://ibm-acpi.sf.net/
[    2.465123] thinkpad_acpi: Unsupported brightness interface, please contact ibm-acpi-devel@lists.sourceforge.net
[    2.469054] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[    2.509842] Bluetooth: hci0: Intel Bluetooth firmware file: intel/ibt-hw-37.7.10-fw-1.80.2.3.d.bseq
[    2.670374] Bluetooth: hci0: Intel Bluetooth firmware patch completed and activated
[    2.671286] ieee80211 phy0: Selected rate control algorithm 'iwl-mvm-rs'
[    3.162266] iwlwifi 0000:03:00.0: L1 Enabled; Disabling L0S
[    3.162714] iwlwifi 0000:03:00.0: L1 Enabled; Disabling L0S
[    3.180968] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[    3.181230] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[    6.550948] psmouse serio2: trackpoint: IBM TrackPoint firmware: 0x0e, buttons: 3/3
[   10.480972] wlan0: authenticate with <MAC C-NA *HokusPokus 1>
[   10.485091] wlan0: send auth to <MAC C-NA *HokusPokus 1> (try 1/3)
[   10.491582] wlan0: authenticated
[   10.491689] iwlwifi 0000:03:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[   10.491693] iwlwifi 0000:03:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[   10.491884] wlan0: associate with <MAC C-NA *HokusPokus 1> (try 1/3)
[   10.496182] wlan0: RX AssocResp from <MAC C-NA *HokusPokus 1> (capab=0x431 status=0 aid=4)
[   10.497443] wlan0: associated
[   10.497464] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   10.539354] wlan0: deauthenticating from <MAC C-NA *HokusPokus 1> by local choice (reason=2)
[   10.544299] wlan0: authenticate with <MAC C-NA *HokusPokus 1>
[   10.547791] wlan0: send auth to <MAC C-NA *HokusPokus 1> (try 1/3)
[   10.549591] wlan0: authenticated
[   10.549748] iwlwifi 0000:03:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[   10.549752] iwlwifi 0000:03:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[   10.551867] wlan0: associate with <MAC C-NA *HokusPokus 1> (try 1/3)
[   10.557504] wlan0: RX AssocResp from <MAC C-NA *HokusPokus 1> (capab=0x431 status=0 aid=4)
[   10.559231] wlan0: associated
[  704.887853] wlan0: deauthenticating from <MAC C-NA *HokusPokus 1> by local choice (reason=3)
[  707.710931] Bluetooth: hci0: Intel Bluetooth firmware file: intel/ibt-hw-37.7.10-fw-1.80.2.3.d.bseq
[  707.826873] Bluetooth: hci0: Intel Bluetooth firmware patch completed and activated
[  708.093517] iwlwifi 0000:03:00.0: L1 Enabled; Disabling L0S
[  708.094122] iwlwifi 0000:03:00.0: L1 Enabled; Disabling L0S
[  708.113678] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  715.298310] wlan0: authenticate with <MAC C-NA *HokusPokus 1>
[  715.304022] wlan0: send auth to <MAC C-NA *HokusPokus 1> (try 1/3)
[  715.305982] wlan0: authenticated
[  715.306107] iwlwifi 0000:03:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[  715.306110] iwlwifi 0000:03:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[  715.306912] wlan0: associate with <MAC C-NA *HokusPokus 1> (try 1/3)
[  715.309168] wlan0: RX AssocResp from <MAC C-NA *HokusPokus 1> (capab=0x431 status=0 aid=7)
[  715.318398] wlan0: associated
[  715.318425] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  715.340626] wlan0: deauthenticating from <MAC C-NA *HokusPokus 1> by local choice (reason=2)
[  715.345654] wlan0: authenticate with <MAC C-NA *HokusPokus 1>
[  715.348894] wlan0: send auth to <MAC C-NA *HokusPokus 1> (try 1/3)
[  715.350657] wlan0: authenticated
[  715.350792] iwlwifi 0000:03:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[  715.350796] iwlwifi 0000:03:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[  715.350922] wlan0: associate with <MAC C-NA *HokusPokus 1> (try 1/3)
[  715.353199] wlan0: RX AssocResp from <MAC C-NA *HokusPokus 1> (capab=0x431 status=0 aid=7)
[  715.355424] wlan0: associated
[ 2161.133038] wlan0: deauthenticating from <MAC C-NA *HokusPokus 1> by local choice (reason=3)
[ 2163.907256] Bluetooth: hci0: Intel Bluetooth firmware file: intel/ibt-hw-37.7.10-fw-1.80.2.3.d.bseq
[ 2164.041154] Bluetooth: hci0: Intel Bluetooth firmware patch completed and activated
[ 2164.326947] iwlwifi 0000:03:00.0: L1 Enabled; Disabling L0S
[ 2164.327554] iwlwifi 0000:03:00.0: L1 Enabled; Disabling L0S
[ 2164.346847] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 2171.610692] wlan0: authenticate with <MAC C-NA *HokusPokus 1>
[ 2171.614269] wlan0: send auth to <MAC C-NA *HokusPokus 1> (try 1/3)
[ 2171.620984] wlan0: authenticated
[ 2171.621292] iwlwifi 0000:03:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[ 2171.621302] iwlwifi 0000:03:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[ 2171.624355] wlan0: associate with <MAC C-NA *HokusPokus 1> (try 1/3)
[ 2171.629974] wlan0: RX AssocResp from <MAC C-NA *HokusPokus 1> (capab=0x431 status=0 aid=7)
[ 2171.631735] wlan0: associated
[ 2171.631756] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 2172.718876] wlan0: deauthenticating from <MAC C-NA *HokusPokus 1> by local choice (reason=2)
[ 2172.725339] wlan0: authenticate with <MAC C-NA *HokusPokus 1>
[ 2172.728932] wlan0: send auth to <MAC C-NA *HokusPokus 1> (try 1/3)
[ 2172.734036] wlan0: authenticated
[ 2172.734346] iwlwifi 0000:03:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[ 2172.734353] iwlwifi 0000:03:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[ 2172.735864] wlan0: associate with <MAC C-NA *HokusPokus 1> (try 1/3)
[ 2172.738232] wlan0: RX AssocResp from <MAC C-NA *HokusPokus 1> (capab=0x431 status=0 aid=7)
[ 2172.739626] wlan0: associated
[ 2721.901878] wlan0: deauthenticating from <MAC C-NA *HokusPokus 1> by local choice (reason=3)
[ 2724.733882] Bluetooth: hci0: Intel Bluetooth firmware file: intel/ibt-hw-37.7.10-fw-1.80.2.3.d.bseq
[ 2724.839825] Bluetooth: hci0: Intel Bluetooth firmware patch completed and activated
[ 2725.052685] iwlwifi 0000:03:00.0: L1 Enabled; Disabling L0S
[ 2725.053277] iwlwifi 0000:03:00.0: L1 Enabled; Disabling L0S
[ 2725.071526] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 2732.345805] wlan0: authenticate with <MAC C-NA *HokusPokus 1>
[ 2732.352161] wlan0: send auth to <MAC C-NA *HokusPokus 1> (try 1/3)
[ 2732.353818] wlan0: authenticated
[ 2732.353943] iwlwifi 0000:03:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[ 2732.353947] iwlwifi 0000:03:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[ 2732.357927] wlan0: associate with <MAC C-NA *HokusPokus 1> (try 1/3)
[ 2732.360173] wlan0: RX AssocResp from <MAC C-NA *HokusPokus 1> (capab=0x431 status=0 aid=6)
[ 2732.361921] wlan0: associated
[ 2732.361947] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 2732.384814] wlan0: deauthenticating from <MAC C-NA *HokusPokus 1> by local choice (reason=2)
[ 2732.390066] wlan0: authenticate with <MAC C-NA *HokusPokus 1>
[ 2732.393018] wlan0: send auth to <MAC C-NA *HokusPokus 1> (try 1/3)
[ 2732.394691] wlan0: authenticated
[ 2732.394891] iwlwifi 0000:03:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[ 2732.394894] iwlwifi 0000:03:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[ 2732.397912] wlan0: associate with <MAC C-NA *HokusPokus 1> (try 1/3)
[ 2732.400524] wlan0: RX AssocResp from <MAC C-NA *HokusPokus 1> (capab=0x431 status=0 aid=6)
[ 2732.401821] wlan0: associated
[ 2737.033337] wlan0: deauthenticated from <MAC C-NA *HokusPokus 1> (Reason: 6)
[ 2746.220091] wlan0: authenticate with <MAC C-NA *HokusPokus 1>
[ 2746.223681] wlan0: send auth to <MAC C-NA *HokusPokus 1> (try 1/3)
[ 2746.228887] wlan0: authenticated
[ 2746.229120] iwlwifi 0000:03:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[ 2746.229131] iwlwifi 0000:03:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[ 2746.231312] wlan0: associate with <MAC C-NA *HokusPokus 1> (try 1/3)
[ 2746.235536] wlan0: RX AssocResp from <MAC C-NA *HokusPokus 1> (capab=0x431 status=0 aid=6)
[ 2746.237261] wlan0: associated
[ 2746.269015] wlan0: deauthenticating from <MAC C-NA *HokusPokus 1> by local choice (reason=2)
[ 2746.273418] wlan0: authenticate with <MAC C-NA *HokusPokus 1>
[ 2746.276913] wlan0: send auth to <MAC C-NA *HokusPokus 1> (try 1/3)
[ 2746.278653] wlan0: authenticated
[ 2746.278924] iwlwifi 0000:03:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[ 2746.278933] iwlwifi 0000:03:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[ 2746.279262] wlan0: associate with <MAC C-NA *HokusPokus 1> (try 1/3)
[ 2746.281821] wlan0: RX AssocResp from <MAC C-NA *HokusPokus 1> (capab=0x431 status=0 aid=6)
[ 2746.284449] wlan0: associated
[ 2791.759393] wlan0: deauthenticating from <MAC C-NA *HokusPokus 1> by local choice (reason=3)
[ 2807.848245] wlan0: authenticate with <MAC C-NA *HokusPokus 1>
[ 2807.851769] wlan0: send auth to <MAC C-NA *HokusPokus 1> (try 1/3)
[ 2807.853420] wlan0: authenticated
[ 2807.853545] iwlwifi 0000:03:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[ 2807.853549] iwlwifi 0000:03:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[ 2807.854228] wlan0: associate with <MAC C-NA *HokusPokus 1> (try 1/3)
[ 2807.858256] wlan0: RX AssocResp from <MAC C-NA *HokusPokus 1> (capab=0x431 status=0 aid=5)
[ 2807.859650] wlan0: associated
[ 5398.292843] wlan0: deauthenticated from <MAC C-NA *HokusPokus 1> (Reason: 6)
[ 5398.316199] wlan0: authenticate with <MAC C-NA *HokusPokus 1>
[ 5398.319572] wlan0: send auth to <MAC C-NA *HokusPokus 1> (try 1/3)
[ 5398.321288] wlan0: authenticated
[ 5398.321657] iwlwifi 0000:03:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[ 5398.321668] iwlwifi 0000:03:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[ 5398.323467] wlan0: associate with <MAC C-NA *HokusPokus 1> (try 1/3)
[ 5398.325793] wlan0: RX AssocResp from <MAC C-NA *HokusPokus 1> (capab=0x431 status=0 aid=5)
[ 5398.327239] wlan0: associated
[ 5403.413987] wlan0: deauthenticated from <MAC C-NA *HokusPokus 1> (Reason: 2)
[ 5407.205742] wlan0: authenticate with <MAC C-NA *HokusPokus 1>
[ 5407.209300] wlan0: send auth to <MAC C-NA *HokusPokus 1> (try 1/3)
[ 5407.212816] wlan0: authenticated
[ 5407.214223] iwlwifi 0000:03:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[ 5407.214234] iwlwifi 0000:03:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[ 5407.214487] wlan0: associate with <MAC C-NA *HokusPokus 1> (try 1/3)
[ 5407.216879] wlan0: RX AssocResp from <MAC C-NA *HokusPokus 1> (capab=0x431 status=0 aid=5)
[ 5407.218522] wlan0: associated
[10288.221383] wlan0: deauthenticating from <MAC C-NA *HokusPokus 1> by local choice (reason=3)
[10291.084701] Bluetooth: hci0: Intel Bluetooth firmware file: intel/ibt-hw-37.7.10-fw-1.80.2.3.d.bseq
[10291.197564] Bluetooth: hci0: Intel Bluetooth firmware patch completed and activated
[10291.504086] iwlwifi 0000:03:00.0: L1 Enabled; Disabling L0S
[10291.504737] iwlwifi 0000:03:00.0: L1 Enabled; Disabling L0S
[10291.523775] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[10295.203218] wlan0: authenticate with <MAC C-NA *HokusPokus 1>
[10295.206737] wlan0: send auth to <MAC C-NA *HokusPokus 1> (try 1/3)
[10295.208429] wlan0: authenticated
[10295.208540] iwlwifi 0000:03:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[10295.208543] iwlwifi 0000:03:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[10295.211563] wlan0: associate with <MAC C-NA *HokusPokus 1> (try 1/3)
[10295.213818] wlan0: RX AssocResp from <MAC C-NA *HokusPokus 1> (capab=0x431 status=0 aid=5)
[10295.215291] wlan0: associated
[10295.215311] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[12855.062001] wlan0: deauthenticating from <MAC C-NA *HokusPokus 1> by local choice (reason=3)
[12858.133424] Bluetooth: hci0: Intel Bluetooth firmware file: intel/ibt-hw-37.7.10-fw-1.80.2.3.d.bseq
[12858.247367] Bluetooth: hci0: Intel Bluetooth firmware patch completed and activated
[12858.561098] iwlwifi 0000:03:00.0: L1 Enabled; Disabling L0S
[12858.561880] iwlwifi 0000:03:00.0: L1 Enabled; Disabling L0S
[12858.580825] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[12865.856756] wlan0: authenticate with <MAC C-NA *HokusPokus 1>
[12865.860704] wlan0: send auth to <MAC C-NA *HokusPokus 1> (try 1/3)
[12865.862618] wlan0: authenticated
[12865.862882] iwlwifi 0000:03:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[12865.862893] iwlwifi 0000:03:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[12865.866448] wlan0: associate with <MAC C-NA *HokusPokus 1> (try 1/3)
[12865.868767] wlan0: RX AssocResp from <MAC C-NA *HokusPokus 1> (capab=0x431 status=0 aid=6)
[12865.870362] wlan0: associated
[12865.870453] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[12865.895932] wlan0: deauthenticating from <MAC C-NA *HokusPokus 1> by local choice (reason=2)
[12865.900443] wlan0: authenticate with <MAC C-NA *HokusPokus 1>
[12865.904307] wlan0: send auth to <MAC C-NA *HokusPokus 1> (try 1/3)
[12865.906019] wlan0: authenticated
[12865.906136] iwlwifi 0000:03:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[12865.906140] iwlwifi 0000:03:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[12865.906401] wlan0: associate with <MAC C-NA *HokusPokus 1> (try 1/3)
[12865.908734] wlan0: RX AssocResp from <MAC C-NA *HokusPokus 1> (capab=0x431 status=0 aid=6)
[12865.910366] wlan0: associated
[13026.767604] wlan0: deauthenticating from <MAC C-NA *HokusPokus 1> by local choice (reason=3)
[13029.657646] Bluetooth: hci0: Intel Bluetooth firmware file: intel/ibt-hw-37.7.10-fw-1.80.2.3.d.bseq
[13029.780458] Bluetooth: hci0: Intel Bluetooth firmware patch completed and activated
[13030.061603] iwlwifi 0000:03:00.0: L1 Enabled; Disabling L0S
[13030.062207] iwlwifi 0000:03:00.0: L1 Enabled; Disabling L0S
[13030.081481] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[13033.766815] wlan0: authenticate with <MAC C-NA *HokusPokus 1>
[13033.770573] wlan0: send auth to <MAC C-NA *HokusPokus 1> (try 1/3)
[13033.772336] wlan0: authenticated
[13033.772451] iwlwifi 0000:03:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[13033.772453] iwlwifi 0000:03:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[13033.775165] wlan0: associate with <MAC C-NA *HokusPokus 1> (try 1/3)
[13033.777456] wlan0: RX AssocResp from <MAC C-NA *HokusPokus 1> (capab=0x431 status=0 aid=7)
[13033.778727] wlan0: associated
[13033.778757] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[13428.220957] wlan0: deauthenticating from <MAC C-NA *HokusPokus 1> by local choice (reason=3)
[13430.386299] Bluetooth: hci0: Intel Bluetooth firmware file: intel/ibt-hw-37.7.10-fw-1.80.2.3.d.bseq
[13430.525275] Bluetooth: hci0: Intel Bluetooth firmware patch completed and activated
[13430.690477] iwlwifi 0000:03:00.0: L1 Enabled; Disabling L0S
[13430.691117] iwlwifi 0000:03:00.0: L1 Enabled; Disabling L0S
[13430.709710] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[13434.390341] wlan0: authenticate with <MAC C-NA *HokusPokus 1>
[13434.393389] wlan0: send auth to <MAC C-NA *HokusPokus 1> (try 1/3)
[13434.395209] wlan0: authenticated
[13434.395339] iwlwifi 0000:03:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[13434.395342] iwlwifi 0000:03:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[13434.397311] wlan0: associate with <MAC C-NA *HokusPokus 1> (try 1/3)
[13434.399592] wlan0: RX AssocResp from <MAC C-NA *HokusPokus 1> (capab=0x431 status=0 aid=2)
[13434.400987] wlan0: associated
[13434.401010] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[15357.707329] wlan0: deauthenticated from <MAC C-NA *HokusPokus 1> (Reason: 6)
[15357.773988] wlan0: authenticate with <MAC C-NA *HokusPokus 1>
[15357.778015] wlan0: send auth to <MAC C-NA *HokusPokus 1> (try 1/3)
[15357.783731] wlan0: authenticated
[15357.784060] iwlwifi 0000:03:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[15357.784068] iwlwifi 0000:03:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[15357.786907] wlan0: associate with <MAC C-NA *HokusPokus 1> (try 1/3)
[15357.789264] wlan0: RX AssocResp from <MAC C-NA *HokusPokus 1> (capab=0x431 status=0 aid=2)
[15357.791292] wlan0: associated


	======== Done ========

```

---

