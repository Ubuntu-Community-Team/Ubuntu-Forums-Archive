---
title: "Sound card: how to make it work?"
date: 2009-07-04
forum: New to Ubuntu
---

### Post by camaron1 on 2009-07-04
Hi everyone

Mi computer came with a cheap, low-quality on-board sound card. I've just bought and installed another one AUDIOPHILE 2496 and no sound comes off it, and basically I DON'T HAVE A CLUE WHAT TO DO. 

Ubuntu has recognized it but when I try to choose the card in the sound-configuration tool I get this error message (see attachment).

I don't have a clue if this is an hardware problem, a driver problem, or what else.

I've checked ALSA website and the instruccions to install the drivers are like Chinese to me. (But then, I don't know if I have to install anything...)

I've googled it and some people seem to indicate that BIOS might have something to do. I checked BIOS and i've got the option HD sound ON or OF, that is all.

Does anyone know where I could start please?

Any help greatly appreciated.

Thanks

---

### Post by AoSteve on 2009-07-04
By chance, did you try the LiveCD and have sound there?  I'm thinking you are having the same problem as I did when I installed 9.04 with my old system.   I had to actually disable the onboard sound before it would use the SBLive! I had for it.  However, I got that same error when I tried to use the onboard with 8.04LTS

---

### Post by camaron1 on 2009-07-04
> **AoSteve said:**
> By chance, did you try the LiveCD and have sound there?  I'm thinking you are having the same problem as I did when I installed 9.04 with my old system.   I had to actually disable the onboard sound before it would use the SBLive! I had for it.  However, I got that same error when I tried to use the onboard with 8.04LTS

How do you disable the on-board card and tell Ubuntu to use the new one?

---

### Post by AoSteve on 2009-07-04
Mine can only be disabled in the BIOS by turning off the AC'97 Audio option completely by marking it disabled.   Once I did that my sound started working perfectly.   That onboard unit never did work, not even in windows! LOL    But once I disabled it it ran perfect!   Try finding that in your bios and see if disabling it fixes you up.  If not, it's probably a driver problem and it could be simple as an install to having to buy a new card like I did in the case with my Creative X-Fi Xtreme Audio. :\

---

### Post by camaron1 on 2009-07-05
> **AoSteve said:**
> Mine can only be disabled in the BIOS by turning off the AC'97 Audio option completely by marking it disabled.   Once I did that my sound started working perfectly.   That onboard unit never did work, not even in windows! LOL    But once I disabled it it ran perfect!   Try finding that in your bios and see if disabling it fixes you up.  If not, it's probably a driver problem and it could be simple as an install to having to buy a new card like I did in the case with my Creative X-Fi Xtreme Audio. :\

The only option that refers to sound in my BIOS is HD audio and it is either ON or OFF. I switched it off and no sound comes off my computer.

Any more ideas?

---

### Post by camaron1 on 2009-07-05
Sorted. For whoever wants to know:

There is a small utility under PREFERENCES called Default Sound Card (how could I miss that eh?) The name is self-explanatory. Then under SOUND AND VIDEO  there is PulseAudio Volume Control where you can change the sound card for specific applications that are producing sound (music or video players etc.)

So no BIOS or drivers to fiddle with...

---

### Post by AoSteve on 2009-07-05
Good to hear bud!   I'm glad you got it working.  I spent about 24 hours trying to deal with my old machine before I figured out about turning the BIOS option off for my add-on SB Live.

---

