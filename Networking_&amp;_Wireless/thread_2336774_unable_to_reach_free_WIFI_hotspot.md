---
title: "unable to reach free WIFI hotspot"
date: 2016-09-11
forum: Networking &amp; Wireless
---

### Post by phileconte on 2016-09-11
Hi,

I have got a problem with Kubuntu 16.04 but It was also the case with Kubuntu 14.04: 
- Using a Realtek[SIZE=3][FONT=arial] RTL8191SEvB Wireless LAN Controller, [/FONT][/SIZE]I can connect to WPA/WPA2 WIFI network and it works just fine
- However,when I try to connect to a WIFI network without WPA, the network controller indicate that I am connected but Firefox cannot go to any site. I'm not redirected to the identification page. Its occurs with all sites with no WPA security. I have another laptop with Kubuntu 16.04 and the connection on these networks work fine. I wonder if it is a driver problem or else ?After an extensive search, I have only retrieved old messages. 
Here are usual requests : 
```
philippe@philippe-Satellite-T230:~$ cat /etc/lsb-release 
DISTRIB_ID=Ubuntu 
DISTRIB_RELEASE=16.04 
DISTRIB_CODENAME=xenial 
DISTRIB_DESCRIPTION="Ubuntu 16.04.1 LTS" 
```
```
philippe@philippe-Satellite-T230:~$ lsusb 
Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub 
Bus 001 Device 003: ID 04f2:b1e4 Chicony Electronics Co., Ltd Toshiba Integrated Webcam 
Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub 
```
```
philippe@philippe-Satellite-T230:~$ lspci 
00:00.0 Host bridge: Intel Corporation Core Processor DRAM Controller (rev 02) 
00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 02) 
00:16.0 Communication controller: Intel Corporation 5 Series/3400 Series Chipset HECI Controller (rev 06) 
00:1a.0 USB controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05) 
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 05) 
00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 05) 
00:1c.1 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 2 (rev 05) 
00:1c.3 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 4 (rev 05) 
00:1c.4 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 5 (rev 05) 
00:1d.0 USB controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05) 
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev a5) 
00:1f.0 ISA bridge: Intel Corporation HM55 Chipset LPC Interface Controller (rev 05) 
00:1f.2 SATA controller: Intel Corporation 5 Series/3400 Series Chipset 4 port SATA AHCI Controller (rev 05) 00:1f.3 SMBus: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller (rev 05) 
00:1f.6 Signal processing controller: Intel Corporation 5 Series/3400 Series Chipset Thermal Subsystem (rev 05) 
01:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller (rev 05) 
06:00.0 Network controller: Realtek Semiconductor Co., Ltd. RTL8191SEvB Wireless LAN Controller (rev 10) 
10:00.0 System peripheral: JMicron Technology Corp. SD/MMC Host Controller (rev 20) 
10:00.2 SD Host controller: JMicron Technology Corp. Standard SD Host Controller (rev 20) 
10:00.3 System peripheral: JMicron Technology Corp. MS Host Controller (rev 20) 
10:00.4 System peripheral: JMicron Technology Corp. xD Host Controller (rev 20)ff:00.0 Host bridge: Intel Corporation Core Processor QuickPath Architecture Generic Non-core Registers (rev 05) 
ff:00.1 Host bridge: Intel Corporation Core Processor QuickPath Architecture System Address Decoder (rev 05) 
ff:02.0 Host bridge: Intel Corporation Core Processor QPI Link 0 (rev 05) 
ff:02.1 Host bridge: Intel Corporation 1st Generation Core i3/5/7 Processor QPI Physical 0 (rev 05) 
ff:02.2 Host bridge: Intel Corporation 1st Generation Core i3/5/7 Processor Reserved (rev 05) 
ff:02.3 Host bridge: Intel Corporation 1st Generation Core i3/5/7 Processor Reserved (rev 05)                                      
philippe@philippe-Satellite-T230:~$ lspci -nn | grep -i net                                                                        
01:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller [10e
c:8136] (rev 05)06:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8191SEvB Wireless LAN Controller [10ec:8172] (rev 10) 
philippe@philippe-Satellite-T230:~$ lspci -k                                                                                       
00:00.0 Host bridge: Intel Corporation Core Processor DRAM Controller (rev 02)                                                     
       Subsystem: Toshiba America Info Systems Core Processor DRAM Controller                                                     
       Kernel driver in use: agpgart-intel                                                                                        
00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 02) 
       Subsystem: Toshiba America Info Systems Core Processor Integrated Graphics Controller 
       Kernel driver in use: i915 00:16.0 Communication controller: Intel Corporation 5 Series/3400 Series Chipset HECI Controller (rev 06) 
       Subsystem: Toshiba America Info Systems 5 Series/3400 Series Chipset HECI Controller 
       Kernel driver in use: mei_me 
       Kernel modules: mei_me 
00:1a.0 USB controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05) 
       Subsystem: Toshiba America Info Systems 5 Series/3400 Series Chipset USB2 Enhanced Host Controller 
       Kernel driver in use: ehci-pci 
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 05) 
       Subsystem: Toshiba America Info Systems 5 Series/3400 Series Chipset High Definition Audio 
       Kernel driver in use: snd_hda_intel 
       Kernel modules: snd_hda_intel 
00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 05) 
       Kernel driver in use: pcieport 
       Kernel modules: shpchp 
00:1c.1 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 2 (rev 05) 
       Kernel driver in use: pcieport 
       Kernel modules: shpchp 
00:1c.3 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 4 (rev 05) 
       Kernel driver in use: pcieport 
       Kernel modules: shpchp 
00:1c.4 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 5 (rev 05) 
       Kernel driver in use: pcieport 
       Kernel modules: shpchp 
00:1d.0 USB controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05) 
       Subsystem: Toshiba America Info Systems 5 Series/3400 Series Chipset USB2 Enhanced Host Controller 
       Kernel driver in use: ehci-pci 
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev a5) 
00:1f.0 ISA bridge: Intel Corporation HM55 Chipset LPC Interface Controller (rev 05) 
       Subsystem: Toshiba America Info Systems HM55 Chipset LPC Interface Controller 
       Kernel driver in use: lpc_ich 
       Kernel modules: lpc_ich 
00:1f.2 SATA controller: Intel Corporation 5 Series/3400 Series Chipset 4 port SATA AHCI Controller (rev 05) 
       Subsystem: Toshiba America Info Systems 5 Series/3400 Series Chipset 4 port SATA AHCI Controller 
       Kernel driver in use: ahci 
       Kernel modules: ahci 
00:1f.3 SMBus: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller (rev 05) 
       Subsystem: Toshiba America Info Systems 5 Series/3400 Series Chipset SMBus Controller 
       Kernel modules: i2c_i801 
00:1f.6 Signal processing controller: Intel Corporation 5 Series/3400 Series Chipset Thermal Subsystem (rev 05) 
       Subsystem: Toshiba America Info Systems 5 Series/3400 Series Chipset Thermal Subsystem 
       Kernel modules: intel_ips 
01:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller (rev 05) 
       Subsystem: Toshiba America Info Systems RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller 
       Kernel driver in use: r8169 
       Kernel modules: r8169 
06:00.0 Network controller: Realtek Semiconductor Co., Ltd. RTL8191SEvB Wireless LAN Controller (rev 10) 
       Subsystem: Realtek Semiconductor Co., Ltd. RTL8191SEvB Wireless LAN Controller 
       Kernel driver in use: rtl8192se 
       Kernel modules: rtl8192se 
10:00.0 System peripheral: JMicron Technology Corp. SD/MMC Host Controller (rev 20) 
       Subsystem: Toshiba America Info Systems SD/MMC Host Controller 
       Kernel driver in use: sdhci-pci 
       Kernel modules: sdhci_pci 
10:00.2 SD Host controller: JMicron Technology Corp. Standard SD Host Controller (rev 20) 
       Subsystem: Toshiba America Info Systems Standard SD Host Controller 
       Kernel modules: sdhci_pci 
10:00.3 System peripheral: JMicron Technology Corp. MS Host Controller (rev 20) 
       Subsystem: Toshiba America Info Systems MS Host Controller 
       Kernel driver in use: jmb38x_ms 
       Kernel modules: jmb38x_ms 
10:00.4 System peripheral: JMicron Technology Corp. xD Host Controller (rev 20) 
       Subsystem: Toshiba America Info Systems xD Host Controller 
ff:00.0 Host bridge: Intel Corporation Core Processor QuickPath Architecture Generic Non-core Registers (rev 05) 
       Subsystem: Intel Corporation Core Processor QuickPath Architecture Generic Non-core Registers 
ff:00.1 Host bridge: Intel Corporation Core Processor QuickPath Architecture System Address Decoder (rev 05) 
       Subsystem: Intel Corporation Core Processor QuickPath Architecture System Address Decoder 
ff:02.0 Host bridge: Intel Corporation Core Processor QPI Link 0 (rev 05)         Subsystem: Intel Corporation Core Processor QPI Link 0 
ff:02.1 Host bridge: Intel Corporation 1st Generation Core i3/5/7 Processor QPI Physical 0 (rev 05) 
       Subsystem: Intel Corporation 1st Generation Core i3/5/7 Processor QPI Physical 0 
ff:02.2 Host bridge: Intel Corporation 1st Generation Core i3/5/7 Processor Reserved (rev 05) 
       Subsystem: Intel Corporation 1st Generation Core i3/5/7 Processor Reserved ff:02.3 Host bridge: Intel Corporation 1st Generation Core i3/5/7 Processor Reserved (rev 05) 
       Subsystem: Intel Corporation 1st Generation Core i3/5/7 Processor Reserved 
```
```
philippe@philippe-Satellite-T230:~$ sudo lshw -C network 
[sudo] password for philippe:  
 *-network                
      description: Ethernet interface 
      product: RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller 
      vendor: Realtek Semiconductor Co., Ltd. 
      physical id: 0 
      bus info: pci@0000:01:00.0 
      logical name: enp1s0 
      version: 05 
      serial: 88:ae:1d:4d:47:8f 
      size: 10Mbit/s 
      capacity: 100Mbit/s 
      width: 64 bits 
      clock: 33MHz 
      capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegot
iation 
      configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=rtl_nic/rtl8168e
-2.fw latency=0 link=no multicast=yes port=MII speed=10Mbit/s 
      resources: irq:25 ioport:6000(size=256) memory:d0404000-d0404fff memory:d0400000-d0403fff*-network 
      description: Wireless interface 
      product: RTL8191SEvB Wireless LAN Controller 
      vendor: Realtek Semiconductor Co., Ltd. 
      physical id: 0 
      bus info: pci@0000:06:00.0 
      logical name: wlp6s0 
      version: 10 
      serial: 00:26:4d:cb:c6:b2 
      width: 32 bits 
      clock: 33MHz 
      capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless 
      configuration: broadcast=yes driver=rtl8192se driverversion=4.4.0-36-generic firmware=N/A ip=192.168.43.165 latency=0 link=
yes multicast=yes wireless=IEEE 802.11bgn 
      resources: irq:17 ioport:4000(size=256) memory:d3600000-d3603fff  


```
```
philippe@philippe-Satellite-T230:~$  lsmod 
Module                  Size  Used by 
nls_iso8859_1          16384  0 
uas                    24576  0 
usb_storage            69632  1 uas 
drbg                   32768  1 
ansi_cprng             16384  0 
ctr                    16384  1 
ccm                    20480  1 
binfmt_misc            20480  1 
intel_powerclamp       16384  0 
coretemp               16384  0 
arc4                   16384  2 
rtl8192se              65536  0 
rtl_pci                28672  1 rtl8192se 
rtlwifi                77824  2 rtl_pci,rtl8192se 
joydev                 20480  0 
uvcvideo               90112  0 
mac80211              737280  3 rtl_pci,rtlwifi,rtl8192se 
input_leds             16384  0 
videobuf2_vmalloc      16384  1 uvcvideo 
serio_raw              16384  0 
videobuf2_memops       16384  1 videobuf2_vmalloc 
videobuf2_v4l2         28672  1 uvcvideo 
videobuf2_core         36864  2 uvcvideo,videobuf2_v4l2 
v4l2_common            16384  1 videobuf2_v4l2 
videodev              176128  4 uvcvideo,v4l2_common,videobuf2_core,videobuf2_v4l2 
media                  24576  2 uvcvideo,videodev 
cfg80211              565248  2 mac80211,rtlwifi 
lpc_ich                24576  0 
jmb38x_ms              20480  0 
memstick               20480  1 jmb38x_ms 
snd_hda_codec_hdmi     53248  1 
snd_hda_codec_realtek    86016  1 
snd_hda_codec_generic    77824  1 snd_hda_codec_realtek 
snd_hda_intel          36864  3 
toshiba_acpi           40960  0 
sparse_keymap          16384  1 toshiba_acpi 
wmi                    20480  1 toshiba_acpi 
snd_hda_codec         135168  4 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_hda_intel 
toshiba_haps           16384  0 
snd_hda_core           73728  5 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_hda_codec,snd_hda_intel 
snd_hwdep              16384  1 snd_hda_codec 
snd_pcm               106496  4 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel,snd_hda_core 
snd_seq_midi           16384  0 
snd_seq_midi_event     16384  1 snd_seq_midi 
snd_rawmidi            32768  1 snd_seq_midi 
acpi_als               16384  0 
snd_seq                69632  2 snd_seq_midi_event,snd_seq_midi 
ene_ir                 20480  0 
kfifo_buf              16384  1 acpi_als 
snd_seq_device         16384  3 snd_seq,snd_rawmidi,snd_seq_midi 
rc_core                28672  1 ene_ir 
snd_timer              32768  2 snd_pcm,snd_seq 
industrialio           57344  2 acpi_als,kfifo_buf 
toshiba_bluetooth      16384  0 
snd                    81920  17 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_
codec_generic,snd_hda_codec,snd_hda_intel,snd_seq_device 
mei_me                 36864  0 
mei                    98304  1 mei_me 
soundcore              16384  1 snd 
shpchp                 36864  0 
mac_hid                16384  0 
parport_pc             32768  0 
ppdev                  20480  0 
lp                     20480  0 
parport                49152  3 lp,ppdev,parport_pc 
autofs4                40960  2 
psmouse               126976  0 
intel_ips              20480  0 
ahci                   36864  3 
libahci                32768  1 ahci 
sdhci_pci              28672  0 
sdhci                  45056  1 sdhci_pci 
r8169                  81920  0 
mii                    16384  1 r8169 
fjes                   28672  0 
i915                 1208320  15 
video                  40960  2 i915,toshiba_acpi 
i2c_algo_bit           16384  1 i915 
drm_kms_helper        147456  1 i915 
syscopyarea            16384  1 drm_kms_helper 
sysfillrect            16384  1 drm_kms_helper 
sysimgblt              16384  1 drm_kms_helper 
fb_sys_fops            16384  1 drm_kms_helper 
drm                   364544  17 i915,drm_kms_helper 
```
```
philippe@philippe-Satellite-T230:~$ iwconfig 
lo        no wireless extensions. 

wlp6s0    IEEE 802.11bgn  ESSID:"portable "   
         Mode:Managed  Frequency:2.462 GHz  Access Point: EC:9B:F3:C6:DA:9E    
         Bit Rate=72.2 Mb/s   Tx-Power=20 dBm    
         Retry short limit:7   RTS thr=2347 B   Fragment thr:off 
         Power Management:on 
         Link Quality=70/70  Signal level=-30 dBm   
         Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0 
         Tx excessive retries:0  Invalid misc:455   Missed beacon:0 

enp1s0    no wireless extensions. 

philippe@philippe-Satellite-T230:~$ ifconfig 
enp1s0    Link encap:Ethernet  HWaddr 88:ae:1d:4d:47:8f   
         UP BROADCAST MULTICAST  MTU:1500  Metric:1 
         RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
         TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 
         collisions:0 txqueuelen:1000  
         RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B) 

lo        Link encap:Local Loopback   
         inet addr:127.0.0.1  Mask:255.0.0.0 
         inet6 addr: ::1/128 Scope:Host 
         UP LOOPBACK RUNNING  MTU:65536  Metric:1 
         RX packets:113107 errors:0 dropped:0 overruns:0 frame:0 
         TX packets:113107 errors:0 dropped:0 overruns:0 carrier:0 
         collisions:0 txqueuelen:1  
         RX bytes:6475692 (6.4 MB)  TX bytes:6475692 (6.4 MB) 

wlp6s0    Link encap:Ethernet  HWaddr 00:26:4d:cb:c6:b2   
         inet addr:192.168.43.165  Bcast:192.168.43.255  Mask:255.255.255.0 
         inet6 addr: fe80::e19a:11f8:f585:7115/64 Scope:Link 
         UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1 
         RX packets:4048496 errors:0 dropped:0 overruns:0 frame:0 
         TX packets:2050871 errors:0 dropped:0 overruns:0 carrier:0 
         collisions:0 txqueuelen:1000  
         RX bytes:5888111271 (5.8 GB)  TX bytes:357205236 (357.2 MB) 

```
```
philippe@philippe-Satellite-T230:~$ sudo iwlist scan 
lo        Interface doesn't support scanning. 

wlp6s0    Scan completed : 
         Cell 01 - Address: EC:9B:F3:C6:DA:9E 
                   Channel:11 
                   Frequency:2.462 GHz (Channel 11) 
                   Quality=70/70  Signal level=-32 dBm   
                   Encryption key:on 
                   ESSID:"portable " 
                   Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s 
                             24 Mb/s; 36 Mb/s; 54 Mb/s 
                   Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s 
                   Mode:Master 
                   Extra:tsf=0000000068fcf817 
                   Extra: Last beacon: 96572ms ago 
                   IE: Unknown: 0009706F727461626C6520 
                   IE: Unknown: 010882848B962430486C 
                   IE: Unknown: 03010B 
                   IE: Unknown: 2A0100 
                   IE: Unknown: 32040C121860 
                   IE: Unknown: 2D1A2D0017FFFF000000000000000000000000000000000000000000 
                   IE: Unknown: 3D160B081500000000000000000000000000000000000000 
                   IE: Unknown: 7F080400008001000040 
                   IE: Unknown: DD050016328000 
                   IE: Unknown: DD1E00904C0408BF0C3258810FFAFF0000FAFF0000C005000B000000C3020000 
                   IE: Unknown: DD090010180201001C0000 
                   IE: WPA Version 1 
                       Group Cipher : TKIP 
                       Pairwise Ciphers (2) : CCMP TKIP 
                       Authentication Suites (1) : PSK 
                   IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00 

enp1s0    Interface doesn't support scanning. philippe@philippe-Satellite-T230:~$ uname -r -m  
4.4.0-36-generic x86_64 
```
```
philippe@philippe-Satellite-T230:~$ cat  /etc/network/interfaces 
# interfaces(5) file used by ifup(8) and ifdown(8) 
auto lo 
iface lo inet loopback 
```
```
philippe@philippe-Satellite-T230:~$ nmcli c
NAME                UUID                                  TYPE             DEVICE 
CHU-PUBLIC          24f82614-84c0-4e19-9011-db6164312809  802-11-wireless  wlp6s0 
MAISON              0a4f7c66-1db9-4993-9743-51391c8d2f31  802-11-wireless  --     
SFR WiFi FON        2d8a8855-2411-48dd-addf-ed99f779e1c1  802-11-wireless  --     
Wired connection 1  d5e694c6-2e06-49af-8591-3838ffe4605a  802-3-ethernet   --     
portable            5922b47b-f993-47c9-91ef-37c69ea03b8f  802-11-wireless  --     
univ-nantes         40958753-fa8a-4d5f-90d5-5a17876fa851  802-11-wireless  --     
philippe@philippe-Satellite-T230:~$ nmcli c
NAME                UUID                                  TYPE             DEVICE 
portable            5922b47b-f993-47c9-91ef-37c69ea03b8f  802-11-wireless  wlp6s0 
CHU-PUBLIC          24f82614-84c0-4e19-9011-db6164312809  802-11-wireless  --     
MAISON              0a4f7c66-1db9-4993-9743-51391c8d2f31  802-11-wireless  --     
SFR WiFi FON        2d8a8855-2411-48dd-addf-ed99f779e1c1  802-11-wireless  --     
Wired connection 1  d5e694c6-2e06-49af-8591-3838ffe4605a  802-3-ethernet   --     
univ-nantes         40958753-fa8a-4d5f-90d5-5a17876fa851  802-11-wireless  --     
```
Here is the nmcli report with first connection to CHU-PUBLIC. Although it declare that there is a full connection, I'm unable to reach any site. After that, I connect to portable and all works fine.
```
philippe@philippe-Satellite-T230:~$ nmcli m
wlp6s0: connection failed
Connectivity is now 'none'
Networkmanager is now in the 'disconnected' state                                                    
wlp6s0: disconnected                                                                                 
There's no primary connection
Networkmanager is now in the 'connecting' state
wlp6s0: connecting (configuring)                                                                     
wlp6s0: using connection 'CHU-PUBLIC'
Connectivity is now 'full'
'CHU-PUBLIC' is now the primary connection
Networkmanager is now in the 'connected' state
wlp6s0: connected                                                                                    
wlp6s0: unmanaged
Connectivity is now 'none'
There's no primary connection
Networkmanager is now in the 'asleep' state
wlp6s0: unavailable
Networkmanager is now in the 'disconnected' state
wlp6s0: disconnected                                                                                 
Networkmanager is now in the 'connecting' state
wlp6s0: connecting (need authentication)                                                             
wlp6s0: using connection 'portable '
portable : connection profile changed
wlp6s0: connecting (configuring)
wlp6s0: connecting (getting IP configuration)                                                        
Connectivity is now 'full'
'portable ' is now the primary connection
Networkmanager is now in the 'connected' state
wlp6s0: connected                                                                                    
portable : connection profile changed
wlp6s0: deactivating
Connectivity is now 'none'
Networkmanager is now in the 'disconnecting' state
wlp6s0: disconnected
There's no primary connection
Networkmanager is now in the 'disconnected' state
wlp6s0: connecting (prepare)
wlp6s0: using connection 'CHU-PUBLIC'
Networkmanager is now in the 'connecting' state
wlp6s0: connecting (configuring)
wlp6s0: connecting (getting IP configuration)
wlp6s0: connecting (checking IP connectivity)
wlp6s0: connecting (starting secondary connections)
Connectivity is now 'full'
'CHU-PUBLIC' is now the primary connection
Networkmanager is now in the 'connected' state
wlp6s0: connected
wlp6s0: deactivating
Connectivity is now 'none'
Networkmanager is now in the 'disconnecting' state
There's no primary connection
Networkmanager is now in the 'disconnected' state
wlp6s0: using connection 'portable '
wlp6s0: connecting (prepare)
Networkmanager is now in the 'connecting' state
wlp6s0: connecting (need authentication)
portable : connection profile changed
wlp6s0: connecting (configuring)
wlp6s0: connecting (getting IP configuration)
wlp6s0: connecting (checking IP connectivity)
wlp6s0: connecting (starting secondary connections)
Connectivity is now 'full'
'portable ' is now the primary connection
Networkmanager is now in the 'connected' state
wlp6s0: connected
```
any help would be greatly appreciated !

