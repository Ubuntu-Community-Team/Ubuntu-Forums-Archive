---
title: "Choppy and Fuzzy audio in Ubuntu 8.04"
date: 2008-12-07
forum: New to Ubuntu
---

### Post by vizitorq on 2008-12-07
Hey guys, I've had Ubuntu 8.04 installed before on my other machine, but I just bought a bunch of new parts and built a really really fast machine, but I've never had this audio problem before...

Every possible time audio comes out of my speakers, it is choppy, and fuzzy. This was never a problem in the past so I have no idea what this new (better) computer could have a problem with it.

I've seen this problem posted on the forums here before, but only by a bunch of people who think the problem stems from the program that's running the audio... I know this is NOT the case, since it happens with flash videos, rhythmbox, and everything else that outputs audio. So, I know it's not the programs, I know it's an AUDIO-specific issue. I'm thinking it might have something to do with alsa.

Can i PLEASE get some help with this? Please. This is driving me nuts and I have absolutely no idea where to begin.

---

### Post by madsc89 on 2008-12-07
> **vizitorq said:**
> Hey guys, I've had Ubuntu 8.04 installed before on my other machine, but I just bought a bunch of new parts and built a really really fast machine, but I've never had this audio problem before...

Every possible time audio comes out of my speakers, it is choppy, and fuzzy. This was never a problem in the past so I have no idea what this new (better) computer could have a problem with it.

I've seen this problem posted on the forums here before, but only by a bunch of people who think the problem stems from the program that's running the audio... I know this is NOT the case, since it happens with flash videos, rhythmbox, and everything else that outputs audio. So, I know it's not the programs, I know it's an AUDIO-specific issue. I'm thinking it might have something to do with alsa.

Can i PLEASE get some help with this? Please. This is driving me nuts and I have absolutely no idea where to begin.

Did you buy a new Sound card? Do you use integrated sound card? Did you replace your motherboard?
If the first or the latter is the case, we need to know the make and model.

The problem is most likely in the drivers.

---

### Post by vizitorq on 2008-12-08
madsc89

This machine is entirely new with a brand new installation of Ubuntu. Nothing has ever been on this machine before. I bought everything from Fry's, came home and built it, and installed ubuntu. i realize it's a driver issue... but WHAT do i do about it?

The specs -
Motherboard: Gigabyte S-series M7505SLI-DS4
Processor:   AMD Athlon Dual-Core 64-bit
Graphics Card: nVidia GeForce 9800 GT (superclocked edition it says)

That's probably all that's necessary to know. I'm using the onboard soundcard. I didn't buy an extra special soundcard or anything. I didn't add any hardware after the installation. I've never encountered this problem before. I'm not new to ubuntu, but I'm a programmer, not an operating system troubleshooter =). Can I get some help here?

---

### Post by madsc89 on 2008-12-09
I found this fix for a similar problem ([http://ubuntuforums.org/archive/index.php/t-848216.html)](http://ubuntuforums.org/archive/index.php/t-848216.html)). You should give it a try.
> If you've never installed sound drivers before, try this:```
apt-get install alsa-utils alsa-base
```

After those packages (and their dependencies) are installed, run the ALSA configuration program (as an administrator):
```
alsaconf
```

Follow the prompts. ALSA should pick up your sound card(s). If all goes well, you should then configure the proper volumes on the ALSA mixer:
```
alsamixer
```

Good luck.

P.S. If you're new to ALSA, it's pretty much the standard sound architecture for Linux now. Go here for more info:
[http://www.alsa-project.org](http://www.alsa-project.org)

Hope it works out.

---

### Post by LowSky on 2008-12-09
click on the sound icon on the top panel, and lower PCM, just a tad, it should fix the distortion

---

### Post by vizitorq on 2008-12-09
madsc89,
```

[kumi][/var]: sudo apt-get install alsa-utils alsa-base 
[sudo] password for kumi: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
alsa-utils is already the newest version.
alsa-base is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

alsaconf doesn't exist. i don't have it installed, and i don't have the repositories to get it from aptitude.

alsamixer i'm familiar with and it's the same as LoWSky's suggestion. Lowering the PCM didn't change anything, just changed the volume, and not the distortion. Nothing has changed. still the same problem...


WTF!!!!

---

### Post by madsc89 on 2008-12-10
Are you sure you typed the mother board name correct?
Gigabyte S-series M7505SLI-DS4

---

### Post by vizitorq on 2008-12-11
Gigabyte S-series M750SLI-DS4

---

