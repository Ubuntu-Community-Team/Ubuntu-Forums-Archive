---
title: "Intrepid won't boot"
date: 2009-03-11
forum: New to Ubuntu
---

### Post by dimitriv on 2009-03-11
I wanted to test the desktop & CD/DVD would work on it's side which the vendor said would be fine. I placed the machine on it's side and momentarily spun up the CD drive which contained 64bit Ubuntu. As it begun to load (so proving it could work happily on it's side) I powered the machine off.

Now when I attempt to boot I see the following message
_
Boot from (hd0,0) ext 3    [then a long serial number]

[   0.004000] Aperture beyond 4GB. Ignoring.
[   0.004000] Your BIOS doesn't leave a aperture memory hole
[   0.004000] Please enable the IOMMU option in the BIOS setup
[   0.004000] This costs you 64MB of RAM
_

the machine then automatically reboots and cycle through the same process repeatedly.

I've not touched the BIOS. Did the boot CD screw something?

I welcome any suggestions

Thank you

---

### Post by samborambo on 2009-03-11
Check that your RAM DIMMs are seated properly. You may have caused a hardware fault.

Also check your bios settings regarding memory aperature. Some older BIOSs may not be 64-bit OS aware and reoganise the memory map for >3GB.

Flash the BIOS with the latest firmware.

Provide more information about your hardware and BIOS when posting this sort of thing in the future.

Hope this helps.

---

### Post by dimitriv on 2009-03-11
abracadabra, after a little fiddle with components including reseating DIMMS (which looked ok before), she's up and running. the previous message still shows but it boots through and loads ubuntu.phew.
thanks

---

