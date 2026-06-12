---
title: "Ethernet only works if I ifconfig down &amp; back up"
date: 2007-09-10
forum: Networking &amp; Wireless
---

### Post by MarkusRTK on 2007-09-10
On a college network here -- my ethernet connection doesn't work at boot. (Doesn't look like it assigns an IP address.) However, if I:

```
sudo ifconfig eth0 down
sudo ifconfig eth0 up
```

the connection proceeds to work flawlessly. 

Any suggestions as to how I can fix this? Would it be possible just to write a script that does this automatically at boot, or is there some file I should tweak...?

(For the record, no such problem in WinXP. It's the Harvard network, if anyone else from that august institution is on the forum...)

---

### Post by Kobalt on 2007-09-10
Make sure you have this line
> auto eth0
in this file
```
cat /etc/network/interfaces
```
If not, add it before the eth0 interface paragraph.

---

### Post by MarkusRTK on 2007-09-10
Already had it. (It was after the eth0 interface paragraph; moved it to before as you indicated, but that made no differences.) Thanks for the tip though. Other suggestions?

---

