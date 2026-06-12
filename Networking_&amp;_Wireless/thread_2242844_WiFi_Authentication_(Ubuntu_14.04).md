---
title: "WiFi Authentication (Ubuntu 14.04)"
date: 2014-09-04
forum: Networking &amp; Wireless
---

### Post by TaiChiRabbit on 2014-09-04
Hi
I can no longer connect to my wifi from my dual boot Samsung Netbook, Ubuntu wired connection and booting under Windows the Wifi works fine. The access point SSID appears on the network manager, but when i try to connect it waits for a while, ask for the password and then fails to connect.  I've tried reboot the access point and deleting the SSID from the network manager, but still cannot connect.  Any ideas what I'm missing?  Thanks


Output from lsmod:
```

Module                  Size  Used by
nls_iso8859_1          12617  0 
usb_storage            48417  0 
cuse                   13213  3 
rfcomm                 53664  8 
bnep                   18895  2 
dm_crypt               22589  0 
binfmt_misc            13140  1 
nfsd                  247797  2 
auth_rpcgss            48979  1 nfsd
nfs_acl                12733  1 nfsd
nfs                   205212  0 
lockd                  78518  2 nfs,nfsd
sunrpc                242555  6 nfs,nfsd,auth_rpcgss,lockd,nfs_acl
fscache                56756  1 nfs
ipt_REJECT             12485  2 
xt_tcpudp              12756  10 
xt_conntrack           12664  3 
iptable_filter         12706  1 
iptable_mangle         12615  0 
iptable_nat            12867  0 
nf_conntrack_ipv4      14492  4 
nf_defrag_ipv4         12649  1 nf_conntrack_ipv4
nf_nat_ipv4            13095  1 iptable_nat
nf_nat                 20861  2 nf_nat_ipv4,iptable_nat
nf_conntrack           83685  5 nf_nat,nf_nat_ipv4,xt_conntrack,iptable_nat,nf_conntrack_ipv4
ip_tables              17987  3 iptable_filter,iptable_mangle,iptable_nat
x_tables               22067  6 ip_tables,xt_tcpudp,xt_conntrack,iptable_filter,ipt_REJECT,iptable_mangle
arc4                   12536  2 
samsung_laptop         14062  0 
uvcvideo               71309  0 
videobuf2_vmalloc      13048  1 uvcvideo
usb_serial_simple      13018  0 
videobuf2_memops       13170  1 videobuf2_vmalloc
snd_hda_codec_realtek    55163  1 
videobuf2_core         39258  1 uvcvideo
videodev              108503  2 uvcvideo,videobuf2_core
snd_hda_intel          42730  3 
usbserial              38902  1 usb_serial_simple
snd_hda_codec         164067  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13272  1 snd_hda_codec
snd_pcm                85501  2 snd_hda_codec,snd_hda_intel
coretemp               13195  0 
snd_page_alloc         14230  2 snd_pcm,snd_hda_intel
snd_seq_midi           13132  0 
snd_seq_midi_event     14475  1 snd_seq_midi
joydev                 17101  0 
snd_rawmidi            25135  1 snd_seq_midi
ath5k                 134977  0 
serio_raw              13230  0 
ath                    23922  1 ath5k
mac80211              546051  1 ath5k
btusb                  27580  0 
bluetooth             342208  22 bnep,btusb,rfcomm
snd_seq                55383  2 snd_seq_midi_event,snd_seq_midi
snd_seq_device         14137  3 snd_seq,snd_rawmidi,snd_seq_midi
lpc_ich                16864  0 
snd_timer              28584  2 snd_pcm,snd_seq
cfg80211              409394  3 ath,ath5k,mac80211
snd                    60939  16  snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_seq_midi
soundcore              12600  1 snd
mac_hid                13037  0 
parport_pc             31981  0 
ppdev                  17391  0 
lp                     13299  0 
parport                40836  3 lp,ppdev,parport_pc
i915                  705659  3 
psmouse                91329  0 
i2c_algo_bit           13197  1 i915
sky2                   52946  0 
drm_kms_helper         47182  1 i915
drm                   244037  4 i915,drm_kms_helper
video                  18903  2 i915,samsung_laptop[/QUOTE]

output from rkill
[QUOTE]0: hci0: Bluetooth
    Soft blocked: yes
    Hard blocked: no
1: samsung-wlan: Wireless LAN
    Soft blocked: no
    Hard blocked: no
2: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
```

out from lspci -nn
```
00:00.0 Host bridge [0600]: Intel Corporation Mobile 945GSE Express Memory Controller Hub [8086:27ac] (rev 03)
00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile  945GSE Express Integrated Graphics Controller [8086:27ae] (rev 03)
00:02.1 Display controller [0380]: Intel Corporation Mobile  945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller  [8086:27a6] (rev 03)
00:1b.0 Audio device [0403]: Intel Corporation NM10/ICH7 Family High Definition Audio Controller [8086:27d8] (rev 02)
00:1c.0 PCI bridge [0604]: Intel Corporation NM10/ICH7 Family PCI Express Port 1 [8086:27d0] (rev 02)
00:1c.2 PCI bridge [0604]: Intel Corporation NM10/ICH7 Family PCI Express Port 3 [8086:27d4] (rev 02)
00:1d.0 USB controller [0c03]: Intel Corporation NM10/ICH7 Family USB UHCI Controller #1 [8086:27c8] (rev 02)
00:1d.1 USB controller [0c03]: Intel Corporation NM10/ICH7 Family USB UHCI Controller #2 [8086:27c9] (rev 02)
00:1d.2 USB controller [0c03]: Intel Corporation NM10/ICH7 Family USB UHCI Controller #3 [8086:27ca] (rev 02)
00:1d.3 USB controller [0c03]: Intel Corporation NM10/ICH7 Family USB UHCI Controller #4 [8086:27cb] (rev 02)
00:1d.7 USB controller [0c03]: Intel Corporation NM10/ICH7 Family USB2 EHCI Controller [8086:27cc] (rev 02)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev e2)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge [8086:27b9] (rev 02)
00:1f.2 IDE interface [0101]: Intel Corporation 82801GBM/GHM (ICH7-M Family) SATA Controller [IDE mode] [8086:27c4] (rev 02)
00:1f.3 SMBus [0c05]: Intel Corporation NM10/ICH7 Family SMBus Controller [8086:27da] (rev 02)
02:00.0 Ethernet controller [0200]: Qualcomm Atheros AR242x / AR542x Wireless Network Adapter (PCI-Express) [168c:001c] (rev 01)
03:00.0 Ethernet controller [0200]: Marvell Technology Group Ltd. 88E8040 PCI-E Fast Ethernet Controller [11ab:4354] (rev 13)
```

output from sudo lshw -C network
```
  *-network
       description: Wireless interface
       product: AR242x / AR542x Wireless Network Adapter (PCI-Express)
       vendor: Qualcomm Atheros
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 01
       serial: 00:21:63:c4:a9:15
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath5k driverversion=3.13.0-35-generic firmware=N/A latency=0 link=no multicast=yes wireless=IEEE 802.11bg
       resources: irq:16 memory:f0100000-f010ffff
  *-network
       description: Ethernet interface
       product: 88E8040 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 13
       serial: 00:13:77:d2:d1:a2
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.30 duplex=full latency=0 link=no multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:42 memory:f0200000-f0203fff ioport:2000(size=256)
```

---

### Post by jeremy31 on 2014-09-04
How about the results from ```
iwlist scan
```

---

### Post by TaiChiRabbit on 2014-09-05
> **jeremy31 said:**
> How about the results from ```
iwlist scan
```

Output from iwlist scan

```
wlan0     Scan completed :
          Cell 01 - Address: 00:FE:F4:40:70:08
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=16/70  Signal level=-94 dBm  
                    Encryption key:on
                    ESSID:"BTHub3-HW9M"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000b9d001be9e
                    Extra: Last beacon: 22600ms ago
                    IE: Unknown: 000B4254487562332D4857394D
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030101
                    IE: Unknown: 2A0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32043048606C
                    IE: Unknown: 2D1AAC011BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1601001100000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F0101
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F20201018D0003A4000027A4000042435E0062322F00
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: Unknown: DDA70050F204104A000110104400010210570001001041000100103B00010310470010565AA94967C14C0EAA8FF349E6F5931110210002425410230017486F6D652048756220332E30204D756C7469204D6F646510240010425420486F6D652048756220332E3041104200122B3035383732302B313131333033343637311054000800060050F204000110110010425420486F6D652048756220332E3041100800020084103C000101
          Cell 02 - Address: 2C:B0:5D:74:9B:8A
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=9/70  Signal level=-101 dBm  
                    Encryption key:on
                    ESSID:"NETGEAR40"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 22600ms ago
                    IE: Unknown: 00094E4554474541523430
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030106
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1AFC181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1606000400000000000000000000000000000000000000
                    IE: Unknown: DD7D0050F204104A00011010440001021041000100103B000103104700106499B912FC8F69B156727955C53EF74E102100074E6574676561721023000944474E3232303076331024000944474E32323030763310420004313233341054000800060050F20400011011000944474E323230307633100800020084103C000101
                    IE: Unknown: DD090010180204F02C0000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 03 - Address: 7C:4C:A5:A7:01:45
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=21/70  Signal level=-89 dBm  
                    Encryption key:on
                    ESSID:"SKY89B43"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000101fdf95d
                    Extra: Last beacon: 22600ms ago
                    IE: Unknown: 0008534B593839423433
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0104
                    IE: Unknown: 2F0104
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1AEC181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D160B080400000000000000000000000000000000000000
                    IE: Unknown: DD800050F204104A0001101044000102103B00010310470010F7087B321E3A05F1F992AE71F5D658561021000842726F6164636F6D1023000842726F6164636F6D1024000631323334353610420004313233341054000800060050F20400011011000A42726F6164636F6D415010080002200C103C0001011049000600372A000120
                    IE: Unknown: DD090010180205F02C0000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 04 - Address: 00:18:4D:D2:07:79
                    Channel:13
                    Frequency:2.472 GHz (Channel 13)
                    Quality=26/70  Signal level=-84 dBm  
                    Encryption key:on
                    ESSID:"BKB102AP"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s
                    Bit Rates:9 Mb/s; 18 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000002a5c59fb1
                    Extra: Last beacon: 22600ms ago
                    IE: Unknown: 0008424B423130324150
                    IE: Unknown: 010882848B960C183048
                    IE: Unknown: 03010D
                    IE: Unknown: 0706474220010D14
                    IE: Unknown: 2A0100
                    IE: Unknown: 32041224606C
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 05 - Address: C0:3E:0F:22:7E:61
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=19/70  Signal level=-91 dBm  
                    Encryption key:on
                    ESSID:"SKYAAA42"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000f2b9ca45c
                    Extra: Last beacon: 22600ms ago
                    IE: Unknown: 0008534B594141413432
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 0B050000600000
                    IE: Unknown: 2D1AAC181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D160B080000000000000000000000000000000000000000
                    IE: Unknown: 7F03000008
                    IE: Unknown: DD800050F204104A0001101044000102103B0001031047001036F4821D259ACABD1B203E29BE072B891021000842726F6164636F6D1023000842726F6164636F6D1024000631323334353610420004313233341054000800060050F20400011011000A42726F6164636F6D415010080002200C103C0001011049000600372A000120
                    IE: Unknown: DD090010180200000C0000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 06 - Address: C8:CD:72:A3:F1:FB
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=10/70  Signal level=-100 dBm  
                    Encryption key:on
                    ESSID:"SKY3F1FA"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000002ed173cc9
                    Extra: Last beacon: 22600ms ago
                    IE: Unknown: 0008534B593346314641
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1A2C181BFF00000000000000000000000000000000000000000000
                    IE: Unknown: 3D160B001100000000000000000000000000000000000000
                    IE: Unknown: DD090010180205F02C0000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00


```

---

### Post by TaiChiRabbit on 2014-09-05
Attached the output from the wireless info script posted on the forum

---

### Post by jeremy31 on 2014-09-05
What access point are you trying to connect to?

---

### Post by TaiChiRabbit on 2014-09-05
Essid:"bkb102ap"

---

### Post by jeremy31 on 2014-09-05
Every thing looks ok except the signal strength from your AP could be better, but try this ```
sudo modprobe -r ath5k
``````
 sudo modprobe ath5k nohwcrypt=Y
```

---

