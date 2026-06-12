---
title: "Belkin N1 Wireless Notebook card"
date: 2007-01-17
forum: Networking &amp; Wireless
---

### Post by gillesmax on 2007-01-17
trying to install the dirver without success?
any idea?
tx

---

### Post by teaker1s on 2007-01-20
what chipset? if your not sure then terminal
[COLOR="Red"]lspci[/COLOR]

or

[COLOR="Red"]lsusb[/COLOR]

---

### Post by falconcy on 2007-03-24
If it is the F5D8011, then it is a Marvell Chipset. I just about got it working using ndiswrapper and a Netgear driver, details from the ndiswrapper page here:

[I]Card: NetGear WN511T 300mbps RangeMax Next (PCMCIA Card)

    * Chipset: Marvell Pre-N
    * pciid: 11ab:2a02
    * Driver: Driver for Netgear WN511T ([http://firmware.netgear-forum.com/index.php?dlfile=705)](http://firmware.netgear-forum.com/index.php?dlfile=705)), Version 08/29/2006, 3.0
    * Other: Tested with ndiswrapper 1.7 (utils) and 1.8 (drivers) for Kubuntu (Live DVD).
    * Other: The lspci command says: "Ethernet Controller: Marvel Technology Group Ltd: Unknown device 2a02 (rev 03)" [/I]

---

### Post by kd5ob on 2008-05-30
Just wanted to say that I've had this Belkin N1 USB wireless adapter for
about 6 months now and never got it to work.

Well, to make a long story short,,,,

I upgraded to Hardy.

Saw on the DVD this set of DEB-s which said something like restricted
net drivers.  So, I installed all of them.

Next, I took the .inf file off the CD and installed it using that
GTK based ndiswrapper tool.  Thing worked right off the bat!

It's been working for a month now.

You won't find these special drivers on the AMD64 DVD which I had been running.  

I later found out that they are saying because the firmware files are designed for a 386 in mind, they may not work with the AMD64 at all.
There is some work to try and correct that but it hasn't worked for me yet on the AMD64.

So, I'm back to a generic kernel 386 and this firmware and it's working
fine.  

Someday, commercial software will have to modernize up to the level 
we've been at for a decade now, 64 bit!

Wonder what Steve Jobs would say about now?

Charlie

---

### Post by yompaz on 2008-06-18
Hey Charlie - good for you! I've been trying to get this card working on my laptop for a few days now, with no joy. I'm running hardy, just like you, so this should be possible.
What version of ndiswrapper are you using?
Any config files that you had to edit?
I'm pretty new to Ubuntu, so excuse my ignorance.
Any help would be appreciated, otherwise there may be a laptop sized hole in my living room window!!! :-)
Thanks,
YOMPAZ.

---

