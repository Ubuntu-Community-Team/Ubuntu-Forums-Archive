---
title: "Need help with wifi drivers for laptop? I'm totally stumped."
date: 2016-05-03
forum: Networking &amp; Wireless
---

### Post by SpaceManJack on 2016-05-03
Ok I got a Lenovo laptop, purchased it November of last year. This laptop had windows 10 pre-installed and what I have done is I installed ubuntu 16.04 LTS on it, just did an "erase disk and install ubuntu" on it. It connects to my wifi but the connection will drop in and out. What I mean is, my wifi will show that I do indeed have wifi and it says I'm connected but in reality its not, I will go to a webpage and it wont load (I need to clarify that a moment later it will load and then a moment later the connection will drop out again) and it'll say I have no internet connection even though my wifi indicator says I do. I took a screenshot of it so you can see firsthand, please follow link [http://imgur.com/eYb08U1](http://imgur.com/eYb08U1)

After doing research it would seem I need to make sure that my wifi drivers are working correctly first. Ok I'm not even sure if my computer has wifi drivers on it or if it does I'm not sure they're the correct ones. So here's some info to get things started. And btw I really do appreciate it, trying to get this figured out by myself got me pulling my hair out!

Ok so I have gone to the settings and checked for additional drivers and this is what I got, please follow this link to see the screenshot I took so you can see firsthand for yourself 
[http://imgur.com/dZaU7SG](http://imgur.com/dZaU7SG)

Here are the commands I'ver entered so far into my terminal
lspci -nn -d 10ec
lsusb
sudo lspci -v
lspci -nn | grep 0280
lspci -knn | grep Net -A2

And here's the results of said commads, I'm posting all this now cause from reading other forum posts I assumed you'd ask me to enter these commands and show you the results so I'm trying to save times is all. And of course I'm a real greenhorn when it comes to linux so if there are other commands you want me to enter in go ahead and just ask, thanks.

p.s. So basically take a look over all this info here and tell me exactly what I need to do in order to get my wifi running smooth, thank you for your time.

```
scott@james:~$ lspci -nn -d 10ec
lspci: -d: ':' expected
```

```
scott@james:~$ lsusb
Bus 002 Device 004: ID 174f:1158 Syntek 
Bus 002 Device 003: ID 0bda:0821 Realtek Semiconductor Corp. 
Bus 002 Device 002: ID 0438:7900 Advanced Micro Devices, Inc. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 0bda:0129 Realtek Semiconductor Corp. RTS5129 Card Reader Controller
Bus 001 Device 002: ID 0438:7900 Advanced Micro Devices, Inc. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```

```
scott@james:~$ sudo lspci -v
00:00.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Device 1566
    Subsystem: Lenovo Device 3806
    Flags: bus master, fast devsel, latency 0

00:01.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Mullins [Radeon R4/R5 Graphics] (rev 45) (prog-if 00 [VGA controller])
    Subsystem: Lenovo Mullins [Radeon R4/R5 Graphics]
    Flags: bus master, fast devsel, latency 0, IRQ 34
    Memory at e0000000 (64-bit, prefetchable) [size=256M]
    Memory at f0000000 (64-bit, prefetchable) [size=8M]
    I/O ports at 3000 [size=256]
    Memory at f0c00000 (32-bit, non-prefetchable) [size=256K]
    Expansion ROM at f0800000 [disabled] [size=128K]
    Capabilities: [48] Vendor Specific Information: Len=08 <?>
    Capabilities: [50] Power Management version 3
    Capabilities: [58] Express Root Complex Integrated Endpoint, MSI 00
    Capabilities: [a0] MSI: Enable+ Count=1/1 Maskable- 64bit+
    Capabilities: [100] Vendor Specific Information: ID=0001 Rev=1 Len=010 <?>
    Capabilities: [270] #19
    Capabilities: [2b0] Address Translation Service (ATS)
    Capabilities: [2c0] #13
    Capabilities: [2d0] #1b
    Kernel driver in use: radeon
    Kernel modules: radeon

00:01.1 Audio device: Advanced Micro Devices, Inc. [AMD/ATI] Kabini HDMI/DP Audio
    Subsystem: Lenovo Kabini HDMI/DP Audio
    Flags: bus master, fast devsel, latency 0, IRQ 38
    Memory at f0c60000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: [48] Vendor Specific Information: Len=08 <?>
    Capabilities: [50] Power Management version 3
    Capabilities: [58] Express Root Complex Integrated Endpoint, MSI 00
    Capabilities: [a0] MSI: Enable+ Count=1/1 Maskable- 64bit+
    Capabilities: [100] Vendor Specific Information: ID=0001 Rev=1 Len=010 <?>
    Kernel driver in use: snd_hda_intel
    Kernel modules: snd_hda_intel

00:02.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Device 156b
    Flags: fast devsel

00:02.3 PCI bridge: Advanced Micro Devices, Inc. [AMD] Family 16h Processor Functions 5:1 (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0, IRQ 25
    Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
    I/O behind bridge: 00002000-00002fff
    Memory behind bridge: f0b00000-f0bfffff
    Capabilities: [50] Power Management version 3
    Capabilities: [58] Express Root Port (Slot+), MSI 00
    Capabilities: [a0] MSI: Enable+ Count=1/1 Maskable- 64bit+
    Capabilities: [b0] Subsystem: Lenovo Family 16h Processor Functions 5:1
    Capabilities: [b8] HyperTransport: MSI Mapping Enable+ Fixed+
    Capabilities: [100] Vendor Specific Information: ID=0001 Rev=1 Len=010 <?>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:02.4 PCI bridge: Advanced Micro Devices, Inc. [AMD] Family 16h Processor Functions 5:1 (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0, IRQ 26
    Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
    I/O behind bridge: 00001000-00001fff
    Memory behind bridge: f0a00000-f0afffff
    Prefetchable memory behind bridge: 00000000f0d00000-00000000f0efffff
    Capabilities: [50] Power Management version 3
    Capabilities: [58] Express Root Port (Slot+), MSI 00
    Capabilities: [a0] MSI: Enable+ Count=1/1 Maskable- 64bit+
    Capabilities: [b0] Subsystem: Lenovo Family 16h Processor Functions 5:1
    Capabilities: [b8] HyperTransport: MSI Mapping Enable+ Fixed+
    Capabilities: [100] Vendor Specific Information: ID=0001 Rev=1 Len=010 <?>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:08.0 Encryption controller: Advanced Micro Devices, Inc. [AMD] Device 1537
    Subsystem: Lenovo Device 3806
    Flags: bus master, fast devsel, latency 0
    Memory at f0c40000 (64-bit, prefetchable) [size=128K]
    Memory at f0900000 (32-bit, non-prefetchable) [size=1M]
    Memory at f0c6c000 (32-bit, non-prefetchable) [size=4K]
    Memory at f0c6a000 (32-bit, non-prefetchable) [size=8K]
    Capabilities: [50] MSI-X: Enable+ Count=2 Masked-
    Capabilities: [5c] HyperTransport: MSI Mapping Enable+ Fixed+
    Capabilities: [60] Power Management version 3
    Kernel driver in use: ccp
    Kernel modules: ccp

00:10.0 USB controller: Advanced Micro Devices, Inc. [AMD] FCH USB XHCI Controller (rev 11) (prog-if 30 [XHCI])
    Subsystem: Lenovo FCH USB XHCI Controller
    Flags: bus master, fast devsel, latency 0
    Memory at f0c68000 (64-bit, non-prefetchable) [size=8K]
    Capabilities: [50] Power Management version 3
    Capabilities: [70] MSI: Enable- Count=1/8 Maskable- 64bit+
    Capabilities: [90] MSI-X: Enable+ Count=8 Masked-
    Capabilities: [a0] Express Root Complex Integrated Endpoint, MSI 00
    Capabilities: [100] Latency Tolerance Reporting
    Kernel driver in use: xhci_hcd

00:11.0 SATA controller: Advanced Micro Devices, Inc. [AMD] FCH SATA Controller [AHCI mode] (rev 40) (prog-if 01 [AHCI 1.0])
    Subsystem: Lenovo FCH SATA Controller [AHCI mode]
    Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 32
    I/O ports at 3118 [size=8]
    I/O ports at 3124 [size=4]
    I/O ports at 3110 [size=8]
    I/O ports at 3120 [size=4]
    I/O ports at 3100 [size=16]
    Memory at f0c6d000 (32-bit, non-prefetchable) [size=1K]
    Capabilities: [60] Power Management version 3
    Capabilities: [70] SATA HBA v1.0
    Capabilities: [50] MSI: Enable+ Count=1/8 Maskable- 64bit+
    Kernel driver in use: ahci
    Kernel modules: ahci

00:12.0 USB controller: Advanced Micro Devices, Inc. [AMD] FCH USB EHCI Controller (rev 39) (prog-if 20 [EHCI])
    Subsystem: Lenovo FCH USB EHCI Controller
    Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 18
    Memory at f0c6d500 (32-bit, non-prefetchable) [size=256]
    Capabilities: [c0] Power Management version 2
    Capabilities: [e4] Debug port: BAR=1 offset=00e0
    Kernel driver in use: ehci-pci

00:13.0 USB controller: Advanced Micro Devices, Inc. [AMD] FCH USB EHCI Controller (rev 39) (prog-if 20 [EHCI])
    Subsystem: Lenovo FCH USB EHCI Controller
    Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 18
    Memory at f0c6d400 (32-bit, non-prefetchable) [size=256]
    Capabilities: [c0] Power Management version 2
    Capabilities: [e4] Debug port: BAR=1 offset=00e0
    Kernel driver in use: ehci-pci

00:14.0 SMBus: Advanced Micro Devices, Inc. [AMD] FCH SMBus Controller (rev 42)
    Subsystem: Lenovo FCH SMBus Controller
    Flags: 66MHz, medium devsel
    Kernel modules: i2c_piix4

00:14.2 Audio device: Advanced Micro Devices, Inc. [AMD] FCH Azalia Controller (rev 02)
    Subsystem: Lenovo FCH Azalia Controller
    Flags: bus master, slow devsel, latency 32, IRQ 16
    Memory at f0c64000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: [50] Power Management version 2
    Kernel driver in use: snd_hda_intel
    Kernel modules: snd_hda_intel

00:14.3 ISA bridge: Advanced Micro Devices, Inc. [AMD] FCH LPC Bridge (rev 11)
    Subsystem: Lenovo FCH LPC Bridge
    Flags: bus master, 66MHz, medium devsel, latency 0

00:18.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Device 1580
    Flags: fast devsel

00:18.1 Host bridge: Advanced Micro Devices, Inc. [AMD] Device 1581
    Flags: fast devsel

00:18.2 Host bridge: Advanced Micro Devices, Inc. [AMD] Device 1582
    Flags: fast devsel
    Kernel modules: amd64_edac_mod

00:18.3 Host bridge: Advanced Micro Devices, Inc. [AMD] Device 1583
    Flags: fast devsel
    Capabilities: [f0] Secure device <?>
    Kernel driver in use: k10temp
    Kernel modules: k10temp

00:18.4 Host bridge: Advanced Micro Devices, Inc. [AMD] Device 1584
    Flags: fast devsel
    Kernel driver in use: fam15h_power
    Kernel modules: fam15h_power

00:18.5 Host bridge: Advanced Micro Devices, Inc. [AMD] Device 1585
    Flags: fast devsel

01:00.0 Network controller: Realtek Semiconductor Co., Ltd. RTL8821AE 802.11ac PCIe Wireless Network Adapter
    Subsystem: Lenovo RTL8821AE 802.11ac PCIe Wireless Network Adapter
    Flags: bus master, fast devsel, latency 0, IRQ 37
    I/O ports at 2000 [size=256]
    Memory at f0b00000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: [40] Power Management version 3
    Capabilities: [50] MSI: Enable+ Count=1/1 Maskable- 64bit+
    Capabilities: [70] Express Endpoint, MSI 00
    Capabilities: [100] Advanced Error Reporting
    Capabilities: [140] Device Serial Number 00-e0-4c-ff-fe-87-2b-01
    Capabilities: [150] Latency Tolerance Reporting
    Capabilities: [158] L1 PM Substates
    Kernel driver in use: rtl8821ae
    Kernel modules: rtl8821ae

02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 15)
    Subsystem: Lenovo RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
    Physical Slot: 0
    Flags: bus master, fast devsel, latency 0, IRQ 33
    I/O ports at 1000 [size=256]
    Memory at f0a04000 (64-bit, non-prefetchable) [size=4K]
    Memory at f0a00000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: [40] Power Management version 3
    Capabilities: [50] MSI: Enable+ Count=1/1 Maskable- 64bit+
    Capabilities: [70] Express Endpoint, MSI 01
    Capabilities: [b0] MSI-X: Enable- Count=4 Masked-
    Capabilities: [100] Advanced Error Reporting
    Capabilities: [140] Virtual Channel
    Capabilities: [160] Device Serial Number 01-00-00-00-68-4c-e0-00
    Capabilities: [170] Latency Tolerance Reporting
    Capabilities: [178] L1 PM Substates
    Kernel driver in use: r8169
    Kernel modules: r8169

scott@james:~$ lspci -nn | grep 0280
01:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8821AE 802.11ac PCIe Wireless Network Adapter [10ec:8821]

scott@james:~$ lspci -knn | grep Net -A2
01:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8821AE 802.11ac PCIe Wireless Network Adapter [10ec:8821]
    Subsystem: Lenovo RTL8821AE 802.11ac PCIe Wireless Network Adapter [17aa:a814]
    Kernel driver in use: rtl8821ae
    Kernel modules: rtl8821ae
```

---

### Post by ajgreeny on 2016-05-03
Please use **Code-Tags** for terminal output. See my signature below for a **How-to**

I have added them on your behalf this time, but in future it will help us if you do it when posting terminal code.

---

### Post by chili555 on 2016-05-03
> Realtek Semiconductor Co., Ltd. RTL8821AE 802.11ac PCIe Wireless Network Adapter [10ec:8821]
    Subsystem: Lenovo RTL8821AE 802.11ac PCIe Wireless Network Adapter [17aa:a814]
    Kernel driver in use: rtl8821aeIt looks like the right driver to me.

Let's try to see why it drops. May we also see:```
sudo iwlist scan
iwconfig
dmesg | grep rtl
```Thanks.

---

### Post by SpaceManJack on 2016-05-05
```

scott@james:~$ sudo iwlist scan
[sudo] password for scott: 
enp2s0    Interface doesn't support scanning.

wlp1s0    Scan completed :
          Cell 01 - Address: 2C:30:33:46:AC:39
                    Channel:153
                    Frequency:5.765 GHz
                    Quality=70/70  Signal level=-32 dBm  
                    Encryption key:on
                    ESSID:"NETGEAR08-5G"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000008eb113618fa
                    Extra: Last beacon: 36ms ago
                    IE: Unknown: 000C4E45544745415230382D3547
                    IE: Unknown: 01088C129824B048606C
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 0B050100040000
                    IE: Unknown: 2D1AFE091BFFFF000001000000000000000000000000000000000000
                    IE: Unknown: 3D16990F0400000000000000000000000000000000000000
                    IE: Unknown: 7F080400080000000040
                    IE: Unknown: DD800050F204104A0001101044000102103B000103104700106DF0F4C83B2F92D09412201488069AD7102100074E657467656172102300074E6574676561721024000631323334353610420007303030303030311054000800060050F2040001101100094E6574676561724150100800022008103C0001031049000600372A000120
                    IE: Unknown: DD090010180201000C0000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: 46057208010000
          Cell 02 - Address: 20:4E:7F:BD:23:B2
                    Channel:153
                    Frequency:5.765 GHz
                    Quality=43/70  Signal level=-67 dBm  
                    Encryption key:on
                    ESSID:"NETGEAR43-5G"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000ea53d3085dc
                    Extra: Last beacon: 36ms ago
                    IE: Unknown: 000C4E45544745415234332D3547
                    IE: Unknown: 01088C129824B048606C
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 2D1AFE081EFFFF000001000000000000000000000000000000000000
                    IE: Unknown: 3D16990F0000000000000000000000000000000000000000
                    IE: Unknown: DD7F0050F204104A0001101044000102103B00010310470010911C7FC51E9543DB2BBD47870CD8F3D11021000D4E4554474541522C20496E632E1023000A574E44523334303076321024000A574E44523334303076321042000230311054000800060050F20400011011000A574E4452333430307632100800020004103C000103
                    IE: Unknown: DD090010180200F0040000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 03 - Address: 22:86:8C:E6:85:50
                    Channel:153
                    Frequency:5.765 GHz
                    Quality=36/70  Signal level=-74 dBm  
                    Encryption key:off
                    ESSID:"xfinitywifi"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000008d4ae5383b
                    Extra: Last beacon: 160ms ago
                    IE: Unknown: 000B7866696E69747977696669
                    IE: Unknown: 01088C129824B048606C
                    IE: Unknown: 030199
                    IE: Unknown: 050400010000
                    IE: Unknown: 07425553202401182801182C01183001183401173801173C01174001176401186801186C01187001187401188401188801188C011895011E99011E9D011EA1011EA5011E
                    IE: Unknown: 200103
                    IE: Unknown: 2D1AEF091BFFFFFF0000000000000000000100000000000000000000
                    IE: Unknown: 3D16990F0400000000000000000000000000000000000000
                    IE: Unknown: 7F0800000F0000000040
                    IE: Unknown: BF0CB2018033EAFF0000EAFF0000
                    IE: Unknown: C005019B00FCFF
                    IE: Unknown: C30402C4C4C4
                    IE: Unknown: DD180050F2020101840003A4000027A4000042435E0062322F00
                    IE: Unknown: DD0900037F01010000FF7F
          Cell 04 - Address: 10:86:8C:E6:85:50
                    Channel:153
                    Frequency:5.765 GHz
                    Quality=37/70  Signal level=-73 dBm  
                    Encryption key:on
                    ESSID:"idontcare"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000008d4ad84be7
                    Extra: Last beacon: 36ms ago
                    IE: Unknown: 000969646F6E7463617265
                    IE: Unknown: 01088C129824B048606C
                    IE: Unknown: 030199
                    IE: Unknown: 07425553202401182801182C01183001183401173801173C01174001176401186801186C01187001187401188401188801188C011895011E99011E9D011EA1011EA5011E
                    IE: Unknown: 200103
                    IE: Unknown: 2D1AEF091BFFFFFF0000000000000000000100000000000000000000
                    IE: Unknown: 3D16990F0400000000000000000000000000000000000000
                    IE: Unknown: 7F0800000F0000000040
                    IE: Unknown: BF0CB2018033EAFF0000EAFF0000
                    IE: Unknown: C005019B00FCFF
                    IE: Unknown: C30402C4C4C4
                    IE: Unknown: DD180050F2020101840003A4000027A4000042435E0062322F00
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD9F0050F204104A0001101044000102103B0001031047001049AF2610044557D7A46061F4017B21331021001C41746865726F7320436F6D6D756E69636174696F6E732C20496E632E102300044150787810240008415078782D7878781042001253657269616C204E756D62657220486572651054000800060050F20400011011000941746865726F734150100800020004103C0001021049000600372A000120
          Cell 05 - Address: 12:86:8C:E6:85:4A
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=42/70  Signal level=-68 dBm  
                    Encryption key:on
                    ESSID:""
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000008d49001180
                    Extra: Last beacon: 10472ms ago
                    IE: Unknown: 0000
                    IE: Unknown: 010882848B968C129824
                    IE: Unknown: 030106
                    IE: Unknown: 050400010000
                    IE: Unknown: 0706555320010B1E
                    IE: Unknown: 2A0100
                    IE: Unknown: 3204B048606C
                    IE: Unknown: 2D1AAD011BFFFFFF00000000000000000001000000000406E6470D00
                    IE: Unknown: 3D1606000100000000000000000000000000000000000000
                    IE: Unknown: 7F080000000000000040
                    IE: Unknown: DD180050F2020101840003A4000027A4000042435E0062322F00
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 06 - Address: 2C:30:33:7A:D8:5B
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=70/70  Signal level=-19 dBm  
                    Encryption key:on
                    ESSID:"NETGEAR08"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000011d6b213f5
                    Extra: Last beacon: 36ms ago
                    IE: Unknown: 00094E4554474541523038
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030106
                    IE: Unknown: 2A0104
                    IE: Unknown: 2F0104
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 0B050100370000
                    IE: Unknown: 2D1ABC191BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1606080400000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F080500080000000040
                    IE: Unknown: DD800050F204104A0001101044000102103B000103104700106DF0F4C83B2F92D09412201488069AD7102100074E657467656172102300074E6574676561721024000631323334353610420007303030303030311054000800060050F2040001101100094E6574676561724150100800022008103C0001031049000600372A000120
                    IE: Unknown: DD090010180201000C0000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: 46057208010000
          Cell 07 - Address: 10:86:8C:E6:85:4A
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=46/70  Signal level=-64 dBm  
                    Encryption key:on
                    ESSID:"idontcare"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000008d48f6fdb6
                    Extra: Last beacon: 36ms ago
                    IE: Unknown: 000969646F6E7463617265
                    IE: Unknown: 010882848B968C129824
                    IE: Unknown: 030106
                    IE: Unknown: 0706555320010B1E
                    IE: Unknown: 2A0100
                    IE: Unknown: 3204B048606C
                    IE: Unknown: 2D1AAD011BFFFFFF00000000000000000001000000000406E6470D00
                    IE: Unknown: 3D1606000100000000000000000000000000000000000000
                    IE: Unknown: 7F080000000000000040
                    IE: Unknown: DD180050F2020101840003A4000027A4000042435E0062322F00
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD9F0050F204104A0001101044000102103B0001031047001049AF2610044557D7A46061F4017B21331021001C41746865726F7320436F6D6D756E69636174696F6E732C20496E632E102300044150787810240008415078782D7878781042001253657269616C204E756D62657220486572651054000800060050F20400011011000941746865726F734150100800020004103C0001021049000600372A000120
          Cell 08 - Address: 20:4E:7F:BD:23:B3
                    Channel:7
                    Frequency:2.442 GHz (Channel 7)
                    Quality=54/70  Signal level=-56 dBm  
                    Encryption key:on
                    ESSID:"NETGEAR43"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000008244e45787f
                    Extra: Last beacon: 36ms ago
                    IE: Unknown: 00094E4554474541523433
                    IE: Unknown: 010882840B162430486C
                    IE: Unknown: 030107
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1AFC181FFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1607080400000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F0101
                    IE: Unknown: DD7F0050F204104A0001101044000102103B00010310470010911C7FC51E9543DB2BBD47870CD8F3D11021000D4E4554474541522C20496E632E1023000A574E44523334303076321024000A574E44523334303076321042000230311054000800060050F20400011011000A574E4452333430307632100800020004103C000103
                    IE: Unknown: DD090010180202F0040000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 09 - Address: 40:16:7E:5C:03:B0
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=50/70  Signal level=-60 dBm  
                    Encryption key:on
                    ESSID:"EUTHYPHRO"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000002b57eb02be1
                    Extra: Last beacon: 36ms ago
                    IE: Unknown: 000945555448595048524F
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030106
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1ABD1917FFFFFF0000000000000000000000000000000000000000
                    IE: Unknown: 3D1606080400000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F080100000000000040
                    IE: Unknown: DDAC0050F204104A0001101044000102103B0001031047001044143303D2F4F55544ADC3583F7BC78B102100154153555354654B20436F6D707574657220496E632E1023001C57692D46692050726F74656374656420536574757020526F757465721024000752542D4E3636551042001134303A31363A37653A35633A30333A62301054000800060050F20400011011000752542D4E363655100800022008103C0001011049000600372A000120
                    IE: Unknown: DD090010180203001C0000
                    IE: Unknown: DD180050F2020101840003A4000027A4000042435E0062322F00
          Cell 10 - Address: 22:86:8C:E6:85:4A
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=44/70  Signal level=-66 dBm  
                    Encryption key:off
                    ESSID:"xfinitywifi"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000008d48f779d9
                    Extra: Last beacon: 36ms ago
                    IE: Unknown: 000B7866696E69747977696669
                    IE: Unknown: 010882848B968C129824
                    IE: Unknown: 030106
                    IE: Unknown: 0706555320010B1E
                    IE: Unknown: 2A0100
                    IE: Unknown: 3204B048606C
                    IE: Unknown: 2D1AAD011BFFFFFF00000000000000000001000000000406E6470D00
                    IE: Unknown: 3D1606000100000000000000000000000000000000000000
                    IE: Unknown: 7F080000000000000040
                    IE: Unknown: DD180050F2020101840003A4000027A4000042435E0062322F00
                    IE: Unknown: DD0900037F01010000FF7F
          Cell 11 - Address: 88:F7:C7:37:C4:DA
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=46/70  Signal level=-64 dBm  
                    Encryption key:on
                    ESSID:"Tribbles-3"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000100bc9795b3
                    Extra: Last beacon: 36ms ago
                    IE: Unknown: 000A54726962626C65732D33
                    IE: Unknown: 010882848B9624B0486C
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32048C129860
                    IE: Unknown: 2D1ABD181BFFFFFF0000000000000000000000000000000000000000
                    IE: Unknown: 3D160B081100000000000000000000000000000000000000
                    IE: Unknown: DD8C0050F204104A0001101044000102103B0001031047001059FE281D202D5E5F5298ADBFD36D3E321021000B546563686E69636F6C6F721023000B546563686E69636F6C6F721024000631323334353610420007303030303030311054000800060050F20400011011000D546563686E69636F6C6F724150100800022008103C0001011049000600372A000120
                    IE: Unknown: DD090010180200001C0000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F20201018C0003A4000027A4000042435E0062322F00
          Cell 12 - Address: 8A:F7:C7:37:C4:DB
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=46/70  Signal level=-64 dBm  
                    Encryption key:on
                    ESSID:"\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000100bc976474
                    Extra: Last beacon: 8812ms ago
                    IE: Unknown: 000C000000000000000000000000
                    IE: Unknown: 010882848B9624B0486C
                    IE: Unknown: 03010B
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32048C129860
                    IE: Unknown: 2D1ABD181BFFFFFF0000000000000000000000000000000000000000
                    IE: Unknown: 3D160B081100000000000000000000000000000000000000
                    IE: Unknown: DD090010180200001C0000
                    IE: Unknown: DD180050F20201018C0003A4000027A4000042435E0062322F00
          Cell 13 - Address: C0:7C:D1:89:EC:2A
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=40/70  Signal level=-70 dBm  
                    Encryption key:off
                    ESSID:"xfinitywifi"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000001584de559b
                    Extra: Last beacon: 10120ms ago
                    IE: Unknown: 000B7866696E69747977696669
                    IE: Unknown: 010882848B968C129824
                    IE: Unknown: 03010B
                    IE: Unknown: 050400010000
                    IE: Unknown: 0706555320010B1E
                    IE: Unknown: 2A0100
                    IE: Unknown: 3204B048606C
                    IE: Unknown: 2D1AAD011BFFFFFF0000000000000000000100000000000000000000
                    IE: Unknown: 3D160B000500000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F080100000000000040
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD0900037F01010000FF7F
          Cell 14 - Address: 20:4E:7F:40:29:BC
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=48/70  Signal level=-62 dBm  
                    Encryption key:on
                    ESSID:"Supercreep"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000006dfabb86cfc
                    Extra: Last beacon: 36ms ago
                    IE: Unknown: 000A53757065726372656570
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: 2D1AAC011BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D160B001500000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F0101
                    IE: Unknown: DD180050F2020101820003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C33AC011BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C340B001500000000000000000000000000000000000000
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD8B0050F204104A0001101044000102103B00010310470010EC4EB8EE2C4253F08293204E7F4029BD102100044E54475210230007574E52323030301024000256331042000C3230346537663430323962641054000800060050F204000110110016574E5232303030763328576972656C65737320415029100800020004103C0001011049000600372A000120
          Cell 15 - Address: C0:7C:D1:89:EC:28
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=48/70  Signal level=-62 dBm  
                    Encryption key:on
                    ESSID:"HOME-0AAF-2.4"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000001584e7a5d3
                    Extra: Last beacon: 36ms ago
                    IE: Unknown: 000D484F4D452D304141462D322E34
                    IE: Unknown: 010882848B968C129824
                    IE: Unknown: 03010B
                    IE: Unknown: 0706555320010B1E
                    IE: Unknown: 2A0100
                    IE: Unknown: 3204B048606C
                    IE: Unknown: 2D1AAD011BFFFFFF0000000000000000000100000000000000000000
                    IE: Unknown: 3D160B000500000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F080100000000000040
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: Unknown: DD8D0050F204104A0001101044000102103B00010310470010D189AE46CBCA51B48FC275F2ED2A751710210013436973636F2053797374656D732C20496E632E10230007445043333934311024000744504333393431104200093030303030303030311054000800060050F2040001101100074450433339343110080002210C103C0001011049000600372A000120
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 16 - Address: 0C:54:A5:61:75:B2
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=44/70  Signal level=-66 dBm  
                    Encryption key:off
                    ESSID:"xfinitywifi"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000100ae808688
                    Extra: Last beacon: 36ms ago
                    IE: Unknown: 000B7866696E69747977696669
                    IE: Unknown: 010882848B968C129824
                    IE: Unknown: 03010B
                    IE: Unknown: 0706555320010B1E
                    IE: Unknown: 2A0100
                    IE: Unknown: 3204B048606C
                    IE: Unknown: 2D1AAD011BFFFFFF0000000000000000000100000000000000000000
                    IE: Unknown: 3D160B080400000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F080100000000000040
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD0900037F01010000FF7F
          Cell 17 - Address: 62:45:B0:4F:0D:2F
                    Channel:36
                    Frequency:5.18 GHz (Channel 36)
                    Quality=38/70  Signal level=-72 dBm  
                    Encryption key:on
                    ESSID:""
                    Mode:Master
                    Extra:tsf=0000008d54dd902b
                    Extra: Last beacon: 8484ms ago
                    IE: Unknown: 0000
                    IE: Unknown: DD100050F211011000A52C30000000000000
          Cell 18 - Address: C0:7C:D1:89:EC:30
                    Channel:36
                    Frequency:5.18 GHz (Channel 36)
                    Quality=36/70  Signal level=-74 dBm  
                    Encryption key:on
                    ESSID:"HOME-0AAF-5"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000001593ffa244
                    Extra: Last beacon: 36ms ago
                    IE: Unknown: 000B484F4D452D304141462D35
                    IE: Unknown: 01088C129824B048606C
                    IE: Unknown: 030124
                    IE: Unknown: 071E5553202401112801112C011130011195011E99011E9D011EA1011EA5011E
                    IE: Unknown: 200103
                    IE: Unknown: 2D1AEF091BFFFFFF0000000000000000000100000000000000000000
                    IE: Unknown: 3D16240D0400000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F080100000000000040
                    IE: Unknown: BF0CB2018033EAFF0000EAFF0000
                    IE: Unknown: C005012A00FCFF
                    IE: Unknown: C30402DEDEDE
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: Unknown: DD8D0050F204104A0001101044000102103B00010310470010D189AE46CBCA51B48FC275F2ED2A751710210013436973636F2053797374656D732C20496E632E10230007445043333934311024000744504333393431104200093030303030303030311054000800060050F2040001101100074450433339343110080002210C103C0001011049000600372A000120
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 19 - Address: C0:7C:D1:89:EC:31
                    Channel:36
                    Frequency:5.18 GHz (Channel 36)
                    Quality=35/70  Signal level=-75 dBm  
                    Encryption key:off
                    ESSID:"xfinitywifi"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000001593fe14f0
                    Extra: Last beacon: 36ms ago
                    IE: Unknown: 000B7866696E69747977696669
                    IE: Unknown: 01088C129824B048606C
                    IE: Unknown: 030124
                    IE: Unknown: 071E5553202401112801112C011130011195011E99011E9D011EA1011EA5011E
                    IE: Unknown: 200103
                    IE: Unknown: 2D1AEF091BFFFFFF0000000000000000000100000000000000000000
                    IE: Unknown: 3D16240D0400000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F080100000000000040
                    IE: Unknown: BF0CB2018033EAFF0000EAFF0000
                    IE: Unknown: C005012A00FCFF
                    IE: Unknown: C30402DEDEDE
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD0900037F01010000FF7F
          Cell 20 - Address: 54:BE:F7:94:99:E2
                    Channel:40
                    Frequency:5.2 GHz (Channel 40)
                    Quality=39/70  Signal level=-71 dBm  
                    Encryption key:off
                    ESSID:"xfinitywifi"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000100ae687450
                    Extra: Last beacon: 36ms ago
                    IE: Unknown: 000B7866696E69747977696669
                    IE: Unknown: 01088C129824B048606C
                    IE: Unknown: 030128
                    IE: Unknown: 071E5553202401112801112C011130011195011E99011E9D011EA1011EA5011E
                    IE: Unknown: 200103
                    IE: Unknown: 2D1AEF011BFFFFFF0000000000000000000100000000000000000000
                    IE: Unknown: 3D16280F0600000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F080100000000000040
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD0900037F01010000FF7F
          Cell 21 - Address: 54:BE:F7:94:99:E0
                    Channel:40
                    Frequency:5.2 GHz (Channel 40)
                    Quality=38/70  Signal level=-72 dBm  
                    Encryption key:on
                    ESSID:"HOME-7A55-5"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000100ae67a86e
                    Extra: Last beacon: 36ms ago
                    IE: Unknown: 000B484F4D452D374135352D35
                    IE: Unknown: 01088C129824B048606C
                    IE: Unknown: 030128
                    IE: Unknown: 071E5553202401112801112C011130011195011E99011E9D011EA1011EA5011E
                    IE: Unknown: 200103
                    IE: Unknown: 2D1AEF011BFFFFFF0000000000000000000100000000000000000000
                    IE: Unknown: 3D16280F0600000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F080100000000000040
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD8D0050F204104A0001101044000102103B00010310470010B081EC1239E45BCAA1EAF25148539CEA10210013436973636F2053797374656D732C20496E632E10230007445043333933391024000744504333393339104200093030303030303030311054000800060050F2040001101100074450433339333910080002210C103C0001011049000600372A000120
          Cell 22 - Address: 62:45:B1:87:20:65
                    Channel:40
                    Frequency:5.2 GHz (Channel 40)
                    Quality=67/70  Signal level=-43 dBm  
                    Encryption key:on
                    ESSID:""
                    Mode:Master
                    Extra:tsf=0000008d43494490
                    Extra: Last beacon: 8112ms ago
                    IE: Unknown: 0000
                    IE: Unknown: DD100050F211011002242C30008100000000
          Cell 23 - Address: 40:16:7E:5C:03:B4
                    Channel:157
                    Frequency:5.785 GHz
                    Quality=34/70  Signal level=-76 dBm  
                    Encryption key:on
                    ESSID:"JO MAMMA"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000007ea4e2a309
                    Extra: Last beacon: 36ms ago
                    IE: Unknown: 00084A4F204D414D4D41
                    IE: Unknown: 01088C129824B048606C
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 2D1AFF0917FFFFFF0001000000000000000000000000000000000000
                    IE: Unknown: 3D169D0D0400000000000000000000000000000000000000
                    IE: Unknown: 7F080000000000000040
                    IE: Unknown: DD090010180202001C0000
                    IE: Unknown: DD180050F2020101840003A4000027A4000042435E0062322F00

lo        Interface doesn't support scanning.

scott@james:~$ iwconfig
enp2s0    no wireless extensions.

wlp1s0    IEEE 802.11abgn  ESSID:"NETGEAR08-5G"  
          Mode:Managed  Frequency:5.765 GHz  Access Point: 2C:30:33:46:AC:39   
          Bit Rate=150 Mb/s   Tx-Power=30 dBm   
          Retry short limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          Link Quality=70/70  Signal level=-31 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:8   Missed beacon:0

lo        no wireless extensions.

scott@james:~$ dmesg | grep rtl
[   22.146751] Bluetooth: hci0: rtl: examining hci_ver=06 hci_rev=000a lmp_ver=06 lmp_subver=8821
[   22.146755] Bluetooth: hci0: rtl: loading rtl_bt/rtl8821a_fw.bin
[   22.468856] rtl8821ae: Using firmware rtlwifi/rtl8821aefw.bin
[   22.468867] rtl8821ae: Using firmware rtlwifi/rtl8821aefw_wowlan.bin
[   22.741445] ieee80211 phy0: Selected rate control algorithm 'rtl_rc'
[   22.741779] rtlwifi: rtlwifi: wireless switch is on
[   22.743583] rtl8821ae 0000:01:00.0 wlp1s0: renamed from wlan0
scott@james:~$ 

```

---

### Post by chili555 on 2016-05-05
We don't see anything wrong there. I wonder if the result might be different if you ran the dmesg part right after a drop.

There are a number of available parameters for the driver. Let's try one:```
sudo -i
echo "options rtl8821ae swenc=1"  >  /etc/modprobe.d/rtl8821ae.conf
exit
```Reboot and tell us if there is any improvement. If not, after a drop, please show us:```
dmesg | grep -e rtl -e wlp
```Thanks.

---

### Post by SpaceManJack on 2016-05-07
```

scott@james:~$ dmesg | grep -e rtl -e wlp
[   12.632929] Bluetooth: hci0: rtl: examining hci_ver=06 hci_rev=000a lmp_ver=06 lmp_subver=8821
[   12.632934] Bluetooth: hci0: rtl: loading rtl_bt/rtl8821a_fw.bin
[   13.531750] rtl8821ae: Using firmware rtlwifi/rtl8821aefw.bin
[   13.531763] rtl8821ae: Using firmware rtlwifi/rtl8821aefw_wowlan.bin
[   13.636994] ieee80211 phy0: Selected rate control algorithm 'rtl_rc'
[   13.637689] rtlwifi: rtlwifi: wireless switch is on
[   13.640913] rtl8821ae 0000:01:00.0 wlp1s0: renamed from wlan0
[   25.208355] IPv6: ADDRCONF(NETDEV_UP): wlp1s0: link is not ready
[   25.436876] IPv6: ADDRCONF(NETDEV_UP): wlp1s0: link is not ready
[   29.396211] IPv6: ADDRCONF(NETDEV_UP): wlp1s0: link is not ready
[   61.955129] wlp1s0: authenticate with 2c:30:33:46:ac:39
[   62.084552] wlp1s0: send auth to 2c:30:33:46:ac:39 (try 1/3)
[   62.086370] wlp1s0: authenticated
[   62.088110] wlp1s0: associate with 2c:30:33:46:ac:39 (try 1/3)
[   62.090201] wlp1s0: RX AssocResp from 2c:30:33:46:ac:39 (capab=0x1011 status=0 aid=1)
[   62.135345] wlp1s0: associated
[   62.135364] IPv6: ADDRCONF(NETDEV_CHANGE): wlp1s0: link becomes ready
scott@james:~$ dmesg | grep -e rtl -e wlp
[   12.632929] Bluetooth: hci0: rtl: examining hci_ver=06 hci_rev=000a lmp_ver=06 lmp_subver=8821
[   12.632934] Bluetooth: hci0: rtl: loading rtl_bt/rtl8821a_fw.bin
[   13.531750] rtl8821ae: Using firmware rtlwifi/rtl8821aefw.bin
[   13.531763] rtl8821ae: Using firmware rtlwifi/rtl8821aefw_wowlan.bin
[   13.636994] ieee80211 phy0: Selected rate control algorithm 'rtl_rc'
[   13.637689] rtlwifi: rtlwifi: wireless switch is on
[   13.640913] rtl8821ae 0000:01:00.0 wlp1s0: renamed from wlan0
[   25.208355] IPv6: ADDRCONF(NETDEV_UP): wlp1s0: link is not ready
[   25.436876] IPv6: ADDRCONF(NETDEV_UP): wlp1s0: link is not ready
[   29.396211] IPv6: ADDRCONF(NETDEV_UP): wlp1s0: link is not ready
[   61.955129] wlp1s0: authenticate with 2c:30:33:46:ac:39
[   62.084552] wlp1s0: send auth to 2c:30:33:46:ac:39 (try 1/3)
[   62.086370] wlp1s0: authenticated
[   62.088110] wlp1s0: associate with 2c:30:33:46:ac:39 (try 1/3)
[   62.090201] wlp1s0: RX AssocResp from 2c:30:33:46:ac:39 (capab=0x1011 status=0 aid=1)
[   62.135345] wlp1s0: associated
[   62.135364] IPv6: ADDRCONF(NETDEV_CHANGE): wlp1s0: link becomes ready
scott@james:~$ 

```

hey i posted these two results cause they were taken right when it didn't load and then five minutes later, but they were entered in after a web page failed to load.
Thanks for helping me I hope we can get this resolved

---

### Post by chili555 on 2016-05-08
We'll have to dig a bit deeper.```
cat /var/log/syslog | grep -e rtl -e etwork | tail -n20
```Again, taken right after a drop.

We needn't see any "before"; it isn't informative to see that everything went perfectly.

---

### Post by SpaceManJack on 2016-05-14
```

scott@james:~$ cat /var/log/syslog | grep -e rtl -e etwork | tail -n20
scott@james:~$ cat /var/log/syslog | grep -e rtl -e etwork | tail -n20
scott@james:~$ 

```

Ok I had multiple web pages open and they were all taking forever to load and then as soon as the one of them said "problem loading" and "unable to connect" I entered the command in and nothing happened so I entered it in again and still nothing happened. So then I reconnected the ethernet cable and was gonna post my results, then I thought I better try it now just to be sure and I did and hey what do you know it gave me some results, which I shall post below. Ok but you need to know that the first one is the one where the ethernet is plugged in and everything is working fine (still slow with the ethernet but at least the connection doesn't drop in and out) the second and third ones were taken with the wifi and the connection dropped out.

```

scott@james:~$ cat /var/log/syslog | grep -e rtl -e etwork | tail -n20
May 14 14:45:22 james NetworkManager[708]: <info>  [1463262322.9677]   nameserver '75.75.76.76'
May 14 14:45:22 james NetworkManager[708]: <info>  [1463262322.9677]   domain name 'hsd1.or.comcast.net.'
May 14 14:45:22 james NetworkManager[708]: <info>  [1463262322.9677] dhcp4 (enp2s0): state changed unknown -> bound
May 14 14:45:22 james NetworkManager[708]: <info>  [1463262322.9721] device (enp2s0): state change: ip-config -> ip-check (reason 'none') [70 80 0]
May 14 14:45:22 james NetworkManager[708]: <info>  [1463262322.9740] device (enp2s0): state change: ip-check -> secondaries (reason 'none') [80 90 0]
May 14 14:45:22 james NetworkManager[708]: <info>  [1463262322.9748] device (enp2s0): state change: secondaries -> activated (reason 'none') [90 100 0]
May 14 14:45:23 james NetworkManager[708]: <info>  [1463262323.1178] policy: set 'Wired connection 1' (enp2s0) as default for IPv4 routing and DNS
May 14 14:45:23 james NetworkManager[708]: <info>  [1463262323.1182] dns-mgr: Writing DNS information to /sbin/resolvconf
May 14 14:45:23 james NetworkManager[708]: <info>  [1463262323.1317] device (enp2s0): Activation: successful, device activated.
May 14 14:45:23 james systemd[1]: Starting Network Manager Script Dispatcher Service...
May 14 14:45:23 james systemd[1]: Started Network Manager Script Dispatcher Service.
May 14 14:45:24 james NetworkManager[708]: <info>  [1463262324.3635] dhcp6 (enp2s0): activation: beginning transaction (timeout in 45 seconds)
May 14 14:45:24 james NetworkManager[708]: <info>  [1463262324.3663] dhcp6 (enp2s0): dhclient started with pid 3167
May 14 14:45:24 james NetworkManager[708]: <info>  [1463262324.3713] policy: set 'Wired connection 1' (enp2s0) as default for IPv6 routing and DNS
May 14 14:45:24 james NetworkManager[708]: <info>  [1463262324.3718] dns-mgr: Writing DNS information to /sbin/resolvconf
May 14 14:45:24 james NetworkManager[708]: <info>  [1463262324.9972]   nameserver '2001:558:feed::1'
May 14 14:45:24 james NetworkManager[708]: <info>  [1463262324.9972]   nameserver '2001:558:feed::2'
May 14 14:45:24 james NetworkManager[708]: <info>  [1463262324.9973] dhcp6 (enp2s0): state changed unknown -> bound
May 14 14:45:25 james NetworkManager[708]: <info>  [1463262325.0021] dhcp6 (enp2s0): client pid 3167 exited with status 0
May 14 14:45:25 james NetworkManager[708]: <info>  [1463262325.0021] dhcp6 (enp2s0): state changed bound -> done

```

```

scott@james:~$ cat /var/log/syslog | grep -e rtl -e etwork | tail -n20
May 14 14:45:24 james NetworkManager[708]: <info>  [1463262324.3663] dhcp6 (enp2s0): dhclient started with pid 3167
May 14 14:45:24 james NetworkManager[708]: <info>  [1463262324.3713] policy: set 'Wired connection 1' (enp2s0) as default for IPv6 routing and DNS
May 14 14:45:24 james NetworkManager[708]: <info>  [1463262324.3718] dns-mgr: Writing DNS information to /sbin/resolvconf
May 14 14:45:24 james NetworkManager[708]: <info>  [1463262324.9972]   nameserver '2001:558:feed::1'
May 14 14:45:24 james NetworkManager[708]: <info>  [1463262324.9972]   nameserver '2001:558:feed::2'
May 14 14:45:24 james NetworkManager[708]: <info>  [1463262324.9973] dhcp6 (enp2s0): state changed unknown -> bound
May 14 14:45:25 james NetworkManager[708]: <info>  [1463262325.0021] dhcp6 (enp2s0): client pid 3167 exited with status 0
May 14 14:45:25 james NetworkManager[708]: <info>  [1463262325.0021] dhcp6 (enp2s0): state changed bound -> done
May 14 14:51:52 james NetworkManager[708]: <info>  [1463262712.8115] device (enp2s0): link disconnected (deferring action for 4 seconds)
May 14 14:51:57 james NetworkManager[708]: <info>  [1463262717.1722] device (enp2s0): link disconnected (calling deferred action)
May 14 14:51:57 james NetworkManager[708]: <info>  [1463262717.1731] device (enp2s0): state change: activated -> unavailable (reason 'carrier-changed') [100 20 40]
May 14 14:51:57 james NetworkManager[708]: <info>  [1463262717.2062] dhcp4 (enp2s0): canceled DHCP transaction, DHCP client pid 3038
May 14 14:51:57 james NetworkManager[708]: <info>  [1463262717.2062] dhcp4 (enp2s0): state changed bound -> done
May 14 14:51:57 james NetworkManager[708]: <info>  [1463262717.2067] dhcp6 (enp2s0): canceled DHCP transaction
May 14 14:51:57 james NetworkManager[708]: <info>  [1463262717.2100] policy: set 'NETGEAR08-5G 2' (wlp1s0) as default for IPv4 routing and DNS
May 14 14:51:57 james NetworkManager[708]: <info>  [1463262717.2104] dns-mgr: Writing DNS information to /sbin/resolvconf
May 14 14:51:57 james NetworkManager[708]: <info>  [1463262717.2224] policy: set 'NETGEAR08-5G 2' (wlp1s0) as default for IPv6 routing and DNS
May 14 14:51:57 james NetworkManager[708]: <info>  [1463262717.2227] dns-mgr: Writing DNS information to /sbin/resolvconf
May 14 14:51:57 james systemd[1]: Starting Network Manager Script Dispatcher Service...
May 14 14:51:57 james systemd[1]: Started Network Manager Script Dispatcher Service.
scott@james:~$ cat /var/log/syslog | grep -e rtl -e etwork | tail -n20
May 14 14:45:24 james NetworkManager[708]: <info>  [1463262324.3663] dhcp6 (enp2s0): dhclient started with pid 3167
May 14 14:45:24 james NetworkManager[708]: <info>  [1463262324.3713] policy: set 'Wired connection 1' (enp2s0) as default for IPv6 routing and DNS
May 14 14:45:24 james NetworkManager[708]: <info>  [1463262324.3718] dns-mgr: Writing DNS information to /sbin/resolvconf
May 14 14:45:24 james NetworkManager[708]: <info>  [1463262324.9972]   nameserver '2001:558:feed::1'
May 14 14:45:24 james NetworkManager[708]: <info>  [1463262324.9972]   nameserver '2001:558:feed::2'
May 14 14:45:24 james NetworkManager[708]: <info>  [1463262324.9973] dhcp6 (enp2s0): state changed unknown -> bound
May 14 14:45:25 james NetworkManager[708]: <info>  [1463262325.0021] dhcp6 (enp2s0): client pid 3167 exited with status 0
May 14 14:45:25 james NetworkManager[708]: <info>  [1463262325.0021] dhcp6 (enp2s0): state changed bound -> done
May 14 14:51:52 james NetworkManager[708]: <info>  [1463262712.8115] device (enp2s0): link disconnected (deferring action for 4 seconds)
May 14 14:51:57 james NetworkManager[708]: <info>  [1463262717.1722] device (enp2s0): link disconnected (calling deferred action)
May 14 14:51:57 james NetworkManager[708]: <info>  [1463262717.1731] device (enp2s0): state change: activated -> unavailable (reason 'carrier-changed') [100 20 40]
May 14 14:51:57 james NetworkManager[708]: <info>  [1463262717.2062] dhcp4 (enp2s0): canceled DHCP transaction, DHCP client pid 3038
May 14 14:51:57 james NetworkManager[708]: <info>  [1463262717.2062] dhcp4 (enp2s0): state changed bound -> done
May 14 14:51:57 james NetworkManager[708]: <info>  [1463262717.2067] dhcp6 (enp2s0): canceled DHCP transaction
May 14 14:51:57 james NetworkManager[708]: <info>  [1463262717.2100] policy: set 'NETGEAR08-5G 2' (wlp1s0) as default for IPv4 routing and DNS
May 14 14:51:57 james NetworkManager[708]: <info>  [1463262717.2104] dns-mgr: Writing DNS information to /sbin/resolvconf
May 14 14:51:57 james NetworkManager[708]: <info>  [1463262717.2224] policy: set 'NETGEAR08-5G 2' (wlp1s0) as default for IPv6 routing and DNS
May 14 14:51:57 james NetworkManager[708]: <info>  [1463262717.2227] dns-mgr: Writing DNS information to /sbin/resolvconf
May 14 14:51:57 james systemd[1]: Starting Network Manager Script Dispatcher Service...
May 14 14:51:57 james systemd[1]: Started Network Manager Script Dispatcher Service.

```

thanks for trying to help but at this point I doubt we'll be able to get this solved, I'm starting to despair to be honest

> **chili555 said:**
> We don't see anything wrong there. I wonder if the result might be different if you ran the dmesg part right after a drop.

There are a number of available parameters for the driver. Let's try one:```
sudo -i
echo "options rtl8821ae swenc=1"  >  /etc/modprobe.d/rtl8821ae.conf
exit
```Reboot and tell us if there is any improvement. If not, after a drop, please show us:```
dmesg | grep -e rtl -e wlp
```Thanks.

Listen I forgot to show you the results of the above parameters you told me to try, I want you to show you the results cause it looks like to me nothing happened at all when I entered the commands in so here they are exactly as seen in my terminal, so basically does this look right to you? Did the parameters go into effect or is something wrong?

```

scott@james:~$ sudo -i
[sudo] password for scott: 
root@james:~# echo "options rtl8821ae swenc=1"  >  /etc/modprobe.d/rtl8821ae.conf
root@james:~# exit
logout
scott@james:~$ 

```

---

### Post by chili555 on 2016-05-15
> Did the parameters go into effect or is something wrong?The parameters go into effect when you either reboot or unload and reload the driver:```
sudo modprobe -r rtl8821ae
sudo modprobe rtl8821ae
```Did you try a reboot? Any change? Better or worse?

---

### Post by SpaceManJack on 2016-05-17
ok listen I'm a total noob so bare with me here, what is 
sudo modprobe -r rtl8821ae
sudo modprobe rtl8821ae??????

Are these new parameters you want me to enter in? And explain how I enter them in, aren't I supposed to enter them in like this for example?
```

sudo -i
sudo modprobe -r rtl8821ae
sudo modprobe rtl8821ae

```

And I posted the results of  "cat /var/log/syslog | grep -e rtl -e etwork | tail -n20"
did you see them? just wanna be sure

could someone please help me get this matter resolved? I cant believe its being this hard just to get Linux up and running on my fricking laptop!

---

### Post by santhony on 2016-05-20
I'm having the same issue too, same wireless NIC..

---

### Post by SpaceManJack on 2016-05-22
could someone answer my question above about parameters?

---

### Post by chili555 on 2016-05-24
> **scott130 said:**
> ok listen I'm a total noob so bare with me here, what is 
sudo modprobe -r rtl8821ae
sudo modprobe rtl8821ae??????

Are these new parameters you want me to enter in? And explain how I enter them in, aren't I supposed to enter them in like this for example?
```

sudo -i
sudo modprobe -r rtl8821ae
sudo modprobe rtl8821ae

```

And I posted the results of  "cat /var/log/syslog | grep -e rtl -e etwork | tail -n20"
did you see them? just wanna be sureYou are supposed to enter the commands in the terminal just as I posted them; there is nothing to add or modify on your end. If there was a need for 'sudo -i' I would have posted it that way.

The command:```
sudo modprobe -r rtl8821ae
```...removes (-r) a currently loaded module from the running system. In this case, it is the driver for your wireless, rtl8821ae. We removed it because we want to add it back in again, but this time, the configuration file you created here will be read and used:> There are a number of available parameters for the driver. Let's try one:

```
sudo -i
echo "options rtl8821ae swenc=1"  >  /etc/modprobe.d/rtl8821ae.conf
exit
```

Reboot and tell us if there is any improvement. This command loads it back in with the new parameter:```
sudo modprobe rtl8821ae
```Notice that there is no -r for remove modifier. 

If you have rebooted the computer in the several days I've been away, it is already done.

So, did you do so? Is there any improvement?

---

### Post by simonn on 2016-05-27
> **scott130 said:**
> could someone answer my question above about parameters?

Hey scott130, just ignore this whole thread and see my post:

[http://ubuntuforums.org/showthread.php?t=1543006&page=42&p=13493037#post13493037](http://ubuntuforums.org/showthread.php?t=1543006&page=42&p=13493037#post13493037)

"802.11AC wireless (rtl8821ae) fails (this has happened every kernel upgrade)."

"Wifi fails after suspend/sleep."

---

