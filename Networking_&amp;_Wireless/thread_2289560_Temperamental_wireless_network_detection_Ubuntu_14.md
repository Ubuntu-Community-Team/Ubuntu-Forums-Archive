---
title: "Temperamental wireless network detection Ubuntu 14.04 LTS"
date: 2015-08-05
forum: Networking &amp; Wireless
---

### Post by lpko908 on 2015-08-05
Hello, 

for a long time now I have been having problems discovering wireless networks from Ubuntu 14.04 LTS. 50% of the time everything works great. Then I'll put the computer to sleep, or just reboot it and suddenly the system cannot detect networks which are definitely present. The problem persists upon reboot until one day it will magically start working again, until the next time.

It has just gone down again and is currently not functioning.

The wired network is working.

Here are the outputs for

$ lspci
```
00:00.0 Host bridge: Intel Corporation Xeon E3-1200 v3/4th Gen Core Processor DRAM Controller (rev 06)00:01.0 PCI bridge: Intel Corporation Xeon E3-1200 v3/4th Gen Core Processor PCI Express x16 Controller (rev 06)
00:01.1 PCI bridge: Intel Corporation Xeon E3-1200 v3/4th Gen Core Processor PCI Express x8 Controller (rev 06)
00:02.0 VGA compatible controller: Intel Corporation 4th Gen Core Processor Integrated Graphics Controller (rev 06)
00:03.0 Audio device: Intel Corporation Xeon E3-1200 v3/4th Gen Core Processor HD Audio Controller (rev 06)
00:14.0 USB controller: Intel Corporation 8 Series/C220 Series Chipset Family USB xHCI (rev 04)
00:16.0 Communication controller: Intel Corporation 8 Series/C220 Series Chipset Family MEI Controller #1 (rev 04)
00:1a.0 USB controller: Intel Corporation 8 Series/C220 Series Chipset Family USB EHCI #2 (rev 04)
00:1b.0 Audio device: Intel Corporation 8 Series/C220 Series Chipset High Definition Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation 8 Series/C220 Series Chipset Family PCI Express Root Port #1 (rev d4)
00:1c.2 PCI bridge: Intel Corporation 8 Series/C220 Series Chipset Family PCI Express Root Port #3 (rev d4)
00:1c.3 PCI bridge: Intel Corporation 8 Series/C220 Series Chipset Family PCI Express Root Port #4 (rev d4)
00:1d.0 USB controller: Intel Corporation 8 Series/C220 Series Chipset Family USB EHCI #1 (rev 04)
00:1f.0 ISA bridge: Intel Corporation HM87 Express LPC Controller (rev 04)
00:1f.2 SATA controller: Intel Corporation 8 Series/C220 Series Chipset Family 6-port SATA Controller 1 [AHCI mode] (rev 04)
00:1f.3 SMBus: Intel Corporation 8 Series/C220 Series Chipset Family SMBus Controller (rev 04)
01:00.0 3D controller: NVIDIA Corporation GK106M [GeForce GTX 765M] (rev a1)
04:00.0 Network controller: Realtek Semiconductor Co., Ltd. RTL8723AE PCIe Wireless Network Adapter
05:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. Device 5289 (rev 01)
05:00.2 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 0a)

```

$ iwconfig

```
eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry short limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          
usb0      no wireless extensions.


lo        no wireless extensions.

```

$ lsmod

