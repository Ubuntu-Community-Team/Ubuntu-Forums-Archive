---
title: "Madwifi and Ndiswrapper, two network cards at the same time?"
date: 2007-12-17
forum: Networking &amp; Wireless
---

### Post by codeandeffect on 2007-12-17
Hello all, I haven't seen this exact question asked before so here goes:

With two separate wireless cards, can I use Madwifi for one and Ndiswrapper for the other? They don't appear to sit happily side by side.

I have an amd64 Acer 5051 laptop, for which I have to run ndiswrapper and appropriate driver to use the built in wifi - it works a treat.

However, I really need to use Monitor mode - it's for a research project. Now my wireless hardware wont work with Madwifi (the dreaded 'Hal Status 13'), and Ndiswrapper doesn't support Monitor mode. so I've had to look at using a separate wifi card.

I have plugged in a Netgear WG511U, a card supported by Madwifi. I have had this up and running, in monitor mode and again, it works a treat.

The trouble I'm now having is running Ndiswrapper on my other internal card - instead that is, not as well as (not yet anyway).

If I pop the WG511U out of the slot, reboot, run all the usual commands to  to get Ndiswrapper going, make sure ath_pci is not running, I can get a list of APs, I can scan, but I cannot connect to them.

Ideally I'd like to run them both at the same time, if that's not possible being able to run one at a time without having to restore from backup or go unistalling  in between would be fine.

I'm getting the impression though that just the presence of Madwifi seems to make ndiswrapper inoperable.

All thoughts welcome, thanks

---

### Post by kevdog on 2007-12-17
Just some thoughts

Ive tried using madwifi and ndiswrapper at the same time (broadcom chipset).  I dont have any problems using them independently such as driver crash.  I dont think however you can run the cards per se at the same time.  netzier is the user I would check with.  Possibly something about network bonding.

---

### Post by codeandeffect on 2007-12-17
Thanks, that's a start.

When I got the WG511U (atheros chipset) running happily, I went back to try the internal Atheros ar5006eg running under Ndiswrapper - decided to start without the other card even installed and work up to having them both running, but it fell at the first hurdle.

I'd like the internal to bond with an AP for internet access, and just leave the WG511U monitoring the ether.

Cheers

---

