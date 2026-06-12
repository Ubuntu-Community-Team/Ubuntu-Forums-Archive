---
title: "no sound from speakers, but heaphones work"
date: 2009-08-17
forum: New to Ubuntu
---

### Post by madurst on 2009-08-17
Hello all, Im new to Ubuntu and slowly getting everything to work. My speakers do not work, but when i plug in headphones those do. The sound control through alsamixer does not do anything and i have to change the volume/mute withing the flash player (for youtube vidoes). 
in alsa mixer, the volume up/down/mute buttons work to change the volume correctly.

Gateway MX7527
aplay-l=
**** List of PLAYBACK Hardware Devices ****
card 0: IXP [ATI IXP], device 0: ATI IXP AC97 [ATI IXP AC97]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: Modem [ATI IXP Modem], device 0: ATI IXP MC97 [ATI IXP MC97]
  Subdevices: 0/1
  Subdevice #0: subdevice #0

lspci=
00:00.0 Host bridge: ATI Technologies Inc RS480 Host Bridge (rev 01)
00:02.0 PCI bridge: ATI Technologies Inc RS480 PCI-X Root Port
00:06.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller
00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller
00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller
00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 11)
00:14.1 IDE interface: ATI Technologies Inc IXP SB400 IDE Controller
00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge
00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge
00:14.5 Multimedia audio controller: ATI Technologies Inc IXP SB400 AC'97 Audio Controller (rev 02)
00:14.6 Modem: ATI Technologies Inc SB400 AC'97 Modem Controller (rev 02)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 VGA compatible controller: ATI Technologies Inc M24 1P [Radeon Mobility X600]
02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8036 PCI-E Fast Ethernet Controller (rev 10)
03:05.0 CardBus bridge: ENE Technology Inc CB1410 Cardbus Controller (rev 01)
03:07.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
03:0e.0 FireWire (IEEE 1394): VIA Technologies, Inc. VT6306 Fire II IEEE 1394 OHCI Link Layer Controller (rev 80)

any other information needed just tell me how to get it. Thanks for your help!

Matt

---

### Post by kambrik on 2009-08-17
Try using the alsamixer at the terminal and make sure that the speakers are not muted/disabled.

---

### Post by madurst on 2009-08-17
alsamixer not muted:
Card: ATI IXP
Chip: Conexant id 30
View: [Playback] Capture  All
Item: Master [dB gain=0.00, 0.00] 

It properly goes up and down wiht the sound up and down buttons on the computer and properly mutes when the mute button is pressed. but this just doesnt control the sound output for some reason...

under the alsa mixer i have the following columns:
Master; headphon; PCM; line; CD; Mic; Mic Boos; IEC958, IEC 958 P; PC Speakl; External

everything is unmuted and at 100% that can be

---

### Post by madurst on 2009-08-17
Just solved it... had the test running in sound preferences... and then was playing around in alsamixer... the external line in alsamixer was not muted and i got no sound... when i muted the external bar in alsamixer the sound came up on my speakers:P.. thanks for your help

---

