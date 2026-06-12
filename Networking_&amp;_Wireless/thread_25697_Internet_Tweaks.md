---
title: "Internet Tweaks"
date: 2005-04-10
forum: Networking &amp; Wireless
---

### Post by tdell on 2005-04-10
Anyone know how to permanently change settings like RWIN default recieve window, turn off time stamping and change window scaling?
I followed instructions on several sites but loose the changes after a reboot.

Any help would be appreciated.

Tom
l

---

### Post by nemin on 2005-04-11
[QUOTE=tdell]Anyone know how to permanently change settings like RWIN default recieve window, turn off time stamping and change window scaling?
I followed instructions on several sites but loose the changes after a reboot.
[/QUOTE]
Maybe the /proc/sys/net/ipv4 tree has some interesting settings for you.

---

### Post by tdell on 2005-04-12
Hi, Thanks tried that but it won't let me save any changes I make.

Tom

---

### Post by banadushi on 2005-04-12
Put your changes in /etc/sysctl.conf, the file format is prettry straight forward and documented in the man page.

---

### Post by tdell on 2005-04-12
Still no joy. Just will not retain settings after a reboot.

Tom

---

### Post by banadushi on 2005-04-12
Have you modified the boot scripts at all, it should be called by /etc/rcS.d/procps.sh.  What is your /etc/sysctl.conf.

If you boot it up then run /etc/init.d/procps.sh does it set the values, if so then your boot order/proccess is jacked.

---

