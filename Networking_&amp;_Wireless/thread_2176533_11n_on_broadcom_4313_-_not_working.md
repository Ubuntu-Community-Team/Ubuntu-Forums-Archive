---
title: "11n on broadcom 4313 - not working"
date: 2013-09-24
forum: Networking &amp; Wireless
---

### Post by linuxgeoff on 2013-09-24
I've spend days searching every blog and try every suggestion I can find to no avail.  Please help if you can.

I have a lenovo with broadcom 4313 wlan.  Ubuntu 13.04, fresh install, network manager, by default.  I want to get 11n working.  The two configurations I've had most luck with are
1) the latest Broadcom drivers:  Everything works and gives me good 11g performance, but does not recognize the 11n capability of the card.  The card "mounts" to eth1 and denies me all but basic admin access (no set commands iwconfig allowed and canot read data, e.g. tx-power, bit rate etc back with iwconfig or wavemon

2) brcmsmac driver: recognizes the 11n capability, but gets very slow connections ( between 1 and 18 Mbit/s).  "mounts" on wlan0 and set and get functions seem to be supported.

What can I do to get this card working on an 11n network, please?  Thanks.

Here are some relevant outputs under both conditions:
```

brcmsmac lshw output:
*-network
                description: Network controller
                product: BCM4313 802.11b/g/n Wireless LAN Controller
                vendor: Broadcom Corporation
                physical id: 0
                bus info: pci@0000:02:00.0
                version: 01
                width: 64 bits
                clock: 33MHz
                capabilities: bus_master cap_list
                configuration: driver=bcma-pci-bridge latency=0
                resources: irq:17 memory:f0100000-f0103fff
-network
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: e0:06:e6:5d:6d:2f
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=brcmsmac driverversion=3.8.0-30-generic firmware=N/A ip=192.168.4.4 link=yes multicast=yes wireless=IEEE 802.11bgn

brcmsmac iwconfig output:
wlan0     IEEE 802.11bgn  ESSID:"xxxxxxx"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: A0:F3:C1:CF:CD:62   
          Bit Rate=1 Mb/s   Tx-Power=19 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=54/70  Signal level=-56 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:75   Missed beacon:0

Broadcom wl lshw output:
           *-network
                description: Wireless interface
                product: BCM4313 802.11b/g/n Wireless LAN Controller
                vendor: Broadcom Corporation
                physical id: 0
                bus info: pci@0000:02:00.0
                logical name: eth1
                version: 01
                serial: e0:06:e6:5d:6d:2f
                width: 64 bits
                clock: 33MHz
                capabilities: bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=wl0 driverversion=6.20.155.1 (r326264) ip=192.168.4.4 latency=0 multicast=yes wireless=IEEE 802.11abg
                resources: irq:17 memory:f0100000-f0103f

Broadcom wl iwconfig output: 
eth1      IEEE 802.11abg  ESSID:"xxxxxxxx"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: A0:F3:C1:CF:CD:62   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off


```

---

### Post by varunendra on 2013-09-26
Since the sta driver is not even recognizing the N-channel, I guess there is only brcmsmac that we can try a few things with. Internally, I don't think there is much to try apart from attempting to fix the speed to a higher rate, for example -
```
sudo iwconfig wlan0 rate 130M
```

But the above alone may fail miserably if the external factors don't support that much speed. For example, if you are using WEP encryption with TKIP, forget about speeds higher that 54 Mbps. Similarly, the noise and quality of the signal are also important factors. Link quality 54/70 is not bad, but not good either.

If you wish to discover possibilities available to you, please post back the outputs of -
```
uname -mr
nm-tool
sudo iwlist wlan0 scan
```
..obviously, when you are using the brcmsmac driver.

Feel free to remove/obscure the MAC addresses and SSIDs in the output, but leave the rest.

---

### Post by linuxgeoff on 2013-09-27
I'm sorry to say that I've mislaid the brmcsmac driver in all the changes i've experimented with, and I cannot figure out how to regain it, so I cannot post back the outputs!

I've tried disabling the wl driver and removed all the brcmsmac blacklists I could find, but it's just not there anymore, so now I have teh wl driver back again and live with the 11g performance (and the way it impacts all the other devices on the wifi network when it's running).  If you have any suggestions other than a fresh install, I'd appreciate it; otherwise I'm about ready to give up - maybe even go back to windows (after 7 years on ubuntu - which I love, but my marraige can't cope any more with the amount of time it takes to get and keep ubuntu working)

