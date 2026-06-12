---
title: "How to make rmmod e100 / modprobe eepro100 permanent?"
date: 2005-05-20
forum: Networking &amp; Wireless
---

### Post by fhennies on 2005-05-20
Thats it. 
Since having problems with the e100 driver and my vpn client i always need to

sudo rmmod e100
sudo modprobe eepro100

but did not manage to make it permanent, neither found something searchng the web.

I would like to make it survive a reboot.


update-modules 

does not help.
Where do i have to place the eepro100?

Any help appreciated...

---

### Post by nad on 2005-05-20
In your modules list, /etc/modules, and blacklist e100, /etc/hotplug/blacklist.

---

### Post by fhennies on 2005-05-21
Thank you, it works!

---