### Post by TaiChiRabbit on 2014-09-06
Unfortunately still not working....
```

########## wireless info START ##########

Report from: 06 Sep 2014 10:25 BST +0100

Script from: 05 Sep 2014 22:42 UTC +0000

##### release #####

Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.1 LTS
Release:    14.04
Codename:    trusty

##### kernel #####

Linux 3.13.0-35-generic #62-Ubuntu SMP Fri Aug 15 01:58:01 UTC 2014 i686 i686 i686 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop #####

Ubuntu

##### lspci #####

02:00.0 Ethernet controller [0200]: Qualcomm Atheros AR242x / AR542x Wireless Network Adapter (PCI-Express) [168c:001c] (rev 01)
    Subsystem: Askey Computer Corp. Device [144f:7131]
    Kernel driver in use: ath5k

03:00.0 Ethernet controller [0200]: Marvell Technology Group Ltd. 88E8040 PCI-E Fast Ethernet Controller [11ab:4354] (rev 13)
    Subsystem: Samsung Electronics Co Ltd Device [144d:ca00]
    Kernel driver in use: sky2

##### lsusb #####

Bus 001 Device 004: ID 0ac8:c326 Z-Star Microelectronics Corp. Namuga 1.3M Webcam
Bus 001 Device 006: ID 058f:6387 Alcor Micro Corp. Flash Drive
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 0a5c:2101 Broadcom Corp. BCM2045 Bluetooth
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 0fcf:1009 Dynastream Innovations, Inc. 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

##### PCMCIA card info #####

##### rfkill #####

0: hci0: Bluetooth
    Soft blocked: yes
    Hard blocked: no
1: samsung-wlan: Wireless LAN
    Soft blocked: no
    Hard blocked: no
3: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

##### lsmod #####

ath5k                 134977  0 
ath                    23922  1 ath5k
mac80211              546051  1 ath5k
cfg80211              409394  3 ath,ath5k,mac80211

##### interfaces #####

auto lo
iface lo inet loopback

auto wlan0

##### ifconfig #####

eth0      Link encap:Ethernet  HWaddr <MAC addr eth0>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:18 

wlan0     Link encap:Ethernet  HWaddr <MAC addr wlan0>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

##### iwconfig #####

lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          

##### route #####

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface

##### resolv.conf #####

##### nm-tool #####

** (process:3031): WARNING **: Could not create object for /org/freedesktop/NetworkManager/Settings/22: uid 1000 has no permission to perform this operation

** (process:3031): WARNING **: Could not create object for /org/freedesktop/NetworkManager/Settings/21: uid 1000 has no permission to perform this operation

** (process:3031): WARNING **: handle_property_changed: failed to update property 'available-connections' of object type NMDeviceWifi.

** (process:3031): WARNING **: error: cannot retrieve connection: uid 1000 has no permission to perform this operation

** (process:3031): WARNING **: error: cannot retrieve connection: uid 1000 has no permission to perform this operation

** (process:3031): WARNING **: error: cannot retrieve connection: uid 1000 has no permission to perform this operation

** (process:3031): WARNING **: error: cannot retrieve connection: uid 1000 has no permission to perform this operation

** (process:3031): WARNING **: error: cannot retrieve connection: uid 1000 has no permission to perform this operation

** (process:3031): WARNING **: error: cannot retrieve connection: uid 1000 has no permission to perform this operation

** (process:3031): WARNING **: error: cannot retrieve connection: uid 1000 has no permission to perform this operation

** (process:3031): WARNING **: error: cannot retrieve connection: uid 1000 has no permission to perform this operation

NetworkManager Tool

State: disconnected

- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            ath5k
  State:             disconnected
  Default:           no
  HW Address:        <MAC addr wlan0>

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 
    BKB102AP:        Infra, <MAC addr BKB102AP>, Freq 2472 MHz, Rate 54 Mb/s, Strength 69 WPA2
    SKYCD70A:        Infra, <MAC addr SKYCD70A>, Freq 2412 MHz, Rate 54 Mb/s, Strength 37 WPA2
    BTHub4-52GR:     Infra, <MAC addr BTHub4-52GR>, Freq 2412 MHz, Rate 54 Mb/s, Strength 27 WPA WPA2
    BTHub3-TPKG:     Infra, <MAC addr BTHub3-TPKG>, Freq 2462 MHz, Rate 54 Mb/s, Strength 20 WPA WPA2
    BTWifi-with-FON: Infra, <MAC addr BTWifi-with-FON>, Freq 2412 MHz, Rate 54 Mb/s, Strength 25

- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            sky2
  State:             unavailable
  Default:           no
  HW Address:        <MAC addr eth0>

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off

##### NetworkManager.state #####

[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true

##### NetworkManager.conf #####

[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq

[ifupdown]
managed=false

##### iw reg get #####

country 00:
    (2402 - 2472 @ 40), (3, 20)
    (2457 - 2482 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (2474 - 2494 @ 20), (3, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
    (5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS

##### iwlist channels #####

lo        no frequency information.

eth0      no frequency information.

wlan0     13 channels in total; available frequencies :
          Channel 01 : 2.412 GHz
          Channel 02 : 2.417 GHz
          Channel 03 : 2.422 GHz
          Channel 04 : 2.427 GHz
          Channel 05 : 2.432 GHz
          Channel 06 : 2.437 GHz
          Channel 07 : 2.442 GHz
          Channel 08 : 2.447 GHz
          Channel 09 : 2.452 GHz
          Channel 10 : 2.457 GHz
          Channel 11 : 2.462 GHz
          Channel 12 : 2.467 GHz
          Channel 13 : 2.472 GHz

##### iwlist scan #####

Channel occupancy:

     3   WLAPs on   Frequency:2.412 GHz (Channel 1)
     2   WLAPs on   Frequency:2.462 GHz (Channel 11)
     1   WLAPs on   Frequency:2.472 GHz (Channel 13)

wlan0     Scan completed :
          Cell 01 - Address: <MAC addr SKYCD70A>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=35/70  Signal level=-75 dBm  
                    Encryption key:on
                    ESSID:"SKYCD70A"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000337fdc6972
                    Extra: Last beacon: 76ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC addr BTHub4-52GR>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=26/70  Signal level=-84 dBm  
                    Encryption key:on
                    ESSID:"BTHub4-52GR"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000224e1a91a18
                    Extra: Last beacon: 20836ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: <MAC addr BTWifi-with-FON>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=25/70  Signal level=-85 dBm  
                    Encryption key:off
                    ESSID:"BTWifi-with-FON"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000224e1a9249c
                    Extra: Last beacon: 19964ms ago
          Cell 04 - Address: <MAC addr BTHub3-TPKG>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=22/70  Signal level=-88 dBm  
                    Encryption key:on
                    ESSID:"BTHub3-TPKG"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000011df84d180
                    Extra: Last beacon: 20192ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 05 - Address: <MAC addr BKB102AP>
                    Channel:13
                    Frequency:2.472 GHz (Channel 13)
                    Quality=52/70  Signal level=-58 dBm  
                    Encryption key:on
                    ESSID:"BKB102AP"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s
                    Bit Rates:9 Mb/s; 18 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000003ca0e226e
                    Extra: Last beacon: 76ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 06 - Address: <MAC address>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=32/70  Signal level=-78 dBm  
                    Encryption key:on
                    ESSID:"SKY89B43"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/slo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000015ee350532
                    Extra: Last beacon: 76ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK

##### module infos #####

[ath5k]
filename:       /lib/modules/3.13.0-35-generic/kernel/drivers/net/wireless/ath/ath5k/ath5k.ko
license:        Dual BSD/GPL
description:    Support for 5xxx series of Atheros 802.11 wireless LAN cards.
author:         Nick Kossifidis
author:         Jiri Slaby
srcversion:     F36818A2F0BCB2B0CC9BB8C
depends:        mac80211,cfg80211,ath
intree:         Y
vermagic:       3.13.0-35-generic SMP mod_unload modversions 686 
signer:         Magrathea: Glacier signing key
sig_key:        A2:8D:B5:FD:6E:29:9C:CE:49:47:DA:CA:A6:6F:45:9D:B4:AC:CE:24
sig_hashalgo:   sha512
parm:           nohwcrypt:Disable hardware encryption. (bool)
parm:           fastchanswitch:Enable fast channel switching for AR2413/AR5413 radios. (bool)
parm:           no_hw_rfkill_switch:Ignore the GPIO RFKill switch state (bool)

[ath]
filename:       /lib/modules/3.13.0-35-generic/kernel/drivers/net/wireless/ath/ath.ko
license:        Dual BSD/GPL
description:    Shared library for Atheros wireless LAN cards.
author:         Atheros Communications
srcversion:     88A67C5359B02C5A710AFCF
depends:        cfg80211
intree:         Y
vermagic:       3.13.0-35-generic SMP mod_unload modversions 686 
signer:         Magrathea: Glacier signing key
sig_key:        A2:8D:B5:FD:6E:29:9C:CE:49:47:DA:CA:A6:6F:45:9D:B4:AC:CE:24
sig_hashalgo:   sha512

##### module parameters #####

[ath5k]
fastchanswitch: N
nohwcrypt: Y
no_hw_rfkill_switch: N

##### /etc/modules #####

lp

##### blacklists #####

[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci

[/etc/modprobe.d/blacklist-bcm43.conf]
blacklist b43
blacklist b43legacy
blacklist ssb
blacklist bcm43xx
blacklist brcm80211
blacklist brcmfmac
blacklist brcmsmac
blacklist bcma

[/etc/modprobe.d/blacklist.conf]
blacklist evbug
blacklist usbmouse
blacklist usbkbd
blacklist eepro100
blacklist de4x5
blacklist eth1394
blacklist snd_intel8x0m
blacklist snd_aw2
blacklist i2c_i801
blacklist prism54
blacklist bcm43xx
blacklist garmin_gps
blacklist asus_acpi
blacklist snd_pcsp
blacklist pcspkr
blacklist amd76x_edac

[/etc/modprobe.d/libpisock9.conf]
blacklist visor

[/etc/modprobe.d/osspd.conf]
blacklist snd-pcm-oss
blacklist snd-mixer-oss
blacklist snd-seq-oss

##### rc.local #####

rfkill block bluetooth
exit 0

##### udev rules #####

[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x11ab:0x4354 (sky2)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC addr eth0>", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# PCI device 0x168c:0x001c (ath5k)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC addr wlan0>", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

##### dmesg #####

[   34.086456] ath5k 0000:02:00.0: can't disable ASPM; OS doesn't have ASPM control
[   34.086740] ath5k 0000:02:00.0: registered as 'phy0'
[   35.759069] ath: EEPROM regdomain: 0x65
[   35.759079] ath: EEPROM indicates we should expect a direct regpair map
[   35.759088] ath: Country alpha2 being used: 00
[   35.759093] ath: Regpair used: 0x65
[   35.811885] ath5k: phy0: Atheros AR2425 chip found (MAC: 0xe2, PHY: 0x70)
[   48.981056] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready (repeated 2 times)
[  285.778746] wlan0: authenticate with <MAC addr BKB102AP>
[  285.790261] wlan0: send auth to <MAC addr BKB102AP> (try 1/3)
[  285.796283] wlan0: authenticated
[  285.796857] ath5k 0000:02:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[  285.796871] ath5k 0000:02:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[  285.800770] wlan0: associate with <MAC addr BKB102AP> (try 1/3)
[  285.904099] wlan0: associate with <MAC addr BKB102AP> (try 2/3)
[  286.008227] wlan0: associate with <MAC addr BKB102AP> (try 3/3)
[  286.112091] wlan0: association with <MAC addr BKB102AP> timed out
[  287.114067] wlan0: authenticate with <MAC addr BKB102AP>
[  287.114457] wlan0: send auth to <MAC addr BKB102AP> (try 1/3)
[  287.116046] wlan0: authenticated
[  287.116537] ath5k 0000:02:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[  287.116547] ath5k 0000:02:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[  287.122069] wlan0: associate with <MAC addr BKB102AP> (try 1/3)
[  287.224113] wlan0: associate with <MAC addr BKB102AP> (try 2/3)
[  287.328176] wlan0: associate with <MAC addr BKB102AP> (try 3/3)
[  287.432159] wlan0: association with <MAC addr BKB102AP> timed out
[  288.902027] wlan0: authenticate with <MAC addr BKB102AP>
[  288.902377] wlan0: send auth to <MAC addr BKB102AP> (try 1/3)
[  288.906666] wlan0: authenticated
[  288.907430] ath5k 0000:02:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[  288.907445] ath5k 0000:02:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[  288.908101] wlan0: associate with <MAC addr BKB102AP> (try 1/3)
[  289.012183] wlan0: associate with <MAC addr BKB102AP> (try 2/3)
[  289.116135] wlan0: associate with <MAC addr BKB102AP> (try 3/3)
[  289.220135] wlan0: association with <MAC addr BKB102AP> timed out
[  291.197180] wlan0: authenticate with <MAC addr BKB102AP>
[  291.197572] wlan0: send auth to <MAC addr BKB102AP> (try 1/3)
[  291.199175] wlan0: authenticated
[  291.201078] ath5k 0000:02:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[  291.201091] ath5k 0000:02:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[  291.204430] wlan0: associate with <MAC addr BKB102AP> (try 1/3)
[  291.308162] wlan0: associate with <MAC addr BKB102AP> (try 2/3)
[  291.412638] wlan0: associate with <MAC addr BKB102AP> (try 3/3)
[  291.516093] wlan0: association with <MAC addr BKB102AP> timed out
[  303.506829] wlan0: authenticate with <MAC addr BKB102AP>
[  303.507358] wlan0: send auth to <MAC addr BKB102AP> (try 1/3)
[  303.509838] wlan0: authenticated
[  303.511554] ath5k 0000:02:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[  303.511580] ath5k 0000:02:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[  303.512592] wlan0: associate with <MAC addr BKB102AP> (try 1/3)
[  303.616173] wlan0: associate with <MAC addr BKB102AP> (try 2/3)
[  303.720182] wlan0: associate with <MAC addr BKB102AP> (try 3/3)
[  303.824149] wlan0: association with <MAC addr BKB102AP> timed out
[ 1699.709705] ath5k 0000:02:00.0: can't disable ASPM; OS doesn't have ASPM control
[ 1699.710120] ath5k 0000:02:00.0: registered as 'phy0'
[ 1700.233722] ath: EEPROM regdomain: 0x65
[ 1700.233737] ath: EEPROM indicates we should expect a direct regpair map
[ 1700.233750] ath: Country alpha2 being used: 00
[ 1700.233758] ath: Regpair used: 0x65
[ 1700.237891] ath5k: phy0: Atheros AR2425 chip found (MAC: 0xe2, PHY: 0x70)
[ 1700.326754] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready (repeated 2 times)

########## wireless info END ############
```

