---
title: "Microphone"
date: 2009-10-14
forum: New to Ubuntu
---

### Post by nothilaryy on 2009-10-14
So I installed Ubuntu netbook remix on my hp netbook a little while ago, but before doing so I forgot to check if there is an internal microphone. According to the system specs from where I bought it, there should be, but I'm not sure if that is the exact product I bought, or an approximation. I've tried simply talking and trying to get it to record something without any clue of where it might be or if it is turned on but that has proved to be quite fruitless. So I suppose my questions are three-fold:

[LIST=1]
[*]How can I check to see if I physically have a microphone?
[*]If it turns out I do how can I turn it on and configure it to work?
[*]If it turns out I do not have a microphone, would I need to do anything special when buying a headset so I can record stuff?
[/LIST]

Thank you so much! Let me know if there is more information that you need.

---

### Post by laidback on 2009-10-14
Try Sound Recorder..it's in Applications>Sound & Video>Sound Recorder. Is installed by default so you should have it. When you record something, by pressing record, you need to SAVE it after you stop in order to replay it. I save mine to the desktop.

Now you may need to adjust you settings too. Go to top right and press the Speaker Icon. A small window will appear with "Volume Control..." in it. Press Volume Control and you'll be presented with another window running Alsa Mixer. In here you can activate/adjust the settings of your sound system. If you cannot see the device you need, in this case mic or front mic, press preferences and activate as required. Make sure you have the device active, no red cross at the bottom of the slider, and set the volume quite high. Now try and record.

"Input" on my system is simply the default Capture, I've never seen any other options, it picks up my mic OK

I don't have an internal mic, mine plugs into a socket on the sound card at the back of the PC. These sockets are normally small jack plugs with a pink surround. I believe that you can get a USB mic but I don't know how Ubuntu will handle these.

---

