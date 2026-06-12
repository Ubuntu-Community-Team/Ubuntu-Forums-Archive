---
title: "Unstable connection to WPA PEAP GTC network"
date: 2013-10-29
forum: Networking &amp; Wireless
---

### Post by chirpis7 on 2013-10-29
Hi everyone,

My school has a WPA PEAP network with GTC inner authentication. I am able to connect to the network, but once I load a website or two, the network become unresponsive (i.e. in Chromium, it gets stuck at "Sending request"), and I'm eventually disconnected. Any help will be greatly appreciated.

Here's some log output. I can provide more if needed:

```
Ubuntu 13.04


3.8.0-32-generic x86_64
```

lsusb:


```
03:00.0 Network controller: Intel Corporation Centrino Advanced-N 6235 (rev 24)
```

lsmod:

```

iwldvm                241872  0 
mac80211              606457  1 iwldvm
iwlwifi               173516  1 iwldvm
cfg80211              511019  3 iwlwifi,mac80211,iwldvm
```

dmesg:

```

[    3.501227] iwlwifi 0000:03:00.0: irq 46 for MSI/MSI-X
[    3.503541] iwlwifi 0000:03:00.0: loaded firmware version 18.168.6.1
[    3.527153] iwlwifi 0000:03:00.0: CONFIG_IWLWIFI_DEBUG disabled
[    3.527162] iwlwifi 0000:03:00.0: CONFIG_IWLWIFI_DEBUGFS enabled
[    3.527170] iwlwifi 0000:03:00.0: CONFIG_IWLWIFI_DEVICE_TRACING enabled
[    3.527178] iwlwifi 0000:03:00.0: CONFIG_IWLWIFI_DEVICE_TESTMODE enabled
[    3.527186] iwlwifi 0000:03:00.0: CONFIG_IWLWIFI_P2P disabled
[    3.527192] iwlwifi 0000:03:00.0: Detected Intel(R) Centrino(R) Advanced-N 6235 AGN, REV=0xB0
[    3.527240] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[    3.551049] ieee80211 phy0: Selected rate control algorithm 'iwl-agn-rs'
[  375.153065] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[  375.159727] iwlwifi 0000:03:00.0: Radio type=0x2-0x1-0x0
[  375.553201] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[  375.559871] iwlwifi 0000:03:00.0: Radio type=0x2-0x1-0x0
[ 1892.110738] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[ 1892.117357] iwlwifi 0000:03:00.0: Radio type=0x2-0x1-0x0
[ 5227.235372] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[ 5227.242122] iwlwifi 0000:03:00.0: Radio type=0x2-0x1-0x0
[ 5817.817954] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[ 5817.824560] iwlwifi 0000:03:00.0: Radio type=0x2-0x1-0x0
[ 5824.571917] iwlwifi 0000:03:00.0 wlan0: disabling HT/VHT due to WEP/TKIP use
[ 5824.571929] iwlwifi 0000:03:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[ 5824.571935] iwlwifi 0000:03:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[ 6956.290061] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[ 6956.296671] iwlwifi 0000:03:00.0: Radio type=0x2-0x1-0x0
[ 6963.080560] iwlwifi 0000:03:00.0 wlan0: disabling HT/VHT due to WEP/TKIP use
[ 6963.080566] iwlwifi 0000:03:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[ 6963.080570] iwlwifi 0000:03:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[ 7613.469241] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[ 7613.475870] iwlwifi 0000:03:00.0: Radio type=0x2-0x1-0x0
[ 7620.201265] iwlwifi 0000:03:00.0 wlan0: disabling HT/VHT due to WEP/TKIP use
[ 7620.201278] iwlwifi 0000:03:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[ 7620.201285] iwlwifi 0000:03:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[ 8232.762453] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[ 8232.769065] iwlwifi 0000:03:00.0: Radio type=0x2-0x1-0x0
[ 8239.581772] iwlwifi 0000:03:00.0 wlan0: disabling HT/VHT due to WEP/TKIP use
[ 8239.581784] iwlwifi 0000:03:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[ 8239.581792] iwlwifi 0000:03:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[13763.634808] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[13763.641427] iwlwifi 0000:03:00.0: Radio type=0x2-0x1-0x0
[16955.598953] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[16955.605574] iwlwifi 0000:03:00.0: Radio type=0x2-0x1-0x0
```

lshw:

```

  *-network
       description: Wireless interface
       product: Centrino Advanced-N 6235
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 24
       serial: b4:b6:76:a0:4b:3c
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlwifi driverversion=3.8.0-32-generic firmware=18.168.6.1 ip=10.250.169.96 latency=0 link=yes multicast=yes wireless=IEEE 802.11abgn
       resources: irq:46 memory:f7c00000-f7c01fff
```
    
iwlist scan:
   
          ```
Cell 02 - Address: 24:DE:C6:B0:C7:D9
                    Channel:36
                    Frequency:5.18 GHz (Channel 36)
                    Quality=29/70  Signal level=-81 dBm  
                    Encryption key:on
                    ESSID:"CatChat2x"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000004ff3fe419b
                    Extra: Last beacon: 27820ms ago
                    IE: Unknown: 0009436174436861743278
                    IE: Unknown: 01088C129824B048606C
                    IE: Unknown: 030124
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
                    IE: Unknown: 2D1ACC011BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1624001B000000FF000000000000000000000000000000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C33CC011BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C3424001B000000FF000000000000000000000000000000


          Cell 04 - Address: 24:DE:C6:B0:C3:E9
                    Channel:149
                    Frequency:5.745 GHz
                    Quality=28/70  Signal level=-82 dBm  
                    Encryption key:on
                    ESSID:"CatChat2x"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000181f60e19c
                    Extra: Last beacon: 28680ms ago
                    IE: Unknown: 0009436174436861743278
                    IE: Unknown: 01088C129824B048606C
                    IE: Unknown: 030195
                    IE: Unknown: 050400010000
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
                    IE: Unknown: 2D1ACC011BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1695001B000000FF000000000000000000000000000000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C33CC011BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C3495001B000000FF000000000000000000000000000000
                    IE: Unknown: DD07000B8601040817
                    IE: Unknown: DD0E000B860103006170313930333032


          Cell 09 - Address: 24:DE:C6:B0:C0:29
                    Channel:149
                    Frequency:5.745 GHz
                    Quality=39/70  Signal level=-71 dBm  
                    Encryption key:on
                    ESSID:"CatChat2x"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000112fb688ede
                    Extra: Last beacon: 27716ms ago

```
ifconfig (while connected):


```
wlan0     Link encap:Ethernet  HWaddr b4:b6:76:a0:4b:3c  
          inet addr:10.250.16.220  Bcast:10.250.31.255  Mask:255.255.240.0
          inet6 addr: fe80::b6b6:76ff:fea0:4b3c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:230023 errors:0 dropped:0 overruns:0 frame:0
          TX packets:130970 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:255999759 (255.9 MB)  TX bytes:16652605 (16.6 MB)

```
iwconfig (while connected):

```

wlan0     IEEE 802.11abgn  ESSID:"CatChat2x"  
          Mode:Managed  Frequency:5.745 GHz  Access Point: 24:DE:C6:B0:C0:29   
          Bit Rate=6 Mb/s   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=36/70  Signal level=-74 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:3   Missed beacon:0
```

---

### Post by chirpis7 on 2013-10-30
bump

So...yeah, I could really use some help here.

---

