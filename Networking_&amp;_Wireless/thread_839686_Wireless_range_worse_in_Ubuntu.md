---
title: "Wireless range worse in Ubuntu"
date: 2008-06-24
forum: Networking &amp; Wireless
---

### Post by PureSamuel on 2008-06-24
Hi.
I have a Dell Inspiron 1501 with a Dell Wireless 1490 Dual Band WLAN Mini-Card built-in wireless card, which is working almost perfectly.
The problem is that when I'm in my study, which is quite far from my router, I get a connection if I'm using XP but can't when using Ubuntu.
Any ideas?
Sam

---

### Post by spd106 on 2008-06-24
Some people have reported that ndiswrapper with the Windows driver gives them better range and speed. So that might be worth a look.

[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

---

### Post by overcaffein8d on 2008-06-25
> **spd106 said:**
> Some people have reported that ndiswrapper with the Windows driver gives them better range and speed. So that might be worth a look.

[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

i just switched to ndiswrapper using Broadcom 4311 from the b43 driver, because i thought it would....well... have better range. Turns out, it's worse range (at least right now) and i don't know how to get it back.

but i still think it's working better; ndiswrapper seems still to be superior.

---

### Post by PureSamuel on 2008-06-25
I'll give it a shot.
I can't understand why drivers should affect range..
Thanks.

I've just been looking through my hardware to find the right drivers and just noticed I have two network adapters:
1) Broadcom 440x 10/100 integrated controller
2) Dell Wireless 1490 Dual Band WLAN Mini-Card

Are they both wireless cards?

---

### Post by spd106 on 2008-06-26
Drivers are very important due to things such as the data rate selection algorithms they implement. A lot of the hardware controls aren't available to the open source driver because the developers have to reverse engineer them. Things like hardware cryptography can't always be enabled, which means it's done in software on your CPU instead. Perhaps if they had manufacturer support...

The Broadcom 440x series nic is for wired ethernet. Just to confuse matters the Dell wifi card actually has a Broadcom 43xx chip.

---

