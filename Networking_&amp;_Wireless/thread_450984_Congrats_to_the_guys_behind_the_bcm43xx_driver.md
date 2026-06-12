---
title: "Congrats to the guys behind the bcm43xx driver"
date: 2007-05-21
forum: Networking &amp; Wireless
---

### Post by justintime32 on 2007-05-21
When the bcm43xx driver was introduced in Dapper, it was very unreliable for me (which is why I blacklisted it in favor of ndiswrapper, which did work reliably). More recently, I tried out the BackTrack live cd (very nice, I might add) which includes the bcm43xx driver with firmware on it, and I was surprised by how well it worked for sniffing WiFi networks in Kismet. Out of curiosity, I installed the firmware into ubuntu, unloaded ndiswrapper, and loaded bcm43xx. And wow... it works! Not only does it work, but it is also reliable (I haven't got disconnected once yet).

The only issue with it at this point is that it cannot go higher that 11 Mb/s (well, reliably at least). But that's it - it is superior to ndiswrapper in almost every other way. It scans faster, associates faster, and has a better indication of signal strength (and, in addition, it can also see more wireless networks than ndiswrapper can).

I know that reverse engineering hardware and writing new drivers from scratch is not an easy task, and takes time to do right. I also know that developers tend to get more complaints if something doesn't work than praise if it does. So here's some praise... bcm43xx is working great for me! Once it can preform at the full 54 Mb/s, I will never have to go back to ndiswrapper again.

And if Ubuntu can ship the necessary firmware, I will finally be able to get my wireless card working out of the box, something that put me off from Linux initially. (speaking of which, does anyone know if Ubuntu has tried to get permission from Broadcom to distribute the firmware?)

---

### Post by jglen490 on 2007-05-21
That's great news!!

However, I'm quite sure that Broadcom would like receiving royalties from Canonical much more than Canonical would enjoy paying them  There's no way to accurately know how many actual times that Ubuntu is passed to users.  It's not like Ubuntu is "sold" on the retail market.  Thus Canonical would be on the short end of the stick when determining how many installs to pay royalties against.  It's much better that bcm43xx is a generic driver that requires firmware from a driver sold with a wifi card.  Broadcom gets some royalty income from each sale of the cards and the card's user "owns" a valid driver copy.  No need for lawyers and lawsuits - there's enough of that going around as it is.

Another problem is that the vendor of a wifi card with a Broadcom chip may add some features (circuitry, additional driver code) that requires a change to the stock Broadcom driver.So how many variants would Ubuntu need and how would the installer be modified to recognize and install the proper driver/firmware?  Big problem.

Personally, I'm glad for having a choice between ndiswrapper and fw-cutter and any other solutions that come along.  Each solution is better off for the competition, also.  Therefore, you and I are better off.  I'd love to see every wifi chip maker produce a Linux driver solution for their product (even better if it were open source), but that won't happen for a while.

The best we can do is talk it up, Let the chip makers and card vendors know that there is a market.  But for goodness sake don't whine ;) !!

---

### Post by justintime32 on 2007-05-22
> **jglen490 said:**
> That's great news!!

However, I'm quite sure that Broadcom would like receiving royalties from Canonical much more than Canonical would enjoy paying them  There's no way to accurately know how many actual times that Ubuntu is passed to users.  It's not like Ubuntu is "sold" on the retail market.  Thus Canonical would be on the short end of the stick when determining how many installs to pay royalties against.  It's much better that bcm43xx is a generic driver that requires firmware from a driver sold with a wifi card.  Broadcom gets some royalty income from each sale of the cards and the card's user "owns" a valid driver copy.  No need for lawyers and lawsuits - there's enough of that going around as it is.


Personally, if I was Broadcom, I would do it. Ubuntu is essentially offering them a platform where their wireless cards work out of the box, and Broadcom doesn't have to do any work to help whatsoever. They only have to agree to let Ubuntu redistribute the firmware. But, with Broadcom being Broadcom, I'm not so sure that this will happen.

> **jglen490 said:**
> 
Another problem is that the vendor of a wifi card with a Broadcom chip may add some features (circuitry, additional driver code) that requires a change to the stock Broadcom driver.So how many variants would Ubuntu need and how would the installer be modified to recognize and install the proper driver/firmware?  Big problem.


Actually, that's not such a big problem. The bcm43xx guys would update the driver to add support for the new chipset, and corresponding firmware would be packaged. Take a look in /lib/firmware/(kernel version)/ - they are already shipping tons of firmware for different chipsets, so I don't see the problem. Additionally, I don't think that vendors can make changes to their cards that would require a different driver or different firmware, as the chipset manufacturer usually provides the driver.

> **jglen490 said:**
> 
Personally, I'm glad for having a choice between ndiswrapper and fw-cutter and any other solutions that come along.  Each solution is better off for the competition, also.  Therefore, you and I are better off.  I'd love to see every wifi chip maker produce a Linux driver solution for their product (even better if it were open source), but that won't happen for a while.


Competition? You don't want competition with open source drivers. It's not a business. In this case, competition is pointless and there is nothing to gain from it. Additionally, native drivers are better for the long term. ndiswrapper is good in the absence of an acceptable native driver, but is not the best solution. (plus, fwcutter is not a solution, it just rips firmware from the Windows broadcom driver; bcm43xx is a solution).

> **jglen490 said:**
> 
The best we can do is talk it up, Let the chip makers and card vendors know that there is a market.  But for goodness sake don't whine ;) !!

With Dell offering Ubuntu very soon, hopefully they will be able to put some pressure on hardware manufacturers (their TrueMobile cards have Broadcom chipsets in them, which is actually what I have). So I am hopeful :)

