---
title: "Wireless N 300Mbps missing in Ubuntu"
date: 2014-06-03
forum: Networking &amp; Wireless
---

### Post by pressko on 2014-06-03
Dear All,

I have very odd problem. First of all my setup : 
WiFi router - mikrotik 2011uas-2hnd-in;
Client 1 - Ubuntu 14.04 with Network controller: Intel Corporation Centrino Wireless-N 1000 [Condor Peak]
Client 2 - Windows 7 with Network controller: Intel Corporation Centrino Wireless-N 1000 [Condor Peak]

The problem is that windows client is linking to the router with 300Mbps and Linux client is linking with max of 150 Mbps. I'm pretty sure that router is right configured.
Also tried Client 1 with windows setup and guess what... it's linking with 300Mbps. So my guess is that  something wrong going on with Ubuntu. Tried the mainline kernel (3.14.5) and default 3.13.0-27-generic, still no change. 


Here is some useful output from Ubuntu : 
```

 [B]grep -iR [a-z0-9] /sys/module/iwlwifi/parameters/
/sys/module/iwlwifi/parameters/nvm_file:(null)
/sys/module/iwlwifi/parameters/swcrypto:0
/sys/module/iwlwifi/parameters/power_save:N
/sys/module/iwlwifi/parameters/led_mode:0
/sys/module/iwlwifi/parameters/amsdu_size_8K:0
/sys/module/iwlwifi/parameters/fw_restart:Y
/sys/module/iwlwifi/parameters/bt_coex_active:Y
/sys/module/iwlwifi/parameters/11n_disable:0
/sys/module/iwlwifi/parameters/antenna_coupling:0
/sys/module/iwlwifi/parameters/wd_disable:1
/sys/module/iwlwifi/parameters/power_level:0
[/B]


[B]iw list
Wiphy phy0
    Band 1:
        Capabilities: 0x1072
            HT20/HT40
            Static SM Power Save
            RX Greenfield
            RX HT20 SGI
            RX HT40 SGI
            No RX STBC
            Max AMSDU length: 3839 bytes
            DSSS/CCK HT40
        Maximum RX AMPDU length 65535 bytes (exponent: 0x003)
        Minimum RX AMPDU time spacing: 4 usec (0x05)
        HT RX MCS rate indexes supported: 0-15, 32
        TX unequal modulation not supported
        HT TX Max spatial streams: 1
        HT TX MCS rate indexes supported may differ
        Frequencies:
            * 2412 MHz [1] (14.0 dBm)
            * 2417 MHz [2] (14.0 dBm)
            * 2422 MHz [3] (14.0 dBm)
            * 2427 MHz [4] (14.0 dBm)
            * 2432 MHz [5] (14.0 dBm)
            * 2437 MHz [6] (14.0 dBm)
            * 2442 MHz [7] (14.0 dBm)
            * 2447 MHz [8] (14.0 dBm)
            * 2452 MHz [9] (14.0 dBm)
            * 2457 MHz [10] (14.0 dBm)
            * 2462 MHz [11] (14.0 dBm)
            * 2467 MHz [12] (14.0 dBm) (passive scanning, no IBSS)
            * 2472 MHz [13] (14.0 dBm) (passive scanning, no IBSS)
        Bitrates (non-HT):
            * 1.0 Mbps
            * 2.0 Mbps (short preamble supported)
            * 5.5 Mbps (short preamble supported)
            * 11.0 Mbps (short preamble supported)
            * 6.0 Mbps
            * 9.0 Mbps
            * 12.0 Mbps
            * 18.0 Mbps
            * 24.0 Mbps
            * 36.0 Mbps
            * 48.0 Mbps
            * 54.0 Mbps
    max # scan SSIDs: 20
    max scan IEs length: 195 bytes
    Coverage class: 0 (up to 0m)
    Supported Ciphers:
        * WEP40 (00-0f-ac:1)
        * WEP104 (00-0f-ac:5)
        * TKIP (00-0f-ac:2)
        * CCMP (00-0f-ac:4)
    Available Antennas: TX 0 RX 0
    Supported interface modes:
         * IBSS
         * managed
         * monitor
    software interface modes (can always be added):
         * monitor
    interface combinations are not supported
    Supported commands:
         * new_interface
         * set_interface
         * new_key
         * new_beacon
         * new_station
         * new_mpath
         * set_mesh_params
         * set_bss
         * authenticate
         * associate
         * deauthenticate
         * disassociate
         * join_ibss
         * join_mesh
         * set_tx_bitrate_mask
         * action
         * frame_wait_cancel
         * set_wiphy_netns
         * set_channel
         * set_wds_peer
         * Unknown command (84)
         * Unknown command (87)
         * Unknown command (85)
         * Unknown command (89)
         * Unknown command (92)
         * Unknown command (104)
         * testmode
         * connect
         * disconnect
    Supported TX frame types:
         * IBSS: 0x00 0x10 0x20 0x30 0x40 0x50 0x60 0x70 0x80 0x90 0xa0 0xb0 0xc0 0xd0 0xe0 0xf0
         * managed: 0x00 0x10 0x20 0x30 0x40 0x50 0x60 0x70 0x80 0x90 0xa0 0xb0 0xc0 0xd0 0xe0 0xf0
         * AP: 0x00 0x10 0x20 0x30 0x40 0x50 0x60 0x70 0x80 0x90 0xa0 0xb0 0xc0 0xd0 0xe0 0xf0
         * AP/VLAN: 0x00 0x10 0x20 0x30 0x40 0x50 0x60 0x70 0x80 0x90 0xa0 0xb0 0xc0 0xd0 0xe0 0xf0
         * mesh point: 0x00 0x10 0x20 0x30 0x40 0x50 0x60 0x70 0x80 0x90 0xa0 0xb0 0xc0 0xd0 0xe0 0xf0
         * P2P-client: 0x00 0x10 0x20 0x30 0x40 0x50 0x60 0x70 0x80 0x90 0xa0 0xb0 0xc0 0xd0 0xe0 0xf0
         * P2P-GO: 0x00 0x10 0x20 0x30 0x40 0x50 0x60 0x70 0x80 0x90 0xa0 0xb0 0xc0 0xd0 0xe0 0xf0
         * Unknown mode (10): 0x00 0x10 0x20 0x30 0x40 0x50 0x60 0x70 0x80 0x90 0xa0 0xb0 0xc0 0xd0 0xe0 0xf0
    Supported RX frame types:
         * IBSS: 0x40 0xb0 0xc0 0xd0
         * managed: 0x40 0xd0
         * AP: 0x00 0x20 0x40 0xa0 0xb0 0xc0 0xd0
         * AP/VLAN: 0x00 0x20 0x40 0xa0 0xb0 0xc0 0xd0
         * mesh point: 0xb0 0xc0 0xd0
         * P2P-client: 0x40 0xd0
         * P2P-GO: 0x00 0x20 0x40 0xa0 0xb0 0xc0 0xd0
         * Unknown mode (10): 0x40 0xd0
    Device supports RSN-IBSS.
    HT Capability overrides:
         * MCS: ff ff ff ff ff ff ff ff ff ff
         * maximum A-MSDU length
         * supported channel width
         * short GI for 40 MHz
         * max A-MPDU length exponent
         * min MPDU start spacing
    Device supports TX status socket option.
    Device supports HT-IBSS.

iw dev wlan0 link
Connected to d4:ca:6d:e6:18:a3 (on wlan0)
    SSID: CvetyBaby
    freq: 2422
    RX: 113048205 bytes (122363 packets)
    TX: 67479855 bytes (74096 packets)
    signal: -35 dBm
    tx bitrate: 150.0 MBit/s MCS 7 40Mhz short GI

    bss flags:    short-preamble short-slot-time
    dtim period:    0
    beacon int:    100
[/B]
```

