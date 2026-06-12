---
title: "which wifi option is best"
date: 2010-01-22
forum: New to Ubuntu
---

### Post by nnjond on 2010-01-22
Hi,

It's no longer convenient for me to use a cable for my Internet connection, but i don't know the pros and cons of my options ; an internal card or a dongle?

Does any one have any opinions?

Thanks

---

### Post by ibuclaw on 2010-01-22
I prefer internal over external.

Atheros devices are guaranteed to work, but they are rather poor chipsets by design (don't get strong signal from them).

As for external, it can be hit and miss - and though I've been around since external wireless devices were a 'No no' - am always surprised at what works nowadays.

If you find a device, try looking it up here: [http://linux-wless.passys.nl/](http://linux-wless.passys.nl/)

That site is an attempt to keep a repository of device compatibility, but being as there are so many devices, and support for them constantly changes, some information may not be up to date.

Regards
Iain

---

### Post by JiuJitsu500 on 2010-01-22
Personally I'd say an internal card, less intrusive and harder to lose (I travel a LOT). Though there are dongle types that are so small after plugging them in they only stick out maybe a few millimeters. But, those Verizon, Sprint, AT&T, etc big type are generally more powerful (and battery consuming) and more reliable in more rural areas bacause they connect to G3 networks and anywhere cell phones can be used (if you're on their network, obviously normal fees).

But anywhere there's Wifi for free you're going to get a connection with any card capable of reading and connecting to a wifi network (including one at home, like I use). There are an endless supply of god cards, internal and external around.... But I choose internal because wires are so..... 20th Century :D And I can't lose it on accident.

---

### Post by myth1914 on 2010-01-22
I've had fairly good success with Intel's b/g cards; although, the a/b/g seems to drop and reconnect fairly consistently.  

Either way, I would go with an internal.

---

### Post by ubunterooster on 2010-01-22
I prefer everything to be internal: everthing external uses up USB ports :P

---

### Post by nnjond on 2010-01-22
Thanks for your advice, but my interest,  is specifically in a desktop function.

---

### Post by warfacegod on 2010-01-22
> **tinivole said:**
> I prefer internal over external.

Atheros devices are guaranteed to work, but they are rather poor chipsets by design (don't get strong signal from them).

As for external, it can be hit and miss - and though I've been around since external wireless devices were a 'No no' - am always surprised at what works nowadays.

If you find a device, try looking it up here: [http://linux-wless.passys.nl/](http://linux-wless.passys.nl/)

That site is an attempt to keep a repository of device compatibility, but being as there are so many devices, and support for them constantly changes, some information may not be up to date.

Regards
Iain

I'm using an internal with the Atheros AR5211 a/b and have no signal strength problems. My router is about 75 ft. away and down stairs. The signal has to go through a partial brick wall and my laptop sits right next to a 27" solid state television that puts out a fair amount of electromagnetic interference. In spite of all that, my signal strength is rarely under 80%. I can download at around 400 - 500 K and torrent downloads will even occasionally hit 750 K. a/b is older tech so you may want to consider a card that will utilize a/b/g/n.

---

### Post by warfacegod on 2010-01-22
> **nnjond said:**
> Thanks for your advice, but my interest,  is specifically in a desktop function.

My wife's computer has an internal Belkin card. It gets crap signal strength but it always connects (eventually).

---

### Post by myth1914 on 2010-01-22
The intersil cards have also been stable for me, but not the best signal or connection quality.

---

### Post by doas777 on 2010-01-22
just to clarify, you mean wired vs wireless, rather than cable vs dsl vs T3 vs pots right?

for wifi, and internal is best, but just make sure it is compatible first. if it is on the madwifi compatibility list, then you should be able to get it going without too much trouble. 
[http://madwifi-project.org/wiki/Compatibility](http://madwifi-project.org/wiki/Compatibility)

---

### Post by sandyd on 2010-01-22
if you get a broadcom  BCM4311-, BCM4312-, BCM4321-, and BCM4322-based chipset, their almost 100%guaranteed to work through Broadcom STA, which are the drivers that broadcom provides. Ive never had a problem using the STA drivers with the above chipsets. ([bcmwl-kernel-source]("apt://bcmwl-kernel-source,bcmwl-modaliases"))

---

