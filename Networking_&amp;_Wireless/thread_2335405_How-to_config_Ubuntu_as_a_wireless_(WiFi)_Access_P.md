---
title: "How-to config Ubuntu as a wireless (WiFi) Access Point via Asus USB-AC56 AC1300"
date: 2016-08-28
forum: Networking &amp; Wireless
---

### Post by maxbar on 2016-08-28
I have followed numerous guides on how to get that done, but without success. The USB-AC56 Wireless-AC1300 is capable of dual-band AP, so it's not a limitation of the device (see output of "iw list" below).

This is the driver (there's also the "gnab" version, which didn't work for me) that keeps the adapter reliably on as such (I can connect to other APs, I just couldn't get it to work as an AP itself):

[github.com/abperiasamy/rtl8812AU_8821AU_linux]("github.com/abperiasamy/rtl8812AU_8821AU_linux")

I just downloaded, unzipped and then I followed the README.md instructions near the end (AKA "make clean, make, make install" - the DKMS version didn't work for me).

**Please no speculations and guesses, only post if you have or had this adapter and you know for sure how to run it as an AP, then respond with up-to-date (for Ubuntu 16.04.1) step-by-step instructions on how to accomplish this! Thanks!**


```
iw list
```

> Wiphy phy0
        max # scan SSIDs: 9
        max scan IEs length: 2304 bytes
        Retry short limit: 7
        Retry long limit: 4
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
                 * AP
                 * monitor
                 * P2P-client
                 * P2P-GO
        Band 1:
                Capabilities: 0x1862
                        HT20/HT40
                        Static SM Power Save
                        RX HT20 SGI
                        RX HT40 SGI
                        No RX STBC
                        Max AMSDU length: 7935 bytes
                        DSSS/CCK HT40
                Maximum RX AMPDU length 65535 bytes (exponent: 0x003)
                Minimum RX AMPDU time spacing: 16 usec (0x07)
                HT TX/RX MCS rate indexes supported: 0-15, 32
                Bitrates (non-HT):
                        * 1.0 Mbps
                        * 2.0 Mbps
                        * 5.5 Mbps
                        * 11.0 Mbps
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
                        * 2484 MHz [14] (20.0 dBm) (no IR)
        Band 2:
                Capabilities: 0x1862
                        HT20/HT40
                        Static SM Power Save
                        RX HT20 SGI
                        RX HT40 SGI
                        No RX STBC
                        Max AMSDU length: 7935 bytes
                        DSSS/CCK HT40
                Maximum RX AMPDU length 65535 bytes (exponent: 0x003)
                Minimum RX AMPDU time spacing: 16 usec (0x07)
                HT TX/RX MCS rate indexes supported: 0-15, 32
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
                        * 5170 MHz [34] (disabled)
                        * 5180 MHz [36] (20.0 dBm) (no IR)
                        * 5190 MHz [38] (20.0 dBm) (no IR)
                        * 5200 MHz [40] (20.0 dBm) (no IR)
                        * 5210 MHz [42] (20.0 dBm) (no IR)
                        * 5220 MHz [44] (20.0 dBm) (no IR)
                        * 5230 MHz [46] (20.0 dBm) (no IR)
                        * 5240 MHz [48] (20.0 dBm) (no IR)
                        * 5260 MHz [52] (20.0 dBm) (no IR, radar detection)
                          DFS state: usable (for 72399 sec)
                          DFS CAC time: 60000 ms
                        * 5280 MHz [56] (20.0 dBm) (no IR, radar detection)
                          DFS state: usable (for 72399 sec)
                          DFS CAC time: 60000 ms
                        * 5300 MHz [60] (20.0 dBm) (no IR, radar detection)
                          DFS state: usable (for 72399 sec)
                          DFS CAC time: 60000 ms
                        * 5320 MHz [64] (20.0 dBm) (no IR, radar detection)
                          DFS state: usable (for 72399 sec)
                          DFS CAC time: 60000 ms
                        * 5500 MHz [100] (20.0 dBm) (no IR, radar detection)
                          DFS state: usable (for 72399 sec)
                          DFS CAC time: 60000 ms
                        * 5520 MHz [104] (20.0 dBm) (no IR, radar detection)
                          DFS state: usable (for 72399 sec)
                          DFS CAC time: 60000 ms
                        * 5540 MHz [108] (20.0 dBm) (no IR, radar detection)
                          DFS state: usable (for 72399 sec)
                          DFS CAC time: 60000 ms
                        * 5560 MHz [112] (20.0 dBm) (no IR, radar detection)
                          DFS state: usable (for 72399 sec)
                          DFS CAC time: 60000 ms
                        * 5580 MHz [116] (20.0 dBm) (no IR, radar detection)
                          DFS state: usable (for 72399 sec)
                          DFS CAC time: 60000 ms
                        * 5600 MHz [120] (20.0 dBm) (no IR, radar detection)
                          DFS state: usable (for 72399 sec)
                          DFS CAC time: 60000 ms
                        * 5620 MHz [124] (20.0 dBm) (no IR, radar detection)
                          DFS state: usable (for 72399 sec)
                          DFS CAC time: 60000 ms
                        * 5640 MHz [128] (20.0 dBm) (no IR, radar detection)
                          DFS state: usable (for 72399 sec)
                          DFS CAC time: 60000 ms
                        * 5660 MHz [132] (20.0 dBm) (no IR, radar detection)
                          DFS state: usable (for 72399 sec)
                          DFS CAC time: 60000 ms
                        * 5680 MHz [136] (20.0 dBm) (no IR, radar detection)
                          DFS state: usable (for 72399 sec)
                          DFS CAC time: 60000 ms
                        * 5700 MHz [140] (20.0 dBm) (no IR, radar detection)
                          DFS state: usable (for 72399 sec)
                          DFS CAC time: 60000 ms
                        * 5745 MHz [149] (20.0 dBm) (no IR)
                        * 5765 MHz [153] (20.0 dBm)
                        * 5785 MHz [157] (20.0 dBm) (no IR)
                        * 5805 MHz [161] (20.0 dBm) (no IR)
                        * 5825 MHz [165] (20.0 dBm) (no IR)
                        * 5920 MHz [184] (disabled)
                        * 5940 MHz [188] (disabled)
                        * 5960 MHz [192] (disabled)
                        * 5980 MHz [196] (disabled)
                        * 6000 MHz [200] (disabled)
                        * 6020 MHz [204] (disabled)
                        * 6040 MHz [208] (disabled)
                        * 6060 MHz [212] (disabled)
                        * 6080 MHz [216] (disabled)
        Supported commands:
                 * new_interface
                 * set_interface
                 * new_key
                 * start_ap
                 * new_station
                 * set_bss
                 * join_ibss
                 * set_pmksa
                 * del_pmksa
                 * flush_pmksa
                 * remain_on_channel
                 * frame
                 * set_channel
                 * connect
                 * disconnect
        Supported TX frame types:
                 * IBSS: 0x00 0x10 0x20 0x30 0x40 0x50 0x60 0x70 0x80 0x90 0xa0 0xb0 0xc0 0xd0 0xe0 0xf0
                 * managed: 0x00 0x10 0x20 0x30 0x40 0x50 0x60 0x70 0x80 0x90 0xa0 0xb0 0xc0 0xd0 0xe0 0xf0
                 * AP: 0x00 0x10 0x20 0x30 0x40 0x50 0x60 0x70 0x80 0x90 0xa0 0xb0 0xc0 0xd0 0xe0 0xf0
                 * AP/VLAN: 0x00 0x10 0x20 0x30 0x40 0x50 0x60 0x70 0x80 0x90 0xa0 0xb0 0xc0 0xd0 0xe0 0xf0
                 * P2P-client: 0x00 0x10 0x20 0x30 0x40 0x50 0x60 0x70 0x80 0x90 0xa0 0xb0 0xc0 0xd0 0xe0 0xf0
                 * P2P-GO: 0x00 0x10 0x20 0x30 0x40 0x50 0x60 0x70 0x80 0x90 0xa0 0xb0 0xc0 0xd0 0xe0 0xf0
        Supported RX frame types:
                 * IBSS: 0xd0
                 * managed: 0x40 0xd0
                 * AP: 0x00 0x20 0x40 0xa0 0xb0 0xc0 0xd0
                 * AP/VLAN: 0x00 0x20 0x40 0xa0 0xb0 0xc0 0xd0
                 * P2P-client: 0x40 0xd0
                 * P2P-GO: 0x00 0x20 0x40 0xa0 0xb0 0xc0 0xd0
        software interface modes (can always be added):
                 * monitor
        interface combinations are not supported
        Device supports scan flush.


---

