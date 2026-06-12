---
title: "loosing wireless interface with custom kernel ..."
date: 2005-10-25
forum: Networking &amp; Wireless
---

### Post by berbs on 2005-10-25
I am trying to replace the standard kernel with my own. I have made several attempts and each time when using the new kernel, the wireless interface is disabled... It get fixed by booting with the standard kernel againl.

I started from the standard kernel configuration (make oldconfig) and only changed the cpu type from i386 to Pentium M and removed the check for the generic x86 code. Once I install the new kernel, the wireless interface is gone.

Any help would be greatly appreciated.

---

### Post by kingsidy on 2005-10-25
i ran into the same problem. i compile the latest stable kernel. everything works fine except the intel wireless card. could not get the darn thing to work. Might be something to do with restricted modules or something like that. Good luck. I you do get it to work, please post a howto if you can

---

### Post by berbs on 2005-10-25
Looking at dmesg, here is the problem

[4295568.513000] ipw2200: Detected Intel PRO/Wireless 2915ABG Network Connection[4295568.564000] ipw2200: ipw-2.3-boot.fw load failed: Reason -2
[4295568.564000] ipw2200: Unable to load firmware: 0xFFFFFFFE
[4295568.564000] ipw2200: failed to register network device
[4295568.564000] ACPI: PCI interrupt for device 0000:03:03.0 disabled
[4295568.564000] ipw2200: probe of 0000:03:03.0 failed with error -5

The firmware is located under /lib/hotplug/firmware

I tried to copy the entire content to /usr/lib/hotplug/firmware but without any result. I will continue to investigate, but if someone has a clue...

---

### Post by berbs on 2005-10-26
it occured to me that the firmware loading was using the kernel version. looking into firmware.agent (/etc/hotplug.d) confirmed. The service looks first for $FIRMWARE-$VERSION and defaults to $FIRMWARE if it can't find it. 

The quick and dirty solution is to copy the ipw-2.3-* to /usr/lib/hotplug/firmware and rename them to remove the -2.6.12-9.i386 that is appended to the default version. 

sudo rmmod ipw2200 
sudo modprobe ipw2200
check dmesg

...et voila

a

---

