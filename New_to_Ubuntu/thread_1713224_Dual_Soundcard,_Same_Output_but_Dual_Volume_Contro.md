---
title: "Dual Soundcard, Same Output but Dual Volume Control"
date: 2011-03-23
forum: New to Ubuntu
---

### Post by Dr_Frost on 2011-03-23
I have searched for over 1 week now and have not been able to find anything that can help me with my setup.

I want to use 2 Sound cards to play same output but at diffrent volume levels.
1. Sound card (Onboard) will be regulated by normal volume control
2. Sound card (USB) will be set at a set volume
Both will output the same but at their respected volumes

Whats the point?, Onboard audio goes to Amplifier, USB goes to light controller for light effect.

OS: Ubuntu 10.10 32-Bit

---

### Post by kostkon on 2011-03-23
Install the *PulseAudio Device Chooser* utility using the software centre. Run it (Applications &#8594; Sound & Video &#8594; PulseAudio Device Chooser) and its icon will appear in your tray.

Left-click on it and select *Volume Control*. Set the volume levels of your cards in the *Output Devices* tab. Then close the volume control utility; left-click again on the tray icon and select *Configure Local Sound Server* and then click on the *Simultaneous Output* tab to configure the... simultaneous output for your cards.

Hope that helps.

---

### Post by Dr_Frost on 2011-03-24
well that kinda worked

i have audio out in both cards and in sync, but can't really do anything, the sound goes on and off sometimes, lags, shutters
in wine games audio is .5 of a second behind
hires movies wont play

But i am able to have audio in both and can set volume levels on both.....

---

