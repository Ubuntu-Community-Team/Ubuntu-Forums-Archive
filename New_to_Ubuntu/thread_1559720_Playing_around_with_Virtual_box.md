---
title: "Playing around with Virtual box"
date: 2010-08-23
forum: New to Ubuntu
---

### Post by cuongjj on 2010-08-23
I was playing around with Virtualbox and installed some distros on it, namely Ubuntu Studio and Linux mint.  Everything went well, however something popped up saying that I have to change the monitor to 32 bit, as I am running on 24 bit.  Does this mean I am running 24bit normally?

Can someone please explain this to me?

After this error, I tried to play around and fix the problem.
System > Preference > Monitors

A dialog pops up and says this:
"It appears that your graphics driver does not support the necessary extensions to use this tool.  Do you want to use your graphics driver vendor's tool instead?"

Clicking yes, It gives me the nvidia x server settings screen..

Graphics card: GeForce 9500 GT
Monitor: Acer X233H 1920x1080

Can someone help me please? Thank you for your time.

---

### Post by uRock on 2010-08-23
Is the host OS Ubuntu? Which release?

---

### Post by cuongjj on 2010-08-23
10.04 LTS desktop version

---

### Post by uRock on 2010-08-23
There should be an Nvidia Settings manager in the System> Administration menu.

---

### Post by cuongjj on 2010-08-23
Yes it does have the settings.  Do you know how I can change it from 24 bit over to 32bit?

X server display Configuration > X screen Tab > The highest Colour depth is 16.7 Million Colours (Depth 24)

:(

---

### Post by uRock on 2010-08-23
That is the same setting which my system is at. When you got the error, would it let you run the VBox after clicking OK?

---

### Post by cuongjj on 2010-08-24
Yes it does let me go through with the installation. However I was just wondering if its normal for me to run on 24bit thats all.

---

