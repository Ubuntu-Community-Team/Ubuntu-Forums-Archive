---
title: "Audio problems with old Toshiba Satellite"
date: 2011-03-08
forum: New to Ubuntu
---

### Post by nathon210 on 2011-03-08
[FONT=Arial][SIZE=2]Hey everyone, I'm new to Ubuntu (and Linux in general) and I was wondering if you could give me a hand. I'm having trouble getting the sound to work on my friend's laptop. The laptop is a Toshiba Satellite A105 S4074, originally running Windows XP. I installed Ubuntu 10.10 alongside the old OS, and it seems to be working normally, minus the audio (neither the headphone jack nor the speakers seem to be working, the laptop is simply silent whenever a sound is supposed to play). 

Under System>Preferences>Sound, when I go to the hardware tab, the device listed is called "Internal Audio," and changing the settings from Analog Stereo Duplex to anything else doesn't seem to do anything.

I've done a little bit of research trying to find out how to fix it, but nothing was up to date (I think most of what I found was for Feisty or something). I tried following the advice of the people in this [COLOR=RoyalBlue][thread]("http://ubuntuforums.org/showthread.php?t=416207")[/COLOR], but nothing happened. 

Then, I tried following the instructions on [[COLOR=RoyalBlue]this page[/COLOR],]("http://taufanlubis.wordpress.com/2007/11/26/fix-no-sound-for-ubuntu-in-toshiba-satellite-a205-s4707/") but I couldn't make the last part of Step 4 work, getting the same problem that the first commenter, *saukya singgih,* had. From that thread, I learned a couple things about the laptop that may (or may not) help: 

If I enter [/SIZE][/FONT][SIZE=2]**"cat /proc/asound/card0/codec#0 | grep Codec**"[/SIZE] [FONT=Arial][SIZE=2]to check the codec, I get back:
***[SIZE=2]Realtek ALC861[/SIZE]***

If I enter [/SIZE][/FONT][FONT=Arial][SIZE=2][SIZE=2]**"lspci"**[/SIZE] to check the sound card, I get a big wall o' text that includes the line: [/SIZE][/FONT][FONT=Arial][SIZE=1] [SIZE=2]
[/SIZE][I][B][SIZE=2]
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02)

[/SIZE][/B][/I][/SIZE][/FONT][FONT=Arial][SIZE=2][SIZE=2][SIZE=2]Finally, if I enter "***[SIZE=2]modinfo soundcore[/SIZE]***" to check (you guessed it) soundcore, I get this lovely block of text:[/SIZE][/SIZE][/SIZE][/FONT]
[FONT=Arial][SIZE=2][I][B][SIZE=2] 
filename:       /lib/modules/2.6.35-27-generic/kernel/sound/soundcore.ko
license:        GPL
author:         Alan Cox
description:    Core sound module
srcversion:     EF16BDAFD00EF5D7A386369
depends:        
vermagic:       2.6.35-27-generic SMP mod_unload modversions 686 
alexia@alexia-Satellite-A100:~$ 

[/SIZE] [/B][/I]To be honest, it's fascinating, but it is still mostly gibberish. What should I do to give this poor old laptop the ability to sing again? Let me know if you need me to provide more information.


[/SIZE][/FONT]

---

### Post by Daveth on 2011-03-09
Hi. Welcome to the Ubuntu forum!
I found a 2008 post which suggested using the snd-hda-intel module for that laptop. Trouble is, things have moved on in Ubuntu, pulseaudio is now the sound server, and I do not know if this is a sound (excuse the pun) path now to follow. Hopefully others might.

---

### Post by nathon210 on 2011-03-10
Alright, how do I go about trying the snd-hda-intel module? Do you have a link or instructions? And would trying it be safe, or could I do irreversible damage in the attempt?

---

### Post by nathon210 on 2011-03-15
I don't really want to bump my thread, but I haven't really resolved the problem. Does anyone have any suggestions, links, or other pages/forums that I could refer to for help?

---

### Post by nathon210 on 2011-03-18
Is there a better forum for me to post this problem in to get more input?

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

I thought I would have to add the line snd-hda-intel to /etc/modules and reboot. Perhaps that would work, but for me it's not necessary.

---

