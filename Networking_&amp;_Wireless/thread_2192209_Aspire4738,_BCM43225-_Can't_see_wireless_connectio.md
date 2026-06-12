---
title: "Aspire4738, BCM43225- Can't see wireless connections.."
date: 2013-12-06
forum: Networking &amp; Wireless
---

### Post by hafiz043 on 2013-12-06
I'm just installed Ubuntu 12.04 on my friend's laptop. I CAN see and connect to the network BEFORE permanently install the Ubuntu. When I start the installation, the wifi suddenly lost and no connections are available.

---

### Post by hafiz043 on 2013-12-06
I try some code and get this output:

```
rahmat@rahmat-Aspire-4738:~$ lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation Core Processor DRAM Controller [8086:0044] (rev 18)
00:02.0 VGA compatible controller [0300]: Intel Corporation Core Processor Integrated Graphics Controller [8086:0046] (rev 18)
00:16.0 Communication controller [0780]: Intel Corporation 5 Series/3400 Series Chipset HECI Controller [8086:3b64] (rev 06)
00:1a.0 USB controller [0c03]: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller [8086:3b3c] (rev 05)
00:1b.0 Audio device [0403]: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio [8086:3b56] (rev 05)
00:1c.0 PCI bridge [0604]: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 [8086:3b42] (rev 05)
00:1c.5 PCI bridge [0604]: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 6 [8086:3b4c] (rev 05)
00:1d.0 USB controller [0c03]: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller [8086:3b34] (rev 05)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev a5)
00:1f.0 ISA bridge [0601]: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller [8086:3b09] (rev 05)
00:1f.2 SATA controller [0106]: Intel Corporation 5 Series/3400 Series Chipset 4 port SATA AHCI Controller [8086:3b29] (rev 05)
00:1f.3 SMBus [0c05]: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller [8086:3b30] (rev 05)
00:1f.6 Signal processing controller [1180]: Intel Corporation 5 Series/3400 Series Chipset Thermal Subsystem [8086:3b32] (rev 05)
01:00.0 Ethernet controller [0200]: Broadcom Corporation NetLink BCM57780 Gigabit Ethernet PCIe [14e4:1692] (rev 01)
02:00.0 Network controller [0280]: Broadcom Corporation BCM43225 802.11b/g/n [14e4:4357] (rev 01)
7f:00.0 Host bridge [0600]: Intel Corporation Core Processor QuickPath Architecture Generic Non-core Registers [8086:2c62] (rev 05)
7f:00.1 Host bridge [0600]: Intel Corporation Core Processor QuickPath Architecture System Address Decoder [8086:2d01] (rev 05)
7f:02.0 Host bridge [0600]: Intel Corporation Core Processor QPI Link 0 [8086:2d10] (rev 05)
7f:02.1 Host bridge [0600]: Intel Corporation Core Processor QPI Physical 0 [8086:2d11] (rev 05)
7f:02.2 Host bridge [0600]: Intel Corporation Core Processor Reserved [8086:2d12] (rev 05)
7f:02.3 Host bridge [0600]: Intel Corporation Core Processor Reserved [8086:2d13] (rev 05)
```


```
rahmat@rahmat-Aspire-4738:~$ lsmodModule                  
Size  Used by
nls_iso8859_1          12713  0 
bnep                   18258  2 
rfcomm                 47864  12 
parport_pc             28284  0 
ppdev                  17113  0 
snd_hda_codec_hdmi     37434  1 
snd_hda_codec_realtek    79916  1 
uvcvideo               82214  0 
snd_hda_intel          44339  3 
snd_hda_codec         141716  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
videobuf2_core         40785  1 uvcvideo
videodev              130053  2 uvcvideo,videobuf2_core
coretemp               13596  0 
i915                  620421  8 
snd_hwdep              13668  1 snd_hda_codec
videobuf2_vmalloc      13056  1 uvcvideo
snd_pcm               102477  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
kvm_intel             137899  0 
videobuf2_memops       13202  1 videobuf2_vmalloc
kvm                   455932  1 kvm_intel
snd_seq_midi           13324  0 
btusb                  22431  0 
snd_rawmidi            30417  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61930  2 snd_seq_midi,snd_seq_midi_event
bluetooth             247024  24 bnep,rfcomm,btusb
snd_timer              29989  2 snd_pcm,snd_seq
snd_seq_device         14497  3 snd_seq_midi,snd_rawmidi,snd_seq
joydev                 17613  0 
drm_kms_helper         49597  1 i915
drm                   287564  4 i915,drm_kms_helper
psmouse                97873  0 
microcode              23017  0 
snd                    69533  16 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
acer_wmi               32858  0 
mei                    41820  0 
sparse_keymap          13890  1 acer_wmi
soundcore              12680  1 snd
snd_page_alloc         18798  2 snd_hda_intel,snd_pcm
lpc_ich                17144  0 
i2c_algo_bit           13564  1 i915
wmi                    19256  1 acer_wmi
intel_ips              18066  0 
serio_raw              13215  0 
mac_hid                13253  0 
video                  19652  2 i915,acer_wmi
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
usb_storage            61749  1 
ahci                   25879  2 
libahci                31606  1 ahci
tg3                   165622  0 
ptp                    18668  1 tg3
pps_core               14080  1 ptp
rahmat@rahmat-Aspire-4738:~$ rfkill list all
0: acer-wireless: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: acer-bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no
2: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
```

```
rahmat@rahmat-Aspire-4738:~$ sudo lshw -c network  *-network               
       description: Ethernet interface
       product: NetLink BCM57780 Gigabit Ethernet PCIe
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: eth0
       version: 01
       serial: 60:eb:69:50:a1:81
       size: 10Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.128 duplex=half firmware=sb latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:44 memory:93400000-9340ffff
  *-network UNCLAIMED
       description: Network controller
       product: BCM43225 802.11b/g/n
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: memory:92400000-92403fff
```

---

