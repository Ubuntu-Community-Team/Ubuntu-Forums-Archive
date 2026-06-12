---
title: "Intel 3168NGW not using full 5GHz channel width"
date: 2021-08-14
forum: Networking &amp; Wireless
---

### Post by inewtons on 2021-08-14
I've been having network performance issues in Ubuntu since installation.
 
Wireless Network Card
```

~$ lspci | grep "Network"
29:00.0 Network controller: Intel Corporation Dual Band Wireless-AC 3168NGW [Stone Peak] (rev 10)

```

Looking at the output, I noticed that the network adapter is only connecting to the channel with width 20 MHz. 
```

~$ iw dev wlp41s0 info 
Interface wlp41s0
    ifindex 3
    wdev 0x1
    addr 98:8d:46:5a:16:34
    ssid home-wifi
    type managed
    wiphy 0
    channel 44 (5220 MHz), width: 20 MHz (no HT), center1: 5220 MHz
    txpower 22.00 dBm
    multicast TXQ:
        qsz-byt    qsz-pkt    flows    drops    marks    overlmt    hashcol    tx-bytes    tx-packets
        0    0    0    0    0    0    0    0        0

```

I confirmed that the network AP seems to be setup correctly. Other Ubuntu devices are connecting properly using full available width (although with different wireless adapters).
```

~$ sudo iw dev wlp41s0 scan ssid
BSS cc:ab:2c:db:be:c9(on wlp41s0) -- associated
    last seen: 2739.005s [boottime]
    TSF: 3259641347 usec (0d, 00:54:19)
    freq: 5220
    beacon interval: 100 TUs
    capability: ESS Privacy SpectrumMgmt (0x0111)
    signal: -44.00 dBm
    last seen: 1136 ms ago
    Information elements from Probe Response frame:
    SSID: home-wifi
    Supported rates: 6.0* 9.0 12.0 18.0 24.0* 36.0 48.0 54.0 
    Country: US    Environment: Indoor/Outdoor
        Channels [36 - 36] @ 30 dBm
        Channels [40 - 40] @ 30 dBm
        Channels [44 - 44] @ 30 dBm
        Channels [48 - 48] @ 30 dBm
        Channels [52 - 52] @ 24 dBm
        Channels [56 - 56] @ 24 dBm
        Channels [60 - 60] @ 24 dBm
        Channels [64 - 64] @ 24 dBm
        Channels [100 - 100] @ 24 dBm
        Channels [104 - 104] @ 24 dBm
        Channels [108 - 108] @ 24 dBm
        Channels [112 - 112] @ 24 dBm
        Channels [116 - 116] @ 24 dBm
        Channels [120 - 120] @ 24 dBm
        Channels [124 - 124] @ 24 dBm
        Channels [128 - 128] @ 24 dBm
        Channels [132 - 132] @ 24 dBm
        Channels [136 - 136] @ 24 dBm
        Channels [140 - 140] @ 24 dBm
        Channels [144 - 144] @ 24 dBm
        Channels [149 - 149] @ 30 dBm
        Channels [153 - 153] @ 30 dBm
        Channels [157 - 157] @ 30 dBm
        Channels [161 - 161] @ 30 dBm
        Channels [165 - 165] @ 30 dBm
    Power constraint: 0 dB
    TPC report: TX power: 22 dBm
    RSN:     * Version: 1
         * Group cipher: CCMP
         * Pairwise ciphers: CCMP
         * Authentication suites: PSK
         * Capabilities: 16-PTKSA-RC 1-GTKSA-RC (0x000c)
    BSS Load:
         * station count: 3
         * channel utilisation: 16/255
         * available admission capacity: 0 [*32us]
    HT capabilities:
        Capabilities: 0x1ef
            RX LDPC
            HT20/HT40
            SM Power Save disabled
            RX HT20 SGI
            RX HT40 SGI
            TX STBC
            RX STBC 1-stream
            Max AMSDU length: 3839 bytes
            No DSSS/CCK HT40
        Maximum RX AMPDU length 65535 bytes (exponent: 0x003)
        Minimum RX AMPDU time spacing: 4 usec (0x05)
        HT RX MCS rate indexes supported: 0-31
        HT TX MCS rate indexes are undefined
    HT operation:
         * primary channel: 44
         * secondary channel offset: above
         * STA channel width: any
         * RIFS: 0
         * HT protection: non-HT mixed
         * non-GF present: 1
         * OBSS non-GF present: 1
         * dual beacon: 0
         * dual CTS protection: 0
         * STBC beacon: 0
         * L-SIG TXOP Prot: 0
         * PCO active: 0
         * PCO phase: 0
    Extended capabilities:
         * Extended Channel Switching
         * BSS Transition
         * Interworking
         * QoS Map
         * Operating Mode Notification
         * Channel Schedule Management
         * Channel Schedule Management
         * 6
         * Max Number Of MSDUs In A-MSDU is 
    VHT capabilities:
        VHT Capabilities (0x0f8b69f5):
            Max MPDU length: 7991
            Supported Channel Width: 160 MHz
            RX LDPC
            short GI (80 MHz)
            short GI (160/80+80 MHz)
            TX STBC
            SU Beamformer
            MU Beamformer
        VHT RX MCS set:
            1 streams: MCS 0-9
            2 streams: MCS 0-9
            3 streams: MCS 0-9
            4 streams: MCS 0-9
            5 streams: not supported
            6 streams: not supported
            7 streams: not supported
            8 streams: not supported
        VHT RX highest supported: 0 Mbps
        VHT TX MCS set:
            1 streams: MCS 0-9
            2 streams: MCS 0-9
            3 streams: MCS 0-9
            4 streams: MCS 0-9
            5 streams: not supported
            6 streams: not supported
            7 streams: not supported
            8 streams: not supported
        VHT TX highest supported: 0 Mbps
    VHT operation:
         * channel width: 1 (80 MHz)
         * center freq segment 1: 42
         * center freq segment 2: 50
         * VHT basic MCS set: 0x0000
    WPS:     * Version: 1.0
         * Wi-Fi Protected Setup State: 2 (Configured)
         * Response Type: 3 (AP)
         * UUID: 
         * Manufacturer: Arris, Inc.
         * Model: BGW320-500
         * Model Number: BGW320-500
         * Serial Number: BGW320-500
         * Primary Device Type: 6-0050f204-1
         * Device name: Arris Wireless
         * Config methods: Display, Keypad
         * RF Bands: 0x3
         * Unknown TLV (0x1049, 6 bytes): 00 37 2a 00 01 20
    WMM:     * Parameter version 1
         * u-APSD
         * BE: CW 15-1023, AIFSN 3
         * BK: CW 15-1023, AIFSN 7
         * VI: CW 7-15, AIFSN 2, TXOP 3008 usec
         * VO: CW 3-7, AIFSN 2, TXOP 1504 usec
    802.11u Advertisement:
        Query Response Info: 0x7f
            Query Response Length Limit: 127
            ANQP

```

