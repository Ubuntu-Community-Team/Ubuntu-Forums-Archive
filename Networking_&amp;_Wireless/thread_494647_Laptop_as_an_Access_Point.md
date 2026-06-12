---
title: "Laptop as an Access Point"
date: 2007-07-07
forum: Networking &amp; Wireless
---

### Post by Paris Heng on 2007-07-07
Dear friends ,

I am currently doing my assignment on building an access point on laptop using Linux.

I have search for the driver for access point, that is HostAP. This HostAP required Prism Chipset in order to run.

Do you all know any other driver that can make my laptop become an access point? 

I am trying very hard to search it. Please assist, thousand thank.

---

### Post by spd106 on 2007-07-07
Atheros based cards using the madwifi driver (default in most distros, though uses a binary blob) can also work with hostapd. In fact any card with a driver capable of master mode can be used as an AP.

This page from IBM is a nice introduction, even though it is a little old now. Especially as they use a Debian system.
[http://www.ibm.com/developerworks/linux/library/l-wap.html](http://www.ibm.com/developerworks/linux/library/l-wap.html) 

Also take a look at this wiki page
[https://help.ubuntu.com/community/Router](https://help.ubuntu.com/community/Router)

If you make good progress then please help by expanding the missing sections.

---

### Post by Paris Heng on 2007-07-08
You mean any card with Master Mode can use as a HostAP? So, we don't care about the Prism chipset in the WLAN card? Are you sure i can do that?

Thank you

---

### Post by Paris Heng on 2007-07-08
Anyways what u mean by (default in most distros, though uses a binary blob) ?

Please assit

---

