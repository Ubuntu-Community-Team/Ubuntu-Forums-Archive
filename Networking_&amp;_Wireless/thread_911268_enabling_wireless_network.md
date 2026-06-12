---
title: "enabling wireless network"
date: 2008-09-05
forum: Networking &amp; Wireless
---

### Post by helpplzhelpplz on 2008-09-05
Hi all,

I just installed Ubuntu 8.04 as a dual booted O/S in conjunction with vista, but I cannot get my wireless network card to work.  I went thru support pages and found my way to a terminal typing given commands to see if the card was enabled...turns out it is disabled.

Can someone plz tell me how to enable the card?  Or tell me how to find the correct driver (not sure what type...not .inf?) along with subsequent steps on how to get my wireless to work? 

Thanks very much to anyone who can assist...much appreciated.

---

### Post by knix on 2008-09-05
use lspci to figure out chipset.
you will possibly need ndiswrapper. if you use ndiswrapper, you use the .inf file
if you have a broadcom card, use wl or ndiswrapper (bcmwl5.inf)
for wl, see [http://ubuntuforums.org/showthread.php?t=880218]("http://ubuntuforums.org/showthread.php?t=880218")

---