```
Module                  Size  Used by
rndis_host             14513  0 
cdc_ether              14361  1 rndis_host
usbnet                 43952  2 rndis_host,cdc_ether
snd_hda_codec_hdmi     47548  1 
snd_hda_codec_via      31956  1 
snd_hda_codec_generic    69011  1 snd_hda_codec_via
mxm_wmi                13021  0 
arc4                   12608  2 
intel_rapl             18783  0 
x86_pkg_temp_thermal    14205  0 
intel_powerclamp       18823  0 
coretemp               13441  0 
kvm_intel             143630  0 
kvm                   452047  1 kvm_intel
crct10dif_pclmul       14307  0 
crc32_pclmul           13133  0 
ghash_clmulni_intel    13230  0 
rtl8723ae              81799  0 
rtl8723_common         23361  1 rtl8723ae
aesni_intel           152552  1 
aes_x86_64             17131  1 aesni_intel
lrw                    13286  1 aesni_intel
gf128mul               14951  1 lrw
rtl_pci                26690  1 rtl8723ae
glue_helper            13990  1 aesni_intel
rtlwifi                64255  2 rtl_pci,rtl8723ae
ablk_helper            13597  1 aesni_intel
cryptd                 20359  3 ghash_clmulni_intel,aesni_intel,ablk_helper
rfcomm                 69509  10 
bnep                   19624  2 
joydev                 17393  0 
btusb                  32497  0 
serio_raw              13483  0 
nvidia              10744914  0 
rtsx_pci_ms            18168  0 
bluetooth             446409  22 bnep,btusb,rfcomm
memstick               16966  1 rtsx_pci_ms
6lowpan_iphc           18702  1 bluetooth
lpc_ich                21093  0 
snd_hda_intel          30469  5 
mac80211              652777  3 rtl_pci,rtlwifi,rtl8723ae
snd_hda_controller     30228  1 snd_hda_intel
snd_hda_codec         139719  5 snd_hda_codec_hdmi,snd_hda_codec_via,snd_hda_codec_generic,snd_hda_intel,snd_hda_controller
snd_hwdep              17698  1 snd_hda_codec
cfg80211              498458  2 mac80211,rtlwifi
snd_pcm               104112  4 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel,snd_hda_controller
snd_seq_midi           13564  0 
snd_seq_midi_event     14899  1 snd_seq_midi
snd_rawmidi            30876  1 snd_seq_midi
i915                  906106  7 
snd_seq                63074  2 snd_seq_midi_event,snd_seq_midi
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
drm_kms_helper         61574  1 i915
snd_timer              29562  2 snd_pcm,snd_seq
drm                   311018  7 i915,drm_kms_helper,nvidia
mei_me                 19696  0 
mei                    87875  1 mei_me
snd                    79468  21 snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_hda_codec_via,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec_generic,snd_hda_codec,snd_hda_intel,snd_seq_device
i2c_algo_bit           13413  1 i915
binfmt_misc            17468  1 
shpchp                 37047  0 
soundcore              15047  2 snd,snd_hda_codec
tpm_infineon           17131  0 
parport_pc             32741  0 
wmi                    19193  1 mxm_wmi
video                  20128  1 i915
ppdev                  17671  0 
mac_hid                13227  0 
lp                     17759  0 
parport                42348  3 lp,ppdev,parport_pc
rtsx_pci_sdmmc         23043  0 
ahci                   34142  2 
psmouse               106767  0 
r8169                  71694  0 
rtsx_pci               46259  2 rtsx_pci_ms,rtsx_pci_sdmmc
libahci                32424  1 ahci
mii                    13934  2 r8169,usbnet

```

$ sudo lshw -C network

```
  *-network               
       description: Wireless interface
       product: RTL8723AE PCIe Wireless Network Adapter
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: wlan0
       version: 00
       serial: 48:d2:24:35:5c:3d
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rtl8723ae driverversion=3.16.0-45-generic firmware=N/A latency=0 link=no multicast=yes wireless=IEEE 802.11bgn
       resources: irq:18 ioport:d000(size=256) memory:f7900000-f7903fff
  *-network
       description: Ethernet interface
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0.2
       bus info: pci@0000:05:00.2
       logical name: eth0
       version: 0a
       serial: 00:90:f5:e6:62:cf
       size: 10Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=rtl8411-1_0.0.3 06/18/12 latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:44 ioport:c000(size=256) memory:f2104000-f2104fff memory:f2100000-f2103fff
  *-network
       description: Ethernet interface
       physical id: 1
       logical name: usb0
       serial: 02:71:18:67:75:77
       capabilities: ethernet physical
       configuration: broadcast=yes driver=rndis_host driverversion=22-Aug-2005 firmware=RNDIS device ip=192.168.42.144 link=yes multicast=yes

```

$ iwlist scan

```
eth0      Interface doesn't support scanning.


wlan0     No scan results


usb0      Interface doesn't support scanning.


lo        Interface doesn't support scanning.

```

Any help for a long term fix to this recurring problem would be most appreciated.

Thanks!

---

