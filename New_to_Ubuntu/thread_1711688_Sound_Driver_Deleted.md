---
title: "Sound Driver Deleted??"
date: 2011-03-21
forum: New to Ubuntu
---

### Post by aashishkotagiri on 2011-03-21
Can Some One fix this problem.....

every thing looks fine but i think some one deleted the sound driver files...

this is a public system...

 lspci
00:00.0 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.1 RAM memory: nVidia Corporation C51 Memory Controller 0 (rev a2)
00:00.2 RAM memory: nVidia Corporation C51 Memory Controller 1 (rev a2)
00:00.3 RAM memory: nVidia Corporation C51 Memory Controller 5 (rev a2)
00:00.4 RAM memory: nVidia Corporation C51 Memory Controller 4 (rev a2)
00:00.5 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.6 RAM memory: nVidia Corporation C51 Memory Controller 3 (rev a2)
00:00.7 RAM memory: nVidia Corporation C51 Memory Controller 2 (rev a2)
00:02.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:03.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:04.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:05.0 VGA compatible controller: nVidia Corporation C51 [GeForce 6150 LE] (rev a2)
00:09.0 RAM memory: nVidia Corporation MCP51 Host Bridge (rev a2)
00:0a.0 ISA bridge: nVidia Corporation MCP51 LPC Bridge (rev a3)
00:0a.1 SMBus: nVidia Corporation MCP51 SMBus (rev a3)
00:0a.2 RAM memory: nVidia Corporation MCP51 Memory Controller 0 (rev a3)
00:0b.0 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0b.1 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0e.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev a1)
00:0f.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev a1)
00:10.0 PCI bridge: nVidia Corporation MCP51 PCI Bridge (rev a2)
00:10.1 Audio device: nVidia Corporation MCP51 High Definition Audio (rev a2)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
02:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5754 Gigabit Ethernet PCI Express (rev 02)
root@# lsmod
Module                  Size  Used by
vmnet                  47470  15 
vmblock                12995  1 
vsock                  43307  0 
vmci                   60422  1 vsock
vmmon                  80151  6 
binfmt_misc             7984  1 
snd_hda_codec_idt      64699  1 
snd_hda_intel          26147  3 
snd_hda_codec         100951  2 snd_hda_codec_idt,snd_hda_intel
snd_hwdep               6660  1 snd_hda_codec
snd_pcm                89104  3 snd_hda_intel,snd_hda_codec
nvidia              10221046  42 
snd_seq_midi            5932  0 
snd_rawmidi            22207  1 snd_seq_midi
snd_seq_midi_event      7291  1 snd_seq_midi
i2c_nforce2             6155  0 
snd_seq                57512  2 snd_seq_midi,snd_seq_midi_event
lp                     10201  0 
ppdev                   6804  0 
k8temp                  4128  0 
serio_raw               4910  0 
edac_core              46822  0 
edac_mce_amd            9387  0 
snd_timer              23850  2 snd_pcm,snd_seq
parport_pc             30086  1 
snd_seq_device          6912  3 snd_seq_midi,snd_rawmidi,snd_seq
parport                37032  3 ppdev,lp,parport_pc
snd                    64181  14 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               1240  1 snd
snd_page_alloc          8588  2 snd_hda_intel,snd_pcm
dcdbas                  6910  0 
usbhid                 42030  0 
hid                    84710  1 usbhid
tg3                   135768  0 
sata_nv                23770  2 
root@# amixer
Simple mixer control 'Master',0
  Capabilities: pvolume pswitch penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 31 [100%] [0.00dB] [on]
  Front Right: Playback 31 [100%] [0.00dB] [on]
Simple mixer control 'PCM',0
  Capabilities: pvolume penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 255
  Mono:
  Front Left: Playback 255 [100%] [0.00dB]
  Front Right: Playback 255 [100%] [0.00dB]
Simple mixer control 'Capture',0
  Capabilities: cvolume cswitch penum
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 15
  Front Left: Capture 15 [100%] [22.50dB] [off]
  Front Right: Capture 15 [100%] [22.50dB] [off]
Simple mixer control 'Input Source',0
  Capabilities: cenum
  Items: 'Mic' 'Line'
  Item0: 'Mic'
Simple mixer control 'Mux',0
  Capabilities: cvolume penum
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 4
  Front Left: Capture 4 [100%] [40.00dB]
  Front Right: Capture 4 [100%] [40.00dB]

---

### Post by cariboo on 2011-03-23
It looks like all your sound drivers are  there. You'll have look elsewhere for your problem. Have you check alsamixer to see if qll the volume levels are turned up?

Open a terminal and type:

```
alsamixer
```

use the arrow keys to navigate and turn the levels up and down, once you have set the levels to where you like, press esc to exit, and then type:

```
sudo alsactl store 
```

---

### Post by aashishkotagiri on 2011-03-24
I actually reinstalled all the packages which sounded like "ALSA" and the sound is working fine now..

thanks for the reply..

---

