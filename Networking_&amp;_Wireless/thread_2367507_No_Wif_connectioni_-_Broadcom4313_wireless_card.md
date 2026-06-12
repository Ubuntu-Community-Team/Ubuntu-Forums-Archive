---
title: "No Wif connectioni - Broadcom4313 wireless card"
date: 2017-07-31
forum: Networking &amp; Wireless
---

### Post by philpot2 on 2017-07-31
I have a netbook (HP-Mini 110-3100sg) with an Intel Atom N.455, 1.6 GHz, 2GB RAM and 250GB HDD.

I created a live USB with Lubuntu 16.04.2 LTS using UNetbootin and got this running.

Although I can use ethernet for an internet connection I couldn't get WiFi to work at all.

Reading posts on this forum it seems that getting Broadcom wireless cards to work with Linux is very problematic.

Using "lspci -nn -d 14e4" I have the following Broadcom wireless card.

Chip ID: BCM 4313
PCI ID: 14e4:4727 (rev 01)

The kernel driver is use: bcma-pci-bridge

I've tried many of the suggestions on this forum, but still can't resolve the issue getting WiFi to work.
I see a list of the possible WiFi connections that are available, but unable to get the one I have at home to work.

In the additional driver I saw that the BCM4313 802.11 bgn wireless network adapter is not working.
It stated next to "not in use"

Broadcom 802.11 Linux STA wireless driver source from bcmwl-kernel-source (proprietary)

Tried changing this to "using", but after doing this it finished up with "not in use" again.

1. Do I need to install Lubuntu first before I can resolve the issue with obtaining a WiFi connection?
2. What do I need to enter in the terminal that I can get a wireless connection?

I'm a complete beginner with Linux, so I'm hope someone can help me with the WiFi issue.

Thanks

Phil




[h=1][/h]

---

