---
title: "Problem installing Belkin F5D8010 (wireless pre-n)"
date: 2008-07-19
forum: Networking &amp; Wireless
---

### Post by TehJumpingJawa on 2008-07-19
I've been following the installation guide for this device:
[https://help.ubuntu.com/community/WifiDocs/Device/Belkin_F5D8010](https://help.ubuntu.com/community/WifiDocs/Device/Belkin_F5D8010)

Everything works perfectly as described up until step 7(activating the driver). When I enter "sudo modprobe ndiswrapper" the machine freezes. (kernel doesn't appear to crash though)

This is using Hardy Heron (8.04), on one of these crappy pcs: [http://global.shuttle.com/product_detail.jsp?PI=471](http://global.shuttle.com/product_detail.jsp?PI=471)
(which incidentally was an absolute nightmare to install! I had to resort to a cli only install from the alternative installer, and apt-get everything else.)

I'm confident the hardware is not at fault, as i've had it all working through XP up until recently. Though I wonder if the underlying problems I encountered during Ubuntu installation could be manifesting themselves again...

Any suggestions on the next course of action?
Incidentally, i'm a linux noobie, so please be patient :)

Cheers very much,

:edit:

To clarify, it's actually the F5D8000. (which is a F5D8010 mounted inside a Rico CardBus bridge)
hmm...... is this the cause of my problems!

---

### Post by TehJumpingJawa on 2008-07-19
[s]Hmm, just noticed this - not sure if it correct behaviour or not?

# sudo modprobe -r ndiswrapper
# modprobe -l ndis*
*/lib/modules/2.6.24-19-generic/misc/ndiswrapper.ko*

Why is the ndiswrapper still listed? shouldn't the '-r' have removed it?
Could this be resulting in the wrong version of ndiswrapper being used?[/s]

:edit:

nvm, was confusing /lib/modules with /proc/modules.

---

### Post by TehJumpingJawa on 2008-07-20
Still no idea on this :(

Please help!

---

