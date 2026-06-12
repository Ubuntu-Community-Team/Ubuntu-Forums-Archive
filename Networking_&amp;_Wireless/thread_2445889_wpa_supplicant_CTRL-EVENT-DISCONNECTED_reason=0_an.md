---
title: "wpa_supplicant CTRL-EVENT-DISCONNECTED reason=0 and slow with a BCM4360 wireless card"
date: 2020-06-21
forum: Networking &amp; Wireless
---

### Post by jrussell88 on 2020-06-21
I'm running Ubuntu 19.10 x64 and using the default bcmwl-kernel-source version 6.30.223.271+bdcom-0ubuntu5

I get repeated wifi disconnections and speeds around 90kBps from my Broadcom BCM4360 wireless card. 

Can you suggest how to fix this? TIA.

```
Jun 21 18:08:46 JohnsMacBookPro wpa_supplicant[1878]: wlp2s0: CTRL-EVENT-DISCONNECTED bssid=c0:56:27:16:47:10 reason=0Jun 21 18:08:46 JohnsMacBookPro wpa_supplicant[1878]: dbus: wpa_dbus_property_changed: no property SessionLength in object /fi/w1/wpa_supplicant1/Interfaces/0
Jun 21 18:08:46 JohnsMacBookPro wpa_supplicant[1878]: wlp2s0: CTRL-EVENT-REGDOM-CHANGE init=CORE type=WORLD
Jun 21 18:08:46 JohnsMacBookPro wpa_supplicant[1878]: wlp2s0: CTRL-EVENT-REGDOM-CHANGE init=USER type=COUNTRY alpha2=GB
Jun 21 18:08:52 JohnsMacBookPro wpa_supplicant[1878]: wlp2s0: Trying to associate with c0:56:27:16:47:10 (SSID='46SMS' freq=2427 MHz)
Jun 21 18:08:52 JohnsMacBookPro wpa_supplicant[1878]: wlp2s0: Associated with c0:56:27:16:47:10
Jun 21 18:08:52 JohnsMacBookPro wpa_supplicant[1878]: wlp2s0: CTRL-EVENT-SUBNET-STATUS-UPDATE status=0
Jun 21 18:08:52 JohnsMacBookPro wpa_supplicant[1878]: wlp2s0: WPA: Key negotiation completed with c0:56:27:16:47:10 [PTK=CCMP GTK=CCMP]
Jun 21 18:08:52 JohnsMacBookPro wpa_supplicant[1878]: wlp2s0: CTRL-EVENT-CONNECTED - Connection to c0:56:27:16:47:10 completed [id=0 id_str=]
Jun 21 18:08:52 JohnsMacBookPro wpa_supplicant[1878]: bgscan simple: Failed to enable signal strength monitoring
Jun 21 18:09:00 JohnsMacBookPro wpa_supplicant[1878]: wlp2s0: CTRL-EVENT-DISCONNECTED bssid=c0:56:27:16:47:10 reason=0
Jun 21 18:09:00 JohnsMacBookPro wpa_supplicant[1878]: dbus: wpa_dbus_property_changed: no property SessionLength in object /fi/w1/wpa_supplicant1/Interfaces/0
Jun 21 18:09:00 JohnsMacBookPro wpa_supplicant[1878]: wlp2s0: CTRL-EVENT-REGDOM-CHANGE init=CORE type=WORLD
Jun 21 18:09:00 JohnsMacBookPro wpa_supplicant[1878]: wlp2s0: CTRL-EVENT-REGDOM-CHANGE init=USER type=COUNTRY alpha2=GB
Jun 21 18:09:06 JohnsMacBookPro wpa_supplicant[1878]: wlp2s0: Trying to associate with c0:56:27:16:47:10 (SSID='46SMS' freq=2427 MHz)
Jun 21 18:09:06 JohnsMacBookPro wpa_supplicant[1878]: wlp2s0: Associated with c0:56:27:16:47:10
Jun 21 18:09:06 JohnsMacBookPro wpa_supplicant[1878]: wlp2s0: CTRL-EVENT-SUBNET-STATUS-UPDATE status=0
Jun 21 18:09:06 JohnsMacBookPro wpa_supplicant[1878]: wlp2s0: CTRL-EVENT-DISCONNECTED bssid=c0:56:27:16:47:10 reason=0
Jun 21 18:09:06 JohnsMacBookPro wpa_supplicant[1878]: dbus: wpa_dbus_property_changed: no property SessionLength in object /fi/w1/wpa_supplicant1/Interfaces/0
Jun 21 18:09:06 JohnsMacBookPro wpa_supplicant[1878]: wlp2s0: CTRL-EVENT-REGDOM-CHANGE init=CORE type=WORLD
Jun 21 18:09:06 JohnsMacBookPro wpa_supplicant[1878]: wlp2s0: CTRL-EVENT-REGDOM-CHANGE init=USER type=COUNTRY alpha2=GB
Jun 21 18:09:12 JohnsMacBookPro wpa_supplicant[1878]: wlp2s0: Trying to associate with c0:56:27:16:47:10 (SSID='46SMS' freq=2427 MHz)
Jun 21 18:09:12 JohnsMacBookPro wpa_supplicant[1878]: wlp2s0: Associated with c0:56:27:16:47:10
Jun 21 18:09:12 JohnsMacBookPro wpa_supplicant[1878]: wlp2s0: CTRL-EVENT-SUBNET-STATUS-UPDATE status=0
Jun 21 18:09:12 JohnsMacBookPro wpa_supplicant[1878]: wlp2s0: WPA: Key negotiation completed with c0:56:27:16:47:10 [PTK=CCMP GTK=CCMP]
Jun 21 18:09:12 JohnsMacBookPro wpa_supplicant[1878]: wlp2s0: CTRL-EVENT-CONNECTED - Connection to c0:56:27:16:47:10 completed [id=0 id_str=]
Jun 21 18:09:12 JohnsMacBookPro wpa_supplicant[1878]: bgscan simple: Failed to enable signal strength monitoring

```

