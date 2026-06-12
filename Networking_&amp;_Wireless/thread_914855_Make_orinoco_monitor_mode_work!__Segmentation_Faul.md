---
title: "Make orinoco monitor mode work!?  Segmentation Fault? Revert to 0.13e?"
date: 2008-09-09
forum: Networking &amp; Wireless
---

### Post by trylleklovn on 2008-09-09
Okay, so i had a working ubuntu 8.04 install running, decided i wanted to play around with airodump, so i needed monitor mode.

My dwl-660 uses the orinoco driver (im aware it doesn't support injection at all). In 8.04 this is version 0.13e of the orinoco driver, as far as I have understood. 

This results in that i need to either patch the 0.13e driver, to enable monitor mode, or upgrade to 0.15 which has monitor mode without patch.

Tried patchin the 0.13e driver firstly, by downloading source+patch, applying patch and then attempting to compile it, but that resultet in a bunch of errors probably due to kernel changes. (i run 2.6.24.19).

Then i tried compiling some 0.15 source i found, but resulted in errors again.

Then i tried using the latest SVN of 0.15 and magicly this compiled without any errors! The momentary outsight a successful outcome was cut of when i loaded the driver, and it merely began spitting Segmentation Fault.

Now i've overwritten my old perfectly good 0.13e driver from the /lib/modules... with a new orinoco_cs that simple fails. 

Now my wish for a solution is either

1. reverting back to the 0.13e driver, which came with the 8.04. (could i just find someone with the same kernel and copy it over manually?)

2. somehow making 0.15 compile correctly so that it doesn't result in Segmentation Faults.

---

### Post by trylleklovn on 2008-09-10
Now i managed to pull off the orinoco_cs modules from another installation and getting this system running on wireless again.

But basicly im back to square one here. Has anyone managed to compile orinoco 0.15 on 8.04 with kernel 2.6.24.19? Or has anyone managed to compile 0.13 patched with monitor mode support?

Or perhaps i can use the hostap module? Im not certain if that works with my dwl-660 card, but if i unload orinoco_cs and load hostap_cs the card stays inactive. I've tried binding the card in /etc/pcmcia/config, but not use this file is even used for binding drivers in 8.04.

---