Thanks, anyway

---

### Post by varunendra on 2013-09-28
> **linuxgeoff said:**
> otherwise I'm about ready to give up - maybe even go back to windows (after 7 years on ubuntu - which I love, but my marraige can't cope any more with the amount of time it takes to get and keep ubuntu working)
Sorry to hear that, I must agree that unexpected regressions/bugs do become annoying sometimes. But I guess I'm fortunate enough that the overall advantage/usability has always remained better than windows for me.

Anyway, I think getting rid of wl and modprobing brcmsmac shouldn't be too difficult. Since it is part of the kernel, I don't think it can just disappear unless you have some serious breakage in the kernel.

What do these tell us ? -
```
modinfo brcmsmac
dpkg -l | grep bcmwl
grep -R brcm /etc/modprobe.d
cat /etc/modules
```

If brcmsmac is still there, it should show up in modinfo, if not, you may need to install/reinstall the kernel image.

---

### Post by linuxgeoff on 2013-09-30
I finally managed to get brcmsmac up and running again.  Will post responses soon.  Thanks for all your help!

---

### Post by linuxgeoff on 2013-09-30
```
 uname -mr
3.8.0-31-generic x86_64

```
```
nm-tool

NetworkManager Tool

State: connected (global)

- Device: wlan0  [zzzzzz] ---------------------------------------------------
  Type:              802.11 WiFi
  Driver:            brcmsmac
  State:             connected
  Default:           yes
  HW Address:        xxxxxxxxxxxxxx

  Capabilities:
    Speed:           24 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    QWJ4H:           Infra, xxxxxxxxxxx, Freq 2462 MHz, Rate 54 Mb/s, Strength 32 WPA2
    belkin.73c:      Infra, xxxxxxxxxxx, Freq 2437 MHz, Rate 54 Mb/s, Strength 29 WPA WPA2
    I9AU1:           Infra, xxxxxxxxxxx, Freq 2437 MHz, Rate 54 Mb/s, Strength 42 WEP
    hpsetup:         Ad-Hoc,xxxxxxxxxxx, Freq 2437 MHz, Rate 54 Mb/s, Strength 30
    *zzzzzzz:      Infra, xxxxxxxxxxx, Freq 2412 MHz, Rate 54 Mb/s, Strength 70 WPA WPA2
    JLKline's Network: Infra,xxxxxxxxxxx, Freq 2412 MHz, Rate 54 Mb/s, Strength 24 WPA2
    cookie monster:  Infra, xxxxxxxxxxx, Freq 2437 MHz, Rate 54 Mb/s, Strength 20 WPA2
    Margarets:       Infra, xxxxxxxxxxx, Freq 2412 MHz, Rate 54 Mb/s, Strength 19 WPA
    37CG4:           Infra, xxxxxxxxxxx, Freq 2462 MHz, Rate 54 Mb/s, Strength 19 WEP

  IPv4 Settings:
    Address:         192.168.4.6
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.4.1

    DNS:             71.243.0.14
    DNS:             71.250.0.14


- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             unavailable
  Default:           no
  HW Address:        xxxxxxxxxxxxxx

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off

```
```
sudo iwlist wlan0 scan
wlan0     Scan completed :
          Cell 01 - Address: xxxxxxxxx.2
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=58/70  Signal level=-52 dBm  
                    Encryption key:on
                    ESSID:"zzzzzzzzzzzz"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000000d6d95d3c
                    Extra: Last beacon: 88ms ago
                    IE: Unknown: 00097761697465686F6D65
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030101
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD1E00904C334C101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 2D1A4C101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C3401001B00000000000000000000000000000000000000
                    IE: Unknown: 3D1601001B00000000000000000000000000000000000000
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: Unknown: DD0A00037F04010006004000
          Cell 02 - Address: xxxxxxxxxxx
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=23/70  Signal level=-87 dBm  
                    Encryption key:on
                    ESSID:"JLKline's Network"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000003f206564a4
                    Extra: Last beacon: 88ms ago
                    IE: Unknown: 00114A4C4B6C696E652773204E6574776F726B
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030101
                    IE: Unknown: 0706555320010B1E
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 2D1AAD511BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 33027734
                    IE: Unknown: 33025106
                    IE: Unknown: 3D1601001100000000000000000000000000000000000000
                    IE: Unknown: 46050200010000
                    IE: Unknown: DD180050F2020101010003A4000027A4000042435E0062322F00
                    IE: Unknown: DD0700039301730B20
                    IE: Unknown: DD0E0017F2070001010628373747B048
                    IE: Unknown: DD0B0017F20100010100000007
          Cell 03 - Address: xxxxxxxxxxxxxxxxx
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=34/70  Signal level=-76 dBm  
                    Encryption key:on
                    ESSID:"I9AU1"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000158432a482
                    Extra: Last beacon: 88ms ago
                    IE: Unknown: 00054939415531
                    IE: Unknown: 010882848B0C12961824
                    IE: Unknown: 030106
                    IE: Unknown: 0706555320010B1B
                    IE: Unknown: 200100
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD0900037F010100200000
          Cell 04 - Address: xxxxxxxxxxxxxxxxxx
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=32/70  Signal level=-78 dBm  
                    Encryption key:on
                    ESSID:"zzzzzzzzzzz"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000085ca87ada5
                    Extra: Last beacon: 88ms ago
                    IE: Unknown: 000A62656C6B696E2E373363
                    IE: Unknown: 010882840B162430486C
                    IE: Unknown: 030106
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1AFC181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1606080400000000000000000000000000000000000000
                    IE: Unknown: DDA20050F204104A00011010440001021041000100103B00010310470010601A24F2DCAFC941F14A7BBFA5D1DDC71021001442656C6B696E20496E7465726E6174696F6E616C1023000A46394B3131303520763110240007312E30302E30361042000E31323132303847453130383534391054000800060050F20400011011001D42656C6B696E204E343530444220576972656C65737320526F75746572100800020084
                    IE: Unknown: DD090010180202F0040000
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 05 - Address: xxxxxxxxxxx
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=20/70  Signal level=-90 dBm  
                    Encryption key:on
                    ESSID:"zzzzzzzz"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000964120589
                    Extra: Last beacon: 88ms ago
                    IE: Unknown: 000E636F6F6B6965206D6F6E73746572
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030106
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 2A0102
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD180050F2020101020003A4000027A4000042435E0062322F00
                    IE: Unknown: 331A4C101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 2D1A4C101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 341606001B00000000000000000000000000000000000000
                    IE: Unknown: 3D1606001B00000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F0101
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: Unknown: DD0A00037F04010000000000
          Cell 06 - Address: xxxxxxxxxxxxxxxxx
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=22/70  Signal level=-88 dBm  
                    Encryption key:on
                    ESSID:"zzzzzzz"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000002231a51b183
                    Extra: Last beacon: 620ms ago
                    IE: Unknown: 00094D6172676172657473
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030101
                    IE: Unknown: 050402030000
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD0E0050F204104A0001101044000102
                    IE: Unknown: DD090010180204F0000000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 07 - Address: F8:E4:FB:8D:3C:11
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=29/70  Signal level=-81 dBm  
                    Encryption key:on
                    ESSID:"QWJ4H"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000012fd3d6431
                    Extra: Last beacon: 88ms ago
                    IE: Unknown: 000551574A3448
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 03010B
                    IE: Unknown: 200100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD180050F2020101060003A4000027A4000042435E0062322F00
                    IE: Unknown: 2D1A8C131BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D160B080800000000000000000000000000000000000000
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: Unknown: DD0A00037F04010000000000
                    IE: Unknown: 0706555320010B1B

```

---

### Post by varunendra on 2013-10-02
> **linuxgeoff said:**
> ```

    *zzzzzzz:      Infra, xxxxxxxxxxx, Freq 2412 MHz, Rate 54 Mb/s, Strength 70 **[COLOR="#FF0000"]WPA WPA2[/COLOR]**
```

Please change the encryption type in the router from WPA/WPA2 mixed mode to pure WPA2-PSK (AES). No mixed mode, not TKIP. Make the same changes in the connection settings in Network Manager (or delete the existing, creating a fresh one). Make sure IPv6 is set to "Ignore" in network manager. See if this helps you getting better speeds.

If still can't get better speeds, try changing your DNS to 8.8.8.8, 8.8.4.4. If this doesn't help either, please post the outputs of -
```
iwconfig
ifconfig
nm-tool
```

---

