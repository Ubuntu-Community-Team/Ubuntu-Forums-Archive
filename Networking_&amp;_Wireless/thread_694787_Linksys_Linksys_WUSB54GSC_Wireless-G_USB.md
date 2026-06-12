---
title: "Linksys Linksys WUSB54GSC Wireless-G USB"
date: 2008-02-12
forum: Networking &amp; Wireless
---

### Post by Johnemil on 2008-02-12
I tried installing a Linksys WUSB54GSC on a Dell Inspiron 8100 running Gutsy.

I used ndiswrapper and it scans fine, locating both my WEP network and two strong unprotected networks. But nothing connects.

Based on a post that notes a power problem, I tried this:

[I]sudo nano -w /etc/udev/rules.d/99-custom.rules
* In the resulting window that opens, type the following on one line:
BUS==”usb”, SYSFS{idProduct}==”0026&#8243;, SYSFS{idVendor}==”13b1&#8243;, RUN+=”/bin/sh -c ‘echo 1 > /sys/$devpath/device/bConfigurationValue’”
[/I]

Two problems: 

1. The card number reports as 20, not 26.
2. Running this either way (20 or 26), I get a boot error trying to handle the bConfigurationValue

Any other ideas?

Johnemil

---

### Post by dca on 2008-02-12
Hmmm, I couldn't even tell you what that option that you added does...
 
For GP, would it be a pain to go to your wireless router, change the WEP key to use key #1 (not #2, 3, or 4 like some allow youto do) and set it for something simple like 64-bit ASCII and see if it allows you to connect then...

---

