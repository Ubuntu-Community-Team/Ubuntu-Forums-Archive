---
title: "Complete system freeze 10.04"
date: 2010-11-18
forum: New to Ubuntu
---

### Post by echo314 on 2010-11-18
I seem to be plagued by random freezes. This did not always occur, it started sometime a few release ago. My only workaround is hitting the comp's physical reset button. The freeze does not seem to happen at a certain time (e.g. right after startup). I know how to export lots of hardware info (sudo lshw > lshw_output) but I don't know how to export log files. 

It may be related to power saving functions, but I have not been able to pin any one factor down related to every freeze.

P.S. why does the attachment system require me to end the output file with .txt to upload it?

---

### Post by Sealbhach on 2010-11-18
When it freezes, are you able to do Ctrl+Alt+F1 to get to another tty screen and log in there? If you can do that, then you can run top or htop and find out what's hogging all your CPU or memory.

.

---

