---
title: "How know what programs using network ?"
date: 2007-05-18
forum: Networking &amp; Wireless
---

### Post by christian.convey on 2007-05-18
Gnome System Monitor is showing some substantial network activity, but I can't figure out which program(s) are the culprit(s).

How can I figure that out?

(I've tried shutting down various applications and services, and that hasn't done the trick.)

---

### Post by Ateo on 2007-05-18
You can check program network activity with the program netstat. Just type 'netstat' from console (without quotes).

---

### Post by christian.convey on 2007-05-18
> **Ateo said:**
> You can check program network activity with the program netstat. Just type 'netstat' from console (without quotes).

It looks to me like the most info of that sort that netstat can provide, is the number of currently undelivered bytes in the send/recv queue for each process.

I was hoping to find a tool that will tell me either (a) the total number of bytes a process has sent/received (so I can watch that number evolve) or, (b) even better, something like the "top" program that sorts processes according to their total network activity over the last *n* seconds.

---

### Post by srt4play on 2007-05-18
Check this out:

[http://sourceforge.net/projects/gnetworkmonitor](http://sourceforge.net/projects/gnetworkmonitor)

It looks like it does what you want, and I am interested in it also.

I can't get it to run though, the .rpm converts ok in alien but it will not run.  The source builds but again the program will not run, first complaining about missing pysqlite2 and after installing that, complaining about a local variable "syslog_rc".

If you get it to run please post about it.

---

### Post by jhrozek on 2007-06-05
Hello,
sorry for coming late into this thread. 

There is a DEB package for Ubuntu made by Oliver Schmidtke at [http://ubuntu.schmidtke-hb.de/](http://ubuntu.schmidtke-hb.de/) That might work better than alienized RPM or the source distribution..

On a side note, of you experience problems with the program, please file them as bugs on the project's space on sourceforge.net - they may actually get fixed :-)

Jakub
GNM Maintainer

---

### Post by srt4play on 2007-06-06
Thank you very much for providing that link.  I have gnome network monitor running now but it doesn't do what the OP wanted.  It does however provide an easy way to see what programs are talking to the network.

---

