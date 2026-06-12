---
title: "Controlling a Ubuntu Studio PC remotely"
date: 2017-12-12
forum: Networking &amp; Wireless
---

### Post by jackelliott on 2017-12-12
Hello all,

I'm having a bit of a quandry with something that's outside of my knowledge, could use some help please.

The setup:
I have a rackmount pc running Ubuntu studio in my band's stage rack that is connected to a router via ethernet. Also connected to the router is a digital mixer and a Laptop (either ethernet or wireless). Now, the laptop is in the mix position and the rackmount pc is buried in the rack usually under several cables, cases, groupies etc. I need to connect to the computer using the laptop and be able to control the computer as if it had a screen/keyboard/mouse attached to it. I cant connect the peripherals myself as it's too far away and not a convenient place anyway. If it matters, we use the laptop to control everything but the mixer will only record over USB not ethernet, so I basically need to access the pc using the laptop and press the record button so the pc on the stage records the gigs. 

Capiche?

The problem:
I've tried various ways of doing this, and they either don't work or aren't neat. I *think* I have managed to setup a VNC server on the pc using X11VNC, and then I can use the command *$gvncviewer 192.168.1.11:0* on the laptop to access it that way, is this the best way to do this? Is there an all GUI solution? A desktop shortcut? I had very little idea what I was doing when I set up the vmc server, so if anyone could point me to an online guide that would be great. All of the ones I found seemed to be for older software that isn't used any more.

I know what I have works, but I worry that the more that can go wrong on a gig the more will go wrong. Anything I can do to simplify, secure, streamline or otherwise improve this would be greatly appreciated!

Thanks,
Jack

---

