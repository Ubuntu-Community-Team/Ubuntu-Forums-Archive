---
title: "Ubuntu Vs.  XP  - loudness?"
date: 2009-09-08
forum: New to Ubuntu
---

### Post by complete-linux-noob on 2009-09-08
I have a dual boot set up with XP and Ubuntu Jaunty.


When I start my computer its pretty loud. Its the heatsink fan I guess that contributes the most...


When I boot into XP it quiets down significantly & I can go about using the computer in peace.  

When I boot into Ubuntu however, nothing changes and my computer stays very LOUD for the duration of my use. 


What can I do?

---

### Post by MelDJ on 2009-09-08
lower the volume in volume control

---

### Post by wojox on 2009-09-08
You may want to check System &#8594; Preferences &#8594; Power Management

---

### Post by gradinaruvasile on 2009-09-08
> **complete-linux-noob said:**
> I have a dual boot set up with XP and Ubuntu Jaunty.


When I start my computer its pretty loud. Its the heatsink fan I guess that contributes the most...


When I boot into XP it quiets down significantly & I can go about using the computer in peace.  

When I boot into Ubuntu however, nothing changes and my computer stays very LOUD for the duration of my use. 


What can I do?

What computer u have? Is it a laptop with Nvidia card?

---

### Post by FreewheelinFrank on 2009-09-08
What CPU chip do you have?

A Google search reveals some problems with specific chips, but without knowing what yours is, it's impossible to give advice.

[http://ubuntuforums.org/showthread.php?t=190921](http://ubuntuforums.org/showthread.php?t=190921)

---

### Post by FreewheelinFrank on 2009-09-08
> **gradinaruvasile said:**
> What computer u have? Is it a laptop with Nvidia card?

gradinaruvasile asks a good question. Could be maker-specific. Here's a Sony problem:

[http://ubuntuforums.org/showthread.php?t=75972](http://ubuntuforums.org/showthread.php?t=75972)

---

### Post by theozzlives on 2009-09-08
If you're running 3D effects, that could make the CPU work harder, and get hotter. Resulting in your fans to work harder causing more noise. On one of my older computers (since upgraded) I had to big of a swap file resulting in the system writing to the HD to much, causing more noise. Now I have enough RAM that my system never  uses swap (except for hibernation).

---

### Post by nvdparker on 2009-09-08
I have noticed this too. When I start my PC the chassis fans run at full speed and slow down once Windows XP starts to load. But when I boot into either Ubuntu or Fedora, the fans are at full speed the whole time.

This isn't actually a problem for me as the noise is bearable and the fans can be easily replaced if they break down.

This is my system:

AMD Athlon FX-55 2.4GHz CPU
Corsair 2 x 1GB DDR Memory
ASUS A8N-SLI Deluxe Motherboard
2 x 256MB nVidia GeForce 6800 Ultra VGA Cards (PCI Express)
2 x 74GB Western Digital Raptor SATA HDD (10,000 rpm)
Creative X-Fi Fatal1ty PCI Sound Card (with front console)
LG DVD+/-RW Optical Drive
Zalman CNPS7000-Cu CPU Cooler
SeaSonic 500W Power Supply Unit (nVidia Certified)
Thermaltake Kandalf Case

---

### Post by XCan on 2009-09-08
Are you sure it's the chassis fan only? It feels more like the GPU fans.

---

### Post by 3rdalbum on 2009-09-08
If the fans slow down in Windows, it's because the BIOS is set to run them at full speed, and there's some software in Windows that is scaling them down depending on load.

That's a bit of a daft way of doing it, IMHO, especially if the software crashes. Just go into your BIOS settings and turn on fan control; on Asus motherboards it's called "Q-Fan", yours may have a different name for it. Now your fans will be controlled by the motherboard and will work properly regardless of operating system.

Alternatively, replace your fans with Noctua-branded fans (and if you have an Intel stock heatsink, replace it with a Noctua heatsink), because you can run them at full speed and barely hear them.

---

### Post by complete-linux-noob on 2009-09-10
Hello thanks for replies everybody. About Power management, found nothing there that would help me unfortunately. 

The computer is self-built. Graphic card is Nvidia 9800gtx(+) CPU is Intel E5200 "WolfDale" dual core. And a gigabyte board. It is the first computer I have built. My username should actually be more along the lines of "complete-computer-noob" lol.


As for effects I'm running nothing atm. This is a **brand new install** with nothing set up, no drivers for video, sound, or anything...Havent even gotten on the internet yet.



> **3rdalbum said:**
> If the fans slow down in Windows, it's because the BIOS is set to run them at full speed, and there's some software in Windows that is scaling them down depending on load.

That's a bit of a daft way of doing it, IMHO, especially if the software crashes. Just go into your BIOS settings and turn on fan control; on Asus motherboards it's called "Q-Fan", yours may have a different name for it. Now your fans will be controlled by the motherboard and will work properly regardless of operating system.



I have pretty much all fans with power direct from PSU and they're all on low. Only one I actually plugged into the mobo is the heatsink fan, so that has to be the loud fan that slows down in XP right?  Or it could be the GPU?? 

I will try mesing with BIOS for that specific fan though.  :popcorn:

---

### Post by XCan on 2009-09-10
You should relatively easily be able to figure out which fan makes the noise by opening the case and listening. Sometimes you will have to stop the fans using an appropriate method to pinpoint it exactly. But most of the time, simply listening is enough.

---

### Post by knepig91 on 2009-09-10
you could also check the sound in alsamixer. Terminal: alsamixer

---

### Post by Bartender on 2009-09-10
alsamixer might be able to control fan noise if the fans had a volume setting, but they don't :P

---

