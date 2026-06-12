---
title: "Replace Video Card on Ubuntu Server 8.04.4LTS"
date: 2010-11-22
forum: New to Ubuntu
---

### Post by Silverfox on 2010-11-22
Hello again folks.

I have a couple of questions for the board. I've been looking around here for a couple of days for anyone else that's had my particular concern, but everything I'm reading relates to GUI versions of Ubuntu.

The system in question:

Ubuntu Server 8.04.4 LTS LAMP installation, fully updated. Hardware is an AthlonX2 4400+ 2.2gHz living on an Asus A8V mobo, with 3 gig RAM installed (upgraded from 1 gig today).
Normally administed remotely using puTTY, even though the box sits about 4 feet away under the printer table (don't have the space for a dedicated KB and monitor).

Since I was upgrading hardware, I dragged out a monitor and kb from storage and hooked up to the KVM switch so I could access BIOS after installing the memory and make sure everything was working. When I hooked up the monitor, I got garbage on the screen :-?. I shut the system down remotely, opened up the case and everything looked ok. Installed the memory, made sure the video card was properly seated, and booted back up. Still mostly unreadable gobbeldygook, although I could tell it was at the BIOS screen. :confused: Shut it down again, pull the vid card and have a closer look. All but one of the capacitors on the card have popped, it's garbage.

My question is this. Once I find a card to replace the fried one with, are there drivers that will need to be upgraded? There is no desktop on this machine, it's strictly command line (what can I say, I'm a sadist), and I don't recall having to install video drivers when I first installed Ubuntu Server (although that was 3 years ago now). I can continue on remotely for now, but I want to upgrade the distro to 10.04, and I need the direct connection before I attempt that.


Any advice is greatly appreciated! :popcorn:


Silverfox

---

### Post by cariboo on 2010-11-22
You can drop in just about any video card, and it should work without any special drivers

---

### Post by Silverfox on 2010-11-23
Awesome, thanks!

---

