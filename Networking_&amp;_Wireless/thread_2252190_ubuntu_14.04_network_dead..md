---
title: "ubuntu 14.04 network dead."
date: 2014-11-10
forum: Networking &amp; Wireless
---

### Post by jackzhp on 2014-11-10
When i turned on my ubuntu, i can use internet, then after a while, Not to mention web browsers. I type
ping [www.google.com](www.google.com)
 no response, dead
And can not quit by control c.
ping 192.168.1.1
No response, dead either 

Seems some thing is locked. And the computer is not able to shutdown or restart. I have to power it off.

Any idea how to.solve this? Thanks.

---

### Post by houstonbofh on 2014-11-10
If ctl-c will not break you out, it is not a network problem, but a hard lock.  For reboots, you might want to try raising elephants.  [http://www.howtogeek.com/119127/use-the-magic-sysrq-key-on-linux-to-fix-frozen-x-servers-cleanly-reboot-and-run-other-low-level-commands/](http://www.howtogeek.com/119127/use-the-magic-sysrq-key-on-linux-to-fix-frozen-x-servers-cleanly-reboot-and-run-other-low-level-commands/)

But as to why, you will have to dig.  While locked, you can try to look at the logs, either by ssh from another machine, or with SysRq-r and alt-F-ing into a new terminal.  Also, running memtest86 overnight might help.

---

