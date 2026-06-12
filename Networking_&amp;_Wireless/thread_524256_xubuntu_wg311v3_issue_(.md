---
title: "xubuntu wg311v3 issue :("
date: 2007-08-12
forum: Networking &amp; Wireless
---

### Post by dwink1217 on 2007-08-12
alright guys, here's the deal.

i recently bought a wireless router and a wireless network card.
both are netgear.

the computer i'm using right now is running ubuntu studio. and the computer upstairs is quite a bit older and running Xubuntu Feisty.

I put the wireless network card into the old computer, and did all the ndiswrapper stuff.

The card and driver all show up.

However... when i go to iwconfig, it says..

lo       no wireless extensions

I'm not sure what the problem is. i KNOW that the wireless is working because i got the Wii on the floor below me set up on the WiFi Network.

any help would be greatly appreciated.

PS. If you want me to give specific outputs, please tell me ALL of the specific outputs you might want. because running up and down stairs and printing sheets is no fun :| i'd like to do that all at once.

---

### Post by moore.bryan on 2007-08-13
> **dwink1217 said:**
> The card and driver all show up.
*how do you know this?  (i.e. what command did you type to give you this definitive info?)  i'd suggest posting the output of ```
lspci
``` and we can start from there.*

---

### Post by dwink1217 on 2007-08-14
i used ndiswrapper -l to find out. it showed the driver and the device that was using it.

but i figured it all out. i just needed to use the windows 98 drivers on the netgear cd as opposed to the marvell drivers that it says to use in the wiki and everything works fine now.:)

i just figured i'd make this post to help anybody else trying to use this card (cause it's cheap!)

---

