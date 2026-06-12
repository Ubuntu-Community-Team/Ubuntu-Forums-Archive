---
title: "Start x11vnc on boot in 11.04?"
date: 2011-05-29
forum: New to Ubuntu
---

### Post by technopagan on 2011-05-29
Hello,
I'm trying to figure out how to execute a simple startup command on boot in 11.04
I've tried adding this to /etc/rc.local (directly even) to no avail. I've searched and am uncertain how this should be accomplished in 11.04.

I simply want to execute "x11vnc" on boot, any input is greatly appreciated to point me in the right direction. Thanks :o

---

### Post by krunge on 2011-05-29
See the section marked 'Continuously' here:
[INDENT][http://www.karlrunge.com/x11vnc/faq.html#faq-display-manager](http://www.karlrunge.com/x11vnc/faq.html#faq-display-manager)[/INDENT]
You basically add the x11vnc command to the display manager's (e.g. gdm) startup script.

---

