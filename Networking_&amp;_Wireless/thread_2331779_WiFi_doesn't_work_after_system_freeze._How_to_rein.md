---
title: "WiFi doesn't work after system freeze. How to reinstall drivers?"
date: 2016-07-25
forum: Networking &amp; Wireless
---

### Post by floyd0117 on 2016-07-25
I was browsing the Internet in chrome when my system froze, completely unresponsive. I waited an hour and checked back and it was still frozen, so I had to just power down by holding the power button. Ever since, my WiFi is gone. When I click on the little WiFi icon in the system bar up top, the "Enable Wifi" option is gone, and obviously no WiFi names are present. A proper restart does nothing, and I have no way to get a wired connection established.

Edit: ```
rfkill list all
``` outputs nothing. ```
dmesg | grep iwl
``` outputs nothing. ```
lsmod | grep iwl
``` outputs nothing. ```
lspci
``` outputs ```
3a:00.0 Network controller: Intel Corporation Device 9d21 (rev 21)
```. And ```
sudo dpkg --configure -a
``` outputs nothing.

I've been suggested to reinstall my wifi drivers. How do I go about that, especially with no connection?

---

