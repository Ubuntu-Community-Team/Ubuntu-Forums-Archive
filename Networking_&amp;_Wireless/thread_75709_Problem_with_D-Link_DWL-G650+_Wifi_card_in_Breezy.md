---
title: "Problem with D-Link DWL-G650+ Wifi card in Breezy"
date: 2005-10-14
forum: Networking &amp; Wireless
---

### Post by _Kris_ on 2005-10-14
Hello,

I've upgraded from Hoary to Breezy on my laptop and now my Wifi Card (D-Link DWL-G650+) is not working anymore.
In Hoary this was working natively, but now I can't get it to work anymore.

Anybody knows if this card is still supported? :confused: 

Thx

---

### Post by _Kris_ on 2005-10-14
OK,

I've found a solution by using the great guide @ [http://www.houseofcraig.net/acx100_howto.php](http://www.houseofcraig.net/acx100_howto.php)

It's not really native, but it works ... kinda ;) 

Kris

---

### Post by ajack on 2005-10-19
@all:

I am a noob, so please forgive me if I explain things differently from what is usually expected from a linux user.  :)

I upgraded from Hoary to Breezy and suddenly find that I cannot use my D-Link DWL-650+ card.  The first thing I did was to do the NDIS tip that seemed to work for the Acer Ferrari 4000 tip by running the Synaptic package and installing the GTK NDISWRAPPER package.  I then installed the WinXP driver for my wi-fi card.  No luck.

I then removed the driver from the ndiswrapper program and decided to search the net for a possible solution.

I then saw the post on this thread (thanks google!) that showed me the how to compile a working driver.  I only used the guide to find and remove the existing driver.  The result was me moving the current driver at:

/lib/modules/2.6.12-9-386/kernel/drivers/net/wireless/acx/acx_pci.ko 

to my home folder (didn't know where else to put the offending file) and ran the "depmod -a" which I did with sudo.

Before trying the ndiswrapper thingy again, I decided to insert the wi-fi card and see what happens and for some strange reason the card now works without me resorting to using the ndiswrapper to install the WinXP driver.

Hope this explanation helps.

---

### Post by ajack on 2005-10-20
An update!

After restarting the computer, Breezy stop working with my wi-fi card.  Going back to the ndiswrapper, I installed the WinXP drivers for my wi-fi card and it seems to be working correctly.  Did a restart and all seems well now.  Not sure if this is the best solution, but it something that works now without having to compile the correct drivers.  I feel its less stressful for noobs like me.

-ajack

---

