---
title: "intel 7260 packet loss on some networks, not others"
date: 2015-02-16
forum: Networking &amp; Wireless
---

### Post by miatawnt2b on 2015-02-16
I have an Intel 7260 wireless card and am having some issues. On some networks, I am getting up tp 50% packet loss. I have disabled 11n with the following iwlwifi.conf
```

uname -a
Linux Ghost 3.16.0-30-generic #40-Ubuntu SMP Mon Jan 12 22:06:37 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux

```
```

# /etc/modprobe.d/iwlwifi.conf
# iwlwifi will dyamically load either iwldvm or iwlmvm depending on the
# microcode file installed on the system.  When removing iwlwifi, first
# remove the iwl?vm module and then iwlwifi.
remove iwlwifi \
(/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
&& /sbin/modprobe -r mac80211
options iwlwifi 11n_disable=1

```

I have added a file wireless to /etc/pm/power.d with 755 permissions

```

#!/bin/sh 
/sbin/iwconfig wlan0 power off

```

I have also tried to install the latest firmware 25.228.9.0 by replacing the iwlwifi-7260-9.ucode file and setting 644 permissions (not sure if there is anything else I need to do other than replace the file)

No luck. Some networks work great, others are terrible.  Any other ideas?

---

### Post by miatawnt2b on 2015-02-18
wireless script output...

