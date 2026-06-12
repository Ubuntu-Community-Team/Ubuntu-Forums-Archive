---
title: "ndiswrapper only works when root"
date: 2007-11-12
forum: Networking &amp; Wireless
---

### Post by wfriesen on 2007-11-12
I'm running Gutsy Gibbon, and have a D-Link AirPlus G DWL-G510 (rev.C) set up using ndiswrapper.
Now, I can enable the card by running

modprobe ndiswrapper
iwconfig wlan0 mode Managed
dhclient

which allows me to connect to my router. The problem is, this only works when I'm logged in as root. As a normal user I get this

$ modprobe ndiswrapper
FATAL: Error inserting ndiswrapper (/lib/modules/2.6.22-14-generic/misc/ndiswrapper.ko): Operation not permitted


So, I have a few questions.
How can I get this to work when I'm not root?
And how can I set it up to happen automatically when I boot up?

Thanks

---

### Post by zanglang on 2007-11-12
Well, you can't load modules into the kernel without some kind of priveleges. You can however add 'ndiswrapper' to the list of modules to automatically load on startup though. Just add the line 'ndiswrapper' into /etc/modules, and reboot.

(I recall ndiswrapper is already automatically loaded by default, though. You can probably try skipping that step and see if it works.)

---

### Post by kevdog on 2007-11-12
When inserting modules into the kernel you need to have root-like privileges.  Hence its

sudo modprobe ndiswrapper

To make it load at startup

echo ndiswrapper | sudo tee -a /etc/modules

Thats it.  By inserting it into the kernel as a custom module and loading it at startup, it will be accessible for all users.

---

