---
title: "Wifi authentication failure  (Intel Corporation Centrino Advanced-N 6235)"
date: 2014-07-22
forum: Networking &amp; Wireless
---

### Post by mattlach on 2014-07-22
Hey all,

Having a problem on a brand new install where the Wifi simply refuses to autheticate to my access point.   All other devices in the house connect just fine, as does this laptop when booted into windows.

A friend had his laptop over a few weeks back and had the same problem.

I ran the network inforation script found everywhere on these forums.  Results are below.   I know this is a Mint 17 install but it is based on 14.04, so I was hoping you guys might have some pointers.

```


	======== Wireless-Info START ========

System-Info ~~~~~~~~~~~~~~~~~~~~~~~~

snlaptop 3.13.0-24-generic x86_64,  Linux Mint 17 Qiana, qiana

CPU    : Intel(R) Core(TM) i5-3427U CPU @ 1.80GHz
Memory : 7848 MB
Uptime : 20:03:43 up  1:18,  2 users,  load average: 0.07, 0.03, 0.05


lspci ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

00:19.0 Ethernet controller [0200]: Intel Corporation 82579LM Gigabit Network Connection [8086:1502] (rev 04)
	Subsystem: Hewlett-Packard Company Device [103c:18df]
	Kernel driver in use: e1000e
--
03:00.0 Network controller [0280]: [8086:088e] (rev 24)
	Subsystem: Intel Corporation Centrino Advanced-N 6235 AGN [8086:4060]
	Kernel driver in use: iwlwifi


lsusb ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Bus 002 Device 003: ID 8087:07da Intel Corp. 
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 004: ID 05c8:034b Cheng Uei Precision Industry Co., Ltd (Foxlink) 
Bus 001 Device 003: ID 138a:003d Validity Sensors, Inc. 
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 002: ID 0781:5580 SanDisk Corp. SDCZ80 Flash Drive
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


PCMCIA Card Info ~~~~~~~~~~~~~~~~~~~



iwconfig ~~~~~~~~~~~~~~~~~~~~~~~~~~~

wlan0     IEEE 802.11abgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          


rfkill ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

      Interface        Soft blocked  Hard blocked
0: hci0: Bluetooth         no            no
1: phy0: Wireless LAN      no            no


lsmod ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

hp_wmi                 14062  0 
sparse_keymap          13948  1 hp_wmi
iwldvm                232285  0 
mac80211              626489  1 iwldvm
iwlwifi               169932  1 iwldvm
cfg80211              484040  3 iwlwifi,mac80211,iwldvm
wmi                    19177  1 hp_wmi


module parameters ~~~~~~~~~~~~~~~~~~

cfg80211      (2): cfg80211_disable_40mhz_24ghz=N | ieee80211_regdom=00
iwlwifi      (11): 11n_disable=0 | amsdu_size_8K=0 | antenna_coupling=0 | bt_coex_active=Y | fw_restart=Y | led_mode=0 | nvm_file=(null) | power_level=0 | power_save=N | swcrypto=0 | wd_disable=1
mac80211      (5): beacon_loss_count=7 | ieee80211_default_rc_algo=minstrel_ht | max_nullfunc_tries=2 | max_probe_tries=5 | probe_wait_ms=500
wmi           (2): debug_dump_wdg=N | debug_event=N


nm-tool ~~~~~~~~~~~~~~~~~~~~~~~~~~~~

State: connecting
=========================o=============o=========o==============o=========o===========o==============o===========
 Interface & ID          | Type        | Driver  | State        | Default | Speed     | Support      | HW Addr   
=========================o=============o=========o==============o=========o===========o==============o===========
 wlan0  [Auto Karlssano] | 802.11 WiFi | iwlwifi | connecting (configuring)| no      |           | WEP/WPA/WPA2 | <MAC wlan0>

    Karlssano:       Infra, <MAC C-01 Karlssano>, Freq 2412 MHz, Rate 54 Mb/s, Strength 100 WPA2
-------------------------+-------------+---------+--------------+---------+-----------+--------------+-----------
 eth0                    | Wired       | e1000e  | unavailable  | no      | 1000 Mb/s |              | <MAC eth0>
-------------------------+-------------+---------+--------------+---------+-----------+--------------+-----------


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

Auto Karlssano       : ssid=Karlssano | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 


interfaces ~~~~~~~~~~~~~~~~~~~~~~~~~

# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback

resolv.conf ~~~~~~~~~~~~~~~~~~~~~~~~



Routes & Ping ~~~~~~~~~~~~~~~~~~~~~~

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface


iw reg get ~~~~~~~~~~~~~~~~~~~~~~~~~

(Region : "en_US.UTF-8")
country 00:
	(2402 - 2472 @ 40), (3, 20)
	(2457 - 2482 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
	(2474 - 2494 @ 20), (3, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
	(5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
	(5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS


iwlist chan ~~~~~~~~~~~~~~~~~~~~~~~~

wlan0     32 channels in total; available frequencies :
          Channel 01 (2.412 GHz) - 13 (2.472 GHz)
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
          Channel 120 (5.6 GHz)
          Channel 124 (5.62 GHz)
          Channel 128 (5.64 GHz)
          Channel 132 (5.66 GHz)
          Channel 136 (5.68 GHz)
          Channel 140 (5.7 GHz) - 13 (2.472 GHz)


iwlist scan ~~~~~~~~~~~~~~~~~~~~~~~~

wlan0     Scan completed :
          Cell 01 - Address: <MAC C-01 Karlssano>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=70/70  Signal level=-34 dBm  
                    Encryption key:on
                    ESSID:"Karlssano"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000008047054b75
                    Extra: Last beacon: 36ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK

blacklist ~~~~~~~~~~~~~~~~~~~~~~~~~~

[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci


modinfo ~~~~~~~~~~~~~~~~~~~~~~~~~~~~

[iwldvm]
filename:       /lib/modules/3.13.0-24-generic/kernel/drivers/net/wireless/iwlwifi/dvm/iwldvm.ko
version:        in-tree:
srcversion:     03CC0BBD2BE23C16DB062DC
depends:        iwlwifi,mac80211,cfg80211

[mac80211]
filename:       /lib/modules/3.13.0-24-generic/kernel/net/mac80211/mac80211.ko
srcversion:     C0F95BBF832E05DEFD722F4
depends:        cfg80211
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[iwlwifi]
filename:       /lib/modules/3.13.0-24-generic/kernel/drivers/net/wireless/iwlwifi/iwlwifi.ko
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
firmware:       iwlwifi-3160-7.ucode
firmware:       iwlwifi-7260-7.ucode
srcversion:     1E6912E109D5A43B310FB34
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
filename:       /lib/modules/3.13.0-24-generic/kernel/net/wireless/cfg80211.ko
srcversion:     8B3D642D1F2E6406EF33F74
depends:        
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)


udev rules ~~~~~~~~~~~~~~~~~~~~~~~~~

# PCI device 0x8086:0x1502 (e1000e)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC eth0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

# PCI device 0x8086:0x088e (iwlwifi)
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

BOOT_IMAGE=/boot/vmlinuz-3.13.0-24-generic root=UUID=9326c97b-4cef-413d-8d43-6e0f61bde39b ro quiet splash vt.handoff=7


dmesg ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

[    2.588972] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[    2.589357] audit: initializing netlink socket (disabled)
[    3.334707] wmi: Mapper loaded
[   11.936628] iwlwifi 0000:03:00.0: can't disable ASPM; OS doesn't have ASPM control
[   11.936704] iwlwifi 0000:03:00.0: irq 48 for MSI/MSI-X
[   12.006341] iwlwifi 0000:03:00.0: loaded firmware version 18.168.6.1 op_mode iwldvm
[   12.083233] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   12.132527] iwlwifi 0000:03:00.0: CONFIG_IWLWIFI_DEBUG disabled
[   12.132534] iwlwifi 0000:03:00.0: CONFIG_IWLWIFI_DEBUGFS enabled
[   12.132537] iwlwifi 0000:03:00.0: CONFIG_IWLWIFI_DEVICE_TRACING enabled
[   12.132542] iwlwifi 0000:03:00.0: Detected Intel(R) Centrino(R) Advanced-N 6235 AGN, REV=0xB0
[   12.132626] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[   12.182190] ieee80211 phy0: Selected rate control algorithm 'iwl-agn-rs'
[   13.553360] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[   13.560024] iwlwifi 0000:03:00.0: Radio type=0x2-0x1-0x0
[   13.830556] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[   13.837236] iwlwifi 0000:03:00.0: Radio type=0x2-0x1-0x0
[   13.926864] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   13.927477] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  156.620214] wlan0: authenticate with <MAC C-01 Karlssano>
[  156.625066] wlan0: send auth to <MAC C-01 Karlssano> (try 1/3)
[  156.626816] wlan0: authenticated
[  156.627111] wlan0: AP has invalid WMM params (AIFSN=1 for ACI 2), disabling WMM
[  156.628760] wlan0: associate with <MAC C-01 Karlssano> (try 1/3)
[  156.631827] wlan0: RX AssocResp from <MAC C-01 Karlssano> (capab=0x431 status=37 aid=0)
[  156.631839] wlan0: <MAC C-01 Karlssano> denied association (code=37)
[  156.644073] wlan0: deauthenticating from <MAC C-01 Karlssano> by local choice (reason=3)
[  159.926007] wlan0: authenticate with <MAC C-01 Karlssano>
[  159.928386] wlan0: send auth to <MAC C-01 Karlssano> (try 1/3)
[  159.930132] wlan0: authenticated
[  159.930486] wlan0: AP has invalid WMM params (AIFSN=1 for ACI 2), disabling WMM
[  159.932741] wlan0: associate with <MAC C-01 Karlssano> (try 1/3)
[  159.935440] wlan0: RX AssocResp from <MAC C-01 Karlssano> (capab=0x431 status=37 aid=0)
[  159.935453] wlan0: <MAC C-01 Karlssano> denied association (code=37)
[  159.950123] wlan0: deauthenticating from <MAC C-01 Karlssano> by local choice (reason=3)
[  163.660256] wlan0: authenticate with <MAC C-01 Karlssano>
[  163.662961] wlan0: send auth to <MAC C-01 Karlssano> (try 1/3)
[  163.664820] wlan0: authenticated
[  163.665698] wlan0: AP has invalid WMM params (AIFSN=1 for ACI 2), disabling WMM
[  163.668720] wlan0: associate with <MAC C-01 Karlssano> (try 1/3)
[  163.671469] wlan0: RX AssocResp from <MAC C-01 Karlssano> (capab=0x431 status=37 aid=0)
[  163.671490] wlan0: <MAC C-01 Karlssano> denied association (code=37)
[  163.678622] wlan0: deauthenticating from <MAC C-01 Karlssano> by local choice (reason=3)
[  167.861639] wlan0: authenticate with <MAC C-01 Karlssano>
[  167.863897] wlan0: send auth to <MAC C-01 Karlssano> (try 1/3)
[  167.968692] wlan0: send auth to <MAC C-01 Karlssano> (try 2/3)
[  167.970586] wlan0: authenticated
[  167.971133] wlan0: AP has invalid WMM params (AIFSN=1 for ACI 2), disabling WMM
[  167.972653] wlan0: associate with <MAC C-01 Karlssano> (try 1/3)
[  167.975439] wlan0: RX AssocResp from <MAC C-01 Karlssano> (capab=0x431 status=37 aid=0)
[  167.975451] wlan0: <MAC C-01 Karlssano> denied association (code=37)
[  167.978396] wlan0: deauthenticating from <MAC C-01 Karlssano> by local choice (reason=3)
[  190.240063] wlan0: authenticate with <MAC C-01 Karlssano>
[  190.241043] wlan0: send auth to <MAC C-01 Karlssano> (try 1/3)
[  190.242899] wlan0: authenticated
[  190.243353] wlan0: AP has invalid WMM params (AIFSN=1 for ACI 2), disabling WMM
[  190.244420] wlan0: associate with <MAC C-01 Karlssano> (try 1/3)
[  190.247234] wlan0: RX AssocResp from <MAC C-01 Karlssano> (capab=0x431 status=37 aid=0)
[  190.247246] wlan0: <MAC C-01 Karlssano> denied association (code=37)
[  190.262043] wlan0: deauthenticating from <MAC C-01 Karlssano> by local choice (reason=3)
[  203.450282] wlan0: authenticate with <MAC C-01 Karlssano>
[  203.452417] wlan0: send auth to <MAC C-01 Karlssano> (try 1/3)
[  203.556241] wlan0: send auth to <MAC C-01 Karlssano> (try 2/3)
[  203.558121] wlan0: authenticated
[  203.558662] wlan0: AP has invalid WMM params (AIFSN=1 for ACI 2), disabling WMM
[  203.560211] wlan0: associate with <MAC C-01 Karlssano> (try 1/3)
[  203.563030] wlan0: RX AssocResp from <MAC C-01 Karlssano> (capab=0x431 status=37 aid=0)
[  203.563043] wlan0: <MAC C-01 Karlssano> denied association (code=37)
[  203.565933] wlan0: deauthenticating from <MAC C-01 Karlssano> by local choice (reason=3)
[ 1535.488278] wlan0: authenticate with <MAC C-01 Karlssano>
[ 1535.490814] wlan0: send auth to <MAC C-01 Karlssano> (try 1/3)
[ 1535.492702] wlan0: authenticated
[ 1535.493411] wlan0: AP has invalid WMM params (AIFSN=1 for ACI 2), disabling WMM
[ 1535.494552] wlan0: associate with <MAC C-01 Karlssano> (try 1/3)
[ 1535.497290] wlan0: RX AssocResp from <MAC C-01 Karlssano> (capab=0x431 status=37 aid=0)
[ 1535.497302] wlan0: <MAC C-01 Karlssano> denied association (code=37)
[ 1535.508272] wlan0: deauthenticating from <MAC C-01 Karlssano> by local choice (reason=3)
[ 1548.691813] wlan0: authenticate with <MAC C-01 Karlssano>
[ 1548.694390] wlan0: send auth to <MAC C-01 Karlssano> (try 1/3)
[ 1548.696211] wlan0: authenticated
[ 1548.696903] wlan0: AP has invalid WMM params (AIFSN=1 for ACI 2), disabling WMM
[ 1548.699742] wlan0: associate with <MAC C-01 Karlssano> (try 1/3)
[ 1548.702461] wlan0: RX AssocResp from <MAC C-01 Karlssano> (capab=0x431 status=37 aid=6531)
[ 1548.702482] wlan0: <MAC C-01 Karlssano> denied association (code=37)
[ 1548.709559] wlan0: deauthenticating from <MAC C-01 Karlssano> by local choice (reason=3)
[ 1569.631762] wlan0: authenticate with <MAC C-01 Karlssano>
[ 1569.632779] wlan0: send auth to <MAC C-01 Karlssano> (try 1/3)
[ 1569.634640] wlan0: authenticated
[ 1569.635172] wlan0: AP has invalid WMM params (AIFSN=1 for ACI 2), disabling WMM
[ 1569.637622] wlan0: associate with <MAC C-01 Karlssano> (try 1/3)
[ 1569.640421] wlan0: RX AssocResp from <MAC C-01 Karlssano> (capab=0x431 status=37 aid=0)
[ 1569.640433] wlan0: <MAC C-01 Karlssano> denied association (code=37)
[ 1569.650569] wlan0: deauthenticating from <MAC C-01 Karlssano> by local choice (reason=3)
[ 1582.832910] wlan0: authenticate with <MAC C-01 Karlssano>
[ 1582.835352] wlan0: send auth to <MAC C-01 Karlssano> (try 1/3)
[ 1582.938233] wlan0: send auth to <MAC C-01 Karlssano> (try 2/3)
[ 1582.940124] wlan0: authenticated
[ 1582.940699] wlan0: AP has invalid WMM params (AIFSN=1 for ACI 2), disabling WMM
[ 1582.942225] wlan0: associate with <MAC C-01 Karlssano> (try 1/3)
[ 1582.945053] wlan0: RX AssocResp from <MAC C-01 Karlssano> (capab=0x431 status=37 aid=6531)
[ 1582.945068] wlan0: <MAC C-01 Karlssano> denied association (code=37)
[ 1582.948338] wlan0: deauthenticating from <MAC C-01 Karlssano> by local choice (reason=3)
[ 1685.275285] wlan0: authenticate with <MAC C-01 Karlssano>
[ 1685.277585] wlan0: send auth to <MAC C-01 Karlssano> (try 1/3)
[ 1685.279370] wlan0: authenticated
[ 1685.279707] wlan0: AP has invalid WMM params (AIFSN=1 for ACI 2), disabling WMM
[ 1685.281123] wlan0: associate with <MAC C-01 Karlssano> (try 1/3)
[ 1685.283781] wlan0: RX AssocResp from <MAC C-01 Karlssano> (capab=0x431 status=37 aid=0)
[ 1685.283791] wlan0: <MAC C-01 Karlssano> denied association (code=37)
[ 1685.300544] wlan0: deauthenticating from <MAC C-01 Karlssano> by local choice (reason=3)
[ 1689.400704] wlan0: authenticate with <MAC C-01 Karlssano>
[ 1689.403330] wlan0: send auth to <MAC C-01 Karlssano> (try 1/3)
[ 1689.405118] wlan0: authenticated
[ 1689.405828] wlan0: AP has invalid WMM params (AIFSN=1 for ACI 2), disabling WMM
[ 1689.408941] wlan0: associate with <MAC C-01 Karlssano> (try 1/3)
[ 1689.411665] wlan0: RX AssocResp from <MAC C-01 Karlssano> (capab=0x431 status=37 aid=0)
[ 1689.411679] wlan0: <MAC C-01 Karlssano> denied association (code=37)
[ 1689.422601] wlan0: deauthenticating from <MAC C-01 Karlssano> by local choice (reason=3)
[ 1689.423382] wlan0: authenticate with <MAC C-01 Karlssano>
[ 1689.425855] wlan0: send auth to <MAC C-01 Karlssano> (try 1/3)
[ 1689.528822] wlan0: send auth to <MAC C-01 Karlssano> (try 2/3)
[ 1689.530737] wlan0: authenticated
[ 1689.531279] wlan0: AP has invalid WMM params (AIFSN=1 for ACI 2), disabling WMM
[ 1689.532800] wlan0: associate with <MAC C-01 Karlssano> (try 1/3)
[ 1689.535561] wlan0: RX AssocResp from <MAC C-01 Karlssano> (capab=0x431 status=37 aid=0)
[ 1689.535588] wlan0: <MAC C-01 Karlssano> denied association (code=37)
[ 1689.538613] wlan0: deauthenticating from <MAC C-01 Karlssano> by local choice (reason=3)
[ 1700.942956] wlan0: authenticate with <MAC C-01 Karlssano>
[ 1700.945255] wlan0: send auth to <MAC C-01 Karlssano> (try 1/3)
[ 1701.049146] wlan0: send auth to <MAC C-01 Karlssano> (try 2/3)
[ 1701.051021] wlan0: authenticated
[ 1701.051517] wlan0: AP has invalid WMM params (AIFSN=1 for ACI 2), disabling WMM
[ 1701.053128] wlan0: associate with <MAC C-01 Karlssano> (try 1/3)
[ 1701.055891] wlan0: RX AssocResp from <MAC C-01 Karlssano> (capab=0x431 status=37 aid=0)
[ 1701.055904] wlan0: <MAC C-01 Karlssano> denied association (code=37)
[ 1701.062839] wlan0: deauthenticating from <MAC C-01 Karlssano> by local choice (reason=3)
[ 1714.274170] wlan0: authenticate with <MAC C-01 Karlssano>
[ 1714.276689] wlan0: send auth to <MAC C-01 Karlssano> (try 1/3)
[ 1714.380386] wlan0: send auth to <MAC C-01 Karlssano> (try 2/3)
[ 1714.382295] wlan0: authenticated
[ 1714.382820] wlan0: AP has invalid WMM params (AIFSN=1 for ACI 2), disabling WMM
[ 1714.384310] wlan0: associate with <MAC C-01 Karlssano> (try 1/3)
[ 1714.387104] wlan0: RX AssocResp from <MAC C-01 Karlssano> (capab=0x431 status=37 aid=0)
[ 1714.387116] wlan0: <MAC C-01 Karlssano> denied association (code=37)
[ 1714.390383] wlan0: deauthenticating from <MAC C-01 Karlssano> by local choice (reason=3)
[ 1966.074246] wlan0: authenticate with <MAC C-01 Karlssano>
[ 1966.076741] wlan0: send auth to <MAC C-01 Karlssano> (try 1/3)
[ 1966.078506] wlan0: authenticated
[ 1966.079038] wlan0: AP has invalid WMM params (AIFSN=1 for ACI 2), disabling WMM
[ 1966.082582] wlan0: associate with <MAC C-01 Karlssano> (try 1/3)
[ 1966.085239] wlan0: RX AssocResp from <MAC C-01 Karlssano> (capab=0x431 status=37 aid=0)
[ 1966.085253] wlan0: <MAC C-01 Karlssano> denied association (code=37)
[ 1966.095909] wlan0: deauthenticating from <MAC C-01 Karlssano> by local choice (reason=3)
[ 1973.013556] wlan0: authenticate with <MAC C-01 Karlssano>
[ 1973.014821] wlan0: send auth to <MAC C-01 Karlssano> (try 1/3)
[ 1973.119028] wlan0: send auth to <MAC C-01 Karlssano> (try 2/3)
[ 1973.120892] wlan0: authenticated
[ 1973.121440] wlan0: AP has invalid WMM params (AIFSN=1 for ACI 2), disabling WMM
[ 1973.123001] wlan0: associate with <MAC C-01 Karlssano> (try 1/3)
[ 1973.125773] wlan0: RX AssocResp from <MAC C-01 Karlssano> (capab=0x431 status=37 aid=12911)
[ 1973.125789] wlan0: <MAC C-01 Karlssano> denied association (code=37)
[ 1973.132741] wlan0: deauthenticating from <MAC C-01 Karlssano> by local choice (reason=3)
[ 1973.133515] wlan0: authenticate with <MAC C-01 Karlssano>
[ 1973.136072] wlan0: send auth to <MAC C-01 Karlssano> (try 1/3)
[ 1973.137958] wlan0: authenticated
[ 1973.138502] wlan0: AP has invalid WMM params (AIFSN=1 for ACI 2), disabling WMM
[ 1973.138971] wlan0: associate with <MAC C-01 Karlssano> (try 1/3)
[ 1973.141755] wlan0: RX AssocResp from <MAC C-01 Karlssano> (capab=0x431 status=37 aid=0)
[ 1973.141767] wlan0: <MAC C-01 Karlssano> denied association (code=37)
[ 1973.148620] wlan0: deauthenticating from <MAC C-01 Karlssano> by local choice (reason=3)
[ 1984.120666] wlan0: authenticate with <MAC C-01 Karlssano>
[ 1984.123089] wlan0: send auth to <MAC C-01 Karlssano> (try 1/3)
[ 1984.229328] wlan0: send auth to <MAC C-01 Karlssano> (try 2/3)
[ 1984.231227] wlan0: authenticated
[ 1984.231715] wlan0: AP has invalid WMM params (AIFSN=1 for ACI 2), disabling WMM
[ 1984.233336] wlan0: associate with <MAC C-01 Karlssano> (try 1/3)
[ 1984.236022] wlan0: RX AssocResp from <MAC C-01 Karlssano> (capab=0x431 status=37 aid=0)
[ 1984.236036] wlan0: <MAC C-01 Karlssano> denied association (code=37)
[ 1984.242644] wlan0: deauthenticating from <MAC C-01 Karlssano> by local choice (reason=3)
[ 1987.739440] wlan0: authenticate with <MAC C-01 Karlssano>
[ 1987.742007] wlan0: send auth to <MAC C-01 Karlssano> (try 1/3)
[ 1987.847480] wlan0: send auth to <MAC C-01 Karlssano> (try 2/3)
[ 1987.849332] wlan0: authenticated
[ 1987.849881] wlan0: AP has invalid WMM params (AIFSN=1 for ACI 2), disabling WMM
[ 1987.851475] wlan0: associate with <MAC C-01 Karlssano> (try 1/3)
[ 1987.854273] wlan0: RX AssocResp from <MAC C-01 Karlssano> (capab=0x431 status=37 aid=10340)
[ 1987.854286] wlan0: <MAC C-01 Karlssano> denied association (code=37)
[ 1987.861161] wlan0: deauthenticating from <MAC C-01 Karlssano> by local choice (reason=3)
[ 1987.861943] wlan0: authenticate with <MAC C-01 Karlssano>
[ 1987.864278] wlan0: send auth to <MAC C-01 Karlssano> (try 1/3)
[ 1987.866059] wlan0: authenticated
[ 1987.866605] wlan0: AP has invalid WMM params (AIFSN=1 for ACI 2), disabling WMM
[ 1987.867449] wlan0: associate with <MAC C-01 Karlssano> (try 1/3)
[ 1987.870273] wlan0: RX AssocResp from <MAC C-01 Karlssano> (capab=0x431 status=37 aid=0)
[ 1987.870285] wlan0: <MAC C-01 Karlssano> denied association (code=37)
[ 1987.885332] wlan0: deauthenticating from <MAC C-01 Karlssano> by local choice (reason=3)
[ 1991.694863] wlan0: authenticate with <MAC C-01 Karlssano>
[ 1991.697168] wlan0: send auth to <MAC C-01 Karlssano> (try 1/3)
[ 1991.699049] wlan0: authenticated
[ 1991.699831] wlan0: AP has invalid WMM params (AIFSN=1 for ACI 2), disabling WMM
[ 1991.701507] wlan0: associate with <MAC C-01 Karlssano> (try 1/3)
[ 1991.704328] wlan0: RX AssocResp from <MAC C-01 Karlssano> (capab=0x431 status=37 aid=3455)
[ 1991.704345] wlan0: <MAC C-01 Karlssano> denied association (code=37)
[ 1991.719265] wlan0: deauthenticating from <MAC C-01 Karlssano> by local choice (reason=3)
[ 1991.720100] wlan0: authenticate with <MAC C-01 Karlssano>
[ 1991.722612] wlan0: send auth to <MAC C-01 Karlssano> (try 1/3)
[ 1991.728339] wlan0: authenticated
[ 1991.728913] wlan0: AP has invalid WMM params (AIFSN=1 for ACI 2), disabling WMM
[ 1991.729431] wlan0: associate with <MAC C-01 Karlssano> (try 1/3)
[ 1991.732222] wlan0: RX AssocResp from <MAC C-01 Karlssano> (capab=0x431 status=37 aid=0)
[ 1991.732234] wlan0: <MAC C-01 Karlssano> denied association (code=37)
[ 1991.739146] wlan0: deauthenticating from <MAC C-01 Karlssano> by local choice (reason=3)
[ 1998.017656] wlan0: authenticate with <MAC C-01 Karlssano>
[ 1998.020027] wlan0: send auth to <MAC C-01 Karlssano> (try 1/3)
[ 1998.021840] wlan0: authenticated
[ 1998.022467] wlan0: AP has invalid WMM params (AIFSN=1 for ACI 2), disabling WMM
[ 1998.026243] wlan0: associate with <MAC C-01 Karlssano> (try 1/3)
[ 1998.028975] wlan0: RX AssocResp from <MAC C-01 Karlssano> (capab=0x431 status=37 aid=0)
[ 1998.028989] wlan0: <MAC C-01 Karlssano> denied association (code=37)
[ 1998.039947] wlan0: deauthenticating from <MAC C-01 Karlssano> by local choice (reason=3)
[ 1998.040753] wlan0: authenticate with <MAC C-01 Karlssano>
[ 1998.043320] wlan0: send auth to <MAC C-01 Karlssano> (try 1/3)
[ 1998.146216] wlan0: send auth to <MAC C-01 Karlssano> (try 2/3)
[ 1998.148095] wlan0: authenticated
[ 1998.148606] wlan0: AP has invalid WMM params (AIFSN=1 for ACI 2), disabling WMM
[ 1998.150182] wlan0: associate with <MAC C-01 Karlssano> (try 1/3)
[ 1998.152960] wlan0: RX AssocResp from <MAC C-01 Karlssano> (capab=0x431 status=37 aid=0)
[ 1998.152973] wlan0: <MAC C-01 Karlssano> denied association (code=37)
[ 1998.156203] wlan0: deauthenticating from <MAC C-01 Karlssano> by local choice (reason=3)
[ 1998.156753] wlan0: authenticate with <MAC C-01 Karlssano>
[ 1998.158918] wlan0: send auth to <MAC C-01 Karlssano> (try 1/3)
[ 1998.160718] wlan0: authenticated
[ 1998.161087] wlan0: AP has invalid WMM params (AIFSN=1 for ACI 2), disabling WMM
[ 1998.162135] wlan0: associate with <MAC C-01 Karlssano> (try 1/3)
[ 1998.164910] wlan0: RX AssocResp from <MAC C-01 Karlssano> (capab=0x431 status=37 aid=0)
[ 1998.164922] wlan0: <MAC C-01 Karlssano> denied association (code=37)
[ 1998.171821] wlan0: deauthenticating from <MAC C-01 Karlssano> by local choice (reason=3)
[ 1998.172813] wlan0: authenticate with <MAC C-01 Karlssano>
[ 1998.176526] wlan0: send auth to <MAC C-01 Karlssano> (try 1/3)
[ 1998.282122] wlan0: send auth to <MAC C-01 Karlssano> (try 2/3)
[ 1998.283981] wlan0: authenticated
[ 1998.284518] wlan0: AP has invalid WMM params (AIFSN=1 for ACI 2), disabling WMM
[ 1998.286140] wlan0: associate with <MAC C-01 Karlssano> (try 1/3)
[ 1998.288947] wlan0: RX AssocResp from <MAC C-01 Karlssano> (capab=0x431 status=37 aid=0)
[ 1998.288969] wlan0: <MAC C-01 Karlssano> denied association (code=37)
[ 1998.292392] wlan0: deauthenticating from <MAC C-01 Karlssano> by local choice (reason=3)
[ 1998.293053] wlan0: authenticate with <MAC C-01 Karlssano>
[ 1998.295633] wlan0: send auth to <MAC C-01 Karlssano> (try 1/3)
[ 1998.297400] wlan0: authenticated
[ 1998.297896] wlan0: AP has invalid WMM params (AIFSN=1 for ACI 2), disabling WMM
[ 1998.298198] wlan0: associate with <MAC C-01 Karlssano> (try 1/3)
[ 1998.300942] wlan0: RX AssocResp from <MAC C-01 Karlssano> (capab=0x431 status=37 aid=0)
[ 1998.300954] wlan0: <MAC C-01 Karlssano> denied association (code=37)
[ 1998.315881] wlan0: deauthenticating from <MAC C-01 Karlssano> by local choice (reason=3)
[ 2011.180648] wlan0: authenticate with <MAC C-01 Karlssano>
[ 2011.183085] wlan0: send auth to <MAC C-01 Karlssano> (try 1/3)
[ 2011.287427] wlan0: send auth to <MAC C-01 Karlssano> (try 2/3)
[ 2011.289302] wlan0: authenticated
[ 2011.289783] wlan0: AP has invalid WMM params (AIFSN=1 for ACI 2), disabling WMM
[ 2011.291420] wlan0: associate with <MAC C-01 Karlssano> (try 1/3)
[ 2011.294183] wlan0: RX AssocResp from <MAC C-01 Karlssano> (capab=0x431 status=37 aid=0)
[ 2011.294196] wlan0: <MAC C-01 Karlssano> denied association (code=37)
[ 2011.301336] wlan0: deauthenticating from <MAC C-01 Karlssano> by local choice (reason=3)
[ 2024.486570] wlan0: authenticate with <MAC C-01 Karlssano>
[ 2024.488870] wlan0: send auth to <MAC C-01 Karlssano> (try 1/3)
[ 2024.592591] wlan0: send auth to <MAC C-01 Karlssano> (try 2/3)
[ 2024.594378] wlan0: authenticated
[ 2024.594720] wlan0: AP has invalid WMM params (AIFSN=1 for ACI 2), disabling WMM
[ 2024.596601] wlan0: associate with <MAC C-01 Karlssano> (try 1/3)
[ 2024.599212] wlan0: RX AssocResp from <MAC C-01 Karlssano> (capab=0x431 status=37 aid=0)
[ 2024.599225] wlan0: <MAC C-01 Karlssano> denied association (code=37)
[ 2024.605868] wlan0: deauthenticating from <MAC C-01 Karlssano> by local choice (reason=3)
[ 4723.155229] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[ 4723.161911] iwlwifi 0000:03:00.0: Radio type=0x2-0x1-0x0
[ 4723.248160] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 4729.622389] wlan0: authenticate with <MAC C-01 Karlssano>
[ 4729.625275] wlan0: send auth to <MAC C-01 Karlssano> (try 1/3)
[ 4729.627054] wlan0: authenticated
[ 4729.627677] wlan0: AP has invalid WMM params (AIFSN=1 for ACI 2), disabling WMM
[ 4729.629801] wlan0: associate with <MAC C-01 Karlssano> (try 1/3)
[ 4729.632571] wlan0: RX AssocResp from <MAC C-01 Karlssano> (capab=0x431 status=37 aid=0)
[ 4729.632582] wlan0: <MAC C-01 Karlssano> denied association (code=37)
[ 4729.639640] wlan0: deauthenticating from <MAC C-01 Karlssano> by local choice (reason=3)
[ 4729.640191] wlan0: authenticate with <MAC C-01 Karlssano>
[ 4729.642546] wlan0: send auth to <MAC C-01 Karlssano> (try 1/3)
[ 4729.644418] wlan0: authenticated
[ 4729.644933] wlan0: AP has invalid WMM params (AIFSN=1 for ACI 2), disabling WMM
[ 4729.645774] wlan0: associate with <MAC C-01 Karlssano> (try 1/3)
[ 4729.648575] wlan0: RX AssocResp from <MAC C-01 Karlssano> (capab=0x431 status=37 aid=768)
[ 4729.648587] wlan0: <MAC C-01 Karlssano> denied association (code=37)
[ 4729.655497] wlan0: deauthenticating from <MAC C-01 Karlssano> by local choice (reason=3)
[ 4733.362713] wlan0: authenticate with <MAC C-01 Karlssano>
[ 4733.365188] wlan0: send auth to <MAC C-01 Karlssano> (try 1/3)
[ 4733.471833] wlan0: send auth to <MAC C-01 Karlssano> (try 2/3)
[ 4733.473708] wlan0: authenticated
[ 4733.474219] wlan0: AP has invalid WMM params (AIFSN=1 for ACI 2), disabling WMM
[ 4733.475832] wlan0: associate with <MAC C-01 Karlssano> (try 1/3)
[ 4733.478643] wlan0: RX AssocResp from <MAC C-01 Karlssano> (capab=0x431 status=37 aid=12911)
[ 4733.478655] wlan0: <MAC C-01 Karlssano> denied association (code=37)
[ 4733.481447] wlan0: deauthenticating from <MAC C-01 Karlssano> by local choice (reason=3)
[ 4737.663888] wlan0: authenticate with <MAC C-01 Karlssano>
[ 4737.666011] wlan0: send auth to <MAC C-01 Karlssano> (try 1/3)
[ 4737.769542] wlan0: send auth to <MAC C-01 Karlssano> (try 2/3)
[ 4737.771204] wlan0: authenticated
[ 4737.771380] wlan0: AP has invalid WMM params (AIFSN=1 for ACI 2), disabling WMM
[ 4737.773547] wlan0: associate with <MAC C-01 Karlssano> (try 1/3)
[ 4737.776122] wlan0: RX AssocResp from <MAC C-01 Karlssano> (capab=0x431 status=37 aid=0)
[ 4737.776125] wlan0: <MAC C-01 Karlssano> denied association (code=37)
[ 4737.782528] wlan0: deauthenticating from <MAC C-01 Karlssano> by local choice (reason=3)
[ 4748.272235] wlan0: authenticate with <MAC C-01 Karlssano>
[ 4748.274865] wlan0: send auth to <MAC C-01 Karlssano> (try 1/3)
[ 4748.380135] wlan0: send auth to <MAC C-01 Karlssano> (try 2/3)
[ 4748.381901] wlan0: authenticated
[ 4748.382201] wlan0: AP has invalid WMM params (AIFSN=1 for ACI 2), disabling WMM
[ 4748.384137] wlan0: associate with <MAC C-01 Karlssano> (try 1/3)
[ 4748.386752] wlan0: RX AssocResp from <MAC C-01 Karlssano> (capab=0x431 status=37 aid=0)
[ 4748.386759] wlan0: <MAC C-01 Karlssano> denied association (code=37)
[ 4748.405426] wlan0: deauthenticating from <MAC C-01 Karlssano> by local choice (reason=3)

	======== Done ========
```

