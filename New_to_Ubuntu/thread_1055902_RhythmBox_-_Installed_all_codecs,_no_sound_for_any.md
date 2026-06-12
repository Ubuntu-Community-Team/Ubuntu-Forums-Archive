---
title: "RhythmBox - Installed all codecs, no sound for anything?"
date: 2009-01-31
forum: New to Ubuntu
---

### Post by UnknownFear on 2009-01-31
I just got all my music from Windows XP to Ubuntu (thanks God! :)) and I had to install a few codecs to get the music to be played in RhythmBox. Now, I installed the codecs, but I don't have sound. I also don't have sound when going on YouTube or anything. Does anyone know how I can fix this? I have a SoundsBlaster soundcard.

---

### Post by methodmarvel on 2009-01-31
> **UnknownFear said:**
> I just got all my music from Windows XP to Ubuntu (thanks God! :)) and I had to install a few codecs to get the music to be played in RhythmBox. Now, I installed the codecs, but I don't have sound. I also don't have sound when going on YouTube or anything. Does anyone know how I can fix this? I have a SoundsBlaster soundcard.

Just a guess but I'm wondering if you have the problem I have - double click the sound icon in the top right corner and put the sliders for "PCM" up - also make sure "Master" is up (but I'm sure you have)

For some reason on my dell laptop Master controls tone and PCM controls volume - go figure...

---

### Post by UnknownFear on 2009-01-31
I have everything set to MAX, but still no sound. I have a CREATIVE EMU10K1 SSB0220 sound card. I got to working months ago, but I don't know how to get it working.

---

### Post by carml on 2009-01-31
Check if you disabled the audio by a combination like Fn + a key(it is present on all notebooks),then if the first check it's false,control if the entry headphone is cheched,you can find that under the speaker icon,right click ther,then Open Volume Control->Switchs. :)

---

### Post by UnknownFear on 2009-01-31
I found a solution by killing pulse audio and forcing alsa to load, but I have to do it everytime I restart my computer.

```

sudo killall pulseaudio

sudo alsa force-reload

```

---

### Post by transmition on 2009-01-31
Well, while I am sure there is a cleaner way of doing this, if you want to save yourself the hassle of typing those commands every time you login, you can add them to your startup.

So, go to System--> Preferences --> Sessions and add your commands to the list of startup items. That way the process will be automated for you.

---

### Post by UnknownFear on 2009-01-31
Yes, but I hate doing that. It slows my computer down so much. And, I tried it, and it won't even play sound anymore!! I don't get why this is so hard to fix. I've tried everything and yet still no sound. There has to be a better way to get sound working.

---

### Post by transmition on 2009-01-31
Do you get sound when you plug in headphones? (Try both the headphone jack in your speakers and on the computer itself)

---

### Post by UnknownFear on 2009-01-31
I don't have a seperate headphone jack, only speakers.

---

### Post by transmition on 2009-01-31
> **UnknownFear said:**
> I don't have a seperate headphone jack, only speakers.

That is odd, are you on a laptop or desktop? Regardless, there should be a headphone jack right next to a microphone jack. If your speakers are plugged into the headphone jack, unplug them and then try with your headphones. Your problems may be with the speakers, so this allows us to confirm what exactly the problem is.

---

### Post by cmay on 2009-01-31
> **UnknownFear said:**
> I have everything set to MAX, but still no sound. I have a CREATIVE EMU10K1 SSB0220 sound card. I got to working months ago, but I don't know how to get it working.

i have a emu 1010m and i get it working by installing the alsa firmware loader packages. they are restricted i seem to remember so it took me a while to figure out where to get the drivers for them . in fact i was disapointed at ubuntu studio for not installing these drivers at the initial installtion when i get the drivers using debian etch or 64studio. i guess the sound card you have uses the same package to install the drivers as mine does. 
the package is found in synaptic. no need to compile anything or load anything. just install the package and reboot.  
hope it helps out.

---

### Post by UnknownFear on 2009-01-31
YES! I got my sound to work. I messed around with the settings and I put everything to SB Live 5.1 [SB0220], Sound caprture to ALSA and Device to SB Live 5.1 [SB0220] (Alsa mixer) and it works! YAY!!! Thanks for the help!

EDIT: How do I mark the thread as "Solved"? I know I have to edit the title, but how do I do that?

---

### Post by methodmarvel on 2009-01-31
> **UnknownFear said:**
> YES! I got my sound to work. I messed around with the settings and I put everything to SB Live 5.1 [SB0220], Sound caprture to ALSA and Device to SB Live 5.1 [SB0220] (Alsa mixer) and it works! YAY!!! Thanks for the help!

EDIT: How do I mark the thread as "Solved"? I know I have to edit the title, but how do I do that?

the solved feature has been removed - something to do with it being database demanding

---

