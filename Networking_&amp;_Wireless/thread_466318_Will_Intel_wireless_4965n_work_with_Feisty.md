---
title: "Will Intel wireless 4965n work with Feisty?"
date: 2007-06-06
forum: Networking &amp; Wireless
---

### Post by stchman on 2007-06-06
I am thinking of getting a new laptop.  It has the 4965n card and I was wondering if Ubuntu works with this card?

Thanks

---

### Post by Swab on 2007-06-06
I don't think there is a Linux driver for that card yet...

---

### Post by chili555 on 2007-06-06
This post reports success with ndiswrapper: [http://ubuntuforums.org/showthread.php?t=451069&highlight=4965](http://ubuntuforums.org/showthread.php?t=451069&highlight=4965)

---

### Post by stchman on 2007-06-06
I guess if I want that laptop I will get the 3945b/g wireless card.

I would suspect that the next kernel for ubuntu will support this card.

---

### Post by mikledet on 2007-06-11
There are various threads here with people who managed to get their 4965AGN to work, mostly using NDISwrapper.  Though I'm still looking for the one methood that will work for me.  :(

---

### Post by RobotJox on 2007-06-11
well, I got mine working sort of with ndiswrapper, but my connection drops out after 30 seconds, or, if I'm very lucky, after 2 minutes, and then I have to reboot.

There is this project: [http://intellinuxwireless.org/](http://intellinuxwireless.org/)  which offers drivers for this card, but I can't get it to compile... If anyone has any luck with it, please do tell

---

### Post by vronp on 2007-06-19
> **stchman said:**
> I guess if I want that laptop I will get the 3945b/g wireless card.

I would suspect that the next kernel for ubuntu will support this card.

The Linux driver is days away.

Someone recently posted some steps for getting a preliminary version running on Feisty.

---

