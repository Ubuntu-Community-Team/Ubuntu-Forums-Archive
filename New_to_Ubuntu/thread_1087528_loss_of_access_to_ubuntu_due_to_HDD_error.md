---
title: "loss of access to ubuntu due to HDD error"
date: 2009-03-05
forum: New to Ubuntu
---

### Post by neilfaraway on 2009-03-05
Hi All,

About 2 months ago I installed ubuntu and have had a great experience so far.  Unfortunately as of yesterday my machine hangs just before it finishes booting into the desktop environment.  All the icons and task bars are there but my hard drive stays active with a regular repetitive 'working' light & noise.  Upon trying to open one of the menus to find a HDD scan tool my computer hangs.

So I am assuming a part of my HDD (which ubuntu needs to read to finish loading) has given up the ghost.  My question is: is there some way I can intervene at some point during boot up and perform a scan disk or something to make things better?

I guess worst case is a OS re-install...

Oh and on one repeat of trying to get my machine to work the desktop disappeared and the following type of messages filled the screen:

[294.371006] ata1.00: status { DRDY ERR }
[294.371006] ata1.00: error { UNC } 
[ 294.370697] ata1.00: exception Emask 0x0 SAct 0x0SErr 0x0 action 0x0
...and so on.

Thanks very much.
Neil

---

### Post by Xiong Chiamiov on 2009-03-07
Ctrl+alt+f1 will get you into a terminal, from which you can enter commands.  I don't know which logfiles would be useful for this, but hopefully my bump will give this visibility to someone who does.

---