The behavior is similar to other threads I have found where Ubuntu won't authenticate to WPA2-Enterprise without certificates (a known bug) but my access point (a Ubiquiti Unifi) is set to WPA2 personal (AES/CCMP only), 802.11n only, and HT20.

It seems to be the combination of Ubuntu and my access point that is the problem. 

I'm not really familiar with the wlan0 output from dmesg in the report above.   Does it provide those of you with more knowledge on the subject what might be going on?

Much obliged,
Matt

---

### Post by praseodym on 2014-07-23
Try to deactivate the N-mode of the driver and the queue:
```

echo "options iwlwifi 11n_disable=1 wd_disable=1" | sudo tee /etc/modprobe.d/iwlwifi.conf
sudo modprobe -rfv iwlwifi
sudo modprobe -v iwlwifi
```

---

### Post by mattlach on 2014-07-23
Thank you for the suggestion.

Is 802.11n a known shortcoming under Linux for this WiFi chip?

If this is the cause I will have to change the settings on my AP, as I currently have it set up to be n only, without g or earlier compatibility.

---

### Post by praseodym on 2014-07-23
Yes, it is. But changing the driver settings helps with other APs in the future...

---

### Post by mattlach on 2014-07-23
Is the iwlwifi module part of the kernel package?

Maybe it has been improved upstream?   Might it be worth trying a later upstream kernel/module before I go ahead and disable N and reconfigure my AP?

