---
title: "No Wireless connection"
date: 2007-11-19
forum: Networking &amp; Wireless
---

### Post by zephyrus17 on 2007-11-19
I have done a fresh install of 7.10, but my wireless N does not work on my Dell 1501. I have tried Fn+F2 but the wireless signal would not light up.
Tried bcm43xx-fwcutter as well, but could not get a detection on the Restricted Drivers manager.
I have attempted to try ndiswrapper 1.49 by downloading the .tar.gz file. But the Install readme lost me in the first sentence.

Any help would be much appreciated.

---

### Post by daengbo on 2007-11-19
Can you go to System -> Preferences -> Hardware Information and find the chipset of your wireless card?

---

### Post by zephyrus17 on 2007-11-19
It's: BCM4328 802.11a/b/g/n

I looked at the the sticky above for the "How To Broadcom...", but it says it doesn't work for 7.10
(Is Ubuntu Gnome or KDE?)

---

### Post by zephyrus17 on 2007-11-19
Bump.

---

### Post by MrSootentai on 2007-11-19
Have you tried using the Broadcom Easy Method that is stickied at the top?

---

### Post by zephyrus17 on 2007-11-21
I've been trying the Gnome online method, but after
"Building tag database... Done",
It says
"E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)"
"E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using 
it?"
"./bcm43xx-ndiswrapper.sh line 125: pushd: ndiswrapper-*: No such file or directory"

And, after a few lines,

[COLOR="Navy"]"Inserting ndiswrapper module...[/COLOR] FATAL: Module ndiswrapper not found."

Is this correct?


One problem is that the wifi light is on, but will not turn off when I press Fn+F2, So, I can't really know if the wifi is really on or not.

---

