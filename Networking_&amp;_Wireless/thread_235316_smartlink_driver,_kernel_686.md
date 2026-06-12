---
title: "smartlink driver, kernel 686"
date: 2006-08-12
forum: Networking &amp; Wireless
---

### Post by exclesodia on 2006-08-12
hi all, first, sorry for my poor english, i'm not a native english speaker

well, last night i've installed ubuntu 6.06 and upgrade my kernel to 686, it's 2.6.15-23-686, everything fine except my smartlink internal modem.

but, in default kernel, the 386, it's work perfect and i'm consider it's faster than in my SUSE 10.0 system.
in 386 i'm use  slamr-2.6.15-23-386.tgz from [http://phep2.technion.ac.il/linmodems/packages/smartlink/Ubuntu/](http://phep2.technion.ac.il/linmodems/packages/smartlink/Ubuntu/) which contain an setup script that automaticaly install and config the modem.

but unfortunately, it's doesn't work in my 686 kernel, when installing it i got messages like "error when inserting module" or  "invalid module"

is there any solution for my problem, i've looked on this forum and google with no result.
 
thanks.

---

### Post by az on 2006-08-12
> **exclesodia said:**
> hi all, first, sorry for my poor english, i'm not a native english speaker

well, last night i've installed ubuntu 6.06 and upgrade my kernel to 686, it's 2.6.15-23-686, everything fine except my smartlink internal modem.

but, in default kernel, the 386, it's work perfect and i'm consider it's faster than in my SUSE 10.0 system.
in 386 i'm use  slamr-2.6.15-23-386.tgz from [http://phep2.technion.ac.il/linmodems/packages/smartlink/Ubuntu/](http://phep2.technion.ac.il/linmodems/packages/smartlink/Ubuntu/) which contain an setup script that automaticaly install and config the modem.

but unfortunately, it's doesn't work in my 686 kernel, when installing it i got messages like "error when inserting module" or  "invalid module"

is there any solution for my problem, i've looked on this forum and google with no result.
 
thanks.

Does it compile the module for you?  Do you have linux-headers-686?

---

### Post by mpvano on 2006-08-13
I believe your problem is part of a deliberate (but badly documented) decision on the part of the ubuntu team. I have the same problem with one of my older machines (but not with my T30).

The problem is that some of the older drivers supported by the smartlink system available in source form (like the very common Lucent softmodem) cannot be run without crashing in multiprocessor systems. This is a common problem, but cannot be easily fixed withut rewriting some of the basic ways the driver works. Since these older drivers no longer have anyone looking after them (especially if they use uncompilable "binary" modules), it may be a while before there's a solution to running them under MP kernels.

Now for the dapper change that's causing our problem: The "686" kernel variants are ALL compiled to support multiprocessor configurations.

There's a long explanation somewhere in the developer wiki about why this improves the performance for single processor machines as well, and I generally agree with it.
 
Unfortunately, it breaks a few older drivers and so they've been deliberately kept out of the 686 module set.

There is only one way to get it working again - you need to build your own kernel. There's a way to do this correctly, and to configure it with all the ubuntu special options and settings, but it's WAAAAY too much trouble  - especially keeping it updated. This is FAR more complicated than just building a standard kernel because the Ubuntu kernels (like those of most distributions) have a lot of customization patches to add features that the rest of the distribution uses.

Personally, since I hardly ever use modems any more, I decided just to choose the 386 kernel from the boot menu those rare times when I need to use the modem on that machine (something I've never done since coffee shop wifi became nearly universal here).

The ideal solution would be if the team would offer another kernel in the repositories that did not have the MP features enabled, but that really greatly increases their testing workload, so I'm guessing it's not going to happen anytime soon.

If you really need the modem, or can't find a more up to date source file for it that supports MP (which of course you'll have to build from source - another ongoing pain in the neck), I'd just find a hardware based modem. Surprisingly enough they DO exist, they're just confusing to buy - it can be quite hard to tell if they're the right kind or not....

hope this saves you some frustration (I wasted at least a day trying to figure this out myself until I stumbled across the answer).

Mario

---

