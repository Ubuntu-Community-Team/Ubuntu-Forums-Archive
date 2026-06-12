---
title: "BCM43xx Problems (edgy 64, 4311 card)"
date: 2007-01-16
forum: Networking &amp; Wireless
---

### Post by Prometheum on 2007-01-16
I am a recent Ubuntu convert. I dual booted on my desktop and have since installed edgy 64 on my new laptop and never looked back. However, I'm having problems with my wireless card, as I have one of the unholy chipsets from corporations that apparently don't like releasing things. As such, I have been wrestling with my wireless card (a bcm4311) for the past few weeks. I am working fine on ndiswrapper, but unfortunately I can't access monitor mode, which I need for airodump. I have set up bcm43xx to the point where I can see in network manager all the networks I am in, but I can't connect to anything using a GUI, and when I connect with dhclient or ifup, I get a DHCP lease and promptly can't do anything. I can, however, use kismet and airodump. 

I'm at a loss here, being a relative noob. Any help I can get would be appreciated. This may be my error, not a bug in the driver/card/etc., and I'll gladly provide any other information needed.

---

### Post by discord on 2007-01-17
search for my bug in launchpad.net by my name discord. I explain how to get network manager working with ndiswrapper and the 4311. basically you cannot use the ubuntu package.

---

