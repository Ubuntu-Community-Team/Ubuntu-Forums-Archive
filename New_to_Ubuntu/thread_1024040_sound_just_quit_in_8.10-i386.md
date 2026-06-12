---
title: "sound just quit in 8.10-i386"
date: 2008-12-28
forum: New to Ubuntu
---

### Post by dspisak on 2008-12-28
Hello.  I had the i386 version of 8.10 running just fine.  Citrix Client 10.6 works just fine.  Flash Player 10.0r15 worked just fine.  Then the audio quit.

When I try Sound Preferences/Devices/Sound Events, with Sound playback set on autodetect, this error message is returned:
audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Failed to connect stream: Invalid argument.

When I try PulseAudio/Volume Control/Playback and play a sound file in Rythmbox, or try YouTube in Firefox 3.0.5, Volume control still reads "no application is currently playing audio."  Rythmbox hangs and there is no sound from YouTube.  I tried several How-Tos but they didn't work.

The PulseAudio package is loaded.

Short of reloading 8.10-i386 and starting over are there any suggestions?

TIA

Dan

---

### Post by 2uRcJQ34G1 on 2008-12-28
Check you default plug-in and audio out device settings in System->Prefrences->Multimedia Systems Selctor and make sure they are what you expect them to be. Then check you settings in the System->Prefrences->Sound as well.

---

### Post by dspisak on 2008-12-28
I tried Multimedia S S/Audio.
Output:
ALSA & NVidia CK8S - test tone
OSS - test tone
all other combinations - no tone, or an error message
Input:
Test Sound - test tone
OSS - faint high pitched tone
all other combinations - no tone

As to Multimedia S S/Video,
Output:
all combinations - test pattern shown
Input:
Test Input - test pattern shown
all other combinations - no pattern

So, I set the various Sound Preferences/Devices to NVidia CK8S (OSS)and they all have test tones.  However, there still is no streaming FM radio or YouTube sound.  What next?

---

### Post by 2uRcJQ34G1 on 2008-12-28
1. Do you get sound otherwise, i.e. outside firefox?

2. Try to for the time being set everything to default and auto detect and try again.

---

### Post by dspisak on 2008-12-28
Ah ha.  Since I set sound preferences devices to NVidia CK8S (OSS) I deleted "pulseaudio" only (did not delete the other pulse files).  Now I have streaming FM and youtube audio.

Thank for the tip about Multimedia Systems Selector.  I did not have it loaded.

Now, my only other major problem is getting "encrypted" DVDs to run.

---

