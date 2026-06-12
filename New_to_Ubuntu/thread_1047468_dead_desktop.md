---
title: "dead desktop?"
date: 2009-01-22
forum: New to Ubuntu
---

### Post by mdewet on 2009-01-22
hardy x64

Something strange happened with my desktop, the toolbars and AWN bar works fine, but my background is just black and the desktop don't respond to right-click.  All the shortcuts and hard drives that was usually on my desktop is also not there anymore.

It happened once before but it was corrected after a reboot, but this time it seems to persist even after several reboots.

How can I correct this?

---

### Post by cmnorton on 2009-01-22
Can you get to an x-term login (CTRL+ALT+F1)?

This sounds like your X-term needs reconfiguring.

If you can log in via an x-term, you might consider poking around in /var/log/messages and /var/log/syslog, and look at the output of dmesg.

---

### Post by Hospadar on 2009-01-22
Can you open windows to browse files?

In a typical ubuntu installation nautilus handles the background, desktop icons, etc, so if those are missing it might be a sign that something is wrong with nautilus.

Try starting it from a terminal and looking for exciting output, or maybe purging and re-installing it.

---

### Post by mdewet on 2009-01-22
> **cmnorton said:**
> Can you get to an x-term login (CTRL+ALT+F1)?

This sounds like your X-term needs reconfiguring.

If you can log in via an x-term, you might consider poking around in /var/log/messages and /var/log/syslog, and look at the output of dmesg.

I did that, not changing anything, and after a reboot my desktop was fine again..I still don't know the cause of it, but it's fine now, so until the next time it happens i'm quite happy..

Thanks for the replies

---

