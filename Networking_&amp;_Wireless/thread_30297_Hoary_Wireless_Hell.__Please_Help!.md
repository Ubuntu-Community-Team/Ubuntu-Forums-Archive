---
title: "Hoary Wireless Hell.  Please Help!"
date: 2005-04-28
forum: Networking &amp; Wireless
---

### Post by ncfoster on 2005-04-28
Hi all,

First off, I want to say that I am quite a Linux noob, so I apologize in advance.  I've got enough experience with Linux to understand most of the basics, but I simply cannot get my wireless networking configuration going.  I have spents days trying to figure this out using various techniques posted throughout these forums and elsewhere.

So, here is my basic situation/setup that I am trying to configure (this is for my sister who keeps wrecking her machine with spyware, no matter what I do to protect her).

Dell Latitude CPi (300 Mhz) with 192 MB RAM (docked in a C/Dock docking station)
Wacom Graphire (I've figured out everything with that, except how to get GiMP to use the eraser tool properly).
and one of several wireless network cards, which is where the problem comes in...

I have used the 3Com ethernet card built-in to the docking station to do everything so far, but where this computer will be used, wireless is a much better option.  The card that I have been trying to get to work, for the most part,  is an Adaptec AWN-8030.  From reading, it would seem like it should either work out of the box, or work with the wlan-ng packages.  I have had no luck with that, and I have had no luck trying the Windows drivers for it with ndiswrapper either.

I also have at my disposal an old D-Link DWL-650, and a newer Dell TrueMobile 1300 USB.  I haven't tried the TrueMobile at all, because I read that it required the ndis-wrapper, and I hadn't wanted to get into all of that until tonight.  Well, at this point, I am willing to try anything.

No matter what I've done, nothing has shown up in the Networking tool in the ubuntu GUI, other than a non-existent modem and the 3Com NIC.  wlan0 never comes up.

I know that you all probably want precise information about what I've tried, and what happened.  Truth is that at this point I've tried so many things that I've lost track.  I am about ready to re-install and start over.  I just want to know which of these three wireless cards I am likely to have the best luck with, and what the simplest way is to get it working.  It only has to be setup once, because if my little sister can figure out how to fark this up, I'm officially quitting the family tech support biz.

So, if you can help me, please do.  In your answers, assume that I have some limited linux knowledge, but if in doubt, spell it out.  I am at the end of my rope and I've searched and searched for a good answer, so please excuse my starting a thread on something that I know has been addressed in some way many times before.

Nathan

---

### Post by Eproxus on 2005-04-28
It may not be of much help but you probably should look for eth0, not wlan0 or wifi0. See more information [here]("http://ubuntuforums.org/showthread.php?t=23371").

---

### Post by nocturn on 2005-04-28
Hmm

I guess none of these cards are supported by the kernel, so they are not detected at boot.
For most of such cards, you can use ndiswrapper to load the windows driver (search the forum for a howto).

Once the card is detected, it will show up in the GUI tools.

BTW, you can check the hardware list in the GUI for the presence of your card.

---

### Post by az on 2005-04-28
Your card may not be supported.  Check this page and then look at the card's revision.  Despite the same name, different revisions have different chipsets.

[http://support.dlink.com/faq/view.asp?prod_id=357&question=General%20Wireless](http://support.dlink.com/faq/view.asp?prod_id=357&question=General%20Wireless)

The card should work fine with ndiswrapper.  I think a pci card would be much more relable than a usb one...

---

### Post by ncfoster on 2005-04-28
On the issue of eth0 vs. wlan0, etc., my actual ethernet adapter (built-in to the docking station) takes eth0.  So, would this interfere with the detection/assignment of the wireless card, or would the wireless card just take eth1 or something?

Well, at the moment, I have two PCMCIA cards, both 802.11b, and the TrueMobile 1300 USB.  As best I can tell, both of the PCMCIA cards *should* work with wlan-ng, if not out of the box.  I think they are both Prism2-based.  Since this is an old machine, and not mine, I don't really want to have to pick up any new hardware, so PCI is not really in the equation at the moment.

I feel like I must have done something wrong with the wlan-ng stuff.  Are there some common pitfalls in this procedure?  I did not recompile the kernel.  I am running the 686 version of the hoary kernel.

Nathan

---

### Post by ncfoster on 2005-04-29
Update: After not too much fuss, I installed a USB 2.0 card in the docking station and got the TrueMobile 1300 USB going.  Only odd thing now is that it reports its name as wacom0.  Is there any way that I can easily change what it shows up as?  I assume it is in some config file somewhere.   Obviously, it stole the name from the tablet.

Second Update: While I previously wrote that the Wacom tablet was performing slowly in GiMP, it seems that this has been alleviated by moving the tablet back to the USB 1.1 ports on the docking station, rather than using one of the USB 2.0 ports.  The question remains "how can I give the wireless card a proper name, instead of wacom0"?

Nathan

---

