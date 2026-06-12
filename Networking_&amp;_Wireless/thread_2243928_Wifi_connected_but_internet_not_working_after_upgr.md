---
title: "Wifi connected but internet not working after upgrade to 14.04"
date: 2014-09-12
forum: Networking &amp; Wireless
---

### Post by mo14 on 2014-09-12
Hi there,

I finally upgraded my 12.04 to 14.04 last night and the upgrade was completed smoothly, until I realised that despite having the Wifi connected, the internet is not working. Everything was fine before the upgrade. I'm using Lenovo X230.

Below is the code generated using "wireless_script":

```


    ======== Wireless-Info START ========

System-Info ~~~~~~~~~~~~~~~~~~~~~~~~

m-ThinkPad-X230-Tablet 3.13.0-35-generic x86_64,  Ubuntu 14.04.1 LTS, trusty

CPU    : Intel(R) Core(TM) i7-3520M CPU @ 2.90GHz
Memory : 7684 MB
Uptime : 11:06:30 up  1:26,  2 users,  load average: 0.08, 0.09, 0.06


lspci ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

00:19.0 Ethernet controller [0200]: Intel Corporation 82579LM Gigabit Network Connection [8086:1502] (rev 04)
    Subsystem: Lenovo Device [17aa:21f3]
    Kernel driver in use: e1000e
--
03:00.0 Network controller [0280]: Intel Corporation Centrino Wireless-N 2200 [8086:0891] (rev c4)
    Subsystem: Intel Corporation Centrino Wireless-N 2200 BGN [8086:4222]
    Kernel driver in use: iwlwifi


lsusb ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Bus 002 Device 003: ID 056a:00e6 Wacom Co., Ltd 
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 005: ID 04f2:b2ea Chicony Electronics Co., Ltd Integrated Camera [ThinkPad]
Bus 001 Device 003: ID 147e:2020 Upek TouchChip Fingerprint Coprocessor (WBF advanced mode)
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 002: ID 04b3:310c IBM Corp. Wheel Mouse
Bus 003 Device 003: ID 05dc:a768 Lexar Media, Inc. 
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


PCMCIA Card Info ~~~~~~~~~~~~~~~~~~~



iwconfig ~~~~~~~~~~~~~~~~~~~~~~~~~~~

wlan0     IEEE 802.11bgn  ESSID:"SKY61376"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: <MAC C-01 SKY61376>   
          Bit Rate=1 Mb/s   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality=60/70  Signal level=-50 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:62   Missed beacon:0



rfkill ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

      Interface                    Soft blocked  Hard blocked
0: tpacpi_bluetooth_sw: Bluetooth      yes           no
2: phy0: Wireless LAN                  no            no


lsmod ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

iwldvm                232285  0 
mac80211              630653  1 iwldvm
iwlwifi               169932  1 iwldvm
cfg80211              484040  3 iwlwifi,mac80211,iwldvm
wmi                    19177  0 


module parameters ~~~~~~~~~~~~~~~~~~

cfg80211      (2): cfg80211_disable_40mhz_24ghz=N | ieee80211_regdom=00
iwlwifi      (11): 11n_disable=0 | amsdu_size_8K=0 | antenna_coupling=0 | bt_coex_active=Y | fw_restart=Y | led_mode=0 | nvm_file=(null) | power_level=0 | power_save=N | swcrypto=0 | wd_disable=1
mac80211      (5): beacon_loss_count=7 | ieee80211_default_rc_algo=minstrel_ht | max_nullfunc_tries=2 | max_probe_tries=5 | probe_wait_ms=500
wmi           (2): debug_dump_wdg=N | debug_event=N


nm-tool ~~~~~~~~~~~~~~~~~~~~~~~~~~~~

State: connected (global)
===================o=============o=========o=============o=========o===========o==============o===========
 Interface & ID    | Type        | Driver  | State       | Default | Speed     | Support      | HW Addr   
===================o=============o=========o=============o=========o===========o==============o===========
 wlan0  [SKY61376] | 802.11 WiFi | iwlwifi | connected   | yes     | 1 Mb/s    | WEP/WPA/WPA2 | <MAC wlan0>

    SKY99FF4:        Infra, <MAC C-03 SKY99FF4>, Freq 2437 MHz, Rate 54 Mb/s, Strength 54 WPA2
    EE-BrightBox-when2n: Infra, <MAC C-02 EE-BrightBox-when2n>, Freq 2412 MHz, Rate 54 Mb/s, Strength 30 WPA WPA2
    BTHub5-TZQ8:     Infra, <MAC C-04 BTHub5-TZQ8>, Freq 2462 MHz, Rate 54 Mb/s, Strength 20 WPA2
    BTWifi-X:        Infra, <MAC C-06 BTWifi-X>, Freq 2462 MHz, Rate 54 Mb/s, Strength 20 WPA WPA2 Enterprise
    HP855302:        Ad-Hoc, <MAC C-NA HP855302 1>, Freq 2457 MHz, Rate 11 Mb/s, Strength 32
    BTWifi-with-FON: Infra, <MAC C-05 BTWifi-with-FON>, Freq 2462 MHz, Rate 54 Mb/s, Strength 24
    test:            Ad-Hoc, <MAC C-NA test 1>, Freq 2412 MHz, Rate 54 Mb/s, Strength 49 WEP
    BTHub5-QKT8:     Infra, <MAC C-NA BTHub5-QKT8 1>, Freq 2437 MHz, Rate 54 Mb/s, Strength 24 WPA2
    SKYDFF07:        Infra, <MAC C-NA SKYDFF07 1>, Freq 2462 MHz, Rate 54 Mb/s, Strength 19 WPA2
    *SKY61376:       Infra, <MAC C-01 SKY61376>, Freq 2412 MHz, Rate 54 Mb/s, Strength 69 WPA
    BTWifi-X:        Infra, <MAC C-NA BTWifi-X 1>, Freq 2437 MHz, Rate 54 Mb/s, Strength 27 WPA WPA2 Enterprise
    BTWifi-with-FON: Infra, <MAC C-NA BTWifi-with-FON 1>, Freq 2437 MHz, Rate 54 Mb/s, Strength 27
    BTHub4-QZPQ:     Infra, <MAC C-NA BTHub4-QZPQ 1>, Freq 2437 MHz, Rate 54 Mb/s, Strength 15 WPA2

-------------------+-------------+---------+-------------+---------+-----------+--------------+-----------
 eth0              | Wired       | e1000e  | unavailable | no      |           |              | <MAC eth0>
-------------------+-------------+---------+-------------+---------+-----------+--------------+-----------


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

2WIRE411             : ssid=2WIRE411 | mac-address=<MAC wlan0> | ipv6=auto | ipv4=auto 
SKY61376             : ssid=SKY61376 | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 
WiFi_87              : ssid=WiFi_87 | mac-address=<MAC wlan0> | ipv6=auto | ipv4=auto 


interfaces ~~~~~~~~~~~~~~~~~~~~~~~~~

auto lo
iface lo inet loopback


resolv.conf ~~~~~~~~~~~~~~~~~~~~~~~~

nameserver 127.0.0.1
search home


Routes & Ping ~~~~~~~~~~~~~~~~~~~~~~

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface

--- 127.0.0.1 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 999ms
rtt min/avg/max/mdev = 0.031/0.036/0.041/0.005 ms


iw reg get ~~~~~~~~~~~~~~~~~~~~~~~~~

(Region : "en_GB.UTF-8")
country 00:
    (2402 - 2472 @ 40), (3, 20)
    (2457 - 2482 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (2474 - 2494 @ 20), (3, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
    (5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS


iwlist chan ~~~~~~~~~~~~~~~~~~~~~~~~

wlan0     13 channels in total; available frequencies :
          Channel 01 (2.412 GHz) - 13 (2.472 GHz)

          Current Frequency:2.412 GHz (Channel 1)


iwlist scan ~~~~~~~~~~~~~~~~~~~~~~~~

wlan0     Scan completed :
          Cell 01 - Address: <MAC C-01 SKY61376>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=54/70  Signal level=-56 dBm  
                    Encryption key:on
                    ESSID:"SKY61376"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000012d53af9dff
                    Extra: Last beacon: 88ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC C-02 EE-BrightBox-when2n>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=23/70  Signal level=-87 dBm  
                    Encryption key:on
                    ESSID:"EE-BrightBox-when2n"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 88ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: <MAC C-03 SKY99FF4>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=44/70  Signal level=-66 dBm  
                    Encryption key:on
                    ESSID:"SKY99FF4"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000006bb8fd4e1d
                    Extra: Last beacon: 88ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 04 - Address: <MAC C-04 BTHub5-TZQ8>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=26/70  Signal level=-84 dBm  
                    Encryption key:on
                    ESSID:"BTHub5-TZQ8"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000029bf063cb
                    Extra: Last beacon: 88ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 05 - Address: <MAC C-05 BTWifi-with-FON>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=26/70  Signal level=-84 dBm  
                    Encryption key:off
                    ESSID:"BTWifi-with-FON"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000029bf19d9c
                    Extra: Last beacon: 88ms ago
          Cell 06 - Address: <MAC C-06 BTWifi-X>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=24/70  Signal level=-86 dBm  
                    Encryption key:on
                    ESSID:"BTWifi-X"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000029bf14de1
                    Extra: Last beacon: 88ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : 802.1x
                       Preauthentication Supported
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : 802.1x


blacklist ~~~~~~~~~~~~~~~~~~~~~~~~~~

[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci

[/etc/modprobe.d/osspd.conf]
blacklist snd-pcm-oss
blacklist snd-mixer-oss
blacklist snd-seq-oss


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

[wmi]
filename:       /lib/modules/3.13.0-35-generic/kernel/drivers/platform/x86/wmi.ko
srcversion:     CED5410F008DC70DF5F064B
depends:        
parm:           debug_event:Log WMI Events [0/1] (bool)
parm:           debug_dump_wdg:Dump available WMI interfaces [0/1] (bool)


udev rules ~~~~~~~~~~~~~~~~~~~~~~~~~

# PCI device 0x8086:/sys/devices/pci0000:00/0000:00:19.0 (e1000e)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC eth0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

# PCI device 0x8086:/sys/devices/pci0000:00/0000:00:1c.1/0000:03:00.0 (iwlwifi)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC wlan0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"


Custom files/entries ~~~~~~~~~~~~~~~

/etc/modules        : Default
/etc/rc.local       : Default
/etc/modprobe.d     : Not Default
/etc/pm/(cnf|pw|sl) : Default

[/etc/modprobe.d]
ath9k.conf        : options ath9k nohwcrypt=1
iwlwifi.conf      : remove iwlwifi \
                    (/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
                    && /sbin/modprobe -r mac80211
mlx4.conf         : softdep mlx4_core post: mlx4_en


Kernel boot line ~~~~~~~~~~~~~~~~~~~

BOOT_IMAGE=/boot/vmlinuz-3.13.0-35-generic root=UUID=341a3bfb-bde6-458e-800f-065cb58e1efd ro quiet splash vt.handoff=7


dmesg ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

[    0.527870] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[    0.528108] audit: initializing netlink socket (disabled)
[    0.844421] wmi: Mapper loaded
[    6.661735] psmouse serio2: trackpoint: IBM TrackPoint firmware: 0x0e, buttons: 3/3
[   33.820178] iwlwifi 0000:03:00.0: can't disable ASPM; OS doesn't have ASPM control
[   33.820306] iwlwifi 0000:03:00.0: irq 46 for MSI/MSI-X
[   33.830867] thinkpad_acpi: http://ibm-acpi.sf.net/
[   34.194194] usb 1-1.4: Direct firmware load failed with error -2
[   34.194605] Bluetooth: can't load firmware, may not work correctly
[   34.248982] iwlwifi 0000:03:00.0: loaded firmware version 18.168.6.1 op_mode iwldvm
[   34.259064] iwlwifi 0000:03:00.0: CONFIG_IWLWIFI_DEBUG disabled
[   34.259067] iwlwifi 0000:03:00.0: CONFIG_IWLWIFI_DEBUGFS enabled
[   34.259069] iwlwifi 0000:03:00.0: CONFIG_IWLWIFI_DEVICE_TRACING enabled
[   34.259071] iwlwifi 0000:03:00.0: Detected Intel(R) Centrino(R) Wireless-N 2200 BGN, REV=0x104
[   34.259166] iwlwifi 0000:03:00.0: L1 Enabled; Disabling L0S
[   34.278561] ieee80211 phy0: Selected rate control algorithm 'iwl-agn-rs'
[   35.653199] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   37.668904] iwlwifi 0000:03:00.0: L1 Enabled; Disabling L0S
[   37.676578] iwlwifi 0000:03:00.0: Radio type=0x2-0x0-0x0
[   37.917864] iwlwifi 0000:03:00.0: L1 Enabled; Disabling L0S
[   37.925571] iwlwifi 0000:03:00.0: Radio type=0x2-0x0-0x0
[   37.996892] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   37.997103] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   38.551240] wlan0: authenticate with <MAC C-01 SKY61376>
[   38.554651] wlan0: send auth to <MAC C-01 SKY61376> (try 1/3)
[   38.557567] wlan0: authenticated
[   38.557643] iwlwifi 0000:03:00.0 wlan0: disabling HT/VHT due to WEP/TKIP use
[   38.557645] iwlwifi 0000:03:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[   38.557646] iwlwifi 0000:03:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[   38.557648] wlan0: waiting for beacon from <MAC C-01 SKY61376>
[   38.611361] wlan0: associate with <MAC C-01 SKY61376> (try 1/3)
[   38.613986] wlan0: RX AssocResp from <MAC C-01 SKY61376> (capab=0x411 status=0 aid=5)
[   38.617783] wlan0: associated
[   38.617807] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 4652.737977] wlan0: deauthenticating from <MAC C-01 SKY61376> by local choice (reason=3)
[ 4655.819855] iwlwifi 0000:03:00.0: L1 Enabled; Disabling L0S
[ 4655.827618] iwlwifi 0000:03:00.0: Radio type=0x2-0x0-0x0
[ 4655.895971] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 4656.899475] wlan0: authenticate with <MAC C-01 SKY61376>
[ 4656.904835] wlan0: send auth to <MAC C-01 SKY61376> (try 1/3)
[ 4656.909630] wlan0: authenticated
[ 4656.909740] iwlwifi 0000:03:00.0 wlan0: disabling HT/VHT due to WEP/TKIP use
[ 4656.909743] iwlwifi 0000:03:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[ 4656.909745] iwlwifi 0000:03:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[ 4656.911262] wlan0: associate with <MAC C-01 SKY61376> (try 1/3)
[ 4656.913657] wlan0: RX AssocResp from <MAC C-01 SKY61376> (capab=0x411 status=0 aid=5)
[ 4656.915773] wlan0: associated
[ 4656.915792] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 4656.934659] wlan0: deauthenticating from <MAC C-01 SKY61376> by local choice (reason=2)
[ 4656.940374] wlan0: authenticate with <MAC C-01 SKY61376>
[ 4656.943128] wlan0: send auth to <MAC C-01 SKY61376> (try 1/3)
[ 4656.945963] wlan0: authenticated
[ 4656.946135] iwlwifi 0000:03:00.0 wlan0: disabling HT/VHT due to WEP/TKIP use
[ 4656.946140] iwlwifi 0000:03:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[ 4656.946143] iwlwifi 0000:03:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[ 4656.947463] wlan0: associate with <MAC C-01 SKY61376> (try 1/3)
[ 4656.949927] wlan0: RX AssocResp from <MAC C-01 SKY61376> (capab=0x411 status=0 aid=5)
[ 4656.952217] wlan0: associated
[ 4666.406294] wlan0: deauthenticating from <MAC C-01 SKY61376> by local choice (reason=3)
[ 4686.277404] wlan0: authenticate with <MAC C-01 SKY61376>
[ 4686.283808] wlan0: send auth to <MAC C-01 SKY61376> (try 1/3)
[ 4686.286648] wlan0: authenticated
[ 4686.286857] iwlwifi 0000:03:00.0 wlan0: disabling HT/VHT due to WEP/TKIP use
[ 4686.286865] iwlwifi 0000:03:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[ 4686.286870] iwlwifi 0000:03:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[ 4686.287064] wlan0: associate with <MAC C-01 SKY61376> (try 1/3)
[ 4686.289484] wlan0: RX AssocResp from <MAC C-01 SKY61376> (capab=0x411 status=0 aid=5)
[ 4686.291495] wlan0: associated
[ 4731.735368] wlan0: deauthenticating from <MAC C-01 SKY61376> by local choice (reason=3)
[ 4793.550502] iwlwifi 0000:03:00.0: L1 Enabled; Disabling L0S
[ 4793.558207] iwlwifi 0000:03:00.0: Radio type=0x2-0x0-0x0
[ 4793.625167] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 4794.185073] wlan0: authenticate with <MAC C-01 SKY61376>
[ 4794.188393] wlan0: send auth to <MAC C-01 SKY61376> (try 1/3)
[ 4794.191176] wlan0: authenticated
[ 4794.191257] iwlwifi 0000:03:00.0 wlan0: disabling HT/VHT due to WEP/TKIP use
[ 4794.191260] iwlwifi 0000:03:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[ 4794.191262] iwlwifi 0000:03:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[ 4794.191336] wlan0: associate with <MAC C-01 SKY61376> (try 1/3)
[ 4794.194950] wlan0: RX AssocResp from <MAC C-01 SKY61376> (capab=0x411 status=0 aid=5)
[ 4794.203925] wlan0: associated
[ 4794.203944] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 4802.326805] wlan0: deauthenticating from <MAC C-01 SKY61376> by local choice (reason=3)
[ 4823.310522] wlan0: authenticate with <MAC C-01 SKY61376>
[ 4823.313912] wlan0: send auth to <MAC C-01 SKY61376> (try 1/3)
[ 4823.316731] wlan0: authenticated
[ 4823.316892] iwlwifi 0000:03:00.0 wlan0: disabling HT/VHT due to WEP/TKIP use
[ 4823.316899] iwlwifi 0000:03:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[ 4823.316904] iwlwifi 0000:03:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[ 4823.319046] wlan0: associate with <MAC C-01 SKY61376> (try 1/3)
[ 4823.321463] wlan0: RX AssocResp from <MAC C-01 SKY61376> (capab=0x411 status=0 aid=5)
[ 4823.323487] wlan0: associated

    ======== Done ========

```

