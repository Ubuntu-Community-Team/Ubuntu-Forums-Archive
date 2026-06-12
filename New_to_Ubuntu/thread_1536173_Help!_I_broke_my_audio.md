---
title: "Help! I broke my audio"
date: 2010-07-21
forum: New to Ubuntu
---

### Post by kevinm416 on 2010-07-21
I'm brand new to Ubuntu, and I trying to get the internal microphone on my laptop to work so I could use skype. I've got an Acer Aspire 5739, and I was following the instructions on a forum that had me installing alsa-driver-1.0.20. Now neither my speakers, headphone jack, nor microphone work. 

How can I reset the audio to how it was when I installed ubuntu so at least my speakers work?
Oh, its 10.04 x64 if that makes a difference.

---

### Post by ubunterooster on 2010-07-21
see: 			                          			 			[Comprehensive Sound Problem Solutions Guide]("http://ubuntuforums.org/showthread.php?t=205449")

---

### Post by kevinm416 on 2010-07-22
Ok, I went through the first 4 steps, but "aplay -l" is not showing my soundcard. I can't figure out what to do next because I can't find my soundcard on the alpa website. "lspci -v" shows this for my soundcard 

```
01:00.1 Audio device: nVidia Corporation High Definition Audio Controller (rev a1)
	Subsystem: Acer Incorporated [ALI] Device 021e
	Flags: bus master, fast devsel, latency 0, IRQ 5
	Memory at cdefc000 (32-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel modules: snd-hda-intel
```

Could anyone give me instructions on how to proceed? The instructions for compiling the alpa driver requires that I know the name of my driver. The driver must exist, because my sound worked before, but there are too many to do by trial and error.

---

### Post by cjv8888 on 2010-07-22
You can try upgrading the Alsa driver to 1.0.23 as instructed [here]("http://monespaceperso.org/blog-en/2010/05/02/upgrade-alsa-1-0-23-on-ubuntu-lucid-lynx-10-04/").

Did wonders for my laptop.

---

### Post by supadupadad1 on 2010-07-22
I had sound issues on my laptop and followed the instructions on this link and works fine now. hope this helps.   [http://www.unixmen.com/linux-tutorials/525-resolve-nosound-problem-on-ubuntu910-karmic-koala](http://www.unixmen.com/linux-tutorials/525-resolve-nosound-problem-on-ubuntu910-karmic-koala)

---

### Post by lidex on 2010-07-22
> **kevinm416 said:**
> I'm brand new to Ubuntu, and I trying to get the internal microphone on my laptop to work so I could use skype. I've got an Acer Aspire 5739, and I was following the instructions on a forum that had me installing alsa-driver-1.0.20. Now neither my speakers, headphone jack, nor microphone work. 

How can I reset the audio to how it was when I installed ubuntu so at least my speakers work?
Oh, its 10.04 x64 if that makes a difference.

That's an old version. To get back to default try this:
Using a Terminal="Applications->Accessories->Terminal"
```
sudo apt-get update
sudo apt-get upgrade
```
```
sudo apt-get purge linux-sound-base alsa-base alsa-utils

```
```
sudo apt-get install linux-sound-base alsa-base alsa-utils gdm ubuntu-desktop

```
**gdm and ubuntu-desktop usually get taken out in the process, so we add them back**
**Reboot.**
If you want to upgrade after that I personally would suggest following the alsa-upgrade link in my sig.

---

### Post by kevinm416 on 2010-07-23
supadupadad1, thank you so much. It didn't fix my mic, but my speakers work again.

---

### Post by sandyd on 2010-07-24
> **kevinm416 said:**
> supadupadad1, thank you so much. It didn't fix my mic, but my speakers work again.

tell me, are you using pulseaudio? because if you are, you will have to install pavucontrol and unmute the mic.

---

### Post by kevinm416 on 2010-07-24
And thank you too carlee. In the pavucontrol window, there is a dropdown list of microphones. Pulse audio defaulted to microphone 1, which does not work for some reason. Microphone 2 works. I'm not sure why there are two options, since I only have one microphone, but everything is working perfectly.

---

