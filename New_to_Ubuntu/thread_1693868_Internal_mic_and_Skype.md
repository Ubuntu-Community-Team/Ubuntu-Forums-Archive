---
title: "Internal mic and Skype"
date: 2011-02-23
forum: New to Ubuntu
---

### Post by Awesome96 on 2011-02-23
I've tried searching around but I haven't found anything.
I downloaded Skype from Skype's website, to be specific Skype for linux; beta 2 64 bit.
The problem is that Skype doesn't seem to detect my internal microphone (or speakers is seems?) however the speakers work, not the microphone, the only choices it gives me for microphone, speakers and ringing is PulseAudio server (local).
How do I fix this? :confused:

---

### Post by markjwarren on 2011-02-23
I also am experiencing the same issue.

I have two different webcams with mics built in as well, same results ? Logitech/Phillips

Only Logitech works with cheese ?

---

### Post by Awesome96 on 2011-02-24
Really, no one?

---

### Post by coffee412 on 2011-02-24
I have skype installed and using a Logitech 9000 pro. Your mileage may vary but here is what I did:

Install the additional pulseaudio volume control packages (dont remember names, Search 'software center' for pulseaudio) and set your mic up as the input device. 

In skype my setup for devices is pulseaudio for the microphone, speakers and ringing.

coffee

---

### Post by Awesome96 on 2011-02-24
> **coffee412 said:**
> I have skype installed and using a Logitech 9000 pro. Your mileage may vary but here is what I did:

Install the additional pulseaudio volume control packages (dont remember names, Search 'software center' for pulseaudio) and set your mic up as the input device. 

In skype my setup for devices is pulseaudio for the microphone, speakers and ringing.

coffee


I installed the pulseaudio volume control and with it device selection, however, for input devices this is the only one listed: Internal Audio Analog Stereo, and it's controls for front left and front right.  to me it sounds like the internal speakers, however it is already selected and the microphone still doesn't work.

---

### Post by coffee412 on 2011-02-24
> **Awesome96 said:**
> I installed the pulseaudio volume control and with it device selection, however, for input devices this is the only one listed: Internal Audio Analog Stereo, and it's controls for front left and front right.  to me it sounds like the internal speakers, however it is already selected and the microphone still doesn't work.

Sounds like your cam is probably not supported? What cam do you have? I guess thats a starting point.

coffee

---

### Post by jflesher on 2011-05-21
Have you tried this using Pidgin?

Skype in Linux has always been flaky to me, but Pidgin works good; you have to rule out the program first.

---

