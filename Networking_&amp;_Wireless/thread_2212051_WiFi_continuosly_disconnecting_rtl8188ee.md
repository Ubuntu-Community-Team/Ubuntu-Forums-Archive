---
title: "WiFi continuosly disconnecting rtl8188ee"
date: 2014-03-19
forum: Networking &amp; Wireless
---

### Post by PsykoMantis on 2014-03-19
**Problem**

When i'm at home, all perfect all works.
 Every time i go at university my wireless connection works for about 4 minutes, after those 4 minutes it says that i'm connected but i cant ping or surf with firefox, basically i loose the connection but it says that i'm connected, and then it try to connect and continuosly ask me the credentials....and stays in the "connecting..." state for ever, opening new windows every time for credentials. (so i think it fails the connection). I have to shut down the network service and restart it, and it works for an onther 4 minutes then same.

So there is a problem here. 

Here all those commands runned when my system is continuosly trying to connect to the wifi.....

uname-a
```
Linux psychoHack 3.8.0-33-generic #48~precise1-Ubuntu SMP Thu Oct 24 16:28:06 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux
```

nm-tool
```

NetworkManager Tool

State: connecting

- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            r8101
  State:             unavailable
  Default:           no
  HW Address:        A0:48:1C:12:AE:93

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off


- Device: wlan0  [ced] ---------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            rtl8188ee
  State:             connecting (configuring)
  Default:           no
  HW Address:        70:18:8B:1D:8C:9D

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 
    Unive_WiFi-Tesisti: Infra, 00:13:60:EF:73:C0, Freq 2412 MHz, Rate 54 Mb/s, Strength 79
    VeniceConnected: Infra, 00:13:60:EF:73:C1, Freq 2412 MHz, Rate 54 Mb/s, Strength 0
    VeniceConnected: Infra, 00:17:59:FB:BB:D1, Freq 2437 MHz, Rate 54 Mb/s, Strength 0
    VeniceConnected: Infra, 70:81:05:45:6B:81, Freq 2462 MHz, Rate 54 Mb/s, Strength 45
    eduroam:         Infra, 00:07:7D:D3:3C:42, Freq 2462 MHz, Rate 54 Mb/s, Strength 54 WPA WPA2 Enterprise
    Unive_WiFi-Laboratorio5-1: Infra, 70:81:05:45:6B:80, Freq 2462 MHz, Rate 54 Mb/s, Strength 85
    Unive_WiFi-Aula1:Infra, 00:07:7D:D3:3C:40, Freq 2462 MHz, Rate 54 Mb/s, Strength 74
    VeniceConnected: Infra, 00:07:7D:D3:3C:41, Freq 2462 MHz, Rate 54 Mb/s, Strength 62
    eduroam:         Infra, 00:13:60:EF:73:C2, Freq 2412 MHz, Rate 54 Mb/s, Strength 56 WPA WPA2 Enterprise
    eduroam:         Infra, 00:17:59:FB:BB:D2, Freq 2437 MHz, Rate 54 Mb/s, Strength 77 WPA WPA2 Enterprise
    eduroam:         Infra, 70:81:05:45:6B:82, Freq 2462 MHz, Rate 54 Mb/s, Strength 68 WPA WPA2 Enterprise
    Unive_WiFi-Laboratorio5: Infra, 00:17:59:FB:BB:D0, Freq 2437 MHz, Rate 54 Mb/s, Strength 0
    ced:             Infra, 00:23:69:3A:56:E8, Freq 2412 MHz, Rate 54 Mb/s, Strength 100 WPA WPA2


```

lspci | grep network
```
07:00.0 Network controller: Realtek Semiconductor Co., Ltd. Device 8179 (rev 01)
```

wilist scan
```
wlan0     Scan completed :
          Cell 01 - Address: 70:81:05:45:6B:80
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=41/70  Signal level=-69 dBm  
                    Encryption key:off
                    ESSID:"Unive_WiFi-Laboratorio5-1"
                    Bit Rates:12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s; 48 Mb/s
                              54 Mb/s
                    Mode:Master
                    Extra:tsf=000000b000d2e316
                    Extra: Last beacon: 29228ms ago
                    IE: Unknown: 0019556E6976655F576946692D4C61626F7261746F72696F352D31
                    IE: Unknown: 010698243048606C
                    IE: Unknown: 03010B
                    IE: Unknown: 0706495449010D17
                    IE: Unknown: 2A0100
                    IE: Unknown: 851E0B0090000F00FF031900313235322D544F522D4C61626F72610009000032
                    IE: Unknown: 9606004096001100
                    IE: Unknown: DD06004096010102
                    IE: Unknown: DD050040960305
                    IE: Unknown: DD050040960B09
                    IE: Unknown: DD050040961400
                    IE: Unknown: DD180050F2020101820003A4000027A400004243BC0062326600
          Cell 02 - Address: 00:23:69:3A:56:E8
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=70/70  Signal level=-18 dBm  
                    Encryption key:on
                    ESSID:"ced"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000077dc5acf5d
                    Extra: Last beacon: 29916ms ago
                    IE: Unknown: 0003636564
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030101
                    IE: Unknown: 2A0104
                    IE: Unknown: 2F0104
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD7E0050F204104A0001101044000102103B00010310470010138140001DD211B29FFFC67E816B4BFB102100074C696E6B73797310230006526F7574657210240007575254353447321042000C43535630314A3136333237391054000800060050F204000110110011576972656C6573732D4720526F75746572100800020088
                    IE: Unknown: DD090010180202F4000000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: 00:17:59:FB:BB:D1
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=41/70  Signal level=-69 dBm  
                    Encryption key:off
                    ESSID:"VeniceConnected"
                    Bit Rates:12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s; 48 Mb/s
                              54 Mb/s
                    Mode:Master
                    Extra:tsf=0000011517d181b3
                    Extra: Last beacon: 29228ms ago
                    IE: Unknown: 000F56656E696365436F6E6E6563746564
                    IE: Unknown: 010698243048606C
                    IE: Unknown: 030106
                    IE: Unknown: 0706495449010D11
                    IE: Unknown: 2A0100
                    IE: Unknown: 851E000084000F00FF031900313233312D544F522D4C61626F72610004000025
                    IE: Unknown: DD06004096010102
                    IE: Unknown: DD050040960304
                    IE: Unknown: DD1600409604000207A4000023A400004243000062320000
                    IE: Unknown: DD050040960B01
                    IE: Unknown: DD180050F2020101820003A4000027A4000042435E0062322F00
          Cell 04 - Address: 00:17:59:FB:BB:D0
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=40/70  Signal level=-70 dBm  
                    Encryption key:off
                    ESSID:"Unive_WiFi-Laboratorio5"
                    Bit Rates:12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s; 48 Mb/s
                              54 Mb/s
                    Mode:Master
                    Extra:tsf=0000011517d28c8c
                    Extra: Last beacon: 29228ms ago
                    IE: Unknown: 0017556E6976655F576946692D4C61626F7261746F72696F35
                    IE: Unknown: 010698243048606C
                    IE: Unknown: 030106
                    IE: Unknown: 0706495449010D11
                    IE: Unknown: 2A0100
                    IE: Unknown: 851E000084000F00FF031900313233312D544F522D4C61626F72610004000025
                    IE: Unknown: DD06004096010102
                    IE: Unknown: DD050040960304
                    IE: Unknown: DD1600409604000207A4000023A400004243000062320000
                    IE: Unknown: DD050040960B01
                    IE: Unknown: DD180050F2020101820003A4000027A4000042435E0062322F00
          Cell 05 - Address: 00:17:59:FB:BB:D2
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=53/70  Signal level=-57 dBm  
                    Encryption key:on
                    ESSID:"eduroam"
                    Bit Rates:12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s; 48 Mb/s
                              54 Mb/s
                    Mode:Master
                    Extra:tsf=0000011517d07696
                    Extra: Last beacon: 29228ms ago
                    IE: Unknown: 0007656475726F616D
                    IE: Unknown: 010698243048606C
                    IE: Unknown: 030106
                    IE: Unknown: 0706495449010D11
                    IE: Unknown: 2A0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
                    IE: Unknown: 851E000084000F00FF031900313233312D544F522D4C61626F72610004000025
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : 802.1x
                    IE: Unknown: DD06004096010102
                    IE: Unknown: DD050040960304
                    IE: Unknown: DD1600409604000207A4000023A400004243000062320000
                    IE: Unknown: DD050040960B01
                    IE: Unknown: DD180050F2020101820003A4000027A4000042435E0062322F00
          Cell 06 - Address: 00:07:7D:D3:3C:41
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=42/70  Signal level=-68 dBm  
                    Encryption key:off
                    ESSID:"VeniceConnected"
                    Bit Rates:12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s; 48 Mb/s
                              54 Mb/s
                    Mode:Master
                    Extra:tsf=000000b001064824
                    Extra: Last beacon: 29404ms ago
                    IE: Unknown: 000F56656E696365436F6E6E6563746564
                    IE: Unknown: 010698243048606C
                    IE: Unknown: 03010B
                    IE: Unknown: 050401020000
                    IE: Unknown: 0706495449010D17
                    IE: Unknown: 2A0100
                    IE: Unknown: 851E000090000F00FF031900313235322D544F522D41756C6131000001000032
                    IE: Unknown: 9606004096001100
                    IE: Unknown: DD06004096010102
                    IE: Unknown: DD050040960305
                    IE: Unknown: DD050040960B09
                    IE: Unknown: DD050040961400
                    IE: Unknown: DD180050F2020101820003A4000027A400004243BC0062326600
          Cell 07 - Address: 70:81:05:45:6B:82
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=40/70  Signal level=-70 dBm  
                    Encryption key:on
                    ESSID:"eduroam"
                    Bit Rates:12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s; 48 Mb/s
                              54 Mb/s
                    Mode:Master
                    Extra:tsf=000000b000d41d75
                    Extra: Last beacon: 29228ms ago
                    IE: Unknown: 0007656475726F616D
                    IE: Unknown: 010698243048606C
                    IE: Unknown: 03010B
                    IE: Unknown: 0706495449010D17
                    IE: Unknown: 2A0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
                    IE: Unknown: 851E0B0090000F00FF031900313235322D544F522D4C61626F72610009000032
                    IE: Unknown: 9606004096001100
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : 802.1x
                    IE: Unknown: DD06004096010102
                    IE: Unknown: DD050040960305
                    IE: Unknown: DD050040960B09
                    IE: Unknown: DD050040961401
                    IE: Unknown: DD180050F2020101820003A4000027A400004243BC0062326600
          Cell 08 - Address: 70:81:05:45:6B:81
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=40/70  Signal level=-70 dBm  
                    Encryption key:off
                    ESSID:"VeniceConnected"
                    Bit Rates:12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s; 48 Mb/s
                              54 Mb/s
                    Mode:Master
                    Extra:tsf=000000b000d3bf26
                    Extra: Last beacon: 29228ms ago
                    IE: Unknown: 000F56656E696365436F6E6E6563746564
                    IE: Unknown: 010698243048606C
                    IE: Unknown: 03010B
                    IE: Unknown: 0706495449010D17
                    IE: Unknown: 2A0100
                    IE: Unknown: 851E0B0090000F00FF031900313235322D544F522D4C61626F72610009000032
                    IE: Unknown: 9606004096001100
                    IE: Unknown: DD06004096010102
                    IE: Unknown: DD050040960305
                    IE: Unknown: DD050040960B09
                    IE: Unknown: DD050040961400
                    IE: Unknown: DD180050F2020101820003A4000027A400004243BC0062326600

```

iwconfig
```
wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off

```


lshw -C network
```
*-network
       description: Wireless interface
       product: Realtek Semiconductor Co., Ltd.
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:07:00.0
       logical name: wlan0
       version: 01
       serial: 70:18:8b:1d:8c:9d
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rtl8188ee driverversion=3.8.0-33-generic firmware=N/A latency=0 link=no multicast=yes wireless=IEEE 802.11bgn
       resources: irq:16 ioport:4000(size=256) memory:c3500000-c3503fff
  *-network
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:08:00.0
       logical name: eth0
       version: 07
       serial: a0:48:1c:12:ae:93
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8101 driverversion=1.024.00-NAPI duplex=half latency=0 link=no multicast=yes port=twisted pair
       resources: irq:43 ioport:3000(size=256) memory:c3404000-c3404fff memory:c3400000-c3403fff memory:9fb00000-9fb0ffff
```

dmesg -l

