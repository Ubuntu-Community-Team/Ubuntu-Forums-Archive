---
title: "RT3090, wi-fi connection problem"
date: 2023-03-24
forum: Networking &amp; Wireless
---

### Post by y-a-d on 2023-03-24
It scans and sees the networks, when connecting to a particular network it asks for a password and the end - it tries to connect and drops out after a while without even connecting. I have seen many reports of problems with this particular chip and the rt2800pci driver. I saw a guy on some forum where he disabled the 2800 module and got the 2860 to work, but I've been struggling for two days and can't resolve the issue using this or that method.

uname -a

```

02:00.0 Network controller: Ralink corp. RT3090 Wireless 802.11n 1T/1R PCIe
        Subsystem: Hewlett-Packard Company RT3090 Wireless 802.11n 1T/1R PCIe
        Physical Slot: 1
        Flags: bus master, fast devsel, latency 0, IRQ 17
        Memory at 98800000 (32-bit, non-prefetchable) [size=64K]
        Capabilities: <access denied>
        Kernel driver in use: rt2800pci
        Kernel modules: rt2800pci

```

lsmod

```

Module                  Size  Used by
rfcomm                 86016  4
bnep                   28672  2
uvcvideo              114688  0
snd_hda_codec_hdmi     81920  2
snd_hda_codec_idt      65536  1
snd_hda_codec_generic   102400  1 snd_hda_codec_idt
btusb                  61440  0
videobuf2_vmalloc      20480  1 uvcvideo
ledtrig_audio          16384  1 snd_hda_codec_generic
videobuf2_memops       20480  1 videobuf2_vmalloc
coretemp               24576  0
rt2800pci              16384  0
rt2800mmio             24576  1 rt2800pci
btrtl                  24576  1 btusb
videobuf2_v4l2         32768  1 uvcvideo
rt2800lib             143360  2 rt2800mmio,rt2800pci
videobuf2_common       81920  4 videobuf2_vmalloc,videobuf2_v4l2,uvcvideo,videobuf2_memops
btbcm                  24576  1 btusb
videodev              274432  3 videobuf2_v4l2,uvcvideo,videobuf2_common
rt2x00pci              16384  1 rt2800pci
btintel                40960  1 btusb
rt2x00mmio             16384  2 rt2800mmio,rt2800pci
snd_hda_intel          53248  3
rt2x00lib              73728  5 rt2x00mmio,rt2x00pci,rt2800mmio,rt2800pci,rt2800lib
snd_intel_dspcfg       36864  1 snd_hda_intel
mac80211             1314816  3 rt2x00pci,rt2x00lib,rt2800lib
snd_intel_sdw_acpi     20480  1 snd_intel_dspcfg
btmtk                  16384  1 btusb
mc                     65536  4 videodev,videobuf2_v4l2,uvcvideo,videobuf2_common
snd_hda_codec         176128  4 snd_hda_codec_generic,snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec_idt
hp_wmi                 20480  0
joydev                 32768  0
sparse_keymap          16384  1 hp_wmi
platform_profile       16384  1 hp_wmi
input_leds             16384  0
cfg80211             1044480  2 rt2x00lib,mac80211
bluetooth             827392  28 btrtl,btmtk,btintel,btbcm,bnep,btusb,rfcomm
snd_hda_core          114688  5 snd_hda_codec_generic,snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec,snd_hda_codec_idt
libarc4                16384  1 mac80211
eeprom_93cx6           16384  1 rt2800pci
serio_raw              20480  0
ecdh_generic           16384  1 bluetooth
snd_hwdep              20480  1 snd_hda_codec
wmi_bmof               16384  0
ecc                    40960  1 ecdh_generic
snd_pcm               155648  4 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec,snd_hda_core
snd_seq_midi           20480  0
snd_seq_midi_event     16384  1 snd_seq_midi
snd_rawmidi            45056  1 snd_seq_midi
snd_seq                77824  2 snd_seq_midi,snd_seq_midi_event
snd_seq_device         16384  3 snd_seq,snd_seq_midi,snd_rawmidi
snd_timer              40960  2 snd_seq,snd_pcm
snd                   114688  17 snd_hda_codec_generic,snd_seq,snd_seq_device,snd_hda_codec_hdmi,snd_hwdep,snd_hda_intel,snd_hda_codec,snd_timer,snd_pcm,snd_hda_codec_idt,snd_rawmidi
soundcore              16384  1 snd
mac_hid                16384  0
binfmt_misc            24576  1
sch_fq_codel           24576  6
msr                    16384  0
parport_pc             53248  0
ppdev                  24576  0
lp                     28672  0
parport                73728  3 parport_pc,lp,ppdev
efi_pstore             16384  0
ramoops                32768  0
pstore_blk             16384  0
pstore_zone            32768  1 pstore_blk
reed_solomon           28672  1 ramoops
ip_tables              32768  0
x_tables               57344  1 ip_tables
autofs4                45056  2
btrfs                1630208  0
blake2b_generic        20480  0
xor                    24576  1 btrfs
raid6_pq              122880  1 btrfs
libcrc32c              16384  1 btrfs
dm_mirror              24576  0
dm_region_hash         24576  1 dm_mirror
dm_log                 20480  2 dm_region_hash,dm_mirror
i915                 3129344  13
hid_generic            16384  0
drm_buddy              20480  1 i915
i2c_algo_bit           16384  1 i915
ttm                    98304  1 i915
usbhid                 65536  0
hid                   159744  2 usbhid,hid_generic
drm_display_helper    184320  1 i915
cec                    81920  2 drm_display_helper,i915
rc_core                65536  1 cec
drm_kms_helper        200704  2 drm_display_helper,i915
psmouse               180224  0
syscopyarea            16384  1 drm_kms_helper
r8169                 102400  0
sysfillrect            20480  1 drm_kms_helper
ahci                   49152  1
sysimgblt              20480  1 drm_kms_helper
lpc_ich                28672  0
libahci                49152  1 ahci
fb_sys_fops            16384  1 drm_kms_helper
realtek                32768  1
drm                   581632  16 drm_kms_helper,drm_display_helper,drm_buddy,i915,ttm
wmi                    32768  2 hp_wmi,wmi_bmof
video                  65536  1 i915

```

iwconfig

```

wls1      IEEE 802.11  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry short  long limit:2   RTS thr:off   Fragment thr:off
          Power Management:on

```

---

