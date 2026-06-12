---
title: "Ubuntu will not detect my wirelss card.. please help"
date: 2007-12-09
forum: Networking &amp; Wireless
---

### Post by jigsaw315 on 2007-12-09
I have a linksys wireless pci card installed on my computer... when i had windows it detected the card fine and i have no problems with my internet... but i recently got ubuntu and i paritinoned the hard drive to where i run both windows and ubuntu on the same harddrive

anyways i am having trouble because ubuntu is not detecting my card.. when i go to the wireless network options "wirless" is not even an option on the list

My linksys card model number is: WMP54GX4 its a Wireless-G PCI Adapter with SRX 400

i figured that what i needed was a linux driver for the card but i was unable to find one

please help?

---

### Post by Squish on 2008-02-24
Bump
Same problem

---

### Post by toa on 2008-02-24
> **jigsaw315 said:**
> I have a linksys wireless pci card installed on my computer... when i had windows it detected the card fine and i have no problems with my internet... but i recently got ubuntu and i paritinoned the hard drive to where i run both windows and ubuntu on the same harddrive

anyways i am having trouble because ubuntu is not detecting my card.. when i go to the wireless network options "wirless" is not even an option on the list

My linksys card model number is: WMP54GX4 its a Wireless-G PCI Adapter with SRX 400

i figured that what i needed was a linux driver for the card but i was unable to find one

please help?

Try the wireless card with Ubuntu the Live CD if recognized then your missing network drivers or so called 'restricted drivers'..

Try the Live CD if it knows the card.

---

### Post by Squish on 2008-02-24
it doesnt
Restricted drivers/modules does nothing. Even tried it on 8.04

---

### Post by kaginken on 2008-02-24
Please post result of:

iwconfig 

and

iwlist scan

Also, is the link light lighting up?  

If you're in dual-boot setup, does this same hardware config work in winblows?

---

### Post by uberlube on 2008-02-24
Also dont fret if the live cd dosent detect your card. You can still install the drivers through other means like ndiswrapper.

---

