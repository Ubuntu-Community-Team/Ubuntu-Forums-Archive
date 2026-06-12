---
title: "Terrible network detection on a rt2500 (yea, another rt problem)"
date: 2007-11-09
forum: Networking &amp; Wireless
---

### Post by sorbix on 2007-11-09
Hi all, I am having more problems with my rt2500.  Huge thanks to the ubuntu devs who somehow got my rt2500 to work without a hitch, except for one thing.  The range and strength of my wireless card is really, really bad.  I can often connect, and everything seems to work fine when I can, but occasionally I will be in a meeting with a whole group of people who have a connection and I don't.  Also, I dual boot, and Windows can connect just fine (signal will even have a high strength when the network manager says 0% in ubuntu).

I am not using ndis as far as I know.  my card is an onboard rt2500.  what other information do people need?  has this already been discussed?

---

### Post by wieman01 on 2007-11-09
All I can say is that you should try "ndiswrapper" which often does a better job. I have a rt2570 as well and after replacing the native driver, I am ok. Give it a go (see tutorial in my signature).

---

### Post by sorbix on 2007-11-09
well then maybe you can help me.  where can i find the driver files for the rt2500?  I haven't been able to find them, especially since my laptop has it onboard so I don't think it came with a driver CD for it.  i couldn't find them on the linksys website either.

---

### Post by wieman01 on 2007-11-10
That'll be a bit more difficult... What brand of computer have you got, what card is it and what's the manufacturer?

---

