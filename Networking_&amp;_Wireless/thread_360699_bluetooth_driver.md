---
title: "bluetooth driver"
date: 2007-02-13
forum: Networking &amp; Wireless
---

### Post by isw on 2007-02-13
Ok, a different question for you all...

I need this info for windows so I can download the correct driver, I dont have the driver cd anymore and I cant remember the vendor of the bluetooth dongle, and windows default drivers doesn't work ... so Im trying to find out which driver to download. 

Is there a way in (x)ubuntu to find ouch what vendor bluetooth device is (if the info is there at all?).

---

### Post by GoingDown on 2007-02-13
Plug the dongle in and take a look of "dmesg" (just run dmesg command from console and see things from end of it).

Or, run command "tail -f /var/log/syslog", and put the dongle in (note that after that command you must leave console open, and tail command running)

Also, lsusb command will give you some info (lsusb -v will give you really verbose output)

---

### Post by isw on 2007-02-13
lsusb -v did the trick! thanks!

---

