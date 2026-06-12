---
title: "microphone for skype"
date: 2010-04-11
forum: New to Ubuntu
---

### Post by dannylee25 on 2010-04-11
hello i have a acer aspire 5720-4171 
and my skype microphone dosent work how can i fixit

---

### Post by grobar87 on 2010-04-11
Me too...same problem on dell vostro a860 laptop.

---

### Post by kleskjr on 2010-04-11
does your microphone work or the problem is just with skype?(you can try to record a sound to check it).

if you can record a sound, then go to the skype options->sound devices and there is an option 'Allow skype to automatically adjust my mixer levels' (or smth similar). Uncheck it!
then you will be able to choose the volume of the input device in 'Sound preferences' (top right in your main panel).
good luck

---

### Post by Azrael3000 on 2010-04-11
Hi.
When I started out with Ubuntu I had the same problems on my Acer Travelmate.

Check out the old thread. If it doesn't work let us know.
[http://ubuntuforums.org/showthread.php?t=1181130](http://ubuntuforums.org/showthread.php?t=1181130)

Br,
Arno

---

### Post by dannylee25 on 2010-04-11
> **kleskjr said:**
> does your microphone work or the problem is just with skype?(you can try to record a sound to check it).

if you can record a sound, then go to the skype options->sound devices and there is an option 'Allow skype to automatically adjust my mixer levels' (or smth similar). Uncheck it!
then you will be able to choose the volume of the input device in 'Sound preferences' (top right in your main panel).
good luck
    
i think it might be the mic because on test call i cant hear mi own voice
:confused::confused::confused::confused:

---

### Post by Azrael3000 on 2010-04-11
by recording a sound he meant go to applications > sound & video > sound recorder. Try if you get something there.

---

### Post by phibxr on 2010-04-11
> **dannylee25 said:**
> hello i have a acer aspire 5720-4171 
and my skype microphone dosent work how can i fixit

What kind of microphone is this? USB-headset, or simply something you plug into your microphone-jack in your computer?

---

### Post by lidex on 2010-04-11
[http://www.google.com/search?q=skype+microphone+not+working&sitesearch=ubuntuforums.org]("http://www.google.com/search?q=skype+microphone+not+working&sitesearch=ubuntuforums.org")

---

### Post by 3rdalbum on 2010-04-11
In Skype, the audio input and output should be 'Pulseaudio'. If it is, then right-click on the volume control on the panel and go to Sound Preferences. Set your microphone on the Input tab.

---

### Post by dannylee25 on 2010-04-12
> **phibxr said:**
> What kind of microphone is this? USB-headset, or simply something you plug into your microphone-jack in your computer?

the mic is a built in 1 as well as a built in camera

---

### Post by mastablasta on 2010-04-12
Mic or complete headset with mic is cheap.
 
also make sure your mic is not muted.

---

### Post by Azrael3000 on 2010-04-12
> **Azrael3000 said:**
> by recording a sound he meant go to applications > sound & video > sound recorder. Try if you get something there.

Sorry but can you try this? It would help us figuring out where things go wrong (at Skype or Ubuntu level).

---

### Post by dannylee25 on 2010-04-12
> **Azrael3000 said:**
> Sorry but can you try this? It would help us figuring out where things go wrong (at Skype or Ubuntu level).

i did it didnt work

---

### Post by tehowe on 2010-04-12
On my Acer Aspire 1410 (the newer, netbook-sized one) I can record a sound file using Sound Recorder but there is no input to Skype through PulseAudio. I've tried both letting Skype control input levels and not.

This is on Lucid Lynx Beta 2. Beta 1 seemed to work just fine.

---

### Post by Azrael3000 on 2010-04-12
can you post the output of:
```
lspci | grep Audio
```

tehowe: check [http://ubuntuforums.org/showpost.php?p=7434632&postcount=3](http://ubuntuforums.org/showpost.php?p=7434632&postcount=3) if you can't figure it out maybe open your own thread since we have two different issues here

---

### Post by mlichtenstein2 on 2010-04-17
I have Ubuntu 8.0.4 with a Sony Vaio.
I did not get my internal mike working with the sound recorder 
or with Skype. Therefore I bought a cheap external mike and did the following to make it work:
System->Preferences->Sound

Sound Events
Sound playback: Autodetect

Music and Movies
Sound playback: Alsa- Advanced Linux Sound

Audio Conferencing
Sound playback: Autodetect
Sound Capture: Alsa- Advanced Linux Sound

Test with Applications->Sound & Video->Sound Recorder
Record from input is set to capture.
Set Record as: voice, lossless wav audio

$ alsamixer 

has Playback: Capture

After that worked, I went to Skype and tested the microphone with the test
call and it worked.

Good Luck

---

