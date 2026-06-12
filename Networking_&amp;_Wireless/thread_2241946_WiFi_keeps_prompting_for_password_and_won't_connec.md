---
title: "WiFi keeps prompting for password and won't connect."
date: 2014-08-29
forum: Networking &amp; Wireless
---

### Post by ben104 on 2014-08-29
Hello people,

I'm new here and still quite a newbie to Ubuntu and would really appreciate some help. Anyway, I have not had any trouble what so ever with my WiFi before and it's always worked fine (with Ubuntu) so I find this quite weird. I installed an emulator called VBA-M as I fancied a go of a few Gameboy Advance games. I full-screened the game and started playing but it ended up crashing! I pressed ESC to get out of full-screen mode but it wouldn't do it. So I started button bashing, pressing all kinds of buttons on the keyboard (silly I know), the game screen went a bit smaller but was still hanging! I saw an error message pop up but most of it was behind the window the game was running on. I was unable to move the mouse or do anything else so I held down the power button until the laptop turned off. I turned the laptop on and logged in, a box came up for the WiFi saying "Disconnected - You are not connected to the internet". I have reset the router, forgot the network and re-entered the password but nothing seems to work. Sometimes it asks me for the network password a few times but still refuses to connect. I'm using a wired connection at the moment which is working fine. I have an output from a wireless script which I'm posting and would really appreciate some help with this as it's driving me crazy!

