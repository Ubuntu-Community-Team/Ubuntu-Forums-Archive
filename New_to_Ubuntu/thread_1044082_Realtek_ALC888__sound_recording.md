---
title: "Realtek ALC888  sound recording?"
date: 2009-01-19
forum: New to Ubuntu
---

### Post by candtalan on 2009-01-19
No sound recording - lots of things attempted and options used:
machine, new purchase,

HP Pavilion a6623uk on the external pack
amd athlon 4450e 

Ubuntu 8.04 and tried also with 8.10 live cd
======================
 lspci
00:00.0 RAM memory: nVidia Corporation MCP61 Memory Controller (rev a1)
00:01.0 ISA bridge: nVidia Corporation MCP61 LPC Bridge (rev a2)
00:01.1 SMBus: nVidia Corporation MCP61 SMBus (rev a2)
00:01.2 RAM memory: nVidia Corporation MCP61 Memory Controller (rev a2)
00:02.0 USB Controller: nVidia Corporation MCP61 USB Controller (rev a3)
00:02.1 USB Controller: nVidia Corporation MCP61 USB Controller (rev a3)
00:04.0 PCI bridge: nVidia Corporation MCP61 PCI bridge (rev a1)
00:05.0 Audio device: nVidia Corporation MCP61 High Definition Audio (rev a2)
00:06.0 IDE interface: nVidia Corporation MCP61 IDE (rev a2)
00:07.0 Bridge: nVidia Corporation MCP61 Ethernet (rev a2)
00:08.0 IDE interface: nVidia Corporation MCP61 SATA Controller (rev a2)
00:08.1 IDE interface: nVidia Corporation MCP61 SATA Controller (rev a2)
00:09.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
00:0b.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
00:0c.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 FireWire (IEEE 1394): Agere Systems FW323 (rev 70)
02:00.0 VGA compatible controller: ATI Technologies Inc Mobilitiy Radeon HD 3450

======================

Audio sound and replay works ok however, recording does not, either using audacity or the ubuntu included sound recorder.

Opening the volume control and also using alsa mixer (installed later) and apparently trying all combinations of capture and recording settings choices, - results in no recording.

The information from the mixer and from audacity reports about
HDA NVidia Realtek ALC888 which I guess is the sound chip on the mainboard

It seems to me that the driver for the chip is somehow limited in the facility of sound capture.
This is a new PC that a friend has purchased, and wanted me to put ubuntu on it, which I have done.
This means I will not be able to follow up any solutions notr probably do a good bug report, I will not have access to the PC.

The friend in very non techie and is just about to take the PC back from me to go home.


Comments will be most welcomed.

---

### Post by chaos51 on 2009-01-29
Hi 
I don't know if this will help but it helped me.
When you go into the Gnome Volume Control with your Device selected do you have a tab that says "Options"?  If you don't then select the Preferences button and check the boxes for Input source: Options.

The in the options tab you should be able to select what input source the capture  volume control slider controls.

In my case I had the HDA Intel (Alsa mixer) defaults taking capture input from the mic (and not line-in). In the preferences of the HDA Intel I added checkmarks for the Input Source: Options and then in the Options tab I was able to select "Line"

I have a RealTek ALC888 device and setting the Options in the HDA Intel(Alsa Mixer) device fixed it so that I could capture audio from my line input.

---

### Post by Truefire on 2009-01-29
I agree with chaos51. Audio is usually a GUI setting, nothing commandlindish.

---

### Post by FunkyFrank on 2009-04-23
Yes! Chaos51, this was spot on for me. It was under options, line was selected. Beauty!!

Cheers
Frank

---

