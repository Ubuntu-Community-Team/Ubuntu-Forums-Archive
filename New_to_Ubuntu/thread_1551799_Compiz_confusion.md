---
title: "Compiz confusion"
date: 2010-08-12
forum: New to Ubuntu
---

### Post by grubstub on 2010-08-12
Hi,

I was messing around with the settings in the Compiz CCSM and accidentally set the opacity of all windows to 0, resulting in a sudden blank screen. After a frantic restart, I resorted to trying to reset Compiz via the terminal using the following command (picked up from another message board):

gconftool-2 --recursive-unset -a /apps/compiz

After restarting again, the window transparencies are thankfully back to normal, however the top panel bar is missing (that containing the applications drop down, etc)... This is a pretty vital part, and rather than mess around any further i'd really appreciate any suggestions you could give in order to get this back!

---

### Post by grubstub on 2010-08-12
Panic over! I managed to restore the default settings using a nifty little program available at:

[http://www.starryhope.com/linux/ubuntu/2010/restore-the-default-panels-in-ubuntu/](http://www.starryhope.com/linux/ubuntu/2010/restore-the-default-panels-in-ubuntu/)

A great help should anyone else find themselves in a similarly silly predicament...

---

