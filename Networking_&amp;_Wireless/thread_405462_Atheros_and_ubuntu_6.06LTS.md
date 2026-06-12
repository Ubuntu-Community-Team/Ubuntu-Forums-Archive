---
title: "Atheros and ubuntu 6.06LTS"
date: 2007-04-09
forum: Networking &amp; Wireless
---

### Post by dastardly on 2007-04-09
Well, Ive been reading that there are often problems with running Ubuntu and Atheros cards, and have been reading the solutions (such as ndiswrapper and madiwifi), but Im having major problems.

First, by default I have no internet at all. The only way that I am on the internet now is with a kubuntu live cd. Next, I have no windows partition so I cant easily just "copy the drivers" as most have been doing. Ive read a ton of things people have posted and have a cd with a (probably old) copy of madwifi. I have tried to set that up, but "make" is an unknown command >>

Any idea what I can do to get this working right? Or should I just install kubuntu and be done with it :p

---

### Post by stchman on 2007-04-10
> **dastardly said:**
> Well, Ive been reading that there are often problems with running Ubuntu and Atheros cards, and have been reading the solutions (such as ndiswrapper and madiwifi), but Im having major problems.

First, by default I have no internet at all. The only way that I am on the internet now is with a kubuntu live cd. Next, I have no windows partition so I cant easily just "copy the drivers" as most have been doing. Ive read a ton of things people have posted and have a cd with a (probably old) copy of madwifi. I have tried to set that up, but "make" is an unknown command >>

Any idea what I can do to get this working right? Or should I just install kubuntu and be done with it :p

You need to do two things:

1.  Install a kernel that is compatible with madwifi.  Go to synaptic and type Atheros.  Install a kernel that supports madwifi.  You will then reboot.

2.  I have a procedure to install madwifi drivers.  [http://www.stchman.com/ath_drv.html](http://www.stchman.com/ath_drv.html).  Reboot and your card will be sniffing for wireless networks.

This will install the madwifi drivers and network manager.

It worked like a charm on my laptop with an Atheros wireless card.

---

