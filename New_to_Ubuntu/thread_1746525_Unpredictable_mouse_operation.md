---
title: "Unpredictable mouse operation"
date: 2011-05-01
forum: New to Ubuntu
---

### Post by iowabeakster on 2011-05-01
I have been having strange mouse issues.  Sometimes it is so bad it is unusable, other times it is just annoying.  If it is particularly bad, a reboot usally gets things working... or at least better.

It's a basic Logitech USB optical mouse.  I have tried switching USB ports.  My computer is a Dell optiplex gx620 mini tower. 

The symptoms are varied and inconsistent, and do not seem to related to the mouse itself.  It definitely feels like it a software issue:

-sometimes left click does not work
-sometimes the right
-grabbing and dragging windows around sometimes won't work
-sometimes the scroll wheel does not scroll, it changes font sizes
-highlighting and copy/pasting can be nearly impossible at times, due to erratic operation
-to get a drop-down menu, sometimes a right click will work, other times I need to hold the right button or the menu disappears before a selection is made

I recently upgraded to 10.10 Xubuntu--64 bit(formerly 10.04 Xubuntu--64 bit).  One of the primary reasons for switching was I was hoping this mouse problem would go away.  It has been the same with both versions.

I want to try some other driver, but don't know how to switch.  I think I need to edit an xconfig file, but I have no idea how, or what drivers there are to try.  The driver as always been automatically chosen at the install of the OS.  

Thanks

---

### Post by Artemis3 on 2011-05-01
Those sound like the wire is damaged, test a second mouse. And don't use a surface that can shine.

---

### Post by iowabeakster on 2011-05-01
I am sure that there would be other mouses that will work fine, but that doesn't help me with the one I have.

The movement of the mouse is always fine.  And the buttons and wheel work reliably, it just that the actions performed are... unpredictable.  Which makes me think the wire is OK.  I'm usually pretty good at trouble shooting actual hardware issues.  

The first two symptoms that I listed "button does not work" were poorly described.  My bad.  They work (things are highlighted, the system responds) it's just the response is totally unpredictable.   That is why I want to try a different driver.

p.s.  I just spent 3-4 minutes trying to copy/paste one sentence in this response... and gave up.:confused:

---

### Post by iowabeakster on 2011-05-13
Sorry for bumping my own thread... just frustrated.

Can anybody give me some help in trying a different mouse driver?  please?

I see that I have evdev driver installed on the system.  I don't know how to modify xorg to make it usable... I've searched... several times.

---

### Post by wildmanne39 on 2011-05-15
> **iowabeakster said:**
> Sorry for bumping my own thread... just frustrated.

Can anybody give me some help in trying a different mouse driver?  please?

I see that I have evdev driver installed on the system.  I don't know how to modify xorg to make it usable... I've searched... several times.

Hi, that is the driver it is suppose to use, if you change it it will not work at all.

---

