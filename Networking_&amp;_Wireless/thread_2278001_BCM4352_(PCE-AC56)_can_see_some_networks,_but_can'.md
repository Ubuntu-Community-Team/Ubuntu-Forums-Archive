---
title: "BCM4352 (PCE-AC56) can see some networks, but can't connect"
date: 2015-05-13
forum: Networking &amp; Wireless
---

### Post by jeff-artik on 2015-05-13
Emergency ! Maybe I still need a doctor. After having issue (solved) with my previous BCM4331 chipset, I bought another computer. What a good idea I had to buy lastest hardware, and in my case a brand new PCE-AC56. I plug it, it can see some netwoks around me (not mine obviously), and can't connect to any of them. Here is some helpfull command lines :

lsusb
```
Bus 004 Device 002: ID 8087:8001 Intel Corp. Bus 004 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 002: ID 8087:8009 Intel Corp. 
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 003: ID 0451:8025 Texas Instruments, Inc. 
Bus 002 Device 002: ID 0451:8140 Texas Instruments, Inc. 
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 011: ID 0451:ca01 Texas Instruments, Inc. 
Bus 001 Device 009: ID 0451:8027 Texas Instruments, Inc. 
Bus 001 Device 008: ID 093a:2510 Pixart Imaging, Inc. Optical Mouse
Bus 001 Device 010: ID 05ac:0250 Apple, Inc. Aluminium Keyboard (ISO)
Bus 001 Device 007: ID 05ac:1006 Apple, Inc. Hub in Aluminum Keyboard
Bus 001 Device 005: ID 0451:8142 Texas Instruments, Inc. 
Bus 001 Device 003: ID 2833:0201  
Bus 001 Device 004: ID 2833:0021  
Bus 001 Device 002: ID 2833:2021  
Bus 001 Device 006: ID 056a:00b5 Wacom Co., Ltd Intuos3 6x11 (PTZ-631W)
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

lspci
```
00:00.0 Host bridge: Intel Corporation 4th Gen Core Processor DRAM Controller (rev 06)00:01.0 PCI bridge: Intel Corporation Xeon E3-1200 v3/4th Gen Core Processor PCI Express x16 Controller (rev 06)
00:01.1 PCI bridge: Intel Corporation Xeon E3-1200 v3/4th Gen Core Processor PCI Express x8 Controller (rev 06)
00:14.0 USB controller: Intel Corporation Device 8cb1
00:16.0 Communication controller: Intel Corporation Device 8cba
00:19.0 Ethernet controller: Intel Corporation Ethernet Connection (2) I218-V
00:1a.0 USB controller: Intel Corporation Device 8cad
00:1b.0 Audio device: Intel Corporation Device 8ca0
00:1c.0 PCI bridge: Intel Corporation Device 8c90 (rev d0)
00:1c.3 PCI bridge: Intel Corporation Device 8c96 (rev d0)
00:1c.5 PCI bridge: Intel Corporation Device 8c9a (rev d0)
00:1d.0 USB controller: Intel Corporation Device 8ca6
00:1f.0 ISA bridge: Intel Corporation Device 8cc4
00:1f.3 SMBus: Intel Corporation Device 8ca2
01:00.0 VGA compatible controller: NVIDIA Corporation Device 13c2 (rev a1)
01:00.1 Audio device: NVIDIA Corporation Device 0fbb (rev a1)
02:00.0 VGA compatible controller: NVIDIA Corporation Device 13c2 (rev a1)
02:00.1 Audio device: NVIDIA Corporation Device 0fbb (rev a1)
04:00.0 SATA controller: ASMedia Technology Inc. ASM1062 Serial ATA Controller (rev 02)
05:00.0 Network controller: Broadcom Corporation BCM4352 802.11ac Wireless Network Adapter (rev 03)

``` 

lspci -nn | grep -i net
```
00:19.0 Ethernet controller [0200]: Intel Corporation Ethernet Connection (2) I218-V [8086:15a1]05:00.0 Network controller [0280]: Broadcom Corporation BCM4352 802.11ac Wireless Network Adapter [14e4:43b1] (rev 03)

```

sudo lshw -C network
```
  *-network                      description: Ethernet interface
       product: Ethernet Connection (2) I218-V
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       logical name: eth0
       version: 00
       serial: 78:24:af:c0:5f:2d
       size: 1Gbit/s
       capacity: 1Gbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=2.3.2-k duplex=full firmware=0.1-4 ip=192.168.0.105 latency=0 link=yes multicast=yes port=twisted pair speed=1Gbit/s
       resources: irq:28 memory:f5100000-f511ffff memory:f5137000-f5137fff ioport:f020(size=32)
  *-network
       description: Wireless interface
       product: BCM4352 802.11ac Wireless Network Adapter
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: wlan0
       version: 03
       serial: ac:22:0b:d6:b2:c5
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=6.30.223.248 (r487574) latency=0 multicast=yes wireless=IEEE 802.11abg
       resources: irq:17 memory:f7400000-f7407fff memory:f7200000-f73fffff

```

iwconfig
```
eth0      no wireless extensions.

wlan0     IEEE 802.11abg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
lo        no wireless extensions.


lxcbr0    no wireless extensions.

