---
title: "nm-applet ignores wifi SSIDs after upgrade"
date: 2014-08-28
forum: Networking &amp; Wireless
---

### Post by cov on 2014-08-28
Since upgrading to 14.04, I find that if I lose my wireless connection, nm-applet will subsequently ignore my wifi SSID and will not attempt to reconnect. The SSID no longer shows up in the applet's menu.

Previously it was a bit of a pain because multiple pop ups would appear on screen asking for the WPA password, but at least there was some attempt to reconnect.

Does anyone have the same issue? and a solution?

---

### Post by varunendra on 2014-08-29
I don't think 'I' have seen or read about a similar problem here, but for solution, could you please provide a detailed report of your wireless setup?

Please follow the instructions in this post to download and run 'wireless_script' (experimental version) and post back the report it generates : [http://ubuntuforums.org/showpost.php?p=13024222](http://ubuntuforums.org/showpost.php?p=13024222)

---

### Post by cov on 2014-09-16
Thanks for the help.

Generated response below:

```

	======== Wireless-Info START ========

System-Info ~~~~~~~~~~~~~~~~~~~~~~~~

Threepwood 3.13.0-34-generic x86_64,  Ubuntu 14.04.1 LTS, trusty

CPU    : Intel(R) Core(TM) i5-2450M CPU @ 2.50GHz
Memory : 7898 MB
Uptime : 10:40:12 up 1 day,  4:02,  2 users,  load average: 0.87, 1.02, 1.17


lspci ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

03:00.0 Network controller [0280]: Intel Corporation Centrino Wireless-N 1000 [Condor Peak] [8086:0084]
	Subsystem: Intel Corporation Centrino Wireless-N 1000 BGN [8086:1315]
	Kernel driver in use: iwlwifi
04:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 05)
	Subsystem: Lenovo Device [17aa:3975]
	Kernel driver in use: r8169


lsusb ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Bus 002 Device 004: ID 0bda:0139 Realtek Semiconductor Corp. RTS5139 Card Reader Controller
Bus 002 Device 003: ID 0489:e00d Foxconn / Hon Hai Broadcom Bluetooth 2.1 Device
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 004: ID 5986:0364 Acer, Inc 
Bus 001 Device 008: ID 093a:2510 Pixart Imaging, Inc. Optical Mouse
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


PCMCIA Card Info ~~~~~~~~~~~~~~~~~~~



iwconfig ~~~~~~~~~~~~~~~~~~~~~~~~~~~

wlan0     IEEE 802.11bgn  ESSID:"dave"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: <MAC C-01 dave>   
          Bit Rate=54 Mb/s   Tx-Power=14 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=59/70  Signal level=-51 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:188   Missed beacon:0



rfkill ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

      Interface                  Soft blocked  Hard blocked
0: ideapad_wlan: Wireless LAN        no            no
1: ideapad_bluetooth: Bluetooth      no            no
2: hci0: Bluetooth                   no            no
3: phy0: Wireless LAN                no            no


lsmod ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

acer_wmi               32522  0 
iwldvm                232285  0 
mac80211              630653  1 iwldvm
iwlwifi               169932  1 iwldvm
cfg80211              484040  3 iwlwifi,mac80211,iwldvm
sparse_keymap          13948  2 acer_wmi,ideapad_laptop
mxm_wmi                13021  1 nouveau
wmi                    19177  3 acer_wmi,mxm_wmi,nouveau
video                  19476  3 i915,acer_wmi,nouveau


module parameters ~~~~~~~~~~~~~~~~~~

acer_wmi      (5): brightness=-1 | ec_raw_mode=N | force_series=0 | mailled=-1 | threeg=-1
cfg80211      (2): cfg80211_disable_40mhz_24ghz=N | ieee80211_regdom=00
iwlwifi      (11): 11n_disable=0 | amsdu_size_8K=0 | antenna_coupling=0 | bt_coex_active=Y | fw_restart=Y | led_mode=0 | nvm_file=(null) | power_level=0 | power_save=N | swcrypto=0 | wd_disable=1
mac80211      (5): beacon_loss_count=7 | ieee80211_default_rc_algo=minstrel_ht | max_nullfunc_tries=2 | max_probe_tries=5 | probe_wait_ms=500
video         (3): allow_duplicates=N | brightness_switch_enabled=Y | use_native_backlight=-1
wmi           (2): debug_dump_wdg=N | debug_event=N


nm-tool ~~~~~~~~~~~~~~~~~~~~~~~~~~~~

State: connected (global)
================o=============o=========o=========  =====o=========o===========o==============o=======  ====
 Interface & ID | Type        | Driver  | State        | Default | Speed     | Support      | HW Addr   
================o=============o=========o=========  =====o=========o===========o==============o=======  ====
 <BT Device>    | Bluetooth   | bluez   | disconnected | no      |           |              |           
----------------+-------------+---------+--------------+---------+-----------+--------------+-----------
 eth0           | Wired       | r8169   | unavailable  | no      |           |              | <MAC eth0>
----------------+-------------+---------+--------------+---------+-----------+--------------+-----------
 wlan0  [dave]  | 802.11 WiFi | iwlwifi | connected    | yes     | 54 Mb/s   | WEP/WPA/WPA2 | <MAC wlan0>

    *dave:           Infra, <MAC C-01 dave>, Freq 2462 MHz, Rate 54 Mb/s, Strength 67 WPA
    CATHERINE-PC_Network: Infra, <MAC C-NA CATHERINE-PC_Network 1>, Freq 2412 MHz, Rate 54 Mb/s, Strength 25 WPA2
    yournetworkname: Infra, <MAC C-02 yournetworkname>, Freq 2462 MHz, Rate 54 Mb/s, Strength 22 WPA

    Address:         10.0.0.3
    Prefix:          24 (255.255.255.0)
    Gateway:         10.0.0.2
    DNS:             8.8.8.8
    DNS:             4.4.4.4
----------------+-------------+---------+--------------+---------+-----------+--------------+-----------


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

Afrihost-Mobile-ea03 : ssid=Afrihost-Mobile-ea03 | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 
AlwaysOn             : ssid=AlwaysOn | mac-address=<MAC wlan0> | ipv6=auto | ipv4=auto 
Coventry             : ssid=Coventry | mac-address=<MAC wlan0> | ipv6=auto | ipv4=auto 
dave                 : ssid=dave | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 
D-Link               : ssid=D-Link | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 
yournetworkname      : ssid=yournetworkname | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 


interfaces ~~~~~~~~~~~~~~~~~~~~~~~~~

auto lo
iface lo inet loopback


resolv.conf ~~~~~~~~~~~~~~~~~~~~~~~~

nameserver 127.0.1.1


Routes & Ping ~~~~~~~~~~~~~~~~~~~~~~

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         10.0.0.2        0.0.0.0         UG    0      0        0 wlan0
10.0.0.0        0.0.0.0         255.255.255.0   U     9      0        0 wlan0

--- 10.0.0.2 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 1005ms
rtt min/avg/max/mdev = 1.587/2.583/3.580/0.997 ms

--- 127.0.1.1 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 999ms
rtt min/avg/max/mdev = 0.036/0.043/0.051/0.010 ms


iw reg get ~~~~~~~~~~~~~~~~~~~~~~~~~

(Region : en_US.UTF-8)
country 00:
	(2402 - 2472 @ 40), (3, 20)
	(2457 - 2482 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
	(2474 - 2494 @ 20), (3, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
	(5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
	(5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS


iwlist chan ~~~~~~~~~~~~~~~~~~~~~~~~

wlan0     13 channels in total; available frequencies :
          Channel 01 (2.412 GHz) - 13 (2.472 GHz)

          Current Frequency:2.462 GHz (Channel 11)


iwlist scan ~~~~~~~~~~~~~~~~~~~~~~~~

wlan0     Scan completed :
          Cell 01 - Address: <MAC C-01 dave>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=59/70  Signal level=-51 dBm  
                    Encryption key:on
                    ESSID:"dave"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000006282a92b97
                    Extra: Last beacon: 44ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC C-02 yournetworkname>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=32/70  Signal level=-78 dBm  
                    Encryption key:on
                    ESSID:"yournetworkname"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000013bf16ee23f
                    Extra: Last beacon: 180ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK


blacklist ~~~~~~~~~~~~~~~~~~~~~~~~~~

[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci

[/etc/modprobe.d/osspd.conf]
blacklist snd-pcm-oss
blacklist snd-mixer-oss
blacklist snd-seq-oss


modinfo ~~~~~~~~~~~~~~~~~~~~~~~~~~~~

[acer_wmi]
filename:       /lib/modules/3.13.0-34-generic/kernel/drivers/platform/x86/acer-wmi.ko
srcversion:     15371DC0E403E93954B38E5
depends:        wmi,sparse-keymap,video
parm:           mailled:Set initial state of Mail LED (int)
parm:           brightness:Set initial LCD backlight brightness (int)
parm:           threeg:Set initial state of 3G hardware (int)
parm:           force_series:Force a different laptop series (int)
parm:           ec_raw_mode:Enable EC raw mode (bool)

[iwldvm]
filename:       /lib/modules/3.13.0-34-generic/kernel/drivers/net/wireless/iwlwifi/dvm/iwldvm.ko
version:        in-tree:
srcversion:     C000699B57577A9A45666BA
depends:        iwlwifi,mac80211,cfg80211

[mac80211]
filename:       /lib/modules/3.13.0-34-generic/kernel/net/mac80211/mac80211.ko
srcversion:     8ADA881D348148A3358334C
depends:        cfg80211
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[iwlwifi]
filename:       /lib/modules/3.13.0-34-generic/kernel/drivers/net/wireless/iwlwifi/iwlwifi.ko
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
srcversion:     5AA2E0FDE335B45C3F44AE0
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
filename:       /lib/modules/3.13.0-34-generic/kernel/net/wireless/cfg80211.ko
srcversion:     E786D076B61F97809B04B64
depends:        
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

[mxm_wmi]
filename:       /lib/modules/3.13.0-34-generic/kernel/drivers/platform/x86/mxm-wmi.ko
srcversion:     62CBD37DE87DF0C4CD7FBA3
depends:        wmi

[wmi]
filename:       /lib/modules/3.13.0-34-generic/kernel/drivers/platform/x86/wmi.ko
srcversion:     CED5410F008DC70DF5F064B
depends:        
parm:           debug_event:Log WMI Events [0/1] (bool)
parm:           debug_dump_wdg:Dump available WMI interfaces [0/1] (bool)

[video]
filename:       /lib/modules/3.13.0-34-generic/kernel/drivers/acpi/video.ko
srcversion:     274A2250DEAB415D412A67C
depends:        
parm:           brightness_switch_enabled:bool
parm:           allow_duplicates:bool
parm:           use_native_backlight:int


udev rules ~~~~~~~~~~~~~~~~~~~~~~~~~

# PCI device 0x10ec:/sys/devices/pci0000:00/0000:00:1c.3/0000:04:00.0 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC eth0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

# PCI device 0x8086:/sys/devices/pci0000:00/0000:00:1c.1/0000:03:00.0 (iwlwifi)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC wlan0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"


Custom files/entries ~~~~~~~~~~~~~~~

/etc/modules        : Default
/etc/rc.local       : Not Default
/etc/modprobe.d     : Not Default
/etc/pm/(cnf|pw|sl) : Default

[/etc/rc.local]
hciconfig hci0 inqmode 0
exit 0

[/etc/modprobe.d]
iwlwifi.conf      : remove iwlwifi \
                    (/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
                    && /sbin/modprobe -r mac80211
mlx4.conf         : softdep mlx4_core post: mlx4_en


Kernel boot line ~~~~~~~~~~~~~~~~~~~

BOOT_IMAGE=/boot/vmlinuz-3.13.0-34-generic root=UUID=0277142b-c575-4175-ac75-acbec68aa5d0 ro quiet splash vt.handoff=7


dmesg ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

[    0.470657] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[    0.470937] audit: initializing netlink socket (disabled)
[    0.697111] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[   20.380752] wmi: Mapper loaded
[   20.482495] iwlwifi 0000:03:00.0: can't disable ASPM; OS doesn't have ASPM control
[   20.482570] iwlwifi 0000:03:00.0: irq 45 for MSI/MSI-X
[   20.883925] iwlwifi 0000:03:00.0: loaded firmware version 39.31.5.1 build 35138 op_mode iwldvm
[   20.899966] iwlwifi 0000:03:00.0: CONFIG_IWLWIFI_DEBUG disabled
[   20.899967] iwlwifi 0000:03:00.0: CONFIG_IWLWIFI_DEBUGFS enabled
[   20.899968] iwlwifi 0000:03:00.0: CONFIG_IWLWIFI_DEVICE_TRACING enabled
[   20.899970] iwlwifi 0000:03:00.0: Detected Intel(R) Centrino(R) Wireless-N 1000 BGN, REV=0x6C
[   20.900021] iwlwifi 0000:03:00.0: L1 Enabled; Disabling L0S
[   20.923479] ieee80211 phy0: Selected rate control algorithm 'iwl-agn-rs'
[   21.388766] acer_wmi: Acer Laptop ACPI-WMI Extras
[   21.429702] acer_wmi: Brightness must be controlled by acpi video driver
[   28.537819] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   31.630630] iwlwifi 0000:03:00.0: L1 Enabled; Disabling L0S
[   31.638052] iwlwifi 0000:03:00.0: Radio type=0x0-0x0-0x3
[   31.673123] iwlwifi 0000:03:00.0: L1 Enabled; Disabling L0S
[   31.680517] iwlwifi 0000:03:00.0: Radio type=0x0-0x0-0x3
[   31.721036] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   31.721298] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   32.534202] wlan0: authenticate with <MAC C-01 dave>
[   32.546807] wlan0: send auth to <MAC C-01 dave> (try 1/3)
[   32.548389] wlan0: authenticated
[   32.548548] iwlwifi 0000:03:00.0 wlan0: disabling HT/VHT due to WEP/TKIP use
[   32.550979] wlan0: associate with <MAC C-01 dave> (try 1/3)
[   32.553913] wlan0: RX AssocResp from <MAC C-01 dave> (capab=0x411 status=0 aid=2)
[   32.557841] wlan0: associated
[   32.557860] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[27801.442489] wlan0: deauthenticated from <MAC C-01 dave> (Reason: 7)
[27801.592040] wlan0: authenticate with <MAC C-01 dave>
[27801.602062] wlan0: send auth to <MAC C-01 dave> (try 1/3)
[27801.604310] wlan0: authenticated
[27801.604512] iwlwifi 0000:03:00.0 wlan0: disabling HT/VHT due to WEP/TKIP use
[27801.604709] wlan0: associate with <MAC C-01 dave> (try 1/3)
[27801.607740] wlan0: RX AssocResp from <MAC C-01 dave> (capab=0x411 status=0 aid=2)
[27801.610964] wlan0: associated
[27844.662348] wlan0: deauthenticated from <MAC C-01 dave> (Reason: 7)
[27844.738608] wlan0: authenticate with <MAC C-01 dave>
[27844.739748] wlan0: send auth to <MAC C-01 dave> (try 1/3)
[27844.741993] wlan0: authenticated
[27844.742207] iwlwifi 0000:03:00.0 wlan0: disabling HT/VHT due to WEP/TKIP use
[27844.744892] wlan0: associate with <MAC C-01 dave> (try 1/3)
[27844.747895] wlan0: RX AssocResp from <MAC C-01 dave> (capab=0x411 status=0 aid=2)
[27844.752304] wlan0: associated
[27975.306044] wlan0: deauthenticated from <MAC C-01 dave> (Reason: 7)
[27991.457018] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[28454.261016] iwlwifi 0000:03:00.0: L1 Enabled; Disabling L0S
[28454.268529] iwlwifi 0000:03:00.0: Radio type=0x0-0x0-0x3
[28454.313593] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[28455.154426] wlan0: authenticate with <MAC C-01 dave>
[28455.164921] wlan0: send auth to <MAC C-01 dave> (try 1/3)
[28455.167143] wlan0: authenticated
[28455.167281] iwlwifi 0000:03:00.0 wlan0: disabling HT/VHT due to WEP/TKIP use
[28455.171112] wlan0: associate with <MAC C-01 dave> (try 1/3)
[28455.174265] wlan0: RX AssocResp from <MAC C-01 dave> (capab=0x411 status=0 aid=2)
[28455.179428] wlan0: associated
[28455.179485] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[28456.196279] wlan0: deauthenticating from <MAC C-01 dave> by local choice (reason=2)
[28456.203574] wlan0: authenticate with <MAC C-01 dave>
[28456.213356] wlan0: send auth to <MAC C-01 dave> (try 1/3)
[28456.217678] wlan0: authenticated
[28456.218025] iwlwifi 0000:03:00.0 wlan0: disabling HT/VHT due to WEP/TKIP use
[28456.221742] wlan0: associate with <MAC C-01 dave> (try 1/3)
[28456.224762] wlan0: RX AssocResp from <MAC C-01 dave> (capab=0x411 status=0 aid=2)
[28456.228958] wlan0: associated
[28460.893446] wlan0: deauthenticated from <MAC C-01 dave> (Reason: 7)
[28461.418228] wlan0: authenticate with <MAC C-01 dave>
[28461.428284] wlan0: send auth to <MAC C-01 dave> (try 1/3)
[28461.430477] wlan0: authenticated
[28461.430773] iwlwifi 0000:03:00.0 wlan0: disabling HT/VHT due to WEP/TKIP use
[28461.431044] wlan0: associate with <MAC C-01 dave> (try 1/3)
[28461.434192] wlan0: RX AssocResp from <MAC C-01 dave> (capab=0x411 status=0 aid=2)
[28461.438541] wlan0: associated
[28462.713556] wlan0: deauthenticating from <MAC C-01 dave> by local choice (reason=3)
[28463.153160] wlan0: authenticate with <MAC C-01 dave>
[28463.155335] wlan0: send auth to <MAC C-01 dave> (try 1/3)
[28463.157538] wlan0: authenticated
[28463.157706] iwlwifi 0000:03:00.0 wlan0: disabling HT/VHT due to WEP/TKIP use
[28463.160763] wlan0: associate with <MAC C-01 dave> (try 1/3)
[28463.163758] wlan0: RX AssocResp from <MAC C-01 dave> (capab=0x411 status=0 aid=2)
[28463.168155] wlan0: associated
[28463.751267] wlan0: deauthenticating from <MAC C-01 dave> by local choice (reason=3)
[28463.758642] wlan0: authenticate with <MAC C-01 dave>
[28463.763616] wlan0: send auth to <MAC C-01 dave> (try 1/3)
[28463.763900] wlan0: deauthenticating from <MAC C-01 dave> by local choice (reason=3)
[28464.162957] wlan0: authenticate with <MAC C-01 dave>
[28464.173171] wlan0: send auth to <MAC C-01 dave> (try 1/3)
[28464.175384] wlan0: authenticated
[28464.175679] iwlwifi 0000:03:00.0 wlan0: disabling HT/VHT due to WEP/TKIP use
[28464.179496] wlan0: associate with <MAC C-01 dave> (try 1/3)
[28464.182485] wlan0: RX AssocResp from <MAC C-01 dave> (capab=0x411 status=0 aid=2)
[28464.185326] wlan0: associated
[28464.213730] wlan0: deauthenticating from <MAC C-01 dave> by local choice (reason=2)
[28464.221780] wlan0: authenticate with <MAC C-01 dave>
[28464.234270] wlan0: send auth to <MAC C-01 dave> (try 1/3)
[28464.236467] wlan0: authenticated
[28464.236629] iwlwifi 0000:03:00.0 wlan0: disabling HT/VHT due to WEP/TKIP use
[28464.239362] wlan0: associate with <MAC C-01 dave> (try 1/3)
[28464.242770] wlan0: RX AssocResp from <MAC C-01 dave> (capab=0x411 status=0 aid=2)
[28464.246972] wlan0: associated
[28478.140822] wlan0: deauthenticated from <MAC C-01 dave> (Reason: 7)
[28478.705240] wlan0: authenticate with <MAC C-01 dave>
[28478.715048] wlan0: send auth to <MAC C-01 dave> (try 1/3)
[28478.717298] wlan0: authenticated
[28478.717497] iwlwifi 0000:03:00.0 wlan0: disabling HT/VHT due to WEP/TKIP use
[28478.720622] wlan0: associate with <MAC C-01 dave> (try 1/3)
[28478.723637] wlan0: RX AssocResp from <MAC C-01 dave> (capab=0x411 status=0 aid=2)
[28478.728332] wlan0: associated
[28485.123983] wlan0: deauthenticated from <MAC C-01 dave> (Reason: 7)
[28485.146693] wlan0: authenticate with <MAC C-01 dave>
[28485.156894] wlan0: send auth to <MAC C-01 dave> (try 1/3)
[28485.159367] wlan0: authenticated
[28485.159726] iwlwifi 0000:03:00.0 wlan0: disabling HT/VHT due to WEP/TKIP use
[28485.161957] wlan0: associate with <MAC C-01 dave> (try 1/3)
[28485.165063] wlan0: RX AssocResp from <MAC C-01 dave> (capab=0x411 status=0 aid=2)
[28485.169356] wlan0: associated
[28488.203797] wlan0: deauthenticated from <MAC C-01 dave> (Reason: 7)
[28488.232187] wlan0: authenticate with <MAC C-01 dave>
[28488.242053] wlan0: send auth to <MAC C-01 dave> (try 1/3)
[28488.244209] wlan0: authenticated
[28488.244378] iwlwifi 0000:03:00.0 wlan0: disabling HT/VHT due to WEP/TKIP use
[28488.247455] wlan0: associate with <MAC C-01 dave> (try 1/3)
[28488.250899] wlan0: RX AssocResp from <MAC C-01 dave> (capab=0x411 status=0 aid=2)
[28488.256547] wlan0: associated
[28490.623969] wlan0: deauthenticated from <MAC C-01 dave> (Reason: 7)
[28490.646024] wlan0: authenticate with <MAC C-01 dave>
[28490.655971] wlan0: send auth to <MAC C-01 dave> (try 1/3)
[28490.658193] wlan0: authenticated
[28490.658483] iwlwifi 0000:03:00.0 wlan0: disabling HT/VHT due to WEP/TKIP use
[28490.661555] wlan0: associate with <MAC C-01 dave> (try 1/3)
[28490.664590] wlan0: RX AssocResp from <MAC C-01 dave> (capab=0x411 status=0 aid=2)
[28490.669133] wlan0: associated
[28558.813077] wlan0: deauthenticated from <MAC C-01 dave> (Reason: 7)
[28558.844663] wlan0: authenticate with <MAC C-01 dave>
[28558.846118] wlan0: send auth to <MAC C-01 dave> (try 1/3)
[28558.847739] wlan0: authenticated
[28558.848125] iwlwifi 0000:03:00.0 wlan0: disabling HT/VHT due to WEP/TKIP use
[28558.851474] wlan0: associate with <MAC C-01 dave> (try 1/3)
[28558.854552] wlan0: RX AssocResp from <MAC C-01 dave> (capab=0x411 status=0 aid=2)
[28558.858369] wlan0: associated
[28562.984340] wlan0: deauthenticated from <MAC C-01 dave> (Reason: 7)
[28578.235492] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[28672.183314] iwlwifi 0000:03:00.0: L1 Enabled; Disabling L0S
[28672.191134] iwlwifi 0000:03:00.0: Radio type=0x0-0x0-0x3
[28672.227494] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[28672.735424] wlan0: authenticate with <MAC C-01 dave>
[28672.746932] wlan0: send auth to <MAC C-01 dave> (try 1/3)
[28672.748508] wlan0: authenticated
[28672.748621] iwlwifi 0000:03:00.0 wlan0: disabling HT/VHT due to WEP/TKIP use
[28672.751694] wlan0: associate with <MAC C-01 dave> (try 1/3)
[28672.754625] wlan0: RX AssocResp from <MAC C-01 dave> (capab=0x411 status=0 aid=1)
[28672.759211] wlan0: associated
[28672.759252] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[28678.876953] wlan0: deauthenticated from <MAC C-01 dave> (Reason: 7)
[28678.908226] wlan0: authenticate with <MAC C-01 dave>
[28678.917972] wlan0: send auth to <MAC C-01 dave> (try 1/3)
[28678.920176] wlan0: authenticated
[28678.920499] iwlwifi 0000:03:00.0 wlan0: disabling HT/VHT due to WEP/TKIP use
[28678.923714] wlan0: associate with <MAC C-01 dave> (try 1/3)
[28678.926812] wlan0: RX AssocResp from <MAC C-01 dave> (capab=0x411 status=0 aid=1)
[28678.930348] wlan0: associated
[28682.331120] wlan0: deauthenticated from <MAC C-01 dave> (Reason: 7)
[28682.360075] wlan0: authenticate with <MAC C-01 dave>
[28682.370095] wlan0: send auth to <MAC C-01 dave> (try 1/3)
[28682.371729] wlan0: authenticated
[28682.372125] iwlwifi 0000:03:00.0 wlan0: disabling HT/VHT due to WEP/TKIP use
[28682.375282] wlan0: associate with <MAC C-01 dave> (try 1/3)
[28682.378308] wlan0: RX AssocResp from <MAC C-01 dave> (capab=0x411 status=0 aid=1)
[28682.382794] wlan0: associated
[28684.622991] wlan0: deauthenticated from <MAC C-01 dave> (Reason: 7)
[28684.644642] wlan0: authenticate with <MAC C-01 dave>
[28684.654352] wlan0: send auth to <MAC C-01 dave> (try 1/3)
[28684.655932] wlan0: authenticated
[28684.656247] iwlwifi 0000:03:00.0 wlan0: disabling HT/VHT due to WEP/TKIP use
[28684.660291] wlan0: associate with <MAC C-01 dave> (try 1/3)
[28684.663323] wlan0: RX AssocResp from <MAC C-01 dave> (capab=0x411 status=0 aid=1)
[28684.667667] wlan0: associated
[28689.326471] wlan0: deauthenticated from <MAC C-01 dave> (Reason: 7)
[28689.348641] wlan0: authenticate with <MAC C-01 dave>
[28689.358593] wlan0: send auth to <MAC C-01 dave> (try 1/3)
[28689.360242] wlan0: authenticated
[28689.360529] iwlwifi 0000:03:00.0 wlan0: disabling HT/VHT due to WEP/TKIP use
[28689.368043] wlan0: associate with <MAC C-01 dave> (try 1/3)
[28689.371118] wlan0: RX AssocResp from <MAC C-01 dave> (capab=0x411 status=0 aid=1)
[28689.375612] wlan0: associated
[28692.045269] wlan0: deauthenticated from <MAC C-01 dave> (Reason: 7)
[28692.073953] wlan0: authenticate with <MAC C-01 dave>
[28692.083888] wlan0: send auth to <MAC C-01 dave> (try 1/3)
[28692.085541] wlan0: authenticated
[28692.085892] iwlwifi 0000:03:00.0 wlan0: disabling HT/VHT due to WEP/TKIP use
[28692.089117] wlan0: associate with <MAC C-01 dave> (try 1/3)
[28692.092196] wlan0: RX AssocResp from <MAC C-01 dave> (capab=0x411 status=0 aid=1)
[28692.096184] wlan0: associated
[28694.560434] wlan0: deauthenticated from <MAC C-01 dave> (Reason: 7)
[28694.590424] wlan0: authenticate with <MAC C-01 dave>
[28694.600452] wlan0: send auth to <MAC C-01 dave> (try 1/3)
[28694.602081] wlan0: authenticated
[28694.602339] iwlwifi 0000:03:00.0 wlan0: disabling HT/VHT due to WEP/TKIP use
[28694.605829] wlan0: associate with <MAC C-01 dave> (try 1/3)
[28694.608879] wlan0: RX AssocResp from <MAC C-01 dave> (capab=0x411 status=0 aid=1)
[28694.613482] wlan0: associated
[28700.402000] wlan0: deauthenticated from <MAC C-01 dave> (Reason: 7)
[28700.422726] wlan0: authenticate with <MAC C-01 dave>
[28700.432964] wlan0: send auth to <MAC C-01 dave> (try 1/3)
[28700.434615] wlan0: authenticated
[28700.434934] iwlwifi 0000:03:00.0 wlan0: disabling HT/VHT due to WEP/TKIP use
[28700.438241] wlan0: associate with <MAC C-01 dave> (try 1/3)
[28700.441316] wlan0: RX AssocResp from <MAC C-01 dave> (capab=0x411 status=0 aid=1)
[28700.445461] wlan0: associated
[28702.834259] wlan0: deauthenticated from <MAC C-01 dave> (Reason: 7)
[28702.851426] wlan0: authenticate with <MAC C-01 dave>
[28702.861113] wlan0: send auth to <MAC C-01 dave> (try 1/3)
[28702.862654] wlan0: authenticated
[28702.862812] iwlwifi 0000:03:00.0 wlan0: disabling HT/VHT due to WEP/TKIP use
[28702.863047] wlan0: associate with <MAC C-01 dave> (try 1/3)
[28702.872771] wlan0: RX AssocResp from <MAC C-01 dave> (capab=0x411 status=0 aid=1)
[28702.876880] wlan0: associated
[28705.468511] wlan0: deauthenticated from <MAC C-01 dave> (Reason: 7)
[28705.492709] wlan0: authenticate with <MAC C-01 dave>
[28705.502843] wlan0: send auth to <MAC C-01 dave> (try 1/3)
[28705.504435] wlan0: authenticated
[28705.504661] iwlwifi 0000:03:00.0 wlan0: disabling HT/VHT due to WEP/TKIP use
[28705.507781] wlan0: associate with <MAC C-01 dave> (try 1/3)
[28705.510914] wlan0: RX AssocResp from <MAC C-01 dave> (capab=0x411 status=0 aid=1)
[28705.514581] wlan0: associated
[28711.298190] wlan0: deauthenticated from <MAC C-01 dave> (Reason: 7)
[28711.317267] wlan0: authenticate with <MAC C-01 dave>
[28711.327290] wlan0: send auth to <MAC C-01 dave> (try 1/3)
[28711.328977] wlan0: authenticated
[28711.329318] iwlwifi 0000:03:00.0 wlan0: disabling HT/VHT due to WEP/TKIP use
[28711.332200] wlan0: associate with <MAC C-01 dave> (try 1/3)
[28711.335260] wlan0: RX AssocResp from <MAC C-01 dave> (capab=0x411 status=0 aid=1)
[28711.338418] wlan0: associated
[28712.339770] wlan0: deauthenticated from <MAC C-01 dave> (Reason: 7)
[28712.355591] wlan0: authenticate with <MAC C-01 dave>
[28712.365879] wlan0: send auth to <MAC C-01 dave> (try 1/3)
[28712.367477] wlan0: authenticated
[28712.367835] iwlwifi 0000:03:00.0 wlan0: disabling HT/VHT due to WEP/TKIP use
[28712.370774] wlan0: associate with <MAC C-01 dave> (try 1/3)
[28712.373794] wlan0: RX AssocResp from <MAC C-01 dave> (capab=0x411 status=0 aid=1)
[28712.378973] wlan0: associated
[29980.255448] wlan0: deauthenticated from <MAC C-01 dave> (Reason: 7)
[29980.316950] wlan0: authenticate with <MAC C-01 dave>
[29980.327972] wlan0: send auth to <MAC C-01 dave> (try 1/3)
[29980.330201] wlan0: authenticated
[29980.330447] iwlwifi 0000:03:00.0 wlan0: disabling HT/VHT due to WEP/TKIP use
[29980.332085] wlan0: associate with <MAC C-01 dave> (try 1/3)
[29980.335150] wlan0: RX AssocResp from <MAC C-01 dave> (capab=0x411 status=0 aid=1)
[29980.339355] wlan0: associated
[29983.338242] wlan0: deauthenticated from <MAC C-01 dave> (Reason: 7)
[29998.766367] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[30018.024428] iwlwifi 0000:03:00.0: L1 Enabled; Disabling L0S
[30018.032137] iwlwifi 0000:03:00.0: Radio type=0x0-0x0-0x3
[30018.076962] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[30018.859928] wlan0: authenticate with <MAC C-01 dave>
[30018.871116] wlan0: send auth to <MAC C-01 dave> (try 1/3)
[30018.873339] wlan0: authenticated
[30018.873732] iwlwifi 0000:03:00.0 wlan0: disabling HT/VHT due to WEP/TKIP use
[30018.873904] wlan0: associate with <MAC C-01 dave> (try 1/3)
[30018.876928] wlan0: RX AssocResp from <MAC C-01 dave> (capab=0x411 status=0 aid=2)
[30018.881159] wlan0: associated
[30018.881222] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[30019.907625] wlan0: deauthenticating from <MAC C-01 dave> by local choice (reason=2)
[30019.917474] wlan0: authenticate with <MAC C-01 dave>
[30019.927915] wlan0: send auth to <MAC C-01 dave> (try 1/3)
[30019.930143] wlan0: authenticated
[30019.930306] iwlwifi 0000:03:00.0 wlan0: disabling HT/VHT due to WEP/TKIP use
[30019.932628] wlan0: associate with <MAC C-01 dave> (try 1/3)
[30019.935575] wlan0: RX AssocResp from <MAC C-01 dave> (capab=0x411 status=0 aid=2)
[30019.938959] wlan0: associated
[31961.493513] wlan0: deauthenticated from <MAC C-01 dave> (Reason: 7)
[31962.097413] wlan0: authenticate with <MAC C-01 dave>
[31962.107363] wlan0: send auth to <MAC C-01 dave> (try 1/3)
[31962.109007] wlan0: authenticated
[31962.109329] iwlwifi 0000:03:00.0 wlan0: disabling HT/VHT due to WEP/TKIP use
[31962.109607] wlan0: associate with <MAC C-01 dave> (try 1/3)
[31962.112642] wlan0: RX AssocResp from <MAC C-01 dave> (capab=0x411 status=0 aid=2)
[31962.115825] wlan0: associated
[32692.764929] wlan0: deauthenticated from <MAC C-01 dave> (Reason: 7)
[32693.048870] wlan0: authenticate with <MAC C-01 dave>
[32693.058943] wlan0: send auth to <MAC C-01 dave> (try 1/3)
[32693.060592] wlan0: authenticated
[32693.060950] iwlwifi 0000:03:00.0 wlan0: disabling HT/VHT due to WEP/TKIP use
[32693.063060] wlan0: associate with <MAC C-01 dave> (try 1/3)
[32693.066143] wlan0: RX AssocResp from <MAC C-01 dave> (capab=0x411 status=0 aid=2)
[32693.070199] wlan0: associated
[32695.161353] wlan0: deauthenticated from <MAC C-01 dave> (Reason: 7)
[32711.114840] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[32788.039576] iwlwifi 0000:03:00.0: L1 Enabled; Disabling L0S
[32788.047157] iwlwifi 0000:03:00.0: Radio type=0x0-0x0-0x3
[32788.084217] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[32788.798919] wlan0: authenticate with <MAC C-01 dave>
[32788.809595] wlan0: send auth to <MAC C-01 dave> (try 1/3)
[32788.811818] wlan0: authenticated
[32788.812136] iwlwifi 0000:03:00.0 wlan0: disabling HT/VHT due to WEP/TKIP use
[32788.815123] wlan0: associate with <MAC C-01 dave> (try 1/3)
[32788.818375] wlan0: RX AssocResp from <MAC C-01 dave> (capab=0x411 status=0 aid=2)
[32788.822346] wlan0: associated
[32788.822373] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[32789.847580] wlan0: deauthenticating from <MAC C-01 dave> by local choice (reason=2)
[32789.863094] wlan0: authenticate with <MAC C-01 dave>
[32789.872760] wlan0: send auth to <MAC C-01 dave> (try 1/3)
[32789.875935] wlan0: authenticated
[32789.876098] iwlwifi 0000:03:00.0 wlan0: disabling HT/VHT due to WEP/TKIP use
[32789.877723] wlan0: associate with <MAC C-01 dave> (try 1/3)
[32789.880712] wlan0: RX AssocResp from <MAC C-01 dave> (capab=0x411 status=0 aid=2)
[32789.884081] wlan0: associated
[43191.991656] wlan0: deauthenticated from <MAC C-01 dave> (Reason: 7)
[43192.546813] wlan0: authenticate with <MAC C-01 dave>
[43192.549076] wlan0: send auth to <MAC C-01 dave> (try 1/3)
[43192.550753] wlan0: authenticated
[43192.550973] iwlwifi 0000:03:00.0 wlan0: disabling HT/VHT due to WEP/TKIP use
[43192.553259] wlan0: associate with <MAC C-01 dave> (try 1/3)
[43192.556278] wlan0: RX AssocResp from <MAC C-01 dave> (capab=0x411 status=0 aid=2)
[43192.560652] wlan0: associated
[49003.222219] wlan0: deauthenticated from <MAC C-01 dave> (Reason: 7)
[49003.269331] wlan0: authenticate with <MAC C-01 dave>
[49003.270576] wlan0: send auth to <MAC C-01 dave> (try 1/3)
[49003.272830] wlan0: authenticated
[49003.273205] iwlwifi 0000:03:00.0 wlan0: disabling HT/VHT due to WEP/TKIP use
[49003.275482] wlan0: associate with <MAC C-01 dave> (try 1/3)
[49003.278669] wlan0: RX AssocResp from <MAC C-01 dave> (capab=0x411 status=0 aid=2)
[49003.282116] wlan0: associated
[49336.609029] wlan0: deauthenticated from <MAC C-01 dave> (Reason: 7)
[49352.402053] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[85024.168860] iwlwifi 0000:03:00.0: L1 Enabled; Disabling L0S
[85024.176558] iwlwifi 0000:03:00.0: Radio type=0x0-0x0-0x3
[85024.223056] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[85025.112931] wlan0: authenticate with <MAC C-01 dave>
[85025.123690] wlan0: send auth to <MAC C-01 dave> (try 1/3)
[85025.125967] wlan0: authenticated
[85025.126304] iwlwifi 0000:03:00.0 wlan0: disabling HT/VHT due to WEP/TKIP use
[85025.126837] wlan0: associate with <MAC C-01 dave> (try 1/3)
[85025.129955] wlan0: RX AssocResp from <MAC C-01 dave> (capab=0x411 status=0 aid=2)
[85025.135449] wlan0: associated
[85025.135529] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[85026.161239] wlan0: deauthenticating from <MAC C-01 dave> by local choice (reason=2)
[85026.170638] wlan0: authenticate with <MAC C-01 dave>
[85026.180266] wlan0: send auth to <MAC C-01 dave> (try 1/3)
[85026.182426] wlan0: authenticated
[85026.182585] iwlwifi 0000:03:00.0 wlan0: disabling HT/VHT due to WEP/TKIP use
[85026.185450] wlan0: associate with <MAC C-01 dave> (try 1/3)
[85026.188398] wlan0: RX AssocResp from <MAC C-01 dave> (capab=0x411 status=0 aid=2)
[85026.192216] wlan0: associated
[92937.609877] wlan0: deauthenticated from <MAC C-01 dave> (Reason: 7)
[92938.081381] wlan0: authenticate with <MAC C-01 dave>
[92938.091362] wlan0: send auth to <MAC C-01 dave> (try 1/3)
[92938.092971] wlan0: authenticated
[92938.093647] iwlwifi 0000:03:00.0 wlan0: disabling HT/VHT due to WEP/TKIP use
[92938.097567] wlan0: associate with <MAC C-01 dave> (try 1/3)
[92938.100685] wlan0: RX AssocResp from <MAC C-01 dave> (capab=0x411 status=0 aid=2)
[92938.104786] wlan0: associated
[98709.005094] wlan0: deauthenticated from <MAC C-01 dave> (Reason: 7)
[98709.076553] wlan0: authenticate with <MAC C-01 dave>
[98709.086402] wlan0: send auth to <MAC C-01 dave> (try 1/3)
[98709.088529] wlan0: authenticated
[98709.088659] iwlwifi 0000:03:00.0 wlan0: disabling HT/VHT due to WEP/TKIP use
[98709.092017] wlan0: associate with <MAC C-01 dave> (try 1/3)
[98709.095064] wlan0: RX AssocResp from <MAC C-01 dave> (capab=0x411 status=0 aid=2)
[98709.100488] wlan0: associated
[98713.118299] wlan0: deauthenticated from <MAC C-01 dave> (Reason: 7)
[98728.423569] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[98860.637157] iwlwifi 0000:03:00.0: L1 Enabled; Disabling L0S
[98860.644957] iwlwifi 0000:03:00.0: Radio type=0x0-0x0-0x3
[98860.684232] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[98861.671789] wlan0: authenticate with <MAC C-01 dave>
[98861.682173] wlan0: send auth to <MAC C-01 dave> (try 1/3)
[98861.683765] wlan0: authenticated
[98861.683996] iwlwifi 0000:03:00.0 wlan0: disabling HT/VHT due to WEP/TKIP use
[98861.686823] wlan0: associate with <MAC C-01 dave> (try 1/3)
[98861.689809] wlan0: RX AssocResp from <MAC C-01 dave> (capab=0x411 status=0 aid=3)
[98861.693990] wlan0: associated
[98861.694037] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[98862.725784] wlan0: deauthenticating from <MAC C-01 dave> by local choice (reason=2)
[98862.734427] wlan0: authenticate with <MAC C-01 dave>
[98862.746080] wlan0: send auth to <MAC C-01 dave> (try 1/3)
[98862.747648] wlan0: authenticated
[98862.751502] iwlwifi 0000:03:00.0 wlan0: disabling HT/VHT due to WEP/TKIP use
[98862.753415] wlan0: associate with <MAC C-01 dave> (try 1/3)
[98862.756384] wlan0: RX AssocResp from <MAC C-01 dave> (capab=0x411 status=0 aid=3)
[98862.761076] wlan0: associated
[98895.741162] wlan0: deauthenticated from <MAC C-01 dave> (Reason: 7)
[98896.263259] wlan0: authenticate with <MAC C-01 dave>
[98896.265205] wlan0: send auth to <MAC C-01 dave> (try 1/3)
[98896.266833] wlan0: authenticated
[98896.267303] iwlwifi 0000:03:00.0 wlan0: disabling HT/VHT due to WEP/TKIP use
[98896.270143] wlan0: associate with <MAC C-01 dave> (try 1/3)
[98896.273248] wlan0: RX AssocResp from <MAC C-01 dave> (capab=0x411 status=0 aid=3)
[98896.278526] wlan0: associated
[98898.981104] wlan0: deauthenticated from <MAC C-01 dave> (Reason: 7)
[98899.003255] wlan0: authenticate with <MAC C-01 dave>
[98899.012911] wlan0: send auth to <MAC C-01 dave> (try 1/3)
[98899.014510] wlan0: authenticated
[98899.014742] iwlwifi 0000:03:00.0 wlan0: disabling HT/VHT due to WEP/TKIP use
[98899.018558] wlan0: associate with <MAC C-01 dave> (try 1/3)
[98899.025399] wlan0: RX AssocResp from <MAC C-01 dave> (capab=0x411 status=0 aid=3)
[98899.028861] wlan0: associated
[98902.689497] wlan0: deauthenticated from <MAC C-01 dave> (Reason: 7)
[98902.715779] wlan0: authenticate with <MAC C-01 dave>
[98902.725588] wlan0: send auth to <MAC C-01 dave> (try 1/3)
[98902.727183] wlan0: authenticated
[98902.727402] iwlwifi 0000:03:00.0 wlan0: disabling HT/VHT due to WEP/TKIP use
[98902.731251] wlan0: associate with <MAC C-01 dave> (try 1/3)
[98902.735296] wlan0: RX AssocResp from <MAC C-01 dave> (capab=0x411 status=0 aid=3)
[98902.739243] wlan0: associated
[98904.972696] wlan0: deauthenticated from <MAC C-01 dave> (Reason: 7)
[98904.998043] wlan0: authenticate with <MAC C-01 dave>
[98905.007971] wlan0: send auth to <MAC C-01 dave> (try 1/3)
[98905.010013] wlan0: authenticated
[98905.010346] iwlwifi 0000:03:00.0 wlan0: disabling HT/VHT due to WEP/TKIP use
[98905.013489] wlan0: associate with <MAC C-01 dave> (try 1/3)
[98905.016479] wlan0: RX AssocResp from <MAC C-01 dave> (capab=0x411 status=0 aid=1)
[98905.020357] wlan0: associated
[98908.277040] wlan0: deauthenticated from <MAC C-01 dave> (Reason: 7)
[98908.295319] wlan0: authenticate with <MAC C-01 dave>
[98908.305124] wlan0: send auth to <MAC C-01 dave> (try 1/3)
[98908.307642] wlan0: authenticated
[98908.307940] iwlwifi 0000:03:00.0 wlan0: disabling HT/VHT due to WEP/TKIP use
[98908.310899] wlan0: associate with <MAC C-01 dave> (try 1/3)
[98908.313940] wlan0: RX AssocResp from <MAC C-01 dave> (capab=0x411 status=0 aid=1)
[98908.317894] wlan0: associated
[98911.040201] wlan0: deauthenticated from <MAC C-01 dave> (Reason: 7)
[98911.093336] wlan0: authenticate with <MAC C-01 dave>
[98911.103077] wlan0: send auth to <MAC C-01 dave> (try 1/3)
[98911.104774] wlan0: authenticated
[98911.104917] iwlwifi 0000:03:00.0 wlan0: disabling HT/VHT due to WEP/TKIP use
[98911.108556] wlan0: associate with <MAC C-01 dave> (try 1/3)
[98911.111605] wlan0: RX AssocResp from <MAC C-01 dave> (capab=0x411 status=0 aid=1)
[98911.115667] wlan0: associated
[98914.031400] wlan0: deauthenticated from <MAC C-01 dave> (Reason: 7)
[98914.058581] wlan0: authenticate with <MAC C-01 dave>
[98914.068292] wlan0: send auth to <MAC C-01 dave> (try 1/3)
[98914.069853] wlan0: authenticated
[98914.069991] iwlwifi 0000:03:00.0 wlan0: disabling HT/VHT due to WEP/TKIP use
[98914.070201] wlan0: associate with <MAC C-01 dave> (try 1/3)
[98914.073220] wlan0: RX AssocResp from <MAC C-01 dave> (capab=0x411 status=0 aid=1)
[98914.077059] wlan0: associated
[98915.580207] wlan0: deauthenticated from <MAC C-01 dave> (Reason: 7)
[98915.609537] wlan0: authenticate with <MAC C-01 dave>
[98915.619552] wlan0: send auth to <MAC C-01 dave> (try 1/3)
[98915.621227] wlan0: authenticated
[98915.621441] iwlwifi 0000:03:00.0 wlan0: disabling HT/VHT due to WEP/TKIP use
[98915.624997] wlan0: associate with <MAC C-01 dave> (try 1/3)
[98915.628009] wlan0: RX AssocResp from <MAC C-01 dave> (capab=0x411 status=0 aid=1)
[98915.631884] wlan0: associated
[98917.579537] wlan0: deauthenticated from <MAC C-01 dave> (Reason: 7)
[98917.608373] wlan0: authenticate with <MAC C-01 dave>
[98917.618144] wlan0: send auth to <MAC C-01 dave> (try 1/3)
[98917.619728] wlan0: authenticated
[98917.619892] iwlwifi 0000:03:00.0 wlan0: disabling HT/VHT due to WEP/TKIP use
[98917.623451] wlan0: associate with <MAC C-01 dave> (try 1/3)
[98917.626536] wlan0: RX AssocResp from <MAC C-01 dave> (capab=0x411 status=0 aid=1)
[98917.630540] wlan0: associated
[98919.884586] wlan0: deauthenticated from <MAC C-01 dave> (Reason: 7)
[98919.921935] wlan0: authenticate with <MAC C-01 dave>
[98919.931851] wlan0: send auth to <MAC C-01 dave> (try 1/3)
[98919.933549] wlan0: authenticated
[98919.933979] iwlwifi 0000:03:00.0 wlan0: disabling HT/VHT due to WEP/TKIP use
[98919.937530] wlan0: associate with <MAC C-01 dave> (try 1/3)
[98919.940531] wlan0: RX AssocResp from <MAC C-01 dave> (capab=0x411 status=0 aid=1)
[98919.943841] wlan0: associated
[98922.513690] wlan0: deauthenticated from <MAC C-01 dave> (Reason: 7)
[98922.556490] wlan0: authenticate with <MAC C-01 dave>
[98922.566341] wlan0: send auth to <MAC C-01 dave> (try 1/3)
[98922.568042] wlan0: authenticated
[98922.568386] iwlwifi 0000:03:00.0 wlan0: disabling HT/VHT due to WEP/TKIP use
[98922.571462] wlan0: associate with <MAC C-01 dave> (try 1/3)
[98922.575213] wlan0: RX AssocResp from <MAC C-01 dave> (capab=0x411 status=0 aid=1)
[98922.578464] wlan0: associated
[98925.448264] wlan0: deauthenticated from <MAC C-01 dave> (Reason: 7)
[98925.465734] wlan0: authenticate with <MAC C-01 dave>
[98925.475563] wlan0: send auth to <MAC C-01 dave> (try 1/3)
[98925.477164] wlan0: authenticated
[98925.477379] iwlwifi 0000:03:00.0 wlan0: disabling HT/VHT due to WEP/TKIP use
[98925.481118] wlan0: associate with <MAC C-01 dave> (try 1/3)
[98925.484204] wlan0: RX AssocResp from <MAC C-01 dave> (capab=0x411 status=0 aid=1)
[98925.489160] wlan0: associated
[98928.202450] wlan0: deauthenticated from <MAC C-01 dave> (Reason: 7)
[98928.255466] wlan0: authenticate with <MAC C-01 dave>
[98928.265514] wlan0: send auth to <MAC C-01 dave> (try 1/3)
[98928.267133] wlan0: authenticated
[98928.267381] iwlwifi 0000:03:00.0 wlan0: disabling HT/VHT due to WEP/TKIP use
[98928.270919] wlan0: associate with <MAC C-01 dave> (try 1/3)
[98928.274462] wlan0: RX AssocResp from <MAC C-01 dave> (capab=0x411 status=0 aid=1)
[98928.277637] wlan0: associated
[98929.156403] wlan0: deauthenticated from <MAC C-01 dave> (Reason: 7)
[98929.194706] wlan0: authenticate with <MAC C-01 dave>
[98929.204624] wlan0: send auth to <MAC C-01 dave> (try 1/3)
[98929.206194] wlan0: authenticated
[98929.206348] iwlwifi 0000:03:00.0 wlan0: disabling HT/VHT due to WEP/TKIP use
[98929.210235] wlan0: associate with <MAC C-01 dave> (try 1/3)
[98929.213229] wlan0: RX AssocResp from <MAC C-01 dave> (capab=0x411 status=0 aid=1)
[98929.216945] wlan0: associated
[98931.700160] wlan0: deauthenticated from <MAC C-01 dave> (Reason: 7)
[98931.733855] wlan0: authenticate with <MAC C-01 dave>
[98931.743571] wlan0: send auth to <MAC C-01 dave> (try 1/3)
[98931.745164] wlan0: authenticated
[98931.745302] iwlwifi 0000:03:00.0 wlan0: disabling HT/VHT due to WEP/TKIP use
[98931.748116] wlan0: associate with <MAC C-01 dave> (try 1/3)
[98931.751069] wlan0: RX AssocResp from <MAC C-01 dave> (capab=0x411 status=0 aid=1)
[98931.755535] wlan0: associated
[98934.769722] wlan0: deauthenticated from <MAC C-01 dave> (Reason: 7)
[98934.802383] wlan0: authenticate with <MAC C-01 dave>
[98934.812205] wlan0: send auth to <MAC C-01 dave> (try 1/3)
[98934.814170] wlan0: authenticated
[98934.814356] iwlwifi 0000:03:00.0 wlan0: disabling HT/VHT due to WEP/TKIP use
[98934.817702] wlan0: associate with <MAC C-01 dave> (try 1/3)
[98934.820757] wlan0: RX AssocResp from <MAC C-01 dave> (capab=0x411 status=0 aid=1)
[98934.824397] wlan0: associated
[98938.238017] wlan0: deauthenticated from <MAC C-01 dave> (Reason: 7)
[98938.267572] wlan0: authenticate with <MAC C-01 dave>
[98938.277507] wlan0: send auth to <MAC C-01 dave> (try 1/3)
[98938.280099] wlan0: authenticated
[98938.280494] iwlwifi 0000:03:00.0 wlan0: disabling HT/VHT due to WEP/TKIP use
[98938.282925] wlan0: associate with <MAC C-01 dave> (try 1/3)
[98938.287255] wlan0: RX AssocResp from <MAC C-01 dave> (capab=0x411 status=0 aid=1)
[98938.290636] wlan0: associated
[98940.957765] wlan0: deauthenticated from <MAC C-01 dave> (Reason: 7)
[98940.993370] wlan0: authenticate with <MAC C-01 dave>
[98941.003333] wlan0: send auth to <MAC C-01 dave> (try 1/3)
[98941.005005] wlan0: authenticated
[98941.005271] iwlwifi 0000:03:00.0 wlan0: disabling HT/VHT due to WEP/TKIP use
[98941.008773] wlan0: associate with <MAC C-01 dave> (try 1/3)
[98941.011842] wlan0: RX AssocResp from <MAC C-01 dave> (capab=0x411 status=0 aid=1)
[98941.015826] wlan0: associated
[98944.353089] wlan0: deauthenticated from <MAC C-01 dave> (Reason: 7)
[98944.394247] wlan0: authenticate with <MAC C-01 dave>
[98944.404055] wlan0: send auth to <MAC C-01 dave> (try 1/3)
[98944.405672] wlan0: authenticated
[98944.406732] iwlwifi 0000:03:00.0 wlan0: disabling HT/VHT due to WEP/TKIP use
[98944.409814] wlan0: associate with <MAC C-01 dave> (try 1/3)
[98944.412803] wlan0: RX AssocResp from <MAC C-01 dave> (capab=0x411 status=0 aid=1)
[98944.416024] wlan0: associated
[98945.839530] wlan0: deauthenticated from <MAC C-01 dave> (Reason: 7)
[98945.860479] wlan0: authenticate with <MAC C-01 dave>
[98945.870424] wlan0: send auth to <MAC C-01 dave> (try 1/3)
[98945.872050] wlan0: authenticated
[98945.872401] iwlwifi 0000:03:00.0 wlan0: disabling HT/VHT due to WEP/TKIP use
[98945.876001] wlan0: associate with <MAC C-01 dave> (try 1/3)
[98945.879086] wlan0: RX AssocResp from <MAC C-01 dave> (capab=0x411 status=0 aid=1)
[98945.883227] wlan0: associated
[98950.287381] wlan0: deauthenticated from <MAC C-01 dave> (Reason: 7)
[98950.322626] wlan0: authenticate with <MAC C-01 dave>
[98950.332367] wlan0: send auth to <MAC C-01 dave> (try 1/3)
[98950.334091] wlan0: authenticated
[98950.334393] iwlwifi 0000:03:00.0 wlan0: disabling HT/VHT due to WEP/TKIP use
[98950.338169] wlan0: associate with <MAC C-01 dave> (try 1/3)
[98950.342777] wlan0: RX AssocResp from <MAC C-01 dave> (capab=0x411 status=0 aid=1)
[98950.346337] wlan0: associated
[98953.285260] wlan0: deauthenticated from <MAC C-01 dave> (Reason: 7)
[98953.326674] wlan0: authenticate with <MAC C-01 dave>
[98953.336520] wlan0: send auth to <MAC C-01 dave> (try 1/3)
[98953.338157] wlan0: authenticated
[98953.338486] iwlwifi 0000:03:00.0 wlan0: disabling HT/VHT due to WEP/TKIP use
[98953.342384] wlan0: associate with <MAC C-01 dave> (try 1/3)
[98953.345329] wlan0: RX AssocResp from <MAC C-01 dave> (capab=0x411 status=0 aid=1)
[98953.348758] wlan0: associated
[99056.798548] wlan0: deauthenticated from <MAC C-01 dave> (Reason: 7)
[99056.832759] wlan0: authenticate with <MAC C-01 dave>
[99056.842889] wlan0: send auth to <MAC C-01 dave> (try 1/3)
[99056.845076] wlan0: authenticated
[99056.845234] iwlwifi 0000:03:00.0 wlan0: disabling HT/VHT due to WEP/TKIP use
[99056.848010] wlan0: associate with <MAC C-01 dave> (try 1/3)
[99056.853527] wlan0: RX AssocResp from <MAC C-01 dave> (capab=0x411 status=0 aid=1)
[99056.858095] wlan0: associated
[99062.290250] wlan0: deauthenticated from <MAC C-01 dave> (Reason: 7)
[99062.309565] wlan0: authenticate with <MAC C-01 dave>
[99062.319480] wlan0: send auth to <MAC C-01 dave> (try 1/3)
[99062.322328] wlan0: authenticated
[99062.322557] iwlwifi 0000:03:00.0 wlan0: disabling HT/VHT due to WEP/TKIP use
[99062.324906] wlan0: associate with <MAC C-01 dave> (try 1/3)
[99062.327860] wlan0: RX AssocResp from <MAC C-01 dave> (capab=0x411 status=0 aid=1)
[99062.332436] wlan0: associated
[99128.763530] wlan0: deauthenticated from <MAC C-01 dave> (Reason: 7)
[99128.810926] wlan0: authenticate with <MAC C-01 dave>
[99128.811967] wlan0: send auth to <MAC C-01 dave> (try 1/3)
[99128.814174] wlan0: authenticated
[99128.814374] iwlwifi 0000:03:00.0 wlan0: disabling HT/VHT due to WEP/TKIP use
[99128.818217] wlan0: associate with <MAC C-01 dave> (try 1/3)
[99128.821254] wlan0: RX AssocResp from <MAC C-01 dave> (capab=0x411 status=0 aid=1)
[99128.824831] wlan0: associated
[99273.062930] wlan0: deauthenticated from <MAC C-01 dave> (Reason: 7)
[99288.614306] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[100306.496872] iwlwifi 0000:03:00.0: L1 Enabled; Disabling L0S
[100306.504405] iwlwifi 0000:03:00.0: Radio type=0x0-0x0-0x3
[100306.545525] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[100307.236230] wlan0: authenticate with <MAC C-01 dave>
[100307.246799] wlan0: send auth to <MAC C-01 dave> (try 1/3)
[100307.249030] wlan0: authenticated
[100307.249377] iwlwifi 0000:03:00.0 wlan0: disabling HT/VHT due to WEP/TKIP use
[100307.251277] wlan0: associate with <MAC C-01 dave> (try 1/3)
[100307.254333] wlan0: RX AssocResp from <MAC C-01 dave> (capab=0x411 status=0 aid=2)
[100307.258510] wlan0: associated
[100307.258531] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[100308.288141] wlan0: deauthenticating from <MAC C-01 dave> by local choice (reason=2)
[100308.294829] wlan0: authenticate with <MAC C-01 dave>
[100308.297418] wlan0: send auth to <MAC C-01 dave> (try 1/3)
[100308.301467] wlan0: authenticated
[100308.301601] iwlwifi 0000:03:00.0 wlan0: disabling HT/VHT due to WEP/TKIP use
[100308.301838] wlan0: associate with <MAC C-01 dave> (try 1/3)
[100308.304841] wlan0: RX AssocResp from <MAC C-01 dave> (capab=0x411 status=0 aid=2)
[100308.313001] wlan0: associated
[100486.116036] wlan0: deauthenticated from <MAC C-01 dave> (Reason: 7)
[100486.640052] wlan0: authenticate with <MAC C-01 dave>
[100486.642217] wlan0: send auth to <MAC C-01 dave> (try 1/3)
[100486.644453] wlan0: authenticated
[100486.644678] iwlwifi 0000:03:00.0 wlan0: disabling HT/VHT due to WEP/TKIP use
[100486.647699] wlan0: associate with <MAC C-01 dave> (try 1/3)
[100486.650776] wlan0: RX AssocResp from <MAC C-01 dave> (capab=0x411 status=0 aid=2)
[100486.655300] wlan0: associated
[100489.365550] wlan0: deauthenticated from <MAC C-01 dave> (Reason: 7)
[100489.402283] wlan0: authenticate with <MAC C-01 dave>
[100489.412109] wlan0: send auth to <MAC C-01 dave> (try 1/3)
[100489.413708] wlan0: authenticated
[100489.413884] iwlwifi 0000:03:00.0 wlan0: disabling HT/VHT due to WEP/TKIP use
[100489.417574] wlan0: associate with <MAC C-01 dave> (try 1/3)
[100489.420657] wlan0: RX AssocResp from <MAC C-01 dave> (capab=0x411 status=0 aid=2)
[100489.425960] wlan0: associated
[100494.735294] wlan0: deauthenticated from <MAC C-01 dave> (Reason: 7)
[100494.785559] wlan0: authenticate with <MAC C-01 dave>
[100494.795306] wlan0: send auth to <MAC C-01 dave> (try 1/3)
[100494.796910] wlan0: authenticated
[100494.797082] iwlwifi 0000:03:00.0 wlan0: disabling HT/VHT due to WEP/TKIP use
[100494.797191] wlan0: associate with <MAC C-01 dave> (try 1/3)
[100494.800262] wlan0: RX AssocResp from <MAC C-01 dave> (capab=0x411 status=0 aid=2)
[100494.803823] wlan0: associated
[100498.516497] wlan0: deauthenticated from <MAC C-01 dave> (Reason: 7)
[100498.550655] wlan0: authenticate with <MAC C-01 dave>
[100498.560311] wlan0: send auth to <MAC C-01 dave> (try 1/3)
[100498.561893] wlan0: authenticated
[100498.562084] iwlwifi 0000:03:00.0 wlan0: disabling HT/VHT due to WEP/TKIP use
[100498.562191] wlan0: associate with <MAC C-01 dave> (try 1/3)
[100498.565122] wlan0: RX AssocResp from <MAC C-01 dave> (capab=0x411 status=0 aid=2)
[100498.568643] wlan0: associated
[100500.858525] wlan0: deauthenticated from <MAC C-01 dave> (Reason: 7)
[100500.896886] wlan0: authenticate with <MAC C-01 dave>
[100500.906748] wlan0: send auth to <MAC C-01 dave> (try 1/3)
[100500.908396] wlan0: authenticated
[100500.908600] iwlwifi 0000:03:00.0 wlan0: disabling HT/VHT due to WEP/TKIP use
[100500.912346] wlan0: associate with <MAC C-01 dave> (try 1/3)
[100500.915365] wlan0: RX AssocResp from <MAC C-01 dave> (capab=0x411 status=0 aid=2)
[100500.918924] wlan0: associated
[100524.794679] wlan0: deauthenticated from <MAC C-01 dave> (Reason: 7)
[100524.821802] wlan0: authenticate with <MAC C-01 dave>
[100524.831579] wlan0: send auth to <MAC C-01 dave> (try 1/3)
[100524.833137] wlan0: authenticated
[100524.833301] iwlwifi 0000:03:00.0 wlan0: disabling HT/VHT due to WEP/TKIP use
[100524.837261] wlan0: associate with <MAC C-01 dave> (try 1/3)
[100524.840260] wlan0: RX AssocResp from <MAC C-01 dave> (capab=0x411 status=0 aid=2)
[100524.843661] wlan0: associated
[100529.843616] wlan0: deauthenticated from <MAC C-01 dave> (Reason: 7)
[100529.865603] wlan0: authenticate with <MAC C-01 dave>
[100529.885031] wlan0: send auth to <MAC C-01 dave> (try 1/3)
[100529.886609] wlan0: authenticated
[100529.886771] iwlwifi 0000:03:00.0 wlan0: disabling HT/VHT due to WEP/TKIP use
[100529.889233] wlan0: associate with <MAC C-01 dave> (try 1/3)
[100529.892191] wlan0: RX AssocResp from <MAC C-01 dave> (capab=0x411 status=0 aid=2)
[100529.895777] wlan0: associated
[100532.829109] wlan0: deauthenticated from <MAC C-01 dave> (Reason: 7)
[100532.859973] wlan0: authenticate with <MAC C-01 dave>
[100532.869899] wlan0: send auth to <MAC C-01 dave> (try 1/3)
[100532.871827] wlan0: authenticated
[100532.871983] iwlwifi 0000:03:00.0 wlan0: disabling HT/VHT due to WEP/TKIP use
[100532.874900] wlan0: associate with <MAC C-01 dave> (try 1/3)
[100532.877828] wlan0: RX AssocResp from <MAC C-01 dave> (capab=0x411 status=0 aid=2)
[100532.881043] wlan0: associated

	======== Done ========
```

---

### Post by varunendra on 2014-09-18
Sorry for the delay, still posting in a hurry....

Two quick observations -

1) You are using WPA with TKIP in your router/AP. Unless you are using some ancient wireless device in home that can't support WPA2/AES, it is highly recommended to change the encryption type in your router to WPA2-PSK with AES. Remember - pure WPA2, not WPA/WPA2 mixed mode, and certainly not TKIP.

