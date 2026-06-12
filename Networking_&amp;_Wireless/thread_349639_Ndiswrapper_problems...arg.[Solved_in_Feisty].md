---
title: "Ndiswrapper problems...arg.[Solved in Feisty]"
date: 2007-01-30
forum: Networking &amp; Wireless
---

### Post by kidicarus on 2007-01-30
Ok...I'm really having some problems here...I used to use NLD10 with this setup and ndiswrapper worked fine, but now since we have Beryl...I no longer need NLD10 for cool effects. But...after I first installed Ubuntu 6.10 I had ndiswrapper load my driver (mrv8000c) fine, though I could not connect to any networks, I saw them...just couldn't connect. ?? So..I thought, well...lets start fresh, so I reinstalled. But now, no matter what I try, it always says that my driver is invalid. I'm using the same driver as before. I've done all updates from the standard repositories (through synaptic) and installed ndiswrapper through automatix2 (I'm pretty sure automatix2 installs ndiswrapper 1.8, ...ndiswrapper-utils-1.8_1.18-1ubuntu2_i386.deb in fact) but still, I get an invalid driver! The card is some generic from ebay, It has no brand that I can find, although it looks exactly like [http://www.encore-usa.com/product_item.php?region=us&bid=2&pgid=81_4&pid=16](http://www.encore-usa.com/product_item.php?region=us&bid=2&pgid=81_4&pid=16). The FCC# is NHPWLG1101. I have tried drivers from the Encore website listed above, from my driver CD, from the Marvell website, I'm outta options here. I know ndiswrapper used to support it. Is this just a problem with Edgy? I love the OS so far, Beryl is much better than Novells run at XGL...but I need wifi!! Is there anyone else who has this card?? Apparently its pretty a popular chipset (Marvell)??:confused:

---

### Post by Brunellus on 2007-01-31
moving this thread to a more relevant forum.  

Try posting more succinctly.  Paragraph breaks in the right places might help readability.

as a first step, try unloading the drivers from ndiswrapper and then re-loading them again.  I haven't run ndiswrapper in a while, but I seem to recall that every kernel update, I had to unload and then re-load the ndis drivers.

---

### Post by Stinger on 2007-01-31
I don't know about your card but my Asus WL-138g uses a Marvell chip too 
Here you can see how I set it up in Edgy

[[COLOR="Sienna"]http://www.ubuntuforums.org/showthread.php?t=288341[/COLOR]]("http://www.ubuntuforums.org/showthread.php?t=288341")

Of course you'll have to use a driver that matches your card , if you don't have one maybe you can find one here at the ndiswrapper wiki's list of cards known to work.

[[COLOR="Sienna"]http://ndiswrapper.sourceforge.net/mediawiki/index.php/List[/COLOR]]("http://ndiswrapper.sourceforge.net/mediawiki/index.php/List")

Hope it helps :)

---

### Post by Stinger on 2007-01-31
Your card most likely is a 
Encore electronics
ENPWI-G
[COLOR="Red"]FCC ID: NHPWLG1101[/COLOR]

Search the ndiswrapper driver page above for "[COLOR="Red"]ENPWI-G[/COLOR]" and you'll get to the driver links.
(mrv8000c)

Or maybe a driver for this card would work ? 
> Card: Trendnet TEW-421PC Wireless CardBus Crd H/W: B1 [COLOR="Red"]fcc id nhpwlg1101[/COLOR]
Chipset: Marvell Technilogy GroupLtd.
pciid: 11ab:1faa (rev 03)
Driver: The WinXP driver coming with the card worked great. The windows XP drivers that came with the card installed really well. (mrv8000c.*).
This was taken from the Fedora forums.

---

### Post by kidicarus on 2007-02-01
Thank you to everyone who replied.

I did try the Encore Electronics driver with no success. I will give the other suggestions a try today and let you know the results.

---

### Post by Stinger on 2007-02-01
A search on the ndiswrapper driver page for "[COLOR="Red"]mrv8000c[/COLOR]" gives more results 
but a search for "[COLOR="Red"]Marvell Technology Group Ltd. 88w8335 [Libertas] 802.11b/g Wireless (rev 03)[/COLOR]" gives the most.
I was reported at one of the cards that the winXP driver froze the system but the win2K driver worked fine.
Hope it helps. :D

---

### Post by FrodoB on 2007-02-01
You might just try this:

[https://help.ubuntu.com/community/WifiDocs/Device/TRENDnet_TEW-421PC_H/W%3aB1_%28ndiswrapper%29?highlight=%28WifiDocs%2FDevice%29](https://help.ubuntu.com/community/WifiDocs/Device/TRENDnet_TEW-421PC_H/W%3aB1_%28ndiswrapper%29?highlight=%28WifiDocs%2FDevice%29)

it may just do the trick.

---

### Post by kidicarus on 2007-02-14
Ok. A little update on this is in order. I tried out Feisty (Herd 3) and ndiswrapper worked great. I used the same driver and the same ndiswrapper release. Maybe some issue with Edgy? 
As for Feisty, its great (even for an alpha release). Since I was a fan of the NLD 10 interface, I like the Novell-type control panel in Gnome!! The only issues I had were involving the partition editor in the install, it does not show a graphical representation. Does anyone know if this is still being implemented? I liked how Edgy installed, why did they change that? Do they use another editor? GParted? Hmm. Thanks anyways to all who replied.

PROBLEM SOLVED...install Fesity!

---

