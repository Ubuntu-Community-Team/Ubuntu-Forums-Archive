---
title: "how can i activate my hp 6715s notebook wireless card"
date: 2008-10-14
forum: Networking &amp; Wireless
---

### Post by osowo on 2008-10-14
thank you very much my people,guess u have the solution to this question.
how can i setup my wireless NIC to run on ubuntu.
thank you very much

---

### Post by Ayuthia on 2008-10-14
> **osowo said:**
> thank you very much my people,guess u have the solution to this question.
how can i setup my wireless NIC to run on ubuntu.
thank you very much

We will need a little help.  Can you go into the Terminal and post the results of lspci -nn?  It will help us identify your wireless card.

---

### Post by beernarrd on 2010-12-30
A bit late but anyhow:
The problem is not the wireless itself, the problem is the "hardware" button on the top of the keyboard that don't go blue (actually it is software driven button).

Try to set the BIOS option "lan/wlan switching" to OFF.
After that, my button went blue when booting up ubuntu.

(I ve done some ndiswrapper stuff a couple of years ago - i don't remember the details, but as I said, the main problem was in the hw button).

---

