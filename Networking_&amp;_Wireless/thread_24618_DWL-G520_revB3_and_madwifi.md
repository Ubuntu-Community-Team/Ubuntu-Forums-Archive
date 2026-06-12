---
title: "DWL-G520 revB3 and madwifi"
date: 2005-04-07
forum: Networking &amp; Wireless
---

### Post by geekboyUK on 2005-04-07
I've installed Ubuntu 5.04 on a desktop PC which has a D-Link DWL-G520 rev B3 wireless network card which will not function. 

When madwifi tries to start the card it fails:
  ath%d: unable to attach hardware; HAL status 13

So I did some digging, and apparently there is a newer version of madwifi that supports this card (and several others using the Atheros AR5412 chip).

Question is, my PC only has WIFI network access (no wires), so I need to build the new madwifi by getting the source files.  I've found the source files online, but when I extract then try to make I'm given:
  Makefile.inc:94: *** KERNELPATH must be defined.  Stop.

Do I need Ubuntu sources also?  

There is no .deb file to download for this version yet.

Anyone else solved this problem?

Please help!

Thanks

Chris

---

### Post by mdelves on 2005-04-08
Yes, madwifi is looking for the kernel source, so this is also required. You will need to burn the required files onto a CD and then install them from there.

Also, I know D-Link does a lot of chip hopping and it maybe (not 100% sure) that your card is using the acx111 chipset instead of the atheros.

Hope you get it all up and running.

Later,
Matthew Delves

---

### Post by acariquara on 2005-04-10
[QUOTE=mdelves]Yes, madwifi is looking for the kernel source, so this is also required. You will need to burn the required files onto a CD and then install them from there.

Also, I know D-Link does a lot of chip hopping and it maybe (not 100% sure) that your card is using the acx111 chipset instead of the atheros.

Hope you get it all up and running.

Later,
Matthew Delves[/QUOTE]
 If the guy bought a USA-made DWL G520 it's prolly an Atheros-based one. "International" DWL-G520+ (the 'plus' meaning *with added crappiness* :) ), that's a cheap, unreliable, dreaded ACX111 one.

---

