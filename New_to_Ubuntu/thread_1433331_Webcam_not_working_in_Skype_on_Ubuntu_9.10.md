---
title: "Webcam not working in Skype on Ubuntu 9.10"
date: 2010-03-18
forum: New to Ubuntu
---

### Post by ramsrambo on 2010-03-18
[SIZE=4][FONT=Lucida Console]My webcam equipment is as follows

Make : Frontech
Model : ecam JIL 2214

When I use gstream-properties and press the test button the webcam works properly. 
By the way this webcam is fully operational with [www.chatroulette.com]("http://www.chatroulette.com")

Problem : 
1. It shows blank with both Skype or Cheese webcam Booth application why? How to fix this ?

2. If I start the gstream-properties the webcam LEDs keeps glowing How to stop webcam?


[/FONT][/SIZE]

---

### Post by N92 on 2010-03-19
In Skype go to preferences - video does it show your web cam there?

---

### Post by no2498 on 2010-03-19
for cheese and skype he needs the preload

---

### Post by ramsrambo on 2010-03-19
> **N92 said:**
> In Skype go to preferences - video does it show your web cam there?
That is where I happen to test for the webcam. In skype Pref ---> options --> I selected enable video and the test button was pressed. The LEDs in the webcam glows up but it shows a blank. No video is displayed

---

### Post by ramsrambo on 2010-03-19
> **no2498 said:**
> for cheese and skype he needs the preload
I am sorry I did understand this preload could you please let me know as to what that would be.

---

### Post by ramsrambo on 2010-03-20
[SIZE=5][FONT=Book Antiqua]I got this problem solved just did a LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype
 at the terminal screen prompt and the video started working[/FONT][/SIZE]

---

### Post by whitone on 2010-03-23
Same solution works for me but I am now trying to 'automate' this by creating a Launcher on the panel. Using the LD_Preload..... command generates the error 'There was an error creating the child process for this terminal'  What do I need to do to correct this ?

Also noted that using the LD_Preload... in a Terminal seems to corrupt something since Cheese crashes thereafter giving   'Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0.'

---

### Post by whitone on 2010-03-23
Same solution works for me but I am now trying to 'automate' this by creating a Launcher on the panel. Using the LD_Preload..... command generates the error 'There was an error creating the child process for this terminal'  What do I need to do to correct this ?

Also noted that using the LD_Preload... in a Terminal seems to corrupt something since Cheese crashes thereafter giving   'Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0.'

---

### Post by manny43 on 2010-03-23
I had the same problem my Logitech Webcam C200 wouldnt work with Skype nor Cheese until i upgraded my integrated video card with e-GeForce FX 5200 PCI

---

