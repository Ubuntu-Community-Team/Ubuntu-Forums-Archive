---
title: "problem connecting to 5ghz network"
date: 2020-10-19
forum: Networking &amp; Wireless
---

### Post by glx28 on 2020-10-19
I want to connect my pc to a 5ghz network but for some reason it can't connect to it on ubuntu, only on windows. The rest of my devices can connect to it.
I have a PCE-AC68 wifi card that uses BCM4360
Does not work with different linux distros like arch or kali 

When I try to run iwlist wlp4s0 scan | grep \Frequency it does not show the channel that the network is on (116)

```
Frequency:2.462 GHz (Channel 11)
                    Frequency:2.462 GHz (Channel 11)
                    Frequency:2.462 GHz (Channel 11)
                    Frequency:2.412 GHz (Channel 1)
                    Frequency:2.437 GHz (Channel 6)
                    Frequency:2.437 GHz (Channel 6)
                    Frequency:5.18 GHz (Channel 36)
                    Frequency:5.18 GHz (Channel 36)
                    Frequency:5.18 GHz (Channel 36)
                    Frequency:5.18 GHz (Channel 36)
                    Frequency:5.22 GHz (Channel 44)
                    Frequency:2.462 GHz (Channel 11)
                    Frequency:5.18 GHz (Channel 36)

```


I also used tools like linSSID with the same result

