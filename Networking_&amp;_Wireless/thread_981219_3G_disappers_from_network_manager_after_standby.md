---
title: "3G disappers from network manager after standby"
date: 2008-11-13
forum: Networking &amp; Wireless
---

### Post by oliwel on 2008-11-13
Hi All,

I am running a X300 Thinkpad with buildin UMTS/3G modem.
The network manager detects the modem without hassle on a fresh start and lets me connect through the modem.
After resuming the system from standby, the networkmanager is empty, some wireless networks appear after some seconds but the 3G modem is not showing up again.
I can fire up umtsmon or connect from the command line with the modem without problems, so the modem seems not to be the problem.

Anbody here can confirm this issue or has an idea how to solve this?

TIA

Oliver

---

### Post by sgrandi on 2009-06-01
Hi, I've the same problem, with my 3g/HSDPA modem. I don't know how to solve the problem, but i could give some additional information, guess re useful.

In my computer I see in /dev directory the devices TTYUSB0 and TTYUSB1, after standby i don't see the devices.

If I disconnect and reconnect the modem the devices reappear.

I am trying to find a workaround.

Ciao,stefano

---

### Post by Cubus on 2009-07-23
I'm experiencing the same issue with my Thinkpad x200s.

Dis- and reconnecting doesnt make it better for me tho.

---

### Post by kaefert66014235 on 2009-10-17
I have a simmilar issue with my Asus Eee PC 1000H Go, which has an internal modem. The modem works fine after a fresh boot, but not after comming back from standby. Is there some way to turn off the internal modem, and turn it on again, without rebooting the whole notebook?

---

### Post by tula on 2009-11-21
I still get this problem on my karmic koala after several times of standby or hibernate, sometimes its disappear from network manager sometimes its not, but after restart it will be showup again.

Is there a clue for this problem ?

thankx

---

