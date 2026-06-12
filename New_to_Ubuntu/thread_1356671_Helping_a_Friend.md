---
title: "Helping a Friend"
date: 2009-12-16
forum: New to Ubuntu
---

### Post by rosswmcgee on 2009-12-16
We have two computers using 9.10 no problems. I suggested Ubuntu to a friend who was fed up with windows. He had a pal install Ubuntu 9.10, system worked fine except for no audio. They gave up on the audio, so I said give me the problem. I brought the computer home this morning and plugged it in and voila! no problem the audio is fine. So I thought I would tinker with his computer a bit, but alas! no video! I mean no video period. Tried another monitor, same thing no video, no bios screen nada.
So I removed the video card and re seated it, still no video. Any ideas? 
Otherwise the guy will have to buy a new computer.

---

### Post by jerrrys on 2009-12-16
any fuses on the card?  is the fan working?

---

### Post by candtalan on 2009-12-16
> **rosswmcgee said:**
> We have two computers using 9.10 no problems. I suggested Ubuntu to a friend who was fed up with windows. He had a pal install Ubuntu 9.10, system worked fine except for no audio. They gave up on the audio, so I said give me the problem. I brought the computer home this morning and plugged it in and voila! no problem the audio is fine. So I thought I would tinker with his computer a bit, but alas! no video! I mean no video period. Tried another monitor, same thing no video, no bios screen nada.
So I removed the video card and re seated it, still no video. Any ideas? 
Otherwise the guy will have to buy a new computer.

Not sure at all, however I am just in the middle of a episode with one of my PCs which suddently 'lost video', at least that is what I thought. Not even any bios display when booting - the hard drive did seem to run with an initial sequence but the hd light eventually stayed on. Anyway, changed monitor, PSU, video card, still nothing. I even changed the mainboard..... there is determination! Still nothing. I was a bit surprised. Current conclusion is the Pentium 4 chip is failed, I have P4 spares to try now but have not had a chance yet. Here's hoping.

Good luck.

---

### Post by rosswmcgee on 2009-12-16
Fan is working now but was slow at first boot before warm up. As to the fuses this is an older computer and I don't know it just looks like a plain card, what do the fuses look like?

---

### Post by jerrrys on 2009-12-16
what model of computer is it and also video board model please...

---

### Post by rosswmcgee on 2009-12-16
OK I took the video card out and re set it again. Then I realized that on this older

computer I was plugging the monitor into the wrong plug, there are two blue  female 

plugs on this computer. So now I have video, but guess what now I have no sound! So why would ubuntu have sound with the video card plugged in wrong but no sound with the video card plugged in correctly?

---

### Post by candtalan on 2009-12-16
> **rosswmcgee said:**
> OK I took the video card out and re set it again. Then I realized that on this older

computer I was plugging the monitor into the wrong plug, there are two blue  female 

plugs on this computer. So now I have video, but guess what now I have no sound! So why would ubuntu have sound with the video card plugged in wrong but no sound with the video card plugged in correctly?

interrupt management maybe? on older PCs this sort of thing was not always automatic?

---

### Post by llawwehttam on 2009-12-16
I recently had a problem with an old agp card where if i was using the dvi port the screen was blank but the vga worked fine. The audio was a bit strange with the dvi as well.

If it has a sound-card try disabling on-board sound as it can interfere. 
It sounds like one of those problems that need fiddling to fix. Maybe play around with the BIOS a bit. Try a default settings load maybe?

---

### Post by rosswmcgee on 2009-12-16
I did the bios thing, no change so now I am installing 9.10 clean myself. New install still no sound.

If sound is still missing how do I disable on board sound as you suggest?

---

### Post by rosswmcgee on 2009-12-18
The problem of no sound has been found. Removed old telephone modem, removed sound card, installed sound card where telephone modem was. This granted more space between the video card and the sound card. I believe there was interference between the two cards. 
Ubuntu 9.10 then recognized the sound card, but still no audio. Installed esound. Problem fixed.

---

### Post by audiomick on 2009-12-18
> **rosswmcgee said:**
> Then I realized that on this older

computer I was plugging the monitor into the wrong plug, there are two blue  female plugs on this computer.

Hi.
I am a sound engineer.
It is *AMAZING* how many of our "digital" problems turn out to be a cable plugged in wrong or not at all.... ;)

---

