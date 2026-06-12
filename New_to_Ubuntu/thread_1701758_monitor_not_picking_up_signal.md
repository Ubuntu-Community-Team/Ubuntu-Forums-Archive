---
title: "monitor not picking up signal"
date: 2011-03-06
forum: New to Ubuntu
---

### Post by philipballew on 2011-03-06
i recently installed ubuntu server 10.04 and set up a few things and when i went to continue setting it up a week later i was unable to due to there now being no picture on the screen. the monitor is say 10 years old. its a boat anchor of a monitor.the monotor still says looking for signal. is this a hardware problem or ubuntu problem?

---

### Post by grahammechanical on 2011-03-07
Have you switched the computer on? Is there a cable connecting the monitor and the computer? These are the kind of things that would produce that message on a monitor. If Ubuntu was having problems using the monitor you would find out about it some other way.

Regards.

---

### Post by Diametric on 2011-03-07
Have you used the monitor on a box that you know works? For instance, plug the monitor to a machine that is up and running, one that you know is sending a valid video signal, and see if the monitor displays.  if it does, then it's not likely the monitor - if it does not, sounds like it might be broke.

---

### Post by Grenage on 2011-03-07
If you're not getting any video signal at all (no BIOS/Boot), then I would assume that either the VGA cable, monitor or GFX card are dead.  I would suspect the GFX card first.

---

### Post by philipballew on 2011-03-07
yeah, how would i know it its the graphics card and not the whole mother board itself?

---

### Post by kj6zd on 2011-03-07
Hi there,
I experience a similar dis-behavior with my setup. :(My Mobo is a MSI SLI board with dual core AMD processor. Both SLI slots are occupied and work fine under, sorry (Windows XP).
I can go through the entire Server setup (10.10) with video etc. The install completes and I remove the CD:). On reboot there will be no Video anymore:(. My guess is that for some strange reason, I been observing this for years, the Video card gets set into a different unfortunately invalid mode:confused:. In my case it doesn't find any video hardware anymore. My monitor is a relatively modern LCD from Acer and reports NO SIGNAL!. Even while trying to use the plain recovery mode, NO VIDEO. Hardware is fine and working. Got to be Video Driver code or something out of our reach!:o
If I physically remove the second Video Card, the server starts and Video is present.
I know, server setups aren't supposed to use SLI or other fancy graphics, but it would be nice to have it working without disassembling the box.

The desktop version works alright, although I have to change configuration to point to only one Card or assign priorities, to be able to use Compiz etc.

As to Phillip's question, I unfortunately have another question. When you power up your system, do you see the POST screen, if not check your cable connection. If this is secured, then it may truly be the hardware that went away. Is your monitor a CRT type or LCD. If it is an LCD have a very close look if you can see something, maybe very hard to make out, then your LCD back light power supply may have gone bad. If all of the previous doesn't apply, guess your video card is gone.

Cheers,
Norbert :popcorn:

---

### Post by philipballew on 2011-03-07
when i use my laptop it shows the screen but when i try to re plug it into the desktops i turned into servers no signal even though the servers are powered on

---

### Post by Grenage on 2011-03-07
Then if you don't get a BIOS/boot screen when it's plugged in, the GFX card is dead.  If it's integrated, you can probably get around it by plugging in a card.

---

### Post by philipballew on 2011-03-07
could the monitor have ruined my graphics card, because it happened to 2 different servers?

---

### Post by dargaud on 2011-03-07
Well, my story is that I had a cheap but recent monitor and an integrated card that behaved the same way: on CD install everything would work fine. After reboot, nothing visible after the BIOS. Tried many times with lots of options. Plugged the monitor on a different (PCI) graphics card: no problem. Plugged a different monitor in the integrated card: no problem. Could never figure it out.

---

### Post by Grenage on 2011-03-08
> **philipballew said:**
> could the monitor have ruined my graphics card, because it happened to 2 different servers?

While it's possible, that does make it somewhat unlikely.  Are they the same model?

---

