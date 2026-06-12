---
title: "Cannot Connect to WiFi After Upgrading to Ubuntu 16.04"
date: 2016-08-09
forum: Networking &amp; Wireless
---

### Post by geogunow on 2016-08-09
Recently I upgraded to Ubuntu 16.04 from 14.04 and now I am having issues connecting to the internet. Every time I try to connect to a wireless network, it tries to connect for a while and then gives up. At first not even the wired ethernet connection was working to connect to the internet. But then I read through these forums and added:

```
auto eth0
iface eth0 inet dhcp
```

to /etc/network/interfaces. Now I can connect via the wired connection but it is listed as "device not managed." However WiFi is still definitely broken and I have not yet been able to come across any solution to fix that yet.

I have gone to the Additional Drivers tab of Software & Updates. There is only one option and it does not appear to affect WiFi - it is listed as  "Unknown:Unkown". I have tried with the box checked for "Using Processor microcode firmware for Intel CPUs from intel-microcode (proprietary)" and "Do not use the device". It doesn't appear to impact anything. I've also restarted the network manager after each time.

I have also tried
```
sudo apt-get update
sudo apt-get install bcmwl-kernel-source
```
But that seemed to have no effect.

Here are my specs:
Computer: Lenovo X1 Carbon
Operating system: Ubuntu 16.04 LTS (I also dual boot with Windows 7, probably not important)
OS Type: 64-bit
Network controller: Intel Corporation Wireless 7260 (rev 83)

Now for the information dump....

Output of ifconfig:
```
eth0      Link encap:Ethernet  HWaddr 54:ee:75:26:23:62            inet addr:18.54.7.82  Bcast:18.54.255.255  Mask:255.255.0.0
          inet6 addr: fe80::56ee:75ff:fe26:2362/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:262127 errors:17 dropped:0 overruns:0 frame:12
          TX packets:11037 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:35966534 (35.9 MB)  TX bytes:2156256 (2.1 MB)
          Interrupt:20 Memory:f0500000-f0520000 


lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:18 errors:0 dropped:0 overruns:0 frame:0
          TX packets:18 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1 
          RX bytes:1314 (1.3 KB)  TX bytes:1314 (1.3 KB)


wlan0     Link encap:Ethernet  HWaddr 28:b2:bd:86:74:32  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)



```

