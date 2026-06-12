---
title: "Wifi hard block Ubuntu 18.04"
date: 2018-10-10
forum: Networking &amp; Wireless
---

### Post by superkid333 on 2018-10-10
I am posting this for two reasons. First, I want to share a "solution" to the wifi hard bock problem that many people have. Second, I want to understand why my solution worked for me. I hope it can be applied to others, but it may be specific to my situation. 

My wifi became hard blocked during a reboot from Ubuntu to Linux Mint USB. I've had this happen before when booting into Windows or Kali Linux. Sometimes it would come back. I tried many solutions but rfkill list all showed hard bock:

rfkill list all:
```
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes
2: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no

```

I tried using modprobe to blacklist the driver for rtl8723ae (or whatever the driver name is for that Realtek device). Nothing worked. I tried re-installing network-manager. Did not work. 

Here is my solution:
Today, I booted up Ubnutu, knowing that the wifi was still hard blocked. I wanted to get some information and post it here. I then suspended my Ubuntu (or made it sleep) by pressing Fn + F4. This can be different per machine and there are ways to suspend in the Terminal as well. This is different than just closing the lid. After it was sleeping, I pressed the power button to wake it up. Suddenly, the green light came on and my wifi was back up. Like magic. 

My question is this: WHY?! What happened? I have read posts over the past few years with people running into the same hard block issue, when indeed there is no hard block there. Clearly the issue has something to do with while the computer is booting, because that is what started the problem. Some how suspending it must have reinitialized the network card.

