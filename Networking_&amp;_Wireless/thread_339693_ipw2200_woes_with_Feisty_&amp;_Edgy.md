---
title: "ipw2200 woes with Feisty &amp; Edgy"
date: 2007-01-16
forum: Networking &amp; Wireless
---

### Post by anders.ostling on 2007-01-16
Hi
Dell D400 laptop with Intel 2200BG wireless card. Everything works just beautiful with OOTB Edgy and also with an dist-update to yesterdays Feisty. Everything except wireless

[   29.464000] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.2.0kmprq
[   29.464000] ipw2200: Copyright(c) 2003-2006 Intel Corporation

[   30.536000] ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection
[   30.620000] ipw2200: dmaWaitSync Failed
[   30.620000] ipw2200: Unable to load boot firmware: -1
[   30.620000] ipw2200: Unable to load firmware: -1
[   30.620000] ipw2200: failed to register network device
[   30.620000] ACPI: PCI interrupt for device 0000:01:03.0 disabled
[   30.620000] ipw2200: probe of 0000:01:03.0 failed with error -5

I have tried to scan the forums and howtos, but no luck so far. Anyone that have any advise to give? Restricted modules, incl firmware are installed (see below)

iissab@iissab-laptop:/lib/firmware/2.6.20-5-generic$ ls -l | grep ipw
-rw-r--r--  1 root root 209190 2007-01-06 16:33 ipw2100-1.3.fw
-rw-r--r--  1 root root 201138 2007-01-06 16:33 ipw2100-1.3-i.fw
-rw-r--r--  1 root root 196458 2007-01-06 16:33 ipw2100-1.3-p.fw
-rw-r--r--  1 root root 191142 2007-01-06 16:33 ipw2200-bss.fw
-rw-r--r--  1 root root 185660 2007-01-06 16:33 ipw2200-ibss.fw
-rw-r--r--  1 root root 187836 2007-01-06 16:33 ipw2200-sniffer.fw
-rw-r--r--  1 root root 111572 2007-01-06 16:33 ipw3945.ucode

iissab@iissab-laptop:/lib/firmware/2.6.20-5-generic$ sudo rmmod ipw2200
Password:
iissab@iissab-laptop:/lib/firmware/2.6.20-5-generic$ sudo rmmod ipw2200
ERROR: Module ipw2200 does not exist in /proc/modules
iissab@iissab-laptop:/lib/firmware/2.6.20-5-generic$ sudo modprobe ipw2200
iissab@iissab-laptop:/lib/firmware/2.6.20-5-generic$ dmesg|tail -10 
[ 1884.504000] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.2.0kmprq
[ 1884.504000] ipw2200: Copyright(c) 2003-2006 Intel Corporation
[ 1884.504000] ACPI: PCI Interrupt 0000:01:03.0[A] -> Link [LNKB] -> GSI 5 (level, low) -> IRQ 5
[ 1884.504000] ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection
[ 1884.552000] ipw2200: Unable to load ucode: -22
[ 1884.552000] ipw2200: Unable to load firmware: -22
[ 1884.556000] ipw2200: failed to register network device
[ 1884.556000] ACPI: PCI interrupt for device 0000:01:03.0 disabled
[ 1884.556000] ipw2200: probe of 0000:01:03.0 failed with error -5


See you
Anders

---

### Post by pcr1 on 2007-01-17
No joy here. I have an Acer Travelmate 4010 with Edgy.   I downloaded and installed ieee80211-1.2.16, and ipw2200-1.2.1 from sourceforge, and the firmware files too.    Install was nominal, and dmesg gives:

pcr1@Alpha:~$ dmesg | grep ipw
[17179585.308000] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.2.1mprq
[17179585.308000] ipw2200: Copyright(c) 2003-2006 Intel Corporation
[17179585.308000] ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection
[17179585.524000] ipw2200: Radio Frequency Kill Switch is On:
[17179585.528000] ipw2200: Detected geography ZZM (11 802.11bg channels, 0 802.11a channels)

What am I missing?

---

### Post by svQuick on 2007-04-11
I had this problem on my toshiba- you can shut off ACPI in boot/grub/menu.lst by adding no acpi acpi=off after your current kernel load line, the first one without a stopper #.  The problem is that you loose power management.  If someone finds a fix that works with both ACPI and the ipw2200 please let us know.  I have been running like this for about 6 months with no problems but I would like power management.

---

