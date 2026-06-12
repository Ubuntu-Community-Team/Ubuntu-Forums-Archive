---
title: "5GHz HOTSPOT CREATION NOT working on Ubuntu MATE 18.04.3. please help me"
date: 2019-08-16
forum: Networking &amp; Wireless
---

### Post by fastestteleport on 2019-08-16
my 5GHz HOTSPOT CREATION NOT working on Ubuntu MATE 18.04.3.

* * * * * please help me in creating 5GHz hotspot on Ubuntu MATE 18.04.3. * * * * *

Also please let me know if you need more logs or details for analysis.


Other details/analysis:[INDENT]1) my network card details:- Intel Corporation Wireless-AC 9560
2) my network card is working perfectly when connected as a wifi CLIENT on both 2.4Ghz & 5GHz
3) I am ABLE to create HOTSPOT using 2.4GHz (with 72Mbps speed) WITHOUT any issues
4) my network card works by default in Ubuntu MATE with bundled intel wifi drivers
5) * * * * * I have attached my HOTSPOT NETWORK SCREENSHOT in attachment below * * * * *

[/INDENT]
[INDENT=2][ATTACH=CONFIG]283815[/ATTACH]

please find the output of "iw list" command below


[https://paste.ubuntu.com/p/V8Y4s939dT/](https://paste.ubuntu.com/p/V8Y4s939dT/)

$ iw list

Wiphy phy0
    max # scan SSIDs: 20
    max scan IEs length: 422 bytes
    max # sched scan SSIDs: 20
    max # match sets: 11
    max # scan plans: 2
    max scan plan interval: 65535
    max scan plan iterations: 254
    Retry short limit: 7
    Retry long limit: 4
    Coverage class: 0 (up to 0m)
    Device supports RSN-IBSS.
    Device supports AP-side u-APSD.
    Device supports T-DLS.
    Supported Ciphers:
        * WEP40 (00-0f-ac:1)
        * WEP104 (00-0f-ac:5)
        * TKIP (00-0f-ac:2)
        * CCMP-128 (00-0f-ac:4)
        * GCMP-128 (00-0f-ac:8)
        * GCMP-256 (00-0f-ac:9)
        * CMAC (00-0f-ac:6)
        * GMAC-128 (00-0f-ac:11)
        * GMAC-256 (00-0f-ac:12)
    Available Antennas: TX 0 RX 0
    Supported interface modes:
         * IBSS
         * managed
         * AP
         * AP/VLAN
         * monitor
         * P2P-client
         * P2P-GO
         * P2P-device
    Band 1:
        Capabilities: 0x19ef
            RX LDPC
            HT20/HT40
            SM Power Save disabled
            RX HT20 SGI
            RX HT40 SGI
            TX STBC
            RX STBC 1-stream
            Max AMSDU length: 7935 bytes
            DSSS/CCK HT40
        Maximum RX AMPDU length 65535 bytes (exponent: 0x003)
        Minimum RX AMPDU time spacing: 4 usec (0x05)
        HT Max RX data rate: 300 Mbps
        HT TX/RX MCS rate indexes supported: 0-15
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
        Frequencies:
            * 2412 MHz [1] (22.0 dBm)
            * 2417 MHz [2] (22.0 dBm)
            * 2422 MHz [3] (22.0 dBm)
            * 2427 MHz [4] (22.0 dBm)
            * 2432 MHz [5] (22.0 dBm)
            * 2437 MHz [6] (22.0 dBm)
            * 2442 MHz [7] (22.0 dBm)
            * 2447 MHz [8] (22.0 dBm)
            * 2452 MHz [9] (22.0 dBm)
            * 2457 MHz [10] (22.0 dBm)
            * 2462 MHz [11] (22.0 dBm)
            * 2467 MHz [12] (22.0 dBm)
            * 2472 MHz [13] (22.0 dBm)
            * 2484 MHz [14] (disabled)
    Band 2:
        Capabilities: 0x19ef
            RX LDPC
            HT20/HT40
            SM Power Save disabled
            RX HT20 SGI
            RX HT40 SGI
            TX STBC
            RX STBC 1-stream
            Max AMSDU length: 7935 bytes
            DSSS/CCK HT40
        Maximum RX AMPDU length 65535 bytes (exponent: 0x003)
        Minimum RX AMPDU time spacing: 4 usec (0x05)
        HT Max RX data rate: 300 Mbps
        HT TX/RX MCS rate indexes supported: 0-15
        VHT Capabilities (0x039071f6):
            Max MPDU length: 11454
            Supported Channel Width: 160 MHz
            RX LDPC
            short GI (80 MHz)
            short GI (160/80+80 MHz)
            TX STBC
            SU Beamformee
            MU Beamformee
        VHT RX MCS set:
            1 streams: MCS 0-9
            2 streams: MCS 0-9
            3 streams: not supported
            4 streams: not supported
            5 streams: not supported
            6 streams: not supported
            7 streams: not supported
            8 streams: not supported
        VHT RX highest supported: 0 Mbps
        VHT TX MCS set:
            1 streams: MCS 0-9
            2 streams: MCS 0-9
            3 streams: not supported
            4 streams: not supported
            5 streams: not supported
            6 streams: not supported
            7 streams: not supported
            8 streams: not supported
        VHT TX highest supported: 0 Mbps
        Bitrates (non-HT):
            * 6.0 Mbps
            * 9.0 Mbps
            * 12.0 Mbps
            * 18.0 Mbps
            * 24.0 Mbps
            * 36.0 Mbps
            * 48.0 Mbps
            * 54.0 Mbps
        Frequencies:
            * 5180 MHz [36] (22.0 dBm) (no IR)
            * 5200 MHz [40] (22.0 dBm) (no IR)
            * 5220 MHz [44] (22.0 dBm) (no IR)
            * 5240 MHz [48] (22.0 dBm) (no IR)
            * 5260 MHz [52] (22.0 dBm) (no IR, radar detection)
            * 5280 MHz [56] (22.0 dBm) (no IR, radar detection)
            * 5300 MHz [60] (22.0 dBm) (no IR, radar detection)
            * 5320 MHz [64] (22.0 dBm) (no IR, radar detection)
            * 5340 MHz [68] (disabled)
            * 5360 MHz [72] (disabled)
            * 5380 MHz [76] (disabled)
            * 5400 MHz [80] (disabled)
            * 5420 MHz [84] (disabled)
            * 5440 MHz [88] (disabled)
            * 5460 MHz [92] (disabled)
            * 5480 MHz [96] (disabled)
            * 5500 MHz [100] (22.0 dBm) (no IR, radar detection)
            * 5520 MHz [104] (22.0 dBm) (no IR, radar detection)
            * 5540 MHz [108] (22.0 dBm) (no IR, radar detection)
            * 5560 MHz [112] (22.0 dBm) (no IR, radar detection)
            * 5580 MHz [116] (22.0 dBm) (no IR, radar detection)
            * 5600 MHz [120] (22.0 dBm) (no IR, radar detection)
            * 5620 MHz [124] (22.0 dBm) (no IR, radar detection)
            * 5640 MHz [128] (22.0 dBm) (no IR, radar detection)
            * 5660 MHz [132] (22.0 dBm) (no IR, radar detection)
            * 5680 MHz [136] (22.0 dBm) (no IR, radar detection)
            * 5700 MHz [140] (22.0 dBm) (no IR, radar detection)
            * 5720 MHz [144] (22.0 dBm) (no IR, radar detection)
            * 5745 MHz [149] (22.0 dBm) (no IR)
            * 5765 MHz [153] (22.0 dBm) (no IR)
            * 5785 MHz [157] (22.0 dBm) (no IR)
            * 5805 MHz [161] (22.0 dBm) (no IR)
            * 5825 MHz [165] (22.0 dBm) (no IR)
            * 5845 MHz [169] (disabled)
            * 5865 MHz [173] (disabled)
            * 5885 MHz [177] (disabled)
            * 5905 MHz [181] (disabled)
    Supported commands:
         * new_interface
         * set_interface
         * new_key
         * start_ap
         * new_station
         * new_mpath
         * set_mesh_config
         * set_bss
         * authenticate
         * associate
         * deauthenticate
         * disassociate
         * join_ibss
         * join_mesh
         * remain_on_channel
         * set_tx_bitrate_mask
         * frame
         * frame_wait_cancel
         * set_wiphy_netns
         * set_channel
         * set_wds_peer
         * tdls_mgmt
         * tdls_oper
         * start_sched_scan
         * probe_client
         * set_noack_map
         * register_beacons
         * start_p2p_device
         * set_mcast_rate
         * connect
         * disconnect
         * channel_switch
         * set_qos_map
         * add_tx_ts
         * set_multicast_to_unicast
    Supported TX frame types:
         * IBSS: 0x00 0x10 0x20 0x30 0x40 0x50 0x60 0x70 0x80 0x90 0xa0 0xb0 0xc0 0xd0 0xe0 0xf0
         * managed: 0x00 0x10 0x20 0x30 0x40 0x50 0x60 0x70 0x80 0x90 0xa0 0xb0 0xc0 0xd0 0xe0 0xf0
         * AP: 0x00 0x10 0x20 0x30 0x40 0x50 0x60 0x70 0x80 0x90 0xa0 0xb0 0xc0 0xd0 0xe0 0xf0
         * AP/VLAN: 0x00 0x10 0x20 0x30 0x40 0x50 0x60 0x70 0x80 0x90 0xa0 0xb0 0xc0 0xd0 0xe0 0xf0
         * mesh point: 0x00 0x10 0x20 0x30 0x40 0x50 0x60 0x70 0x80 0x90 0xa0 0xb0 0xc0 0xd0 0xe0 0xf0
         * P2P-client: 0x00 0x10 0x20 0x30 0x40 0x50 0x60 0x70 0x80 0x90 0xa0 0xb0 0xc0 0xd0 0xe0 0xf0
         * P2P-GO: 0x00 0x10 0x20 0x30 0x40 0x50 0x60 0x70 0x80 0x90 0xa0 0xb0 0xc0 0xd0 0xe0 0xf0
         * P2P-device: 0x00 0x10 0x20 0x30 0x40 0x50 0x60 0x70 0x80 0x90 0xa0 0xb0 0xc0 0xd0 0xe0 0xf0
    Supported RX frame types:
         * IBSS: 0x40 0xb0 0xc0 0xd0
         * managed: 0x40 0xd0
         * AP: 0x00 0x20 0x40 0xa0 0xb0 0xc0 0xd0
         * AP/VLAN: 0x00 0x20 0x40 0xa0 0xb0 0xc0 0xd0
         * mesh point: 0xb0 0xc0 0xd0
         * P2P-client: 0x40 0xd0
         * P2P-GO: 0x00 0x20 0x40 0xa0 0xb0 0xc0 0xd0
         * P2P-device: 0x40 0xd0
    WoWLAN support:
         * wake up on disconnect
         * wake up on magic packet
         * wake up on pattern match, up to 20 patterns of 16-128 bytes,
           maximum packet offset 0 bytes
         * can do GTK rekeying
         * wake up on GTK rekey failure
         * wake up on EAP identity request
         * wake up on 4-way handshake
         * wake up on rfkill release
         * wake up on network detection, up to 11 match sets
         * wake up on TCP connection
    software interface modes (can always be added):
         * AP/VLAN
         * monitor
    valid interface combinations:
         * #{ managed } <= 1, #{ AP, P2P-client, P2P-GO } <= 1, #{ P2P-device } <= 1,
           total <= 3, #channels <= 2
    HT Capability overrides:
         * MCS: ff ff ff ff ff ff ff ff ff ff
         * maximum A-MSDU length
         * supported channel width
         * short GI for 40 MHz
         * max A-MPDU length exponent
         * min MPDU start spacing
    Device supports TX status socket option.
    Device supports HT-IBSS.
    Device supports SAE with AUTHENTICATE command
    Device supports low priority scan.
    Device supports scan flush.
    Device supports per-vif TX power setting
    P2P GO supports CT window setting
    P2P GO supports opportunistic powersave setting
    Driver supports full state transitions for AP/GO clients
    Driver supports a userspace MPM
    Driver/device bandwidth changes during BSS lifetime (AP/GO mode)
    Device adds DS IE to probe requests
    Device can update TPC Report IE
    Device supports static SMPS
    Device supports dynamic SMPS
    Device supports WMM-AC admission (TSPECs)
    Device supports configuring vdev MAC-addr on create.
    Device supports TDLS channel switching

[/INDENT]

---

### Post by guiverc on 2019-08-16
FYI: OP also posted it on [https://askubuntu.com/questions/1166098/5ghz-hotspot-creation-using-ubuntu-mate-18-04-3](https://askubuntu.com/questions/1166098/5ghz-hotspot-creation-using-ubuntu-mate-18-04-3)

---

