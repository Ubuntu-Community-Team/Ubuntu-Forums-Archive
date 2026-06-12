---
title: "make usb cardbus reader u132 work"
date: 2006-08-29
forum: Networking &amp; Wireless
---

### Post by axel_orth on 2006-08-29
Hey, 
I recently installed ubuntu on my laptop [FSJ Amilo 1437G] and intend to use it as my primary operating system. Therefore it must be possible for my to connect to the internet and I think this gonna be difficult to accomplish because of the following circumstances:

- the notebook has only a express-card slot and no pcmcia slot but i use [under windows xp] a pcmcia umts card of the phone company vodafone – the cards name: novatel merlin u740

-to make it work i have to use an adapter [usb cardbus card adapter]: the u132 of elan systems – it can be join to the laptop via usb and is a kind of external pcmcia slot

-no linux drivers seem to be supported

To my surprise the u132 is listed in the “device manager” [in German: Gerätemanager] as usb device [see attachment]– I have no idea if i have gained something by that or what to do with it.
I am a totally newbie but eager to make it run.

So the question is if there is a chance that i can use the u132 under ubuntu. Has someone made it work before? Any clues? A how-to somewhere?

TIA
Axel

---

### Post by axel_orth on 2006-09-01
Hey,
the distributor i bough the U132 from gave me the link to its linux drivers:
[http://www.elandigitalsystems.com/support/ufaq/u132linux.php](http://www.elandigitalsystems.com/support/ufaq/u132linux.php)

I'll see what I can make with that ...


Cheers
Axel

---

### Post by $ark on 2006-09-05
Axel

I would be very interested to hear how you made out with this problem. I have a work laptop that only supports Express Port and as a security professional I require my wireless PCMCIA wireless cards to work for security audits. If you would be so kind a report back with a "works" or "does not work" with wireless cards that would be great.

Thanks
$ark

---

### Post by axel_orth on 2006-09-06
Hey,
as mentioned in the beginning of the thread, i am totally new to linux. So I do not know how much help I can provide. Nevertheless I will try to give as much information as possible:

- to use my pcmcia card with a loptop that just has an express card slot, i use the U132 by Elan Digitalsystems:
[http://www.elandigitalsystems.com/usb/u132.php](http://www.elandigitalsystems.com/usb/u132.php)
I do not know if this is the only existing hardware of its kind - perhaps there are other ones

- the linux driver that can be found at their website:
[http://www.elandigitalsystems.com/support/ufaq/u132linux.php](http://www.elandigitalsystems.com/support/ufaq/u132linux.php)

- in the readme file:
[http://www.ubuntuusers.de/paste/3358/](http://www.ubuntuusers.de/paste/3358/)
it is mentioned that the U132 will only work with pccards that
contain OHCI Host Controller [and a way to check that]

- I was able to install the 2 driver modules and it looks like ubuntu recognizes the U132. I guess that because the LCDs started to blink green after the installation and did nothing before

- I am not able to use my pccard, yet. It is an UMTS card I need to connect to the internet. I try to figure out what is wrong.

--> So I can not really say "what works and what does not".


Hope that helps at least a little bit.
Axel

---