When i try to set MCS index to 15 with[B]:
[/B]```
[B]
# iw dev wlan0 set bitrates mcs-2.4 15
[/B]
```It's showing : **tx bitrate: 1MBit/s** 


Can you help me to figure it out? Thank you in advance! 

Best Regards,
Presian

---

### Post by varunendra on 2014-06-05
I doubt I can make it any better, but still, I'd like to see a detailed diagnostics report. Please follow the instructions in this post to download and run 'wireless_script' (experimental version) and post back the report it generates : [http://ubuntuforums.org/showpost.php?p=13024222](http://ubuntuforums.org/showpost.php?p=13024222)

In the meanwhile, you may try the following driver parameters - **swcrypto=1** and **bt_coex_active=N**. If you don't know how to use them, just post the report I asked above, and we'll try them according to the report.

---

### Post by pressko on 2014-06-05
> **varunendra said:**
> I doubt I can make it any better, but still, I'd like to see a detailed diagnostics report. Please follow the instructions in this post to download and run 'wireless_script' (experimental version) and post back the report it generates : [http://ubuntuforums.org/showpost.php?p=13024222](http://ubuntuforums.org/showpost.php?p=13024222)

In the meanwhile, you may try the following driver parameters - **swcrypto=1** and **bt_coex_active=N**. If you don't know how to use them, just post the report I asked above, and we'll try them according to the report.

Thank you for your replay! I think already tried **swcrypto=1 **and it makes no difference. I'm not quite sure where should i use **bt_coex_active=N**. 

