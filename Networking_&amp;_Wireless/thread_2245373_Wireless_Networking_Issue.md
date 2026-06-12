---
title: "Wireless Networking Issue"
date: 2014-09-23
forum: Networking &amp; Wireless
---

### Post by newholm1 on 2014-09-23
Hi. I've just got Ubuntu Studio 14.04 up and running on my Lenovo E540 laptop. Most features are working fine, but the Wireless is an issue. It connects to my network, but seems to be slow, and after a while it disconnects. It asks me for the wireless password quite often, and this seems to be in conjunction with the disconnection. Switching the wireless on and off on the laptop will make it reconnect, but it is then extremely sluggish and after a while I have no option but to restart the laptop. My ethernet connection is fine. My wireless card is an [COLOR=#545454][FONT=arial]Intel® Dual Band Wireless-[/FONT][/COLOR][COLOR=#545454][FONT=arial]**AC 7260**[/FONT][/COLOR][COLOR=#545454][FONT=arial] Wi-Fi and Bluetooth. [/FONT][/COLOR]Please help me!

---

### Post by varunendra on 2014-09-23
Please follow the instructions in this post to download and run 'wireless_script' (experimental version) and post back the report it generates : [http://ubuntuforums.org/showpost.php?p=13024222](http://ubuntuforums.org/showpost.php?p=13024222)

While posting the outputs, please use '**Code**' tags. It preserves the output's formatting and makes the post cleaner, compact and more readable. To see a quick 'HowTo' with screenshots, please follow the "Use Code Tags" link in my signature.

---

### Post by slickymaster on 2014-09-23
*Moved to the ***Networking & Wireless*** sub-forum*

---

### Post by newholm1 on 2014-09-23
Hello. Here is the code: 
```


    ======== Wireless-Info START ========

System-Info ~~~~~~~~~~~~~~~~~~~~~~~~

Leonardo-14000 3.13.0-35-lowlatency x86_64,  Ubuntu 14.04.1 LTS, trusty

CPU    : Intel(R) Core(TM) i3-4000M CPU @ 2.40GHz
Memory : 3671 MB
Uptime : 18:55:53 up 6 min,  2 users,  load average: 0.12, 0.15, 0.08


lspci ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 10)
    Subsystem: Lenovo Device [17aa:5028]
    Kernel driver in use: r8169
04:00.0 Network controller [0280]: Intel Corporation Wireless 7260 [8086:08b2] (rev 83)
    Subsystem: Intel Corporation Dual Band Wireless-AC 7260 [8086:4270]
    Kernel driver in use: iwlwifi


lsusb ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Bus 002 Device 002: ID 8087:8000 Intel Corp. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:8008 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 002: ID 8087:07dc Intel Corp. 
Bus 003 Device 003: ID 5986:0397 Acer, Inc 
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


PCMCIA Card Info ~~~~~~~~~~~~~~~~~~~



iwconfig ~~~~~~~~~~~~~~~~~~~~~~~~~~~

wlan0     IEEE 802.11abgn  ESSID:"BTHub3-P4Z8"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: <MAC C-01 BTHub3-P4Z8>   
          Bit Rate=144.4 Mb/s   Tx-Power=16 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=70/70  Signal level=-32 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:3   Missed beacon:0



rfkill ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

      Interface                    Soft blocked  Hard blocked
0: hci0: Bluetooth                     no            no
1: tpacpi_bluetooth_sw: Bluetooth      no            no
2: phy0: Wireless LAN                  no            no


lsmod ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

iwlmvm                189729  0 
mac80211              638933  1 iwlmvm
iwlwifi               174028  1 iwlmvm
cfg80211              496328  3 iwlwifi,mac80211,iwlmvm
wmi                    19177  0 


module parameters ~~~~~~~~~~~~~~~~~~

cfg80211      (2): cfg80211_disable_40mhz_24ghz=N | ieee80211_regdom=00
iwlmvm        (2): init_dbg=N | power_scheme=2
iwlwifi      (11): 11n_disable=0 | amsdu_size_8K=0 | antenna_coupling=0 | bt_coex_active=Y | fw_restart=Y | led_mode=0 | nvm_file=(null) | power_level=0 | power_save=N | swcrypto=0 | wd_disable=1
mac80211      (5): beacon_loss_count=7 | ieee80211_default_rc_algo=minstrel_ht | max_nullfunc_tries=2 | max_probe_tries=5 | probe_wait_ms=500
wmi           (2): debug_dump_wdg=N | debug_event=N


nm-tool ~~~~~~~~~~~~~~~~~~~~~~~~~~~~

State: connected (global)
======================o=============o=========o==============o=========o===========o==============o===========
 Interface & ID       | Type        | Driver  | State        | Default | Speed     | Support      | HW Addr   
======================o=============o=========o==============o=========o===========o==============o===========
 wlan0  [BTHub3-P4Z8] | 802.11 WiFi | iwlwifi | connected    | yes     | 144 Mb/s  | WEP/WPA/WPA2 | <MAC wlan0>

    SKY1704C:        Infra, <MAC C-02 SKY1704C>, Freq 2412 MHz, Rate 54 Mb/s, Strength 55 WPA2
    PlusnetWireless0D3F70: Infra, <MAC C-03 PlusnetWireless0D3F70>, Freq 2437 MHz, Rate 54 Mb/s, Strength 37 WPA WPA2
    TALKTALK-DF2498: Infra, <MAC C-05 TALKTALK-DF2498>, Freq 2462 MHz, Rate 54 Mb/s, Strength 32 WPA WPA2
    SKY6C89E:        Infra, <MAC C-NA SKY6C89E 1>, Freq 2467 MHz, Rate 54 Mb/s, Strength 32 WPA2
    TP-LINK_9F1F0E:  Infra, <MAC C-NA TP-LINK_9F1F0E 1>, Freq 2412 MHz, Rate 54 Mb/s, Strength 30 WPA WPA2
    BTHub4-86PR:     Infra, <MAC C-NA BTHub4-86PR 1>, Freq 2462 MHz, Rate 54 Mb/s, Strength 20 WPA WPA2
    BTWiFi:          Infra, <MAC C-NA BTWiFi 1>, Freq 2412 MHz, Rate 54 Mb/s, Strength 22
    BTWiFi-with-FON: Infra, <MAC C-NA BTWiFi-with-FON 1>, Freq 2412 MHz, Rate 54 Mb/s, Strength 20
    *BTHub3-P4Z8:    Infra, <MAC C-01 BTHub3-P4Z8>, Freq 2412 MHz, Rate 54 Mb/s, Strength 66 WPA WPA2
    TALKTALK-10DE4D: Infra, <MAC C-06 TALKTALK-10DE4D>, Freq 2462 MHz, Rate 54 Mb/s, Strength 17 WPA WPA2
    BTWiFi-with-FON: Infra, <MAC C-04 BTWiFi-with-FON>, Freq 2412 MHz, Rate 54 Mb/s, Strength 100
    TP-LINK_804E3F:  Infra, <MAC C-NA TP-LINK_804E3F 1>, Freq 2412 MHz, Rate 54 Mb/s, Strength 29 WPA WPA2
    PlusnetWirelessB1E21D: Infra, <MAC C-NA PlusnetWirelessB1E21D 1>, Freq 2437 MHz, Rate 54 Mb/s, Strength 27 WPA WPA2
    BTWifi-with-FON: Infra, <MAC C-07 BTWifi-with-FON>, Freq 2462 MHz, Rate 54 Mb/s, Strength 20
    BTHub3-5RW6:     Infra, <MAC C-NA BTHub3-5RW6 1>, Freq 2437 MHz, Rate 54 Mb/s, Strength 32 WPA WPA2
    BTWifi-X:        Infra, <MAC C-NA BTWifi-X 1>, Freq 2462 MHz, Rate 54 Mb/s, Strength 24 WPA WPA2 Enterprise
    TALKTALK-D3B440: Infra, <MAC C-NA TALKTALK-D3B440 1>, Freq 2452 MHz, Rate 54 Mb/s, Strength 22 WPA WPA2
    BTHub3-6WSS:     Infra, <MAC C-NA BTHub3-6WSS 1>, Freq 2412 MHz, Rate 54 Mb/s, Strength 19 WPA WPA2

    Address:         192.168.1.77
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.254
    DNS:             192.168.1.254
----------------------+-------------+---------+--------------+---------+-----------+--------------+-----------
 eth0                 | Wired       | r8169   | disconnected | no      | 100 Mb/s  |              | <MAC eth0>
----------------------+-------------+---------+--------------+---------+-----------+--------------+-----------


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

BTHub3-P4Z8          : ssid=BTHub3-P4Z8 | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 


interfaces ~~~~~~~~~~~~~~~~~~~~~~~~~

# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback

resolv.conf ~~~~~~~~~~~~~~~~~~~~~~~~

nameserver 127.0.1.1
search home


Routes & Ping ~~~~~~~~~~~~~~~~~~~~~~

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.254   0.0.0.0         UG    0      0        0 wlan0
192.168.1.0     0.0.0.0         255.255.255.0   U     9      0        0 wlan0

--- 192.168.1.254 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 1001ms
rtt min/avg/max/mdev = 3.152/14.512/25.873/11.361 ms

--- 127.0.1.1 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 999ms
rtt min/avg/max/mdev = 0.033/0.039/0.046/0.009 ms


iw reg get ~~~~~~~~~~~~~~~~~~~~~~~~~

(Region : "en_GB.UTF-8")
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
          Cell 01 - Address: <MAC C-01 BTHub3-P4Z8>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=70/70  Signal level=-33 dBm  
                    Encryption key:on
                    ESSID:"BTHub3-P4Z8"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000105386e1f73
                    Extra: Last beacon: 2ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC C-02 SKY1704C>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=47/70  Signal level=-63 dBm  
                    Encryption key:on
                    ESSID:"SKY1704C"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000d6403c2ae
                    Extra: Last beacon: 2ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: <MAC C-03 PlusnetWireless0D3F70>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=34/70  Signal level=-76 dBm  
                    Encryption key:on
                    ESSID:"PlusnetWireless0D3F70"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000825dc590a
                    Extra: Last beacon: 2ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 04 - Address: <MAC C-04 BTWiFi-with-FON>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=70/70  Signal level=-32 dBm  
                    Encryption key:off
                    ESSID:"BTWiFi-with-FON"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000105386e2c6d
                    Extra: Last beacon: 2ms ago
          Cell 05 - Address: <MAC C-05 TALKTALK-DF2498>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=28/70  Signal level=-82 dBm  
                    Encryption key:on
                    ESSID:"TALKTALK-DF2498"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000bc41cbd77f3
                    Extra: Last beacon: 2ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
          Cell 06 - Address: <MAC C-06 TALKTALK-10DE4D>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=22/70  Signal level=-88 dBm  
                    Encryption key:on
                    ESSID:"TALKTALK-10DE4D"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000003c7c6731
                    Extra: Last beacon: 4275ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
          Cell 07 - Address: <MAC C-07 BTWifi-with-FON>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=21/70  Signal level=-89 dBm  
                    Encryption key:off
                    ESSID:"BTWifi-with-FON"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000c32f1f11f4
                    Extra: Last beacon: 4271ms ago
          Cell 08 - Address: <MAC C-08 Rodney>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=22/70  Signal level=-88 dBm  
                    Encryption key:on
                    ESSID:"Rodney"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000017faefc666e
                    Extra: Last beacon: 4262ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
          Cell 09 - Address: <MAC C-09 >
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=27/70  Signal level=-83 dBm  
                    Encryption key:on
                    ESSID:""
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000c85029e197
                    Extra: Last beacon: 4256ms ago
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

[iwlmvm]
filename:       /lib/modules/3.13.0-35-lowlatency/kernel/drivers/net/wireless/iwlwifi/mvm/iwlmvm.ko
version:        in-tree:
srcversion:     478509C929B480278881B2A
depends:        iwlwifi,mac80211,cfg80211
parm:           init_dbg:set to true to debug an ASSERT in INIT fw (default: false (bool)
parm:           power_scheme:power management scheme: 1-active, 2-balanced, 3-low power, default: 2 (int)

[mac80211]
filename:       /lib/modules/3.13.0-35-lowlatency/kernel/net/mac80211/mac80211.ko
srcversion:     D491AB7C521706DA5F4BE7C
depends:        cfg80211
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[iwlwifi]
filename:       /lib/modules/3.13.0-35-lowlatency/kernel/drivers/net/wireless/iwlwifi/iwlwifi.ko
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
filename:       /lib/modules/3.13.0-35-lowlatency/kernel/net/wireless/cfg80211.ko
srcversion:     C2478077E22138832B71659
depends:        
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

[wmi]
filename:       /lib/modules/3.13.0-35-lowlatency/kernel/drivers/platform/x86/wmi.ko
srcversion:     CED5410F008DC70DF5F064B
depends:        
parm:           debug_event:Log WMI Events [0/1] (bool)
parm:           debug_dump_wdg:Dump available WMI interfaces [0/1] (bool)


udev rules ~~~~~~~~~~~~~~~~~~~~~~~~~

# PCI device 0x10ec:0x8168 (r8169)
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

BOOT_IMAGE=/boot/vmlinuz-3.13.0-35-lowlatency root=UUID=a8644d35-3e63-4741-94c0-7e86d805573b ro quiet splash vt.handoff=7


dmesg ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

[    1.594638] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[    1.595340] audit: initializing netlink socket (disabled)
[    2.424411] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    2.425765] wmi: Mapper loaded
[    7.986016] psmouse serio2: trackpoint: IBM TrackPoint firmware: 0x0e, buttons: 3/3
[   13.622164] thinkpad_acpi: http://ibm-acpi.sf.net/
[   13.623997] thinkpad_acpi: Unsupported brightness interface, please contact ibm-acpi-devel@lists.sourceforge.net
[   13.633995] iwlwifi 0000:04:00.0: irq 48 for MSI/MSI-X
[   13.874736] Bluetooth: hci0: Intel Bluetooth firmware file: intel/ibt-hw-37.7.10-fw-1.80.2.3.d.bseq
[   13.985530] Bluetooth: hci0: Intel Bluetooth firmware patch completed and activated
[   14.367961] iwlwifi 0000:04:00.0: loaded firmware version 22.24.8.0 op_mode iwlmvm
[   14.382118] iwlwifi 0000:04:00.0: Detected Intel(R) Dual Band Wireless AC 7260, REV=0x144
[   14.382200] iwlwifi 0000:04:00.0: L1 Enabled; Disabling L0S
[   14.382444] iwlwifi 0000:04:00.0: L1 Enabled; Disabling L0S
[   14.582453] ieee80211 phy0: Selected rate control algorithm 'iwl-mvm-rs'
[   16.405804] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   17.666375] iwlwifi 0000:04:00.0: L1 Enabled; Disabling L0S
[   17.666630] iwlwifi 0000:04:00.0: L1 Enabled; Disabling L0S
[   17.678421] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   17.678641] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   21.266773] wlan0: authenticate with <MAC C-01 BTHub3-P4Z8>
[   21.268960] wlan0: send auth to <MAC C-01 BTHub3-P4Z8> (try 1/3)
[   21.307862] wlan0: authenticated
[   21.308791] wlan0: associate with <MAC C-01 BTHub3-P4Z8> (try 1/3)
[   21.313051] wlan0: RX AssocResp from <MAC C-01 BTHub3-P4Z8> (capab=0x411 status=0 aid=1)
[   21.318929] wlan0: associated
[   21.318971] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready

    ======== Done ========


```

Thanks!

---

### Post by varunendra on 2014-09-23
First off, please change the encryption type in your router to pure WPA2-PSK with AES (CCMP). It might not be related to the disconnection issue, but is definitely not 'optimal' in its current state, which is WPA/WPA2 mixed mode with TKIP. Reboot the router after saving the change. Pure WPA2-PSK with AES will just 'optimize' the encryption for better security and better performance.

Then, for the disconnection issue, please try the following -

[indent]**1)** Turn "Power Management" off on the wireless interface -
```
sudo iwconfig wlan0 power off
```
Then check -
```
iwconfig
```
..to confirm it is turned off. If this seems to help initially, but slows down or disconnects again, check the output again and let us know if it automatically turned "on" in the later outputs. We'll try to force it off then.

