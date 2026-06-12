---
title: "How to Disable Onboard NIC"
date: 2008-10-04
forum: Networking &amp; Wireless
---

### Post by jecottrell on 2008-10-04
I'm now using a wireless PCI card and would like for the onboard NIC not to be brought up during boot. (It's causing problems.) How do I do that? 

I have searched and haven't found the answer....


Thanks,

John

---

### Post by mindoms on 2008-10-04
quick fix: Disable in Bios, or by jumper on mainboard

---

### Post by lswb on 2008-10-04
mindoms suggestion of disabling in BIOS is good. If that is not practical you can blacklist the driver module for the ethernet port. You will have to determine what the driver is, then add the line "blacklist drivername" to any file in /etc/modprobe.d (or make a new file with this line in it)

To find the module name, in a terminal try 

lshw -C network|more

and look for "module=name" in the section for your ethernet interface. It can be a little tough to spot, maybe someone else knows a better way to determine the module name.

---

### Post by lswb on 2008-10-04
mindoms suggestion of disabling in BIOS is good. If that is not practical you can blacklist the driver module for the ethernet port. You will have to determine what the driver is, then add the line "blacklist drivername" to any file in /etc/modprobe.d (or make a new file with this line in it)

To find the module name, in a terminal try 

lshw -C network|more

and look for "module=name" in the section for your ethernet interface. It can be a little tough to spot, maybe someone else knows a better way to determine the module name.

---