---

### Post by jeremy31 on 2014-07-23
> **mattlach said:**
> Is the iwlwifi module part of the kernel package?

Maybe it has been improved upstream?   Might it be worth trying a later upstream kernel/module before I go ahead and disable N and reconfigure my AP?

That is your choice, and it might work.  I usually download and try out the latest stable kernels

---

### Post by mattlach on 2014-07-23
Turns I didn't even need to disable N in the driver options.   Simply switching my access point from N only mode to g/n mode allowed me to connect.

I hope this gets fixed upstream soon!  I hate workarounds, and settling for less than my hardware is capable of.

---

### Post by varunendra on 2014-07-24
So are you getting only g-mode speeds only (54 Mbps max)? If yes, I suggest also trying "swcrypto=1" and "bt_coex_active=N" parameters (as explained [here]("http://ubuntuforums.org/showpost.php?p=12943350")) to see if you can get advantage of N-speeds.

My awareness about these drivers and related developments is not as good as praseodym's, but the kernel version you are using is one of the latest ones, so we should expect proper support for N channel from it. Although just yesterday I read a couple of posts suggesting the N-6235 card is not performing as good as slightly older N-6200 with the current kernel versions, so there may be some minor glitch with this particular card that will, hopefully, be fixed in future updates.

---

### Post by mattlach on 2014-07-26
> **varunendra said:**
> So are you getting only g-mode speeds only (54 Mbps max)? If yes, I suggest also trying "swcrypto=1" and "bt_coex_active=N" parameters (as explained [here]("http://ubuntuforums.org/showpost.php?p=12943350")) to see if you can get advantage of N-speeds.