---

### Post by varunendra on 2014-09-06
@TaiChiRabbit,

Could you please edit your above posts (all of the ones containing terminal outputs) to wrap the output parts within 'Code' tags? You are currently using 'Quote' tags which can't preserve its formatting, thus making it difficult to read and interpret.

Please follow the "Use Code Tags" link in my signature below to see how to use them.

And regarding the problem, please post the output of -
```
id
```
..in your next post. It would help us determining if it could be a permission problem like 'nm-tool' is suggesting.

---

### Post by TaiChiRabbit on 2014-09-07
Sorry for using the wrong tags and the annoying smilies it created.

id output:
```
uid=1000(fred) gid=1000(fred) groups=1000(fred),4(adm),20(dialout),24(cdrom),46(plugdev),108(lpadmin),123(admin),124(sambashare),1001(vi)
```

wirless-info.txt output:

```

########## wireless info START ##########

Report from: 06 Sep 2014 10:25 BST +0100

Script from: 05 Sep 2014 22:42 UTC +0000

##### release #####

Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.1 LTS
Release:    14.04
Codename:    trusty

##### kernel #####

Linux 3.13.0-35-generic #62-Ubuntu SMP Fri Aug 15 01:58:01 UTC 2014 i686 i686 i686 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop #####

Ubuntu

##### lspci #####

02:00.0 Ethernet controller [0200]: Qualcomm Atheros AR242x / AR542x Wireless Network Adapter (PCI-Express) [168c:001c] (rev 01)
    Subsystem: Askey Computer Corp. Device [144f:7131]
    Kernel driver in use: ath5k

03:00.0 Ethernet controller [0200]: Marvell Technology Group Ltd. 88E8040 PCI-E Fast Ethernet Controller [11ab:4354] (rev 13)
    Subsystem: Samsung Electronics Co Ltd Device [144d:ca00]
    Kernel driver in use: sky2

##### lsusb #####

Bus 001 Device 004: ID 0ac8:c326 Z-Star Microelectronics Corp. Namuga 1.3M Webcam
Bus 001 Device 006: ID 058f:6387 Alcor Micro Corp. Flash Drive
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 0a5c:2101 Broadcom Corp. BCM2045 Bluetooth
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 0fcf:1009 Dynastream Innovations, Inc. 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

##### PCMCIA card info #####

##### rfkill #####

0: hci0: Bluetooth
    Soft blocked: yes
    Hard blocked: no
1: samsung-wlan: Wireless LAN
    Soft blocked: no
    Hard blocked: no
3: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

##### lsmod #####

ath5k                 134977  0 
ath                    23922  1 ath5k
mac80211              546051  1 ath5k
cfg80211              409394  3 ath,ath5k,mac80211

##### interfaces #####

auto lo
iface lo inet loopback

auto wlan0

##### ifconfig #####

eth0      Link encap:Ethernet  HWaddr <MAC addr eth0>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:18 

wlan0     Link encap:Ethernet  HWaddr <MAC addr wlan0>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

##### iwconfig #####

lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          

##### route #####

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface

##### resolv.conf #####

##### nm-tool #####

** (process:3031): WARNING **: Could not create object for /org/freedesktop/NetworkManager/Settings/22: uid 1000 has no permission to perform this operation

** (process:3031): WARNING **: Could not create object for /org/freedesktop/NetworkManager/Settings/21: uid 1000 has no permission to perform this operation

** (process:3031): WARNING **: handle_property_changed: failed to update property 'available-connections' of object type NMDeviceWifi.

** (process:3031): WARNING **: error: cannot retrieve connection: uid 1000 has no permission to perform this operation

** (process:3031): WARNING **: error: cannot retrieve connection: uid 1000 has no permission to perform this operation

** (process:3031): WARNING **: error: cannot retrieve connection: uid 1000 has no permission to perform this operation

** (process:3031): WARNING **: error: cannot retrieve connection: uid 1000 has no permission to perform this operation

** (process:3031): WARNING **: error: cannot retrieve connection: uid 1000 has no permission to perform this operation

** (process:3031): WARNING **: error: cannot retrieve connection: uid 1000 has no permission to perform this operation

** (process:3031): WARNING **: error: cannot retrieve connection: uid 1000 has no permission to perform this operation

** (process:3031): WARNING **: error: cannot retrieve connection: uid 1000 has no permission to perform this operation

NetworkManager Tool

State: disconnected

- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            ath5k
  State:             disconnected
  Default:           no
  HW Address:        <MAC addr wlan0>

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 
    BKB102AP:        Infra, <MAC addr BKB102AP>, Freq 2472 MHz, Rate 54 Mb/s, Strength 69 WPA2
    SKYCD70A:        Infra, <MAC addr SKYCD70A>, Freq 2412 MHz, Rate 54 Mb/s, Strength 37 WPA2
    BTHub4-52GR:     Infra, <MAC addr BTHub4-52GR>, Freq 2412 MHz, Rate 54 Mb/s, Strength 27 WPA WPA2
    BTHub3-TPKG:     Infra, <MAC addr BTHub3-TPKG>, Freq 2462 MHz, Rate 54 Mb/s, Strength 20 WPA WPA2
    BTWifi-with-FON: Infra, <MAC addr BTWifi-with-FON>, Freq 2412 MHz, Rate 54 Mb/s, Strength 25

- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            sky2
  State:             unavailable
  Default:           no
  HW Address:        <MAC addr eth0>

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off

##### NetworkManager.state #####

[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true

##### NetworkManager.conf #####

[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq

[ifupdown]
managed=false

##### iw reg get #####

country 00:
    (2402 - 2472 @ 40), (3, 20)
    (2457 - 2482 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (2474 - 2494 @ 20), (3, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
    (5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS

##### iwlist channels #####

lo        no frequency information.

eth0      no frequency information.

wlan0     13 channels in total; available frequencies :
          Channel 01 : 2.412 GHz
          Channel 02 : 2.417 GHz
          Channel 03 : 2.422 GHz
          Channel 04 : 2.427 GHz
          Channel 05 : 2.432 GHz
          Channel 06 : 2.437 GHz
          Channel 07 : 2.442 GHz
          Channel 08 : 2.447 GHz
          Channel 09 : 2.452 GHz
          Channel 10 : 2.457 GHz
          Channel 11 : 2.462 GHz
          Channel 12 : 2.467 GHz
          Channel 13 : 2.472 GHz

##### iwlist scan #####

Channel occupancy:

     3   WLAPs on   Frequency:2.412 GHz (Channel 1)
     2   WLAPs on   Frequency:2.462 GHz (Channel 11)
     1   WLAPs on   Frequency:2.472 GHz (Channel 13)

wlan0     Scan completed :
          Cell 01 - Address: <MAC addr SKYCD70A>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=35/70  Signal level=-75 dBm  
                    Encryption key:on
                    ESSID:"SKYCD70A"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000337fdc6972
                    Extra: Last beacon: 76ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC addr BTHub4-52GR>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=26/70  Signal level=-84 dBm  
                    Encryption key:on
                    ESSID:"BTHub4-52GR"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000224e1a91a18
                    Extra: Last beacon: 20836ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: <MAC addr BTWifi-with-FON>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=25/70  Signal level=-85 dBm  
                    Encryption key:off
                    ESSID:"BTWifi-with-FON"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000224e1a9249c
                    Extra: Last beacon: 19964ms ago
          Cell 04 - Address: <MAC addr BTHub3-TPKG>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=22/70  Signal level=-88 dBm  
                    Encryption key:on
                    ESSID:"BTHub3-TPKG"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000011df84d180
                    Extra: Last beacon: 20192ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 05 - Address: <MAC addr BKB102AP>
                    Channel:13
                    Frequency:2.472 GHz (Channel 13)
                    Quality=52/70  Signal level=-58 dBm  
                    Encryption key:on
                    ESSID:"BKB102AP"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s
                    Bit Rates:9 Mb/s; 18 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000003ca0e226e
                    Extra: Last beacon: 76ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 06 - Address: <MAC address>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=32/70  Signal level=-78 dBm  
                    Encryption key:on
                    ESSID:"SKY89B43"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/slo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000015ee350532
                    Extra: Last beacon: 76ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK

##### module infos #####

[ath5k]
filename:       /lib/modules/3.13.0-35-generic/kernel/drivers/net/wireless/ath/ath5k/ath5k.ko
license:        Dual BSD/GPL
description:    Support for 5xxx series of Atheros 802.11 wireless LAN cards.
author:         Nick Kossifidis
author:         Jiri Slaby
srcversion:     F36818A2F0BCB2B0CC9BB8C
depends:        mac80211,cfg80211,ath
intree:         Y
vermagic:       3.13.0-35-generic SMP mod_unload modversions 686 
signer:         Magrathea: Glacier signing key
sig_key:        A2:8D:B5:FD:6E:29:9C:CE:49:47:DA:CA:A6:6F:45:9D:B4:AC:CE:24
sig_hashalgo:   sha512
parm:           nohwcrypt:Disable hardware encryption. (bool)
parm:           fastchanswitch:Enable fast channel switching for AR2413/AR5413 radios. (bool)
parm:           no_hw_rfkill_switch:Ignore the GPIO RFKill switch state (bool)

[ath]
filename:       /lib/modules/3.13.0-35-generic/kernel/drivers/net/wireless/ath/ath.ko
license:        Dual BSD/GPL
description:    Shared library for Atheros wireless LAN cards.
author:         Atheros Communications
srcversion:     88A67C5359B02C5A710AFCF
depends:        cfg80211
intree:         Y
vermagic:       3.13.0-35-generic SMP mod_unload modversions 686 
signer:         Magrathea: Glacier signing key
sig_key:        A2:8D:B5:FD:6E:29:9C:CE:49:47:DA:CA:A6:6F:45:9D:B4:AC:CE:24
sig_hashalgo:   sha512

##### module parameters #####

[ath5k]
fastchanswitch: N
nohwcrypt: Y
no_hw_rfkill_switch: N

##### /etc/modules #####

lp

##### blacklists #####

[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci

[/etc/modprobe.d/blacklist-bcm43.conf]
blacklist b43
blacklist b43legacy
blacklist ssb
blacklist bcm43xx
blacklist brcm80211
blacklist brcmfmac
blacklist brcmsmac
blacklist bcma

[/etc/modprobe.d/blacklist.conf]
blacklist evbug
blacklist usbmouse
blacklist usbkbd
blacklist eepro100
blacklist de4x5
blacklist eth1394
blacklist snd_intel8x0m
blacklist snd_aw2
blacklist i2c_i801
blacklist prism54
blacklist bcm43xx
blacklist garmin_gps
blacklist asus_acpi
blacklist snd_pcsp
blacklist pcspkr
blacklist amd76x_edac

[/etc/modprobe.d/libpisock9.conf]
blacklist visor

[/etc/modprobe.d/osspd.conf]
blacklist snd-pcm-oss
blacklist snd-mixer-oss
blacklist snd-seq-oss

##### rc.local #####

rfkill block bluetooth
exit 0

##### udev rules #####

[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x11ab:0x4354 (sky2)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC addr eth0>", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# PCI device 0x168c:0x001c (ath5k)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC addr wlan0>", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

##### dmesg #####

[   34.086456] ath5k 0000:02:00.0: can't disable ASPM; OS doesn't have ASPM control
[   34.086740] ath5k 0000:02:00.0: registered as 'phy0'
[   35.759069] ath: EEPROM regdomain: 0x65
[   35.759079] ath: EEPROM indicates we should expect a direct regpair map
[   35.759088] ath: Country alpha2 being used: 00
[   35.759093] ath: Regpair used: 0x65
[   35.811885] ath5k: phy0: Atheros AR2425 chip found (MAC: 0xe2, PHY: 0x70)
[   48.981056] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready (repeated 2 times)
[  285.778746] wlan0: authenticate with <MAC addr BKB102AP>
[  285.790261] wlan0: send auth to <MAC addr BKB102AP> (try 1/3)
[  285.796283] wlan0: authenticated
[  285.796857] ath5k 0000:02:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[  285.796871] ath5k 0000:02:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[  285.800770] wlan0: associate with <MAC addr BKB102AP> (try 1/3)
[  285.904099] wlan0: associate with <MAC addr BKB102AP> (try 2/3)
[  286.008227] wlan0: associate with <MAC addr BKB102AP> (try 3/3)
[  286.112091] wlan0: association with <MAC addr BKB102AP> timed out
[  287.114067] wlan0: authenticate with <MAC addr BKB102AP>
[  287.114457] wlan0: send auth to <MAC addr BKB102AP> (try 1/3)
[  287.116046] wlan0: authenticated
[  287.116537] ath5k 0000:02:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[  287.116547] ath5k 0000:02:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[  287.122069] wlan0: associate with <MAC addr BKB102AP> (try 1/3)
[  287.224113] wlan0: associate with <MAC addr BKB102AP> (try 2/3)
[  287.328176] wlan0: associate with <MAC addr BKB102AP> (try 3/3)
[  287.432159] wlan0: association with <MAC addr BKB102AP> timed out
[  288.902027] wlan0: authenticate with <MAC addr BKB102AP>
[  288.902377] wlan0: send auth to <MAC addr BKB102AP> (try 1/3)
[  288.906666] wlan0: authenticated
[  288.907430] ath5k 0000:02:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[  288.907445] ath5k 0000:02:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[  288.908101] wlan0: associate with <MAC addr BKB102AP> (try 1/3)
[  289.012183] wlan0: associate with <MAC addr BKB102AP> (try 2/3)
[  289.116135] wlan0: associate with <MAC addr BKB102AP> (try 3/3)
[  289.220135] wlan0: association with <MAC addr BKB102AP> timed out
[  291.197180] wlan0: authenticate with <MAC addr BKB102AP>
[  291.197572] wlan0: send auth to <MAC addr BKB102AP> (try 1/3)
[  291.199175] wlan0: authenticated
[  291.201078] ath5k 0000:02:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[  291.201091] ath5k 0000:02:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[  291.204430] wlan0: associate with <MAC addr BKB102AP> (try 1/3)
[  291.308162] wlan0: associate with <MAC addr BKB102AP> (try 2/3)
[  291.412638] wlan0: associate with <MAC addr BKB102AP> (try 3/3)
[  291.516093] wlan0: association with <MAC addr BKB102AP> timed out
[  303.506829] wlan0: authenticate with <MAC addr BKB102AP>
[  303.507358] wlan0: send auth to <MAC addr BKB102AP> (try 1/3)
[  303.509838] wlan0: authenticated
[  303.511554] ath5k 0000:02:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[  303.511580] ath5k 0000:02:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[  303.512592] wlan0: associate with <MAC addr BKB102AP> (try 1/3)
[  303.616173] wlan0: associate with <MAC addr BKB102AP> (try 2/3)
[  303.720182] wlan0: associate with <MAC addr BKB102AP> (try 3/3)
[  303.824149] wlan0: association with <MAC addr BKB102AP> timed out
[ 1699.709705] ath5k 0000:02:00.0: can't disable ASPM; OS doesn't have ASPM control
[ 1699.710120] ath5k 0000:02:00.0: registered as 'phy0'
[ 1700.233722] ath: EEPROM regdomain: 0x65
[ 1700.233737] ath: EEPROM indicates we should expect a direct regpair map
[ 1700.233750] ath: Country alpha2 being used: 00
[ 1700.233758] ath: Regpair used: 0x65
[ 1700.237891] ath5k: phy0: Atheros AR2425 chip found (MAC: 0xe2, PHY: 0x70)
[ 1700.326754] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready (repeated 2 times)

########## wireless info END ############
```

