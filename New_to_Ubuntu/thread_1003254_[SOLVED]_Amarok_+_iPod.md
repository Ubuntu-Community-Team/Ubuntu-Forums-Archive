---
title: "[SOLVED] Amarok + iPod"
date: 2008-12-05
forum: New to Ubuntu
---

### Post by benjamin.s.vaccaro on 2008-12-05
I just set up Amarok and I was thinking about how I would import my music. Because music files have such a proclivity for getting incredibly large over time I have mine stored on my external HD and my iPod. For obvious reasons I do not want to turn my external on just to play music so I was wondering if it would be possible for Ubuntu and Amarok to not only recognize iPod and iTunes, but to play the music off an iPod. If Amarok cannot perform this, is there another highly recommended software?

---

### Post by Nano Geek on 2008-12-06
What type of iPod is it?

---

### Post by barbedsaber on 2008-12-06
> **benjamin.s.vaccaro said:**
> I just set up Amarok and I was thinking about how I would import my music. Because music files have such a proclivity for getting incredibly large over time I have mine stored on my external HD and my iPod. For obvious reasons I do not want to turn my external on just to play music so I was wondering if it would be possible for Ubuntu and Amarok to not only recognize iPod and iTunes, but to play the music off an iPod. If Amarok cannot perform this, is there another highly recommended software?

if you don't mind me asking, why don't you just try it and see what happens.
Half the fun of linux is trying new things. (well, not half, and its not really fun, but you get the picture)

---

### Post by benjamin.s.vaccaro on 2008-12-06
iPod 180GB. I'll see what happens.

---

### Post by benjamin.s.vaccaro on 2008-12-06
Okay, after plugging my 180GB iPod in Rhythmbox 0.11.5 recognized it and displayed all the music. Some files were not able to be played. I could also locate it in Amarok 1.4.9.1, however; the artist names are listed as F00, F01 etc. And the song titles are displayed in capital letters "KKUM.m4a" or "KLKG.mp3". They play and when playing the proper information is displayed, but the file name remains "KLKG.mp3".

---

### Post by ColeJayStooks on 2008-12-06
Hey, try this out.

Plug in your iPod and it should mount, right? If you're running Ubuntu (GNOME) then there should be an icon on your desktop saying so. Make sure it's mounted.

Then in Amarok, click *Settings*, then *Configure Amarok*. Click the *Media Devices* tab. Click *Add Device*.

Where it asks, "Select the plugin to use with this device", click the menu and select *Apple iPod Media Device*. Where it asks to enter a name, just give it a name or the iPod's name or whatever.

Then where it asks about the "Mount point" at the bottom, type in where your iPod mounts. For example, mine mounts at /media/, so you need to write out the full address of the iPod. Here's how I did mine:

/media/COLEMAN'S IP/

Because it's case sensitive and stuff. You can check where it's been mounted through the icon on your desktop, the file manager should show you where it is.

Then back in Amarok, go to *Devices* (on the side) and find your iPod profile, then click Connect. Hope that works!

You'll need to unmount through Amarok before unmounting through Ubuntu to get it out too.

---

### Post by benjamin.s.vaccaro on 2008-12-06
Awesome, that does it. Thanks a lot.

---

