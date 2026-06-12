---
title: "Clock changes after wireless connection"
date: 2009-10-10
forum: New to Ubuntu
---

### Post by donescamillo on 2009-10-10
Hi,

I installed Ubuntu 9.04 on my notebook. After I have rebooted the clock stays the same as it was before rebooting until the notebook gets connected to my modem (Netcomm6plus) via wireless. Once it gets connected it changes the clock. It is even stranger that the modem has the right clock. I have Ubuntu installed to a desktop connected wired to the same modem and there is no clock problem.
How can I stop Ubuntu from changing the clock?

regards,
donescamillo

---

### Post by coffeeaddict22 on 2009-10-11
Hi,
Not 100% sure what the exact problem is.  Your post makes it clear the clock is updating once the PC is booted up, but I'm not sure what time it's ?resetting to or whether it's staying at the previous shutdown time when you power down.
  The PC has a small battery on the motherboard; a large part of it's job is keeping the motherboard's clock going.  They usually fail at I think 5-10 years, depending on the system. The system clock going walkabout is a fair indication this is happening, and this may be your problem.

---

### Post by 3rdalbum on 2009-10-11
Ubuntu can sync to Network Time Protocol servers around the place, which keep a track of the exact correct time. It looks like that's what your laptop is doing.

I can't find the setting for turning NTP on and off, but maybe some Google skills will help you.

As your desktop computer is wired to the modem, then the time gets synchronised during boot, and therefore you don't see it get changed.

---

