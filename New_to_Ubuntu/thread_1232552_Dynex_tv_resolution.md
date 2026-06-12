---
title: "Dynex tv resolution"
date: 2009-08-05
forum: New to Ubuntu
---

### Post by kevindubrow on 2009-08-05
Hey, I have a Dynex tv that I am using as a computer monitor. I can't get Ubuntu to display a resolution greater than 800x600. There is a portion of the right screen that isn't being used and part of the right side of the display is cut off.

Its a Dynex 22" class: 22 inch tv, 16:9 aspect ratio, max resolution of 1366 x 768, 720p.

Is there any way I can force Ubuntu to give me a higher resolution? I would tell you what video card I have, but I can't seem to find an answer online. I have a Dell Dimension 4500 and for some reason I want to say that it has a Nvidia Geforce 4.

Thank you in advance for the help!

---

### Post by kevindubrow on 2009-08-05
I just figured out that I have a GeForce4 MX 420.

Ubuntu told me that it was recommended that I install the Version 96 Nvidia accelerated graphics driver. I installed it and did a reset, afterwards the whole screen did display on the monitor without being cut off, but I still have a really low resolution. The new video manager program that Nvidia uses does not let me increase the resolution either. Does anyone have any ideas? Thanks!

---

### Post by kevindubrow on 2009-08-13
Hey, I just wanted to bump this. I could really use some help with my problem. Thanks.

---

### Post by wizard10000 on 2009-08-13
I did some checking, Kevin -

Your TV has composite, component, s-video and HDMI inputs.  Your video card doesn't have a DVI output and your TV doesn't have a VGA input.

Best resolution you're gonna see over s-video is 800x600 - the interface isn't designed for a resolution higher than that.

Your best options -

1.  Replace the video card with something that's got a DVI output so you can use a DVI --> HDMI cable or a DVI male to HDMI female adapter and a real HDMI cable.  Figure $35 or so for a GF6200 card and about $7 for a DVI-HDMI cable.  I have this setup driving a 50" 1080p set under Jaunty - works fine.

2.  Use your existing video card and get a VGA to component video cable - it's got a VGA plug on one end and RGB RCA plugs on the other.  Should be around $20.

Anyway, if you have $45 plus shipping or so, pick option 1.  You're not gonna be able to get to where you wanna be without buying some hardware.

Hope this helps -

---

### Post by kevindubrow on 2009-08-15
Hey, maybe I have the wrong tv model, but my tv does have a VGA output. I'm using a VGA cable between the desktop and the tv.

This computer ran Windows at some point and I got a very high resolution to work so I'm not sure if its a hardware problem unless something happened to the video card.

I really appreciate your reply, I'm having a lot of trouble with this issue.

---

### Post by kevindubrow on 2009-08-18
Sorry about bumping this thread again, but I have still not found a way to fix this issue.

Just in case, ill sum up my issue here:
I installed Ubuntu on my Dell Dimension 4550, but I had low resolution and the right side of my screen was cut off. 

Later, I installed the GeForce4 MX 420 driver and the screen was no longer cut off, but the resolution was still low. 

When this computer ran Windows, I was able to get a much higher resolution... 1200-ishx700-ish. Hah, sorry I don't remember exactly what it was. Anyway, that leads me to believe that I'm not having a hardware problem.

I am connected to a Dynex tv through a VGA cable.

Oh, and just to make sure that this wasn't a hardware issue, I plugged in a 15 inch computer monitor and I had no resolution issues.

Thanks in advance for any help!

---

### Post by kevindubrow on 2009-08-20
Ok, well this will be the last time I bump this topic. 

To anyone reading this: Could you maybe suggest somewhere that would be better to get a solution to my issue? Thank you!

---

### Post by rjs1064 on 2009-08-20
i had a similar sounding problem with my old monitor and had to add hsync  and rsync values to the xorg conf file. i can't remember exactly how i had to do it but put screen resolution into search at the top of this page

---

### Post by kevindubrow on 2009-08-20
Ok, thank you so much for your reply! I'll see what I can find.

---

