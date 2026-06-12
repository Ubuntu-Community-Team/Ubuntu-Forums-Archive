---
title: "D800 ndiswrapper pcmcia (no hardware present)"
date: 2005-05-01
forum: Networking &amp; Wireless
---

### Post by cdburgess75 on 2005-05-01
I have a D800 without a built in wireless card.  I have purchased 2 pcmcia 802.11g cards and I cannot make ndiswrapper work for either.  I get the same problem with both cards.  
After loading the inf file i do a ndiswrapper -l
I can see the driver (for both) and it says present but it never says hardware present.  (like I thought it was supposed to do)

I have followed the forums and doublechecked my ndiswrapper install and I am still at a loss.  Any help would be greatly appreciated.

cards
1. linksys wpc54g ver. 4
2. d-link   dwl-g630

Dave

---

### Post by az on 2005-05-01
I am assuming that you are talkign about a loptop.

Is pcmcia-cs installed?

---

### Post by cdburgess75 on 2005-05-03
[QUOTE=azz]I am assuming that you are talkign about a loptop.

Is pcmcia-cs installed?[/QUOTE]
I did a default install of 5.04.  I'm not sure if its loaded.  Im not sure how to tell if pcmcia-cs is loaded....I do see PCMCIA services start up at boot.  My card doesnt power until hotplug though.

---

