---
title: "Encore ENL832-TX ethernet controler problem :("
date: 2005-09-21
forum: Networking &amp; Wireless
---

### Post by antox on 2005-09-21
Hi everybody!

Couple of days ago I installed Ubuntu, and I liked it too much!
But there's a little problem: it won't recognise my ENCORE ENL832-TX-ICNT network adapter and I cannot connect to internet via ADSL. I tryed to compile driver module, but I get a lot of errors (even after installing essential tools and kernel headers). I think it is necessary to have installed whole kernel source tree, but I couldn't find it in internet (uname -r gives 2.6.12-8-386 version). And I don't know what to do now...  :-| 

PLEASE, HELP!  ](*,)

---

### Post by mlomker on 2005-09-22
If the card doesn't have a driver then it must be an unusual card.  I know how hard it is to compile a working kernel and I think it'd be a lot less trouble to just buy a different card.

Do a search in Synaptic for **linux-tree**.  It's in there.

---

### Post by mips on 2005-12-06
Your card uses a Realtek 8139 chipset so try and use that driver. there are different versions of this driver so you might have to try more than one.

The Realtek cards do seem to be a bit problematic though.

---

