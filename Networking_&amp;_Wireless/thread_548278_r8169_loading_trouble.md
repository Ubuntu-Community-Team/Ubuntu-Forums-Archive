---
title: "r8169 loading trouble"
date: 2007-09-11
forum: Networking &amp; Wireless
---

### Post by brujoand on 2007-09-11
hi
i'm running Ubuntu 7.10 on a dual core laptop and everything works nicely(including wireless and suspend !! ) But when i boot up and plug in an network kabel, nothing happens, there is no way i can get an ip, not statical or for dhclient. However reloading the modul like this
"
rmmod r8169
modprobe r8169
"
Makes eveything nice and dandy, but its a pain having to do this at every boot up as a script as this would not because modprobe can not be run as suid. 

- also i can mention that when i boot with tha cable plugged in, everything works fine. 

Any ideas?

tnx .)

---

### Post by noob12 on 2007-09-11
That you have to have the cable connected (to a live endpoint) is a known issue
[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/86798](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/86798)

---

