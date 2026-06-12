---
title: "Skype, webcam ... and Update Manager?"
date: 2011-07-31
forum: New to Ubuntu
---

### Post by vmsda on 2011-07-31
Up until middle of last week I had Skype working perfectly in my system, video included. I have done nothing hardware or software wise to change the system, but the webcam stopped working and people I communicate with do not get the video images. I read some appends, installed "cheese", but even this tool does not manage to find the webcam.

The only cause I can think of relates to software updates that I installed, based on a pop-up window which I received, as usual. I recall that one of those updates was particularly large, and it may have made alterations to the kernel, and the webcam driver was probably a victim.

Since everything worked fine right from the start when I installed this version of Ubuntu, what am I to do? Re-install the whole system?

Thank you for your help.

---

### Post by Paqman on 2011-07-31
> **vmsda said:**
> 
The only cause I can think of relates to software updates that I installed

...or your webcam has died. Can you plug it into another computer to check?

---

### Post by westie457 on 2011-07-31
Are you able to boot into an earlier version of the kernel via your grub menu.

EG 2.6.35-30 is the latest and 2.6.35-28 the previous working one

If everything is working as it should add the updates one at a time until the problem reappears. Then go through the whole process again leaving out the problem update.

This is a work around and not a fix.

---

### Post by vmsda on 2011-07-31
Thank you for your reply, Paqman.

The webcam is not external, nor do I have a spare one to try.

---

### Post by vmsda on 2011-07-31
Thank you for your suggestion, westie457. I tried restarting with every available kernel version (including the one you suggested), and the result was the same. In the restart, two messages flicker very very briefly on the black screen, and I seemed to see something like "... video failed ...".

Could I be grappling with a hardware failure after all?

---

### Post by jaunty.jacklope on 2011-07-31
As another try use a live CD to boot your system and see if you can get the webcam to work.

---

### Post by no2498 on 2011-07-31
LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype

put that in a terminal see if it helps

---

### Post by Paqman on 2011-07-31
> **jaunty.jacklope said:**
> As another try use a live CD to boot your system and see if you can get the webcam to work.

^ This. If it doesn't work on the LiveCD either, then it's hardware, if it does work on the LiveCD then you are correct and it is software.

---

### Post by vmsda on 2011-07-31
Thank you for your suggestion no2498.

I tried the command you suggest, then in skype I chose Options --> Video, and I get "no devices found". Tried the same command but replaced 'skype' with 'cheese' and got the same result.

---

### Post by vmsda on 2011-07-31
> **jaunty.jacklope said:**
> ... try use a live CD ...

Well, I did try:
1. Tried to install 'cheese' after installing from the live CD; told me it could not reach the repositories and I should check my internet connection. This made no sense.
2. Tried to install 'skype', re-directed me to another location, from which skype installed just fine.
3. Launched skype, went into Options --> Video Devices, and again the "no devices found" on the display. Actually, I could not get the sound working properly either, but that may have been because I did not have the microphone connected when I booted from the live CD.

This is looking very much like the end of the road.

---