---

### Post by wildmanne39 on 2016-09-11
To be honest that driver has been an issue in the past and has trouble connecting to some routers with certain settings so if you can not changed the settings we may not be able to make it work in those locations but we can try please click on the wireless script in my signature and follow the directions for running the script and posting the results here one for when it is working and one for when it is not.
Thanks

---

### Post by phileconte on 2016-09-11
Hi, thanks for your message. As requested, the two files :

- one (wireless-info_not_working), while "connected"on a non secured network, thus not working
 - one (wireless-info_working), while connected to a WPA secured network, thus working

sincerely[ATTACH]271087[/ATTACH][ATTACH]271088[/ATTACH]

---

### Post by Keith_Helms on 2016-09-11
You may genuinely have some kind of system configuration issue, but I also frequently have problems with Firefox when i connect to some network at an RV park that is unsecured, but runs you through a "I agree to the usage terms" screen.  The symptom is exactly what you describe.  I'll click on some website and nothing will happen.  It appears Firefox's cache is getting in the way.  I usually get the "terms" page to come up and save its cookie by browsing to some site I haven't visited in a while and which is no longer in cache.  You could also try Holding the shift key down while clicking on reload for the page that wouldn't display.  That is supposed to bypass cache and retrieve a fresh copy of the page.

---

