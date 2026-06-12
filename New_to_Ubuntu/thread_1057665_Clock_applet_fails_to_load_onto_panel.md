---
title: "Clock applet fails to load onto panel"
date: 2009-02-02
forum: New to Ubuntu
---

### Post by PhilOHara on 2009-02-02
Hello everyone,

I am having some trouble with my clock applet. Here's the error message I get:

"The panel encountered a problem while loading "OAFIID:GNOME_ClockApplet"."

This appears whenever I try to add the clock applet to the gnome panel. It didn't use to give me any trouble, but now it won't display the time. I think it may have happened after a software upgrade, but I'm not certain if that was the issue or not. Has any one else had similar issues, like there was a error in an update?

Any ideas?

---

### Post by cmnorton on 2009-02-03
I've found some links:

[https://bugzilla.redhat.com/show_bug.cgi?id=200232](https://bugzilla.redhat.com/show_bug.cgi?id=200232)
[http://forums.fedoraforum.org/showthread.php?t=115080](http://forums.fedoraforum.org/showthread.php?t=115080)

Other than these links, I suggest looking in your logs under /var/log

sudo tail /var/log/messages
sudo tail /var/log/syslog

right after this happens.

I would also post this as a bug up in Ubuntu Launchpad.
[https://launchpad.net/ubuntu](https://launchpad.net/ubuntu)

---

