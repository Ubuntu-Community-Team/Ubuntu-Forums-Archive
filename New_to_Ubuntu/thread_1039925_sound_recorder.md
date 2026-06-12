---
title: "sound recorder"
date: 2009-01-15
forum: New to Ubuntu
---

### Post by cosine352 on 2009-01-15
Hi all. Does anyone know how to record my computer sound? I was trying to use sound recorder, but no success. 
thanks

---

### Post by cdtech on 2009-01-15
On a command line use:
```
arecord -D default testrec.wav
```
To playback:
```
aplay -D default testrec.wav
```

---

### Post by cosine352 on 2009-01-15
thanks for replying cdtech. I have tried like you said. But nothing got recorded.

---

### Post by cdtech on 2009-01-15
Do you receive any error messages or does it look like it's recording?

---

### Post by cosine352 on 2009-01-15
> Do you receive any error messages or does it look like it's recording?

looks like it is recording. But the out put file has no sound (size of the file does increase with time of recording though)

---

### Post by syntrichia.ruralis on 2009-01-17
Hey

I've got the same problem. I can record myself in Sound Recorder or Skype, but than i don't hear the recording.

I've got no idea why is it like that, because all the settings seem to be correct and microphone itself is working.

Looking for some help...

---

### Post by cosine352 on 2009-01-19
If someone knows how to resolve this problem please help. 
Here is the issue;
in 'sound recorder' I can not chose mixer as input to record. 

thanks

---

### Post by mjheagle8 on 2009-01-19
sound recorder should work. what settings are you using?

---

### Post by mjheagle8 on 2009-01-19
also, are you using alsa and pulseaudio?  how is your sound system set up?

---

### Post by cosine352 on 2009-01-19
> also, are you using alsa and pulseaudio? how is your sound system set up?

here is my sound setting. I am using Ubuntu8.10. It used to work in 8.04.

---

### Post by mjheagle8 on 2009-01-19
try changing all the alsa mixer settings to pulseaudio. pulseaudio is default in 8.10, so i'm assuming you did an upgrade instead of a clean install.

---

### Post by syntrichia.ruralis on 2009-01-19
I am using ubuntu 8.04 and set sound to work with pulseaudio. 

When I open alsamixer i can see only Master and Capture. Shouldn't i see more things there?

---

### Post by mjheagle8 on 2009-01-19
if you are using pulseaudio for your sound, you shouldnt use alsamixer. you should be looking at your pulseaudio mixer.

---

### Post by syntrichia.ruralis on 2009-01-19
Good to know, thanks :)

I have just one silly question: where is it?! I cannot find it in Sound & Video neither in Sound devices. Does it mean i haven't installed it?

---

### Post by mjheagle8 on 2009-01-20
what are you looking for? the sound recorder?

---

### Post by syntrichia.ruralis on 2009-01-21
I was looking for pulseaudio mixer to check if my microphone is not muted there. 
Actually i think i've found the right thing- pulseaudio device chooser. The problem is it is not muted. I tried to make it as loud as possible and play what i recorded, but i heard just louder noise.

When I check volume meter, the playback part shows nice range of sounds, but recording part stays more less in the same place.
I have absolutely no idea what is wrong...

---

