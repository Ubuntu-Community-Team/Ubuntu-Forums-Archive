---
title: "Ubuntu 18.04 LTS / network manager / wireless lost"
date: 2018-08-24
forum: Networking &amp; Wireless
---

### Post by devfabien on 2018-08-24
Hello

I migrate to Ubuntu 18.04 LTS but my wireless doesn't work. It crach after one hour or more.

[IMG]https://image.ibb.co/iekNoU/lkjahgoaebjdbopb.png\]https://image.ibb.co/iekNoU/lkjahgoaebjdbopb.png][/IMG]

I do this but it not resolve the problem :

    > sudo apt install --reinstall network-manager-gnome

I ran script (wireless info) 

Could you help me to decrypt the result ?

    ```
########## wireless info START ##########
    
    Report from: 24 Aug 2018 10:14 CEST +0200
    
    Booted last: 24 Aug 2018 00:00 CEST +0200
    
    Script from: 10 Jan 2018 20:04 UTC +0000
    
    ##### release ###########################
    
    Distributor ID:    Ubuntu
    Description:    Ubuntu 18.04.1 LTS
    Release:    18.04
    Codename:    bionic
    
    ##### kernel ############################
    
    Linux 4.15.0-32-generic #35-Ubuntu SMP Fri Aug 10 17:58:07 UTC 2018 x86_64 x86_64 x86_64 GNU/Linux
    
    Parameters: ro, quiet, splash, vt.handoff=1
    
    ##### desktop ###########################
    
    Ubuntu
    
    ##### lspci #############################
    
    00:1f.6 Ethernet controller [0200]: Intel Corporation Ethernet Connection I219-LM [8086:156f] (rev 21)
        Subsystem: Hewlett-Packard Company Ethernet Connection I219-LM [103c:8079]
        Kernel driver in use: e1000e
    
    02:00.0 Network controller [0280]: Intel Corporation Wireless 8260 [8086:24f3] (rev 3a)
        Subsystem: Intel Corporation Dual Band Wireless-AC 8260 [8086:0010]
        Kernel driver in use: iwlwifi
    
    ##### lsusb #############################
    
    Bus 002 Device 002: ID 0424:5534 Standard Microsystems Corp. Hub
    Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
    Bus 001 Device 007: ID 05c8:0383 Cheng Uei Precision Industry Co., Ltd (Foxlink) 
    Bus 001 Device 005: ID 138a:003f Validity Sensors, Inc. VFS495 Fingerprint Reader
    Bus 001 Device 003: ID 8087:0a2b Intel Corp. 
    Bus 001 Device 006: ID 413c:3016 Dell Computer Corp. Optical 5-Button Wheel Mouse
    Bus 001 Device 004: ID 413c:2107 Dell Computer Corp. 
    Bus 001 Device 002: ID 0424:2134 Standard Microsystems Corp. Hub
    Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
    
    ##### PCMCIA card info ##################
    
    ##### rfkill ############################
    
    0: hci0: Bluetooth
        Soft blocked: no
        Hard blocked: no
    1: phy0: Wireless LAN
        Soft blocked: no
        Hard blocked: no
    
    ##### lsmod #############################
    
    iwlmvm                364544  0
    mac80211              778240  1 iwlmvm
    hp_wmi                 16384  0
    intel_wmi_thunderbolt    16384  0
    iwlwifi               282624  1 iwlmvm
    sparse_keymap          16384  1 hp_wmi
    wmi_bmof               16384  0
    cfg80211              622592  3 iwlmvm,iwlwifi,mac80211
    wmi                    24576  3 wmi_bmof,intel_wmi_thunderbolt,hp_wmi
    
    ##### interfaces ########################
    
    [/etc/network/interfaces]
    auto lo
    iface lo inet loopback
    
    ##### ifconfig ##########################
    
    enp0s31f6: flags=4099<UP,BROADCAST,MULTICAST>  mtu 1500
            ether <MAC address>  txqueuelen 1000  (Ethernet)
            RX packets 0  bytes 0 (0.0 B)
            RX errors 0  dropped 0  overruns 0  frame 0
            TX packets 0  bytes 0 (0.0 B)
            TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0
            device interrupt 16  memory 0xe1200000-e1220000  
    
    lo: flags=73<UP,LOOPBACK,RUNNING>  mtu 65536
            inet 127.0.0.1  netmask 255.0.0.0
            inet6 ::1  prefixlen 128  scopeid 0x10<host>
            loop  txqueuelen 1000  (Local Loopback)
            RX packets 36494  bytes 3192677 (3.1 MB)
            RX errors 0  dropped 0  overruns 0  frame 0
            TX packets 36494  bytes 3192677 (3.1 MB)
            TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0
    
    wlp2s0: flags=4098<BROADCAST,MULTICAST>  mtu 1500
            ether <MAC address>  txqueuelen 1000  (Ethernet)
            RX packets 54224  bytes 50293042 (50.2 MB)
            RX errors 0  dropped 0  overruns 0  frame 0
            TX packets 50273  bytes 10642491 (10.6 MB)
            TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0
    
    ##### iwconfig ##########################
    
    enp0s31f6  no wireless extensions.
    
    lo        no wireless extensions.
    
    wlp2s0    IEEE 802.11  ESSID:off/any  
              Mode:Managed  Access Point: Not-Associated   Tx-Power=16 dBm   
              Retry short limit:7   RTS thr:off   Fragment thr:off
              Power Management:on
              
    
    ##### route #############################
    
    Kernel IP routing table
    Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
    
    ##### resolv.conf #######################
    
    nameserver 127.0.0.53
    search agent-creps.loc
    
    ##### network managers ##################
    
    Installed:
    
        NetworkManager
    
    Running:
    
    root      6946     1  0 10:13 ?        00:00:00 /usr/sbin/NetworkManager --no-daemon
    
    ##### NetworkManager info ###############
    
    GENERAL.DEVICE:                         enp0s31f6
    GENERAL.TYPE:                           ethernet
    GENERAL.NM-TYPE:                        NMDeviceEthernet
    GENERAL.VENDOR:                         Intel Corporation
    GENERAL.PRODUCT:                        Ethernet Connection I219-LM
    GENERAL.DRIVER:                         e1000e
    GENERAL.DRIVER-VERSION:                 3.2.6-k
    GENERAL.FIRMWARE-VERSION:               0.13-4
    GENERAL.HWADDR:                         <MAC address>
    GENERAL.MTU:                            1500
    GENERAL.STATE:                          20 (unavailable)
    GENERAL.REASON:                         2 (Device is now managed)
    GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1f.6/net/enp0s31f6
    GENERAL.IP-IFACE:                       --
    GENERAL.IS-SOFTWARE:                    no
    GENERAL.NM-MANAGED:                     yes
    GENERAL.AUTOCONNECT:                    yes
    GENERAL.FIRMWARE-MISSING:               no
    GENERAL.NM-PLUGIN-MISSING:              no
    GENERAL.PHYS-PORT-ID:                   --
    GENERAL.CONNECTION:                     --
    GENERAL.CON-UUID:                       --
    GENERAL.CON-PATH:                       --
    GENERAL.METERED:                        unknown
    CAPABILITIES.CARRIER-DETECT:            yes
    CAPABILITIES.SPEED:                     unknown
    CAPABILITIES.IS-SOFTWARE:               no
    CAPABILITIES.SRIOV:                     no
    WIRED-PROPERTIES.CARRIER:               off
    CONNECTIONS.AVAILABLE-CONNECTION-PATHS: --
    
    GENERAL.DEVICE:                         wlp2s0
    GENERAL.TYPE:                           wifi
    GENERAL.NM-TYPE:                        NMDeviceWifi
    GENERAL.VENDOR:                         Intel Corporation
    GENERAL.PRODUCT:                        Wireless 8260 (Dual Band Wireless-AC 8260)
    GENERAL.DRIVER:                         iwlwifi
    GENERAL.DRIVER-VERSION:                 4.15.0-32-generic
    GENERAL.FIRMWARE-VERSION:               34.0.1
    GENERAL.HWADDR:                         <MAC address>
    GENERAL.MTU:                            1500
    GENERAL.STATE:                          20 (unavailable)
    GENERAL.REASON:                         2 (Device is now managed)
    GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.3/0000:02:00.0/net/wlp2s0
    GENERAL.IP-IFACE:                       --
    GENERAL.IS-SOFTWARE:                    no
    GENERAL.NM-MANAGED:                     yes
    GENERAL.AUTOCONNECT:                    yes
    GENERAL.FIRMWARE-MISSING:               no
    GENERAL.NM-PLUGIN-MISSING:              no
    GENERAL.PHYS-PORT-ID:                   --
    GENERAL.CONNECTION:                     --
    GENERAL.CON-UUID:                       --
    GENERAL.CON-PATH:                       --
    GENERAL.METERED:                        unknown
    CAPABILITIES.CARRIER-DETECT:            no
    CAPABILITIES.SPEED:                     unknown
    CAPABILITIES.IS-SOFTWARE:               no
    CAPABILITIES.SRIOV:                     no
    WIFI-PROPERTIES.WEP:                    yes
    WIFI-PROPERTIES.WPA:                    yes
    WIFI-PROPERTIES.WPA2:                   yes
    WIFI-PROPERTIES.TKIP:                   yes
    WIFI-PROPERTIES.CCMP:                   yes
    WIFI-PROPERTIES.AP:                     yes
    WIFI-PROPERTIES.ADHOC:                  yes
    WIFI-PROPERTIES.2GHZ:                   yes
    WIFI-PROPERTIES.5GHZ:                   yes
    CONNECTIONS.AVAILABLE-CONNECTION-PATHS: --
    
    SSID  BSSID  MODE  CHAN  FREQ  RATE  SIGNAL  BARS  SECURITY  ACTIVE  IN-USE 
    
    ##### NetworkManager.state ##############
    
    [main]
    NetworkingEnabled=true
    WirelessEnabled=true
    WWANEnabled=true
    
    ##### NetworkManager.conf ###############
    
    [main]
    plugins=ifupdown,keyfile
    
    [ifupdown]
    managed=false
    
    [device]
    wifi.scan-rand-mac-address=no
    
    ##### NetworkManager profiles ###########
    
    [[/etc/NetworkManager/system-connections/DIRECT-27CF9851]] (600 root)
    [connection] id=DIRECT-27CF9851 | type=wifi | permissions=user:wald_f:;
    [wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=DIRECT-27CF9851
    [ipv4] method=auto
    [ipv6] method=auto
    
    [[/etc/NetworkManager/system-connections/cre_profs 1]] (600 root)
    [connection] id=cre_profs 1 | type=wifi | permissions=user:wald_f:;
    [wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=cre_profs
    [ipv4] method=auto
    [ipv6] method=auto
    
    [[/etc/NetworkManager/system-connections/eduroam]] (600 root)
    [connection] id=eduroam | type=wifi | permissions=user:ubuntu:;
    [wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=eduroam
    [ipv4] method=auto
    [ipv6] method=auto
    
    [[/etc/NetworkManager/system-connections/public]] (600 root)
    [connection] id=public | type=wifi | permissions=user:wald_f:;
    [wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=public
    [ipv4] method=auto
    [ipv6] method=auto
    
    [[/etc/NetworkManager/system-connections/eduroam 1]] (600 root)
    [connection] id=eduroam 1 | type=wifi | permissions=user:wald_f:;
    [wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=eduroam
    [ipv4] method=auto
    [ipv6] method=auto
    
    [[/etc/NetworkManager/system-connections/fabien]] (600 root)
    [connection] id=fabien | type=wifi | permissions=
    [wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=fabien
    [ipv4] method=auto
    [ipv6] method=auto
    
    [[/etc/NetworkManager/system-connections/cre-profs2]] (600 root)
    [connection] id=cre-profs2 | type=wifi | permissions=user:wald_f:;
    [wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=cre-profs2
    [ipv4] method=auto
    [ipv6] method=auto
    
    [[/etc/NetworkManager/system-connections/freebox_estelle]] (600 root)
    [connection] id=freebox_estelle | type=wifi | permissions=
    [wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=freebox_estelle
    [ipv4] method=auto
    [ipv6] method=auto
    
    [[/etc/NetworkManager/system-connections/PDA_ADET]] (600 root)
    [connection] id=PDA_ADET | type=wifi | permissions=user:wald_f:;
    [wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=PDA_ADET
    [ipv4] method=auto
    [ipv6] method=auto
    
    [[/etc/NetworkManager/system-connections/orange]] (600 root)
    [connection] id=orange | type=wifi | permissions=user:wald_f:;
    [wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=orange
    [ipv4] method=auto
    [ipv6] method=auto
    
    [[/etc/NetworkManager/system-connections/SFR WiFi FON]] (600 root)
    [connection] id=SFR WiFi FON | type=wifi | permissions=user:wald_f:;
    [wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=SFR WiFi FON
    [ipv4] method=auto
    [ipv6] method=auto
    
    [[/etc/NetworkManager/system-connections/iciwifi]] (600 root)
    [connection] id=iciwifi | type=wifi | permissions=user:wald_f:;
    [wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=iciwifi
    [ipv4] method=auto
    [ipv6] method=auto
    
    [[/etc/NetworkManager/system-connections/Houston]] (600 root)
    [connection] id=Houston | type=wifi | permissions=user:wald_f:;
    [wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=Houston
    [ipv4] method=auto
    [ipv6] method=auto
    
    [[/etc/NetworkManager/system-connections/cre_profs]] (600 root)
    [connection] id=cre_profs | type=wifi | autoconnect=false | permissions=
    [wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=cre_profs
    [ipv4] method=shared
    [ipv6] method=auto
    
    [[/etc/NetworkManager/system-connections/Fabien (je vous surveille)]] (600 root)
    [connection] id=Fabien (je vous surveille) | type=wifi | permissions=user:wald_f:;
    [wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=Fabien (je vous surveille)
    [ipv4] method=auto
    [ipv6] method=auto
    
    ##### Netplan config ####################
    
    ##### iw reg get ########################
    
    Region: Europe/Paris (based on set time zone)
    
    global
    country 00: DFS-UNSET
        (2402 - 2472 @ 40), (6, 20), (N/A)
        (2457 - 2482 @ 20), (6, 20), (N/A), AUTO-BW, PASSIVE-SCAN
        (2474 - 2494 @ 20), (6, 20), (N/A), NO-OFDM, PASSIVE-SCAN
        (5170 - 5250 @ 80), (6, 20), (N/A), AUTO-BW, PASSIVE-SCAN
        (5250 - 5330 @ 80), (6, 20), (0 ms), DFS, AUTO-BW, PASSIVE-SCAN
        (5490 - 5730 @ 160), (6, 20), (0 ms), DFS, PASSIVE-SCAN
        (5735 - 5835 @ 80), (6, 20), (N/A), PASSIVE-SCAN
        (57240 - 63720 @ 2160), (N/A, 0), (N/A)
    
    phy#0 (self-managed)
    country FR: DFS-UNSET
        (2402 - 2437 @ 40), (6, 22), (N/A), AUTO-BW, NO-HT40MINUS, NO-80MHZ, NO-160MHZ
        (2422 - 2462 @ 40), (6, 22), (N/A), AUTO-BW, NO-80MHZ, NO-160MHZ
        (2447 - 2482 @ 40), (6, 22), (N/A), AUTO-BW, NO-HT40PLUS, NO-80MHZ, NO-160MHZ
        (5170 - 5190 @ 80), (6, 22), (N/A), NO-OUTDOOR, AUTO-BW, IR-CONCURRENT, NO-HT40MINUS, NO-160MHZ, PASSIVE-SCAN
        (5190 - 5210 @ 80), (6, 22), (N/A), NO-OUTDOOR, AUTO-BW, IR-CONCURRENT, NO-HT40PLUS, NO-160MHZ, PASSIVE-SCAN
        (5210 - 5230 @ 80), (6, 22), (N/A), NO-OUTDOOR, AUTO-BW, IR-CONCURRENT, NO-HT40MINUS, NO-160MHZ, PASSIVE-SCAN
        (5230 - 5250 @ 80), (6, 22), (N/A), NO-OUTDOOR, AUTO-BW, IR-CONCURRENT, NO-HT40PLUS, NO-160MHZ, PASSIVE-SCAN
        (5250 - 5270 @ 80), (6, 22), (0 ms), DFS, AUTO-BW, NO-HT40MINUS, NO-160MHZ, PASSIVE-SCAN
        (5270 - 5290 @ 80), (6, 22), (0 ms), DFS, AUTO-BW, NO-HT40PLUS, NO-160MHZ, PASSIVE-SCAN
        (5290 - 5310 @ 80), (6, 22), (0 ms), DFS, AUTO-BW, NO-HT40MINUS, NO-160MHZ, PASSIVE-SCAN
        (5310 - 5330 @ 80), (6, 22), (0 ms), DFS, AUTO-BW, NO-HT40PLUS, NO-160MHZ, PASSIVE-SCAN
        (5490 - 5510 @ 80), (6, 22), (0 ms), DFS, AUTO-BW, NO-HT40MINUS, NO-160MHZ, PASSIVE-SCAN
        (5510 - 5530 @ 80), (6, 22), (0 ms), DFS, AUTO-BW, NO-HT40PLUS, NO-160MHZ, PASSIVE-SCAN
        (5530 - 5550 @ 80), (6, 22), (0 ms), DFS, AUTO-BW, NO-HT40MINUS, NO-160MHZ, PASSIVE-SCAN
        (5550 - 5570 @ 80), (6, 22), (0 ms), DFS, AUTO-BW, NO-HT40PLUS, NO-160MHZ, PASSIVE-SCAN
        (5570 - 5590 @ 80), (6, 22), (0 ms), DFS, AUTO-BW, NO-HT40MINUS, NO-160MHZ, PASSIVE-SCAN
        (5590 - 5610 @ 80), (6, 22), (0 ms), DFS, AUTO-BW, NO-HT40PLUS, NO-160MHZ, PASSIVE-SCAN
        (5610 - 5630 @ 80), (6, 22), (0 ms), DFS, AUTO-BW, NO-HT40MINUS, NO-160MHZ, PASSIVE-SCAN
        (5630 - 5650 @ 80), (6, 22), (0 ms), DFS, AUTO-BW, NO-HT40PLUS, NO-160MHZ, PASSIVE-SCAN
        (5650 - 5670 @ 80), (6, 22), (0 ms), DFS, AUTO-BW, NO-HT40MINUS, NO-160MHZ, PASSIVE-SCAN
        (5670 - 5690 @ 80), (6, 22), (0 ms), DFS, AUTO-BW, NO-HT40PLUS, NO-160MHZ, PASSIVE-SCAN
        (5690 - 5710 @ 80), (6, 22), (0 ms), DFS, AUTO-BW, NO-HT40MINUS, NO-160MHZ, PASSIVE-SCAN
        (5710 - 5730 @ 80), (6, 22), (0 ms), DFS, AUTO-BW, NO-HT40PLUS, NO-160MHZ, PASSIVE-SCAN
        (5735 - 5755 @ 80), (6, 22), (N/A), AUTO-BW, NO-HT40MINUS, NO-160MHZ
        (5755 - 5775 @ 80), (6, 22), (N/A), AUTO-BW, NO-HT40PLUS, NO-160MHZ
        (5775 - 5795 @ 80), (6, 22), (N/A), AUTO-BW, NO-HT40MINUS, NO-160MHZ
        (5795 - 5815 @ 80), (6, 22), (N/A), AUTO-BW, NO-HT40PLUS, NO-160MHZ
        (5815 - 5835 @ 20), (6, 22), (N/A), AUTO-BW, NO-HT40MINUS, NO-HT40PLUS, NO-80MHZ, NO-160MHZ
    
    ##### iwlist channels ###################
    
    enp0s31f6  no frequency information.
    
    lo        no frequency information.
    
    wlp2s0    32 channels in total; available frequencies :
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
    
    ##### iwlist scan #######################
    
    enp0s31f6  Interface doesn't support scanning.
    
    lo        Interface doesn't support scanning.
    
    wlp2s0    Failed to read scan data : Network is down
    
    ##### module infos ######################
    
    [iwlmvm]
    filename:       /lib/modules/4.15.0-32-generic/kernel/drivers/net/wireless/intel/iwlwifi/mvm/iwlmvm.ko
    license:        GPL
    author:         Copyright(c) 2003- 2015 Intel Corporation <linuxwifi@intel.com>
    description:    The new Intel(R) wireless AGN driver for Linux
    srcversion:     8459DFE0C7E84CD497647AA
    depends:        iwlwifi,mac80211,cfg80211
    retpoline:      Y
    intree:         Y
    name:           iwlmvm
    vermagic:       4.15.0-32-generic SMP mod_unload 
    signat:         PKCS#7
    signer:         
    sig_key:        
    sig_hashalgo:   md4
    parm:           init_dbg:set to true to debug an ASSERT in INIT fw (default: false (bool)
    parm:           power_scheme:power management scheme: 1-active, 2-balanced, 3-low power, default: 2 (int)
    parm:           tfd_q_hang_detect:TFD queues hang detection (default: true (bool)
    
    [mac80211]
    filename:       /lib/modules/4.15.0-32-generic/kernel/net/mac80211/mac80211.ko
    license:        GPL
    description:    IEEE 802.11 subsystem
    srcversion:     1CEA5CF286EDB289C1D0BF8
    depends:        cfg80211
    retpoline:      Y
    intree:         Y
    name:           mac80211
    vermagic:       4.15.0-32-generic SMP mod_unload 
    signat:         PKCS#7
    signer:         
    sig_key:        
    sig_hashalgo:   md4
    parm:           minstrel_vht_only:Use only VHT rates when VHT is supported by sta. (bool)
    parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
    parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
    parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
    parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
    parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)
    
    [iwlwifi]
    filename:       /lib/modules/4.15.0-32-generic/kernel/drivers/net/wireless/intel/iwlwifi/iwlwifi.ko
    license:        GPL
    author:         Copyright(c) 2003- 2015 Intel Corporation <linuxwifi@intel.com>
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
    firmware:       iwlwifi-6000g2a-6.ucode
    firmware:       iwlwifi-6050-5.ucode
    firmware:       iwlwifi-6000-6.ucode
    firmware:       iwlwifi-7265D-29.ucode
    firmware:       iwlwifi-7265-17.ucode
    firmware:       iwlwifi-3168-29.ucode
    firmware:       iwlwifi-3160-17.ucode
    firmware:       iwlwifi-7260-17.ucode
    firmware:       iwlwifi-8265-34.ucode
    firmware:       iwlwifi-8000C-34.ucode
    firmware:       iwlwifi-9260-th-b0-jf-b0-34.ucode
    firmware:       iwlwifi-9260-th-a0-jf-a0-34.ucode
    firmware:       iwlwifi-9000-pu-a0-jf-b0-34.ucode
    firmware:       iwlwifi-9000-pu-b0-jf-b0-34.ucode
    firmware:       iwlwifi-9000-pu-a0-jf-a0-34.ucode
    firmware:       iwlwifi-QuQnj-a0-hr-a0-34.ucode
    firmware:       iwlwifi-QuQnj-a0-jf-b0-34.ucode
    firmware:       iwlwifi-QuQnj-f0-hr-a0-34.ucode
    firmware:       iwlwifi-Qu-a0-jf-b0-34.ucode
    firmware:       iwlwifi-Qu-a0-hr-a0-34.ucode
    srcversion:     6BA065AF04F0DFDB8D91DBF
    depends:        cfg80211
    retpoline:      Y
    intree:         Y
    name:           iwlwifi
    vermagic:       4.15.0-32-generic SMP mod_unload 
    signat:         PKCS#7
    signer:         
    sig_key:        
    sig_hashalgo:   md4
    parm:           swcrypto:using crypto in software (default 0 [hardware]) (int)
    parm:           11n_disable:disable 11n functionality, bitmap: 1: full, 2: disable agg TX, 4: disable agg RX, 8 enable agg TX (uint)
    parm:           amsdu_size:amsdu size 0: 12K for multi Rx queue devices, 4K for other devices 1:4K 2:8K 3:12K (default 0) (int)
    parm:           fw_restart:restart firmware in case of error (default true) (bool)
    parm:           antenna_coupling:specify antenna coupling in dB (default: 0 dB) (int)
    parm:           nvm_file:NVM file name (charp)
    parm:           d0i3_disable:disable d0i3 functionality (default: Y) (bool)
    parm:           lar_disable:disable LAR functionality (default: N) (bool)
    parm:           uapsd_disable:disable U-APSD functionality bitmap 1: BSS 2: P2P Client (default: 3) (uint)
    parm:           bt_coex_active:enable wifi/bt co-exist (default: enable) (bool)
    parm:           led_mode:0=system default, 1=On(RF On)/Off(RF Off), 2=blinking, 3=Off (default: 0) (int)
    parm:           power_save:enable WiFi power management (default: disable) (bool)
    parm:           power_level:default power save level (range from 1 - 5, default: 1) (int)
    parm:           fw_monitor:firmware monitor - to debug FW (default: false - needs lots of memory) (bool)
    parm:           d0i3_timeout:Timeout to D0i3 entry when idle (ms) (uint)
    parm:           disable_11ac:Disable VHT capabilities (default: false) (bool)
    
    [cfg80211]
    filename:       /lib/modules/4.15.0-32-generic/kernel/net/wireless/cfg80211.ko
    description:    wireless configuration support
    license:        GPL
    author:         Johannes Berg
    srcversion:     D5B0789D4C423C81CCFB437
    depends:        
    retpoline:      Y
    intree:         Y
    name:           cfg80211
    vermagic:       4.15.0-32-generic SMP mod_unload 
    signat:         PKCS#7
    signer:         
    sig_key:        
    sig_hashalgo:   md4
    parm:           bss_entries_limit:limit to number of scan BSS entries (per wiphy, default 1000) (int)
    parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
    parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)
    
    ##### module parameters #################
    
    [iwlmvm]
    init_dbg: N
    power_scheme: 2
    tfd_q_hang_detect: Y
    
    [mac80211]
    beacon_loss_count: 7
    ieee80211_default_rc_algo: minstrel_ht
    max_nullfunc_tries: 2
    max_probe_tries: 5
    minstrel_vht_only: Y
    probe_wait_ms: 500
    
    [iwlwifi]
    11n_disable: 0
    amsdu_size: 0
    antenna_coupling: 0
    bt_coex_active: Y
    d0i3_disable: Y
    d0i3_timeout: 1000
    disable_11ac: N
    fw_monitor: N
    fw_restart: Y
    lar_disable: N
    led_mode: 0
    nvm_file: (null)
    power_level: 0
    power_save: N
    swcrypto: 0
    uapsd_disable: 3
    
    [cfg80211]
    bss_entries_limit: 1000
    cfg80211_disable_40mhz_24ghz: N
    ieee80211_regdom: 00
    
    ##### /etc/modules ######################
    
    ##### modprobe options ##################
    
    [/etc/modprobe.d/amd64-microcode-blacklist.conf]
    blacklist microcode
    
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
    
    [/etc/modprobe.d/blacklist-rare-network.conf]
    alias net-pf-3 off
    alias net-pf-6 off
    alias net-pf-9 off
    alias net-pf-11 off
    alias net-pf-12 off
    alias net-pf-19 off
    alias net-pf-21 off
    alias net-pf-36 off
    
    [/etc/modprobe.d/intel-microcode-blacklist.conf]
    blacklist microcode
    
    [/etc/modprobe.d/iwlwifi.conf]
    remove iwlwifi \
    (/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
    && /sbin/modprobe -r mac80211
    
    ##### rc.local ##########################
    
    grep: /etc/rc.local: No such file or directory
    
    ##### pm-utils ##########################
    
    ##### udev rules ########################
    
    ##### dmesg #############################
    
    [ 3719.349962] IPv6: ADDRCONF(NETDEV_UP): wlp2s0: link is not ready (repeated 75 times)
    
    ########## wireless info END ############
```

