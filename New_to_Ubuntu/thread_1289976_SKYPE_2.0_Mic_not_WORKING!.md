---
title: "SKYPE 2.0 Mic not WORKING!"
date: 2009-10-13
forum: New to Ubuntu
---

### Post by appoloin on 2009-10-13
In option i can only select pulse but my mic not working.
i tried changing things in  sound control and making sure its not muted and max level still nothing

HelLLP!! PLEASE!!!

---

### Post by anewguy on 2009-10-13
In the Skype options for sound devices, try turning off the option for letting Skype control your mixers.  If it is already off, try turning it on.

Had a similar problem quite a long time ago myself, but I don't use Skype right now so I'm not positive but I think that was the problem with mine.

Dave :)

---

### Post by s.fox on 2009-10-13
Hello,

Can you tell us which make and model web camera you have?  Is it inbuilt into a laptop?   

You may also want to have a quick look on [here ]("https://wiki.ubuntu.com/HardwareSupportComponentsMultimediaWebCameras")too.  Please post back :)

-Silver Fox

---

### Post by laidback on 2009-10-13
I've just installed Skype in 9.04 and had similar problems. Here are my Skype settings that have worked on 2 machines, both running 9.04:-

Sound In   HDA NVidia (hw:NVidia,0)
Sound Out  Pulse
Ringing    Pulse

I have allowed Skype to automatically adjust mixer levels.

But you may also need to activate/increase the volume on your mic. Top right of your desktop is the volume control. Drop it down and you'll see a button called "Volume Control...", press that and you'll see "Alsa Mixer". Now depending what's on display you may see controls for mic, or front mic. You need to activate the appropriate one by clicking on the speaker button at the bottom in order to remove the red cross symbol. Also adjust the volume up towards maximum.

Should controls for mic not appear go into Preferences and activate it by putting a cross in the appropriate box. Now proceed as above.

I tested my mic by using "Sound Recorder" which is in Appications>Sound and Video. Remember that you have to SAVE a recording to be able to play it back.

---

### Post by MrWES on 2009-10-13
> **Silver_fox_ said:**
> Hello,

Can you tell us which make and model web camera you have?  Is it inbuilt into a laptop?   

You may also want to have a quick look on [here ]("https://wiki.ubuntu.com/HardwareSupportComponentsMultimediaWebCameras")too.  Please post back :)

-Silver Fox

This site is more up-to-date:
[http://www.quickcamteam.net/devices]("http://www.quickcamteam.net/devices")

~Bill

---