Here is the output from diagnostic script :
```


    ======== Wireless-Info START ========

System-Info ~~~~~~~~~~~~~~~~~~~~~~~~

Y570 3.14.5 x86_64,  Ubuntu 14.04 LTS, trusty

CPU    : Intel(R) Core(TM) i7-2670QM CPU @ 2.20GHz
Memory : 5912 MB
Uptime : 20:01:11 up 14 min,  1 user,  load average: 0,27, 0,50, 0,49


lspci ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

07:00.0 Ethernet controller [0200]: Broadcom Corporation NetLink BCM57781 Gigabit Ethernet PCIe [14e4:16b1] (rev 10)
    Subsystem: Lenovo Device [17aa:3975]
    Kernel driver in use: tg3
08:00.0 Network controller [0280]: Intel Corporation Centrino Wireless-N 1000 [Condor Peak] [8086:0084]
    Subsystem: Intel Corporation Centrino Wireless-N 1000 BGN [8086:1315]
    Kernel driver in use: iwlwifi


lsusb ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Bus 002 Device 003: ID 5986:a006 Acer, Inc 
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


PCMCIA Card Info ~~~~~~~~~~~~~~~~~~~



iwconfig ~~~~~~~~~~~~~~~~~~~~~~~~~~~

wlan0     IEEE 802.11bgn  ESSID:"CvetyBaby"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: <MAC C-01 CvetyBaby>   
          Bit Rate=150 Mb/s   Tx-Power=14 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=70/70  Signal level=-35 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:188   Missed beacon:0



rfkill ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

      Interface                  Soft blocked  Hard blocked
0: ideapad_wlan: Wireless LAN        no            no
1: ideapad_bluetooth: Bluetooth      yes           no
2: phy0: Wireless LAN                no            no


lsmod ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

iwldvm                236252  0 
mac80211              644457  1 iwldvm
iwlwifi               173872  1 iwldvm
mxm_wmi                13021  0 
cfg80211              512135  3 iwlwifi,mac80211,iwldvm
wmi                    19177  1 mxm_wmi


module parameters ~~~~~~~~~~~~~~~~~~

cfg80211      (2): cfg80211_disable_40mhz_24ghz=N | ieee80211_regdom=00
iwlwifi      (11): 11n_disable=0 | amsdu_size_8K=0 | antenna_coupling=0 | bt_coex_active=Y | fw_restart=Y | led_mode=0 | nvm_file=(null) | power_level=0 | power_save=N | swcrypto=0 | wd_disable=1
mac80211      (5): beacon_loss_count=7 | ieee80211_default_rc_algo=minstrel_ht | max_nullfunc_tries=2 | max_probe_tries=5 | probe_wait_ms=500
wmi           (2): debug_dump_wdg=N | debug_event=N


nm-tool ~~~~~~~~~~~~~~~~~~~~~~~~~~~~

State: connected (global)
=========================o=============o=========o==============o=========o===========o==============o===========
 Interface & ID          | Type        | Driver  | State        | Default | Speed     | Support      | HW Addr   
=========================o=============o=========o==============o=========o===========o==============o===========
 wlan0  [Auto CvetyBaby] | 802.11 WiFi | iwlwifi | connected    | yes     | 150 Mb/s  | WEP/WPA/WPA2 | <MAC wlan0>

    Ivanov:          Infra, <MAC C-07 Ivanov>, Freq 2427 MHz, Rate 54 Mb/s, Strength 55 WPA
    Mimi86:          Infra, <MAC C-16 Mimi86>, Freq 2447 MHz, Rate 54 Mb/s, Strength 37 WPA2
    BlackP:          Infra, <MAC C-05 BlackP>, Freq 2437 MHz, Rate 54 Mb/s, Strength 50 WPA WPA2
    dlink:           Infra, <MAC C-04 dlink>, Freq 2417 MHz, Rate 54 Mb/s, Strength 24 WPA
    peychev:         Infra, <MAC C-18 peychev>, Freq 2437 MHz, Rate 54 Mb/s, Strength 50 WPA2
    harrys:          Infra, <MAC C-23 harrys>, Freq 2462 MHz, Rate 54 Mb/s, Strength 39 WPA WPA2
    Mira:            Infra, <MAC C-24 Mira>, Freq 2462 MHz, Rate 54 Mb/s, Strength 39 WPA WPA2
    Tenda_1B9788:    Infra, <MAC C-14 Tenda_1B9788>, Freq 2452 MHz, Rate 54 Mb/s, Strength 42 WPA
    Radoozzy:        Infra, <MAC C-03 Radoozzy>, Freq 2412 MHz, Rate 54 Mb/s, Strength 35 WPA2
    zoin:            Infra, <MAC C-NA zoin 1>, Freq 2462 MHz, Rate 54 Mb/s, Strength 25 WPA2
    maradona:        Infra, <MAC C-NA maradona 1>, Freq 2462 MHz, Rate 54 Mb/s, Strength 22 WPA WPA2
    *CvetyBaby:      Infra, <MAC C-01 CvetyBaby>, Freq 2462 MHz, Rate 54 Mb/s, Strength 83 WPA2
    Eli:             Infra, <MAC C-02 Eli>, Freq 2412 MHz, Rate 54 Mb/s, Strength 35 WPA WPA2
    TP-LINK_A6CA04:  Infra, <MAC C-22 TP-LINK_A6CA04>, Freq 2457 MHz, Rate 54 Mb/s, Strength 30 WPA WPA2
    Sasho:           Infra, <MAC C-NA Sasho 1>, Freq 2447 MHz, Rate 54 Mb/s, Strength 32 WPA2
    Nexus7Home:      Infra, <MAC C-NA Nexus7Home 1>, Freq 2412 MHz, Rate 54 Mb/s, Strength 35 WPA WPA2
    tin@tin:         Infra, <MAC C-20 tin@tin>, Freq 2457 MHz, Rate 54 Mb/s, Strength 39
    Niki:            Infra, <MAC C-NA Niki 1>, Freq 2452 MHz, Rate 54 Mb/s, Strength 20 WPA2
    Diana:           Infra, <MAC C-11 Diana>, Freq 2437 MHz, Rate 54 Mb/s, Strength 40 WPA
    Joreto:          Infra, <MAC C-19 Joreto>, Freq 2452 MHz, Rate 54 Mb/s, Strength 34 WPA WPA2
    Chep za zele:    Infra, <MAC C-NA Chep za zele 1>, Freq 2472 MHz, Rate 54 Mb/s, Strength 20 WPA WPA2
    Ivan:            Infra, <MAC C-21 Ivan>, Freq 2452 MHz, Rate 54 Mb/s, Strength 27 WPA WPA2
    Cas7ell0_jr:     Infra, <MAC C-25 Cas7ell0_jr>, Freq 2472 MHz, Rate 54 Mb/s, Strength 22 WPA WPA2
    NET1 WiFi:       Infra, <MAC C-NA NET1 WiFi 1>, Freq 2437 MHz, Rate 54 Mb/s, Strength 22
    Youlia:          Infra, <MAC C-NA Youlia 1>, Freq 2442 MHz, Rate 54 Mb/s, Strength 35 WPA WPA2
    Boyan:           Infra, <MAC C-13 Boyan>, Freq 2437 MHz, Rate 54 Mb/s, Strength 29 WPA
    nadyabg:         Infra, <MAC C-15 nadyabg>, Freq 2447 MHz, Rate 54 Mb/s, Strength 97 WPA WPA2
    Tenda_1B9788:    Infra, <MAC C-14 Tenda_1B9788>, Freq 2442 MHz, Rate 54 Mb/s, Strength 42 WPA
    Bai HUI:         Infra, <MAC C-12 Bai HUI>, Freq 2437 MHz, Rate 54 Mb/s, Strength 37 WPA2

    Address:         192.168.88.254
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.88.1
    DNS:             192.168.88.1
-------------------------+-------------+---------+--------------+---------+-----------+--------------+-----------
 eth0                    | Wired       | tg3     | unavailable  | no      |           |              | <MAC eth0>
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

no-auto-default=<MAC eth0>,<MAC ID removed>,

[ifupdown]
managed=false


NM WiFi Profiles ~~~~~~~~~~~~~~~~~~~

Auto Abajur          : ssid=Abajur | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 
Auto Adriana         : ssid=Adriana | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 
Auto alibaba         : ssid=alibaba | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 
Auto Cekovi          : ssid=Cekovi | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 
Auto cvetybaby       : ssid=cvetybaby | mac-address=<MAC wlan0> | ipv6=auto | ipv4=auto 
Auto Cvetybaby       : ssid=Cvetybaby | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 
Auto CvetyBaby       : ssid=CvetyBaby | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 
Auto CvetyBaby       : ssid=CvetyBaby | mac-address=<MAC wlan0> | ipv6=auto | ipv4=auto 
Auto cvetybaby       : ssid=cvetybaby | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 
Auto EnGeniusCC992C  : ssid=EnGeniusCC992C | mac-address=<MAC wlan0> | ipv6=auto | ipv4=manual 
Auto KempiSof        : ssid=KempiSof | mac-address=<MAC wlan0> | ipv6=auto | ipv4=auto 
Auto KempiSof-MADARA : ssid=KempiSof-MADARA | mac-address=<MAC wlan0> | ipv6=auto | ipv4=auto 
Auto KempiSof-WiFi   : ssid=KempiSof-WiFi | mac-address=<MAC wlan0> | ipv6=auto | ipv4=auto 
Auto MikroTik-1B538F : ssid=MikroTik-1B538F | mac-address=<MAC wlan0> | ipv6=auto | ipv4=auto 
Auto MikroTik-C7F29F : ssid=MikroTik-C7F29F | mac-address=<MAC wlan0> | ipv6=auto | ipv4=auto 
Auto MikroTik-E618A3 : ssid=MikroTik-E618A3 | mac-address=<MAC wlan0> | ipv6=auto | ipv4=auto 
Auto Mr.Pizza        : ssid=Mr.Pizza | mac-address=<MAC wlan0> | ipv6=auto | ipv4=manual 
Auto Mr.Pizza        : ssid=Mr.Pizza | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 
Auto Net IS Sat-3G   : ssid=Net IS Sat-3G | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 
Auto NETISSAT_3G     : ssid=NETISSAT_3G | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 
Auto Net IS Sat-3G   : ssid=Net IS Sat-3G | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 
Auto Net IS Sat-3G   : ssid=Net IS Sat-3G | mac-address=<MAC wlan1> | ipv4=auto | ipv6=auto 
Auto NETISSAT-Admin  : ssid=NETISSAT-Admin | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 
Auto punkmaster      : ssid=punkmaster | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 
Auto SEE3            : ssid=SEE3 | mac-address=<MAC wlan0> | ipv6=auto | ipv4=auto 
Auto Tenda           : ssid=Tenda | mac-address=<MAC wlan0> | ipv6=auto | ipv4=auto 
Auto VedraInt        : ssid=VedraInt | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 
Auto VedraINT        : ssid=VedraINT | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 
Auto Vedra-INT       : ssid=Vedra-INT | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 


interfaces ~~~~~~~~~~~~~~~~~~~~~~~~~

# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback

resolv.conf ~~~~~~~~~~~~~~~~~~~~~~~~

nameserver 192.168.88.1


Routes & Ping ~~~~~~~~~~~~~~~~~~~~~~

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.88.1    0.0.0.0         UG    0      0        0 wlan0
192.168.88.0    0.0.0.0         255.255.255.0   U     9      0        0 wlan0

--- 192.168.88.1 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 1001ms
rtt min/avg/max/mdev = 5.043/5.092/5.142/0.086 ms

--- 192.168.88.1 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 1001ms
rtt min/avg/max/mdev = 3.285/4.257/5.229/0.972 ms


iw reg get ~~~~~~~~~~~~~~~~~~~~~~~~~

(Region : bg_BG.UTF-8)
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
          Cell 01 - Address: <MAC C-01 CvetyBaby>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=70/70  Signal level=-31 dBm  
                    Encryption key:on
                    ESSID:"CvetyBaby"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000001e3c2e8c90
                    Extra: Last beacon: 24ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC C-02 Eli>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=34/70  Signal level=-76 dBm  
                    Encryption key:on
                    ESSID:"Eli"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000b3c89147e2
                    Extra: Last beacon: 24ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: <MAC C-03 Radoozzy>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=36/70  Signal level=-74 dBm  
                    Encryption key:on
                    ESSID:"Radoozzy"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000b3c9618a89
                    Extra: Last beacon: 24ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 04 - Address: <MAC C-04 dlink>
                    Channel:2
                    Frequency:2.417 GHz (Channel 2)
                    Quality=29/70  Signal level=-81 dBm  
                    Encryption key:on
                    ESSID:"dlink"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000654c76f181
                    Extra: Last beacon: 1260ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 05 - Address: <MAC C-05 BlackP>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=27/70  Signal level=-83 dBm  
                    Encryption key:on
                    ESSID:"BlackP"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000098c5ce77b
                    Extra: Last beacon: 24ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 06 - Address: <MAC C-06 viliqna>
                    Channel:4
                    Frequency:2.427 GHz (Channel 4)
                    Quality=28/70  Signal level=-82 dBm  
                    Encryption key:on
                    ESSID:"viliqna"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s
                    Bit Rates:9 Mb/s; 18 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000516a61a37
                    Extra: Last beacon: 24ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                       Preauthentication Supported
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
          Cell 07 - Address: <MAC C-07 Ivanov>
                    Channel:4
                    Frequency:2.427 GHz (Channel 4)
                    Quality=46/70  Signal level=-64 dBm  
                    Encryption key:on
                    ESSID:"Ivanov"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000006b25aa8bb6
                    Extra: Last beacon: 24ms ago
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 08 - Address: <MAC C-08 TP-LINK_DF5384>
                    Channel:5
                    Frequency:2.432 GHz (Channel 5)
                    Quality=31/70  Signal level=-79 dBm  
                    Encryption key:on
                    ESSID:"TP-LINK_DF5384"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000b3c961a92e
                    Extra: Last beacon: 24ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 09 - Address: <MAC C-09 UNIX>
                    Channel:5
                    Frequency:2.432 GHz (Channel 5)
                    Quality=26/70  Signal level=-84 dBm  
                    Encryption key:on
                    ESSID:"UNIX"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000b3c9ccf342
                    Extra: Last beacon: 24ms ago
          Cell 10 - Address: <MAC C-10 new-09>
                    Channel:5
                    Frequency:2.432 GHz (Channel 5)
                    Quality=27/70  Signal level=-83 dBm  
                    Encryption key:on
                    ESSID:"new-09"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000b3c88ccd40
                    Extra: Last beacon: 24ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 11 - Address: <MAC C-11 Diana>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=35/70  Signal level=-75 dBm  
                    Encryption key:on
                    ESSID:"Diana"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s
                    Bit Rates:9 Mb/s; 18 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000004103c1b82d
                    Extra: Last beacon: 24ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
          Cell 12 - Address: <MAC C-12 Bai HUI>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=27/70  Signal level=-83 dBm  
                    Encryption key:on
                    ESSID:"Bai HUI"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000008559fd796
                    Extra: Last beacon: 892ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 13 - Address: <MAC C-13 Boyan>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=28/70  Signal level=-82 dBm  
                    Encryption key:on
                    ESSID:"Boyan"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000000f656894d
                    Extra: Last beacon: 24ms ago
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 14 - Address: <MAC C-14 Tenda_1B9788>
                    Channel:7
                    Frequency:2.442 GHz (Channel 7)
                    Quality=35/70  Signal level=-75 dBm  
                    Encryption key:on
                    ESSID:"Tenda_1B9788"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000003d11b04a5a
                    Extra: Last beacon: 24ms ago
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 15 - Address: <MAC C-15 nadyabg>
                    Channel:8
                    Frequency:2.447 GHz (Channel 8)
                    Quality=67/70  Signal level=-43 dBm  
                    Encryption key:on
                    ESSID:"nadyabg"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000000039f9a11
                    Extra: Last beacon: 24ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 16 - Address: <MAC C-16 Mimi86>
                    Channel:8
                    Frequency:2.447 GHz (Channel 8)
                    Quality=32/70  Signal level=-78 dBm  
                    Encryption key:on
                    ESSID:"Mimi86"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000008b3cd74cc3
                    Extra: Last beacon: 24ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 17 - Address: <MAC C-17 Ficheto>
                    Channel:8
                    Frequency:2.447 GHz (Channel 8)
                    Quality=25/70  Signal level=-85 dBm  
                    Encryption key:on
                    ESSID:"Ficheto"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000b3c8b923fb
                    Extra: Last beacon: 24ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 18 - Address: <MAC C-18 peychev>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=32/70  Signal level=-78 dBm  
                    Encryption key:on
                    ESSID:"peychev"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000006a55e5b5
                    Extra: Last beacon: 684ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 19 - Address: <MAC C-19 Joreto>
                    Channel:9
                    Frequency:2.452 GHz (Channel 9)
                    Quality=27/70  Signal level=-83 dBm  
                    Encryption key:on
                    ESSID:"Joreto"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000018ac08c516
                    Extra: Last beacon: 24ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 20 - Address: <MAC C-20 tin@tin>
                    Channel:10
                    Frequency:2.457 GHz (Channel 10)
                    Quality=31/70  Signal level=-79 dBm  
                    Encryption key:off
                    ESSID:"tin@tin"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000001be5a9a268
                    Extra: Last beacon: 636ms ago
          Cell 21 - Address: <MAC C-21 Ivan>
                    Channel:9
                    Frequency:2.452 GHz (Channel 9)
                    Quality=31/70  Signal level=-79 dBm  
                    Encryption key:on
                    ESSID:"Ivan"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000015c25183
                    Extra: Last beacon: 632ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 22 - Address: <MAC C-22 TP-LINK_A6CA04>
                    Channel:10
                    Frequency:2.457 GHz (Channel 10)
                    Quality=28/70  Signal level=-82 dBm  
                    Encryption key:on
                    ESSID:"TP-LINK_A6CA04"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000030a1c942f0
                    Extra: Last beacon: 24ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 23 - Address: <MAC C-23 harrys>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=34/70  Signal level=-76 dBm  
                    Encryption key:on
                    ESSID:"harrys"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000006b25943f05
                    Extra: Last beacon: 24ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 24 - Address: <MAC C-24 Mira>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=37/70  Signal level=-73 dBm  
                    Encryption key:on
                    ESSID:"Mira"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000083cfbd191
                    Extra: Last beacon: 24ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 25 - Address: <MAC C-25 Cas7ell0_jr>
                    Channel:13
                    Frequency:2.472 GHz (Channel 13)
                    Quality=22/70  Signal level=-88 dBm  
                    Encryption key:on
                    ESSID:"Cas7ell0_jr"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000012d99ab0
                    Extra: Last beacon: 24ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK


blacklist ~~~~~~~~~~~~~~~~~~~~~~~~~~

[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci

[/etc/modprobe.d/bumblebee.conf]
blacklist nouveau
blacklist nvidia
blacklist nvidia-current
blacklist nvidia-current-updates
blacklist nvidia-304
blacklist nvidia-304-updates
blacklist nvidia-experimental-304
blacklist nvidia-310
blacklist nvidia-310-updates
blacklist nvidia-experimental-310
blacklist nvidia-313
blacklist nvidia-313-updates
blacklist nvidia-experimental-313
blacklist nvidia-319
blacklist nvidia-319-updates
blacklist nvidia-experimental-319
blacklist nvidia-325
blacklist nvidia-325-updates
blacklist nvidia-experimental-325
blacklist nvidia-331
blacklist nvidia-331-updates
blacklist nvidia-experimental-331
blacklist nvidia-334
blacklist nvidia-334-updates
blacklist nvidia-experimental-334
blacklist nvidia-337
blacklist nvidia-337-updates
blacklist nvidia-experimental-337


modinfo ~~~~~~~~~~~~~~~~~~~~~~~~~~~~

[iwldvm]
filename:       /lib/modules/3.14.5/kernel/drivers/net/wireless/iwlwifi/dvm/iwldvm.ko
version:        in-tree:
srcversion:     179A379BD0445B7DE86A2F1
depends:        iwlwifi,mac80211,cfg80211

[mac80211]
filename:       /lib/modules/3.14.5/kernel/net/mac80211/mac80211.ko
srcversion:     32EDEFC4B81844BEA7AC047
depends:        cfg80211
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[iwlwifi]
filename:       /lib/modules/3.14.5/kernel/drivers/net/wireless/iwlwifi/iwlwifi.ko
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
srcversion:     900BC7FF805B79DE0D82BFF
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
filename:       /lib/modules/3.14.5/kernel/net/wireless/cfg80211.ko
srcversion:     0739D3437930A94073358B8
depends:        
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)


udev rules ~~~~~~~~~~~~~~~~~~~~~~~~~

# PCI device 0x14e4:0x16b1 (tg3)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC eth0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

# PCI device 0x8086:0x0084 (iwlwifi)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC wlan0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

# PCI device 0x8086:0x0888 (iwlwifi)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC wlan1>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan1"


Custom files/entries ~~~~~~~~~~~~~~~

/etc/modules        : Not Default
/etc/rc.local       : Default
/etc/modprobe.d     : Not Default
/etc/pm/(cnf|pw|sl) : Not Default

[/etc/modules]
coretemp
coretemp

[/etc/modprobe.d]
iwlwifi.conf      : remove iwlwifi \
                    (/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
                    && /sbin/modprobe -r mac80211
mlx4.conf         : softdep mlx4_core post: mlx4_en

[/etc/pm/power.d/95hdparm-apm] [executable]
#!/bin/sh
# tlp - if tlp is enabled, override corresponding script
#       in /usr/lib*/pm-utils/power.d/

CONFFILE=/etc/default/tlp
LIBDIRS='/usr/lib /usr/lib64'

for d in ${LIBDIRS}; do
    if [ -d "${d}/pm-utils/power.d" ]; then
        blocked="${d}/pm-utils/power.d/${0##*/}"
        break
    fi
done

if [ -n "$blocked" ] && [ -x "$blocked" ]; then
    # else nothing to disable -> don't read $CONFFILE

    if [ -e "$CONFFILE" ] && . "$CONFFILE" -- && [ "$TLP_ENABLE" = '1' ]; then
        # TLP is enabled -> disable $blocked
        echo "Notice: '${blocked}' disabled by TLP."
    else
        exec "$blocked" $*
    fi
fi

exit 0

[/etc/pm/power.d/disable_wol] [executable]
#!/bin/sh
# tlp - if tlp is enabled, override corresponding script
#       in /usr/lib*/pm-utils/power.d/

CONFFILE=/etc/default/tlp
LIBDIRS='/usr/lib /usr/lib64'

for d in ${LIBDIRS}; do
    if [ -d "${d}/pm-utils/power.d" ]; then
        blocked="${d}/pm-utils/power.d/${0##*/}"
        break
    fi
done

if [ -n "$blocked" ] && [ -x "$blocked" ]; then
    # else nothing to disable -> don't read $CONFFILE

    if [ -e "$CONFFILE" ] && . "$CONFFILE" -- && [ "$TLP_ENABLE" = '1' ]; then
        # TLP is enabled -> disable $blocked
        echo "Notice: '${blocked}' disabled by TLP."
    else
        exec "$blocked" $*
    fi
fi

exit 0

[/etc/pm/power.d/intel-audio-powersave] [executable]
#!/bin/sh
# tlp - if tlp is enabled, override corresponding script
#       in /usr/lib*/pm-utils/power.d/

CONFFILE=/etc/default/tlp
LIBDIRS='/usr/lib /usr/lib64'

for d in ${LIBDIRS}; do
    if [ -d "${d}/pm-utils/power.d" ]; then
        blocked="${d}/pm-utils/power.d/${0##*/}"
        break
    fi
done

if [ -n "$blocked" ] && [ -x "$blocked" ]; then
    # else nothing to disable -> don't read $CONFFILE

    if [ -e "$CONFFILE" ] && . "$CONFFILE" -- && [ "$TLP_ENABLE" = '1' ]; then
        # TLP is enabled -> disable $blocked
        echo "Notice: '${blocked}' disabled by TLP."
    else
        exec "$blocked" $*
    fi
fi

exit 0

[/etc/pm/power.d/laptop-mode] [executable]
#!/bin/sh
# tlp - if tlp is enabled, override corresponding script
#       in /usr/lib*/pm-utils/power.d/

CONFFILE=/etc/default/tlp
LIBDIRS='/usr/lib /usr/lib64'

for d in ${LIBDIRS}; do
    if [ -d "${d}/pm-utils/power.d" ]; then
        blocked="${d}/pm-utils/power.d/${0##*/}"
        break
    fi
done

if [ -n "$blocked" ] && [ -x "$blocked" ]; then
    # else nothing to disable -> don't read $CONFFILE

    if [ -e "$CONFFILE" ] && . "$CONFFILE" -- && [ "$TLP_ENABLE" = '1' ]; then
        # TLP is enabled -> disable $blocked
        echo "Notice: '${blocked}' disabled by TLP."
    else
        exec "$blocked" $*
    fi
fi

exit 0

[/etc/pm/power.d/pci_devices] [executable]
#!/bin/sh
# tlp - if tlp is enabled, override corresponding script
#       in /usr/lib*/pm-utils/power.d/

CONFFILE=/etc/default/tlp
LIBDIRS='/usr/lib /usr/lib64'

for d in ${LIBDIRS}; do
    if [ -d "${d}/pm-utils/power.d" ]; then
        blocked="${d}/pm-utils/power.d/${0##*/}"
        break
    fi
done

if [ -n "$blocked" ] && [ -x "$blocked" ]; then
    # else nothing to disable -> don't read $CONFFILE

    if [ -e "$CONFFILE" ] && . "$CONFFILE" -- && [ "$TLP_ENABLE" = '1' ]; then
        # TLP is enabled -> disable $blocked
        echo "Notice: '${blocked}' disabled by TLP."
    else
        exec "$blocked" $*
    fi
fi

exit 0

[/etc/pm/power.d/pcie_aspm] [executable]
#!/bin/sh
# tlp - if tlp is enabled, override corresponding script
#       in /usr/lib*/pm-utils/power.d/

CONFFILE=/etc/default/tlp
LIBDIRS='/usr/lib /usr/lib64'

for d in ${LIBDIRS}; do
    if [ -d "${d}/pm-utils/power.d" ]; then
        blocked="${d}/pm-utils/power.d/${0##*/}"
        break
    fi
done

if [ -n "$blocked" ] && [ -x "$blocked" ]; then
    # else nothing to disable -> don't read $CONFFILE

    if [ -e "$CONFFILE" ] && . "$CONFFILE" -- && [ "$TLP_ENABLE" = '1' ]; then
        # TLP is enabled -> disable $blocked
        echo "Notice: '${blocked}' disabled by TLP."
    else
        exec "$blocked" $*
    fi
fi

exit 0

[/etc/pm/power.d/sata_alpm] [executable]
#!/bin/sh
# tlp - if tlp is enabled, override corresponding script
#       in /usr/lib*/pm-utils/power.d/

CONFFILE=/etc/default/tlp
LIBDIRS='/usr/lib /usr/lib64'

for d in ${LIBDIRS}; do
    if [ -d "${d}/pm-utils/power.d" ]; then
        blocked="${d}/pm-utils/power.d/${0##*/}"
        break
    fi
done

if [ -n "$blocked" ] && [ -x "$blocked" ]; then
    # else nothing to disable -> don't read $CONFFILE

    if [ -e "$CONFFILE" ] && . "$CONFFILE" -- && [ "$TLP_ENABLE" = '1' ]; then
        # TLP is enabled -> disable $blocked
        echo "Notice: '${blocked}' disabled by TLP."
    else
        exec "$blocked" $*
    fi
fi

exit 0

[/etc/pm/power.d/sched-powersave] [executable]
#!/bin/sh
# tlp - if tlp is enabled, override corresponding script
#       in /usr/lib*/pm-utils/power.d/

CONFFILE=/etc/default/tlp
LIBDIRS='/usr/lib /usr/lib64'

for d in ${LIBDIRS}; do
    if [ -d "${d}/pm-utils/power.d" ]; then
        blocked="${d}/pm-utils/power.d/${0##*/}"
        break
    fi
done

if [ -n "$blocked" ] && [ -x "$blocked" ]; then
    # else nothing to disable -> don't read $CONFFILE

    if [ -e "$CONFFILE" ] && . "$CONFFILE" -- && [ "$TLP_ENABLE" = '1' ]; then
        # TLP is enabled -> disable $blocked
        echo "Notice: '${blocked}' disabled by TLP."
    else
        exec "$blocked" $*
    fi
fi

exit 0

[/etc/pm/power.d/usb_bluetooth] [executable]
#!/bin/sh
# tlp - if tlp is enabled, override corresponding script
#       in /usr/lib*/pm-utils/power.d/

CONFFILE=/etc/default/tlp
LIBDIRS='/usr/lib /usr/lib64'

for d in ${LIBDIRS}; do
    if [ -d "${d}/pm-utils/power.d" ]; then
        blocked="${d}/pm-utils/power.d/${0##*/}"
        break
    fi
done

if [ -n "$blocked" ] && [ -x "$blocked" ]; then
    # else nothing to disable -> don't read $CONFFILE

    if [ -e "$CONFFILE" ] && . "$CONFFILE" -- && [ "$TLP_ENABLE" = '1' ]; then
        # TLP is enabled -> disable $blocked
        echo "Notice: '${blocked}' disabled by TLP."
    else
        exec "$blocked" $*
    fi
fi

exit 0

[/etc/pm/power.d/wireless] [executable]
#!/bin/sh
# tlp - if tlp is enabled, override corresponding script
#       in /usr/lib*/pm-utils/power.d/

CONFFILE=/etc/default/tlp
LIBDIRS='/usr/lib /usr/lib64'

for d in ${LIBDIRS}; do
    if [ -d "${d}/pm-utils/power.d" ]; then
        blocked="${d}/pm-utils/power.d/${0##*/}"
        break
    fi
done

if [ -n "$blocked" ] && [ -x "$blocked" ]; then
    # else nothing to disable -> don't read $CONFFILE

    if [ -e "$CONFFILE" ] && . "$CONFFILE" -- && [ "$TLP_ENABLE" = '1' ]; then
        # TLP is enabled -> disable $blocked
        echo "Notice: '${blocked}' disabled by TLP."
    else
        exec "$blocked" $*
    fi
fi

exit 0

[/etc/pm/power.d/xfs_buffer] [executable]
#!/bin/sh
# tlp - if tlp is enabled, override corresponding script
#       in /usr/lib*/pm-utils/power.d/

CONFFILE=/etc/default/tlp
LIBDIRS='/usr/lib /usr/lib64'

for d in ${LIBDIRS}; do
    if [ -d "${d}/pm-utils/power.d" ]; then
        blocked="${d}/pm-utils/power.d/${0##*/}"
        break
    fi
done

if [ -n "$blocked" ] && [ -x "$blocked" ]; then
    # else nothing to disable -> don't read $CONFFILE

    if [ -e "$CONFFILE" ] && . "$CONFFILE" -- && [ "$TLP_ENABLE" = '1' ]; then
        # TLP is enabled -> disable $blocked
        echo "Notice: '${blocked}' disabled by TLP."
    else
        exec "$blocked" $*
    fi
fi

exit 0

[/etc/pm/sleep.d/00_check_touchpad_status]
#!/bin/sh
#copy to /etc/pm/sleep.d
LOGFILE="/var/log/sleep.log"

case "$1" in
        resume|thaw)
                echo "Resumed from suspend at `date`" >> "$LOGFILE"
                /usr/bin/python3 /opt/extras.ubuntu.com/touchpad-indicator/share/touchpad-indicator/check_touchpad_status.py
                echo "Touchpad enabled"
                ;;
esac

[/etc/pm/sleep.d/50-razer] [executable]
#!/bin/sh

razer_suspend()
{
    true # Do nothing
}

razer_resume()
{
    /usr/local/bin/razercfg -B -K
}

case $1 in
    hibernate|suspend)
        razer_suspend
        ;;
    resume|thaw)
        razer_resume
        ;;
esac


Kernel boot line ~~~~~~~~~~~~~~~~~~~

BOOT_IMAGE=/boot/vmlinuz-3.14.5 root=UUID=0b860d42-810e-448d-8857-e9b071e4e3a0 ro persistent


dmesg ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

[    0.027813] Initializing cgroup subsys net_cls
[    0.027821] Initializing cgroup subsys net_prio
[    1.022788] audit: initializing netlink subsys (disabled)
[    5.427636] tg3 0000:07:00.0 eth0: attached PHY is 57765 (10/100/1000Base-T Ethernet) (WireSpeed[1], EEE[1])
[   17.754103] wmi: Mapper loaded
[   17.762739] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[   18.759815] iwlwifi: module has bad taint, not creating trace events
[   18.759973] iwlwifi 0000:08:00.0: can't disable ASPM; OS doesn't have ASPM control
[   18.760035] iwlwifi 0000:08:00.0: irq 51 for MSI/MSI-X
[   18.992540] iwlwifi 0000:08:00.0: loaded firmware version 39.31.5.1 build 35138 op_mode iwldvm
[   19.265715] iwlwifi 0000:08:00.0: CONFIG_IWLWIFI_DEBUG disabled
[   19.265716] iwlwifi 0000:08:00.0: CONFIG_IWLWIFI_DEBUGFS enabled
[   19.265716] iwlwifi 0000:08:00.0: CONFIG_IWLWIFI_DEVICE_TRACING enabled
[   19.265718] iwlwifi 0000:08:00.0: Detected Intel(R) Centrino(R) Wireless-N 1000 BGN, REV=0x6C
[   19.265816] iwlwifi 0000:08:00.0: L1 Enabled; Disabling L0S
[   19.315647] ieee80211 phy0: Selected rate control algorithm 'iwl-agn-rs'
[   32.939345] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   38.907363] iwlwifi 0000:08:00.0: L1 Enabled; Disabling L0S
[   38.914803] iwlwifi 0000:08:00.0: Radio type=0x0-0x0-0x3
[   38.952239] iwlwifi 0000:08:00.0: L1 Enabled; Disabling L0S
[   38.959636] iwlwifi 0000:08:00.0: Radio type=0x0-0x0-0x3
[   39.033548] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   40.834672] wlan0: authenticate with <MAC C-01 CvetyBaby>
[   40.850320] wlan0: send auth to <MAC C-01 CvetyBaby> (try 1/3)
[   40.852205] wlan0: authenticated
[   40.852853] wlan0: associate with <MAC C-01 CvetyBaby> (try 1/3)
[   40.859956] wlan0: RX AssocResp from <MAC C-01 CvetyBaby> (capab=0x431 status=0 aid=3)
[   40.876801] wlan0: associated
[   40.876813] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   41.038487] wlan0: deauthenticating from <MAC C-01 CvetyBaby> by local choice (reason=2)
[   41.048400] wlan0: authenticate with <MAC C-01 CvetyBaby>
[   41.063137] wlan0: send auth to <MAC C-01 CvetyBaby> (try 1/3)
[   41.065719] wlan0: authenticated
[   41.069067] wlan0: associate with <MAC C-01 CvetyBaby> (try 1/3)
[   41.076863] wlan0: RX AssocResp from <MAC C-01 CvetyBaby> (capab=0x431 status=0 aid=3)
[   41.094435] wlan0: associated
[   74.311579] thinkpad_acpi: http://ibm-acpi.sf.net/

    ======== Done ========



```

