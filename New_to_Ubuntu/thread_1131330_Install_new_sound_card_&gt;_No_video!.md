---
title: "Install new sound card &gt; No video!"
date: 2009-04-20
forum: New to Ubuntu
---

### Post by SumthingWicked5 on 2009-04-20
The onboard sound card with my ASUS M2R32-MVP Motherboard wasn't cutting it for me so I decided to buy a new sound card. I got a Creative Sound Blaster XFi XtremeMusic SC.

When I plug it in to my PCI slot and turn my system on, everything sounds normal, and I can hear it "thinking" but I get no output to my monitor. It stays in standby mode like the video card isn't even looking for it anymore.

I assumed it was just plug-and-play, and haven't changed any settings anywhere. 

Any thoughts?

---

### Post by Jazzy_Jeff on 2009-04-20
First thing I would do is pull out the new sound card and log into your bios and disable the onboard sound and then add the new sound card and see if that fixes the problem.

---

### Post by Shazaam on 2009-04-20
Two questions...
1. Did you disable the onboard sound in your bios?
2. Did you accidently disable your onboard video (if you were using it)?

---

### Post by Jazzy_Jeff on 2009-04-20
> **Shazaam said:**
> Two questions...
1. Did you disable the onboard sound in your bios?
2. Did you accidently disable your onboard video (if you were using it)?

This board does not have onboard video.  :D

---

### Post by SumthingWicked5 on 2009-04-20
i did not disable the onboard card in my bios because I don't know how to do that. 

I'm really new at all of this stuff. How do I do what you're suggesting?

---

### Post by Shazaam on 2009-04-20
When your pc first boots it should list the key(s) to get into the bios. Normally this is the DELETE button. Other keys are F2 or F12 (sometimes F6). The best thing to do is to look in the manual for the correct key (if you have one).
What you do is push the power button then start tapping whatever key you need to use to enter the bios setup screen. Then look for something similar to "Integrated" or "Onboard". Then go to "Save and Exit" when you are done.

---

### Post by halitech on 2009-04-20
I think we are jumping the gun here. How can he log into the BIOS if he can't see anything on the screen?

I would power down the system, take out the sound card, then take out the video card and reseat it. Power the sytem back up to confirm you can now see output to the monitor. Then go into the BIOS and disable the onboard sound. Power down again and insert the new sound card. Power up and see if you have video. If not, something is screwy with the new sound card.

---

### Post by Jazzy_Jeff on 2009-04-20
I have the same board as you do. First thing restart your computer and as it is starting up hit the DELETE key. Once in the bios go to the Advanced tab. Go down to onboard devices configuration and the first option should be your audio. You have to hit the + or - key to change the option. Once it is disabled hit F10 to save and exit.

---

### Post by Jazzy_Jeff on 2009-04-20
> **halitech said:**
> I think we are jumping the gun here. How can he log into the BIOS if he can't see anything on the screen?


That is why I told him to take the new audio card out first. If he still does not have video then he has another problem.

---

### Post by halitech on 2009-04-20
Yes you did but everyone else is concentrating on the BIOS settings and haven't mentioned taking out the card :)

Its nice that you have the same board and can help him exactly with the settings.

---

### Post by Jazzy_Jeff on 2009-04-20
I am not sure what video card you have but when you have the system opened up make sure your video card did not come unplugged as well.

---

### Post by SumthingWicked5 on 2009-04-20
Thank you all so much. you're amazing. It works! You made my night.

---

### Post by SumthingWicked5 on 2009-04-20
Nope, turns out I'm not even as smart as I thought I was. I'd forgotten to put the card back in after de-activating my onboard audio. I found it on the floor, plugged it in, and still nothing. Unplugged it, and it works fine. 

So for the short version, onboard is deactivated in Bios and saved, and it still doesn't work.

---

### Post by halitech on 2009-04-21
have you resolved at least the issue with not having any video?

---

### Post by SumthingWicked5 on 2009-04-21
No the issue is the same. No improvement.

---

### Post by halitech on 2009-04-21
do you have video if the sound card is not installed?

---

### Post by SumthingWicked5 on 2009-04-21
Yes I do. When it is not in the PCI slot, everything works perfectly. Right now there's no sound, because I still have my onboard card disabled, but yeah. Everything is fine. Then I turn off the system, plug in the sound card, and turn it back on, and I get nothing. the little yellow "standby" no-signal light on my monitor doesn't even turn green.

---

### Post by halitech on 2009-04-21
do you have another slot you could try? maybe its an issue with the slot. If not, might be a bad card.

---

### Post by SumthingWicked5 on 2009-04-21
i did try both of my slots. I did get the card from a discount site online, but it seemed to have fairly good reviews, so I thought it was safe.

---

### Post by halitech on 2009-04-22
well, not saying the site knew it was bad but it might have just been a dud from the manufactorer. Contact them and see if you can return it for a replacement.

---

### Post by SumthingWicked5 on 2009-04-22
Will do! Thanks.

---

