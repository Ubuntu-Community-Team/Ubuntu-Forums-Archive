---
title: "Headphone with mic dont/wont working!"
date: 2009-07-18
forum: New to Ubuntu
---

### Post by Lollating on 2009-07-18
Hi guys,

I got a brand new Creative HS-400 Headset with MIC.
But it wont work!

PLease reply I use Audacity to record becuase im working on a Podcast

THANKS!!

---

### Post by Lollating on 2009-07-18
Cmon!

PLEASE HELP ME!!

:(:(:(

---

### Post by 311005901 on 2009-07-18
Do you have sound through regular speakers?

---

### Post by 4Orbs on 2009-07-18
I use a different brand of headset, but I suspect the problems I encountered apply in other situations.

1. Even at full volume (computer volume slider at max and PCM slider at max) I could only slightly hear any audio through the headphones. I now use an external headphone amplifier in order to hear the audio at acceptable levels.

2. The microphone works properly, but I didn't know until I was able to hear the audio after using the external headphone amp.

3. I'm sure you are aware of the inline (on the headphone wire) volume and mute control.

---

### Post by Risoh on 2009-07-18
the problem might be Pulseaudio which is default in Jaunty jack. (9.04)

here is forum explaining why that could be a problem:
[http://forum.audacityteam.org/viewtopic.php?f=14&t=3541](http://forum.audacityteam.org/viewtopic.php?f=14&t=3541)

try ALSA or OSS System -> Preferences -> Sound

Check the audacity forum to see whats the best.

---

### Post by Risoh on 2009-07-21
I find this on [Pulseaudio web]("http://www.pulseaudio.org/wiki/PerfectSetup"):

> Audacity 

Audacity has now been packaged with a proper "alsa: pulse" device listed, in a ppa for ubuntu intrepid. See [https://launchpad.net/~diwic/+archive](https://launchpad.net/~diwic/+archive)

The following is information for versions without the pulseaudio patch:

Audacity doesn't support PulseAudio, nor Esound for the moment. You'll have to kill or suspend pulseaudio before you use this application. Audacity uses the PortAudio cross-platform Audio API which doesnt support pulseaudio. Some work was started on making portaudio support PulseAudio but this does not appear to be under active development currently and does not work in it's current state.

Audacity can use OSS for sound input and sound output. By changing the 2 settings in preferences to /dev/dsp, and running audacity as

```
padsp audacity
```

you route OSS sound through pulseaudio and can have successful playback and recording with audacity. You could also set the sound input to be ALSA which (for regular users) is less likely to be blocked by another application, as recording with multiple applications at once is less commonly done

Using pasuspender to momentarily suspend pulseaudio is another way to use Audacity.

```
pasuspender -- audacity <argument>
```


I think that its worth trying it in Jaunty.

---

### Post by uberlube on 2009-07-21
youll prolly have to set up an .asoundrc file. theres lots of documentation and chat about it.

---