Interestingly enough, even though I am in the US, iwlist reports frequencies that shouldn't be available by regulation.
```

~$ iwlist wlp41s0 freq
wlp41s0   32 channels in total; available frequencies :
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
          Current Frequency:5.22 GHz (Channel 44)

```

In /etc/default/crda, I set regdomain to US to try and make sure that the adapter is set to operate in the correct region, but didn't seem to change the above. I could not confirm from dmesg that the crda change was effective.
```

REGDOMAIN=US

```

I also tried to set the frequency manually, but get a reply that the channel is disabled, making me believe that the region is incorrect still.
```

~$ sudo iw wlp41s0 set freq 5220 80 5210
kernel reports: (extension) channel is disabled
command failed: Invalid argument (-22)

```

I have also updated the Intel firmware in /lib/firmware using the latest downloaded from Intel.

Any thoughts or recommendations on where to go next would be appreciated.

---

### Post by inewtons on 2021-08-14
Quick note, output of iw get reg.
```

~$ iw reg get
global
country US: DFS-FCC
    (2400 - 2472 @ 40), (N/A, 30), (N/A)
    (5150 - 5250 @ 80), (N/A, 23), (N/A), AUTO-BW
    (5250 - 5350 @ 80), (N/A, 23), (0 ms), DFS, AUTO-BW
    (5470 - 5730 @ 160), (N/A, 23), (0 ms), DFS
    (5730 - 5850 @ 80), (N/A, 30), (N/A), AUTO-BW
    (5850 - 5895 @ 40), (N/A, 27), (N/A), NO-OUTDOOR, AUTO-BW, PASSIVE-SCAN
    (57240 - 71000 @ 2160), (N/A, 40), (N/A)

phy#0 (self-managed)
country US: DFS-UNSET
    (2402 - 2437 @ 40), (6, 22), (N/A), AUTO-BW, NO-HT40MINUS, NO-80MHZ, NO-160MHZ
    (2422 - 2462 @ 40), (6, 22), (N/A), AUTO-BW, NO-80MHZ, NO-160MHZ
    (2447 - 2482 @ 40), (6, 22), (N/A), AUTO-BW, NO-HT40PLUS, NO-80MHZ, NO-160MHZ
    (5170 - 5190 @ 80), (6, 22), (N/A), AUTO-BW, NO-HT40MINUS, NO-160MHZ
    (5190 - 5210 @ 80), (6, 22), (N/A), AUTO-BW, NO-HT40PLUS, NO-160MHZ
    (5210 - 5230 @ 80), (6, 22), (N/A), AUTO-BW, NO-HT40MINUS, NO-160MHZ
    (5230 - 5250 @ 80), (6, 22), (N/A), AUTO-BW, NO-HT40PLUS, NO-160MHZ
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

```

---

### Post by him610 on 2021-08-16
Hello inewtons,

I assume your issue is still unresolved; however, if you have discovered a resolution, please mark the thread as "solved".
You are encouraged to "bump" if you have not received a reply within 24 hours. 

I have the very same intel 3168NGW [Stone Peak] wireless device. No issues since installation 17 months ago.

Please go to this site and complete the suggestions even though you have already run some of the commands. 
[https://ubuntuforums.org/showthread.php?t=370108]("https://ubuntuforums.org/showthread.php?t=370108")

One of the network SMEs will be along to advise on your issue.

---

### Post by chili555 on 2021-08-17
If this or any other networking SME had a single clue, we would have answered or at least guessed by now.

The only thing I've found that is remotely promising is this: [https://unix.stackexchange.com/questions/381298/how-to-calculate-parameters-to-iw-set-freq](https://unix.stackexchange.com/questions/381298/how-to-calculate-parameters-to-iw-set-freq)

I suggest that you try the parameters:

```
sudo -i
echo "options iwlwifi 11n_disable=8 amsdu_size=3"  >>  /etc/modprobe.d/iwlwifi.conf
modprobe -r iwlwifi
modprobe iwlwifi
exit

```
I also suggest that the channel 44 be fixed in your router and certainly not auto channel select (code for, "Just when things are going well, I'll change my address. Catch me if you can!").

Is there any improvement?```
 iw dev wlp41s0 info 

```

---