---

### Post by alex_anthony on 2007-05-23
On [[COLOR="Blue"]_Engadget,_[/COLOR]]("http://podcasts.engadget.com/2007/05/22/dell-selling-ubuntu-linux-preloads-on-thursday/")
it says that 
>  Dell says that they'll be working with other vendors to create stable drivers for currently unsupported hardware 
Do you think this means we may get a bcm43xx driver? most dell laptops use this, so I think we could get one which works well

---

### Post by onbongos on 2007-05-23
> **alex_anthony said:**
> On [[COLOR="Blue"]_Engadget,_[/COLOR]]("http://podcasts.engadget.com/2007/05/22/dell-selling-ubuntu-linux-preloads-on-thursday/")
it says that 

Do you think this means we may get a bcm43xx driver? most dell laptops use this, so I think we could get one which works well

i think it's a foregone conclusion and, in fact, has already happened

---

### Post by justintime32 on 2007-05-23
> **alex_anthony said:**
> On [[COLOR="Blue"]_Engadget,_[/COLOR]]("http://podcasts.engadget.com/2007/05/22/dell-selling-ubuntu-linux-preloads-on-thursday/")
it says that 

Do you think this means we may get a bcm43xx driver? most dell laptops use this, so I think we could get one which works well

Because Dell extensively uses Broadcom chipsets in their laptops, I think they will at least exert some pressure on Broadcom to allow redistribution of their firmware. Though, they might also push for Broadcom to help with the bcm43xx driver in some way (but that may just be wishful thinking on my part). Either that, or they will only ship Intel wireless cards on their laptops with Ubuntu, who is very Linux friendly.

---

### Post by g8m on 2007-05-23
Yes, good job.

Just installed an old linksys pci wireless card and it worked like a charm. The card popped up as an bcm43xx in lspci.  I was just amazed how I was able to backup my files from the laptop (wireless) to an old computer on the attic (wireless). 

Over the years using linux I am used to things not working, but lately everything just seems to work.

---

### Post by justintime32 on 2007-05-23
> **g8m said:**
> Yes, good job.

Just installed an old linksys pci wireless card and it worked like a charm. The card popped up as an bcm43xx in lspci.  I was just amazed how I was able to backup my files from the laptop (wireless) to an old computer on the attic (wireless). 

Over the years using linux I am used to things not working, but lately everything just seems to work.

Yes, I agree. When I was using RH9, the only external hardware that worked was my Printer (an HP, of course). Forget wireless, sound, webcam, and almost everything else that wasn't part of a typical computer. Fast forward to Feisty, and now my Logitech QuickCam Fusion is even working out of the box. Very nice.

On a somewhat related note, I have to say that NetworkManager is also very nice. It works good with every wireless card that I've used with it, and makes wireless a breeze (finally, I can have full WPA support without messing around with hard to use, unintuitive wpa_supplicant configuration files). I think the only major feature it is missing right now is Static IP, but that's not a problem for me.

The only annoyance is the fact that it requires the Gnome Keyring, which is annoying to unlock upon login. There should definitely be an option for this. If someone manages to get direct access to my computer, I have bigger problems to worry about than the loss of a WPA password (I can always change it if needed).

---