---

### Post by varunendra on 2014-09-07
No problem about the wrong tags, even some old users don't get it right until told how. :)

But now that you know 'how', please edit your previous posts as well, to change [noparse]>  and  to ```
 and 
```.[/noparse]

About the problem, this is strange -
> **TaiChiRabbit said:**
> id output:
```
uid=1000(fred) gid=1000(fred) groups=1000(fred),4(adm),20(dialout),24(cdrom),46(plugdev),108(lpadmin),123(admin),124(sambashare),1001(vi)
```

Are you sure the above is the entire output and you didn't miss out part of it?

I was suspecting only 'dip' usergroup to be missing, but if the above is the full output, even 'sudo' is missing too! I would think that you shouldn't be able to use 'sudo' if you are not a member of that group.

So.. can you successfully run commands with 'sudo'? For example -
```
sudo iwlist scan
```
(from script report it seems you can)

Please check the output of "id" command again, and if it is indeed same as above (that is, no 'sudo' or 'dip' in the output), please do the following (if you can successfully run commands with sudo) -
```
sudo adduser fred sudo
sudo adduser fred dip
```
Then check the output of "id" command again. Do they appear in the output now? If yes, can you authenticate with wifi now? Reboot if required.

However, if you can't run commands with sudo, we may have to use 'pkexec' to add you to the '/etc/sudoers' file first.

---

### Post by TaiChiRabbit on 2014-09-07
Hi

Id output now:

```
uid=1000(fred) gid=1000(fred) groups=1000(fred),4(adm),20(dialout),24(cdrom),27(sudo),30(dip),46(plugdev),108(lpadmin),123(admin),124(sambashare),1001(vi)
```


wireless script output:

