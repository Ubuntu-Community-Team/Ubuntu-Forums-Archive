---
title: "Help With Wireless..."
date: 2008-05-05
forum: Networking &amp; Wireless
---

### Post by RobDude16 on 2008-05-05
Hi all,

I've read through the WifiDocs/WirelessCardsSupported page and I'm still a bit confused.  There are a lot of devices where it says that it works 'out of the box' with different specific versions of Ubuntu.  Anyway, I had a few questions, I was hoping someone could help me out with.

1.)  If a piece of hardware works in an older version of Ubuntu, does Ubuntu guarantee that it will continue to work with future versions of Ubuntu?  

2.)  All of the items in the hardware doc have 'Make / Model / Chipset/Driver'.  I know this might sound silly; but when I go shopping for a piece of hardware at a story like BestBuy or Circuit City, how can I know which Chipset that hardware will have?  Will every LinkSys WUSB300N wireless usb adapter have the same chipset?  Or can two boxes with the same name from the same manufacture have different chipsets?  And if they can have different chipsets; how can I possibly know if what I am buying will work with Ubuntu?

3.)  Is there any wireless network adapter that anyone here will personally guarantee?  I hear people say things like get an 'Atheros' chipset or something, but I don't know what that means.  I was hoping to buy a new wireless device today during lunch and BestBuy is the only computer store that is within driving distance.  Is there anything someone could point me to on the BestBuy.com website that will 100% without-a-doubt work on the current version of Ubuntu and all future versions of Ubuntu?

Thanks in advance!

---

### Post by nixscripter on 2008-05-05
Unfortunately, wireless drivers on linux are usually written by very determined individuals with time on their hands. There are few "guarantees" about anything.

As a general rule, to answer your second question, every card model has a single chipset in it. The "chipset" really is a description of the interface between the card and your computer, which is what any driver has to deal with in order to communicate with it. Broadcomm chips, for example, appear in many cards, but can all be used by the same driver, bcm43xx (though this has its own quirks).

If you look for the driver's webpage, you can often find lists of cards with broadcomm chips the drivers have been tested in. Sometimes the card manufactuerers will tell on their "detailed specification" sheets, but often they won't. Unfortunately, you "just have to know" what kind of chip controls your card. Google is your friend (try "PCI wireless card **your-brand** linux driver" or something like that).

Attempts have been made to rectify this situation. Probably the best one is ndiswrapper, a package which Ubuntu provides, but does not support as far as I know (in terms of its use in any particular driver). It allows you to take a wireless driver from Windows, like with an install CD that came with the card, and use it on Linux. Again, this is by no means a guarantee, but it seems to work for a lot of people. For the device you mentioned, this method has a set of instructions [here]("http://ubuntuforums.org/showthread.php?p=3268995").

Alas, like many things in life -- and many more in linux -- there is no easy answer. I hope this helps anyway.

---

