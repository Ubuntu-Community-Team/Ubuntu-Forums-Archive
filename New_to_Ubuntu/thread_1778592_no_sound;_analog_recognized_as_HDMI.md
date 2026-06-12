---
title: "no sound; analog recognized as HDMI"
date: 2011-06-09
forum: New to Ubuntu
---

### Post by darkzavulon on 2011-06-09
Hello everyone.
By some reason my ubuntu thinks, that I'm using HDMI connection with my sound card.
My sound card doesn't even have HDMI out (using onboard Creative Sound Blaster Audigy SE CA0106 - motherboard MSI K9N Diamond).
Alsamixer's soundcard list consists only of HDA Nvidia.

I've reinstalled alsa package and still have no sound at all.
How do I fix it?

---

### Post by jtarin on 2011-06-09
Let's see if we can determine if you have the correct driver loaded. Could you post the output of these two commands.
```
lspci
```
```
lsmod
```

---

### Post by darkzavulon on 2011-06-09
lspci
```
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
00:08.0 RAM memory: nVidia Corporation MCP55 Memory Controller (rev a1)
00:09.0 ISA bridge: nVidia Corporation MCP55 LPC Bridge (rev a2)
00:09.1 SMBus: nVidia Corporation MCP55 SMBus (rev a2)
00:0a.0 USB Controller: nVidia Corporation MCP55 USB Controller (rev a1)
00:0a.1 USB Controller: nVidia Corporation MCP55 USB Controller (rev a2)
00:0c.0 IDE interface: nVidia Corporation MCP55 IDE (rev a1)
00:0d.0 IDE interface: nVidia Corporation MCP55 SATA Controller (rev a2)
00:0d.1 IDE interface: nVidia Corporation MCP55 SATA Controller (rev a2)
00:0d.2 IDE interface: nVidia Corporation MCP55 SATA Controller (rev a2)
00:0e.0 PCI bridge: nVidia Corporation MCP55 PCI bridge (rev a2)
00:10.0 Bridge: nVidia Corporation MCP55 Ethernet (rev a2)
00:11.0 Bridge: nVidia Corporation MCP55 Ethernet (rev a2)
00:12.0 PCI bridge: nVidia Corporation MCP55 PCI Express bridge (rev a2)
00:13.0 PCI bridge: nVidia Corporation MCP55 PCI Express bridge (rev a2)
00:14.0 PCI bridge: nVidia Corporation MCP55 PCI Express bridge (rev a2)
00:15.0 PCI bridge: nVidia Corporation MCP55 PCI Express bridge (rev a2)
00:16.0 PCI bridge: nVidia Corporation MCP55 PCI Express bridge (rev a2)
00:17.0 PCI bridge: nVidia Corporation MCP55 PCI Express bridge (rev a2)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
0a:00.0 VGA compatible controller: nVidia Corporation GT218 [GeForce 210] (rev a2)
0a:00.1 Audio device: nVidia Corporation High Definition Audio Controller (rev a1)
```lsmod
```
Module                  Size  Used by
snd_seq_dummy          12686  0 
ipt_MASQUERADE         12663  1 
iptable_nat            12977  1 
nf_nat                 24827  2 ipt_MASQUERADE,iptable_nat
nf_conntrack_ipv4      19024  3 iptable_nat,nf_nat
nf_conntrack           69744  4 ipt_MASQUERADE,iptable_nat,nf_nat,nf_conntrack_ipv4
nf_defrag_ipv4         12649  1 nf_conntrack_ipv4
iptable_filter         12706  0 
ip_tables              18125  2 iptable_nat,iptable_filter
x_tables               21907  4 ipt_MASQUERADE,iptable_nat,iptable_filter,ip_tables
binfmt_misc            13213  1 
parport_pc             32111  0 
ppdev                  12849  0 
vesafb                 13449  1 
snd_hda_codec_hdmi     27479  4 
nvidia               9766978  40 
snd_hda_intel          24140  0 
snd_hda_codec          90901  2 snd_hda_codec_hdmi,snd_hda_intel
snd_hwdep              13274  1 snd_hda_codec
snd_pcm                80244  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
snd_rawmidi            25269  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51291  3 snd_seq_dummy,snd_seq_midi,snd_seq_midi_event
snd_timer              28659  2 snd_pcm,snd_seq
snd_seq_device         14110  4 snd_seq_dummy,snd_seq_midi,snd_rawmidi,snd_seq
snd                    55295  9 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              12600  1 snd
nv_tco                 13331  0 
psmouse                73312  0 
lp                     13349  0 
snd_page_alloc         14073  2 snd_hda_intel,snd_pcm
serio_raw              12990  0 
joydev                 17322  0 
i2c_nforce2            12906  0 
k8temp                 12872  0 
parport                36746  3 parport_pc,ppdev,lp
usbhid                 41704  0 
hid                    77084  1 usbhid
usb_storage            43946  0 
uas                    17676  0 
floppy                 60032  0 
sata_nv                23176  0 
pata_amd               13762  3 
forcedeth              58190  0
```

---

### Post by jtarin on 2011-06-09
How do you know you have the Creative Sound Blaster Audigy SE CA0106 chip?
According to ALSA you should have these modules loaded for that chip:```
snd-ca0106 ; snd-pcm-oss ;  snd-mixer-oss ; snd-seq-oss
```Do you have two cards/chips for sound? If yes then you might see which one is activated in the "bios". If not we'll go another route.

---

### Post by darkzavulon on 2011-06-09
> How do you know you have the Creative Sound Blaster Audigy SE CA0106 chip?
Thats what my motherboard's user guide says. 
And it is the only audio chip installed.

---

### Post by jtarin on 2011-06-09
Then in a terminal issue the command "modprobe snd-ca0106" and then post "lsmod" again.

---

### Post by darkzavulon on 2011-06-09
I found the reason. After you said about chipset activated in bios, I thought it won't be odd to go and check it.
And yes, my onboard audio was somehow set to "Disabled".
Thanks a lot.:)

---

### Post by jtarin on 2011-06-09
Good! If that fixed it, would you mark the thread as solved.

---

