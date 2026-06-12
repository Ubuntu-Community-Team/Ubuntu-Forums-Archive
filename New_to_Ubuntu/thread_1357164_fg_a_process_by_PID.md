---
title: "fg a process by PID"
date: 2009-12-16
forum: New to Ubuntu
---

### Post by taras.di on 2009-12-16
Hi all,

I'm running bash on a GNU/Linux box.

I'm trying to restore an emacs process I sent to the background (emacs is running in non-windowed mode) by using fg <pid>, but it's not working.

* start emacs with: emacs -nw
* ctrl-z to send emacs to sleep
* ps shows:

8476 pts/0    00:00:00 emacs
8485 pts/0    00:00:00 ps
14615 pts/0    00:00:00 bash

* fg 8476 gives:

bash: fg: 8476: no such job

* typing in fg works

What am I missing?

Thanks

Taras

---

### Post by bodhi.zazen on 2009-12-17
I believe you need to specify a job by job number or name (ie emacs), but I do not know how to do it using the PID

fg %1
fg emacs

[http://www.museum.state.il.us/ismdepts/library/linuxguides/abs-guide/x5514.html](http://www.museum.state.il.us/ismdepts/library/linuxguides/abs-guide/x5514.html)

---

### Post by taras.di on 2010-01-05
Hmm, that didn't work either! Anyone have any ideas?

Thanks

Taras

---

### Post by falconindy on 2010-01-05
What you want is the 'jobs' command. Then follow bodhi's advice about using 'fg %job'.

---

