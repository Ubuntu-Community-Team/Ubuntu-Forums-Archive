---
title: "screen blanks at login"
date: 2010-01-15
forum: New to Ubuntu
---

### Post by rrashkin on 2010-01-15
Greeting.

First let me say that I realize that among the serious problems some people have, this is really quite trivial.  That said...

Since I installed 9.10, when I click my user name at the login screen, the whole screen bounces, then goes blank (for maybe a second), then it comes back with the password entry.

Like I said, it's a small problem but I just wondered if anyone knows why it happens and if there is some possible fix.  I have an EVEREX with VIA graphics.

---

### Post by phidia on 2010-01-15
There are several ways to troubleshoot this, after login you could open a terminal and type dmesg, press <enter> and look through that for anything that's graphics related.
You can also view your most recent logfiles either from the logfile menu under system or from /var/log 
Hope that helps

---

### Post by dzon65 on 2010-01-15
And,perhaps silly,but when you see the gdm,click on user........there's a panel at the bottom.Check if it's set on gnome session.

---

