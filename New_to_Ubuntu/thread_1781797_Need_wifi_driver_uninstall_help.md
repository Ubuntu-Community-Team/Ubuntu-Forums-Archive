---
title: "Need wifi driver uninstall help"
date: 2011-06-14
forum: New to Ubuntu
---

### Post by Crimzonblade on 2011-06-14
Hello everyone, I installed Ubuntu 10.10, kernal 2.6.38.8-generic a few days ago and I'm trying to learn all the ins and outs. I installed the Linksy AE1000 wireless adapter driver, 2010_0915_RT3572_Linux_STA_v2.4.0.2.tar.bz2., from [http://www.ralinktech.com/support.php?s=2](http://www.ralinktech.com/support.php?s=2), and now I need to uninstall it. I've tried Ubuntu Software Center and Synaptic Package Manager and had no success. I don't know what was specifically compiled and installed so I'm lost. Anyone have any ideas how to help me?

---

### Post by jtarin on 2011-06-14
_**From man modprobe:**_

```
modprobe -r <nameofmodule>
```

This option causes modprobe to remove, rather than insert a module.   If  the  modules  it depends on are also unused, modprobe will try to remove them, too.  Unlike insertion, more  than  one module  can  be  specified on the command line (it does not make sense to specify module parameters when removing modules). There is usually no reason to remove  modules,  but  some  buggy modules require it.  Your kernel may not support removal of modules.

---

### Post by Crimzonblade on 2011-06-14
Thank you very much for the quick reply and the explanation for the code! Bear with me, I have to boot back and forth between Windows and Ubuntu. My problem is I don't know the name of the package that was installed for my wifi adapter. I tried modprobe -r with the names of the files in my driver folder which were: RT3572USB, 2011_0427_RT3572_Linux_STA_v2.5.0.0.DPO, RT2870STACard.dat, and RT2870STA.dat. I don't even know what extention to look for.

---

### Post by Crimzonblade on 2011-06-14
I also tried 2010_0915_RT3572_Linux_STA_v2.4.0.2.tar.bz2 just now but all my tries get 'File not found'.

---

### Post by Crimzonblade on 2011-06-14
I'm sorry, the driver I installed was 2011_0427_RT3572_Linux_STA_v2.5.0.0.DPO, not 2010_0915_RT3572_Linux_STA_v2.4.0.2.tar.bz2.

---

### Post by jtarin on 2011-06-14
I want you to run two commands for me...separately.

```
lspci
```and ```
lsmod
```

---

### Post by jtarin on 2011-06-14
To find files better use the command "locate <filename>", but first you have to update the database before you run it, so the first command will be ```
sudo updatedb
``` then when it has returned to the prompt run the command ```
locate <filename>
```.

---

