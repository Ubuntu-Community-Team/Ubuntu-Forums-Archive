---
title: "No soundscard..."
date: 2009-08-28
forum: New to Ubuntu
---

### Post by lover_of_sc on 2009-08-28
Hi guys, problems again - this time caused by no one else then myself. I tried to get my microphone to work properly in skype and found a tut orial in how to do so. One of the tips was to reinstall the alsa mixer which i did.
So now my soundcard isn't available anymore??

anders@anders-laptop:~$ aplay -l
aplay: device_list:217: no soundcards found...

Can someone plz help me again... :-)

---

### Post by sydbat on 2009-08-28
> **lover_of_sc said:**
> Hi guys, problems again - this time caused by no one else then myself. I tried to get my microphone to work properly in skype and found a tut orial in how to do so. One of the tips was to reinstall the alsa mixer which i did.
So now my soundcard isn't available anymore??

anders@anders-laptop:~$ aplay -l
aplay: device_list:217: no soundcards found...

Can someone plz help me again... :-)Which version of Ubuntu are you using?

With Hardy (8.04), go to System > Preferences > Sound and make sure that everything in the Device tab is set to Alsa.

Then, you Right click on your Volume control (the little speaker, usually in the upper right corner of your desktop) and choose "Open Volume Control". From there you have to enable the correct volume levels (like Mic) and set them accordingly. Also, make sure what you want to use is not muted.

---

### Post by lover_of_sc on 2009-08-28
I am using 9.04 32bit version on my sony vaio w seriwes netbook. I think I may have lost just the alsa driver, i found the sound card by running command: 

anders@anders-laptop:~$ find /lib/modules/`uname -r` | grep snd
/lib/modules/2.6.28-11-generic/kernel/sound/oss/msnd_pinnacle.ko
/lib/modules/2.6.28-11-generic/kernel/sound/oss/msnd_classic.ko
/lib/modules/2.6.28-11-generic/kernel/sound/oss/msnd.ko

and

anders@anders-laptop:~$ lspci -v | less
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
        Subsystem: Sony Corporation Device 9064
        Flags: bus master, fast devsel, latency 0, IRQ 7
        Memory at f0440000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>
        Kernel modules: snd-hda-intel


I wonder if its just the alsa driver I need to install? I can not select an alsa mixer under the sound settings...

---

### Post by lover_of_sc on 2009-08-28
Maybe this information will help...


anders@anders-laptop:~$ cat /proc/asound/card0/codec#* | grep Codec
cat: /proc/asound/card0/codec#*: No such file or directory
anders@anders-laptop:~$ lspci -nv 
00:00.0 0600: 8086:27ac (rev 03)
	Subsystem: 104d:9064
	Flags: bus master, fast devsel, latency 0
	Capabilities: <access denied>
	Kernel driver in use: agpgart-intel
	Kernel modules: intel-agp

00:02.0 0300: 8086:27ae (rev 03)
	Subsystem: 104d:9064
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at f0000000 (32-bit, non-prefetchable) [size=512K]
	I/O ports at 1800 [size=8]
	Memory at d0000000 (32-bit, prefetchable) [size=256M]
	Memory at f0400000 (32-bit, non-prefetchable) [size=256K]
	Capabilities: <access denied>
	Kernel modules: intelfb

00:02.1 0380: 8086:27a6 (rev 03)
	Subsystem: 104d:9064
	Flags: bus master, fast devsel, latency 0
	Memory at f0080000 (32-bit, non-prefetchable) [size=512K]
	Capabilities: <access denied>

00:1b.0 0403: 8086:27d8 (rev 02)
	Subsystem: 104d:9064
	Flags: bus master, fast devsel, latency 0, IRQ 7
	Memory at f0440000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel modules: snd-hda-intel

