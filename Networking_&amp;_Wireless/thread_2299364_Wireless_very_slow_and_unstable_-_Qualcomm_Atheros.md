---
title: "Wireless very slow and unstable - Qualcomm Atheros AR9285 - Ubuntu 14.04"
date: 2015-10-17
forum: Networking &amp; Wireless
---

### Post by SpaceCowboy64 on 2015-10-17
Hello, 
I've installed yesterday the Ubuntu 14.04.3 LTS in a Lenovo G470, all things working well, except the Wifi, that connects to my network, but is slow and unstable. The network adapter is Qualcomm Atheros AR9285, I've edited "/etc/modprobe.d/ath9k" and added the line "options ath9k nohwcrypt=1", Installed backports, and still no working. Now, I've updated the kernel version to 3.19.0-30(The old was 3.19.0-25), but the problem continues.
Here is my wireless info:
```

    ########## wireless info START ##########
     
    Report from: 17 Oct 2015 20:44 BRT -0300
     
    Booted last: 17 Oct 2015 20:41 BRT -0300
     
    Script from: 27 Sep 2015 00:34 UTC +0000
     
    ##### release ###########################
     
    Distributor ID: Ubuntu
    Description:    Ubuntu 14.04.3 LTS
    Release:        14.04
    Codename:       trusty
     
    ##### kernel ############################
     
    Linux 3.19.0-30-generic #34~14.04.1-Ubuntu SMP Fri Oct 2 22:09:39 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux
     
    Parameters: ro, quiet, splash, vt.handoff=7
     
    ##### desktop ###########################
     
    Ubuntu
     
    ##### lspci #############################
     
    01:00.0 Ethernet controller [0200]: Qualcomm Atheros AR8152 v2.0 Fast Ethernet [1969:2062] (rev c1)
            Subsystem: Lenovo Device [17aa:3979]
            Kernel driver in use: atl1c
     
    02:00.0 Network controller [0280]: Qualcomm Atheros AR9285 Wireless Network Adapter (PCI-Express) [168c:002b] (rev 01)
            Subsystem: Lenovo Device [17aa:30a1]
            Kernel driver in use: ath9k
     
    ##### lsusb #############################
     
    Bus 002 Device 005: ID 064e:a222 Suyin Corp.
    Bus 002 Device 004: ID 03f0:5307 Hewlett-Packard
    Bus 002 Device 003: ID 045e:07b2 Microsoft Corp.
    Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
    Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
    Bus 001 Device 004: ID 0489:e00d Foxconn / Hon Hai Broadcom Bluetooth 2.1 Device
    Bus 001 Device 003: ID 0bda:0139 Realtek Semiconductor Corp. RTS5139 Card Reader Controller
    Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
    Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
     
    ##### PCMCIA card info ##################
     
    ##### rfkill ############################
     
    0: ideapad_wlan: Wireless LAN
            Soft blocked: no
            Hard blocked: no
    1: ideapad_bluetooth: Bluetooth
            Soft blocked: no
            Hard blocked: no
    2: hci0: Bluetooth
            Soft blocked: no
            Hard blocked: no
    3: phy0: Wireless LAN
            Soft blocked: no
            Hard blocked: no
     
    ##### lsmod #############################
     
    ath9k                 147456  0
    ath9k_common           32768  1 ath9k
    ath9k_hw              458752  2 ath9k_common,ath9k
    ath                    32768  3 ath9k_common,ath9k,ath9k_hw
    mac80211              708608  1 ath9k
    cfg80211              524288  4 ath,ath9k_common,ath9k,mac80211
    ideapad_laptop         20480  0
    sparse_keymap          16384  1 ideapad_laptop
     
    ##### interfaces ########################
     
    auto lo
    iface lo inet loopback
     
    ##### ifconfig ##########################
     
    eth0      Link encap:Ethernet  HWaddr <MAC 'eth0' [IF]>  
              UP BROADCAST MULTICAST  MTU:1500  Metric:1
              RX packets:0 errors:0 dropped:0 overruns:0 frame:0
              TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
              collisions:0 txqueuelen:1000
              RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
     
    wlan0     Link encap:Ethernet  HWaddr <MAC 'wlan0' [IF]>  
              inet addr:10.10.10.100  Bcast:10.10.10.255  Mask:255.255.255.0
              inet6 addr: fe80::<IP6 'wlan0' [IF]>/64 Scope:Link
              UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
              RX packets:29 errors:0 dropped:0 overruns:0 frame:0
              TX packets:225 errors:0 dropped:0 overruns:0 carrier:0
              collisions:0 txqueuelen:1000
              RX bytes:2888 (2.8 KB)  TX bytes:26521 (26.5 KB)
     
    ##### iwconfig ##########################
     
    eth0      no wireless extensions.
     
    lo        no wireless extensions.
     
    wlan0     IEEE 802.11bgn  ESSID:"MyNetwork"  
              Mode:Managed  Frequency:2.462 GHz  Access Point: <MAC '' [AC1]>  
              Bit Rate=1 Mb/s   Tx-Power=17 dBm  
              Retry short limit:7   RTS thr:off   Fragment thr:off
              Power Management:off
              Link Quality=65/70  Signal level=-45 dBm  
              Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
              Tx excessive retries:0  Invalid misc:2   Missed beacon:0
     
    ##### route #############################
     
    Kernel IP routing table
    Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
    0.0.0.0         10.10.10.1      0.0.0.0         UG    0      0        0 wlan0
    10.10.10.0      0.0.0.0         255.255.255.0   U     9      0        0 wlan0
     
    ##### resolv.conf #######################
     
    nameserver 127.0.1.1
     
    ##### network managers ##################
     
    Installed:
     
            NetworkManager
     
    Running:
     
    root       745     1  0 20:41 ?        00:00:00 NetworkManager
     
    ##### NetworkManager info ###############
     
    NetworkManager Tool
     
    State: connected (global)
     
    - Device: wlan0  [MyNetwork] --------------------------------------------------
      Type:              802.11 WiFi
      Driver:            ath9k
      State:             connected
      Default:           yes
      HW Address:        <MAC 'wlan0' [IF]>
     
      Capabilities:
        Speed:           1 Mb/s
     
      Wireless Properties
        WEP Encryption:  yes
        WPA Encryption:  yes
        WPA2 Encryption: yes
     
      Wireless Access Points (* = current AP)
        casa 1:          Infra, <MAC 'casa 1' [AC3]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 47 WPA WPA2
        NETGEAR:         Infra, <MAC 'NETGEAR' [AC4]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 35 WPA WPA2
        Casa:            Infra, <MAC 'Casa' [AN3]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 34 WPA2
        hunTT:           Infra, <MAC 'hunTT' [AN4]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 25 WPA2
        Hmiranda:        Infra, <MAC 'Hmiranda' [AC5]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 22 WPA2
        A_casa:          Infra, <MAC 'A_casa' [AN6]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 20 WPA WPA2
        BRV:             Infra, <MAC 'BRV' [AC9]>, Freq 2427 MHz, Rate 54 Mb/s, Strength 20 WPA WPA2
        marbias:         Infra, <MAC 'marbias' [AN8]>, Freq 2452 MHz, Rate 54 Mb/s, Strength 14 WPA WPA2
        *MyNetwork:     Infra, <MAC '' [AC1]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 73 WPA2
        Andrade:         Infra, <MAC 'Andrade' [AC7]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 17 WPA WPA2
        hunTT:           Infra, <MAC 'hunTT' [AC8]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 12 WPA WPA2
        Pousada-:        Infra, <MAC 'Pousada-' [AC6]>, Freq 2452 MHz, Rate 54 Mb/s, Strength 35 WPA WPA2
        Casa:            Infra, <MAC 'Casa' [AN13]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 27 WPA WPA2
        dlinkbla:        Infra, <MAC 'dlinkbla' [AN14]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 20 WPA2
        Renato Lopes:    Infra, <MAC 'Renato Lopes' [AN15]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 10 WPA
     
      IPv4 Settings:
        Address:         10.10.10.100
        Prefix:          24 (255.255.255.0)
        Gateway:         10.10.10.1
     
        DNS:             10.10.10.1
     
    - Device: eth0 -----------------------------------------------------------------
      Type:              Wired
      Driver:            atl1c
      State:             unavailable
      Default:           no
      HW Address:        <MAC 'eth0' [IF]>
     
      Capabilities:
        Carrier Detect:  yes
     
      Wired Properties
        Carrier:         off
     
    ##### NetworkManager.state ##############
     
    [main]
    NetworkingEnabled=true
    WirelessEnabled=true
    WWANEnabled=true
    WimaxEnabled=true
     
    ##### NetworkManager.conf ###############
     
    [main]
    plugins=ifupdown,keyfile,ofono
    dns=dnsmasq
     
    [ifupdown]
    managed=false
     
    ##### NetworkManager profiles ###########
     
    [[/etc/NetworkManager/system-connections/MyNetwork]] (600 root)
    [connection] id=MyNetwork | type=802-11-wireless
    [802-11-wireless] ssid=MyNetwork | mac-address=<MAC 'wlan0' [IF]>
    [ipv4] method=auto
    [ipv6] method=auto
     
    ##### iw reg get ########################
     
    Region: America/Sao_Paulo (based on set time zone)
     
    country US:
            (2402 - 2472 @ 40), (3, 27)
            (5170 - 5250 @ 40), (3, 17)
            (5250 - 5330 @ 40), (3, 20), DFS
            (5490 - 5600 @ 40), (3, 20), DFS
            (5650 - 5710 @ 40), (3, 20), DFS
            (5735 - 5835 @ 40), (3, 30)
            (57240 - 63720 @ 2160), (N/A, 40)
     
    ##### iwlist channels ###################
     
    eth0      no frequency information.
     
    lo        no frequency information.
     
    wlan0     11 channels in total; available frequencies :
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
              Current Frequency:2.462 GHz (Channel 11)
     
    ##### iwlist scan #######################
     
    eth0      Interface doesn't support scanning.
     
    lo        Interface doesn't support scanning.
     
    Channel occupancy:
     
          2   APs on   Frequency:2.412 GHz (Channel 1)
          1   APs on   Frequency:2.427 GHz (Channel 4)
          1   APs on   Frequency:2.437 GHz (Channel 6)
          1   APs on   Frequency:2.452 GHz (Channel 9)
          4   APs on   Frequency:2.462 GHz (Channel 11)
     
    wlan0     Scan completed :
              Cell 01 - Address: <MAC '' [AC1]>
                        Channel:11
                        Frequency:2.462 GHz (Channel 11)
                        Quality=66/70  Signal level=-44 dBm  
                        Encryption key:on
                        ESSID:""
                        Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                                  18 Mb/s; 36 Mb/s; 54 Mb/s
                        Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                        Mode:Master
                        Extra:tsf=000000048e987156
                        Extra: Last beacon: 60ms ago
                        IE: IEEE 802.11i/WPA2 Version 1
                            Group Cipher : CCMP
                            Pairwise Ciphers (1) : CCMP
                            Authentication Suites (1) : PSK
              Cell 02 - Address: <MAC '' [AC1]>
                        Channel:11
                        Frequency:2.462 GHz (Channel 11)
                        Quality=70/70  Signal level=-38 dBm  
                        Encryption key:on
                        ESSID:"MyNetwork"
                        Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                                  18 Mb/s; 36 Mb/s; 54 Mb/s
                        Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                        Mode:Master
                        Extra:tsf=00000004889d1987
                        Extra: Last beacon: 100164ms ago
                        IE: IEEE 802.11i/WPA2 Version 1
                            Group Cipher : CCMP
                            Pairwise Ciphers (1) : CCMP
                            Authentication Suites (1) : PSK
              Cell 03 - Address: <MAC 'casa 1' [AC3]>
                        Channel:1
                        Frequency:2.412 GHz (Channel 1)
                        Quality=39/70  Signal level=-71 dBm  
                        Encryption key:on
                        ESSID:"casa 1"
                        Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                                  9 Mb/s; 12 Mb/s; 18 Mb/s
                        Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                        Mode:Master
                        Extra:tsf=00000029c7d3dc02
                        Extra: Last beacon: 8ms ago
                        IE: IEEE 802.11i/WPA2 Version 1
                            Group Cipher : CCMP
                            Pairwise Ciphers (1) : CCMP
                            Authentication Suites (1) : PSK
                        IE: WPA Version 1
                            Group Cipher : CCMP
                            Pairwise Ciphers (1) : CCMP
                            Authentication Suites (1) : PSK
              Cell 04 - Address: <MAC 'NETGEAR' [AC4]>
                        Channel:11
                        Frequency:2.462 GHz (Channel 11)
                        Quality=34/70  Signal level=-76 dBm  
                        Encryption key:on
                        ESSID:"NETGEAR"
                        Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                                  24 Mb/s; 36 Mb/s; 54 Mb/s
                        Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                        Mode:Master
                        Extra:tsf=00000005fb9587df
                        Extra: Last beacon: 8ms ago
                        IE: IEEE 802.11i/WPA2 Version 1
                            Group Cipher : TKIP
                            Pairwise Ciphers (2) : CCMP TKIP
                            Authentication Suites (1) : PSK
                        IE: WPA Version 1
                            Group Cipher : TKIP
                            Pairwise Ciphers (2) : CCMP TKIP
                            Authentication Suites (1) : PSK
              Cell 05 - Address: <MAC 'Hmiranda' [AC5]>
                        Channel:6
                        Frequency:2.437 GHz (Channel 6)
                        Quality=21/70  Signal level=-89 dBm  
                        Encryption key:on
                        ESSID:"Hmiranda"
                        Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                                  18 Mb/s; 36 Mb/s; 54 Mb/s
                        Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                        Mode:Master
                        Extra:tsf=00000029c323c5d0
                        Extra: Last beacon: 8ms ago
                        IE: IEEE 802.11i/WPA2 Version 1
                            Group Cipher : CCMP
                            Pairwise Ciphers (1) : CCMP
                            Authentication Suites (1) : PSK
              Cell 06 - Address: <MAC 'Pousada-' [AC6]>
                        Channel:9
                        Frequency:2.452 GHz (Channel 9)
                        Quality=25/70  Signal level=-85 dBm  
                        Encryption key:on
                        ESSID:"Pousada-"
                        Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                                  24 Mb/s; 36 Mb/s; 54 Mb/s
                        Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                        Mode:Master
                        Extra:tsf=00000029bf17ad67
                        Extra: Last beacon: 632ms ago
                        IE: IEEE 802.11i/WPA2 Version 1
                            Group Cipher : CCMP
                            Pairwise Ciphers (1) : CCMP
                            Authentication Suites (1) : PSK
                        IE: WPA Version 1
                            Group Cipher : CCMP
                            Pairwise Ciphers (1) : CCMP
                            Authentication Suites (1) : PSK
              Cell 07 - Address: <MAC 'Andrade' [AC7]>
                        Channel:11
                        Frequency:2.462 GHz (Channel 11)
                        Quality=17/70  Signal level=-93 dBm  
                        Encryption key:on
                        ESSID:"Andrade"
                        Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                                  9 Mb/s; 12 Mb/s; 18 Mb/s
                        Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                        Mode:Master
                        Extra:tsf=00000029cf14b818
                        Extra: Last beacon: 8ms ago
                        IE: IEEE 802.11i/WPA2 Version 1
                            Group Cipher : TKIP
                            Pairwise Ciphers (2) : CCMP TKIP
                            Authentication Suites (1) : PSK
                        IE: WPA Version 1
                            Group Cipher : TKIP
                            Pairwise Ciphers (2) : CCMP TKIP
                            Authentication Suites (1) : PSK
              Cell 08 - Address: <MAC 'hunTT' [AC8]>
                        Channel:1
                        Frequency:2.412 GHz (Channel 1)
                        Quality=25/70  Signal level=-85 dBm  
                        Encryption key:on
                        ESSID:"hunTT"
                        Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                                  9 Mb/s; 12 Mb/s; 18 Mb/s
                        Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                        Mode:Master
                        Extra:tsf=00000029bfed5d80
                        Extra: Last beacon: 1648ms ago
                        IE: IEEE 802.11i/WPA2 Version 1
                            Group Cipher : CCMP
                            Pairwise Ciphers (1) : CCMP
                            Authentication Suites (1) : PSK
                        IE: WPA Version 1
                            Group Cipher : CCMP
                            Pairwise Ciphers (1) : CCMP
                            Authentication Suites (1) : PSK
              Cell 09 - Address: <MAC 'BRV' [AC9]>
                        Channel:4
                        Frequency:2.427 GHz (Channel 4)
                        Quality=22/70  Signal level=-88 dBm  
                        Encryption key:on
                        ESSID:"BRV"
                        Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                                  9 Mb/s; 12 Mb/s; 18 Mb/s
                        Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                        Mode:Master
                        Extra:tsf=00000001bbbc51b9
                        Extra: Last beacon: 8ms ago
                        IE: IEEE 802.11i/WPA2 Version 1
                            Group Cipher : CCMP
                            Pairwise Ciphers (1) : CCMP
                            Authentication Suites (1) : PSK
                        IE: WPA Version 1
                            Group Cipher : CCMP
                            Pairwise Ciphers (1) : CCMP
                            Authentication Suites (1) : PSK
     
    ##### module infos ######################
     
    [ath9k]
    filename:       /lib/modules/3.19.0-30-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k.ko
    license:        Dual BSD/GPL
    description:    Support for Atheros 802.11n wireless LAN cards.
    author:         Atheros Communications
    srcversion:     DFC03DD607884E899C8398C
    depends:        ath9k_hw,mac80211,ath9k_common,cfg80211,ath
    intree:         Y
    vermagic:       3.19.0-30-generic SMP mod_unload modversions
    signer:         Magrathea: Glacier signing key
    sig_key:        53:B8:7E:38:B5:24:CD:28:12:67:2F:C8:90:43:71:EA:0F:AB:DC:E5
    sig_hashalgo:   sha512
    parm:           debug:Debugging mask (uint)
    parm:           nohwcrypt:Disable hardware encryption (int)
    parm:           blink:Enable LED blink on activity (int)
    parm:           btcoex_enable:Enable wifi-BT coexistence (int)
    parm:           bt_ant_diversity:Enable WLAN/BT RX antenna diversity (int)
    parm:           ps_enable:Enable WLAN PowerSave (int)
    parm:           use_chanctx:Enable channel context for concurrency (int)
     
    [ath9k_common]
    filename:       /lib/modules/3.19.0-30-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_common.ko
    license:        Dual BSD/GPL
    description:    Shared library for Atheros wireless 802.11n LAN cards.
    author:         Atheros Communications
    srcversion:     8836292C9539A29CB162A5D
    depends:        ath9k_hw,cfg80211,ath
    intree:         Y
    vermagic:       3.19.0-30-generic SMP mod_unload modversions
    signer:         Magrathea: Glacier signing key
    sig_key:        53:B8:7E:38:B5:24:CD:28:12:67:2F:C8:90:43:71:EA:0F:AB:DC:E5
    sig_hashalgo:   sha512
     
    [ath9k_hw]
    filename:       /lib/modules/3.19.0-30-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_hw.ko
    license:        Dual BSD/GPL
    description:    Support for Atheros 802.11n wireless LAN cards.
    author:         Atheros Communications
    srcversion:     C1A24C37619ED65AB1240B9
    depends:        ath
    intree:         Y
    vermagic:       3.19.0-30-generic SMP mod_unload modversions
    signer:         Magrathea: Glacier signing key
    sig_key:        53:B8:7E:38:B5:24:CD:28:12:67:2F:C8:90:43:71:EA:0F:AB:DC:E5
    sig_hashalgo:   sha512
     
    [ath]
    filename:       /lib/modules/3.19.0-30-generic/kernel/drivers/net/wireless/ath/ath.ko
    license:        Dual BSD/GPL
    description:    Shared library for Atheros wireless LAN cards.
    author:         Atheros Communications
    srcversion:     D89F916A5E804AF040C4D29
    depends:        cfg80211
    intree:         Y
    vermagic:       3.19.0-30-generic SMP mod_unload modversions
    signer:         Magrathea: Glacier signing key
    sig_key:        53:B8:7E:38:B5:24:CD:28:12:67:2F:C8:90:43:71:EA:0F:AB:DC:E5
    sig_hashalgo:   sha512
     
    [mac80211]
    filename:       /lib/modules/3.19.0-30-generic/kernel/net/mac80211/mac80211.ko
    license:        GPL
    description:    IEEE 802.11 subsystem
    srcversion:     6AE775D26377F997426A49D
    depends:        cfg80211
    intree:         Y
    vermagic:       3.19.0-30-generic SMP mod_unload modversions
    signer:         Magrathea: Glacier signing key
    sig_key:        53:B8:7E:38:B5:24:CD:28:12:67:2F:C8:90:43:71:EA:0F:AB:DC:E5
    sig_hashalgo:   sha512
    parm:           minstrel_vht_only:Use only VHT rates when VHT is supported by sta. (bool)
    parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
    parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
    parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
    parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
    parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)
     
    [cfg80211]
    filename:       /lib/modules/3.19.0-30-generic/kernel/net/wireless/cfg80211.ko
    description:    wireless configuration support
    license:        GPL
    author:         Johannes Berg
    srcversion:     F28307769349A31F4B24FC2
    depends:        
    intree:         Y
    vermagic:       3.19.0-30-generic SMP mod_unload modversions
    signer:         Magrathea: Glacier signing key
    sig_key:        53:B8:7E:38:B5:24:CD:28:12:67:2F:C8:90:43:71:EA:0F:AB:DC:E5
    sig_hashalgo:   sha512
    parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
    parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)
     
    ##### module parameters #################
     
    [ath9k]
    blink: 0
    bt_ant_diversity: 0
    btcoex_enable: 0
    nohwcrypt: 1
    ps_enable: 0
    use_chanctx: 0
     
    [mac80211]
    beacon_loss_count: 7
    ieee80211_default_rc_algo: minstrel_ht
    max_nullfunc_tries: 2
    max_probe_tries: 5
    minstrel_vht_only: Y
    probe_wait_ms: 500
     
    [cfg80211]
    cfg80211_disable_40mhz_24ghz: N
    ieee80211_regdom: 00
     
    ##### /etc/modules ######################
     
    lp
    rtc
     
    ##### modprobe options ##################
     
    [/etc/modprobe.d/1blacklist-ath_pci.conf]
    blacklist ath_pci
     
    [/etc/modprobe.d/ath9k.conf]
    options ath9k nohwcrypt=1
     
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
     
    [/etc/modprobe.d/iwlwifi.conf]
    options iwlwifi 11n_disable=1
     
    [/etc/modprobe.d/mlx4.conf]
    softdep mlx4_core post: mlx4_en
     
    ##### rc.local ##########################
     
    exit 0
     
    ##### pm-utils ##########################
     
    ##### udev rules ########################
     
    [/etc/udev/rules.d/70-persistent-net.rules]
    # PCI device 0x1969:0x2062 (atl1c)
    SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
    # PCI device 0x168c:0x002b (ath9k)
    SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"
     
    ##### dmesg #############################
     
    [   14.826609] ath: phy0: Enable LNA combining
    [   14.832448] ath: phy0: ASPM enabled: 0x43
    [   14.832454] ath: EEPROM regdomain: 0x65
    [   14.832455] ath: EEPROM indicates we should expect a direct regpair map
    [   14.832458] ath: Country alpha2 being used: 00
    [   14.832460] ath: Regpair used: 0x65
    [   23.856223] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
    [   79.882314] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
    [   81.752094] wlan0: authenticate with <MAC '' [AC1]>
    [   81.773796] wlan0: send auth to <MAC '' [AC1]> (try 1/3)
    [   81.775591] wlan0: authenticated
    [   81.778398] wlan0: associate with <MAC '' [AC1]> (try 1/3)
    [   81.787649] wlan0: RX AssocResp from <MAC '' [AC1]> (capab=0xc11 status=0 aid=4)
    [   81.787801] wlan0: associated
    [   81.787837] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
    [   81.818764] ath: EEPROM regdomain: 0x8348
    [   81.818769] ath: EEPROM indicates we should expect a country code
    [   81.818771] ath: doing EEPROM country->regdmn map search
    [   81.818772] ath: country maps to regdmn code: 0x3a
    [   81.818774] ath: Country alpha2 being used: US
    [   81.818775] ath: Regpair used: 0x3a
    [   81.818777] ath: regdomain 0x8348 dynamically updated by country IE
     
    ########## wireless info END ############

```

