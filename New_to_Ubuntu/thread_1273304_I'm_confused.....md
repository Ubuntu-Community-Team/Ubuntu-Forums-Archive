---
title: "I'm confused...."
date: 2009-09-23
forum: New to Ubuntu
---

### Post by humphreybc on 2009-09-23
Okay so I have the ATI Catalyst 9.4 drivers installed from the ATI website... installed using the .run sh file.

But I do not have the Catalyst Control Center...

In Synaptic, I see that these two packages:

fglrx-amdcccle
xorg-driver-fglrx

Are not installed, so I mark fglrx-amdcccle to be installed and it says that I need to install xorg-driver-fglrx as well... The description of this says it's the 3D proprietary driver from ATI.... so is this an older one available in the repos and if I install it won't it conflict with the .run file installed one?!?!

Do I need these packages for the driver? Do I have these packages in conjunction with the driver, or instead of? Or not at all?!

Then there's the "Hardware Drivers" driver which says that it's not installed and that I should activate it... and then also in synaptic there's the open source radeon driver which is installed.... so there are FOUR different ways of getting the ATI drivers, three of which are fglrx.... and only ONE of those three you actually know what Catalyst version you're installing.... the Hardware Drivers one, and the xorg-driver-fglrx drivers don't tell you what version of Catalyst it is... so therefore you don't know whether to use these ones provided by Ubuntu through the repos, or the ones off the ATI site, or the open source driver, or the one suggested by Hardware Drivers..... could it get any more confusing?!?!

I'm confused... someone please clarify!!

---

### Post by etnlIcarus on 2009-09-23
Unless you've got a particular reason to use the latest drivers, it's best to stick with the version in the repos. If you mistakenly installed the latest drivers from amd.com, uninstall them, then use synaptic to install the repo versions.

If you want to keep the latest drivers, check to see if CCC is available as a separate download from amd.com. IIRC, it should all be together. Try opening a terminal and running ccc.

---

