---
title: "New beta version of Skype records static from my mic"
date: 2009-10-25
forum: New to Ubuntu
---

### Post by diablo75 on 2009-10-25
I just replaced my older version of Skype (2.0 something) with the newer 2.1 beta version.  In the old version I had to pick between a handful of recording devices (what they actually are was very unclear and it was hit or miss before finding the right one to make it work right).  Now all I have for a selection is "PulseAudio Server (Local)" and nothing else.

When I do a Skype test call, the playback of the recording sounds like utter static.  I have no idea how to fix this.

---

### Post by Arla on 2009-10-25
Unfortunately I have the same issues, can you record in sound recorder? Pulseaudio doesn't seem the best (to me) but it may be better than whatever else was out there.

---

### Post by laidback on 2009-10-25
I've just installed Skype in 9.04. Here are my Skype settings that have worked on 2 machines, both running 9.04:-

Sound In HDA NVidia (hw:NVidia,0)
Sound Out Pulse
Ringing Pulse

I have allowed Skype to automatically adjust mixer levels.

I am using a mic plugged into the pink jack of my sound card and headphones/speakers into the black socket.

If you use USB a friend has just told me that different settings were needed (webcam + mic).

I'm using Skype 2.0.0.7

But you may also need to activate/increase the volume on your mic. Top right of your desktop is the volume control. Drop it down and you'll see a button called "Volume Control...", press that and you'll see "Alsa Mixer". Now depending what's on display you may see controls for mic, or front mic. You need to activate the appropriate one by clicking on the speaker button at the bottom in order to remove the red cross symbol. Also adjust the volume up towards maximum.

Should controls for mic not appear go into Preferences and activate it by putting a cross in the appropriate box. Now proceed as above.

I tested my mic by using "Sound Recorder" which is in Applications>Sound and Video. Remember that you have to SAVE a recording to be able to play it back.

---

### Post by Jazzy_Jeff on 2009-10-25
I have the same problem with the beta of Skype, I had to switch back to an older version. It is a bug on their part.

---

### Post by diablo75 on 2009-10-25
> **Jazzy_Jeff said:**
> I have the same problem with the beta of Skype, I had to switch back to an older version. It is a bug on their part.

I'm going to do the same.

---