My awareness about these drivers and related developments is not as good as praseodym's, but the kernel version you are using is one of the latest ones, so we should expect proper support for N channel from it. Although just yesterday I read a couple of posts suggesting the N-6235 card is not performing as good as slightly older N-6200 with the current kernel versions, so there may be some minor glitch with this particular card that will, hopefully, be fixed in future updates.

Yep, it is connected as a 802.11G device.

Thank you for those suggestions.   I will give them a try.

As always, Linux is great, but lags in hardware compatibility, due to us not being the priority of the hardware manufacturers...   Hoping for an upstream kernel fix as well!

---

### Post by mattlach on 2014-07-26
I appreciate the suggestion to try ""swcrypto=1" and "bt_coex_active=N", but unfortunately they had no impact on N capability.  It is still connecting in G mode.

Looks like I will just have to wait for driver fixes.

---

### Post by varunendra on 2014-07-26
There is also an issue with firmware versions in case of Intel AC 7260 chips. Although that seems to be specific to 7260 and 3160 chips due to rapid firmware development, others should be fine if using any kernel version of 3x series (as per the compatibility table [here]("http://www.intel.com/support/wireless/wlan/sb/CS-034398.htm")). But just to make sure that you are using firmware version 18x or above, please post the output of -
```
sudo lshw -C network | grep iwlwifi
```

