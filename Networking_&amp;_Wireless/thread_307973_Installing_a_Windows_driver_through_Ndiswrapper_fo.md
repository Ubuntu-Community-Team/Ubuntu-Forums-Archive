---
title: "Installing a Windows driver through Ndiswrapper for a Belkin F5D7000 desktop card"
date: 2006-11-27
forum: Networking &amp; Wireless
---

### Post by Dannt on 2006-11-27
Hi all,

I recently installed a copy of Ubuntu 6.10 in my Pentium 4 box, the installation recognised all the hardward perfectly exept for the Belkin Wireless G Desktop Network Card F5D7000, I first tried with the default driver provided for Ubuntu: bcmXX, but it didn't wotk at all, then I decided to download the lastest version of Ndiswrapper and try with the drivers advised by the Ndiswrapper list (bwmwl5.inf, bcmwl5a.inf and rt2500.inf) this last I used to got it working good in this same machine when I was running Fedora Core 5, but when I tried to load any of those in Ubuntu they don't work, the RT2500 is the closest and when loading it with Ndiswrapper this is the output

rt2500 driver installed (alternate driver: rt2500)

And of course when I modprobe -i ndiswrapper nothing happens .

The other two drivers are recognised simply as invalid.

Does anyone has gone through the same? any advise will be highly appreciate.

Many thanks

---

### Post by cilynx on 2006-11-27
When you played with bcmXX, did you go through the PITA process of finding and splicing the right driver with fwcutter?

---

### Post by Dannt on 2006-11-27
Sorry for my ignorance,

but not really sure what you mean, Do you mind being more especific?

Thanks, again, sorry for being so ignorant.

Dannt

---

### Post by cilynx on 2006-11-27
In order to use bcm43xx, you need bcm43xx-fwcutter and then an original driver firmware for your card.  I found the firmware for my (built-in HP) card at Dell.  fwcutter splices out the part that it needs from the Windows archive or exe depending on what you manage to find.  Once that is spliced out, you can use the bcm43xx module and it should work.  I have found that some cards also require that you add "Rate 11" as an option in /etc/network/interfaces as 54G mode doesn't work.

---

### Post by Dannt on 2006-11-28
Thanks Cilynx,

All done now! I followed the instructions at the Ubuntu documentation in order to install the fwcutter as you suggested and I add a line with "rate 11" in /etc/network/interfaces and now everything is in perfect working order.

I do appreciate your help very much

Have a nice day :)

---

### Post by cilynx on 2006-11-28
Glad you got it working.  Have fun with it --

---

