---
title: "Usb asus usb-n13"
date: 2010-11-21
forum: New to Ubuntu
---

### Post by Tagged on 2010-11-21
Would these instructions work for both 32 bit and 64 bit installs?  I do not see the instructions state if they are running 32 or 64 bit and want to see if that will affect anything.

Instructions found on newegg are:

```

Step 1:
sudo gedit /etc/udev/rules.d/network_drivers.rules

Step 2 (add the follow text to the file and save):
ACTION=="add", SUBSYSTEM=="usb", ATTR{idVendor}=="0b05", ATTR{idProduct}=="1784", RUN+="/sbin/modprobe -qba rt2870sta"

Step 3:
sudo gedit /etc/modprobe.d/network_drivers.conf

Step 4 (add the follow text to the file then save):
install rt2870sta /sbin/modprobe --ignore-install rt2870sta $CMDLINE_OPTS; /bin/echo "0b05 1784" > /sys/bus/usb/drivers/rt2870/new_id

```

Will this work with my 64 bit Ubuntu 10.10?   Thanks all!!

---

### Post by cariboo on 2010-11-22
Because you didn't give us what the instructions are about, I would suggest you try them. Be sure to make a backup of /etc/udev/rules.d/network_drivers.rules, before you make any changes, just in case something goes wrong.

---

