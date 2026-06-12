---
title: "DSE xh6859 can't compile driver"
date: 2006-09-18
forum: Networking &amp; Wireless
---

### Post by peterroots on 2006-09-18
I have a usb wirless adaptor from DSE - xh6859 - which is based on a zd2101 chip.
Nothing worked when I plugged it in but I did find a driver file and firmware file on sourceforge.
The driver fails on make due to a missing folder

make -C /lib/modules/`uname -r`/build/ M=/home/peter/Download/zd1201-0.14 modules
make: *** /lib/modules/2.6.15-23-386/build/: No such file or directory.  Stop.
make: *** [modules] Error 2

I then found linux-wlan-ng using Adept so I installed this - no drivers or firmware for my wifi were installed and still nothing worked.

next I tried to iinstall the firmware as there was a driver for zd1211 which I thought might work.
make for the firmware failed as the kubuntu location for frimware did not match the folders the make file was using.  I then manually copied the 2 files and rebooted.
things now sort of work, I get an IP address but am unable to use the network and kwifimanager reports I am out of range even though I can see the router (in the config page).

Perhaps if I had the correct driver things would work better.

What do I need to install to be able to get make to work?

---

### Post by tturrisi on 2006-09-18
[http://linux-lc100020.sourceforge.net/](http://linux-lc100020.sourceforge.net/)

---

### Post by peterroots on 2006-09-19
Thanks, but that was the driver I down loaded - the firmware is in place but I can't compile the dirver.  I do notice now (having gone back to look) that the driver claims to be included in the 2.6 kernel. so maybe I don't need to compile it after all.
At the moment sometimes things work and sometimes they don't - I have yet to figure out what is different on those occasions when things do work!!
Life is one big learning experience!

---

