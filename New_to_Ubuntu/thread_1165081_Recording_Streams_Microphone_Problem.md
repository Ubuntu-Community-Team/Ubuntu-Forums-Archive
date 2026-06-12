---
title: "Recording Streams Microphone Problem"
date: 2009-05-20
forum: New to Ubuntu
---

### Post by tommo12 on 2009-05-20
This a deal breaker for me with linux. Hopefully I can fix it.

I ve been trying to get my ALC 888 HD ATI sound card, Recording (Mic) working in my laptop. Everything else works except the Recording from the Microphones plugged in and inbuilt, and the headphone switch does not work. 
I had the sound recording working at two stages. Firstly before I installed Gstreamer... strange
Secondly I installed Padevchooser package (Pulse A.. Device Chooser) after reading a manual on how to set up the sound, which basicalled said install pulse gear and use that instead of the default volume control prgram (or atleast use it beside it) What I did exactly was the padevchooser program allowed me to change the streams in the recording program. 

The Microphones work in "playback" so I can hear nose from them coming out of my speakers. But the capture does not work, hence the switching the streams allowed them to work.

Is there a program using Alsa that allows you to switch streams? Any other ideas :)

Cheers

---

### Post by tommo12 on 2009-05-20
into terminal
lspci
= 

00:00.0 Host bridge: Advanced Micro Devices [AMD] RS780 Host Bridge
00:02.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (ext gfx port 0)
00:04.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 0)
00:05.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 1)
00:11.0 SATA controller: ATI Technologies Inc SB700/SB800 SATA Controller [AHCI mode]
00:12.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:12.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller
00:12.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:13.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:13.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 3a)
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
00:14.3 ISA bridge: ATI Technologies Inc SB700/SB800 LPC host controller
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 11h HyperTransport Configuration (rev 40)
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 11h Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 11h DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 11h Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 11h Link Control
02:00.0 VGA compatible controller: ATI Technologies Inc M92 [Mobility Radeon HD 4500 Series]
02:00.1 Audio device: ATI Technologies Inc R700 Audio Device [Radeon HD 4000 Series]
03:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5784M Gigabit Ethernet PCIe (rev 10)
06:00.0 Network controller: Atheros Communications Inc. AR928X Wireless Network Adapter (PCI-Express) (rev 01)

---

### Post by tommo12 on 2009-05-20
_[COLOR=Lime]**Any ideas pee**[/COLOR]_[U][COLOR=Lime][B]ps :)
[/B][/COLOR][/U]_[COLOR=Lime]**[IMG]http://www.platteville.org/Portals/31/2008/Admin/Pictures/cow-smiling.jpg[/IMG]**[/COLOR]_
[COLOR=Red]Love the Cow![/COLOR]

---

### Post by tommo12 on 2009-05-20
ppls?

---

### Post by BandD on 2009-05-23
I'm not familiar with card. I do know that ATI rolls out linux drivers to some extent.  Do you know if you are using ati's driver or the open source driver?

When you got to Preferences--> Sound...what do you have in the box that says "Sound Capture"?  Try out different options there.

Also, many people with audio problems seem to have luck by simply removing pulse (you can always reinstall).

---

### Post by tommo12 on 2009-05-25
I have found out the problem is that recording is just plain dodgy. It works when i restart my computer, but if I have more than one recording stream or guitar tuner input device open at once it just dies. Same if I have Rhythm box open then open recorder it just dies... What Packages should I take out to get rid of Pulse Audio?

---

