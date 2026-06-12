---
title: "After BIOS reset, system hangs before Ubuntu loading screen"
date: 2010-04-18
forum: New to Ubuntu
---

### Post by gmxgeek on 2010-04-18
I have a custom built machine that has been working mostly fine up until recently. I had my motherboard die on me, so I replaced it. Shortly thereafter, I noticed that my video card was artifacting terribly. So today I bought a new one. It also began artifacting. 
Everything was working fine, except for this. Thinking that it might be a BIOS setting gone awry with the new board, I reset the BIOS settings back to factory defaults (I had done some tweaking when I first bought it).

However, after resetting the BIOS, Ubuntu will not display the loading screen. It displays the GRUB menu, and the Starting Up... text, but goes no further. Recovery console reveals that it gets suck after "io scheduler cfq registered (default)". Any ideas on why this might be happening?

This issue also persists in my Windows partition, hanging after acpitabl.dat

Motherboard: Biostar TA790GXE
OS: 9.04 x64 / XP x64

---

### Post by candtalan on 2010-04-18
I wonder - does a live CD  (ubuntu?) work ok?

---

### Post by bpowell2005 on 2010-04-18
> **gmxgeek said:**
> I have a custom built machine that has been working mostly fine up until recently. I had my motherboard die on me, so I replaced it. Shortly thereafter, I noticed that my video card was artifacting terribly. So today I bought a new one. It also began artifacting. 
Everything was working fine, except for this. Thinking that it might be a BIOS setting gone awry with the new board, I reset the BIOS settings back to factory defaults (I had done some tweaking when I first bought it).

However, after resetting the BIOS, Ubuntu will not display the loading screen. It displays the GRUB menu, and the Starting Up... text, but goes no further. Recovery console reveals that it gets suck after "io scheduler cfq registered (default)". Any ideas on why this might be happening?

This issue also persists in my Windows partition, hanging after acpitabl.dat

Motherboard: Biostar TA790GXE
OS: 9.04 x64 / XP x64

I've been fighting something like this myself these last few days! Just got a new MOBO, trying to install Lucid...boot hangs. My Windows boots fine though.

I think I've narrowed the problem down to shared video memory...which is strange, because Jaunty will run just fine, but any version past Jaunty hangs. Try looking in your BIOS settings, make sure only the one video card is selected...and if you have some kind of memory sharing...turn that down to 128m...no higher. That seems to be working for me right now.

---

### Post by gmxgeek on 2010-04-18
Hey guys. I fixed the problem. Turns out it was somthing involving the way the USB was set up (WTF?)

I set legacy support from enabled to auto, and set the speed from hispeed to fullspeed.

Just those two options, with everything else factory default, allows me to boot. Very weird, but I'm happy to have my computer back :)

---