```

########## wireless info START ##########

Report from: 07 Sep 2014 11:43 BST +0100

Script from: 05 Sep 2014 22:42 UTC +0000

##### release #####

Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.1 LTS
Release:    14.04
Codename:    trusty

##### kernel #####

Linux 3.13.0-35-generic #62-Ubuntu SMP Fri Aug 15 01:58:01 UTC 2014 i686 i686 i686 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop #####

Ubuntu

##### lspci #####

02:00.0 Ethernet controller [0200]: Qualcomm Atheros AR242x / AR542x Wireless Network Adapter (PCI-Express) [168c:001c] (rev 01)
    Subsystem: Askey Computer Corp. Device [144f:7131]
    Kernel driver in use: ath5k

03:00.0 Ethernet controller [0200]: Marvell Technology Group Ltd. 88E8040 PCI-E Fast Ethernet Controller [11ab:4354] (rev 13)
    Subsystem: Samsung Electronics Co Ltd Device [144d:ca00]
    Kernel driver in use: sky2

##### lsusb #####

Bus 001 Device 004: ID 0ac8:c326 Z-Star Microelectronics Corp. Namuga 1.3M Webcam
Bus 001 Device 005: ID 058f:6387 Alcor Micro Corp. Flash Drive
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 0a5c:2101 Broadcom Corp. BCM2045 Bluetooth
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 0fcf:1009 Dynastream Innovations, Inc. 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

##### PCMCIA card info #####

##### rfkill #####

0: hci0: Bluetooth
    Soft blocked: yes
    Hard blocked: no
1: samsung-wlan: Wireless LAN
    Soft blocked: no
    Hard blocked: no
2: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

##### lsmod #####

ath5k                 134977  0 
ath                    23922  1 ath5k
mac80211              546051  1 ath5k
cfg80211              409394  3 ath,ath5k,mac80211

##### interfaces #####

auto lo
iface lo inet loopback

auto wlan0

##### ifconfig #####

eth0      Link encap:Ethernet  HWaddr <MAC addr eth0>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:18 

wlan0     Link encap:Ethernet  HWaddr <MAC addr wlan0>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

##### iwconfig #####

lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          

##### route #####

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface

##### resolv.conf #####

##### nm-tool #####

** (process:2685): WARNING **: Could not create object for /org/freedesktop/NetworkManager/Settings/21: uid 1000 has no permission to perform this operation

** (process:2685): WARNING **: Could not create object for /org/freedesktop/NetworkManager/Settings/13: uid 1000 has no permission to perform this operation

** (process:2685): WARNING **: Could not create object for /org/freedesktop/NetworkManager/Settings/23: uid 1000 has no permission to perform this operation

** (process:2685): WARNING **: handle_property_changed: failed to update property 'available-connections' of object type NMDeviceWifi.

** (process:2685): WARNING **: error: cannot retrieve connection: uid 1000 has no permission to perform this operation

** (process:2685): WARNING **: error: cannot retrieve connection: uid 1000 has no permission to perform this operation

** (process:2685): WARNING **: error: cannot retrieve connection: uid 1000 has no permission to perform this operation

** (process:2685): WARNING **: error: cannot retrieve connection: uid 1000 has no permission to perform this operation

** (process:2685): WARNING **: error: cannot retrieve connection: uid 1000 has no permission to perform this operation

** (process:2685): WARNING **: error: cannot retrieve connection: uid 1000 has no permission to perform this operation

** (process:2685): WARNING **: error: cannot retrieve connection: uid 1000 has no permission to perform this operation

** (process:2685): WARNING **: error: cannot retrieve connection: uid 1000 has no permission to perform this operation

NetworkManager Tool

State: disconnected

- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            sky2
  State:             unavailable
  Default:           no
  HW Address:        <MAC addr eth0>

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off

- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            ath5k
  State:             disconnected
  Default:           no
  HW Address:        <MAC addr wlan0>

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 
    SKYCD70A:        Infra, <MAC addr SKYCD70A>, Freq 2412 MHz, Rate 54 Mb/s, Strength 42 WPA2
    SKY89B43:        Infra, <MAC addr SKY89B43>, Freq 2462 MHz, Rate 54 Mb/s, Strength 22 WPA2
    HELEN-PC_Network:Infra, <MAC addr HELEN-PC_Network>, Freq 2417 MHz, Rate 54 Mb/s, Strength 17 WPA2
    TNCAP3EF2F9:     Infra, <MAC addr TNCAP3EF2F9>, Freq 2437 MHz, Rate 54 Mb/s, Strength 10 WPA2
    NTGR_eks1vae376ff: Infra, <MAC addr NTGR_eks1vae376ff>, Freq 2437 MHz, Rate 54 Mb/s, Strength 10 WPA2
    14:              Infra, <MAC addr 14>, Freq 2462 MHz, Rate 54 Mb/s, Strength 25 WPA2
    BTWifi-X:        Infra, <MAC addr BTWifi-X>, Freq 2412 MHz, Rate 54 Mb/s, Strength 15 WPA WPA2 Enterprise
    NETGEAR40:       Infra, <MAC addr NETGEAR40>, Freq 2412 MHz, Rate 54 Mb/s, Strength 15 WPA2
    BTWifi-X:        Infra, <MAC addr BTWifi-X>, Freq 2462 MHz, Rate 54 Mb/s, Strength 5 WPA WPA2 Enterprise
    BTWifi-with-FON: Infra, <MAC addr BTWifi-with-FON>, Freq 2437 MHz, Rate 54 Mb/s, Strength 17
    BTWifi-X:        Infra, <MAC addr BTWifi-X>, Freq 2437 MHz, Rate 54 Mb/s, Strength 10 WPA WPA2 Enterprise
    BTHub3-HW9M:     Infra, <MAC addr BTHub3-HW9M>, Freq 2412 MHz, Rate 54 Mb/s, Strength 15 WPA WPA2
    BTHub3-ZXHK:     Infra, <MAC addr BTHub3-ZXHK>, Freq 2437 MHz, Rate 54 Mb/s, Strength 14 WPA WPA2
    BKB102AP:        Infra, <MAC addr BKB102AP>, Freq 2472 MHz, Rate 54 Mb/s, Strength 82 WPA2
    thor:            Infra, <MAC addr thor>, Freq 2437 MHz, Rate 54 Mb/s, Strength 10 WPA2
    BTWifi-with-FON: Infra, <MAC addr BTWifi-with-FON>, Freq 2412 MHz, Rate 54 Mb/s, Strength 14
    BTWifi-with-FON: Infra, <MAC addr BTWifi-with-FON>, Freq 2462 MHz, Rate 54 Mb/s, Strength 4

##### NetworkManager.state #####

[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true

##### NetworkManager.conf #####

[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq

[ifupdown]
managed=false

##### iw reg get #####

country 00:
    (2402 - 2472 @ 40), (3, 20)
    (2457 - 2482 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (2474 - 2494 @ 20), (3, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
    (5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS

##### iwlist channels #####

lo        no frequency information.

eth0      no frequency information.

wlan0     13 channels in total; available frequencies :
          Channel 01 : 2.412 GHz
          Channel 02 : 2.417 GHz
          Channel 03 : 2.422 GHz
          Channel 04 : 2.427 GHz
          Channel 05 : 2.432 GHz
          Channel 06 : 2.437 GHz
          Channel 07 : 2.442 GHz
          Channel 08 : 2.447 GHz
          Channel 09 : 2.452 GHz
          Channel 10 : 2.457 GHz
          Channel 11 : 2.462 GHz
          Channel 12 : 2.467 GHz
          Channel 13 : 2.472 GHz

##### iwlist scan #####

Channel occupancy:

     3   WLAPs on   Frequency:2.412 GHz (Channel 1)
     1   WLAPs on   Frequency:2.417 GHz (Channel 2)
     1   WLAPs on   Frequency:2.437 GHz (Channel 6)
     3   WLAPs on   Frequency:2.462 GHz (Channel 11)
     1   WLAPs on   Frequency:2.472 GHz (Channel 13)

wlan0     Scan completed :
          Cell 01 - Address: <MAC addr HELEN-PC_Network>
                    Channel:2
                    Frequency:2.417 GHz (Channel 2)
                    Quality=20/70  Signal level=-90 dBm  
                    Encryption key:on
                    ESSID:"HELEN-PC_Network"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000ca28ccab0
                    Extra: Last beacon: 20ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC addr SKYCD70A>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=23/70  Signal level=-87 dBm  
                    Encryption key:on
                    ESSID:"SKYCD70A"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000b046efa6c
                    Extra: Last beacon: 17184ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: <MAC addr 14>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=26/70  Signal level=-84 dBm  
                    Encryption key:on
                    ESSID:"14"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000000a37c6b59
                    Extra: Last beacon: 20ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 04 - Address: <MAC addr SKY89B43>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=21/70  Signal level=-89 dBm  
                    Encryption key:on
                    ESSID:"SKY89B43"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000be6868ffc
                    Extra: Last beacon: 20ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 05 - Address: <MAC addr BTWifi-with-FON>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=21/70  Signal level=-89 dBm  
                    Encryption key:off
                    ESSID:"BTWifi-with-FON"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000e1ea0f169
                    Extra: Last beacon: 828ms ago
          Cell 06 - Address: <MAC addr BKB102AP>
                    Channel:13
                    Frequency:2.472 GHz (Channel 13)
                    Quality=56/70  Signal level=-54 dBm  
                    Encryption key:on
                    ESSID:"BKB102AP"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s
                    Bit Rates:9 Mb/s; 18 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000076cac1069
                    Extra: Last beacon: 20ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 07 - Address: <MAC addr BTWifi-X>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=14/70  Signal level=-96 dBm  
                    Encryption key:on
                    ESSID:"BTWifi-X"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000e1d9ad180
                    Extra: Last beacon: 18008ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : 802.1x
                       Preauthentication Supported
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : 802.1x
          Cell 08 - Address: <MAC addr BTWifi-X>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=17/70  Signal level=-93 dBm  
                    Encryption key:on
                    ESSID:"BTWifi-X"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000009ddcc33180
                    Extra: Last beacon: 532ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : 802.1x
                       Preauthentication Supported
               lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

     IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : 802.1x
          Cell 09 - Address: <MAC address>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=13/70  Signal level=-97 dBm  
                    Encryption key:on
                    ESSID:"BTHub3-TPKG"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000271547fe69
                    Extra: Last beacon: 20ms ago

##### module infos #####

[ath5k]
filename:       /lib/modules/3.13.0-35-generic/kernel/drivers/net/wireless/ath/ath5k/ath5k.ko
license:        Dual BSD/GPL
description:    Support for 5xxx series of Atheros 802.11 wireless LAN cards.
author:         Nick Kossifidis
author:         Jiri Slaby
srcversion:     F36818A2F0BCB2B0CC9BB8C
depends:        mac80211,cfg80211,ath
intree:         Y
vermagic:       3.13.0-35-generic SMP mod_unload modversions 686 
signer:         Magrathea: Glacier signing key
sig_key:        A2:8D:B5:FD:6E:29:9C:CE:49:47:DA:CA:A6:6F:45:9D:B4:AC:CE:24
sig_hashalgo:   sha512
parm:           nohwcrypt:Disable hardware encryption. (bool)
parm:           fastchanswitch:Enable fast channel switching for AR2413/AR5413 radios. (bool)
parm:           no_hw_rfkill_switch:Ignore the GPIO RFKill switch state (bool)

[ath]
filename:       /lib/modules/3.13.0-35-generic/kernel/drivers/net/wireless/ath/ath.ko
license:        Dual BSD/GPL
description:    Shared library for Atheros wireless LAN cards.
author:         Atheros Communications
srcversion:     88A67C5359B02C5A710AFCF
depends:        cfg80211
intree:         Y
vermagic:       3.13.0-35-generic SMP mod_unload modversions 686 
signer:         Magrathea: Glacier signing key
sig_key:        A2:8D:B5:FD:6E:29:9C:CE:49:47:DA:CA:A6:6F:45:9D:B4:AC:CE:24
sig_hashalgo:   sha512

##### module parameters #####

[ath5k]
fastchanswitch: N
nohwcrypt: N
no_hw_rfkill_switch: N

##### /etc/modules #####

lp

##### blacklists #####

[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci

[/etc/modprobe.d/blacklist-bcm43.conf]
blacklist b43
blacklist b43legacy
blacklist ssb
blacklist bcm43xx
blacklist brcm80211
blacklist brcmfmac
blacklist brcmsmac
blacklist bcma

[/etc/modprobe.d/blacklist.conf]
blacklist evbug
blacklist usbmouse
blacklist usbkbd
blacklist eepro100
blacklist de4x5
blacklist eth1394
blacklist snd_intel8x0m
blacklist snd_aw2
blacklist i2c_i801
blacklist prism54
blacklist bcm43xx
blacklist garmin_gps
blacklist asus_acpi
blacklist snd_pcsp
blacklist pcspkr
blacklist amd76x_edac

[/etc/modprobe.d/libpisock9.conf]
blacklist visor

[/etc/modprobe.d/osspd.conf]
blacklist snd-pcm-oss
blacklist snd-mixer-oss
blacklist snd-seq-oss

##### rc.local #####

rfkill block bluetooth
exit 0

##### udev rules #####

[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x11ab:0x4354 (sky2)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC addr eth0>", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# PCI device 0x168c:0x001c (ath5k)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC addr wlan0>", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

##### dmesg #####

[   34.074848] ath5k 0000:02:00.0: can't disable ASPM; OS doesn't have ASPM control
[   34.075139] ath5k 0000:02:00.0: registered as 'phy0'
[   35.842485] ath: EEPROM regdomain: 0x65
[   35.842495] ath: EEPROM indicates we should expect a direct regpair map
[   35.842504] ath: Country alpha2 being used: 00
[   35.842510] ath: Regpair used: 0x65
[   36.061437] ath5k: phy0: Atheros AR2425 chip found (MAC: 0xe2, PHY: 0x70)
[   48.888226] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready (repeated 2 times)
[  120.377705] wlan0: authenticate with <MAC addr BKB102AP>
[  120.388113] wlan0: send auth to <MAC addr BKB102AP> (try 1/3)
[  120.390239] wlan0: authenticated
[  120.390769] ath5k 0000:02:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[  120.390783] ath5k 0000:02:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[  120.392478] wlan0: associate with <MAC addr BKB102AP> (try 1/3)
[  120.500086] wlan0: associate with <MAC addr BKB102AP> (try 2/3)
[  120.604174] wlan0: associate with <MAC addr BKB102AP> (try 3/3)
[  120.708107] wlan0: association with <MAC addr BKB102AP> timed out
[  121.699637] wlan0: authenticate with <MAC addr BKB102AP>
[  121.700026] wlan0: send auth to <MAC addr BKB102AP> (try 1/3)
[  121.704081] wlan0: authenticated
[  121.704618] ath5k 0000:02:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[  121.704634] ath5k 0000:02:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[  121.708479] wlan0: associate with <MAC addr BKB102AP> (try 1/3)
[  121.812194] wlan0: associate with <MAC addr BKB102AP> (try 2/3)
[  121.916960] wlan0: associate with <MAC addr BKB102AP> (try 3/3)
[  122.020158] wlan0: association with <MAC addr BKB102AP> timed out
[  123.398497] wlan0: authenticate with <MAC addr BKB102AP>
[  123.398963] wlan0: send auth to <MAC addr BKB102AP> (try 1/3)
[  123.400617] wlan0: authenticated
[  123.401402] ath5k 0000:02:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[  123.401426] ath5k 0000:02:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[  123.404486] wlan0: associate with <MAC addr BKB102AP> (try 1/3)
[  123.508140] wlan0: associate with <MAC addr BKB102AP> (try 2/3)
[  123.612237] wlan0: associate with <MAC addr BKB102AP> (try 3/3)
[  123.716159] wlan0: association with <MAC addr BKB102AP> timed out
[  125.595745] wlan0: authenticate with <MAC addr BKB102AP>
[  125.596951] wlan0: send auth to <MAC addr BKB102AP> (try 1/3)
[  125.598402] wlan0: authenticated
[  125.599146] ath5k 0000:02:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[  125.599161] ath5k 0000:02:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[  125.600422] wlan0: associate with <MAC addr BKB102AP> (try 1/3)
[  125.704162] wlan0: associate with <MAC addr BKB102AP> (try 2/3)
[  125.808084] wlan0: associate with <MAC addr BKB102AP> (try 3/3)
[  125.912110] wlan0: association with <MAC addr BKB102AP> timed out
[  137.658151] wlan0: authenticate with <MAC addr BKB102AP>
[  137.658507] wlan0: send auth to <MAC addr BKB102AP> (try 1/3)
[  137.659982] wlan0: authenticated
[  137.661440] ath5k 0000:02:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[  137.661467] ath5k 0000:02:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[  137.664831] wlan0: associate with <MAC addr BKB102AP> (try 1/3)
[  137.768177] wlan0: associate with <MAC addr BKB102AP> (try 2/3)
[  137.872143] wlan0: associate with <MAC addr BKB102AP> (try 3/3)
[  137.976144] wlan0: association with <MAC addr BKB102AP> timed out
[  154.693755] wlan0: authenticate with <MAC addr BKB102AP>
[  154.694119] wlan0: send auth to <MAC addr BKB102AP> (try 1/3)
[  154.695548] wlan0: authenticated
[  154.696070] ath5k 0000:02:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[  154.696083] ath5k 0000:02:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[  154.700134] wlan0: associate with <MAC addr BKB102AP> (try 1/3)
[  154.804164] wlan0: associate with <MAC addr BKB102AP> (try 2/3)
[  154.908763] wlan0: associate with <MAC addr BKB102AP> (try 3/3)
[  155.012074] wlan0: association with <MAC addr BKB102AP> timed out
[  165.896558] wlan0: authenticate with <MAC addr BKB102AP>
[  165.896952] wlan0: send auth to <MAC addr BKB102AP> (try 1/3)
[  165.899936] wlan0: authenticated
[  165.901157] ath5k 0000:02:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[  165.901172] ath5k 0000:02:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[  165.904123] wlan0: associate with <MAC addr BKB102AP> (try 1/3)
[  166.008122] wlan0: associate with <MAC addr BKB102AP> (try 2/3)
[  166.112104] wlan0: associate with <MAC addr BKB102AP> (try 3/3)
[  166.216121] wlan0: association with <MAC addr BKB102AP> timed out
[  207.857681] wlan0: authenticate with <MAC addr BKB102AP>
[  207.858045] wlan0: send auth to <MAC addr BKB102AP> (try 1/3)
[  207.860416] wlan0: authenticated
[  207.860928] ath5k 0000:02:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[  207.860941] ath5k 0000:02:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[  207.864104] wlan0: associate with <MAC addr BKB102AP> (try 1/3)
[  207.968183] wlan0: associate with <MAC addr BKB102AP> (try 2/3)
[  208.072154] wlan0: associate with <MAC addr BKB102AP> (try 3/3)
[  208.176138] wlan0: association with <MAC addr BKB102AP> timed out
[  219.034813] wlan0: authenticate with <MAC addr BKB102AP>
[  219.035350] wlan0: send auth to <MAC addr BKB102AP> (try 1/3)
[  219.036932] wlan0: authenticated
[  219.038351] ath5k 0000:02:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[  219.038378] ath5k 0000:02:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[  219.041603] wlan0: associate with <MAC addr BKB102AP> (try 1/3)
[  219.144120] wlan0: associate with <MAC addr BKB102AP> (try 2/3)
[  219.248143] wlan0: associate with <MAC addr BKB102AP> (try 3/3)
[  219.352118] wlan0: association with <MAC addr BKB102AP> timed out
[  248.437796] wlan0: authenticate with <MAC addr BKB102AP>
[  248.438152] wlan0: send auth to <MAC addr BKB102AP> (try 1/3)
[  248.439680] wlan0: authenticated
[  248.440250] ath5k 0000:02:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[  248.440263] ath5k 0000:02:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[  248.444098] wlan0: associate with <MAC addr BKB102AP> (try 1/3)
[  248.548111] wlan0: associate with <MAC addr BKB102AP> (try 2/3)
[  248.652176] wlan0: associate with <MAC addr BKB102AP> (try 3/3)
[  248.756106] wlan0: association with <MAC addr BKB102AP> timed out
[  259.636603] wlan0: authenticate with <MAC addr BKB102AP>
[  259.636957] wlan0: send auth to <MAC addr BKB102AP> (try 1/3)
[  259.639006] wlan0: authenticated
[  259.639549] ath5k 0000:02:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[  259.639565] ath5k 0000:02:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[  259.640098] wlan0: associate with <MAC addr BKB102AP> (try 1/3)
[  259.744102] wlan0: associate with <MAC addr BKB102AP> (try 2/3)
[  259.848141] wlan0: associate with <MAC addr BKB102AP> (try 3/3)
[  259.952226] wlan0: association with <MAC addr BKB102AP> timed out

########## wireless info END ############
```

