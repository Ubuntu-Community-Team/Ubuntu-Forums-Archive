---
title: "Wifi Hardware no longer toggleable"
date: 2014-07-19
forum: Networking &amp; Wireless
---

### Post by matthew44 on 2014-07-19
Hello, all. Im quite new to Ubuntu and Linux all in itself.

So, a while ago my father worked in a school district that gave out PCs to every staff member, it being a HP Compaq 6715b has a built in WiFi receiver. I recently upgraded from Vista to Linux as Vista got slow and when my father left he had no admin powers on this PC.

Anyway, that Wifi receiver has a touch button above the keyboard to activate and de-activate it (even though the rest work but have no function). It seems after upgrading to Ubuntu 13.04 I no longer can toggle the receiver. Even if I go and configure a Wifi Network with my router's IP, Mac address, and such it cannot connect let alone turn the hardware on. I hope I can fix this as I wish to get more time out of this laptop. 

P.S: I hope its just a driver problem or something of that sort, honestly.

EDIT: I can get it enabled if I hit the Bluetooth on a few times.. But other times the Bluetooth toggle is grayed out and untoggle-able, oh. Is there a way to have Ubuntu look for all/any Wifi network connections?

---

### Post by kc1di on 2014-07-19
Hi matthew44 and Welcome to Ubuntu, 

We could use a little more information about which wireless card this machine uses. 
if you could go to a terminal and issue the following commands and post the outputs here it would be helpful.
```
lshw
lspci
lsmod
``` 
do them one at a time.

---

