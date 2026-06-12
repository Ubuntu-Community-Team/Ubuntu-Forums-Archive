---
title: "[SOLVED] serial monkey rt2570 driver in 8.04??"
date: 2008-05-12
forum: Networking &amp; Wireless
---

### Post by ncumming on 2008-05-12
I've been through all sorts of problems with my D-Link DWL-G122 B1 usb wireless adapter.  I originally was using ndiswrapper which worked ok but not great in 7.04.  In 7.10, I was able to use the serial monkey drivers thanks to the advice in this post: [http://ubuntuforums.org/showthread.php?p=4347558#post4347558](http://ubuntuforums.org/showthread.php?p=4347558#post4347558)

However, now that i've installed 8.04 (had to do clean install after upgrade failed) the instructions in that tutorial don't seem to work.  When I try to compile the driver, I get the error:

make *** /lib/modules/2.6.25-16-rt/build: No such file or directory.  Stop.
rt2570.ko failed to build!
make: *** [module] Error 1

Are the directions in the tutorial no good anymore?  Do i need to go back to using ndiswrapper?

---

### Post by octoberdan on 2009-02-25
For the benefit of others, could you please describe how you solved the issue?

---

### Post by ncumming on 2009-03-01
let's see...its been quite a while, but i'm pretty sure the problem was being caused by the fact that i was running the ubuntu studio flavor of 8.04, and specifically the real-time kernel.  I can't remember, at the time, if i was able to get the drivers working simply by booting to the standard kernel through GRUB or if i had to completely wipe the system, install the standard load of 8.04, and then just install the studio packages that i wanted individually through synaptic.  Since then, though, I upgraded to 8.10, and the wireless chipset seems to be supported naitively now.

---

