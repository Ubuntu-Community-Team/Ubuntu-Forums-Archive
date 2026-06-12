---
title: "messages while loading. should i worry"
date: 2009-03-01
forum: New to Ubuntu
---

### Post by steve joe bob on 2009-03-01
i have a dual boot setup with windows and kubuntu 8.10 64 bit edition. when loading kubuntu it says "Starting up....   [0.004000] Aperture beyond 4gb. Ignoring.           PCI 0000:03:00.0:unsupported PM Cap Regs Version (7)" I'm not sure if i need to worry about that or not. Also, i used to use ubuntu 8.4 32 bit on my desktop and it seemed faster than this kubuntu install on my laptop which is considerably more powerful. my desktop had a p4 and 1.25 Gb's of DDR where as my laptop has a Dual Core with 3 GB's of DDR 2 and i was wondering if something is wrong or if this is just a slower distro. Looking forward to any feedback

---

### Post by t0p on 2009-03-01
I wouldn't worry about the messages.  I've found that all sorts of disconcerting messages can be generated during boot-up, but they can generally be ignored.  Of course, if you've got some kind of problem with your system then you should pay attention to them.  Otherwise, just watch the progress bar!

As for your ubuntu system being faster than your kubuntu:  I have found that ubuntu is faster than kubuntu, period.  No doubt some kubuntu enthusiasts will slap me down for saying that.  But that's my experience.

---

### Post by ibuclaw on 2009-03-01
Nothing to worry about the first message. It's just Linux checking that the aperture on your machine is valid, if not, it goes off to use it's own workaround to make it work for the hardware you have.

Aperture = a region of the physical address space that opens access to a particular device or memory unit.

In some benchmarks, 32bit applications has proven to be quicker than the 64bit ones due to lack of optimisation in the amd64 arch from software maintainers. But 64bit outshines on kernel tasks by a landslide, such as disk read/write speed :)

Regards
Iain

---

