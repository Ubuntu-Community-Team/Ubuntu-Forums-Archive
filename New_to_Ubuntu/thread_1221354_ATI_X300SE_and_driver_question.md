---
title: "ATI X300SE and driver question"
date: 2009-07-23
forum: New to Ubuntu
---

### Post by Whydoe on 2009-07-23
Before I go and wreck my system by installing something I may not need I have to ask; Is it better to install the ATI driver from Application --> Add/Remove (ATI Binary X.org driver) or download the latest .run file from ati/amd support?  I have the file ati-driver-installer-9-3-x86.x86_64.run.  I'm just having issues with some games/screensavers locking up the computer and thought setting up the fglrx driver may fix this. 

Anyone else install the latest drivers from either location (I'm obviously using an X300SE card) and using Jaunty?

---

### Post by Whydoe on 2009-07-25
So, um... no.  Don't do it.  Added ATI Binary X.org Driver and it just garbled my system.  Had to use recover and remove xorg-driver-fglrx and use xfix.  No big deal.

---

### Post by Mark Phelps on 2009-07-25
> **Whydoe said:**
> Before I go and wreck my system by installing something I may not need I have to ask; Is it better to install the ATI driver from Application --> Add/Remove (ATI Binary X.org driver) or download the latest .run file from ati/amd support?  I have the file ati-driver-installer-9-3-x86.x86_64.run.  I'm just having issues with some games/screensavers locking up the computer and thought setting up the fglrx driver may fix this. 

Anyone else install the latest drivers from either location (I'm obviously using an X300SE card) and using Jaunty?

Do NOT attempt to install the ATI drivers.  As has been pointed out LOTS of times in this forum, AMD/ATI has dropped support for the older legacy cards from their current drivers, and the older drivers that DO support these cards will not work in Ubuntu 9.04.  You're stuck using the open source drivers like a lot of the rest of us.

---

### Post by Whydoe on 2009-07-26
Yes.  I found that out the hardish way.  It was easy enough to recover from.  I'm just going to save up for an NVidia card.  9500 or something like that.  

I did read other posts on forum about ATI dropping support but there was a lot of conflicting information from the AMD support page.

---

