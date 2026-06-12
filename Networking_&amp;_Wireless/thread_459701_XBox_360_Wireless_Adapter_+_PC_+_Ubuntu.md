---
title: "XBox 360 Wireless Adapter + PC + Ubuntu?"
date: 2007-05-30
forum: Networking &amp; Wireless
---

### Post by Databit on 2007-05-30
Is it possible to use the XBox 360 wireless adapter on a PC with Ubuntu?

---

### Post by goonies on 2007-07-16
I have the same question.... Anyone?

---

### Post by ders on 2007-07-25
I would also like to know that.  It seems like a pretty simple thing.  From what I know about video game controllers the inputs are just 8 bit serial signals.  I can imagine the wireless device simply moves the signal from the controller to the USB.  What I'm getting at is, have you tried the PC controller drivers?  They might work.  Otherwise someone who is good with C will alter them to work sometime soon.

---

### Post by Oen386 on 2008-01-07
I would like to know also.. but it looks like no. :(

---

### Post by Phil Urich on 2008-01-08
Have you tried xpad360?  It's for the wired version, but perhaps to Ubuntu the devices will seem the same.  I know it works flawlessly on my wired xbox360 controller on both Kubuntu 7.04 and 7.10.

The xbox360 wireless adapter is pretty evil, though.  My one friend (who runs WinXP SP2) just got a Logitech G15v2 keyboard  and a G9 mouse; when he first installed them they worked fine, all the snazzy features and all (which are also possible under linux, btw), but after his first reboot they stopped working!  The G15 wouldn't display anything on the LCD, and the G9 wouldn't work at all period.  We pulled our hair our for quite awhile until we stumbled upon a post where someone mentioned having the exact same problem, and the solution being, get this, *unplug the xbox360 wireless adapter before turning on the computer*.  Once we did it was fine.  Why the hell it should do that (and it could be plugged in after everything was running) is a mystery, and it does lead me to believe that the adapter is doing some pretty weird stuff in the background, far more than you'd reasonably expect it to need to do.

I'm curious myself, though . . . I'll look into this.

Edit: over [here]("http://gentoo-wiki.com/HOWTO_Xbox_360_controller_on_Linux") they mention that "wireless support is still experimental", which I guess implies that the xpad360 drivers must work to at least some degree!  So I'd highly recommend trying them out; there are versions patched by folks for Gutsy Gibbon around these forums here, you've probably found some if you've searched around for an answer to your question already anyways, try them out and get back to us!

---

### Post by Zeyelth on 2008-01-09
The wireless controller does "work" with the latest drivers from CVS. There are some minor problems with it though, but most of them can be fixed. There are various threads on this forum that deals with the installation of the latest drivers, though some instructions are system specific and may break over time.

I've made an adaptation of the HOWTO for Gentoo Linux mentioned by the parent poster, following the general outline of some threads on this forum. The adaptation can be viewed [here]("https://help.ubuntu.com/community/Xbox360Controller"). I have only been able to test the HOWTO on my own computer thus far, so while it should work on other computers running Ubuntu 7.10 in theory, I make no guarantees; use at your own risk and all that.

---