**2)** Along with the above, also use a driver parameter with "iwlwifi" -
```
echo "options iwlwifi 11n_disable=8" | sudo tee -a /etc/modprobe.d/iwlwifi.conf
```
..followed by a reboot.

**3)** If the "Power Management" trick in point 1 above doesn't seem to help, or turns on automatically after some time, try a parameter with the "iwlmvm" module -
```
echo "options iwlmvm power_scheme=1" | sudo tee /etc/modprobe.d/iwlmvm.conf
```
..followed by a reboot.[/indent]

Check and apply point 1 after every reboot if required. If it helps, but is required to be done manually after every reboot, we can try to make it permanent using a different approach.

If none of these seems to help, please post a fresh report with the suggested changes applied (encryption change, module parameters with iwlwifi and iwlmvm applied, power-management turned off).

---

### Post by newholm1 on 2014-09-24
Great! That seems to have done the trick quite nicely, thanks so much. The only thing is that after reboot, the wireless card's power management is back on. I believe you mentioned a way round this ...

---

### Post by varunendra on 2014-09-24
Actually there are two ways.

**1)**
If you need to run the command only once after each reboot, add it to the /etc/rc.local file, just above the last line that says "exit 0". The following command will do it -
```
sudo sed -i '/^exit 0/i /sbin/iwconfig wlan0 power off' /etc/rc.local
```
You can run the command without the "-i" option to see its effect without actually changing the file - good for testing if you are typing it right.

