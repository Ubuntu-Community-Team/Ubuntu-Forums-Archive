---
title: "Bluetooth keeps turning ON"
date: 2017-07-31
forum: Networking &amp; Wireless
---

### Post by Hasimir on 2017-07-31
I'm running Ubuntu Gnome 17.04 on the kernel 4.12.4
I specifically set my Bluetooth OFF from both the top right panel and the gnome settings, but at random times (most often after a reboot but not always) I find it turned ON again.
Any clue on how to stop this madness? :)

---

### Post by jeremy31 on 2017-07-31
Do you ever plan on using bluetooth?

---

### Post by Hasimir on 2017-07-31
It is possible, yes, but not often and not in the foreseeable future (months).

---

### Post by jeremy31 on 2017-07-31
Post results for ```
lsusb
```
We could blacklist a bluetooth kernel module or use a udev rule to disable.  I don't use bluetooth very often so I use a udev rule but then I have to edit the rule and reboot to use bluetooth unless I use my small bluetooth dongle

---

### Post by meijer.o on 2017-08-05
Create the following file and make it executable

/etc/rc.local

which contains te code:


#!/bin/sh
rfkill block bluetooth

exit 0


Restart the computer. This will probably solve your issue, you can now turn on your Bluetooth in Gnome settings but it will be off again after a reboot.

---

### Post by Hasimir on 2017-08-05
> **jeremy31 said:**
> Post results for ```
lsusb
```
We could blacklist a bluetooth kernel module or use a udev rule to disable. I don't use bluetooth very often so I use a udev rule but then I have to edit the rule and reboot to use bluetooth unless I use my small bluetooth dongle

Sorry for the slow reply.
The result is:
```

Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 003: ID 8087:0a2b Intel Corp. 
Bus 001 Device 002: ID 0bda:58d2 Realtek Semiconductor Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

But anyway...
> **meijer.o said:**
> Create the following file and make it executable

It works. Thanks a lot to all! :D

---

