---
title: "Patching workaround for e100 driver"
date: 2006-09-19
forum: Networking &amp; Wireless
---

### Post by Haim on 2006-09-19
The e100 driver returns a corrupt eeprom and fails to load.

(thinkpad 20, intel etherject minipc).

I've given up on the idea of doing something about the eeprom, and considering its been ok with windows I'll risk it being wrong.

So instead I've found a patch for e100 driver that will basically ignore the check.  However for the life of me I can't work out the steps for patching.  Can someone give me a quick list of the steps I've gotta do.....bearing in mind I can't update over the net as no ethernet, however I can download with windows and have available to the linux partition.

So far i think.....

- somehow download and install linux headers package for the kernal on my ubuntu partition. Remember I can only dload from windows.

- get e100.c the source for the driver.

- use patch command with the patch file i have on the e100.c

- Does patch also do the make and all that?  or do I need to compile and apply the driver to the kernal?

- Can this be done more easily by changing this to a loadable module version of the same driver?

Cheers for any help.

---