I'd appreciate any advice to help me reconnect my machine to the internet.

Thank you

---

### Post by jeremy31 on 2014-09-12
Welcome to the forum.  First thing to do is access your routers wifi settings and set it to use WPA2-AES encryption- if you look at the end of your wireless-info it shows HT/VHT being disabled due to WEP/TKIP

---

### Post by mo14 on 2014-09-12
Thanks for the reply. I don't have access to the router as it's managed by someone else. 
Is there anything I can do on my machine instead? 

Thanks

---

### Post by jeremy31 on 2014-09-12
can you ping 8.8.4.4```
ping 8.8.4.4
``` or ```
ping google.com
```

---

### Post by mo14 on 2014-09-12
Here is the output to ping 8.8.4.4:

I stopped it after a while by ctrl+c

```

m@m-ThinkPad-X230-Tablet:~$ ping 8.8.4.4
PING 8.8.4.4 (8.8.4.4) 56(84) bytes of data.
64 bytes from 8.8.4.4: icmp_seq=1 ttl=50 time=44.0 ms
64 bytes from 8.8.4.4: icmp_seq=2 ttl=50 time=42.6 ms
64 bytes from 8.8.4.4: icmp_seq=3 ttl=50 time=42.0 ms
64 bytes from 8.8.4.4: icmp_seq=4 ttl=50 time=41.7 ms
64 bytes from 8.8.4.4: icmp_seq=5 ttl=50 time=44.3 ms
64 bytes from 8.8.4.4: icmp_seq=6 ttl=50 time=41.3 ms
64 bytes from 8.8.4.4: icmp_seq=7 ttl=50 time=41.8 ms
64 bytes from 8.8.4.4: icmp_seq=8 ttl=50 time=42.1 ms
64 bytes from 8.8.4.4: icmp_seq=9 ttl=50 time=41.6 ms
64 bytes from 8.8.4.4: icmp_seq=10 ttl=50 time=41.0 ms
64 bytes from 8.8.4.4: icmp_seq=11 ttl=50 time=42.0 ms
64 bytes from 8.8.4.4: icmp_seq=12 ttl=50 time=41.8 ms
64 bytes from 8.8.4.4: icmp_seq=13 ttl=50 time=40.9 ms
64 bytes from 8.8.4.4: icmp_seq=14 ttl=50 time=41.6 ms
64 bytes from 8.8.4.4: icmp_seq=15 ttl=50 time=42.3 ms
64 bytes from 8.8.4.4: icmp_seq=16 ttl=50 time=42.4 ms
64 bytes from 8.8.4.4: icmp_seq=17 ttl=50 time=41.9 ms
64 bytes from 8.8.4.4: icmp_seq=18 ttl=50 time=47.6 ms
64 bytes from 8.8.4.4: icmp_seq=19 ttl=50 time=41.0 ms
64 bytes from 8.8.4.4: icmp_seq=20 ttl=50 time=40.8 ms
64 bytes from 8.8.4.4: icmp_seq=21 ttl=50 time=42.2 ms
64 bytes from 8.8.4.4: icmp_seq=22 ttl=50 time=40.8 ms
64 bytes from 8.8.4.4: icmp_seq=23 ttl=50 time=42.3 ms
64 bytes from 8.8.4.4: icmp_seq=24 ttl=50 time=41.8 ms
64 bytes from 8.8.4.4: icmp_seq=25 ttl=50 time=40.7 ms
64 bytes from 8.8.4.4: icmp_seq=26 ttl=50 time=42.3 ms
64 bytes from 8.8.4.4: icmp_seq=27 ttl=50 time=41.6 ms
64 bytes from 8.8.4.4: icmp_seq=28 ttl=50 time=41.7 ms
64 bytes from 8.8.4.4: icmp_seq=29 ttl=50 time=40.5 ms
64 bytes from 8.8.4.4: icmp_seq=30 ttl=50 time=42.6 ms
64 bytes from 8.8.4.4: icmp_seq=31 ttl=50 time=41.6 ms
64 bytes from 8.8.4.4: icmp_seq=32 ttl=50 time=40.9 ms
64 bytes from 8.8.4.4: icmp_seq=33 ttl=50 time=41.8 ms
64 bytes from 8.8.4.4: icmp_seq=34 ttl=50 time=41.8 ms
64 bytes from 8.8.4.4: icmp_seq=35 ttl=50 time=41.1 ms
^C
--- 8.8.4.4 ping statistics ---
35 packets transmitted, 35 received, 0% packet loss, time 34048ms
rtt min/avg/max/mdev = 40.578/42.000/47.601/1.254 ms


```

