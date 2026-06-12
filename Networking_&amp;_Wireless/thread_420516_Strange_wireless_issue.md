---
title: "Strange wireless issue"
date: 2007-04-23
forum: Networking &amp; Wireless
---

### Post by chrisjs87 on 2007-04-23
Ok, so I installed ndiswrapper, found the correct driver for my device (Inprocomm 2220), got everything up and running and was connecting to wireless networks without a problem.  Then today I wake up, sit down at my computer and attempt to connect to my wireless network.... The option to connect to wireless networks has completely disappeared from "Network".  Only wired and modem connections are present.  So I checked ndiswrapper to see if the driver was still installed and present and sure enough:

------
root@chris-laptop:~# ndiswrapper -l
neti2220 : driver installed
        device (17FE:2220) present
root@chris-laptop:~# 
-----

Something I noticed as strange that might somehow be causing this problem

----

00:00.0 0600: 8086:3580 (rev 02)
00:00.1 0880: 8086:3584 (rev 02)
00:00.3 0880: 8086:3585 (rev 02)
00:02.0 0300: 8086:3582 (rev 02)
00:02.1 0380: 8086:3582 (rev 02)
00:1d.0 0c03: 8086:24c2 (rev 03)
00:1d.1 0c03: 8086:24c4 (rev 03)
00:1d.2 0c03: 8086:24c7 (rev 03)
00:1d.7 0c03: 8086:24cd (rev 03)
00:1e.0 0604: 8086:2448 (rev 83)
00:1f.0 0601: 8086:24cc (rev 03)
00:1f.1 0101: 8086:24ca (rev 03)
00:1f.3 0c05: 8086:24c3 (rev 03)
00:1f.5 0401: 8086:24c5 (rev 03)
00:1f.6 0703: 8086:24c6 (rev 03)
01:01.0 0200: 10ec:8139 (rev 10)
01:02.0 0200: 17fe:2220                **<--- Here's the ID, but theres no (rev #).  Is that part of the problem?**
01:04.0 0607: 1524:1410 (rev 01)
root@chris-laptop:~

-------

Can anyone tell me what the deal is?

---

### Post by Floppyjoe on 2007-04-23
Did you add the word ndiswrapper to /etc/modules?
```
sudo gedit /etc/modules
```
add the word ndiswrapper then save and close file.

---

### Post by chrisjs87 on 2007-04-23
Success.  Thanks!

---

