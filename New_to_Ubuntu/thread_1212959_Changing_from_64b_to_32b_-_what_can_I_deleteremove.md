---
title: "Changing from 64b to 32b - what can I delete/remove from the old 64b /home?"
date: 2009-07-14
forum: New to Ubuntu
---

### Post by Daremo_06 on 2009-07-14
I recently reinstalled 9.04 on my machine, but I shifted from the 64b version to the 32b because until 64b is widely supported by things like adobe flash ect ect, I would prefer to stop tinkering with my PC and actually use it ;).

So with that being said, while my ~/ partition is now 32b, I had saved my previous home.  Actually its more like this...

~/home/home(64b) 

its like this because my original 64b installation was a single partition, and for the 32b i made 2 partitions and renamed the original single one to /home.  

What do I need to keep in the original home folders and migrate over and what can i remove completely?

I have already recovered all my evolution settings, firefox has all my favorites, anything else i might need in there?  (I store documents, photos ect ect in a separate 500g HD so those things are already safe.)

Thanks!

---

### Post by mikechant on 2009-07-14
Given your data is on a seperate HD, and you've copied your email and browser settings, there's probably not much else worth copying across. 

Each program you've run will usually have created a config file or filesin your home directory but these will be recreated as necessary (although if you've changed any defaults they will be lost, but that's not usually a big deal). 

Apart from the config files, the only things that might matter would have been placed there by you so if you've checked to make sure you haven't put anything there accidentally you should be OK.

May be worth sticking a copy of your 64-bit home in a backup directory on your 500Gb drive before you delete it, just in case.

---

### Post by Hospadar on 2009-07-14
In terms of your home folder you should be able to keep pretty much everything.  That's all just configuration files, which are mainly text and sqlite-ey databases.

Anything you want to keep you should, almost every program keeps some config data in your home folder, so any of that that you want to save, bring it over.  I usually leave my home folder untouched between installations, even between 32/64 bit changeovers with no problems.

---