```
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 3.8.0-33-generic (buildd@toyol) (gcc version 4.6.3 (Ubuntu/Linaro 4.6.3-1ubuntu5) ) #48~precise1-Ubuntu SMP Thu Oct 24 16:28:06 UTC 2013 (Ubuntu 3.8.0-33.48~precise1-generic 3.8.13.11)
[    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-3.8.0-33-generic.efi.signed root=UUID=66a4c22f-60ec-4202-a91d-b15f2b67db2a ro quiet splash vt.handoff=7
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   Centaur CentaurHauls
[    0.000000] e820: BIOS-provided physical RAM map:
[    0.000000] BIOS-e820: [mem 0x0000000000000000-0x0000000000087fff] usable
[    0.000000] BIOS-e820: [mem 0x0000000000088000-0x00000000000bffff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000000100000-0x000000001fffffff] usable
[    0.000000] BIOS-e820: [mem 0x0000000020000000-0x00000000201fffff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000020200000-0x0000000040003fff] usable
[    0.000000] BIOS-e820: [mem 0x0000000040004000-0x0000000040004fff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000040005000-0x000000009a0befff] usable
[    0.000000] BIOS-e820: [mem 0x000000009a0bf000-0x000000009aebefff] reserved
[    0.000000] BIOS-e820: [mem 0x000000009aebf000-0x000000009afbefff] ACPI NVS
[    0.000000] BIOS-e820: [mem 0x000000009afbf000-0x000000009affefff] ACPI data
[    0.000000] BIOS-e820: [mem 0x000000009afff000-0x000000009affffff] usable
[    0.000000] BIOS-e820: [mem 0x000000009b000000-0x000000009f9fffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000e0000000-0x00000000efffffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000feb00000-0x00000000feb03fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fec00000-0x00000000fec00fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fed10000-0x00000000fed19fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fed1c000-0x00000000fed1ffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fee00000-0x00000000fee00fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000ffd80000-0x00000000ffffffff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000100000000-0x000000025f5fffff] usable
[    0.000000] NX (Execute Disable) protection: active
[    0.000000] efi: EFI v2.31 by INSYDE Corp.
[    0.000000] efi:  ACPI=0x9affe000  ACPI 2.0=0x9affe014  SMBIOS=0x9aebef98 
[    0.000000] efi: mem00: type=3, attr=0xf, range=[0x0000000000000000-0x0000000000001000) (0MB)
[    0.000000] efi: mem01: type=7, attr=0xf, range=[0x0000000000001000-0x000000000006f000) (0MB)
[    0.000000] efi: mem02: type=4, attr=0xf, range=[0x000000000006f000-0x0000000000070000) (0MB)
[    0.000000] efi: mem03: type=7, attr=0xf, range=[0x0000000000070000-0x0000000000088000) (0MB)
[    0.000000] efi: mem04: type=6, attr=0x800000000000000f, range=[0x0000000000088000-0x00000000000a0000) (0MB)
[    0.000000] efi: mem05: type=2, attr=0xf, range=[0x0000000000100000-0x0000000000629000) (5MB)
[    0.000000] efi: mem06: type=7, attr=0xf, range=[0x0000000000629000-0x0000000020000000) (505MB)
[    0.000000] efi: mem07: type=0, attr=0xf, range=[0x0000000020000000-0x0000000020200000) (2MB)
[    0.000000] efi: mem08: type=7, attr=0xf, range=[0x0000000020200000-0x0000000036140000) (351MB)
[    0.000000] efi: mem09: type=2, attr=0xf, range=[0x0000000036140000-0x0000000036142000) (0MB)
[    0.000000] efi: mem10: type=7, attr=0xf, range=[0x0000000036142000-0x0000000036144000) (0MB)
[    0.000000] efi: mem11: type=2, attr=0xf, range=[0x0000000036144000-0x000000003709a000) (15MB)
[    0.000000] efi: mem12: type=7, attr=0xf, range=[0x000000003709a000-0x0000000040004000) (143MB)
[    0.000000] efi: mem13: type=0, attr=0xf, range=[0x0000000040004000-0x0000000040005000) (0MB)
[    0.000000] efi: mem14: type=7, attr=0xf, range=[0x0000000040005000-0x0000000068b55000) (651MB)
[    0.000000] efi: mem15: type=2, attr=0xf, range=[0x0000000068b55000-0x000000008e6c0000) (603MB)
[    0.000000] efi: mem16: type=4, attr=0xf, range=[0x000000008e6c0000-0x000000008e6e0000) (0MB)
[    0.000000] efi: mem17: type=7, attr=0xf, range=[0x000000008e6e0000-0x0000000090da1000) (38MB)
[    0.000000] efi: mem18: type=2, attr=0xf, range=[0x0000000090da1000-0x0000000090f24000) (1MB)
[    0.000000] efi: mem19: type=4, attr=0xf, range=[0x0000000090f24000-0x00000000916b0000) (7MB)
[    0.000000] efi: mem20: type=7, attr=0xf, range=[0x00000000916b0000-0x00000000916bd000) (0MB)
[    0.000000] efi: mem21: type=2, attr=0xf, range=[0x00000000916bd000-0x00000000916bf000) (0MB)
[    0.000000] efi: mem22: type=7, attr=0xf, range=[0x00000000916bf000-0x000000009178b000) (0MB)
[    0.000000] efi: mem23: type=1, attr=0xf, range=[0x000000009178b000-0x00000000918bf000) (1MB)
[    0.000000] efi: mem24: type=7, attr=0xf, range=[0x00000000918bf000-0x00000000973ed000) (91MB)
[    0.000000] efi: mem25: type=4, attr=0xf, range=[0x00000000973ed000-0x0000000097c6f000) (8MB)
[    0.000000] efi: mem26: type=7, attr=0xf, range=[0x0000000097c6f000-0x0000000097f25000) (2MB)
[    0.000000] efi: mem27: type=4, attr=0xf, range=[0x0000000097f25000-0x0000000097fc5000) (0MB)
[    0.000000] efi: mem28: type=7, attr=0xf, range=[0x0000000097fc5000-0x0000000097fc6000) (0MB)
[    0.000000] efi: mem29: type=4, attr=0xf, range=[0x0000000097fc6000-0x0000000097fd8000) (0MB)
[    0.000000] efi: mem30: type=7, attr=0xf, range=[0x0000000097fd8000-0x0000000097fda000) (0MB)
[    0.000000] efi: mem31: type=4, attr=0xf, range=[0x0000000097fda000-0x0000000098008000) (0MB)
[    0.000000] efi: mem32: type=7, attr=0xf, range=[0x0000000098008000-0x0000000098009000) (0MB)
[    0.000000] efi: mem33: type=4, attr=0xf, range=[0x0000000098009000-0x0000000098011000) (0MB)
[    0.000000] efi: mem34: type=7, attr=0xf, range=[0x0000000098011000-0x0000000098018000) (0MB)
[    0.000000] efi: mem35: type=4, attr=0xf, range=[0x0000000098018000-0x0000000098021000) (0MB)
[    0.000000] efi: mem36: type=7, attr=0xf, range=[0x0000000098021000-0x0000000098022000) (0MB)
[    0.000000] efi: mem37: type=4, attr=0xf, range=[0x0000000098022000-0x000000009804c000) (0MB)
[    0.000000] efi: mem38: type=7, attr=0xf, range=[0x000000009804c000-0x000000009804e000) (0MB)
[    0.000000] efi: mem39: type=4, attr=0xf, range=[0x000000009804e000-0x0000000098196000) (1MB)
[    0.000000] efi: mem40: type=7, attr=0xf, range=[0x0000000098196000-0x0000000098198000) (0MB)
[    0.000000] efi: mem41: type=4, attr=0xf, range=[0x0000000098198000-0x00000000981c0000) (0MB)
[    0.000000] efi: mem42: type=7, attr=0xf, range=[0x00000000981c0000-0x00000000981c2000) (0MB)
[    0.000000] efi: mem43: type=4, attr=0xf, range=[0x00000000981c2000-0x00000000981c5000) (0MB)
[    0.000000] efi: mem44: type=7, attr=0xf, range=[0x00000000981c5000-0x00000000981c7000) (0MB)
[    0.000000] efi: mem45: type=4, attr=0xf, range=[0x00000000981c7000-0x00000000981e6000) (0MB)
[    0.000000] efi: mem46: type=7, attr=0xf, range=[0x00000000981e6000-0x00000000981ef000) (0MB)
[    0.000000] efi: mem47: type=4, attr=0xf, range=[0x00000000981ef000-0x00000000981fe000) (0MB)
[    0.000000] efi: mem48: type=7, attr=0xf, range=[0x00000000981fe000-0x00000000981ff000) (0MB)
[    0.000000] efi: mem49: type=4, attr=0xf, range=[0x00000000981ff000-0x00000000998bf000) (22MB)
[    0.000000] efi: mem50: type=7, attr=0xf, range=[0x00000000998bf000-0x0000000099d14000) (4MB)
[    0.000000] efi: mem51: type=2, attr=0xf, range=[0x0000000099d14000-0x0000000099d18000) (0MB)
[    0.000000] efi: mem52: type=3, attr=0xf, range=[0x0000000099d18000-0x000000009a0bf000) (3MB)
[    0.000000] efi: mem53: type=5, attr=0x800000000000000f, range=[0x000000009a0bf000-0x000000009a4bf000) (4MB)
[    0.000000] efi: mem54: type=6, attr=0x800000000000000f, range=[0x000000009a4bf000-0x000000009a6bf000) (2MB)
[    0.000000] efi: mem55: type=0, attr=0xf, range=[0x000000009a6bf000-0x000000009aebf000) (8MB)
[    0.000000] efi: mem56: type=10, attr=0xf, range=[0x000000009aebf000-0x000000009afbf000) (1MB)
[    0.000000] efi: mem57: type=9, attr=0xf, range=[0x000000009afbf000-0x000000009afff000) (0MB)
[    0.000000] efi: mem58: type=4, attr=0xf, range=[0x000000009afff000-0x000000009b000000) (0MB)
[    0.000000] efi: mem59: type=7, attr=0xf, range=[0x0000000100000000-0x000000025f600000) (5622MB)
[    0.000000] efi: mem60: type=0, attr=0x0, range=[0x00000000000a0000-0x00000000000c0000) (0MB)
[    0.000000] efi: mem61: type=0, attr=0x0, range=[0x000000009b000000-0x000000009fa00000) (74MB)
[    0.000000] efi: mem62: type=11, attr=0x8000000000000001, range=[0x00000000e0000000-0x00000000f0000000) (256MB)
[    0.000000] efi: mem63: type=11, attr=0x8000000000000001, range=[0x00000000feb00000-0x00000000feb04000) (0MB)
[    0.000000] efi: mem64: type=11, attr=0x8000000000000001, range=[0x00000000fec00000-0x00000000fec01000) (0MB)
[    0.000000] efi: mem65: type=11, attr=0x8000000000000001, range=[0x00000000fed10000-0x00000000fed1a000) (0MB)
[    0.000000] efi: mem66: type=11, attr=0x8000000000000001, range=[0x00000000fed1c000-0x00000000fed20000) (0MB)
[    0.000000] efi: mem67: type=11, attr=0x8000000000000001, range=[0x00000000fee00000-0x00000000fee01000) (0MB)
[    0.000000] efi: mem68: type=11, attr=0x8000000000000000, range=[0x00000000ffd80000-0x0000000100000000) (2MB)
[    0.000000] SMBIOS 2.7 present.
[    0.000000] DMI: Hewlett-Packard HP Pavilion 15 Notebook PC/1970, BIOS F.07 07/03/2013
[    0.000000] e820: update [mem 0x00000000-0x0000ffff] usable ==> reserved
[    0.000000] e820: remove [mem 0x000a0000-0x000fffff] usable
[    0.000000] No AGP bridge found
[    0.000000] e820: last_pfn = 0x25f600 max_arch_pfn = 0x400000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-E7FFF write-protect
[    0.000000]   E8000-EFFFF write-combining
[    0.000000]   F0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000 mask F80000000 write-back
[    0.000000]   1 base 080000000 mask FE0000000 write-back
[    0.000000]   2 base 09B000000 mask FFF000000 uncachable
[    0.000000]   3 base 09C000000 mask FFC000000 uncachable
[    0.000000]   4 base 0FFC00000 mask FFFC00000 write-protect
[    0.000000]   5 base 100000000 mask F00000000 write-back
[    0.000000]   6 base 200000000 mask F80000000 write-back
[    0.000000]   7 base 25F600000 mask FFFE00000 uncachable
[    0.000000]   8 base 25F800000 mask FFF800000 uncachable
[    0.000000]   9 base 260000000 mask FE0000000 uncachable
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] e820: last_pfn = 0x9b000 max_arch_pfn = 0x400000000
[    0.000000] initial memory mapped: [mem 0x00000000-0x1fffffff]
[    0.000000] Base memory trampoline at [ffff880000082000] 82000 size 24576
[    0.000000] init_memory_mapping: [mem 0x00000000-0x9affffff]
[    0.000000]  [mem 0x00000000-0x9affffff] page 2M
[    0.000000] kernel direct mapping tables up to 0x9affffff @ [mem 0x1fffc000-0x1fffffff]
[    0.000000] init_memory_mapping: [mem 0x100000000-0x25f5fffff]
[    0.000000]  [mem 0x100000000-0x25f5fffff] page 2M
[    0.000000] kernel direct mapping tables up to 0x25f5fffff @ [mem 0x99d11000-0x99d17fff]
[    0.000000] RAMDISK: [mem 0x36144000-0x37099fff]
[    0.000000] ACPI: RSDP 000000009affe014 00024 (v02 HPQOEM)
[    0.000000] ACPI: XSDT 000000009affe210 000AC (v01 HPQOEM SLIC-MPC 00000001 HP   01000013)
[    0.000000] ACPI: FACP 000000009affb000 0010C (v05 HPQOEM SLIC-MPC 00000001 HP   00040000)
[    0.000000] ACPI: DSDT 000000009afe8000 0F297 (v01 HPQOEM INSYDE   00000000 INTL 00040000)
[    0.000000] ACPI: FACS 000000009afba000 00040
[    0.000000] ACPI: UEFI 000000009affd000 00236 (v01 HPQOEM 1970     00000001 HP   00040000)
[    0.000000] ACPI: ASF! 000000009affc000 000A5 (v32 HPQOEM 1970     00000001 HP   00040000)
[    0.000000] ACPI: HPET 000000009affa000 00038 (v01 HPQOEM 1970     00000001 HP   00040000)
[    0.000000] ACPI: APIC 000000009aff9000 0008C (v03 HPQOEM 1970     00000001 HP   00040000)
[    0.000000] ACPI: MCFG 000000009aff8000 0003C (v01 HPQOEM 1970     00000001 HP   00040000)
[    0.000000] ACPI: WDAT 000000009afe7000 00224 (v01 HPQOEM 1970     00000001 HP   00040000)
[    0.000000] ACPI: SSDT 000000009afe6000 00E21 (v01 HPQOEM INSYDE   00001000 INTL 00040000)
[    0.000000] ACPI: BOOT 000000009afe4000 00028 (v01 HPQOEM 1970     00000001 HP   00040000)
[    0.000000] ACPI: ASPT 000000009afe2000 00034 (v07 HPQOEM 1970     00000001 HP   00040000)
[    0.000000] ACPI: DBGP 000000009afe1000 00034 (v01 HPQOEM 1970     00000001 HP   00040000)
[    0.000000] ACPI: FPDT 000000009afdf000 00044 (v01 HPQOEM 1970     00000001 HP   00040000)
[    0.000000] ACPI: MSDM 000000009afde000 00055 (v03 HPQOEM SLIC-MPC 00000001 HP   00040000)
[    0.000000] ACPI: SSDT 000000009afdd000 009AA (v01 HPQOEM INSYDE   00003000 INTL 00040000)
[    0.000000] ACPI: SSDT 000000009afdc000 00B22 (v01 HPQOEM INSYDE   00003000 INTL 00040000)
[    0.000000] ACPI: SSDT 000000009afd9000 01EED (v01 HPQOEM INSYDE   00001000 INTL 00040000)
[    0.000000] ACPI: BGRT 000000009afdb000 00038 (v01 HPQOEM 1970     00000001 HP   00040000)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at [mem 0x0000000000000000-0x000000025f5fffff]
[    0.000000] Initmem setup node 0 [mem 0x00000000-0x25f5fffff]
[    0.000000]   NODE_DATA [mem 0x25f5fb000-0x25f5fffff]
[    0.000000]  [ffffea0000000000-ffffea00097fffff] PMD -> [ffff880256c00000-ffff88025ebfffff] on node 0
[    0.000000] Zone ranges:
[    0.000000]   DMA      [mem 0x00010000-0x00ffffff]
[    0.000000]   DMA32    [mem 0x01000000-0xffffffff]
[    0.000000]   Normal   [mem 0x100000000-0x25f5fffff]
[    0.000000] Movable zone start for each node
[    0.000000] Early memory node ranges
[    0.000000]   node   0: [mem 0x00010000-0x00087fff]
[    0.000000]   node   0: [mem 0x00100000-0x1fffffff]
[    0.000000]   node   0: [mem 0x20200000-0x40003fff]
[    0.000000]   node   0: [mem 0x40005000-0x9a0befff]
[    0.000000]   node   0: [mem 0x9afff000-0x9affffff]
[    0.000000]   node   0: [mem 0x100000000-0x25f5fffff]
[    0.000000] On node 0 totalpages: 2069559
[    0.000000]   DMA zone: 64 pages used for memmap
[    0.000000]   DMA zone: 7 pages reserved
[    0.000000]   DMA zone: 3889 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 9787 pages used for memmap
[    0.000000]   DMA32 zone: 616580 pages, LIFO batch:31
[    0.000000]   Normal zone: 22488 pages used for memmap
[    0.000000]   Normal zone: 1416744 pages, LIFO batch:31
[    0.000000] ACPI: PM-Timer IO Port: 0x408
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x02] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x03] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x05] lapic_id[0x00] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x06] lapic_id[0x00] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x07] lapic_id[0x00] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x08] lapic_id[0x00] disabled)
[    0.000000] ACPI: IOAPIC (id[0x00] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 0, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
[    0.000000] smpboot: Allowing 8 CPUs, 4 hotplug CPUs
[    0.000000] nr_irqs_gsi: 40
[    0.000000] PM: Registered nosave memory: 0000000000088000 - 00000000000c0000
[    0.000000] PM: Registered nosave memory: 00000000000c0000 - 0000000000100000
[    0.000000] PM: Registered nosave memory: 0000000020000000 - 0000000020200000
[    0.000000] PM: Registered nosave memory: 0000000040004000 - 0000000040005000
[    0.000000] PM: Registered nosave memory: 000000009a0bf000 - 000000009aebf000
[    0.000000] PM: Registered nosave memory: 000000009aebf000 - 000000009afbf000
[    0.000000] PM: Registered nosave memory: 000000009afbf000 - 000000009afff000
[    0.000000] PM: Registered nosave memory: 000000009b000000 - 000000009fa00000
[    0.000000] PM: Registered nosave memory: 000000009fa00000 - 00000000e0000000
[    0.000000] PM: Registered nosave memory: 00000000e0000000 - 00000000f0000000
[    0.000000] PM: Registered nosave memory: 00000000f0000000 - 00000000feb00000
[    0.000000] PM: Registered nosave memory: 00000000feb00000 - 00000000feb04000
[    0.000000] PM: Registered nosave memory: 00000000feb04000 - 00000000fec00000
[    0.000000] PM: Registered nosave memory: 00000000fec00000 - 00000000fec01000
[    0.000000] PM: Registered nosave memory: 00000000fec01000 - 00000000fed10000
[    0.000000] PM: Registered nosave memory: 00000000fed10000 - 00000000fed1a000
[    0.000000] PM: Registered nosave memory: 00000000fed1a000 - 00000000fed1c000
[    0.000000] PM: Registered nosave memory: 00000000fed1c000 - 00000000fed20000
[    0.000000] PM: Registered nosave memory: 00000000fed20000 - 00000000fee00000
[    0.000000] PM: Registered nosave memory: 00000000fee00000 - 00000000fee01000
[    0.000000] PM: Registered nosave memory: 00000000fee01000 - 00000000ffd80000
[    0.000000] PM: Registered nosave memory: 00000000ffd80000 - 0000000100000000
[    0.000000] e820: [mem 0x9fa00000-0xdfffffff] available for PCI devices
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:256 nr_cpumask_bits:256 nr_cpu_ids:8 nr_node_ids:1
[    0.000000] PERCPU: Embedded 28 pages/cpu @ffff88025f200000 s84928 r8192 d21568 u262144
[    0.000000] pcpu-alloc: s84928 r8192 d21568 u262144 alloc=1*2097152
[    0.000000] pcpu-alloc: [0] 0 1 2 3 4 5 6 7 
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 2037213
[    0.000000] Policy zone: Normal
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.8.0-33-generic.efi.signed root=UUID=66a4c22f-60ec-4202-a91d-b15f2b67db2a ro quiet splash vt.handoff=7
[    0.000000] PID hash table entries: 4096 (order: 3, 32768 bytes)
[    0.000000] __ex_table already sorted, skipping sort
[    0.000000] xsave: enabled xstate_bv 0x7, cntxt size 0x340
[    0.000000] Checking aperture...
[    0.000000] No AGP bridge found
[    0.000000] Calgary: detecting Calgary via BIOS EBDA area
[    0.000000] Calgary: Unable to locate Rio Grande table in EBDA - bailing!
[    0.000000] Memory: 8002228k/9951232k available (7172k kernel code, 1672996k absent, 276008k reserved, 6071k data, 1016k init)
[    0.000000] SLUB: Genslabs=15, HWalign=64, Order=0-3, MinObjects=0, CPUs=8, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000]     RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000]     RCU restricting CPUs from NR_CPUS=256 to nr_cpu_ids=8.
[    0.000000] NR_IRQS:16640 nr_irqs:744 16
[    0.000000] Console: colour dummy device 80x25
[    0.000000] console [tty0] enabled
[    0.000000] allocated 33554432 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] hpet clockevent registered
[    0.000000] tsc: Fast TSC calibration using PIT
[    0.004000] tsc: Detected 2594.204 MHz processor
[    0.000002] Calibrating delay loop (skipped), value calculated using timer frequency.. 5188.40 BogoMIPS (lpj=10376816)
[    0.000004] pid_max: default: 32768 minimum: 301
[    0.032245] Security Framework initialized
[    0.032256] AppArmor: AppArmor initialized
[    0.032256] Yama: becoming mindful.
[    0.032700] Dentry cache hash table entries: 1048576 (order: 11, 8388608 bytes)
[    0.034602] Inode-cache hash table entries: 524288 (order: 10, 4194304 bytes)
[    0.035433] Mount-cache hash table entries: 256
[    0.035577] Initializing cgroup subsys cpuacct
[    0.035579] Initializing cgroup subsys memory
[    0.035584] Initializing cgroup subsys devices
[    0.035586] Initializing cgroup subsys freezer
[    0.035587] Initializing cgroup subsys blkio
[    0.035589] Initializing cgroup subsys perf_event
[    0.035590] Initializing cgroup subsys hugetlb
[    0.035611] CPU: Physical Processor ID: 0
[    0.035612] CPU: Processor Core ID: 0
[    0.035616] ENERGY_PERF_BIAS: Set to 'normal', was 'performance'
[    0.035616] ENERGY_PERF_BIAS: View and update with x86_energy_perf_policy(8)
[    0.035960] mce: CPU supports 7 MCE banks
[    0.035970] CPU0: Thermal monitoring enabled (TM1)
[    0.035976] process: using mwait in idle threads
[    0.035980] Last level iTLB entries: 4KB 512, 2MB 0, 4MB 0
[    0.035980] Last level dTLB entries: 4KB 512, 2MB 32, 4MB 32
[    0.035980] tlb_flushall_shift: 1
[    0.036115] Freeing SMP alternatives: 24k freed
[    0.038074] ACPI: Core revision 20121018
[    0.059209] ftrace: allocating 29363 entries in 115 pages
[    0.072650] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.112263] smpboot: CPU0: Intel(R) Core(TM) i5-3230M CPU @ 2.60GHz (fam: 06, model: 3a, stepping: 09)
[    0.112270] TSC deadline timer enabled
[    0.112274] Performance Events: PEBS fmt1+, 16-deep LBR, IvyBridge events, Intel PMU driver.
[    0.112280] ... version:                3
[    0.112281] ... bit width:              48
[    0.112281] ... generic registers:      4
[    0.112282] ... value mask:             0000ffffffffffff
[    0.112283] ... max period:             000000007fffffff
[    0.112284] ... fixed-purpose events:   3
[    0.112285] ... event mask:             000000070000000f
[    0.126764] NMI watchdog: enabled on all CPUs, permanently consumes one hw-PMU counter.
[    0.113289] smpboot: Booting Node   0, Processors  #1 #2 #3
[    0.153741] Brought up 4 CPUs
[    0.153744] smpboot: Total of 4 processors activated (20753.63 BogoMIPS)
[    0.157114] devtmpfs: initialized
[    0.157978] EVM: security.selinux
[    0.157979] EVM: security.SMACK64
[    0.157980] EVM: security.capability
[    0.158017] PM: Registering ACPI NVS region [mem 0x9aebf000-0x9afbefff] (1048576 bytes)
[    0.158652] regulator-dummy: no parameters
[    0.158689] NET: Registered protocol family 16
[    0.158805] ACPI FADT declares the system doesn't support PCIe ASPM, so disable it
[    0.158807] ACPI: bus type pci registered
[    0.158862] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)
[    0.158864] PCI: MMCONFIG at [mem 0xe0000000-0xefffffff] reserved in E820
[    0.180096] PCI: Using configuration type 1 for base access
[    0.180801] bio: create slab <bio-0> at 0
[    0.180868] ACPI: Added _OSI(Module Device)
[    0.180870] ACPI: Added _OSI(Processor Device)
[    0.180871] ACPI: Added _OSI(3.0 _SCP Extensions)
[    0.180873] ACPI: Added _OSI(Processor Aggregator Device)
[    0.182167] ACPI: EC: Look up EC in DSDT
[    0.183434] ACPI: Executed 1 blocks of module-level executable AML code
[    0.185702] [Firmware Bug]: ACPI: BIOS _OSI(Linux) query ignored
[    0.186126] ACPI: SSDT 000000009ae19018 0083B (v01  PmRef  Cpu0Cst 00003001 INTL 20111123)
[    0.186456] ACPI: Dynamic OEM Table Load:
[    0.186457] ACPI: SSDT           (null) 0083B (v01  PmRef  Cpu0Cst 00003001 INTL 20111123)
[    0.186686] ACPI: SSDT 000000009ae5ba98 00303 (v01  PmRef    ApIst 00003000 INTL 20111123)
[    0.187040] ACPI: Dynamic OEM Table Load:
[    0.187042] ACPI: SSDT           (null) 00303 (v01  PmRef    ApIst 00003000 INTL 20111123)
[    0.188302] ACPI: SSDT 000000009ae18d98 00119 (v01  PmRef    ApCst 00003000 INTL 20111123)
[    0.188625] ACPI: Dynamic OEM Table Load:
[    0.188627] ACPI: SSDT           (null) 00119 (v01  PmRef    ApCst 00003000 INTL 20111123)
[    1.823213] ACPI: Interpreter enabled
[    1.823217] ACPI: (supports S0 S3 S4 S5)
[    1.823236] ACPI: Using IOAPIC for interrupt routing
[    1.827003] ACPI: EC: GPE = 0x1d, I/O: command/status = 0x66, data = 0x62
[    1.827157] ACPI: No dock devices found.
[    1.827161] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    1.827305] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-fe])
[    1.827307] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    1.827481] \_SB_.PCI0:_OSC invalid UUID
[    1.827482] _OSC request data:1 8 0 
[    1.827722] PCI host bridge to bus 0000:00
[    1.827725] pci_bus 0000:00: root bus resource [bus 00-fe]
[    1.827727] pci_bus 0000:00: root bus resource [io  0x0000-0x0cf7]
[    1.827728] pci_bus 0000:00: root bus resource [io  0x0d00-0xffff]
[    1.827730] pci_bus 0000:00: root bus resource [mem 0x000a0000-0x000bffff]
[    1.827731] pci_bus 0000:00: root bus resource [mem 0x000c0000-0x000c3fff]
[    1.827733] pci_bus 0000:00: root bus resource [mem 0x000c4000-0x000c7fff]
[    1.827734] pci_bus 0000:00: root bus resource [mem 0x000c8000-0x000cbfff]
[    1.827736] pci_bus 0000:00: root bus resource [mem 0x000cc000-0x000cffff]
[    1.827737] pci_bus 0000:00: root bus resource [mem 0x000d0000-0x000d3fff]
[    1.827738] pci_bus 0000:00: root bus resource [mem 0x000d4000-0x000d7fff]
[    1.827740] pci_bus 0000:00: root bus resource [mem 0x000d8000-0x000dbfff]
[    1.827741] pci_bus 0000:00: root bus resource [mem 0x000dc000-0x000dffff]
[    1.827743] pci_bus 0000:00: root bus resource [mem 0x000e0000-0x000e3fff]
[    1.827744] pci_bus 0000:00: root bus resource [mem 0x000e4000-0x000e7fff]
[    1.827745] pci_bus 0000:00: root bus resource [mem 0x000e8000-0x000ebfff]
[    1.827747] pci_bus 0000:00: root bus resource [mem 0x000ec000-0x000effff]
[    1.827748] pci_bus 0000:00: root bus resource [mem 0x000f0000-0x000fffff]
[    1.827750] pci_bus 0000:00: root bus resource [mem 0x9fa00000-0xfeafffff]
[    1.827758] pci 0000:00:00.0: [8086:0154] type 00 class 0x060000
[    1.827792] pci 0000:00:01.0: [8086:0151] type 01 class 0x060400
[    1.827820] pci 0000:00:01.0: PME# supported from D0 D3hot D3cold
[    1.827838] pci 0000:00:02.0: [8086:0166] type 00 class 0x030000
[    1.827848] pci 0000:00:02.0: reg 10: [mem 0xc3000000-0xc33fffff 64bit]
[    1.827855] pci 0000:00:02.0: reg 18: [mem 0xb0000000-0xbfffffff 64bit pref]
[    1.827859] pci 0000:00:02.0: reg 20: [io  0x6000-0x603f]
[    1.827910] pci 0000:00:14.0: [8086:1e31] type 00 class 0x0c0330
[    1.827931] pci 0000:00:14.0: reg 10: [mem 0xc3600000-0xc360ffff 64bit]
[    1.828002] pci 0000:00:14.0: PME# supported from D3hot D3cold
[    1.828025] pci 0000:00:16.0: [8086:1e3a] type 00 class 0x078000
[    1.828048] pci 0000:00:16.0: reg 10: [mem 0xc3614000-0xc361400f 64bit]
[    1.828124] pci 0000:00:16.0: PME# supported from D0 D3hot D3cold
[    1.828157] pci 0000:00:1a.0: [8086:1e2d] type 00 class 0x0c0320
[    1.828177] pci 0000:00:1a.0: reg 10: [mem 0xc3619000-0xc36193ff]
[    1.828267] pci 0000:00:1a.0: PME# supported from D0 D3hot D3cold
[    1.828294] pci 0000:00:1b.0: [8086:1e20] type 00 class 0x040300
[    1.828308] pci 0000:00:1b.0: reg 10: [mem 0xc3610000-0xc3613fff 64bit]
[    1.828375] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    1.828398] pci 0000:00:1c.0: [8086:1e10] type 01 class 0x060400
[    1.828476] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    1.828501] pci 0000:00:1c.1: [8086:1e12] type 01 class 0x060400
[    1.828578] pci 0000:00:1c.1: PME# supported from D0 D3hot D3cold
[    1.828604] pci 0000:00:1c.2: [8086:1e14] type 01 class 0x060400
[    1.828680] pci 0000:00:1c.2: PME# supported from D0 D3hot D3cold
[    1.828714] pci 0000:00:1d.0: [8086:1e26] type 00 class 0x0c0320
[    1.828735] pci 0000:00:1d.0: reg 10: [mem 0xc3618000-0xc36183ff]
[    1.828825] pci 0000:00:1d.0: PME# supported from D0 D3hot D3cold
[    1.828851] pci 0000:00:1f.0: [8086:1e59] type 00 class 0x060100
[    1.828975] pci 0000:00:1f.2: [8086:1e03] type 00 class 0x010601
[    1.828993] pci 0000:00:1f.2: reg 10: [io  0x6088-0x608f]
[    1.829001] pci 0000:00:1f.2: reg 14: [io  0x6094-0x6097]
[    1.829009] pci 0000:00:1f.2: reg 18: [io  0x6080-0x6087]
[    1.829017] pci 0000:00:1f.2: reg 1c: [io  0x6090-0x6093]
[    1.829025] pci 0000:00:1f.2: reg 20: [io  0x6060-0x607f]
[    1.829033] pci 0000:00:1f.2: reg 24: [mem 0xc3617000-0xc36177ff]
[    1.829078] pci 0000:00:1f.2: PME# supported from D3hot
[    1.829097] pci 0000:00:1f.3: [8086:1e22] type 00 class 0x0c0500
[    1.829112] pci 0000:00:1f.3: reg 10: [mem 0xc3615000-0xc36150ff 64bit]
[    1.829132] pci 0000:00:1f.3: reg 20: [io  0x6040-0x605f]
[    1.829184] pci 0000:01:00.0: [1002:6660] type 00 class 0x038000
[    1.829192] pci 0000:01:00.0: reg 10: [mem 0xa0000000-0xafffffff 64bit pref]
[    1.829198] pci 0000:01:00.0: reg 18: [mem 0xc2000000-0xc203ffff 64bit]
[    1.829203] pci 0000:01:00.0: reg 20: [io  0x5000-0x50ff]
[    1.829211] pci 0000:01:00.0: reg 30: [mem 0xfffe0000-0xffffffff pref]
[    1.829234] pci 0000:01:00.0: supports D1 D2
[    1.829236] pci 0000:01:00.0: PME# supported from D1 D2 D3hot
[    1.837867] pci 0000:00:01.0: PCI bridge to [bus 01-06]
[    1.837872] pci 0000:00:01.0:   bridge window [io  0x5000-0x5fff]
[    1.837877] pci 0000:00:01.0:   bridge window [mem 0xc2000000-0xc2ffffff]
[    1.837883] pci 0000:00:01.0:   bridge window [mem 0xa0000000-0xafffffff 64bit pref]
[    1.837986] pci 0000:07:00.0: [10ec:8179] type 00 class 0x028000
[    1.838013] pci 0000:07:00.0: reg 10: [io  0x4000-0x40ff]
[    1.838061] pci 0000:07:00.0: reg 18: [mem 0xc3500000-0xc3503fff 64bit]
[    1.838213] pci 0000:07:00.0: supports D1 D2
[    1.838214] pci 0000:07:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    1.845877] pci 0000:00:1c.0: PCI bridge to [bus 07]
[    1.845885] pci 0000:00:1c.0:   bridge window [io  0x4000-0x4fff]
[    1.845892] pci 0000:00:1c.0:   bridge window [mem 0xc3500000-0xc35fffff]
[    1.845981] pci 0000:08:00.0: [10ec:8136] type 00 class 0x020000
[    1.846001] pci 0000:08:00.0: reg 10: [io  0x3000-0x30ff]
[    1.846035] pci 0000:08:00.0: reg 18: [mem 0xc3404000-0xc3404fff 64bit pref]
[    1.846057] pci 0000:08:00.0: reg 20: [mem 0xc3400000-0xc3403fff 64bit pref]
[    1.846071] pci 0000:08:00.0: reg 30: [mem 0xffff0000-0xffffffff pref]
[    1.846151] pci 0000:08:00.0: supports D1 D2
[    1.846152] pci 0000:08:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    1.853855] pci 0000:00:1c.1: PCI bridge to [bus 08]
[    1.853863] pci 0000:00:1c.1:   bridge window [io  0x3000-0x3fff]
[    1.853870] pci 0000:00:1c.1:   bridge window [mem 0xc3400000-0xc34fffff]
[    1.853941] pci 0000:00:1c.2: PCI bridge to [bus 09-0e]
[    1.853945] pci 0000:00:1c.2:   bridge window [io  0x2000-0x2fff]
[    1.853950] pci 0000:00:1c.2:   bridge window [mem 0xc1000000-0xc1ffffff]
[    1.853956] pci 0000:00:1c.2:   bridge window [mem 0xc0000000-0xc0ffffff 64bit pref]
[    1.853983] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEG0._PRT]
[    1.854027] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP01._PRT]
[    1.854048] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP02._PRT]
[    1.854071] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP03._PRT]
[    1.854139] \_SB_.PCI0:_OSC invalid UUID
[    1.854140] _OSC request data:1 1f 0 
[    1.854143]  pci0000:00: ACPI _OSC support notification failed, disabling PCIe ASPM
[    1.854144]  pci0000:00: Unable to request _OSC control (_OSC support mask: 0x08)
[    1.854604] ACPI: PCI Interrupt Link [LNKA] (IRQs 1 3 4 5 6 10 11 12 14 15) *0, disabled.
[    1.854641] ACPI: PCI Interrupt Link [LNKB] (IRQs 1 3 4 5 6 10 11 12 14 15) *0, disabled.
[    1.854677] ACPI: PCI Interrupt Link [LNKC] (IRQs 1 3 4 5 6 10 11 12 14 15) *0, disabled.
[    1.854713] ACPI: PCI Interrupt Link [LNKD] (IRQs 1 3 4 5 6 10 11 12 14 15) *0, disabled.
[    1.854748] ACPI: PCI Interrupt Link [LNKE] (IRQs 1 3 4 5 6 10 11 12 14 15) *0, disabled.
[    1.854781] ACPI: PCI Interrupt Link [LNKF] (IRQs 1 3 4 5 6 10 11 12 14 15) *0, disabled.
[    1.854815] ACPI: PCI Interrupt Link [LNKG] (IRQs 1 3 4 5 6 10 11 12 14 15) *0, disabled.
[    1.854851] ACPI: PCI Interrupt Link [LNKH] (IRQs 1 3 4 5 6 10 11 12 14 15) *0, disabled.
[    1.854926] vgaarb: device added: PCI:0000:00:02.0,decodes=io+mem,owns=io+mem,locks=none
[    1.854929] vgaarb: loaded
[    1.854930] vgaarb: bridge control possible 0000:00:02.0
[    1.855057] SCSI subsystem initialized
[    1.855059] ACPI: bus type scsi registered
[    1.855086] libata version 3.00 loaded.
[    1.855098] ACPI: bus type usb registered
[    1.855113] usbcore: registered new interface driver usbfs
[    1.855118] usbcore: registered new interface driver hub
[    1.855134] usbcore: registered new device driver usb
[    1.855197] PCI: Using ACPI for IRQ routing
[    1.861603] PCI: pci_cache_line_size set to 64 bytes
[    1.861661] e820: reserve RAM buffer [mem 0x00088000-0x0008ffff]
[    1.861663] e820: reserve RAM buffer [mem 0x40004000-0x43ffffff]
[    1.861664] e820: reserve RAM buffer [mem 0x9a0bf000-0x9bffffff]
[    1.861666] e820: reserve RAM buffer [mem 0x9b000000-0x9bffffff]
[    1.861667] e820: reserve RAM buffer [mem 0x25f600000-0x25fffffff]
[    1.861731] NetLabel: Initializing
[    1.861733] NetLabel:  domain hash size = 128
[    1.861733] NetLabel:  protocols = UNLABELED CIPSOv4
[    1.861741] NetLabel:  unlabeled traffic allowed by default
[    1.861784] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0, 0, 0, 0, 0
[    1.861788] hpet0: 8 comparators, 64-bit 14.318180 MHz counter
[    1.863798] Switching to clocksource hpet
[    1.867727] AppArmor: AppArmor Filesystem Enabled
[    1.867747] pnp: PnP ACPI init
[    1.867757] ACPI: bus type pnp registered
[    1.867988] pnp 00:00: [dma 4]
[    1.868007] pnp 00:00: Plug and Play ACPI device, IDs PNP0200 (active)
[    1.868022] pnp 00:01: Plug and Play ACPI device, IDs INT0800 (active)
[    1.868099] pnp 00:02: Plug and Play ACPI device, IDs PNP0103 (active)
[    1.868122] pnp 00:03: Plug and Play ACPI device, IDs PNP0c04 (active)
[    1.868162] system 00:04: [io  0x0680-0x069f] has been reserved
[    1.868164] system 00:04: [io  0x1000-0x100f] has been reserved
[    1.868166] system 00:04: [io  0xffff] has been reserved
[    1.868167] system 00:04: [io  0xffff] has been reserved
[    1.868169] system 00:04: [io  0x0400-0x0453] has been reserved
[    1.868170] system 00:04: [io  0x0458-0x047f] has been reserved
[    1.868172] system 00:04: [io  0x0500-0x057f] has been reserved
[    1.868174] system 00:04: [io  0x164e-0x164f] has been reserved
[    1.868175] system 00:04: [io  0x0454-0x0457] has been reserved
[    1.868177] system 00:04: [io  0x0380-0x0387] has been reserved
[    1.868179] system 00:04: Plug and Play ACPI device, IDs PNP0c02 (active)
[    1.868197] pnp 00:05: Plug and Play ACPI device, IDs PNP0b00 (active)
[    1.868225] pnp 00:06: Plug and Play ACPI device, IDs HPQ8001 PNP0303 (active)
[    1.868252] pnp 00:07: Plug and Play ACPI device, IDs SYN1e91 SYN1e00 SYN0002 PNP0f13 (active)
[    1.868283] pnp 00:08: Plug and Play ACPI device, IDs HPQ0004 (active)
[    1.868458] system 00:09: [mem 0xfed1c000-0xfed1ffff] has been reserved
[    1.868460] system 00:09: [mem 0xfed10000-0xfed17fff] has been reserved
[    1.868462] system 00:09: [mem 0xfed18000-0xfed18fff] has been reserved
[    1.868463] system 00:09: [mem 0xfed19000-0xfed19fff] has been reserved
[    1.868465] system 00:09: [mem 0xe0000000-0xefffffff] has been reserved
[    1.868467] system 00:09: [mem 0xfed20000-0xfed3ffff] has been reserved
[    1.868468] system 00:09: [mem 0xfed90000-0xfed93fff] has been reserved
[    1.868470] system 00:09: [mem 0xff000000-0xffffffff] could not be reserved
[    1.868472] system 00:09: [mem 0xfee00000-0xfeefffff] could not be reserved
[    1.868474] system 00:09: [mem 0x9fa00000-0x9fa00fff] has been reserved
[    1.868476] system 00:09: Plug and Play ACPI device, IDs PNP0c02 (active)
[    1.868641] system 00:0a: [mem 0x20000000-0x201fffff] has been reserved
[    1.868643] system 00:0a: [mem 0x40004000-0x40004fff] has been reserved
[    1.868645] system 00:0a: Plug and Play ACPI device, IDs PNP0c01 (active)
[    1.868660] pnp: PnP ACPI: found 11 devices
[    1.868661] ACPI: ACPI bus type pnp unregistered
[    1.874492] pci 0000:01:00.0: no compatible bridge window for [mem 0xfffe0000-0xffffffff pref]
[    1.874494] pci 0000:08:00.0: no compatible bridge window for [mem 0xffff0000-0xffffffff pref]
[    1.874531] pci 0000:00:1c.1: BAR 15: assigned [mem 0x9fb00000-0x9fbfffff pref]
[    1.874533] pci 0000:01:00.0: BAR 6: assigned [mem 0xc2040000-0xc205ffff pref]
[    1.874535] pci 0000:00:01.0: PCI bridge to [bus 01-06]
[    1.874537] pci 0000:00:01.0:   bridge window [io  0x5000-0x5fff]
[    1.874540] pci 0000:00:01.0:   bridge window [mem 0xc2000000-0xc2ffffff]
[    1.874542] pci 0000:00:01.0:   bridge window [mem 0xa0000000-0xafffffff 64bit pref]
[    1.874546] pci 0000:00:1c.0: PCI bridge to [bus 07]
[    1.874549] pci 0000:00:1c.0:   bridge window [io  0x4000-0x4fff]
[    1.874554] pci 0000:00:1c.0:   bridge window [mem 0xc3500000-0xc35fffff]
[    1.874563] pci 0000:08:00.0: BAR 6: assigned [mem 0x9fb00000-0x9fb0ffff pref]
[    1.874564] pci 0000:00:1c.1: PCI bridge to [bus 08]
[    1.874567] pci 0000:00:1c.1:   bridge window [io  0x3000-0x3fff]
[    1.874572] pci 0000:00:1c.1:   bridge window [mem 0xc3400000-0xc34fffff]
[    1.874576] pci 0000:00:1c.1:   bridge window [mem 0x9fb00000-0x9fbfffff pref]
[    1.874583] pci 0000:00:1c.2: PCI bridge to [bus 09-0e]
[    1.874586] pci 0000:00:1c.2:   bridge window [io  0x2000-0x2fff]
[    1.874591] pci 0000:00:1c.2:   bridge window [mem 0xc1000000-0xc1ffffff]
[    1.874595] pci 0000:00:1c.2:   bridge window [mem 0xc0000000-0xc0ffffff 64bit pref]
[    1.874625] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
[    1.874626] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
[    1.874628] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
[    1.874629] pci_bus 0000:00: resource 7 [mem 0x000c0000-0x000c3fff]
[    1.874631] pci_bus 0000:00: resource 8 [mem 0x000c4000-0x000c7fff]
[    1.874632] pci_bus 0000:00: resource 9 [mem 0x000c8000-0x000cbfff]
[    1.874634] pci_bus 0000:00: resource 10 [mem 0x000cc000-0x000cffff]
[    1.874635] pci_bus 0000:00: resource 11 [mem 0x000d0000-0x000d3fff]
[    1.874637] pci_bus 0000:00: resource 12 [mem 0x000d4000-0x000d7fff]
[    1.874638] pci_bus 0000:00: resource 13 [mem 0x000d8000-0x000dbfff]
[    1.874640] pci_bus 0000:00: resource 14 [mem 0x000dc000-0x000dffff]
[    1.874641] pci_bus 0000:00: resource 15 [mem 0x000e0000-0x000e3fff]
[    1.874643] pci_bus 0000:00: resource 16 [mem 0x000e4000-0x000e7fff]
[    1.874644] pci_bus 0000:00: resource 17 [mem 0x000e8000-0x000ebfff]
[    1.874646] pci_bus 0000:00: resource 18 [mem 0x000ec000-0x000effff]
[    1.874647] pci_bus 0000:00: resource 19 [mem 0x000f0000-0x000fffff]
[    1.874649] pci_bus 0000:00: resource 20 [mem 0x9fa00000-0xfeafffff]
[    1.874650] pci_bus 0000:01: resource 0 [io  0x5000-0x5fff]
[    1.874652] pci_bus 0000:01: resource 1 [mem 0xc2000000-0xc2ffffff]
[    1.874653] pci_bus 0000:01: resource 2 [mem 0xa0000000-0xafffffff 64bit pref]
[    1.874655] pci_bus 0000:07: resource 0 [io  0x4000-0x4fff]
[    1.874656] pci_bus 0000:07: resource 1 [mem 0xc3500000-0xc35fffff]
[    1.874658] pci_bus 0000:08: resource 0 [io  0x3000-0x3fff]
[    1.874659] pci_bus 0000:08: resource 1 [mem 0xc3400000-0xc34fffff]
[    1.874661] pci_bus 0000:08: resource 2 [mem 0x9fb00000-0x9fbfffff pref]
[    1.874662] pci_bus 0000:09: resource 0 [io  0x2000-0x2fff]
[    1.874664] pci_bus 0000:09: resource 1 [mem 0xc1000000-0xc1ffffff]
[    1.874665] pci_bus 0000:09: resource 2 [mem 0xc0000000-0xc0ffffff 64bit pref]
[    1.874689] NET: Registered protocol family 2
[    1.874833] TCP established hash table entries: 65536 (order: 8, 1048576 bytes)
[    1.875002] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    1.875121] TCP: Hash tables configured (established 65536 bind 65536)
[    1.875136] TCP: reno registered
[    1.875147] UDP hash table entries: 4096 (order: 5, 131072 bytes)
[    1.875171] UDP-Lite hash table entries: 4096 (order: 5, 131072 bytes)
[    1.875226] NET: Registered protocol family 1
[    1.875237] pci 0000:00:02.0: Boot video device
[    1.907777] PCI: CLS 64 bytes, default 64
[    1.907835] Trying to unpack rootfs image as initramfs...
[    2.128647] Freeing initrd memory: 15704k freed
[    2.130364] PCI-DMA: Using software bounce buffering for IO (SWIOTLB)
[    2.130368] software IO TLB [mem 0x933ed000-0x973ed000] (64MB) mapped at [ffff8800933ed000-ffff8800973ecfff]
[    2.130403] Simple Boot Flag at 0x44 set to 0x1
[    2.130722] Initialise module verification
[    2.130757] audit: initializing netlink socket (disabled)
[    2.130765] type=2000 audit(1395220348.104:1): initialized
[    2.158121] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    2.159279] VFS: Disk quotas dquot_6.5.2
[    2.159310] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    2.159650] fuse init (API version 7.20)
[    2.159703] msgmni has been set to 15750
[    2.160088] Key type asymmetric registered
[    2.160091] Asymmetric key parser 'x509' registered
[    2.160117] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 252)
[    2.160139] io scheduler noop registered
[    2.160141] io scheduler deadline registered (default)
[    2.160146] io scheduler cfq registered
[    2.160224] pcieport 0000:00:01.0: irq 40 for MSI/MSI-X
[    2.160378] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    2.160389] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    2.160430] efifb: probing for efifb
[    2.160853] efifb: framebuffer at 0xb0000000, mapped to 0xffffc90021280000, using 4160k, total 4160k
[    2.160854] efifb: mode is 1366x768x32, linelength=5504, pages=1
[    2.160855] efifb: scrolling: redraw
[    2.160857] efifb: Truecolor: size=8:8:8:8, shift=24:16:8:0
[    2.162907] Console: switching to colour frame buffer device 170x48
[    2.164853] fb0: EFI VGA frame buffer device
[    2.164858] intel_idle: MWAIT substates: 0x21120
[    2.164859] intel_idle: v0.4 model 0x3A
[    2.164860] intel_idle: lapic_timer_reliable_states 0xffffffff
[    2.165264] ACPI: AC Adapter [ACAD] (off-line)
[    2.165337] input: Lid Switch as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0D:00/input/input0
[    2.167573] ACPI: Lid Switch [LID0]
[    2.167601] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input1
[    2.167604] ACPI: Power Button [PWRB]
[    2.167636] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input2
[    2.167638] ACPI: Power Button [PWRF]
[    2.167697] ACPI: Requesting acpi_cpufreq
[    2.171918] [Firmware Bug]: Invalid critical threshold (0)
[    2.173162] thermal LNXTHERM:00: registered as thermal_zone0
[    2.173164] ACPI: Thermal Zone [TZ01] (0 C)
[    2.173193] GHES: HEST is not enabled!
[    2.173260] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    2.175017] Linux agpgart interface v0.103
[    2.175931] brd: module loaded
[    2.176348] loop: module loaded
[    2.176576] libphy: Fixed MDIO Bus: probed
[    2.176616] tun: Universal TUN/TAP device driver, 1.6
[    2.176617] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    2.176646] PPP generic driver version 2.4.2
[    2.176691] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    2.176692] ehci-pci: EHCI PCI platform driver
[    2.176726] ehci-pci 0000:00:1a.0: setting latency timer to 64
[    2.176730] ehci-pci 0000:00:1a.0: EHCI Host Controller
[    2.176734] ehci-pci 0000:00:1a.0: new USB bus registered, assigned bus number 1
[    2.176747] ehci-pci 0000:00:1a.0: debug port 2
[    2.180638] ehci-pci 0000:00:1a.0: cache line size of 64 is not supported
[    2.180652] ehci-pci 0000:00:1a.0: irq 16, io mem 0xc3619000
[    2.191213] ehci-pci 0000:00:1a.0: USB 2.0 started, EHCI 1.00
[    2.191243] usb usb1: New USB device found, idVendor=1d6b, idProduct=0002
[    2.191246] usb usb1: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    2.191249] usb usb1: Product: EHCI Host Controller
[    2.191252] usb usb1: Manufacturer: Linux 3.8.0-33-generic ehci_hcd
[    2.191255] usb usb1: SerialNumber: 0000:00:1a.0
[    2.191370] hub 1-0:1.0: USB hub found
[    2.191375] hub 1-0:1.0: 2 ports detected
[    2.191454] ehci-pci 0000:00:1d.0: setting latency timer to 64
[    2.191457] ehci-pci 0000:00:1d.0: EHCI Host Controller
[    2.191462] ehci-pci 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    2.191473] ehci-pci 0000:00:1d.0: debug port 2
[    2.195347] ehci-pci 0000:00:1d.0: cache line size of 64 is not supported
[    2.195359] ehci-pci 0000:00:1d.0: irq 20, io mem 0xc3618000
[    2.207185] ehci-pci 0000:00:1d.0: USB 2.0 started, EHCI 1.00
[    2.207206] usb usb2: New USB device found, idVendor=1d6b, idProduct=0002
[    2.207209] usb usb2: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    2.207212] usb usb2: Product: EHCI Host Controller
[    2.207215] usb usb2: Manufacturer: Linux 3.8.0-33-generic ehci_hcd
[    2.207218] usb usb2: SerialNumber: 0000:00:1d.0
[    2.207322] hub 2-0:1.0: USB hub found
[    2.207327] hub 2-0:1.0: 2 ports detected
[    2.207390] ehci-platform: EHCI generic platform driver
[    2.207396] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    2.207406] uhci_hcd: USB Universal Host Controller Interface driver
[    2.207439] xhci_hcd 0000:00:14.0: setting latency timer to 64
[    2.207443] xhci_hcd 0000:00:14.0: xHCI Host Controller
[    2.207446] xhci_hcd 0000:00:14.0: new USB bus registered, assigned bus number 3
[    2.207532] xhci_hcd 0000:00:14.0: cache line size of 64 is not supported
[    2.207572] xhci_hcd 0000:00:14.0: irq 41 for MSI/MSI-X
[    2.207614] usb usb3: New USB device found, idVendor=1d6b, idProduct=0002
[    2.207616] usb usb3: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    2.207617] usb usb3: Product: xHCI Host Controller
[    2.207618] usb usb3: Manufacturer: Linux 3.8.0-33-generic xhci_hcd
[    2.207620] usb usb3: SerialNumber: 0000:00:14.0
[    2.207676] xHCI xhci_add_endpoint called for root hub
[    2.207678] xHCI xhci_check_bandwidth called for root hub
[    2.207692] hub 3-0:1.0: USB hub found
[    2.207699] hub 3-0:1.0: 4 ports detected
[    2.207919] xhci_hcd 0000:00:14.0: xHCI Host Controller
[    2.207922] xhci_hcd 0000:00:14.0: new USB bus registered, assigned bus number 4
[    2.207939] usb usb4: New USB device found, idVendor=1d6b, idProduct=0003
[    2.207941] usb usb4: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    2.207942] usb usb4: Product: xHCI Host Controller
[    2.207943] usb usb4: Manufacturer: Linux 3.8.0-33-generic xhci_hcd
[    2.207945] usb usb4: SerialNumber: 0000:00:14.0
[    2.207997] xHCI xhci_add_endpoint called for root hub
[    2.207998] xHCI xhci_check_bandwidth called for root hub
[    2.208011] hub 4-0:1.0: USB hub found
[    2.208018] hub 4-0:1.0: 4 ports detected
[    2.208309] i8042: PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    2.216116] serio: i8042 KBD port at 0x60,0x64 irq 1
[    2.216121] serio: i8042 AUX port at 0x60,0x64 irq 12
[    2.216212] mousedev: PS/2 mouse device common for all mice
[    2.216341] rtc_cmos 00:05: RTC can wake from S4
[    2.216466] rtc_cmos 00:05: rtc core: registered rtc_cmos as rtc0
[    2.216493] rtc0: alarms up to one month, 242 bytes nvram, hpet irqs
[    2.216552] device-mapper: uevent: version 1.0.3
[    2.216605] device-mapper: ioctl: 4.23.1-ioctl (2012-12-18) initialised: dm-devel@redhat.com
[    2.216672] cpuidle: using governor ladder
[    2.216744] cpuidle: using governor menu
[    2.216749] ledtrig-cpu: registered to indicate activity on CPUs
[    2.216750] EFI Variables Facility v0.08 2004-May-17
[    2.228065] ACPI: Battery Slot [BAT0] (battery present)
[    2.254549] ashmem: initialized
[    2.254642] TCP: cubic registered
[    2.254709] NET: Registered protocol family 10
[    2.254824] NET: Registered protocol family 17
[    2.254831] Key type dns_resolver registered
[    2.255013] Loading module verification certificates
[    2.255773] MODSIGN: Loaded cert 'Magrathea: Glacier signing key: f18b7991d2384529679d61befc4fb536686c75e2'
[    2.255783] registered taskstats version 1
[    2.257534] Key type trusted registered
[    2.258847] Key type encrypted registered
[    2.260608] rtc_cmos 00:05: setting system clock to 2014-03-19 09:12:28 UTC (1395220348)
[    2.261215] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    2.261216] EDD information not available.
[    2.262325] Freeing unused kernel memory: 1016k freed
[    2.262427] Write protecting the kernel read-only data: 12288k
[    2.264386] Freeing unused kernel memory: 1008k freed
[    2.266315] Freeing unused kernel memory: 1008k freed
[    2.276631] udevd[108]: starting version 175
[    2.299352] Disabling lock debugging due to kernel taint
[    2.299838] ahci 0000:00:1f.2: version 3.0
[    2.299892] ahci 0000:00:1f.2: irq 42 for MSI/MSI-X
[    2.314997] ahci 0000:00:1f.2: AHCI 0001.0300 32 slots 6 ports 6 Gbps 0x11 impl SATA mode
[    2.315002] ahci 0000:00:1f.2: flags: 64bit ncq pm led clo pio slum part ems apst 
[    2.315009] ahci 0000:00:1f.2: setting latency timer to 64
[    2.316509] r8101 Fast Ethernet driver 1.024.00-NAPI loaded
[    2.316614] r8101 0000:08:00.0: irq 43 for MSI/MSI-X
[    2.323667] scsi0 : ahci
[    2.323744] scsi1 : ahci
[    2.323803] scsi2 : ahci
[    2.323865] scsi3 : ahci
[    2.324008] scsi4 : ahci
[    2.325382] scsi5 : ahci
[    2.325442] ata1: SATA max UDMA/133 abar m2048@0xc3617000 port 0xc3617100 irq 42
[    2.325444] ata2: DUMMY
[    2.325446] ata3: DUMMY
[    2.325447] ata4: DUMMY
[    2.325450] ata5: SATA max UDMA/133 abar m2048@0xc3617000 port 0xc3617300 irq 42
[    2.325451] ata6: DUMMY
[    2.326785] eth%d: RTL8101E at 0xffffc9000006a000, a0:48:1c:12:ae:93, IRQ 43
[    2.327020] r8101: This product is covered by one or more of the following patents: US6,570,884, US6,115,776, and US6,327,625.
[    2.327022] eth0: Identified chip type is 'RTL8106E'.
[    2.327027] r8101  Copyright (C) 2013  Realtek NIC software team <nicfae@realtek.com> 
[    2.327027]  This program comes with ABSOLUTELY NO WARRANTY; for details, please see <http://www.gnu.org/licenses/>. 
[    2.327027]  This is free software, and you are welcome to redistribute it under certain conditions; see <http://www.gnu.org/licenses/>. 
[    2.502661] usb 1-1: new high-speed USB device number 2 using ehci-pci
[    2.634757] usb 1-1: New USB device found, idVendor=8087, idProduct=0024
[    2.634764] usb 1-1: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[    2.635027] hub 1-1:1.0: USB hub found
[    2.635104] hub 1-1:1.0: 6 ports detected
[    2.642392] ata5: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    2.645639] ata5.00: ATAPI: hp       DVD-RAM UJ8DB, H.02, max UDMA/100
[    2.648128] ata5.00: configured for UDMA/100
[    2.650374] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    2.651854] ata1.00: ATA-9: HGST HTS541075A9E680, JA2OA590, max UDMA/133
[    2.651861] ata1.00: 1465149168 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
[    2.682359] ata1.00: configured for UDMA/133
[    2.682663] scsi 0:0:0:0: Direct-Access     ATA      HGST HTS541075A9 JA2O PQ: 0 ANSI: 5
[    2.682811] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    2.682821] sd 0:0:0:0: [sda] 1465149168 512-byte logical blocks: (750 GB/698 GiB)
[    2.682826] sd 0:0:0:0: [sda] 4096-byte physical blocks
[    2.682900] sd 0:0:0:0: [sda] Write Protect is off
[    2.682903] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.682935] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.685588] scsi 4:0:0:0: CD-ROM            hp       DVD-RAM UJ8DB    H.02 PQ: 0 ANSI: 5
[    2.688956] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[    2.688962] cdrom: Uniform CD-ROM driver Revision: 3.20
[    2.689135] sr 4:0:0:0: Attached scsi CD-ROM sr0
[    2.689202] sr 4:0:0:0: Attached scsi generic sg1 type 5
[    2.723796] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
[    2.746200] usb 2-1: new high-speed USB device number 2 using ehci-pci
[    2.749435]  sda: sda1 sda2 sda3 sda4 sda5 sda6 sda7
[    2.749885] sd 0:0:0:0: [sda] Attached SCSI disk
[    2.878263] usb 2-1: New USB device found, idVendor=8087, idProduct=0024
[    2.878270] usb 2-1: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[    2.878539] hub 2-1:1.0: USB hub found
[    2.878639] hub 2-1:1.0: 6 ports detected
[    3.045618] usb 3-3: new high-speed USB device number 2 using xhci_hcd
[    3.108046] usb 3-3: New USB device found, idVendor=05c8, idProduct=0361
[    3.108052] usb 3-3: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[    3.108056] usb 3-3: Product: HP Truevision HD
[    3.108059] usb 3-3: Manufacturer: SunplusIT INC.
[    3.125470] tsc: Refined TSC clocksource calibration: 2594.107 MHz
[    3.125477] Switching to clocksource tsc
[    3.950074] EXT4-fs (sda6): mounted filesystem with ordered data mode. Opts: (null)
[    5.078828] init: ureadahead main process (274) terminated with status 5
[    5.982994] Adding 2928636k swap on /dev/sda7.  Priority:-1 extents:1 across:2928636k 
[    6.974039] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[    7.088876] udevd[351]: starting version 175
[    7.965953] microcode: CPU0 sig=0x306a9, pf=0x10, revision=0x17
[    8.023043] lp: driver loaded but no devices found
[    8.147779] ACPI Warning: 0x0000000000000428-0x000000000000042f SystemIO conflicts with Region \PMIO 1 (20121018/utaddress-251)
[    8.147785] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[    8.147788] ACPI Warning: 0x0000000000000530-0x000000000000053f SystemIO conflicts with Region \GPIO 1 (20121018/utaddress-251)
[    8.147790] ACPI Warning: 0x0000000000000530-0x000000000000053f SystemIO conflicts with Region \_SB_.PCI0.PEG0.PEGP.GPIO 2 (20121018/utaddress-251)
[    8.147793] ACPI Warning: 0x0000000000000530-0x000000000000053f SystemIO conflicts with Region \_SB_.PCI0.LPCB.GPIO 3 (20121018/utaddress-251)
[    8.147795] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[    8.147796] ACPI Warning: 0x0000000000000500-0x000000000000052f SystemIO conflicts with Region \GPIO 1 (20121018/utaddress-251)
[    8.147798] ACPI Warning: 0x0000000000000500-0x000000000000052f SystemIO conflicts with Region \_SB_.PCI0.PEG0.PEGP.GPIO 2 (20121018/utaddress-251)
[    8.147800] ACPI Warning: 0x0000000000000500-0x000000000000052f SystemIO conflicts with Region \_SB_.PCI0.LPCB.GPIO 3 (20121018/utaddress-251)
[    8.147802] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[    8.147803] lpc_ich: Resource conflict(s) found affecting gpio_ich
[    8.194156] wmi: Mapper loaded
[    8.217974] microcode: CPU1 sig=0x306a9, pf=0x10, revision=0x17
[    8.218936] microcode: CPU2 sig=0x306a9, pf=0x10, revision=0x17
[    8.219802] microcode: CPU3 sig=0x306a9, pf=0x10, revision=0x17
[    8.220750] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[    8.236840] AMD IOMMUv2 driver by Joerg Roedel <joerg.roedel@amd.com>
[    8.236843] AMD IOMMUv2 functionality not available on this system
[    8.245808] input: HP WMI hotkeys as /devices/virtual/input/input4
[    8.247161] hp_accel: laptop model unknown, using default axes configuration
[    8.252179] lis3lv02d: 8 bits 3DC sensor found
[    8.291824] input: ST LIS3LV02DL Accelerometer as /devices/platform/lis3lv02d/input/input5
[    8.543222] mei 0000:00:16.0: setting latency timer to 64
[    8.543286] mei 0000:00:16.0: irq 44 for MSI/MSI-X
[    8.553049] [drm] Initialized drm 1.1.0 20060810
[    8.871060] Loading modules backported from Linux version v3.11-rc3-0-g5ae90d8
[    8.871063] Backport generated by backports.git v3.11-rc3-1-0-g4e81a94
[    9.295412] cfg80211: Calling CRDA to update world regulatory domain
[    9.309360] [drm] Memory usable by graphics device = 2048M
[    9.309363] checking generic (b0000000 410000) vs hw (b0000000 10000000)
[    9.309365] fb: conflicting fb hw usage inteldrmfb vs EFI VGA - removing generic driver
[    9.309387] Console: switching to colour dummy device 80x25
[    9.309429] i915 0000:00:02.0: setting latency timer to 64
[    9.334191] i915 0000:00:02.0: irq 45 for MSI/MSI-X
[    9.334198] [drm] Supports vblank timestamp caching Rev 1 (10.10.2010).
[    9.334199] [drm] Driver supports precise vblank timestamp query.
[    9.334265] vgaarb: device changed decodes: PCI:0000:00:02.0,olddecodes=io+mem,decodes=io+mem:owns=io+mem
[    9.496610] psmouse serio1: synaptics: Touchpad model: 1, fw: 7.5, id: 0x1c0b1, caps: 0xf00133/0x240000/0xa2400, board id: 2665, fw id: 1458825
[    9.513436] [drm] failed to retrieve link info, disabling eDP
[    9.534002] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input6
[    9.636137] fbcon: inteldrmfb (fb0) is primary device
[    9.922016] Linux video capture interface: v2.00
[    9.935814] rtl8188ee: Using firmware rtlwifi/rtl8188efw.bin
[   10.149106] uvcvideo: Found UVC 1.00 device HP Truevision HD (05c8:0361)
[   10.157509] input: HP Truevision HD as /devices/pci0000:00/0000:00:14.0/usb3/3-3/3-3:1.0/input/input7
[   10.157570] usbcore: registered new interface driver uvcvideo
[   10.157571] USB Video Class driver (1.1.1)
[   10.287269] ieee80211 phy0: Selected rate control algorithm 'rtl_rc'
[   10.287419] rtlwifi: wireless switch is on
[   10.367942] Console: switching to colour frame buffer device 170x48
[   10.369664] i915 0000:00:02.0: fb0: inteldrmfb frame buffer device
[   10.369666] i915 0000:00:02.0: registered panic notifier
[   10.369799] [Firmware Bug]: ACPI(PEGP) defines _DOD but not _DOS
[   10.370421] ACPI Error: Too many duplicates in _BCL package
[   10.370424]  (20121018/video-724)
[   10.371061] acpi device:04: registered as cooling_device4
[   10.371211] ACPI: Video Device [PEGP] (multi-head: yes  rom: no  post: no)
[   10.371247] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:02/LNXVIDEO:00/input/input8
[   10.372137] ACPI Error: Too many duplicates in _BCL package
[   10.372140]  (20121018/video-724)
[   10.372675] acpi device:0e: registered as cooling_device5
[   10.372801] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
[   10.372833] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/LNXVIDEO:01/input/input9
[   10.372897] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[   10.372997] snd_hda_intel 0000:00:1b.0: irq 46 for MSI/MSI-X
[   10.495769] input: HDA Intel PCH HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:1b.0/sound/card0/input10
[   10.495838] input: HDA Intel PCH Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input11
[   10.495897] input: HDA Intel PCH Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card0/input12
[   10.656391] type=1400 audit(1395216756.907:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=817 comm="apparmor_parser"
[   10.656435] type=1400 audit(1395216756.907:3): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=706 comm="apparmor_parser"
[   10.656442] type=1400 audit(1395216756.907:4): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=707 comm="apparmor_parser"
[   10.656697] type=1400 audit(1395216756.907:5): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=817 comm="apparmor_parser"
[   10.656833] type=1400 audit(1395216756.907:6): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=706 comm="apparmor_parser"
[   10.656845] type=1400 audit(1395216756.907:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=707 comm="apparmor_parser"
[   10.656866] type=1400 audit(1395216756.907:8): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=817 comm="apparmor_parser"
[   10.657041] type=1400 audit(1395216756.907:9): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=706 comm="apparmor_parser"
[   10.657049] type=1400 audit(1395216756.907:10): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=707 comm="apparmor_parser"
[   10.827259] [drm] Enabling RC6 states: RC6 on, RC6p on, RC6pp off
[   10.934675] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
[   10.940968] <6>[fglrx] Maximum main memory to use for locked dma buffers: 7647 MBytes.
[   10.941076] <6>[fglrx]   vendor: 1002 device: 6660 count: 1
[   10.941239] <6>[fglrx] ioport: bar 4, base 0x5000, size: 0x100
[   10.941245] pci 0000:01:00.0: enabling device (0000 -> 0003)
[   10.941328] <6>[fglrx] Kernel PAT support is enabled
[   10.941340] <6>[fglrx] module loaded - fglrx 13.10.10 [May 23 2013] with 1 minors
[   11.939185] EXT4-fs (sda6): re-mounted. Opts: errors=remount-ro
[   13.926807] init: failsafe main process (936) killed by TERM signal
[   14.753237] type=1400 audit(1395216761.011:11): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=1005 comm="apparmor_parser"
[   15.016866] ppdev: user-space parallel port driver
[   15.845436] Bluetooth: Core ver 2.16
[   15.845454] NET: Registered protocol family 31
[   15.845456] Bluetooth: HCI device and connection manager initialized
[   15.845463] Bluetooth: HCI socket layer initialized
[   15.845466] Bluetooth: L2CAP socket layer initialized
[   15.845470] Bluetooth: SCO socket layer initialized
[   16.120855] Bluetooth: RFCOMM TTY layer initialized
[   16.120866] Bluetooth: RFCOMM socket layer initialized
[   16.120868] Bluetooth: RFCOMM ver 1.11
[   16.158002] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   16.158004] Bluetooth: BNEP filters: protocol multicast
[   16.158011] Bluetooth: BNEP socket layer initialized
[   16.743594] vboxdrv: Found 4 processor cores.
[   16.743777] vboxdrv: fAsync=0 offMin=0x194 offMax=0x1f4e
[   16.743821] vboxdrv: TSC mode is 'synchronous', kernel timer mode is 'normal'.
[   16.743822] vboxdrv: Successfully loaded version 4.1.12_Ubuntu (interface 0x00190000).
[   17.101712] vboxpci: IOMMU not found (not registered)
[   19.319253] init: plymouth-stop pre-start process (1339) terminated with status 1
[   19.876663] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   19.876872] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   20.035846] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   20.036062] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   20.353427] fglrx_pci 0000:01:00.0: irq 47 for MSI/MSI-X
[   20.353822] <6>[fglrx] Firegl kernel thread PID: 1348
[   20.353934] <6>[fglrx] Firegl kernel thread PID: 1349
[   20.354045] <6>[fglrx] Firegl kernel thread PID: 1350
[   20.354103] <6>[fglrx] IRQ 47 Enabled
[   20.362415] <6>[fglrx] Reserved FB block: Shared offset:0, size:1000000 
[   20.362417] <6>[fglrx] Reserved FB block: Unshared offset:f87c000, size:484000 
[   20.362418] <6>[fglrx] Reserved FB block: Unshared offset:7fff4000, size:c000 
[   20.558077] vgaarb: this pci device is not a vga device
[   22.394791] wlan0: authenticate with 00:07:7d:d3:3c:42
[   22.413520] wlan0: direct probe to 00:07:7d:d3:3c:42 (try 1/3)
[   22.616796] wlan0: direct probe to 00:07:7d:d3:3c:42 (try 2/3)
[   22.820459] wlan0: direct probe to 00:07:7d:d3:3c:42 (try 3/3)
[   23.024072] wlan0: authentication with 00:07:7d:d3:3c:42 timed out
[   24.451672] vgaarb: this pci device is not a vga device
[   29.244674] wlan0: authenticate with 00:13:60:ef:73:c2
[   29.264577] wlan0: send auth to 00:13:60:ef:73:c2 (try 1/3)
[   29.265655] wlan0: authenticated
[   29.268327] wlan0: associate with 00:13:60:ef:73:c2 (try 1/3)
[   29.270508] wlan0: RX AssocResp from 00:13:60:ef:73:c2 (capab=0x31 status=0 aid=88)
[   29.270680] wlan0: associated
[   29.270687] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   56.783661] audit_printk_skb: 57 callbacks suppressed
[   56.783663] type=1400 audit(1395216803.127:31): apparmor="DENIED" operation="open" parent=1 profile="/usr/lib/telepathy/mission-control-5" name="/usr/share/gvfs/remote-volume-monitors/" pid=2115 comm="mission-control" requested_mask="r" denied_mask="r" fsuid=1000 ouid=0
[  339.470628] wlan0: authenticate with 70:81:05:45:6b:82
[  339.480810] wlan0: send auth to 70:81:05:45:6b:82 (try 1/3)
[  339.481072] cfg80211: Calling CRDA for country: IT
[  339.482019] wlan0: authenticated
[  339.487820] wlan0: associate with 70:81:05:45:6b:82 (try 1/3)
[  339.489514] wlan0: RX AssocResp from 70:81:05:45:6b:82 (capab=0x31 status=0 aid=9)
[  339.489689] wlan0: associated
[  404.675488] wlan0: authenticate with 00:07:7d:d3:3c:42
[  404.675615] wlan0: direct probe to 00:07:7d:d3:3c:42 (try 1/3)
[  404.675753] cfg80211: Calling CRDA to update world regulatory domain
[  404.876115] wlan0: direct probe to 00:07:7d:d3:3c:42 (try 2/3)
[  405.079625] wlan0: direct probe to 00:07:7d:d3:3c:42 (try 3/3)
[  405.283178] wlan0: authentication with 00:07:7d:d3:3c:42 timed out
[  411.497599] wlan0: authenticate with 00:13:60:ef:73:c2
[  411.516773] wlan0: send auth to 00:13:60:ef:73:c2 (try 1/3)
[  411.517897] wlan0: authenticated
[  411.520311] wlan0: associate with 00:13:60:ef:73:c2 (try 1/3)
[  411.524292] wlan0: RX AssocResp from 00:13:60:ef:73:c2 (capab=0x31 status=0 aid=91)
[  411.524466] wlan0: associated
[  503.511950] wlan0: authenticate with 70:81:05:45:6b:82
[  503.522133] wlan0: send auth to 70:81:05:45:6b:82 (try 1/3)
[  503.522253] cfg80211: Calling CRDA to update world regulatory domain
[  503.524206] wlan0: authenticated
[  503.525223] wlan0: associate with 70:81:05:45:6b:82 (try 1/3)
[  503.529694] wlan0: RX AssocResp from 70:81:05:45:6b:82 (capab=0x31 status=0 aid=4)
[  503.529867] wlan0: associated
[  628.498403] wlan0: authenticate with 00:13:60:ef:73:c2
[  628.508600] wlan0: send auth to 00:13:60:ef:73:c2 (try 1/3)
[  628.508725] cfg80211: Calling CRDA for country: IT
[  628.510783] wlan0: authenticated
[  628.511615] wlan0: associate with 00:13:60:ef:73:c2 (try 1/3)
[  628.514223] wlan0: RX AssocResp from 00:13:60:ef:73:c2 (capab=0x31 status=0 aid=93)
[  628.514402] wlan0: associated
[  643.470819] wlan0: authenticate with 70:81:05:45:6b:82
[  643.480986] wlan0: send auth to 70:81:05:45:6b:82 (try 1/3)
[  643.481568] cfg80211: Calling CRDA to update world regulatory domain
[  643.485698] wlan0: authenticated
[  643.487920] wlan0: associate with 70:81:05:45:6b:82 (try 1/3)
[  643.491247] wlan0: RX AssocResp from 70:81:05:45:6b:82 (capab=0x31 status=0 aid=4)
[  643.491433] wlan0: associated
[  711.848003] wlan0: authenticate with 00:13:60:ef:73:c2
[  711.858190] wlan0: send auth to 00:13:60:ef:73:c2 (try 1/3)
[  711.858413] cfg80211: Calling CRDA for country: IT
[  711.859197] wlan0: authenticated
[  711.861116] wlan0: associate with 00:13:60:ef:73:c2 (try 1/3)
[  711.863572] wlan0: RX AssocResp from 00:13:60:ef:73:c2 (capab=0x31 status=0 aid=94)
[  711.863748] wlan0: associated
[  805.840112] wlan0: authenticate with 00:17:59:fb:bb:d2
[  805.850278] wlan0: send auth to 00:17:59:fb:bb:d2 (try 1/3)
[  805.850431] cfg80211: Calling CRDA to update world regulatory domain
[  805.851970] wlan0: authenticated
[  805.853281] wlan0: associate with 00:17:59:fb:bb:d2 (try 1/3)
[  805.855200] wlan0: RX AssocResp from 00:17:59:fb:bb:d2 (capab=0x31 status=0 aid=173)
[  805.855378] wlan0: associated
[  827.229202] wlan0: authenticate with 70:81:05:45:6b:82
[  827.239363] wlan0: send auth to 70:81:05:45:6b:82 (try 1/3)
[  827.239521] cfg80211: Calling CRDA to update world regulatory domain
[  827.241721] wlan0: authenticated
[  827.242594] wlan0: associate with 70:81:05:45:6b:82 (try 1/3)
[  827.247466] wlan0: RX AssocResp from 70:81:05:45:6b:82 (capab=0x31 status=0 aid=4)
[  827.247641] wlan0: associated
[  877.345912] wlan0: authenticate with 00:07:7d:d3:3c:42
[  877.346043] wlan0: direct probe to 00:07:7d:d3:3c:42 (try 1/3)
[  877.347485] cfg80211: Calling CRDA for country: IT
[  877.546585] wlan0: send auth to 00:07:7d:d3:3c:42 (try 2/3)
[  890.431170] type=1400 audit(1395217638.761:32): apparmor="DENIED" operation="capable" parent=1 profile="/usr/sbin/cupsd" pid=1036 comm="cupsd" pid=1036 comm="cupsd" capability=36  capname="block_suspend"
[ 1443.592862] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
```