### Post by matthew44 on 2014-07-19
```
lshw results:
PCI (sysfs)  
luczynskilaptop           
    description: Computer
    width: 64 bits
    capabilities: vsyscall32
  *-core
       description: Motherboard
       physical id: 0
     *-memory
          description: System memory
          physical id: 0
          size: 1876MiB
     *-cpu
          product: AMD Turion(tm) 64 X2 Mobile Technology TL-52
          vendor: Advanced Micro Devices [AMD]
          physical id: 1
          bus info: cpu@0
          size: 1600MHz
          capacity: 1600MHz
          width: 64 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt rdtscp x86-64 3dnowext 3dnow rep_good nopl extd_apicid pni cx16 lahf_lm cmp_legacy svm extapic cr8_legacy cpufreq
     *-pci:0
          description: Host bridge
          product: RS690 Host Bridge
          vendor: Advanced Micro Devices, Inc. [AMD/ATI]
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 00
          width: 32 bits
          clock: 66MHz
          configuration: latency=64
        *-pci:0
             description: PCI bridge
             product: RS690 PCI to PCI Bridge (Internal gfx)
             vendor: Advanced Micro Devices, Inc. [AMD/ATI]
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pci normal_decode bus_master cap_list
             resources: ioport:4000(size=4096) memory:d0400000-d05fffff ioport:c0000000(size=134217728)
           *-display
                description: VGA compatible controller
                product: RS690M [Radeon Xpress 1200/1250/1270]
                vendor: Advanced Micro Devices, Inc. [AMD/ATI]
                physical id: 5
                bus info: pci@0000:01:05.0
                version: 00
                width: 64 bits
                clock: 33MHz
                capabilities: vga_controller bus_master cap_list rom
                configuration: driver=radeon latency=64
                resources: irq:43 memory:c0000000-c7ffffff memory:d0400000-d040ffff ioport:4000(size=256) memory:d0500000-d05fffff
        *-pci:1
             description: PCI bridge
             product: Advanced Micro Devices, Inc. [AMD/ATI]
             vendor: Advanced Micro Devices, Inc. [AMD/ATI]
             physical id: 4
             bus info: pci@0000:00:04.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:40 memory:d0000000-d00fffff
           *-network
                description: Ethernet interface
                product: NetLink BCM5787M Gigabit Ethernet PCI Express
                vendor: Broadcom Corporation
                physical id: 0
                bus info: pci@0000:10:00.0
                logical name: eth0
                version: 02
                serial: 00:1a:4b:88:f2:64
                size: 1Gbit/s
                capacity: 1Gbit/s
                width: 64 bits
                clock: 33MHz
                capabilities: bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.132 duplex=full firmware=sb v2.09 ip=192.168.1.12 latency=0 link=yes multicast=yes port=twisted pair speed=1Gbit/s
                resources: irq:44 memory:d0000000-d000ffff
        *-pci:2
             description: PCI bridge
             product: RS690 PCI to PCI Bridge (PCI Express Port 1)
             vendor: Advanced Micro Devices, Inc. [AMD/ATI]
             physical id: 5
             bus info: pci@0000:00:05.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:41 ioport:2000(size=8192) memory:cc000000-cfffffff
        *-pci:3
             description: PCI bridge
             product: RS690 PCI to PCI Bridge (PCI Express Port 2)
             vendor: Advanced Micro Devices, Inc. [AMD/ATI]
             physical id: 6
             bus info: pci@0000:00:06.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:42 memory:c8000000-c80fffff
           *-network
                description: Network controller
                product: BCM4311 802.11a/b/g
                vendor: Broadcom Corporation
                physical id: 0
                bus info: pci@0000:30:00.0
                version: 02
                width: 64 bits
                clock: 33MHz
                capabilities: cap_list
                configuration: driver=wl latency=0
                resources: irq:0 memory:c8000000-c8003fff
        *-storage
             description: SATA controller
             product: SB600 Non-Raid-5 SATA
             vendor: Advanced Micro Devices, Inc. [AMD/ATI]
             physical id: 12
             bus info: pci@0000:00:12.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: storage ahci_1.0 bus_master cap_list
             configuration: driver=ahci latency=64
             resources: irq:16 ioport:9000(size=8) ioport:9008(size=4) ioport:9010(size=8) ioport:5018(size=4) ioport:5020(size=16) memory:d0609000-d06093ff
        *-usb:0
             description: USB controller
             product: SB600 USB (OHCI0)
             vendor: Advanced Micro Devices, Inc. [AMD/ATI]
             physical id: 13
             bus info: pci@0000:00:13.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ohci bus_master
             configuration: driver=ohci-pci latency=64
             resources: irq:23 memory:d0601000-d0601fff
        *-usb:1
             description: USB controller
             product: SB600 USB (OHCI1)
             vendor: Advanced Micro Devices, Inc. [AMD/ATI]
             physical id: 13.1
             bus info: pci@0000:00:13.1
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ohci bus_master
             configuration: driver=ohci-pci latency=64
             resources: irq:17 memory:d0602000-d0602fff
        *-usb:2
             description: USB controller
             product: SB600 USB (OHCI2)
             vendor: Advanced Micro Devices, Inc. [AMD/ATI]
             physical id: 13.2
             bus info: pci@0000:00:13.2
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ohci bus_master
             configuration: driver=ohci-pci latency=64
             resources: irq:17 memory:d0603000-d0603fff
        *-usb:3
             description: USB controller
             product: SB600 USB (OHCI3)
             vendor: Advanced Micro Devices, Inc. [AMD/ATI]
             physical id: 13.3
             bus info: pci@0000:00:13.3
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ohci bus_master
             configuration: driver=ohci-pci latency=64
             resources: irq:17 memory:d0604000-d0604fff
        *-usb:4
             description: USB controller
             product: SB600 USB (OHCI4)
             vendor: Advanced Micro Devices, Inc. [AMD/ATI]
             physical id: 13.4
             bus info: pci@0000:00:13.4
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ohci bus_master
             configuration: driver=ohci-pci latency=64
             resources: irq:17 memory:d0605000-d0605fff
        *-usb:5
             description: USB controller
             product: SB600 USB Controller (EHCI)
             vendor: Advanced Micro Devices, Inc. [AMD/ATI]
             physical id: 13.5
             bus info: pci@0000:00:13.5
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ehci bus_master cap_list
             configuration: driver=ehci-pci latency=64
             resources: irq:23 memory:d0606000-d06060ff
        *-serial
             description: SMBus
             product: SBx00 SMBus Controller
             vendor: Advanced Micro Devices, Inc. [AMD/ATI]
             physical id: 14
             bus info: pci@0000:00:14.0
             version: 14
             width: 32 bits
             clock: 66MHz
             capabilities: cap_list
             configuration: driver=piix4_smbus latency=0
             resources: irq:0 ioport:8200(size=16)
        *-ide
             description: IDE interface
             product: SB600 IDE
             vendor: Advanced Micro Devices, Inc. [AMD/ATI]
             physical id: 14.1
             bus info: pci@0000:00:14.1
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ide bus_master
             configuration: driver=pata_atiixp latency=64
             resources: irq:16 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:5040(size=16)
        *-multimedia
             description: Audio device
             product: SBx00 Azalia (Intel HDA)
             vendor: Advanced Micro Devices, Inc. [AMD/ATI]
             physical id: 14.2
             bus info: pci@0000:00:14.2
             version: 00
             width: 64 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=snd_hda_intel latency=64
             resources: irq:16 memory:84000000-84003fff
        *-isa
             description: ISA bridge
             product: SB600 PCI to LPC Bridge
             vendor: Advanced Micro Devices, Inc. [AMD/ATI]
             physical id: 14.3
             bus info: pci@0000:00:14.3
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-pci:4
             description: PCI bridge
             product: SBx00 PCI to PCI Bridge
             vendor: Advanced Micro Devices, Inc. [AMD/ATI]
             physical id: 14.4
             bus info: pci@0000:00:14.4
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pci subtractive_decode bus_master vga_palette
             resources: ioport:1000(size=4096) memory:d0100000-d03fffff memory:80000000-83ffffff
           *-pcmcia
                description: CardBus bridge
                product: RL5c476 II
                vendor: Ricoh Co Ltd
                physical id: 4
                bus info: pci@0000:02:04.0
                version: b6
                width: 64 bits
                clock: 33MHz
                capabilities: pcmcia bus_master cap_list
                configuration: driver=yenta_cardbus latency=176 maxlatency=5 mingnt=128
                resources: iomemory:b00603020-b0060301f irq:20 memory:d0100000-d0100fff ioport:1000(size=256) ioport:1400(size=256) memory:80000000-83ffffff memory:88000000-8bffffff
           *-firewire
                description: FireWire (IEEE 1394)
                product: R5C832 IEEE 1394 Controller
                vendor: Ricoh Co Ltd
                physical id: 4.1
                bus info: pci@0000:02:04.1
                version: 02
                width: 32 bits
                clock: 33MHz
                capabilities: ohci bus_master cap_list
                configuration: driver=firewire_ohci latency=64 maxlatency=4 mingnt=2
                resources: irq:21 memory:d0101000-d01017ff
     *-pci:1
          description: Host bridge
          product: K8 [Athlon64/Opteron] HyperTransport Technology Configuration
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 101
          bus info: pci@0000:00:18.0
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:2
          description: Host bridge
          product: K8 [Athlon64/Opteron] Address Map
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 102
          bus info: pci@0000:00:18.1
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:3
          description: Host bridge
          product: K8 [Athlon64/Opteron] DRAM Controller
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 103
          bus info: pci@0000:00:18.2
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:4
          description: Host bridge
          product: K8 [Athlon64/Opteron] Miscellaneous Control
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 104
          bus info: pci@0000:00:18.3
          version: 00

   lspci results

00:00.0 Host bridge: Advanced Micro Devices, Inc. [AMD/ATI] RS690 Host Bridge
00:01.0 PCI bridge: Advanced Micro Devices, Inc. [AMD/ATI] RS690 PCI to PCI Bridge (Internal gfx)
00:04.0 PCI bridge: Advanced Micro Devices, Inc. [AMD/ATI] Device 7914
00:05.0 PCI bridge: Advanced Micro Devices, Inc. [AMD/ATI] RS690 PCI to PCI Bridge (PCI Express Port 1)
00:06.0 PCI bridge: Advanced Micro Devices, Inc. [AMD/ATI] RS690 PCI to PCI Bridge (PCI Express Port 2)
00:12.0 SATA controller: Advanced Micro Devices, Inc. [AMD/ATI] SB600 Non-Raid-5 SATA
00:13.0 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB600 USB (OHCI0)
00:13.1 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB600 USB (OHCI1)
00:13.2 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB600 USB (OHCI2)
00:13.3 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB600 USB (OHCI3)
00:13.4 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB600 USB (OHCI4)
00:13.5 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB600 USB Controller (EHCI)
00:14.0 SMBus: Advanced Micro Devices, Inc. [AMD/ATI] SBx00 SMBus Controller (rev 14)
00:14.1 IDE interface: Advanced Micro Devices, Inc. [AMD/ATI] SB600 IDE
00:14.2 Audio device: Advanced Micro Devices, Inc. [AMD/ATI] SBx00 Azalia (Intel HDA)
00:14.3 ISA bridge: Advanced Micro Devices, Inc. [AMD/ATI] SB600 PCI to LPC Bridge
00:14.4 PCI bridge: Advanced Micro Devices, Inc. [AMD/ATI] SBx00 PCI to PCI Bridge
00:18.0 Host bridge: Advanced Micro Devices, Inc. [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices, Inc. [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices, Inc. [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices, Inc. [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] RS690M [Radeon Xpress 1200/1250/1270]
02:04.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev b6)
02:04.1 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 02)
10:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5787M Gigabit Ethernet PCI Express (rev 02)
30:00.0 Network controller: Broadcom Corporation BCM4311 802.11a/b/g (rev 02)


    lsmod results
Module                  Size  Used by
btusb                  28267  0 
bnep                   19564  2 
rfcomm                 69070  12 
bluetooth             371874  22 bnep,btusb,rfcomm
joydev                 17377  0 
lib80211_crypt_tkip    17619  0 
hp_wmi                 14062  0 
sparse_keymap          13948  1 hp_wmi
ppdev                  17671  0 
wl                   4207474  0 
radeon               1402449  3 
snd_hda_codec_analog    94059  1 
snd_hda_intel          48171  2 
snd_hda_codec         188738  2 snd_hda_intel,snd_hda_codec_analog
snd_hwdep              13602  1 snd_hda_codec
kvm_amd                59958  0 
snd_pcm               102033  2 snd_hda_codec,snd_hda_intel
kvm                   431315  1 kvm_amd
snd_page_alloc         18710  2 snd_pcm,snd_hda_intel
snd_seq_midi           13324  0 
snd_seq_midi_event     14899  1 snd_seq_midi
snd_rawmidi            30095  1 snd_seq_midi
snd_seq                61560  2 snd_seq_midi_event,snd_seq_midi
ttm                    83995  1 radeon
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              29433  2 snd_pcm,snd_seq
drm_kms_helper         52651  1 radeon
tpm_infineon           17372  0 
snd                    69141  14 snd_hwdep,snd_timer,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_hda_codec_analog,snd_seq_midi
drm                   296739  5 ttm,drm_kms_helper,radeon
soundcore              12680  1 snd
psmouse                97626  0 
pcmcia                 61727  0 
lib80211               14352  2 wl,lib80211_crypt_tkip
yenta_socket           41019  0 
i2c_algo_bit           13413  1 radeon
edac_core              62312  0 
cfg80211              479757  1 wl
sp5100_tco             13979  0 
pcmcia_rsrc            18407  1 yenta_socket
serio_raw              13413  0 
k8temp                 12978  0 
edac_mce_amd           22617  0 
pcmcia_core            23592  3 pcmcia,pcmcia_rsrc,yenta_socket
i2c_piix4              22106  0 
wmi                    19070  1 hp_wmi
hp_accel               26012  0 
lis3lv02d              20156  1 hp_accel
input_polldev          13896  1 lis3lv02d
shpchp                 37032  0 
ohci_pci               13561  0 
mac_hid                13205  0 
video                  19318  0 
tpm_tis                19123  0 
parport_pc             32701  1 
lp                     17759  0 
parport                42299  3 lp,ppdev,parport_pc
firewire_ohci          40060  0 
firewire_core          64476  1 firewire_ohci
pata_acpi              13038  0 
crc_itu_t              12707  1 firewire_core
pata_atiixp            13242  0 
tg3                   162230  0 
ptp                    18580  1 tg3
pps_core               19027  1 ptp
ahci                   25819  2 
libahci                31898  1 ahci
```

Oh, and I am capable of inserting an ethernet cable into this laptop. I just would like to have WiFi to use whillist out or something. 
          width: 32 bits
          clock: 33MHz
          configuration: driver=k8temp
          resources: irq:0

---

### Post by kc1di on 2014-07-19
You have the wrong driver installed for your wireless card.  you have the bcmwl-kernel-source and you need the linux-firmware-nonfree

you can install the correct one with these commands:

```
sudo apt-get purge bcmwl-kernel-source
```
Then
```
sudo apt-get install linux-firmware-nonfree
```

Reboot and you should be good to go.  Oh yes you will have to be connect via the ethernet cable. 

Good Luck

---

### Post by matthew44 on 2014-07-19
Ah, thanks. Thats what I assumed after being able to enable the reciever. :)

---

### Post by kc1di on 2014-07-19
Glad it worked for you ;) enjoy !

---

