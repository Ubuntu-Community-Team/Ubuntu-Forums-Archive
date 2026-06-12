---
title: "Fairytales of a Jackalope who was quite Jaunty"
date: 2009-08-04
forum: New to Ubuntu
---

### Post by Fancycakes on 2009-08-04
I recently installed Ubuntu onto my laptop for school and all was swell, I had installed Intrepid Ibex, got all the available updates and hey, it was nice and pretty, everything was as it should be. Since I went to a far stronger internet connection rescently, I decided to upgrade to Jaunty Jackalope. It made things ever so much easier on the eyes, nice features here and there and yet.... something was missing.

Throughout all the shazam and shamwow, Jaunty Jackalope janked my sound.

I have a few clues here, and I really hope it helps. But before that, I must warn you: I have the most terrible luck with things going wrong with my computer: I ask for help and it magically fixes itself one way or another.

I went to sound preferences and tested the different settings, anything to get some kind of sound. All nothing. I checked the sounds, nothing muted, everything as loud as it could get. In the sound preferences, however, there was one setting that caught my eye: the setting for "HDA ATI SB ALC272 Analog (ALSA)" not only didn't give me any sound to work with, it gave me an error.

audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Could not open audio device for playback.

Now, I may not be a smart man, or even a good Forrest impressionist, but I do know what error reports mean.... kinda. My guess/hope is that this selection is my sound, trapped by the magical fiend that makes computers work in ways ill befitting their stature.

The only reason, actually, that it caught my attention was the SB part. My sound card is SB! Live. ALSA is a very common driver, SB is my sound card, the connection is there, is it not?

My question is how do I put the pain back onto both driver and card so I can go back to listening to music and/or watching movies?

inb4 tl;dr, and an Hero.

---

### Post by CLomax on 2009-08-04
> I recently installed Ubuntu onto my laptop for school and all was swell, I had installed Intrepid Ibex, got all the available updates and hey, it was nice and pretty, everything was as it should be.
Remember. When all is well it's best to stay where you are. Unless you don't mind breaking stuff.

> audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Could not open audio device for playback.
That error usually occurs when the audio device is being used by another process. The infamous PulseAudio bug.

Do you have audio codecs and such installed?
```
sudo apt-get install ubuntu-restricted-extras
```

Also, medibuntu...        [https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

> inb4 tl;dr, and an Hero.
We're not that way inclined :)

---

### Post by sandwormblues on 2009-08-04
> **CLomax said:**
> Remember. When all is well it's best to stay where you are. Unless you don't mind breaking stuff.

That's not the way it should be.  That's why there are different classes of updates.  That's why there are alpha and beta, and release candidate versions.  Users should be encouraged to install security updates zero-day.

Cannonical needs to get it together and quit breaking our sound.  I have faith, but does that make me a fanboy?

---

### Post by Fancycakes on 2009-08-05
> Do you have audio codecs and such installed?
```
sudo apt-get install ubuntu-restricted-extras
```Also, medibuntu...        [https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

I did all that fun stuff and nothing has changed. This is all just silliness. I can't go without music and sound on my laptop of epic proportions.

---

### Post by kansasnoob on 2009-08-05
Start with the basic troubleshooting steps here:

[https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)

---