Thanks a lot

**EDIT 1** : when i do this :

> sudo service network-manager restart

I have this : [https://pastebin.com/Ekj2mUzk](https://pastebin.com/Ekj2mUzk)

---

### Post by devfabien on 2018-08-24
For information, the result of command dmesg when WIFI crash :

```
wald_f@fw-uc9371:~$ dmesg
[    0.000000] microcode: microcode updated early to revision 0xc2, date = 2017-11-16
[    0.000000] Linux version 4.15.0-33-generic (buildd@lcy01-amd64-024) (gcc version 7.3.0 (Ubuntu 7.3.0-16ubuntu3)) #36-Ubuntu SMP Wed Aug 15 16:00:05 UTC 2018 (Ubuntu 4.15.0-33.36-generic 4.15.18)
[    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-4.15.0-33-generic root=UUID=557666b5-bb4f-4e9e-bdda-d59e6e3b85a7 ro quiet splash vt.handoff=1
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   Centaur CentaurHauls
[    0.000000] x86/fpu: Supporting XSAVE feature 0x001: 'x87 floating point registers'
[    0.000000] x86/fpu: Supporting XSAVE feature 0x002: 'SSE registers'
[    0.000000] x86/fpu: Supporting XSAVE feature 0x004: 'AVX registers'
[    0.000000] x86/fpu: Supporting XSAVE feature 0x008: 'MPX bounds registers'
[    0.000000] x86/fpu: Supporting XSAVE feature 0x010: 'MPX CSR'
[    0.000000] x86/fpu: xstate_offset[2]:  576, xstate_sizes[2]:  256
[    0.000000] x86/fpu: xstate_offset[3]:  832, xstate_sizes[3]:   64
[    0.000000] x86/fpu: xstate_offset[4]:  896, xstate_sizes[4]:   64
[    0.000000] x86/fpu: Enabled xstate features 0x1f, context size is 960 bytes, using 'compacted' format.
[    0.000000] e820: BIOS-provided physical RAM map:
[    0.000000] BIOS-e820: [mem 0x0000000000000000-0x000000000009dbff] usable
[    0.000000] BIOS-e820: [mem 0x000000000009dc00-0x000000000009ffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000000e0000-0x00000000000fffff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000000100000-0x00000000c70fafff] usable
[    0.000000] BIOS-e820: [mem 0x00000000c70fb000-0x00000000c7c7efff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000c7c7f000-0x00000000c7e7efff] ACPI NVS
[    0.000000] BIOS-e820: [mem 0x00000000c7e7f000-0x00000000c7efefff] ACPI data
[    0.000000] BIOS-e820: [mem 0x00000000c7eff000-0x00000000c7efffff] usable
[    0.000000] BIOS-e820: [mem 0x00000000c7f00000-0x00000000cc7fffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000f8000000-0x00000000fbffffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fd000000-0x00000000fe7fffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fec00000-0x00000000fec00fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fed00000-0x00000000fed00fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fed10000-0x00000000fed19fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fed84000-0x00000000fed84fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fedf0000-0x00000000fee00fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000ff700000-0x00000000ffffffff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000100000000-0x00000004317fffff] usable
[    0.000000] NX (Execute Disable) protection: active
[    0.000000] SMBIOS 2.7 present.
[    0.000000] DMI: HP HP EliteBook 840 G3/8079, BIOS N75 Ver. 01.13 11/01/2016
[    0.000000] e820: update [mem 0x00000000-0x00000fff] usable ==> reserved
[    0.000000] e820: remove [mem 0x000a0000-0x000fffff] usable
[    0.000000] e820: last_pfn = 0x431800 max_arch_pfn = 0x400000000
[    0.000000] MTRR default type: write-back
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 00E0000000 mask 7FE0000000 uncachable
[    0.000000]   1 base 00D0000000 mask 7FF0000000 uncachable
[    0.000000]   2 base 00CC000000 mask 7FFC000000 uncachable
[    0.000000]   3 base 00CA000000 mask 7FFE000000 uncachable
[    0.000000]   4 disabled
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000]   8 disabled
[    0.000000]   9 disabled
[    0.000000] x86/PAT: Configuration [0-7]: WB  WC  UC- UC  WB  WP  UC- WT  
[    0.000000] e820: last_pfn = 0xc7f00 max_arch_pfn = 0x400000000
[    0.000000] Scanning 1 areas for low memory corruption
[    0.000000] Base memory trampoline at [        (ptrval)] 97000 size 24576
[    0.000000] Using GB pages for direct mapping
[    0.000000] BRK [0x20e53f000, 0x20e53ffff] PGTABLE
[    0.000000] BRK [0x20e540000, 0x20e540fff] PGTABLE
[    0.000000] BRK [0x20e541000, 0x20e541fff] PGTABLE
[    0.000000] BRK [0x20e542000, 0x20e542fff] PGTABLE
[    0.000000] BRK [0x20e543000, 0x20e543fff] PGTABLE
[    0.000000] BRK [0x20e544000, 0x20e544fff] PGTABLE
[    0.000000] BRK [0x20e545000, 0x20e545fff] PGTABLE
[    0.000000] BRK [0x20e546000, 0x20e546fff] PGTABLE
[    0.000000] RAMDISK: [mem 0x31635000-0x34b11fff]
[    0.000000] ACPI: Early table checksum verification disabled
[    0.000000] ACPI: RSDP 0x00000000000FBE30 000024 (v02 HPQOEM)
[    0.000000] ACPI: XSDT 0x00000000C7EBB188 0000D4 (v01 HPQOEM SLIC-BPC 00000000      01000013)
[    0.000000] ACPI: FACP 0x00000000C7EEF000 0000F4 (v05 HPQOEM SLIC-BPC 00000000 HP   00000001)
[    0.000000] ACPI: DSDT 0x00000000C7EC5000 026168 (v02 HPQOEM 8079     00000000 INTL 20121018)
[    0.000000] ACPI: FACS 0x00000000C7E68000 000040
[    0.000000] ACPI: SSDT 0x00000000C7EFC000 000108 (v02 HP     ShmTable 00000001 INTL 20121018)
[    0.000000] ACPI: TCPA 0x00000000C7EFA000 000032 (v02 HPQOEM EDK2     00000002      01000013)
[    0.000000] ACPI: SSDT 0x00000000C7EF9000 0003B8 (v02 HPQOEM TcgTable 00001000 INTL 20121018)
[    0.000000] ACPI: UEFI 0x00000000C7E7A000 000042 (v01 HPQOEM EDK2     00000002      01000013)
[    0.000000] ACPI: SSDT 0x00000000C7EF3000 0051FA (v02 SaSsdt SaSsdt   00003000 INTL 20121018)
[    0.000000] ACPI: SSDT 0x00000000C7EF2000 0005B1 (v01 Intel  PerfTune 00001000 INTL 20121018)
[    0.000000] ACPI: MSDM 0x00000000C7EF1000 000055 (v03 HPQOEM SLIC-BPC 00000000 HP   00000001)
[    0.000000] ACPI: SLIC 0x00000000C7EF0000 000176 (v01 HPQOEM SLIC-BPC 00000001 HP   00000001)
[    0.000000] ACPI: HPET 0x00000000C7EEE000 000038 (v01 HPQOEM 8079     00000001 HP   00000001)
[    0.000000] ACPI: APIC 0x00000000C7EED000 0000BC (v01 HPQOEM 8079     00000001 HP   00000001)
[    0.000000] ACPI: MCFG 0x00000000C7EEC000 00003C (v01 HPQOEM 8079     00000001 HP   00000001)
[    0.000000] ACPI: SSDT 0x00000000C7EC4000 00019A (v02 HPQOEM Sata0Ide 00001000 INTL 20121018)
[    0.000000] ACPI: SSDT 0x00000000C7EC3000 000729 (v01 HPQOEM PtidDevc 00001000 INTL 20121018)
[    0.000000] ACPI: SSDT 0x00000000C7EC2000 0003DC (v02 HPQOEM SDS_RTD3 00001000 INTL 20121018)
[    0.000000] ACPI: SSDT 0x00000000C7EC1000 000E73 (v02 CpuRef CpuSsdt  00003000 INTL 20121018)
[    0.000000] ACPI: SSDT 0x00000000C7EBF000 001B5C (v01 HP     LAPTOPPC 00001000 INTL 20121018)
[    0.000000] ACPI: NHLT 0x00000000C7EBE000 00002D (v00 INTEL  EDK2     00000002      01000013)
[    0.000000] ACPI: ASF! 0x00000000C7EBD000 0000A5 (v32 HPQOEM  UYA     00000001 TFSM 000F4240)
[    0.000000] ACPI: FPDT 0x00000000C7EBC000 000044 (v01 HPQOEM EDK2     00000002      01000013)
[    0.000000] ACPI: BGRT 0x00000000C7EFD000 000038 (v01 HPQOEM EDK2     00000002      01000013)
[    0.000000] ACPI: SSDT 0x00000000C7EFB000 000260 (v02 HP     PwrCtlEv 00000001 INTL 20121018)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at [mem 0x0000000000000000-0x00000004317fffff]
[    0.000000] NODE_DATA(0) allocated [mem 0x4317d5000-0x4317fffff]
[    0.000000] Zone ranges:
[    0.000000]   DMA      [mem 0x0000000000001000-0x0000000000ffffff]
[    0.000000]   DMA32    [mem 0x0000000001000000-0x00000000ffffffff]
[    0.000000]   Normal   [mem 0x0000000100000000-0x00000004317fffff]
[    0.000000]   Device   empty
[    0.000000] Movable zone start for each node
[    0.000000] Early memory node ranges
[    0.000000]   node   0: [mem 0x0000000000001000-0x000000000009cfff]
[    0.000000]   node   0: [mem 0x0000000000100000-0x00000000c70fafff]
[    0.000000]   node   0: [mem 0x00000000c7eff000-0x00000000c7efffff]
[    0.000000]   node   0: [mem 0x0000000100000000-0x00000004317fffff]
[    0.000000] Initmem setup node 0 [mem 0x0000000000001000-0x00000004317fffff]
[    0.000000] On node 0 totalpages: 4163736
[    0.000000]   DMA zone: 64 pages used for memmap
[    0.000000]   DMA zone: 21 pages reserved
[    0.000000]   DMA zone: 3996 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 12676 pages used for memmap
[    0.000000]   DMA32 zone: 811260 pages, LIFO batch:31
[    0.000000]   Normal zone: 52320 pages used for memmap
[    0.000000]   Normal zone: 3348480 pages, LIFO batch:31
[    0.000000] Reserved but unavailable: 100 pages
[    0.000000] Reserving Intel graphics memory at 0x00000000ca800000-0x00000000cc7fffff
[    0.000000] ACPI: PM-Timer IO Port: 0x1808
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x02] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x03] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x04] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x05] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x06] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x07] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x08] high edge lint[0x1])
[    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-119
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
[    0.000000] smpboot: Allowing 4 CPUs, 0 hotplug CPUs
[    0.000000] PM: Registered nosave memory: [mem 0x00000000-0x00000fff]
[    0.000000] PM: Registered nosave memory: [mem 0x0009d000-0x0009dfff]
[    0.000000] PM: Registered nosave memory: [mem 0x0009e000-0x0009ffff]
[    0.000000] PM: Registered nosave memory: [mem 0x000a0000-0x000dffff]
[    0.000000] PM: Registered nosave memory: [mem 0x000e0000-0x000fffff]
[    0.000000] PM: Registered nosave memory: [mem 0xc70fb000-0xc7c7efff]
[    0.000000] PM: Registered nosave memory: [mem 0xc7c7f000-0xc7e7efff]
[    0.000000] PM: Registered nosave memory: [mem 0xc7e7f000-0xc7efefff]
[    0.000000] PM: Registered nosave memory: [mem 0xc7f00000-0xcc7fffff]
[    0.000000] PM: Registered nosave memory: [mem 0xcc800000-0xf7ffffff]
[    0.000000] PM: Registered nosave memory: [mem 0xf8000000-0xfbffffff]
[    0.000000] PM: Registered nosave memory: [mem 0xfc000000-0xfcffffff]
[    0.000000] PM: Registered nosave memory: [mem 0xfd000000-0xfe7fffff]
[    0.000000] PM: Registered nosave memory: [mem 0xfe800000-0xfebfffff]
[    0.000000] PM: Registered nosave memory: [mem 0xfec00000-0xfec00fff]
[    0.000000] PM: Registered nosave memory: [mem 0xfec01000-0xfecfffff]
[    0.000000] PM: Registered nosave memory: [mem 0xfed00000-0xfed00fff]
[    0.000000] PM: Registered nosave memory: [mem 0xfed01000-0xfed0ffff]
[    0.000000] PM: Registered nosave memory: [mem 0xfed10000-0xfed19fff]
[    0.000000] PM: Registered nosave memory: [mem 0xfed1a000-0xfed83fff]
[    0.000000] PM: Registered nosave memory: [mem 0xfed84000-0xfed84fff]
[    0.000000] PM: Registered nosave memory: [mem 0xfed85000-0xfedeffff]
[    0.000000] PM: Registered nosave memory: [mem 0xfedf0000-0xfee00fff]
[    0.000000] PM: Registered nosave memory: [mem 0xfee01000-0xff6fffff]
[    0.000000] PM: Registered nosave memory: [mem 0xff700000-0xffffffff]
[    0.000000] e820: [mem 0xcc800000-0xf7ffffff] available for PCI devices
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] clocksource: refined-jiffies: mask: 0xffffffff max_cycles: 0xffffffff, max_idle_ns: 7645519600211568 ns
[    0.000000] random: get_random_bytes called from start_kernel+0x99/0x4fd with crng_init=0
[    0.000000] setup_percpu: NR_CPUS:8192 nr_cpumask_bits:4 nr_cpu_ids:4 nr_node_ids:1
[    0.000000] percpu: Embedded 46 pages/cpu @        (ptrval) s151552 r8192 d28672 u524288
[    0.000000] pcpu-alloc: s151552 r8192 d28672 u524288 alloc=1*2097152
[    0.000000] pcpu-alloc: [0] 0 1 2 3 
[    0.000000] Built 1 zonelists, mobility grouping on.  Total pages: 4098655
[    0.000000] Policy zone: Normal
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-4.15.0-33-generic root=UUID=557666b5-bb4f-4e9e-bdda-d59e6e3b85a7 ro quiet splash vt.handoff=1
[    0.000000] Calgary: detecting Calgary via BIOS EBDA area
[    0.000000] Calgary: Unable to locate Rio Grande table in EBDA - bailing!
[    0.000000] Memory: 16243716K/16654944K available (12300K kernel code, 2470K rwdata, 4244K rodata, 2408K init, 2416K bss, 411228K reserved, 0K cma-reserved)
[    0.000000] SLUB: HWalign=64, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
[    0.000000] Kernel/User page tables isolation: enabled
[    0.000000] ftrace: allocating 39121 entries in 153 pages
[    0.000000] Hierarchical RCU implementation.
[    0.000000]     RCU restricting CPUs from NR_CPUS=8192 to nr_cpu_ids=4.
[    0.000000]     Tasks RCU enabled.
[    0.000000] RCU: Adjusting geometry for rcu_fanout_leaf=16, nr_cpu_ids=4
[    0.000000] NR_IRQS: 524544, nr_irqs: 1024, preallocated irqs: 16
[    0.000000] vt handoff: transparent VT on vt#1
[    0.000000] Console: colour dummy device 80x25
[    0.000000] console [tty0] enabled
[    0.000000] ACPI: Core revision 20170831
[    0.000000] ACPI: 11 ACPI AML tables successfully acquired and loaded
[    0.000000] clocksource: hpet: mask: 0xffffffff max_cycles: 0xffffffff, max_idle_ns: 79635855245 ns
[    0.000000] hpet clockevent registered
[    0.004000] APIC: Switch to symmetric I/O mode setup
[    0.004000] x2apic: IRQ remapping doesn't support X2APIC mode
[    0.008000] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.028000] tsc: Detected 2800.000 MHz processor
[    0.028000] tsc: Detected 2808.000 MHz TSC
[    0.028000] Calibrating delay loop (skipped), value calculated using timer frequency.. 5616.00 BogoMIPS (lpj=11232000)
[    0.028000] pid_max: default: 32768 minimum: 301
[    0.028000] Security Framework initialized
[    0.028000] Yama: becoming mindful.
[    0.028000] AppArmor: AppArmor initialized
[    0.028000] Dentry cache hash table entries: 2097152 (order: 12, 16777216 bytes)
[    0.033873] Inode-cache hash table entries: 1048576 (order: 11, 8388608 bytes)
[    0.033938] Mount-cache hash table entries: 32768 (order: 6, 262144 bytes)
[    0.033994] Mountpoint-cache hash table entries: 32768 (order: 6, 262144 bytes)
[    0.034187] ENERGY_PERF_BIAS: Set to 'normal', was 'performance'
[    0.034188] ENERGY_PERF_BIAS: View and update with x86_energy_perf_policy(8)
[    0.034192] mce: CPU supports 8 MCE banks
[    0.034200] CPU0: Thermal monitoring enabled (TM1)
[    0.034212] process: using mwait in idle threads
[    0.034214] Last level iTLB entries: 4KB 64, 2MB 8, 4MB 8
[    0.034215] Last level dTLB entries: 4KB 64, 2MB 0, 4MB 0, 1GB 4
[    0.034216] Spectre V2 : Mitigation: Full generic retpoline
[    0.034217] Spectre V2 : Spectre v2 mitigation: Filling RSB on context switch
[    0.034217] Spectre V2 : Spectre v2 mitigation: Enabling Indirect Branch Prediction Barrier
[    0.034217] Spectre V2 : Enabling Restricted Speculation for firmware calls
[    0.034218] Speculative Store Bypass: Vulnerable
[    0.040977] Freeing SMP alternatives memory: 36K
[    0.042999] TSC deadline timer enabled
[    0.043003] smpboot: CPU0: Intel(R) Core(TM) i7-6600U CPU @ 2.60GHz (family: 0x6, model: 0x4e, stepping: 0x3)
[    0.043049] Performance Events: PEBS fmt3+, Skylake events, 32-deep LBR, full-width counters, Intel PMU driver.
[    0.043073] ... version:                4
[    0.043073] ... bit width:              48
[    0.043073] ... generic registers:      4
[    0.043074] ... value mask:             0000ffffffffffff
[    0.043074] ... max period:             00007fffffffffff
[    0.043075] ... fixed-purpose events:   3
[    0.043075] ... event mask:             000000070000000f
[    0.043105] Hierarchical SRCU implementation.
[    0.043912] NMI watchdog: Enabled. Permanently consumes one hw-PMU counter.
[    0.043922] smp: Bringing up secondary CPUs ...
[    0.043977] x86: Booting SMP configuration:
[    0.043978] .... node  #0, CPUs:      #1 #2 #3
[    0.044008] smp: Brought up 1 node, 4 CPUs
[    0.044008] smpboot: Max logical packages: 1
[    0.044008] smpboot: Total of 4 processors activated (22464.00 BogoMIPS)
[    0.047424] devtmpfs: initialized
[    0.047424] x86/mm: Memory block size: 128MB
[    0.048916] evm: security.selinux
[    0.048916] evm: security.SMACK64
[    0.048916] evm: security.SMACK64EXEC
[    0.048917] evm: security.SMACK64TRANSMUTE
[    0.048917] evm: security.SMACK64MMAP
[    0.048918] evm: security.apparmor
[    0.048918] evm: security.ima
[    0.048918] evm: security.capability
[    0.048929] PM: Registering ACPI NVS region [mem 0xc7c7f000-0xc7e7efff] (2097152 bytes)
[    0.048929] clocksource: jiffies: mask: 0xffffffff max_cycles: 0xffffffff, max_idle_ns: 7645041785100000 ns
[    0.048929] futex hash table entries: 1024 (order: 4, 65536 bytes)
[    0.048929] pinctrl core: initialized pinctrl subsystem
[    0.048929] RTC time: 13:44:13, date: 08/24/18
[    0.048929] NET: Registered protocol family 16
[    0.048929] audit: initializing netlink subsys (disabled)
[    0.048929] audit: type=2000 audit(1535118253.048:1): state=initialized audit_enabled=0 res=1
[    0.048929] cpuidle: using governor ladder
[    0.048929] cpuidle: using governor menu
[    0.048929] ACPI FADT declares the system doesn't support PCIe ASPM, so disable it
[    0.048929] ACPI: bus type PCI registered
[    0.048929] acpiphp: ACPI Hot Plug PCI Controller Driver version: 0.5
[    0.048929] PCI: MMCONFIG for domain 0000 [bus 00-3f] at [mem 0xf8000000-0xfbffffff] (base 0xf8000000)
[    0.048929] PCI: MMCONFIG at [mem 0xf8000000-0xfbffffff] reserved in E820
[    0.048929] PCI: Using configuration type 1 for base access
[    0.048938] HugeTLB registered 1.00 GiB page size, pre-allocated 0 pages
[    0.048938] HugeTLB registered 2.00 MiB page size, pre-allocated 0 pages
[    0.048938] ACPI: Added _OSI(Module Device)
[    0.048938] ACPI: Added _OSI(Processor Device)
[    0.048938] ACPI: Added _OSI(3.0 _SCP Extensions)
[    0.048938] ACPI: Added _OSI(Processor Aggregator Device)
[    0.048938] ACPI: Added _OSI(Linux-Dell-Video)
[    0.052056] ACPI: Executed 17 blocks of module-level executable AML code
[    0.063901] ACPI: [Firmware Bug]: BIOS _OSI(Linux) query ignored
[    0.069006] ACPI: Dynamic OEM Table Load:
[    0.069016] ACPI: SSDT 0xFFFF8C05DE9B5000 0006A2 (v02 PmRef  Cpu0Ist  00003000 INTL 20121018)
[    0.069319] ACPI: \_PR_.CPU0: _OSC native thermal LVT Acked
[    0.070470] ACPI: Dynamic OEM Table Load:
[    0.070475] ACPI: SSDT 0xFFFF8C05DEA2D400 00037F (v02 PmRef  Cpu0Cst  00003001 INTL 20121018)
[    0.070810] ACPI: Dynamic OEM Table Load:
[    0.070814] ACPI: SSDT 0xFFFF8C05DEA28240 00008E (v02 PmRef  Cpu0Hwp  00003000 INTL 20121018)
[    0.071062] ACPI: Dynamic OEM Table Load:
[    0.071065] ACPI: SSDT 0xFFFF8C05DEA31A00 000130 (v02 PmRef  HwpLvt   00003000 INTL 20121018)
[    0.071828] ACPI: Dynamic OEM Table Load:
[    0.071834] ACPI: SSDT 0xFFFF8C05DE9B2800 0005AA (v02 PmRef  ApIst    00003000 INTL 20121018)
[    0.072438] ACPI: Dynamic OEM Table Load:
[    0.072442] ACPI: SSDT 0xFFFF8C05DEA30600 000119 (v02 PmRef  ApHwp    00003000 INTL 20121018)
[    0.072778] ACPI: Dynamic OEM Table Load:
[    0.072782] ACPI: SSDT 0xFFFF8C05DEA30C00 000119 (v02 PmRef  ApCst    00003000 INTL 20121018)
[    0.074648] ACPI: EC: EC started
[    0.074649] ACPI: EC: interrupt blocked
[    3.372312] ACPI: \_SB_.PCI0.LPCB.EC0_: Used as first EC
[    3.372313] ACPI: \_SB_.PCI0.LPCB.EC0_: GPE=0x6e, EC_CMD/EC_SC=0x66, EC_DATA=0x62
[    3.372315] ACPI: \_SB_.PCI0.LPCB.EC0_: Used as boot DSDT EC to handle transactions
[    3.372315] ACPI: Interpreter enabled
[    3.372363] ACPI: (supports S0 S3 S4 S5)
[    3.372364] ACPI: Using IOAPIC for interrupt routing
[    3.372403] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    3.373071] ACPI: GPE 0x23 active on init
[    3.373122] ACPI: Enabled 8 GPEs in block 00 to 7F
[    3.373861] ACPI: Power Resource [PG01] (on)
[    3.373861] ACPI: Power Resource [PG02] (on)
[    3.373861] ACPI: Power Resource [PG00] (on)
[    3.378786] ACPI: Power Resource [WRST] (on)
[    3.379013] ACPI: Power Resource [PXP] (on)
[    3.512695] ACPI: Power Resource [WRST] (on)
[    3.513198] ACPI: Power Resource [WRST] (on)
[    3.513785] ACPI: Power Resource [WRST] (on)
[    3.514274] ACPI: Power Resource [WRST] (on)
[    3.514793] ACPI: Power Resource [WRST] (on)
[    3.515279] ACPI: Power Resource [WRST] (on)
[    3.515772] ACPI: Power Resource [WRST] (on)
[    3.516266] ACPI: Power Resource [WRST] (on)
[    3.516755] ACPI: Power Resource [WRST] (on)
[    3.517241] ACPI: Power Resource [WRST] (on)
[    3.517726] ACPI: Power Resource [WRST] (on)
[    3.518188] ACPI: Power Resource [WRST] (on)
[    3.518644] ACPI: Power Resource [WRST] (on)
[    3.519097] ACPI: Power Resource [WRST] (on)
[    3.519558] ACPI: Power Resource [WRST] (on)
[    3.520015] ACPI: Power Resource [WRST] (on)
[    3.520472] ACPI: Power Resource [WRST] (on)
[    3.520934] ACPI: Power Resource [WRST] (on)
[    3.521396] ACPI: Power Resource [WRST] (on)
[    3.532107] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-3e])
[    3.532117] acpi PNP0A08:00: _OSC: OS supports [ExtendedConfig ASPM ClockPM Segments MSI]
[    3.535262] acpi PNP0A08:00: _OSC: OS now controls [PCIeHotplug PME AER PCIeCapability]
[    3.535263] acpi PNP0A08:00: FADT indicates ASPM is unsupported, using BIOS configuration
[    3.537254] PCI host bridge to bus 0000:00
[    3.537256] pci_bus 0000:00: root bus resource [io  0x0000-0x0cf7 window]
[    3.537257] pci_bus 0000:00: root bus resource [io  0x0d00-0xffff window]
[    3.537258] pci_bus 0000:00: root bus resource [mem 0x000a0000-0x000bffff window]
[    3.537259] pci_bus 0000:00: root bus resource [mem 0xcc800000-0xf7ffffff window]
[    3.537260] pci_bus 0000:00: root bus resource [mem 0xfd000000-0xfe7fffff window]
[    3.537262] pci_bus 0000:00: root bus resource [bus 00-3e]
[    3.537271] pci 0000:00:00.0: [8086:1904] type 00 class 0x060000
[    3.537954] pci 0000:00:02.0: [8086:1916] type 00 class 0x030000
[    3.537965] pci 0000:00:02.0: reg 0x10: [mem 0xe0000000-0xe0ffffff 64bit]
[    3.537970] pci 0000:00:02.0: reg 0x18: [mem 0xd0000000-0xdfffffff 64bit pref]
[    3.537974] pci 0000:00:02.0: reg 0x20: [io  0x3000-0x303f]
[    3.538716] pci 0000:00:14.0: [8086:9d2f] type 00 class 0x0c0330
[    3.538734] pci 0000:00:14.0: reg 0x10: [mem 0xe1220000-0xe122ffff 64bit]
[    3.538792] pci 0000:00:14.0: PME# supported from D3hot D3cold
[    3.539527] pci 0000:00:14.2: [8086:9d31] type 00 class 0x118000
[    3.539547] pci 0000:00:14.2: reg 0x10: [mem 0xe124b000-0xe124bfff 64bit]
[    3.540325] pci 0000:00:15.0: [8086:9d60] type 00 class 0x118000
[    3.540411] pci 0000:00:15.0: reg 0x10: [mem 0xe124c000-0xe124cfff 64bit]
[    3.541412] pci 0000:00:16.0: [8086:9d3a] type 00 class 0x078000
[    3.541437] pci 0000:00:16.0: reg 0x10: [mem 0xe124d000-0xe124dfff 64bit]
[    3.541500] pci 0000:00:16.0: PME# supported from D3hot
[    3.542185] pci 0000:00:16.3: [8086:9d3d] type 00 class 0x070002
[    3.542202] pci 0000:00:16.3: reg 0x10: [io  0x3080-0x3087]
[    3.542209] pci 0000:00:16.3: reg 0x14: [mem 0xe124a000-0xe124afff]
[    3.542926] pci 0000:00:17.0: [8086:9d03] type 00 class 0x010601
[    3.542943] pci 0000:00:17.0: reg 0x10: [mem 0xe1248000-0xe1249fff]
[    3.542950] pci 0000:00:17.0: reg 0x14: [mem 0xe1250000-0xe12500ff]
[    3.542957] pci 0000:00:17.0: reg 0x18: [io  0x3088-0x308f]
[    3.542963] pci 0000:00:17.0: reg 0x1c: [io  0x3090-0x3093]
[    3.542969] pci 0000:00:17.0: reg 0x20: [io  0x3040-0x305f]
[    3.542975] pci 0000:00:17.0: reg 0x24: [mem 0xe124e000-0xe124e7ff]
[    3.543013] pci 0000:00:17.0: PME# supported from D3hot
[    3.543708] pci 0000:00:1c.0: [8086:9d11] type 01 class 0x060400
[    3.543773] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    3.544505] pci 0000:00:1c.3: [8086:9d13] type 01 class 0x060400
[    3.544571] pci 0000:00:1c.3: PME# supported from D0 D3hot D3cold
[    3.545305] pci 0000:00:1f.0: [8086:9d48] type 00 class 0x060100
[    3.546056] pci 0000:00:1f.2: [8086:9d21] type 00 class 0x058000
[    3.546071] pci 0000:00:1f.2: reg 0x10: [mem 0xe1240000-0xe1243fff]
[    3.546805] pci 0000:00:1f.3: [8086:9d70] type 00 class 0x040380
[    3.546832] pci 0000:00:1f.3: reg 0x10: [mem 0xe1244000-0xe1247fff 64bit]
[    3.546863] pci 0000:00:1f.3: reg 0x20: [mem 0xe1230000-0xe123ffff 64bit]
[    3.546914] pci 0000:00:1f.3: PME# supported from D3hot D3cold
[    3.547630] pci 0000:00:1f.4: [8086:9d23] type 00 class 0x0c0500
[    3.547689] pci 0000:00:1f.4: reg 0x10: [mem 0xe124f000-0xe124f0ff 64bit]
[    3.547759] pci 0000:00:1f.4: reg 0x20: [io  0xefa0-0xefbf]
[    3.548519] pci 0000:00:1f.6: [8086:156f] type 00 class 0x020000
[    3.548542] pci 0000:00:1f.6: reg 0x10: [mem 0xe1200000-0xe121ffff]
[    3.548636] pci 0000:00:1f.6: PME# supported from D0 D3hot D3cold
[    3.549388] pci 0000:01:00.0: [10ec:522a] type 00 class 0xff0000
[    3.549419] pci 0000:01:00.0: reg 0x10: [mem 0xe1000000-0xe1000fff]
[    3.549580] pci 0000:01:00.0: supports D1 D2
[    3.549581] pci 0000:01:00.0: PME# supported from D1 D2 D3hot D3cold
[    3.564090] pci 0000:00:1c.0: PCI bridge to [bus 01]
[    3.564094] pci 0000:00:1c.0:   bridge window [mem 0xe1000000-0xe10fffff]
[    3.564253] pci 0000:02:00.0: [8086:24f3] type 00 class 0x028000
[    3.564351] pci 0000:02:00.0: reg 0x10: [mem 0xe1100000-0xe1101fff 64bit]
[    3.564639] pci 0000:02:00.0: PME# supported from D0 D3hot D3cold
[    3.580086] pci 0000:00:1c.3: PCI bridge to [bus 02]
[    3.580091] pci 0000:00:1c.3:   bridge window [mem 0xe1100000-0xe11fffff]
[    3.582503] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 10 *11 12 14 15)
[    3.582585] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 *10 11 12 14 15)
[    3.582660] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 10 *11 12 14 15)
[    3.582734] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 10 *11 12 14 15)
[    3.582809] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 10 *11 12 14 15)
[    3.582883] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 10 *11 12 14 15)
[    3.582957] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 10 *11 12 14 15)
[    3.583031] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 10 *11 12 14 15)
[    3.584001] ACPI: EC: interrupt unblocked
[    3.584001] ACPI: EC: event unblocked
[    3.584001] ACPI: \_SB_.PCI0.LPCB.EC0_: GPE=0x6e, EC_CMD/EC_SC=0x66, EC_DATA=0x62
[    3.584001] ACPI: \_SB_.PCI0.LPCB.EC0_: Used as boot DSDT EC to handle transactions and events
[    3.584001] SCSI subsystem initialized
[    3.584011] libata version 3.00 loaded.
[    3.584018] pci 0000:00:02.0: vgaarb: setting as boot VGA device
[    3.584018] pci 0000:00:02.0: vgaarb: VGA device added: decodes=io+mem,owns=io+mem,locks=none
[    3.584018] pci 0000:00:02.0: vgaarb: bridge control possible
[    3.584018] vgaarb: loaded
[    3.584023] ACPI: bus type USB registered
[    3.584034] usbcore: registered new interface driver usbfs
[    3.584040] usbcore: registered new interface driver hub
[    3.584061] usbcore: registered new device driver usb
[    3.584092] EDAC MC: Ver: 3.0.0
[    3.584092] PCI: Using ACPI for IRQ routing
[    3.591147] PCI: pci_cache_line_size set to 64 bytes
[    3.591333] e820: reserve RAM buffer [mem 0x0009dc00-0x0009ffff]
[    3.591334] e820: reserve RAM buffer [mem 0xc70fb000-0xc7ffffff]
[    3.591335] e820: reserve RAM buffer [mem 0xc7f00000-0xc7ffffff]
[    3.591335] e820: reserve RAM buffer [mem 0x431800000-0x433ffffff]
[    3.591400] NetLabel: Initializing
[    3.591400] NetLabel:  domain hash size = 128
[    3.591401] NetLabel:  protocols = UNLABELED CIPSOv4 CALIPSO
[    3.591413] NetLabel:  unlabeled traffic allowed by default
[    3.592317] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0, 0, 0, 0, 0
[    3.592321] hpet0: 8 comparators, 64-bit 24.000000 MHz counter
[    3.598039] clocksource: Switched to clocksource hpet
[    3.604548] VFS: Disk quotas dquot_6.6.0
[    3.604560] VFS: Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    3.604636] AppArmor: AppArmor Filesystem Enabled
[    3.604652] pnp: PnP ACPI init
[    3.604828] system 00:00: [mem 0xfd000000-0xfdabffff] has been reserved
[    3.604829] system 00:00: [mem 0xfdad0000-0xfdadffff] has been reserved
[    3.604831] system 00:00: [mem 0xfdb00000-0xfdffffff] has been reserved
[    3.604832] system 00:00: [mem 0xfe000000-0xfe01ffff] has been reserved
[    3.604833] system 00:00: [mem 0xfe03d000-0xfe3fffff] has been reserved
[    3.604837] system 00:00: Plug and Play ACPI device, IDs PNP0c02 (active)
[    3.605120] system 00:01: [io  0x2000-0x20fe] has been reserved
[    3.605122] system 00:01: Plug and Play ACPI device, IDs PNP0c02 (active)
[    3.605348] system 00:02: [io  0x0680-0x069f] has been reserved
[    3.605349] system 00:02: [io  0xffff] has been reserved
[    3.605350] system 00:02: [io  0xffff] has been reserved
[    3.605351] system 00:02: [io  0xffff] has been reserved
[    3.605352] system 00:02: [io  0x1800-0x18fe] has been reserved
[    3.605353] system 00:02: [io  0x164e-0x164f] has been reserved
[    3.605356] system 00:02: Plug and Play ACPI device, IDs PNP0c02 (active)
[    3.605442] pnp 00:03: Plug and Play ACPI device, IDs PNP0b00 (active)
[    3.605471] system 00:04: [io  0x1854-0x1857] has been reserved
[    3.605473] system 00:04: Plug and Play ACPI device, IDs INT3f0d PNP0c02 (active)
[    3.605490] pnp 00:05: Plug and Play ACPI device, IDs HPQ8002 PNP0303 (active)
[    3.605525] pnp 00:06: Plug and Play ACPI device, IDs SYN3037 SYN0100 SYN0002 PNP0f13 (active)
[    3.605583] system 00:07: [io  0x0200-0x023f] has been reserved
[    3.605584] system 00:07: [mem 0xfedf0000-0xfedfffff] has been reserved
[    3.605587] system 00:07: Plug and Play ACPI device, IDs PNP0c02 (active)
[    3.606725] system 00:08: [mem 0xfe031000-0xfe031fff] has been reserved
[    3.606726] system 00:08: [mem 0xfe030008-0xfe030fff] has been reserved
[    3.606728] system 00:08: Plug and Play ACPI device, IDs PNP0c02 (active)
[    3.607146] system 00:09: [mem 0xfe030000-0xfe030007] has been reserved
[    3.607148] system 00:09: Plug and Play ACPI device, IDs PNP0c02 (active)
[    3.607404] system 00:0a: [mem 0xfed10000-0xfed17fff] has been reserved
[    3.607407] system 00:0a: [mem 0xfed18000-0xfed18fff] has been reserved
[    3.607408] system 00:0a: [mem 0xfed19000-0xfed19fff] has been reserved
[    3.607409] system 00:0a: [mem 0xf8000000-0xfbffffff] has been reserved
[    3.607410] system 00:0a: [mem 0xfed20000-0xfed3ffff] has been reserved
[    3.607411] system 00:0a: [mem 0xfed90000-0xfed93fff] has been reserved
[    3.607412] system 00:0a: [mem 0xfed45000-0xfed8ffff] could not be reserved
[    3.607414] system 00:0a: [mem 0xff000000-0xffffffff] could not be reserved
[    3.607415] system 00:0a: [mem 0xfee00000-0xfeefffff] could not be reserved
[    3.607416] system 00:0a: [mem 0xcc800000-0xcc81ffff] has been reserved
[    3.607419] system 00:0a: Plug and Play ACPI device, IDs PNP0c02 (active)
[    3.607725] pnp 00:0b: Plug and Play ACPI device, IDs IFX0102 PNP0c31 (active)
[    3.607882] pnp: PnP ACPI: found 12 devices
[    3.615986] clocksource: acpi_pm: mask: 0xffffff max_cycles: 0xffffff, max_idle_ns: 2085701024 ns
[    3.615998] pci 0000:00:1c.0: bridge window [io  0x1000-0x0fff] to [bus 01] add_size 1000
[    3.616000] pci 0000:00:1c.0: bridge window [mem 0x00100000-0x000fffff 64bit pref] to [bus 01] add_size 200000 add_align 100000
[    3.616034] pci 0000:00:1c.0: BAR 15: assigned [mem 0xcc900000-0xccafffff 64bit pref]
[    3.616036] pci 0000:00:1c.0: BAR 13: assigned [io  0x4000-0x4fff]
[    3.616038] pci 0000:00:1c.0: PCI bridge to [bus 01]
[    3.616042] pci 0000:00:1c.0:   bridge window [io  0x4000-0x4fff]
[    3.616045] pci 0000:00:1c.0:   bridge window [mem 0xe1000000-0xe10fffff]
[    3.616047] pci 0000:00:1c.0:   bridge window [mem 0xcc900000-0xccafffff 64bit pref]
[    3.616051] pci 0000:00:1c.3: PCI bridge to [bus 02]
[    3.616054] pci 0000:00:1c.3:   bridge window [mem 0xe1100000-0xe11fffff]
[    3.616059] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7 window]
[    3.616060] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff window]
[    3.616061] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff window]
[    3.616062] pci_bus 0000:00: resource 7 [mem 0xcc800000-0xf7ffffff window]
[    3.616063] pci_bus 0000:00: resource 8 [mem 0xfd000000-0xfe7fffff window]
[    3.616064] pci_bus 0000:01: resource 0 [io  0x4000-0x4fff]
[    3.616065] pci_bus 0000:01: resource 1 [mem 0xe1000000-0xe10fffff]
[    3.616066] pci_bus 0000:01: resource 2 [mem 0xcc900000-0xccafffff 64bit pref]
[    3.616067] pci_bus 0000:02: resource 1 [mem 0xe1100000-0xe11fffff]
[    3.616196] NET: Registered protocol family 2
[    3.616367] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    3.616632] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    3.616837] TCP: Hash tables configured (established 131072 bind 65536)
[    3.616870] UDP hash table entries: 8192 (order: 6, 262144 bytes)
[    3.616927] UDP-Lite hash table entries: 8192 (order: 6, 262144 bytes)
[    3.617026] NET: Registered protocol family 1
[    3.617038] pci 0000:00:02.0: Video device with shadowed ROM at [mem 0x000c0000-0x000dffff]
[    3.717429] PCI: CLS 0 bytes, default 64
[    3.717456] Unpacking initramfs...
[    4.331881] Freeing initrd memory: 54132K
[    4.331897] PCI-DMA: Using software bounce buffering for IO (SWIOTLB)
[    4.331900] software IO TLB [mem 0xc30fb000-0xc70fb000] (64MB) mapped at [        (ptrval)-        (ptrval)]
[    4.332236] clocksource: tsc: mask: 0xffffffffffffffff max_cycles: 0x2879c5f06f2, max_idle_ns: 440795220049 ns
[    4.332374] Scanning for low memory corruption every 60 seconds
[    4.333031] Initialise system trusted keyrings
[    4.333038] Key type blacklist registered
[    4.333101] workingset: timestamp_bits=36 max_order=22 bucket_order=0
[    4.333962] zbud: loaded
[    4.334364] squashfs: version 4.0 (2009/01/31) Phillip Lougher
[    4.334518] fuse init (API version 7.26)
[    4.337262] Key type asymmetric registered
[    4.337263] Asymmetric key parser 'x509' registered
[    4.337289] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 246)
[    4.337344] io scheduler noop registered
[    4.337344] io scheduler deadline registered
[    4.337378] io scheduler cfq registered (default)
[    4.337987] pcieport 0000:00:1c.0: AER enabled with IRQ 120
[    4.338008] pcieport 0000:00:1c.3: AER enabled with IRQ 121
[    4.338020] pcieport 0000:00:1c.0: Signaling PME with IRQ 120
[    4.338032] pcieport 0000:00:1c.3: Signaling PME with IRQ 121
[    4.338046] pciehp 0000:00:1c.0:pcie004: Slot #1 AttnBtn- PwrCtrl- MRL- AttnInd- PwrInd- HotPlug+ Surprise+ Interlock- NoCompl+ LLActRep+
[    4.338103] vesafb: mode is 1920x1080x32, linelength=7680, pages=0
[    4.338104] vesafb: scrolling: redraw
[    4.338105] vesafb: Truecolor: size=8:8:8:8, shift=24:16:8:0
[    4.338112] vesafb: framebuffer at 0xd0000000, mapped to 0x        (ptrval), using 8128k, total 8128k
[    4.338219] Console: switching to colour frame buffer device 240x67
[    4.338237] fb0: VESA VGA frame buffer device
[    4.338246] intel_idle: MWAIT substates: 0x11142120
[    4.338247] intel_idle: v0.4.1 model 0x4E
[    4.338460] intel_idle: lapic_timer_reliable_states 0xffffffff
[    4.338638] ACPI: AC Adapter [AC] (on-line)
[    4.338692] input: Sleep Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0E:00/input/input0
[    4.338707] ACPI: Sleep Button [SLPB]
[    4.338727] input: Lid Switch as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0D:00/input/input1
[    4.338737] ACPI: Lid Switch [LID]
[    4.338760] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input2
[    4.338811] ACPI: Power Button [PWRF]
[    4.343965] (NULL device *): hwmon_device_register() is deprecated. Please convert the driver to use hwmon_device_register_with_info().
[    4.344537] thermal LNXTHERM:00: registered as thermal_zone0
[    4.344538] ACPI: Thermal Zone [CPUZ] (49 C)
[    4.346951] thermal LNXTHERM:01: registered as thermal_zone1
[    4.346952] ACPI: Thermal Zone [GFXZ] (0 C)
[    4.349785] thermal LNXTHERM:02: registered as thermal_zone2
[    4.349785] ACPI: Thermal Zone [EXTZ] (35 C)
[    4.353001] thermal LNXTHERM:03: registered as thermal_zone3
[    4.353002] ACPI: Thermal Zone [LOCZ] (34 C)
[    4.355765] thermal LNXTHERM:04: registered as thermal_zone4
[    4.355766] ACPI: Thermal Zone [BATZ] (30 C)
[    4.356186] thermal LNXTHERM:05: registered as thermal_zone5
[    4.356187] ACPI: Thermal Zone [PCHZ] (127 C)
[    4.356322] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    4.379677] 0000:00:16.3: ttyS4 at I/O 0x3080 (irq = 19, base_baud = 115200) is a 16550A
[    4.380034] Linux agpgart interface v0.103
[    4.387583] ACPI: Battery Slot [BAT0] (battery present)
[    4.396537] tpm_tis 00:0b: 1.2 TPM (device-id 0x1B, rev-id 16)
[    4.488318] tpm tpm0: A TPM error (7) occurred attempting to read a pcr value
[    4.488322] tpm tpm0: TPM is disabled/deactivated (0x7)
[    4.488325] tpm tpm0: tpm_read_log_acpi: TCPA log area empty
[    4.488347] tpm_tis: probe of 00:0b failed with error -5
[    4.490321] loop: module loaded
[    4.490464] libphy: Fixed MDIO Bus: probed
[    4.490465] tun: Universal TUN/TAP device driver, 1.6
[    4.490527] PPP generic driver version 2.4.2
[    4.490603] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    4.490605] ehci-pci: EHCI PCI platform driver
[    4.490613] ehci-platform: EHCI generic platform driver
[    4.490622] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    4.490624] ohci-pci: OHCI PCI platform driver
[    4.490629] ohci-platform: OHCI generic platform driver
[    4.490635] uhci_hcd: USB Universal Host Controller Interface driver
[    4.490847] xhci_hcd 0000:00:14.0: xHCI Host Controller
[    4.490851] xhci_hcd 0000:00:14.0: new USB bus registered, assigned bus number 1
[    4.491967] xhci_hcd 0000:00:14.0: hcc params 0x200077c1 hci version 0x100 quirks 0x00109810
[    4.491974] xhci_hcd 0000:00:14.0: cache line size of 64 is not supported
[    4.492162] usb usb1: New USB device found, idVendor=1d6b, idProduct=0002
[    4.492164] usb usb1: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    4.492165] usb usb1: Product: xHCI Host Controller
[    4.492166] usb usb1: Manufacturer: Linux 4.15.0-33-generic xhci-hcd
[    4.492167] usb usb1: SerialNumber: 0000:00:14.0
[    4.492280] hub 1-0:1.0: USB hub found
[    4.492298] hub 1-0:1.0: 12 ports detected
[    4.492949] xhci_hcd 0000:00:14.0: xHCI Host Controller
[    4.492952] xhci_hcd 0000:00:14.0: new USB bus registered, assigned bus number 2
[    4.492954] xhci_hcd 0000:00:14.0: Host supports USB 3.0  SuperSpeed
[    4.492986] usb usb2: New USB device found, idVendor=1d6b, idProduct=0003
[    4.492987] usb usb2: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    4.492989] usb usb2: Product: xHCI Host Controller
[    4.492990] usb usb2: Manufacturer: Linux 4.15.0-33-generic xhci-hcd
[    4.492991] usb usb2: SerialNumber: 0000:00:14.0
[    4.493124] hub 2-0:1.0: USB hub found
[    4.493137] hub 2-0:1.0: 6 ports detected
[    4.493398] usb: port power management may be unreliable
[    4.493799] i8042: PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    4.495251] i8042: Detected active multiplexing controller, rev 1.1
[    4.495546] serio: i8042 KBD port at 0x60,0x64 irq 1
[    4.495549] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[    4.495569] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[    4.495584] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[    4.495598] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[    4.495749] mousedev: PS/2 mouse device common for all mice
[    4.496061] rtc_cmos 00:03: RTC can wake from S4
[    4.496469] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0
[    4.496552] rtc_cmos 00:03: alarms up to one month, y3k, 242 bytes nvram, hpet irqs
[    4.496558] i2c /dev entries driver
[    4.496596] device-mapper: uevent: version 1.0.3
[    4.496673] device-mapper: ioctl: 4.37.0-ioctl (2017-09-20) initialised: dm-devel@redhat.com
[    4.496676] intel_pstate: Intel P-state driver initializing
[    4.497300] intel_pstate: HWP enabled
[    4.497541] ledtrig-cpu: registered to indicate activity on CPUs
[    4.498718] intel_pmc_core:  initialized
[    4.498908] NET: Registered protocol family 10
[    4.503693] Segment Routing with IPv6
[    4.503722] NET: Registered protocol family 17
[    4.503795] Key type dns_resolver registered
[    4.504186] RAS: Correctable Errors collector initialized.
[    4.504222] microcode: sig=0x406e3, pf=0x80, revision=0xc2
[    4.504385] microcode: Microcode Update Driver: v2.2.
[    4.504393] sched_clock: Marking stable (4504380412, 0)->(4487130406, 17250006)
[    4.504751] registered taskstats version 1
[    4.504758] Loading compiled-in X.509 certificates
[    4.506540] Loaded X.509 cert 'Build time autogenerated kernel key: b2b2adbda3eef7b219e699c1b87c022096150517'
[    4.506553] zswap: loaded using pool lzo/zbud
[    4.509938] Key type big_key registered
[    4.509940] Key type trusted registered
[    4.511730] Key type encrypted registered
[    4.511733] AppArmor: AppArmor sha1 policy hashing enabled
[    4.511735] ima: No TPM chip found, activating TPM-bypass! (rc=-19)
[    4.511747] evm: HMAC attrs: 0x1
[    4.512905]   Magic number: 14:877:736
[    4.513163] rtc_cmos 00:03: setting system clock to 2018-08-24 13:44:17 UTC (1535118257)
[    4.513220] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    4.513221] EDD information not available.
[    4.521095] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
[    4.832029] usb 1-4: new high-speed USB device number 2 using xhci_hcd
[    4.944964] Freeing unused kernel memory: 2408K
[    4.964499] Write protecting the kernel read-only data: 20480k
[    4.965802] Freeing unused kernel memory: 2008K
[    4.968427] Freeing unused kernel memory: 1900K
[    4.972771] x86/mm: Checked W+X mappings: passed, no W+X pages found.
[    4.972772] x86/mm: Checking user space page tables
[    4.977021] x86/mm: Checked W+X mappings: passed, no W+X pages found.
[    4.984367] usb 1-4: New USB device found, idVendor=0424, idProduct=2134
[    4.984369] usb 1-4: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[    4.984370] usb 1-4: Product: USB2134B
[    4.984371] usb 1-4: Manufacturer: SMSC
[    4.984764] hub 1-4:1.0: USB hub found
[    4.984840] hub 1-4:1.0: 4 ports detected
[    5.062193] acpi PNP0C14:01: duplicate WMI GUID 05901221-D566-11D1-B2F0-00A0C9062910 (first instance was on PNP0C14:00)
[    5.090564] ahci 0000:00:17.0: version 3.0
[    5.090744] ahci 0000:00:17.0: SSS flag set, parallel bus scan disabled
[    5.091224] pps_core: LinuxPPS API ver. 1 registered
[    5.091225] pps_core: Software ver. 5.3.6 - Copyright 2005-2007 Rodolfo Giometti <giometti@linux.it>
[    5.092667] PTP clock support registered
[    5.096894] e1000e: Intel(R) PRO/1000 Network Driver - 3.2.6-k
[    5.096895] e1000e: Copyright(c) 1999 - 2015 Intel Corporation.
[    5.100903] ahci 0000:00:17.0: AHCI 0001.0301 32 slots 2 ports 6 Gbps 0x5 impl SATA mode
[    5.100906] ahci 0000:00:17.0: flags: 64bit ncq stag pm led clo only pio slum part deso sadm sds apst 
[    5.108486] scsi host0: ahci
[    5.108719] scsi host1: ahci
[    5.108828] scsi host2: ahci
[    5.108870] ata1: SATA max UDMA/133 abar m2048@0xe124e000 port 0xe124e100 irq 124
[    5.108871] ata2: DUMMY
[    5.108873] ata3: SATA max UDMA/133 abar m2048@0xe124e000 port 0xe124e200 irq 124
[    5.109365] e1000e 0000:00:1f.6: Interrupt Throttling Rate (ints/sec) set to dynamic conservative mode
[    5.112062] usb 2-4: new SuperSpeed USB device number 2 using xhci_hcd
[    5.132444] usb 2-4: New USB device found, idVendor=0424, idProduct=5534
[    5.132446] usb 2-4: New USB device strings: Mfr=2, Product=3, SerialNumber=0
[    5.132447] usb 2-4: Product: USB5534B
[    5.132448] usb 2-4: Manufacturer: SMSC
[    5.132981] random: fast init done
[    5.133080] hub 2-4:1.0: USB hub found
[    5.133149] random: systemd-udevd: uninitialized urandom read (16 bytes read)
[    5.133155] random: systemd-udevd: uninitialized urandom read (16 bytes read)
[    5.133168] random: systemd-udevd: uninitialized urandom read (16 bytes read)
[    5.133264] hub 2-4:1.0: 4 ports detected
[    5.260190] usb 1-7: new full-speed USB device number 3 using xhci_hcd
[    5.300735] e1000e 0000:00:1f.6 0000:00:1f.6 (uninitialized): registered PHC clock
[    5.350356] clocksource: Switched to clocksource tsc
[    5.369642] e1000e 0000:00:1f.6 eth0: (PCI Express:2.5GT/s:Width x1) 3c:52:82:49:92:51
[    5.369644] e1000e 0000:00:1f.6 eth0: Intel(R) PRO/1000 Network Connection
[    5.369719] e1000e 0000:00:1f.6 eth0: MAC: 12, PHY: 12, PBA No: FFFFFF-0FF
[    5.370358] e1000e 0000:00:1f.6 enp0s31f6: renamed from eth0
[    5.372967] [drm] Memory usable by graphics device = 4096M
[    5.372968] checking generic (d0000000 7f0000) vs hw (d0000000 10000000)
[    5.372969] fb: switching to inteldrmfb from VESA VGA
[    5.372983] Console: switching to colour dummy device 80x25
[    5.373241] [drm] Replacing VGA console driver
[    5.378660] [drm] Supports vblank timestamp caching Rev 2 (21.10.2013).
[    5.378660] [drm] Driver supports precise vblank timestamp query.
[    5.380305] i915 0000:00:02.0: vgaarb: changed VGA decodes: olddecodes=io+mem,decodes=io+mem:owns=io+mem
[    5.380736] [drm] Finished loading DMC firmware i915/skl_dmc_ver1_26.bin (v1.26)
[    5.388380] [drm] Initialized i915 1.6.0 20171023 for 0000:00:02.0 on minor 0
[    5.390416] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
[    5.393133] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/LNXVIDEO:00/input/input10
[    5.412952] usb 1-7: New USB device found, idVendor=8087, idProduct=0a2b
[    5.412973] usb 1-7: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[    5.422162] ata1: SATA link up 6.0 Gbps (SStatus 133 SControl 300)
[    5.422751] ata1.00: ACPI cmd f5/00:00:00:00:00:e0 (SECURITY FREEZE LOCK) filtered out
[    5.422753] ata1.00: ACPI cmd b1/c1:00:00:00:00:e0 (DEVICE CONFIGURATION OVERLAY) filtered out
[    5.432084] ata1.00: ATA-8: ST500LM021-1KJ152, 0002YXM1, max UDMA/133
[    5.432086] ata1.00: 976773168 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
[    5.441235] fbcon: inteldrmfb (fb0) is primary device
[    5.441270] Console: switching to colour frame buffer device 240x67
[    5.441289] i915 0000:00:02.0: fb0: inteldrmfb frame buffer device
[    5.444937] ata1.00: ACPI cmd f5/00:00:00:00:00:e0 (SECURITY FREEZE LOCK) filtered out
[    5.444939] ata1.00: ACPI cmd b1/c1:00:00:00:00:e0 (DEVICE CONFIGURATION OVERLAY) filtered out
[    5.454690] ata1.00: configured for UDMA/133
[    5.454917] scsi 0:0:0:0: Direct-Access     ATA      ST500LM021-1KJ15 YXM1 PQ: 0 ANSI: 5
[    5.455381] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    5.455432] sd 0:0:0:0: [sda] 976773168 512-byte logical blocks: (500 GB/466 GiB)
[    5.455433] sd 0:0:0:0: [sda] 4096-byte physical blocks
[    5.455446] sd 0:0:0:0: [sda] Write Protect is off
[    5.455447] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    5.455486] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    5.492098] usb 1-4.2: new low-speed USB device number 4 using xhci_hcd
[    5.518576]  sda: sda1 sda2 sda3 < sda5 sda6 >
[    5.519462] sd 0:0:0:0: [sda] Attached SCSI disk
[    5.597474] usb 1-4.2: New USB device found, idVendor=413c, idProduct=2107
[    5.597485] usb 1-4.2: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[    5.597493] usb 1-4.2: Product: Dell USB Entry Keyboard
[    5.597501] usb 1-4.2: Manufacturer: DELL
[    5.720078] usb 1-8: new full-speed USB device number 5 using xhci_hcd
[    5.769655] ata3: SATA link up 6.0 Gbps (SStatus 133 SControl 300)
[    5.770951] ata3.00: ACPI cmd f5/00:00:00:00:00:e0 (SECURITY FREEZE LOCK) filtered out
[    5.771068] ata3.00: ATA-9: SanDisk SD8SN8U-256G-1006, X4120006, max UDMA/133
[    5.771069] ata3.00: 500118192 sectors, multi 1: LBA48 NCQ (depth 31/32), AA
[    5.773652] ata3.00: ACPI cmd f5/00:00:00:00:00:e0 (SECURITY FREEZE LOCK) filtered out
[    5.774986] ata3.00: configured for UDMA/133
[    5.775256] scsi 2:0:0:0: Direct-Access     ATA      SanDisk SD8SN8U- 0006 PQ: 0 ANSI: 5
[    5.775716] sd 2:0:0:0: Attached scsi generic sg1 type 0
[    5.775792] sd 2:0:0:0: [sdb] 500118192 512-byte logical blocks: (256 GB/238 GiB)
[    5.775794] sd 2:0:0:0: [sdb] 4096-byte physical blocks
[    5.775806] sd 2:0:0:0: [sdb] Write Protect is off
[    5.775807] sd 2:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[    5.775821] sd 2:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    5.776135]  sdb: sdb1 sdb2 sdb3 sdb4
[    5.776353] sd 2:0:0:0: [sdb] Attached SCSI disk
[    5.869716] usb 1-8: New USB device found, idVendor=138a, idProduct=003f
[    5.869717] usb 1-8: New USB device strings: Mfr=0, Product=0, SerialNumber=1
[    5.869718] usb 1-8: SerialNumber: 003026655a80
[    5.948331] usb 1-4.4: new low-speed USB device number 6 using xhci_hcd
[    6.056906] usb 1-4.4: New USB device found, idVendor=413c, idProduct=3016
[    6.056908] usb 1-4.4: New USB device strings: Mfr=0, Product=2, SerialNumber=0
[    6.056909] usb 1-4.4: Product: Dell Premium USB Optical Mouse
[    6.176056] usb 1-9: new high-speed USB device number 7 using xhci_hcd
[    6.182065] input: PS/2 Generic Mouse as /devices/platform/i8042/serio2/input/input9
[    6.363870] usb 1-9: New USB device found, idVendor=05c8, idProduct=0383
[    6.363872] usb 1-9: New USB device strings: Mfr=2, Product=1, SerialNumber=0
[    6.363873] usb 1-9: Product: HP HD Camera
[    6.363874] usb 1-9: Manufacturer: Sonix Technology Co., Ltd.
[    6.373550] hidraw: raw HID events driver (C) Jiri Kosina
[    6.380997] usbcore: registered new interface driver usbhid
[    6.380997] usbhid: USB HID core driver
[    6.383226] input: DELL Dell USB Entry Keyboard as /devices/pci0000:00/0000:00:14.0/usb1/1-4/1-4.2/1-4.2:1.0/0003:413C:2107.0001/input/input12
[    6.440693] hid-generic 0003:413C:2107.0001: input,hidraw0: USB HID v1.10 Keyboard [DELL Dell USB Entry Keyboard] on usb-0000:00:14.0-4.2/input0
[    6.440805] input: Dell Premium USB Optical Mouse as /devices/pci0000:00/0000:00:14.0/usb1/1-4/1-4.4/1-4.4:1.0/0003:413C:3016.0002/input/input13
[    6.441190] hid-generic 0003:413C:3016.0002: input,hidraw1: USB HID v1.11 Mouse [Dell Premium USB Optical Mouse] on usb-0000:00:14.0-4.4/input0
[    6.813092] [drm] RC6 on
[    6.955304] psmouse serio3: synaptics: queried max coordinates: x [..5670], y [..4758]
[    6.987489] psmouse serio3: synaptics: queried min coordinates: x [1360..], y [1198..]
[    6.987492] psmouse serio3: synaptics: Your touchpad (PNP: SYN3037 SYN0100 SYN0002 PNP0f13) says it can support a different bus. If i2c-hid and hid-rmi are not used, you might want to try setting psmouse.synaptics_intertouch to 1 and report this to linux-input@vger.kernel.org.
[    7.047230] psmouse serio3: synaptics: Touchpad model: 1, fw: 8.2, id: 0x1e2b1, caps: 0xf00123/0x840300/0x2e800/0x0, board id: 3139, fw id: 2000742
[    7.084352] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio3/input/input11
[    7.571295] EXT4-fs (sda5): mounted filesystem with ordered data mode. Opts: (null)
[    8.466118] random: crng init done
[    8.466120] random: 7 urandom warning(s) missed due to ratelimiting
[    8.962449] systemd[1]: RTC configured in localtime, applying delta of 120 minutes to system time.
[    9.365647] ip_tables: (C) 2000-2006 Netfilter Core Team
[    9.519754] systemd[1]: systemd 237 running in system mode. (+PAM +AUDIT +SELINUX +IMA +APPARMOR +SMACK +SYSVINIT +UTMP +LIBCRYPTSETUP +GCRYPT +GNUTLS +ACL +XZ +LZ4 +SECCOMP +BLKID +ELFUTILS +KMOD -IDN2 +IDN -PCRE2 default-hierarchy=hybrid)
[    9.536106] systemd[1]: Detected architecture x86-64.
[    9.555422] systemd[1]: Set hostname to <fw-uc9371>.
[   11.825590] systemd[1]: Started Forward Password Requests to Wall Directory Watch.
[   11.825758] systemd[1]: Set up automount Arbitrary Executable File Formats File System Automount Point.
[   11.825768] systemd[1]: Reached target Remote File Systems.
[   11.825774] systemd[1]: Reached target User and Group Name Lookups.
[   11.825882] systemd[1]: Created slice User and Session Slice.
[   11.825956] systemd[1]: Created slice System Slice.
[   11.825970] systemd[1]: Reached target Slices.
[   12.334538] lp: driver loaded but no devices found
[   12.395820] ppdev: user-space parallel port driver
[   12.512295] EXT4-fs (sda5): re-mounted. Opts: errors=remount-ro
[   13.412971] systemd-journald[329]: Received request to flush runtime journal from PID 1
[   35.736927] audit: type=1400 audit(1535111088.721:2): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/sbin/dhclient" pid=458 comm="apparmor_parser"
[   35.736930] audit: type=1400 audit(1535111088.721:3): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=458 comm="apparmor_parser"
[   35.736931] audit: type=1400 audit(1535111088.721:4): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-helper" pid=458 comm="apparmor_parser"
[   35.736933] audit: type=1400 audit(1535111088.721:5): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=458 comm="apparmor_parser"
[   35.737628] audit: type=1400 audit(1535111088.721:6): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/bin/ubuntu-core-launcher" pid=462 comm="apparmor_parser"
[   35.830880] audit: type=1400 audit(1535111088.813:7): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/bin/man" pid=461 comm="apparmor_parser"
[   35.830883] audit: type=1400 audit(1535111088.813:8): apparmor="STATUS" operation="profile_load" profile="unconfined" name="man_filter" pid=461 comm="apparmor_parser"
[   35.830885] audit: type=1400 audit(1535111088.813:9): apparmor="STATUS" operation="profile_load" profile="unconfined" name="man_groff" pid=461 comm="apparmor_parser"
[   35.832147] audit: type=1400 audit(1535111088.817:10): apparmor="STATUS" operation="profile_load" profile="unconfined" name="libreoffice-senddoc" pid=468 comm="apparmor_parser"
[   35.832150] audit: type=1400 audit(1535111088.817:11): apparmor="STATUS" operation="profile_load" profile="unconfined" name="libreoffice-senddoc//sanitized_helper" pid=468 comm="apparmor_parser"
[   36.463107] tpm_inf_pnp 00:0b: Found TPM with ID IFX0102
[   36.475364] hp_accel: hardware type HPB64xx found
[   36.480181] input: HP Wireless hotkeys as /devices/virtual/input/input15
[   36.521384] (NULL device *): hwmon_device_register() is deprecated. Please convert the driver to use hwmon_device_register_with_info().
[   36.524479] intel-lpss 0000:00:15.0: enabling device (0000 -> 0002)
[   36.531230] idma64 idma64.0: Found Intel integrated DMA 64-bit
[   36.565743] Bluetooth: Core ver 2.22
[   36.565755] NET: Registered protocol family 31
[   36.565756] Bluetooth: HCI device and connection manager initialized
[   36.565759] Bluetooth: HCI socket layer initialized
[   36.565760] Bluetooth: L2CAP socket layer initialized
[   36.565764] Bluetooth: SCO socket layer initialized
[   36.569007] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   36.585977] cfg80211: Loading compiled-in X.509 certificates for regulatory database
[   36.587497] cfg80211: Loaded X.509 cert 'sforshee: 00b28ddf47aef9cea7'
[   36.591588] Intel(R) Wireless WiFi driver for Linux
[   36.591589] Copyright(c) 2003- 2015 Intel Corporation
[   36.602288] lis3lv02d: 8 bits 3DC sensor found
[   36.687712] mei_me 0000:00:16.0: enabling device (0000 -> 0002)
[   36.709608] ACPI Error: Needed [Buffer/String/Package], found [Integer] 000000007e8a01a7 (20170831/exresop-593)
[   36.709647] ACPI Exception: AE_AML_OPERAND_TYPE, While resolving operands for [Index] (20170831/dswexec-461)
[   36.709689] 
               Initialized Local Variables for Method [WVPO]:
[   36.709689]   Local1: 00000000c8206fd7 <Obj>           Buffer(12) 00 00 00 00 00 00 00 00
[   36.709697] Initialized Arguments for Method [WVPO]:  (2 arguments defined for method invocation)
[   36.709697]   Arg0:   00000000c48abf24 <Obj>           Integer 0000000000000004
[   36.709700]   Arg1:   000000007e8a01a7 <Obj>           Integer 0000000000000000
[   36.709704] ACPI Error: Method parse/execution failed \_SB.WMIV.WVPO, AE_AML_OPERAND_TYPE (20170831/psparse-550)
[   36.709735] ACPI Error: Method parse/execution failed \_SB.WMIV.WMPV, AE_AML_OPERAND_TYPE (20170831/psparse-550)
[   36.710805] ACPI Error: Needed [Buffer/String/Package], found [Integer] 000000008b1edd84 (20170831/exresop-593)
[   36.710836] ACPI Exception: AE_AML_OPERAND_TYPE, While resolving operands for [Index] (20170831/dswexec-461)
[   36.710865] 
               Initialized Local Variables for Method [WVPO]:
[   36.710865]   Local1: 000000007f14c774 <Obj>           Buffer(12) 00 00 00 00 00 00 00 00
[   36.710872] Initialized Arguments for Method [WVPO]:  (2 arguments defined for method invocation)
[   36.710873]   Arg0:   00000000cd8601b3 <Obj>           Integer 0000000000000004
[   36.710875]   Arg1:   000000008b1edd84 <Obj>           Integer 0000000000000000
[   36.710879] ACPI Error: Method parse/execution failed \_SB.WMIV.WVPO, AE_AML_OPERAND_TYPE (20170831/psparse-550)
[   36.710918] ACPI Error: Method parse/execution failed \_SB.WMIV.WMPV, AE_AML_OPERAND_TYPE (20170831/psparse-550)
[   36.712803] ACPI Error: Needed [Buffer/String/Package], found [Integer] 00000000d5ea36b4 (20170831/exresop-593)
[   36.712839] ACPI Exception: AE_AML_OPERAND_TYPE, While resolving operands for [Index] (20170831/dswexec-461)
[   36.712881] 
               Initialized Local Variables for Method [WVPO]:
[   36.712881]   Local1: 00000000bebb1051 <Obj>           Buffer(12) 00 00 00 00 00 00 00 00
[   36.712888] Initialized Arguments for Method [WVPO]:  (2 arguments defined for method invocation)
[   36.712889]   Arg0:   00000000befe7690 <Obj>           Integer 0000000000000004
[   36.712892]   Arg1:   00000000d5ea36b4 <Obj>           Integer 0000000000000000
[   36.712896] ACPI Error: Method parse/execution failed \_SB.WMIV.WVPO, AE_AML_OPERAND_TYPE (20170831/psparse-550)
[   36.712926] ACPI Error: Method parse/execution failed \_SB.WMIV.WMPV, AE_AML_OPERAND_TYPE (20170831/psparse-550)
[   36.712990] input: HP WMI hotkeys as /devices/virtual/input/input16
[   36.716967] ACPI Error: Attempt to CreateField of length zero (20170831/dsopcode-168)
[   36.717015] 
               Initialized Local Variables for Method [WVPI]:
[   36.717016]   Local0: 00000000cad9e9da <Obj>           Integer 0000000000000080
[   36.717021]   Local1: 0000000075237d58 <Obj>           Package 0000000075237d58
[   36.717026] Initialized Arguments for Method [WVPI]:  (3 arguments defined for method invocation)
[   36.717027]   Arg0:   00000000d0a7708a <Obj>           Integer 0000000000000000
[   36.717031]   Arg1:   00000000fe523499 <Obj>           Integer 0000000000000003
[   36.717035]   Arg2:   0000000079455cc9 <Obj>           Buffer(20) 53 45 43 55 01 00 00 00
[   36.717045] ACPI Error: Method parse/execution failed \_SB.WMIV.WVPI, AE_AML_OPERAND_VALUE (20170831/psparse-550)
[   36.717100] ACPI Error: Method parse/execution failed \_SB.WMIV.WMPV, AE_AML_OPERAND_VALUE (20170831/psparse-550)
[   36.837315] RAPL PMU: API unit is 2^-32 Joules, 5 fixed counters, 655360 ms ovfl timer
[   36.837316] RAPL PMU: hw unit of domain pp0-core 2^-14 Joules
[   36.837317] RAPL PMU: hw unit of domain package 2^-14 Joules
[   36.837317] RAPL PMU: hw unit of domain dram 2^-14 Joules
[   36.837317] RAPL PMU: hw unit of domain pp1-gpu 2^-14 Joules
[   36.837318] RAPL PMU: hw unit of domain psys 2^-14 Joules
[   36.912953] usbcore: registered new interface driver btusb
[   36.914112] Bluetooth: hci0: Firmware revision 0.0 build 176 week 45 2017
[   36.984036] iwlwifi 0000:02:00.0: loaded firmware version 34.0.1 op_mode iwlmvm
[   37.080214] iwlwifi 0000:02:00.0: Detected Intel(R) Dual Band Wireless AC 8260, REV=0x208
[   37.152782] iwlwifi 0000:02:00.0: base HW address: f4:8c:50:ff:f1:1d
[   37.776736] AVX2 version of gcm_enc/dec engaged.
[   37.776737] AES CTR mode by8 optimization enabled
[   37.804018] kvm: disabled by bios
[   37.804603] ieee80211 phy0: Selected rate control algorithm 'iwl-mvm-rs'
[   37.804842] (NULL device *): hwmon_device_register() is deprecated. Please convert the driver to use hwmon_device_register_with_info().
[   37.804867] thermal thermal_zone7: failed to read out thermal zone (-61)
[   37.809804] intel_rapl: Found RAPL domain package
[   37.809805] intel_rapl: Found RAPL domain core
[   37.809806] intel_rapl: Found RAPL domain uncore
[   37.904053] input: ST LIS3LV02DL Accelerometer as /devices/platform/lis3lv02d/input/input17
[   37.952507] iwlwifi 0000:02:00.0 wlp2s0: renamed from wlan0
[   38.615806] media: Linux media interface: v0.10
[   38.621677] Linux video capture interface: v2.00
[   38.628947] uvcvideo: Found UVC 1.00 device HP HD Camera (05c8:0383)
[   38.655257] uvcvideo 1-9:1.0: Entity type for entity Extension 3 was not initialized!
[   38.655259] uvcvideo 1-9:1.0: Entity type for entity Processing 2 was not initialized!
[   38.655260] uvcvideo 1-9:1.0: Entity type for entity Camera 1 was not initialized!
[   38.655318] input: HP HD Camera: HP HD Camera as /devices/pci0000:00/0000:00:14.0/usb1/1-9/1-9:1.0/input/input18
[   38.655372] usbcore: registered new interface driver uvcvideo
[   38.655372] USB Video Class driver (1.1.1)
[   38.718960] snd_hda_intel 0000:00:1f.3: bound 0000:00:02.0 (ops i915_audio_component_bind_ops [i915])
[   38.792869] snd_hda_codec_conexant hdaudioC0D0: CX20724: BIOS auto-probing.
[   38.793345] snd_hda_codec_conexant hdaudioC0D0: action: 0 gpio_led: 0
[   38.793487] snd_hda_codec_conexant hdaudioC0D0: autoconfig for CX20724: line_outs=1 (0x16/0x0/0x0/0x0/0x0) type:line
[   38.793488] snd_hda_codec_conexant hdaudioC0D0:    speaker_outs=1 (0x17/0x0/0x0/0x0/0x0)
[   38.793489] snd_hda_codec_conexant hdaudioC0D0:    hp_outs=1 (0x1d/0x0/0x0/0x0/0x0)
[   38.793490] snd_hda_codec_conexant hdaudioC0D0:    mono: mono_out=0x0
[   38.793491] snd_hda_codec_conexant hdaudioC0D0:    inputs:
[   38.793492] snd_hda_codec_conexant hdaudioC0D0:      Mic=0x19
[   38.793493] snd_hda_codec_conexant hdaudioC0D0:      Internal Mic=0x1a
[   38.793494] snd_hda_codec_conexant hdaudioC0D0:      Line=0x18
[   38.794702] snd_hda_codec_conexant hdaudioC0D0: Enable sync_write for stable communication
[   38.794703] snd_hda_codec_conexant hdaudioC0D0: action: 1 gpio_led: 0
[   38.797950] snd_hda_codec_conexant hdaudioC0D0: action: 2 gpio_led: 0
[   38.805112] input: HDA Intel PCH Mic as /devices/pci0000:00/0000:00:1f.3/sound/card0/input19
[   38.805173] input: HDA Intel PCH Line as /devices/pci0000:00/0000:00:1f.3/sound/card0/input20
[   38.805218] input: HDA Intel PCH Dock Line Out as /devices/pci0000:00/0000:00:1f.3/sound/card0/input21
[   38.805268] input: HDA Intel PCH Headphone as /devices/pci0000:00/0000:00:1f.3/sound/card0/input22
[   38.805312] input: HDA Intel PCH HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:1f.3/sound/card0/input23
[   38.805356] input: HDA Intel PCH HDMI/DP,pcm=7 as /devices/pci0000:00/0000:00:1f.3/sound/card0/input24
[   38.805423] input: HDA Intel PCH HDMI/DP,pcm=8 as /devices/pci0000:00/0000:00:1f.3/sound/card0/input25
[   38.805466] input: HDA Intel PCH HDMI/DP,pcm=9 as /devices/pci0000:00/0000:00:1f.3/sound/card0/input26
[   38.805509] input: HDA Intel PCH HDMI/DP,pcm=10 as /devices/pci0000:00/0000:00:1f.3/sound/card0/input27
[   38.829161] snd_hda_codec_conexant hdaudioC0D0: action: 2 gpio_led: 1
[   42.453325] Adding 16652284k swap on /dev/sda6.  Priority:-2 extents:1 across:16652284k FS
[   42.781516] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   42.781517] Bluetooth: BNEP filters: protocol multicast
[   42.781519] Bluetooth: BNEP socket layer initialized
[   47.901010] kauditd_printk_skb: 33 callbacks suppressed
[   47.901011] audit: type=1400 audit(1535111100.885:45): apparmor="DENIED" operation="open" profile="/usr/sbin/mysqld" name="/sys/devices/system/node/" pid=1094 comm="mysqld" requested_mask="r" denied_mask="r" fsuid=0 ouid=0
[   47.918048] audit: type=1400 audit(1535111100.901:46): apparmor="DENIED" operation="capable" profile="/usr/sbin/mysqld" pid=1094 comm="mysqld" capability=2  capname="dac_read_search"
[   48.009696] IPv6: ADDRCONF(NETDEV_UP): enp0s31f6: link is not ready
[   48.127171] audit: type=1400 audit(1535111101.109:47): apparmor="DENIED" operation="capable" profile="/usr/sbin/mysqld" pid=1094 comm="mysqld" capability=2  capname="dac_read_search"
[   48.172914] audit: type=1400 audit(1535111101.157:48): apparmor="DENIED" operation="open" profile="/usr/sbin/mysqld" name="/sys/devices/system/node/" pid=1134 comm="mysqld" requested_mask="r" denied_mask="r" fsuid=121 ouid=0
[   48.232234] IPv6: ADDRCONF(NETDEV_UP): enp0s31f6: link is not ready
[   48.249224] IPv6: ADDRCONF(NETDEV_UP): wlp2s0: link is not ready
[   48.492554] IPv6: ADDRCONF(NETDEV_UP): wlp2s0: link is not ready
[   48.567739] IPv6: ADDRCONF(NETDEV_UP): wlp2s0: link is not ready
[   68.764266] wlp2s0: authenticate with a0:e0:af:f8:45:0d
[   68.772910] wlp2s0: send auth to a0:e0:af:f8:45:0d (try 1/3)
[   68.779119] wlp2s0: authenticated
[   68.779305] iwlwifi 0000:02:00.0 wlp2s0: disabling HT/VHT due to WEP/TKIP use
[   68.780062] wlp2s0: associate with a0:e0:af:f8:45:0d (try 1/3)
[   68.781878] wlp2s0: RX AssocResp from a0:e0:af:f8:45:0d (capab=0x11 status=0 aid=1)
[   68.784162] wlp2s0: associated
[   68.784196] wlp2s0: Limiting TX power to 18 dBm as advertised by a0:e0:af:f8:45:0d
[   68.785036] IPv6: ADDRCONF(NETDEV_CHANGE): wlp2s0: link becomes ready
[   70.519025] Bluetooth: RFCOMM TTY layer initialized
[   70.519034] Bluetooth: RFCOMM socket layer initialized
[   70.519040] Bluetooth: RFCOMM ver 1.11
[   72.788896] rfkill: input handler disabled
[  106.159357] netlink: 'svpn': attribute type 6 has an invalid length.
[  106.159360] netlink: 'svpn': attribute type 4 has an invalid length.
[  106.159777] netlink: 'svpn': attribute type 6 has an invalid length.
[  106.159779] netlink: 'svpn': attribute type 4 has an invalid length.
[  106.160693] netlink: 'svpn': attribute type 6 has an invalid length.
[  106.160695] netlink: 'svpn': attribute type 4 has an invalid length.
[  106.161359] netlink: 'svpn': attribute type 6 has an invalid length.
[  106.161361] netlink: 'svpn': attribute type 4 has an invalid length.
[  106.162033] netlink: 'svpn': attribute type 6 has an invalid length.
[  106.162035] netlink: 'svpn': attribute type 4 has an invalid length.
[ 1878.813784] wlp2s0: deauthenticated from a0:e0:af:f8:45:0d (Reason: 2=PREV_AUTH_NOT_VALID)
[ 1878.987660] wlp2s0: authenticate with a0:e0:af:f8:45:02
[ 1878.996332] wlp2s0: send auth to a0:e0:af:f8:45:02 (try 1/3)
[ 1879.004897] wlp2s0: authenticated
[ 1879.005674] iwlwifi 0000:02:00.0 wlp2s0: disabling HT/VHT due to WEP/TKIP use
[ 1879.008096] wlp2s0: associate with a0:e0:af:f8:45:02 (try 1/3)
[ 1879.013578] wlp2s0: RX AssocResp from a0:e0:af:f8:45:02 (capab=0x431 status=0 aid=2)
[ 1879.024968] wlp2s0: associated
[ 1879.067912] wlp2s0: Limiting TX power to 16 dBm as advertised by a0:e0:af:f8:45:02
[ 3339.966816] [drm:intel_pipe_update_end [i915]] *ERROR* Atomic update failure on pipe A (start=200922 end=200923) time 137 us, min 1073, max 1079, scanline start 1071, end 1080
[ 3689.101718] wlp2s0: deauthenticated from a0:e0:af:f8:45:02 (Reason: 2=PREV_AUTH_NOT_VALID)
[ 3689.544963] validate_nla: 2 callbacks suppressed
[ 3689.544968] netlink: 'svpn': attribute type 6 has an invalid length.
[ 3689.544974] netlink: 'svpn': attribute type 4 has an invalid length.
[ 3689.556844] netlink: 'svpn': attribute type 6 has an invalid length.
[ 3689.556849] netlink: 'svpn': attribute type 4 has an invalid length.
[ 3689.653957] netlink: 'svpn': attribute type 6 has an invalid length.
[ 3689.653959] netlink: 'svpn': attribute type 4 has an invalid length.
[ 3689.655107] netlink: 'svpn': attribute type 6 has an invalid length.
[ 3689.655110] netlink: 'svpn': attribute type 4 has an invalid length.
[ 3689.655327] netlink: 'svpn': attribute type 6 has an invalid length.
[ 3689.655329] netlink: 'svpn': attribute type 4 has an invalid length.
[ 3690.565905] IPv6: ADDRCONF(NETDEV_UP): enp0s31f6: link is not ready
[ 3690.569219] IPv6: ADDRCONF(NETDEV_UP): wlp2s0: link is not ready
[ 3690.819683] IPv6: ADDRCONF(NETDEV_UP): wlp2s0: link is not ready
[ 3691.083976] IPv6: ADDRCONF(NETDEV_UP): wlp2s0: link is not ready
[ 3691.987118] IPv6: ADDRCONF(NETDEV_UP): enp0s31f6: link is not ready
[ 3691.990613] IPv6: ADDRCONF(NETDEV_UP): wlp2s0: link is not ready
[ 3692.243980] IPv6: ADDRCONF(NETDEV_UP): wlp2s0: link is not ready
[ 3692.525189] IPv6: ADDRCONF(NETDEV_UP): wlp2s0: link is not ready
[ 3693.920701] IPv6: ADDRCONF(NETDEV_UP): enp0s31f6: link is not ready
[ 3693.923960] IPv6: ADDRCONF(NETDEV_UP): wlp2s0: link is not ready
[ 3694.174891] IPv6: ADDRCONF(NETDEV_UP): wlp2s0: link is not ready
[ 3694.381204] IPv6: ADDRCONF(NETDEV_UP): wlp2s0: link is not ready
[ 3695.925218] IPv6: ADDRCONF(NETDEV_UP): enp0s31f6: link is not ready
[ 3695.928812] IPv6: ADDRCONF(NETDEV_UP): wlp2s0: link is not ready
[ 3696.187946] IPv6: ADDRCONF(NETDEV_UP): wlp2s0: link is not ready
[ 3696.354164] IPv6: ADDRCONF(NETDEV_UP): wlp2s0: link is not ready
[ 3697.905857] IPv6: ADDRCONF(NETDEV_UP): enp0s31f6: link is not ready
[ 3697.909032] IPv6: ADDRCONF(NETDEV_UP): wlp2s0: link is not ready
[ 3698.164326] IPv6: ADDRCONF(NETDEV_UP): wlp2s0: link is not ready
[ 3698.361441] IPv6: ADDRCONF(NETDEV_UP): wlp2s0: link is not ready
[ 3701.868320] IPv6: ADDRCONF(NETDEV_UP): enp0s31f6: link is not ready
[ 3701.872318] IPv6: ADDRCONF(NETDEV_UP): wlp2s0: link is not ready
[ 3702.123379] IPv6: ADDRCONF(NETDEV_UP): wlp2s0: link is not ready
[ 3702.328097] IPv6: ADDRCONF(NETDEV_UP): wlp2s0: link is not ready
[ 3703.937169] IPv6: ADDRCONF(NETDEV_UP): enp0s31f6: link is not ready
[ 3703.939951] IPv6: ADDRCONF(NETDEV_UP): wlp2s0: link is not ready
[ 3704.191823] IPv6: ADDRCONF(NETDEV_UP): wlp2s0: link is not ready
[ 3704.337532] IPv6: ADDRCONF(NETDEV_UP): wlp2s0: link is not ready
[ 3705.960583] IPv6: ADDRCONF(NETDEV_UP): enp0s31f6: link is not ready
[ 3705.963729] IPv6: ADDRCONF(NETDEV_UP): wlp2s0: link is not ready
[ 3706.215046] IPv6: ADDRCONF(NETDEV_UP): wlp2s0: link is not ready
[ 3706.461340] IPv6: ADDRCONF(NETDEV_UP): wlp2s0: link is not ready
[ 3707.980947] IPv6: ADDRCONF(NETDEV_UP): enp0s31f6: link is not ready
[ 3707.984803] IPv6: ADDRCONF(NETDEV_UP): wlp2s0: link is not ready
[ 3708.236547] IPv6: ADDRCONF(NETDEV_UP): wlp2s0: link is not ready
[ 3708.471963] IPv6: ADDRCONF(NETDEV_UP): wlp2s0: link is not ready
[ 3709.969968] IPv6: ADDRCONF(NETDEV_UP): enp0s31f6: link is not ready
[ 3709.973224] IPv6: ADDRCONF(NETDEV_UP): wlp2s0: link is not ready
[ 3710.225343] IPv6: ADDRCONF(NETDEV_UP): wlp2s0: link is not ready
[ 3710.490661] IPv6: ADDRCONF(NETDEV_UP): wlp2s0: link is not ready
wald_f@fw-uc9371:~$ 

```

---

### Post by devfabien on 2018-08-27
To complete my message. When i do a dmseg, i think the error is on this lines :

```
[   74.744854] wlp2s0: authenticate with a0:e0:af:f8:45:0d
[   74.753830] wlp2s0: send auth to a0:e0:af:f8:45:0d (try 1/3)
[   74.760188] wlp2s0: authenticated
[   74.760415] iwlwifi 0000:02:00.0 wlp2s0: disabling HT/VHT due to WEP/TKIP use
[   74.768085] wlp2s0: associate with a0:e0:af:f8:45:0d (try 1/3)
[   74.770621] wlp2s0: RX AssocResp from a0:e0:af:f8:45:0d (capab=0x11 status=0 aid=4)
[   74.773382] wlp2s0: associated
[   74.774018] IPv6: ADDRCONF(NETDEV_CHANGE): wlp2s0: link becomes ready
[   74.797751] wlp2s0: Limiting TX power to 18 dBm as advertised by a0:e0:af:f8:45:0d
[   76.462375] Bluetooth: RFCOMM TTY layer initialized
[   76.462383] Bluetooth: RFCOMM socket layer initialized
[   76.462387] Bluetooth: RFCOMM ver 1.11
[   78.810902] rfkill: input handler disabled
[  123.484780] netlink: 'svpn': attribute type 6 has an invalid length.
[  123.484781] netlink: 'svpn': attribute type 4 has an invalid length.
[  123.484874] netlink: 'svpn': attribute type 6 has an invalid length.
[  123.484875] netlink: 'svpn': attribute type 4 has an invalid length.
[  123.485208] netlink: 'svpn': attribute type 6 has an invalid length.
[  123.485209] netlink: 'svpn': attribute type 4 has an invalid length.
[  123.485350] netlink: 'svpn': attribute type 6 has an invalid length.
[  123.485351] netlink: 'svpn': attribute type 4 has an invalid length.
[  123.485489] netlink: 'svpn': attribute type 6 has an invalid length.
[  123.485490] netlink: 'svpn': attribute type 4 has an invalid length.
[ 1884.698683] wlp2s0: deauthenticated from a0:e0:af:f8:45:0d (Reason: 2=PREV_AUTH_NOT_VALID)
```

---

### Post by devfabien on 2018-08-28
**i resolve the problem when i change wep to wpa (wifi)**

---

