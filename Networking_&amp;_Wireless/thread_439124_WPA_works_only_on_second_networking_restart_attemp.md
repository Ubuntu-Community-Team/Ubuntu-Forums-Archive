---
title: "WPA works only on second networking restart attempt"
date: 2007-05-10
forum: Networking &amp; Wireless
---

### Post by ocwo92 on 2007-05-10
I'm hoping someone can help me resolve the following problem:

I've managed to connect to a WLAN via the network manager on Kubuntu (not Ubuntu). It works, but I'd rather have the application remember the password for the network.

Instead, I followed [these instructions]("http://ubuntuforums.org/showthread.php?t=318539") for setting up a WPA connection instead. It works, kind of.

Once I sudo /etc/init.d/networking restart, I'm online (well, at least I am after having spent what feels like ages waiting for the script to finish, most of the time spent waiting for the non-connected eth* to time out). So, nothing is wrong with the network card, passwords, SSID, etc.

However - here's the problem: the wireless connection is off when I reboot.

I have to manually type "sudo /etc/init.d/networking restart" in order to connect to the WLAN, and that kind of defeats the purpose of remembering the password.

It might be possible to add an automatic shell script startup that executes the ../networking script by adding the users to the sudoers list without password, but I'd rather not pursue that option.

There's no symbolic link to ../init.d/networking from /etc/rc5.d; I assume this is not required, but I may be wrong.

Can any of you help me figure out what I need to do to have the WLAN enabled at start-up?

---

### Post by ocwo92 on 2007-05-10
Well, I suppose part of the problem was that I'm used to other Linux distributions. Adding a link to a script that executes "/etc/init.d/networking restart &" within /etc/rcS.d instead of /etc/rc5.d seems to make the network card connect to the WLAN at start-up.

---

