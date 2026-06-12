---
title: "Slow WiFi connection DWA 131 rev.B1 - Ubuntu 16.04 LTS"
date: 2017-06-21
forum: Networking &amp; Wireless
---

### Post by artuist on 2017-06-21
For the last day or two I've been trying to speed the WiFi on this USB adapter without luck.
Willing to offer any logs or anything that's needed to fix this.
I just switched to Ubuntu so I immediately saw the difference from the speed I had on Windows 10
Download Speed used to be around 12-16Mbps and now It's around 1 or 2 and in general feels quite sluggish. 
Any help would be appreciated!
Thanks in advance!
```
artuist@artuist-desktop:~$ sudo lshw -C network  *-network               
       description: Ethernet interface
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: enp2s0
       version: 11
       serial: d0:50:99:37:d7:6d
       size: 10Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=rtl8168g-2_0.0.1 02/06/13 latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:38 ioport:d000(size=256) memory:fe900000-fe900fff memory:d0300000-d0303fff
  *-network
       description: Wireless interface
       physical id: 1
       bus info: usb@2:2
       logical name: wlxd8fee33ee03a
       serial: d8:fe:e3:3e:e0:3a
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=rtl8192cu ip=192.168.1.49 multicast=yes wireless=IEEE 802.11bg



```

---

### Post by chili555 on 2017-06-21
Please run and post:```
lsmod | grep rtl
uname -r
```

---

### Post by artuist on 2017-06-21
4.8.0-56-generic

---

### Post by chili555 on 2017-06-21
How about the first command??

---

### Post by artuist on 2017-06-22
It didn't return anything

---

### Post by artuist on 2017-06-22
lsmod by itself returned this
```
Module                  Size  Used by
8192cu                532480  0
mac80211              761856  0
cfg80211              581632  1 mac80211
binfmt_misc            20480  1
kvm_amd                73728  0
kvm                   598016  1 kvm_amd
snd_hda_codec_realtek    86016  1
snd_hda_codec_generic    73728  1 snd_hda_codec_realtek
snd_hda_codec_hdmi     45056  1
irqbypass              16384  1 kvm
snd_hda_intel          36864  5
crct10dif_pclmul       16384  0
crc32_pclmul           16384  0
snd_hda_codec         135168  4 snd_hda_intel,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_hda_codec_realtek
ghash_clmulni_intel    16384  0
aesni_intel           167936  0
fam15h_power           16384  0
k10temp                16384  0
snd_hda_core           86016  5 snd_hda_intel,snd_hda_codec,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_hda_codec_realtek
aes_x86_64             20480  1 aesni_intel
lrw                    16384  1 aesni_intel
glue_helper            16384  1 aesni_intel
ablk_helper            16384  1 aesni_intel
cryptd                 24576  3 ablk_helper,ghash_clmulni_intel,aesni_intel
input_leds             16384  0
joydev                 20480  0
snd_seq_midi           16384  0
snd_seq_midi_event     16384  1 snd_seq_midi
snd_hwdep              16384  1 snd_hda_codec
snd_pcm               110592  4 snd_hda_intel,snd_hda_codec,snd_hda_core,snd_hda_codec_hdmi
snd_rawmidi            32768  1 snd_seq_midi
serio_raw              16384  0
snd_seq                69632  2 snd_seq_midi_event,snd_seq_midi
snd_seq_device         16384  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              32768  2 snd_seq,snd_pcm
i2c_piix4              24576  0
snd                    86016  21 snd_hda_intel,snd_hwdep,snd_seq,snd_hda_codec,snd_timer,snd_rawmidi,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_seq_device,snd_hda_codec_realtek,snd_pcm
soundcore              16384  1 snd
shpchp                 36864  0
mac_hid                16384  0
parport_pc             32768  0
ppdev                  20480  0
lp                     20480  0
parport                49152  3 lp,parport_pc,ppdev
autofs4                40960  2
hid_generic            16384  0
pata_acpi              16384  0
usbhid                 53248  0
hid                   122880  2 hid_generic,usbhid
amdkfd                139264  1
amd_iommu_v2           20480  1 amdkfd
amdgpu               2150400  75
amdttm                102400  1 amdgpu
amdkcl                 32768  1 amdgpu
i2c_algo_bit           16384  1 amdgpu
psmouse               139264  0
drm_kms_helper        167936  1 amdgpu
syscopyarea            16384  1 drm_kms_helper
pata_atiixp            16384  0
sysfillrect            16384  1 drm_kms_helper
sysimgblt              16384  1 drm_kms_helper
fb_sys_fops            16384  1 drm_kms_helper
ahci                   36864  3
libahci                32768  1 ahci
drm                   368640  12 amdttm,amdgpu,amdkcl,drm_kms_helper
r8169                  81920  0
mii                    16384  1 r8169
fjes                   28672  0
video                  40960  0



```
From what I looked up, grep searches for a certain pattern but looks like it doesn't work in this case since the module is called 8192cu and doesn't have rtl before it (it's on the first line obviously), so using 8192 with grep did actually find it.

---

### Post by artuist on 2017-06-22
So I tried to install some fixed drivers for it with these
```

wget https://launchpad.net/~hanipouspilot/+archive/ubuntu/rtlwifi/+files/rtl8192cu-dkms_0.2_all.deb
sudo dpkg -i  rtl8192cu-dkms_0.2_all.deb

```
I did try to add the repository but then it wouldn't find the certain package so I did this.
Restarted and atm I consider this solved since it gets me around 7-8Mbps which is kinda normal since I also moved my computer a bit further from my router.
Thanks anyways.

---

### Post by chili555 on 2017-06-22
I assume that the reason that the original rtl drivers didn't load and appear with grep is that one of your attempts to install a different driver is that all of the rtl drivers were blacklisted. In fact, I suspect that the real reason for your low speeds is that two conflicting drivers loaded and that just one needed to be blacklisted. We have seen this many times.

If it is solved to your satisfaction, then all is well.

---