```

ifconfig
```
eth0      Link encap:Ethernet  HWaddr 78:24:af:c0:5f:2d            inet addr:192.168.0.105  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::7a24:afff:fec0:5f2d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:70517 errors:0 dropped:0 overruns:0 frame:0
          TX packets:35124 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:76358802 (76.3 MB)  TX bytes:4250427 (4.2 MB)
          Interrupt:20 Memory:f5100000-f5120000 


lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:2518 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2518 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:914340 (914.3 KB)  TX bytes:914340 (914.3 KB)


lxcbr0    Link encap:Ethernet  HWaddr ee:a1:12:c7:aa:f4  
          inet addr:10.0.3.1  Bcast:10.0.3.255  Mask:255.255.255.0
          inet6 addr: fe80::eca1:12ff:fec7:aaf4/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:155 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:24709 (24.7 KB)


wlan0     Link encap:Ethernet  HWaddr ac:22:0b:d6:b2:c5  
          inet6 addr: fe80::ae22:bff:fed6:b2c5/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:17 

```

uname -r -m
```
3.18.13-031813-generic x86_64
```

nm-tool
```
NetworkManager Tool

State: connected (global)


- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            wl
  State:             disconnected
  Default:           no
  HW Address:        AC:22:0B:D6:B2:C5


  Capabilities:


  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes


  Wireless Access Points 
    dlink_wifi:      Infra, E8:DE:27:DD:D9:AB, Freq 2417 MHz, Rate 54 Mb/s, Strength 79 WPA WPA2
    MOVISTAR_44DF:   Infra, D8:61:94:64:44:DF, Freq 2417 MHz, Rate 54 Mb/s, Strength 70 WPA
    BBM:             Infra, F8:8E:85:FA:0B:83, Freq 2462 MHz, Rate 54 Mb/s, Strength 57 WPA




- Device: eth0  [Wired connection 1] -------------------------------------------
  Type:              Wired
  Driver:            e1000e
  State:             connected
  Default:           yes
  HW Address:        78:24:AF:C0:5F:2D


  Capabilities:
    Carrier Detect:  yes
    Speed:           1000 Mb/s


  Wired Properties
    Carrier:         on


  IPv4 Settings:
    Address:         192.168.0.105
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.0.254


    DNS:             80.58.61.250
    DNS:             80.58.61.254

```

sudo rfkill list
```
0: phy0: Wireless LAN    Soft blocked: no
    Hard blocked: no
1: brcmwl-0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

```

sudo dpkg -s bcmwl-kernel-source | grep Version
```
Version: 6.30.223.248+bdcom-0ubuntu0.1
```

sudo iwlist wlan0 scan
```
wlan0     Scan completed :          Cell 01 - Address: E8:DE:27:DD:D9:AB
                    Channel:2
                    Frequency:2.417 GHz (Channel 2)
                    Quality=54/70  Signal level=-56 dBm  
                    Encryption key:on
                    ESSID:"dlink_wifi"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 96ms ago
                    IE: Unknown: 000A646C696E6B5F77696669
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030102
                    IE: Unknown: 2A0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32043048606C
                    IE: Unknown: 2D1AEF1103FFFF0000000000000000000000000000000406E6E70D00
                    IE: Unknown: 331AEF1103FFFF0000000000000000000000000000000406E6E70D00
                    IE: Unknown: 3D1602051500000000000000000000000000000000000000
                    IE: Unknown: 341602051500000000000000000000000000000000000000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101040003A4000027A4000042435E0062322F00
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: Unknown: DD970050F204104A0001101044000102103B0001031047001000000000000010000000E8DE27DDD9AB1021000754502D4C494E4B10230009544C2D57413830314E10240003322E3010420003312E301054000800060050F204000110110017576972656C657373204E20415020544C2D57413830314E100800020086103C000101104900140024E26002000101600000020001600100020001
          Cell 02 - Address: D8:61:94:64:44:DF
                    Channel:2
                    Frequency:2.417 GHz (Channel 2)
                    Quality=52/70  Signal level=-58 dBm  
                    Encryption key:on
                    ESSID:"MOVISTAR_44DF"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 96ms ago
                    IE: Unknown: 000D4D4F5649535441525F34344446
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030102
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: 2D1A2C181EFF00000000000000000000000000000000000000000000
                    IE: Unknown: 3D1602000000000000000000000000000000000000000000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C332C181EFF00000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C3402000000000000000000000000000000000000000000
                    IE: Unknown: DD0600E04C020160
                    IE: Unknown: DDA50050F204104A0001101044000102103B0001031047001063041253101920061228D861946444DF1021001B5265616C74656B2053656D69636F6E647563746F7220436F72702E1023000752544C383637311024000D45562D323030362D30372D32371042000F3132333435363738393031323334371054000800060050F2040001101100104144534C20536F486F20526F757465721008000200061049000600372A000120

```

I tried the b43, but it's the same.
I also tried the driver 6.30.223.248+bdcom-0ubuntu2 that Chili gave me : [http://packages.ubuntu.com/vivid/bcmwl-kernel-source](http://packages.ubuntu.com/vivid/bcmwl-kernel-source) but no luck this time.

I hear that compiling the driver can works (I got an error at the compilation).

I bit of help could be great to make this great hardware working.

---