```
########## wireless info START ##########

Report from: 29 Aug 2014 16:03 BST +0100


Script from: 17 Aug 2014 02:46 UTC +0000


##### release #####


Distributor ID:	Ubuntu
Description:	Ubuntu 14.04.1 LTS
Release:	14.04
Codename:	trusty


##### kernel #####


Linux 3.13.0-35-generic #62-Ubuntu SMP Fri Aug 15 01:58:42 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux


Parameters: ro, quiet, splash, vt.handoff=7


##### desktop #####


Ubuntu


##### lspci #####


02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 0c)
	Subsystem: Toshiba America Info Systems Device [1179:facb]
	Kernel driver in use: r8169


03:00.0 Network controller [0280]: Intel Corporation Wireless 7260 [8086:08b1] (rev 6b)
	Subsystem: Intel Corporation Wireless-N 7260 [8086:c162]
	Kernel driver in use: iwlwifi


##### lsusb #####


Bus 001 Device 004: ID 04ca:7017 Lite-On Technology Corp. 
Bus 001 Device 003: ID 04f3:0165 Elan Microelectronics Corp. 
Bus 001 Device 005: ID 8087:07dc Intel Corp. 
Bus 001 Device 002: ID 8087:8000 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


##### PCMCIA card info #####


##### rfkill #####


0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
1: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no


##### lsmod #####


iwlmvm                189774  0 
mac80211              630653  1 iwlmvm
iwlwifi               169932  1 iwlmvm
cfg80211              484040  3 iwlwifi,mac80211,iwlmvm
wmi                    19177  1 toshiba_acpi


##### interfaces #####


auto lo
iface lo inet loopback


##### ifconfig #####


eth0      Link encap:Ethernet  HWaddr <MAC addr eth0>  
          inet addr:192.168.0.7  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::221a:6ff:fe7c:8db4/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2649 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1740 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1992275 (1.9 MB)  TX bytes:312885 (312.8 KB)


vmnet1    Link encap:Ethernet  HWaddr <MAC addr vmnet1>  
          inet addr:172.16.172.1  Bcast:172.16.172.255  Mask:255.255.255.0
          inet6 addr: fe80::250:56ff:fec0:1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:53 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


vmnet8    Link encap:Ethernet  HWaddr <MAC addr vmnet8>  
          inet addr:172.16.102.1  Bcast:172.16.102.255  Mask:255.255.255.0
          inet6 addr: fe80::250:56ff:fec0:8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:54 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


wlan0     Link encap:Ethernet  HWaddr <MAC addr wlan0>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


##### iwconfig #####


vmnet8    no wireless extensions.


eth0      no wireless extensions.


lo        no wireless extensions.


vmnet1    no wireless extensions.


wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=16 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          


##### route #####


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.0.1     0.0.0.0         UG    0      0        0 eth0
172.16.102.0    0.0.0.0         255.255.255.0   U     0      0        0 vmnet8
172.16.172.0    0.0.0.0         255.255.255.0   U     0      0        0 vmnet1
192.168.0.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0


##### resolv.conf #####


nameserver 127.0.1.1


##### nm-tool #####


NetworkManager Tool


State: connected (global)


- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            iwlwifi
  State:             disconnected
  Default:           no
  HW Address:        <MAC addr wlan0>


  Capabilities:


  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes


  Wireless Access Points 
    BTHub3-455R:     Infra, <MAC addr BTHub3-455R>, Freq 2412 MHz, Rate 54 Mb/s, Strength 64 WPA WPA2
    BTWifi-X:        Infra, <MAC addr BTWifi-X>, Freq 2412 MHz, Rate 54 Mb/s, Strength 64 WPA WPA2 Enterprise
    BTHub3-5CS2:     Infra, <MAC addr BTHub3-5CS2>, Freq 2412 MHz, Rate 54 Mb/s, Strength 27 WPA WPA2
    BTWifi-with-FON: Infra, <MAC addr BTWifi-with-FON>, Freq 2412 MHz, Rate 54 Mb/s, Strength 65
    BTWiFi-with-FON: Infra, <MAC addr BTWiFi-with-FON>, Freq 2412 MHz, Rate 54 Mb/s, Strength 30
    TALKTALK-E05AF4: Infra, <MAC addr TALKTALK-E05AF4>, Freq 2462 MHz, Rate 54 Mb/s, Strength 22 WPA WPA2
    virginmedia9610545: Infra, <MAC addr virginmedia9610545>, Freq 2462 MHz, Rate 54 Mb/s, Strength 22 WPA WPA2
    VM561371-2G:     Infra, <MAC addr VM561371-2G>, Freq 2447 MHz, Rate 54 Mb/s, Strength 100 WPA WPA2


- Device: eth0  [Wired connection 1] -------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             connected
  Default:           yes
  HW Address:        <MAC addr eth0>


  Capabilities:
    Carrier Detect:  yes
    Speed:           1000 Mb/s


  Wired Properties
    Carrier:         on


  IPv4 Settings:
    Address:         192.168.0.7
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.0.1


    DNS:             192.168.0.1


##### NetworkManager.state #####


[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true


##### NetworkManager.conf #####


[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq


no-auto-default=<MAC addr eth0>,


[ifupdown]
managed=false


##### iw reg get #####


country 00:
	(2402 - 2472 @ 40), (3, 20)
	(2457 - 2482 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
	(2474 - 2494 @ 20), (3, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
	(5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
	(5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS


##### iwlist channels #####


vmnet8    no frequency information.


eth0      no frequency information.


lo        no frequency information.


vmnet1    no frequency information.


wlan0     13 channels in total; available frequencies :
          Channel 01 : 2.412 GHz
          Channel 02 : 2.417 GHz
          Channel 03 : 2.422 GHz
          Channel 04 : 2.427 GHz
          Channel 05 : 2.432 GHz
          Channel 06 : 2.437 GHz
          Channel 07 : 2.442 GHz
          Channel 08 : 2.447 GHz
          Channel 09 : 2.452 GHz
          Channel 10 : 2.457 GHz
          Channel 11 : 2.462 GHz
          Channel 12 : 2.467 GHz
          Channel 13 : 2.472 GHz


##### iwlist scan #####


Channel occupancy:


     5   WLAPs on   Frequency:2.412 GHz (Channel 1)
     2   WLAPs on   Frequency:2.447 GHz (Channel 8)
     1   WLAPs on   Frequency:2.462 GHz (Channel 11)


vmnet8    Interface doesn't support scanning.


eth0      Interface doesn't support scanning.


lo        Interface doesn't support scanning.


wlan0     Scan completed :
          Cell 01 - Address: <MAC addr BTHub3-455R>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=49/70  Signal level=-61 dBm  
                    Encryption key:on
                    ESSID:"BTHub3-455R"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000008cd2408123
                    Extra: Last beacon: 48ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC addr BTWifi-with-FON>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=46/70  Signal level=-64 dBm  
                    Encryption key:off
                    ESSID:"BTWifi-with-FON"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000008cd241595c
                    Extra: Last beacon: 48ms ago
          Cell 03 - Address: <MAC addr BTWifi-X>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=46/70  Signal level=-64 dBm  
                    Encryption key:on
                    ESSID:"BTWifi-X"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000008cd24162ae
                    Extra: Last beacon: 48ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : 802.1x
                       Preauthentication Supported
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : 802.1x
          Cell 04 - Address: <MAC address>
                    Channel:8
                    Frequency:2.447 GHz (Channel 8)
                    Quality=70/70  Signal level=-28 dBm  
                    Encryption key:on
                    ESSID:"VM561371-2G"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000014dff5a82
                    Extra: Last beacon: 48ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 05 - Address: <MAC addr BTHub3-5CS2>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=25/70  Signal level=-85 dBm  
                    Encryption key:on
                    ESSID:"BTHub3-5CS2"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000b62621d13a
                    Extra: Last beacon: 48ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 06 - Address: <MAC addr BTWiFi-with-FON>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=27/70  Signal level=-83 dBm  
                    Encryption key:off
                    ESSID:"BTWiFi-with-FON"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000b62621fa6d
                    Extra: Last beacon: 48ms ago
          Cell 07 - Address: <MAC addr virginmedia9610545>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=23/70  Signal level=-87 dBm  
                    Encryption key:on
                    ESSID:"virginmedia9610545"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000020e2264a18b
                    Extra: Last beacon: 28556ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 08 - Address: <MAC addr VM561371-2G>
                    Channel:8
                    Frequency:2.447 GHz (Channel 8)
                    Quality=70/70  Signal level=-27 dBm  
                    Encryption key:on
                    ESSID:"VM561371-2G"
                    Bit Rates:1 Mb/vmnet1    Interface doesn't support scanning.


s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000014ddcc180
                    Extra: Last beacon: 2728ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK


##### module infos #####


[iwlmvm]
filename:       /lib/modules/3.13.0-35-generic/kernel/drivers/net/wireless/iwlwifi/mvm/iwlmvm.ko
license:        GPL
author:         Copyright(c) 2003-2013 Intel Corporation <ilw@linux.intel.com>
version:        in-tree:
description:    The new Intel(R) wireless AGN driver for Linux
srcversion:     478509C929B480278881B2A
depends:        iwlwifi,mac80211,cfg80211
intree:         Y
vermagic:       3.13.0-35-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        B1:41:4A:E9:6C:1B:0E:BB:7C:14:1F:A4:05:C1:F6:C9:8E:8A:66:F0
sig_hashalgo:   sha512
parm:           init_dbg:set to true to debug an ASSERT in INIT fw (default: false (bool)
parm:           power_scheme:power management scheme: 1-active, 2-balanced, 3-low power, default: 2 (int)


[iwlwifi]
filename:       /lib/modules/3.13.0-35-generic/kernel/drivers/net/wireless/iwlwifi/iwlwifi.ko
license:        GPL
author:         Copyright(c) 2003-2013 Intel Corporation <ilw@linux.intel.com>
version:        in-tree:
description:    Intel(R) Wireless WiFi driver for Linux
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
intree:         Y
vermagic:       3.13.0-35-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        B1:41:4A:E9:6C:1B:0E:BB:7C:14:1F:A4:05:C1:F6:C9:8E:8A:66:F0
sig_hashalgo:   sha512
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


##### module parameters #####


[iwlmvm]
init_dbg: N
power_scheme: 2


[iwlwifi]
11n_disable: 0
amsdu_size_8K: 0
antenna_coupling: 0
bt_coex_active: Y
fw_restart: Y
led_mode: 0
nvm_file: (null)
power_level: 0
power_save: N
swcrypto: 0
wd_disable: 1


##### /etc/modules #####


lp
rtc


##### blacklists #####


[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci


[/etc/modprobe.d/blacklist.conf]
blacklist evbug
blacklist usbmouse
blacklist usbkbd
blacklist eepro100
blacklist de4x5
blacklist eth1394
blacklist snd_intel8x0m
blacklist snd_aw2
blacklist i2c_i801
blacklist prism54
blacklist bcm43xx
blacklist garmin_gps
blacklist asus_acpi
blacklist snd_pcsp
blacklist pcspkr
blacklist amd76x_edac


##### udev rules #####


[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x10ec:0x8168 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC addr eth0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# PCI device 0x8086:0x08b1 (iwlwifi)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC addr wlan0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"


##### dmesg #####


[    1.643020] psmouse serio1: elantech: assuming hardware version 4 (with firmware version 0x381f01)
[    3.577849] iwlwifi 0000:03:00.0: enabling device (0000 -> 0002)
[    3.577998] iwlwifi 0000:03:00.0: irq 60 for MSI/MSI-X
[    3.585780] iwlwifi 0000:03:00.0: loaded firmware version 22.24.8.0 op_mode iwlmvm
[    3.617086] iwlwifi 0000:03:00.0: Detected Intel(R) Wireless N 7260, REV=0x144
[    3.618205] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S (repeated 2 times)
[    3.820354] ieee80211 phy0: Selected rate control algorithm 'iwl-mvm-rs'
[    3.931253] Bluetooth: hci0: Intel Bluetooth firmware file: intel/ibt-hw-37.7.10-fw-1.80.2.3.d.bseq
[    4.112858] Bluetooth: hci0: Intel Bluetooth firmware patch completed and activated
[    5.911584] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S (repeated 2 times)
[    5.923108] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready (repeated 2 times)
[   42.692519] wlan0: authenticate with <MAC address>
[   42.694548] wlan0: send auth to <MAC address> (try 1/3)
[   42.761676] wlan0: send auth to <MAC address> (try 2/3)
[   42.845529] wlan0: send auth to <MAC address> (try 3/3)
[   42.906778] wlan0: authentication with <MAC address> timed out
[   43.058520] wlan0: authenticate with <MAC addr VM561371-2G>
[   43.060272] wlan0: direct probe to <MAC addr VM561371-2G> (try 1/3)
[   43.264760] wlan0: direct probe to <MAC addr VM561371-2G> (try 2/3)
[   43.468758] wlan0: direct probe to <MAC addr VM561371-2G> (try 3/3)
[   43.672088] wlan0: authentication with <MAC addr VM561371-2G> timed out
[  227.498433] wlan0: authenticate with <MAC address>
[  227.499336] wlan0: send auth to <MAC address> (try 1/3)
[  227.559127] wlan0: send auth to <MAC address> (try 2/3)
[  227.629206] wlan0: send auth to <MAC address> (try 3/3)
[  227.675685] wlan0: authentication with <MAC address> timed out
[  228.727500] wlan0: authenticate with <MAC addr VM561371-2G>
[  228.729228] wlan0: direct probe to <MAC addr VM561371-2G> (try 1/3)
[  228.932709] wlan0: direct probe to <MAC addr VM561371-2G> (try 2/3)
[  229.136730] wlan0: direct probe to <MAC addr VM561371-2G> (try 3/3)
[  229.340137] wlan0: authentication with <MAC addr VM561371-2G> timed out


########## wireless info END ############
```

