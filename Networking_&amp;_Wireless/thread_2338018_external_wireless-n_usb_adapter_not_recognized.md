---
title: "external wireless-n usb adapter not recognized"
date: 2016-09-23
forum: Networking &amp; Wireless
---

### Post by ald2 on 2016-09-23
I have a Compaq Presario CQ56 laptop.  My Ralink RT5390 wifi card is junk and slow.  I have an external Zoom 300M Wireless-N USB adapter.  It worked for a second, but on reboot it no longer exists.  I might have too many things going on.  Any help would be greatly appreciated.  Ubuntu 14.04.5 LTS installed.


```
Module                  Size  Used by
snd_hrtimer            16384  1 
drbg                   28672  1 
ansi_cprng             16384  0 
ctr                    16384  2 
ccm                    20480  2 
dm_crypt               28672  0 
snd_hda_codec_realtek    86016  1 
snd_hda_codec_generic    73728  1 snd_hda_codec_realtek
gpio_ich               16384  0 
hp_wmi                 16384  0 
sparse_keymap          16384  1 hp_wmi
snd_hda_intel          36864  3 
arc4                   16384  2 
snd_hda_codec         135168  3 snd_hda_codec_realtek,snd_hda_codec_generic,snd_hda_intel
snd_hda_core           73728  4 snd_hda_codec_realtek,snd_hda_codec_generic,snd_hda_codec,snd_hda_intel
snd_hwdep              16384  1 snd_hda_codec
rt2800pci              16384  0 
rt2800mmio             20480  1 rt2800pci
rt2800lib              90112  2 rt2800pci,rt2800mmio
rt2x00pci              16384  1 rt2800pci
snd_pcm               106496  3 snd_hda_codec,snd_hda_intel,snd_hda_core
rt2x00mmio             16384  2 rt2800pci,rt2800mmio
rt2x00lib              53248  5 rt2x00pci,rt2800lib,rt2800pci,rt2800mmio,rt2x00mmio
snd_seq_midi           16384  0 
snd_seq_midi_event     16384  1 snd_seq_midi
mac80211              733184  3 rt2x00lib,rt2x00pci,rt2800lib
snd_rawmidi            32768  1 snd_seq_midi
dm_multipath           24576  0 
joydev                 20480  0 
input_leds             16384  0 
snd_seq                69632  3 snd_seq_midi_event,snd_seq_midi
serio_raw              16384  0 
cfg80211              557056  2 mac80211,rt2x00lib
snd_seq_device         16384  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              32768  3 snd_hrtimer,snd_pcm,snd_seq
hid_logitech_hidpp     20480  0 
rfcomm                 69632  0 
bnep                   20480  2 
lpc_ich                24576  0 
bluetooth             516096  10 bnep,rfcomm
snd                    81920  17 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec_generic,snd_hda_codec,snd_hda_intel,snd_seq_device
eeprom_93cx6           16384  1 rt2800pci
crc_ccitt              16384  1 rt2800lib
parport_pc             36864  0 
ppdev                  20480  0 
shpchp                 36864  0 
soundcore              16384  1 snd
coretemp               16384  0 
binfmt_misc            20480  1 
mac_hid                16384  0 
lp                     20480  0 
parport                49152  3 lp,ppdev,parport_pc
btrfs                 966656  0 
xor                    24576  1 btrfs
raid6_pq              102400  1 btrfs
dm_mirror              24576  0 
dm_region_hash         20480  1 dm_mirror
dm_log                 20480  2 dm_region_hash,dm_mirror
hid_logitech_dj        20480  0 
usbhid                 49152  0 
hid                   118784  3 usbhid,hid_logitech_dj,hid_logitech_hidpp
i915                 1208320  3 
i2c_algo_bit           16384  1 i915
drm_kms_helper        143360  1 i915
ahci                   36864  1 
syscopyarea            16384  1 drm_kms_helper
sysfillrect            16384  1 drm_kms_helper
psmouse               122880  0 
sysimgblt              16384  1 drm_kms_helper
libahci                32768  1 ahci
r8169                  81920  0 
mii                    16384  1 r8169
fb_sys_fops            16384  1 drm_kms_helper
drm                   360448  5 i915,drm_kms_helper
fjes                   28672  0 
video                  40960  1 i915
wmi                    20480  1 hp_wmi


eth0      Link encap:Ethernet  HWaddr 78:ac:c0:52:23:02  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:1659 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1659 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1 
          RX bytes:149261 (149.2 KB)  TX bytes:149261 (149.2 KB)

wlan0     Link encap:Ethernet  HWaddr 88:9f:fa:22:5d:2b  
          inet addr:192.168.86.31  Bcast:192.168.86.255  Mask:255.255.255.0
          inet6 addr: fe80::8a9f:faff:fe22:5d2b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:45351 errors:0 dropped:0 overruns:0 frame:0
          TX packets:32330 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:61523761 (61.5 MB)  TX bytes:3392380 (3.3 MB)
```

---

