---
title: "Something of a sound problem"
date: 2009-05-22
forum: New to Ubuntu
---

### Post by MaxVK on 2009-05-22
I'm using Jaunty (and very good it is too), however I have come across a sound issue that is most annoying:

I have an NVIDIA motherboard that has an on-board *but disabled in the BIOS* sound card.

I have a Creative Live Drive thing, that is used as my primary sound card. Jaunty found this card and set it up and it has so far worked just fine.

**The Problem**
I now want to record via a microphone, however, when I use the Sound Recorder program the playback of any recording is stuttery (kind of watery) and all but useless (Yes, I can understand what was said, but only because I said it!)

I looked at my sound settings (Prefs/Sound) and everything is set to automatic detection except for Sound Capture, which has been set by Jaunty to: *SBLive 5.1 [SB0060] (rev.7, serial:0x80611102) Multichannel Capture/PT Playback (ALSA)*

This would appear to be correct, however, in the selection drop down list for this item, there are another 3 SBLive items, as well as ALSA, OSS and PulsAudio.

I have installed The GNome ALSA Mixer, but the name of the sound card in there is *SigmaTel STAC9708,11*. There is a huge list of scrollers to adjust sound etc, including some like *IEC958 C*, *AC97*, and *Sigmatel* (which is muted)

I have so far tried to plug a (working) microphone into all of the possible SBLive ports, but so far I can only get it to work when it is plugged into the back of the machine, rather than the Live drive at the front.

The results are horrible, and I am far too confused by the multitude of possible settings, to have any idea of exactly what I want to enable and disable etc, to get a nice clean recorded sound.

I don't care where the mic plugs in, just as long as the recorded sound is clean enough to be of any use.

Iv read through several tutorials to get sound cards (including the Live Drive) working, but so far they have been of no help at all, bearing in mind what I'm actually looking at, and the configuration programs/ OS that I am using.

I have now screwed with the settings so much that I can hear my voice through the speakers when I use the mic, and even mute it, but I cant make anything record it.

Can anyone help me please?

cheers

Max

---

### Post by gettinoriginal on 2009-05-22
Have you tried these??  

[http://www.ubuntugeek.com/sound-solutions-for-ubuntu-904-jaunty-users.html]("http://www.ubuntugeek.com/sound-solutions-for-ubuntu-904-jaunty-users.html")

[http://blog.mageprojects.com/2009/03/24/get-your-microphone-working-in-ubuntu-904-and-skype-x64/]("http://blog.mageprojects.com/2009/03/24/get-your-microphone-working-in-ubuntu-904-and-skype-x64/")

---

### Post by MaxVK on 2009-05-22
Thanks gettinoriginal, I have now!

The first link seems to go on a lot, but I already have all the files suggested. The second was informative, but ultimately it made no difference. With a mic plugged in I can hear myself speaking into it, but it wont record a thing.

cheers

Max

---