Output of sudo lspci -v:
```
00:00.0 Host bridge: Intel Corporation Haswell-ULT DRAM Controller (rev 0b)    Subsystem: Lenovo Haswell-ULT DRAM Controller
    Flags: bus master, fast devsel, latency 0
    Capabilities: [e0] Vendor Specific Information: Len=0c <?>
    Kernel driver in use: hsw_uncore


00:02.0 VGA compatible controller: Intel Corporation Haswell-ULT Integrated Graphics Controller (rev 0b) (prog-if 00 [VGA controller])
    Subsystem: Lenovo Haswell-ULT Integrated Graphics Controller
    Flags: bus master, fast devsel, latency 0, IRQ 43
    Memory at f0000000 (64-bit, non-prefetchable) [size=4M]
    Memory at e0000000 (64-bit, prefetchable) [size=256M]
    I/O ports at 3000 [size=64]
    Expansion ROM at <unassigned> [disabled]
    Capabilities: [90] MSI: Enable+ Count=1/1 Maskable- 64bit-
    Capabilities: [d0] Power Management version 2
    Capabilities: [a4] PCI Advanced Features
    Kernel driver in use: i915
    Kernel modules: i915


00:03.0 Audio device: Intel Corporation Haswell-ULT HD Audio Controller (rev 0b)
    Subsystem: Lenovo Haswell-ULT HD Audio Controller
    Flags: bus master, fast devsel, latency 0, IRQ 47
    Memory at f0530000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: [50] Power Management version 2
    Capabilities: [60] MSI: Enable+ Count=1/1 Maskable- 64bit-
    Capabilities: [70] Express Root Complex Integrated Endpoint, MSI 00
    Kernel driver in use: snd_hda_intel
    Kernel modules: snd_hda_intel


00:14.0 USB controller: Intel Corporation 8 Series USB xHCI HC (rev 04) (prog-if 30 [XHCI])
    Subsystem: Lenovo 8 Series USB xHCI HC
    Flags: bus master, medium devsel, latency 0, IRQ 40
    Memory at f0520000 (64-bit, non-prefetchable) [size=64K]
    Capabilities: [70] Power Management version 2
    Capabilities: [80] MSI: Enable+ Count=1/8 Maskable- 64bit+
    Kernel driver in use: xhci_hcd


00:16.0 Communication controller: Intel Corporation 8 Series HECI #0 (rev 04)
    Subsystem: Lenovo 8 Series HECI
    Flags: bus master, fast devsel, latency 0, IRQ 44
    Memory at f0539000 (64-bit, non-prefetchable) [size=32]
    Capabilities: [50] Power Management version 3
    Capabilities: [8c] MSI: Enable+ Count=1/1 Maskable- 64bit+
    Kernel driver in use: mei_me
    Kernel modules: mei_me


00:16.3 Serial controller: Intel Corporation 8 Series HECI KT (rev 04) (prog-if 02 [16550])
    Subsystem: Lenovo 8 Series HECI KT
    Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 17
    I/O ports at 30b0 [size=8]
    Memory at f053f000 (32-bit, non-prefetchable) [size=4K]
    Capabilities: [c8] Power Management version 3
    Capabilities: [d0] MSI: Enable- Count=1/1 Maskable- 64bit+
    Kernel driver in use: serial


00:19.0 Ethernet controller: Intel Corporation Ethernet Connection I218-LM (rev 04)
    Subsystem: Lenovo ThinkPad X240
    Flags: bus master, fast devsel, latency 0, IRQ 41
    Memory at f0500000 (32-bit, non-prefetchable) [size=128K]
    Memory at f053e000 (32-bit, non-prefetchable) [size=4K]
    I/O ports at 3080 [size=32]
    Capabilities: [c8] Power Management version 2
    Capabilities: [d0] MSI: Enable+ Count=1/1 Maskable- 64bit+
    Capabilities: [e0] PCI Advanced Features
    Kernel driver in use: e1000e
    Kernel modules: e1000e


00:1b.0 Audio device: Intel Corporation 8 Series HD Audio Controller (rev 04)
    Subsystem: Lenovo 8 Series HD Audio Controller
    Flags: bus master, fast devsel, latency 0, IRQ 45
    Memory at f0534000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: [50] Power Management version 3
    Capabilities: [60] MSI: Enable+ Count=1/1 Maskable- 64bit+
    Capabilities: [70] Express Root Complex Integrated Endpoint, MSI 00
    Capabilities: [100] Virtual Channel
    Kernel driver in use: snd_hda_intel
    Kernel modules: snd_hda_intel


00:1c.0 PCI bridge: Intel Corporation 8 Series PCI Express Root Port 6 (rev e4) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0, IRQ 17
    Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
    I/O behind bridge: 00002000-00002fff
    Memory behind bridge: dfb00000-dfcfffff
    Prefetchable memory behind bridge: 00000000dfd00000-00000000dfefffff
    Capabilities: [40] Express Root Port (Slot+), MSI 00
    Capabilities: [80] MSI: Enable- Count=1/1 Maskable- 64bit-
    Capabilities: [90] Subsystem: Lenovo 8 Series PCI Express Root Port 6
    Capabilities: [a0] Power Management version 3
    Kernel driver in use: pcieport
    Kernel modules: shpchp


00:1c.1 PCI bridge: Intel Corporation 8 Series PCI Express Root Port 3 (rev e4) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0, IRQ 18
    Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
    Memory behind bridge: f0400000-f04fffff
    Capabilities: [40] Express Root Port (Slot+), MSI 00
    Capabilities: [80] MSI: Enable- Count=1/1 Maskable- 64bit-
    Capabilities: [90] Subsystem: Lenovo 8 Series PCI Express Root Port 3
    Capabilities: [a0] Power Management version 3
    Capabilities: [100] #00
    Capabilities: [200] L1 PM Substates
    Kernel driver in use: pcieport
    Kernel modules: shpchp


00:1d.0 USB controller: Intel Corporation 8 Series USB EHCI #1 (rev 04) (prog-if 20 [EHCI])
    Subsystem: Lenovo 8 Series USB EHCI
    Flags: bus master, medium devsel, latency 0, IRQ 23
    Memory at f053d000 (32-bit, non-prefetchable) [size=1K]
    Capabilities: [50] Power Management version 3
    Capabilities: [58] Debug port: BAR=1 offset=00a0
    Capabilities: [98] PCI Advanced Features
    Kernel driver in use: ehci-pci


00:1f.0 ISA bridge: Intel Corporation 8 Series LPC Controller (rev 04)
    Subsystem: Lenovo 8 Series LPC Controller
    Flags: bus master, medium devsel, latency 0
    Capabilities: [e0] Vendor Specific Information: Len=0c <?>
    Kernel driver in use: lpc_ich
    Kernel modules: lpc_ich


00:1f.2 SATA controller: Intel Corporation 8 Series SATA Controller 1 [AHCI mode] (rev 04) (prog-if 01 [AHCI 1.0])
    Subsystem: Lenovo 8 Series SATA Controller 1 [AHCI mode]
    Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 42
    I/O ports at 30a8 [size=8]
    I/O ports at 30bc [size=4]
    I/O ports at 30a0 [size=8]
    I/O ports at 30b8 [size=4]
    I/O ports at 3060 [size=32]
    Memory at f053c000 (32-bit, non-prefetchable) [size=2K]
    Capabilities: [80] MSI: Enable+ Count=1/1 Maskable- 64bit-
    Capabilities: [70] Power Management version 3
    Capabilities: [a8] SATA HBA v1.0
    Kernel driver in use: ahci
    Kernel modules: ahci


00:1f.3 SMBus: Intel Corporation 8 Series SMBus Controller (rev 04)
    Subsystem: Lenovo 8 Series SMBus Controller
    Flags: medium devsel, IRQ 10
    Memory at f0538000 (64-bit, non-prefetchable) [size=256]
    I/O ports at efa0 [size=32]
    Kernel modules: i2c_i801


03:00.0 Network controller: Intel Corporation Wireless 7260 (rev 83)
    Subsystem: Intel Corporation Dual Band Wireless-AC 7260
    Flags: bus master, fast devsel, latency 0, IRQ 46
    Memory at f0400000 (64-bit, non-prefetchable) [size=8K]
    Capabilities: [c8] Power Management version 3
    Capabilities: [d0] MSI: Enable+ Count=1/1 Maskable- 64bit+
    Capabilities: [40] Express Endpoint, MSI 00
    Capabilities: [100] Advanced Error Reporting
    Capabilities: [140] Device Serial Number 28-b2-bd-ff-ff-86-74-32
    Capabilities: [14c] Latency Tolerance Reporting
    Capabilities: [154] Vendor Specific Information: ID=cafe Rev=1 Len=014 <?>
    Kernel driver in use: iwlwifi
    Kernel modules: iwlwifi, wl



```

