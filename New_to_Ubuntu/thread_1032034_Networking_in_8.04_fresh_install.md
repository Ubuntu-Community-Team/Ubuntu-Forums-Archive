---
title: "Networking in 8.04 fresh install"
date: 2009-01-05
forum: New to Ubuntu
---

### Post by Sydius on 2009-01-05
I tried to install 8.10 on my girlfriend's new Asus N50V series laptop, but it would get to a point where the display manager would stop working during install and I could do nothing except wait (forever) or reboot.  So I tried 8.04 and it works, but networking doesn't.  Neither wireless nor wired.

The wired connection looks like it is connected, but it doesn't get an IP from dhcp, and I think it's assigning itself one.  Browsing the Internet or pinging Google does not work (host unreachable).  It works fine from all other Ubuntu computers in the house (some 8.04 and some 8.10) without any changes, and it works fine from the same laptop from within Vista.

Any tips?  If I can get the wired connection to work, I may try to get it to upgrade itself to 8.10 and hope that takes care of the wireless.

---

### Post by theozzlives on 2009-01-05
I had to use ndiswrapper in 7.10 and 8.04 on my Dell laptop, 8.10 just found my wireless by itself.

---

### Post by Sydius on 2009-01-12
But NDISwrapper is for wireless, right? Wired networking isn't even working.

---

