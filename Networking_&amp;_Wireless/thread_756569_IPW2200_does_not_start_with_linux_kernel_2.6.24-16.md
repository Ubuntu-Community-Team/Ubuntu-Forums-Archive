---
title: "IPW2200 does not start with linux kernel 2.6.24-16"
date: 2008-04-16
forum: Networking &amp; Wireless
---

### Post by ibmg on 2008-04-16
My wireless card Intel 2200BG was working when I was using the linux 2.6.24-12 kernel. However after an auto update from the repositories installed 2.6.24-16 kernel, my wireless card was no longer running/installed.

I've managed to trace the problem to the IPW2200 not starting with error messages
Unable to load firmware: -2

If I load Ubuntu using the 2.6.24-12 kernel, everything works as usual.

Anyone has any ideas for a fix to have wireless working in 2.6.24-16 kernel?

---

### Post by Whiffle on 2008-04-16
Have a look in /lib/firmware .  If I remember correctly, each kernel version is listed in there and has its own firmware folder.  With the kernel update, I think the firmware didn't get installed into a directory where the kernel expects it.  There might be package to reinstall the firmware in the correct directory, but you would probably be okay just copying it over to a directory with the name of the new kernel.

---

### Post by ibmg on 2008-04-16
Hi whiffle, thanks for the quick reply.

Yes they have different folders for different kernels but both folders already have the necessary files which are
ipw2200-bss.fw
ipw2200-ibss.fw
ipw2200-sniffer.fw

Are there any other files that might be required?

---

### Post by Whiffle on 2008-04-16
Try doing

sudo modprobe ipw2200

and then 

dmesg

It might give some more info.  If nothing else, you could download the firmware from [http://ipw2200.sourceforge.net/firmware.php](http://ipw2200.sourceforge.net/firmware.php) and install it.  I'm kind of out of ideas at the moment.

---

### Post by ibmg on 2008-04-16
Thanks for trying whiffle but...

I tried getting new firmware, mounting /sys (as mentioned in the site's INSTALL doc) but still same results

dmesg | ipw2200 results are

> [   20.981407] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.2.2kmprq
[   20.981411] ipw2200: Copyright(c) 2003-2006 Intel Corporation
[   21.142256] ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection
[   23.236277] ipw2200: ipw2200-bss.fw request_firmware failed: Reason -2
[   23.236283] ipw2200: Unable to load firmware: -2
[   23.236287] ipw2200: failed to register network device
[   23.242442] ipw2200: probe of 0000:04:02.0 failed with error -5


---

### Post by dgcaste on 2008-05-29
my first order of troubleshooting is to let the computer cool off for half an hour to an hour. this actually fixed my problem when I had an identical one. your next order of business is to download the new firmware:

[http://ipw2200.sourceforge.net/firmware.php](http://ipw2200.sourceforge.net/firmware.php)

and put it in the place of the old firmware. I also recommend compiling the new firmware altogether. the ieee80211 libraries are already installed but depending on what packages you have installed they might be placed on the right locations or not. you can find the source code for ipw2200 at that sourceforge parent page.

---

