---
title: "Inter centrino Advanced-N 6230 wifi connected, no internet, unbuntu 13.04"
date: 2014-05-04
forum: Networking &amp; Wireless
---

### Post by Nicolas_H on 2014-05-04
Hello,
I can't ping nothing when using wifi. I can connect to the network but I'm not able to load any web page or ping [www.google.com](www.google.com).

Here is the output of the wireless_script:



########## wireless info START ##########


##### release #####


Distributor ID:	Ubuntu
Description:	Ubuntu 13.04
Release:	13.04
Codename:	raring


##### kernel #####


Linux nhallepee-TECRA-R850 3.8.0-35-generic #50-Ubuntu SMP Tue Dec 3 01:24:59 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux


##### lspci #####


00:19.0 Ethernet controller [0200]: Intel Corporation 82579LM Gigabit Network Connection [8086:1502] (rev 04)
	Subsystem: Toshiba America Info Systems Device [1179:0001]
	Kernel driver in use: e1000e


05:00.0 Network controller [0280]: Intel Corporation Centrino Advanced-N 6230 [Rainbow Peak] [8086:0091] (rev 34)
	Subsystem: Intel Corporation Centrino Advanced-N 6230 AGN [8086:5201]
	Kernel driver in use: iwlwifi


##### lsusb #####


Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 003: ID 08ff:168b AuthenTec, Inc. 
Bus 001 Device 004: ID 04f2:b1d6 Chicony Electronics Co., Ltd 
Bus 002 Device 003: ID 8086:0189 Intel Corp. 


##### PCMCIA Card Info #####


##### rfkill #####


0: Toshiba Bluetooth: Bluetooth
	Soft blocked: no
	Hard blocked: no
1: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
2: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no


##### iw reg get #####