---

### Post by weatherman2 on 2014-07-27
For what it's worth, I'm using the Intel 6235 wireless card successfully in several laptops running Ubuntu 12.04.2 (that would be kernel 3.5).  I connect at N speeds to both 2.4GHZ and 5GHZ access points, and I get excellent download speeds.  I don't have any iwlwifi overrides - I don't need them.  I've connected to a few dozen access points successfully, without issues anywhere.

---

### Post by mattlach on 2014-07-27
> **varunendra said:**
> There is also an issue with firmware versions in case of Intel AC 7260 chips. Although that seems to be specific to 7260 and 3160 chips due to rapid firmware development, others should be fine if using any kernel version of 3x series (as per the compatibility table [here]("http://www.intel.com/support/wireless/wlan/sb/CS-034398.htm")). But just to make sure that you are using firmware version 18x or above, please post the output of -
```
sudo lshw -C network | grep iwlwifi
```

Thanks for the suggestion.   It looks like I am indeed on 18+

```
configuration: broadcast=yes driver=iwlwifi driverversion=3.13.0-24-generic firmware=18.168.6.1 ip=10.0.1.140 latency=0 link=yes multicast=yes wireless=IEEE 802.11abgn
```


> **weatherman2 said:**
> For what it's worth, I'm using the Intel 6235 wireless card successfully in several laptops running Ubuntu 12.04.2 (that would be kernel 3.5).  I connect at N speeds to both 2.4GHZ and 5GHZ access points, and I get excellent download speeds.  I don't have any iwlwifi overrides - I don't need them.  I've connected to a few dozen access points successfully, without issues anywhere.

