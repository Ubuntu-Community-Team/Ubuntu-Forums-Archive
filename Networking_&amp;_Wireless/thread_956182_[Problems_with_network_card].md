---
title: "[Problems with network card]"
date: 2008-10-23
forum: Networking &amp; Wireless
---

### Post by Jaypur on 2008-10-23
Hi, my friend is having a problem with the network card. He was using ubuntu 7.04, and all configs were ok, and today he installed 8.04 and what he is trying to do is...

**He gets the the driver package, follows the installing instructions, but at the time to run hsfconfig, it asks:  *"Where is the Linux source build directory that matches your running kernel? [/lib/modules/2.6.22-14-generic/build]" *so he writes it, but it doesnt read it, and get an error - *"ERROR: Module build failed"***


the error log is:



(cd /lib/modules/2.6.24-19-generic/build && make "CNXT_KERNELSRC=/lib/modules/2.6.24-19-generic/build" "M=/usr/lib/hsfmodem/modules" "CC=gcc" clean)
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-19-generic'
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-19-generic'
(cd /lib/modules/2.6.24-19-generic/build && make "CNXT_KERNELSRC=/lib/modules/2.6.24-19-generic/build" "M=/usr/lib/hsfmodem/modules/GPL/hda" "CC=gcc" "HDA_CFLAGS=-DFOUND_KZALLOC  -DFOUND_TLV   -DFOUND_IRQ_HANDLER_T -DFOUND_DELAYED_WORK " clean)



the network card is:
[B]
 PCI SoftV92 Modem, diver: SL2801[/B]



a lot of people now maybe is asking, why didn't he post by himself?

its because, he doesn't know much english... 



thx!

---

