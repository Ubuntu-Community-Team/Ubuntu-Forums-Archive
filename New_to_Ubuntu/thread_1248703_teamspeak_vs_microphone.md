---
title: "teamspeak vs microphone"
date: 2009-08-24
forum: New to Ubuntu
---

### Post by taith on 2009-08-24
hey everyone

small problem here... i have a mic on my computer... and the teamspeak server running... now i can hear myself through the speakers, but nobody else can hear me atall...

any idea why?

---

### Post by LowSky on 2009-08-24
dont know, we need more info.

Could you suppply your computer specs, including what type of microphone, the chipset to your sound card would be great. if you dont know then please enter this command into a terminal and paste the results here

```
lspci
```

---

### Post by taith on 2009-08-24
> taith@craig:~$ lspci
00:00.0 Host bridge: ATI Technologies Inc RX780/RX790 Chipset Host Bridge
00:02.0 PCI bridge: ATI Technologies Inc RD790 PCI to PCI bridge (external gfx0 port A)
00:06.0 PCI bridge: ATI Technologies Inc RD790 PCI to PCI bridge (PCI express gpp port C)
00:12.0 SATA controller: ATI Technologies Inc SB600 Non-Raid-5 SATA
00:13.0 USB Controller: ATI Technologies Inc SB600 USB (OHCI0)
00:13.1 USB Controller: ATI Technologies Inc SB600 USB (OHCI1)
00:13.2 USB Controller: ATI Technologies Inc SB600 USB (OHCI2)
00:13.3 USB Controller: ATI Technologies Inc SB600 USB (OHCI3)
00:13.4 USB Controller: ATI Technologies Inc SB600 USB (OHCI4)
00:13.5 USB Controller: ATI Technologies Inc SB600 USB Controller (EHCI)
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 14)
00:14.1 IDE interface: ATI Technologies Inc SB600 IDE
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
00:14.3 ISA bridge: ATI Technologies Inc SB600 PCI to LPC Bridge
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 VGA compatible controller: nVidia Corporation GeForce 9800 GT (rev a2)
02:00.0 Ethernet controller: Attansic Technology Corp. L1 Gigabit Ethernet Adapter (rev b0)
03:05.0 Multimedia video controller: Conexant Systems, Inc. CX23880/1/2/3 PCI Video and Audio Decoder (rev 05)
03:07.0 Ethernet controller: VIA Technologies, Inc. VT6105/VT6106S [Rhine-III] (rev 86)

and the mic is a logitech headset...

i also hear alot of static when i enable the mic(and boost) in the volumn controls...

---

### Post by Desktop_n00b on 2009-08-24
is there a selection in the preferences of teamspeak where you can choose to push a button to talk or where it automatically starts playing when the sound gets to a certain volume?

---

### Post by taith on 2009-08-24
true, but even if i [push to talk], nobody can hear me... tho i can hear myself perfectly well...

---

### Post by dlmarti on 2009-08-24
> **taith said:**
> true, but even if i [push to talk], nobody can hear me... tho i can hear myself perfectly well...

Thats because you have the mic turned on under the playback options for the "volume control", and the mic muted under record.

Rather than trying to debug this under teamspeak, use one of the built in mic recorder applications first.

---

### Post by LowSky on 2009-08-24
> **dlmarti said:**
> Thats because you have the mic turned on under the playback options for the "volume control", and the mic muted under record.

Rather than trying to debug this under teamspeak, use one of the built in mic recorder applications first.

Actually it could be teamspeak,, skype has a similar issue, got to the preferences or settings menu in teamspeak, and for mic input change it to another option and save it, then close teamspeak and then reopen. might work... it isn't a driver issue.

---

