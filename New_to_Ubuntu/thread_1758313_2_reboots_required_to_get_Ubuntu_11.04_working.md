---
title: "2 reboots required to get Ubuntu 11.04 working"
date: 2011-05-14
forum: New to Ubuntu
---

### Post by maciej234 on 2011-05-14
Ububtu/Kubuntu need 2 reboots to load.  The first boot is a black screen with a a colored strip on the left edge the lcd/ no graphics.  Occacionally grub will load but still needs restart.  Second boot loads kubuntu normally.  Please help me figure out how i can fix the problem; this is on a new intel 2nd gen processor i5 with Intel HD 3000 graphics, and occurs only on this laptop.

---

### Post by P&amp;N on 2011-06-16
Hey, have u verified that unity-2d is installed and running? I had a similar problem and installing unity-2d solved it. 

Note! this may help with the graphics, but not the shutdown problems.

---

### Post by maciej234 on 2011-06-27
also happens on kubuntu 11.04.  First boot is either a black screen or pinstripes, second boot shows graphics and boots normal

---

### Post by jtarin on 2011-06-27
Next time on the desktop open a terminal and issue the command ```
lspci
``` and the ```
lsmod
```......post the results of both.

---

### Post by maciej234 on 2011-07-08
ThinkPad:~$ lspci
00:00.0 Host bridge: Intel Corporation 2nd Generation Core Processor Family DRAM Controller (rev 09)
00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)
00:16.0 Communication controller: Intel Corporation 6 Series Chipset Family MEI Controller #1 (rev 04)
00:1a.0 USB Controller: Intel Corporation 6 Series Chipset Family USB Enhanced Host Controller #2 (rev 04)
00:1b.0 Audio device: Intel Corporation 6 Series Chipset Family High Definition Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation 6 Series Chipset Family PCI Express Root Port 1 (rev b4)
00:1c.1 PCI bridge: Intel Corporation 6 Series Chipset Family PCI Express Root Port 2 (rev b4)
00:1c.2 PCI bridge: Intel Corporation 6 Series Chipset Family PCI Express Root Port 3 (rev b4)
00:1c.3 PCI bridge: Intel Corporation 6 Series Chipset Family PCI Express Root Port 4 (rev b4)
00:1c.4 PCI bridge: Intel Corporation 6 Series Chipset Family PCI Express Root Port 5 (rev b4)
00:1c.5 PCI bridge: Intel Corporation 6 Series Chipset Family PCI Express Root Port 6 (rev b4)
00:1d.0 USB Controller: Intel Corporation 6 Series Chipset Family USB Enhanced Host Controller #1 (rev 04)
00:1f.0 ISA bridge: Intel Corporation HM65 Express Chipset Family LPC Controller (rev 04)
00:1f.2 SATA controller: Intel Corporation 6 Series Chipset Family 6 port SATA AHCI Controller (rev 04)
00:1f.3 SMBus: Intel Corporation 6 Series Chipset Family SMBus Controller (rev 04)
03:00.0 Network controller: Realtek Semiconductor Co., Ltd. RTL8188CE 802.11b/g/n WiFi Adapter (rev 01)
04:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. Device 5209 (rev 01)
09:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 03)

---

### Post by maciej234 on 2011-07-08
ThinkPad:~$ lsmod
Module                  Size  Used by
parport_pc             32111  0 
ppdev                  12849  0 
dm_crypt               22463  0 
snd_hda_codec_hdmi     27479  1 
snd_hda_codec_realtek   255820  1 
snd_hda_intel          24140  3 
joydev                 17322  0 
snd_hda_codec          90901  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13274  1 snd_hda_codec
snd_pcm                80244  4 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
thinkpad_acpi          73750  0 
snd_seq_midi           13132  0 
snd_rawmidi            25269  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
psmouse                59039  0 
snd_timer              28659  2 snd_pcm,snd_seq
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
arc4                   12473  2 
snd                    55295  16 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,thinkpad_acpi,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
tpm_tis                18089  0 
tpm                    21251  1 tpm_tis
tpm_bios               13460  1 tpm
rtl8192ce             120897  0 
rtlwifi                78961  1 rtl8192ce
serio_raw              12990  0 
lp                     13349  0 
nvram                  14035  1 thinkpad_acpi
rts_pstor             348243  0 
soundcore              12600  1 snd
parport                36746  3 parport_pc,ppdev,lp
snd_page_alloc         14073  2 snd_hda_intel,snd_pcm
mac80211              257001  2 rtl8192ce,rtlwifi
cfg80211              156212  2 rtlwifi,mac80211
i915                  450979  3 
drm_kms_helper         40745  1 i915
drm                   184133  4 i915,drm_kms_helper
r8169                  46630  0 
ahci                   21591  2 
libahci                25548  1 ahci
i2c_algo_bit           13184  1 i915
video                  18951  1 i915

---

### Post by maciej234 on 2011-07-08
> **P&N said:**
> Hey, have u verified that unity-2d is installed and running? I had a similar problem and installing unity-2d solved it. 

Note! this may help with the graphics, but not the shutdown problems.


I'm using KDE and still have the issue not using gnome.  This is related to Ubuntu 11.04 because on Fedora 15 KDE no issues

---

### Post by maciej234 on 2011-07-24
Does anyone know the bug thats happening here?  I assume its just the new hardware (intel hd 3000 graphics).  I can record a youtube video.  But the striped screen, and multiple reboots still required on 11.04 running unity with all the updates (no backports).  On Fedora 15/opensuse boots on first boot , but ubuntu no.

---