lsmod
```
Module                  Size  Used by
pci_stub               12622  1 
vboxpci                23236  0 
vboxnetadp             13382  0 
vboxnetflt             23478  0 
vboxdrv               283008  3 vboxpci,vboxnetadp,vboxnetflt
bnep                   18258  2 
rfcomm                 47864  4 
bluetooth             247165  10 bnep,rfcomm
parport_pc             28284  0 
ppdev                  17113  0 
nls_iso8859_1          12713  1 
fglrx                6728820  145 
snd_hda_codec_hdmi     37463  1 
snd_hda_codec_realtek    79916  1 
arc4                   12573  2 
uvcvideo               82214  0 
videobuf2_core         40785  1 uvcvideo
rtl8188ee             137586  0 
videodev              130053  2 uvcvideo,videobuf2_core
snd_hda_intel          44339  3 
rtlwifi               120562  1 rtl8188ee
videobuf2_vmalloc      13056  1 uvcvideo
videobuf2_memops       13202  1 videobuf2_vmalloc
snd_hda_codec         141761  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
mac80211              555015  2 rtl8188ee,rtlwifi
coretemp               13596  0 
snd_hwdep              13668  1 snd_hda_codec
snd_pcm               102477  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
kvm_intel             137899  0 
snd_seq_midi           13324  0 
snd_rawmidi            30417  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
i915                  620571  2 
kvm                   455932  1 kvm_intel
cfg80211              549566  2 rtlwifi,mac80211
snd_seq                61930  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29989  2 snd_pcm,snd_seq
snd_seq_device         14497  3 snd_seq_midi,snd_rawmidi,snd_seq
compat                 15085  4 rtl8188ee,rtlwifi,mac80211,cfg80211
ghash_clmulni_intel    13259  0 
psmouse                97873  0 
drm_kms_helper         49597  1 i915
drm                   287564  3 i915,drm_kms_helper
mei                    41820  0 
snd                    69533  16 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
aesni_intel            55495  0 
ablk_helper            13597  1 aesni_intel
cryptd                 20501  3 ghash_clmulni_intel,aesni_intel,ablk_helper
lrw                    13294  1 aesni_intel
aes_x86_64             17255  1 aesni_intel
xts                    12922  1 aesni_intel
gf128mul               14951  2 lrw,xts
joydev                 17613  0 
hp_accel               26012  0 
hp_wmi                 18092  0 
amd_iommu_v2           19198  1 fglrx
lis3lv02d              20200  1 hp_accel
i2c_algo_bit           13564  1 i915
sparse_keymap          13890  1 hp_wmi
serio_raw              13215  0 
wmi                    19256  1 hp_wmi
soundcore              12680  1 snd
input_polldev          13896  1 lis3lv02d
snd_page_alloc         18798  2 snd_hda_intel,snd_pcm
video                  19652  1 i915
lpc_ich                17144  0 
mac_hid                13253  0 
microcode              23017  0 
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
r8101                 111980  0 
ahci                   25879  3 
libahci                31606  1 ahci
```

