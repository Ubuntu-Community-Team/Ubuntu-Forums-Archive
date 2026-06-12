---
title: "No sound on Toshiba satellite a105..."
date: 2011-05-26
forum: New to Ubuntu
---

### Post by JulioGee on 2011-05-26
Ive been trying to fix this darn thing for what seems like days now.
i have a toshiba satellite a105 running ubuntu 11.04.
runs awesome, just one problem.
my sound doesnt work.
i know it has to do with the sound card, 
i guess they dont support toshiba but ive been looking around on the internet
and i know that there is a way to do it.

PLEASEEEEEEEEEEE...
some one help me figure out how to fix this:(

---

### Post by James Keating on 2011-10-28
I had the same problem, and for me the solution was surprisingly simple. The correct module was present, but turned off. I am using Lubuntu, which uses Alsa. 

From the command line, I ran alsamixer, pressed F6 to select sound card, and chose HDA Intel. Now sound works, even after rebooting.

Alsamixergui doesn't seem to have the ability to select the sound card. If you are using a different sound system, there should be some equivalent ability to turn on the master.

Before I found the solution, I went through the steps in the sticky Sound Problems Solutions Guide. Following that, I ran 

aplay -l

which told me I had
card 0: Intel [HDA Intel], device 0: ALC861 Analog [ALC861 Analog]

then

lspci -v

which told me
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02)
	Subsystem: Toshiba America Info Systems Toshiba Satellite A100-796 audio (Realtek ALC861)
	Flags: bus master, fast devsel, latency 0, IRQ 43
	Memory at f0b40000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

so I know I need to enable module snd-hda-intel

I tried
sudo modprobe snd-[tab]

but the card wasn't listed.

However, the search
slocate hda-intel

turned up 
/lib/modules/3.0.0-12-generic/kernel/sound/pci/hda/snd-hda-intel.ko

so I knew the module was present.

I thought I would have to add the line snd-hda-intel to /etc/modules and reboot. Perhaps that would work, but for me it's not neccessary.

---

