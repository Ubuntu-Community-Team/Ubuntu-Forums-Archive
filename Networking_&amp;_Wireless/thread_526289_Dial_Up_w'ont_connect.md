---
title: "Dial Up w'ont connect"
date: 2007-08-15
forum: Networking &amp; Wireless
---

### Post by kiwimage on 2007-08-15
Dialing with wvdial or pon (or gnome-ppp) ends up requiring a reboot. 

I hear the modem dial and make the same sounds as under windows but where in windows it'd place the icon in the systray and start working Ubuntu gives a short message and states that its disabling irq #193 (possibly 163? one time)
at which point the the mouse cusor while still moving about can't click upon anything and the keyboard does nothing. I can do nothing more but hit the reset button.

---

### Post by ihristov on 2007-08-17
You apparently have hardware (IRQ) issues. You could try to boot with "noapic" kernel option.

Another test I would suggest is to try to use an external modem.

---