Interesting. I've heard it suggested that it depends on the method of authentication.   That N connections fail if you use WPA2 without a certificate.  The drivers assume a certificate is supposed to be present, and when it isn't fail to connect.

I've also heard it suggested that this issue didn't exist prior to 14.04, and that a bug may have been introduced to this kerner revision upstream...

What type of authentication have you used?  Have you tried it on 14.04 in addition to 12.04?

Thanks,
Matt

---

### Post by jeremy31 on 2014-07-27
I keep seeing this in the dmesg part of the wireless-info ```
wlan0: AP has invalid WMM params (AIFSN=1 for ACI 2), disabling WMM
```
So disabling WMM on the router might be a solution

---

### Post by mattlach on 2014-07-27
Yeah, I'm seeing that too.   What is WMM anyway?

---

### Post by jeremy31 on 2014-07-27
> **mattlach said:**
> Yeah, I'm seeing that too.   What is WMM anyway?
Not exactly sure without doing a google search, my router(cellular hotspot) shows no such option

---

### Post by weatherman2 on 2014-07-27
> **mattlach said:**
> Interesting. I've heard it suggested that it depends on the method of authentication.   That N connections fail if you use WPA2 without a certificate.  The drivers assume a certificate is supposed to be present, and when it isn't fail to connect.