**2)**
If running it only once is not enough, and it automatically turns back on after sometime, then we'll have to create a one-line script in "/etc/pm/power.d" directory, and make it executable -
```
echo "/sbin/iwconfig wlan0 power off" | sudo tee /etc/pm/power.d/wireless
sudo chmod +x /etc/pm/power.d/wireless
```
This will create a file "wireless" in the directory that will override the default power-management script that exists in "/usr/lib/pm-utils/power.d" directory.

Try one of these as required, and let us know if it worked.

---

### Post by newholm1 on 2014-09-26
Excellent, that's sorted now. I haven't really had a chance to see if  the signal drops after a while, but the wireless interface's power  management now registers as being Off when I run iwconfig after startup.  Is there any reason not to run solution 2 as well, just in case? Or  would that create some kind of conflict? I'd like to get it properly  sorted so I can make a backup disc.

---

### Post by varunendra on 2014-09-26
> **newholm1 said:**
> Is there any reason not to run solution 2 as well, just in case? Or  would that create some kind of conflict?
Not a conflict, but the default script is there for a reason. We only need to override it with some certain cards in some certain situations, in which it doesn't work as expected.

A good way to test whether the power management turns on automatically is to just connect and leave the network idle for about half an hour. The machine doesn't need to be idle (you can work on it during this time), just the network. It is this idle state of the network card that *can* trigger the power management again. Run "iwconfig" after about 30-40 minutes of idle network time. If it has not been turned on again, the fix is solid and you don't need the second trick of creating a "wireless" file.

But again, creating one anyway is not going to hurt much (if at all), but I also can't say if it is guaranteed to work better.

In any case, if the fix seems to be permanent, please consider marking the thread as **[SOLVED]** to make it more helpful for others like you. :)

---

### Post by newholm1 on 2014-09-26
I just did the idle test, and the power management had not switched back on. Thanks very much! I shall indeed mark this thread as solved.

---

### Post by varunendra on 2014-09-26
You're welcome! And thanks for the confirmation and feedback. :)

---

