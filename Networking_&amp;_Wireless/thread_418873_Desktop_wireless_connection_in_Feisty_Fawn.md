---
title: "Desktop wireless connection in Feisty Fawn"
date: 2007-04-22
forum: Networking &amp; Wireless
---

### Post by jazzman65 on 2007-04-22
Hi,

I'm still very new to Ubuntu but I am quickly growing to appreciate it over Windows, hands down.  In fact, I am in the process of building a brand new machine which will be solely Ubuntu-based.  There's one aspect to the build that I'd like some advice on if someone out there is willing to share your experience.  Due to its planned location, I'm looking to incorporate a wireless connection on my new machine.  My question:  has anyone experienced setting up a wireless desktop connection with Feisty Fawn?  If so, would you share your method?  Was it via a wireless access point or a wireless adapter card?  Also, what type of equipment did you successfully use?

I certainly appreciate in advance any help or advice anyone shares.  One of the nicest aspects of my experience with Ubuntu so far is reading through these forums and seeing the willingness of people to share their knowledge!

Thanks,
jazzman65

---

### Post by rich.bradshaw on 2007-04-22
Most wireless cards I have used have worked either out of the box or with a bit of work. The main thing to realise is that it's not necessarily the brand of the card that matters (D-link, Belkin, Linksys), it's the chip inside. Some of these are well supported, others are a bit of a nightmare. 

I have 3 Belkin cards, a PCI card, USB external, and PCMCIA card. 2 have Ralink chips in, 1 has a Broadcom chip. I also have used a built in wireless in a Dell laptop.

All work fine, but with a little work. The Built in one worked with no work at all. (intel proset?)

There is a list in this forum somewhere of which cards definatly work - most will eventually work.

ndiswrapper is the tool you need to get some "Windows only" cards to work, it basically lets you use the Windows driver which comes on the disk with the wireless card. For others they will probably just work.

---

### Post by jazzman65 on 2007-04-22
Thanks for the quick response Rich!  I have seen a couple of reviews here and there on Newegg where people have related their success with a desktop card or such with Ubuntu, but since Feisty is so new, I thought I'd ask about people's more immediate experience here.

I appreciate your input!

---

