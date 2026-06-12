---
title: "Ubuntu and my iPhone... a grim reality"
date: 2011-01-11
forum: New to Ubuntu
---

### Post by jermza on 2011-01-11
So it seems that my iPhone can't work in Ubuntu 10.10.

When I plug it in via USB, Ubuntu says that it can't mount it.

Some googling reveals that it's pretty much a dead-end.

Really?

---

### Post by mbeierl on 2011-01-11
Not true.  It's just that there are a few limitations and a few updates.  First - synching iTunes to the iPhone or latest iPod Touches requires them to be jailbroken so that you can change the DB version and recreate the itunes database.

Straightforward tethering and seeing the phone - just add the ppa:pmcenery/ppa to your apt sources and make sure you've installed the ipheth tools.

[http://www.ubuntugeek.com/how-to-get-ios-4-iphone-os-to-sync-with-rhythmbox-in-ubuntu-10-04-lucid.html](http://www.ubuntugeek.com/how-to-get-ios-4-iphone-os-to-sync-with-rhythmbox-in-ubuntu-10-04-lucid.html)

---

### Post by Habeouscorpus on 2011-01-11
Under Ubuntu Tweak's Source Center, There's an Other category. There's  an ethernet driver for iPhone there.

---

### Post by Habeouscorpus on 2011-01-11
Under Ubuntu Tweak's Source Center, There's an Other category. There's  an ethernet driver for iPhone there.

---

### Post by jermza on 2011-01-12
Thanks for the help.  Ubuntu now sees my iPhone and I even managed to copy music onto it.

One thing that doesn't work is that Rhythmbox successfully changes the phone's name, but Ubuntu still sees the old name after mounting and dismounting and mounting.

Any ideas?

---

### Post by jermza on 2011-01-12
Also, it seems that Rhythmbox can't do much other than sending songs to my iPhone.

No other files supported?

---

### Post by mbeierl on 2011-01-12
I use gtkpod.  I find its support to be much better, but it does lack the unified feel of Rhythmbox.  Just putting it out there as a choice.

---

### Post by Tony Flury on 2011-01-12
If you have a windows xp licence - you could do what I do : Are a fruitless period trying to get gtkpod, rythmnbox, Amarok and a number of other proposed solutions to work on my Ubuntu installation - I installed Windows XP under Virtual Box, and I then happily installed and ran Itunes inside Virtual Box, and I get all the good ITunes stuff including upgrade notification, library syncs and the ability to "rip" music CDs into my library and onto the Phone.

---

### Post by jermza on 2011-01-15
> **Tony Flury said:**
> If you have a windows xp licence - you could do what I do : Are a fruitless period trying to get gtkpod, rythmnbox, Amarok and a number of other proposed solutions to work on my Ubuntu installation - I installed Windows XP under Virtual Box, and I then happily installed and ran Itunes inside Virtual Box, and I get all the good ITunes stuff including upgrade notification, library syncs and the ability to "rip" music CDs into my library and onto the Phone.
Which, of course, defeats the point of running Ubuntu as an exclusive OS.

&%$@ Apple and their tight regulations and control.

---

### Post by panderohit on 2011-03-02
I have done what Tony Flurry has done too and find that this is the best and quickest method. All other methods on Ubuntu are workarounds and are too troublesome. You will be left without a choice but to manage it on Windows itself. At least the virtual box allows you to work on Ubuntu while the iPod syncs, because there is nothing worse than waiting for the iPod to sync in Windows on a dual booted machine while you want to get on with other work on Ubuntu.

I share your feeling about Apple, jermza. I plan to go Android next. No more iPhones for me.

---

