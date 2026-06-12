---
title: "One more dial-up problem"
date: 2007-06-09
forum: Networking &amp; Wireless
---

### Post by danopolis on 2007-06-09
I recently downloaded Ubuntu 7.04. I used pppconfig to setup my external serial modem and everything seems to connect fine. I am able to ping addresses sucessfully. However, when i attempt to access web pages or update any packages the system freeezes and I am forced to use the reset button.

Any help would be greatly appreciated.

---

### Post by danopolis on 2007-06-09
I think the problem related to ppp compression. I was able to fix it by adding the following entries to /etc/ppp/options file:

nodeflate
novj
nobsdcomp
noaccomp
nopcomp
defaultroute
noipdefault
noccp

Computer no longer freezes. Now its just a matter of narrowing down exactly which entries are necessary. Hopefully someone else may be able to use this information.

Thanks

---

### Post by poe503 on 2007-06-09
I didn't have any luck using ppp config.  I did get online using the graphical interface located at System>Networking but quickly downloaded Gnome PPP which works great as the dialup interface.

---

