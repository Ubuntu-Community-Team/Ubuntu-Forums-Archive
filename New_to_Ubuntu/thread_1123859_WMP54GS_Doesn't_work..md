---
title: "WMP54GS Doesn't work."
date: 2009-04-12
forum: New to Ubuntu
---

### Post by Zummy on 2009-04-12
I'm back and I brought my problems with me again! Anyway, long story short...

I have a linksys WMP54GS wireless card I've been able to port my drivers over, and now this happens.

Under System->Administration->Windows Wireless Drivers they appear installed and "hardware present=yes". Good.

Under System->Administration->Hardware Drivers I only see drivers for my NVidia card.   I know my linksys drivers are restricted, but under the list I can't find them to activate/ unrestrict them.

Any help?  Also post commands for me to give you info if you need it. I'm on the newest stable version of Ubuntu.

---

### Post by cariboo on 2009-04-12
What do you mean by 

> I've been able to port my drivers over

Are you using ndiswrapper to run the windows driver?

If you are, you won't see anything in restricted drivers.

Jim

---

### Post by Zummy on 2009-04-12
That's exactly it! I used NDIS Wrapper.  Sorry for the lousy explaining.

But yea, NDIS shows them as installed and hard present, but they aren't working and they aren't showing up in the hardware drivers.

---

