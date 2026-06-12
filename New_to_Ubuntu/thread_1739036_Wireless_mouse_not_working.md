---
title: "Wireless mouse not working"
date: 2011-04-25
forum: New to Ubuntu
---

### Post by Pragz28 on 2011-04-25
I have a wireless mouse and keyboard. The keyboard is working fine on Ubuntu but the Mouse isn't, I can't click on anything. The cursor moves around fine though (Microsoft Wireless Mouse 700 V2.0)

I have two operating systems, XP and now Ubuntu, so a dual boot.

The Mouse works fine on XP, however on Ubuntu it will work for around 5 minutes and then randomly stop clicking. 


What can I do?

Thanks

---

### Post by LewRockwellFAN on 2011-04-25
I'm no expert but you might try System/Administration/Hardware Drivers and let it look for a better driver. Then select and activate the one labeled "recommended" if it is not already active. If that doesn't work, try System/Administration/Software Sources and check some of the unchecked sources, especially "proprietary drivers".  Then System/Administration/update manager and press the check button. Install any updates, then go back and try step one, System/Administration/Hardware Drivers and let it look for a better  driver. Then select and activate the one labeled "recommended" if it is  not already active. It's worth a try.

---

### Post by josephmills on 2011-04-25
I am to new to this all but lets try this make sure that your wireless mouse is plugged in and then go to applications-->accessories-->terminal then type in ```
lsusb
```then post that here thanks

---

