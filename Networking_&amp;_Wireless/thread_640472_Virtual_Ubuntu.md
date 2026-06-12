---
title: "Virtual Ubuntu"
date: 2007-12-14
forum: Networking &amp; Wireless
---

### Post by SamTzu on 2007-12-14
I like Ubuntu. And I would like to thank the community and the people who have seen so much trouble to make it for us, BUT...

Consistantly there seems to be problems with Ubuntu and Virtualisation.
Since for some obscure reason Ubuntu's eth0 interface is married with the MAC address.
This is not a problem with most other Linux / windows distributions since they will mostly ignore any MAC address discrepancy.

Not so with Ubuntu.

If you make a VMWare virtual server and distribute it it will not work in most of the servers.

Why, you ask?

Because the MAC address changes
Then you get errors like "SIOCSIDADDR: No such device" eth0: ERROR etc.
Then your eth0 files end up in somewhere like...
/etc/udev/rules.d/70-persistent-net.rules
???

I (and thousands of other people) would really like to see this changed.
Ubuntu is really good Linux distribution that can be used in Virtual Machines.

Please fix this. I would do it myself but I don't know how.

Sam

---

### Post by netztier on 2007-12-14
> **SamTzu said:**
> 
Please fix this. I would do it myself but I don't know how.


Forums are the wrong place for such requests since this is not where developers hang around.

You should open an account on [https://launchpad.net](https://launchpad.net) and submit a bug report there.

best regards

Marc

---