### Post by wildmanne39 on 2016-09-11
I missed this earlier > I'm not redirected to the identification page
it does sound like an issue with firefox, I have that issue to sometimes it works and sometimes it does not.

I do not see any reason your device will not connect but it can not if it is not redirected I use chrome when I am needing to connect to a page to sign on.

---

### Post by phileconte on 2016-09-11
Thanks for your two responses. I'll try your solution and tell you what will happened.

---

### Post by phileconte on 2016-09-13
Hi, I've tried the your solutions but it doesn't work at all. Chrome doesn't connect. I have tried with a Kubuntu live CD and connection was functional. I will provide the WIFI script results within few hours.

---

### Post by phileconte on 2016-09-13
Hi,

the situation become more complicated because I'm unable now  to connect via a WPA secured network (MAISON)  and only via another one  (portable). Attached the wireless_info files and another using a live session
- WPA (MAISON) not working
- WPA (portable) working
- WPA (MAISON) working using a live session

Thanks for your help

---

### Post by wildmanne39 on 2016-09-13
Let's reset your name servers and see if that helps like I think it will:
```
sudo dpkg-reconfigure resolvconf
```
and then answer [COLOR="#FF0000"]Yes[/COLOR] to the "Prepare /etc/resolv.conf for dynamic updates?" question and [COLOR="#FF0000"]No[/COLOR] to the one about temporarily appending your existing config to the dynamic one, then reboot.
We are just going to make one change at a time for now.