I've also heard it suggested that this issue didn't exist prior to 14.04, and that a bug may have been introduced to this kerner revision upstream...

What type of authentication have you used?  Have you tried it on 14.04 in addition to 12.04?

Only used with 12.04.2 as far as I know.  I'll have to boot up 14.04 on of my laptops and try it.  I have used an Intel 5100 card (same iwlwifi driver, probably different firmware) successfully with 14.04 and WPA2/no certificates.

I've used WPA2, WEP, and none (various access points, some not secured) without any certificates in 12.04.2 and the 6235.

---

### Post by jeremy31 on 2014-07-27
> **weatherman2 said:**
> Only used with 12.04.2 as far as I know.  I'll have to boot up 14.04 on of my laptops and try it.  I have used an Intel 5100 card (same iwlwifi driver, probably different firmware) successfully with 14.04 and WPA2/no certificates.

I've used WPA2, WEP, and none (various access points, some not secured) without any certificates in 12.04.2 and the 6235.

It could always be the router that has an issue...otherwise why would you need to install software in windows for a router when most of them have a web based control interface

---

### Post by mattlach on 2014-07-28
> **jeremy31 said:**
> It could always be the router that has an issue...otherwise why would you need to install software in windows for a router when most of them have a web based control interface

What kind of routers have you used that require special software?

