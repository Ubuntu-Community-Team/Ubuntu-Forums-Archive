---
title: "Wifi connection is unstable"
date: 2013-12-23
forum: Networking &amp; Wireless
---

### Post by moreplavatel on 2013-12-23
Hello community! 
I need guidance for fixing my wifi connection. I've tried some recepies but nothing worked for me. I'm very bad informed about connection issues, so please have patience to explain me what to do.
My wifi falls after about 5 minutes after starting. It's different for each Network, at home it's fine (there was a problem, but it's gone somehow), but at university situation is bad. We have public and enterprise connetions here, public works for 5-10 minutes and stops, enterprise (protected EAP) works worse, it connected once and doesnt' work after that. 
I had no problem before - it wokred just fine. I used 13.04 when the problem started. After that I've tried 13.10 and now I'm using 12.04 - nothing get better. For a time I used Wicd and it worked little better, but problem remained. May be my problem is of hardware nature and I need to replace certain chip? How can I be sure about that?
My Notebook is Lenovo x120e, (I've installed SSD could it provoke this problem?) 
lspci 
```
00:00.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 14h Processor Root Complex
00:01.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Wrestler [Radeon HD 6310]
00:01.1 Audio device: Advanced Micro Devices, Inc. [AMD/ATI] Wrestler HDMI Audio
00:06.0 PCI bridge: Advanced Micro Devices, Inc. [AMD] Family 14h Processor Root Port
00:11.0 SATA controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 SATA Controller [AHCI mode]
00:12.0 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:12.2 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:13.0 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:13.2 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:14.0 SMBus: Advanced Micro Devices, Inc. [AMD/ATI] SBx00 SMBus Controller (rev 42)
00:14.2 Audio device: Advanced Micro Devices, Inc. [AMD/ATI] SBx00 Azalia (Intel HDA) (rev 40)
00:14.3 ISA bridge: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 LPC host controller (rev 40)
00:14.4 PCI bridge: Advanced Micro Devices, Inc. [AMD/ATI] SBx00 PCI to PCI Bridge (rev 40)
00:15.0 PCI bridge: Advanced Micro Devices, Inc. [AMD/ATI] SB700/SB800/SB900 PCI to PCI bridge (PCIE port 0)
00:15.1 PCI bridge: Advanced Micro Devices, Inc. [AMD/ATI] SB700/SB800/SB900 PCI to PCI bridge (PCIE port 1)
00:18.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 12h/14h Processor Function 0 (rev 43)
00:18.1 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 12h/14h Processor Function 1
00:18.2 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 12h/14h Processor Function 2
00:18.3 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 12h/14h Processor Function 3
00:18.4 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 12h/14h Processor Function 4
00:18.5 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 12h/14h Processor Function 6
00:18.6 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 12h/14h Processor Function 5
00:18.7 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 12h/14h Processor Function 7
01:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 03)
04:00.0 Network controller: Realtek Semiconductor Co., Ltd. RTL8188CE 802.11b/g/n WiFi Adapter (rev 01) 
```
iwconfig
```
eth0      no wireless extensions.


lo        no wireless extensions.


wlan0     IEEE 802.11bgn  ESSID:"EUSP-Network"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:27:22:F9:A9:35   
          Bit Rate=72.2 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          Link Quality=62/70  Signal level=-48 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:242   Missed beacon:0

```

lsmod
```
Module                  Size  Used by
joydev                 17613  0 
kvm                   455932  0 
arc4                   12573  2 
microcode              23017  0 
rtl8192ce              58733  0 
rtl8192c_common        49561  1 rtl8192ce
rtlwifi                81225  1 rtl8192ce
uvcvideo               82214  0 
videobuf2_core         40785  1 uvcvideo
videodev              130053  2 uvcvideo,videobuf2_core
snd_hda_codec_conexant    62464  1 
psmouse                97873  0 
videobuf2_vmalloc      13056  1 uvcvideo
serio_raw              13215  0 
videobuf2_memops       13202  1 videobuf2_vmalloc
mac80211              630977  3 rtl8192ce,rtl8192c_common,rtlwifi
snd_hda_codec_hdmi     37463  1 
snd_hda_intel          44339  5 
k10temp                13173  0 
snd_hda_codec         141761  3 snd_hda_codec_conexant,snd_hda_codec_hdmi,snd_hda_intel
snd_hwdep              13668  1 snd_hda_codec
cfg80211              525326  2 rtlwifi,mac80211
snd_seq_midi           13324  0 
snd_pcm               102477  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
sp5100_tco             13870  0 
i2c_piix4              13459  0 
snd_rawmidi            30417  1 snd_seq_midi
btusb                  22431  0 
thinkpad_acpi          81843  0 
snd_seq_midi_event     14899  1 snd_seq_midi
nvram                  14413  1 thinkpad_acpi
snd_seq                61930  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29989  2 snd_pcm,snd_seq
snd_seq_device         14497  3 snd_seq_midi,snd_rawmidi,snd_seq
fglrx                5294837  198 
snd                    69533  21 snd_hda_codec_conexant,snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,thinkpad_acpi,snd_seq,snd_timer,snd_seq_device
bnep                   18258  2 
rfcomm                 47864  12 
bluetooth             247165  24 btusb,bnep,rfcomm
parport_pc             28284  0 
ppdev                  17113  0 
soundcore              12680  1 snd
snd_page_alloc         18798  2 snd_hda_intel,snd_pcm
wmi                    19256  0 
video                  19652  0 
amd_iommu_v2           19198  1 fglrx
nls_iso8859_1          12713  1 
mac_hid                13253  0 
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
ums_realtek            18256  0 
usb_storage            61749  1 ums_realtek
ahci                   25879  4 
libahci                31606  1 ahci
r8169                  68716  0 

```
sudo lshw -C network
```

  *-network               
       description: Ethernet interface
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: eth0
       version: 03
       serial: 04:7d:7b:35:4c:1a
       size: 10Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=rtl_nic/rtl8168d-2.fw latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:43 ioport:3000(size=256) memory:f0004000-f0004fff memory:f0000000-f0003fff memory:f0020000-f003ffff
  *-network
       description: Wireless interface
       product: RTL8188CE 802.11b/g/n WiFi Adapter
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: wlan0
       version: 01
       serial: 60:d8:19:c6:c3:80
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rtl8192ce driverversion=3.8.0-34-generic firmware=N/A ip=192.168.4.118 latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn
       resources: irq:17 ioport:2000(size=256) memory:f0100000-f0103fff

```
iwlist scan
```
eth0      Interface doesn't support scanning.


lo        Interface doesn't support scanning.


wlan0     Scan completed :
          Cell 01 - Address: 00:27:22:F9:A9:35
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=60/70  Signal level=-50 dBm  
                    Encryption key:on
                    ESSID:"EUSP-Network"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000040bd7180
                    Extra: Last beacon: 350884ms ago
                    IE: Unknown: 000C455553502D4E6574776F726B
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030106
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
                    IE: Unknown: 32043048606C
                    IE: Unknown: 2D1ACC111BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1606001F00000000000000000000000000000000000000
                    IE: Unknown: DD180050F202010103000364000027A4000041435E0061322F00
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: Unknown: DD0A00037F04010002004000
                    IE: Unknown: DD1E00904C33CC111BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C3406001F00000000000000000000000000000000000000
                    IE: Unknown: DD0C00156D0001000000E5120014

```

---

### Post by ajgreeny on 2013-12-23
Lots of info and possible solutions at [http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=realtek+8188+wifi+driver&as_qdr=all&sa=Google+Search&lang=en](http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=realtek+8188+wifi+driver&as_qdr=all&sa=Google+Search&lang=en)

Sorry for simply throwing you a search page, but there are too many possible options to really give you a definite answer to your problem.

---