---

### Post by varunendra on 2014-09-07
I am wondering if you tried something fancy that got you out of those two groups in the first place. Please confirm if it is a default installation or not.

What I mean to ask is - have you tried something with accounts, permissions, cloning or anything that you think might give us some clues?

For now, I suggest downloading fresh Network Manager packages, then purge it > reboot > reinstall it. Here's how -

1) While being connected with wired connection, download the packages first so you can install them offline (you will go completely offline after purging it) -
```
sudo apt-get install -d --reinstall network-manager network-manager-gnome
```

2) Purge it -
```
sudo apt-get purge network-manager-gnome network-manager
```

3) Reboot and reinstall it -
```
sudo apt-get install network-manager network-manager-gnome
```

Retry to connect after this. If it still fails, check 'nm-tool' again -
```
nm-tool
```
Do the "[COLOR="#FF0000"]..Could not create object ..... uid 1000 has no permission to perform this operation[/COLOR]" errors still appear?

---

### Post by TaiChiRabbit on 2014-09-07
unfortunately still not working after reinstalling network managers, still get "[COLOR=#FF0000].Could not create object ..... uid 1000 has no permission to perform this operation[/COLOR]" errors.
The setup is plain vanilla, just a dual boot netbook.

Output from nm-tool

```

NetworkManager Tool

State: disconnected

- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            sky2
  State:             unavailable
  Default:           no
  HW Address:        00:13:77:D2:D1:A2

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off


- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            ath5k
  State:             disconnected
  Default:           no
  HW Address:        00:21:63:C4:A9:15

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 
    HELEN-PC_Network:Infra, 00:22:3F:8D:2B:00, Freq 2417 MHz, Rate 54 Mb/s, Strength 37 WPA2
    BTWifi-X:        Infra, 22:81:D8:69:30:BA, Freq 2462 MHz, Rate 54 Mb/s, Strength 32 WPA WPA2 Enterprise
    14:              Infra, 90:72:40:20:F8:84, Freq 2462 MHz, Rate 54 Mb/s, Strength 32 WPA2
    NTGR_eks1vae376ff: Infra, E0:91:F5:50:56:D6, Freq 2412 MHz, Rate 54 Mb/s, Strength 27 WPA2
    SKYCD70A:        Infra, 7C:4C:A5:B2:47:59, Freq 2412 MHz, Rate 54 Mb/s, Strength 25 WPA2
    BTHub3-HW9M:     Infra, 00:FE:F4:40:70:08, Freq 2412 MHz, Rate 54 Mb/s, Strength 22 WPA WPA2
    BTWiFi:          Infra, 02:24:17:DE:04:D0, Freq 2412 MHz, Rate 54 Mb/s, Strength 19
    SKY89B43:        Infra, 7C:4C:A5:A7:01:45, Freq 2462 MHz, Rate 54 Mb/s, Strength 14 WPA2
    BTWifi-with-FON: Infra, 02:81:D8:69:30:BA, Freq 2462 MHz, Rate 54 Mb/s, Strength 27
    BKB102AP:        Infra, 00:18:4D:D2:07:79, Freq 2472 MHz, Rate 54 Mb/s, Strength 74 WPA2


```

Output from Wireless script:

```

########## wireless info START ##########

Report from: 07 Sep 2014 13:40 BST +0100

Script from: 05 Sep 2014 22:42 UTC +0000

##### release #####

Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.1 LTS
Release:    14.04
Codename:    trusty

##### kernel #####

Linux 3.13.0-35-generic #62-Ubuntu SMP Fri Aug 15 01:58:01 UTC 2014 i686 i686 i686 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop #####

Ubuntu

##### lspci #####

02:00.0 Ethernet controller [0200]: Qualcomm Atheros AR242x / AR542x Wireless Network Adapter (PCI-Express) [168c:001c] (rev 01)
    Subsystem: Askey Computer Corp. Device [144f:7131]
    Kernel driver in use: ath5k

03:00.0 Ethernet controller [0200]: Marvell Technology Group Ltd. 88E8040 PCI-E Fast Ethernet Controller [11ab:4354] (rev 13)
    Subsystem: Samsung Electronics Co Ltd Device [144d:ca00]
    Kernel driver in use: sky2

##### lsusb #####

Bus 001 Device 004: ID 0ac8:c326 Z-Star Microelectronics Corp. Namuga 1.3M Webcam
Bus 001 Device 007: ID 058f:6387 Alcor Micro Corp. Flash Drive
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 0a5c:2101 Broadcom Corp. BCM2045 Bluetooth
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 0fcf:1009 Dynastream Innovations, Inc. 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

##### PCMCIA card info #####

##### rfkill #####

2: samsung-wlan: Wireless LAN
    Soft blocked: no
    Hard blocked: no
3: hci0: Bluetooth
    Soft blocked: yes
    Hard blocked: no
4: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

##### lsmod #####

ath5k                 134977  0 
ath                    23922  1 ath5k
mac80211              546051  1 ath5k
cfg80211              409394  3 ath,ath5k,mac80211

##### interfaces #####

auto lo
iface lo inet loopback

auto wlan0

##### ifconfig #####

eth0      Link encap:Ethernet  HWaddr <MAC addr eth0>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:18 

wlan0     Link encap:Ethernet  HWaddr <MAC addr wlan0>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

##### iwconfig #####

lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          

##### route #####

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface

##### resolv.conf #####

##### nm-tool #####

** (process:3482): WARNING **: Could not create object for /org/freedesktop/NetworkManager/Settings/21: uid 1000 has no permission to perform this operation

** (process:3482): WARNING **: Could not create object for /org/freedesktop/NetworkManager/Settings/23: uid 1000 has no permission to perform this operation

** (process:3482): WARNING **: handle_property_changed: failed to update property 'available-connections' of object type NMDeviceWifi.

** (process:3482): WARNING **: error: cannot retrieve connection: uid 1000 has no permission to perform this operation

** (process:3482): WARNING **: error: cannot retrieve connection: uid 1000 has no permission to perform this operation

** (process:3482): WARNING **: error: cannot retrieve connection: uid 1000 has no permission to perform this operation

** (process:3482): WARNING **: error: cannot retrieve connection: uid 1000 has no permission to perform this operation

** (process:3482): WARNING **: error: cannot retrieve connection: uid 1000 has no permission to perform this operation

** (process:3482): WARNING **: error: cannot retrieve connection: uid 1000 has no permission to perform this operation

** (process:3482): WARNING **: error: cannot retrieve connection: uid 1000 has no permission to perform this operation

** (process:3482): WARNING **: error: cannot retrieve connection: uid 1000 has no permission to perform this operation

NetworkManager Tool

State: disconnected

- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            ath5k
  State:             disconnected
  Default:           no
  HW Address:        <MAC addr wlan0>

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 
    BKB102AP:        Infra, <MAC addr BKB102AP>, Freq 2472 MHz, Rate 54 Mb/s, Strength 34 WPA2
    4A's Network:    Infra, <MAC addr 4A's Network>, Freq 2412 MHz, Rate 54 Mb/s, Strength 7 WPA2
    SKY89B43:        Infra, <MAC addr SKY89B43>, Freq 2462 MHz, Rate 54 Mb/s, Strength 27 WPA2
    SKYAAA42:        Infra, <MAC addr SKYAAA42>, Freq 2437 MHz, Rate 54 Mb/s, Strength 25 WPA2
    4A's Network:    Infra, <MAC addr 4A's Network>, Freq 2412 MHz, Rate 54 Mb/s, Strength 22 WPA2
    SKY19849:        Infra, <MAC addr SKY19849>, Freq 2432 MHz, Rate 54 Mb/s, Strength 17 WPA
    SKY3F1FA:        Infra, <MAC addr SKY3F1FA>, Freq 2462 MHz, Rate 54 Mb/s, Strength 14 WPA WPA2
    14:              Infra, <MAC addr 14>, Freq 2462 MHz, Rate 54 Mb/s, Strength 12 WPA2
    BTWifi-with-FON: Infra, <MAC addr BTWifi-with-FON>, Freq 2412 MHz, Rate 54 Mb/s, Strength 30
    BTWifi-with-FON: Infra, <MAC addr BTWifi-with-FON>, Freq 2437 MHz, Rate 54 Mb/s, Strength 24
    4A's Guest Network: Infra, <MAC addr 4A's Guest Network>, Freq 2412 MHz, Rate 54 Mb/s, Strength 24 WPA2
    BTWifi-with-FON: Infra, <MAC addr BTWifi-with-FON>, Freq 2462 MHz, Rate 54 Mb/s, Strength 24
    BTWifi-X:        Infra, <MAC addr BTWifi-X>, Freq 2412 MHz, Rate 54 Mb/s, Strength 29 WPA WPA2 Enterprise
    BTHub4-52GR:     Infra, <MAC addr BTHub4-52GR>, Freq 2412 MHz, Rate 54 Mb/s, Strength 22 WPA WPA2
    NETGEAR40:       Infra, <MAC addr NETGEAR40>, Freq 2412 MHz, Rate 54 Mb/s, Strength 15 WPA2
    BTWifi-X:        Infra, <MAC addr BTWifi-X>, Freq 2412 MHz, Rate 54 Mb/s, Strength 14 WPA WPA2 Enterprise
    SKYC200D:        Infra, <MAC addr SKYC200D>, Freq 2437 MHz, Rate 54 Mb/s, Strength 9 WPA2
    BTHub3-TPKG:     Infra, <MAC addr BTHub3-TPKG>, Freq 2462 MHz, Rate 54 Mb/s, Strength 4 WPA WPA2
    BTWifi-X:        Infra, <MAC addr BTWifi-X>, Freq 2462 MHz, Rate 54 Mb/s, Strength 4 WPA WPA2 Enterprise

- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            sky2
  State:             unavailable
  Default:           no
  HW Address:        <MAC addr eth0>

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off

##### NetworkManager.state #####

[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true

##### NetworkManager.conf #####

[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq

[ifupdown]
managed=false

##### iw reg get #####

country 00:
    (2402 - 2472 @ 40), (3, 20)
    (2457 - 2482 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (2474 - 2494 @ 20), (3, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
    (5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS

##### iwlist channels #####

lo        no frequency information.

eth0      no frequency information.

wlan0     13 channels in total; available frequencies :
          Channel 01 : 2.412 GHz
          Channel 02 : 2.417 GHz
          Channel 03 : 2.422 GHz
          Channel 04 : 2.427 GHz
          Channel 05 : 2.432 GHz
          Channel 06 : 2.437 GHz
          Channel 07 : 2.442 GHz
          Channel 08 : 2.447 GHz
          Channel 09 : 2.452 GHz
          Channel 10 : 2.457 GHz
          Channel 11 : 2.462 GHz
          Channel 12 : 2.467 GHz
          Channel 13 : 2.472 GHz

##### iwlist scan #####

Channel occupancy:

     2   WLAPs on   Frequency:2.412 GHz (Channel 1)
     4   WLAPs on   Frequency:2.437 GHz (Channel 6)
     4   WLAPs on   Frequency:2.462 GHz (Channel 11)
     1   WLAPs on   Frequency:2.472 GHz (Channel 13)

wlan0     Scan completed :
          Cell 01 - Address: <MAC addr BKB102AP>
                    Channel:13
                    Frequency:2.472 GHz (Channel 13)
                    Quality=21/70  Signal level=-89 dBm  
                    Encryption key:on
                    ESSID:"BKB102AP"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s
                    Bit Rates:9 Mb/s; 18 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000ab312c9e0
                    Extra: Last beacon: 16ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC addr SKY89B43>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=18/70  Signal level=-92 dBm  
                    Encryption key:on
                    ESSID:"SKY89B43"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000d89bb0ac4
                    Extra: Last beacon: 16ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: <MAC addr SKYAAA42>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=18/70  Signal level=-92 dBm  
                    Encryption key:on
                    ESSID:"SKYAAA42"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000f81ffb0e9
                    Extra: Last beacon: 16ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 04 - Address: <MAC addr BTHub3-TPKG>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=17/70  Signal level=-93 dBm  
                    Encryption key:on
                    ESSID:"BTHub3-TPKG"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000003df799c1
                    Extra: Last beacon: 16ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 05 - Address: <MAC addr BTWifi-with-FON>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=18/70  Signal level=-92 dBm  
                    Encryption key:off
                    ESSID:"BTWifi-with-FON"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000003df87930
                    Extra: Last beacon: 16ms ago
          Cell 06 - Address: <MAC addr BTWifi-X>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=18/70  Signal level=-92 dBm  
                    Encryption key:on
                    ESSID:"BTWifi-X"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000003df88bf8
                    Extra: Last beacon: 16ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : 802.1x
                       Preauthentication Supported
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : 802.1x
          Cell 07 - Address: <MAC addr BTWifi-X>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=14/70  Signal level=-96 dBm  
                    Encryption key:on
                    ESSID:"BTWifi-X"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000fc1d4f180
                    Extra: Last beacon: 840ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : 802.1x
                       Preauthentication Supported
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : 802.1x
          Cell 08 - Address: <MAC addr NETGEAR40>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=13/70  Signal level=-97 dBm  
                    Encryption key:on
                    ESSID:"NETGEAR40"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 16ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 09 - Address: <MAC address>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=10/70  Signal level=-100 dBm  
                    Encryption key:on
                    ESSID:"BTHub3-NXM9"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000308de604ce
                    Extra: Last beacon: 16ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 10 - Address: <MAC addr BTWifi-with-FON>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=10/70  Signal level=-100 dBm  
                    Encryption key:off
                    ESSID:"BTWifi-with-FON"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000308de6dd07
                    Extra: Last beacon: 16ms ago
          Cell 11 - Address: <MAC address>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=7/70  Signal level=-103 dBm  
                    Encryption key:on
              lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

      ESSID:"BTWifi-X"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000308de6fb2a
                    Extra: Last beacon: 16ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : 802.1x
                       Preauthentication Supported
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : 802.1x

##### module infos #####

[ath5k]
filename:       /lib/modules/3.13.0-35-generic/kernel/drivers/net/wireless/ath/ath5k/ath5k.ko
license:        Dual BSD/GPL
description:    Support for 5xxx series of Atheros 802.11 wireless LAN cards.
author:         Nick Kossifidis
author:         Jiri Slaby
srcversion:     F36818A2F0BCB2B0CC9BB8C
depends:        mac80211,cfg80211,ath
intree:         Y
vermagic:       3.13.0-35-generic SMP mod_unload modversions 686 
signer:         Magrathea: Glacier signing key
sig_key:        A2:8D:B5:FD:6E:29:9C:CE:49:47:DA:CA:A6:6F:45:9D:B4:AC:CE:24
sig_hashalgo:   sha512
parm:           nohwcrypt:Disable hardware encryption. (bool)
parm:           fastchanswitch:Enable fast channel switching for AR2413/AR5413 radios. (bool)
parm:           no_hw_rfkill_switch:Ignore the GPIO RFKill switch state (bool)

[ath]
filename:       /lib/modules/3.13.0-35-generic/kernel/drivers/net/wireless/ath/ath.ko
license:        Dual BSD/GPL
description:    Shared library for Atheros wireless LAN cards.
author:         Atheros Communications
srcversion:     88A67C5359B02C5A710AFCF
depends:        cfg80211
intree:         Y
vermagic:       3.13.0-35-generic SMP mod_unload modversions 686 
signer:         Magrathea: Glacier signing key
sig_key:        A2:8D:B5:FD:6E:29:9C:CE:49:47:DA:CA:A6:6F:45:9D:B4:AC:CE:24
sig_hashalgo:   sha512

##### module parameters #####

[ath5k]
fastchanswitch: N
nohwcrypt: N
no_hw_rfkill_switch: N

##### /etc/modules #####

lp

##### blacklists #####

[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci

[/etc/modprobe.d/blacklist-bcm43.conf]
blacklist b43
blacklist b43legacy
blacklist ssb
blacklist bcm43xx
blacklist brcm80211
blacklist brcmfmac
blacklist brcmsmac
blacklist bcma

[/etc/modprobe.d/blacklist.conf]
blacklist evbug
blacklist usbmouse
blacklist usbkbd
blacklist eepro100
blacklist de4x5
blacklist eth1394
blacklist snd_intel8x0m
blacklist snd_aw2
blacklist i2c_i801
blacklist prism54
blacklist bcm43xx
blacklist garmin_gps
blacklist asus_acpi
blacklist snd_pcsp
blacklist pcspkr
blacklist amd76x_edac

[/etc/modprobe.d/libpisock9.conf]
blacklist visor

[/etc/modprobe.d/osspd.conf]
blacklist snd-pcm-oss
blacklist snd-mixer-oss
blacklist snd-seq-oss

##### rc.local #####

rfkill block bluetooth
exit 0

##### udev rules #####

[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x11ab:0x4354 (sky2)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC addr eth0>", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# PCI device 0x168c:0x001c (ath5k)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC addr wlan0>", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

##### dmesg #####

[   21.506256] ath5k 0000:02:00.0: can't disable ASPM; OS doesn't have ASPM control
[   21.506560] ath5k 0000:02:00.0: registered as 'phy0'
[   22.238148] ath: EEPROM regdomain: 0x65
[   22.238159] ath: EEPROM indicates we should expect a direct regpair map
[   22.238169] ath: Country alpha2 being used: 00
[   22.238175] ath: Regpair used: 0x65
[   22.489436] ath5k: phy0: Atheros AR2425 chip found (MAC: 0xe2, PHY: 0x70)
[   55.646001] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready (repeated 2 times)
[   58.016138] ath5k: ath5k_hw_get_isr: ISR: 0x00040001 IMR: 0x00000000
[   58.190877] wlan0: authenticate with <MAC addr BKB102AP>
[   58.201878] wlan0: send auth to <MAC addr BKB102AP> (try 1/3)
[   58.206759] wlan0: authenticated
[   58.207303] ath5k 0000:02:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[   58.207319] ath5k 0000:02:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[   58.208232] wlan0: associate with <MAC addr BKB102AP> (try 1/3)
[   58.312181] wlan0: associate with <MAC addr BKB102AP> (try 2/3)
[   58.416102] wlan0: associate with <MAC addr BKB102AP> (try 3/3)
[   58.520086] wlan0: association with <MAC addr BKB102AP> timed out
[   58.561559] wlan0: authenticate with <MAC addr BKB102AP>
[   58.561913] wlan0: send auth to <MAC addr BKB102AP> (try 1/3)
[   58.563604] wlan0: authenticated
[   58.564190] ath5k 0000:02:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[   58.564204] ath5k 0000:02:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[   58.568124] wlan0: associate with <MAC addr BKB102AP> (try 1/3)
[   58.672114] wlan0: associate with <MAC addr BKB102AP> (try 2/3)
[   58.776090] wlan0: associate with <MAC addr BKB102AP> (try 3/3)
[   58.880129] wlan0: association with <MAC addr BKB102AP> timed out
[  415.589278] ath5k 0000:02:00.0: can't disable ASPM; OS doesn't have ASPM control
[  415.589642] ath5k 0000:02:00.0: registered as 'phy0'
[  416.171742] ath: EEPROM regdomain: 0x65
[  416.171751] ath: EEPROM indicates we should expect a direct regpair map
[  416.171758] ath: Country alpha2 being used: 00
[  416.171762] ath: Regpair used: 0x65
[  416.174766] ath5k: phy0: Atheros AR2425 chip found (MAC: 0xe2, PHY: 0x70)
[  417.017313] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready (repeated 2 times)

########## wireless info END ############
```