Here is the link to the output of dmesg:
[https://paste.ubuntu.com/p/hrRWcBTBT3/](https://paste.ubuntu.com/p/hrRWcBTBT3/)

If someone can review that and let me know what happened that would be great. I want to share knowledge that might help others resolve this problem.

---

### Post by praseodym on 2018-10-10
What kind of computer is it? Please show
```

lspci -nnk
lsusb
lsmod
```

---

### Post by superkid333 on 2018-10-10
I will post that later tonight when I get home. 

In the meantime, I just read some kernel level document regarding rfkill. I feel like a mad scientist reading this! However, it actually talks about some platforms change the hardware state during suspend/hibernation. This might actually explain the hard block switch. 
[FONT=Verdana]Here is an excerpt:[/FONT]

For some platforms, it is possible that the hardware state changes during
suspend/hibernation, in which case it will be necessary to update the rfkill
core with the current state at resume time.

Website here: [https://www.kernel.org/doc/Documentation/rfkill.txt](https://www.kernel.org/doc/Documentation/rfkill.txt)

---

### Post by superkid333 on 2018-10-11
> **praseodym said:**
> What kind of computer is it? Please show
```

lspci -nnk
lsusb
lsmod
```

Here is the output of lspci -nnk, lsusb, and lsmod. Hopefully this can shed some light on the issue (and why the solution may have worked). 
```
lspci -nnk
00:00.0 Host bridge [0600]: Intel Corporation 3rd Gen Core processor DRAM Controller [8086:0154] (rev 09)
    Subsystem: CLEVO/KAPOK Computer 3rd Gen Core processor DRAM Controller [1558:2701]
    Kernel driver in use: ivb_uncore
00:01.0 PCI bridge [0604]: Intel Corporation Xeon E3-1200 v2/3rd Gen Core processor PCI Express Root Port [8086:0151] (rev 09)
    Kernel driver in use: pcieport
    Kernel modules: shpchp
00:01.1 PCI bridge [0604]: Intel Corporation Xeon E3-1200 v2/3rd Gen Core processor PCI Express Root Port [8086:0155] (rev 09)
    Kernel driver in use: pcieport
    Kernel modules: shpchp
00:02.0 VGA compatible controller [0300]: Intel Corporation 3rd Gen Core processor Graphics Controller [8086:0166] (rev 09)
    Subsystem: CLEVO/KAPOK Computer 3rd Gen Core processor Graphics Controller [1558:2701]
    Kernel driver in use: i915
    Kernel modules: i915
00:14.0 USB controller [0c03]: Intel Corporation 7 Series/C210 Series Chipset Family USB xHCI Host Controller [8086:1e31] (rev 04)
    Subsystem: CLEVO/KAPOK Computer 7 Series/C210 Series Chipset Family USB xHCI Host Controller [1558:2701]
    Kernel driver in use: xhci_hcd
00:16.0 Communication controller [0780]: Intel Corporation 7 Series/C216 Chipset Family MEI Controller #1 [8086:1e3a] (rev 04)
    Subsystem: CLEVO/KAPOK Computer 7 Series/C216 Chipset Family MEI Controller [1558:2701]
    Kernel driver in use: mei_me
    Kernel modules: mei_me
00:1a.0 USB controller [0c03]: Intel Corporation 7 Series/C216 Chipset Family USB Enhanced Host Controller #2 [8086:1e2d] (rev 04)
    Subsystem: CLEVO/KAPOK Computer 7 Series/C216 Chipset Family USB Enhanced Host Controller [1558:2701]
    Kernel driver in use: ehci-pci
00:1b.0 Audio device [0403]: Intel Corporation 7 Series/C216 Chipset Family High Definition Audio Controller [8086:1e20] (rev 04)
    Subsystem: CLEVO/KAPOK Computer 7 Series/C216 Chipset Family High Definition Audio Controller [1558:2701]
    Kernel driver in use: snd_hda_intel
    Kernel modules: snd_hda_intel
00:1c.0 PCI bridge [0604]: Intel Corporation 7 Series/C216 Chipset Family PCI Express Root Port 1 [8086:1e10] (rev c4)
    Kernel driver in use: pcieport
    Kernel modules: shpchp
00:1c.2 PCI bridge [0604]: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 3 [8086:1e14] (rev c4)
    Kernel driver in use: pcieport
    Kernel modules: shpchp
00:1c.3 PCI bridge [0604]: Intel Corporation 7 Series/C216 Chipset Family PCI Express Root Port 4 [8086:1e16] (rev c4)
    Kernel driver in use: pcieport
    Kernel modules: shpchp
00:1d.0 USB controller [0c03]: Intel Corporation 7 Series/C216 Chipset Family USB Enhanced Host Controller #1 [8086:1e26] (rev 04)
    Subsystem: CLEVO/KAPOK Computer 7 Series/C216 Chipset Family USB Enhanced Host Controller [1558:2701]
    Kernel driver in use: ehci-pci
00:1f.0 ISA bridge [0601]: Intel Corporation HM76 Express Chipset LPC Controller [8086:1e59] (rev 04)
    Subsystem: CLEVO/KAPOK Computer HM76 Express Chipset LPC Controller [1558:2701]
    Kernel driver in use: lpc_ich
    Kernel modules: lpc_ich
00:1f.2 SATA controller [0106]: Intel Corporation 7 Series Chipset Family 6-port SATA Controller [AHCI mode] [8086:1e03] (rev 04)
    Subsystem: CLEVO/KAPOK Computer 7 Series Chipset Family 6-port SATA Controller [AHCI mode] [1558:2701]
    Kernel driver in use: ahci
    Kernel modules: ahci
00:1f.3 SMBus [0c05]: Intel Corporation 7 Series/C216 Chipset Family SMBus Controller [8086:1e22] (rev 04)
    Subsystem: CLEVO/KAPOK Computer 7 Series/C216 Chipset Family SMBus Controller [1558:2701]
    Kernel modules: i2c_i801
01:00.0 VGA compatible controller [0300]: NVIDIA Corporation GK107M [GeForce GT 640M] [10de:0fd2] (rev a1)
    Subsystem: CLEVO/KAPOK Computer GK107M [GeForce GT 640M] [1558:2701]
    Kernel modules: nvidiafb, nouveau
04:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8723AE PCIe Wireless Network Adapter [10ec:8723]
    Subsystem: Realtek Semiconductor Co., Ltd. RTL8723AE PCIe Wireless Network Adapter [10ec:0726]
    Kernel driver in use: rtl8723ae
    Kernel modules: rtl8723ae
05:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. RTL8411 PCI Express Card Reader [10ec:5289] (rev 01)
    Subsystem: CLEVO/KAPOK Computer RTL8411 PCI Express Card Reader [1558:2701]
    Kernel driver in use: rtsx_pci
    Kernel modules: rtsx_pci
05:00.2 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 0a)
    Subsystem: CLEVO/KAPOK Computer RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [1558:2701]
    Kernel driver in use: r8169
    Kernel modules: r8169
 
```

lsusb:
```
lsusb
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 003: ID 0bda:8723 Realtek Semiconductor Corp. 
Bus 003 Device 002: ID 04d9:fa56 Holtek Semiconductor, Inc. 
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

lsmod:
```
lsmod
Module                  Size  Used by
rfcomm                 77824  4
ccm                    20480  9
bnep                   20480  2
binfmt_misc            20480  1
snd_hda_codec_hdmi     49152  1
snd_hda_codec_via      24576  1
snd_hda_codec_generic    73728  1 snd_hda_codec_via
snd_hda_intel          40960  3
snd_hda_codec         126976  4 snd_hda_intel,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_hda_codec_via
snd_hda_core           81920  5 snd_hda_intel,snd_hda_codec,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_hda_codec_via
snd_hwdep              20480  1 snd_hda_codec
snd_pcm                98304  4 snd_hda_intel,snd_hda_codec,snd_hda_core,snd_hda_codec_hdmi
btusb                  45056  0
btrtl                  16384  1 btusb
btbcm                  16384  1 btusb
btintel                16384  1 btusb
bluetooth             548864  33 btrtl,btintel,bnep,btbcm,rfcomm,btusb
ecdh_generic           24576  1 bluetooth
arc4                   16384  2
rtl8723ae              94208  0
btcoexist             135168  1 rtl8723ae
rtl8723_common         24576  1 rtl8723ae
rtl_pci                32768  1 rtl8723ae
rtlwifi                77824  4 rtl_pci,btcoexist,rtl8723_common,rtl8723ae
mac80211              778240  2 rtl_pci,rtlwifi
cfg80211              622592  2 mac80211,rtlwifi
snd_seq_midi           16384  0
snd_seq_midi_event     16384  1 snd_seq_midi
snd_rawmidi            32768  1 snd_seq_midi
joydev                 24576  0
wmi_bmof               16384  0
mxm_wmi                16384  0
intel_rapl             20480  0
x86_pkg_temp_thermal    16384  0
intel_powerclamp       16384  0
coretemp               16384  0
kvm_intel             212992  0
kvm                   598016  1 kvm_intel
irqbypass              16384  1 kvm
crct10dif_pclmul       16384  0
crc32_pclmul           16384  0
ghash_clmulni_intel    16384  0
pcbc                   16384  0
wmi                    24576  2 wmi_bmof,mxm_wmi
aesni_intel           188416  6
aes_x86_64             20480  1 aesni_intel
crypto_simd            16384  1 aesni_intel
glue_helper            16384  1 aesni_intel
cryptd                 24576  3 crypto_simd,ghash_clmulni_intel,aesni_intel
intel_cstate           20480  0
intel_rapl_perf        16384  0
rtsx_pci_ms            20480  0
memstick               16384  1 rtsx_pci_ms
snd_seq                65536  2 snd_seq_midi_event,snd_seq_midi
input_leds             16384  0
snd_seq_device         16384  3 snd_seq,snd_rawmidi,snd_seq_midi
serio_raw              16384  0
snd_timer              32768  2 snd_seq,snd_pcm
snd                    81920  17 snd_hda_intel,snd_hwdep,snd_seq,snd_hda_codec,snd_timer,snd_rawmidi,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_seq_device,snd_pcm,snd_hda_codec_via
lpc_ich                24576  0
mei_me                 40960  0
soundcore              16384  1 snd
mei                    90112  1 mei_me
shpchp                 36864  0
mac_hid                16384  0
sch_fq_codel           20480  6
parport_pc             36864  0
ppdev                  20480  0
lp                     20480  0
parport                49152  3 lp,parport_pc,ppdev
ip_tables              28672  0
x_tables               40960  1 ip_tables
autofs4                40960  2
hid_generic            16384  0
usbhid                 49152  0
hid                   118784  2 hid_generic,usbhid
i915                 1617920  11
rtsx_pci_sdmmc         24576  0
i2c_algo_bit           16384  1 i915
drm_kms_helper        172032  1 i915
syscopyarea            16384  1 drm_kms_helper
sysfillrect            16384  1 drm_kms_helper
sysimgblt              16384  1 drm_kms_helper
fb_sys_fops            16384  1 drm_kms_helper
r8169                  86016  0
drm                   401408  5 i915,drm_kms_helper
psmouse               147456  0
ahci                   36864  2
rtsx_pci               65536  2 rtsx_pci_sdmmc,rtsx_pci_ms
libahci                32768  1 ahci
mii                    16384  1 r8169
video                  45056  1 i915

```

---

### Post by superkid333 on 2018-10-13
Does anyone have any idea why the suspend and wake-up returned my network card to life? I can't decipher the system logs for more useful information. 

Any light would be excellent.

---

