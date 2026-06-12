---
title: "Freenx opens applications wrong comptuer!"
date: 2010-06-04
forum: New to Ubuntu
---

### Post by bpowell2005 on 2010-06-04
Hello,

I am running NXServer (free version from noMachine) on a laptop, and the NXClient on the desktop...(actually, running both client and server on both machines)

When I connect to the desktop from the laptop, everything works perfectly.

When I connect to the laptop from the desktop...when I open applications (office, internet) the application opens on the local laptop!

My goal is to remote into the laptop and do work while my wife uses the laptop as well...but it's no good if I can't use any applications because they open in my wife's face on the laptop.

Any ideas?

both machines are Ubuntu 10.04, current on updates.

Thanks!

---

### Post by pricetech on 2010-06-04
I'm not positive I understand what you're saying but here goes anyway:

There's a setting, in one of the configuration files, that turns that behaviour on or off.  I don't recall exactly how it's worded, but I specifically remember it being explained in the manuals from NoMachine.

What you want is to have a session separate from whoever is using the laptop at time, right ??

---

### Post by bpowell2005 on 2010-06-05
> **pricetech said:**
> I'm not positive I understand what you're saying but here goes anyway:

There's a setting, in one of the configuration files, that turns that behaviour on or off.  I don't recall exactly how it's worded, but I specifically remember it being explained in the manuals from NoMachine.

What you want is to have a session separate from whoever is using the laptop at time, right ??

Hi Pricetech, correct.

Ubuntu's default remote desktop simply connects a user from the client to the host's main desktop (0:) and that is useful for when I'm troubleshooting a problem for somebody, I can watch what they're doing, or I can take control and demonstrate what needs to be done.

However, I installed FreeNX as an alternative to VNCServer...What I'm looking for there is an entirely new session (1: for instance) where I can log into the host computer, and it's as if I'm sitting at the host computer, and I can work on it even while my wife is using the host computer.

By default, this has worked every other time I've installed freenx...but for some reason, when I put the Node and Server on my laptop...I connect from the desktop...and I get a completely different session (as I'd expect)...so I can move the mouse, and it doesn't move on the laptop screen...applications open on the laptop do not show up on the freenx desktop (indicating there are two different sessions in play..all good)..but, then when I try to open an Open Office document from the client...the Open Office document pops open on the host's (laptop's) desktop...completely unexpected to my wife who is doing her own thing on the laptop.

It's very strange.

I'm looking for those settings, but have not been able to find anything like that.

---

