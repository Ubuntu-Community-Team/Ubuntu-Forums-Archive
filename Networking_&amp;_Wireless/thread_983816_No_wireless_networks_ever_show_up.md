---
title: "No wireless networks ever show up"
date: 2008-11-16
forum: Networking &amp; Wireless
---

### Post by dayyou on 2008-11-16
Ok, kinda new to linux and im running ubuntu 8.04 i think it is, and everything is installed fine and all, but my wireless say's its all installed but it simply does not show any sign of network connections. none show up, it doesnt even scan, i know theres a whay to fix this and you guys always ask for info for someone to enter a command line and give the results,

i need help

thanks

---

### Post by xadder on 2008-11-16
I solve this for my Thinkpad, see "Simple wireless solution" thread I started.

---

### Post by dayyou on 2008-11-16
> **xadder said:**
> I solve this for my Thinkpad, see "Simple wireless solution" thread I started.

im sorry, im reading it but im not finding a solution, im obviously missing something

---

### Post by jnorthr on 2008-11-16
we can start by doing a simple command from a terminal session.
click applicaions>accessories>terminal to start a command session.
Then type ifconfig. If you can find a way to post the results here it will help us to help you. There is a second command called 'iwconfig' that shows more details about your specific wireless configurations.

Obvious question, but i'll ask anyway, do you have any other computers that currently use your router ? If so, we can conclude your problems are not do to 1) your service provider 2) your wiring/cables/physical connections. It just helps to eliminate possible causes why your system won't work.
thx
jim

---

### Post by dayyou on 2008-11-16
ok i got it guys,   i simply grabbed a cat5 cable plug it in and it started to download a butload of updates and apparently a wireless driver was one of them and it works now, thank for your help anyways

---

### Post by Hawk__0 on 2008-11-16
hey, havin the same problem here but with 8.10.  Wireless was picking up networks until I grabbed this "buttload" of updates.  Now it wont find anything even though the wireless card appears to be working.

Any Ideas on how to fix this?

---

