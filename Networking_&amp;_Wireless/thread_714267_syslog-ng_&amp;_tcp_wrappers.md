---
title: "syslog-ng &amp; tcp wrappers"
date: 2008-03-03
forum: Networking &amp; Wireless
---

### Post by seeker1458 on 2008-03-03
Ok got a question!

I just built a gutsy box, and am replacing syslogd w/ syslog-ng. I've gone through and installed the following: eventlog-0.2.5, gettext-0.17, glib-2.2.3, pkgconfig-0.15.0.  Then I compiled and installed syslog-ng-2.0.8.  The only problem is I don't think I am using syslog-ng.  When I run the top command in terminal I still see syslogd at the botttom of the list...not syslog-ng.  Also, I am wanting to use this machine to monitor some hardware on a domain.  I can rdp via tightvnc as the system sits, so do really I need to recompile using tcp-wrappers?, If so, how do I do that...b/c when I run ./configure in the tcp-wrapper dir, i get a not found.  If I run make, I get a message saying to define REAL_DAEMON_DIR. also do I have to go though the hastle of joining the machine in AD?   Any help is appreciated, and if I need to move this to another forum just let me know where to put it.  Thanks.

---

### Post by grittyminder on 2008-03-03
Out of curiosity, is there any particular reason why you are using the binary and not the syslog-ng package?

---

### Post by seeker1458 on 2008-03-04
I am using 2.0.8, the most current edition available from Balabit's website. Is there a .deb or something elese that has everything (all the necessary dependencies) already compiled?

---

### Post by grittyminder on 2008-03-04
Now that you mention it, it does look like the default Ubuntu syslog-ng package is... pretty damn old. Maybe I'll try using the binary myself (I've been having difficulties with the default package). Sorry I can't help you...

---

