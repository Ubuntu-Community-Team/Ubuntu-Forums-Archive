---
title: "Looking for a wireless SSID browser/viewer that will work in Ubuntu"
date: 2007-07-08
forum: Networking &amp; Wireless
---

### Post by AhrenBa on 2007-07-08
Hey Guys,

I am looking for an SSID browser or viewer that will let me see all the wireless networks an my area? Is there a program I can get that will do this?

---

### Post by justind on 2007-07-08
Kismet is pretty good.

---

### Post by AhrenBa on 2007-07-08
> **justind said:**
> Kismet is pretty good.

OK, I just installed this via the sudo apt-get command and tried to run it. However it is telling me to change something about the packets in the configuration file. Do you know how to do this?

---

### Post by justind on 2007-07-08
No, mine worked fine without changing any settings. Sorry

---

### Post by splintercellguy on 2007-07-08
I think Ubuntu has the Network Manager.

---

### Post by tturrisi on 2007-07-09
open a terminal and type:
iwlist ethX scan
where ethX is the name of your adapter.

---

