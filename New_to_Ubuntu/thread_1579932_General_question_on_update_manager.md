---
title: "General question on update manager"
date: 2010-09-22
forum: New to Ubuntu
---

### Post by JamButty on 2010-09-22
I am confused about the constant updates I am bugged to install. Most of them seem to be for programs I am not using and do not want or are strictly for developers. Declining to install does not work as the update manager will keep offering the updates until they are accepted.
Most of Ubuntu seems very well thought out, but this part just seems MS stupid.
I thought there were dependency lists which update manager could check to determine which updates were pertinent to each user, but I seem to get everything offered to me.

Is there a way to decline install without being re-prompted on every boot? Or to get it to stop offering me irrelevant updates altogether?

---

### Post by mcduck on 2010-09-22
Uninstall the programs.

The package management will update everything you have installed. So if it's offering an update for a package, its something that you have installed on your system. Be it a program that you use, or  some system component. So there is no such thing as "irrelevant update".

(by the way, it's very unlikely that your updates would offer you anything intended for developers unless you have installed some developer software yourself. It's more likely that they are system components, or dependencies of some program you are actually using).

---

### Post by JamButty on 2010-09-22
As an example, currently on tap is
dpkg-dev
Debian package development tools
description:
This package provides the development tools (including dpkg-source) required to unpack, build and upload Debian source packages.
Most Debian source packages will require additional tools to build; for example, most packages need make and the C compiler gcc.
------------
It might be nice to be able to do this at some point, but I would have no idea how to deal with compiling source code and have not done it on this machine.

---

### Post by thatguruguy on 2010-09-22
That's the program used to install packages onto your system.  In other words, if you download any program through the Ubuntu Software Center, that's the program that will actually configure and install it.

You want to keep it, and you want to ensure that it works properly.

---

### Post by coffeecat on 2010-09-22
dpkg-dev is not included in a default install. So - either you installed it or it was a dependency of something you installed. 

No - this is not "stupid". :) This is simply the system trying to keep what you installed up-to-date.

---

### Post by coffeecat on 2010-09-22
> **thatguruguy said:**
> That's the program used to install packages onto your system.

I think you're thinking of dpkg which is, indeed, essential. The OP is right - dpkg-dev is for developers. However, the OP must have installed it, either directly or indirectly.

---

### Post by philinux on 2010-09-22
> **coffeecat said:**
> I think you're thinking of dpkg which is, indeed, essential. The OP is right - dpkg-dev is for developers. However, the OP must have installed it, either directly or indirectly.

+1 apps do not instal themselves ;)

---

### Post by JamButty on 2010-09-22
I bow to the surfeit of beans and the sword of Elendil. I never installed developer related apps (outside of update) that I am aware of - no reason to. I did download two small packages that turned out to have only source code in them. I could do nothing with them and tossed them. 

I was just a bit touchy as two "linux header" updates in a row knocked out my system, apparently due to a grub/grub2 conflict somewhere in the install coding. The most recent kernel updates installed without incident. I'll be a good boy now and eat what the penguin feeds me. Thanks!

---

