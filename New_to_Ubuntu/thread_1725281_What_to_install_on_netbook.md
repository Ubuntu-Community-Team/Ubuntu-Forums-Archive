---
title: "What to install on netbook?"
date: 2011-04-09
forum: New to Ubuntu
---

### Post by IHeequ5i on 2011-04-09
I've recently acquired a Gateway LT120 series netbook that's apparently 3 or 4 years old. It has XP Home on it currently, and Gateway tells me that it "probably" won't run Windows 7. Has anyone ever put Ubuntu on one of these successfully? Any gotchas?

---

### Post by Rex Bouwense on 2011-04-09
I've got an ASUS EeePC that I have a desktop version of Ubuntu 10.04 installed.  No gotchas here.  Can't speak for the Gateway.

---

### Post by jerenept on 2011-04-09
try [fuduntu]("http://fuduntu.org/")
Works like a charm for me.

---

### Post by shad0w_walker on 2011-04-09
The bulk of netbooks have pretty similar hardware internally, most of which seems to be very well supported. Got a Dell Mini 9 here, no hassles with it on any of the distros I've tried. If in doubt, there are various tools about to create a Live USB, so try it out before hand, see how it handles.

---

### Post by IHeequ5i on 2011-04-09
The adventures of the netbook install: Part I

This particular netbook has no CD or DVD drive. Ergo, I must create a bootable USB. "No problem," says I. "I has a spare USB stick that's not doing anything." So I backup all my files off the USB drive...

Download Unetbootin... no problems...
Execute Unetbootin...  choose Ubuntu 10.04 LTS and the USB drive...

And come to find out that I've managed to make the smart card for my digital camera into a bootable Ubuntu drive. It's a 4-gig card, so plenty of room. But I was mightily amused.

This particular netbook DOES have a smart-card reader that can be set in BIOS as a valid boot device. So at the moment, it's installing.

---

### Post by Rex Bouwense on 2011-04-09
Outstanding.:popcorn:

---

### Post by I2k4 on 2011-04-09
I'm happily testing out various versions on a first gen Acer One netbook bought Sept 2008.  I'm using these excellent foolproof instructions and sofware:

[http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)

The one other thing to do to keep using Live USB is to use "Persistence" after the last step at Step 2 - if you don't you don't save your settings and preferences and they're lost between boot ups.  I'd also suggest using a 4GB USB thumb drive and set 2GB of Persistence.

I learned a lot from starting with Ubuntu Desktop which preinstalls a lot of software and has a helpful interface for Windows converts.  I found the "Netbook" version of Ubuntu slow and badly developed, and others on this forum seem to find similarly.  I am currently liking Lubuntu 10.10 as being very fast and lightweight on the older netbook, but it is less "user friendly" than Ubuntu Desktop, so suggest that if you're on a learning curve, play around with Live USB, and find what you like or don't in Linux, for a while before mucking around with hard drive installations.

---

### Post by matty abbo on 2011-04-09
you could always try using Xubuntu, low RAM footprint and uses low CPU so won't generate that much heat :D

---

### Post by IHeequ5i on 2011-04-09
The Laptop Install Adventure - Part II

10.04 installed with no problems off the smart card - which still amuses me greatly. I believe I forgot to mention that I did try it before I did the actual install, to make sure everything worked fairly well.

The display is stuck on 800x600 resolution, but given the small screen size, that's not too horrid. I can't figure out where to adjust it, though. I'll have to poke around on Gateway's website and see if I can figure out what sort of graphics chip this thing has - Ubuntu didn't detect ATI or Nvidia.

I didn't play with the wireless connection, but it picked up the wired connection within seconds after plugging it in - and I was able to download and install security updates.

I may wipe it and install 10.10 just to bring it in sync with my desktop.

---

### Post by hatalar205 on 2011-05-29
Try Lubuntu it works perfect on Netbooks.

---

