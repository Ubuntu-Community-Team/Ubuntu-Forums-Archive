---
title: "wifi Qualcomm Atheros Device UNCLAIMED, Ubuntu 14.04 / 14.10"
date: 2015-02-19
forum: Networking &amp; Wireless
---

### Post by razvandrt on 2015-02-19
Hello everybody,

Unfortunately I have been trying to make use of similar issues on the forum but cannot seem to set up the WiFi interface and make it work.

I have followed the instructions for generating the required dump file, and attached it to this post.

Initially I have installed Ubuntu 14.04 but thought to upgrade it (do-release-upgrade -d) maybe it will get some drivers for it to work..

Any help is appreciated.


Thank you!

---

### Post by chili555 on 2015-02-19
Your device is: > Qualcomm Atheros Device [168c:003e] (rev 20)
	Subsystem: Foxconn International, Inc. Device [105b:e08e]Please see: [http://ubuntuforums.org/showthread.php?t=2248919](http://ubuntuforums.org/showthread.php?t=2248919) Also: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1383184](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1383184)

There is currently no support for your device. I suggest you register at Launchpad and add to the bug report.

---

### Post by jeremy31 on 2015-02-19
I think that device is the one that will see some minimal support in kernel 3.20 as the ath10k devs are still working on it

---

### Post by razvandrt on 2015-02-19
Thanks a lot Chili for the prompt reply! unfortunately not good news :P

I have noticed the bug and forum post too, but being different product name / subsystem, thought it might be a different case.
Anyway, I opened a question on Launchpad also , and maybe the guys will turn it into a bug or something ... 


Been looking at Qualcomm too but cannot seem to find appropriate support in regards to the acquired Atheros brand... was thinking to contact them too or Acer about the lack of drivers.
A bit weird to ship a laptop with a Linux distro (Linpus), but not consider other major ones too..

Thank you again and hopefully some smart devs will come up with a fix soon! :)

---

### Post by razvandrt on 2015-02-19
Jeremy, thank you for your update too!

will look more into their site also: [https://wireless.wiki.kernel.org/en/users/Drivers/ath10k](https://wireless.wiki.kernel.org/en/users/Drivers/ath10k)

---

