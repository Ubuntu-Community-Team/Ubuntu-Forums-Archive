---
title: "ipw2200 version"
date: 2006-11-22
forum: Networking &amp; Wireless
---

### Post by rykel on 2006-11-22
Hi,

Ubuntu comes with ipw2200 driver and firmware.

However, how do I check the version of the driver?

And is the firmware up-to-date?

Thanks!!

---

### Post by zgornel on 2006-11-22
cat /var/log/messages | grep ipw2200 . You should see something like this: *ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.1.2kmprq*
The latest firmware is from March 2006 I think: [http://ipw2200.sourceforge.net/firmware.php](http://ipw2200.sourceforge.net/firmware.php)

---

### Post by rykel on 2006-11-22
wow, when i ran the commands, i received a variety of messages... what concerned me was the "firmware error" and that ipw2200 needs updating...

how do i update ipw2200? (current stable version: 1.2.0)

[INDENT]Nov 22 18:57:36 nil kernel: [17215299.780000] ipw2200: Firmware error detected.  Restarting.
Nov 23 01:22:59 nil kernel: [17179590.028000] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.1.2kmprq
Nov 23 01:22:59 nil kernel: [17179590.028000] ipw2200: Copyright(c) 2003-2006 Intel Corporation
Nov 23 01:22:59 nil kernel: [17179590.028000] Driver 'ipw2200' needs updating - please use bus_type methods
Nov 23 01:22:59 nil kernel: [17179590.028000] ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection
Nov 23 01:22:59 nil kernel: [17179590.248000] ipw2200: Detected geography ZZR (14 802.11bg channels, 0 802.11a channels)
[/INDENT]

---

### Post by zgornel on 2006-11-23
No need to panic. Download v 3.0 of the firmware from [http://ipw2200.sourceforge.net/firmware.php](http://ipw2200.sourceforge.net/firmware.php) and put it in  /lib/firmware/2.6.17-10-generic/ . (Do a backup of the old firmware). Afterwords, do a *sudo ifconfig eth1 down* and *sudo ifconfig eth1 up * and check *dmesg* or the logs.

---

### Post by rykel on 2006-11-23
Hi, thanks!

I shall update the firmware... however, how do I update the Driver?

---

### Post by zgornel on 2006-11-24
> **rykel said:**
> Hi, thanks!

I shall update the firmware... however, how do I update the Driver?
This might provide some help: [http://ipw2200.sourceforge.net/INSTALL](http://ipw2200.sourceforge.net/INSTALL). However, if everything works I wouldn't update the driver.

---

