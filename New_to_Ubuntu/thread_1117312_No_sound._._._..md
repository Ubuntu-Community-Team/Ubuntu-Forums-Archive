---
title: "No sound. . . ."
date: 2009-04-05
forum: New to Ubuntu
---

### Post by halfmt on 2009-04-05
Hello:

I am new to ubuntu, just installed it this weekend;)  I am thinking of switching over from windows and this is my test run.  I have done a bit of configuring thus far with the help of the forum but I can't find a solution to this sound problem.  I have a MCP73 High Definition Audio chipset on my motherboard and I can not get any sound out of it.  Not even with "Hardware testing" under administration.  I am hoping someone can point me in the right direction to resolve the issue.

Here's what I get from lspci -v for the audio portion:

00:09.0 Audio device: nVidia Corporation MCP73 High Definition Audio (rev a1)
	Subsystem: nVidia Corporation MCP73 High Definition Audio
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 23
	Memory at efff8000 (32-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

Thanks

---

### Post by taqkavar on 2009-04-05
first update your system:

sudo apt-get update
sudo apt-get upgrade

if it requires a restart then do restart it. then go to System > Preferences > Sound and choose ALSA for Sound Playback. click the test button to see if it works. If it doesn't, also try PulseAudio and OSS and click on the test. Everything should be fine if any of those play a beep when you press Test.

---

### Post by halfmt on 2009-04-06
Thank you! I got sound from two (of six) of the back ports now that's way better than nothing:p  Unfortunately there is still no sound from the front ports.  Any suggestions?

---

