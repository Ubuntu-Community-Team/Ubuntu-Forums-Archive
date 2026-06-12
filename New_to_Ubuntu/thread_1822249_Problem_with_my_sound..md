---
title: "Problem with my sound."
date: 2011-08-10
forum: New to Ubuntu
---

### Post by unaz on 2011-08-10
Hello, i got a problem with my sound as the topic says, the problem is that i get either sound in both headset and speakers or no sound at all. if i choose "Analog output" i get sound from both headset and speakers as i said and if i choose "Analog Headphones" i get no sound from any of them. The speakers are connected at the back of my computer and the headset/headphones at the front of the computer. Got some kind of Intel HDA integrated soundcard on my motherboard. Perhaps it sounds like a smal problem but i want to choose if the speakers or the headphones should sound.

if i type aplay -l in the terminal i get this answer:

**** Lista över PLAYBACK hårdvaruenheter ****kort 0: Intel [HDA Intel],  enhet 0: ALC888 Analog [ALC888 Analog] Underordnade enheter: 1/1  Underordnad enhet nr. 0: subdevice #0kort 0: Intel [HDA Intel], enhet 1:  ALC888 Digital [ALC888 Digital] Underordnade enheter: 1/1 Underordnad  enhet nr. 0: subdevice #0

lspci gives thisr:
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 01)

Feels like my computer know what hardware i got but it aint working as i like. I tried to change hardware profiles but its only Analog Stereoduplex that works.

Im using 11.04 installed with wubi if it matters.

Hope someone knows whats up, ive googled alot but couldnt find anything about this.

---

### Post by mmsmc on 2011-08-10
just a quick suggestion, have you tried plugging the headphones into a different usb jack?

---

### Post by JC Cheloven on 2011-08-10
From where do you exactly choose between outputs? (speakers/headphones).
Did you changed something in "alsamixer" (at terminal) or by some equivalent method?

For this type of integrated intel audio chips, normal behaviour would be speakers getting silent as soon as the headphone jack is plugged in, without need of any adjustement... 

I'm not sure whether the wubi install may have something to do with your problem or not. I'd say not, but I never installed using wubi really.

---

### Post by JC Cheloven on 2011-08-10
> **mmsmc said:**
> just a quick suggestion, have you tried plugging the headphones into a different usb jack?
Does the speakers connect via usb?? 
I thought they were plugged to an input in the soundcard. If it's not the case, please ignore my post above.

---

### Post by unaz on 2011-08-10
They are connected to the soundcard, not USB

I rightclick the speaker icon in the top right corner, choose soundsettings and go to hardware to change hardwareprofiles, as said only analog stereoduplex works, i only use the analog connections so thats fine, havent even tried the digital jacks. if i go to output there is an option as said analog output or analog headphones, analag output plays in both and analaog headphones plays in none...

---

### Post by JC Cheloven on 2011-08-10
> **unaz said:**
> They are connected to the soundcard, not USB

I rightclick the speaker icon in the top right corner, choose soundsettings and go to hardware to change hardwareprofiles, as said only analog stereoduplex works, i only use the analog connections so thats fine, havent even tried the digital jacks. if i go to output there is an option as said analog output or analog headphones, analag output plays in both and analaog headphones plays in none...

Ok, time to check your alsa setings. Please open a terminal and type ```
alsamixer
```
You'll be presented with a semigraphical interface where you'll find controls for "line out", "phones", "spdif", and probably others (maybe not even those, as it depends on the hardware). PLease see if the volume of headphones is set to zero. If so, navigate to it (right-left arrows), and raise the volume (up-down arrows).  

Note.- If you press F1 some help will appear. To exit alsamixer ctrl-C.

---

