---
title: "ipw2200 firmware errors when downloading in Gutsy 7.10"
date: 2008-01-26
forum: Networking &amp; Wireless
---

### Post by Giraffe.SDMB on 2008-01-26
I recently installed Ubuntu Gutsy 7.10 on my Dell Inspiron 9200 laptop.  I've used Redhat and Gentoo quite a bit in the past, but this is my first Ubuntu (and linux laptop) installation.  Very impressive so far, but I have a problem with my wireless card I don't know how to fix.  

The card is an Intel Pro/Wireless 2200BG.  It was easy to set up and connects automatically to my home WPA wireless network.  The problem comes when downloading large files, e.g. streaming video from my MythTV server.  The connection stalls every few minutes, making it impossible to use with MythTV.  dmesg shows firmware errors:
```
Xubuntu-laptop:~> dmesg | grep ipw
[   15.864000] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.2.2
[   15.864000] ipw2200: Copyright(c) 2003-2006 Intel Corporation
[   15.864000] ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection
[   16.192000] ipw2200: Detected geography ZZM (11 802.11bg channels, 0 802.11a channels)
[  196.672000] ipw2200: Firmware error detected.  Restarting.
[  208.960000] ipw2200: Firmware error detected.  Restarting.
[  225.348000] ipw2200: Firmware error detected.  Restarting.
[  233.540000] ipw2200: Firmware error detected.  Restarting.
[  275.080000] ipw2200: Firmware error detected.  Restarting.
[  297.636000] ipw2200: Firmware error detected.  Restarting.

```
This error comes up quite often in Google searches, most of which date back to 2005.  The only proposed solution I found (adding the line "options hwcrypto=0" to /etc/modprobe.d) didn't make a difference.  I just updated the firmware to 3.0 and the driver to 1.2.2 following the directions [from this blog]("http://www.waraey.com/blog/?p=10"), but again it made no difference.  

Any ideas?  I really want to use this laptop as a MythTV frontend, but it's impossible when the wireless keeps dropping connections every few minutes.

---

### Post by Giraffe.SDMB on 2008-01-26
Bump?

---

### Post by Giraffe.SDMB on 2008-01-28
OK, I guess no one else is having this problem.  Too bad.  

Is there a PCMCIA wireless card that works without a hitch under Gutsy 7.10?

---

### Post by Gtaylor on 2008-02-01
This has been the case since Dapper, but the issue hasn't received any real attention. I've had a few bugs open over the last few releases but they never get addressed. The current ticket we're commenting on in hope of getting a response is at [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.15/+bug/27778](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.15/+bug/27778)

Feel free to add to it so the devs see how many people this bug is affecting.

---

