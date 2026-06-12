---
title: "no sound with sb xfi, or mother board."
date: 2011-02-27
forum: New to Ubuntu
---

### Post by wjs1968 on 2011-02-27
Can anyone tell me if there is way to get sound. I'm running Ubuntu 10.10 fresh install. I spent most of yesterday reading the forums to discover my sound blaster x fi extreme probably will never be supported, but I can't get sound from the mother board either.

---

### Post by Silent Warrior on 2011-02-27
What do you get when you enter:
```
lspci | grep Audio
```
If your card or chip is correctly identified, what are the volumes set to in the volume-control applet? What output? And, yes, you should double-check this (happened to my parents, and one of them is an engineer with nearly 40 years experience): Are the speakers connected correctly?

---

### Post by wjs1968 on 2011-02-27
I ran that script, here is what I got.....

00:04.0 Multimedia audio controller: nVidia Corporation CK804 AC'97 Audio Controller (rev a2)
03:00.0 PCI bridge: Creative Labs [SB X-Fi Xtreme Audio] CA0110-IBG PCI to PCIe Bridge
04:00.0 Audio device: Creative Labs [SB X-Fi Xtreme Audio] CA0110-IBG

btw, speakers are plugged in, they work well for windows just not ubuntu.

---

### Post by Silent Warrior on 2011-02-27
Ok, good so far. Then there are two possibilities that I can see: Either the volume is down as far as it can go, or the output is at the wrong setting. You'll have to check that, though. Checking that nothing is muted is, I think, best done with a command-line utility, alsa-something, but I don't remember exactly what it's called. Right-click the volume-control applet, open Sound settings, and look at the Output-tab. What does the drop-down box say?

---

### Post by wjs1968 on 2011-03-08
Just realized I didnt post answer..sorry..  nothing is muted, all volumes are turned up, card selected and set to default. No sound yet. I think I read somewhere that I have to compile my own driver for this card, which is way beyond my abilities

---

### Post by Silent Warrior on 2011-03-08
Compiling, beyond your abilities? You know, you'd be surprised! Either way, this IS the place to ask for assistance.
Well, what happens if you disable the onboard sound (nVidia AC97) in BIOS?

---

### Post by wjs1968 on 2011-03-09
Still Have no sound.   My Linux classes don't start until next semester!

---

### Post by wingman358 on 2011-03-09
> **wjs1968 said:**
> I ran that script, here is what I got.....

00:04.0 Multimedia audio controller: nVidia Corporation CK804 AC'97 Audio Controller (rev a2)
03:00.0 PCI bridge: Creative Labs [SB X-Fi Xtreme Audio] CA0110-IBG PCI to PCIe Bridge
04:00.0 Audio device: Creative Labs [SB X-Fi Xtreme Audio] CA0110-IBG

btw, speakers are plugged in, they work well for windows just not ubuntu.

Your motherboard has a built-in sound card, which is completely separate from the X-Fi sound card. I don't mean to insult your intelligence, but which card are you using in Windows?

---

### Post by wjs1968 on 2011-03-09
No insult taken, I run all my audio off of the xfi, I have the audio on the MB disabled in the BIOS.

---

### Post by wjs1968 on 2011-03-09
Just a quick note. I have always run my sound in Windows off the sound card, but the MB sound wasn't disabled until today. I have another machine I want to put together and have it dedicated to UBUNTU, it will have the same sound card, as I got 2 of them some time ago for a deal.  Thats part of the reason I would like to get the audio working on this machine first.  (wish I could find the link with info on compiling my my own driver!)

---

