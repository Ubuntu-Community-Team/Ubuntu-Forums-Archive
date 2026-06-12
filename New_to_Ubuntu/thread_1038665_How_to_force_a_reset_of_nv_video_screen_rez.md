---
title: "How to force a reset of nv video screen rez?"
date: 2009-01-13
forum: New to Ubuntu
---

### Post by Razmear on 2009-01-13
I've been fighting to get the Nvidia GeForce MX440 card working under 8.10. From other posts I can tell that this card is a problem child and I'll probably just give up soon and get another cheap AGP video card. 
Anyways, here is my current issue. 
Using the 96.xx driver I am locked into 800x600 resolution. There is no method to change it, even editing xorg.conf does not work. The driver is listed as not working in the 8.10 docs and the 180.xx driver is not compatible with my video card. 
I was able to have limited success using the nv driver instead of the 96.xx version driver. I was able to select screen resolutions under the Preferences option and things were starting to look up. I then selected a screen rez that the monitor could not handle which made the screen unusable. There was no 'revert in 15 seconds' dialog, so now the nv driver is stuck in that rez. Even after changing to the nvidia driver and back again the rez is stuck at the unusable setting. 
I am guessing that the bad rez is saved in a config file somewhere and gets reloaded everytime I try to use the nv driver again. 
If someone can tell me how to wipe out or reset this nv screen rez it would let me get back to searching for a compatible screen rez for this card using the nv driver, and I might be able to save $30 on a new vid card. 

I have also tried: sudo dpkg-reconfigure xserver-xorg but it never asks any questions about video settings, just the keyboard. 

Thanks for any help you can offer,
eb

---

### Post by Razmear on 2009-01-13
Anyone?

eb

---