```

	======== Wireless-Info START ========

System-Info ~~~~~~~~~~~~~~~~~~~~~~~~

Ghost 3.16.0-30-generic x86_64,  Ubuntu 14.10, utopic

CPU    : Intel(R) Core(TM) i7-4710HQ CPU @ 2.50GHz
Memory : 11935 MB
Uptime : 11:53:56 up 17 min,  2 users,  load average: 0.13, 0.24, 0.22


lspci ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

04:00.0 Ethernet controller [0200]: Qualcomm Atheros Killer E220x Gigabit Ethernet Controller [1969:e091] (rev 13)
	Subsystem: Micro-Star International Co., Ltd. [MSI] Device [1462:10fd]
	Kernel driver in use: alx
05:00.0 Network controller [0280]: Intel Corporation Wireless 7260 [8086:08b1] (rev 6b)
	Subsystem: Intel Corporation Dual Band Wireless-AC 7260 [8086:c070]
	Kernel driver in use: iwlwifi


lsusb ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Bus 002 Device 003: ID 1770:ff00  
Bus 002 Device 002: ID 8087:8000 Intel Corp. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 8087:07dc Intel Corp. 
Bus 001 Device 002: ID 8087:8008 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 002: ID 04b4:0060 Cypress Semiconductor Corp. 
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


PCMCIA Card Info ~~~~~~~~~~~~~~~~~~~



iwconfig ~~~~~~~~~~~~~~~~~~~~~~~~~~~

wlan0     IEEE 802.11abgn  ESSID:"PANERA"  
          Mode:Managed  Frequency:5.18 GHz  Access Point: <MAC C-01 PANERA>   
          Bit Rate=135 Mb/s   Tx-Power=22 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=48/70  Signal level=-62 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:1   Missed beacon:0



rfkill ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

      Interface        Soft blocked  Hard blocked
0: hci0: Bluetooth         no            no
1: phy0: Wireless LAN      no            no


lsmod ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

msi_wmi                13354  0 
mxm_wmi                13021  0 
sparse_keymap          13948  1 msi_wmi
iwlmvm                217797  0 
mac80211              660592  1 iwlmvm
iwlwifi               183038  1 iwlmvm
cfg80211              510218  3 iwlwifi,mac80211,iwlmvm
wmi                    19193  2 msi_wmi,mxm_wmi


module parameters ~~~~~~~~~~~~~~~~~~

cfg80211      (2): cfg80211_disable_40mhz_24ghz=N | ieee80211_regdom=00
iwlmvm        (2): init_dbg=N | power_scheme=2
iwlwifi      (13): 11n_disable=8 | amsdu_size_8K=0 | antenna_coupling=0 | bt_coex_active=Y | fw_monitor=N | fw_restart=Y | led_mode=0 | nvm_file=(null) | power_level=0 | power_save=N | swcrypto=0 | uapsd_disable=N | wd_disable=1
mac80211      (5): beacon_loss_count=7 | ieee80211_default_rc_algo=minstrel_ht | max_nullfunc_tries=2 | max_probe_tries=5 | probe_wait_ms=500
wmi           (2): debug_dump_wdg=N | debug_event=N


nm-tool ~~~~~~~~~~~~~~~~~~~~~~~~~~~~

State: connected (global)
=================o=============o=========o=============o=========o===========o==============o===========
 Interface & ID  | Type        | Driver  | State       | Default | Speed     | Support      | HW Addr   
=================o=============o=========o=============o=========o===========o==============o===========
 wlan0  [PANERA] | 802.11 WiFi | iwlwifi | connected   | yes     | 108 Mb/s  | WEP/WPA/WPA2 | <MAC wlan0>

    audit:           Infra, <MAC C-03 audit>, Freq 5180 MHz, Rate 54 Mb/s, Strength 69 WPA WPA2
    franchise:       Infra, <MAC C-04 franchise>, Freq 5180 MHz, Rate 54 Mb/s, Strength 65 WPA2
    *PANERA:         Infra, <MAC C-01 PANERA>, Freq 5180 MHz, Rate 54 Mb/s, Strength 60
    franchise:       Infra, <MAC C-NA franchise 1>, Freq 2462 MHz, Rate 54 Mb/s, Strength 72 WPA2
    CenturyLink5240: Infra, <MAC C-02 CenturyLink5240>, Freq 2412 MHz, Rate 54 Mb/s, Strength 35 WPA WPA2

    Address:         10.1.0.63
    Prefix:          24 (255.255.255.0)
    Gateway:         10.1.0.1
    DNS:             205.139.50.143
    DNS:             199.106.140.143
-----------------+-------------+---------+-------------+---------+-----------+--------------+-----------
 eth0            | Wired       | alx     | unavailable | no      |           |              | <MAC eth0>
-----------------+-------------+---------+-------------+---------+-----------+--------------+-----------


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

no-auto-default=<MAC eth0>,

[ifupdown]
managed=false


NM WiFi Profiles ~~~~~~~~~~~~~~~~~~~

AirConsole-98        : ssid=AirConsole-98 | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 
CasaTest             : ssid=CasaTest | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 
CasaWiFi             : ssid=CasaWiFi | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 
FedoNet              : ssid=FedoNet | mac-address=<MAC wlan0> | ipv6=auto | ipv4=auto 
Hillside Spot        : ssid=Hillside Spot | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 
icgguest             : ssid=icgguest | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 
IO                   : ssid=IO | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 
Keebaugh             : ssid=Keebaugh | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 
Library-Public       : ssid=Library-Public | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 
Linksys05174         : ssid=Linksys05174 | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 
MPS                  : ssid=MPS | mac-address=<MAC wlan0> | ipv4=auto 
MVFD-Public          : ssid=MVFD-Public | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 
MVFD-Public 1        : ssid=MVFD-Public | mac-address=<MAC wlan0> | ipv6=auto | ipv4=auto 
MVFD-WiFi            : ssid=MVFD-WiFi | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 
OFF-THE-WAGON        : ssid=OFF-THE-WAGON | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 
PANERA               : ssid=PANERA | mac-address=<MAC wlan0> | ipv6=auto | ipv4=auto 
PepBoysGuest         : ssid=PepBoysGuest | mac-address=<MAC wlan0> | ipv6=auto | ipv4=auto 
rcstu                : ssid=rcstu | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 
SNAP                 : ssid=SNAP | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 
Sun City Oro Valley  : ssid=Sun City Oro Valley | mac-address=<MAC wlan0> | ipv6=auto | ipv4=auto 
TAA-WiFi-HotSpot     : ssid=TAA-WiFi-HotSpot | mac-address=<MAC wlan0> | ipv6=auto | ipv4=auto 
Troegs_Public        : ssid=Troegs_Public | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 
Wingate              : ssid=Wingate | mac-address=<MAC wlan0> | ipv6=auto | ipv4=auto 


interfaces ~~~~~~~~~~~~~~~~~~~~~~~~~

# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback

resolv.conf ~~~~~~~~~~~~~~~~~~~~~~~~

nameserver 127.0.1.1
search WiFi.IPv4InfoBelow


Routes & Ping ~~~~~~~~~~~~~~~~~~~~~~

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         10.1.0.1        0.0.0.0         UG    0      0        0 wlan0
10.1.0.0        0.0.0.0         255.255.255.0   U     9      0        0 wlan0

--- 10.1.0.1 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 1001ms
rtt min/avg/max/mdev = 1.122/1.313/1.505/0.194 ms

--- 127.0.1.1 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 999ms
rtt min/avg/max/mdev = 0.012/0.014/0.016/0.002 ms


iw reg get ~~~~~~~~~~~~~~~~~~~~~~~~~

(Region : "en_US.UTF-8")
country 00: DFS-UNSET
	(2402 - 2472 @ 40), (3, 20)
	(2457 - 2482 @ 40), (3, 20), NO-IR
	(2474 - 2494 @ 20), (3, 20), NO-OFDM, NO-IR
	(5170 - 5250 @ 40), (3, 20), NO-IR
	(5735 - 5835 @ 40), (3, 20), NO-IR


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

          Current Frequency:5.18 GHz (Channel 36)


iwlist scan ~~~~~~~~~~~~~~~~~~~~~~~~

wlan0     Scan completed :
          Cell 01 - Address: <MAC C-01 PANERA>
                    Channel:36
                    Frequency:5.18 GHz (Channel 36)
                    Quality=48/70  Signal level=-62 dBm  
                    Encryption key:off
                    ESSID:"PANERA"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000001ea9306dd37
                    Extra: Last beacon: 92ms ago
          Cell 02 - Address: <MAC C-02 CenturyLink5240>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=32/70  Signal level=-78 dBm  
                    Encryption key:on
                    ESSID:"CenturyLink5240"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000de31ac9b7f
                    Extra: Last beacon: 18120ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: <MAC C-03 audit>
                    Channel:36
                    Frequency:5.18 GHz (Channel 36)
                    Quality=48/70  Signal level=-62 dBm  
                    Encryption key:on
                    ESSID:"audit"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000001ea9306de61
                    Extra: Last beacon: 92ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 04 - Address: <MAC C-04 franchise>
                    Channel:36
                    Frequency:5.18 GHz (Channel 36)
                    Quality=48/70  Signal level=-62 dBm  
                    Encryption key:on
                    ESSID:"franchise"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000001ea9306dfc8
                    Extra: Last beacon: 92ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK


blacklist ~~~~~~~~~~~~~~~~~~~~~~~~~~

[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci


modinfo ~~~~~~~~~~~~~~~~~~~~~~~~~~~~

[msi_wmi]
filename:       /lib/modules/3.16.0-30-generic/kernel/drivers/platform/x86/msi-wmi.ko
srcversion:     DDF9307A2E9F8A49A15BC8E
depends:        wmi,sparse-keymap

[mxm_wmi]
filename:       /lib/modules/3.16.0-30-generic/kernel/drivers/platform/x86/mxm-wmi.ko
srcversion:     D566C16ECB7E11FB9DF5C84
depends:        wmi

[iwlmvm]
filename:       /lib/modules/3.16.0-30-generic/kernel/drivers/net/wireless/iwlwifi/mvm/iwlmvm.ko
version:        in-tree:
srcversion:     DF2B4108DD59AC2EC4C7D5B
depends:        iwlwifi,mac80211,cfg80211
parm:           init_dbg:set to true to debug an ASSERT in INIT fw (default: false (bool)
parm:           power_scheme:power management scheme: 1-active, 2-balanced, 3-low power, default: 2 (int)

[mac80211]
filename:       /lib/modules/3.16.0-30-generic/kernel/net/mac80211/mac80211.ko
srcversion:     D421794D4F30DF3A540FD24
depends:        cfg80211
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[iwlwifi]
filename:       /lib/modules/3.16.0-30-generic/kernel/drivers/net/wireless/iwlwifi/iwlwifi.ko
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
firmware:       iwlwifi-7265-9.ucode
firmware:       iwlwifi-3160-9.ucode
firmware:       iwlwifi-7260-9.ucode
firmware:       iwlwifi-8000-8.ucode
srcversion:     D335B9FC08B25C4ADA0BD33
depends:        cfg80211
parm:           swcrypto:using crypto in software (default 0 [hardware]) (int)
parm:           11n_disable:disable 11n functionality, bitmap: 1: full, 2: disable agg TX, 4: disable agg RX, 8 enable agg TX (uint)
parm:           amsdu_size_8K:enable 8K amsdu size (default 0) (int)
parm:           fw_restart:restart firmware in case of error (default true) (bool)
parm:           antenna_coupling:specify antenna coupling in dB (defualt: 0 dB) (int)
parm:           wd_disable:Disable stuck queue watchdog timer 0=system default, 1=disable (default: 1) (int)
parm:           nvm_file:NVM file name (charp)
parm:           uapsd_disable:disable U-APSD functionality (default: N) (bool)
parm:           bt_coex_active:enable wifi/bt co-exist (default: enable) (bool)
parm:           led_mode:0=system default, 1=On(RF On)/Off(RF Off), 2=blinking, 3=Off (default: 0) (int)
parm:           power_save:enable WiFi power management (default: disable) (bool)
parm:           power_level:default power save level (range from 1 - 5, default: 1) (int)
parm:           fw_monitor:firmware monitor - to debug FW (default: false - needs lots of memory) (bool)

[cfg80211]
filename:       /lib/modules/3.16.0-30-generic/kernel/net/wireless/cfg80211.ko
srcversion:     DEE8EAA48495E392CD51C2D
depends:        
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

[wmi]
filename:       /lib/modules/3.16.0-30-generic/kernel/drivers/platform/x86/wmi.ko
srcversion:     347CF30B94B5549A75865A8
depends:        
parm:           debug_event:Log WMI Events [0/1] (bool)
parm:           debug_dump_wdg:Dump available WMI interfaces [0/1] (bool)


udev rules ~~~~~~~~~~~~~~~~~~~~~~~~~

# PCI device 0x1969:0xe091 (alx)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC eth0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

# PCI device 0x8086:0x08b1 (iwlwifi)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC wlan0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"


Custom files/entries ~~~~~~~~~~~~~~~

/etc/modules        : Default
/etc/rc.local       : Default
/etc/modprobe.d     : Not Default
/etc/pm/(cnf|pw|sl) : Not Default

[/etc/modprobe.d]
iwlwifi.conf      : options iwlwifi 11n_disable=8
                    remove iwlwifi \
                    (/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
                    && /sbin/modprobe -r mac80211
                    options iwlwifi 11n_disable=8
iwlwifi.conf~     : remove iwlwifi \
                    (/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
                    && /sbin/modprobe -r mac80211
                    options iwlwifi 11n_disable=1
mlx4.conf         : softdep mlx4_core post: mlx4_en
modesetting.conf  : options cirrus modeset=1
                    options mgag200 modeset=1

[/etc/pm/config.d/block-powermanagement] [executable]
HOOK_BLACKLIST="$HOOK_BLACKLIST wireless"

[/etc/pm/power.d/wireless] [executable]
#!/bin/sh 
/sbin/iwconfig wlan0 power off


Kernel boot line ~~~~~~~~~~~~~~~~~~~

BOOT_IMAGE=/vmlinuz-3.16.0-30-generic.efi.signed root=UUID=de16e92f-6304-4ba1-b972-5dd96eb7d214 ro quiet splash vt.handoff=7


dmesg ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

[    0.014989] Initializing cgroup subsys net_cls
[    0.014995] Initializing cgroup subsys net_prio
[    0.508007] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[    0.508283] audit: initializing netlink subsys (disabled)
[    0.761098] alx 0000:04:00.0 eth0: Qualcomm Atheros AR816x/AR817x Ethernet [<MAC eth0>]
[    1.381197] psmouse serio1: elantech: assuming hardware version 4 (with firmware version 0x461f00)
[    1.770796] wmi: Mapper loaded
[    1.949148] iwlwifi 0000:05:00.0: enabling device (0000 -> 0002)
[    1.949319] iwlwifi 0000:05:00.0: irq 47 for MSI/MSI-X
[    1.958240] iwlwifi 0000:05:00.0: loaded firmware version 25.228.9.0 op_mode iwlmvm
[    1.981947] iwlwifi 0000:05:00.0: Detected Intel(R) Dual Band Wireless AC 7260, REV=0x144
[    1.982005] iwlwifi 0000:05:00.0: L1 Disabled - LTR Enabled
[    1.982225] iwlwifi 0000:05:00.0: L1 Disabled - LTR Enabled
[    2.089706] Bluetooth: hci0: Intel Bluetooth firmware file: intel/ibt-hw-37.7.10-fw-1.80.2.3.d.bseq
[    2.164514] ieee80211 phy0: Selected rate control algorithm 'iwl-mvm-rs'
[    2.293759] Bluetooth: hci0: Intel Bluetooth firmware patch completed and activated
[    2.673635] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[    3.161080] iwlwifi 0000:05:00.0: L1 Disabled - LTR Enabled
[    3.161323] iwlwifi 0000:05:00.0: L1 Disabled - LTR Enabled
[    3.172539] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[    6.769310] wlan0: authenticate with <MAC C-01 PANERA>
[    6.772141] wlan0: send auth to <MAC C-01 PANERA> (try 1/3)
[    6.773103] wlan0: authenticated
[    6.774548] wlan0: associate with <MAC C-01 PANERA> (try 1/3)
[    6.776919] wlan0: RX AssocResp from <MAC C-01 PANERA> (capab=0x401 status=0 aid=1)
[    6.777826] wlan0: associated
[    6.777854] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   30.649107] wlan0: authenticate with <MAC ID removed>
[   30.650659] wlan0: direct probe to <MAC ID removed> (try 1/3)
[   30.853775] wlan0: direct probe to <MAC ID removed> (try 2/3)
[   31.057966] wlan0: direct probe to <MAC ID removed> (try 3/3)
[   31.261443] wlan0: authentication with <MAC ID removed> timed out
[   31.402286] wlan0: authenticate with <MAC C-01 PANERA>
[   31.404656] wlan0: send auth to <MAC C-01 PANERA> (try 1/3)
[   31.407930] wlan0: authenticated
[   31.409620] wlan0: associate with <MAC C-01 PANERA> (try 1/3)
[   31.412072] wlan0: RX AssocResp from <MAC C-01 PANERA> (capab=0x401 status=0 aid=1)
[   31.412977] wlan0: associated

	======== Done ========

```

Another slight issue. The wireless script in power.d does not seem to be worrking on boot. I need to manually disable power management on the wifi with a 'sudo iwconfig wlan0 power off' every reboot.

ANy ideas where to go from here?

---

### Post by ilja.polivanovas on 2015-03-22
I have absolutely the same problem. Lenovo Yoga 2 Pro.

In windows i have 0% packet loss. But in Ubuntu I have 5-10% loss to wifi gataway.


```
wlan0     IEEE 802.11bgn  ESSID:"IPA"  
          Mode:Managed  Frequency:2.472 GHz  Access Point: 54:04:A6:D2:B1:00
          Bit Rate=2 Mb/s   Tx-Power=22 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=56/70  Signal level=-54 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:53  Invalid misc:54   Missed beacon:0


lo        no wireless extensions.

```

---

### Post by ilja.polivanovas on 2015-09-22
Still no ideas?

---

