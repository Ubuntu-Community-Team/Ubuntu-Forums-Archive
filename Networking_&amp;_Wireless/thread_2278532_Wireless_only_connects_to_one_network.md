---
title: "Wireless only connects to one network"
date: 2015-05-17
forum: Networking &amp; Wireless
---

### Post by cuthbert.nibbles on 2015-05-17
Hello Ubuntu Community! Thank you very much for taking the time to look at my post, I usually don't bug online forums for help but I'm totally stumped on this one. I've been in and out of Linux for the better part of my life, I recently set up an old laptop as a home server to play around with. But that's not where my problem sits.

I have an MSI GE60 2PL Apache, and for the life of me I can't get the Wi-Fi to work. I had a bit of a problem with the NVidia GPU, but I sorted that out. Everything else works fine, but no Wi-Fi; and a laptop without Wi-Fi is useless to me. Pulling from [http://ubuntuforums.org/showthread.php?t=2277786](http://ubuntuforums.org/showthread.php?t=2277786) here's a few diagnostics:

cat /etc/lsb-release; uname -a
```

DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=15.04
DISTRIB_CODENAME=vivid
DISTRIB_DESCRIPTION="Ubuntu 15.04"
Linux unknown 3.19.0-16-generic #16-Ubuntu SMP Thu Apr 30 16:09:58 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux

```

lspci -nnk | grep -iA2 net
```

03:00.0 Ethernet controller [0200]: Qualcomm Atheros Killer E220x Gigabit Ethernet Controller [1969:e091] (rev 13)
    Subsystem: Micro-Star International Co., Ltd. [MSI] Device [1462:1113]
    Kernel driver in use: alx
--
05:00.0 Network controller [0280]: Intel Corporation Wireless 3160 [8086:08b3] (rev 83)
    Subsystem: Intel Corporation Dual Band Wireless-AC 3160 [8086:0070]
    Kernel driver in use: iwlwifi

```

lsusb
```

Bus 004 Device 002: ID 8087:8000 Intel Corp. 
Bus 004 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 004: ID 5986:014c Acer, Inc 
Bus 003 Device 003: ID 8087:07dc Intel Corp. 
Bus 003 Device 002: ID 8087:8008 Intel Corp. 
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 002: ID 046d:c531 Logitech, Inc. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

iwconfig
```

wlan0     IEEE 802.11abgn  ESSID:"BowzNET"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=22 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
eth1      no wireless extensions.

lo        no wireless extensions.