modprobe
```
kernel/arch/x86/kernel/cpu/mcheck/mce-inject.ko
kernel/arch/x86/kernel/msr.ko
kernel/arch/x86/kernel/cpuid.ko
kernel/arch/x86/kernel/microcode.ko
kernel/arch/x86/crypto/ablk_helper.ko
kernel/arch/x86/crypto/glue_helper.ko
kernel/arch/x86/crypto/aes-x86_64.ko
kernel/arch/x86/crypto/camellia-x86_64.ko
kernel/arch/x86/crypto/camellia-aesni-avx-x86_64.ko
kernel/arch/x86/crypto/cast5-avx-x86_64.ko
kernel/arch/x86/crypto/cast6-avx-x86_64.ko
kernel/arch/x86/crypto/blowfish-x86_64.ko
kernel/arch/x86/crypto/twofish-x86_64.ko
kernel/arch/x86/crypto/twofish-x86_64-3way.ko
kernel/arch/x86/crypto/twofish-avx-x86_64.ko
kernel/arch/x86/crypto/salsa20-x86_64.ko
kernel/arch/x86/crypto/serpent-sse2-x86_64.ko
kernel/arch/x86/crypto/serpent-avx-x86_64.ko
kernel/arch/x86/crypto/aesni-intel.ko
kernel/arch/x86/crypto/ghash-clmulni-intel.ko
kernel/arch/x86/crypto/sha1-ssse3.ko
kernel/arch/x86/kvm/kvm.ko
kernel/arch/x86/kvm/kvm-intel.ko
kernel/arch/x86/kvm/kvm-amd.ko
kernel/mm/hwpoison-inject.ko
kernel/fs/nfs_common/nfs_acl.ko
kernel/fs/quota/quota_v1.ko
kernel/fs/quota/quota_v2.ko
kernel/fs/quota/quota_tree.ko
kernel/fs/fat/msdos.ko
kernel/fs/nls/nls_cp737.ko
kernel/fs/nls/nls_cp775.ko
kernel/fs/nls/nls_cp850.ko
kernel/fs/nls/nls_cp852.ko
kernel/fs/nls/nls_cp855.ko
kernel/fs/nls/nls_cp857.ko
kernel/fs/nls/nls_cp860.ko
kernel/fs/nls/nls_cp861.ko
kernel/fs/nls/nls_cp862.ko
kernel/fs/nls/nls_cp863.ko
kernel/fs/nls/nls_cp864.ko
kernel/fs/nls/nls_cp865.ko
kernel/fs/nls/nls_cp866.ko
kernel/fs/nls/nls_cp869.ko
kernel/fs/nls/nls_cp874.ko
kernel/fs/nls/nls_cp932.ko
kernel/fs/nls/nls_euc-jp.ko
kernel/fs/nls/nls_cp936.ko
kernel/fs/nls/nls_cp949.ko
kernel/fs/nls/nls_cp950.ko
kernel/fs/nls/nls_cp1250.ko
kernel/fs/nls/nls_cp1251.ko
kernel/fs/nls/nls_ascii.ko
kernel/fs/nls/nls_iso8859-1.ko
kernel/fs/nls/nls_iso8859-2.ko
kernel/fs/nls/nls_iso8859-3.ko
kernel/fs/nls/nls_iso8859-4.ko
kernel/fs/nls/nls_iso8859-5.ko
kernel/fs/nls/nls_iso8859-6.ko
kernel/fs/nls/nls_iso8859-7.ko
kernel/fs/nls/nls_cp1255.ko
kernel/fs/nls/nls_iso8859-9.ko
kernel/fs/nls/nls_iso8859-13.ko
kernel/fs/nls/nls_iso8859-14.ko
kernel/fs/nls/nls_iso8859-15.ko
kernel/fs/nls/nls_koi8-r.ko
kernel/fs/nls/nls_koi8-u.ko
kernel/fs/nls/nls_koi8-ru.ko
kernel/fs/nls/nls_utf8.ko
kernel/fs/nls/mac-celtic.ko
kernel/fs/nls/mac-centeuro.ko
kernel/fs/nls/mac-croatian.ko
kernel/fs/nls/mac-cyrillic.ko
kernel/fs/nls/mac-gaelic.ko
kernel/fs/nls/mac-greek.ko
kernel/fs/nls/mac-iceland.ko
kernel/fs/nls/mac-inuit.ko
kernel/fs/nls/mac-romanian.ko
kernel/fs/nls/mac-roman.ko
kernel/fs/nls/mac-turkish.ko
kernel/fs/fuse/cuse.ko
kernel/fs/exofs/libore.ko
kernel/fs/exofs/exofs.ko
kernel/fs/pstore/ramoops.ko
kernel/fs/binfmt_misc.ko
kernel/fs/configfs/configfs.ko
kernel/fs/dlm/dlm.ko
kernel/fs/fscache/fscache.ko
kernel/fs/reiserfs/reiserfs.ko
kernel/fs/ext2/ext2.ko
kernel/fs/cramfs/cramfs.ko
kernel/fs/squashfs/squashfs.ko
kernel/fs/coda/coda.ko
kernel/fs/minix/minix.ko
kernel/fs/bfs/bfs.ko
kernel/fs/isofs/isofs.ko
kernel/fs/hfsplus/hfsplus.ko
kernel/fs/hfs/hfs.ko
kernel/fs/freevxfs/freevxfs.ko
kernel/fs/nfs/nfs.ko
kernel/fs/nfs/nfsv2.ko
kernel/fs/nfs/nfsv3.ko
kernel/fs/nfs/nfsv4.ko
kernel/fs/nfs/nfs_layout_nfsv41_files.ko
kernel/fs/nfs/objlayout/objlayoutdriver.ko
kernel/fs/nfs/blocklayout/blocklayoutdriver.ko
kernel/fs/nfsd/nfsd.ko
kernel/fs/lockd/lockd.ko
kernel/fs/sysv/sysv.ko
kernel/fs/cifs/cifs.ko
kernel/fs/ncpfs/ncpfs.ko
kernel/fs/hpfs/hpfs.ko
kernel/fs/ntfs/ntfs.ko
kernel/fs/ufs/ufs.ko
kernel/fs/efs/efs.ko
kernel/fs/jffs2/jffs2.ko
kernel/fs/ubifs/ubifs.ko
kernel/fs/affs/affs.ko
kernel/fs/romfs/romfs.ko
kernel/fs/qnx4/qnx4.ko
kernel/fs/qnx6/qnx6.ko
kernel/fs/autofs4/autofs4.ko
kernel/fs/adfs/adfs.ko
kernel/fs/overlayfs/overlayfs.ko
kernel/fs/udf/udf.ko
kernel/fs/omfs/omfs.ko
kernel/fs/jfs/jfs.ko
kernel/fs/xfs/xfs.ko
kernel/fs/9p/9p.ko
kernel/fs/afs/kafs.ko
kernel/fs/nilfs2/nilfs2.ko
kernel/fs/befs/befs.ko
kernel/fs/cachefiles/cachefiles.ko
kernel/fs/ocfs2/ocfs2.ko
kernel/fs/ocfs2/ocfs2_stackglue.ko
kernel/fs/ocfs2/ocfs2_stack_o2cb.ko
kernel/fs/ocfs2/ocfs2_stack_user.ko
kernel/fs/ocfs2/dlmfs/ocfs2_dlmfs.ko
kernel/fs/ocfs2/cluster/ocfs2_nodemanager.ko
kernel/fs/ocfs2/dlm/ocfs2_dlm.ko
kernel/fs/btrfs/btrfs.ko
kernel/fs/gfs2/gfs2.ko
kernel/fs/f2fs/f2fs.ko
kernel/fs/ceph/ceph.ko
kernel/crypto/seqiv.ko
kernel/crypto/crypto_user.ko
kernel/crypto/vmac.ko
kernel/crypto/xcbc.ko
kernel/crypto/crypto_null.ko
kernel/crypto/md4.ko
kernel/crypto/rmd128.ko
kernel/crypto/rmd160.ko
kernel/crypto/rmd256.ko
kernel/crypto/rmd320.ko
kernel/crypto/wp512.ko
kernel/crypto/tgr192.ko
kernel/crypto/gf128mul.ko
kernel/crypto/pcbc.ko
kernel/crypto/cts.ko
kernel/crypto/lrw.ko
kernel/crypto/xts.ko
kernel/crypto/ctr.ko
kernel/crypto/gcm.ko
kernel/crypto/ccm.ko
kernel/crypto/pcrypt.ko
kernel/crypto/cryptd.ko
kernel/crypto/des_generic.ko
kernel/crypto/fcrypt.ko
kernel/crypto/blowfish_generic.ko
kernel/crypto/blowfish_common.ko
kernel/crypto/twofish_generic.ko
kernel/crypto/twofish_common.ko
kernel/crypto/serpent_generic.ko
kernel/crypto/camellia_generic.ko
kernel/crypto/cast_common.ko
kernel/crypto/cast5_generic.ko
kernel/crypto/cast6_generic.ko
kernel/crypto/arc4.ko
kernel/crypto/tea.ko
kernel/crypto/khazad.ko
kernel/crypto/anubis.ko
kernel/crypto/seed.ko
kernel/crypto/salsa20_generic.ko
kernel/crypto/deflate.ko
kernel/crypto/zlib.ko
kernel/crypto/michael_mic.ko
kernel/crypto/authenc.ko
kernel/crypto/authencesn.ko
kernel/crypto/ansi_cprng.ko
kernel/crypto/tcrypt.ko
kernel/crypto/ghash-generic.ko
kernel/crypto/af_alg.ko
kernel/crypto/algif_hash.ko
kernel/crypto/algif_skcipher.ko
kernel/crypto/xor.ko
kernel/crypto/async_tx/async_tx.ko
kernel/crypto/async_tx/async_memcpy.ko
kernel/crypto/async_tx/async_xor.ko
kernel/crypto/async_tx/async_pq.ko
kernel/crypto/async_tx/async_raid6_recov.ko
kernel/crypto/async_tx/raid6test.ko
kernel/drivers/gpio/gpio-generic.ko
kernel/drivers/gpio/gpio-74x164.ko
kernel/drivers/gpio/gpio-adp5520.ko
kernel/drivers/gpio/gpio-adp5588.ko
kernel/drivers/gpio/gpio-amd8111.ko
kernel/drivers/gpio/gpio-arizona.ko
kernel/drivers/gpio/gpio-cs5535.ko
kernel/drivers/gpio/gpio-da9052.ko
kernel/drivers/gpio/gpio-da9055.ko
kernel/drivers/gpio/gpio-ich.ko
kernel/drivers/gpio/gpio-it8761e.ko
kernel/drivers/gpio/gpio-janz-ttl.ko
kernel/drivers/gpio/gpio-max730x.ko
kernel/drivers/gpio/gpio-max7300.ko
kernel/drivers/gpio/gpio-max7301.ko
kernel/drivers/gpio/gpio-max732x.ko
kernel/drivers/gpio/gpio-mc33880.ko
kernel/drivers/gpio/gpio-mcp23s08.ko
kernel/drivers/gpio/gpio-ml-ioh.ko
kernel/drivers/gpio/gpio-pca953x.ko
kernel/drivers/gpio/gpio-pcf857x.ko
kernel/drivers/gpio/gpio-pch.ko
kernel/drivers/gpio/gpio-rdc321x.ko
kernel/drivers/gpio/gpio-sch.ko
kernel/drivers/gpio/gpio-tps65912.ko
kernel/drivers/gpio/gpio-ts5500.ko
kernel/drivers/gpio/gpio-twl4030.ko
kernel/drivers/gpio/gpio-twl6040.ko
kernel/drivers/gpio/gpio-viperboard.ko
kernel/drivers/gpio/gpio-vx855.ko
kernel/drivers/gpio/gpio-wm831x.ko
kernel/drivers/gpio/gpio-wm8350.ko
kernel/drivers/gpio/gpio-wm8994.ko
kernel/drivers/pwm/pwm-twl.ko
kernel/drivers/pwm/pwm-twl-led.ko
kernel/drivers/pci/hotplug/cpcihp_zt5550.ko
kernel/drivers/pci/hotplug/cpcihp_generic.ko
kernel/drivers/pci/hotplug/shpchp.ko
kernel/drivers/pci/hotplug/acpiphp.ko
kernel/drivers/pci/hotplug/acpiphp_ibm.ko
kernel/drivers/pci/pci-stub.ko
kernel/drivers/pci/xen-pcifront.ko
kernel/drivers/video/backlight/lcd.ko
kernel/drivers/video/backlight/l4f00242t03.ko
kernel/drivers/video/backlight/lms283gf05.ko
kernel/drivers/video/backlight/ltv350qv.ko
kernel/drivers/video/backlight/ili9320.ko
kernel/drivers/video/backlight/platform_lcd.ko
kernel/drivers/video/backlight/vgg2432a4.ko
kernel/drivers/video/backlight/tdo24m.ko
kernel/drivers/video/backlight/s6e63m0.ko
kernel/drivers/video/backlight/ld9040.ko
kernel/drivers/video/backlight/ams369fg06.ko
kernel/drivers/video/backlight/generic_bl.ko
kernel/drivers/video/backlight/lm3533_bl.ko
kernel/drivers/video/backlight/lm3630_bl.ko
kernel/drivers/video/backlight/lm3639_bl.ko
kernel/drivers/video/backlight/lp855x_bl.ko
kernel/drivers/video/backlight/pandora_bl.ko
kernel/drivers/video/backlight/cr_bllcd.ko
kernel/drivers/video/backlight/pwm_bl.ko
kernel/drivers/video/backlight/da903x_bl.ko
kernel/drivers/video/backlight/da9052_bl.ko
kernel/drivers/video/backlight/max8925_bl.ko
kernel/drivers/video/backlight/apple_bl.ko
kernel/drivers/video/backlight/kb3886_bl.ko
kernel/drivers/video/backlight/wm831x_bl.ko
kernel/drivers/video/backlight/adp5520_bl.ko
kernel/drivers/video/backlight/adp8860_bl.ko
kernel/drivers/video/backlight/adp8870_bl.ko
kernel/drivers/video/backlight/88pm860x_bl.ko
kernel/drivers/video/backlight/pcf50633-backlight.ko
kernel/drivers/video/backlight/aat2870_bl.ko
kernel/drivers/video/backlight/tps65217_bl.ko
kernel/drivers/video/geode/gx1fb.ko
kernel/drivers/video/geode/gxfb.ko
kernel/drivers/video/geode/lxfb.ko
kernel/drivers/video/vgastate.ko
kernel/drivers/video/sysfillrect.ko
kernel/drivers/video/syscopyarea.ko
kernel/drivers/video/sysimgblt.ko
kernel/drivers/video/fb_sys_fops.ko
kernel/drivers/video/svgalib.ko
kernel/drivers/video/fb_ddc.ko
kernel/drivers/video/arcfb.ko
kernel/drivers/video/cyber2000fb.ko
kernel/drivers/video/pm2fb.ko
kernel/drivers/video/pm3fb.ko
kernel/drivers/video/i740fb.ko
kernel/drivers/video/matrox/matroxfb_base.ko
kernel/drivers/video/matrox/matroxfb_accel.ko
kernel/drivers/video/matrox/matroxfb_DAC1064.ko
kernel/drivers/video/matrox/matroxfb_Ti3026.ko
kernel/drivers/video/matrox/matroxfb_misc.ko
kernel/drivers/video/matrox/g450_pll.ko
kernel/drivers/video/matrox/matroxfb_g450.ko
kernel/drivers/video/matrox/matroxfb_crtc2.ko
kernel/drivers/video/matrox/i2c-matroxfb.ko
kernel/drivers/video/matrox/matroxfb_maven.ko
kernel/drivers/video/riva/rivafb.ko
kernel/drivers/video/nvidia/nvidiafb.ko
kernel/drivers/video/aty/atyfb.ko
kernel/drivers/video/aty/aty128fb.ko
kernel/drivers/video/aty/radeonfb.ko
kernel/drivers/video/macmodes.ko
kernel/drivers/video/sis/sisfb.ko
kernel/drivers/video/via/viafb.ko
kernel/drivers/video/kyro/kyrofb.ko
kernel/drivers/video/savage/savagefb.ko
kernel/drivers/video/neofb.ko
kernel/drivers/video/tdfxfb.ko
kernel/drivers/video/vt8623fb.ko
kernel/drivers/video/tridentfb.ko
kernel/drivers/video/vermilion/vmlfb.ko
kernel/drivers/video/vermilion/crvml.ko
kernel/drivers/video/s3fb.ko
kernel/drivers/video/arkfb.ko
kernel/drivers/video/hecubafb.ko
kernel/drivers/video/n411.ko
kernel/drivers/video/hgafb.ko
kernel/drivers/video/sstfb.ko
kernel/drivers/video/cirrusfb.ko
kernel/drivers/video/tmiofb.ko
kernel/drivers/video/metronomefb.ko
kernel/drivers/video/broadsheetfb.ko
kernel/drivers/video/auo_k190x.ko
kernel/drivers/video/auo_k1900fb.ko
kernel/drivers/video/auo_k1901fb.ko
kernel/drivers/video/s1d13xxxfb.ko
kernel/drivers/video/sm501fb.ko
kernel/drivers/video/udlfb.ko
kernel/drivers/video/smscufx.ko
kernel/drivers/video/xen-fbfront.ko
kernel/drivers/video/carminefb.ko
kernel/drivers/video/mb862xx/mb862xxfb.ko
kernel/drivers/video/uvesafb.ko
kernel/drivers/video/vga16fb.ko
kernel/drivers/video/output.ko
kernel/drivers/idle/i7300_idle.ko
kernel/drivers/acpi/apei/einj.ko
kernel/drivers/acpi/acpi_ipmi.ko
kernel/drivers/acpi/video.ko
kernel/drivers/acpi/pci_slot.ko
kernel/drivers/acpi/acpi_memhotplug.ko
kernel/drivers/acpi/sbshc.ko
kernel/drivers/acpi/sbs.ko
kernel/drivers/acpi/ec_sys.ko
kernel/drivers/acpi/acpi_pad.ko
kernel/drivers/dma/intel_mid_dma.ko
kernel/drivers/dma/ioat/ioatdma.ko
kernel/drivers/dma/dw_dmac.ko
kernel/drivers/dma/timb_dma.ko
kernel/drivers/dma/pch_dma.ko
kernel/drivers/virtio/virtio_mmio.ko
kernel/drivers/virtio/virtio_balloon.ko
kernel/drivers/xen/xen-evtchn.ko
kernel/drivers/xen/xen-gntdev.ko
kernel/drivers/xen/xen-gntalloc.ko
kernel/drivers/xen/xenfs/xenfs.ko
kernel/drivers/xen/xen-pciback/xen-pciback.ko
kernel/drivers/xen/xen-privcmd.ko
kernel/drivers/regulator/fixed.ko
kernel/drivers/regulator/virtual.ko
kernel/drivers/regulator/userspace-consumer.ko
kernel/drivers/regulator/aat2870-regulator.ko
kernel/drivers/regulator/ab3100.ko
kernel/drivers/regulator/ad5398.ko
kernel/drivers/regulator/arizona-micsupp.ko
kernel/drivers/regulator/arizona-ldo1.ko
kernel/drivers/regulator/as3711-regulator.ko
kernel/drivers/regulator/da903x.ko
kernel/drivers/regulator/da9052-regulator.ko
kernel/drivers/regulator/da9055-regulator.ko
kernel/drivers/regulator/fan53555.ko
kernel/drivers/regulator/gpio-regulator.ko
kernel/drivers/regulator/isl6271a-regulator.ko
kernel/drivers/regulator/lp3971.ko
kernel/drivers/regulator/lp3972.ko
kernel/drivers/regulator/max1586.ko
kernel/drivers/regulator/max8649.ko
kernel/drivers/regulator/max8660.ko
kernel/drivers/regulator/max8907-regulator.ko
kernel/drivers/regulator/max8925-regulator.ko
kernel/drivers/regulator/max8952.ko
kernel/drivers/regulator/max8973-regulator.ko
kernel/drivers/regulator/max8997.ko
kernel/drivers/regulator/max8998.ko
kernel/drivers/regulator/max77686.ko
kernel/drivers/regulator/mc13783-regulator.ko
kernel/drivers/regulator/mc13892-regulator.ko
kernel/drivers/regulator/mc13xxx-regulator-core.ko
kernel/drivers/regulator/palmas-regulator.ko
kernel/drivers/regulator/tps51632-regulator.ko
kernel/drivers/regulator/pcap-regulator.ko
kernel/drivers/regulator/pcf50633-regulator.ko
kernel/drivers/regulator/rc5t583-regulator.ko
kernel/drivers/regulator/s2mps11.ko
kernel/drivers/regulator/s5m8767.ko
kernel/drivers/regulator/tps6105x-regulator.ko
kernel/drivers/regulator/tps62360-regulator.ko
kernel/drivers/regulator/tps65023-regulator.ko
kernel/drivers/regulator/tps6507x-regulator.ko
kernel/drivers/regulator/tps65090-regulator.ko
kernel/drivers/regulator/tps65217-regulator.ko
kernel/drivers/regulator/tps6524x-regulator.ko
kernel/drivers/regulator/tps6586x-regulator.ko
kernel/drivers/regulator/tps65910-regulator.ko
kernel/drivers/regulator/tps65912-regulator.ko
kernel/drivers/regulator/tps80031-regulator.ko
kernel/drivers/regulator/wm831x-dcdc.ko
kernel/drivers/regulator/wm831x-isink.ko
kernel/drivers/regulator/wm831x-ldo.ko
kernel/drivers/regulator/wm8350-regulator.ko
kernel/drivers/regulator/wm8400-regulator.ko
kernel/drivers/regulator/wm8994-regulator.ko
kernel/drivers/tty/serial/8250/serial_cs.ko
kernel/drivers/tty/serial/8250/8250_dw.ko
kernel/drivers/tty/serial/max3100.ko
kernel/drivers/tty/serial/jsm/jsm.ko
kernel/drivers/tty/serial/uartlite.ko
kernel/drivers/tty/serial/altera_uart.ko
kernel/drivers/tty/serial/timbuart.ko
kernel/drivers/tty/serial/altera_jtaguart.ko
kernel/drivers/tty/serial/mrst_max3110.ko
kernel/drivers/tty/serial/mfd.ko
kernel/drivers/tty/serial/pch_uart.ko
kernel/drivers/tty/serial/arc_uart.ko
kernel/drivers/tty/ipwireless/ipwireless.ko
kernel/drivers/tty/n_hdlc.ko
kernel/drivers/tty/n_tracerouter.ko
kernel/drivers/tty/n_tracesink.ko
kernel/drivers/tty/n_r3964.ko
kernel/drivers/tty/cyclades.ko
kernel/drivers/tty/isicom.ko
kernel/drivers/tty/moxa.ko
kernel/drivers/tty/mxser.ko
kernel/drivers/tty/nozomi.ko
kernel/drivers/tty/rocket.ko
kernel/drivers/tty/synclink_gt.ko
kernel/drivers/tty/synclinkmp.ko
kernel/drivers/tty/synclink.ko
kernel/drivers/char/hw_random/timeriomem-rng.ko
kernel/drivers/char/hw_random/intel-rng.ko
kernel/drivers/char/hw_random/amd-rng.ko
kernel/drivers/char/hw_random/via-rng.ko
kernel/drivers/char/hw_random/virtio-rng.ko
kernel/drivers/char/hw_random/tpm-rng.ko
kernel/drivers/char/agp/sis-agp.ko
kernel/drivers/char/tpm/tpm_tis.ko
kernel/drivers/char/tpm/tpm_i2c_infineon.ko
kernel/drivers/char/tpm/tpm_nsc.ko
kernel/drivers/char/tpm/tpm_atmel.ko
kernel/drivers/char/tpm/tpm_infineon.ko
kernel/drivers/char/virtio_console.ko
kernel/drivers/char/raw.ko
kernel/drivers/char/lp.ko
kernel/drivers/char/applicom.ko
kernel/drivers/char/nvram.ko
kernel/drivers/char/i8k.ko
kernel/drivers/char/ppdev.ko
kernel/drivers/char/tlclk.ko
kernel/drivers/char/mwave/mwave.ko
kernel/drivers/char/pcmcia/synclink_cs.ko
kernel/drivers/char/pcmcia/cm4000_cs.ko
kernel/drivers/char/pcmcia/cm4040_cs.ko
kernel/drivers/char/hangcheck-timer.ko
kernel/drivers/gpu/drm/i2c/ch7006.ko
kernel/drivers/gpu/drm/i2c/sil164.ko
kernel/drivers/gpu/drm/drm_kms_helper.ko
kernel/drivers/gpu/drm/drm.ko
kernel/drivers/gpu/drm/drm_usb.ko
kernel/drivers/gpu/drm/ttm/ttm.ko
kernel/drivers/gpu/drm/tdfx/tdfx.ko
kernel/drivers/gpu/drm/r128/r128.ko
kernel/drivers/gpu/drm/radeon/radeon.ko
kernel/drivers/gpu/drm/mga/mga.ko
kernel/drivers/gpu/drm/i810/i810.ko
kernel/drivers/gpu/drm/i915/i915.ko
kernel/drivers/gpu/drm/cirrus/cirrus.ko
kernel/drivers/gpu/drm/sis/sis.ko
kernel/drivers/gpu/drm/savage/savage.ko
kernel/drivers/gpu/drm/vmwgfx/vmwgfx.ko
kernel/drivers/gpu/drm/via/via.ko
kernel/drivers/gpu/drm/nouveau/nouveau.ko
kernel/drivers/gpu/drm/gma500/gma500_gfx.ko
kernel/drivers/gpu/drm/udl/udl.ko
kernel/drivers/gpu/drm/ast/ast.ko
kernel/drivers/base/regmap/regmap-mmio.ko
kernel/drivers/block/floppy.ko
kernel/drivers/block/cpqarray.ko
kernel/drivers/block/cciss.ko
kernel/drivers/block/DAC960.ko
kernel/drivers/block/pktcdvd.ko
kernel/drivers/block/nvme.ko
kernel/drivers/block/osdblk.ko
kernel/drivers/block/umem.ko
kernel/drivers/block/nbd.ko
kernel/drivers/block/cryptoloop.ko
kernel/drivers/block/sx8.ko
kernel/drivers/block/xen-blkback/xen-blkback.ko
kernel/drivers/block/drbd/drbd.ko
kernel/drivers/block/rbd.ko
kernel/drivers/block/mtip32xx/mtip32xx.ko
kernel/drivers/misc/eeprom/at24.ko
kernel/drivers/misc/eeprom/at25.ko
kernel/drivers/misc/eeprom/eeprom.ko
kernel/drivers/misc/eeprom/max6875.ko
kernel/drivers/misc/eeprom/eeprom_93cx6.ko
kernel/drivers/misc/eeprom/eeprom_93xx46.ko
kernel/drivers/misc/cb710/cb710.ko
kernel/drivers/misc/ti-st/st_drv.ko
kernel/drivers/misc/lis3lv02d/lis3lv02d.ko
kernel/drivers/misc/lis3lv02d/lis3lv02d_i2c.ko
kernel/drivers/misc/ibmasm/ibmasm.ko
kernel/drivers/misc/ad525x_dpot.ko
kernel/drivers/misc/ad525x_dpot-i2c.ko
kernel/drivers/misc/ad525x_dpot-spi.ko
kernel/drivers/misc/pti.ko
kernel/drivers/misc/bmp085-i2c.ko
kernel/drivers/misc/bmp085-spi.ko
kernel/drivers/misc/ics932s401.ko
kernel/drivers/misc/tifm_core.ko
kernel/drivers/misc/tifm_7xx1.ko
kernel/drivers/misc/phantom.ko
kernel/drivers/misc/bh1780gli.ko
kernel/drivers/misc/bh1770glc.ko
kernel/drivers/misc/apds990x.ko
kernel/drivers/misc/ioc4.ko
kernel/drivers/misc/enclosure.ko
kernel/drivers/misc/hpilo.ko
kernel/drivers/misc/apds9802als.ko
kernel/drivers/misc/isl29003.ko
kernel/drivers/misc/isl29020.ko
kernel/drivers/misc/tsl2550.ko
kernel/drivers/misc/ds1682.ko
kernel/drivers/misc/ti_dac7512.ko
kernel/drivers/misc/c2port/core.ko
kernel/drivers/misc/c2port/c2port-duramar2150.ko
kernel/drivers/misc/hmc6352.ko
kernel/drivers/misc/vmw_balloon.ko
kernel/drivers/misc/pch_phub.ko
kernel/drivers/misc/fsa9480.ko
kernel/drivers/misc/altera-stapl/altera-stapl.ko
kernel/drivers/misc/mei/mei.ko
kernel/drivers/mfd/88pm800.ko
kernel/drivers/mfd/88pm80x.ko
kernel/drivers/mfd/88pm805.ko
kernel/drivers/mfd/sm501.ko
kernel/drivers/mfd/rtsx_pci.ko
kernel/drivers/mfd/htc-pasic3.ko
kernel/drivers/mfd/ti_am335x_tscadc.ko
kernel/drivers/mfd/arizona-i2c.ko
kernel/drivers/mfd/arizona-spi.ko
kernel/drivers/mfd/tps6105x.ko
kernel/drivers/mfd/tps65010.ko
kernel/drivers/mfd/tps6507x.ko
kernel/drivers/mfd/tps65217.ko
kernel/drivers/mfd/twl4030-madc.ko
kernel/drivers/mfd/mc13xxx-core.ko
kernel/drivers/mfd/mc13xxx-spi.ko
kernel/drivers/mfd/mc13xxx-i2c.ko
kernel/drivers/mfd/ucb1400_core.ko
kernel/drivers/mfd/max8907.ko
kernel/drivers/mfd/pcf50633.ko
kernel/drivers/mfd/pcf50633-adc.ko
kernel/drivers/mfd/pcf50633-gpio.ko
kernel/drivers/mfd/ab3100-otp.ko
kernel/drivers/mfd/timberdale.ko
kernel/drivers/mfd/lpc_sch.ko
kernel/drivers/mfd/lpc_ich.ko
kernel/drivers/mfd/rdc321x-southbridge.ko
kernel/drivers/mfd/janz-cmodio.ko
kernel/drivers/mfd/vx855.ko
kernel/drivers/mfd/wl1273-core.ko
kernel/drivers/mfd/cs5535-mfd.ko
kernel/drivers/mfd/viperboard.ko
kernel/drivers/mfd/lm3533-core.ko
kernel/drivers/mfd/lm3533-ctrlbank.ko
kernel/drivers/mfd/retu-mfd.ko
kernel/drivers/nfc/pn544/pn544_i2c.ko
kernel/drivers/nfc/pn533.ko
kernel/drivers/nfc/nfcwilink.ko
kernel/drivers/macintosh/mac_hid.ko
kernel/drivers/scsi/megaraid/megaraid_mm.ko
kernel/drivers/scsi/megaraid/megaraid_mbox.ko
kernel/drivers/scsi/megaraid/megaraid_sas.ko
kernel/drivers/scsi/pcmcia/qlogic_cs.ko
kernel/drivers/scsi/pcmcia/fdomain_cs.ko
kernel/drivers/scsi/pcmcia/aha152x_cs.ko
kernel/drivers/scsi/pcmcia/sym53c500_cs.ko
kernel/drivers/scsi/scsi_tgt.ko
kernel/drivers/scsi/raid_class.ko
kernel/drivers/scsi/scsi_transport_fc.ko
kernel/drivers/scsi/scsi_transport_iscsi.ko
kernel/drivers/scsi/scsi_transport_sas.ko
kernel/drivers/scsi/libsas/libsas.ko
kernel/drivers/scsi/scsi_transport_srp.ko
kernel/drivers/scsi/device_handler/scsi_dh.ko
kernel/drivers/scsi/device_handler/scsi_dh_rdac.ko
kernel/drivers/scsi/device_handler/scsi_dh_hp_sw.ko
kernel/drivers/scsi/device_handler/scsi_dh_emc.ko
kernel/drivers/scsi/device_handler/scsi_dh_alua.ko
kernel/drivers/scsi/libfc/libfc.ko
kernel/drivers/scsi/fcoe/fcoe.ko
kernel/drivers/scsi/fcoe/libfcoe.ko
kernel/drivers/scsi/fnic/fnic.ko
kernel/drivers/scsi/bnx2fc/bnx2fc.ko
kernel/drivers/scsi/libiscsi.ko
kernel/drivers/scsi/libiscsi_tcp.ko
kernel/drivers/scsi/iscsi_tcp.ko
kernel/drivers/scsi/iscsi_boot_sysfs.ko
kernel/drivers/scsi/advansys.ko
kernel/drivers/scsi/BusLogic.ko
kernel/drivers/scsi/dpt_i2o.ko
kernel/drivers/scsi/arcmsr/arcmsr.ko
kernel/drivers/scsi/aic7xxx/aic7xxx.ko
kernel/drivers/scsi/aic7xxx/aic79xx.ko
kernel/drivers/scsi/aacraid/aacraid.ko
kernel/drivers/scsi/aic94xx/aic94xx.ko
kernel/drivers/scsi/pm8001/pm8001.ko
kernel/drivers/scsi/isci/isci.ko
kernel/drivers/scsi/ips.ko
kernel/drivers/scsi/fdomain.ko
kernel/drivers/scsi/qlogicfas408.ko
kernel/drivers/scsi/qla1280.ko
kernel/drivers/scsi/qla2xxx/qla2xxx.ko
kernel/drivers/scsi/qla2xxx/tcm_qla2xxx.ko
kernel/drivers/scsi/qla4xxx/qla4xxx.ko
kernel/drivers/scsi/lpfc/lpfc.ko
kernel/drivers/scsi/bfa/bfa.ko
kernel/drivers/scsi/csiostor/csiostor.ko
kernel/drivers/scsi/dmx3191d.ko
kernel/drivers/scsi/hpsa.ko
kernel/drivers/scsi/sym53c8xx_2/sym53c8xx.ko
kernel/drivers/scsi/eata.ko
kernel/drivers/scsi/dc395x.ko
kernel/drivers/scsi/tmscsim.ko
kernel/drivers/scsi/megaraid.ko
kernel/drivers/scsi/mpt2sas/mpt2sas.ko
kernel/drivers/scsi/mpt3sas/mpt3sas.ko
kernel/drivers/scsi/ufs/ufshcd.ko
kernel/drivers/scsi/atp870u.ko
kernel/drivers/scsi/gdth.ko
kernel/drivers/scsi/initio.ko
kernel/drivers/scsi/a100u2w.ko
kernel/drivers/scsi/3w-xxxx.ko
kernel/drivers/scsi/3w-9xxx.ko
kernel/drivers/scsi/3w-sas.ko
kernel/drivers/scsi/ppa.ko
kernel/drivers/scsi/imm.ko
kernel/drivers/scsi/ipr.ko
kernel/drivers/scsi/libsrp.ko
kernel/drivers/scsi/hptiop.ko
kernel/drivers/scsi/stex.ko
kernel/drivers/scsi/mvsas/mvsas.ko
kernel/drivers/scsi/mvumi.ko
kernel/drivers/scsi/cxgbi/libcxgbi.ko
kernel/drivers/scsi/cxgbi/cxgb3i/cxgb3i.ko
kernel/drivers/scsi/cxgbi/cxgb4i/cxgb4i.ko
kernel/drivers/scsi/bnx2i/bnx2i.ko
kernel/drivers/scsi/be2iscsi/be2iscsi.ko
kernel/drivers/scsi/pmcraid.ko
kernel/drivers/scsi/virtio_scsi.ko
kernel/drivers/scsi/vmw_pvscsi.ko
kernel/drivers/scsi/hv_storvsc.ko
kernel/drivers/scsi/st.ko
kernel/drivers/scsi/osst.ko
kernel/drivers/scsi/ch.ko
kernel/drivers/scsi/ses.ko
kernel/drivers/scsi/osd/libosd.ko
kernel/drivers/scsi/osd/osd.ko
kernel/drivers/scsi/scsi_debug.ko
kernel/drivers/ata/ahci.ko
kernel/drivers/ata/libahci.ko
kernel/drivers/ata/acard-ahci.ko
kernel/drivers/ata/ahci_platform.ko
kernel/drivers/ata/sata_inic162x.ko
kernel/drivers/ata/sata_sil24.ko
kernel/drivers/ata/pdc_adma.ko
kernel/drivers/ata/pata_arasan_cf.ko
kernel/drivers/ata/sata_qstor.ko
kernel/drivers/ata/sata_sx4.ko
kernel/drivers/ata/sata_mv.ko
kernel/drivers/ata/sata_nv.ko
kernel/drivers/ata/sata_promise.ko
kernel/drivers/ata/sata_sil.ko
kernel/drivers/ata/sata_sis.ko
kernel/drivers/ata/sata_svw.ko
kernel/drivers/ata/sata_uli.ko
kernel/drivers/ata/sata_via.ko
kernel/drivers/ata/sata_vsc.ko
kernel/drivers/ata/pata_ali.ko
kernel/drivers/ata/pata_amd.ko
kernel/drivers/ata/pata_artop.ko
kernel/drivers/ata/pata_atiixp.ko
kernel/drivers/ata/pata_atp867x.ko
kernel/drivers/ata/pata_cmd64x.ko
kernel/drivers/ata/pata_cs5520.ko
kernel/drivers/ata/pata_cs5530.ko
kernel/drivers/ata/pata_cs5536.ko
kernel/drivers/ata/pata_cypress.ko
kernel/drivers/ata/pata_efar.ko
kernel/drivers/ata/pata_hpt366.ko
kernel/drivers/ata/pata_hpt37x.ko
kernel/drivers/ata/pata_hpt3x2n.ko
kernel/drivers/ata/pata_hpt3x3.ko
kernel/drivers/ata/pata_it8213.ko
kernel/drivers/ata/pata_it821x.ko
kernel/drivers/ata/pata_jmicron.ko
kernel/drivers/ata/pata_marvell.ko
kernel/drivers/ata/pata_netcell.ko
kernel/drivers/ata/pata_ninja32.ko
kernel/drivers/ata/pata_ns87415.ko
kernel/drivers/ata/pata_oldpiix.ko
kernel/drivers/ata/pata_optidma.ko
kernel/drivers/ata/pata_pdc2027x.ko
kernel/drivers/ata/pata_pdc202xx_old.ko
kernel/drivers/ata/pata_radisys.ko
kernel/drivers/ata/pata_rdc.ko
kernel/drivers/ata/pata_sc1200.ko
kernel/drivers/ata/pata_sch.ko
kernel/drivers/ata/pata_serverworks.ko
kernel/drivers/ata/pata_sil680.ko
kernel/drivers/ata/pata_piccolo.ko
kernel/drivers/ata/pata_triflex.ko
kernel/drivers/ata/pata_via.ko
kernel/drivers/ata/pata_sl82c105.ko
kernel/drivers/ata/pata_cmd640.ko
kernel/drivers/ata/pata_mpiix.ko
kernel/drivers/ata/pata_ns87410.ko
kernel/drivers/ata/pata_opti.ko
kernel/drivers/ata/pata_pcmcia.ko
kernel/drivers/ata/pata_platform.ko
kernel/drivers/ata/pata_rz1000.ko
kernel/drivers/ata/pata_acpi.ko
kernel/drivers/ata/pata_legacy.ko
kernel/drivers/spi/spidev.ko
kernel/drivers/spi/spi-altera.ko
kernel/drivers/spi/spi-bitbang.ko
kernel/drivers/spi/spi-butterfly.ko
kernel/drivers/spi/spi-dw.ko
kernel/drivers/spi/spi-dw-midpci.ko
kernel/drivers/spi/spi-gpio.ko
kernel/drivers/spi/spi-lm70llp.ko
kernel/drivers/spi/spi-oc-tiny.ko
kernel/drivers/spi/spi-pxa2xx-platform.ko
kernel/drivers/spi/spi-pxa2xx-pci.ko
kernel/drivers/spi/spi-sc18is602.ko
kernel/drivers/spi/spi-tle62x0.ko
kernel/drivers/spi/spi-topcliff-pch.ko
kernel/drivers/spi/spi-xcomm.ko
kernel/drivers/hsi/clients/hsi_char.ko
kernel/drivers/hsi/hsi.ko
kernel/drivers/net/phy/spi_ks8995.ko
kernel/drivers/net/ethernet/3com/3c589_cs.ko
kernel/drivers/net/ethernet/3com/3c574_cs.ko
kernel/drivers/net/ethernet/3com/3c59x.ko
kernel/drivers/net/ethernet/3com/typhoon.ko
kernel/drivers/net/ethernet/8390/ne2k-pci.ko
kernel/drivers/net/ethernet/8390/8390.ko
kernel/drivers/net/ethernet/8390/axnet_cs.ko
kernel/drivers/net/ethernet/8390/pcnet_cs.ko
kernel/drivers/net/ethernet/adaptec/starfire.ko
kernel/drivers/net/ethernet/alteon/acenic.ko
kernel/drivers/net/ethernet/amd/amd8111e.ko
kernel/drivers/net/ethernet/amd/nmclan_cs.ko
kernel/drivers/net/ethernet/amd/pcnet32.ko
kernel/drivers/net/ethernet/atheros/atlx/atl1.ko
kernel/drivers/net/ethernet/atheros/atlx/atl2.ko
kernel/drivers/net/ethernet/atheros/atl1e/atl1e.ko
kernel/drivers/net/ethernet/atheros/atl1c/atl1c.ko
kernel/drivers/net/ethernet/cadence/at91_ether.ko
kernel/drivers/net/ethernet/cadence/macb.ko
kernel/drivers/net/ethernet/broadcom/b44.ko
kernel/drivers/net/ethernet/broadcom/bnx2.ko
kernel/drivers/net/ethernet/broadcom/cnic.ko
kernel/drivers/net/ethernet/broadcom/bnx2x/bnx2x.ko
kernel/drivers/net/ethernet/broadcom/tg3.ko
kernel/drivers/net/ethernet/brocade/bna/bna.ko
kernel/drivers/net/ethernet/chelsio/cxgb/cxgb.ko
kernel/drivers/net/ethernet/chelsio/cxgb3/cxgb3.ko
kernel/drivers/net/ethernet/chelsio/cxgb4/cxgb4.ko
kernel/drivers/net/ethernet/chelsio/cxgb4vf/cxgb4vf.ko
kernel/drivers/net/ethernet/cisco/enic/enic.ko
kernel/drivers/net/ethernet/dec/tulip/xircom_cb.ko
kernel/drivers/net/ethernet/dec/tulip/dmfe.ko
kernel/drivers/net/ethernet/dec/tulip/winbond-840.ko
kernel/drivers/net/ethernet/dec/tulip/de2104x.ko
kernel/drivers/net/ethernet/dec/tulip/tulip.ko
kernel/drivers/net/ethernet/dec/tulip/de4x5.ko
kernel/drivers/net/ethernet/dec/tulip/uli526x.ko
kernel/drivers/net/ethernet/dlink/de600.ko
kernel/drivers/net/ethernet/dlink/de620.ko
kernel/drivers/net/ethernet/dlink/dl2k.ko
kernel/drivers/net/ethernet/dlink/sundance.ko
kernel/drivers/net/ethernet/emulex/benet/be2net.ko
kernel/drivers/net/ethernet/neterion/s2io.ko
kernel/drivers/net/ethernet/neterion/vxge/vxge.ko
kernel/drivers/net/ethernet/fujitsu/fmvj18x_cs.ko
kernel/drivers/net/ethernet/hp/hp100.ko
kernel/drivers/net/ethernet/intel/e100.ko
kernel/drivers/net/ethernet/intel/e1000/e1000.ko
kernel/drivers/net/ethernet/intel/e1000e/e1000e.ko
kernel/drivers/net/ethernet/intel/igb/igb.ko
kernel/drivers/net/ethernet/intel/igbvf/igbvf.ko
kernel/drivers/net/ethernet/intel/ixgbe/ixgbe.ko
kernel/drivers/net/ethernet/intel/ixgbevf/ixgbevf.ko
kernel/drivers/net/ethernet/intel/ixgb/ixgb.ko
kernel/drivers/net/ethernet/i825xx/znet.ko
kernel/drivers/net/ethernet/marvell/mvmdio.ko
kernel/drivers/net/ethernet/marvell/skge.ko
kernel/drivers/net/ethernet/marvell/sky2.ko
kernel/drivers/net/ethernet/mellanox/mlx4/mlx4_core.ko
kernel/drivers/net/ethernet/mellanox/mlx4/mlx4_en.ko
kernel/drivers/net/ethernet/micrel/ks8842.ko
kernel/drivers/net/ethernet/micrel/ks8851.ko
kernel/drivers/net/ethernet/micrel/ks8851_mll.ko
kernel/drivers/net/ethernet/micrel/ksz884x.ko
kernel/drivers/net/ethernet/microchip/enc28j60.ko
kernel/drivers/net/ethernet/myricom/myri10ge/myri10ge.ko
kernel/drivers/net/ethernet/natsemi/natsemi.ko
kernel/drivers/net/ethernet/natsemi/ns83820.ko
kernel/drivers/net/ethernet/nvidia/forcedeth.ko
kernel/drivers/net/ethernet/oki-semi/pch_gbe/pch_gbe.ko
kernel/drivers/net/ethernet/packetengines/hamachi.ko
kernel/drivers/net/ethernet/packetengines/yellowfin.ko
kernel/drivers/net/ethernet/qlogic/qla3xxx.ko
kernel/drivers/net/ethernet/qlogic/qlcnic/qlcnic.ko
kernel/drivers/net/ethernet/qlogic/qlge/qlge.ko
kernel/drivers/net/ethernet/qlogic/netxen/netxen_nic.ko
kernel/drivers/net/ethernet/realtek/8139cp.ko
kernel/drivers/net/ethernet/realtek/8139too.ko
kernel/drivers/net/ethernet/realtek/atp.ko
kernel/drivers/net/ethernet/rdc/r6040.ko
kernel/drivers/net/ethernet/seeq/seeq8005.ko
kernel/drivers/net/ethernet/silan/sc92031.ko
kernel/drivers/net/ethernet/sis/sis190.ko
kernel/drivers/net/ethernet/sis/sis900.ko
kernel/drivers/net/ethernet/smsc/smc91c92_cs.ko
kernel/drivers/net/ethernet/smsc/epic100.ko
kernel/drivers/net/ethernet/smsc/smsc9420.ko
kernel/drivers/net/ethernet/stmicro/stmmac/stmmac.ko
kernel/drivers/net/ethernet/sun/sunhme.ko
kernel/drivers/net/ethernet/sun/sungem.ko
kernel/drivers/net/ethernet/sun/cassini.ko
kernel/drivers/net/ethernet/sun/niu.ko
kernel/drivers/net/ethernet/tehuti/tehuti.ko
kernel/drivers/net/ethernet/ti/tlan.ko
kernel/drivers/net/ethernet/via/via-rhine.ko
kernel/drivers/net/ethernet/via/via-velocity.ko
kernel/drivers/net/ethernet/wiznet/w5100.ko
kernel/drivers/net/ethernet/wiznet/w5300.ko
kernel/drivers/net/ethernet/xircom/xirc2ps_cs.ko
kernel/drivers/net/ethernet/calxeda/xgmac.ko
kernel/drivers/net/ethernet/dnet.ko
kernel/drivers/net/ethernet/icplus/ipg.ko
kernel/drivers/net/ethernet/jme.ko
kernel/drivers/net/ethernet/fealnx.ko
kernel/drivers/net/ethernet/ethoc.ko
kernel/drivers/net/ethernet/sfc/sfc.ko
kernel/drivers/net/fddi/defxx.ko
kernel/drivers/net/fddi/skfp/skfp.ko
kernel/drivers/net/hamradio/mkiss.ko
kernel/drivers/net/hamradio/6pack.ko
kernel/drivers/net/hamradio/yam.ko
kernel/drivers/net/hamradio/bpqether.ko
kernel/drivers/net/hamradio/baycom_ser_fdx.ko
kernel/drivers/net/hamradio/hdlcdrv.ko
kernel/drivers/net/hamradio/baycom_ser_hdx.ko
kernel/drivers/net/hamradio/baycom_par.ko
kernel/drivers/net/ppp/ppp_async.ko
kernel/drivers/net/ppp/bsd_comp.ko
kernel/drivers/net/ppp/ppp_deflate.ko
kernel/drivers/net/ppp/ppp_mppe.ko
kernel/drivers/net/ppp/ppp_synctty.ko
kernel/drivers/net/ppp/pppox.ko
kernel/drivers/net/ppp/pppoe.ko
kernel/drivers/net/ppp/pptp.ko
kernel/drivers/net/slip/slip.ko
kernel/drivers/net/wan/hdlc.ko
kernel/drivers/net/wan/hdlc_raw.ko
kernel/drivers/net/wan/hdlc_raw_eth.ko
kernel/drivers/net/wan/hdlc_cisco.ko
kernel/drivers/net/wan/hdlc_fr.ko
kernel/drivers/net/wan/hdlc_ppp.ko
kernel/drivers/net/wan/hdlc_x25.ko
kernel/drivers/net/wan/farsync.ko
kernel/drivers/net/wan/dscc4.ko
kernel/drivers/net/wan/x25_asy.ko
kernel/drivers/net/wan/lmc/lmc.ko
kernel/drivers/net/wan/dlci.ko
kernel/drivers/net/wan/cycx_drv.ko
kernel/drivers/net/wan/cyclomx.ko
kernel/drivers/net/wan/lapbether.ko
kernel/drivers/net/wan/sbni.ko
kernel/drivers/net/wan/wanxl.ko
kernel/drivers/net/wan/pci200syn.ko
kernel/drivers/net/wan/pc300too.ko
kernel/drivers/net/wireless/ti/wlcore/wlcore.ko
kernel/drivers/net/wireless/ti/wlcore/wlcore_spi.ko
kernel/drivers/net/wireless/ti/wlcore/wlcore_sdio.ko
kernel/drivers/net/wireless/ti/wl12xx/wl12xx.ko
kernel/drivers/net/wireless/ti/wl1251/wl1251.ko
kernel/drivers/net/wireless/ti/wl1251/wl1251_spi.ko
kernel/drivers/net/wireless/ti/wl1251/wl1251_sdio.ko
kernel/drivers/net/wireless/ti/wl18xx/wl18xx.ko
kernel/drivers/net/wireless/ipw2x00/ipw2100.ko
kernel/drivers/net/wireless/ipw2x00/ipw2200.ko
kernel/drivers/net/wireless/ipw2x00/libipw.ko
kernel/drivers/net/wireless/orinoco/orinoco.ko
kernel/drivers/net/wireless/orinoco/orinoco_cs.ko
kernel/drivers/net/wireless/orinoco/orinoco_plx.ko
kernel/drivers/net/wireless/orinoco/orinoco_tmd.ko
kernel/drivers/net/wireless/orinoco/orinoco_nortel.ko
kernel/drivers/net/wireless/orinoco/spectrum_cs.ko
kernel/drivers/net/wireless/orinoco/orinoco_usb.ko
kernel/drivers/net/wireless/airo.ko
kernel/drivers/net/wireless/airo_cs.ko
kernel/drivers/net/wireless/atmel.ko
kernel/drivers/net/wireless/atmel_pci.ko
kernel/drivers/net/wireless/atmel_cs.ko
kernel/drivers/net/wireless/at76c50x-usb.ko
kernel/drivers/net/wireless/hostap/hostap.ko
kernel/drivers/net/wireless/hostap/hostap_cs.ko
kernel/drivers/net/wireless/hostap/hostap_plx.ko
kernel/drivers/net/wireless/hostap/hostap_pci.ko
kernel/drivers/net/wireless/b43/b43.ko
kernel/drivers/net/wireless/b43legacy/b43legacy.ko
kernel/drivers/net/wireless/zd1211rw/zd1211rw.ko
kernel/drivers/net/wireless/rtl818x/rtl8180/rtl8180.ko
kernel/drivers/net/wireless/rtl818x/rtl8187/rtl8187.ko
kernel/drivers/net/wireless/ray_cs.ko
kernel/drivers/net/wireless/wl3501_cs.ko
kernel/drivers/net/wireless/rndis_wlan.ko
kernel/drivers/net/wireless/zd1201.ko
kernel/drivers/net/wireless/libertas/libertas.ko
kernel/drivers/net/wireless/libertas/usb8xxx.ko
kernel/drivers/net/wireless/libertas/libertas_cs.ko
kernel/drivers/net/wireless/libertas/libertas_sdio.ko
kernel/drivers/net/wireless/libertas/libertas_spi.ko
kernel/drivers/net/wireless/libertas_tf/libertas_tf.ko
kernel/drivers/net/wireless/libertas_tf/libertas_tf_usb.ko
kernel/drivers/net/wireless/adm8211.ko
kernel/drivers/net/wireless/mwl8k.ko
kernel/drivers/net/wireless/iwlwifi/iwlwifi.ko
kernel/drivers/net/wireless/iwlwifi/dvm/iwldvm.ko
kernel/drivers/net/wireless/iwlegacy/iwlegacy.ko
kernel/drivers/net/wireless/iwlegacy/iwl4965.ko
kernel/drivers/net/wireless/iwlegacy/iwl3945.ko
kernel/drivers/net/wireless/rt2x00/rt2x00lib.ko
kernel/drivers/net/wireless/rt2x00/rt2x00pci.ko
kernel/drivers/net/wireless/rt2x00/rt2x00usb.ko
kernel/drivers/net/wireless/rt2x00/rt2800lib.ko
kernel/drivers/net/wireless/rt2x00/rt2400pci.ko
kernel/drivers/net/wireless/rt2x00/rt2500pci.ko
kernel/drivers/net/wireless/rt2x00/rt61pci.ko
kernel/drivers/net/wireless/rt2x00/rt2800pci.ko
kernel/drivers/net/wireless/rt2x00/rt2500usb.ko
kernel/drivers/net/wireless/rt2x00/rt73usb.ko
kernel/drivers/net/wireless/rt2x00/rt2800usb.ko
kernel/drivers/net/wireless/p54/p54common.ko
kernel/drivers/net/wireless/p54/p54usb.ko
kernel/drivers/net/wireless/p54/p54pci.ko
kernel/drivers/net/wireless/p54/p54spi.ko
kernel/drivers/net/wireless/ath/ath5k/ath5k.ko
kernel/drivers/net/wireless/ath/ath9k/ath9k.ko
kernel/drivers/net/wireless/ath/ath9k/ath9k_hw.ko
kernel/drivers/net/wireless/ath/ath9k/ath9k_common.ko
kernel/drivers/net/wireless/ath/ath9k/ath9k_htc.ko
kernel/drivers/net/wireless/ath/carl9170/carl9170.ko
kernel/drivers/net/wireless/ath/ath6kl/ath6kl_core.ko
kernel/drivers/net/wireless/ath/ath6kl/ath6kl_sdio.ko
kernel/drivers/net/wireless/ath/ath6kl/ath6kl_usb.ko
kernel/drivers/net/wireless/ath/ar5523/ar5523.ko
kernel/drivers/net/wireless/ath/wil6210/wil6210.ko
kernel/drivers/net/wireless/ath/ath.ko
kernel/drivers/net/wireless/mac80211_hwsim.ko
kernel/drivers/net/wireless/mwifiex/mwifiex.ko
kernel/drivers/net/wireless/mwifiex/mwifiex_sdio.ko
kernel/drivers/net/wireless/mwifiex/mwifiex_pcie.ko
kernel/drivers/net/wireless/mwifiex/mwifiex_usb.ko
kernel/drivers/net/wireless/brcm80211/brcmutil/brcmutil.ko
kernel/drivers/net/wireless/brcm80211/brcmfmac/brcmfmac.ko
kernel/drivers/net/wireless/brcm80211/brcmsmac/brcmsmac.ko
kernel/drivers/net/bonding/bonding.ko
kernel/drivers/net/dummy.ko
kernel/drivers/net/eql.ko
kernel/drivers/net/ifb.ko
kernel/drivers/net/macvlan.ko
kernel/drivers/net/macvtap.ko
kernel/drivers/net/mdio.ko
kernel/drivers/net/netconsole.ko
kernel/drivers/net/rionet.ko
kernel/drivers/net/veth.ko
kernel/drivers/net/vxlan.ko
kernel/drivers/net/arcnet/arcnet.ko
kernel/drivers/net/arcnet/rfc1201.ko
kernel/drivers/net/arcnet/rfc1051.ko
kernel/drivers/net/arcnet/arc-rawmode.ko
kernel/drivers/net/arcnet/capmode.ko
kernel/drivers/net/arcnet/com90xx.ko
kernel/drivers/net/arcnet/com90io.ko
kernel/drivers/net/arcnet/arc-rimi.ko
kernel/drivers/net/arcnet/com20020.ko
kernel/drivers/net/arcnet/com20020-pci.ko
kernel/drivers/net/arcnet/com20020_cs.ko
kernel/drivers/net/appletalk/ipddp.ko
kernel/drivers/net/caif/caif_serial.ko
kernel/drivers/net/caif/cfspi_slave.ko
kernel/drivers/net/caif/caif_hsi.ko
kernel/drivers/net/can/usb/ems_usb.ko
kernel/drivers/net/can/usb/esd_usb2.ko
kernel/drivers/net/can/usb/kvaser_usb.ko
kernel/drivers/net/can/usb/peak_usb/peak_usb.ko
kernel/drivers/net/can/softing/softing.ko
kernel/drivers/net/can/softing/softing_cs.ko
kernel/drivers/net/can/vcan.ko
kernel/drivers/net/can/slcan.ko
kernel/drivers/net/can/can-dev.ko
kernel/drivers/net/can/sja1000/sja1000.ko
kernel/drivers/net/can/sja1000/sja1000_isa.ko
kernel/drivers/net/can/sja1000/sja1000_platform.ko
kernel/drivers/net/can/sja1000/ems_pcmcia.ko
kernel/drivers/net/can/sja1000/ems_pci.ko
kernel/drivers/net/can/sja1000/kvaser_pci.ko
kernel/drivers/net/can/sja1000/peak_pcmcia.ko
kernel/drivers/net/can/sja1000/peak_pci.ko
kernel/drivers/net/can/sja1000/plx_pci.ko
kernel/drivers/net/can/c_can/c_can.ko
kernel/drivers/net/can/c_can/c_can_platform.ko
kernel/drivers/net/can/c_can/c_can_pci.ko
kernel/drivers/net/can/cc770/cc770.ko
kernel/drivers/net/can/cc770/cc770_isa.ko
kernel/drivers/net/can/cc770/cc770_platform.ko
kernel/drivers/net/can/mcp251x.ko
kernel/drivers/net/can/janz-ican3.ko
kernel/drivers/net/can/pch_can.ko
kernel/drivers/net/dsa/mv88e6060.ko
kernel/drivers/net/dsa/mv88e6xxx_drv.ko
kernel/drivers/net/irda/irda-usb.ko
kernel/drivers/net/irda/stir4200.ko
kernel/drivers/net/irda/nsc-ircc.ko
kernel/drivers/net/irda/w83977af_ir.ko
kernel/drivers/net/irda/smsc-ircc2.ko
kernel/drivers/net/irda/ali-ircc.ko
kernel/drivers/net/irda/vlsi_ir.ko
kernel/drivers/net/irda/via-ircc.ko
kernel/drivers/net/irda/mcs7780.ko
kernel/drivers/net/irda/irtty-sir.ko
kernel/drivers/net/irda/sir-dev.ko
kernel/drivers/net/irda/esi-sir.ko
kernel/drivers/net/irda/tekram-sir.ko
kernel/drivers/net/irda/actisys-sir.ko
kernel/drivers/net/irda/litelink-sir.ko
kernel/drivers/net/irda/girbil-sir.ko
kernel/drivers/net/irda/old_belkin-sir.ko
kernel/drivers/net/irda/mcp2120-sir.ko
kernel/drivers/net/irda/act200l-sir.ko
kernel/drivers/net/irda/ma600-sir.ko
kernel/drivers/net/irda/toim3232-sir.ko
kernel/drivers/net/irda/kingsun-sir.ko
kernel/drivers/net/irda/ksdazzle-sir.ko
kernel/drivers/net/irda/ks959-sir.ko
kernel/drivers/net/plip/plip.ko
kernel/drivers/net/sb1000.ko
kernel/drivers/net/sungem_phy.ko
kernel/drivers/net/wimax/i2400m/i2400m.ko
kernel/drivers/net/wimax/i2400m/i2400m-usb.ko
kernel/drivers/net/ieee802154/fakelb.ko
kernel/drivers/net/ieee802154/at86rf230.ko
kernel/drivers/net/ieee802154/mrf24j40.ko
kernel/drivers/net/vmxnet3/vmxnet3.ko
kernel/drivers/net/xen-netback/xen-netback.ko
kernel/drivers/net/usb/catc.ko
kernel/drivers/net/usb/kaweth.ko
kernel/drivers/net/usb/pegasus.ko
kernel/drivers/net/usb/rtl8150.ko
kernel/drivers/net/usb/hso.ko
kernel/drivers/net/usb/asix.ko
kernel/drivers/net/usb/cdc_ether.ko
kernel/drivers/net/usb/cdc_eem.ko
kernel/drivers/net/usb/dm9601.ko
kernel/drivers/net/usb/smsc75xx.ko
kernel/drivers/net/usb/smsc95xx.ko
kernel/drivers/net/usb/gl620a.ko
kernel/drivers/net/usb/net1080.ko
kernel/drivers/net/usb/plusb.ko
kernel/drivers/net/usb/rndis_host.ko
kernel/drivers/net/usb/cdc_subset.ko
kernel/drivers/net/usb/zaurus.ko
kernel/drivers/net/usb/mcs7830.ko
kernel/drivers/net/usb/usbnet.ko
kernel/drivers/net/usb/int51x1.ko
kernel/drivers/net/usb/cdc-phonet.ko
kernel/drivers/net/usb/kalmia.ko
kernel/drivers/net/usb/ipheth.ko
kernel/drivers/net/usb/sierra_net.ko
kernel/drivers/net/usb/cx82310_eth.ko
kernel/drivers/net/usb/cdc_ncm.ko
kernel/drivers/net/usb/lg-vl600.ko
kernel/drivers/net/usb/qmi_wwan.ko
kernel/drivers/net/usb/cdc_mbim.ko
kernel/drivers/net/hyperv/hv_netvsc.ko
kernel/drivers/message/fusion/mptbase.ko
kernel/drivers/message/fusion/mptscsih.ko
kernel/drivers/message/fusion/mptspi.ko
kernel/drivers/message/fusion/mptfc.ko
kernel/drivers/message/fusion/mptsas.ko
kernel/drivers/message/fusion/mptctl.ko
kernel/drivers/message/fusion/mptlan.ko
kernel/drivers/message/i2o/i2o_core.ko
kernel/drivers/message/i2o/i2o_config.ko
kernel/drivers/message/i2o/i2o_bus.ko
kernel/drivers/message/i2o/i2o_block.ko
kernel/drivers/message/i2o/i2o_scsi.ko
kernel/drivers/message/i2o/i2o_proc.ko
kernel/drivers/firewire/firewire-core.ko
kernel/drivers/firewire/firewire-ohci.ko
kernel/drivers/firewire/firewire-sbp2.ko
kernel/drivers/firewire/firewire-net.ko
kernel/drivers/firewire/nosy.ko
kernel/drivers/auxdisplay/ks0108.ko
kernel/drivers/auxdisplay/cfag12864b.ko
kernel/drivers/auxdisplay/cfag12864bfb.ko
kernel/drivers/usb/otg/gpio_vbus.ko
kernel/drivers/usb/otg/nop-usb-xceiv.ko
kernel/drivers/usb/host/whci/whci-hcd.ko
kernel/drivers/usb/host/oxu210hp-hcd.ko
kernel/drivers/usb/host/isp116x-hcd.ko
kernel/drivers/usb/host/isp1362-hcd.ko
kernel/drivers/usb/host/sl811-hcd.ko
kernel/drivers/usb/host/sl811_cs.ko
kernel/drivers/usb/host/u132-hcd.ko
kernel/drivers/usb/host/r8a66597-hcd.ko
kernel/drivers/usb/host/isp1760.ko
kernel/drivers/usb/host/hwa-hc.ko
kernel/drivers/usb/host/bcma-hcd.ko
kernel/drivers/usb/host/ssb-hcd.ko
kernel/drivers/usb/storage/usb-storage.ko
kernel/drivers/usb/storage/ums-alauda.ko
kernel/drivers/usb/storage/ums-cypress.ko
kernel/drivers/usb/storage/ums-datafab.ko
kernel/drivers/usb/storage/ums-eneub6250.ko
kernel/drivers/usb/storage/ums-freecom.ko
kernel/drivers/usb/storage/ums-isd200.ko
kernel/drivers/usb/storage/ums-jumpshot.ko
kernel/drivers/usb/storage/ums-karma.ko
kernel/drivers/usb/storage/ums-onetouch.ko
kernel/drivers/usb/storage/ums-realtek.ko
kernel/drivers/usb/storage/ums-sddr09.ko
kernel/drivers/usb/storage/ums-sddr55.ko
kernel/drivers/usb/storage/ums-usbat.ko
kernel/drivers/usb/misc/adutux.ko
kernel/drivers/usb/misc/appledisplay.ko
kernel/drivers/usb/misc/cypress_cy7c63.ko
kernel/drivers/usb/misc/cytherm.ko
kernel/drivers/usb/misc/emi26.ko
kernel/drivers/usb/misc/emi62.ko
kernel/drivers/usb/misc/ezusb.ko
kernel/drivers/usb/misc/ftdi-elan.ko
kernel/drivers/usb/misc/idmouse.ko
kernel/drivers/usb/misc/iowarrior.ko
kernel/drivers/usb/misc/isight_firmware.ko
kernel/drivers/usb/misc/usblcd.ko
kernel/drivers/usb/misc/ldusb.ko
kernel/drivers/usb/misc/usbled.ko
kernel/drivers/usb/misc/legousbtower.ko
kernel/drivers/usb/misc/rio500.ko
kernel/drivers/usb/misc/usbtest.ko
kernel/drivers/usb/misc/trancevibrator.ko
kernel/drivers/usb/misc/uss720.ko
kernel/drivers/usb/misc/usbsevseg.ko
kernel/drivers/usb/misc/yurex.ko
kernel/drivers/usb/misc/sisusbvga/sisusbvga.ko
kernel/drivers/usb/phy/isp1301.ko
kernel/drivers/usb/phy/rcar-phy.ko
kernel/drivers/usb/dwc3/dwc3.ko
kernel/drivers/usb/dwc3/dwc3-omap.ko
kernel/drivers/usb/dwc3/dwc3-exynos.ko
kernel/drivers/usb/dwc3/dwc3-pci.ko
kernel/drivers/usb/mon/usbmon.ko
kernel/drivers/usb/c67x00/c67x00.ko
kernel/drivers/usb/wusbcore/wusbcore.ko
kernel/drivers/usb/wusbcore/wusb-wa.ko
kernel/drivers/usb/wusbcore/wusb-cbaf.ko
kernel/drivers/usb/class/cdc-acm.ko
kernel/drivers/usb/class/usblp.ko
kernel/drivers/usb/class/cdc-wdm.ko
kernel/drivers/usb/class/usbtmc.ko
kernel/drivers/usb/image/mdc800.ko
kernel/drivers/usb/image/microtek.ko
kernel/drivers/usb/serial/usbserial.ko
kernel/drivers/usb/serial/aircable.ko
kernel/drivers/usb/serial/ark3116.ko
kernel/drivers/usb/serial/belkin_sa.ko
kernel/drivers/usb/serial/ch341.ko
kernel/drivers/usb/serial/cp210x.ko
kernel/drivers/usb/serial/cyberjack.ko
kernel/drivers/usb/serial/cypress_m8.ko
kernel/drivers/usb/serial/usb_debug.ko
kernel/drivers/usb/serial/digi_acceleport.ko
kernel/drivers/usb/serial/io_edgeport.ko
kernel/drivers/usb/serial/io_ti.ko
kernel/drivers/usb/serial/empeg.ko
kernel/drivers/usb/serial/f81232.ko
kernel/drivers/usb/serial/ftdi_sio.ko
kernel/drivers/usb/serial/funsoft.ko
kernel/drivers/usb/serial/garmin_gps.ko
kernel/drivers/usb/serial/hp4x.ko
kernel/drivers/usb/serial/ipaq.ko
kernel/drivers/usb/serial/ipw.ko
kernel/drivers/usb/serial/ir-usb.ko
kernel/drivers/usb/serial/iuu_phoenix.ko
kernel/drivers/usb/serial/keyspan.ko
kernel/drivers/usb/serial/keyspan_pda.ko
kernel/drivers/usb/serial/kl5kusb105.ko
kernel/drivers/usb/serial/kobil_sct.ko
kernel/drivers/usb/serial/mct_u232.ko
kernel/drivers/usb/serial/metro-usb.ko
kernel/drivers/usb/serial/mos7720.ko
kernel/drivers/usb/serial/mos7840.ko
kernel/drivers/usb/serial/moto_modem.ko
kernel/drivers/usb/serial/navman.ko
kernel/drivers/usb/serial/omninet.ko
kernel/drivers/usb/serial/opticon.ko
kernel/drivers/usb/serial/option.ko
kernel/drivers/usb/serial/oti6858.ko
kernel/drivers/usb/serial/pl2303.ko
kernel/drivers/usb/serial/qcaux.ko
kernel/drivers/usb/serial/qcserial.ko
kernel/drivers/usb/serial/quatech2.ko
kernel/drivers/usb/serial/safe_serial.ko
kernel/drivers/usb/serial/siemens_mpi.ko
kernel/drivers/usb/serial/sierra.ko
kernel/drivers/usb/serial/spcp8x5.ko
kernel/drivers/usb/serial/ssu100.ko
kernel/drivers/usb/serial/symbolserial.ko
kernel/drivers/usb/serial/usb_wwan.ko
kernel/drivers/usb/serial/ti_usb_3410_5052.ko
kernel/drivers/usb/serial/visor.ko
kernel/drivers/usb/serial/whiteheat.ko
kernel/drivers/usb/serial/vivopay-serial.ko
kernel/drivers/usb/serial/zio.ko
kernel/drivers/usb/serial/zte_ev.ko
kernel/drivers/usb/atm/cxacru.ko
kernel/drivers/usb/atm/speedtch.ko
kernel/drivers/usb/atm/ueagle-atm.ko
kernel/drivers/usb/atm/usbatm.ko
kernel/drivers/usb/atm/xusbatm.ko
kernel/drivers/usb/musb/musb_hdrc.ko
kernel/drivers/usb/musb/tusb6010.ko
kernel/drivers/usb/chipidea/ci_hdrc.ko
kernel/drivers/usb/chipidea/ci13xxx_msm.ko
kernel/drivers/usb/chipidea/ci13xxx_pci.ko
kernel/drivers/usb/renesas_usbhs/renesas_usbhs.ko
kernel/drivers/usb/gadget/udc-core.ko
kernel/drivers/usb/gadget/libcomposite.ko
kernel/drivers/usb/gadget/net2272.ko
kernel/drivers/usb/gadget/net2280.ko
kernel/drivers/usb/gadget/amd5536udc.ko
kernel/drivers/usb/gadget/goku_udc.ko
kernel/drivers/usb/gadget/r8a66597-udc.ko
kernel/drivers/usb/gadget/pch_udc.ko
kernel/drivers/usb/gadget/mv_udc.ko
kernel/drivers/usb/gadget/g_zero.ko
kernel/drivers/usb/gadget/g_audio.ko
kernel/drivers/usb/gadget/g_ether.ko
kernel/drivers/usb/gadget/gadgetfs.ko
kernel/drivers/usb/gadget/g_ffs.ko
kernel/drivers/usb/gadget/g_mass_storage.ko
kernel/drivers/usb/gadget/g_serial.ko
kernel/drivers/usb/gadget/g_printer.ko
kernel/drivers/usb/gadget/g_midi.ko
kernel/drivers/usb/gadget/g_cdc.ko
kernel/drivers/usb/gadget/g_hid.ko
kernel/drivers/usb/gadget/g_dbgp.ko
kernel/drivers/usb/gadget/g_nokia.ko
kernel/drivers/usb/gadget/g_webcam.ko
kernel/drivers/usb/gadget/g_ncm.ko
kernel/drivers/usb/gadget/g_acm_ms.ko
kernel/drivers/usb/gadget/tcm_usb_gadget.ko
kernel/drivers/input/serio/parkbd.ko
kernel/drivers/input/serio/serport.ko
kernel/drivers/input/serio/ct82c710.ko
kernel/drivers/input/serio/pcips2.ko
kernel/drivers/input/serio/ps2mult.ko
kernel/drivers/input/serio/serio_raw.ko
kernel/drivers/input/serio/altera_ps2.ko
kernel/drivers/input/serio/arc_ps2.ko
kernel/drivers/input/keyboard/adp5520-keys.ko
kernel/drivers/input/keyboard/adp5588-keys.ko
kernel/drivers/input/keyboard/adp5589-keys.ko
kernel/drivers/input/keyboard/gpio_keys.ko
kernel/drivers/input/keyboard/gpio_keys_polled.ko
kernel/drivers/input/keyboard/tca6416-keypad.ko
kernel/drivers/input/keyboard/tca8418_keypad.ko
kernel/drivers/input/keyboard/lkkbd.ko
kernel/drivers/input/keyboard/lm8323.ko
kernel/drivers/input/keyboard/lm8333.ko
kernel/drivers/input/keyboard/matrix_keypad.ko
kernel/drivers/input/keyboard/max7359_keypad.ko
kernel/drivers/input/keyboard/mcs_touchkey.ko
kernel/drivers/input/keyboard/mpr121_touchkey.ko
kernel/drivers/input/keyboard/newtonkbd.ko
kernel/drivers/input/keyboard/opencores-kbd.ko
kernel/drivers/input/keyboard/qt1070.ko
kernel/drivers/input/keyboard/qt2160.ko
kernel/drivers/input/keyboard/stmpe-keypad.ko
kernel/drivers/input/keyboard/stowaway.ko
kernel/drivers/input/keyboard/sunkbd.ko
kernel/drivers/input/keyboard/tc3589x-keypad.ko
kernel/drivers/input/keyboard/twl4030_keypad.ko
kernel/drivers/input/keyboard/xtkbd.ko
kernel/drivers/input/mouse/appletouch.ko
kernel/drivers/input/mouse/bcm5974.ko
kernel/drivers/input/mouse/gpio_mouse.ko
kernel/drivers/input/mouse/psmouse.ko
kernel/drivers/input/mouse/sermouse.ko
kernel/drivers/input/mouse/synaptics_i2c.ko
kernel/drivers/input/mouse/synaptics_usb.ko
kernel/drivers/input/mouse/vsxxxaa.ko
kernel/drivers/input/joystick/a3d.ko
kernel/drivers/input/joystick/adi.ko
kernel/drivers/input/joystick/as5011.ko
kernel/drivers/input/joystick/analog.ko
kernel/drivers/input/joystick/cobra.ko
kernel/drivers/input/joystick/db9.ko
kernel/drivers/input/joystick/gamecon.ko
kernel/drivers/input/joystick/gf2k.ko
kernel/drivers/input/joystick/grip.ko
kernel/drivers/input/joystick/grip_mp.ko
kernel/drivers/input/joystick/guillemot.ko
kernel/drivers/input/joystick/iforce/iforce.ko
kernel/drivers/input/joystick/interact.ko
kernel/drivers/input/joystick/joydump.ko
kernel/drivers/input/joystick/magellan.ko
kernel/drivers/input/joystick/sidewinder.ko
kernel/drivers/input/joystick/spaceball.ko
kernel/drivers/input/joystick/spaceorb.ko
kernel/drivers/input/joystick/stinger.ko
kernel/drivers/input/joystick/tmdc.ko
kernel/drivers/input/joystick/turbografx.ko
kernel/drivers/input/joystick/twidjoy.ko
kernel/drivers/input/joystick/warrior.ko
kernel/drivers/input/joystick/xpad.ko
kernel/drivers/input/joystick/zhenhua.ko
kernel/drivers/input/joystick/walkera0701.ko
kernel/drivers/input/tablet/acecad.ko
kernel/drivers/input/tablet/aiptek.ko
kernel/drivers/input/tablet/gtco.ko
kernel/drivers/input/tablet/hanwang.ko
kernel/drivers/input/tablet/kbtab.ko
kernel/drivers/input/tablet/wacom.ko
kernel/drivers/input/touchscreen/88pm860x-ts.ko
kernel/drivers/input/touchscreen/ad7877.ko
kernel/drivers/input/touchscreen/ad7879.ko
kernel/drivers/input/touchscreen/ad7879-i2c.ko
kernel/drivers/input/touchscreen/ad7879-spi.ko
kernel/drivers/input/touchscreen/ads7846.ko
kernel/drivers/input/touchscreen/atmel_mxt_ts.ko
kernel/drivers/input/touchscreen/auo-pixcir-ts.ko
kernel/drivers/input/touchscreen/bu21013_ts.ko
kernel/drivers/input/touchscreen/cy8ctmg110_ts.ko
kernel/drivers/input/touchscreen/cyttsp_core.ko
kernel/drivers/input/touchscreen/cyttsp_i2c.ko
kernel/drivers/input/touchscreen/cyttsp_spi.ko
kernel/drivers/input/touchscreen/da9034-ts.ko
kernel/drivers/input/touchscreen/da9052_tsi.ko
kernel/drivers/input/touchscreen/dynapro.ko
kernel/drivers/input/touchscreen/edt-ft5x06.ko
kernel/drivers/input/touchscreen/hampshire.ko
kernel/drivers/input/touchscreen/gunze.ko
kernel/drivers/input/touchscreen/eeti_ts.ko
kernel/drivers/input/touchscreen/elo.ko
kernel/drivers/input/touchscreen/fujitsu_ts.ko
kernel/drivers/input/touchscreen/ili210x.ko
kernel/drivers/input/touchscreen/inexio.ko
kernel/drivers/input/touchscreen/max11801_ts.ko
kernel/drivers/input/touchscreen/mc13783_ts.ko
kernel/drivers/input/touchscreen/mcs5000_ts.ko
kernel/drivers/input/touchscreen/mms114.ko
kernel/drivers/input/touchscreen/mtouch.ko
kernel/drivers/input/touchscreen/mk712.ko
kernel/drivers/input/touchscreen/usbtouchscreen.ko
kernel/drivers/input/touchscreen/pcap_ts.ko
kernel/drivers/input/touchscreen/penmount.ko
kernel/drivers/input/touchscreen/pixcir_i2c_ts.ko
kernel/drivers/input/touchscreen/st1232.ko
kernel/drivers/input/touchscreen/stmpe-ts.ko
kernel/drivers/input/touchscreen/ti_am335x_tsc.ko
kernel/drivers/input/touchscreen/touchit213.ko
kernel/drivers/input/touchscreen/touchright.ko
kernel/drivers/input/touchscreen/touchwin.ko
kernel/drivers/input/touchscreen/tsc40.ko
kernel/drivers/input/touchscreen/tsc2005.ko
kernel/drivers/input/touchscreen/tsc2007.ko
kernel/drivers/input/touchscreen/ucb1400_ts.ko
kernel/drivers/input/touchscreen/wacom_w8001.ko
kernel/drivers/input/touchscreen/wacom_i2c.ko
kernel/drivers/input/touchscreen/wm831x-ts.ko
kernel/drivers/input/touchscreen/wm97xx-ts.ko
kernel/drivers/input/touchscreen/tps6507x-ts.ko
kernel/drivers/input/misc/88pm860x_onkey.ko
kernel/drivers/input/misc/88pm80x_onkey.ko
kernel/drivers/input/misc/ad714x.ko
kernel/drivers/input/misc/ad714x-i2c.ko
kernel/drivers/input/misc/ad714x-spi.ko
kernel/drivers/input/misc/adxl34x.ko
kernel/drivers/input/misc/adxl34x-i2c.ko
kernel/drivers/input/misc/adxl34x-spi.ko
kernel/drivers/input/misc/apanel.ko
kernel/drivers/input/misc/arizona-haptics.ko
kernel/drivers/input/misc/ati_remote2.ko
kernel/drivers/input/misc/atlas_btns.ko
kernel/drivers/input/misc/bma150.ko
kernel/drivers/input/misc/cm109.ko
kernel/drivers/input/misc/cma3000_d0x.ko
kernel/drivers/input/misc/cma3000_d0x_i2c.ko
kernel/drivers/input/misc/da9052_onkey.ko
kernel/drivers/input/misc/da9055_onkey.ko
kernel/drivers/input/misc/gp2ap002a00f.ko
kernel/drivers/input/misc/gpio_tilt_polled.ko
kernel/drivers/input/misc/keyspan_remote.ko
kernel/drivers/input/misc/kxtj9.ko
kernel/drivers/input/misc/max8925_onkey.ko
kernel/drivers/input/misc/mc13783-pwrbutton.ko
kernel/drivers/input/misc/mma8450.ko
kernel/drivers/input/misc/mpu3050.ko
kernel/drivers/input/misc/pcap_keys.ko
kernel/drivers/input/misc/pcf50633-input.ko
kernel/drivers/input/misc/pcf8574_keypad.ko
kernel/drivers/input/misc/pcspkr.ko
kernel/drivers/input/misc/powermate.ko
kernel/drivers/input/misc/pwm-beeper.ko
kernel/drivers/input/misc/retu-pwrbutton.ko
kernel/drivers/input/misc/rotary_encoder.ko
kernel/drivers/input/misc/twl4030-pwrbutton.ko
kernel/drivers/input/misc/twl4030-vibra.ko
kernel/drivers/input/misc/twl6040-vibra.ko
kernel/drivers/input/misc/wm831x-on.ko
kernel/drivers/input/misc/xen-kbdfront.ko
kernel/drivers/input/misc/yealink.ko
kernel/drivers/input/ff-memless.ko
kernel/drivers/input/input-polldev.ko
kernel/drivers/input/sparse-keymap.ko
kernel/drivers/input/matrix-keymap.ko
kernel/drivers/input/joydev.ko
kernel/drivers/input/evbug.ko
kernel/drivers/rtc/rtc-88pm860x.ko
kernel/drivers/rtc/rtc-88pm80x.ko
kernel/drivers/rtc/rtc-ab3100.ko
kernel/drivers/rtc/rtc-bq32k.ko
kernel/drivers/rtc/rtc-bq4802.ko
kernel/drivers/rtc/rtc-da9052.ko
kernel/drivers/rtc/rtc-da9055.ko
kernel/drivers/rtc/rtc-ds1286.ko
kernel/drivers/rtc/rtc-ds1305.ko
kernel/drivers/rtc/rtc-ds1307.ko
kernel/drivers/rtc/rtc-ds1374.ko
kernel/drivers/rtc/rtc-ds1390.ko
kernel/drivers/rtc/rtc-ds1511.ko
kernel/drivers/rtc/rtc-ds1553.ko
kernel/drivers/rtc/rtc-ds1672.ko
kernel/drivers/rtc/rtc-ds1742.ko
kernel/drivers/rtc/rtc-ds2404.ko
kernel/drivers/rtc/rtc-ds3232.ko
kernel/drivers/rtc/rtc-ds3234.ko
kernel/drivers/rtc/rtc-em3027.ko
kernel/drivers/rtc/rtc-fm3130.ko
kernel/drivers/rtc/rtc-isl1208.ko
kernel/drivers/rtc/rtc-isl12022.ko
kernel/drivers/rtc/rtc-m41t80.ko
kernel/drivers/rtc/rtc-m41t93.ko
kernel/drivers/rtc/rtc-m41t94.ko
kernel/drivers/rtc/rtc-m48t35.ko
kernel/drivers/rtc/rtc-m48t59.ko
kernel/drivers/rtc/rtc-m48t86.ko
kernel/drivers/rtc/rtc-max6900.ko
kernel/drivers/rtc/rtc-max8907.ko
kernel/drivers/rtc/rtc-max8925.ko
kernel/drivers/rtc/rtc-max8998.ko
kernel/drivers/rtc/rtc-max6902.ko
kernel/drivers/rtc/rtc-mc13xxx.ko
kernel/drivers/rtc/rtc-msm6242.ko
kernel/drivers/rtc/rtc-pcap.ko
kernel/drivers/rtc/rtc-pcf8523.ko
kernel/drivers/rtc/rtc-pcf8563.ko
kernel/drivers/rtc/rtc-pcf8583.ko
kernel/drivers/rtc/rtc-pcf2123.ko
kernel/drivers/rtc/rtc-pcf50633.ko
kernel/drivers/rtc/rtc-r9701.ko
kernel/drivers/rtc/rtc-rc5t583.ko
kernel/drivers/rtc/rtc-rp5c01.ko
kernel/drivers/rtc/rtc-rs5c348.ko
kernel/drivers/rtc/rtc-rs5c372.ko
kernel/drivers/rtc/rtc-rv3029c2.ko
kernel/drivers/rtc/rtc-rx8025.ko
kernel/drivers/rtc/rtc-rx8581.ko
kernel/drivers/rtc/rtc-s35390a.ko
kernel/drivers/rtc/rtc-stk17ta8.ko
kernel/drivers/rtc/rtc-twl.ko
kernel/drivers/rtc/rtc-tps6586x.ko
kernel/drivers/rtc/rtc-tps65910.ko
kernel/drivers/rtc/rtc-v3020.ko
kernel/drivers/rtc/rtc-wm831x.ko
kernel/drivers/rtc/rtc-wm8350.ko
kernel/drivers/rtc/rtc-x1205.ko
kernel/drivers/i2c/algos/i2c-algo-bit.ko
kernel/drivers/i2c/algos/i2c-algo-pca.ko
kernel/drivers/i2c/busses/i2c-scmi.ko
kernel/drivers/i2c/busses/i2c-ali1535.ko
kernel/drivers/i2c/busses/i2c-ali1563.ko
kernel/drivers/i2c/busses/i2c-ali15x3.ko
kernel/drivers/i2c/busses/i2c-amd756.ko
kernel/drivers/i2c/busses/i2c-amd756-s4882.ko
kernel/drivers/i2c/busses/i2c-amd8111.ko
kernel/drivers/i2c/busses/i2c-i801.ko
kernel/drivers/i2c/busses/i2c-isch.ko
kernel/drivers/i2c/busses/i2c-ismt.ko
kernel/drivers/i2c/busses/i2c-nforce2.ko
kernel/drivers/i2c/busses/i2c-nforce2-s4985.ko
kernel/drivers/i2c/busses/i2c-piix4.ko
kernel/drivers/i2c/busses/i2c-sis5595.ko
kernel/drivers/i2c/busses/i2c-sis630.ko
kernel/drivers/i2c/busses/i2c-sis96x.ko
kernel/drivers/i2c/busses/i2c-via.ko
kernel/drivers/i2c/busses/i2c-viapro.ko
kernel/drivers/i2c/busses/i2c-cbus-gpio.ko
kernel/drivers/i2c/busses/i2c-designware-core.ko
kernel/drivers/i2c/busses/i2c-designware-pci.ko
kernel/drivers/i2c/busses/i2c-eg20t.ko
kernel/drivers/i2c/busses/i2c-gpio.ko
kernel/drivers/i2c/busses/i2c-intel-mid.ko
kernel/drivers/i2c/busses/i2c-ocores.ko
kernel/drivers/i2c/busses/i2c-pca-platform.ko
kernel/drivers/i2c/busses/i2c-simtec.ko
kernel/drivers/i2c/busses/i2c-xiic.ko
kernel/drivers/i2c/busses/i2c-diolan-u2c.ko
kernel/drivers/i2c/busses/i2c-parport.ko
kernel/drivers/i2c/busses/i2c-parport-light.ko
kernel/drivers/i2c/busses/i2c-taos-evm.ko
kernel/drivers/i2c/busses/i2c-tiny-usb.ko
kernel/drivers/i2c/busses/i2c-viperboard.ko
kernel/drivers/i2c/muxes/i2c-mux-gpio.ko
kernel/drivers/i2c/muxes/i2c-mux-pca9541.ko
kernel/drivers/i2c/muxes/i2c-mux-pca954x.ko
kernel/drivers/i2c/i2c-smbus.ko
kernel/drivers/i2c/i2c-dev.ko
kernel/drivers/i2c/i2c-mux.ko
kernel/drivers/i2c/i2c-stub.ko
kernel/drivers/media/i2c/soc_camera/imx074.ko
kernel/drivers/media/i2c/soc_camera/mt9m001.ko
kernel/drivers/media/i2c/soc_camera/mt9m111.ko
kernel/drivers/media/i2c/soc_camera/mt9t031.ko
kernel/drivers/media/i2c/soc_camera/mt9t112.ko
kernel/drivers/media/i2c/soc_camera/mt9v022.ko
kernel/drivers/media/i2c/soc_camera/ov2640.ko
kernel/drivers/media/i2c/soc_camera/ov5642.ko
kernel/drivers/media/i2c/soc_camera/ov6650.ko
kernel/drivers/media/i2c/soc_camera/ov772x.ko
kernel/drivers/media/i2c/soc_camera/ov9640.ko
kernel/drivers/media/i2c/soc_camera/ov9740.ko
kernel/drivers/media/i2c/soc_camera/rj54n1cb0c.ko
kernel/drivers/media/i2c/soc_camera/tw9910.ko
kernel/drivers/media/i2c/msp3400.ko
kernel/drivers/media/i2c/cx25840/cx25840.ko
kernel/drivers/media/i2c/tvaudio.ko
kernel/drivers/media/i2c/tda7432.ko
kernel/drivers/media/i2c/saa6588.ko
kernel/drivers/media/i2c/tda9840.ko
kernel/drivers/media/i2c/tea6415c.ko
kernel/drivers/media/i2c/tea6420.ko
kernel/drivers/media/i2c/saa7110.ko
kernel/drivers/media/i2c/saa7115.ko
kernel/drivers/media/i2c/saa717x.ko
kernel/drivers/media/i2c/saa7127.ko
kernel/drivers/media/i2c/saa7185.ko
kernel/drivers/media/i2c/adv7170.ko
kernel/drivers/media/i2c/adv7175.ko
kernel/drivers/media/i2c/adv7180.ko
kernel/drivers/media/i2c/vpx3220.ko
kernel/drivers/media/i2c/bt819.ko
kernel/drivers/media/i2c/bt856.ko
kernel/drivers/media/i2c/bt866.ko
kernel/drivers/media/i2c/ks0127.ko
kernel/drivers/media/i2c/tvp5150.ko
kernel/drivers/media/i2c/cs5345.ko
kernel/drivers/media/i2c/cs53l32a.ko
kernel/drivers/media/i2c/m52790.ko
kernel/drivers/media/i2c/wm8775.ko
kernel/drivers/media/i2c/wm8739.ko
kernel/drivers/media/i2c/vp27smpx.ko
kernel/drivers/media/i2c/upd64031a.ko
kernel/drivers/media/i2c/upd64083.ko
kernel/drivers/media/i2c/ov7670.ko
kernel/drivers/media/i2c/tveeprom.ko
kernel/drivers/media/i2c/mt9v011.ko
kernel/drivers/media/i2c/btcx-risc.ko
kernel/drivers/media/i2c/cx2341x.ko
kernel/drivers/media/i2c/ir-kbd-i2c.ko
kernel/drivers/media/tuners/tuner-xc2028.ko
kernel/drivers/media/tuners/tuner-simple.ko
kernel/drivers/media/tuners/tuner-types.ko
kernel/drivers/media/tuners/mt20xx.ko
kernel/drivers/media/tuners/tda8290.ko
kernel/drivers/media/tuners/tea5767.ko
kernel/drivers/media/tuners/tea5761.ko
kernel/drivers/media/tuners/tda9887.ko
kernel/drivers/media/tuners/tda827x.ko
kernel/drivers/media/tuners/tda18271.ko
kernel/drivers/media/tuners/xc5000.ko
kernel/drivers/media/tuners/xc4000.ko
kernel/drivers/media/tuners/mt2060.ko
kernel/drivers/media/tuners/mt2063.ko
kernel/drivers/media/tuners/mt2266.ko
kernel/drivers/media/tuners/qt1010.ko
kernel/drivers/media/tuners/mt2131.ko
kernel/drivers/media/tuners/mxl5005s.ko
kernel/drivers/media/tuners/mxl5007t.ko
kernel/drivers/media/tuners/mc44s803.ko
kernel/drivers/media/tuners/max2165.ko
kernel/drivers/media/tuners/tda18218.ko
kernel/drivers/media/tuners/tda18212.ko
kernel/drivers/media/tuners/e4000.ko
kernel/drivers/media/tuners/fc2580.ko
kernel/drivers/media/tuners/tua9001.ko
kernel/drivers/media/tuners/fc0011.ko
kernel/drivers/media/tuners/fc0012.ko
kernel/drivers/media/tuners/fc0013.ko
kernel/drivers/media/rc/keymaps/rc-adstech-dvb-t-pci.ko
kernel/drivers/media/rc/keymaps/rc-alink-dtu-m.ko
kernel/drivers/media/rc/keymaps/rc-anysee.ko
kernel/drivers/media/rc/keymaps/rc-apac-viewcomp.ko
kernel/drivers/media/rc/keymaps/rc-asus-pc39.ko
kernel/drivers/media/rc/keymaps/rc-asus-ps3-100.ko
kernel/drivers/media/rc/keymaps/rc-ati-tv-wonder-hd-600.ko
kernel/drivers/media/rc/keymaps/rc-ati-x10.ko
kernel/drivers/media/rc/keymaps/rc-avermedia-a16d.ko
kernel/drivers/media/rc/keymaps/rc-avermedia.ko
kernel/drivers/media/rc/keymaps/rc-avermedia-cardbus.ko
kernel/drivers/media/rc/keymaps/rc-avermedia-dvbt.ko
kernel/drivers/media/rc/keymaps/rc-avermedia-m135a.ko
kernel/drivers/media/rc/keymaps/rc-avermedia-m733a-rm-k6.ko
kernel/drivers/media/rc/keymaps/rc-avermedia-rm-ks.ko
kernel/drivers/media/rc/keymaps/rc-avertv-303.ko
kernel/drivers/media/rc/keymaps/rc-azurewave-ad-tu700.ko
kernel/drivers/media/rc/keymaps/rc-behold.ko
kernel/drivers/media/rc/keymaps/rc-behold-columbus.ko
kernel/drivers/media/rc/keymaps/rc-budget-ci-old.ko
kernel/drivers/media/rc/keymaps/rc-cinergy-1400.ko
kernel/drivers/media/rc/keymaps/rc-cinergy.ko
kernel/drivers/media/rc/keymaps/rc-dib0700-nec.ko
kernel/drivers/media/rc/keymaps/rc-dib0700-rc5.ko
kernel/drivers/media/rc/keymaps/rc-digitalnow-tinytwin.ko
kernel/drivers/media/rc/keymaps/rc-digittrade.ko
kernel/drivers/media/rc/keymaps/rc-dm1105-nec.ko
kernel/drivers/media/rc/keymaps/rc-dntv-live-dvb-t.ko
kernel/drivers/media/rc/keymaps/rc-dntv-live-dvbt-pro.ko
kernel/drivers/media/rc/keymaps/rc-em-terratec.ko
kernel/drivers/media/rc/keymaps/rc-encore-enltv2.ko
kernel/drivers/media/rc/keymaps/rc-encore-enltv.ko
kernel/drivers/media/rc/keymaps/rc-encore-enltv-fm53.ko
kernel/drivers/media/rc/keymaps/rc-evga-indtube.ko
kernel/drivers/media/rc/keymaps/rc-eztv.ko
kernel/drivers/media/rc/keymaps/rc-flydvb.ko
kernel/drivers/media/rc/keymaps/rc-flyvideo.ko
kernel/drivers/media/rc/keymaps/rc-fusionhdtv-mce.ko
kernel/drivers/media/rc/keymaps/rc-gadmei-rm008z.ko
kernel/drivers/media/rc/keymaps/rc-genius-tvgo-a11mce.ko
kernel/drivers/media/rc/keymaps/rc-gotview7135.ko
kernel/drivers/media/rc/keymaps/rc-imon-mce.ko
kernel/drivers/media/rc/keymaps/rc-imon-pad.ko
kernel/drivers/media/rc/keymaps/rc-iodata-bctv7e.ko
kernel/drivers/media/rc/keymaps/rc-it913x-v1.ko
kernel/drivers/media/rc/keymaps/rc-it913x-v2.ko
kernel/drivers/media/rc/keymaps/rc-kaiomy.ko
kernel/drivers/media/rc/keymaps/rc-kworld-315u.ko
kernel/drivers/media/rc/keymaps/rc-kworld-pc150u.ko
kernel/drivers/media/rc/keymaps/rc-kworld-plus-tv-analog.ko
kernel/drivers/media/rc/keymaps/rc-leadtek-y04g0051.ko
kernel/drivers/media/rc/keymaps/rc-lirc.ko
kernel/drivers/media/rc/keymaps/rc-lme2510.ko
kernel/drivers/media/rc/keymaps/rc-manli.ko
kernel/drivers/media/rc/keymaps/rc-medion-x10.ko
kernel/drivers/media/rc/keymaps/rc-medion-x10-digitainer.ko
kernel/drivers/media/rc/keymaps/rc-medion-x10-or2x.ko
kernel/drivers/media/rc/keymaps/rc-msi-digivox-ii.ko
kernel/drivers/media/rc/keymaps/rc-msi-digivox-iii.ko
kernel/drivers/media/rc/keymaps/rc-msi-tvanywhere.ko
kernel/drivers/media/rc/keymaps/rc-msi-tvanywhere-plus.ko
kernel/drivers/media/rc/keymaps/rc-nebula.ko
kernel/drivers/media/rc/keymaps/rc-nec-terratec-cinergy-xs.ko
kernel/drivers/media/rc/keymaps/rc-norwood.ko
kernel/drivers/media/rc/keymaps/rc-npgtech.ko
kernel/drivers/media/rc/keymaps/rc-pctv-sedna.ko
kernel/drivers/media/rc/keymaps/rc-pinnacle-color.ko
kernel/drivers/media/rc/keymaps/rc-pinnacle-grey.ko
kernel/drivers/media/rc/keymaps/rc-pinnacle-pctv-hd.ko
kernel/drivers/media/rc/keymaps/rc-pixelview.ko
kernel/drivers/media/rc/keymaps/rc-pixelview-mk12.ko
kernel/drivers/media/rc/keymaps/rc-pixelview-002t.ko
kernel/drivers/media/rc/keymaps/rc-pixelview-new.ko
kernel/drivers/media/rc/keymaps/rc-powercolor-real-angel.ko
kernel/drivers/media/rc/keymaps/rc-proteus-2309.ko
kernel/drivers/media/rc/keymaps/rc-purpletv.ko
kernel/drivers/media/rc/keymaps/rc-pv951.ko
kernel/drivers/media/rc/keymaps/rc-hauppauge.ko
kernel/drivers/media/rc/keymaps/rc-rc6-mce.ko
kernel/drivers/media/rc/keymaps/rc-real-audio-220-32-keys.ko
kernel/drivers/media/rc/keymaps/rc-snapstream-firefly.ko
kernel/drivers/media/rc/keymaps/rc-streamzap.ko
kernel/drivers/media/rc/keymaps/rc-tbs-nec.ko
kernel/drivers/media/rc/keymaps/rc-technisat-usb2.ko
kernel/drivers/media/rc/keymaps/rc-terratec-cinergy-xs.ko
kernel/drivers/media/rc/keymaps/rc-terratec-slim.ko
kernel/drivers/media/rc/keymaps/rc-terratec-slim-2.ko
kernel/drivers/media/rc/keymaps/rc-tevii-nec.ko
kernel/drivers/media/rc/keymaps/rc-tivo.ko
kernel/drivers/media/rc/keymaps/rc-total-media-in-hand.ko
kernel/drivers/media/rc/keymaps/rc-trekstor.ko
kernel/drivers/media/rc/keymaps/rc-tt-1500.ko
kernel/drivers/media/rc/keymaps/rc-twinhan1027.ko
kernel/drivers/media/rc/keymaps/rc-videomate-m1f.ko
kernel/drivers/media/rc/keymaps/rc-videomate-s350.ko
kernel/drivers/media/rc/keymaps/rc-videomate-tv-pvr.ko
kernel/drivers/media/rc/keymaps/rc-winfast.ko
kernel/drivers/media/rc/keymaps/rc-winfast-usbii-deluxe.ko
kernel/drivers/media/rc/rc-core.ko
kernel/drivers/media/rc/lirc_dev.ko
kernel/drivers/media/rc/ir-nec-decoder.ko
kernel/drivers/media/rc/ir-rc5-decoder.ko
kernel/drivers/media/rc/ir-rc6-decoder.ko
kernel/drivers/media/rc/ir-jvc-decoder.ko
kernel/drivers/media/rc/ir-sony-decoder.ko
kernel/drivers/media/rc/ir-rc5-sz-decoder.ko
kernel/drivers/media/rc/ir-sanyo-decoder.ko
kernel/drivers/media/rc/ir-mce_kbd-decoder.ko
kernel/drivers/media/rc/ir-lirc-codec.ko
kernel/drivers/media/rc/ati_remote.ko
kernel/drivers/media/rc/imon.ko
kernel/drivers/media/rc/ite-cir.ko
kernel/drivers/media/rc/mceusb.ko
kernel/drivers/media/rc/fintek-cir.ko
kernel/drivers/media/rc/nuvoton-cir.ko
kernel/drivers/media/rc/ene_ir.ko
kernel/drivers/media/rc/redrat3.ko
kernel/drivers/media/rc/streamzap.ko
kernel/drivers/media/rc/winbond-cir.ko
kernel/drivers/media/rc/rc-loopback.ko
kernel/drivers/media/rc/gpio-ir-recv.ko
kernel/drivers/media/rc/iguanair.ko
kernel/drivers/media/rc/ttusbir.ko
kernel/drivers/media/common/b2c2/b2c2-flexcop.ko
kernel/drivers/media/common/saa7146/saa7146.ko
kernel/drivers/media/common/saa7146/saa7146_vv.ko
kernel/drivers/media/common/siano/smsmdtv.ko
kernel/drivers/media/common/siano/smsdvb.ko
kernel/drivers/media/platform/timblogiw.ko
kernel/drivers/media/platform/via-camera.ko
kernel/drivers/media/platform/marvell-ccic/cafe_ccic.ko
kernel/drivers/media/platform/vivi.ko
kernel/drivers/media/platform/mem2mem_testdev.ko
kernel/drivers/media/platform/m2m-deinterlace.ko
kernel/drivers/media/platform/soc_camera/soc_camera.ko
kernel/drivers/media/platform/soc_camera/soc_mediabus.ko
kernel/drivers/media/platform/soc_camera/soc_camera_platform.ko
kernel/drivers/media/pci/ttpci/ttpci-eeprom.ko
kernel/drivers/media/pci/ttpci/budget-core.ko
kernel/drivers/media/pci/ttpci/budget.ko
kernel/drivers/media/pci/ttpci/budget-av.ko
kernel/drivers/media/pci/ttpci/budget-ci.ko
kernel/drivers/media/pci/ttpci/budget-patch.ko
kernel/drivers/media/pci/ttpci/dvb-ttpci.ko
kernel/drivers/media/pci/b2c2/b2c2-flexcop-pci.ko
kernel/drivers/media/pci/pluto2/pluto2.ko
kernel/drivers/media/pci/dm1105/dm1105.ko
kernel/drivers/media/pci/pt1/earth-pt1.ko
kernel/drivers/media/pci/mantis/mantis_core.ko
kernel/drivers/media/pci/mantis/mantis.ko
kernel/drivers/media/pci/mantis/hopper.ko
kernel/drivers/media/pci/ngene/ngene.ko
kernel/drivers/media/pci/ddbridge/ddbridge.ko
kernel/drivers/media/pci/saa7146/mxb.ko
kernel/drivers/media/pci/saa7146/hexium_orion.ko
kernel/drivers/media/pci/saa7146/hexium_gemini.ko
kernel/drivers/media/pci/ivtv/ivtv.ko
kernel/drivers/media/pci/ivtv/ivtv-alsa.ko
kernel/drivers/media/pci/ivtv/ivtvfb.ko
kernel/drivers/media/pci/zoran/zr36067.ko
kernel/drivers/media/pci/zoran/videocodec.ko
kernel/drivers/media/pci/zoran/zr36050.ko
kernel/drivers/media/pci/zoran/zr36016.ko
kernel/drivers/media/pci/zoran/zr36060.ko
kernel/drivers/media/pci/cx18/cx18.ko
kernel/drivers/media/pci/cx18/cx18-alsa.ko
kernel/drivers/media/pci/cx23885/cx23885.ko
kernel/drivers/media/pci/cx23885/altera-ci.ko
kernel/drivers/media/pci/cx25821/cx25821.ko
kernel/drivers/media/pci/cx25821/cx25821-alsa.ko
kernel/drivers/media/pci/cx88/cx88xx.ko
kernel/drivers/media/pci/cx88/cx8800.ko
kernel/drivers/media/pci/cx88/cx8802.ko
kernel/drivers/media/pci/cx88/cx88-alsa.ko
kernel/drivers/media/pci/cx88/cx88-blackbird.ko
kernel/drivers/media/pci/cx88/cx88-dvb.ko
kernel/drivers/media/pci/cx88/cx88-vp3054-i2c.ko
kernel/drivers/media/pci/bt8xx/bttv.ko
kernel/drivers/media/pci/bt8xx/bt878.ko
kernel/drivers/media/pci/bt8xx/dvb-bt8xx.ko
kernel/drivers/media/pci/bt8xx/dst.ko
kernel/drivers/media/pci/bt8xx/dst_ca.ko
kernel/drivers/media/pci/saa7134/saa6752hs.ko
kernel/drivers/media/pci/saa7134/saa7134.ko
kernel/drivers/media/pci/saa7134/saa7134-empress.ko
kernel/drivers/media/pci/saa7134/saa7134-alsa.ko
kernel/drivers/media/pci/saa7134/saa7134-dvb.ko
kernel/drivers/media/pci/saa7164/saa7164.ko
kernel/drivers/media/pci/meye/meye.ko
kernel/drivers/media/usb/ttusb-dec/ttusb_dec.ko
kernel/drivers/media/usb/ttusb-dec/ttusbdecfe.ko
kernel/drivers/media/usb/ttusb-budget/dvb-ttusb-budget.ko
kernel/drivers/media/usb/dvb-usb/dvb-usb.ko
kernel/drivers/media/usb/dvb-usb/dvb-usb-vp7045.ko
kernel/drivers/media/usb/dvb-usb/dvb-usb-vp702x.ko
kernel/drivers/media/usb/dvb-usb/dvb-usb-gp8psk.ko
kernel/drivers/media/usb/dvb-usb/dvb-usb-dtt200u.ko
kernel/drivers/media/usb/dvb-usb/dvb-usb-dibusb-common.ko
kernel/drivers/media/usb/dvb-usb/dvb-usb-a800.ko
kernel/drivers/media/usb/dvb-usb/dvb-usb-dibusb-mb.ko
kernel/drivers/media/usb/dvb-usb/dvb-usb-dibusb-mc.ko
kernel/drivers/media/usb/dvb-usb/dvb-usb-nova-t-usb2.ko
kernel/drivers/media/usb/dvb-usb/dvb-usb-umt-010.ko
kernel/drivers/media/usb/dvb-usb/dvb-usb-m920x.ko
kernel/drivers/media/usb/dvb-usb/dvb-usb-digitv.ko
kernel/drivers/media/usb/dvb-usb/dvb-usb-cxusb.ko
kernel/drivers/media/usb/dvb-usb/dvb-usb-ttusb2.ko
kernel/drivers/media/usb/dvb-usb/dvb-usb-dib0700.ko
kernel/drivers/media/usb/dvb-usb/dvb-usb-opera.ko
kernel/drivers/media/usb/dvb-usb/dvb-usb-af9005.ko
kernel/drivers/media/usb/dvb-usb/dvb-usb-af9005-remote.ko
kernel/drivers/media/usb/dvb-usb/dvb-usb-pctv452e.ko
kernel/drivers/media/usb/dvb-usb/dvb-usb-dw2102.ko
kernel/drivers/media/usb/dvb-usb/dvb-usb-dtv5100.ko
kernel/drivers/media/usb/dvb-usb/dvb-usb-cinergyT2.ko
kernel/drivers/media/usb/dvb-usb/dvb-usb-friio.ko
kernel/drivers/media/usb/dvb-usb/dvb-usb-az6027.ko
kernel/drivers/media/usb/dvb-usb/dvb-usb-technisat-usb2.ko
kernel/drivers/media/usb/dvb-usb-v2/dvb_usb_v2.ko
kernel/drivers/media/usb/dvb-usb-v2/dvb_usb_cypress_firmware.ko
kernel/drivers/media/usb/dvb-usb-v2/dvb-usb-af9015.ko
kernel/drivers/media/usb/dvb-usb-v2/dvb-usb-af9035.ko
kernel/drivers/media/usb/dvb-usb-v2/dvb-usb-anysee.ko
kernel/drivers/media/usb/dvb-usb-v2/dvb-usb-au6610.ko
kernel/drivers/media/usb/dvb-usb-v2/dvb-usb-az6007.ko
kernel/drivers/media/usb/dvb-usb-v2/dvb-usb-ce6230.ko
kernel/drivers/media/usb/dvb-usb-v2/dvb-usb-ec168.ko
kernel/drivers/media/usb/dvb-usb-v2/dvb-usb-it913x.ko
kernel/drivers/media/usb/dvb-usb-v2/dvb-usb-lmedm04.ko
kernel/drivers/media/usb/dvb-usb-v2/dvb-usb-gl861.ko
kernel/drivers/media/usb/dvb-usb-v2/dvb-usb-mxl111sf.ko
kernel/drivers/media/usb/dvb-usb-v2/mxl111sf-demod.ko
kernel/drivers/media/usb/dvb-usb-v2/mxl111sf-tuner.ko
kernel/drivers/media/usb/dvb-usb-v2/dvb-usb-rtl28xxu.ko
kernel/drivers/media/usb/siano/smsusb.ko
kernel/drivers/media/usb/b2c2/b2c2-flexcop-usb.ko
kernel/drivers/media/usb/zr364xx/zr364xx.ko
kernel/drivers/media/usb/stkwebcam/stkwebcam.ko
kernel/drivers/media/usb/s2255/s2255drv.ko
kernel/drivers/media/usb/uvc/uvcvideo.ko
kernel/drivers/media/usb/gspca/gspca_main.ko
kernel/drivers/media/usb/gspca/gspca_benq.ko
kernel/drivers/media/usb/gspca/gspca_conex.ko
kernel/drivers/media/usb/gspca/gspca_cpia1.ko
kernel/drivers/media/usb/gspca/gspca_etoms.ko
kernel/drivers/media/usb/gspca/gspca_finepix.ko
kernel/drivers/media/usb/gspca/gspca_jeilinj.ko
kernel/drivers/media/usb/gspca/gspca_jl2005bcd.ko
kernel/drivers/media/usb/gspca/gspca_kinect.ko
kernel/drivers/media/usb/gspca/gspca_konica.ko
kernel/drivers/media/usb/gspca/gspca_mars.ko
kernel/drivers/media/usb/gspca/gspca_mr97310a.ko
kernel/drivers/media/usb/gspca/gspca_nw80x.ko
kernel/drivers/media/usb/gspca/gspca_ov519.ko
kernel/drivers/media/usb/gspca/gspca_ov534.ko
kernel/drivers/media/usb/gspca/gspca_ov534_9.ko
kernel/drivers/media/usb/gspca/gspca_pac207.ko
kernel/drivers/media/usb/gspca/gspca_pac7302.ko
kernel/drivers/media/usb/gspca/gspca_pac7311.ko
kernel/drivers/media/usb/gspca/gspca_se401.ko
kernel/drivers/media/usb/gspca/gspca_sn9c2028.ko
kernel/drivers/media/usb/gspca/gspca_sn9c20x.ko
kernel/drivers/media/usb/gspca/gspca_sonixb.ko
kernel/drivers/media/usb/gspca/gspca_sonixj.ko
kernel/drivers/media/usb/gspca/gspca_spca500.ko
kernel/drivers/media/usb/gspca/gspca_spca501.ko
kernel/drivers/media/usb/gspca/gspca_spca505.ko
kernel/drivers/media/usb/gspca/gspca_spca506.ko
kernel/drivers/media/usb/gspca/gspca_spca508.ko
kernel/drivers/media/usb/gspca/gspca_spca561.ko
kernel/drivers/media/usb/gspca/gspca_spca1528.ko
kernel/drivers/media/usb/gspca/gspca_sq905.ko
kernel/drivers/media/usb/gspca/gspca_sq905c.ko
kernel/drivers/media/usb/gspca/gspca_sq930x.ko
kernel/drivers/media/usb/gspca/gspca_sunplus.ko
kernel/drivers/media/usb/gspca/gspca_stk014.ko
kernel/drivers/media/usb/gspca/gspca_stv0680.ko
kernel/drivers/media/usb/gspca/gspca_t613.ko
kernel/drivers/media/usb/gspca/gspca_topro.ko
kernel/drivers/media/usb/gspca/gspca_tv8532.ko
kernel/drivers/media/usb/gspca/gspca_vc032x.ko
kernel/drivers/media/usb/gspca/gspca_vicam.ko
kernel/drivers/media/usb/gspca/gspca_xirlink_cit.ko
kernel/drivers/media/usb/gspca/gspca_zc3xx.ko
kernel/drivers/media/usb/gspca/m5602/gspca_m5602.ko
kernel/drivers/media/usb/gspca/stv06xx/gspca_stv06xx.ko
kernel/drivers/media/usb/gspca/gl860/gspca_gl860.ko
kernel/drivers/media/usb/pwc/pwc.ko
kernel/drivers/media/usb/cpia2/cpia2.ko
kernel/drivers/media/usb/au0828/au0828.ko
kernel/drivers/media/usb/hdpvr/hdpvr.ko
kernel/drivers/media/usb/pvrusb2/pvrusb2.ko
kernel/drivers/media/usb/tlg2300/poseidon.ko
kernel/drivers/media/usb/usbvision/usbvision.ko
kernel/drivers/media/usb/stk1160/stk1160.ko
kernel/drivers/media/usb/cx231xx/cx231xx.ko
kernel/drivers/media/usb/cx231xx/cx231xx-alsa.ko
kernel/drivers/media/usb/cx231xx/cx231xx-dvb.ko
kernel/drivers/media/usb/tm6000/tm6000.ko
kernel/drivers/media/usb/tm6000/tm6000-alsa.ko
kernel/drivers/media/usb/tm6000/tm6000-dvb.ko
kernel/drivers/media/usb/em28xx/em28xx.ko
kernel/drivers/media/usb/em28xx/em28xx-alsa.ko
kernel/drivers/media/usb/em28xx/em28xx-dvb.ko
kernel/drivers/media/usb/em28xx/em28xx-rc.ko
kernel/drivers/media/mmc/siano/smssdio.ko
kernel/drivers/media/firewire/firedtv.ko
kernel/drivers/media/parport/c-qcam.ko
kernel/drivers/media/parport/bw-qcam.ko
kernel/drivers/media/parport/w9966.ko
kernel/drivers/media/dvb-frontends/dvb-pll.ko
kernel/drivers/media/dvb-frontends/stv0299.ko
kernel/drivers/media/dvb-frontends/stb0899.ko
kernel/drivers/media/dvb-frontends/stb6100.ko
kernel/drivers/media/dvb-frontends/sp8870.ko
kernel/drivers/media/dvb-frontends/cx22700.ko
kernel/drivers/media/dvb-frontends/cx24110.ko
kernel/drivers/media/dvb-frontends/tda8083.ko
kernel/drivers/media/dvb-frontends/l64781.ko
kernel/drivers/media/dvb-frontends/dib3000mb.ko
kernel/drivers/media/dvb-frontends/dib3000mc.ko
kernel/drivers/media/dvb-frontends/dibx000_common.ko
kernel/drivers/media/dvb-frontends/dib7000m.ko
kernel/drivers/media/dvb-frontends/dib7000p.ko
kernel/drivers/media/dvb-frontends/dib8000.ko
kernel/drivers/media/dvb-frontends/mt312.ko
kernel/drivers/media/dvb-frontends/ves1820.ko
kernel/drivers/media/dvb-frontends/ves1x93.ko
kernel/drivers/media/dvb-frontends/tda1004x.ko
kernel/drivers/media/dvb-frontends/sp887x.ko
kernel/drivers/media/dvb-frontends/nxt6000.ko
kernel/drivers/media/dvb-frontends/mt352.ko
kernel/drivers/media/dvb-frontends/zl10036.ko
kernel/drivers/media/dvb-frontends/zl10039.ko
kernel/drivers/media/dvb-frontends/zl10353.ko
kernel/drivers/media/dvb-frontends/cx22702.ko
kernel/drivers/media/dvb-frontends/drxd.ko
kernel/drivers/media/dvb-frontends/tda10021.ko
kernel/drivers/media/dvb-frontends/tda10023.ko
kernel/drivers/media/dvb-frontends/stv0297.ko
kernel/drivers/media/dvb-frontends/nxt200x.ko
kernel/drivers/media/dvb-frontends/or51211.ko
kernel/drivers/media/dvb-frontends/or51132.ko
kernel/drivers/media/dvb-frontends/bcm3510.ko
kernel/drivers/media/dvb-frontends/s5h1420.ko
kernel/drivers/media/dvb-frontends/lgdt330x.ko
kernel/drivers/media/dvb-frontends/lgdt3305.ko
kernel/drivers/media/dvb-frontends/lg2160.ko
kernel/drivers/media/dvb-frontends/cx24123.ko
kernel/drivers/media/dvb-frontends/lnbp21.ko
kernel/drivers/media/dvb-frontends/lnbp22.ko
kernel/drivers/media/dvb-frontends/isl6405.ko
kernel/drivers/media/dvb-frontends/isl6421.ko
kernel/drivers/media/dvb-frontends/tda10086.ko
kernel/drivers/media/dvb-frontends/tda826x.ko
kernel/drivers/media/dvb-frontends/tda8261.ko
kernel/drivers/media/dvb-frontends/dib0070.ko
kernel/drivers/media/dvb-frontends/dib0090.ko
kernel/drivers/media/dvb-frontends/tua6100.ko
kernel/drivers/media/dvb-frontends/s5h1409.ko
kernel/drivers/media/dvb-frontends/itd1000.ko
kernel/drivers/media/dvb-frontends/au8522_common.ko
kernel/drivers/media/dvb-frontends/au8522_dig.ko
kernel/drivers/media/dvb-frontends/au8522_decoder.ko
kernel/drivers/media/dvb-frontends/tda10048.ko
kernel/drivers/media/dvb-frontends/cx24113.ko
kernel/drivers/media/dvb-frontends/s5h1411.ko
kernel/drivers/media/dvb-frontends/tda665x.ko
kernel/drivers/media/dvb-frontends/lgs8gxx.ko
kernel/drivers/media/dvb-frontends/atbm8830.ko
kernel/drivers/media/dvb-frontends/af9013.ko
kernel/drivers/media/dvb-frontends/cx24116.ko
kernel/drivers/media/dvb-frontends/si21xx.ko
kernel/drivers/media/dvb-frontends/stv0288.ko
kernel/drivers/media/dvb-frontends/stb6000.ko
kernel/drivers/media/dvb-frontends/s921.ko
kernel/drivers/media/dvb-frontends/stv6110.ko
kernel/drivers/media/dvb-frontends/stv0900.ko
kernel/drivers/media/dvb-frontends/stv090x.ko
kernel/drivers/media/dvb-frontends/stv6110x.ko
kernel/drivers/media/dvb-frontends/isl6423.ko
kernel/drivers/media/dvb-frontends/ec100.ko
kernel/drivers/media/dvb-frontends/ds3000.ko
kernel/drivers/media/dvb-frontends/mb86a16.ko
kernel/drivers/media/dvb-frontends/mb86a20s.ko
kernel/drivers/media/dvb-frontends/ix2505v.ko
kernel/drivers/media/dvb-frontends/stv0367.ko
kernel/drivers/media/dvb-frontends/cxd2820r.ko
kernel/drivers/media/dvb-frontends/drxk.ko
kernel/drivers/media/dvb-frontends/tda18271c2dd.ko
kernel/drivers/media/dvb-frontends/it913x-fe.ko
kernel/drivers/media/dvb-frontends/a8293.ko
kernel/drivers/media/dvb-frontends/tda10071.ko
kernel/drivers/media/dvb-frontends/rtl2830.ko
kernel/drivers/media/dvb-frontends/rtl2832.ko
kernel/drivers/media/dvb-frontends/m88rs2000.ko
kernel/drivers/media/dvb-frontends/af9033.ko
kernel/drivers/media/v4l2-core/videodev.ko
kernel/drivers/media/v4l2-core/v4l2-int-device.ko
kernel/drivers/media/v4l2-core/v4l2-common.ko
kernel/drivers/media/v4l2-core/tuner.ko
kernel/drivers/media/v4l2-core/v4l2-mem2mem.ko
kernel/drivers/media/v4l2-core/videobuf-core.ko
kernel/drivers/media/v4l2-core/videobuf-dma-sg.ko
kernel/drivers/media/v4l2-core/videobuf-dma-contig.ko
kernel/drivers/media/v4l2-core/videobuf-vmalloc.ko
kernel/drivers/media/v4l2-core/videobuf-dvb.ko
kernel/drivers/media/v4l2-core/videobuf2-core.ko
kernel/drivers/media/v4l2-core/videobuf2-memops.ko
kernel/drivers/media/v4l2-core/videobuf2-vmalloc.ko
kernel/drivers/media/v4l2-core/videobuf2-dma-contig.ko
kernel/drivers/media/dvb-core/dvb-core.ko
kernel/drivers/media/radio/si470x/radio-usb-si470x.ko
kernel/drivers/media/radio/si470x/radio-i2c-si470x.ko
kernel/drivers/media/radio/radio-maxiradio.ko
kernel/drivers/media/radio/radio-shark.ko
kernel/drivers/media/radio/shark2.ko
kernel/drivers/media/radio/si4713-i2c.ko
kernel/drivers/media/radio/radio-si4713.ko
kernel/drivers/media/radio/dsbr100.ko
kernel/drivers/media/radio/radio-mr800.ko
kernel/drivers/media/radio/radio-keene.ko
kernel/drivers/media/radio/radio-tea5764.ko
kernel/drivers/media/radio/saa7706h.ko
kernel/drivers/media/radio/tef6862.ko
kernel/drivers/media/radio/radio-timb.ko
kernel/drivers/media/radio/radio-wl1273.ko
kernel/drivers/media/radio/wl128x/fm_drv.ko
kernel/drivers/power/generic-adc-battery.ko
kernel/drivers/power/pda_power.ko
kernel/drivers/power/max8925_power.ko
kernel/drivers/power/wm831x_backup.ko
kernel/drivers/power/wm831x_power.ko
kernel/drivers/power/wm8350_power.ko
kernel/drivers/power/test_power.ko
kernel/drivers/power/88pm860x_battery.ko
kernel/drivers/power/ds2760_battery.ko
kernel/drivers/power/ds2780_battery.ko
kernel/drivers/power/ds2781_battery.ko
kernel/drivers/power/ds2782_battery.ko
kernel/drivers/power/sbs-battery.ko
kernel/drivers/power/bq27x00_battery.ko
kernel/drivers/power/da9030_battery.ko
kernel/drivers/power/da9052-battery.ko
kernel/drivers/power/max17040_battery.ko
kernel/drivers/power/max17042_battery.ko
kernel/drivers/power/88pm860x_charger.ko
kernel/drivers/power/pcf50633-charger.ko
kernel/drivers/power/rx51_battery.ko
kernel/drivers/power/isp1704_charger.ko
kernel/drivers/power/max8903_charger.ko
kernel/drivers/power/twl4030_charger.ko
kernel/drivers/power/lp8727_charger.ko
kernel/drivers/power/lp8788-charger.ko
kernel/drivers/power/gpio-charger.ko
kernel/drivers/power/max8997_charger.ko
kernel/drivers/power/max8998_charger.ko
kernel/drivers/power/bq2415x_charger.ko
kernel/drivers/power/smb347-charger.ko
kernel/drivers/hwmon/hwmon-vid.ko
kernel/drivers/hwmon/acpi_power_meter.ko
kernel/drivers/hwmon/asus_atk0110.ko
kernel/drivers/hwmon/asb100.ko
kernel/drivers/hwmon/w83627hf.ko
kernel/drivers/hwmon/w83792d.ko
kernel/drivers/hwmon/w83793.ko
kernel/drivers/hwmon/w83795.ko
kernel/drivers/hwmon/w83781d.ko
kernel/drivers/hwmon/w83791d.ko
kernel/drivers/hwmon/abituguru.ko
kernel/drivers/hwmon/abituguru3.ko
kernel/drivers/hwmon/ad7314.ko
kernel/drivers/hwmon/ad7414.ko
kernel/drivers/hwmon/ad7418.ko
kernel/drivers/hwmon/adcxx.ko
kernel/drivers/hwmon/adm1021.ko
kernel/drivers/hwmon/adm1025.ko
kernel/drivers/hwmon/adm1026.ko
kernel/drivers/hwmon/adm1029.ko
kernel/drivers/hwmon/adm1031.ko
kernel/drivers/hwmon/adm9240.ko
kernel/drivers/hwmon/ads1015.ko
kernel/drivers/hwmon/ads7828.ko
kernel/drivers/hwmon/ads7871.ko
kernel/drivers/hwmon/adt7411.ko
kernel/drivers/hwmon/adt7462.ko
kernel/drivers/hwmon/adt7470.ko
kernel/drivers/hwmon/adt7475.ko
kernel/drivers/hwmon/applesmc.ko
kernel/drivers/hwmon/asc7621.ko
kernel/drivers/hwmon/atxp1.ko
kernel/drivers/hwmon/coretemp.ko
kernel/drivers/hwmon/da9052-hwmon.ko
kernel/drivers/hwmon/da9055-hwmon.ko
kernel/drivers/hwmon/dme1737.ko
kernel/drivers/hwmon/ds620.ko
kernel/drivers/hwmon/ds1621.ko
kernel/drivers/hwmon/emc1403.ko
kernel/drivers/hwmon/emc2103.ko
kernel/drivers/hwmon/emc6w201.ko
kernel/drivers/hwmon/f71805f.ko
kernel/drivers/hwmon/f71882fg.ko
kernel/drivers/hwmon/f75375s.ko
kernel/drivers/hwmon/fam15h_power.ko
kernel/drivers/hwmon/fschmd.ko
kernel/drivers/hwmon/g760a.ko
kernel/drivers/hwmon/gl518sm.ko
kernel/drivers/hwmon/gl520sm.ko
kernel/drivers/hwmon/gpio-fan.ko
kernel/drivers/hwmon/hih6130.ko
kernel/drivers/hwmon/i5k_amb.ko
kernel/drivers/hwmon/ibmaem.ko
kernel/drivers/hwmon/ibmpex.ko
kernel/drivers/hwmon/ina2xx.ko
kernel/drivers/hwmon/it87.ko
kernel/drivers/hwmon/jc42.ko
kernel/drivers/hwmon/k8temp.ko
kernel/drivers/hwmon/k10temp.ko
kernel/drivers/hwmon/lineage-pem.ko
kernel/drivers/hwmon/lm63.ko
kernel/drivers/hwmon/lm70.ko
kernel/drivers/hwmon/lm73.ko
kernel/drivers/hwmon/lm75.ko
kernel/drivers/hwmon/lm77.ko
kernel/drivers/hwmon/lm78.ko
kernel/drivers/hwmon/lm80.ko
kernel/drivers/hwmon/lm83.ko
kernel/drivers/hwmon/lm85.ko
kernel/drivers/hwmon/lm87.ko
kernel/drivers/hwmon/lm90.ko
kernel/drivers/hwmon/lm92.ko
kernel/drivers/hwmon/lm93.ko
kernel/drivers/hwmon/lm95241.ko
kernel/drivers/hwmon/lm95245.ko
kernel/drivers/hwmon/ltc4151.ko
kernel/drivers/hwmon/ltc4215.ko
kernel/drivers/hwmon/ltc4245.ko
kernel/drivers/hwmon/ltc4261.ko
kernel/drivers/hwmon/max1111.ko
kernel/drivers/hwmon/max16065.ko
kernel/drivers/hwmon/max1619.ko
kernel/drivers/hwmon/max1668.ko
kernel/drivers/hwmon/max197.ko
kernel/drivers/hwmon/max6639.ko
kernel/drivers/hwmon/max6642.ko
kernel/drivers/hwmon/max6650.ko
kernel/drivers/hwmon/mc13783-adc.ko
kernel/drivers/hwmon/mcp3021.ko
kernel/drivers/hwmon/ntc_thermistor.ko
kernel/drivers/hwmon/pc87360.ko
kernel/drivers/hwmon/pc87427.ko
kernel/drivers/hwmon/pcf8591.ko
kernel/drivers/hwmon/sch56xx-common.ko
kernel/drivers/hwmon/sch5627.ko
kernel/drivers/hwmon/sch5636.ko
kernel/drivers/hwmon/sht15.ko
kernel/drivers/hwmon/sht21.ko
kernel/drivers/hwmon/sis5595.ko
kernel/drivers/hwmon/smm665.ko
kernel/drivers/hwmon/smsc47b397.ko
kernel/drivers/hwmon/smsc47m1.ko
kernel/drivers/hwmon/smsc47m192.ko
kernel/drivers/hwmon/amc6821.ko
kernel/drivers/hwmon/thmc50.ko
kernel/drivers/hwmon/tmp102.ko
kernel/drivers/hwmon/tmp401.ko
kernel/drivers/hwmon/tmp421.ko
kernel/drivers/hwmon/twl4030-madc-hwmon.ko
kernel/drivers/hwmon/via-cputemp.ko
kernel/drivers/hwmon/via686a.ko
kernel/drivers/hwmon/vt1211.ko
kernel/drivers/hwmon/vt8231.ko
kernel/drivers/hwmon/w83627ehf.ko
kernel/drivers/hwmon/w83l785ts.ko
kernel/drivers/hwmon/w83l786ng.ko
kernel/drivers/hwmon/wm831x-hwmon.ko
kernel/drivers/hwmon/wm8350-hwmon.ko
kernel/drivers/hwmon/pmbus/pmbus_core.ko
kernel/drivers/hwmon/pmbus/pmbus.ko
kernel/drivers/hwmon/pmbus/adm1275.ko
kernel/drivers/hwmon/pmbus/lm25066.ko
kernel/drivers/hwmon/pmbus/ltc2978.ko
kernel/drivers/hwmon/pmbus/max16064.ko
kernel/drivers/hwmon/pmbus/max34440.ko
kernel/drivers/hwmon/pmbus/max8688.ko
kernel/drivers/hwmon/pmbus/ucd9000.ko
kernel/drivers/hwmon/pmbus/ucd9200.ko
kernel/drivers/hwmon/pmbus/zl6100.ko
kernel/drivers/watchdog/pcwd_pci.ko
kernel/drivers/watchdog/wdt_pci.ko
kernel/drivers/watchdog/pcwd_usb.ko
kernel/drivers/watchdog/twl4030_wdt.ko
kernel/drivers/watchdog/acquirewdt.ko
kernel/drivers/watchdog/advantechwdt.ko
kernel/drivers/watchdog/alim1535_wdt.ko
kernel/drivers/watchdog/alim7101_wdt.ko
kernel/drivers/watchdog/f71808e_wdt.ko
kernel/drivers/watchdog/sp5100_tco.ko
kernel/drivers/watchdog/sc520_wdt.ko
kernel/drivers/watchdog/sbc_fitpc2_wdt.ko
kernel/drivers/watchdog/eurotechwdt.ko
kernel/drivers/watchdog/ib700wdt.ko
kernel/drivers/watchdog/ibmasr.ko
kernel/drivers/watchdog/wafer5823wdt.ko
kernel/drivers/watchdog/i6300esb.ko
kernel/drivers/watchdog/ie6xx_wdt.ko
kernel/drivers/watchdog/iTCO_wdt.ko
kernel/drivers/watchdog/iTCO_vendor_support.ko
kernel/drivers/watchdog/it8712f_wdt.ko
kernel/drivers/watchdog/it87_wdt.ko
kernel/drivers/watchdog/hpwdt.ko
kernel/drivers/watchdog/sc1200wdt.ko
kernel/drivers/watchdog/pc87413_wdt.ko
kernel/drivers/watchdog/nv_tco.ko
kernel/drivers/watchdog/sbc60xxwdt.ko
kernel/drivers/watchdog/sbc8360.ko
kernel/drivers/watchdog/cpu5wdt.ko
kernel/drivers/watchdog/sch311x_wdt.ko
kernel/drivers/watchdog/smsc37b787_wdt.ko
kernel/drivers/watchdog/via_wdt.ko
kernel/drivers/watchdog/w83627hf_wdt.ko
kernel/drivers/watchdog/w83697hf_wdt.ko
kernel/drivers/watchdog/w83697ug_wdt.ko
kernel/drivers/watchdog/w83877f_wdt.ko
kernel/drivers/watchdog/w83977f_wdt.ko
kernel/drivers/watchdog/machzwd.ko
kernel/drivers/watchdog/sbc_epx_c3.ko
kernel/drivers/watchdog/xen_wdt.ko
kernel/drivers/watchdog/da9052_wdt.ko
kernel/drivers/watchdog/da9055_wdt.ko
kernel/drivers/watchdog/wm831x_wdt.ko
kernel/drivers/watchdog/wm8350_wdt.ko
kernel/drivers/watchdog/softdog.ko
kernel/drivers/md/linear.ko
kernel/drivers/md/raid0.ko
kernel/drivers/md/raid1.ko
kernel/drivers/md/raid10.ko
kernel/drivers/md/raid456.ko
kernel/drivers/md/multipath.ko
kernel/drivers/md/faulty.ko
kernel/drivers/md/dm-bufio.ko
kernel/drivers/md/dm-bio-prison.ko
kernel/drivers/md/dm-crypt.ko
kernel/drivers/md/dm-delay.ko
kernel/drivers/md/dm-flakey.ko
kernel/drivers/md/dm-multipath.ko
kernel/drivers/md/dm-round-robin.ko
kernel/drivers/md/dm-queue-length.ko
kernel/drivers/md/dm-service-time.ko
kernel/drivers/md/dm-snapshot.ko
kernel/drivers/md/persistent-data/dm-persistent-data.ko
kernel/drivers/md/dm-mirror.ko
kernel/drivers/md/dm-log.ko
kernel/drivers/md/dm-region-hash.ko
kernel/drivers/md/dm-log-userspace.ko
kernel/drivers/md/dm-zero.ko
kernel/drivers/md/dm-raid.ko
kernel/drivers/md/dm-thin-pool.ko
kernel/drivers/md/dm-verity.ko
kernel/drivers/isdn/hardware/avm/b1pci.ko
kernel/drivers/isdn/hardware/avm/b1.ko
kernel/drivers/isdn/hardware/avm/b1dma.ko
kernel/drivers/isdn/hardware/avm/b1pcmcia.ko
kernel/drivers/isdn/hardware/avm/avm_cs.ko
kernel/drivers/isdn/hardware/avm/t1pci.ko
kernel/drivers/isdn/hardware/avm/c4.ko
kernel/drivers/isdn/hardware/eicon/divadidd.ko
kernel/drivers/isdn/hardware/eicon/divas.ko
kernel/drivers/isdn/hardware/eicon/diva_mnt.ko
kernel/drivers/isdn/hardware/eicon/diva_idi.ko
kernel/drivers/isdn/hardware/eicon/divacapi.ko
kernel/drivers/isdn/hardware/mISDN/hfcpci.ko
kernel/drivers/isdn/hardware/mISDN/hfcmulti.ko
kernel/drivers/isdn/hardware/mISDN/hfcsusb.ko
kernel/drivers/isdn/hardware/mISDN/avmfritz.ko
kernel/drivers/isdn/hardware/mISDN/speedfax.ko
kernel/drivers/isdn/hardware/mISDN/mISDNinfineon.ko
kernel/drivers/isdn/hardware/mISDN/w6692.ko
kernel/drivers/isdn/hardware/mISDN/netjet.ko
kernel/drivers/isdn/hardware/mISDN/mISDNipac.ko
kernel/drivers/isdn/hardware/mISDN/mISDNisar.ko
kernel/drivers/isdn/i4l/isdn.ko
kernel/drivers/isdn/i4l/isdn_bsdcomp.ko
kernel/drivers/isdn/i4l/isdnhdlc.ko
kernel/drivers/isdn/capi/kernelcapi.ko
kernel/drivers/isdn/capi/capi.ko
kernel/drivers/isdn/capi/capidrv.ko
kernel/drivers/isdn/mISDN/mISDN_core.ko
kernel/drivers/isdn/mISDN/mISDN_dsp.ko
kernel/drivers/isdn/mISDN/l1oip.ko
kernel/drivers/isdn/divert/dss1_divert.ko
kernel/drivers/isdn/hisax/hisax.ko
kernel/drivers/isdn/hisax/sedlbauer_cs.ko
kernel/drivers/isdn/hisax/elsa_cs.ko
kernel/drivers/isdn/hisax/avma1_cs.ko
kernel/drivers/isdn/hisax/teles_cs.ko
kernel/drivers/isdn/hisax/hisax_st5481.ko
kernel/drivers/isdn/hisax/hfc_usb.ko
kernel/drivers/isdn/hisax/hfc4s8s_l1.ko
kernel/drivers/isdn/hisax/hisax_isac.ko
kernel/drivers/isdn/hisax/hisax_fcpcipnp.ko
kernel/drivers/isdn/hysdn/hysdn.ko
kernel/drivers/isdn/gigaset/gigaset.ko
kernel/drivers/isdn/gigaset/usb_gigaset.ko
kernel/drivers/isdn/gigaset/bas_gigaset.ko
kernel/drivers/isdn/gigaset/ser_gigaset.ko
kernel/drivers/edac/edac_core.ko
kernel/drivers/edac/mce_amd_inj.ko
kernel/drivers/edac/edac_mce_amd.ko
kernel/drivers/edac/i5000_edac.ko
kernel/drivers/edac/i5100_edac.ko
kernel/drivers/edac/i5400_edac.ko
kernel/drivers/edac/i7300_edac.ko
kernel/drivers/edac/i7core_edac.ko
kernel/drivers/edac/sb_edac.ko
kernel/drivers/edac/e752x_edac.ko
kernel/drivers/edac/i82975x_edac.ko
kernel/drivers/edac/i3000_edac.ko
kernel/drivers/edac/i3200_edac.ko
kernel/drivers/edac/x38_edac.ko
kernel/drivers/edac/amd64_edac_mod.ko
kernel/drivers/cpufreq/speedstep-lib.ko
kernel/drivers/cpufreq/p4-clockmod.ko
kernel/drivers/mmc/card/mmc_block.ko
kernel/drivers/mmc/card/sdio_uart.ko
kernel/drivers/mmc/host/sdhci.ko
kernel/drivers/mmc/host/sdhci-pci.ko
kernel/drivers/mmc/host/sdhci-acpi.ko
kernel/drivers/mmc/host/wbsd.ko
kernel/drivers/mmc/host/tifm_sd.ko
kernel/drivers/mmc/host/mmc_spi.ko
kernel/drivers/mmc/host/sdricoh_cs.ko
kernel/drivers/mmc/host/cb710-mmc.ko
kernel/drivers/mmc/host/via-sdmmc.ko
kernel/drivers/mmc/host/vub300.ko
kernel/drivers/mmc/host/ushc.ko
kernel/drivers/mmc/host/rtsx_pci_sdmmc.ko
kernel/drivers/mmc/host/sdhci-pltfm.ko
kernel/drivers/leds/leds-88pm860x.ko
kernel/drivers/leds/leds-bd2802.ko
kernel/drivers/leds/leds-lm3530.ko
kernel/drivers/leds/leds-lm3533.ko
kernel/drivers/leds/leds-lm3642.ko
kernel/drivers/leds/leds-pca9532.ko
kernel/drivers/leds/leds-gpio.ko
kernel/drivers/leds/leds-lp3944.ko
kernel/drivers/leds/leds-lp5521.ko
kernel/drivers/leds/leds-lp5523.ko
kernel/drivers/leds/leds-lp8788.ko
kernel/drivers/leds/leds-tca6507.ko
kernel/drivers/leds/leds-clevo-mail.ko
kernel/drivers/leds/leds-ot200.ko
kernel/drivers/leds/leds-pca955x.ko
kernel/drivers/leds/leds-pca9633.ko
kernel/drivers/leds/leds-da903x.ko
kernel/drivers/leds/leds-da9052.ko
kernel/drivers/leds/leds-wm831x-status.ko
kernel/drivers/leds/leds-wm8350.ko
kernel/drivers/leds/leds-regulator.ko
kernel/drivers/leds/leds-ss4200.ko
kernel/drivers/leds/leds-lt3593.ko
kernel/drivers/leds/leds-adp5520.ko
kernel/drivers/leds/dell-led.ko
kernel/drivers/leds/leds-mc13783.ko
kernel/drivers/leds/leds-max8997.ko
kernel/drivers/leds/leds-lm355x.ko
kernel/drivers/leds/leds-blinkm.ko
kernel/drivers/leds/leds-dac124s085.ko
kernel/drivers/leds/ledtrig-timer.ko
kernel/drivers/leds/ledtrig-oneshot.ko
kernel/drivers/leds/ledtrig-heartbeat.ko
kernel/drivers/leds/ledtrig-backlight.ko
kernel/drivers/leds/ledtrig-gpio.ko
kernel/drivers/leds/ledtrig-default-on.ko
kernel/drivers/leds/ledtrig-transient.ko
kernel/drivers/firmware/dmi-sysfs.ko
kernel/drivers/firmware/dell_rbu.ko
kernel/drivers/firmware/dcdbas.ko
kernel/drivers/firmware/iscsi_ibft.ko
kernel/drivers/crypto/padlock-aes.ko
kernel/drivers/crypto/padlock-sha.ko
kernel/drivers/staging/media/lirc/lirc_bt829.ko
kernel/drivers/staging/media/lirc/lirc_igorplugusb.ko
kernel/drivers/staging/media/lirc/lirc_imon.ko
kernel/drivers/staging/media/lirc/lirc_parallel.ko
kernel/drivers/staging/media/lirc/lirc_sasem.ko
kernel/drivers/staging/media/lirc/lirc_serial.ko
kernel/drivers/staging/media/lirc/lirc_sir.ko
kernel/drivers/staging/media/lirc/lirc_zilog.ko
kernel/drivers/staging/media/as102/dvb-as102.ko
kernel/drivers/staging/media/cxd2099/cxd2099.ko
kernel/drivers/staging/media/solo6x10/solo6x10.ko
kernel/drivers/staging/media/dt3155v4l/dt3155v4l.ko
kernel/drivers/staging/media/go7007/go7007.ko
kernel/drivers/staging/media/go7007/go7007-usb.ko
kernel/drivers/staging/media/go7007/s2250.ko
kernel/drivers/staging/media/go7007/s2250-loader.ko
kernel/drivers/staging/media/go7007/wis-saa7113.ko
kernel/drivers/staging/media/go7007/wis-ov7640.ko
kernel/drivers/staging/media/go7007/wis-saa7115.ko
kernel/drivers/staging/media/go7007/wis-tw9903.ko
kernel/drivers/staging/media/go7007/wis-uda1342.ko
kernel/drivers/staging/media/go7007/wis-sony-tuner.ko
kernel/drivers/staging/media/go7007/wis-tw2804.ko
kernel/drivers/staging/android/logger.ko
kernel/drivers/staging/android/timed_gpio.ko
kernel/drivers/staging/silicom/bpctl_mod.ko
kernel/drivers/staging/silicom/bypasslib/bypass.ko
kernel/drivers/staging/et131x/et131x.ko
kernel/drivers/staging/slicoss/slicoss.ko
kernel/drivers/staging/usbip/usbip-core.ko
kernel/drivers/staging/usbip/vhci-hcd.ko
kernel/drivers/staging/usbip/usbip-host.ko
kernel/drivers/staging/winbond/w35und.ko
kernel/drivers/staging/wlan-ng/prism2_usb.ko
kernel/drivers/staging/echo/echo.ko
kernel/drivers/staging/comedi/comedi.ko
kernel/drivers/staging/comedi/kcomedilib/kcomedilib.ko
kernel/drivers/staging/comedi/drivers/pcm_common.ko
kernel/drivers/staging/comedi/drivers/comedi_bond.ko
kernel/drivers/staging/comedi/drivers/comedi_test.ko
kernel/drivers/staging/comedi/drivers/comedi_parport.ko
kernel/drivers/staging/comedi/drivers/serial2002.ko
kernel/drivers/staging/comedi/drivers/skel.ko
kernel/drivers/staging/comedi/drivers/8255_pci.ko
kernel/drivers/staging/comedi/drivers/addi_apci_035.ko
kernel/drivers/staging/comedi/drivers/addi_apci_1032.ko
kernel/drivers/staging/comedi/drivers/addi_apci_1500.ko
kernel/drivers/staging/comedi/drivers/addi_apci_1516.ko
kernel/drivers/staging/comedi/drivers/addi_apci_1564.ko
kernel/drivers/staging/comedi/drivers/addi_apci_16xx.ko
kernel/drivers/staging/comedi/drivers/addi_apci_2032.ko
kernel/drivers/staging/comedi/drivers/addi_apci_2200.ko
kernel/drivers/staging/comedi/drivers/addi_apci_3120.ko
kernel/drivers/staging/comedi/drivers/addi_apci_3501.ko
kernel/drivers/staging/comedi/drivers/addi_apci_3xxx.ko
kernel/drivers/staging/comedi/drivers/adl_pci6208.ko
kernel/drivers/staging/comedi/drivers/adl_pci7x3x.ko
kernel/drivers/staging/comedi/drivers/adl_pci8164.ko
kernel/drivers/staging/comedi/drivers/adl_pci9111.ko
kernel/drivers/staging/comedi/drivers/adl_pci9118.ko
kernel/drivers/staging/comedi/drivers/adv_pci1710.ko
kernel/drivers/staging/comedi/drivers/adv_pci1723.ko
kernel/drivers/staging/comedi/drivers/adv_pci_dio.ko
kernel/drivers/staging/comedi/drivers/amplc_dio200.ko
kernel/drivers/staging/comedi/drivers/amplc_pc236.ko
kernel/drivers/staging/comedi/drivers/amplc_pc263.ko
kernel/drivers/staging/comedi/drivers/amplc_pci224.ko
kernel/drivers/staging/comedi/drivers/amplc_pci230.ko
kernel/drivers/staging/comedi/drivers/contec_pci_dio.ko
kernel/drivers/staging/comedi/drivers/dt3000.ko
kernel/drivers/staging/comedi/drivers/dyna_pci10xx.ko
kernel/drivers/staging/comedi/drivers/unioxx5.ko
kernel/drivers/staging/comedi/drivers/gsc_hpdi.ko
kernel/drivers/staging/comedi/drivers/icp_multi.ko
kernel/drivers/staging/comedi/drivers/ii_pci20kc.ko
kernel/drivers/staging/comedi/drivers/daqboard2000.ko
kernel/drivers/staging/comedi/drivers/jr3_pci.ko
kernel/drivers/staging/comedi/drivers/ke_counter.ko
kernel/drivers/staging/comedi/drivers/cb_pcidas64.ko
kernel/drivers/staging/comedi/drivers/cb_pcidas.ko
kernel/drivers/staging/comedi/drivers/cb_pcidda.ko
kernel/drivers/staging/comedi/drivers/cb_pcimdas.ko
kernel/drivers/staging/comedi/drivers/cb_pcimdda.ko
kernel/drivers/staging/comedi/drivers/me4000.ko
kernel/drivers/staging/comedi/drivers/me_daq.ko
kernel/drivers/staging/comedi/drivers/ni_6527.ko
kernel/drivers/staging/comedi/drivers/ni_65xx.ko
kernel/drivers/staging/comedi/drivers/ni_660x.ko
kernel/drivers/staging/comedi/drivers/ni_670x.ko
kernel/drivers/staging/comedi/drivers/ni_pcidio.ko
kernel/drivers/staging/comedi/drivers/ni_pcimio.ko
kernel/drivers/staging/comedi/drivers/rtd520.ko
kernel/drivers/staging/comedi/drivers/s526.ko
kernel/drivers/staging/comedi/drivers/s626.ko
kernel/drivers/staging/comedi/drivers/ssv_dnp.ko
kernel/drivers/staging/comedi/drivers/cb_das16_cs.ko
kernel/drivers/staging/comedi/drivers/das08_cs.ko
kernel/drivers/staging/comedi/drivers/ni_daq_700.ko
kernel/drivers/staging/comedi/drivers/ni_daq_dio24.ko
kernel/drivers/staging/comedi/drivers/ni_labpc_cs.ko
kernel/drivers/staging/comedi/drivers/ni_mio_cs.ko
kernel/drivers/staging/comedi/drivers/quatech_daqp_cs.ko
kernel/drivers/staging/comedi/drivers/dt9812.ko
kernel/drivers/staging/comedi/drivers/usbdux.ko
kernel/drivers/staging/comedi/drivers/usbduxfast.ko
kernel/drivers/staging/comedi/drivers/usbduxsigma.ko
kernel/drivers/staging/comedi/drivers/vmk80xx.ko
kernel/drivers/staging/comedi/drivers/mite.ko
kernel/drivers/staging/comedi/drivers/ni_tio.ko
kernel/drivers/staging/comedi/drivers/ni_tiocmd.ko
kernel/drivers/staging/comedi/drivers/ni_labpc.ko
kernel/drivers/staging/comedi/drivers/8255.ko
kernel/drivers/staging/comedi/drivers/das08.ko
kernel/drivers/staging/comedi/drivers/comedi_fc.ko
kernel/drivers/staging/asus_oled/asus_oled.ko
kernel/drivers/staging/panel/panel.ko
kernel/drivers/staging/rtl8187se/r8187se.ko
kernel/drivers/staging/rtl8192u/r8192u_usb.ko
kernel/drivers/staging/rtl8192e/rtllib.ko
kernel/drivers/staging/rtl8192e/rtllib_crypt_ccmp.ko
kernel/drivers/staging/rtl8192e/rtllib_crypt_tkip.ko
kernel/drivers/staging/rtl8192e/rtllib_crypt_wep.ko
kernel/drivers/staging/rtl8192e/rtl8192e/r8192e_pci.ko
kernel/drivers/staging/rtl8712/r8712u.ko
kernel/drivers/staging/rts5139/rts5139.ko
kernel/drivers/staging/frontier/tranzport.ko
kernel/drivers/staging/frontier/alphatrack.ko
kernel/drivers/staging/phison/phison.ko
kernel/drivers/staging/line6/line6usb.ko
kernel/drivers/staging/serqt_usb2/serqt_usb2.ko
kernel/drivers/staging/vt6655/vt6655_stage.ko
kernel/drivers/staging/vt6656/vt6656_stage.ko
kernel/drivers/staging/vme/devices/vme_user.ko
kernel/drivers/staging/vme/devices/vme_pio2.ko
kernel/drivers/staging/sep/sep_driver.ko
kernel/drivers/staging/iio/accel/adis16201.ko
kernel/drivers/staging/iio/accel/adis16203.ko
kernel/drivers/staging/iio/accel/adis16204.ko
kernel/drivers/staging/iio/accel/adis16209.ko
kernel/drivers/staging/iio/accel/adis16220.ko
kernel/drivers/staging/iio/accel/adis16240.ko
kernel/drivers/staging/iio/accel/kxsd9.ko
kernel/drivers/staging/iio/accel/lis3l02dq.ko
kernel/drivers/staging/iio/accel/sca3000.ko
kernel/drivers/staging/iio/adc/ad7606.ko
kernel/drivers/staging/iio/adc/ad799x.ko
kernel/drivers/staging/iio/adc/ad7291.ko
kernel/drivers/staging/iio/adc/ad7780.ko
kernel/drivers/staging/iio/adc/ad7816.ko
kernel/drivers/staging/iio/adc/ad7192.ko
kernel/drivers/staging/iio/adc/adt7410.ko
kernel/drivers/staging/iio/adc/ad7280a.ko
kernel/drivers/staging/iio/addac/adt7316.ko
kernel/drivers/staging/iio/addac/adt7316-spi.ko
kernel/drivers/staging/iio/addac/adt7316-i2c.ko
kernel/drivers/staging/iio/cdc/ad7150.ko
kernel/drivers/staging/iio/cdc/ad7152.ko
kernel/drivers/staging/iio/cdc/ad7746.ko
kernel/drivers/staging/iio/frequency/ad5930.ko
kernel/drivers/staging/iio/frequency/ad9832.ko
kernel/drivers/staging/iio/frequency/ad9834.ko
kernel/drivers/staging/iio/frequency/ad9850.ko
kernel/drivers/staging/iio/frequency/ad9852.ko
kernel/drivers/staging/iio/frequency/ad9910.ko
kernel/drivers/staging/iio/frequency/ad9951.ko
kernel/drivers/staging/iio/gyro/adis16060.ko
kernel/drivers/staging/iio/gyro/adis16080.ko
kernel/drivers/staging/iio/gyro/adis16130.ko
kernel/drivers/staging/iio/gyro/adis16260.ko
kernel/drivers/staging/iio/gyro/adxrs450.ko
kernel/drivers/staging/iio/impedance-analyzer/ad5933.ko
kernel/drivers/staging/iio/imu/adis16400.ko
kernel/drivers/staging/iio/light/tsl2563.ko
kernel/drivers/staging/iio/light/isl29018.ko
kernel/drivers/staging/iio/light/isl29028.ko
kernel/drivers/staging/iio/light/tsl2583.ko
kernel/drivers/staging/iio/light/tsl2x7x_core.ko
kernel/drivers/staging/iio/magnetometer/ak8975.ko
kernel/drivers/staging/iio/magnetometer/hmc5843.ko
kernel/drivers/staging/iio/meter/ade7753.ko
kernel/drivers/staging/iio/meter/ade7754.ko
kernel/drivers/staging/iio/meter/ade7758.ko
kernel/drivers/staging/iio/meter/ade7759.ko
kernel/drivers/staging/iio/meter/ade7854.ko
kernel/drivers/staging/iio/meter/ade7854-i2c.ko
kernel/drivers/staging/iio/meter/ade7854-spi.ko
kernel/drivers/staging/iio/resolver/ad2s90.ko
kernel/drivers/staging/iio/resolver/ad2s1200.ko
kernel/drivers/staging/iio/resolver/ad2s1210.ko
kernel/drivers/staging/iio/trigger/iio-trig-periodic-rtc.ko
kernel/drivers/staging/iio/trigger/iio-trig-gpio.ko
kernel/drivers/staging/iio/trigger/iio-trig-sysfs.ko
kernel/drivers/staging/iio/ring_sw.ko
kernel/drivers/staging/iio/iio_dummy.ko
kernel/drivers/staging/iio/iio_hwmon.ko
kernel/drivers/staging/zram/zram.ko
kernel/drivers/staging/wlags49_h2/wlags49_h2_cs.ko
kernel/drivers/staging/wlags49_h25/wlags49_h25_cs.ko
kernel/drivers/staging/sm7xxfb/sm7xxfb.ko
kernel/drivers/staging/crystalhd/crystalhd.ko
kernel/drivers/staging/cxt1e1/cxt1e1.ko
kernel/drivers/staging/xgifb/xgifb.ko
kernel/drivers/staging/quickstart/quickstart.ko
kernel/drivers/staging/sbe-2t3e3/sbe-2t3e3.ko
kernel/drivers/staging/keucr/keucr.ko
kernel/drivers/staging/bcm/bcm_wimax.ko
kernel/drivers/staging/ft1000/ft1000-usb/ft1000.ko
kernel/drivers/staging/ft1000/ft1000-pcmcia/ft1000_pcmcia.ko
kernel/drivers/staging/speakup/speakup_acntsa.ko
kernel/drivers/staging/speakup/speakup_acntpc.ko
kernel/drivers/staging/speakup/speakup_apollo.ko
kernel/drivers/staging/speakup/speakup_audptr.ko
kernel/drivers/staging/speakup/speakup_bns.ko
kernel/drivers/staging/speakup/speakup_dectlk.ko
kernel/drivers/staging/speakup/speakup_decext.ko
kernel/drivers/staging/speakup/speakup_decpc.ko
kernel/drivers/staging/speakup/speakup_dtlk.ko
kernel/drivers/staging/speakup/speakup_keypc.ko
kernel/drivers/staging/speakup/speakup_ltlk.ko
kernel/drivers/staging/speakup/speakup_soft.ko
kernel/drivers/staging/speakup/speakup_spkout.ko
kernel/drivers/staging/speakup/speakup_txprt.ko
kernel/drivers/staging/speakup/speakup_dummy.ko
kernel/drivers/staging/speakup/speakup.ko
kernel/drivers/staging/cptm1217/clearpad_tm1217.ko
kernel/drivers/staging/ste_rmi4/synaptics_i2c_rmi4.ko
kernel/drivers/staging/ozwpan/ozwpan.ko
kernel/drivers/staging/gdm72xx/gdmwm.ko
kernel/drivers/staging/csr/csr_wifi.ko
kernel/drivers/staging/csr/csr_helper.ko
kernel/drivers/staging/ced1401/cedusb.ko
kernel/drivers/staging/dgrp/dgrp.ko
kernel/drivers/staging/sb105x/sb105x.ko
kernel/drivers/staging/fwserial/firewire-serial.ko
kernel/drivers/platform/x86/asus-laptop.ko
kernel/drivers/platform/x86/asus-wmi.ko
kernel/drivers/platform/x86/asus-nb-wmi.ko
kernel/drivers/platform/x86/eeepc-laptop.ko
kernel/drivers/platform/x86/eeepc-wmi.ko
kernel/drivers/platform/x86/msi-laptop.ko
kernel/drivers/platform/x86/classmate-laptop.ko
kernel/drivers/platform/x86/compal-laptop.ko
kernel/drivers/platform/x86/dell-laptop.ko
kernel/drivers/platform/x86/dell-wmi.ko
kernel/drivers/platform/x86/dell-wmi-aio.ko
kernel/drivers/platform/x86/acer-wmi.ko
kernel/drivers/platform/x86/acerhdf.ko
kernel/drivers/platform/x86/hp_accel.ko
kernel/drivers/platform/x86/hp-wmi.ko
kernel/drivers/platform/x86/amilo-rfkill.ko
kernel/drivers/platform/x86/sony-laptop.ko
kernel/drivers/platform/x86/ideapad-laptop.ko
kernel/drivers/platform/x86/thinkpad_acpi.ko
kernel/drivers/platform/x86/hdaps.ko
kernel/drivers/platform/x86/fujitsu-laptop.ko
kernel/drivers/platform/x86/fujitsu-tablet.ko
kernel/drivers/platform/x86/panasonic-laptop.ko
kernel/drivers/platform/x86/intel_menlow.ko
kernel/drivers/platform/x86/wmi.ko
kernel/drivers/platform/x86/msi-wmi.ko
kernel/drivers/platform/x86/topstar-laptop.ko
kernel/drivers/platform/x86/toshiba_acpi.ko
kernel/drivers/platform/x86/toshiba_bluetooth.ko
kernel/drivers/platform/x86/intel_ips.ko
kernel/drivers/platform/x86/xo15-ebook.ko
kernel/drivers/platform/x86/ibm_rtl.ko
kernel/drivers/platform/x86/samsung-laptop.ko
kernel/drivers/platform/x86/mxm-wmi.ko
kernel/drivers/platform/x86/intel_oaktrail.ko
kernel/drivers/platform/x86/samsung-q10.ko
kernel/drivers/platform/x86/apple-gmux.ko
kernel/drivers/iommu/amd_iommu_v2.ko
kernel/drivers/extcon/extcon-gpio.ko
kernel/drivers/extcon/extcon-adc-jack.ko
kernel/drivers/extcon/extcon-max77693.ko
kernel/drivers/extcon/extcon-max8997.ko
kernel/drivers/extcon/extcon-arizona.ko
kernel/drivers/char/ipmi/ipmi_msghandler.ko
kernel/drivers/char/ipmi/ipmi_devintf.ko
kernel/drivers/char/ipmi/ipmi_si.ko
kernel/drivers/char/ipmi/ipmi_watchdog.ko
kernel/drivers/char/ipmi/ipmi_poweroff.ko
kernel/drivers/video/intelfb/intelfb.ko
kernel/drivers/parport/parport.ko
kernel/drivers/parport/parport_pc.ko
kernel/drivers/parport/parport_serial.ko
kernel/drivers/parport/parport_cs.ko
kernel/drivers/parport/parport_ax88796.ko
kernel/drivers/target/target_core_mod.ko
kernel/drivers/target/target_core_iblock.ko
kernel/drivers/target/target_core_file.ko
kernel/drivers/target/target_core_pscsi.ko
kernel/drivers/target/loopback/tcm_loop.ko
kernel/drivers/target/tcm_fc/tcm_fc.ko
kernel/drivers/target/iscsi/iscsi_target_mod.ko
kernel/drivers/target/sbp/sbp_target.ko
kernel/drivers/mtd/chips/chipreg.ko
kernel/drivers/mtd/chips/cfi_probe.ko
kernel/drivers/mtd/chips/cfi_util.ko
kernel/drivers/mtd/chips/cfi_cmdset_0020.ko
kernel/drivers/mtd/chips/cfi_cmdset_0002.ko
kernel/drivers/mtd/chips/cfi_cmdset_0001.ko
kernel/drivers/mtd/chips/gen_probe.ko
kernel/drivers/mtd/chips/jedec_probe.ko
kernel/drivers/mtd/chips/map_ram.ko
kernel/drivers/mtd/chips/map_rom.ko
kernel/drivers/mtd/chips/map_absent.ko
kernel/drivers/mtd/lpddr/qinfo_probe.ko
kernel/drivers/mtd/lpddr/lpddr_cmds.ko
kernel/drivers/mtd/maps/map_funcs.ko
kernel/drivers/mtd/maps/l440gx.ko
kernel/drivers/mtd/maps/amd76xrom.ko
kernel/drivers/mtd/maps/esb2rom.ko
kernel/drivers/mtd/maps/ichxrom.ko
kernel/drivers/mtd/maps/ck804xrom.ko
kernel/drivers/mtd/maps/physmap.ko
kernel/drivers/mtd/maps/pcmciamtd.ko
kernel/drivers/mtd/maps/sbc_gxx.ko
kernel/drivers/mtd/maps/sc520cdp.ko
kernel/drivers/mtd/maps/netsc520.ko
kernel/drivers/mtd/maps/ts5500_flash.ko
kernel/drivers/mtd/maps/pci.ko
kernel/drivers/mtd/maps/nettel.ko
kernel/drivers/mtd/maps/scb2_flash.ko
kernel/drivers/mtd/maps/plat-ram.ko
kernel/drivers/mtd/maps/intel_vr_nor.ko
kernel/drivers/mtd/maps/gpio-addr-flash.ko
kernel/drivers/mtd/maps/latch-addr-flash.ko
kernel/drivers/mtd/devices/doc2001plus.ko
kernel/drivers/mtd/devices/docg3.ko
kernel/drivers/mtd/devices/docprobe.ko
kernel/drivers/mtd/devices/docecc.ko
kernel/drivers/mtd/devices/slram.ko
kernel/drivers/mtd/devices/phram.ko
kernel/drivers/mtd/devices/pmc551.ko
kernel/drivers/mtd/devices/mtdram.ko
kernel/drivers/mtd/devices/block2mtd.ko
kernel/drivers/mtd/devices/mtd_dataflash.ko
kernel/drivers/mtd/devices/m25p80.ko
kernel/drivers/mtd/devices/sst25l.ko
kernel/drivers/mtd/nand/nand.ko
kernel/drivers/mtd/nand/nand_ecc.ko
kernel/drivers/mtd/nand/nand_bch.ko
kernel/drivers/mtd/nand/nand_ids.ko
kernel/drivers/mtd/nand/sm_common.ko
kernel/drivers/mtd/nand/cafe_nand.ko
kernel/drivers/mtd/nand/denali.ko
kernel/drivers/mtd/nand/denali_pci.ko
kernel/drivers/mtd/nand/diskonchip.ko
kernel/drivers/mtd/nand/docg4.ko
kernel/drivers/mtd/nand/nandsim.ko
kernel/drivers/mtd/nand/plat_nand.ko
kernel/drivers/mtd/nand/alauda.ko
kernel/drivers/mtd/nand/r852.ko
kernel/drivers/mtd/onenand/onenand.ko
kernel/drivers/mtd/onenand/generic.ko
kernel/drivers/mtd/mtd.ko
kernel/drivers/mtd/redboot.ko
kernel/drivers/mtd/ar7part.ko
kernel/drivers/mtd/mtdchar.ko
kernel/drivers/mtd/mtd_blkdevs.ko
kernel/drivers/mtd/mtdblock.ko
kernel/drivers/mtd/mtdblock_ro.ko
kernel/drivers/mtd/ftl.ko
kernel/drivers/mtd/nftl.ko
kernel/drivers/mtd/inftl.ko
kernel/drivers/mtd/rfd_ftl.ko
kernel/drivers/mtd/ssfdc.ko
kernel/drivers/mtd/sm_ftl.ko
kernel/drivers/mtd/mtdoops.ko
kernel/drivers/mtd/mtdswap.ko
kernel/drivers/mtd/ubi/ubi.ko
kernel/drivers/mtd/ubi/gluebi.ko
kernel/drivers/atm/zatm.ko
kernel/drivers/atm/uPD98402.ko
kernel/drivers/atm/nicstar.ko
kernel/drivers/atm/ambassador.ko
kernel/drivers/atm/horizon.ko
kernel/drivers/atm/iphase.ko
kernel/drivers/atm/suni.ko
kernel/drivers/atm/fore_200e.ko
kernel/drivers/atm/eni.ko
kernel/drivers/atm/idt77252.ko
kernel/drivers/atm/solos-pci.ko
kernel/drivers/atm/adummy.ko
kernel/drivers/atm/atmtcp.ko
kernel/drivers/atm/firestream.ko
kernel/drivers/atm/lanai.ko
kernel/drivers/atm/he.ko
kernel/drivers/uio/uio.ko
kernel/drivers/uio/uio_cif.ko
kernel/drivers/uio/uio_pdrv.ko
kernel/drivers/uio/uio_pdrv_genirq.ko
kernel/drivers/uio/uio_dmem_genirq.ko
kernel/drivers/uio/uio_aec.ko
kernel/drivers/uio/uio_sercos3.ko
kernel/drivers/uio/uio_pci_generic.ko
kernel/drivers/uio/uio_netx.ko
kernel/drivers/vfio/vfio.ko
kernel/drivers/vfio/vfio_iommu_type1.ko
kernel/drivers/vfio/pci/vfio-pci.ko
kernel/drivers/pcmcia/pcmcia_core.ko
kernel/drivers/pcmcia/pcmcia.ko
kernel/drivers/pcmcia/pcmcia_rsrc.ko
kernel/drivers/pcmcia/yenta_socket.ko
kernel/drivers/pcmcia/pd6729.ko
kernel/drivers/pcmcia/i82092.ko
kernel/drivers/block/aoe/aoe.ko
kernel/drivers/block/paride/paride.ko
kernel/drivers/block/paride/aten.ko
kernel/drivers/block/paride/bpck.ko
kernel/drivers/block/paride/comm.ko
kernel/drivers/block/paride/dstr.ko
kernel/drivers/block/paride/kbic.ko
kernel/drivers/block/paride/epat.ko
kernel/drivers/block/paride/epia.ko
kernel/drivers/block/paride/frpw.ko
kernel/drivers/block/paride/friq.ko
kernel/drivers/block/paride/fit2.ko
kernel/drivers/block/paride/fit3.ko
kernel/drivers/block/paride/on20.ko
kernel/drivers/block/paride/on26.ko
kernel/drivers/block/paride/ktti.ko
kernel/drivers/block/paride/pd.ko
kernel/drivers/block/paride/pcd.ko
kernel/drivers/block/paride/pf.ko
kernel/drivers/block/paride/pt.ko
kernel/drivers/block/paride/pg.ko
kernel/drivers/uwb/uwb.ko
kernel/drivers/uwb/umc.ko
kernel/drivers/uwb/whci.ko
kernel/drivers/uwb/whc-rc.ko
kernel/drivers/uwb/hwa-rc.ko
kernel/drivers/uwb/i1480/dfu/i1480-dfu-usb.ko
kernel/drivers/uwb/i1480/i1480-est.ko
kernel/drivers/input/gameport/gameport.ko
kernel/drivers/input/gameport/emu10k1-gp.ko
kernel/drivers/input/gameport/fm801-gp.ko
kernel/drivers/input/gameport/lightning.ko
kernel/drivers/input/gameport/ns558.ko
kernel/drivers/pps/clients/pps-ldisc.ko
kernel/drivers/pps/clients/pps_parport.ko
kernel/drivers/pps/clients/pps-gpio.ko
kernel/drivers/pps/pps_core.ko
kernel/drivers/ptp/ptp.ko
kernel/drivers/ptp/ptp_pch.ko
kernel/drivers/w1/masters/matrox_w1.ko
kernel/drivers/w1/masters/ds2490.ko
kernel/drivers/w1/masters/ds2482.ko
kernel/drivers/w1/masters/ds1wm.ko
kernel/drivers/w1/masters/w1-gpio.ko
kernel/drivers/w1/slaves/w1_therm.ko
kernel/drivers/w1/slaves/w1_smem.ko
kernel/drivers/w1/slaves/w1_ds2408.ko
kernel/drivers/w1/slaves/w1_ds2423.ko
kernel/drivers/w1/slaves/w1_ds2431.ko
kernel/drivers/w1/slaves/w1_ds2433.ko
kernel/drivers/w1/slaves/w1_ds2760.ko
kernel/drivers/w1/slaves/w1_ds2780.ko
kernel/drivers/w1/slaves/w1_ds2781.ko
kernel/drivers/w1/slaves/w1_bq27000.ko
kernel/drivers/w1/slaves/w1_ds28e04.ko
kernel/drivers/w1/wire.ko
kernel/drivers/bluetooth/hci_vhci.ko
kernel/drivers/bluetooth/hci_uart.ko
kernel/drivers/bluetooth/bcm203x.ko
kernel/drivers/bluetooth/bpa10x.ko
kernel/drivers/bluetooth/bfusb.ko
kernel/drivers/bluetooth/dtl1_cs.ko
kernel/drivers/bluetooth/bt3c_cs.ko
kernel/drivers/bluetooth/bluecard_cs.ko
kernel/drivers/bluetooth/btuart_cs.ko
kernel/drivers/bluetooth/btusb.ko
kernel/drivers/bluetooth/btsdio.ko
kernel/drivers/bluetooth/ath3k.ko
kernel/drivers/bluetooth/btmrvl.ko
kernel/drivers/bluetooth/btmrvl_sdio.ko
kernel/drivers/bluetooth/btwilink.ko
kernel/drivers/memstick/core/memstick.ko
kernel/drivers/memstick/core/mspro_block.ko
kernel/drivers/memstick/host/tifm_ms.ko
kernel/drivers/memstick/host/jmb38x_ms.ko
kernel/drivers/memstick/host/r592.ko
kernel/drivers/memstick/host/rtsx_pci_ms.ko
kernel/drivers/infiniband/core/ib_core.ko
kernel/drivers/infiniband/core/ib_mad.ko
kernel/drivers/infiniband/core/ib_sa.ko
kernel/drivers/infiniband/core/ib_cm.ko
kernel/drivers/infiniband/core/iw_cm.ko
kernel/drivers/infiniband/core/ib_addr.ko
kernel/drivers/infiniband/core/rdma_cm.ko
kernel/drivers/infiniband/core/ib_umad.ko
kernel/drivers/infiniband/core/ib_uverbs.ko
kernel/drivers/infiniband/core/ib_ucm.ko
kernel/drivers/infiniband/core/rdma_ucm.ko
kernel/drivers/infiniband/hw/mthca/ib_mthca.ko
kernel/drivers/infiniband/hw/ipath/ib_ipath.ko
kernel/drivers/infiniband/hw/qib/ib_qib.ko
kernel/drivers/infiniband/hw/amso1100/iw_c2.ko
kernel/drivers/infiniband/hw/cxgb3/iw_cxgb3.ko
kernel/drivers/infiniband/hw/cxgb4/iw_cxgb4.ko
kernel/drivers/infiniband/hw/mlx4/mlx4_ib.ko
kernel/drivers/infiniband/hw/nes/iw_nes.ko
kernel/drivers/infiniband/hw/ocrdma/ocrdma.ko
kernel/drivers/infiniband/ulp/ipoib/ib_ipoib.ko
kernel/drivers/infiniband/ulp/srp/ib_srp.ko
kernel/drivers/infiniband/ulp/srpt/ib_srpt.ko
kernel/drivers/infiniband/ulp/iser/ib_iser.ko
kernel/drivers/dca/dca.ko
kernel/drivers/hid/hid.ko
kernel/drivers/hid/uhid.ko
kernel/drivers/hid/hid-generic.ko
kernel/drivers/hid/hid-a4tech.ko
kernel/drivers/hid/hid-axff.ko
kernel/drivers/hid/hid-apple.ko
kernel/drivers/hid/hid-aureal.ko
kernel/drivers/hid/hid-belkin.ko
kernel/drivers/hid/hid-cherry.ko
kernel/drivers/hid/hid-chicony.ko
kernel/drivers/hid/hid-cypress.ko
kernel/drivers/hid/hid-dr.ko
kernel/drivers/hid/hid-emsff.ko
kernel/drivers/hid/hid-elecom.ko
kernel/drivers/hid/hid-ezkey.ko
kernel/drivers/hid/hid-gyration.ko
kernel/drivers/hid/hid-holtek-kbd.ko
kernel/drivers/hid/hid-holtekff.ko
kernel/drivers/hid/hid-hyperv.ko
kernel/drivers/hid/hid-icade.ko
kernel/drivers/hid/hid-kensington.ko
kernel/drivers/hid/hid-keytouch.ko
kernel/drivers/hid/hid-kye.ko
kernel/drivers/hid/hid-lcpower.ko
kernel/drivers/hid/hid-lenovo-tpkbd.ko
kernel/drivers/hid/hid-logitech.ko
kernel/drivers/hid/hid-logitech-dj.ko
kernel/drivers/hid/hid-magicmouse.ko
kernel/drivers/hid/hid-microsoft.ko
kernel/drivers/hid/hid-monterey.ko
kernel/drivers/hid/hid-multitouch.ko
kernel/drivers/hid/hid-ntrig.ko
kernel/drivers/hid/hid-ortek.ko
kernel/drivers/hid/hid-prodikeys.ko
kernel/drivers/hid/hid-pl.ko
kernel/drivers/hid/hid-petalynx.ko
kernel/drivers/hid/hid-picolcd.ko
kernel/drivers/hid/hid-primax.ko
kernel/drivers/hid/hid-ps3remote.ko
kernel/drivers/hid/hid-roccat.ko
kernel/drivers/hid/hid-roccat-common.ko
kernel/drivers/hid/hid-roccat-arvo.ko
kernel/drivers/hid/hid-roccat-isku.ko
kernel/drivers/hid/hid-roccat-kone.ko
kernel/drivers/hid/hid-roccat-koneplus.ko
kernel/drivers/hid/hid-roccat-kovaplus.ko
kernel/drivers/hid/hid-roccat-lua.ko
kernel/drivers/hid/hid-roccat-pyra.ko
kernel/drivers/hid/hid-roccat-savu.ko
kernel/drivers/hid/hid-saitek.ko
kernel/drivers/hid/hid-samsung.ko
kernel/drivers/hid/hid-sjoy.ko
kernel/drivers/hid/hid-sony.ko
kernel/drivers/hid/hid-speedlink.ko
kernel/drivers/hid/hid-sunplus.ko
kernel/drivers/hid/hid-gaff.ko
kernel/drivers/hid/hid-tmff.ko
kernel/drivers/hid/hid-tivo.ko
kernel/drivers/hid/hid-topseed.ko
kernel/drivers/hid/hid-twinhan.ko
kernel/drivers/hid/hid-uclogic.ko
kernel/drivers/hid/hid-zpff.ko
kernel/drivers/hid/hid-zydacron.ko
kernel/drivers/hid/hid-wacom.ko
kernel/drivers/hid/hid-waltop.ko
kernel/drivers/hid/hid-wiimote.ko
kernel/drivers/hid/hid-sensor-hub.ko
kernel/drivers/hid/usbhid/usbhid.ko
kernel/drivers/hid/usbhid/usbkbd.ko
kernel/drivers/hid/usbhid/usbmouse.ko
kernel/drivers/hid/i2c-hid/i2c-hid.ko
kernel/drivers/ssb/ssb.ko
kernel/drivers/bcma/bcma.ko
kernel/drivers/vhost/vhost_net.ko
kernel/drivers/vhost/tcm_vhost.ko
kernel/drivers/remoteproc/remoteproc.ko
kernel/drivers/remoteproc/ste_modem_rproc.ko
kernel/drivers/hv/hv_vmbus.ko
kernel/drivers/hv/hv_utils.ko
kernel/drivers/hv/hv_balloon.ko
kernel/drivers/iio/accel/hid-sensor-accel-3d.ko
kernel/drivers/iio/adc/ad_sigma_delta.ko
kernel/drivers/iio/adc/ad7266.ko
kernel/drivers/iio/adc/ad7298.ko
kernel/drivers/iio/adc/ad7476.ko
kernel/drivers/iio/adc/ad7791.ko
kernel/drivers/iio/adc/ad7793.ko
kernel/drivers/iio/adc/ad7887.ko
kernel/drivers/iio/adc/max1363.ko
kernel/drivers/iio/adc/ti-adc081c.ko
kernel/drivers/iio/adc/ti_am335x_adc.ko
kernel/drivers/iio/adc/viperboard_adc.ko
kernel/drivers/iio/amplifiers/ad8366.ko
kernel/drivers/iio/common/hid-sensors/hid-sensor-iio-common.ko
kernel/drivers/iio/common/hid-sensors/hid-sensor-trigger.ko
kernel/drivers/iio/dac/ad5360.ko
kernel/drivers/iio/dac/ad5380.ko
kernel/drivers/iio/dac/ad5421.ko
kernel/drivers/iio/dac/ad5624r_spi.ko
kernel/drivers/iio/dac/ad5064.ko
kernel/drivers/iio/dac/ad5504.ko
kernel/drivers/iio/dac/ad5446.ko
kernel/drivers/iio/dac/ad5449.ko
kernel/drivers/iio/dac/ad5755.ko
kernel/drivers/iio/dac/ad5764.ko
kernel/drivers/iio/dac/ad5791.ko
kernel/drivers/iio/dac/ad5686.ko
kernel/drivers/iio/dac/max517.ko
kernel/drivers/iio/dac/mcp4725.ko
kernel/drivers/iio/gyro/adis16136.ko
kernel/drivers/iio/gyro/hid-sensor-gyro-3d.ko
kernel/drivers/iio/frequency/ad9523.ko
kernel/drivers/iio/frequency/adf4350.ko
kernel/drivers/iio/imu/adis16480.ko
kernel/drivers/iio/imu/adis_lib.ko
kernel/drivers/iio/light/adjd_s311.ko
kernel/drivers/iio/light/lm3533-als.ko
kernel/drivers/iio/light/vcnl4000.ko
kernel/drivers/iio/light/hid-sensor-als.ko
kernel/drivers/iio/magnetometer/hid-sensor-magn-3d.ko
kernel/drivers/iio/industrialio.ko
kernel/drivers/iio/industrialio-triggered-buffer.ko
kernel/drivers/iio/kfifo_buf.ko
kernel/drivers/vme/bridges/vme_ca91cx42.ko
kernel/drivers/vme/bridges/vme_tsi148.ko
kernel/drivers/vme/boards/vme_vmivme7805.ko
kernel/drivers/vme/vme.ko
kernel/drivers/ipack/devices/ipoctal.ko
kernel/drivers/ipack/carriers/tpci200.ko
kernel/drivers/ipack/ipack.ko
kernel/sound/soundcore.ko
kernel/sound/core/snd.ko
kernel/sound/core/snd-hwdep.ko
kernel/sound/core/snd-timer.ko
kernel/sound/core/snd-hrtimer.ko
kernel/sound/core/snd-pcm.ko
kernel/sound/core/snd-page-alloc.ko
kernel/sound/core/snd-rawmidi.ko
kernel/sound/core/seq/snd-seq.ko
kernel/sound/core/seq/snd-seq-device.ko
kernel/sound/core/seq/snd-seq-dummy.ko
kernel/sound/core/seq/snd-seq-virmidi.ko
kernel/sound/core/seq/snd-seq-midi-event.ko
kernel/sound/core/seq/snd-seq-midi.ko
kernel/sound/core/seq/snd-seq-midi-emul.ko
kernel/sound/core/snd-compress.ko
kernel/sound/i2c/other/snd-ak4117.ko
kernel/sound/i2c/other/snd-ak4xxx-adda.ko
kernel/sound/i2c/other/snd-ak4114.ko
kernel/sound/i2c/other/snd-ak4113.ko
kernel/sound/i2c/other/snd-pt2258.ko
kernel/sound/i2c/other/snd-tea575x-tuner.ko
kernel/sound/i2c/snd-cs8427.ko
kernel/sound/i2c/snd-i2c.ko
kernel/sound/drivers/snd-dummy.ko
kernel/sound/drivers/snd-aloop.ko
kernel/sound/drivers/snd-virmidi.ko
kernel/sound/drivers/snd-serial-u16550.ko
kernel/sound/drivers/snd-mtpav.ko
kernel/sound/drivers/snd-mts64.ko
kernel/sound/drivers/snd-portman2x4.ko
kernel/sound/drivers/opl3/snd-opl3-lib.ko
kernel/sound/drivers/opl3/snd-opl3-synth.ko
kernel/sound/drivers/mpu401/snd-mpu401-uart.ko
kernel/sound/drivers/mpu401/snd-mpu401.ko
kernel/sound/drivers/vx/snd-vx-lib.ko
kernel/sound/drivers/pcsp/snd-pcsp.ko
kernel/sound/isa/sb/snd-sb-common.ko
kernel/sound/isa/sb/snd-sb16-dsp.ko
kernel/sound/pci/snd-ad1889.ko
kernel/sound/pci/snd-als300.ko
kernel/sound/pci/snd-als4000.ko
kernel/sound/pci/snd-atiixp.ko
kernel/sound/pci/snd-atiixp-modem.ko
kernel/sound/pci/snd-azt3328.ko
kernel/sound/pci/snd-bt87x.ko
kernel/sound/pci/snd-cmipci.ko
kernel/sound/pci/snd-cs4281.ko
kernel/sound/pci/snd-cs5530.ko
kernel/sound/pci/snd-ens1370.ko
kernel/sound/pci/snd-ens1371.ko
kernel/sound/pci/snd-es1938.ko
kernel/sound/pci/snd-es1968.ko
kernel/sound/pci/snd-fm801.ko
kernel/sound/pci/snd-intel8x0.ko
kernel/sound/pci/snd-intel8x0m.ko
kernel/sound/pci/snd-maestro3.ko
kernel/sound/pci/snd-rme32.ko
kernel/sound/pci/snd-rme96.ko
kernel/sound/pci/snd-sonicvibes.ko
kernel/sound/pci/snd-via82xx.ko
kernel/sound/pci/snd-via82xx-modem.ko
kernel/sound/pci/ac97/snd-ac97-codec.ko
kernel/sound/pci/ali5451/snd-ali5451.ko
kernel/sound/pci/asihpi/snd-asihpi.ko
kernel/sound/pci/au88x0/snd-au8810.ko
kernel/sound/pci/au88x0/snd-au8820.ko
kernel/sound/pci/au88x0/snd-au8830.ko
kernel/sound/pci/aw2/snd-aw2.ko
kernel/sound/pci/ctxfi/snd-ctxfi.ko
kernel/sound/pci/ca0106/snd-ca0106.ko
kernel/sound/pci/cs46xx/snd-cs46xx.ko
kernel/sound/pci/cs5535audio/snd-cs5535audio.ko
kernel/sound/pci/lola/snd-lola.ko
kernel/sound/pci/lx6464es/snd-lx6464es.ko
kernel/sound/pci/echoaudio/snd-darla20.ko
kernel/sound/pci/echoaudio/snd-gina20.ko
kernel/sound/pci/echoaudio/snd-layla20.ko
kernel/sound/pci/echoaudio/snd-darla24.ko
kernel/sound/pci/echoaudio/snd-gina24.ko
kernel/sound/pci/echoaudio/snd-layla24.ko
kernel/sound/pci/echoaudio/snd-mona.ko
kernel/sound/pci/echoaudio/snd-mia.ko
kernel/sound/pci/echoaudio/snd-echo3g.ko
kernel/sound/pci/echoaudio/snd-indigo.ko
kernel/sound/pci/echoaudio/snd-indigoio.ko
kernel/sound/pci/echoaudio/snd-indigodj.ko
kernel/sound/pci/echoaudio/snd-indigoiox.ko
kernel/sound/pci/echoaudio/snd-indigodjx.ko
kernel/sound/pci/emu10k1/snd-emu10k1.ko
kernel/sound/pci/emu10k1/snd-emu10k1-synth.ko
kernel/sound/pci/emu10k1/snd-emu10k1x.ko
kernel/sound/pci/hda/snd-hda-codec.ko
kernel/sound/pci/hda/snd-hda-codec-realtek.ko
kernel/sound/pci/hda/snd-hda-codec-cmedia.ko
kernel/sound/pci/hda/snd-hda-codec-analog.ko
kernel/sound/pci/hda/snd-hda-codec-idt.ko
kernel/sound/pci/hda/snd-hda-codec-si3054.ko
kernel/sound/pci/hda/snd-hda-codec-cirrus.ko
kernel/sound/pci/hda/snd-hda-codec-ca0110.ko
kernel/sound/pci/hda/snd-hda-codec-ca0132.ko
kernel/sound/pci/hda/snd-hda-codec-conexant.ko
kernel/sound/pci/hda/snd-hda-codec-via.ko
kernel/sound/pci/hda/snd-hda-codec-hdmi.ko
kernel/sound/pci/hda/snd-hda-intel.ko
kernel/sound/pci/ice1712/snd-ice1712.ko
kernel/sound/pci/ice1712/snd-ice17xx-ak4xxx.ko
kernel/sound/pci/ice1712/snd-ice1724.ko
kernel/sound/pci/korg1212/snd-korg1212.ko
kernel/sound/pci/mixart/snd-mixart.ko
kernel/sound/pci/nm256/snd-nm256.ko
kernel/sound/pci/oxygen/snd-oxygen-lib.ko
kernel/sound/pci/oxygen/snd-oxygen.ko
kernel/sound/pci/oxygen/snd-virtuoso.ko
kernel/sound/pci/pcxhr/snd-pcxhr.ko
kernel/sound/pci/riptide/snd-riptide.ko
kernel/sound/pci/rme9652/snd-rme9652.ko
kernel/sound/pci/rme9652/snd-hdsp.ko
kernel/sound/pci/rme9652/snd-hdspm.ko
kernel/sound/pci/trident/snd-trident.ko
kernel/sound/pci/ymfpci/snd-ymfpci.ko
kernel/sound/pci/vx222/snd-vx222.ko
kernel/sound/synth/snd-util-mem.ko
kernel/sound/synth/emux/snd-emux-synth.ko
kernel/sound/usb/snd-usb-audio.ko
kernel/sound/usb/snd-usbmidi-lib.ko
kernel/sound/usb/misc/snd-ua101.ko
kernel/sound/usb/usx2y/snd-usb-usx2y.ko
kernel/sound/usb/usx2y/snd-usb-us122l.ko
kernel/sound/usb/caiaq/snd-usb-caiaq.ko
kernel/sound/usb/6fire/snd-usb-6fire.ko
kernel/sound/firewire/snd-firewire-lib.ko
kernel/sound/firewire/snd-firewire-speakers.ko
kernel/sound/firewire/snd-isight.ko
kernel/sound/firewire/snd-scs1x.ko
kernel/sound/pcmcia/vx/snd-vxpocket.ko
kernel/sound/pcmcia/pdaudiocf/snd-pdaudiocf.ko
kernel/sound/soc/snd-soc-core.ko
kernel/sound/soc/codecs/snd-soc-88pm860x.ko
kernel/sound/soc/codecs/snd-soc-ab8500-codec.ko
kernel/sound/soc/codecs/snd-soc-ad1836.ko
kernel/sound/soc/codecs/snd-soc-ad193x.ko
kernel/sound/soc/codecs/snd-soc-ad73311.ko
kernel/sound/soc/codecs/snd-soc-adau1373.ko
kernel/sound/soc/codecs/snd-soc-adav80x.ko
kernel/sound/soc/codecs/snd-soc-ads117x.ko
kernel/sound/soc/codecs/snd-soc-ak4104.ko
kernel/sound/soc/codecs/snd-soc-ak4535.ko
kernel/sound/soc/codecs/snd-soc-ak4641.ko
kernel/sound/soc/codecs/snd-soc-ak4642.ko
kernel/sound/soc/codecs/snd-soc-ak4671.ko
kernel/sound/soc/codecs/snd-soc-alc5623.ko
kernel/sound/soc/codecs/snd-soc-alc5632.ko
kernel/sound/soc/codecs/snd-soc-arizona.ko
kernel/sound/soc/codecs/snd-soc-cs42l51.ko
kernel/sound/soc/codecs/snd-soc-cs42l52.ko
kernel/sound/soc/codecs/snd-soc-cs42l73.ko
kernel/sound/soc/codecs/snd-soc-cs4270.ko
kernel/sound/soc/codecs/snd-soc-cs4271.ko
kernel/sound/soc/codecs/snd-soc-cx20442.ko
kernel/sound/soc/codecs/snd-soc-da7210.ko
kernel/sound/soc/codecs/snd-soc-da732x.ko
kernel/sound/soc/codecs/snd-soc-da9055.ko
kernel/sound/soc/codecs/snd-soc-dfbmcs320.ko
kernel/sound/soc/codecs/snd-soc-isabelle.ko
kernel/sound/soc/codecs/snd-soc-jz4740-codec.ko
kernel/sound/soc/codecs/snd-soc-l3.ko
kernel/sound/soc/codecs/snd-soc-lm4857.ko
kernel/sound/soc/codecs/snd-soc-lm49453.ko
kernel/sound/soc/codecs/snd-soc-max9768.ko
kernel/sound/soc/codecs/snd-soc-max98088.ko
kernel/sound/soc/codecs/snd-soc-max98090.ko
kernel/sound/soc/codecs/snd-soc-max98095.ko
kernel/sound/soc/codecs/snd-soc-max9850.ko
kernel/sound/soc/codecs/snd-soc-mc13783.ko
kernel/sound/soc/codecs/snd-soc-ml26124.ko
kernel/sound/soc/codecs/snd-soc-pcm3008.ko
kernel/sound/soc/codecs/snd-soc-rt5631.ko
kernel/sound/soc/codecs/snd-soc-sgtl5000.ko
kernel/sound/soc/codecs/snd-soc-spdif-rx.ko
kernel/sound/soc/codecs/snd-soc-spdif-tx.ko
kernel/sound/soc/codecs/snd-soc-ssm2602.ko
kernel/sound/soc/codecs/snd-soc-sta32x.ko
kernel/sound/soc/codecs/snd-soc-sta529.ko
kernel/sound/soc/codecs/snd-soc-tlv320aic23.ko
kernel/sound/soc/codecs/snd-soc-tlv320aic26.ko
kernel/sound/soc/codecs/snd-soc-tlv320aic3x.ko
kernel/sound/soc/codecs/snd-soc-tlv320aic32x4.ko
kernel/sound/soc/codecs/snd-soc-tlv320dac33.ko
kernel/sound/soc/codecs/snd-soc-twl4030.ko
kernel/sound/soc/codecs/snd-soc-twl6040.ko
kernel/sound/soc/codecs/snd-soc-uda134x.ko
kernel/sound/soc/codecs/snd-soc-uda1380.ko
kernel/sound/soc/codecs/snd-soc-wl1273.ko
kernel/sound/soc/codecs/snd-soc-wm0010.ko
kernel/sound/soc/codecs/snd-soc-wm1250-ev1.ko
kernel/sound/soc/codecs/snd-soc-wm2000.ko
kernel/sound/soc/codecs/snd-soc-wm2200.ko
kernel/sound/soc/codecs/snd-soc-wm5100.ko
kernel/sound/soc/codecs/snd-soc-wm5102.ko
kernel/sound/soc/codecs/snd-soc-wm5110.ko
kernel/sound/soc/codecs/snd-soc-wm8350.ko
kernel/sound/soc/codecs/snd-soc-wm8400.ko
kernel/sound/soc/codecs/snd-soc-wm8510.ko
kernel/sound/soc/codecs/snd-soc-wm8523.ko
kernel/sound/soc/codecs/snd-soc-wm8580.ko
kernel/sound/soc/codecs/snd-soc-wm8711.ko
kernel/sound/soc/codecs/snd-soc-wm8727.ko
kernel/sound/soc/codecs/snd-soc-wm8728.ko
kernel/sound/soc/codecs/snd-soc-wm8731.ko
kernel/sound/soc/codecs/snd-soc-wm8737.ko
kernel/sound/soc/codecs/snd-soc-wm8741.ko
kernel/sound/soc/codecs/snd-soc-wm8750.ko
kernel/sound/soc/codecs/snd-soc-wm8753.ko
kernel/sound/soc/codecs/snd-soc-wm8770.ko
kernel/sound/soc/codecs/snd-soc-wm8776.ko
kernel/sound/soc/codecs/snd-soc-wm8782.ko
kernel/sound/soc/codecs/snd-soc-wm8804.ko
kernel/sound/soc/codecs/snd-soc-wm8900.ko
kernel/sound/soc/codecs/snd-soc-wm8903.ko
kernel/sound/soc/codecs/snd-soc-wm8904.ko
kernel/sound/soc/codecs/snd-soc-wm8996.ko
kernel/sound/soc/codecs/snd-soc-wm8940.ko
kernel/sound/soc/codecs/snd-soc-wm8955.ko
kernel/sound/soc/codecs/snd-soc-wm8960.ko
kernel/sound/soc/codecs/snd-soc-wm8961.ko
kernel/sound/soc/codecs/snd-soc-wm8962.ko
kernel/sound/soc/codecs/snd-soc-wm8971.ko
kernel/sound/soc/codecs/snd-soc-wm8974.ko
kernel/sound/soc/codecs/snd-soc-wm8978.ko
kernel/sound/soc/codecs/snd-soc-wm8983.ko
kernel/sound/soc/codecs/snd-soc-wm8985.ko
kernel/sound/soc/codecs/snd-soc-wm8988.ko
kernel/sound/soc/codecs/snd-soc-wm8990.ko
kernel/sound/soc/codecs/snd-soc-wm8991.ko
kernel/sound/soc/codecs/snd-soc-wm8993.ko
kernel/sound/soc/codecs/snd-soc-wm8994.ko
kernel/sound/soc/codecs/snd-soc-wm8995.ko
kernel/sound/soc/codecs/snd-soc-wm9081.ko
kernel/sound/soc/codecs/snd-soc-wm9090.ko
kernel/sound/soc/codecs/snd-soc-wm-adsp.ko
kernel/sound/soc/codecs/snd-soc-wm-hubs.ko
kernel/sound/soc/codecs/snd-soc-max9877.ko
kernel/sound/soc/codecs/snd-soc-tpa6130a2.ko
kernel/sound/soc/generic/snd-soc-simple-card.ko
kernel/sound/ac97_bus.ko
kernel/ubuntu/dm-raid4-5/dm-raid45.ko
kernel/ubuntu/aufs/aufs.ko
kernel/ubuntu/alx/alx.ko
kernel/arch/x86/oprofile/oprofile.ko
kernel/net/core/pktgen.ko
kernel/net/core/netprio_cgroup.ko
kernel/net/802/p8022.ko
kernel/net/802/psnap.ko
kernel/net/802/p8023.ko
kernel/net/802/stp.ko
kernel/net/802/garp.ko
kernel/net/sched/act_police.ko
kernel/net/sched/act_gact.ko
kernel/net/sched/act_mirred.ko
kernel/net/sched/act_ipt.ko
kernel/net/sched/act_nat.ko
kernel/net/sched/act_pedit.ko
kernel/net/sched/act_simple.ko
kernel/net/sched/act_skbedit.ko
kernel/net/sched/act_csum.ko
kernel/net/sched/sch_cbq.ko
kernel/net/sched/sch_htb.ko
kernel/net/sched/sch_hfsc.ko
kernel/net/sched/sch_red.ko
kernel/net/sched/sch_gred.ko
kernel/net/sched/sch_ingress.ko
kernel/net/sched/sch_dsmark.ko
kernel/net/sched/sch_sfb.ko
kernel/net/sched/sch_sfq.ko
kernel/net/sched/sch_tbf.ko
kernel/net/sched/sch_teql.ko
kernel/net/sched/sch_prio.ko
kernel/net/sched/sch_multiq.ko
kernel/net/sched/sch_atm.ko
kernel/net/sched/sch_netem.ko
kernel/net/sched/sch_drr.ko
kernel/net/sched/sch_plug.ko
kernel/net/sched/sch_mqprio.ko
kernel/net/sched/sch_choke.ko
kernel/net/sched/sch_qfq.ko
kernel/net/sched/sch_codel.ko
kernel/net/sched/sch_fq_codel.ko
kernel/net/sched/cls_u32.ko
kernel/net/sched/cls_route.ko
kernel/net/sched/cls_fw.ko
kernel/net/sched/cls_rsvp.ko
kernel/net/sched/cls_tcindex.ko
kernel/net/sched/cls_rsvp6.ko
kernel/net/sched/cls_basic.ko
kernel/net/sched/cls_flow.ko
kernel/net/sched/cls_cgroup.ko
kernel/net/sched/em_cmp.ko
kernel/net/sched/em_nbyte.ko
kernel/net/sched/em_u32.ko
kernel/net/sched/em_meta.ko
kernel/net/sched/em_text.ko
kernel/net/sched/em_canid.ko
kernel/net/sched/em_ipset.ko
kernel/net/netfilter/nfnetlink.ko
kernel/net/netfilter/nfnetlink_acct.ko
kernel/net/netfilter/nfnetlink_queue.ko
kernel/net/netfilter/nfnetlink_log.ko
kernel/net/netfilter/nf_conntrack.ko
kernel/net/netfilter/nf_conntrack_proto_dccp.ko
kernel/net/netfilter/nf_conntrack_proto_gre.ko
kernel/net/netfilter/nf_conntrack_proto_sctp.ko
kernel/net/netfilter/nf_conntrack_proto_udplite.ko
kernel/net/netfilter/nf_conntrack_netlink.ko
kernel/net/netfilter/nfnetlink_cttimeout.ko
kernel/net/netfilter/nfnetlink_cthelper.ko
kernel/net/netfilter/nf_conntrack_amanda.ko
kernel/net/netfilter/nf_conntrack_ftp.ko
kernel/net/netfilter/nf_conntrack_h323.ko
kernel/net/netfilter/nf_conntrack_irc.ko
kernel/net/netfilter/nf_conntrack_broadcast.ko
kernel/net/netfilter/nf_conntrack_netbios_ns.ko
kernel/net/netfilter/nf_conntrack_snmp.ko
kernel/net/netfilter/nf_conntrack_pptp.ko
kernel/net/netfilter/nf_conntrack_sane.ko
kernel/net/netfilter/nf_conntrack_sip.ko
kernel/net/netfilter/nf_conntrack_tftp.ko
kernel/net/netfilter/nf_nat.ko
kernel/net/netfilter/nf_nat_proto_dccp.ko
kernel/net/netfilter/nf_nat_proto_udplite.ko
kernel/net/netfilter/nf_nat_proto_sctp.ko
kernel/net/netfilter/nf_nat_amanda.ko
kernel/net/netfilter/nf_nat_ftp.ko
kernel/net/netfilter/nf_nat_irc.ko
kernel/net/netfilter/nf_nat_sip.ko
kernel/net/netfilter/nf_nat_tftp.ko
kernel/net/netfilter/nf_tproxy_core.ko
kernel/net/netfilter/x_tables.ko
kernel/net/netfilter/xt_tcpudp.ko
kernel/net/netfilter/xt_mark.ko
kernel/net/netfilter/xt_connmark.ko
kernel/net/netfilter/xt_set.ko
kernel/net/netfilter/xt_nat.ko
kernel/net/netfilter/xt_AUDIT.ko
kernel/net/netfilter/xt_CHECKSUM.ko
kernel/net/netfilter/xt_CLASSIFY.ko
kernel/net/netfilter/xt_CONNSECMARK.ko
kernel/net/netfilter/xt_CT.ko
kernel/net/netfilter/xt_DSCP.ko
kernel/net/netfilter/xt_HL.ko
kernel/net/netfilter/xt_HMARK.ko
kernel/net/netfilter/xt_LED.ko
kernel/net/netfilter/xt_LOG.ko
kernel/net/netfilter/xt_NETMAP.ko
kernel/net/netfilter/xt_NFLOG.ko
kernel/net/netfilter/xt_NFQUEUE.ko
kernel/net/netfilter/xt_RATEEST.ko
kernel/net/netfilter/xt_REDIRECT.ko
kernel/net/netfilter/xt_SECMARK.ko
kernel/net/netfilter/xt_TPROXY.ko
kernel/net/netfilter/xt_TCPMSS.ko
kernel/net/netfilter/xt_TCPOPTSTRIP.ko
kernel/net/netfilter/xt_TEE.ko
kernel/net/netfilter/xt_TRACE.ko
kernel/net/netfilter/xt_IDLETIMER.ko
kernel/net/netfilter/xt_addrtype.ko
kernel/net/netfilter/xt_cluster.ko
kernel/net/netfilter/xt_comment.ko
kernel/net/netfilter/xt_connbytes.ko
kernel/net/netfilter/xt_connlimit.ko
kernel/net/netfilter/xt_conntrack.ko
kernel/net/netfilter/xt_cpu.ko
kernel/net/netfilter/xt_dccp.ko
kernel/net/netfilter/xt_devgroup.ko
kernel/net/netfilter/xt_dscp.ko
kernel/net/netfilter/xt_ecn.ko
kernel/net/netfilter/xt_esp.ko
kernel/net/netfilter/xt_hashlimit.ko
kernel/net/netfilter/xt_helper.ko
kernel/net/netfilter/xt_hl.ko
kernel/net/netfilter/xt_iprange.ko
kernel/net/netfilter/xt_ipvs.ko
kernel/net/netfilter/xt_length.ko
kernel/net/netfilter/xt_limit.ko
kernel/net/netfilter/xt_mac.ko
kernel/net/netfilter/xt_multiport.ko
kernel/net/netfilter/xt_nfacct.ko
kernel/net/netfilter/xt_osf.ko
kernel/net/netfilter/xt_owner.ko
kernel/net/netfilter/xt_physdev.ko
kernel/net/netfilter/xt_pkttype.ko
kernel/net/netfilter/xt_policy.ko
kernel/net/netfilter/xt_quota.ko
kernel/net/netfilter/xt_rateest.ko
kernel/net/netfilter/xt_realm.ko
kernel/net/netfilter/xt_recent.ko
kernel/net/netfilter/xt_sctp.ko
kernel/net/netfilter/xt_socket.ko
kernel/net/netfilter/xt_state.ko
kernel/net/netfilter/xt_statistic.ko
kernel/net/netfilter/xt_string.ko
kernel/net/netfilter/xt_tcpmss.ko
kernel/net/netfilter/xt_time.ko
kernel/net/netfilter/xt_u32.ko
kernel/net/netfilter/ipset/ip_set.ko
kernel/net/netfilter/ipset/ip_set_bitmap_ip.ko
kernel/net/netfilter/ipset/ip_set_bitmap_ipmac.ko
kernel/net/netfilter/ipset/ip_set_bitmap_port.ko
kernel/net/netfilter/ipset/ip_set_hash_ip.ko
kernel/net/netfilter/ipset/ip_set_hash_ipport.ko
kernel/net/netfilter/ipset/ip_set_hash_ipportip.ko
kernel/net/netfilter/ipset/ip_set_hash_ipportnet.ko
kernel/net/netfilter/ipset/ip_set_hash_net.ko
kernel/net/netfilter/ipset/ip_set_hash_netport.ko
kernel/net/netfilter/ipset/ip_set_hash_netiface.ko
kernel/net/netfilter/ipset/ip_set_list_set.ko
kernel/net/netfilter/ipvs/ip_vs.ko
kernel/net/netfilter/ipvs/ip_vs_rr.ko
kernel/net/netfilter/ipvs/ip_vs_wrr.ko
kernel/net/netfilter/ipvs/ip_vs_lc.ko
kernel/net/netfilter/ipvs/ip_vs_wlc.ko
kernel/net/netfilter/ipvs/ip_vs_lblc.ko
kernel/net/netfilter/ipvs/ip_vs_lblcr.ko
kernel/net/netfilter/ipvs/ip_vs_dh.ko
kernel/net/netfilter/ipvs/ip_vs_sh.ko
kernel/net/netfilter/ipvs/ip_vs_sed.ko
kernel/net/netfilter/ipvs/ip_vs_nq.ko
kernel/net/netfilter/ipvs/ip_vs_ftp.ko
kernel/net/netfilter/ipvs/ip_vs_pe_sip.ko
kernel/net/ipv4/netfilter/nf_conntrack_ipv4.ko
kernel/net/ipv4/netfilter/nf_nat_ipv4.ko
kernel/net/ipv4/netfilter/nf_defrag_ipv4.ko
kernel/net/ipv4/netfilter/nf_nat_h323.ko
kernel/net/ipv4/netfilter/nf_nat_pptp.ko
kernel/net/ipv4/netfilter/nf_nat_snmp_basic.ko
kernel/net/ipv4/netfilter/nf_nat_proto_gre.ko
kernel/net/ipv4/netfilter/ip_tables.ko
kernel/net/ipv4/netfilter/iptable_filter.ko
kernel/net/ipv4/netfilter/iptable_mangle.ko
kernel/net/ipv4/netfilter/iptable_nat.ko
kernel/net/ipv4/netfilter/iptable_raw.ko
kernel/net/ipv4/netfilter/iptable_security.ko
kernel/net/ipv4/netfilter/ipt_ah.ko
kernel/net/ipv4/netfilter/ipt_rpfilter.ko
kernel/net/ipv4/netfilter/ipt_CLUSTERIP.ko
kernel/net/ipv4/netfilter/ipt_ECN.ko
kernel/net/ipv4/netfilter/ipt_MASQUERADE.ko
kernel/net/ipv4/netfilter/ipt_REJECT.ko
kernel/net/ipv4/netfilter/ipt_ULOG.ko
kernel/net/ipv4/netfilter/arp_tables.ko
kernel/net/ipv4/netfilter/arpt_mangle.ko
kernel/net/ipv4/netfilter/arptable_filter.ko
kernel/net/ipv4/ipip.ko
kernel/net/ipv4/gre.ko
kernel/net/ipv4/ip_gre.ko
kernel/net/ipv4/ip_vti.ko
kernel/net/ipv4/ah4.ko
kernel/net/ipv4/esp4.ko
kernel/net/ipv4/ipcomp.ko
kernel/net/ipv4/xfrm4_tunnel.ko
kernel/net/ipv4/xfrm4_mode_beet.ko
kernel/net/ipv4/tunnel4.ko
kernel/net/ipv4/xfrm4_mode_transport.ko
kernel/net/ipv4/xfrm4_mode_tunnel.ko
kernel/net/ipv4/inet_diag.ko
kernel/net/ipv4/tcp_diag.ko
kernel/net/ipv4/udp_diag.ko
kernel/net/ipv4/tcp_probe.ko
kernel/net/ipv4/tcp_bic.ko
kernel/net/ipv4/tcp_westwood.ko
kernel/net/ipv4/tcp_highspeed.ko
kernel/net/ipv4/tcp_hybla.ko
kernel/net/ipv4/tcp_htcp.ko
kernel/net/ipv4/tcp_vegas.ko
kernel/net/ipv4/tcp_veno.ko
kernel/net/ipv4/tcp_scalable.ko
kernel/net/ipv4/tcp_lp.ko
kernel/net/ipv4/tcp_yeah.ko
kernel/net/ipv4/tcp_illinois.ko
kernel/net/xfrm/xfrm_algo.ko
kernel/net/xfrm/xfrm_user.ko
kernel/net/xfrm/xfrm_ipcomp.ko
kernel/net/unix/unix_diag.ko
kernel/net/ipv6/netfilter/ip6_tables.ko
kernel/net/ipv6/netfilter/ip6table_filter.ko
kernel/net/ipv6/netfilter/ip6table_mangle.ko
kernel/net/ipv6/netfilter/ip6table_raw.ko
kernel/net/ipv6/netfilter/ip6table_security.ko
kernel/net/ipv6/netfilter/ip6table_nat.ko
kernel/net/ipv6/netfilter/nf_conntrack_ipv6.ko
kernel/net/ipv6/netfilter/nf_defrag_ipv6.ko
kernel/net/ipv6/netfilter/nf_nat_ipv6.ko
kernel/net/ipv6/netfilter/ip6t_ah.ko
kernel/net/ipv6/netfilter/ip6t_eui64.ko
kernel/net/ipv6/netfilter/ip6t_frag.ko
kernel/net/ipv6/netfilter/ip6t_ipv6header.ko
kernel/net/ipv6/netfilter/ip6t_mh.ko
kernel/net/ipv6/netfilter/ip6t_hbh.ko
kernel/net/ipv6/netfilter/ip6t_rpfilter.ko
kernel/net/ipv6/netfilter/ip6t_rt.ko
kernel/net/ipv6/netfilter/ip6t_MASQUERADE.ko
kernel/net/ipv6/netfilter/ip6t_NPT.ko
kernel/net/ipv6/netfilter/ip6t_REJECT.ko
kernel/net/ipv6/ah6.ko
kernel/net/ipv6/esp6.ko
kernel/net/ipv6/ipcomp6.ko
kernel/net/ipv6/xfrm6_tunnel.ko
kernel/net/ipv6/tunnel6.ko
kernel/net/ipv6/xfrm6_mode_transport.ko
kernel/net/ipv6/xfrm6_mode_tunnel.ko
kernel/net/ipv6/xfrm6_mode_ro.ko
kernel/net/ipv6/xfrm6_mode_beet.ko
kernel/net/ipv6/mip6.ko
kernel/net/ipv6/sit.ko
kernel/net/ipv6/ip6_tunnel.ko
kernel/net/ipv6/ip6_gre.ko
kernel/net/packet/af_packet_diag.ko
kernel/net/8021q/8021q.ko
kernel/net/wireless/lib80211.ko
kernel/net/wireless/lib80211_crypt_wep.ko
kernel/net/wireless/lib80211_crypt_ccmp.ko
kernel/net/wireless/lib80211_crypt_tkip.ko
kernel/net/rfkill/rfkill-regulator.ko
kernel/net/llc/llc.ko
kernel/net/llc/llc2.ko
kernel/net/key/af_key.ko
kernel/net/bridge/bridge.ko
kernel/net/bridge/netfilter/ebtables.ko
kernel/net/bridge/netfilter/ebtable_broute.ko
kernel/net/bridge/netfilter/ebtable_filter.ko
kernel/net/bridge/netfilter/ebtable_nat.ko
kernel/net/bridge/netfilter/ebt_802_3.ko
kernel/net/bridge/netfilter/ebt_among.ko
kernel/net/bridge/netfilter/ebt_arp.ko
kernel/net/bridge/netfilter/ebt_ip.ko
kernel/net/bridge/netfilter/ebt_ip6.ko
kernel/net/bridge/netfilter/ebt_limit.ko
kernel/net/bridge/netfilter/ebt_mark_m.ko
kernel/net/bridge/netfilter/ebt_pkttype.ko
kernel/net/bridge/netfilter/ebt_stp.ko
kernel/net/bridge/netfilter/ebt_vlan.ko
kernel/net/bridge/netfilter/ebt_arpreply.ko
kernel/net/bridge/netfilter/ebt_mark.ko
kernel/net/bridge/netfilter/ebt_dnat.ko
kernel/net/bridge/netfilter/ebt_redirect.ko
kernel/net/bridge/netfilter/ebt_snat.ko
kernel/net/bridge/netfilter/ebt_log.ko
kernel/net/bridge/netfilter/ebt_nflog.ko
kernel/net/dsa/dsa_core.ko
kernel/net/ipx/ipx.ko
kernel/net/appletalk/appletalk.ko
kernel/net/wanrouter/wanrouter.ko
kernel/net/x25/x25.ko
kernel/net/lapb/lapb.ko
kernel/net/netrom/netrom.ko
kernel/net/rose/rose.ko
kernel/net/ax25/ax25.ko
kernel/net/can/can.ko
kernel/net/can/can-raw.ko
kernel/net/can/can-bcm.ko
kernel/net/can/can-gw.ko
kernel/net/irda/irda.ko
kernel/net/irda/irlan/irlan.ko
kernel/net/irda/irnet/irnet.ko
kernel/net/irda/ircomm/ircomm.ko
kernel/net/irda/ircomm/ircomm-tty.ko
kernel/net/bluetooth/bluetooth.ko
kernel/net/bluetooth/rfcomm/rfcomm.ko
kernel/net/bluetooth/bnep/bnep.ko
kernel/net/bluetooth/cmtp/cmtp.ko
kernel/net/bluetooth/hidp/hidp.ko
kernel/net/sunrpc/sunrpc.ko
kernel/net/sunrpc/auth_gss/auth_rpcgss.ko
kernel/net/sunrpc/auth_gss/rpcsec_gss_krb5.ko
kernel/net/sunrpc/xprtrdma/xprtrdma.ko
kernel/net/sunrpc/xprtrdma/svcrdma.ko
kernel/net/rxrpc/af-rxrpc.ko
kernel/net/rxrpc/rxkad.ko
kernel/net/atm/atm.ko
kernel/net/atm/clip.ko
kernel/net/atm/br2684.ko
kernel/net/atm/lec.ko
kernel/net/atm/mpoa.ko
kernel/net/atm/pppoatm.ko
kernel/net/l2tp/l2tp_core.ko
kernel/net/l2tp/l2tp_ppp.ko
kernel/net/l2tp/l2tp_debugfs.ko
kernel/net/decnet/netfilter/dn_rtmsg.ko
kernel/net/decnet/decnet.ko
kernel/net/phonet/phonet.ko
kernel/net/phonet/pn_pep.ko
kernel/net/dccp/dccp.ko
kernel/net/dccp/dccp_ipv4.ko
kernel/net/dccp/dccp_ipv6.ko
kernel/net/dccp/dccp_diag.ko
kernel/net/dccp/dccp_probe.ko
kernel/net/sctp/sctp.ko
kernel/net/sctp/sctp_probe.ko
kernel/net/rds/rds.ko
kernel/net/rds/rds_rdma.ko
kernel/net/rds/rds_tcp.ko
kernel/net/tipc/tipc.ko
kernel/net/9p/9pnet.ko
kernel/net/9p/9pnet_virtio.ko
kernel/net/9p/9pnet_rdma.ko
kernel/net/caif/caif.ko
kernel/net/caif/chnl_net.ko
kernel/net/caif/caif_socket.ko
kernel/net/caif/caif_usb.ko
kernel/net/ieee802154/ieee802154.ko
kernel/net/ieee802154/af_802154.ko
kernel/net/ieee802154/6lowpan.ko
kernel/net/mac802154/mac802154.ko
kernel/net/wimax/wimax.ko
kernel/net/ceph/libceph.ko
kernel/net/batman-adv/batman-adv.ko
kernel/net/nfc/nfc.ko
kernel/net/nfc/nci/nci.ko
kernel/net/nfc/hci/hci.ko
kernel/net/openvswitch/openvswitch.ko
kernel/lib/xz/xz_dec_test.ko
kernel/lib/test-kstrtox.ko
kernel/lib/crc-ccitt.ko
kernel/lib/crc-itu-t.ko
kernel/lib/crc7.ko
kernel/lib/libcrc32c.ko
kernel/lib/crc8.ko
kernel/lib/zlib_deflate/zlib_deflate.ko
kernel/lib/reed_solomon/reed_solomon.ko
kernel/lib/bch.ko
kernel/lib/raid6/raid6_pq.ko
kernel/lib/ts_kmp.ko
kernel/lib/ts_bm.ko
kernel/lib/ts_fsm.ko
kernel/lib/notifier-error-inject.ko
kernel/lib/cpu-notifier-error-inject.ko
kernel/lib/pm-notifier-error-inject.ko
kernel/lib/memory-notifier-error-inject.ko
kernel/lib/lru_cache.ko
kernel/lib/cordic.ko
kernel/lib/rbtree_test.ko
kernel/lib/interval_tree_test.ko
updates/drivers/net/wireless/rtlwifi/rtl8188ee/rtl8188ee.ko
updates/compat/compat.ko
updates/dkms/vboxdrv.ko
updates/dkms/vboxnetflt.ko
updates/dkms/vboxnetadp.ko
updates/dkms/fglrx_experimental_13.ko
updates/dkms/vboxpci.ko
updates/drivers/net/wireless/rtlwifi/rtlwifi.ko
updates/drivers/net/wireless/rtlwifi/rtl8723ae/rtl8723ae.ko
updates/drivers/net/wireless/rtlwifi/rtl8192ce/rtl8192ce.ko
updates/drivers/net/wireless/rtlwifi/rtl8192de/rtl8192de.ko
updates/drivers/net/wireless/rtlwifi/rtl8192cu/rtl8192cu.ko
updates/drivers/net/wireless/rtlwifi/rtl8192se/rtl8192se.ko
updates/drivers/net/wireless/rtlwifi/rtl8192c/rtl8192c-common.ko
kernel/drivers/net/ethernet/realtek/r8101.ko
updates/net/mac80211/mac80211.ko
updates/net/wireless/cfg80211.ko
initrd/vesafb.ko
```