### Post by chili555 on 2017-07-31
First, make sure that the wireless switch or key combination is set to enable wireless; check from the terminal:```
rfkill list all
```Next, the device in question uses the driver brcmsmac. Let's unload b43 and load brcmsmac and see if the wireless starts:```
sudo modprobe -r b43
sudo modprobe brcmsmac
```Is a wireless interface created?```
iwconfig
```Any clues in the log?```
dmesg | grep brcm
```

---

### Post by philpot2 on 2017-08-01
> **chili555 said:**
> First, make sure that the wireless switch or key combination is set to enable wireless; check from the terminal:```
rfkill list all
```

After entering this I got:

0: hp-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: n


Next, the device in question uses the driver brcmsmac. Let's unload b43 and load brcmsmac and see if the wireless starts:```
sudo modprobe -r b43
sudo modprobe brcmsmac
```

After entering these two codes, no wireless interface seemed to be created.

Is a wireless interface created?```
iwconfig
```

wlp2s0b1  IEEE 802.11  ESSID: off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=30 dBm   
          Retry short limit:7   RTS thr: off   Fragment thr: off
          Power Management: off
          
enp1s0f0  no wireless extensions.

lo        no wireless extensions.


Confirmed by this code.

Any clues in the log?```
dmesg | grep brcm
```

This is what the log produced.

[   57.981113] brcmsmac bcma0:1: mfg 4bf core 812 rev 24 class 0 irq 17
[   58.062370] ieee80211 phy0: registered radio enabled led device: brcmsmac-phy0:radio gpio: 499
[   58.139903] brcmsmac bcma0:1 wlp2s0b1: renamed from wlan0
[   58.357522] brcmsmac bcma0:1: brcms_ops_bss_info_changed: qos enabled: false (implement)
[   58.357547] brcmsmac bcma0:1: brcms_ops_config: change power-save mode: false (implement)

There is still no WiFi connection, but hopefully the above will help you to find out what I now need to do.

Thanks.

Phil

---

### Post by chili555 on 2017-08-01
Yes! Indeed a wireless interface is created:> wlp2s0b1 IEEE 802.11 ESSID: off/any 
Mode:Managed Access Point: Not-Associated Tx-Power=30 dBm 
Retry short limit:7 RTS thr: off Fragment thr: off
Power Management: off
Does it scan and see networks?```
sudo iwlist wlp2s0b1 scan
```If it scans, we can probably get it connected. If not, what are the terminal errors, warnings, clues, etc.?

---

### Post by philpot2 on 2017-08-01
> **chili555 said:**
> Yes! Indeed a wireless interface is created. Does it scan and see networks?```
sudo iwlist wlp2s0b1 scan
```If it scans, we can probably get it connected. If not, what are the terminal errors, warnings, clues, etc.?

Here is the resultof the scan.

```
wlp2s0b1  Scan completed :
          Cell 01 - Address: 74:A2:E6:95:04:F2
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=53/70  Signal level=-57 dBm  
                    Encryption key off
                    ESSID:"AMD-Extranet"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000020b0e9888c5
                    Extra: Last beacon: 40ms ago
                    IE: Unknown: 000C414D442D45787472616E6574
                    IE: Unknown: 010882848B0C12961824
                    IE: Unknown: 030101
                    IE: Unknown: 0706444520010D14
                    IE: Unknown: 0B0504002B8D5B
                    IE: Unknown: 2A0100
                    IE: Unknown: 2D1AAC191BFFFFFF0000000000000000000000000000000000000000
                    IE: Unknown: 32043048606C
                    IE: Unknown: 3D1601000500000000000000000000000000000000000000
                    IE: Unknown: 7F06001000000040
                    IE: Unknown: 851E04008F000F00FF0359006D756E2D6E65772D61703031000000000400004C
                    IE: Unknown: 9606004096001000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD06004096010104
                    IE: Unknown: DD050040960305
                    IE: Unknown: DD050040960B09
                    IE: Unknown: DD050040961400
          Cell 02 - Address: 74:A2:E6:95:04:F0
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=63/70  Signal level=-47 dBm  
                    Encryption key on
                    ESSID:"amdwireless"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000020b0e98d432
                    Extra: Last beacon: 40ms ago
                    IE: Unknown: 000B616D64776972656C657373
                    IE: Unknown: 010882848B0C12961824
                    IE: Unknown: 030101
                    IE: Unknown: 0706444520010D14
                    IE: Unknown: 0B0504002B8D5B
                    IE: Unknown: 2A0100
                    IE: Unknown: 2D1AAC191BFFFFFF0000000000000000000000000000000000000000
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
                    IE: Unknown: 32043048606C
                    IE: Unknown: 3D1601000500000000000000000000000000000000000000
                    IE: Unknown: 7F06001000000040
                    IE: Unknown: 851E04008F000F00FF0359006D756E2D6E65772D61703031000000000400004C
                    IE: Unknown: 9606004096001000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD06004096010104
                    IE: Unknown: DD050040960305
                    IE: Unknown: DD050040960B09
                    IE: Unknown: DD050040961401
          Cell 03 - Address: 00:24:6C:24:09:61
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=35/70  Signal level=-75 dBm  
                    Encryption key off
                    ESSID:"guest"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000f5862f9206
                    Extra: Last beacon: 40ms ago
                    IE: Unknown: 00056775657374
                    IE: Unknown: 010882840B0C12161824
                    IE: Unknown: 030106
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: 2D1A4C101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D16060008000000FF000000000000000000000000000000
                    IE: Unknown: DD1E00904C334C101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C34060008000000FF000000000000000000000000000000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD0A00037F04010000000000
          Cell 04 - Address: 00:24:6C:24:09:60
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=34/70  Signal level=-76 dBm  
                    Encryption key on
                    ESSID:"perot"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000f5863091ab
                    Extra: Last beacon: 40ms ago
                    IE: Unknown: 00057065726F74
                    IE: Unknown: 010882840B0C12161824
                    IE: Unknown: 030106
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : 802.1x
                    IE: Unknown: 2D1A4C101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D16060008000000FF000000000000000000000000000000
                    IE: Unknown: DD1E00904C334C101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C34060008000000FF000000000000000000000000000000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD0A00037F04010000000000
          Cell 05 - Address: 24 DE:C6:C6:C6:50
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=31/70  Signal level=-79 dBm  
                    Encryption key on
                    ESSID:"east"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000106554e83dd
                    Extra: Last beacon: 19864ms ago
                    IE: Unknown: 000465617374
                    IE: Unknown: 010882840B0C12161824
                    IE: Unknown: 030106
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
                    IE: Unknown: 2D1ACC111BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1606000800000000000000000000000000000000000000
                    IE: Unknown: 7F080000080000000000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 06 - Address: 24 DE:C6:C6:B4:F0
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=30/70  Signal level=-80 dBm  
                    Encryption key on
                    ESSID:"east"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000001805d9eb349
                    Extra: Last beacon: 132ms ago
                    IE: Unknown: 000465617374
                    IE: Unknown: 010882840B0C12161824
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
                    IE: Unknown: 2D1ACC111BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D160B000800000000000000000000000000000000000000
                    IE: Unknown: 7F080000080000000000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 07 - Address: 24 DE:C6:C6:BC:61
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=32/70  Signal level=-78 dBm  
                    Encryption key off
                    ESSID:"DELL_Guest"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000f56bec2e8a
                    Extra: Last beacon: 20008ms ago
                    IE: Unknown: 000A44454C4C5F4775657374
                    IE: Unknown: 010882840B0C12161824
                    IE: Unknown: 030101
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: 2D1A8C111BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1601000800000000000000000000000000000000000000
                    IE: Unknown: 7F080000080000000000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 08 - Address: 24 DE:C6:C6:B4:F1
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=30/70  Signal level=-80 dBm  
                    Encryption key off
                    ESSID:"DELL_Guest"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000001805d9ebaea
                    Extra: Last beacon: 19352ms ago
                    IE: Unknown: 000A44454C4C5F4775657374
                    IE: Unknown: 010882840B0C12161824
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: 2D1A8C111BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D160B000800000000000000000000000000000000000000
                    IE: Unknown: 7F080000080000000000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 09 - Address: 24 DE:C6:C6:C5:30
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=29/70  Signal level=-81 dBm  
                    Encryption key on
                    ESSID:"east"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000001805dc5b7b8
                    Extra: Last beacon: 19376ms ago
                    IE: Unknown: 000465617374
                    IE: Unknown: 010882840B160C121824
                    IE: Unknown: 03010B
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
                    IE: Unknown: 2D1ACC111BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D160B000800000000000000000000000000000000000000
                    IE: Unknown: 7F080000080000000000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD07000B8601040812
          Cell 10 - Address: 24 DE:C6:C6:C6:51
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=33/70  Signal level=-77 dBm  
                    Encryption key off
                    ESSID:"DELL_Guest"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000010664521aa2
                    Extra: Last beacon: 19764ms ago
                    IE: Unknown: 000A44454C4C5F4775657374
                    IE: Unknown: 010882840B160C121824
                    IE: Unknown: 030106
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: 2D1A8C111BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1606000800000000000000000000000000000000000000
                    IE: Unknown: 7F080000080000000000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD07000B8601040813
