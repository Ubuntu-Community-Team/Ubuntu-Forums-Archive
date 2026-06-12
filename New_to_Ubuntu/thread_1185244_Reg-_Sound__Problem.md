---
title: "Reg:- Sound  Problem"
date: 2009-06-12
forum: New to Ubuntu
---

### Post by halovivek on 2009-06-12
Hi
I have installed ubuntu and it is doing well. but the output of the laptop speaker volume is very low. I dont know how to probe and to make more volume. I tried the volume increase and all but still low volume output. In windows it is good. 
Any suggestion and help please

---

### Post by allenbradley on 2009-06-12
Hello! I did this :
(1) Click on the sound icon in the top right of your screen.
(2) Open volume control 
(3) You will see options to increase the master, PCM and front volume. Make sure they are maxed out.
(4) Try playing a file now.

Does it help?

---

### Post by bennachie on 2009-06-12
This is a well-known bug in the PulseAudio system, which has been the subject of much, sometimes, heated debate. Matters have reached such an extent that the recently-released Fedora 11 includes a nice GUI to work around the problem and, perhaps somewhat tongue-in-cheek, invites each user who has had to make use of the facility to raise a fresh bug with the embattled PulseAudio developers.

You can achieve exactly the same result in Ubuntu by opening a terminal window and typing "alsamixer -c0" (without the quotation marks) at the prompt. You'll be presented with a rather old-fashioned preference pane which allows you manually to adjust the underlying volume settings for each relevant device. A coloured bar shows the existing settings.

Navigate between the devices using the left and right arrows, and use the up arrow to set each of them to 100%. Keep working your way to the right until you are certain you have adjusted the settings on all available devices (the last one is often the most critical). 

Once you've finished, close the terminal window and enjoy the music.

---

### Post by gastly on 2009-06-12
Maybe this would help: [http://ubuntuforums.org/showthread.php?t=1043568](http://ubuntuforums.org/showthread.php?t=1043568)

---

