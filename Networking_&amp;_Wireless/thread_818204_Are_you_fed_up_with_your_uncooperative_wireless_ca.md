---
title: "Are you fed up with your uncooperative wireless card?"
date: 2008-06-04
forum: Networking &amp; Wireless
---

### Post by Bartender on 2008-06-04
This won't work for everyone, but I wanted to relay how easy it was in our situation.
My Dad (78 years old, a new convert) asked me to install Ubuntu to his new HP/Compaq notebook.  I got his Atheros 5007 card to work for one hour, then the latest kernel upgrade knocked it out.  We live 700 miles away from him.  Needed a more reliable fix.  Opened up our Acer Centrino notebook and his HP, took pictures and notes, then carefully removed the little tiny wires that clip onto the wireless cards, backed out the two little tiny screws, and swapped them.  Ubuntu immediately recognized the Intel 4965 card and connected to his wireless network.  Shut down, booted into Vista, Vista saw the new device and got drivers, and he was online in Vista too.
Great.  But now I was stuck with the Atheros.  Got it working in the Acer.  Went to Amazon.  Typed in "intel 4965".  Ordered one from Amazon, not one of their resellers.  About $38.  Didn't know if it'd be a used part or what.  Arrived UPS a few days later in an Intel box with Intel directions, Intel driver CD, tucked inside a cute little plastic wallet that had "Intel" stamped on it.  Removed the Atheros, plugged in the 4965, it works like a champ.  The Intel card seems to give better signal strength than the Atheros too.  

If you have a relatively new laptop and you're sick and tired of fighting that Broadcom/Atheros/whatever card, you might want to consider just buying an Intel 4965 and being done with it. There may be some combinations of hardware that don't work, but I think the mini-PCI (or whatever it's called) slot in modern laptops is pretty much universal.

The two miniscule wires that attach to the card are delicate, and so are the even-smaller ring-and-pin fittings on the cards.  The wires should be wriggled off and pushed on with the utmost care.

You'll need: 
1) a good quality small Philips screwdriver
2) the ability to carefully manipulate little tiny parts - you do not want to lose one of the two screws that holds down the card inside your notebook, or mangle those tiny connectors!
3) A good source of illumination
4) Unless your eyesight is very good, some magnification.  I used my trusty hobby visor.

EDIT: A quick search reveals that even the trusty 4965 doesn't work for everyone.  Wish I knew why that is...

---

### Post by chili555 on 2008-06-04
An excellent suggestion! Before any of you attempt this, please make sure the BIOS on your laptop doesn't have a whitelist that only allows certain wireless cards. Here is an example: [http://www.thinkwiki.org/wiki/Problem_with_unauthorized_MiniPCI_network_card](http://www.thinkwiki.org/wiki/Problem_with_unauthorized_MiniPCI_network_card)

Many other laptop manufacturers utilize a whitelist. I recommend careful research before you press the "Place Bid" button.

There are scary work-arounds for _some_ laptop models.

---

### Post by Bartender on 2008-06-04
Thanks, chili -
Things are never as simple as they oughta be.  I had no idea there was such a thing as a BIOS whitelist!

---

