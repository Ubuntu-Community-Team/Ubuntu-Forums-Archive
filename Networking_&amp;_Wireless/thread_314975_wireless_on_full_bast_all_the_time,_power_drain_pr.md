---
title: "wireless on full bast all the time, power drain problem"
date: 2006-12-08
forum: Networking &amp; Wireless
---

### Post by double u u on 2006-12-08
thinkpad x60s intel pro wireless 3945abg,

wireless working (after much fiddling), problem is that it's on and active when not using wireless-related tasks.  This is the draining battery big time and worsens the already bad right palm-rest temperature problem on the x60s'.
 
is there a way to step the wireless down?
a new manager or driver?

any help appreciated!

-new linux user

---

### Post by Spif on 2006-12-15
Have you tried "sudo eth1 power on"? That enables power saving mode for the old 2200 wireless card, maybe it works with 3945 too.

In Windows you can fiddle with lots of power management settings for the card, so it should be possible in Linux too...

---

### Post by Spif on 2006-12-15
Found this on Intel's site:

> Intel® Intelligent Scanning Technology reduces power by controlling the frequency of scanning for access points

A user selectable feature with five different Power states, which allows the user to make their own power vs. performance choices when in battery mode

Lots of settings to control power consumption, all we need to know now is how to enable them.

---

### Post by Spif on 2006-12-30
sudo iwpriv eth0 set_power 7

That should set it to a power saving state. Works great on my X60s!

---