Cheers!

PS: Just tried with
```

/sys/module/iwlwifi/parameters/nvm_file:(null)
/sys/module/iwlwifi/parameters/swcrypto:1
/sys/module/iwlwifi/parameters/power_save:N
/sys/module/iwlwifi/parameters/led_mode:0
/sys/module/iwlwifi/parameters/amsdu_size_8K:0
/sys/module/iwlwifi/parameters/fw_restart:Y
/sys/module/iwlwifi/parameters/bt_coex_active:N
/sys/module/iwlwifi/parameters/11n_disable:0
/sys/module/iwlwifi/parameters/antenna_coupling:0
/sys/module/iwlwifi/parameters/wd_disable:1
/sys/module/iwlwifi/parameters/power_level:0

```

And still can't get 300Mbps. I'm thinking what is so different between Windows and Linux setup/drivers ?

---

### Post by varunendra on 2014-06-06
> **pressko said:**
> I'm thinking what is so different between Windows and Linux setup/drivers ?

Windows drivers are developed by device manufacturers themselves (hence coded or 'patched' to deliver optimal performance), while the Linux drivers are developed mostly by volunteers, only the firmware (where applicable) is supplied by the manufacturers.

You are using 'tlp', which includes scripts that try to save power on all devices, including wireless, as much and as often as possible. I'm not sure how much these scripts or the whole package can affect the wireless performance, but can you try Ubuntu (same version) in Live mode so we can determine if the link/speed is same or different without this package? If it seems to perform better in Live mode, you may try disabling the wireless power-saving script by removing its 'executable' permission -
```
sudo chmod -x /etc/pm/power.d/wireless
```

