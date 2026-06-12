---
title: "Net connection lost"
date: 2008-04-16
forum: Networking &amp; Wireless
---

### Post by kjaada on 2008-04-16
I am running 7.10 KDE 4.0 and have done so for a while.Also installed 8.04 a few days ago. and 
both systems worked fine on their own HDD's.
Problem is I shut down the 7.10 install this morning and on returning to it it no longer connects to my network.8.04 on the other drive has no problems.When I check the IP address etc they are all 0.0.0.0. and when I put my router 10.1.1.1 into my browser it says can not make connection.
This is with both Gnome and KDE.I have tried powering down my router for a long period but to no avail.

---

### Post by Triggerhapp on 2008-04-16
Impressive, posting without a network connection, teach me how to sometime ok? :D

try these.
```

sudo ifconfig eth0 up
sudo dhclient eth0
```

If your network card is another, use that name instead. Let us know if they throw tantrums :)

---

### Post by kjaada on 2008-04-16
HaHa did not read the post proper:
Have 2  OS's on separate hds and only one is not connecting.
Will try yr code and see how I get on.
Thanks

---

### Post by Triggerhapp on 2008-04-17
> **kjaada said:**
> Have 2  OS's on separate hds and only one is not connecting.
I *was* joking :) any luck?

---

### Post by kjaada on 2008-04-17
Went from bad to worse.Could not get sudo says must be set suid root.I think my problem started with changing ownership of the HDD that the OS is on.Have tried a few things and can now boot but still no sudo or internet connection.I also tried sudo bash to change the password but that won't work either.Will reinstall if it can,t be sorted not really a big deal,more of a niggle.

---