and here is the output to ping google.com

```

m@m-ThinkPad-X230-Tablet:~$ ping google.com
ping: unknown host google.com

```

thanks

---

### Post by jeremy31 on 2014-09-12
Go into network manager and edit your connection, IPv4 where you should be able to set additional DNS. Add ```
8.8.8.8, 8.8.4.4
```   You may have to disconnect/connect or possibly reboot for it to work.  Then try ping google.com again, hopefully it works and you will have internet access

---

### Post by mo14 on 2014-09-12
Thanks Jeremy.
I've added the additional DNS servers as suggested (pls see the screenshot), then disconnected and connected several times, but no result. I then rebooted, but still I get the same message when I ping google.com [ping: unknown host google.com]

Any idea what I might have done wrong?
[ATTACH=CONFIG]256395[/ATTACH]

---

### Post by jesse111 on 2014-09-12
Since you can ping an IP adres but can't ping a hostname there is going something wrong with your DNS resolving. Which DNS Servers are you using now?

Also you can try to clear your DNS

```
[FONT=Ubuntu Mono]sudo /etc/init.d/dns-clean restart[/FONT]
```

Followed by

```
[FONT=Ubuntu Mono]sudo /etc/init.d/networking force-reload[/FONT]
```

---

### Post by mo14 on 2014-09-12
> **jesse111 said:**
> Since you can ping an IP adres but can't ping a hostname there is going something wrong with your DNS resolving. Which DNS Servers are you using now?

