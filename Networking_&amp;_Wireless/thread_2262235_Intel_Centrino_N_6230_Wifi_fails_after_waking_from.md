---
title: "Intel Centrino N 6230: Wifi fails after waking from sleep"
date: 2015-01-23
forum: Networking &amp; Wireless
---

### Post by AdamMPkins on 2015-01-23
I'm on Ubuntu 14.04 and my wifi is failing after waking from sleep. It seems to be using the iwlwifi driver and I've seen these issues in the past, but can't recall what fixes them. I am on a Dell XPS 14z. Here is the output of Wild Man and Krytarik's wifi script:

```


	======== Wireless-Info START ========

System-Info ~~~~~~~~~~~~~~~~~~~~~~~~

adam-14z-ubuntu 3.13.0-35-generic x86_64,  Ubuntu 14.04.1 LTS, trusty

CPU    : Intel(R) Core(TM) i7-2640M CPU @ 2.80GHz
Memory : 7932 MB
Uptime : 18:40:26 up 23:01,  3 users,  load average: 0.22, 0.39, 0.44


lspci ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

07:00.0 Ethernet controller [0200]: Qualcomm Atheros AR8151 v2.0 Gigabit Ethernet [1969:1083] (rev c0)
	Subsystem: Dell Device [1028:0522]
	Kernel driver in use: atl1c
08:00.0 Network controller [0280]: Intel Corporation Centrino Advanced-N 6230 [Rainbow Peak] [8086:0091] (rev 34)
	Subsystem: Intel Corporation Centrino Advanced-N 6230 AGN [8086:5221]
	Kernel driver in use: iwlwifi


lsusb ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Bus 001 Device 007: ID 8086:0189 Intel Corp. 
Bus 001 Device 003: ID 174f:143f Syntek 
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


PCMCIA Card Info ~~~~~~~~~~~~~~~~~~~



iwconfig ~~~~~~~~~~~~~~~~~~~~~~~~~~~

wlan0     IEEE 802.11abgn  ESSID:"TallTyrionLANnister"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: <MAC C-01 TallTyrionLANnister>   
          Bit Rate=1 Mb/s   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=70/70  Signal level=-38 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:148   Missed beacon:0



rfkill ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

      Interface        Soft blocked  Hard blocked
0: phy0: Wireless LAN      no            no
8: hci0: Bluetooth         no            no


lsmod ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

iwldvm                232285  0 
mac80211              630653  1 iwldvm
iwlwifi               169932  1 iwldvm
cfg80211              484040  3 iwlwifi,mac80211,iwldvm
dell_wmi               12761  0 
sparse_keymap          13948  1 dell_wmi
mxm_wmi                13021  1 nouveau
wmi                    19177  3 dell_wmi,mxm_wmi,nouveau


module parameters ~~~~~~~~~~~~~~~~~~

cfg80211      (2): cfg80211_disable_40mhz_24ghz=N | ieee80211_regdom=00
iwlwifi      (11): 11n_disable=0 | amsdu_size_8K=0 | antenna_coupling=0 | bt_coex_active=Y | fw_restart=Y | led_mode=0 | nvm_file=(null) | power_level=0 | power_save=N | swcrypto=0 | wd_disable=1
mac80211      (5): beacon_loss_count=7 | ieee80211_default_rc_algo=minstrel_ht | max_nullfunc_tries=2 | max_probe_tries=5 | probe_wait_ms=500
wmi           (2): debug_dump_wdg=N | debug_event=N


nm-tool ~~~~~~~~~~~~~~~~~~~~~~~~~~~~

State: connected (global)
==============================o=============o=========o=============o=========o===========o==============o===========
 Interface & ID               | Type        | Driver  | State       | Default | Speed     | Support      | HW Addr   
==============================o=============o=========o=============o=========o===========o==============o===========
 wlan0  [TallTyrionLANnister] | 802.11 WiFi | iwlwifi | connected   | yes     | 1 Mb/s    | WEP/WPA/WPA2 | <MAC wlan0>

    WOW!2429:        Infra, <MAC C-NA WOW!2429 1>, Freq 2422 MHz, Rate 54 Mb/s, Strength 60 WPA WPA2
    ATT7K4f8r8:      Infra, <MAC C-02 ATT7K4f8r8>, Freq 2412 MHz, Rate 54 Mb/s, Strength 45 WPA WPA2
    Bolitho Network: Infra, <MAC C-NA Bolitho Network 1>, Freq 2412 MHz, Rate 54 Mb/s, Strength 40 WPA2
    2WIRE914:        Infra, <MAC C-04 2WIRE914>, Freq 2447 MHz, Rate 54 Mb/s, Strength 27 WPA WPA2
    Cisco_D47345A4:  Infra, <MAC C-NA Cisco_D47345A4 1>, Freq 5785 MHz, Rate 54 Mb/s, Strength 19 WPA2
    xfinitywifi:     Infra, <MAC C-03 xfinitywifi>, Freq 2412 MHz, Rate 54 Mb/s, Strength 100
    *TallTyrionLANnister: Infra, <MAC C-01 TallTyrionLANnister>, Freq 2412 MHz, Rate 54 Mb/s, Strength 81 WPA WPA2
    2WIRE263:        Infra, <MAC C-NA 2WIRE263 1>, Freq 2447 MHz, Rate 54 Mb/s, Strength 20 WPA WPA2
    2WIRE593:        Infra, <MAC C-NA 2WIRE593 1>, Freq 2457 MHz, Rate 54 Mb/s, Strength 49 WPA WPA2
    xfinitywifi:     Infra, <MAC C-NA xfinitywifi 2>, Freq 2462 MHz, Rate 54 Mb/s, Strength 29
    HOME-CCA2:       Infra, <MAC C-NA HOME-CCA2 1>, Freq 2462 MHz, Rate 54 Mb/s, Strength 39 WPA WPA2

    Address:         10.0.0.6
    Prefix:          24 (255.255.255.0)
    Gateway:         10.0.0.1
    DNS:             75.75.76.76
    DNS:             75.75.75.75

    Address:         2601:4:2901:6390::1
    Prefix:          128
    Gateway:         fe80::5a23:8cff:fe2d:d84

    Address:         2601:4:2901:6390:d9ef:5745:3d30:6645
    Prefix:          64
    Gateway:         fe80::5a23:8cff:fe2d:d84

    Address:         2601:4:2901:6390:8a53:2eff:fea0:edf3
    Prefix:          64
    Gateway:         fe80::5a23:8cff:fe2d:d84

    Address:         fe80::8a53:2eff:fea0:edf3
    Prefix:          64
    Gateway:         fe80::5a23:8cff:fe2d:d84

    Address:         2601:4:2901:6390::1
    Prefix:          128
    Gateway:         ::
    DNS:             2001:558:feed::2
    DNS:             2001:558:feed::1
------------------------------+-------------+---------+-------------+---------+-----------+--------------+-----------
 eth0                         | Wired       | atl1c   | unavailable | no      |           |              | <MAC eth0>
------------------------------+-------------+---------+-------------+---------+-----------+--------------+-----------


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

Kyle                 : ssid=Kyle | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 
Perkins2Go           : ssid=Perkins2Go | mac-address=<MAC wlan0> | ipv6=auto | ipv4=auto 
TallTyrionLANnister  : ssid=TallTyrionLANnister | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 
TimeyWimeyWifi       : ssid=TimeyWimeyWifi | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 
WhyFly               : ssid=WhyFly | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 
WOW!2429             : ssid=WOW!2429 | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 


interfaces ~~~~~~~~~~~~~~~~~~~~~~~~~

# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback

resolv.conf ~~~~~~~~~~~~~~~~~~~~~~~~

nameserver 127.0.1.1


Routes & Ping ~~~~~~~~~~~~~~~~~~~~~~

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         10.0.0.1        0.0.0.0         UG    0      0        0 wlan0
10.0.0.0        0.0.0.0         255.255.255.0   U     9      0        0 wlan0

--- 10.0.0.1 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 1000ms
rtt min/avg/max/mdev = 91.033/105.053/119.073/14.020 ms

--- 127.0.1.1 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 999ms
rtt min/avg/max/mdev = 0.040/0.049/0.058/0.009 ms


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
          Channel 140 (5.7 GHz)

          Current Frequency:2.412 GHz (Channel 1)


iwlist scan ~~~~~~~~~~~~~~~~~~~~~~~~

wlan0     Scan completed :
          Cell 01 - Address: <MAC C-01 TallTyrionLANnister>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=70/70  Signal level=-38 dBm  
                    Encryption key:on
                    ESSID:"TallTyrionLANnister"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000002a6c250d2c
                    Extra: Last beacon: 0ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC C-02 ATT7K4f8r8>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=45/70  Signal level=-65 dBm  
                    Encryption key:on
                    ESSID:"ATT7K4f8r8"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000009413d912
                    Extra: Last beacon: 8164ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: <MAC C-03 xfinitywifi>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=65/70  Signal level=-45 dBm  
                    Encryption key:off
                    ESSID:"xfinitywifi"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000002a6c252684
                    Extra: Last beacon: 0ms ago
          Cell 04 - Address: <MAC C-04 2WIRE914>
                    Channel:8
                    Frequency:2.447 GHz (Channel 8)
                    Quality=32/70  Signal level=-78 dBm  
                    Encryption key:on
                    ESSID:"2WIRE914"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000003b575abcb61
                    Extra: Last beacon: 0ms ago
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

[iwldvm]
filename:       /lib/modules/3.13.0-35-generic/kernel/drivers/net/wireless/iwlwifi/dvm/iwldvm.ko
version:        in-tree:
srcversion:     CC4D1BA11C1EF73A6ABDE53
depends:        iwlwifi,mac80211,cfg80211

[mac80211]
filename:       /lib/modules/3.13.0-35-generic/kernel/net/mac80211/mac80211.ko
srcversion:     D491AB7C521706DA5F4BE7C
depends:        cfg80211
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[iwlwifi]
filename:       /lib/modules/3.13.0-35-generic/kernel/drivers/net/wireless/iwlwifi/iwlwifi.ko
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
srcversion:     C2D0F3DFCA289585C100E36
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
filename:       /lib/modules/3.13.0-35-generic/kernel/net/wireless/cfg80211.ko
srcversion:     C2478077E22138832B71659
depends:        
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

[dell_wmi]
filename:       /lib/modules/3.13.0-35-generic/kernel/drivers/platform/x86/dell-wmi.ko
srcversion:     0ED3A43A5709CF19B7DFD19
depends:        wmi,sparse-keymap

[mxm_wmi]
filename:       /lib/modules/3.13.0-35-generic/kernel/drivers/platform/x86/mxm-wmi.ko
srcversion:     62CBD37DE87DF0C4CD7FBA3
depends:        wmi

[wmi]
filename:       /lib/modules/3.13.0-35-generic/kernel/drivers/platform/x86/wmi.ko
srcversion:     CED5410F008DC70DF5F064B
depends:        
parm:           debug_event:Log WMI Events [0/1] (bool)
parm:           debug_dump_wdg:Dump available WMI interfaces [0/1] (bool)


udev rules ~~~~~~~~~~~~~~~~~~~~~~~~~

# PCI device 0x1969:0x1083 (atl1c)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC eth0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

# PCI device 0x8086:0x0091 (iwlwifi)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC wlan0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"


Custom files/entries ~~~~~~~~~~~~~~~

/etc/modules        : Default
/etc/rc.local       : Default
/etc/modprobe.d     : Not Default
/etc/pm/(cnf|pw|sl) : Not Default

[/etc/modprobe.d]
iwlwifi.conf      : remove iwlwifi \
                    (/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
                    && /sbin/modprobe -r mac80211
mlx4.conf         : softdep mlx4_core post: mlx4_en

[/etc/pm/power.d/wireless]
#!/bin/bash
/sbin/iwconfig eth1 power off


Kernel boot line ~~~~~~~~~~~~~~~~~~~

BOOT_IMAGE=/boot/vmlinuz-3.13.0-35-generic root=UUID=eb699b21-b6df-4be4-9984-622edc330a5a ro quiet splash vt.handoff=7


dmesg ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

[    0.681942] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[    0.682205] audit: initializing netlink socket (disabled)
[    2.259800] wmi: Mapper loaded
[    2.490973] iwlwifi 0000:08:00.0: can't disable ASPM; OS doesn't have ASPM control
[    2.491829] iwlwifi 0000:08:00.0: irq 51 for MSI/MSI-X
[    2.641860] iwlwifi 0000:08:00.0: loaded firmware version 18.168.6.1 op_mode iwldvm
[    2.658751] iwlwifi 0000:08:00.0: CONFIG_IWLWIFI_DEBUG disabled
[    2.658754] iwlwifi 0000:08:00.0: CONFIG_IWLWIFI_DEBUGFS enabled
[    2.658756] iwlwifi 0000:08:00.0: CONFIG_IWLWIFI_DEVICE_TRACING enabled
[    2.658758] iwlwifi 0000:08:00.0: Detected Intel(R) Centrino(R) Advanced-N 6230 AGN, REV=0xB0
[    2.658935] iwlwifi 0000:08:00.0: L1 Enabled; Disabling L0S
[    2.694092] ieee80211 phy0: Selected rate control algorithm 'iwl-agn-rs'
[    3.529843] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[    4.180777] iwlwifi 0000:08:00.0: L1 Enabled; Disabling L0S
[    4.187417] iwlwifi 0000:08:00.0: Radio type=0x1-0x2-0x0
[    4.460035] iwlwifi 0000:08:00.0: L1 Enabled; Disabling L0S
[    4.466659] iwlwifi 0000:08:00.0: Radio type=0x1-0x2-0x0
[    4.551231] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[    4.552240] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[    7.917525] wlan0: authenticate with <MAC C-01 TallTyrionLANnister>
[    7.921372] wlan0: send auth to <MAC C-01 TallTyrionLANnister> (try 1/3)
[    7.926652] wlan0: authenticated
[    7.927618] wlan0: associate with <MAC C-01 TallTyrionLANnister> (try 1/3)
[    7.931238] wlan0: RX AssocResp from <MAC C-01 TallTyrionLANnister> (capab=0x411 status=0 aid=4)
[    7.933583] wlan0: associated
[    7.933611] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  269.875811] wlan0: deauthenticating from <MAC C-01 TallTyrionLANnister> by local choice (reason=3)
[  274.951679] iwlwifi 0000:08:00.0: no hotplug settings from platform
[  276.164385] iwlwifi 0000:08:00.0: L1 Enabled; Disabling L0S
[  276.170970] iwlwifi 0000:08:00.0: Radio type=0x1-0x2-0x0
[  276.262332] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  279.520969] wlan0: authenticate with <MAC C-01 TallTyrionLANnister>
[  279.525220] wlan0: send auth to <MAC C-01 TallTyrionLANnister> (try 1/3)
[  279.534243] wlan0: authenticated
[  279.538654] wlan0: associate with <MAC C-01 TallTyrionLANnister> (try 1/3)
[  279.542900] wlan0: RX AssocResp from <MAC C-01 TallTyrionLANnister> (capab=0x411 status=0 aid=4)
[  279.548253] wlan0: associated
[  279.548316] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  919.841437] wlan0: deauthenticating from <MAC C-01 TallTyrionLANnister> by local choice (reason=3)
[  924.820106] iwlwifi 0000:08:00.0: no hotplug settings from platform
[  926.177290] iwlwifi 0000:08:00.0: L1 Enabled; Disabling L0S
[  926.183961] iwlwifi 0000:08:00.0: Radio type=0x1-0x2-0x0
[  926.273574] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  929.499673] wlan0: authenticate with <MAC C-01 TallTyrionLANnister>
[  929.502314] wlan0: send auth to <MAC C-01 TallTyrionLANnister> (try 1/3)
[  929.505065] wlan0: authenticated
[  929.506384] wlan0: associate with <MAC C-01 TallTyrionLANnister> (try 1/3)
[  929.510088] wlan0: RX AssocResp from <MAC C-01 TallTyrionLANnister> (capab=0x411 status=0 aid=4)
[  929.513085] wlan0: associated
[  929.513135] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 1018.303883] wlan0: deauthenticating from <MAC C-01 TallTyrionLANnister> by local choice (reason=3)
[ 1023.014951] iwlwifi 0000:08:00.0: no hotplug settings from platform
[ 1023.391439] iwlwifi 0000:08:00.0: L1 Enabled; Disabling L0S
[ 1023.398113] iwlwifi 0000:08:00.0: Radio type=0x1-0x2-0x0
[ 1023.481278] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1026.727153] wlan0: authenticate with <MAC C-01 TallTyrionLANnister>
[ 1026.730396] wlan0: send auth to <MAC C-01 TallTyrionLANnister> (try 1/3)
[ 1026.733215] wlan0: authenticated
[ 1026.736543] wlan0: associate with <MAC C-01 TallTyrionLANnister> (try 1/3)
[ 1026.740230] wlan0: RX AssocResp from <MAC C-01 TallTyrionLANnister> (capab=0x411 status=0 aid=4)
[ 1026.744199] wlan0: associated
[ 1026.744258] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 5269.405158] wlan0: deauthenticating from <MAC C-01 TallTyrionLANnister> by local choice (reason=3)
[ 5274.282930] iwlwifi 0000:08:00.0: no hotplug settings from platform
[ 5274.961943] iwlwifi 0000:08:00.0: L1 Enabled; Disabling L0S
[ 5274.968557] iwlwifi 0000:08:00.0: Radio type=0x1-0x2-0x0
[ 5275.053260] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 5278.319471] wlan0: authenticate with <MAC C-01 TallTyrionLANnister>
[ 5278.322560] wlan0: send auth to <MAC C-01 TallTyrionLANnister> (try 1/3)
[ 5278.325282] wlan0: authenticated
[ 5278.329373] wlan0: associate with <MAC C-01 TallTyrionLANnister> (try 1/3)
[ 5278.333034] wlan0: RX AssocResp from <MAC C-01 TallTyrionLANnister> (capab=0x411 status=0 aid=6)
[ 5278.335750] wlan0: associated
[ 5278.335775] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 5718.543734] iwlwifi 0000:08:00.0: RF_KILL bit toggled to disable radio.
[ 5718.543867] wlan0: deauthenticating from <MAC C-01 TallTyrionLANnister> by local choice (reason=3)
[ 5718.543936] iwlwifi 0000:08:00.0: Not sending command - RF KILL
[ 5718.543940] wlan0: HW problem - can not stop rx aggregation for <MAC C-01 TallTyrionLANnister> tid 0
[ 5718.543948] iwlwifi 0000:08:00.0: Not sending command - RF KILL
[ 5718.543950] wlan0: HW problem - can not stop rx aggregation for <MAC C-01 TallTyrionLANnister> tid 1
[ 5718.543954] iwlwifi 0000:08:00.0: Not sending command - RF KILL
[ 5718.543958] wlan0: HW problem - can not stop rx aggregation for <MAC C-01 TallTyrionLANnister> tid 2
[ 5718.544066] iwlwifi 0000:08:00.0: Not sending command - RF KILL
[ 5718.544070] wlan0: failed to remove key (0, <MAC C-01 TallTyrionLANnister>) from hardware (-5)
[ 5718.544182] iwlwifi 0000:08:00.0: Not sending command - RF KILL
[ 5718.544191] iwlwifi 0000:08:00.0: Not sending command - RF KILL
[ 5718.544200] iwlwifi 0000:08:00.0: Not sending command - RF KILL
[ 5718.544210] iwlwifi 0000:08:00.0: Not sending command - RF KILL
[ 5718.544224] iwlwifi 0000:08:00.0: Not sending command - RF KILL
[ 5718.544477] iwlwifi 0000:08:00.0: Not sending command - RF KILL
[ 5718.544481] wlan0: failed to remove key (1, <MAC ID removed>) from hardware (-5)
[ 5718.587704] iwlwifi 0000:08:00.0: Not sending command - RF KILL
[ 5718.587751] iwlwifi 0000:08:00.0: Not sending command - RF KILL
[ 5718.947692] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 5720.117969] iwlwifi 0000:08:00.0: RF_KILL bit toggled to enable radio.
[ 5720.123897] iwlwifi 0000:08:00.0: L1 Enabled; Disabling L0S
[ 5720.130619] iwlwifi 0000:08:00.0: Radio type=0x1-0x2-0x0
[ 5720.224754] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 5726.597847] wlan0: authenticate with <MAC C-01 TallTyrionLANnister>
[ 5726.601151] wlan0: send auth to <MAC C-01 TallTyrionLANnister> (try 1/3)
[ 5726.603188] wlan0: authenticated
[ 5726.605684] wlan0: associate with <MAC C-01 TallTyrionLANnister> (try 1/3)
[ 5726.609394] wlan0: RX AssocResp from <MAC C-01 TallTyrionLANnister> (capab=0x411 status=0 aid=6)
[ 5726.611270] wlan0: associated
[ 5726.611292] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 5726.649688] wlan0: deauthenticating from <MAC C-01 TallTyrionLANnister> by local choice (reason=2)
[ 5726.661125] wlan0: authenticate with <MAC C-01 TallTyrionLANnister>
[ 5726.663637] wlan0: send auth to <MAC C-01 TallTyrionLANnister> (try 1/3)
[ 5726.665615] wlan0: authenticated
[ 5726.669722] wlan0: associate with <MAC C-01 TallTyrionLANnister> (try 1/3)
[ 5726.673424] wlan0: RX AssocResp from <MAC C-01 TallTyrionLANnister> (capab=0x411 status=0 aid=6)
[ 5726.677061] wlan0: associated
[ 5775.317202] wlan0: deauthenticating from <MAC C-01 TallTyrionLANnister> by local choice (reason=3)
[ 5778.918826] iwlwifi 0000:08:00.0: L1 Enabled; Disabling L0S
[ 5778.925465] iwlwifi 0000:08:00.0: Radio type=0x1-0x2-0x0
[ 5779.014789] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 5785.557794] wlan0: authenticate with <MAC C-01 TallTyrionLANnister>
[ 5785.560781] wlan0: send auth to <MAC C-01 TallTyrionLANnister> (try 1/3)
[ 5785.564660] wlan0: authenticated
[ 5785.567231] wlan0: associate with <MAC C-01 TallTyrionLANnister> (try 1/3)
[ 5785.570999] wlan0: RX AssocResp from <MAC C-01 TallTyrionLANnister> (capab=0x411 status=0 aid=6)
[ 5785.574063] wlan0: associated
[ 5785.574126] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 5785.611248] wlan0: deauthenticating from <MAC C-01 TallTyrionLANnister> by local choice (reason=2)
[ 5785.623032] wlan0: authenticate with <MAC C-01 TallTyrionLANnister>
[ 5785.624858] wlan0: send auth to <MAC C-01 TallTyrionLANnister> (try 1/3)
[ 5785.626732] wlan0: authenticated
[ 5785.627338] wlan0: associate with <MAC C-01 TallTyrionLANnister> (try 1/3)
[ 5785.630975] wlan0: RX AssocResp from <MAC C-01 TallTyrionLANnister> (capab=0x411 status=0 aid=6)
[ 5785.632572] wlan0: associated
[ 5830.868077] wlan0: deauthenticating from <MAC C-01 TallTyrionLANnister> by local choice (reason=3)
[ 5834.135832] wlan0: authenticate with <MAC C-01 TallTyrionLANnister>
[ 5834.143671] wlan0: send auth to <MAC C-01 TallTyrionLANnister> (try 1/3)
[ 5834.153203] wlan0: authenticated
[ 5834.155793] wlan0: associate with <MAC C-01 TallTyrionLANnister> (try 1/3)
[ 5834.170131] wlan0: RX AssocResp from <MAC C-01 TallTyrionLANnister> (capab=0x411 status=0 aid=6)
[ 5834.179630] wlan0: associated
[ 5954.725970] iwlwifi 0000:08:00.0: RF_KILL bit toggled to disable radio.
[ 5954.726102] wlan0: deauthenticating from <MAC C-01 TallTyrionLANnister> by local choice (reason=3)
[ 5954.726179] iwlwifi 0000:08:00.0: Not sending command - RF KILL
[ 5954.726190] wlan0: HW problem - can not stop rx aggregation for <MAC C-01 TallTyrionLANnister> tid 0
[ 5954.726466] iwlwifi 0000:08:00.0: Not sending command - RF KILL
[ 5954.726476] wlan0: HW problem - can not stop rx aggregation for <MAC C-01 TallTyrionLANnister> tid 1
[ 5954.726520] iwlwifi 0000:08:00.0: Not sending command - RF KILL
[ 5954.726528] wlan0: failed to remove key (0, <MAC C-01 TallTyrionLANnister>) from hardware (-5)
[ 5954.726741] iwlwifi 0000:08:00.0: Not sending command - RF KILL
[ 5954.726752] iwlwifi 0000:08:00.0: Not sending command - RF KILL
[ 5954.726763] iwlwifi 0000:08:00.0: Not sending command - RF KILL
[ 5954.726775] iwlwifi 0000:08:00.0: Not sending command - RF KILL
[ 5954.726793] iwlwifi 0000:08:00.0: Not sending command - RF KILL
[ 5954.727302] iwlwifi 0000:08:00.0: Not sending command - RF KILL
[ 5954.727313] wlan0: failed to remove key (1, <MAC ID removed>) from hardware (-5)
[ 5954.757542] iwlwifi 0000:08:00.0: Not sending command - RF KILL
[ 5954.757608] iwlwifi 0000:08:00.0: Not sending command - RF KILL
[ 5954.932127] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 5955.487100] iwlwifi 0000:08:00.0: RF_KILL bit toggled to enable radio.
[ 5955.492709] iwlwifi 0000:08:00.0: L1 Enabled; Disabling L0S
[ 5955.499395] iwlwifi 0000:08:00.0: Radio type=0x1-0x2-0x0
[ 5955.589367] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 5958.918752] wlan0: authenticate with <MAC C-01 TallTyrionLANnister>
[ 5958.925285] wlan0: send auth to <MAC C-01 TallTyrionLANnister> (try 1/3)
[ 5958.927251] wlan0: authenticated
[ 5958.928717] wlan0: associate with <MAC C-01 TallTyrionLANnister> (try 1/3)
[ 5958.932349] wlan0: RX AssocResp from <MAC C-01 TallTyrionLANnister> (capab=0x411 status=0 aid=6)
[ 5958.934214] wlan0: associated
[ 5958.934239] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 6013.632274] iwlwifi 0000:08:00.0: RF_KILL bit toggled to disable radio.
[ 6013.632404] wlan0: deauthenticating from <MAC C-01 TallTyrionLANnister> by local choice (reason=3)
[ 6013.632483] iwlwifi 0000:08:00.0: Not sending command - RF KILL
[ 6013.632492] wlan0: HW problem - can not stop rx aggregation for <MAC C-01 TallTyrionLANnister> tid 0
[ 6013.632566] iwlwifi 0000:08:00.0: Not sending command - RF KILL
[ 6013.632574] wlan0: HW problem - can not stop rx aggregation for <MAC C-01 TallTyrionLANnister> tid 1
[ 6013.632627] iwlwifi 0000:08:00.0: Not sending command - RF KILL
[ 6013.632635] wlan0: failed to remove key (0, <MAC C-01 TallTyrionLANnister>) from hardware (-5)
[ 6013.632864] iwlwifi 0000:08:00.0: Not sending command - RF KILL
[ 6013.632879] iwlwifi 0000:08:00.0: Not sending command - RF KILL
[ 6013.632895] iwlwifi 0000:08:00.0: Not sending command - RF KILL
[ 6013.632912] iwlwifi 0000:08:00.0: Not sending command - RF KILL
[ 6013.632936] iwlwifi 0000:08:00.0: Not sending command - RF KILL
[ 6013.633458] iwlwifi 0000:08:00.0: Not sending command - RF KILL
[ 6013.633467] wlan0: failed to remove key (1, <MAC ID removed>) from hardware (-5)
[ 6013.668015] iwlwifi 0000:08:00.0: Not sending command - RF KILL
[ 6013.668062] iwlwifi 0000:08:00.0: Not sending command - RF KILL
[ 6013.836889] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 6026.186278] iwlwifi 0000:08:00.0: RF_KILL bit toggled to enable radio.
[ 6026.193839] iwlwifi 0000:08:00.0: L1 Enabled; Disabling L0S
[ 6026.200549] iwlwifi 0000:08:00.0: Radio type=0x1-0x2-0x0
[ 6026.296897] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 6029.597540] wlan0: authenticate with <MAC C-01 TallTyrionLANnister>
[ 6029.600227] wlan0: send auth to <MAC C-01 TallTyrionLANnister> (try 1/3)
[ 6029.602263] wlan0: authenticated
[ 6029.603613] wlan0: associate with <MAC C-01 TallTyrionLANnister> (try 1/3)
[ 6029.607234] wlan0: RX AssocResp from <MAC C-01 TallTyrionLANnister> (capab=0x411 status=0 aid=6)
[ 6029.611904] wlan0: associated
[ 6029.611926] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 6163.349901] iwlwifi 0000:08:00.0: Microcode SW error detected.  Restarting 0x2000000.
[ 6163.349913] iwlwifi 0000:08:00.0: CSR values:
[ 6163.349919] iwlwifi 0000:08:00.0: (2nd byte of CSR_INT_COALESCING is CSR_INT_PERIODIC_REG)
[ 6163.349951] iwlwifi 0000:08:00.0:        CSR_HW_IF_CONFIG_REG: 0X00488700
[ 6163.349983] iwlwifi 0000:08:00.0:          CSR_INT_COALESCING: 0X00000040
[ 6163.350012] iwlwifi 0000:08:00.0:                     CSR_INT: 0X00000000
[ 6163.350043] iwlwifi 0000:08:00.0:                CSR_INT_MASK: 0X00000000
[ 6163.350071] iwlwifi 0000:08:00.0:           CSR_FH_INT_STATUS: 0X00000000
[ 6163.350099] iwlwifi 0000:08:00.0:                 CSR_GPIO_IN: 0X0000003c
[ 6163.350127] iwlwifi 0000:08:00.0:                   CSR_RESET: 0X00000000
[ 6163.350155] iwlwifi 0000:08:00.0:                CSR_GP_CNTRL: 0X080403c5
[ 6163.350183] iwlwifi 0000:08:00.0:                  CSR_HW_REV: 0X000000b0
[ 6163.350211] iwlwifi 0000:08:00.0:              CSR_EEPROM_REG: 0X40120ffd
[ 6163.350239] iwlwifi 0000:08:00.0:               CSR_EEPROM_GP: 0X90000801
[ 6163.350268] iwlwifi 0000:08:00.0:              CSR_OTP_GP_REG: 0X00030001
[ 6163.350297] iwlwifi 0000:08:00.0:                 CSR_GIO_REG: 0X00080042
[ 6163.350328] iwlwifi 0000:08:00.0:            CSR_GP_UCODE_REG: 0X00006952
[ 6163.350356] iwlwifi 0000:08:00.0:           CSR_GP_DRIVER_REG: 0X00000000
[ 6163.350384] iwlwifi 0000:08:00.0:           CSR_UCODE_DRV_GP1: 0X00000000
[ 6163.350414] iwlwifi 0000:08:00.0:           CSR_UCODE_DRV_GP2: 0X00000000
[ 6163.350445] iwlwifi 0000:08:00.0:                 CSR_LED_REG: 0X00000060
[ 6163.350473] iwlwifi 0000:08:00.0:        CSR_DRAM_INT_TBL_REG: 0X88251b0c
[ 6163.350501] iwlwifi 0000:08:00.0:        CSR_GIO_CHICKEN_BITS: 0X27800200
[ 6163.350529] iwlwifi 0000:08:00.0:             CSR_ANA_PLL_CFG: 0X00000000
[ 6163.350558] iwlwifi 0000:08:00.0:           CSR_HW_REV_WA_REG: 0X0001001a
[ 6163.350590] iwlwifi 0000:08:00.0:        CSR_DBG_HPET_MEM_REG: 0Xffff0000
[ 6163.350595] iwlwifi 0000:08:00.0: FH register values:
[ 6163.350634] iwlwifi 0000:08:00.0:         FH_RSCSR_CHNL0_STTS_WPTR_REG: 0X250da000
[ 6163.350671] iwlwifi 0000:08:00.0:        FH_RSCSR_CHNL0_RBDCB_BASE_REG: 0X0250da10
[ 6163.350749] iwlwifi 0000:08:00.0:                  FH_RSCSR_CHNL0_WPTR: 0X00000098
[ 6163.350805] iwlwifi 0000:08:00.0:         FH_MEM_RCSR_CHNL0_CONFIG_REG: 0X00801114
[ 6163.350859] iwlwifi 0000:08:00.0:          FH_MEM_RSSR_SHARED_CTRL_REG: 0X000000fc
[ 6163.350911] iwlwifi 0000:08:00.0:            FH_MEM_RSSR_RX_STATUS_REG: 0X07030000
[ 6163.350951] iwlwifi 0000:08:00.0:    FH_MEM_RSSR_RX_ENABLE_ERR_IRQ2DRV: 0X00000000
[ 6163.350995] iwlwifi 0000:08:00.0:                FH_TSSR_TX_STATUS_REG: 0X07ff0001
[ 6163.351040] iwlwifi 0000:08:00.0:                 FH_TSSR_TX_ERROR_REG: 0X00000000
[ 6163.351051] iwlwifi 0000:08:00.0: Loaded firmware version: 18.168.6.1
[ 6163.351210] iwlwifi 0000:08:00.0: Start IWL Error Log Dump:
[ 6163.351217] iwlwifi 0000:08:00.0: Status: 0x0000004C, count: 6
[ 6163.351223] iwlwifi 0000:08:00.0: 0x00000034 | NMI_INTERRUPT_WDG           
[ 6163.351227] iwlwifi 0000:08:00.0: 0x00010564 | uPc
[ 6163.351232] iwlwifi 0000:08:00.0: 0x0001054E | branchlink1
[ 6163.351237] iwlwifi 0000:08:00.0: 0x00010580 | branchlink2
[ 6163.351241] iwlwifi 0000:08:00.0: 0x0000DBEA | interruptlink1
[ 6163.351246] iwlwifi 0000:08:00.0: 0x0000CE22 | interruptlink2
[ 6163.351250] iwlwifi 0000:08:00.0: 0x00000002 | data1
[ 6163.351254] iwlwifi 0000:08:00.0: 0x07030000 | data2
[ 6163.351259] iwlwifi 0000:08:00.0: 0x000260A4 | line
[ 6163.351263] iwlwifi 0000:08:00.0: 0x4600205D | beacon time
[ 6163.351268] iwlwifi 0000:08:00.0: 0x69CCBFA3 | tsf low
[ 6163.351272] iwlwifi 0000:08:00.0: 0x0000002A | tsf hi
[ 6163.351276] iwlwifi 0000:08:00.0: 0x00000000 | time gp1
[ 6163.351281] iwlwifi 0000:08:00.0: 0x0828B9BD | time gp2
[ 6163.351285] iwlwifi 0000:08:00.0: 0x00000000 | time gp3
[ 6163.351289] iwlwifi 0000:08:00.0: 0x754312A8 | uCode version
[ 6163.351294] iwlwifi 0000:08:00.0: 0x000000B0 | hw version
[ 6163.351298] iwlwifi 0000:08:00.0: 0x00488700 | board version
[ 6163.351302] iwlwifi 0000:08:00.0: 0x0000001C | hcmd
[ 6163.351307] iwlwifi 0000:08:00.0: 0x2F963048 | isr0
[ 6163.351311] iwlwifi 0000:08:00.0: 0x11887800 | isr1
[ 6163.351316] iwlwifi 0000:08:00.0: 0x00000E1F | isr2
[ 6163.351320] iwlwifi 0000:08:00.0: 0x8547FCC3 | isr3
[ 6163.351325] iwlwifi 0000:08:00.0: 0x00000000 | isr4
[ 6163.351329] iwlwifi 0000:08:00.0: 0x00890110 | isr_pref
[ 6163.351334] iwlwifi 0000:08:00.0: 0x000260A4 | wait_event
[ 6163.351338] iwlwifi 0000:08:00.0: 0x000000D4 | l2p_control
[ 6163.351343] iwlwifi 0000:08:00.0: 0x00000000 | l2p_duration
[ 6163.351347] iwlwifi 0000:08:00.0: 0x00000007 | l2p_mhvalid
[ 6163.351352] iwlwifi 0000:08:00.0: 0x00101042 | l2p_addr_match
[ 6163.351356] iwlwifi 0000:08:00.0: 0x00000005 | lmpm_pmg_sel
[ 6163.351361] iwlwifi 0000:08:00.0: 0x13011136 | timestamp
[ 6163.351365] iwlwifi 0000:08:00.0: 0x000098A8 | flow_handler
[ 6163.351446] iwlwifi 0000:08:00.0: Start IWL Event Log Dump: display last 1 entries
[ 6163.351490] iwlwifi 0000:08:00.0: EVT_LOGT:0136886713:0x0000010c:0123
[ 6165.152940] iwlwifi 0000:08:00.0: fail to flush all tx fifo queues Q 0
[ 6165.152946] iwlwifi 0000:08:00.0: Current SW read_ptr 52 write_ptr 53
[ 6165.152995] iwl data: 00000000: 00 00 00 00 00 00 00 00 00 00 10 00 00 00 00 00  ................
[ 6165.153030] iwlwifi 0000:08:00.0: FH TRBs(0) = 0x80003016
[ 6165.153050] iwlwifi 0000:08:00.0: FH TRBs(1) = 0x80102060
[ 6165.153064] iwlwifi 0000:08:00.0: FH TRBs(2) = 0x00000000
[ 6165.153078] iwlwifi 0000:08:00.0: FH TRBs(3) = 0x80300034
[ 6165.153091] iwlwifi 0000:08:00.0: FH TRBs(4) = 0x00000000
[ 6165.153105] iwlwifi 0000:08:00.0: FH TRBs(5) = 0x00000000
[ 6165.153125] iwlwifi 0000:08:00.0: FH TRBs(6) = 0x00000000
[ 6165.153139] iwlwifi 0000:08:00.0: FH TRBs(7) = 0x0070908a
[ 6165.153195] iwlwifi 0000:08:00.0: Q 0 is active and mapped to fifo 3 ra_tid 0x0000 [52,53]
[ 6165.153256] iwlwifi 0000:08:00.0: Q 1 is active and mapped to fifo 2 ra_tid 0x0000 [0,0]
[ 6165.153317] iwlwifi 0000:08:00.0: Q 2 is active and mapped to fifo 1 ra_tid 0x0000 [97,97]
[ 6165.153379] iwlwifi 0000:08:00.0: Q 3 is active and mapped to fifo 0 ra_tid 0x0000 [23,23]
[ 6165.153441] iwlwifi 0000:08:00.0: Q 4 is active and mapped to fifo 0 ra_tid 0x0000 [0,0]
[ 6165.153502] iwlwifi 0000:08:00.0: Q 5 is active and mapped to fifo 4 ra_tid 0x0000 [0,0]
[ 6165.153563] iwlwifi 0000:08:00.0: Q 6 is active and mapped to fifo 2 ra_tid 0x0000 [0,0]
[ 6165.153625] iwlwifi 0000:08:00.0: Q 7 is active and mapped to fifo 5 ra_tid 0x0000 [0,0]
[ 6165.153687] iwlwifi 0000:08:00.0: Q 8 is active and mapped to fifo 4 ra_tid 0x0000 [0,0]
[ 6165.153749] iwlwifi 0000:08:00.0: Q 9 is active and mapped to fifo 7 ra_tid 0x0000 [139,139]
[ 6165.153810] iwlwifi 0000:08:00.0: Q 10 is active and mapped to fifo 5 ra_tid 0x0000 [0,0]
[ 6165.153871] iwlwifi 0000:08:00.0: Q 11 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[ 6165.153933] iwlwifi 0000:08:00.0: Q 12 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[ 6165.153995] iwlwifi 0000:08:00.0: Q 13 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[ 6165.154056] iwlwifi 0000:08:00.0: Q 14 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[ 6165.154117] iwlwifi 0000:08:00.0: Q 15 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[ 6165.154179] iwlwifi 0000:08:00.0: Q 16 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[ 6165.154241] iwlwifi 0000:08:00.0: Q 17 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[ 6165.154301] iwlwifi 0000:08:00.0: Q 18 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[ 6165.154363] iwlwifi 0000:08:00.0: Q 19 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[ 6165.154809] iwlwifi 0000:08:00.0: Fw not loaded - dropping CMD: 18
[ 6165.154813] wlan0: HW problem - can not stop rx aggregation for <MAC C-01 TallTyrionLANnister> tid 1
[ 6165.154818] iwlwifi 0000:08:00.0: Fw not loaded - dropping CMD: 18
[ 6165.154820] wlan0: HW problem - can not stop rx aggregation for <MAC C-01 TallTyrionLANnister> tid 0
[ 6165.154837] iwlwifi 0000:08:00.0: Fw not loaded - dropping CMD: 18
[ 6165.154854] iwlwifi 0000:08:00.0: Fw not loaded - dropping CMD: 18
[ 6165.154864] iwlwifi 0000:08:00.0: Fw not loaded - dropping CMD: 18
[ 6165.154872] iwlwifi 0000:08:00.0: Fw not loaded - dropping CMD: 18
[ 6165.154886] iwlwifi 0000:08:00.0: Fw not loaded - dropping CMD: 18
[ 6165.154896] iwlwifi 0000:08:00.0: Fw not loaded - dropping CMD: 18
[ 6165.154914] iwlwifi 0000:08:00.0: Fw not loaded - dropping CMD: 18
[ 6165.154935] iwlwifi 0000:08:00.0: Fw not loaded - dropping CMD: 18
[ 6165.155175] iwlwifi 0000:08:00.0: L1 Enabled; Disabling L0S
[ 6165.161829] iwlwifi 0000:08:00.0: Radio type=0x1-0x2-0x0

	======== Done ========


```

---

### Post by AdamMPkins on 2015-01-24
Any ideas what might cause this?

---

### Post by chili555 on 2015-01-24
Have you tried this method? [http://askubuntu.com/questions/317478/wifi-doesnt-work-after-suspend/317545#317545](http://askubuntu.com/questions/317478/wifi-doesnt-work-after-suspend/317545#317545)

---

