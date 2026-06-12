---
title: "Sound Recorder won't record"
date: 2010-03-18
forum: New to Ubuntu
---

### Post by asharpham on 2010-03-18
I can't get sound recorder to record anything. I have a mic plugged into the correct socket but when I click on the record button on sound recorder, nothing happens. The time line for recording is greyed out and doesn't show as available at all. There are no error messages.

---

### Post by I8NY on 2010-03-18
what sound driver are you using?  I use ALSA and i can get the microphone working but if you are using the default plusaudio then i don't know how to help.

---

### Post by ankspo71 on 2010-03-18
Hi,
To get my microphone working with pulseaudio I had to do these steps:

Go to System > Preferences > Sound:
Click on the hardware tab
Choose "Analog Stereo Duplex"
(Duplex means audio in and out)
(Note: to record sound from your sound card, choose "Analog Stereo Output")

Next, install a package called gnome-alsamixer:
```
sudo apt-get install gnome-alsamixer
```

Go to applications > Sound & Video > GNOME Alsa Mixer
When it opens, adjust the Microphone levels, Mic Boost levels, and Capture levels
Microphone = high and not muted, 
Mic Boost = low, 
Capture = high with "rec" enabled
(adjust any as necessary)

That should do it, and I hope this helps.

PS. If you have multiple mic ports, use the ones connected directly to the sound card in back, because I don't think my front ones are working with Ubuntu. Just thought I would mention that.

---

### Post by asharpham on 2010-03-19
Thanks guys. I installed ALSA as suggested but when I opened the Gnome Alsa Mixer the only items showing were Master, PCM, Capture & Mux. No mic inputs are shown. Nevertheless, sound recorder is now working! Now I just need to get Audacity working!

---

