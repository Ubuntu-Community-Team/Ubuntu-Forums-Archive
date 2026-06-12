---
title: "Wifi connection keeps disconnecting on Asus Laptop"
date: 2017-03-16
forum: Networking &amp; Wireless
---

### Post by tekek on 2017-03-16
My Asus laptop has extremely flaky wifi connection and it disconnects every few minutes. Upon installation of Ubuntu the wifi driver didnt work at all. Here is what I have done since installation:

[LIST=1]
[*]Installed the MT7630E driver for my computer and started getting a connection but disconnected frequently.
[*]Made a hotkey to refresh wifi as it would not connect again otherwise with a hotkey that executed the following: gksudo systemctl restart network-manager
[*]Installed the driver again with dkms make to keep it working after updates
[*]tried turning the wifi.powersave to = 2
[*]tried disabling ipv6
[/LIST]

I have no idea what to do and havent found any answers anywhere besides installing the driver. Any help would be extremely appreciated. 

[http://paste.ubuntu.com/24191754/](http://paste.ubuntu.com/24191754/)


```
lsusb results:
Bus 001 Device 002: ID 8087:8000 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 002 Device 004: ID 0457:10c0 Silicon Integrated Systems Corp. 
Bus 002 Device 003: ID 0bda:57bc Realtek Semiconductor Corp. 
Bus 002 Device 002: ID 0e8d:763f MediaTek Inc. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub



**lsmod results: **
Module                  Size  Used by
ccm                    20480  0
bnep                   20480  2
binfmt_misc            20480  1
nls_iso8859_1          16384  1
btusb                  45056  0
btrtl                  16384  1 btusb
btbcm                  16384  1 btusb
btintel                16384  1 btusb
bluetooth             557056  12 btrtl,btintel,bnep,btbcm,btusb
intel_rapl             20480  0
x86_pkg_temp_thermal    16384  0
intel_powerclamp       16384  0
asus_nb_wmi            24576  0
asus_wmi               28672  1 asus_nb_wmi
coretemp               16384  0
sparse_keymap          16384  1 asus_wmi
kvm_intel             192512  0
uvcvideo               90112  0
kvm                   598016  1 kvm_intel
videobuf2_vmalloc      16384  1 uvcvideo
videobuf2_memops       16384  1 videobuf2_vmalloc
videobuf2_v4l2         24576  1 uvcvideo
irqbypass              16384  1 kvm
snd_hda_codec_hdmi     45056  1
hid_multitouch         20480  0
videobuf2_core         40960  2 uvcvideo,videobuf2_v4l2
videodev              180224  3 uvcvideo,videobuf2_core,videobuf2_v4l2
media                  40960  2 uvcvideo,videodev
snd_hda_codec_realtek    86016  1
snd_hda_codec_generic    73728  1 snd_hda_codec_realtek
snd_hda_intel          36864  5
snd_soc_rt5640        118784  0
snd_soc_rl6231         16384  1 snd_soc_rt5640
arc4                   16384  2
crct10dif_pclmul       16384  0
snd_soc_core          233472  1 snd_soc_rt5640
snd_compress           20480  1 snd_soc_core
ac97_bus               16384  1 snd_soc_core
mt7630e               180224  0
crc32_pclmul           16384  0
snd_hda_codec         135168  4 snd_hda_intel,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_hda_codec_realtek
ghash_clmulni_intel    16384  0
snd_hda_core           86016  5 snd_hda_intel,snd_hda_codec,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_hda_codec_realtek
snd_pcm_dmaengine      16384  1 snd_soc_core
snd_hwdep              16384  1 snd_hda_codec
aesni_intel           167936  0
snd_pcm               110592  7 snd_hda_intel,snd_hda_codec,snd_pcm_dmaengine,snd_hda_core,snd_soc_rt5640,snd_hda_codec_hdmi,snd_soc_core
aes_x86_64             20480  1 aesni_intel
mac80211              761856  1 mt7630e
lrw                    16384  1 aesni_intel
snd_seq_midi           16384  0
glue_helper            16384  1 aesni_intel
snd_seq_midi_event     16384  1 snd_seq_midi
ablk_helper            16384  1 aesni_intel
snd_rawmidi            32768  1 snd_seq_midi
ak8975                 20480  0
cryptd                 24576  3 ablk_helper,ghash_clmulni_intel,aesni_intel
snd_seq                69632  2 snd_seq_midi_event,snd_seq_midi
cfg80211              581632  2 mac80211,mt7630e
snd_seq_device         16384  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              32768  2 snd_seq,snd_pcm
eeprom_93cx6           16384  1 mt7630e
intel_cstate           16384  0
inv_mpu6050_i2c        16384  0
intel_rapl_perf        16384  0
inv_mpu6050            20480  1 inv_mpu6050_i2c
rtsx_pci_ms            20480  0
industrialio_triggered_buffer    16384  2 ak8975,inv_mpu6050
kfifo_buf              16384  1 industrialio_triggered_buffer
snd                    86016  23 snd_compress,snd_hda_intel,snd_hwdep,snd_seq,snd_hda_codec,snd_timer,snd_rawmidi,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_seq_device,snd_hda_codec_realtek,snd_soc_core,snd_pcm
industrialio           65536  4 ak8975,inv_mpu6050,industrialio_triggered_buffer,kfifo_buf
joydev                 20480  0
input_leds             16384  0
soundcore              16384  1 snd
memstick               20480  1 rtsx_pci_ms
serio_raw              16384  0
i2c_mux                16384  1 inv_mpu6050_i2c
mei_me                 40960  0
mei                   102400  1 mei_me
elan_i2c               36864  0
spi_pxa2xx_platform    24576  0
snd_soc_sst_acpi       16384  0
snd_soc_sst_match      16384  1 snd_soc_sst_acpi
dw_dmac                16384  0
dw_dmac_core           24576  1 dw_dmac
i2c_designware_platform    16384  0
8250_dw                16384  0
shpchp                 36864  0
i2c_designware_core    20480  1 i2c_designware_platform
asus_wireless          16384  0
lpc_ich                24576  0
mac_hid                16384  0
tifm_sd                20480  0
tifm_core              16384  1 tifm_sd
parport_pc             32768  0
ppdev                  20480  0
lp                     20480  0
parport                49152  3 lp,parport_pc,ppdev
autofs4                40960  2
usbhid                 53248  0
rtsx_pci_sdmmc         24576  0
i915                 1310720  153
psmouse               139264  0
i2c_algo_bit           16384  1 i915
drm_kms_helper        167936  1 i915
syscopyarea            16384  1 drm_kms_helper
sysfillrect            16384  1 drm_kms_helper
sysimgblt              16384  1 drm_kms_helper
fb_sys_fops            16384  1 drm_kms_helper
ahci                   36864  3
libahci                32768  1 ahci
r8169                  81920  0
drm                   368640  7 i915,drm_kms_helper
rtsx_pci               57344  2 rtsx_pci_sdmmc,rtsx_pci_ms
mii                    16384  1 r8169
wmi                    16384  1 asus_wmi
video                  40960  2 asus_wmi,i915
i2c_hid                20480  0
hid                   122880  3 i2c_hid,usbhid,hid_multitouch
sdhci_acpi             16384  0
sdhci                  45056  1 sdhci_acpi
fjes                   28672  0


**iwconfig:**
wlp3s0f0  IEEE 802.11  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
enp2s0f1  no wireless extensions.


lo        no wireless extensions.
```

---

### Post by praseodym on 2017-03-17
The pasted output shows five networks named "PAWS-Secure". Add the MAC address of the AP you want to connect to to the field BSSID in the network-manager profile.

---

### Post by tekek on 2017-03-17
It isn't just on those networks that I have the issue with. The reason there are so many is due to the fact that I am on a college campus and they have a ton of routers. At home, the problem still prevails.

The network manager itself just gives up and stops searching for any routers.

---

