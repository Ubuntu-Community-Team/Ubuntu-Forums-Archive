---
title: "Start network interface before other processes"
date: 2007-05-23
forum: Networking &amp; Wireless
---

### Post by sniper89 on 2007-05-23
Hey, as the topic says, I want to start (to be sure it does so!) the network interface before all the other network-related processes, because some time ago I had an issue that I had to start apache2 after the system booted, but doing /etc/init.d/apache2 start actually started apache2, and I found out that just doing update-rc.d -f apache2 remove and update-rc.d apache defaults solved the case. Unfortunately (my server doesn't have a screen and any peripherials), it didn't for sshd, that stopped starting on-boot too and is the most important service for me. Again, creating a script doing /etc/init.d/ssh start on startup solves the problem, but removing the ssh rc.d entries using update-rc.d and restoring doesn't, that's why I'm asking for your help. I'm looking for something like /etc/conf.d/rc in some other distros (there's a directive in it allowing you to make the system check whether networking is up before starting any networking processes).

Cherries ;)

---

### Post by sniper89 on 2007-05-26
Errr... I'm an administrator on many boards and I know how annoying bumping is and thus I'm against it, but I think that if anybody knows how to do it it should save many hours of work for people that also need to be sure networking starts before Internet apps do.

EDIT: Oh, this might help: I had that problem with some other (can't remember) program not running on startup, I didn't know how to solve it then, but I've upgraded to Feisty and it just "solved itself". Now it's back for apache2 (as mentioned, I've solved that one, but it sometimes comes back) and sshd :(

---