That's what I think too. I've added the additional DNS suggested by Jermey, but still no result.

I've tried to clear the DNS as you recommended; disconnected/connected and it didn't work. I also rebooted, but still cannot ping any external address.

Any other idea what might be going wrong?

---

### Post by jeremy31 on 2014-09-12
Lets run the script again ```
./wireless_script
```

---

### Post by mo14 on 2014-09-12
Please find below

```


    ======== Wireless-Info START ========

System-Info ~~~~~~~~~~~~~~~~~~~~~~~~

m-ThinkPad-X230-Tablet 3.13.0-35-generic x86_64,  Ubuntu 14.04.1 LTS, trusty

CPU    : Intel(R) Core(TM) i7-3520M CPU @ 2.90GHz
Memory : 7684 MB
Uptime : 15:16:59 up 1 min,  2 users,  load average: 0.89, 0.43, 0.16


lspci ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

00:19.0 Ethernet controller [0200]: Intel Corporation 82579LM Gigabit Network Connection [8086:1502] (rev 04)
    Subsystem: Lenovo Device [17aa:21f3]
    Kernel driver in use: e1000e
--
03:00.0 Network controller [0280]: Intel Corporation Centrino Wireless-N 2200 [8086:0891] (rev c4)
    Subsystem: Intel Corporation Centrino Wireless-N 2200 BGN [8086:4222]
    Kernel driver in use: iwlwifi


lsusb ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Bus 002 Device 003: ID 056a:00e6 Wacom Co., Ltd 
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 004: ID 04f2:b2ea Chicony Electronics Co., Ltd Integrated Camera [ThinkPad]
Bus 001 Device 003: ID 147e:2020 Upek TouchChip Fingerprint Coprocessor (WBF advanced mode)
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 002: ID 05dc:a768 Lexar Media, Inc. 
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


PCMCIA Card Info ~~~~~~~~~~~~~~~~~~~



iwconfig ~~~~~~~~~~~~~~~~~~~~~~~~~~~

wlan0     IEEE 802.11bgn  ESSID:"SKY61376"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: <MAC C-01 SKY61376>   
          Bit Rate=1 Mb/s   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality=52/70  Signal level=-58 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:1  Invalid misc:51   Missed beacon:0



rfkill ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

      Interface                    Soft blocked  Hard blocked
0: tpacpi_bluetooth_sw: Bluetooth      yes           no
1: phy0: Wireless LAN                  no            no


lsmod ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

iwldvm                232285  0 
mac80211              630653  1 iwldvm
iwlwifi               169932  1 iwldvm
cfg80211              484040  3 iwlwifi,mac80211,iwldvm
wmi                    19177  0 


module parameters ~~~~~~~~~~~~~~~~~~

cfg80211      (2): cfg80211_disable_40mhz_24ghz=N | ieee80211_regdom=00
iwlwifi      (11): 11n_disable=0 | amsdu_size_8K=0 | antenna_coupling=0 | bt_coex_active=Y | fw_restart=Y | led_mode=0 | nvm_file=(null) | power_level=0 | power_save=N | swcrypto=0 | wd_disable=1
mac80211      (5): beacon_loss_count=7 | ieee80211_default_rc_algo=minstrel_ht | max_nullfunc_tries=2 | max_probe_tries=5 | probe_wait_ms=500
wmi           (2): debug_dump_wdg=N | debug_event=N


nm-tool ~~~~~~~~~~~~~~~~~~~~~~~~~~~~

State: connected (global)
===================o=============o=========o=============o=========o===========o==============o===========
 Interface & ID    | Type        | Driver  | State       | Default | Speed     | Support      | HW Addr   
===================o=============o=========o=============o=========o===========o==============o===========
 wlan0  [SKY61376] | 802.11 WiFi | iwlwifi | connected   | yes     | 1 Mb/s    | WEP/WPA/WPA2 | <MAC wlan0>

    SKY99FF4:        Infra, <MAC C-02 SKY99FF4>, Freq 2437 MHz, Rate 54 Mb/s, Strength 52 WPA2
    BTWifi-X:        Infra, <MAC C-04 BTWifi-X>, Freq 2462 MHz, Rate 54 Mb/s, Strength 30 WPA WPA2 Enterprise
    EE-BrightBox-when2n: Infra, <MAC C-07 EE-BrightBox-when2n>, Freq 2412 MHz, Rate 54 Mb/s, Strength 29 WPA WPA2
    BTHub5-TZQ8:     Infra, <MAC C-05 BTHub5-TZQ8>, Freq 2462 MHz, Rate 54 Mb/s, Strength 22 WPA2
    HP855302:        Ad-Hoc, <MAC C-03 HP855302>, Freq 2457 MHz, Rate 11 Mb/s, Strength 40
    BTWifi-with-FON: Infra, <MAC C-06 BTWifi-with-FON>, Freq 2462 MHz, Rate 54 Mb/s, Strength 24
    *SKY61376:       Infra, <MAC C-01 SKY61376>, Freq 2412 MHz, Rate 54 Mb/s, Strength 62 WPA
    SKYDFF07:        Infra, <MAC C-08 SKYDFF07>, Freq 2462 MHz, Rate 54 Mb/s, Strength 17 WPA2

-------------------+-------------+---------+-------------+---------+-----------+--------------+-----------
 eth0              | Wired       | e1000e  | unavailable | no      |           |              | <MAC eth0>
-------------------+-------------+---------+-------------+---------+-----------+--------------+-----------


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

2WIRE411             : ssid=2WIRE411 | mac-address=<MAC wlan0> | ipv6=auto | ipv4=auto 
SKY61376             : ssid=SKY61376 | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 
WiFi_87              : ssid=WiFi_87 | mac-address=<MAC wlan0> | ipv6=auto | ipv4=auto 


interfaces ~~~~~~~~~~~~~~~~~~~~~~~~~

auto lo
iface lo inet loopback


resolv.conf ~~~~~~~~~~~~~~~~~~~~~~~~

nameserver 127.0.0.1
search home


Routes & Ping ~~~~~~~~~~~~~~~~~~~~~~

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface

--- 127.0.0.1 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 999ms
rtt min/avg/max/mdev = 0.016/0.019/0.023/0.005 ms


iw reg get ~~~~~~~~~~~~~~~~~~~~~~~~~

(Region : "en_GB.UTF-8")
country 00:
    (2402 - 2472 @ 40), (3, 20)
    (2457 - 2482 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (2474 - 2494 @ 20), (3, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
    (5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS


iwlist chan ~~~~~~~~~~~~~~~~~~~~~~~~

wlan0     13 channels in total; available frequencies :
          Channel 01 (2.412 GHz) - 13 (2.472 GHz)

          Current Frequency:2.412 GHz (Channel 1)


iwlist scan ~~~~~~~~~~~~~~~~~~~~~~~~

wlan0     Scan completed :
          Cell 01 - Address: <MAC C-01 SKY61376>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=51/70  Signal level=-59 dBm  
                    Encryption key:on
                    ESSID:"SKY61376"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000130d37cf54d
                    Extra: Last beacon: 60ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC C-02 SKY99FF4>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=29/70  Signal level=-81 dBm  
                    Encryption key:on
                    ESSID:"SKY99FF4"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000006f38d108e9
                    Extra: Last beacon: 60ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: <MAC C-03 HP855302>
                    Channel:10
                    Frequency:2.457 GHz (Channel 10)
                    Quality=34/70  Signal level=-76 dBm  
                    Encryption key:off
                    ESSID:"HP855302"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Mode:Ad-Hoc
                    Extra:tsf=0000000559bc8561
                    Extra: Last beacon: 60ms ago
          Cell 04 - Address: <MAC C-04 BTWifi-X>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=24/70  Signal level=-86 dBm  
                    Encryption key:on
                    ESSID:"BTWifi-X"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000061bc4d374
                    Extra: Last beacon: 60ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : 802.1x
                       Preauthentication Supported
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : 802.1x
          Cell 05 - Address: <MAC C-05 BTHub5-TZQ8>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=21/70  Signal level=-89 dBm  
                    Encryption key:on
                    ESSID:"BTHub5-TZQ8"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000061bc3ea1a
                    Extra: Last beacon: 60ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 06 - Address: <MAC C-06 BTWifi-with-FON>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=24/70  Signal level=-86 dBm  
                    Encryption key:off
                    ESSID:"BTWifi-with-FON"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000061bc52394
                    Extra: Last beacon: 60ms ago
          Cell 07 - Address: <MAC C-07 EE-BrightBox-when2n>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=28/70  Signal level=-82 dBm  
                    Encryption key:on
                    ESSID:"EE-BrightBox-when2n"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 60ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 08 - Address: <MAC C-08 SKYDFF07>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=23/70  Signal level=-87 dBm  
                    Encryption key:on
                    ESSID:"SKYDFF07"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000000a0b5a112
                    Extra: Last beacon: 60ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK


blacklist ~~~~~~~~~~~~~~~~~~~~~~~~~~

[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci

[/etc/modprobe.d/osspd.conf]
blacklist snd-pcm-oss
blacklist snd-mixer-oss
blacklist snd-seq-oss


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

[wmi]
filename:       /lib/modules/3.13.0-35-generic/kernel/drivers/platform/x86/wmi.ko
srcversion:     CED5410F008DC70DF5F064B
depends:        
parm:           debug_event:Log WMI Events [0/1] (bool)
parm:           debug_dump_wdg:Dump available WMI interfaces [0/1] (bool)


udev rules ~~~~~~~~~~~~~~~~~~~~~~~~~

# PCI device 0x8086:/sys/devices/pci0000:00/0000:00:19.0 (e1000e)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC eth0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

# PCI device 0x8086:/sys/devices/pci0000:00/0000:00:1c.1/0000:03:00.0 (iwlwifi)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC wlan0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"


Custom files/entries ~~~~~~~~~~~~~~~

/etc/modules        : Default
/etc/rc.local       : Default
/etc/modprobe.d     : Not Default
/etc/pm/(cnf|pw|sl) : Default

[/etc/modprobe.d]
ath9k.conf        : options ath9k nohwcrypt=1
iwlwifi.conf      : remove iwlwifi \
                    (/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
                    && /sbin/modprobe -r mac80211
mlx4.conf         : softdep mlx4_core post: mlx4_en


Kernel boot line ~~~~~~~~~~~~~~~~~~~

BOOT_IMAGE=/boot/vmlinuz-3.13.0-35-generic root=UUID=341a3bfb-bde6-458e-800f-065cb58e1efd ro quiet splash vt.handoff=7


dmesg ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

[    0.527339] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[    0.527598] audit: initializing netlink socket (disabled)
[    0.892215] wmi: Mapper loaded
[    6.790994] psmouse serio2: trackpoint: IBM TrackPoint firmware: 0x0e, buttons: 3/3
[   35.970812] thinkpad_acpi: http://ibm-acpi.sf.net/
[   35.974925] iwlwifi 0000:03:00.0: can't disable ASPM; OS doesn't have ASPM control
[   35.975116] iwlwifi 0000:03:00.0: irq 45 for MSI/MSI-X
[   36.299631] iwlwifi 0000:03:00.0: loaded firmware version 18.168.6.1 op_mode iwldvm
[   36.309364] iwlwifi 0000:03:00.0: CONFIG_IWLWIFI_DEBUG disabled
[   36.309366] iwlwifi 0000:03:00.0: CONFIG_IWLWIFI_DEBUGFS enabled
[   36.309367] iwlwifi 0000:03:00.0: CONFIG_IWLWIFI_DEVICE_TRACING enabled
[   36.309368] iwlwifi 0000:03:00.0: Detected Intel(R) Centrino(R) Wireless-N 2200 BGN, REV=0x104
[   36.309474] iwlwifi 0000:03:00.0: L1 Enabled; Disabling L0S
[   36.331009] ieee80211 phy0: Selected rate control algorithm 'iwl-agn-rs'
[   36.773699] usb 1-1.4: Direct firmware load failed with error -2
[   36.774310] Bluetooth: can't load firmware, may not work correctly
[   37.512046] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   40.157647] iwlwifi 0000:03:00.0: L1 Enabled; Disabling L0S
[   40.165757] iwlwifi 0000:03:00.0: Radio type=0x2-0x0-0x0
[   40.406796] iwlwifi 0000:03:00.0: L1 Enabled; Disabling L0S
[   40.414514] iwlwifi 0000:03:00.0: Radio type=0x2-0x0-0x0
[   40.481957] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   40.482164] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   41.124414] wlan0: authenticate with <MAC C-01 SKY61376>
[   41.127525] wlan0: send auth to <MAC C-01 SKY61376> (try 1/3)
[   41.130357] wlan0: authenticated
[   41.130445] iwlwifi 0000:03:00.0 wlan0: disabling HT/VHT due to WEP/TKIP use
[   41.130447] iwlwifi 0000:03:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[   41.130448] iwlwifi 0000:03:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[   41.130450] wlan0: waiting for beacon from <MAC C-01 SKY61376>
[   41.171893] wlan0: associate with <MAC C-01 SKY61376> (try 1/3)
[   41.174540] wlan0: RX AssocResp from <MAC C-01 SKY61376> (capab=0x411 status=0 aid=8)
[   41.177280] wlan0: associated
[   41.177316] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready

    ======== Done ========

```

