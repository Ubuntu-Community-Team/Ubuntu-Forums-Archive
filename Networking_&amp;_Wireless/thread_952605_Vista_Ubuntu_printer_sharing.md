---
title: "Vista/ Ubuntu printer sharing"
date: 2008-10-19
forum: Networking &amp; Wireless
---

### Post by Powderhound01 on 2008-10-19
Hi all, first post, but I've been a lurker for the past year or so and have been using Ubuntu for just as long. :)
OK, I've been having all sorts of fun trying to get my Vista Home Premium PC to use a printer over a network (All wired, D-Link DSL 2640B router) connected to another PC running Ubuntu 8.04. Until a few weeks ago, I had it working perfectly, but all of a sudden, Windows with its usual knack for these kinds of things decided that the printer was permanently offline. Reinstalling the printer drivers cured this, but only while the PC remained on; following a reboot it's gone again. Now even this seems to have stopped working, and violence towards my PC is becoming increasingly imminent.
For some reason, Windows simply refuses to believe that there is a printer at the IP address of the PC it is connected to, whether I let it scan for it or input the IP manually directly from CUPS. I am able to access the printer's CUPS page in Firefox and make it print a test page, so there is clearly some major problem at my end. If anyone could give me a simple, step by step guide to getting it to work from scratch (At the Vista end; Ubuntu is definitely set up correctly), then I would be extremely grateful.
Powder

---

### Post by kingtiger01 on 2008-10-19
I know that its probably no help to you're Current Situation, but you could check the Wiki at Cups. issues like this are handled often. most of the time its do to poorly written drivers, that are attempting to communicate via USB or LPT,

and i know the head aches trust me, been running my old HP Laserjet 1100 for 2 years off my Ubuntu server, thats been sharing to all kinds of other os'es from Sun to Microsoft.

Food for Though...

~Kingtiger

---

### Post by superprash2003 on 2008-10-19
do you have a static internal ip for your vista machine?? if the keeps changing , then that could be the problem..

---

### Post by Powderhound01 on 2008-10-19
> **superprash2003 said:**
> do you have a static internal ip for your vista machine?? if the keeps changing , then that could be the problem..

Static IP on both boxes, so no joy there. :mad:

---

### Post by jimv on 2008-10-19
Plug the printer into the Vista machine and share it to the Ubuntu machine?

---

