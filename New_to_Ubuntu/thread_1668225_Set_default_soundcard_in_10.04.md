---
title: "Set default soundcard in 10.04"
date: 2011-01-16
forum: New to Ubuntu
---

### Post by Jetro on 2011-01-16
How do I set default soundcard in Ubuntu 10.04?

I've searched *so much* for this, but everything seems to be for earlier versions. Nothing has worked...

I have a USB soundcard. Whenever I start Ubuntu, it reverts back to the internal sound, so I have to manually change it in Sound preferences every t ime.

Before (8.04) I could do this:
```
sudo asoundconf set-default-card Xmod
```

But that can't be done any more. Any tips?

---

### Post by BcRich on 2011-05-04
hi Jetro
did you ever find a solution to this? I've been googling the same problem for ages and in the process have made modifications to my setup which has rendered my sound totally non-existent. I also use an external usb sound device. it used to work until i messed around with some files only thing is i have no idea how to get the sound back to the way it was.
sorry i can't help you :(

---

### Post by samizdatstudio on 2011-05-04
my fujitsu u810 have the some problem,
when i wanna listen music from headphone,speaker and headphone function at same time,it havent change each other,
i no install any additional driver for sound card
is it need install alsa?
where i go change this or fix it?
thanks

if any one know,please help

---

### Post by Jetro on 2011-05-30
> **BcRich said:**
> hi Jetro
did you ever find a solution to this? I've been googling the same problem for ages and in the process have made modifications to my setup which has rendered my sound totally non-existent. I also use an external usb sound device. it used to work until i messed around with some files only thing is i have no idea how to get the sound back to the way it was.
sorry i can't help you :(
Hey, actually, no, I haven't found one. It's weird that it is that hard. I don't know how to get the developers to start listening, either. Reporting a bug is such a hazzle...

Sometimes the sound is by default in the USB audio speakers, but I can't control them (turn the volume up or down). When in Sound preferences, Internal audio is still selected even though the sound came from the USB speakers. So you have to change it anyway.

And just a final tip: Don't install 10.10 og 11.04, with USB audio (to) me I get a bad quality with shrieking whenever the slider's not at max volume :|

---

### Post by jtarin on 2011-05-30
Have you tried disabling the onboard soundcard in the bios?

---

### Post by BcRich on 2011-06-01
Hi jtarin
thanks for the suggestion :) although it might be a working solution for many people as disabling the onboard soundcard in the bios seems to be the most common solution for this problem on ubuntuforums it's not as effective as a tool that would simply allow for the selection of a default sound device. For example I have multiple soundcards to alleviate some of the strain that is placed on my external sound device which is a usb 1.1 device I use the midi functionality of my other soundcard (whether that is onboard or PCI is not really of relevance as long as it is not the usb device). disabling the onboard sound card means that I have to do everything with my external soundcard, this is probably not the most efficient way of using system resources and recording 4  48kHz tracks, routing midi through and monitoring sound all through the same device can cause unnecessary 'wear and tear' on the device, when I could just as easily use the other resources that are working perfectly and already in place such as another sound device for midi and not have this in any way compromise the integrity of my recording (and even perhaps prolong the lifespan of my external device).
I hope this explains, a little more clearly why I would prefer to simply select a default sound device as opposed to disabling sound devices through bios, which in some instances has been the only method available to get any sound at all in ubuntu.

---

