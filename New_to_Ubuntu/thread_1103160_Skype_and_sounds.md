---
title: "Skype and sounds"
date: 2009-03-22
forum: New to Ubuntu
---

### Post by Skol312000 on 2009-03-22
skype says that it cant connect me to voice becasue i dont know how to set up my sound in/out/ and stuff up...i have a hp pavilion dv5

and i dont know whch ones will work where  for sound in and out...if anyone knows anything please help

---

### Post by M4rotku on 2009-03-22
I might be able to help.  I have an hp dv6 Pavilion.

My sound settings are as follows:

Sound in:  pulse
Sound out: pulse
Ringing:   pulse

Also, to get my mic working, I had to change my input source to:

Front mic

You can access this by right-clicking on your volume control, selecting "Open Volume Control" and choosing the "Options" tab.

If you do not have an "Options" tab, then right click on the volume knob, select "Open Volume Control" and click "Edit" "Preferences" and then check all of the boxes listed.

If this doesn't work, then their is a chance that you might not have your pulse audio stuff set up correctly.

Good Luck :D

---

### Post by ronocdh on 2009-03-22
Have you confirmed whether you're using Pulse, or ALSA, or even OSS or something? Try typing **alsamixer** into a terminal and mess with the levels there, see if that helps you.

If you're using GNOME, you can check pretty easily how things are set by going to the Sound entry in your system conf menu and looking at the pull-down menus there.

---

### Post by Skol312000 on 2009-03-22
i have no idea...i set up all under preferences i checked all boxes and everything but wwhen i did the "test call"  some lady robot told me to speak so it can record and i did and it did not record...i can hear everything  but no one can hear me talk...i have the option for pulse and so i choose that...man...it works fine under windows...but i want it on Ubuntu

---

### Post by huruixd on 2009-03-22
Thank you. I set up the sound in/out to pulse, it works for me.

---

### Post by Skol312000 on 2009-03-22
lucky.....

---