Thanks.

Also here is the contents of my iwlwifi.conf file:
```
# /etc/modprobe.d/iwlwifi.conf# iwlwifi will dyamically load either iwldvm or iwlmvm depending on the
# microcode file installed on the system.  When removing iwlwifi, first
# remove the iwl?vm module and then iwlwifi.
remove iwlwifi \
(/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
&& /sbin/modprobe -r mac80211
```

---

### Post by varunendra on 2014-08-29
Welcome to the forums ben104!

Please try the easiest shot first -
```
sudo iwconfig wlan0 power off
```
Then check -
```
iwconfig
```
..to make sure "Power Management" turned "off". Does it help? If yes, please confirm and we'll try to make it permanent. If not, try a driver parameter -
```
echo "options iwlmvm power_scheme=1" | sudo tee /etc/modprobe.d/iwlmvm.conf
```
Reboot, turn power management off again using the first command if required, and see if it can connect now.

By the way, if the power management keeps turning "on" automatically (after manually turning it 'off', or across reboots), please confirm so, and we'll take care of that first.

Be aware that it is supposed to save battery power when running on battery. So turning power management 'off' will cause the wireless card to operate at full power, without caring about power drain. But it shouldn't turn on at all when running on AC power.

---

### Post by ben104 on 2014-08-29
Thanks for your reply. While waiting for reply I was googling around and found a program called Wicd. I used that to try to connect but it was getting stuck at "Validating Authentication". So I decided that was no good and started googling how to get rid of it and why it was getting stuck, I came across the command: sudo apt-get remove --purge wicd. I did that and then just clicked connect through network manager again (in a final desperate attempt) and it connected straight away?!? I'm using it now! So I don't know what was going on. Thank you though for taking the time to reply, much appreciated.

---

