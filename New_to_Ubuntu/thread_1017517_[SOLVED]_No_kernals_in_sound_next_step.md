---
title: "[SOLVED] No kernals in sound: next step?"
date: 2008-12-21
forum: New to Ubuntu
---

### Post by vikigal on 2008-12-21
I am working through the sound troubleshooting guide, again, and I noticed in the lspci -v | less output there are no kernals listed. I believe they should be there. the illustrations all show them, but not mine. I am not sure what to do next. I looked for my driver at the alsa project site and found my sound card listed in black, ich5/ich5r with ac97 audio controller. I am just uncertain whether it is neccessary for me to go this step.

I have had sound problems since upgrading to 8.04. Working through How-tos has not helped. Had bad sound, now no sound. Have installed-uninstalled pulseaudio and alsamixer. Everything I can find is unmuted.

I had my son-in-law look at it and although he does not currently work with linux he knows computers (unix) he said everything appears to be on the machine it is just not connecting up.

modinfo soundcore tells me it is there: Where do I go from here? If I must do the driver from the matrix:module page, do I do all the steps? Will I screw my system or just the sound system (which is already foobar) if I goof up?


oldgal1@user-desktop:~$ modinfo soundcore
filename:       /lib/modules/2.6.24-22-generic/kernel/sound/soundcore.ko
alias:          char-major-14-*
license:        GPL
author:         Alan Cox
description:    Core sound module
srcversion:     548AA54AF08207316C104F8
depends:        
vermagic:       2.6.24-22-generic SMP mod_unload 586 
oldgal1@user-desktop:~$ 

<snipped from>  
lspci -v | less

00:1f.5 Multimedia audio controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)
        Subsystem: IBM Unknown device 0285
        Flags: bus master, medium devsel, latency 0, IRQ 20
        I/O ports at 1c00 [size=256]
        I/O ports at 18c0 [size=64]
        Memory at e8080800 (32-bit, non-prefetchable) [size=512]
        Memory at e8080400 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>

03:0b.0 Ethernet controller: Intel Corporation 82541EI Gigabit Ethernet Controller


Any body got any suggestions?

---

### Post by vikigal on 2008-12-23
I solved the sound and mounting issues by disabling pulseaudio and re-installing the driver for the Intel 8280IEB/ER AC 97 Audio Controller. I am just using alsamixer and sound is great everywhere but the disk and that just needs some audio adjustments. I now get a long list of things when I run  lspci -v | less, bridges and busses that had not shown up before. I can ride anywhere now.

I still need to adjust some permissions that got foobar-ed by my tinkering. Audio disks are all that it will mount at the moment but I believe I can fix that. (I bought two books, a phrase book and the tool book.)

I firmly believe that pulseaudio was causing the problems.

---

