---
title: "Ubuntu 14.04: Realtek RTL8188EE wireless randomly drops, disappears"
date: 2015-02-08
forum: Networking &amp; Wireless
---

### Post by Halfling Rogue on 2015-02-08
Have a similar issue to [this]("http://askubuntu.com/questions/525397/network-disappears-from-list-disconnects-others-remain"); I have an HP 15-f009ca with 64-bit Ubuntu 14.04 LTS as its sole OS (no dual boot), and it will randomly disconnect its wifi connection while simultaneously removing the connection from the Wireless Networks list.

I can usually reconnect using the "Connect to Hidden Wi-Fi Network..." option, but this is not ideal as 1) it doesn't always work (right now all networks have disappeared from the list and reconnecting is not working), 2) even when it does work, it keeps disconnecting while I'm trying to do system updates, and 3) this laptop is going to a grandparent who is not going to know to do that if the connection gets dropped.

I know it's not an issue with the router or the connection, as we have several computers in the house using this connection on a daily basis (including Windows machines, Ubuntu 14.04, and Ubuntu 12.04) with no drops and no disappearances from the Wireless Network list.

wireless-info script results attached.

Here's the results of iwlist scan when disconnected (Cell 01 is the main connection I'm trying to use):
```
eth0      Interface doesn't support scanning.

lo        Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: C0:C1:C0:22:91:4B
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=54/70  Signal level=-56 dBm
                    Encryption key:on
                    ESSID:"********"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000004184c985651
                    Extra: Last beacon: 8ms ago
                    IE: Unknown: 000753617669636873
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030106
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1AFC181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1606080400000000000000000000000000000000000000
                    IE: Unknown: DD700050F204104A00011010440001021041000100103B000103104700100E9514E096A2E86BB46D4C4324F64E40102100074C696E6B737973102300054531303030102400063132333435361042000234321054000800060050F2040001101100054531303030100800020084103C000101
                    IE: Unknown: DD090010180202F0040000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
          Cell 02 - Address: 38:60:77:23:A5:97
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=28/70  Signal level=-82 dBm
                    Encryption key:on
                    ESSID:"******"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000017446166195
                    Extra: Last beacon: 732ms ago
                    IE: Unknown: 0006373031433238
                    IE: Unknown: 010482848B96
                    IE: Unknown: 030101
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0104
                    IE: Unknown: 2F0104
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32080C1218243048606C
                    IE: Unknown: 2D1AFC181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1601080000000000000000000000000000000000000000
                    IE: Unknown: DD090010180201F02C0000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 03 - Address: B4:75:0E:FA:B6:29
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=46/70  Signal level=-64 dBm
                    Encryption key:on
                    ESSID:"********"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000233641529e6
                    Extra: Last beacon: 8ms ago
                    IE: Unknown: 000C4C696E6B7379733033313332
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030106
                    IE: Unknown: 2A0104
                    IE: Unknown: 2F0104
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1A6F1917FFFFFF0000000000000000000000000000000000000000
                    IE: Unknown: 3D16060F1600000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F080500000000000040
                    IE: Unknown: DD8C0050F204104A0001101044000102103B00010310470010E7E1206110AF22941714083450C62FB11021000B4C696E6B737973204C4C431023000E4C696E6B73797320454136393030102400064541363930301042000230311054000800060050F20400011011000F4C696E6B737973303331333220415010080002200C103C0001031049000600372A000120
                    IE: Unknown: DD090010180204001C0000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: 46057200010000
          Cell 04 - Address: C0:C1:C0:22:91:4C
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=56/70  Signal level=-54 dBm
                    Encryption key:off
                    ESSID:"*******"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000004184c987050
                    Extra: Last beacon: 8ms ago
                    IE: Unknown: 000D536176696368732D6775657374
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030106
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1AFC181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1606080400000000000000000000000000000000000000
                    IE: Unknown: DD090010180202F0040000
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
          Cell 05 - Address: 20:C9:D0:1A:D0:6F
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=34/70  Signal level=-76 dBm
                    Encryption key:on
                    ESSID:"*******"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000005ff1832b189
                    Extra: Last beacon: 184ms ago
                    IE: Unknown: 0013526F6E27732057692D4669204E6574776F726B
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 03010B
                    IE: Unknown: 050400030000
                    IE: Unknown: 0706434120010B1E
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 2D1AAD511BFFFFFF0000000000000000000000000000000000000000
                    IE: Unknown: 33027E95
                    IE: Unknown: 33025106
                    IE: Unknown: 3D160B000000000000000000000000000000000000000000
                    IE: Unknown: 46050200010000
                    IE: Unknown: DD180050F2020101010003A4000027A4000042435E0062322F00
                    IE: Unknown: DD0700039301740320
                    IE: Unknown: DD0E0017F2070001010620C9D01AD06F
                    IE: Unknown: DD0B0017F20100010100000007
          Cell 06 - Address: 78:54:2E:EE:B4:A2
                    Channel:10
                    Frequency:2.457 GHz (Channel 10)
                    Quality=70/70  Signal level=-18 dBm
                    Encryption key:on
                    ESSID:"*******"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000d37e1d8b176
                    Extra: Last beacon: 152ms ago
                    IE: Unknown: 000A4861766F6352696E676F
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 03010A
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: 2D1A2C181EFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D160A000000000000000000000000000000000000000000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C332C181EFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C340A000000000000000000000000000000000000000000
                    IE: Unknown: DD0600E04C020160
                    IE: Unknown: DD180050F204104A00011010440001021049000600372A000120
          Cell 07 - Address: 8C:7F:3B:7E:9C:68
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=26/70  Signal level=-84 dBm
                    Encryption key:on
                    ESSID:"******"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000080a15ba1bc
                    Extra: Last beacon: 844ms ago
                    IE: Unknown: 000543686F6D65
                    IE: Unknown: 010882848B9624B0486C
                    IE: Unknown: 030101
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0104
                    IE: Unknown: 2F0104
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32048C129860
                    IE: Unknown: 2D1ABD181BFFFFFF0000000000000000000000000000000000000000
                    IE: Unknown: 3D1601001300000000000000000000000000000000000000
                    IE: Unknown: DD090010180201001C0000
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101840003A4000027A4000042435E0062322F00
          Cell 08 - Address: 20:76:00:1D:FC:24
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=28/70  Signal level=-82 dBm
                    Encryption key:on
                    ESSID:"********"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s
```