```

This means nothing to me, but assume zou know what to look for.

Thanks.

Phil

---

### Post by philpot2 on 2017-08-01
> **chili555 said:**
> Yes! Indeed a wireless interface is created

Based on your reply, I just tried to get a WiFi connection and it was successful.
WiFi is now working.

I'll try this out at home tonight to make sure the WiFi is working correctly.

Many thanks for your help in resolving the WiFi issue.

Phil

---

### Post by chili555 on 2017-08-01
It will probably be helpful to blacklist the conflicting drivers:```
sudo -i
echo "blacklist b43" >>  /etc/modprobe.d/blacklist.conf
echo "blacklist ssb" >>  /etc/modprobe.d/blacklist.conf
exit
```However, if you also have a Broadcom ethernet card, it will disable it, too. Before you proceed, check:```
lspci -nnk | grep 0200
```If it is not a Broadcom, please proceed. If it is, post back and I'll refine the process.

---

### Post by philpot2 on 2017-08-02
I have a Realthek ethernet card, so it would be no problem to blacklist conflicting drivers.

I tried out the live USB Lubuntu at home and had to enter all the codes again.

This time I was unable to to get a WiFi connection, and I think it has something to do with my home server.

I have a Fritz!box 7490 which has no issues with obtaining a WiFi connection for a Windows 10 tablet, Android smartphones,  smart TV, eBook reader and Nintendo Wii U.

Using Lubuntu, I see Fritz!Box 7490 in the list of WiFi connections. After entering the router password nothing happens and there is no WiFi connection.

I find it very strange that my router works fine for all the other devices, but not for Lubuntu.

Do you know what I need to do to get a WiFi connection to my router when using Lubuntu.

Thanks.

Phil.

---

