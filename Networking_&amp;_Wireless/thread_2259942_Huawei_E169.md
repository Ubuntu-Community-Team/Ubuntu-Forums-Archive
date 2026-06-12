---
title: "Huawei E169"
date: 2015-01-08
forum: Networking &amp; Wireless
---

### Post by asus77x on 2015-01-08
Im running ubuntu 13.10 as VM in ESXi 5.0, usb passthrough is enabled and huawei E169 plugin in host. E169 tested in other OS and working well.

* in ubuntu, unable to conenct to internet cause no profile yet. so added new profile for mobile broadband and still not work.
* check in dmesg and lsusb and cannot see huawei e169 in list. likely the passthrough not working?
* test using usb thumbdrive and i can see it come in to ubuntu screen, so confirmed passthrough is working there.
* tried set e169 with modprobe and wvdial, but not work.
* test again e169 in other OS, and still working well.

anyone can advice? quite desperate with 13.10

thanks

---

### Post by mörgæs on 2015-01-08
Hi, welcome to the fora.
First step is installing 14.04 or 14.10, because 13.10 is out of support. Best is to use wired connection.

Please post again when that is working.

---

### Post by asus77x on 2015-01-12
hi morgaes

just finished installing 14.10, but after plugin and do lsusb, there's no huawei appear. back to thumbdrive, working well. any idea?

---

### Post by mörgæs on 2015-01-12
Sorry, I don't have more ideas but there are several capable people here in Networking and Wireless.

---