Results of iwconfig when connected:
```
eth0      no wireless extensions.

lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"******"
          Mode:Managed  Frequency:2.437 GHz  Access Point: C0:C1:C0:22:91:4B
          Bit Rate=72.2 Mb/s   Tx-Power=20 dBm
          Retry  long limit:7   RTS thr=2347 B   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality=58/70  Signal level=-52 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```


Results of lspci:
```
00:00.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 16h Processor Root Complex
00:01.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Kabini [Radeon HD 8210]
00:01.1 Audio device: Advanced Micro Devices, Inc. [AMD/ATI] Device 9840
00:02.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 16h Processor Function 0
00:02.2 PCI bridge: Advanced Micro Devices, Inc. [AMD] Family 16h Processor Functions 5:1
00:02.3 PCI bridge: Advanced Micro Devices, Inc. [AMD] Family 16h Processor Functions 5:1
00:02.5 PCI bridge: Advanced Micro Devices, Inc. [AMD] Family 16h Processor Functions 5:1
00:10.0 USB controller: Advanced Micro Devices, Inc. [AMD] FCH USB XHCI Controller (rev 01)
00:11.0 SATA controller: Advanced Micro Devices, Inc. [AMD] FCH SATA Controller [AHCI mode]
00:12.0 USB controller: Advanced Micro Devices, Inc. [AMD] FCH USB OHCI Controller (rev 39)
00:12.2 USB controller: Advanced Micro Devices, Inc. [AMD] FCH USB EHCI Controller (rev 39)
00:13.0 USB controller: Advanced Micro Devices, Inc. [AMD] FCH USB OHCI Controller (rev 39)
00:13.2 USB controller: Advanced Micro Devices, Inc. [AMD] FCH USB EHCI Controller (rev 39)
00:14.0 SMBus: Advanced Micro Devices, Inc. [AMD] FCH SMBus Controller (rev 3a)
00:14.2 Audio device: Advanced Micro Devices, Inc. [AMD] FCH Azalia Controller (rev 02)
00:14.3 ISA bridge: Advanced Micro Devices, Inc. [AMD] FCH LPC Bridge (rev 11)
00:18.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 16h Processor Function 0
00:18.1 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 16h Processor Function 1
00:18.2 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 16h Processor Function 2
00:18.3 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 16h Processor Function 3
00:18.4 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 16h Processor Function 4
00:18.5 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 16h Processor Function 5
01:00.0 Network controller: Realtek Semiconductor Co., Ltd. RTL8188EE Wireless Network Adapter (rev 01)
05:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 07)
06:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. RTS5229 PCI Express Card Reader (rev 01)
```