Output of lsmod:
```
Module                  Size  Used byrfcomm                 69632  0
ebtable_filter         16384  0
ebtables               36864  1 ebtable_filter
ip6table_filter        16384  0
ip6_tables             28672  1 ip6table_filter
iptable_filter         16384  0
ip_tables              24576  1 iptable_filter
x_tables               36864  5 ip6table_filter,ip_tables,iptable_filter,ebtables,ip6_tables
openafs               782336  2
bnep                   20480  2
snd_hda_codec_hdmi     53248  1
arc4                   16384  2
intel_rapl             20480  0
x86_pkg_temp_thermal    16384  0
intel_powerclamp       16384  0
coretemp               16384  0
crct10dif_pclmul       16384  0
crc32_pclmul           16384  0
aesni_intel           167936  0
aes_x86_64             20480  1 aesni_intel
lrw                    16384  1 aesni_intel
gf128mul               16384  1 lrw
glue_helper            16384  1 aesni_intel
uvcvideo               90112  0
ablk_helper            16384  1 aesni_intel
cryptd                 20480  2 aesni_intel,ablk_helper
videobuf2_vmalloc      16384  1 uvcvideo
videobuf2_memops       16384  1 videobuf2_vmalloc
videobuf2_v4l2         28672  1 uvcvideo
videobuf2_core         36864  2 uvcvideo,videobuf2_v4l2
wl                   6365184  0
v4l2_common            16384  1 videobuf2_v4l2
videodev              176128  4 uvcvideo,v4l2_common,videobuf2_core,videobuf2_v4l2
media                  24576  2 uvcvideo,videodev
iwlmvm                311296  0
mac80211              737280  1 iwlmvm
joydev                 20480  0
input_leds             16384  0
btusb                  45056  0
btrtl                  16384  1 btusb
serio_raw              16384  0
btbcm                  16384  1 btusb
btintel                16384  1 btusb
bluetooth             520192  29 bnep,btbcm,btrtl,btusb,rfcomm,btintel
iwlwifi               200704  1 iwlmvm
cfg80211              565248  4 wl,iwlwifi,mac80211,iwlmvm
snd_hda_codec_realtek    86016  1
snd_hda_codec_generic    77824  1 snd_hda_codec_realtek
snd_hda_intel          36864  5
snd_hda_codec         135168  4 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_hda_intel
snd_hda_core           73728  5 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_hda_codec,snd_hda_intel
lpc_ich                24576  0
snd_hwdep              16384  1 snd_hda_codec
shpchp                 36864  0
snd_pcm               106496  4 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel,snd_hda_core
mei_me                 36864  0
mei                    98304  1 mei_me
snd_seq_midi           16384  0
snd_seq_midi_event     16384  1 snd_seq_midi
snd_rawmidi            32768  1 snd_seq_midi
thinkpad_acpi          90112  1
nvram                  16384  1 thinkpad_acpi
snd_seq                69632  2 snd_seq_midi_event,snd_seq_midi
snd_seq_device         16384  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              32768  2 snd_pcm,snd_seq
snd                    81920  22 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec_generic,snd_hda_codec,snd_hda_intel,thinkpad_acpi,snd_seq_device
i2c_designware_platform    16384  0
i2c_designware_core    20480  1 i2c_designware_platform
mac_hid                16384  0
intel_rst              16384  0
soundcore              16384  1 snd
binfmt_misc            20480  1
kvm                   540672  0
irqbypass              16384  1 kvm
parport_pc             32768  0
ppdev                  20480  0
lp                     20480  0
parport                49152  3 lp,ppdev,parport_pc
autofs4                40960  2
i915                 1208320  6
psmouse               126976  0
i2c_algo_bit           16384  1 i915
ahci                   36864  2
drm_kms_helper        147456  1 i915
libahci                32768  1 ahci
syscopyarea            16384  1 drm_kms_helper
sysfillrect            16384  1 drm_kms_helper
sysimgblt              16384  1 drm_kms_helper
e1000e                237568  0
fb_sys_fops            16384  1 drm_kms_helper
drm                   364544  7 i915,drm_kms_helper
ptp                    20480  1 e1000e
pps_core               20480  1 ptp
wmi                    20480  0
fjes                   28672  0
video                  40960  2 i915,thinkpad_acpi



```



