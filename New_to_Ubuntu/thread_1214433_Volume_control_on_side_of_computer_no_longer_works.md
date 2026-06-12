---
title: "Volume control on side of computer no longer works"
date: 2009-07-15
forum: New to Ubuntu
---

### Post by Jacroe on 2009-07-15
For since I've been using Ubuntu, I've been able to control my volume through the little slide thing on the side of my Acer. The other day, I bought a microphone headset and needed to increase the volume on my microphone input. I opened the Volume control and changed the setting to what I wanted. But now, I can only change the volume by clicking on the volume icon on the status bar and changing it by sliding the bar over. When I do spin the wheel, the little notify bar does come up and it recognizes my input, but fails to change the volume itself. How can I fix this?

---

### Post by hardyn on 2009-07-15
basically its not working because there is driver or handler for the input that you dial device is producing.  now to get it working, you sorta have to figure out how it talks to the computer and then find somebody smarter than me to help you get it functioning, i suspect it will be similar to the special keys on a notebook.  unless somebody has already worked it out how to get it working, you might have to do a bit of digging around the forums.

I know this isn't much help, but hope it gives you a start.

---

### Post by Jacroe on 2009-07-15
> **hardyn said:**
> basically its not working because there is driver or handler for the input that you dial device is producing.  now to get it working, you sorta have to figure out how it talks to the computer and then find somebody smarter than me to help you get it functioning, i suspect it will be similar to the special keys on a notebook.  unless somebody has already worked it out how to get it working, you might have to do a bit of digging around the forums.

I know this isn't much help, but hope it gives you a start.

Well it *has* been working. Just recently it has stopped. I'm new to this and may be a complete idiot (I have before :P ) but it sounds like a config error to me.

---

### Post by lavinog on 2009-07-15
> **Jacroe said:**
> Well it *has* been working. Just recently it has stopped. I'm new to this and may be a complete idiot (I have before :P ) but it sounds like a config error to me.

When you open the mixer, what device is listed as the selected device?
Since you mentioned the microphone, it seems that you would have the capture device selected, which wouldn't be controlled by the volume buttons/slider

---

### Post by Jacroe on 2009-07-22
Alright I got it by changing the settings on my sound. Thanks for everyone who's helped! :D

---

