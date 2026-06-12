---
title: "Atmel at76c503/Belkin 5D6050 firmware loading problem"
date: 2005-04-18
forum: Networking &amp; Wireless
---

### Post by jleino on 2005-04-18
Hi All,

I upgraded warty to hoary recently and got some problems with my wireless
USB nic. The driver (or kernel?) does not seem to load the firmware correctly to the
device. Here's a snippet from my syslog after I have disconnected and connected the device (should erase the firmware):

```

Apr 18 17:57:22 localhost kernel: usb 1-1: new full speed USB device using uhci_hcd and address 8
Apr 18 17:57:22 localhost kernel: /usr/src/modules/at76c503a/at76c503-fw_skel.c: downloading
firmware atmel_at76c503-rfmd-acc.bin
Apr 18 17:57:32 localhost kernel: /usr/src/modules/at76c503a/at76c503-fw_skel.c: firmware atmel_at76c503-rfmd-acc.bin not found.
Apr 18 17:57:32 localhost kernel: /usr/src/modules/at76c503a/at76c503-fw_skel.c: You may need to download the firmware from http://www.thekelleys.org.uk/atmel or ftp://ftp.berlios.de/pub/at76c503a/firmware/
Apr 18 17:57:32 localhost kernel: at76c503-rfmd-acc: probe of 1-1:1.0 failed with error -14
Apr 18 17:57:32 localhost usb.agent[10975]:      at76c503-rfmd-acc: already loaded

```

I have:

```

# uname -a
Linux stanza 2.6.10-5-686-smp #1 SMP Tue Apr 5 12:41:40 UTC 2005 i686 GNU/Linux
# ls -l /lib/hotplug/firmware/atmel_at76c503-rfmd-acc.bin
-rw-r--r--  1 root root 37804 Apr 12 22:57 /lib/hotplug/firmware/atmel_at76c503-rfmd-acc.bin
# ls -l /usr/lib/hotplug/firmware/atmel_at76c503-rfmd-acc.bin
-rw-r--r--  1 root root 37804 Aug 13  2004 /usr/lib/hotplug/firmware/atmel_at76c503-rfmd-acc.bin

```

I have linux headers installed and compiled the driver
from source (package at76c503-source 0.12beta19-4).

Funny thing is that for some reason the loading seem to succeed
and I occasionally get a working WiFi.

All help is appreciated highly, I'm starting to run out of ideas myself.

-- Juha

PS: With atmel driver I have had even less luck, it does not seem
to compile correctly.

---

