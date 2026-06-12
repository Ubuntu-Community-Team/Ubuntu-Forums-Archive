---
title: "WINE installer conflict in 64-bit Intrepid"
date: 2009-02-14
forum: New to Ubuntu
---

### Post by Kawaiii on 2009-02-14
Hello,
I'm getting my shiny new Ubuntu working, currently dual-booting with xp.  I'd like to be able to run some of the adobe programs (photoshop CS, etc) in ubuntu to make use of the 64-bit-ness, at least for the extra ram.

Anyway. I'm trying to install WINE, and add and remove programs gives me the error
Cannot install 'wine'

This application conflicts with other installed software. To install 'wine' the conflicting software must be removed first.

Switch to the 'synaptic' package manager to resolve this conflict.

Searching for "wine" in synaptic gets me nothing. I've already used sudo apt-get update, so I'm not sure what the problem is. I'm a linux noob.


(and on a side note, I have a few other little questions:
~how do I make adobe pdf the default printer?
~I'm trying to use devilspie to make applications launch in specific workspaces but they aren't launching in the right place, I'm not sure why.
~And I'd like a different wallpaper on each workspace. Should I just try KDE?
that's about all. Thanks!)

---

### Post by lazyart on 2009-02-14
- Be sure you've enabled all the repositories.
- As for the printer, go to system>administration>printing and right click on the adobe pdf printer.  Then set as default from the resulting menu.
- yes, KDE is the way to go for different wallpaper on the workspaces
- can't help you with devilspie.  Have you gone straight to it's homepage for answers?

---

### Post by Kawaiii on 2009-02-14
I managed to install WINE- thanks! I feel silly, I could have sworn I had enabled all the repositories...
Do I have to use WINE to install the program? It's already installed on the XP partition, and since the adobe suite takes up a few gigs, it'd be silly to install it again. Just using wine to run photoshop.exe gives me an error "because of missing or invalid personal information"

My main problem is that the printer dialog doesn't have an option for adobe pdf printing. What is the recommended program to download for this?

If I switch to KDE does this mean that many of the programs won't work? I just managed to get Evolution set up. I'd be loath to do it again one day later.

I followed step-by-step some tutorials I found online for devilspie, but they don't work. I'm not even sure how to get the debug.ds running, even though I made the file.

Bunches of questions, but thanks for helping! =)

---

### Post by ant2ne on 2009-02-14
It is my understanding that wine creates its own registry entries, which your suite will probably need to function properly. It can't just mooch off of the xp install. That would be kind of cool (and scary) if it could.

---

