---
title: "How to use a Bluetooth headset with Ubuntu"
date: 2009-09-18
forum: New to Ubuntu
---

### Post by r3bol on 2009-09-18
I've managed to pair my BT headset and I selected it as mic and speaker in Skype. I can't hear and noise in the sound test though. I also can't hear audio if I play a regular sound file (the headset supports A2DP).

I've been through the speaker icon > Volume control > Device: (drop down menu) and couldn't see anything that referenced the headset. Skype seems to have an option for it though.

Has anyone had any success using a BT headset with ubuntu? 

Thanks

---

### Post by Kryzzalid on 2009-09-19
Moi:)
I got the BT headset almost working with blueman, bluez and ALSA but the problem is now that the microphone doesn't work at all and the sound is kinda odd! I got the A2DP otherwise working perfectely with Audacious. Well, I haven't really tried with the other players since my goal is to get it work with Skype. Any idea?

for the A2DP simply i wrote in ~/.asoundrc:

pcm.headset {
       type bluetooth
       device 00:0C:78:4F:D2:CE
       profile "auto"
}

bluez-alsa is i think also required.

In Audacious I choose ALSA Output plugin and in the its configuration i wrote **headset** in the audio device box. This only works with ALSA.

---