2) What is "acer-wmi" doing there? Yours seems to be a Lenovo laptop. Please blacklist acer-wmi -
```
echo "blacklist acer_wmi" | sudo tee -a /etc/modprobe.d/blacklist.conf
```
Reboot for the change to take effect.

If the problem persists, please post a fresh wireless script report.

---

### Post by cov on 2014-09-18
Can't connect using WPA2.

I've set up the router as follows:

[ATTACH=CONFIG]256521[/ATTACH]

This may be a South African thing: the TKIP settings were out of the box.



```

	======== Wireless-Info START ========

System-Info ~~~~~~~~~~~~~~~~~~~~~~~~

Threepwood 3.13.0-34-generic x86_64,  Ubuntu 14.04.1 LTS, trusty

CPU    : Intel(R) Core(TM) i5-2450M CPU @ 2.50GHz
Memory : 7898 MB
Uptime : 16:42:22 up 46 min,  3 users,  load average: 0.21, 0.28, 0.36


lspci ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

03:00.0 Network controller [0280]: Intel Corporation Centrino Wireless-N 1000 [Condor Peak] [8086:0084]
	Subsystem: Intel Corporation Centrino Wireless-N 1000 BGN [8086:1315]
	Kernel driver in use: iwlwifi
04:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 05)
	Subsystem: Lenovo Device [17aa:3975]
	Kernel driver in use: r8169


lsusb ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Bus 002 Device 004: ID 0bda:0139 Realtek Semiconductor Corp. RTS5139 Card Reader Controller
Bus 002 Device 003: ID 0489:e00d Foxconn / Hon Hai Broadcom Bluetooth 2.1 Device
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 004: ID 5986:0364 Acer, Inc 
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


PCMCIA Card Info ~~~~~~~~~~~~~~~~~~~



iwconfig ~~~~~~~~~~~~~~~~~~~~~~~~~~~

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=14 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          


rfkill ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

      Interface                  Soft blocked  Hard blocked
0: ideapad_wlan: Wireless LAN        no            no
1: ideapad_bluetooth: Bluetooth      no            no
2: hci0: Bluetooth                   no            no
3: phy0: Wireless LAN                no            no


lsmod ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

iwldvm                232285  0 
mac80211              630653  1 iwldvm
iwlwifi               169932  1 iwldvm
cfg80211              484040  3 iwlwifi,mac80211,iwldvm
mxm_wmi                13021  1 nouveau
wmi                    19177  2 mxm_wmi,nouveau


module parameters ~~~~~~~~~~~~~~~~~~

cfg80211      (2): cfg80211_disable_40mhz_24ghz=N | ieee80211_regdom=00
iwlwifi      (11): 11n_disable=0 | amsdu_size_8K=0 | antenna_coupling=0 | bt_coex_active=Y | fw_restart=Y | led_mode=0 | nvm_file=(null) | power_level=0 | power_save=N | swcrypto=0 | wd_disable=1
mac80211      (5): beacon_loss_count=7 | ieee80211_default_rc_algo=minstrel_ht | max_nullfunc_tries=2 | max_probe_tries=5 | probe_wait_ms=500
wmi           (2): debug_dump_wdg=N | debug_event=N


nm-tool ~~~~~~~~~~~~~~~~~~~~~~~~~~~~

State: disconnected
================o=============o=========o==============o=========o===========o==============o===========
 Interface & ID | Type        | Driver  | State        | Default | Speed     | Support      | HW Addr   
================o=============o=========o==============o=========o===========o==============o===========
 <BT Device>    | Bluetooth   | bluez   | disconnected | no      |           |              |           
----------------+-------------+---------+--------------+---------+-----------+--------------+-----------
 eth0           | Wired       | r8169   | unavailable  | no      | 100 Mb/s  |              | <MAC eth0>
----------------+-------------+---------+--------------+---------+-----------+--------------+-----------
 wlan0          | 802.11 WiFi | iwlwifi | disconnected | no      |           | WEP/WPA/WPA2 | <MAC wlan0>

    yournetworkname: Infra, <MAC C-01 yournetworkname>, Freq 2462 MHz, Rate 54 Mb/s, Strength 20 WPA
    dave:            Infra, <MAC C-02 dave>, Freq 2462 MHz, Rate 54 Mb/s, Strength 84 WPA2
----------------+-------------+---------+--------------+---------+-----------+--------------+-----------


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

Afrihost-Mobile-ea03 : ssid=Afrihost-Mobile-ea03 | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 
AlwaysOn             : ssid=AlwaysOn | mac-address=<MAC wlan0> | ipv6=auto | ipv4=auto 
Coventry             : ssid=Coventry | mac-address=<MAC wlan0> | ipv6=auto | ipv4=auto 
dave                 : ssid=dave | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 
yournetworkname      : ssid=yournetworkname | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 


interfaces ~~~~~~~~~~~~~~~~~~~~~~~~~

auto lo
iface lo inet loopback


resolv.conf ~~~~~~~~~~~~~~~~~~~~~~~~



Routes & Ping ~~~~~~~~~~~~~~~~~~~~~~

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface


iw reg get ~~~~~~~~~~~~~~~~~~~~~~~~~

(Region : en_US.UTF-8)
country 00:
	(2402 - 2472 @ 40), (3, 20)
	(2457 - 2482 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
	(2474 - 2494 @ 20), (3, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
	(5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
	(5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS


iwlist chan ~~~~~~~~~~~~~~~~~~~~~~~~

wlan0     13 channels in total; available frequencies :
          Channel 01 (2.412 GHz) - 13 (2.472 GHz)


iwlist scan ~~~~~~~~~~~~~~~~~~~~~~~~

wlan0     Scan completed :
          Cell 01 - Address: <MAC C-01 yournetworkname>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=33/70  Signal level=-77 dBm  
                    Encryption key:on
                    ESSID:"yournetworkname"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000001693aeb19a3
                    Extra: Last beacon: 48ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC C-02 dave>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=70/70  Signal level=-28 dBm  
                    Encryption key:on
                    ESSID:"dave"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000071c3e223
                    Extra: Last beacon: 48ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK


blacklist ~~~~~~~~~~~~~~~~~~~~~~~~~~

[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci

[/etc/modprobe.d/blacklist.conf]
blacklist acer_wmi

[/etc/modprobe.d/osspd.conf]
blacklist snd-pcm-oss
blacklist snd-mixer-oss
blacklist snd-seq-oss


modinfo ~~~~~~~~~~~~~~~~~~~~~~~~~~~~

[iwldvm]
filename:       /lib/modules/3.13.0-34-generic/kernel/drivers/net/wireless/iwlwifi/dvm/iwldvm.ko
version:        in-tree:
srcversion:     C000699B57577A9A45666BA
depends:        iwlwifi,mac80211,cfg80211

[mac80211]
filename:       /lib/modules/3.13.0-34-generic/kernel/net/mac80211/mac80211.ko
srcversion:     8ADA881D348148A3358334C
depends:        cfg80211
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[iwlwifi]
filename:       /lib/modules/3.13.0-34-generic/kernel/drivers/net/wireless/iwlwifi/iwlwifi.ko
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
srcversion:     5AA2E0FDE335B45C3F44AE0
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
filename:       /lib/modules/3.13.0-34-generic/kernel/net/wireless/cfg80211.ko
srcversion:     E786D076B61F97809B04B64
depends:        
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

[mxm_wmi]
filename:       /lib/modules/3.13.0-34-generic/kernel/drivers/platform/x86/mxm-wmi.ko
srcversion:     62CBD37DE87DF0C4CD7FBA3
depends:        wmi

[wmi]
filename:       /lib/modules/3.13.0-34-generic/kernel/drivers/platform/x86/wmi.ko
srcversion:     CED5410F008DC70DF5F064B
depends:        
parm:           debug_event:Log WMI Events [0/1] (bool)
parm:           debug_dump_wdg:Dump available WMI interfaces [0/1] (bool)


udev rules ~~~~~~~~~~~~~~~~~~~~~~~~~

# PCI device 0x10ec:/sys/devices/pci0000:00/0000:00:1c.3/0000:04:00.0 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC eth0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

# PCI device 0x8086:/sys/devices/pci0000:00/0000:00:1c.1/0000:03:00.0 (iwlwifi)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC wlan0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"


Custom files/entries ~~~~~~~~~~~~~~~

/etc/modules        : Default
/etc/rc.local       : Not Default
/etc/modprobe.d     : Not Default
/etc/pm/(cnf|pw|sl) : Default

[/etc/rc.local]
hciconfig hci0 inqmode 0
exit 0

[/etc/modprobe.d]
iwlwifi.conf      : remove iwlwifi \
                    (/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
                    && /sbin/modprobe -r mac80211
mlx4.conf         : softdep mlx4_core post: mlx4_en


Kernel boot line ~~~~~~~~~~~~~~~~~~~

BOOT_IMAGE=/boot/vmlinuz-3.13.0-34-generic root=UUID=0277142b-c575-4175-ac75-acbec68aa5d0 ro quiet splash vt.handoff=7


dmesg ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

[    0.471681] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[    0.471959] audit: initializing netlink socket (disabled)
[    0.695827] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[   21.750127] wmi: Mapper loaded
[   21.836303] iwlwifi 0000:03:00.0: can't disable ASPM; OS doesn't have ASPM control
[   21.836360] iwlwifi 0000:03:00.0: irq 44 for MSI/MSI-X
[   22.167154] iwlwifi 0000:03:00.0: loaded firmware version 39.31.5.1 build 35138 op_mode iwldvm
[   22.181923] iwlwifi 0000:03:00.0: CONFIG_IWLWIFI_DEBUG disabled
[   22.181925] iwlwifi 0000:03:00.0: CONFIG_IWLWIFI_DEBUGFS enabled
[   22.181926] iwlwifi 0000:03:00.0: CONFIG_IWLWIFI_DEVICE_TRACING enabled
[   22.181927] iwlwifi 0000:03:00.0: Detected Intel(R) Centrino(R) Wireless-N 1000 BGN, REV=0x6C
[   22.181979] iwlwifi 0000:03:00.0: L1 Enabled; Disabling L0S
[   22.205457] ieee80211 phy0: Selected rate control algorithm 'iwl-agn-rs'
[   33.975484] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   37.211751] iwlwifi 0000:03:00.0: L1 Enabled; Disabling L0S
[   37.219235] iwlwifi 0000:03:00.0: Radio type=0x0-0x0-0x3
[   37.260641] iwlwifi 0000:03:00.0: L1 Enabled; Disabling L0S
[   37.268124] iwlwifi 0000:03:00.0: Radio type=0x0-0x0-0x3
[   37.309717] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   37.310006] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   38.191536] wlan0: authenticate with <MAC C-02 dave>
[   38.204373] wlan0: send auth to <MAC C-02 dave> (try 1/3)
[   38.206186] wlan0: authenticated

...

[ 2598.103741] wlan0: associate with <MAC C-02 dave> (try 1/3)
[ 2598.211912] wlan0: associate with <MAC C-02 dave> (try 2/3)
[ 2598.320041] wlan0: associate with <MAC C-02 dave> (try 3/3)
[ 2598.428179] wlan0: association with <MAC C-02 dave> timed out
[ 2608.815695] wlan0: authenticate with <MAC C-02 dave>
[ 2608.825611] wlan0: send auth to <MAC C-02 dave> (try 1/3)
[ 2608.827253] wlan0: authenticated
[ 2608.828631] wlan0: associate with <MAC C-02 dave> (try 1/3)
[ 2608.936796] wlan0: associate with <MAC C-02 dave> (try 2/3)
[ 2609.045145] wlan0: associate with <MAC C-02 dave> (try 3/3)
[ 2609.153256] wlan0: association with <MAC C-02 dave> timed out

	======== Done ========
```