And make sure the "Power Management" is "on" in 'iwconfig' output, and remains 'on' -
```
sudo iwconfig wlan0 power off
```
Then try disconnecting - reconnecting the wifi and see if the link speed improves.

Oh, and at this high speed (even 150 Mb/s), you might wish to make the 'swcrypto=1' parameter permanent by adding a line -
```
options iwlwifi swcrypto=1
```
..into your **/etc/modprobe.d/iwlwifi.conf** file. No need for that if the 'Actual' file transfer speed looks good and consistent with the 'Link' speed. But if you notice too slow speeds compared to 'Link' speed, try that.

---

### Post by pressko on 2014-06-06
Hi,

I already tried different Linux distrubution - Fedora 20. There is no difference :( The really odd thing is that friend of mine has Intel N 2230 + Fedora 20 and working on 300Mbps. My guess is that only N1000 is broken.

Cheers!

---

### Post by varunendra on 2014-06-06
If the practical transfer speeds are consistent with 150 Mbps, I wouldn't call it "broken", just not optimal. The 'N' mode depends on many factors - both internal and external, and can reach its peak when everything is in optimal condition - driver, firmware (both in the router/ap and the card), signal quality, distance etc. Anything goes down, the result is a faulty connection.

Most of us wireless troubleshooters here consider even 150 Mbps really good if the connection is stable and strong! :)