---

### Post by varunendra on 2014-09-07
I must admit I'm stumped. Could you try the script on the live session from the DVD/USB which you installed from and please confirm if the errors appear there as well?

---

### Post by TaiChiRabbit on 2014-09-08
Thank so much for all the patience and help, I booted on a USB live disk and still couldnt get access, so I thought it must be the access point so went through all those settings and rebooted and still no joy, it's just weird how I can access the wifi when I boot under windows!  Still it not vital and can work around no wifi on this machine.  

for info here is the wireless output under the livedisk

```

########## wireless info START ##########

Report from: 08 Sep 2014 10:48 UTC +0000

Script from: 05 Sep 2014 22:42 UTC +0000

##### release #####

Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.1 LTS
Release:    14.04
Codename:    trusty

##### kernel #####

Linux 3.13.0-32-generic #57-Ubuntu SMP Tue Jul 15 03:51:12 UTC 2014 i686 i686 i686 GNU/Linux

noprompt, cdrom-detect/try-usb=true, persistent, file=/cdrom/preseed/ubuntu.seed, boot=casper, initrd=/casper/initrd.lz, quiet, splash, --, maybe-ubiquity

##### desktop #####

Ubuntu

##### lspci #####

02:00.0 Ethernet controller [0200]: Qualcomm Atheros AR242x / AR542x Wireless Network Adapter (PCI-Express) [168c:001c] (rev 01)
    Subsystem: Askey Computer Corp. Device [144f:7131]
    Kernel driver in use: ath5k

03:00.0 Ethernet controller [0200]: Marvell Technology Group Ltd. 88E8040 PCI-E Fast Ethernet Controller [11ab:4354] (rev 13)
    Subsystem: Samsung Electronics Co Ltd Device [144d:ca00]
    Kernel driver in use: sky2

##### lsusb #####

Bus 001 Device 004: ID 0ac8:c326 Z-Star Microelectronics Corp. Namuga 1.3M Webcam
Bus 001 Device 003: ID 0781:556b SanDisk Corp. 
Bus 001 Device 005: ID 058f:6387 Alcor Micro Corp. Flash Drive
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 0a5c:2101 Broadcom Corp. BCM2045 Bluetooth
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

##### PCMCIA card info #####

##### rfkill #####

0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
1: samsung-wlan: Wireless LAN
    Soft blocked: no
    Hard blocked: no
2: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

##### lsmod #####

ath5k                 134977  0 
ath                    23922  1 ath5k
mac80211              546051  1 ath5k
cfg80211              409394  3 ath,ath5k,mac80211

##### interfaces #####

auto lo
iface lo inet loopback

##### ifconfig #####

eth0      Link encap:Ethernet  HWaddr <MAC addr eth0>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:18 

wlan0     Link encap:Ethernet  HWaddr <MAC addr wlan0>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

##### iwconfig #####

lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          

##### route #####

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface

##### resolv.conf #####

##### nm-tool #####

NetworkManager Tool

State: disconnected

- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            sky2
  State:             unavailable
  Default:           no
  HW Address:        <MAC addr eth0>

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off

- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            ath5k
  State:             disconnected
  Default:           no
  HW Address:        <MAC addr wlan0>

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 
    SKYAAA42:        Infra, <MAC addr SKYAAA42>, Freq 2412 MHz, Rate 54 Mb/s, Strength 22 WPA2
    4A's Network:    Infra, <MAC addr 4A's Network>, Freq 2412 MHz, Rate 54 Mb/s, Strength 15 WPA2
    4A's Guest Network: Infra, <MAC addr 4A's Guest Network>, Freq 2412 MHz, Rate 54 Mb/s, Strength 15 WPA2
    BTHub3-HW9M:     Infra, <MAC addr BTHub3-HW9M>, Freq 2412 MHz, Rate 54 Mb/s, Strength 4 WPA WPA2
    BTWifi-with-FON: Infra, <MAC addr BTWifi-with-FON>, Freq 2462 MHz, Rate 54 Mb/s, Strength 5
    SKY19849:        Infra, <MAC addr SKY19849>, Freq 2432 MHz, Rate 54 Mb/s, Strength 4 WPA
    BTWifi-X:        Infra, <MAC addr BTWifi-X>, Freq 2412 MHz, Rate 54 Mb/s, Strength 9 WPA WPA2 Enterprise
    SKY89B43:        Infra, <MAC addr SKY89B43>, Freq 2462 MHz, Rate 54 Mb/s, Strength 10 WPA2
    BKB102AP:        Infra, <MAC addr BKB102AP>, Freq 2412 MHz, Rate 54 Mb/s, Strength 19 WPA2
    thor:            Infra, <MAC addr thor>, Freq 2437 MHz, Rate 54 Mb/s, Strength 15 WPA2
    BTHub3-TPKG:     Infra, <MAC addr BTHub3-TPKG>, Freq 2462 MHz, Rate 54 Mb/s, Strength 5 WPA WPA2
    SKYC200D:        Infra, <MAC addr SKYC200D>, Freq 2437 MHz, Rate 54 Mb/s, Strength 10 WPA2
    NETGEAR40:       Infra, <MAC addr NETGEAR40>, Freq 2412 MHz, Rate 54 Mb/s, Strength 2 WPA2
    BTWifi-with-FON: Infra, <MAC addr BTWifi-with-FON>, Freq 2412 MHz, Rate 54 Mb/s, Strength 0
    BTHub4-52GR:     Infra, <MAC addr BTHub4-52GR>, Freq 2412 MHz, Rate 54 Mb/s, Strength 0 WPA WPA2
    NTGR_eks1vae376ff: Infra, <MAC addr NTGR_eks1vae376ff>, Freq 2412 MHz, Rate 54 Mb/s, Strength 0 WPA2
    SKY1D01B:        Infra, <MAC addr SKY1D01B>, Freq 2462 MHz, Rate 54 Mb/s, Strength 0 WPA WPA2
    BTWifi-with-FON: Infra, <MAC addr BTWifi-with-FON>, Freq 2412 MHz, Rate 54 Mb/s, Strength 4

##### NetworkManager.state #####

[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true

##### NetworkManager.conf #####

[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq

[ifupdown]
managed=false

##### iw reg get #####

country 00:
    (2402 - 2472 @ 40), (3, 20)
    (2457 - 2482 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (2474 - 2494 @ 20), (3, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
    (5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS

##### iwlist channels #####

lo        no frequency information.

eth0      no frequency information.

wlan0     13 channels in total; available frequencies :
          Channel 01 : 2.412 GHz
          Channel 02 : 2.417 GHz
          Channel 03 : 2.422 GHz
          Channel 04 : 2.427 GHz
          Channel 05 : 2.432 GHz
          Channel 06 : 2.437 GHz
          Channel 07 : 2.442 GHz
          Channel 08 : 2.447 GHz
          Channel 09 : 2.452 GHz
          Channel 10 : 2.457 GHz
          Channel 11 : 2.462 GHz
          Channel 12 : 2.467 GHz
          Channel 13 : 2.472 GHz

##### iwlist scan #####

Channel occupancy:

     5   WLAPs on   Frequency:2.412 GHz (Channel 1)
     1   WLAPs on   Frequency:2.432 GHz (Channel 5)
     1   WLAPs on   Frequency:2.462 GHz (Channel 11)
     1   WLAPs on   Frequency:2.462 GHz (Channel 11)

wlan0     Scan completed :
          Cell 01 - Address: <MAC addr BKB102AP>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=19/70  Signal level=-91 dBm  
                    Encryption key:on
                    ESSID:"BKB102AP"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s
                    Bit Rates:9 Mb/s; 18 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000029946713
                    Extra: Last beacon: 12ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC addr NETGEAR40>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=16/70  Signal level=-94 dBm  
                    Encryption key:on
                    ESSID:"NETGEAR40"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 12ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: <MAC addr NTGR_eks1vae376ff>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=8/70  Signal level=-102 dBm  
                    Encryption key:on
                    ESSID:"NTGR_eks1vae376ff"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000060581c1c188
                    Extra: Last beacon: 17712ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 04 - Address: <MAC addr BTWifi-with-FON>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=16/70  Signal level=-94 dBm  
                    Encryption key:off
                    ESSID:"BTWifi-with-FON"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000024e45275ab6
                    Extra: Last beacon: 12ms ago
          Cell 05 - Address: <MAC addr SKY19849>
                    Channel:5
                    Frequency:2.432 GHz (Channel 5)
                    Quality=11/70  Signal level=-99 dBm  
                    Encryption key:on
                    ESSID:"SKY19849"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 22 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000063e50dea25
                    Extra: Last beacon: 12ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 06 - Address: <MAC addr SKY1D01B>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=6/70  Signal level=-104 dBm  
                    Encryption key:on
                    ESSID:"SKY1D01B"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000252ac9f19e
                    Extra: Last beacon: 17116ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 07 - Address: <MAC addr SKY89B43>
                    Channel:11
      lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

              Frequency:2.462 GHz (Channel 11)
                    Quality=16/70  Signal level=-94 dBm  
                    Encryption key:on
                    ESSID:"SKY89B43"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000201339073d
                    Extra: Last beacon: 16892ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 08 - Address: <MAC address>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=15/70  Signal level=-95 dBm  
                    Encryption key:on
                    ESSID:"BTWifi-X"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000024e4526fe87
                    Extra: Last beacon: 12ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : 802.1x
                       Preauthentication Supported
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : 802.1x

##### module infos #####

[ath5k]
filename:       /lib/modules/3.13.0-32-generic/kernel/drivers/net/wireless/ath/ath5k/ath5k.ko
license:        Dual BSD/GPL
description:    Support for 5xxx series of Atheros 802.11 wireless LAN cards.
author:         Nick Kossifidis
author:         Jiri Slaby
srcversion:     F36818A2F0BCB2B0CC9BB8C
depends:        mac80211,cfg80211,ath
intree:         Y
vermagic:       3.13.0-32-generic SMP mod_unload modversions 686 
signer:         Magrathea: Glacier signing key
sig_key:        A7:FC:65:90:FC:4A:8D:85:9A:AE:BD:A2:CA:5D:D0:47:16:24:4F:A0
sig_hashalgo:   sha512
parm:           nohwcrypt:Disable hardware encryption. (bool)
parm:           fastchanswitch:Enable fast channel switching for AR2413/AR5413 radios. (bool)
parm:           no_hw_rfkill_switch:Ignore the GPIO RFKill switch state (bool)

[ath]
filename:       /lib/modules/3.13.0-32-generic/kernel/drivers/net/wireless/ath/ath.ko
license:        Dual BSD/GPL
description:    Shared library for Atheros wireless LAN cards.
author:         Atheros Communications
srcversion:     88A67C5359B02C5A710AFCF
depends:        cfg80211
intree:         Y
vermagic:       3.13.0-32-generic SMP mod_unload modversions 686 
signer:         Magrathea: Glacier signing key
sig_key:        A7:FC:65:90:FC:4A:8D:85:9A:AE:BD:A2:CA:5D:D0:47:16:24:4F:A0
sig_hashalgo:   sha512

##### module parameters #####

[ath5k]
fastchanswitch: N
nohwcrypt: N
no_hw_rfkill_switch: N

##### /etc/modules #####

##### blacklists #####

[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci

[/etc/modprobe.d/blacklist.conf]
blacklist evbug
blacklist usbmouse
blacklist usbkbd
blacklist eepro100
blacklist de4x5
blacklist eth1394
blacklist snd_intel8x0m
blacklist snd_aw2
blacklist i2c_i801
blacklist prism54
blacklist bcm43xx
blacklist garmin_gps
blacklist asus_acpi
blacklist snd_pcsp
blacklist pcspkr
blacklist amd76x_edac

##### rc.local #####

exit 0

##### udev rules #####

[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x11ab:0x4354 (sky2)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC addr eth0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# PCI device 0x168c:0x001c (ath5k)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC addr wlan0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

##### dmesg #####

[   51.202657] ath5k 0000:02:00.0: can't disable ASPM; OS doesn't have ASPM control
[   51.203965] ath5k 0000:02:00.0: registered as 'phy0'
[   53.597229] ath: EEPROM regdomain: 0x65
[   53.597240] ath: EEPROM indicates we should expect a direct regpair map
[   53.597249] ath: Country alpha2 being used: 00
[   53.597255] ath: Regpair used: 0x65
[   53.778694] ath5k: phy0: Atheros AR2425 chip found (MAC: 0xe2, PHY: 0x70)
[   57.818343] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready (repeated 2 times)
[  213.049688] wlan0: authenticate with <MAC addr BKB102AP>
[  213.058940] wlan0: send auth to <MAC addr BKB102AP> (try 1/3)
[  213.062508] wlan0: authenticated
[  213.063020] ath5k 0000:02:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[  213.063030] ath5k 0000:02:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[  213.064131] wlan0: associate with <MAC addr BKB102AP> (try 1/3)
[  213.168073] wlan0: associate with <MAC addr BKB102AP> (try 2/3)
[  213.272084] wlan0: associate with <MAC addr BKB102AP> (try 3/3)
[  213.376106] wlan0: association with <MAC addr BKB102AP> timed out
[  214.338181] wlan0: authenticate with <MAC addr BKB102AP>
[  214.341384] wlan0: send auth to <MAC addr BKB102AP> (try 1/3)
[  214.342859] wlan0: authenticated
[  214.349603] ath5k 0000:02:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[  214.349618] ath5k 0000:02:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[  214.352088] wlan0: associate with <MAC addr BKB102AP> (try 1/3)
[  214.456124] wlan0: associate with <MAC addr BKB102AP> (try 2/3)
[  214.560084] wlan0: associate with <MAC addr BKB102AP> (try 3/3)
[  214.664182] wlan0: association with <MAC addr BKB102AP> timed out
[  216.028011] wlan0: authenticate with <MAC addr BKB102AP>
[  216.028691] wlan0: send auth to <MAC addr BKB102AP> (try 1/3)
[  216.032093] wlan0: authenticated
[  216.034932] ath5k 0000:02:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[  216.034947] ath5k 0000:02:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[  216.036116] wlan0: associate with <MAC addr BKB102AP> (try 1/3)
[  216.140176] wlan0: associate with <MAC addr BKB102AP> (try 2/3)
[  216.244152] wlan0: associate with <MAC addr BKB102AP> (try 3/3)
[  216.348165] wlan0: association with <MAC addr BKB102AP> timed out
[  224.061886] wlan0: authenticate with <MAC addr BKB102AP>
[  224.062270] wlan0: send auth to <MAC addr BKB102AP> (try 1/3)
[  224.063751] wlan0: authenticated
[  224.064380] ath5k 0000:02:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[  224.064395] ath5k 0000:02:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[  224.069006] wlan0: associate with <MAC addr BKB102AP> (try 1/3)
[  224.176164] wlan0: associate with <MAC addr BKB102AP> (try 2/3)
[  224.280107] wlan0: associate with <MAC addr BKB102AP> (try 3/3)
[  224.384135] wlan0: association with <MAC addr BKB102AP> timed out
[  236.134645] wlan0: authenticate with <MAC addr BKB102AP>
[  236.134983] wlan0: send auth to <MAC addr BKB102AP> (try 1/3)
[  236.137499] wlan0: authenticated
[  236.138017] ath5k 0000:02:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[  236.138032] ath5k 0000:02:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[  236.140345] wlan0: associate with <MAC addr BKB102AP> (try 1/3)
[  236.244256] wlan0: associate with <MAC addr BKB102AP> (try 2/3)
[  236.348135] wlan0: associate with <MAC addr BKB102AP> (try 3/3)
[  236.452128] wlan0: association with <MAC addr BKB102AP> timed out
[  611.621743] wlan0: authenticate with <MAC addr BKB102AP>
[  611.628835] wlan0: send auth to <MAC addr BKB102AP> (try 1/3)
[  611.632868] wlan0: authenticated
[  611.635700] ath5k 0000:02:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[  611.635718] ath5k 0000:02:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[  611.636122] wlan0: associate with <MAC addr BKB102AP> (try 1/3)
[  611.740100] wlan0: associate with <MAC addr BKB102AP> (try 2/3)
[  611.844118] wlan0: associate with <MAC addr BKB102AP> (try 3/3)
[  611.952113] wlan0: association with <MAC addr BKB102AP> timed out
[  622.826540] wlan0: authenticate with <MAC addr BKB102AP>
[  622.835400] wlan0: send auth to <MAC addr BKB102AP> (try 1/3)
[  622.839023] wlan0: authenticated
[  622.839558] ath5k 0000:02:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[  622.839572] ath5k 0000:02:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[  622.840289] wlan0: associate with <MAC addr BKB102AP> (try 1/3)
[  622.944071] wlan0: associate with <MAC addr BKB102AP> (try 2/3)
[  623.052610] wlan0: associate with <MAC addr BKB102AP> (try 3/3)
[  623.156119] wlan0: association with <MAC addr BKB102AP> timed out
[  661.039874] wlan0: authenticate with <MAC addr BKB102AP>
[  661.044671] wlan0: send auth to <MAC addr BKB102AP> (try 1/3)
[  661.055635] wlan0: authenticated
[  661.056448] ath5k 0000:02:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[  661.056463] ath5k 0000:02:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[  661.060171] wlan0: associate with <MAC addr BKB102AP> (try 1/3)
[  661.164094] wlan0: associate with <MAC addr BKB102AP> (try 2/3)
[  661.268187] wlan0: associate with <MAC addr BKB102AP> (try 3/3)
[  661.400177] wlan0: association with <MAC addr BKB102AP> timed out
[  672.266827] wlan0: authenticate with <MAC addr BKB102AP>
[  672.274117] wlan0: send auth to <MAC addr BKB102AP> (try 1/3)
[  672.277995] wlan0: authenticated
[  672.280695] ath5k 0000:02:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[  672.280710] ath5k 0000:02:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[  672.284560] wlan0: associate with <MAC addr BKB102AP> (try 1/3)
[  672.388138] wlan0: associate with <MAC addr BKB102AP> (try 2/3)
[  672.492175] wlan0: associate with <MAC addr BKB102AP> (try 3/3)
[  672.596163] wlan0: association with <MAC addr BKB102AP> timed out
[  693.222509] wlan0: authenticate with <MAC addr BKB102AP>
[  693.227027] wlan0: send auth to <MAC addr BKB102AP> (try 1/3)
[  693.231401] wlan0: authenticated
[  693.231880] ath5k 0000:02:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[  693.231894] ath5k 0000:02:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[  693.232452] wlan0: associate with <MAC addr BKB102AP> (try 1/3)
[  693.340057] wlan0: associate with <MAC addr BKB102AP> (try 2/3)
[  693.444169] wlan0: associate with <MAC addr BKB102AP> (try 3/3)
[  693.548138] wlan0: association with <MAC addr BKB102AP> timed out
[  704.419134] wlan0: authenticate with <MAC addr BKB102AP>
[  704.423708] wlan0: send auth to <MAC addr BKB102AP> (try 1/3)
[  704.426959] wlan0: authenticated
[  704.427447] ath5k 0000:02:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[  704.427461] ath5k 0000:02:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[  704.429512] wlan0: associate with <MAC addr BKB102AP> (try 1/3)
[  704.532142] wlan0: associate with <MAC addr BKB102AP> (try 2/3)
[  704.636170] wlan0: associate with <MAC addr BKB102AP> (try 3/3)
[  704.740158] wlan0: association with <MAC addr BKB102AP> timed out

########## wireless info END ############
```

---

### Post by jeremy31 on 2014-09-08
I wonder if it would work on Ubuntu 12.04 live USB

---