Thanks in advance for any help

---

### Post by Hadaka on 2015-10-17
hi please open a terminal and do,,
```
echo "blacklist ideapad_laptop" | sudo tee -a  /etc/modprobe.d/blacklist/ideapad_laptop.conf
```
then go into network manager and set your IPV6 to Ignore  see screen shot.
[ATTACH=CONFIG]265013[/ATTACH]

---

### Post by SpaceCowboy64 on 2015-10-18
> **Hadaka said:**
> hi please open a terminal and do,,
```
echo "blacklist ideapad_laptop" | sudo tee -a  /etc/modprobe.d/blacklist/ideapad_laptop.conf
```
then go into network manager and set your IPV6 to Ignore  see screen shot.
[ATTACH=CONFIG]265013[/ATTACH]
Well, this worked for a while,but then, the connection was back unstable and sometimes with no connection. Any suggestion?
Thanks for the help

---

### Post by Hadaka on 2015-10-18
Hi,while connected to the internet please do..
```
sudo apt-get update && sudo apt-get upgrade
sudo apt-get autoremove && sudo apt-get autoclean
```
then go into the network manager and change your dns like the
attached for IPV4.
[ATTACH=CONFIG]265034[/ATTACH]

---

### Post by SpaceCowboy64 on 2015-10-18
> **Hadaka said:**
> Hi,while connected to the internet please do..
```
sudo apt-get update && sudo apt-get upgrade
sudo apt-get autoremove && sudo apt-get autoclean
```
then go into the network manager and change your dns like the
attached for IPV4.
[ATTACH=CONFIG]265034[/ATTACH]
This didn't work yet..
When I checked recently the system, I realize this:
```
 ariel@ArieLL-PC:~$ dmesg | grep ath
[    1.201962] Loaded X.509 cert 'Magrathea: Glacier signing key: 53b87e38b524cd2812672fc8904371ea0fabdce5'
[   14.356918] ath: phy0: Enable LNA combining
[   14.362458] ath: phy0: ASPM enabled: 0x43
[   14.362463] ath: EEPROM regdomain: 0x65
[   14.362465] ath: EEPROM indicates we should expect a direct regpair map
[   14.362468] ath: Country alpha2 being used: 00
[   14.362470] ath: Regpair used: 0x65
[   21.849035] ath: EEPROM regdomain: 0x8348
[   21.849039] ath: EEPROM indicates we should expect a country code
[   21.849040] ath: doing EEPROM country->regdmn map search
[   21.849042] ath: country maps to regdmn code: 0x3a
**[   21.849043] ath: Country alpha2 being used: US**
[   21.849045] ath: Regpair used: 0x3a
[   21.849046] ath: regdomain 0x8348 dynamically updated by country IE

```
Maybe the problem is in the countrycode, I'm in Brazil. Tomorrow I'll try to change it

---

### Post by Hadaka on 2015-10-18
Hi, it will depend on where you are..NorthEast Brazil or South Brazil
NE Brazil [MA, PI, CE, RN, PB]
S & SE Brazil [GO, DF, MG, ES, RJ, SP, PR, SC, RS]

here is the command. This *Example is US  note the uppercase letters
exchange the **US** for your Brazil code.
```
sudo iw reg set **US**
sudo sed -i 's/^REG.*=$/&**US**/' /etc/default/crda
```

---

