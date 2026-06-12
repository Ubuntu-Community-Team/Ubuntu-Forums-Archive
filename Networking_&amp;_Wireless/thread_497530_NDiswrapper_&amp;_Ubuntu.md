---
title: "NDiswrapper &amp; Ubuntu"
date: 2007-07-10
forum: Networking &amp; Wireless
---

### Post by suspend on 2007-07-10
Any idea why ndiswrapper does not come with Ubuntu?  I have a gateway 7405gx with a broadcom and I need to, sadly, use the windows driver.  I tried out PCLinuxOS the other day and the install realized this and asked me fir the .inf file, I have never had a distro that did this.  I like PCLinuxOS (with gnome of course), but was wondering why Ubuntu does not include the same "feature".  Does this have to do with the "open" vs "closed" Ubuntu policy on software/drivers?  If so, they should at least include ndiswrapper so you can decide on your own what driver type you will use.  Any ideas?

---

### Post by spd106 on 2007-07-10
Ubuntu has included the ndiswrapper kernel modules since at least Ubuntu 6.06 (Dapper), only the user space utilities necessary to load the firmware weren't installed by default, though they used to be on the CD. For some reason they were dropped in Ubuntu 7.04 (Feisty).

I agree that it should have been much more easier to use in the last two releases, I guess it just seems to have been a low priority. However, I believe the Restricted Driver Manager in Ubuntu 7.10 (Gutsy) should be upgraded with the necessary functionality to allow you to install your windows drivers.

---

### Post by multiscan69 on 2008-03-13
I got the ubuntu bible which came with ubuntu 6.
the book says that i have ndiswrapper, but I don't and my futil atempts to load it are becoming frustrating.
please help!

---

