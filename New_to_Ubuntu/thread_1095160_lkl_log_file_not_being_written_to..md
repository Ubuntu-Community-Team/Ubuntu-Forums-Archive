---
title: "lkl log file not being written to."
date: 2009-03-13
forum: New to Ubuntu
---

### Post by juicyoner on 2009-03-13
hello all -

i am trying to run lkl (keylogger) on my machine. my run command is as follows:

sudo lkl -l -k /usr/share/lkl/keymaps/us_km /home/username/log.temp

But the log file never gets written to. i've tried running 'touch' on the file beforehand to make sure it is there, but that doesn't help.

Any ideas?

---

### Post by pytheas22 on 2009-03-13
In my experience, lkl is a pretty buggy program, and it doesn't provide much debugging information.  It's possible that it's not really running at all when you try to start it.  It also may not work with your keyboard (meaning it's running but is not logging anything, hence no logfile)--as I recall, it doesn't like most USB keyboards.  I've tried lkl on half a dozen different Ubuntu machines and never had it work the way it's supposed to (in the two cases where it worked at all, it made the system almost unresponsive while it was running).

The only keylogger I've found that works reliably on Linux is [pykeylogger]("http://pykeylogger.wiki.sourceforge.net/").  Its disadvantages are that it only logs activity in X sessions (so keys in virtual terminals won't be recorded, and you have to start a new pykeylogger session for each X session/user on the machine) and it's not designed to be stealthy (but I'm sure that's not a problem because you wouldn't be asking about keyloggers here if you were doing anything illegal).  But it produces reliable logs and has nice features.  I'd look into it instead of lkl if I were you.

---

### Post by juicyoner on 2009-03-13
Thanks for the ideas!

yes, nothing illegal going on here. I just want to keep some usage stats on my home machine - which is only used by me.

---