Results of lshw -C network:
```
*-network
       description: Wireless interface
       product: RTL8188EE Wireless Network Adapter
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: wlan0
       version: 01
       serial: 90:48:9a:de:e4:b2
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rtl8188ee driverversion=3.13.0-45-generic firmware=N/A ip=192.168.1.135 latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn
       resources: irq:28 ioport:3000(size=256) memory:f1000000-f1003fff
  *-network
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: eth0
       version: 07
       serial: 6c:c2:17:65:65:1d
       size: 10Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=rtl8106e-1_0.0.1 06/29/12 latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:76 ioport:2000(size=256) memory:f0104000-f0104fff memory:f0100000-f0103fff memory:f0110000-f011ffff
```


Any insight would be appreciated.

---

### Post by EzerchE on 2015-02-09
Same problem. still waiting for a solution...

---

### Post by Halfling Rogue on 2015-02-09
Belatedly read the forum rules and added output from the wireless script.

---

### Post by EzerchE on 2015-02-10
I have resolved my problem! So please try; [http://ubuntuforums.org/showthread.php?t=2264585](http://ubuntuforums.org/showthread.php?t=2264585)

---

### Post by jeremy31 on 2015-02-10
```
sudo apt-get install linux-headers-generic build-essential
```
```
[FONT=Ubuntu Mono]wget -N -t 5 -T 10 https://www.kernel.org/pub/linux/kernel/projects/backports/stable/v3.18.1/backports-3.18.1-1.tar.xz[/FONT]
```
```
tar -xf backports-3.18.1-1.tar.xz
```
```
cd ~/backports-3.18.1-1
```
```
make defconfig-rtlwifi
```
```
make
```
```
sudo make install
```
Reboot
It usually works well with realtek

---

### Post by Halfling Rogue on 2015-02-11
> **EzerchE said:**
> I have resolved my problem! So please try; [http://ubuntuforums.org/showthread.php?t=2264585](http://ubuntuforums.org/showthread.php?t=2264585)

Thanks, EzerchE. I gave it a shot, but while connection strength has improved, the network is still getting dropped. And now when it drops, *all* local wifi networks are disappearing from the list.

> **jeremy31 said:**
> ```
sudo apt-get install linux-headers-generic build-essential
```
```
wget -N -t 5 -T 10 https://www.kernel.org/pub/linux/ker....18.1-1.tar.xz
```
```
tar -xf backports-3.18.1-1.tar.xz
```
```
cd ~/backports-3.18.1-1
```
```
make defconfig-rtlwifi
```
```
make
```
```
sudo make install
```
Reboot
It usually works well with realtek

I might give that a shot, jeremy. Is the build safe for 64 bit machines? What's the full link for the kernel.org wget?

---

### Post by jeremy31 on 2015-02-11
```
[FONT=Ubuntu Mono]wget -N -t 5 -T 10 https://www.kernel.org/pub/linux/kernel/projects/backports/stable/v3.18.1/backports-3.18.1-1.tar.xz[/FONT]
```[FONT=Ubuntu Mono]

I have used backports on 64 bit machines.  Didn't notice the URL got shortened when I posted from my phone, thanks[/FONT]

---

### Post by Halfling Rogue on 2015-02-11
> **jeremy31 said:**
> I have used backports on 64 bit machines.  Didn't notice the URL got shortened when I posted from my phone, thanks[/FONT]

Getting the error "xz: (stdin): Unexpected end of input; tar: Unexpected EOF in archive" when trying to unpack. Got a mirror anywhere?

---

### Post by jeremy31 on 2015-02-12
Could try downloading from browser [COLOR=#000000][FONT=Ubuntu Mono]https://www.kernel.org/pub/linux/kernel/projects/backports/stable/v3.18.1/backports-3.18.1-1.tar.xz[/FONT][/COLOR]

---

### Post by Halfling Rogue on 2015-02-12
Already gave that a shot when the wget started having trouble. No go. :(

---

### Post by jeremy31 on 2015-02-12
not sure what is going on but it just downloaded and extracted on my phone

---

### Post by Halfling Rogue on 2015-02-12
Do you know if they have an md5 checksum? If not I might try extracting it on another machine and transferring it.

---

### Post by jeremy31 on 2015-02-12
I could do one when I get home but it might be in the [https://www.kernel.org/pub/linux/kernel/projects/backports/stable/v3.18.1/](https://www.kernel.org/pub/linux/kernel/projects/backports/stable/v3.18.1/) directory.  There is a file named sha256sums.asc but my phone won't open it

---

### Post by kadir7 on 2015-02-12
Hallo every body could you help me why my wirrelles card that chipest does not interface....my wirrelles card is rtl8723be


backbox@KaesarG40-45:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 28:d2:44:8b:24:fa  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

eth1      Link encap:Ethernet  HWaddr 00:1e:10:1f:00:00  
          inet addr:192.168.8.100  Bcast:192.168.8.255  Mask:255.255.255.0
          inet6 addr: fe80::21e:10ff:fe1f:0/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:337700 errors:0 dropped:0 overruns:0 frame:0
          TX packets:219756 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:463545364 (463.5 MB)  TX bytes:17977451 (17.9 MB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:5700 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5700 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:923782 (923.7 KB)  TX bytes:923782 (923.7 KB)

wlan0     Link encap:Ethernet  HWaddr 00:71:cc:1a:db:db  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

backbox@KaesarG40-45:~$ iwconfig
eth0      no wireless extensions.

eth1      no wireless extensions.

lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          
backbox@KaesarG40-45:~$ sudo su
[sudo] password for backbox: 
root@KaesarG40-45:/home/backbox# airmon-ng


Interface      Chipset           Driver

wlan0               Unknown          rtl8723be - [phy0]

root@KaesarG40-45:/home/backbox#

---

### Post by jeremy31 on 2015-02-12
Try the instructions in post #5

---

### Post by jeremy31 on 2015-02-13
> **Halfling Rogue said:**
> Do you know if they have an md5 checksum? If not I might try extracting it on another machine and transferring it.
I got this for md5sum ```
6cef5f2c800e12441d2cba9fa42b6a5b
```

---

### Post by Halfling Rogue on 2015-02-14
Perfect, thanks! Got it to work this time; the connection might have been affecting the download. Trying the make and install now, will see how it goes.

---

### Post by Halfling Rogue on 2015-02-14
Been half a day so far with no connection drops; I think that might have done it! Thanks a bunch, jeremy.

---

### Post by thisisbasil on 2015-06-08
I bought a new laptop and am Xubuntu 14.04. Its also got the RTL8188EE chipset. It is beyond annoying at this point.  It is finicky if/when it connects to a hotspot; if connecting, it usually takes a LONG time and this is after cycling through any and all possible connections. It will randomly disconnect from a hotspot. It will not even see other hotspots. I tried whats listed in post 5 but it still has the same activity. Any other suggestions would be appreciated.

---

### Post by Pilot6 on 2015-06-09
I built a ppa with Realtek wireless drivers in DKMS format. It can be installed by

```
sudo add-apt-repository ppa:hanipouspilot/rtlwifi
sudo apt-get update
sudo apt-gt install rtlwifi-new-dkms linux-firmware
```

For rtl8192cu USB dongles a standalone driver is better

```
sudo apt-get install rtl8192cu-dkms
```

form same PPA.

Bluetooth driver is also there

```
sudo apt-get install [COLOR=#333333][FONT=Ubuntu]rtl8723au-bt-dkms[/FONT][/COLOR]
```

---

### Post by thisisbasil on 2015-06-09
I get this error when trying to add the repository:

> 
Cannot add PPA: 'ppa:hanipouspilot/rtlwifi'.
Please check that the PPA name or format is correct.


edit: nevermind, I guess it was my *awesome* realtek wireless card crapping the bed when trying to add. I tried again and it added it.

I rebooted and now it is not able to see my card I guess, as wifi is not an option to enable/disable. This is the output of the apt-get install command.  

```

rtl_pci:
 Running module version sanity check.
  - Original module
    - Multiple original modules exist but DKMS does not know which to pick
    - Due to the confusion, none will be considered during a later uninstall
  - Multiple same named modules!
    - 2 named rtl_pci.ko in /lib/modules/3.16.0-38-generic/
  - Installation
    - Installing to /lib/modules/3.16.0-38-generic/updates/dkms/
 
 rtl_usb.ko:
 Running module version sanity check.
  - Original module
    - Multiple original modules exist but DKMS does not know which to pick
    - Due to the confusion, none will be considered during a later uninstall
  - Multiple same named modules!
    - 2 named rtl_usb.ko in /lib/modules/3.16.0-38-generic/
  - Installation
    - Installing to /lib/modules/3.16.0-38-generic/updates/dkms/
 
 rtlwifi.ko:
 Running module version sanity check.
 Error! Module version backported for rtlwifi.ko
 is not newer than what is already found in kernel 3.16.0-38-generic (backported).
 You may override by specifying --force.
 
 btcoexist.ko:
 Running module version sanity check.
 Error! Module version backported for btcoexist.ko
 is not newer than what is already found in kernel 3.16.0-38-generic (backported).
 You may override by specifying --force.
 
 rtl8188ee.ko:
 Running module version sanity check.
 Error! Module version backported for rtl8188ee.ko
 is not newer than what is already found in kernel 3.16.0-38-generic (backported).
 You may override by specifying --force.
 
 rtl8192c-common.ko:
 Running module version sanity check.
  - Original module
    - Multiple original modules exist but DKMS does not know which to pick
    - Due to the confusion, none will be considered during a later uninstall
  - Multiple same named modules!
    - 2 named rtl8192c-common.ko in /lib/modules/3.16.0-38-generic/
  - Installation
    - Installing to /lib/modules/3.16.0-38-generic/updates/dkms/
 
 rtl8192ce.ko:
 Running module version sanity check.
 Error! Module version backported for rtl8192ce.ko
 is not newer than what is already found in kernel 3.16.0-38-generic (backported).
 You may override by specifying --force.
 
 rtl8192cu.ko:
 Running module version sanity check.
 Error! Module version backported for rtl8192cu.ko
 is not newer than what is already found in kernel 3.16.0-38-generic (backported).
 You may override by specifying --force.
 
 rtl8192de.ko:
 Running module version sanity check.
 Error! Module version backported for rtl8192de.ko
 is not newer than what is already found in kernel 3.16.0-38-generic (backported).
 You may override by specifying --force.
 
 rtl8192ee.ko:
 Running module version sanity check.
 Error! Module version backported for rtl8192ee.ko
 is not newer than what is already found in kernel 3.16.0-38-generic (backported).
 You may override by specifying --force.
 
 rtl8192se.ko:
 Running module version sanity check.
 Error! Module version backported for rtl8192se.ko
 is not newer than what is already found in kernel 3.16.0-38-generic (backported).
 You may override by specifying --force.
 
 rtl8723ae.ko:
 Running module version sanity check.
 Error! Module version backported for rtl8723ae.ko
 is not newer than what is already found in kernel 3.16.0-38-generic (backported).
 You may override by specifying --force.
 
 rtl8723be.ko:
 Running module version sanity check.
 Error! Module version backported for rtl8723be.ko
 is not newer than what is already found in kernel 3.16.0-38-generic (backported).
 You may override by specifying --force.
 
 rtl8821ae.ko:
 Running module version sanity check.
 Error! Module version backported for rtl8821ae.ko
 is not newer than what is already found in kernel 3.16.0-38-generic (backported).
 You may override by specifying --force.
 
 depmod.........
 
 Backing up initrd.img-3.16.0-38-generic to /boot/initrd.img-3.16.0-38-generic.old-dkms
 Making new initrd.img-3.16.0-38-generic
 (If next boot fails, revert to initrd.img-3.16.0-38-generic.old-dkms image)
 update-initramfs....
 
 DKMS: install completed.
 Processing triggers for initramfs-tools (0.103ubuntu4.2) ...
 update-initramfs: Generating /boot/initrd.img-3.16.0-38-generic

```

I am assuming that an apt-get remove won't roll back to where I was?

---

### Post by Halfling Rogue on 2015-06-09
I spoke too soon &#8212; the card's back to randomly disconnecting and refusing to reconnect. Hesitant to try Pilot6's fix since thisisbasil says his card is now crapped (and I don't have the computer in my possession, I have to give instructions to a third party).

Does *anyone* have a fix for this? Seems a rather major thing for the distro to miss, and it looks like the issue's been around at least since 2012.

---

### Post by Halfling Rogue on 2015-06-09
Found a fix on [http://askubuntu.com/questions/337785/wireless-not-working-on-toshiba-satellite-c55-a5281](http://askubuntu.com/questions/337785/wireless-not-working-on-toshiba-satellite-c55-a5281) but it requires recompiling after every linux-image update (not an option with the tech-illiterate user). Anyone know a good way to automate this, or an alternative fix?

---

### Post by wildmanne39 on 2015-06-09
Please use code tags - if you are using New Reply button - highlight text and use the # button in the text box header. 
 
If using Quick Reply then [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.

---

### Post by Halfling Rogue on 2015-06-09
Uh, which post, Wild Man? Looks like all of them use the code tags appropriately as far as I can see (aside from kadir).

---

### Post by wildmanne39 on 2015-06-09
Post 21, I already edited it.

---

