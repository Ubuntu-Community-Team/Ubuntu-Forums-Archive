---
title: "Help, DWL-520+ not working"
date: 2007-02-22
forum: Networking &amp; Wireless
---

### Post by M$LOL on 2007-02-22
I bought a DWL-520+ because I thought it would work out of the box, as it says on the HCL. I inserted the card, turned on the comp and tried iwconfig in the terminal. It says lo no wireless extensions and sit0 no wireless extensions. The card comes up as "Network Controller Texas Instruments ACX 22mbps Wireless Interface" in lspci. I thought it was supposed to work?

BTW, it's the x64 version of edgy if that helps.

---

### Post by M$LOL on 2007-02-22
I downloaded the 6.06 LTS x64 version, and it can't detect the card either. Why does the HCL say that it works when it doesn't?

---

### Post by Titus A Duxass on 2007-02-22
site:ubuntuforums.org DWL-520+ may help you.

Honestly this has been raised many times, try a search from time to time.

---

### Post by M$LOL on 2007-02-22
I found this
> **FrodoB said:**
> If you have access to the card you need to boot the system and run from a live CD and then publish the output of:

lspci

There is a chance that this card will just work with a regular install of Edgy, in fact it may just work on the live CD. Many of these cards have the TI ACX111 chipset which is supported in Edgy. The only thing to note is that an install from the Alternate CD does not work after a reboot until the linux-restricted-modules have been installed for your particular kernel.

The output of lspci will tell us if we are on the right track here.
It says ACX in my lspci output. Does this mean I need the linux-restricted-modules, and if so, how do I get and install them?
EDIT: That should be ACX 100. My mistake.

---

### Post by dca on 2007-02-22
The 520 revision B works out of the box using restricted modules.  Rev B is the Atheros chips...  Rev A uses Marvell which would require ndiswrapper...

---

### Post by M$LOL on 2007-02-22
OK, I got it working with restricted-modules. Thanks for the info.

---

