---
title: "Skype - Problem With Audio Playbck"
date: 2009-06-25
forum: New to Ubuntu
---

### Post by DaveySpeedstar on 2009-06-25
Hi

I'm using 32bit Jaunty 9.04, and want to use Skype, However whenever I try to connect I get the message above (Problem with Audio Playback) and the window closes down.

I've tried changing the audio setting from Alsa to Pulse, checked all the connections, and tried shutting down and re-starting, however nothing seems to work.

The Skype site says that another application might be using all the sound-cards resources, but this can't be the case, as nothing else is open when I'm doing all this.

Obviously I'm missing something I just don't know what - Help!!! :confused:

---

### Post by antikristian on 2009-06-26
First of all, do you have sound in other applications?

Have you tried changing the skype settings? You can locate the settings menu by right-xlicking the skype icon in the taskbar, and selecting options. Then go to "Sound Devices" and make sure "sound out" is set to pulse

If that does not work, check your sound settings in system->settings->audio(or sound) and make sure that the playback device that is selected, and works (there's a test button) is equal to the one set in skype.

---

### Post by earthpigg on 2009-06-26
changing everything in skype's 'sound devices' to 'pulse' did the trick for me

---

### Post by antikristian on 2009-06-26
> **earthpigg said:**
> changing everything in skype's 'sound devices' to 'pulse' did the trick for me

You might have problems with sound recording (sound in) by doing it that way, if it works than it's great, but let me know of you still have any problems

---

### Post by DaveySpeedstar on 2009-06-26
> **antikristian said:**
> Have you tried changing the skype settings? You can locate the settings menu by right-xlicking the skype icon in the taskbar, and selecting options. Then go to "Sound Devices" and make sure "sound out" is set to pulse

That did the trick - thanks very much :D

---