```
$ lspci -vnn -d 14e4:
02:00.0 Network controller [0280]: Broadcom Inc. and subsidiaries BCM4360 802.11ac Wireless Network Adapter [14e4:43a0] (rev 03)
	Subsystem: Apple Inc. BCM4360 802.11ac Wireless Network Adapter [106b:0134]
	Flags: bus master, fast devsel, latency 0, IRQ 18
	Memory at a0600000 (64-bit, non-prefetchable) [size=32K]
	Memory at a0400000 (64-bit, non-prefetchable) [size=2M]
	Capabilities: <access denied>
	Kernel driver in use: wl
	Kernel modules: bcma, wl



```

```
$ sudo lshw -C network
  *-network                 
       description: Ethernet interface
       product: NetXtreme BCM57762 Gigabit Ethernet PCIe
       vendor: Broadcom Inc. and subsidiaries
       physical id: 0
       bus info: pci@0000:0a:00.0
       logical name: ens9
       version: 00
       serial: 68:5b:35:ac:95:69
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi msix pciexpress bus_master cap_list rom ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.137 duplex=full firmware=57762-a1.10 latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:19 memory:acc00000-acc0ffff memory:acc10000-acc1ffff memory:a0c00000-a0c0ffff
  *-network
       description: Wireless interface
       product: BCM4360 802.11ac Wireless Network Adapter
       vendor: Broadcom Inc. and subsidiaries
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlp2s0
       version: 03
       serial: b8:e8:56:3a:42:26
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=6.30.223.271 (r587334) ip=192.168.10.100 latency=0 multicast=yes wireless=IEEE 802.11
       resources: irq:18 memory:a0600000-a0607fff memory:a0400000-a05fffff



```

```
$ sudo dpkg -s bcmwl-kernel-source | grep Version
Version: 6.30.223.271+bdcom-0ubuntu5
```

```
$ uname -r -m
5.3.0-59-generic x86_64
```

It connects on the 2.4GHz SSID

```
$ sudo iwlist wlp2s0 scan
wlp2s0    Scan completed :
          Cell 01 - Address: C0:56:27:16:47:10
                    Channel:4
                    Frequency:2.427 GHz (Channel 4)
                    Quality=70/70  Signal level=-34 dBm  
                    Encryption key:on
                    ESSID:"46SMS"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 24ms ago
                    IE: Unknown: 00053436534D53
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030104
                    IE: Unknown: 2A0104
                    IE: Unknown: 32043048606C
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 3B025100
                    IE: Unknown: 2D1AED191BFFFFFFFF00000000000000000100000000000000000000
                    IE: Unknown: 3D1604000400000000000000000000000000000000000000
                    IE: Unknown: 7F080400000000000040
                    IE: Unknown: DD180050F2020101000003A4400027A4000042435E0062322F00
...
          Cell 06 - Address: C0:56:27:16:47:11
                    Channel:112
                    Frequency:5.56 GHz
                    Quality=70/70  Signal level=-38 dBm  
                    Encryption key:on
                    ESSID:"46SMS"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Bit Rates:63.5 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 24ms ago
                    IE: Unknown: 00053436534D53
                    IE: Unknown: 01088C129824B048606C
                    IE: Unknown: 030170
                    IE: Unknown: 070A474220240814640B1B00
                    IE: Unknown: 3201FF
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 3B028000
                    IE: Unknown: 2D1AEF091BFFFFFFFF00000000000000000100000000000000000000
                    IE: Unknown: 3D1670070000000000000000000000000000000000000000
                    IE: Unknown: 7F080400000000000040
                    IE: Unknown: BF0CB2018033AAFF0000AAFF0000
                    IE: Unknown: C005016A00FCFF
                    IE: Unknown: C30402363636
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00


```

---