---

### Post by phileconte on 2016-09-14
Hi, thanks for the tip,

I'm now able to connect to a WPA secured network, that's great, thanks a lot. I'll try to connect to not secured network as early as possible

---

### Post by phileconte on 2016-09-14
I've tried to connect to a network secured by login/psswd that doesn't work before and now, no problem.! 

Thanks again for your time and your advices

---

### Post by wildmanne39 on 2016-09-14
So it is working as expected that is great.
Enjoy!

---

### Post by phileconte on 2016-09-15
Hi again,

not a big problem but I had to run once again  resolvconf today because I was unable to connect to a network. After  that, connection works. Any idea ?

---

### Post by wildmanne39 on 2016-09-15
I thought when that command was ran it would make the changes permanent, did it only reset after you rebooted? if so you can set the dns nameserver to what you want in network manager that way the changes will not be overwritten for sure unless something is really wrong.

I use google dns because it is faster then any others that I have tried it is [COLOR="#000080"]8.8.8.8,8.8.4.4[/COLOR] that is how you type it in.
Click on network-manager -> Edit connections 
- click on your wireless network, then click edit
- go to IPv4 Settings tab.
- Select Method: Automatic (DHCP) addreses only
- then add nameserver in DNS Servers, save and close, refer to the screenshot for help.

---