Thanks

---

### Post by jesse111 on 2014-09-12
The only thing that I can think of is disabling all the automated services, so connect manually to your gateway. That way you are ensured of a correct config. So in network settings go to IPv4 settings and choose the Method Manual.

Then click add, type 192.168.0.4 at the address, 255.255.255.0 at the Netmask and 192.168.0.1 at the Gateway. Still keep the DNS server 8.8.8.8 and 8.8.4.4.

After that go to IPv6 and choose ignore at Method.

---

### Post by mo14 on 2014-09-12
I tried that, but unfortunately it didn't work.
I disconnected/connected, rebooted the machine, but no luck.

If there is no hope, I might have to backup and install a fresh copy. 

But I'll wait to see if you have any other advice before I proceed.

thanks

---

### Post by jeremy31 on 2014-09-12
It might be worth looking at some of the syslog ```
cat /var/log/syslog | grep -i dns
``` ```
cat /var/log/syslog | grep -i dhcp
```

---

### Post by mo14 on 2014-09-12
I've included both, DNS and DHCP related logs

```
Sep 12 01:23:01 m-ThinkPad-X230-Tablet avahi-daemon[10128]: Joining mDNS multicast group on interface wlan0.IPv6 with address 
....
```

```
Sep 12 01:23:48 m-ThinkPad-X230-Tablet kernel: [44238.488463] type=1400 audit(1410477828.360:41): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=18342 comm="apparmor_parser"
.....

```


Thank you

---

### Post by mo14 on 2014-09-12
Thanks Jeremy and Jesse!
I've given up hope and installed a fresh copy of Ububtu 14.04. This upgrade was a nightmare but hopefully the fresh installation makes up for the unknown problem.

---

### Post by jeremy31 on 2014-09-12
If the issue remains, try changing the IPv6 to ignore in network manager

---

### Post by mo14 on 2014-09-12
I had tried changing IPv6 to ignore, but it didn't solve the problem.
While the mystry remains in the upgraded version, now thing are OK in the fresh installation. Thanks again

---

### Post by hesseny20002 on 2014-09-13
check this link maybe find something helpful ....
[http://ubuntuforums.org/showthread.php?t=2082305](http://ubuntuforums.org/showthread.php?t=2082305)

---