```
Frequencies:                        * 2412 MHz [1] (20.0 dBm)
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
                        * 2467 MHz [12] (20.0 dBm)
                        * 2472 MHz [13] (20.0 dBm)
                        * 2484 MHz [14] (disabled)
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
                        * 5160 MHz [32] (23.0 dBm)
                        * 5170 MHz [34] (23.0 dBm)
                        * 5180 MHz [36] (23.0 dBm)
                        * 5190 MHz [38] (23.0 dBm)
                        * 5200 MHz [40] (23.0 dBm)
                        * 5210 MHz [42] (23.0 dBm)
                        * 5220 MHz [44] (23.0 dBm)
                        * 5230 MHz [46] (23.0 dBm)
                        * 5240 MHz [48] (23.0 dBm)
                        * 5250 MHz [50] (disabled)
                        * 5260 MHz [52] (20.0 dBm) (radar detection)
                        * 5270 MHz [54] (20.0 dBm) (radar detection)
                        * 5280 MHz [56] (20.0 dBm) (radar detection)
                        * 5290 MHz [58] (20.0 dBm) (radar detection)
                        * 5300 MHz [60] (20.0 dBm) (radar detection)
                        * 5310 MHz [62] (20.0 dBm) (radar detection)
                        * 5320 MHz [64] (20.0 dBm) (radar detection)
                        * 5330 MHz [66] (20.0 dBm) (radar detection)
                        * 5340 MHz [68] (20.0 dBm) (radar detection)
                        * 5350 MHz [70] (disabled)
                        * 5360 MHz [72] (disabled)
                        * 5370 MHz [74] (disabled)
                        * 5380 MHz [76] (disabled)
                        * 5390 MHz [78] (disabled)
                        * 5400 MHz [80] (disabled)
                        * 5410 MHz [82] (disabled)
                        * 5420 MHz [84] (disabled)
                        * 5430 MHz [86] (disabled)
                        * 5440 MHz [88] (disabled)
                        * 5450 MHz [90] (disabled)
                        * 5460 MHz [92] (disabled)
                        * 5470 MHz [94] (disabled)
                        * 5480 MHz [96] (26.0 dBm) (radar detection)
                        * 5490 MHz [98] (26.0 dBm) (radar detection)
                        * 5500 MHz [100] (26.0 dBm) (radar detection)
                        * 5510 MHz [102] (26.0 dBm) (radar detection)
                        * 5520 MHz [104] (26.0 dBm) (radar detection)
                        * 5530 MHz [106] (26.0 dBm) (radar detection)
                        * 5540 MHz [108] (26.0 dBm) (radar detection)
                        * 5550 MHz [110] (26.0 dBm) (radar detection)
                        * 5560 MHz [112] (26.0 dBm) (radar detection)
                        * 5570 MHz [114] (26.0 dBm) (radar detection)
                        * 5580 MHz [116] (26.0 dBm) (radar detection)
                        * 5590 MHz [118] (26.0 dBm) (radar detection)
                        * 5600 MHz [120] (26.0 dBm) (radar detection)
                        * 5610 MHz [122] (26.0 dBm) (radar detection)
                        * 5620 MHz [124] (26.0 dBm) (radar detection)
                        * 5630 MHz [126] (26.0 dBm) (radar detection)
                        * 5640 MHz [128] (26.0 dBm) (radar detection)
                        * 5650 MHz [130] (26.0 dBm) (radar detection)
                        * 5660 MHz [132] (26.0 dBm) (radar detection)
                        * 5670 MHz [134] (26.0 dBm) (radar detection)
                        * 5680 MHz [136] (26.0 dBm) (radar detection)
                        * 5690 MHz [138] (26.0 dBm) (radar detection)
                        * 5700 MHz [140] (26.0 dBm) (radar detection)
                        * 5710 MHz [142] (26.0 dBm) (radar detection)
                        * 5720 MHz [144] (disabled)
                        * 5725 MHz [145] (disabled)
                        * 5730 MHz [146] (disabled)
                        * 5735 MHz [147] (13.0 dBm)
                        * 5740 MHz [148] (13.0 dBm)
                        * 5745 MHz [149] (13.0 dBm)
                        * 5750 MHz [150] (13.0 dBm)
                        * 5755 MHz [151] (13.0 dBm)
                        * 5760 MHz [152] (13.0 dBm)
                        * 5765 MHz [153] (13.0 dBm)
                        * 5770 MHz [154] (13.0 dBm)
                        * 5775 MHz [155] (13.0 dBm)
                        * 5780 MHz [156] (13.0 dBm)
                        * 5785 MHz [157] (13.0 dBm)
                        * 5790 MHz [158] (13.0 dBm)
                        * 5795 MHz [159] (13.0 dBm)
                        * 5800 MHz [160] (13.0 dBm)
                        * 5805 MHz [161] (13.0 dBm)
                        * 5810 MHz [162] (13.0 dBm)
                        * 5815 MHz [163] (13.0 dBm)
                        * 5820 MHz [164] (13.0 dBm)
                        * 5825 MHz [165] (13.0 dBm)
                        * 5830 MHz [166] (13.0 dBm)
                        * 5840 MHz [168] (13.0 dBm)
                        * 5850 MHz [170] (13.0 dBm)
                        * 5860 MHz [172] (13.0 dBm)
                        * 5870 MHz [174] (disabled)
                        * 5880 MHz [176] (disabled)
                        * 5890 MHz [178] (disabled)
                        * 5900 MHz [180] (disabled)
                        * 5910 MHz [182] (disabled)
                        * 5920 MHz [184] (disabled)
                        * 5930 MHz [186] (disabled)
                        * 5940 MHz [188] (disabled)
                        * 5950 MHz [0] (disabled)
                        * 5960 MHz [2] (disabled)
                        * 5970 MHz [4] (disabled)
                        * 5980 MHz [6] (disabled)
                        * 5990 MHz [8] (disabled)
                        * 6000 MHz [10] (disabled)
                        * 6010 MHz [12] (disabled)
                        * 6020 MHz [14] (disabled)
                        * 6030 MHz [16] (disabled)
                        * 6040 MHz [18] (disabled)
                        * 6050 MHz [20] (disabled)
                        * 6060 MHz [22] (disabled)
                        * 6070 MHz [24] (disabled)
                        * 6080 MHz [26] (disabled)
                        * 6090 MHz [28] (disabled)
                        * 6100 MHz [30] (disabled)
                        * 6110 MHz [32] (disabled)
                        * 6120 MHz [34] (disabled)
                        * 6130 MHz [36] (disabled)
                        * 6140 MHz [38] (disabled)
```

---

