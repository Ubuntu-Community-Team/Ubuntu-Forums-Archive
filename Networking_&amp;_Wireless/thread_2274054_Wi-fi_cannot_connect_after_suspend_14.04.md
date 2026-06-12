---
title: "Wi-fi cannot connect after suspend 14.04"
date: 2015-04-17
forum: Networking &amp; Wireless
---

### Post by giokokos on 2015-04-17
When I wake up the computer from suspend, the wi-fi connection does not come up, and 'enable networking' becomes unticked. I have to restart the computer and the wi-fi connection comes up.

I have already tried the following [solution]("http://ubuntuforums.org/showthread.php?t=2218043&p=13000035#post13000035") as many users have reported that it worked for them but apparently not for me.

Some useful info about my system:

```

&#10140;  ~  uname -mr
4.0.0-040000-generic x86_64

```
```

&#10140;  ~  lspci -nnk                
00:00.0 Host bridge [0600]: Intel Corporation 3rd Gen Core processor DRAM Controller [8086:0154] (rev 09)
    Subsystem: Samsung Electronics Co Ltd Device [144d:c711]
    Kernel driver in use: ivb_uncore
00:01.0 PCI bridge [0604]: Intel Corporation Xeon E3-1200 v2/3rd Gen Core processor PCI Express Root Port [8086:0151] (rev 09)
    Kernel driver in use: pcieport
00:02.0 VGA compatible controller [0300]: Intel Corporation 3rd Gen Core processor Graphics Controller [8086:0166] (rev 09)
    Subsystem: Samsung Electronics Co Ltd Device [144d:c711]
    Kernel driver in use: i915
00:14.0 USB controller [0c03]: Intel Corporation 7 Series/C210 Series Chipset Family USB xHCI Host Controller [8086:1e31] (rev 04)
    Subsystem: Samsung Electronics Co Ltd Device [144d:c711]
    Kernel driver in use: xhci_hcd
00:16.0 Communication controller [0780]: Intel Corporation 7 Series/C210 Series Chipset Family MEI Controller #1 [8086:1e3a] (rev 04)
    Subsystem: Samsung Electronics Co Ltd Device [144d:c711]
    Kernel driver in use: mei_me
00:1a.0 USB controller [0c03]: Intel Corporation 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #2 [8086:1e2d] (rev 04)
    Subsystem: Samsung Electronics Co Ltd Device [144d:c711]
    Kernel driver in use: ehci-pci
00:1b.0 Audio device [0403]: Intel Corporation 7 Series/C210 Series Chipset Family High Definition Audio Controller [8086:1e20] (rev 04)
    Subsystem: Samsung Electronics Co Ltd Device [144d:c711]
    Kernel driver in use: snd_hda_intel
00:1c.0 PCI bridge [0604]: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 1 [8086:1e10] (rev c4)
    Kernel driver in use: pcieport
00:1c.3 PCI bridge [0604]: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 4 [8086:1e16] (rev c4)
    Kernel driver in use: pcieport
00:1d.0 USB controller [0c03]: Intel Corporation 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #1 [8086:1e26] (rev 04)
    Subsystem: Samsung Electronics Co Ltd Device [144d:c711]
    Kernel driver in use: ehci-pci
00:1f.0 ISA bridge [0601]: Intel Corporation HM76 Express Chipset LPC Controller [8086:1e59] (rev 04)
    Subsystem: Samsung Electronics Co Ltd Device [144d:c711]
    Kernel driver in use: lpc_ich
00:1f.2 SATA controller [0106]: Intel Corporation 7 Series Chipset Family 6-port SATA Controller [AHCI mode] [8086:1e03] (rev 04)
    Subsystem: Samsung Electronics Co Ltd Device [144d:c711]
    Kernel driver in use: ahci
00:1f.3 SMBus [0c05]: Intel Corporation 7 Series/C210 Series Chipset Family SMBus Controller [8086:1e22] (rev 04)
    Subsystem: Samsung Electronics Co Ltd Device [144d:c711]
01:00.0 3D controller [0302]: NVIDIA Corporation GF117M [GeForce 610M/710M/820M / GT 620M/625M/630M/720M] [10de:1140] (rev a1)
    Subsystem: Samsung Electronics Co Ltd GeForce 710M [144d:c711]
    Kernel driver in use: nouveau
02:00.0 Network controller [0280]: Qualcomm Atheros AR9485 Wireless Network Adapter [168c:0032] (rev 01)
    Subsystem: Samsung Electronics Co Ltd Device [144d:410e]
    Kernel driver in use: ath9k
03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 06)
    Subsystem: Samsung Electronics Co Ltd Device [144d:c711]
    Kernel driver in use: r8169

```
```

&#10140;  ~  cat /var/log/pm-suspend.log  
Initial commandline parameters: 
Wed Apr  1 23:51:44 EEST 2015: Running hooks for suspend.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:
/usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/000record-status suspend suspend:
/usr/lib/pm-utils/sleep.d/000record-status suspend suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/00logging suspend suspend:
Linux laptop 3.16.0-33-generic #44~14.04.1-Ubuntu SMP Fri Mar 13 10:33:29 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux
Module                  Size  Used by
ctr                    13049  0 
ccm                    17773  0 
bnep                   19624  2 
rfcomm                 69509  8 
nls_iso8859_1          12713  1 
snd_hda_codec_hdmi     47548  1 
snd_hda_codec_realtek    77467  1 
snd_hda_codec_generic    68937  1 snd_hda_codec_realtek
uvcvideo               81073  0 
videobuf2_vmalloc      13216  1 uvcvideo
videobuf2_memops       13362  1 videobuf2_vmalloc
videobuf2_core         59104  1 uvcvideo
v4l2_common            15681  1 videobuf2_core
videodev              153793  3 uvcvideo,v4l2_common,videobuf2_core
media                  21903  2 uvcvideo,videodev
snd_hda_intel          30469  3 
snd_hda_controller     31056  1 snd_hda_intel
snd_hda_codec         139682  5 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_hda_intel,snd_hda_controller
snd_hwdep              17698  1 snd_hda_codec
intel_rapl             18783  0 
x86_pkg_temp_thermal    14205  0 
intel_powerclamp       18823  0 
coretemp               13441  0 
kvm_intel             143590  0 
snd_pcm               104112  4 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel,snd_hda_controller
kvm                   452043  1 kvm_intel
arc4                   12608  2 
crct10dif_pclmul       14307  0 
crc32_pclmul           13133  0 
snd_seq_midi           13564  0 
snd_seq_midi_event     14899  1 snd_seq_midi
ath9k                 137283  0 
ghash_clmulni_intel    13230  0 
cryptd                 20359  1 ghash_clmulni_intel
snd_rawmidi            30876  1 snd_seq_midi
ath3k                  13331  0 
ath9k_common           25638  1 ath9k
ath9k_hw              446521  2 ath9k_common,ath9k
snd_seq                63074  2 snd_seq_midi_event,snd_seq_midi
ath                    29006  3 ath9k_common,ath9k,ath9k_hw
mac80211              652718  1 ath9k
joydev                 17393  0 
btusb                  32497  0 
serio_raw              13483  0 
cfg80211              494362  4 ath,ath9k_common,ath9k,mac80211
i915                  905954  4 
mei_me                 19696  0 
bluetooth             446409  23 bnep,ath3k,btusb,rfcomm
nouveau              1206535  1 
lpc_ich                21093  0 
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              29562  2 snd_pcm,snd_seq
snd                    79468  17 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec_generic,snd_hda_codec,snd_hda_intel,snd_seq_device
6lowpan_iphc           18702  1 bluetooth
soundcore              15047  2 snd,snd_hda_codec
ttm                    93588  1 nouveau
drm_kms_helper         61574  2 i915,nouveau
mei                    87875  1 mei_me
drm                   311018  9 ttm,i915,drm_kms_helper,nouveau
i2c_algo_bit           13413  2 i915,nouveau
shpchp                 37047  0 
mxm_wmi                13021  1 nouveau
video                  20128  2 i915,nouveau
wmi                    19193  2 mxm_wmi,nouveau
mac_hid                13227  0 
parport_pc             32741  0 
ppdev                  17671  0 
lp                     17759  0 
parport                42348  3 lp,ppdev,parport_pc
hid_logitech_dj        18469  0 
usbhid                 52616  0 
hid                   110426  4 usbhid,hid_logitech_dj
psmouse               106561  0 
ahci                   34062  5 
r8169                  71694  0 
libahci                32424  1 ahci
mii                    13934  1 r8169
             total       used       free     shared    buffers     cached
Mem:       8059604    6424700    1634904     800636     215900    2470260
-/+ buffers/cache:    3738540    4321064
Swap:     15625212     367248   15257964
/usr/lib/pm-utils/sleep.d/00logging suspend suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/00powersave suspend suspend:
/usr/lib/pm-utils/sleep.d/00powersave suspend suspend: success.


Running hook /etc/pm/sleep.d/10_grub-common suspend suspend:
/etc/pm/sleep.d/10_grub-common suspend suspend: success.


Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend:
/etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/50unload_alx suspend suspend:
/usr/lib/pm-utils/sleep.d/50unload_alx suspend suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend:
Failed to connect to non-global ctrl_ifname: (null)  error: No such file or directory
/usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/75modules suspend suspend:
Unloading kernel module r8169...Done.
/usr/lib/pm-utils/sleep.d/75modules suspend suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/90clock suspend suspend:
/usr/lib/pm-utils/sleep.d/90clock suspend suspend: not applicable.


Running hook /usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend:
/usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/95anacron suspend suspend:
stop: Unknown instance: 
/usr/lib/pm-utils/sleep.d/95anacron suspend suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend:
/usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend: not applicable.


Running hook /usr/lib/pm-utils/sleep.d/95led suspend suspend:
/usr/lib/pm-utils/sleep.d/95led suspend suspend: not applicable.


Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend:
Kernel modesetting video driver detected, not using quirks.
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/99video suspend suspend:
kernel.acpi_video_flags = 0
/usr/lib/pm-utils/sleep.d/99video suspend suspend: success.


Running hook /etc/pm/sleep.d/novatel_3g_suspend suspend suspend:
/etc/pm/sleep.d/novatel_3g_suspend suspend suspend: success.


Wed Apr  1 23:51:46 EEST 2015: performing suspend
Thu Apr  2 14:09:50 EEST 2015: Awake.
Thu Apr  2 14:09:50 EEST 2015: Running hooks for resume
Running hook /etc/pm/sleep.d/novatel_3g_suspend resume suspend:
/etc/pm/sleep.d/novatel_3g_suspend resume suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/99video resume suspend:
/usr/lib/pm-utils/sleep.d/99video resume suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend:
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/95led resume suspend:
/usr/lib/pm-utils/sleep.d/95led resume suspend: not applicable.


Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm resume suspend:


/dev/sda:
 setting Advanced Power Management level to 0xfe (254)
 APM_level    = 254
/usr/lib/pm-utils/sleep.d/95hdparm-apm resume suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/95anacron resume suspend:
/usr/lib/pm-utils/sleep.d/95anacron resume suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/94cpufreq resume suspend:
/usr/lib/pm-utils/sleep.d/94cpufreq resume suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/90clock resume suspend:
/usr/lib/pm-utils/sleep.d/90clock resume suspend: not applicable.


Running hook /usr/lib/pm-utils/sleep.d/75modules resume suspend:
Reloaded unloaded modules.
/usr/lib/pm-utils/sleep.d/75modules resume suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant resume suspend:
Failed to connect to non-global ctrl_ifname: (null)  error: No such file or directory
/usr/lib/pm-utils/sleep.d/60_wpa_supplicant resume suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/50unload_alx resume suspend:
/usr/lib/pm-utils/sleep.d/50unload_alx resume suspend: success.


Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate resume suspend:
/etc/pm/sleep.d/10_unattended-upgrades-hibernate resume suspend: success.


Running hook /etc/pm/sleep.d/10_grub-common resume suspend:
/etc/pm/sleep.d/10_grub-common resume suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/00powersave resume suspend:
/usr/lib/pm-utils/sleep.d/00powersave resume suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/00logging resume suspend:
/usr/lib/pm-utils/sleep.d/00logging resume suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/000record-status resume suspend:
/usr/lib/pm-utils/sleep.d/000record-status resume suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/000kernel-change resume suspend:
/usr/lib/pm-utils/sleep.d/000kernel-change resume suspend: success.


Thu Apr  2 14:09:51 EEST 2015: Finished.
Initial commandline parameters: 
Thu Apr  2 14:10:34 EEST 2015: Running hooks for suspend.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:
/usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/000record-status suspend suspend:
/usr/lib/pm-utils/sleep.d/000record-status suspend suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/00logging suspend suspend:
Linux laptop 3.16.0-33-generic #44~14.04.1-Ubuntu SMP Fri Mar 13 10:33:29 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux
Module                  Size  Used by
r8169                  71694  0 
mii                    13934  1 r8169
ctr                    13049  0 
ccm                    17773  0 
bnep                   19624  2 
rfcomm                 69509  8 
nls_iso8859_1          12713  1 
snd_hda_codec_hdmi     47548  1 
snd_hda_codec_realtek    77467  1 
snd_hda_codec_generic    68937  1 snd_hda_codec_realtek
uvcvideo               81073  0 
videobuf2_vmalloc      13216  1 uvcvideo
videobuf2_memops       13362  1 videobuf2_vmalloc
videobuf2_core         59104  1 uvcvideo
v4l2_common            15681  1 videobuf2_core
videodev              153793  3 uvcvideo,v4l2_common,videobuf2_core
media                  21903  2 uvcvideo,videodev
snd_hda_intel          30469  3 
snd_hda_controller     31056  1 snd_hda_intel
snd_hda_codec         139682  5 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_hda_intel,snd_hda_controller
snd_hwdep              17698  1 snd_hda_codec
intel_rapl             18783  0 
x86_pkg_temp_thermal    14205  0 
intel_powerclamp       18823  0 
coretemp               13441  0 
kvm_intel             143590  0 
snd_pcm               104112  4 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel,snd_hda_controller
kvm                   452043  1 kvm_intel
arc4                   12608  2 
crct10dif_pclmul       14307  0 
crc32_pclmul           13133  0 
snd_seq_midi           13564  0 
snd_seq_midi_event     14899  1 snd_seq_midi
ath9k                 137283  0 
ghash_clmulni_intel    13230  0 
cryptd                 20359  1 ghash_clmulni_intel
snd_rawmidi            30876  1 snd_seq_midi
ath3k                  13331  0 
ath9k_common           25638  1 ath9k
ath9k_hw              446521  2 ath9k_common,ath9k
snd_seq                63074  2 snd_seq_midi_event,snd_seq_midi
ath                    29006  3 ath9k_common,ath9k,ath9k_hw
mac80211              652718  1 ath9k
joydev                 17393  0 
btusb                  32497  0 
serio_raw              13483  0 
cfg80211              494362  4 ath,ath9k_common,ath9k,mac80211
i915                  905954  3 
mei_me                 19696  0 
bluetooth             446409  23 bnep,ath3k,btusb,rfcomm
nouveau              1206535  1 
lpc_ich                21093  0 
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              29562  2 snd_pcm,snd_seq
snd                    79468  17 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec_generic,snd_hda_codec,snd_hda_intel,snd_seq_device
6lowpan_iphc           18702  1 bluetooth
soundcore              15047  2 snd,snd_hda_codec
ttm                    93588  1 nouveau
drm_kms_helper         61574  2 i915,nouveau
mei                    87875  1 mei_me
drm                   311018  8 ttm,i915,drm_kms_helper,nouveau
i2c_algo_bit           13413  2 i915,nouveau
shpchp                 37047  0 
mxm_wmi                13021  1 nouveau
video                  20128  2 i915,nouveau
wmi                    19193  2 mxm_wmi,nouveau
mac_hid                13227  0 
parport_pc             32741  0 
ppdev                  17671  0 
lp                     17759  0 
parport                42348  3 lp,ppdev,parport_pc
hid_logitech_dj        18469  0 
usbhid                 52616  0 
hid                   110426  4 usbhid,hid_logitech_dj
psmouse               106561  0 
ahci                   34062  5 
libahci                32424  1 ahci
             total       used       free     shared    buffers     cached
Mem:       8059604    3296444    4763160     437284     218228    2081432
-/+ buffers/cache:     996784    7062820
Swap:     15625212     251172   15374040
/usr/lib/pm-utils/sleep.d/00logging suspend suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/00powersave suspend suspend:
/usr/lib/pm-utils/sleep.d/00powersave suspend suspend: success.


Running hook /etc/pm/sleep.d/10_grub-common suspend suspend:
/etc/pm/sleep.d/10_grub-common suspend suspend: success.


Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend:
/etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/50unload_alx suspend suspend:
/usr/lib/pm-utils/sleep.d/50unload_alx suspend suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend:
Failed to connect to non-global ctrl_ifname: (null)  error: No such file or directory
/usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/75modules suspend suspend:
Unloading kernel module r8169...Done.
/usr/lib/pm-utils/sleep.d/75modules suspend suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/90clock suspend suspend:
/usr/lib/pm-utils/sleep.d/90clock suspend suspend: not applicable.


Running hook /usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend:
/usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/95anacron suspend suspend:
/usr/lib/pm-utils/sleep.d/95anacron suspend suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend:
/usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend: not applicable.


Running hook /usr/lib/pm-utils/sleep.d/95led suspend suspend:
/usr/lib/pm-utils/sleep.d/95led suspend suspend: not applicable.


Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend:
Kernel modesetting video driver detected, not using quirks.
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/99video suspend suspend:
kernel.acpi_video_flags = 0
/usr/lib/pm-utils/sleep.d/99video suspend suspend: success.


Running hook /etc/pm/sleep.d/novatel_3g_suspend suspend suspend:
/etc/pm/sleep.d/novatel_3g_suspend suspend suspend: success.


Thu Apr  2 14:10:34 EEST 2015: performing suspend
Thu Apr  2 14:10:42 EEST 2015: Awake.
Thu Apr  2 14:10:42 EEST 2015: Running hooks for resume
Running hook /etc/pm/sleep.d/novatel_3g_suspend resume suspend:
/etc/pm/sleep.d/novatel_3g_suspend resume suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/99video resume suspend:
/usr/lib/pm-utils/sleep.d/99video resume suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend:
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/95led resume suspend:
/usr/lib/pm-utils/sleep.d/95led resume suspend: not applicable.


Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm resume suspend:


/dev/sda:
 setting Advanced Power Management level to 0xfe (254)
 APM_level    = 254
/usr/lib/pm-utils/sleep.d/95hdparm-apm resume suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/95anacron resume suspend:
/usr/lib/pm-utils/sleep.d/95anacron resume suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/94cpufreq resume suspend:
/usr/lib/pm-utils/sleep.d/94cpufreq resume suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/90clock resume suspend:
/usr/lib/pm-utils/sleep.d/90clock resume suspend: not applicable.


Running hook /usr/lib/pm-utils/sleep.d/75modules resume suspend:
Reloaded unloaded modules.
/usr/lib/pm-utils/sleep.d/75modules resume suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant resume suspend:
Failed to connect to non-global ctrl_ifname: (null)  error: No such file or directory
/usr/lib/pm-utils/sleep.d/60_wpa_supplicant resume suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/50unload_alx resume suspend:
/usr/lib/pm-utils/sleep.d/50unload_alx resume suspend: success.


Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate resume suspend:
/etc/pm/sleep.d/10_unattended-upgrades-hibernate resume suspend: success.


Running hook /etc/pm/sleep.d/10_grub-common resume suspend:
/etc/pm/sleep.d/10_grub-common resume suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/00powersave resume suspend:
/usr/lib/pm-utils/sleep.d/00powersave resume suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/00logging resume suspend:
/usr/lib/pm-utils/sleep.d/00logging resume suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/000record-status resume suspend:
/usr/lib/pm-utils/sleep.d/000record-status resume suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/000kernel-change resume suspend:
/usr/lib/pm-utils/sleep.d/000kernel-change resume suspend: success.


Thu Apr  2 14:10:44 EEST 2015: Finished.
Initial commandline parameters: 
Fri Apr  3 01:31:19 EEST 2015: Running hooks for suspend.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:
/usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/000record-status suspend suspend:
/usr/lib/pm-utils/sleep.d/000record-status suspend suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/00logging suspend suspend:
Linux laptop 3.16.0-33-generic #44~14.04.1-Ubuntu SMP Fri Mar 13 10:33:29 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux
Module                  Size  Used by
ctr                    13049  0 
ccm                    17773  0 
bnep                   19624  2 
rfcomm                 69509  8 
nls_iso8859_1          12713  1 
uvcvideo               81073  0 
videobuf2_vmalloc      13216  1 uvcvideo
videobuf2_memops       13362  1 videobuf2_vmalloc
videobuf2_core         59104  1 uvcvideo
v4l2_common            15681  1 videobuf2_core
videodev              153793  3 uvcvideo,v4l2_common,videobuf2_core
media                  21903  2 uvcvideo,videodev
intel_rapl             18783  0 
x86_pkg_temp_thermal    14205  0 
intel_powerclamp       18823  0 
coretemp               13441  0 
ath3k                  13331  0 
snd_hda_codec_hdmi     47548  1 
kvm_intel             143590  0 
snd_hda_codec_realtek    77467  1 
i915                  905954  6 
snd_hda_codec_generic    68937  1 snd_hda_codec_realtek
kvm                   452043  1 kvm_intel
snd_hda_intel          30469  3 
arc4                   12608  2 
btusb                  32497  0 
ath9k                 137283  0 
snd_hda_controller     31056  1 snd_hda_intel
ath9k_common           25638  1 ath9k
ath9k_hw              446521  2 ath9k_common,ath9k
bluetooth             446409  23 bnep,ath3k,btusb,rfcomm
snd_hda_codec         139682  5 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_hda_intel,snd_hda_controller
ath                    29006  3 ath9k_common,ath9k,ath9k_hw
snd_hwdep              17698  1 snd_hda_codec
snd_pcm               104112  4 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel,snd_hda_controller
mac80211              652718  1 ath9k
nouveau              1206535  1 
6lowpan_iphc           18702  1 bluetooth
crct10dif_pclmul       14307  0 
snd_seq_midi           13564  0 
snd_seq_midi_event     14899  1 snd_seq_midi
snd_rawmidi            30876  1 snd_seq_midi
snd_seq                63074  2 snd_seq_midi_event,snd_seq_midi
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
mxm_wmi                13021  1 nouveau
ttm                    93588  1 nouveau
cfg80211              494362  4 ath,ath9k_common,ath9k,mac80211
drm_kms_helper         61574  2 i915,nouveau
drm                   311018  11 ttm,i915,drm_kms_helper,nouveau
snd_timer              29562  2 snd_pcm,snd_seq
snd                    79468  17 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec_generic,snd_hda_codec,snd_hda_intel,snd_seq_device
crc32_pclmul           13133  0 
ghash_clmulni_intel    13230  0 
i2c_algo_bit           13413  2 i915,nouveau
joydev                 17393  0 
cryptd                 20359  1 ghash_clmulni_intel
mei_me                 19696  0 
serio_raw              13483  0 
soundcore              15047  2 snd,snd_hda_codec
mei                    87875  1 mei_me
lpc_ich                21093  0 
shpchp                 37047  0 
video                  20128  2 i915,nouveau
wmi                    19193  2 mxm_wmi,nouveau
mac_hid                13227  0 
parport_pc             32741  0 
ppdev                  17671  0 
lp                     17759  0 
parport                42348  3 lp,ppdev,parport_pc
hid_logitech_dj        18469  0 
usbhid                 52616  0 
hid                   110426  4 usbhid,hid_logitech_dj
psmouse               106561  0 
ahci                   34062  5 
libahci                32424  1 ahci
r8169                  71694  0 
mii                    13934  1 r8169
             total       used       free     shared    buffers     cached
Mem:       8059604    7123624     935980     830736     134760    1566224
-/+ buffers/cache:    5422640    2636964
Swap:     15625212     624352   15000860
/usr/lib/pm-utils/sleep.d/00logging suspend suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/00powersave suspend suspend:
/usr/lib/pm-utils/sleep.d/00powersave suspend suspend: success.


Running hook /etc/pm/sleep.d/10_grub-common suspend suspend:
/etc/pm/sleep.d/10_grub-common suspend suspend: success.


Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend:
/etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/50unload_alx suspend suspend:
/usr/lib/pm-utils/sleep.d/50unload_alx suspend suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend:
Failed to connect to non-global ctrl_ifname: (null)  error: No such file or directory
/usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/75modules suspend suspend:
Unloading kernel module r8169...Done.
/usr/lib/pm-utils/sleep.d/75modules suspend suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/90clock suspend suspend:
/usr/lib/pm-utils/sleep.d/90clock suspend suspend: not applicable.


Running hook /usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend:
/usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/95anacron suspend suspend:
/usr/lib/pm-utils/sleep.d/95anacron suspend suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend:
/usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend: not applicable.


Running hook /usr/lib/pm-utils/sleep.d/95led suspend suspend:
/usr/lib/pm-utils/sleep.d/95led suspend suspend: not applicable.


Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend:
Kernel modesetting video driver detected, not using quirks.
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/99video suspend suspend:
kernel.acpi_video_flags = 0
/usr/lib/pm-utils/sleep.d/99video suspend suspend: success.


Running hook /etc/pm/sleep.d/novatel_3g_suspend suspend suspend:
/etc/pm/sleep.d/novatel_3g_suspend suspend suspend: success.


Fri Apr  3 01:31:20 EEST 2015: performing suspend
Fri Apr  3 13:06:59 EEST 2015: Awake.
Fri Apr  3 13:06:59 EEST 2015: Running hooks for resume
Running hook /etc/pm/sleep.d/novatel_3g_suspend resume suspend:
/etc/pm/sleep.d/novatel_3g_suspend resume suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/99video resume suspend:
/usr/lib/pm-utils/sleep.d/99video resume suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend:
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/95led resume suspend:
/usr/lib/pm-utils/sleep.d/95led resume suspend: not applicable.


Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm resume suspend:


/dev/sda:
 setting Advanced Power Management level to 0xfe (254)
 APM_level    = 254
/usr/lib/pm-utils/sleep.d/95hdparm-apm resume suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/95anacron resume suspend:
/usr/lib/pm-utils/sleep.d/95anacron resume suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/94cpufreq resume suspend:
/usr/lib/pm-utils/sleep.d/94cpufreq resume suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/90clock resume suspend:
/usr/lib/pm-utils/sleep.d/90clock resume suspend: not applicable.


Running hook /usr/lib/pm-utils/sleep.d/75modules resume suspend:
Reloaded unloaded modules.
/usr/lib/pm-utils/sleep.d/75modules resume suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant resume suspend:
Failed to connect to non-global ctrl_ifname: (null)  error: No such file or directory
/usr/lib/pm-utils/sleep.d/60_wpa_supplicant resume suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/50unload_alx resume suspend:
/usr/lib/pm-utils/sleep.d/50unload_alx resume suspend: success.


Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate resume suspend:
/etc/pm/sleep.d/10_unattended-upgrades-hibernate resume suspend: success.


Running hook /etc/pm/sleep.d/10_grub-common resume suspend:
/etc/pm/sleep.d/10_grub-common resume suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/00powersave resume suspend:
/usr/lib/pm-utils/sleep.d/00powersave resume suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/00logging resume suspend:
/usr/lib/pm-utils/sleep.d/00logging resume suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/000record-status resume suspend:
/usr/lib/pm-utils/sleep.d/000record-status resume suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/000kernel-change resume suspend:
/usr/lib/pm-utils/sleep.d/000kernel-change resume suspend: success.


Fri Apr  3 13:07:01 EEST 2015: Finished.
Initial commandline parameters: 
Fri Apr  3 14:59:09 EEST 2015: Running hooks for suspend.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:
/usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/000record-status suspend suspend:
/usr/lib/pm-utils/sleep.d/000record-status suspend suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/00logging suspend suspend:
Linux laptop 3.16.0-33-generic #44~14.04.1-Ubuntu SMP Fri Mar 13 10:33:29 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux
Module                  Size  Used by
bnep                   19624  2 
rfcomm                 69509  8 
nls_iso8859_1          12713  1 
uvcvideo               81073  0 
videobuf2_vmalloc      13216  1 uvcvideo
videobuf2_memops       13362  1 videobuf2_vmalloc
videobuf2_core         59104  1 uvcvideo
v4l2_common            15681  1 videobuf2_core
videodev              153793  3 uvcvideo,v4l2_common,videobuf2_core
media                  21903  2 uvcvideo,videodev
snd_hda_codec_hdmi     47548  1 
snd_hda_codec_realtek    77467  1 
snd_hda_codec_generic    68937  1 snd_hda_codec_realtek
snd_hda_intel          30469  3 
snd_hda_controller     31056  1 snd_hda_intel
snd_hda_codec         139682  5 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_hda_intel,snd_hda_controller
snd_hwdep              17698  1 snd_hda_codec
snd_pcm               104112  4 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel,snd_hda_controller
snd_seq_midi           13564  0 
snd_seq_midi_event     14899  1 snd_seq_midi
intel_rapl             18783  0 
snd_rawmidi            30876  1 snd_seq_midi
x86_pkg_temp_thermal    14205  0 
intel_powerclamp       18823  0 
coretemp               13441  0 
kvm_intel             143590  0 
ath3k                  13331  0 
kvm                   452043  1 kvm_intel
crct10dif_pclmul       14307  0 
snd_seq                63074  2 snd_seq_midi_event,snd_seq_midi
arc4                   12608  2 
crc32_pclmul           13133  0 
ghash_clmulni_intel    13230  0 
cryptd                 20359  1 ghash_clmulni_intel
btusb                  32497  0 
ath9k                 137283  0 
bluetooth             446409  23 bnep,ath3k,btusb,rfcomm
joydev                 17393  0 
ath9k_common           25638  1 ath9k
ath9k_hw              446521  2 ath9k_common,ath9k
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
6lowpan_iphc           18702  1 bluetooth
ath                    29006  3 ath9k_common,ath9k,ath9k_hw
snd_timer              29562  2 snd_pcm,snd_seq
nouveau              1206535  1 
mac80211              652718  1 ath9k
serio_raw              13483  0 
snd                    79468  17 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec_generic,snd_hda_codec,snd_hda_intel,snd_seq_device
ttm                    93588  1 nouveau
cfg80211              494362  4 ath,ath9k_common,ath9k,mac80211
i915                  905954  5 
lpc_ich                21093  0 
drm_kms_helper         61574  2 i915,nouveau
drm                   311018  10 ttm,i915,drm_kms_helper,nouveau
mei_me                 19696  0 
soundcore              15047  2 snd,snd_hda_codec
mei                    87875  1 mei_me
i2c_algo_bit           13413  2 i915,nouveau
shpchp                 37047  0 
parport_pc             32741  0 
mxm_wmi                13021  1 nouveau
ppdev                  17671  0 
mac_hid                13227  0 
wmi                    19193  2 mxm_wmi,nouveau
lp                     17759  0 
parport                42348  3 lp,ppdev,parport_pc
video                  20128  2 i915,nouveau
hid_logitech_dj        18469  0 
usbhid                 52616  0 
hid                   110426  4 usbhid,hid_logitech_dj
psmouse               106561  0 
r8169                  71694  0 
ahci                   34062  4 
libahci                32424  1 ahci
mii                    13934  1 r8169
             total       used       free     shared    buffers     cached
Mem:       8059604    4319020    3740584     341992      99196    1467248
-/+ buffers/cache:    2752576    5307028
Swap:     15625212          0   15625212
/usr/lib/pm-utils/sleep.d/00logging suspend suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/00powersave suspend suspend:
/usr/lib/pm-utils/sleep.d/00powersave suspend suspend: success.


Running hook /etc/pm/sleep.d/10_grub-common suspend suspend:
/etc/pm/sleep.d/10_grub-common suspend suspend: success.


Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend:
/etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/50unload_alx suspend suspend:
/usr/lib/pm-utils/sleep.d/50unload_alx suspend suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend:
Failed to connect to non-global ctrl_ifname: (null)  error: No such file or directory
/usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/75modules suspend suspend:
Unloading kernel module r8169...Done.
/usr/lib/pm-utils/sleep.d/75modules suspend suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/90clock suspend suspend:
/usr/lib/pm-utils/sleep.d/90clock suspend suspend: not applicable.


Running hook /usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend:
/usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/95anacron suspend suspend:
stop: Unknown instance: 
/usr/lib/pm-utils/sleep.d/95anacron suspend suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend:
/usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend: not applicable.


Running hook /usr/lib/pm-utils/sleep.d/95led suspend suspend:
/usr/lib/pm-utils/sleep.d/95led suspend suspend: not applicable.


Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend:
Kernel modesetting video driver detected, not using quirks.
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/99video suspend suspend:
kernel.acpi_video_flags = 0
/usr/lib/pm-utils/sleep.d/99video suspend suspend: success.


Running hook /etc/pm/sleep.d/novatel_3g_suspend suspend suspend:
/etc/pm/sleep.d/novatel_3g_suspend suspend suspend: success.


Fri Apr  3 14:59:09 EEST 2015: performing suspend
Fri Apr  3 18:04:52 EEST 2015: Awake.
Fri Apr  3 18:04:52 EEST 2015: Running hooks for resume
Running hook /etc/pm/sleep.d/novatel_3g_suspend resume suspend:
/etc/pm/sleep.d/novatel_3g_suspend resume suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/99video resume suspend:
/usr/lib/pm-utils/sleep.d/99video resume suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend:
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/95led resume suspend:
/usr/lib/pm-utils/sleep.d/95led resume suspend: not applicable.


Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm resume suspend:


/dev/sda:
 setting Advanced Power Management level to 0xfe (254)
 APM_level    = 254
/usr/lib/pm-utils/sleep.d/95hdparm-apm resume suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/95anacron resume suspend:
/usr/lib/pm-utils/sleep.d/95anacron resume suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/94cpufreq resume suspend:
/usr/lib/pm-utils/sleep.d/94cpufreq resume suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/90clock resume suspend:
/usr/lib/pm-utils/sleep.d/90clock resume suspend: not applicable.


Running hook /usr/lib/pm-utils/sleep.d/75modules resume suspend:
Reloaded unloaded modules.
/usr/lib/pm-utils/sleep.d/75modules resume suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant resume suspend:
Failed to connect to non-global ctrl_ifname: (null)  error: No such file or directory
/usr/lib/pm-utils/sleep.d/60_wpa_supplicant resume suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/50unload_alx resume suspend:
/usr/lib/pm-utils/sleep.d/50unload_alx resume suspend: success.


Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate resume suspend:
/etc/pm/sleep.d/10_unattended-upgrades-hibernate resume suspend: success.


Running hook /etc/pm/sleep.d/10_grub-common resume suspend:
/etc/pm/sleep.d/10_grub-common resume suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/00powersave resume suspend:
/usr/lib/pm-utils/sleep.d/00powersave resume suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/00logging resume suspend:
/usr/lib/pm-utils/sleep.d/00logging resume suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/000record-status resume suspend:
/usr/lib/pm-utils/sleep.d/000record-status resume suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/000kernel-change resume suspend:
/usr/lib/pm-utils/sleep.d/000kernel-change resume suspend: success.


Fri Apr  3 18:04:52 EEST 2015: Finished.
Initial commandline parameters: 
Sat Apr  4 02:47:58 EEST 2015: Running hooks for suspend.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:
/usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/000record-status suspend suspend:
/usr/lib/pm-utils/sleep.d/000record-status suspend suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/00logging suspend suspend:
Linux laptop 3.16.0-33-generic #44~14.04.1-Ubuntu SMP Fri Mar 13 10:33:29 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux
Module                  Size  Used by
ctr                    13049  0 
ccm                    17773  0 
bnep                   19624  2 
rfcomm                 69509  8 
nls_iso8859_1          12713  1 
snd_hda_codec_hdmi     47548  1 
snd_hda_codec_realtek    77467  1 
snd_hda_codec_generic    68937  1 snd_hda_codec_realtek
uvcvideo               81073  0 
videobuf2_vmalloc      13216  1 uvcvideo
videobuf2_memops       13362  1 videobuf2_vmalloc
videobuf2_core         59104  1 uvcvideo
v4l2_common            15681  1 videobuf2_core
videodev              153793  3 uvcvideo,v4l2_common,videobuf2_core
media                  21903  2 uvcvideo,videodev
snd_hda_intel          30469  3 
snd_hda_controller     31056  1 snd_hda_intel
snd_hda_codec         139682  5 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_hda_intel,snd_hda_controller
snd_hwdep              17698  1 snd_hda_codec
snd_pcm               104112  4 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel,snd_hda_controller
snd_seq_midi           13564  0 
snd_seq_midi_event     14899  1 snd_seq_midi
snd_rawmidi            30876  1 snd_seq_midi
snd_seq                63074  2 snd_seq_midi_event,snd_seq_midi
intel_rapl             18783  0 
x86_pkg_temp_thermal    14205  0 
intel_powerclamp       18823  0 
coretemp               13441  0 
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
arc4                   12608  2 
kvm_intel             143590  0 
kvm                   452043  1 kvm_intel
crct10dif_pclmul       14307  0 
snd_timer              29562  2 snd_pcm,snd_seq
crc32_pclmul           13133  0 
ath9k                 137283  0 
ghash_clmulni_intel    13230  0 
ath9k_common           25638  1 ath9k
cryptd                 20359  1 ghash_clmulni_intel
ath9k_hw              446521  2 ath9k_common,ath9k
snd                    79468  17 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec_generic,snd_hda_codec,snd_hda_intel,snd_seq_device
ath                    29006  3 ath9k_common,ath9k,ath9k_hw
ath3k                  13331  0 
nouveau              1206535  1 
mac80211              652718  1 ath9k
i915                  905954  6 
joydev                 17393  0 
ttm                    93588  1 nouveau
serio_raw              13483  0 
cfg80211              494362  4 ath,ath9k_common,ath9k,mac80211
lpc_ich                21093  0 
btusb                  32497  0 
bluetooth             446409  23 bnep,ath3k,btusb,rfcomm
drm_kms_helper         61574  2 i915,nouveau
6lowpan_iphc           18702  1 bluetooth
shpchp                 37047  0 
mei_me                 19696  0 
drm                   311018  11 ttm,i915,drm_kms_helper,nouveau
soundcore              15047  2 snd,snd_hda_codec
mei                    87875  1 mei_me
i2c_algo_bit           13413  2 i915,nouveau
parport_pc             32741  0 
ppdev                  17671  0 
lp                     17759  0 
parport                42348  3 lp,ppdev,parport_pc
mxm_wmi                13021  1 nouveau
wmi                    19193  2 mxm_wmi,nouveau
video                  20128  2 i915,nouveau
mac_hid                13227  0 
hid_logitech_dj        18469  0 
usbhid                 52616  0 
hid                   110426  4 usbhid,hid_logitech_dj
ahci                   34062  4 
psmouse               106561  0 
r8169                  71694  0 
libahci                32424  1 ahci
mii                    13934  1 r8169
             total       used       free     shared    buffers     cached
Mem:       8059604    5208016    2851588     717640     138384    1874832
-/+ buffers/cache:    3194800    4864804
Swap:     15625212        300   15624912
/usr/lib/pm-utils/sleep.d/00logging suspend suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/00powersave suspend suspend:
/usr/lib/pm-utils/sleep.d/00powersave suspend suspend: success.


Running hook /etc/pm/sleep.d/10_grub-common suspend suspend:
/etc/pm/sleep.d/10_grub-common suspend suspend: success.


Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend:
/etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/50unload_alx suspend suspend:
/usr/lib/pm-utils/sleep.d/50unload_alx suspend suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend:
Failed to connect to non-global ctrl_ifname: (null)  error: No such file or directory
/usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/75modules suspend suspend:
Unloading kernel module r8169...Done.
/usr/lib/pm-utils/sleep.d/75modules suspend suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/90clock suspend suspend:
/usr/lib/pm-utils/sleep.d/90clock suspend suspend: not applicable.


Running hook /usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend:
/usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/95anacron suspend suspend:
/usr/lib/pm-utils/sleep.d/95anacron suspend suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend:
/usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend: not applicable.


Running hook /usr/lib/pm-utils/sleep.d/95led suspend suspend:
/usr/lib/pm-utils/sleep.d/95led suspend suspend: not applicable.


Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend:
Kernel modesetting video driver detected, not using quirks.
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/99video suspend suspend:
kernel.acpi_video_flags = 0
/usr/lib/pm-utils/sleep.d/99video suspend suspend: success.


Running hook /etc/pm/sleep.d/novatel_3g_suspend suspend suspend:
/etc/pm/sleep.d/novatel_3g_suspend suspend suspend: success.


Sat Apr  4 02:48:01 EEST 2015: performing suspend
Sat Apr  4 11:18:01 EEST 2015: Awake.
Sat Apr  4 11:18:01 EEST 2015: Running hooks for resume
Running hook /etc/pm/sleep.d/novatel_3g_suspend resume suspend:
/etc/pm/sleep.d/novatel_3g_suspend resume suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/99video resume suspend:
/usr/lib/pm-utils/sleep.d/99video resume suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend:
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/95led resume suspend:
/usr/lib/pm-utils/sleep.d/95led resume suspend: not applicable.


Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm resume suspend:


/dev/sda:
 setting Advanced Power Management level to 0xfe (254)
 APM_level    = 254
/usr/lib/pm-utils/sleep.d/95hdparm-apm resume suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/95anacron resume suspend:
/usr/lib/pm-utils/sleep.d/95anacron resume suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/94cpufreq resume suspend:
/usr/lib/pm-utils/sleep.d/94cpufreq resume suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/90clock resume suspend:
/usr/lib/pm-utils/sleep.d/90clock resume suspend: not applicable.


Running hook /usr/lib/pm-utils/sleep.d/75modules resume suspend:
Reloaded unloaded modules.
/usr/lib/pm-utils/sleep.d/75modules resume suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant resume suspend:
Failed to connect to non-global ctrl_ifname: (null)  error: No such file or directory
/usr/lib/pm-utils/sleep.d/60_wpa_supplicant resume suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/50unload_alx resume suspend:
/usr/lib/pm-utils/sleep.d/50unload_alx resume suspend: success.


Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate resume suspend:
/etc/pm/sleep.d/10_unattended-upgrades-hibernate resume suspend: success.


Running hook /etc/pm/sleep.d/10_grub-common resume suspend:
/etc/pm/sleep.d/10_grub-common resume suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/00powersave resume suspend:
/usr/lib/pm-utils/sleep.d/00powersave resume suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/00logging resume suspend:
/usr/lib/pm-utils/sleep.d/00logging resume suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/000record-status resume suspend:
/usr/lib/pm-utils/sleep.d/000record-status resume suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/000kernel-change resume suspend:
/usr/lib/pm-utils/sleep.d/000kernel-change resume suspend: success.


Sat Apr  4 11:18:01 EEST 2015: Finished.
Initial commandline parameters: 
Sat Apr  4 17:35:03 EEST 2015: Running hooks for suspend.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:
/usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/000record-status suspend suspend:
/usr/lib/pm-utils/sleep.d/000record-status suspend suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/00logging suspend suspend:
Linux laptop 3.16.0-33-generic #44~14.04.1-Ubuntu SMP Fri Mar 13 10:33:29 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux
Module                  Size  Used by
bnep                   19624  2 
rfcomm                 69509  8 
nls_iso8859_1          12713  1 
snd_hda_codec_hdmi     47548  1 
snd_hda_codec_realtek    77467  1 
snd_hda_codec_generic    68937  1 snd_hda_codec_realtek
uvcvideo               81073  0 
videobuf2_vmalloc      13216  1 uvcvideo
videobuf2_memops       13362  1 videobuf2_vmalloc
videobuf2_core         59104  1 uvcvideo
v4l2_common            15681  1 videobuf2_core
videodev              153793  3 uvcvideo,v4l2_common,videobuf2_core
media                  21903  2 uvcvideo,videodev
snd_hda_intel          30469  3 
snd_hda_controller     31056  1 snd_hda_intel
snd_hda_codec         139682  5 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_hda_intel,snd_hda_controller
snd_hwdep              17698  1 snd_hda_codec
snd_pcm               104112  4 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel,snd_hda_controller
snd_seq_midi           13564  0 
snd_seq_midi_event     14899  1 snd_seq_midi
intel_rapl             18783  0 
x86_pkg_temp_thermal    14205  0 
intel_powerclamp       18823  0 
coretemp               13441  0 
kvm_intel             143590  0 
snd_rawmidi            30876  1 snd_seq_midi
kvm                   452043  1 kvm_intel
snd_seq                63074  2 snd_seq_midi_event,snd_seq_midi
crct10dif_pclmul       14307  0 
crc32_pclmul           13133  0 
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
arc4                   12608  2 
snd_timer              29562  2 snd_pcm,snd_seq
ghash_clmulni_intel    13230  0 
cryptd                 20359  1 ghash_clmulni_intel
ath9k                 137283  0 
joydev                 17393  0 
serio_raw              13483  0 
ath9k_common           25638  1 ath9k
ath9k_hw              446521  2 ath9k_common,ath9k
ath                    29006  3 ath9k_common,ath9k,ath9k_hw
mac80211              652718  1 ath9k
lpc_ich                21093  0 
cfg80211              494362  4 ath,ath9k_common,ath9k,mac80211
ath3k                  13331  0 
btusb                  32497  0 
snd                    79468  17 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec_generic,snd_hda_codec,snd_hda_intel,snd_seq_device
i915                  905954  6 
bluetooth             446409  23 bnep,ath3k,btusb,rfcomm
mei_me                 19696  0 
nouveau              1206535  1 
soundcore              15047  2 snd,snd_hda_codec
ttm                    93588  1 nouveau
drm_kms_helper         61574  2 i915,nouveau
mei                    87875  1 mei_me
6lowpan_iphc           18702  1 bluetooth
drm                   311018  11 ttm,i915,drm_kms_helper,nouveau
i2c_algo_bit           13413  2 i915,nouveau
shpchp                 37047  0 
mxm_wmi                13021  1 nouveau
wmi                    19193  2 mxm_wmi,nouveau
video                  20128  2 i915,nouveau
mac_hid                13227  0 
parport_pc             32741  0 
ppdev                  17671  0 
lp                     17759  0 
parport                42348  3 lp,ppdev,parport_pc
hid_logitech_dj        18469  0 
usbhid                 52616  0 
hid                   110426  4 usbhid,hid_logitech_dj
psmouse               106561  0 
r8169                  71694  0 
ahci                   34062  4 
libahci                32424  1 ahci
mii                    13934  1 r8169
             total       used       free     shared    buffers     cached
Mem:       8059604    5487948    2571656     434160     284464    1972252
-/+ buffers/cache:    3231232    4828372
Swap:     15625212          0   15625212
/usr/lib/pm-utils/sleep.d/00logging suspend suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/00powersave suspend suspend:
/usr/lib/pm-utils/sleep.d/00powersave suspend suspend: success.


Running hook /etc/pm/sleep.d/10_grub-common suspend suspend:
/etc/pm/sleep.d/10_grub-common suspend suspend: success.


Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend:
/etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/50unload_alx suspend suspend:
/usr/lib/pm-utils/sleep.d/50unload_alx suspend suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend:
Failed to connect to non-global ctrl_ifname: (null)  error: No such file or directory
/usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/75modules suspend suspend:
Unloading kernel module r8169...Done.
/usr/lib/pm-utils/sleep.d/75modules suspend suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/90clock suspend suspend:
/usr/lib/pm-utils/sleep.d/90clock suspend suspend: not applicable.


Running hook /usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend:
/usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/95anacron suspend suspend:
stop: Unknown instance: 
/usr/lib/pm-utils/sleep.d/95anacron suspend suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend:
/usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend: not applicable.


Running hook /usr/lib/pm-utils/sleep.d/95led suspend suspend:
/usr/lib/pm-utils/sleep.d/95led suspend suspend: not applicable.


Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend:
Kernel modesetting video driver detected, not using quirks.
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/99video suspend suspend:
kernel.acpi_video_flags = 0
/usr/lib/pm-utils/sleep.d/99video suspend suspend: success.


Running hook /etc/pm/sleep.d/novatel_3g_suspend suspend suspend:
/etc/pm/sleep.d/novatel_3g_suspend suspend suspend: success.


Sat Apr  4 17:35:04 EEST 2015: performing suspend
Sat Apr  4 19:55:15 EEST 2015: Awake.
Sat Apr  4 19:55:15 EEST 2015: Running hooks for resume
Running hook /etc/pm/sleep.d/novatel_3g_suspend resume suspend:
/etc/pm/sleep.d/novatel_3g_suspend resume suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/99video resume suspend:
/usr/lib/pm-utils/sleep.d/99video resume suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend:
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/95led resume suspend:
/usr/lib/pm-utils/sleep.d/95led resume suspend: not applicable.


Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm resume suspend:


/dev/sda:
 setting Advanced Power Management level to 0x80 (128)
 APM_level    = 128


/dev/sda:
 setting standby to 36 (3 minutes)
/usr/lib/pm-utils/sleep.d/95hdparm-apm resume suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/95anacron resume suspend:
/usr/lib/pm-utils/sleep.d/95anacron resume suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/94cpufreq resume suspend:
/usr/lib/pm-utils/sleep.d/94cpufreq resume suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/90clock resume suspend:
/usr/lib/pm-utils/sleep.d/90clock resume suspend: not applicable.


Running hook /usr/lib/pm-utils/sleep.d/75modules resume suspend:
Reloaded unloaded modules.
/usr/lib/pm-utils/sleep.d/75modules resume suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant resume suspend:
Failed to connect to non-global ctrl_ifname: (null)  error: No such file or directory
/usr/lib/pm-utils/sleep.d/60_wpa_supplicant resume suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/50unload_alx resume suspend:
/usr/lib/pm-utils/sleep.d/50unload_alx resume suspend: success.


Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate resume suspend:
/etc/pm/sleep.d/10_unattended-upgrades-hibernate resume suspend: success.


Running hook /etc/pm/sleep.d/10_grub-common resume suspend:
/etc/pm/sleep.d/10_grub-common resume suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/00powersave resume suspend:
/usr/lib/pm-utils/sleep.d/00powersave resume suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/00logging resume suspend:
/usr/lib/pm-utils/sleep.d/00logging resume suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/000record-status resume suspend:
/usr/lib/pm-utils/sleep.d/000record-status resume suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/000kernel-change resume suspend:
/usr/lib/pm-utils/sleep.d/000kernel-change resume suspend: success.


Sat Apr  4 19:55:16 EEST 2015: Finished.
Initial commandline parameters: 
Sat Apr  4 21:30:08 EEST 2015: Running hooks for suspend.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:
/usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/000record-status suspend suspend:
/usr/lib/pm-utils/sleep.d/000record-status suspend suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/00logging suspend suspend:
Linux laptop 3.16.0-33-generic #44~14.04.1-Ubuntu SMP Fri Mar 13 10:33:29 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux
Module                  Size  Used by
ctr                    13049  0 
ccm                    17773  0 
bnep                   19624  2 
rfcomm                 69509  8 
nls_iso8859_1          12713  1 
uvcvideo               81073  0 
videobuf2_vmalloc      13216  1 uvcvideo
videobuf2_memops       13362  1 videobuf2_vmalloc
videobuf2_core         59104  1 uvcvideo
v4l2_common            15681  1 videobuf2_core
videodev              153793  3 uvcvideo,v4l2_common,videobuf2_core
media                  21903  2 uvcvideo,videodev
snd_hda_codec_hdmi     47548  1 
snd_hda_codec_realtek    77467  1 
snd_hda_codec_generic    68937  1 snd_hda_codec_realtek
snd_hda_intel          30469  3 
snd_hda_controller     31056  1 snd_hda_intel
snd_hda_codec         139682  5 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_hda_intel,snd_hda_controller
snd_hwdep              17698  1 snd_hda_codec
snd_pcm               104112  4 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel,snd_hda_controller
intel_rapl             18783  0 
x86_pkg_temp_thermal    14205  0 
intel_powerclamp       18823  0 
coretemp               13441  0 
kvm_intel             143590  0 
snd_seq_midi           13564  0 
kvm                   452043  1 kvm_intel
snd_seq_midi_event     14899  1 snd_seq_midi
snd_rawmidi            30876  1 snd_seq_midi
crct10dif_pclmul       14307  0 
crc32_pclmul           13133  0 
snd_seq                63074  2 snd_seq_midi_event,snd_seq_midi
ghash_clmulni_intel    13230  0 
cryptd                 20359  1 ghash_clmulni_intel
ath3k                  13331  0 
arc4                   12608  2 
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              29562  2 snd_pcm,snd_seq
joydev                 17393  0 
ath9k                 137283  0 
serio_raw              13483  0 
btusb                  32497  0 
ath9k_common           25638  1 ath9k
bluetooth             446409  23 bnep,ath3k,btusb,rfcomm
ath9k_hw              446521  2 ath9k_common,ath9k
ath                    29006  3 ath9k_common,ath9k,ath9k_hw
6lowpan_iphc           18702  1 bluetooth
mac80211              652718  1 ath9k
snd                    79468  17 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec_generic,snd_hda_codec,snd_hda_intel,snd_seq_device
nouveau              1206535  1 
cfg80211              494362  4 ath,ath9k_common,ath9k,mac80211
i915                  905954  4 
ttm                    93588  1 nouveau
drm_kms_helper         61574  2 i915,nouveau
lpc_ich                21093  0 
soundcore              15047  2 snd,snd_hda_codec
drm                   311018  9 ttm,i915,drm_kms_helper,nouveau
mei_me                 19696  0 
mei                    87875  1 mei_me
i2c_algo_bit           13413  2 i915,nouveau
shpchp                 37047  0 
mxm_wmi                13021  1 nouveau
video                  20128  2 i915,nouveau
wmi                    19193  2 mxm_wmi,nouveau
mac_hid                13227  0 
parport_pc             32741  0 
ppdev                  17671  0 
lp                     17759  0 
parport                42348  3 lp,ppdev,parport_pc
hid_logitech_dj        18469  0 
usbhid                 52616  0 
hid                   110426  4 usbhid,hid_logitech_dj
psmouse               106561  0 
r8169                  71694  0 
ahci                   34062  4 
libahci                32424  1 ahci
mii                    13934  1 r8169
             total       used       free     shared    buffers     cached
Mem:       8059604    3017544    5042060     253936      90748     973840
-/+ buffers/cache:    1952956    6106648
Swap:     15625212          0   15625212
/usr/lib/pm-utils/sleep.d/00logging suspend suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/00powersave suspend suspend:
/usr/lib/pm-utils/sleep.d/00powersave suspend suspend: success.


Running hook /etc/pm/sleep.d/10_grub-common suspend suspend:
/etc/pm/sleep.d/10_grub-common suspend suspend: success.


Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend:
/etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/50unload_alx suspend suspend:
/usr/lib/pm-utils/sleep.d/50unload_alx suspend suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend:
Failed to connect to non-global ctrl_ifname: (null)  error: No such file or directory
/usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/75modules suspend suspend:
Unloading kernel module r8169...Done.
/usr/lib/pm-utils/sleep.d/75modules suspend suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/90clock suspend suspend:
/usr/lib/pm-utils/sleep.d/90clock suspend suspend: not applicable.


Running hook /usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend:
/usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/95anacron suspend suspend:
stop: Unknown instance: 
/usr/lib/pm-utils/sleep.d/95anacron suspend suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend:
/usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend: not applicable.


Running hook /usr/lib/pm-utils/sleep.d/95led suspend suspend:
/usr/lib/pm-utils/sleep.d/95led suspend suspend: not applicable.


Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend:
Kernel modesetting video driver detected, not using quirks.
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/99video suspend suspend:
kernel.acpi_video_flags = 0
/usr/lib/pm-utils/sleep.d/99video suspend suspend: success.


Running hook /etc/pm/sleep.d/novatel_3g_suspend suspend suspend:
/etc/pm/sleep.d/novatel_3g_suspend suspend suspend: success.


Sat Apr  4 21:30:09 EEST 2015: performing suspend
Sun Apr  5 17:41:52 EEST 2015: Awake.
Sun Apr  5 17:41:52 EEST 2015: Running hooks for resume
Running hook /etc/pm/sleep.d/novatel_3g_suspend resume suspend:
/etc/pm/sleep.d/novatel_3g_suspend resume suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/99video resume suspend:
/usr/lib/pm-utils/sleep.d/99video resume suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend:
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/95led resume suspend:
/usr/lib/pm-utils/sleep.d/95led resume suspend: not applicable.


Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm resume suspend:


/dev/sda:
 setting Advanced Power Management level to 0xfe (254)
 APM_level    = 254
/usr/lib/pm-utils/sleep.d/95hdparm-apm resume suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/95anacron resume suspend:
/usr/lib/pm-utils/sleep.d/95anacron resume suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/94cpufreq resume suspend:
/usr/lib/pm-utils/sleep.d/94cpufreq resume suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/90clock resume suspend:
/usr/lib/pm-utils/sleep.d/90clock resume suspend: not applicable.


Running hook /usr/lib/pm-utils/sleep.d/75modules resume suspend:
Reloaded unloaded modules.
/usr/lib/pm-utils/sleep.d/75modules resume suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant resume suspend:
Failed to connect to non-global ctrl_ifname: (null)  error: No such file or directory
/usr/lib/pm-utils/sleep.d/60_wpa_supplicant resume suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/50unload_alx resume suspend:
/usr/lib/pm-utils/sleep.d/50unload_alx resume suspend: success.


Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate resume suspend:
/etc/pm/sleep.d/10_unattended-upgrades-hibernate resume suspend: success.


Running hook /etc/pm/sleep.d/10_grub-common resume suspend:
/etc/pm/sleep.d/10_grub-common resume suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/00powersave resume suspend:
/usr/lib/pm-utils/sleep.d/00powersave resume suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/00logging resume suspend:
/usr/lib/pm-utils/sleep.d/00logging resume suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/000record-status resume suspend:
/usr/lib/pm-utils/sleep.d/000record-status resume suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/000kernel-change resume suspend:
/usr/lib/pm-utils/sleep.d/000kernel-change resume suspend: success.


Sun Apr  5 17:41:53 EEST 2015: Finished.
Initial commandline parameters: 
Sun Apr  5 18:56:49 EEST 2015: Running hooks for suspend.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:
/usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/000record-status suspend suspend:
/usr/lib/pm-utils/sleep.d/000record-status suspend suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/00logging suspend suspend:
Linux laptop 3.16.0-33-generic #44~14.04.1-Ubuntu SMP Fri Mar 13 10:33:29 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux
Module                  Size  Used by
ctr                    13049  0 
ccm                    17773  0 
rfcomm                 69509  8 
bnep                   19624  2 
nls_iso8859_1          12713  1 
uvcvideo               81073  0 
videobuf2_vmalloc      13216  1 uvcvideo
videobuf2_memops       13362  1 videobuf2_vmalloc
videobuf2_core         59104  1 uvcvideo
v4l2_common            15681  1 videobuf2_core
videodev              153793  3 uvcvideo,v4l2_common,videobuf2_core
media                  21903  2 uvcvideo,videodev
snd_hda_codec_hdmi     47548  1 
snd_hda_codec_realtek    77467  1 
snd_hda_codec_generic    68937  1 snd_hda_codec_realtek
snd_hda_intel          30469  3 
snd_hda_controller     31056  1 snd_hda_intel
snd_hda_codec         139682  5 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_hda_intel,snd_hda_controller
snd_hwdep              17698  1 snd_hda_codec
intel_rapl             18783  0 
x86_pkg_temp_thermal    14205  0 
intel_powerclamp       18823  0 
coretemp               13441  0 
snd_pcm               104112  4 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel,snd_hda_controller
kvm_intel             143590  0 
kvm                   452043  1 kvm_intel
snd_seq_midi           13564  0 
arc4                   12608  2 
crct10dif_pclmul       14307  0 
snd_seq_midi_event     14899  1 snd_seq_midi
crc32_pclmul           13133  0 
snd_rawmidi            30876  1 snd_seq_midi
ghash_clmulni_intel    13230  0 
ath9k                 137283  0 
cryptd                 20359  1 ghash_clmulni_intel
ath9k_common           25638  1 ath9k
ath9k_hw              446521  2 ath9k_common,ath9k
ath                    29006  3 ath9k_common,ath9k,ath9k_hw
joydev                 17393  0 
mac80211              652718  1 ath9k
snd_seq                63074  2 snd_seq_midi_event,snd_seq_midi
ath3k                  13331  0 
nouveau              1206535  1 
serio_raw              13483  0 
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              29562  2 snd_pcm,snd_seq
snd                    79468  17 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec_generic,snd_hda_codec,snd_hda_intel,snd_seq_device
btusb                  32497  0 
bluetooth             446409  23 bnep,ath3k,btusb,rfcomm
ttm                    93588  1 nouveau
i915                  905954  5 
cfg80211              494362  4 ath,ath9k_common,ath9k,mac80211
6lowpan_iphc           18702  1 bluetooth
lpc_ich                21093  0 
soundcore              15047  2 snd,snd_hda_codec
mei_me                 19696  0 
drm_kms_helper         61574  2 i915,nouveau
mei                    87875  1 mei_me
drm                   311018  10 ttm,i915,drm_kms_helper,nouveau
shpchp                 37047  0 
i2c_algo_bit           13413  2 i915,nouveau
mxm_wmi                13021  1 nouveau
parport_pc             32741  0 
wmi                    19193  2 mxm_wmi,nouveau
video                  20128  2 i915,nouveau
ppdev                  17671  0 
mac_hid                13227  0 
lp                     17759  0 
parport                42348  3 lp,ppdev,parport_pc
hid_logitech_dj        18469  0 
usbhid                 52616  0 
hid                   110426  4 usbhid,hid_logitech_dj
psmouse               106561  0 
ahci                   34062  4 
r8169                  71694  0 
libahci                32424  1 ahci
mii                    13934  1 r8169
             total       used       free     shared    buffers     cached
Mem:       8059604    5652932    2406672     594500     235108    2332756
-/+ buffers/cache:    3085068    4974536
Swap:     15625212          0   15625212
/usr/lib/pm-utils/sleep.d/00logging suspend suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/00powersave suspend suspend:
/usr/lib/pm-utils/sleep.d/00powersave suspend suspend: success.


Running hook /etc/pm/sleep.d/10_grub-common suspend suspend:
/etc/pm/sleep.d/10_grub-common suspend suspend: success.


Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend:
/etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/50unload_alx suspend suspend:
/usr/lib/pm-utils/sleep.d/50unload_alx suspend suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend:
Failed to connect to non-global ctrl_ifname: (null)  error: No such file or directory
/usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/75modules suspend suspend:
Unloading kernel module r8169...Done.
/usr/lib/pm-utils/sleep.d/75modules suspend suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/90clock suspend suspend:
/usr/lib/pm-utils/sleep.d/90clock suspend suspend: not applicable.


Running hook /usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend:
/usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/95anacron suspend suspend:
stop: Unknown instance: 
/usr/lib/pm-utils/sleep.d/95anacron suspend suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend:
/usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend: not applicable.


Running hook /usr/lib/pm-utils/sleep.d/95led suspend suspend:
/usr/lib/pm-utils/sleep.d/95led suspend suspend: not applicable.


Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend:
Kernel modesetting video driver detected, not using quirks.
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/99video suspend suspend:
kernel.acpi_video_flags = 0
/usr/lib/pm-utils/sleep.d/99video suspend suspend: success.


Running hook /etc/pm/sleep.d/novatel_3g_suspend suspend suspend:
/etc/pm/sleep.d/novatel_3g_suspend suspend suspend: success.


Sun Apr  5 18:56:49 EEST 2015: performing suspend
Mon Apr  6 02:16:46 EEST 2015: Awake.
Mon Apr  6 02:16:46 EEST 2015: Running hooks for resume
Running hook /etc/pm/sleep.d/novatel_3g_suspend resume suspend:
/etc/pm/sleep.d/novatel_3g_suspend resume suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/99video resume suspend:
/usr/lib/pm-utils/sleep.d/99video resume suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend:
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/95led resume suspend:
/usr/lib/pm-utils/sleep.d/95led resume suspend: not applicable.


Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm resume suspend:


/dev/sda:
 setting Advanced Power Management level to 0xfe (254)
 APM_level    = 254
/usr/lib/pm-utils/sleep.d/95hdparm-apm resume suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/95anacron resume suspend:
/usr/lib/pm-utils/sleep.d/95anacron resume suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/94cpufreq resume suspend:
/usr/lib/pm-utils/sleep.d/94cpufreq resume suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/90clock resume suspend:
/usr/lib/pm-utils/sleep.d/90clock resume suspend: not applicable.


Running hook /usr/lib/pm-utils/sleep.d/75modules resume suspend:
Reloaded unloaded modules.
/usr/lib/pm-utils/sleep.d/75modules resume suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant resume suspend:
Failed to connect to non-global ctrl_ifname: (null)  error: No such file or directory
/usr/lib/pm-utils/sleep.d/60_wpa_supplicant resume suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/50unload_alx resume suspend:
/usr/lib/pm-utils/sleep.d/50unload_alx resume suspend: success.


Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate resume suspend:
/etc/pm/sleep.d/10_unattended-upgrades-hibernate resume suspend: success.


Running hook /etc/pm/sleep.d/10_grub-common resume suspend:
/etc/pm/sleep.d/10_grub-common resume suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/00powersave resume suspend:
/usr/lib/pm-utils/sleep.d/00powersave resume suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/00logging resume suspend:
/usr/lib/pm-utils/sleep.d/00logging resume suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/000record-status resume suspend:
/usr/lib/pm-utils/sleep.d/000record-status resume suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/000kernel-change resume suspend:
/usr/lib/pm-utils/sleep.d/000kernel-change resume suspend: success.


Mon Apr  6 02:16:46 EEST 2015: Finished.
Initial commandline parameters: 
Wed Apr  8 02:00:20 EEST 2015: Running hooks for suspend.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:
/usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/000record-status suspend suspend:
/usr/lib/pm-utils/sleep.d/000record-status suspend suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/00logging suspend suspend:
Linux laptop 3.16.0-33-generic #44~14.04.1-Ubuntu SMP Fri Mar 13 10:33:29 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux
Module                  Size  Used by
ctr                    13049  0 
ccm                    17773  0 
bnep                   19624  2 
rfcomm                 69509  8 
nls_iso8859_1          12713  1 
uvcvideo               81073  0 
videobuf2_vmalloc      13216  1 uvcvideo
videobuf2_memops       13362  1 videobuf2_vmalloc
videobuf2_core         59104  1 uvcvideo
v4l2_common            15681  1 videobuf2_core
videodev              153793  3 uvcvideo,v4l2_common,videobuf2_core
media                  21903  2 uvcvideo,videodev
snd_hda_codec_hdmi     47548  1 
snd_hda_codec_realtek    77467  1 
snd_hda_codec_generic    68937  1 snd_hda_codec_realtek
intel_rapl             18783  0 
x86_pkg_temp_thermal    14205  0 
intel_powerclamp       18823  0 
coretemp               13441  0 
kvm_intel             143590  0 
kvm                   452043  1 kvm_intel
snd_hda_intel          30469  3 
snd_hda_controller     31056  1 snd_hda_intel
snd_hda_codec         139682  5 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_hda_intel,snd_hda_controller
crct10dif_pclmul       14307  0 
snd_hwdep              17698  1 snd_hda_codec
crc32_pclmul           13133  0 
snd_pcm               104112  4 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel,snd_hda_controller
ghash_clmulni_intel    13230  0 
cryptd                 20359  1 ghash_clmulni_intel
snd_seq_midi           13564  0 
snd_seq_midi_event     14899  1 snd_seq_midi
snd_rawmidi            30876  1 snd_seq_midi
arc4                   12608  2 
joydev                 17393  0 
serio_raw              13483  0 
ath9k                 137283  0 
ath9k_common           25638  1 ath9k
ath9k_hw              446521  2 ath9k_common,ath9k
snd_seq                63074  2 snd_seq_midi_event,snd_seq_midi
ath                    29006  3 ath9k_common,ath9k,ath9k_hw
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
mac80211              652718  1 ath9k
snd_timer              29562  2 snd_pcm,snd_seq
lpc_ich                21093  0 
nouveau              1206535  1 
i915                  905954  5 
cfg80211              494362  4 ath,ath9k_common,ath9k,mac80211
snd                    79468  17 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec_generic,snd_hda_codec,snd_hda_intel,snd_seq_device
ath3k                  13331  0 
btusb                  32497  0 
bluetooth             446409  23 bnep,ath3k,btusb,rfcomm
ttm                    93588  1 nouveau
drm_kms_helper         61574  2 i915,nouveau
6lowpan_iphc           18702  1 bluetooth
drm                   311018  10 ttm,i915,drm_kms_helper,nouveau
soundcore              15047  2 snd,snd_hda_codec
mei_me                 19696  0 
mei                    87875  1 mei_me
i2c_algo_bit           13413  2 i915,nouveau
shpchp                 37047  0 
mxm_wmi                13021  1 nouveau
parport_pc             32741  0 
ppdev                  17671  0 
video                  20128  2 i915,nouveau
wmi                    19193  2 mxm_wmi,nouveau
lp                     17759  0 
mac_hid                13227  0 
parport                42348  3 lp,ppdev,parport_pc
hid_logitech_dj        18469  0 
usbhid                 52616  0 
hid                   110426  4 usbhid,hid_logitech_dj
psmouse               106561  0 
ahci                   34062  4 
r8169                  71694  0 
libahci                32424  1 ahci
mii                    13934  1 r8169
             total       used       free     shared    buffers     cached
Mem:       8059604    6714188    1345416     503352     224120    4960808
-/+ buffers/cache:    1529260    6530344
Swap:     15625212     156600   15468612
/usr/lib/pm-utils/sleep.d/00logging suspend suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/00powersave suspend suspend:
/usr/lib/pm-utils/sleep.d/00powersave suspend suspend: success.


Running hook /etc/pm/sleep.d/10_grub-common suspend suspend:
/etc/pm/sleep.d/10_grub-common suspend suspend: success.


Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend:
/etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/50unload_alx suspend suspend:
/usr/lib/pm-utils/sleep.d/50unload_alx suspend suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend:
Failed to connect to non-global ctrl_ifname: (null)  error: No such file or directory
/usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/75modules suspend suspend:
Unloading kernel module r8169...Done.
/usr/lib/pm-utils/sleep.d/75modules suspend suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/90clock suspend suspend:
/usr/lib/pm-utils/sleep.d/90clock suspend suspend: not applicable.


Running hook /usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend:
/usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/95anacron suspend suspend:
/usr/lib/pm-utils/sleep.d/95anacron suspend suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend:
/usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend: not applicable.


Running hook /usr/lib/pm-utils/sleep.d/95led suspend suspend:
/usr/lib/pm-utils/sleep.d/95led suspend suspend: not applicable.


Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend:
Kernel modesetting video driver detected, not using quirks.
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/99video suspend suspend:
kernel.acpi_video_flags = 0
/usr/lib/pm-utils/sleep.d/99video suspend suspend: success.


Running hook /etc/pm/sleep.d/novatel_3g_suspend suspend suspend:
/etc/pm/sleep.d/novatel_3g_suspend suspend suspend: success.


Wed Apr  8 02:00:21 EEST 2015: performing suspend
Wed Apr  8 10:05:56 EEST 2015: Awake.
Wed Apr  8 10:05:56 EEST 2015: Running hooks for resume
Running hook /etc/pm/sleep.d/novatel_3g_suspend resume suspend:
/etc/pm/sleep.d/novatel_3g_suspend resume suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/99video resume suspend:
/usr/lib/pm-utils/sleep.d/99video resume suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend:
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/95led resume suspend:
/usr/lib/pm-utils/sleep.d/95led resume suspend: not applicable.


Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm resume suspend:


/dev/sda:
 setting Advanced Power Management level to 0xfe (254)
 APM_level    = 254
/usr/lib/pm-utils/sleep.d/95hdparm-apm resume suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/95anacron resume suspend:
/usr/lib/pm-utils/sleep.d/95anacron resume suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/94cpufreq resume suspend:
/usr/lib/pm-utils/sleep.d/94cpufreq resume suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/90clock resume suspend:
/usr/lib/pm-utils/sleep.d/90clock resume suspend: not applicable.


Running hook /usr/lib/pm-utils/sleep.d/75modules resume suspend:
Reloaded unloaded modules.
/usr/lib/pm-utils/sleep.d/75modules resume suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant resume suspend:
Failed to connect to non-global ctrl_ifname: (null)  error: No such file or directory
/usr/lib/pm-utils/sleep.d/60_wpa_supplicant resume suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/50unload_alx resume suspend:
/usr/lib/pm-utils/sleep.d/50unload_alx resume suspend: success.


Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate resume suspend:
/etc/pm/sleep.d/10_unattended-upgrades-hibernate resume suspend: success.


Running hook /etc/pm/sleep.d/10_grub-common resume suspend:
/etc/pm/sleep.d/10_grub-common resume suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/00powersave resume suspend:
/usr/lib/pm-utils/sleep.d/00powersave resume suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/00logging resume suspend:
/usr/lib/pm-utils/sleep.d/00logging resume suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/000record-status resume suspend:
/usr/lib/pm-utils/sleep.d/000record-status resume suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/000kernel-change resume suspend:
/usr/lib/pm-utils/sleep.d/000kernel-change resume suspend: success.


Wed Apr  8 10:05:57 EEST 2015: Finished.
Initial commandline parameters: 
Wed Apr  8 17:46:30 EEST 2015: Running hooks for suspend.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:
/usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/000record-status suspend suspend:
/usr/lib/pm-utils/sleep.d/000record-status suspend suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/00logging suspend suspend:
Linux laptop 3.16.0-33-generic #44~14.04.1-Ubuntu SMP Fri Mar 13 10:33:29 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux
Module                  Size  Used by
ctr                    13049  0 
ccm                    17773  0 
bnep                   19624  2 
rfcomm                 69509  8 
nls_iso8859_1          12713  1 
snd_hda_codec_hdmi     47548  1 
snd_hda_codec_realtek    77467  1 
snd_hda_codec_generic    68937  1 snd_hda_codec_realtek
uvcvideo               81073  0 
videobuf2_vmalloc      13216  1 uvcvideo
videobuf2_memops       13362  1 videobuf2_vmalloc
videobuf2_core         59104  1 uvcvideo
v4l2_common            15681  1 videobuf2_core
videodev              153793  3 uvcvideo,v4l2_common,videobuf2_core
media                  21903  2 uvcvideo,videodev
intel_rapl             18783  0 
x86_pkg_temp_thermal    14205  0 
intel_powerclamp       18823  0 
coretemp               13441  0 
kvm_intel             143590  0 
kvm                   452043  1 kvm_intel
crct10dif_pclmul       14307  0 
snd_hda_intel          30469  3 
crc32_pclmul           13133  0 
snd_hda_controller     31056  1 snd_hda_intel
ghash_clmulni_intel    13230  0 
snd_hda_codec         139682  5 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_hda_intel,snd_hda_controller
cryptd                 20359  1 ghash_clmulni_intel
snd_hwdep              17698  1 snd_hda_codec
snd_pcm               104112  4 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel,snd_hda_controller
snd_seq_midi           13564  0 
snd_seq_midi_event     14899  1 snd_seq_midi
arc4                   12608  2 
snd_rawmidi            30876  1 snd_seq_midi
ath3k                  13331  0 
snd_seq                63074  2 snd_seq_midi_event,snd_seq_midi
joydev                 17393  0 
ath9k                 137283  0 
serio_raw              13483  0 
ath9k_common           25638  1 ath9k
ath9k_hw              446521  2 ath9k_common,ath9k
ath                    29006  3 ath9k_common,ath9k,ath9k_hw
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              29562  2 snd_pcm,snd_seq
i915                  905954  4 
mac80211              652718  1 ath9k
btusb                  32497  0 
bluetooth             446409  23 bnep,ath3k,btusb,rfcomm
nouveau              1206535  1 
cfg80211              494362  4 ath,ath9k_common,ath9k,mac80211
6lowpan_iphc           18702  1 bluetooth
lpc_ich                21093  0 
ttm                    93588  1 nouveau
snd                    79468  17 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec_generic,snd_hda_codec,snd_hda_intel,snd_seq_device
drm_kms_helper         61574  2 i915,nouveau
drm                   311018  9 ttm,i915,drm_kms_helper,nouveau
mei_me                 19696  0 
soundcore              15047  2 snd,snd_hda_codec
mei                    87875  1 mei_me
i2c_algo_bit           13413  2 i915,nouveau
shpchp                 37047  0 
mxm_wmi                13021  1 nouveau
wmi                    19193  2 mxm_wmi,nouveau
video                  20128  2 i915,nouveau
mac_hid                13227  0 
parport_pc             32741  0 
ppdev                  17671  0 
lp                     17759  0 
parport                42348  3 lp,ppdev,parport_pc
hid_logitech_dj        18469  0 
usbhid                 52616  0 
hid                   110426  4 usbhid,hid_logitech_dj
psmouse               106561  0 
ahci                   34062  4 
r8169                  71694  0 
libahci                32424  1 ahci
mii                    13934  1 r8169
             total       used       free     shared    buffers     cached
Mem:       8059604    4872568    3187036     573896      62628     844724
-/+ buffers/cache:    3965216    4094388
Swap:     15625212     405360   15219852
/usr/lib/pm-utils/sleep.d/00logging suspend suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/00powersave suspend suspend:
/usr/lib/pm-utils/sleep.d/00powersave suspend suspend: success.


Running hook /etc/pm/sleep.d/10_grub-common suspend suspend:
/etc/pm/sleep.d/10_grub-common suspend suspend: success.


Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend:
/etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/50unload_alx suspend suspend:
/usr/lib/pm-utils/sleep.d/50unload_alx suspend suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend:
Failed to connect to non-global ctrl_ifname: (null)  error: No such file or directory
/usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/75modules suspend suspend:
Unloading kernel module r8169...Done.
/usr/lib/pm-utils/sleep.d/75modules suspend suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/90clock suspend suspend:
/usr/lib/pm-utils/sleep.d/90clock suspend suspend: not applicable.


Running hook /usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend:
/usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/95anacron suspend suspend:
stop: Unknown instance: 
/usr/lib/pm-utils/sleep.d/95anacron suspend suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend:
/usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend: not applicable.


Running hook /usr/lib/pm-utils/sleep.d/95led suspend suspend:
/usr/lib/pm-utils/sleep.d/95led suspend suspend: not applicable.


Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend:
Kernel modesetting video driver detected, not using quirks.
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/99video suspend suspend:
kernel.acpi_video_flags = 0
/usr/lib/pm-utils/sleep.d/99video suspend suspend: success.


Running hook /etc/pm/sleep.d/novatel_3g_suspend suspend suspend:
/etc/pm/sleep.d/novatel_3g_suspend suspend suspend: success.


Wed Apr  8 17:46:33 EEST 2015: performing suspend
Fri Apr 10 17:13:00 EEST 2015: Awake.
Fri Apr 10 17:13:00 EEST 2015: Running hooks for resume
Running hook /etc/pm/sleep.d/novatel_3g_suspend resume suspend:
/etc/pm/sleep.d/novatel_3g_suspend resume suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/99video resume suspend:
/usr/lib/pm-utils/sleep.d/99video resume suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend:
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/95led resume suspend:
/usr/lib/pm-utils/sleep.d/95led resume suspend: not applicable.


Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm resume suspend:


/dev/sda:
 setting Advanced Power Management level to 0xfe (254)
 APM_level    = 254
/usr/lib/pm-utils/sleep.d/95hdparm-apm resume suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/95anacron resume suspend:
/usr/lib/pm-utils/sleep.d/95anacron resume suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/94cpufreq resume suspend:
/usr/lib/pm-utils/sleep.d/94cpufreq resume suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/90clock resume suspend:
/usr/lib/pm-utils/sleep.d/90clock resume suspend: not applicable.


Running hook /usr/lib/pm-utils/sleep.d/75modules resume suspend:
Reloaded unloaded modules.
/usr/lib/pm-utils/sleep.d/75modules resume suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant resume suspend:
Failed to connect to non-global ctrl_ifname: (null)  error: No such file or directory
/usr/lib/pm-utils/sleep.d/60_wpa_supplicant resume suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/50unload_alx resume suspend:
/usr/lib/pm-utils/sleep.d/50unload_alx resume suspend: success.


Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate resume suspend:
/etc/pm/sleep.d/10_unattended-upgrades-hibernate resume suspend: success.


Running hook /etc/pm/sleep.d/10_grub-common resume suspend:
/etc/pm/sleep.d/10_grub-common resume suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/00powersave resume suspend:
/usr/lib/pm-utils/sleep.d/00powersave resume suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/00logging resume suspend:
/usr/lib/pm-utils/sleep.d/00logging resume suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/000record-status resume suspend:
/usr/lib/pm-utils/sleep.d/000record-status resume suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/000kernel-change resume suspend:
/usr/lib/pm-utils/sleep.d/000kernel-change resume suspend: success.


Fri Apr 10 17:13:01 EEST 2015: Finished.
Initial commandline parameters: 
Fri Apr 10 23:16:33 EEST 2015: Running hooks for suspend.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:
/usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/000record-status suspend suspend:
/usr/lib/pm-utils/sleep.d/000record-status suspend suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/00logging suspend suspend:
Linux laptop 3.16.0-33-generic #44~14.04.1-Ubuntu SMP Fri Mar 13 10:33:29 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux
Module                  Size  Used by
ctr                    13049  0 
ccm                    17773  0 
bnep                   19624  2 
rfcomm                 69509  8 
nls_iso8859_1          12713  1 
uvcvideo               81073  0 
videobuf2_vmalloc      13216  1 uvcvideo
videobuf2_memops       13362  1 videobuf2_vmalloc
videobuf2_core         59104  1 uvcvideo
v4l2_common            15681  1 videobuf2_core
videodev              153793  3 uvcvideo,v4l2_common,videobuf2_core
media                  21903  2 uvcvideo,videodev
snd_hda_codec_hdmi     47548  1 
snd_hda_codec_realtek    77467  1 
snd_hda_codec_generic    68937  1 snd_hda_codec_realtek
intel_rapl             18783  0 
x86_pkg_temp_thermal    14205  0 
intel_powerclamp       18823  0 
coretemp               13441  0 
kvm_intel             143590  0 
kvm                   452043  1 kvm_intel
crct10dif_pclmul       14307  0 
crc32_pclmul           13133  0 
ghash_clmulni_intel    13230  0 
snd_hda_intel          30469  3 
cryptd                 20359  1 ghash_clmulni_intel
snd_hda_controller     31056  1 snd_hda_intel
snd_hda_codec         139682  5 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_hda_intel,snd_hda_controller
snd_hwdep              17698  1 snd_hda_codec
snd_pcm               104112  4 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel,snd_hda_controller
joydev                 17393  0 
serio_raw              13483  0 
snd_seq_midi           13564  0 
snd_seq_midi_event     14899  1 snd_seq_midi
ath3k                  13331  0 
snd_rawmidi            30876  1 snd_seq_midi
arc4                   12608  2 
snd_seq                63074  2 snd_seq_midi_event,snd_seq_midi
nouveau              1206535  1 
ath9k                 137283  0 
ath9k_common           25638  1 ath9k
ath9k_hw              446521  2 ath9k_common,ath9k
lpc_ich                21093  0 
btusb                  32497  0 
ath                    29006  3 ath9k_common,ath9k,ath9k_hw
bluetooth             446409  23 bnep,ath3k,btusb,rfcomm
mac80211              652718  1 ath9k
6lowpan_iphc           18702  1 bluetooth
ttm                    93588  1 nouveau
i915                  905954  5 
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
cfg80211              494362  4 ath,ath9k_common,ath9k,mac80211
snd_timer              29562  2 snd_pcm,snd_seq
drm_kms_helper         61574  2 i915,nouveau
snd                    79468  17 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec_generic,snd_hda_codec,snd_hda_intel,snd_seq_device
drm                   311018  10 ttm,i915,drm_kms_helper,nouveau
mei_me                 19696  0 
mei                    87875  1 mei_me
soundcore              15047  2 snd,snd_hda_codec
i2c_algo_bit           13413  2 i915,nouveau
shpchp                 37047  0 
mxm_wmi                13021  1 nouveau
wmi                    19193  2 mxm_wmi,nouveau
video                  20128  2 i915,nouveau
mac_hid                13227  0 
parport_pc             32741  0 
ppdev                  17671  0 
lp                     17759  0 
parport                42348  3 lp,ppdev,parport_pc
hid_logitech_dj        18469  0 
usbhid                 52616  0 
hid                   110426  4 usbhid,hid_logitech_dj
psmouse               106561  0 
r8169                  71694  0 
ahci                   34062  4 
libahci                32424  1 ahci
mii                    13934  1 r8169
             total       used       free     shared    buffers     cached
Mem:       8059604    5330684    2728920     258176      95564    1305072
-/+ buffers/cache:    3930048    4129556
Swap:     15625212    1220720   14404492
/usr/lib/pm-utils/sleep.d/00logging suspend suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/00powersave suspend suspend:
/usr/lib/pm-utils/sleep.d/00powersave suspend suspend: success.


Running hook /etc/pm/sleep.d/10_grub-common suspend suspend:
/etc/pm/sleep.d/10_grub-common suspend suspend: success.


Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend:
/etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/50unload_alx suspend suspend:
/usr/lib/pm-utils/sleep.d/50unload_alx suspend suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend:
Failed to connect to non-global ctrl_ifname: (null)  error: No such file or directory
/usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/75modules suspend suspend:
Unloading kernel module r8169...Done.
/usr/lib/pm-utils/sleep.d/75modules suspend suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/90clock suspend suspend:
/usr/lib/pm-utils/sleep.d/90clock suspend suspend: not applicable.


Running hook /usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend:
/usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/95anacron suspend suspend:
stop: Unknown instance: 
/usr/lib/pm-utils/sleep.d/95anacron suspend suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend:
/usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend: not applicable.


Running hook /usr/lib/pm-utils/sleep.d/95led suspend suspend:
/usr/lib/pm-utils/sleep.d/95led suspend suspend: not applicable.


Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend:
Kernel modesetting video driver detected, not using quirks.
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/99video suspend suspend:
kernel.acpi_video_flags = 0
/usr/lib/pm-utils/sleep.d/99video suspend suspend: success.


Running hook /etc/pm/sleep.d/novatel_3g_suspend suspend suspend:
/etc/pm/sleep.d/novatel_3g_suspend suspend suspend: success.


Fri Apr 10 23:16:35 EEST 2015: performing suspend
Sat Apr 11 18:57:36 EEST 2015: Awake.
Sat Apr 11 18:57:36 EEST 2015: Running hooks for resume
Running hook /etc/pm/sleep.d/novatel_3g_suspend resume suspend:
/etc/pm/sleep.d/novatel_3g_suspend resume suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/99video resume suspend:
/usr/lib/pm-utils/sleep.d/99video resume suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend:
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/95led resume suspend:
/usr/lib/pm-utils/sleep.d/95led resume suspend: not applicable.


Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm resume suspend:


/dev/sda:
 setting Advanced Power Management level to 0xfe (254)
 APM_level    = 254
/usr/lib/pm-utils/sleep.d/95hdparm-apm resume suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/95anacron resume suspend:
/usr/lib/pm-utils/sleep.d/95anacron resume suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/94cpufreq resume suspend:
/usr/lib/pm-utils/sleep.d/94cpufreq resume suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/90clock resume suspend:
/usr/lib/pm-utils/sleep.d/90clock resume suspend: not applicable.


Running hook /usr/lib/pm-utils/sleep.d/75modules resume suspend:
Reloaded unloaded modules.
/usr/lib/pm-utils/sleep.d/75modules resume suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant resume suspend:
Failed to connect to non-global ctrl_ifname: (null)  error: No such file or directory
/usr/lib/pm-utils/sleep.d/60_wpa_supplicant resume suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/50unload_alx resume suspend:
/usr/lib/pm-utils/sleep.d/50unload_alx resume suspend: success.


Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate resume suspend:
/etc/pm/sleep.d/10_unattended-upgrades-hibernate resume suspend: success.


Running hook /etc/pm/sleep.d/10_grub-common resume suspend:
/etc/pm/sleep.d/10_grub-common resume suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/00powersave resume suspend:
/usr/lib/pm-utils/sleep.d/00powersave resume suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/00logging resume suspend:
/usr/lib/pm-utils/sleep.d/00logging resume suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/000record-status resume suspend:
/usr/lib/pm-utils/sleep.d/000record-status resume suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/000kernel-change resume suspend:
/usr/lib/pm-utils/sleep.d/000kernel-change resume suspend: success.


Sat Apr 11 18:57:37 EEST 2015: Finished.
Initial commandline parameters: 
Sun Apr 12 00:48:53 EEST 2015: Running hooks for suspend.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:
/usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/000record-status suspend suspend:
/usr/lib/pm-utils/sleep.d/000record-status suspend suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/00logging suspend suspend:
Linux laptop 3.16.0-33-generic #44~14.04.1-Ubuntu SMP Fri Mar 13 10:33:29 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux
Module                  Size  Used by
ctr                    13049  0 
ccm                    17773  0 
bnep                   19624  2 
rfcomm                 69509  8 
nls_iso8859_1          12713  1 
uvcvideo               81073  0 
videobuf2_vmalloc      13216  1 uvcvideo
videobuf2_memops       13362  1 videobuf2_vmalloc
videobuf2_core         59104  1 uvcvideo
v4l2_common            15681  1 videobuf2_core
videodev              153793  3 uvcvideo,v4l2_common,videobuf2_core
media                  21903  2 uvcvideo,videodev
snd_hda_codec_hdmi     47548  1 
snd_hda_codec_realtek    77467  1 
snd_hda_codec_generic    68937  1 snd_hda_codec_realtek
intel_rapl             18783  0 
x86_pkg_temp_thermal    14205  0 
intel_powerclamp       18823  0 
coretemp               13441  0 
kvm_intel             143590  0 
kvm                   452043  1 kvm_intel
crct10dif_pclmul       14307  0 
crc32_pclmul           13133  0 
ghash_clmulni_intel    13230  0 
cryptd                 20359  1 ghash_clmulni_intel
snd_hda_intel          30469  5 
snd_hda_controller     31056  1 snd_hda_intel
snd_hda_codec         139682  5 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_hda_intel,snd_hda_controller
arc4                   12608  2 
snd_hwdep              17698  1 snd_hda_codec
joydev                 17393  0 
ath3k                  13331  0 
serio_raw              13483  0 
snd_pcm               104112  5 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel,snd_hda_controller
ath9k                 137283  0 
snd_seq_midi           13564  0 
ath9k_common           25638  1 ath9k
snd_seq_midi_event     14899  1 snd_seq_midi
ath9k_hw              446521  2 ath9k_common,ath9k
snd_rawmidi            30876  1 snd_seq_midi
ath                    29006  3 ath9k_common,ath9k,ath9k_hw
btusb                  32497  0 
bluetooth             446409  23 bnep,ath3k,btusb,rfcomm
mac80211              652718  1 ath9k
snd_seq                63074  2 snd_seq_midi_event,snd_seq_midi
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              29562  2 snd_pcm,snd_seq
6lowpan_iphc           18702  1 bluetooth
snd                    79468  20 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec_generic,snd_hda_codec,snd_hda_intel,snd_seq_device
cfg80211              494362  4 ath,ath9k_common,ath9k,mac80211
nouveau              1206535  1 
lpc_ich                21093  0 
i915                  905954  5 
soundcore              15047  2 snd,snd_hda_codec
ttm                    93588  1 nouveau
drm_kms_helper         61574  2 i915,nouveau
mei_me                 19696  0 
drm                   311018  10 ttm,i915,drm_kms_helper,nouveau
mei                    87875  1 mei_me
i2c_algo_bit           13413  2 i915,nouveau
shpchp                 37047  0 
mxm_wmi                13021  1 nouveau
mac_hid                13227  0 
wmi                    19193  2 mxm_wmi,nouveau
video                  20128  2 i915,nouveau
parport_pc             32741  0 
ppdev                  17671  0 
lp                     17759  0 
parport                42348  3 lp,ppdev,parport_pc
hid_logitech_dj        18469  0 
usbhid                 52616  0 
hid                   110426  4 usbhid,hid_logitech_dj
psmouse               106561  0 
ahci                   34062  5 
r8169                  71694  0 
libahci                32424  1 ahci
mii                    13934  1 r8169
             total       used       free     shared    buffers     cached
Mem:       8059604    5479764    2579840     595752      77352    1110624
-/+ buffers/cache:    4291788    3767816
Swap:     15625212    1080984   14544228
/usr/lib/pm-utils/sleep.d/00logging suspend suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/00powersave suspend suspend:
/usr/lib/pm-utils/sleep.d/00powersave suspend suspend: success.


Running hook /etc/pm/sleep.d/10_grub-common suspend suspend:
/etc/pm/sleep.d/10_grub-common suspend suspend: success.


Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend:
/etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/50unload_alx suspend suspend:
/usr/lib/pm-utils/sleep.d/50unload_alx suspend suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend:
Failed to connect to non-global ctrl_ifname: (null)  error: No such file or directory
/usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/75modules suspend suspend:
Unloading kernel module r8169...Done.
/usr/lib/pm-utils/sleep.d/75modules suspend suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/90clock suspend suspend:
/usr/lib/pm-utils/sleep.d/90clock suspend suspend: not applicable.


Running hook /usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend:
/usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/95anacron suspend suspend:
/usr/lib/pm-utils/sleep.d/95anacron suspend suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend:
/usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend: not applicable.


Running hook /usr/lib/pm-utils/sleep.d/95led suspend suspend:
/usr/lib/pm-utils/sleep.d/95led suspend suspend: not applicable.


Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend:
Kernel modesetting video driver detected, not using quirks.
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/99video suspend suspend:
kernel.acpi_video_flags = 0
/usr/lib/pm-utils/sleep.d/99video suspend suspend: success.


Running hook /etc/pm/sleep.d/novatel_3g_suspend suspend suspend:
/etc/pm/sleep.d/novatel_3g_suspend suspend suspend: success.


Sun Apr 12 00:48:55 EEST 2015: performing suspend
Sun Apr 12 18:58:27 EEST 2015: Awake.
Sun Apr 12 18:58:27 EEST 2015: Running hooks for resume
Running hook /etc/pm/sleep.d/novatel_3g_suspend resume suspend:
/etc/pm/sleep.d/novatel_3g_suspend resume suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/99video resume suspend:
/usr/lib/pm-utils/sleep.d/99video resume suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend:
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/95led resume suspend:
/usr/lib/pm-utils/sleep.d/95led resume suspend: not applicable.


Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm resume suspend:


/dev/sda:
 setting Advanced Power Management level to 0xfe (254)
 APM_level    = 254
/usr/lib/pm-utils/sleep.d/95hdparm-apm resume suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/95anacron resume suspend:
/usr/lib/pm-utils/sleep.d/95anacron resume suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/94cpufreq resume suspend:
/usr/lib/pm-utils/sleep.d/94cpufreq resume suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/90clock resume suspend:
/usr/lib/pm-utils/sleep.d/90clock resume suspend: not applicable.


Running hook /usr/lib/pm-utils/sleep.d/75modules resume suspend:
Reloaded unloaded modules.
/usr/lib/pm-utils/sleep.d/75modules resume suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant resume suspend:
Failed to connect to non-global ctrl_ifname: (null)  error: No such file or directory
/usr/lib/pm-utils/sleep.d/60_wpa_supplicant resume suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/50unload_alx resume suspend:
/usr/lib/pm-utils/sleep.d/50unload_alx resume suspend: success.


Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate resume suspend:
/etc/pm/sleep.d/10_unattended-upgrades-hibernate resume suspend: success.


Running hook /etc/pm/sleep.d/10_grub-common resume suspend:
/etc/pm/sleep.d/10_grub-common resume suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/00powersave resume suspend:
/usr/lib/pm-utils/sleep.d/00powersave resume suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/00logging resume suspend:
/usr/lib/pm-utils/sleep.d/00logging resume suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/000record-status resume suspend:
/usr/lib/pm-utils/sleep.d/000record-status resume suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/000kernel-change resume suspend:
/usr/lib/pm-utils/sleep.d/000kernel-change resume suspend: success.


Sun Apr 12 18:58:29 EEST 2015: Finished.
Initial commandline parameters: 
Sun Apr 12 23:37:07 EEST 2015: Running hooks for suspend.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:
/usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/000record-status suspend suspend:
/usr/lib/pm-utils/sleep.d/000record-status suspend suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/00logging suspend suspend:
Linux laptop 3.16.0-33-generic #44~14.04.1-Ubuntu SMP Fri Mar 13 10:33:29 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux
Module                  Size  Used by
ctr                    13049  0 
ccm                    17773  0 
rfcomm                 69509  8 
bnep                   19624  2 
nls_iso8859_1          12713  1 
uvcvideo               81073  0 
videobuf2_vmalloc      13216  1 uvcvideo
videobuf2_memops       13362  1 videobuf2_vmalloc
videobuf2_core         59104  1 uvcvideo
v4l2_common            15681  1 videobuf2_core
videodev              153793  3 uvcvideo,v4l2_common,videobuf2_core
media                  21903  2 uvcvideo,videodev
snd_hda_codec_hdmi     47548  1 
snd_hda_codec_realtek    77467  1 
snd_hda_codec_generic    68937  1 snd_hda_codec_realtek
intel_rapl             18783  0 
x86_pkg_temp_thermal    14205  0 
intel_powerclamp       18823  0 
coretemp               13441  0 
kvm_intel             143590  0 
kvm                   452043  1 kvm_intel
crct10dif_pclmul       14307  0 
crc32_pclmul           13133  0 
snd_hda_intel          30469  3 
snd_hda_controller     31056  1 snd_hda_intel
ghash_clmulni_intel    13230  0 
cryptd                 20359  1 ghash_clmulni_intel
snd_hda_codec         139682  5 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_hda_intel,snd_hda_controller
joydev                 17393  0 
arc4                   12608  2 
snd_hwdep              17698  1 snd_hda_codec
snd_pcm               104112  4 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel,snd_hda_controller
serio_raw              13483  0 
ath9k                 137283  0 
ath3k                  13331  0 
ath9k_common           25638  1 ath9k
snd_seq_midi           13564  0 
ath9k_hw              446521  2 ath9k_common,ath9k
snd_seq_midi_event     14899  1 snd_seq_midi
btusb                  32497  0 
bluetooth             446409  23 bnep,ath3k,btusb,rfcomm
ath                    29006  3 ath9k_common,ath9k,ath9k_hw
mac80211              652718  1 ath9k
6lowpan_iphc           18702  1 bluetooth
nouveau              1206535  1 
snd_rawmidi            30876  1 snd_seq_midi
i915                  905954  5 
cfg80211              494362  4 ath,ath9k_common,ath9k,mac80211
snd_seq                63074  2 snd_seq_midi_event,snd_seq_midi
ttm                    93588  1 nouveau
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              29562  2 snd_pcm,snd_seq
lpc_ich                21093  0 
drm_kms_helper         61574  2 i915,nouveau
snd                    79468  17 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec_generic,snd_hda_codec,snd_hda_intel,snd_seq_device
drm                   311018  10 ttm,i915,drm_kms_helper,nouveau
mei_me                 19696  0 
mei                    87875  1 mei_me
soundcore              15047  2 snd,snd_hda_codec
i2c_algo_bit           13413  2 i915,nouveau
shpchp                 37047  0 
mxm_wmi                13021  1 nouveau
parport_pc             32741  0 
wmi                    19193  2 mxm_wmi,nouveau
ppdev                  17671  0 
video                  20128  2 i915,nouveau
mac_hid                13227  0 
lp                     17759  0 
parport                42348  3 lp,ppdev,parport_pc
hid_logitech_dj        18469  0 
usbhid                 52616  0 
hid                   110426  4 usbhid,hid_logitech_dj
psmouse               106561  0 
ahci                   34062  4 
r8169                  71694  0 
libahci                32424  1 ahci
mii                    13934  1 r8169
             total       used       free     shared    buffers     cached
Mem:       8059604    7247772     811832     431880      54848    1576192
-/+ buffers/cache:    5616732    2442872
Swap:     15625212     525212   15100000
/usr/lib/pm-utils/sleep.d/00logging suspend suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/00powersave suspend suspend:
/usr/lib/pm-utils/sleep.d/00powersave suspend suspend: success.


Running hook /etc/pm/sleep.d/10_grub-common suspend suspend:
/etc/pm/sleep.d/10_grub-common suspend suspend: success.


Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend:
/etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/50unload_alx suspend suspend:
/usr/lib/pm-utils/sleep.d/50unload_alx suspend suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend:
Failed to connect to non-global ctrl_ifname: (null)  error: No such file or directory
/usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/75modules suspend suspend:
Unloading kernel module r8169...Done.
/usr/lib/pm-utils/sleep.d/75modules suspend suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/90clock suspend suspend:
/usr/lib/pm-utils/sleep.d/90clock suspend suspend: not applicable.


Running hook /usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend:
/usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/95anacron suspend suspend:
stop: Unknown instance: 
/usr/lib/pm-utils/sleep.d/95anacron suspend suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend:
/usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend: not applicable.


Running hook /usr/lib/pm-utils/sleep.d/95led suspend suspend:
/usr/lib/pm-utils/sleep.d/95led suspend suspend: not applicable.


Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend:
Kernel modesetting video driver detected, not using quirks.
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/99video suspend suspend:
kernel.acpi_video_flags = 0
/usr/lib/pm-utils/sleep.d/99video suspend suspend: success.


Running hook /etc/pm/sleep.d/novatel_3g_suspend suspend suspend:
/etc/pm/sleep.d/novatel_3g_suspend suspend suspend: success.


Sun Apr 12 23:37:09 EEST 2015: performing suspend
Mon Apr 13 15:06:51 EEST 2015: Awake.
Mon Apr 13 15:06:51 EEST 2015: Running hooks for resume
Running hook /etc/pm/sleep.d/novatel_3g_suspend resume suspend:
/etc/pm/sleep.d/novatel_3g_suspend resume suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/99video resume suspend:
/usr/lib/pm-utils/sleep.d/99video resume suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend:
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/95led resume suspend:
/usr/lib/pm-utils/sleep.d/95led resume suspend: not applicable.


Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm resume suspend:


/dev/sda:
 setting Advanced Power Management level to 0xfe (254)
 APM_level    = 254
/usr/lib/pm-utils/sleep.d/95hdparm-apm resume suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/95anacron resume suspend:
/usr/lib/pm-utils/sleep.d/95anacron resume suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/94cpufreq resume suspend:
/usr/lib/pm-utils/sleep.d/94cpufreq resume suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/90clock resume suspend:
/usr/lib/pm-utils/sleep.d/90clock resume suspend: not applicable.


Running hook /usr/lib/pm-utils/sleep.d/75modules resume suspend:
Reloaded unloaded modules.
/usr/lib/pm-utils/sleep.d/75modules resume suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant resume suspend:
Failed to connect to non-global ctrl_ifname: (null)  error: No such file or directory
/usr/lib/pm-utils/sleep.d/60_wpa_supplicant resume suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/50unload_alx resume suspend:
/usr/lib/pm-utils/sleep.d/50unload_alx resume suspend: success.


Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate resume suspend:
/etc/pm/sleep.d/10_unattended-upgrades-hibernate resume suspend: success.


Running hook /etc/pm/sleep.d/10_grub-common resume suspend:
/etc/pm/sleep.d/10_grub-common resume suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/00powersave resume suspend:
/usr/lib/pm-utils/sleep.d/00powersave resume suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/00logging resume suspend:
/usr/lib/pm-utils/sleep.d/00logging resume suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/000record-status resume suspend:
/usr/lib/pm-utils/sleep.d/000record-status resume suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/000kernel-change resume suspend:
/usr/lib/pm-utils/sleep.d/000kernel-change resume suspend: success.


Mon Apr 13 15:06:52 EEST 2015: Finished.
Initial commandline parameters: 
Mon Apr 13 21:40:25 EEST 2015: Running hooks for suspend.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:
/usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/000record-status suspend suspend:
/usr/lib/pm-utils/sleep.d/000record-status suspend suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/00logging suspend suspend:
Linux laptop 3.16.0-33-generic #44~14.04.1-Ubuntu SMP Fri Mar 13 10:33:29 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux
Module                  Size  Used by
ctr                    13049  0 
ccm                    17773  0 
rfcomm                 69509  8 
bnep                   19624  2 
nls_iso8859_1          12713  1 
snd_hda_codec_hdmi     47548  1 
snd_hda_codec_realtek    77467  1 
snd_hda_codec_generic    68937  1 snd_hda_codec_realtek
uvcvideo               81073  0 
videobuf2_vmalloc      13216  1 uvcvideo
videobuf2_memops       13362  1 videobuf2_vmalloc
videobuf2_core         59104  1 uvcvideo
v4l2_common            15681  1 videobuf2_core
videodev              153793  3 uvcvideo,v4l2_common,videobuf2_core
media                  21903  2 uvcvideo,videodev
intel_rapl             18783  0 
x86_pkg_temp_thermal    14205  0 
intel_powerclamp       18823  0 
coretemp               13441  0 
kvm_intel             143590  0 
kvm                   452043  1 kvm_intel
crct10dif_pclmul       14307  0 
snd_hda_intel          30469  3 
snd_hda_controller     31056  1 snd_hda_intel
crc32_pclmul           13133  0 
snd_hda_codec         139682  5 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_hda_intel,snd_hda_controller
ghash_clmulni_intel    13230  0 
cryptd                 20359  1 ghash_clmulni_intel
snd_hwdep              17698  1 snd_hda_codec
snd_pcm               104112  4 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel,snd_hda_controller
joydev                 17393  0 
snd_seq_midi           13564  0 
snd_seq_midi_event     14899  1 snd_seq_midi
serio_raw              13483  0 
arc4                   12608  2 
ath3k                  13331  0 
snd_rawmidi            30876  1 snd_seq_midi
ath9k                 137283  0 
nouveau              1206535  1 
snd_seq                63074  2 snd_seq_midi_event,snd_seq_midi
ath9k_common           25638  1 ath9k
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
ath9k_hw              446521  2 ath9k_common,ath9k
snd_timer              29562  2 snd_pcm,snd_seq
btusb                  32497  0 
ath                    29006  3 ath9k_common,ath9k,ath9k_hw
bluetooth             446409  23 bnep,ath3k,btusb,rfcomm
mac80211              652718  1 ath9k
6lowpan_iphc           18702  1 bluetooth
ttm                    93588  1 nouveau
i915                  905954  5 
lpc_ich                21093  0 
cfg80211              494362  4 ath,ath9k_common,ath9k,mac80211
mei_me                 19696  0 
drm_kms_helper         61574  2 i915,nouveau
drm                   311018  10 ttm,i915,drm_kms_helper,nouveau
snd                    79468  17 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec_generic,snd_hda_codec,snd_hda_intel,snd_seq_device
mei                    87875  1 mei_me
shpchp                 37047  0 
soundcore              15047  2 snd,snd_hda_codec
i2c_algo_bit           13413  2 i915,nouveau
mxm_wmi                13021  1 nouveau
video                  20128  2 i915,nouveau
mac_hid                13227  0 
wmi                    19193  2 mxm_wmi,nouveau
parport_pc             32741  0 
ppdev                  17671  0 
lp                     17759  0 
parport                42348  3 lp,ppdev,parport_pc
hid_logitech_dj        18469  0 
usbhid                 52616  0 
hid                   110426  4 usbhid,hid_logitech_dj
psmouse               106561  0 
ahci                   34062  4 
libahci                32424  1 ahci
r8169                  71694  0 
mii                    13934  1 r8169
             total       used       free     shared    buffers     cached
Mem:       8059604    7109360     950244     654980      49112    1608480
-/+ buffers/cache:    5451768    2607836
Swap:     15625212      27284   15597928
/usr/lib/pm-utils/sleep.d/00logging suspend suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/00powersave suspend suspend:
/usr/lib/pm-utils/sleep.d/00powersave suspend suspend: success.


Running hook /etc/pm/sleep.d/10_grub-common suspend suspend:
/etc/pm/sleep.d/10_grub-common suspend suspend: success.


Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend:
/etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/50unload_alx suspend suspend:
/usr/lib/pm-utils/sleep.d/50unload_alx suspend suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend:
Failed to connect to non-global ctrl_ifname: (null)  error: No such file or directory
/usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/75modules suspend suspend:
Unloading kernel module r8169...Done.
/usr/lib/pm-utils/sleep.d/75modules suspend suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/90clock suspend suspend:
/usr/lib/pm-utils/sleep.d/90clock suspend suspend: not applicable.


Running hook /usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend:
/usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/95anacron suspend suspend:
stop: Unknown instance: 
/usr/lib/pm-utils/sleep.d/95anacron suspend suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend:
/usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend: not applicable.


Running hook /usr/lib/pm-utils/sleep.d/95led suspend suspend:
/usr/lib/pm-utils/sleep.d/95led suspend suspend: not applicable.


Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend:
Kernel modesetting video driver detected, not using quirks.
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/99video suspend suspend:
kernel.acpi_video_flags = 0
/usr/lib/pm-utils/sleep.d/99video suspend suspend: success.


Running hook /etc/pm/sleep.d/novatel_3g_suspend suspend suspend:
/etc/pm/sleep.d/novatel_3g_suspend suspend suspend: success.


Mon Apr 13 21:40:27 EEST 2015: performing suspend
Wed Apr 15 02:42:56 EEST 2015: Awake.
Wed Apr 15 02:42:56 EEST 2015: Running hooks for resume
Running hook /etc/pm/sleep.d/novatel_3g_suspend resume suspend:
/etc/pm/sleep.d/novatel_3g_suspend resume suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/99video resume suspend:
/usr/lib/pm-utils/sleep.d/99video resume suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend:
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/95led resume suspend:
/usr/lib/pm-utils/sleep.d/95led resume suspend: not applicable.


Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm resume suspend:


/dev/sda:
 setting Advanced Power Management level to 0x80 (128)
 APM_level    = 128


/dev/sda:
 setting standby to 36 (3 minutes)
/usr/lib/pm-utils/sleep.d/95hdparm-apm resume suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/95anacron resume suspend:
/usr/lib/pm-utils/sleep.d/95anacron resume suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/94cpufreq resume suspend:
/usr/lib/pm-utils/sleep.d/94cpufreq resume suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/90clock resume suspend:
/usr/lib/pm-utils/sleep.d/90clock resume suspend: not applicable.


Running hook /usr/lib/pm-utils/sleep.d/75modules resume suspend:
Reloaded unloaded modules.
/usr/lib/pm-utils/sleep.d/75modules resume suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant resume suspend:
Failed to connect to non-global ctrl_ifname: (null)  error: No such file or directory
/usr/lib/pm-utils/sleep.d/60_wpa_supplicant resume suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/50unload_alx resume suspend:
/usr/lib/pm-utils/sleep.d/50unload_alx resume suspend: success.


Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate resume suspend:
/etc/pm/sleep.d/10_unattended-upgrades-hibernate resume suspend: success.


Running hook /etc/pm/sleep.d/10_grub-common resume suspend:
/etc/pm/sleep.d/10_grub-common resume suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/00powersave resume suspend:
/usr/lib/pm-utils/sleep.d/00powersave resume suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/00logging resume suspend:
/usr/lib/pm-utils/sleep.d/00logging resume suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/000record-status resume suspend:
/usr/lib/pm-utils/sleep.d/000record-status resume suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/000kernel-change resume suspend:
/usr/lib/pm-utils/sleep.d/000kernel-change resume suspend: success.


Wed Apr 15 02:42:57 EEST 2015: Finished.
Initial commandline parameters: 
Wed Apr 15 04:17:04 EEST 2015: Running hooks for suspend.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:
/usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/000record-status suspend suspend:
/usr/lib/pm-utils/sleep.d/000record-status suspend suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/00logging suspend suspend:
Linux laptop 3.16.0-33-generic #44~14.04.1-Ubuntu SMP Fri Mar 13 10:33:29 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux
Module                  Size  Used by
ctr                    13049  0 
ccm                    17773  0 
rfcomm                 69509  8 
bnep                   19624  2 
nls_iso8859_1          12713  1 
uvcvideo               81073  0 
videobuf2_vmalloc      13216  1 uvcvideo
videobuf2_memops       13362  1 videobuf2_vmalloc
videobuf2_core         59104  1 uvcvideo
v4l2_common            15681  1 videobuf2_core
videodev              153793  3 uvcvideo,v4l2_common,videobuf2_core
media                  21903  2 uvcvideo,videodev
snd_hda_codec_hdmi     47548  1 
snd_hda_codec_realtek    77467  1 
snd_hda_codec_generic    68937  1 snd_hda_codec_realtek
snd_hda_intel          30469  3 
snd_hda_controller     31056  1 snd_hda_intel
intel_rapl             18783  0 
x86_pkg_temp_thermal    14205  0 
snd_hda_codec         139682  5 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_hda_intel,snd_hda_controller
intel_powerclamp       18823  0 
coretemp               13441  0 
snd_hwdep              17698  1 snd_hda_codec
kvm_intel             143590  0 
kvm                   452043  1 kvm_intel
snd_pcm               104112  4 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel,snd_hda_controller
crct10dif_pclmul       14307  0 
snd_seq_midi           13564  0 
crc32_pclmul           13133  0 
snd_seq_midi_event     14899  1 snd_seq_midi
ghash_clmulni_intel    13230  0 
snd_rawmidi            30876  1 snd_seq_midi
cryptd                 20359  1 ghash_clmulni_intel
snd_seq                63074  2 snd_seq_midi_event,snd_seq_midi
arc4                   12608  2 
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              29562  2 snd_pcm,snd_seq
snd                    79468  17 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec_generic,snd_hda_codec,snd_hda_intel,snd_seq_device
joydev                 17393  0 
ath9k                 137283  0 
serio_raw              13483  0 
ath9k_common           25638  1 ath9k
ath3k                  13331  0 
ath9k_hw              446521  2 ath9k_common,ath9k
ath                    29006  3 ath9k_common,ath9k,ath9k_hw
mac80211              652718  1 ath9k
soundcore              15047  2 snd,snd_hda_codec
lpc_ich                21093  0 
nouveau              1206535  1 
btusb                  32497  0 
bluetooth             446409  23 bnep,ath3k,btusb,rfcomm
i915                  905954  4 
ttm                    93588  1 nouveau
6lowpan_iphc           18702  1 bluetooth
cfg80211              494362  4 ath,ath9k_common,ath9k,mac80211
drm_kms_helper         61574  2 i915,nouveau
mei_me                 19696  0 
drm                   311018  9 ttm,i915,drm_kms_helper,nouveau
shpchp                 37047  0 
mei                    87875  1 mei_me
i2c_algo_bit           13413  2 i915,nouveau
parport_pc             32741  0 
ppdev                  17671  0 
lp                     17759  0 
parport                42348  3 lp,ppdev,parport_pc
mxm_wmi                13021  1 nouveau
wmi                    19193  2 mxm_wmi,nouveau
video                  20128  2 i915,nouveau
mac_hid                13227  0 
hid_logitech_dj        18469  0 
usbhid                 52616  0 
hid                   110426  4 usbhid,hid_logitech_dj
psmouse               106561  0 
ahci                   34062  4 
r8169                  71694  0 
libahci                32424  1 ahci
mii                    13934  1 r8169
             total       used       free     shared    buffers     cached
Mem:       8059604    5702744    2356860     178972      13364     437084
-/+ buffers/cache:    5252296    2807308
Swap:     15625212     547632   15077580
/usr/lib/pm-utils/sleep.d/00logging suspend suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/00powersave suspend suspend:
/usr/lib/pm-utils/sleep.d/00powersave suspend suspend: success.


Running hook /etc/pm/sleep.d/10_grub-common suspend suspend:
/etc/pm/sleep.d/10_grub-common suspend suspend: success.


Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend:
/etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/50unload_alx suspend suspend:
/usr/lib/pm-utils/sleep.d/50unload_alx suspend suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend:
Failed to connect to non-global ctrl_ifname: (null)  error: No such file or directory
/usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/75modules suspend suspend:
Unloading kernel module r8169...Done.
/usr/lib/pm-utils/sleep.d/75modules suspend suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/90clock suspend suspend:
/usr/lib/pm-utils/sleep.d/90clock suspend suspend: not applicable.


Running hook /usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend:
/usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/95anacron suspend suspend:
stop: Unknown instance: 
/usr/lib/pm-utils/sleep.d/95anacron suspend suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend:
/usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend: not applicable.


Running hook /usr/lib/pm-utils/sleep.d/95led suspend suspend:
/usr/lib/pm-utils/sleep.d/95led suspend suspend: not applicable.


Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend:
Kernel modesetting video driver detected, not using quirks.
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/99video suspend suspend:
kernel.acpi_video_flags = 0
/usr/lib/pm-utils/sleep.d/99video suspend suspend: success.


Running hook /etc/pm/sleep.d/novatel_3g_suspend suspend suspend:
/etc/pm/sleep.d/novatel_3g_suspend suspend suspend: success.


Wed Apr 15 04:17:10 EEST 2015: performing suspend
Wed Apr 15 15:31:56 EEST 2015: Awake.
Wed Apr 15 15:31:56 EEST 2015: Running hooks for resume
Running hook /etc/pm/sleep.d/novatel_3g_suspend resume suspend:
/etc/pm/sleep.d/novatel_3g_suspend resume suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/99video resume suspend:
/usr/lib/pm-utils/sleep.d/99video resume suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend:
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/95led resume suspend:
/usr/lib/pm-utils/sleep.d/95led resume suspend: not applicable.


Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm resume suspend:


/dev/sda:
 setting Advanced Power Management level to 0xfe (254)
 APM_level    = 254
/usr/lib/pm-utils/sleep.d/95hdparm-apm resume suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/95anacron resume suspend:
/usr/lib/pm-utils/sleep.d/95anacron resume suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/94cpufreq resume suspend:
/usr/lib/pm-utils/sleep.d/94cpufreq resume suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/90clock resume suspend:
/usr/lib/pm-utils/sleep.d/90clock resume suspend: not applicable.


Running hook /usr/lib/pm-utils/sleep.d/75modules resume suspend:
Reloaded unloaded modules.
/usr/lib/pm-utils/sleep.d/75modules resume suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant resume suspend:
Failed to connect to non-global ctrl_ifname: (null)  error: No such file or directory
/usr/lib/pm-utils/sleep.d/60_wpa_supplicant resume suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/50unload_alx resume suspend:
/usr/lib/pm-utils/sleep.d/50unload_alx resume suspend: success.


Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate resume suspend:
/etc/pm/sleep.d/10_unattended-upgrades-hibernate resume suspend: success.


Running hook /etc/pm/sleep.d/10_grub-common resume suspend:
/etc/pm/sleep.d/10_grub-common resume suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/00powersave resume suspend:
/usr/lib/pm-utils/sleep.d/00powersave resume suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/00logging resume suspend:
/usr/lib/pm-utils/sleep.d/00logging resume suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/000record-status resume suspend:
/usr/lib/pm-utils/sleep.d/000record-status resume suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/000kernel-change resume suspend:
/usr/lib/pm-utils/sleep.d/000kernel-change resume suspend: success.


Wed Apr 15 15:31:58 EEST 2015: Finished.
Initial commandline parameters: 
Thu Apr 16 01:46:25 EEST 2015: Running hooks for suspend.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:
/usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/000record-status suspend suspend:
/usr/lib/pm-utils/sleep.d/000record-status suspend suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/00logging suspend suspend:
Linux laptop 3.16.0-33-generic #44~14.04.1-Ubuntu SMP Fri Mar 13 10:33:29 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux
Module                  Size  Used by
ctr                    13049  0 
ccm                    17773  0 
rfcomm                 69509  8 
bnep                   19624  2 
nls_iso8859_1          12713  1 
snd_hda_codec_hdmi     47548  1 
snd_hda_codec_realtek    77467  1 
snd_hda_codec_generic    68937  1 snd_hda_codec_realtek
uvcvideo               81073  0 
videobuf2_vmalloc      13216  1 uvcvideo
videobuf2_memops       13362  1 videobuf2_vmalloc
videobuf2_core         59104  1 uvcvideo
v4l2_common            15681  1 videobuf2_core
videodev              153793  3 uvcvideo,v4l2_common,videobuf2_core
media                  21903  2 uvcvideo,videodev
snd_hda_intel          30469  3 
intel_rapl             18783  0 
x86_pkg_temp_thermal    14205  0 
intel_powerclamp       18823  0 
coretemp               13441  0 
snd_hda_controller     31056  1 snd_hda_intel
kvm_intel             143590  0 
snd_hda_codec         139682  5 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_hda_intel,snd_hda_controller
snd_hwdep              17698  1 snd_hda_codec
kvm                   452043  1 kvm_intel
crct10dif_pclmul       14307  0 
crc32_pclmul           13133  0 
ghash_clmulni_intel    13230  0 
cryptd                 20359  1 ghash_clmulni_intel
snd_pcm               104112  4 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel,snd_hda_controller
joydev                 17393  0 
serio_raw              13483  0 
snd_seq_midi           13564  0 
snd_seq_midi_event     14899  1 snd_seq_midi
snd_rawmidi            30876  1 snd_seq_midi
arc4                   12608  2 
ath3k                  13331  0 
i915                  905954  4 
ath9k                 137283  0 
nouveau              1206535  1 
snd_seq                63074  2 snd_seq_midi_event,snd_seq_midi
ath9k_common           25638  1 ath9k
lpc_ich                21093  0 
ath9k_hw              446521  2 ath9k_common,ath9k
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
ath                    29006  3 ath9k_common,ath9k,ath9k_hw
btusb                  32497  0 
bluetooth             446409  23 bnep,ath3k,btusb,rfcomm
ttm                    93588  1 nouveau
mac80211              652718  1 ath9k
6lowpan_iphc           18702  1 bluetooth
snd_timer              29562  2 snd_pcm,snd_seq
cfg80211              494362  4 ath,ath9k_common,ath9k,mac80211
drm_kms_helper         61574  2 i915,nouveau
snd                    79468  17 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec_generic,snd_hda_codec,snd_hda_intel,snd_seq_device
drm                   311018  9 ttm,i915,drm_kms_helper,nouveau
mei_me                 19696  0 
mei                    87875  1 mei_me
i2c_algo_bit           13413  2 i915,nouveau
soundcore              15047  2 snd,snd_hda_codec
shpchp                 37047  0 
mxm_wmi                13021  1 nouveau
parport_pc             32741  0 
wmi                    19193  2 mxm_wmi,nouveau
ppdev                  17671  0 
video                  20128  2 i915,nouveau
mac_hid                13227  0 
lp                     17759  0 
parport                42348  3 lp,ppdev,parport_pc
hid_logitech_dj        18469  0 
usbhid                 52616  0 
hid                   110426  4 usbhid,hid_logitech_dj
psmouse               106561  0 
ahci                   34062  4 
libahci                32424  1 ahci
r8169                  71694  0 
mii                    13934  1 r8169
             total       used       free     shared    buffers     cached
Mem:       8059604    5935324    2124280     400224      60584     724864
-/+ buffers/cache:    5149876    2909728
Swap:     15625212    1380540   14244672
/usr/lib/pm-utils/sleep.d/00logging suspend suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/00powersave suspend suspend:
/usr/lib/pm-utils/sleep.d/00powersave suspend suspend: success.


Running hook /etc/pm/sleep.d/10_grub-common suspend suspend:
/etc/pm/sleep.d/10_grub-common suspend suspend: success.


Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend:
/etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/50unload_alx suspend suspend:
/usr/lib/pm-utils/sleep.d/50unload_alx suspend suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend:
Failed to connect to non-global ctrl_ifname: (null)  error: No such file or directory
/usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/75modules suspend suspend:
Unloading kernel module r8169...Done.
/usr/lib/pm-utils/sleep.d/75modules suspend suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/90clock suspend suspend:
/usr/lib/pm-utils/sleep.d/90clock suspend suspend: not applicable.


Running hook /usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend:
/usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/95anacron suspend suspend:
/usr/lib/pm-utils/sleep.d/95anacron suspend suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend:
/usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend: not applicable.


Running hook /usr/lib/pm-utils/sleep.d/95led suspend suspend:
/usr/lib/pm-utils/sleep.d/95led suspend suspend: not applicable.


Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend:
Kernel modesetting video driver detected, not using quirks.
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/99video suspend suspend:
kernel.acpi_video_flags = 0
/usr/lib/pm-utils/sleep.d/99video suspend suspend: success.


Running hook /etc/pm/sleep.d/novatel_3g_suspend suspend suspend:
/etc/pm/sleep.d/novatel_3g_suspend suspend suspend: success.


Thu Apr 16 01:46:29 EEST 2015: performing suspend
Thu Apr 16 14:56:53 EEST 2015: Awake.
Thu Apr 16 14:56:53 EEST 2015: Running hooks for resume
Running hook /etc/pm/sleep.d/novatel_3g_suspend resume suspend:
/etc/pm/sleep.d/novatel_3g_suspend resume suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/99video resume suspend:
/usr/lib/pm-utils/sleep.d/99video resume suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend:
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/95led resume suspend:
/usr/lib/pm-utils/sleep.d/95led resume suspend: not applicable.


Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm resume suspend:


/dev/sda:
 setting Advanced Power Management level to 0xfe (254)
 APM_level    = 254
/usr/lib/pm-utils/sleep.d/95hdparm-apm resume suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/95anacron resume suspend:
/usr/lib/pm-utils/sleep.d/95anacron resume suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/94cpufreq resume suspend:
/usr/lib/pm-utils/sleep.d/94cpufreq resume suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/90clock resume suspend:
/usr/lib/pm-utils/sleep.d/90clock resume suspend: not applicable.


Running hook /usr/lib/pm-utils/sleep.d/75modules resume suspend:
Reloaded unloaded modules.
/usr/lib/pm-utils/sleep.d/75modules resume suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant resume suspend:
Failed to connect to non-global ctrl_ifname: (null)  error: No such file or directory
/usr/lib/pm-utils/sleep.d/60_wpa_supplicant resume suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/50unload_alx resume suspend:
/usr/lib/pm-utils/sleep.d/50unload_alx resume suspend: success.


Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate resume suspend:
/etc/pm/sleep.d/10_unattended-upgrades-hibernate resume suspend: success.


Running hook /etc/pm/sleep.d/10_grub-common resume suspend:
/etc/pm/sleep.d/10_grub-common resume suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/00powersave resume suspend:
/usr/lib/pm-utils/sleep.d/00powersave resume suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/00logging resume suspend:
/usr/lib/pm-utils/sleep.d/00logging resume suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/000record-status resume suspend:
/usr/lib/pm-utils/sleep.d/000record-status resume suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/000kernel-change resume suspend:
/usr/lib/pm-utils/sleep.d/000kernel-change resume suspend: success.


Thu Apr 16 14:56:54 EEST 2015: Finished.
Initial commandline parameters: 
Fri Apr 17 15:23:26 EEST 2015: Running hooks for suspend.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:
/usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/000record-status suspend suspend:
/usr/lib/pm-utils/sleep.d/000record-status suspend suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/00logging suspend suspend:
Linux laptop 4.0.0-040000-generic #201504121935 SMP Sun Apr 12 23:36:33 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux
Module                  Size  Used by
ctr                    16384  0 
ccm                    20480  0 
bnep                   24576  2 
rfcomm                 77824  8 
nls_iso8859_1          16384  1 
uvcvideo               94208  0 
videobuf2_vmalloc      16384  1 uvcvideo
videobuf2_memops       16384  1 videobuf2_vmalloc
videobuf2_core         53248  1 uvcvideo
v4l2_common            16384  1 videobuf2_core
videodev              163840  3 uvcvideo,v4l2_common,videobuf2_core
snd_hda_codec_hdmi     53248  1 
snd_hda_codec_realtek    81920  1 
intel_rapl             20480  0 
hid_logitech_hidpp     20480  0 
snd_hda_codec_generic    73728  1 snd_hda_codec_realtek
media                  24576  2 uvcvideo,videodev
iosf_mbi               16384  1 intel_rapl
snd_hda_intel          32768  3 
snd_hda_controller     36864  1 snd_hda_intel
x86_pkg_temp_thermal    16384  0 
intel_powerclamp       20480  0 
arc4                   16384  2 
coretemp               16384  0 
ath9k                 155648  0 
snd_hda_codec         147456  5 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_hda_intel,snd_hda_controller
kvm_intel             159744  0 
kvm                   512000  1 kvm_intel
ath9k_common           32768  1 ath9k
snd_hwdep              16384  1 snd_hda_codec
i915                 1126400  3 
ath9k_hw              487424  2 ath9k_common,ath9k
snd_pcm               110592  4 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel,snd_hda_controller
nouveau              1396736  1 
crct10dif_pclmul       16384  0 
ath                    32768  3 ath9k_common,ath9k,ath9k_hw
snd_seq_midi           16384  0 
snd_seq_midi_event     16384  1 snd_seq_midi
snd_rawmidi            32768  1 snd_seq_midi
mac80211              774144  1 ath9k
snd_seq                69632  2 snd_seq_midi_event,snd_seq_midi
snd_seq_device         16384  3 snd_seq,snd_rawmidi,snd_seq_midi
mxm_wmi                16384  1 nouveau
ttm                   102400  1 nouveau
cfg80211              581632  4 ath,ath9k_common,ath9k,mac80211
crc32_pclmul           16384  0 
ghash_clmulni_intel    16384  0 
ath3k                  16384  0 
drm_kms_helper        126976  2 i915,nouveau
btusb                  45056  0 
drm                   352256  8 ttm,i915,drm_kms_helper,nouveau
snd_timer              32768  2 snd_pcm,snd_seq
joydev                 20480  0 
serio_raw              16384  0 
shpchp                 40960  0 
bluetooth             524288  23 bnep,ath3k,btusb,rfcomm
i2c_algo_bit           16384  2 i915,nouveau
snd                    86016  17 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec_generic,snd_hda_codec,snd_hda_intel,snd_seq_device
soundcore              16384  2 snd,snd_hda_codec
lpc_ich                24576  0 
cryptd                 24576  1 ghash_clmulni_intel
mei_me                 20480  0 
mei                    90112  1 mei_me
video                  28672  2 i915,nouveau
mac_hid                16384  0 
wmi                    20480  2 mxm_wmi,nouveau
parport_pc             36864  0 
ppdev                  20480  0 
lp                     20480  0 
parport                45056  3 lp,ppdev,parport_pc
hid_logitech_dj        20480  0 
usbhid                 53248  0 
hid                   114688  3 usbhid,hid_logitech_dj,hid_logitech_hidpp
psmouse               126976  0 
ahci                   36864  4 
r8169                  90112  0 
libahci                32768  1 ahci
mii                    16384  1 r8169
             total       used       free     shared    buffers     cached
Mem:       8058676    1315108    6743568     482696      40248     778032
-/+ buffers/cache:     496828    7561848
Swap:     15625212          0   15625212
/usr/lib/pm-utils/sleep.d/00logging suspend suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/00powersave suspend suspend:
/usr/lib/pm-utils/sleep.d/00powersave suspend suspend: success.


Running hook /etc/pm/sleep.d/10_grub-common suspend suspend:
/etc/pm/sleep.d/10_grub-common suspend suspend: success.


Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend:
/etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/50unload_alx suspend suspend:
/usr/lib/pm-utils/sleep.d/50unload_alx suspend suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend:
Failed to connect to non-global ctrl_ifname: (null)  error: No such file or directory
/usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/75modules suspend suspend:
Unloading kernel module r8169...Done.
/usr/lib/pm-utils/sleep.d/75modules suspend suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/90clock suspend suspend:
/usr/lib/pm-utils/sleep.d/90clock suspend suspend: not applicable.


Running hook /usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend:
/usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/95anacron suspend suspend:
stop: Unknown instance: 
/usr/lib/pm-utils/sleep.d/95anacron suspend suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend:
/usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend: not applicable.


Running hook /usr/lib/pm-utils/sleep.d/95led suspend suspend:
/usr/lib/pm-utils/sleep.d/95led suspend suspend: not applicable.


Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend:
Kernel modesetting video driver detected, not using quirks.
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/99video suspend suspend:
kernel.acpi_video_flags = 0
/usr/lib/pm-utils/sleep.d/99video suspend suspend: success.


Running hook /etc/pm/sleep.d/novatel_3g_suspend suspend suspend:
/etc/pm/sleep.d/novatel_3g_suspend suspend suspend: success.


Fri Apr 17 15:23:26 EEST 2015: performing suspend
Fri Apr 17 15:23:44 EEST 2015: Awake.
Fri Apr 17 15:23:44 EEST 2015: Running hooks for resume
Running hook /etc/pm/sleep.d/novatel_3g_suspend resume suspend:
/etc/pm/sleep.d/novatel_3g_suspend resume suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/99video resume suspend:
/usr/lib/pm-utils/sleep.d/99video resume suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend:
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/95led resume suspend:
/usr/lib/pm-utils/sleep.d/95led resume suspend: not applicable.


Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm resume suspend:


/dev/sda:
 setting Advanced Power Management level to 0xfe (254)
 APM_level    = 254
/usr/lib/pm-utils/sleep.d/95hdparm-apm resume suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/95anacron resume suspend:
/usr/lib/pm-utils/sleep.d/95anacron resume suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/94cpufreq resume suspend:
/usr/lib/pm-utils/sleep.d/94cpufreq resume suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/90clock resume suspend:
/usr/lib/pm-utils/sleep.d/90clock resume suspend: not applicable.


Running hook /usr/lib/pm-utils/sleep.d/75modules resume suspend:
Reloaded unloaded modules.
/usr/lib/pm-utils/sleep.d/75modules resume suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant resume suspend:
Failed to connect to non-global ctrl_ifname: (null)  error: No such file or directory
/usr/lib/pm-utils/sleep.d/60_wpa_supplicant resume suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/50unload_alx resume suspend:
/usr/lib/pm-utils/sleep.d/50unload_alx resume suspend: success.


Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate resume suspend:
/etc/pm/sleep.d/10_unattended-upgrades-hibernate resume suspend: success.


Running hook /etc/pm/sleep.d/10_grub-common resume suspend:
/etc/pm/sleep.d/10_grub-common resume suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/00powersave resume suspend:
/usr/lib/pm-utils/sleep.d/00powersave resume suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/00logging resume suspend:
/usr/lib/pm-utils/sleep.d/00logging resume suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/000record-status resume suspend:
/usr/lib/pm-utils/sleep.d/000record-status resume suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/000kernel-change resume suspend:
/usr/lib/pm-utils/sleep.d/000kernel-change resume suspend: success.


Fri Apr 17 15:23:44 EEST 2015: Finished.

```

As you may have noticed already, I have installed the kernel v4.0 with the hope that this known problem would have been resolved but it doesn't seem so.

Any useful advice would be highly appreciated.

---

### Post by giokokos on 2015-04-20
Bump. Any help?

---

