---
title: "ipw2200 firmware problem"
date: 2005-12-04
forum: Networking &amp; Wireless
---

### Post by joee92 on 2005-12-04
Like many people on the Internet, my linux installation is failing to load its ipw2200 firmware.  I think I caused the problem by installing linux-image-2.6.15-6-686 from the "dapper" release.  Though I have since removed that kernel image and my system seems to be configured the way everyone says it should be, I get the following messages in /var/log/kern.log when I try to "modprobe ipw2200":

Dec  4 15:39:31 hostname kernel: [4297934.075000] ieee80211_crypt: registered algorithm 'NULL'
Dec  4 15:39:31 hostname kernel: [4297934.079000] ieee80211: 802.11 data/management/control stack, 1.0.3
Dec  4 15:39:31 hostname kernel: [4297934.079000] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
Dec  4 15:39:31 hostname kernel: [4297934.091000] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.0.6
Dec  4 15:39:31 hostname kernel: [4297934.091000] ipw2200: Copyright(c) 2003-2004 Intel Corporation
Dec  4 15:39:31 hostname kernel: [4297934.097000] ACPI: PCI Interrupt 0000:06:03.0[A] -> GSI 20 (level, low) -> IRQ 20
Dec  4 15:39:31 hostname kernel: [4297934.097000] ipw2200: Detected Intel PRO/Wireless 2915ABG Network Connection
Dec  4 15:39:41 hostname kernel: [4297944.099000] ipw2200: ipw-2.3-boot.fw load failed: Reason -2
Dec  4 15:39:41 hostname kernel: [4297944.099000] ipw2200: Unable to load firmware: 0xFFFFFFFE
Dec  4 15:39:41 hostname kernel: [4297944.099000] ipw2200: failed to register network device
Dec  4 15:39:42 hostname kernel: [4297944.409000] ACPI: PCI interrupt for device 0000:06:03.0 disabled
Dec  4 15:39:42 hostname kernel: [4297944.409000] ipw2200: probe of 0000:06:03.0 failed with error -5

Here are some relevant aspects of my system configuration:

username@hostname$ uname -r
2.6.12-10-686

username@hostname$ cat /proc/sys/kernel/hotplug
/sbin/udevsend

username@hostname$ ls -l /lib/hotplug/firmware/ipw-2.3-*
-rw-r--r--  1 root root   6472 2005-11-18 05:30 /lib/hotplug/firmware/ipw-2.3-boot.fw-2.6.12-10-686
-rw-r--r--  1 root root 166960 2005-11-18 05:30 /lib/hotplug/firmware/ipw-2.3-bss.fw-2.6.12-10-686
-rw-r--r--  1 root root  16334 2005-11-18 05:30 /lib/hotplug/firmware/ipw-2.3-bss_ucode.fw-2.6.12-10-686
-rw-r--r--  1 root root 161568 2005-11-18 05:30 /lib/hotplug/firmware/ipw-2.3-ibss.fw-2.6.12-10-686
-rw-r--r--  1 root root  16312 2005-11-18 05:30 /lib/hotplug/firmware/ipw-2.3-ibss_ucode.fw-2.6.12-10-686
-rw-r--r--  1 root root 165028 2005-11-18 05:30 /lib/hotplug/firmware/ipw-2.3-sniffer.fw-2.6.12-10-686
-rw-r--r--  1 root root  16344 2005-11-18 05:30 /lib/hotplug/firmware/ipw-2.3-sniffer_ucode.fw-2.6.12-10-686

username@hostname$ grep firmware /etc/udev/rules.d/*
/etc/udev/rules.d/85-pcmcia.rules:# Very few CIS firmware entries (which we use for matching)

Another problem that started occurring at the same time as this is that my host's load average (as reported by "uptime") hovers between 1 and 2, despite the fact that "top" shows few processes utilizing CPU cycles.  Nothing is being logged under /var/log despite the high load.

Any thoughts?  Having spent a few hours on this already, I'm thinking the quickest resolution will probably be just to reinstall breezy.

---

### Post by joee92 on 2005-12-05
I couldn't find any obvious way to reinstall breezy on top of my mixed installation, so I decided to press forward and install all of dapper, including linux-image-2.6.15-6-386.  This seems to have fixed the loading of ipw2200 and its firmware.

The mystery load problem remains.

---

### Post by joee92 on 2005-12-05
The mystery load problem turned out to be ifplugd.  One of the interfaces listed in /etc/default/ifplugd was a Marvell 88E8053 that isn't working anymore.  Thanks to the (lowercase) marvel of wifi, I can live without a wired network for the time being.

---

### Post by mscman on 2005-12-07
I was able to get both my wireless and wired LAN interfaces to work by disabling ACPI for the PCI slots.  If you add "pci=noacpi" to the grub boot sequence, it may work...

BTW, I have the IPW2200 wireless and the marvell 88E8036 ethernet.   

Worked for me, maybe you should try it...

---

