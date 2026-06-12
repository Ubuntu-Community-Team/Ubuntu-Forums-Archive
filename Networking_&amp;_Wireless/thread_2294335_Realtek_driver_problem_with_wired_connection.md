---
title: "Realtek driver problem with wired connection"
date: 2015-09-10
forum: Networking &amp; Wireless
---

### Post by spearhead2 on 2015-09-10
Hello

My PC with fresh Lubuntu 15.04 installed has no wired connection. The settings of IP/mask/gateway etc. are proper, since I can connect with same values using Macbook. I suspect that the problem is related to the Realtek driver:

> # mii-tool -v
eth0: no link
  product info: vendor 00:07:32, model 17 rev 2
  basic mode:   autonegotiation enabled
  basic status: no link
  capabilities: 1000baseT-HD 1000baseT-FD 100baseTx-FD 100baseTx-HD 10baseT-FD 10baseT-HD
  advertising:  100baseTx-FD 100baseTx-HD 10baseT-FD 10baseT-HD flow-control

I found [this]("http://askubuntu.com/questions/586634/ethernet-link-not-detected-in-ubuntu-14-04-after-update") thread and decided to replaced r8169 with r8168 using 

> sudo apt-get install r8168-dkms

Command found [here]("http://askubuntu.com/questions/654496/wired-network-connection-in-xubuntu-not-working-with-r8169"). After that r8168 is used, as I can see in lspci output:

> 04:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 01)
    Subsystem: Micro-Star International Co., Ltd. [MSI] Device 395c
    Physical Slot: 0-2
    Flags: bus master, fast devsel, latency 0, IRQ 28
    I/O ports at e800 [size=256]
    Memory at febff000 (64-bit, non-prefetchable) [size=4K]
    Expansion ROM at febc0000 [disabled] [size=128K]
    Capabilities: [40] Power Management version 2
    Capabilities: [48] Vital Product Data
    Capabilities: [50] MSI: Enable+ Count=1/2 Maskable- 64bit+
    Capabilities: [60] Express Endpoint, MSI 00
    Capabilities: [84] Vendor Specific Information: Len=4c <?>
    Capabilities: [100] Advanced Error Reporting
    Capabilities: [12c] Virtual Channel
    Capabilities: [148] Device Serial Number 6e-00-00-00-10-ec-81-68
    Capabilities: [154] Power Budgeting <?>
    Kernel driver in use: r8168

And also lsmod:

> Module                  Size  Used by
mii                    16384  0 
nls_iso8859_1          16384  1 
amdkfd                 81920  1 
amd_iommu_v2           20480  1 amdkfd
radeon               1556480  2 
gpio_ich               16384  0 
snd_hda_codec_realtek    86016  1 
snd_hda_codec_generic    69632  1 snd_hda_codec_realtek
snd_hda_codec_hdmi     53248  1 
snd_hda_intel          36864  5 
snd_hda_controller     32768  1 snd_hda_intel
snd_hda_codec         143360  5 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_hda_intel,snd_hda_controller
snd_hwdep              20480  1 snd_hda_codec
ttm                    98304  1 radeon
drm_kms_helper        126976  1 radeon
drm                   344064  5 ttm,drm_kms_helper,radeon
snd_pcm               106496  4 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel,snd_hda_controller
snd_seq_midi           16384  0 
snd_seq_midi_event     16384  1 snd_seq_midi
snd_rawmidi            32768  1 snd_seq_midi
i2c_algo_bit           16384  1 radeon
snd_seq                69632  2 snd_seq_midi_event,snd_seq_midi
snd_seq_device         16384  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              32768  2 snd_pcm,snd_seq
snd                    90112  21 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec_generic,snd_hda_codec,snd_hda_intel,snd_seq_device
coretemp               16384  0 
serio_raw              16384  0 
soundcore              16384  2 snd,snd_hda_codec
lpc_ich                24576  0 
shpchp                 40960  0 
8250_fintek            16384  0 
tpm_infineon           20480  0 
mac_hid                16384  0 
parport_pc             32768  1 
ppdev                  20480  0 
lp                     20480  0 
parport                45056  3 lp,ppdev,parport_pc
autofs4                40960  2 
hid_generic            16384  0 
usbhid                 53248  0 
hid                   110592  2 hid_generic,usbhid
uas                    24576  0 
usb_storage            69632  2 uas
pata_acpi              16384  0 
pata_jmicron           16384  0 
r8168                 499712  0 
floppy                 77824  0 
ahci                   36864  0 
libahci                32768  1 ahci

This didn't help and the network is still down. I tried to to manually set up mii-tool, something like [here]("http://ubuntuforums.org/showthread.php?t=1602482&p=10015184#post10015184"), but to no avail. 

The weird thing is that one time all of sudden network was working again and then everything went down again after a restart.

Any ideas how to proceed?

---

