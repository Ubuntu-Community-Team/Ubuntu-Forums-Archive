---
title: "what is 'x'?"
date: 2009-01-28
forum: New to Ubuntu
---

### Post by insanity99 on 2009-01-28
i have seen it mendioned on a few linux sites but dont get it. for example a game and on the site it says 'runs with x: yes'

thanks

---

### Post by billgoldberg on 2009-01-28
> **insanity99 said:**
> i have seen it mendioned on a few linux sites but dont get it. for example a game and on the site it says 'runs with x: yes'

thanks

The X-window system:

[http://en.wikipedia.org/wiki/X_Window_System](http://en.wikipedia.org/wiki/X_Window_System)

---

### Post by blazemore on 2009-01-28
X is the X Window System.
It sits between the kernel and the user interface.
It translates pointer movements, applications' display and user input into a display on the screen.
Without it, you'd just be working from a command-line
(hit CTRL+ALT+F4 to see a command-line system, hit CTRL+ALT+F7 to return to X)

---

### Post by insanity99 on 2009-01-28
oh right so that gives the GUI for ubuntu? and someone mention'd this but i'm not sure what he was saying exactly but does winsow system x have trouble with ATI drivers? and thats why videos flicker with effects on?

sorry about my grammar by the way

---

### Post by billgoldberg on 2009-01-28
> **insanity99 said:**
> oh right so that gives the GUI for ubuntu? and someone mention'd this but i'm not sure what he was saying exactly but does winsow system x have trouble with ATI drivers? and thats why videos flicker with effects on?

sorry about my grammar by the way

Not exactly, the GUI is Gnome. It uses the X Window System (also referred to as X11) to function.

ATI drivers perform poorly on Linux, but that should change pretty quickly because they have been open sourced.

---

### Post by insanity99 on 2009-01-28
cool so how will i know when this problem is fixed?

---

### Post by blazemore on 2009-01-28
If you go into Compiz settings and check the Video Playback button, that might fix video

---

### Post by hesjnet on 2009-01-28
I had the same flickering problem on a computer(EDIT: with an ATI graphic chipset). What I did to work around it was to install the "fusion-icon" from synaptic and set it to start automaticly in "Sessions" under system. When this loaded I chose Metacity as the Window manager and the flickering stopped. If it ever did something unwanted again I just used the "reload window manager" function.

Hope it works for you;)

---

### Post by GepettoBR on 2009-01-28
> **blazemore said:**
> If you go into Compiz settings and check the Video Playback button, that might fix video

> **hesjnet said:**
> I had the same flickering problem on a computer(EDIT: with an ATI graphic chipset). What I did to work around it was to install the "fusion-icon" from synaptic and set it to start automaticly in "Sessions" under system. When this loaded I chose Metacity as the Window manager and the flickering stopped. If it ever did something unwanted again I just used the "reload window manager" function.

Hope it works for you;)

blazemore's solution and hesjnet's solution are two workarounds to the same problem, with different results. I'll explain in case you're interested:
Compiz is a composite window manager, which basically means it emulates a 3D environment to create all of its eye-candy. Because of this, sometimes (depending on many things, including your video driver) it won't play nice with 3D applications and video. Checking the Video Playback button in Compiz settings is like giving Compiz a slap on the wrist and telling it to behave. Choosing Metacity as your Window Manager means telling Compiz to go away and replacing it with a non-compositing Window Manager (Metacity) that doesn't have these problems. But if you do that, you won't get some eye-candy that you might like, such as wobbly windows.

---

### Post by Miljet on 2009-01-28
Thank you GepettoBR for that information. It is always helpful to explain why something works instead of just what to do.

---

### Post by tarps87 on 2009-01-28
> **billgoldberg said:**
> ATI drivers perform poorly on Linux, but that should change pretty quickly because they have been open sourced.

Do you mean that the driver made by ATI are now open source or that they are using 'other' open source drivers?

---

### Post by insanity99 on 2009-01-28
oh i see thanks, switching to metacity works

---

### Post by GepettoBR on 2009-01-28
> **tarps87 said:**
> Do you mean that the driver made by ATI are now open source or that they are using 'other' open source drivers?

IIRC the official drivers from ATI are now open-source.

---

### Post by tarps87 on 2009-01-28
> **GepettoBR said:**
> IIRC the official drivers from ATI are now open-source.

Just done some reading about it, how did I miss this. I only just seen the topic review bit in this forum #-o

---

### Post by insanity99 on 2009-01-28
so will i have these open source drivers installed? i have catalyst control center if it helps

---

### Post by GepettoBR on 2009-01-28
> **insanity99 said:**
> so will i have these open source drivers installed? i have catalyst control center if it helps

Update Manager should inform you when a new driver reaches the repos. You can probably also get them at ATI's website. I don't know about Catalyst, though, because I don't use it.

---

### Post by Martje_001 on 2009-01-28
> **GepettoBR said:**
> IIRC the official drivers from ATI are now open-source.
I'm sorry?

They only released documentation for the videocards, not the catalyst driver!

---

### Post by GepettoBR on 2009-01-28
> **Martje_001 said:**
> I'm sorry?

They only released documentation for the videocards, not the catalyst driver!

[http://www.linux.com/feature/119049](http://www.linux.com/feature/119049)
[http://www.desktoplinux.com/news/NS2568321546.html](http://www.desktoplinux.com/news/NS2568321546.html)

They still have their closed-source drivers, but ATI is now working directly on community-developed open-source drivers as well.

---

### Post by Martje_001 on 2009-01-28
Ah, OK, that's good to hear. Sorry for my ignorance.

---

### Post by GepettoBR on 2009-01-28
No need to apologize :)

---