Usually they just use standard networking interfaces.

I doubt the router/access point in my network is to blame, as all other hardware works fine, as does the same laptop under windows, but for what it is worth, my setup is as follows:

Router:  pfSense
AP: Ubiquiti Unifi LR (2.4ghz b/g/n, set up with WPA2 Personal, AES/TKIP, and HT20)

---

### Post by jeremy31 on 2014-07-28
It was a cheap Belkin that I trashed after I couldn't connect to it with my android phone, the netgear I replaced it with has worked with everything and my ZTE mobile hotspot has no issues

---

### Post by varunendra on 2014-07-29
> **mattlach said:**
> Yeah, I'm seeing that too.   What is WMM anyway?

Probably not a useful response at this time, but "WMM" stands for "**W**iFi **M**ulti**M**edia" and its use is to prioritize the network traffic in its own new ways in an attempt to optimize it for multimedia experience. A detailed explanation is here : [http://kb.netgear.com/app/answers/detail/a_id/221/~/wmm-%28wifi-multimedia%29](http://kb.netgear.com/app/answers/detail/a_id/221/~/wmm-%28wifi-multimedia%29)

It is usually located under 'QoS' settings of the routers.

While a small post [here]("http://www.smallnetbuilder.com/wireless/wireless-features/30938-dont-mess-with-wmm") recommends to keep it "Enabled" to reach "N" speeds, we have many evidence threads here on the forums that suggest that it is better to keep it off to solve speed problems. Explanation of WMM is probably an explanation of the solution as well - it can '_delay_' other traffic in its attempt to optimize multimedia traffic; but some of the evidence posts here suggested that the problem (when it was "enabled") occurred even when the posters were the only users on the network, and had no multimedia traffic. So maybe the technology itself is reasonably positive, its implementations are no doubt still buggy. We network troubleshooters here already know how much the hardware vendors 'Love' patching their firmware instead of re-coding it to properly follow the standards.

Oh, and while the above linked post that recommends to keep it "enabled" suggests that it is [COLOR="#FF0000"]enabled by default[/COLOR] in routers supporting "N" speeds, my personal experience has been opposite - I have always found it "disabled" by default - even in popular router models that I have personally tested (one Asus and one D-Link with 150 Mbps support, a Netgear with 300 Mbps support). Same is confirmed again and again here on the forums - it is usually (but not always) disabled by default.

And regarding a router can be blamed or not - we can always blame it because we can.. :p

The more serious (attempt on) explanation, **almost entirely based on my own assumptions and personal opinion, and can be entirely wrong** -

Both driver and firmware are designed to tolerate *some* level of *unexpected* things in a traffic. Some are good at it, some not so much. When things at both end are following the standards, every thing is nice and peachy. But when they start going 'off-the-standards', the outcome depends on how good the device at the other end is at tolerating the *unexpected* parts. The better the toleration, the less you see the problems. But when a driver or firmware can't handle the 'unusuals' anymore, we need to adjust things at the other end so they are in a form that is *expected* by the driver/firmware at the other end.

I'm not saying that the non-standard or *unexpected* things only exist in the router/AP firmware. But given the very nature of Open Source vs Proprietary code development - that IS most often the truth. The Open Source software developers always try to fully comply the standards, while also trying to make the code as robust as possible. Workarounds, if required, are only temporary until the problem is found and properly fixed in the code. Whereas in proprietary code development (e.g. the firmware of routers/cards), the manufacturers tend to simply 'patch' a buggy/outdated code to optimize it for selected target system(s) and forget it to save development costs. And most often they do that to satisfy the needs of the target systems that have a bigger market share (Android and Windows). In the device-manufacturing world, nobody really cares about Linux due to its tiny market share. Except the cases when the manufacturers use its *patched* versions themselves as embedded OS for their devices.

So...., regardless of how accurate or inaccurate the explanation above can be, the bottomline is - "Try optimizing things when they are not performing good with the defaults".

And so.... could you find the "WMM" thing and tried toggling its state in the router? No change in performance?

---

### Post by Tomasz_Janczewski on 2015-01-26
Thank You for those fix,
I added line disabling n and wifi works grat:)

---

