---
title: "Looking for a driver for a Broadcom BCM4312 802.11b/g LP-PHY"
date: 2017-06-20
forum: Networking &amp; Wireless
---

### Post by Joe_G. on 2017-06-20
My girlfriend gave me an old HP Pavillion to tinker with, but I cannot get the wireless card to work. I've found a old forum that helped me out, but when I put the command: > sudo apt-get install firmware-b43-lpphy-installer


I received this response from terminal.

> Package firmware-b43-lpphy-installer is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  firmware-b43-installer




Any ideas?

---

### Post by Hadaka on 2017-06-21
Hi, please open a terminal...ctrl/alt/t...then, from a working wired
connection please Copy and paste one line at a time..
```
lspci -n | awk '/0280/{print$3}'
```
*If and only if the output is--> 14e4:4315  then do..

*Ignore any file not found or error message..do each line one at a time,
```
sudo apt-get update
sudo apt-get remove --purge bcmwl-kernel-source
sudo rm /etc/modprobe.d/blacklist-bcm43.conf
sudo apt-get install b43-fwcutter firmware-b43-installer
sudo modprobe b43
```
Remove wired connection,reboot and test wireless.

**If you have NO internet access you can load the drive using this method.
[https://askubuntu.com/questions/470153/no-wireless-when-install-14-04-on-macbook-pro/470347#470347](https://askubuntu.com/questions/470153/no-wireless-when-install-14-04-on-macbook-pro/470347#470347)
Thanks.

---

