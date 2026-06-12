---
title: "Computer Building Help"
date: 2009-06-23
forum: New to Ubuntu
---

### Post by Joe_ on 2009-06-23
I'm not sure where to post this.

To be straight to the point: I'm trying to build a computer. I'm new to the concept, I've never built one before, and I had a friend who knows more about Linux than I probably ever will (and who works in a computer lab and is trying to get his boss to move all the machines from Fedora to Ubuntu) recommend that I ask around for help here.

I'm looking at two things: First, hardware issues with the other hardware, and then hardware compatibility with Ubuntu. I've opened up plenty of machines, but I've never built something from scratch before. While I've done some research, I'd like to ask people who know much more than I do to make sure everything will work before starting. I believe you all qualify as people who know more than I do (or more than most people do, for that matter).

AMD Phenom 2 x2 550
Gigabyte MA 770t UD3P Motherboard
G.SKILL 2x2GB DDR3 1333 Dual Channel
EVGA 8800GTS 512MB or GTX 260 (undecided)
Western Digital Caviar 640GB
EDIMAX PCI Wireless Card
LG CD/DVD RW Combo
Antec Three Hundred ATX Mid Tower
OCZ GameXStreme 600 Watt Power Supply Unit


I can't possibly thank you enough for any help you give.

---

### Post by doas777 on 2009-06-23
well, you've got all the core parts there (and not bad quality choices either), so now you just gotta make sure their compatible with each other and you should be ready to go.

I don't suppose you already have links to these parts assembled? I would be happy to take a quick look, though you seem to know whats going on.

----
Well your exact hardware did not appear on the ubuntu hcl ([http://www.ubuntuhcl.org/](http://www.ubuntuhcl.org/))
but a very similar mobo got 5 stars from 1 reviewer. I couldn't find the vidcard there either (which seems odd to me). it was listed but had no reviews. the proc, the mobo and the vidcard are goign to be your major points where compatibility is important. most everything else either does not directly interact with the OS or is so standard that it shoudl be flawlessly supported.

---

### Post by LewRockwell on 2009-06-23
give us a brief idea of what you want this machine to do please

to be completely honest, unless you want "bleeding edge" performance, finding a decent used machine may cut your initial investment substantially which would leave you with enough beans for other goodies as well

---

### Post by Zzl1xndd on 2009-06-23
I can't speak for the Motherboard or the Wireless card but the rest of your rig looks fine. I would say go with the 8800GT, im using it now and its a great card works very well with Linux.

---

### Post by Joe_ on 2009-06-23
My current machine a Lenovo z60t laptop, is dying because I tried playing too much Civ4 (beyond its abilities) and the fan and hard drive are both mad at me. I don't just want a computer, though; this is an academic exercise for me as much as anything. I want to learn to build a machine.

As for what I want the machine to actually do: I'm a college student at UC Davis. My aforementioned friend is part of several friends and family "encouraging" me to learn computer skills to help with future job prospects. I figured the best way to learn is by doing. I intend to use the computer for internet, programming, and gaming (Wine is getting better and better, from what I hear). I eventually intend to dual boot to Windows 7, but that's significantly down the road and depends on how much I like Ubuntu by then (or how much other people hate windows 7). 

For the video card, I'm wondering whether the more expensive 260 is worth the extra cost over the 8800, especially since I'm considering Windows significantly down the line. That's my own choice, but I'm taking recommendations. 

DOAS777: Apparently the motherboard works with Linux. I found a newegg review; "...Working great with Ubuntu 9.04 64 bit (don't use windows)..." I could give links to everything, but they'd really be newegg links. Would that suffice?

---

### Post by 3rdalbum on 2009-06-23
I believe the 8800GTS doesn't support VDPAU.

VDPAU is a video output module and a set of video decoders that offload most of the processing onto the graphics card, so you can play video without putting load on your CPU. This results in better quality video and better multitasking while watching video, so I'd go for either an Nvidia 9800 or a GTX260, both of which support it.

VDPAU also requires an up-to-date Mplayer compiled from SVN with the '--enable-vdpau' option passed to the configure script. There are a number of howtos around.

---

### Post by synapsys on 2009-06-23
Or get an 8800 gtx oc edition which I am running that makes my processor and ram yawn from boredom.....

---

### Post by Joe_ on 2009-06-23
[http://en.wikipedia.org/wiki/VDPAU](http://en.wikipedia.org/wiki/VDPAU)

Looks like the 8800GTX 512 supports it, which is what I was thinking of. Thanks for the tip, I'll look into vdpau. 

So short story is that everything fits and is compatible with Ubuntu. This is awesome thread, thank you all.

---

### Post by ACupOfCoffee on 2009-06-24
The Gigabyte 770's are good motherboards. You'll have few problems with them.

---

