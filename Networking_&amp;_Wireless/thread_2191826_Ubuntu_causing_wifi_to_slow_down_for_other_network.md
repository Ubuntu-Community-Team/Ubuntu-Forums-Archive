---
title: "Ubuntu causing wifi to slow down for other network users"
date: 2013-12-04
forum: Networking &amp; Wireless
---

### Post by _user on 2013-12-04
There are 5 users using our wireless network (other users are non-linux).  It appears that my ubuntu machine reduces the wireless internet speed by a factor of 10 when connected to the internet.  This only seems to have happened in the past week - no known changes other than automatic updates from Ubuntu.  I've included relevant links below to other users with the same problem.  One user in the thread suggests that switching the encryption from hardware to software will fix it.

Same issues as people in this thread: [http://ubuntuforums.org/showthread.php?t=1877120&page=2](http://ubuntuforums.org/showthread.php?t=1877120&page=2)

This ([https://dl.dropboxusercontent.com/u/8528853/wireless-info.txt](https://dl.dropboxusercontent.com/u/8528853/wireless-info.txt)) is the output from one of the posts in the thread: [http://ubuntuforums.org/showthread.php?t=1877120&p=12588426#post12588426](http://ubuntuforums.org/showthread.php?t=1877120&p=12588426#post12588426)

What commands should I run to debug / fix this?

---

### Post by chili555 on 2013-12-04
This sometimes helps:```
sudo -i
echo "options iwlwifi 11n_disable=1"  >>  /etc/modprobe.d/iwlwifi.conf
exit
```Reboot and let us have your report.

---

### Post by _user on 2013-12-04
Here is the report: [https://dl.dropboxusercontent.com/u/8528853/wireless-info2.txt](https://dl.dropboxusercontent.com/u/8528853/wireless-info2.txt)

---

### Post by chili555 on 2013-12-05
Thanks. The report I was really hoping for was either that the change made no difference and that your  ubuntu machine still reduces the wireless internet speed by a factor of 10 when connected to the internet; *OR* that the problem is solved. Which did you find?

---

### Post by _user on 2013-12-05
Sorry I forgot to add, the change made no difference.

---

### Post by tlk2drew on 2013-12-07
Turn off WMM in your wireless router.  Should be under QoS.

---

### Post by _user on 2013-12-07
I fixed this issue by rolling back the kernel to an earlier version.  Thanks for the help!

---

