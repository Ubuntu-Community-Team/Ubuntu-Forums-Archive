---
title: "monitor mode and wpa w/ ndiswrapper"
date: 2007-03-07
forum: Networking &amp; Wireless
---

### Post by cr4z3d on 2007-03-07
What I'm currently trying to do is get my wireless card (Netgear WG511v1) into monitor mode. The problem is, apparently you can't do that if you're using ndiswrapper. The other problem is my wireless is WPA encrypted, which the prism54 drivers don't support when using network manager. 

So what it all comes down to is, how do I get WPA encryption using prism54 drivers, or is there a non-stable release of ndiswrapper that will let me put my card in monitor mode. Or do I have to keep switching between the two drivers to get what I want?

Finally, if there's no easy solution, what's a good wireless card (PCMCIA) that can do everything I'm looking for?

---

### Post by Dwiman89 on 2008-02-23
I need to know to get monitor mode to work with my Netgear wg311v3(Marvell chipset) or if it is possible. I have to use Ndiswrapper

---

### Post by kevdog on 2008-02-23
ndiswrapper never supports monitor mode -- period.  Cards that use the madwifi drivers (some atheros cards), and ra based chipsets support monitor modes.  There may be other chipsets (like orinoco), however atheros and ra are the two chipsets that usually come up in conversation.  Possilbly you can do this with prism devices, but Im not sure.

---

### Post by Dwiman89 on 2008-02-23
OS it looks like I have to get a new card in order to use monitor mode?

---