00:1c.0 0604: 8086:27d0 (rev 02)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
	I/O behind bridge: 00002000-00002fff
	Memory behind bridge: f0100000-f01fffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:1c.1 0604: 8086:27d2 (rev 02)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
	Memory behind bridge: f0200000-f02fffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:1d.0 0c03: 8086:27c8 (rev 02)
	Subsystem: 104d:9064
	Flags: bus master, medium devsel, latency 0, IRQ 23
	I/O ports at 1820 [size=32]
	Kernel driver in use: uhci_hcd

00:1d.1 0c03: 8086:27c9 (rev 02)
	Subsystem: 104d:9064
	Flags: bus master, medium devsel, latency 0, IRQ 19
	I/O ports at 1840 [size=32]
	Kernel driver in use: uhci_hcd

00:1d.2 0c03: 8086:27ca (rev 02)
	Subsystem: 104d:9064
	Flags: bus master, medium devsel, latency 0, IRQ 18
	I/O ports at 1860 [size=32]
	Kernel driver in use: uhci_hcd

00:1d.3 0c03: 8086:27cb (rev 02)
	Subsystem: 104d:9064
	Flags: bus master, medium devsel, latency 0, IRQ 16
	I/O ports at 1880 [size=32]
	Kernel driver in use: uhci_hcd

00:1d.7 0c03: 8086:27cc (rev 02) (prog-if 20)
	Subsystem: 104d:9064
	Flags: bus master, medium devsel, latency 0, IRQ 23
	Memory at f0644000 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd

00:1e.0 0604: 8086:2448 (rev e2) (prog-if 01)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=0a, subordinate=0a, sec-latency=32
	Memory behind bridge: f0300000-f03fffff
	Capabilities: <access denied>

00:1f.0 0601: 8086:27b9 (rev 02)
	Subsystem: 104d:9064
	Flags: bus master, medium devsel, latency 0
	Capabilities: <access denied>
	Kernel modules: iTCO_wdt, intel-rng

00:1f.2 0101: 8086:27c4 (rev 02) (prog-if 80 [Master])
	Subsystem: 104d:9064
	Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 19
	I/O ports at 01f0 [size=8]
	I/O ports at 03f4 [size=1]
	I/O ports at 0170 [size=8]
	I/O ports at 0374 [size=1]
	I/O ports at 18b0 [size=16]
	Capabilities: <access denied>
	Kernel driver in use: ata_piix

00:1f.3 0c05: 8086:27da (rev 02)
	Subsystem: 104d:9064
	Flags: medium devsel, IRQ 10
	I/O ports at 18c0 [size=32]
	Kernel modules: i2c-i801

02:00.0 0200: 1969:1062 (rev c0)
	Subsystem: 104d:9064
	Flags: bus master, fast devsel, latency 0, IRQ 11
	Memory at f0100000 (64-bit, non-prefetchable) [size=256K]
	I/O ports at 2000 [size=128]
	Capabilities: <access denied>

03:00.0 0280: 168c:002b (rev 01)
	Subsystem: 105b:e017
	Flags: bus master, fast devsel, latency 0, IRQ 17
	Memory at f0200000 (64-bit, non-prefetchable) [size=64K]
	Capabilities: <access denied>
	Kernel driver in use: ath9k
	Kernel modules: ath9k

0a:09.0 0805: 1180:0822 (rev 22)
	Subsystem: 104d:9064
	Flags: bus master, medium devsel, latency 32, IRQ 16
	Memory at f0300000 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>
	Kernel driver in use: sdhci-pci
	Kernel modules: sdhci-pci

0a:09.1 0880: 1180:0592 (rev 12)
	Subsystem: 104d:9064
	Flags: bus master, medium devsel, latency 32
	Memory at f0300400 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>

---

### Post by lover_of_sc on 2009-08-28
Actually managed to get it sorted via [http://webupd8.blogspot.com/2009/08/how-to-upgrade-to-alsa-1020-on-ubuntu.html](http://webupd8.blogspot.com/2009/08/how-to-upgrade-to-alsa-1020-on-ubuntu.html).

Fantastic easy to use manual for reinstalling the ALSA drivers.

---

