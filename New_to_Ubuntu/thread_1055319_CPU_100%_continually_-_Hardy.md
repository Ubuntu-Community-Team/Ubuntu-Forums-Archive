---
title: "CPU 100% continually - Hardy"
date: 2009-01-30
forum: New to Ubuntu
---

### Post by Kellemora on 2009-01-30
Hi Gang

My CPU has been running at 100%

System Monitor Shows these items:

gpilotd SLEEPING cpu usage 93% Nice 0
gnome-system-monitor RUNNING 4%


Switching to HTOP shows:

97.4% to 98% fluctuating /usr/bin gpilotd
1.3% also fluctuation htop
0.7% /usr/bin/X

Yes I did a hot sync with a Palm E2 this morning, had an error, out of storage space, HA......  20 megs internal FREE, 940 megs Card is Free, 18 gigs free on HD.

In other words, I've never got the Palm to work right on Ubuntu!

But nonetheless, it shouldn't HOG the CPU all day long!

Force Ending the Process does restore the CPU back down to like 4 to 8%, but it then requires a reboot to sync the calendar.

Also, NEVER have found where it HIDES the documents from the card?

Bug or ?????

TTUL
Gary

---

### Post by spcwingo on 2009-01-30
Sounds like this bug:

[https://bugs.launchpad.net/ubuntu/+source/gnome-pilot/+bug/29043]("https://bugs.launchpad.net/ubuntu/+source/gnome-pilot/+bug/29043")

---

### Post by Kellemora on 2009-01-30
Hi SPC

Yeppers!

That's it!

REPORTED first on January 16, 2006

I had tried my Palm once before on Ubuntu, perhaps this is why I went back to the DOZE for keeping it updated?

Unresolved after 3 years, with Medium priority yet, is really unbelievable!

But there are TONS of other unresolved issues much more important than making a Palm work, and many of those are well beyond the 2 year mark also!

Can't mark it solved since the problem still exists!

Killall Reboot, the usual FIX, hi hi...........

TTUL
Gary

---

