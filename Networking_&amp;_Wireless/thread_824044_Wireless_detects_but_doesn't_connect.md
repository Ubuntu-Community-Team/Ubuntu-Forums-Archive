---
title: "Wireless detects but doesn't connect"
date: 2008-06-09
forum: Networking &amp; Wireless
---

### Post by Yog_hurts on 2008-06-09
My internet reciever can see all of the local internet connections but for some reason i can't seem to get it to connect.  it spends ages trying and then fails.  My 2nd pc worked perfectly after installation,
can anyone tell me why my 1st pc isn't connecting to the internet?

---

### Post by issih on 2008-06-09
Whether wireless works or not is very variable, it depends on the hardware. Some hardware works perfectly out of the box, and some doesn't. It depends what wireless card your machines use.

Thats the why out of the way, onto trying to be helpful..Just to make sre I have the situation right, ubuntu sees the hardware, and in the network manager applet you are offered a list of detected networks to connect to.

You then select your network from the list, but it fails to connect?

If that is right then first try disabling encryption on the wireless network you are connecting to (just to check if the driver ubuntu is using will function at all), if that works then let us know what kind of encyption you are using....I'm going to guess wpa, and I'm going to guess you will probably need to install wpa-supplicant, but first of all I'd test the connection with encryption turned off

---

### Post by smartsmokey on 2008-06-09
is there a physical switch on the exterior that turns wifi on or off? That slowed me for a day or so. If you're detecting it's working...
Did you try google or synaptic?

---

