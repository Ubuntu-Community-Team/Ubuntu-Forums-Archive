---
title: "D-Link G510 REV. A problems"
date: 2006-10-19
forum: Networking &amp; Wireless
---

### Post by odbod on 2006-10-19
Dwl-G510 Rev. A
Ubuntu 6.06 (LTS??)

I have tested each driver, 98, me, 2k, xp(wouldn't work).

The drivers that worked (first three) showed that the hardware was present and the driver was present. Here is the problem. When I say modprobe ndiswrapper, it sits.. Nothing happens. Just a blinking cursor. If I do modprobe mrv8k , it does what it's supposed to do.. And I have done this:

modprobe mrv8k
modprobe ndiswrapper

And Ndiswrapper goes through perfectly, but wlan0 doesn't appear.
I have no possible internet connection, I am on windows partition at the moment using my wireless perfectly fine. I have no cord's, so I can not do anything.. I installed the ndiswrapper-utils off the CD, but is that enough? Is it causing this problem?

Any help would be apreciated.

---

