---
title: "Easy to use audio recording software in ubuntu karmic"
date: 2009-12-31
forum: New to Ubuntu
---

### Post by Jas_India on 2009-12-31
Hi, can anyone please suggest a decent audio recording software for streaming audio as well as sound playing through the sound cards....I have tried Audacity but somehow there are some issues with my RealTEk audio drivers. It is not picking the sound. In the input tab..i do not see any stereo mx option. The software has to be easy to use...something like mp3mymp3 for WIndows. THANKS

---

### Post by candtalan on 2009-12-31
The software I use is  the Sound Recorder found in 
Applications>Sound and Video>Sound recorder.

However there may be some items that may need setting up. This may also be useful if using Audacity too. Some of these include the sound preferences or options or properties found by right-click onto the loudspeaker icon at the top panel.

Your sound input can be from a microphone which is internal  or is plugged in etc etc or your input might be from line in or whatever. You will find a bit of experimenting will be useful.

The Sound Record also has Edit>Preferences too, and these will be useful and some might overlap with settings you have seen before.

Mix and Capture may be of interest if they are available.

Please note that the facilities you see will depend upon the facilities in your particular sound card.

this will hopefully get you started
hth

---

### Post by Jas_India on 2009-12-31
Thanks! It will be best if i could use the in-built Sound Recorder facility. I prefer to have less software installed as it makes our life much easier.

---

### Post by Jas_India on 2009-12-31
THe in-built sound recording function does not seem to be working. ANY OTHER OPTION PLEASE??

---

### Post by candtalan on 2010-01-03
> **Jas_India said:**
> THe in-built sound recording function does not seem to be working. ANY OTHER OPTION PLEASE??
Which version of Ubuntu are you using? I had some sound problems using version 8.04, but no problems with 8.10 or 9.04, or 9.10.

It is very important to configure the mixer (volume control) If you have fully explored those possibilities, and the facility is not apparently shown in the mixer (volume control) then it may just be that your sound card does not have the facility to record its own output, which is sometimes the situation.

If so, then you can use a 3.5mm stero jack to take the sound out to external speakers or phones, and a second wire from the jack to go ALSO to the record (microphone) or Line In jack socket. The configuration of the mixer (volume control) is still very important. If a mic socket input is used then the signal may be to high without adjustment.

hth

---

### Post by ankspo71 on 2010-01-03
Hi,
If your sound card has multiple input and output modes like mine does (analog, digital, , duplex, etc), you might have to make some changes in your sound preferences. Right click on the speaker icon in your panel, click on Sound Preferences, then click on the Hardware tab. Change your profile if possible at the bottom of the Hardware tab.

By default, my sound card was set up as Analog Stereo Duplex, but I had to change it to Analog Stereo Output in order to do any sound recording with Audacity. See the screenshot below. 

I'm using Audacity 1.3.10 beta, and I'm using the default settings. In the devices settings of Audacity...
Interface Host = ALSA
Playback Device = Default
Recording Device = Default

I should probably also mention I'm using Ubuntu 10.04 (alpha test release). PS. I just now recorded a 30 second sound sample with Sound Recorder, and it works... unlike before.
Hope this helps.

---

### Post by dzon65 on 2010-01-03
I use rhythmbox with streaming audio recorder and equalizer plugins.Very easy to use,just rightckick to record.Check it out:

---

