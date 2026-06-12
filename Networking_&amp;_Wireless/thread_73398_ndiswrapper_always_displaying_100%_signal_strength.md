---
title: "ndiswrapper always displaying 100% signal strength"
date: 2005-10-08
forum: Networking &amp; Wireless
---

### Post by Confuse on 2005-10-08
Does anyone know how to fix that? I'm using ndiswrapper with the Broadcom bcmwl5 card. Ndiswrapper always shows the signal strength as 100% sorta annoying. Thanks.

Damian

---

### Post by spd106 on 2005-10-10
As far as I am aware this is fairly normal. The problem is that Broadcom have not released the specs for the chips used on these cards, so no one can write a driver that works 100%. That's why we fall back to using ndiswrapper that works by imitating the windows api for wireless devices. Check out the [ndiswrapper website]("http://ndiswrapper.sourceforge.net/") for more information about this. I suppose the best we can hope for is the wonderful developers of ndiswrapper to work some sort of miracle. So you might want to keep tracking the latest revisions. I'm just greatful it works at all!

The best way to get fully functional wi-fi is to buy a card the uses a chipset that is supported in linux, such as Atheros, Prism, etc. This isn't easy as the vendors change chips all the time. Don't expect any help from Dell, Belkin, D-link etc for non-windows problems.

---

