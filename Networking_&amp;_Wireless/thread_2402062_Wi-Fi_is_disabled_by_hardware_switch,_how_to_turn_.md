---
title: "Wi-Fi is disabled by hardware switch, how to turn in on [Dell Precision M4800]"
date: 2018-09-25
forum: Networking &amp; Wireless
---

### Post by hays-joe on 2018-09-25
There are a number of closed threads that are related but none have solved my problem. 

I have a Dell Precision M4800. I am running Ubuntu 16.04. I cannot get the wifi to work. 

The hardware switch does not seem to change the state of the machine when I switch it on and off. As a result, the wifi networking does not work.

I have already verified that wifi is enabled in the BIOS. I've also reloaded the default settings in the BIOS. None of these changes removes the hardware block.

Here is some information about my setup:

'rfkill list all' returns,
```

1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
2: brcmwl-0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes
3: dell-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: yes
4: dell-bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: yes

```

and, 'lsmod' returns

```

lsmod
Module                  Size  Used by
appletalk              36864  0
ipx                    28672  0
p8023                  16384  1 ipx
psnap                  16384  2 appletalk,ipx
p8022                  16384  1 ipx
llc                    16384  2 p8022,psnap
binfmt_misc            20480  1
snd_hda_codec_hdmi     49152  1
intel_rapl             20480  0
x86_pkg_temp_thermal    16384  0
intel_powerclamp       16384  0
dell_laptop            20480  0
dell_smm_hwmon         16384  0
coretemp               16384  0
kvm_intel             204800  0
kvm                   593920  1 kvm_intel
irqbypass              16384  1 kvm
intel_cstate           20480  0
intel_rapl_perf        16384  0
snd_soc_rt5640        118784  0
uvcvideo               90112  0
snd_soc_rl6231         16384  1 snd_soc_rt5640
dell_wmi               16384  0
input_leds             16384  0
joydev                 20480  0
videobuf2_vmalloc      16384  1 uvcvideo
dell_smbios            16384  2 dell_wmi,dell_laptop
dcdbas                 16384  1 dell_smbios
sparse_keymap          16384  1 dell_wmi
serio_raw              16384  0
wl                   6447104  0
wmi_bmof               16384  0
videobuf2_memops       16384  1 videobuf2_vmalloc
snd_soc_core          229376  1 snd_soc_rt5640
videobuf2_v4l2         24576  1 uvcvideo
videobuf2_core         40960  2 uvcvideo,videobuf2_v4l2
snd_hda_codec_realtek    98304  1
snd_compress           20480  1 snd_soc_core
videodev              176128  3 uvcvideo,videobuf2_core,videobuf2_v4l2
ac97_bus               16384  1 snd_soc_core
snd_hda_codec_generic    73728  1 snd_hda_codec_realtek
snd_pcm_dmaengine      16384  1 snd_soc_core
media                  40960  2 uvcvideo,videodev
cfg80211              614400  1 wl
snd_hda_intel          40960  4
snd_seq_midi           16384  0
snd_seq_midi_event     16384  1 snd_seq_midi
snd_hda_codec         126976  4 snd_hda_intel,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_hda_codec_realtek
snd_rawmidi            32768  1 snd_seq_midi
snd_hda_core           81920  5 snd_hda_intel,snd_hda_codec,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_hda_codec_realtek
snd_hwdep              20480  1 snd_hda_codec
mei_me                 40960  0
mei                   102400  1 mei_me
shpchp                 36864  0
ie31200_edac           16384  0
lpc_ich                24576  0
snd_pcm                98304  7 snd_hda_intel,snd_hda_codec,snd_pcm_dmaengine,snd_hda_core,snd_soc_rt5640,snd_hda_codec_hdmi,snd_soc_core
snd_seq                65536  2 snd_seq_midi_event,snd_seq_midi
snd_seq_device         16384  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              32768  2 snd_seq,snd_pcm
snd                    81920  21 snd_compress,snd_hda_intel,snd_hwdep,snd_seq,snd_hda_codec,snd_timer,snd_rawmidi,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_seq_device,snd_hda_codec_realtek,snd_soc_core,snd_pcm
dell_smo8800           16384  0
dw_dmac                16384  0
soundcore              16384  1 snd
dw_dmac_core           24576  1 dw_dmac
snd_soc_sst_acpi       16384  0
snd_soc_sst_match      16384  1 snd_soc_sst_acpi
elan_i2c               36864  0
8250_dw                16384  0
spi_pxa2xx_platform    24576  0
mac_hid                16384  0
dell_rbtn              16384  1
parport_pc             32768  0
ppdev                  20480  0
lp                     20480  0
parport                49152  3 lp,parport_pc,ppdev
autofs4                40960  2
algif_skcipher         20480  0
af_alg                 16384  1 algif_skcipher
dm_crypt               36864  1
nouveau              1650688  3
crct10dif_pclmul       16384  0
crc32_pclmul           16384  0
ghash_clmulni_intel    16384  0
pcbc                   16384  0
aesni_intel           188416  2
mxm_wmi                16384  1 nouveau
i2c_algo_bit           16384  1 nouveau
aes_x86_64             20480  1 aesni_intel
ttm                    94208  1 nouveau
crypto_simd            16384  1 aesni_intel
glue_helper            16384  1 aesni_intel
cryptd                 24576  4 crypto_simd,ghash_clmulni_intel,aesni_intel
drm_kms_helper        167936  1 nouveau
syscopyarea            16384  1 drm_kms_helper
psmouse               147456  0
sysfillrect            16384  1 drm_kms_helper
ahci                   36864  2
sysimgblt              16384  1 drm_kms_helper
e1000e                249856  0
fb_sys_fops            16384  1 drm_kms_helper
libahci                32768  1 ahci
sdhci_pci              28672  0
drm                   360448  6 nouveau,ttm,drm_kms_helper
ptp                    20480  1 e1000e
pps_core               20480  1 ptp
wmi                    24576  4 dell_wmi,wmi_bmof,mxm_wmi,nouveau
sdhci_acpi             16384  0
sdhci                  45056  2 sdhci_pci,sdhci_acpi
video                  40960  3 dell_wmi,dell_laptop,nouveau
i2c_hid                20480  0
hid                   118784  1 i2c_hid

```

