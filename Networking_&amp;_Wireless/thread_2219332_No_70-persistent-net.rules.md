---
title: "No 70-persistent-net.rules?"
date: 2014-04-23
forum: Networking &amp; Wireless
---

### Post by jruden on 2014-04-23
I am trying to see/control how my 14.04 ubuntu server maps NICs to ethX names. I have two NICs in my host.

Usually with earlier versions (and also suggested by Ubuntu Server Guide for 14.04!) I configure the file /etc/udev/rules.d/70-persistent-net.rules in which Ubuntu writes mappings for the interfaces after having discovered them for the first time.

However with 14.04 there is no such file at all! How is this managed in 14.04?

---

### Post by jruden on 2014-04-25
Hi, I got the interfaces in correct order by refreshing their MAC addresses in the virtual box settings.

Still I am confused though, as to why no 70-persistent-net.rules is written.

---

### Post by Doug S on 2014-04-25
> **jruden said:**
> Usually with earlier versions (and also suggested by Ubuntu Server Guide for 14.04!) I configure the file /etc/udev/rules.d/70-persistent-net.rules in which Ubuntu writes mappings for the interfaces after having discovered them for the first time.Yes, this change was not captured in the 14.04 Serverguide. I'll put in a bug report.

See these:
[https://wiki.gentoo.org/wiki/Udev/upgrade](https://wiki.gentoo.org/wiki/Udev/upgrade)
[http://www.freedesktop.org/wiki/Software/systemd/PredictableNetworkInterfaceNames/](http://www.freedesktop.org/wiki/Software/systemd/PredictableNetworkInterfaceNames/)

Edit: [Bug report]("https://bugs.launchpad.net/serverguide/+bug/1312785")

---

### Post by jruden on 2014-04-26
> **Doug S said:**
> Yes, this change was not captured in the 14.04 Serverguide. I'll put in a bug report.
Ahh, nice. This explains my confusion, it has really been a change in this area. Great links and bug report. Thanks!

---

