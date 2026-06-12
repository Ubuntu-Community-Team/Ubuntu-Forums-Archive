---
title: "how to change resolution ubuntu 9.10"
date: 2010-04-19
forum: New to Ubuntu
---

### Post by blizta on 2010-04-19
hi everybody.........:P

i recommend my friend to use ubuntu 9.10 in his laptop. so, we try with live cd. But, the resolution didn't match with the screen ( the icon too big and blur)

when i try 
system>preference>Display

there are just two options 

640 x 480 

and 

800 x 600


how do i change to 1024 x 768???

---

### Post by cascade9 on 2010-04-19
Probably the video card drivers arent installed. Go to-

System-> Administration-> Hardware Drivers.

---

### Post by dwarfolo on 2010-04-19
If those are the only two resolutions you can choose from, then there's a good chance that your graphics card isn't supported by the vesa framebuffer.
To see more resolutions available you must use a specific driver for your card.

---

### Post by blizta on 2010-04-19
thanks, but how do i search and install video card drivers. 

when i installed ubuntu, i even don't need any driver for my laptop.... :)

and no problem with the resolution

---

### Post by dwarfolo on 2010-04-19
Follow casacade9 suggestion. If your card is supported this is the preferred way to find and install the driver.
If this doesn't work you can try to search the website of the manufacturer of the video card and see if it has a driver for linux.

---

