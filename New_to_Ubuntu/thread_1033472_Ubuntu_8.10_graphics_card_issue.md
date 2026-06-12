---
title: "Ubuntu 8.10 graphics card issue"
date: 2009-01-07
forum: New to Ubuntu
---

### Post by melrokz on 2009-01-07
My PC is 4 years old - (P4 2.4GHz, 160GB HDD, 760MB RAM, Intel 845GL graphics card).
I was using Ubuntu 7.10 till now, and i installed 8.10 recently.
Live CD starts up well, I'm able to install, but the installed version does not start (no GUI, no login screen).
Does Ubuntu 8.10 support Intel 845gl graphics card?
Or could there be any other problem???

---

### Post by quip on 2009-01-07
As a rule, intel is well-supported in Linux.  I would say that there might be something else afoot, since it worked before, and the live cd was fine.

Do you get dropped to a shell?  Does it go through the booting process at all?  Where does it stop?  A little more info would be helpful...

---

### Post by efexD on 2009-01-07
The same thing happened to me. If my memory serves me right goto Boot options-> Boot in VGA. And that seemed to do the trick until i could update some drivers.

---

### Post by Zill on 2009-01-07
Does this help?

[https://wiki.ubuntu.com/IntrepidReleaseNotes]("https://wiki.ubuntu.com/IntrepidReleaseNotes")

> There is a bug in the Intel video driver for the older intel 830 and 845 integrated video cards that are used on laptops like the IBM R30. Desktop effects with compiz will not work on those chips and will freeze the system. For new installations, please install using the safe graphics mode (press F4 in the startup screen) on these systems and disable desktop effects via System -> Preferences -> Appearance, clicking on "Visual effects" and choosing "None".

---

### Post by melrokz on 2009-01-08
Sorry, the live cd also does not start. Only the option to install works with GUI.

---