---

### Post by chili555 on 2014-03-19
This appears to be the classic case of the device roaming from one network to another nearby network with the same name:> wlan0: authenticate with 00:13:60:ef:73:c2Which is this:> [COLOR="#FF0000"]eduroam[/COLOR]:         Infra, 00:13:60:EF:73:C2, Freq 2412 MHz, Rate 54 Mb/s, [COLOR="#FF0000"]Strength 56[/COLOR] WPA WPA2 Enterprise...but then:> wlan0: associate with 70:81:05:45:6b:82 (try 1/3)Which is this:> [COLOR="#FF0000"]eduroam[/COLOR]:         Infra, 70:81:05:45:6B:82, Freq 2462 MHz, Rate 54 Mb/s, [COLOR="#FF0000"]Strength 68[/COLOR] WPA WPA2 EnterpriseAnd then, a few minutes later, it starts again.

A probable solution is to tell Network Manager to bind to one and only network and, like my ex-girlfriend, stop looking around for something better! The procedure is described here: [http://askubuntu.com/questions/425583/ubuntu-connect-drops-worked-for-a-while-then-started-dropping-again](http://askubuntu.com/questions/425583/ubuntu-connect-drops-worked-for-a-while-then-started-dropping-again)

---

### Post by PsykoMantis on 2014-03-20
Thanks so much it worked!!!
It because there are people like you, that helps the next one, that the world is better!!!! 

Cheers psykomantis!):P

---

### Post by chili555 on 2014-03-20
Glad it's working. So that the searchers will find the answer, please use thread tools at the top to mark Solved.

---

