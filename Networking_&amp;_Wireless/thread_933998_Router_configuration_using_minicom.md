---
title: "Router configuration using minicom"
date: 2008-09-30
forum: Networking &amp; Wireless
---

### Post by shunmugaprabhu on 2008-09-30
I am using Ubuntu. I wrote expect programming for router configuration. I run this script via minicom.I captured the router response into variable/file. But it contains unnecessary characters added. How to remove the terminal code ? Please guide me.

By
Shun

---

### Post by MrFSL on 2008-09-30
More information please.

---

### Post by superprash2003 on 2008-09-30
if the unnecessary characters are at the beginning or end of the output, you could just store it into a variable and remove the first few or last few characters which are unwanted..

---

### Post by iponeverything on 2008-09-30
you can remove minicom from the equation and have expect talk directly to the serial port.

see: 
[http://www.linuxjournal.com/article/3357](http://www.linuxjournal.com/article/3357)
[http://www.uni.aps.anl.gov/controls/docs/serialWatch.html](http://www.uni.aps.anl.gov/controls/docs/serialWatch.html)


Another option:
most routers do telnet and expect script would be a bit easier over telnet.

---

