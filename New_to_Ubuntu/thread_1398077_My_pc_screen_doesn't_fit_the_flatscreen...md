---
title: "My pc screen doesn't fit the flatscreen.."
date: 2010-02-04
forum: New to Ubuntu
---

### Post by tweety_r78 on 2010-02-04
I have a harddisc (Ubuntu 9.10 I think...) which plays through the flatscreen, and I finally managed to get the sound working by enabling the NIVIDA soundcard. But after rebooting the machine the desktop suddenly went oversized. As a result all of my menus are hidden under the frame of the flatscreen. I've tried to change the resolution in the NIVIDIA panel, but that does not help. Do anyone have any tips on how to fix this...?

---

### Post by nhasian on 2010-02-04
use the controls on your monitor to resize the display area so you can see the entire desktop.  this happens on CRTs when you change the refresh rate on the monitor.  LCDs should auto detect and resize automatically but depending on your brand/model you may need to hit a button on the monitor for it to automagically adjust or you may have to do it manually.

---

### Post by tweety_r78 on 2010-02-04
ehmm.. I'm quite the beginner here, so this may be a stupid question..
I've tried to change the size on the monitor by using the remote for the tv (the picture size button), this didn't help. the only thing that happened was that the image got "cramped" together or stretch out, nothing more of the desktop was made visible...
But is it maybe another function you're talking about...?

---

### Post by Cheezespread on 2010-02-04
I believe he is referring to the buttons on the CRT . If clicked ( Physically pressed) , it gives function options like - Change Vsize or Hsize , Dgauss and all that stuff.Some of them have "Auto-adjust " as well - if I am not mistaken

---

### Post by freak42 on 2010-02-04
if you do not have access to your menubars and you have installed the nvidia driver try:

opening the nvidia utility:

press ALT + F2
then type in the textbox of the window
gksudo nvidia-settings

and enter your password, you can now lower the resolution of your video output to match your tv.

If nvidia-settings is not installed, try:
press ALT+ F2
then type in the textbox of the window:
gksudo apt-get install nvidia-settings

hth!

---

### Post by tweety_r78 on 2010-02-04
Thank you so much for the advices.
I'll try this as soon as I get home.:D

---

