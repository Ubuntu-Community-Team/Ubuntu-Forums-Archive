---
title: "Wake on Wireless LAN (Intel Wireless AC-3160)"
date: 2017-12-02
forum: Networking &amp; Wireless
---

### Post by makem2 on 2017-12-02
Windows tells me:

ARP offload for WoWLAN - Enabled
GTK rekeyring for WoWLAN - Enabled
Sleep on WoWLAN - Disabled
Wake on magic Package - Enabled

It does not say: Wake  on WoWLAN

[https://communities.intel.com/thread/58970](https://communities.intel.com/thread/58970)

[https://dl.tvcdn.de/docs/en/TeamViewer-Manual-Wake-on-LAN-en.pdf](https://dl.tvcdn.de/docs/en/TeamViewer-Manual-Wake-on-LAN-en.pdf)

I cannot find and ubuntu command which gives such information and allows enabling/disabling.

Am I wasting my time attempting to find a way of waking from WLAN?

EDIT: It would seem not:

[https://askubuntu.com/questions/168982/how-do-i-get-wireless-wake-on-lan-work-with-an-intel-5100-agn](https://askubuntu.com/questions/168982/how-do-i-get-wireless-wake-on-lan-work-with-an-intel-5100-agn)

```

makem@ssdTOSH:~$ iw phy0 info
Wiphy phy0
    max # scan SSIDs: 20
    max scan IEs length: 425 bytes
    Retry short limit: 7
    Retry long limit: 4
    Coverage class: 0 (up to 0m)
    Device supports RSN-IBSS.
    Device supports AP-side u-APSD.
    Supported Ciphers:
        * WEP40 (00-0f-ac:1)
        * WEP104 (00-0f-ac:5)
        * TKIP (00-0f-ac:2)
        * CCMP (00-0f-ac:4)
        * CMAC (00-0f-ac:6)
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
        Capabilities: 0x116e
            HT20/HT40
            SM Power Save disabled
            RX HT20 SGI
            RX HT40 SGI
            RX STBC 1-stream
            Max AMSDU length: 3839 bytes
            DSSS/CCK HT40
        Maximum RX AMPDU length 65535 bytes (exponent: 0x003)
        Minimum RX AMPDU time spacing: 4 usec (0x05)
        HT TX/RX MCS rate indexes supported: 0-7
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
            * 2412 MHz [1] (20.0 dBm)
            * 2417 MHz [2] (20.0 dBm)
            * 2422 MHz [3] (20.0 dBm)
            * 2427 MHz [4] (20.0 dBm)
            * 2432 MHz [5] (20.0 dBm)
            * 2437 MHz [6] (20.0 dBm)
            * 2442 MHz [7] (20.0 dBm)
            * 2447 MHz [8] (20.0 dBm)
            * 2452 MHz [9] (20.0 dBm)
            * 2457 MHz [10] (20.0 dBm)
            * 2462 MHz [11] (20.0 dBm)
            * 2467 MHz [12] (20.0 dBm) (no IR)
            * 2472 MHz [13] (20.0 dBm) (no IR)
    Band 2:
        Capabilities: 0x116e
            HT20/HT40
            SM Power Save disabled
            RX HT20 SGI
            RX HT40 SGI
            RX STBC 1-stream
            Max AMSDU length: 3839 bytes
            DSSS/CCK HT40
        Maximum RX AMPDU length 65535 bytes (exponent: 0x003)
        Minimum RX AMPDU time spacing: 4 usec (0x05)
        HT TX/RX MCS rate indexes supported: 0-7
        VHT Capabilities (0x33807120):
            Max MPDU length: 3895
            Supported Channel Width: neither 160 nor 80+80
            short GI (80 MHz)
            SU Beamformee
            RX antenna pattern consistency
            TX antenna pattern consistency
        VHT RX MCS set:
            1 streams: MCS 0-9
            2 streams: not supported
            3 streams: not supported
            4 streams: not supported
            5 streams: not supported
            6 streams: not supported
            7 streams: not supported
            8 streams: not supported
        VHT RX highest supported: 0 Mbps
        VHT TX MCS set:
            1 streams: MCS 0-9
            2 streams: not supported
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
            * 5180 MHz [36] (20.0 dBm) (no IR)
            * 5200 MHz [40] (20.0 dBm) (no IR)
            * 5220 MHz [44] (20.0 dBm) (no IR)
            * 5240 MHz [48] (20.0 dBm) (no IR)
            * 5260 MHz [52] (20.0 dBm) (no IR, radar detection)
              DFS state: usable (for 1050 sec)
              DFS CAC time: 60000 ms
            * 5280 MHz [56] (20.0 dBm) (no IR, radar detection)
              DFS state: usable (for 1050 sec)
              DFS CAC time: 60000 ms
            * 5300 MHz [60] (20.0 dBm) (no IR, radar detection)
              DFS state: usable (for 1050 sec)
              DFS CAC time: 60000 ms
            * 5320 MHz [64] (20.0 dBm) (no IR, radar detection)
              DFS state: usable (for 1050 sec)
              DFS CAC time: 60000 ms
            * 5500 MHz [100] (22.0 dBm) (no IR, radar detection)
              DFS state: usable (for 1050 sec)
              DFS CAC time: 60000 ms
            * 5520 MHz [104] (22.0 dBm) (no IR, radar detection)
              DFS state: usable (for 1050 sec)
              DFS CAC time: 60000 ms
            * 5540 MHz [108] (22.0 dBm) (no IR, radar detection)
              DFS state: usable (for 1050 sec)
              DFS CAC time: 60000 ms
            * 5560 MHz [112] (22.0 dBm) (no IR, radar detection)
              DFS state: usable (for 1050 sec)
              DFS CAC time: 60000 ms
            * 5580 MHz [116] (22.0 dBm) (no IR, radar detection)
              DFS state: usable (for 1050 sec)
              DFS CAC time: 60000 ms
            * 5600 MHz [120] (22.0 dBm) (no IR, radar detection)
              DFS state: usable (for 1050 sec)
              DFS CAC time: 60000 ms
            * 5620 MHz [124] (22.0 dBm) (no IR, radar detection)
              DFS state: usable (for 1050 sec)
              DFS CAC time: 60000 ms
            * 5640 MHz [128] (22.0 dBm) (no IR, radar detection)
              DFS state: usable (for 1050 sec)
              DFS CAC time: 60000 ms
            * 5660 MHz [132] (22.0 dBm) (no IR, radar detection)
              DFS state: usable (for 1050 sec)
              DFS CAC time: 60000 ms
            * 5680 MHz [136] (22.0 dBm) (no IR, radar detection)
              DFS state: usable (for 1050 sec)
              DFS CAC time: 60000 ms
            * 5700 MHz [140] (22.0 dBm) (no IR, radar detection)
              DFS state: usable (for 1050 sec)
              DFS CAC time: 60000 ms
            * 5720 MHz [144] (disabled)
            * 5745 MHz [149] (disabled)
            * 5765 MHz [153] (disabled)
            * 5785 MHz [157] (disabled)
            * 5805 MHz [161] (disabled)
            * 5825 MHz [165] (disabled)
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
         * start_sched_scan
         * probe_client
         * set_noack_map
         * register_beacons
         * start_p2p_device
         * set_mcast_rate
         * connect
         * disconnect
         * channel_switch
         * Unknown command (104)
         * Unknown command (105)
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
    Device supports static SMPS
    Device supports dynamic SMPS
makem@ssdTOSH:~$

```

Relevant section:

```

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
         * wake up on TCP connection

```

```

makem@ssdTOSH:~$ iw phy0 wowlan show
WoWLAN is disabled.
makem@ssdTOSH:~$ sudo iw phy0 wowlan enable magic-packet
makem@ssdTOSH:~$ iw phy0 wowlan show
WoWLAN is enabled:
 * wake up on magic packet
makem@ssdTOSH:~$

```

---