I cannot think how the acer_wmi came to be present, but I've blacklisted it as you suggested.

---

### Post by varunendra on 2014-09-19
Isn't the screenshot a bit weird? It is showing WPA two times, then two radio buttons selected at the same time (radio buttons are supposed to be selectable only one at a time), and then there is an "Any WPA" button which I can't think to be anything else than WPA/WPA2 mixed mode.

Could you select "None", then only "WPA2" alone? Did you reboot the router after saving the change? Please do so to make sure the changes are applied properly.

If that is not changeable, or doesn't help, please try a driver parameter commonly needed with the iwlwifi driver in current kernel versions -
```
echo "options iwlwifi 11n_disable=8" | sudo tee -a /etc/modprobe.d/iwlwifi.conf
```
Reboot, and retry to connect. It is recommended to try this with WPA2-PSK/AES first. Revert to WPA/TKIP only if there seems to be no way out of it.

---

### Post by cov on 2014-09-19
Yes, it is odd.

After the settings were changed, saved and the router rebooted I was unable to connect.

Selecting "None" removes the second row of radio buttons.

I'll fiddle with drivers later: there are other people using the router.

---

### Post by varunendra on 2014-09-19
> **cov said:**
> Selecting "None" removes the second row of radio buttons.

Ah, now it does make sense. The 2nd row basically lets you choose 'Which' kind of WPA if you select 'WPA' in the 1st row, and you have chosen the recommended one.

Your card supports 'N' speeds upto 300 Mbps, certainly NOT too old to support WPA2/AES. Must be some other discrepancy causing the connection trouble with it.

---

