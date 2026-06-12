---
title: "Wake On Lan: Dell 8400"
date: 2008-10-26
forum: Networking &amp; Wireless
---

### Post by keatonvictor on 2008-10-26
Hi everyone

Il start by giving you a little background on the problem.

1. I have successfully setup WakeOnLan before using other machines & network however something seems to be preventing me from setting it up this time.

Ok.. 

I have a Dell 8400 Desktop which as far as I can see form the BIOS has the ability for remote booting, aka wakeonlan. I set this to "on" aswell as running the script found at [http://ubuntuforums.org/showthread.php?t=234588](http://ubuntuforums.org/showthread.php?t=234588).

However Nothing is working. When I type the following....


(ip shielded on purpose)

wakeonlan -i 86.17*.***.**  00:11:11:3e:2e:99

I get...

"Sending magic packet to... 00:11:11:3e:2e:99

However when I run this using a incorrect mac address I get 

"cannot resolve address"

This says to me that the device must be recognised, however no wake on lan. any ideas on whats going on ?


Thanks in advance

---

### Post by Blue_Screen on 2009-10-26
keatonvictor,

I have the same Dell as you and am attempting to set up something similar.

When you set the WOL settings in the BIOS does the light by the RJ-45 jack on
you computer stay illuminated?  MIne does not and from the descriptions of other 
people with their NIC cards there is usally a light that stays on when the 
computer has been turned off.

If you light is on you are a step ahaed of where I am, if not we may be facing a 
similar problem and hopefully can work to find a solution.

---

