---
title: "intermitent wifi signal with Netopia TER/GUSB2-N &amp; comcast"
date: 2016-01-31
forum: Networking &amp; Wireless
---

### Post by starrtennis on 2016-01-31
Not sure what other information I need to provide to have this issue debugged. Just let me know.

Disconnecting and reconnecting (in the software; the wifi signal top right corner of the screen) helps sometimes. Maybe there is some command that the machine is issuing that is improper?

I was actually surprised; the wifi worked just after plugging the usb card right in. No drivers or anything needed to be installed. But maybe I need to update it or something?

Thank you.

Edit: The wifi icon in the top right continuously indicates 3/4 bars. No disconnection apparent. But loading timeouts on webpage requests.

---

### Post by Hadaka on 2016-01-31
Hi, from a working wired connection please copy and paste
one line at a time..
```
sudo apt-get update
sudo apt-get dist-upgrade
sudo rm -rf rt73usb
sudo apt-get install linux-firmware
echo "options rt73usb nohwcrypt=1" | sudo tee -a /etc/modprobe.d/rt73usb.conf
sudo modprobe rt73usb
```
remove wired connection,boot and test wireless.

---

### Post by starrtennis on 2016-02-01
Works like a charm. Thank you!

Out of curiosity, what does the code do?

~.

---

### Post by Hadaka on 2016-02-02
Hi, basically just brought your os up to date with security features and  module functions.
sudo apt-get update
sudo apt-get dist-upgrade <- do a search on 'ubuntu what's the difference between update and dist-upgrade'

sudo rm -rf rt73usb <- remove the usb wifi driver

sudo apt-get install  linux firmware <-insures firmware is up to date..see -> [https://wiki.ubuntu.com/Kernel/Firmware](https://wiki.ubuntu.com/Kernel/Firmware)

echo "options rt73usb nohwcrypt=1" | sudo tee -a /etc/modprobe.d/rt73usb.conf <-removes hardware encryption

sudo modprobe rt73usb <- inserts/activates rt73usb wifi driver

you can do a search on each comand for more detailed explination.
please take the time to mark your thread solved by clicking  TOOLS and then SOLVED
thanks.

---

