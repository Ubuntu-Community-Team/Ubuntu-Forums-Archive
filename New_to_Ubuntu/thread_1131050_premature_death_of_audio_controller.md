---
title: "premature death of audio controller?"
date: 2009-04-20
forum: New to Ubuntu
---

### Post by linuxgrrl on 2009-04-20
I just got my PC back from the repair shop where they replaced the circuit board on the primary hard drive, which died suddenly when my toddler got ahold of the PC for a minute (whoops). Everything else on the PC was working fine before the repair.

Now I have no sound from the onboard AC97 audio controller.  I have taken all the steps in the Ubuntu sound troubleshooting guide, including reinstalling all audio components and drivers, checking alsamixer, etc.  The PC seems to THINK it has sound (dmesg doesn't indicate errors, lspci finds the card, aplay thinks it's playing a sound).  All channels are up and unmuted in Alsamixer.

Several questions here:
1. is there any possible physical connection between the death of my hard drive circuit board and the simultaneous demise of my onboard audio?  Could the same event (toddler pressing on/off button) have fried both of them?

2. Is there any way to determine if the audio controller is in fact fried?  All the drivers seem to load fine so I feel like maybe it's not actually broken, there's just something stuipd that I've overlooked. Anything else I can check for?

thanks
Mary

---

### Post by halitech on 2009-04-20
since you say its an onboard sound card, first thing I would doublechek is that it is enabled in the bios (shouldn't be listed if its disabled but never know) and 2, since you had things disconnected, just double check that the soeakers are plugged in properly in the correct jack.

---

### Post by linuxgrrl on 2009-04-20
Thanks.  The controller has three jacks - pink (mic), then green and blue.  The green and blue have inscrutable pictograms next to them (circle with a line).  Which jack should I use for a set of powered speakers?  

FWIW, I did all my troubleshooting tests against both the green and blue jacks, so I'm pretty sure that's not the problem but it would be nice to know which one is correct and save a step.

I will check the BIOS also.

---

### Post by halitech on 2009-04-20
I figured you had checked the jacks but sometimes they are mixed up so check the easiest things first :)

I didn't feel like trying to get my system out of the cubby hole I have it in but I have a spare card here and if the colors are universal, then the speakers should be plugged into the green jack. If you look very closely you should see the lines on each jack have an arow on them, the green should be pointing away from the jack and the blue is pointing towards the jack.

---

### Post by gali98 on 2009-04-20
Also, if you know what it should look like, you may check inside to make sure a cable is not disconnected. I'm not seeing this as being the case since you have onboard audio, but it could be possible.
Is this a laptop or a desktop?
Kory

---

### Post by linuxgrrl on 2009-04-20
> **gali98 said:**
> Also, if you know what it should look like, you may check inside to make sure a cable is not disconnected. I'm not seeing this as being the case since you have onboard audio, but it could be possible.
Is this a laptop or a desktop?
Kory

It is a desktop.  

Kory, I just remembered that when I put this mobo into a new case last year, the sound card rear jacks would not work if the supplemental cable to the case's front jacks was wrong in any way.  I bet you are right, the repair shop bumped something inside the box.  Can't wait to get home and check!  Thank you!

---

### Post by gali98 on 2009-04-21
Sure thing. Let us know how it turns out.
Kory

---

