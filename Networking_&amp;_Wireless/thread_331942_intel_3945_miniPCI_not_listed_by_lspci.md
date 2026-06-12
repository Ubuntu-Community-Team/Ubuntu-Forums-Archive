---
title: "intel 3945 miniPCI not listed by lspci?"
date: 2007-01-05
forum: Networking &amp; Wireless
---

### Post by eudoxos on 2007-01-05
Hello,

in my Fujistu-Simemens Lifebook b-2562, I replaced the factory-provided lan/modem combo by a new minipci Intel Pro/Wireless 2915abg wireless card. The problem is that the card doesn't show up in lspci at all (hence it is not a driver problem), but the miniPCI slot itself worked for the lan/modem card flawlessly.

I know that the card should be installed in Centrino systems only (this laptop predates Centrino by a few years), but forums revealed that the 2200 cards work with regular miniPCI just as well, even without the rest of Centrino (chipset etc). Can this be the problem?

What do you suggest? Should I return the card as defective immediately? Has someone had that problem also?

Regards, Václav

---

### Post by deculpep on 2007-07-11
I had the exact same idea (and ran into the exact same problem today).  I just picked up a Fujitsu B-2562 as well and decided that swapping out the MiniPCI ethernet/modem card with a wireless card would be one of my first moves.  MiniPCI, that's what standards are for, right?  I've always had excellent results with the Intel wireless cards (and so has most everybody else), so the purchase of a 2915 was a no brainer.

Or so I thought.

On Xubuntu feisty...
Nothing in the network-manager app.
lspci doesn't list the adapter.
the module ipw2200 is not loaded, and when I load it manually, it doesn't bind a network interface to the device.

Sigh, I guess a search on the forums would have brought this to my attention.  I was really hoping to go with a minipci solution (especially since I wired two antennas inside the base and screen) instead of a bulky PCMCIA card.

So is there anything I can try?  eudoxos, what did you end up doing?
The minipci slot worked just fine with the ethernet/modem card.  Possibly a bios issue (I've got the latest and last version from Fujitsu, circa 2003 or so)?  Nothing in the BIOS on the card at all, but normally with the ethernet card in I can set some options about booting from the network card etc.

Its like the hardware isn't letting Ubuntu *see* the new card .  Sorry I'm not going to spend the time to get windows up and running on this machine, but I will try the minipci card in another (more modern, centrino based) laptop in both OS's to see if it is an issue with the card.

---

### Post by eudoxos on 2007-07-12
Some people told me that there are different version of minipci. I gave that card to a friend of mine with a more recent notebook (thinkpad) and it works very well. So I keep using PCMCIA wifi (which still sucks, since after 2.6.12, pcmcia doesn't detect acrd insertion at runtime and have to say "pccardctl insert" and there are other weirdnesses as well - I suspect older ACPI (?) for that, again). Long live, standards! :mad:

---