You can also say that I (or 'we') say so because we are clueless on how to make it optimal, which by the way is true for the most part at least in my context.. :-\"

---

### Post by pressko on 2014-06-06
> **varunendra said:**
> If the practical transfer speeds are consistent with 150 Mbps, I wouldn't call it "broken", just not optimal. The 'N' mode depends on many factors - both internal and external, and can reach its peak when everything is in optimal condition - driver, firmware (both in the router/ap and the card), signal quality, distance etc. Anything goes down, the result is a faulty connection.

Most of us wireless troubleshooters here consider even 150 Mbps really good if the connection is stable and strong! :)

You can also say that I (or 'we') say so because we are clueless on how to make it optimal, which by the way is true for the most part at least in my context.. :-\"

hahaha ;) True story, but still...
I'm gonna try with different card and will post results.

10x for your time ! :)

Have a good day, sir !

---

### Post by pressko on 2014-06-06
"PROBLEM" IS SOLVED :

According to ARK intel website:
```

[B][SIZE=3]Intel® Centrino® Wireless-N 1000, Single Band
[/SIZE][/B]

 **Specifications**

                     [TABLE="class: specs infoTable"]
[TR="class: infoSection odd"]
[TD="colspan: 3"]     -
Essentials[/TD]
[/TR]
[TR]
[TD="class: lc"]     Status[/TD]
[TD="class: rc"]Launched[/TD]
[/TR]
[TR="class: tech odd"]
[TD="class: lc"]     Launch Date[/TD]
[TD="class: rc"]Q1'11[/TD]
[/TR]
[TR]
[TD="class: lc"]     Board Form Factor[/TD]
[TD="class: rc"]PCIe Half Mini Card[/TD]
[/TR]
[TR="class: odd"]
[TD="class: lc"]     Weight (in grams)[/TD]
[TD="class: rc"]3.4[/TD]
[/TR]
[TR]
[TD="class: lc"]     Operating Temperature Range[/TD]
[TD="class: rc"]0°C to 80°C[/TD]
[/TR]
[TR="class: odd"]
[TD="class: lc"]     Supported Operating Systems[/TD]
[TD="class: rc"]Windows XP, Windows Vista, Windows 8, Windows 7, Linux[/TD]
[/TR]
[/TABLE]

[TABLE="class: specs infoTable"]
[TR="class: infoSection odd"]
[TD="colspan: 3"]     -
Networking Specifications[/TD]
[/TR]
[TR]
[TD="class: lc"][B]     TX/RX Streams   
[/B][/TD]
[TD="class: rc"]**1x2**[/TD]
[/TR]
[TR="class: odd"]
[TD="class: lc"]     Bands[/TD]
[TD="class: rc"]2.4GHz[/TD]
[/TR]
[TR]
[TD="class: lc"]     Max Speed[/TD]
[TD="class: rc"]300 Mbps[/TD]
[/TR]
[TR="class: odd"]
[TD="class: lc"]     Wi-Fi CERTIFIED*[/TD]
[TD="class: rc"]802.11bgn[/TD]
[/TR]
[TR]
[TD="class: lc"]     Compliance[/TD]
[TD="class: rc"]PCI, CISP, FIPS, FISMA[/TD]
[/TR]
[TR="class: odd"]
[TD="class: lc"]     Integrated Bluetooth[/TD]
[TD="class: rc"]No[/TD]
[/TR]
[TR]
[TD="class: lc"]     System Interface Type[/TD]
[TD="class: rc"]PCIe[/TD]
[/TR]
[/TABLE]

```