and, 'lspci' returns,

```
00:00.0 Host bridge: Intel Corporation Xeon E3-1200 v3/4th Gen Core Processor DRAM Controller (rev 06)
00:01.0 PCI bridge: Intel Corporation Xeon E3-1200 v3/4th Gen Core Processor PCI Express x16 Controller (rev 06)
00:14.0 USB controller: Intel Corporation 8 Series/C220 Series Chipset Family USB xHCI (rev 04)
00:16.0 Communication controller: Intel Corporation 8 Series/C220 Series Chipset Family MEI Controller #1 (rev 04)
00:19.0 Ethernet controller: Intel Corporation Ethernet Connection I217-LM (rev 04)
00:1a.0 USB controller: Intel Corporation 8 Series/C220 Series Chipset Family USB EHCI #2 (rev 04)
00:1b.0 Audio device: Intel Corporation 8 Series/C220 Series Chipset High Definition Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation 8 Series/C220 Series Chipset Family PCI Express Root Port #1 (rev d4)
00:1c.2 PCI bridge: Intel Corporation 8 Series/C220 Series Chipset Family PCI Express Root Port #3 (rev d4)
00:1c.3 PCI bridge: Intel Corporation 8 Series/C220 Series Chipset Family PCI Express Root Port #4 (rev d4)
00:1c.4 PCI bridge: Intel Corporation 8 Series/C220 Series Chipset Family PCI Express Root Port #5 (rev d4)
00:1c.6 PCI bridge: Intel Corporation 8 Series/C220 Series Chipset Family PCI Express Root Port #7 (rev d4)
00:1c.7 PCI bridge: Intel Corporation 8 Series/C220 Series Chipset Family PCI Express Root Port #8 (rev d4)
00:1d.0 USB controller: Intel Corporation 8 Series/C220 Series Chipset Family USB EHCI #1 (rev 04)
00:1f.0 ISA bridge: Intel Corporation QM87 Express LPC Controller (rev 04)
00:1f.2 RAID bus controller: Intel Corporation 82801 Mobile SATA Controller [RAID mode] (rev 04)
00:1f.3 SMBus: Intel Corporation 8 Series/C220 Series Chipset Family SMBus Controller (rev 04)
01:00.0 VGA compatible controller: NVIDIA Corporation GK107GLM [Quadro K1100M] (rev a1)
01:00.1 Audio device: NVIDIA Corporation GK107 HDMI Audio Controller (rev a1)
03:00.0 Network controller: Broadcom Inc. and subsidiaries BCM4352 802.11ac Wireless Network Adapter (rev 03)
11:00.0 SD Host controller: O2 Micro, Inc. SD/MMC Card Reader Controller (rev 01)

```
finally, 'sudo lshw -class network' returns```

  *-network               
       description: Ethernet interface
       product: Ethernet Connection I217-LM
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       logical name: eno1
       version: 04
       serial: f0:1f:af:69:c3:db
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=3.2.6-k duplex=full firmware=0.13-3 ip=192.168.1.151 latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:25 memory:f7400000-f741ffff memory:f7439000-f7439fff ioport:f040(size=32)
  *-network
       description: Wireless interface
       product: BCM4352 802.11ac Wireless Network Adapter
       vendor: Broadcom Inc. and subsidiaries
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlp3s0
       version: 03
       serial: 24:fd:52:45:6a:ef
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=6.30.223.271 (r587334) latency=0 multicast=yes wireless=IEEE 802.11
       resources: irq:18 memory:f5400000-f5407fff memory:f5200000-f53fffff

```

