---
title: "How do I switch to closed-source drivers for ATI Radeon X1250 mobile graphics?"
date: 2009-07-05
forum: New to Ubuntu
---

### Post by diablo75 on 2009-07-05
I have an HP laptop with an ATI Radeon X1250 graphics chipset in it.  Some of the effects compiz is able to do (such as the Burn/Fire effect) is has HORRIBLE performance when rendered, but I know for a fact the card is capable of so much more (based on the gaming experience I get from playing games from the Windows partition).

I've caught snippets here and there by people telling me that my laptop is likely using the open-source ATI drivers and that others in my situation have had better luck/performance by using the close source drivers.  Though I've also had people tell me flat out, "Just stick with the open-source drivers." without giving me a decent reason to do so.  I at least want to try to get the close source drivers working to see if it makes a difference for a better.  

So how do I install these drivers to try them out?  Any help in doing this would be much appreciated!

---

### Post by Abu_Dayya on 2009-07-05
Is there anything listed in System -> Administration -> Restricted Hardware ?

---

### Post by diablo75 on 2009-07-05
> **Abu_Dayya said:**
> Is there anything listed in System -> Administration -> Restricted Hardware ?

No and there never has been.  Out of the box, Compiz was enabled, but no restricted drivers are in use or shown in the Hardware Drivers thing.

---

### Post by Abu_Dayya on 2009-07-05
I would download the latest driver from amd's website, and follow the installation instructions.

Thats just me though, you can wait for other more experienced guys to answer this

---

### Post by Abu_Dayya on 2009-07-05
the drivers in their website *ARE* the propriatary, closed-source drivers

---

### Post by 3rdalbum on 2009-07-05
I wouldn't bother trying to install the proprietary ATI driver. It doesn't support the X1250 anymore, and the old driver doesn't work on Ubuntu 9.04. Installing the driver is likely to break things.

---

