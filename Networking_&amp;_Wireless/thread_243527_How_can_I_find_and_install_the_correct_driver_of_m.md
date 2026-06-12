---
title: "How can I find and install the correct driver of my wireless card?"
date: 2006-08-25
forum: Networking &amp; Wireless
---

### Post by Vinze on 2006-08-25
Hey, since the last Xorg crash I do not have internet. It does work with the LiveCD though. I have this program airmon-ng which places a card into monitor mode, when run it shows:
> Interface       Chipset         Driver

wlan0           Unknown              ndiswrapper (monitor mode not supported)


While when run via the LiveCD it says:
> Interface       Chipset         Driver

wlan0           TI              acx111 (monitor mode enabled)


Now I want don't know if the driver is totally removed, if it isn't, how can I make sure it is used again? And if it's not, how can I reinstall it? I've already found [this site](http://acx100.sourceforge.net/) but I have no idea how to install it.

Thanks in advance.

---

### Post by Titus A Duxass on 2006-08-25
Check that the driver is installed or not by doing

"ndiswrapper -l" from the CLI

---

### Post by Vinze on 2006-08-25
> **Titus A Duxass said:**
> Check that the driver is installed or not by doing

"ndiswrapper -l" from the CLI

Thanks, will try that. Will post the results after I've rebooted.

---

### Post by Vinze on 2006-08-26
Come to think of it, doesn't that just list the Windows drivers ndiswrapper uses? I want to know if I installed the native Linux drive and how I can use it instead of ndiswrapper.

---

### Post by gannic on 2006-08-26
> **Vinze said:**
> Come to think of it, doesn't that just list the Windows drivers ndiswrapper uses? I want to know if I installed the native Linux drive and how I can use it instead of ndiswrapper.

Dont know if it will be any help, but I used the following method for an ACX111 chipset (PCI)

[http://www.ubuntuforums.org/showthread.php?t=230128&highlight=safecom](http://www.ubuntuforums.org/showthread.php?t=230128&highlight=safecom)

---

### Post by Vinze on 2006-08-26
> **gannic said:**
> Dont know if it will be any help, but I used the following method for an ACX111 chipset (PCI)

[http://www.ubuntuforums.org/showthread.php?t=230128&highlight=safecom](http://www.ubuntuforums.org/showthread.php?t=230128&highlight=safecom)

That looks good, thanks, will try it after a reboot :D

---

### Post by Vinze on 2006-08-26
> **Vinze said:**
> That looks good, thanks, will try it after a reboot :D

OK, I tried it, but I have no folder /etc/modprobe.d/kernel_version/acx so I guess the driver is somehow uninstalled and I have no idea how to reinstall it...

---

### Post by Vinze on 2006-08-27
I've found this file /etc/var/log/syslog so I cut out the I think useful lines, surely someone will be able to help me now? Please?

> Aug 27 10:14:26 localhost kernel: [17179583.420000] acx: Loaded combined PCI/USB driver, firmware_ver=1.2.1.34
Aug 27 10:14:26 localhost kernel: [17179583.420000] acx: compiled to use 32bit I/O access. I/O timing issues might occur, such as non-working firmware upload. Report them
Aug 27 10:14:26 localhost kernel: [17179583.420000] ACPI: PCI Interrupt 0000:00:0b.0[A] -> GSI 19 (level, low) -> IRQ 177
Aug 27 10:14:26 localhost kernel: [17179583.420000] acx: found ACX100-based wireless network card at 0000:00:0b.0, irq:177, phymem1:0xDFFFF000, phymem2:0xDFFE0000, mem1:0xe08ba000, mem1_size:4096, mem2:0xe0980000, mem2_size:65536
(snip)
Aug 27 10:14:26 localhost kernel: [17179584.284000] acx: firmware image 'acx/1.2.1.34/tiacx100c11' was not provided. Check your hotplug scripts
Aug 27 10:14:26 localhost kernel: [17179584.288000] acx: firmware image 'acx/1.2.1.34/tiacx100' was not provided. Check your hotplug scripts
Aug 27 10:14:26 localhost kernel: [17179584.288000] acx: reset_dev() FAILED
Aug 27 10:14:26 localhost kernel: [17179584.288000] ACPI: PCI interrupt for device 0000:00:0b.0 disabled
Aug 27 10:14:26 localhost kernel: [17179584.304000] acx_pci: probe of 0000:00:0b.0 failed with error -5
Aug 27 10:14:26 localhost kernel: [17179584.304000] usbcore: registered new driver acx_usb
Aug 27 10:14:26 localhost kernel: [17179584.304000] ACPI: PCI Interrupt 0000:00:12.0[A] -> GSI 23 (level, low) -> IRQ 185
(snip)
Aug 27 10:14:26 localhost kernel: [17179585.720000] ndiswrapper version 1.8 loaded (preempt=yes,smp=no)
Aug 27 10:14:26 localhost kernel: [17179585.956000] ndiswrapper: driver tiacxln (U.S.Robotics,06/20/2002,1.2.2.27) loaded
Aug 27 10:14:26 localhost kernel: [17179585.976000] ACPI: PCI Interrupt 0000:00:0b.0[A] -> GSI 19 (level, low) -> IRQ 177
Aug 27 10:14:26 localhost kernel: [17179585.976000] ndiswrapper: using irq 177
Aug 27 10:14:26 localhost kernel: [17179586.596000] ndiswrapper (IoCreateUnprotectedSymbolicLink:744): --UNIMPLEMENTED--
Aug 27 10:14:26 localhost kernel: [17179587.604000] wlan0: vendor: 'U.S. Robotics 22Mbps Wireless Lan Adapter'
Aug 27 10:14:26 localhost kernel: [17179587.604000] wlan0: ndiswrapper ethernet device 00:c0:49:c9:f1:08 using driver tiacxln, 104C:8400:00FD:16EC.5.conf
Aug 27 10:14:26 localhost kernel: [17179587.604000] wlan0: encryption modes supported: none
(snip)
Aug 27 10:14:26 localhost kernel: [17179587.708000] ieee80211_crypt: registered algorithm 'NULL'
Aug 27 10:14:26 localhost kernel: [17179587.712000] ieee80211: 802.11 data/management/control stack, git-1.1.7
Aug 27 10:14:26 localhost kernel: [17179587.712000] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>

[http://paste.ubuntu-nl.org/21782](http://paste.ubuntu-nl.org/21782)

---

