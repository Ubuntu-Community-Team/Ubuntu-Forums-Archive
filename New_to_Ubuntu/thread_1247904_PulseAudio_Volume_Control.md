---
title: "PulseAudio Volume Control"
date: 2009-08-23
forum: New to Ubuntu
---

### Post by IanCompetent on 2009-08-23
First day with Ubuntu. I love it so far, but no sound. Been through a million different things to try to solve the problem, but nothing. One thing that I have noticed is that the PulseAudio Volume Control has everything on "mute" but will not allow me to turn it off. I'm sure that this means something...

Thanks!!

- Ian

---

### Post by SuaSwe on 2009-08-23
If you go into Terminal and type in 'alsamixer', can you max everything in there?

---

### Post by utnubuuser on 2009-08-23
Here's the link to UbuntuGeeks sound help:> [http://www.ubuntugeek.com/simple-guide-to-sound-solutions-for-hardyintrepid-and-jaunty-jackalope-users.html]("http://www.ubuntugeek.com/simple-guide-to-sound-solutions-for-hardyintrepid-and-jaunty-jackalope-users.html")

---

### Post by IanCompetent on 2009-08-23
I do appear to be able to "max: everything, but I still get no sound.

As for the guide, I've already tried to follow the directions, but have I have an issue when it gets to the part that says: "*Push up the sliders in the volume control and make sure the little speakers do not have little red mute marks on them*." It doesn't tell me what to do if the mute is on or how to turn the mute off. I keep trying to click the mute off, but it doesn't work.

Thanks for your help guys!!

---

### Post by CatKiller on 2009-08-23
> **IanCompetent said:**
> One thing that I have noticed is that the PulseAudio Volume Control has everything on "mute" but will not allow me to turn it off. I'm sure that this means something...

I don't think it does. The PulseAudio volume control show the mute symbol (always) because it's a button that mutes the input/output. When it's enabled, the symbol looks exactly the same, but the button is highlighted and the volume controls are ghosted out. I believe your problem lies elsewhere.

---

### Post by Codix121 on 2009-08-23
It might be your computer, my computer had a similiar issue,
Ubuntu has a lot of sound issues, especially with laptops.
I also had a lot of errors coming from PulseAudio,
I completely removed PulseAudio and "Esound",
Which fixed most of my sound errors and my "one channel" sound issue.

It'd be helpful to know what's the make of your computer.

---

### Post by SuaSwe on 2009-08-24
Try going into System -> Preferences -> Sound and selecting different modes for sound detection. I had an issue where mine wouldn't work on autodetect but worked fine when set to ALSA. You can also test the sound from there and see if you get any errors. :)

---

### Post by Mike3 on 2009-08-24
What sound card do you have?, Please tell us what model it is by typing this into the terminal:

                                            ```
aplay -l
```

---