### Post by Crimzonblade on 2011-06-14
lspci: 00:00.0 RAM memory: nVidia Corporation MCP78S [GeForce 8200] Memory Controller (rev a2) 00:01.0 ISA bridge: nVidia Corporation MCP78S [GeForce 8200] LPC Bridge (rev a2) 00:01.1 SMBus: nVidia Corporation MCP78S [GeForce 8200] SMBus (rev a1) 00:01.2 RAM memory: nVidia Corporation MCP78S [GeForce 8200] Memory Controller (rev a1) 00:01.3 Co-processor: nVidia Corporation MCP78S [GeForce 8200] Co-Processor (rev a2) 00:01.4 RAM memory: nVidia Corporation MCP78S [GeForce 8200] Memory Controller (rev a1) 00:02.0 USB Controller: nVidia Corporation MCP78S [GeForce 8200] OHCI USB 1.1 Controller (rev a1) 00:02.1 USB Controller: nVidia Corporation MCP78S [GeForce 8200] EHCI USB 2.0 Controller (rev a1) 00:04.0 USB Controller: nVidia Corporation MCP78S [GeForce 8200] OHCI USB 1.1 Controller (rev a1) 00:04.1 USB Controller: nVidia Corporation MCP78S [GeForce 8200] EHCI USB 2.0 Controller (rev a1) 00:06.0 IDE interface: nVidia Corporation MCP78S [GeForce 8200] IDE (rev a1) 00:07.0 Audio device: nVidia Corporation MCP72XE/MCP72P/MCP78U/MCP78S High Definition Audio (rev a1) 00:08.0 PCI bridge: nVidia Corporation MCP78S [GeForce 8200] PCI Bridge (rev a1) 00:09.0 IDE interface: nVidia Corporation MCP78S [GeForce 8200] SATA Controller (non-AHCI mode) (rev a2) 00:0a.0 Ethernet controller: nVidia Corporation MCP77 Ethernet (rev a2) 00:10.0 PCI bridge: nVidia Corporation MCP78S [GeForce 8200] PCI Express Bridge (rev a1) 00:12.0 PCI bridge: nVidia Corporation MCP78S [GeForce 8200] PCI Express Bridge (rev a1) 00:13.0 PCI bridge: nVidia Corporation MCP78S [GeForce 8200] PCI Bridge (rev a1) 00:14.0 PCI bridge: nVidia Corporation MCP78S [GeForce 8200] PCI Bridge (rev a1) 00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor HyperTransport Configuration 00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Address Map 00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor DRAM Controller 00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Miscellaneous Control 00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Link Control 01:06.0 Multimedia audio controller: Creative Labs CA0106 Soundblaster 02:00.0 VGA compatible controller: nVidia Corporation G92 [GeForce 9600 GSO] (rev a2)  lsmod: Module                  Size  Used by parport_pc             32111  0  ppdev                  12849  0  binfmt_misc            13213  1  snd_hda_codec_realtek   255820  1  rt3572sta             593116  1  snd_hda_intel          24140  2  snd_hda_codec          90901  2 snd_hda_codec_realtek,snd_hda_intel snd_hwdep              13274  1 snd_hda_codec snd_ca0106             39319  2  snd_ac97_codec        105614  1 snd_ca0106 ac97_bus               12642  1 snd_ac97_codec snd_pcm                80244  4 snd_hda_intel,snd_hda_codec,snd_ca0106,snd_ac97_codec nouveau               621970  2  snd_seq_midi           13132  0  snd_rawmidi            25269  2 snd_ca0106,snd_seq_midi snd_seq_midi_event     14475  1 snd_seq_midi ttm                    65184  1 nouveau snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event drm_kms_helper         40745  1 nouveau joydev                 17322  0  snd_timer              28659  2 snd_pcm,snd_seq snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq drm                   180037  4 nouveau,ttm,drm_kms_helper i2c_algo_bit           13184  1 nouveau k10temp                12951  0  video                  18951  1 nouveau snd                    55295  19 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_ca0106,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device psmouse                73312  0  serio_raw              12990  0  soundcore              12600  1 snd snd_page_alloc         14073  3 snd_hda_intel,snd_ca0106,snd_pcm i2c_nforce2            12906  0  lp                     13349  0  parport                36746  3 parport_pc,ppdev,lp hid_microsoft          12745  0  usbhid                 41704  0  hid                    77084  2 hid_microsoft,usbhid floppy                 60032  0  ahci                   21591  0  pata_amd               13762  3  forcedeth              58190  0  libahci                25548  1 ahci

---

### Post by jtarin on 2011-06-14
When replying with code from the terminal use the "#" (pound sign to bracket your code.Each command should be bracketed. You will see it in the menu of the reply box.I can't help you ,trying to read it as you have posted. Delete what you have posted above and post it correctly , please.

---

### Post by jtarin on 2011-06-14
I forgot....yours is a USB so delete the ```
lspci
``` one and let me see ```
lusb
```

---

### Post by Crimzonblade on 2011-06-14
I'm assuming from the 'lsmod' results that I'll be looking for 'rt3572sta'...brb after I do 'code: locate rt3572sta'.

---

### Post by jtarin on 2011-06-14
Something of that nature.....but couldn't say 100% until I see those two commands.

---

### Post by 3rdalbum on 2011-06-14
```
sudo modprobe -r rt3572sta
```

There should be instructions in the archive you downloaded, for inserting and removing the module...

I've noticed that Ubuntu 11.04 has better support for the later RT chipsets, you might benefit from trying the latest version of Ubuntu. You might not even need to install a driver. With my card I had to blacklist another module on Ubuntu 10.10 to get the built-in driver to work; with Ubuntu 11.04 the correct driver loads out-of-the-box.

---

### Post by Crimzonblade on 2011-06-14
Excellent idea jtarin! rather than edit my output from lsmod and lspci, I'm going to install Ubuntu 11.04. I copied and pasted all your instructions and learned quite a bit in a short amount of time! Thank you so very much for all your time pardner!! I hope to talk with you again sometime. Take it easy my friend.

---

### Post by Crimzonblade on 2011-06-14
Oops, thank you both and I'll take your advice 13rdalbum.

---

