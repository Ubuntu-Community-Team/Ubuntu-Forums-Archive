---
title: "Resolution and fullscreen problems, wierd drive partitioning, incomplete uninstalls"
date: 2010-02-14
forum: New to Ubuntu
---

### Post by rklpro on 2010-02-14
Hello and thanks for checking out the post.  I have some issues that I consider critical and would appreciate any help you can offer.  Keep one more person away from the Microsoft Machine...

SYSTEM:
Samsung N120 netbook running Ubuntu Netbook Remix 9.10

First, I've posted this before but no solution was found so here I go again.  I use my netbook with a 22" Acer display.  If I want to sit and stare at the screens without running programs, it's fantastic.  Anytime I run anything full screen, I either get the black or frozen screen.  Depending on what it is, sometimes I get sound.  Everything works perfectly when I use 800x600 reso.  

Second, I was downloading something the other day and the file couldn't finish because I had run out of space.  For whatever reason, there seems to be a 30- or 40-gig cap on my home drive so nothing else could go there.  I was suggested to create a folder elsewhere and go from there.  That works, but it's not what I want to do.  I prefer to keep all of my system files separate from my useless crap.  

Third, when I uninstall some programs, there's some stupid files that get left behind-- like application icons that stay on my desktop.  I discovered the beauty of the Package Manager which helped a lot, but didn't get everything.  


Okay-- that's it for now... but I must warn you.  I'm a complete Linux beginner but I'm computer savvy.  You'll probably have to explain a lot but I'm a quick study.  Thanks in advance... I really don't want to go back to Windows.

---

### Post by iponeverything on 2010-02-14
To remove totally remove a package, in theory you should be to do:

sudo dpkg --purge <package name>

---

### Post by rklpro on 2010-02-14
I appreciate the quick response... here's what I got:

dpkg: warning: ignoring request to remove onboard which isn't installed.

Is this something I might have to just search through the package manager to find?

---

### Post by crf on 2010-02-14
Run df in a terminal to see the space left on your partitions and file systems.

It's pretty easy using synaptic to remove the left-over configuration files from programs you've removed.

In the system menu, there is a "hardware drivers" menu entry: maybe there is a non-free driver for your acer monitor or graphics card. You may try running without "visual effects" (see the appearance preferences in the system menu).

---

### Post by rklpro on 2010-02-14
It's usually more than just config files... Data files, icon images... just random, dumb crap.  I've been using Synaptic to get rid of what I can find but some of it is elusive.  Is there any sort of global preference that includes these things in the uninstall?  I always look for the relevant checkboxes during individual installs.

Thanks for the tips about the graphics card-- I'll frig around with that when I'm back at my apartment.

---

