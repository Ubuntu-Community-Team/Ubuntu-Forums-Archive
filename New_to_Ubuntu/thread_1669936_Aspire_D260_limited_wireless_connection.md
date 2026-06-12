---
title: "Aspire D260 limited wireless connection"
date: 2011-01-18
forum: New to Ubuntu
---

### Post by merizim on 2011-01-18
My daughter has an Acer Aspire D260 on which I recently installed 10.10 in a dual boot configuration with Windows XP. She has been complaining of a slow connection on wireless. When I checked the connection information it said that it was at 1Mbs. My own Dell 1564 connects at 54Mbs. Both use a Broadcom chipset and propietary drivers.
I have deleted and re-attached the connection with no effect.
The machine was installed with ubuntu desktop and then netbook edition with unity on top.
Has anybody else come across anything similar?

---

### Post by hansolo4949 on 2011-01-18
By Broadcomm chipset, you mean it's the wireless card, right? if it is, then you lucked out, my friend. Broadcomm wireless cards are notoriously hard to set up. I must have spent over 10 hours on one of my computers trying to get the broadcomm wireless on that one working. It sounds like it may be a problem with the driver. have you tried the wireless in XP yet? if so, was the wireless in windows faster than on linux? if so, then it is the driver. if not... your daughter may be stuck with a slow/possibly failing wireless card.

How old is the computer?

---

### Post by merizim on 2011-01-21
In XP the wireless connects at 65Mb, so it is the driver that seems at fault. Think it may be time to try ndiswrapper, never used it before so it should be fun learning!

---

