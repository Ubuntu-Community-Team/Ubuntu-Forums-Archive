---
title: "Downloading pics from Digital Camera"
date: 2009-03-31
forum: New to Ubuntu
---

### Post by mllelinotte on 2009-03-31
i am trying to find a way to download pictures from my digital camera.

i have installed the digital camera program that came with Ubuntu.
It recognizes the camera but says there are no files on it to download.

i also installed gthumb. When trying to access the camera that way
this is the error message:
"An error occurred in the io-library ('Could not claim the USB device'): Could not claim interface 0 (Operation not permitted). Make sure no other program or kernel module (such as sdc2xx, stv680, spca50x) is using the device and you have read/write access to the device."

i have a Sony Cyber shot digital camera.

Anyone know how to make this work?

thanks

---

### Post by _Purple_ on 2009-03-31
Are you using Edgy - 6.10?

---

### Post by mllelinotte on 2009-03-31
i dont know. i have only had Ubuntu a few days. So i am not sure what that is...
i have not installed anything by that name.

---

### Post by leonardo_neo on 2009-03-31
When you plug in your camera, does it mount the camera memory card?? (you will get a camera icon on your desktop)

If yes, then when gthumb opens by default, and asks for permission to import pictures from camera, then deny that, and close gthumb. Then double click the camera icon, go the the folder/pics which you want on your computer, and copy and paste that on your computer.

This works with me, hope should work with you too.

---

### Post by mllelinotte on 2009-03-31
No the computer does not recognize the camera. No icon appears. no way to access it at all. Both programs do not recognize it either. As far as my computer is concerened there is no Camera.

---

### Post by abn91c on 2009-03-31
are you using **[COLOR="Red"]F-Spot[/COLOR]**?

---

### Post by philinux on 2009-03-31
> **mllelinotte said:**
> i am trying to find a way to download pictures from my digital camera.

i have installed the digital camera program that came with Ubuntu.
It recognizes the camera but says there are no files on it to download.
i have a Sony Cyber shot digital camera.
Anyone know how to make this work?
thanks


Which version of ubuntu are you using.

---

### Post by mllelinotte on 2009-03-31
F-Spot is like the others. 
The F-Spot error reads:
 "Could not claim the USB device while connecting to Camera."

---

### Post by _Purple_ on 2009-03-31
Applications> Accessories> Terminal

Can you please type the following in your terminal and paste the output here?

```
lsb_release -a
```


This will show which version of Ubuntu you are using.

---

### Post by CRIMPS on 2009-03-31
Also, what brand of camera are you using?  I know there were some issues with Sony's proprietary memory cards.

---

### Post by _Purple_ on 2009-03-31
CRIMPS, he mentioned its Sony Cybershot.

---

### Post by mllelinotte on 2009-03-31
my camera is a Sony Cyber-shot DSC-W55 

and i am running ubuntu 8.10

---

### Post by CRIMPS on 2009-03-31
I swear I read through the original post twice to find the brand of camera. :(

Yeah, that is probably the problem.  Sony uses Proprietary media/drivers and will not release the necessary info to developers, I believe.

Im sure there is a valid workaround until you decide to upgrade your camera to a different brand ;)  We love our new Panasonic Lumix! :)

---