Linux is showing the TX bitrate, which is = 1. And windows (dunno why) is showing the RX rate, which is = 2.
Mikrotik shows bitrate of it's clients, in this case my Linux laptop : 
```

Tx/Rx rates 240.0Mbps/150.0Mbps

```

So Tx for Mikrotik is Rx for my Laptop = 240 Mbps (in other words RX rate = 2). Rx for Mikrotik is Tx for my laptop (in oder words Tx rate =1).

The proove ?

```

iw dev wlan0 link
Connected to d4:ca:6d:e6:18:a3 (on wlan0)
    SSID: CvetyBaby
    freq: 2457
    RX: 222010900 bytes (198422 packets)
    TX: 89380272 bytes (132287 packets)
    signal: -30 dBm
    tx bitrate: 150.0 MBit/s MCS 7 40Mhz short GI

    bss flags:    short-preamble short-slot-time
    dtim period:    0
    beacon int:    100


```


MISTERY SOLVED !

---

### Post by varunendra on 2014-06-07
..and the discovery bookmarked here. :p

---

### Post by S4boteur on 2015-02-22
Hey guys, 

Trying to get some help from you, you might tell me what might cause this phenomenon: 

Dualbooting (ubuntu + windows) Dell Studio XPS 1640, with Intel wifi 5100 + tp-link wdr3600 on 5Ghz

On ubuntu, I only get 150Mbps speed, according to Network Manager. 
On Windows, I can get 300Mbps. 

The answer to this might be the one pressko said. But! 

I checked my speed with this program: [https://play.google.com/store/apps/details?id=com.pzolee.android.localwifispeedtester](https://play.google.com/store/apps/details?id=com.pzolee.android.localwifispeedtester) 

Using it on Ubuntu, I get max. 22Mbit/s. Nothing changes, I restart my computer, and the same program using it with Windows, measure even 57.8Mbit/s. How is this possible? What is wrong with Ubuntu? Why can't I get the same speed with it? 
Please help, I'm getting mad a little. :(

---