I'm completely stuck...

thoughts?

PS: I forgot to mention that originally the system was blacklisting the bcm43xx drivers. But, I removed the blacklists. This can be seen by,

```

/etc/modprobe.d$ grep bcm *
blacklist-bcm43.conf:# Warning: This file is autogenerated by bcmwl. All changes to this file will be lost.
blacklist-bcm43.conf:#blacklist bcm43xx
blacklist-bcm43.conf:blacklist bcma
blacklist.conf:#blacklist bcm43xx

```

---

### Post by jeremy31 on 2018-09-25
Have you tried the FN + F? button combination to try to enable wifi?  The dell_rbtn modules normally helps and I see it is loaded

---

### Post by chili555 on 2018-09-25
> PS: I forgot to mention that originally the system was blacklisting the bcm43xx drivers. But, I removed the blacklists. This can be seen by,
There is no, and there hasn't been for a decade or so, driver named bcm43xx.

Confirm:```
modinfo bcm43xx
```Blacklisting it or not makes no difference.

---

### Post by hays-joe on 2018-09-25
@jeremy31, thanks for the idea. I just tested all 12 combinations of FN + F# one at a time and ran 'rfkill list all' between each. None of these removed the hardware block.

@chili555, thanks for the insight. The bcm43xx already existed in some of the .conf files for some reason. Since this is all new to me I incorrectly assumed that the 'x' were wild variable placeholders.

One interesting data point... FN + F1 on this laptop puts the laptop to sleep. When waking the system back up, the LED associated with the hardware wifi enable switch lite up for a brief moment and then went out again. It seems that something in the system is forcing the hardware switch to be interpreted as off...

Any other ideas out there?

---

### Post by hays-joe on 2018-09-26
Well... I'm embarrassed to say that this was 'user error' once again. When I checked the BIOS I was looking to verify that wifi was enabled. I also saw that wifi was configured to be controlled by the hardware switch. Not thinking deeply enough about this I then thought it was configured correctly... 

Turns out that since Ubuntu drivers are not able to read the switch state, then by changing the BIOS configuration so wifi is NOT enabled by the hardware switch, the hardware block was removed. Now everything is working as expected. 

Thanks again to chili555 and jeremy31 for trying to help.

---

### Post by chili555 on 2018-09-26
> Turns out that since Ubuntu drivers are not able to read the switch state, then by changing the BIOS configuration so wifi is NOT enabled by the hardware switch, the hardware block was removed. Now everything is working as expected. Wow! That is an interesting result and, to me at least, new information. We are very glad that you posted the answer so that other Dell owners can search and see it.

Glad it's working as expected.

---

