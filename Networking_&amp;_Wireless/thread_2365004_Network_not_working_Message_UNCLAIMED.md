---
title: "Network not working: Message UNCLAIMED"
date: 2017-06-30
forum: Networking &amp; Wireless
---

### Post by leejonathan on 2017-06-30
Hello everyone, sorry to bother, but I have a quick question.

I recently bought a used Dell Latitude D531 **AMD** to wipe and install Ubuntu 16.04.2 LTS. I made a bootable USB stick and installed everything.
However, when trying to connect to a wireless network via the top menu bar, the wireless network wouldn't show up. In fact, the only viable internet connection listed was ethernet. I connected to ethernet, and everything is working fine. However, I would like to enable wireless connection on this computer, because I don't carry an ethernet cable everywhere I go.

So, I tried pressing the wireless hardware switch multiple times, but the wireless network option still wouldn't show up on the top menu bar. I looked at the BIOS, and I had the wireless switch enabled. At this point I concluded that it may not be a hardware issue, but a software issue. After reading troubleshooting tutorials, I entered the Terminal and entered:```
sudo lshw -C network
```

The results were as follows:
```

*-network UNCLAIMED     
       description: Network controller
       product: BCM4311 802.11a/b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0b:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: memory:fe8fc000-fe8fffff
  *-network
       description: Ethernet interface
       product: NetXtreme BCM5755M Gigabit Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: enp9s0
       version: 02
       serial: 00:22:19:d9:73:1a
       size: 1Gbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.137 duplex=full firmware=5755m-v3.29 ip=192.168.0.15 latency=0 link=yes multicast=yes port=twisted pair speed=1Gbit/s
       resources: irq:27 memory:fe7f0000-fe7fffff

```

From here, I noticed the "UNCLAIMED" text in the "Network controller" category, but not in the ethernet category, concluding that it must be something to do with that word.
I have already perused the other threads about this, but they were using different systems with different settings, leading me to create my own thread.

[B]FYI:
[/B]-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
```
lsb_release -a

```
gives
```

No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 16.04.2 LTS
Release:    16.04
Codename:    xenial

```
-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
```

lspci -nn | grep 0280

```
gives
```

0b:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11a/b/g [14e4:4312] (rev 01)

```
-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
```

iwconfig

```
gives
```

enp9s0    no wireless extensions.


lo        no wireless extensions.



```
-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
```

rfkill list all

```
produces no results, and
-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
```

lsmod

```
gives
```

Module                  Size  Used by
binfmt_misc            20480  1
dell_wmi               16384  0
dell_laptop            20480  0
sparse_keymap          16384  1 dell_wmi
dell_smbios            16384  2 dell_wmi,dell_laptop
dcdbas                 16384  1 dell_smbios
dell_smm_hwmon         16384  0
wl                   6447104  0
snd_hda_codec_hdmi     45056  1
snd_hda_codec_idt      57344  1
snd_hda_codec_generic    73728  1 snd_hda_codec_idt
snd_hda_intel          36864  3
snd_hda_codec         135168  4 snd_hda_intel,snd_hda_codec_idt,snd_hda_codec_hdmi,snd_hda_codec_generic
snd_hda_core           86016  5 snd_hda_intel,snd_hda_codec,snd_hda_codec_idt,snd_hda_codec_hdmi,snd_hda_codec_generic
snd_hwdep              16384  1 snd_hda_codec
snd_pcm               110592  4 snd_hda_intel,snd_hda_codec,snd_hda_core,snd_hda_codec_hdmi
snd_seq_midi           16384  0
snd_seq_midi_event     16384  1 snd_seq_midi
snd_rawmidi            32768  1 snd_seq_midi
snd_seq                69632  2 snd_seq_midi_event,snd_seq_midi
snd_seq_device         16384  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              32768  2 snd_seq,snd_pcm
kvm_amd                73728  0
kvm                   598016  1 kvm_amd
snd                    86016  17 snd_hda_intel,snd_hwdep,snd_seq,snd_hda_codec,snd_hda_codec_idt,snd_timer,snd_rawmidi,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_seq_device,snd_pcm
irqbypass              16384  1 kvm
soundcore              16384  1 snd
cfg80211              581632  1 wl
pcmcia                 69632  0
yenta_socket           49152  0
pcmcia_rsrc            20480  1 yenta_socket
joydev                 20480  0
pcmcia_core            24576  3 yenta_socket,pcmcia,pcmcia_rsrc
input_leds             16384  0
k8temp                 16384  0
serio_raw              16384  0
i2c_piix4              24576  0
shpchp                 36864  0
mac_hid                16384  0
parport_pc             32768  0
ppdev                  20480  0
lp                     20480  0
parport                49152  3 lp,parport_pc,ppdev
autofs4                40960  2
pata_acpi              16384  0
hid_generic            16384  0
usbhid                 53248  0
hid                   122880  3 hid_generic,usbhid
amdkfd                139264  1
amd_iommu_v2           20480  1 amdkfd
radeon               1515520  3
i2c_algo_bit           16384  1 radeon
ttm                   102400  1 radeon
psmouse               139264  0
drm_kms_helper        167936  1 radeon
firewire_ohci          40960  0
syscopyarea            16384  1 drm_kms_helper
sysfillrect            16384  1 drm_kms_helper
firewire_core          65536  1 firewire_ohci
crc_itu_t              16384  1 firewire_core
pata_atiixp            16384  0
sysimgblt              16384  1 drm_kms_helper
tg3                   163840  0
ahci                   36864  2
ptp                    20480  1 tg3
libahci                32768  1 ahci
pps_core               20480  1 ptp
fb_sys_fops            16384  1 drm_kms_helper
drm                   368640  6 radeon,ttm,drm_kms_helper
wmi                    16384  1 dell_wmi
video                  40960  2 dell_wmi,dell_laptop

```
-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

Please advise. Thanks!

---

