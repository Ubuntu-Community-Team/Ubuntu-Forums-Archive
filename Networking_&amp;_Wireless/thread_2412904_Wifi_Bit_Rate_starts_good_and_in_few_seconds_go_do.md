---
title: "Wifi Bit Rate starts good and in few seconds go down"
date: 2019-02-18
forum: Networking &amp; Wireless
---

### Post by rodrigoguariento on 2019-02-18
Dears,

What is going on with my Wifi bit rate? Usually it works fine in 72Mb/s, but there is some days that bit rate is working in 5.5Mb/s, my Internet speed go slower.

Today is a bad day, the bit rate stays in 5.5Mb/s. But I did a test: I turned on the Airplane Mode, then my wifi turned off. I went to console and repeated the following code, and at same time I turned the Airplane Mode off (my wifi was turned on again). This is the result:

```
rodrigo@rf511:~$ sudo iwconfig wlp2s0

wlp2s0    IEEE 802.11  ESSID:"Marte"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 70:03:7E:A0:47:E5   
          Bit Rate=65 Mb/s   Tx-Power=200 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:on
          Link Quality=70/70  Signal level=58 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


rodrigo@rf511:~$ sudo iwconfig wlp2s0
wlp2s0    IEEE 802.11  ESSID:"Marte"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 70:03:7E:A0:47:E5   
          Bit Rate=19.5 Mb/s   Tx-Power=200 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:on
          Link Quality=70/70  Signal level=-29 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


rodrigo@rf511:~$ sudo iwconfig wlp2s0
wlp2s0    IEEE 802.11  ESSID:"Marte"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 70:03:7E:A0:47:E5   
          Bit Rate=5.5 Mb/s   Tx-Power=200 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:on
          Link Quality=70/70  Signal level=22 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```



More info about my environ:

```
$ sudo iw listWiphy phy0
    max # scan SSIDs: 1
    max scan IEs length: 0 bytes
    max # sched scan SSIDs: 0
    max # match sets: 0
    max # scan plans: 1
    max scan plan interval: -1
    max scan plan iterations: 0
    Retry short limit: 7
    Retry long limit: 4
    Coverage class: 0 (up to 0m)
    Supported Ciphers:
        * WEP40 (00-0f-ac:1)
        * WEP104 (00-0f-ac:5)
        * TKIP (00-0f-ac:2)
        * CCMP-128 (00-0f-ac:4)
        * CMAC (00-0f-ac:6)
    Available Antennas: TX 0 RX 0
    Supported interface modes:
         * IBSS
         * managed
    Band 1:
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
            * 2484 MHz [14] (20.0 dBm) (no IR)
    Band 2:
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
            * 5280 MHz [56] (20.0 dBm) (no IR, radar detection)
            * 5300 MHz [60] (20.0 dBm) (no IR, radar detection)
            * 5320 MHz [64] (20.0 dBm) (no IR, radar detection)
            * 5500 MHz [100] (20.0 dBm) (no IR, radar detection)
            * 5520 MHz [104] (20.0 dBm) (no IR, radar detection)
            * 5540 MHz [108] (20.0 dBm) (no IR, radar detection)
            * 5560 MHz [112] (20.0 dBm) (no IR, radar detection)
            * 5580 MHz [116] (20.0 dBm) (no IR, radar detection)
            * 5600 MHz [120] (20.0 dBm) (no IR, radar detection)
            * 5620 MHz [124] (20.0 dBm) (no IR, radar detection)
            * 5640 MHz [128] (20.0 dBm) (no IR, radar detection)
            * 5660 MHz [132] (20.0 dBm) (no IR, radar detection)
            * 5680 MHz [136] (20.0 dBm) (no IR, radar detection)
            * 5700 MHz [140] (20.0 dBm) (no IR, radar detection)
            * 5745 MHz [149] (20.0 dBm) (no IR)
            * 5765 MHz [153] (20.0 dBm) (no IR)
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
         * set_interface
         * new_key
         * join_ibss
         * set_pmksa
         * del_pmksa
         * flush_pmksa
         * connect
         * disconnect
    software interface modes (can always be added):
    interface combinations are not supported
    Device supports scan flush.

$ sudo lshw -class network
  *-network                 
       description: Wireless interface
       product: BCM4313 802.11bgn Wireless Network Adapter
       vendor: Broadcom Inc. and subsidiaries
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlp2s0
       version: 01
       serial: 30:14:4a:86:a4:cf
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=6.30.223.271 (r587334) ip=192.168.0.14 latency=0 multicast=yes wireless=IEEE 802.11
       resources: irq:16 memory:f6c00000-f6c03fff
  *-network
       description: Ethernet interface
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: enp3s0
       version: 06
       serial: 50:b7:c3:02:58:0c
       size: 10Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=rtl8168e-3_0.0.4 03/27/12 latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:19 ioport:b000(size=256) memory:e2c04000-e2c04fff memory:e2c00000-e2c03fff



```


Thanks for some help since now!

---