country 00:
	(2402 - 2472 @ 40), (3, 20)
	(2457 - 2482 @ 20), (3, 20), PASSIVE-SCAN, NO-IBSS
	(2474 - 2494 @ 20), (3, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
	(5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
	(5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS


##### interfaces #####


# interfaces(5) file used by ifup(8) and ifdown(8)
auto eth0 inet dhcp


auto lo
iface lo inet loopback


##### iwconfig #####


wlan0     IEEE 802.11abgn  ESSID:"Bighouse"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: <MAC address removed>   
          Bit Rate=18 Mb/s   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality=61/70  Signal level=-49 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:51   Missed beacon:0


##### route #####


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.0.1     0.0.0.0         UG    0      0        0 wlan0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 wlan0
192.168.0.0     0.0.0.0         255.255.255.0   U     9      0        0 wlan0


##### resolv.conf #####


##### nm-tool #####


NetworkManager Tool


State: connected (global)


- Device: wlan0  [Bighouse] ----------------------------------------------------
  Type:              802.11 WiFi
  Driver:            iwlwifi
  State:             connected
  Default:           yes
  HW Address:        <MAC address removed>


  Capabilities:
    Speed:           18 Mb/s


  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes


  Wireless Access Points (* = current AP)
    Super:           Infra, <MAC address removed>, Freq 5220 MHz, Rate 54 Mb/s, Strength 90 WPA2
    belkin.47e:      Infra, <MAC address removed>, Freq 2442 MHz, Rate 54 Mb/s, Strength 77 WPA WPA2
    TNCAP0004B9:     Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 29 WPA WPA2
    Belkin_2B04FF:   Infra, <MAC address removed>, Freq 2457 MHz, Rate 54 Mb/s, Strength 17 WPA WPA2
    TOYDEN_WiFi:     Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 15 WPA WPA2
    *Bighouse:       Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 72 WPA WPA2
    Open Door:       Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 14 WPA WPA2
    SETUP:           Ad-Hoc, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 12
    TOYDEN_WiFi:     Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 34 WPA WPA2
    TOYDEN_WiFi:     Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 27 WPA WPA2
    Nederland:       Infra, <MAC address removed>, Freq 2457 MHz, Rate 54 Mb/s, Strength 20 WPA
    vodafoneB9E2:    Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 19 WPA


  IPv4 Settings:
    Address:         192.168.0.26
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.0.1


    DNS:             192.168.0.1


- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            e1000e
  State:             unavailable
  Default:           no
  HW Address:        <MAC address removed>


  Capabilities:
    Carrier Detect:  yes


  Wired Properties
    Carrier:         off


##### NetworkManager.state #####


[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true


##### NetworkManager.conf #####


[main]
plugins=ifupdown,keyfile
dns=dnsmasq


no-auto-default=<MAC address removed>,


[ifupdown]
managed=false


##### iwlist #####


wlan0     Scan completed :
          Cell 01 - Address: <MAC address removed>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=60/70  Signal level=-50 dBm  
                    Encryption key:on
                    ESSID:"Bighouse"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000001d1b56ee23
                    Extra: Last beacon: 68ms ago
                    IE: Unknown: 0008426967686F757365
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030101
                    IE: Unknown: 2A0104
                    IE: Unknown: 2F0104
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD7C0050F204104A0001101044000102103B00010310470010298C5C548EDC2D72DBB414967B36C95A1021000D4E4554474541522C20496E632E10230005443633303010240005443633303010420004333730301054000800060050F2040001101100054436333030100800020004103C0001011049000600372A000120
                    IE: Unknown: DD09001018020CF02C0000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 02 - Address: <MAC address removed>
[...]
##### iwlist channel #####


wlan0     32 channels in total; available frequencies :
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
          Channel 36 : 5.18 GHz
          Channel 40 : 5.2 GHz
          Channel 44 : 5.22 GHz
          Channel 48 : 5.24 GHz
          Channel 52 : 5.26 GHz
          Channel 56 : 5.28 GHz
          Channel 60 : 5.3 GHz
          Channel 64 : 5.32 GHz
          Channel 100 : 5.5 GHz
          Channel 104 : 5.52 GHz
          Channel 108 : 5.54 GHz
          Channel 112 : 5.56 GHz
          Channel 116 : 5.58 GHz
          Channel 120 : 5.6 GHz
          Channel 124 : 5.62 GHz
          Channel 128 : 5.64 GHz
          Channel 132 : 5.66 GHz
          Channel 136 : 5.68 GHz
          Channel 140 : 5.7 GHz
          Current Frequency:2.412 GHz (Channel 1)


##### lsmod #####


iwldvm                241901  0 
mac80211              606872  1 iwldvm
iwlwifi               173803  1 iwldvm
cfg80211              512114  3 iwlwifi,mac80211,iwldvm


##### modinfo #####


filename:       /lib/modules/3.8.0-35-generic/kernel/drivers/net/wireless/iwlwifi/dvm/iwldvm.ko
license:        GPL
author:         Copyright(c) 2003-2012 Intel Corporation <ilw@linux.intel.com>
version:        in-tree:
description:    Intel(R) Wireless WiFi Link AGN driver for Linux
srcversion:     EECB8DFF0B4BD5CD4432F8E
depends:        iwlwifi,mac80211,cfg80211
intree:         Y
vermagic:       3.8.0-35-generic SMP mod_unload modversions 


filename:       /lib/modules/3.8.0-35-generic/kernel/drivers/net/wireless/iwlwifi/iwlwifi.ko
license:        GPL
author:         Copyright(c) 2003-2012 Intel Corporation <ilw@linux.intel.com>
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
firmware:       iwlwifi-3160-6.ucode
firmware:       iwlwifi-7260-6.ucode
srcversion:     5A113A7294F746786C0EDF7
alias:          pci:v00008086d000008B3sv*sd00008070bc*sc*i*
[...]
alias:          pci:v00008086d00004232sv*sd00001201bc*sc*i*
depends:        cfg80211
intree:         Y
vermagic:       3.8.0-35-generic SMP mod_unload modversions 
parm:           swcrypto:using crypto in software (default 0 [hardware]) (int)
parm:           11n_disable:disable 11n functionality, bitmap: 1: full, 2: agg TX, 4: agg RX (uint)
parm:           amsdu_size_8K:enable 8K amsdu size (int)
parm:           fw_restart:restart firmware in case of error (int)
parm:           antenna_coupling:specify antenna coupling in dB (defualt: 0 dB) (int)
parm:           bt_ch_inhibition:Enable BT channel inhibition (default: enable) (bool)
parm:           plcp_check:Check plcp health (default: 1 [enabled]) (bool)
parm:           wd_disable:Disable stuck queue watchdog timer 0=system default, 1=disable, 2=enable (default: 0) (int)
parm:           bt_coex_active:enable wifi/bt co-exist (default: enable) (bool)
parm:           led_mode:0=system default, 1=On(RF On)/Off(RF Off), 2=blinking, 3=Off (default: 0) (int)
parm:           power_save:enable WiFi power management (default: disable) (bool)
parm:           power_level:default power save level (range from 1 - 5, default: 1) (int)
parm:           auto_agg:enable agg w/o check traffic load (default: enable) (bool)
parm:           5ghz_disable:disable 5GHz band (default: 0 [enabled]) (bool)


##### modules #####


loop
lp
rtc


##### blacklist #####


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


SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"


# PCI device 0x8086:/sys/devices/pci0000:00/0000:00:19.0 (e1000e)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"


##### dmesg #####


[    2.094958] iwlwifi 0000:05:00.0: irq 49 for MSI/MSI-X
[    2.110436] iwlwifi 0000:05:00.0: loaded firmware version 18.168.6.1
[    2.139545] iwlwifi 0000:05:00.0: CONFIG_IWLWIFI_DEBUG disabled
[    2.139550] iwlwifi 0000:05:00.0: CONFIG_IWLWIFI_DEBUGFS enabled
[    2.139553] iwlwifi 0000:05:00.0: CONFIG_IWLWIFI_DEVICE_TRACING enabled
[    2.139555] iwlwifi 0000:05:00.0: CONFIG_IWLWIFI_DEVICE_TESTMODE enabled
[    2.139557] iwlwifi 0000:05:00.0: CONFIG_IWLWIFI_P2P disabled
[    2.139560] iwlwifi 0000:05:00.0: Detected Intel(R) Centrino(R) Advanced-N 6230 AGN, REV=0xB0
[    2.139677] iwlwifi 0000:05:00.0: L1 Enabled; Disabling L0S
[    2.139893] iwlwifi 0000:05:00.0: RF_KILL bit toggled to enable radio.
[    2.320739] ieee80211 phy0: Selected rate control algorithm 'iwl-agn-rs'
[    4.355885] iwlwifi 0000:05:00.0: L1 Enabled; Disabling L0S
[    4.356081] iwlwifi 0000:05:00.0: Radio type=0x1-0x2-0x0
[    4.746914] iwlwifi 0000:05:00.0: L1 Enabled; Disabling L0S
[    4.747178] iwlwifi 0000:05:00.0: Radio type=0x1-0x2-0x0
[    4.963369] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[    4.963618] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   11.470336] wlan0: authenticate with <MAC address removed>
[   11.479342] wlan0: send auth to <MAC address removed> (try 1/3)
[   11.481244] wlan0: authenticated
[   11.485489] wlan0: associate with <MAC address removed> (try 1/3)
[   11.488377] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=2)
[   11.493514] wlan0: associated
[   11.493537] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready


########## wireless info END ############

---

### Post by varunendra on 2014-05-04
Please edit your post to wrap the output part within 'Code' tags. Please follow the "Using Code Tags" link in my signature below to see how.

About the problem - Please log into your router's web interface and change the wireless security type to pure WPA2-PSK with AES (CCMP). Currently it is using WPA/WPA2 mixed mode with TKIP that should be avoided. Reboot the router after saving the change, and retry to connect (reboot the laptop too, if required).

If the problem persists, may I request to run an experimental version of "wireless_script"? It covers much more information (while maintaining the security filters) but is still experimental and may have bugs. If it generates the report correctly, please post that one. Here's the link to the experimental script : [https://dl.dropbox.com/s/qjc87hzk1z5x6z0/wireless_script](https://dl.dropbox.com/s/qjc87hzk1z5x6z0/wireless_script)

---

### Post by Nicolas_H on 2014-05-07
Hello Varunendra,

Thank for the reply
I'm afraid I don't have access to the router. I've run your script, I also tryed to ping the gateway successfully, but failed to reach [www.google.com](www.google.com) for example :

```



	======== Wireless-Info START ========


System-Info ~~~~~~~~~~~~~~~~~~~~~~~~


nhallepee-TECRA-R850 3.8.0-35-generic x86_64,  Ubuntu 13.04, raring


CPU    : Intel(R) Core(TM) i5-2520M CPU @ 2.50GHz
Memory : 5919 MB
Uptime : 10:19:11 up 1 min,  2 users,  load average: 0.17, 0.09, 0.04




lspci ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~


00:19.0 Ethernet controller [0200]: Intel Corporation 82579LM Gigabit Network Connection [8086:1502] (rev 04)
	Subsystem: Toshiba America Info Systems Device [1179:0001]
	Kernel driver in use: e1000e
--
05:00.0 Network controller [0280]: Intel Corporation Centrino Advanced-N 6230 [Rainbow Peak] [8086:0091] (rev 34)
	Subsystem: Intel Corporation Centrino Advanced-N 6230 AGN [8086:5201]
	Kernel driver in use: iwlwifi




lsusb ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~


Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 003: ID 08ff:168b AuthenTec, Inc. 
Bus 001 Device 004: ID 04f2:b1d6 Chicony Electronics Co., Ltd 
Bus 002 Device 003: ID 8086:0189 Intel Corp. 




PCMCIA Card Info ~~~~~~~~~~~~~~~~~~~






iwconfig ~~~~~~~~~~~~~~~~~~~~~~~~~~~


wlan0     IEEE 802.11abgn  ESSID:"Bighouse"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: <MAC C-01 Bighouse>   
          Bit Rate=48 Mb/s   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=53/70  Signal level=-57 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:51   Missed beacon:0






rfkill ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~


      Interface                  Soft blocked  Hard blocked
0: Toshiba Bluetooth: Bluetooth      no            no
1: phy0: Wireless LAN                no            no
2: hci0: Bluetooth                   no            no




lsmod ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~


iwldvm                241901  0 
mac80211              606872  1 iwldvm
wmi                    19070  1 toshiba_acpi
iwlwifi               173803  1 iwldvm
cfg80211              512114  3 iwlwifi,mac80211,iwldvm




module parameters ~~~~~~~~~~~~~~~~~~


cfg80211      (2): cfg80211_disable_40mhz_24ghz=N | ieee80211_regdom=00
iwlwifi      (14): 11n_disable=0 | 5ghz_disable=N | amsdu_size_8K=1 | antenna_coupling=0 | auto_agg=Y | bt_ch_inhibition=Y | bt_coex_active=Y | fw_restart=1 | led_mode=0 | plcp_check=Y | power_level=0 | power_save=N | swcrypto=0 | wd_disable=1
mac80211      (4): ieee80211_default_rc_algo=minstrel_ht | max_nullfunc_tries=2 | max_probe_tries=5 | probe_wait_ms=500
wmi           (2): debug_dump_wdg=N | debug_event=N




nm-tool ~~~~~~~~~~~~~~~~~~~~~~~~~~~~


State: connected (global)
===================o=============o=========o==============o=========o===========o==============o===========
 Interface & ID    | Type        | Driver  | State        | Default | Speed     | Support      | HW Addr   
===================o=============o=========o==============o=========o===========o==============o===========
 wlan0  [Bighouse] | 802.11 WiFi | iwlwifi | connected    | yes     | 48 Mb/s   | WEP/WPA/WPA2 | <MAC wlan0>


    Super:           Infra, <MAC C-NA Super 1>, Freq 5220 MHz, Rate 54 Mb/s, Strength 92 WPA2
    belkin.47e:      Infra, <MAC C-04 belkin.47e>, Freq 2442 MHz, Rate 54 Mb/s, Strength 90 WPA WPA2
    TNCAP0004B9:     Infra, <MAC C-02 TNCAP0004B9>, Freq 2437 MHz, Rate 54 Mb/s, Strength 45 WPA WPA2
    vodafone5F01:    Infra, <MAC C-03 vodafone5F01>, Freq 2432 MHz, Rate 54 Mb/s, Strength 19 WPA
    *Bighouse:       Infra, <MAC C-01 Bighouse>, Freq 2462 MHz, Rate 54 Mb/s, Strength 66 WPA WPA2
    reidresidence:   Infra, <MAC C-05 reidresidence>, Freq 2462 MHz, Rate 54 Mb/s, Strength 19 WPA


    Address:         192.168.0.10
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.0.1
    DNS:             192.168.0.1
-------------------+-------------+---------+--------------+---------+-----------+--------------+-----------
 eth0              | Wired       | e1000e  | unavailable  | no      |           |              | <MAC eth0>
-------------------+-------------+---------+--------------+---------+-----------+--------------+-----------




NetworkManager.state ~~~~~~~~~~~~~~~
[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true




NetworkManager.conf ~~~~~~~~~~~~~~~~


[main]
plugins=ifupdown,keyfile
dns=dnsmasq


no-auto-default=<MAC eth0>,


[ifupdown]
managed=false




NM WiFi Profiles ~~~~~~~~~~~~~~~~~~~


Bighouse             : ssid=Bighouse | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 
Campus SFR           : ssid=Campus SFR | mac-address=<MAC wlan0> | ipv6=auto | ipv4=auto 
Christchurch City Libraries : ssid=Christchurch City Libraries | mac-address=<MAC wlan0> | ipv6=auto | ipv4=auto 
Deathstar            : ssid=Deathstar | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 
ECOM_MOB_DEV         : ssid=ECOM_MOB_DEV | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 
ippon-formation      : ssid=ippon-formation | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 




interfaces ~~~~~~~~~~~~~~~~~~~~~~~~~


# interfaces(5) file used by ifup(8) and ifdown(8)
auto eth0 inet dhcp


auto lo
iface lo inet loopback


resolv.conf ~~~~~~~~~~~~~~~~~~~~~~~~










Routes & Ping ~~~~~~~~~~~~~~~~~~~~~~


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.0.1     0.0.0.0         UG    0      0        0 wlan0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 wlan0
192.168.0.0     0.0.0.0         255.255.255.0   U     9      0        0 wlan0


--- 192.168.0.1 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 1001ms
rtt min/avg/max/mdev = 1.690/1.752/1.815/0.075 ms




iw reg get ~~~~~~~~~~~~~~~~~~~~~~~~~


(Region : "en_US.UTF-8")
country 00:
	(2402 - 2472 @ 40), (3, 20)
	(2457 - 2482 @ 20), (3, 20), PASSIVE-SCAN, NO-IBSS
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


          Current Frequency:2.462 GHz (Channel 11)




iwlist scan ~~~~~~~~~~~~~~~~~~~~~~~~


wlan0     Scan completed :
          Cell 01 - Address: <MAC C-01 Bighouse>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=51/70  Signal level=-59 dBm  
                    Encryption key:on
                    ESSID:"Bighouse"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000312ffc7fcc
                    Extra: Last beacon: 80ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC C-02 TNCAP0004B9>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=35/70  Signal level=-75 dBm  
                    Encryption key:on
                    ESSID:"TNCAP0004B9"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 80ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: <MAC C-03 vodafone5F01>
                    Channel:5
                    Frequency:2.432 GHz (Channel 5)
                    Quality=22/70  Signal level=-88 dBm  
                    Encryption key:on
                    ESSID:"vodafone5F01"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000003ac3c5254f
                    Extra: Last beacon: 18104ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 04 - Address: <MAC C-04 belkin.47e>
                    Channel:7
                    Frequency:2.442 GHz (Channel 7)
                    Quality=64/70  Signal level=-46 dBm  
                    Encryption key:on
                    ESSID:"belkin.47e"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000051841267f6a
                    Extra: Last beacon: 80ms ago
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 05 - Address: <MAC C-05 reidresidence>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=21/70  Signal level=-89 dBm  
                    Encryption key:on
                    ESSID:"reidresidence"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000045ef47c0fde
                    Extra: Last beacon: 18104ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK




blacklist ~~~~~~~~~~~~~~~~~~~~~~~~~~


[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci




modinfo ~~~~~~~~~~~~~~~~~~~~~~~~~~~~


[iwldvm]
filename:       /lib/modules/3.8.0-35-generic/kernel/drivers/net/wireless/iwlwifi/dvm/iwldvm.ko
version:        in-tree:
srcversion:     EECB8DFF0B4BD5CD4432F8E
depends:        iwlwifi,mac80211,cfg80211


[mac80211]
filename:       /lib/modules/3.8.0-35-generic/kernel/net/mac80211/mac80211.ko
srcversion:     F9675B7933C26FC7BDD7E95
depends:        cfg80211
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)


[iwlwifi]
filename:       /lib/modules/3.8.0-35-generic/kernel/drivers/net/wireless/iwlwifi/iwlwifi.ko
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
firmware:       iwlwifi-3160-6.ucode
firmware:       iwlwifi-7260-6.ucode
srcversion:     5A113A7294F746786C0EDF7
depends:        cfg80211
parm:           swcrypto:using crypto in software (default 0 [hardware]) (int)
parm:           11n_disable:disable 11n functionality, bitmap: 1: full, 2: agg TX, 4: agg RX (uint)
parm:           amsdu_size_8K:enable 8K amsdu size (int)
parm:           fw_restart:restart firmware in case of error (int)
parm:           antenna_coupling:specify antenna coupling in dB (defualt: 0 dB) (int)
parm:           bt_ch_inhibition:Enable BT channel inhibition (default: enable) (bool)
parm:           plcp_check:Check plcp health (default: 1 [enabled]) (bool)
parm:           wd_disable:Disable stuck queue watchdog timer 0=system default, 1=disable, 2=enable (default: 0) (int)
parm:           bt_coex_active:enable wifi/bt co-exist (default: enable) (bool)
parm:           led_mode:0=system default, 1=On(RF On)/Off(RF Off), 2=blinking, 3=Off (default: 0) (int)
parm:           power_save:enable WiFi power management (default: disable) (bool)
parm:           power_level:default power save level (range from 1 - 5, default: 1) (int)
parm:           auto_agg:enable agg w/o check traffic load (default: enable) (bool)
parm:           5ghz_disable:disable 5GHz band (default: 0 [enabled]) (bool)


[cfg80211]
filename:       /lib/modules/3.8.0-35-generic/kernel/net/wireless/cfg80211.ko
srcversion:     5A5A1CFD1D461C7BBD4F92F
depends:        
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)




udev rules ~~~~~~~~~~~~~~~~~~~~~~~~~


SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC wlan0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"


# PCI device 0x8086:/sys/devices/pci0000:00/0000:00:19.0 (e1000e)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC eth0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"




Custom files/entries ~~~~~~~~~~~~~~~


/etc/modules        : Not Default
/etc/rc.local       : Default
/etc/modprobe.d     : Not Default
/etc/pm/(cnf|pw|sl) : Not Default


[/etc/modules]
loop


[/etc/modprobe.d]
iwlwifi.conf      : remove iwlwifi \
                    (/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
                    && /sbin/modprobe -r mac80211
iwlwifi.conf~     : remove iwlwifi \
                    (/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
                    && /sbin/modprobe -r mac80211
                    options iwlwifi 11n_disable=1
mlx4.conf         : softdep mlx4_core post: mlx4_en


[/etc/pm/power.d/wireless]
#!/bin/sh
/sbin/iwconfig wlan0 power off




Kernel boot line ~~~~~~~~~~~~~~~~~~~


BOOT_IMAGE=/boot/vmlinuz-3.8.0-35-generic root=UUID=9fa3f9db-f36f-4c83-b775-af855869af8e ro quiet splash vt.handoff=7




dmesg ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~


[    0.416502] audit: initializing netlink socket (disabled)
[    2.086386] iwlwifi 0000:05:00.0: irq 49 for MSI/MSI-X
[    2.107762] wmi: Mapper loaded
[    2.112543] iwlwifi 0000:05:00.0: loaded firmware version 18.168.6.1
[    2.148808] iwlwifi 0000:05:00.0: CONFIG_IWLWIFI_DEBUG disabled
[    2.148811] iwlwifi 0000:05:00.0: CONFIG_IWLWIFI_DEBUGFS enabled
[    2.148813] iwlwifi 0000:05:00.0: CONFIG_IWLWIFI_DEVICE_TRACING enabled
[    2.148815] iwlwifi 0000:05:00.0: CONFIG_IWLWIFI_DEVICE_TESTMODE enabled
[    2.148816] iwlwifi 0000:05:00.0: CONFIG_IWLWIFI_P2P disabled
[    2.148819] iwlwifi 0000:05:00.0: Detected Intel(R) Centrino(R) Advanced-N 6230 AGN, REV=0xB0
[    2.148957] iwlwifi 0000:05:00.0: L1 Enabled; Disabling L0S
[    2.149139] iwlwifi 0000:05:00.0: RF_KILL bit toggled to enable radio.
[    2.313280] ieee80211 phy0: Selected rate control algorithm 'iwl-agn-rs'
[    2.348314] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[    4.006028] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[    4.403204] iwlwifi 0000:05:00.0: L1 Enabled; Disabling L0S
[    4.403400] iwlwifi 0000:05:00.0: Radio type=0x1-0x2-0x0
[    4.794773] iwlwifi 0000:05:00.0: L1 Enabled; Disabling L0S
[    4.794976] iwlwifi 0000:05:00.0: Radio type=0x1-0x2-0x0
[    5.016204] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[    5.016425] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   11.368551] wlan0: authenticate with <MAC C-01 Bighouse>
[   11.377018] wlan0: send auth to <MAC C-01 Bighouse> (try 1/3)
[   11.379840] wlan0: authenticated
[   11.381362] wlan0: associate with <MAC C-01 Bighouse> (try 1/3)
[   11.384875] wlan0: RX AssocResp from <MAC C-01 Bighouse> (capab=0x411 status=0 aid=1)
[   11.390092] wlan0: associated
[   11.390159] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready


	======== Done ========




nhallepee@nhallepee-TECRA-R850:~$ ping 192.168.0.1
PING 192.168.0.1 (192.168.0.1) 56(84) bytes of data.
64 bytes from 192.168.0.1: icmp_req=1 ttl=64 time=1.34 ms
64 bytes from 192.168.0.1: icmp_req=2 ttl=64 time=2.78 ms
^C
--- 192.168.0.1 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 1001ms
rtt min/avg/max/mdev = 1.344/2.066/2.789/0.723 ms
nhallepee@nhallepee-TECRA-R850:~$ ping www.google.com
ping: unknown host www.google.com



```

---

### Post by Nicolas_H on 2014-05-07
Ok, that's what i tought in the first place : the resolv.conf file was empty. That's why the host name couldn't be resolved.
I added 192.168.0.1 and the google dns and it works fine now.

Thanks

---