```

lsmod
```
Module                  Size  Used by
cpuid                  16384  0 
wl                   6369280  0 
bbswitch               16384  0 
rfcomm                 69632  8 
bnep                   20480  2 
nls_iso8859_1          16384  2 
dm_crypt               24576  1 
nvidia               8380416  43 
intel_rapl             20480  0 
iosf_mbi               16384  1 intel_rapl
arc4                   16384  2 
uvcvideo               90112  0 
videobuf2_vmalloc      16384  1 uvcvideo
x86_pkg_temp_thermal    16384  0 
intel_powerclamp       20480  0 
videobuf2_memops       16384  1 videobuf2_vmalloc
coretemp               16384  0 
videobuf2_core         49152  1 uvcvideo
v4l2_common            16384  1 videobuf2_core
iwlmvm                278528  0 
kvm_intel             151552  0 
videodev              159744  3 uvcvideo,v4l2_common,videobuf2_core
kvm                   483328  1 kvm_intel
media                  24576  2 uvcvideo,videodev
mac80211              720896  1 iwlmvm
crct10dif_pclmul       16384  0 
crc32_pclmul           16384  0 
ghash_clmulni_intel    16384  0 
snd_hda_codec_realtek    86016  1 
snd_hda_codec_generic    69632  1 snd_hda_codec_realtek
snd_hda_codec_hdmi     53248  1 
aesni_intel           172032  2743 
snd_soc_rt5640         94208  0 
aes_x86_64             20480  1 aesni_intel
snd_hda_intel          32768  10 
iwlwifi               196608  1 iwlmvm
snd_soc_rl6231         16384  1 snd_soc_rt5640
mxm_wmi                16384  0 
snd_soc_core          196608  1 snd_soc_rt5640
lrw                    16384  1 aesni_intel
gf128mul               16384  1 lrw
msi_wmi                16384  0 
snd_hda_controller     32768  1 snd_hda_intel
glue_helper            16384  1 aesni_intel
sparse_keymap          16384  1 msi_wmi
snd_hda_codec         143360  5 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_hda_intel,snd_hda_controller
snd_compress           20480  1 snd_soc_core
snd_hwdep              20480  1 snd_hda_codec
snd_pcm_dmaengine      16384  1 snd_soc_core
cfg80211              540672  4 wl,iwlwifi,mac80211,iwlmvm
ablk_helper            16384  1 aesni_intel
rtsx_pci_ms            20480  0 
btusb                  32768  0 
joydev                 20480  0 
bluetooth             491520  22 bnep,btusb,rfcomm
memstick               20480  1 rtsx_pci_ms
serio_raw              16384  0 
snd_pcm               106496  7 snd_soc_rt5640,snd_soc_core,snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel,snd_hda_controller,snd_pcm_dmaengine
cryptd                 20480  1374 ghash_clmulni_intel,aesni_intel,ablk_helper
snd_seq_midi           16384  0 
i2c_hid                20480  0 
snd_seq_midi_event     16384  1 snd_seq_midi
snd_rawmidi            32768  1 snd_seq_midi
snd_seq                69632  2 snd_seq_midi_event,snd_seq_midi
snd_seq_device         16384  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              32768  2 snd_pcm,snd_seq
mei_me                 20480  0 
ie31200_edac           16384  0 
snd                    90112  33 snd_hda_codec_realtek,snd_soc_core,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec_generic,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_compress
edac_core              53248  1 ie31200_edac
mei                    90112  1 mei_me
soundcore              16384  2 snd,snd_hda_codec
i2c_designware_platform    16384  0 
dw_dmac                16384  0 
i2c_designware_core    16384  1 i2c_designware_platform
dw_dmac_core           24576  1 dw_dmac
spi_pxa2xx_platform    24576  0 
lpc_ich                24576  0 
shpchp                 40960  0 
snd_soc_sst_acpi       16384  0 
mac_hid                16384  0 
8250_dw                16384  0 
wmi                    20480  2 msi_wmi,mxm_wmi
parport_pc             32768  0 
ppdev                  20480  0 
lp                     20480  0 
parport                45056  3 lp,ppdev,parport_pc
autofs4                40960  2 
mmc_block              36864  2 
hid_generic            16384  0 
usbhid                 53248  0 
hid                   110592  3 i2c_hid,hid_generic,usbhid
i915                 1052672  6 
rtsx_pci_sdmmc         24576  0 
i2c_algo_bit           16384  1 i915
drm_kms_helper        122880  1 i915
psmouse               118784  0 
ahci                   36864  3 
drm                   344064  7 i915,drm_kms_helper,nvidia
libahci                32768  1 ahci
alx                    36864  0 
rtsx_pci               49152  2 rtsx_pci_ms,rtsx_pci_sdmmc
mdio                   16384  1 alx
video                  20480  1 i915
sdhci_acpi             16384  0 
sdhci                  45056  1 sdhci_acpi

```

If you need anything else, just let me know. Mi config es su config. Thank you so very much!

---

### Post by grahammechanical on 2015-05-17
As far as I can tell you have a working wireless adapter - an Intel wireless 3160 and it has a kernel driver that is described as "in use" - iwlwifi. Network manager has a connection to BowzNET but you are not currently connected to the access point.

Run this command

```
sudo iwlist wlan0 scan
```

That should give a list of wireless access points within range. If it does that then Ubuntu has identified the wireless adapter and has installed a driver for it and is using it. The problem then most likely comes down to making a connection to a particular wireless access point. I do not understand what you mean by the title of this thread.

Right now my wireless adapter is detecting 10 wireless access points but I can only connect to one and that is my wireless access point that have have the pass phrase or wireless key for. These others I cannot access as I do not have the correct pass phrase. Nor, do I want to access them.

Regards.

---

### Post by cuthbert.nibbles on 2015-05-17
Thanks for the quick response grahammechanical! I totally forgot to explain that, there is one Wi-Fi network at my school that for some reason works. Every other network I've tried to connect to (both of my home network, my neighbour's network, etc) fails. But as sure as the sun rises this computer's Wi-Fi works at school. Like my home network, the school network uses WPA encryption, but I've tried connecting to an unsecured network and it still fails. Using WICD, it would fail during the "Validating Authentication" step. I've since stopped using WICD.
Right now I'm using a LAN cable to connect to BowzNET, that might be why it says I'm connected to it?
So sorry about that, thanks for the reply.

---

### Post by cuthbert.nibbles on 2015-05-17
[SIZE=3]Update #1:[/SIZE][SIZE=3][/SIZE]
After about the 60th reboot, BowzNET has suddenly connected (literally the only things I changed since my last post was installing Blender and SuperTux). There's a chance one of the Blender Libraries were required by the network chain, but I'm not the expert. I'll try a few more networks, but for now things seem fine.
Thank you very much for your help!
[SIZE=3]Update #2:
[/SIZE]Signed into another network (the third one) this evening. So it seems to have been fixed, I likely screwed up one of the libraries for the Network Manager and (maybe?) fixed it with the installs, I don't know. But it's working now, and I'd like to thank everyone for their help!

---