Output of the wireless info script
```

########## wireless info START ##########


Report from: 09 Aug 2016 12:25 EDT -0400


Booted last: 09 Aug 2016 00:00 EDT -0400


Script from: 08 Jul 2016 02:16 UTC +0000


##### release ###########################


Distributor ID:    Ubuntu
Description:    Ubuntu 16.04.1 LTS
Release:    16.04
Codename:    xenial


##### kernel ############################


Linux 4.4.0-34-generic #53-Ubuntu SMP Wed Jul 27 16:06:39 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux


Parameters: ro, quiet, splash, vt.handoff=7


##### desktop ###########################


Ubuntu


##### lspci #############################


00:19.0 Ethernet controller [0200]: Intel Corporation Ethernet Connection I218-LM [8086:155a] (rev 04)
    Subsystem: Lenovo ThinkPad X240 [17aa:2214]
    Kernel driver in use: e1000e


03:00.0 Network controller [0280]: Intel Corporation Wireless 7260 [8086:08b2] (rev 83)
    Subsystem: Intel Corporation Dual Band Wireless-AC 7260 [8086:c270]
    Kernel driver in use: iwlwifi


##### lsusb #############################


Bus 001 Device 003: ID 04f2:b3f5 Chicony Electronics Co., Ltd 
Bus 001 Device 002: ID 8087:8000 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 002 Device 003: ID 8087:07dc Intel Corp. 
Bus 002 Device 002: ID 138a:0017 Validity Sensors, Inc. Fingerprint Reader
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


##### PCMCIA card info ##################


##### rfkill ############################


0: tpacpi_bluetooth_sw: Bluetooth
    Soft blocked: no
    Hard blocked: no
1: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
2: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no


##### lsmod #############################


wl                   6365184  0
iwlmvm                311296  0
mac80211              737280  1 iwlmvm
iwlwifi               200704  1 iwlmvm
cfg80211              565248  4 wl,iwlwifi,mac80211,iwlmvm
wmi                    20480  0


##### interfaces ########################


auto lo
iface lo inet loopback
auto eth0
iface eth0 inet dhcp


##### ifconfig ##########################


eth0      Link encap:Ethernet  HWaddr <MAC 'eth0' [IF1]>  
          inet addr:18.54.7.82  Bcast:18.54.255.255  Mask:255.255.0.0
          inet6 addr: fe80::<IP6 'eth0' [IF1]>/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:546715 errors:18 dropped:0 overruns:0 frame:13
          TX packets:16826 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:58901376 (58.9 MB)  TX bytes:3942839 (3.9 MB)
          Interrupt:20 Memory:f0500000-f0520000 


wlan0     Link encap:Ethernet  HWaddr <MAC 'wlan0' [IF2]>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:2 errors:0 dropped:1 overruns:0 frame:0
          TX packets:23 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:382 (382.0 B)  TX bytes:3368 (3.3 KB)


##### iwconfig ##########################


lo        no wireless extensions.


eth0      no wireless extensions.


wlan0     IEEE 802.11abgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=22 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          


##### route #############################


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         18.54.0.1       0.0.0.0         UG    0      0        0 eth0
18.54.0.0       0.0.0.0         255.255.0.0     U     0      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0


##### resolv.conf #######################


nameserver 18.71.0.151
nameserver 18.70.0.160
nameserver 18.72.0.3
search mit.edu


##### network managers ##################


Installed:


    NetworkManager


Running:


root      2493     1  0 11:31 ?        00:00:02 /usr/sbin/NetworkManager --no-daemon


##### NetworkManager info ###############


GENERAL.DEVICE:                         wlan0
GENERAL.TYPE:                           wifi
GENERAL.NM-TYPE:                        NMDeviceWifi
GENERAL.VENDOR:                         Intel Corporation
GENERAL.PRODUCT:                        Wireless 7260 (Dual Band Wireless-AC 7260)
GENERAL.DRIVER:                         iwlwifi
GENERAL.DRIVER-VERSION:                 4.4.0-34-generic
GENERAL.FIRMWARE-VERSION:               16.242414.0
GENERAL.HWADDR:                         <MAC 'wlan0' [IF2]>
GENERAL.MTU:                            0
GENERAL.STATE:                          30 (disconnected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.1/0000:03:00.0/net/wlan0
GENERAL.IP-IFACE:                       
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     --
GENERAL.CON-UUID:                       --
GENERAL.CON-PATH:                       --
GENERAL.METERED:                        unknown
CAPABILITIES.CARRIER-DETECT:            no
CAPABILITIES.SPEED:                     unknown
CAPABILITIES.IS-SOFTWARE:               no
WIFI-PROPERTIES.WEP:                    yes
WIFI-PROPERTIES.WPA:                    yes
WIFI-PROPERTIES.WPA2:                   yes
WIFI-PROPERTIES.TKIP:                   yes
WIFI-PROPERTIES.CCMP:                   yes
WIFI-PROPERTIES.AP:                     yes
WIFI-PROPERTIES.ADHOC:                  yes
WIFI-PROPERTIES.2GHZ:                   yes
WIFI-PROPERTIES.5GHZ:                   yes
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{1,2,0}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   2a219cfc-4a37-4b06-8d74-e33db79518da | MIT SECURE
CONNECTIONS.AVAILABLE-CONNECTIONS[2]:   26cdb641-ee26-4ffa-a4fd-4ee494394ffa | MIT GUEST
CONNECTIONS.AVAILABLE-CONNECTIONS[3]:   c9b5f5db-9990-4715-88e3-887efa05a01d | MIT


GENERAL.DEVICE:                         eth0
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Intel Corporation
GENERAL.PRODUCT:                        Ethernet Connection I218-LM (ThinkPad X240)
GENERAL.DRIVER:                         e1000e
GENERAL.DRIVER-VERSION:                 3.2.6-k
GENERAL.FIRMWARE-VERSION:               0.6-4
GENERAL.HWADDR:                         <MAC 'eth0' [IF1]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          10 (unmanaged)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:19.0/net/eth0
GENERAL.IP-IFACE:                       eth0
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     no
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     --
GENERAL.CON-UUID:                       --
GENERAL.CON-PATH:                       --
GENERAL.METERED:                        unknown
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     1000 Mb/s
CAPABILITIES.IS-SOFTWARE:               no
WIRED-PROPERTIES.CARRIER:               on
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: 
IP4.ADDRESS[1]:                         18.54.7.82/16
IP4.GATEWAY:                            18.54.0.1
IP4.ROUTE[1]:                           dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000
IP6.ADDRESS[1]:                         fe80::<IP6 'eth0' [IF1]>/64
IP6.GATEWAY:                            

```


**UPDATE: Issue solved:**

I downloaded Wild Man's links [here]("https://ubuntuforums.org/showthread.php?t=2333291") and followed his instructions. At first it didn't work. But when I rebooted it actually connected to the wireless network (woot!). But wait, it still didn't work. Even though it said it was connected I couldn't reach any sites. Then I rebooted again (because hey it kind of worked the last time). And then on reboot Ubuntu somehow figured out something was up and started an auto-fix. Now it works. I have no idea what Ubuntu did during the reboot but it did something that brought a terminal screen that ran some stuff that fixed the issue.

---

### Post by howefield on 2016-08-09
Thread moved to the "*Networking & Wireless*" forum.

---

### Post by mlnease on 2017-06-16
> **howefield said:**
> Thread moved to the "*Networking & Wireless*" forum.

A link would be helpful, I think.

---

